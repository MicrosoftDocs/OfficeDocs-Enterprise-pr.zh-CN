---
title: 在 Office 365 中查看目录同步状态
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: 了解如何停用目录同步。您还可以查看其状态。
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539841"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="423fb-104">在 Office 365 中查看目录同步状态</span><span class="sxs-lookup"><span data-stu-id="423fb-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="423fb-105">如果具有与 Azure AD 集成您的本地 Active Directory，通过将您的内部部署环境与 Office 365 同步，您还可以检查您同步的状态。</span><span class="sxs-lookup"><span data-stu-id="423fb-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="423fb-106">查看目录同步状态</span><span class="sxs-lookup"><span data-stu-id="423fb-106">View directory synchronization status</span></span>
- <span data-ttu-id="423fb-107">登录到 Office 365 管理中心，并选择在主页上的**目录同步状态**。</span><span class="sxs-lookup"><span data-stu-id="423fb-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="423fb-p102">另外，您可以转到**用户** \> **活动用户**，并在**活动用户**页上选择**多个** \> **目录同步**。在**目录同步**窗格中，选择**转到目录同步管理**。</span><span class="sxs-lookup"><span data-stu-id="423fb-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="423fb-110">在管理目录同步页上的信息</span><span class="sxs-lookup"><span data-stu-id="423fb-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="423fb-111">下表列出了您可以在获得信息的功能。</span><span class="sxs-lookup"><span data-stu-id="423fb-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="423fb-p103">如果使用目录同步问题，以及此页上列出错误。有关不同可能会遇到的错误的详细信息，请参阅[Office 365 中的标识目录同步错误](identify-directory-synchronization-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="423fb-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="423fb-114">**项**</span><span class="sxs-lookup"><span data-stu-id="423fb-114">**Item**</span></span>|<span data-ttu-id="423fb-115">**它为**</span><span class="sxs-lookup"><span data-stu-id="423fb-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="423fb-116">**验证域**</span><span class="sxs-lookup"><span data-stu-id="423fb-116">**Domains verified**</span></span> | <span data-ttu-id="423fb-117">拥有在 Office 365 租户，您必须验证您的域数。</span><span class="sxs-lookup"><span data-stu-id="423fb-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="423fb-118">**未验证的域**</span><span class="sxs-lookup"><span data-stu-id="423fb-118">**Domains not verified**</span></span> | <span data-ttu-id="423fb-119">已添加，但未验证的域。</span><span class="sxs-lookup"><span data-stu-id="423fb-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="423fb-120">**启用目录同步**</span><span class="sxs-lookup"><span data-stu-id="423fb-120">**Directory sync enabled**</span></span> |<span data-ttu-id="423fb-p104">True 或 False。指定是否已启用目录同步。</span><span class="sxs-lookup"><span data-stu-id="423fb-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="423fb-123">**最新的目录同步**</span><span class="sxs-lookup"><span data-stu-id="423fb-123">**Latest directory sync**</span></span> | <span data-ttu-id="423fb-p105">上次运行目录同步。如果将显示一条警告和链接到故障排除工具上次同步已超过三天。</span><span class="sxs-lookup"><span data-stu-id="423fb-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="423fb-126">**启用密码同步**</span><span class="sxs-lookup"><span data-stu-id="423fb-126">**Password sync enabled**</span></span> | <span data-ttu-id="423fb-p106">True 或 False。指定您是否具有我们本地和 Office 365 租户之间的密码哈希同步。</span><span class="sxs-lookup"><span data-stu-id="423fb-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="423fb-129">**最后一个密码同步**</span><span class="sxs-lookup"><span data-stu-id="423fb-129">**Last Password Sync**</span></span> | <span data-ttu-id="423fb-p107">上次密码哈希同步运行。如果将显示一条警告和链接到故障排除工具上次同步已超过三天。</span><span class="sxs-lookup"><span data-stu-id="423fb-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="423fb-132">**目录同步客户端版本**</span><span class="sxs-lookup"><span data-stu-id="423fb-132">**Directory sync client version**</span></span> | <span data-ttu-id="423fb-133">如果已释放新版本的 Azure AD 连接，包含下载链接。</span><span class="sxs-lookup"><span data-stu-id="423fb-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="423fb-134">**IDFix 工具**</span><span class="sxs-lookup"><span data-stu-id="423fb-134">**IDFix Tool**</span></span> | <span data-ttu-id="423fb-135">下载到[IDFix](install-and-run-idfix.md)，您可用于检查您的本地 Active Directory 的工具的链接。</span><span class="sxs-lookup"><span data-stu-id="423fb-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="423fb-136">**目录同步服务帐户**</span><span class="sxs-lookup"><span data-stu-id="423fb-136">**Directory sync service account**</span></span> | <span data-ttu-id="423fb-137">显示您的 Office 365 目录同步服务帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="423fb-137">Displays the name of you Office 365 directory sync service account.</span></span> |