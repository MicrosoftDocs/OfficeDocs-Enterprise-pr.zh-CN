---
title: 如何配置本地 Exchange Server 以使用混合新式验证
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/16/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: 混合新式身份验证（HMA）是一种身份管理方法，它提供更安全的用户身份验证和授权，并可用于 Exchange server 本地混合部署。
ms.openlocfilehash: 4348de3fbec5917c2b13af3f93bf79ad898af017
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502587"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="c4377-103">如何配置本地 Exchange Server 以使用混合新式验证</span><span class="sxs-lookup"><span data-stu-id="c4377-103">How to configure Exchange Server on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="c4377-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* </span><span class="sxs-lookup"><span data-stu-id="c4377-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c4377-105">混合新式身份验证（HMA）是一种标识管理方法，可提供更安全的用户身份验证和授权，并可用于 Exchange server 本地混合部署。</span><span class="sxs-lookup"><span data-stu-id="c4377-105">Hybrid Modern Authentication (HMA) is a method of identity management that offers more secure user authentication and authorization, and is available for Exchange server on-premises hybrid deployments.</span></span>
  
## <a name="fyi"></a><span data-ttu-id="c4377-106">仅供参考</span><span class="sxs-lookup"><span data-stu-id="c4377-106">FYI</span></span>

<span data-ttu-id="c4377-107">在开始之前，我称之为：</span><span class="sxs-lookup"><span data-stu-id="c4377-107">Before we begin, I call:</span></span>
  
- <span data-ttu-id="c4377-108">混合新式身份验证 \> HMA</span><span class="sxs-lookup"><span data-stu-id="c4377-108">Hybrid Modern Authentication \> HMA</span></span>

- <span data-ttu-id="c4377-109">Exchange 本地 \> EXCH</span><span class="sxs-lookup"><span data-stu-id="c4377-109">Exchange on-premises \> EXCH</span></span>

- <span data-ttu-id="c4377-110">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="c4377-110">Exchange Online \> EXO</span></span>

<span data-ttu-id="c4377-111">此外，*如果本文中的图形有一个 "灰显" 或 "变暗" 的对象，则表示以灰色显示的元素不包含在 HMA 的特定配置中*。</span><span class="sxs-lookup"><span data-stu-id="c4377-111">Also, *if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray is not included in HMA-specific configuration* .</span></span>
  
## <a name="enabling-hybrid-modern-authentication"></a><span data-ttu-id="c4377-112">启用混合新式身份验证</span><span class="sxs-lookup"><span data-stu-id="c4377-112">Enabling Hybrid Modern Authentication</span></span>

<span data-ttu-id="c4377-113">启用 HMA 的打开方式：</span><span class="sxs-lookup"><span data-stu-id="c4377-113">Turning HMA on means:</span></span>
  
1. <span data-ttu-id="c4377-114">在开始之前，请务必满足先决条件。</span><span class="sxs-lookup"><span data-stu-id="c4377-114">Being sure you meet the prereqs before you begin.</span></span>

