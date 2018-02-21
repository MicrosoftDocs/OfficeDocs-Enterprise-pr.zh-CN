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
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 79a61003-4905-4ba8-9e8a-16def7add37c
description: "摘要： 管理这些过程带有独立的 SharePoint Online 工作组站点。"
ms.openlocfilehash: bc6a3487f8e7dd6d6c3c0c8a38d2ac85e3565091
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="manage-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="7765d-103">管理独立的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="7765d-103">Manage an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="7765d-104">**摘要：**管理这些过程带有独立的 SharePoint Online 工作组站点。</span><span class="sxs-lookup"><span data-stu-id="7765d-104">**Summary:** Manage your isolated SharePoint Online team site with these procedures.</span></span>
  
<span data-ttu-id="7765d-105">本文介绍常见的管理操作的独立在线 SharePoint 工作组网站。</span><span class="sxs-lookup"><span data-stu-id="7765d-105">This article describes common management operations for an isolated SharePoint Online team site.</span></span>
  
## <a name="add-a-new-user"></a><span data-ttu-id="7765d-106">添加新用户</span><span class="sxs-lookup"><span data-stu-id="7765d-106">Add a new user</span></span>

<span data-ttu-id="7765d-107">当某个新人加入该网站时，您必须决定在网站中的参与程度：</span><span class="sxs-lookup"><span data-stu-id="7765d-107">When someone new joins the site, you must decide their level of participation in the site:</span></span>
  
- <span data-ttu-id="7765d-108">管理： 向网站中添加新的用户帐户管理员访问组</span><span class="sxs-lookup"><span data-stu-id="7765d-108">Administration: Add the new user account to the site admins access group</span></span>
    
- <span data-ttu-id="7765d-109">协作活动： 将用户帐户添加到该站点成员访问组</span><span class="sxs-lookup"><span data-stu-id="7765d-109">Active collaboration: Add the user account to the site members access group</span></span>
    
- <span data-ttu-id="7765d-110">查看： 将用户帐户添加到网站查看器访问组</span><span class="sxs-lookup"><span data-stu-id="7765d-110">Viewing: Add the user account to the site viewers access group</span></span>
    
<span data-ttu-id="7765d-111">如果您在管理用户帐户和组通过 Windows 服务器活动目录 (AD)，将相应的用户添加到使用标准 Windows 服务器 AD 用户和组管理过程的适当访问权限组和等待同步与您Office 365 的订阅。</span><span class="sxs-lookup"><span data-stu-id="7765d-111">If you are managing user accounts and groups through Windows Server Active Directory (AD), add the appropriate users to the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="7765d-112">如果您在管理用户帐户和组通过 Office 365，可以使用 Office 管理中心或 Microsoft PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7765d-112">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or Microsoft PowerShell:</span></span>
  
- <span data-ttu-id="7765d-113">对于 Office 管理中心，使用已分配的用户的帐户管理员或公司管理员角色的用户帐户登录和使用组将相应的用户添加到适当的访问权限的组。</span><span class="sxs-lookup"><span data-stu-id="7765d-113">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate users to the appropriate access groups.</span></span>
    
- <span data-ttu-id="7765d-p101">对于 PowerShell，第一个[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。若要将用户帐户添加到访问组的用户主体名称 (UPN)，使用下面的 PowerShell 命令块：</span><span class="sxs-lookup"><span data-stu-id="7765d-p101">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218). To add a user account to an access group with its user principal name (UPN), use the following PowerShell command block:</span></span>
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> <span data-ttu-id="7765d-116">对于文本文件，其中包含所有 PowerShell 命令和 Excel 配置 PowerShell 命令将生成的工作表中根据您的组和用户帐户名称、 下载[独立 SharePoint 在线团队站点部署工具包](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907)。</span><span class="sxs-lookup"><span data-stu-id="7765d-116">For a text file that contains all the PowerShell commands and an Excel configuration worksheet that generates PowerShell commands based on your group and user account names, download the [Isolated SharePoint Online Team Site Deployment Kit](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907).</span></span> 

<span data-ttu-id="7765d-117">若要将用户帐户添加到其显示名称的访问组，使用以下 PowerShell 命令块：</span><span class="sxs-lookup"><span data-stu-id="7765d-117">To add a user account to an access group with its display name, use the following PowerShell command block:</span></span>

