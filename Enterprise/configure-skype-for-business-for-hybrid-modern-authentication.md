---
title: 如何配置本地 Skype for Business 以使用混合新式验证
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
description: 新式身份验证是一种提供更安全的用户身份验证和授权的身份管理方法，适用于本地 Skype for business server 本地和 Exchange server 以及拆分域 Skype for Business 混合。
ms.openlocfilehash: fbbf7c9188d7c0a1d9d4b936b066c0a1fa4e83e9
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813430"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="d0e81-103">如何配置本地 Skype for Business 以使用混合新式验证</span><span class="sxs-lookup"><span data-stu-id="d0e81-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="d0e81-104">*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="d0e81-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="d0e81-105">新式身份验证是一种提供更安全的用户身份验证和授权的身份管理方法，适用于本地 Skype for business server 本地和 Exchange server 以及拆分域 Skype for Business 混合。</span><span class="sxs-lookup"><span data-stu-id="d0e81-105">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="d0e81-106">**重要说明**您想了解有关新式验证（MA）的详细信息，以及您希望在贵公司或组织中使用它的原因吗？</span><span class="sxs-lookup"><span data-stu-id="d0e81-106">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization?</span></span> <span data-ttu-id="d0e81-107">查看[此文档](hybrid-modern-auth-overview.md)以了解概述。</span><span class="sxs-lookup"><span data-stu-id="d0e81-107">Check [this document](hybrid-modern-auth-overview.md) for an overview.</span></span> <span data-ttu-id="d0e81-108">如果需要了解 MA 支持的 Skype for Business 拓扑，此处对此进行了介绍！</span><span class="sxs-lookup"><span data-stu-id="d0e81-108">If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span>
  
 <span data-ttu-id="d0e81-109">**在开始之前**，我称之为：</span><span class="sxs-lookup"><span data-stu-id="d0e81-109">**Before we begin**, I call:</span></span>
  
- <span data-ttu-id="d0e81-110">新式验证\> MA</span><span class="sxs-lookup"><span data-stu-id="d0e81-110">Modern Authentication \> MA</span></span>

- <span data-ttu-id="d0e81-111">混合新式身份\>验证 HMA</span><span class="sxs-lookup"><span data-stu-id="d0e81-111">Hybrid Modern Authentication \> HMA</span></span>

- <span data-ttu-id="d0e81-112">Exchange 本地\> EXCH</span><span class="sxs-lookup"><span data-stu-id="d0e81-112">Exchange on-premises \> EXCH</span></span>

- <span data-ttu-id="d0e81-113">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="d0e81-113">Exchange Online \> EXO</span></span>

- <span data-ttu-id="d0e81-114">Skype for Business 本地\> SFB</span><span class="sxs-lookup"><span data-stu-id="d0e81-114">Skype for Business on-premises \> SFB</span></span>

- <span data-ttu-id="d0e81-115">和 Skype for Business Online \> SFBO</span><span class="sxs-lookup"><span data-stu-id="d0e81-115">and Skype for Business Online \> SFBO</span></span>

<span data-ttu-id="d0e81-116">此外，如果本文中的图形有一个灰显或变暗的对象，表示以灰色显示的元素**不**包含在 MA 特定的配置中。</span><span class="sxs-lookup"><span data-stu-id="d0e81-116">Also, if a graphic in this article has an object that's greyed-out or dimmed that means the element shown in gray **is not** included in MA-specific configuration.</span></span>
  
## <a name="read-the-summary"></a><span data-ttu-id="d0e81-117">阅读摘要</span><span class="sxs-lookup"><span data-stu-id="d0e81-117">Read the summary</span></span>

<span data-ttu-id="d0e81-118">此摘要将流程分解为在执行过程中可能会丢失的步骤，并适用于整个清单，以跟踪您在进程中所处的位置。</span><span class="sxs-lookup"><span data-stu-id="d0e81-118">This summary breaks down the process into steps that might otherwise get lost during the execution, and is good for an overall checklist to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="d0e81-119">首先，请确保满足所有先决条件。</span><span class="sxs-lookup"><span data-stu-id="d0e81-119">First, make sure you meet all the prerequisites.</span></span>

