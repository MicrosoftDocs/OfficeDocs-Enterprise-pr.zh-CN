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
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="1be36-103">部署独立 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="1be36-103">Deploy an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="1be36-104">**摘要：** 部署新独立的 SharePoint Online 团队网站与这些分步说明。</span><span class="sxs-lookup"><span data-stu-id="1be36-104">**Summary:** Deploy a new isolated SharePoint Online team site with these step-by-step instructions.</span></span>
  
<span data-ttu-id="1be36-p101">本文是针对创建和配置 Microsoft Office 365 中的一个独立的 SharePoint Online 团队网站的分步部署指南。这些步骤假定使用三个默认 SharePoint 组和相应的权限级别，与单个基于 Azure Active Directory AD 的访问组每个级别的访问。</span><span class="sxs-lookup"><span data-stu-id="1be36-p101">This article is a step-by-step deployment guide for creating and configuring an isolated SharePoint Online team site in Microsoft Office 365. These steps assume the use of the three default SharePoint groups and corresponding permission levels, with a single Azure Active Directory (AD)-based access group for each level of access.</span></span>
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a><span data-ttu-id="1be36-107">阶段 1： 创建和填充工作组网站的访问组</span><span class="sxs-lookup"><span data-stu-id="1be36-107">Phase 1: Create and populate the team site access groups</span></span>

<span data-ttu-id="1be36-108">在此阶段中，可以创建三个默认 SharePoint 组的三个 Azure 基于 AD 的访问组和填充它们与相应的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="1be36-108">In this phase, you create the three Azure AD-based access groups for the three default SharePoint groups and populate them with the appropriate user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1be36-p102">下面的步骤假定所有必要的用户帐户已存在且已分配相应的许可证。如果没有，请将其添加并分配许可证，然后再继续步骤 1。</span><span class="sxs-lookup"><span data-stu-id="1be36-p102">The following steps assume that all necessary user accounts already exist and are assigned the appropriate licenses. If not, please add them and assign licenses before proceeding to step 1.</span></span> 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a><span data-ttu-id="1be36-111">步骤 1： 列表的网站 SharePoint Online 管理员</span><span class="sxs-lookup"><span data-stu-id="1be36-111">Step 1: List the SharePoint Online admins for the site</span></span>

<span data-ttu-id="1be36-112">确定一组的用户帐户在对应于独立的工作组网站的 SharePoint Online 管理员。</span><span class="sxs-lookup"><span data-stu-id="1be36-112">Determine the set of user accounts corresponding to the SharePoint Online admins for the isolated team site.</span></span>
  
