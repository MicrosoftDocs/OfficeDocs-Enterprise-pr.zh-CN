---
title: 调整 Exchange Online 性能
ms.author: krowley
author: kccross
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
description: 本文包含一般的提示和告诉您如何提高 Exchange online 的性能的其他资源的链接。
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539899"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="3f2dc-103">调整 Exchange Online 性能</span><span class="sxs-lookup"><span data-stu-id="3f2dc-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="3f2dc-p101">本文包含一般的提示和告诉您如何提高 Exchange online 的性能的其他资源的链接。本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)项目的一部分。</span><span class="sxs-lookup"><span data-stu-id="3f2dc-p101">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="3f2dc-106">为了提高 Exchange Online 的性能注意事项</span><span class="sxs-lookup"><span data-stu-id="3f2dc-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="3f2dc-107">若要提高迁移速度并减少组织的带宽限制的 Exchange Online，考虑下列问题：</span><span class="sxs-lookup"><span data-stu-id="3f2dc-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="3f2dc-p102">**减小邮箱大小。** 减小邮箱大小可提高迁移速度。</span><span class="sxs-lookup"><span data-stu-id="3f2dc-p102">**Reduce mailbox sizes.** Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="3f2dc-p103">**将邮箱移动功能与 Exchange 混合部署一起使用。** 在 Exchange 混合部署中，脱机邮件（.OST 文件格式）在迁移到 Exchange Online 时不需要重新下载。这可以大大降低下载带宽要求。</span><span class="sxs-lookup"><span data-stu-id="3f2dc-p103">**Use the mailbox move capabilities with an Exchange hybrid deployment.** With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online. This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="3f2dc-p104">**将邮箱移动安排在低 Internet 通信和低内部部署 Exchange 使用的时间段内进行。** 当计划移动时，迁移请求将提交到邮箱复制代理，并且可能不会立即发生。</span><span class="sxs-lookup"><span data-stu-id="3f2dc-p104">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.** When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="3f2dc-p105">**使用 web 上的 Outlook 精益 popouts。** 精益 popouts 更小，请提供更少内存密集型版本的 Microsoft 边缘或 Internet Explorer 中的呈现服务器上的某些组件某些电子邮件。有关详细信息，请参阅[使用精益 popouts 以减少内存使用阅读邮件时](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)。</span><span class="sxs-lookup"><span data-stu-id="3f2dc-p105">**Use lean popouts for Outlook on the web.** Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server. For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>
    
<span data-ttu-id="3f2dc-118">有关 Exchange 迁移性能的详细信息，请参阅[Office 365 迁移性能和最佳做法](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)。</span><span class="sxs-lookup"><span data-stu-id="3f2dc-118">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

