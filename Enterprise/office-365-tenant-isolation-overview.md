---
title: Office 365 中的租户隔离
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
description: Microsoft 对 Office 365 强制实施租户隔离的方式的摘要。
ms.openlocfilehash: 4859fd5feec50159e71ca2ca8968388c5ab82d64
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067233"
---
# <a name="tenant-isolation-in-office-365"></a>Office 365 中的租户隔离

云计算的主要优势之一是多个客户之间共享的通用基础结构的概念，从而导致规模经济。 此概念称为*多租户*。 Microsoft 连续工作，以确保云服务的多租户体系结构支持企业级安全性、机密性、隐私、完整性和可用性标准。

根据可[信赖的计算](https://www.microsoft.com/en-us/twc/default.aspx)和[安全开发生命周期](http://www.microsoft.com/security/sdl/default.aspx)收集到的大量投资和经验，Microsoft 云服务的设计假定所有租户都有可能与所有租户进行恶意其他租户，我们已经实施了安全措施，以防止一个租户的操作影响另一个租户的安全或服务，或访问其他租户的内容。

在多租户环境中维护租户隔离的两个主要目标是：
1.  防止对租户之间的客户内容的泄露或未经授权访问;并
2.  防止一个租户的操作对另一个租户的服务产生不利影响

在整个 Office 365 中实施了多种形式的保护，以防止客户损害 Office 365 服务或应用程序，或未经授权访问其他租户或 Office 365 系统本身的信息，其中包括：
- 通过 Azure Active Directory 授权和基于角色的访问控制实现每个租户中的客户内容在 Office 365 服务中的逻辑隔离。
- SharePoint Online 在存储级别提供了数据隔离机制。
- Microsoft 使用严格的物理安全、背景屏蔽和多层加密策略来保护客户内容的机密性和完整性。 所有 Office 365 数据中心都具有生物特征访问控制，大多数情况下需要 palm 打印才能获得物理访问权限。 此外，所有基于美国的 Microsoft 员工都需要在聘用过程中成功完成标准背景检查。 有关 Office 365 中用于管理访问的控件的详细信息，请参阅[office 365 管理访问控制](office-365-administrative-access-controls-overview.md)。
- Office 365 使用服务端技术来加密 rest 和传输中的客户内容，包括 BitLocker、文件加密、传输层安全性（TLS）和 Internet 协议安全性（IPsec）。 有关 Office 365 中的加密的具体详细信息，请参阅[office 365 中的数据加密技术](/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview.md)。

上面列出的保护功能提供了可靠的逻辑隔离控制，它们提供了与独立的物理隔离提供的威胁防护和缓解等效项。

## <a name="related-links"></a>相关链接
- [Azure Active Directory 中的隔离和访问控制](office-365-isolation-in-azure-active-directory.md)
- [Office Graph 和 Delve 中的租户隔离](office-365-isolation-in-graph-and-delve.md)
- [Office 365 搜索中的租户隔离](office-365-isolation-in-office-365-search.md)
- [Office 365 视频中的租户隔离](office-365-isolation-in-office-365-video.md)
- [资源限制](office-365-resource-limits.md)
- [监视和测试租户边界](office-365-monitoring-and-testing.md)
- [Office 365 中的隔离和访问控制](office-365-isolation-in-office-365.md)