1. <span data-ttu-id="d0e81-120">由于许多**先决条件**对于 Skype for Business 和 Exchange 都是常见的，[请参阅预先申请清单的概述文章](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e81-120">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md).</span></span> <span data-ttu-id="d0e81-121">在开始本文中的任何步骤*之前*，请执行此操作。</span><span class="sxs-lookup"><span data-stu-id="d0e81-121">Do this  *before*  you begin any of the steps in this article.</span></span>

1. <span data-ttu-id="d0e81-122">收集您在文件或 OneNote 中需要的 HMA 特定信息。</span><span class="sxs-lookup"><span data-stu-id="d0e81-122">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>

1. <span data-ttu-id="d0e81-123">打开 EXO 的新式验证（如果尚未打开）。</span><span class="sxs-lookup"><span data-stu-id="d0e81-123">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>

1. <span data-ttu-id="d0e81-124">打开 SFBO 的新式验证（如果尚未打开）。</span><span class="sxs-lookup"><span data-stu-id="d0e81-124">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>

1. <span data-ttu-id="d0e81-125">为本地 Exchange 启用混合新式身份验证。</span><span class="sxs-lookup"><span data-stu-id="d0e81-125">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>

1. <span data-ttu-id="d0e81-126">启用本地 Skype for business 的混合新式身份验证。</span><span class="sxs-lookup"><span data-stu-id="d0e81-126">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>

<span data-ttu-id="d0e81-127">这些步骤为 SFB、SFBO、EXCH 和 EXO 启用了 MA，即，可以参与 HMA 和 SFB 的 SFBO 配置的所有产品（包括对 EXCH/EXO 的依赖项）。</span><span class="sxs-lookup"><span data-stu-id="d0e81-127">These steps turn on MA for SFB, SFBO, EXCH, and EXO - that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO).</span></span> <span data-ttu-id="d0e81-128">换句话说，如果用户驻留在混合的任何部分（EXO + SFBO、EXO + SFB、EXCH + SFBO 或 EXCH + SFB）中的邮箱，则最终产品将如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0e81-128">In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![混合的6个 Skype for business HMA 拓扑在所有四个可能的位置都有 MA。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="d0e81-130">正如您所看到的，有四个不同的位置可以打开 MA！</span><span class="sxs-lookup"><span data-stu-id="d0e81-130">As you can see there are four different places to turn on MA!</span></span> <span data-ttu-id="d0e81-131">为获得最佳用户体验，建议您在所有四个位置都打开 MA。</span><span class="sxs-lookup"><span data-stu-id="d0e81-131">For the best user experience we recommend you turn on MA in all four of these locations.</span></span> <span data-ttu-id="d0e81-132">如果无法在所有这些位置启用 MA，请调整步骤，以便仅在环境所需的位置启用 MA。</span><span class="sxs-lookup"><span data-stu-id="d0e81-132">If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="d0e81-133">有关支持的拓扑，请参阅[Skype for](https://technet.microsoft.com/library/mt803262.aspx) business 的可支持性主题（MA 为 MA）。</span><span class="sxs-lookup"><span data-stu-id="d0e81-133">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/library/mt803262.aspx) for supported topologies.</span></span>
  
 <span data-ttu-id="d0e81-134">**重要说明**在开始之前，请仔细检查是否满足所有先决条件。</span><span class="sxs-lookup"><span data-stu-id="d0e81-134">**Important** Double-check that you've met all the prerequisites before you begin.</span></span> <span data-ttu-id="d0e81-135">你将在[此处](hybrid-modern-auth-overview.md)找到此信息。</span><span class="sxs-lookup"><span data-stu-id="d0e81-135">You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="d0e81-136">收集您需要的所有 HMA 特定信息</span><span class="sxs-lookup"><span data-stu-id="d0e81-136">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="d0e81-137">在仔细检查您是否符合使用新式验证的[先决条件](hybrid-modern-auth-overview.md)后（请参阅上面的注释），应创建一个文件，以保存在前面步骤中配置 HMA 所需的信息。</span><span class="sxs-lookup"><span data-stu-id="d0e81-137">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead.</span></span> <span data-ttu-id="d0e81-138">本文中使用的示例：</span><span class="sxs-lookup"><span data-stu-id="d0e81-138">Examples used in this article:</span></span>
  
