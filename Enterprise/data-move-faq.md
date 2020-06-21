---
title: 数据移动常见问题解答
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
f1.keywords:
- NOCSH
description: 以下是有关将核心数据移动到新的数据中心地理位置的常见问题的解答。
ms.openlocfilehash: 2954d85b0094a8d0f74980fa4e0ee9cac504abbe
ms.sourcegitcommit: e0603d9259e9be1aeb110fc3dd8b9abc6138c55d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "44781037"
---
# <a name="data-move-general-faq"></a><span data-ttu-id="bb1c5-103">数据移动常见问题解答</span><span class="sxs-lookup"><span data-stu-id="bb1c5-103">Data move general FAQ</span></span>

<span data-ttu-id="bb1c5-104">以下是有关将核心数据移动到新的数据中心地理位置的常见问题的解答。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-104">Here are answers to general questions about moving core data to a new datacenter geo.</span></span>
  
## <a name="what-customers-are-eligible-to-request-a-move"></a><span data-ttu-id="bb1c5-105">哪些客户有资格请求移动？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-105">What customers are eligible to request a move?</span></span>
  
<span data-ttu-id="bb1c5-106">选择符合新数据中心地理位置的国家/地区的现有 Microsoft 365 商业客户将能够请求移动。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-106">Existing Microsoft 365 commercial customers who selected a country eligible for the new datacenter geo will be able to request a move.</span></span>  <span data-ttu-id="bb1c5-107">此程序仅适用于分配有符合条件的国家/地区代码的租户，以将核心客户数据迁移到 Microsoft 365 租户，以将适用的工作负载迁移到相应的 Microsoft 365 数据中心地理位置。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-107">The program exists only for tenants with an eligible country code assigned to the Microsoft 365 tenant to migrate core customer data at rest for eligible workloads to the corresponding Microsoft 365 datacenter geo.</span></span>  <span data-ttu-id="bb1c5-108">请参阅 how [to request the data move](request-your-data-move.md) page，确认国家/地区的资格。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-108">Please refer to the [How to request your data move](request-your-data-move.md) page to confirm country eligibility.</span></span>   

## <a name="how-do-we-define-core-customer-data"></a><span data-ttu-id="bb1c5-109">如何定义核心客户数据？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-109">How do we define Core Customer Data?</span></span>
 
