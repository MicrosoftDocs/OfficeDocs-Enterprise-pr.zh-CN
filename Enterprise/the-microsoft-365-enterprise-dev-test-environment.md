---
title: Microsoft 365 企业版开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 简介：使用此测试实验室指南创建包含 Office 365 E5、企业移动性+安全性 (EMS) E5 和运行 Windows 10 企业版的计算机的开发/测试环境。
ms.openlocfilehash: 5a4c23b3bde309a75a61e574e91823ecdd4629fe
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 企业版开发/测试环境

 **摘要：** 使用此测试实验室指南创建包含 Office 365 E5、企业移动性+安全性 (EMS) E5 和运行 Windows 10 企业版的计算机的开发/测试环境。
  
本文通过分步说明，指导你创建一个简化的环境来测试 [Microsoft 365 企业版](https://www.microsoft.com/microsoft-365/enterprise)的特性和功能。
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a>第 1 阶段：创建 Office 365 E5 订阅

按照 [Office 365 开发/测试环境](office-365-dev-test-environment.md)的第 2 和 第 3 阶段的步骤，创建轻型 Office 365 开发/测试环境，如图 1 中所示。
  
**图 1：带 Azure Active Directory (AD) 租户和用户帐户的 Office 365 E5 订阅**

![Microsoft 365 企业版开发/测试环境的第 1 阶段](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> Office 365 E5 订阅试用期是 30 天，可以轻松地将该订阅的试用期扩展为 60 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。 
  
## <a name="phase-2-add-ems"></a>第 2 阶段：添加 EMS

在此阶段，注册 EMS E5 试用订阅，并将其作为 Office 365 E5 试用订阅添加到同一组织。
  
首先，添加 EMS E5 试用订阅，向全局管理员帐户分配 EMS 许可证。
  
1. 通过 Internet 浏览器的专用实例，使用全局管理员帐户凭据登录到 Office 365 门户。如需帮助，请参阅[在哪里登录 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 单击“管理员”磁贴****。
    
3. 在浏览器的“Office 管理中心”标签页的左侧导航中，单击“帐单”>“购买服务”********。
    
4. 在“购买服务”页上，找到“企业移动性 + 安全性 E5”项。将鼠标指针悬停在此项之上，然后单击“开始免费试用”************。
    
5. 在“确认订单”页上，单击“立即试用”********。
    
6. 在“订单签收”页上，单击“继续”********。
    
7. 在浏览器的“Office 365 管理中心”标签页的左侧导航中，单击“用户”>“活动用户”********。
    
8. 单击全局管理员帐户，然后针对“产品许可证”单击“编辑”********。
    
9. 在“产品许可证”窗格上，将“企业移动性 + 安全性 E5”的产品许可证设置为“打开”，单击“保存”，然后单击“关闭”两次********************。
    
> [!NOTE]
> 企业移动性 + 安全性 E5 的试订阅期为 90 天。对于永久性开发/测试环境，请使用少量许可证新建付费订阅。 
  
 ****** 如果完成了 [Office 365 开发/测试环境](office-365-dev-test-environment.md)的第 3 阶段，请为所有其他帐户（用户 2、用户 3、用户 4 和用户 5）重复前述过程的步骤 8 和 9。
  
开发/测试环境目前包含：
  
- 与你列表中的用户帐户共享相同 Azure AD 租户的 Office 365 E5 企业版和 EMS E5 试用订阅。
- 所有适当的用户帐户（无论是全局管理员帐户还是全部五个用户帐户）都可以使用 Office 365 E5 和 EMS E5。
    
图 2 显示添加 EMS 的生成配置。
  
**图 2：添加 EMS 试用订阅**

![Microsoft 365 企业版开发/测试环境的第 2 阶段](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a>第 3 阶段：创建 Windows 10 企业版计算机

在这一阶段，你创建运行 Windows 10 企业版的独立计算机。
  
### <a name="physical-computer"></a>物理计算机

获取个人计算机并在其上安装 Windows 10 企业版。你可在[此处](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)下载 Windows 10 企业版试用。
  
### <a name="virtual-machine"></a>虚拟机

使用你选择的虚拟机监控程序创建一个虚拟机并在其上安装 Windows 10 企业版。你可在[此处](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)下载 Windows 10 企业版试用。
  
### <a name="virtual-machine-in-azure"></a>Azure 中的虚拟机

要在 Microsoft Azure 中创建 Windows 10 虚拟机，你必须拥有基于 Visual Studio 的订阅******，以便有权访问 Windows 10 企业版的映像。其他类型的 Azure 订阅（如试用版和付费订阅）均无权访问此映像。
  
> [!NOTE]
> 下面的命令集使用最新版 Azure PowerShell。请参阅 [Azure PowerShell cmdlet 入门](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)。这些命令集构建了名为 WIN10 的 Windows 10 企业版虚拟机及其所需的全部基础架构，其中包括资源组、存储帐户和虚拟网络。如果你已熟悉 Azure 基础架构服务，请修改这些说明以适应当前部署的基础架构。 
  
首先，启动 Microsoft PowerShell 提示符。
  
使用以下命令登录 Azure 帐户。
  
```
Login-AzureRMAccount
```

使用以下命令获得订阅名称。
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

设置 Azure 订阅。使用正确的名称替换引号内的所有内容（包括 \< 和 > 字符）。
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

接下来，创建一个新的资源组。要确定一个唯一的资源组名称，请使用此命令列出你现有的资源组。
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

使用这些命令创建新的资源组。使用正确的名称替换引号内的所有内容（包括 \< 和 > 字符）。
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

接下来，使用这些命令创建新的虚拟网络和 WIN10 虚拟机。出现提示时，为 WIN10 提供本地管理员帐户的名称和密码，并将这些名称和密码存储在安全位置。
  
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

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a>第 4 阶段：将 Windows 10 计算机加入到 Azure AD

在创建具有 Windows 10 企业版的物理计算机或虚拟机之后，使用本地管理员帐户登录。
  
> [!NOTE]
> 对于 Azure 中的虚拟机，使用[这些说明](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)进行连接。使用本地管理员帐户的凭据登录。 
  
接下来，将 WIN10 计算机加入到 Office 365 和 EMS 订阅的 Azure AD 租户。
  
1. 在 WIN10 计算机的桌面上，依次单击“开始”>“设置”>“帐户”>“访问单位或学校”>“连接”****。
    
2. 在“设置工作或学校帐户”**** 对话框中，单击“将此设备加入到 Azure Active Directory”****。
    
3. 在“工作或学校帐户”**** 中，键入 Office 365 订阅的全局管理员帐户名称，然后单击“下一步”****。
    
4. 在“输入密码”**** 中，键入全局管理员帐户的密码，然后单击“登录”****。
    
5. 当提示你确定这是你的组织时，单击“加入”****，然后单击“完成”****。
    
6. 关闭“设置“窗口。
    
接下来，在 WIN10 计算机上安装 Office 2016。
  
1. 打开 Microsoft Edge 浏览器，使用全局管理员帐户凭据登录到 Office 365 门户。如需帮助，请参阅[在哪里登录 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在“Microsoft Office 主页”**** 标签页上，单击“安装 Office 2016”****。
    
3. 出现应执行的操作提示时，单击“运行”****，然后针对“用户帐户控制”单击“是”********。
    
4. 等待 Office 完成安装。当看到“你已设置完毕!”**** 时，单击“关闭”**** 两次。
    
图 3 显示了你的生成环境，其中包括已加入 Office 365 和 EMS 订阅的 Azure AD 租户的 WIN10 计算机。
  
**图 3：将 WIN10 计算机帐户添加到 Azure AD 租户**

![Microsoft 365 企业版开发/测试环境的第 4 阶段](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
现在你可以试验 [Microsoft 365 企业版](https://www.microsoft.com/microsoft-365/enterprise)的其他功能。
  
## <a name="next-steps"></a>后续步骤

使用这些附加文章来探索 Microsoft 365 企业版的功能：
  
- [添加移动应用管理 (MAM) 策略](https://technet.microsoft.com/library/mt764059.aspx)
    
- [注册 iOS 和 Android 设备](https://technet.microsoft.com/library/mt743077.aspx)
    
- [配置并测试高级安全管理](https://technet.microsoft.com/library/mt757250.aspx)
    
- [配置和测试高级威胁防护](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a>另请参阅

- [Microsoft 365 企业版文档](https://docs.microsoft.com/microsoft-365-enterprise/)
- [部署 Microsoft 365 企业版](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)
- [One Microsoft 云开发/测试环境](the-one-microsoft-cloud-dev-test-environment.md)
- [云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
