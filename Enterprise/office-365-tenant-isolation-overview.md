---
title: Microsoft 365 中的租户隔离
ms.author: josephd
author: JoeDavies-MSFT
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
f1.keywords:
- NOCSH
description: 本文摘要介绍了 Microsoft 如何在云服务（如 Microsoft 365）中强制实施租户隔离。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 531b5023af49c776cccfef06dee5bff4b303beff
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606538"
---
# <a name="tenant-isolation-in-microsoft-365"></a>Microsoft 365 中的租户隔离

云计算的主要优势之一是多个客户之间共享的通用基础结构的概念，从而导致规模经济。 此概念称为*多租户*。 Microsoft 连续工作，以确保云服务的多租户体系结构支持企业级安全性、机密性、隐私、完整性和可用性标准。

根据可[信赖的计算](https://www.microsoft.com/trust-center)和[安全开发生命周期](https://www.microsoft.com/securityengineering/sdl/)收集到的重要投资和经验，Microsoft 云服务设计为假设所有租户都有可能与所有其他租户有敌意，并实施了安全措施以防止一个租户的操作影响另一个租户的安全或服务，或访问其他租户的内容。

在多租户环境中维护租户隔离的两个主要目标是：

1.    防止对租户之间的客户内容的泄露或未经授权访问;并
2.    防止一个租户的操作对另一个租户的服务产生不利影响

在整个 Microsoft 365 中实施了多种形式的保护，以防止客户损害 Microsoft 365 服务或应用程序，或未经授权访问其他租户或 Microsoft 365 系统本身的信息，其中包括：

- 通过 Azure Active Directory 授权和基于角色的访问控制实现 Microsoft 365 服务中每个租户内的客户内容的逻辑隔离。
- SharePoint Online 在存储级别提供了数据隔离机制。
- Microsoft 使用严格的物理安全、背景屏蔽和多层加密策略来保护客户内容的机密性和完整性。 所有 Microsoft 365 数据中心都具有生物特征访问控制，大多数情况下需要 palm 打印才能获得物理访问权限。 此外，所有基于美国的 Microsoft 员工都需要在聘用过程中成功完成标准背景检查。 有关在 Microsoft 365 中用于管理访问的控件的详细信息，请参阅[microsoft 365 管理访问控制](office-365-administrative-access-controls-overview.md)。
- Microsoft 365 使用服务端技术来加密 rest 和传输中的客户内容，包括 BitLocker、文件加密、传输层安全性 (TLS) 和 Internet 协议安全 (IPsec) 。 有关 Microsoft 365 中的加密的具体详细信息，请参阅[microsoft 365 中的数据加密技术](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview)。

上面列出的保护功能提供了可靠的逻辑隔离控制，它们提供了与独立的物理隔离提供的威胁防护和缓解等效项。

## <a name="related-links"></a>相关链接

- [Azure Active Directory 中的隔离和访问控制](office-365-isolation-in-azure-active-directory.md)
- [Office Graph 和 Delve 中的租户隔离](office-365-isolation-in-graph-and-delve.md)
- [Microsoft 365 搜索中的租户隔离](office-365-isolation-in-office-365-search.md)
- [Office 365 视频中的租户隔离](office-365-isolation-in-office-365-video.md)
- [资源限制](office-365-resource-limits.md)
- [监视和测试租户边界](office-365-monitoring-and-testing.md)
- [Microsoft 365 中的隔离和访问控制](office-365-isolation-in-office-365.md)
