---
title: 部署独立 SharePoint Online 团队网站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: 摘要： 部署新独立的 SharePoint Online 团队网站与这些分步说明。
ms.openlocfilehash: e71564248716523a53fcdda48f3a9fdc6349a2c5
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914947"
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a>部署独立 SharePoint Online 团队网站

 **摘要：** 部署新独立的 SharePoint Online 团队网站与这些分步说明。
  
本文是针对创建和配置 Microsoft Office 365 中的一个独立的 SharePoint Online 团队网站的分步部署指南。这些步骤假定使用三个默认 SharePoint 组和相应的权限级别，与单个基于 Azure Active Directory AD 的访问组每个级别的访问。
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a>阶段 1： 创建和填充工作组网站的访问组

在此阶段中，可以创建三个默认 SharePoint 组的三个 Azure 基于 AD 的访问组和填充它们与相应的用户帐户。
  
> [!NOTE]
> 下面的步骤假定所有必要的用户帐户已存在且已分配相应的许可证。如果没有，请将其添加并分配许可证，然后再继续步骤 1。 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a>步骤 1： 列表的网站 SharePoint Online 管理员

确定一组的用户帐户在对应于独立的工作组网站的 SharePoint Online 管理员。
  
如果您正在管理用户帐户和组通过 Office 365，并且想要使用 Windows PowerShell，使列表的用户主体名称 (Upn) (示例 UPN: belindan@contoso.com)。
  
### <a name="step-2-list-the-members-for-the-site"></a>步骤 2： 列出网站的成员

确定对独立的工作组网站的那些用户将在网站中存储的资源协作的成员对应的用户帐户的组。
  
如果您正在管理用户帐户和组通过 Office 365，并且想要使用 PowerShell，使其 Upn 列表。如果有大量的网站成员，您可以在文本文件中存储的 Upn 列表，并将其添加所有与单个 PowerShell 命令。
  
### <a name="step-3-list-the-viewers-for-the-site"></a>步骤 3： 列出网站的查看者

确定用户帐户对应的独立的工作组网站，那些可以查看网站中存储的资源，但不是修改这些或直接协作及其内容查看者的组。
  
如果您正在管理用户帐户和组通过 Office 365，并且想要使用 PowerShell，使其 Upn 列表。如果有大量的网站成员，您可以在文本文件中存储的 Upn 列表，并将其添加所有与单个 PowerShell 命令。
  
网站的查看者可能包括管理层、 法律顾问或执行部门间利益干系人。
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a>步骤 4: Azure AD 中创建网站的三个访问组

您需要在 Azure AD 中创建以下访问组：
  
- 网站管理员 （其中将包含步骤 1 中的列表）
    
- 网站成员 （其中将包含从步骤 2 列表）
    
- 网站查看器 （其中将包含从步骤 3 列表）
    
