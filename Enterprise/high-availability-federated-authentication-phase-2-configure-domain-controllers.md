---
title: 高可用性联合身份验证阶段 2 配置域控制器
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 摘要：在 Microsoft Azure 中为 Office 365 的高可用性联合身份验证配置域控制器和目录同步服务器。
ms.openlocfilehash: 88e96c8173a209eb9a0a371b65eacda769e1f50f
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897215"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="ffa19-103">高可用性联合身份验证阶段 2：配置域控制器</span><span class="sxs-lookup"><span data-stu-id="ffa19-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

 <span data-ttu-id="ffa19-104">**摘要：** 在 Microsoft Azure 中为 Office 365 的高可用性联合身份验证配置域控制器和目录同步服务器。</span><span class="sxs-lookup"><span data-stu-id="ffa19-104">**Summary:** Configure the domain controllers and DirSync server for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="ffa19-p101">在为 Azure 基础结构服务中的 Office 365 联合身份验证部署高可用性的这一阶段中，可以在 Azure 虚拟网络中配置两个域控制器和目录同步服务器。然后用于身份验证的客户端 Web 请求可以在 Azure 虚拟网络中进行身份验证，而不是将通过站点到站点 VPN 连接的该身份验证流量发送到本地网络。</span><span class="sxs-lookup"><span data-stu-id="ffa19-p101">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the DirSync server in the Azure virtual network. Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ffa19-107">Active Directory 联合身份验证服务 (AD FS) 不能用 Azure Active Directory 域服务代替 Windows Server AD 域控制器。</span><span class="sxs-lookup"><span data-stu-id="ffa19-107">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Windows Server AD domain controllers.</span></span> 
  
