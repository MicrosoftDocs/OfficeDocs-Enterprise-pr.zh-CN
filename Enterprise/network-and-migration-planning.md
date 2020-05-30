---
title: Office 365 的网络和迁移规划
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: 包含有关网络规划和测试以及迁移到 Office 365 的信息的链接。
ms.openlocfilehash: 88dd3e4fca66855e8204b452aea6cfb4c659d201
ms.sourcegitcommit: bb5b7bd241f58491198de2d74dbdce76f7bb8f62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "44419380"
---
# <a name="network-and-migration-planning-for-office-365"></a>Office 365 的网络和迁移规划

*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*

本文包含有关网络规划和测试以及迁移到 Office 365 的信息的链接。
  
在首次部署或迁移到 Office 365 之前，您可以使用这些主题中的信息来估计所需的带宽，然后测试并验证是否有足够的带宽来部署或迁移到 Office 365。

||
|:-----|
| 本文是[Office 365 的网络规划和性能调整](https://aka.ms/tune)的一部分。|

|||
|:-----|:-----|
|![请参阅适用于企业架构师的 Microsoft 云网络海报](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|有关为 Office 365 和其他 Microsoft 云平台和服务优化网络的步骤，请参阅适用于[企业架构师的 Microsoft 云网络](https://aka.ms/cloudarchnetworking)海报。 |
   
## <a name="estimate-network-bandwidth-requirements"></a>估计网络带宽要求
<a name="EstimateBandwidthRequirements"> </a>

使用 Office 365 可能会提高组织的 internet 电路的利用率。 务必要确定当前可用的带宽量是否足以处理在完全部署 Office 365 时的估计增加，同时留下至少20% 的容量来处理最空闲的天数。
  
若要估计带宽，请执行以下步骤：
  
1. 评估将使用每个 Internet 出口的客户端数量。 让我们的多 terabit 网络能够处理尽可能多的连接。 
    
2. 确定哪些 Office 365 服务和功能将可供客户端使用。 您可能拥有不同的服务或使用情况配置文件的用户组。
    
3. 测量客户端的引导组的网络使用情况。 确保试点客户端代表组织中的人员的不同配置文件以及不同的地理位置。 您可以针对[Exchange](https://go.microsoft.com/fwlink/p/?LinkId=321550)和[Skype for business](https://go.microsoft.com/fwlink/p/?LinkId=321551)的旧计算器或我们在自己的网络上执行的[案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)，对结果进行交叉检查。 
    
4. 使用试点组中的度量来推断整个组织的需求，并在对网络进行任何更改之前，重新测试以验证评估。
    
## <a name="test-your-existing-network"></a>测试现有网络
<a name="calculators"> </a>

 **网络工具。** 测试和验证你的 Internet 带宽，以确定下载、上传和延迟限制。 这些工具将帮助您确定用于迁移的网络功能以及在完全部署之后的功能。 
    
- [Microsoft 远程连接分析器](https://go.microsoft.com/fwlink/p/?LinkId=517243)：测试 Exchange Online 环境中的连接性。
    
- 使用[适用于 Office 365 的 Microsoft 支持和恢复助理](https://diagnostics.office.com/#/Download?env=SOC)解决 Outlook 和 Office 365 问题。 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>针对 Office 365 的网络规划和提高迁移性能的最佳做法
<a name="BestPractices"> </a>

深入了解这些最佳做法，以了解有关改进 Office 365 体验的详细信息。
  
1. 想要立即开始帮助你的用户吗？ 有关在[慢速网络上使用 office 365 的最佳实践](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)，请参阅在网络不合作时使用 office 365 的提示（包括 SharePoint Online、Exchange Online 和 Lync online）。 本文链接到 TechNet 和 Support.office.com 上的内容加载以优化 Office 365 体验，其中包括有关自定义网页的简单方法以及如何设置 Internet Explorer 设置以实现最佳 Office 365 体验的信息。 
    
2. 阅读[office 365 网络连接原则](https://aka.ms/o365networkingprinciples)，了解用于安全管理 Office 365 流量和获得最佳性能的连接原则。 本文将帮助您了解有关安全优化 Office 365 网络连接的最新指南。 
    
3. 通过仔细管理 Windows 更新的日程安排，提高邮件迁移性能。 您可以成批更新客户端计算机，并确保在迁移到 Office 365 之前更新所有客户端计算机，以控制网络带宽的使用。 有关详细信息，请参阅为[Office 365 手动更新和配置桌面，以获取最新更新](https://support.microsoft.com/gp/office-2013-365-update)。
    
4. Office 365 网络流量在被视为受信任的 Internet 服务时执行得最佳，并允许绕过大部分传统筛选和扫描，以避免某些组织将网络流量置于不受信任的 Internet 服务中。 这通常包括删除出站处理（如代理用户身份验证和数据包检查），以及使用正确的网络地址转换（NAT）和足够的带宽容量来处理增加的网络请求，从而确保本地进入 Internet。 有关配置网络以将 Office 365 作为受信任的 Internet 服务在网络上进行处理的其他指导，请参阅[管理 office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。
    
1. 确保[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。 转到 Office 365 的其他流量会导致出站代理连接的增加以及通过 TLS/SSL 的安全通信的增长。
    
2. 如果出站代理要求用户身份验证，则可能会遇到连接速度慢或功能丢失的情况。 绕过 Office 365 域的身份验证要求可以降低此开销。
    
3. 如果有大量共享日历和邮箱，您可能会看到从 Outlook 到 Exchange 的连接数增加。 例如，对于使用的每个共享日历，Outlook 客户端可能会打开多达两个附加连接。 在这种情况下，请确保出站代理可以处理连接，或者绕过代理连接到适用于 Office 365 for Outlook 的连接。
    
4. 确定公共 IP 地址支持的最大设备数以及如何在多个 IP 地址之间实现负载平衡。 有关详细信息，请参阅[与 Office 365 的 NAT 支持](nat-support-with-office-365.md)。
    
5. 如果要检查来自网络上的计算机的出站连接，则绕过对 Office 365 域的此筛选可提高连接性和性能。 此外，绕过出站检查通常无需进行单个 Internet 出口，并为 Office 365 发来的网络请求启用本地 Internet 出口。
    
6. 某些客户发现内部网络设置可能会影响性能。 指向 Internet 的最大传输单位（MTU）大小、网络自动协商或自动检测以及子最佳路由等设置是常见的外观。
    
## <a name="network-planning-reference-for-office-365"></a>Office 365 的网络规划参考
<a name="NetReference"> </a>

这些主题包含详细的 Office 365 网络参考信息。
  
- [管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [内容分发网络](content-delivery-networks.md)
    
- [Office 365 的外部域名系统记录](external-domain-name-system-records.md)
    
- [Office 365 服务中的 IPv6 支持](ipv6-support.md)
    
- [Office 365 网络连接原则](https://aka.ms/o365networkingprinciples)
    
- [Office 365 视频网络常见问题（FAQ）](office-365-video-networking-faq.md)
    
- [有关连接到 Office 365 服务的网络设备的计划](plan-for-network-devices.md)
    
- [Office 365 服务的安装指南](setup-guides-for-office-365.md)
 
## <a name="see-also"></a>另请参阅

[Microsoft 365 企业版概述](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
