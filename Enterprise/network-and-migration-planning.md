---
title: Office 365 的网络和迁移规划
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: 包含有关网络规划和测试的信息的链接和迁移到 Office 365。
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223054"
---
# <a name="network-and-migration-planning-for-office-365"></a>Office 365 的网络和迁移规划

本文包含有关网络规划和测试的信息链接和迁移到 Office 365。
  
在首次部署或迁移到 Office 365 之前，可以使用这些主题中的信息来估计您需要的带宽，然后测试和验证您是否具有足够的带宽来部署或迁移到 Office 365。

||
|:-----|
| 本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)的一部分。|

|||
|:-----|:-----|
|![请参阅 Microsoft 云网络企业架构师海报](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|优化网络 for Office 365 和其他 Microsoft 云平台和服务的步骤，请参阅[Microsoft 云网络的企业架构师](https://aka.ms/cloudarchnetworking)海报。 |
   
## <a name="estimate-network-bandwidth-requirements"></a>估计网络带宽要求
<a name="EstimateBandwidthRequirements"> </a>

使用 Office 365 可能会增加贵组织的 internet 电路的使用率。非常重要，以确定当前可用带宽量是否足以同时保持至少 20%完全部署 Office 365 之后处理估计的增加容量来处理繁忙的天数。
  
若要估计带宽，请使用以下步骤：
  
1. 评估客户端将使用每个 Internet 出口数。让我们多 terabit 网络中处理尽可能尽可能的连接。 
    
2. 确定哪些 Office 365 服务和功能可供客户端使用。您可能必须具有不同的服务或使用情况配置文件的人员的组。
    
3. 测量网络使用的客户端试点组。确保试点客户端所代表的不同的配置文件的组织，以及在不同地理位置中的人员。您可以跨检查您对我们旧计算器的结果的[Exchange](https://go.microsoft.com/fwlink/p/?LinkId=321550)和[for Business 的 Skype](https://go.microsoft.com/fwlink/p/?LinkId=321551)或[案例研究](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)我们我们自己的网络执行。 
    
4. 从试用组的度量值用于在整个组织的需求外推并重新测试对您的网络进行任何更改之前验证估计值。
    
## <a name="test-your-existing-network"></a>测试您现有的网络
<a name="calculators"> </a>

 **网络工具。** 测试和验证您的 Internet 带宽，以确定下载、 上载和延迟的约束。这些工具将帮助您确定您的网络迁移以及完全正在部署后的功能。 
  
- [Microsoft 消息分析器](https://technet.microsoft.com/library/jj649776.aspx)： 消息分析器是有效的网络问题进行故障排除工具。消息分析器捕获、 显示，并分析基于协议消息通信和系统消息。消息分析器还可以导入、 合计并分析日志和跟踪文件中的数据。
    
- [Microsoft 远程连接分析器](https://go.microsoft.com/fwlink/p/?LinkId=517243)： Exchange Online 环境中测试连接。
    
- 使用[Microsoft 支持和 Office 365 恢复助手](https://diagnostics.office.com/#/Download?env=SOC)修复 Outlook 和 Office 365 问题。 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Best practices for network planning and improving migration performance for Office 365
<a name="BestPractices"> </a>

深入到这些最佳做法有关提高您的 Office 365 体验的详细信息。
  
1. 要开始立即帮助您的用户？有关使用 Office 365，包括 SharePoint Online、 Exchange Online 和 Lync Online，您的网络刚刚不共同完成时提示，请参阅[使用在低速网络中的 Office 365 的最佳实践](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。本文出链接到 TechNet 和 Support.office.com 上的内容加载优化您的 Office 365 体验，并包括有关自定义网页以及如何设置 Internet Explorer 设置获得最佳的 Office 365 体验的简单方法。 
    
2. 阅读[Office 365 网络连接原则](https://aka.ms/o365networkingprinciples)了解用于安全地管理 Office 365 流量和获取最佳性能的连接原则。本文将帮助您了解有关安全地优化 Office 365 网络连接的最新指南。 
    
3. 通过仔细管理 Windows 更新的计划来提高邮件迁移性能。可以更新成批客户端计算机，并确保迁移到 Office 365 以哪种网络带宽使用之前更新所有客户端计算机。有关详细信息，请参阅[手动更新和配置最新的更新的 Office 365 的桌面](https://support.microsoft.com/gp/office-2013-365-update)。
    
4. Office 365 网络流量最佳执行时有视为受信任的 Internet 服务，并且允许绕过大部分传统筛选和扫描的某些组织将置于不受信任的 Internet 服务网络流量。这通常包括删除出站代理用户身份验证和检查数据包来，如处理，以及确保使用适当的网络地址转换 (NAT) 和足够的带宽容量来处理增加 internet 本地出口网络请求。配置网络以处理作为受信任的 Internet 服务网络上的 Office 365 的其他指导信息，请参阅[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。
    
1. 确保[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)。额外的流量转到 Office 365 结果中的出站代理服务器连接的增加，以及增加的安全流量通过 TLS/SSL。
    
2. 如果您的出站代理需要用户身份验证可能会遇到低速连接性或功能损失。绕过的 Office 365 域的身份验证要求可以减少此开销。
    
3. 如果您有大量的共享日历和邮箱，则可能会发现从 Outlook 到 Exchange 的连接数有所增加。例如，Outlook 客户端会为每个使用中的共享日历打开最多两个其他连接。在这种情况下，请确保出口代理可以处理这些连接，或者对 Outlook 不使用代理以连接到 Office 365。
    
4. 确定的公共 IP 地址的受支持设备的最大数量以及如何跨多个 IP 地址负载平衡。有关详细信息，请参阅[Office 365 的 NAT 支持](nat-support-with-office-365.md)。
    
5. 如果网络上，要检查的计算机的出站连接，绕过此筛选到 Office 365 域将以下措施改善连接性和性能。此外，绕过出站检查通常删除单个的 Internet 出口需要和允许的发往的 Office 365 网络请求的本地 Internet 出口。
    
6. 某些客户发现内部网络设置可能会影响性能。设置最大传输单元 (MTU) 大小，如网络自动协商或自动检测和不够理想路由到 Internet 的查看常见位置。
    
## <a name="network-planning-reference-for-office-365"></a>Office 365 的网络规划参考
<a name="NetReference"> </a>

这些主题包含 Office 365 网络引用的详细的信息。
  
- [管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [客户端连接](client-connectivity.md)
    
- [内容传递网络](content-delivery-networks.md)
    
- [Office 365 的外部域名系统记录](external-domain-name-system-records.md)
    
- [Office 365 服务中的 IPv6 支持](ipv6-support.md)
    
- [Office 365 网络连接原则](https://aka.ms/o365networkingprinciples)
    
- [Microsoft 虚拟学院： Office 365 性能管理](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [Office 365 视频网络经常常见问题 (FAQ)](office-365-video-networking-faq.md)
    
- [有关连接到 Office 365 服务的网络设备的计划](plan-for-network-devices.md)
    
- [Office 365 服务的部署顾问](deployment-advisors-for-office-365.md)
    

