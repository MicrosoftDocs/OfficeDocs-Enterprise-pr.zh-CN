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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: 了解如何使用 PowerShell 关闭 Office 365 的目录同步
ms.openlocfilehash: 4fbfb6b9e3fcb1512fc4aa9c3d8ee6c37682e58a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085071"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="0caa7-103">禁用 Office 365 的目录同步</span><span class="sxs-lookup"><span data-stu-id="0caa7-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="0caa7-p101">您可以使用 PowerShell 关闭目录同步。但是, 不建议您将目录同步作为故障排除步骤关闭。如果您需要有关对目录同步进行故障排除的帮助, 请参阅[解决 Office 365 文章中的目录同步问题](fix-problems-with-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="0caa7-p101">You can use PowerShell to turn off directory synchronization. However, it is not recommended that you turn off directory synchronization as a troubleshooting step. If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="0caa7-107">如果需要,[请联系](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)业务产品支持人员。</span><span class="sxs-lookup"><span data-stu-id="0caa7-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="0caa7-108">关闭目录同步</span><span class="sxs-lookup"><span data-stu-id="0caa7-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="0caa7-109">若要关闭目录同步, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="0caa7-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="0caa7-p102">首先, 安装所需的软件并连接到 Office 365 订阅。有关这两种情况的说明, 请参阅[连接到 Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938)。</span><span class="sxs-lookup"><span data-stu-id="0caa7-p102">First, install the required software and connect to your Office 365 subscription. For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="0caa7-112">使用[MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)禁用目录同步:</span><span class="sxs-lookup"><span data-stu-id="0caa7-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```