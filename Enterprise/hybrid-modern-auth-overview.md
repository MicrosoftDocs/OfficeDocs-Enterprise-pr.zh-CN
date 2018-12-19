---
title: 混合现代身份验证概述和使用内部部署 Skype 使用的业务和 Exchange 服务器的先决条件
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 10/02/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: 现代身份验证是一种身份管理提供更安全的用户身份验证和授权的方法。它是可用于业务服务器本地和 Exchange server 内部部署，以及业务混合的拆分域 Skype 的 Skype 的混合部署。此文章链接到相关文档有关先决条件，安装程序/禁用现代身份验证，以及某些相关的客户端 （如 Outlook 和 Skype 客户端） 信息。
ms.openlocfilehash: c10e5660d43ccce50497fccfd9d830d31ac07d55
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371106"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>混合现代身份验证概述和使用内部部署 Skype 使用的业务和 Exchange 服务器的先决条件

现代身份验证是一种身份管理提供更安全的用户身份验证和授权的方法。适用于 Office 365 混合部署的 Skype 的业务服务器本地和 Exchange server 内部部署，以及，业务混合的拆分域 Skype 它。此文章链接到相关文档有关先决条件，安装程序/禁用现代身份验证，以及某些相关的客户端 （如 Outlook 和 Skype 客户端） 信息。 
  
