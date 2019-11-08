---
title: 从 Skype for Business 和 Exchange 删除或禁用混合新式验证
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
description: 如果您已启用混合新式身份验证（HMA），则可以禁用 HMA。 本文介绍如何操作。
ms.openlocfilehash: 9f1236775f60fdb37ab12cd7cfb7eabd9763466d
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031597"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>从 Skype for Business 和 Exchange 删除或禁用混合新式验证

如果您已启用混合新式身份验证（HMA），则可以禁用 HMA。 本文介绍如何操作。
  
## <a name="who-is-this-article-for"></a>本文的目标是什么？

如果已在 Skype for Business Online 或内部部署中启用新式验证，以及/或 Exchange Online 或本地，并且发现您需要禁用 HMA，则这些步骤适用于您。

> [!IMPORTANT]
> 如果你在 Skype for Business Online 或内部部署中，请参阅 "[使用新式身份验证支持的 Skype For business 拓扑](https://technet.microsoft.com/library/mt803262.aspx)" 一文具有混合拓扑 HMA，在开始之前，需要查看受支持的拓扑。
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>如何禁用混合新式身份验证（Exchange）

1. **Exchange 本地**：打开 Exchange 命令行管理程序并运行以下命令： 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange online**：使用远程 PowerShell[连接到 Exchange online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。 运行以下命令，将您的*OAuth2ClientProfileEnabled*标志转换为 "false"：

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>如何禁用混合新式身份验证（Skype for Business）

1. **Skype**for business 本地：在 Skype For Business 命令行管理程序中运行以下命令：

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype for Business online**：使用远程 PowerShell[连接到 Skype for business online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) 。 运行以下命令以禁用新式验证：

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[链接回新式验证概述](hybrid-modern-auth-overview.md)。 
  

