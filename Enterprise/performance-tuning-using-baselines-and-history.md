---
title: 使用基线和性能历史记录优化 Office 365 性能
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/31/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 1492cb94-bd62-43e6-b8d0-2a61ed88ebae
description: 有一些简单的方法，可以检查 Office 365 和业务，以便可以建立粗略您连接的基准之间的连接性能。了解您的客户端的性能历史记录计算机连接可以帮助您早期检测新兴问题、 识别和预测问题。
ms.openlocfilehash: bb1fe1e1450798e43c15a07610e27450bce6ea5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539691"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a><span data-ttu-id="33ffc-104">使用基线和性能历史记录优化 Office 365 性能</span><span class="sxs-lookup"><span data-stu-id="33ffc-104">Office 365 performance tuning using baselines and performance history</span></span>

<span data-ttu-id="33ffc-p102">有一些简单的方法，可以检查 Office 365 和业务，以便可以建立粗略您连接的基准之间的连接性能。了解您的客户端的性能历史记录计算机连接可以帮助您早期检测新兴问题、 识别和预测问题。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p102">There are some simple ways to check the connection performance between Office 365 and your business that will let you establish a rough baseline of your connectivity. Knowing the performance history of your client computer connections can help you detect emerging issues early, identify, and predict problems.</span></span>
  
<span data-ttu-id="33ffc-p103">如果您不是用于处理性能问题，这篇文章旨在帮助您考虑一些常见的问题，就像您如何知道您会看到的问题是性能问题而不是 Office 365 服务事件？如何可以规划好的性能，长期？如何对性能保留眼睛？如果您团队或客户端查看性能太慢时使用的 Office 365 和橙黄以上任一问题，请继续阅读。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p103">If you're not used to working on performance issues, this article is designed to help you consider some common questions, like How do you know the problem you're seeing is a performance issue and not an Office 365 service incident? How can you plan for good performance, long term? How can you keep an eye on performance? If your team or clients are seeing slow performance while using Office 365, and you wonder about any of these questions, read on.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="33ffc-p104">**立即具有您的客户端和 Office 365 之间的性能问题？** 按照列出的[性能疑难解答规划 Office 365](performance-troubleshooting-plan.md)中的步骤。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p104">**Have a performance issue between your client and Office 365 right now?** Follow the steps outlined in the [Performance troubleshooting plan for Office 365](performance-troubleshooting-plan.md).</span></span> 
    
## <a name="something-you-should-know-about-office-365-performance"></a><span data-ttu-id="33ffc-113">您应了解有关 Office 365 性能内容</span><span class="sxs-lookup"><span data-stu-id="33ffc-113">Something you should know about Office 365 performance</span></span>

<span data-ttu-id="33ffc-p105">Office 365 居住持续监视而不仅仅是通过自动化，但实际用户所关注的高容量、 专用 Microsoft 网络内部。构建在性能调整和优化可能的维护 Office 365 云角色的一部分。Office 365 云的客户端必须通过 Internet 连接，因为没有连续努力过优化跨 Office 365 服务的性能。性能改进从不真正停止在云中，并且没有大量使用健康和快速保留在云中的累计体验。您应遇到性能问题从您的位置连接到 Office 365，它最佳，并不等待，支持案例。相反，您应该先调查从 inside out 问题 （英文）。即在您的网络，启动并计算出到 Office 365 自己的方式。使用 Office 365 支持打开案例之前，您可以收集数据，并执行操作会探索，并可能会解决问题。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p105">Office 365 lives inside a high-capacity, dedicated Microsoft network that is steadily monitored not just by automation, but by real people. Part of the role of maintaining the Office 365 cloud is building-in performance tuning and streamlining where it's possible. Since clients of the Office 365 cloud have to connect across the Internet, there is a continuous effort to fine-tune the performance across Office 365 services too. Performance improvements never really stop in the cloud, and there is a lot of accumulated experience with keeping the cloud healthy and quick. Should you experience a performance issue connecting from your location to Office 365, it's best not to start with, and wait on, a Support case. Instead, you should begin investigating the problem from 'the inside out'. That is, start inside of your network, and work your way out to Office 365. Before you open a case with Office 365 Support, you can gather data and take actions that will explore, and may resolve, your problem.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="33ffc-p106">注意的容量规划和 Office 365 中的限制。该信息会将您之前曲线尝试解决性能问题时。下面是指向[Office 365 平台服务说明](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx)的链接。这是中心位置，并提供 Office 365 的所有服务都有一个从此处转到其自己的服务说明的链接。这意味着，您需要以查看 SharePoint online 标准限制，例如单击[SharePoint Online 服务说明](https://technet.microsoft.com/en-us/library/sharepoint-online-service-description.aspx)并找到其[SharePoint Online 限制部分](https://go.microsoft.com/fwlink/p/?LinkID=856113)。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p106">Be aware of capacity planning and limits in Office 365. That information will put you ahead of the curve when trying to resolve a performance issue. Here's a link to the [Office 365 Platform Service Description](https://technet.microsoft.com/en-us/library/office-365-service-descriptions.aspx). This is a central hub, and all the services offered by Office 365 have a link that goes to their own Service Descriptions from here. That means, should you need to see the standard limits for SharePoint Online, for example, you would click [SharePoint Online Service Description](https://technet.microsoft.com/en-us/library/sharepoint-online-service-description.aspx) and locate its [SharePoint Online Limits section](https://go.microsoft.com/fwlink/p/?LinkID=856113).</span></span> 
  
<span data-ttu-id="33ffc-p107">请确保您转到了解与故障排除性能弹性标准，它不是有关实现看到理想的值并永久维护 (如果您认为这是，那么可以偶尔高带宽任务喜欢的白板大量用户，或执行大量数据迁移将非常压力-，以便执行规划性能的影响然后)。可以并应，具有大致了解您性能目标，但大量变量播放到性能，因此，性能会有所不同。这是性能的特性。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p107">Make sure you go into your troubleshooting with the understanding that performance is a sliding scale, it's not about achieving an idealized value and maintaining it permanently (if you believe this is so, then occasional high-bandwidth tasks like on-boarding a large number of users, or doing large data migrations will be very stressful -- so do plan for performance impacts then). You can, and should, have a rough idea of your performance targets, but a lot of variables play into performance, therefore, performance varies. That's the nature of performance.</span></span> 
  
<span data-ttu-id="33ffc-130">有关会议特定目标性能疑难解答不和无限期保留这些编号，它是有关改进现有活动授予所有变量。</span><span class="sxs-lookup"><span data-stu-id="33ffc-130">Performance troubleshooting isn't about meeting specific goals and maintaining those numbers indefinitely, it's about improving existing activities, given all the variables.</span></span> 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a><span data-ttu-id="33ffc-131">好了，性能问题表现形式是什么？</span><span class="sxs-lookup"><span data-stu-id="33ffc-131">Okay, what does a performance problem look like?</span></span>

<span data-ttu-id="33ffc-p108">首先，您需要确保您遇到良言性能问题和不服务事件。性能问题是不同 Office 365 中服务事件。下面是如何告知他们分离。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p108">First, you need to make sure that what you are experiencing is indeed a performance issue and not a service incident. A performance problem is different from a service incident in Office 365. Here's how to tell them apart.</span></span>
  
<span data-ttu-id="33ffc-p109">Office 365 服务时遇到问题，如果这是服务事件。您将看到运行 Office 365 管理中心中的**当前运行状况**的红色或黄色图标，您还可能注意到客户端计算机连接到 Office 365 上的性能太慢。例如，如果当前运行状况报告红色图标，请参阅**Investigating** Exchange 旁边，您可能会然后还收到大量呼叫从您的组织用户抱怨客户端使用 Exchange Online 的邮箱执行的格式错误的人员。在这种情况下，它是理由假定您的 Exchange Online 性能刚刚变为服务中的问题的受害者。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p109">If the Office 365 service is having issues, that's a service incident. You will see red or yellow icons under **Current health** in the Office 365 admin center, you may also notice slow performance on client computers connecting to Office 365. For example, if Current health reports a red icon and you see **Investigating** beside Exchange, you might then also receive a bunch of calls from people in your organization who complain that client mailboxes that use Exchange Online are performing badly. In that case, it's reasonable to assume that your Exchange Online performance just became a victim of issues within the Service.</span></span> 
  
