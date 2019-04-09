---
title: Office 365 客户端应用程序支持-移动应用程序管理
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
description: 了解 Office 365 客户端应用程序对移动应用程序管理的支持
ms.openlocfilehash: b75b992bf45ff1a899e71a9f6b7903e3f78a34d4
ms.sourcegitcommit: 80bc767a9c88a259facb3894b9a168c85d35eb70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "31517546"
---
# <a name="office-365-client-app-support---mobile-application-management"></a><span data-ttu-id="194e4-103">Office 365 客户端应用程序支持-移动应用程序管理</span><span class="sxs-lookup"><span data-stu-id="194e4-103">Office 365 Client App Support - Mobile Application Management</span></span>

<span data-ttu-id="194e4-104">通过利用 Intune 管理功能套件, 移动应用程序管理 (MAM) 可让你为用户发布、推送、配置、保护、监视和更新移动应用。</span><span class="sxs-lookup"><span data-stu-id="194e4-104">Leveraging the suite of Intune management features, mobile application management (MAM) lets you publish, push, configure, secure, monitor, and update mobile apps for your users.</span></span> <span data-ttu-id="194e4-105">在 Intune 中是否已注册, MAM 可以保护所有设备的应用程序内的组织数据。</span><span class="sxs-lookup"><span data-stu-id="194e4-105">MAM can protect an organization's data within an application for all devices, whether enrolled in Intune or not.</span></span>

