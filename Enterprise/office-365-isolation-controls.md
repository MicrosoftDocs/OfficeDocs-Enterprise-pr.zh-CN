---
title: Office 365 隔离控制
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
description: 摘要： Office 365 中的隔离控件的说明。
ms.openlocfilehash: 87317d753198b50ce360640c94f042adf27ed06e
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067217"
---
# <a name="office-365-isolation-controls"></a><span data-ttu-id="2b67e-103">Office 365 隔离控制</span><span class="sxs-lookup"><span data-stu-id="2b67e-103">Office 365 Isolation Controls</span></span> 

<span data-ttu-id="2b67e-104">Microsoft 连续工作，以确保 Office 365 的多租户体系结构支持企业级安全性、机密性、隐私、完整性、本地、国际和可用性[标准](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)。</span><span class="sxs-lookup"><span data-stu-id="2b67e-104">Microsoft continuously works to ensure that the multi-tenant architecture of Office 365 supports enterprise-level security, confidentiality, privacy, integrity, local, international, and availability [standards](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons).</span></span> <span data-ttu-id="2b67e-105">Microsoft 提供的服务的规模和范围使其难以和非经济地管理 Office 365，从而实现显著的人工交互。</span><span class="sxs-lookup"><span data-stu-id="2b67e-105">The scale and the scope of services provided by Microsoft make it difficult and non-economical to manage Office 365 with significant human interaction.</span></span> <span data-ttu-id="2b67e-106">Office 365 服务通过多个全局分布式数据中心提供，每个都具有极大的自动化，需要人工触摸或任何对客户内容的访问。</span><span class="sxs-lookup"><span data-stu-id="2b67e-106">Office 365 services are provided through multiple globally distributed data centers, each highly automated with few operations requiring a human touch or any access to customer content.</span></span> <span data-ttu-id="2b67e-107">我们的员工使用自动化工具和高度安全的远程访问支持这些服务和数据中心。</span><span class="sxs-lookup"><span data-stu-id="2b67e-107">Our staff supports these services and data centers using automated tools and highly secure remote access.</span></span> <span data-ttu-id="2b67e-108">有关如何在 Office 365 中运行大规模服务的一些详细信息，请参阅[IT 专业人员在 office 365 中的幕后外观](https://channel9.msdn.com/Events/SharePoint-Conference/2014/SPC202)。</span><span class="sxs-lookup"><span data-stu-id="2b67e-108">For some of the details about how large-scale services are operated in Office 365, see [a behind the scenes look at Office 365 for IT Pros](https://channel9.msdn.com/Events/SharePoint-Conference/2014/SPC202).</span></span>

<span data-ttu-id="2b67e-109">Office 365 由多个服务组成，这些服务可提供重要的业务功能并参与整个 Office 365 体验。</span><span class="sxs-lookup"><span data-stu-id="2b67e-109">Office 365 is composed of multiple services that provide important business functionality and contribute to the entire Office 365 experience.</span></span> <span data-ttu-id="2b67e-110">这些服务中的每一项都是独立的，旨在与另一项集成。</span><span class="sxs-lookup"><span data-stu-id="2b67e-110">Each of these services is self-contained and designed to integrate with one another.</span></span>

<span data-ttu-id="2b67e-111">Office 365 的设计具有以下原则：</span><span class="sxs-lookup"><span data-stu-id="2b67e-111">Office 365 is designed with the following principles:</span></span>

 - <span data-ttu-id="2b67e-112">**[面向服务的体系结构](https://msdn.microsoft.com/library/aa480021.aspx)：** 以可互操作的服务的形式设计和开发软件，以提供完善定义的业务功能。</span><span class="sxs-lookup"><span data-stu-id="2b67e-112">**[Service-Oriented Architecture](https://msdn.microsoft.com/library/aa480021.aspx):** designing and developing software in the form of interoperable services providing well-defined business functionality.</span></span>
 - <span data-ttu-id="2b67e-113">**[操作安全保证](http://www.microsoft.com/download/details.aspx?id=40872)：** 一个框架，其中包含通过与 microsoft 独有的各种功能获得的知识，包括 Microsoft 安全[开发生命周期](https://www.microsoft.com/sdl/default.aspx)、 [microsoft 安全响应中心](https://technet.microsoft.com/library/dn440717.aspx)，并深入了解 cybersecurity 威胁的前景。</span><span class="sxs-lookup"><span data-stu-id="2b67e-113">**[Operational Security Assurance](http://www.microsoft.com/download/details.aspx?id=40872):** a framework that incorporates the knowledge gained through various capabilities that are unique to Microsoft, including the Microsoft [Security Development Lifecycle](https://www.microsoft.com/sdl/default.aspx), the [Microsoft Security Response Center](https://technet.microsoft.com/library/dn440717.aspx), and deep awareness of the cybersecurity threat landscape.</span></span>

<span data-ttu-id="2b67e-114">Office 365 服务之间相互进行互操作，但它们已经过设计和实现，以便可以将它们作为自治服务进行部署，并相互独立。</span><span class="sxs-lookup"><span data-stu-id="2b67e-114">Office 365 services inter-operate with each other, but are designed and implemented so they can be deployed and operated as autonomous services, independent of each other.</span></span> <span data-ttu-id="2b67e-115">Microsoft segregates Office 365 的责任和职责范围，以减少对组织资产进行未经授权或无意的修改或误用的机会。</span><span class="sxs-lookup"><span data-stu-id="2b67e-115">Microsoft segregates duties and areas of responsibility for Office 365 to reduce opportunities for unauthorized or unintentional modification or misuse of the organization's assets.</span></span> <span data-ttu-id="2b67e-116">Office 365 团队已将角色定义为全面的基于角色的访问控制机制的一部分。</span><span class="sxs-lookup"><span data-stu-id="2b67e-116">Office 365 teams have defined roles as part of a comprehensive role-based access control mechanism.</span></span>

## <a name="customer-content-isolation"></a><span data-ttu-id="2b67e-117">客户内容隔离</span><span class="sxs-lookup"><span data-stu-id="2b67e-117">Customer content isolation</span></span>

<span data-ttu-id="2b67e-118">租户中的所有客户内容都独立于其他租户以及 Office 365 管理中使用的操作和系统数据。</span><span class="sxs-lookup"><span data-stu-id="2b67e-118">All customer content in a tenant is isolated from other tenants and from operations and systems data used in the management of Office 365.</span></span> <span data-ttu-id="2b67e-119">在整个 Office 365 中实施多种形式的保护，以最大限度地降低对任何 Office 365 服务或应用程序造成危害的风险。</span><span class="sxs-lookup"><span data-stu-id="2b67e-119">Multiple forms of protection are implemented throughout Office 365 to minimize the risk of compromise of any Office 365 service or application.</span></span> <span data-ttu-id="2b67e-120">多种形式的保护也会阻止对租户或 Office 365 系统本身的信息进行未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="2b67e-120">Multiple forms of protection also prevent unauthorized access to the information of tenants or the Office 365 system itself.</span></span>

<span data-ttu-id="2b67e-121">有关 Microsoft 如何在 Office 365 中实现租户数据的逻辑隔离的信息，请参阅[office 365 中的租户隔离](office-365-tenant-isolation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="2b67e-121">For information about how Microsoft implements logical isolation of tenant data within Office 365, see [Tenant Isolation in Office 365](office-365-tenant-isolation-overview.md).</span></span>
