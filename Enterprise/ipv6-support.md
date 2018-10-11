---
title: Office 365 服务中的 IPv6 支持
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 摘要： 介绍了在 Microsoft Office 365 组件和 Office 365 政府版产品中的 IPv6 支持。
ms.openlocfilehash: ed06f1eac3c6a3d631445db1d623bd25c62a309c
ms.sourcegitcommit: ae7f2087d51698d3c5ef371888278544a7046205
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2018
ms.locfileid: "25493827"
---
# <a name="ipv6-support-in-office-365-services"></a>Office 365 服务中的 IPv6 支持

 **摘要**： 介绍了在 Microsoft Office 365 组件和 Office 365 政府版产品中的 IPv6 支持。
  
Office 365 支持 IPv6 和 IPv4;但是，不是所有的 Office 365 功能完全启用 ipv6。这意味着，您必须使用 IPv4 和 IPv6 连接到 Office 365。如果进行筛选到 Office 365 您出站通信，可以[Office 365 Url 和 IP 地址范围](https://go.microsoft.com/fwlink/?LinkId=293744)一文中找到支持的 Office 365 的 IPv6 地址的完整列表。您的网络配置并允许相应的 IPv6 地址后，您可以下载[Office 365 IPv6 测试计划](https://go.microsoft.com/fwlink/?LinkId=293447)从 Microsoft 下载中心。
  
||
|:-----|
| 本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)的一部分。|

## <a name="ipv6-support-in-office-365-subscription-service"></a>Office 365 订阅服务中的 IPv6 支持

### <a name="exchange-online-and-ipv6"></a>Exchange Online 和 IPv6

如果您使用连接到 Exchange Online 的程序支持 IPv6，它将有线和无线网络上的默认情况下使用 IPv6。如果您希望控制与 Exchange Online 的通信，请在[Office 365 Url 和 IP 地址范围](https://go.microsoft.com/fwlink/?LinkId=293744)中使用的 IP 地址范围。
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online 和 IPv6

 **Office 365 政府版 G1/G3/G4/版 K1**如果您使用连接到 SharePoint Online 的程序支持 IPv6，它会默认情况下使用 IPv6。
  
 **公共多租户云**Microsoft 启用您的请求的 SharePoint Online IPv6。您需要提供 CIDR 表示该组织的 DNS 基础结构的 IP 地址。请记住，不能由租户启用 IPv6 的其他组织共享此 DNS 基础结构。启用 IPv6 时，如果您使用连接到 SharePoint Online 的程序支持 IPv6 后，将默认情况下使用 IPv6。
  
如果您使用连接到 SharePoint Online 的程序支持 IPv6，它将有线和无线网络上的默认情况下使用 IPv6。如果您希望控制与 SharePoint Online 的通信，请在[Office 365 Url 和 IP 地址范围](https://go.microsoft.com/fwlink/?LinkId=293744)中使用的 IP 地址范围。
  
 **Office 365 政府版 G1/G3/G4/版 K1**如果您使用连接到 SharePoint Online 的程序支持 IPv6，它会默认情况下使用 IPv6。
  
### <a name="skype-for-business-and-ipv6"></a>商业和 IPv6 的 Skype

Microsoft 将您的请求和 Office 365 政府版 G1/G3/G4/版 K1 订阅公共多租户云中，为 for Business 的 Skype 启用 IPv6。它启用时，如果您使用连接到业务的 Skype 的程序支持 IPv6 后，它将默认情况下使用 IPv6。如果您希望控制与 Skype 的业务通信，请在[Office 365 Url 和 IP 地址范围](https://go.microsoft.com/fwlink/?LinkId=293744)中使用的 IP 地址范围。
  
请注意 IPv6 所有区域中不可用，Microsoft 可能无法在能够为您的租户激活这一次。
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection 和 IPv6

Exchange Online Protection (EOP) 支持 IPv6，如果通过传输层安全协议进行传输。对于 EOP 区域中，使用[Office 365 Url 和 IP 地址范围](https://go.microsoft.com/fwlink/?LinkId=293744)。
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Office 365 政府版产品的 IPv6 支持

Office 365 政府版产品的 IPv6 支持符合 Office 的管理和预算 (OMB) 备忘录的主管部门和机构，以及联邦政府应用的 Internet 协议版本 6 (IPv6 的首席信息官) 备忘录。[Microsoft Office 365 政府版](https://go.microsoft.com/fwlink/p/?LinkId=325414)是我们政府数据存储在隔离的社区云中多租户服务。像其他 Office 365 产品，它提供了工作效率和协作服务，包括 Exchange Online，Skype 的业务、 SharePoint Online 和 Office Professional Plus。Microsoft Office 365 政府版产品应用仅用于 2013年及更高版本。有关 Office 365 政府版产品的详细信息，请参阅[宣布 Office 365 政府版： 美国政府社区云](https://go.microsoft.com/fwlink/p/?LinkId=325414)。国际流量在 Arm 法规 (ITAR) 是一套美国政府法规，控制导出和导入防御相关的文章和[美国军需列表 (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)上的服务。Microsoft Office 365 企业版提供支持安全、 隐私和法规遵从性要求我们需要确保联邦信息安全联邦机构的 Microsoft 生产力解决方案的专用托管的服务管理 (FISMA) 证书和 ITAR 受到商业实体。
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>使用 IPv6 和 Office 365 时的注意事项

我们建议您不要禁用 IPv6。有关详细信息，请参阅[针对 Microsoft Windows IPv6： 常见问题解答](https://go.microsoft.com/fwlink/p/?LinkId=325418)。若要确定您的网络上正在使用的哪些 IP 版本，请考虑以下方面：
  
- 如果 IPConfig 命令的命令提示符处显示包含名为"IPv6 地址"临时 IPv6 地址"行，您的环境中有 IPv6。

- 如果所有 IPv6 地址以"fe80"开头，并且对应于名为"链接-本地 IPv6 地址"行中，您无需在您的环境中的 IPv6。

以下注意事项可能适用于您的网络：
  
- 公共订阅服务不支持通过 IPv6 进行信用卡购买。这不适用于政府社区云 (GCC)，原因在于政府拥有企业协议 (EA) 授权。

- IPv6 不支持某些权限管理服务 (RMS) 方案。

- IPv6 不支持 BlackBerry® Enterprise Server (BES)，因为 BlackBerry 不支持 IPv6。

- 如果您使用 Office 365 使用 Active Directory 联合身份验证服务 (AD FS)，播发到 Office 365 您 AD FS 网络终结点使用 IPv6 不支持。使用 Exchange Online 时，不应在 AD FS DNS 条目中包括 AAAA 记录。 

以下是可以用于返回的简短链接：[https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>另请参阅

[Microsoft 技术位置纸张](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[TCP/IP v4 和 v6](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[IPv6 生存指南](https://go.microsoft.com/fwlink/p/?LinkID=237480)