```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="add-a-new-group"></a><span data-ttu-id="7765d-118">添加新组</span><span class="sxs-lookup"><span data-stu-id="7765d-118">Add a new group</span></span>

<span data-ttu-id="7765d-119">若要向整个组访问权限，您必须决定站点组的所有成员的参与程度：</span><span class="sxs-lookup"><span data-stu-id="7765d-119">To add access to an entire group, you must decide the level of participation of all the members of the group in the site:</span></span>
  
- <span data-ttu-id="7765d-120">管理： 将组添加到该站点管理员访问组</span><span class="sxs-lookup"><span data-stu-id="7765d-120">Administration: Add the group to the site admins access group</span></span>
    
- <span data-ttu-id="7765d-121">协作活动： 向网站中添加组成员访问组</span><span class="sxs-lookup"><span data-stu-id="7765d-121">Active collaboration: Add the group to the site members access group</span></span>
    
- <span data-ttu-id="7765d-122">查看： 将组添加到该网站浏览者访问组</span><span class="sxs-lookup"><span data-stu-id="7765d-122">Viewing: Add the group to the site viewers access group</span></span>
    
<span data-ttu-id="7765d-123">如果您在管理用户帐户和组通过 Windows 服务器 AD，将适当的组添加到适当的组使用正常的 Windows 服务器 AD 用户和组的管理过程，并等待与 Office 365 订阅进行同步处理。</span><span class="sxs-lookup"><span data-stu-id="7765d-123">If you are managing user accounts and groups through Windows Server AD, add the appropriate groups to the appropriate groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="7765d-124">如果您在管理用户帐户和组通过 Office 365，您可以使用 Office 管理中心或 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7765d-124">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell:</span></span>
  
- <span data-ttu-id="7765d-125">办公室管理的中心，使用已分配的用户的帐户管理员或公司管理员角色的用户帐户登录和使用组来向适当的访问权限的组添加到相应的组。</span><span class="sxs-lookup"><span data-stu-id="7765d-125">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate groups to the appropriate access groups.</span></span>
    
- <span data-ttu-id="7765d-p102">对于 PowerShell，第一个[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。然后，使用下列的 PowerShell 命令：</span><span class="sxs-lookup"><span data-stu-id="7765d-p102">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218). Then, use the following PowerShell commands:</span></span>
 
```
$newGroupName="<display name of the new group to add>"
$siteGrpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $newGroupName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $siteGrpName }).ObjectID
```

## <a name="remove-a-user"></a><span data-ttu-id="7765d-128">删除用户</span><span class="sxs-lookup"><span data-stu-id="7765d-128">Remove a user</span></span>

<span data-ttu-id="7765d-129">当某人的访问必须从站点中删除时，它们从组中删除访问它们所当前基于他们参与该网站的成员：</span><span class="sxs-lookup"><span data-stu-id="7765d-129">When someone's access must be removed from the site, you remove them from the access group for which they are currently a member based on their participation in the site:</span></span>
  
- <span data-ttu-id="7765d-130">管理： 删除管理员访问权限的网站用户组中的用户帐户</span><span class="sxs-lookup"><span data-stu-id="7765d-130">Administration: Remove the user account from the site admins access group</span></span>
    
- <span data-ttu-id="7765d-131">活动的协作： 删除站点成员访问组中的用户帐户</span><span class="sxs-lookup"><span data-stu-id="7765d-131">Active collaboration: Remove the user account from the site members access group</span></span>
    
- <span data-ttu-id="7765d-132">查看： 删除站点查看器访问组中的用户帐户</span><span class="sxs-lookup"><span data-stu-id="7765d-132">Viewing: Remove the user account from the site viewers access group</span></span>
    
<span data-ttu-id="7765d-133">如果您在管理用户帐户和组通过 Windows 服务器 AD，从使用正常的 Windows 服务器 AD 用户和组管理过程的适当访问权限组中删除相应的用户，并等待与 Office 365 的同步预订。</span><span class="sxs-lookup"><span data-stu-id="7765d-133">If you are managing user accounts and groups through Windows Server AD, remove the appropriate users from the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="7765d-134">如果您在管理用户帐户和组通过 Office 365，您可以使用 Office 管理中心或 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7765d-134">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell:</span></span>
  
- <span data-ttu-id="7765d-135">对于 Office 管理中心，使用已分配的用户的帐户管理员或公司管理员角色的用户帐户登录和使用适当的访问权限的组中删除相应的用户组。</span><span class="sxs-lookup"><span data-stu-id="7765d-135">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to remove the appropriate users from the appropriate access groups.</span></span>
    
- <span data-ttu-id="7765d-p103">对于 PowerShell，第一个[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。若要通过其 UPN 访问组中删除用户帐户，请使用下面的 PowerShell 命令块：</span><span class="sxs-lookup"><span data-stu-id="7765d-p103">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218). To remove a user account from an access group with its UPN, use the following PowerShell command block:</span></span>
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

<span data-ttu-id="7765d-138">要从其显示名称的访问组中删除用户帐户，使用下面的 PowerShell 命令块：</span><span class="sxs-lookup"><span data-stu-id="7765d-138">To remove a user account from an access group with its display name, use the following PowerShell command block:</span></span>
    
```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="remove-a-group"></a><span data-ttu-id="7765d-139">删除组</span><span class="sxs-lookup"><span data-stu-id="7765d-139">Remove a group</span></span>

