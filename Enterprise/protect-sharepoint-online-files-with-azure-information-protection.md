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
ms.openlocfilehash: 2c4776f5795a5a0b07be0f04b4872abadb4d31ca
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319283"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="e4ceb-103">使用 Azure 信息保护来保护 SharePoint Online 文件</span><span class="sxs-lookup"><span data-stu-id="e4ceb-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="e4ceb-104">**摘要：** 应用 Azure 信息保护来保护高度机密的 SharePoint Online 团队网站中的文件。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="e4ceb-p101">本文逐步介绍了如何将 Azure 信息保护配置为，加密文件和授予对文件的权限。可以将这些文件添加到配置了高度机密保护的 SharePoint 库。也可以直接从网站中打开文件，并使用 Azure 信息保护客户端添加加密。加密和权限保护与文件如影随形，即使从网站下载文件，也不例外。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files. These files can be added to a SharePoint library configured for highly confidential protection. Or, you can open a file directly from the site and use the Azure Information Protection client to add encryption. The encryption and permissions protection travels with a file even when it is downloaded from the site.</span></span> 

<span data-ttu-id="e4ceb-p102">为 SharePoint 网站及其中文件配置高度机密保护的大型解决方案采用这些步骤。有关详细信息，请参阅[保护 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-p102">These steps are part of a larger solution for configuring highly confidential protection for SharePoint sites and the files within these sites. For more information, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span> 

<span data-ttu-id="e4ceb-111">对 SharePoint Online 中的文件使用 Azure 信息保护不建议用于所有客户，但适用于部分文件需要这种保护级别的客户。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-111">Using Azure Information Protection for files in SharePoint Online is not recommended for all customers, but is an option for customers who need this level of protection for a subset of files.</span></span>

<span data-ttu-id="e4ceb-112">关于此解决方案，请务必注意以下几点：</span><span class="sxs-lookup"><span data-stu-id="e4ceb-112">Some important notes about this solution:</span></span>
- <span data-ttu-id="e4ceb-p103">将 Azure 信息保护加密应用于 Office 365 中存储的文件时，该服务无法处理这些文件的内容。 共同创作、电子数据展示、搜索、Delve 和其他协作功能将无法正常使用。 数据丢失防护 (DLP) 策略只适用于元数据（包括 Office 365 标签），但并不适用于这些文件的内容（如文件内的信用卡号）。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-p103">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
- <span data-ttu-id="e4ceb-p104">此解决方案要求，用户必须选择通过 Azure 信息保护应用保护的标签。如果需要自动加密并便于 SharePoint 能够将文件编入索引和检查文件，建议在 SharePoint Online 中使用信息权限管理 (IRM)。为 SharePoint 库配置 IRM 后，文件会在下载以供编辑时自动加密。SharePoint IRM 有可能会影响你决定的限制。有关详细信息，请参阅[在 SharePoint 管理中心内设置信息权限管理 (IRM)](https://support.office.com/zh-CN/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C)。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-p104">This solution requires a user to select a label that applies the protection from Azure Information Protection. If you require automatic encryption and the ability for SharePoint to index and inspect the files, consider using Information Rights Management (IRM) in SharePoint Online. When you configure a SharePoint library for IRM, files are automatically encrypted when they are downloaded for editing.  SharePoint IRM includes limitations that might influence your decision. For more information, see [Set up Information Rights Management (IRM) in SharePoint admin center](https://support.office.com/zh-CN/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).</span></span>

##<a name="admin-setup"></a><span data-ttu-id="e4ceb-121">管理员设置</span><span class="sxs-lookup"><span data-stu-id="e4ceb-121">Admin setup</span></span>
<span data-ttu-id="e4ceb-122">首先，对 Office 365 订阅按照[使用 Office 365 管理中心激活 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) 中的说明操作。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-122">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="e4ceb-123">接下来，使用新作用域内的策略以及高度机密的 SharePoint Online 团队网站用于保护和权限的子标签来配置 Azure 信息保护。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-123">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="e4ceb-p105">使用具有安全管理员或公司管理员角色的帐户登录到 Office 365 门户。有关帮助信息，请参阅[在何处登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-p105">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e4ceb-126">在浏览器的单独标签页中，转到 Azure 门户 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-126">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="e4ceb-127">如果是首次配置 Azure 信息保护，请参阅这些[说明](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-127">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="e4ceb-128">在列表窗格中，单击“**更多服务**”，键入“**信息**”，然后单击“**Azure 信息保护**”。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-128">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="e4ceb-129">在“**Azure 信息保护**”边栏选项卡上，选择“**作用域内策略”>“+ 添加新策略**”。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-129">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="e4ceb-130">在“策略名称”中键入新策略的名称，并在“描述”中键入新策略的描述********。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-130">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="e4ceb-131">单击“选择获取此策略的用户或组”>“用户/组”，然后选择高度敏感的 SharePoint Online 团队网站的网站成员访问组****。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-131">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="e4ceb-132">单击“选择”>“确定”****。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-132">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="e4ceb-133">对于“高度机密”标签，请单击省略号 (…)，然后单击“添加子标签”********。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-133">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="e4ceb-134">在“名称”中键入子标签的名称，并在“描述”中键入标签的描述********。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-134">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="e4ceb-135">在“为包含此标签的文档和电子邮件设置权限”中，单击“保护”********。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-135">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="e4ceb-136">在“保护”部分中，单击“Azure (云密钥)”********。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-136">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="e4ceb-137">在“保护”边栏选项卡中，在“保护设置”下，单击“+ 添加权限”************。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-137">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="e4ceb-138">在“添加权限”**** 边栏选项卡的“指定用户和组”**** 下，单击“+ 浏览目录”****。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-138">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="e4ceb-139">在“AAD 用户和组”**** 窗格中，选择高度敏感的 SharePoint Online 团队网站的网站成员访问组，然后单击“选择”****。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-139">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="e4ceb-140">在“从预设中选择权限”**** 下，取消勾选“打印”****、“复制和提取内容”**** 和“转接”**** 复选框。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-140">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="e4ceb-141">单击“确定”**** 两次。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-141">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="e4ceb-142">在“子标签”边栏选项卡上，单击“保存”********。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-142">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="e4ceb-143">关闭“新作用域内策略”边栏选项卡。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-143">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="e4ceb-144">在“Azure 信息保护 - 范围内策略”**** 边栏选项卡上，单击“发布”****。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-144">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
 
##<a name="client-setup"></a><span data-ttu-id="e4ceb-145">客户端设置</span><span class="sxs-lookup"><span data-stu-id="e4ceb-145">Client setup</span></span>
<span data-ttu-id="e4ceb-146">现在可以开始创建文档，并使用 Azure 信息保护和新标签来保护它们。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-146">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="e4ceb-p106">你必须在设备或基于 Windows 的计算机上[安装 Azure 信息保护客户端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)。可以编写脚本，使安装自动化，也可手动安装客户端。请参阅以下资源：</span><span class="sxs-lookup"><span data-stu-id="e4ceb-p106">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="e4ceb-150">Azure 信息保护的客户端</span><span class="sxs-lookup"><span data-stu-id="e4ceb-150">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="e4ceb-151">安装 Azure 信息保护客户端</span><span class="sxs-lookup"><span data-stu-id="e4ceb-151">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="e4ceb-152">手动安装的下载页</span><span class="sxs-lookup"><span data-stu-id="e4ceb-152">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="e4ceb-p107">安装后，用户就可以运行 Office 应用程序（如 Microsoft Word），然后使用其 Office 365 帐户登录。新的“信息保护”**** 栏允许用户选择新标签。请确保你的用户知道 SharePoint Online 团队网站，以及要使用哪个标签来保护其高度机密的文件。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-p107">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e4ceb-156">如果有多个高度敏感的 SharePoint Online 团队网站，应创建多个 Azure 信息保护作用域内策略以及多个包含上述设置的子标签，另外每个子标签的权限设置为特定 SharePoint Online 团队网站的网站成员访问组。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-156">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
##<a name="adding-permissions-for-external-users"></a><span data-ttu-id="e4ceb-157">为外部用户添加权限</span><span class="sxs-lookup"><span data-stu-id="e4ceb-157">Adding permissions for external users</span></span>
<span data-ttu-id="e4ceb-p108">可通过两种方式向外部用户授予对 Azure 信息保护已保护文件的访问权限。在这两种情况下，外部用户都必须拥有 Azure AD 帐户。如果外部用户不属于使用 Azure AD 的组织，可以使用下面的注册页以个人身份获得 Azure AD 帐户：[https://aka.ms/aip-signup](https://aka.ms/aip-signup)。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-p108">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>

 - <span data-ttu-id="e4ceb-p109">将外部用户添加到用于配置标签保护的 Azure AD 组。需要先以 B2B 用户身份在目录中添加此帐户。[Azure 权限管理缓存组成员资格](https://docs.microsoft.com/zh-CN/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection)可能需要几个小时才能完成。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-p109">Add external users to an Azure AD group that is used to configure protection for a label. You'll need to first add the account as a B2B user in your directory. It can take a couple of hours for [group memership caching by Azure Rights Management](https://docs.microsoft.com/zh-CN/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection).</span></span>  
 - <span data-ttu-id="e4ceb-p110">将外部用户直接添加到标签保护设置中。可以添加组织（例如 Fabrikam.com）中的所有用户、Azure AD 组（如组织内的财务组）或单个用户。例如，可以将监管机构的外部团队添加到标签保护设置中。</span><span class="sxs-lookup"><span data-stu-id="e4ceb-p110">Add external users directly to the label protection. You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4ceb-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4ceb-167">See Also</span></span>

[<span data-ttu-id="e4ceb-168">保护 SharePoint Online 网站和文件</span><span class="sxs-lookup"><span data-stu-id="e4ceb-168">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="e4ceb-169">在开发/测试环境中保护 SharePoint Online 网站</span><span class="sxs-lookup"><span data-stu-id="e4ceb-169">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="e4ceb-170">Microsoft 针对政治宣传活动、非营利组织和其他敏捷性组织的安全指南</span><span class="sxs-lookup"><span data-stu-id="e4ceb-170">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="e4ceb-171">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="e4ceb-171">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




