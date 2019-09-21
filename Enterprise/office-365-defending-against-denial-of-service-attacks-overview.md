---
title: 防御 Office 365 中的拒绝服务攻击
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
description: 拒绝服务（DoS）攻击概述。
ms.openlocfilehash: 55fffccfc59f13d32cdd19930320c1df1cf58461
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067238"
---
# <a name="defend-against-denial-of-service-attacks-in-office-365"></a>防御 Office 365 中的拒绝服务攻击

## <a name="introduction"></a>简介

对于托管在超过100个数据中心的全球云基础结构中的200云服务，Microsoft 提供了一个可信赖的基础结构。 具体包括：

- Microsoft Azure
- Microsoft Bing
- Microsoft Dynamics 365
- Microsoft Office 365
- Microsoft OneDrive
- Skype
- Xbox Live

作为具有大量 Internet 状态以及提供云服务的显著 Internet 属性的全球组织，Microsoft 是黑客和其他恶意用户的一个大型、常见的目标。 客户端和 Microsoft 云之间的网络通信层是恶意攻击的最大目标之一。 事实上，Microsoft 持续且永久地采用某种形式的基于网络的 cyberattack。 根据这一点，Microsoft 使用纵深防御安全原则来保护其云服务和网络。 如果没有可靠且持久的缓解系统防御这些攻击，Microsoft 的云服务将处于脱机状态，并且对客户不可用。

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a>拒绝服务攻击的定义和症状

攻击网络服务的一种方法是，创建多个针对服务主机的请求，以使网络和服务器严重遭受向合法用户授予服务的攻击。 这称为拒绝服务（DoS）攻击。 当多个参与者、终结点和/或向量执行攻击时，它称为分布式拒绝服务（DDoS）攻击。 尽管方法、motives 和目标各不相同，但 DoS 和 DDoS 攻击通常都是为了防止 Internet 站点或服务正常运行，或者暂时或无限期。

[美国计算机紧急就绪团队](https://www.us-cert.gov/)（美国-CERT）定义 DoS 攻击的症状，以包括：

- 网络性能异常慢（打开文件或访问 Internet 站点时）
- 网站不可用
- 无法访问网站
- 收到的垃圾邮件大大增加
- 断开无线连接或有线 Internet 连接
- 长期失去对 Web 或任何 Internet 服务的访问权限

## <a name="related-topics"></a>相关主题

- [防御拒绝服务攻击的核心原则](office-365-core-principles-of-defense-against-dos-attacks.md)
- [Microsoft 的拒绝服务防御策略](office-365-microsoft-dos-defense-strategy.md)
- [防御拒绝服务攻击的 Microsoft 云服务](office-365-defending-cloud-services-against-dos-attacks.md)
