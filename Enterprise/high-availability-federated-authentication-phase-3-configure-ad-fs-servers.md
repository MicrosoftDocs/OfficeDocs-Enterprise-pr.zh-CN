---
title: 高可用性联合身份验证阶段3配置 AD FS 服务器
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: 摘要：在 Microsoft Azure 中为 Office 365 的高可用性联合身份验证创建和配置 Active Directory 联合身份验证服务 (AD FS) 服务器。
ms.openlocfilehash: add154dbce67c76b3f88e205c683711f72cb7b9a
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741158"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="15cf3-103">高可用性联合身份验证阶段 3：配置 AD FS 服务器</span><span class="sxs-lookup"><span data-stu-id="15cf3-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

 <span data-ttu-id="15cf3-104">**摘要：** 在 Microsoft Azure 中为 Office 365 的高可用性联合身份验证创建和配置 Active Directory 联合身份验证服务 (AD FS) 服务器。</span><span class="sxs-lookup"><span data-stu-id="15cf3-104">**Summary:** Create and configure the Active Directory Federation Services (AD FS) servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="15cf3-105">在为 Azure 基础结构服务中的 Office 365 联合身份验证部署高可用性的这一阶段中，创建一个内部负载均衡器和两个 AD FS 服务器。</span><span class="sxs-lookup"><span data-stu-id="15cf3-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="15cf3-106">必须先完成这一阶段，然后才能移至[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)。</span><span class="sxs-lookup"><span data-stu-id="15cf3-106">You must complete this phase before moving on to [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span></span> <span data-ttu-id="15cf3-107">请参阅[在 Azure 中部署 Office 365 的高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)，了解所有阶段。</span><span class="sxs-lookup"><span data-stu-id="15cf3-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="15cf3-108">在 Azure 中创建 AD FS 服务器虚拟机</span><span class="sxs-lookup"><span data-stu-id="15cf3-108">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="15cf3-p102">使用以下 PowerShell 命令块创建两个 AD FS 服务器的虚拟机。此 PowerShell 命令集使用下表中的值：</span><span class="sxs-lookup"><span data-stu-id="15cf3-p102">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers. This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="15cf3-111">表 M，用于虚拟机</span><span class="sxs-lookup"><span data-stu-id="15cf3-111">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="15cf3-112">表 R，用于资源组</span><span class="sxs-lookup"><span data-stu-id="15cf3-112">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="15cf3-113">表 V，用于虚拟网络设置</span><span class="sxs-lookup"><span data-stu-id="15cf3-113">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="15cf3-114">表 S，用于子网</span><span class="sxs-lookup"><span data-stu-id="15cf3-114">Table S, for your subnets</span></span>
    
- <span data-ttu-id="15cf3-115">表 I，用于静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="15cf3-115">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="15cf3-116">表 A（针对可用性集）</span><span class="sxs-lookup"><span data-stu-id="15cf3-116">Table A, for your availability sets</span></span>
    
<span data-ttu-id="15cf3-117">回想一下您在[高可用性联合身份验证阶段 2](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)中定义了表 M: 配置域控制器和表 R、V、S、I 和 A in [high availability 联合身份验证阶段 1: configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="15cf3-117">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="15cf3-118">[!注意] 下面的命令集使用最新版 Azure PowerShell。</span><span class="sxs-lookup"><span data-stu-id="15cf3-118">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="15cf3-119">请参阅 [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)（Azure PowerShell cmdlet 使用入门）。</span><span class="sxs-lookup"><span data-stu-id="15cf3-119">See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="15cf3-120">首先，为两个 AD FS 服务器创建 Azure 内部负载均衡器。</span><span class="sxs-lookup"><span data-stu-id="15cf3-120">First, you create an Azure internal load balancer for the two AD FS servers.</span></span> <span data-ttu-id="15cf3-121">指定变量的值, \<并删除和 > 字符。</span><span class="sxs-lookup"><span data-stu-id="15cf3-121">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="15cf3-122">提供所有正确值后，在 Azure PowerShell 命令提示符处或 PowerShell ISE 上运行生成块。</span><span class="sxs-lookup"><span data-stu-id="15cf3-122">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
```
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

<span data-ttu-id="15cf3-123">接下来，创建 AD FS 服务器虚拟机。</span><span class="sxs-lookup"><span data-stu-id="15cf3-123">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="15cf3-124">提供所有正确值后，在 Azure PowerShell 命令提示符处或 PowerShell ISE 上运行生成块。</span><span class="sxs-lookup"><span data-stu-id="15cf3-124">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
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
> <span data-ttu-id="15cf3-p105">由于这些虚拟机用于 Intranet 应用程序，所以不会为它们分配公用 IP 地址或 DNS 域名称标签，也不会将它们公开到 Internet。但是，这也意味着你无法从 Azure 门户与它们进行连接。查看虚拟机的属性时“连接”\*\*\*\* 选项不可用。使用远程桌面连接附件或另一个远程桌面工具连接使用其专用 IP 地址或 Intranet DNS 名称的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="15cf3-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="15cf3-p106">对于每个虚拟机，请使用所选择的远程桌面客户端并创建远程桌面连接。使用其 Intranet DNS 或计算机名称以及本地管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="15cf3-p106">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="15cf3-131">对于每个虚拟机, 请通过 Windows PowerShell 提示符下的这些命令将它们加入相应的 Active Directory 域服务 (AD DS) 域。</span><span class="sxs-lookup"><span data-stu-id="15cf3-131">For each virtual machine, join them to the appropriate Active Directory Domain Services (AD DS) domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="15cf3-132">以下是因成功完成这一阶段后生成的配置，包含占位符计算机名称。</span><span class="sxs-lookup"><span data-stu-id="15cf3-132">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
**<span data-ttu-id="15cf3-133">阶段 3：Azure 中用于高可用性联合身份验证基础结构的 AD FS 服务器和内部负载均衡器</span><span class="sxs-lookup"><span data-stu-id="15cf3-133">Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure</span></span>**

![AD FS 服务器的 Azure 中的高可用性 Office 365 联合身份验证基础结构的第3阶段](media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="15cf3-135">后续步骤</span><span class="sxs-lookup"><span data-stu-id="15cf3-135">Next step</span></span>

<span data-ttu-id="15cf3-136">使用[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)继续配置此工作负载。</span><span class="sxs-lookup"><span data-stu-id="15cf3-136">Use [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="15cf3-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15cf3-137">See Also</span></span>

[<span data-ttu-id="15cf3-138">在 Azure 中部署 Office 365 的高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="15cf3-138">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="15cf3-139">用于 Office 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="15cf3-139">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)


