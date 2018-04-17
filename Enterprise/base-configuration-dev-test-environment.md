---
title: 基础配置开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 摘要： 创建的简化内部网作为 Microsoft Azure 中的开发/测试环境。
ms.openlocfilehash: a874260510b2825fae0f0fd9154912d35e555d19
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="base-configuration-devtest-environment"></a>基础配置开发/测试环境

 **摘要：**作为 Microsoft Azure 中的开发/测试环境中创建简化的内联网。
  
本文提供了在 Azure 中创建以下基础配置开发/测试环境的分步说明：
  
**图 1： 基本配置开发/测试环境**

![CLIENT1 虚拟机的 Azure 中的基础配置的阶段 4](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
在图 1 中的基本配置开发/测试环境由仅云 Azure 虚拟网络命名测试实验室模拟简化、 专用内联网连接到 Internet 的企业网络子网组成。它包含三个运行 WIndows 服务器 2016年的 Azure 虚拟机：
  
- DC1 被配置为一个内部网域控制器和域名系统 (DNS) 服务器
    
- APP1 被配置为常规应用程序和 Web 服务器
    
- 	CLIENT 1 用作内部网客户端
    
这种配置使得 DC1、APP1、CLIENT 1 以及其他企业网络子网计算机得以：  
  
- 连接到 Internet 来安装更新程序，访问实时互联网资源，并且参与公有云技术，如 Microsoft Office 365 和其他 Azure 服务。
    
- 	使用连接至 Internet 或组织网络的计算机中的远程桌面连接进行远程管理。
    
可以使用生成的测试环境：
  
- 用于应用程序开发和测试。
    
- 为自己设计一个长的测试环境的初始配置，包括附加的虚拟机、 Azure 服务或其他 Microsoft 云产品如 Office 365 和企业安全 + 移动 (EMS)。
    
在 Azure 中设置基本配置测试环境的四个阶段：
  
1. 	创建虚拟网络。
    
2. 	配置 DC1。
    
3. 	配置 APP1。
    
4. 	配置 CLIENT1。
    
如果您已经没有 Azure 的订阅，您可以注册在[尝试 Azure](https://azure.microsoft.com/pricing/free-trial/)的免费试用版。如果您订阅了 MSDN 或 Visual Studio，请参见[为 Visual Studio 订户每月 Azure 信用](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。
  
> [!NOTE]
> 在 Azure 中的虚拟机运行时招来持续的货币成本。此成本记帐针对免费试用版，MSDN 订阅，或付款订购。运行虚拟机 Azure 的成本的详细信息，请参阅[虚拟机定价详细信息](https://azure.microsoft.com/pricing/details/virtual-machines/)和[Azure 定价计算器](https://azure.microsoft.com/pricing/calculator/)。为了降低成本，请参阅[测试环境在 Azure 中的虚拟机的成本降至最低](base-configuration-dev-test-environment.md#mincost)。 
  
![Microsoft 云中的测试实验室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。
  
## <a name="phase-1-create-the-virtual-network"></a>第 1 阶段：创建虚拟网络

首先，从 Azure PowerShell 提示符开始。
  
> [!NOTE]
> 下面的命令设置使用 Azure PowerShell 的最新版本。请参阅[开始使用 Azure PowerShell cmdlet](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)。 
  
使用以下命令登录 Azure 帐户。
  
```
Login-AzureRMAccount
```

> [!TIP]
> 单击[此处](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d)以获取包含本文中的所有 PowerShell 命令的文本文件。
  
使用以下命令获得订阅名称。
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

设置 Azure 订阅。使用正确的名称替换引号内的所有内容（包括 < 和 > 字符）。
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

接下来，为基础配置测试实验室创建一个新的资源组。要确定一个唯一的资源组名称，请使用此命令列出现有的资源组。
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

使用这些命令创建新的资源组。使用正确的名称替换引号内的所有内容（包括 < 和 > 字符）。
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

接下来，创建 TestLab 虚拟网络，它将托管基础配置的企业网络子网并通过网络安全组对其进行保护。
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

这是你的当前配置。
  
![虚拟网络和子网的 Azure 中的基础配置的阶段 1](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a>第 2 阶段：配置 DC1

在此阶段，我们需要创建 DC1 虚拟机，并将它配置为 corp.contoso.com Windows Server Active Directory (AD) 域的域控制器，并配置为 TestLab 虚拟网络中虚拟机的 DNS 服务器。
  
要为 DC1 创建 Azure 的虚拟机，请填入您的资源组并在 Azure PowerShell 命令提示符下运行这些命令，您的本地计算机上。
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzureRMVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

系统将提示你为 DC1 上的本地管理员帐户输入用户名和密码。使用强密码，并在安全位置记录名称和密码。
  
接下来，连接到 DC1 虚拟机。
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a>使用本地管理员帐户凭据连接到 DC1。

1. 在[Azure 门户](https://portal.azure.com)，单击**资源组 >** [新的资源组的名称] **> DC1 > 连接**。
    
2. 打开已下载的 DC1.rdp 文件，然后单击**连接**。
    
3. 指定 DC1 本地管理员帐户名称：
    
  - 对于 Windows 7：
    
    在**Windows 安全**对话框中，单击**使用另一个帐户**。在**用户名称**中键入**DC1\\**[本地管理员帐户名称]。
    
  - 对于 Windows 8 或 Windows 10：
    
    在**Windows 安全**对话框中，单击**更多的选择**，，然后单击**使用不同的帐户**。在**用户名称**中键入**DC1\\**[本地管理员帐户名称]。
    
4. 在**密码**框中，键入本地管理员帐户的密码，然后单击**确定**。
    
5. 出现提示时，请单击**是**。
    
接下来，添加额外的数据磁盘作为新卷驱动器号 f： 使用此命令在 DC1 上的 Windows PowerShell 命令提示符管理员级别。
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

接下来，将 DC1 配置为 corp.contoso.com 域的域控制器和 DNS 服务器。在管理员级别 Windows PowerShell 命令提示符中，运行这些命令。
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```

需指定安全模式管理员密码。在安全的位置存储该密码。
  
请注意，这些命令可能会花几分钟才能完成。
  
DC1 重启后，重新连接到 DC1 虚拟机。
  
### <a name="connect-to-dc1-using-domain-credentials"></a>使用域凭据连接到 DC1

1. 在[Azure 门户](https://portal.azure.com)，单击**资源组 >** [资源组名称] **> DC1 > 连接**。
    
2. 运行已下载的 DC1.rdp 文件，然后单击**连接**。
    
3. 在**Windows 安全**中，单击**使用其他帐户**。在**用户名称**中键入**CORP\\**[本地管理员帐户名称]。
    
4. 在**密码**框中，键入本地管理员帐户的密码，然后单击**确定**。
    
5. 出现提示时，请单击**是**。
    
接下来，在 Active Directory 中创建一个用户帐户，将使用该帐户登录到 CORP 域成员计算机。在管理员级别 Windows PowerShell 命令提示符中，运行此命令。
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

请注意，此命令会提示你提供用户 1 帐户密码。由于此帐户将用于所有 CORP 域成员计算机的远程桌面连接，请选择强密码。记录 User1 帐户密码并将其存储在安全位置。
  
接下来，配置新的 User1 帐户作为企业管理员。在管理员级别 Windows PowerShell 命令提示符中，运行此命令。
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

关闭与 DC1 的远程桌面会话，然后重新连接使用 CORP\\User1 帐户。
  
接下来，若要允许 Ping 工具使用流量，请在管理员级别 Windows PowerShell 命令提示符中，运行此命令。
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

这是你的当前配置。
  
![DC1 虚拟机的 Azure 中的基础配置的阶段 2](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a>第 3 阶段：配置 APP1

APP1 提供 Web 和文件共享服务。

-> [!NOTE]  
-> 以下命令集创建客户端 1 运行 Windows 服务器 2016年数据，这可以为所有类型的 Azure 订阅中心。如果您有基于 Visual Studio 的 Azure 订阅，您可以创建客户端 1 使用[Azure 门户](https://portal.azure.com)运行 Windows 10。 

若要创建 APP1 Azure 的虚拟机，填入您的资源组，Azure PowerShell 命令提示符下运行这些命令，您的本地计算机上。
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

接下来，使用 APP1 本地管理员帐户名称和密码连接到 APP1 虚拟机，然后打开 Windows PowerShell 命令提示符。
  
若要检查 APP1 和 DC1 之间的名称解析和网络通信，请运行**ping dc1.corp.contoso.com**命令，验证存在四个答复。
  
接下来，通过 Windows PowerShell 提示符下的这些命令将 APP1 虚拟机加入 CORP 域。
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

请注意，您必须提供 CORP\\User1 域帐户凭据后运行**添加计算机**命令。
  
App1 发出重新启动后，连接到该公司\\User1 帐户，然后打开管理员级 Windows PowerShell 命令提示符。
  
下一步，使用此命令在 APP1 的 Windows PowerShell 命令提示符处将 APP1 设置为 Web 服务器。
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

下一步，使用这些 PowerShell 命令在 APP1 的文件夹中创建一个共享文件夹和文本文件。
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

这是你的当前配置。
  
![APP1 虚拟机的 Azure 中的基础配置的阶段 3](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a>第 4 阶段：配置 CLIENT1

CLIENT 1 可在 Contoso 内部网上充当典型的笔记本电脑、平板电脑或台式计算机。
  
若要创建的客户端 1 Azure 的虚拟机，填充您的资源组的名称和在 Azure PowerShell 命令提示符下运行这些命令，您的本地计算机上。
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

接下来，使用 CLIENT1 本地管理员帐户名称和密码连接到 CLIENT1 虚拟机，然后打开管理员级别 Windows PowerShell 命令提示符。
  
要检查 CLIENT1 DC1 之间的名称解析和网络通信，请在 Windows PowerShell 命令提示符运行**ping dc1.corp.contoso.com**命令并验证存在四个答复。
  
接下来，通过 Windows PowerShell 提示符下的这些命令将 CLIENT1 虚拟机加入 CORP 域。
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

请注意，您必须提供您公司\\User1 域帐户凭据后运行**添加计算机**命令。
  
客户端 1 重新启动后，连接到该公司\\User1 帐户名称和密码，然后再打开管理员级别的 Windows PowerShell 命令提示符。
  
接下来，验证是否可以从 CLIENT1 访问 APP1 上的 Web 和文件共享资源。
  
### <a name="verify-client-access-to-app1"></a>验证 CLIENT 是否可以访问 APP1

1. 在服务器管理器中，在树窗格中，单击**本地服务器**命令。
    
2. 在**客户端 1 的属性**中，单击**在**旁边**IE 增强的安全配置**。
    
3. 在**Internet Explorer 增强的安全配置**，**管理员**和**用户**，单击**关闭**，然后单击**确定**。
    
4. 从开始屏幕中，单击**Internet Explorer**，，然后单击**确定**。
    
5. 在地址栏中，键入**http://app1.corp.contoso.com/**，然后按 enter 键。您应该看到 APP1 默认 Internet Information Services 网页。
    
6. 从桌面任务栏中，单击文件资源管理器图标。
    
7. 在地址栏中，键入**\\ \\app1\\文件**，然后按 enter 键。您会看到文件的共享文件夹中的内容的文件夹窗口。
    
8. 在**文件**共享的文件夹窗口中，双击**Example.txt**文件。您应该看到 Example.txt 文件的内容。
    
9. **Example.txt-记事本**和共享**文件**文件夹窗口关闭。
    
这就是你的最终配置。
  
![CLIENT1 虚拟机的 Azure 中的基础配置的阶段 4](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
Azure 中的基本配置现在已准备就绪，可用于应用程序开发和测试或用于构建其他测试环境。 
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。
  
<a name="mincost"> </a>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a>将 Azure 中的测试环境虚拟机成本降至最低

若要将运行测试环境虚拟机的成本降至最低，可以执行以下任一操作：
  
- 创建测试环境，并尽快执行所需的测试和演示。完成后，删除测试环境的资源组。
    
- 	关闭测试环境虚拟机，进入已取消分配状态。
    
若要使用 Azure PowerShell 关闭虚拟机，请填写资源组名称并运行这些命令。
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

若要确保所有虚拟机在从停止（已取消分配）状态启动时可以正常工作，则应按以下顺序进行启动：
  
1. DC1
2. APP1
3. 客户端 1
    
若要使用 Azure PowerShell 按顺序启动虚拟机，请填写资源组名称并运行这些命令。
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a>另请参阅

- [Office 365 开发/测试环境](office-365-dev-test-environment.md)
- [用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
- [Office 365 开发/测试环境的云应用程序安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [为您的 Office 365 开发/测试环境高级威胁防护](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
