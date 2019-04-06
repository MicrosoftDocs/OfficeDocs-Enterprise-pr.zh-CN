---
title: Exchange 多地理位置
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 了解 Exchange Online 中的多地理位置功能。
ms.openlocfilehash: 60d25cab08ada195d1b189b30bdce8ea505f1d19
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931771"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="79cb1-103">Exchange Online 中的多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="79cb1-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="79cb1-104">在多地理位置环境中, 您可以在每个用户的基础上选择 Exchange Online 邮箱内容 (静态数据) 的位置。</span><span class="sxs-lookup"><span data-stu-id="79cb1-104">In a multi-geo environment, you can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="79cb1-105">您可以通过以下方式将邮箱放置在附属位置:</span><span class="sxs-lookup"><span data-stu-id="79cb1-105">You can place mailboxes in satellite locations by:</span></span>

- <span data-ttu-id="79cb1-106">在卫星位置中直接创建新的 Exchange Online 邮箱</span><span class="sxs-lookup"><span data-stu-id="79cb1-106">Creating a new Exchange Online mailbox directly in a satellite location</span></span>

- <span data-ttu-id="79cb1-107">通过更改用户的首选数据位置将现有 Exchange Online 邮箱移动到附属位置</span><span class="sxs-lookup"><span data-stu-id="79cb1-107">Moving an existing Exchange Online mailbox to a satellite location by changing the user's preferred data location</span></span>

- <span data-ttu-id="79cb1-108">将邮箱从本地 Exchange 组织直接加入到附属位置</span><span class="sxs-lookup"><span data-stu-id="79cb1-108">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite location</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="79cb1-109">邮箱放置和移动</span><span class="sxs-lookup"><span data-stu-id="79cb1-109">Mailbox placement and moves</span></span>
<span data-ttu-id="79cb1-110">Microsoft 完成先决条件多地理位置配置步骤后, Exchange Online 将服从 Azure AD 中用户对象的**PreferredDataLocation**属性。</span><span class="sxs-lookup"><span data-stu-id="79cb1-110">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="79cb1-111">exchange online 将 Azure AD 中的**PreferredDataLocation**属性同步到 Exchange Online 目录服务中的**MailboxRegion**属性。</span><span class="sxs-lookup"><span data-stu-id="79cb1-111">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service.</span></span> <span data-ttu-id="79cb1-112">**MailboxRegion**的值决定了将放置用户邮箱和任何相关联的存档邮箱的地理位置。</span><span class="sxs-lookup"><span data-stu-id="79cb1-112">The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed.</span></span> <span data-ttu-id="79cb1-113">不能将用户的主邮箱和存档邮箱配置为驻留在不同的地理位置。</span><span class="sxs-lookup"><span data-stu-id="79cb1-113">It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations.</span></span> <span data-ttu-id="79cb1-114">每个 user 对象仅可配置一个地理位置。</span><span class="sxs-lookup"><span data-stu-id="79cb1-114">Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="79cb1-115">当在具有现有邮箱的用户上配置**PreferredDataLocation**时, 邮箱将被放入一个重新定位队列并自动移到指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="79cb1-115">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span> 

- <span data-ttu-id="79cb1-116">如果在没有现有邮箱的用户上配置了**PreferredDataLocation** , 则在设置邮箱时, 它将预配到指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="79cb1-116">When **PreferredDataLocation** is configured on a user without an existing mailbox, when you provision the mailbox, it will be provisioned into the specified geo location.</span></span> 

- <span data-ttu-id="79cb1-117">如果未在用户上指定**PreferredDataLocation** , 则在设置邮箱时, 它将在中心位置进行设置。</span><span class="sxs-lookup"><span data-stu-id="79cb1-117">When **PreferredDataLocation** is not specified on a user, when you provision the mailbox, it will be provisioned in the central location.</span></span>

- <span data-ttu-id="79cb1-118">如果**PreferredDataLocation**代码不正确 (例如, 类型为 NAN, 而不是是, 则在中心位置设置邮箱。</span><span class="sxs-lookup"><span data-stu-id="79cb1-118">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be provisioned in the central location.</span></span>

<span data-ttu-id="79cb1-119">**注意**: 多地理位置功能和 Skype for business Online 地区组织托管会议都使用 user 对象的**PreferredDataLocation**属性来查找服务。</span><span class="sxs-lookup"><span data-stu-id="79cb1-119">**Note**: multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services.</span></span> <span data-ttu-id="79cb1-120">如果为地区组织托管会议的用户对象配置**PreferredDataLocation**值, 则在 Office 365 租户上启用多地理位置之后, 这些用户的邮箱将自动移到指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="79cb1-120">If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="79cb1-121">Exchange Online 中多地理位置的功能限制</span><span class="sxs-lookup"><span data-stu-id="79cb1-121">Feature limitations for multi-geo in Exchange Online</span></span>

1. <span data-ttu-id="79cb1-122">Exchange 管理中心 (EAC) 中可用的安全性和合规性功能 (例如, 审核和电子数据展示) 在多地理位置组织中不可用。</span><span class="sxs-lookup"><span data-stu-id="79cb1-122">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations.</span></span> <span data-ttu-id="79cb1-123">相反, 您需要使用[Office 365 安全 & 合规中心](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)来配置安全和合规性功能。</span><span class="sxs-lookup"><span data-stu-id="79cb1-123">Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

2. <span data-ttu-id="79cb1-124">Outlook for Mac 用户在将其邮箱移动到新的地理位置时, 可能会遇到临时丢失对其联机存档文件夹的访问权限。</span><span class="sxs-lookup"><span data-stu-id="79cb1-124">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location.</span></span> <span data-ttu-id="79cb1-125">如果用户的主邮箱和存档邮箱位于不同的地理位置, 则会出现这种情况, 这是因为跨地区邮箱移动可能在不同的时间完成。</span><span class="sxs-lookup"><span data-stu-id="79cb1-125">This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-geo mailbox moves may complete at different times.</span></span>

3. <span data-ttu-id="79cb1-126">用户无法在 Outlook 网页版 (以前称为 Outlook web App 或 OWA) 的各个地理位置共享*邮箱文件夹*。</span><span class="sxs-lookup"><span data-stu-id="79cb1-126">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA).</span></span> <span data-ttu-id="79cb1-127">例如, 欧盟中的用户无法使用 web 上的 Outlook 打开位于美国的邮箱中的共享文件夹。</span><span class="sxs-lookup"><span data-stu-id="79cb1-127">For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States.</span></span> <span data-ttu-id="79cb1-128">但是, Web 上的 outlook 用户可以使用单独的浏览器窗口打开不同信息中的*其他邮箱*, 如在[Outlook Web App 中的单独浏览器窗口中打开其他人的邮箱](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)中所述。</span><span class="sxs-lookup"><span data-stu-id="79cb1-128">However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="79cb1-129">**注意**: 在 Windows 上的 Outlook 中支持跨地区邮箱文件夹共享。</span><span class="sxs-lookup"><span data-stu-id="79cb1-129">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

