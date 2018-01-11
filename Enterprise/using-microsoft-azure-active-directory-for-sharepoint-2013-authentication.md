---
title: "将 Microsoft Azure Active Directory 用于 SharePoint 2013 身份验证"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: "摘要：了解如何使用 Azure 访问控制服务，在 Azure Active Directory 中对 SharePoint Server 2013 用户进行身份验证。"
ms.openlocfilehash: 9025eb53f4d8e37403c48416f41adbe35fa9fa01
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="using-microsoft-azure-active-directory-for-sharepoint-2013-authentication"></a><span data-ttu-id="36eec-103">将 Microsoft Azure Active Directory 用于 SharePoint 2013 身份验证</span><span class="sxs-lookup"><span data-stu-id="36eec-103">Using Microsoft Azure Active Directory for SharePoint 2013 authentication</span></span>

 <span data-ttu-id="36eec-104">**摘要：**了解如何使用 Azure 访问控制服务，在 Azure Active Directory 中对 SharePoint Server 2013 用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="36eec-104">**Summary:** Learn how to use the Azure Access Control Service to authenticate your SharePoint Server 2013 users with Azure Active Directory.</span></span>
  
<span data-ttu-id="36eec-p101">通过使用不同的标识提供程序对用户进行身份验证，可以更轻松地管理用户。设想一下，使用您信任但是由其他人来管理的标识提供程序有多么方便。例如，您可能对访问云中的 SharePoint Server 2013 的用户使用一种身份验证类型，对内部部署环境中的 SharePoint 2013 用户使用另一种身份验证类型。Azure 访问控制服务使这些选择成为可能。</span><span class="sxs-lookup"><span data-stu-id="36eec-p101">It can be easier to manage your users by authenticating them with different identity providers. Consider how convenient it can be to use an identity provider that you trust, but someone else manages. For example, you could have one type of authentication for users who access SharePoint Server 2013 in the cloud and another for SharePoint 2013 users in your on-premises environment. The Azure Access Control Service makes these choices possible.</span></span> 
  
<span data-ttu-id="36eec-p102">本文介绍如何使用 Azure 访问控制服务，在 Azure AD 中对 SharePoint 2013 用户进行身份验证，而不是您的内部部署 Active Directory。在此配置中，Azure AD 成为 SharePoint 2013 的受信任标识提供程序。此配置增加了一个与 SharePoint 2013 安装本身使用的 Active Directory 身份验证独立的用户身份验证方法。要从本文中受益，您应该熟悉 WS-Federation。有关详细信息，请参阅[了解 WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)。</span><span class="sxs-lookup"><span data-stu-id="36eec-p102">This article explains how you can use the Azure Access Control Service to authenticate your SharePoint 2013 users with Azure AD, instead of your on-premises Active Directory. In this configuration, Azure AD becomes a trusted identity provider for SharePoint 2013. This configuration adds a user authentication method that is separate from Active Directory authentication used by the SharePoint 2013 installation itself. To benefit from this article, you should be familiar with WS-Federation. For more information, see [Understanding WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052).</span></span>
  
<span data-ttu-id="36eec-114">下图显示了如何为此配置中的 SharePoint 2013 用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="36eec-114">The following figure shows how authentication works for SharePoint 2013 users in this configuration.</span></span>
  
![已通过 Azure Active Directory 身份验证的用户](images/SP_AzureAD.png)
  
<span data-ttu-id="36eec-116">本文中使用的示例由 Azure 卓越中心 Microsoft 架构师 Kirk Evans 提供。</span><span class="sxs-lookup"><span data-stu-id="36eec-116">The example used in this article is provided by Kirk Evans, Microsoft Architect for the Azure Center of Excellence.</span></span> 
  
