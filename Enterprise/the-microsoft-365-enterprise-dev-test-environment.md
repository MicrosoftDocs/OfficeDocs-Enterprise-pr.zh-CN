---
title: Microsoft 365 企业开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 摘要： 使用此测试实验室指南创建开发/测试环境，包括 Office 365 E5、 企业移动性 + 安全 (EMS) E5 和计算机运行 Windows 10 企业。
ms.openlocfilehash: 47557b7d7bdb09e2ce2731a17d6e4b35ddcd063d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 企业开发/测试环境

 **摘要：**此测试实验室指南用于创建一个包括 Office 365 E5、 企业移动性 + 安全 (EMS) E5 和计算机运行 Windows 10 企业的开发/测试环境。
  
这篇文章为您提供了创建要测试的功能和功能的[Microsoft 365 企业](https://www.microsoft.com/microsoft-365/enterprise)简化的环境的分步说明。
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a>阶段 1： 创建 Office 365 E5 订阅

按照在第 2 阶段和第 3 阶段的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)来创建 Office 365 轻量级开发/测试环境中，如图 1 所示的步骤。
  
**图 1: Office 365 E5 订阅其 Azure 活动目录 (AD) 租户和用户帐户**

![Microsoft 365 企业版开发/测试环境的第 1 阶段](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)
  
## <a name="phase-2-add-ems"></a>阶段 2： 添加 EMS

在此阶段中，EMS E5 试用订阅注册，并将其添加到 Office 365 E5 试用为同一个组织。
  
首先，添加 EMS E5 试用订阅并将 EMS 许可证分配给全局管理员帐户。
  
1. 与 Internet 浏览器的专用实例，登录到 Office 365 门户使用您的全局管理员帐户凭据。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 单击“管理”磁贴。
    
3. 在浏览器的“Office 管理中心”选项卡的左侧导航中，单击“帐单”>“购买服务”。
    
4. **购买服务**页上找到**企业移动 + 安全 E5**项。将鼠标指针悬停在其上，单击**启动免费试用版**。
    
5. 在“确认订单”页中，单击“立即试用”。
    
6. 在“订单签收”页中，单击“继续”。
    
7. 在浏览器的“Office 365 管理中心”选项卡的左侧导航中，单击“用户”>“活动用户”。
    
8. 单击您的全局管理员帐户，然后单击**编辑****产品**许可证。
    
9. **产品许可证**的窗格中，在打开产品许可证**的企业移动性 + 安全 E5**到**上**，单击**保存**，然后两次单击**关闭**。
    
> [!NOTE]
> 企业移动性 + 安全性 E5 的试订阅期为 90 天。对于永久性开发/测试环境，请使用少量许可证新建付费订阅。 
  
 ***如果您完成了第 3 阶段***[Office 365 的开发/测试环境](office-365-dev-test-environment.md)，重复步骤 8 和 9 的前一过程的所有其他帐户 （用户 2、 用户 3、 用户 4 和用户 5）。
  
现在已开发/测试环境：
  
- 与你的用户帐户列表共享同一个组织和相同 Azure AD 租户的 Office 365 E5 企业版和 EMS 试用订阅。
- 所有适当的用户帐户 （只是全局管理员或所有五个用户帐户） 都可以使用 Office 365 E5 和 EMS E5。
    
图 2 显示您生成的配置，它增加了 EMS。
  
**图 2： 添加 EMS 试用订阅**

