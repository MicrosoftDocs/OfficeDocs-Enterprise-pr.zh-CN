---
title: 客户端连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 摘要：介绍了客户端计算机如何根据客户端计算机和 Office 365 租户数据中心的位置连接到 Office 365 租户。
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223034"
---
# <a name="client-connectivity"></a>客户端连接

 **摘要：** 介绍了客户端计算机如何根据客户端计算机和 Office 365 租户数据中心的位置连接到 Office 365 租户。
  
Office 365 驻留在世界各地的 Microsoft 数据中心帮助保留设置的服务和运行即使一个区域，如地震或停电中没有重大问题。当您连接到 Office 365 租户时，客户端连接将被定向到适当的数据中心到承载您的租户。由您与 Microsoft 的协议定义确定可以承载您的租户的规则。确定您的客户端如何获取该数据中心位置中的数据的规则取决于您正在使用的服务的体系结构。
  
例如，当您在登录到 Office 365 门户，您通常连接到最接近数据中心到客户端，然后定向根据服务使用下一步。如果您启动电子邮件，以显示用户界面的初始连接可能仍来自最近的数据中心，但第二个连接可能打开最近的数据中心之间的数据中心，您的租户所在的位置显示您什么是电子邮件在您阅读。Microsoft 运行世界上导致非常快速数据中心到 datacenter 连接 fast 顶部的十个网络之一。
  
阅读此文章后，您可能会明白为什么我们不提供[Office 365 Url 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)每个数据中心，它们只是太相互连接和依赖相互进行的可行。
  
如果使用的 Office 365 的 Azure ExpressRoute，在大多数情况下您连接将转通过专用连接到 Office 365 而不是公共此处描述的连接。有关如何客户端连接的原则准确。了解有关[Office 365 的 Azure ExpressRoute](azure-expressroute.md)。
  
有关业务网络请求 Skype 的深入，阅读文章[媒体质量和 Skype 业务 online 中的网络连接性能](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)。

||
|:-----|
| 本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)的一部分。|

