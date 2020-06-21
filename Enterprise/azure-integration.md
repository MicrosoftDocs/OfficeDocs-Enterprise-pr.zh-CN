---
title: Azure 与 Microsoft 365 的集成
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/09/2019
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: 你的 Microsoft 365 订阅包括 Azure AD 订阅。 如果要使用本地环境进行密码同步或单一登录，请将 Microsoft 365 与 Azure AD 集成。
ms.openlocfilehash: 40426c20f12cf17955457c38d809926550efa188
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774837"
---
# <a name="azure-integration-with-microsoft-365"></a><span data-ttu-id="33399-104">Azure 与 Microsoft 365 的集成</span><span class="sxs-lookup"><span data-stu-id="33399-104">Azure integration with Microsoft 365</span></span>

<span data-ttu-id="33399-105">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="33399-105">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="33399-106">Microsoft 365 使用 Azure Active Directory （Azure AD）管理场景背后的用户身份。</span><span class="sxs-lookup"><span data-stu-id="33399-106">Microsoft 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes.</span></span> <span data-ttu-id="33399-107">Microsoft 365 订阅包括对 Azure AD 的免费订阅，这样，如果要同步密码或使用本地环境设置单一登录，则可以将 Microsoft 365 与 Azure AD 集成。</span><span class="sxs-lookup"><span data-stu-id="33399-107">Your Microsoft 365 subscription includes a free subscription to Azure AD so that you can integrate Microsoft 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment.</span></span> <span data-ttu-id="33399-108">您还可以购买高级功能，以便更好地管理帐户。</span><span class="sxs-lookup"><span data-stu-id="33399-108">You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="33399-109">Azure 还提供其他功能（如管理集成的应用程序），您可以使用这些功能来扩展和自定义 Microsoft 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="33399-109">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Microsoft 365 subscriptions.</span></span>
  
