---
title: 适用于 Project Server 的 GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 了解如何解决本地 Project Server 中的 GDPR 要求。
ms.openlocfilehash: 6a630dc4cef2c4117e0ba25497f898d0b8da221b
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-project-server"></a><span data-ttu-id="31dee-103">适用于 Project Server 的 GDPR</span><span class="sxs-lookup"><span data-stu-id="31dee-103">Plan for Project Server</span></span>

<span data-ttu-id="31dee-p101">Project Server 使用自定义脚本在 Project Web App 中导出和修订用户数据。基本过程是：</span><span class="sxs-lookup"><span data-stu-id="31dee-p101">Project Server uses custom scripts to export and redact user data in Project Web App. The basic process is:</span></span>

1.  <span data-ttu-id="31dee-106">在服务器场中找到 Project Web App 网站。</span><span class="sxs-lookup"><span data-stu-id="31dee-106">Find the Project Web App sites in your farm.</span></span>

2.  <span data-ttu-id="31dee-107">在包含此用户的每个网站中找到项目。</span><span class="sxs-lookup"><span data-stu-id="31dee-107">Find the projects in each site that contain the user.</span></span>

3.  <span data-ttu-id="31dee-108">导出并查看想要查看的数据类型。</span><span class="sxs-lookup"><span data-stu-id="31dee-108">Export and review the types of data that you want to review.</span></span>

4.  <span data-ttu-id="31dee-109">根据需要修订数据。</span><span class="sxs-lookup"><span data-stu-id="31dee-109">Redact data as needed.</span></span>

<span data-ttu-id="31dee-110">下文详细介绍了这些步骤：</span><span class="sxs-lookup"><span data-stu-id="31dee-110">These three scenarios are covered in detail in the following articles:</span></span>

- [<span data-ttu-id="31dee-111">从 Project Server 中导出用户数据</span><span class="sxs-lookup"><span data-stu-id="31dee-111">Export user data from Project Server</span></span>](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [<span data-ttu-id="31dee-112">从 Project Server 中删除用户数据</span><span class="sxs-lookup"><span data-stu-id="31dee-112">Delete user data from Project Server</span></span>](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


<span data-ttu-id="31dee-113">请注意，Project Server 构建于 SharePoint Server 之上，并将事件记录到 SharePoint ULS 日志和使用情况数据库中。</span><span class="sxs-lookup"><span data-stu-id="31dee-113">Note that Project Server is built on top of SharePoint Server and logs events to the SharePoint ULS logs and Usage database.</span></span>
