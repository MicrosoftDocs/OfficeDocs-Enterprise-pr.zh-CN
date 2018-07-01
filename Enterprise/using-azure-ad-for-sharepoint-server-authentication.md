---
title: 使用 Azure AD 进行 SharePoint Server 身份验证
ms.author: tracyp
author: MSFTTracyP
ms.reviewer:
- kirke
- josephd
- kirks
manager: laurawi
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: ''
description: 摘要： 了解如何以绕过 Azure 访问控制服务，使用 SAML 1.1 与 Azure Active Directory 在 SharePoint Server 用户进行身份验证。
ms.openlocfilehash: dfaede331233444413d82b500e14fc68195eaca1
ms.sourcegitcommit: fe406eacd92dd5b3bd8c127b7bd8f2d0ef216404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "19856267"
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a><span data-ttu-id="9907f-103">使用 Azure AD 进行 SharePoint Server 身份验证</span><span class="sxs-lookup"><span data-stu-id="9907f-103">Using Azure AD for SharePoint Server Authentication</span></span>

 <span data-ttu-id="9907f-104">**摘要：** 了解如何在 SharePoint Server 2016 用户与 Azure Active Directory 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9907f-104">**Summary:** Learn how to authenticate your SharePoint Server 2016 users with Azure Active Directory.</span></span> 

