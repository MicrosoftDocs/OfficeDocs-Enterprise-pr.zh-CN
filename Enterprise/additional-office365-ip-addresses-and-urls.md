---
title: Office 365 IP 地址和 URL Web 服务中未包含的其他终结点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/04/2019
audience: Admin
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
description: 摘要：新终结点 Web 服务不包含特定应用场景的少量终结点。
hideEdit: true
ms.openlocfilehash: d124ac514e83c7cb9a2d8baf476b6a5880acb0ed
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068478"
---
# <a name="additional-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>Office 365 IP 地址和 URL Web 服务中未包含的其他终结点

某些网络终结点以前已发布，但尚未包含在 [Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)中。Web 服务范围是跨企业外围网络从 Office 365 用户进行连接所需的网络终结点。目前不包括：

1. 可能需要从 Microsoft 数据中心建立到客户网络的网络连接（入站混合服务器网络流量）。
2. 跨企业外围网络从客户网络上的服务器建立的网络连接（出站服务器网络流量）。
3. 用户的网络连接要求的不常用方案。
4. DNS 解析连接要求（未在下面列出）。
5. Internet Explorer 或 Microsoft Edge 受信任的站点。

除了 DNS 之外，这些对于大多数客户来说都是可选的，需要所描述的特定应用场景的情况除外。

