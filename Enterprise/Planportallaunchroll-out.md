---
title: 在 SharePoint Online 中规划门户启动滚动计划
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
description: 本文介绍如何在 SharePoint Online 中规划门户启动以及成功启动所需的步骤
ms.openlocfilehash: bba38bb188235ed38f3719cb4472ef156a4d76b3
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077565"
---
# <a name="planning-your-portal-launch-roll-out-plan-in-sharepoint-online"></a>在 SharePoint Online 中规划门户启动滚动计划
门户是贵公司的默认 SharePoint 网站;在大型组织中，可能有多种。 如果你希望组织内 20% 以上的用户都能访问该页面，应考虑将该页面设置为门户页面。 此页面不应与你的部门用于在团队中协作和共享文档的团队网站混淆。

本文介绍如何规划部署和向 SharePoint Online 计划。 它还提供了在 SharePoint Online 上不允许进行传统负载测试时遵循的方法。 SharePoint Online 是云服务，服务中负载的负载功能、运行状况和总体平衡由 Microsoft 进行管理。

若要帮助创建成功的门户，请遵循[创建、启动和维护正常门户](https://go.microsoft.com/fwlink/?linkid=2105838)中详细介绍的基本原则、做法和建议 

下面突出显示了部署方法。

## <a name="overview-of-capacity-planning-in-sharepoint-online"></a>SharePoint Online 中的容量规划概述
为了高效地使用容量并处理意外增长，在任何服务器场中，我们都具有跟踪特定使用方案的自动化。 在任何一个服务器场中的任何一个租户的确切增长不可预测的情况下，累积的请求总数将随时间推移而预测。 通过确定 SharePoint Online 中的增长趋势，我们可以规划未来的扩展。 有关[SharePoint Online 的容量规划和负载测试](https://docs.microsoft.com/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online)的详细信息。

成功启动的关键部分是以下详细说明的 "波形" 或 "分阶段式输出" 方法。 

## <a name="can-i-load-test-sharepoint-online"></a>我可以加载测试 SharePoint Online 吗？
SharePoint Online 是一个共享的多租用环境，它在服务器场之间平衡，并在不断调整规模。 负载测试环境（如 SharePoint Online）的缩放更改不会持续提供意外结果，但不允许这样做。 

了解详细信息：[容量规划和负载测试 SharePoint Online](https://docs.microsoft.com/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online)

## <a name="optimize-pages-by-following-recommended-guidelines"></a>按照建议的准则优化页面
本地部署中的页面不应简单地移动到 SharePoint Online 中，而无需针对 SharePoint Online 的建议准则进行评审。 最佳方法是始终为 SharePoint 中的任何网站或门户优化任何主页，因为这是组织中的大多数用户将作为网站的起始点进行访问的位置。

应考虑以下几个基本因素：
- 内部部署可以利用传统的服务器端缓存，如对象缓存、输出缓存和 blob 缓存。 由于云中的拓扑差异，这些选项不一定可用作非常大的规模差异，从而使其不是可行的方法。
- 用于云使用的任何页面/功能/自定义应针对较高的延迟和用户的分布式位置进行优化，以便不同区域或区域中的用户具有更一致的体验。 云提供了优化（如内容传递网络（CDN））以优化分布式用户库和新式 SharePoint，我们的现成（OOTB） web 部件使用最后一种已知良好（LKG）。

### <a name="what-to-do"></a>要执行的操作：
 - 对于 SharePoint Online 中的所有网站页面，使用[页面诊断工具](https://aka.ms/perftool)，这是一种 Chromium 扩展，可帮助分析和提供指导。 这可供网站所有者、编辑者、管理员和开发人员使用，因为它旨在作为分析和优化的起始点。
 - 开发人员还应在新式页面的浏览器中使用类似于 F12 浏览器开发人员工具和 CTRL-F12 的开发工具。 [Fiddler](https://www.telerik.com/download/fiddler)还可用于查看页面的大小权重（页面大小为兆字节）以及影响整个页面负载的呼叫和元素的数量。 

此部分是优化页面的简短摘要。  若要了解详细信息[，请参阅创建、启动和维护正常的门户](https://go.microsoft.com/fwlink/?linkid=2105838)。

## <a name="follow-a-wave--phased-roll-out-approach"></a>遵循波形/分阶段的滚动方法
用于网站启动的传统的大方法将不允许验证自定义项、外部源、服务或进程是否已在适当的规模进行测试。 这并不意味着需要几个月即可启动，但建议在至少几天内取决于您的组织的规模。 因此，在执行下一阶段时，可以选择暂停和解决问题，从而减少受任何问题影响的潜在用户数。 SharePoint as service 根据使用情况和预测使用率扩展了你的容量，同时我们不需要你通知我们你的产品发布，你应遵循确保成功的指南。
  
如下图所示，通常受邀的用户数量明显高于实际使用网站的用户数量。 此图显示了有关如何推出发布的策略。 此方法可帮助您确定在大多数用户看到 SharePoint 网站之前改进 SharePoint 网站的方法。
  
![显示受邀并且处于活动状态的用户的图形](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
在试验阶段，最好从组织信任和知道将参与的用户获取反馈。 通过这种方式，可以测量系统的使用情况及其执行方式。
  
在每个波形过程中，收集有关功能的用户反馈，以及每个部署浪潮期间的性能。 这样做的优势在于系统在获得更多使用时慢慢引入系统并进行改进。 这还使我们能够在向越来越多的用户推出网站时对增加的负载做出响应，并将其与遵循页面优化的准则结合起来，以确保为用户提供积极的体验。

### <a name="what-to-do"></a>要执行的操作：
- 确定每个阶段的时间，并确保您有应急/暂停机会，应在继续进行调整前进行调整
- 规划您要启用的第一组用户，以确保您收到要向前移动的反馈。 这意味着，在可能的情况下，选择将及时提供反馈的一组活动用户。
- 在规划每个浪潮时，请尝试并从一个小用户群（少于5000个用户）开始，然后在每个浪潮继续时增加组大小。 这有助于创建交错的方法，并允许更轻松地暂停可能需要的商机。
