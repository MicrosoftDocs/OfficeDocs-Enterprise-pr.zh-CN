---
title: 如何配置本地 Skype for Business 以使用混合新式验证
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: 现代身份验证，是一种身份管理提供更安全的用户身份验证和授权，适用于 Skype 用于业务服务器本地和 Exchange server 内部部署，以及业务混合的拆分域 Skype 方法。
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539883"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a><span data-ttu-id="33c5c-103">如何配置本地 Skype for Business 以使用混合新式验证</span><span class="sxs-lookup"><span data-stu-id="33c5c-103">How to configure Skype for Business on-premises to use Hybrid Modern Authentication</span></span>

<span data-ttu-id="33c5c-104">现代身份验证，是一种身份管理提供更安全的用户身份验证和授权，适用于 Skype 用于业务服务器本地和 Exchange server 内部部署，以及业务混合的拆分域 Skype 方法。</span><span class="sxs-lookup"><span data-stu-id="33c5c-104">Modern Authentication, is a method of identity management that offers more secure user authentication and authorization, is available for Skype for Business server on-premises and Exchange server on-premises, as well as split-domain Skype for Business hybrids.</span></span>
  
 <span data-ttu-id="33c5c-p101">**重要**若要了解有关现代身份验证 (MA) 和为什么您可能希望在贵公司或组织中使用它的详细信息吗？检查[本文档](hybrid-modern-auth-overview.md)概述。如果您需要了解哪些 Skype 的业务拓扑支持与 MA，此处介绍的 ！</span><span class="sxs-lookup"><span data-stu-id="33c5c-p101">**Important** Would you like to know more about Modern Authentication (MA) and why you might prefer to use it in your company or organization? Check [this document](hybrid-modern-auth-overview.md) for an overview. If you need to know what Skype for Business topologies are supported with MA, that's documented here!</span></span> 
  
 <span data-ttu-id="33c5c-108">**我们在开始之前**，请调用：</span><span class="sxs-lookup"><span data-stu-id="33c5c-108">**Before we begin**, I call:</span></span> 
  
- <span data-ttu-id="33c5c-109">现代身份验证\>MA</span><span class="sxs-lookup"><span data-stu-id="33c5c-109">Modern Authentication \> MA</span></span>
    
- <span data-ttu-id="33c5c-110">混合现代身份验证\>HMA</span><span class="sxs-lookup"><span data-stu-id="33c5c-110">Hybrid Modern Authentication \> HMA</span></span>
    
- <span data-ttu-id="33c5c-111">Exchange 内部部署\>EXCH</span><span class="sxs-lookup"><span data-stu-id="33c5c-111">Exchange on-premises \> EXCH</span></span>
    
- <span data-ttu-id="33c5c-112">Exchange Online \> EXO</span><span class="sxs-lookup"><span data-stu-id="33c5c-112">Exchange Online \> EXO</span></span>
    
- <span data-ttu-id="33c5c-113">为业务本地 Skype \> SFB</span><span class="sxs-lookup"><span data-stu-id="33c5c-113">Skype for Business on-premises \> SFB</span></span>
    
- <span data-ttu-id="33c5c-114">和 Skype for Business 联机\>SFBO</span><span class="sxs-lookup"><span data-stu-id="33c5c-114">and Skype for Business Online \> SFBO</span></span>
    
<span data-ttu-id="33c5c-115">此外，\* 本文中的图形是否具有灰显或变暗的对象，该对象表示灰色**不**包括特定于 MA 的配置中所示的元素。</span><span class="sxs-lookup"><span data-stu-id="33c5c-115">Also,  \*if a graphic in this article has an object that's 'grayed-out' or 'dimmed' that means the element shown in gray **is not** included in MA-specific configuration.</span></span> * 
  
## <a name="read-the-summary"></a><span data-ttu-id="33c5c-116">阅读摘要</span><span class="sxs-lookup"><span data-stu-id="33c5c-116">Read the summary</span></span>

<span data-ttu-id="33c5c-117">这段摘要最终过程是： 到步骤，可能否则迷失执行期间，并且最好使用以跟踪您在何处过程中的总体检查的列表。</span><span class="sxs-lookup"><span data-stu-id="33c5c-117">This summary boils the process into steps that might otherwise get lost during the execution, and is good for an overall check-list to keep track of where you are in the process.</span></span>
  
