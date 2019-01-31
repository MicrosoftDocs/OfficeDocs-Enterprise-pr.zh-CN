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
ms.openlocfilehash: 7e04e1309c990ccced67663576285f7276603ccc
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651182"
---
# <a name="how-to-check-office-365-service-health"></a>如何查看 Office 365 服务运行状况

在管理中心中的 Office 365**服务运行状况**页上，您可以查看 Office 365、 Yammer、 Microsoft Dynamics CRM 和 Microsoft Intune 云服务的运行状况。如果遇到被云服务的问题，您可以检查服务运行状况，以确定是否正在解析的已知的问题之前呼叫支持或花时间进行故障排除。 

如果您不能登录到服务门户，您可以使用[服务状态页](https://status.office365.com)以检查阻止您登录到您的租户的已知问题。
  
### <a name="how-to-check-service-health"></a>如何查看服务运行状况

1. 转到 [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) 并使用管理员帐户登录。 
    
    > [!NOTE]
    > 分配为全局管理员或服务管理员角色的人员可以查看服务运行状况。若要允许 Exchange、SharePoint 和 Skype for Business 管理员查看服务运行状况，必须向他们分配服务管理员角色。
  
2. 若要打开在管理中心的服务运行状况，转到**运行状况** > **服务运行状况**，或单击**主页仪表板**上的**服务运行状况卡片**。仪表板卡片指示是否存在活动服务问题和详细的服务运行状况页面的链接。
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. 每个云服务的运行状态均以表格格式显示，其中包含指示可能状态的图标。
    
> [!TIP]
> 你也可以在移动设备上使用 [Office 365 Admin 应用](https://go.microsoft.com/fwlink/p/?linkid=627216)查看服务运行状况，这是一种通过推送通知随时获取最新消息的好方法。 
  
### <a name="view-details-of-posted-service-health"></a>查看已发布服务的运行状况详细信息

在默认视图中，将显示所有服务和及其当前运行状况状态。若要筛选视图服务当前遇到一个事件，请从左侧的灰色栏中选择**事件**。选择**通报**会显示当前具有安全公告发布的服务。从**的所有服务**视图中，单击显示的服务状态将打开 advisory 或事件的摘要视图。 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
公告或事件摘要提供以下信息： 
  
![标记服务通报中的字段的屏幕截图](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
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
|**发布后事件报告** | 我们已发布的特定问题包含根原因信息和下一步步骤，以确保类似问题不会再次发生 Post 事件报告。 |
   
## <a name="history"></a>“历史记录”

可通过服务运行状况查看当前运行状况状态，以及过去 30 天中任何服务公告和事件的历史记录。若要查看所有服务以往的运行状况，请在" **服务运行状况**"页上选择" **查看历史记录**"。 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
显示在选定时间范围内发布的所有服务运行状况消息的列表，如下所示：
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
最近 7 天或 30 天内，您可以查看运行状况历史记录。选择要查看有关该问题的更多详细信息任何行。
  
有关我们承诺正常运行时间的详细信息，请参阅[从 Office 365 的透明操作](https://go.microsoft.com/fwlink/?linkid=848695)。
  
## <a name="leave-feedback"></a>提供反馈

我们的目标是确保向你及时、准确地提供仍在持续的问题的有用信息。若要告知我们采取的操作是否切实有效，请选择一个星级评分。给我们评出 1 - 5 星的分数后，你可以提供有关任何特定详细信息的反馈。我们将使用你的反馈微调服务运行状况系统。
  
![Feedback form for service health issues](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a>另请参阅

[Office 365 管理中心内的活动报表](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