![显示绿色，除 Exchange，其中显示服务还原的所有工作负荷与 Office 365 运行状况仪表板。](media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
<span data-ttu-id="33ffc-p110">此时，您的 Office 365 管理员、 应检查**当前运行状况**，然后**查看详细信息和历史记录**，经常以在我们的系统执行的维护保持最新。**当前运行状况**仪表板进行了更新您更改，以及服务中的问题。注释和说明写入运行状况历史记录，管理到管理员，以帮助您评估您的影响，并保留您发布有关正在进行的工作存在。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p110">At this point, you, the Office 365 admin, should check **Current health** and then **View details and history**, frequently, to keep up to date on maintenance we perform on the system. The **Current health** dashboard was made to update you about changes to, and problems in, the service. The notes and explanations written to health history, admin to admin, are there to help you gauge your impact, and to keep you posted about ongoing work.</span></span> 
  
![Office 365 运行状况仪表板解释的 Exchange Online 服务已还原的图片及使用原因。](media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
<span data-ttu-id="33ffc-p111">性能问题不服务事件，即使事件可能会导致性能太慢。性能问题如下所示：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p111">A performance issue isn't a service incident, even though incidents can cause slow performance. A performance issue looks like this:</span></span>
  
- <span data-ttu-id="33ffc-146">无论在 Office 365 管理中心内，**当前运行状况**报告服务会出现性能问题。</span><span class="sxs-lookup"><span data-stu-id="33ffc-146">A performance issue occurs no matter what the Office 365 admin center **Current health** is reporting for the service.</span></span> 
    
-  <span data-ttu-id="33ffc-147">用于为相对无缝行为需要很长时间才能完成，或无法完成。</span><span class="sxs-lookup"><span data-stu-id="33ffc-147">A behavior that used to be relatively seamless takes a long time to complete or never completes.</span></span> 
    
- <span data-ttu-id="33ffc-148">可以复制该问题，或至少，您知道它会发生是否系列正确的步骤。</span><span class="sxs-lookup"><span data-stu-id="33ffc-148">You can replicate the problem too, or, at least, you know it will happen if you do the right series of steps.</span></span>
    
-  <span data-ttu-id="33ffc-149">如果问题是间歇性，仍没有模式，例如，您知道的 10:00 将具有来自无法可靠地访问 Office 365 的用户的呼叫和周围中午死向下呼叫。</span><span class="sxs-lookup"><span data-stu-id="33ffc-149">If the problem is intermittent, there is still a pattern, for example, you know that by 10:00 AM you will have calls from users who can't reliably access Office 365, and that the calls will die down around noon.</span></span> 
    
<span data-ttu-id="33ffc-p112">这可能声音熟悉;可能会过熟悉。一旦您知道非常性能问题，变得问题，"实现哪些功能执行下一步"本文的其余部分将帮助您确定完全的。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p112">This probably sounds familiar; maybe too familiar. Once you know it's a performance problem, the question becomes, "What do you do next?" The rest of this article helps you determine exactly that.</span></span>
  
## <a name="how-to-define-and-test-the-performance-problem"></a><span data-ttu-id="33ffc-153">如何定义和测试性能问题</span><span class="sxs-lookup"><span data-stu-id="33ffc-153">How to define and test the performance problem</span></span>

<span data-ttu-id="33ffc-p113">性能问题经常出现随时间推移，因此它可以具有挑战性定义实际问题。您需要创建好问题语句，最好的问题上下文，然后您需要可重复测试步骤 win 某一天。否则，通过您自己的任何错误，可能会丢失。为什么？嗯，下面是不提供足够的信息的问题语句的一些示例：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p113">Performance issues often emerge over time, so it can be challenging to define the actual problem. You need to create a good problem statement and a good idea of issue context, and then you need to repeatable testing steps to win the day. Otherwise, through no fault of your own, you may be lost. Why? Well, here are some examples of problems statements that don't provide enough information:</span></span>
  
- <span data-ttu-id="33ffc-p114">从收件箱切换到我的日历用于有我未请注意，并且现在休息。您可以使其像它用于？</span><span class="sxs-lookup"><span data-stu-id="33ffc-p114">Switching from my Inbox to my Calendar used to be something I didn't notice, and now it's a coffee-break. Can you make it act like it used to?</span></span>
    
- <span data-ttu-id="33ffc-p115">正在永远将我的文件上载到 SharePoint Online。为什么在下午，但其他任何时间慢，它是 fast？不能它只是 fast？</span><span class="sxs-lookup"><span data-stu-id="33ffc-p115">Uploading my files to SharePoint Online is taking forever. Why is it slow in the afternoon, but any other time, it's fast? Can't it just be fast?</span></span>
    
<span data-ttu-id="33ffc-p116">有问题的语句上面所带来的几个大型挑战。具体而言，有大量的不明确问题处理。例如：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p116">There are several large challenges posed by the problem statements above. Specifically, there are a lot of ambiguities to deal with. for example:</span></span>
  
- <span data-ttu-id="33ffc-167">它不清楚如何收件箱和日历之间切换用于在便携式计算机上执行操作。</span><span class="sxs-lookup"><span data-stu-id="33ffc-167">It's unclear how switching between Inbox and Calendar used to act on the laptop.</span></span>
    
- <span data-ttu-id="33ffc-168">当用户说"无法它只是 fast"，什么是"快速"？</span><span class="sxs-lookup"><span data-stu-id="33ffc-168">When the user says, "Can't it just be fast", what's "fast"?</span></span>
    
- <span data-ttu-id="33ffc-p117">长为"永久"？这是几秒或数分钟，或无法用户转到可边午餐和它将完成 10 分钟后用户赢得 back up？</span><span class="sxs-lookup"><span data-stu-id="33ffc-p117">How long is "forever"? Is that several seconds, or minutes, or could the user go to lunch and it would finish up ten minutes after the user got back?</span></span>
    
<span data-ttu-id="33ffc-p118">所有这些是无需考虑的管理和疑难解答程序不能为注意以下问题语句从许多详细信息。例如，当问题启动最新动态;家庭网络; 上慢切换用户适用于从主页和始终只看到用户必须运行多个其他 RAM 密集型应用程序上的本地客户端或用户运行早期版本的操作系统或尚未运行新的更新。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p118">All of this is without considering that the admin and troubleshooter can't be aware of many details from problem statements like these. For example, when the problem started happening; That the user works from home and only ever sees slow switching while on a home network; That the user must run several other RAM intensive applications on the local client, or the user is running an older operating system or hasn't run recent updates.</span></span>
  
<span data-ttu-id="33ffc-p119">当用户报告性能问题时，没有大量收集的信息。收集此信息是过程的一个称为范围问题，或对其进行调查的一部分。以下是基本范围列表可用于收集有关您的性能问题的信息。此列表不是详尽，但它并开始一张您自己的地方：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p119">When users report a performance problem, there's a lot of information to collect. Collecting this information is part of a process called scoping the issue, or investigating it. The following is a basic scoping list you can use to collect information about your performance issue. This list is not exhaustive, but it's a place to start one of your own:</span></span> 
  
- <span data-ttu-id="33ffc-177">在哪些日期发生的问题，及其周围的白天或晚上皆什么时候未问题？</span><span class="sxs-lookup"><span data-stu-id="33ffc-177">On what date did the issue happen, and around what time of day or night?</span></span>
    
- <span data-ttu-id="33ffc-178">您已使用哪种类型的客户端计算机，以及如何应用程序连接到企业网络 （VPN、 有线无线）？</span><span class="sxs-lookup"><span data-stu-id="33ffc-178">What kind of client computer were you using, and how does it connect to the business network (VPN, Wired, Wireless)?</span></span>
    
- <span data-ttu-id="33ffc-179">您已使用远程或了您在办公室？</span><span class="sxs-lookup"><span data-stu-id="33ffc-179">Were you working remotely or were you in the office?</span></span>
    
- <span data-ttu-id="33ffc-180">您未尝试使用另一台计算机上的相同操作并查看相同的行为？</span><span class="sxs-lookup"><span data-stu-id="33ffc-180">Did you try the same actions on another computer and see the same behavior?</span></span>
    
- <span data-ttu-id="33ffc-181">逐步完成提供您麻烦，以便您可以编写下采取的操作的步骤。</span><span class="sxs-lookup"><span data-stu-id="33ffc-181">Walk through the steps that are giving you the trouble so that you can write the actions you take down.</span></span>
    
- <span data-ttu-id="33ffc-182">如何在秒或数分钟慢是性能？</span><span class="sxs-lookup"><span data-stu-id="33ffc-182">How slow in seconds or minutes is the performance?</span></span>
    
- <span data-ttu-id="33ffc-183">到底是您位于何处？</span><span class="sxs-lookup"><span data-stu-id="33ffc-183">Where in the world are you located?</span></span>
    
<span data-ttu-id="33ffc-p120">一些更显而易见比其他这些问题。大多数每个人都将了解疑难解答需要重现问题的具体步骤。毕竟，如何 else 可以记录新增错误，和 else 如何可以测试如果固定问题？不明显是诸如"什么的日期和时间吗问题，请参阅？"，并且"其中世界您位于？"，可在迁移后的信息。根据用户正在工作时，几个小时的时间差别可能意味着维护已在执行在您的公司网络的部分。例如，您的公司具有一个混合实现，如混合 SharePoint 搜索，可以查询搜索索引中 SharePoint Online 和本地 SharePoint Server 2013 实例，请更新可能正在进行的本地服务器场中。如果贵公司为所有在云中，系统维护可能包括添加或删除网络硬件，推出所公司范围内或发起更改 DNS 或其他核心基础结构更新。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p120">Some of these questions are more obvious than others. Most everyone will understand a troubleshooter needs the exact steps to reproduce the issue. After all, how else can you record what's wrong, and how else can you test if the issue is fixed? Less obvious are things like "What date and time did you see the issue?", and "Where in the world are you located?", information that can be used in tandem. Depending on when the user was working, a few hours of time difference may mean maintenance is already underway on parts of your company's network. If, for example, your company has a hybrid implementation, like a hybrid SharePoint Search, which can query search indexes in both SharePoint Online and an On-premises SharePoint Server 2013 instance, updates may be underway in the on-premises farm. If your company is all in the cloud, system maintenance may include adding or removing network hardware, rolling out updates that are company-wide, or making changes to DNS, or other core infrastructure.</span></span>
  
<span data-ttu-id="33ffc-p121">在解决性能问题时，它有点像犯罪场景，您必须是精确和老从证据绘制任何结论。才能执行此操作，您必须通过收集证据获取正确的问题语句。它应包括计算机的上下文、 用户的上下文中，将出现问题时, 和公开性能问题的具体步骤。此问题语句应，并保持，在您 notes 上边页面。通过演练的问题语句的分辨率工作后，您正在测试和证明您采取的操作是否已解决该问题的步骤。这是非常重要的知道完您的工作，。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p121">When you're troubleshooting a performance problem, it's a bit like a crime scene, you need to be precise and observant to draw any conclusions from the evidence. In order to do this, you must get a good problem statement by gathering evidence. It should include the computer's context, the user's context, when the problem began, and the exact steps that exposed the performance issue. This problem statement should be, and stay, the topmost page in your notes. By walking through the problem statement again after you work on the resolution, you are taking the steps to test and prove whether the actions you take have resolved the issue. This is critical to knowing when your work, there, is done.</span></span>
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a><span data-ttu-id="33ffc-197">您知道如何用于查找时良好性能吗？</span><span class="sxs-lookup"><span data-stu-id="33ffc-197">Do you know how performance used to look when it was good?</span></span>

<span data-ttu-id="33ffc-p122">如果您是 unlucky，没有人知道。没人号码。这意味着没有人可以应答简单的问题，"关于如何秒数？ 它用于接受以显示 Office 365 中的收件箱"，或"长未它使用高级管理人员的具有 Lync Online 会议时要采取？"，这是个许多公司的常见方案。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p122">If you're unlucky, nobody knows. Nobody had numbers. That means nobody can answer the simple question "About how many seconds did it used to take to bring up an Inbox in Office 365?", or "How long did it used to take when the Executives had a Lync Online meeting?", which is a common scenario for many companies.</span></span>
  
<span data-ttu-id="33ffc-201">什么是缺少下面是性能基准。</span><span class="sxs-lookup"><span data-stu-id="33ffc-201">What's missing here is a performance baseline.</span></span>
  
<span data-ttu-id="33ffc-p123">比较基准授予您的性能的上下文。应采取的比较基准偶尔为频繁，具体取决于您的公司的需求。如果您是较大的公司，您的运营团队可能已需要为您的内部部署环境的比较基准。例如，如果您的月和所有 SharePoint 服务器上的第三个星期一的第一个星期一修补所有 Exchange 服务器，您的运营团队可能具有的任务列表和方案运行后修补，证明重要功能是操作。例如，打开收件箱、 单击发送/接收，并确保更新文件夹，或在 SharePoint 中，浏览网站的主页转至企业搜索页中，并进行搜索的返回结果。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p123">Baselines give you a context for your performance. You should take a baseline occasionally to frequently, depending on the needs of your company. If you are a larger company, your Operations team may take baselines for your on-premises environment already. For example, if you patch all the Exchange servers on the first Monday of the month, and all your SharePoint servers on the third Monday, your Operations team probably has a list of tasks and scenarios it runs post-patching, to prove that critical functions are operational. For example, opening the Inbox, clicking Send/Receive, and making sure the folders update, or, in SharePoint, browsing the main page of the site, going into the enterprise Search page, and doing a search that returns results.</span></span>
  
<span data-ttu-id="33ffc-p124">如果您的应用程序使用 Office 365，一些可采取的最基本基准测量的时间 （以毫秒计） 从内部网络，客户端计算机出口点，或您保留您的网络并转到 Office 365 的点。下面是一些有用的比较基准的可以调查和记录：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p124">If your applications are in Office 365, some of the most fundamental baselines you can take measure the time (in milliseconds) from a client computer inside your network, to an egress point, or the point where you leave your network and go out to Office 365. Here are some helpful baselines that you can investigate and record:</span></span>
  
- <span data-ttu-id="33ffc-209">标识您的客户端计算机和您出口点，例如，您的代理服务器之间的设备。</span><span class="sxs-lookup"><span data-stu-id="33ffc-209">Identify the devices between your client computer and your egress point, for example, your proxy server.</span></span>
    
  - <span data-ttu-id="33ffc-210">您需要知道您的设备，以便您能上下文 (IP 地址类型的设备，et cetera) 所发生的性能问题。</span><span class="sxs-lookup"><span data-stu-id="33ffc-210">You need to know your devices so that you have context (IP addresses, type of device, et cetera) for performance problems that arise.</span></span>
    
  - <span data-ttu-id="33ffc-211">代理服务器是常见出口点，因此您可以检查 web 浏览器中查看其设置为使用，如果有哪些代理服务器。</span><span class="sxs-lookup"><span data-stu-id="33ffc-211">Proxy servers are common egress points, so you can check your web browser to see what proxy server it is set to use, if any.</span></span>
    
  - <span data-ttu-id="33ffc-212">第三方工具，能够发现并映射网络，但知道您的设备的安全方式是提出您的网络团队的成员。</span><span class="sxs-lookup"><span data-stu-id="33ffc-212">There are third party tools that can discover and map your network, but the safest way to know your devices is to ask a member of your network team.</span></span>
    
- <span data-ttu-id="33ffc-213">确定 Internet 服务提供商 (ISP)，记下他们的联系信息，并要求多少电路您有多少带宽。</span><span class="sxs-lookup"><span data-stu-id="33ffc-213">Identify your Internet service provider (ISP), write down their contact information, and ask how many circuits how much bandwidth you have.</span></span>
    
- <span data-ttu-id="33ffc-214">您的公司内标识资源出口点，您的客户端之间的设备或确定紧急联系人可以与讨论网络问题。</span><span class="sxs-lookup"><span data-stu-id="33ffc-214">Inside your company, identify resources for the devices between your client and the egress point, or identify an emergency contact to talk to about networking issues.</span></span>
    
<span data-ttu-id="33ffc-215">下面是一些比较基准的简单测试工具可以为您进行计算：</span><span class="sxs-lookup"><span data-stu-id="33ffc-215">Here are some baselines that simple testing with tools can calculate for you:</span></span>
  
- <span data-ttu-id="33ffc-216">从客户端计算机到出口点以毫秒为单位的时间</span><span class="sxs-lookup"><span data-stu-id="33ffc-216">Time from your client computer to your egress point in milliseconds</span></span>
    
- <span data-ttu-id="33ffc-217">时间从出口点到 Office 365 （毫秒）</span><span class="sxs-lookup"><span data-stu-id="33ffc-217">Time from your egress point to Office 365 in milliseconds</span></span>
    
- <span data-ttu-id="33ffc-218">世界上的服务器的 Office 365 中解析 URL 时您浏览的位置</span><span class="sxs-lookup"><span data-stu-id="33ffc-218">Location in the world of the server that resolves the URLS for Office 365 when you browse</span></span>
    
- <span data-ttu-id="33ffc-219">您的 ISP DNS 解析，以毫秒为单位，数据包到达 （网络抖动） 中的不一致的速度上载和下载以毫秒为单位的时间</span><span class="sxs-lookup"><span data-stu-id="33ffc-219">The speed of your ISP's DNS resolution in milliseconds, inconsistencies in packet arrival (network jitter), upload and download times in milliseconds</span></span>
    
<span data-ttu-id="33ffc-220">如果您不熟悉如何执行这些步骤，我们将进入本文中的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="33ffc-220">If you're unfamiliar with how to carry out these steps, we'll go into more detail in this article.</span></span> 
  
## <a name="what-is-a-baseline"></a><span data-ttu-id="33ffc-221">什么是一个比较基准？</span><span class="sxs-lookup"><span data-stu-id="33ffc-221">What is a baseline?</span></span>

<span data-ttu-id="33ffc-p125">它不仅仅是错误，但如果您不知道您历史性能数据，则不能具有上下文如何错误它可能已损坏，以及时，您将知道影响。使您没有比较基准，缺少关键的线索，拼图： 拼图框上的图片。在性能疑难解答，您需要*比较*的点。简单的性能比较基准不执行变得比较困难。可以按计划执行这些被需要运营团队。例如，假设您的连接如下所示：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p125">You'll know the impact when it goes bad, but if you don't know your historical performance data, it's not possible to have a context for how bad it may have become, and when. So without a baseline, you're missing the key clue to solve the puzzle: the picture on the puzzle box. In performance troubleshooting, you need a point of  *comparison*  . Simple performance baselines aren't difficult to take. Your Operations team can be tasked with carrying these out on a schedule. For example, let's say your connection looks like this:</span></span> 
  
![显示客户端、 代理和 Office 365 云基本网络图形。](media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
<span data-ttu-id="33ffc-p126">这意味着您已与网络团队检查并找到保留通过代理服务器，Internet 贵公司和该代理服务器处理所有客户端计算机发送到云的请求。在这种情况下，您应绘制连接，其中列出了所有干扰的设备的简化的版本。现在，插入可用于测试客户端 （即您离开网络为 Internet） 的出口点，之间的性能和 Office 365 云的工具。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p126">That means you've checked with your network team and found out that you leave your company for the Internet through a proxy server, and that proxy handles all the requests your client computer sends to the cloud. In this case, you should draw a simplified version of your connection that lists all the intervening devices. Now, insert tools that you can use to test the performance between the client, the egress point (where you leave your network for the Internet), and the Office 365 cloud.</span></span>
  
![与客户端、 代理和云和工具建议 PSPing，TraceTCP，基本网络和网络跟踪。](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
<span data-ttu-id="33ffc-p127">由于专业技能需要查找性能数据量为**简单**和**高级**列出了选项。网络跟踪将花费大量的时间，相比于运行 PsPing 和 TraceTCP 类似的命令行工具。已选择这两个命令行工具，因为它们不使用 ICMP 数据包，将受到阻止 Office 365，以及他们授予以毫秒为单位的时间，因为需要使客户端计算机或代理服务器 （如果您具有访问权限） 和 Office 365 到达。每个单个跃点计算机到另一个将结尾时间值，就是非常适合基线 ！就像重要的是，这些命令行工具允许您添加到命令一个端口号，这很有用是因为通过端口 443，它是使用安全套接字层以及传输层安全性 （SSL 和 TLS） 的端口的 Office 365 通信。但是，其他第三方工具可能更好的解决方案，您的具体情况。Microsoft 不支持所有这些工具，因此，如果由于某种原因，无法获取 PsPing TraceTCP 工作，移到带有 Netmon 类似的工具的网络跟踪。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p127">The options are listed as **Simple** and **Advanced** because of the amount of expertise you need in order to find the performance data. A network trace will take a lot of time, compared to running command-line tools like PsPing and TraceTCP. These two command-line tools were chosen because they don't use ICMP packets, which will be blocked by Office 365, and because they give the time in milliseconds that it takes to leave the client computer, or proxy server (if you have access) and arrive at Office 365. Each individual hop from one computer to another will end up with a time value, and that's great for baselines! Just as importantly, these command-line tools allow you to add a port number onto the command, this is useful because Office 365 communicates over port 443, which is the port used by Secure Sockets Layer and Transport Layer Security (SSL and TLS). However, other third-party tools may be better solutions for your situation. Microsoft doesn't support all of these tools, so if, for some reason, you can't get PsPing and TraceTCP working, move on to a network trace with a tool like Netmon.</span></span> 
  
<span data-ttu-id="33ffc-p128">您可以采取之前营业再次期间大量使用的比较基准，然后再次班后的。这意味着您可能遇到的文件夹结构如下所示有点最终：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p128">You can take a baseline before business hours, again during heavy use, and then again after hours. This means you may have a folder structure that looks a bit like this in the end:</span></span>
  
![建议将性能数据组织到文件夹的方式的图形。](media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
<span data-ttu-id="33ffc-p129">您还应选取的命名约定文件。下面是一些示例：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p129">You should also pick a naming convention your files. Here are some examples:</span></span>
  
- <span data-ttu-id="33ffc-245">Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal</span><span class="sxs-lookup"><span data-stu-id="33ffc-245">Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal</span></span>
    
- <span data-ttu-id="33ffc-246">Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW</span><span class="sxs-lookup"><span data-stu-id="33ffc-246">Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW</span></span>
    
- <span data-ttu-id="33ffc-247">Feb_08_2015_2pmEST_PerfBaseline_BADPerf</span><span class="sxs-lookup"><span data-stu-id="33ffc-247">Feb_08_2015_2pmEST_PerfBaseline_BADPerf</span></span>
    
- <span data-ttu-id="33ffc-248">Feb_08_2015_8 30amEST_PerfBaseline_GoodPerf</span><span class="sxs-lookup"><span data-stu-id="33ffc-248">Feb_08_2015_8-30amEST_PerfBaseline_GoodPerf</span></span>
    
<span data-ttu-id="33ffc-p130">有许多不同的方式来执行此操作，但使用格式**\<dateTime\>\<在测试中发生了什么情况\>** 是启动的好地方。正在认真地这有助于大量您尝试解决问题的更高版本。更高版本，您将能够说"我发生两个跟踪年 2 月第 8 上, 一个显示的良好的性能和一个显示错误，以便我们比较"。这是非常有用故障排除。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p130">There are lots of different ways to do this, but using the format **\<dateTime\>\<what's happening in the test\>** is a good place to start. Being diligent about this will help a lot when you are trying to troubleshoot issues later. Later, you'll be able to say "I took two traces on February 8th, one showed good performance and one showed bad, so we can compare them". This is extremely helpful for troubleshooting.</span></span> 
  
<span data-ttu-id="33ffc-p131">您需要有序的方式，以保留您历史的基线。本示例中，简单方法生成三个命令行输出和结果收集为屏幕截图，但改为您可以使用网络捕获文件。使用最适合您的方法。存储您历史比较基准和引用这些时刻其中您注意到联机服务的行为发生变化。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p131">You need to have an organized way to keep your historical baselines. In this example, the simple methods produced three command line outputs and the results were collected as screen shots, but you may have network capture files instead. Use the method that works best for you. Store your historical baselines and refer to them at points where you notice changes in the behavior of online services.</span></span> 
  
## <a name="why-collect-performance-data-during-a-pilot"></a><span data-ttu-id="33ffc-257">为什么在试生产期间收集性能数据？</span><span class="sxs-lookup"><span data-stu-id="33ffc-257">Why collect performance data during a pilot?</span></span>

<span data-ttu-id="33ffc-p132">没有更好的时间，以开始进行过程中的 Office 365 服务试验比的比较基准。办公室可能有成千上万个用户、 数百千位，也可能有五，但通过少量的用户，甚至可以执行测试以测量波动的性能。对于大型公司代表性的试验 Office 365 的成百上千个用户可以进行预估向外到数千以便您知道之前正好可能出现问题。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p132">There is no better time to start making baselines than during a pilot of the Office 365 service. Your office may have thousands of users, hundreds of thousands, or it may have five, but even with a small number of users, you can perform tests to measure fluctuations in performance. In the case of a large company, a representative sample of several hundred users piloting Office 365 can be projected outward to several thousands so you know where issues might arise before they happen.</span></span>
  
<span data-ttu-id="33ffc-p133">对于其中的白板意味着所有用户在同一时间都转到服务并没有任何试点，某小公司保留性能度量值，以便您能向可能需要解决错误执行操作的任何人显示的数据。例如，如果您注意突然之间可以遍历周围花费的时间上载中型图形它使用很快发生在您构建。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p133">In the case of a small company, where on-boarding means that all users go to the service at the same time and there is no pilot, keep performance measures so that you have data to show to anyone who may have to troubleshoot a badly performing operation. For example, if you notice that all of a sudden you can walk around your building in the time it takes to upload a medium-sized graphic where it used to happen very quickly.</span></span>
  
## <a name="how-to-collect-baselines"></a><span data-ttu-id="33ffc-263">如何收集比较基准</span><span class="sxs-lookup"><span data-stu-id="33ffc-263">How to collect baselines</span></span>

<span data-ttu-id="33ffc-264">对于所有疑难解答计划您需要确定至少以下事项：</span><span class="sxs-lookup"><span data-stu-id="33ffc-264">For all troubleshooting plans you need to identify these things at a minimum:</span></span>
  
- <span data-ttu-id="33ffc-265">客户端计算机正在使用 （的计算机或设备、 IP 地址和导致问题的操作的类型）</span><span class="sxs-lookup"><span data-stu-id="33ffc-265">The client computer you're using (the type of computer or device, an IP address, and the actions that caused the issue)</span></span>
    
- <span data-ttu-id="33ffc-266">客户端计算机位于世界上的位置 (例如，是否在到网络，在远程工作 VPN 或公司 intranet 上此用户)</span><span class="sxs-lookup"><span data-stu-id="33ffc-266">Where the client computer is located in the world (for example, whether this user on a VPN to the network, working remotely, or on the company intranet)</span></span>
    
- <span data-ttu-id="33ffc-267">出口点客户端计算机使用从您的网络 （通信 ISP 或 Internet 离开业务点）</span><span class="sxs-lookup"><span data-stu-id="33ffc-267">The egress point the client computer uses from your network (the point at which traffic leaves your business for an ISP or the Internet)</span></span>
    
 <span data-ttu-id="33ffc-p134">可以从网络管理员了解您的网络的布局。如果您是小型网络上，看看您连接到 Internet 的设备和呼叫您的 isp 联系，如果您有任何疑问布局。创建供您参考最终布局的图形。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p134">You can find out the layout of your network from the network administrator. If you're on a small network, take a look at the devices connecting you to the Internet, and call your ISP if you have questions about the layout. Create a graphic of the final layout for your reference.</span></span> 
  
<span data-ttu-id="33ffc-p135">此部分分为简单命令行工具和方法，并更多高级工具选项。我们将首先介绍简单的方法。但是，如果您立即有性能问题，您应该跳转到高级方法并试用示例性能疑难解答行动计划。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p135">This section is broken into simple command-line tools and methods, and more advanced tools options. We'll cover simple methods first. But if you've got a performance problem right now, you should jump to advanced methods and try out the sample performance-troubleshooting action plan.</span></span>
  
### <a name="simple-methods"></a><span data-ttu-id="33ffc-274">简单的方法</span><span class="sxs-lookup"><span data-stu-id="33ffc-274">Simple methods</span></span>

<span data-ttu-id="33ffc-p136">这些简单的方法的目标是了解如何执行、 了解和正确简单性能基准存储随着时间的推移，这样会通知有关 Office 365 性能。下面是非常简单的简单图表，如如上所示：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p136">The objective of these simple methods is to learn to take, understand, and properly store simple performance baselines over time so that you are informed about Office 365 performance. Here's the very simple diagram for simple, as you've seen before:</span></span>
  
![与客户端、 代理和云和工具建议 PSPing，TraceTCP，基本网络和网络跟踪。](media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> <span data-ttu-id="33ffc-p137">此屏幕截图显示，以毫秒为单位，长请求所需过程，以及多少网络跃点数或连接到下一步，一台计算机从请求到达目标所需的有用工具，因为它包含 TraceTCP。TraceTCP 还可以使用期间对 Microsoft Office 365 疑难解答支持是非常有用的跃点服务器的名称。> TraceTCP 命令可以非常简单，如： > `tracetcp.exe outlook.office365.com:443`> 命令中包括端口号，请务必 ！> [TraceTCP](https://simulatedsimian.github.io/tracetcp.mdl)免费下载，但依赖于 Wincap。Wincap 是一个工具，还使用并安装 Netmon。我们还高级的方法一节中使用网络监视器。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p137">TraceTCP is included in this screen shot because it's a useful tool for showing, in milliseconds, how long a request takes to process, and how many network hops, or connections from one computer to the next, that the request takes to reach a destination. TraceTCP can also give the names of servers used during hops, which can be useful to a Microsoft Office 365 troubleshooter in Support. > TraceTCP commands can be very simple, such as: >  `tracetcp.exe outlook.office365.com:443`> Remember to include the port number in the command! > [TraceTCP](https://simulatedsimian.github.io/tracetcp.mdl) is a free download, but relies on Wincap. Wincap is a tool that is also used and installed by Netmon. We also use Netmon in the advanced methods section.</span></span> 
  
 <span data-ttu-id="33ffc-p138">如果您有多个办公室，您需要从客户端中每个位置以及保留的一组数据。此测试测量延迟，即，在这种情况下，介绍将请求发送到 Office 365 和 Office 365 响应请求的客户端之间的时间量的数值。测试您的域的客户端计算机上，在发起和查找衡量往返行程从内部网络，通过出口点，在到 Office 365 Internet 和备份。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p138">If you have multiple offices, you'll need to keep a set of data from a client in each of those locations as well. This test measures latency, which, in this case, is a number value that describes the amount of time between a client sending a request to Office 365, and Office 365 responding to the request. The testing originates inside your domain on a client computer, and looks to measure a round trip from inside your network, out through an egress point, across the Internet to Office 365, and back.</span></span> 
  
<span data-ttu-id="33ffc-p139">有几种方法处理出口点，在这种情况下，代理服务器。您可以跟踪介于 1 到 2 和然后 2 到 3，然后数字相加 （毫秒） 获取到边缘的网络，最后一个总计。或者，您可以配置要绕过 Office 365 地址的代理服务器的连接。在较大的网络防火墙、 反向代理或两者的一些组合，您可能需要将允许通信大量的 Url 为传递代理服务器上创建的例外。Office 365 使用的终结点列表中，请参阅[Office 365 Url 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)。如果您有身份验证的代理，首先测试以下例外：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p139">There are a few ways to deal with the egress point, in this case, the proxy server. You can either trace from 1 to 2 and then 2 to 3, and then add the numbers in milliseconds to get a final total to the edge of your network. Or, you can configure the connection to bypass the proxy for Office 365 addresses. In a larger network with a firewall, reverse proxy, or some combination of the two, you may need to make exceptions on the proxy server that will allow traffic to pass for a lot of URLs. For the list of endpoints used by Office 365, see [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). If you have an authenticating proxy, begin by testing exceptions for the following:</span></span>
  
- <span data-ttu-id="33ffc-293">端口 80 和 443</span><span class="sxs-lookup"><span data-stu-id="33ffc-293">Ports 80 and 443</span></span>
    
- <span data-ttu-id="33ffc-294">TCP 和 HTTPs</span><span class="sxs-lookup"><span data-stu-id="33ffc-294">TCP and HTTPs</span></span>
    
- <span data-ttu-id="33ffc-295">对任何这些 Url 出站连接：</span><span class="sxs-lookup"><span data-stu-id="33ffc-295">Connections that are outbound to any of these URLs:</span></span>
    
- <span data-ttu-id="33ffc-296">\*。 microsoftonline.com</span><span class="sxs-lookup"><span data-stu-id="33ffc-296">\*.microsoftonline.com</span></span>
    
- <span data-ttu-id="33ffc-297">\*.microsoftonline p.com</span><span class="sxs-lookup"><span data-stu-id="33ffc-297">\*.microsoftonline-p.com</span></span>
    
- <span data-ttu-id="33ffc-298">\*。 sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="33ffc-298">\*.sharepoint.com</span></span>
    
- <span data-ttu-id="33ffc-299">\*。 outlook.com</span><span class="sxs-lookup"><span data-stu-id="33ffc-299">\*.outlook.com</span></span>
    
- <span data-ttu-id="33ffc-300">\*。 lync.com</span><span class="sxs-lookup"><span data-stu-id="33ffc-300">\*.lync.com</span></span>
    
- <span data-ttu-id="33ffc-301">osub.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="33ffc-301">osub.microsoft.com</span></span>
    
<span data-ttu-id="33ffc-p140">所有用户都都要允许访问这些地址没有任何代理干扰或身份验证。在较小的网络中，您应添加到您的代理服务器绕过在 web 浏览器中的列表。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p140">All users need to be allowed to get to these addresses without any proxy interference or authentication. On a smaller network, you should add these to your proxy bypass list in your web browser.</span></span> 
  
<span data-ttu-id="33ffc-p141">若要添加到代理绕过列表这些在 Internet Explorer 中，转到**工具** \> **Internet 选项** \> **连接** \> **LAN 设置** \> **高级**。高级选项卡也是，您将在其中找到您的代理服务器和代理服务器的端口。您可能需要单击**使用代理服务器用于 LAN**，访问**高级**按钮复选框。您需要确保已**对本地地址绕过代理服务器**。之后单击**高级**，将会看到一个文本框，其中可以输入例外。分隔上面列出使用分号分隔，例如通配符 Url:</span><span class="sxs-lookup"><span data-stu-id="33ffc-p141">To add these to your proxy bypass list in Internet Explorer, go to **Tools** \> **Internet Options** \> **Connections** \> **LAN settings** \> **Advanced**. The advanced tab is also where you will find your proxy server and proxy server port. You may need to click the checkbox **Use a proxy server for your LAN**, to access the **Advanced** button. You'll want to make sure that **Bypass proxy server for local addresses** is checked. Once you click **Advanced**, you'll see a text box where you can enter exceptions. Separate the wildcard URLs listed above with semi-colons, for example:</span></span>
  
<span data-ttu-id="33ffc-310">\*。 microsoftonline.com;\*。 sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="33ffc-310">\*.microsoftonline.com; \*.sharepoint.com</span></span>
  
<span data-ttu-id="33ffc-p142">一旦您绕过您的代理服务器，您应该能够直接在 Office 365 URL 上使用 ping 或 PsPing。下一步将测试 ping **outlook.office365.com**。或者，如果您使用 PsPing 或其他工具，将会让您提供端口号，在命令中针对**portal.microsoftonline.com:443** PsPing 以查看以毫秒为单位的平均来回行程时间。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p142">Once you bypass your proxy, you should be able to use ping or PsPing directly on an Office 365 URL. The next step will be to test ping **outlook.office365.com**. Or, if you're using PsPing or another tool that will let you supply a port number to the command, PsPing against **portal.microsoftonline.com:443** to see the average round trip time in milliseconds.</span></span> 
  
<span data-ttu-id="33ffc-p143">来回行程的时间或 RTT，度量计到像 outlook.office365.com 服务器发送 HTTP 请求和获取发回认可服务器知道您这样做的响应时间长度为数值。有时，您将看到此缩写为 RTT。这应该是时间的相对较短量。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p143">The round trip time, or RTT, is a number value that measures how long it takes to send a HTTP request to a server like outlook.office365.com and get a response back that acknowledges the server knows that you did it. You'll sometimes see this abbreviated as RTT. This should be a relatively short amount of time.</span></span>
  
<span data-ttu-id="33ffc-317">您必须使用[PSPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx)或不使用被阻止 Office 365 才能执行此测试的 ICMP 数据包的其他工具。</span><span class="sxs-lookup"><span data-stu-id="33ffc-317">You have to use [PSPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) or another tool that does not use ICMP packets which are blocked by Office 365 in order to do this test.</span></span> 
  
 <span data-ttu-id="33ffc-318">**如何使用 PsPing 来获得的总体直接从 Office 365 URL 往返时间 （毫秒）**</span><span class="sxs-lookup"><span data-stu-id="33ffc-318">**How to use PsPing to get an overall round trip time in milliseconds directly from an Office 365 URL**</span></span>
  
1. <span data-ttu-id="33ffc-319">提升的命令提示符处运行通过完成下列步骤：</span><span class="sxs-lookup"><span data-stu-id="33ffc-319">Run an elevated command prompt by completing these steps:</span></span>
    
1. <span data-ttu-id="33ffc-320">单击**启动**。</span><span class="sxs-lookup"><span data-stu-id="33ffc-320">Click **Start**.</span></span>
    
2. <span data-ttu-id="33ffc-321">在**开始搜索**框中，键入 cmd，然后按 CTRL + SHIFT + ENTER。</span><span class="sxs-lookup"><span data-stu-id="33ffc-321">In the **Start Search** box, type cmd, and then press CTRL+SHIFT+ENTER.</span></span>
    
3. <span data-ttu-id="33ffc-322">如果出现“**用户帐户控制**”对话框，请确认所显示的是您想要执行的操作，然后单击“**继续**”。</span><span class="sxs-lookup"><span data-stu-id="33ffc-322">If the **User Account Control** dialog box appears, confirm that the action it displays is what you want, and then click **Continue**.</span></span>
    
2. <span data-ttu-id="33ffc-323">导航到安装 （在此案例 PsPing) 的工具的文件夹，并测试这些 Office 365 Url:</span><span class="sxs-lookup"><span data-stu-id="33ffc-323">Navigate to the folder where the tool (in this case PsPing) is installed and test these Office 365 URLs:</span></span>
    
  - <span data-ttu-id="33ffc-324">psping portal.office.com:443</span><span class="sxs-lookup"><span data-stu-id="33ffc-324">psping portal.office.com:443</span></span>
    
  - <span data-ttu-id="33ffc-325">psping microsoft my.sharepoint.com:443</span><span class="sxs-lookup"><span data-stu-id="33ffc-325">psping microsoft-my.sharepoint.com:443</span></span>
    
  - <span data-ttu-id="33ffc-326">psping outlook.office365.com:443</span><span class="sxs-lookup"><span data-stu-id="33ffc-326">psping outlook.office365.com:443</span></span>
    
  - <span data-ttu-id="33ffc-327">psping www.yammer.com:443</span><span class="sxs-lookup"><span data-stu-id="33ffc-327">psping www.yammer.com:443</span></span>
    
    ![转到 microsoft my.sharepoint.com 端口 443 PSPing 命令。](media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
<span data-ttu-id="33ffc-p144">请务必包括 443 的端口号。请记住，Office 365 处理加密通道。如果您的端口号不 PsPing 您的请求将失败。一旦您已 ping 操作您简短的列表中，查找毫秒 (ms) 的平均时间。这是您想要记录 ！</span><span class="sxs-lookup"><span data-stu-id="33ffc-p144">Be sure to include the port number of 443. Remember that Office 365 works on an encrypted channel. If you PsPing without the port number, your request will fail. Once you've pinged your short list, look for the Average time in milliseconds (ms). That is what you want to record!</span></span>
  
![图形显示举例说明了客户端到代理 PSPing 的 2.8 毫秒来回行程时间。](media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
<span data-ttu-id="33ffc-p145">如果您不熟悉绕过代理服务器，并希望执行分步操作，您需要先了解您的代理服务器的名称。在 Internet Explorer 转到**工具** \> **Internet 选项** \> **连接** \> **LAN 设置** \> **高级**。**高级**选项卡是，您将看到您列出的代理服务器。通过完成此任务的 ping 命令提示符处的代理服务器：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p145">If you're not familiar with proxy bypass, and prefer to take things step-by-step, you need to first find out the name of your proxy server. In Internet Explorer go to **Tools** \> **Internet Options** \> **Connections** \> **LAN settings** \> **Advanced**. The **Advanced** tab is where you will see your proxy server listed. Ping that proxy server at a command prompt by completing this task:</span></span> 
  
 <span data-ttu-id="33ffc-339">**要 ping 代理服务器并获取阶段 1 到 2 毫秒来回行程值**</span><span class="sxs-lookup"><span data-stu-id="33ffc-339">**To ping the proxy server and get a round trip value in milliseconds for stage 1 to 2**</span></span>
  
1. <span data-ttu-id="33ffc-340">提升的命令提示符处运行通过完成下列步骤：</span><span class="sxs-lookup"><span data-stu-id="33ffc-340">Run an elevated command prompt by completing these steps:</span></span>
    
1. <span data-ttu-id="33ffc-341">单击**启动**。</span><span class="sxs-lookup"><span data-stu-id="33ffc-341">Click **Start**.</span></span>
    
2. <span data-ttu-id="33ffc-342">在**开始搜索**框中，键入 cmd，然后按 CTRL + SHIFT + ENTER。</span><span class="sxs-lookup"><span data-stu-id="33ffc-342">In the **Start Search** box, type cmd, and then press CTRL+SHIFT+ENTER.</span></span>
    
3. <span data-ttu-id="33ffc-343">如果出现“**用户帐户控制**”对话框，请确认所显示的是您想要执行的操作，然后单击“**继续**”。</span><span class="sxs-lookup"><span data-stu-id="33ffc-343">If the **User Account Control** dialog box appears, confirm that the action it displays is what you want, and then click **Continue**.</span></span>
    
2. <span data-ttu-id="33ffc-p146">键入 ping\<的代理服务器名称您的浏览器使用或代理服务器的 IP 地址\>，然后按 ENTER。如果您有 PsPing 或其他工具，安装，您可以选择改为使用该工具。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p146">Type ping \<the name of the proxy server your browser uses, or the IP address of the proxy server\> and then press ENTER. If you have PsPing, or some other tool, installed, you can choose to use that tool instead.</span></span> 
    
    <span data-ttu-id="33ffc-346">您的命令可能类似于任何这些示例：</span><span class="sxs-lookup"><span data-stu-id="33ffc-346">Your command may look like any of these examples:</span></span> 
    
  - <span data-ttu-id="33ffc-347">ping ourproxy.ourdomain.industry.business.com</span><span class="sxs-lookup"><span data-stu-id="33ffc-347">ping ourproxy.ourdomain.industry.business.com</span></span>
    
  - <span data-ttu-id="33ffc-348">ping 155.55.121.55</span><span class="sxs-lookup"><span data-stu-id="33ffc-348">ping 155.55.121.55</span></span>
    
  - <span data-ttu-id="33ffc-349">ping ourproxy</span><span class="sxs-lookup"><span data-stu-id="33ffc-349">ping ourproxy</span></span>
    
  - <span data-ttu-id="33ffc-350">psping ourproxy.ourdomain.industry.business.com:80</span><span class="sxs-lookup"><span data-stu-id="33ffc-350">psping ourproxy.ourdomain.industry.business.com:80</span></span>
    
  - <span data-ttu-id="33ffc-351">psping 155.55.121.55:80</span><span class="sxs-lookup"><span data-stu-id="33ffc-351">psping 155.55.121.55:80</span></span>
    
  - <span data-ttu-id="33ffc-352">psping ourproxy:80</span><span class="sxs-lookup"><span data-stu-id="33ffc-352">psping ourproxy:80</span></span>
    
3. <span data-ttu-id="33ffc-p147">当跟踪停止发送测试数据包时，您将获取小型摘要列出平均，以毫秒为单位，并且您后的值。执行提示符处的屏幕截图并保存它使用您的命名约定。此时它还可以帮助来填充的值图表中。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p147">When the trace stops sending test packets, you'll get a small summary that lists an average, in milliseconds, and that's the value you're after. Take a screen shot of the prompt and save it using your naming convention. At this point it may also help to fill in the diagram with the value.</span></span>
    
<span data-ttu-id="33ffc-p148">也许您已在早期上午，带跟踪和您的客户端可以快速获取到代理服务器 （或任何出口服务器退出到 Internet）。在这种情况下，您的号码可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p148">Maybe you've taken a trace in the early morning, and your client can get to the proxy (or whatever egress server exits to the Internet) quickly. In this case, your numbers may look like this:</span></span>
  
![图形显示来回行程的时间从客户端向 2.8 毫秒的代理。](media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
<span data-ttu-id="33ffc-p149">如果您的客户端计算机是有权访问代理服务器 （或出口） 服务器选择几之一，您可以运行测试的下一步线路进行远程连接到该计算机上，从该处到 Office 365 URL PsPing 运行命令提示符处。如果您没有访问该计算机，您可以与您的网络资源联系以帮助与下一个线路和获取准确数字这样。如果这是不可能，将针对 Office 365 URL PsPing 有问题，并比较为针对您的代理服务器 PsPing 或 Ping 时间。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p149">If your client computer is one of the select few with access to the proxy (or egress) server, you can run the next leg of the test by remotely connecting to that computer, running the command prompt to PsPing to an Office 365 URL from there. If you don't have access to that computer, you can contact your network resources for help with the next leg and get exact numbers that way. If that's not possible, take a PsPing against the Office 365 URL in question and compare it to the PsPing or Ping time against your proxy server.</span></span> 
  
<span data-ttu-id="33ffc-p150">例如，如果您拥有 51.84 毫秒从客户端到 Office 365 URL，并且必须从客户端到的代理服务器 （或出口点） 的 2.8 毫秒，则可以从出口到 Office 365 的 49.04 毫秒。同样，如果必须从客户端到代理的 12.25 毫秒 PsPing 期间 62.01 毫秒从客户端与 Office 365 URL 和日的高度，与 Office 365 URL 代理出口您平均值将为 49.76 毫秒。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p150">For example, if you have 51.84 milliseconds from the client to the Office 365 URL, and you have 2.8 milliseconds from the client to the proxy (or egress point), then you have 49.04 milliseconds from the egress to Office 365. Likewise, if you have a PsPing of 12.25 milliseconds from the client to the proxy during the height of the day, and 62.01 milliseconds from the client to the Office 365 URL, then your average value for the proxy egress to the Office 365 URL is 49.76 milliseconds.</span></span>
  
![显示 ping 以毫秒为单位从客户端到代理服务器到 Office 365 的客户端旁边以便可以中减去值的其他图形。](media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
<span data-ttu-id="33ffc-p151">方面疑难解答，您可能会发现只从保留这些基线的有趣。例如，如果您发现您通常必须有关则 40 到 59 毫秒延迟从代理或出口将指向 Office 365 URL 和具有代理或出口点延迟大约 3 到 7 毫秒的客户端 (具体取决于量网络流量您正在 seein一天中的这段时间内 g) 然后您肯定会知道内容有问题，如果您与代理或出口基线的最后三个客户端显示的 45 毫秒延迟。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p151">In terms of troubleshooting, you may find something interesting just from keeping these baselines. For example, if you find that you generally have about 40 to 59 milliseconds of latency from the proxy or egress point to the Office 365 URL, and have a client to proxy or egress point latency of about 3 to 7 milliseconds (depending on the amount network traffic you're seeing during that time of day) then you will surely know something is problematic if your last three client to proxy or egress baselines show a latency of 45 milliseconds.</span></span>
  
### <a name="advanced-methods"></a><span data-ttu-id="33ffc-367">高级的方法</span><span class="sxs-lookup"><span data-stu-id="33ffc-367">Advanced methods</span></span>

<span data-ttu-id="33ffc-p152">如果您确实要了解到 Office 365 的最新动态 Internet 请求，您需要熟悉网络跟踪。无关紧要您想用于这些跟踪，HTTPWatch、 Netmon、 消息分析器、 Wireshark、 Fiddler，开发人员仪表板工具哪些工具或任何其他将执行操作，只要该工具可以捕获和筛选网络流量。您将看到此部分中，最好运行多个之一以获取问题的更完整地了解这些工具。当您测试时，这些工具的一些将还充当自身的代理。[性能疑难解答规划 Office 365](performance-troubleshooting-plan.md)的姐妹篇文章中使用的工具包括[Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865)、 [HTTPWatch](https://www.httpwatch.com/download/)或[WireShark](https://www.wireshark.org/)。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p152">If you really want to know what is happening with your Internet requests to Office 365, you need to become familiar with network traces. It does not matter which tools you prefer for these traces, HTTPWatch, Netmon, Message Analyzer, Wireshark, Fiddler, Developer Dashboard tool or any other will do as long as that tool can capture and filter network traffic. You'll see in this section that it's beneficial to run more than one of these tools to get a more complete picture of the problem. When you're testing, some of these tools also act as proxies in their own right. Tools used in the companion article, [Performance troubleshooting plan for Office 365](performance-troubleshooting-plan.md), include [Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/), or [WireShark](https://www.wireshark.org/).</span></span>
  
<span data-ttu-id="33ffc-p153">作为性能基准是此方法中，简单一部分并且的许多步骤相同时解决性能问题。创建性能的比较基准的更高级的方法，需要执行和存储网络跟踪。大部分本文中的示例使用 SharePoint Online，但您应跨 Office 365 服务订阅测试和记录开发常见操作的列表。下面是一个比较基准示例：</span><span class="sxs-lookup"><span data-stu-id="33ffc-p153">Taking a performance baseline is the simple part of this method, and many of the steps are the same as when you troubleshoot a performance issue. The more advanced methods of creating baselines for performance requires you to take and store network traces. Most of the examples in this article use SharePoint Online, but you should develop a list of common actions across the Office 365 services to which you subscribe to test and record. Here is a baseline example:</span></span>
  
- <span data-ttu-id="33ffc-p154">比较基准列表 SPO-* * 步骤 1: * * 浏览主页 SPO 网站和执行网络跟踪。保存跟踪。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p154">Baseline list for SPO - ** Step 1: ** Browse the home page of the SPO website and do a network trace. Save the trace.</span></span> 
    
- <span data-ttu-id="33ffc-p155">比较基准列表 SPO-**步骤 2:** 搜索术语 （例如您的公司名称） 通过企业级搜索和执行网络跟踪。保存跟踪。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p155">Baseline list for SPO - **Step 2:** Search for a term (such as your company name) via Enterprise Search and do a network trace. Save the trace.</span></span> 
    
- <span data-ttu-id="33ffc-p156">比较基准列表 SPO-**步骤 3:** 上载到 SharePoint Online 的文档库和执行网络跟踪的大型文件。保存跟踪。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p156">Baseline list for SPO - **Step 3:** Upload a large file to a SharePoint Online document library and do a network trace. Save the trace.</span></span> 
    
- <span data-ttu-id="33ffc-p157">比较基准列表 SPO-**步骤 4:** 浏览主页 OneDrive 网站和执行网络跟踪。保存跟踪。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p157">Baseline list for SPO - **Step 4:** Browse the home page of the OneDrive website and do a network trace. Save the trace.</span></span> 
    
<span data-ttu-id="33ffc-p158">此列表应包括针对 SharePoint Online 执行用户的最重要的常见操作。请注意，最后一步，转到 OneDrive for Business，跟踪生成-中的业务主页上，很少自定义 SharePoint Online 主页 （这通常由自定义公司） 的负载之间 OneDrive 比较。当谈到慢加载 SharePoint Online 网站，这是一个非常基本测试。您可以测试生成此差异的记录。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p158">This list should include the most important common actions that users take against SharePoint Online. Notice that the last step, to trace going to OneDrive for Business, builds-in a comparison between the load of the SharePoint Online home page (which is often customized by companies) and OneDrive for Business home page, which is seldom customized. This is a very basic test when it comes to a slow-loading SharePoint Online site. You can build a record of this difference into your testing.</span></span>
  
<span data-ttu-id="33ffc-p159">如果您是中间性能问题的许多步骤是相同时作为基准。网络跟踪成为关键，因此我们*如何*才能重要跟踪下一步将处理一样。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p159">If you are in the middle of a performance problem, many of the steps are the same as when taking a baseline. Network traces become critical, so we'll handle  *how*  to take the important traces next.</span></span> 
  
<span data-ttu-id="33ffc-p160">若要解决性能问题，*现在*，您需要遇到性能问题时需要跟踪。您需要具备可用于收集日志，正确的工具和所需的操作计划，即的故障排除要收集最有用的信息，您可以执行的操作列表。首先要做为记录的日期和时间的测试，以使这些文件可以保存在反映计时的文件夹。接下来，缩小到自己的问题步骤。这些是用于测试的具体步骤。不要忘记基础知识： 如果仅使用 Outlook 有问题，请确保只有一个 Office 365 服务中出现的问题行为的记录。关闭此问题的范围将缩小将帮助您重点关注内容可以解析。</span><span class="sxs-lookup"><span data-stu-id="33ffc-p160">To tackle a performance problem,  *right now*  , you need to be taking a trace at the time you are experiencing the performance issue. You need to have the proper tools available to gather logs, and you need an action plan, that is, a list of troubleshooting actions to take to gather the best information that you can. The first thing to do is record the date and time of the test so that the files can be saved in a folder that reflect the timing. Next, narrow down to the problem steps themselves. These are the exact steps you will use for testing. Don't forget the basics: if the issue is only with Outlook, make sure to record that the problem behavior happens in only one Office 365 service. Narrowing down the scope of this issue will help you to focus on something you can resolve.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="33ffc-398">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33ffc-398">See also</span></span>

[<span data-ttu-id="33ffc-399">管理 Office 365 终结点</span><span class="sxs-lookup"><span data-stu-id="33ffc-399">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