<span data-ttu-id="7765d-140">若要删除整个组的访问权限，请从它们所当前成员根据他们参与该网站的访问组删除组：</span><span class="sxs-lookup"><span data-stu-id="7765d-140">To remove access for an entire group, you remove the group from the access group for which they are currently a member based on their participation in the site:</span></span>
  
- <span data-ttu-id="7765d-141">管理： 删除站点管理员访问组中的组</span><span class="sxs-lookup"><span data-stu-id="7765d-141">Administration: Remove the group from the site admins access group</span></span>
    
- <span data-ttu-id="7765d-142">活动的协作： 删除组成员访问权限的网站用户组</span><span class="sxs-lookup"><span data-stu-id="7765d-142">Active collaboration: Remove the group from the site members access group</span></span>
    
- <span data-ttu-id="7765d-143">查看： 删除站点查看器访问组中的组</span><span class="sxs-lookup"><span data-stu-id="7765d-143">Viewing: Remove the group from the site viewers access group</span></span>
    
<span data-ttu-id="7765d-144">如果您在管理用户帐户和组通过 Windows 服务器的 Active Directory，从使用普通 Windows 服务器 AD 用户和组管理过程的适当访问权限组中删除相应的组并等待同步与您Office 365 的订阅。</span><span class="sxs-lookup"><span data-stu-id="7765d-144">If you are managing user accounts and groups through Windows Server Active Directory, remove the appropriate groups from the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="7765d-145">如果您在管理用户帐户和组通过 Office 365，您可以使用 Office 管理中心或 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7765d-145">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell:</span></span>
  
- <span data-ttu-id="7765d-146">办公室管理的中心，使用已分配的用户的帐户管理员或公司管理员角色的用户帐户登录，然后使用组从适当的访问权限组中删除相应的组。</span><span class="sxs-lookup"><span data-stu-id="7765d-146">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to remove the appropriate groups from the appropriate access groups.</span></span>
    
