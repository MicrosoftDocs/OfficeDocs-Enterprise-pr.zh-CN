---
title: 如何查看 Office 365 服务运行状况
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: 在调用支持之前查看 Office 365 服务的运行状况状态，以查看是否有活动的服务中断。
ms.openlocfilehash: 4dace633b4f68f3f9361096a4bd99296b8b807b2
ms.sourcegitcommit: 226989f5a6a252e67debf7613bf13aa679a43f92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "41721973"
---
# <a name="how-to-check-office-365-service-health"></a>如何查看 Office 365 服务运行状况

[![显示管理中心正在更改且你可在 aka.ms/aboutM365preview 找到更多详细信息的标签。](media/O365-Admin-AdminCenterChanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview?view=o365-worldwide)

您可以在[管理中心](https://go.microsoft.com/fwlink/p/?linkid=2024339)的 "Office 365**服务运行状况**" 页上查看 microsoft 服务的运行状况，包括 web 上的 Office、YAMMER、Microsoft Dynamics CRM 和 microsoft Intune 云服务。 If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.

如果无法登录到服务门户，则可以使用 "[服务状态" 页](https://status.office365.com)来检查阻止你登录租户的已知问题。
  
### <a name="how-to-check-service-health"></a>如何查看服务运行状况

1. 转到管理中心[https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339)，并使用管理员帐户登录。

    > [!NOTE]
    > 分配为全局管理员或服务管理员角色的人员可以查看服务运行状况。 若要允许 Exchange、SharePoint 和 Skype for Business 管理员查看服务运行状况，必须向他们分配服务管理员角色。 有关可查看服务运行状况的角色的详细信息，请参阅[关于管理员角色](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles?view=o365-worldwide#roles-available-in-the-microsoft-365-admin-center)。
  
2. 如果您没有使用新管理中心，请在主页上，选择右上角的 "**尝试新管理中心**" 切换。

3. 若要查看服务运行状况，请在 "管理中心" 中，转到 "**运行状况** > **服务运行状况**"，或选择 "**主页" 仪表板**上的**服务运行状况**卡片。 仪表板卡片指示是否存在活动的服务问题，以及指向详细**服务运行状况**页面的链接。
  
4. 在 "**服务运行状况**" 页上，将以表格格式显示每个云服务的运行状况状态。

   ![View of current issues in service health](media/service-health-all-services.png)

"**所有服务**" 选项卡（默认视图）显示所有服务及其当前运行状况状态。 图标和**状态**列指示每个服务的状态。 若要将视图筛选为当前遇到事件的服务，请选择页面顶部的 "**事件**" 选项卡。 选择 "**建议**" 选项卡将仅显示当前已发布建议的服务。 "**历史记录**" 选项卡显示已解决的事件和建议的历史记录。

如果您遇到 Office 365 服务的问题，但未在 "**服务运行状况**" 页上看到它，请通过选择 "**报告问题**" 和 "填写短格式" 来告诉我们它。 我们将介绍其他组织提供的相关数据和报告，以查看问题的广泛程度，以及是否与我们的服务有关。 如果是，我们会将其作为新事件或 "**服务运行状况**" 页上的公告添加，您可以在其中跟踪其解决方案。 如果您在30分钟内未看到它显示在列表中，请考虑联系支持人员以解决此问题。

> [!TIP]
> 你也可以在移动设备上使用 [Office 365 Admin 应用](https://go.microsoft.com/fwlink/p/?linkid=627216)查看服务运行状况，这是一种通过推送通知随时获取最新消息的好方法。 
  
### <a name="view-details-of-posted-service-health"></a>查看已发布服务的运行状况详细信息

在 "**所有服务**" 视图中，选择服务状态将打开 "建议" 或 "事件" 的摘要视图。
  
![显示服务建议的屏幕截图](media/service-health-advisory.png)

公告或事件摘要提供以下信息：

- **标题**-问题的摘要。
- **服务**-受影响的服务的名称。
- **ID** -问题的数字标识符。
- **状态**-此问题对服务产生的影响。
- **开始时间**-问题开始的时间。
- **上次更新**时间-上次更新服务运行状况消息的时间。 我们会通过频繁的消息进行发布，让你知道我们在应用解决方案时要做的进展。

选择 "问题标题" 以查看 "问题详细信息" 页，其中显示了有关该问题的详细信息，包括在处理解决方案时发布的所有邮件的[历史记录](#history)。

![显示问题详细信息的屏幕截图](media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a>翻译服务运行状况详细信息

服务运行状况说明是实时发布的，因此这些说明不会自动翻译成你的语言，并且服务事件的详细信息仅以英语形式提供。若要翻译这些说明，请遵循以下步骤：
  
1. 转到[翻译工具](https://www.bing.com/translator/)。

2. 在" **服务运行状况**"页上，选择一个事件或公告。在" **显示详细信息**"下，复制关于该问题的文本。

3. 在"翻译工具"中，粘贴文本，然后选择" **翻译**"。

### <a name="definitions"></a>定义

大多数情况下，服务将显示为正常，没有进一步的信息。 服务出现问题时，该问题会标识为公告或事件，并显示当前状态。
  
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
|**误报** | 在进行详细调查之后，我们已确认服务运行正常且按设计正常运行。 不会对服务造成任何影响，也不会导致事件发生在服务之外。 |
|**已发布事件后报告** | 我们已发布了一个针对特定问题的公告事件报告，其中包括根本原因信息和后续步骤，以确保不会发生类似的问题。 |

### <a name="history"></a>历史记录

服务运行状况允许你查看当前运行状况状态，并查看在过去30天内受到影响的任何服务通知和事件的历史记录。 若要查看所有服务的过去运行状况，请在 "问题详细信息" 页上选择 "**查看历史记录**"。
  
![Show link to health history](media/service-health-view-history.png)
  
显示在选定时间范围内发布的所有服务运行状况消息的列表，如下所示：
  
![View service health history](media/service-health-history.png)
  
展开任意行以查看有关问题的更多详细信息。
  
有关我们对运行时间的承诺的详细信息，请参阅[Office 365 中的透明操作](https://go.microsoft.com/fwlink/?linkid=848695)。
  
## <a name="leave-feedback"></a>提供反馈

我们的目标是确保向你及时、准确地提供仍在持续的问题的有用信息。若要告知我们采取的操作是否切实有效，请选择一个星级评分。给我们评出 1 - 5 星的分数后，你可以提供有关任何特定详细信息的反馈。我们将使用你的反馈微调服务运行状况系统。
  
## <a name="see-also"></a>另请参阅

[Microsoft 365 管理中心中的活动报告](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)