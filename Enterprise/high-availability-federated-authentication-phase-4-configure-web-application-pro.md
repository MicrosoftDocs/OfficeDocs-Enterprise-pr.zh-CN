---
title: 高可用性联合身份验证阶段 4 配置 web 应用程序代理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 摘要： 配置 Microsoft Azure 中的 Office 365 您高可用性联合身份验证的 web 应用程序代理服务器。
ms.openlocfilehash: 0f0299fe8fecdea608330eebc12aea01098f8cec
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915807"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="8efb8-103">高可用性联合身份验证阶段 4:配置 Web 应用程序代理</span><span class="sxs-lookup"><span data-stu-id="8efb8-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

 <span data-ttu-id="8efb8-104">**摘要：** 在 Microsoft Azure 中配置的 web 应用程序代理服务器的 Office 365 您高可用性联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="8efb8-104">**Summary:** Configure the web application proxy servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="8efb8-105">在为 Azure 基础结构服务中的 Office 365 联合身份验证部署高可用性的这一阶段中，创建一个内部负载均衡器和两个 AD FS 服务器。</span><span class="sxs-lookup"><span data-stu-id="8efb8-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="8efb8-p101">您必须完成之后才能接着到此阶段[高可用性联合身份验证阶段 5： 配置适用于 Office 365 联合身份验证](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)。为所有阶段，请参阅[在 Azure 中的 Office 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="8efb8-p101">You must complete this phase before moving on to [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="8efb8-108">在 Azure 中创建面向 Internet 的负载均衡器</span><span class="sxs-lookup"><span data-stu-id="8efb8-108">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="8efb8-109">必须创建面向 Internet 的负载均衡器，以便 Azure 在两个 Web 应用程序代理服务器之间平均分发来自 Internet 的传入客户端身份验证通信。</span><span class="sxs-lookup"><span data-stu-id="8efb8-109">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8efb8-p102">下面的命令集使用最新版 Azure PowerShell。请参阅 [Azure PowerShell cmdlet 使用入门](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)。</span><span class="sxs-lookup"><span data-stu-id="8efb8-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="8efb8-112">提供位置和资源组值后，在 Azure PowerShell 命令提示符处或 PowerShell ISE 中运行生成块。</span><span class="sxs-lookup"><span data-stu-id="8efb8-112">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="8efb8-113">对于包含所有这篇文章并生成即点即已准备 PowerShell 命令块，根据您的自定义设置 Microsoft Excel 配置工作簿中的 PowerShell 命令的文本文件，请参阅[联合身份验证的 Office 365 中的Azure 部署工具包](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)。</span><span class="sxs-lookup"><span data-stu-id="8efb8-113">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzureRmPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzureRmLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzureRMLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzureRMLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzureRMLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="8efb8-114">若要显示分配给面向 Internet 的负载均衡器的公用 IP 地址，请在本地计算机上的 Azure PowerShell 命令提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="8efb8-114">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="8efb8-115">确定联合身份验证服务 FQDN 并创建 DNS 记录</span><span class="sxs-lookup"><span data-stu-id="8efb8-115">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="8efb8-p103">需要确定 DNS 名称以在 Internet 上标识联合身份验证服务名称。Azure AD Connect 将在阶段 5 中使用此名称来配置 Office 365，该名称将成为 Office 365 发送到连接客户端以获取安全令牌的 URL 的一部分。例如，fs.contoso.com（fs 代表联合身份验证服务）。</span><span class="sxs-lookup"><span data-stu-id="8efb8-p103">You need to determine the DNS name to identify your federation service name on the Internet. Azure AD Connect will configure Office 365 with this name in Phase 5, which will become part of the URL that Office 365 sends to connecting clients to get a security token. An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="8efb8-119">在拥有联合身份验证服务 FDQN 之后，创建联合身份验证服务 FDQN 的公用 DNS 域 A 记录，该完全限定的域名可解析为面向 Internet 的 Azure 负载均衡器的公用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="8efb8-119">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="8efb8-120">**名称**</span><span class="sxs-lookup"><span data-stu-id="8efb8-120">**Name**</span></span>|<span data-ttu-id="8efb8-121">**类型**</span><span class="sxs-lookup"><span data-stu-id="8efb8-121">**Type**</span></span>|<span data-ttu-id="8efb8-122">**TTL**</span><span class="sxs-lookup"><span data-stu-id="8efb8-122">**TTL**</span></span>|<span data-ttu-id="8efb8-123">**值**</span><span class="sxs-lookup"><span data-stu-id="8efb8-123">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="8efb8-124">联合身份验证服务 FDQN</span><span class="sxs-lookup"><span data-stu-id="8efb8-124">federation service FDQN</span></span>  <br/> |<span data-ttu-id="8efb8-125">A</span><span class="sxs-lookup"><span data-stu-id="8efb8-125">A</span></span>  <br/> |<span data-ttu-id="8efb8-126">3600</span><span class="sxs-lookup"><span data-stu-id="8efb8-126">3600</span></span>  <br/> |<span data-ttu-id="8efb8-127">面向 Internet 的 Azure 负载均衡器的公用 IP 地址（通过上一节中的 **Write-Host** 命令显示)</span><span class="sxs-lookup"><span data-stu-id="8efb8-127">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="8efb8-128">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="8efb8-128">Here is an example:</span></span>
  
