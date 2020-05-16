---
title: 如何检查 Microsoft 365 服务运行状况
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
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: 在呼叫支持之前查看 Microsoft 365 服务的运行状况状态，以查看是否有活动的服务中断。
ms.openlocfilehash: d937310faeaf5af63a6c36841d7a609006fc4ab5
ms.sourcegitcommit: 057f0fce08b41a00581fc4736cad89270129c703
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2020
ms.locfileid: "44266674"
---
# <a name="how-to-check-microsoft-365-service-health"></a><span data-ttu-id="6ce02-103">如何检查 Microsoft 365 服务运行状况</span><span class="sxs-lookup"><span data-stu-id="6ce02-103">How to check Microsoft 365 service health</span></span>

<span data-ttu-id="6ce02-104">[![显示管理中心正在更改且你可在 aka.ms/aboutM365preview 找到更多详细信息的标签。](media/O365-Admin-AdminCenterChanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview?view=o365-worldwide)</span><span class="sxs-lookup"><span data-stu-id="6ce02-104">[![Label to let you know the admin center is changing and you can find more details at aka.ms/aboutM365preview.](media/O365-Admin-AdminCenterChanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview?view=o365-worldwide)</span></span>

<span data-ttu-id="6ce02-105">您可以在[microsoft 365 管理中心](https://go.microsoft.com/fwlink/p/?linkid=2024339)的 "**服务运行状况**" 页上查看 microsoft 服务的运行状况，包括 web 上的 Office、YAMMER、Microsoft Dynamics CRM 和移动设备管理云服务。</span><span class="sxs-lookup"><span data-stu-id="6ce02-105">You can view the health of your Microsoft services, including Office on the web, Yammer, Microsoft Dynamics CRM, and mobile device management cloud services, on the **Service health** page in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).</span></span> <span data-ttu-id="6ce02-106">If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span><span class="sxs-lookup"><span data-stu-id="6ce02-106">If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span>

<span data-ttu-id="6ce02-107">如果无法登录到服务门户，则可以使用 "[服务状态" 页](https://status.office365.com)来检查阻止你登录租户的已知问题。</span><span class="sxs-lookup"><span data-stu-id="6ce02-107">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="6ce02-108">如何查看服务运行状况</span><span class="sxs-lookup"><span data-stu-id="6ce02-108">How to check service health</span></span>

1. <span data-ttu-id="6ce02-109">转到 Microsoft 365 管理中心 [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339) ，并使用管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="6ce02-109">Go to the Microsoft 365 admin center at [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339), and sign in with an admin account.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6ce02-110">分配为全局管理员或服务管理员角色的人员可以查看服务运行状况。</span><span class="sxs-lookup"><span data-stu-id="6ce02-110">People who are assigned the global admin or service administrator role can view service health.</span></span> <span data-ttu-id="6ce02-111">若要允许 Exchange、SharePoint 和 Skype for Business 管理员查看服务运行状况，必须向他们分配服务管理员角色。</span><span class="sxs-lookup"><span data-stu-id="6ce02-111">To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span> <span data-ttu-id="6ce02-112">有关可查看服务运行状况的角色的详细信息，请参阅[关于管理员角色](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide#roles-available-in-the-microsoft-365-admin-center)。</span><span class="sxs-lookup"><span data-stu-id="6ce02-112">For more information about roles that can view service health, see [About admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide#roles-available-in-the-microsoft-365-admin-center).</span></span>
  
2. <span data-ttu-id="6ce02-113">如果您没有使用新管理中心，请在**主页**上，选择右上角的 "**尝试新管理中心**" 切换。</span><span class="sxs-lookup"><span data-stu-id="6ce02-113">If you are not using the new admin center, on the **Home** page, select the **Try the new admin center** toggle in the upper-right corner.</span></span>

3. <span data-ttu-id="6ce02-114">若要查看服务运行状况，请在 "管理中心" 中，转到 "**运行状况**  >  **服务运行状况**"，或选择 "**主页" 仪表板**上的**服务运行状况**卡片。</span><span class="sxs-lookup"><span data-stu-id="6ce02-114">To view service health, in the admin center, go to **Health** > **Service health**, or select the **Service health** card on the **Home dashboard**.</span></span> <span data-ttu-id="6ce02-115">仪表板卡片指示是否存在活动的服务问题，以及指向详细**服务运行状况**页面的链接。</span><span class="sxs-lookup"><span data-stu-id="6ce02-115">The dashboard card indicates whether there is an active service issue and links to the detailed **Service health** page.</span></span>
  
4. <span data-ttu-id="6ce02-116">在 "**服务运行状况**" 页上，将以表格格式显示每个云服务的运行状况状态。</span><span class="sxs-lookup"><span data-stu-id="6ce02-116">On the **Service health** page, the health state of each cloud service is shown in a table format.</span></span>

   ![View of current issues in service health](media/service-health-all-services.png)

<span data-ttu-id="6ce02-118">"**所有服务**" 选项卡（默认视图）显示所有服务及其当前运行状况状态。</span><span class="sxs-lookup"><span data-stu-id="6ce02-118">The **All services** tab (the default view) shows all services and their current health state.</span></span> <span data-ttu-id="6ce02-119">图标和**状态**列指示每个服务的状态。</span><span class="sxs-lookup"><span data-stu-id="6ce02-119">An icon and the **Status** column indicate the state of each service.</span></span> 

<span data-ttu-id="6ce02-120">若要将视图筛选为当前遇到事件的服务，请选择页面顶部的 "**事件**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="6ce02-120">To filter your view to services currently experiencing an incident, select the **Incidents** tab at the top of the page.</span></span> <span data-ttu-id="6ce02-121">选择 "**建议**" 选项卡将仅显示当前已发布建议的服务。</span><span class="sxs-lookup"><span data-stu-id="6ce02-121">Selecting the **Advisories** tab will show only services that currently have an advisory posted.</span></span> 

<span data-ttu-id="6ce02-122">"**历史记录**" 选项卡显示已解决的事件和建议的历史记录。</span><span class="sxs-lookup"><span data-stu-id="6ce02-122">The **History** tab shows the history of incidents and advisories that have been resolved.</span></span>

<span data-ttu-id="6ce02-123">如果 Microsoft 365 服务遇到问题，并且未在 "**服务运行状况**" 页上看到它，请选择 "**报告问题**" 并填写 "短格式" 来告诉我们它。</span><span class="sxs-lookup"><span data-stu-id="6ce02-123">If you're experiencing an issue with a Microsoft 365 service and you don’t see it listed on the **Service health** page, tell us about it by selecting **Report an issue**, and completing the short form.</span></span> <span data-ttu-id="6ce02-124">我们将介绍其他组织提供的相关数据和报告，以查看问题的广泛程度，以及是否与我们的服务有关。</span><span class="sxs-lookup"><span data-stu-id="6ce02-124">We’ll look at related data and reports from other organizations to see how widespread the issue is, and if it originated with our service.</span></span> <span data-ttu-id="6ce02-125">如果是，我们会将其作为新事件或 "**服务运行状况**" 页上的公告添加，您可以在其中跟踪其解决方案。</span><span class="sxs-lookup"><span data-stu-id="6ce02-125">If it did, we’ll add it as a new incident or advisory on the **Service health** page, where you can track its resolution.</span></span> <span data-ttu-id="6ce02-126">如果您在30分钟内未看到它显示在列表中，请考虑联系支持人员以解决此问题。</span><span class="sxs-lookup"><span data-stu-id="6ce02-126">If you don’t see it appear on the list within about 30 minutes, consider contacting support to resolve the issue.</span></span>

<span data-ttu-id="6ce02-127">若要注册影响你的租户的新事件的电子邮件通知以及活动事件的状态更改，请选择 "**首选项**"，单击 "**在电子邮件中向我发送服务 heath 通知**"，然后指定：</span><span class="sxs-lookup"><span data-stu-id="6ce02-127">To sign up for email notifications of new incidents that affect your tenant and status changes for an active incident, select **Preferences**, click **Send me service heath notifications in email**, and then specify:</span></span>

- <span data-ttu-id="6ce02-128">最大为两个电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="6ce02-128">Up to two email addresses.</span></span>
- <span data-ttu-id="6ce02-129">您是否需要针对事件或建议的通知</span><span class="sxs-lookup"><span data-stu-id="6ce02-129">Whether you want notifications for incidents or advisories</span></span>
- <span data-ttu-id="6ce02-130">要通知的服务</span><span class="sxs-lookup"><span data-stu-id="6ce02-130">The services for which you want notification</span></span>

> [!TIP]
> <span data-ttu-id="6ce02-131">您还可以在移动设备上使用[Microsoft 365 管理应用](https://go.microsoft.com/fwlink/p/?linkid=627216)来查看服务运行状况，这是保持最新的推送通知的绝佳方式。</span><span class="sxs-lookup"><span data-stu-id="6ce02-131">You can also use the [Microsoft 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="6ce02-132">查看已发布服务的运行状况详细信息</span><span class="sxs-lookup"><span data-stu-id="6ce02-132">View details of posted service health</span></span>

<span data-ttu-id="6ce02-133">在 "**所有服务**" 视图中，选择服务状态将打开 "建议" 或 "事件" 的摘要视图。</span><span class="sxs-lookup"><span data-stu-id="6ce02-133">On the **All services** view, selecting the service status will open a summary view of advisories or incidents.</span></span>
  
![显示服务建议的屏幕截图](media/service-health-advisory.png)

<span data-ttu-id="6ce02-135">公告或事件摘要提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="6ce02-135">The advisory or incident summary provides the following information:</span></span>

- <span data-ttu-id="6ce02-136">**标题**-问题的摘要。</span><span class="sxs-lookup"><span data-stu-id="6ce02-136">**Title** - A summary of the problem.</span></span>
- <span data-ttu-id="6ce02-137">**服务**-受影响的服务的名称。</span><span class="sxs-lookup"><span data-stu-id="6ce02-137">**Service** - The name of the affected service.</span></span>
- <span data-ttu-id="6ce02-138">**ID** -问题的数字标识符。</span><span class="sxs-lookup"><span data-stu-id="6ce02-138">**ID** - A numeric identifier for the problem.</span></span>
- <span data-ttu-id="6ce02-139">**状态**-此问题对服务产生的影响。</span><span class="sxs-lookup"><span data-stu-id="6ce02-139">**Status** - How this problem affects the service.</span></span>
- <span data-ttu-id="6ce02-140">**开始时间**-问题开始的时间。</span><span class="sxs-lookup"><span data-stu-id="6ce02-140">**Start time** - The time when the issue started.</span></span>
- <span data-ttu-id="6ce02-141">**上次更新**时间-上次更新服务运行状况消息的时间。</span><span class="sxs-lookup"><span data-stu-id="6ce02-141">**Last updated** - The last time that the service health message was updated.</span></span> <span data-ttu-id="6ce02-142">我们会通过频繁的消息进行发布，让你知道我们在应用解决方案时要做的进展。</span><span class="sxs-lookup"><span data-stu-id="6ce02-142">We post frequent messages to let you know the progress that we're making in applying a solution.</span></span>

<span data-ttu-id="6ce02-143">选择 "问题标题" 以查看 "问题详细信息" 页，其中显示了有关该问题的详细信息，包括在处理解决方案时发布的所有邮件的[历史记录](#history)。</span><span class="sxs-lookup"><span data-stu-id="6ce02-143">Select the issue title to see the issue detail page, which shows more information about the issue, including the [history](#history) of all messages posted while we work on a solution.</span></span>

![显示问题详细信息的屏幕截图](media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a><span data-ttu-id="6ce02-145">翻译服务运行状况详细信息</span><span class="sxs-lookup"><span data-stu-id="6ce02-145">Translate service health details</span></span>

<span data-ttu-id="6ce02-p108">服务运行状况说明是实时发布的，因此这些说明不会自动翻译成你的语言，并且服务事件的详细信息仅以英语形式提供。若要翻译这些说明，请遵循以下步骤：</span><span class="sxs-lookup"><span data-stu-id="6ce02-p108">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="6ce02-148">转到[翻译工具](https://www.bing.com/translator/)。</span><span class="sxs-lookup"><span data-stu-id="6ce02-148">Go to [Translator](https://www.bing.com/translator/).</span></span>

2. <span data-ttu-id="6ce02-p109">在" **服务运行状况**"页上，选择一个事件或公告。在" **显示详细信息**"下，复制关于该问题的文本。</span><span class="sxs-lookup"><span data-stu-id="6ce02-p109">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>

3. <span data-ttu-id="6ce02-151">在"翻译工具"中，粘贴文本，然后选择" **翻译**"。</span><span class="sxs-lookup"><span data-stu-id="6ce02-151">In Translator, paste the text and choose **Translate**.</span></span>

### <a name="definitions"></a><span data-ttu-id="6ce02-152">定义</span><span class="sxs-lookup"><span data-stu-id="6ce02-152">Definitions</span></span>

<span data-ttu-id="6ce02-153">大多数情况下，服务将显示为正常，没有进一步的信息。</span><span class="sxs-lookup"><span data-stu-id="6ce02-153">Most of the time, services will appear as healthy with no further information.</span></span> <span data-ttu-id="6ce02-154">服务出现问题时，该问题会标识为公告或事件，并显示当前状态。</span><span class="sxs-lookup"><span data-stu-id="6ce02-154">When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="6ce02-155">服务运行状况中不会显示计划内维护事件。</span><span class="sxs-lookup"><span data-stu-id="6ce02-155">Planned maintenance events aren't shown in service health.</span></span> <span data-ttu-id="6ce02-156">可以通过" **消息中心**"随时了解最新消息，从而跟踪计划内维护事件。</span><span class="sxs-lookup"><span data-stu-id="6ce02-156">You can track planned maintenance events by staying up to date with the **Message center**.</span></span> <span data-ttu-id="6ce02-157">筛选出分类为"更改计划"的消息，了解发生更改的时间、其影响以及如何做好相应准备。</span><span class="sxs-lookup"><span data-stu-id="6ce02-157">Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it.</span></span> <span data-ttu-id="6ce02-158">有关详细信息，请参阅[Microsoft 365 中的消息中心](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093)。</span><span class="sxs-lookup"><span data-stu-id="6ce02-158">See [Message center in Microsoft 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span>
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="6ce02-159">事件和公告</span><span class="sxs-lookup"><span data-stu-id="6ce02-159">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="6ce02-p112">如果服务显示公告，这意味着某问题正在影响一些用户，但该服务仍然可用。公告中通常存在针对该问题的变通方法，并且该问题可能是间歇性的，或其作用范围和对用户的影响有限。</span><span class="sxs-lookup"><span data-stu-id="6ce02-p112">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="6ce02-p113">如果服务显示遇到活动事件，则说明遇到关键问题，且服务或其主要功能目前不可用。例如，用户可能无法发送和接收电子邮件，或无法登录。事件会对用户产生显著影响。对于正在进行的事件，我们会在服务运行状况仪表板中提供有关调查、缓解措施和解决方法确认的更新。</span><span class="sxs-lookup"><span data-stu-id="6ce02-p113">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |

### <a name="status-definitions"></a><span data-ttu-id="6ce02-168">状态定义</span><span class="sxs-lookup"><span data-stu-id="6ce02-168">Status definitions</span></span>

|<span data-ttu-id="6ce02-169">**状态**</span><span class="sxs-lookup"><span data-stu-id="6ce02-169">**Status**</span></span>|<span data-ttu-id="6ce02-170">**定义**</span><span class="sxs-lookup"><span data-stu-id="6ce02-170">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6ce02-171">**正在调查**</span><span class="sxs-lookup"><span data-stu-id="6ce02-171">**Investigating**</span></span> | <span data-ttu-id="6ce02-172">我们已发现存在潜在问题，我们正在收集有关情况和影响范围的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6ce02-172">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="6ce02-173">**服务降级**</span><span class="sxs-lookup"><span data-stu-id="6ce02-173">**Service degradation**</span></span> | <span data-ttu-id="6ce02-p114">我们已确认存在可能影响服务或功能使用的问题。例如，如果服务的执行速度比平常慢、存在间歇性中断或某功能运行不正常，则可能看到此状态。</span><span class="sxs-lookup"><span data-stu-id="6ce02-p114">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="6ce02-176">**服务中断**</span><span class="sxs-lookup"><span data-stu-id="6ce02-176">**Service interruption**</span></span> | <span data-ttu-id="6ce02-p115">如果我们确定某问题影响用户访问服务的能力，则你将看到此状态。在本例中，问题十分重大且可持续重现。</span><span class="sxs-lookup"><span data-stu-id="6ce02-p115">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="6ce02-179">**正在还原服务**</span><span class="sxs-lookup"><span data-stu-id="6ce02-179">**Restoring service**</span></span> | <span data-ttu-id="6ce02-180">我们已确定问题成因，知晓需要采取的纠正措施，并正在将服务恢复到正常状态。</span><span class="sxs-lookup"><span data-stu-id="6ce02-180">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="6ce02-181">**延期恢复**</span><span class="sxs-lookup"><span data-stu-id="6ce02-181">**Extended recovery**</span></span> | <span data-ttu-id="6ce02-p116">此状态表示正在执行纠正措施，为大多数用户恢复服务，但恢复所有受影响的系统仍需一些时间。如果我们为了减轻影响，而在实施永久解决措施前实施临时措施，你也可能看到此状态。</span><span class="sxs-lookup"><span data-stu-id="6ce02-p116">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="6ce02-184">**调查暂停**</span><span class="sxs-lookup"><span data-stu-id="6ce02-184">**Investigation suspended**</span></span> | <span data-ttu-id="6ce02-p117">如果对潜在问题的详细调查需要请求客户提供其他信息，以便进行进一步的调查，则你将看到此状态。如果我们需要你的参与，我们会告知你所需的数据或日志。</span><span class="sxs-lookup"><span data-stu-id="6ce02-p117">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="6ce02-187">**已还原服务**</span><span class="sxs-lookup"><span data-stu-id="6ce02-187">**Service restored**</span></span> | <span data-ttu-id="6ce02-p118">我们确认纠正措施已解决基础问题，且服务已还原到正常状态。若要了解出了什么问题，请查看问题详细信息。</span><span class="sxs-lookup"><span data-stu-id="6ce02-p118">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="6ce02-190">**误报**</span><span class="sxs-lookup"><span data-stu-id="6ce02-190">**False positive**</span></span> | <span data-ttu-id="6ce02-191">在进行详细调查之后，我们已确认服务运行正常且按设计正常运行。</span><span class="sxs-lookup"><span data-stu-id="6ce02-191">After a detailed investigation, we’ve confirmed the service is healthy and operating as designed.</span></span> <span data-ttu-id="6ce02-192">不会对服务造成任何影响，也不会导致事件发生在服务之外。</span><span class="sxs-lookup"><span data-stu-id="6ce02-192">No impact to the service was observed or the cause of the incident originated outside of the service.</span></span> |
|<span data-ttu-id="6ce02-193">**已发布事件后报告**</span><span class="sxs-lookup"><span data-stu-id="6ce02-193">**Post-incident report published**</span></span> | <span data-ttu-id="6ce02-194">我们已发布了一个针对特定问题的公告事件报告，其中包括根本原因信息和后续步骤，以确保不会发生类似的问题。</span><span class="sxs-lookup"><span data-stu-id="6ce02-194">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |

### <a name="history"></a><span data-ttu-id="6ce02-195">历史记录</span><span class="sxs-lookup"><span data-stu-id="6ce02-195">History</span></span>

<span data-ttu-id="6ce02-196">服务运行状况允许你查看当前运行状况状态，并查看在过去30天内受到影响的任何服务通知和事件的历史记录。</span><span class="sxs-lookup"><span data-stu-id="6ce02-196">Service health lets you look at current health status and view the history of any service advisories and incidents that have affected your tenant in the past 30 days.</span></span> <span data-ttu-id="6ce02-197">若要查看所有服务的过去运行状况，请在 "问题详细信息" 页上选择 "**查看历史记录**"。</span><span class="sxs-lookup"><span data-stu-id="6ce02-197">To view the past health of all services, select **View history** on the issue detail page.</span></span>
  
![Show link to health history](media/service-health-view-history.png)
  
<span data-ttu-id="6ce02-199">显示在选定时间范围内发布的所有服务运行状况消息的列表，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6ce02-199">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![View service health history](media/service-health-history.png)
  
<span data-ttu-id="6ce02-201">展开任意行以查看有关问题的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="6ce02-201">Expand any row to view more details about the issue.</span></span>
  
<span data-ttu-id="6ce02-202">有关我们对运行时间的承诺的详细信息，请参阅[来自 Microsoft 365 的透明操作](https://go.microsoft.com/fwlink/?linkid=848695)。</span><span class="sxs-lookup"><span data-stu-id="6ce02-202">For more information about our commitment to uptime, see [Transparent operations from Microsoft 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ce02-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ce02-203">See also</span></span>

[<span data-ttu-id="6ce02-204">Microsoft 365 管理中心中的活动报告</span><span class="sxs-lookup"><span data-stu-id="6ce02-204">Activity Reports in the Microsoft 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)