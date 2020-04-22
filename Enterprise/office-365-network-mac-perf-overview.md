---
title: Microsoft 365 管理中心中的网络性能建议（预览）
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 管理中心中的网络性能建议概述（预览）
ms.openlocfilehash: 077202f5ba1ffa95324131e6c283f2c3845aa07f
ms.sourcegitcommit: 07ab7d300c8df8b1665cfe569efc506b00915d23
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2020
ms.locfileid: "43612932"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>Microsoft 365 管理中心中的网络性能建议（预览）

Microsoft 365 管理中心现在包含从 Microsoft 365 租户收集的实时性能指标，仅可供租户中的管理用户查看。 **网络洞察力和性能建议**和**网络评估**显示在 Microsoft 365 管理中心<https://portal.microsoft.com/adminportal/home#/networkperformance>。 您可以在 "运行状况" 下的导航窗格中找到该页面。 **网络性能**。

![网络性能页面](Media/m365-mac-perf/m365-mac-perf-page-nav.png)

当您第一次导航到 "网络性能" 页面时，将看到 "概述" 窗格，其中包含全局网络性能的地图、网络评估范围为整个租户以及当前问题的列表。 从概述中，您可以深入查看特定的网络性能指标和按位置的问题。 有关详细信息，请参阅[Microsoft 365 管理中心中的网络性能概述](#network-performance-overview-in-the-microsoft-365-admin-center)。

## <a name="pre-requisites-for-connectivity-measurements-to-appear"></a>要显示的连接度量的先决条件

为使连接测量显示出来，必须至少有两台在支持先决条件的办公室位置运行的计算机。 必须在每台计算机上安装 OneDrive for business 同步客户端版本19.232 或更高版本。 有关详细信息，请参阅[OneDrive 发行说明](https://support.office.com/article/onedrive-release-notes-845dcf18-f921-435e-bf28-4e24b95e5fc0)。

Windows 位置服务必须在计算机上同意。 您可以通过运行 "**地图**" 应用并找到自己来对此进行测试。 可以**在具有** -> 设置**隐私** -> **位置**的单个计算机上启用此设置，必须启用设置 "允许应用访问你的位置"。 可以将 Windows 位置服务同意部署到使用 MDM 或组策略的电脑中，设置_LetAppsAccessLocation_。

计算机应具有 Wi-fi 网络，而不是以太网电缆。 具有以太网电缆的计算机没有准确的位置信息。

满足这些先决条件后，度量样本和办公室位置应会在24小时后开始显示。

## <a name="how-do-i-use-this-information"></a>如何使用此信息？

**网络洞察力**、其相关的性能建议和网络评估旨在帮助为你的办公室位置设计网络外围。 每个真知灼见都提供有关用户访问你的租户的每个地理位置的特定常见问题的性能特征的实时详细信息。 每个网络洞察力的**性能建议**提供了您可以进行的特定网络体系结构设计更改，以改进与 Microsoft 365 网络连接相关的用户体验。 网络评估显示网络连接对用户体验的影响，从而允许比较不同的用户位置网络连接。

**网络评估**将许多网络性能指标的聚合提取到企业网络运行状况的快照中，由 1-100 中的点值表示。 网络评估的作用范围为整个租户和每个地理位置，用户将从该位置连接到你的租户，从而为 Microsoft 365 管理员提供一种简单的方法来即时了解企业网络运行状况的 gestalt，并快速深入到任何全球办公地点的详细报告。

具有多个办公室位置和非普通网络外围体系结构的复杂企业可以在初始加入 Microsoft 365 或解决使用情况增长发现的网络性能问题时从这些信息中受益。 对于使用 Microsoft 365 的小型企业或已具有简单且直接的网络连接的企业，这通常是不必要的。 具有500个以上的用户和多个办公地点的企业有望获益最多。

>[!IMPORTANT]
>网络洞察力、Microsoft 365 管理中心中的性能建议和评估当前处于预览状态，并且仅适用于已在功能预览计划中注册的 Microsoft 365 租户。

## <a name="enterprise-network-connectivity-challenges"></a>企业网络连接难题

![客户网络到云](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

许多企业都具有网络外围配置，这些配置随着时间的推移而逐渐发展，主要旨在适应员工 Internet 网站访问，其中大多数网站都不是预先知道的，不受信任。 这些未知网站的受攻击和必要的重点是避免恶意软件和钓鱼攻击。 此网络配置策略虽然有助于安全目的，但会导致 Microsoft 365 用户性能和用户体验下降。

## <a name="how-we-can-solve-these-challenges"></a>我们可以如何解决这些难题

企业可以通过遵循[Office 365 连接原则](https://aka.ms/pnc)和使用 Microsoft 365 管理中心网络性能功能来改进常规用户体验并保护其环境。 在大多数情况下，遵循这些常规原则将对最终用户延迟、服务可靠性和 Microsoft 365 的总体性能产生重大影响。

有时，microsoft 需要调查大型企业客户的 Microsoft 365 的网络性能问题，并且这些问题通常有与客户网络出口基础结构相关的根本原因。 当发现客户网络外围问题的常见根源时，我们会设法确定确定它的简单测试指标。 具有确定特定问题的度量阈值的测试非常有用，因为我们可以在任何位置测试相同的指标，告知是否存在此根本原因，并将其共享为与管理员的网络洞察力。

一些网络见解只表示需要进一步调查的问题。 一种网络洞察力，其中我们有足够的测试来显示解决根本原因的特定修正操作，作为**建议的操作**列出。 这些建议基于实时指标，其中显示超出预先确定的阈值之外的值，比一般的最佳实践建议更有价值，因为它们是特定于您的环境的，并且会在进行建议的更改后显示实际的改进。

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>Microsoft 365 管理中心中的网络性能概述

Microsoft 从多个 Office 桌面和 web 客户端中获得了支持 Microsoft 365 操作的现有网络度量。 这些度量现在用于提供网络体系结构设计见解和网络性能评估，这些评估显示在 Microsoft 365 管理中心的**网络性能**页面中。

默认情况下，与网络度量相关联的近似位置信息标识客户端设备所在的城市。 每个位置的网络评估均以颜色显示，并且每个位置的用户相对数量由圆的大小表示。

![网络洞察力概述映射](Media/m365-mac-perf/m365-mac-perf-overview-map.png)

概述页面还显示了客户的网络评估，作为所有办公地点的加权平均。

![网络评估](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

## <a name="specific-office-location-network-performance-summary-and-insights"></a>特定的办公室位置网络性能摘要和见解

选择 "办公室位置" 将打开一个特定位置的摘要页面，其中显示了已从该办公室位置测量指标中标识的网络出口的详细信息。

![按位置的网络洞察力详细信息](Media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

"Office 位置摘要" 页还会显示位置的网络评估、网络评估历史记录、此位置的评估与同一城市中的其他客户的比较，以及您可以采取以提高网络性能和可靠性的特定见解和建议的列表。 具有特定建议的位置也可能包括估计的潜在延迟改进。

同一个城市中的客户之间的比较取决于所有客户都具有对网络服务提供商、电信基础结构和附近 Microsoft 网络状态点的同等访问权限的预期。

![网络见解位置](Media/m365-mac-perf/m365-mac-perf-locations.png)

"Office 位置" 页上的 "详细信息" 选项卡显示了用于提供任何见解、建议和网络评估的具体测量结果。 提供此信息是为了让网络工程师能够验证其环境中的任何约束或细节方面的建议和因素。

![位置特定的详细信息](Media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)

对于希望提高特定位置的指标和建议的准确性的客户，我们允许输入更具体的信息。 这样可以减少可用于网络指标的位置信息中固有的近似值。 若要编辑特定办公室位置的地址，请<functionality not there yet>。

## <a name="import-undiscovered-office-locations"></a>导入未发现的 office 位置

"网络性能**位置**" 选项卡显示从网络遥测中自动发现的办公室位置的列表。 这些办公室位置是被发现的城市。 如果不自动显示在列表中，则可以手动在这些城市中添加更多特定位置，方法是从 CSV 文件中导入这些位置。 如果 office 位置根本不显示，您应排除其网络度量不显示的原因，而不只是将位置添加到此处。 您还可以更新现有办公室位置的地址值。

在 CSV 文件中，aA 中发现的城市位置标有 " **city**"，手动添加的 "office 位置" 标记为 "**位置**"。

1. 在 " _Microsoft 365_的主要连接" 窗口中，单击 "**位置**" 选项卡。
1. 单击 "位置" 列表正上方的 "**导入**" 按钮。 将显示 "**导入 office 位置**" 浮出控件。

   ![CSV 导入错误消息](Media/m365-mac-perf/m365-mac-perf-import.png)

1. 单击 "**下载当前的 office 位置（.csv）** " 链接，将当前位置列表导出到 csv 文件，并将其保存到本地硬盘。 这将为您提供一个可向其添加位置的格式正确的 CSV。 您可以保留导出的位置。当您导入更新的 CSV 时，将不会复制它们。 如果要更改现有位置的地址，则会在您导入 CSV 时对其进行更新。 您无法更改发现的城市的地址。
1. 打开 CSV 并添加您的位置，方法是在要添加的每个位置的新行上填写以下字段。 将所有其他字段保留为空;您在其他字段中输入的值将被忽略。
   1. **Address** （必需）： office 的物理地址
   1. **纬度**（可选）：如果为空，则从 Bing 地图查找中填充
   1. **经度**（可选）：如果为空，则从 Bing 地图查找中填充
   1. **出局 IP 地址范围 1-5** （可选）：对于每个区域，请输入电路名称，后跟一个以空格分隔的有效 IPv4 或 IPv6 CIDR 地址列表。 仅当您为给定的办公室位置启用了 SDWAN 集成时，才使用这些值。
1. 添加办公室位置并保存文件后，单击 "**上载完成**时间" 字段旁边的 "**浏览**" 按钮，然后选择保存的 CSV 文件。
1. 将自动验证文件。 如果存在验证错误，您将看到错误消息_导入文件中存在一些错误。请查看错误，更正导入文件，然后重试。_ 有关特定字段验证错误的列表，请单击链接的 "**打开错误详细信息**"。

   ![CSV 导入错误消息](Media/m365-mac-perf/m365-mac-perf-import-error.png)

1. 如果文件中没有任何错误，您将看到_报告已准备好的消息。找到要添加的 x 位置和要更新的 x 位置。_ 单击 "**导入**" 按钮上传 CSV。

   ![CSV 导入就绪消息](Media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="faq"></a>常见问题

### <a name="what-is-a-microsoft-365-service-front-door"></a>什么是 Microsoft 365 服务的前盖？

Microsoft 365 服务的前端是 Microsoft 全球网络的一个入口点，Office 客户端和服务终止其网络连接。 为实现到 Microsoft 365 的最佳网络连接，建议您的网络连接在城市或地铁的最近 Microsoft 365 前向外端终止。

>[!NOTE]
>Microsoft 365 服务前向与 azure marketplace 提供的 Azure 前门服务产品没有直接关系。

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a>什么是最佳 Microsoft 365 服务前门？

最佳 Microsoft 365 服务前盖是最接近你的网络出口（通常在你所在的城市或大都市区域中）的一门。 使用[microsoft 365 连接测试](office-365-network-mac-perf-onboarding-tool.md)确定正在使用的 microsoft 365 服务前盖和最佳服务前盖的位置。 如果该工具确定你的使用中的前向门是最佳的，则表示你正在以最佳方式连接到 Microsoft 的全球网络。

### <a name="what-is-an-internet-egress-location"></a>Internet 出口的位置是什么？

Internet 出局位置是网络流量退出企业网络并连接到 Internet 的位置。 这也被标识为您拥有网络地址转换（NAT）设备且通常与 Internet 服务提供商（ISP）进行连接的位置。 如果你发现您的位置和 internet 出局位置之间的距离很长，则这可能表示有重要的 WAN backhaul。

## <a name="related-topics"></a>相关主题

[Microsoft 365 网络见解（预览）](office-365-network-mac-perf-insights.md)

[Microsoft 365 网络评估（预览）](office-365-network-mac-perf-score.md)

[M365 管理中心中的 Microsoft 365 连接测试（预览）](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 网络连接位置服务（预览）](office-365-network-mac-location-services.md)
