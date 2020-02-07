---
title: 处理数据损坏的 Office 365
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
description: Office 365 中的数据损坏的说明，以及 Microsoft 预防和恢复的努力。
ms.openlocfilehash: 1477ab4dca0f9126eb04b76b9f8f65ff0b5eefc8
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844483"
---
# <a name="dealing-with-data-corruption-in-office-365"></a>处理 Office 365 中的数据损坏

运行大型云服务的一个有挑战性的方面是，如果数据量和独立系统的数据量较大，如何处理数据损坏。 数据损坏可能是由以下原因导致的：

- 应用程序或基础结构错误，损坏部分或全部应用程序状态
- 导致数据丢失或无法读取数据的硬件问题
- 人为操作错误
- 恶意黑客和不满意的员工
- 外部服务中导致数据丢失的事件

由于数据完整性方面的更高的恢复意味着较少的数据损坏事件，Microsoft 已经内置了 Office 365 保护机制，以防止发生损坏，以及使我们能够恢复数据的系统和进程。 在工程发布过程的各个阶段中都存在检查和流程，以提高对数据损坏的恢复能力，包括：

- 系统设计
- 代码组织和结构
- 代码评审
- 单元测试、集成测试和系统测试
- 行程线路测试/关口

在 Office 365 生产环境中，数据中心之间的对等复制可确保始终有任何数据的多个活动副本。 标准图像和脚本用于恢复丢失的服务器，复制的数据用于还原客户数据。 由于内置的数据弹性检查和过程，Microsoft 在 SharePoint Online 和我们的内部代码中使用内置复制功能，仅维护 Office 365 信息系统文档（包括与安全相关的文档）的备份存储库工具，源仓库。 系统文档存储在 SharePoint Online 中，源仓库包含系统和应用程序映像。 SharePoint Online 和源仓库都使用版本控制，并在近实时进行复制。
