---
title: "SharePoint Online 的团队站点开发/测试环境的独立"
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
description: "摘要： 配置 Office 365 开发/测试环境中组织的其余部分隔离的 SharePoint Online 工作组网站。"
ms.openlocfilehash: c6115e48f1b2453aaf173b384a30c1cc34ce7b5a
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a><span data-ttu-id="06557-103">SharePoint Online 的团队站点开发/测试环境的独立</span><span class="sxs-lookup"><span data-stu-id="06557-103">Isolated SharePoint Online team site dev/test environment</span></span>

 <span data-ttu-id="06557-104">**摘要：**配置与您 Office 365 的开发/测试环境中组织的其余部分隔离的 SharePoint Online 工作组网站。</span><span class="sxs-lookup"><span data-stu-id="06557-104">**Summary:** Configure a SharePoint Online team site that is isolated from the rest of the organization in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="06557-p101">Office 365 中的 SharePoint Online 工作组网站是协作使用公共的文档库，OneNote 笔记本和其他服务的地方。在许多情况下，跨部门或组织希望广泛访问和协作。但是，在某些情况下，要严格控制访问和权限的一小群人之间的协作。</span><span class="sxs-lookup"><span data-stu-id="06557-p101">SharePoint Online team sites in Office 365 are locations for collaboration using a common document library, a OneNote notebook, and other services. In many cases, you want wide access and collaboration across departments or organizations. However, in some cases, you want to tightly control the access and permissions for collaboration among a small group of people.</span></span>
  
<span data-ttu-id="06557-p102">通过 SharePoint 组和权限级别控制访问 SharePoint Online 的工作组站点和用户可以执行哪些操作。默认情况下，SharePoint Online 网站有三个访问级别：</span><span class="sxs-lookup"><span data-stu-id="06557-p102">Access to SharePoint Online team sites and what users can do is controlled by SharePoint groups and permission levels. By default, SharePoint Online sites have three levels of access:</span></span>
  
- <span data-ttu-id="06557-110">**成员**，可以查看、 创建和修改站点上的资源。</span><span class="sxs-lookup"><span data-stu-id="06557-110">**Members**, who can view, create, and modify resources on the site.</span></span>
    
- <span data-ttu-id="06557-111">**所有者**，拥有网站的完全控制，包括更改权限的能力。</span><span class="sxs-lookup"><span data-stu-id="06557-111">**Owners**, who have complete control of the site, including the ability to change permissions.</span></span>
    
- <span data-ttu-id="06557-112">**访问者**的用户才可以查看资源的网站上。</span><span class="sxs-lookup"><span data-stu-id="06557-112">**Visitors**, who only can view resources on the site.</span></span>
    
<span data-ttu-id="06557-p103">此步骤通过秘密研究项目独立 SharePoint Online 团队站点的配置命名为 ProjectX。访问要求如下：</span><span class="sxs-lookup"><span data-stu-id="06557-p103">This article steps you through the configuration of an isolated SharePoint Online team site for a secret research project named ProjectX. The access requirements are:</span></span>
  
- <span data-ttu-id="06557-115">只有此项目的成员才能访问网站及其内容（文档、OneNote 笔记本、网页），编辑和查看 SharePoint 权限级别是通过组成员身份进行控制。</span><span class="sxs-lookup"><span data-stu-id="06557-115">Only members of the project can access the site and its contents (documents, OneNote Notebook, Pages), with edit and view SharePoint permission levels controlled through group membership.</span></span>
    
- <span data-ttu-id="06557-116">只有网站创建者和网站管理员组成员才能管理网站，包括可以修改网站级权限。</span><span class="sxs-lookup"><span data-stu-id="06557-116">Only the site creator and members of an Admins group for the site can perform site administration, which includes modifying site-level permissions.</span></span>
    
<span data-ttu-id="06557-117">没有设置独立的 SharePoint Online 团队站点您 Office 365 的开发/测试环境中的三个阶段：</span><span class="sxs-lookup"><span data-stu-id="06557-117">There are three phases to setting up an isolated SharePoint Online team site in your Office 365 dev/test environment:</span></span>
  