<span data-ttu-id="194e4-106">了解有关[移动应用程序管理](https://docs.microsoft.com/intune/mam-faq)和[多标识 MAM](https://docs.microsoft.com/intune/app-protection-policy)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="194e4-106">Learn more about [mobile application management](https://docs.microsoft.com/intune/mam-faq) and [multi-identity MAM](https://docs.microsoft.com/intune/app-protection-policy).</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="194e4-107">支持的平台</span><span class="sxs-lookup"><span data-stu-id="194e4-107">Supported platforms</span></span>

 - <span data-ttu-id="194e4-108">Android</span><span class="sxs-lookup"><span data-stu-id="194e4-108">Android</span></span>
 - <span data-ttu-id="194e4-109">iOS<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="194e4-109">iOS<sup>1</sup></span></span>

<span data-ttu-id="194e4-110">有关 office 365 中平台支持的详细信息, 请参阅[office 365 的系统要求](https://products.office.com/office-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="194e4-110">For more information about platform support in Office 365, see [System requirements for Office 365](https://products.office.com/office-system-requirements).</span></span>

## <a name="supported-clients"></a><span data-ttu-id="194e4-111">支持的客户端</span><span class="sxs-lookup"><span data-stu-id="194e4-111">Supported clients</span></span>

<span data-ttu-id="194e4-112">以下客户端的最新版本支持移动应用程序管理:</span><span class="sxs-lookup"><span data-stu-id="194e4-112">The latest versions of the following clients support mobile application management:</span></span>

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Dynamics 365 图标](media/o365-dynamics365-64x64.png) <br> [<span data-ttu-id="194e4-114">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="194e4-114">Dynamics 365</span></span>](https://dynamics.microsoft.com) | ![边缘图标](media/o365-edge-64x64.png) <br> [<span data-ttu-id="194e4-116">边线</span><span class="sxs-lookup"><span data-stu-id="194e4-116">Edge</span></span>](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 图标](media/o365-excel-64x64.png) <br> [<span data-ttu-id="194e4-118">Excel</span><span class="sxs-lookup"><span data-stu-id="194e4-118">Excel</span></span>](https://products.office.com/excel) | ![流图标](media/o365-flow-64x64.png) <br> [<span data-ttu-id="194e4-120">流程</span><span class="sxs-lookup"><span data-stu-id="194e4-120">Flow</span></span>](https://flow.microsoft.com) | ![Kaizala 图标](media/o365-kaizala-64x64.png) <br> [<span data-ttu-id="194e4-122">Kaizala</span><span class="sxs-lookup"><span data-stu-id="194e4-122">Kaizala</span></span>](https://products.office.com/en/business/microsoft-kaizala) 
| ![OneDrive for business 图标](media/o365-OneDrive-64x64.png) <br> [<span data-ttu-id="194e4-124">OneDrive</span><span class="sxs-lookup"><span data-stu-id="194e4-124">OneDrive</span></span>](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 图标](media/o365-OneNote-64x64.png) <br> [<span data-ttu-id="194e4-126">OneNote</span><span class="sxs-lookup"><span data-stu-id="194e4-126">OneNote</span></span>](https://products.office.com/onenote) | ![Outlook 图标](media/o365-outlook-64x64.png) <br> [<span data-ttu-id="194e4-128">Outlook</span><span class="sxs-lookup"><span data-stu-id="194e4-128">Outlook</span></span>](https://products.office.com/outlook) | ![Planner 图标](media/o365-planner-64x64.png) <br> [<span data-ttu-id="194e4-130">规划器</span><span class="sxs-lookup"><span data-stu-id="194e4-130">Planner</span></span>](https://products.office.com/business/task-management-software) | ![PowerApps 图标](media/o365-powerapps-64x64.png) <br> [<span data-ttu-id="194e4-132">PowerApps</span><span class="sxs-lookup"><span data-stu-id="194e4-132">PowerApps</span></span> ](https://powerapps.microsoft.com) 
| ![PowerBI 图标](media/o365-powerbi-64x64.png) <br> [<span data-ttu-id="194e4-134">Power BI</span><span class="sxs-lookup"><span data-stu-id="194e4-134">Power BI</span></span>](https://powerbi.microsoft.com) | ![PowerPoint 图标](media/o365-powerpoint-64x64.png) <br> [<span data-ttu-id="194e4-136">PowerPoint</span><span class="sxs-lookup"><span data-stu-id="194e4-136">PowerPoint</span></span>](https://products.office.com/powerpoint) | ![SharePoint 图标](media/o365-sharepoint-64x64.png) <br> [<span data-ttu-id="194e4-138">Sharepoint</span><span class="sxs-lookup"><span data-stu-id="194e4-138">Sharepoint</span></span>](https://products.office.com/sharepoint) | ![Skype for business 图标](media/o365-skypeforbusiness-64x64.png) <br> [<span data-ttu-id="194e4-140">Skype for <br> business</span><span class="sxs-lookup"><span data-stu-id="194e4-140">Skype for <br> Business</span></span>](https://www.skype.com/business/) | ![StaffHub 图标](media/o365-staffhub-64x64.png) <br> [<span data-ttu-id="194e4-142">StaffHub</span><span class="sxs-lookup"><span data-stu-id="194e4-142">StaffHub</span></span>](https://products.office.com/microsoft-staffhub/staff-scheduling-software) 
| ![流图标](media/o365-stream-64x64.png) <br> [<span data-ttu-id="194e4-144">流</span><span class="sxs-lookup"><span data-stu-id="194e4-144">Stream</span></span>](https://stream.microsoft.com) | ![Sway 图标](media/o365-sway-64x64.png) <br> [<span data-ttu-id="194e4-146">Sway<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="194e4-146">Sway<sup>1</sup></span></span>](https://sway.com) | ![团队图标](media/o365-teams-64x64.png) <br> [<span data-ttu-id="194e4-148">Teams</span><span class="sxs-lookup"><span data-stu-id="194e4-148">Teams</span></span>](https://products.office.com/microsoft-teams/group-chat-software) | ![待办情况图标](media/o365-todo-64x64.png) <br> [<span data-ttu-id="194e4-150">微软待办</span><span class="sxs-lookup"><span data-stu-id="194e4-150">To-Do</span></span>](https://todo.microsoft.com) | ![Visio 图标](media/o365-visio-64x64.png) <br> [<span data-ttu-id="194e4-152">Visio</span><span class="sxs-lookup"><span data-stu-id="194e4-152">Visio</span></span>](https://products.office.com/visio/flowchart-software) 
| ![Word 图标](media/o365-word-64x64.png) <br> [<span data-ttu-id="194e4-154">Word</span><span class="sxs-lookup"><span data-stu-id="194e4-154">Word</span></span>](https://products.office.com/word) | ![Yammer 图标](media/o365-yammer-64x64.png) <br> [<span data-ttu-id="194e4-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="194e4-156">Yammer</span></span>](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <span data-ttu-id="194e4-157"><sup>1</sup>对即将推出的 iOS 上的 Sway 提供支持。</span><span class="sxs-lookup"><span data-stu-id="194e4-157"><sup>1</sup> Support for Sway on iOS coming soon.</span></span>