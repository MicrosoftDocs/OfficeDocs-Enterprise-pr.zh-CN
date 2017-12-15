---
title: "SharePoint Online Azure 的信息保护文件保护"
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "摘要： 应用 Azure 的信息保护，以保护高度机密的在线 SharePoint 工作组网站中的文件。"
ms.openlocfilehash: bc2c7dbbcc254270cf2c7db3d3eed98b3f7872f6
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="896f3-103">SharePoint Online Azure 的信息保护文件保护</span><span class="sxs-lookup"><span data-stu-id="896f3-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="896f3-104">**摘要：**应用 Azure 的信息保护，以保护高度机密的在线 SharePoint 工作组网站中的文件。</span><span class="sxs-lookup"><span data-stu-id="896f3-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="896f3-p101">使用本文中的步骤配置 Azure 信息保护提供加密和高度机密的 SharePoint Online 工作组站点中的文件的权限。即使从网站上下载，使用文件传输时加密和权限保护。关于高度机密的在线 SharePoint 工作组网站的详细信息，请参阅[安全 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)。</span><span class="sxs-lookup"><span data-stu-id="896f3-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="896f3-p102">当 Azure 信息保护加密应用于存储在 Office 365 中的文件时，该服务无法处理这些文件的内容。共同创作、 eDiscovery、 搜索、 Delve 和其他协作功能不起作用。数据丢失防护 (DLP) 策略只能处理的元数据 （包括 Office 365 的标签），但不是包括这些文件 （例如，信用卡号文件内） 的内容。</span><span class="sxs-lookup"><span data-stu-id="896f3-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="896f3-111">首先，使用中的说明[将 Azure RMS 激活 Office 365 管理中心](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)为您 Office 365 的订阅。</span><span class="sxs-lookup"><span data-stu-id="896f3-111">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="896f3-112">接下来，使用一个指定了作用域的新策略和子标签保护和高度机密 SharePoint Online 工作组站点的权限配置 Azure 的信息保护。</span><span class="sxs-lookup"><span data-stu-id="896f3-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="896f3-p103">Office 365 门户拥有安全管理员或公司管理员角色的帐户登录。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="896f3-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="896f3-115">在浏览器的单独的选项卡，请转到 Azure 门户网站 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="896f3-115">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="896f3-116">如果这是首次配置 Azure 信息保护，请参见以下[说明](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。</span><span class="sxs-lookup"><span data-stu-id="896f3-116">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="896f3-117">在列表窗格中，单击**更多服务**，键入**信息**，，然后单击**Azure 信息保护**。</span><span class="sxs-lookup"><span data-stu-id="896f3-117">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="896f3-118">**Azure 信息保护**刀片式服务器，，单击**范围策略 > 添加新策略 +**。</span><span class="sxs-lookup"><span data-stu-id="896f3-118">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="896f3-119">键入**策略的名称**和**描述**中的说明新策略的名称。</span><span class="sxs-lookup"><span data-stu-id="896f3-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="896f3-120">单击**选择哪些用户或组获取该策略 > 用户/用户组**，然后选择网站成员访问高度敏感联机 SharePoint 工作组网站用户组。</span><span class="sxs-lookup"><span data-stu-id="896f3-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="896f3-121">单击**选择 > 确定**。</span><span class="sxs-lookup"><span data-stu-id="896f3-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="896f3-122">**高度机密**的标签，请单击省略号 （...），然后单击**添加子标签**。</span><span class="sxs-lookup"><span data-stu-id="896f3-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="896f3-123">键入**名称**和说明中**说明**的标签的子标签的名称。</span><span class="sxs-lookup"><span data-stu-id="896f3-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="896f3-124">在**设置权限的文档和电子邮件包含此标签**，请单击**保护**。</span><span class="sxs-lookup"><span data-stu-id="896f3-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="896f3-125">在**保护**部分中，单击**Azure （云键）**。</span><span class="sxs-lookup"><span data-stu-id="896f3-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="896f3-126">在**保护**刀片式服务器下**保护设置**，, 单击**+ 添加权限**。</span><span class="sxs-lookup"><span data-stu-id="896f3-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="896f3-127">**添加权限**刀片式服务器，在**指定用户和组**，请单击**+ 浏览目录**。</span><span class="sxs-lookup"><span data-stu-id="896f3-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="896f3-128">在**AAD 的用户和组**窗格中，选择高度敏感 SharePoint Online 工作组站点，站点成员访问组，然后单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="896f3-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="896f3-129">在**选择权限从预设**清除**打印**、**复制和内容的提取**和**转发**复选框。</span><span class="sxs-lookup"><span data-stu-id="896f3-129">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="896f3-130">单击**确定**两次。</span><span class="sxs-lookup"><span data-stu-id="896f3-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="896f3-131">在**子标签**刀片式服务器，单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="896f3-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="896f3-132">关闭新的指定了作用域的策略刀片。</span><span class="sxs-lookup"><span data-stu-id="896f3-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="896f3-133">在**Azure 信息保护的指定了作用域策略**刀片式服务器，单击**发布**。</span><span class="sxs-lookup"><span data-stu-id="896f3-133">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
<span data-ttu-id="896f3-134">这是高度机密 SharePoint Online 工作组站点为您生成配置。</span><span class="sxs-lookup"><span data-stu-id="896f3-134">This is your resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![独立 SharePoint Online 团队网站的 Azure 信息保护标签。](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="896f3-136">现在您可以开始创建文档，并加以保护利用 Azure 的信息保护和新的标签。</span><span class="sxs-lookup"><span data-stu-id="896f3-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="896f3-p104">您必须在您的设备或基于 Windows 的计算机上[安装 Azure 信息保护客户端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)。您可以编写脚本和自动安装，或者用户可以手动安装客户端。请参阅以下资源：</span><span class="sxs-lookup"><span data-stu-id="896f3-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="896f3-140">客户端的 Azure 的信息保护</span><span class="sxs-lookup"><span data-stu-id="896f3-140">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="896f3-141">安装 Azure 信息保护客户端</span><span class="sxs-lookup"><span data-stu-id="896f3-141">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="896f3-142">下载页面的手动安装</span><span class="sxs-lookup"><span data-stu-id="896f3-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="896f3-p105">安装后，您的用户运行，然后登录某个 Office 应用程序 （如 Microsoft Word) 与他们 Office 365 的帐户。新的**信息保护**栏，用户可选择的新标签。请确保您的用户知道在线 SharePoint 工作组网站和其标签使用，来保护他们的高度机密文件。</span><span class="sxs-lookup"><span data-stu-id="896f3-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="896f3-146">如果您有多个高度敏感的 SharePoint Online 工作组网站，应创建多个范围的 Azure 的信息保护策略的子标签，上面的设置，与每个子标签设置为网站成员访问权限组的权限SharePoint Online 的特定工作组站点。</span><span class="sxs-lookup"><span data-stu-id="896f3-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="896f3-147">See Also</span><span class="sxs-lookup"><span data-stu-id="896f3-147">See Also</span></span>

[<span data-ttu-id="896f3-148">SharePoint Online 网站和文件保护</span><span class="sxs-lookup"><span data-stu-id="896f3-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="896f3-149">开发/测试环境中的安全 SharePoint Online 网站</span><span class="sxs-lookup"><span data-stu-id="896f3-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="896f3-150">为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南</span><span class="sxs-lookup"><span data-stu-id="896f3-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="896f3-151">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="896f3-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




