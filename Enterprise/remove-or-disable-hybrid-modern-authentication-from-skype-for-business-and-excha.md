---
title: 从 Skype for Business 和 Exchange 删除或禁用混合新式验证
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
description: 如果已启用混合现代身份验证 (HMA) 仅要查找其不适用于您当前的环境，您可以禁用 HMA。本文介绍如何。
ms.openlocfilehash: fff9599641630386183ab9e1a0b8f597f0ba6e5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539775"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>从 Skype for Business 和 Exchange 删除或禁用混合新式验证

如果已启用混合现代身份验证 (HMA) 仅要查找其不适用于您当前的环境，您可以禁用 HMA。本文介绍如何。
  
## <a name="who-is-this-article-for"></a>谁是本文？

如果您已启用业务联机或本地和/或 Exchange Online 或内部部署中 Skype 的现代身份验证并找到您需要禁用 HMA，这些步骤是为您。
  
 **重要**如果您正在 Skype 业务联机或内部部署，请参阅[Skype 的业务拓扑支持现代身份验证](https://technet.microsoft.com/en-us/library/mt803262.aspx)文章、 具有混合拓扑 HMA，并且需要您在开始之前查看受支持的拓扑。
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>如何禁用混合现代身份验证 (Exchange)

1. **Exchange 内部部署**： 打开 Exchange Management Shell 并运行以下命令。 
    
1. Set-organizationconfig-OAuth2ClientProfileEnabled $false
    
2. Set-authserver-Identity evoSTS-IsDefaultAuthorizationEndpoint $false
    
2. **Exchange Online**： 连接到 Exchange Online 与 Remote PowerShell。运行以下命令以打开您*OAuth2ClientProfileEnabled*标志为 false。 
    
1. Set-organizationconfig-OAuth2ClientProfileEnabled: $false
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>如何禁用混合现代身份验证 (for Business 的 Skype)

1. **Skype 业务本地**： 业务命令行管理程序 Skype 中运行以下命令。
    
1. Set-csoauthconfiguration ClientAuthorizationOAuthServerIdentity""
    
2. **Skype for Business Online**： 业务联机使用远程 PowerShell 连接到 Skype。运行以下命令以禁用现代身份验证。 
    
1. Set-csoauthconfiguration ClientAdalAuthOverride 不允许
    
[现代身份验证概述的反向链接](hybrid-modern-auth-overview.md)。 
  

