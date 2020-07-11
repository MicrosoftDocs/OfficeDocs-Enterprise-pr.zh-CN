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
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>高可用性联合身份验证阶段 2：配置域控制器

在此阶段，在 Azure 基础结构服务中为 Microsoft 365 联合身份验证部署高可用性时，需要在 Azure 虚拟网络中配置两个域控制器和目录同步服务器。 然后用于身份验证的客户端 Web 请求可以在 Azure 虚拟网络中进行身份验证，而不是将通过站点到站点 VPN 连接的该身份验证流量发送到本地网络。
  
> [!NOTE]
> Active Directory 联合身份验证服务 (AD FS) 无法使用 Azure Active Directory (Azure AD) 以替代 Active Directory 域服务 (AD DS) 域控制器。 
  
在转到[第3阶段：配置 AD FS 服务器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)之前，您必须完成此阶段。 有关所有阶段，请参阅[在 Azure 中为 Microsoft 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>在 Azure 中创建域控制器虚拟机

首先，需要填写表 M 的 **虚拟机名称** 列，并根据需要在 **最小大小** 列修改虚拟机大小。
  
|**项**|**虚拟机名称**|**库图像**|**存储类型**|**最小大小**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![线条](./media/Common-Images/TableLine.png) （第一个域控制器，例如 DC1）  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![线条](./media/Common-Images/TableLine.png) （第二个域控制器，例如 DC2）  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![线条](./media/Common-Images/TableLine.png)  (目录同步服务器，示例 DS1)   <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![线条](./media/Common-Images/TableLine.png)  (第一个 AD FS 服务器，示例 ADFS1)   <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![线条](./media/Common-Images/TableLine.png)  (第二个 AD FS 服务器，示例 ADFS2)   <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![线条](./media/Common-Images/TableLine.png)  (第一个 web 应用程序代理服务器，示例 WEB1)   <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![线条](./media/Common-Images/TableLine.png)  (第二个 web 应用程序代理服务器，示例 WEB2)   <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **表 M-Azure 中适用于 Microsoft 365 的高可用性联合身份验证的虚拟机**
  
有关虚拟机大小的完整列表，请参阅[虚拟机的大小](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)。
  
以下 Azure PowerShell 命令块可创建两个域控制器的虚拟机。 指定变量的值，并删除 \< and > 字符。 请注意，此 Azure PowerShell 命令块使用下表中的值：
  
- 表 M，用于虚拟机
    
- 表 R，用于资源组
    
- 表 V，用于虚拟网络设置
    
- 表 S，用于子网
    
- 表 I，用于静态 IP 地址
    
- 表 A（针对可用性集）
    
回想一下您在[第1阶段： Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md)中定义了表 R、V、S、I 和 A。
  
> [!NOTE]
> [!注意] 下面的命令集使用最新版 Azure PowerShell。 请参阅[Azure PowerShell 入门](https://docs.microsoft.com/powershell/azure/get-started-azureps)。 
  
提供所有正确值后，在 Azure PowerShell 提示符处或本地计算机的 PowerShell 集成脚本环境 (ISE) 上运行生成块。
  
> [!TIP]
> 若要基于自定义设置生成可随时运行的 PowerShell 命令块，请使用此[Microsoft Excel 配置工作簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx)。 

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
> Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.
  
## <a name="configure-the-first-domain-controller"></a>配置第一个域控制器

Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.
  
接下来，使用**第一个域控制器虚拟机上**的 Windows PowerShell 命令提示符将额外的数据磁盘添加到第一个域控制器中：
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

接下来，使用 **ping** 命令对组织网络中的资源名称和 IP 地址执行 ping 操作，测试第一个域控制器到组织网络中的位置的连接。
  
This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.
  
接下来，从第一个域控制器的 Windows PowerShell 命令提示符处运行以下命令：
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

You will be prompted to supply the credentials of a domain administrator account. The computer will restart.
  
## <a name="configure-the-second-domain-controller"></a>配置第二个域控制器

Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.
  
接下来，您需要使用**第二个域控制器虚拟机上**的 Windows PowerShell 命令提示符中的此命令将额外的数据磁盘添加到第二个域控制器中：
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

接下来，请运行以下命令：
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

You will be prompted to supply the credentials of a domain administrator account. The computer will restart.
  
接下来，需要为虚拟网络更新 DNS 服务器，以便 Azure 为虚拟机分配两个新域控制器的 IP 地址，将它们用作其 DNS 服务器。 填写变量，然后从本地计算机上的 Windows PowerShell 命令提示符处运行以下命令：
  
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

Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.
  
Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a>配置目录同步服务器

使用您选择的远程桌面客户端并创建到目录同步服务器虚拟机的远程桌面连接。 使用其 Intranet DNS 或计算机名称以及本地管理员帐户的凭据。
  
接下来，通过 Windows PowerShell 提示符下的这些命令将其加入相应的 AD DS 域。
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

以下是因成功完成这一阶段后生成的配置，包含占位符计算机名称。
  
**第2阶段：适用于 Azure 中的高可用性联合身份验证基础结构的域控制器和目录同步服务器**

![具有域控制器的 Azure 中的高可用性 Microsoft 365 联合身份验证基础结构的第2阶段](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>后续步骤

使用[阶段3：配置 AD FS 服务器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)以继续配置此工作负载。
  
## <a name="see-also"></a>另请参阅

[在 Azure 中为 Microsoft 365 部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Microsoft 365 开发/测试环境的联合身份](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.yml)


