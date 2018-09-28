---
title: 如何配置本地 Exchange Server 以使用混合新式验证
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 3/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: 混合现代身份验证 (HMA)，是一种身份管理提供更安全的用户身份验证和授权，并适用于 Exchange server 内部部署混合部署的方法。
ms.openlocfilehash: cfacb5661ddf4a2ac61054582f0c2043d8fe7a5a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975190"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="25bb8-103">如何配置本地 Exchange Server 以使用混合新式验证</span><span class="sxs-lookup"><span data-stu-id="25bb8-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="25bb8-104">混合现代身份验证 (HMA)，是一种身份管理提供更安全的用户身份验证和授权，并适用于 Exchange server 内部部署混合部署的方法。</span><span class="sxs-lookup"><span data-stu-id="25bb8-104">Hybrid Modern Authentication (HMA), is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="25bb8-105">注意</span><span class="sxs-lookup"><span data-stu-id="25bb8-105">FYI</span></span>

<span data-ttu-id="25bb8-106">我们开始之前，请调用：</span><span class="sxs-lookup"><span data-stu-id="25bb8-106">Before we begin, I call:</span></span>
  
- <span data-ttu-id="25bb8-107">混合现代身份验证\>HMA</span><span class="sxs-lookup"><span data-stu-id="25bb8-107">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="25bb8-108">Exchange 内部部署\>EXCH</span><span class="sxs-lookup"><span data-stu-id="25bb8-108">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="25bb8-109">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="25bb8-109">Exchange Online \> EXO</span></span>
    
<span data-ttu-id="25bb8-110">此外，*如果中的图形本文具有已灰显或变暗这意味着，以灰色显示的元素未包括在 HMA 特定的配置对象*。</span><span class="sxs-lookup"><span data-stu-id="25bb8-110">Also,  *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration*  .</span></span> 
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="25bb8-111">启用混合现代身份验证</span><span class="sxs-lookup"><span data-stu-id="25bb8-111">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="25bb8-112">HMA 开启方法：</span><span class="sxs-lookup"><span data-stu-id="25bb8-112">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="25bb8-113">要确保在开始之前满足先决条件。</span><span class="sxs-lookup"><span data-stu-id="25bb8-113">Being sure you meet the prereqs before you begin.</span></span>
    
1. <span data-ttu-id="25bb8-p101">以来多个**必备组件**是常见的业务和 Exchange[混合现代身份验证概述和必备软件以便使用其本地 Skype 业务和 Exchange 服务器的](hybrid-modern-auth-overview.md)两个 Skype。在开始任何本文中的步骤之前执行此操作。</span><span class="sxs-lookup"><span data-stu-id="25bb8-p101">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this before you begin any of the steps in this article.</span></span>
    
2. <span data-ttu-id="25bb8-116">添加内部部署 web 服务 Url 为服务主体名称 (Spn) 在 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="25bb8-116">Adding on-premises web service URLs as Service Principal Names (SPNs) in Azure AD.</span></span>
    
3. <span data-ttu-id="25bb8-117">确保所有虚拟目录启用了 HMA</span><span class="sxs-lookup"><span data-stu-id="25bb8-117">Ensuring all Virtual Directories are enabled for HMA</span></span>
    
4. <span data-ttu-id="25bb8-118">检查 EvoSTS 身份验证服务器对象</span><span class="sxs-lookup"><span data-stu-id="25bb8-118">Checking for the EvoSTS Auth Server object</span></span>
    
