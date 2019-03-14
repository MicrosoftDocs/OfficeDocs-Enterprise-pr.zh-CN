---
title: 从 Skype for business 和 Exchange 中删除或禁用混合新式身份验证
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
description: 如果您已启用混合新式身份验证 (HMA), 则可以禁用 HMA。 本文介绍如何操作。
ms.openlocfilehash: 4df044a8243bc6016f71c31d5b5cba7db901be98
ms.sourcegitcommit: 1d84e2289fc87717f8a9cd12c68ab27c84405348
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "30372839"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>从 Skype for business 和 Exchange 中删除或禁用混合新式身份验证

如果您已启用混合新式身份验证 (HMA), 则可以禁用 HMA。 本文介绍如何操作。
  
## <a name="who-is-this-article-for"></a>本文的目标是什么？

如果已在 Skype for business Online 或内部部署中启用新式验证, 以及/或 Exchange Online 或本地, 并且发现您需要禁用 HMA, 则这些步骤适用于您。

> [!IMPORTANT]
> 如果你在 Skype for business Online 或内部部署中, 请参阅 "[使用新式身份验证支持的 Skype for business 拓扑](https://technet.microsoft.com/en-us/library/mt803262.aspx)" 一文具有混合拓扑 HMA, 在开始之前, 需要查看受支持的拓扑。
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>如何禁用混合新式身份验证 (Exchange)

1. **exchange 本地**: 打开 exchange 命令行管理程序并运行以下命令: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **exchange online**: 使用远程 PowerShell[连接到 Exchange online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。 运行以下命令, 将您的*OAuth2ClientProfileEnabled*标志转换为 "false":

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>如何禁用混合新式身份验证 (Skype for business)

1. **skype**for business 本地: 在 skype for business 命令行管理程序中运行以下命令:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype for business online**: 使用远程 PowerShell[连接到 Skype for business online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) 。 运行以下命令以禁用新式验证:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[链接回新式验证概述](hybrid-modern-auth-overview.md)。 
  

