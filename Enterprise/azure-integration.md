---
title: 与 Office 365 的 azure 集成
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Office 365 订阅包括订阅 Azure AD。将 Office 365 与 Azure AD 集成，如果您希望与您的本地环境密码同步还是单一登录。
ms.openlocfilehash: abeda5eb915ac4ff9e395ab3b28f1e0cb7a68163
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2018
ms.locfileid: "21550076"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="4047e-104">与 Office 365 的 azure 集成</span><span class="sxs-lookup"><span data-stu-id="4047e-104">Azure integration with Office 365</span></span>

<span data-ttu-id="4047e-p102">Office 365 使用 Azure Active Directory (Azure AD) 来管理用户标识后台。Office 365 订阅包括免费订阅 Azure AD，以便您可以与 Azure AD 集成 Office 365，如果您想要同步密码或与您的本地环境的单一登录设置。您还可以购买高级的功能，以更好地管理您的帐户。</span><span class="sxs-lookup"><span data-stu-id="4047e-p102">Office 365 uses Azure Active Directory (Azure AD)to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="4047e-108">Azure 还提供其他一些功能，如管理集成的应用程序，可用于扩展和自定义 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="4047e-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="4047e-109">您还可以使用 Azure AD 顾问： [Azure AD 连接顾问](https://aka.ms/aadconnectpwsync)、 [AD FS 部署顾问](https://aka.ms/adfsguidance)、 [Azure RMS Deploymnet 向导](https://aka.ms/azuremsguidance)和[Azure AD Premium 安装指南](https://aka.ms/aadpguidance)。</span><span class="sxs-lookup"><span data-stu-id="4047e-109">You can also use the Azure AD advisors: the [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync), the [AD FS deployment advisor](https://aka.ms/adfsguidance), the [Azure RMS Deploymnet Wizard](https://aka.ms/azuremsguidance), and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance).</span></span>
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="4047e-110">Azure AD 版本和 Office 365 标识管理</span><span class="sxs-lookup"><span data-stu-id="4047e-110">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="4047e-p103">如果您具有付费的 Office 365 订阅，您还可以免费订阅 Azure AD。Azure AD 可用于创建和管理用户和组帐户。若要激活此订阅您必须完成一次性注册。此后，您可以从您的 Office 365 管理门户访问 Azure AD。有关说明，请参阅[注册免费 Azure AD 订阅](https://go.microsoft.com/fwlink/p/?LinkId=617127)。</span><span class="sxs-lookup"><span data-stu-id="4047e-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="4047e-p104">注册免费的 Azure AD 订阅附带到 Office 365 订阅到按照上方的说明。不直接转到 Azure.Microsoft.com 注册或您将结尾独立于您免费一个用于 Office 365 的 Microsoft Azure 试用版或付费订阅。</span><span class="sxs-lookup"><span data-stu-id="4047e-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to Azure.Microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="4047e-118">与免费订阅可以与内部部署目录同步，设置单一登录，并将与多个软件同步作为服务应用程序，如销售队伍、 收存箱及更多。</span><span class="sxs-lookup"><span data-stu-id="4047e-118">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="4047e-p105">如果您希望 AD DS 的增强的功能、 双向同步和其他管理功能，则可以将免费订阅升级为付费的 premium 订阅。有关详细信息，请参阅[Azure Active Directory 版本](https://go.microsoft.com/fwlink/p/?LinkId=524280)。</span><span class="sxs-lookup"><span data-stu-id="4047e-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=524280).</span></span>
  
<span data-ttu-id="4047e-121">有关 Office 365 和 Azure AD 的详细信息，请参阅[了解 Office 365 标识和 Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)。</span><span class="sxs-lookup"><span data-stu-id="4047e-121">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="4047e-122">扩展 Office 365 租户的功能</span><span class="sxs-lookup"><span data-stu-id="4047e-122">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="4047e-123">**功能**</span><span class="sxs-lookup"><span data-stu-id="4047e-123">**Feature**</span></span>|<span data-ttu-id="4047e-124">**说明**</span><span class="sxs-lookup"><span data-stu-id="4047e-124">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4047e-125">集成的应用程序</span><span class="sxs-lookup"><span data-stu-id="4047e-125">Integrated apps</span></span>  <br/> |<span data-ttu-id="4047e-p106">您可以授予各个应用程序访问 Office 365 数据，如邮件、 日历、 联系人、 用户、 组、 文件和文件夹。您还可以授权全局管理员级别这些应用程序，并使其可供整个公司使用 Azure AD 中注册应用程序。有关详细信息，请参阅[集成的应用程序和 Office 365 管理员的 Azure AD](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)。</span><span class="sxs-lookup"><span data-stu-id="4047e-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="4047e-129">另请参阅[Azure AD 应用程序库和单点登录](https://go.microsoft.com/fwlink/p/?LinkId=698604)。</span><span class="sxs-lookup"><span data-stu-id="4047e-129">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="4047e-130">PowerApps</span><span class="sxs-lookup"><span data-stu-id="4047e-130">PowerApps</span></span>  <br/> | <span data-ttu-id="4047e-p107">电源应用程序是重点相关应用程序可以连接到现有数据源，如 SharePoint 列表的移动设备和其他数据应用程序。有关详细信息，请参阅[创建有关 SharePoint Online 中的列表 PowerApp](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)和[PowerApps 页](https://powerapps.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="4047e-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="4047e-133">有关 Microsoft 云和 Office 365 的其他资源，请参阅以下资源：</span><span class="sxs-lookup"><span data-stu-id="4047e-133">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="4047e-134">面向企业架构师的 Microsoft 云标识</span><span class="sxs-lookup"><span data-stu-id="4047e-134">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=828642)
    
- [<span data-ttu-id="4047e-135">在 Microsoft Azure 中部署 Office 365 目录同步 (DirSync)</span><span class="sxs-lookup"><span data-stu-id="4047e-135">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