1. <span data-ttu-id="33c5c-118">首先，请确保您满足所有先决条件。</span><span class="sxs-lookup"><span data-stu-id="33c5c-118">First, make sure you meet all the prerequisites.</span></span>
    
1. <span data-ttu-id="33c5c-p102">以来多个**必备组件**是针对常用于这两个 Skype 商业和 Exchange，[请参阅此概述文章以必备项检查表](hybrid-modern-auth-overview.md)。执行此*之前*开始任何本文中的步骤。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p102">Since many **prerequisites** are common for both Skype for Business and Exchange, [see the overview article for your pre-req checklist](hybrid-modern-auth-overview.md). Do this  *before*  you begin any of the steps in this article.</span></span> 
    
2. <span data-ttu-id="33c5c-121">收集您将需要一个文件或 OneNote 中的特定于 HMA 的信息。</span><span class="sxs-lookup"><span data-stu-id="33c5c-121">Collect the HMA-specific info you'll need in a file, or OneNote.</span></span>
    
3. <span data-ttu-id="33c5c-122">打开 ON 现代的身份验证 EXO （如果尚未打开）。</span><span class="sxs-lookup"><span data-stu-id="33c5c-122">Turn ON Modern Authentication for EXO (if it is not already turned on).</span></span>
    
4. <span data-ttu-id="33c5c-123">打开 ON 现代的身份验证 SFBO （如果尚未打开）。</span><span class="sxs-lookup"><span data-stu-id="33c5c-123">Turn ON Modern Authentication for SFBO (if it is not already turned on).</span></span>
    
5. <span data-ttu-id="33c5c-124">打开 Exchange 内部部署混合现代身份验证。</span><span class="sxs-lookup"><span data-stu-id="33c5c-124">Turn ON Hybrid Modern Authentication for Exchange on-premises.</span></span>
    
6. <span data-ttu-id="33c5c-125">打开业务本地混合 Skype 现代的身份验证。</span><span class="sxs-lookup"><span data-stu-id="33c5c-125">Turn ON Hybrid Modern Authentication for Skype for Business on-premises.</span></span>
    
<span data-ttu-id="33c5c-p103">请注意以下步骤打开 MA SFB、 SFBO、 EXCH，和 EXO-，即可以参与了 HMA 配置 SFB 和 SFBO （包括依赖 EXCH/EXO） 的所有产品。换句话说，如果用户驻留在 / 混合 （EXO + SFBO、 EXO + SFB、 EXCH + SFBO，或 EXCH + SFB） 的任何部分中创建邮箱，完成的产品将如下所示：</span><span class="sxs-lookup"><span data-stu-id="33c5c-p103">Note These steps turn on MA for SFB, SFBO, EXCH, and EXO -- that is, all the products that can participate in a HMA configuration of SFB and SFBO (including dependencies on EXCH/EXO). In other words, if your users are homed in/have mailboxes created in any part of the Hybrid (EXO + SFBO, EXO + SFB, EXCH + SFBO, or EXCH + SFB), your finished product will look like this:</span></span>
  