<span data-ttu-id="ffa19-p102">您必须完成之后才能接着到此阶段[高可用性联合身份验证第 3 阶段： 配置 AD FS 服务器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)。为所有阶段，请参阅[在 Azure 中的 Office 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="ffa19-p102">You must complete this phase before moving on to [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="ffa19-110">在 Azure 中创建域控制器虚拟机</span><span class="sxs-lookup"><span data-stu-id="ffa19-110">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="ffa19-111">首先，需要填写表 M 的 **虚拟机名称** 列，并根据需要在 **最小大小** 列修改虚拟机大小。</span><span class="sxs-lookup"><span data-stu-id="ffa19-111">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="ffa19-112">**项**</span><span class="sxs-lookup"><span data-stu-id="ffa19-112">**Item**</span></span>|<span data-ttu-id="ffa19-113">**虚拟机名称**</span><span class="sxs-lookup"><span data-stu-id="ffa19-113">**Virtual machine name**</span></span>|<span data-ttu-id="ffa19-114">**库图像**</span><span class="sxs-lookup"><span data-stu-id="ffa19-114">**Gallery image**</span></span>|<span data-ttu-id="ffa19-115">**存储类型**</span><span class="sxs-lookup"><span data-stu-id="ffa19-115">**Storage type**</span></span>|<span data-ttu-id="ffa19-116">**最小大小**</span><span class="sxs-lookup"><span data-stu-id="ffa19-116">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="ffa19-117">1.</span><span class="sxs-lookup"><span data-stu-id="ffa19-117">1.</span></span>  <br/> |<span data-ttu-id="ffa19-118">![](./media/Common-Images/TableLine.png)（第一个域控制器，例如 DC1）</span><span class="sxs-lookup"><span data-stu-id="ffa19-118">![](./media/Common-Images/TableLine.png) (first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="ffa19-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ffa19-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ffa19-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ffa19-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ffa19-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ffa19-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="ffa19-122">2.</span><span class="sxs-lookup"><span data-stu-id="ffa19-122">2.</span></span>  <br/> |<span data-ttu-id="ffa19-123">![](./media/Common-Images/TableLine.png)（第二个域控制器，例如 DC2）</span><span class="sxs-lookup"><span data-stu-id="ffa19-123">![](./media/Common-Images/TableLine.png) (second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="ffa19-124">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ffa19-124">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ffa19-125">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ffa19-125">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ffa19-126">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ffa19-126">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="ffa19-127">3.</span><span class="sxs-lookup"><span data-stu-id="ffa19-127">3.</span></span>  <br/> |<span data-ttu-id="ffa19-128">![](./media/Common-Images/TableLine.png)（目录同步服务器，示例 DS1）</span><span class="sxs-lookup"><span data-stu-id="ffa19-128">![](./media/Common-Images/TableLine.png) (DirSync server, example DS1)</span></span>  <br/> |<span data-ttu-id="ffa19-129">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ffa19-129">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ffa19-130">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ffa19-130">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ffa19-131">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ffa19-131">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="ffa19-132">4.</span><span class="sxs-lookup"><span data-stu-id="ffa19-132">4.</span></span>  <br/> |<span data-ttu-id="ffa19-133">![](./media/Common-Images/TableLine.png)（第一台 AD FS 服务器，示例 ADFS1）</span><span class="sxs-lookup"><span data-stu-id="ffa19-133">![](./media/Common-Images/TableLine.png) (first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="ffa19-134">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ffa19-134">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ffa19-135">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ffa19-135">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ffa19-136">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ffa19-136">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="ffa19-137">5.</span><span class="sxs-lookup"><span data-stu-id="ffa19-137">5.</span></span>  <br/> |<span data-ttu-id="ffa19-138">![](./media/Common-Images/TableLine.png)（第二个 AD FS 服务器，示例 ADFS2）</span><span class="sxs-lookup"><span data-stu-id="ffa19-138">![](./media/Common-Images/TableLine.png) (second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="ffa19-139">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ffa19-139">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ffa19-140">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ffa19-140">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ffa19-141">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ffa19-141">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="ffa19-142">6.</span><span class="sxs-lookup"><span data-stu-id="ffa19-142">6.</span></span>  <br/> |<span data-ttu-id="ffa19-143">![](./media/Common-Images/TableLine.png)（第一个 web 应用程序代理服务器，示例 WEB1）</span><span class="sxs-lookup"><span data-stu-id="ffa19-143">![](./media/Common-Images/TableLine.png) (first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="ffa19-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ffa19-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ffa19-145">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ffa19-145">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ffa19-146">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ffa19-146">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="ffa19-147">7.</span><span class="sxs-lookup"><span data-stu-id="ffa19-147">7.</span></span>  <br/> |<span data-ttu-id="ffa19-148">![](./media/Common-Images/TableLine.png)（第二个 web 应用程序代理服务器，示例 WEB2）</span><span class="sxs-lookup"><span data-stu-id="ffa19-148">![](./media/Common-Images/TableLine.png) (second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="ffa19-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ffa19-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ffa19-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ffa19-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ffa19-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ffa19-151">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="ffa19-152">**表 M-Azure 中的 Office 365 的高可用性联合身份验证的虚拟机**</span><span class="sxs-lookup"><span data-stu-id="ffa19-152">**Table M - Virtual machines for the high availability federated authentication for Office 365 in Azure**</span></span>
  
<span data-ttu-id="ffa19-153">有关虚拟机大小的完整列表，请参阅[虚拟机的大小](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)。</span><span class="sxs-lookup"><span data-stu-id="ffa19-153">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="ffa19-p103">下面的 Azure PowerShell 命令块创建虚拟机的两个域控制器。指定的值的变量，删除\<和 > 字符。请注意此 Azure PowerShell 命令块，使用下表中的值：</span><span class="sxs-lookup"><span data-stu-id="ffa19-p103">The following Azure PowerShell command block creates the virtual machines for the two domain controllers. Specify the values for the variables, removing the \< and > characters. Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="ffa19-157">表 M，用于虚拟机</span><span class="sxs-lookup"><span data-stu-id="ffa19-157">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="ffa19-158">表 R，用于资源组</span><span class="sxs-lookup"><span data-stu-id="ffa19-158">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="ffa19-159">表 V，用于虚拟网络设置</span><span class="sxs-lookup"><span data-stu-id="ffa19-159">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="ffa19-160">表 S，用于子网</span><span class="sxs-lookup"><span data-stu-id="ffa19-160">Table S, for your subnets</span></span>
    
- <span data-ttu-id="ffa19-161">表 I，用于静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="ffa19-161">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="ffa19-162">表 A（针对可用性集）</span><span class="sxs-lookup"><span data-stu-id="ffa19-162">Table A, for your availability sets</span></span>
    
<span data-ttu-id="ffa19-163">撤回您定义表 R、 V、 S、 I 和中的[高可用性联合身份验证第 1 阶段： 配置 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="ffa19-163">Recall that you defined Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="ffa19-p104">下面的命令集使用最新版 Azure PowerShell。请参阅 [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)（Azure PowerShell cmdlet 使用入门）。</span><span class="sxs-lookup"><span data-stu-id="ffa19-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="ffa19-166">提供所有正确值后，在 Azure PowerShell 提示符处或本地计算机的 PowerShell 集成脚本环境 (ISE) 上运行生成块。</span><span class="sxs-lookup"><span data-stu-id="ffa19-166">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="ffa19-167">对于所有这篇文章并生成即点即已准备 PowerShell 命令块，根据您的自定义设置 Microsoft Excel 配置工作簿中的 PowerShell 命令的文本文件，请参阅在 Azure 中的[for Office 365 联合身份验证部署工具包](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)。</span><span class="sxs-lookup"><span data-stu-id="ffa19-167">For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="ffa19-p105">由于这些虚拟机 intranet 应用程序，它们不是分配公共 IP 地址或 DNS 域名称标签，向 Internet 公开。但是，这也意味着，您无法从 Azure 门户连接到它们。查看虚拟机的属性时，**连接**选项不可用。使用远程桌面连接附件或另一个远程桌面工具连接到虚拟机使用其专用 IP 地址或 intranet DNS 名称。</span><span class="sxs-lookup"><span data-stu-id="ffa19-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="ffa19-172">配置第一个域控制器</span><span class="sxs-lookup"><span data-stu-id="ffa19-172">Configure the first domain controller</span></span>

<span data-ttu-id="ffa19-p106">使用你选择的远程桌面客户端并创建到第一个域控制器虚拟机的远程桌面连接。使用其 Intranet DNS 或计算机名称以及本地管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="ffa19-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="ffa19-175">接下来，从 Windows PowerShell 命令提示符**上第一个域控制器虚拟机**添加到使用此命令的第一个域控制器的额外数据磁盘：</span><span class="sxs-lookup"><span data-stu-id="ffa19-175">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="ffa19-176">接下来，使用 **ping** 命令对组织网络中的资源名称和 IP 地址执行 ping 操作，测试第一个域控制器到组织网络中的位置的连接。</span><span class="sxs-lookup"><span data-stu-id="ffa19-176">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="ffa19-p107">此过程确保 DNS 名称解析正常进行（已为该虚拟机正确配置本地 DNS 服务器），并可以向/从跨本地虚拟网络发送数据。如果这个基本测试失败，请与你的 IT 部门联系，来解决 DNS 名称解析和数据包传递问题。</span><span class="sxs-lookup"><span data-stu-id="ffa19-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="ffa19-179">接下来，从第一个域控制器的 Windows PowerShell 命令提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ffa19-179">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="ffa19-p108">系统将提示你提供域管理员帐户的凭据。计算机将重新启动。</span><span class="sxs-lookup"><span data-stu-id="ffa19-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="ffa19-182">配置第二个域控制器</span><span class="sxs-lookup"><span data-stu-id="ffa19-182">Configure the second domain controller</span></span>

<span data-ttu-id="ffa19-p109">使用你选择的远程桌面客户端并创建到第二个域控制器虚拟机的远程桌面连接。使用其 Intranet DNS 或计算机名称以及本地管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="ffa19-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="ffa19-185">接下来，您需要从 Windows PowerShell 命令提示符处**第二个域控制器虚拟机上**，向使用此命令的第二个域控制器中添加额外数据磁盘：</span><span class="sxs-lookup"><span data-stu-id="ffa19-185">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="ffa19-186">接下来，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ffa19-186">Next, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="ffa19-p110">系统将提示你提供域管理员帐户的凭据。计算机将重新启动。</span><span class="sxs-lookup"><span data-stu-id="ffa19-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="ffa19-p111">接下来，您需要更新的 DNS 服务器的虚拟网络，以便该 Azure 分配虚拟机的两个新的域控制器，以用作其 DNS 服务器的 IP 地址。填写变量，然后在本地计算机上从 Windows PowerShell 命令提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ffa19-p111">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers. Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzureRMVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="ffa19-p112">请注意，我们重新启动两个域控制器，这样不会为它们配置本地 DNS 服务器作为 DNS 服务器。因为这两个控制器本身就是 DNS 服务器，因此在升级为域控制器后会自动为它们配置本地 DNS 服务器作为 DNS 转发器。</span><span class="sxs-lookup"><span data-stu-id="ffa19-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="ffa19-p113">接下来，我们需要创建一个 Active Directory 复制站点以确保 Azure 虚拟网络中的服务器使用本地域控制器。使用域管理员帐户连接到任一域控制器，从管理员级 Windows PowerShell 提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ffa19-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a><span data-ttu-id="ffa19-195">配置目录同步服务器</span><span class="sxs-lookup"><span data-stu-id="ffa19-195">Configure the DirSync server</span></span>

<span data-ttu-id="ffa19-p114">使用您选择的远程桌面客户端并创建远程桌面连接到目录同步服务器虚拟机。使用其 intranet DNS 或计算机名称和本地管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="ffa19-p114">Use the remote desktop client of your choice and create a remote desktop connection to the DirSync server virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="ffa19-198">接下来，通过 Windows PowerShell 提示符下的这些命令将其加入相应的 Windows Server AD 域。</span><span class="sxs-lookup"><span data-stu-id="ffa19-198">Next, join it to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="ffa19-199">以下是因成功完成这一阶段后生成的配置，包含占位符计算机名称。</span><span class="sxs-lookup"><span data-stu-id="ffa19-199">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="ffa19-200">**阶段 2：Azure 中用于高可用性联合身份验证基础结构的域控制器和目录同步服务器**</span><span class="sxs-lookup"><span data-stu-id="ffa19-200">**Phase 2: The domain controllers and DirSync server for your high availability federated authentication infrastructure in Azure**</span></span>

![阶段 2：在包含域控制器的 Azure 中配置高可用性 Office 365 联合身份验证基础结构](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="ffa19-202">后续步骤</span><span class="sxs-lookup"><span data-stu-id="ffa19-202">Next step</span></span>

<span data-ttu-id="ffa19-203">使用[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)继续配置此工作负载。</span><span class="sxs-lookup"><span data-stu-id="ffa19-203">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ffa19-204">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ffa19-204">See Also</span></span>

[<span data-ttu-id="ffa19-205">在 Azure 中部署 Office 365 的高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="ffa19-205">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="ffa19-206">用于 Office 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="ffa19-206">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="ffa19-207">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="ffa19-207">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="ffa19-208">联合身份验证选项</span><span class="sxs-lookup"><span data-stu-id="ffa19-208">Federated authentication options</span></span>](about-office-365-identity.md#federated-authentication-options)


