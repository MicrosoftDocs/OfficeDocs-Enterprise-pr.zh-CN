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
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: 了解如何停用目录同步。 您还可以查看其状态。
ms.openlocfilehash: d6f3a9f1f4e069716501f58e188daedacbf7e597
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906195"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="1ec3d-104">在 Microsoft 365 中查看目录同步状态</span><span class="sxs-lookup"><span data-stu-id="1ec3d-104">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="1ec3d-105">如果已通过将本地环境与 Microsoft 365 同步，将本地 Active Directory 与 Azure AD 集成，则还可以检查同步的状态。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="1ec3d-106">查看目录同步状态</span><span class="sxs-lookup"><span data-stu-id="1ec3d-106">View directory synchronization status</span></span>

- <span data-ttu-id="1ec3d-107">登录到[Microsoft 365 管理中心](https://admin.microsoft.com)，并在主页上选择 " **DirSync Status** "。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="1ec3d-108">或者，您可以转到**用户** \> **活动用户**，并在 "**活动用户**" 页上选择 "**更多** \> **目录同步**"。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="1ec3d-109">在 "**目录同步**" 窗格中，选择 "**转到 DirSync management**"。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="1ec3d-110">"管理目录同步" 页上的信息</span><span class="sxs-lookup"><span data-stu-id="1ec3d-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="1ec3d-111">下表列出了可以在页面上获取相关信息的功能。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="1ec3d-112">如果目录同步存在问题，则还会在此页面上列出这些错误。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="1ec3d-113">有关可能遇到的不同错误的详细信息，请参阅[确定 Microsoft 365 中的目录同步错误](identify-directory-synchronization-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="1ec3d-114">**项**</span><span class="sxs-lookup"><span data-stu-id="1ec3d-114">**Item**</span></span>|<span data-ttu-id="1ec3d-115">**它有何用途？**</span><span class="sxs-lookup"><span data-stu-id="1ec3d-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="1ec3d-116">**已验证域**</span><span class="sxs-lookup"><span data-stu-id="1ec3d-116">**Domains verified**</span></span> | <span data-ttu-id="1ec3d-117">你已验证的 Microsoft 365 租户中的域的数量。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-117">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="1ec3d-118">**未验证域**</span><span class="sxs-lookup"><span data-stu-id="1ec3d-118">**Domains not verified**</span></span> | <span data-ttu-id="1ec3d-119">已添加但未验证的域。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="1ec3d-120">**目录同步已启用**</span><span class="sxs-lookup"><span data-stu-id="1ec3d-120">**Directory sync enabled**</span></span> |<span data-ttu-id="1ec3d-121">True 或 False。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-121">True or False.</span></span> <span data-ttu-id="1ec3d-122">指定是否已启用目录同步。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="1ec3d-123">**最新目录同步**</span><span class="sxs-lookup"><span data-stu-id="1ec3d-123">**Latest directory sync**</span></span> | <span data-ttu-id="1ec3d-124">上次运行目录同步的时间。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-124">Last time directory sync ran.</span></span> <span data-ttu-id="1ec3d-125">如果上一次同步的时间已超过三天，将显示一条警告和指向故障排除工具的链接。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="1ec3d-126">**启用密码同步**</span><span class="sxs-lookup"><span data-stu-id="1ec3d-126">**Password sync enabled**</span></span> | <span data-ttu-id="1ec3d-127">True 或 False。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-127">True or False.</span></span> <span data-ttu-id="1ec3d-128">指定在内部部署和 Microsoft 365 租户之间是否有密码哈希同步。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-128">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="1ec3d-129">**上次密码同步**</span><span class="sxs-lookup"><span data-stu-id="1ec3d-129">**Last Password Sync**</span></span> | <span data-ttu-id="1ec3d-130">上次运行密码哈希同步的时间。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-130">Last time password hash sync ran.</span></span> <span data-ttu-id="1ec3d-131">如果上一次同步的时间已超过三天，将显示一条警告和指向故障排除工具的链接。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="1ec3d-132">**目录同步客户端版本**</span><span class="sxs-lookup"><span data-stu-id="1ec3d-132">**Directory sync client version**</span></span> | <span data-ttu-id="1ec3d-133">如果已发布新版本的 Azure AD Connect，则包含下载链接。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="1ec3d-134">**IDFix 工具**</span><span class="sxs-lookup"><span data-stu-id="1ec3d-134">**IDFix Tool**</span></span> | <span data-ttu-id="1ec3d-135">下载指向[IDFix](install-and-run-idfix.md)的链接，可用于检查本地 Active Directory 的工具。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="1ec3d-136">**目录同步服务帐户**</span><span class="sxs-lookup"><span data-stu-id="1ec3d-136">**Directory sync service account**</span></span> | <span data-ttu-id="1ec3d-137">显示 Microsoft 365 目录同步服务帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="1ec3d-137">Displays the name of your Microsoft 365 directory sync service account.</span></span> |