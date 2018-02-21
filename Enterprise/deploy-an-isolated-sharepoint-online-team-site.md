---
title: "部署独立的在线 SharePoint 工作组网站"
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
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: "摘要： 部署新独立的 SharePoint Online 工作组网站提供这些分步说明。"
ms.openlocfilehash: 297681b688b43eb02ee4f99f983a0f796312e599
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2018
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="c4243-103">部署独立的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="c4243-103">Deploy an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="c4243-104">**摘要：**部署新独立的 SharePoint Online 工作组网站提供这些分步说明。</span><span class="sxs-lookup"><span data-stu-id="c4243-104">**Summary:** Deploy a new isolated SharePoint Online team site with these step-by-step instructions.</span></span>
  
<span data-ttu-id="c4243-p101">本文是用于创建和配置 Microsoft Office 365 中的独立在线 SharePoint 工作组网站逐步部署指南。这些步骤假设使用三个默认 SharePoint 用户组和相应的权限级别，与每个级别的访问权限的单个基于 Azure 活动目录 AD 的访问组。</span><span class="sxs-lookup"><span data-stu-id="c4243-p101">This article is a step-by-step deployment guide for creating and configuring an isolated SharePoint Online team site in Microsoft Office 365. These steps assume the use of the three default SharePoint groups and corresponding permission levels, with a single Azure Active Directory (AD)-based access group for each level of access.</span></span>
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a><span data-ttu-id="c4243-107">阶段 1： 创建并填充团队站点访问组</span><span class="sxs-lookup"><span data-stu-id="c4243-107">Phase 1: Create and populate the team site access groups</span></span>

<span data-ttu-id="c4243-108">在此阶段中，您创建的三个默认 SharePoint 组三个 Azure 基于 AD 的访问组和其中填充适当的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c4243-108">In this phase, you create the three Azure AD-based access groups for the three default SharePoint groups and populate them with the appropriate user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c4243-p102">以下步骤假定所有必要的用户帐户已经存在并分配相应的许可证。如果不是，请将它们添加和分配许可证之前，以步骤 1。</span><span class="sxs-lookup"><span data-stu-id="c4243-p102">The following steps assume that all necessary user accounts already exist and are assigned the appropriate licenses. If not, please add them and assign licenses before proceeding to step 1.</span></span> 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a><span data-ttu-id="c4243-111">步骤 1： 列出网站的 SharePoint Online 管理员</span><span class="sxs-lookup"><span data-stu-id="c4243-111">Step 1: List the SharePoint Online admins for the site</span></span>

<span data-ttu-id="c4243-112">确定组的用户帐户对应于独立的工作组网站的 SharePoint Online 管理员。</span><span class="sxs-lookup"><span data-stu-id="c4243-112">Determine the set of user accounts corresponding to the SharePoint Online admins for the isolated team site.</span></span>
  
