---
title: 高可用性联合身份验证阶段4配置 web 应用程序代理
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 摘要：为 microsoft Azure 中的 Microsoft 365 的高可用性联合身份验证配置 web 应用程序代理服务器。
ms.openlocfilehash: 005497f9da7986fb4538b4d4c9699e55fe26fa65
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102490"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="42bc6-103">高可用性联合身份验证阶段 4：配置 Web 应用程序代理</span><span class="sxs-lookup"><span data-stu-id="42bc6-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

<span data-ttu-id="42bc6-104">在此阶段，在 Azure 基础结构服务中为 Microsoft 365 联合身份验证部署高可用性时，将创建内部负载平衡器和两个 AD FS 服务器。</span><span class="sxs-lookup"><span data-stu-id="42bc6-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="42bc6-105">您必须先完成此阶段，然后再转到[第5阶段： Configure 联合身份验证 For Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)。</span><span class="sxs-lookup"><span data-stu-id="42bc6-105">You must complete this phase before moving on to [Phase 5: Configure federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md).</span></span> <span data-ttu-id="42bc6-106">有关所有阶段，请参阅[在 Azure 中为 Microsoft 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="42bc6-106">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="42bc6-107">在 Azure 中创建面向 Internet 的负载均衡器</span><span class="sxs-lookup"><span data-stu-id="42bc6-107">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="42bc6-108">必须创建面向 Internet 的负载均衡器，以便 Azure 在两个 Web 应用程序代理服务器之间平均分发来自 Internet 的传入客户端身份验证通信。</span><span class="sxs-lookup"><span data-stu-id="42bc6-108">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="42bc6-109">[!注意] 下面的命令集使用最新版 Azure PowerShell。</span><span class="sxs-lookup"><span data-stu-id="42bc6-109">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="42bc6-110">请参阅[Azure PowerShell 入门](https://docs.microsoft.com/powershell/azure/get-started-azureps)。</span><span class="sxs-lookup"><span data-stu-id="42bc6-110">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="42bc6-111">提供位置和资源组值后，在 Azure PowerShell 命令提示符处或 PowerShell ISE 中运行生成块。</span><span class="sxs-lookup"><span data-stu-id="42bc6-111">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="42bc6-112">若要基于自定义设置生成可随时运行的 PowerShell 命令块，请使用此[Microsoft Excel 配置工作簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx)。</span><span class="sxs-lookup"><span data-stu-id="42bc6-112">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="42bc6-113">若要显示分配给面向 Internet 的负载均衡器的公用 IP 地址，请在本地计算机上的 Azure PowerShell 命令提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="42bc6-113">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="42bc6-114">确定联合身份验证服务 FQDN 并创建 DNS 记录</span><span class="sxs-lookup"><span data-stu-id="42bc6-114">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="42bc6-115">需要确定 DNS 名称以在 Internet 上标识联合身份验证服务名称。</span><span class="sxs-lookup"><span data-stu-id="42bc6-115">You need to determine the DNS name to identify your federation service name on the Internet.</span></span> <span data-ttu-id="42bc6-116">Azure AD Connect 将在第5阶段将 Microsoft 365 配置为使用此名称，这将成为 Microsoft 365 发送到连接客户端以获取安全令牌的 URL 的一部分。</span><span class="sxs-lookup"><span data-stu-id="42bc6-116">Azure AD Connect will configure Microsoft 365 with this name in Phase 5, which will become part of the URL that Microsoft 365 sends to connecting clients to get a security token.</span></span> <span data-ttu-id="42bc6-117">例如，fs.contoso.com（fs 代表联合身份验证服务）。</span><span class="sxs-lookup"><span data-stu-id="42bc6-117">An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="42bc6-118">在拥有联合身份验证服务 FDQN 之后，创建联合身份验证服务 FDQN 的公用 DNS 域 A 记录，该完全限定的域名可解析为面向 Internet 的 Azure 负载均衡器的公用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="42bc6-118">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="42bc6-119">**名称**</span><span class="sxs-lookup"><span data-stu-id="42bc6-119">**Name**</span></span>|<span data-ttu-id="42bc6-120">**Type**</span><span class="sxs-lookup"><span data-stu-id="42bc6-120">**Type**</span></span>|<span data-ttu-id="42bc6-121">**TTL**</span><span class="sxs-lookup"><span data-stu-id="42bc6-121">**TTL**</span></span>|<span data-ttu-id="42bc6-122">**值**</span><span class="sxs-lookup"><span data-stu-id="42bc6-122">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="42bc6-123">联合身份验证服务 FDQN</span><span class="sxs-lookup"><span data-stu-id="42bc6-123">federation service FDQN</span></span>  <br/> |<span data-ttu-id="42bc6-124">A</span><span class="sxs-lookup"><span data-stu-id="42bc6-124">A</span></span>  <br/> |<span data-ttu-id="42bc6-125">3600</span><span class="sxs-lookup"><span data-stu-id="42bc6-125">3600</span></span>  <br/> |<span data-ttu-id="42bc6-126">面向 Internet 的 Azure 负载均衡器的公用 IP 地址（通过上一节中的 **Write-Host** 命令显示)</span><span class="sxs-lookup"><span data-stu-id="42bc6-126">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="42bc6-127">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="42bc6-127">Here is an example:</span></span>
  
