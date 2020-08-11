---
title: 在 Microsoft 365 中查看目录同步状态
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: 在本文中，您将了解如何在 Office 365 中检查目录同步的状态。
ms.openlocfilehash: 9aaad085854326ebb6542f03256ae851b27f0980
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605858"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="5039e-103">在 Microsoft 365 中查看目录同步状态</span><span class="sxs-lookup"><span data-stu-id="5039e-103">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="5039e-104">如果已通过将本地环境与 Microsoft 365 同步，将本地 Active Directory 与 Azure AD 集成，则还可以检查同步的状态。</span><span class="sxs-lookup"><span data-stu-id="5039e-104">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="5039e-105">查看目录同步状态</span><span class="sxs-lookup"><span data-stu-id="5039e-105">View directory synchronization status</span></span>

- <span data-ttu-id="5039e-106">登录到[Microsoft 365 管理中心](https://admin.microsoft.com)，并在主页上选择 " **DirSync Status** "。</span><span class="sxs-lookup"><span data-stu-id="5039e-106">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="5039e-107">或者，您可以转到**用户** \> **活动用户**，并在 "**活动用户**" 页上选择 "**更多** \> **目录同步**"。</span><span class="sxs-lookup"><span data-stu-id="5039e-107">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="5039e-108">在 "**目录同步**" 窗格中，选择 "**转到 DirSync management**"。</span><span class="sxs-lookup"><span data-stu-id="5039e-108">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="5039e-109">"管理目录同步" 页上的信息</span><span class="sxs-lookup"><span data-stu-id="5039e-109">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="5039e-110">下表列出了可以在页面上获取相关信息的功能。</span><span class="sxs-lookup"><span data-stu-id="5039e-110">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="5039e-111">如果目录同步存在问题，则还会在此页面上列出这些错误。</span><span class="sxs-lookup"><span data-stu-id="5039e-111">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="5039e-112">有关可能遇到的不同错误的详细信息，请参阅[确定 Microsoft 365 中的目录同步错误](identify-directory-synchronization-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="5039e-112">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="5039e-113">**项目**</span><span class="sxs-lookup"><span data-stu-id="5039e-113">**Item**</span></span>|<span data-ttu-id="5039e-114">**它有何用途？**</span><span class="sxs-lookup"><span data-stu-id="5039e-114">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5039e-115">**已验证域**</span><span class="sxs-lookup"><span data-stu-id="5039e-115">**Domains verified**</span></span> | <span data-ttu-id="5039e-116">你已验证的 Microsoft 365 租户中的域的数量。</span><span class="sxs-lookup"><span data-stu-id="5039e-116">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="5039e-117">**未验证域**</span><span class="sxs-lookup"><span data-stu-id="5039e-117">**Domains not verified**</span></span> | <span data-ttu-id="5039e-118">已添加但未验证的域。</span><span class="sxs-lookup"><span data-stu-id="5039e-118">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="5039e-119">**目录同步已启用**</span><span class="sxs-lookup"><span data-stu-id="5039e-119">**Directory sync enabled**</span></span> |<span data-ttu-id="5039e-120">True 或 False。</span><span class="sxs-lookup"><span data-stu-id="5039e-120">True or False.</span></span> <span data-ttu-id="5039e-121">指定是否已启用目录同步。</span><span class="sxs-lookup"><span data-stu-id="5039e-121">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="5039e-122">**最新目录同步**</span><span class="sxs-lookup"><span data-stu-id="5039e-122">**Latest directory sync**</span></span> | <span data-ttu-id="5039e-123">上次运行目录同步的时间。</span><span class="sxs-lookup"><span data-stu-id="5039e-123">Last time directory sync ran.</span></span> <span data-ttu-id="5039e-124">如果上一次同步的时间已超过三天，将显示一条警告和指向故障排除工具的链接。</span><span class="sxs-lookup"><span data-stu-id="5039e-124">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="5039e-125">**启用密码同步**</span><span class="sxs-lookup"><span data-stu-id="5039e-125">**Password sync enabled**</span></span> | <span data-ttu-id="5039e-126">True 或 False。</span><span class="sxs-lookup"><span data-stu-id="5039e-126">True or False.</span></span> <span data-ttu-id="5039e-127">指定在内部部署和 Microsoft 365 租户之间是否有密码哈希同步。</span><span class="sxs-lookup"><span data-stu-id="5039e-127">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="5039e-128">**上次密码同步**</span><span class="sxs-lookup"><span data-stu-id="5039e-128">**Last Password Sync**</span></span> | <span data-ttu-id="5039e-129">上次运行密码哈希同步的时间。</span><span class="sxs-lookup"><span data-stu-id="5039e-129">Last time password hash sync ran.</span></span> <span data-ttu-id="5039e-130">如果上一次同步的时间已超过三天，将显示一条警告和指向故障排除工具的链接。</span><span class="sxs-lookup"><span data-stu-id="5039e-130">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="5039e-131">**目录同步客户端版本**</span><span class="sxs-lookup"><span data-stu-id="5039e-131">**Directory sync client version**</span></span> | <span data-ttu-id="5039e-132">如果已发布新版本的 Azure AD Connect，则包含下载链接。</span><span class="sxs-lookup"><span data-stu-id="5039e-132">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="5039e-133">**目录同步服务帐户**</span><span class="sxs-lookup"><span data-stu-id="5039e-133">**Directory sync service account**</span></span> | <span data-ttu-id="5039e-134">显示 Microsoft 365 目录同步服务帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="5039e-134">Displays the name of your Microsoft 365 directory sync service account.</span></span> |