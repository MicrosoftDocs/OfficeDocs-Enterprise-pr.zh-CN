---
title: 调整 Exchange Online 性能
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: 本文包含一般提示和指向其他资源的链接, 这些链接告诉您如何提高 Exchange Online 的性能。
ms.openlocfilehash: f75869ba6d83a92b1e19743c8b38c4bcbb6762cf
ms.sourcegitcommit: 1d84e2289fc87717f8a9cd12c68ab27c84405348
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "30372849"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="8e859-103">调整 Exchange Online 性能</span><span class="sxs-lookup"><span data-stu-id="8e859-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="8e859-104">本文包含的常规提示和指向其他资源的链接, 这些链接告诉您如何提高 Exchange Online 的性能 (尤其是在迁移之前)。</span><span class="sxs-lookup"><span data-stu-id="8e859-104">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online, particularly in front of a migration.</span></span> <span data-ttu-id="8e859-105">本文是 Office 365 项目的[网络规划和性能调整](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="8e859-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="8e859-106">为了改进 Exchange Online 性能, 需要考虑的事项</span><span class="sxs-lookup"><span data-stu-id="8e859-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="8e859-107">若要提高迁移速度并减少组织的 Exchange Online 带宽限制, 请考虑以下事项:</span><span class="sxs-lookup"><span data-stu-id="8e859-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="8e859-108">**减小邮箱大小。**</span><span class="sxs-lookup"><span data-stu-id="8e859-108">**Reduce mailbox sizes.**</span></span> <span data-ttu-id="8e859-109">邮箱大小较小可提高迁移速度。</span><span class="sxs-lookup"><span data-stu-id="8e859-109">Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="8e859-110">**将邮箱移动功能与 Exchange 混合部署结合使用。**</span><span class="sxs-lookup"><span data-stu-id="8e859-110">**Use the mailbox move capabilities with an Exchange hybrid deployment.**</span></span> <span data-ttu-id="8e859-111">使用 Exchange 混合部署时, 脱机邮件 (格式为)。OST 文件) 在迁移到 Exchange Online 时不需要重新下载。</span><span class="sxs-lookup"><span data-stu-id="8e859-111">With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online.</span></span> <span data-ttu-id="8e859-112">这极大地降低了下载带宽要求。</span><span class="sxs-lookup"><span data-stu-id="8e859-112">This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="8e859-113">**将邮箱移动安排在 Internet 流量较低和本地 Exchange 使用较低的时段发生。**</span><span class="sxs-lookup"><span data-stu-id="8e859-113">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.**</span></span> <span data-ttu-id="8e859-114">在安排移动时, 迁移请求将提交到邮箱复制代理, 并且不会立即生效。</span><span class="sxs-lookup"><span data-stu-id="8e859-114">When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="8e859-115">**对 web 上的 Outlook 使用精益弹出内容。**</span><span class="sxs-lookup"><span data-stu-id="8e859-115">**Use lean popouts for Outlook on the web.**</span></span> <span data-ttu-id="8e859-116">精益弹出内容通过在服务器上呈现一些组件, 在 Microsoft Edge 或 Internet Explorer 中提供特定电子邮件的较小、占用大量内存的版本。</span><span class="sxs-lookup"><span data-stu-id="8e859-116">Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server.</span></span> <span data-ttu-id="8e859-117">有关详细信息, 请参阅[使用精益弹出内容以减少阅读邮件时使用的内存](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)。</span><span class="sxs-lookup"><span data-stu-id="8e859-117">For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>


## <a name="general-advice"></a><span data-ttu-id="8e859-118">一般建议</span><span class="sxs-lookup"><span data-stu-id="8e859-118">General advice</span></span>

- <span data-ttu-id="8e859-119">确保 outlook.office.com 的 DNS 查找在你的位置的逻辑入口位置输入 MS 数据中心。</span><span class="sxs-lookup"><span data-stu-id="8e859-119">Make certain that DNS lookup for outlook.office.com enters the MS-datacenter at a logical entry location for your location.</span></span>

- <span data-ttu-id="8e859-120">研究邮箱缓存并选择适当的选项 (re)。</span><span class="sxs-lookup"><span data-stu-id="8e859-120">Research mailbox caching and choose the appropriate options (re.</span></span> <span data-ttu-id="8e859-121">缓存期, 共享邮箱缓存, et。</span><span class="sxs-lookup"><span data-stu-id="8e859-121">caching period, shared mailbox caching, et cetera).</span></span>

- <span data-ttu-id="8e859-122">将 Outlook 数据传递到 Internet 之前, 请保留 VPN 连接 (到中央办公室)。</span><span class="sxs-lookup"><span data-stu-id="8e859-122">Keep your Outlook data from passing over VPN connections (to a central office) before it goes over the Internet.</span></span>

- <span data-ttu-id="8e859-123">请确保您的邮箱数据符合对文件夹、项目、数量的限制。</span><span class="sxs-lookup"><span data-stu-id="8e859-123">Be sure your mailbox data adheres to the limitations on folder, and item, amounts.</span></span>
    
<span data-ttu-id="8e859-124">有关 Exchange 迁移性能的详细信息, 请参阅[Office 365 迁移性能和最佳实践](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)。</span><span class="sxs-lookup"><span data-stu-id="8e859-124">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

