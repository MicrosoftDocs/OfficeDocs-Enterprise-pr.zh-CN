---
title: 监视 Office 365 连接性
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: 部署 Office 365 后，可以使用下面的一些工具和技术保持 Office 36 5 连接。需要了解官方服务运行状况和连续性指南以及在慢速网络中使用 Office 365 的最佳做法。还需要获取 Office 365 管理员应用程序并为“Office 365 商业版 - 管理帮助”添加书签。
ms.openlocfilehash: ce307e01a3d7da4a24a06e58d293b9598c684d8f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070048"
---
# <a name="monitor-office-365-connectivity"></a>监视 Office 365 连接性

部署 Office 365 后，可以使用下面的一些工具和技术保持 Office 36 5 连接。需要了解官方[服务运行状况和连续性](https://technet.microsoft.com/library/office-365-service-health.aspx)指南以及[在慢速网络中使用 Office 365 的最佳做法](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。还需要获取 [Office 365 管理员应用程序](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/)并为 [Office 365 商业版 - 管理帮助](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)添加书签。
  
## <a name="monitoring-office-365-connectivity"></a>监视 Office 365 连接性

|||
|:-----|:-----|
|**获得有关新 Office 365 终结点的通知** <br/> |如果你要[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)，并且需要在我们发布新终结点时收到通知，可以使用自己喜欢的 RSS 阅读器订阅我们的 RSS 源。下面介绍了如何[通过 Outlook 进行订阅](https://go.microsoft.com/fwlink/p/?LinkId=532416)，或者，可以设置[通过电子邮件向你发送 RSS 源更新](https://go.microsoft.com/fwlink/p/?LinkId=532417)。<br/> |
|**使用 System Center 监视 Office 365** <br/> |如果你使用的是 Microsoft System Center，可以下载[适用于 Office 365 的 System Center 管理包](https://www.microsoft.com/download/details.aspx?id=43708)，以便立即开始监视 Office 365。有关详细指导，请参阅管理包操作指南或此博客文章：[使用 System Center Operations Manager 监视 Office365](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx) <br/> |
|**监视 Azure ExpressRoute 运行状况** <br/> |如果使用适用于 Office 365 的 Azure ExpressRoute 连接到 Office 365，则需要确保同时使用 Office 365 服务运行状况仪表板以及 Azure [通过 Azure 资源运行状况减少故障排除时间](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**将 Azure AD Connect Health 与 AD FS 一起使用** <br/> |如果你使用 AD FS 进行 Office 365 单一登录，则需要开始[使用 Azure AD Connect Health 监视 AD FS 基础结构](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)。  <br/> |
|**以编程方式监视 Office 365** <br/> |请参阅有关 [Office 365 管理 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) 的指南。  <br/> |

以下是可以用于返回的简短链接：[hhttps://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="see-also"></a>另请参阅

[配置 Office 365 企业版服务和应用程序](configure-services-and-applications.md)
  
[使组织为部署 Office 365 企业版做好准备](get-your-organization-ready-for-office-365.md)
  
[Office 365 的网络规划和性能优化](network-planning-and-performance.md)
  
[Office 365 与本地环境的集成](office-365-integration.md)
  
[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
