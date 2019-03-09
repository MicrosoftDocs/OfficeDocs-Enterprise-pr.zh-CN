---
title: 容量规划和负载测试 SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: 本文介绍如何在不执行传统负载测试的情况下部署到 SharePoint Online, 因为这是不允许的。
ms.openlocfilehash: ef5d6c043b4be2e8c5358a9c060459b4c6a92156
ms.sourcegitcommit: 468c8e8d2f951e08cf50301445ad650ef17328aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "30512717"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>SharePoint Online 的容量规划和负载测试。

本文介绍了如何在不进行传统负载测试的情况下部署到 sharepoint online, 因为 sharepoint Online 不允许进行负载测试。 SharePoint Online 是一项云服务, 服务中负载的负载功能、运行状况和总体平衡由 Microsoft 进行管理。
  
确保网站启动成功的最佳方法是遵循下面突出显示的基本原则、做法和建议。
  
在本地环境中, 负载测试用于验证扩展假设并最终发现服务器场的中断点;通过将其与负载进行饱和。 通过 SharePoint Online, 我们需要以不同的方式执行操作。 作为多租户环境, 我们必须保护同一服务器场中的所有租户, 因此我们将自动限制任何负载测试。 这意味着, 如果您尝试加载测试您的环境, 您将收到 disappointing 和潜在的令人误解的结果。
  
在本地部署中, SharePoint Online 的主要优势之一是云的弹性。 我们将大型环境设置为每天为数百万个用户提供服务, 因此我们必须通过平衡和扩展服务器场有效地处理容量。 此外, 本文还介绍了不涉及负载测试的方法, 但涉及到了将设置为成功启动的以下准则。 
  
在任何一个服务器场中的任何一个租户的增长不可预测的情况下, 累积的请求总数将随时间推移而预测。 通过确定 SharePoint Online 中的增长趋势, 我们可以规划未来的扩展。
  
为了高效地使用容量并处理意外增长, 在任何服务器场中, 我们都具有可在需要时跟踪前端负载和扩展的自动化。 有多个指标使用的是 CPU 负载, 其中一个主要是 CPU 负载, 用作扩展前端服务器的信号。 此外, 您还将在本文中进一步说明, 我们建议采用分阶段/波形方法, 因为 SQL 环境将根据负载和需求进行扩展, 并遵循这些阶段和波形, 从而实现负载和增长的正确分布。 
  
## <a name="how-do-i-plan-for-a-site-launch"></a>如何规划网站启动？

### <a name="optimize-pages-by-following-recommended-guidelines"></a>按照建议的准则优化页面
不应简单地将本地部署中的页面视为 sharepoint online, 而不是针对 sharepoint online 的建议准则进行评审。

应考虑以下几个关键因素:
- 内部部署可以利用传统的服务器端缓存 (如对象缓存), 但在云中的拓扑差异, 这些选项不可用。
- 用于云消耗量的任何页面/功能/自定义应针对多个位置进行优化, 以便不同区域或区域中的用户具有一致的体验。 云提供了优化, 如内容传递网络 (CDN), 可针对分布式用户群进行优化。

对于 SharePoint Online 中的经典发布页面, 可以使用 "[页面诊断工具](https://aka.ms/perftool)" Chrome 扩展名, 该扩展将帮助分析用户使用的主登录页。
浏览器或[Fiddler](https://www.telerik.com/download/fiddler)中的 F12 开发人员工具可用于查看页面的重量, 以及应检查和优化整个页面负载影响的呼叫和元素的数量。 可以在 "[优化 SharePoint Online 性能](https://aka.ms/spoperformance)" 文章中查看包括使用内容传递网络和其他优化的建议列表。

### <a name="wave--phase-approach"></a>波形/相位方法
用于站点启动的传统的大做法不会有效地允许验证自定义、外部源、服务或流程是否已在适当的规模进行了测试。 作为服务的 SharePoint 还可以根据使用情况和预测使用率来扩展容量, 同时我们不需要你通知网站发布, 您应遵循以下指南以确保成功。
  
如下图所示, 通常受邀的用户数量明显高于实际使用网站的用户数量。 此图显示了有关如何推出发布的策略。 此方法可帮助您确定在大多数用户看到 SharePoint 网站之前改进 SharePoint 网站的方法。 如果在任何阶段/波浪中遇到问题, 并且限制受影响的用户数, 则它还允许暂停部署。
  
![显示受邀并且处于活动状态的用户的图形](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
在试验阶段, 最好从组织信任和知道将参与的用户获取反馈。 通过这种方式, 可以测量系统的使用情况及其执行方式。
  
在每个波形过程中, 收集有关功能的用户反馈, 以及每个部署浪潮期间的性能。 这样做的优势在于系统在获得更多使用时慢慢引入系统并进行改进。 这还使我们能够在向越来越多的用户推出网站时对增加的负载做出反应。