<span data-ttu-id="bb1c5-110">Core customer data 是一个术语，指的是在[Microsoft Online Services 术语](https://aka.ms/ost)中定义的客户数据子集：</span><span class="sxs-lookup"><span data-stu-id="bb1c5-110">Core customer data is a term that refers to a subset of customer data defined in the [Microsoft Online Services Terms](https://aka.ms/ost):</span></span> 
- <span data-ttu-id="bb1c5-111">Exchange Online 邮箱内容（电子邮件正文、日历条目和电子邮件附件的内容）</span><span class="sxs-lookup"><span data-stu-id="bb1c5-111">Exchange Online mailbox content (email body, calendar entries, and the content of email attachments)</span></span>
- <span data-ttu-id="bb1c5-112">SharePoint Online 网站内容和该网站中存储的文件</span><span class="sxs-lookup"><span data-stu-id="bb1c5-112">SharePoint Online site content and the files stored within that site</span></span>
- <span data-ttu-id="bb1c5-113">上载到 OneDrive for business 的文件</span><span class="sxs-lookup"><span data-stu-id="bb1c5-113">Files uploaded to OneDrive for Business</span></span> 

## <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a><span data-ttu-id="bb1c5-114">在什么时候完成了我的迁移，以便我的租户的核心客户数据存储在我的新 geo 中的地方？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-114">At what point is my migration complete so that my tenant’s core customer data is being stored at rest in my new geo?</span></span>

<span data-ttu-id="bb1c5-115">由于 Exchange Online 和 SharePoint Online/OneDrive for Business 之间存在共享依赖关系，因此在迁移这两个服务之前，不能将任何迁移都视为已完成。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-115">Due to shared dependencies between Exchange Online and SharePoint Online/OneDrive for Business, any migration cannot be considered completed until both services are migrated.</span></span>  <span data-ttu-id="bb1c5-116">Exchange Online 和 SharePoint Online/OneDrive for Business 通常分别以不同的时间进行迁移，且相互独立。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-116">Exchange Online and SharePoint Online/OneDrive for Business often migrate at separate times and independently from one another.</span></span>  <span data-ttu-id="bb1c5-117">在每个服务迁移完成时，租户管理员会在邮件中心中接收确认，并且可以随时查看管理中心中的数据位置卡，以确认每个服务的 rest 位置的核心客户数据。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-117">Tenant admins receive confirmation in Message Center when each service migration is completed and can view the data location card in the Admin Center at any time to confirm the core customer data at rest location for each service.</span></span>

## <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a><span data-ttu-id="bb1c5-118">如何确保移动过程中的客户数据是安全的，并且不会经历停机时间？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-118">How do you make sure my customer data is safe during the move and that I won't experience downtime?</span></span>
  
<span data-ttu-id="bb1c5-119">数据移动是一种后端服务操作，对最终用户影响最小。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-119">Data moves are a back-end service operation with minimal impact to end-users.</span></span> <span data-ttu-id="bb1c5-120">在[数据移动期间和之后](during-and-after-your-data-move.md)会列出受影响的功能。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-120">Features that can be impacted are listed in [During and after your data move](during-and-after-your-data-move.md).</span></span> <span data-ttu-id="bb1c5-121">我们遵循[Microsoft Online Services 服务级别协议（SLA）](https://go.microsoft.com/fwlink/p/?LinkId=523897)的可用性，以便客户无需准备或在移动过程中进行监视。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-121">We adhere to the [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for availability so there is nothing that customers need to prepare for or to monitor during the move.</span></span> 
  
<span data-ttu-id="bb1c5-122">所有 Microsoft 365 服务在数据中心中运行相同的版本，因此您可以确保功能一致。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-122">All Microsoft 365 services run the same versions in the datacenters, so you can be assured of consistent functionality.</span></span> <span data-ttu-id="bb1c5-123">您的服务在整个过程中完全受支持。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-123">Your service is fully supported throughout the process.</span></span>

## <a name="what-is-in-scope-for-teams-migration"></a><span data-ttu-id="bb1c5-124">团队迁移的范围是什么？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-124">What is in scope for Teams migration?</span></span>

<span data-ttu-id="bb1c5-125">除了 Exchange Online、SharePoint Online 和 OneDrive for Business;Microsoft 会将团队数据迁移到本地数据中心。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-125">In addition to Exchange Online, SharePoint Online, and OneDrive for Business; Microsoft will migrate Teams data to the local datacenter.</span></span>  
- <span data-ttu-id="bb1c5-126">工作组聊天邮件，包括私人邮件和频道消息。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-126">Teams chat messages, including private messages and channel messages.</span></span> 
- <span data-ttu-id="bb1c5-127">在聊天中使用的团队图像。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-127">Teams images used in chats.</span></span> 

<span data-ttu-id="bb1c5-128">团队文件存储在 SharePoint Online 中，团队聊天文件存储在 OneDrive for Business 中。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-128">Teams files are stored in SharePoint Online and Teams chat files are stored in OneDrive for Business.</span></span>  <span data-ttu-id="bb1c5-129">语音邮件、日历、聊天历史记录和联系人存储在 Exchange Online 中。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-129">Voicemail, calendar, chat history, and contacts are stored in Exchange Online.</span></span>  <span data-ttu-id="bb1c5-130">在许多情况下，Exchange Online、SharePoint Online 和 OneDrive for business 已由本地数据中心地理位置的客户使用，并且也是适用于符合条件的客户国家/地区的 Microsoft 365 迁移计划的一部分。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-130">In many cases, Exchange Online, SharePoint Online and OneDrive for Business are already used by the customer in the local datacenter geo and are also part of the Microsoft 365 migration program for eligible customer countries.</span></span>
  
## <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a><span data-ttu-id="bb1c5-131">在不同的信息中具有不同的服务会有什么影响？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-131">What is the impact of having different services located in different geos?</span></span>

<span data-ttu-id="bb1c5-132">某些 Microsoft 365 服务可能位于不同的信息中，用于某些现有客户和移动过程中间的客户。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-132">Some of the Microsoft 365 services may be located in different geos for some existing customers and for customers that are in the middle of the move process.</span></span> <span data-ttu-id="bb1c5-133">我们的服务独立运行，在这种情况下，不会对用户体验产生任何影响。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-133">Our services run independently of each other and there is no impact on the user experience if this is the case.</span></span><span data-ttu-id="bb1c5-134">但是，出于数据驻留目的，在 Exchange Online 和 SharePoint Online/OneDrive for business 都迁移到同一数据中心地理位置之前，不能认为租户迁移已完成。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-134"> However, for data residency purposes, a tenant migration cannot be considered as complete until both Exchange Online and SharePoint Online/OneDrive for Business are migrated to the same datacenter geo.</span></span>
  
## <a name="will-new-microsoft-365-customers-be-automatically-provisioned-in-the-new-datacenter-geos"></a><span data-ttu-id="bb1c5-135">新的 Microsoft 365 客户是否会在新的数据中心信息中自动预配？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-135">Will new Microsoft 365 customers be automatically provisioned in the new datacenter geos?</span></span>
  
<span data-ttu-id="bb1c5-136">是。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-136">Yes.</span></span> <span data-ttu-id="bb1c5-137">新的数据中心地理位置可用后，在注册过程中选择符合新地理位置的国家/地区的新 Microsoft 365 客户将把其核心客户数据存储在新的数据中心地理位置。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-137">Once a new datacenter geo is available, new Microsoft 365 customers who select a country eligible for the new geo as their country during sign-up will have their core customer data stored at rest in the new datacenter geo.</span></span>
  
 ## <a name="where-is-my-core-customer-data-located"></a><span data-ttu-id="bb1c5-138">我的核心客户数据位于何处？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-138">Where is my core customer data located?</span></span>

<span data-ttu-id="bb1c5-139">租户管理员可随时查看管理中心内的数据位置卡，以确认每个服务的 rest 位置的核心客户数据，尤其针对其租户。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-139">Tenant admins can view the data location card in the Admin Center at any time to confirm the core customer data at rest location for each service, specifically for their tenant.</span></span><span data-ttu-id="bb1c5-140">我们还发布了 [office 365 交互式数据中心](https://office.com/datamaps)的数据中心信息、数据中心和365位置的位置，作为对新租户的当前默认核心客户数据的参考。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-140">  We also publish the location of datacenter geos, datacenters, and location of Office 365 customer data on the [Office 365 interactive datacenter maps ](https://office.com/datamaps) as a reference for the current default core customer data at rest locations for new tenants.</span></span>  <span data-ttu-id="bb1c5-141">您可以通过 Microsoft 365 管理中心内组织配置文件下的 "数据位置" 部分，验证 rest 上的客户数据的位置。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-141">You can verify the location of your customer data at rest via the Data Location section under your Organization Profile in the Microsoft 365 Admin Center.</span></span>  
 
## <a name="when-will-i-be-able-to-request-a-move"></a><span data-ttu-id="bb1c5-142">何时我将能够请求移动？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-142">When will I be able to request a move?</span></span>
  
<span data-ttu-id="bb1c5-143">请参阅 how [to request the data move](request-your-data-move.md) page for a datacenter geo 支持的时间段。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-143">Please refer to the [How to request your data move](request-your-data-move.md) page for supported timeframes for your datacenter geo.</span></span>
  
## <a name="how-can-i-request-to-be-moved"></a><span data-ttu-id="bb1c5-144">如何请求移动？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-144">How can I request to be moved?</span></span>
  
<span data-ttu-id="bb1c5-145">符合条件的客户将在其[Microsoft 365 管理中心](https://admin.microsoft.com/)中看到一个页面。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-145">Eligible customers will see a page in their [Microsoft 365 admin center](https://admin.microsoft.com/).</span></span> <span data-ttu-id="bb1c5-146">请参阅[如何请求数据移动](request-your-data-move.md)以获取有关如何请求移动的说明。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-146">Please see [How to request your data move](request-your-data-move.md) for instructions on how to request a move.</span></span> 
  
## <a name="can-i-change-my-selection-after-requesting-a-move"></a><span data-ttu-id="bb1c5-147">在请求移动后，是否可以更改我的选定内容？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-147">Can I change my selection after requesting a move?</span></span>
  
<span data-ttu-id="bb1c5-148">提交请求后，我们无法将您从进程中删除。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-148">It is not possible for us to remove you from the process after you submit your request.</span></span>
  
## <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a><span data-ttu-id="bb1c5-149">如果我在最后期限之前未请求移动，会发生什么情况？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-149">What happens if I do not request a move before the deadline?</span></span>
  
<span data-ttu-id="bb1c5-150">我们可能会在异常基础上接受请求，以向你的租户授予完成移动的承诺期限。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-150">We may be able to accept requests on an exception basis to grant your tenant a committed deadline to complete the move.</span></span> <span data-ttu-id="bb1c5-151"> 若要发出请求，请联系[Microsoft 365 支持部门](https://go.microsoft.com/fwlink/p/?LinkID=522459)。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-151">Please  contact [Microsoft 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) to make the request.</span></span>

## <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a><span data-ttu-id="bb1c5-152">如果我想要移动数据以便获得更好的网络性能，该怎么办？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-152">What if I want to move my data in order to get better network performance?</span></span>
  
<span data-ttu-id="bb1c5-153">与 Microsoft 365 数据中心的物理邻近性并不能保证更好的网络性能。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-153">Physical proximity to a Microsoft 365 datacenter is not a guarantee for a better networking performance.</span></span> <span data-ttu-id="bb1c5-154">有许多因素和组件会影响最终用户与 Microsoft 365 服务之间的网络性能。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-154">There are many factors and components that impact the network performance between the end-user and the Microsoft 365 service.</span></span> <span data-ttu-id="bb1c5-155">有关此和性能调整的详细信息，请参阅[Microsoft 365 的网络规划和性能调整](network-planning-and-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-155">For more information about this and performance tuning see [Network planning and performance tuning for Microsoft 365](network-planning-and-performance.md).</span></span>
  
 ## <a name="do-all-the-services-move-their-data-on-the-same-day"></a><span data-ttu-id="bb1c5-156">所有服务是否都在同一天移动其数据？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-156">Do all the services move their data on the same day?</span></span>
 
<span data-ttu-id="bb1c5-157">每个服务都独立移动，并且可能会在不同时间移动其数据。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-157">Each service moves independently and will likely move their data at different times.</span></span>
  
 ## <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a><span data-ttu-id="bb1c5-158">我是否可以选择何时移动数据？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-158">Can I choose when I want my data to be moved?</span></span>
 
<span data-ttu-id="bb1c5-159">客户无法选择特定日期，它们不能延迟移动，也不能共享特定的移动日期或时间范围。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-159">Customers are not able to select a specific date, they cannot delay their move, and we cannot share a specific date or timeframe for the moves.</span></span>
  
 ## <a name="can-you-share-when-my-data-will-be-be-moved"></a><span data-ttu-id="bb1c5-160">是否可以在移动数据时共享？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-160">Can you share when my data will be be moved?</span></span>
  
<span data-ttu-id="bb1c5-161">数据移动是一种后端操作，对最终用户影响最小。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-161">Data moves are a back-end operation with minimal impact to end-users.</span></span> <span data-ttu-id="bb1c5-162">我们需要在全局运营和自动环境中执行数据移动的复杂性、精度和规模将禁止我们在对你的租户或任何其他单一租户完成数据移动时进行共享。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-162">The complexity, precision and scale at which we need to perform data moves within a globally operated and automated environment prohibit us from sharing when a data move is expected to complete for your tenant or any other single tenant.</span></span> <span data-ttu-id="bb1c5-163">客户在其数据移动完成后，每个参与的服务都会在邮件中心收到一条确认消息。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-163">Customers will receive one confirmation in Message Center per participating service when its data move has completed.</span></span> 
  
 ## <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a><span data-ttu-id="bb1c5-164">如果用户在移动数据时访问服务，会发生什么情况？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-164">What happens if users access services while the data is being moved?</span></span>

<span data-ttu-id="bb1c5-165">在[数据移动过程中和之后，请参阅数据移动](during-and-after-your-data-move.md)的完整列表，在每个服务的部分数据移动过程中可能会受到限制。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-165">See [During and after your data move](during-and-after-your-data-move.md) for a complete list of features that may be limited during portions of the data move for each service.</span></span> 
  
 ## <a name="how-do-i-know-the-move-is-complete"></a><span data-ttu-id="bb1c5-166">如何知道移动已完成？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-166">How do I know the move is complete?</span></span>
  
<span data-ttu-id="bb1c5-167">观看 Microsoft 365 消息中心，确认是否已完成每个服务的数据移动。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-167">Watch the Microsoft 365 Message Center for confirmation that the move of each service's data is complete.</span></span> <span data-ttu-id="bb1c5-168">移动每个服务的数据后，我们将发布一个完成通知，以便您将获得三个完成通知：每个完成通知分别对应于 Exchange Online、SharePoint Online 和 Skype for Business Online。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-168">When each service's data is moved, we'll post a completion notice so you'll get three completion notices: one each for Exchange Online, SharePoint Online, and Skype for Business Online.</span></span>  <span data-ttu-id="bb1c5-169">您还可以通过 Microsoft 365 管理中心中组织配置文件下的 "数据位置" 部分，验证 rest 上的客户数据的位置。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-169">You can also verify the location of your customer data at rest via the Data Location section under your Organization Profile in the Microsoft 365 Admin Center.</span></span>  
  
## <a name="i-am-a-microsoft-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a><span data-ttu-id="bb1c5-170">我是一个新的数据中心信息中的 Microsoft 365 客户，但当我注册时，我选择了其他国家/地区。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-170">I am a Microsoft 365 customer in one of the new datacenter geos, but when I signed up, I selected a different country.</span></span> <span data-ttu-id="bb1c5-171">如何将移动到新的数据中心地理位置？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-171">How can I be moved to the new datacenter geo?</span></span>

<span data-ttu-id="bb1c5-172">无法更改与你的租户关联的注册国家/地区。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-172">It is not possible to change the signup country associated with your tenant.</span></span> <span data-ttu-id="bb1c5-173">而是需要使用新订阅创建一个新的 Microsoft 365 租户，并将用户和数据手动移动到新的租户。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-173">Instead, you need to create a new Microsoft 365 tenant with a new subscription and manually move your users and data to the new tenant.</span></span>
  
## <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-microsoft-365-during-the-exchange-online-move"></a><span data-ttu-id="bb1c5-174">如果我们在 Exchange Online 移动过程中将电子邮件数据迁移到 Microsoft 365，会发生什么情况？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-174">What happens if we are in process of email data migration to Microsoft 365 during the Exchange Online move?</span></span>

<span data-ttu-id="bb1c5-175">这是一种非常常见的方案，完全受支持。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-175">This is a very common scenario and is fully supported.</span></span>  <span data-ttu-id="bb1c5-176">Datacenter 信息之间的云迁移不会干扰任何 on premisis to 云邮箱迁移。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-176">Cloud migration between datacenter geos does not interfere with any on-premisis to cloud mailbox migrations.</span></span>
  
 ## <a name="can-i-pilot-some-users"></a><span data-ttu-id="bb1c5-177">我可以试运行某些用户吗？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-177">Can I pilot some users?</span></span>
  
<span data-ttu-id="bb1c5-178">您可以创建单独的试用租户来测试连接，但不能以任何方式将试用租户与现有租户组合在一起。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-178">You can create a separate trial tenant to test connectivity, but the trial tenant can't be combined in any way with your existing tenant.</span></span>

## <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a><span data-ttu-id="bb1c5-179">我不想等待 Microsoft 移动我的数据。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-179">I don't want to wait for Microsoft to move my data.</span></span> <span data-ttu-id="bb1c5-180">我是否可以只创建一个新的租户并移动自己？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-180">Can I just create a new tenant and move myself?</span></span>
  
<span data-ttu-id="bb1c5-181">是的，但是此过程不会像 Microsoft 执行数据移动那样顺畅。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-181">Yes, however the process will not be as seamless as if Microsoft were to perform the data move.</span></span>
  
<span data-ttu-id="bb1c5-182">如果在新的数据中心地理位置之后创建新租户，新租户将托管在新地理位置。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-182">If you create a new tenant after the new datacenter geo is available, the new tenant will be hosted in the new geo.</span></span> <span data-ttu-id="bb1c5-183">此新租户完全独立于以前的租户，您将负责移动所有用户邮箱、网站内容、域名和其他任何数据。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-183">This new tenant is completely separate from your previous tenant and you would be responsible for moving all user mailboxes, site content, domain names, and any other data.</span></span> <span data-ttu-id="bb1c5-184">请注意，不能将租户名称从一个租户移动到另一个租户。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-184">Note that you can't move the tenant name from one tenant to another.</span></span> <span data-ttu-id="bb1c5-185">我们建议您等待 Microsoft 提供的移动程序，因为我们将负责移动用户的所有设置、数据和订阅。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-185">We recommend that you wait for the move program provided by Microsoft as we'll take care of moving all settings, data, and subscriptions for your users.</span></span>
  
## <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a><span data-ttu-id="bb1c5-186">我的客户数据已移动到新的数据中心地理位置。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-186">My customer data has already been moved to a new datacenter geo.</span></span> <span data-ttu-id="bb1c5-187">我可以向后移动吗？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-187">Can I move back?</span></span>
 
<span data-ttu-id="bb1c5-188">否，这是不可能的。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-188">No, this is not possible.</span></span> <span data-ttu-id="bb1c5-189">已移动到新 geo 数据中心的客户不能移动回来。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-189">Customers who have been moved to new geo datacenters cannot be moved back.</span></span> <span data-ttu-id="bb1c5-190">作为任何地区的客户，你将体验到以前所做的相同质量的服务、性能和安全控制。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-190">As a customer in any geo, you will experience the same quality of service, performance, and security controls as you did before.</span></span>  <span data-ttu-id="bb1c5-191">[Microsoft 365 多地理](https://aka.ms/multi-geo)位置可供某些客户作为加载项，并允许单个租户创建多个附属信息，并将用户数据移动到具有数据派驻服务承诺的这些信息中。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-191">[Microsoft 365 Multi Geo](https://aka.ms/multi-geo) is available to some customers as an add-on and lets a single tenant create multiple satellite geos and move user data to those geos with data residency commitments.</span></span>
  
## <a name="will-microsoft-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a><span data-ttu-id="bb1c5-192">在新数据中心托管的 Microsoft 365 租户是否适用于该国家/地区之外的用户？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-192">Will Microsoft 365 tenants hosted in the new datacenters be available to users outside of the country?</span></span>
  
<span data-ttu-id="bb1c5-193">是。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-193">Yes.</span></span> <span data-ttu-id="bb1c5-194">Microsoft 在全球范围内的35国家/地区内的国家/地区的多达130个位置维护一个大型的全球网络，其 Internet 服务提供商（Isp）数量超过2700的对等协议。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-194">Microsoft maintains a large global network with public Internet connections in more than 130 locations in 35 countries around the world with peering agreements with more than 2,700 Internet Service Providers (ISPs).</span></span> <span data-ttu-id="bb1c5-195">用户将能够从 Internet 上的任何位置访问数据中心。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-195">Users will be able to access the datacenters from wherever they are on the Internet.</span></span>

## <a name="my-tenant-has-configured-the-multi-geo-add-on-can-i-still-enroll-in-my-tenant-in-the-microsoft-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a><span data-ttu-id="bb1c5-196">我的租户配置了[多地理加载](https://aka.ms/multi-geo)项。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-196">My tenant has configured the [Multi Geo add-on](https://aka.ms/multi-geo).</span></span> <span data-ttu-id="bb1c5-197">我是否可以在 Microsoft 365 移动程序中注册我的租户以更改我的默认地理位置并将任何用户不在附属区域中移动到新的默认地理位置？</span><span class="sxs-lookup"><span data-stu-id="bb1c5-197">Can I still enroll in my tenant in the Microsoft 365 Move Program to change my default geo and move any user not in a satellite region to the new default geo?</span></span>

<span data-ttu-id="bb1c5-198">是的，你的租户符合注册条件。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-198">Yes, your tenant is eligible to enroll.</span></span> <span data-ttu-id="bb1c5-199">我们会将所有 EXO 邮箱从当前的默认地理位置移动到新的本地数据中心地理位置。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-199">We will move all EXO mailboxes from your current default geo to your new local datacenter geo.</span></span>  <span data-ttu-id="bb1c5-200">我们不会移动在 "多地理" 卫星区域中配置的任何 EXO 邮箱，而是按预期继续遵循卫星区域数据派驻服务。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-200">We will not move any EXO mailboxes configured in Multi Geo satellite regions to continue to respect satellite region data residency as you’ve intended.</span></span>  

<span data-ttu-id="bb1c5-201">SharePoint Online 和 OneDrive for business 无法迁移到新的数据中心地理位置作为移动程序的一部分，但您可以通过多地理程序将 OneDrive for Business 共享配置为移动到您想要的任何区域。</span><span class="sxs-lookup"><span data-stu-id="bb1c5-201">SharePoint Online and OneDrive for Business cannot migrate to the new datacenter geo as part of the Move Program, though you can configure OneDrive for Business shares to move to any region you wish via the Multi Geo program.</span></span>

## <a name="related-topics"></a><span data-ttu-id="bb1c5-202">相关主题</span><span class="sxs-lookup"><span data-stu-id="bb1c5-202">Related topics</span></span>

[<span data-ttu-id="bb1c5-203">将核心数据移动到新的 Microsoft 365 数据中心信息</span><span class="sxs-lookup"><span data-stu-id="bb1c5-203">Moving core data to new Microsoft 365 datacenter geos</span></span>](moving-data-to-new-datacenter-geos.md)

[<span data-ttu-id="bb1c5-204">如何请求数据移动</span><span class="sxs-lookup"><span data-stu-id="bb1c5-204">How to request your data move</span></span>](request-your-data-move.md)

[<span data-ttu-id="bb1c5-205">Microsoft 365 多地理位置</span><span class="sxs-lookup"><span data-stu-id="bb1c5-205">Microsoft 365 Multi Geo</span></span>](https://aka.ms/multi-geo)

[<span data-ttu-id="bb1c5-206">Microsoft 365 交互式数据中心映射</span><span class="sxs-lookup"><span data-stu-id="bb1c5-206">Microsoft 365 interactive datacenter map</span></span>](https://office.com/datamaps)

[<span data-ttu-id="bb1c5-207">Microsoft 365 支持</span><span class="sxs-lookup"><span data-stu-id="bb1c5-207">Microsoft 365 Support</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=522459)

[<span data-ttu-id="bb1c5-208">适用于 Microsoft Dynamics CRM Online 的新数据中心信息</span><span class="sxs-lookup"><span data-stu-id="bb1c5-208">New datacenter geos for Microsoft Dynamics CRM Online</span></span>](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[<span data-ttu-id="bb1c5-209">按区域的 Azure 服务</span><span class="sxs-lookup"><span data-stu-id="bb1c5-209">Azure services by region</span></span>](https://azure.microsoft.com/regions/)