- <span data-ttu-id="d0e81-139">**SIP/SMTP 域**</span><span class="sxs-lookup"><span data-stu-id="d0e81-139">**SIP/SMTP domain**</span></span>

  - <span data-ttu-id="d0e81-140">Ex.</span><span class="sxs-lookup"><span data-stu-id="d0e81-140">Ex.</span></span> <span data-ttu-id="d0e81-141">contoso.com （与 Office 365 联合）</span><span class="sxs-lookup"><span data-stu-id="d0e81-141">contoso.com (is federated with Office 365)</span></span>

- <span data-ttu-id="d0e81-142">**租户 ID**</span><span class="sxs-lookup"><span data-stu-id="d0e81-142">**Tenant ID**</span></span>

  - <span data-ttu-id="d0e81-143">表示 Office 365 租户的 GUID （在 contoso.onmicrosoft.com 的登录名处）。</span><span class="sxs-lookup"><span data-stu-id="d0e81-143">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>

- <span data-ttu-id="d0e81-144">**SFB 2015 CU5 Web 服务 Url**</span><span class="sxs-lookup"><span data-stu-id="d0e81-144">**SFB 2015 CU5 Web Service URLs**</span></span>

<span data-ttu-id="d0e81-145">您将需要部署的所有 SfB 2015 池的内部和外部 web 服务 URL。</span><span class="sxs-lookup"><span data-stu-id="d0e81-145">You will need internal and external web service URL's for all SfB 2015 pools deployed.</span></span> <span data-ttu-id="d0e81-146">若要获取这些内容，请从 Skype for Business 命令行管理程序运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d0e81-146">To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- <span data-ttu-id="d0e81-147">Ex.</span><span class="sxs-lookup"><span data-stu-id="d0e81-147">Ex.</span></span> <span data-ttu-id="d0e81-148">里面https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="d0e81-148">Internal: https://lyncwebint01.contoso.com</span></span>

- <span data-ttu-id="d0e81-149">Ex.</span><span class="sxs-lookup"><span data-stu-id="d0e81-149">Ex.</span></span> <span data-ttu-id="d0e81-150">对外https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="d0e81-150">External: https://lyncwebext01.contoso.com</span></span>

