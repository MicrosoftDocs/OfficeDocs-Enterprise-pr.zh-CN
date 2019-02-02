---
title: 如何查看 Office 365 服务运行状况
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: 查看 Office 365 服务的运行状况状态之前调用支持，以了解是否有有效的服务中断
ms.openlocfilehash: 52a7b762b8e86c3e538579f7c1e1611515469389
ms.sourcegitcommit: c7ad181394a8a3ee261dc44e7a1e70f6ebe7cbcf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2019
ms.locfileid: "29696349"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="021ff-103">如何查看 Office 365 服务运行状况</span><span class="sxs-lookup"><span data-stu-id="021ff-103">How to check Office 365 service health</span></span>

<span data-ttu-id="021ff-p101">在管理中心中的 Office 365**服务运行状况**页上，您可以查看 Office 365、 Yammer、 Microsoft Dynamics CRM 和 Microsoft Intune 云服务的运行状况。如果遇到被云服务的问题，您可以检查服务运行状况，以确定是否正在解析的已知的问题之前呼叫支持或花时间进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="021ff-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 **Service health** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 

<span data-ttu-id="021ff-106">如果您不能登录到服务门户，您可以使用[服务状态页](https://status.office365.com)以检查阻止您登录到您的租户的已知问题。</span><span class="sxs-lookup"><span data-stu-id="021ff-106">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="021ff-107">如何查看服务运行状况</span><span class="sxs-lookup"><span data-stu-id="021ff-107">How to check service health</span></span>

1. <span data-ttu-id="021ff-108">转到 [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) 并使用管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="021ff-108">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="021ff-p102">分配为全局管理员或服务管理员角色的人员可以查看服务运行状况。若要允许 Exchange、SharePoint 和 Skype for Business 管理员查看服务运行状况，必须向他们分配服务管理员角色。</span><span class="sxs-lookup"><span data-stu-id="021ff-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span>
  
2. <span data-ttu-id="021ff-p103">若要打开在管理中心的服务运行状况，转到**运行状况** > **服务运行状况**，或单击**主页仪表板**上的**服务运行状况卡片**。仪表板卡片指示是否存在活动服务问题和详细的服务运行状况页面的链接。</span><span class="sxs-lookup"><span data-stu-id="021ff-p103">To open service health, in the admin center, go to **Health** > **Service health**, or click the **Service health card** on the **Home dashboard**. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="021ff-114">每个云服务的运行状态均以表格格式显示，其中包含指示可能状态的图标。</span><span class="sxs-lookup"><span data-stu-id="021ff-114">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="021ff-115">你也可以在移动设备上使用 [Office 365 Admin 应用](https://go.microsoft.com/fwlink/p/?linkid=627216)查看服务运行状况，这是一种通过推送通知随时获取最新消息的好方法。</span><span class="sxs-lookup"><span data-stu-id="021ff-115">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="021ff-116">查看已发布服务的运行状况详细信息</span><span class="sxs-lookup"><span data-stu-id="021ff-116">View details of posted service health</span></span>

<span data-ttu-id="021ff-p104">在默认视图中，将显示所有服务和及其当前运行状况状态。若要筛选视图服务当前遇到一个事件，请从左侧的灰色栏中选择**事件**。选择**通报**会显示当前具有安全公告发布的服务。从**的所有服务**视图中，单击显示的服务状态将打开 advisory 或事件的摘要视图。</span><span class="sxs-lookup"><span data-stu-id="021ff-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="021ff-122">公告或事件摘要提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="021ff-122">The advisory or incident summary provides the following information:</span></span> 
  
![标记服务通报中的字段的屏幕截图](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="021ff-124">该问题的问题标识符和摘要语句。</span><span class="sxs-lookup"><span data-stu-id="021ff-124">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="021ff-p105">当前状态。请参阅本文中的状态定义，获取每种潜在状态的说明。</span><span class="sxs-lookup"><span data-stu-id="021ff-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="021ff-127">关于此问题如何影响用户的说明。</span><span class="sxs-lookup"><span data-stu-id="021ff-127">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="021ff-p106">该问题发生的时间以及上一次更新服务运行状况消息的时间。出现问题期间，我们会经常发布消息，说明我们在应用解决方案时取得的进展。</span><span class="sxs-lookup"><span data-stu-id="021ff-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="021ff-130">选择" **显示详细信息**"链接来查看有关该问题的更多详细信息，包括我们在开发解决方案时发布的所有消息的历史记录。</span><span class="sxs-lookup"><span data-stu-id="021ff-130">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="021ff-131">翻译服务运行状况详细信息</span><span class="sxs-lookup"><span data-stu-id="021ff-131">Translate service health details</span></span>

<span data-ttu-id="021ff-p107">服务运行状况说明是实时发布的，因此这些说明不会自动翻译成你的语言，并且服务事件的详细信息仅以英语形式提供。若要翻译这些说明，请遵循以下步骤：</span><span class="sxs-lookup"><span data-stu-id="021ff-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="021ff-134">转到[翻译工具](https://www.bing.com/translator/)。</span><span class="sxs-lookup"><span data-stu-id="021ff-134">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="021ff-p108">在" **服务运行状况**"页上，选择一个事件或公告。在" **显示详细信息**"下，复制关于该问题的文本。</span><span class="sxs-lookup"><span data-stu-id="021ff-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="021ff-137">在"翻译工具"中，粘贴文本，然后选择" **翻译**"。</span><span class="sxs-lookup"><span data-stu-id="021ff-137">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="021ff-138">定义</span><span class="sxs-lookup"><span data-stu-id="021ff-138">Definitions</span></span>

<span data-ttu-id="021ff-p109">在大多数情况下，服务正常运行且没有进一步的信息。服务出现问题时，该问题会标识为公告或事件，并显示当前状态。</span><span class="sxs-lookup"><span data-stu-id="021ff-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="021ff-p110">服务运行状况中不会显示计划内维护事件。可以通过" **消息中心**"随时了解最新消息，从而跟踪计划内维护事件。筛选出分类为"更改计划"的消息，了解发生更改的时间、其影响以及如何做好相应准备。请参阅 [Office 365 中的消息中心](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093)获取更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="021ff-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="021ff-145">事件和公告</span><span class="sxs-lookup"><span data-stu-id="021ff-145">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="021ff-p111">如果服务显示公告，这意味着某问题正在影响一些用户，但该服务仍然可用。公告中通常存在针对该问题的变通方法，并且该问题可能是间歇性的，或其作用范围和对用户的影响有限。</span><span class="sxs-lookup"><span data-stu-id="021ff-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="021ff-p112">如果服务显示遇到活动事件，则说明遇到关键问题，且服务或其主要功能目前不可用。例如，用户可能无法发送和接收电子邮件，或无法登录。事件会对用户产生显著影响。对于正在进行的事件，我们会在服务运行状况仪表板中提供有关调查、缓解措施和解决方法确认的更新。</span><span class="sxs-lookup"><span data-stu-id="021ff-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="021ff-154">状态定义</span><span class="sxs-lookup"><span data-stu-id="021ff-154">Status definitions</span></span>

|<span data-ttu-id="021ff-155">**状态**</span><span class="sxs-lookup"><span data-stu-id="021ff-155">**Status**</span></span>|<span data-ttu-id="021ff-156">**定义**</span><span class="sxs-lookup"><span data-stu-id="021ff-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="021ff-157">**正在调查**</span><span class="sxs-lookup"><span data-stu-id="021ff-157">**Investigating**</span></span> | <span data-ttu-id="021ff-158">我们已发现存在潜在问题，我们正在收集有关情况和影响范围的详细信息。</span><span class="sxs-lookup"><span data-stu-id="021ff-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="021ff-159">**服务降级**</span><span class="sxs-lookup"><span data-stu-id="021ff-159">**Service degradation**</span></span> | <span data-ttu-id="021ff-p113">我们已确认存在可能影响服务或功能使用的问题。例如，如果服务的执行速度比平常慢、存在间歇性中断或某功能运行不正常，则可能看到此状态。</span><span class="sxs-lookup"><span data-stu-id="021ff-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="021ff-162">**服务中断**</span><span class="sxs-lookup"><span data-stu-id="021ff-162">**Service interruption**</span></span> | <span data-ttu-id="021ff-p114">如果我们确定某问题影响用户访问服务的能力，则你将看到此状态。在本例中，问题十分重大且可持续重现。</span><span class="sxs-lookup"><span data-stu-id="021ff-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="021ff-165">**正在还原服务**</span><span class="sxs-lookup"><span data-stu-id="021ff-165">**Restoring service**</span></span> | <span data-ttu-id="021ff-166">我们已确定问题成因，知晓需要采取的纠正措施，并正在将服务恢复到正常状态。</span><span class="sxs-lookup"><span data-stu-id="021ff-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="021ff-167">**延期恢复**</span><span class="sxs-lookup"><span data-stu-id="021ff-167">**Extended recovery**</span></span> | <span data-ttu-id="021ff-p115">此状态表示正在执行纠正措施，为大多数用户恢复服务，但恢复所有受影响的系统仍需一些时间。如果我们为了减轻影响，而在实施永久解决措施前实施临时措施，你也可能看到此状态。</span><span class="sxs-lookup"><span data-stu-id="021ff-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="021ff-170">**调查暂停**</span><span class="sxs-lookup"><span data-stu-id="021ff-170">**Investigation suspended**</span></span> | <span data-ttu-id="021ff-p116">如果对潜在问题的详细调查需要请求客户提供其他信息，以便进行进一步的调查，则你将看到此状态。如果我们需要你的参与，我们会告知你所需的数据或日志。</span><span class="sxs-lookup"><span data-stu-id="021ff-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="021ff-173">**已还原服务**</span><span class="sxs-lookup"><span data-stu-id="021ff-173">**Service restored**</span></span> | <span data-ttu-id="021ff-p117">我们确认纠正措施已解决基础问题，且服务已还原到正常状态。若要了解出了什么问题，请查看问题详细信息。</span><span class="sxs-lookup"><span data-stu-id="021ff-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="021ff-176">**发布后事件报告**</span><span class="sxs-lookup"><span data-stu-id="021ff-176">**Post-incident report published**</span></span> | <span data-ttu-id="021ff-177">我们已发布的特定问题包含根原因信息和下一步步骤，以确保类似问题不会再次发生 Post 事件报告。</span><span class="sxs-lookup"><span data-stu-id="021ff-177">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |
   
## <a name="history"></a><span data-ttu-id="021ff-178">“历史记录”</span><span class="sxs-lookup"><span data-stu-id="021ff-178">History</span></span>

<span data-ttu-id="021ff-p118">服务运行状况，可以查看当前运行状况和查看任何服务咨询和已过去 30 天内影响您的租户的事件的历史记录。若要查看过去的所有服务运行状况，选择**服务运行状况**页上的**查看历史记录**。</span><span class="sxs-lookup"><span data-stu-id="021ff-p118">Service health lets you look at current health status and view the history of any service advisories and incidents that have impacted your tenant in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="021ff-182">显示在选定时间范围内发布的所有服务运行状况消息的列表，如下所示：</span><span class="sxs-lookup"><span data-stu-id="021ff-182">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="021ff-p119">最近 7 天或 30 天内，您可以查看运行状况历史记录。选择要查看有关该问题的更多详细信息任何行。</span><span class="sxs-lookup"><span data-stu-id="021ff-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="021ff-186">有关我们承诺正常运行时间的详细信息，请参阅[从 Office 365 的透明操作](https://go.microsoft.com/fwlink/?linkid=848695)。</span><span class="sxs-lookup"><span data-stu-id="021ff-186">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="021ff-187">提供反馈</span><span class="sxs-lookup"><span data-stu-id="021ff-187">Leave feedback</span></span>

<span data-ttu-id="021ff-p120">我们的目标是确保向你及时、准确地提供仍在持续的问题的有用信息。若要告知我们采取的操作是否切实有效，请选择一个星级评分。给我们评出 1 - 5 星的分数后，你可以提供有关任何特定详细信息的反馈。我们将使用你的反馈微调服务运行状况系统。</span><span class="sxs-lookup"><span data-stu-id="021ff-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Feedback form for service health issues](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="021ff-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="021ff-193">See also</span></span>

[<span data-ttu-id="021ff-194">Office 365 管理中心内的活动报表</span><span class="sxs-lookup"><span data-stu-id="021ff-194">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

