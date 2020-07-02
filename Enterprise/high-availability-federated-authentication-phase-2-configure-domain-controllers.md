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
ms.openlocfilehash: c10fb2d32ea572280b43d32da56b9e4d6affa22a
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998050"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="62303-103">高可用性联合身份验证阶段 2：配置域控制器</span><span class="sxs-lookup"><span data-stu-id="62303-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

<span data-ttu-id="62303-104">在此阶段，在 Azure 基础结构服务中为 Microsoft 365 联合身份验证部署高可用性时，需要在 Azure 虚拟网络中配置两个域控制器和目录同步服务器。</span><span class="sxs-lookup"><span data-stu-id="62303-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the directory synchronization server in the Azure virtual network.</span></span> <span data-ttu-id="62303-105">然后用于身份验证的客户端 Web 请求可以在 Azure 虚拟网络中进行身份验证，而不是将通过站点到站点 VPN 连接的该身份验证流量发送到本地网络。</span><span class="sxs-lookup"><span data-stu-id="62303-105">Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="62303-106">Active Directory 联合身份验证服务（AD FS）无法使用 Azure Active Directory （Azure AD）替代 Active Directory 域服务（AD DS）域控制器。</span><span class="sxs-lookup"><span data-stu-id="62303-106">Active Directory Federation Services (AD FS) cannot use Azure Active Directory (Azure AD) as a substitute for Active Directory Domain Services (AD DS) domain controllers.</span></span> 
  
