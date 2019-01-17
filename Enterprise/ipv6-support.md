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
ms.openlocfilehash: 82af5c7659b3c16c8e92b45b65b6868a404eca23
ms.sourcegitcommit: c5ee713709d76f519cb77de0e12c435d8409f571
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2019
ms.locfileid: "28327354"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="98966-103">Office 365 服务中的 IPv6 支持</span><span class="sxs-lookup"><span data-stu-id="98966-103">IPv6 support in Office 365 services</span></span>

 <span data-ttu-id="98966-104">**摘要**： 介绍了在 Microsoft Office 365 组件和 Office 365 政府版产品中的 IPv6 支持。</span><span class="sxs-lookup"><span data-stu-id="98966-104">**Summary**: Describes IPv6 support in Microsoft Office 365 components and in Office 365 government offerings.</span></span>
  
<span data-ttu-id="98966-p101">Office 365 支持 IPv6 和 IPv4;但是，不是所有的 Office 365 功能完全启用 ipv6。这意味着，您必须使用 IPv4 和 IPv6 连接到 Office 365。如果进行筛选到 Office 365 您出站通信，可以[Office 365 Url 和 IP 地址范围](urls-and-ip-address-ranges.md)一文中找到支持的 Office 365 的 IPv6 地址的完整列表。您的网络配置并允许相应的 IPv6 地址后，您可以下载[Office 365 IPv6 测试计划](https://go.microsoft.com/fwlink/?LinkId=293447)从 Microsoft 下载中心。</span><span class="sxs-lookup"><span data-stu-id="98966-p101">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6. This means that you must use both IPv4 and IPv6 to connect to Office 365. If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md). After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
||
|:-----|
| <span data-ttu-id="98966-109">本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="98966-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="98966-110">Office 365 订阅服务中的 IPv6 支持</span><span class="sxs-lookup"><span data-stu-id="98966-110">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="98966-111">Exchange Online 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="98966-111">Exchange Online and IPv6</span></span>

<span data-ttu-id="98966-p102">如果您使用连接到 Exchange Online 的程序支持 IPv6，它将有线和无线网络上的默认情况下使用 IPv6。如果您希望控制与 Exchange Online 的通信，请在[Office 365 Url 和 IP 地址范围](urls-and-ip-address-ranges.md)中使用的 IP 地址范围。</span><span class="sxs-lookup"><span data-stu-id="98966-p102">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="98966-114">SharePoint Online 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="98966-114">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="98966-115">**Office 365 政府版 G1/G3/G4/版 K1**如果您使用连接到 SharePoint Online 的程序支持 IPv6，它会默认情况下使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="98966-115">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="98966-p103">**公共多租户云**Microsoft 启用您的请求的 SharePoint Online IPv6。您需要提供 CIDR 表示该组织的 DNS 基础结构的 IP 地址。请记住，不能由租户启用 IPv6 的其他组织共享此 DNS 基础结构。启用 IPv6 时，如果您使用连接到 SharePoint Online 的程序支持 IPv6 后，将默认情况下使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="98966-p103">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request. You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure. Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant. After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="98966-p104">如果您使用连接到 SharePoint Online 的程序支持 IPv6，它将有线和无线网络上的默认情况下使用 IPv6。如果您希望控制与 SharePoint Online 的通信，请在[Office 365 Url 和 IP 地址范围](urls-and-ip-address-ranges.md)中使用的 IP 地址范围。</span><span class="sxs-lookup"><span data-stu-id="98966-p104">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
 <span data-ttu-id="98966-122">**Office 365 政府版 G1/G3/G4/版 K1**如果您使用连接到 SharePoint Online 的程序支持 IPv6，它会默认情况下使用 IPv6。</span><span class="sxs-lookup"><span data-stu-id="98966-122">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="98966-123">商业和 IPv6 的 Skype</span><span class="sxs-lookup"><span data-stu-id="98966-123">Skype for Business and IPv6</span></span>

<span data-ttu-id="98966-124">请注意 IPv6 Skype for Business 中不支持和不再可以启用。</span><span class="sxs-lookup"><span data-stu-id="98966-124">Please be aware IPv6 is not supported in Skype for Business and can no longer be enabled.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="98966-125">Exchange Online Protection 和 IPv6</span><span class="sxs-lookup"><span data-stu-id="98966-125">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="98966-p105">Exchange Online Protection (EOP) 支持 IPv6，如果通过传输层安全协议进行传输。对于 EOP 区域中，使用[Office 365 Url 和 IP 地址范围](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="98966-p105">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol. For the EOP range, use [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="98966-128">Office 365 政府版产品的 IPv6 支持</span><span class="sxs-lookup"><span data-stu-id="98966-128">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="98966-p106">Office 365 政府版产品的 IPv6 支持符合 Office 的管理和预算 (OMB) 备忘录的主管部门和机构，以及联邦政府应用的 Internet 协议版本 6 (IPv6 的首席信息官) 备忘录。[Microsoft Office 365 政府版](https://go.microsoft.com/fwlink/p/?LinkId=325414)是我们政府数据存储在隔离的社区云中多租户服务。像其他 Office 365 产品，它提供了工作效率和协作服务，包括 Exchange Online，Skype 的业务、 SharePoint Online 和 Office Professional Plus。</span><span class="sxs-lookup"><span data-stu-id="98966-p106">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum. [Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud. Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office Professional Plus.</span></span> 

<span data-ttu-id="98966-p107">Microsoft Office 365 政府版产品应用仅用于 2013年及更高版本。有关 Office 365 政府版产品的详细信息，请参阅[宣布 Office 365 政府版： 美国政府社区云](https://go.microsoft.com/fwlink/p/?LinkId=325414)。国际流量在 Arm 法规 (ITAR) 是一套美国政府法规，控制导出和导入防御相关的文章和[美国军需列表 (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)上的服务。</span><span class="sxs-lookup"><span data-stu-id="98966-p107">The Microsoft Office 365 government offerings apply only for 2013 and later. For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415).</span></span> 

<span data-ttu-id="98966-135">Microsoft Office 365 企业版提供支持安全、 隐私和法规遵从性要求我们需要确保联邦信息安全联邦机构的 Microsoft 生产力解决方案的专用托管的服务管理 (FISMA) 证书和 ITAR 受到商业实体。</span><span class="sxs-lookup"><span data-stu-id="98966-135">Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="98966-136">使用 IPv6 和 Office 365 时的注意事项</span><span class="sxs-lookup"><span data-stu-id="98966-136">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="98966-p108">我们建议您不要禁用 IPv6。有关详细信息，请参阅此[指南文章](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users)。若要确定您的网络上正在使用的哪些 IP 版本，请考虑以下方面：</span><span class="sxs-lookup"><span data-stu-id="98966-p108">We recommend that you do not disable IPv6. For more information, see this [guidance article](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="98966-140">如果**IPConfig**命令的命令提示符处显示包含名为"IPv6 地址"临时 IPv6 地址"行，您的环境中有 IPv6。</span><span class="sxs-lookup"><span data-stu-id="98966-140">If the display of the **IPConfig** command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="98966-141">如果所有 IPv6 地址以"fe80"开头，并且对应于名为"链接-本地 IPv6 地址"行中，您无需在您的环境中的 IPv6。</span><span class="sxs-lookup"><span data-stu-id="98966-141">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="98966-142">以下注意事项可能适用于您的网络：</span><span class="sxs-lookup"><span data-stu-id="98966-142">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="98966-p109">公共订阅服务不支持通过 IPv6 进行信用卡购买。这不适用于政府社区云 (GCC)，原因在于政府拥有企业协议 (EA) 授权。</span><span class="sxs-lookup"><span data-stu-id="98966-p109">The public subscription service does not support purchase by credit card over IPv6. This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="98966-145">IPv6 不支持某些权限管理服务 (RMS) 方案。</span><span class="sxs-lookup"><span data-stu-id="98966-145">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="98966-146">IPv6 不支持 BlackBerry® Enterprise Server (BES)，因为 BlackBerry 不支持 IPv6。</span><span class="sxs-lookup"><span data-stu-id="98966-146">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

- <span data-ttu-id="98966-p110">如果您使用 Office 365 使用 Active Directory 联合身份验证服务 (AD FS)，播发到 Office 365 您 AD FS 网络终结点使用 IPv6 不支持。使用 Exchange Online 时，不应在 AD FS DNS 条目中包括 AAAA 记录。</span><span class="sxs-lookup"><span data-stu-id="98966-p110">If you use Active Directory Federation Services (AD FS) with Office 365, advertising your AD FS network endpoint to Office 365 using IPv6 is not supported. You should not include AAAA records in the AD FS DNS entry when using Exchange Online.</span></span> 

<span data-ttu-id="98966-149">以下是可以用于返回的简短链接：[https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="98966-149">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="98966-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="98966-150">See also</span></span>

<span data-ttu-id="98966-151">[IPv6 学习路线图](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span><span class="sxs-lookup"><span data-stu-id="98966-151">[IPv6 Learning Roadmap](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span></span>
  
[<span data-ttu-id="98966-152">IPv6 生存指南</span><span class="sxs-lookup"><span data-stu-id="98966-152">IPv6 Survival Guide</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
