---
title: OneDrive 和 SharePoint Online 中的多地理位置功能
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: 利用 OneDrive Online 中的多地理位置功能将 Office 365 的触及范围扩展到多个地理区域。
ms.openlocfilehash: 15dcb44943fa1bf331ef6260946f7c3a632d3c4a
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948583"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a><span data-ttu-id="d75fb-103">OneDrive 和 SharePoint Online 中的多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="d75fb-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="d75fb-104">利用 OneDrive 和 SharePoint Online 中的多地理位置功能，可以控制在其中静态存储共享资源（比如 SharePoint 团队站点和 Office 365 组邮箱）的国家或地区。</span><span class="sxs-lookup"><span data-stu-id="d75fb-104">Multi-Geo capabilities in OneDrive and SharePoint Online enables control of the country or region where shared resources like SharePoint team sites and Office 365 Group mailboxes are stored at rest.</span></span>

<span data-ttu-id="d75fb-105">每个用户、组邮箱和 SharePoint 站点都有一个首选数据位置 (PDL)，表示要在其中存储相关数据的地理位置。</span><span class="sxs-lookup"><span data-stu-id="d75fb-105">Each user, Group mailbox, and SharePoint site has a Preferred Data Location (PDL) which denotes the geo location where related data is to be stored.</span></span> <span data-ttu-id="d75fb-106">可将用户的个人数据（Exchange 邮箱和 OneDrive）以及用户创建的任何 Office 365 组或 SharePoint 站点存储在指定地理位置，以满足数据驻留要求。</span><span class="sxs-lookup"><span data-stu-id="d75fb-106">Users' personal data (Exchange mailbox and OneDrive) along with any Office 365 Groups or SharePoint sites that they create can be stored in the specified geo location to meet data residency requirements.</span></span> <span data-ttu-id="d75fb-107">你可以[为每个地理位置指定不同的管理员](add-a-sharepoint-geo-admin.md)。</span><span class="sxs-lookup"><span data-stu-id="d75fb-107">You can [specify different administrators for each geo location](add-a-sharepoint-geo-admin.md).</span></span>

<span data-ttu-id="d75fb-108">用户在使用 Office 365 服务（包括 Office 应用程序、OneDrive 和搜索）时将能获得无缝体验。</span><span class="sxs-lookup"><span data-stu-id="d75fb-108">Users get a seamless experience when using Office 365 services, including Office applications, OneDrive, and Search.</span></span> <span data-ttu-id="d75fb-109">有关详细信息，请参阅[多地理位置环境中的用户体验](multi-geo-user-experience.md)。</span><span class="sxs-lookup"><span data-stu-id="d75fb-109">See [User experience in a multi-geo environment](multi-geo-user-experience.md) for details.</span></span>

## <a name="onedrive"></a><span data-ttu-id="d75fb-110">OneDrive</span><span class="sxs-lookup"><span data-stu-id="d75fb-110">OneDrive</span></span>

<span data-ttu-id="d75fb-111">管理员可依据用户的 PDL 配置每个用户的 OneDrive，或[将其移至](move-onedrive-between-geo-locations.md)附属位置。</span><span class="sxs-lookup"><span data-stu-id="d75fb-111">Each user's OneDrive can be provisioned in or [moved by an administrator](move-onedrive-between-geo-locations.md) to a satellite location in accordance with the user's PDL.</span></span> <span data-ttu-id="d75fb-112">个人文件随后保留在该地理位置中，不过可以将这些文件与其他地理位置中的用户共享。</span><span class="sxs-lookup"><span data-stu-id="d75fb-112">Personal files are then kept in that geo location, though they can be shared with users in other geo locations.</span></span>

## <a name="sites-and-groups"></a><span data-ttu-id="d75fb-113">站点和组</span><span class="sxs-lookup"><span data-stu-id="d75fb-113">Active Directory Sites and Routing Groups tab</span></span>

<span data-ttu-id="d75fb-114">当用户创建 SharePoint 组连接的站点时，将使用他们的 PDL 来确定在其中创建站点及其关联组邮箱的地理位置。</span><span class="sxs-lookup"><span data-stu-id="d75fb-114">When a user creates a SharePoint group-connected site, their PDL is used to determine the geo location where the site and its associated Group mailbox is created.</span></span> <span data-ttu-id="d75fb-115">（如果尚未设置用户的 PDL 值，或已将其设置为未配置为附属位置的地理位置，则会在中心位置创建站点和邮箱。）</span><span class="sxs-lookup"><span data-stu-id="d75fb-115">(If the user's PDL value hasn't been set, or has been set to geo location that hasn't been configured as a satellite location, then the site and mailbox are created in the central location.)</span></span>

<span data-ttu-id="d75fb-116">除 Exchange、OneDrive 和 SharePoint 外的其他 Office 365 服务都不是多地理位置服务。</span><span class="sxs-lookup"><span data-stu-id="d75fb-116">Office 365 services other than Exchange, OneDrive, and SharePoint are not Multi-Geo.</span></span> <span data-ttu-id="d75fb-117">但是，通过这些服务创建的 Office 365 组带有创建者的 PDL 的印记，并将在对应的地理位置中设置其 Exchange 组邮箱和 SharePoint O365 组站点。</span><span class="sxs-lookup"><span data-stu-id="d75fb-117">However, Office 365 Groups that are created by these services will be stamped with the PDL of the creator and their Exchange Group mailbox and SharePoint O365 Group Site provisioned in the corresponding geo.</span></span> 

## <a name="managing-the-multi-geo-environment"></a><span data-ttu-id="d75fb-118">管理多地理位置环境</span><span class="sxs-lookup"><span data-stu-id="d75fb-118">Managing the multi-geo environment</span></span>

<span data-ttu-id="d75fb-119">多地理位置环境的设置和管理是通过 SharePoint 管理中心完成的。</span><span class="sxs-lookup"><span data-stu-id="d75fb-119">Setting up and managing your multi-geo environment is done through the SharePoint admin center.</span></span> 

![SharePoint 管理中心中地理位置页面的屏幕截图](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="d75fb-121">（诸如移动 SharePoint 站点或 OneDrive 站点的某些操作需要 Microsoft PowerShell。）</span><span class="sxs-lookup"><span data-stu-id="d75fb-121">(Some actions, such as moving a SharePoint site or a OneDrive site require Microsoft PowerShell.)</span></span>

## <a name="see-also"></a><span data-ttu-id="d75fb-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d75fb-122">See also</span></span>

[<span data-ttu-id="d75fb-123">亦称 ms/GetMultiGeo </span><span class="sxs-lookup"><span data-stu-id="d75fb-123">Aka.ms/GetMultiGeo </span></span>](https://Aka.ms/GetMultiGeo)

[<span data-ttu-id="d75fb-124">管理多地理位置环境</span><span class="sxs-lookup"><span data-stu-id="d75fb-124">Administering a multi-geo environment</span></span>](administering-a-multi-geo-environment.md)

[<span data-ttu-id="d75fb-125">多地理位置环境中的 SharePoint 存储配额</span><span class="sxs-lookup"><span data-stu-id="d75fb-125">SharePoint storage quotas in multi-geo environments</span></span>](sharepoint-multi-geo-storage-quota.md)

[<span data-ttu-id="d75fb-126">在多地理位置环境中管理 Exchange Online 邮箱</span><span class="sxs-lookup"><span data-stu-id="d75fb-126">Administering Exchange Online mailboxes in a multi-geo environment</span></span>](administering-exchange-online-multi-geo.md)
