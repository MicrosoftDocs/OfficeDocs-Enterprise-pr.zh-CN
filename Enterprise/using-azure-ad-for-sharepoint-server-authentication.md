---
title: "SharePoint 服务器身份验证使用 Azure 的广告"
ms.author: tracyp
author: MSFTTracyP
ms.reviewer:
- kirke
- josephd
- kirks
manager: laurawi
ms.date: 3/2/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: 
description: "摘要： 了解如何绕过 Azure 访问控制服务和使用 SAML 1.1 Azure Active Directory 与您 SharePoint 服务器用户进行身份验证。"
ms.openlocfilehash: e57414c3ed5af5c02b719d0c3639542e154be5bf
ms.sourcegitcommit: fbf33e74fd74c4ad6d60b2214329a3bbbdb3cc7c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a><span data-ttu-id="b00e7-103">SharePoint 服务器身份验证使用 Azure 的广告</span><span class="sxs-lookup"><span data-stu-id="b00e7-103">Using Azure AD for SharePoint Server Authentication</span></span>

 <span data-ttu-id="b00e7-104">**摘要：**了解如何使用 Azure Active Directory 您 SharePoint 服务器 2016年用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b00e7-104">**Summary:** Learn how to authenticate your SharePoint Server 2016 users with Azure Active Directory.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b00e7-105">本文基于 Kirk Evans，Microsoft 主体项目经理的工作。</span><span class="sxs-lookup"><span data-stu-id="b00e7-105">This article is based on the work of Kirk Evans, a Microsoft Principal Program Manager.</span></span> 

