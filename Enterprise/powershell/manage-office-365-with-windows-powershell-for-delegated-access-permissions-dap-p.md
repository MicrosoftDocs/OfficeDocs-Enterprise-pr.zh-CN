---
title: 使用 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴管理 Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: 摘要：联合和云解决方案提供商 (CSP) 合作伙伴 可以使用 Windows PowerShell 管理 Office 365 客户租户。
ms.openlocfilehash: f36762cd8e78485316270f8eec8386229a84a276
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068906"
---
# <a name="manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="8e647-103">使用 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="8e647-103">Manage Office 365 with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="8e647-104">**摘要：** 联合和云解决方案提供商 (CSP) 合作伙伴可以使用 Windows PowerShell 管理 Office 365 客户租户。</span><span class="sxs-lookup"><span data-stu-id="8e647-104">**Summary:** Syndication and Cloud Solution Provider (CSP) partners can use Windows PowerShell to manage Office 365 customer tenants.</span></span>
  
<span data-ttu-id="8e647-105">委派访问权限 (DAP) 合作伙伴是联合和云解决方案提供商 (CSP) 合作伙伴。</span><span class="sxs-lookup"><span data-stu-id="8e647-105">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="8e647-106">他们通常是面向其他公司的网络或电信提供商。</span><span class="sxs-lookup"><span data-stu-id="8e647-106">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="8e647-107">他们将 Office 365 订阅捆绑到为其客户提供的服务产品中。</span><span class="sxs-lookup"><span data-stu-id="8e647-107">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="8e647-108">当他们销售 Office 365 订阅时，会自动获得对客户租赁的“代表以下方管理”(AOBO) 权限，这样他们便可以管理客户租赁并生成相应报告。</span><span class="sxs-lookup"><span data-stu-id="8e647-108">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span> <span data-ttu-id="8e647-109">即使在最好的情况下，在 Office 365 管理中心 中执行此操作也非常困难且耗时。</span><span class="sxs-lookup"><span data-stu-id="8e647-109">At best, this is difficult and time consuming to do in the Office 365 admin center.</span></span> <span data-ttu-id="8e647-110">执行管理任务要简单得多，例如列出所有客户 **TenantIds** 及其域或标识客户租赁中的所有用户，以及使用适用于 Office 365 的 Windows PowerShell 标识它们所分配的许可证。</span><span class="sxs-lookup"><span data-stu-id="8e647-110">It is much easier to do administrative tasks like listing all the customer **TenantIds** and their domains or identifying all users in a customer tenancy and what licenses they are assigned by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="8e647-111">在某些情况下，可以仅在适用于 Office 365 的 Windows PowerShell 中执行这些管理任务。</span><span class="sxs-lookup"><span data-stu-id="8e647-111">In some cases, it is possible to do these administrative tasks only in Windows PowerShell for Office 365.</span></span> <span data-ttu-id="8e647-112">下面是联合和 CSP 合作伙伴最常用来管理其客户租赁的方案示例：</span><span class="sxs-lookup"><span data-stu-id="8e647-112">Here are samples of scenarios that Syndication and CSP partners most frequently use to administer their customer tenancies:</span></span>
  
## 

- [<span data-ttu-id="8e647-113">使用 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴管理 Office 365 租户</span><span class="sxs-lookup"><span data-stu-id="8e647-113">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [<span data-ttu-id="8e647-114">使用 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴将域添加到客户端租赁</span><span class="sxs-lookup"><span data-stu-id="8e647-114">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [<span data-ttu-id="8e647-115">通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户</span><span class="sxs-lookup"><span data-stu-id="8e647-115">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
- [<span data-ttu-id="8e647-116">通过 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴检索客户报告数据</span><span class="sxs-lookup"><span data-stu-id="8e647-116">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
    

    

