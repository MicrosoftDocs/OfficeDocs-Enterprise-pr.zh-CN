---
title: Exchange 多地理位置
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: 了解 Exchange Online 中的多地理位置功能。
ms.openlocfilehash: 034631d10cc46fc24a7714dee13ddfc667272a49
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974834"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="676ef-103">Exchange Online 中的多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="676ef-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="676ef-104">在多地理位置环境中，可以基于每个用户选择 Exchange Online 邮箱内容（静态数据）的位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-104">In a multi-geo environment, you can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="676ef-105">你可以通过以下方式将邮箱放置在卫星地理位置：</span><span class="sxs-lookup"><span data-stu-id="676ef-105">You can place mailboxes in satellite geo locations by:</span></span>

- <span data-ttu-id="676ef-106">直接在卫星地理位置创建新的 Exchange Online 邮箱。</span><span class="sxs-lookup"><span data-stu-id="676ef-106">Creating a new Exchange Online mailbox directly in a satellite geo location.</span></span>

- <span data-ttu-id="676ef-107">通过更改用户的首选数据位置，将现有 Exchange Online 邮箱移动到卫星地理位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-107">Moving an existing Exchange Online mailbox to a satellite geo location by changing the user's preferred data location.</span></span>

- <span data-ttu-id="676ef-108">将邮箱从内部部署 Exchange 组织直接挂载到卫星地理位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-108">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite geo location.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="676ef-109">邮箱放置和移动</span><span class="sxs-lookup"><span data-stu-id="676ef-109">Mailbox placement and moves</span></span>

<span data-ttu-id="676ef-110">Microsoft 完成必备的多地理位置配置步骤后，Exchange Online 将遵循 Azure AD 中用户对象的 **PreferredDataLocation** 属性。</span><span class="sxs-lookup"><span data-stu-id="676ef-110">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="676ef-111">Exchange Online 将 **PreferredDataLocation** 属性从 Azure AD 同步到 Exchange Online 目录服务中的 **MailboxRegion** 属性。</span><span class="sxs-lookup"><span data-stu-id="676ef-111">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service.</span></span> <span data-ttu-id="676ef-112">**MailboxRegion** 的值确定将放置用户邮箱和任何相关存档邮箱的地理位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-112">The value of **MailboxRegion** determines the geo location where user mailboxes and any associated archive mailboxes will be placed.</span></span> <span data-ttu-id="676ef-113">无法将用户的主邮箱和存档邮箱配置为驻留在不同的地理位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-113">It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations.</span></span> <span data-ttu-id="676ef-114">每个用户对象只能配置一个地理位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-114">Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="676ef-115">在具有现有邮箱的用户上配置 **PreferredDataLocation** 时，邮箱将被放入重定位队列，并自动移动到指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-115">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span>

- <span data-ttu-id="676ef-116">如果在没有现有邮箱的用户上配置 **PreferredDataLocation**，则在配置邮箱时，它将被配置到指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-116">When **PreferredDataLocation** is configured on a user without an existing mailbox, when you provision the mailbox, it will be provisioned into the specified geo location.</span></span>

- <span data-ttu-id="676ef-117">如果用户上未指定 **PreferredDataLocation**，则在配置邮箱时，它将被配置在中心地理位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-117">When **PreferredDataLocation** is not specified on a user, when you provision the mailbox, it will be provisioned in the central geo location.</span></span>

- <span data-ttu-id="676ef-118">如果 **PreferredDataLocation** 代码不正确（例如，类型为 NAN 而不是 NAM），则邮箱将被配置在中心地理位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-118">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be provisioned in the central geo location.</span></span>

<span data-ttu-id="676ef-119">**注意**：多地理位置功能和 Skype for Business Online 区域性托管会议都使用用户对象上的 **PreferredDataLocation** 属性来定位服务。</span><span class="sxs-lookup"><span data-stu-id="676ef-119">**Note**: Multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services.</span></span> <span data-ttu-id="676ef-120">如果在区域托管会议的用户对象上配置 **PreferredDataLocation** 值，则在 Office 365 租户上启用多地理位置后，这些用户的邮箱将自动移动到指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-120">If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="676ef-121">Exchange Online 中多地理位置的功能限制</span><span class="sxs-lookup"><span data-stu-id="676ef-121">Feature limitations for multi-geo in Exchange Online</span></span>

- <span data-ttu-id="676ef-122">Exchange 管理中心 (EAC) 中提供的安全性和合规性功能（例如，审核和电子数据展示）在多地理位置组织中不可用。</span><span class="sxs-lookup"><span data-stu-id="676ef-122">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations.</span></span> <span data-ttu-id="676ef-123">你需要改用 [Office 365 安全与合规中心](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)来配置安全性和合规性功能。</span><span class="sxs-lookup"><span data-stu-id="676ef-123">Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

- <span data-ttu-id="676ef-124">当你将 Outlook for Mac 用户的邮箱移动到新的地理位置时，他们可能会暂时无法访问其在线存档文件夹。</span><span class="sxs-lookup"><span data-stu-id="676ef-124">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location.</span></span> <span data-ttu-id="676ef-125">当用户的主邮箱和存档邮箱位于不同的地理位置时，会出现这种情况，因为跨地理位置邮箱移动可能会在不同时间完成。</span><span class="sxs-lookup"><span data-stu-id="676ef-125">This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-geo mailbox moves may complete at different times.</span></span>

- <span data-ttu-id="676ef-126">用户无法在 Web 上的 Outlook（以前称为 Outlook Web App 或 OWA）中跨地理位置共享*邮箱文件夹*。</span><span class="sxs-lookup"><span data-stu-id="676ef-126">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA).</span></span> <span data-ttu-id="676ef-127">例如，欧盟的用户无法使用 Web 上的 Outlook 打开位于美国的邮箱中的共享文件夹。</span><span class="sxs-lookup"><span data-stu-id="676ef-127">For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States.</span></span> <span data-ttu-id="676ef-128">但是，Web 上的 Outlook 用户可以使用单独的浏览器窗口打开不同地理位置中的*其他邮箱*，如[在 Outlook Web App 的单独浏览器窗口中打开其他人的邮箱](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)中所述。</span><span class="sxs-lookup"><span data-stu-id="676ef-128">However, Outlook on the Web users can open *other mailboxes* in different geo locations by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

  <span data-ttu-id="676ef-129">**注意**：Windows 上的 Outlook 支持跨地理位置邮箱文件夹共享。</span><span class="sxs-lookup"><span data-stu-id="676ef-129">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

- <span data-ttu-id="676ef-130">多地理位置组织支持公用文件夹。</span><span class="sxs-lookup"><span data-stu-id="676ef-130">Public folders are supported in multi-geo organizations.</span></span> <span data-ttu-id="676ef-131">但是，公用文件夹必须保留在中心地理位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-131">However, the public folders must remain in the central geo location.</span></span> <span data-ttu-id="676ef-132">无法将公用文件夹移动到卫星地理位置。</span><span class="sxs-lookup"><span data-stu-id="676ef-132">You can't move public folders to satellite geo locations.</span></span>