<span data-ttu-id="d0e81-151">如果使用的是 Standard Edition server，则内部 URL 将为空。</span><span class="sxs-lookup"><span data-stu-id="d0e81-151">If you are using a Standard Edition server, the internal URL will be blank.</span></span> <span data-ttu-id="d0e81-152">在这种情况下，请使用内部 URL 的池 fqdn。</span><span class="sxs-lookup"><span data-stu-id="d0e81-152">In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="d0e81-153">打开 EXO 的新式验证</span><span class="sxs-lookup"><span data-stu-id="d0e81-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="d0e81-154">请按照以下说明操作： [Exchange Online：如何为你的租户启用新式验证。](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="d0e81-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="d0e81-155">打开 SFBO 的新式验证</span><span class="sxs-lookup"><span data-stu-id="d0e81-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="d0e81-156">请按照以下说明操作： [Skype For Business Online：为你的租户启用新式验证](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d0e81-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="d0e81-157">启用本地 Exchange 的混合新式身份验证</span><span class="sxs-lookup"><span data-stu-id="d0e81-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="d0e81-158">请按照以下说明操作：[如何将 Exchange Server 本地配置为使用混合新式身份验证](configure-exchange-server-for-hybrid-modern-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e81-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="d0e81-159">启用本地 Skype for business 的混合新式身份验证</span><span class="sxs-lookup"><span data-stu-id="d0e81-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="d0e81-160">在 Azure AD 中将本地 web 服务 Url 添加为 Spn</span><span class="sxs-lookup"><span data-stu-id="d0e81-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="d0e81-161">现在，您需要运行命令以在 SFBO 中添加 Url （之前收集的）作为服务主体。</span><span class="sxs-lookup"><span data-stu-id="d0e81-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="d0e81-162">**注释**服务主体名称（Spn）标识 web 服务并将它们与安全主体（如帐户名或组）相关联，以便该服务可以代表授权的用户执行操作。</span><span class="sxs-lookup"><span data-stu-id="d0e81-162">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user.</span></span> <span data-ttu-id="d0e81-163">对服务器进行身份验证的客户端使用 Spn 中包含的信息。</span><span class="sxs-lookup"><span data-stu-id="d0e81-163">Clients authenticating to a server make use of information that's contained in SPNs.</span></span>
  
1. <span data-ttu-id="d0e81-164">首先，使用[这些说明](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0)连接到 AAD。</span><span class="sxs-lookup"><span data-stu-id="d0e81-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0).</span></span>

2. <span data-ttu-id="d0e81-165">运行此命令（本地）以获取 SFB web 服务 Url 的列表。</span><span class="sxs-lookup"><span data-stu-id="d0e81-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>

   <span data-ttu-id="d0e81-166">请注意，AppPrincipalId 以开头`00000004`。</span><span class="sxs-lookup"><span data-stu-id="d0e81-166">Note that the AppPrincipalId begins with `00000004`.</span></span> <span data-ttu-id="d0e81-167">这对应于 Skype for Business Online。</span><span class="sxs-lookup"><span data-stu-id="d0e81-167">This corresponds to Skype for Business Online.</span></span>

   <span data-ttu-id="d0e81-168">记下（以及稍后比较的屏幕截图）此命令的输出将包含 SE 和 WS URL，但主要由以开头的 Spn 组成`00000004-0000-0ff1-ce00-000000000000/`。</span><span class="sxs-lookup"><span data-stu-id="d0e81-168">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with `00000004-0000-0ff1-ce00-000000000000/`.</span></span>

```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
```

3. <span data-ttu-id="d0e81-169">如果内部**或**外部 SFB url 缺少内部部署（例如， https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com)我们需要将这些特定记录添加到此列表。</span><span class="sxs-lookup"><span data-stu-id="d0e81-169">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span>

    <span data-ttu-id="d0e81-170">请务必将下面的*示例 url*替换为添加命令中的实际 url！</span><span class="sxs-lookup"><span data-stu-id="d0e81-170">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span>
  
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
$x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
$x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
  
4. <span data-ttu-id="d0e81-171">再次运行步骤2中的**new-msolserviceprincipal**命令，并查看输出，以验证新记录是否已添加。</span><span class="sxs-lookup"><span data-stu-id="d0e81-171">Verify your new records were added by running the **Get-MsolServicePrincipal** command from step 2 again, and looking through the output.</span></span> <span data-ttu-id="d0e81-172">将列表/屏幕截图从早到新的 Spn 列表进行比较（您还可能会为您的记录提供新列表的屏幕截图）。</span><span class="sxs-lookup"><span data-stu-id="d0e81-172">Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records).</span></span> <span data-ttu-id="d0e81-173">如果成功，您将在列表中看到两个新的 Url。</span><span class="sxs-lookup"><span data-stu-id="d0e81-173">If you were successful, you will see the two new URLs in the list.</span></span> <span data-ttu-id="d0e81-174">根据我们的示例，Spn 列表现在将包含特定的 Url https://lyncwebint01.contoso.com和。 https://lyncwebext01.contoso.com/</span><span class="sxs-lookup"><span data-stu-id="d0e81-174">Going by our example, the list of SPNs will now include the specific URLs https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com/.</span></span>

### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="d0e81-175">创建 EvoSTS Auth Server 对象</span><span class="sxs-lookup"><span data-stu-id="d0e81-175">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="d0e81-176">在 Skype for Business 命令行管理程序中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d0e81-176">Run the following command in the Skype for Business Management Shell.</span></span>
  
