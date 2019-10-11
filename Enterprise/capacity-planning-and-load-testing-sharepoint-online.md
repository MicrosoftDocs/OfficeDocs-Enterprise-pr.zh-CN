---
title: 容量规划和负载测试 SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: 本文介绍如何在不执行传统负载测试的情况下部署到 SharePoint Online，因为这是不允许的。
ms.openlocfilehash: d62b15be38b3f62c64c2943313b94aa99cbd14ab
ms.sourcegitcommit: 739024fe2862ab646b36e218b57c5cc16ebe7892
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2019
ms.locfileid: "37422139"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>容量规划和负载测试 SharePoint Online
本文介绍了如何在不进行传统负载测试的情况下部署到 SharePoint Online，因为 SharePoint Online 不允许进行负载测试。 SharePoint Online 是云服务，服务中负载的负载功能、运行状况和总体平衡由 Microsoft 进行管理。
  
确保网站启动成功的最佳方法是遵循在[规划门户启动](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out)时的规划中突出显示的基本原则、做法和建议。

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>SharePoint Online 执行容量规划的概述 
在本地部署中，SharePoint Online 的主要好处之一是云的弹性，以及针对分布式区域中用户的优化。 我们将大型环境设置为每天为数百万个用户提供服务，因此我们必须通过平衡和扩展服务器场有效地处理容量。
  
虽然在任何一个服务器场中的任何一个租户的增长通常不可预测，但累积的请求总数可随时间推移而预测。 通过确定 SharePoint Online 中的增长趋势，我们可以规划未来的扩展。
  
为了高效地使用容量并处理意外增长，在任何服务器场中，我们都具有跟踪和监控服务的各种元素的自动化。 使用多个指标，其中一个主要指标是 CPU 负载，可用作扩展前端服务器的信号。 此外，我们还建议采用[分阶段/浪潮方法](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out)，因为 SQL 环境将根据时间的负载和增长进行扩展，并且按照这些阶段和波形可实现该负载和增长的正确分布。 

容量不仅仅是在不断添加更多硬件，还与管理和控制容量以确保它为有效的加载请求提供服务相关。 我们建议客户遵循建议的指南，以确保他们获得最佳体验。 这也意味着我们已经实施了限制模式和控制，以确保我们不允许在服务中执行 "滥用" 的行为。 尽管并非所有 "错误" 行为是特意的，但我们确实必须确保我们限制该行为的影响。 有关限制以及如何避免此限制的详细信息，请查看[如何避免受限制的指南](https://docs.microsoft.com/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online)文章。

## <a name="why-you-cannot-load-test-sharepoint-online"></a>为什么您无法加载测试 SharePoint Online
在本地环境中，负载测试用于验证扩展假设并最终发现服务器场的中断点;通过将其与负载进行饱和。 

通过 SharePoint Online，我们需要执行不同的操作，因为扩展相对于特定试探法进行了相对流动和调整、限制和控件负载。 作为大型规模的多租户环境，我们必须保护同一服务器场中的所有租户，因此我们将自动限制任何负载测试。 如果您现在尝试加载测试，除了受到限制之外，您将收到 disappointing 和潜在的误导性结果，因为您在测试期间测试的服务器场可能在测试窗口中或在测试之后的几小时内发生扩展更改，如扩展和服务器场平衡操作在不断执行。

而不是尝试将测试 SharePoint 作为服务进行加载，而是侧重于遵循建议的做法，并遵循[创建、启动和维护正常的门户](https://go.microsoft.com/fwlink/?linkid=2105838)指南。
