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
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>通过 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴检索客户报告数据

使用适用于 Microsoft Exchange Online 的远程 Windows PowerShell 从各个客户租户检索报告。
  
联合和云解决方案提供商 (CSP) 合作伙伴 可以直接通过适用于 Exchange Online PowerShell 的远程 Windows PowerShell 访问构成客户租户报告的数据。这样，合作伙伴可以收集并保存报告数据，然后对其执行其他操作。打开远程连接后，检索有关客户租赁的报告数据与在客户租赁中运行任何 cmdlet 的效果是一样的。
  
在本文中，您使用适用于 Exchange Online 的远程 Windows PowerShell 连接到单个客户租赁并检索报告。默认情况下，Windows PowerShell 不支持聚合多个客户租赁中的报告数据。通过此过程检索的报告仅适用于您连接到的  _DelegatedOrg_。
  
 
## <a name="before-you-begin"></a>准备工作

- 您需要使用远程 Windows PowerShell 连接到您的 Exchange Online 租户。有关说明，请参阅[通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)。
    
## <a name="run-the-get-stalemailboxreport-sample"></a>运行 Get-StaleMailboxReport 示例

打开到 Exchange Online 的远程会话后，运行此命令可检索日期范围 03/25/2015 到 03/31/2015 的 **Get-StaleMailboxReport** 。
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

有许多其他报告 cmdlet 可用于 Exchange Online、Lync Online 和 SharePoint Online，还有其他报告 cmdlet 可用于您可以使用的邮件跟踪。若要了解有关可用的报告 cmdlet 和 Office 365 报告 Web 服务的详细信息，请参阅下一节中的主题。
  
## <a name="see-also"></a>另请参阅

#### 

[Office 365 报告 Web 服务](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Exchange Online 中的报告 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[适于合作伙伴的帮助](https://go.microsoft.com/fwlink/p/?LinkID=533477)