> [!NOTE]
> 我们需要谨慎以使其安全和专用我们数据中心中管理客户数据。[信任中心](https://go.microsoft.com/fwlink/?LinkID=397383)中包含有关管理隐私我们采取的步骤的详细信息。
  
## <a name="connecting-to-the-nearest-datacenter"></a>连接到最接近数据中心

这是最常见类型的连接，并使用 Office 365 门户和 Exchange Online。在此情况下，当客户端尝试连接到 Office 365，其计算机的 DNS 查询确定其计算机来自的世界区域和 Office 365 将请求重定向到最近的数据中心。
  
连接到门户停止在最近的数据中心，并在客户端计算机将显示有关从该位置的客户端的租户的信息。
  
Exchange Online 转步骤进一步。一旦客户端计算机连接到最近的数据中心，该数据中心中的 Exchange 服务器连接到数据中心租户所在实际中所示*原理这工作部分*下方。Exchange Online 中最近的数据中心然后代理服务器到邮箱服务器从客户端计算机请求。这加快客户端计算机的体验通过移动繁重的检索电子邮件和日历项目与 Microsoft 网络。
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a>这如何工作的标准云产品？

此连接过程是标准对于高流量，高价值 web 应用程序类似于 Office 365。在此部分中，我们大纲，说明在进程中的步骤。当客户端计算机不是作为租户的同一区域中时，查找得多不同，具体取决于客户端连接到的服务连接。
  
 此图说明了在北美租户中使用标准的 Office 365 产品的客户。在此方案中，发出请求的人移动到欧洲，从该位置使用 Office 365。
  
1. 客户端计算机请求本地 DNS 服务器提供与 Office 365 关联的 IP 地址。

2. 客户端计算机的本地 DNS 服务器请求 Microsoft DNS 服务器提供与 Office 365 关联的 IP 地址。

3. Microsoft 的 DNS 服务器返回 （根据客户端的 DNS 服务器的位置），该区域的服务器的名称和客户端计算机重复步骤 1 和 2 来获得区域的 Office 365 数据中心的 IP 地址。

4. 客户端计算机连接到区域数据中心 IP 地址。

5. Exchange Online 服务器建立到客户租户所在的活动数据中心的连接。

![最近的区域数据中心](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a>Sovereign 此工作是如何云产品的？

此连接是 sovereign 云产品，例如 Office 365 由 21 Vianet 略有不同。与 Office 365 的 sovereign 实例中租户，将接受门户进行连接的最接近的 Office 365 服务器是租户所在的 sovereign 区域内的服务器。同样，访问 SharePoint Online 我们 sovereign 云或标准产品中的客户将被导向租户所在的前端服务器。请参阅连接到下面的活动数据中心。
  
1. 客户端计算机请求本地 DNS 服务器提供与 Office 365 关联的 IP 地址。

2. 客户端计算机的本地 DNS 服务器请求 Microsoft DNS 服务器提供与 Office 365 关联的 IP 地址。

3. Microsoft 的 DNS 服务器返回 （根据客户端的 DNS 服务器的位置），该区域的服务器的名称和客户端计算机重复步骤 1 和 2 来获得区域的 Office 365 数据中心的 IP 地址。

4. 客户端计算机连接到区域数据中心 IP 地址。

5. Exchange Online 服务器建立到客户租户所在的活动数据中心的连接。

![最近的区域美国数据中心](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a>连接到活动数据中心

连接到活动数据中心专为粗数据传输工作负荷和当前使用 SharePoint Online。在此情况下，当客户端尝试连接到 Office 365 时其浏览器将重定向到活动数据中心其 SharePoint Online 租户。
  
## <a name="how-does-this-work"></a>其工作方式如何？

当其他区域的客户端计算机连接到 SharePoint Online 时，则会将连接重定向至活动的 SharePoint Online 数据中心。在此方案中，客户使用服务的功能，从而门户剩余本地连接和定向到活动数据中心的 SharePoint Online 连接的标准。
  
1. 客户端计算机请求本地 DNS 服务器提供与 Office 365 关联的 IP 地址。

2. 客户端计算机的本地 DNS 服务器请求 Microsoft DNS 服务器提供与 Office 365 关联的 IP 地址。

3. Microsoft 的 DNS 服务器返回 （根据客户端的 Office 365 租户的位置），活动 SharePoint Online 数据中心的服务器名称和客户端计算机重复步骤 1 和 2 来获得的活动 Office 365 数据中心的 IP 地址。

4. 客户端计算机连接到活动数据中心 IP 地址。

![活动的美国数据中心](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a>通过虚拟专用网络 (VPN) 连接

此类型的连接适用仅虚拟专用网络 (VPN) 使用客户端计算机。Office 365 行为不只需更改事实上，因为使用了 VPN，但 Vpn 通常用于控制客户端计算机降级体验中建立连接到 Office 365 和通常结果的方式，因此它非常重要覆盖。
  
## <a name="how-does-this-work"></a>其工作方式如何？

当客户端计算机建立到公司办公不同区域中的 VPN 连接时，而不是在客户端计算机的位置的 DNS 服务器使用的 office 上的 DNS 服务器。在大多数情况下，此额外通过 VPN 连接将降低了 Office 365 体验。为最终用户尽可能接近服务客户连接到优化 Office 365 服务。许多服务利用 Azure 边缘网络、 内容传递网络和 Microsoft 网络上可靠网络容量，如接近客户端计算机进行 for Office 365 服务的网络请求时提供最佳的用户体验尽可能。
  
1. 客户端计算机请求 VPN DNS 服务器提供与 Office 365 关联的 IP 地址。

2. 客户端计算机的 VPN DNS 服务器请求 Microsoft DNS 服务器提供与 Office 365 关联的 IP 地址。

3. Microsoft 的 DNS 服务器返回 （基于位置的 VPN DNS 服务器） 的区域服务器名称，并在客户端计算机重复步骤 1 和 2 来获取区域的 Office 365 数据中心的 IP 地址信息。

4. 客户端计算机连接到数据中心在公司办公室，它们建立 VPN 连接与最接近的 IP 地址。

![VPN 数据中心连接](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
这是一个简短的链接，您可以使用回来：[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)
  
## <a name="see-also"></a>另请参阅

[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[与 Office 365 的网络连接](network-connectivity.md)
