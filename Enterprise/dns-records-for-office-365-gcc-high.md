---
title: Office 365 GCC High DNS 记录
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 摘要：适用于 Office 365 的 DNS 记录（GCC 高）
hideEdit: true
ms.openlocfilehash: 9bcaa71ab965f01481887d50a3e6ddbbbe3fadee
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "44339779"
---
# <a name="dns-records-for-office-365-gcc-high"></a>Office 365 GCC High DNS 记录

*本文适用于 Office 365 GCC 高和 Microsoft 365 GCC 高*

作为加入 Office 365 GCC 的一部分，你需要将 SMTP 和 SIP 域添加到你的在线服务租户。  你将使用 Azure AD PowerShell 中的 MsolDomain cmdlet 执行此操作，或使用[Azure 政府门户](https://portal.azure.us)启动添加域和证明所有权的过程。

将你的域添加到租户并进行验证后，请使用以下指南为以下服务添加适当的 DNS 记录。  您可能需要修改下表，以适合组织的入站 MX 记录和任何现有的 Exchange 自动发现记录的相关需求。  强烈建议将这些 DNS 记录与邮件团队进行协调，以避免任何中断或电子邮件的误传递。

## <a name="exchange-online"></a>Exchange Online

| 类型 | 优先级 | 主机名 | 指向 "地址" 或 "值" | TTL |
| --- | --- | --- | --- | --- |
| MX | 0 | @ | *tenant*mail.protection.office365.us （有关其他详细信息，请参阅下文） | 1 Hour |
| TXT | - | @ | v = spf1 包括 include spf.protection.outlook.com-all | 1 小时 |
| CNAME | - | autodiscover | autodiscover.office365.us | 1 Hour |

### <a name="exchange-autodiscover-record"></a>Exchange 自动发现记录

如果您有本地 Exchange Server，我们建议您在迁移到 Exchange Online 时就地保留现有记录，并在完成迁移后立即更新该记录。 

### <a name="exchange-online-mx-record"></a>Exchange Online MX 记录

您的接受域的 MX 记录值遵循上面所述的标准*格式： mail.protection.office365.us*，将*租户*替换为默认租户名称的第一部分。

例如，如果您的租户名称为 contoso.onmicrosoft.us，则应使用**contoso.mail.protection.office365.us**作为 MX 记录的值。

## <a name="skype-for-business-online"></a>Skype for Business Online

### <a name="cname-records"></a>CNAME 记录

| 类型 | 主机名 | 指向 "地址" 或 "值" | TTL |
| --- | --- | --- | --- |
| CNAME | sip | sipdir.online.gov.skypeforbusiness.us | 1 小时 |
| CNAME | lyncdiscover | webdir.online.gov.skypeforbusiness.us | 1 Hour |

### <a name="srv-records"></a>SRV 记录

| 类型 | 服务 | 协议 | 端口 | 粗细 | Priority | 名称 | Target | TTL |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRV | \_sip | \_eap-tls | 443 | 1  | 100 | @ | sipdir.online.gov.skypeforbusiness.us | 1 Hour |
| SRV | \_sipfederationtls | \_rdp-tcp | 5061 | 1  | 100 | @ | sipfed.online.gov.skypeforbusiness.us | 1 Hour |

## <a name="additional-dns-records"></a>其他 DNS 记录

> [!IMPORTANT]
> 如果您的 DNS 区域中有一个现有的*msoid* CNAME 记录，则您必须在此时**删除**dns 中的记录。  Msoid 记录与 Microsoft 365 企业版应用程序 *（以前称为 Office 365 专业增强版）* 不兼容，并将阻止激活成功。
