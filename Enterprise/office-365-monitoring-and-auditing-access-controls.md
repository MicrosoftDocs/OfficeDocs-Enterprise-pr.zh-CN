---
title: Microsoft 365 监视和审核访问控制
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
description: 摘要： Microsoft 365 中可用的各种监视和审核访问控件的摘要。
ms.openlocfilehash: aba1a9966cf50735ba3348fe126d7b4c9233b4b2
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774867"
---
# <a name="monitoring-and-auditing-access-controls-in-microsoft-365"></a>在 Microsoft 365 中监视和审核访问控制

Microsoft 对在 Microsoft 365 中发生的所有委派、特权和操作执行全面的监视和审核。 Microsoft 365 访问控制是基于最小特权原则生成的自动化过程，其中包含数据访问控制和审核：

- 所有允许的访问都可供唯一用户跟踪。 管理员负责处理客户内容。
- 捕获访问控制请求、审批和管理操作日志，以分析安全和恶意事件。
- 根据安全组成员身份，在接近实时的情况中查看访问级别，以确保只有具有授权的业务理由并满足资格要求的用户才有权访问系统。
- Microsoft 365，其访问控制和支持服务（包括 Azure Active Directory 和物理数据中心）定期通过独立第三方进行审核，以符合[ISO/IEC 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001)、 [ISO/iec 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018)、 [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC)、 [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP)和其他[标准](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)。
- Microsoft 365 工程师必须参加每年一次安全培训，查看提升的访问最佳步骤，并确认 Microsoft 的安全和隐私政策，以维持对服务的权利。

当检测到可疑活动（如短时间内的多个失败的登录）时，自动通知会触发。 Microsoft 365 安全响应团队使用机器学习和大型数据分析来查看和分析活动、查找不规则的访问模式并主动响应异常和违法活动。 Microsoft 还采用了一组专门的渗透测试人员，并参与定期的红色团队和蓝色的团队练习，以查找服务中的安全性和访问控制问题。 客户可以通过使用由 Microsoft 365 提供的审核报告和管理活动 API 来验证访问控制系统的有效性。

有关详细信息，请参阅 Microsoft 365 中的[Office 365 管理活动 API 参考](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference)和[审核与报告](office-365-auditing-and-reporting-overview.md)。