<span data-ttu-id="1be36-113">如果您正在管理用户帐户和组通过 Office 365，并且想要使用 Windows PowerShell，使列表的用户主体名称 (Upn) (示例 UPN: belindan@contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="1be36-113">If you are managing user accounts and groups through Office 365 and want to use Windows PowerShell, make a list of their user principal names (UPNs) (example UPN: belindan@contoso.com).</span></span>
  
### <a name="step-2-list-the-members-for-the-site"></a><span data-ttu-id="1be36-114">步骤 2： 列出网站的成员</span><span class="sxs-lookup"><span data-stu-id="1be36-114">Step 2: List the members for the site</span></span>

<span data-ttu-id="1be36-115">确定对独立的工作组网站的那些用户将在网站中存储的资源协作的成员对应的用户帐户的组。</span><span class="sxs-lookup"><span data-stu-id="1be36-115">Determine the set of user accounts corresponding to the members for the isolated team site, those who will be collaborating on resources stored within the site.</span></span>
  
<span data-ttu-id="1be36-p103">如果您正在管理用户帐户和组通过 Office 365，并且想要使用 PowerShell，使其 Upn 列表。如果有大量的网站成员，您可以在文本文件中存储的 Upn 列表，并将其添加所有与单个 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="1be36-p103">If you are managing user accounts and groups through Office 365 and want to use PowerShell, make a list of their UPNs. If there are a lot of site members, you can store the list of UPNs in a text file and add them all with a single PowerShell command.</span></span>
  
### <a name="step-3-list-the-viewers-for-the-site"></a><span data-ttu-id="1be36-118">步骤 3： 列出网站的查看者</span><span class="sxs-lookup"><span data-stu-id="1be36-118">Step 3: List the viewers for the site</span></span>

<span data-ttu-id="1be36-119">确定用户帐户对应的独立的工作组网站，那些可以查看网站中存储的资源，但不是修改这些或直接协作及其内容查看者的组。</span><span class="sxs-lookup"><span data-stu-id="1be36-119">Determine the set of user accounts corresponding to the viewers of the isolated team site, those who can view the resources stored in the site but not modify them or directly collaborate on their contents.</span></span>
  
<span data-ttu-id="1be36-p104">如果您正在管理用户帐户和组通过 Office 365，并且想要使用 PowerShell，使其 Upn 列表。如果有大量的网站成员，您可以在文本文件中存储的 Upn 列表，并将其添加所有与单个 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="1be36-p104">If you are managing user accounts and groups through Office 365 and want to use PowerShell, make a list of their UPNs. If there are a lot of site members, you can store the list of UPNs in a text file and add them all with a single PowerShell command.</span></span>
  
<span data-ttu-id="1be36-122">网站的查看者可能包括管理层、 法律顾问或执行部门间利益干系人。</span><span class="sxs-lookup"><span data-stu-id="1be36-122">Viewers for the site might include executive management, legal counsel, or inter-departmental stakeholders.</span></span>
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a><span data-ttu-id="1be36-123">步骤 4: Azure AD 中创建网站的三个访问组</span><span class="sxs-lookup"><span data-stu-id="1be36-123">Step 4: Create the three access groups for the site in Azure AD</span></span>

<span data-ttu-id="1be36-124">您需要在 Azure AD 中创建以下访问组：</span><span class="sxs-lookup"><span data-stu-id="1be36-124">You need to create the following access groups in Azure AD:</span></span>
  
- <span data-ttu-id="1be36-125">网站管理员 （其中将包含步骤 1 中的列表）</span><span class="sxs-lookup"><span data-stu-id="1be36-125">Site admins (which will contain the list from step 1)</span></span>
    
- <span data-ttu-id="1be36-126">网站成员 （其中将包含从步骤 2 列表）</span><span class="sxs-lookup"><span data-stu-id="1be36-126">Site members (which will contain the list from step 2)</span></span>
    
- <span data-ttu-id="1be36-127">网站查看器 （其中将包含从步骤 3 列表）</span><span class="sxs-lookup"><span data-stu-id="1be36-127">Site viewers (which will contain the list from step 3)</span></span>
    
1. <span data-ttu-id="1be36-128">在浏览器中，转到 Azure 门户在[https://portal.azure.com](https://portal.azure.com)和使用已分配与用户管理管理员或公司管理员角色的帐户凭据登录。</span><span class="sxs-lookup"><span data-stu-id="1be36-128">In your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com) and sign in with the credentials of an account that has been assigned with User Management Admin or Company Administrator role.</span></span>
    
2. <span data-ttu-id="1be36-129">在 Azure 门户中，单击“**Azure Active Directory”>“组**”。</span><span class="sxs-lookup"><span data-stu-id="1be36-129">In the Azure portal, click **Azure Active Directory > Groups**.</span></span>
    
3. <span data-ttu-id="1be36-130">在“**组 - 所有组**”边栏选项卡上，单击“**+ 新建组**”。</span><span class="sxs-lookup"><span data-stu-id="1be36-130">On the **Groups - All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="1be36-131">在“**组**”边栏选项卡上：</span><span class="sxs-lookup"><span data-stu-id="1be36-131">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="1be36-132">在“**组类型**”中，选择“**Office 365**”。</span><span class="sxs-lookup"><span data-stu-id="1be36-132">Select **Office 365** in **Group type**.</span></span>
    
  - <span data-ttu-id="1be36-133">在**名称**中键入组名称。</span><span class="sxs-lookup"><span data-stu-id="1be36-133">Type the group name in **Name**.</span></span>
    
  - <span data-ttu-id="1be36-134">在**说明组**中键入组的说明。</span><span class="sxs-lookup"><span data-stu-id="1be36-134">Type a description of the group in **Group description**.</span></span>
    
  - <span data-ttu-id="1be36-135">在“**成员身份**”类型中，选择“**已分配**”。</span><span class="sxs-lookup"><span data-stu-id="1be36-135">Select **Assigned** in **Membership type**.</span></span>
    
5. <span data-ttu-id="1be36-136">单击“**创建**”，然后关闭“**组**”边栏选项卡。</span><span class="sxs-lookup"><span data-stu-id="1be36-136">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="1be36-137">对其他组重复步骤 3-5。</span><span class="sxs-lookup"><span data-stu-id="1be36-137">Repeat steps 3-5 for your additional groups.</span></span>
    
> [!NOTE]
> <span data-ttu-id="1be36-p105">您需要使用 Azure 门户网站创建的组，以便他们已启用的 Office 功能。如果更高版本，SharePoint Online 独立的网站被配置为具有加密文件并将权限分配给特定组 Azure 信息保护 (AIP) 标签的高度机密网站，允许的组必须已创建的 Office 功能启用。创建它之后，您无法更改 Azure AD 组的 Office 功能设置。</span><span class="sxs-lookup"><span data-stu-id="1be36-p105">You need to use the Azure portal to create the groups so that they have Office features enabled. If a SharePoint Online isolated site is later configured as a Highly Confidential site with an Azure Information Protection (AIP) label to encrypt files and assign permission to specific groups, the permitted groups must have been created with Office features enabled. You cannot change the Office features setting of an Azure AD group after it has been created.</span></span> 
  
<span data-ttu-id="1be36-141">下面是与三个网站的访问组您生成的配置。</span><span class="sxs-lookup"><span data-stu-id="1be36-141">Here is your resulting configuration with the three site access groups.</span></span>
  
![三个适用于部署独立 SharePoint Online 网站的访问组。](media/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a><span data-ttu-id="1be36-p106">步骤 5。向 access 组添加用户帐户</span><span class="sxs-lookup"><span data-stu-id="1be36-p106">Step 5. Add the user accounts to the access groups</span></span>

<span data-ttu-id="1be36-145">在此步骤中，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1be36-145">In this step, do the following:</span></span>
  
1. <span data-ttu-id="1be36-146">步骤 1 中的用户列表添加到网站管理员访问组</span><span class="sxs-lookup"><span data-stu-id="1be36-146">Add the list of users from step 1 to the site admins access group</span></span>
    
2. <span data-ttu-id="1be36-147">步骤 2 中的用户列表添加到网站成员访问组</span><span class="sxs-lookup"><span data-stu-id="1be36-147">Add the list of users from step 2 to the site members access group</span></span>
    
3. <span data-ttu-id="1be36-148">步骤 3 中的用户列表添加到网站查看器访问组</span><span class="sxs-lookup"><span data-stu-id="1be36-148">Add the list of users from step 3 to the site viewers access group</span></span>
    
<span data-ttu-id="1be36-149">如果您在管理用户帐户和通过 Windows Server AD 的组，将用户添加到适当的访问组使用普通的 Windows Server AD 用户和组管理过程并等待与 Office 365 订阅的同步。</span><span class="sxs-lookup"><span data-stu-id="1be36-149">If you are managing user accounts and groups through Windows Server AD, add users to the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="1be36-p107">如果您在管理用户帐户和组通过 Office 365，您可以使用 Office 管理中心或 PowerShell。如果您有任何访问组重复组名称，您应使用 Office 管理中心。</span><span class="sxs-lookup"><span data-stu-id="1be36-p107">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell. If you have duplicate group names for any of the access groups, you should use the Office Admin center.</span></span>
  
<span data-ttu-id="1be36-152">对于 Office 管理中心中，使用已分配的用户帐户管理员或公司管理员角色的用户帐户登录，并使用组添加相应的用户帐户和组添加到适当的访问组。</span><span class="sxs-lookup"><span data-stu-id="1be36-152">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate user accounts and groups to the appropriate access groups.</span></span>
  
<span data-ttu-id="1be36-153">Powershell，第一个[使用 Azure Active Directory V2 PowerShell 模块的连接](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="1be36-153">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="1be36-154">接下来，使用以下命令块向 access 组添加单个用户帐户：</span><span class="sxs-lookup"><span data-stu-id="1be36-154">Next, use the following command block to add an individual user account to an access group:</span></span>
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> <span data-ttu-id="1be36-155">对于包含所有 PowerShell 命令和 Excel 的文本文件配置工作表中生成 PowerShell 命令的基于您的组和用户帐户名，下载[独立 SharePoint Online 团队网站部署工具包](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907)。</span><span class="sxs-lookup"><span data-stu-id="1be36-155">For a text file that contains all the PowerShell commands and an Excel configuration worksheet that generates PowerShell commands based on your group and user account names, download the [Isolated SharePoint Online Team Site Deployment Kit](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907).</span></span> 
  
<span data-ttu-id="1be36-156">如果您在文本文件中存储的用户帐户的任何访问组 Upn，您可以使用以下 PowerShell 命令块以将他们添加一次：</span><span class="sxs-lookup"><span data-stu-id="1be36-156">If you stored the UPNs of user accounts for any of the access groups in a text file, you can use the following PowerShell command block to add them all at one time:</span></span>
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

<span data-ttu-id="1be36-157">对于 PowerShell 中，使用以下命令块向 access 组添加单个组：</span><span class="sxs-lookup"><span data-stu-id="1be36-157">For PowerShell, use the following command block to add an individual group to an access group:</span></span>
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

<span data-ttu-id="1be36-158">结果应如下：</span><span class="sxs-lookup"><span data-stu-id="1be36-158">The results should be the following:</span></span>
  
- <span data-ttu-id="1be36-159">网站管理员 Azure AD 组包含的网站管理员用户帐户或组</span><span class="sxs-lookup"><span data-stu-id="1be36-159">The site admins Azure AD group contains the site admin user accounts or groups</span></span>
    
- <span data-ttu-id="1be36-160">网站成员 Azure AD 组包含的网站成员的用户帐户或组</span><span class="sxs-lookup"><span data-stu-id="1be36-160">The site members Azure AD group contains the site member user accounts or groups</span></span>
    
- <span data-ttu-id="1be36-161">网站查看者 Azure AD 组包含用户帐户或组的只能查看网站内容</span><span class="sxs-lookup"><span data-stu-id="1be36-161">The site viewers Azure AD group contains the user accounts or groups that can only view the site contents</span></span>
    
<span data-ttu-id="1be36-162">验证每个访问组与 Office 管理中心或以下 PowerShell 命令块的组成员的列表：</span><span class="sxs-lookup"><span data-stu-id="1be36-162">Validate the list of group members for each access group with the Office Admin center or with the following PowerShell command block:</span></span>
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

<span data-ttu-id="1be36-163">下面是与填充的用户帐户或组的三个网站的访问组您生成的配置。</span><span class="sxs-lookup"><span data-stu-id="1be36-163">Here is your resulting configuration with the three site access groups populated with user accounts or groups.</span></span>
  
![三个使用用户帐户填充的访问组。](media/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a><span data-ttu-id="1be36-165">第 2 阶段： 创建和配置独立的工作组网站</span><span class="sxs-lookup"><span data-stu-id="1be36-165">Phase 2: Create and configure the isolated team site</span></span>

<span data-ttu-id="1be36-166">在此阶段中，您将创建独立的 SharePoint Online 网站，并配置默认 SharePoint Online 权限级别以使用新 Azure 基于 AD 的访问组的权限。</span><span class="sxs-lookup"><span data-stu-id="1be36-166">In this phase, you create the isolated SharePoint Online site and configure the permissions for the default SharePoint Online permission levels to use your new Azure AD-based access groups.</span></span>
  
<span data-ttu-id="1be36-167">首先，通过以下步骤创建 SharePoint Online 团队网站。</span><span class="sxs-lookup"><span data-stu-id="1be36-167">First, create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="1be36-p108">请通过还可用于管理 SharePoint Online 团队网站的帐户（即 SharePoint Online 管理员帐户）登录 Office 365 门户。如需帮助，请参阅[在何处登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="1be36-p108">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="1be36-170">在磁贴列表中，单击“SharePoint”****。</span><span class="sxs-lookup"><span data-stu-id="1be36-170">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="1be36-171">在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。********</span><span class="sxs-lookup"><span data-stu-id="1be36-171">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="1be36-172">在“创建网站”页中，单击“团队网站”********。</span><span class="sxs-lookup"><span data-stu-id="1be36-172">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="1be36-173">在**网站名称**框中，键入工作组网站的名称。</span><span class="sxs-lookup"><span data-stu-id="1be36-173">In **Site name**, type a name for the team site.</span></span> 
    
6. <span data-ttu-id="1be36-174">在**工作组网站说明中，** 键入网站的用途的可选说明。</span><span class="sxs-lookup"><span data-stu-id="1be36-174">In **Team site description,** type an optional description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="1be36-175">在“隐私设置”中，选择“专用 - 仅成员可以访问此网站”，然后单击“下一步”************。</span><span class="sxs-lookup"><span data-stu-id="1be36-175">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="1be36-176">在“希望添加哪些人员?”窗格中，单击“完成”********。</span><span class="sxs-lookup"><span data-stu-id="1be36-176">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="1be36-177">接下来，在新 SharePoint Online 团队网站上，配置权限。</span><span class="sxs-lookup"><span data-stu-id="1be36-177">Next, from the new SharePoint Online team site, configure permissions.</span></span>
  
1. <span data-ttu-id="1be36-178">在工具栏中，依次单击设置图标和“网站权限”****。</span><span class="sxs-lookup"><span data-stu-id="1be36-178">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
2. <span data-ttu-id="1be36-179">在“网站权限”窗格中，单击“高级权限设置”********。</span><span class="sxs-lookup"><span data-stu-id="1be36-179">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
3. <span data-ttu-id="1be36-180">在浏览器的新“权限”标签页中，单击“访问请求设置”********。</span><span class="sxs-lookup"><span data-stu-id="1be36-180">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
4. <span data-ttu-id="1be36-181">在**访问请求设置**对话框中，清除**要共享的网站和单独的文件和文件夹的允许成员**并**允许访问请求**（以便清除所有三个复选框），然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="1be36-181">In the **Access Requests Settings** dialog box, clear **Allow member to share the site and individual files and folders** and **Allow access requests** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
5. <span data-ttu-id="1be36-182">在浏览器的**权限**选项卡上，单击**\<网站名称 > 成员**列表中。</span><span class="sxs-lookup"><span data-stu-id="1be36-182">On the **Permissions** tab of your browser, click **\<site name> Members** in the list.</span></span>
    
6. <span data-ttu-id="1be36-183">在“人员和组”中，单击“新建”********。</span><span class="sxs-lookup"><span data-stu-id="1be36-183">In **People and Groups**, click **New**.</span></span>
    
7. <span data-ttu-id="1be36-184">在**共享**对话框中，键入网站成员访问组的名称，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="1be36-184">In the **Share** dialog box, type the name of the site members access group, select it, and then click **Share**.</span></span>
    
8. <span data-ttu-id="1be36-185">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="1be36-185">Click the back button on your browser.</span></span>
    
9. <span data-ttu-id="1be36-186">单击**\<网站名称 > 所有者**列表中。</span><span class="sxs-lookup"><span data-stu-id="1be36-186">Click **\<site name> Owners** in the list.</span></span>
    
10. <span data-ttu-id="1be36-187">在“人员和组”中，单击“新建”********。</span><span class="sxs-lookup"><span data-stu-id="1be36-187">In **People and Groups**, click **New**.</span></span>
    
11. <span data-ttu-id="1be36-188">在**共享**对话框中，键入网站管理员访问组的名称，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="1be36-188">In the **Share** dialog box, type the name of the site admins access group, select it, and then click **Share**.</span></span>
    
12. <span data-ttu-id="1be36-189">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="1be36-189">Click the back button on your browser.</span></span>
    
13. <span data-ttu-id="1be36-190">单击**\<网站名称 > 访问者**列表中。</span><span class="sxs-lookup"><span data-stu-id="1be36-190">Click **\<site name> Visitors** in the list.</span></span>
    
14. <span data-ttu-id="1be36-191">在“人员和组”中，单击“新建”********。</span><span class="sxs-lookup"><span data-stu-id="1be36-191">In **People and Groups**, click **New**.</span></span>
    
15. <span data-ttu-id="1be36-192">在**共享**对话框中，键入网站的查看者访问组的名称，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="1be36-192">In the **Share** dialog box, type the name of the site viewers access group, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="1be36-193">关闭浏览器的“权限”标签页****。</span><span class="sxs-lookup"><span data-stu-id="1be36-193">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="1be36-194">以下是这些权限设置的结果：</span><span class="sxs-lookup"><span data-stu-id="1be36-194">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="1be36-195">**\<网站名称 > 所有者**SharePoint 组包含所有成员中具有**完全控制**权限级别的网站管理员访问组。</span><span class="sxs-lookup"><span data-stu-id="1be36-195">The **\<site name> Owners** SharePoint group contains the site admins access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="1be36-196">**\<网站名称 > 成员**中的所有成员都具有**编辑**权限级别的网站成员访问组所在的 SharePoint 组。</span><span class="sxs-lookup"><span data-stu-id="1be36-196">The **\<site name> Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="1be36-197">**\<网站名称 > 访问者**中所有成员具有**读取**权限级别的网站查看器访问组所在的 SharePoint 组。</span><span class="sxs-lookup"><span data-stu-id="1be36-197">The **\<site name> Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="1be36-198">要邀请其他成员成员或非成员请求访问的功能被禁用。</span><span class="sxs-lookup"><span data-stu-id="1be36-198">The ability for members to invite other members or for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="1be36-199">下面是生成配置与网站配置为使用三个访问组，填入用户帐户或 Azure AD 组的三个 SharePoint 组。</span><span class="sxs-lookup"><span data-stu-id="1be36-199">Here is your resulting configuration with the three SharePoint groups for the site configured to use the three access groups, which are populated with user accounts or Azure AD groups.</span></span>
  
![包含访问组和用户帐户的独立 SharePoint Online 网站的最终配置。](media/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
<span data-ttu-id="1be36-201">您和网站，通过组成员的访问组中，之一的成员可以立即协作使用网站的资源。</span><span class="sxs-lookup"><span data-stu-id="1be36-201">You and the members of the site, through group membership in one of the access groups, can now collaborate using the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="1be36-202">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1be36-202">Next step</span></span>

<span data-ttu-id="1be36-203">当您需要更改网站的访问组成员身份或创建具有自定义权限的文档文件夹时，请参阅[Manage 独立的 SharePoint Online 团队网站](manage-an-isolated-sharepoint-online-team-site.md)。</span><span class="sxs-lookup"><span data-stu-id="1be36-203">When you need to change site access group membership or create a document folder with custom permissions, see [Manage an isolated SharePoint Online team site](manage-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1be36-204">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1be36-204">See Also</span></span>

[<span data-ttu-id="1be36-205">独立 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="1be36-205">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="1be36-206">设计独立 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="1be36-206">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="1be36-207">管理单独的 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="1be36-207">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="1be36-208">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="1be36-208">Security solutions</span></span>](security-solutions.md)