|<span data-ttu-id="8efb8-129">**名称**</span><span class="sxs-lookup"><span data-stu-id="8efb8-129">**Name**</span></span>|<span data-ttu-id="8efb8-130">**类型**</span><span class="sxs-lookup"><span data-stu-id="8efb8-130">**Type**</span></span>|<span data-ttu-id="8efb8-131">**TTL**</span><span class="sxs-lookup"><span data-stu-id="8efb8-131">**TTL**</span></span>|<span data-ttu-id="8efb8-132">**值**</span><span class="sxs-lookup"><span data-stu-id="8efb8-132">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="8efb8-133">fs.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8efb8-133">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="8efb8-134">A</span><span class="sxs-lookup"><span data-stu-id="8efb8-134">A</span></span>  <br/> |<span data-ttu-id="8efb8-135">3600</span><span class="sxs-lookup"><span data-stu-id="8efb8-135">3600</span></span>  <br/> |<span data-ttu-id="8efb8-136">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="8efb8-136">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="8efb8-137">接下来，将一个 DNS 地址记录添加到组织的专用 DNS 命名空间，以将联合身份验证服务 FQDN 解析为分配给 AD FS 服务器（表 I，第 4 项，值列）的内部负载均衡器的专用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="8efb8-137">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="8efb8-138">在 Azure 中创建 Web 应用程序代理服务器虚拟机</span><span class="sxs-lookup"><span data-stu-id="8efb8-138">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="8efb8-139">使用下面的 Azure PowerShell 命令块为两个 Web 应用程序代理服务器创建虚拟机。 </span><span class="sxs-lookup"><span data-stu-id="8efb8-139">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="8efb8-140">请注意，以下 Azure PowerShell 命令集使用下表中的值：</span><span class="sxs-lookup"><span data-stu-id="8efb8-140">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="8efb8-141">表 M，用于虚拟机</span><span class="sxs-lookup"><span data-stu-id="8efb8-141">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="8efb8-142">表 R，用于资源组</span><span class="sxs-lookup"><span data-stu-id="8efb8-142">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="8efb8-143">表 V，用于虚拟网络设置</span><span class="sxs-lookup"><span data-stu-id="8efb8-143">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="8efb8-144">表 S，用于子网</span><span class="sxs-lookup"><span data-stu-id="8efb8-144">Table S, for your subnets</span></span>
    
- <span data-ttu-id="8efb8-145">表 I，用于静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="8efb8-145">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="8efb8-146">表 A（针对可用性集）</span><span class="sxs-lookup"><span data-stu-id="8efb8-146">Table A, for your availability sets</span></span>
    
<span data-ttu-id="8efb8-147">撤回您定义中的表 M[高可用性联合身份验证第 2 阶段： 配置域控制器](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)和表 R、 V、 S、 I 和中的[高可用性联合身份验证第 1 阶段： 配置 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="8efb8-147">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="8efb8-148">提供所有正确值后，在 Azure PowerShell 命令提示符处或 PowerShell ISE 上运行生成块。</span><span class="sxs-lookup"><span data-stu-id="8efb8-148">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzureRMVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="8efb8-p104">由于这些虚拟机 intranet 应用程序，它们不是分配公共 IP 地址或 DNS 域名称标签，向 Internet 公开。但是，这也意味着，您无法从 Azure 门户连接到它们。查看虚拟机的属性时，**连接**选项不可用。使用远程桌面连接附件或另一个远程桌面工具连接到虚拟机使用其专用 IP 地址或 intranet DNS 名称和本地管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="8efb8-p104">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="8efb8-153">以下是因成功完成这一阶段后生成的配置，包含占位符计算机名称。</span><span class="sxs-lookup"><span data-stu-id="8efb8-153">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="8efb8-154">**阶段 4：Azure 中用于高可用性联合身份验证基础结构的面向 Internet 的负载均衡器和 Web 应用程序代理服务器**</span><span class="sxs-lookup"><span data-stu-id="8efb8-154">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![阶段 4：在包含 Web 应用程序代理服务器的 Azure 中配置高可用性 Office 365 联合身份验证基础结构](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="8efb8-156">后续步骤</span><span class="sxs-lookup"><span data-stu-id="8efb8-156">Next step</span></span>

<span data-ttu-id="8efb8-157">使用[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)继续配置此工作负载。</span><span class="sxs-lookup"><span data-stu-id="8efb8-157">Use [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8efb8-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8efb8-158">See Also</span></span>

[<span data-ttu-id="8efb8-159">在 Azure 中部署 Office 365 的高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="8efb8-159">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="8efb8-160">用于 Office 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="8efb8-160">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="8efb8-161">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="8efb8-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="8efb8-162">联合身份验证选项</span><span class="sxs-lookup"><span data-stu-id="8efb8-162">Federated authentication options</span></span>](about-office-365-identity.md#federated-authentication-options)


