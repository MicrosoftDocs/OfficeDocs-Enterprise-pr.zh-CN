---
title: 使用 Azure AD 进行 SharePoint Server 身份验证
ms.author: tracyp
author: MSFTTracyP
ms.reviewer: kirke, josephd, kirks
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: ''
description: '摘要: 了解如何绕过 Azure 访问控制服务并使用 SAML 1.1 对 SharePoint Server 用户使用 Azure Active Directory 进行身份验证。'
ms.openlocfilehash: c2c9f33aa5e095a8b7fdde08e80cb1a61e88f3eb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070788"
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a><span data-ttu-id="0b993-103">使用 Azure AD 进行 SharePoint Server 身份验证</span><span class="sxs-lookup"><span data-stu-id="0b993-103">Using Azure AD for SharePoint Server Authentication</span></span>

 <span data-ttu-id="0b993-104">**摘要:** 了解如何使用 Azure Active Directory 对 SharePoint Server 2016 用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="0b993-104">**Summary:** Learn how to authenticate your SharePoint Server 2016 users with Azure Active Directory.</span></span> 

<blockquote>
<p><span data-ttu-id="0b993-105">本文引用与 Azure Active Directory 图形交互的代码示例。</span><span class="sxs-lookup"><span data-stu-id="0b993-105">This article refers to code samples for interacting with Azure Active Directory Graph.</span></span> <span data-ttu-id="0b993-106">你可以在[此处](https://github.com/kaevans/spsaml11/tree/master/scripts)下载代码示例。</span><span class="sxs-lookup"><span data-stu-id="0b993-106">You can download the code samples [here](https://github.com/kaevans/spsaml11/tree/master/scripts).</span></span></p>
</blockquote>

<span data-ttu-id="0b993-107">SharePoint Server 2016 提供了使用基于声明的身份验证对用户进行身份验证的能力, 通过使用您信任但其他人管理的不同标识提供程序对用户进行身份验证, 可以轻松地管理用户。</span><span class="sxs-lookup"><span data-stu-id="0b993-107">SharePoint Server 2016 provides the ability to authenticate users using claims-based authentication, making it easy to manage your users by authenticating them with different identity providers that you trust but someone else manages.</span></span> <span data-ttu-id="0b993-108">例如, 您可以使用户能够使用 Azure Active Directory (Azure AD) 进行身份验证, 而不是通过 Active Directory 域服务 (AD DS) 管理用户身份验证。</span><span class="sxs-lookup"><span data-stu-id="0b993-108">For example, instead of managing user authentication through Active Directory Domain Services (AD DS), you could enable users to authenticate using Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="0b993-109">这将为仅限云的用户使用其用户名中的 onmicrosoft.com 后缀、与本地目录同步的用户和其他目录中的受邀来宾用户启用身份验证。</span><span class="sxs-lookup"><span data-stu-id="0b993-109">This enables authentication for cloud-only users with the onmicrosoft.com suffix in their username, users synchronized with an on-premises directory, and invited guest users from other directories.</span></span> <span data-ttu-id="0b993-110">它还使您能够利用 Azure AD 功能, 如多因素身份验证和高级报告功能。</span><span class="sxs-lookup"><span data-stu-id="0b993-110">It also enables you to take advantage of Azure AD features such as multi-factor authentication and advanced reporting capabilities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b993-111">本文中所述的解决方案也可用于 SharePoint Server 2013;但请记住, SharePoint Server 2013 即将结束主流支持。</span><span class="sxs-lookup"><span data-stu-id="0b993-111">The solution described in this article can also be used with SharePoint Server 2013; however, keep in mind that SharePoint Server 2013 is nearing the end of mainstream support.</span></span> <span data-ttu-id="0b993-112">有关详细信息, 请参阅适用[于 SharePoint 2013 的](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx) [Microsoft 生命周期策略](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013)和更新的产品服务策略。</span><span class="sxs-lookup"><span data-stu-id="0b993-112">For more information, see [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) and [Updated Product Servicing Policy for SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).</span></span>

<span data-ttu-id="0b993-113">本文介绍如何使用 Azure AD (而不是本地 AD DS) 对用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="0b993-113">This article explains how you can use Azure AD instead of your on-premises AD DS to authenticate your users.</span></span> <span data-ttu-id="0b993-114">在此配置中, Azure AD 成为 SharePoint Server 2016 的受信任标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-114">In this configuration, Azure AD becomes a trusted identity provider for SharePoint Server 2016.</span></span> <span data-ttu-id="0b993-115">此配置将添加独立于 SharePoint Server 2016 安装本身所使用的 AD DS 身份验证的用户身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="0b993-115">This configuration adds a user authentication method that is separate from the AD DS authentication used by the SharePoint Server 2016 installation itself.</span></span> <span data-ttu-id="0b993-116">要从本文中受益，您应该熟悉 WS-Federation。</span><span class="sxs-lookup"><span data-stu-id="0b993-116">To benefit from this article, you should be familiar with WS-Federation.</span></span> <span data-ttu-id="0b993-117">有关详细信息，请参阅[了解 WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)。</span><span class="sxs-lookup"><span data-stu-id="0b993-117">For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span> <span data-ttu-id="0b993-118">有关使用 Azure Active Directory 集成 SharePoint 本地的详细信息, 请参阅[专用教程](https://docs.microsoft.com/azure/active-directory/saas-apps/sharepoint-on-premises-tutorial)。</span><span class="sxs-lookup"><span data-stu-id="0b993-118">For detailed information about integration of SharePoint on-premises with Azure Active Directory, see the [dedicated tutorial](https://docs.microsoft.com/azure/active-directory/saas-apps/sharepoint-on-premises-tutorial).</span></span>

![使用 Azure AD 进行 SharePoint 身份验证](media/SAML11/fig1-architecture.png)

<span data-ttu-id="0b993-120">之前, 此配置需要在云或承载 Active Directory 联合身份验证服务 (AD FS) 的环境中使用联合身份验证服务 (如 Azure 访问控制服务 (AD FS), 以将令牌从 SAML 2.0 转换为 SAML 1.1。</span><span class="sxs-lookup"><span data-stu-id="0b993-120">Previously, this configuration would have required a federation service such as Azure Access Control Service (ACS) in the cloud or an environment that hosts Active Directory Federation Services (AD FS) to transform tokens from SAML 2.0 to SAML 1.1.</span></span> <span data-ttu-id="0b993-121">此转换不再是必需的, 因为 Azure AD 现在启用了 "颁发 SAML 1.1 令牌"。</span><span class="sxs-lookup"><span data-stu-id="0b993-121">This transformation is no longer required as Azure AD now enables issuing SAML 1.1 tokens.</span></span> <span data-ttu-id="0b993-122">上图显示了此配置中的 SharePoint 2016 用户对身份验证的工作原理, 演示了如何对中间项执行此转换不再要求。</span><span class="sxs-lookup"><span data-stu-id="0b993-122">The diagram above shows how authentication works for SharePoint 2016 users in this configuration, demonstrating that there is no longer a requirement for an intermediary to perform this transformation.</span></span>

> [!NOTE]
> <span data-ttu-id="0b993-123">此配置适用于 SharePoint 服务器场是在 Azure 虚拟机中托管, 还是在本地托管。</span><span class="sxs-lookup"><span data-stu-id="0b993-123">This configuration works whether the SharePoint farm is hosted in Azure virtual machines or on-premises.</span></span> <span data-ttu-id="0b993-124">它不需要打开其他防火墙端口, 而是确保用户可以从其浏览器访问 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="0b993-124">It does not require opening additional firewall ports other than ensuring users can access Azure Active Directory from their browser.</span></span>

<span data-ttu-id="0b993-125">有关 SharePoint 2016 辅助功能的信息, 请参阅[Sharepoint Server 2016 中的辅助功能准则](https://go.microsoft.com/fwlink/p/?LinkId=393123)。</span><span class="sxs-lookup"><span data-stu-id="0b993-125">For information about SharePoint 2016 accessibility, see [Accessibility Guidelines in SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>

## <a name="configuration-overview"></a><span data-ttu-id="0b993-126">配置概述</span><span class="sxs-lookup"><span data-stu-id="0b993-126">Configuration overview</span></span>

<span data-ttu-id="0b993-127">按照以下常规步骤, 将您的环境设置为使用 Azure AD 作为 SharePoint Server 2016 标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-127">Follow these general steps to set up your environment to use Azure AD as a SharePoint Server 2016 identity provider.</span></span>

1. <span data-ttu-id="0b993-128">创建新的 Azure AD 目录或使用现有目录。</span><span class="sxs-lookup"><span data-stu-id="0b993-128">Create a new Azure AD directory or use your existing directory.</span></span>
2. <span data-ttu-id="0b993-129">确保要使用 Azure AD 进行保护的 web 应用程序的区域配置为使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="0b993-129">Ensure the zone for the web application that you want to secure with Azure AD is configured to use SSL.</span></span>
3. <span data-ttu-id="0b993-130">在 Azure AD 中创建新的企业应用程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-130">Create a new enterprise application in Azure AD.</span></span>
4. <span data-ttu-id="0b993-131">在 SharePoint Server 2016 中配置新的受信任标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-131">Configure a new trusted identity provider in SharePoint Server 2016.</span></span>
5. <span data-ttu-id="0b993-132">设置 web 应用程序的权限。</span><span class="sxs-lookup"><span data-stu-id="0b993-132">Set the permissions for the web application.</span></span>
6. <span data-ttu-id="0b993-133">在 Azure AD 中添加 SAML 1.1 令牌颁发策略。</span><span class="sxs-lookup"><span data-stu-id="0b993-133">Add a SAML 1.1 token issuance policy in Azure AD.</span></span>
7. <span data-ttu-id="0b993-134">验证新的提供程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-134">Verify the new provider.</span></span>

<span data-ttu-id="0b993-135">以下各节介绍如何执行这些任务。</span><span class="sxs-lookup"><span data-stu-id="0b993-135">The following sections describe how to perform these tasks.</span></span>

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a><span data-ttu-id="0b993-136">步骤 1: 创建新的 Azure AD 目录或使用现有目录</span><span class="sxs-lookup"><span data-stu-id="0b993-136">Step 1: Create a new Azure AD directory or use your existing directory</span></span>

<span data-ttu-id="0b993-137">在 Azure 门户 ([https://portal.azure.com](https://portal.azure.com)) 中, 创建一个新目录。</span><span class="sxs-lookup"><span data-stu-id="0b993-137">In the Azure Portal ([https://portal.azure.com](https://portal.azure.com)), create a new directory.</span></span> <span data-ttu-id="0b993-138">提供组织名称、初始域名以及国家或地区。</span><span class="sxs-lookup"><span data-stu-id="0b993-138">Provide the organization name, initial domain name, and the country or region.</span></span>

![创建目录](media/SAML11/fig2-createdirectory.png) 

 <span data-ttu-id="0b993-140">如果您已有一个目录 (如用于 Microsoft Office 365 的目录) 或 Microsoft Azure 订阅, 则可以改为使用该目录。</span><span class="sxs-lookup"><span data-stu-id="0b993-140">If you already have a directory such as the one used for Microsoft Office 365 or your Microsoft Azure subscription, you can use that directory instead.</span></span> <span data-ttu-id="0b993-141">您必须具有在目录中注册应用程序的权限。</span><span class="sxs-lookup"><span data-stu-id="0b993-141">You must have permissions to register applications in the directory.</span></span>

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a><span data-ttu-id="0b993-142">步骤 2: 确保要使用 Azure AD 保护的 web 应用程序的区域配置为使用 SSL</span><span class="sxs-lookup"><span data-stu-id="0b993-142">Step 2: Ensure the zone for the web application that you want to secure with Azure AD is configured to use SSL</span></span>

<span data-ttu-id="0b993-143">本文是使用在[Azure 中运行高可用性 SharePoint Server 2016 场](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)中的参考体系结构编写的。</span><span class="sxs-lookup"><span data-stu-id="0b993-143">This article was written using the reference architecture in [Run a high availability SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint).</span></span> <span data-ttu-id="0b993-144">本文附带的脚本 (用于部署[本文](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)中所述的解决方案) 创建了不使用 SSL 的网站。</span><span class="sxs-lookup"><span data-stu-id="0b993-144">The article’s accompanying scripts used to deploy the solution described in [this article](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) create a site that does not use SSL.</span></span>  

<span data-ttu-id="0b993-145">使用 SAML 要求将应用程序配置为使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="0b993-145">Using SAML requires the application be configured to use SSL.</span></span> <span data-ttu-id="0b993-146">如果您的 SharePoint web 应用程序未配置为使用 SSL, 请使用以下步骤创建新的自签名证书, 以配置用于 SSL 的 web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-146">If your SharePoint web application is not configured to use SSL, use the following steps to create a new self-signed certificate to configure the web application for SSL.</span></span> <span data-ttu-id="0b993-147">此配置仅适用于实验室环境, 不用于生产。</span><span class="sxs-lookup"><span data-stu-id="0b993-147">This configuration is only meant for a lab environment and is not intended for production.</span></span> <span data-ttu-id="0b993-148">生产环境应使用已签名的证书。</span><span class="sxs-lookup"><span data-stu-id="0b993-148">Production environments should use a signed certificate.</span></span>

1. <span data-ttu-id="0b993-149">转到 "**管理中心** > **应用程序管理** > "**管理 web 应用程序**, 并选择需要扩展的 web 应用程序以使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="0b993-149">Go to **Central Administration** > **Application Management** > **Manage Web Applications**, and choose the web application that needs to be extended to use SSL.</span></span> <span data-ttu-id="0b993-150">选择 web 应用程序, 然后单击 "**扩展功能区**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="0b993-150">Select the web application and click the **Extend ribbon** button.</span></span> <span data-ttu-id="0b993-151">扩展 web 应用程序以使用相同的 URL, 但使用带端口443的 SSL。</span><span class="sxs-lookup"><span data-stu-id="0b993-151">Extend the web application to use the same URL but use SSL with port 443.</span></span><br/><span data-ttu-id="0b993-152">![将 web 应用程序扩展到另一个 IIS 网站](media/SAML11/fig3-extendwebapptoiis.png)</span><span class="sxs-lookup"><span data-stu-id="0b993-152">![Extending the web app to another IIS site](media/SAML11/fig3-extendwebapptoiis.png)</span></span><br/>
2. <span data-ttu-id="0b993-153">在 IIS 管理器 中，双击"服务器证书"。</span><span class="sxs-lookup"><span data-stu-id="0b993-153">In IIS Manager, double-click **Server Certificates**.</span></span>
3. <span data-ttu-id="0b993-154">在"操作"窗格中，单击"创建自签名证书"。</span><span class="sxs-lookup"><span data-stu-id="0b993-154">In the **Actions** pane, click **Create Self-Signed Certificate**.</span></span> <span data-ttu-id="0b993-155">在 "指定证书的友好名称" 框中键入证书的友好名称, 然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="0b993-155">Type a friendly name for the certificate in the Specify a friendly name for the certificate box, and then click **OK**.</span></span>
4. <span data-ttu-id="0b993-156">从 "**编辑网站绑定**" 对话框中, 确保主机名与友好名称相同, 如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="0b993-156">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following image.</span></span><br/><span data-ttu-id="0b993-157">![在 IIS 中编辑网站绑定](media/SAML11/fig4-editsitebinding.png)</span><span class="sxs-lookup"><span data-stu-id="0b993-157">![Editing site binding in IIS](media/SAML11/fig4-editsitebinding.png)</span></span><br/>

<span data-ttu-id="0b993-158">SharePoint 场中的每台 web 前端服务器都需要在 IIS 中为网站绑定配置证书。</span><span class="sxs-lookup"><span data-stu-id="0b993-158">Each of the web front end servers in the SharePoint farm will require configuring the certificate for the site binding in IIS.</span></span>


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a><span data-ttu-id="0b993-159">步骤 3: 在 Azure AD 中创建新的企业应用程序</span><span class="sxs-lookup"><span data-stu-id="0b993-159">Step 3: Create a new enterprise application in Azure AD</span></span>

1. <span data-ttu-id="0b993-160">在 Azure 门户 ([https://portal.azure.com](https://portal.azure.com)) 中, 打开 azure AD 目录。</span><span class="sxs-lookup"><span data-stu-id="0b993-160">In the Azure Portal ([https://portal.azure.com](https://portal.azure.com)), open your Azure AD directory.</span></span> <span data-ttu-id="0b993-161">单击 "**企业应用程序**", 然后单击 "**新建应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-161">Click **Enterprise Applications**, then click **New application**.</span></span> <span data-ttu-id="0b993-162">选择 "**非库应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-162">Choose **Non-gallery application**.</span></span> <span data-ttu-id="0b993-163">提供一个名称, 如*SHAREPOINT SAML 集成*, 然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-163">Provide a name such as *SharePoint SAML Integration* and click **Add**.</span></span><br/><span data-ttu-id="0b993-164">![添加新的非库应用程序](media/SAML11/fig5-addnongalleryapp.png)</span><span class="sxs-lookup"><span data-stu-id="0b993-164">![Adding a new non-gallery application](media/SAML11/fig5-addnongalleryapp.png)</span></span><br/>
2. <span data-ttu-id="0b993-165">单击导航窗格中的 "单一登录" 链接以配置应用程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-165">Click the Single sign-on link in the navigation pane to configure the application.</span></span> <span data-ttu-id="0b993-166">将**单点登录模式**下拉列表更改为**基于 saml 的登录**, 以显示应用程序的 SAML 配置属性。</span><span class="sxs-lookup"><span data-stu-id="0b993-166">Change the **Single Sign-on Mode** dropdown to **SAML-based Sign-on** to reveal the SAML configuration properties for the application.</span></span> <span data-ttu-id="0b993-167">使用以下属性进行配置:</span><span class="sxs-lookup"><span data-stu-id="0b993-167">Configure with the following properties:</span></span><br/>
    - <span data-ttu-id="0b993-168">标识号`urn:sharepoint:portal.contoso.local`</span><span class="sxs-lookup"><span data-stu-id="0b993-168">Identifier: `urn:sharepoint:portal.contoso.local`</span></span>
    - <span data-ttu-id="0b993-169">回复 URL:`https://portal.contoso.local/_trust/default.aspx`</span><span class="sxs-lookup"><span data-stu-id="0b993-169">Reply URL: `https://portal.contoso.local/_trust/default.aspx`</span></span>
    - <span data-ttu-id="0b993-170">登录 URL:`https://portal.contoso.local/_trust/default.aspx`</span><span class="sxs-lookup"><span data-stu-id="0b993-170">Sign-on URL: `https://portal.contoso.local/_trust/default.aspx`</span></span>
    - <span data-ttu-id="0b993-171">用户标识符:`user.userprincipalname`</span><span class="sxs-lookup"><span data-stu-id="0b993-171">User Identifier: `user.userprincipalname`</span></span><br/>
    - <span data-ttu-id="0b993-172">注意: 请记住通过将*门户*替换为要保护的 SharePoint 网站的 url 来更改 url。</span><span class="sxs-lookup"><span data-stu-id="0b993-172">Note: Remember to change the URLs by replacing *portal.contoso.local* with the URL of the SharePoint site you want to secure.</span></span><br/>
3. <span data-ttu-id="0b993-173">设置表 (类似于下面的表 1), 其中包含以下行:</span><span class="sxs-lookup"><span data-stu-id="0b993-173">Set up a table (similar to Table 1 below) that includes the following rows:</span></span><br/> 
    - <span data-ttu-id="0b993-174">Realm</span><span class="sxs-lookup"><span data-stu-id="0b993-174">Realm</span></span>
    - <span data-ttu-id="0b993-175">SAML 签名证书文件的完整路径</span><span class="sxs-lookup"><span data-stu-id="0b993-175">Full path to SAML signing certificate file</span></span>
    - <span data-ttu-id="0b993-176">SAML 单一登录服务 URL (将 */saml2*替换为 */wsfed*)</span><span class="sxs-lookup"><span data-stu-id="0b993-176">SAML Single Sign-On service URL (replacing */saml2* with */wsfed*)</span></span>
    - <span data-ttu-id="0b993-177">Application 对象 ID。</span><span class="sxs-lookup"><span data-stu-id="0b993-177">Application Object ID.</span></span> <br/>
<span data-ttu-id="0b993-178">将 "*标识符*" 值复制到 "*领域*" 属性中的表中 (请参阅下面的表1。)</span><span class="sxs-lookup"><span data-stu-id="0b993-178">Copy the *Identifier* value into the *Realm* property into a table  (See Table 1 below.)</span></span>
4. <span data-ttu-id="0b993-179">保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="0b993-179">Save your changes.</span></span>
5. <span data-ttu-id="0b993-180">单击 "**配置 (应用名称)** " 链接以访问 "配置" 登录页。</span><span class="sxs-lookup"><span data-stu-id="0b993-180">Click the **Configure (app name)** link to access the Configure sign-on page.</span></span><br/><span data-ttu-id="0b993-181">![配置单一登录页](media/SAML11/fig7-configssopage.png)</span><span class="sxs-lookup"><span data-stu-id="0b993-181">![Configuring a single-sign on page](media/SAML11/fig7-configssopage.png)</span></span><br/> 
    -  <span data-ttu-id="0b993-182">单击**Saml 签名证书-Raw**链接以将 Saml 签名证书下载为扩展名为 .cer 的文件。</span><span class="sxs-lookup"><span data-stu-id="0b993-182">Click the **SAML Signing Certificate - Raw** link to download the SAML Signing Certificate as a file with the .cer extension.</span></span> <span data-ttu-id="0b993-183">将下载的文件的完整路径复制并粘贴到您的表中。</span><span class="sxs-lookup"><span data-stu-id="0b993-183">Copy and paste the full path to the downloaded file into your table.</span></span>
    - <span data-ttu-id="0b993-184">将 SAML 单一登录服务 URL 链接复制并粘贴到中, 将 URL 的 */saml2*部分替换为 */wsfed*。</span><span class="sxs-lookup"><span data-stu-id="0b993-184">Copy and paste the SAML Single Sign-On Service URL link into your, replacing the */saml2* portion of the URL with */wsfed*.</span></span><br/>
6.  <span data-ttu-id="0b993-185">导航到应用程序的 "**属性**" 窗格。</span><span class="sxs-lookup"><span data-stu-id="0b993-185">Navigate to the **Properties** pane for the application.</span></span> <span data-ttu-id="0b993-186">将 "对象 ID" 值复制并粘贴到您在步骤3中设置的表中。</span><span class="sxs-lookup"><span data-stu-id="0b993-186">Copy and paste the Object ID value into the table you set up in Step 3.</span></span><br/><span data-ttu-id="0b993-187">![应用程序的 "属性" 窗格](media/SAML11/fig8-propertiespane.png)</span><span class="sxs-lookup"><span data-stu-id="0b993-187">![Properties pane for the application](media/SAML11/fig8-propertiespane.png)</span></span><br/>
7. <span data-ttu-id="0b993-188">使用您捕获的值, 确保您在步骤3中设置的表类似于下面的表1。</span><span class="sxs-lookup"><span data-stu-id="0b993-188">Using the values you captured, make sure the table you set up in Step 3 resembles Table 1 below.</span></span>


| <span data-ttu-id="0b993-189">表 1: 捕获的值</span><span class="sxs-lookup"><span data-stu-id="0b993-189">Table 1: Values captured</span></span>  |  |
|---------|---------|
|<span data-ttu-id="0b993-190">Realm</span><span class="sxs-lookup"><span data-stu-id="0b993-190">Realm</span></span> | `urn:sharepoint:portal.contoso.local` |
|<span data-ttu-id="0b993-191">SAML 签名证书文件的完整路径</span><span class="sxs-lookup"><span data-stu-id="0b993-191">Full path to SAML signing certificate file</span></span> | `C:/temp/SharePoint SAML Integration.cer`  |
|<span data-ttu-id="0b993-192">SAML 单一登录服务 URL (将/saml2 替换为/wsfed)</span><span class="sxs-lookup"><span data-stu-id="0b993-192">SAML single sign-on service URL (replace /saml2 with /wsfed)</span></span> | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|<span data-ttu-id="0b993-193">Application 对象 ID</span><span class="sxs-lookup"><span data-stu-id="0b993-193">Application Object ID</span></span> | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> <span data-ttu-id="0b993-194">将 URL 中的 */saml2*值替换为 */wsfed*。</span><span class="sxs-lookup"><span data-stu-id="0b993-194">Replace the */saml2* value in the URL with */wsfed*.</span></span> <span data-ttu-id="0b993-195">*/Saml2*终结点将处理 SAML 2.0 令牌。</span><span class="sxs-lookup"><span data-stu-id="0b993-195">The */saml2* endpoint will process SAML 2.0 tokens.</span></span> <span data-ttu-id="0b993-196">*/Wsfed*终结点启用对 saml 1.1 令牌的处理, 这是 SHAREPOINT 2016 SAML 联合所必需的。</span><span class="sxs-lookup"><span data-stu-id="0b993-196">The */wsfed* endpoint enables processing SAML 1.1 tokens and is required for SharePoint 2016 SAML federation.</span></span>

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a><span data-ttu-id="0b993-197">步骤 4: 在 SharePoint Server 2016 中配置新的受信任标识提供程序</span><span class="sxs-lookup"><span data-stu-id="0b993-197">Step 4: Configure a new trusted identity provider in SharePoint Server 2016</span></span>

<span data-ttu-id="0b993-198">登录到 SharePoint Server 2016 服务器并打开 SharePoint 2016 命令行管理程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-198">Sign into the SharePoint Server 2016 server and open the SharePoint 2016 Management Shell.</span></span> <span data-ttu-id="0b993-199">在表1中填写 $realm、$wsfedurl 和 $filepath 的值, 然后运行以下命令来配置新的受信任标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-199">Fill in the values of $realm, $wsfedurl, and $filepath from Table 1 and run the following commands to configure a new trusted identity provider.</span></span>

> [!TIP]
> <span data-ttu-id="0b993-200">如果你不熟悉使用 PowerShell, 或者想详细了解 PowerShell 的工作方式, 请参阅[SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="0b993-200">If you're new to using PowerShell or want to learn more about how PowerShell works, see [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps).</span></span> 

```
$realm = "<Realm from Table 1>"
$wsfedurl="<SAML single sign-on service URL from Table 1>"
$filepath="<Full path to SAML signing certificate file from Table 1>"
$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filepath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
$map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" -IncomingClaimTypeDisplayName "name" -LocalClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
$map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
$map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
$ap = New-SPTrustedIdentityTokenIssuer -Name "AzureAD" -Description "SharePoint secured by Azure AD" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl $wsfedurl -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name"
```

<span data-ttu-id="0b993-201">接下来, 按照以下步骤为您的应用程序启用受信任的标识提供程序:</span><span class="sxs-lookup"><span data-stu-id="0b993-201">Next, follow these steps to enable the trusted identity provider for your application:</span></span>
1. <span data-ttu-id="0b993-202">在管理中心中, 导航到 "**管理 Web 应用程序**", 然后选择要使用 Azure AD 进行保护的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-202">In Central Administration, navigate to **Manage Web Application** and select the web application that you wish to secure with Azure AD.</span></span> 
2. <span data-ttu-id="0b993-203">在功能区中, 单击 "**身份验证提供程序**", 然后选择要使用的区域。</span><span class="sxs-lookup"><span data-stu-id="0b993-203">In the ribbon, click **Authentication Providers** and choose the zone that you wish to use.</span></span>
3. <span data-ttu-id="0b993-204">选择 "**受信任的身份提供程序**", 然后选择刚刚注册的名为*AzureAD*的标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-204">Select **Trusted Identity provider** and select the identify provider you just registered named *AzureAD*.</span></span>  
4. <span data-ttu-id="0b993-205">在 "登录页 URL" 设置中, 选择 "**自定义登录页**" 并提供值 "/_trust/"。</span><span class="sxs-lookup"><span data-stu-id="0b993-205">On the sign-in page URL setting, select **Custom sign in page** and provide the value "/_trust/".</span></span> 
5. <span data-ttu-id="0b993-206">单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0b993-206">Click **OK**.</span></span>

![配置身份验证提供程序](media/SAML11/fig10-configauthprovider.png)

> [!IMPORTANT]
> <span data-ttu-id="0b993-208">务必遵循所有步骤, 包括将自定义登录页设置为 "/_trust/", 如图所示。</span><span class="sxs-lookup"><span data-stu-id="0b993-208">It is important to follow all steps, including setting the custom sign in page to "/_trust/" as shown.</span></span> <span data-ttu-id="0b993-209">除非遵循所有步骤, 否则配置将无法正常运行。</span><span class="sxs-lookup"><span data-stu-id="0b993-209">The configuration will not work correctly unless all steps are followed.</span></span>

## <a name="step-5-set-the-permissions"></a><span data-ttu-id="0b993-210">步骤 5: 设置权限</span><span class="sxs-lookup"><span data-stu-id="0b993-210">Step 5: Set the permissions</span></span>

<span data-ttu-id="0b993-211">必须向要登录到 Azure AD 和 access SharePoint 的用户授予对应用程序的访问权限。</span><span class="sxs-lookup"><span data-stu-id="0b993-211">The users who will log into Azure AD and access SharePoint must be granted access to the application.</span></span> 

1. <span data-ttu-id="0b993-212">在 Azure 门户中, 打开 Azure AD 目录。</span><span class="sxs-lookup"><span data-stu-id="0b993-212">In the Azure Portal, open the Azure AD directory.</span></span> <span data-ttu-id="0b993-213">单击 "**企业应用程序**", 然后单击 "**所有应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-213">Click **Enterprise Applications**, then click **All applications**.</span></span> <span data-ttu-id="0b993-214">单击先前创建的应用程序 (SharePoint SAML 集成)。</span><span class="sxs-lookup"><span data-stu-id="0b993-214">Click the application that you created previously (SharePoint SAML Integration).</span></span>
2. <span data-ttu-id="0b993-215">单击 "**用户和组**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-215">Click **Users and Groups**.</span></span> 
3. <span data-ttu-id="0b993-216">单击 "**添加用户**" 以添加将有权使用 Azure AD 登录到 SharePoint 的用户或组。</span><span class="sxs-lookup"><span data-stu-id="0b993-216">Click **Add user** to add a user or group who will have permissions to log into SharePoint using Azure AD.</span></span>
4. <span data-ttu-id="0b993-217">选择用户或组, 然后单击 "**分配**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-217">Select the user or group then click **Assign**.</span></span>
 
<span data-ttu-id="0b993-218">用户已在 Azure AD 中授予权限, 但还必须在 SharePoint 中授予权限。</span><span class="sxs-lookup"><span data-stu-id="0b993-218">The user has been granted permission in Azure AD, but also must be granted permission in SharePoint.</span></span> <span data-ttu-id="0b993-219">执行下列步骤，设置访问 Web 应用程序的权限。</span><span class="sxs-lookup"><span data-stu-id="0b993-219">Use the following steps to set the permissions to access the web application.</span></span>

1. <span data-ttu-id="0b993-220">在管理中心中，单击“应用程序管理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0b993-220">In Central Administration, click **Application Management**.</span></span>
2. <span data-ttu-id="0b993-221">在"应用程序管理"页上的"Web 应用程序"部分，单击"管理 Web 应用程序"。</span><span class="sxs-lookup"><span data-stu-id="0b993-221">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
3. <span data-ttu-id="0b993-222">单击适当的 Web 应用程序，然后单击"用户策略"。</span><span class="sxs-lookup"><span data-stu-id="0b993-222">Click the appropriate web application, and then click **User Policy**.</span></span>
4. <span data-ttu-id="0b993-223">在 "Web 应用程序的策略" 中, 单击 "**添加用户**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-223">In Policy for Web Application, click **Add Users**.</span></span><br/><span data-ttu-id="0b993-224">![按名称声明搜索用户](media/SAML11/fig11-searchbynameclaim.png)</span><span class="sxs-lookup"><span data-stu-id="0b993-224">![Searching for a user by their name claim](media/SAML11/fig11-searchbynameclaim.png)</span></span><br/>
5. <span data-ttu-id="0b993-225">在"添加用户" 对话框中，单击"区域"中的适当区域，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="0b993-225">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
6. <span data-ttu-id="0b993-226">在 " **Web 应用程序的策略**" 对话框的 "**选择用户**" 部分, 单击 "**浏览**" 图标。</span><span class="sxs-lookup"><span data-stu-id="0b993-226">In the **Policy for Web Application** dialog box, in the **Choose Users** section, click the **Browse** icon.</span></span>
7. <span data-ttu-id="0b993-227">在 "**查找**" textbox 中, 在目录中键入用户的登录名, 然后单击 "**搜索**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-227">In the **Find** textbox, type the sign-in name for a user in your directory and click **Search**.</span></span> <br/><span data-ttu-id="0b993-228">示例: *demouser@blueskyabove.onmicrosoft.com*。</span><span class="sxs-lookup"><span data-stu-id="0b993-228">Example: *demouser@blueskyabove.onmicrosoft.com*.</span></span>
8. <span data-ttu-id="0b993-229">在列表视图中的 "AzureAD" 标题下, 选择 "名称" 属性并单击 "**添加**", 然后单击 **"确定"** 以关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="0b993-229">Under the AzureAD heading in the list view, select the name property and click **Add** then click **OK** to close the dialog.</span></span>
9. <span data-ttu-id="0b993-230">在 "权限" 中, 单击 "**完全控制**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-230">In Permissions, click **Full Control**.</span></span><br/><span data-ttu-id="0b993-231">![为声明用户授予 "完全控制" 权限](media/SAML11/fig12-grantfullcontrol.png)</span><span class="sxs-lookup"><span data-stu-id="0b993-231">![Granting full control to a claims user](media/SAML11/fig12-grantfullcontrol.png)</span></span><br/>
10. <span data-ttu-id="0b993-232">单击"完成"，然后单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="0b993-232">Click **Finish**, and then click **OK**.</span></span>

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a><span data-ttu-id="0b993-233">步骤 6: 在 Azure AD 中添加 SAML 1.1 令牌颁发策略</span><span class="sxs-lookup"><span data-stu-id="0b993-233">Step 6: Add a SAML 1.1 token issuance policy in Azure AD</span></span>

<span data-ttu-id="0b993-234">在门户中创建 Azure AD 应用程序时, 它将默认使用 SAML 2.0。</span><span class="sxs-lookup"><span data-stu-id="0b993-234">When the Azure AD application is created in the portal, it defaults to using SAML 2.0.</span></span> <span data-ttu-id="0b993-235">SharePoint Server 2016 需要 SAML 1.1 令牌格式。</span><span class="sxs-lookup"><span data-stu-id="0b993-235">SharePoint Server 2016 requires the SAML 1.1 token format.</span></span> <span data-ttu-id="0b993-236">下面的脚本将删除默认的 SAML 2.0 策略, 并添加新策略以颁发 SAML 1.1 令牌。</span><span class="sxs-lookup"><span data-stu-id="0b993-236">The following script will remove the default SAML 2.0 policy and add a new policy to issue SAML 1.1 tokens.</span></span> 

> <span data-ttu-id="0b993-237">此代码要求下载[演示与 Azure Active Directory Graph 交互](https://github.com/kaevans/spsaml11/tree/master/scripts)的附带示例。</span><span class="sxs-lookup"><span data-stu-id="0b993-237">This code requires downloading the accompanying [samples demonstrating interacting with Azure Active Directory Graph](https://github.com/kaevans/spsaml11/tree/master/scripts).</span></span> <span data-ttu-id="0b993-238">如果将脚本作为 ZIP 文件从 GitHub 下载到 Windows 桌面, 请确保取消阻止`MSGraphTokenLifetimePolicy.psm1`脚本模块文件和`Initialize.ps1`脚本文件 (右键单击 "属性", 选择 "取消阻止", 然后单击 "确定")。</span><span class="sxs-lookup"><span data-stu-id="0b993-238">If you download the scripts as a ZIP file from GitHub to a Windows desktop, make sure to unblock the `MSGraphTokenLifetimePolicy.psm1` script module file and the `Initialize.ps1` script file (right-click Properties, choose Unblock, click OK).</span></span> 
<span data-ttu-id="0b993-239">![取消阻止下载的文件](media/SAML11/fig17-unblock.png)</span><span class="sxs-lookup"><span data-stu-id="0b993-239">![Unblocking downloaded files](media/SAML11/fig17-unblock.png)</span></span>

<span data-ttu-id="0b993-240">下载示例脚本后, 请使用以下代码创建一个新的 PowerShell 脚本, 将占位符替换为本地计算机上下载`Initialize.ps1`的文件路径。</span><span class="sxs-lookup"><span data-stu-id="0b993-240">Once the sample script is downloaded, create a new PowerShell script using the following code, replacing the placeholder with the file path of the downloaded `Initialize.ps1` on your local machine.</span></span> <span data-ttu-id="0b993-241">将应用程序对象 ID 占位符替换为您在表1中输入的 application 对象 ID。</span><span class="sxs-lookup"><span data-stu-id="0b993-241">Replace the application object ID placeholder with the application object ID that you entered in Table 1.</span></span> <span data-ttu-id="0b993-242">创建后, 执行 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="0b993-242">Once created, execute the PowerShell script.</span></span> 

```
function AssignSaml11PolicyToAppPrincipal
{
    Param(
        [Parameter(Mandatory=$true)]
        [string]$pathToInitializeScriptFile, 
        [Parameter(Mandatory=$true)]
        [string]$appObjectid
    )

    $folder = Split-Path $pathToInitializeScriptFile
    Push-Location $folder

    #Loads the dependent ADAL module used to acquire tokens
    Import-Module $pathToInitializeScriptFile 

    #Gets the existing token issuance policy
    $existingTokenIssuancePolicy = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $appObjectid | ?{$_.type -EQ "TokenIssuancePolicy"} 
    Write-Host "The following TokenIssuancePolicy policies are assigned to the service principal." -ForegroundColor Green
    Write-Host $existingTokenIssuancePolicy -ForegroundColor White
    $policyId = $existingTokenIssuancePolicy.objectId

    #Removes existing token issuance policy
    Write-Host "Only a single policy can be assigned to the service principal. Removing the existing policy with ID $policyId" -ForegroundColor Green
    Remove-PolicyFromServicePrincipal -policyId $policyId -servicePrincipalId $appObjectid

    #Creates a new token issuance policy and assigns to the service principal
    Write-Host "Adding the new SAML 1.1 TokenIssuancePolicy" -ForegroundColor Green
    $policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
    Write-Host "Assigning the new SAML 1.1 TokenIssuancePolicy $policy.objectId to the service principal $appObjectid" -ForegroundColor Green
    Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $appObjectid
    Pop-Location
}

#Only edit the following two variables
$pathToInitializeScriptFile = "<file path of Initialize.ps1>"
$appObjectid = "<Application Object ID from Table 1>"

AssignSaml11PolicyToAppPrincipal $pathToInitializeScriptFile $appObjectid
```
> [!IMPORTANT]
> <span data-ttu-id="0b993-243">PowerShell 脚本未签名, 可能会提示您设置执行策略。</span><span class="sxs-lookup"><span data-stu-id="0b993-243">The PowerShell scripts are not signed and you may be prompted to set the execution policy.</span></span> <span data-ttu-id="0b993-244">有关执行策略的详细信息, 请参阅[关于执行策略](http://go.microsoft.com/fwlink/?LinkID=135170)。</span><span class="sxs-lookup"><span data-stu-id="0b993-244">For more information on execution policies, see [About Execution Policies](http://go.microsoft.com/fwlink/?LinkID=135170).</span></span> <span data-ttu-id="0b993-245">此外, 您可能需要打开提升的命令提示符, 才能成功执行示例脚本中包含的命令。</span><span class="sxs-lookup"><span data-stu-id="0b993-245">Additionally, you may need to open an elevated command prompt to successfully execute the commands contained in the sample scripts.</span></span>

<span data-ttu-id="0b993-246">这些示例 PowerShell 命令是有关如何对 Graph API 执行查询的示例。</span><span class="sxs-lookup"><span data-stu-id="0b993-246">These sample PowerShell commands are examples of how to execute queries against the Graph API.</span></span> <span data-ttu-id="0b993-247">有关 Azure AD 令牌颁发策略的更多详细信息, 请参阅[针对策略的操作的 GRAPH API 参考](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy)。</span><span class="sxs-lookup"><span data-stu-id="0b993-247">For more details on Token Issuance Policies with Azure AD, see the [Graph API reference for operations on policy](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy).</span></span>

## <a name="step-7-verify-the-new-provider"></a><span data-ttu-id="0b993-248">步骤 7: 验证新提供程序</span><span class="sxs-lookup"><span data-stu-id="0b993-248">Step 7: Verify the new provider</span></span>

<span data-ttu-id="0b993-249">打开浏览器, 使其指向您在前面步骤中配置的 web 应用程序的 URL。</span><span class="sxs-lookup"><span data-stu-id="0b993-249">Open a browser to the URL of the web application that you configured in the previous steps.</span></span> <span data-ttu-id="0b993-250">你将重定向到 "注册到 Azure AD"。</span><span class="sxs-lookup"><span data-stu-id="0b993-250">You are redirected to sign into Azure AD.</span></span>

![登录到为联合身份验证配置的 Azure AD](media/SAML11/fig13-examplesignin.png)

<span data-ttu-id="0b993-252">系统会询问您是否要保持登录。</span><span class="sxs-lookup"><span data-stu-id="0b993-252">You are asked if you want to stay signed in.</span></span>

![是否保持登录状态？](media/SAML11/fig14-staysignedin.png)

<span data-ttu-id="0b993-254">最后, 您可以从 Azure Active Directory 租户访问以用户身份登录的网站。</span><span class="sxs-lookup"><span data-stu-id="0b993-254">Finally, you can access the site logged in as a user from your Azure Active Directory tenant.</span></span>

![登录到 SharePoint 的用户](media/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a><span data-ttu-id="0b993-256">管理证书</span><span class="sxs-lookup"><span data-stu-id="0b993-256">Managing certificates</span></span>
<span data-ttu-id="0b993-257">请务必了解, 在上面的步骤4中为受信任的标识提供程序配置的签名证书具有过期日期, 必须续订。</span><span class="sxs-lookup"><span data-stu-id="0b993-257">It is important to understand that the signing certificate that was configured for the trusted identity provider in step 4 above has an expiration date and must be renewed.</span></span> <span data-ttu-id="0b993-258">有关证书续订的信息, 请参阅[在 Azure Active Directory 中管理联合单一登录的证书一](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs)文。</span><span class="sxs-lookup"><span data-stu-id="0b993-258">See the article [Manage certificates for federated single sign-on in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) for information on certificate renewal.</span></span> <span data-ttu-id="0b993-259">在 Azure AD 中续订证书后, 下载到本地文件, 并使用以下脚本配置已续订签名证书的受信任标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-259">Once the certificate has been renewed in Azure AD, download to a local file and use the following script to configure the trusted identity provider with the renewed signing certificate.</span></span> 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a><span data-ttu-id="0b993-260">为多个 web 应用程序配置一个受信任的标识提供程序</span><span class="sxs-lookup"><span data-stu-id="0b993-260">Configuring one trusted identity provider for multiple web applications</span></span>
<span data-ttu-id="0b993-261">配置适用于单个 web 应用程序, 但如果打算对多个 web 应用程序使用相同的受信任标识提供程序, 则需要其他配置。</span><span class="sxs-lookup"><span data-stu-id="0b993-261">The configuration works for a single web application, but needs additional configuration if you intend to use the same trusted identity provider for multiple web applications.</span></span> <span data-ttu-id="0b993-262">例如, 假定我们已将 web 应用程序扩展为使用 URL `https://portal.contoso.local` , 现在想要对用户`https://sales.contoso.local`进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="0b993-262">For example, assume we had extended a web application to use the URL `https://portal.contoso.local` and now want to authenticate the users to `https://sales.contoso.local` as well.</span></span> <span data-ttu-id="0b993-263">为此, 我们需要更新标识提供程序以接受 WReply 参数, 并更新 Azure AD 中的应用程序注册, 以添加回复 URL。</span><span class="sxs-lookup"><span data-stu-id="0b993-263">To do this, we need to update the identity provider to honor the WReply parameter and update the application registration in Azure AD to add a reply URL.</span></span>

1. <span data-ttu-id="0b993-264">在 Azure 门户中, 打开 Azure AD 目录。</span><span class="sxs-lookup"><span data-stu-id="0b993-264">In the Azure Portal, open the Azure AD directory.</span></span> <span data-ttu-id="0b993-265">单击 "**应用程序注册**", 然后单击 "**查看所有应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-265">Click **App registrations**, then click **View all applications**.</span></span> <span data-ttu-id="0b993-266">单击先前创建的应用程序 (SharePoint SAML 集成)。</span><span class="sxs-lookup"><span data-stu-id="0b993-266">Click the application that you created previously (SharePoint SAML Integration).</span></span>
2. <span data-ttu-id="0b993-267">单击 "**设置**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-267">Click **Settings**.</span></span>
3. <span data-ttu-id="0b993-268">在 "设置" 边栏选项卡中, 单击 "**答复 url**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-268">In the settings blade, click **Reply URLs**.</span></span> 
4. <span data-ttu-id="0b993-269">添加附加到 URL 的其他 web 应用程序`/_trust/default.aspx`的 url (例如`https://sales.contoso.local/_trust/default.aspx`), 然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-269">Add the URL for the additional web application with `/_trust/default.aspx` appended to the URL (such as `https://sales.contoso.local/_trust/default.aspx`) and click **Save**.</span></span> 
5. <span data-ttu-id="0b993-270">在 SharePoint 服务器上, 使用之前使用的受信任的标识令牌颁发者的名称打开**sharepoint 2016 命令行管理**程序, 并执行以下命令。</span><span class="sxs-lookup"><span data-stu-id="0b993-270">On the SharePoint server, open the **SharePoint 2016 Management Shell** and execute the following commands, using the name of the trusted identity token issuer that you used previously.</span></span>

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. <span data-ttu-id="0b993-271">在管理中心中, 转到 web 应用程序并启用现有的受信任标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-271">In Central Administration, go to the web application and enable the existing trusted identity provider.</span></span> <span data-ttu-id="0b993-272">请记住, 还要将登录页面 URL 配置为自定义登录页`/_trust/`。</span><span class="sxs-lookup"><span data-stu-id="0b993-272">Remember to also configure the sign-in page URL as a custom sign in page `/_trust/`.</span></span>
7. <span data-ttu-id="0b993-273">在管理中心中, 单击 "web 应用程序", 然后选择 "**用户策略**"。</span><span class="sxs-lookup"><span data-stu-id="0b993-273">In Central Administration, click the web application and choose **User Policy**.</span></span> <span data-ttu-id="0b993-274">按照本文前面所述, 添加具有适当权限的用户。</span><span class="sxs-lookup"><span data-stu-id="0b993-274">Add a user with the appropriate permissions as demonstrated previously in this article.</span></span>

## <a name="fixing-people-picker"></a><span data-ttu-id="0b993-275">修复人员选取器</span><span class="sxs-lookup"><span data-stu-id="0b993-275">Fixing People Picker</span></span>
<span data-ttu-id="0b993-276">用户现在可以使用 Azure AD 中的标识登录到 SharePoint 2016, 但仍有机会改进用户体验。</span><span class="sxs-lookup"><span data-stu-id="0b993-276">Users can now log into SharePoint 2016 using identities from Azure AD, but there are still opportunities for improvement to the user experience.</span></span> <span data-ttu-id="0b993-277">例如, 搜索用户会在人员选取器中提供多个搜索结果。</span><span class="sxs-lookup"><span data-stu-id="0b993-277">For instance, searching for a user presents multiple search results in the people picker.</span></span> <span data-ttu-id="0b993-278">在声明映射中创建的三个声明类型中的每一个都有一个搜索结果。</span><span class="sxs-lookup"><span data-stu-id="0b993-278">There is a search result for each of the 3 claim types that were created in the claim mapping.</span></span> <span data-ttu-id="0b993-279">若要使用人员选取器选择用户, 您必须完全键入其用户名, 然后选择**名称**声明结果。</span><span class="sxs-lookup"><span data-stu-id="0b993-279">To choose a user using the people picker, you must type their user name exactly and choose the **name** claim result.</span></span>

![声明搜索结果](media/SAML11/fig16-claimssearchresults.png)

<span data-ttu-id="0b993-281">您搜索的值没有验证, 这可能会导致拼写错误或用户意外选择了错误的声明类型来分配, 例如,**姓**声明。</span><span class="sxs-lookup"><span data-stu-id="0b993-281">There is no validation on the values you search for, which can lead to misspellings or users accidentally choosing the wrong claim type to assign such as the **SurName** claim.</span></span> <span data-ttu-id="0b993-282">这可能会阻止用户成功访问资源。</span><span class="sxs-lookup"><span data-stu-id="0b993-282">This can prevent users from successfully accessing resources.</span></span>

<span data-ttu-id="0b993-283">为帮助此方案, 存在一个名为[AzureCP](https://yvand.github.io/AzureCP/)的开放源代码解决方案, 该解决方案为 SharePoint 2016 提供了自定义声明提供程序。</span><span class="sxs-lookup"><span data-stu-id="0b993-283">To assist with this scenario, there is an open-source solution called [AzureCP](https://yvand.github.io/AzureCP/) that provides a custom claims provider for SharePoint 2016.</span></span> <span data-ttu-id="0b993-284">它将使用 Azure AD Graph 解析用户输入和执行验证的内容。</span><span class="sxs-lookup"><span data-stu-id="0b993-284">It will use the Azure AD Graph to resolve what users enter and perform validation.</span></span> <span data-ttu-id="0b993-285">有关详细信息, 请参阅[AzureCP](https://yvand.github.io/AzureCP/)。</span><span class="sxs-lookup"><span data-stu-id="0b993-285">Learn more at [AzureCP](https://yvand.github.io/AzureCP/).</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="0b993-286">其他资源</span><span class="sxs-lookup"><span data-stu-id="0b993-286">Additional resources</span></span>

[<span data-ttu-id="0b993-287">了解 WS-Federation</span><span class="sxs-lookup"><span data-stu-id="0b993-287">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="0b993-288">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="0b993-288">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="0b993-289">加入讨论</span><span class="sxs-lookup"><span data-stu-id="0b993-289">Join the discussion</span></span>

|<span data-ttu-id="0b993-290">**联系我们**</span><span class="sxs-lookup"><span data-stu-id="0b993-290">**Contact us**</span></span>|<span data-ttu-id="0b993-291">**说明**</span><span class="sxs-lookup"><span data-stu-id="0b993-291">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="0b993-292">**您需要什么样的解决方案？**</span><span class="sxs-lookup"><span data-stu-id="0b993-292">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="0b993-p136">我们正在为跨多个 Microsoft 产品和服务的解决方案创建内容。请告诉我们您对我们的跨服务器解决方案的想法，或者发送电子邮件到 [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) 寻求具体的解决方案。</span><span class="sxs-lookup"><span data-stu-id="0b993-p136">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="0b993-295">**参加解决方案讨论**</span><span class="sxs-lookup"><span data-stu-id="0b993-295">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="0b993-p137">如果热衷于基于云的解决方案，请考虑加入云采用咨询委员会 (CAAB)，以便与充满活力的更大规模社区保持联络，其中包括 Microsoft 内容开发人员、行业专家和全球各地的客户。若要加入，请将自己添加为 Microsoft 技术社区的[云采用咨询委员会 (CAAB) 空间](https://aka.ms/caab)成员，并向我们 ([CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)) 发送电子邮件。任何人都可以阅读 [CAAB 博客](https://blogs.technet.com/b/solutions_advisory_board/)上与社区相关的内容。不过，CAAB 成员可获邀参加私人网络研讨会，了解新云采用资源和解决方案。</span><span class="sxs-lookup"><span data-stu-id="0b993-p137">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="0b993-300">**获取您在此处看到的图片**</span><span class="sxs-lookup"><span data-stu-id="0b993-300">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="0b993-p138">若要获取本文中图片的可编辑副本，请告诉我们，我们非常乐意发送副本。请通过电子邮件方式将请求（包括图片的 URL 和标题）发送到 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)。</span><span class="sxs-lookup"><span data-stu-id="0b993-p138">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   