<span data-ttu-id="62303-107">在转到[第3阶段：配置 AD FS 服务器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)之前，您必须完成此阶段。</span><span class="sxs-lookup"><span data-stu-id="62303-107">You must complete this phase before moving on to [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span></span> <span data-ttu-id="62303-108">有关所有阶段，请参阅[在 Azure 中为 Microsoft 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="62303-108">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="62303-109">在 Azure 中创建域控制器虚拟机</span><span class="sxs-lookup"><span data-stu-id="62303-109">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="62303-110">首先，需要填写表 M 的 **虚拟机名称** 列，并根据需要在 **最小大小** 列修改虚拟机大小。</span><span class="sxs-lookup"><span data-stu-id="62303-110">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="62303-111">**项**</span><span class="sxs-lookup"><span data-stu-id="62303-111">**Item**</span></span>|<span data-ttu-id="62303-112">**虚拟机名称**</span><span class="sxs-lookup"><span data-stu-id="62303-112">**Virtual machine name**</span></span>|<span data-ttu-id="62303-113">**库图像**</span><span class="sxs-lookup"><span data-stu-id="62303-113">**Gallery image**</span></span>|<span data-ttu-id="62303-114">**存储类型**</span><span class="sxs-lookup"><span data-stu-id="62303-114">**Storage type**</span></span>|<span data-ttu-id="62303-115">**最小大小**</span><span class="sxs-lookup"><span data-stu-id="62303-115">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="62303-116">1.</span><span class="sxs-lookup"><span data-stu-id="62303-116">1.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="62303-118">（第一个域控制器，例如 DC1）</span><span class="sxs-lookup"><span data-stu-id="62303-118">(first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="62303-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="62303-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="62303-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="62303-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="62303-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="62303-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="62303-122">2.</span><span class="sxs-lookup"><span data-stu-id="62303-122">2.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="62303-124">（第二个域控制器，例如 DC2）</span><span class="sxs-lookup"><span data-stu-id="62303-124">(second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="62303-125">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="62303-125">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="62303-126">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="62303-126">Standard_LRS</span></span>  <br/> |<span data-ttu-id="62303-127">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="62303-127">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="62303-128">3.</span><span class="sxs-lookup"><span data-stu-id="62303-128">3.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="62303-130">（目录同步服务器，示例 DS1）</span><span class="sxs-lookup"><span data-stu-id="62303-130">(directory synchronization server, example DS1)</span></span>  <br/> |<span data-ttu-id="62303-131">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="62303-131">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="62303-132">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="62303-132">Standard_LRS</span></span>  <br/> |<span data-ttu-id="62303-133">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="62303-133">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="62303-134">4.</span><span class="sxs-lookup"><span data-stu-id="62303-134">4.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="62303-136">（第一个 AD FS 服务器，示例 ADFS1）</span><span class="sxs-lookup"><span data-stu-id="62303-136">(first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="62303-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="62303-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="62303-138">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="62303-138">Standard_LRS</span></span>  <br/> |<span data-ttu-id="62303-139">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="62303-139">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="62303-140">5.</span><span class="sxs-lookup"><span data-stu-id="62303-140">5.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="62303-142">（第二个 AD FS 服务器，示例 ADFS2）</span><span class="sxs-lookup"><span data-stu-id="62303-142">(second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="62303-143">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="62303-143">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="62303-144">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="62303-144">Standard_LRS</span></span>  <br/> |<span data-ttu-id="62303-145">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="62303-145">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="62303-146">6.</span><span class="sxs-lookup"><span data-stu-id="62303-146">6.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="62303-148">（第一个 web 应用程序代理服务器，示例 WEB1）</span><span class="sxs-lookup"><span data-stu-id="62303-148">(first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="62303-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="62303-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="62303-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="62303-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="62303-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="62303-151">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="62303-152">7.</span><span class="sxs-lookup"><span data-stu-id="62303-152">7.</span></span>  <br/> |![线条](./media/Common-Images/TableLine.png) <span data-ttu-id="62303-154">（第二个 web 应用程序代理服务器，示例 WEB2）</span><span class="sxs-lookup"><span data-stu-id="62303-154">(second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="62303-155">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="62303-155">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="62303-156">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="62303-156">Standard_LRS</span></span>  <br/> |<span data-ttu-id="62303-157">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="62303-157">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="62303-158">**表 M-Azure 中适用于 Microsoft 365 的高可用性联合身份验证的虚拟机**</span><span class="sxs-lookup"><span data-stu-id="62303-158">**Table M - Virtual machines for the high availability federated authentication for Microsoft 365 in Azure**</span></span>
  
<span data-ttu-id="62303-159">有关虚拟机大小的完整列表，请参阅[虚拟机的大小](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)。</span><span class="sxs-lookup"><span data-stu-id="62303-159">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="62303-160">以下 Azure PowerShell 命令块可创建两个域控制器的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="62303-160">The following Azure PowerShell command block creates the virtual machines for the two domain controllers.</span></span> <span data-ttu-id="62303-161">指定变量的值，并删除 \< and > 字符。</span><span class="sxs-lookup"><span data-stu-id="62303-161">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="62303-162">请注意，此 Azure PowerShell 命令块使用下表中的值：</span><span class="sxs-lookup"><span data-stu-id="62303-162">Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="62303-163">表 M，用于虚拟机</span><span class="sxs-lookup"><span data-stu-id="62303-163">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="62303-164">表 R，用于资源组</span><span class="sxs-lookup"><span data-stu-id="62303-164">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="62303-165">表 V，用于虚拟网络设置</span><span class="sxs-lookup"><span data-stu-id="62303-165">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="62303-166">表 S，用于子网</span><span class="sxs-lookup"><span data-stu-id="62303-166">Table S, for your subnets</span></span>
    
- <span data-ttu-id="62303-167">表 I，用于静态 IP 地址</span><span class="sxs-lookup"><span data-stu-id="62303-167">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="62303-168">表 A（针对可用性集）</span><span class="sxs-lookup"><span data-stu-id="62303-168">Table A, for your availability sets</span></span>
    
<span data-ttu-id="62303-169">回想一下您在[第1阶段： Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md)中定义了表 R、V、S、I 和 A。</span><span class="sxs-lookup"><span data-stu-id="62303-169">Recall that you defined Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="62303-170">[!注意] 下面的命令集使用最新版 Azure PowerShell。</span><span class="sxs-lookup"><span data-stu-id="62303-170">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="62303-171">请参阅[Azure PowerShell 入门](https://docs.microsoft.com/powershell/azure/get-started-azureps)。</span><span class="sxs-lookup"><span data-stu-id="62303-171">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="62303-172">提供所有正确值后，在 Azure PowerShell 提示符处或本地计算机的 PowerShell 集成脚本环境 (ISE) 上运行生成块。</span><span class="sxs-lookup"><span data-stu-id="62303-172">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="62303-173">若要基于自定义设置生成可随时运行的 PowerShell 命令块，请使用此[Microsoft Excel 配置工作簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx)。</span><span class="sxs-lookup"><span data-stu-id="62303-173">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span></span> 

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
> <span data-ttu-id="62303-174">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span><span class="sxs-lookup"><span data-stu-id="62303-174">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span></span> <span data-ttu-id="62303-175">However, this also means that you cannot connect to them from the Azure portal.</span><span class="sxs-lookup"><span data-stu-id="62303-175">However, this also means that you cannot connect to them from the Azure portal.</span></span> <span data-ttu-id="62303-176">The **Connect** option is unavailable when you view the properties of the virtual machine.</span><span class="sxs-lookup"><span data-stu-id="62303-176">The **Connect** option is unavailable when you view the properties of the virtual machine.</span></span> <span data-ttu-id="62303-177">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span><span class="sxs-lookup"><span data-stu-id="62303-177">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="62303-178">配置第一个域控制器</span><span class="sxs-lookup"><span data-stu-id="62303-178">Configure the first domain controller</span></span>

<span data-ttu-id="62303-179">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine.</span><span class="sxs-lookup"><span data-stu-id="62303-179">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine.</span></span> <span data-ttu-id="62303-180">Use its intranet DNS or computer name and the credentials of the local administrator account.</span><span class="sxs-lookup"><span data-stu-id="62303-180">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="62303-181">接下来，使用**第一个域控制器虚拟机上**的 Windows PowerShell 命令提示符将额外的数据磁盘添加到第一个域控制器中：</span><span class="sxs-lookup"><span data-stu-id="62303-181">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="62303-182">接下来，使用 **ping** 命令对组织网络中的资源名称和 IP 地址执行 ping 操作，测试第一个域控制器到组织网络中的位置的连接。</span><span class="sxs-lookup"><span data-stu-id="62303-182">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="62303-183">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network.</span><span class="sxs-lookup"><span data-stu-id="62303-183">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network.</span></span> <span data-ttu-id="62303-184">If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span><span class="sxs-lookup"><span data-stu-id="62303-184">If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="62303-185">接下来，从第一个域控制器的 Windows PowerShell 命令提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="62303-185">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="62303-186">You will be prompted to supply the credentials of a domain administrator account.</span><span class="sxs-lookup"><span data-stu-id="62303-186">You will be prompted to supply the credentials of a domain administrator account.</span></span> <span data-ttu-id="62303-187">The computer will restart.</span><span class="sxs-lookup"><span data-stu-id="62303-187">The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="62303-188">配置第二个域控制器</span><span class="sxs-lookup"><span data-stu-id="62303-188">Configure the second domain controller</span></span>

<span data-ttu-id="62303-189">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine.</span><span class="sxs-lookup"><span data-stu-id="62303-189">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine.</span></span> <span data-ttu-id="62303-190">Use its intranet DNS or computer name and the credentials of the local administrator account.</span><span class="sxs-lookup"><span data-stu-id="62303-190">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="62303-191">接下来，您需要使用**第二个域控制器虚拟机上**的 Windows PowerShell 命令提示符中的此命令将额外的数据磁盘添加到第二个域控制器中：</span><span class="sxs-lookup"><span data-stu-id="62303-191">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="62303-192">接下来，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="62303-192">Next, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="62303-193">You will be prompted to supply the credentials of a domain administrator account.</span><span class="sxs-lookup"><span data-stu-id="62303-193">You will be prompted to supply the credentials of a domain administrator account.</span></span> <span data-ttu-id="62303-194">The computer will restart.</span><span class="sxs-lookup"><span data-stu-id="62303-194">The computer will restart.</span></span>
  
<span data-ttu-id="62303-195">接下来，需要为虚拟网络更新 DNS 服务器，以便 Azure 为虚拟机分配两个新域控制器的 IP 地址，将它们用作其 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="62303-195">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers.</span></span> <span data-ttu-id="62303-196">填写变量，然后从本地计算机上的 Windows PowerShell 命令提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="62303-196">Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
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

<span data-ttu-id="62303-197">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers.</span><span class="sxs-lookup"><span data-stu-id="62303-197">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers.</span></span> <span data-ttu-id="62303-198">Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span><span class="sxs-lookup"><span data-stu-id="62303-198">Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="62303-199">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers.</span><span class="sxs-lookup"><span data-stu-id="62303-199">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers.</span></span> <span data-ttu-id="62303-200">Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span><span class="sxs-lookup"><span data-stu-id="62303-200">Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a><span data-ttu-id="62303-201">配置目录同步服务器</span><span class="sxs-lookup"><span data-stu-id="62303-201">Configure the directory synchronization server</span></span>

<span data-ttu-id="62303-202">使用您选择的远程桌面客户端并创建到目录同步服务器虚拟机的远程桌面连接。</span><span class="sxs-lookup"><span data-stu-id="62303-202">Use the remote desktop client of your choice and create a remote desktop connection to the directory synchronization server virtual machine.</span></span> <span data-ttu-id="62303-203">使用其 Intranet DNS 或计算机名称以及本地管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="62303-203">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="62303-204">接下来，通过 Windows PowerShell 提示符下的这些命令将其加入相应的 AD DS 域。</span><span class="sxs-lookup"><span data-stu-id="62303-204">Next, join it to the appropriate AD DS domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="62303-205">以下是因成功完成这一阶段后生成的配置，包含占位符计算机名称。</span><span class="sxs-lookup"><span data-stu-id="62303-205">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="62303-206">**第2阶段：适用于 Azure 中的高可用性联合身份验证基础结构的域控制器和目录同步服务器**</span><span class="sxs-lookup"><span data-stu-id="62303-206">**Phase 2: The domain controllers and directory synchronization server for your high availability federated authentication infrastructure in Azure**</span></span>

![具有域控制器的 Azure 中的高可用性 Microsoft 365 联合身份验证基础结构的第2阶段](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="62303-208">后续步骤</span><span class="sxs-lookup"><span data-stu-id="62303-208">Next step</span></span>

<span data-ttu-id="62303-209">使用[阶段3：配置 AD FS 服务器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)以继续配置此工作负载。</span><span class="sxs-lookup"><span data-stu-id="62303-209">Use [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="62303-210">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62303-210">See Also</span></span>

[<span data-ttu-id="62303-211">在 Azure 中为 Microsoft 365 部署高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="62303-211">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="62303-212">Microsoft 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="62303-212">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[<span data-ttu-id="62303-213">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="62303-213">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)