1. <span data-ttu-id="06557-118">创建 Office 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="06557-118">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="06557-119">创建 ProjectX 用户和组。</span><span class="sxs-lookup"><span data-stu-id="06557-119">Create the users and groups for ProjectX.</span></span>
    
3. <span data-ttu-id="06557-120">创建新的团队 ProjectX SharePoint Online 网站并将其隔离。</span><span class="sxs-lookup"><span data-stu-id="06557-120">Create a new ProjectX SharePoint Online team site and isolate it.</span></span>
    
> [!TIP]
> <span data-ttu-id="06557-121">单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。</span><span class="sxs-lookup"><span data-stu-id="06557-121">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="06557-122">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="06557-122">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="06557-123">如果要仅达到最低要求轻量级的方式创建独立的在线 SharePoint 工作组网站，按照在阶段 2 和 3 的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="06557-123">If you just want to create an isolated SharePoint Online team site in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="06557-124">如果您想要在模拟的企业配置中创建独立的在线 SharePoint 工作组网站，请按[您 Office 365 的开发/测试环境的目录同步](dirsync-for-your-office-365-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="06557-124">If you want to create an isolated SharePoint Online team site in a simulated enterprise configuration, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="06557-p104">创建独立 SharePoint Online 网站不需要模拟的企业开发/测试环境（包括连接 Internet 的模拟 Intranet 和 Windows Server AD 林的目录同步）。可以根据需要选择此选项，以便能够测试独立 SharePoint Online 网站，并在代表典型组织的环境中对其进行试验。</span><span class="sxs-lookup"><span data-stu-id="06557-p104">Creating an isolated SharePoint Online site does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test an isolated SharePoint Online site and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a><span data-ttu-id="06557-127">第 2 阶段： 创建用户帐户和访问组</span><span class="sxs-lookup"><span data-stu-id="06557-127">Phase 2: Create user accounts and access groups</span></span>

<span data-ttu-id="06557-128">使用中的说明[连接到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx)连接到您的全局管理员帐户从 Office 365 跟踪订阅：</span><span class="sxs-lookup"><span data-stu-id="06557-128">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to connect to your Office 365 trail subscription with your global administrator account from:</span></span>
  
- <span data-ttu-id="06557-129">你的计算机（对于轻量级的 Office 365 开发/测试环境）。</span><span class="sxs-lookup"><span data-stu-id="06557-129">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="06557-130">CLIENT1 虚拟机（对于企业 Office 365 开发/测试环境）。</span><span class="sxs-lookup"><span data-stu-id="06557-130">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="06557-131">若要创建新的访问组的 ProjectX 在线 SharePoint 工作组网站，请在 Windows Azure 活动目录模块用于 Windows PowerShell 提示符下运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="06557-131">To create the new access groups for the ProjectX SharePoint Online team site, run these commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
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
> <span data-ttu-id="06557-132">单击[此处](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1)为包含所有这篇文章中的 PowerShell 命令的文本文件。</span><span class="sxs-lookup"><span data-stu-id="06557-132">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) for a text file that contains all of the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="06557-133">填写组织名称（示例：contosotoycompany），你所在位置的两位字符的国家/地区代码，然后从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="06557-133">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="06557-134">从**新建 MsolUser**命令显示时，请注意生成的密码会导致设计器帐户并将其记录在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="06557-134">From the display of the **New-MsolUser** command, note the generated password for the Lead Designer account and record it in a safe location.</span></span>
  
<span data-ttu-id="06557-135">从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="06557-135">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="06557-136">从**新建 MsolUser**命令显示时，请注意生成的密码会导致研究人员帐户并将其记录在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="06557-136">From the display of the **New-MsolUser** command, note the generated password for the Lead Researcher account and record it in a safe location.</span></span>
  