- <span data-ttu-id="7765d-147">对于 PowerShell，第一个[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="7765d-147">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>    
<span data-ttu-id="7765d-148">若要从使用显示名称访问组中删除一个组，使用下面的 PowerShell 命令块：</span><span class="sxs-lookup"><span data-stu-id="7765d-148">To remove a group from an access group using their display names, use the following PowerShell command block:</span></span>
    
```
$groupMemberName="<display name of the group to remove>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="create-a-documents-subfolder-with-custom-permissions"></a><span data-ttu-id="7765d-149">使用自定义权限创建一个文档的子文件夹</span><span class="sxs-lookup"><span data-stu-id="7765d-149">Create a documents subfolder with custom permissions</span></span>

<span data-ttu-id="7765d-p104">在某些情况下，子集的独立站点内工作的人需要更多私人场所进行协作。SharePoint Online 网站，可以在网站的文档文件夹中创建子文件夹并指定自定义权限。那些没有权限看不到子文件夹。</span><span class="sxs-lookup"><span data-stu-id="7765d-p104">In some cases, a subset of the people working within the isolated site need a more private place to collaborate. For SharePoint Online sites, you can create a subfolder in the Documents folder of the site and assign custom permissions. Those without permissions will not see the subfolder.</span></span>
  
<span data-ttu-id="7765d-153">若要使用自定义权限创建一个文档的子文件夹，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="7765d-153">To create a documents subfolder with custom permissions, do the following:</span></span>
  
1. <span data-ttu-id="7765d-p105">是网站的管理员访问权限组成员的帐户登录到 Office 365。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="7765d-p105">Sign in to Office 365 with an account that is a member of the admins access group for the site. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="7765d-156">转到独立的工作组站点并单击**文档**。</span><span class="sxs-lookup"><span data-stu-id="7765d-156">Go to the isolated team site and click **Documents**.</span></span>
    
3. <span data-ttu-id="7765d-157">浏览到该文件夹的文档文件夹中将包含具有自定义权限的子文件夹，创建该文件夹，然后再打开它。</span><span class="sxs-lookup"><span data-stu-id="7765d-157">Browse to the folder in the documents folder that will contain the subfolder with custom permissions, create the folder, and then open it.</span></span>
    
4. <span data-ttu-id="7765d-158">单击"共享"。</span><span class="sxs-lookup"><span data-stu-id="7765d-158">Click **Share**.</span></span>
    
5. <span data-ttu-id="7765d-159">单击**与共享 > 高级**。</span><span class="sxs-lookup"><span data-stu-id="7765d-159">Click **Shared with > Advanced**.</span></span>
    
6. <span data-ttu-id="7765d-160">单击**停止继承权限**，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="7765d-160">Click **Stop inheriting permissions**, and then click **OK**.</span></span>
    
7. <span data-ttu-id="7765d-161">单击"共享"。</span><span class="sxs-lookup"><span data-stu-id="7765d-161">Click **Share**.</span></span>
    
8. <span data-ttu-id="7765d-162">单击**与共享 > 高级**。</span><span class="sxs-lookup"><span data-stu-id="7765d-162">Click **Shared with > Advanced**.</span></span>
    
9. <span data-ttu-id="7765d-163">单击**授予权限 > 与共享 > 高级**。</span><span class="sxs-lookup"><span data-stu-id="7765d-163">Click **Grant Permissions > Shared with > Advanced**.</span></span>
    
10. <span data-ttu-id="7765d-164">在权限页上单击**\<网站名称 > 列表中的成员**。</span><span class="sxs-lookup"><span data-stu-id="7765d-164">On the permissions page, click **\<site name> Members in the list**.</span></span>
    
11. <span data-ttu-id="7765d-165">在**\<网站名称 > 成员**页上，选择成员访问权限的网站用户组旁边的复选标记，单击**操作**，单击**用户从组中删除**，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="7765d-165">On the **\<site name> Members** page, select the checkmark next to the site members access group, click **Actions**, click **Remove users from group**, and then click **OK**.</span></span>
    
12. <span data-ttu-id="7765d-166">若要将特定成员添加到此子文件夹，请单击**新建 > 添加用户**。</span><span class="sxs-lookup"><span data-stu-id="7765d-166">To add specific members to this subfolder, click **New > Add users**.</span></span>
    
13. <span data-ttu-id="7765d-167">在**共享**对话框中，键入可以进行协作的子文件夹中的文件，然后单击**共享**的用户帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="7765d-167">In the **Share** dialog box, type the names of the user accounts that can collaborate on files in the subfolder, and then click **Share**.</span></span>
    
14. <span data-ttu-id="7765d-168">刷新网页以查看新的结果。</span><span class="sxs-lookup"><span data-stu-id="7765d-168">Refresh the web page to see the new results.</span></span>
    
15. <span data-ttu-id="7765d-169">在左侧导航区域中的**组**中，单击**\<网站名称 > 访问者**组和使用步骤 11-14 （根据需要） 可以查看子文件夹中的文件的用户帐户的设置。</span><span class="sxs-lookup"><span data-stu-id="7765d-169">Under **Groups** in the left navigation, click the **\<site name> Visitors** group and use steps 11-14 to specify the set of user accounts that can view the files in the subfolder (as needed).</span></span>
    
16. <span data-ttu-id="7765d-170">在左侧导航区域中的**组**，单击**\<网站名称 > 所有者**组和使用步骤 11-14 （根据需要），可以管理的子文件夹中的权限的用户帐户的设置。</span><span class="sxs-lookup"><span data-stu-id="7765d-170">Under **Groups** in the left navigation, click the **\<site name> Owners** group and use steps 11-14 to specify the set of user accounts that can administer the permissions in the subfolder (as needed).</span></span>
    
17. <span data-ttu-id="7765d-171">关闭您的浏览器中的**用户和用户组**选项卡。</span><span class="sxs-lookup"><span data-stu-id="7765d-171">Close the **People and Groups** tab in your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="7765d-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7765d-172">See Also</span></span>

[<span data-ttu-id="7765d-173">SharePoint Online 的独立的团队站点</span><span class="sxs-lookup"><span data-stu-id="7765d-173">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="7765d-174">设计独立的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="7765d-174">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="7765d-175">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="7765d-175">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="7765d-176">部署独立的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="7765d-176">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)