|<span data-ttu-id="42bc6-128">**名称**</span><span class="sxs-lookup"><span data-stu-id="42bc6-128">**Name**</span></span>|<span data-ttu-id="42bc6-129">**Type**</span><span class="sxs-lookup"><span data-stu-id="42bc6-129">**Type**</span></span>|<span data-ttu-id="42bc6-130">**TTL**</span><span class="sxs-lookup"><span data-stu-id="42bc6-130">**TTL**</span></span>|<span data-ttu-id="42bc6-131">**值**</span><span class="sxs-lookup"><span data-stu-id="42bc6-131">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="42bc6-132">fs.contoso.com</span><span class="sxs-lookup"><span data-stu-id="42bc6-132">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="42bc6-133">A</span><span class="sxs-lookup"><span data-stu-id="42bc6-133">A</span></span>  <br/> |<span data-ttu-id="42bc6-134">3600</span><span class="sxs-lookup"><span data-stu-id="42bc6-134">3600</span></span>  <br/> |<span data-ttu-id="42bc6-135">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="42bc6-135">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="42bc6-136">接下来，将一个 DNS 地址记录添加到组织的专用 DNS 命名空间，以将联合身份验证服务 FQDN 解析为分配给 AD FS 服务器（表 I，第 4 项，值列）的内部负载均衡器的专用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="42bc6-136">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="42bc6-137">在 Azure 中创建 Web 应用程序代理服务器虚拟机</span><span class="sxs-lookup"><span data-stu-id="42bc6-137">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="42bc6-138">使用下面的 Azure PowerShell 命令块为两个 Web 应用程序代理服务器创建虚拟机。 </span><span class="sxs-lookup"><span data-stu-id="42bc6-138">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="42bc6-139">请注意，以下 Azure PowerShell 命令集使用下表中的值：</span><span class="sxs-lookup"><span data-stu-id="42bc6-139">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="42bc6-140">表 M，用于虚拟机</span><span class="sxs-lookup"><span data-stu-id="42bc6-140">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="42bc6-141">表 R，用于资源组</span><span class="sxs-lookup"><span data-stu-id="42bc6-141">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="42bc6-142">表 V，用于虚拟网络设置</span><span class="sxs-lookup"><span data-stu-id="42bc6-142">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="42bc6-143">表 S，用于子网</span><span class="sxs-lookup"><span data-stu-id="42bc6-143">Table S, for your subnets</span></span>
    
- <span data-ttu-id="42bc6-144">表 I，用于静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="42bc6-144">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="42bc6-145">表 A（针对可用性集）</span><span class="sxs-lookup"><span data-stu-id="42bc6-145">Table A, for your availability sets</span></span>
    
<span data-ttu-id="42bc6-146">回想一下在[阶段2：配置域控制器](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)和表 R、V、S、I 和 A[阶段1： configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md)中定义了表 M。</span><span class="sxs-lookup"><span data-stu-id="42bc6-146">Recall that you defined Table M in [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="42bc6-147">提供所有正确值后，在 Azure PowerShell 命令提示符处或 PowerShell ISE 上运行生成块。</span><span class="sxs-lookup"><span data-stu-id="42bc6-147">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="42bc6-148">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span><span class="sxs-lookup"><span data-stu-id="42bc6-148">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span></span> <span data-ttu-id="42bc6-149">However, this also means that you cannot connect to them from the Azure portal.</span><span class="sxs-lookup"><span data-stu-id="42bc6-149">However, this also means that you cannot connect to them from the Azure portal.</span></span> <span data-ttu-id="42bc6-150">The **Connect** option is unavailable when you view the properties of the virtual machine.</span><span class="sxs-lookup"><span data-stu-id="42bc6-150">The **Connect** option is unavailable when you view the properties of the virtual machine.</span></span> <span data-ttu-id="42bc6-151">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span><span class="sxs-lookup"><span data-stu-id="42bc6-151">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="42bc6-152">以下是因成功完成这一阶段后生成的配置，包含占位符计算机名称。</span><span class="sxs-lookup"><span data-stu-id="42bc6-152">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="42bc6-153">**阶段 4：Azure 中用于高可用性联合身份验证基础结构的面向 Internet 的负载均衡器和 Web 应用程序代理服务器**</span><span class="sxs-lookup"><span data-stu-id="42bc6-153">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![在 Azure 中使用 web 应用程序代理服务器的高可用性 Microsoft 365 联合身份验证基础结构的第4阶段](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="42bc6-155">后续步骤</span><span class="sxs-lookup"><span data-stu-id="42bc6-155">Next step</span></span>

<span data-ttu-id="42bc6-156">使用[阶段5：为 Microsoft 365 配置联合身份验证](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)以继续配置此工作负载。</span><span class="sxs-lookup"><span data-stu-id="42bc6-156">Use [Phase 5: Configure federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="42bc6-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42bc6-157">See Also</span></span>

[<span data-ttu-id="42bc6-158">在 Azure 中为 Microsoft 365 部署高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="42bc6-158">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="42bc6-159">Microsoft 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="42bc6-159">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[<span data-ttu-id="42bc6-160">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="42bc6-160">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)

