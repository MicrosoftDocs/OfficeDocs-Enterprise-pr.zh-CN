---
title: 使用 Office 365 PowerShell 查看授权和未授权的用户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: 介绍如何使用 Office 365 PowerShell 查看授权和未授权的用户帐户。
ms.openlocfilehash: 61f94664a62b6a5cb178579c1a5777b208d0b2ec
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123359"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="15bdf-103">使用 Office 365 PowerShell 查看授权和未授权的用户</span><span class="sxs-lookup"><span data-stu-id="15bdf-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="15bdf-104">**摘要：** 介绍如何使用 Office 365 PowerShell 查看许可和非许可用户帐户。</span><span class="sxs-lookup"><span data-stu-id="15bdf-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="15bdf-p101">您的 Office 365 组织中的用户帐户可能已从组织提供的许可计划中分配到部分或全部可用的许可证，或者未分配到任何许可证。您可以使用 Office 365 PowerShell 快速查找您组织中的授权和未授权的用户。</span><span class="sxs-lookup"><span data-stu-id="15bdf-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="15bdf-107">准备工作</span><span class="sxs-lookup"><span data-stu-id="15bdf-107">Before you begin</span></span>

- <span data-ttu-id="15bdf-p102">若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="15bdf-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="15bdf-110">如果使用 **Get-MsolUser** cmdlet，而未使用 _-All_ 参数，只返回前 500 个帐户。</span><span class="sxs-lookup"><span data-stu-id="15bdf-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="viewing-licensed-and-unlicensed-users"></a><span data-ttu-id="15bdf-111">查看许可和未许可用户</span><span class="sxs-lookup"><span data-stu-id="15bdf-111">Viewing licensed and unlicensed users</span></span>

<span data-ttu-id="15bdf-112">若要查看组织中所有用户帐户及其授权状态的列表，请在 Office 365 PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="15bdf-112">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="15bdf-113">若要查看组织中所有未授权用户帐户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="15bdf-113">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="15bdf-114">若要查看组织中所有授权用户帐户的列表，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="15bdf-114">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="15bdf-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15bdf-115">See also</span></span>

<span data-ttu-id="15bdf-116">有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="15bdf-116">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="15bdf-117">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="15bdf-117">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="15bdf-118">Where-Object</span><span class="sxs-lookup"><span data-stu-id="15bdf-118">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

