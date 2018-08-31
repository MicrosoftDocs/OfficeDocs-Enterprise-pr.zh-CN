---
title: 禁用 Office 365 的目录同步
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: 了解如何使用 PowerShell，将会关闭 Office 365 的目录同步
ms.openlocfilehash: f47209dd8b6be47b7ae7a4b63a9fae38c5cb498f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539767"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="df8c6-103">禁用 Office 365 的目录同步</span><span class="sxs-lookup"><span data-stu-id="df8c6-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="df8c6-p101">您可以使用 PowerShell 关闭目录同步。但是，不建议您关闭目录同步，作为故障排除步骤。如果您需要与排除目录同步问题的帮助，请参阅[正在修复 Office 365 的目录同步问题](fix-problems-with-directory-synchronization.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="df8c6-p101">You can use PowerShell to turn off directory synchronization. However, it is not recommended that you turn off directory synchronization as a troubleshooting step. If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="df8c6-107">如果需要业务产品的[联系人支持](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)。</span><span class="sxs-lookup"><span data-stu-id="df8c6-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="df8c6-108">关闭目录同步</span><span class="sxs-lookup"><span data-stu-id="df8c6-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="df8c6-109">若要关闭目录同步：</span><span class="sxs-lookup"><span data-stu-id="df8c6-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="df8c6-p102">首先，安装必需的软件并连接到 Office 365 订阅。有关说明，请参阅[连接到 Office 365 PowerShell 中](https://go.microsoft.com/fwlink/p/?LinkId=821938)。</span><span class="sxs-lookup"><span data-stu-id="df8c6-p102">First, install the required software and connect to your Office 365 subscription. For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="df8c6-112">使用[Set-msoldirsyncenabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)禁用目录同步：</span><span class="sxs-lookup"><span data-stu-id="df8c6-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```