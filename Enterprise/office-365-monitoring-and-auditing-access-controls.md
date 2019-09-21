---
title: Office 365 监控和审核访问控制
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
description: 摘要： Office 365 中可用的各种监视和审核访问控件的摘要。
ms.openlocfilehash: 00f0032afa85905ed5b1e0c4e016ea218207fc34
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067201"
---
# <a name="monitoring-and-auditing-access-controls-in-office-365"></a>监视和审核 Office 365 中的访问控件

Microsoft 对 Office 365 中发生的所有委派、特权和操作执行全面的监视和审核。 Office 365 访问控制是基于最小特权原则构建的自动化过程，并包含数据访问控制和审核：

- 所有允许的访问都可供唯一用户跟踪。 管理员负责处理客户内容。
- 捕获访问控制请求、审批和管理操作日志，以分析安全和恶意事件。
- 根据安全组成员身份，在接近实时的情况中查看访问级别，以确保只有具有授权的业务理由并满足资格要求的用户才有权访问系统。
- Office 365、其访问控制和支持服务（包括 Azure Active Directory 和物理数据中心）定期通过独立第三方进行审核，以实现[ISO/IEC 27001](https://www.microsoft.com/en-us/TrustCenter/Compliance/iso-iec-27001)、 [iso/iec 27018](https://www.microsoft.com/en-us/TrustCenter/Compliance/iso-iec-27018)、 [SOC](https://www.microsoft.com/en-us/TrustCenter/Compliance/SOC)、 [FedRAMP](https://www.microsoft.com/en-us/TrustCenter/Compliance/FedRAMP)和其他[标准](https://www.microsoft.com/en-us/TrustCenter/Compliance?service=Office#Icons)。
- Office 365 工程师必须参加年度安全培训，查看提升的访问最佳步骤，并确认 Microsoft 的安全和隐私政策，以维持对服务的权利。

当检测到可疑活动（如短时间内的多个失败的登录）时，自动通知会触发。 Office 365 安全响应团队使用机器学习和大型数据分析来查看和分析活动、查找不规则的访问模式并主动响应异常和违法活动。 Microsoft 还采用了一组专门的渗透测试人员，并参与定期的红色团队和蓝色的团队练习，以查找服务中的安全性和访问控制问题。 客户可以通过使用由 Office 365 提供的审核报告和管理活动 API 来验证访问控制系统的有效性。

有关详细信息，请参阅 Office [365 管理活动 API 参考](https://msdn.microsoft.com/en-us/library/office/mt227394.aspx)和[office 365 中的审核与报告](office-365-auditing-and-reporting-overview.md)。