<span data-ttu-id="36eec-117">有关 SharePoint 2013 辅助功能的信息，请参阅 [SharePoint 2013 的辅助功能](https://go.microsoft.com/fwlink/p/?LinkId=393123)。</span><span class="sxs-lookup"><span data-stu-id="36eec-117">For information about SharePoint 2013 accessibility, see [Accessibility for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393123).</span></span>
  
## <a name="configuration-overview"></a><span data-ttu-id="36eec-118">配置概述</span><span class="sxs-lookup"><span data-stu-id="36eec-118">Configuration overview</span></span>

<span data-ttu-id="36eec-119">按照下列常规步骤，将您的环境设置为使用 Azure AD 作为 SharePoint 2013 标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="36eec-119">Follow these general steps to set up your environment to use Azure AD as a SharePoint 2013 identity provider.</span></span>
  
1. <span data-ttu-id="36eec-120">创建新的 Azure AD 租户和命名空间。</span><span class="sxs-lookup"><span data-stu-id="36eec-120">Create a new Azure AD tenant and namespace.</span></span>
    
2. <span data-ttu-id="36eec-121">添加 WS-Federation 标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="36eec-121">Add a WS-Federation identity provider.</span></span>
    
3. <span data-ttu-id="36eec-122">将 SharePoint 添加为信赖方应用程序。</span><span class="sxs-lookup"><span data-stu-id="36eec-122">Add SharePoint as a relying party application.</span></span>
    
4. <span data-ttu-id="36eec-123">创建自签名的证书以用于 SSL。</span><span class="sxs-lookup"><span data-stu-id="36eec-123">Create a self-signed certificate to use for SSL.</span></span>
    
5. <span data-ttu-id="36eec-124">创建用于基于声明的身份验证的规则组。</span><span class="sxs-lookup"><span data-stu-id="36eec-124">Create a rule group for claims-based authentication.</span></span>
    
6. <span data-ttu-id="36eec-125">配置 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="36eec-125">Configure the X.509 certificate.</span></span>
    
7. <span data-ttu-id="36eec-126">创建声明映射。</span><span class="sxs-lookup"><span data-stu-id="36eec-126">Create a claim mapping.</span></span>
    
8. <span data-ttu-id="36eec-127">为新的标识提供程序配置 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="36eec-127">Configure SharePoint for the new identity provider.</span></span>
    
9. <span data-ttu-id="36eec-128">设置权限。</span><span class="sxs-lookup"><span data-stu-id="36eec-128">Set the permissions.</span></span>
    
10. <span data-ttu-id="36eec-129">验证新的提供程序。</span><span class="sxs-lookup"><span data-stu-id="36eec-129">Verify the new provider.</span></span>
    
## <a name="create-azure-ad-tenant-and-namespace"></a><span data-ttu-id="36eec-130">创建 Azure AD 租户和命名空间</span><span class="sxs-lookup"><span data-stu-id="36eec-130">Create Azure AD tenant and namespace</span></span>

<span data-ttu-id="36eec-p103">执行下列步骤，创建一个新的 Azure AD 租户和关联的命名空间。在此示例中，我们使用命名空间"blueskyabove"。</span><span class="sxs-lookup"><span data-stu-id="36eec-p103">Use the following steps to create a new Azure AD tenant and an associated namespace. In this example, we use the namespace "blueskyabove."</span></span> 
  
1. <span data-ttu-id="36eec-133">在 Azure 管理门户中，单击"Active Directory"，然后创建一个新的 Azure AD 租户。</span><span class="sxs-lookup"><span data-stu-id="36eec-133">In the Azure Management Portal, click **Active Directory**, and then create a new Azure AD tenant.</span></span>
    
2. <span data-ttu-id="36eec-134">单击"访问控制命名空间"，并创建新的命名空间。</span><span class="sxs-lookup"><span data-stu-id="36eec-134">Click **Access Control Namespaces**, and create a new namespace.</span></span> 
    
3. <span data-ttu-id="36eec-p104">单击底部栏中的"管理"。这应该会打开此位置：https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web。</span><span class="sxs-lookup"><span data-stu-id="36eec-p104">Click **Manage** on the bottom bar. This should open this location, https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web.</span></span>
    
4. <span data-ttu-id="36eec-p105">打开 Windows PowerShell。使用 Windows PowerShell 的 Microsoft Online Services 模块，这是为 Windows PowerShell cmdlet 安装 Azure 的先决条件。</span><span class="sxs-lookup"><span data-stu-id="36eec-p105">Open Windows PowerShell. Use the Microsoft Online Services Module for Windows PowerShell, which is a prerequisite for installing the Azure for Windows PowerShell cmdlets.</span></span>
    
5. <span data-ttu-id="36eec-139">从 Windows PowerShell 命令提示符处，键入以下命令： `Connect-Msolservice`，然后键入您的凭据。</span><span class="sxs-lookup"><span data-stu-id="36eec-139">From the Windows PowerShell command prompt, type the command:  `Connect-Msolservice`, and then type your credentials.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="36eec-140">有关如何将 Azure 用于 Windows PowerShell cmdlet 的其他信息，请参阅[使用 Windows PowerShell 管理 Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=393124)。</span><span class="sxs-lookup"><span data-stu-id="36eec-140">For additional information about how to use Azure for Windows PowerShell cmdlets, see [Manage Azure AD using Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=393124).</span></span> 
  
6. <span data-ttu-id="36eec-141">在 Windows PowerShell 命令提示符处，键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="36eec-141">From a Windows PowerShell command prompt, type the following commands:</span></span>
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    <span data-ttu-id="36eec-142">下图说明了输出结果。</span><span class="sxs-lookup"><span data-stu-id="36eec-142">The following figure illustrates the output result.</span></span>
    
     ![创建服务主体名称](images/ServicePrincipalNames.jpg)
  
## <a name="add-a-ws-federation-identity-provider-to-the-namespace"></a><span data-ttu-id="36eec-144">将 WS-Federation 标识提供程序添加到命名空间</span><span class="sxs-lookup"><span data-stu-id="36eec-144">Add a WS-Federation identity provider to the namespace</span></span>

<span data-ttu-id="36eec-145">执行下列步骤，将 WS-Federation 标识提供程序添加到 blueskyabove 命名空间。</span><span class="sxs-lookup"><span data-stu-id="36eec-145">Use the following steps to add a new WS-Federation identity provider to the blueskyabove namespace.</span></span>
  
1. <span data-ttu-id="36eec-146">在 Azure 管理门户中，转到"Active Directory">"访问控制命名空间"，单击"新建实例"，然后单击"管理"。</span><span class="sxs-lookup"><span data-stu-id="36eec-146">From the Azure management portal, go to **Active Directory** > **Access Control Namespaces**, click **Create a new instance**, and then click **Manage**.</span></span>
    
2. <span data-ttu-id="36eec-147">在 Azure 访问控制门户上，单击"标识提供程序">"添加"，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="36eec-147">From the Azure Access Control portal, click **Identity Providers** > **Add**, as illustrated in the following figure.</span></span>
    
     ![Azure 中的“标识提供程序”对话框](images/Identity.jpg)
  
3. <span data-ttu-id="36eec-149">单击"WS-Federation 标识提供程序"（如下图中所示），然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="36eec-149">Click **WS-Federation identity provider**, as illustrated in the following figure, and then click **Next**.</span></span>
    
     ![“添加标识提供程序”设置](images/AddIdentity.jpg)
  
4. <span data-ttu-id="36eec-p106">填写显示名称和登录链接文本，然后单击"保存" 。对于 WS-Federation 元数据 URL，键入 https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml。下图说明了该设置。</span><span class="sxs-lookup"><span data-stu-id="36eec-p106">Fill out the display name and logon link text, and then click **Save**. For the WS-Federation metadata URL, type https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml. The following figure illustrates the setting.</span></span>
    
     ![联合身份提供程序](images/FederationIdentity.jpg)
  
## <a name="add-sharepoint-as-a-relying-party-application"></a><span data-ttu-id="36eec-155">将 SharePoint 添加为信赖方应用程序</span><span class="sxs-lookup"><span data-stu-id="36eec-155">Add SharePoint as a relying party application</span></span>

<span data-ttu-id="36eec-156">执行下列步骤，将 SharePoint 添加为信赖方应用程序。</span><span class="sxs-lookup"><span data-stu-id="36eec-156">Use the following steps to add SharePoint as a relying party application.</span></span>
  
<span data-ttu-id="36eec-157">有关信赖方应用程序设置的其他信息，请参阅[信赖方应用程序](https://go.microsoft.com/fwlink/p/?LinkId=393125)。</span><span class="sxs-lookup"><span data-stu-id="36eec-157">For additional information about relying party application settings, see [Relying Party Applications](https://go.microsoft.com/fwlink/p/?LinkId=393125).</span></span>
  
1. <span data-ttu-id="36eec-158">在 Azure 访问控制门户上，单击"信赖方应用程序"，然后单击"添加"，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="36eec-158">From the Azure Access Control portal, click **Relying party applications**, and then click **Add**, as illustrated in the following figure.</span></span>
    
     ![“信赖方应用”设置](images/RelyingPartyApplications.jpg)
  
## <a name="create-a-self-signed-certificate-to-use-for-ssl"></a><span data-ttu-id="36eec-160">创建自签名的证书以用于 SSL</span><span class="sxs-lookup"><span data-stu-id="36eec-160">Create a self-signed certificate to use for SSL</span></span>

<span data-ttu-id="36eec-161">执行下列步骤，创建一个新的自签名证书，以用于通过 SSL 的安全通信。</span><span class="sxs-lookup"><span data-stu-id="36eec-161">Use the following steps to create a new, self-signed certificate to use for secure communications over SSL.</span></span>
  
1. <span data-ttu-id="36eec-162">将 Web 应用程序扩展为使用相同的 URL 作为 PublishingSite，但使用端口为 443 的 SSL，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="36eec-162">Extend the web application to use the same URL as PublishingSite, but use SSL with port 443, as illustrated in the following figure.</span></span>
    
     ![扩展应用程序的设置](images/ExtendWebApp.jpg)
  
2. <span data-ttu-id="36eec-164">在 IIS 管理器 中，双击"服务器证书"。</span><span class="sxs-lookup"><span data-stu-id="36eec-164">In IIS Manager, double-click **Server Certificates**.</span></span>
    
3. <span data-ttu-id="36eec-p107">在"操作"窗格中，单击"创建自签名证书"。在"为证书指定一个好记名称"框中为证书键入一个好记名称，然后单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="36eec-p107">In the **Actions** pane, click **Create Self-Signed Certificate**. Type a friendly name for the certificate in the **Specify a friendly name for the certificate** box, and then click **OK**.</span></span>
    
4. <span data-ttu-id="36eec-167">从"编辑网站绑定"对话框中，确保主机名与指定的好记名称相同，如以下各图中所示。</span><span class="sxs-lookup"><span data-stu-id="36eec-167">From the **Edit Site Binding** dialog box, ensure the host name is the same as the friendly name, as illustrated in the following figures.</span></span>
    
     ![自签名证书向导](images/SelfSignedCert.jpg)
  
     ![“编辑绑定”对话框中的主机名](images/SelfSignedCert1.jpg)
  
5. <span data-ttu-id="36eec-170">在 Azure 管理门户上，单击您想要配置的虚拟机，然后单击"终结点"。</span><span class="sxs-lookup"><span data-stu-id="36eec-170">From the Azure management portal, click the virtual machine that you want to configure, and then click **Endpoints**.</span></span>
    
6. <span data-ttu-id="36eec-171">单击"添加"，然后单击"-->"（对于"下一步"）。</span><span class="sxs-lookup"><span data-stu-id="36eec-171">Click **Add**, and then click **-->** (for Next).</span></span>
    
7. <span data-ttu-id="36eec-172">在"名称"中，为该终结点键入一个名称。</span><span class="sxs-lookup"><span data-stu-id="36eec-172">In **Name**, type a name for the endpoint.</span></span>
    
8. <span data-ttu-id="36eec-p108">在"公用端口"和"专用端口"中，键入您想要使用的端口号，然后单击复选标记以完成。这些数字可能会有所不同。出于本文的目的，我们将使用 443，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="36eec-p108">In **Public Port** and **Private Port**, type the port numbers that you want to use, and then click the check mark to complete. These numbers can be different. For the purposes of this article, we are using 443, as illustrated in the following figure.</span></span>
    
     ![Azure 中的终结点设置](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="36eec-177">有关如何将终结点添加到 Azure 中的虚拟机的其他信息，请参阅[如何将终结点安装到虚拟机上](https://go.microsoft.com/fwlink/p/?LinkId=393126)。</span><span class="sxs-lookup"><span data-stu-id="36eec-177">For additional information about how to add an endpoint to a virtual machine in Azure, see [How to Set Up Endpoints to a Virtual Machine](https://go.microsoft.com/fwlink/p/?LinkId=393126).</span></span> 
  
9. <span data-ttu-id="36eec-178">从访问控制服务门户中，添加信赖方，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="36eec-178">From the Access Control services portal, add a relying party, as illustrated in the following figure.</span></span>
    
     ![“添加信赖方”应用程序设置](images/AddRelyingParty.jpg)
  
## <a name="create-a-rule-group-for-claims-based-authentication"></a><span data-ttu-id="36eec-180">创建用于基于声明的身份验证的规则组</span><span class="sxs-lookup"><span data-stu-id="36eec-180">Create a rule group for claims-based authentication</span></span>

<span data-ttu-id="36eec-181">执行下列步骤，创建一个新的规则组，以控制基于声明的身份验证。</span><span class="sxs-lookup"><span data-stu-id="36eec-181">Use the following steps to create a new rule group to control claims-based authentication.</span></span>
  
1. <span data-ttu-id="36eec-182">在左侧窗格中，单击"规则组"，然后单击"添加"。</span><span class="sxs-lookup"><span data-stu-id="36eec-182">In the left pane, click **Rule groups**, and then click **Add**.</span></span>
    
2. <span data-ttu-id="36eec-p109">键入规则组的名称，再依次单击“保存”****和“生成”****。本文使用的是“Default Rule Group for. spvms.cloudapp.net”****，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="36eec-p109">Type a name for the rule group, click **Save**, and then click **Generate**. For the purposes of this article, we are using **Default Rule Group for. spvms.cloudapp.net**, as illustrated in the following figure.</span></span>
    
     ![Azure 中的“规则组”设置](images/RuleGroup.jpg)
  
     ![选择“生成”后的规则](images/GenerateRules.jpg)
  
    > [!NOTE]
    > <span data-ttu-id="36eec-187">有关如何创建规则组的其他信息，请参阅[规则组和规则](https://go.microsoft.com/fwlink/p/?LinkId=393128)。</span><span class="sxs-lookup"><span data-stu-id="36eec-187">For additional information about how to create rule groups, see [Rule Groups and Rules](https://go.microsoft.com/fwlink/p/?LinkId=393128).</span></span> 
  
3. <span data-ttu-id="36eec-p110">单击您想要更改的规则组，然后单击您想要更改的声明规则。出于本文的目的，我们将声明规则添加到组，以将 **name** 传递为 **upn** ，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="36eec-p110">Click the rule group that you want to change, and then click the claim rule that you want to change. For the purposes of this article, we add a claim rule to the group to pass **name** as **upn**, as illustrated by the following figure.</span></span>
    
     ![Azure 访问控制的声明规则](images/ClaimRules.jpg)
  
4. <span data-ttu-id="36eec-191">删除名为 **upn** 的现有声明规则并保留 **Name Claim to UPN** 规则，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="36eec-191">Delete the existing claim rule named **upn**, and leave the **Name Claim to UPN** rule, as illustrated by the following figure.</span></span>
    
     ![Azure 访问控制的规则设置](images/ClaimToUPN.jpg)
  
## <a name="configure-the-x509-certificate"></a><span data-ttu-id="36eec-193">配置 X.509 证书</span><span class="sxs-lookup"><span data-stu-id="36eec-193">Configure the X.509 certificate</span></span>

<span data-ttu-id="36eec-194">执行下列步骤，将 X.509 证书配置为用于令牌签名。</span><span class="sxs-lookup"><span data-stu-id="36eec-194">Use the following steps to configure the X.509 certificate to use for token signing.</span></span>
  
1. <span data-ttu-id="36eec-195">在访问控制服务窗格中，在"开发"下单击"应用程序集成"。</span><span class="sxs-lookup"><span data-stu-id="36eec-195">In the Access Control Service pane, under **Development**, click **Application integration**.</span></span>
    
2. <span data-ttu-id="36eec-196">在“终结点引用”****中，找到与 Azure 租户关联的“Federation.xml”****，再复制浏览器地址栏中的位置。</span><span class="sxs-lookup"><span data-stu-id="36eec-196">In **Endpoint Reference**, locate the **Federation.xml** that is associated with your Azure tenant, and then copy the location in the address bar of a browser.</span></span>
    
3. <span data-ttu-id="36eec-197">在 **Federation.xml** 文件中，找到 **RoleDescriptor** 部分，并复制 _<X509Certificate>_ 元素中的信息，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="36eec-197">In the **Federation.xml** file, locate the **RoleDescriptor** section, and copy the information from the _<X509Certificate>_ element, as illustrated in the following figure.</span></span>
    
     ![Federation.xml 文件的 X509 Certificate 元素](images/X509Cert.jpg)
  
4. <span data-ttu-id="36eec-199">从驱动器 C:\\ 的根目录中，创建一个名为 **Certificates** 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="36eec-199">From the root of drive C:\\, create a folder named **Certificates**.</span></span>
    
5. <span data-ttu-id="36eec-200">将 X509Certificate 信息保存到文件夹 C:\\Certificates 中，文件名为 **AcsTokenSigning.cer** 。</span><span class="sxs-lookup"><span data-stu-id="36eec-200">Save the X509Certificate information to the folder C:\\Certificates with the file name, **AcsTokenSigning.cer**.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="36eec-201">必须使用 .cer 扩展名保存文件名。</span><span class="sxs-lookup"><span data-stu-id="36eec-201">The file name must be saved with a .cer extension.</span></span> 
  
     ![将 X509Certificate 元素另存为文件](images/X509Cert_Save.jpg)
  
## <a name="create-a-claim-mapping-by-using-windows-powershell"></a><span data-ttu-id="36eec-203">使用 Windows PowerShell 创建声明映射</span><span class="sxs-lookup"><span data-stu-id="36eec-203">Create a claim mapping by using Windows PowerShell</span></span>

<span data-ttu-id="36eec-204">执行下列步骤，使用 Windows PowerShell 创建声明映射。</span><span class="sxs-lookup"><span data-stu-id="36eec-204">Use the following steps to create a claim mapping by using Windows PowerShell.</span></span>
  
<span data-ttu-id="36eec-205">确认您具有以下成员身份：</span><span class="sxs-lookup"><span data-stu-id="36eec-205">Verify that you have the following memberships:</span></span>
  
1. <span data-ttu-id="36eec-206">SQL Server 实例上的 **securityadmin** 固定服务器角色。</span><span class="sxs-lookup"><span data-stu-id="36eec-206">**securityadmin** fixed server role on the SQL Server instance.</span></span>
    
2. <span data-ttu-id="36eec-207">要更新的所有数据库上的 **db_owner** 固定数据库角色。</span><span class="sxs-lookup"><span data-stu-id="36eec-207">**db_owner** fixed database role on all databases that will be updated.</span></span>
    
3. <span data-ttu-id="36eec-208">运行 Windows PowerShell cmdlet 的服务器上的 Administrators 组。</span><span class="sxs-lookup"><span data-stu-id="36eec-208">Administrators group on the server on which you are running the Windows PowerShell cmdlets.</span></span>
    
<span data-ttu-id="36eec-209">管理员可使用 **Add-SPShellAdmin** cmdlet 来授予使用 SharePoint 2013 cmdlet 的权限。</span><span class="sxs-lookup"><span data-stu-id="36eec-209">An administrator can use the **Add-SPShellAdmin** cmdlet to grant permissions to use SharePoint 2013 cmdlets.</span></span>
  
> [!NOTE]
> <span data-ttu-id="36eec-p111">如果您不具有这些权限，请联系您的安装管理员或 SQL Server 管理员来请求权限。有关 Windows PowerShell 权限的其他信息，请参阅 [Add-SPShellAdmin]((http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx))。</span><span class="sxs-lookup"><span data-stu-id="36eec-p111">If you do not have permissions, contact your Setup administrator or SQL Server administrator to request permissions. For additional information about Windows PowerShell permissions, see [Add-SPShellAdmin]((http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx)).</span></span> 
  
1. <span data-ttu-id="36eec-212">在"开始"菜单上，单击"所有程序"。</span><span class="sxs-lookup"><span data-stu-id="36eec-212">From the **Start** menu, click **All Programs**.</span></span>
    
2. <span data-ttu-id="36eec-213">单击"Microsoft SharePoint 2013 产品"。</span><span class="sxs-lookup"><span data-stu-id="36eec-213">Click **Microsoft SharePoint 2013 Products**.</span></span>
    
3. <span data-ttu-id="36eec-214">单击“SharePoint 2013 命令行管理程序”****。</span><span class="sxs-lookup"><span data-stu-id="36eec-214">Click **SharePoint 2013 Management Shell**.</span></span>
    
4. <span data-ttu-id="36eec-215">在 Windows PowerShell 命令提示符处，键入以下命令以创建声明映射：</span><span class="sxs-lookup"><span data-stu-id="36eec-215">At the Windows PowerShell command prompt, type the following commands to create a claim mapping:</span></span>
    
  ```
  $cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("c:\\certificates\\AcsTokenSigning.cer")
  ```

  ```
  New-SPTrustedRootAuthority -Name "ACS BlueSkyAbove Token Signing" -Certificate $cert
  ```

  ```
  $map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -IncomingClaimTypeDisplayName "UPN" -SameAsIncoming
  ```

  ```
  $map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
  ```

  ```
  $map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
  ```

  ```
  $realm = "urn:sharepoint:spvms"
  ```

  ```
  $ap = New-SPTrustedIdentityTokenIssuer -Name "ACS Provider" -Description "SharePoint secured by SAML in ACS" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl "https://blueskyabove.accesscontrol.windows.net/v2/wsfederation" -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
  ```

## <a name="configure-sharepoint-for-the-new-identity-provider"></a><span data-ttu-id="36eec-216">为新的标识提供程序配置 SharePoint</span><span class="sxs-lookup"><span data-stu-id="36eec-216">Configure SharePoint for the new identity provider</span></span>

<span data-ttu-id="36eec-217">执行下列步骤，将您的 SharePoint 安装配置为 Azure AD 的新标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="36eec-217">Use the following steps to configure your SharePoint installation to the new identity provider for Azure AD.</span></span>
  
1. <span data-ttu-id="36eec-218">确认执行此过程的用户帐户是 SharePoint 组“服务器场管理员”的成员。</span><span class="sxs-lookup"><span data-stu-id="36eec-218">Verify that the user account that is performing this procedure is a member of the Farm Administrators SharePoint group.</span></span>
    
2. <span data-ttu-id="36eec-219">在管理中心的主页上，单击"应用程序管理"。</span><span class="sxs-lookup"><span data-stu-id="36eec-219">In Central Administration, on the home page, click **Application Management**.</span></span>
    
3. <span data-ttu-id="36eec-220">在"应用程序管理"页上的"Web 应用程序"部分，单击"管理 Web 应用程序"。</span><span class="sxs-lookup"><span data-stu-id="36eec-220">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
4. <span data-ttu-id="36eec-221">单击适当的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="36eec-221">Click the appropriate web application.</span></span>
    
5. <span data-ttu-id="36eec-222">从功能区中单击"身份验证提供程序"。</span><span class="sxs-lookup"><span data-stu-id="36eec-222">From the ribbon, click **Authentication Providers**.</span></span>
    
6. <span data-ttu-id="36eec-p112">在"区域"下单击区域的名称，例如"Default"。</span><span class="sxs-lookup"><span data-stu-id="36eec-p112">Under **Zone**, click the name of the zone. For example, **Default**.</span></span>
    
7. <span data-ttu-id="36eec-p113">在“编辑身份验证”****页上的“声明身份验证类型”****部分中，选择“受信任的标识提供程序”****，再单击提供程序名称（本文使用的是“ACS 提供程序”****）。单击“确定”****。</span><span class="sxs-lookup"><span data-stu-id="36eec-p113">On the **Edit Authentication** page, in the **Claims Authentication Types** section, select **Trusted Identity provider**, and then click the name of your provider, which for purposes of this article is **ACS Provider**. Click **OK**.</span></span>
    
8. <span data-ttu-id="36eec-227">下图说明了 **Trusted Provider** 设置。</span><span class="sxs-lookup"><span data-stu-id="36eec-227">The following figure illustrates the **Trusted Provider** setting.</span></span>
    
![Web 应用程序中的“受信任提供程序”设置](images/AddProvider_Azure.jpg)
  
## <a name="set-the-permissions"></a><span data-ttu-id="36eec-229">设置权限</span><span class="sxs-lookup"><span data-stu-id="36eec-229">Set the permissions</span></span>

<span data-ttu-id="36eec-230">执行下列步骤，设置访问 Web 应用程序的权限。</span><span class="sxs-lookup"><span data-stu-id="36eec-230">Use the following steps to set the permissions to access the web application.</span></span>
  
1. <span data-ttu-id="36eec-231">在管理中心的主页上，单击"应用程序管理"。</span><span class="sxs-lookup"><span data-stu-id="36eec-231">In Central Administration, on the home page, click **Application Management**.</span></span>
    
2. <span data-ttu-id="36eec-232">在"应用程序管理"页上的"Web 应用程序"部分，单击"管理 Web 应用程序"。</span><span class="sxs-lookup"><span data-stu-id="36eec-232">On the **Application Management** page, in the **Web Applications** section, click **Manage web applications**.</span></span>
    
3. <span data-ttu-id="36eec-233">单击适当的 Web 应用程序，然后单击"用户策略"。</span><span class="sxs-lookup"><span data-stu-id="36eec-233">Click the appropriate web application, and then click **User Policy**.</span></span>
    
4. <span data-ttu-id="36eec-234">在"Web 应用程序的策略"中，单击"添加用户"。</span><span class="sxs-lookup"><span data-stu-id="36eec-234">In **Policy for Web Application**, click **Add Users**.</span></span>
    
5. <span data-ttu-id="36eec-235">在"添加用户" 对话框中，单击"区域"中的适当区域，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="36eec-235">In the **Add Users** dialog box, click the appropriate zone in **Zones**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="36eec-236">在"添加用户" 对话框中，键入 user2@blueskyabove.onmicrosoft.com (ACS Provider)。</span><span class="sxs-lookup"><span data-stu-id="36eec-236">In the **Add Users** dialog box, typeuser2@blueskyabove.onmicrosoft.com (ACS Provider).</span></span>
    
7. <span data-ttu-id="36eec-237">在"权限"中，单击"完全控制"。</span><span class="sxs-lookup"><span data-stu-id="36eec-237">In **Permissions**, click **Full Control**.</span></span>
    
8. <span data-ttu-id="36eec-238">单击"完成"，然后单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="36eec-238">Click **Finish**, and then click **OK**.</span></span>
    
<span data-ttu-id="36eec-239">下图显示了现有 Web 应用程序的"添加用户"部分。</span><span class="sxs-lookup"><span data-stu-id="36eec-239">The following figure illustrates the **Add Users** section of an existing web application.</span></span>
  
![将用户添加到现有 Web 应用程序](images/AddUsers_Azure.jpg)
  
## <a name="verify-the-new-provider"></a><span data-ttu-id="36eec-241">验证新的提供程序</span><span class="sxs-lookup"><span data-stu-id="36eec-241">Verify the new provider</span></span>

<span data-ttu-id="36eec-242">执行下列步骤，确保新的身份验证提供程序在出现登录提示时显示，确认新的标识提供程序正常运行。</span><span class="sxs-lookup"><span data-stu-id="36eec-242">Use the following steps to verify that the new identity provider is working by ensuring that the new authentication provider appears on the sign-in prompt.</span></span>
  
1. <span data-ttu-id="36eec-243">使用名为 **Blue Sky Above** 的新提供程序登录，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="36eec-243">Sign in by using the new provider named **Blue Sky Above**, as illustrated in the following figure.</span></span>
    
     ![登录对话框显示了受信任的新提供程序](images/BlueSkyAbove.jpg)
  
## <a name="additional-resources"></a><span data-ttu-id="36eec-245">其他资源</span><span class="sxs-lookup"><span data-stu-id="36eec-245">Additional resources</span></span>

[<span data-ttu-id="36eec-246">了解 WS-Federation</span><span class="sxs-lookup"><span data-stu-id="36eec-246">Understanding WS-Federation</span></span>](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[<span data-ttu-id="36eec-247">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="36eec-247">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a><span data-ttu-id="36eec-248">加入讨论</span><span class="sxs-lookup"><span data-stu-id="36eec-248">Join the discussion</span></span>

|<span data-ttu-id="36eec-249">**联系我们**</span><span class="sxs-lookup"><span data-stu-id="36eec-249">**Contact us**</span></span>|<span data-ttu-id="36eec-250">**说明**</span><span class="sxs-lookup"><span data-stu-id="36eec-250">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="36eec-251">**您需要什么样的解决方案？**</span><span class="sxs-lookup"><span data-stu-id="36eec-251">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="36eec-p114">我们正在为跨多个 Microsoft 产品和服务的解决方案创建内容。请告诉我们您对我们的跨服务器解决方案的想法，或者发送电子邮件到 [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) 寻求具体的解决方案。</span><span class="sxs-lookup"><span data-stu-id="36eec-p114">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="36eec-254">**参加解决方案讨论**</span><span class="sxs-lookup"><span data-stu-id="36eec-254">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="36eec-p115">如果热衷于基于云的解决方案，请考虑加入云采用咨询委员会 (CAAB)，以便与充满活力的更大规模社区保持联络，其中包括 Microsoft 内容开发人员、行业专家和全球各地的客户。若要加入，请将自己添加为 Microsoft 技术社区的[云采用咨询委员会 (CAAB) 空间]((https://aka.ms/caab))成员，并向我们 ([CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)) 发送电子邮件。任何人都可以阅读 [CAAB 博客]((https://blogs.technet.com/b/solutions_advisory_board/))上与社区相关的内容。不过，CAAB 成员可获邀参加私人网络研讨会，了解新云采用资源和解决方案。</span><span class="sxs-lookup"><span data-stu-id="36eec-p115">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space]((https://aka.ms/caab)) of the Microsoft Tech Community and send us a quick email at [CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog]((https://blogs.technet.com/b/solutions_advisory_board/)). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="36eec-258">**获取您在此处看到的图片**</span><span class="sxs-lookup"><span data-stu-id="36eec-258">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="36eec-p116">若要获取本文中图片的可编辑副本，请告诉我们，我们非常乐意发送副本。请通过电子邮件方式将请求（包括图片的 URL 和标题）发送到 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)。</span><span class="sxs-lookup"><span data-stu-id="36eec-p116">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   

