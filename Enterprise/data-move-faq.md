---
title: 数据移动常见问题解答
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 9/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: 以下是有关将核心数据移动到新的数据中心按地理的常见问题的解答。
ms.openlocfilehash: 40f83ee94aaa7c919f08d91d888ff131da02df67
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539700"
---
# <a name="data-move-general-faq"></a><span data-ttu-id="f33c4-103">数据移动常见问题解答</span><span class="sxs-lookup"><span data-stu-id="f33c4-103">Data move general FAQ</span></span>

<span data-ttu-id="f33c4-104">以下是有关将核心数据移动到新的数据中心按地理的常见问题的解答。</span><span class="sxs-lookup"><span data-stu-id="f33c4-104">Here are answers to general questions about moving core data to a new datacenter geo.</span></span>
  
 <span data-ttu-id="f33c4-105">**问： 如何确保我客户数据是在移动过程中的安全和我不经历停机时间？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-105">**Q. How do you make sure my customer data is safe during the move and that I won't experience downtime?**</span></span>
  
<span data-ttu-id="f33c4-p101">答： 数据移动是对最终用户影响最小的后端服务操作。在[过程中和数据移动后](during-and-after-your-data-move.md)列出了可能会影响的功能。我们遵守[Microsoft Online Services 服务级别协议 (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897)的可用性，客户需要准备或在移动过程中监视的不存在。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p101">A. Data moves are a back-end service operation with minimal impact to end-users. Features that can be impacted are listed in [During and after your data move](during-and-after-your-data-move.md). We adhere to the [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for availability so there is nothing that customers need to prepare for or to monitor during the move.</span></span> 
  
<span data-ttu-id="f33c4-p102">所有 Office 365 服务在数据中心中, 都运行的相同版本，以便您可以确保一致的功能。在整个过程完全支持您的服务。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p102">All Office 365 services run the same versions in the datacenters, so you can be assured of consistent functionality. Your service is fully supported throughout the process.</span></span>
  
 <span data-ttu-id="f33c4-112">**问： 什么是具有位于不同 geo 的不同服务的影响？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-112">**Q. What is the impact of having different services located in different geos?**</span></span>
  
<span data-ttu-id="f33c4-p103">答： 对于某些现有客户和移动过程的中间的客户，Office 365 服务的一些可能会出现在不同 geo。我们的服务运行独立于每个其他并如果这种情况，则不会影响用户。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p103">A. For some existing customers and customers in the middle of the move process, some of the Office 365 services may be located in different geos. Our services run independently of each other and there is no user impact if this is the case.</span></span>
  
 <span data-ttu-id="f33c4-116">**问： 将新的 Office 365 客户自动设置新的数据中心 geo 中？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-116">**Q. Will new Office 365 customers be automatically provisioned in the new datacenter geos?**</span></span>
  
<span data-ttu-id="f33c4-p104">答: 是。新的数据中心按地理可用后，新的 Office 365 的业务用户在注册期间选择作为其国家/地区的国家/地区合格的新地理位置将具有中新数据中心按地理承载其核心数据。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p104">A. Yes. Once a new datacenter geo is available, new Office 365 for business customers who select a country eligible for the new geo as their country during sign-up will have their core data hosted in the new datacenter geo.</span></span>
  
 <span data-ttu-id="f33c4-120">**问： 在哪里是我的数据是位于？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-120">**Q. Where is my data is located?**</span></span>
  
<span data-ttu-id="f33c4-p105">我们将发布的数据中心 geo 和数据中心，位置上的[Office 365 交互式数据中心映射](https://o365datacentermap.azurewebsites.net)的客户数据的位置。从 8 月 1 日，您将能够验证您的客户数据在通过数据位置部分下您的组织配置文件在 Office 365 管理中心中的其余部分的位置。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p105">We publish the location of datacenter geos, datacenters, and location of customer data on the [ Office 365 interactive datacenter maps ](https://o365datacentermap.azurewebsites.net). As of August 1, you will be able to verify the location of your customer data at rest via the Data Location section under your Organization Profile in the Office 365 Admin Center.</span></span>
  
 <span data-ttu-id="f33c4-123">**问： 将现有 Office 365 客户被移动到新的数据中心 geo？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-123">**Q. Will existing Office 365 customers be moved to the new datacenter geos?**</span></span>
  
<span data-ttu-id="f33c4-p106">答： 合格的 Office 365 客户可以请求已移至新 geo 其核心数据。客户需要之前及其地理位置的截止时间才能参加提交一个请求。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p106">A. Eligible Office 365 customers can request to have their core data moved to the new geos. Customers will need to submit a request before the deadline for their geo in order to participate.</span></span> 
  
 <span data-ttu-id="f33c4-127">**问： 什么客户有资格请求移动？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-127">**Q. What customers are eligible to request a move?**</span></span>
  
<span data-ttu-id="f33c4-p107">答： 现有的 Office 365 商业客户选择国家/地区合格的新数据中心按地理都将能够请求移动。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p107">A. Existing Office 365 commercial customers who selected a country eligible for the new datacenter geo will be able to request a move.</span></span> 
  
 <span data-ttu-id="f33c4-130">**问： 何时都将能够请求移动？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-130">**Q. When will I be able to request a move?**</span></span>
  
<span data-ttu-id="f33c4-p108">A.将[如何请求数据移动](request-your-data-move.md)上宣布请求期限。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p108">A. The request period will be announced on the [How to request your data move](request-your-data-move.md) page.</span></span> 
  
 <span data-ttu-id="f33c4-133">**问： 如何可以请求移动？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-133">**Q. How can I request to be moved?**</span></span>
  
<span data-ttu-id="f33c4-p109">答： 合格的客户将看到其[Office 365 管理门户](https://portal.office.com/)中的页面。请有关如何移动请求的说明，参阅[如何请求数据移动](request-your-data-move.md)。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p109">A. Eligible customers will see a page in their [Office 365 Admin Portal](https://portal.office.com/). Please see [How to request your data move](request-your-data-move.md) for instructions on how to request a move.</span></span> 
  
 <span data-ttu-id="f33c4-137">**问： 是否可以更改请求移动之后我选择？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-137">**Q. Can I change my selection after requesting a move?**</span></span>
  
<span data-ttu-id="f33c4-p110">答： 这不是我们可以您删除过程后提交您的请求。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p110">A. It is not possible for us to remove you from the process after you submit your request.</span></span>
  
 <span data-ttu-id="f33c4-140">**问： 什么情况，我不请求在截止日期前的移动？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-140">**Q. What happens if I do not request a move before the deadline?**</span></span>
  
<span data-ttu-id="f33c4-p111">答： 我们不能接受请求中每个地理位置期限结束之后移动。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p111">A. We are unable to accept requests to be moved after the deadline in each geo.</span></span>
  
 <span data-ttu-id="f33c4-143">**问： 如果我想才能获得更好的网络性能移动我的数据？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-143">**Q. What if I want to move my data in order to get better network performance?**</span></span>
  
<span data-ttu-id="f33c4-p112">Office 365 数据中心接近正在不是更好的网络性能保证。有许多因素和影响最终用户和 Office 365 服务之间的网络性能的组件。有关更多有关此信息和优化性能，请参阅[网络规划和性能优化 Office 365](network-planning-and-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p112">Being close to an Office 365 datacenter is not a guarantee for a better networking performance. There are many factors and components that impact the network performance between the end user and the Office 365 service. For more information about this and performance tuning see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>
  
 <span data-ttu-id="f33c4-147">**问： 所有服务将其数据都移动在同一天？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-147">**Q. Do all the services move their data on the same day?**</span></span>
  
<span data-ttu-id="f33c4-p113">答： 服务不会同时移动其数据。每个服务能够独立移动，并且可能会在不同时间移动其数据。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p113">A. The services do not move their data at the same time. Each service will move independently and will likely move their data at different times.</span></span>
  
 <span data-ttu-id="f33c4-151">**问： 是否可以选择时，我希望我要移动的数据？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-151">**Q. Can I choose when I want my data to be moved?**</span></span>
  
<span data-ttu-id="f33c4-p114">A.客户不能够选择特定的日期，它们能延迟其移动，以及我们不能共享特定日期或时间范围的移动。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p114">A. Customers are not able to select a specific date, they cannot delay their move, and we cannot share a specific date or timeframe for the moves.</span></span>
  
 <span data-ttu-id="f33c4-154">**问： 是否可以共享我的数据将移动时？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-154">**Q. Can you share when my data will be be moved?**</span></span>
  
<span data-ttu-id="f33c4-p115">答： 数据移动是对最终用户影响最小的后端操作。复杂性、 精度和刻度我们需要执行全局操作和自动环境中的数据移动禁止我们共享后的数据移动预计完成您的租户或任何其他单租户。客户将收到一个确认在邮件中心每个参与的服务完成后其数据移动。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p115">A. Data moves are a back-end operation with minimal impact to end-users. The complexity, precision and scale at which we need to perform data moves within a globally operated and automated environment prohibit us from sharing when a data move is expected to complete for your tenant or any other single tenant. Customers will receive one confirmation in Message Center per participating service when its data move has completed.</span></span> 
  
 <span data-ttu-id="f33c4-159">**问： 什么情况，用户在移动数据时访问服务？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-159">**Q. What happens if users access services while the data is being moved?**</span></span>
  
<span data-ttu-id="f33c4-p116">答： 有关期间数据移动的每个服务的部分可能会受到限制的功能的完整列表，请参阅[期间和之后数据移动](during-and-after-your-data-move.md)。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p116">A. See [During and after your data move](during-and-after-your-data-move.md) for a complete list of features that may be limited during portions of the data move for each service.</span></span> 
  
 <span data-ttu-id="f33c4-162">**问： 如何知道移动是否完成？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-162">**Q. How do I know the move is complete?**</span></span>
  
<span data-ttu-id="f33c4-p117">答： 观看 Office 365 邮件中心确认每个服务的数据的移动完成。当每个服务的数据会移时，因此您将获取三次完成通知，我们将公布完成通知： 两个分别用于 Exchange Online、 SharePoint Online 和 Skype 业务 online。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p117">A. Watch the Office 365 message center for confirmation that the move of each service's data is complete. When each service's data is moved, we'll post a completion notice so you'll get three completion notices: one each for Exchange Online, SharePoint Online, and Skype for Business Online.</span></span>
  
<span data-ttu-id="f33c4-166">如果在迁移之后，您看到的任何问题，请与[Office 365 支持](https://go.microsoft.com/fwlink/p/?LinkID=522459)以获得帮助。</span><span class="sxs-lookup"><span data-stu-id="f33c4-166">If you see any issues after the move, contact [Office 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) to get assistance.</span></span> 
  
 <span data-ttu-id="f33c4-167">**问： Office 365 的数据存储在新的数据中心 geo？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-167">**Q. What data for Office 365 is stored in the new datacenter geos?**</span></span>
  
<span data-ttu-id="f33c4-p118">答： 如果客户设置新的数据中心 geo，Microsoft 之一其租户存储在地理位置中的其余部分的以下客户数据：</span><span class="sxs-lookup"><span data-stu-id="f33c4-p118">A. If a customer provisions its tenant in one of the new datacenter geos, Microsoft stores the following customer data at rest within the geo:</span></span>
  
- <span data-ttu-id="f33c4-170">Exchange Online 邮箱内容 （电子邮件正文、 日历项和电子邮件附件的内容）</span><span class="sxs-lookup"><span data-stu-id="f33c4-170">Exchange Online mailbox content (e-mail body, calendar entries, and the content of email attachments)</span></span>
    
- <span data-ttu-id="f33c4-171">SharePoint Online 网站内容和该网站，包括 Project Online 和访问联机内容中存储的文件。</span><span class="sxs-lookup"><span data-stu-id="f33c4-171">SharePoint Online site content and the files stored within that site, including Project Online and Access Online content.</span></span>
    
<span data-ttu-id="f33c4-172">此外，此数据不会复制之外地理位置中。</span><span class="sxs-lookup"><span data-stu-id="f33c4-172">In addition, this data is not replicated outside of the geo.</span></span>
  
 <span data-ttu-id="f33c4-173">**问： 我是在一个新的数据中心 geo，Office 365 客户，但当注册我，我选择不同的国家/地区。可以我将如何移动到新的数据中心按地理？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-173">**Q. I am an Office 365 customer in one of the new datacenter geos, but when I signed up, I selected a different country. How can I be moved to the new datacenter geo?**</span></span>
  
<span data-ttu-id="f33c4-p119">答： 遗憾的是，不能更改您的租户相关联的国家或地区。相反，您需要使用新的订阅创建一个新的 Office 365 租户和手动将您的用户和数据移动到新的租户。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p119">A. Unfortunately, it is not possible to change the country associated with your tenant. Instead, you need to create a new Office 365 tenant with a new subscription and manually move your users and data to the new tenant.</span></span>
  
 <span data-ttu-id="f33c4-177">**问： 是否有我 bill 上的任何更改？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-177">**Q. Will there be any changes on my bill?**</span></span>
  
<span data-ttu-id="f33c4-p120">答： 在大多数情况下有中的客户将在其帐单看到的任何更改。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p120">A. In most cases there are no changes that customers in will see on their billing statement.</span></span>
  
<span data-ttu-id="f33c4-p121">Microsoft 将其他数量等于 for Office 365 服务澳大利亚 GST 收取所有澳大利亚客户的 Office 365，并将发出税费 invoices。因为澳大利亚 GST 应付上应纳税提供的商品和服务提供，并能提供澳大利亚中，将发生此更改。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p121">Microsoft will charge all Australian customers of Office 365 an additional amount equal to the Australian GST for Office 365 services and will issue tax invoices. This change will occur because Australian GST is payable on taxable supplies of goods and services provided and offered in Australia.</span></span>
  
 <span data-ttu-id="f33c4-182">**问： 什么情况，我们的过程在 Exchange Online 的移动电子邮件数据迁移到 Office 365？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-182">**Q. What happens if we are in process of email data migration to Office 365 during the Exchange Online move?**</span></span>
  
<span data-ttu-id="f33c4-p122">答： 如果电子邮件迁移正在进行，租户移动完成，并在目标数据中心中租户后，将自动重新启动这些邮箱的迁移时，将被取消当前迁移对单个邮箱。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p122">A. If email migrations are in progress, any individual mailboxes that are currently being migrated will be canceled while the tenant move finalizes, and migration of those mailboxes will automatically restart once the tenant is in the target datacenters.</span></span>
  
 <span data-ttu-id="f33c4-185">**问： 数据会移出以前的数据中心按地理后，它已从这些数据中心？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-185">**Q. After data is moved out of the previous datacenter geo, is it removed from those datacenters?**</span></span>
  
<span data-ttu-id="f33c4-p123">答: 是，将在一段时间后清除旧数据。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p123">A. Yes, the old data will be purged after a period of time.</span></span>
  
 <span data-ttu-id="f33c4-188">**问： 是否可以试运行某些用户？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-188">**Q. Can I pilot some users?**</span></span>
  
<span data-ttu-id="f33c4-p124">答： 当您的 Office 365 租户移至新的数据中心按地理，同时移动所有用户。您可以创建单独的试用版租户来测试连接，但试用租户不能以任何方式与您现有的租户组合使用。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p124">A. When your Office 365 tenant is moved to a new datacenter geo, all users are moved at once. You can create a separate trial tenant to test connectivity, but the trial tenant can't be combined in any way with your existing tenant.</span></span>
  
 <span data-ttu-id="f33c4-192">**问： 如何会通知有关移动和谁在我的公司是否将会通知？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-192">**Q. How will I be notified about the move and who at my company will be notified?**</span></span>
  
<span data-ttu-id="f33c4-p125">答： 我们将使用 Office 365 邮件中心，这是与 Office 365 中的任何管理员权限的任何人都可见。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p125">A. We'll use the Office 365 message center, which is visible to anyone with any admin permissions in Office 365.</span></span>
  
 <span data-ttu-id="f33c4-195">**问： 我不想要等待的 Microsoft 将我的数据。可以只创建一个新的租户和移动自己？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-195">**Q. I don't want to wait for Microsoft to move my data. Can I just create a new tenant and move myself?**</span></span>
  
<span data-ttu-id="f33c4-p126">答： 是的但是的过程将不会像 Microsoft 是执行数据移动无缝。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p126">A. Yes, however the process will not be as seamless as if Microsoft were to perform the data move.</span></span>
  
<span data-ttu-id="f33c4-p127">如果您创建一个新的租户，新的数据中心按地理可用后，将在新的地理位置承载新的租户。此新的租户是完全分开您以前的租户，您将负责移动所有用户邮箱、 网站内容、 域名称和任何其他数据。请注意，不能到另一个，从一个租户移动租户名称。我们建议您等待移动程序由 Microsoft 提供的我们将负责移动所有设置、 数据和用户的订阅。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p127">If you create a new tenant after the new datacenter geo is available, the new tenant will be hosted in the new geo. This new tenant is completely separate from your previous tenant and you would be responsible for moving all user mailboxes, site content, domain names, and any other data. Note that you can't move the tenant name from one tenant to another. We recommend that you wait for the move program provided by Microsoft as we'll take care of moving all settings, data, and subscriptions for your users.</span></span>
  
 <span data-ttu-id="f33c4-202">**问： 我不准备好移动，可以选择特定 move date？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-202">**Q. I'm not ready to be moved, can I pick a specific move date?**</span></span>
  
<span data-ttu-id="f33c4-p128">答： 不能为您要更改时将移动每个服务的客户数据。数据移动是对最终用户影响最小的后端操作。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p128">A. It is not possible for you to change when each service's customer data will be moved. Data moves are a back-end operation with minimal impact to end-users.</span></span>
  
 <span data-ttu-id="f33c4-206">**问： 我的客户数据已移动到新的数据中心按地理。是否可以返回迁移？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-206">**Q. My customer data has already been moved to a new datacenter geo. Can I move back?**</span></span>
  
<span data-ttu-id="f33c4-p129">答： 此方法不可行。无法移回客户已移至新的地理位置数据中心。作为任何地理位置中的客户，将会遇到相同质量服务、 性能和安全控制，像往常一样。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p129">A. This is not possible. Customers who have been moved to new geo datacenters cannot be moved back. As a customer in any geo, you will experience the same quality of service, performance, and security controls as you did before.</span></span>
  
 <span data-ttu-id="f33c4-211">**问： 是否新的数据中心 geo 使用当前的数据中心 geo 作为 Office 365 服务的相同版本？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-211">**Q. Do the new datacenter geos use the same versions of Office 365 services as the current datacenter geos?**</span></span>
  
<span data-ttu-id="f33c4-p130">答: 是。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p130">A. Yes.</span></span>
  
 <span data-ttu-id="f33c4-214">**问： 将 Office 365 租户中新数据中心托管可向之外的国家/地区的用户？**</span><span class="sxs-lookup"><span data-stu-id="f33c4-214">**Q. Will Office 365 tenants hosted in the new datacenters be available to users outside of the country?**</span></span>
  
<span data-ttu-id="f33c4-p131">答: 是。Microsoft 维护大型全局网络有 50 多个位置中对等协议 1,500 个以上 Internet 服务提供商 (Isp) 与世界各地的 23 国家/地区的公共 Internet 连接。用户将能够从所在 Internet 上访问数据中心。</span><span class="sxs-lookup"><span data-stu-id="f33c4-p131">A. Yes. Microsoft maintains a large global network with public Internet connections in more than 50 locations in 23 countries around the world with peering agreements with more than 1,500 Internet Service Providers (ISPs). Users will be able to access the datacenters from wherever they are on the Internet.</span></span>
  

