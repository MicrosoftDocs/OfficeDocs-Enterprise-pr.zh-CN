---
title: 高可用性联合身份验证阶段1配置 Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 摘要：配置 Microsoft Azure 基础结构以托管适用于 Office 365 的高可用性联合身份验证。
ms.openlocfilehash: 262a7dcdb2dc48f7890b7ef188b1d8ce506f40dd
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072134"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>高可用性联合身份验证阶段 1：配置 Azure

在此阶段中，将在 Azure 中创建资源组、虚拟网络（VNet）和可用性集，这些集将承载第2阶段、3步和第4阶段的虚拟机。 必须先完成此阶段，然后才能进入[第2阶段：配置域控制器](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)。 请参阅[在 Azure 中部署 Office 365 的高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)，了解所有阶段。
  
必须使用以下基本组件预配 Azure：
  
- 资源组
    
- 包含用于托管 Azure 虚拟机的子网的跨界 Azure 虚拟网络（VNet）
    
- 执行子网隔离的网络安全组
    
- 可用性集
    
## <a name="configure-azure-components"></a>配置 Azure 组件

开始配置 Azure 组件之前，请填写下表。 为了帮助你完成配置 Azure 的过程，请打印此部分并记下所需的信息，或将此部分复制到文档中进行填写。 对于 VNet 的设置，请填写表 V。
  
