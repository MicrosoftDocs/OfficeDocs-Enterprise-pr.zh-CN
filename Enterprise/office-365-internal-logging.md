---
title: Office 365 Office 365 工程的内部日志记录
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
description: 有关 Office 365 工程团队的内部日志记录如何工作的说明。
ms.openlocfilehash: 3f0a65b618e34e5bba92a0f0b471c5c7c43bb329
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035522"
---
# <a name="internal-logging-for-office-365-engineering"></a><span data-ttu-id="fb7ca-103">Office 365 工程团队的内部日志记录</span><span class="sxs-lookup"><span data-stu-id="fb7ca-103">Internal Logging for Office 365 Engineering</span></span>

<span data-ttu-id="fb7ca-104">除了可用于客户的事件和日志数据之外，Office 365 工程师还提供了内部日志数据收集系统。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-104">In addition to the events and log data available for customers, there is also an internal log data collection system that is available to Office 365 engineers.</span></span> <span data-ttu-id="fb7ca-105">许多不同类型的日志数据将从 Office 365 服务器上传到内部的大型数据计算服务（称为 Cosmos）。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-105">Many different types of log data are uploaded from Office 365 servers to an internal, big data computing service called Cosmos.</span></span> <span data-ttu-id="fb7ca-106">每个服务团队将审核日志从各自的服务器上载到 Cosmos 数据库中，以进行聚合和分析。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-106">Each service team uploads audit logs from their respective servers into the Cosmos database for aggregation and analysis.</span></span> <span data-ttu-id="fb7ca-107">此数据传输通过经过专用的自动化工具（称为 Office 数据加载程序（ODL））在专门批准的端口和协议上进行 FIPS 140-2 验证的 TLS 连接。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-107">This data transfer occurs over a FIPS 140-2-validated TLS connection on specifically approved ports and protocols using a proprietary automation tool called the Office Data Loader (ODL).</span></span> <span data-ttu-id="fb7ca-108">Office 365 中用于收集和处理审核记录的工具不允许对原始审核记录的内容或时间排序进行永久或不可恢复的更改。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-108">The tools used in Office 365 to collect and process audit records do not allow permanent or irreversible changes to the original audit record content or time ordering.</span></span>

<span data-ttu-id="fb7ca-109">服务团队使用 Cosmos 作为一个集中存储库来对应用程序使用情况进行分析，以衡量系统和操作性能，并查找可能指示问题或安全问题的 abnormalities 和模式。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-109">Service teams use Cosmos as a centralized repository to conduct an analysis of application usage, to measure system and operational performance, and to look for abnormalities and patterns that may indicate problems or security issues.</span></span> <span data-ttu-id="fb7ca-110">每个服务团队将日志的基准上载到 Cosmos，具体取决于他们要分析的内容，这通常包括：</span><span class="sxs-lookup"><span data-stu-id="fb7ca-110">Each service team uploads a baseline of logs into Cosmos, depending on what they are looking to analyze, that often include:</span></span>

- <span data-ttu-id="fb7ca-111">事件日志</span><span class="sxs-lookup"><span data-stu-id="fb7ca-111">Event logs</span></span>
- <span data-ttu-id="fb7ca-112">AppLocker 日志</span><span class="sxs-lookup"><span data-stu-id="fb7ca-112">AppLocker logs</span></span>
- <span data-ttu-id="fb7ca-113">性能数据</span><span class="sxs-lookup"><span data-stu-id="fb7ca-113">Performance data</span></span>
- <span data-ttu-id="fb7ca-114">System Center data</span><span class="sxs-lookup"><span data-stu-id="fb7ca-114">System Center data</span></span>
- <span data-ttu-id="fb7ca-115">呼叫详细信息记录</span><span class="sxs-lookup"><span data-stu-id="fb7ca-115">Call detail records</span></span>
- <span data-ttu-id="fb7ca-116">经验数据的质量</span><span class="sxs-lookup"><span data-stu-id="fb7ca-116">Quality of experience data</span></span>
- <span data-ttu-id="fb7ca-117">IIS Web 服务器日志</span><span class="sxs-lookup"><span data-stu-id="fb7ca-117">IIS Web Server logs</span></span>
- <span data-ttu-id="fb7ca-118">SQL Server 日志</span><span class="sxs-lookup"><span data-stu-id="fb7ca-118">SQL Server logs</span></span>
- <span data-ttu-id="fb7ca-119">Syslog 数据</span><span class="sxs-lookup"><span data-stu-id="fb7ca-119">Syslog data</span></span>
- <span data-ttu-id="fb7ca-120">安全审核日志</span><span class="sxs-lookup"><span data-stu-id="fb7ca-120">Security audit logs</span></span>