<span data-ttu-id="06557-137">从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="06557-137">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="06557-138">从**新建 MsolUser**命令显示时，请注意开发副总裁帐户生成的密码并将其记录在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="06557-138">From the display of the **New-MsolUser** command, note the generated password for the Development VP account and record it in a safe location.</span></span>
  
<span data-ttu-id="06557-139">接下来，要到新的访问组中添加新帐户，这些 PowerShell 命令提示符处运行 Windows Azure 活动目录模块用于 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="06557-139">Next, to add the new accounts to the new access groups, run these PowerShell commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
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

<span data-ttu-id="06557-140">结果：</span><span class="sxs-lookup"><span data-stu-id="06557-140">Results:</span></span>
  
- <span data-ttu-id="06557-141">ProjectX 成员访问组包含会导致设计器和领导研究员用户帐户</span><span class="sxs-lookup"><span data-stu-id="06557-141">The ProjectX-Members access group contains the Lead Designer and Lead Researcher user accounts</span></span>
    
- <span data-ttu-id="06557-142">ProjectX 管理员访问组中包含您的订购试用期的全局管理员帐户</span><span class="sxs-lookup"><span data-stu-id="06557-142">The ProjectX-Admins access group contains the global administrator account for your trial subscription</span></span>
    
- <span data-ttu-id="06557-143">使用 ProjectX 查看器访问组包含开发副总裁用户帐户</span><span class="sxs-lookup"><span data-stu-id="06557-143">The ProjectX-Viewers access group contains the Development VP user account</span></span>
    
<span data-ttu-id="06557-144">图 1 显示的访问组，其成员资格。</span><span class="sxs-lookup"><span data-stu-id="06557-144">Figure 1 shows the access groups and their membership.</span></span>
  
<span data-ttu-id="06557-145">**图 1**</span><span class="sxs-lookup"><span data-stu-id="06557-145">**Figure 1**</span></span>