<span data-ttu-id="33399-110">您可以使用 Azure AD 部署顾问进行引导式设置和配置体验（您必须登录到 Microsoft 365）：</span><span class="sxs-lookup"><span data-stu-id="33399-110">You can use the Azure AD deployment advisors for a guided setup and configuration experience (you must be signed in to Microsoft 365):</span></span>

 - [<span data-ttu-id="33399-111">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="33399-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="33399-112">AD FS 部署顾问</span><span class="sxs-lookup"><span data-stu-id="33399-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="33399-113">Azure AD 高级设置指南</span><span class="sxs-lookup"><span data-stu-id="33399-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a><span data-ttu-id="33399-114">Azure AD 版本和 Microsoft 365 身份管理</span><span class="sxs-lookup"><span data-stu-id="33399-114">Azure AD editions and Microsoft 365 identity management</span></span>

<span data-ttu-id="33399-115">如果你已付费订阅 Microsoft 365，你也可以免费订阅 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="33399-115">If you have a paid subscription to Microsoft 365, you also have a free subscription to Azure AD.</span></span> <span data-ttu-id="33399-116">您可以使用 Azure AD 创建和管理用户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="33399-116">You can use Azure AD to create and manage user and group accounts.</span></span> <span data-ttu-id="33399-117">若要激活此订阅，你必须完成一次性注册。</span><span class="sxs-lookup"><span data-stu-id="33399-117">To activate this subscription you have to complete a one-time registration.</span></span> <span data-ttu-id="33399-118">之后，你可以从 Microsoft 365 管理中心访问 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="33399-118">Afterward, you can access Azure AD from your Microsoft 365 admin center.</span></span> 

<span data-ttu-id="33399-119">有关说明，请参阅[使用免费的 AZURE AD 订阅](https://go.microsoft.com/fwlink/p/?LinkId=617127)。</span><span class="sxs-lookup"><span data-stu-id="33399-119">For instructions, see [use your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> <span data-ttu-id="33399-120">按照说明将订阅附带的免费 Azure AD 订阅注册到 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="33399-120">Follow the instructions to register the free Azure AD subscription that comes with your subscription to Microsoft 365.</span></span> <span data-ttu-id="33399-121">请勿直接转到 azure.microsoft.com 进行注册，否则你将结束与 microsoft Azure 的试用版或付费订阅，这些订阅与 Microsoft 365 的免费订阅是独立的。</span><span class="sxs-lookup"><span data-stu-id="33399-121">Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Microsoft 365.</span></span> 
  
<span data-ttu-id="33399-122">使用免费订阅，您可以与本地目录同步，设置单一登录，并与服务应用程序（如 Salesforce、DropBox 和更多）作为服务应用程序与多个软件同步。</span><span class="sxs-lookup"><span data-stu-id="33399-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="33399-123">如果需要增强的 Active Directory 域服务（AD DS）功能、双向同步和其他管理功能，可以将免费订阅升级到付费的高级订阅。</span><span class="sxs-lookup"><span data-stu-id="33399-123">If you want enhanced Active Directory Domain Services (AD DS) functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription.</span></span> <span data-ttu-id="33399-124">有关详细信息，请参阅[Azure Active Directory 版本](https://azure.microsoft.com/pricing/details/active-directory/)。</span><span class="sxs-lookup"><span data-stu-id="33399-124">For details see [Azure Active Directory editions](https://azure.microsoft.com/pricing/details/active-directory/).</span></span>
  
<span data-ttu-id="33399-125">有关 Microsoft 365 和 Azure AD 的详细信息，请参阅[了解 microsoft 365 标识和 Azure Active Directory](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="33399-125">For more information about Microsoft 365 and Azure AD, see [Understanding Microsoft 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a><span data-ttu-id="33399-126">扩展 Microsoft 365 租户的功能</span><span class="sxs-lookup"><span data-stu-id="33399-126">Extend the capabilities of your Microsoft 365 tenant</span></span>

|<span data-ttu-id="33399-127">**功能**</span><span class="sxs-lookup"><span data-stu-id="33399-127">**Feature**</span></span>|<span data-ttu-id="33399-128">**说明**</span><span class="sxs-lookup"><span data-stu-id="33399-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="33399-129">集成应用程序</span><span class="sxs-lookup"><span data-stu-id="33399-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="33399-130">您可以向各个应用授予对您的 Microsoft 365 数据的访问权限，如邮件、日历、联系人、用户、组、文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="33399-130">You can grant individual apps access to your Microsoft 365 data, like mail, calendars, contacts, users, groups, files, and folders.</span></span> <span data-ttu-id="33399-131">你还可以在全局管理员级别授权这些应用，并通过在 Azure AD 中注册应用，使其对你的整个公司可用。</span><span class="sxs-lookup"><span data-stu-id="33399-131">You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD.</span></span> <span data-ttu-id="33399-132">有关详细信息，请参阅适用[于 Microsoft 365 管理员的集成应用和 AZURE AD](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)。</span><span class="sxs-lookup"><span data-stu-id="33399-132">For details see [Integrated Apps and Azure AD for Microsoft 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span></span>  <br/> <span data-ttu-id="33399-133">另请参阅[应用程序的单一登录](https://go.microsoft.com/fwlink/p/?LinkId=698604)。</span><span class="sxs-lookup"><span data-stu-id="33399-133">Also see [single sign-on to applications](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="33399-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="33399-134">PowerApps</span></span>  <br/> | <span data-ttu-id="33399-135">Power apps 是可连接到现有数据源（如 SharePoint 列表和其他数据应用程序）的移动设备的重点应用程序。</span><span class="sxs-lookup"><span data-stu-id="33399-135">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="33399-136">有关详细信息，请参阅[Create a PowerApp for a list In SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) 。</span><span class="sxs-lookup"><span data-stu-id="33399-136">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>  <br/> |
   
<span data-ttu-id="33399-137">有关详细信息，请参阅适用于 Microsoft 365 管理员和[AZURE ad 应用程序库和单一登录](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)[的集成应用和 azure ad](integrated-apps-and-azure-ads.md) 。</span><span class="sxs-lookup"><span data-stu-id="33399-137">Learn more at [Integrated Apps and Azure AD for Microsoft 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

## <a name="see-also"></a><span data-ttu-id="33399-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33399-138">See also</span></span>

[<span data-ttu-id="33399-139">Microsoft 365 企业版概述</span><span class="sxs-lookup"><span data-stu-id="33399-139">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