5. <span data-ttu-id="25bb8-119">汇兑损益在启用 HMA</span><span class="sxs-lookup"><span data-stu-id="25bb8-119">Enabling HMA in EXCH.</span></span>
    
 <span data-ttu-id="25bb8-p102">**注释**您的 Office 版本是否支持 MA？请参阅[如何现代身份验证适用于 Office 2013 和 Office 2016 客户端应用程序](modern-auth-for-office-2013-and-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="25bb8-p102">**Note** Does your version of Office support MA? See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a><span data-ttu-id="25bb8-122">请确保您满足所有前要求</span><span class="sxs-lookup"><span data-stu-id="25bb8-122">Make sure you meet all the pre-reqs</span></span>

<span data-ttu-id="25bb8-p103">由于多个必备组件以针对常用于这两个 Skype 商业和 Exchange，查看[混合现代身份验证概述和使用它与业务和 Exchange 服务器的内部部署 Skype 的先决条件](hybrid-modern-auth-overview.md)。执行此*之前*开始任何本文中的步骤。</span><span class="sxs-lookup"><span data-stu-id="25bb8-p103">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="25bb8-125">添加内部部署 Azure AD 中为 Spn web 服务 Url</span><span class="sxs-lookup"><span data-stu-id="25bb8-125">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="25bb8-p104">运行命令的 Azure AD Spn。 Spn 的身份验证和授权过程中使用的客户端计算机和设备分配在本地 web 服务 Url。必须在 AAD （这包括内部和外部的命名空间） 中注册所有可能会用于从内部连接到 Azure Active Directory (AAD) 的 Url。</span><span class="sxs-lookup"><span data-stu-id="25bb8-p104">Run the commands that assign your on-premises web service URLs as Azure AD SPNs. SPNs are used by client machines and devices during authentication and authorization. All the URLs that might be used to connect from on-premises to Azure Active Directory (AAD) must be registered in AAD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="25bb8-p105">首先，收集所有 AAD 中添加所需的 Url。运行这些命令在本地：</span><span class="sxs-lookup"><span data-stu-id="25bb8-p105">First, gather all the URLs that you need to add in AAD. Run these commands on-premises:</span></span>
  
- <span data-ttu-id="25bb8-131">Get MapiVirtualDirectory |FL 服务器\*url\*</span><span class="sxs-lookup"><span data-stu-id="25bb8-131">Get-MapiVirtualDirectory | FL server,\*url\*</span></span>
    
- <span data-ttu-id="25bb8-132">Get-webservicesvirtualdirectory |FL 服务器\*url\*</span><span class="sxs-lookup"><span data-stu-id="25bb8-132">Get-WebServicesVirtualDirectory | FL server,\*url\*</span></span>
    
- <span data-ttu-id="25bb8-133">**Get-activesyncvirtualdirectory |FL 服务器\*url\***</span><span class="sxs-lookup"><span data-stu-id="25bb8-133">**Get-ActiveSyncVirtualDirectory | FL server,\*url\***</span></span>
    
- <span data-ttu-id="25bb8-134">Get-oabvirtualdirectory |FL 服务器\*url\*</span><span class="sxs-lookup"><span data-stu-id="25bb8-134">Get-OABVirtualDirectory | FL server,\*url\*</span></span>
    
<span data-ttu-id="25bb8-135">确保客户端可以连接到列为 HTTPS AAD 中的服务主体名称的 Url。</span><span class="sxs-lookup"><span data-stu-id="25bb8-135">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="25bb8-136">首先，连接到 AAD 与[这些说明](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell)。</span><span class="sxs-lookup"><span data-stu-id="25bb8-136">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span>
    
2. <span data-ttu-id="25bb8-137">对于 Exchange 相关的 Url，键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="25bb8-137">For your Exchange related URLs, type the following command:</span></span>
    
- <span data-ttu-id="25bb8-138">Get MsolServicePrincipal-AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 |选择-ExpandProperty ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="25bb8-138">Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames</span></span>
    
<span data-ttu-id="25bb8-p106">执行此命令，应包括 https:// 的输出的注释 （和更高版本比较的屏幕快照） \* 自动发现。*yourdomain* .com \* 和 https:// *mail.yourdomain.com* URL，但主要包含开头 00000002-0000-0ff1-ce00-000000000000 的 Spn /。从内部部署的缺少的 https:// Url 时我们将需要这些特定记录添加到此列表。</span><span class="sxs-lookup"><span data-stu-id="25bb8-p106">Take note of (and screenshot for later comparison) the output of this command, which should include an https:// \*autodiscover. *yourdomain*  .com \*  and https://  *mail.yourdomain.com*  URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/. If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span> 
  
3. <span data-ttu-id="25bb8-142">如果看不到您内部和外部 MAPI/HTTP、 EWS、 ActiveSync、 OAB 和自动发现记录此列表中的，您必须添加它们使用下面的命令 (示例 Url 是`mail.corp.contoso.com`和`owa.contoso.com`，但您必须**替换为您自己的示例 Url** ):</span><span class="sxs-lookup"><span data-stu-id="25bb8-142">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```
- $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
- $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
- $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
- $x.ServicePrincipalnames.Add("https://eas.contoso.com/")
- Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. <span data-ttu-id="25bb8-p107">确认通过 Get MsolServicePrincipal 命令从步骤 2 再次运行，并将输出通过查找已添加新记录。比较列表 / 屏幕截图从之前对新列表的 Spn （您还可以屏幕截图新列表的记录）。如果您已成功完成，您将看到列表中的两个新 Url。通过我们的示例转，Spn 的列表将现已包括特定的 Url`https://mail.corp.contoso.com`和`https://owa.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="25bb8-p107">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="25bb8-147">确认正确配置虚拟目录</span><span class="sxs-lookup"><span data-stu-id="25bb8-147">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="25bb8-148">现在验证中正确启用 OAuth 在所有虚拟目录 Outlook 上的 Exchange 可能使用通过运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="25bb8-148">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```
Get-MapiVirtualDirectory | FL server,\*url\*,\*auth\* 
Get-WebServicesVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-OABVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-AutoDiscoverVirtualDirectory | FL server,\*oauth\*
```

<span data-ttu-id="25bb8-149">检查以确保**OAuth**的输出启用每个这些 VDirs，它看起来如下所示 （和需要查看的重要一点是 OAuth）;</span><span class="sxs-lookup"><span data-stu-id="25bb8-149">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth');</span></span> 
  
 <span data-ttu-id="25bb8-150">**[PS]C:\Windows\system32\>Get MapiVirtualDirectory |fl 服务器\*url\*，\*身份验证\***</span><span class="sxs-lookup"><span data-stu-id="25bb8-150">**[PS] C:\Windows\system32\>Get-MapiVirtualDirectory | fl server,\*url\*,\*auth\***</span></span>
  
 <span data-ttu-id="25bb8-151">**服务器： EX1**</span><span class="sxs-lookup"><span data-stu-id="25bb8-151">**Server : EX1**</span></span>
  
 <span data-ttu-id="25bb8-152">**InternalUrl:`https://mail.contoso.com/mapi`**</span><span class="sxs-lookup"><span data-stu-id="25bb8-152">**InternalUrl : `https://mail.contoso.com/mapi`**</span></span>
  
 <span data-ttu-id="25bb8-153">**ExternalUrl:`https://mail.contoso.com/mapi`**</span><span class="sxs-lookup"><span data-stu-id="25bb8-153">**ExternalUrl : `https://mail.contoso.com/mapi`**</span></span>
  
 <span data-ttu-id="25bb8-154">**IISAuthenticationMethods: {Ntlm、 OAuth、 Negotiate}**</span><span class="sxs-lookup"><span data-stu-id="25bb8-154">**IISAuthenticationMethods : {Ntlm, OAuth, Negotiate}**</span></span>
  
 <span data-ttu-id="25bb8-155">**InternalAuthenticationMethods: {Ntlm、 OAuth、 Negotiate}**</span><span class="sxs-lookup"><span data-stu-id="25bb8-155">**InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}**</span></span>
  
 <span data-ttu-id="25bb8-156">**ExternalAuthenticationMethods: {Ntlm、 OAuth、 Negotiate}**</span><span class="sxs-lookup"><span data-stu-id="25bb8-156">**ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}**</span></span>
  
