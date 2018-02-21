---
title: "在开发/测试环境中保护 SharePoint Online 网站"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "摘要： 在开发/测试环境中创建公共、 私人、 敏感和高度机密 SharePoint Online 的工作组网站。"
ms.openlocfilehash: a79ba4aa5dea043884d8540fb642bbb742d08222
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a>在开发/测试环境中保护 SharePoint Online 网站

 **摘要：**开发/测试环境中创建公共、 私人、 敏感和高度机密 SharePoint Online 的工作组网站。
  
本文提供了分步说明创建包含四种不同类型的[安全 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)解决方案的 SharePoint Online 工作组站点的开发/测试环境。
  
![安全 SharePoint Online 开发/测试环境中的所有四个团队网站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
使用此开发/测试环境来试验信息保护行为，并根据具体要求微调设置，然后在生产中部署 SharePoint Online 团队网站。
  
## <a name="phase-1-create-your-devtest-environment"></a>阶段 1：创建开发/测试环境

在此阶段，将获取用于虚拟组织的 Office 365 和企业移动性 + 安全性的试用订阅。
  
首先，按照**第二阶段**的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)中的说明进行操作。
  
接下来，EMS 试用订阅注册，即可将其添加到作为 Office 365 的试用订阅的同一组织。
  
1. 如果需要请登录到您的订购试用期的全局管理员帐户的凭据对 Office 365 门户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 单击“管理”磁贴。
    
3. 在浏览器的“Office 管理中心”选项卡的左侧导航中，单击“帐单”>“购买服务”。
    
4. **购买服务**页上找到**企业移动 + 安全 E5**项。将鼠标指针悬停在其上，单击**启动免费试用版**。
    
5. 在“确认订单”页中，单击“立即试用”。
    
6. 在“订单签收”页中，单击“继续”。
    
接下来，为全局管理员帐户启用企业移动性 + 安全性 E5 许可证。
  
1. 在浏览器的“Office 365 管理中心”选项卡的左侧导航中，单击“用户”>“活动用户”。
    
2. 单击您的全局管理员帐户，然后单击**编辑****产品**许可证。
    
3. **产品许可证**的窗格中，在打开产品许可证**的企业移动性 + 安全 E5**到**上**，单击**保存**，然后两次单击**关闭**。
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a>阶段 2：创建和配置 Azure Active Directory (AD) 组和用户

此阶段为虚构组织创建和配置 Azure AD 组和用户。
  
首先，通过 Azure 门户为典型组织创建一系列组。
  
