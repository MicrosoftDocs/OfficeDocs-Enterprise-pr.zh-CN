---
title: 通过 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴检索客户报告数据
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 摘要：使用适用于 Microsoft Exchange Online 的远程 Windows PowerShell 检索单个客户租户的报告。
ms.openlocfilehash: d4b8d931b6b8ea8c7b8467dd70326e1b0fbfc3d5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998621"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="30174-103">通过 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴检索客户报告数据</span><span class="sxs-lookup"><span data-stu-id="30174-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="30174-104">使用适用于 Microsoft Exchange Online 的远程 Windows PowerShell 从各个客户租户检索报告。</span><span class="sxs-lookup"><span data-stu-id="30174-104">Use remote Windows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="30174-p101">联合和云解决方案提供商 (CSP) 合作伙伴 可以直接通过适用于 Exchange Online PowerShell 的远程 Windows PowerShell 访问构成客户租户报告的数据。这样，合作伙伴可以收集并保存报告数据，然后对其执行其他操作。打开远程连接后，检索有关客户租赁的报告数据与在客户租赁中运行任何 cmdlet 的效果是一样的。</span><span class="sxs-lookup"><span data-stu-id="30174-p101">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="30174-p102">在本文中，您使用适用于 Exchange Online 的远程 Windows PowerShell 连接到单个客户租赁并检索报告。默认情况下，Windows PowerShell 不支持聚合多个客户租赁中的报告数据。通过此过程检索的报告仅适用于您连接到的  _DelegatedOrg_。</span><span class="sxs-lookup"><span data-stu-id="30174-p102">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
 
## <a name="before-you-begin"></a><span data-ttu-id="30174-111">准备工作</span><span class="sxs-lookup"><span data-stu-id="30174-111">Before you begin</span></span>

- <span data-ttu-id="30174-p103">您需要使用远程 Windows PowerShell 连接到您的 Exchange Online 租户。有关说明，请参阅[通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)。</span><span class="sxs-lookup"><span data-stu-id="30174-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="30174-114">运行 Get-StaleMailboxReport 示例</span><span class="sxs-lookup"><span data-stu-id="30174-114">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="30174-115">打开到 Exchange Online 的远程会话后，运行此命令可检索日期范围 03/25/2015 到 03/31/2015 的 **Get-StaleMailboxReport** 。</span><span class="sxs-lookup"><span data-stu-id="30174-115">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="30174-p104">有许多其他报告 cmdlet 可用于 Exchange Online、Lync Online 和 SharePoint Online，还有其他报告 cmdlet 可用于您可以使用的邮件跟踪。若要了解有关可用的报告 cmdlet 和 Office 365 报告 Web 服务的详细信息，请参阅下一节中的主题。</span><span class="sxs-lookup"><span data-stu-id="30174-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="30174-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30174-118">See also</span></span>

#### 

[<span data-ttu-id="30174-119">Office 365 报告 Web 服务</span><span class="sxs-lookup"><span data-stu-id="30174-119">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="30174-120">Exchange Online 中的报告 cmdlet</span><span class="sxs-lookup"><span data-stu-id="30174-120">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="30174-121">适于合作伙伴的帮助</span><span class="sxs-lookup"><span data-stu-id="30174-121">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

