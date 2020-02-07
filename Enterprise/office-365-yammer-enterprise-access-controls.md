---
title: Office 365 Yammer 企业访问控制
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
description: 摘要：有关生产环境中 Yammer 企业访问控制的简要摘要。
ms.openlocfilehash: 9b88ff0f8c480dd3726246e47714d9468509ef08
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841789"
---
# <a name="yammer-enterprise-access-controls"></a>Yammer Enterprise访问控制 

对 Yammer 生产环境的物理和逻辑访问仅限于一小部分人员（基础结构和操作）。 与其他 Office 365 工程师一样，Yammer 工程师可以获得对客户数据的零访问权限。 必须使用基于审批的实时访问控制系统请求访问，这类似于具有有限数量的审批者的密码箱。 审批者验证请求（例如，他们根据需求、业务案例、时间等验证请求是否合法），然后批准或拒绝该请求。 如果请求得到批准，则会为已定义和有限的时间授予 JIT 访问权限。 超出访问时间后，访问将自动过期。

与其他 Office 365 服务一样，对 Yammer 生产环境的所有访问都将使用多重身份验证。 所有访问和命令历史记录都属于用户，并定期由 Yammer 安全团队记录和查看。

有关 Yammer 管理和管理的详细信息，请参阅[Yammer 管理员帮助](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US)。