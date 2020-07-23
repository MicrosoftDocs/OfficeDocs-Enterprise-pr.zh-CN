---
title: 使用适用于 Microsoft 365 的 PowerShell 禁用对 Sway 的访问
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 7221a4c9-ae03-4598-81fe-a655c02f40ab
description: 了解在何处下载可让您在 Microsoft 365 组织中禁用对 Sway 的访问的 ManageSway.ps1 PowerShell 脚本。
ms.openlocfilehash: d02a197e2767a1883abcc8fcb4074f3ac92de88a
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230698"
---
# <a name="disable-access-to-sway-with-powershell-for-microsoft-365"></a><span data-ttu-id="e1467-103">使用适用于 Microsoft 365 的 PowerShell 禁用对 Sway 的访问</span><span class="sxs-lookup"><span data-stu-id="e1467-103">Disable access to Sway with PowerShell for Microsoft 365</span></span>

<span data-ttu-id="e1467-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="e1467-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="e1467-105">通过 ManageSway.ps1 PowerShell 脚本，您可以查看和禁用 Microsoft 365 组织中的服务，包括 Sway。</span><span class="sxs-lookup"><span data-stu-id="e1467-105">The ManageSway.ps1 PowerShell script lets you view and disable services in your Microsoft 365 organization, including Sway.</span></span> <span data-ttu-id="e1467-106">此脚本可以自动执行以下主题中描述的过程：</span><span class="sxs-lookup"><span data-stu-id="e1467-106">This script automates the procedures that are described in the following topics:</span></span>
  
- [<span data-ttu-id="e1467-107">使用 PowerShell 查看许可证和服务</span><span class="sxs-lookup"><span data-stu-id="e1467-107">View licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="e1467-108">使用 PowerShell 禁用对服务的访问</span><span class="sxs-lookup"><span data-stu-id="e1467-108">Disable access to services with PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
<span data-ttu-id="e1467-109">你需要下载与此脚本相关联的两个文件：</span><span class="sxs-lookup"><span data-stu-id="e1467-109">You need to download the two files that are associated with the script:</span></span>
  
- <span data-ttu-id="e1467-110">ManageSway.ps1 脚本（位于 [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)）</span><span class="sxs-lookup"><span data-stu-id="e1467-110">The ManageSway.ps1 script at [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span></span>
    
- <span data-ttu-id="e1467-111">该脚本的帮助文件（位于 [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)）</span><span class="sxs-lookup"><span data-stu-id="e1467-111">The help file for the script at [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span></span>
    

