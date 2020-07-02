---
title: 使用 Windows PowerShell 为委派访问权限（分配）合作伙伴管理 Microsoft 365
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
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: 摘要：联合和云解决方案提供商（CSP）合作伙伴可以使用 Windows PowerShell 管理 Microsoft 365 客户租户。
ms.openlocfilehash: 00e60693ad10b705765da9ed57142c893a74b034
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998218"
---
# <a name="manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="f57ce-103">使用 Windows PowerShell 为委派访问权限（分配）合作伙伴管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f57ce-103">Manage Microsoft 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="f57ce-104">委派访问权限 (DAP) 合作伙伴是联合和云解决方案提供商 (CSP) 合作伙伴。</span><span class="sxs-lookup"><span data-stu-id="f57ce-104">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="f57ce-105">他们通常是面向其他公司的网络或电信提供商。</span><span class="sxs-lookup"><span data-stu-id="f57ce-105">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="f57ce-106">他们将 Microsoft 365 订阅捆绑到其客户的服务产品中。</span><span class="sxs-lookup"><span data-stu-id="f57ce-106">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="f57ce-107">在销售 Microsoft 365 订阅时，会自动将代表（AOBO）权限的 "管理" 授予 "客户" 租赁，以便他们可以管理和报告客户租赁。</span><span class="sxs-lookup"><span data-stu-id="f57ce-107">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="f57ce-108">最大程度上，这在 Microsoft 365 管理中心中非常困难且耗时。</span><span class="sxs-lookup"><span data-stu-id="f57ce-108">At best, this is difficult and time consuming to do in the Microsoft 365 admin center.</span></span> <span data-ttu-id="f57ce-109">执行管理任务要简单得多，例如列出所有客户 **TenantIds** 及其域或标识客户租赁中的所有用户，以及使用适用于 Office 365 的 Windows PowerShell 标识它们所分配的许可证。</span><span class="sxs-lookup"><span data-stu-id="f57ce-109">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="f57ce-110">在某些情况下，可以仅在适用于 Office 365 的 Windows PowerShell 中执行这些管理任务。</span><span class="sxs-lookup"><span data-stu-id="f57ce-110">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="f57ce-111">下面是联合和 CSP 合作伙伴最常用来管理其客户租赁的方案示例：</span><span class="sxs-lookup"><span data-stu-id="f57ce-111">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="f57ce-112">使用 Windows PowerShell 为委派访问权限（分配）合作伙伴管理 Microsoft 365 租户</span><span class="sxs-lookup"><span data-stu-id="f57ce-112">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="f57ce-113">使用 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴将域添加到客户端租赁</span><span class="sxs-lookup"><span data-stu-id="f57ce-113">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="f57ce-114">通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户</span><span class="sxs-lookup"><span data-stu-id="f57ce-114">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="f57ce-115">通过 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴检索客户报告数据</span><span class="sxs-lookup"><span data-stu-id="f57ce-115">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

