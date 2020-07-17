---
title: 高可用性联合身份验证阶段2配置域控制器
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
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 摘要：为 microsoft Azure 中的 Microsoft 365 的高可用性联合身份验证配置域控制器和目录同步服务器。
ms.openlocfilehash: 14939691e8dc114a6234bfee1ade7212762eae04
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102520"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="a3d88-103">高可用性联合身份验证阶段 2：配置域控制器</span><span class="sxs-lookup"><span data-stu-id="a3d88-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

<span data-ttu-id="a3d88-104">在此阶段，在 Azure 基础结构服务中为 Microsoft 365 联合身份验证部署高可用性时，需要在 Azure 虚拟网络中配置两个域控制器和目录同步服务器。</span><span class="sxs-lookup"><span data-stu-id="a3d88-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the directory synchronization server in the Azure virtual network.</span></span> <span data-ttu-id="a3d88-105">然后用于身份验证的客户端 Web 请求可以在 Azure 虚拟网络中进行身份验证，而不是将通过站点到站点 VPN 连接的该身份验证流量发送到本地网络。</span><span class="sxs-lookup"><span data-stu-id="a3d88-105">Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a3d88-106">Active Directory 联合身份验证服务 (AD FS) 无法使用 Azure Active Directory (Azure AD) 以替代 Active Directory 域服务 (AD DS) 域控制器。</span><span class="sxs-lookup"><span data-stu-id="a3d88-106">Active Directory Federation Services (AD FS) cannot use Azure Active Directory (Azure AD) as a substitute for Active Directory Domain Services (AD DS) domain controllers.</span></span> 
  