<span data-ttu-id="c4243-113">如果您正在管理用户帐户和组通过 Office 365 并且想要使用 Windows PowerShell，使列表中的用户主体名称 (Upn) (UPN 的示例： belindan@contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="c4243-113">If you are managing user accounts and groups through Office 365 and want to use Windows PowerShell, make a list of their user principal names (UPNs) (example UPN: belindan@contoso.com).</span></span>
  
### <a name="step-2-list-the-members-for-the-site"></a><span data-ttu-id="c4243-114">步骤 2： 列出站点的成员</span><span class="sxs-lookup"><span data-stu-id="c4243-114">Step 2: List the members for the site</span></span>

<span data-ttu-id="c4243-115">确定的一套独立的工作组站点，将协作资源存储在该网站上的那些成员所对应的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c4243-115">Determine the set of user accounts corresponding to the members for the isolated team site, those who will be collaborating on resources stored within the site.</span></span>
  
<span data-ttu-id="c4243-p103">如果您的用户帐户和组通过 Office 365 管理并且想要使用 PowerShell，请其 Upn 的列表。如果有大量的网站成员，您可以 Upn 的列表存储在文本文件中并将其添加所有使用单个 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="c4243-p103">If you are managing user accounts and groups through Office 365 and want to use PowerShell, make a list of their UPNs. If there are a lot of site members, you can store the list of UPNs in a text file and add them all with a single PowerShell command.</span></span>
  
### <a name="step-3-list-the-viewers-for-the-site"></a><span data-ttu-id="c4243-118">步骤 3： 列出了网站的观众</span><span class="sxs-lookup"><span data-stu-id="c4243-118">Step 3: List the viewers for the site</span></span>

<span data-ttu-id="c4243-119">确定的一套独立的工作组站点的那些可以查看网站中存储的资源但没有对其进行修改或直接对其内容进行协作的查看器所对应的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c4243-119">Determine the set of user accounts corresponding to the viewers of the isolated team site, those who can view the resources stored in the site but not modify them or directly collaborate on their contents.</span></span>
  
<span data-ttu-id="c4243-p104">如果您的用户帐户和组通过 Office 365 管理并且想要使用 PowerShell，请其 Upn 的列表。如果有大量的网站成员，您可以 Upn 的列表存储在文本文件中并将其添加所有使用单个 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="c4243-p104">If you are managing user accounts and groups through Office 365 and want to use PowerShell, make a list of their UPNs. If there are a lot of site members, you can store the list of UPNs in a text file and add them all with a single PowerShell command.</span></span>
  
<span data-ttu-id="c4243-122">查看该站点可能包括行政管理、 法律顾问或执行部门间利益干系人。</span><span class="sxs-lookup"><span data-stu-id="c4243-122">Viewers for the site might include executive management, legal counsel, or inter-departmental stakeholders.</span></span>
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a><span data-ttu-id="c4243-123">步骤 4： 创建在 Azure AD 站点的三个访问组</span><span class="sxs-lookup"><span data-stu-id="c4243-123">Step 4: Create the three access groups for the site in Azure AD</span></span>

<span data-ttu-id="c4243-124">您需要在 Azure AD 中创建以下访问组：</span><span class="sxs-lookup"><span data-stu-id="c4243-124">You need to create the following access groups in Azure AD:</span></span>
  
- <span data-ttu-id="c4243-125">站点管理员 （这将包含从第 1 步的列表）</span><span class="sxs-lookup"><span data-stu-id="c4243-125">Site admins (which will contain the list from step 1)</span></span>
    
- <span data-ttu-id="c4243-126">网站成员 （它将包含在步骤 2 中的列表）</span><span class="sxs-lookup"><span data-stu-id="c4243-126">Site members (which will contain the list from step 2)</span></span>
    
- <span data-ttu-id="c4243-127">站点访问者 （其中将包含从第 3 步的列表）</span><span class="sxs-lookup"><span data-stu-id="c4243-127">Site viewers (which will contain the list from step 3)</span></span>
    
1. <span data-ttu-id="c4243-128">在浏览器中，转到 Azure 门户网站位于[https://portal.azure.com](https://portal.azure.com)并使用已分配的用户管理管理员或公司管理员角色帐户的凭据登录。</span><span class="sxs-lookup"><span data-stu-id="c4243-128">In your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com) and sign in with the credentials of an account that has been assigned with User Management Admin or Company Administrator role.</span></span>
    
2. <span data-ttu-id="c4243-129">在 Azure 门户中，单击“Azure Active Directory”>“用户和组”>“所有组”。</span><span class="sxs-lookup"><span data-stu-id="c4243-129">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="c4243-130">在“所有组”边栏选项卡上，单击“+ 新建组”。</span><span class="sxs-lookup"><span data-stu-id="c4243-130">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="c4243-131">在“组”边栏选项卡上：</span><span class="sxs-lookup"><span data-stu-id="c4243-131">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="c4243-132">在**名称**中键入组的名称。</span><span class="sxs-lookup"><span data-stu-id="c4243-132">Type the group name in **Name**.</span></span>
    
  - <span data-ttu-id="c4243-133">在“成员身份”中选择“已分配”。</span><span class="sxs-lookup"><span data-stu-id="c4243-133">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="c4243-134">对“启用 Office 功能”单击“是”。</span><span class="sxs-lookup"><span data-stu-id="c4243-134">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="c4243-135">单击“创建”，然后关闭“组”边栏选项卡。</span><span class="sxs-lookup"><span data-stu-id="c4243-135">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="c4243-136">对于其他的组，请重复步骤 3-5。</span><span class="sxs-lookup"><span data-stu-id="c4243-136">Repeat steps 3-5 for your additional groups.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c4243-p105">您需要使用 Azure 门户创建组，以使它们具有 Office 功能已启用。如果以后为高度机密站点使用 Azure 信息保护 (AIP) 标签对文件进行加密并将权限分配给特定的组配置 SharePoint Online 的独立的网站，允许的组必须创建的 Office 功能已启用。它创建后，不能更改 Office 功能设置 Azure AD 组。</span><span class="sxs-lookup"><span data-stu-id="c4243-p105">You need to use the Azure portal to create the groups so that they have Office features enabled. If a SharePoint Online isolated site is later configured as a Highly Confidential site with an Azure Information Protection (AIP) label to encrypt files and assign permission to specific groups, the permitted groups must have been created with Office features enabled. You cannot change the Office features setting of an Azure AD group after it has been created.</span></span> 
  
<span data-ttu-id="c4243-140">这里有三个站点访问组与您生成的配置。</span><span class="sxs-lookup"><span data-stu-id="c4243-140">Here is your resulting configuration with the three site access groups.</span></span>
  
![三个适用于部署独立 SharePoint Online 网站的访问组。](images/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a><span data-ttu-id="c4243-p106">第 5 步。将用户帐户添加到访问组</span><span class="sxs-lookup"><span data-stu-id="c4243-p106">Step 5. Add the user accounts to the access groups</span></span>

<span data-ttu-id="c4243-144">在此步骤中，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="c4243-144">In this step, do the following:</span></span>
  
1. <span data-ttu-id="c4243-145">向站点管理员访问权限组第 1 步中添加的用户的列表</span><span class="sxs-lookup"><span data-stu-id="c4243-145">Add the list of users from step 1 to the site admins access group</span></span>
    
2. <span data-ttu-id="c4243-146">在步骤 2 中的用户列表添加成员访问权限的网站用户组</span><span class="sxs-lookup"><span data-stu-id="c4243-146">Add the list of users from step 2 to the site members access group</span></span>
    
3. <span data-ttu-id="c4243-147">到网站查看器访问组从第 3 步中添加的用户的列表</span><span class="sxs-lookup"><span data-stu-id="c4243-147">Add the list of users from step 3 to the site viewers access group</span></span>
    
<span data-ttu-id="c4243-148">如果您在管理用户帐户和组通过 Windows 服务器 AD，将用户添加到适当的访问权限组使用正常的 Windows 服务器 AD 用户和组的管理过程，并等待与 Office 365 订阅进行同步处理。</span><span class="sxs-lookup"><span data-stu-id="c4243-148">If you are managing user accounts and groups through Windows Server AD, add users to the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="c4243-p107">如果您在管理用户帐户和组通过 Office 365，您可以使用 Office 管理中心或 PowerShell。如果您有访问组中的任何重复的组名，您应使用办公室管理中心。</span><span class="sxs-lookup"><span data-stu-id="c4243-p107">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell. If you have duplicate group names for any of the access groups, you should use the Office Admin center.</span></span>
  
<span data-ttu-id="c4243-151">对于 Office 管理中心，使用已分配的用户的帐户管理员或公司管理员角色的用户帐户登录和使用组添加合适的用户帐户和组添加到适当的访问权限组。</span><span class="sxs-lookup"><span data-stu-id="c4243-151">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate user accounts and groups to the appropriate access groups.</span></span>
  
<span data-ttu-id="c4243-152">对于 PowerShell，第一个[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="c4243-152">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="c4243-153">接下来，使用下面的命令块将单个用户帐户添加到访问组：</span><span class="sxs-lookup"><span data-stu-id="c4243-153">Next, use the following command block to add an individual user account to an access group:</span></span>
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> <span data-ttu-id="c4243-154">对于文本文件，其中包含所有 PowerShell 命令和 Excel 配置 PowerShell 命令将生成的工作表中根据您的组和用户帐户名称、 下载[独立 SharePoint 在线团队站点部署工具包](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907)。</span><span class="sxs-lookup"><span data-stu-id="c4243-154">For a text file that contains all the PowerShell commands and an Excel configuration worksheet that generates PowerShell commands based on your group and user account names, download the [Isolated SharePoint Online Team Site Deployment Kit](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907).</span></span> 
  
<span data-ttu-id="c4243-155">如果在文本文件中存储访问组中的任何用户帐户的 Upn，可以使用下面的 PowerShell 命令块要一次添加它们：</span><span class="sxs-lookup"><span data-stu-id="c4243-155">If you stored the UPNs of user accounts for any of the access groups in a text file, you can use the following PowerShell command block to add them all at one time:</span></span>
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

<span data-ttu-id="c4243-156">对于 PowerShell，使用下面的命令块单独的组添加到访问组：</span><span class="sxs-lookup"><span data-stu-id="c4243-156">For PowerShell, use the following command block to add an individual group to an access group:</span></span>
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

<span data-ttu-id="c4243-157">结果应如下：</span><span class="sxs-lookup"><span data-stu-id="c4243-157">The results should be the following:</span></span>
  
- <span data-ttu-id="c4243-158">站点管理员 Azure AD 组包含站点管理员用户帐户或组</span><span class="sxs-lookup"><span data-stu-id="c4243-158">The site admins Azure AD group contains the site admin user accounts or groups</span></span>
    
- <span data-ttu-id="c4243-159">网站成员 Azure AD 组包含站点成员用户帐户或组</span><span class="sxs-lookup"><span data-stu-id="c4243-159">The site members Azure AD group contains the site member user accounts or groups</span></span>
    
- <span data-ttu-id="c4243-160">网站查看 Azure AD 组中包含的用户帐户或组，可以只查看网站内容</span><span class="sxs-lookup"><span data-stu-id="c4243-160">The site viewers Azure AD group contains the user accounts or groups that can only view the site contents</span></span>
    
<span data-ttu-id="c4243-161">验证列表中的每个访问组与 Office 管理中心或以下 PowerShell 命令块组成员：</span><span class="sxs-lookup"><span data-stu-id="c4243-161">Validate the list of group members for each access group with the Office Admin center or with the following PowerShell command block:</span></span>
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

<span data-ttu-id="c4243-162">这里是您生成的配置与使用用户帐户或组填充三个站点访问组。</span><span class="sxs-lookup"><span data-stu-id="c4243-162">Here is your resulting configuration with the three site access groups populated with user accounts or groups.</span></span>
  
![三个使用用户帐户填充的访问组。](images/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a><span data-ttu-id="c4243-164">第 2 阶段： 创建和配置独立的工作组站点</span><span class="sxs-lookup"><span data-stu-id="c4243-164">Phase 2: Create and configure the isolated team site</span></span>

<span data-ttu-id="c4243-165">在此阶段中，您可以创建独立的 SharePoint Online 网站并配置默认 SharePoint Online 权限级别来使用新的 Azure 基于 AD 的访问组的权限。</span><span class="sxs-lookup"><span data-stu-id="c4243-165">In this phase, you create the isolated SharePoint Online site and configure the permissions for the default SharePoint Online permission levels to use your new Azure AD-based access groups.</span></span>
  
<span data-ttu-id="c4243-166">首先，通过这些步骤创建 SharePoint Online 的工作组网站。</span><span class="sxs-lookup"><span data-stu-id="c4243-166">First, create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="c4243-p108">登录到 Office 365 门户网站也将用来管理 SharePoint Online 工作组网站 （SharePoint Online 管理员） 的帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="c4243-p108">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c4243-169">在磁贴列表中，单击“SharePoint”。</span><span class="sxs-lookup"><span data-stu-id="c4243-169">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c4243-170">在您的浏览器的新**SharePoint**选项卡，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="c4243-170">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c4243-171">在“创建网站”页中，单击“团队网站”。</span><span class="sxs-lookup"><span data-stu-id="c4243-171">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c4243-172">在**站点名称**中，键入工作组网站的名称。</span><span class="sxs-lookup"><span data-stu-id="c4243-172">In **Site name**, type a name for the team site.</span></span> 
    
6. <span data-ttu-id="c4243-173">在**团队站点描述中，**键入站点的用途的可选说明。</span><span class="sxs-lookup"><span data-stu-id="c4243-173">In **Team site description,** type an optional description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="c4243-174">在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="c4243-174">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c4243-175">在“希望添加哪些人员?”窗格中，单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="c4243-175">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="c4243-176">接下来，从新的 SharePoint Online 团队站点配置权限。</span><span class="sxs-lookup"><span data-stu-id="c4243-176">Next, from the new SharePoint Online team site, configure permissions.</span></span>
  
1. <span data-ttu-id="c4243-177">在工具栏上，单击设置图标，然后单击**网站权限**。</span><span class="sxs-lookup"><span data-stu-id="c4243-177">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
2. <span data-ttu-id="c4243-178">在“网站权限”窗格中，单击“高级权限设置”。</span><span class="sxs-lookup"><span data-stu-id="c4243-178">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
3. <span data-ttu-id="c4243-179">在浏览器的新“权限”标签页中，单击“访问请求设置”。</span><span class="sxs-lookup"><span data-stu-id="c4243-179">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
4. <span data-ttu-id="c4243-180">在**访问请求设置**对话框中，清除**允许成员共享的网站和个别文件和文件夹**，并**允许访问请求**（以使所有三个复选框都被清除），然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="c4243-180">In the **Access Requests Settings** dialog box, clear **Allow member to share the site and individual files and folders** and **Allow access requests** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
5. <span data-ttu-id="c4243-181">在浏览器**权限**选项卡上，单击**\<网站名称 > 成员**列表中。</span><span class="sxs-lookup"><span data-stu-id="c4243-181">On the **Permissions** tab of your browser, click **\<site name> Members** in the list.</span></span>
    
6. <span data-ttu-id="c4243-182">在**用户和用户组**中，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="c4243-182">In **People and Groups**, click **New**.</span></span>
    
7. <span data-ttu-id="c4243-183">在**共享**对话框中，键入成员访问权限的网站用户组的名称，选择它，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="c4243-183">In the **Share** dialog box, type the name of the site members access group, select it, and then click **Share**.</span></span>
    
8. <span data-ttu-id="c4243-184">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="c4243-184">Click the back button on your browser.</span></span>
    
9. <span data-ttu-id="c4243-185">单击**\<网站名称 > 所有者**在列表中。</span><span class="sxs-lookup"><span data-stu-id="c4243-185">Click **\<site name> Owners** in the list.</span></span>
    
10. <span data-ttu-id="c4243-186">在**用户和用户组**中，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="c4243-186">In **People and Groups**, click **New**.</span></span>
    
11. <span data-ttu-id="c4243-187">在**共享**对话框中，键入管理员访问权限的网站用户组的名称，选择它，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="c4243-187">In the **Share** dialog box, type the name of the site admins access group, select it, and then click **Share**.</span></span>
    
12. <span data-ttu-id="c4243-188">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="c4243-188">Click the back button on your browser.</span></span>
    
13. <span data-ttu-id="c4243-189">单击**\<网站名称 > 访问者**在列表中。</span><span class="sxs-lookup"><span data-stu-id="c4243-189">Click **\<site name> Visitors** in the list.</span></span>
    
14. <span data-ttu-id="c4243-190">在**用户和用户组**中，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="c4243-190">In **People and Groups**, click **New**.</span></span>
    
15. <span data-ttu-id="c4243-191">在**共享**对话框中，键入站点查看器访问组的名称，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="c4243-191">In the **Share** dialog box, type the name of the site viewers access group, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="c4243-192">关闭浏览器的“权限”选项卡。</span><span class="sxs-lookup"><span data-stu-id="c4243-192">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="c4243-193">这些权限设置的结果是：</span><span class="sxs-lookup"><span data-stu-id="c4243-193">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="c4243-194">**\<网站名称 > 所有者**SharePoint 组包含所有成员中具有**完全控制**权限级别的网站管理员访问组。</span><span class="sxs-lookup"><span data-stu-id="c4243-194">The **\<site name> Owners** SharePoint group contains the site admins access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="c4243-195">**\<网站名称 > 成员**SharePoint 组包含在所有的成员拥有**编辑**权限级别的网站成员访问组。</span><span class="sxs-lookup"><span data-stu-id="c4243-195">The **\<site name> Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="c4243-196">**\<网站名称 > 访问者**SharePoint 组包含所有成员中具有**读取**权限级别的网站查看器访问组。</span><span class="sxs-lookup"><span data-stu-id="c4243-196">The **\<site name> Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="c4243-197">邀请其他成员的成员或非成员请求访问的功能被禁用。</span><span class="sxs-lookup"><span data-stu-id="c4243-197">The ability for members to invite other members or for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="c4243-198">这里是您与网站配置为使用与用户帐户填充的三个访问组或 Azure AD 组三个 SharePoint 组生成的配置。</span><span class="sxs-lookup"><span data-stu-id="c4243-198">Here is your resulting configuration with the three SharePoint groups for the site configured to use the three access groups, which are populated with user accounts or Azure AD groups.</span></span>
  
![包含访问组和用户帐户的独立 SharePoint Online 网站的最终配置。](images/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
<span data-ttu-id="c4243-200">您和网站，通过一个访问组中的组成员资格的成员可以立即协同使用网站的资源。</span><span class="sxs-lookup"><span data-stu-id="c4243-200">You and the members of the site, through group membership in one of the access groups, can now collaborate using the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="c4243-201">后续步骤</span><span class="sxs-lookup"><span data-stu-id="c4243-201">Next step</span></span>

<span data-ttu-id="c4243-202">当您需要更改网站访问组成员身份或创建具有自定义权限的文档文件夹时，请参阅[管理独立的在线 SharePoint 工作组网站](manage-an-isolated-sharepoint-online-team-site.md)。</span><span class="sxs-lookup"><span data-stu-id="c4243-202">When you need to change site access group membership or create a document folder with custom permissions, see [Manage an isolated SharePoint Online team site](manage-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c4243-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4243-203">See Also</span></span>

[<span data-ttu-id="c4243-204">SharePoint Online 的独立的团队站点</span><span class="sxs-lookup"><span data-stu-id="c4243-204">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="c4243-205">设计独立的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="c4243-205">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="c4243-206">管理独立的在线 SharePoint 工作组网站</span><span class="sxs-lookup"><span data-stu-id="c4243-206">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="c4243-207">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="c4243-207">Security solutions</span></span>](security-solutions.md)



