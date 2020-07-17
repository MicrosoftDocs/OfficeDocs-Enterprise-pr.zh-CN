---
title: Microsoft 365 中的租户隔离
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
description: Microsoft 为 Microsoft 365 强制实施租户隔离的方式的摘要。
ms.openlocfilehash: 891fdb9bebb500c40a9658d170942ca396facfd1
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998641"
---
# <a name="tenant-isolation-in-microsoft-365"></a><span data-ttu-id="d701d-103">Microsoft 365 中的租户隔离</span><span class="sxs-lookup"><span data-stu-id="d701d-103">Tenant Isolation in Microsoft 365</span></span>

<span data-ttu-id="d701d-104">云计算的主要优势之一是多个客户之间共享的通用基础结构的概念，从而导致规模经济。</span><span class="sxs-lookup"><span data-stu-id="d701d-104">One of the primary benefits of cloud computing is concept of a shared, common infrastructure across numerous customers simultaneously, leading to economies of scale.</span></span> <span data-ttu-id="d701d-105">此概念称为*多租户*。</span><span class="sxs-lookup"><span data-stu-id="d701d-105">This concept is called *multi-tenancy*.</span></span> <span data-ttu-id="d701d-106">Microsoft 连续工作，以确保云服务的多租户体系结构支持企业级安全性、机密性、隐私、完整性和可用性标准。</span><span class="sxs-lookup"><span data-stu-id="d701d-106">Microsoft works continuously to ensure that the multi-tenant architectures of our cloud services support enterprise-level security, confidentiality, privacy, integrity, and availability standards.</span></span>

