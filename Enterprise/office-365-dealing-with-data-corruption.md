---
title: Microsoft 365 处理数据损坏
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
ms.custom: seo-marvel-apr2020
description: 本文介绍了 Microsoft 365 中的数据损坏情况，以及 Microsoft 在阻止和恢复数据时所采取的努力。
ms.openlocfilehash: dc8e865a69e110fa0a68e6cd9d9f4d6b45d43d71
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606628"
---
# <a name="dealing-with-data-corruption-in-microsoft-365"></a><span data-ttu-id="8875d-103">处理 Microsoft 365 中的数据损坏</span><span class="sxs-lookup"><span data-stu-id="8875d-103">Dealing with Data Corruption in Microsoft 365</span></span>

<span data-ttu-id="8875d-104">运行大型云服务的一个有挑战性的方面是，如果数据量和独立系统的数据量较大，如何处理数据损坏。</span><span class="sxs-lookup"><span data-stu-id="8875d-104">One of the challenging aspects of running a large-scale cloud service is how to handle data corruption, given the large volume of data and independent systems.</span></span> <span data-ttu-id="8875d-105">数据损坏可能是由以下原因导致的：</span><span class="sxs-lookup"><span data-stu-id="8875d-105">Data corruption can be caused by:</span></span>

- <span data-ttu-id="8875d-106">应用程序或基础结构错误，损坏部分或全部应用程序状态</span><span class="sxs-lookup"><span data-stu-id="8875d-106">Application or infrastructure bugs, corrupting some or all of the application state</span></span>
- <span data-ttu-id="8875d-107">导致数据丢失或无法读取数据的硬件问题</span><span class="sxs-lookup"><span data-stu-id="8875d-107">Hardware issues that result in lost data or an inability to read data</span></span>
- <span data-ttu-id="8875d-108">人为操作错误</span><span class="sxs-lookup"><span data-stu-id="8875d-108">Human operational errors</span></span>
- <span data-ttu-id="8875d-109">恶意黑客和不满意的员工</span><span class="sxs-lookup"><span data-stu-id="8875d-109">Malicious hackers and disgruntled employees</span></span>
- <span data-ttu-id="8875d-110">外部服务中导致数据丢失的事件</span><span class="sxs-lookup"><span data-stu-id="8875d-110">Incidents in external services that result in some loss of data</span></span>

<span data-ttu-id="8875d-111">由于数据完整性的更高的恢复意味着较少的数据损坏事件，因此 Microsoft 内置了 Microsoft 365 保护机制，以防止发生损坏，以及使我们能够恢复数据的系统和进程。</span><span class="sxs-lookup"><span data-stu-id="8875d-111">Because greater resiliency in data integrity means fewer data corruption incidents, Microsoft has built into Microsoft 365 protection mechanisms to prevent corruption from happening, as well as systems and processes that enable us to recover data if it does.</span></span> <span data-ttu-id="8875d-112">在工程发布过程的各个阶段中都存在检查和流程，以提高对数据损坏的恢复能力，包括：</span><span class="sxs-lookup"><span data-stu-id="8875d-112">Checks and processes exist within the various stages of the engineering release process to increase resiliency against data corruption, including:</span></span>

- <span data-ttu-id="8875d-113">系统设计</span><span class="sxs-lookup"><span data-stu-id="8875d-113">System Design</span></span>
- <span data-ttu-id="8875d-114">代码组织和结构</span><span class="sxs-lookup"><span data-stu-id="8875d-114">Code organization and structure</span></span>
- <span data-ttu-id="8875d-115">代码评审</span><span class="sxs-lookup"><span data-stu-id="8875d-115">Code review</span></span>
- <span data-ttu-id="8875d-116">单元测试、集成测试和系统测试</span><span class="sxs-lookup"><span data-stu-id="8875d-116">Unit tests, integration tests, and system tests</span></span>
- <span data-ttu-id="8875d-117">行程线路测试/关口</span><span class="sxs-lookup"><span data-stu-id="8875d-117">Trip wires tests/gates</span></span>

<span data-ttu-id="8875d-118">在 Microsoft 365 的生产环境中，数据中心之间的对等复制可确保始终有任何数据的多个活动副本。</span><span class="sxs-lookup"><span data-stu-id="8875d-118">Within Microsoft 365 production environments, peer replication between datacenters ensures that there are always multiple live copies of any data.</span></span> <span data-ttu-id="8875d-119">标准图像和脚本用于恢复丢失的服务器，复制的数据用于还原客户数据。</span><span class="sxs-lookup"><span data-stu-id="8875d-119">Standard images and scripts are used to recover lost servers, and replicated data is used to restore customer data.</span></span> <span data-ttu-id="8875d-120">由于内置的数据弹性检查和过程，Microsoft 仅维护 Microsoft 365 信息系统文档 (，其中包括与安全相关的文档) ，使用 SharePoint Online 中的内置复制和我们的内部代码库工具（来源仓库）。</span><span class="sxs-lookup"><span data-stu-id="8875d-120">Because of the built-in data resiliency checks and processes, Microsoft maintains backups only of Microsoft 365 information system documentation (including security-related documentation), using built-in replication in SharePoint Online and our internal code repository tool, Source Depot.</span></span> <span data-ttu-id="8875d-121">系统文档存储在 SharePoint Online 中，源仓库包含系统和应用程序映像。</span><span class="sxs-lookup"><span data-stu-id="8875d-121">System documentation is stored in SharePoint Online, and Source Depot contains system and application images.</span></span> <span data-ttu-id="8875d-122">SharePoint Online 和源仓库都使用版本控制，并在近实时进行复制。</span><span class="sxs-lookup"><span data-stu-id="8875d-122">Both SharePoint Online and Source Depot use versioning and are replicated in near real time.</span></span>
