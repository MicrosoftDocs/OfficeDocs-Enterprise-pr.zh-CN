---
title: 使用 PowerShell 管理 Microsoft 团队
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 摘要：使用 PowerShell 管理 Microsoft 团队。
ms.openlocfilehash: 8958c6ec6f0c17c21461cbee4cb1a6441ceed8d6
ms.sourcegitcommit: 132c97bd5e0dbe469da64356ace5084b71419cea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "45429186"
---
# <a name="manage-microsoft-teams-with-powershell"></a><span data-ttu-id="6371e-103">使用 PowerShell 管理 Microsoft 团队</span><span class="sxs-lookup"><span data-stu-id="6371e-103">Manage Microsoft Teams with PowerShell</span></span>

<span data-ttu-id="6371e-104">*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* </span><span class="sxs-lookup"><span data-stu-id="6371e-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="6371e-105">您可以使用 PowerShell 管理 Microsoft 团队。</span><span class="sxs-lookup"><span data-stu-id="6371e-105">You can manage Microsoft Teams with PowerShell.</span></span>
  
<span data-ttu-id="6371e-106">首先，安装[Microsoft 团队模块](https://www.powershellgallery.com/packages/MicrosoftTeams/)。</span><span class="sxs-lookup"><span data-stu-id="6371e-106">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="6371e-107">使用用户名和密码登录</span><span class="sxs-lookup"><span data-stu-id="6371e-107">Sign in with a user name and password</span></span>

<span data-ttu-id="6371e-108">对于 Office 365 全球版（+ GCC）云：</span><span class="sxs-lookup"><span data-stu-id="6371e-108">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="6371e-109">对于 Office 365 美国政府 DoD 云：</span><span class="sxs-lookup"><span data-stu-id="6371e-109">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="6371e-110">对于 Office 365 美国政府版 GCC 高云：</span><span class="sxs-lookup"><span data-stu-id="6371e-110">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="6371e-111">使用多重身份验证（MFA）登录</span><span class="sxs-lookup"><span data-stu-id="6371e-111">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="6371e-112">对于 Office 365 全球版（+ GCC）云：</span><span class="sxs-lookup"><span data-stu-id="6371e-112">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="6371e-113">对于 Office 365 美国政府 DoD 云：</span><span class="sxs-lookup"><span data-stu-id="6371e-113">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="6371e-114">对于 Office 365 美国政府版 GCC 高云：</span><span class="sxs-lookup"><span data-stu-id="6371e-114">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="6371e-115">断开与 Microsoft 团队的连接</span><span class="sxs-lookup"><span data-stu-id="6371e-115">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="6371e-116">请使用此命令：</span><span class="sxs-lookup"><span data-stu-id="6371e-116">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="6371e-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6371e-117">See also</span></span>

[<span data-ttu-id="6371e-118">团队 PowerShell 概述</span><span class="sxs-lookup"><span data-stu-id="6371e-118">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="6371e-119">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="6371e-119">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="6371e-120">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="6371e-120">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