<span data-ttu-id="fb7ca-121">在将数据上载到 Cosmos 中之前，ODL 应用程序使用清理服务来模糊处理包含客户数据（如租户信息和最终用户身份信息）的任何字段，并将这些字段替换为哈希值。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-121">Prior to uploading data into Cosmos, the ODL application uses a scrubbing service to obfuscate any fields that contain customer data, such as tenant information and end-user identifiable information, and replace those fields with a hash value.</span></span> <span data-ttu-id="fb7ca-122">重写匿名和哈希日志，然后将其上载到 Cosmos。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-122">The anonymized and hashed logs are rewritten and then uploaded into Cosmos.</span></span> <span data-ttu-id="fb7ca-123">服务团队针对 Cosmos 中的数据在关联、警报和报告方面运行作用域内查询。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-123">Service teams run scoped queries against their data in Cosmos for correlation, alerting, and reporting.</span></span> <span data-ttu-id="fb7ca-124">Cosmos 中的审核日志数据保留期由服务团队决定;大多数审核日志数据会保留90天或更长的时间，以支持安全事件调查并满足法规保留要求。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-124">The period of audit log data retention in Cosmos is determined by the service teams; most audit log data is retained for 90 days or longer to support security incident investigations and to meet regulatory retention requirements.</span></span>

<span data-ttu-id="fb7ca-125">对存储在 Cosmos 中的 Office 365 数据的访问权限仅限于已授权的人员。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-125">Access to Office 365 data stored in Cosmos is restricted to authorized personnel.</span></span> <span data-ttu-id="fb7ca-126">Microsoft 将审核功能的管理限制为负责审核功能的服务团队成员的有限子集。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-126">Microsoft restricts the management of audit functionality to the limited subset of service team members that are responsible for audit functionality.</span></span> <span data-ttu-id="fb7ca-127">这些团队成员不能修改或删除 Cosmos 中的数据，并且会记录和审核对 Cosmos 的日志记录机制所做的所有更改。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-127">These team members do not have the ability to modify or delete data from Cosmos, and all changes to logging mechanisms for Cosmos are recorded and audited.</span></span>

<span data-ttu-id="fb7ca-128">每个服务团队通过授权某些应用程序进行特定分析来访问其日志数据以供分析。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-128">Each service team accesses its log data for analysis by authorizing certain applications to conduct specific analysis.</span></span> <span data-ttu-id="fb7ca-129">例如，Office 365 安全团队通过专有事件日志分析器使用 Cosmos 中的数据来关联、通知和生成可操作报告，以了解 Office 365 生产环境中可能存在的可疑活动。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-129">For example, the Office 365 Security team uses data from Cosmos through a proprietary event log parser to correlate, alert, and generate actionable reports on possible suspicious activity in the Office 365 production environment.</span></span> <span data-ttu-id="fb7ca-130">这些数据中的报告用于更正漏洞，并可提高服务的整体性能。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-130">The reports from this data are used to correct vulnerabilities, and to improve the overall performance of the service.</span></span> <span data-ttu-id="fb7ca-131">如果特定警报或报告需要进一步调查，服务人员可以请求将数据导入回 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-131">If a specific alert or report requires further investigation, service personnel can request that data be imported back into the Office 365 service.</span></span> <span data-ttu-id="fb7ca-132">由于要从 Cosmos 导入的特定日志是加密的，并且服务人员不具有解密密钥的访问权限，因此目标日志以编程方式传递给授权服务人员的解密服务返回范围的结果。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-132">Since the specific log being imported from Cosmos is in encrypted and service personnel do not have access to decryption keys, the target log is programmatically passed through a decryption service that returns scoped results to the authorized service personnel.</span></span> <span data-ttu-id="fb7ca-133">将使用 Microsoft 的标准安全事件管理渠道报告和升级从本练习中发现的任何漏洞。</span><span class="sxs-lookup"><span data-stu-id="fb7ca-133">Any vulnerabilities found from this exercise are reported and escalated using Microsoft's standard security incident management channels.</span></span>