![独立 SharePoint Online 组网站的 Office 365 组及其成员资格](images/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a><span data-ttu-id="06557-147">阶段 3： 创建新的团队 ProjectX SharePoint Online 网站并将其隔离</span><span class="sxs-lookup"><span data-stu-id="06557-147">Phase 3: Create a new ProjectX SharePoint Online team site and isolate it</span></span>

<span data-ttu-id="06557-148">要为 ProjectX 创建 SharePoint Online 的工作组网站，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="06557-148">To create a SharePoint Online team site for ProjectX, do the following:</span></span>
  
1. <span data-ttu-id="06557-149">本地计算机 （轻量配置） 上使用浏览器或客户端 1 （模拟的企业配置），登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用您的全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="06557-149">Using a browser on either your local computer (lightweight configuration) or on CLIENT1 (simulated enterprise configuration), sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="06557-150">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="06557-150">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="06557-151">在您的浏览器新 SharePoint 选项卡上，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="06557-151">On the new SharePoint tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="06557-p105">在**团队站点名称**框中，键入**ProjectX**。在**隐私设置**，选择**专用的只有成员才能访问此网站**。</span><span class="sxs-lookup"><span data-stu-id="06557-p105">In **Team site name**, type **ProjectX**. In **Privacy settings**, select **Private - only members can access this site**.</span></span>
    
5. <span data-ttu-id="06557-154">在**团队站点的说明**中，键入**ProjectX 的 SharePoint 网站**，，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="06557-154">In **Team site description**, type **SharePoint site for ProjectX**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="06557-155">**谁您想要添加吗**？窗格中，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="06557-155">On the **Who do you want to add**? pane, click **Finish**.</span></span>
    
7. <span data-ttu-id="06557-156">您的浏览器工具栏中的新**ProjectX 主页**选项卡上单击设置图标，然后单击**网站权限**。</span><span class="sxs-lookup"><span data-stu-id="06557-156">On the new **ProjectX-Home** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
8. <span data-ttu-id="06557-157">在**网站权限**窗格中，单击**高级的权限设置**。</span><span class="sxs-lookup"><span data-stu-id="06557-157">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
9. <span data-ttu-id="06557-158">在新**权限： 项目 X**在您的浏览器选项卡上，单击**访问请求的设置**。</span><span class="sxs-lookup"><span data-stu-id="06557-158">In the new **Permissions: Project X** tab in your browser, click **Access Request Settings**.</span></span>
    
10. <span data-ttu-id="06557-159">在**访问请求设置**对话框中，清除**允许成员共享的网站和个别文件和文件夹**，并**允许访问请求**（以使所有三个复选框都被清除），然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="06557-159">In the **Access Requests Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow access requests** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
11. <span data-ttu-id="06557-160">单击列表中的**ProjectX 成员**。</span><span class="sxs-lookup"><span data-stu-id="06557-160">Click **ProjectX Members** in the list.</span></span>
    
12. <span data-ttu-id="06557-161">在**用户和用户组**页上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="06557-161">On the **People and Groups** page, click **New**.</span></span>
    
13. <span data-ttu-id="06557-162">在**共享**对话框中，键入**ProjectX 成员**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="06557-162">In the **Share** dialog box, type **ProjectX-Members**, select it, and then click **Share**.</span></span>
    
14. <span data-ttu-id="06557-163">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="06557-163">Click the back button on your browser.</span></span>
    
15. <span data-ttu-id="06557-164">单击列表中的**ProjectX 的所有者**。</span><span class="sxs-lookup"><span data-stu-id="06557-164">Click **ProjectX Owners** in the list.</span></span>
    
16. <span data-ttu-id="06557-165">在**用户和用户组**页上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="06557-165">On the **People and Groups** page, click **New**.</span></span>
    
17. <span data-ttu-id="06557-166">在**共享**对话框中，键入**ProjectX 管理员**，选择它，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="06557-166">In the **Share** dialog box, type **ProjectX-Admins**, select it, and then click **Share**.</span></span>
    
18. <span data-ttu-id="06557-167">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="06557-167">Click the back button on your browser.</span></span>
    
19. <span data-ttu-id="06557-168">单击列表中的**ProjectX 的访问者**。</span><span class="sxs-lookup"><span data-stu-id="06557-168">Click **ProjectX Visitors** in the list.</span></span>
    
20. <span data-ttu-id="06557-169">在**用户和用户组**页上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="06557-169">On the **People and Groups** page, click **New**.</span></span>
    
21. <span data-ttu-id="06557-170">在**共享**对话框中，类型**ProjectX 查看器**，选择它，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="06557-170">In the **Share** dialog box, type **ProjectX-Viewers**, select it, and then click **Share**.</span></span>
    
22. <span data-ttu-id="06557-171">关闭您的浏览器中的**用户和用户组**选项卡，单击在浏览器中， **ProjectX 主页**选项卡，然后关闭**网站权限**窗格。</span><span class="sxs-lookup"><span data-stu-id="06557-171">Close the **People and Groups** tab in your browser, click the **ProjectX-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="06557-172">下面介绍了权限配置结果：</span><span class="sxs-lookup"><span data-stu-id="06557-172">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="06557-173">ProjectX 成员 SharePoint 组包含仅 ProjectX 成员访问组 （其中包含只会导致设计器和领导研究员用户帐户） 和 ProjectX 组 （其中包含只有全局管理员用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="06557-173">The ProjectX Members SharePoint group contains only the ProjectX-Members access group (which contains only the Lead Designer and Lead Researcher user accounts) and the ProjectX group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="06557-174">ProjectX 的所有者 SharePoint 组包含仅 ProjectX 管理员访问组 （其中包含只有全局管理员用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="06557-174">The ProjectX Owners SharePoint group contains only the ProjectX-Admins access group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="06557-175">ProjectX 访问 SharePoint 组包含仅 ProjectX 查看器访问组 （其中包含开发副总裁用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="06557-175">The ProjectX Visitors SharePoint group contains only the ProjectX-Viewers access group (which contains only the Development VP user account).</span></span>
    
- <span data-ttu-id="06557-176">成员无法修改网站级权限（只有 ProjectX-Admins 组成员才能修改）。</span><span class="sxs-lookup"><span data-stu-id="06557-176">Members cannot modify site-level permissions (this can only be done by members of the ProjectX-Admins group).</span></span>
    
- <span data-ttu-id="06557-177">其他用户帐户无法访问网站及其资源，也无法请求访问网站。</span><span class="sxs-lookup"><span data-stu-id="06557-177">Other user accounts cannot access the site or its resources or request access to the site.</span></span>
    
<span data-ttu-id="06557-178">图 2 展示了 SharePoint 组及其成员身份。</span><span class="sxs-lookup"><span data-stu-id="06557-178">Figure 2 shows the SharePoint groups and their membership.</span></span>
  
<span data-ttu-id="06557-179">**图 2**</span><span class="sxs-lookup"><span data-stu-id="06557-179">**Figure 2**</span></span>

![独立 SharePoint Online 组网站的 SharePoint Online 组及其成员资格](images/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
<span data-ttu-id="06557-181">现在让我们来演示使用会导致设计器用户帐户的访问权限：</span><span class="sxs-lookup"><span data-stu-id="06557-181">Now let's demonstrate access using the Lead Designer user account:</span></span>
  
1. <span data-ttu-id="06557-182">关闭您的浏览器， **ProjectX 主页**选项卡，再单击在浏览器中的**Microsoft Office 家庭**。</span><span class="sxs-lookup"><span data-stu-id="06557-182">Close the **ProjectX-Home** tab in your browser, and then click the **Microsoft Office Home** tab in your browser.</span></span>
    
2. <span data-ttu-id="06557-183">单击您的全局管理员的名称，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="06557-183">Click the name of your global administrator, and then click **Sign out**.</span></span>
    
3. <span data-ttu-id="06557-184">登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用会导致设计器的帐户名和密码。</span><span class="sxs-lookup"><span data-stu-id="06557-184">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the Lead Designer account name and its password.</span></span>
    
4. <span data-ttu-id="06557-185">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="06557-185">In the list of tiles, click **SharePoint**.</span></span>
    
5. <span data-ttu-id="06557-p106">在您的浏览器的新**SharePoint**选项卡，请在搜索框中，键入**ProjectX**激活搜索，，然后单击**ProjectX**工作组站点。ProjectX 团队站点浏览器中，您会看到一个新的选项卡。</span><span class="sxs-lookup"><span data-stu-id="06557-p106">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box, activate the search, and then click the **ProjectX** team site. You should see a new tab in your browser for the ProjectX team site.</span></span>
    
6. <span data-ttu-id="06557-p107">单击设置图标。注意到没有为**站点权限**选项。这是正确的因为只有 ProjectX 管理员组的成员可以修改网站上的权限</span><span class="sxs-lookup"><span data-stu-id="06557-p107">Click the settings icon. Notice that there is no option for **Site Permissions**. This is correct because only the members of the ProjectX-Admins group can modify permissions on the site</span></span>
    
7. <span data-ttu-id="06557-191">打开选择的记事本或文本编辑器。</span><span class="sxs-lookup"><span data-stu-id="06557-191">Open Notepad or a text editor of your choice.</span></span>
    
8. <span data-ttu-id="06557-192">ProjectX 团队站点的 URL 复制并粘贴到记事本或文本编辑器中的新行。</span><span class="sxs-lookup"><span data-stu-id="06557-192">Copy the URL of the ProjectX team site and paste it on a new line in Notepad or your text editor.</span></span>
    
9. <span data-ttu-id="06557-193">在浏览器中新**ProjectX 主页**选项卡，单击**文档**。</span><span class="sxs-lookup"><span data-stu-id="06557-193">On the new **ProjectX-Home** tab in your browser, click **Documents**.</span></span>
    
10. <span data-ttu-id="06557-194">将 ProjectX 文档文件夹的 URL 复制并粘贴到记事本或文本编辑器中的新行上。</span><span class="sxs-lookup"><span data-stu-id="06557-194">Copy the URL of the ProjectX documents folder and paste it on a new line in Notepad or your text editor.</span></span>
    
11. <span data-ttu-id="06557-195">在浏览器中的新**ProjectX 文档**选项卡，单击**新建 > Word 文档**。</span><span class="sxs-lookup"><span data-stu-id="06557-195">On the new **ProjectX-Documents** tab in your browser, click **New > Word document**.</span></span>
    
12. <span data-ttu-id="06557-p108">**联机单词**页中键入一些文本，等待状态以指明**保存**，请单击浏览器上的后退按钮，然后刷新该页。您应该看到新**Document.docx**在**文档**文件夹中。</span><span class="sxs-lookup"><span data-stu-id="06557-p108">Type some text in the **Word Online** page, wait for the status to indicate **Saved**, click the back button on your browser, and then refresh the page. You should see a new **Document.docx** in the **Documents** folder.</span></span>
    
13. <span data-ttu-id="06557-198">对于**Document.docx**的文档，单击，然后单击**获取链接**。</span><span class="sxs-lookup"><span data-stu-id="06557-198">Click the ellipsis for the **Document.docx** document, and then click **Get a link**.</span></span>
    
14. <span data-ttu-id="06557-199">在**共享 Document.docx**对话框中复制的 URL 并将其粘贴在记事本或文本编辑器中，在新的一行，然后关闭**共享 Document.docx**对话框中。</span><span class="sxs-lookup"><span data-stu-id="06557-199">Copy the URL in the **Share 'Document.docx'** dialog box and paste it on a new line in Notepad or your text editor, and then close the **Share 'Document.docx'** dialog box.</span></span>
    
15. <span data-ttu-id="06557-200">关闭您的浏览器中的**ProjectX 文档**和**SharePoint**选项卡，然后单击**Microsoft Office 主页**选项卡。</span><span class="sxs-lookup"><span data-stu-id="06557-200">Close the **ProjectX-Documents** and **SharePoint** tabs in your browser, and then click the **Microsoft Office Home** tab.</span></span>
    
16. <span data-ttu-id="06557-201">**会导致设计器**的名称，请单击，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="06557-201">Click the **Lead Designer** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="06557-202">现在让我们来演示使用开发副总裁用户帐户的访问权限：</span><span class="sxs-lookup"><span data-stu-id="06557-202">Now let's demonstrate access using the Development VP user account:</span></span>
  
1. <span data-ttu-id="06557-203">登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用开发副总裁帐户名和密码。</span><span class="sxs-lookup"><span data-stu-id="06557-203">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the Development VP account name and its password.</span></span>
    
2. <span data-ttu-id="06557-204">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="06557-204">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="06557-p109">在您的浏览器的新**SharePoint**选项卡，请在搜索框中，键入**ProjectX**激活搜索，，然后单击**ProjectX**工作组站点。ProjectX 团队站点浏览器中，您会看到一个新的选项卡。</span><span class="sxs-lookup"><span data-stu-id="06557-p109">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box, activate the search, and then click the **ProjectX** team site. You should see a new tab in your browser for the ProjectX team site.</span></span>
    
4. <span data-ttu-id="06557-207">单击**文档**，然后单击**Document.docx**文件。</span><span class="sxs-lookup"><span data-stu-id="06557-207">Click **Documents**, and then click the **Document.docx** file.</span></span>
    
5. <span data-ttu-id="06557-p110">您的浏览器的**Document.docx**选项卡上，在尝试修改的文本。您应该看到一条消息指出**此文档是只读的。**这被预期行为，因为开发副总裁用户帐户仅具有查看该站点的权限。</span><span class="sxs-lookup"><span data-stu-id="06557-p110">In the **Document.docx** tab in your browser, try to modify the text. You should see a message stating **This document is read-only.** This is expected because the Development VP user account only has view permissions for the site.</span></span>
    
6. <span data-ttu-id="06557-211">关闭您的浏览器中的**Document.docx**、 **ProjectX 文档**和**SharePoint**选项卡。</span><span class="sxs-lookup"><span data-stu-id="06557-211">Close the **Document.docx**, **ProjectX-Documents**, and **SharePoint** tabs in your browser.</span></span>
    
7. <span data-ttu-id="06557-212">单击**Microsoft Office 主页**选项卡，单击**开发副总裁**的名称，然后单击**退出**。</span><span class="sxs-lookup"><span data-stu-id="06557-212">Click the **Microsoft Office Home** tab, click the **Development VP** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="06557-213">现在让我们证明没有权限的用户帐户的访问权限：</span><span class="sxs-lookup"><span data-stu-id="06557-213">Now let's demonstrate access with a user account that has no permissions:</span></span>
  
1. <span data-ttu-id="06557-214">登录到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 使用用户 3 帐户名和密码。</span><span class="sxs-lookup"><span data-stu-id="06557-214">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the User 3 account name and its password.</span></span>
    
2. <span data-ttu-id="06557-215">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="06557-215">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="06557-p111">在您的浏览器的新**SharePoint**选项卡，在搜索框中键入**ProjectX** ，然后激活搜索。您应该看到该消息**这里没有什么可以与您的搜索。**</span><span class="sxs-lookup"><span data-stu-id="06557-p111">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box and then activate the search. You should see the message **Nothing here matches your search.**</span></span>
    
4. <span data-ttu-id="06557-p112">从记事本或您的文本编辑器打开实例，将 ProjectX 网站的 URL 复制到浏览器的地址栏，然后按**Enter**。您应该看到**拒绝访问**页。</span><span class="sxs-lookup"><span data-stu-id="06557-p112">From the open instance of Notepad or your text editor, copy the URL for the ProjectX site into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
5. <span data-ttu-id="06557-p113">在记事本或文本编辑器中，将 ProjectX 文档文件夹的 URL 复制到浏览器的地址栏，然后按**Enter**。您应该看到**拒绝访问**页。</span><span class="sxs-lookup"><span data-stu-id="06557-p113">From Notepad or your text editor, copy the URL for the ProjectX Documents folder into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
6. <span data-ttu-id="06557-p114">在记事本或文本编辑器中，将 Documents.docx 文件的 URL 复制到浏览器的地址栏，然后按**Enter**。您应该看到**拒绝访问**页。</span><span class="sxs-lookup"><span data-stu-id="06557-p114">From Notepad or your text editor, copy the URL for the Documents.docx file into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
7. <span data-ttu-id="06557-224">关闭您的浏览器中的**SharePoint**选项卡，单击**Microsoft Office 主页**选项卡，单击**用户 3**名，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="06557-224">Close the **SharePoint** tab in your browser, click the **Microsoft Office Home** tab, click the **User 3** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="06557-225">独立的 SharePoint Online 网站现准备了更多的试验过程。</span><span class="sxs-lookup"><span data-stu-id="06557-225">Your isolated SharePoint Online site is now ready for your additional experimentation.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="06557-226">下一步</span><span class="sxs-lookup"><span data-stu-id="06557-226">Next Step</span></span>

<span data-ttu-id="06557-227">当您准备部署在生产环境中的独立的 SharePoint Online 工作组网站时，请参阅[设计独立的在线 SharePoint 工作组网站](design-an-isolated-sharepoint-online-team-site.md)中的分步设计考虑事项。</span><span class="sxs-lookup"><span data-stu-id="06557-227">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="06557-228">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06557-228">See Also</span></span>

[<span data-ttu-id="06557-229">SharePoint Online 的独立的团队站点</span><span class="sxs-lookup"><span data-stu-id="06557-229">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="06557-230">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="06557-230">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="06557-231">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="06557-231">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="06557-232">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="06557-232">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="06557-233">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="06557-233">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




