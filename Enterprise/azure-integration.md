---
title: 与 Office 365 的 Azure 集成
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: 你的 Office 365 订阅包括 Azure AD 订阅。如果要使用本地环境进行密码同步或单一登录, 请将 Office 365 与 Azure AD 集成。
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085471"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="4fb97-104">与 Office 365 的 Azure 集成</span><span class="sxs-lookup"><span data-stu-id="4fb97-104">Azure integration with Office 365</span></span>

<span data-ttu-id="4fb97-p102">Office 365 使用 azure Active Directory (azure AD) 管理场景背后的用户身份。Office 365 订阅包括对 azure ad 的免费订阅, 因此, 如果要同步密码或使用本地环境设置单一登录, 则可以将 office 365 与 azure ad 集成。您还可以购买高级功能, 以便更好地管理帐户。</span><span class="sxs-lookup"><span data-stu-id="4fb97-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="4fb97-108">Azure 还提供其他功能 (如管理集成的应用程序), 您可以使用这些功能来扩展和自定义 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="4fb97-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="4fb97-109">您可以使用 Azure AD 部署顾问来实现引导式安装和配置体验:</span><span class="sxs-lookup"><span data-stu-id="4fb97-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="4fb97-110">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="4fb97-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="4fb97-111">AD FS 部署顾问</span><span class="sxs-lookup"><span data-stu-id="4fb97-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="4fb97-112">Azure RMS 部署向导</span><span class="sxs-lookup"><span data-stu-id="4fb97-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="4fb97-113">Azure AD 高级设置指南</span><span class="sxs-lookup"><span data-stu-id="4fb97-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="4fb97-114">Azure AD 版本和 Office 365 身份管理</span><span class="sxs-lookup"><span data-stu-id="4fb97-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="4fb97-p103">如果你已付费订阅 Office 365, 你也可以免费订阅 Azure AD。您可以使用 Azure AD 创建和管理用户和组帐户。若要激活此订阅, 你必须完成一次性注册。之后, 你可以从 Office 365 管理门户访问 Azure AD。有关说明, 请参阅[注册免费的 Azure AD 订阅](https://go.microsoft.com/fwlink/p/?LinkId=617127)。</span><span class="sxs-lookup"><span data-stu-id="4fb97-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="4fb97-p104">按照上面的说明, 注册 Office 365 订阅随附的免费 Azure AD 订阅。请勿直接转到 azure.microsoft.com 进行注册, 否则你将结束与 microsoft azure 的试用版或付费订阅 (与 Office 365 中的免费订阅分开)。</span><span class="sxs-lookup"><span data-stu-id="4fb97-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="4fb97-122">使用免费订阅, 您可以与本地目录同步, 设置单一登录, 并与服务应用程序 (如 Salesforce、DropBox 和更多) 作为服务应用程序与多个软件同步。</span><span class="sxs-lookup"><span data-stu-id="4fb97-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="4fb97-p105">如果需要增强的 AD DS 功能、双向同步和其他管理功能, 可以将免费订阅升级到付费的高级订阅。有关详细信息, 请参阅[Azure Active Directory 版本](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)。</span><span class="sxs-lookup"><span data-stu-id="4fb97-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="4fb97-125">有关 office 365 和 azure AD 的详细信息, 请参阅[了解 office 365 标识和 azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)。</span><span class="sxs-lookup"><span data-stu-id="4fb97-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="4fb97-126">扩展 Office 365 租户的功能</span><span class="sxs-lookup"><span data-stu-id="4fb97-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="4fb97-127">**功能**</span><span class="sxs-lookup"><span data-stu-id="4fb97-127">**Feature**</span></span>|<span data-ttu-id="4fb97-128">**说明**</span><span class="sxs-lookup"><span data-stu-id="4fb97-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4fb97-129">集成应用程序</span><span class="sxs-lookup"><span data-stu-id="4fb97-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="4fb97-p106">您可以向各个应用授予对您的 Office 365 数据 (如邮件、日历、联系人、用户、组、文件和文件夹) 的访问权限。你还可以在全局管理员级别授权这些应用, 并通过在 Azure AD 中注册应用, 使其对你的整个公司可用。有关详细信息, 请参阅[集成应用和适用于 Office 365 的 Azure AD 管理员](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)。</span><span class="sxs-lookup"><span data-stu-id="4fb97-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="4fb97-133">另请参阅[Azure AD 应用程序库和单一登录](https://go.microsoft.com/fwlink/p/?LinkId=698604)。</span><span class="sxs-lookup"><span data-stu-id="4fb97-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="4fb97-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="4fb97-134">PowerApps</span></span>  <br/> | <span data-ttu-id="4fb97-p107">Power apps 是可连接到现有数据源 (如 SharePoint 列表和其他数据应用程序) 的移动设备的重点应用程序。有关详细信息, 请参阅[Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) 。</span><span class="sxs-lookup"><span data-stu-id="4fb97-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="4fb97-137">有关 Microsoft 云和 Office 365 的其他资源, 请参阅以下资源:</span><span class="sxs-lookup"><span data-stu-id="4fb97-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="4fb97-138">面向企业架构师的 Microsoft 云标识</span><span class="sxs-lookup"><span data-stu-id="4fb97-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="4fb97-139">在 Microsoft Azure 中部署 Office 365 目录同步 (DirSync)</span><span class="sxs-lookup"><span data-stu-id="4fb97-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="4fb97-140">有关详细信息[, 请参阅集成应用和 azure ad for Office 365 管理员](integrated-apps-and-azure-ads.md)和[azure ad 应用程序库和单一登录](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)。</span><span class="sxs-lookup"><span data-stu-id="4fb97-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="4fb97-141">Power Apps</span><span class="sxs-lookup"><span data-stu-id="4fb97-141">Power Apps</span></span>
<span data-ttu-id="4fb97-p108">Power apps 是可连接到现有数据源 (如 SharePoint 列表和其他数据应用程序) 的移动设备的重点应用程序。有关详细信息, 请参阅[Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) 。</span><span class="sxs-lookup"><span data-stu-id="4fb97-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>