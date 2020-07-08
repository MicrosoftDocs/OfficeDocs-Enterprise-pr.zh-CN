---
title: 混合新式身份验证概述和用于本地 Skype for Business 和 Exchange 服务器的先决条件
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
ms.date: 04/15/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: 新式身份验证是标识管理的一种方法，可提供更安全的用户身份验证和授权。 它可用于本地的 Skype for Business server 本地和 Exchange server 的混合部署，以及拆分域 Skype for Business 混合。 本文链接到有关先决条件、设置/禁用新式身份验证和一些相关客户端的相关文档（如 Outlook 和 Skype 客户端）信息。
ms.openlocfilehash: 056262ade67b8ffd452f68cc0c5e3882326b2e44
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052415"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>混合新式身份验证概述和在本地 Skype for Business 和 Exchange 服务器上使用它的先决条件

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

_新式身份验证_是标识管理的一种方法，可提供更安全的用户身份验证和授权。 它适用于 Skype for business server 本地和 Exchange server 本地部署的 Office 365 混合部署，以及拆分域 Skype for Business 混合部署。 本文链接到有关先决条件、设置/禁用新式身份验证和一些相关客户端的相关文档（如 Outlook 和 Skype 客户端）信息。
  
- [什么是新式身份验证？](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [使用新式验证时有哪些变化？](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [检查您的本地环境的新式身份验证状态](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [您是否满足新式身份验证先决条件？](#do-you-meet-modern-authentication-prerequisites)
- [在开始之前，我还需要了解哪些信息？](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>什么是新式身份验证？
<a name="BKMK_WhatisModAuth"> </a>

新式验证是一项用于在客户端（例如，便携式计算机或电话）和服务器之间进行身份验证和授权方法组合的伞，以及一些依赖您可能已经熟悉的访问策略的安全措施。 其中包括：
  
- **身份验证方法**：多因素身份验证（MFA）;智能卡身份验证;基于客户端证书的身份验证
- **授权方法**： Microsoft 的开放授权实施（OAuth）
- **条件访问策略**：移动应用程序管理（MAM）和 Azure Active Directory （azure AD）条件访问

使用新式身份验证管理用户标识，可以让管理员在保护资源时使用多种不同的工具，并为内部部署（Exchange 和 Skype for business）、Exchange 混合和 Skype for business 混合/拆分域方案提供更安全的身份管理方法。
  
请注意，由于 Skype for business 与 Exchange 密切合作，因此 Exchange 的新式验证状态将影响 Skype for Business 客户端用户将看到的登录行为。 如果你拥有 Skype for business_拆分域_混合体系结构（其中既有 skype For business Online），又有 skype for business 本地，并且用户驻留在这两个位置，则也适用。

有关 Office 365 中的新式验证的详细信息，请参阅[office 365 客户端应用程序支持-新式验证](office-365-client-support-modern-authentication.md)。
  
> [!IMPORTANT]
> 从2017年8月起，包括 Skype for Business online 和 Exchange online 的所有新的 Office 365 租户默认启用新式身份验证。 预先存在的租户在其默认 MA 状态中不会发生更改，但所有新租户都会自动支持您在上面列出的一组已扩展的标识功能。 若要检查您的 MA 状态，请参阅[检查本地环境的新式验证状态](hybrid-modern-auth-overview.md#BKMK_CheckStatus)部分。
  
## <a name="what-changes-when-i-use-modern-authentication"></a>使用新式验证时有哪些变化？
<a name="BKMK_WhatChanges"> </a>

将新式验证与本地 Skype for Business 或 Exchange server 一起使用时，仍对本地用户进行*身份*验证，但*授权*他们访问资源（如文件或电子邮件）的情景也会发生变化。 这就是为什么新式验证是客户端和服务器通信的原因，在 evoSTS 中配置 MA 结果时所执行的步骤（Azure AD 使用的安全令牌服务）被设置为 Skype for business 和本地 Exchange server 的身份验证服务器。
  
对 evoSTS 的更改允许您的内部部署服务器利用 OAuth （令牌颁发）来授权客户端，还允许您的本地使用云中常见的安全方法（如多重身份验证）。 此外，evoSTS 还会发出令牌，使用户可以请求访问资源，而无需在请求中提供其密码。 无论您的用户驻留在何处（联机或本地），无论哪个位置承载所需的资源，EvoSTS 将成为在配置新式身份验证后授权用户和客户端的核心。
  
例如，如果 Skype for Business 客户端需要访问 Exchange server 以代表用户获取日历信息，则它使用 Active Directory 身份验证库（ADAL）执行此操作。 ADAL 是一个代码库，旨在使用 OAuth 安全令牌使目录中的安全资源对客户端应用程序可用。 ADAL 与 OAuth 配合使用，以验证声明和交换令牌（而不是密码），以授予用户对资源的访问权限。 过去，事务中的颁发机构（如此类）—知道如何验证用户声明并发出所需令牌的服务器可能是本地的安全令牌服务，甚至是 Active Directory 联合身份验证服务。 但是，新式验证使用 Azure AD 对该颁发机构进行了集中。
  
这也意味着，尽管您的 Exchange server 和 Skype for business 环境可能完全位于本地，但授权服务器将处于联机状态，并且您的本地环境必须能够创建和维护与云中的 Office 365 订阅的连接（以及您的订阅用作其目录的 Azure AD 实例）。
  
不会发生什么变化？ 无论你是处于拆分域混合还是使用 Skype for Business 和本地 Exchange server，所有用户都必须先*在本地*进行身份验证。 在新式验证的混合实施中， _Lyncdiscovery_和_自动发现_都指向您的本地服务器。
  
> [!IMPORTANT]
> 如果需要了解 MA 支持的特定 Skype for Business 拓扑，请[在此处记录](https://technet.microsoft.com/library/mt803262.aspx)。
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>检查您的本地环境的新式身份验证状态
<a name="BKMK_CheckStatus"> </a>

由于新式验证会更改服务利用 OAuth/S2S 时使用的授权服务器，你需要知道是否为本地 Skype for Business 和 Exchange 环境启用或禁用新式身份验证。 您可以通过运行以下 PowerShell 命令检查 Exchange 服务器上的状态：

```powershell
Get-OrganizationConfig | ft OAuth*
```

如果_OAuth2ClientProfileEnabled_属性的值为**False**，则会禁用新式验证。

有关 Set-organizationconfig cmdlet 的详细信息，请参阅[set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/get-organizationconfig)。

您可以通过运行以下 PowerShell 命令检查您的 Skype for Business 服务器：

```powershell
Get-CSOAuthConfiguration
```

如果该命令返回一个空的_OAuthServers_属性，或者不**允许** _ClientADALAuthOverride_属性的值，则会禁用新式身份验证。

有关 Set-csoauthconfiguration cmdlet 的详细信息，请参阅[set-csoauthconfiguration](https://docs.microsoft.com/powershell/module/skype/get-csoauthconfiguration)。
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>您是否满足新式身份验证先决条件？

请先验证并检查列表中的这些项，然后再继续操作：
  
- **Skype for business 特定**
  - 对于 Skype for Business Server 2015 或更高版本，所有服务器必须具有2017累积更新（CU5）
    - **异常**留存分支设备（SBA）可以在当前版本上（基于 Lync 2013）
  - 您的 SIP 域作为 Office 365 中的联合域添加
  - 所有 SFB 前端必须具有到 internet 的出站连接，在[office 125 url 和 IP 地址范围](urls-and-ip-address-ranges.md)的 "Microsoft 365 Common and Office" 部分的行56和365中列出了 Office 365 身份验证 URL （tcp 443）和众所周知的证书根 CRL （tcp 80）。
  
- **混合 Office 365 环境中的 Skype for business 本地部署**
  - 一个 Skype for business Server 2019 部署，其中包含运行 Skype for Business Server 2019 的所有服务器。
  - 一个 Skype for business Server 2015 部署，其中包含运行 Skype for Business Server 2015 的所有服务器。
  - 一种部署，其最多包含两个不同的服务器版本，如下所示：
    - Skype for Business Server 2015
    - Skype for Business Server 2019
  - 所有 Skype for business 服务器都必须安装最新的累积更新，请参阅[Skype For Business Server 更新](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates)以查找和管理所有可用的更新。
  - 混合环境中没有 Lync Server 2010 或2013。

>[!NOTE]
>如果 Skype for Business 前端服务器使用代理服务器进行 Internet 访问，则必须在每个前端的 web.config 文件的 "配置" 部分中输入所使用的代理服务器 IP 和端口号。
  
- C:\Program Files\Skype for Business Server 2015 \ Web Components\Web ticket\int\web.config
- C:\Program Files\Skype for Business Server 2015 \ Web Components\Web ticket\ext\web.config

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</configuration>
```

> [!IMPORTANT]
> 请务必订阅[Office 365 url 和 IP 地址范围](urls-and-ip-address-ranges.md)的 RSS 源，以了解所需 url 的最新列表。
  
- **特定于 Exchange Server**
  - 您使用的是 Exchange server 2013 CU19 和 up，Exchange server 2016 CU8 和 up，或 Exchange Server 2019 CU1 和 up。
  - 环境中没有 Exchange server 2010。
  - 未配置 SSL 卸载。 支持 SSL 终止和重新加密。
  - 在您的环境使用代理服务器基础结构以允许服务器连接到 Internet 时，请确保所有 Exchange 服务器都在[InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx)属性中定义了代理服务器。
  
- **混合 Office 365 环境中的本地 Exchange Server**

  - 如果使用的是 Exchange Server 2013，则必须至少有一台服务器安装了邮箱和客户端访问服务器角色。 虽然可以在单独的服务器上安装邮箱和客户端访问角色，但强烈建议您在同一台服务器上安装这两个角色，以提供更高的可靠性和改进的性能。
  - 如果您使用的是 Exchange server 2016 或更高版本，则必须至少有一台服务器安装了邮箱服务器角色。
  - 混合环境中没有 Exchange server 2007 或2010。
  - 所有 Exchange 服务器都必须安装最新的累积更新，请参阅将[Exchange 升级到最新累积更新](https://docs.microsoft.com/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019)以查找和管理所有可用更新。

- **Exchange 客户端和协议要求**
  
  - 以下客户端支持新式身份验证：

  |**客户端**|**主要协议**|**备注**|
  |:-----|:-----|:-----|
  |Outlook 2013 和 Outlook 2016  <br/> |MAPI over HTTP  <br/> |必须在 Exchange 中启用 MAPI over HTTP，才能将新式验证用于这些客户端（通常为 Exchange 2013 Service Pack 1 及更高版本启用或设置为启用）;有关详细信息，请参阅[office 2013 和 office 2016 客户端应用的新式身份验证的工作方式](https://docs.microsoft.com/office365/enterprise/modern-auth-for-office-2013-and-2016)。  <br/> 确保您运行的是所需的最低版本的 Outlook;[有关使用 Windows Installer （MSI）的 Outlook 版本，](https://docs.microsoft.com/officeupdates/outlook-updates-msi)请参阅最新更新。  <br/> |
  |Outlook 2016 for Mac  <br/> |Exchange Web 服务  <br/> |  <br/> |
  |Outlook for iOS 和 Outlook for Android  <br/> |  <br/> |有关详细信息，请参阅[结合使用混合新式身份验证和 Outlook For iOS 和 Outlook For Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) 。  <br/> |
  |Exchange ActiveSync 客户端（例如，iOS11 邮件）  <br/> |Exchange ActiveSync  <br/> |对于支持新式身份验证的 Exchange ActiveSync 客户端，必须重新创建配置文件，才能从基本身份验证切换到新式身份验证。  <br/> |

- **一般先决条件**
  - 如果使用 ADFS，则应具有 Windows 2012 R2 ADFS 3.0 和更高版本的联合身份验证
  - 您的身份配置是 Azure AD Connect 支持的任何类型（例如，密码哈希同步、传递身份验证、Office 365 支持的本地 STS 等）。
  - Azure AD Connect 已配置并在进行用户复制和同步时运行。
  - 您已验证是否使用 Exchange 经典混合拓扑模式在本地和 Office 365 环境中配置混合。 Exchange 混合的官方支持声明说，您必须具有当前 CU 或当前 CU-1。
    > [!NOTE]
    > [混合代理](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent)不支持混合新式身份验证。

  - 确保本地测试用户和在 Office 365 中托管的混合测试用户可以登录到 Skype for Business 桌面客户端（如果要将新式验证用于 Skype）和 Microsoft Outlook （如果要将新式验证用于 Exchange）。

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>在开始之前，我还需要了解哪些信息？
<a name="BKMK_Whatelse"> </a>

- 内部部署服务器的所有方案都涉及在本地设置新式身份验证（事实上，对于 Skype for business，存在受支持拓扑的列表），以便负责身份验证和授权的服务器位于 Microsoft 云中（Azure AD 的安全令牌服务，称为 "evoSTS"）中，并更新 Azure AD，以了解本地安装的 Skype for Business 或 Exchange 所使用的 Url 或命名空间。 因此，内部部署服务器采用 Microsoft 云依赖关系。 采取此操作可能会被视为配置 "混合身份验证"。
- 本文链接到的其他用户将帮助您选择受支持的新式身份验证拓扑（仅适用于 Skype for business），以及概述了安装步骤的操作方法文章，或者为 Exchange 本地和 Skype for Business 本地部署了禁用新式身份验证的步骤。 如果您需要在您的服务器环境中使用新式验证的总部，请将此页面收藏在浏览器中。

## <a name="related-topics"></a>相关主题
<a name="BKMK_URLListforMA"> </a>

- [如何将 Exchange Server 本地配置为使用新式验证](configure-exchange-server-for-hybrid-modern-authentication.md)
- [新式验证支持的 Skype for business 拓扑](https://technet.microsoft.com/library/mt803262.aspx)
- [如何配置 Skype for Business 本地以使用新式验证](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [从 Skype for Business 和 Exchange 删除或禁用混合新式验证](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
