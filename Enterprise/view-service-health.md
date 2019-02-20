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
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: 在呼叫支持之前查看 Office 365 服务的运行状况状态, 以查看是否有活动的服务中断
ms.openlocfilehash: 7a8d6c028caa72d332a51123233b2d0642311da0
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085291"
---
# <a name="how-to-check-office-365-service-health"></a>如何查看 Office 365 服务运行状况

您可以在管理中心的 "office 365**服务运行状况**" 页上查看 office 365、Yammer、microsoft Dynamics CRM 和 microsoft Intune 云服务的运行状况。如果您在云服务中遇到问题, 则可以检查服务运行状况, 以确定这是否是在致电支持或花时间故障排除之前进行的解决方案中存在的已知问题。 

如果无法登录到服务门户, 则可以使用 "[服务状态" 页](https://status.office365.com)来检查阻止你登录租户的已知问题。
  
### <a name="how-to-check-service-health"></a>如何查看服务运行状况

1. 转到 [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) 并使用管理员帐户登录。 
    
    > [!NOTE]
    > 分配为全局管理员或服务管理员角色的人员可以查看服务运行状况。若要允许 Exchange、SharePoint 和 Skype for Business 管理员查看服务运行状况，必须向他们分配服务管理员角色。
  
2. 若要打开服务运行状况, 请在管理中心中, 转到**运行状况** > **服务运行状况**, 或单击**主页仪表板**上的**服务运行状况卡片**。仪表板卡片指示是否存在活动的服务问题, 以及指向详细服务运行状况页面的链接。
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. 每个云服务的运行状态均以表格格式显示，其中包含指示可能状态的图标。
    
> [!TIP]
> 你也可以在移动设备上使用 [Office 365 Admin 应用](https://go.microsoft.com/fwlink/p/?linkid=627216)查看服务运行状况，这是一种通过推送通知随时获取最新消息的好方法。 
  
### <a name="view-details-of-posted-service-health"></a>查看已发布服务的运行状况详细信息

在默认视图中, 将显示所有服务及其当前运行状况状态。若要将视图筛选为当前遇到事件的服务, 请从左侧的阴影条中选择 "**事件**"。选择 "**建议**" 将仅显示当前已发布建议的服务。从 "**所有服务**" 视图中, 单击显示的服务状态将打开公告或事件的摘要视图。 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
公告或事件摘要提供以下信息： 
  
![标记服务公告中的字段的屏幕截图](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. 该问题的问题标识符和摘要语句。
    
2. 当前状态。请参阅本文中的状态定义，获取每种潜在状态的说明。
    
3. 关于此问题如何影响用户的说明。
    
4. 该问题发生的时间以及上一次更新服务运行状况消息的时间。出现问题期间，我们会经常发布消息，说明我们在应用解决方案时取得的进展。
    
5. 选择" **显示详细信息**"链接来查看有关该问题的更多详细信息，包括我们在开发解决方案时发布的所有消息的历史记录。 
    
### <a name="translate-service-health-details"></a>翻译服务运行状况详细信息

服务运行状况说明是实时发布的，因此这些说明不会自动翻译成你的语言，并且服务事件的详细信息仅以英语形式提供。若要翻译这些说明，请遵循以下步骤：
  
1. 转到[翻译工具](https://www.bing.com/translator/)。
    
2. 在" **服务运行状况**"页上，选择一个事件或公告。在" **显示详细信息**"下，复制关于该问题的文本。
    
3. 在"翻译工具"中，粘贴文本，然后选择" **翻译**"。
    
### <a name="definitions"></a>定义

在大多数情况下，服务正常运行且没有进一步的信息。服务出现问题时，该问题会标识为公告或事件，并显示当前状态。
  
> [!TIP]
> 服务运行状况中不会显示计划内维护事件。可以通过" **消息中心**"随时了解最新消息，从而跟踪计划内维护事件。筛选出分类为"更改计划"的消息，了解发生更改的时间、其影响以及如何做好相应准备。请参阅 [Office 365 中的消息中心](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093)获取更多详细信息。 
  
### <a name="incidents-and-advisories"></a>事件和公告

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|如果服务显示公告，这意味着某问题正在影响一些用户，但该服务仍然可用。公告中通常存在针对该问题的变通方法，并且该问题可能是间歇性的，或其作用范围和对用户的影响有限。  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|如果服务显示遇到活动事件，则说明遇到关键问题，且服务或其主要功能目前不可用。例如，用户可能无法发送和接收电子邮件，或无法登录。事件会对用户产生显著影响。对于正在进行的事件，我们会在服务运行状况仪表板中提供有关调查、缓解措施和解决方法确认的更新。  <br/> |
   
### <a name="status-definitions"></a>状态定义

|**状态**|**定义**|
|:-----|:-----|
|**正在调查** | 我们已发现存在潜在问题，我们正在收集有关情况和影响范围的详细信息。 |
|**服务降级** | 我们已确认存在可能影响服务或功能使用的问题。例如，如果服务的执行速度比平常慢、存在间歇性中断或某功能运行不正常，则可能看到此状态。 |
|**服务中断** | 如果我们确定某问题影响用户访问服务的能力，则你将看到此状态。在本例中，问题十分重大且可持续重现。 |
|**正在还原服务** | 我们已确定问题成因，知晓需要采取的纠正措施，并正在将服务恢复到正常状态。 |
|**延期恢复** | 此状态表示正在执行纠正措施，为大多数用户恢复服务，但恢复所有受影响的系统仍需一些时间。如果我们为了减轻影响，而在实施永久解决措施前实施临时措施，你也可能看到此状态。 |
|**调查暂停** | 如果对潜在问题的详细调查需要请求客户提供其他信息，以便进行进一步的调查，则你将看到此状态。如果我们需要你的参与，我们会告知你所需的数据或日志。 |
|**已还原服务** | 我们确认纠正措施已解决基础问题，且服务已还原到正常状态。若要了解出了什么问题，请查看问题详细信息。 |
|**已发布事件后报告** | 我们已发布了一个针对特定问题的公告事件报告, 其中包括根本原因信息和后续步骤, 以确保不会发生类似的问题。 |
   
## <a name="history"></a>“历史记录”

服务运行状况允许你查看当前运行状况状态, 并查看在过去30天内受影响的租户的任何服务通知和事件的历史记录。若要查看所有服务的过去运行状况, 请选择 "**服务运行状况**" 页上的 "**查看历史记录**"。 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
显示在选定时间范围内发布的所有服务运行状况消息的列表，如下所示：
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
您可以查看最近7天或最近30天的运行状况历史记录。选择任意行以查看有关该问题的更多详细信息。
  
有关我们对运行时间的承诺的详细信息, 请参阅[Office 365 中的透明操作](https://go.microsoft.com/fwlink/?linkid=848695)。
  
## <a name="leave-feedback"></a>提供反馈

我们的目标是确保向你及时、准确地提供仍在持续的问题的有用信息。若要告知我们采取的操作是否切实有效，请选择一个星级评分。给我们评出 1 - 5 星的分数后，你可以提供有关任何特定详细信息的反馈。我们将使用你的反馈微调服务运行状况系统。
  
![Feedback form for service health issues](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a>另请参阅

[Office 365 管理中心内的活动报表](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

