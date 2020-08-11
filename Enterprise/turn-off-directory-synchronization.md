---
title: 关闭 Microsoft 365 的目录同步
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: 在本文中，查找有关使用 PowerShell 关闭 Microsoft 365 的目录同步的信息。
ms.openlocfilehash: 815d20ff6a0697f1533e44305e20e61a9282312b
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46603644"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="6790b-103">关闭 Microsoft 365 的目录同步</span><span class="sxs-lookup"><span data-stu-id="6790b-103">Turn off directory synchronization for Microsoft 365</span></span>
<span data-ttu-id="6790b-104">您可以使用 PowerShell 关闭目录同步。</span><span class="sxs-lookup"><span data-stu-id="6790b-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="6790b-105">但是，不建议您将目录同步作为故障排除步骤关闭。</span><span class="sxs-lookup"><span data-stu-id="6790b-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="6790b-106">如果您需要有关对目录同步进行故障排除的帮助，请参阅[解决 Microsoft 365 文章的目录同步问题](fix-problems-with-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="6790b-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="6790b-107">如果需要，[请联系](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)业务产品支持人员。</span><span class="sxs-lookup"><span data-stu-id="6790b-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="6790b-108">关闭目录同步</span><span class="sxs-lookup"><span data-stu-id="6790b-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="6790b-109">若要关闭目录同步，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="6790b-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="6790b-110">首先，安装所需的软件并连接到 Microsoft 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="6790b-110">First, install the required software and connect to your Microsoft 365 subscription.</span></span> <span data-ttu-id="6790b-111">有关说明，请参阅[连接到适用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="6790b-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="6790b-112">使用[MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)禁用目录同步：</span><span class="sxs-lookup"><span data-stu-id="6790b-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
><span data-ttu-id="6790b-113">如果使用此命令，则必须等待72小时，然后才能重新打开目录同步。</span><span class="sxs-lookup"><span data-stu-id="6790b-113">If you use this command, you must wait 72 hours before you can turn directory synchronization back on.</span></span>
>
 