<blockquote>
<p><span data-ttu-id="b00e7-p101">这篇文章是指与 Azure 活动目录图表进行交互的代码样本。您可以下载代码示例[这里](https://github.com/kaevans/spsaml11/tree/master/scripts)。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p101">This article refers to code samples for interacting with Azure Active Directory Graph. You can download the code samples  [here](https://github.com/kaevans/spsaml11/tree/master/scripts).</span></span></p>
</blockquote>

<span data-ttu-id="b00e7-p102">SharePoint 服务器 2016年提供使用基于声明的身份验证，使其更容易地管理您的用户通过与不同的标识提供程序信任，但其他人管理对进行身份验证的用户进行身份验证的能力。例如，而不是管理用户身份验证通过 Active Directory 域服务 (AD DS)，可以使用户能够使用 Azure 活动目录 (AD Azure) 进行身份验证。这样，仅云用户与他们的用户名中的 onmicrosoft.com 后缀的身份验证，用户与内部部署目录，同步和邀请的来宾用户从其他目录。它还使您能够利用 Azure 的广告功能，例如多因素身份验证和高级报告功能。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p102">SharePoint Server 2016 provides the ability to authenticate users using claims-based authentication, making it easy to manage your users by authenticating them with different identity providers that you trust but someone else manages. For example, instead of managing user authentication through Active Directory Domain Services (AD DS), you could enable users to authenticate using Azure Active Directory (Azure AD). This enables authentication for cloud-only users with the onmicrosoft.com suffix in their username, users synchronized with an on-premises directory, and invited guest users from other directories. It also enables you to take advantage of Azure AD features such as multi-factor authentication and advanced reporting capabilities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b00e7-p103">也可以与 SharePoint Server 2013; 使用本文中介绍的解决方案但是，记住 SharePoint Server 2013 已接近主流支持期结束。有关详细信息，请参阅[Microsoft 生命周期策略](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013)和[更新产品维修策略的 SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx)。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p103">The solution described in this article can also be used with SharePoint Server 2013; however, keep in mind that SharePoint Server 2013 is nearing the end of mainstream support. For more information, see [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) and [Updated Product Servicing Policy for SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).</span></span>

<span data-ttu-id="b00e7-p104">这篇文章解释了如何使用 Azure 的广告来对用户进行身份验证而不是您在部署 AD DS。在此配置中，Azure 广告成为 SharePoint 服务器 2016 年受信任的身份提供程序。此配置将是分开由本身的 SharePoint 服务器 2016年安装 AD DS 身份验证的用户身份验证方法。要从本文获益，您应该熟悉 WS 联合身份验证。有关详细信息，请参阅[了解 WS 联合身份验证](https://go.microsoft.com/fwlink/p/?linkid=188052)。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p104">This article explains how you can use Azure AD to authenticate your users instead of your on-premises AD DS. In this configuration, Azure AD becomes a trusted identity provider for SharePoint Server 2016. This configuration adds a user authentication method that is separate from the AD DS authentication used by the SharePoint Server 2016 installation itself. To benefit from this article, you should be familiar with WS-Federation. For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span>

![SharePoint 身份验证使用 Azure 的广告](images/SAML11/fig1-architecture.png)

<span data-ttu-id="b00e7-p105">以前，这种配置需要如 Azure 访问控制服务 (ACS) 云或环境中的联合身份验证服务来转换标记从 SAML 2.0 SAML 1.1 到该主机 Active Directory 联合身份验证服务 (AD FS)。不再需要这种转换后 Azure 广告现在可支持颁发 SAML 1.1 标记。上图显示对 SharePoint 2016 用户在此配置中，证明不会再为中介，以执行这项转换要求身份验证的方式。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p105">Previously, this configuration would have required a federation service such as Azure Access Control Service (ACS) in the cloud or an environment that hosts Active Directory Federation Services (AD FS) to transform tokens from SAML 2.0 to SAML 1.1. This transformation is no longer required as Azure AD now enables issuing SAML 1.1 tokens. The diagram above shows how authentication works for SharePoint 2016 users in this configuration, demonstrating that there is no longer a requirement for an intermediary to perform this transformation.</span></span>

> [!NOTE]
> <span data-ttu-id="b00e7-p106">这种配置工作是否在 Azure 的虚拟机或内部承载 SharePoint 服务器场。它不需要打开其他防火墙端口而不是确保用户可以从浏览器访问 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p106">This configuration works whether the SharePoint farm is hosted in Azure virtual machines or on-premises. It does not require opening additional firewall ports other than ensuring users can access Azure Active Directory from their browser.</span></span>

<span data-ttu-id="b00e7-125">关于 SharePoint 2016 辅助功能的信息，请参阅[SharePoint 服务器 2016年中的可访问性准则](https://go.microsoft.com/fwlink/p/?LinkId=393123)。</span><span class="sxs-lookup"><span data-stu-id="b00e7-125">For information about SharePoint 2016 accessibility, see [Accessibility Guidelines in SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>

## <a name="configuration-overview"></a><span data-ttu-id="b00e7-126">配置概述</span><span class="sxs-lookup"><span data-stu-id="b00e7-126">Configuration overview</span></span>

<span data-ttu-id="b00e7-127">请执行以下常规步骤，将您的环境设置为作为 SharePoint 服务器 2016年身份标识提供程序使用 Azure 的广告。</span><span class="sxs-lookup"><span data-stu-id="b00e7-127">Follow these general steps to set up your environment to use Azure AD as a SharePoint Server 2016 identity provider.</span></span>

1. <span data-ttu-id="b00e7-128">创建一个新 Azure 的广告目录，或者使用您现有的目录。</span><span class="sxs-lookup"><span data-stu-id="b00e7-128">Create a new Azure AD directory or use your existing directory.</span></span>
2. <span data-ttu-id="b00e7-129">请确保您想要使用 Azure AD 安全的 web 应用程序的区域被配置为使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="b00e7-129">Ensure the zone for the web application that you want to secure with Azure AD is configured to use SSL.</span></span>
3. <span data-ttu-id="b00e7-130">在 Azure AD 中创建新的企业级应用程序。</span><span class="sxs-lookup"><span data-stu-id="b00e7-130">Create a new enterprise application in Azure AD.</span></span>
4. <span data-ttu-id="b00e7-131">在 SharePoint 服务器 2016年配置新的受信任的身份提供程序。</span><span class="sxs-lookup"><span data-stu-id="b00e7-131">Configure a new trusted identity provider in SharePoint Server 2016.</span></span>
5. <span data-ttu-id="b00e7-132">设置 web 应用程序的权限。</span><span class="sxs-lookup"><span data-stu-id="b00e7-132">Set the permissions for the web application.</span></span>
6. <span data-ttu-id="b00e7-133">在 Azure AD 中添加 SAML 1.1 令牌颁发策略。</span><span class="sxs-lookup"><span data-stu-id="b00e7-133">Add a SAML 1.1 token issuance policy in Azure AD.</span></span>
7. <span data-ttu-id="b00e7-134">验证新的提供程序。</span><span class="sxs-lookup"><span data-stu-id="b00e7-134">Verify the new provider.</span></span>

<span data-ttu-id="b00e7-135">以下各节介绍如何执行这些任务。</span><span class="sxs-lookup"><span data-stu-id="b00e7-135">The following sections describe how to perform these tasks.</span></span>

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a><span data-ttu-id="b00e7-136">步骤 1： 创建一个新 Azure 的广告目录，或者使用您现有的目录</span><span class="sxs-lookup"><span data-stu-id="b00e7-136">Step 1: Create a new Azure AD directory or use your existing directory</span></span>

<span data-ttu-id="b00e7-p107">在 Azure 门户网站 ([https://portal.azure.com](https://portal.azure.com))，创建一个新目录。提供组织名称、 初始域名称和国家 / 地区。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p107">In the Azure Portal ([https://portal.azure.com](https://portal.azure.com)), create a new directory. Provide the organization name, initial domain name, and the country or region.</span></span>

![创建目录](images/SAML11/fig2-createdirectory.png) 

 <span data-ttu-id="b00e7-p108">如果已经有类似用于 Microsoft Office 365 或 Microsoft Azure 订阅目录，您可以改为使用该目录。您必须在目录中注册应用程序的权限。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p108">If you already have a directory such as the one used for Microsoft Office 365 or your Microsoft Azure subscription, you can use that directory instead. You must have permissions to register applications in the directory.</span></span>

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a><span data-ttu-id="b00e7-142">第 2 步： 确认您想要使用 Azure AD 安全的 web 应用程序的区域被配置为使用 SSL</span><span class="sxs-lookup"><span data-stu-id="b00e7-142">Step 2: Ensure the zone for the web application that you want to secure with Azure AD is configured to use SSL</span></span>

<span data-ttu-id="b00e7-p109">撰写本文时使用参考体系结构中[运行高可用性在 Azure 中的 SharePoint 服务器 2016年场](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)。使用[本文](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)中介绍的解决方案部署的文章的伴随脚本可创建不使用 SSL 的网站。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p109">This article was written using the reference architecture in [Run a high availability SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint). The article’s accompanying scripts used to deploy the solution described in [this article](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) create a site that does not use SSL.</span></span>  

<span data-ttu-id="b00e7-p110">使用 SAML 需要将应用程序配置为使用 SSL。如果 SharePoint web 应用程序未配置为使用 SSL，请使用以下步骤创建新的自签名的证书配置 SSL 的 web 应用程序。此配置仅适用于实验室环境并不适合生产。生产环境应该使用一个签名的证书。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p110">Using SAML requires the application be configured to use SSL. If your SharePoint web application is not configured to use SSL, use the following steps to create a new self-signed certificate to configure the web application for SSL. This configuration is only meant for a lab environment and is not intended for production. Production environments should use a signed certificate.</span></span>

1. <span data-ttu-id="b00e7-p111">转到**管理中心** > **应用程序管理** > **管理 Web 应用程序**，然后选择需要进行扩展，以使用 SSL 的 web 应用程序。选择 web 应用程序并单击**扩展功能区**按钮。扩展的 web 应用程序使用相同的 URL，但端口 443 上使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p111">Go to **Central Administration** > **Application Management** > **Manage Web Applications**, and choose the web application that needs to be extended to use SSL. Select the web application and click the **Extend ribbon** button. Extend the web application to use the same URL but use SSL with port 443.</span></span></br><span data-ttu-id="b00e7-152">![扩展到另一个 IIS 网站的 web 应用程序](images/SAML11/fig3-extendwebapptoiis.png)</span><span class="sxs-lookup"><span data-stu-id="b00e7-152">![Extending the web app to another IIS site](images/SAML11/fig3-extendwebapptoiis.png)</span></span></br>
2. <span data-ttu-id="b00e7-153">在 IIS 管理器 中，双击"服务器证书"。</span><span class="sxs-lookup"><span data-stu-id="b00e7-153">In IIS Manager, double-click **Server Certificates**.</span></span>
3. <span data-ttu-id="b00e7-p112">在**操作**窗格中，单击**创建自签名证书**。在指定友好名称的证书框中，键入证书的友好名称，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p112">In the **Actions** pane, click **Create Self-Signed Certificate**. Type a friendly name for the certificate in the Specify a friendly name for the certificate box, and then click **OK**.</span></span>
4. <span data-ttu-id="b00e7-156">从**编辑站点绑定**对话框中，确保主机名相同的友好名称，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="b00e7-156">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following image.</span></span></br><span data-ttu-id="b00e7-157">![在 IIS 中的编辑站点绑定](images/SAML11/fig4-editsitebinding.png)</span><span class="sxs-lookup"><span data-stu-id="b00e7-157">![Editing site binding in IIS](images/SAML11/fig4-editsitebinding.png)</span></span></br>

<span data-ttu-id="b00e7-158">每个 SharePoint 服务器场中的 web 前端服务器将需要在 IIS 中配置网站绑定的证书。</span><span class="sxs-lookup"><span data-stu-id="b00e7-158">Each of the web front end servers in the SharePoint farm will require configuring the certificate for the site binding in IIS.</span></span>


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a><span data-ttu-id="b00e7-159">步骤 3： 创建新的企业级应用程序在 Azure 的广告</span><span class="sxs-lookup"><span data-stu-id="b00e7-159">Step 3: Create a new enterprise application in Azure AD</span></span>

1. <span data-ttu-id="b00e7-p113">在 Azure 门户网站 ([https://portal.azure.com](https://portal.azure.com))，打开 Azure 的广告目录。单击**企业应用程序**，然后单击**新的应用程序**。选择**非库应用程序**。提供一个名称，如*SharePoint SAML 集成*并单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p113">In the Azure Portal ([https://portal.azure.com](https://portal.azure.com)), open your Azure AD directory. Click **Enterprise Applications**, then click **New application**. Choose **Non-gallery application**. Provide a name such as *SharePoint SAML Integration* and click **Add**.</span></span></br><span data-ttu-id="b00e7-164">![添加一个新的非库应用程序](images/SAML11/fig5-addnongalleryapp.png)</span><span class="sxs-lookup"><span data-stu-id="b00e7-164">![Adding a new non-gallery application](images/SAML11/fig5-addnongalleryapp.png)</span></span></br>
2. <span data-ttu-id="b00e7-p114">单击导航窗格中配置应用程序，一个登录链接。为**基于 SAML 的登录方式进行登录**以显示应用程序的 SAML 配置属性更改**单一登录模式**下拉列表。配置具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="b00e7-p114">Click the Single sign-on link in the navigation pane to configure the application. Change the **Single Sign-on Mode** dropdown to **SAML-based Sign-on** to reveal the SAML configuration properties for the application. Configure with the following properties:</span></span></br>
    - <span data-ttu-id="b00e7-168">标识符：`urn:sharepoint:portal.contoso.local`</span><span class="sxs-lookup"><span data-stu-id="b00e7-168">Identifier: `urn:sharepoint:portal.contoso.local`</span></span>
    - <span data-ttu-id="b00e7-169">答复的 URL:`https://portal.contoso.local/_trust/default.aspx`</span><span class="sxs-lookup"><span data-stu-id="b00e7-169">Reply URL: `https://portal.contoso.local/_trust/default.aspx`</span></span>
    - <span data-ttu-id="b00e7-170">登录 URL:`https://portal.contoso.local/_trust/default.aspx`</span><span class="sxs-lookup"><span data-stu-id="b00e7-170">Sign-on URL: `https://portal.contoso.local/_trust/default.aspx`</span></span>
    - <span data-ttu-id="b00e7-171">用户标识符：`user.userprincipalname`</span><span class="sxs-lookup"><span data-stu-id="b00e7-171">User Identifier: `user.userprincipalname`</span></span></br>
    - <span data-ttu-id="b00e7-172">注： 请记住，若要通过将*portal.contoso.local*替换为要保护的 SharePoint 网站的 URL 更改 Url。</span><span class="sxs-lookup"><span data-stu-id="b00e7-172">Note: Remember to change the URLs by replacing *portal.contoso.local* with the URL of the SharePoint site you want to secure.</span></span></br>
3. <span data-ttu-id="b00e7-173">设置表 （类似于下面的表 1），其中包含以下行：</span><span class="sxs-lookup"><span data-stu-id="b00e7-173">Set up a table (similar to Table 1 below) that includes the following rows:</span></span></br> 
    - <span data-ttu-id="b00e7-174">领域</span><span class="sxs-lookup"><span data-stu-id="b00e7-174">Realm</span></span>
    - <span data-ttu-id="b00e7-175">SAML 签名证书文件的完整路径</span><span class="sxs-lookup"><span data-stu-id="b00e7-175">Full path to SAML signing certificate file</span></span>
    - <span data-ttu-id="b00e7-176">SAML 单一登录服务 URL 中 （替换*/wsfed* */saml2* ）</span><span class="sxs-lookup"><span data-stu-id="b00e7-176">SAML Single Sign-On service URL (replacing */saml2* with */wsfed*)</span></span>
    - <span data-ttu-id="b00e7-177">应用程序对象的 id。</span><span class="sxs-lookup"><span data-stu-id="b00e7-177">Application Object ID.</span></span> </br>
<span data-ttu-id="b00e7-178">将*标识符*值复制到*领域*属性到表中 (请参阅表 1 下面)。</span><span class="sxs-lookup"><span data-stu-id="b00e7-178">Copy the *Identifier* value into the *Realm* property into a table  (See Table 1 below.)</span></span>
4. <span data-ttu-id="b00e7-179">保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="b00e7-179">Save your changes.</span></span>
5. <span data-ttu-id="b00e7-180">单击**配置 （应用程序名称）**链接来访问配置登录页。</span><span class="sxs-lookup"><span data-stu-id="b00e7-180">Click the **Configure (app name)** link to access the Configure sign-on page.</span></span></br><span data-ttu-id="b00e7-181">![在页面上配置单一登录](images/SAML11/fig7-configssopage.png)</span><span class="sxs-lookup"><span data-stu-id="b00e7-181">![Configuring a single-sign on page](images/SAML11/fig7-configssopage.png)</span></span></br> 
    -  <span data-ttu-id="b00e7-p115">单击要作为扩展名为.cer 的文件下载 SAML 签名证书的**SAML 签名证书的原始**链接。复制并粘贴到您的表下载的文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p115">Click the **SAML Signing Certificate - Raw** link to download the SAML Signing Certificate as a file with the .cer extension. Copy and paste the full path to the downloaded file into your table.</span></span>
    - <span data-ttu-id="b00e7-184">复制和粘贴的 SAML 单一登录服务 URL 链接到您，用*/wsfed*替换 URL 的*/saml2*部分。</span><span class="sxs-lookup"><span data-stu-id="b00e7-184">Copy and paste the SAML Single Sign-On Service URL link into your, replacing the */saml2* portion of the URL with */wsfed*.</span></span></br>
6.  <span data-ttu-id="b00e7-p116">导航到应用程序的**属性**窗格中。复制并粘贴到您在第 3 步中设置的表的对象 ID 值。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p116">Navigate to the **Properties** pane for the application. Copy and paste the Object ID value into the table you set up in Step 3.</span></span></br><span data-ttu-id="b00e7-187">![应用程序的属性窗格](images/SAML11/fig8-propertiespane.png)</span><span class="sxs-lookup"><span data-stu-id="b00e7-187">![Properties pane for the application](images/SAML11/fig8-propertiespane.png)</span></span></br>
7. <span data-ttu-id="b00e7-188">使用值捕获，请确保您在第 3 步中设置的表类似于下面的表 1。</span><span class="sxs-lookup"><span data-stu-id="b00e7-188">Using the values you captured, make sure the table you set up in Step 3 resembles Table 1 below.</span></span>


| <span data-ttu-id="b00e7-189">表 1： 值捕获</span><span class="sxs-lookup"><span data-stu-id="b00e7-189">Table 1: Values captured</span></span>  |  |
|---------|---------|
|<span data-ttu-id="b00e7-190">领域</span><span class="sxs-lookup"><span data-stu-id="b00e7-190">Realm</span></span> | `urn:sharepoint:portal.contoso.local` |
|<span data-ttu-id="b00e7-191">SAML 签名证书文件的完整路径</span><span class="sxs-lookup"><span data-stu-id="b00e7-191">Full path to SAML signing certificate file</span></span> | `C:/temp/SharePoint SAML Integration.cer`  |
|<span data-ttu-id="b00e7-192">SAML 单一登录服务 URL （替换 /wsfed /saml2）</span><span class="sxs-lookup"><span data-stu-id="b00e7-192">SAML single sign-on service URL (replace /saml2 with /wsfed)</span></span> | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|<span data-ttu-id="b00e7-193">应用程序对象 ID</span><span class="sxs-lookup"><span data-stu-id="b00e7-193">Application Object ID</span></span> | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> <span data-ttu-id="b00e7-p117">在 URL 中的*/saml2*值替换为*/wsfed*。*/Saml2*终结点将处理 SAML 2.0 令牌。*/Wsfed*终结点使处理 SAML 1.1 标记，并且需要为 SharePoint 2016 SAML 联盟。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p117">Replace the */saml2* value in the URL with */wsfed*. The */saml2* endpoint will process SAML 2.0 tokens. The */wsfed* endpoint enables processing SAML 1.1 tokens and is required for SharePoint 2016 SAML federation.</span></span>

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a><span data-ttu-id="b00e7-197">步骤 4： 配置新的受信任的身份提供方在 SharePoint 服务器 2016</span><span class="sxs-lookup"><span data-stu-id="b00e7-197">Step 4: Configure a new trusted identity provider in SharePoint Server 2016</span></span>

<span data-ttu-id="b00e7-p118">登录到 SharePoint 服务器 2016年服务器并打开 SharePoint 2016 管理外壳。在 $realm、 $wsfedurl 和 $filepath 从表 1 的值填充并运行下面的命令来配置新的受信任的身份提供程序。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p118">Sign into the SharePoint Server 2016 server and open the SharePoint 2016 Management Shell. Fill in the values of $realm, $wsfedurl, and $filepath from Table 1 and run the following commands to configure a new trusted identity provider.</span></span>

> [!TIP]
> <span data-ttu-id="b00e7-200">如果使用 PowerShell 新手或想要了解有关 PowerShell 的工作原理的详细信息，请参阅[SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="b00e7-200">If you're new to using PowerShell or want to learn more about how PowerShell works, see [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps).</span></span> 

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

<span data-ttu-id="b00e7-201">接下来，请按照以下步骤来启用应用程序信任的身份提供程序：</span><span class="sxs-lookup"><span data-stu-id="b00e7-201">Next, follow these steps to enable the trusted identity provider for your application:</span></span>
1. <span data-ttu-id="b00e7-202">在管理中心，导航到**管理 Web 应用程序**并选择您想要使用 Azure AD 安全 web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="b00e7-202">In Central Administration, navigate to **Manage Web Application** and select the web application that you wish to secure with Azure AD.</span></span> 
2. <span data-ttu-id="b00e7-203">在功能区中，单击**身份验证提供程序**，并选择您想要使用的区域。</span><span class="sxs-lookup"><span data-stu-id="b00e7-203">In the ribbon, click **Authentication Providers** and choose the zone that you wish to use.</span></span>
3. <span data-ttu-id="b00e7-204">选择**受信任的身份提供程序**并选择名为*AzureAD*的识别提供只需注册。</span><span class="sxs-lookup"><span data-stu-id="b00e7-204">Select **Trusted Identity provider** and select the identify provider you just registered named *AzureAD*.</span></span>  
4. <span data-ttu-id="b00e7-205">登录页的 URL 设置，请选择**自定义登录页**和提供的值"/_trust/"。</span><span class="sxs-lookup"><span data-stu-id="b00e7-205">On the sign-in page URL setting, select **Custom sign in page** and provide the value “/_trust/”.</span></span> 
5. <span data-ttu-id="b00e7-206">单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="b00e7-206">Click **OK**.</span></span>

![配置身份验证提供程序](images/SAML11/fig10-configauthprovider.png)

## <a name="step-5-set-the-permissions"></a><span data-ttu-id="b00e7-208">步骤 5： 设置权限</span><span class="sxs-lookup"><span data-stu-id="b00e7-208">Step 5: Set the permissions</span></span>

<span data-ttu-id="b00e7-209">将登录到 Azure 的 AD 和访问 SharePoint 用户必须被授予访问应用程序。</span><span class="sxs-lookup"><span data-stu-id="b00e7-209">The users who will log into Azure AD and access SharePoint must be granted access to the application.</span></span> 

1. <span data-ttu-id="b00e7-p119">在 Azure 门户中，打开 Azure 的广告目录。单击**企业应用程序**，然后单击**所有应用程序**。单击以前创建的应用程序 （SharePoint SAML 集成）。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p119">In the Azure Portal, open the Azure AD directory. Click **Enterprise Applications**, then click **All applications**. Click the application that you created previously (SharePoint SAML Integration).</span></span>
2. <span data-ttu-id="b00e7-213">单击**用户和组**。</span><span class="sxs-lookup"><span data-stu-id="b00e7-213">Click **Users and Groups**.</span></span> 
3. <span data-ttu-id="b00e7-214">单击**添加用户**添加用户或组有权登录到 SharePoint 使用 Azure 的广告。</span><span class="sxs-lookup"><span data-stu-id="b00e7-214">Click **Add user** to add a user or group who will have permissions to log into SharePoint using Azure AD.</span></span>
4. <span data-ttu-id="b00e7-215">选择用户或组，然后单击**指派**。</span><span class="sxs-lookup"><span data-stu-id="b00e7-215">Select the user or group then click **Assign**.</span></span>
 
<span data-ttu-id="b00e7-p120">用户已被授予权限的 Azure 的广告，但还必须授予在 SharePoint 中的权限。使用以下步骤设置访问 web 应用程序的权限。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p120">The user has been granted permission in Azure AD, but also must be granted permission in SharePoint. Use the following steps to set the permissions to access the web application.</span></span>

1. <span data-ttu-id="b00e7-218">在管理中心中，单击"应用程序管理"。</span><span class="sxs-lookup"><span data-stu-id="b00e7-218">In Central Administration, click **Application Management**.</span></span>
2. <span data-ttu-id="b00e7-219">在"应用程序管理"页上的"Web 应用程序"部分，单击"管理 Web 应用程序"。</span><span class="sxs-lookup"><span data-stu-id="b00e7-219">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
3. <span data-ttu-id="b00e7-220">单击适当的 Web 应用程序，然后单击"用户策略"。</span><span class="sxs-lookup"><span data-stu-id="b00e7-220">Click the appropriate web application, and then click **User Policy**.</span></span>
4. <span data-ttu-id="b00e7-221">在 Web 应用程序的策略，单击**添加用户**。</span><span class="sxs-lookup"><span data-stu-id="b00e7-221">In Policy for Web Application, click **Add Users**.</span></span></br><span data-ttu-id="b00e7-222">![搜索用户通过其名称声明](images/SAML11/fig11-searchbynameclaim.png)</span><span class="sxs-lookup"><span data-stu-id="b00e7-222">![Searching for a user by their name claim](images/SAML11/fig11-searchbynameclaim.png)</span></span></br>
5. <span data-ttu-id="b00e7-223">在"添加用户"对话框中，单击"区域"中的适当区域，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="b00e7-223">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
6. <span data-ttu-id="b00e7-224">在**Web 应用程序的策略**对话框中的在**选择用户**部分，单击**浏览**图标。</span><span class="sxs-lookup"><span data-stu-id="b00e7-224">In the **Policy for Web Application** dialog box, in the **Choose Users** section, click the **Browse** icon.</span></span>
7. <span data-ttu-id="b00e7-225">在**查找**文本框中，键入用户的登录名称在您的目录中，单击**搜索**。</span><span class="sxs-lookup"><span data-stu-id="b00e7-225">In the **Find** textbox, type the sign-in name for a user in your directory and click **Search**.</span></span> </br><span data-ttu-id="b00e7-226">例如： *demouser@blueskyabove.onmicrosoft.com*。</span><span class="sxs-lookup"><span data-stu-id="b00e7-226">Example: *demouser@blueskyabove.onmicrosoft.com*.</span></span>
8. <span data-ttu-id="b00e7-227">AzureAD 在标题下的列表视图中，选择名称属性，单击**添加**，然后单击**确定**以关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="b00e7-227">Under the AzureAD heading in the list view, select the name property and click **Add** then click **OK** to close the dialog.</span></span>
9. <span data-ttu-id="b00e7-228">在权限中，单击**完全控制**。</span><span class="sxs-lookup"><span data-stu-id="b00e7-228">In Permissions, click **Full Control**.</span></span></br><span data-ttu-id="b00e7-229">![声明用户授权完全控制](images/SAML11/fig12-grantfullcontrol.png)</span><span class="sxs-lookup"><span data-stu-id="b00e7-229">![Granting full control to a claims user](images/SAML11/fig12-grantfullcontrol.png)</span></span></br>
10. <span data-ttu-id="b00e7-230">单击"完成"，然后单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="b00e7-230">Click **Finish**, and then click **OK**.</span></span>

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a><span data-ttu-id="b00e7-231">步骤 6： 在 Azure AD 中添加 SAML 1.1 令牌颁发策略</span><span class="sxs-lookup"><span data-stu-id="b00e7-231">Step 6: Add a SAML 1.1 token issuance policy in Azure AD</span></span>

<span data-ttu-id="b00e7-p121">在门户中创建 AD Azure 应用程序时，它默认使用 SAML 2.0。SharePoint 服务器 2016年要求 SAML 1.1 标记格式。下面的脚本将删除默认 SAML 2.0 策略，并对问题 SAML 1.1 标记中添加新的策略。这段代码要求下载附带的[示例演示与 Azure 活动目录图表进行交互](https://github.com/kaevans/spsaml11/tree/master/scripts)。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p121">When the Azure AD application is created in the portal, it defaults to using SAML 2.0. SharePoint Server 2016 requires the SAML 1.1 token format. The following script will remove the default SAML 2.0 policy and add a new policy to issue SAML 1.1 tokens. This code requires downloading the accompanying [samples demonstrating interacting with Azure Active Directory Graph](https://github.com/kaevans/spsaml11/tree/master/scripts).</span></span> 


```
Import-Module <file path of Initialize.ps1> 
$objectid = "<Application Object ID from Table 1>"
$saml2policyid = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $objectid | ?{$_.displayName -EQ "TokenIssuancePolicy"} | select objectId
Remove-PolicyFromServicePrincipal -policyId $saml2policyid -servicePrincipalId $objectid
$policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $objectid
```
> <span data-ttu-id="b00e7-p122">需要注意的是一定要运行`Import-Module`在此示例中所示的命令。这将加载的依赖模块包含所示的命令。您可能需要打开提升的命令提示符成功执行这些命令。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p122">Note that it is important to run the `Import-Module` command as shown in this example. This will load a dependent module that contains the commands shown. You may need to open an elevated command prompt to successfully execute these commands.</span></span>

<span data-ttu-id="b00e7-p123">这些示例 PowerShell 命令是如何对图形 API 执行查询的示例。使用 Azure AD 的令牌颁发策略的详细信息，请参阅[图形 API 参考的操作策略](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy)。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p123">These sample PowerShell commands are examples of how to execute queries against the Graph API. For more details on Token Issuance Policies with Azure AD, see the [Graph API reference for operations on policy](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy).</span></span>

## <a name="step-7-verify-the-new-provider"></a><span data-ttu-id="b00e7-241">第 7 步： 验证新的提供程序</span><span class="sxs-lookup"><span data-stu-id="b00e7-241">Step 7: Verify the new provider</span></span>

<span data-ttu-id="b00e7-p124">打开您在前面的步骤中配置的 web 应用程序的 url 的浏览器。您将被重定向，以登录到 Azure 的广告。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p124">Open a browser to the URL of the web application that you configured in the previous steps. You are redirected to sign into Azure AD.</span></span>

![登录到 Azure AD 配置联盟](images/SAML11/fig13-examplesignin.png)

<span data-ttu-id="b00e7-245">询问您是否要保持登录状态。</span><span class="sxs-lookup"><span data-stu-id="b00e7-245">You are asked if you want to stay signed in.</span></span>

![保持登录状态吗？](images/SAML11/fig14-staysignedin.png)

<span data-ttu-id="b00e7-247">最后，您可以访问网站从 Azure Active Directory 租户的用户的身份登录。</span><span class="sxs-lookup"><span data-stu-id="b00e7-247">Finally, you can access the site logged in as a user from your Azure Active Directory tenant.</span></span>

![用户登录到 SharePoint](images/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a><span data-ttu-id="b00e7-249">管理证书</span><span class="sxs-lookup"><span data-stu-id="b00e7-249">Managing certificates</span></span>
<span data-ttu-id="b00e7-p125">请务必了解上面的步骤 4 中的信任的身份提供程序配置的签名证书已到期日期和必须续订。有关续订证书，请参阅文章[管理联盟单一登录 Azure Active Directory 中的证书](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs)的信息。一旦已经在 Azure AD 续订该证书，下载到本地文件，并使用下面的脚本来配置续订签名证书与受信任的身份提供方。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p125">It is important to understand that the signing certificate that was configured for the trusted identity provider in step 4 above has an expiration date and must be renewed. See the article [Manage certificates for federated single sign-on in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) for information on certificate renewal. Once the certificate has been renewed in Azure AD, download to a local file and use the following script to configure the trusted identity provider with the renewed signing certificate.</span></span> 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```

## <a name="fixing-people-picker"></a><span data-ttu-id="b00e7-253">修复人员选取器</span><span class="sxs-lookup"><span data-stu-id="b00e7-253">Fixing People Picker</span></span>
<span data-ttu-id="b00e7-p126">用户现在可以登录到 SharePoint 2016 使用标识从 Azure 的广告，但仍有改进的用户体验的机会。例如，搜索用户人员选取器中显示多个搜索结果。还有 3 声明类型中声明映射创建的每个搜索结果。若要选择用户使用人员选取器，必须准确地键入他们的用户名并选择**名称**声明的结果。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p126">Users can now log into SharePoint 2016 using identities from Azure AD, but there are still opportunities for improvement to the user experience. For instance, searching for a user presents multiple search results in the people picker. There is a search result for each of the 3 claim types that were created in the claim mapping. To choose a user using the people picker, you must type their user name exactly and choose the **name** claim result.</span></span>

![索赔的搜索结果](images/SAML11/fig16-claimssearchresults.png)

<span data-ttu-id="b00e7-p127">没有验证您搜索的这会导致拼写错误的值或用户意外地选择错误声称如**姓**分配类型声明。这可以防止用户成功访问资源。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p127">There is no validation on the values you search for, which can lead to misspellings or users accidentally choosing the wrong claim type to assign such as the **SurName** claim. This can prevent users from successfully accessing resources.</span></span>

<span data-ttu-id="b00e7-p128">为了帮助这种情况下，提供了开源的解决方案称为 SharePoint 2016 年提供的自定义声明提供程序的[AzureCP](https://yvand.github.io/AzureCP/) 。它将使用 Azure 广告图解决用户输入并执行验证。了解更多信息，请访问[AzureCP](https://yvand.github.io/AzureCP/)。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p128">To assist with this scenario, there is an open-source solution called [AzureCP](https://yvand.github.io/AzureCP/) that provides a custom claims provider for SharePoint 2016. It will use the Azure AD Graph to resolve what users enter and perform validation. Learn more at [AzureCP](https://yvand.github.io/AzureCP/).</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="b00e7-264">其他资源</span><span class="sxs-lookup"><span data-stu-id="b00e7-264">Additional resources</span></span>

[<span data-ttu-id="b00e7-265">了解 WS-Federation</span><span class="sxs-lookup"><span data-stu-id="b00e7-265">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="b00e7-266">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="b00e7-266">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="b00e7-267">加入讨论</span><span class="sxs-lookup"><span data-stu-id="b00e7-267">Join the discussion</span></span>

|<span data-ttu-id="b00e7-268">**联系我们**</span><span class="sxs-lookup"><span data-stu-id="b00e7-268">**Contact us**</span></span>|<span data-ttu-id="b00e7-269">**说明**</span><span class="sxs-lookup"><span data-stu-id="b00e7-269">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b00e7-270">**你需要什么样的解决方案？**</span><span class="sxs-lookup"><span data-stu-id="b00e7-270">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="b00e7-p129">我们正在创建跨越多个 Microsoft 云平台和服务的云采用内容。请告诉我们你对云采用内容的想法，或者发送电子邮件至 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) 请求获取特定内容。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p129">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="b00e7-273">**参加解决方案讨论**</span><span class="sxs-lookup"><span data-stu-id="b00e7-273">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="b00e7-p130">如果热衷于基于云的解决方案，请考虑加入云采用咨询委员会 (CAAB)，以便与充满活力的更大规模社区保持联络，其中包括 Microsoft 内容开发人员、行业专家和全球各地的客户。若要加入，请将自己添加为 Microsoft 技术社区的[云采用咨询委员会 (CAAB) 空间](https://aka.ms/caab)成员，并向我们 ([CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)) 发送电子邮件。任何人都可以阅读 [CAAB 博客](https://blogs.technet.com/b/solutions_advisory_board/)上与社区相关的内容。不过，CAAB 成员可获邀参加私人网络研讨会，了解新云采用资源和解决方案。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p130">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="b00e7-277">**获取您在此处看到的图片**</span><span class="sxs-lookup"><span data-stu-id="b00e7-277">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="b00e7-p131">若要获取本文中图片的可编辑副本，请告诉我们，我们非常乐意发送副本。请通过电子邮件方式将请求（包括图片的 URL 和标题）发送到 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)。</span><span class="sxs-lookup"><span data-stu-id="b00e7-p131">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   

