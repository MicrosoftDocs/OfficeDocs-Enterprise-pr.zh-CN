---
title: 使用 Windows PowerShell 为 "联盟" 合作伙伴管理 Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: 摘要：联合和云解决方案提供商 (CSP) 合作伙伴可以使用 Windows PowerShell 管理 Microsoft 365 客户租户。
ms.openlocfilehash: a2b05a5f24984d4113c856920d217f47d55f606b
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605918"
---
# <a name="manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="221a1-103">使用 Windows PowerShell 管理 Microsoft 365，以获取委派访问权限 () 合作伙伴的权限</span><span class="sxs-lookup"><span data-stu-id="221a1-103">Manage Microsoft 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="221a1-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="221a1-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="221a1-105">委派访问权限 (DAP) 合作伙伴是联合和云解决方案提供商 (CSP) 合作伙伴。</span><span class="sxs-lookup"><span data-stu-id="221a1-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="221a1-106">他们通常是面向其他公司的网络或电信提供商。</span><span class="sxs-lookup"><span data-stu-id="221a1-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="221a1-107">他们将 Microsoft 365 订阅捆绑到其客户的服务产品中。</span><span class="sxs-lookup"><span data-stu-id="221a1-107">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="221a1-108">在销售 Microsoft 365 订阅时，会自动为他们代表 (AOBO) 权限授予对 customer 租赁的管理权限，以便他们可以管理和报告客户租赁。</span><span class="sxs-lookup"><span data-stu-id="221a1-108">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="221a1-109">最大程度上，这在 Microsoft 365 管理中心中非常困难且耗时。</span><span class="sxs-lookup"><span data-stu-id="221a1-109">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="221a1-110">执行管理任务（如列出所有客户**TenantIds**及其域，或通过使用 PowerShell for Microsoft 365 为其分配的许可证）要容易得多。</span><span class="sxs-lookup"><span data-stu-id="221a1-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using PowerShell for Microsoft 365.</span></span> <span data-ttu-id="221a1-111">在某些情况下，可以仅在 PowerShell for Microsoft 365 中执行这些管理任务。</span><span class="sxs-lookup"><span data-stu-id="221a1-111">In some cases, it is possible to do these administrative tasks only in PowerShell for Microsoft 365.</span></span> <span data-ttu-id="221a1-112">下面是联合和 CSP 合作伙伴最常用来管理其客户租赁的方案示例：</span><span class="sxs-lookup"><span data-stu-id="221a1-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="221a1-113">使用 Windows PowerShell 为 Microsoft 365 租户管理 () 合作伙伴的委派访问权限</span><span class="sxs-lookup"><span data-stu-id="221a1-113">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="221a1-114">使用 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴将域添加到客户端租赁</span><span class="sxs-lookup"><span data-stu-id="221a1-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="221a1-115">通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户</span><span class="sxs-lookup"><span data-stu-id="221a1-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="221a1-116">通过 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴检索客户报告数据</span><span class="sxs-lookup"><span data-stu-id="221a1-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