<span data-ttu-id="25bb8-157">如果您需将其使用相关的命令，然后再继续添加 OAuth 缺少来自任何服务器和任何四个虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="25bb8-157">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding.</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="25bb8-158">确认存在 EvoSTS 身份验证服务器对象</span><span class="sxs-lookup"><span data-stu-id="25bb8-158">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="25bb8-p108">返回到此最后一个命令的本地 Exchange 命令行管理程序。现在您可以验证本地 evoSTS 身份验证提供程序有一项：</span><span class="sxs-lookup"><span data-stu-id="25bb8-p108">Return to the on-premises Exchange Management Shell for this last command. Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
`Get-AuthServer | where {$_.Name -eq "EvoSts"}`
    
<span data-ttu-id="25bb8-p109">输出应显示的名称 EvoSts 认证服务器和已启用状态应该为 True。如果您看不到此，您应下载并运行混合配置向导的最新版本。</span><span class="sxs-lookup"><span data-stu-id="25bb8-p109">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True. If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="25bb8-163">**重要**如果您在您的环境中运行 Exchange 2010，不会创建 EvoSTS 身份验证提供程序。</span><span class="sxs-lookup"><span data-stu-id="25bb8-163">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="25bb8-164">启用 HMA</span><span class="sxs-lookup"><span data-stu-id="25bb8-164">Enable HMA</span></span>

<span data-ttu-id="25bb8-165">在 Exchange Management Shell 中，在本地运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="25bb8-165">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a><span data-ttu-id="25bb8-166">“验证”</span><span class="sxs-lookup"><span data-stu-id="25bb8-166">Verify</span></span>

<span data-ttu-id="25bb8-p110">一旦您启用 HMA，下次登录时的客户端将使用新的身份验证流。请注意刚打开 HMA 不会触发重新进行身份验证的任何客户端。客户端重新进行身份验证基于身份验证令牌和/或拥有的证书的生存期。</span><span class="sxs-lookup"><span data-stu-id="25bb8-p110">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="25bb8-p111">您还应右键单击该图标的 Outlook 客户端 （还在 Windows 通知任务栏中） 的同时按住 CTRL 键，然后单击连接状态。查找针对的身份验证类型的客户端的 SMTP 地址持有者\*，它代表用于 OAuth 持有者令牌。</span><span class="sxs-lookup"><span data-stu-id="25bb8-p111">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="25bb8-p112">**注释**需要配置 HMA Skype for Business？您将需要两篇文章： 一个列出了[受支持的拓扑](https://technet.microsoft.com/en-us/library/mt803262.aspx)，，另一个演示[如何执行配置](configure-skype-for-business-for-hybrid-modern-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="25bb8-p112">**Note** Need to configure Skype for Business with HMA? You'll need two articles: One that lists [supported topologies](https://technet.microsoft.com/en-us/library/mt803262.aspx), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
  

## <a name="related-topics"></a><span data-ttu-id="25bb8-174">相关主题</span><span class="sxs-lookup"><span data-stu-id="25bb8-174">Related topics</span></span>

[<span data-ttu-id="25bb8-175">混合现代身份验证概述和使用内部部署 Skype 使用的业务和 Exchange 服务器的先决条件</span><span class="sxs-lookup"><span data-stu-id="25bb8-175">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>](hybrid-modern-auth-overview.md) 
  

