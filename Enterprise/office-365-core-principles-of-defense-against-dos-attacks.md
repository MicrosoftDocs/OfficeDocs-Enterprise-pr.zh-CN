---
title: Office 365 防御拒绝服务攻击的核心原则
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
description: Microsoft 如何在防御拒绝服务（DoS）攻击的同时，利用其核心原则、检测和缓解措施。
ms.openlocfilehash: abfb0efda679930c22d9ce87709aded9a2880f06
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067248"
---
# <a name="core-principles-of-defense-against-denial-of-service-attacks"></a>防御拒绝服务攻击的核心原则

防御基于网络的 DoS 攻击时的三个核心原则是吸收、检测和缓解。 在检测之前全部发生，并在缓解之前发生检测。 吸收是抵御 DoS 攻击的最佳防御能力。 如果无法检测到攻击，则无法缓解攻击。 但是，如果甚至无法吸收最小的 DoS 攻击，则服务的运行时间将不足以检测到攻击。

对于大多数组织来说，购买多余的容量来吸收 DoS 攻击并不可行，因为这需要在技术和技术方面有相当大的投资。 这将重点介绍使用 Microsoft 云服务的安全优势之一。 Microsoft 服务的巨大规模将以经济高效的方式为云客户提供强大的网络保护。 甚至在规模较大的情况下，在吸收、检测和缓解之间必须有平衡。 为了找出这种平衡，Microsoft 会研究攻击增长率，以估计 Microsoft 需要吸收多少内容。

检测是一种 cat 和鼠标游戏。 您必须不断寻找用户受到攻击的新方法，并尝试击败您的系统。 检测-> 缓解-> 检测-> 缓解等，是永久永久状态，持续无限期。

## <a name="defending-against-dos-attacks"></a>防御 DoS 攻击

若要成功抵御 DoS 攻击，早期检测是必不可少的。 通过在系统被淹没之前检测攻击，defenders 可以执行响应计划。

下面的公式有助于估计 DoS 攻击的影响时间：

   **最大容量（以字节/秒为单位）/增长率（以字节/秒为单位） = 影响的时间（以字节/秒为单位）**

如果检测时间发生在时间影响之后，则 DoS 攻击可能会成功。 如果检测时间在影响时间之前发生，则在使用缓解策略时，攻击服务应保持在线并可访问。 因此，防御 DoS 攻击只需要执行以下两项操作：

- 增加容量以提升最大容量的上限（进而提供更多的时间来检测攻击）;和
- 缩短要检测的时间。

增加的容量有直接的财政影响。 Microsoft 建议客户至少开发最基本的容量，以确保其可经受一定级别的 DoS 攻击。 实际的最大产量因客户而异，因为每个客户都有其自己的针对暴露、风险和财务 outlay 的阈值。 出于经济方面的原因，在研究和时间缩短检测时间的方法方面的投资通常是最经济高效的防御措施。