<span data-ttu-id="a3d88-107">在转到[第3阶段：配置 AD FS 服务器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)之前，您必须完成此阶段。</span><span class="sxs-lookup"><span data-stu-id="a3d88-107">You must complete this phase before moving on to [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span></span> <span data-ttu-id="a3d88-108">有关所有阶段，请参阅[在 Azure 中为 Microsoft 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d88-108">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="a3d88-109">在 Azure 中创建域控制器虚拟机</span><span class="sxs-lookup"><span data-stu-id="a3d88-109">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="a3d88-110">首先，需要填写表 M 的 **虚拟机名称** 列，并根据需要在 **最小大小** 列修改虚拟机大小。</span><span class="sxs-lookup"><span data-stu-id="a3d88-110">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="a3d88-111">**项**</span><span class="sxs-lookup"><span data-stu-id="a3d88-111">**Item**</span></span>|<span data-ttu-id="a3d88-112">**虚拟机名称**</span><span class="sxs-lookup"><span data-stu-id="a3d88-112">**Virtual machine name**</span></span>|<span data-ttu-id="a3d88-113">**库图像**</span><span class="sxs-lookup"><span data-stu-id="a3d88-113">**Gallery image**</span></span>|<span data-ttu-id="a3d88-114">**存储类型**</span><span class="sxs-lookup"><span data-stu-id="a3d88-114">**Storage type**</span></span>|<span data-ttu-id="a3d88-115">**最小大小**</span><span class="sxs-lookup"><span data-stu-id="a3d88-115">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="a3d88-116">1.</span><span class="sxs-lookup"><span data-stu-id="a3d88-116">1.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="a3d88-118">（第一个域控制器，例如 DC1）</span><span class="sxs-lookup"><span data-stu-id="a3d88-118">(first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="a3d88-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a3d88-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a3d88-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="a3d88-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="a3d88-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="a3d88-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="a3d88-122">2.</span><span class="sxs-lookup"><span data-stu-id="a3d88-122">2.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="a3d88-124">（第二个域控制器，例如 DC2）</span><span class="sxs-lookup"><span data-stu-id="a3d88-124">(second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="a3d88-125">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a3d88-125">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a3d88-126">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="a3d88-126">Standard_LRS</span></span>  <br/> |<span data-ttu-id="a3d88-127">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="a3d88-127">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="a3d88-128">3.</span><span class="sxs-lookup"><span data-stu-id="a3d88-128">3.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="a3d88-130"> (目录同步服务器，示例 DS1) </span><span class="sxs-lookup"><span data-stu-id="a3d88-130">(directory synchronization server, example DS1)</span></span>  <br/> |<span data-ttu-id="a3d88-131">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a3d88-131">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a3d88-132">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="a3d88-132">Standard_LRS</span></span>  <br/> |<span data-ttu-id="a3d88-133">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="a3d88-133">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="a3d88-134">4.</span><span class="sxs-lookup"><span data-stu-id="a3d88-134">4.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="a3d88-136"> (第一个 AD FS 服务器，示例 ADFS1) </span><span class="sxs-lookup"><span data-stu-id="a3d88-136">(first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="a3d88-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a3d88-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a3d88-138">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="a3d88-138">Standard_LRS</span></span>  <br/> |<span data-ttu-id="a3d88-139">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="a3d88-139">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="a3d88-140">5.</span><span class="sxs-lookup"><span data-stu-id="a3d88-140">5.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="a3d88-142"> (第二个 AD FS 服务器，示例 ADFS2) </span><span class="sxs-lookup"><span data-stu-id="a3d88-142">(second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="a3d88-143">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a3d88-143">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a3d88-144">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="a3d88-144">Standard_LRS</span></span>  <br/> |<span data-ttu-id="a3d88-145">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="a3d88-145">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="a3d88-146">6.</span><span class="sxs-lookup"><span data-stu-id="a3d88-146">6.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="a3d88-148"> (第一个 web 应用程序代理服务器，示例 WEB1) </span><span class="sxs-lookup"><span data-stu-id="a3d88-148">(first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="a3d88-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a3d88-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a3d88-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="a3d88-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="a3d88-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="a3d88-151">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="a3d88-152">7.</span><span class="sxs-lookup"><span data-stu-id="a3d88-152">7.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="a3d88-154"> (第二个 web 应用程序代理服务器，示例 WEB2) </span><span class="sxs-lookup"><span data-stu-id="a3d88-154">(second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="a3d88-155">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="a3d88-155">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="a3d88-156">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="a3d88-156">Standard_LRS</span></span>  <br/> |<span data-ttu-id="a3d88-157">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="a3d88-157">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="a3d88-158">**表 M-Azure 中适用于 Microsoft 365 的高可用性联合身份验证的虚拟机**</span><span class="sxs-lookup"><span data-stu-id="a3d88-158">**Table M - Virtual machines for the high availability federated authentication for Microsoft 365 in Azure**</span></span>
  
<span data-ttu-id="a3d88-159">有关虚拟机大小的完整列表，请参阅[虚拟机的大小](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)。</span><span class="sxs-lookup"><span data-stu-id="a3d88-159">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="a3d88-160">以下 Azure PowerShell 命令块可创建两个域控制器的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="a3d88-160">The following Azure PowerShell command block creates the virtual machines for the two domain controllers.</span></span> <span data-ttu-id="a3d88-161">指定变量的值，并删除 \< and > 字符。</span><span class="sxs-lookup"><span data-stu-id="a3d88-161">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="a3d88-162">请注意，此 Azure PowerShell 命令块使用下表中的值：</span><span class="sxs-lookup"><span data-stu-id="a3d88-162">Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="a3d88-163">表 M，用于虚拟机</span><span class="sxs-lookup"><span data-stu-id="a3d88-163">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="a3d88-164">表 R，用于资源组</span><span class="sxs-lookup"><span data-stu-id="a3d88-164">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="a3d88-165">表 V，用于虚拟网络设置</span><span class="sxs-lookup"><span data-stu-id="a3d88-165">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="a3d88-166">表 S，用于子网</span><span class="sxs-lookup"><span data-stu-id="a3d88-166">Table S, for your subnets</span></span>
    
- <span data-ttu-id="a3d88-167">表 I，用于静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="a3d88-167">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="a3d88-168">表 A（针对可用性集）</span><span class="sxs-lookup"><span data-stu-id="a3d88-168">Table A, for your availability sets</span></span>
    
<span data-ttu-id="a3d88-169">回想一下您在[第1阶段： Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md)中定义了表 R、V、S、I 和 A。</span><span class="sxs-lookup"><span data-stu-id="a3d88-169">Recall that you defined Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="a3d88-170">[!注意] 下面的命令集使用最新版 Azure PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a3d88-170">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="a3d88-171">请参阅[Azure PowerShell 入门](https://docs.microsoft.com/powershell/azure/get-started-azureps)。</span><span class="sxs-lookup"><span data-stu-id="a3d88-171">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="a3d88-172">提供所有正确值后，在 Azure PowerShell 提示符处或本地计算机的 PowerShell 集成脚本环境 (ISE) 上运行生成块。</span><span class="sxs-lookup"><span data-stu-id="a3d88-172">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="a3d88-173">若要基于自定义设置生成可随时运行的 PowerShell 命令块，请使用此[Microsoft Excel 配置工作簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx)。</span><span class="sxs-lookup"><span data-stu-id="a3d88-173">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Active Directory Domain Services (AD DS) data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for AD DS data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the directory synchronization server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the directory synchronization server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="a3d88-p105">由于这些虚拟机用于 Intranet 应用程序，所以不会为它们分配公用 IP 地址或 DNS 域名称标签，也不会将它们公开到 Internet。但是，这也意味着你无法从 Azure 门户与它们进行连接。查看虚拟机的属性时“连接”\*\*\*\* 选项不可用。使用远程桌面连接附件或另一个远程桌面工具连接使用其专用 IP 地址或 Intranet DNS 名称的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="a3d88-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="a3d88-178">配置第一个域控制器</span><span class="sxs-lookup"><span data-stu-id="a3d88-178">Configure the first domain controller</span></span>

<span data-ttu-id="a3d88-p106">使用你选择的远程桌面客户端并创建到第一个域控制器虚拟机的远程桌面连接。使用其 Intranet DNS 或计算机名称以及本地管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="a3d88-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="a3d88-181">接下来，使用**第一个域控制器虚拟机上**的 Windows PowerShell 命令提示符将额外的数据磁盘添加到第一个域控制器中：</span><span class="sxs-lookup"><span data-stu-id="a3d88-181">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="a3d88-182">接下来，使用 **ping** 命令对组织网络中的资源名称和 IP 地址执行 ping 操作，测试第一个域控制器到组织网络中的位置的连接。</span><span class="sxs-lookup"><span data-stu-id="a3d88-182">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="a3d88-p107">此过程确保 DNS 名称解析正常进行（已为该虚拟机正确配置本地 DNS 服务器），并可以向/从跨本地虚拟网络发送数据。如果这个基本测试失败，请与你的 IT 部门联系，来解决 DNS 名称解析和数据包传递问题。</span><span class="sxs-lookup"><span data-stu-id="a3d88-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="a3d88-185">接下来，从第一个域控制器的 Windows PowerShell 命令提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a3d88-185">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="a3d88-p108">系统将提示你提供域管理员帐户的凭据。计算机将重新启动。</span><span class="sxs-lookup"><span data-stu-id="a3d88-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="a3d88-188">配置第二个域控制器</span><span class="sxs-lookup"><span data-stu-id="a3d88-188">Configure the second domain controller</span></span>

<span data-ttu-id="a3d88-p109">使用你选择的远程桌面客户端并创建到第二个域控制器虚拟机的远程桌面连接。使用其 Intranet DNS 或计算机名称以及本地管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="a3d88-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="a3d88-191">接下来，您需要使用**第二个域控制器虚拟机上**的 Windows PowerShell 命令提示符中的此命令将额外的数据磁盘添加到第二个域控制器中：</span><span class="sxs-lookup"><span data-stu-id="a3d88-191">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="a3d88-192">接下来，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a3d88-192">Next, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="a3d88-p110">系统将提示你提供域管理员帐户的凭据。计算机将重新启动。</span><span class="sxs-lookup"><span data-stu-id="a3d88-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="a3d88-195">接下来，需要为虚拟网络更新 DNS 服务器，以便 Azure 为虚拟机分配两个新域控制器的 IP 地址，将它们用作其 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="a3d88-195">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers.</span></span> <span data-ttu-id="a3d88-196">填写变量，然后从本地计算机上的 Windows PowerShell 命令提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a3d88-196">Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
```powershell
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

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="a3d88-p112">请注意，我们重新启动两个域控制器，这样不会为它们配置本地 DNS 服务器作为 DNS 服务器。因为这两个控制器本身就是 DNS 服务器，因此在升级为域控制器后会自动为它们配置本地 DNS 服务器作为 DNS 转发器。</span><span class="sxs-lookup"><span data-stu-id="a3d88-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="a3d88-p113">接下来，我们需要创建一个 Active Directory 复制站点以确保 Azure 虚拟网络中的服务器使用本地域控制器。使用域管理员帐户连接到任一域控制器，从管理员级 Windows PowerShell 提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a3d88-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a><span data-ttu-id="a3d88-201">配置目录同步服务器</span><span class="sxs-lookup"><span data-stu-id="a3d88-201">Configure the directory synchronization server</span></span>

<span data-ttu-id="a3d88-202">使用您选择的远程桌面客户端并创建到目录同步服务器虚拟机的远程桌面连接。</span><span class="sxs-lookup"><span data-stu-id="a3d88-202">Use the remote desktop client of your choice and create a remote desktop connection to the directory synchronization server virtual machine.</span></span> <span data-ttu-id="a3d88-203">使用其 Intranet DNS 或计算机名称以及本地管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="a3d88-203">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="a3d88-204">接下来，通过 Windows PowerShell 提示符下的这些命令将其加入相应的 AD DS 域。</span><span class="sxs-lookup"><span data-stu-id="a3d88-204">Next, join it to the appropriate AD DS domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="a3d88-205">以下是因成功完成这一阶段后生成的配置，包含占位符计算机名称。</span><span class="sxs-lookup"><span data-stu-id="a3d88-205">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="a3d88-206">**第2阶段：适用于 Azure 中的高可用性联合身份验证基础结构的域控制器和目录同步服务器**</span><span class="sxs-lookup"><span data-stu-id="a3d88-206">**Phase 2: The domain controllers and directory synchronization server for your high availability federated authentication infrastructure in Azure**</span></span>

![具有域控制器的 Azure 中的高可用性 Microsoft 365 联合身份验证基础结构的第2阶段](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="a3d88-208">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a3d88-208">Next step</span></span>

<span data-ttu-id="a3d88-209">使用[阶段3：配置 AD FS 服务器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)以继续配置此工作负载。</span><span class="sxs-lookup"><span data-stu-id="a3d88-209">Use [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a3d88-210">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a3d88-210">See Also</span></span>

[<span data-ttu-id="a3d88-211">在 Azure 中为 Microsoft 365 部署高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="a3d88-211">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="a3d88-212">Microsoft 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="a3d88-212">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[<span data-ttu-id="a3d88-213">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="a3d88-213">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)


