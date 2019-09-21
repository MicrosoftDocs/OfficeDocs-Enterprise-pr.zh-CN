---
title: Office 365 针对拒绝服务攻击防御云服务
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Microsoft 如何抵御拒绝服务（DoS）攻击的云服务。
ms.openlocfilehash: ad15349832c36a7dceae59503055606999a3193c
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067235"
---
# <a name="defending-microsoft-cloud-services-against-denial-of-service-attacks"></a>防御拒绝服务攻击的 Microsoft 云服务

## <a name="introduction"></a>简介
Microsoft 数据中心受纵深防御安全保护，其中包括外围防护、视频相机、安全人员和使用生物特征、智能卡和多因素身份验证的安全入口。 纵深防御安全在设备的每个区域和每个物理服务器单元继续进行。 [Microsoft 云基础结构和操作组](https://www.microsoft.com/en-us/cloud-platform/global-datacenters)为云服务提供了核心基础结构和基础技术。 我们的数据中心符合物理安全性和可靠性的行业标准，由 Microsoft 操作人员管理、监视和管理。

为了进一步保护我们的云服务，Microsoft 提供了一种 DDoS 防御系统，这是 Microsoft Azure 持续监控和渗透测试过程的一部分。 Azure DDoS 防御系统不仅用于抵御来自外部的攻击，还能抵御来自其他 Azure 租户的攻击。 Azure 使用标准检测和缓解技术，如 SYN cookie、速率限制和连接限制，以防止出现 DDoS 攻击。

Microsoft 的云服务受来自多个来源的攻击的威胁。 为了缓解和防范各种 DoS 威胁，我们已经开发并实施了一个高度可扩展且动态基于 Azure 的威胁检测和缓解系统，其主要目标是从 DoS 保护底层基础结构攻击和帮助防止云服务客户的服务中断。 Azure DoS 缓解系统可保护入站、出站和区域到区域的流量。

对[开放式系统互连](https://docs.microsoft.com/windows-hardware/drivers/network/windows-network-architecture-and-the-osi-model)（OSI）模型的网络（L3）和传输（L4）层上的目标启动的大多数 DoS 攻击。 在 L3 和 L4 层上定向的攻击旨在使网络接口或服务面临大量资源的攻击流量，并拒绝对合法流量做出响应的能力。 具体来说，L3 和 L4 攻击尝试将网络链接、设备或服务的容量饱和，或者使支持应用程序的服务器或虚拟机的 Cpu 发生不足。

为防止 L3 和 L4 攻击，Microsoft 设计、开发和部署了一个解决方案，该解决方案专门针对通过保护这些层来保护受攻击的基础结构和客户目标。 保护基础结构可确保面向某个客户的攻击流量不会导致对其他客户的宣传资料损坏或网络服务质量降低。 解决方案使用数据中心路由器的流量采样数据。 此数据由网络监控服务进行分析以检测攻击。 检测到攻击时，自动防护机制会启动。

## <a name="application-level-defenses"></a>应用程序级别防御
Microsoft 工程团队遵循[Microsoft 操作安全保障](https://www.microsoft.com/en-us/SDL/OperationalSecurityAssurance)所设置的严格标准，以帮助保护客户数据。 Microsoft 的云服务是专门为支持非常高的负载而构建的，并且可以针对应用程序级别的 DoS 攻击进行保护和缓解。 我们实施了一个扩展体系结构，其中的服务分布在多个全球数据中心，其中一些工作负载中的区域隔离和限制功能。

在服务的初始安装过程中，客户管理员标识的每个客户的国家或地区决定了该客户的数据的主存储位置。 根据主/备份策略在冗余数据中心之间复制客户数据。 主数据中心将应用程序软件与在软件上运行的所有主要客户数据一起承载。 备份数据中心提供自动故障转移。 如果由于任何原因而导致主数据中心停止运行，则会将请求重定向到备份数据中心中的软件和客户数据的副本。 在任何给定时间，客户数据可能会在主数据中心或备份数据中心中进行处理。 跨多个数据中心分布数据可在一个数据中心受到攻击时减少受影响的表面区域。 此外，受影响的数据中心中的服务可以作为恢复机制之一快速重定向到辅助数据中心，反之亦然（重定向回一次服务后重定向到主数据中心）。

各个工作负载包含管理资源利用率的内置功能。 例如，Exchange Online 和 SharePoint Online 中的限制机制是用于防御 DoS 攻击的多层方法的一部分。 Exchange Online 用户的限制基于最终用户消耗的资源的级别，无论资源是处于 Active Directory、Exchange Online 信息存储还是其他地方。 将预算分配给每个客户端，以限制用户消耗的资源。 对用户活动和系统组件的 Exchange Online 限制基于[工作负载管理](http://technet.microsoft.com/en-us/library/jj150503(v=exchg.150).aspx)。 Exchange Online 工作负载是为 Exchange Online 系统资源管理明确定义的 Exchange Online 功能、协议或服务。 每个 Exchange Online 工作负载需要系统资源（如 CPU、邮箱数据库操作或 Active Directory 请求）来执行用户请求或后台工作。 Exchange Online 工作负载的示例包括 web 上的 Outlook、Exchange ActiveSync、邮箱迁移和邮箱助理。 租户管理员可以使用 Exchange 命令行管理程序管理用户的 Exchange 工作负荷管理限制设置。 在 Exchange Online 中实施了各种形式的限制，包括 PowerShell、Exchange Web 服务、POP 和 IMAP、Exchange ActiveSync、移动设备连接、收件人等。 虽然本地 Exchange 部署的管理员可以配置限制策略，但管理员无法为 Exchange Online 配置限制策略。

SharePoint Online 中最常见的限制触发是客户端对象模型（CSOM）代码，该代码在频率过高的情况中执行的操作过多。 使用 CSOM，可以通过单个请求执行许多操作，这会超过使用限制，并导致每用户限制。

无论可能导致限制的活动是什么，当用户超过使用限制时，SharePoint Online 将对来自该用户帐户的任何其他请求进行限制，通常较短一段时间。 在用户限制生效时，将限制该用户的所有操作，直到限制过期，具体取决于以下条件：
- 对于用户直接在浏览器中执行的请求，SharePoint Online 将重定向到限制信息页面，请求将失败。
- 对于所有其他请求（包括 CSOM 调用），SharePoint Online 将返回 HTTP 状态代码429（"请求过多"），请求失败。

如果有问题的过程仍超过使用限制，SharePoint Online 可能会完全阻止进程并返回 HTTP 状态代码503（"服务不可用"）。

## <a name="vulnerability-and-penetration-testing"></a>漏洞和渗透测试
Microsoft 使用多种[安全技术和做法](https://www.microsoft.com/en-us/trustcenter/security/threatmanagement)针对新式复杂威胁[保护其云基础结构](https://blogs.technet.microsoft.com/hybridcloud/2015/05/05/protecting-your-datacenter-and-cloud-from-emerging-threats/)和本地网络，包括对云服务使用反恶意软件组件和服务、虚拟计算机（Vm）和其他系统。 高级威胁分析，它监视网络、系统和用户的正常使用模式，并使用机器学习来标记出不正常且常规渗透测试的任何行为。

除了执行我们自己的渗透测试并向我们的客户提供[Microsoft 云统一渗透测试计划](https://technet.microsoft.com/en-us/mt784683)之外，我们还将参与第三方安全专业人员，他们将定期执行漏洞评估并针对云服务的渗透测试。 我们将从[服务信任](https://aka.ms/STP)和[服务保证](https://aka.ms/ServiceAssurance)门户下载这些第三方漏洞评估中的报告。
