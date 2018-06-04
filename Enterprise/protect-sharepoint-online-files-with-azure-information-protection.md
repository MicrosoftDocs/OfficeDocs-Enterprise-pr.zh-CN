---
title: 使用 Azure 信息保护来保护 SharePoint Online 文件
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 摘要：应用 Azure 信息保护来保护高度机密的 SharePoint Online 团队网站中的文件。
ms.openlocfilehash: bab799a784cac579c92fb06ea17592d85fd59af2
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "19168496"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="47dd0-103">使用 Azure 信息保护来保护 SharePoint Online 文件</span><span class="sxs-lookup"><span data-stu-id="47dd0-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="47dd0-104">**摘要：** 应用 Azure 信息保护来保护高度机密的 SharePoint Online 团队网站中的文件。</span><span class="sxs-lookup"><span data-stu-id="47dd0-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="47dd0-p101">使用本文中的步骤配置 Azure 信息保护，以便为高度机密的 SharePoint Online 团队网站中的文件提供加密和权限。即使从网站下载了文件，加密和权限保护也会与文件一起传输。有关高度机密的 SharePoint Online 团队网站的详细信息，请参阅[保护 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)。</span><span class="sxs-lookup"><span data-stu-id="47dd0-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="47dd0-p102">将 Azure 信息保护加密应用于 Office 365 中存储的文件时，该服务无法处理这些文件的内容。 共同创作、电子数据展示、搜索、Delve 和其他协作功能将无法正常使用。 数据丢失防护 (DLP) 策略只适用于元数据（包括 Office 365 标签），但并不适用于这些文件的内容（如文件内的信用卡号）。</span><span class="sxs-lookup"><span data-stu-id="47dd0-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="47dd0-111">首先，请按照[使用 Office 365 管理中心激活 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) 中的说明进行操作，以获取 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="47dd0-111">First, follow the instructions in [Activate Azure RMS with the Office 365 admin center for your Office 365 subscription](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="47dd0-112">接下来，使用新作用域内的策略以及高度机密的 SharePoint Online 团队网站用于保护和权限的子标签来配置 Azure 信息保护。</span><span class="sxs-lookup"><span data-stu-id="47dd0-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions for your highly confidential SharePoint Online team site by following these steps:</span></span>
  
1. <span data-ttu-id="47dd0-p103">使用具有安全管理员或公司管理员角色的帐户登录到 Office 365 门户。有关帮助信息，请参阅[在何处登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="47dd0-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="47dd0-115">在浏览器的单独标签页中，转到 Azure 门户 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="47dd0-115">In a separate tab of your browser, go to the Azure portal (https://portal.azure.com).</span></span>
    
3. <span data-ttu-id="47dd0-116">如果是首次配置 Azure 信息保护，请参阅这些[说明](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。</span><span class="sxs-lookup"><span data-stu-id="47dd0-116">If this is the first time you are configuring Azure Information Protection, see [these instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="47dd0-117">在列表窗格中，单击“**更多服务**”，键入“**信息**”，然后单击“**Azure 信息保护**”。</span><span class="sxs-lookup"><span data-stu-id="47dd0-117">In the list pane, click **More services**, type **information**, and click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="47dd0-118">在“**Azure 信息保护**”边栏选项卡上，选择“**作用域内策略”>“+ 添加新策略**”。</span><span class="sxs-lookup"><span data-stu-id="47dd0-118">On the **Azure Information protection** blade, click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="47dd0-119">在“策略名称”中键入新策略的名称，并在“描述”中键入新策略的描述********。</span><span class="sxs-lookup"><span data-stu-id="47dd0-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="47dd0-120">单击“选择获取此策略的用户或组”>“用户/组”，然后选择高度敏感的 SharePoint Online 团队网站的网站成员访问组****。</span><span class="sxs-lookup"><span data-stu-id="47dd0-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="47dd0-121">单击“选择”>“确定”****。</span><span class="sxs-lookup"><span data-stu-id="47dd0-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="47dd0-122">对于“高度机密”标签，请单击省略号 (…)，然后单击“添加子标签”********。</span><span class="sxs-lookup"><span data-stu-id="47dd0-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="47dd0-123">在“名称”中键入子标签的名称，并在“描述”中键入标签的描述********。</span><span class="sxs-lookup"><span data-stu-id="47dd0-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="47dd0-124">在“为包含此标签的文档和电子邮件设置权限”中，单击“保护”********。</span><span class="sxs-lookup"><span data-stu-id="47dd0-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="47dd0-125">在“保护”部分中，单击“Azure (云密钥)”********。</span><span class="sxs-lookup"><span data-stu-id="47dd0-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="47dd0-126">在“保护”边栏选项卡中，在“保护设置”下，单击“+ 添加权限”************。</span><span class="sxs-lookup"><span data-stu-id="47dd0-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="47dd0-127">在“添加权限”**** 边栏选项卡的“指定用户和组”**** 下，单击“+ 浏览目录”****。</span><span class="sxs-lookup"><span data-stu-id="47dd0-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="47dd0-128">在“AAD 用户和组”**** 窗格中，选择高度敏感的 SharePoint Online 团队网站的网站成员访问组，然后单击“选择”****。</span><span class="sxs-lookup"><span data-stu-id="47dd0-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and click **Select**.</span></span>
    
16. <span data-ttu-id="47dd0-129">在“从预设中选择权限”**** 下，取消勾选“打印”****、“复制和提取内容”**** 和“转接”**** 复选框。</span><span class="sxs-lookup"><span data-stu-id="47dd0-129">Under Choose permissions from the preset, clear the Print, Copy and extract content, and Forward check boxes.</span></span>
    
17. <span data-ttu-id="47dd0-130">单击“确定”**** 两次。</span><span class="sxs-lookup"><span data-stu-id="47dd0-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="47dd0-131">在“子标签”边栏选项卡上，单击“保存”********。</span><span class="sxs-lookup"><span data-stu-id="47dd0-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="47dd0-132">关闭“新作用域内策略”边栏选项卡。</span><span class="sxs-lookup"><span data-stu-id="47dd0-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="47dd0-133">在“Azure 信息保护 - 作用域内策略”**** 边栏选项卡上，单击“发布”****。</span><span class="sxs-lookup"><span data-stu-id="47dd0-133">On the **Azure Information Protection – Scoped policies** blade, click **Publish**, and then click Yes.</span></span>
    
<span data-ttu-id="47dd0-134">下面是高度机密的 SharePoint Online 团队网站的配置结果。</span><span class="sxs-lookup"><span data-stu-id="47dd0-134">This is the resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![独立 SharePoint Online 团队网站的 Azure 信息保护标签。](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="47dd0-136">现在可以准备开始创建文档并使用 Azure 信息保护和新的标签来保护它们。</span><span class="sxs-lookup"><span data-stu-id="47dd0-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="47dd0-p104">你必须在设备或基于 Windows 的计算机上[安装 Azure 信息保护客户端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)。可以编写脚本，使安装自动化，也可手动安装客户端。请参阅以下资源：</span><span class="sxs-lookup"><span data-stu-id="47dd0-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually.</span></span>
  
- [<span data-ttu-id="47dd0-140">Azure 信息保护的客户端</span><span class="sxs-lookup"><span data-stu-id="47dd0-140">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="47dd0-141">安装 Azure 信息保护客户端</span><span class="sxs-lookup"><span data-stu-id="47dd0-141">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="47dd0-142">手动安装的下载页</span><span class="sxs-lookup"><span data-stu-id="47dd0-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="47dd0-p105">安装后，用户就可以运行 Office 应用程序（如 Microsoft Word），然后使用其 Office 365 帐户登录。新的“信息保护”**** 栏允许用户选择新标签。请确保你的用户知道 SharePoint Online 团队网站，以及要使用哪个标签来保护其高度机密的文件。</span><span class="sxs-lookup"><span data-stu-id="47dd0-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="47dd0-146">如果有多个高度敏感的 SharePoint Online 团队网站，应创建多个 Azure 信息保护作用域内策略以及多个包含上述设置的子标签，另外每个子标签的权限设置为特定 SharePoint Online 团队网站的网站成员访问组。</span><span class="sxs-lookup"><span data-stu-id="47dd0-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="47dd0-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47dd0-147">See Also</span></span>

[<span data-ttu-id="47dd0-148">保护 SharePoint Online 网站和文件</span><span class="sxs-lookup"><span data-stu-id="47dd0-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="47dd0-149">在开发/测试环境中保护 SharePoint Online 网站</span><span class="sxs-lookup"><span data-stu-id="47dd0-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="47dd0-150">Microsoft 针对政治宣传活动、非营利组织和其他敏捷性组织的安全指南</span><span class="sxs-lookup"><span data-stu-id="47dd0-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="47dd0-151">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="47dd0-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




