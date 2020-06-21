---
title: Microsoft 365 工程版的 microsoft 365 内部日志记录
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
description: Microsoft 365 工程的内部日志记录的工作原理的说明。
ms.openlocfilehash: 09e0d2910a71cbcae9db0b75193cc5d672914737
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774917"
---
# <a name="internal-logging-for-microsoft-365-engineering"></a>Microsoft 365 工程的内部日志记录

除了可供客户使用的事件和日志数据之外，microsoft 365 工程师还可以使用 Microsoft 的内部日志数据收集系统。 将许多不同类型的日志数据从 Microsoft 365 服务器上传到内部的大型数据计算服务（称为 Cosmos）。 每个服务团队将审核日志从各自的服务器上载到 Cosmos 数据库中，以进行聚合和分析。 此数据传输通过经过专用的自动化工具（称为 Office 数据加载程序（ODL））在专门批准的端口和协议上进行 FIPS 140-2 验证的 TLS 连接。 Microsoft 365 中用于收集和处理审核记录的工具不允许对原始审核记录的内容或时间排序进行永久或不可恢复的更改。

服务团队使用 Cosmos 作为一个集中存储库来对应用程序使用情况进行分析，以衡量系统和操作性能，并查找可能指示问题或安全问题的 abnormalities 和模式。 每个服务团队将日志的基准上载到 Cosmos，具体取决于他们要分析的内容，这通常包括：

- 事件日志
- AppLocker 日志
- 性能数据
- System Center data
- 呼叫详细信息记录
- 经验数据的质量
- IIS Web 服务器日志
- SQL Server 日志
- Syslog 数据
- 安全审核日志

在将数据上载到 Cosmos 中之前，ODL 应用程序使用清理服务来模糊处理包含客户数据（如租户信息和最终用户身份信息）的任何字段，并将这些字段替换为哈希值。 重写匿名和哈希日志，然后将其上载到 Cosmos。 服务团队针对 Cosmos 中的数据在关联、警报和报告方面运行作用域内查询。 Cosmos 中的审核日志数据保留期由服务团队决定;大多数审核日志数据会保留90天或更长的时间，以支持安全事件调查并满足法规保留要求。

对存储在 Cosmos 中的 Microsoft 365 数据的访问仅限于已授权的人员。 Microsoft 将审核功能的管理限制为负责审核功能的服务团队成员的有限子集。 这些团队成员不能修改或删除 Cosmos 中的数据，并且会记录和审核对 Cosmos 的日志记录机制所做的所有更改。

每个服务团队通过授权某些应用程序进行特定分析来访问其日志数据以供分析。 例如，Microsoft 365 安全团队通过专有的事件日志分析器使用 Cosmos 中的数据来关联、通知并生成有关 Microsoft 365 生产环境中可能存在的可疑活动的可操作报告。 这些数据中的报告用于更正漏洞，并可提高服务的整体性能。 如果特定警报或报告需要进一步调查，服务人员可以请求将数据导入回 Microsoft 365 服务。 由于要从 Cosmos 导入的特定日志是加密的，并且服务人员不具有解密密钥的访问权限，因此目标日志以编程方式传递给授权服务人员的解密服务返回范围的结果。 将使用 Microsoft 的标准安全事件管理渠道报告和升级从本练习中发现的任何漏洞。
