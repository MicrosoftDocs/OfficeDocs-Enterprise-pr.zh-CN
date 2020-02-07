---
title: Office 365 隔离控制
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
f1.keywords:
- NOCSH
description: 摘要： Office 365 中的隔离控件的说明。
ms.openlocfilehash: e5ce9f2b581c49f3c08803034bc526b2fdb91a9a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844443"
---
# <a name="office-365-isolation-controls"></a>Office 365 隔离控制 

Microsoft 连续工作，以确保 Office 365 的多租户体系结构支持企业级安全性、机密性、隐私、完整性、本地、国际和可用性[标准](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)。 Microsoft 提供的服务的规模和范围使其难以和非经济地管理 Office 365，从而实现显著的人工交互。 Office 365 服务通过多个全局分布式数据中心提供，每个都具有极大的自动化，需要人工触摸或任何对客户内容的访问。 我们的员工使用自动化工具和高度安全的远程访问支持这些服务和数据中心。 有关如何在 Office 365 中运行大规模服务的一些详细信息，请参阅[IT 专业人员在 office 365 中的幕后外观](https://channel9.msdn.com/Events/SharePoint-Conference/2014/SPC202)。

Office 365 由多个服务组成，这些服务可提供重要的业务功能并参与整个 Office 365 体验。 这些服务中的每一项都是独立的，旨在与另一项集成。

Office 365 的设计具有以下原则：

 - **[面向服务的体系结构](https://msdn.microsoft.com/library/aa480021.aspx)：** 以可互操作的服务的形式设计和开发软件，以提供完善定义的业务功能。
 - **[操作安全保证](https://www.microsoft.com/download/details.aspx?id=40872)：** 一种框架，其中包含通过 microsoft 独有的各种功能获得的知识，包括 Microsoft[安全开发生命周期](https://www.microsoft.com/sdl/default.aspx)、 [microsoft 安全响应中心](https://technet.microsoft.com/library/dn440717.aspx)和 cybersecurity 威胁的深层感知。

Office 365 服务之间相互进行互操作，但它们已经过设计和实现，以便可以将它们作为自治服务进行部署，并相互独立。 Microsoft segregates Office 365 的责任和职责范围，以减少对组织资产进行未经授权或无意的修改或误用的机会。 Office 365 团队已将角色定义为全面的基于角色的访问控制机制的一部分。

## <a name="customer-content-isolation"></a>客户内容隔离

租户中的所有客户内容都独立于其他租户以及 Office 365 管理中使用的操作和系统数据。 在整个 Office 365 中实施多种形式的保护，以最大限度地降低对任何 Office 365 服务或应用程序造成危害的风险。 多种形式的保护也会阻止对租户或 Office 365 系统本身的信息进行未经授权的访问。

有关 Microsoft 如何在 Office 365 中实现租户数据的逻辑隔离的信息，请参阅[office 365 中的租户隔离](office-365-tenant-isolation-overview.md)。
