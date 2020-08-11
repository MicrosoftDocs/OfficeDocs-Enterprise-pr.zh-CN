---
title: Microsoft 365 隔离控件
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
description: 了解隔离控制在 Microsoft 365 中的工作方式，允许服务在需要时进行操作或保持自治。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: da49d19371c0b7f704bf7cb1c4c83205b9cc9cb0
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605614"
---
# <a name="microsoft-365-isolation-controls"></a>Microsoft 365 隔离控件 

Microsoft 连续工作，以确保 Microsoft 365 的多租户体系结构支持企业级安全性、机密性、隐私、完整性、本地、国际和可用性[标准](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)。 Microsoft 提供的服务的规模和范围使其难以和非经济地管理 Microsoft 365，从而实现显著的人工交互。 Microsoft 365 服务通过多个全局分布式数据中心提供，每个都以高自动化方式进行，其中几个操作需要人工触摸或对客户内容的任何访问。 我们的员工使用自动化工具和高度安全的远程访问支持这些服务和数据中心。 

Microsoft 365 由多个服务组成，这些服务提供重要的业务功能并参与整个 Microsoft 365 体验。 这些服务中的每一项都是独立的，旨在与另一项集成。

Microsoft 365 的设计原则如下：

 - **[面向服务的体系结构](https://docs.microsoft.com/previous-versions/aa480021(v=msdn.10))：** 以可互操作的服务的形式设计和开发软件，以提供完善定义的业务功能。
 - **[操作安全保证](https://www.microsoft.com/download/details.aspx?id=40872)：** 一种框架，其中包含通过 microsoft 独有的各种功能获得的知识，包括 Microsoft[安全开发生命周期](https://www.microsoft.com/sdl/default.aspx)、 [microsoft 安全响应中心](https://technet.microsoft.com/library/dn440717.aspx)和 cybersecurity 威胁的深层感知。

Microsoft 365 服务之间相互进行互操作，但这些服务是专门设计和实施的，因此它们可以独立于自治服务进行部署和操作。 Microsoft segregates 对 Microsoft 365 的责任和责任范围，以减少对组织资产进行未经授权或无意的修改或误用的机会。 Microsoft 365 团队已将角色定义为全面的基于角色的访问控制机制的一部分。

## <a name="customer-content-isolation"></a>客户内容隔离

租户中的所有客户内容都独立于其他租户以及 Microsoft 365 管理中使用的操作和系统数据。 在整个 Microsoft 365 中实施了多种形式的保护，以最大限度地降低泄露任何 Microsoft 365 服务或应用程序的风险。 多种形式的保护也会阻止对租户或 Microsoft 365 系统本身的信息进行未经授权的访问。

有关 Microsoft 如何在 Microsoft 365 中实现租户数据的逻辑隔离的信息，请参阅[microsoft 365 中的租户隔离](office-365-tenant-isolation-overview.md)。