![Microsoft 365 企业版开发/测试环境的第 2 阶段](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a>阶段 3： 创建 Windows 10 企业计算机

在此阶段中，您将创建独立的计算机运行 Windows 10 企业。
  
### <a name="physical-computer"></a>物理计算机

获取个人计算机并在其上安装 Windows 10 企业。您可以下载 Windows 10 企业试用版在[这里](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)。
  
### <a name="virtual-machine"></a>虚拟机

创建一个使用您所选的虚拟机管理程序的虚拟机并在其上安装 Windows 10 企业。您可以下载 Windows 10 企业试用版在[这里](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)。
  
### <a name="virtual-machine-in-azure"></a>在 Azure 中的虚拟机

若要在 Microsoft Azure，***您必须基于 Visual Studio 的预订***，为 Windows 10 企业有权图像创建 Windows 10 虚拟机。其他类型的 Azure 订阅，如试用和付费订阅，不能访问到此图像。
  
> [!NOTE]
> 下面的命令设置使用 Azure PowerShell 的最新版本。请参阅[开始使用 Azure PowerShell cmdlet](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)。这些命令集生成 Windows 10 企业虚拟机命名为 WIN10，其所需的基础结构，包括某一资源组、 存储帐户和虚拟网络的所有。如果您已熟悉 Azure 的基础结构服务，请调整这些说明来满足您当前部署的基础结构。 
  
首先，启动 Microsoft PowerShell 提示。
  
使用以下命令登录 Azure 帐户。
  
```
Login-AzureRMAccount
```

使用以下命令获得订阅名称。
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

设置 Azure 订购。引号，包括的所有内容替换\<和 > 字符，用正确的名称。
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

接下来，创建一个新的资源组。要确定一个唯一的资源组名称，请使用此命令列出你现有的资源组。
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

使用这些命令创建新的资源组。引号，包括的所有内容替换\<和 > 字符，替换为正确的名称。
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

接下来，创建一个新的虚拟网络和 WIN10 虚拟机使用这些命令。出现提示时，为 WIN10 提供的用户名和密码的本地管理员帐户和存储在一个安全的位置。
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a>阶段 4: Windows 10 将计算机加入到 Azure 的广告

创建物理或虚拟机，它与 Windows 10 企业后，使用本地管理员帐户登录。
  
> [!NOTE]
> 在 Azure 中的虚拟机，将连接到使用[这些说明](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)。使用本地管理员帐户的凭据登录。 
  
接下来，将 WIN10 计算机加入到 Office 365 和 EMS 订阅的 Azure AD 租户。
  
1. 在 WIN10 计算机的桌面，请单击**开始 > 设置 > 帐户 > 访问工作或学校 > 连接**。
    
2. 在**工作或学校的科目设置**对话框中，单击**加入到 Azure Active Directory 该设备**。
    
3. 在**工作或学校帐户**，键入您的 Office 365 订购的全局管理员帐户名，然后单击**下一步**。
    
4. 在**输入密码**框中，键入您的全局管理员帐户的密码，然后单击**登录**。
    
5. 出现提示时，以确保这是您的组织，**加入**，请单击，然后单击**完成**。
    
6. 关闭设置窗口。
    
接下来，在 WIN10 计算机上安装 Office 2016。
  
1. 打开 Microsoft 边浏览器并登录到您的全局管理员帐户凭据与 Office 365 门户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在**Microsoft Office 主页**选项卡上，单击**安装 Office 2016**。
    
3. 当收到提示时要执行的操作，单击**运行**，然后单击**是****用户帐户**控制。
    
4. 等待 Office 来完成安装。当您看到**就可以了 ！**，两次单击**关闭**。
    
图 3 显示您生成的环境，其中包括 WIN10 计算机已加入的 Office 365 和 EMS 订阅 Azure AD 租户。
  
**图 3： 将 WIN10 的计算机帐户添加到 Azure AD 租户**

![Microsoft 365 企业版开发/测试环境的第 4 阶段](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
现在您可以尝试使用[Microsoft 365 企业](https://www.microsoft.com/microsoft-365/enterprise)的其他功能。
  
## <a name="next-steps"></a>后续步骤

使用这些附加的文章浏览 Microsoft 365 企业的功能：
  
- [添加移动应用程序 (MAM) 管理策略](https://technet.microsoft.com/library/mt764059.aspx)
    
- [IOS 和 Android 设备注册](https://technet.microsoft.com/library/mt743077.aspx)
    
- [配置和测试高级安全管理](https://technet.microsoft.com/library/mt757250.aspx)
    
- [配置和测试高级威胁防护](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a>另请参阅

- [Microsoft 365 企业文档](https://docs.microsoft.com/microsoft-365-enterprise/)
- [部署 Microsoft 365 企业](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)
- [一个 Microsoft 云开发/测试环境](the-one-microsoft-cloud-dev-test-environment.md)
