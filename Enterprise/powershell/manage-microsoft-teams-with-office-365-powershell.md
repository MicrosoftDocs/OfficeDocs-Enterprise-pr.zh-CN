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
# <a name="manage-microsoft-teams-with-powershell"></a>使用 PowerShell 管理 Microsoft 团队

*此文章适用于 Microsoft 365 企业版和 Office 365 企业版。* 

您可以使用 PowerShell 管理 Microsoft 团队。
  
首先，安装[Microsoft 团队模块](https://www.powershellgallery.com/packages/MicrosoftTeams/)。
    
## <a name="sign-in-with-a-user-name-and-password"></a>使用用户名和密码登录

对于 Office 365 全球版（+ GCC）云：

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

对于 Office 365 美国政府 DoD 云： 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

对于 Office 365 美国政府版 GCC 高云：

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a>使用多重身份验证（MFA）登录

对于 Office 365 全球版（+ GCC）云：

```powershell
Connect-MicrosoftTeams
```

对于 Office 365 美国政府 DoD 云： 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

对于 Office 365 美国政府版 GCC 高云：

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a>断开与 Microsoft 团队的连接

请使用此命令：

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a>另请参阅

[团队 PowerShell 概述](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[使用 PowerShell 管理 Microsoft 365](manage-office-365-with-office-365-powershell.md)
  
[PowerShell for Microsoft 365 入门](getting-started-with-office-365-powershell.md)

