---
title: 使用 Office 365 PowerShell 管理 Microsoft 团队
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 摘要：使用 Office 365 PowerShell 管理 Microsoft 团队。
ms.openlocfilehash: 0f15d71558ddb5166090b067da06e0a6321a2b99
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209116"
---
# <a name="manage-microsoft-teams-with-office-365-powershell"></a><span data-ttu-id="92e4a-103">使用 Office 365 PowerShell 管理 Microsoft 团队</span><span class="sxs-lookup"><span data-stu-id="92e4a-103">Manage Microsoft Teams with Office 365 PowerShell</span></span>

<span data-ttu-id="92e4a-104">您可以使用 Office 365 PowerShell 管理 Microsoft 团队。</span><span class="sxs-lookup"><span data-stu-id="92e4a-104">You can manage Microsoft Teams with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="92e4a-105">首先，安装[Microsoft 团队模块](https://www.powershellgallery.com/packages/MicrosoftTeams/)。</span><span class="sxs-lookup"><span data-stu-id="92e4a-105">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="92e4a-106">使用用户名和密码登录</span><span class="sxs-lookup"><span data-stu-id="92e4a-106">Sign in with a user name and password</span></span>

<span data-ttu-id="92e4a-107">对于 Office 365 全球版（+ GCC）云：</span><span class="sxs-lookup"><span data-stu-id="92e4a-107">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="92e4a-108">对于 Office 365 美国政府 DoD 云：</span><span class="sxs-lookup"><span data-stu-id="92e4a-108">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="92e4a-109">对于 Office 365 美国政府版 GCC 高云：</span><span class="sxs-lookup"><span data-stu-id="92e4a-109">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="92e4a-110">使用多重身份验证（MFA）登录</span><span class="sxs-lookup"><span data-stu-id="92e4a-110">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="92e4a-111">对于 Office 365 全球版（+ GCC）云：</span><span class="sxs-lookup"><span data-stu-id="92e4a-111">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="92e4a-112">对于 Office 365 美国政府 DoD 云：</span><span class="sxs-lookup"><span data-stu-id="92e4a-112">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="92e4a-113">对于 Office 365 美国政府版 GCC 高云：</span><span class="sxs-lookup"><span data-stu-id="92e4a-113">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="92e4a-114">断开与 Microsoft 团队的连接</span><span class="sxs-lookup"><span data-stu-id="92e4a-114">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="92e4a-115">请使用此命令：</span><span class="sxs-lookup"><span data-stu-id="92e4a-115">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="92e4a-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92e4a-116">See also</span></span>

[<span data-ttu-id="92e4a-117">团队 PowerShell 概述</span><span class="sxs-lookup"><span data-stu-id="92e4a-117">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="92e4a-118">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="92e4a-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="92e4a-119">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="92e4a-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