|**项**|**配置设置**|**说明**|**值**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |VNet 名称  <br/> |要分配给 VNet 的名称（示例 FedAuthNet）。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |VNet 位置  <br/> |将包含虚拟网络的区域 Azure 数据中心。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |VPN 设备 IP 地址  <br/> |Internet 上 VPN 设备接口的公共 IPv4 地址。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |VNet 地址空间  <br/> |虚拟网络的地址空间。与 IT 部门协作，以确定该地址空间。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |IPsec 共享的密钥  <br/> |一组 32 位字符的随机字母数字字符串，用于对站点间 VPN 连接的两端进行身份验证。与 IT 或安全部门协作来确定此密钥值。或者，请参阅[创建 IPsec 预共享密钥的随机字符串](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
   
 **表 V：跨部署虚拟网络配置**
  
接下来，填写针对此解决方案的子网的表 S。所有地址空间应为无类别域际路由选择 (CIDR) 格式，也称为网络前缀格式。例如，10.24.64.0/20。
  
对于前三个子网，请根据虚拟网络地址空间指定一个名称和一个 IP 地址空间。 对于网关子网，请使用以下命令确定 Azure 网关子网的27位地址空间（带 a/27 前缀长度）：
  
1. 将 VNet 地址空间的可变位设置为 1，直到用于网关子网的位，然后将剩余位设置为 0。
    
2. 将生成位转换为十进制并表示为一个地址空间，其中将前缀长度设置为网关子网的大小。
    
有关为您执行此计算的 PowerShell 命令块和 c # 或 Python 控制台应用程序，请参阅[Azure 网关子网的地址空间计算器](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)。
  
与 IT 部门协作以确定这些虚拟网络地址空间中的地址空间。
  
|**项**|**子网名称**|**子网地址空间**|**用途**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |Active Directory 域服务（AD DS）域控制器和目录同步服务器虚拟机（Vm）使用的子网。  <br/> |
|2.  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |AD FS Vm 使用的子网。  <br/> |
|3.  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |Web 应用程序代理虚拟机使用的子网。  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |Azure 网关虚拟机使用的子网。  <br/> |
   
 **表 S：虚拟网络中的子网**
  
下一步，针对分配给虚拟机和负载平衡器实例的静态 IP 地址填写表 I。
  
|**项目**|**用途**|**子网的 IP 地址**|**值**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |第一个域控制器的静态 IP 地址  <br/> |在表 S 的项目 1 中定义的子网地址空间的第四个可能的 IP 地址。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |第二个域控制器的静态 IP 地址  <br/> |在表 S 的项目 1 中定义的子网地址空间的第五个可能的 IP 地址。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |目录同步服务器的静态 IP 地址  <br/> |在表 S 的项目1中定义的子网地址空间的第六个可能的 IP 地址。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |AD FS 服务器的内部负载平衡器的静态 IP 地址  <br/> |在表 S 的项目 2 中定义的子网地址空间的第四个可能的 IP 地址。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |第一个 AD FS 服务器的静态 IP 地址  <br/> |在表 S 的项目 2 中定义的子网地址空间的第五个可能的 IP 地址。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|6.  <br/> |第二个 AD FS 服务器的静态 IP 地址  <br/> |在表 S 的项目 2 中定义的子网地址空间的第六个可能的 IP 地址。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|7.  <br/> |第一个 web 应用程序代理服务器的静态 IP 地址  <br/> |在表 S 的项目 3 中定义的子网地址空间的第四个可能的 IP 地址。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|8.  <br/> |第二个 web 应用程序代理服务器的静态 IP 地址  <br/> |在表 S 的项目 3 中定义的子网地址空间的第五个可能的 IP 地址。  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
   
 **表 I：虚拟网络中的静态 IP 地址**
  
对于您希望在最初设置虚拟网络中的域控制器时使用的本地网络中的两个域名系统（DNS）服务器，请填写表 D。与 IT 部门合作以确定此列表。
  
|**项**|**DNS 服务器的友好名称**|**DNS 服务器的 IP 地址**|
|:-----|:-----|:-----|
|1.  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
   
 **表 D：本地 DNS 服务器**
  
若要通过站点到站点 VPN 连接将数据包从跨界网络路由到组织网络，您必须为虚拟网络配置具有所有可访问的地址空间列表（在 CIDR 表示法中）的本地网络。组织的本地网络上的位置。 定义本地网络的地址空间列表必须是唯一的，并且不得与用于其他虚拟网络或其他本地网络的地址空间重叠。
  
对于本地网络地址空间集，请填写表 L。请注意已列出三个空白条目，但通常需要更多。与 IT 部门协作，以确定该地址空间列表。
  
|**项**|**本地网络地址空间**|
|:-----|:-----|
|1.  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
   
 **表 L：本地网络的地址前缀**
  
现在，让我们开始构建 Azure 基础结构以托管 Office 365 的联合身份验证。
  
> [!NOTE]
> [!注意] 下面的命令集使用最新版 Azure PowerShell。 请参阅[Azure PowerShell 入门](https://docs.microsoft.com/powershell/azure/get-started-azureps)。 
  
首先，启动 Azure PowerShell 提示符并登录到你的帐户。
  
```powershell
Connect-AzAccount
```

> [!TIP]
> 若要基于自定义设置生成可随时运行的 PowerShell 命令块，请使用此[Microsoft Excel 配置工作簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx)。 

使用以下命令获得订阅名称。
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

对于较旧版本的 Azure PowerShell，请改为使用此命令。
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

设置 Azure 订阅。 使用正确的名称替换引号内的\<所有内容，包括和 > 字符。
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

接下来，创建新的资源组。 要确定唯一的一组资源组名称，请使用此命令列出现有的资源组。
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

为一组唯一资源组名称填写下表。
  
|**项目**|**资源组名称**|**用途**|
|:-----|:-----|:-----|
|1.  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |域控制器  <br/> |
|2.  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |AD FS 服务器  <br/> |
|3.  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |Web 应用程序代理服务器  <br/> |
|4.  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |基础结构元素  <br/> |
   
 **表 R：资源组**
  
使用这些命令创建新的资源组。
  
```powershell
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

接下来，创建 Azure 虚拟网络及其子网。
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

接下来，为每个具有虚拟机的子网创建网络安全组。 若要执行子网隔离，可以添加规则，指定允许或拒绝进入子网的网络安全组的特定类型流量。
  
```powershell
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

下一步，请使用这些命令来创建站点间 VPN 连接的网关。
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> 各个用户的联合身份验证不依赖任何本地资源。 但是，如果此站点到站点 VPN 连接变得不可用，VNet 中的域控制器将不会收到在本地 Active Directory 域服务中进行的用户帐户和组的更新。 若要确保不会发生这种情况，可以为站点到站点 VPN 连接配置高可用性。 有关详细信息，请参阅[高可用性跨界连接与 VNet 到 VNet 连接](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
接下来，从此命令的显示内容中，记录用于虚拟网络的 Azure VPN 网关的公用 IPv4 地址。
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

接下来，请将本地 VPN 设备配置为连接到 Azure VPN 网关。有关详细信息，请参阅[配置 VPN 设备](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。
  
若要配置本地 VPN 设备，需要以下各项：
  
- Azure VPN 网关的公用 IPv4 地址。
    
- 站点到站点 VPN 连接的 IPsec 预共享密钥（表 V - 第 5 项 - 值列）。
    
接下来，请确保虚拟网络的地址空间是可以从本地网络访问。这通常是通过以下操作完成：将对应于虚拟网络地址空间的路由添加到 VPN 设备中，然后将该路由公布到组织网络中其余的路由基础结构。与 IT 部门协作，以确定如何完成上述操作。
  
接下来，定义三个可用性集的名称。 填写表 A。 
  
|**项目**|**用途**|**可用性集的名称**|
|:-----|:-----|:-----|
|1.  <br/> |域控制器  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |AD FS 服务器  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Web 应用程序代理服务器  <br/> |![line](./media/Common-Images/TableLine.png)  <br/> |
   
 **表 A：可用性集**
  
在第 2、3 和 4 阶段中创建虚拟机时，将需要这些名称。
  
使用这些 Azure PowerShell 命令创建新的可用性集。
  
```powershell
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

这是该阶段成功完成后生成的配置。
  
**第1阶段：适用于 Office 365 的高可用性联合身份验证的 Azure 基础结构**

![Azure 基础结构在 Azure 中实现高可用性 Office 365 联合身份验证的第1阶段](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>后续步骤

使用[阶段2：配置域控制器](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)以继续配置此工作负载。
  
## <a name="see-also"></a>另请参阅

[在 Azure 中部署 Office 365 的高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[用于 Office 365 开发/测试环境的联合身份](federated-identity-for-your-office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)

[了解 Office 365 标识和 Azure Active Directory](about-office-365-identity.md)