```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="d0e81-177">启用混合新式身份验证</span><span class="sxs-lookup"><span data-stu-id="d0e81-177">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="d0e81-178">这是实际打开 MA 的步骤。</span><span class="sxs-lookup"><span data-stu-id="d0e81-178">This is the step that actually turns MA on.</span></span> <span data-ttu-id="d0e81-179">前面的所有步骤都可以提前运行，而无需更改客户端身份验证流。</span><span class="sxs-lookup"><span data-stu-id="d0e81-179">All the previous steps can be run ahead of time without changing the client authentication flow.</span></span> <span data-ttu-id="d0e81-180">当您准备好更改身份验证流时，请在 Skype for Business 命令行管理程序中运行此命令。</span><span class="sxs-lookup"><span data-stu-id="d0e81-180">When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a><span data-ttu-id="d0e81-181">Verify</span><span class="sxs-lookup"><span data-stu-id="d0e81-181">Verify</span></span>

<span data-ttu-id="d0e81-182">启用 HMA 后，客户端的下一次登录将使用新的身份验证流。</span><span class="sxs-lookup"><span data-stu-id="d0e81-182">Once you enable HMA, a client's next login will use the new auth flow.</span></span> <span data-ttu-id="d0e81-183">请注意，仅打开 HMA 不会触发任何客户端的重新身份验证。</span><span class="sxs-lookup"><span data-stu-id="d0e81-183">Note that just turning on HMA won't trigger a re-authentication for any client.</span></span> <span data-ttu-id="d0e81-184">客户端将根据身份验证令牌和/或证书的有效期重新进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d0e81-184">The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="d0e81-185">若要测试 HMA 在启用后是否正常工作，请注销测试 SFB Windows 客户端，并确保单击 "删除我的凭据"。</span><span class="sxs-lookup"><span data-stu-id="d0e81-185">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'.</span></span> <span data-ttu-id="d0e81-186">重新登录。</span><span class="sxs-lookup"><span data-stu-id="d0e81-186">Sign in again.</span></span> <span data-ttu-id="d0e81-187">客户端现在应使用新式的身份验证流，并且您的登录现在将包含**Office 365**提示 "工作或学校" 帐户，在客户端与服务器联系并登录之前，请立即看到该帐户。</span><span class="sxs-lookup"><span data-stu-id="d0e81-187">The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span>
  
<span data-ttu-id="d0e81-188">您还应检查 "OAuth 颁发机构" 的 Skype for business 客户端的 "配置信息"。</span><span class="sxs-lookup"><span data-stu-id="d0e81-188">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'.</span></span> <span data-ttu-id="d0e81-189">若要在客户端计算机上执行此操作，请按住 CTRL 键，同时右键单击 Windows 通知托盘中的 "Skype for Business" 图标。</span><span class="sxs-lookup"><span data-stu-id="d0e81-189">To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray.</span></span> <span data-ttu-id="d0e81-190">在出现的菜单中单击 "**配置信息**"。</span><span class="sxs-lookup"><span data-stu-id="d0e81-190">Click **Configuration Information** in the menu that appears.</span></span> <span data-ttu-id="d0e81-191">在将出现在桌面上的 "Skype for Business 配置信息" 窗口中，查找以下内容：</span><span class="sxs-lookup"><span data-stu-id="d0e81-191">In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![使用新式验证的 Skype for business 客户端的配置信息显示了的 Lync 和 EWS OAUTH 授权 URL https://login.windows.net/common/oauth2/authorize。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="d0e81-193">您还应按住 CTRL 键，同时右键单击 Outlook 客户端的图标（也在 Windows 通知栏中），然后单击 "连接状态"。</span><span class="sxs-lookup"><span data-stu-id="d0e81-193">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'.</span></span> <span data-ttu-id="d0e81-194">针对身份验证类型的 "载荷\*" 查找客户端的 SMTP 地址，该类型表示在 OAuth 中使用的持有者令牌。</span><span class="sxs-lookup"><span data-stu-id="d0e81-194">Look for the client's SMTP address against an AuthN type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="d0e81-195">相关文章</span><span class="sxs-lookup"><span data-stu-id="d0e81-195">Related articles</span></span>

<span data-ttu-id="d0e81-196">[链接回新式验证概述](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e81-196">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md).</span></span>
  
<span data-ttu-id="d0e81-197">您是否需要了解如何对 Skype for business 客户端使用新式验证（ADAL）？</span><span class="sxs-lookup"><span data-stu-id="d0e81-197">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients?</span></span> <span data-ttu-id="d0e81-198">我们[在此处](https://technet.microsoft.com/library/mt710548.aspx)获取了一些步骤。</span><span class="sxs-lookup"><span data-stu-id="d0e81-198">We've got steps [here](https://technet.microsoft.com/library/mt710548.aspx).</span></span>
