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
# <a name="dealing-with-data-corruption-in-office-365"></a><span data-ttu-id="2a57b-103">处理 Office 365 中的数据损坏</span><span class="sxs-lookup"><span data-stu-id="2a57b-103">Dealing with Data Corruption in Office 365</span></span>

<span data-ttu-id="2a57b-104">运行大型云服务的一个有挑战性的方面是，如果数据量和独立系统的数据量较大，如何处理数据损坏。</span><span class="sxs-lookup"><span data-stu-id="2a57b-104">One of the challenging aspects of running a large-scale cloud service is how to handle data corruption, given the large volume of data and independent systems.</span></span> <span data-ttu-id="2a57b-105">数据损坏可能是由以下原因导致的：</span><span class="sxs-lookup"><span data-stu-id="2a57b-105">Data corruption can be caused by:</span></span>

- <span data-ttu-id="2a57b-106">应用程序或基础结构错误，损坏部分或全部应用程序状态</span><span class="sxs-lookup"><span data-stu-id="2a57b-106">Application or infrastructure bugs, corrupting some or all of the application state</span></span>
- <span data-ttu-id="2a57b-107">导致数据丢失或无法读取数据的硬件问题</span><span class="sxs-lookup"><span data-stu-id="2a57b-107">Hardware issues that result in lost data or an inability to read data</span></span>
- <span data-ttu-id="2a57b-108">人为操作错误</span><span class="sxs-lookup"><span data-stu-id="2a57b-108">Human operational errors</span></span>
- <span data-ttu-id="2a57b-109">恶意黑客和不满意的员工</span><span class="sxs-lookup"><span data-stu-id="2a57b-109">Malicious hackers and disgruntled employees</span></span>
- <span data-ttu-id="2a57b-110">外部服务中导致数据丢失的事件</span><span class="sxs-lookup"><span data-stu-id="2a57b-110">Incidents in external services that result in some loss of data</span></span>

<span data-ttu-id="2a57b-111">由于数据完整性方面的更高的恢复意味着较少的数据损坏事件，Microsoft 已经内置了 Office 365 保护机制，以防止发生损坏，以及使我们能够恢复数据的系统和进程。</span><span class="sxs-lookup"><span data-stu-id="2a57b-111">Because greater resiliency in data integrity means fewer data corruption incidents, Microsoft has built into Office 365 protection mechanisms to prevent corruption from happening, as well as systems and processes that enable us to recover data if it does.</span></span> <span data-ttu-id="2a57b-112">在工程发布过程的各个阶段中都存在检查和流程，以提高对数据损坏的恢复能力，包括：</span><span class="sxs-lookup"><span data-stu-id="2a57b-112">Checks and processes exist within the various stages of the engineering release process to increase resiliency against data corruption, including:</span></span>

- <span data-ttu-id="2a57b-113">系统设计</span><span class="sxs-lookup"><span data-stu-id="2a57b-113">System Design</span></span>
- <span data-ttu-id="2a57b-114">代码组织和结构</span><span class="sxs-lookup"><span data-stu-id="2a57b-114">Code organization and structure</span></span>
- <span data-ttu-id="2a57b-115">代码评审</span><span class="sxs-lookup"><span data-stu-id="2a57b-115">Code review</span></span>
- <span data-ttu-id="2a57b-116">单元测试、集成测试和系统测试</span><span class="sxs-lookup"><span data-stu-id="2a57b-116">Unit tests, integration tests, and system tests</span></span>
- <span data-ttu-id="2a57b-117">行程线路测试/关口</span><span class="sxs-lookup"><span data-stu-id="2a57b-117">Trip wires tests/gates</span></span>

<span data-ttu-id="2a57b-118">在 Office 365 生产环境中，数据中心之间的对等复制可确保始终有任何数据的多个活动副本。</span><span class="sxs-lookup"><span data-stu-id="2a57b-118">Within Office 365 production environments, peer replication between datacenters ensures that there are always multiple live copies of any data.</span></span> <span data-ttu-id="2a57b-119">标准图像和脚本用于恢复丢失的服务器，复制的数据用于还原客户数据。</span><span class="sxs-lookup"><span data-stu-id="2a57b-119">Standard images and scripts are used to recover lost servers, and replicated data is used to restore customer data.</span></span> <span data-ttu-id="2a57b-120">由于内置的数据弹性检查和过程，Microsoft 在 SharePoint Online 和我们的内部代码中使用内置复制功能，仅维护 Office 365 信息系统文档（包括与安全相关的文档）的备份存储库工具，源仓库。</span><span class="sxs-lookup"><span data-stu-id="2a57b-120">Because of the built-in data resiliency checks and processes, Microsoft maintains backups only of Office 365 information system documentation (including security-related documentation), using built-in replication in SharePoint Online and our internal code repository tool, Source Depot.</span></span> <span data-ttu-id="2a57b-121">系统文档存储在 SharePoint Online 中，源仓库包含系统和应用程序映像。</span><span class="sxs-lookup"><span data-stu-id="2a57b-121">System documentation is stored in SharePoint Online, and Source Depot contains system and application images.</span></span> <span data-ttu-id="2a57b-122">SharePoint Online 和源仓库都使用版本控制，并在近实时进行复制。</span><span class="sxs-lookup"><span data-stu-id="2a57b-122">Both SharePoint Online and Source Depot use versioning and are replicated in near real time.</span></span>
