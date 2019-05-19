---
title: 基础配置开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 摘要：在 Microsoft Azure 中创建一个简化的内部网作为开发/测试环境。
ms.openlocfilehash: f6a9f2f2742b56ffb5f8a7521a14bfe48d3adc22
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162435"
---
# <a name="base-configuration-devtest-environment"></a>基础配置开发/测试环境

 **** 摘要：在 Microsoft Azure 中创建一个简化的 Intranet 作为开发/测试环境。
  
本文提供了在 Azure 中创建以下基础配置开发/测试环境的说明：
  
![Azure 中的基础配置](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
**图 1：基础配置开发/测试环境**

图 1 中的基础配置开发/测试环境，由一个仅限云的 Azure 虚拟网络（名为 TestLab）中的 Corpnet 子网组成，可模拟连接到 Internet 的简化专用内部网。它包含三个运行 Windows Server 2016 的 Azure 虚拟机：
  
- DC1 被配置为内部网域控制器和域名系统 (DNS) 服务器
    
- APP1 被配置为常规应用程序和 Web 服务器
    
- CLIENT1 用作内部网客户端
    
这种配置使得 DC1、APP1、CLIENT1 以及其他企业网络子网计算机可以： 
  
- 连接到 Internet 来安装更新，访问实时 Internet 资源，并参与公有云技术，如 Microsoft Office 365 和其他 Azure 服务。
    
- 使用连接至 Internet 或组织网络的计算机中的远程桌面连接进行远程管理。
    
可以使用生成的测试环境：
  
- 用于应用程序开发和测试。
    
- 作为自己设计的扩展测试环境的初始配置，包括附加的虚拟机、Azure 服务或其他 Microsoft 云产品/服务，如 Office 365 和企业版移动性 + 安全性 (EMS)。
    
创建此环境有两种方法：

1. Azure 资源管理器模板
2. Azure Powershell

## <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a>方法 1：使用 Azure 资源管理器模板构建模拟 Intranet

在此方法中，可以使用 Azure 资源管理器 (ARM) 模板来构建模拟 Intranet。ARM 模板包含有关创建和配置 Azure 网络基础结构和虚拟机的所有说明。

部署该模板之前，请通读“模板自述文件”[](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm)页面并准备好以下信息：

- Azure 订阅名称。你需要在“自定义部署”**** 页的“订阅”**** 字段输入此标签。
- Azure 资源组名称。你需要在“自定义部署”**** 页的“资源组”**** 字段输入此标签。
- 虚拟机公共 IP 地址 URL 的 DNS 标签前缀。你将需要在“**自定义部署**”页面的“**Dns 标签前缀**”字段中输入此标签。

通读说明后，在“[模板自述文件](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm)”页面上单击“**部署到 Azure**”，以开始进行部署。

>[!Note]
>通过 ARM 模板构建的模拟 Intranet 需要付费 Azure 订阅。
>

模板完成后，会生成以下配置。

![Azure 中的基础配置](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


## <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a>方法 2：使用 Azure PowerShell 构建模拟 Intranet

在此方法中，你可以使用 Windows PowerShell 和 Azure PowerShell 模块来构建网络基础结构、虚拟机及其配置。

如果想要体验通过 PowerShell 一次使用一个命令块创建 Azure 基础结构元素的过程，则可以使用此方法。然后可以自定义 PowerShell 命令块，以便自行在 Azure 中部署其他虚拟机。

使用 Azure PowerShell 设置基础配置测试环境有如下四个步骤：
  
1. 创建虚拟网络。
    
2. 配置 DC1。
    
3. 配置 APP1。
    
4. 配置 CLIENT1。
    
如果还没有 Azure 订阅，可以在[试用 Azure](https://azure.microsoft.com/pricing/free-trial/) 上注册免费试用版。如果你有 MSDN 或 Visual Studio 订阅，请参阅 [Visual Studio 订阅者的每月 Azure 信用额度](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。
  
> [!NOTE]
> Azure 中的虚拟机在运行时会持续产生费用。该项费用是针对运行免费试用版、MSDN 订阅或付费订阅收取的。关于运行 Azure 虚拟机成本的详细信息，请参阅[虚拟机定价详细信息](https://azure.microsoft.com/pricing/details/virtual-machines/)和 [Azure 定价计算器](https://azure.microsoft.com/pricing/calculator/)。为了节约成本，请参阅[最大限度降低 Azure 中测试环境虚拟机的成本](base-configuration-dev-test-environment.md#mincost)。 
  
![Microsoft 云中的测试实验室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 Office 365 测试实验室指南堆栈中的所有文章。
  
### <a name="step-1-create-the-virtual-network"></a>步骤 1：创建虚拟网络

在此步骤中，将在 Azure 中创建 TestLab 虚拟网络。

首先，从 Azure PowerShell 提示符开始。
  
> [!NOTE]
> 下面的命令集使用最新版 Azure PowerShell。请参阅 [Azure PowerShell cmdlet 使用入门](https://docs.microsoft.com/zh-CN/powershell/azureps-cmdlets-docs/)。 
  
使用以下命令登录 Azure 帐户。
  
```
Connect-AzAccount
```

> [!TIP]
> 单击[此处](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d)可获取包含本文中所有 PowerShell 命令的文本文件。

使用以下命令获取订阅名称。
  
```
Get-AzSubscription | Sort Name | Select Name
```

设置 Azure 订阅。使用正确的名称替换引号内的所有内容（包括 < 和 > 字符）。
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

接下来，为基础配置测试实验室创建一个新的资源组。要确定一个唯一的资源组名称，请使用此命令列出现有的资源组。
  
```
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

使用这些命令创建新的资源组。使用正确的名称替换引号内的所有内容（包括 < 和 > 字符）。
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

接下来，创建 TestLab 虚拟网络，它将托管基础配置的企业网络子网并通过网络安全组对其进行保护。
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

当前配置如下。
  
![通过虚拟网络和子网在 Azure 中进行基础配置的第 1 步](media/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
### <a name="step-2-configure-dc1"></a>步骤 2：配置 DC1

在此步骤中，我们需要创建 DC1 虚拟机，并将它配置为 corp.contoso.com Active Directory 域服务 (AD DS) 域的域控制器，以及 TestLab 虚拟网络中虚拟机的 DNS 服务器。

> [!NOTE]
> 执行以下命令块前，请确保选择的 Azure 区域（位置）支持 Azure 虚拟机大小，默认情况下设置为“Standard_A1”。单击[此处](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)，查看有关 Azure 虚拟机大小和位置的最新信息。
  
要为 DC1 创建 Azure 虚拟机，请填写资源组名称，并在本地计算机上在 Azure PowerShell 命令提示符运行下面这些命令。
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

系统将提示你为 DC1 上的本地管理员帐户输入用户名和密码。使用强密码，并在安全位置记录名称和密码。
  
接下来，连接到 DC1 虚拟机。
  
1. 在 [Azure 门户](https://portal.azure.com)中，单击“**资源组”>** [新资源组的名称] ** > DC1 >“连接**”。
    
2. 在打开的窗格中，单击“**下载 RDP 文件**”。打开下载的 DC1.rdp 文件，然后单击“**连接**”。
    
3. 指定 DC1 本地管理员帐户名：
    
  - 对于 Windows 7：
    
    在“Windows 安全性”**** 对话框中，单击“使用另一个帐户”****。在“用户名称”**** 中，键入 **DC1\\**[本地管理员帐户名称]
    
  - 对于 Windows 8 或 Windows 10：
    
    在“Windows 安全性”**** 对话框中，单击“更多选择”****，然后单击“使用不同帐户”****。在“用户名”**** 中，键入 **DC1\\**[本地管理员帐户名称]。
    
4. 在“密码”**** 中，键入本地管理员帐户密码，然后单击“确定”****。
    
5. 出现提示时，请单击“是”****。
    
接下来，在 DC1 上管理员一级的 Windows PowerShell 命令提示符处，使用下面的命令将额外的数据磁盘添加为新卷，驱动器号为 F:。
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

接下来，将 DC1 配置为 corp.contoso.com 域的域控制器和 DNS 服务器。在管理员级别 Windows PowerShell 命令提示符中，运行这些命令。
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
需指定安全模式管理员密码。在安全的位置存储该密码。
  
请注意，这些命令可能需要几分钟才能完成。
  
DC1 重启后，使用域凭据重新连接到 DC1 虚拟机。
  
1. 在 [Azure 门户](https://portal.azure.com)中，单击“资源组 > [你的资源组名称] ****> DC1 > 连接”****。
    
2. 运行下载的 DC1.rdp 文件，然后单击“连接”****。
    
3. 在“Windows 安全性”**** 中，单击“使用另一个帐户”****。在“用户名称”**** 中，键入 **CORP\\**[本地管理员帐户名称]。
    
4. 在“密码”**** 中，键入本地管理员帐户密码，然后单击“确定”****。
    
5. 出现提示时，请单击“是”****。
    
接下来，在 Active Directory 中创建一个用户帐户，将使用该帐户登录到 CORP 域成员计算机。在管理员级别 Windows PowerShell 命令提示符中，运行此命令。
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

请注意，此命令会提示你提供用户 1 帐户密码。由于此帐户将用于所有 CORP 域成员计算机的远程桌面连接，请选择强密码。记录 User1 帐户密码并将其存储在安全位置。
  
接下来，将新的 User1 帐户配置为企业管理员。在管理员级别 Windows PowerShell 命令提示符处运行此命令。
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

关闭与 DC1 的远程桌面会话，然后使用 CORP\\User1 帐户重新连接。
  
接下来，若要允许 Ping 工具使用流量，请在管理员级别 Windows PowerShell 命令提示符处运行此命令。
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

当前配置如下。
  
![使用 DC1 虚拟机在 Azure 中进行基础配置的第 2 步](media/49069908-29c3-4d73-87f7-debbea067261.png)
  
### <a name="step-3-configure-app1"></a>步骤 3：配置 APP1

在这一步，创建和配置 APP1，它提供 Web 和文件共享服务。

> [!NOTE]
> 执行以下命令块前，请确保选择的 Azure 区域（位置）支持 Azure 虚拟机大小，默认情况下设置为“Standard_A1”。单击[此处](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)，查看有关 Azure 虚拟机大小和位置的最新信息。
  
若要为 APP1 创建 Azure 虚拟机，请填写资源组名称，并在本地计算机上的 Azure PowerShell 命令提示符处运行下面这些命令。
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

接下来，使用 APP1 本地管理员帐户名称和密码连接到 APP1 虚拟机，然后打开 Windows PowerShell 命令提示符。
  
若要检查 APP1 和 DC1 之间的名称解析和网络通信，请运行 **ping dc1.corp.contoso.com** 命令，并查看是否存在四个答复。
  
接下来，在 Windows PowerShell 提示符处使用这些命令将 APP1 虚拟机加入 CORP 域。
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

请注意，在运行 **Add-Computer** 命令后，你必须提供 CORP\\User1 域帐户凭据。
  
App1 重启后，请使用 CORP\\User1 帐户进行连接，然后打开管理员级别 Windows PowerShell 命令提示符。
  
下一步，在 APP1 上的 Windows PowerShell 命令提示符处使用此命令将 APP1 设置为 Web 服务器。
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

下一步，使用这些 PowerShell 命令在 APP1 的文件夹中创建一个共享文件夹和文本文件。
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

当前配置如下。
  
![使用 APP1 虚拟机在 Azure 中进行基础配置的第 3 步](media/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
### <a name="step-4-configure-client1"></a>步骤 4：配置 CLIENT1

在这一步，创建和配置 CLIENT1，这是 Contoso Intranet 上的典型笔记本电脑、平板电脑或台式计算机。

> [!NOTE]  
> 下面的命令集会创建运行 Windows Server 2016 Datacenter 的 CLIENT1，可对所有类型的 Azure 订阅执行此操作。若有基于 Visual Studio 的 Azure 订阅，可以通过 [Azure 门户](https://portal.azure.com)创建运行 Windows 10 的 CLIENT1。 
  

> [!NOTE]
> 执行以下命令块前，请确保选择的 Azure 区域（位置）支持 Azure 虚拟机大小，默认情况下设置为“Standard_A1”。单击[此处](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)，查看有关 Azure 虚拟机大小和位置的最新信息。
  
若要为 CLIENT1 创建 Azure 虚拟机，请填写资源组名称，并在本地计算机上的 Azure PowerShell 命令提示符处运行下面这些命令。
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

接下来，使用 CLIENT1 本地管理员帐户名称和密码连接到 CLIENT1 虚拟机，然后打开管理员级别 Windows PowerShell 命令提示符。
  
若要检查 CLIENT1 和 DC1 之间的名称解析和网络通信，请在 Windows PowerShell 命令提示符处运行 **ping dc1.corp.contoso.com** 命令，并查看是否存在四个答复。
  
接下来，在 Windows PowerShell 提示符处使用这些命令将 CLIENT1 虚拟机加入 CORP 域。
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

请注意，在运行 **Add-Computer** 命令后，你必须提供 CORP\\User1 域帐户凭据。
  
CLIENT1 重启后，请使用 CORP\\User1 帐户名称和密码进行连接，然后打开管理员级别 Windows PowerShell 命令提示符。
  
接下来，查看能否从 CLIENT1 访问 APP1 上的 Web 和文件共享资源。
  
1. 在服务器管理器的树窗格中，单击“本地服务器”****。
    
2. 在“CLIENT1 的属性”**** 中，单击“IE 增强的安全配置”**** 旁边的“打开”****。
    
3. 在“Internet Explorer 增强的安全性配置”**** 中，为**管理员**和**用户**单击“关闭”****，然后单击“确定”****。
    
4. 在“开始”屏幕中，单击“**Internet Explorer**”，然后单击“**确定**”。
    
5. 在地址栏中，键入 **http:\//app1.corp.contoso.com/**，然后按 ENTER 。应会看到 APP1 的默认 Internet Information Services 网页。
    
6. 从桌面任务栏中，单击“文件资源管理器”图标。
    
7. 在地址栏中，键入 **\\\\app1\\Files**，然后按 ENTER 键。应该会看到带有文件共享文件夹内容的文件夹窗口。
    
8. 在“文件”**** 共享文件夹窗口中，双击“Example.txt”**** 文件。应该会看到 Example.txt 文件的内容。
    
9. 关闭“example.txt - 记事本”**** 和“文件”**** 共享文件夹窗口。
    
最终配置如下。
  
![使用 CLIENT1 虚拟机在 Azure 中进行基础配置的第 4 步](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
Azure 中的基础配置现在已完成，可用于应用程序开发和测试或用于构建其他测试环境。 
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 Office 365 测试实验室指南堆栈中的所有文章。
  
<a name="mincost"> </a>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a>最大限度降低 Azure 中测试环境虚拟机的成本

若要将运行测试环境虚拟机的成本降至最低，可以执行以下任一操作：
  
- 创建测试环境，并尽快执行所需的测试和演示。完成后，删除测试环境的资源组。
    
- 关闭测试环境虚拟机，进入已取消分配状态。
    
若要使用 Azure PowerShell 关闭虚拟机，请填写资源组名称并运行这些命令。
  
```
$rgName="<your resource group name>"
Stop-AzVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "DC1" -Force
```

若要确保所有虚拟机在从停止（已取消分配）状态启动时可以正常工作，则应按以下顺序进行启动：
  
1. DC1
2. APP1
3. CLIENT1
    
若要使用 Azure PowerShell 按顺序启动虚拟机，请填写资源组名称并运行这些命令。
  
```
$rgName="<your resource group name>"
Start-AzVM -ResourceGroupName $rgName -Name "DC1"
Start-AzVM -ResourceGroupName $rgName -Name "APP1"
Start-AzVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a>另请参阅

- [Office 365 开发/测试环境](office-365-dev-test-environment.md)
- [用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
- [Office 365 开发/测试环境中的高级威胁防护](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
