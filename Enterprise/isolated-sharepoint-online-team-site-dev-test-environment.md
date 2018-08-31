---
title: 独立 SharePoint Online 团队网站开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d1795031-beef-49ea-a6fc-5da5450d320d
description: 摘要： 配置的 Office 365 开发/测试环境中的组织的其余部分隔离的 SharePoint Online 团队网站。
ms.openlocfilehash: d2a75f3a3a410116c454892c9ecf3747fb3da53d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915047"
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a><span data-ttu-id="28e8d-103">独立 SharePoint Online 团队网站开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="28e8d-103">Isolated SharePoint Online team site dev/test environment</span></span>

 <span data-ttu-id="28e8d-104">**摘要：** 配置 Office 365 开发/测试环境的组织的其余部分隔离的 SharePoint Online 团队网站。</span><span class="sxs-lookup"><span data-stu-id="28e8d-104">**Summary:** Configure a SharePoint Online team site that is isolated from the rest of the organization in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="28e8d-p101">Office 365 中的 SharePoint Online 团队网站是协作使用常见的文档库、 OneNote 笔记本和其他服务的位置。在许多情况下，跨部门或组织希望范围访问和协作。但是，在某些情况下，您想要严格控制访问和小组人之间的协作程序的权限。</span><span class="sxs-lookup"><span data-stu-id="28e8d-p101">SharePoint Online team sites in Office 365 are locations for collaboration using a common document library, a OneNote notebook, and other services. In many cases, you want wide access and collaboration across departments or organizations. However, in some cases, you want to tightly control the access and permissions for collaboration among a small group of people.</span></span>
  
<span data-ttu-id="28e8d-p102">由 SharePoint 组和权限级别控制访问 SharePoint Online 团队网站和用户可以执行的操作。默认情况下，SharePoint Online 网站具有三种访问级别：</span><span class="sxs-lookup"><span data-stu-id="28e8d-p102">Access to SharePoint Online team sites and what users can do is controlled by SharePoint groups and permission levels. By default, SharePoint Online sites have three levels of access:</span></span>
  
- <span data-ttu-id="28e8d-110">**成员**：可以在网站上查看、创建和修改资源。</span><span class="sxs-lookup"><span data-stu-id="28e8d-110">**Members**, who can view, create, and modify resources on the site.</span></span>
    
- <span data-ttu-id="28e8d-111">**所有者**：可完全控制网站，包括能够更改权限。</span><span class="sxs-lookup"><span data-stu-id="28e8d-111">**Owners**, who have complete control of the site, including the ability to change permissions.</span></span>
    
- <span data-ttu-id="28e8d-112">**访问者**：只能在网站上查看资源。</span><span class="sxs-lookup"><span data-stu-id="28e8d-112">**Visitors**, who only can view resources on the site.</span></span>
    
<span data-ttu-id="28e8d-p103">此文章步骤您通过独立的 SharePoint Online 团队网站机密信息检索项目的配置名为 ProjectX。访问要求如下：</span><span class="sxs-lookup"><span data-stu-id="28e8d-p103">This article steps you through the configuration of an isolated SharePoint Online team site for a secret research project named ProjectX. The access requirements are:</span></span>
  
- <span data-ttu-id="28e8d-115">只有此项目的成员才能访问网站及其内容（文档、OneNote 笔记本、网页），编辑和查看 SharePoint 权限级别是通过组成员身份进行控制。</span><span class="sxs-lookup"><span data-stu-id="28e8d-115">Only members of the project can access the site and its contents (documents, OneNote Notebook, Pages), with edit and view SharePoint permission levels controlled through group membership.</span></span>
    
- <span data-ttu-id="28e8d-116">只有网站创建者和网站管理员组成员才能管理网站，包括可以修改网站级权限。</span><span class="sxs-lookup"><span data-stu-id="28e8d-116">Only the site creator and members of an Admins group for the site can perform site administration, which includes modifying site-level permissions.</span></span>
    
<span data-ttu-id="28e8d-117">有三个阶段设置 Office 365 开发/测试环境中的独立 SharePoint Online 团队网站：</span><span class="sxs-lookup"><span data-stu-id="28e8d-117">There are three phases to setting up an isolated SharePoint Online team site in your Office 365 dev/test environment:</span></span>
  