1. 在浏览器中，转到 Azure 门户在[https://portal.azure.com](https://portal.azure.com)和使用已分配与用户管理管理员或公司管理员角色的帐户凭据登录。
    
2. 在 Azure 门户中，单击“**Azure Active Directory”>“组**”。
    
3. 在“**组 - 所有组**”边栏选项卡上，单击“**+ 新建组**”。
    
4. 在“**组**”边栏选项卡上：
    
  - 在“**组类型**”中，选择“**Office 365**”。
    
  - 在**名称**中键入组名称。
    
  - 在**说明组**中键入组的说明。
    
  - 在“**成员身份**”类型中，选择“**已分配**”。
    
5. 单击“**创建**”，然后关闭“**组**”边栏选项卡。
    
6. 对其他组重复步骤 3-5。
    
> [!NOTE]
> 您需要使用 Azure 门户网站创建的组，以便他们已启用的 Office 功能。如果更高版本，SharePoint Online 独立的网站被配置为具有加密文件并将权限分配给特定组 Azure 信息保护 (AIP) 标签的高度机密网站，允许的组必须已创建的 Office 功能启用。创建它之后，您无法更改 Azure AD 组的 Office 功能设置。 
  
下面是与三个网站的访问组您生成的配置。
  
![三个适用于部署独立 SharePoint Online 网站的访问组。](media/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a>步骤 5。向 access 组添加用户帐户

在此步骤中，执行以下操作：
  
1. 步骤 1 中的用户列表添加到网站管理员访问组
    
2. 步骤 2 中的用户列表添加到网站成员访问组
    
3. 步骤 3 中的用户列表添加到网站查看器访问组
    
如果您在管理用户帐户和通过 Windows Server AD 的组，将用户添加到适当的访问组使用普通的 Windows Server AD 用户和组管理过程并等待与 Office 365 订阅的同步。
  
如果您在管理用户帐户和组通过 Office 365，您可以使用 Office 管理中心或 PowerShell。如果您有任何访问组重复组名称，您应使用 Office 管理中心。
  
对于 Office 管理中心中，使用已分配的用户帐户管理员或公司管理员角色的用户帐户登录，并使用组添加相应的用户帐户和组添加到适当的访问组。
  
Powershell，第一个[使用 Azure Active Directory V2 PowerShell 模块的连接](https://go.microsoft.com/fwlink/?linkid=842218)。
  
接下来，使用以下命令块向 access 组添加单个用户帐户：
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> 对于包含所有 PowerShell 命令和 Excel 的文本文件配置工作表中生成 PowerShell 命令的基于您的组和用户帐户名，下载[独立 SharePoint Online 团队网站部署工具包](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907)。 
  
如果您在文本文件中存储的用户帐户的任何访问组 Upn，您可以使用以下 PowerShell 命令块以将他们添加一次：
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

对于 PowerShell 中，使用以下命令块向 access 组添加单个组：
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

结果应如下：
  
- 网站管理员 Azure AD 组包含的网站管理员用户帐户或组
    
- 网站成员 Azure AD 组包含的网站成员的用户帐户或组
    
- 网站查看者 Azure AD 组包含用户帐户或组的只能查看网站内容
    
验证每个访问组与 Office 管理中心或以下 PowerShell 命令块的组成员的列表：
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

下面是与填充的用户帐户或组的三个网站的访问组您生成的配置。
  
![三个使用用户帐户填充的访问组。](media/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a>第 2 阶段： 创建和配置独立的工作组网站

在此阶段中，您将创建独立的 SharePoint Online 网站，并配置默认 SharePoint Online 权限级别以使用新 Azure 基于 AD 的访问组的权限。
  
首先，通过以下步骤创建 SharePoint Online 团队网站。
  
1. 请通过还可用于管理 SharePoint Online 团队网站的帐户（即 SharePoint Online 管理员帐户）登录 Office 365 门户。如需帮助，请参阅[在何处登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在磁贴列表中，单击“SharePoint”****。
    
3. 在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。********
    
4. 在“创建网站”页中，单击“团队网站”********。
    
5. 在**网站名称**框中，键入工作组网站的名称。 
    
6. 在**工作组网站说明中，** 键入网站的用途的可选说明。
    
7. 在“隐私设置”中，选择“专用 - 仅成员可以访问此网站”，然后单击“下一步”************。
    
8. 在“希望添加哪些人员?”窗格中，单击“完成”********。
    
接下来，在新 SharePoint Online 团队网站上，配置权限。
  
1. 在工具栏中，依次单击设置图标和“网站权限”****。
    
2. 在“网站权限”窗格中，单击“高级权限设置”********。
    
3. 在浏览器的新“权限”标签页中，单击“访问请求设置”********。
    
4. 在**访问请求设置**对话框中，清除**要共享的网站和单独的文件和文件夹的允许成员**并**允许访问请求**（以便清除所有三个复选框），然后单击**确定**。
    
5. 在浏览器的**权限**选项卡上，单击**\<网站名称 > 成员**列表中。
    
6. 在“人员和组”中，单击“新建”********。
    
7. 在**共享**对话框中，键入网站成员访问组的名称，选择它，，然后单击**共享**。
    
8. 单击浏览器上的后退按钮。
    
9. 单击**\<网站名称 > 所有者**列表中。
    
10. 在“人员和组”中，单击“新建”********。
    
11. 在**共享**对话框中，键入网站管理员访问组的名称，选择它，，然后单击**共享**。
    
12. 单击浏览器上的后退按钮。
    
13. 单击**\<网站名称 > 访问者**列表中。
    
14. 在“人员和组”中，单击“新建”********。
    
15. 在**共享**对话框中，键入网站的查看者访问组的名称，选择它，，然后单击**共享**。
    
16. 关闭浏览器的“权限”标签页****。
    
以下是这些权限设置的结果：
  
- **\<网站名称 > 所有者**SharePoint 组包含所有成员中具有**完全控制**权限级别的网站管理员访问组。
    
- **\<网站名称 > 成员**中的所有成员都具有**编辑**权限级别的网站成员访问组所在的 SharePoint 组。
    
- **\<网站名称 > 访问者**中所有成员具有**读取**权限级别的网站查看器访问组所在的 SharePoint 组。
    
- 要邀请其他成员成员或非成员请求访问的功能被禁用。
    
下面是生成配置与网站配置为使用三个访问组，填入用户帐户或 Azure AD 组的三个 SharePoint 组。
  
![包含访问组和用户帐户的独立 SharePoint Online 网站的最终配置。](media/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
您和网站，通过组成员的访问组中，之一的成员可以立即协作使用网站的资源。
  
## <a name="next-step"></a>后续步骤

当您需要更改网站的访问组成员身份或创建具有自定义权限的文档文件夹时，请参阅[Manage 独立的 SharePoint Online 团队网站](manage-an-isolated-sharepoint-online-team-site.md)。
  
## <a name="see-also"></a>另请参阅

[独立 SharePoint Online 团队网站](isolated-sharepoint-online-team-sites.md)
  
[设计独立 SharePoint Online 团队网站](design-an-isolated-sharepoint-online-team-site.md)
  
[管理单独的 SharePoint Online 团队网站](manage-an-isolated-sharepoint-online-team-site.md)
  
[安全解决方案](security-solutions.md)



