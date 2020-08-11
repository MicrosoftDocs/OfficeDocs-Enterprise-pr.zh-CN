---
title: 监视 Microsoft 365 连接
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: 在本文中，您将了解可用于监视和维护 Microsoft 365 连接的工具和技术。
ms.openlocfilehash: 791352910cf82bf4d43543166cb4b1e974f9a238
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606858"
---
# <a name="monitor-microsoft-365-connectivity"></a>监视 Microsoft 365 连接

部署 Microsoft 365 后，可以使用下面的一些工具和技术来维护 Microsoft 365 连接。 你将需要了解官方[服务运行状况和连续性](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity)准则以及我们[在慢速网络上使用 Microsoft 365 的最佳做法](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)。 你还需要获取[microsoft 365 管理应用](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/)并[为 microsoft 365 For Business-管理员帮助](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791)添加书签。
  
## <a name="monitoring-microsoft-365-connectivity"></a>监视 Microsoft 365 连接

|||
|:-----|:-----|
|**收到新的 Microsoft 365 终结点通知** <br/> |如果你正在[管理 Microsoft 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)，则需要在发布新终结点时接收通知，你可以使用你喜爱的 rss 阅读器订阅我们的 rss 源。 下面介绍如何[通过 Outlook 进行订阅](https://go.microsoft.com/fwlink/p/?LinkId=532416)，或者您可以通过[电子邮件将 rss 源更新到您](https://go.microsoft.com/fwlink/p/?LinkId=532417)。  <br/> |
|**使用 System Center 监视 Microsoft 365** <br/> |如果使用的是 Microsoft System Center，可以下载适用于[Office 365 的 System Center 管理包](https://www.microsoft.com/download/details.aspx?id=43708)，以便立即开始监视 Microsoft 365。 有关更多详细指导，请参阅管理包操作指南或此博客文章[Office365 使用 System 中心 Operations Manager 进行监视](https://blogs.msdn.com/b/mvpawardprogram/archive/2015/07/08/office365-monitoring-using-system-centre-operations-manager.aspx) <br/> |
|**监视 Azure ExpressRoute 运行状况** <br/> |如果使用 Azure ExpressRoute for Microsoft 365 连接到 Microsoft 365，您需要确保使用的是 Microsoft 365 服务运行状况仪表板以及 azure[资源运行状况降低故障排除时间](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**将 Azure AD Connect Health 与 AD FS 一起使用** <br/> |如果要使用 AD FS 进行单一登录（使用 Microsoft 365），则需要开始[使用 AZURE AD Connect Health 来监视 AD fs 基础结构](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-health-adfs/)。  <br/> |
|**以编程方式监视 Microsoft 365** <br/> |请参阅我们关于[Microsoft 365 管理 API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview)的指导。  <br/> |

以下是可以用于返回的简短链接：[https://aka.ms/monitorconnectivity365](https://aka.ms/monitorconnectivity365)
  
## <a name="related-topics"></a>相关主题

[配置 Microsoft 365 企业版服务和应用程序](configure-services-and-applications.md)
  
[为你的组织准备好 Microsoft 365 企业版](get-your-organization-ready-for-office-365.md)
  
[Microsoft 365 网络计划和性能优化](network-planning-and-performance.md)
  
[Microsoft 365 与本地环境的集成](office-365-integration.md)
  
[管理 Microsoft 365 终结点](managing-office-365-endpoints.md)