|||||
|:-----|:-----|:-----|:-----|
| **行** | **用途** | **目标** | **类型** |
| 1  | [导入服务](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6)以进行 PST 和文件引入 | 有关其他要求，请参阅[导入服务](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6)。 | 不常用的出站方案 |
| 2  | [Microsoft Office 365 支持和恢复助手](https://diagnostics.office.com/#/) - 验证单一登录用户凭据。来源：<br> ```o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)``` <br> ```o365diagnosticworker-eus.cloudapp.net (104.211.54.134)```  | 本地安全令牌服务 | 入站服务器流量 |
| 3  | Azure AD Connect（带有 SSO 选项） - WinRM 和远程 PowerShell | 客户 STS 环境（AD FS 服务器和 AD FS 代理）\| TCP 端口 80 和 443 | 入站服务器流量 |
| 4  | ST FS，例如 AD FS 代理服务器（仅限联盟客户） | 客户 STS（例如 AD FS 代理）\| 端口 TCP 443 或 TCP 49443，带有 ClientTLS | 入站服务器流量 |
| 5  | [Exchange Online 统一消息/SBC 集成](https://technet.microsoft.com/library/jj673565.aspx) | 本地会话边界控制器和 *.um.outlook.com 之间的双向 | 仅出站服务器流量 |
| 6  | 邮箱迁移。从本地 [Exchange 混合部署](https://docs.microsoft.com/exchange/exchange-deployment-assistant)向 Office 365 进行邮箱迁移时，Office 365 将连接到你已发布的 Exchange Web 服务 (EWS)/邮箱复制服务 (MRS) 服务器。如果你需要了解 Exchange Online 服务器使用的 NAT IP 地址，以限制来自特定源 IP 范围的入站连接，可在“Exchange Online”服务区域下的 [Office 365 URL 和 IP 范围](urls-and-ip-address-ranges.md)中找到相关信息。请注意确保不会影响对已发布 EWS 端点（如 OWA）的访问，这就需要确保 MRS 代理会在限制来自特定源 IP 范围的 TCP 443 连接之前先解析至独立的 FQDN 和公共 IP 地址。 | 客户本地 EWS/MRS 代理<br> TCP 端口 443 | 入站服务器流量 |
| 7  | [Exchange 混合部署](https://docs.microsoft.com/exchange/exchange-deployment-assistant)共存功能，例如忙/闲共享。 | 客户本地 Exchange 服务器 | 入站服务器流量 |
| 8  | [Exchange 混合部署](https://docs.microsoft.com/exchange/exchange-deployment-assistant)代理身份验证 | 客户本地 STS | 入站服务器流量 |
| 9  | 用于使用 [Exchange 混合配置向导](https://docs.microsoft.com/exchange/hybrid-configuration-wizard)来配置 [Exchange 混合](https://docs.microsoft.com/exchange/exchange-deployment-assistant) <br> 注意：这些终结点仅用于配置 Exchange 混合  | TCP 端口 80 和 443 上的 domains.live.com，仅用于 Exchange 2010 SP3 混合配置向导。<BR> <BR> GCC High，DoD IP 地址：40.118.209.192/32；168.62.190.41/32 <BR> <BR> Worldwide Commercial & GCC: *.store.core.windows.net; asl.configure.office.com; mshrcstorageprod.blob.core.windows.net; tds.configure.office.com; mshybridservice.trafficmanager.net <BR>  | 仅出站服务器流量 |
| 10  | AutoDetect 服务用于 [Exchange 混合部署](https://docs.microsoft.com/exchange/exchange-deployment-assistant)应用场景，可实现[适用于 iOS 和 Android 的 Outlook 的混合型新式验证](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) <BR> <BR> ```*.acompli.net``` <BR> <BR> ```*.outlookmobile.com``` <BR> <BR> ```*.outlookmobile.us``` <BR> <BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> | TCP 443 上的客户本地 Exchange 服务器 | 入站服务器流量 |
| 11  | Office 2016 中的 Skype for Business 包括使用 UDP 端口的基于视频的屏幕共享。Office 2013 和早期版本中的先前 Skype for Business 客户端使用 RDP over TCP 端口 443。 | TCP 端口 443 对 52.112.0.0/14 开放 | Office 2013 和早期版本中的 Skype for Business 早期客户端版本 |
| 12  | Skype for Business 混合内部部署服务器与 Skype for Business Online 之间的连接 | 13.107.64.0/18，52.112.0.0/14 UDP 端口 50,000-59,999 <BR>  TCP 端口 50,000-59,999 | Skype for Business 内部部署服务器出站连接 |
| 13  | 具有内部部署混合连接的云 PSTN 要求网络连接对内部部署主机开放。有关 Skype for Business Online 混合配置的更多详细信息，  | 请参阅[ Skype for Business Server 和 Office 365 之间的混合连接](https://docs.microsoft.com/skypeforbusiness/hybrid/plan-hybrid-connectivity) | Skype for Business 内部部署混合入站 |
| 14  | **身份验证和标识 FQDN** <br> FQDN ```secure.aadcdn.microsoftonline-p.com``` 必须位于客户端的 Internet Explorer (IE) 或 Edge 受信任的站点区域内才能起作用。 |  | 受信任的站点 |
| 15  |  **Microsoft Teams FQDN** <br> 如果你使用的是 Internet Explorer 或 Microsoft Edge，则需要启用第一方和第三方 Cookie，并将 Teams FQDN 添加到受信任的站点。这是除 14 行列出的套件级 FQDN、CDN 和遥测之外的补充内容。有关详细信息，请参阅 [ Microsoft Teams 的已知问题](https://docs.microsoft.com/microsoftteams/known-issues)。 |  | 受信任的站点 |
| 16  |  **SharePoint Online 和 OneDrive for Business FQDN** <br> FQDN 中带有“\<tenant>”的所有“.sharepoint.com”FQDN 都需要在客户的 IE 或 Edge 受信任的站点区域中才能起作用。除了 14 行列出的套件级 FQDN、CDN 和遥测之外，还需要添加这些终结点。 |  | 受信任的站点 |
| 17  | **Yammer**  <br> Yammer 仅在浏览器中可用，并要求经过身份验证的用户通过代理传递。所有 Yammer FQDN 都需要在客户的 IE 或 Edge 受信任的站点区域中才能起作用。 |  | 受信任的站点 |

## <a name="related-topics"></a>相关主题

[管理 Office 365 终结点](managing-office-365-endpoints.md)
  
[排查 Office 365 连接故障](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[客户端连接](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[内容分发网络](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure 数据中心 IP 范围](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 公共 IP 空间](https://www.microsoft.com/download/details.aspx?id=53602)