1. <span data-ttu-id="28e8d-118">创建 Office 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="28e8d-118">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="28e8d-119">创建 ProjectX 用户和组。</span><span class="sxs-lookup"><span data-stu-id="28e8d-119">Create the users and groups for ProjectX.</span></span>
    
3. <span data-ttu-id="28e8d-120">创建新的 ProjectX SharePoint Online 团队网站，并将其隔离。</span><span class="sxs-lookup"><span data-stu-id="28e8d-120">Create a new ProjectX SharePoint Online team site and isolate it.</span></span>
    
> [!TIP]
> <span data-ttu-id="28e8d-121">单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="28e8d-121">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="28e8d-122">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="28e8d-122">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="28e8d-123">如果您只想要的最低硬件要求与轻型的方式创建独立的 SharePoint Online 团队网站，请在阶段 2 和 3 的[Office 365 开发/测试环境](office-365-dev-test-environment.md)按照的说明。</span><span class="sxs-lookup"><span data-stu-id="28e8d-123">If you just want to create an isolated SharePoint Online team site in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="28e8d-124">如果您想要创建独立的 SharePoint Online 团队网站模拟的企业配置中，按照[目录同步的 Office 365 开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="28e8d-124">If you want to create an isolated SharePoint Online team site in a simulated enterprise configuration, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="28e8d-p104">创建独立 SharePoint Online 网站不需要模拟的企业开发/测试环境（包括连接 Internet 的模拟 Intranet 和 Windows Server AD 林的目录同步）。可以根据需要选择此选项，以便能够测试独立 SharePoint Online 网站，并在代表典型组织的环境中对其进行试验。</span><span class="sxs-lookup"><span data-stu-id="28e8d-p104">Creating an isolated SharePoint Online site does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test an isolated SharePoint Online site and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a><span data-ttu-id="28e8d-127">阶段 2： 创建用户帐户并访问组</span><span class="sxs-lookup"><span data-stu-id="28e8d-127">Phase 2: Create user accounts and access groups</span></span>

<span data-ttu-id="28e8d-128">使用中的说明[连接到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx)连接到您的全局管理员帐户从 Office 365 线索订阅：</span><span class="sxs-lookup"><span data-stu-id="28e8d-128">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to connect to your Office 365 trail subscription with your global administrator account from:</span></span>
  
- <span data-ttu-id="28e8d-129">你的计算机（对于轻量级的 Office 365 开发/测试环境）。</span><span class="sxs-lookup"><span data-stu-id="28e8d-129">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="28e8d-130">CLIENT1 虚拟机（对于模拟的企业 Office 365 开发/测试环境）。</span><span class="sxs-lookup"><span data-stu-id="28e8d-130">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="28e8d-131">若要创建新的访问组 ProjectX SharePoint Online 团队网站，请在 Windows Azure Active Directory 模块用于 Windows PowerShell 提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="28e8d-131">To create the new access groups for the ProjectX SharePoint Online team site, run these commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$groupName="ProjectX-Members"
$groupDesc="People allowed to collaborate for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Admins"
$groupDesc="People allowed to administer SharePoint for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Viewers"
$groupDesc="People allowed to view the SharePoint resources for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
```

> [!TIP]
> <span data-ttu-id="28e8d-132">单击[此处](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1)为包含所有这篇文章中的 PowerShell 命令的文本文件。</span><span class="sxs-lookup"><span data-stu-id="28e8d-132">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) for a text file that contains all of the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="28e8d-133">填写组织名称（示例：contosotoycompany），你所在位置的两位字符的国家/地区代码，然后从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="28e8d-133">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="28e8d-134">在安全的位置上，记下显示的 **New-MsolUser** 命令中为 Lead Designer 帐户生成的密码。</span><span class="sxs-lookup"><span data-stu-id="28e8d-134">From the display of the **New-MsolUser** command, note the generated password for the Lead Designer account and record it in a safe location.</span></span>
  
<span data-ttu-id="28e8d-135">从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="28e8d-135">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="28e8d-136">在安全的位置上，记下显示的 **New-MsolUser** 命令中为 Lead Researcher 帐户生成的密码。</span><span class="sxs-lookup"><span data-stu-id="28e8d-136">From the display of the **New-MsolUser** command, note the generated password for the Lead Researcher account and record it in a safe location.</span></span>
  
<span data-ttu-id="28e8d-137">从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="28e8d-137">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="28e8d-138">在安全的位置上，记下显示的 **New-MsolUser** 命令中为 Development VP 帐户生成的密码。</span><span class="sxs-lookup"><span data-stu-id="28e8d-138">From the display of the **New-MsolUser** command, note the generated password for the Development VP account and record it in a safe location.</span></span>
  
<span data-ttu-id="28e8d-139">接下来，将新的帐户添加到新的访问组，这些 PowerShell 命令提示符处运行 Windows Azure Active Directory 的 Windows PowerShell 模块：</span><span class="sxs-lookup"><span data-stu-id="28e8d-139">Next, to add the new accounts to the new access groups, run these PowerShell commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$grpName="ProjectX-Members"
$userUPN="designer@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$userUPN="researcher@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Admins"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userCredential.UserName }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Viewers"
$userUPN="devvp@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
```

<span data-ttu-id="28e8d-140">结果：</span><span class="sxs-lookup"><span data-stu-id="28e8d-140">Results:</span></span>
  
- <span data-ttu-id="28e8d-141">ProjectX 成员访问组包含导致 Designer 和导致研究人员用户帐户</span><span class="sxs-lookup"><span data-stu-id="28e8d-141">The ProjectX-Members access group contains the Lead Designer and Lead Researcher user accounts</span></span>
    
- <span data-ttu-id="28e8d-142">ProjectX Admins 访问组包含您的试用版订阅的全局管理员帐户</span><span class="sxs-lookup"><span data-stu-id="28e8d-142">The ProjectX-Admins access group contains the global administrator account for your trial subscription</span></span>
    
- <span data-ttu-id="28e8d-143">ProjectX 查看器访问组包含开发 VP 用户帐户</span><span class="sxs-lookup"><span data-stu-id="28e8d-143">The ProjectX-Viewers access group contains the Development VP user account</span></span>
    
<span data-ttu-id="28e8d-144">图 1 显示了访问组和其成员资格。</span><span class="sxs-lookup"><span data-stu-id="28e8d-144">Figure 1 shows the access groups and their membership.</span></span>
  
<span data-ttu-id="28e8d-145">**图 1**</span><span class="sxs-lookup"><span data-stu-id="28e8d-145">**Figure 1**</span></span>

![独立 SharePoint Online 组网站的 Office 365 组及其成员资格](media/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a><span data-ttu-id="28e8d-147">阶段 3： 创建新的 ProjectX SharePoint Online 团队网站，并将其隔离</span><span class="sxs-lookup"><span data-stu-id="28e8d-147">Phase 3: Create a new ProjectX SharePoint Online team site and isolate it</span></span>

<span data-ttu-id="28e8d-148">要创建 ProjectX SharePoint Online 团队网站，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="28e8d-148">To create a SharePoint Online team site for ProjectX, do the following:</span></span>
  
1. <span data-ttu-id="28e8d-149">本地计算机 （轻型配置） 上使用浏览器或在 CLIENT1 上 （模拟的企业配置），登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="28e8d-149">Using a browser on either your local computer (lightweight configuration) or on CLIENT1 (simulated enterprise configuration), sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="28e8d-150">在磁贴列表中，单击“SharePoint”****。</span><span class="sxs-lookup"><span data-stu-id="28e8d-150">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="28e8d-151">在新 SharePoint 选项卡在浏览器中，单击 **+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-151">On the new SharePoint tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="28e8d-p105">在**工作组网站名称**框中，键入**ProjectX**。在**隐私设置**中，选择**专用-只有成员可以访问此网站**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-p105">In **Team site name**, type **ProjectX**. In **Privacy settings**, select **Private - only members can access this site**.</span></span>
    
5. <span data-ttu-id="28e8d-154">在**团队网站说明**框中，键入**ProjectX 的 SharePoint 网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-154">In **Team site description**, type **SharePoint site for ProjectX**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="28e8d-155">在**要添加人员**？窗格中，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-155">On the **Who do you want to add**? pane, click **Finish**.</span></span>
    
7. <span data-ttu-id="28e8d-156">在浏览器中，在工具栏中，在新**ProjectX 主页**选项卡上单击设置图标，然后单击**网站权限**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-156">On the new **ProjectX-Home** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
8. <span data-ttu-id="28e8d-157">在“网站权限”窗格中，单击“高级权限设置”********。</span><span class="sxs-lookup"><span data-stu-id="28e8d-157">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
9. <span data-ttu-id="28e8d-158">在新**权限： 项目 X**选项卡上在浏览器中，单击**访问请求设置**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-158">In the new **Permissions: Project X** tab in your browser, click **Access Request Settings**.</span></span>
    
10. <span data-ttu-id="28e8d-159">在**访问请求设置**对话框中，清除**允许成员来共享网站和单独的文件和文件夹**和**允许访问请求**（以便清除所有三个复选框），然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-159">In the **Access Requests Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow access requests** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
11. <span data-ttu-id="28e8d-160">在列表中单击**ProjectX 成员**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-160">Click **ProjectX Members** in the list.</span></span>
    
12. <span data-ttu-id="28e8d-161">在“人员和组”页中，单击“新建”********。</span><span class="sxs-lookup"><span data-stu-id="28e8d-161">On the **People and Groups** page, click **New**.</span></span>
    
13. <span data-ttu-id="28e8d-162">**共享**对话框中，键入**ProjectX 成员**和选择它，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-162">In the **Share** dialog box, type **ProjectX-Members**, select it, and then click **Share**.</span></span>
    
14. <span data-ttu-id="28e8d-163">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="28e8d-163">Click the back button on your browser.</span></span>
    
15. <span data-ttu-id="28e8d-164">在列表中单击**ProjectX 所有者**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-164">Click **ProjectX Owners** in the list.</span></span>
    
16. <span data-ttu-id="28e8d-165">在“人员和组”页中，单击“新建”********。</span><span class="sxs-lookup"><span data-stu-id="28e8d-165">On the **People and Groups** page, click **New**.</span></span>
    
17. <span data-ttu-id="28e8d-166">在**共享**对话框中，键入**ProjectX 管理员**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-166">In the **Share** dialog box, type **ProjectX-Admins**, select it, and then click **Share**.</span></span>
    
18. <span data-ttu-id="28e8d-167">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="28e8d-167">Click the back button on your browser.</span></span>
    
19. <span data-ttu-id="28e8d-168">在列表中，单击**ProjectX 访问者**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-168">Click **ProjectX Visitors** in the list.</span></span>
    
20. <span data-ttu-id="28e8d-169">在“人员和组”页中，单击“新建”********。</span><span class="sxs-lookup"><span data-stu-id="28e8d-169">On the **People and Groups** page, click **New**.</span></span>
    
21. <span data-ttu-id="28e8d-170">**共享**对话框中，键入**ProjectX 查看者**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-170">In the **Share** dialog box, type **ProjectX-Viewers**, select it, and then click **Share**.</span></span>
    
22. <span data-ttu-id="28e8d-171">关闭浏览器中的**人员和组**选项卡，单击浏览器中， **ProjectX 主页**选项卡，然后关闭**网站权限**窗格。</span><span class="sxs-lookup"><span data-stu-id="28e8d-171">Close the **People and Groups** tab in your browser, click the **ProjectX-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="28e8d-172">权限的配置结果如下所示：</span><span class="sxs-lookup"><span data-stu-id="28e8d-172">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="28e8d-173">ProjectX 成员 SharePoint 组包含仅 ProjectX 成员访问 （其中包含只会导致设计器和导致研究人员用户帐户） 和 ProjectX 组 （其中包含仅的全局管理员用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="28e8d-173">The ProjectX Members SharePoint group contains only the ProjectX-Members access group (which contains only the Lead Designer and Lead Researcher user accounts) and the ProjectX group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="28e8d-174">ProjectX 所有者 SharePoint 组包含仅 ProjectX Admins 访问组 （其中包含仅的全局管理员用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="28e8d-174">The ProjectX Owners SharePoint group contains only the ProjectX-Admins access group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="28e8d-175">ProjectX 访问者 SharePoint 组包含仅 ProjectX 查看器访问组 （其中包含只有开发 VP 用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="28e8d-175">The ProjectX Visitors SharePoint group contains only the ProjectX-Viewers access group (which contains only the Development VP user account).</span></span>
    
- <span data-ttu-id="28e8d-176">成员无法修改网站级权限（只有 ProjectX-Admins 组成员才能修改）。</span><span class="sxs-lookup"><span data-stu-id="28e8d-176">Members cannot modify site-level permissions (this can only be done by members of the ProjectX-Admins group).</span></span>
    
- <span data-ttu-id="28e8d-177">其他用户帐户无法访问网站及其资源，也无法请求访问网站。</span><span class="sxs-lookup"><span data-stu-id="28e8d-177">Other user accounts cannot access the site or its resources or request access to the site.</span></span>
    
<span data-ttu-id="28e8d-178">图 2 展示了 SharePoint 组及其成员身份。</span><span class="sxs-lookup"><span data-stu-id="28e8d-178">Figure 2 shows the SharePoint groups and their membership.</span></span>
  
<span data-ttu-id="28e8d-179">**图 2**</span><span class="sxs-lookup"><span data-stu-id="28e8d-179">**Figure 2**</span></span>

![独立 SharePoint Online 组网站的 SharePoint Online 组及其成员资格](media/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
<span data-ttu-id="28e8d-181">现在让我们演示使用导致设计器的用户帐户的访问：</span><span class="sxs-lookup"><span data-stu-id="28e8d-181">Now let's demonstrate access using the Lead Designer user account:</span></span>
  
1. <span data-ttu-id="28e8d-182">关闭浏览器中， **ProjectX 主页**选项卡，然后单击在浏览器中的**Microsoft Office Home**选项卡。</span><span class="sxs-lookup"><span data-stu-id="28e8d-182">Close the **ProjectX-Home** tab in your browser, and then click the **Microsoft Office Home** tab in your browser.</span></span>
    
2. <span data-ttu-id="28e8d-183">单击您的全局管理员的名称，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-183">Click the name of your global administrator, and then click **Sign out**.</span></span>
    
3. <span data-ttu-id="28e8d-184">登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用导致 Designer 帐户名和其密码。</span><span class="sxs-lookup"><span data-stu-id="28e8d-184">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the Lead Designer account name and its password.</span></span>
    
4. <span data-ttu-id="28e8d-185">在磁贴列表中，单击“SharePoint”****。</span><span class="sxs-lookup"><span data-stu-id="28e8d-185">In the list of tiles, click **SharePoint**.</span></span>
    
5. <span data-ttu-id="28e8d-p106">在新**SharePoint**选项卡在浏览器中，在搜索框中键入**ProjectX**激活搜索，，然后单击**ProjectX**工作组网站。在浏览器中的 ProjectX 工作组网站，您应看到新选项卡。</span><span class="sxs-lookup"><span data-stu-id="28e8d-p106">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box, activate the search, and then click the **ProjectX** team site. You should see a new tab in your browser for the ProjectX team site.</span></span>
    
6. <span data-ttu-id="28e8d-p107">单击设置图标。请注意，没有**网站**权限的选项。这是正确的因为只会将 ProjectX Admins 组的成员可以修改网站上的权限</span><span class="sxs-lookup"><span data-stu-id="28e8d-p107">Click the settings icon. Notice that there is no option for **Site Permissions**. This is correct because only the members of the ProjectX-Admins group can modify permissions on the site</span></span>
    
7. <span data-ttu-id="28e8d-191">打开选择的记事本或文本编辑器。</span><span class="sxs-lookup"><span data-stu-id="28e8d-191">Open Notepad or a text editor of your choice.</span></span>
    
8. <span data-ttu-id="28e8d-192">复制 ProjectX 工作组网站的 URL，并将其粘贴到记事本或文本编辑器中的新行。</span><span class="sxs-lookup"><span data-stu-id="28e8d-192">Copy the URL of the ProjectX team site and paste it on a new line in Notepad or your text editor.</span></span>
    
9. <span data-ttu-id="28e8d-193">在新**ProjectX 主页**选项卡在浏览器中，单击**文档**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-193">On the new **ProjectX-Home** tab in your browser, click **Documents**.</span></span>
    
10. <span data-ttu-id="28e8d-194">将 ProjectX 文档文件夹的 URL 复制并粘贴到记事本或文本编辑器中的新行上。</span><span class="sxs-lookup"><span data-stu-id="28e8d-194">Copy the URL of the ProjectX documents folder and paste it on a new line in Notepad or your text editor.</span></span>
    
11. <span data-ttu-id="28e8d-195">在新**ProjectX 文档**选项卡在浏览器中，单击**新建 > Word 文档**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-195">On the new **ProjectX-Documents** tab in your browser, click **New > Word document**.</span></span>
    
12. <span data-ttu-id="28e8d-p108">在**Word Online**页上键入一些文本，等待状态指示**保存**，单击浏览器中，在后退按钮，然后刷新页面。您应看到新**Document.docx** **文档**文件夹中。</span><span class="sxs-lookup"><span data-stu-id="28e8d-p108">Type some text in the **Word Online** page, wait for the status to indicate **Saved**, click the back button on your browser, and then refresh the page. You should see a new **Document.docx** in the **Documents** folder.</span></span>
    
13. <span data-ttu-id="28e8d-198">单击省略号**Document.docx**文档，然后单击**获取链接**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-198">Click the ellipsis for the **Document.docx** document, and then click **Get a link**.</span></span>
    
14. <span data-ttu-id="28e8d-199">在**共享 Document.docx'** 对话框中复制的 URL 和将其粘贴到记事本或文本编辑器中中的新行，然后关闭**共享 Document.docx**对话框中。</span><span class="sxs-lookup"><span data-stu-id="28e8d-199">Copy the URL in the **Share 'Document.docx'** dialog box and paste it on a new line in Notepad or your text editor, and then close the **Share 'Document.docx'** dialog box.</span></span>
    
15. <span data-ttu-id="28e8d-200">关闭浏览器中的**ProjectX 文档**和**SharePoint**选项卡，然后单击**Microsoft Office Home**选项卡。</span><span class="sxs-lookup"><span data-stu-id="28e8d-200">Close the **ProjectX-Documents** and **SharePoint** tabs in your browser, and then click the **Microsoft Office Home** tab.</span></span>
    
16. <span data-ttu-id="28e8d-201">单击**导致设计器**名称，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-201">Click the **Lead Designer** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="28e8d-202">现在让我们演示使用开发 VP 用户帐户的访问：</span><span class="sxs-lookup"><span data-stu-id="28e8d-202">Now let's demonstrate access using the Development VP user account:</span></span>
  
1. <span data-ttu-id="28e8d-203">登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用的开发 VP 帐户名和其密码。</span><span class="sxs-lookup"><span data-stu-id="28e8d-203">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the Development VP account name and its password.</span></span>
    
2. <span data-ttu-id="28e8d-204">在磁贴列表中，单击“SharePoint”****。</span><span class="sxs-lookup"><span data-stu-id="28e8d-204">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="28e8d-p109">在新**SharePoint**选项卡在浏览器中，在搜索框中键入**ProjectX**激活搜索，，然后单击**ProjectX**工作组网站。在浏览器中的 ProjectX 工作组网站，您应看到新选项卡。</span><span class="sxs-lookup"><span data-stu-id="28e8d-p109">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box, activate the search, and then click the **ProjectX** team site. You should see a new tab in your browser for the ProjectX team site.</span></span>
    
4. <span data-ttu-id="28e8d-207">单击**文档**，然后单击**Document.docx**文件。</span><span class="sxs-lookup"><span data-stu-id="28e8d-207">Click **Documents**, and then click the **Document.docx** file.</span></span>
    
5. <span data-ttu-id="28e8d-p110">在浏览器中**Document.docx**选项卡上，在尝试修改的文本。您应看到一条消息指出**本文档是只读的。** 此举有望因为的开发 VP 用户帐户只具有该网站的查看权限。</span><span class="sxs-lookup"><span data-stu-id="28e8d-p110">In the **Document.docx** tab in your browser, try to modify the text. You should see a message stating **This document is read-only.** This is expected because the Development VP user account only has view permissions for the site.</span></span>
    
6. <span data-ttu-id="28e8d-211">关闭浏览器中的**Document.docx**、 **ProjectX 文档**和**SharePoint**选项卡。</span><span class="sxs-lookup"><span data-stu-id="28e8d-211">Close the **Document.docx**, **ProjectX-Documents**, and **SharePoint** tabs in your browser.</span></span>
    
7. <span data-ttu-id="28e8d-212">单击**Microsoft Office Home**选项卡，单击**开发 VP**名称，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-212">Click the **Microsoft Office Home** tab, click the **Development VP** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="28e8d-213">现在让我们演示使用没有任何权限的用户帐户的访问：</span><span class="sxs-lookup"><span data-stu-id="28e8d-213">Now let's demonstrate access with a user account that has no permissions:</span></span>
  
1. <span data-ttu-id="28e8d-214">登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用用户 3 帐户名和其密码。</span><span class="sxs-lookup"><span data-stu-id="28e8d-214">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the User 3 account name and its password.</span></span>
    
2. <span data-ttu-id="28e8d-215">在磁贴列表中，单击“SharePoint”****。</span><span class="sxs-lookup"><span data-stu-id="28e8d-215">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="28e8d-p111">在新**SharePoint**选项卡在浏览器中，在搜索框中键入**ProjectX** ，然后激活搜索。您应看到消息**Nothing 此处匹配您的搜索。**</span><span class="sxs-lookup"><span data-stu-id="28e8d-p111">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box and then activate the search. You should see the message **Nothing here matches your search.**</span></span>
    
4. <span data-ttu-id="28e8d-p112">从记事本或文本编辑器打开实例，将 ProjectX 网站的 URL 复制到您的浏览器的地址栏，然后按**Enter**。您应看到**访问被拒绝**页面。</span><span class="sxs-lookup"><span data-stu-id="28e8d-p112">From the open instance of Notepad or your text editor, copy the URL for the ProjectX site into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
5. <span data-ttu-id="28e8d-p113">从记事本或文本编辑器中，将 ProjectX 文档文件夹的 URL 复制到您的浏览器的地址栏，然后按**Enter**。您应看到**访问被拒绝**页面。</span><span class="sxs-lookup"><span data-stu-id="28e8d-p113">From Notepad or your text editor, copy the URL for the ProjectX Documents folder into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
6. <span data-ttu-id="28e8d-p114">从记事本或文本编辑器中，复制到您的浏览器的地址栏的 Documents.docx 文件的 URL，然后按**Enter**。您应看到**访问被拒绝**页面。</span><span class="sxs-lookup"><span data-stu-id="28e8d-p114">From Notepad or your text editor, copy the URL for the Documents.docx file into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
7. <span data-ttu-id="28e8d-224">关闭浏览器中的**SharePoint**选项卡，单击**Microsoft Office Home**选项卡，单击**用户 3**的名称，，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="28e8d-224">Close the **SharePoint** tab in your browser, click the **Microsoft Office Home** tab, click the **User 3** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="28e8d-225">独立的 SharePoint Online 网站现在就您的其他实验。</span><span class="sxs-lookup"><span data-stu-id="28e8d-225">Your isolated SharePoint Online site is now ready for your additional experimentation.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="28e8d-226">后续步骤</span><span class="sxs-lookup"><span data-stu-id="28e8d-226">Next Step</span></span>

<span data-ttu-id="28e8d-227">当准备好在生产中部署单独的 SharePoint Online 团队网站后，请参阅[设计单独的 SharePoint Online 团队网站](design-an-isolated-sharepoint-online-team-site.md)中的分步设计注意事项。</span><span class="sxs-lookup"><span data-stu-id="28e8d-227">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="28e8d-228">另请参阅</span><span class="sxs-lookup"><span data-stu-id="28e8d-228">See Also</span></span>

[<span data-ttu-id="28e8d-229">独立 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="28e8d-229">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="28e8d-230">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="28e8d-230">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="28e8d-231">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="28e8d-231">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="28e8d-232">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="28e8d-232">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="28e8d-233">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="28e8d-233">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




