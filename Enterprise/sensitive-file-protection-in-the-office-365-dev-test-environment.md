---
title: Office 365 开发/测试环境中的敏感文件保护
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: '摘要: 配置和演示 Office 365 信息权限管理如何保护您的敏感文件, 即使这些文件发布到错误的 SharePoint Online 网站集也是如此。'
ms.openlocfilehash: a845742f7ec874d63269f5f380568b7bb59cfe0d
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070888"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="c11b2-103">Office 365 开发/测试环境中的敏感文件保护</span><span class="sxs-lookup"><span data-stu-id="c11b2-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="c11b2-104">**摘要:** 配置并演示 Office 365 信息权限管理如何保护您的敏感文件, 即使这些文件发布到错误的 SharePoint Online 网站集也是如此。</span><span class="sxs-lookup"><span data-stu-id="c11b2-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="c11b2-p101">Office 365 中的信息权限管理 (IRM) 是一系列保护从 SharePoint Online 库和列表下载的文档的功能。下载的文件经加密处理并且包含显示存储文件的 SharePoint Online 库的打开、复制、保存和打印权限。</span><span class="sxs-lookup"><span data-stu-id="c11b2-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="c11b2-107">使用本文中的说明进行操作，你可以启用和测试 Office 365 中的 IRM，以查看 Office 365 试用订阅中的文件是否包含潜在敏感信息。</span><span class="sxs-lookup"><span data-stu-id="c11b2-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="c11b2-108">单击[此处](http://aka.ms/catlgstack)可直观映射到 Office 365 测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="c11b2-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="c11b2-109">第 1 阶段：构建 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="c11b2-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="c11b2-110">如果只需要测试达到最低要求的轻型敏感文件保护，请按照 [Office 365 dev/test environment](office-365-dev-test-environment.md) 中第 2 阶段和第 3 阶段的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c11b2-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="c11b2-111">如果你想要测试模拟企业中的敏感文件保护，请按照 [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) 中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c11b2-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c11b2-112">测试敏感文件保护不需要模拟企业开发/测试环境, 其中包括连接到 Internet 的模拟 intranet 和 Active Directory 域服务 (AD DS) 林的目录同步。</span><span class="sxs-lookup"><span data-stu-id="c11b2-112">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="c11b2-113">它在此处作为一个选项提供，以便你可以测试敏感文件保护，并在代表典型组织的环境中对其进行试验。</span><span class="sxs-lookup"><span data-stu-id="c11b2-113">It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="c11b2-114">阶段 2：演示受权限保护的站点中的文档如何被泄漏</span><span class="sxs-lookup"><span data-stu-id="c11b2-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="c11b2-115">在此阶段，证明某人可以从受权限保护的站点下载文档，然后将其上载到具有完全开放权限的站点。</span><span class="sxs-lookup"><span data-stu-id="c11b2-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="c11b2-116">首先，你可以添加三个新的代表执行人员的用户帐户，并为他们分配 Office 365 E5 许可证。</span><span class="sxs-lookup"><span data-stu-id="c11b2-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="c11b2-117">使用[连接到 Office 365 powershell](https://technet.microsoft.com/library/dn975125.aspx)中的说明安装 powershell 模块 (如果需要), 并连接到你的新 Office 365 订阅 (如果需要):</span><span class="sxs-lookup"><span data-stu-id="c11b2-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="c11b2-118">你的计算机（对于轻量级的 Office 365 开发/测试环境）。</span><span class="sxs-lookup"><span data-stu-id="c11b2-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="c11b2-119">CLIENT1 虚拟机（对于模拟的企业 Office 365 开发/测试环境）。</span><span class="sxs-lookup"><span data-stu-id="c11b2-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="c11b2-120">在“**Windows PowerShell 凭据请求**”对话框中，键入 Office 365 试用订阅中的 Office 365 全局管理员名称（示例：jdoe@contosotoycompany.onmicrosoft.com）和密码。</span><span class="sxs-lookup"><span data-stu-id="c11b2-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="c11b2-121">填写组织名称（示例：contosotoycompany）以及你所在位置的两位字符的国家/地区代码，然后从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="c11b2-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="c11b2-122">在显示的 **New-MsolUser** 命令中，记下 CEO 帐户的生成密码并将其记录在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="c11b2-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="c11b2-123">从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="c11b2-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="c11b2-124">在显示的 **New-MsolUser** 命令中，记下 CFO 帐户的生成密码并将其记录在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="c11b2-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="c11b2-125">从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="c11b2-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="c11b2-126">在显示的 **New-MsolUser** 命令中，记下 COO 帐户的生成密码并将其记录在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="c11b2-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="c11b2-127">接下来，创建一个专用的执行人员组，并向其添加新的执行帐户。</span><span class="sxs-lookup"><span data-stu-id="c11b2-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="c11b2-128">在浏览器中, 转到 Office 门户, [http://admin.microsoft.com](http://admin.microsoft.com)并使用全局管理员帐户登录到你的 office 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="c11b2-128">In your browser, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="c11b2-129">如果使用的是轻型 Office 365 开发/测试环境，请打开 Internet Explorer 或浏览器的专用会话并从本地计算机登录。</span><span class="sxs-lookup"><span data-stu-id="c11b2-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="c11b2-130">如果你使用的是模拟的企业 Office 365 开发/测试环境，请使用 Azure 门户连接到 CLIENT1 虚拟机，然后从 CLIENT1 登录。</span><span class="sxs-lookup"><span data-stu-id="c11b2-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="c11b2-131">在“**Microsoft Office 主页**”选项卡上，单击“**管理 > 组 > 组**”，然后单击“**添加组**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="c11b2-132">在“**添加组**”中，选择“**Office 365 组**”组类型，在“**名称**”和“**组 ID**”中键入“**执行人员**”，为“**隐私**”选择“**专用**”，然后单击“**选择所有者**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="c11b2-133">在列表中，单击你的全局管理员帐户名。</span><span class="sxs-lookup"><span data-stu-id="c11b2-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="c11b2-134">单击“**添加**”，然后单击“**关闭**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="c11b2-135">在组列表中，单击“**执行人员**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="c11b2-136">单击“**编辑成员**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="c11b2-p103">单击“**添加成员**”。在成员列表中，选择下列用户帐户：</span><span class="sxs-lookup"><span data-stu-id="c11b2-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="c11b2-139">首席执行官</span><span class="sxs-lookup"><span data-stu-id="c11b2-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="c11b2-140">首席财务官</span><span class="sxs-lookup"><span data-stu-id="c11b2-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="c11b2-141">首席运营官</span><span class="sxs-lookup"><span data-stu-id="c11b2-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="c11b2-142">单击“**保存**”，然后单击“**关闭**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="c11b2-143">关闭“**Office 管理中心**”选项卡。</span><span class="sxs-lookup"><span data-stu-id="c11b2-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="c11b2-144">接下来，创建一个执行人员网站集，并仅允许执行人员组的成员对其进行访问。</span><span class="sxs-lookup"><span data-stu-id="c11b2-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="c11b2-145">在 " **Microsoft Office 主页**" 选项卡上, 单击 "**管理**" 磁贴。</span><span class="sxs-lookup"><span data-stu-id="c11b2-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="c11b2-146">在 " **Office 管理中心**" 选项卡上, 单击 "管理中心" " **> SharePoint**"。</span><span class="sxs-lookup"><span data-stu-id="c11b2-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="c11b2-147">在 " **SharePoint 管理中心**" 选项卡上, 单击 "**新建 > 专用网站集**"。</span><span class="sxs-lookup"><span data-stu-id="c11b2-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="c11b2-148">在 "新建网站集" 窗格中, 在\*\*\*\*"URL" 框中键入**行政主管**, 在 "**管理员**" 中指定全局管理员帐户的名称, 然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="c11b2-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="c11b2-149">等到创建新网站集。</span><span class="sxs-lookup"><span data-stu-id="c11b2-149">Wait until the new site collection has been created.</span></span> <span data-ttu-id="c11b2-150">完成后, 复制新的 "执行人员" 网站集的 URL, 并将其粘贴到浏览器的新选项卡中。</span><span class="sxs-lookup"><span data-stu-id="c11b2-150">When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="c11b2-151">在“**执行人员**”网站集的右上方，单击设置图标，然后单击“**共享**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="c11b2-152">在**共享 "高级管理人员"** 中, 单击 "**高级**"。</span><span class="sxs-lookup"><span data-stu-id="c11b2-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="c11b2-153">在 SharePoint 组列表中，单击“**执行人员成员**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="c11b2-154">在“人员和组”页中，单击“新建”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c11b2-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="c11b2-155">在 **"共享 ' 执行人员 '"** 中, 键入**主管**, 单击 "**主管**" 组, 然后单击 "**共享**"。</span><span class="sxs-lookup"><span data-stu-id="c11b2-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="c11b2-156">关闭 "**人员和组**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c11b2-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="c11b2-157">接下来，允许每个人访问销售网站集。</span><span class="sxs-lookup"><span data-stu-id="c11b2-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="c11b2-158">在 " **SharePoint 管理中心**" 选项卡上, 复制 "销售" 网站集的 URL, 并将其粘贴到浏览器的新选项卡中。</span><span class="sxs-lookup"><span data-stu-id="c11b2-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="c11b2-159">在右上方，单击“设置”图标，然后单击“**共享**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="c11b2-160">在 **"共享 ' 销售 ' 网站集 '"** 中, 单击 "**高级**"。</span><span class="sxs-lookup"><span data-stu-id="c11b2-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="c11b2-161">在 SharePoint 组列表中，单击“**销售网站集成员**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="c11b2-162">在“**人员和组**”页面上，单击“**新建**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="c11b2-163">在 **"共享" "销售网站集"** 中, 键入**everyone**, 单击 "**除外部用户之外的所有人**", 然后单击 "**共享**"。</span><span class="sxs-lookup"><span data-stu-id="c11b2-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="c11b2-164">关闭“**销售网站集**”和“**SharePoint**”选项卡。</span><span class="sxs-lookup"><span data-stu-id="c11b2-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="c11b2-165">接下来，使用执行人员帐户登录并在执行人员网站集中创建文档。</span><span class="sxs-lookup"><span data-stu-id="c11b2-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="c11b2-166">在“**Microsoft Office 主页**”选项卡上，单击右上方的用户图标，然后单击“**注销**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="c11b2-167">转到 [http://admin.microsoft.com](http://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="c11b2-167">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="c11b2-168">在“**Office 365 登录**”页面上，单击“**使用其他帐户**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="c11b2-169">键入 **CEO** 帐户名及其密码，然后单击“**登录**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="c11b2-170">在浏览器的新选项卡上, 键入 "执行人员" 网站集 ( **https://**\<组织 name>**sharepoint.com/sites/executives**) 的 URL。</span><span class="sxs-lookup"><span data-stu-id="c11b2-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="c11b2-171">单击 "**文档**", 单击 "**新建",** 然后单击 " **Word 文档**"。</span><span class="sxs-lookup"><span data-stu-id="c11b2-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="c11b2-172">单击“标题栏”并键入 **SensitiveData BeforeIRM**。</span><span class="sxs-lookup"><span data-stu-id="c11b2-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="c11b2-173">单击文档正文并键入**最新董事会会议的会议记录**，然后单击“**执行人员**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="c11b2-174"> 应该会在*\*文档*\*文件夹中看到 *\*SensitiveData BeforeIRM.docx*\*。</span><span class="sxs-lookup"><span data-stu-id="c11b2-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="c11b2-175">接下来，下载 SensitiveData BeforeIRM.docx 文档的本地副本，然后再意外地将其发布到销售网站集。</span><span class="sxs-lookup"><span data-stu-id="c11b2-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="c11b2-176">在您的本地计算机上, 创建一个新文件夹 (例如, C\\:\\tlg SensitiveDataTestFiles)。</span><span class="sxs-lookup"><span data-stu-id="c11b2-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="c11b2-177">在浏览器的“**文档**”选项卡上，选择 **SensitiveData BeforeIRM.docx** 文档，单击省略号，然后单击“**下载**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="c11b2-178">将 **SensitiveData BeforeIRM.docx** 文档存储在步骤 1 中创建的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="c11b2-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="c11b2-179">在浏览器的新选项卡上, 键入销售网站集的 URL ( **https://**\<组织 name>**sharepoint.com/sites/sales**)。</span><span class="sxs-lookup"><span data-stu-id="c11b2-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="c11b2-180">单击**销售网站集**的“**文档**”文件夹。</span><span class="sxs-lookup"><span data-stu-id="c11b2-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="c11b2-181">单击“**上载**”，指定步骤 1 中创建的文件夹中的 **SensitiveData BeforeIRM.docx** 文档，然后单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="c11b2-182">验证 **SensitiveData BeforeIRM.docx** 文档位于**文档**文件夹。</span><span class="sxs-lookup"><span data-stu-id="c11b2-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="c11b2-183">关闭“**销售**”和“**SharePoint**”选项卡。</span><span class="sxs-lookup"><span data-stu-id="c11b2-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="c11b2-184">接下来，以 User5 身份登录并尝试打开销售网站集中的 SensitiveData-BeforeIRM.docx 文档。</span><span class="sxs-lookup"><span data-stu-id="c11b2-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="c11b2-185">在“**Microsoft Office 主页**”选项卡上，单击右上方的用户图标，然后单击“**注销**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="c11b2-186">转到 [http://admin.microsoft.com](http://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="c11b2-186">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="c11b2-187">在“**Office 365 登录**”页面上，单击“**使用其他帐户**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="c11b2-188">键入 User 5 帐户名及其密码，然后单击“**登录**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="c11b2-189">在浏览器的新选项卡上, 键入销售网站集的 URL。</span><span class="sxs-lookup"><span data-stu-id="c11b2-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="c11b2-190">在**销售网站集**的**文档**文件夹中，单击“**SensitiveData BeforeIRM.docx**”文档。 </span><span class="sxs-lookup"><span data-stu-id="c11b2-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="c11b2-191">应该会看到其内容。</span><span class="sxs-lookup"><span data-stu-id="c11b2-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="c11b2-192">关闭“**文档**”和“**销售网站集**”选项卡。</span><span class="sxs-lookup"><span data-stu-id="c11b2-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="c11b2-193">通过在销售网站集上意外发布 SensitiveData BeforeIRM.docx 文档，CEO 可以绕过执行人员网站集的权限安全性。</span><span class="sxs-lookup"><span data-stu-id="c11b2-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="c11b2-194">若要为阶段 3 和 4 准备 Office 365，请为 SharePoint Online 启用 IRM。</span><span class="sxs-lookup"><span data-stu-id="c11b2-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="c11b2-195">在“**Microsoft Office 主页**”选项卡上，单击右上方的用户图标，然后单击“**注销**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="c11b2-196">转到 [http://admin.microsoft.com](http://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="c11b2-196">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="c11b2-197">在“**Office 365 登录**”页，单击全局管理员帐户名，键入其密码，然后单击“**登录**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="c11b2-198">在“**Microsoft Office 主页**”选项卡上，单击“**管理员 > 管理中心 > SharePoint**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="c11b2-199">在“**SharePoint 管理中心**”选项卡上，单击“**设置**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="c11b2-200">在页面上的 "**信息权限管理 (IRM)** " 部分中, 选择 "**使用您的配置中指定的 IRM 服务"**, 然后选择 "**刷新 IRM 设置**"。</span><span class="sxs-lookup"><span data-stu-id="c11b2-200">On the page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="c11b2-201">关闭“**SharePoint 管理中心**”选项卡。</span><span class="sxs-lookup"><span data-stu-id="c11b2-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="c11b2-202">第 3 阶段：将 SharePoint 信息权限管理与 Office 365 专用组配合使用</span><span class="sxs-lookup"><span data-stu-id="c11b2-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="c11b2-203">在此阶段，将 SharePoint 信息权限管理与 Office 365 专用组配合使用以保护对包含敏感信息的文档的访问，即使它在公开权限的站点上发布。</span><span class="sxs-lookup"><span data-stu-id="c11b2-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="c11b2-204">首先，可以为执行人员网站集文档库启用和配置 IRM。 </span><span class="sxs-lookup"><span data-stu-id="c11b2-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="c11b2-205">在浏览器的新选项卡上, 键入 "执行人员" 网站集的 URL。</span><span class="sxs-lookup"><span data-stu-id="c11b2-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="c11b2-206">单击“文档”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c11b2-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="c11b2-207">在右上方，单击设置图标，然后单击“**库设置**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="c11b2-208">在“**设置**”页的“**权限和管理**”下方，单击“**信息权限管理**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="c11b2-209">在“**信息权限管理设置**”页上：</span><span class="sxs-lookup"><span data-stu-id="c11b2-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="c11b2-210">选择“**限制此库文档的下载权限**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="c11b2-211">对于**创建权限策略标题**，键入**执行人员**。</span><span class="sxs-lookup"><span data-stu-id="c11b2-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="c11b2-212">对于**添加权限策略说明**，键入**针对执行人员的 IRM**。</span><span class="sxs-lookup"><span data-stu-id="c11b2-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="c11b2-213">单击“**显示选项**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="c11b2-214">在“**设置其他 IRM 库设置**”下方，选择“**不允许用户上载不支持 IRM 的文档**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="c11b2-215">在“**配置文档访问权限**”下方，选择“**允许查看者打印**”和“**允许查看者写入下载文档副本**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="c11b2-216">在 "**设置组保护和凭据间隔**" 下, 选择 "**允许组保护"。默认组**, 然后键入**高级管理人员**。</span><span class="sxs-lookup"><span data-stu-id="c11b2-216">Under **Set group protection and credentials interval**, select **Allow group protection. Default group**, and then type **Executives**.</span></span>
    
10. <span data-ttu-id="c11b2-217">单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-217">Click **OK**.</span></span>
    
<span data-ttu-id="c11b2-218">接下来，以 CEO 身份进行操作，将新文档上载到执行人员文档文件夹，下载它，再意外地将其上载到销售文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="c11b2-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="c11b2-219">打开存储 **SensitiveData BeforeIRM.docx** 文档的本地文件夹。</span><span class="sxs-lookup"><span data-stu-id="c11b2-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="c11b2-220">	右键单击“*\*SensitiveData BeforeIRM.docx*\*”，然后单击“*\*复制*\*”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="c11b2-221">在该文件夹内右键单击，然后单击“**粘贴**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="c11b2-222">将新的**SensitiveData-BeforeIRM-复制的 .docx**文件重命名为**sensitivedata afterirm.docx**。</span><span class="sxs-lookup"><span data-stu-id="c11b2-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="c11b2-223">在浏览器的“**Microsoft Office 主页**”选项卡上，单击右上方的用户图标，然后单击“**注销**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="c11b2-224">转到 [http://admin.microsoft.com](http://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="c11b2-224">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
7. <span data-ttu-id="c11b2-225">在“**Office 365 登录**”页，单击 CEO 帐户名，键入其密码，然后单击“**登录**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="c11b2-226">在浏览器的新选项卡上, 键入 "执行人员" 网站集的 URL。</span><span class="sxs-lookup"><span data-stu-id="c11b2-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="c11b2-227">在“**文档**”页上，单击“**上载**”，指定本地文件夹中的 **SensitiveData AfterIRM.docx** 文档，然后单击“**打开**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="c11b2-228">选择“**文档**”页上新的 **SensitiveData AfterIRM.docx** 文档，单击菜单栏中的省略号 (…)，然后单击“**下载**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="c11b2-229">出现提示时，保存本地文件夹中的 **SensitiveData AfterIRM.docx** 文档，并覆盖原始版本。</span><span class="sxs-lookup"><span data-stu-id="c11b2-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="c11b2-230">关闭“**文档**”页的选项卡。</span><span class="sxs-lookup"><span data-stu-id="c11b2-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="c11b2-231">在浏览器的新选项卡上, 键入销售网站集的 URL。</span><span class="sxs-lookup"><span data-stu-id="c11b2-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="c11b2-232">单击“文档”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c11b2-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="c11b2-233">在“**文档**”页上，单击“**上载**”，指定本地文件夹中的 **SensitiveData AfterIRM.docx** 文档，然后单击“**打开**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="c11b2-234">关闭“**销售网站集**”和“**SharePoint**”选项卡。</span><span class="sxs-lookup"><span data-stu-id="c11b2-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="c11b2-235">接下来，以普通用户身份进行操作，尝试访问销售文档文件夹中的 **SensitiveData AfterIRM.docx** 文档。</span><span class="sxs-lookup"><span data-stu-id="c11b2-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="c11b2-236">在浏览器的“**Microsoft Office 主页**”选项卡上，单击右上方的用户图标，然后单击“**注销**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="c11b2-237">转到 [http://admin.microsoft.com](http://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="c11b2-237">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="c11b2-238">在 " **Office 365 登录**" 页上, 单击 User5 帐户名, 键入其密码, 然后单击 "**登录**"。</span><span class="sxs-lookup"><span data-stu-id="c11b2-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="c11b2-239">在浏览器的新选项卡上, 键入销售网站集的 URL。</span><span class="sxs-lookup"><span data-stu-id="c11b2-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="c11b2-240">单击“文档”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c11b2-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="c11b2-241">在“**文档**”页上，打开 **SensitiveData AfterIRM.docx** 文档。 </span><span class="sxs-lookup"><span data-stu-id="c11b2-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="c11b2-242">应该会看到一条消息显示“很抱歉，Word Online 无法打开此文档，因为它受信息权限管理 (IRM) 的保护”。 </span><span class="sxs-lookup"><span data-stu-id="c11b2-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="c11b2-p105">单击“**在 Word 中编辑**”。如果要打开文件，系统会提示你。单击“**是**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="c11b2-p106">将提示你登录。键入帐户名称 User5，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="c11b2-p107">将提示你提供密码。键入 User 5 帐户密码，然后单击“**登录**”。 </span><span class="sxs-lookup"><span data-stu-id="c11b2-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="c11b2-250">应该会看到一条消息显示如下：“你没有允许打开此文档的凭据”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="c11b2-251">单击“**否**”。</span><span class="sxs-lookup"><span data-stu-id="c11b2-251">Click **No**.</span></span>
    
<span data-ttu-id="c11b2-p108">查看 IRM 保护的另一个方法是浏览本地文件夹中的文件。**SensitiveData AfterIRM.docx** 应远大于 **SensitiveData BeforeIRM.docx** 文件。**SensitiveData AfterIRM.docx** 文件经加密处理，并添加有 IRM 保护信息。</span><span class="sxs-lookup"><span data-stu-id="c11b2-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c11b2-255">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c11b2-255">See Also</span></span>

[<span data-ttu-id="c11b2-256">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="c11b2-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c11b2-257">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="c11b2-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="c11b2-258">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="c11b2-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="c11b2-259">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="c11b2-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