<blockquote>
<p><span data-ttu-id="9907f-p101">本文是指与 Azure Active Directory 图形进行交互的代码示例。您可以下载代码示例[此处](https://github.com/kaevans/spsaml11/tree/master/scripts)。</span><span class="sxs-lookup"><span data-stu-id="9907f-p101">This article refers to code samples for interacting with Azure Active Directory Graph. You can download the code samples [here](https://github.com/kaevans/spsaml11/tree/master/scripts).</span></span></p>
</blockquote>

<span data-ttu-id="9907f-p102">SharePoint Server 2016 能够轻松地通过不同的身份提供程序的信任，但其他人管理对进行身份验证来管理您的用户使用基于声明的身份验证的用户进行身份验证。例如，而不是管理通过 Active Directory 域服务 (AD DS) 的用户身份验证，您无法使用户能够使用 Azure Active Directory (Azure AD) 进行身份验证。这样，具有中其用户名的 onmicrosoft.com 后缀的仅使用云的用户的身份验证，用户与内部部署目录同步和邀请来宾用户从其他目录。它还可以充分利用 Azure AD 功能，如多因素身份验证和高级报告功能。</span><span class="sxs-lookup"><span data-stu-id="9907f-p102">SharePoint Server 2016 provides the ability to authenticate users using claims-based authentication, making it easy to manage your users by authenticating them with different identity providers that you trust but someone else manages. For example, instead of managing user authentication through Active Directory Domain Services (AD DS), you could enable users to authenticate using Azure Active Directory (Azure AD). This enables authentication for cloud-only users with the onmicrosoft.com suffix in their username, users synchronized with an on-premises directory, and invited guest users from other directories. It also enables you to take advantage of Azure AD features such as multi-factor authentication and advanced reporting capabilities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9907f-p103">也可以与 SharePoint Server 2013; 使用本文中所述的解决方案但是，记住 SharePoint Server 2013 已接近主流支持结束。有关详细信息，请参阅[Microsoft 生命周期策略](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013)和[更新产品服务策略的 SharePoint 2013。](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx)</span><span class="sxs-lookup"><span data-stu-id="9907f-p103">The solution described in this article can also be used with SharePoint Server 2013; however, keep in mind that SharePoint Server 2013 is nearing the end of mainstream support. For more information, see [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013) and [Updated Product Servicing Policy for SharePoint 2013](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx).</span></span>

<span data-ttu-id="9907f-p104">本文介绍如何使用 Azure AD 以进行用户身份验证而不是您的内部部署 AD DS。在此配置中，Azure AD 将成为受信任的身份提供程序的 SharePoint Server 2016。此配置添加独立于所使用的 SharePoint Server 2016 安装本身的 AD DS 验证用户身份验证方法。这样可以受益这篇文章，您应熟悉 WS 联合身份验证。有关详细信息，请参阅[了解 WS 联合身份验证](https://go.microsoft.com/fwlink/p/?linkid=188052)。</span><span class="sxs-lookup"><span data-stu-id="9907f-p104">This article explains how you can use Azure AD to authenticate your users instead of your on-premises AD DS. In this configuration, Azure AD becomes a trusted identity provider for SharePoint Server 2016. This configuration adds a user authentication method that is separate from the AD DS authentication used by the SharePoint Server 2016 installation itself. To benefit from this article, you should be familiar with WS-Federation. For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span>

![SharePoint 身份验证使用 Azure AD](images/SAML11/fig1-architecture.png)

<span data-ttu-id="9907f-p105">以前，这种配置需要联合身份验证服务如 Azure 访问控制服务 (ACS) 在云中或环境中承载 Active Directory 联合身份验证服务 (AD FS) 转换为 SAML 1.1 SAML 2.0 令牌。Azure AD 现在可支持颁发的 SAML 1.1 令牌，该转换不再需要。上图显示 SharePoint 2016 用户在此配置中，演示不再媒介执行该转换的要求对身份验证的方式。</span><span class="sxs-lookup"><span data-stu-id="9907f-p105">Previously, this configuration would have required a federation service such as Azure Access Control Service (ACS) in the cloud or an environment that hosts Active Directory Federation Services (AD FS) to transform tokens from SAML 2.0 to SAML 1.1. This transformation is no longer required as Azure AD now enables issuing SAML 1.1 tokens. The diagram above shows how authentication works for SharePoint 2016 users in this configuration, demonstrating that there is no longer a requirement for an intermediary to perform this transformation.</span></span>

> [!NOTE]
> <span data-ttu-id="9907f-p106">此配置适用于是否在 Azure 虚拟机或内部部署承载于 SharePoint 场。它不需要打开确保用户之外的其他防火墙端口可以从其浏览器访问 Azure Active Directory。</span><span class="sxs-lookup"><span data-stu-id="9907f-p106">This configuration works whether the SharePoint farm is hosted in Azure virtual machines or on-premises. It does not require opening additional firewall ports other than ensuring users can access Azure Active Directory from their browser.</span></span>

<span data-ttu-id="9907f-124">有关 SharePoint 2016 辅助功能的信息，请参阅[SharePoint Server 2016 中的辅助功能准则](https://go.microsoft.com/fwlink/p/?LinkId=393123)。</span><span class="sxs-lookup"><span data-stu-id="9907f-124">For information about SharePoint 2016 accessibility, see [Accessibility Guidelines in SharePoint Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>

## <a name="configuration-overview"></a><span data-ttu-id="9907f-125">配置概述</span><span class="sxs-lookup"><span data-stu-id="9907f-125">Configuration overview</span></span>

<span data-ttu-id="9907f-126">按照以下常规步骤设置您的环境，以用作 SharePoint Server 2016 身份提供程序使用 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="9907f-126">Follow these general steps to set up your environment to use Azure AD as a SharePoint Server 2016 identity provider.</span></span>

1. <span data-ttu-id="9907f-127">创建新 Azure AD 目录或使用您现有的目录。</span><span class="sxs-lookup"><span data-stu-id="9907f-127">Create a new Azure AD directory or use your existing directory.</span></span>
2. <span data-ttu-id="9907f-128">确保您想要使用 Azure AD 安全的 web 应用程序的区域配置为使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="9907f-128">Ensure the zone for the web application that you want to secure with Azure AD is configured to use SSL.</span></span>
3. <span data-ttu-id="9907f-129">在 Azure AD 中创建新的企业应用程序。</span><span class="sxs-lookup"><span data-stu-id="9907f-129">Create a new enterprise application in Azure AD.</span></span>
4. <span data-ttu-id="9907f-130">在 SharePoint Server 2016 中配置新的受信任的身份提供程序。</span><span class="sxs-lookup"><span data-stu-id="9907f-130">Configure a new trusted identity provider in SharePoint Server 2016.</span></span>
5. <span data-ttu-id="9907f-131">设置 web 应用程序的权限。</span><span class="sxs-lookup"><span data-stu-id="9907f-131">Set the permissions for the web application.</span></span>
6. <span data-ttu-id="9907f-132">在 Azure AD 中添加的 SAML 1.1 令牌颁发策略。</span><span class="sxs-lookup"><span data-stu-id="9907f-132">Add a SAML 1.1 token issuance policy in Azure AD.</span></span>
7. <span data-ttu-id="9907f-133">验证新的提供程序。</span><span class="sxs-lookup"><span data-stu-id="9907f-133">Verify the new provider.</span></span>

<span data-ttu-id="9907f-134">以下各节介绍如何执行这些任务。</span><span class="sxs-lookup"><span data-stu-id="9907f-134">The following sections describe how to perform these tasks.</span></span>

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a><span data-ttu-id="9907f-135">步骤 1： 创建一个新 Azure AD 目录或使用您现有的目录</span><span class="sxs-lookup"><span data-stu-id="9907f-135">Step 1: Create a new Azure AD directory or use your existing directory</span></span>

<span data-ttu-id="9907f-p107">Azure 门户中 ([https://portal.azure.com](https://portal.azure.com))，创建一个新目录。提供组织名称、 初始域名的国家或地区。</span><span class="sxs-lookup"><span data-stu-id="9907f-p107">In the Azure Portal ([https://portal.azure.com](https://portal.azure.com)), create a new directory. Provide the organization name, initial domain name, and the country or region.</span></span>

![创建一个目录](images/SAML11/fig2-createdirectory.png) 

 <span data-ttu-id="9907f-p108">如果您已有一个目录，如用于 Microsoft Office 365 或 Microsoft Azure 订阅，则您可以改用该目录。您必须有权在目录中注册应用程序。</span><span class="sxs-lookup"><span data-stu-id="9907f-p108">If you already have a directory such as the one used for Microsoft Office 365 or your Microsoft Azure subscription, you can use that directory instead. You must have permissions to register applications in the directory.</span></span>

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a><span data-ttu-id="9907f-141">步骤 2： 确保您想要使用 Azure AD 安全的 web 应用程序的区域配置为使用 SSL</span><span class="sxs-lookup"><span data-stu-id="9907f-141">Step 2: Ensure the zone for the web application that you want to secure with Azure AD is configured to use SSL</span></span>

<span data-ttu-id="9907f-p109">本文是编写使用中[运行 SharePoint Server 2016 Azure 中的服务器场的高可用性](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)的参考体系结构。使用[本文](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)中所述将解决方案部署的文章的相应脚本创建在不使用 SSL 的网站。</span><span class="sxs-lookup"><span data-stu-id="9907f-p109">This article was written using the reference architecture in [Run a high availability SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint). The article’s accompanying scripts used to deploy the solution described in [this article](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint) create a site that does not use SSL.</span></span>  

<span data-ttu-id="9907f-p110">使用 SAML 要求应用程序配置为使用 SSL。如果您的 SharePoint web 应用程序未配置为使用 SSL，使用以下步骤创建新的自签名的证书配置 SSL 的 web 应用程序。此配置仅适用于实验室环境，并不是生产。生产环境应使用签名的证书。</span><span class="sxs-lookup"><span data-stu-id="9907f-p110">Using SAML requires the application be configured to use SSL. If your SharePoint web application is not configured to use SSL, use the following steps to create a new self-signed certificate to configure the web application for SSL. This configuration is only meant for a lab environment and is not intended for production. Production environments should use a signed certificate.</span></span>

1. <span data-ttu-id="9907f-p111">转到**管理中心** > **应用程序管理** > **管理 Web 应用程序**，并选择需要扩展，以使用 SSL 的 web 应用程序。选择 web 应用程序，然后单击**扩展功能区**按钮。扩展的 web 应用程序使用相同的 URL，但使用端口 443 使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="9907f-p111">Go to **Central Administration** > **Application Management** > **Manage Web Applications**, and choose the web application that needs to be extended to use SSL. Select the web application and click the **Extend ribbon** button. Extend the web application to use the same URL but use SSL with port 443.</span></span></br><span data-ttu-id="9907f-151">![扩展到其他 IIS 网站的 web 应用程序](images/SAML11/fig3-extendwebapptoiis.png)</span><span class="sxs-lookup"><span data-stu-id="9907f-151">![Extending the web app to another IIS site](images/SAML11/fig3-extendwebapptoiis.png)</span></span></br>
2. <span data-ttu-id="9907f-152">在 IIS 管理器 中，双击"服务器证书"。</span><span class="sxs-lookup"><span data-stu-id="9907f-152">In IIS Manager, double-click **Server Certificates**.</span></span>
3. <span data-ttu-id="9907f-p112">在**操作**窗格中，单击**创建自签名证书**。在指定的友好名称证书框中，键入证书的友好名称，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="9907f-p112">In the **Actions** pane, click **Create Self-Signed Certificate**. Type a friendly name for the certificate in the Specify a friendly name for the certificate box, and then click **OK**.</span></span>
4. <span data-ttu-id="9907f-155">从**编辑网站绑定**对话框中，确保 host name 是相同的友好名称，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="9907f-155">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following image.</span></span></br><span data-ttu-id="9907f-156">![在 IIS 中编辑网站绑定](images/SAML11/fig4-editsitebinding.png)</span><span class="sxs-lookup"><span data-stu-id="9907f-156">![Editing site binding in IIS](images/SAML11/fig4-editsitebinding.png)</span></span></br>

<span data-ttu-id="9907f-157">每个 SharePoint 场中的 web 前端服务器将需要在 IIS 中配置网站绑定的证书。</span><span class="sxs-lookup"><span data-stu-id="9907f-157">Each of the web front end servers in the SharePoint farm will require configuring the certificate for the site binding in IIS.</span></span>


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a><span data-ttu-id="9907f-158">步骤 3: Azure AD 中创建新的企业应用程序</span><span class="sxs-lookup"><span data-stu-id="9907f-158">Step 3: Create a new enterprise application in Azure AD</span></span>

1. <span data-ttu-id="9907f-p113">Azure 门户中 ([https://portal.azure.com](https://portal.azure.com))，打开 Azure AD 目录。单击**企业应用程序**，然后单击**新建应用程序**。选择**非库应用**程序。提供一个名称，如*SharePoint SAML 集成*并单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="9907f-p113">In the Azure Portal ([https://portal.azure.com](https://portal.azure.com)), open your Azure AD directory. Click **Enterprise Applications**, then click **New application**. Choose **Non-gallery application**. Provide a name such as *SharePoint SAML Integration* and click **Add**.</span></span></br><span data-ttu-id="9907f-163">![添加新的非库应用程序](images/SAML11/fig5-addnongalleryapp.png)</span><span class="sxs-lookup"><span data-stu-id="9907f-163">![Adding a new non-gallery application](images/SAML11/fig5-addnongalleryapp.png)</span></span></br>
2. <span data-ttu-id="9907f-p114">单击的单一登录链接在导航窗格中配置应用程序。将**单一登录模式**下拉列表更改为**基于 SAML 的单一登录**以显示应用程序的 SAML 配置属性。配置具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="9907f-p114">Click the Single sign-on link in the navigation pane to configure the application. Change the **Single Sign-on Mode** dropdown to **SAML-based Sign-on** to reveal the SAML configuration properties for the application. Configure with the following properties:</span></span></br>
    - <span data-ttu-id="9907f-167">标识符：`urn:sharepoint:portal.contoso.local`</span><span class="sxs-lookup"><span data-stu-id="9907f-167">Identifier: `urn:sharepoint:portal.contoso.local`</span></span>
    - <span data-ttu-id="9907f-168">答复 URL:`https://portal.contoso.local/_trust/default.aspx`</span><span class="sxs-lookup"><span data-stu-id="9907f-168">Reply URL: `https://portal.contoso.local/_trust/default.aspx`</span></span>
    - <span data-ttu-id="9907f-169">登录 URL:`https://portal.contoso.local/_trust/default.aspx`</span><span class="sxs-lookup"><span data-stu-id="9907f-169">Sign-on URL: `https://portal.contoso.local/_trust/default.aspx`</span></span>
    - <span data-ttu-id="9907f-170">用户标识符：`user.userprincipalname`</span><span class="sxs-lookup"><span data-stu-id="9907f-170">User Identifier: `user.userprincipalname`</span></span></br>
    - <span data-ttu-id="9907f-171">注意： 请记住，更改*portal.contoso.local*替换要保护的 SharePoint 网站的 URL 的 Url。</span><span class="sxs-lookup"><span data-stu-id="9907f-171">Note: Remember to change the URLs by replacing *portal.contoso.local* with the URL of the SharePoint site you want to secure.</span></span></br>
3. <span data-ttu-id="9907f-172">设置表格 （类似于下面的表 1），包括以下行：</span><span class="sxs-lookup"><span data-stu-id="9907f-172">Set up a table (similar to Table 1 below) that includes the following rows:</span></span></br> 
    - <span data-ttu-id="9907f-173">Realm</span><span class="sxs-lookup"><span data-stu-id="9907f-173">Realm</span></span>
    - <span data-ttu-id="9907f-174">SAML 签名证书文件的完整路径</span><span class="sxs-lookup"><span data-stu-id="9907f-174">Full path to SAML signing certificate file</span></span>
    - <span data-ttu-id="9907f-175">（替换 */wsfed* */saml2* ） SAML 单一登录服务 URL</span><span class="sxs-lookup"><span data-stu-id="9907f-175">SAML Single Sign-On service URL (replacing */saml2* with */wsfed*)</span></span>
    - <span data-ttu-id="9907f-176">应用程序的对象 id。</span><span class="sxs-lookup"><span data-stu-id="9907f-176">Application Object ID.</span></span> </br>
<span data-ttu-id="9907f-177">将*Identifier*值复制到的*领域*属性表中 (请参见表 1 下方)。</span><span class="sxs-lookup"><span data-stu-id="9907f-177">Copy the *Identifier* value into the *Realm* property into a table  (See Table 1 below.)</span></span>
4. <span data-ttu-id="9907f-178">保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="9907f-178">Save your changes.</span></span>
5. <span data-ttu-id="9907f-179">单击**配置 （应用程序名称）** 链接访问配置单一登录页。</span><span class="sxs-lookup"><span data-stu-id="9907f-179">Click the **Configure (app name)** link to access the Configure sign-on page.</span></span></br><span data-ttu-id="9907f-180">![在页面上配置单一登录](images/SAML11/fig7-configssopage.png)</span><span class="sxs-lookup"><span data-stu-id="9907f-180">![Configuring a single-sign on page](images/SAML11/fig7-configssopage.png)</span></span></br> 
    -  <span data-ttu-id="9907f-p115">单击**SAML 签名证书的原始**链接以下载扩展名.cer 文件 SAML 签名证书。复制并粘贴到数据表下载的文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="9907f-p115">Click the **SAML Signing Certificate - Raw** link to download the SAML Signing Certificate as a file with the .cer extension. Copy and paste the full path to the downloaded file into your table.</span></span>
    - <span data-ttu-id="9907f-183">复制并粘贴到 SAML 单一登录服务 URL 链接，替换 */wsfed*URL */saml2*部分。</span><span class="sxs-lookup"><span data-stu-id="9907f-183">Copy and paste the SAML Single Sign-On Service URL link into your, replacing the */saml2* portion of the URL with */wsfed*.</span></span></br>
6.  <span data-ttu-id="9907f-p116">导航到**属性**窗格中的应用程序。复制并粘贴到您在步骤 3 中设置的表的对象 ID 值。</span><span class="sxs-lookup"><span data-stu-id="9907f-p116">Navigate to the **Properties** pane for the application. Copy and paste the Object ID value into the table you set up in Step 3.</span></span></br><span data-ttu-id="9907f-186">![应用程序的属性窗格](images/SAML11/fig8-propertiespane.png)</span><span class="sxs-lookup"><span data-stu-id="9907f-186">![Properties pane for the application](images/SAML11/fig8-propertiespane.png)</span></span></br>
7. <span data-ttu-id="9907f-187">使用您捕获的值，请确保您在步骤 3 中设置表类似于下面的表 1。</span><span class="sxs-lookup"><span data-stu-id="9907f-187">Using the values you captured, make sure the table you set up in Step 3 resembles Table 1 below.</span></span>


| <span data-ttu-id="9907f-188">捕获的表 1： 值</span><span class="sxs-lookup"><span data-stu-id="9907f-188">Table 1: Values captured</span></span>  |  |
|---------|---------|
|<span data-ttu-id="9907f-189">Realm</span><span class="sxs-lookup"><span data-stu-id="9907f-189">Realm</span></span> | `urn:sharepoint:portal.contoso.local` |
|<span data-ttu-id="9907f-190">SAML 签名证书文件的完整路径</span><span class="sxs-lookup"><span data-stu-id="9907f-190">Full path to SAML signing certificate file</span></span> | `C:/temp/SharePoint SAML Integration.cer`  |
|<span data-ttu-id="9907f-191">SAML 单一登录服务 URL （替换 /wsfed /saml2）</span><span class="sxs-lookup"><span data-stu-id="9907f-191">SAML single sign-on service URL (replace /saml2 with /wsfed)</span></span> | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|<span data-ttu-id="9907f-192">应用程序对象 ID</span><span class="sxs-lookup"><span data-stu-id="9907f-192">Application Object ID</span></span> | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> <span data-ttu-id="9907f-p117">在 URL */saml2*值替换为 */wsfed*。*/Saml2*终结点将处理 SAML 2.0 令牌。*/Wsfed*终结点启用处理 SAML 1.1 令牌，并需要 SharePoint 2016 SAML 联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="9907f-p117">Replace the */saml2* value in the URL with */wsfed*. The */saml2* endpoint will process SAML 2.0 tokens. The */wsfed* endpoint enables processing SAML 1.1 tokens and is required for SharePoint 2016 SAML federation.</span></span>

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a><span data-ttu-id="9907f-196">步骤 4： 在 SharePoint Server 2016 中配置新的受信任的身份提供程序</span><span class="sxs-lookup"><span data-stu-id="9907f-196">Step 4: Configure a new trusted identity provider in SharePoint Server 2016</span></span>

<span data-ttu-id="9907f-p118">登录到 SharePoint Server 2016 服务器，然后打开 SharePoint 2016 命令行管理程序。填写 $realm、 $wsfedurl 和 $filepath 从表 1 的值并运行以下命令以配置新的受信任的身份提供程序。</span><span class="sxs-lookup"><span data-stu-id="9907f-p118">Sign into the SharePoint Server 2016 server and open the SharePoint 2016 Management Shell. Fill in the values of $realm, $wsfedurl, and $filepath from Table 1 and run the following commands to configure a new trusted identity provider.</span></span>

> [!TIP]
> <span data-ttu-id="9907f-199">如果您使用 PowerShell 新手，或要了解有关 PowerShell 的工作原理的详细信息，请参阅[SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="9907f-199">If you're new to using PowerShell or want to learn more about how PowerShell works, see [SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps).</span></span> 

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

<span data-ttu-id="9907f-200">接下来，执行以下步骤来启用的受信任的身份提供程序应用程序：</span><span class="sxs-lookup"><span data-stu-id="9907f-200">Next, follow these steps to enable the trusted identity provider for your application:</span></span>
1. <span data-ttu-id="9907f-201">在管理中心中，导航到**管理 Web 应用程序**，然后选择您希望与 Azure AD 安全的 web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9907f-201">In Central Administration, navigate to **Manage Web Application** and select the web application that you wish to secure with Azure AD.</span></span> 
2. <span data-ttu-id="9907f-202">在功能区中，单击**验证提供程序**，然后选择您想要使用的区域。</span><span class="sxs-lookup"><span data-stu-id="9907f-202">In the ribbon, click **Authentication Providers** and choose the zone that you wish to use.</span></span>
3. <span data-ttu-id="9907f-203">选择**受信任标识提供程序**并选择的标识提供程序只需注册名为*AzureAD*。</span><span class="sxs-lookup"><span data-stu-id="9907f-203">Select **Trusted Identity provider** and select the identify provider you just registered named *AzureAD*.</span></span>  
4. <span data-ttu-id="9907f-204">登录页 URL 设置，请选择**自定义登录页**，并提供"/_trust/"的值。</span><span class="sxs-lookup"><span data-stu-id="9907f-204">On the sign-in page URL setting, select **Custom sign in page** and provide the value "/_trust/".</span></span> 
5. <span data-ttu-id="9907f-205">单击“确定”****。</span><span class="sxs-lookup"><span data-stu-id="9907f-205">Click **OK**.</span></span>

![配置验证提供程序](images/SAML11/fig10-configauthprovider.png)

> [!IMPORTANT]
> <span data-ttu-id="9907f-p119">务必执行所有步骤，包括自定义登录设置"/_trust/"页中，如下所示。除非时遵循所有步骤，配置将无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="9907f-p119">It is important to follow all steps, including setting the custom sign in page to "/_trust/" as shown. The configuration will not work correctly unless all steps are followed.</span></span>

## <a name="step-5-set-the-permissions"></a><span data-ttu-id="9907f-209">步骤 5： 设置权限</span><span class="sxs-lookup"><span data-stu-id="9907f-209">Step 5: Set the permissions</span></span>

<span data-ttu-id="9907f-210">将登录到 Azure AD 和访问 SharePoint 的用户必须被授予访问应用程序。</span><span class="sxs-lookup"><span data-stu-id="9907f-210">The users who will log into Azure AD and access SharePoint must be granted access to the application.</span></span> 

1. <span data-ttu-id="9907f-p120">在 Azure 门户中，打开 Azure AD 目录。单击**企业应用程序**，然后单击**所有应用程序**。单击以前创建的应用程序 （SharePoint SAML 集成）。</span><span class="sxs-lookup"><span data-stu-id="9907f-p120">In the Azure Portal, open the Azure AD directory. Click **Enterprise Applications**, then click **All applications**. Click the application that you created previously (SharePoint SAML Integration).</span></span>
2. <span data-ttu-id="9907f-214">单击**用户和组**。</span><span class="sxs-lookup"><span data-stu-id="9907f-214">Click **Users and Groups**.</span></span> 
3. <span data-ttu-id="9907f-215">单击**添加用户**以添加用户或组拥有权限登录到 SharePoint 使用 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="9907f-215">Click **Add user** to add a user or group who will have permissions to log into SharePoint using Azure AD.</span></span>
4. <span data-ttu-id="9907f-216">选择用户或组，然后单击**分配**。</span><span class="sxs-lookup"><span data-stu-id="9907f-216">Select the user or group then click **Assign**.</span></span>
 
<span data-ttu-id="9907f-p121">用户已被授予在 Azure AD 权限，但还必须被授予 SharePoint 中的权限。使用以下步骤可设置访问 web 应用程序的权限。</span><span class="sxs-lookup"><span data-stu-id="9907f-p121">The user has been granted permission in Azure AD, but also must be granted permission in SharePoint. Use the following steps to set the permissions to access the web application.</span></span>

1. <span data-ttu-id="9907f-219">在管理中心中，单击“应用程序管理”****。</span><span class="sxs-lookup"><span data-stu-id="9907f-219">In Central Administration, click **Application Management**.</span></span>
2. <span data-ttu-id="9907f-220">在"应用程序管理"页上的"Web 应用程序"部分，单击"管理 Web 应用程序"。</span><span class="sxs-lookup"><span data-stu-id="9907f-220">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
3. <span data-ttu-id="9907f-221">单击适当的 Web 应用程序，然后单击"用户策略"。</span><span class="sxs-lookup"><span data-stu-id="9907f-221">Click the appropriate web application, and then click **User Policy**.</span></span>
4. <span data-ttu-id="9907f-222">在 Web 应用程序的策略，单击**添加用户**。</span><span class="sxs-lookup"><span data-stu-id="9907f-222">In Policy for Web Application, click **Add Users**.</span></span></br><span data-ttu-id="9907f-223">![按其名称声明搜索的用户](images/SAML11/fig11-searchbynameclaim.png)</span><span class="sxs-lookup"><span data-stu-id="9907f-223">![Searching for a user by their name claim](images/SAML11/fig11-searchbynameclaim.png)</span></span></br>
5. <span data-ttu-id="9907f-224">在"添加用户"对话框中，单击"区域"中的适当区域，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="9907f-224">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
6. <span data-ttu-id="9907f-225">在**Web 应用程序的策略**对话框的**选择用户**部分中，单击**浏览**图标。</span><span class="sxs-lookup"><span data-stu-id="9907f-225">In the **Policy for Web Application** dialog box, in the **Choose Users** section, click the **Browse** icon.</span></span>
7. <span data-ttu-id="9907f-226">在**查找**文本框中，键入您的目录中的用户的登录名并单击**搜索**。</span><span class="sxs-lookup"><span data-stu-id="9907f-226">In the **Find** textbox, type the sign-in name for a user in your directory and click **Search**.</span></span> </br><span data-ttu-id="9907f-227">示例： *demouser@blueskyabove.onmicrosoft.com*。</span><span class="sxs-lookup"><span data-stu-id="9907f-227">Example: *demouser@blueskyabove.onmicrosoft.com*.</span></span>
8. <span data-ttu-id="9907f-228">在列表视图中 AzureAD 标题下，选择名称属性，单击**添加**，然后单击**确定**关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="9907f-228">Under the AzureAD heading in the list view, select the name property and click **Add** then click **OK** to close the dialog.</span></span>
9. <span data-ttu-id="9907f-229">在权限中，单击**完全控制**。</span><span class="sxs-lookup"><span data-stu-id="9907f-229">In Permissions, click **Full Control**.</span></span></br><span data-ttu-id="9907f-230">![向声明用户授予完全控制](images/SAML11/fig12-grantfullcontrol.png)</span><span class="sxs-lookup"><span data-stu-id="9907f-230">![Granting full control to a claims user](images/SAML11/fig12-grantfullcontrol.png)</span></span></br>
10. <span data-ttu-id="9907f-231">单击“完成”****，然后单击“确定”****。</span><span class="sxs-lookup"><span data-stu-id="9907f-231">Click **Finish**, and then click **OK**.</span></span>

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a><span data-ttu-id="9907f-232">步骤 6: Azure AD 中添加的 SAML 1.1 令牌颁发策略</span><span class="sxs-lookup"><span data-stu-id="9907f-232">Step 6: Add a SAML 1.1 token issuance policy in Azure AD</span></span>

<span data-ttu-id="9907f-p122">在门户中创建 Azure AD 应用程序后，它默认为使用 SAML 2.0。SharePoint Server 2016 需要的 SAML 1.1 令牌格式。以下脚本将删除默认 SAML 2.0 策略，并向问题 SAML 1.1 令牌中添加新的策略。</span><span class="sxs-lookup"><span data-stu-id="9907f-p122">When the Azure AD application is created in the portal, it defaults to using SAML 2.0. SharePoint Server 2016 requires the SAML 1.1 token format. The following script will remove the default SAML 2.0 policy and add a new policy to issue SAML 1.1 tokens.</span></span> 

> <span data-ttu-id="9907f-p123">此代码需要下载附带的[示例演示与 Azure Active Directory 图表交互](https://github.com/kaevans/spsaml11/tree/master/scripts)。如果您从 GitHub 到 Windows 桌面 ZIP 文件下载脚本，请确保取消阻止`MSGraphTokenLifetimePolicy.psm1`脚本模块文件和`Initialize.ps1`脚本文件 （右键单击属性、 选择取消阻止，请单击确定）。![阻塞下载文件](images/SAML11/fig17-unblock.png)</span><span class="sxs-lookup"><span data-stu-id="9907f-p123">This code requires downloading the accompanying [samples demonstrating interacting with Azure Active Directory Graph](https://github.com/kaevans/spsaml11/tree/master/scripts). If you download the scripts as a ZIP file from GitHub to a Windows desktop, make sure to unblock the `MSGraphTokenLifetimePolicy.psm1` script module file and the `Initialize.ps1` script file (right-click Properties, choose Unblock, click OK). ![Unblocking downloaded files](images/SAML11/fig17-unblock.png)</span></span>

<span data-ttu-id="9907f-p124">示例脚本下载后，创建新的 PowerShell 脚本使用下面的代码，将下载的文件路径替换为占位符`Initialize.ps1`本地计算机上。应用程序的对象 ID 占位符替换为您在表 1 中输入的应用程序对象 ID。创建后，执行 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="9907f-p124">Once the sample script is downloaded, create a new PowerShell script using the following code, replacing the placeholder with the file path of the downloaded `Initialize.ps1` on your local machine. Replace the application object ID placeholder with the application object ID that you entered in Table 1. Once created, execute the PowerShell script.</span></span> 

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
> <span data-ttu-id="9907f-p125">未签名的 PowerShell 脚本，系统可能提示您设置执行策略。执行策略的详细信息，请参阅[有关执行策略](http://go.microsoft.com/fwlink/?LinkID=135170)。此外，您可能需要打开提升的命令提示符处，若要成功执行示例脚本中包含的命令。</span><span class="sxs-lookup"><span data-stu-id="9907f-p125">The PowerShell scripts are not signed and you may be prompted to set the execution policy. For more information on execution policies, see [About Execution Policies](http://go.microsoft.com/fwlink/?LinkID=135170). Additionally, you may need to open an elevated command prompt to successfully execute the commands contained in the sample scripts.</span></span>

<span data-ttu-id="9907f-p126">这些示例 PowerShell 命令是如何对图形 API 执行查询的示例。使用 Azure AD 的令牌颁发策略的详细信息，请参阅[图 API 参考 （英文） 策略操作](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy)。</span><span class="sxs-lookup"><span data-stu-id="9907f-p126">These sample PowerShell commands are examples of how to execute queries against the Graph API. For more details on Token Issuance Policies with Azure AD, see the [Graph API reference for operations on policy](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy).</span></span>

## <a name="step-7-verify-the-new-provider"></a><span data-ttu-id="9907f-247">步骤 7： 确认新的提供程序</span><span class="sxs-lookup"><span data-stu-id="9907f-247">Step 7: Verify the new provider</span></span>

<span data-ttu-id="9907f-p127">打开浏览器中为您在前面的步骤中配置的 web 应用程序的 URL。将重定向以登录到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="9907f-p127">Open a browser to the URL of the web application that you configured in the previous steps. You are redirected to sign into Azure AD.</span></span>

![登录为联盟配置的 Azure AD](images/SAML11/fig13-examplesignin.png)

<span data-ttu-id="9907f-251">系统要求您是否要保持登录状态。</span><span class="sxs-lookup"><span data-stu-id="9907f-251">You are asked if you want to stay signed in.</span></span>

![保持登录状态？](images/SAML11/fig14-staysignedin.png)

<span data-ttu-id="9907f-253">最后，您可以访问网站以从 Azure Active Directory 租户的用户身份登录。</span><span class="sxs-lookup"><span data-stu-id="9907f-253">Finally, you can access the site logged in as a user from your Azure Active Directory tenant.</span></span>

![用户登录到 SharePoint](images/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a><span data-ttu-id="9907f-255">管理证书</span><span class="sxs-lookup"><span data-stu-id="9907f-255">Managing certificates</span></span>
<span data-ttu-id="9907f-p128">务必要了解已配置为在第 4 步中的受信任的身份提供程序的签名证书已到期日期，并且必须进行更新。在续订证书，请参阅文章[管理联合单一登录 Azure Active Directory 中的证书](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs)的信息。一旦在 Azure AD 中已经续订证书，下载到本地文件，并使用以下脚本续订签名证书配置受信任的身份提供程序。</span><span class="sxs-lookup"><span data-stu-id="9907f-p128">It is important to understand that the signing certificate that was configured for the trusted identity provider in step 4 above has an expiration date and must be renewed. See the article [Manage certificates for federated single sign-on in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs) for information on certificate renewal. Once the certificate has been renewed in Azure AD, download to a local file and use the following script to configure the trusted identity provider with the renewed signing certificate.</span></span> 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a><span data-ttu-id="9907f-259">配置一个受信任的身份提供程序的多个 web 应用程序</span><span class="sxs-lookup"><span data-stu-id="9907f-259">Configuring one trusted identity provider for multiple web applications</span></span>
<span data-ttu-id="9907f-p129">配置适用于单个 web 应用程序，但如果您打算使用相同的受信任的身份提供程序的多个 web 应用程序需要其他配置。例如，假定我们已经扩展 web 应用程序使用的 URL `https://portal.contoso.local` ，现在要对用户进行身份验证`https://sales.contoso.local`以及。若要执行此操作，我们需要更新要服从 WReply 参数和 Azure AD 将答复 URL 中更新应用程序注册的标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="9907f-p129">The configuration works for a single web application, but needs additional configuration if you intend to use the same trusted identity provider for multiple web applications. For example, assume we had extended a web application to use the URL `https://portal.contoso.local` and now want to authenticate the users to `https://sales.contoso.local` as well. To do this, we need to update the identity provider to honor the WReply parameter and update the application registration in Azure AD to add a reply URL.</span></span>

1. <span data-ttu-id="9907f-p130">在 Azure 门户中，打开 Azure AD 目录。单击**应用程序注册**，然后单击**查看所有应用程序**。单击以前创建的应用程序 （SharePoint SAML 集成）。</span><span class="sxs-lookup"><span data-stu-id="9907f-p130">In the Azure Portal, open the Azure AD directory. Click **App registrations**, then click **View all applications**. Click the application that you created previously (SharePoint SAML Integration).</span></span>
2. <span data-ttu-id="9907f-266">单击**设置**。</span><span class="sxs-lookup"><span data-stu-id="9907f-266">Click **Settings**.</span></span>
3. <span data-ttu-id="9907f-267">在设置刀片中，单击**回复 Url**。</span><span class="sxs-lookup"><span data-stu-id="9907f-267">In the settings blade, click **Reply URLs**.</span></span> 
4. <span data-ttu-id="9907f-268">添加的其他 web 应用程序的 URL`/_trust/default.aspx`追加到 URL (如`https://sales.contoso.local/_trust/default.aspx`) 并单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="9907f-268">Add the URL for the additional web application with `/_trust/default.aspx` appended to the URL (such as `https://sales.contoso.local/_trust/default.aspx`) and click **Save**.</span></span> 
5. <span data-ttu-id="9907f-269">在 SharePoint 服务器上，打开**SharePoint 2016 命令行管理程序**并执行以下命令，将使用您以前使用的受信任的身份令牌颁发者的名称。</span><span class="sxs-lookup"><span data-stu-id="9907f-269">On the SharePoint server, open the **SharePoint 2016 Management Shell** and execute the following commands, using the name of the trusted identity token issuer that you used previously.</span></span>

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. <span data-ttu-id="9907f-p131">在管理中心，转到的 web 应用程序，并启用的现有的受信任的身份提供程序。请记住还配置为自定义登录页的登录页 URL `/_trust/`。</span><span class="sxs-lookup"><span data-stu-id="9907f-p131">In Central Administration, go to the web application and enable the existing trusted identity provider. Remember to also configure the sign-in page URL as a custom sign in page `/_trust/`.</span></span>
7. <span data-ttu-id="9907f-p132">在管理中心内，单击 web 应用程序，然后选择**用户策略**。添加具有适当权限的用户，如本文中前面所述。</span><span class="sxs-lookup"><span data-stu-id="9907f-p132">In Central Administration, click the web application and choose **User Policy**. Add a user with the appropriate permissions as demonstrated previously in this article.</span></span>

## <a name="fixing-people-picker"></a><span data-ttu-id="9907f-274">修复人员选取器</span><span class="sxs-lookup"><span data-stu-id="9907f-274">Fixing People Picker</span></span>
<span data-ttu-id="9907f-p133">用户现在可以登录到 SharePoint 2016 使用从 Azure AD 的标识，但仍有机会改善用户体验。例如，搜索用户在人员选取器中显示多个搜索结果。没有为每个声明映射中创建的 3 的声明类型的搜索结果。若要选择使用人员选取器的用户，必须完全键入用户姓名并选择**名称**声明结果。</span><span class="sxs-lookup"><span data-stu-id="9907f-p133">Users can now log into SharePoint 2016 using identities from Azure AD, but there are still opportunities for improvement to the user experience. For instance, searching for a user presents multiple search results in the people picker. There is a search result for each of the 3 claim types that were created in the claim mapping. To choose a user using the people picker, you must type their user name exactly and choose the **name** claim result.</span></span>

![声明搜索结果](images/SAML11/fig16-claimssearchresults.png)

<span data-ttu-id="9907f-p134">这会导致拼写错误，搜索值没有验证或意外选择错误声明类型，如**姓**分配的用户声明。这样可以防止用户成功访问资源。</span><span class="sxs-lookup"><span data-stu-id="9907f-p134">There is no validation on the values you search for, which can lead to misspellings or users accidentally choosing the wrong claim type to assign such as the **SurName** claim. This can prevent users from successfully accessing resources.</span></span>

<span data-ttu-id="9907f-p135">为了帮助这种情况下，没有打开源解决方案调用[AzureCP](https://yvand.github.io/AzureCP/) SharePoint 2016 提供自定义声明提供程序。它将使用 Azure AD 图形来解析用户输入并执行验证。有关详细信息[AzureCP](https://yvand.github.io/AzureCP/)。</span><span class="sxs-lookup"><span data-stu-id="9907f-p135">To assist with this scenario, there is an open-source solution called [AzureCP](https://yvand.github.io/AzureCP/) that provides a custom claims provider for SharePoint 2016. It will use the Azure AD Graph to resolve what users enter and perform validation. Learn more at [AzureCP](https://yvand.github.io/AzureCP/).</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="9907f-285">其他资源</span><span class="sxs-lookup"><span data-stu-id="9907f-285">Additional resources</span></span>

[<span data-ttu-id="9907f-286">了解 WS-Federation</span><span class="sxs-lookup"><span data-stu-id="9907f-286">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="9907f-287">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="9907f-287">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="9907f-288">加入讨论</span><span class="sxs-lookup"><span data-stu-id="9907f-288">Join the discussion</span></span>

|<span data-ttu-id="9907f-289">**联系我们**</span><span class="sxs-lookup"><span data-stu-id="9907f-289">**Contact us**</span></span>|<span data-ttu-id="9907f-290">**说明**</span><span class="sxs-lookup"><span data-stu-id="9907f-290">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="9907f-291">**你需要什么样的解决方案？**</span><span class="sxs-lookup"><span data-stu-id="9907f-291">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="9907f-p136">我们正在为跨多个 Microsoft 产品和服务的解决方案创建内容。请告诉我们你对我们的跨服务器解决方案的想法，或者发送电子邮件到 [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) 寻求具体的解决方案。</span><span class="sxs-lookup"><span data-stu-id="9907f-p136">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="9907f-294">**参加解决方案讨论**</span><span class="sxs-lookup"><span data-stu-id="9907f-294">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="9907f-p137">如果热衷于基于云的解决方案，请考虑加入云采用咨询委员会 (CAAB)，以便与充满活力的更大规模社区保持联络，其中包括 Microsoft 内容开发人员、行业专家和全球各地的客户。若要加入，请将自己添加为 Microsoft 技术社区的[云采用咨询委员会 (CAAB) 空间](https://aka.ms/caab)成员，并向我们 ([CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)) 发送电子邮件。任何人都可以阅读 [CAAB 博客](https://blogs.technet.com/b/solutions_advisory_board/)上与社区相关的内容。不过，CAAB 成员可获邀参加私人网络研讨会，了解新云采用资源和解决方案。</span><span class="sxs-lookup"><span data-stu-id="9907f-p137">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="9907f-299">**获取您在此处看到的图片**</span><span class="sxs-lookup"><span data-stu-id="9907f-299">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="9907f-p138">若要获取本文中图片的可编辑副本，请告诉我们，我们非常乐意发送副本。请通过电子邮件方式将请求（包括图片的 URL 和标题）发送到 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)。</span><span class="sxs-lookup"><span data-stu-id="9907f-p138">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   

