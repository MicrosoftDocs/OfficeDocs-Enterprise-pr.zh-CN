---
title: 如何检查 Office 365 服务运行状况
ms.author: kfollis
author: kfollis
manager: scotv
ms.date: 6/15/2018
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
ms.openlocfilehash: d01fe8e269ace922ab92cca779d6f8fea8b6802e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539595"
---
# <a name="how-to-check-office-365-service-health"></a>如何检查 Office 365 服务运行状况

您可以在 Office 365 中查看 Office 365、 Yammer、 Microsoft Dynamics CRM 和 Microsoft Intune 云服务的运行状况 * * 服务运行状况 * * 在管理中心页面。如果遇到被云服务的问题，您可以检查服务运行状况，以确定是否正在解析的已知的问题之前呼叫支持或花时间进行故障排除。 
  
### <a name="how-to-check-service-health"></a>如何检查服务运行状况

1. 转到[https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage)和管理帐户登录。 
    
    > [!NOTE]
    > 已分配的全局管理员或服务管理员角色的人员可以查看服务运行状况。若要允许 Exchange、 SharePoint 和 Skype 对于业务管理员查看服务运行状况，它们必须指定服务管理员角色。 
  
2. 若要打开在管理中心的服务运行状况，转到**运行状况** \> **服务运行状况**或单击卡片主页仪表板的服务运行状况。仪表板卡片指示是否存在活动服务问题和详细的服务运行状况页面的链接。
    
    ![服务运行状况的仪表板卡片](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. 每个云服务的运行状况状态图标以表格形式显示，以指示可能的状态。
    
> [!TIP]
> 您可以使用移动设备上的[Office 365 管理应用程序](https://go.microsoft.com/fwlink/p/?linkid=627216)以查看服务运行状况，即了解最新的推送通知的好方法。 
  
### <a name="view-details-of-posted-service-health"></a>查看已发布的服务运行状况的详细信息

在默认视图中，将显示所有服务和及其当前运行状况状态。若要筛选视图服务当前遇到一个事件，请从左侧的灰色栏中选择**事件**。选择**通报**会显示当前具有安全公告发布的服务。从**的所有服务**视图中，单击显示的服务状态将打开 advisory 或事件的摘要视图。 
  
![当前服务运行状况中的问题视图](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
Advisory 或摘要事件提供以下信息： 
  
![标记服务通报中的字段的屏幕截图](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. 问题的问题标识符和摘要语句。
    
2. 当前状态。请参阅有关的每个可能的状态说明本文中的状态 definitions。
    
3. 此问题可以如何影响用户的说明。
    
4. 问题已启动的时间和服务运行状况消息已更新的最后一次。整个的问题持续时间中，我们将发布常用消息让您知道我们发出中将解决方案应用的进度。
    
5. 选择**显示详细信息**链接以查看有关此问题，包括所有发布的消息时我们从事解决方案的历史记录的详细信息。 
    
### <a name="translate-service-health-details"></a>翻译服务运行状况详细信息

由于实时发布服务运行状况说明，它们不自动转换到您的语言，仅为英文服务事件的详细信息。若要翻译的说明，请按照下列步骤：
  
1. 转到[translator （英文）](https://www.bing.com/translator/)。
    
2. 在**服务运行状况**页上，选择事件或 advisory。在**显示详细信息**复制有关问题的文本。
    
3. 在 translator （英文），将文本粘贴，然后选择**翻译**。
    
### <a name="definitions"></a>定义

大部分时间服务将按正常，带有任何进一步的信息。时服务时遇到问题，问题将识别为 advisory 或事件并显示当前状态。
  
> [!TIP]
> 计划的维护事件不会显示在服务运行状况。您可以通过保持最新**消息中心**跟踪计划内的维护事件。筛选邮件归类为更改的计划以找出时将发生更改，其生效，以及如何准备它。有关详细信息，请参阅[Office 365 中的邮件中心](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093)。 
  
### <a name="incidents-and-advisories"></a>事件和建议

|||
|:-----|:-----|
|![信息图标 advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|如果服务显示 advisory，我们将了解问题影响某些用户，但仍然可用服务。在 advisory，通常的问题解决方法，该问题可能间歇性或限制的作用域和用户的影响。  <br/> |
|![事件感叹号图标](media/a636db57-6083-44dc-bbd5-556850804f17.png)|如果服务显示一个活动事件，这是一个关键问题和服务或该服务的一项主要功能不可用。例如，用户可能无法发送和接收电子邮件或无法登录事件将具有对用户的显著影响。当正在进行中有一个事件时，我们将提供有关调查、 缓解措施，并确认服务运行状况仪表板中的解决方案的更新。  <br/> |
   
### <a name="status-definitions"></a>状态定义

| |
|**状态**|**定义**|
|:-----|:-----|
|调查 （英文)  <br/> |我们知道的潜在问题，并将收集有关了什么事和的影响范围的详细信息。  <br/> |
|服务降级  <br/> |我们已确认存在可能会影响使用服务或功能的问题。如果服务执行速度比往常很慢，您可能会看到此状态、 有间歇性中断或如果工作不一项功能，例如。  <br/> |
|服务中断  <br/> |如果我们确定问题影响用户以访问服务的功能，您将看到此状态。在这种情况下，问题很重要，并且可以一致重现。  <br/> |
|还原服务  <br/> |已发现的问题原因，我们知道哪些要执行的更正操作和正在将服务后引入正常运行状态。  <br/> |
|扩展的恢复  <br/> |此状态指示纠正措施正在还原到大多数用户的服务，但需要花一些时间到达的所有受影响的系统。如果我们已进行临时修复以减少影响我们等待应用永久修复，则还可以看到此状态。  <br/> |
|挂起的调查  <br/> |如果我们的潜在问题的详细的调查结果从客户的其他信息，以便我们能够进一步调查的请求，您将看到此状态。如果我们需要您操作，我们会让您知道我们需要哪些数据或日志。  <br/> |
|还原的服务  <br/> |我们已确认纠正措施已解析的底层问题和服务已还原到正常运行状态。若要找出出现的问题，请查看问题详细信息。  <br/> |
   
## <a name="history"></a>“历史记录”

服务运行状况允许您查看当前运行状况状态以及过去 30 天内查看任何服务通报和事件的历史记录。若要查看过去的所有服务运行状况，选择**服务运行状况**页上的**查看历史记录**。 
  
![显示链接到运行状况历史记录](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
将显示所有服务运行状况发布的消息中的选定时间段列表，如下所示：
  
![查看服务运行状况历史记录](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
最近 7 天或 30 天内，您可以查看运行状况历史记录。选择要查看有关该问题的更多详细信息任何行。
  
有关我们承诺正常运行时间的详细信息，请参阅[从 Office 365 的透明操作](https://go.microsoft.com/fwlink/?linkid=848695)。
  
## <a name="leave-feedback"></a>提供反馈

我们的目标是确保我们向您提供有关后续问题的信息及时、 准确和有用。告诉我们如何我们执行的操作中，选择星评级。您给我们分数从 1 到 5 星形后，您可以在任何特定的详细信息移交反馈。我们将使用您的反馈来调整我们的服务运行状况系统。
  
![服务运行状况问题的反馈表单](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a>另请参阅

[Office 365 管理中心中的活动报告](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