1. 在浏览器中，创建一个单独的选项卡，然后转到在[https://portal.azure.com](https://portal.azure.com)Azure 的门户。如果需要请为您的 Office 365 E5 试用订阅登录的全局管理员帐户的凭据。
    
2. 在 Azure 门户中，单击“Azure Active Directory”>“用户和组”>“所有组”。
    
3. 在“所有组”边栏选项卡上，单击“+ 新建组”。
    
4. 在“组”边栏选项卡上：
    
  - 在“名称”中键入“高层管理人员”。
    
  - 在“成员身份”中选择“已分配”。
    
  - 对“启用 Office 功能”单击“是”。
    
5. 单击“创建”，然后关闭“组”边栏选项卡。
    
6. 对以下组名称重复步骤 3-5：
    
  - IT 人员
    
  - 研究人员
    
  - 正式员工
    
  - 市场营销人员
    
  - 销售人员
    
7. 使浏览器中的 Azure 门户选项卡保持打开状态。
    
接下来，您将配置自动授权，使您的组的成员会自动分配为 Office 365 和 EMS 订阅许可证。
  
1. 在 Azure 门户中，单击“Azure Active Directory”>“许可证”>“所有产品”。
    
2. 在列表中，选择**企业移动 + 安全 E5**和**Office 365 企业 E5**，然后单击**分配**。
    
3. 在“分配许可证”边栏选项卡中，单击“用户和组”。
    
4. 在组列表中，选择以下各项：
    
  - 高层管理人员
    
  - IT 人员
    
  - 研究人员
    
  - 正式员工
    
  - 市场营销人员
    
  - 销售人员
    
5. 单击**选择**，然后单击**分配**。
    
6. 关闭浏览器中的 Azure 门户选项卡。
    
接下来，[连接到 Azure Active Directory V2 PowerShell 模块](https://go.microsoft.com/fwlink/?linkid=842218)。
  
填写您的组织名称、 您所在的位置和常见的密码，并再从 PowerShell 命令提示符或集成脚本环境 (ISE) 来创建用户帐户并将其添加到它们的组运行这些命令：
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> 此处使用公用密码旨在自动配置开发/测试环境，简化配置过程。 但不建议生产订阅这样做。 
  
使用下列步骤验证基于组的授权正常工作。
  
1. 在浏览器的“Microsoft Office 主页”标签页中，单击“管理”磁贴。
    
2. 在浏览器的新“Office 管理中心”标签页中，单击“用户”。
    
3. 在用户列表中，单击“CEO”。
    
4. 在列出 CEO 用户帐户属性的窗格中，验证已向其分配“企业移动性 + 安全性 E5”和“Office 365 企业版 E5”许可证（位于“产品许可证”中）。
    
## <a name="phase-3-create-office-365-labels"></a>阶段 3：创建 Office 365 标签

此阶段将针对 SharePoint Online 团队网站文档文件夹的不同安全级别创建标签。
  
1. 如果需要请使用 Internet 浏览器的专用实例并登录到您的 Office 365 E5 试用的全局管理员帐户具有 Office 365 门户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在“Microsoft Office 主页”标签页中，单击“管理”磁贴。
    
3. 您的浏览器的新**办公室管理中心**标签，请单击**中心管理 > 安全&amp;法规遵从性**。
    
4. 从新**家庭-安全&amp;法规遵从性**选项卡上的浏览器中，单击**分类 > 标签**。
    
5. 在“开始”>“标签”窗格中，单击“创建标签”。
    
6. 在**标签名称**窗格中，键入**内部公共**的，然后单击**下一步**。
    
7. 在“标签设置”窗格中，单击“下一步”。
    
8. 上的**查看设置**窗格中，单击**创建此标签**，然后单击**关闭**。
    
9. 对以下标签重复步骤 5-8：
    
  - Private
    
  - 敏感
    
  - 高度机密
    
10. 在“开始”>“标签”窗格中，单击“发布标签”。
    
11. 在“选择要发布的标签”窗格中，单击“选择要发布的标签”。
    
12. 在“选择标签”窗格中，单击“添加”并选择全部四个标签。
    
13. 单击“完成”。
    
14. 在“选择要发布的标签”窗格中，单击“下一步”。
    
15. 在“选择位置”窗格中，单击“下一步”。
    
16. 在**您的策略名称**窗格中，在**名称**中键入**示例组织中**，然后单击**下一步**。
    
17. 上的**查看设置**窗格中，单击**发布标签**，然后单击**关闭**。
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a>阶段 4：创建 SharePoint Online 团队网站

在此阶段中，将为示例组织创建和配置四种类型的 SharePoint Online 团队网站。
  
### <a name="organization-wide-team-site"></a>组织范围团队网站

要创建基线公共 SharePoint Online 团队网站，请执行以下操作：
  
1. 如果需要，请使用本地计算机上的浏览器，并使用全局管理员帐户登录 Office 365 门户。 如需帮助，请参阅[如何登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磁贴列表中，单击“SharePoint”。
    
3. 在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。
    
4. 在“创建网站”页中，单击“团队网站”。
    
5. 在“网站名称”中，键入“组织范围”。 
    
6. 在“团队网站描述”中，键入“用于整个组织的 SharePoint 网站”。
    
7. 在**隐私设置**选择**公用-组织中的任何人都可以访问该网站**，，然后单击**下一步**。
    
8. 在“希望添加哪些人员?”窗格中，单击“完成”。
    
接下来，针对内部公共标签配置组织范围团队网站的文档文件夹。
  
1. 在您的浏览器**组织总部范围**选项卡上，单击**文档**。
    
2. 单击设置图标，然后单击“库设置”。
    
3. 在“权限和管理”下，单击“向此库中的项应用标签”。
    
4. 在**设置应用标签**，选择**内部公共**的，然后单击**保存**。
    
生成的配置如下。
  
![适用于全组织公共 SharePoint Online 团队网站的基线级保护。](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a>项目 1 团队网站

要为组织内的项目创建基线专用 SharePoint Online 团队网站，请执行以下操作：
  
1. 如果需要，请使用本地计算机上的浏览器，并使用全局管理员帐户登录 Office 365 门户。 如需帮助，请参阅[如何登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磁贴列表中，单击“SharePoint”。
    
3. 在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。
    
4. 在“创建网站”页中，单击“团队网站”。
    
5. 在“网站名称”中，键入“项目 1”。 
    
6. 在**团队站点说明，**键入**项目 1 的 SharePoint 网站**。
    
7. 在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。
    
8. 在“希望添加哪些人员?”窗格中，单击“完成”。
    
接下来，针对专用标签配置项目 1 团队网站的文档文件夹。
  
1. 在浏览器的“项目 1 - 主页”标签页中，单击“文档”。
    
2. 单击设置图标，然后单击“库设置”。
    
3. 在“权限和管理”下，单击“向此库中的项应用标签”。
    
4. 在**设置应用标签**，选择**专用**，然后单击**保存**。
    
生成的配置如下。
  
![适用于 Project1 专用 SharePoint Online 团队网站的基线级保护。](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a>市场营销活动团队网站

要为市场营销活动资源创建敏感级别的独立 SharePoint Online 团队网站，请执行以下操作：
  
1. 在您的本地计算机上使用浏览器，登录到 Office 365 门户使用全局管理员帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磁贴列表中，单击“SharePoint”。
    
3. 在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。
    
4. 在“创建网站”页中，单击“团队网站”。
    
5. 在“团队网站名称”中，键入“市场营销活动”。
    
6. 在“团队网站描述”中，键入“用于市场营销活动资源的 SharePoint 网站(敏感)”。
    
7.  在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。
    
8. 在“希望添加哪些人员?”窗格中，单击“完成”。
    
9. 在您的浏览器工具条中，在新的**市场营销活动**选项卡上单击设置图标，然后单击**网站权限**。
    
10. 在“网站权限”窗格中，单击“高级权限设置”。
    
11. 在浏览器的新“权限”标签页中，单击“访问请求设置”。
    
12. 在**访问请求设置**对话框中，清除**允许成员共享的网站和个别文件和文件夹**和**允许成员若要邀请其他人到网站用户组成员**复选框，键入**ITAdmin1 @**\<您组织名称 >**。 onmicrosoft.com**在**将所有访问请求都发送**，然后单击**确定**。
    
13. 单击列表中的“市场营销活动成员”。
    
14. 在“人员和组”页中，单击“新建”。
    
15. 在**共享**对话框中，键入**市场营销人员**，选择它，，然后单击**共享**。
    
16. **Researcher1**用户帐户，请重复步骤 14 和 15。
    
17. 单击浏览器上的后退按钮。
    
18. 单击列表中的**市场营销活动的所有者**。
    
19. 在“人员和组”页中，单击“新建”。
    
20. 在**共享**对话框中，键入**的 IT 人员**，选择它，，然后单击**共享**。
    
21. 单击浏览器上的后退按钮。
    
22. 关闭您的浏览器中的**用户和用户组**选项卡，单击在浏览器中，**市场营销活动主页**选项卡上，然后关闭**网站权限**窗格。
    
权限的配置结果如下所示：
  
- 市场营销活动-成员：SharePoint 组仅包含“市场营销活动”组（其中包含全局管理员用户帐户）、“市场营销人员”组（其中包含 Marketing1 和 Marketing2 用户帐户）以及 Researcher1 用户帐户。
    
- 市场营销活动-所有者：SharePoint 组仅包含“IT 人员”组（其中仅包含 ITAdmin1 和 ITAdmin2 用户帐户）。
    
- 市场营销活动-访问者：SharePoint 组不包含任何组或用户帐户。
    
- 成员不能修改网站级权限（此设置只能由营销活动-所有者组的成员执行）。
    
- 其他用户帐户无法访问网站或它的资源，但可以请求访问该网站，将电子邮件发送给 ITAdmin1 用户帐户邮箱。
    
接下来，针对敏感标签配置市场营销活动团队网站的文档文件夹。
  
1. 在浏览器的“市场营销活动 - 主页”标签页中，单击“文档”。
    
2. 单击设置图标，然后单击“库设置”。
    
3. 在“权限和管理”下，单击“向此库中的项应用标签”。
    
4. 在**设置应用标签**，选择**敏感**，，然后单击**保存**。
    
接下来，配置数据丢失防护 (DLP) 策略，以便在用户共享关于含敏感标签的 SharePoint Online 团队网站（包括组织外的营销活动网站）的文档时进行通知。
  
1. 从**Microsoft Office 主页**选项卡上的在浏览器中，单击**安全&amp;法规遵从性**平铺。
    
2. 对新**安全&amp;法规遵从性**在您的浏览器选项卡上，单击**数据丢失防范 > 策略**。
    
3. 在“数据丢失防护”窗格中，单击“+ 创建策略”。
    
4. 在**从模板开始创建自定义策略或**窗格中，单击**自定义**，然后单击**下一步**。
    
5. **名称您的策略**中，在**名称**中键入**敏感标签 SharePoint Online 工作组站点**，然后单击**下一步**。
    
6. 在“选择位置”窗格中，单击“允许选择特定位置”，然后单击“下一步”。
    
7. 在位置列表中，禁用**Exchange 电子邮件**帐户和**OneDrive 帐户**位置，然后单击**下一步**。
    
8. 在“自定义要保护的敏感信息类型”窗格中，单击“编辑”。
    
9. 在**选择要保护的内容的类型**窗格中，单击下拉列表框中，**添加**，然后单击**标签**。
    
10. 在**标签**窗格中，单击**+ 添加**，选择**敏感**标签，单击**添加**，然后单击**完成**。
    
11. 在“选择要保护的内容类型”窗格中，单击“保存”。
    
12. 在“自定义要保护的敏感信息类型”窗格中，单击“下一步”。
    
13. 在“如果检测到敏感信息，希望采取什么操作?”窗格中，单击“自定义提示和电子邮件”。
    
14. 在“自定义策略提示和电子邮件通知”窗格中，单击“自定义策略提示文本”。
    
15. 在文本框中，键入或粘贴以下内容：
    
  - 要与组织外部的用户共享，请下载并打开文件。 依次单击“文件”、“保护文档”、“使用密码加密”，然后指定强密码。 通过单独的电子邮件或其他通信方式发送密码。
    
16. 单击“**确定**”。
    
17. 在**您想要我们检测敏感信息办？**窗格中，清除**阻止某些人共享，并限制对内容的访问**复选框，然后单击**下一步**。
    
18. 在**所需的策略或测试的事情，首先打开？**窗格中，单击**是，立即启用**，然后单击**下一步**。
    
19. 在**查看设置**窗格上，单击**创建**，然后单击**关闭**。
    
生成的配置如下。
  
![适用于市场营销活动专用独立 SharePoint Online 团队网站的敏感级保护。](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a>公司策略团队网站

若要针对组织首席执行官的公司战略资源创建高度机密级别的独立 SharePoint Online 团队网站，请执行以下操作：
  
1. 如果需要，请使用本地计算机上的浏览器，并使用全局管理员帐户登录 Office 365 门户。 如需帮助，请参阅[如何登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磁贴列表中，单击“SharePoint”。
    
3. 在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。
    
4. 在“创建网站”页中，单击“团队网站”。
    
5. 在“团队网站名称”中，键入“公司战略”。
    
6. 在“团队网站描述”中，键入“针对公司战略的 SharePoint 网站(高度机密)”。
    
7.  在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。
    
8. 在“希望添加哪些人员?”窗格中，单击“完成”。
    
9. 在您的浏览器工具条中，在新的**公司策略**选项卡上单击设置图标，然后单击**网站权限**。
    
10. 在“网站权限”窗格中，单击“高级权限设置”。
    
11. 在浏览器的新“权限”标签页中，单击“访问请求设置”。
    
12. 在**访问请求设置**对话框中，清除**允许成员共享的网站和个别文件和文件夹**，并**允许成员要邀请到网站的成员组的其他人**（以便所有三个复选框都被清除），然后单击**确定**。
    
13. 单击列表中的**成员的公司战略**。
    
14. 在“人员和组”页中，单击“新建”。
    
15. 在**共享**对话框中，键入**C 套件**，选择它，然后单击**共享**。
    
16. 单击列表中的**公司策略的所有者**。
    
17. 在“人员和组”页中，单击“新建”。
    
18. 在**共享**对话框中，键入**的 IT 人员**，选择它，，然后单击**共享**。
    
19. 单击浏览器上的后退按钮。
    
20. 关闭您的浏览器中的**用户和用户组**选项卡，单击您的浏览器中的**公司战略总部**选项卡，然后关闭**网站权限**窗格。
    
权限的配置结果如下所示：
  
- 公司战略-成员：SharePoint 组仅包含“高层管理人员”组（其中仅包含 CEO、CFO和 CIO 用户帐户）和“公司战略”组（其中仅包含全局管理员用户帐户）。
    
- **公司战略负责人**SharePoint 组包含仅**IT staff**组 （其中包含仅 ITAdmin1 和 ITAdmin2 用户帐户）。
    
- 公司战略-访问者：SharePoint 组不包含任何组或用户帐户。
    
- 成员不能修改网站级别权限（仅“公司战略-所有者”组的成员才可进行修改）。
    
- 其他用户帐户无法访问网站或其资源，也无法请求访问网站。 网站的其他权限必须由全局管理员或“公司战略-所有者”组的成员履行。
    
接下来，针对高度机密标签配置公司战略团队网站的文档文件夹。
  
1. 在浏览器的“公司战略-主页”标签页中，单击“文档”。
    
2. 单击设置图标，然后单击“库设置”。
    
3. 在“权限和管理”下，单击“向此库中的项应用标签”。
    
4. 在**设置应用标签**，选择**高度机密**，然后单击**保存**。
    
接下来，配置 DLP 策略，当用户在具有“高度机密”标签的 SharePoint Online 团队网站（包括组织外的公司战略网站）上共享文档时，该策略会阻止用户。
  
1. 如果需要请使用本地计算机上的浏览器，到 Office 365 门户拥有安全管理员或公司管理员角色的帐户登录。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 从**Microsoft Office 主页**选项卡上的在浏览器中，单击**安全&amp;法规遵从性**平铺。
    
3. 对新**安全&amp;法规遵从性**在您的浏览器选项卡上，单击**数据丢失防范 > 策略**。
    
4. 在“数据丢失防护”窗格中，单击“+ 创建策略”。
    
5. 在**从模板开始创建自定义策略或**窗格中，单击**自定义**，然后单击**下一步**。
    
6. **名称您的策略**中，在**名称**中键入**高度机密的标签 SharePoint Online 工作组站点**，然后单击**下一步**。
    
7. 在“选择位置”窗格中，单击“允许选择特定位置”，然后单击“下一步”。
    
8. 在位置列表中，禁用**Exchange 电子邮件**帐户和**OneDrive 帐户**位置，然后单击**下一步**。
    
9. 在“自定义要保护的敏感信息类型”窗格中，单击“编辑”。
    
10. 在**选择要保护的内容的类型**窗格中，单击下拉列表框中，**添加**，然后单击**标签**。
    
11. **标签**的窗格中，单击**+ 添加**，选择**高度机密**标签，单击**添加**，然后单击**完成**。
    
12. 在“选择要保护的内容类型”窗格中，单击“保存”。
    
13. 在“自定义要保护的敏感信息类型”窗格中，单击“下一步”。
    
14. 在“如果检测到敏感信息，希望采取什么操作?”窗格中，单击“自定义提示和电子邮件”。
    
15. 在“自定义策略提示和电子邮件通知”窗格中，单击“自定义策略提示文本”。
    
16. 在文本框中，键入或粘贴以下内容：
    
  - 要与组织外部的用户共享，请下载并打开文件。 依次单击“文件”、“保护文档”、“使用密码加密”，然后指定强密码。 通过单独的电子邮件或其他通信方式发送密码。
    
17. 单击“**确定**”。
    
18. 在**您想要我们检测敏感信息办？**窗格中，选择**需要重写的理由**，然后再单击**下一步**。
    
19. 在**所需的策略或测试的事情，首先打开？**窗格中，单击**是，立即启用**，然后单击**下一步**。
    
20. 在**查看设置**窗格上，单击**创建**，然后单击**关闭**。
    
接下来，按照[使用 Office 365 管理中心激活 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) 中的说明进行操作。
  
接下来，通过执行以下步骤，使用新作用域内策略以及保护和权限的子标签来配置 Azure 信息保护：
  
1. Office 365 门户拥有安全管理员或公司管理员角色的帐户登录。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在浏览器的单独选项卡中，转到 Azure 门户 ([https://portal.azure.com](https://portal.azure.com))。
    
3. 如果这是首次配置 Azure 信息保护，请参见以下[说明](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。
    
4. 在列表窗格中，单击**更多服务**，键入**信息**，，然后单击**Azure 信息保护**。
    
5. **Azure 信息保护**刀片式服务器，，单击**范围策略 > 添加新策略 +**。
    
6. 在“策略名称”中键入“CompanyStrategy”，并在“描述”中键入“公司策略团队网站中文档的标签”。
    
7. 单击“选择获取此策略的用户或组”>“用户/组”，然后选择“高层管理人员”。
    
8. 单击“选择”>“确定”。
    
9. 对于“高度机密”标签，请单击省略号 (…)，然后单击“添加子标签”。
    
10. 在“名称”中键入子标签的名称，并在“描述”中键入标签的描述。
    
11. 在“为包含此标签的文档和电子邮件设置权限”中，单击“保护”。
    
12. 在“保护”部分中，单击“Azure (云密钥)”。
    
13. 在“保护”边栏选项卡中，在“保护设置”下，单击“+ 添加权限”。
    
14. 在“添加权限”边栏选项卡的“指定用户和组”下，单击“+ 浏览目录”。
    
15. 在**AAD 的用户和组**窗格中，选择**C 套件**，，然后单击**选择**。
    
16. 在**选择权限从预设**清除**打印**、**复制和内容的提取**和**转发**复选框。
    
17. 单击**确定**两次。
    
18. 在“子标签”边栏选项卡上，单击“保存”。
    
19. 关闭“新作用域内策略”边栏选项卡。
    
20. 在**Azure 信息保护的指定了作用域策略**刀片式服务器，单击**发布**，然后单击**是**。
    
要保护与 Azure 的信息保护和此新的标签文档，则必须在测试机器上[安装 Azure 信息保护客户端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)、 从 Office 365 管理门户安装 Office，**中的帐户然后登录从 Microsoft WordC 套件**组您的订购试用期。
  
生成的配置如下。
  
![适用于公司策略专用独立 SharePoint Online 团队网站的高度机密级保护。](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
现在，可以在这四个网站中创建文档，并使用试用订阅中的各种用户帐户进行访问测试。
  
下面是针对全部四个 SharePoint Online 团队网站的整体配置。
  
![安全 SharePoint Online 开发/测试环境中的所有四个团队网站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a>后续步骤

如果已准备好进行安全 SharePoint Online 网站的生产部署，请参阅[保护 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)，了解详细信息，获取分步部署文章的链接。
  
## <a name="see-also"></a>另请参阅

[SharePoint Online 网站和文件保护](secure-sharepoint-online-sites-and-files.md)
  
[安全解决方案](security-solutions.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
  
[为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




