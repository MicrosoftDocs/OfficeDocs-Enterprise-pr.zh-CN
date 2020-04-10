---
title: Office 365 服务中的 IPv6 支持
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 摘要：介绍了 Microsoft Office 365 组件和 Office 365 政府产品中的 IPv6 支持。
ms.openlocfilehash: 13fd1cfef26f5e69c87f650c46f71071b72f2d15
ms.sourcegitcommit: 3aa6c61242c5691e3180a474ad059bd84c86dc9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2020
ms.locfileid: "43206539"
---
# <a name="ipv6-support-in-office-365-services"></a>Office 365 服务中的 IPv6 支持

*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*

Office 365 支持 IPv6 和 IPv4;但是，并不是所有的 Office 365 功能都完全启用了 IPv6。 这意味着，您必须同时使用 IPv4 和 IPv6 连接到 Office 365。 如果要筛选出出到 Office 365 的出站流量，则可以在[office 365 url 和 IP 地址范围](urls-and-ip-address-ranges.md)一文中找到 office 365 支持的 IPv6 地址的完整列表。 配置网络并允许适当的 IPv6 地址后，可以从 Microsoft 下载中心下载[Office 365 IPv6 测试计划](https://go.microsoft.com/fwlink/?LinkId=293447)。
  
## <a name="ipv6-support-in-office-365-subscription-service"></a>Office 365 订阅服务中的 IPv6 支持

### <a name="exchange-online-and-ipv6"></a>Exchange Online 和 IPv6

如果用于连接到 Exchange Online 的程序支持 IPv6，则它将在有线网络和无线网络上默认使用 IPv6。 如果要控制与 Exchange Online 的通信，请使用[Office 365 url 和 IP 地址范围](urls-and-ip-address-ranges.md)中的 IP 地址范围。
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online 和 IPv6

 **Office 365 政府 G1/G3/G4/K1**如果用于连接到 SharePoint Online 的程序支持 IPv6，则默认情况下它将尝试使用 IPv6。
  
 **公用多租户云**Microsoft 在你的请求中启用 SharePoint Online IPv6。 您需要为您的组织的 DNS 基础结构提供 CIDR 表示的 IP 地址。 请记住，其他组织无法共享此 DNS 基础结构，以便对租户启用 IPv6。 启用 IPv6 之后，如果用于连接到 SharePoint Online 的程序支持 IPv6，则默认情况下它使用 IPv6。
  
如果用于连接到 SharePoint Online 的程序支持 IPv6，则它将在有线网络和无线网络上默认使用 IPv6。 如果要控制与 SharePoint Online 的通信，请使用[Office 365 url 和 IP 地址范围](urls-and-ip-address-ranges.md)中的 IP 地址范围。
  
 **Office 365 政府 G1/G3/G4/K1**如果用于连接到 SharePoint Online 的程序支持 IPv6，则默认情况下它将尝试使用 IPv6。
  
### <a name="skype-for-business-and-ipv6"></a>Skype for Business 和 IPv6

请注意，Ipv4 在 Skype for Business 中不受支持，无法再启用。
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection 和 IPv6

如果通过传输层安全协议进行传输，则 Exchange Online Protection （EOP）支持 IPv6。 对于 EOP 范围，请使用[Office 365 url 和 IP 地址范围](urls-and-ip-address-ranges.md)。
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>适用于 Office 365 政府产品的 IPv6 支持

适用于政府产品的 office 365 IPv6 支持符合管理部门和机构的首席信息官的管理和预算（OMB）备忘录，以及联邦政府采用 Internet 协议版本6（IPv6）备忘录的情况。 [Microsoft Office 365 For 政府](https://go.microsoft.com/fwlink/p/?LinkId=325414)是一项多租户服务，可将美国政府数据存储在隔离的社区云中。 与其他 Office 365 产品一样，它提供了生产力和协作服务，包括 Exchange Online、Skype for Business、SharePoint Online 和 Office 365 专业增强版。 

Microsoft Office 365 政府版产品仅适用于2013及更高版本。 有关 Office 365 政府版产品的详细信息，请参阅[宣布 office 365 For 政府： A 美国政府社区云](https://go.microsoft.com/fwlink/p/?LinkId=325414)。 Arm 规章中的国际流量（ITAR）是一组美国政府管理法规，可控制美国英语的文章和服务的导出和导入[Munitions 列表（USML）](https://go.microsoft.com/fwlink/p/?LinkId=325415)。 

适用于企业的 microsoft Office 365 为 Microsoft 工作效率解决方案提供专用托管服务，这些服务支持要求美国联邦信息安全管理（FISMA）认证和商业实体受 ITAR 的安全、隐私和法规遵从性要求。
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>使用 IPv6 和 Office 365 时需要考虑的事项

我们建议您不要禁用 IPv6。 有关详细信息，请参阅本[指南文章](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users)。 若要确定网络中使用的 IP 版本，请考虑以下事项：
  
- 如果命令提示符处的**IPConfig**命令的显示包含名为 "IPv6 地址" 或 "临时 IPv6 地址" 的行，则您的环境中有 IPv6。

- 如果所有 IPv6 地址都以 "fe80" 开头，并且对应于名为 "Link Local IPv6 Address" 的行，则您的环境中没有 IPv6。

这些注意事项可能适用于您的网络：
  
- 公共订阅服务不支持通过 IPv6 通过信用卡购买。 这不适用于政府社区云（GCC），因为政府拥有企业协议（EA）许可。

- IPv6 不支持某些权限管理服务（RMS）方案。

- IPv6 不支持 BlackBerry® Enterprise Server （BE），因为 BlackBerry 不支持 IPv6。

- 如果将 Active Directory 联合身份验证服务（AD FS）与 Office 365 一起使用，则不支持使用 IPv6 将 AD FS 网络终结点播发到 Office 365。 使用 Exchange Online 时，不应在 AD FS DNS 条目中包含 AAAA 记录。 

以下是可以用于返回的简短链接：[https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>另请参阅

[IPv6 学习路线图](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[IPv6 生存指南](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
