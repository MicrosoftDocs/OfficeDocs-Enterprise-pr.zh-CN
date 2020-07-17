---
title: Microsoft 365 隔离控件
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
description: 摘要： Microsoft 365 中的隔离控件的说明。
ms.openlocfilehash: da26bb6a41c97a16865bfdd5bdf6aada2069f7fe
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774907"
---
# <a name="microsoft-365-isolation-controls"></a><span data-ttu-id="e9ac2-103">Microsoft 365 隔离控件</span><span class="sxs-lookup"><span data-stu-id="e9ac2-103">Microsoft 365 isolation controls</span></span> 

<span data-ttu-id="e9ac2-104">Microsoft 连续工作，以确保 Microsoft 365 的多租户体系结构支持企业级安全性、机密性、隐私、完整性、本地、国际和可用性[标准](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-104">Microsoft continuously works to ensure that the multi-tenant architecture of Microsoft 365 supports enterprise-level security, confidentiality, privacy, integrity, local, international, and availability [standards](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons).</span></span> <span data-ttu-id="e9ac2-105">Microsoft 提供的服务的规模和范围使其难以和非经济地管理 Microsoft 365，从而实现显著的人工交互。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-105">The scale and the scope of services provided by Microsoft make it difficult and non-economical to manage Microsoft 365 with significant human interaction.</span></span> <span data-ttu-id="e9ac2-106">Microsoft 365 服务通过多个全局分布式数据中心提供，每个都以高自动化方式进行，其中几个操作需要人工触摸或对客户内容的任何访问。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-106">Microsoft 365 services are provided through multiple globally distributed data centers, each highly automated with few operations requiring a human touch or any access to customer content.</span></span> <span data-ttu-id="e9ac2-107">我们的员工使用自动化工具和高度安全的远程访问支持这些服务和数据中心。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-107">Our staff supports these services and data centers using automated tools and highly secure remote access.</span></span> 

<span data-ttu-id="e9ac2-108">Microsoft 365 由多个服务组成，这些服务提供重要的业务功能并参与整个 Microsoft 365 体验。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-108">Microsoft 365 is composed of multiple services that provide important business functionality and contribute to the entire Microsoft 365 experience.</span></span> <span data-ttu-id="e9ac2-109">这些服务中的每一项都是独立的，旨在与另一项集成。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-109">Each of these services is self-contained and designed to integrate with one another.</span></span>

<span data-ttu-id="e9ac2-110">Microsoft 365 的设计原则如下：</span><span class="sxs-lookup"><span data-stu-id="e9ac2-110">Microsoft 365 is designed with the following principles:</span></span>

 - <span data-ttu-id="e9ac2-111">**[面向服务的体系结构](https://docs.microsoft.com/previous-versions/aa480021(v=msdn.10))：** 以可互操作的服务的形式设计和开发软件，以提供完善定义的业务功能。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-111">**[Service-Oriented Architecture](https://docs.microsoft.com/previous-versions/aa480021(v=msdn.10)):** designing and developing software in the form of interoperable services providing well-defined business functionality.</span></span>
 - <span data-ttu-id="e9ac2-112">**[操作安全保证](https://www.microsoft.com/download/details.aspx?id=40872)：** 一种框架，其中包含通过 microsoft 独有的各种功能获得的知识，包括 Microsoft[安全开发生命周期](https://www.microsoft.com/sdl/default.aspx)、 [microsoft 安全响应中心](https://technet.microsoft.com/library/dn440717.aspx)和 cybersecurity 威胁的深层感知。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-112">**[Operational Security Assurance](https://www.microsoft.com/download/details.aspx?id=40872):** a framework that incorporates the knowledge gained through various capabilities that are unique to Microsoft, including the Microsoft [Security Development Lifecycle](https://www.microsoft.com/sdl/default.aspx), the [Microsoft Security Response Center](https://technet.microsoft.com/library/dn440717.aspx), and deep awareness of the cybersecurity threat landscape.</span></span>

<span data-ttu-id="e9ac2-113">Microsoft 365 服务之间相互进行互操作，但这些服务是专门设计和实施的，因此它们可以独立于自治服务进行部署和操作。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-113">Microsoft 365 services inter-operate with each other, but are designed and implemented so they can be deployed and operated as autonomous services, independent of each other.</span></span> <span data-ttu-id="e9ac2-114">Microsoft segregates 对 Microsoft 365 的责任和责任范围，以减少对组织资产进行未经授权或无意的修改或误用的机会。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-114">Microsoft segregates duties and areas of responsibility for Microsoft 365 to reduce opportunities for unauthorized or unintentional modification or misuse of the organization's assets.</span></span> <span data-ttu-id="e9ac2-115">Microsoft 365 团队已将角色定义为全面的基于角色的访问控制机制的一部分。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-115">Microsoft 365 teams have defined roles as part of a comprehensive role-based access control mechanism.</span></span>

## <a name="customer-content-isolation"></a><span data-ttu-id="e9ac2-116">客户内容隔离</span><span class="sxs-lookup"><span data-stu-id="e9ac2-116">Customer content isolation</span></span>

<span data-ttu-id="e9ac2-117">租户中的所有客户内容都独立于其他租户以及 Microsoft 365 管理中使用的操作和系统数据。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-117">All customer content in a tenant is isolated from other tenants and from operations and systems data used in the management of Microsoft 365.</span></span> <span data-ttu-id="e9ac2-118">在整个 Microsoft 365 中实施了多种形式的保护，以最大限度地降低泄露任何 Microsoft 365 服务或应用程序的风险。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-118">Multiple forms of protection are implemented throughout Microsoft 365 to minimize the risk of compromise of any Microsoft 365 service or application.</span></span> <span data-ttu-id="e9ac2-119">多种形式的保护也会阻止对租户或 Microsoft 365 系统本身的信息进行未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-119">Multiple forms of protection also prevent unauthorized access to the information of tenants or the Microsoft 365 system itself.</span></span>

<span data-ttu-id="e9ac2-120">有关 Microsoft 如何在 Microsoft 365 中实现租户数据的逻辑隔离的信息，请参阅[microsoft 365 中的租户隔离](office-365-tenant-isolation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e9ac2-120">For information about how Microsoft implements logical isolation of tenant data within Microsoft 365, see [Tenant Isolation in Microsoft 365](office-365-tenant-isolation-overview.md).</span></span>
