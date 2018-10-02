---
title: Web 服务中未包含的其他 Office 365 IP 地址和 URL
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 9/13/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: 摘要：新端点 Web 服务不包含特定应用场景的少量端点。
hideEdit: true
ms.openlocfilehash: 4711f9b9560b0fab6d18700fcf3e933150861946
ms.sourcegitcommit: 0f98c342f80ffa21ec35bbf4ae5619b5e3271da5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2018
ms.locfileid: "23977347"
---
# <a name="additional-office-365-ip-addresses-and-urls-not-included-in-the-web-services"></a>Web 服务中未包含的其他 Office 365 IP 地址和 URL

某些网络终结点以前已发布，尚未包含在 Web 服务中。Web 服务范围是跨企业外围网络从 Office 365 的最终用户进行连接所需的网络终结点。目前不包括：

1. 从 Microsoft 数据中心到客户网络可能需要的网络连接（入站混合服务器网络流量）
2. 跨企业外围的客户网络上的服务器的网络连接（出站服务器网络流量）
3. 来自用户的网络连接要求的不常用方案
4. DNS 解析连接要求（未在下面列出）
5. Internet Explorer 或 Microsoft Edge 受信任的站点

除了 DNS 之外，这些对于大多数客户来说都是可选的，需要所描述的特定应用场景的情况除外。

|||||
|:-----|:-----|:-----|:-----|
| **行** | **用途** | **目标** | **类型** |
| 1  | [导入服务](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6)以进行 PST 和文件引入 | 有关其他要求，请参阅[导入服务](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6)。 | 不常用的出站方案 |
| 2  | [Microsoft Office 365 支持和恢复助手](https://diagnostics.office.com/#/) - 验证单一登录用户凭据。来源：<br> ```o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)``` <br> ```o365diagnosticworker-eus.cloudapp.net (104.211.54.134)```  | 本地安全令牌服务 | 入站服务器流量 |
| 3  | Azure AD Connect（带有 SSO 选项） - WinRM 和远程 PowerShell | 客户 STS 环境（AD FS 服务器和 AD FS 代理）\| TCP 端口 80 和 443 | 入站服务器流量 |
| 4  | ST FS，例如 AD FS 代理服务器（仅限联盟客户） | 客户 STS（例如 AD FS 代理）\| 端口 TCP 443 或 TCP 49443，带有 ClientTLS | 入站服务器流量 |
| 5  | [Exchange Online 统一消息/SBC 集成](https://technet.microsoft.com/library/jj673565.aspx) | 本地会话边界控制器和 *.um.outlook.com 之间的双向 | 仅出站服务器流量 |
| 6  | [Exchange 混合](https://docs.microsoft.com/exchange/exchange-deployment-assistant)共存功能，例如忙/闲共享。 | 客户本地 Exchange 服务器 | 入站服务器流量 |
| 7  | [Exchange 混合](https://docs.microsoft.com/exchange/exchange-deployment-assistant)代理身份验证 | 客户本地 STS | 入站服务器流量 |
| 8  | 用于使用 Exchange 混合配置向导配置 [Exchange 混合](https://docs.microsoft.com/exchange/exchange-deployment-assistant)。 <br> 注意：这些终结点仅用于配置 Exchange 混合  | TCP 端口 80 和 443 上的 ```domains.live.com```，仅用于 Exchange 2010 SP3 混合配置向导。 | 仅出站服务器流量 |
| 9  | AutoDetect 服务用于 [Exchange 混合](https://docs.microsoft.com/exchange/exchange-deployment-assistant)应用场景，可实现[适用于 iOS 和 Android 的 Outlook 的混合型新式验证](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) <BR> <BR> ```*.acompli.net``` <BR> ```*.outlookmobile.us``` <BR> <BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> | TCP 443 上的客户本地 Exchange 服务器 | 入站服务器流量 |
| 10  | **身份验证和标识 FQDN** <br> FQDN ```secure.aadcdn.microsoftonline-p.com``` 必须位于客户端的 Internet Explorer (IE) 或 Edge 受信任的站点区域内才能起作用。 |  | 受信任的站点 |
| 11  |  **Microsoft Teams FQDN** <br> 如果你使用的是 Internet Explorer 或 Microsoft Edge，则需要启用第一方和第三方 Cookie，并将 Teams FQDN 添加到受信任的站点。这是除上面列出的套件级 FQDN、CDN 和遥测之外的补充内容。有关详细信息，请参阅 [ Microsoft Teams 的已知问题](https://docs.microsoft.com/microsoftteams/known-issues)。 |  | 受信任的站点 |
| 12  |  **SharePoint Online 和 OneDrive for Business FQDN** <br> FQDN 中带有“\<tenant>”的所有“.sharepoint.com”FQDN 都需要在客户的 IE 或 Edge 受信任的站点区域中才能起作用。除了上面列出的套件级 FQDN、CDN 和遥测之外，还需要添加这些终结点。 |  | 受信任的站点 |
| 13  | **Yammer**  <br> Yammer 仅在浏览器中可用，并要求经过身份验证的用户通过代理传递。所有 Yammer FQDN 都需要在客户的 IE 或 Edge 受信任的站点区域中才能起作用。 |  | 受信任的站点 |

## <a name="related-topics"></a>相关主题

[管理 Office 365 终结点](managing-office-365-endpoints.md)
  
[排查 Office 365 连接故障](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[客户端连接](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[内容分发网络](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure 数据中心 IP 范围](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 公共 IP 空间](https://www.microsoft.com/download/details.aspx?id=53602)

