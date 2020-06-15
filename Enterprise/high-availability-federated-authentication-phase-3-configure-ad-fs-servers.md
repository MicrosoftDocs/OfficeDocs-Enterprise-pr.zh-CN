---
title: 高可用性联合身份验证阶段3配置 AD FS 服务器
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: 摘要：在 Microsoft Azure 中为 Microsoft Microsoft Microsoft 365 的高可用性联合身份验证创建和配置 Active Directory 联合身份验证服务（AD FS）服务器。
ms.openlocfilehash: 7b32c39ada30059df78ccb5429dba11c1576dff7
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711925"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="cf9b5-103">高可用性联合身份验证阶段 3：配置 AD FS 服务器</span><span class="sxs-lookup"><span data-stu-id="cf9b5-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

<span data-ttu-id="cf9b5-104">在此阶段，在 Azure 基础结构服务中为 Microsoft 365 联合身份验证部署高可用性时，将创建内部负载平衡器和两个 AD FS 服务器。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="cf9b5-105">必须先完成此阶段，然后才能进入[第4阶段：配置 web 应用程序代理](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-105">You must complete this phase before moving on to [Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span></span> <span data-ttu-id="cf9b5-106">有关所有阶段，请参阅[在 Azure 中为 Microsoft 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-106">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="cf9b5-107">在 Azure 中创建 AD FS 服务器虚拟机</span><span class="sxs-lookup"><span data-stu-id="cf9b5-107">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="cf9b5-p102">使用以下 PowerShell 命令块创建两个 AD FS 服务器的虚拟机。此 PowerShell 命令集使用下表中的值：</span><span class="sxs-lookup"><span data-stu-id="cf9b5-p102">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers. This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="cf9b5-110">表 M，用于虚拟机</span><span class="sxs-lookup"><span data-stu-id="cf9b5-110">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="cf9b5-111">表 R，用于资源组</span><span class="sxs-lookup"><span data-stu-id="cf9b5-111">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="cf9b5-112">表 V，用于虚拟网络设置</span><span class="sxs-lookup"><span data-stu-id="cf9b5-112">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="cf9b5-113">表 S，用于子网</span><span class="sxs-lookup"><span data-stu-id="cf9b5-113">Table S, for your subnets</span></span>
    
- <span data-ttu-id="cf9b5-114">表 I，用于静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="cf9b5-114">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="cf9b5-115">表 A（针对可用性集）</span><span class="sxs-lookup"><span data-stu-id="cf9b5-115">Table A, for your availability sets</span></span>
    
<span data-ttu-id="cf9b5-116">回想一下在[阶段2：配置域控制器](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)和表 R、V、S、I 和 A[阶段1： configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md)中定义了表 M。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-116">Recall that you defined Table M in [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="cf9b5-117">[!注意] 下面的命令集使用最新版 Azure PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-117">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="cf9b5-118">请参阅[Azure PowerShell 入门](https://docs.microsoft.com/powershell/azure/get-started-azureps)。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-118">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="cf9b5-119">首先，为两个 AD FS 服务器创建 Azure 内部负载均衡器。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-119">First, you create an Azure internal load balancer for the two AD FS servers.</span></span> <span data-ttu-id="cf9b5-120">指定变量的值，并删除 \< and > 字符。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-120">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="cf9b5-121">提供所有正确值后，在 Azure PowerShell 命令提示符处或 PowerShell ISE 上运行生成块。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-121">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="cf9b5-122">若要基于自定义设置生成可随时运行的 PowerShell 命令块，请使用此[Microsoft Excel 配置工作簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx)。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-122">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="cf9b5-123">接下来，创建 AD FS 服务器虚拟机。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-123">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="cf9b5-124">提供所有正确值后，在 Azure PowerShell 命令提示符处或 PowerShell ISE 上运行生成块。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-124">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> <span data-ttu-id="cf9b5-p105">由于这些虚拟机用于 Intranet 应用程序，所以不会为它们分配公用 IP 地址或 DNS 域名称标签，也不会将它们公开到 Internet。但是，这也意味着你无法从 Azure 门户与它们进行连接。查看虚拟机的属性时“连接”\*\*\*\* 选项不可用。使用远程桌面连接附件或另一个远程桌面工具连接使用其专用 IP 地址或 Intranet DNS 名称的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="cf9b5-p106">对于每个虚拟机，请使用所选择的远程桌面客户端并创建远程桌面连接。使用其 Intranet DNS 或计算机名称以及本地管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-p106">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="cf9b5-131">对于每个虚拟机，请通过 Windows PowerShell 提示符下的这些命令将它们加入相应的 Active Directory 域服务（AD DS）域。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-131">For each virtual machine, join them to the appropriate Active Directory Domain Services (AD DS) domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="cf9b5-132">以下是因成功完成这一阶段后生成的配置，包含占位符计算机名称。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-132">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="cf9b5-133">**阶段 3：Azure 中用于高可用性联合身份验证基础结构的 AD FS 服务器和内部负载均衡器**</span><span class="sxs-lookup"><span data-stu-id="cf9b5-133">**Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure**</span></span>

![在 Azure 中使用 AD FS 服务器的高可用性 Microsoft 365 联合身份验证基础结构的第3阶段](media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="cf9b5-135">后续步骤</span><span class="sxs-lookup"><span data-stu-id="cf9b5-135">Next step</span></span>

<span data-ttu-id="cf9b5-136">使用[阶段4：配置 web 应用程序代理](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)以继续配置此工作负载。</span><span class="sxs-lookup"><span data-stu-id="cf9b5-136">Use [Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cf9b5-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf9b5-137">See Also</span></span>

[<span data-ttu-id="cf9b5-138">在 Azure 中部署适用于 Microsoft 365 的高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="cf9b5-138">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="cf9b5-139">Microsoft 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="cf9b5-139">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)