1. <span data-ttu-id="c4377-115">由于很多**先决条件**对于 Skype for Business 和 exchange 都是常见的，因此[混合新式身份验证概述和用于在本地 Skype For business 和 exchange 服务器上使用它的先决条件](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c4377-115">Since many **prerequisites** are common for both Skype for Business and Exchange, [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="c4377-116">在开始本文中的任何步骤之前，请执行此操作。</span><span class="sxs-lookup"><span data-stu-id="c4377-116">Do this before you begin any of the steps in this article.</span></span>

1. <span data-ttu-id="c4377-117">在 Azure AD 中将本地 web 服务 Url 添加为**服务主体名称（spn）** 。</span><span class="sxs-lookup"><span data-stu-id="c4377-117">Adding on-premises web service URLs as **Service Principal Names (SPNs)** in Azure AD.</span></span>

1. <span data-ttu-id="c4377-118">确保为 HMA 启用所有虚拟目录</span><span class="sxs-lookup"><span data-stu-id="c4377-118">Ensuring all Virtual Directories are enabled for HMA</span></span>

1. <span data-ttu-id="c4377-119">检查 EvoSTS Auth Server 对象</span><span class="sxs-lookup"><span data-stu-id="c4377-119">Checking for the EvoSTS Auth Server object</span></span>

1. <span data-ttu-id="c4377-120">在 EXCH 中启用 HMA。</span><span class="sxs-lookup"><span data-stu-id="c4377-120">Enabling HMA in EXCH.</span></span>

 <span data-ttu-id="c4377-121">**注释**您的 Office 版本是否支持 MA？</span><span class="sxs-lookup"><span data-stu-id="c4377-121">**Note** Does your version of Office support MA?</span></span> <span data-ttu-id="c4377-122">请参阅[如何在 office 2013 和 office 2016 客户端应用程序中运行新式验证](modern-auth-for-office-2013-and-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="c4377-122">See [How modern authentication works for Office 2013 and Office 2016 client apps](modern-auth-for-office-2013-and-2016.md).</span></span>
  
## <a name="make-sure-you-meet-all-the-prerequisites"></a><span data-ttu-id="c4377-123">请确保满足所有先决条件</span><span class="sxs-lookup"><span data-stu-id="c4377-123">Make sure you meet all the prerequisites</span></span>

<span data-ttu-id="c4377-124">由于很多先决条件对于 Skype for business 和 Exchange 都是常见的，因此请参阅[混合新式身份验证概述和在本地 skype for business 和 exchange 服务器上使用它的先决条件](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c4377-124">Since many prerequisites are common for both Skype for Business and Exchange, review [Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="c4377-125">在开始本文中的任何步骤*之前*，请执行此操作。</span><span class="sxs-lookup"><span data-stu-id="c4377-125">Do this  *before*  you begin any of the steps in this article.</span></span>
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="c4377-126">在 Azure AD 中将本地 web 服务 Url 添加为 Spn</span><span class="sxs-lookup"><span data-stu-id="c4377-126">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="c4377-127">运行将本地 web 服务 Url 分配为 Azure AD Spn 的命令。</span><span class="sxs-lookup"><span data-stu-id="c4377-127">Run the commands that assign your on-premises web service URLs as Azure AD SPNs.</span></span> <span data-ttu-id="c4377-128">在身份验证和授权过程中，客户端计算机和设备使用 Spn。</span><span class="sxs-lookup"><span data-stu-id="c4377-128">SPNs are used by client machines and devices during authentication and authorization.</span></span> <span data-ttu-id="c4377-129">所有可用于从本地连接到 Azure Active Directory （Azure AD）的 Url 都必须在 Azure AD 中注册（这包括内部和外部命名空间）。</span><span class="sxs-lookup"><span data-stu-id="c4377-129">All the URLs that might be used to connect from on-premises to Azure Active Directory (Azure AD) must be registered in Azure AD (this includes both internal and external namespaces).</span></span>
  
<span data-ttu-id="c4377-130">首先，收集您需要在 AAD 中添加的所有 Url。</span><span class="sxs-lookup"><span data-stu-id="c4377-130">First, gather all the URLs that you need to add in AAD.</span></span> <span data-ttu-id="c4377-131">在本地运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="c4377-131">Run these commands on-premises:</span></span>
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
Get-AutodiscoverVirtualDirectory | FL server,*url*
Get-OutlookAnywhere | FL server,*url*
```
    
<span data-ttu-id="c4377-132">确保客户端可以连接的 Url 在 AAD 中列为 HTTPS 服务主体名称。</span><span class="sxs-lookup"><span data-stu-id="c4377-132">Ensure the URLs clients may connect to are listed as HTTPS service principal names in AAD.</span></span>
  
1. <span data-ttu-id="c4377-133">首先，使用[这些说明](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)连接到 AAD。</span><span class="sxs-lookup"><span data-stu-id="c4377-133">First, connect to AAD with [these instructions](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span>

 <span data-ttu-id="c4377-134">**注释**您需要使用此页面中的_connect-msolservice_选项，才能使用下面的命令。</span><span class="sxs-lookup"><span data-stu-id="c4377-134">**Note** You need to use the _Connect-MsolService_ option from this page to be able to use the command below.</span></span>

2. <span data-ttu-id="c4377-135">对于与 Exchange 相关的 Url，请键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="c4377-135">For your Exchange related URLs, type the following command:</span></span>

```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

<span data-ttu-id="c4377-136">记下（和屏幕截图以便稍后比较）此命令的输出应包括 https:// *autodiscover.yourdomain.com*和 Https:// *mail.yourdomain.com* URL，但主要是由以 00000002-0000-0Ff1-ce00-000000000000/开头的 spn 组成。</span><span class="sxs-lookup"><span data-stu-id="c4377-136">Take note of (and screenshot for later comparison) the output of this command, which should include an https://  *autodiscover.yourdomain.com*  and https://  *mail.yourdomain.com* URL, but mostly consist of SPNs that begin with 00000002-0000-0ff1-ce00-000000000000/.</span></span> <span data-ttu-id="c4377-137">如果缺少内部部署中的 https://Url，我们需要将这些特定记录添加到此列表中。</span><span class="sxs-lookup"><span data-stu-id="c4377-137">If there are https:// URLs from your on-premises that are missing we will need to add those specific records to this list.</span></span>
  
3. <span data-ttu-id="c4377-138">如果您在此列表中看不到内部和外部 MAPI/HTTP、EWS、ActiveSync、OAB 和自动发现记录，则必须使用下面的命令添加它们（示例 Url 是 ' `mail.corp.contoso.com` ' and ' `owa.contoso.com` '，但您需要将**示例 url 替换为您自己的 url** ）：</span><span class="sxs-lookup"><span data-stu-id="c4377-138">If you don't see your internal and external MAPI/HTTP, EWS, ActiveSync, OAB and Autodiscover records in this list, you must add them using the command below (the example URLs are '`mail.corp.contoso.com`' and '`owa.contoso.com`', but you'd **replace the example URLs with your own** ):</span></span> <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```

4. <span data-ttu-id="c4377-139">再次运行步骤2中的 New-msolserviceprincipal 命令，并查看输出，以验证新记录是否已添加。</span><span class="sxs-lookup"><span data-stu-id="c4377-139">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="c4377-140">将列表/屏幕截图从早到新的 Spn 列表进行比较（您还可能会为您的记录提供新列表的屏幕截图）。</span><span class="sxs-lookup"><span data-stu-id="c4377-140">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="c4377-141">如果成功，您将在列表中看到两个新的 Url。</span><span class="sxs-lookup"><span data-stu-id="c4377-141">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="c4377-142">根据我们的示例，Spn 列表现在将包含特定的 Url `https://mail.corp.contoso.com` 和 `https://owa.contoso.com` 。</span><span class="sxs-lookup"><span data-stu-id="c4377-142">Going by our example, the list of SPNs will now include the specific URLs  `https://mail.corp.contoso.com`  and  `https://owa.contoso.com`.</span></span> 
  
## <a name="verify-virtual-directories-are-properly-configured"></a><span data-ttu-id="c4377-143">验证是否正确配置了虚拟目录</span><span class="sxs-lookup"><span data-stu-id="c4377-143">Verify Virtual Directories are Properly Configured</span></span>

<span data-ttu-id="c4377-144">现在，验证是否已在 Outlook 的所有虚拟目录上通过运行以下命令，正确启用了 OAuth：</span><span class="sxs-lookup"><span data-stu-id="c4377-144">Now verify OAuth is properly enabled in Exchange on all of the Virtual Directories Outlook might use by running the following commands:</span></span>

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

<span data-ttu-id="c4377-145">检查输出以确保每个 VDirs 上启用了**OAuth** ，它将如下所示（要查看的关键内容是 "OAuth"）：</span><span class="sxs-lookup"><span data-stu-id="c4377-145">Check the output to make sure **OAuth** is enabled on each of these VDirs, it will look something like this (and the key thing to look at is 'OAuth'):</span></span>

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*

Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
<span data-ttu-id="c4377-146">如果任何服务器和四个虚拟目录中的任何一个都缺少 OAuth，则需要在继续之前使用相关命令添加它（[MapiVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-mapivirtualdirectory?view=exchange-ps)、 [set-webservicesvirtualdirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-webservicesvirtualdirectory?view=exchange-ps)、 [set-oabvirtualdirectory](https://docs.microsoft.com/powershell/module/exchange/email-addresses-and-address-books/set-oabvirtualdirectory?view=exchange-ps)和[set-new-autodiscovervirtualdirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-autodiscovervirtualdirectory?view=exchange-ps)）。</span><span class="sxs-lookup"><span data-stu-id="c4377-146">If OAuth is missing from any server and any of the four virtual directories then you need to add it using the relevant commands before proceeding ([Set-MapiVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-mapivirtualdirectory?view=exchange-ps), [Set-WebServicesVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-webservicesvirtualdirectory?view=exchange-ps), [Set-OABVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/email-addresses-and-address-books/set-oabvirtualdirectory?view=exchange-ps), and [Set-AutodiscoverVirtualDirectory](https://docs.microsoft.com/powershell/module/exchange/client-access-servers/set-autodiscovervirtualdirectory?view=exchange-ps)).</span></span>
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a><span data-ttu-id="c4377-147">确认 EvoSTS Auth Server 对象是否存在</span><span class="sxs-lookup"><span data-stu-id="c4377-147">Confirm the EvoSTS Auth Server Object is Present</span></span>

<span data-ttu-id="c4377-148">返回到此最后一个命令的内部部署 Exchange 命令行管理程序。</span><span class="sxs-lookup"><span data-stu-id="c4377-148">Return to the on-premises Exchange Management Shell for this last command.</span></span> <span data-ttu-id="c4377-149">现在，您可以验证您的内部部署是否具有 evoSTS 身份验证提供程序的条目：</span><span class="sxs-lookup"><span data-stu-id="c4377-149">Now you can validate that your on-premises has an entry for the evoSTS authentication provider:</span></span>
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

<span data-ttu-id="c4377-150">您的输出应显示名称 EvoSts 的 Get-authserver，并且 "已启用" 状态应为 True。</span><span class="sxs-lookup"><span data-stu-id="c4377-150">Your output should show an AuthServer of the Name EvoSts and the 'Enabled' state should be True.</span></span> <span data-ttu-id="c4377-151">如果看不到此内容，应下载并运行 "混合配置" 向导的最新版本。</span><span class="sxs-lookup"><span data-stu-id="c4377-151">If you don't see this, you should download and run the most recent version of the Hybrid Configuration Wizard.</span></span>
  
 <span data-ttu-id="c4377-152">**重要说明**如果您的环境中运行的是 Exchange 2010，则不会创建 EvoSTS 身份验证提供程序。</span><span class="sxs-lookup"><span data-stu-id="c4377-152">**Important** If you're running Exchange 2010 in your environment, the EvoSTS authentication provider won't be created.</span></span> 
  
## <a name="enable-hma"></a><span data-ttu-id="c4377-153">启用 HMA</span><span class="sxs-lookup"><span data-stu-id="c4377-153">Enable HMA</span></span>

<span data-ttu-id="c4377-154">在 Exchange 命令行管理程序（本地）中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="c4377-154">Run the following command in the Exchange Management Shell, on-premises:</span></span>

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

## <a name="verify"></a><span data-ttu-id="c4377-155">Verify</span><span class="sxs-lookup"><span data-stu-id="c4377-155">Verify</span></span>

<span data-ttu-id="c4377-156">启用 HMA 后，客户端的下一次登录将使用新的身份验证流。</span><span class="sxs-lookup"><span data-stu-id="c4377-156">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="c4377-157">请注意，仅打开 HMA 不会触发任何客户端的重新身份验证。</span><span class="sxs-lookup"><span data-stu-id="c4377-157">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="c4377-158">客户端将根据身份验证令牌和/或证书的有效期重新进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c4377-158">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="c4377-159">您还应按住 CTRL 键，同时右键单击 Outlook 客户端的图标（也在 Windows 通知栏中），然后单击 "连接状态"。</span><span class="sxs-lookup"><span data-stu-id="c4377-159">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="c4377-160">针对 "身份验证" 类型的 "载荷" 查找客户端的 SMTP 地址 \* ，该类型表示在 OAuth 中使用的持有者令牌。</span><span class="sxs-lookup"><span data-stu-id="c4377-160">Look for the client's SMTP address against an 'Authn' type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
 <span data-ttu-id="c4377-161">**注释**是否需要使用 HMA 配置 Skype for Business？</span><span class="sxs-lookup"><span data-stu-id="c4377-161">**Note** Need to configure Skype for Business with HMA?</span></span> <span data-ttu-id="c4377-162">您将需要两个文章：一个列出[受支持的拓扑](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)，另一个演示[如何执行配置](configure-skype-for-business-for-hybrid-modern-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="c4377-162">You'll need two articles: One that lists [supported topologies](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), and one that shows you [how to do the configuration](configure-skype-for-business-for-hybrid-modern-authentication.md).</span></span>
 
## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a><span data-ttu-id="c4377-163">将混合新式验证用于 Outlook for iOS 和 Outlook for Android</span><span class="sxs-lookup"><span data-stu-id="c4377-163">Using hybrid Modern Authentication with Outlook for iOS and Android</span></span>

<span data-ttu-id="c4377-164">如果您是在 TCP 443 上使用 Exchange server 的本地客户，请为以下 IP 范围列入白名单： </span><span class="sxs-lookup"><span data-stu-id="c4377-164">If you are an on-premises customer using Exchange server on TCP 443, please whitelist the following IP ranges:  </span></span><BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR>

## <a name="related-topics"></a><span data-ttu-id="c4377-165">相关主题</span><span class="sxs-lookup"><span data-stu-id="c4377-165">Related topics</span></span>

[<span data-ttu-id="c4377-166">从 Office 365 专用/ITAR 到 vNext 的转换的新式身份验证配置要求</span><span class="sxs-lookup"><span data-stu-id="c4377-166">Modern Authentication configuration requirements for transition from Office 365 dedicated/ITAR to vNext</span></span>](https://docs.microsoft.com/exchange/troubleshoot/modern-authentication/modern-authentication-configuration)
