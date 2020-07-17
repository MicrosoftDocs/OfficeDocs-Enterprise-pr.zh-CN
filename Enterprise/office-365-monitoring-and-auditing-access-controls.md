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
# <a name="monitoring-and-auditing-access-controls-in-microsoft-365"></a><span data-ttu-id="8bdcf-103">在 Microsoft 365 中监视和审核访问控制</span><span class="sxs-lookup"><span data-stu-id="8bdcf-103">Monitoring and Auditing Access Controls in Microsoft 365</span></span>

<span data-ttu-id="8bdcf-104">Microsoft 对在 Microsoft 365 中发生的所有委派、特权和操作执行全面的监视和审核。</span><span class="sxs-lookup"><span data-stu-id="8bdcf-104">Microsoft performs extensive monitoring and auditing of all delegation, privileges, and operations that occur within Microsoft 365.</span></span> <span data-ttu-id="8bdcf-105">Microsoft 365 访问控制是基于最小特权原则生成的自动化过程，其中包含数据访问控制和审核：</span><span class="sxs-lookup"><span data-stu-id="8bdcf-105">Microsoft 365 access control is an automated process built on the principle of least privilege and incorporating data access controls and audits:</span></span>

- <span data-ttu-id="8bdcf-106">所有允许的访问都可供唯一用户跟踪。</span><span class="sxs-lookup"><span data-stu-id="8bdcf-106">All permitted access is traceable to a unique user.</span></span> <span data-ttu-id="8bdcf-107">管理员负责处理客户内容。</span><span class="sxs-lookup"><span data-stu-id="8bdcf-107">Administrators are accountable for their handling of customer content.</span></span>
- <span data-ttu-id="8bdcf-108">捕获访问控制请求、审批和管理操作日志，以分析安全和恶意事件。</span><span class="sxs-lookup"><span data-stu-id="8bdcf-108">Access control requests, approvals, and administrative operations logs are captured for analysis of security and malicious events.</span></span>
- <span data-ttu-id="8bdcf-109">根据安全组成员身份，在接近实时的情况中查看访问级别，以确保只有具有授权的业务理由并满足资格要求的用户才有权访问系统。</span><span class="sxs-lookup"><span data-stu-id="8bdcf-109">Access levels are reviewed in near real-time based on security group membership to ensure that only users who have authorized business justifications and meet the eligibility requirements have access to the systems.</span></span>
- <span data-ttu-id="8bdcf-110">Microsoft 365，其访问控制和支持服务（包括 Azure Active Directory 和物理数据中心）定期通过独立第三方进行审核，以符合[ISO/IEC 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001)、 [ISO/iec 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018)、 [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC)、 [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP)和其他[标准](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)。</span><span class="sxs-lookup"><span data-stu-id="8bdcf-110">Microsoft 365, its access controls, and supporting services, including Azure Active Directory and physical datacenters, are regularly audited by independent third-parties for compliance with [ISO/IEC 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001), [ISO/IEC 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018), [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC), [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP), and other [standards](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons).</span></span>
- <span data-ttu-id="8bdcf-111">Microsoft 365 工程师必须参加每年一次安全培训，查看提升的访问最佳步骤，并确认 Microsoft 的安全和隐私政策，以维持对服务的权利。</span><span class="sxs-lookup"><span data-stu-id="8bdcf-111">Microsoft 365 engineers must take yearly security training, review elevated access best procedures, and acknowledge Microsoft's security and privacy policies to maintain entitlements to the service.</span></span>

<span data-ttu-id="8bdcf-112">当检测到可疑活动（如短时间内的多个失败的登录）时，自动通知会触发。</span><span class="sxs-lookup"><span data-stu-id="8bdcf-112">Automated alerts trigger when suspicious activity is detected, such as multiple failed logins within a short period.</span></span> <span data-ttu-id="8bdcf-113">Microsoft 365 安全响应团队使用机器学习和大型数据分析来查看和分析活动、查找不规则的访问模式并主动响应异常和违法活动。</span><span class="sxs-lookup"><span data-stu-id="8bdcf-113">The Microsoft 365 Security Response team uses machine learning and big data analysis to review and analyze activity, look for irregular access patterns, and proactively respond to anomalous and illicit activities.</span></span> <span data-ttu-id="8bdcf-114">Microsoft 还采用了一组专门的渗透测试人员，并参与定期的红色团队和蓝色的团队练习，以查找服务中的安全性和访问控制问题。</span><span class="sxs-lookup"><span data-stu-id="8bdcf-114">Microsoft also employs a dedicated team of penetration testers and engages in periodic Red Team and Blue Team exercises to find security and access control issues in the service.</span></span> <span data-ttu-id="8bdcf-115">客户可以通过使用由 Microsoft 365 提供的审核报告和管理活动 API 来验证访问控制系统的有效性。</span><span class="sxs-lookup"><span data-stu-id="8bdcf-115">Customers can verify the effectiveness of access control systems by using audit reports and the management activity API provided by Microsoft 365.</span></span>

<span data-ttu-id="8bdcf-116">有关详细信息，请参阅 Microsoft 365 中的[Office 365 管理活动 API 参考](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference)和[审核与报告](office-365-auditing-and-reporting-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="8bdcf-116">For more information, see [Office 365 Management Activity API reference](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference) and [Auditing and reporting in Microsoft 365](office-365-auditing-and-reporting-overview.md).</span></span>