![业务 HMA 拓扑的混合 6 Skype 对 MA 中所有四个可能的位置。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
<span data-ttu-id="33c5c-p104">您可以看到有四个不同的位置打开 MA ！获得最佳用户体验，我们建议您打开 MA 中所有四个这些位置。如果所有这些位置中，不能打开 MA，调整的步骤，以便您打开 MA 仅在所需的环境的位置。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p104">As you can see there are four different places to turn on MA! For the best user experience we recommend you turn on MA in all four of these locations. If you can't turn MA on in all these locations, adjust the steps so that you turn on MA only in the locations that are necessary for your environment.</span></span>
  
<span data-ttu-id="33c5c-132">请参阅[可支持性主题 Business MA 的 Skype](https://technet.microsoft.com/en-us/library/mt803262.aspx)受支持的拓扑。</span><span class="sxs-lookup"><span data-stu-id="33c5c-132">See the [Supportability topic for Skype for Business with MA](https://technet.microsoft.com/en-us/library/mt803262.aspx) for supported topologies.</span></span> 
  
 <span data-ttu-id="33c5c-p105">**重要**仔细检查之前您已满足所有必备组件。您可以找到该信息[此处](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p105">**Important** Double-check that you've met all the prerequisites before you begin. You'll find that information [here](hybrid-modern-auth-overview.md).</span></span>
  
## <a name="collect-all-hma-specific-info-youll-need"></a><span data-ttu-id="33c5c-135">收集所需的所有 HMA 特有信息</span><span class="sxs-lookup"><span data-stu-id="33c5c-135">Collect all HMA-specific info you'll need</span></span>

<span data-ttu-id="33c5c-p106">双重的检查后满足用于现代身份验证的[先决条件](hybrid-modern-auth-overview.md)（请参阅上面的说明），您应创建文件来保存所需的步骤提前中的 configuring HMA 的信息。使用本文中的示例：</span><span class="sxs-lookup"><span data-stu-id="33c5c-p106">After you've double-checked that you meet the [prerequisites](hybrid-modern-auth-overview.md) to use Modern Authentication (see the note above), you should create a file to hold the info you'll need for configuring HMA in the steps ahead. Examples used in this article:</span></span> 
  
- <span data-ttu-id="33c5c-138">**SIP/SMTP 域**</span><span class="sxs-lookup"><span data-stu-id="33c5c-138">**SIP/SMTP domain**</span></span>
    
  - <span data-ttu-id="33c5c-p107">例如 contoso.com （与 Office 365 联盟）</span><span class="sxs-lookup"><span data-stu-id="33c5c-p107">Ex. contoso.com (is federated with Office 365)</span></span>
    
- <span data-ttu-id="33c5c-141">**租户 ID**</span><span class="sxs-lookup"><span data-stu-id="33c5c-141">**Tenant ID**</span></span>
    
  - <span data-ttu-id="33c5c-142">GUID 值，该值代表 Office 365 租户 （在的 contoso.onmicrosoft.com 登录）。</span><span class="sxs-lookup"><span data-stu-id="33c5c-142">The GUID that represents your Office 365 tenant (at the login of contoso.onmicrosoft.com).</span></span>
    
- <span data-ttu-id="33c5c-143">**SFB 2015 CU5 Web 服务 Url**</span><span class="sxs-lookup"><span data-stu-id="33c5c-143">**SFB 2015 CU5 Web Service URLs**</span></span>
    
<span data-ttu-id="33c5c-p108">为所有 SfB 2015 池部署，您将需要内部和外部 web 服务 URL。若要获得这些，运行以下命令从 Skype 的业务命令行管理程序：</span><span class="sxs-lookup"><span data-stu-id="33c5c-p108">You will need internal and external web service URL's for all SfB 2015 pools deployed. To obtain these, run the following from Skype for Business Management Shell:</span></span>
  
<span data-ttu-id="33c5c-146">Get-csservice-WebServer |选择对象 PoolFqdn，InternalFqdn，外部 |FL</span><span class="sxs-lookup"><span data-stu-id="33c5c-146">Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL</span></span>
  
- <span data-ttu-id="33c5c-p109">例如内部：https://lyncwebint01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="33c5c-p109">Ex. Internal: https://lyncwebint01.contoso.com</span></span>
    
- <span data-ttu-id="33c5c-p110">例如外部：https://lyncwebext01.contoso.com</span><span class="sxs-lookup"><span data-stu-id="33c5c-p110">Ex. External: https://lyncwebext01.contoso.com</span></span>
    
<span data-ttu-id="33c5c-p111">如果您使用的 Standard Edition server，该内部 URL 将为空。在这种情况下，使用内部 URL 池 fqdn。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p111">If you are using a Standard Edition server, the internal URL will be blank. In this case, use the pool fqdn for the internal URL.</span></span>
  
## <a name="turn-on-modern-authentication-for-exo"></a><span data-ttu-id="33c5c-153">打开 EXO 现代身份验证</span><span class="sxs-lookup"><span data-stu-id="33c5c-153">Turn on Modern Authentication for EXO</span></span>

<span data-ttu-id="33c5c-154">按照说明进行操作： [Exchange Online： 如何启用现代身份验证您的租户。](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span><span class="sxs-lookup"><span data-stu-id="33c5c-154">Follow the instructions here: [Exchange Online: How to enable your tenant for modern authentication.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)</span></span>
  
## <a name="turn-on-modern-authentication-for-sfbo"></a><span data-ttu-id="33c5c-155">打开 SFBO 现代身份验证</span><span class="sxs-lookup"><span data-stu-id="33c5c-155">Turn on Modern Authentication for SFBO</span></span>

<span data-ttu-id="33c5c-156">按照说明进行操作： [Skype 业务 online： 启用您的租户的现代身份验证](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。</span><span class="sxs-lookup"><span data-stu-id="33c5c-156">Follow the instructions here: [Skype for Business Online: Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a><span data-ttu-id="33c5c-157">打开 Exchange 内部部署混合现代身份验证</span><span class="sxs-lookup"><span data-stu-id="33c5c-157">Turn on Hybrid Modern Authentication for Exchange on-premises</span></span>

<span data-ttu-id="33c5c-158">按照说明进行操作：[如何配置 Exchange Server 内部部署用于混合现代身份验证](configure-exchange-server-for-hybrid-modern-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="33c5c-158">Follow the instructions here: [How to configure Exchange Server on-premises to use Hybrid Modern Authentication](configure-exchange-server-for-hybrid-modern-authentication.md).</span></span>
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a><span data-ttu-id="33c5c-159">打开业务本地混合 Skype 现代的身份验证</span><span class="sxs-lookup"><span data-stu-id="33c5c-159">Turn on Hybrid Modern Authentication for Skype for Business on-premises</span></span>

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a><span data-ttu-id="33c5c-160">添加内部部署 Azure AD 中为 Spn web 服务 Url</span><span class="sxs-lookup"><span data-stu-id="33c5c-160">Add on-premises web service URLs as SPNs in Azure AD</span></span>

<span data-ttu-id="33c5c-161">现在，您需要运行命令以将 （收集更早版本） 的 Url 添加为 SFBO 中的服务主体。</span><span class="sxs-lookup"><span data-stu-id="33c5c-161">Now you'll need to run commands to add the URLs (collected earlier) as Service Principals in SFBO.</span></span>
  
 <span data-ttu-id="33c5c-p112">**注释**服务主体名称 (Spn) 确定 web 服务，并将其与安全主体 （如帐户名或组中） 关联，以便该服务可充当授权用户替。客户端到服务器身份验证发出信息的使用的中包含的 Spn。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p112">**Note** Service principal names (SPNs) identify web services and associate them with a security principal (such as an account name or group) so that the service can act on the behalf of an authorized user. Clients authenticating to a server make use of information that's contained in SPNs.</span></span> 
  
1. <span data-ttu-id="33c5c-164">首先，连接到 AAD 与[这些说明](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0)。</span><span class="sxs-lookup"><span data-stu-id="33c5c-164">First, connect to AAD with [these instructions](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).</span></span>
    
2. <span data-ttu-id="33c5c-165">运行此命令中，内部部署，以获取 SFB web 服务 Url 的列表。</span><span class="sxs-lookup"><span data-stu-id="33c5c-165">Run this command, on-premises, to get a list of SFB web service URLs.</span></span>
    
  - <span data-ttu-id="33c5c-166">Get MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 |选择-ExpandProperty ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="33c5c-166">Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames</span></span>
    
    <span data-ttu-id="33c5c-p113">请注意，AppPrincipalId 开头"00000004"。这对应于 Skype 的业务联机。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p113">Notice that the AppPrincipalId begins with '00000004'. This corresponds to Skype for Business Online.</span></span>
    
    <span data-ttu-id="33c5c-169">执行此命令，其中将包括 SE 和 WS URL，但主要包含开头 00000004-0000-0ff1-ce00-000000000000 的 Spn 的输出的注释 （和更高版本比较的屏幕快照） /。</span><span class="sxs-lookup"><span data-stu-id="33c5c-169">Take note of (and screenshot for later comparison) the output of this command, which will include an SE and WS URL, but mostly consist of SPNs that begin with 00000004-0000-0ff1-ce00-000000000000/.</span></span>
    
3. <span data-ttu-id="33c5c-170">如果内部**或**外部丢失了从本地 SFB Url (例如，https://lyncwebint01.contoso.com和https://lyncwebext01.contoso.com)我们需要这些特定记录添加到此列表。</span><span class="sxs-lookup"><span data-stu-id="33c5c-170">If the internal **or** external SFB URLs from on-premises are missing (for example, https://lyncwebint01.contoso.com and https://lyncwebext01.contoso.com) we will need to add those specific records to this list.</span></span> 
    
    <span data-ttu-id="33c5c-171">请务必下面的*示例 Url* ，替换中添加命令您实际 Url ！</span><span class="sxs-lookup"><span data-stu-id="33c5c-171">Be sure to replace  *the example URLs*  , below, with your actual URLs in the Add commands!</span></span> 
    
  - <span data-ttu-id="33c5c-172">$x = get MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span><span class="sxs-lookup"><span data-stu-id="33c5c-172">$x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000</span></span>
    
  - <span data-ttu-id="33c5c-173">$x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="33c5c-173">$x.ServicePrincipalnames.Add(" *https://lyncwebint01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="33c5c-174">$x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ")</span><span class="sxs-lookup"><span data-stu-id="33c5c-174">$x.ServicePrincipalnames.Add(" *https://lyncwebext01.contoso.com/*  ")</span></span> 
    
  - <span data-ttu-id="33c5c-175">设置 MSOLServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000-ServicePrincipalNames $x.ServicePrincipalNames</span><span class="sxs-lookup"><span data-stu-id="33c5c-175">Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames</span></span>
    
4. <span data-ttu-id="33c5c-p114">确认通过 Get MsolServicePrincipal 命令从步骤 2 再次运行，并将输出通过查找已添加新记录。比较列表 / 屏幕截图从之前对新列表的 Spn （您还可以屏幕截图新列表的记录）。如果您已成功完成，您将看到列表中的两个新 Url。通过我们的示例转，Spn 的列表将现已包括特定的 Urlhttps://lyncweb01.contoso.com和https://autodiscover.contoso.com。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p114">Verify your new records were added by running the Get-MsolServicePrincipal command from step 2 again, and looking through the output. Compare the list / screenshot from before to the new list of SPNs (you may also screenshot the new list for your records). If you were successful, you will see the two new URLs in the list. Going by our example, the list of SPNs will now include the specific URLs https://lyncweb01.contoso.com and https://autodiscover.contoso.com.</span></span>
    
### <a name="create-the-evosts-auth-server-object"></a><span data-ttu-id="33c5c-180">创建 EvoSTS 身份验证服务器对象</span><span class="sxs-lookup"><span data-stu-id="33c5c-180">Create the EvoSTS Auth Server Object</span></span>

<span data-ttu-id="33c5c-181">为业务命令行管理程序 Skype 中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="33c5c-181">Run the following command in the Skype for Business Management Shell.</span></span>
  
- <span data-ttu-id="33c5c-182">New-csoauthserver-Identity evoSTS-MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true-类型 AzureAD</span><span class="sxs-lookup"><span data-stu-id="33c5c-182">New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD</span></span>
    
### <a name="enable-hybrid-modern-authentication"></a><span data-ttu-id="33c5c-183">启用混合现代身份验证</span><span class="sxs-lookup"><span data-stu-id="33c5c-183">Enable Hybrid Modern Authentication</span></span>

<span data-ttu-id="33c5c-p115">这是实际开启 MA 的步骤。可以提早制定运行上述所有步骤，而不更改客户端身份验证流程。若要更改身份验证流程，准备就绪后，运行此命令中 Skype 的业务命令行管理程序。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p115">This is the step that actually turns MA on. All the previous steps can be run ahead of time without changing the client authentication flow. When you are ready to change the authentication flow, run this command in the Skype for Business Management Shell.</span></span> 
  
- <span data-ttu-id="33c5c-187">Set-csoauthconfiguration-ClientAuthorizationOAuthServerIdentity evoSTS</span><span class="sxs-lookup"><span data-stu-id="33c5c-187">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS</span></span>
    
## <a name="verify"></a><span data-ttu-id="33c5c-188">“验证”</span><span class="sxs-lookup"><span data-stu-id="33c5c-188">Verify</span></span>

<span data-ttu-id="33c5c-p116">一旦您启用 HMA，下次登录时的客户端将使用新的身份验证流。请注意刚打开 HMA 不会触发重新进行身份验证的任何客户端。客户端重新进行身份验证基于身份验证令牌和/或拥有的证书的生存期。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p116">Once you enable HMA, a client's next login will use the new auth flow. Note that just turning on HMA won't trigger a re-authentication for any client. The clients re-authenticate based on the lifetime of the auth tokens and/or certs they have.</span></span>
  
<span data-ttu-id="33c5c-p117">若要测试 HMA 正常启用此功能后，注销测试 SFB Windows 客户端，并确保单击删除我的凭据。再次登录。客户端现在应使用的现代身份验证流程和您的登录将现已包括一个**Office 365**提示符 '工作或学校看到右之前客户端与服务器联系，并登录您的帐户。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p117">To test that HMA is working after you've enabled it, sign out of a test SFB Windows client and be sure to click 'delete my credentials'. Sign in again. The client should now use the Modern Auth flow and your login will now include an **Office 365** prompt for a 'Work or school' account, seen right before the client contacts the server and logs you in.</span></span> 
  
<span data-ttu-id="33c5c-p118">您还应检查配置信息的 Skype 业务客户端的 OAuth 颁发机构。若要在客户端计算机上执行此操作，请按住 CTRL 键的同时右键 Skype 业务图标单击 Windows 通知托盘中。在出现的菜单中，单击配置信息。在桌面上将出现 Skype 的业务配置信息窗口中，查找以下问题：</span><span class="sxs-lookup"><span data-stu-id="33c5c-p118">You should also check the 'Configuration Information' for Skype for Business Clients for an 'OAuth Authority'. To do this on your client computer, hold down the CTRL key at the same time you right-click the Skype for Business Icon in the Windows Notification tray. Click Configuration Information in the menu that appears. In the 'Skype for Business Configuration Information' window that will appear on the desktop, look for the following:</span></span>
  
![使用现代身份验证的业务客户端的配置信息的 Skype 显示 Lync 和 EWS OAUTH 证书颁发机构 URL https://login.windows.net/common/oauth2/authorize。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
<span data-ttu-id="33c5c-p119">您还应右键单击该图标的 Outlook 客户端 （还在 Windows 通知任务栏中） 的同时按住 CTRL 键，然后单击连接状态。查找针对的身份验证类型的客户端的 SMTP 地址持有者\*，它代表用于 OAuth 持有者令牌。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p119">You should also hold down the CTRL key at the same time you right click the icon for the Outlook client (also in the Windows Notifications tray) and click 'Connection Status'. Look for the client's SMTP address against an Authn type of 'Bearer\*', which represents the bearer token used in OAuth.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="33c5c-202">相关的文章</span><span class="sxs-lookup"><span data-stu-id="33c5c-202">Related articles</span></span>

<span data-ttu-id="33c5c-203">[现代身份验证概述的反向链接](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="33c5c-203">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
<span data-ttu-id="33c5c-p120">您是否需要知道如何用于现代身份验证 (ADAL) 您 Skype 业务客户端？我们提供了步骤[此处](https://technet.microsoft.com/en-us/library/mt710548.aspx)。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p120">Do you need to know how to use Modern Authentication (ADAL) for your Skype for Business clients? We've got steps [here](https://technet.microsoft.com/en-us/library/mt710548.aspx).</span></span>
  
<span data-ttu-id="33c5c-p121">是否要阅读这些步骤，显示为 Exchange Server、 本地、 SFB 的情况下运行？这些步骤在此处可用。</span><span class="sxs-lookup"><span data-stu-id="33c5c-p121">Would you like to read these steps as they appear for Exchange Server, on-premises, running without SFB? Those steps are available here.</span></span>
  