<span data-ttu-id="d701d-107">根据可[信赖的计算](https://www.microsoft.com/trust-center)和[安全开发生命周期](https://www.microsoft.com/securityengineering/sdl/)收集到的重要投资和经验，Microsoft 云服务设计为假设所有租户都有可能与所有其他租户有敌意，并实施了安全措施以防止一个租户的操作影响另一个租户的安全或服务，或访问其他租户的内容。</span><span class="sxs-lookup"><span data-stu-id="d701d-107">Based upon the significant investments and experience gathered from [Trustworthy Computing](https://www.microsoft.com/trust-center) and the [Security Development Lifecycle](https://www.microsoft.com/securityengineering/sdl/), Microsoft cloud services were designed with the assumption that all tenants are potentially hostile to all other tenants, and we have implemented security measures to prevent the actions of one tenant from affecting the security or service of another tenant, or accessing the content of another tenant.</span></span>

<span data-ttu-id="d701d-108">在多租户环境中维护租户隔离的两个主要目标是：</span><span class="sxs-lookup"><span data-stu-id="d701d-108">The two primary goals of maintaining tenant isolation in a multi-tenant environment are:</span></span>

1.  <span data-ttu-id="d701d-109">防止对租户之间的客户内容的泄露或未经授权访问;并</span><span class="sxs-lookup"><span data-stu-id="d701d-109">Preventing leakage of, or unauthorized access to, customer content across tenants; and</span></span>
2.  <span data-ttu-id="d701d-110">防止一个租户的操作对另一个租户的服务产生不利影响</span><span class="sxs-lookup"><span data-stu-id="d701d-110">Preventing the actions of one tenant from adversely affecting the service for another tenant</span></span>

<span data-ttu-id="d701d-111">在整个 Microsoft 365 中实施了多种形式的保护，以防止客户损害 Microsoft 365 服务或应用程序，或未经授权访问其他租户或 Microsoft 365 系统本身的信息，其中包括：</span><span class="sxs-lookup"><span data-stu-id="d701d-111">Multiple forms of protection have been implemented throughout Microsoft 365 to prevent customers from compromising Microsoft 365 services or applications or gaining unauthorized access to the information of other tenants or the Microsoft 365 system itself, including:</span></span>

- <span data-ttu-id="d701d-112">通过 Azure Active Directory 授权和基于角色的访问控制实现 Microsoft 365 服务中每个租户内的客户内容的逻辑隔离。</span><span class="sxs-lookup"><span data-stu-id="d701d-112">Logical isolation of customer content within each tenant for Microsoft 365 services is achieved through Azure Active Directory authorization and role-based access control.</span></span>
- <span data-ttu-id="d701d-113">SharePoint Online 在存储级别提供了数据隔离机制。</span><span class="sxs-lookup"><span data-stu-id="d701d-113">SharePoint Online provides data isolation mechanisms at the storage level.</span></span>
- <span data-ttu-id="d701d-114">Microsoft 使用严格的物理安全、背景屏蔽和多层加密策略来保护客户内容的机密性和完整性。</span><span class="sxs-lookup"><span data-stu-id="d701d-114">Microsoft uses rigorous physical security, background screening, and a multi-layered encryption strategy to protect the confidentiality and integrity of customer content.</span></span> <span data-ttu-id="d701d-115">所有 Microsoft 365 数据中心都具有生物特征访问控制，大多数情况下需要 palm 打印才能获得物理访问权限。</span><span class="sxs-lookup"><span data-stu-id="d701d-115">All Microsoft 365 datacenters have biometric access controls, with most requiring palm prints to gain physical access.</span></span> <span data-ttu-id="d701d-116">此外，所有基于美国的 Microsoft 员工都需要在聘用过程中成功完成标准背景检查。</span><span class="sxs-lookup"><span data-stu-id="d701d-116">In addition, all U.S.-based Microsoft employees are required to successfully complete a standard background check as part of the hiring process.</span></span> <span data-ttu-id="d701d-117">有关在 Microsoft 365 中用于管理访问的控件的详细信息，请参阅[microsoft 365 管理访问控制](office-365-administrative-access-controls-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d701d-117">For more information on the controls used for administrative access in Microsoft 365, see [Microsoft 365 Administrative Access Controls](office-365-administrative-access-controls-overview.md).</span></span>
- <span data-ttu-id="d701d-118">Microsoft 365 使用服务端技术来加密 rest 和传输中的客户内容，包括 BitLocker、每文件加密、传输层安全性（TLS）和 Internet 协议安全性（IPsec）。</span><span class="sxs-lookup"><span data-stu-id="d701d-118">Microsoft 365 uses service-side technologies that encrypt customer content at rest and in transit, including BitLocker, per-file encryption, Transport Layer Security (TLS) and Internet Protocol Security (IPsec).</span></span> <span data-ttu-id="d701d-119">有关 Microsoft 365 中的加密的具体详细信息，请参阅[microsoft 365 中的数据加密技术](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview)。</span><span class="sxs-lookup"><span data-stu-id="d701d-119">For specific details about encryption in Microsoft 365, see [Data Encryption Technologies in Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview).</span></span>

<span data-ttu-id="d701d-120">上面列出的保护功能提供了可靠的逻辑隔离控制，它们提供了与独立的物理隔离提供的威胁防护和缓解等效项。</span><span class="sxs-lookup"><span data-stu-id="d701d-120">Together, the above-listed protections provide robust logical isolation controls that provide threat protection and mitigation equivalent to that provided by physical isolation alone.</span></span>

## <a name="related-links"></a><span data-ttu-id="d701d-121">相关链接</span><span class="sxs-lookup"><span data-stu-id="d701d-121">Related Links</span></span>

- [<span data-ttu-id="d701d-122">Azure Active Directory 中的隔离和访问控制</span><span class="sxs-lookup"><span data-stu-id="d701d-122">Isolation and Access Control in Azure Active Directory</span></span>](office-365-isolation-in-azure-active-directory.md)
- [<span data-ttu-id="d701d-123">Office Graph 和 Delve 中的租户隔离</span><span class="sxs-lookup"><span data-stu-id="d701d-123">Tenant Isolation in the Office Graph and Delve</span></span>](office-365-isolation-in-graph-and-delve.md)
- [<span data-ttu-id="d701d-124">Microsoft 365 搜索中的租户隔离</span><span class="sxs-lookup"><span data-stu-id="d701d-124">Tenant Isolation in Microsoft 365 Search</span></span>](office-365-isolation-in-office-365-search.md)
- [<span data-ttu-id="d701d-125">Office 365 视频中的租户隔离</span><span class="sxs-lookup"><span data-stu-id="d701d-125">Tenant Isolation in Office 365 Video</span></span>](office-365-isolation-in-office-365-video.md)
- [<span data-ttu-id="d701d-126">资源限制</span><span class="sxs-lookup"><span data-stu-id="d701d-126">Resource Limits</span></span>](office-365-resource-limits.md)
- [<span data-ttu-id="d701d-127">监视和测试租户边界</span><span class="sxs-lookup"><span data-stu-id="d701d-127">Monitoring and Testing Tenant Boundaries</span></span>](office-365-monitoring-and-testing.md)
- [<span data-ttu-id="d701d-128">Microsoft 365 中的隔离和访问控制</span><span class="sxs-lookup"><span data-stu-id="d701d-128">Isolation and Access Control in Microsoft 365</span></span>](office-365-isolation-in-office-365.md)