- [什么是现代身份验证？](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [有哪些变化时使用现代身份验证？](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [检查本地环境的现代身份验证状态](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [您是否满足现代身份验证系统必备组件？](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [了解在开始之前需要些什么？](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [现代身份验证 Url 的列表](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>什么是现代身份验证？
<a name="BKMK_WhatisModAuth"> </a>

当谈 （例如，便携式计算机或电话） 的客户端和服务器之间的通信，Microsoft 将使用短语现代身份验证。
  
现代身份验证是身份验证和授权方法，以及您可能已经熟悉的访问策略所依赖的一些安全措施的组合的总括性术语。它包括：
  
- **身份验证方法**： 多因素身份验证;客户端基于证书的身份验证;和 Active Directory 身份验证库 ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx))。
    
- **授权方法**： Open Authorization (OAuth) Microsoft 的实现。 
    
- **条件访问策略**： 移动应用程序管理 (MAM) 和 Azure Active Directory 条件访问。 
    
管理现代身份验证的用户标识为管理员提供了许多不同的工具来使用方面保护资源和提供更安全的身份管理这两个内部部署 （Exchange 和 for Business 的 Skype） 方法时，Exchange 混合和 Skype 业务混合/拆分域方案。
  
请注意，因为与 Exchange 紧密合作 for Business 的 Skype，用户会看到的业务客户端的登录行为 Skype 将会影响 Exchange 的现代身份验证状态。如果您有业务拆分域混合 Skype，也将应用此问题。此外，支持使用现代身份验证的业务混合的 Skype 的类型通常称为拆分域 （拆分域中具有业务 online Skype 和 Skype 的业务上-prem，并且用户都驻留在两个位置）。
  
> [!IMPORTANT]
> 您知道，从 2017 年 8 月，所有新的 Office 365 租户，包括 for Business 的 Skype online 和 Exchange online 会默认启用的现代身份验证吗？事先租户都不会有更改，在其默认 MA 状态，但新的所有租户自动都支持的扩展您看到上面列出的标识功能集。若要联机检查 for Business 的 Skype MA 状态，您可以用于 Skype 业务 online PowerShell 中使用全局管理员凭据。运行`Get-CsOAuthConfiguration`检查-ClientADALAuthOverride 的输出。如果-ClientADALAuthOverride 允许您现代的身份验证已打开。 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>有哪些变化时使用现代身份验证？
<a name="BKMK_WhatChanges"> </a>

当业务或 Exchange 服务器，使用内部部署 Skype 现代身份验证，您仍*进行身份验证*的用户内部部署，但的*授权*案例资源 （如文件或电子邮件） 更改其访问。尽管现代身份验证，客户端和服务器的通信，evoSTS （安全令牌服务使用的 Azure AD） 中的 configuring MA 结果期间所采取的步骤，这是原因，正在将设置身份验证服务器为 Skype 的业务和 Exchange server 内部部署。 
  
对 evoSTS 的更改允许在本地服务器的授权客户端，充分利用 OAuth （令牌颁发），并还允许在云中 （如多因素身份验证） 常见您的本地使用安全方法。此外，evoSTS 颁发令牌，允许用户请求资源的访问权限，而无需为请求的一部分提供自己的密码。无论您的用户位于 (的联机或本地)，和哪些位置承载所需的资源，无论 EvoSTS 将成为现代身份验证的配置后，授权用户和客户端的核心。
  
下面是一个示例的含义。如果需要访问 Exchange 服务器获取代表用户的日历信息 Skype 业务客户端，它使用 Active Directory 身份验证库 (ADAL) 时才这样。ADAL 代码库旨在使您目录中的受保护的资源可使用 OAuth 安全令牌的客户端应用程序。ADAL 适用于 OAuth 验证声明和 exchange 令牌 （而不是密码），以授予用户对资源的访问。过去，类似如下-知道如何验证用户声明和问题所需的令牌的服务器-事务中的证书颁发机构可能已安全令牌服务内部部署或甚至 Active Directory 联合身份验证服务。但是，现代身份验证集中化与云中的 Azure Active Directory (Azure AD) 的证书颁发机构。
  
这也意味着，即使您的 Exchange server 和 Skype 的业务环境可能完全内部部署、 授权服务器将处于联机状态，并且您的内部部署环境必须能够创建和维护与您的办公室的连接在云中 （和您的订阅用作其目录的 Azure Active Directory 实例） 的 365 订阅。
  
什么也不会更改？无论您是在拆分域混合或 Skype 用于业务和 Exchange server 内部部署中，所有用户首先必须进行身份都验证*内部部署*。在现代的身份验证的混合实现，Lyncdiscovery 和自动发现是指向您的本地服务器。 
  
> [!IMPORTANT]
> 如果您需要知道业务拓扑支持 MA 的特定 Skype，这是[记录此处](https://technet.microsoft.com/en-us/library/mt803262.aspx)。
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>检查本地环境的现代身份验证状态
<a name="BKMK_CheckStatus"> </a>

因为现代身份验证更改时服务利用 OAuth/S2S 使用授权服务器，您需要知道现代身份验证的业务和 Exchange 环境您 Skype 是否是打开还是关闭。您可以通过运行检查业务服务器，内部部署 Exchange 或 Skype 上的状态`Get-CSOAuthConfiguration`在 PowerShell 命令。如果该命令将返回 OAuthServers 属性为空，则会禁用现代身份验证。
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>您是否满足现代身份验证系统必备组件？

验证并继续之前检查这些项目关闭您的列表：
  
- **特定于业务的 Skype**
    
  - 所有服务器都必须都具有 SFB 服务器 2015 CU5 或更高版本
    
  - **异常**-生存能力 Branch Appliance (SBA) 可以位于当前版本 （基于 Lync 2013） 
    
  - 您的 SIP 域添加作为 Office 365 中的联盟域
    
  - 所有 SFB 前端必须都能够连接到 internet，到 Office 365 身份验证 Url (TCP 443) 出站和 Office 365 Url 和 IP，行 56 和 125 的[Microsoft 365 常见和 Office Online 部分中列出已知证书根 Crl (TCP 80)地址范围](urls-and-ip-address-ranges.md)。
    
 **注释**如果您 Skype 业务前端服务器使用代理服务器访问 Internet，必须在每个前端的 web.config 文件的配置部分中输入使用的代理服务器 IP 和端口号。 
  
- 为业务服务器 2015\Web Components\Web C:\Program Files\Skype ticket\int\web.config
    
- 为业务服务器 2015\Web Components\Web C:\Program Files\Skype ticket\ext\web.config
    
```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="http://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```
    
> [!IMPORTANT]
> 请务必订阅 RSS 源获取有关[Office 365 Url 和 IP 地址范围](urls-and-ip-address-ranges.md)可保持最新列表的所需的 Url。 
  
- **Exchange Server 特定**
    
  - 您将任一 Exchange server 2013 CU19 向上，或 Exchange server 2016 CU8 和设置。
    
  - 没有任何环境中的 Exchange server 2010。
    
  - 未配置 SSL 卸载。支持 SSL 终止并重新加密。
    
  - 在事件环境使用代理服务器基础结构，若要允许服务器连接到 Internet，确保所有 Exchange 服务器都具有[InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx)属性中定义的代理服务器。
    
- **Exchange 客户端和协议要求**
  
  - 以下客户端支持现代身份验证：

  |**客户端**|**主要协议**|**备注**|
  |:-----|:-----|:-----|
  |Outlook 2013 和 Outlook 2016  <br/> |MAPI over HTTP  <br/> |MAPI over HTTP 必须启用 Exchange 中才能将现代身份验证与这些客户端 （通常启用或 True 新安装的 Exchange 2013 Service Pack 1）; 结合使用有关详细信息，请参阅[如何现代身份验证适用于 Office 2013 和 Office 2016 客户端应用程序](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016)。  <br/> 确保您正在运行的 Outlook; 最小必需的生成请参阅[最新版本的使用 Windows Installer (MSI) 的 Outlook 更新](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi)。  <br/> |
  |Outlook 2016 for Mac  <br/> |Exchange Web 服务  <br/> |  <br/> |
  |Outlook for iOS 和 Outlook for Android  <br/> |  <br/> |有关详细信息，请参阅[使用 hybrid 现代 Authentication with Outlook for iOS 和 Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) 。  <br/> |
  |Exchange ActiveSync 客户端 （例如，iOS11 邮件）  <br/> |Exchange ActiveSync  <br/> |对于支持现代身份验证的 Exchange ActiveSync 客户端，必须以从基本身份验证切换到现代身份验证重新创建配置文件。  <br/> |

- **常规系统必备组件**
    
  - 如果您使用 ADFS，您应具有 Windows 2012 R2 ADFS 3.0 及以上的联合身份验证
    
  - 标识配置的任何支持 AAD 连接的类型 (如密码哈希同步，传递身份验证，内部部署 STS 支持的 Office 365，et cetera。)
    
  - 您必须 AAD 连接配置和用户复制和同步正常工作。
    
  - 您已验证的混合使用您在本地和 Office 365 之间：
    
  - Exchange 混合部署的正式支持语句指出您必须具有当前 CU 或当前 CU-1。
    
  - 确保同时进行内部部署测试用户，以及混合测试用户驻留在 Office 365 中，可以登录到业务桌面客户端 （如果您想要使用与 Skype 的现代的身份验证） Skype 和 Microsoft Outlook （如果需要，以便使用现代身份验证Exchange)。
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>了解在开始之前需要些什么？
<a name="BKMK_Whatelse"> </a>

1. 在本地服务器的所有方案都涉及现代身份验证本地设置 （实际上的 Skype for Business 没有受支持的拓扑的列表） 以便负责身份验证和授权的服务器处于 Microsoft 云 （AAD 的安全令牌服务，名为 evoSTS），并更新 Azure Active Directory (AAD) 有关的 Url 或本地安装的任一 Skype 适用于商务或 Exchange 使用的命名空间。因此，在本地服务器承担 Microsoft 云依赖关系。执行此操作无法视为配置混合身份验证。
    
2. 此文章链接出到其他人将帮助您选择的支持 （仅对业务的 Skype 有必要），现代的身份验证拓扑和操作方法文章的大纲安装步骤，或步骤禁用现代的身份验证的 Exchange 内部部署和 for Business 的 Skype 本地。收藏此页面在浏览器中如果您将需要主页库 server 环境中使用现代的身份验证。
    
## <a name="list-of-modern-authentication-urls"></a>现代身份验证 Url 的列表
<a name="BKMK_URLListforMA"> </a>

- [如何配置 Exchange Server 内部部署用于现代身份验证](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [Skype 的业务拓扑支持现代身份验证](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [如何配置用于业务本地的 Skype 用于现代身份验证](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [从 Skype for Business 和 Exchange 删除或禁用混合新式验证](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

