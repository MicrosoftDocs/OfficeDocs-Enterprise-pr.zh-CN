---
title: "管理独立的在线 SharePoint 工作组网站"
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 79a61003-4905-4ba8-9e8a-16def7add37c
description: "摘要： 管理这些过程带有独立的 SharePoint Online 工作组站点。"
ms.openlocfilehash: 516bf9d1c94992789bd8341b347a5788dbb04933
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="manage-an-isolated-sharepoint-online-team-site"></a>管理独立的在线 SharePoint 工作组网站

 **摘要：**管理这些过程带有独立的 SharePoint Online 工作组站点。
  
本文介绍常见的管理操作的独立在线 SharePoint 工作组网站。
  
## <a name="add-a-new-user"></a>添加新用户

当某个新人加入该网站时，您必须决定在网站中的参与程度：
  
- 管理： 向网站中添加新的用户帐户管理员访问组
    
- 协作活动： 将用户帐户添加到该站点成员访问组
    
- 查看： 将用户帐户添加到网站查看器访问组
    
如果您在管理用户帐户和组通过 Windows 服务器活动目录 (AD)，将相应的用户添加到使用标准 Windows 服务器 AD 用户和组管理过程的适当访问权限组和等待同步与您Office 365 的订阅。
  
如果您在管理用户帐户和组通过 Office 365，可以使用 Office 管理中心或 Microsoft PowerShell:
  
- 对于 Office 管理中心，使用已分配的用户的帐户管理员或公司管理员角色的用户帐户登录和使用组将相应的用户添加到适当的访问权限的组。
    
- 对于 PowerShell，第一个[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。若要将用户帐户添加到访问组的用户主体名称 (UPN)，使用下面的 PowerShell 命令块：
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> 对于文本文件，其中包含所有 PowerShell 命令和 Excel 配置 PowerShell 命令将生成的工作表中根据您的组和用户帐户名称、 下载[独立 SharePoint 在线团队站点部署工具包](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907)。 

若要将用户帐户添加到其显示名称的访问组，使用以下 PowerShell 命令块：

```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="add-a-new-group"></a>添加新组

若要向整个组访问权限，您必须决定站点组的所有成员的参与程度：
  
- 管理： 将组添加到该站点管理员访问组
    
- 协作活动： 向网站中添加组成员访问组
    
- 查看： 将组添加到该网站浏览者访问组
    
如果您在管理用户帐户和组通过 Windows 服务器 AD，将适当的组添加到适当的组使用正常的 Windows 服务器 AD 用户和组的管理过程，并等待与 Office 365 订阅进行同步处理。
  
如果您在管理用户帐户和组通过 Office 365，您可以使用 Office 管理中心或 PowerShell:
  
- 办公室管理的中心，使用已分配的用户的帐户管理员或公司管理员角色的用户帐户登录和使用组来向适当的访问权限的组添加到相应的组。
    
- 对于 PowerShell，第一个[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。然后，使用下列的 PowerShell 命令：
 
```
$newGroupName="<display name of the new group to add>"
$siteGrpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $newGroupName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $siteGrpName }).ObjectID
```

## <a name="remove-a-user"></a>删除用户

当某人的访问必须从站点中删除时，它们从组中删除访问它们所当前基于他们参与该网站的成员：
  
- 管理： 删除管理员访问权限的网站用户组中的用户帐户
    
- 活动的协作： 删除站点成员访问组中的用户帐户
    
- 查看： 删除站点查看器访问组中的用户帐户
    
如果您在管理用户帐户和组通过 Windows 服务器 AD，从使用正常的 Windows 服务器 AD 用户和组管理过程的适当访问权限组中删除相应的用户，并等待与 Office 365 的同步预订。
  
如果您在管理用户帐户和组通过 Office 365，您可以使用 Office 管理中心或 PowerShell:
  
- 对于 Office 管理中心，使用已分配的用户的帐户管理员或公司管理员角色的用户帐户登录和使用适当的访问权限的组中删除相应的用户组。
    
- 对于 PowerShell，第一个[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。若要通过其 UPN 访问组中删除用户帐户，请使用下面的 PowerShell 命令块：
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

要从其显示名称的访问组中删除用户帐户，使用下面的 PowerShell 命令块：
    
```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="remove-a-group"></a>删除组

若要删除整个组的访问权限，请从它们所当前成员根据他们参与该网站的访问组删除组：
  
- 管理： 删除站点管理员访问组中的组
    
- 活动的协作： 删除组成员访问权限的网站用户组
    
- 查看： 删除站点查看器访问组中的组
    
如果您在管理用户帐户和组通过 Windows 服务器的 Active Directory，从使用普通 Windows 服务器 AD 用户和组管理过程的适当访问权限组中删除相应的组并等待同步与您Office 365 的订阅。
  
如果您在管理用户帐户和组通过 Office 365，您可以使用 Office 管理中心或 PowerShell:
  
- 办公室管理的中心，使用已分配的用户的帐户管理员或公司管理员角色的用户帐户登录，然后使用组从适当的访问权限组中删除相应的组。
    
- 对于 PowerShell，第一个[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。    
若要从使用显示名称访问组中删除一个组，使用下面的 PowerShell 命令块：
    
```
$groupMemberName="<display name of the group to remove>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="create-a-documents-subfolder-with-custom-permissions"></a>使用自定义权限创建一个文档的子文件夹

在某些情况下，子集的独立站点内工作的人需要更多私人场所进行协作。SharePoint Online 网站，可以在网站的文档文件夹中创建子文件夹并指定自定义权限。那些没有权限看不到子文件夹。
  
若要使用自定义权限创建一个文档的子文件夹，请执行以下操作：
  
1. 是网站的管理员访问权限组成员的帐户登录到 Office 365。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 转到独立的工作组站点并单击**文档**。
    
3. 浏览到该文件夹的文档文件夹中将包含具有自定义权限的子文件夹，创建该文件夹，然后再打开它。
    
4. 单击"共享"。
    
5. 单击**与共享 > 高级**。
    
6. 单击**停止继承权限**，然后单击**确定**。
    
7. 单击"共享"。
    
8. 单击**与共享 > 高级**。
    
9. 单击**授予权限 > 与共享 > 高级**。
    
10. 在权限页上单击**\<网站名称 > 列表中的成员**。
    
11. 在**\<网站名称 > 成员**页上，选择成员访问权限的网站用户组旁边的复选标记，单击**操作**，单击**用户从组中删除**，然后单击**确定**。
    
12. 若要将特定成员添加到此子文件夹，请单击**新建 > 添加用户**。
    
13. 在**共享**对话框中，键入可以进行协作的子文件夹中的文件，然后单击**共享**的用户帐户的名称。
    
14. 刷新网页以查看新的结果。
    
15. 在左侧导航区域中的**组**中，单击**\<网站名称 > 访问者**组和使用步骤 11-14 （根据需要） 可以查看子文件夹中的文件的用户帐户的设置。
    
16. 在左侧导航区域中的**组**，单击**\<网站名称 > 所有者**组和使用步骤 11-14 （根据需要），可以管理的子文件夹中的权限的用户帐户的设置。
    
17. 关闭您的浏览器中的**用户和用户组**选项卡。
    
## <a name="see-also"></a>See Also

[SharePoint Online 的独立的团队站点](isolated-sharepoint-online-team-sites.md)
  
[设计独立的在线 SharePoint 工作组网站](design-an-isolated-sharepoint-online-team-site.md)
  
[安全解决方案](security-solutions.md)

[部署独立的在线 SharePoint 工作组网站](deploy-an-isolated-sharepoint-online-team-site.md)



