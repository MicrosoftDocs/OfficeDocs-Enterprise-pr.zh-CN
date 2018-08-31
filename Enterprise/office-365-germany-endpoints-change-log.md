---
title: Office 365 德国终结点更改日志
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid: MOE150
ms.assetid: 980041c9-7984-44b2-95f0-af66743543a1
ms.openlocfilehash: e77d6fc3b8136f39ed75ef21b0ff417a4ad6465a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539770"
---
# <a name="office-365-germany-endpoints-change-log"></a>Office 365 德国终结点更改日志

*应用于： Office 365 管理*

## <a name="list-of-changes-to-the-endpoints-required-for-office-365-germany"></a>对所需的 Office 365 德国的终结点的更改列表

下表列出了对[Office 365 德国终结点](office-365-germany-endpoints.md)的更改。
  
|"日期"|**更改**|
|:-----|:-----|
|1/24/2017  <br/> |初始发布的文章。  <br/> |
|2/28/2017  <br/> |添加 3 Fqdn;1 / [有效 4/1/2017。必需： Office 365 门户和共享。ExpressRoute: 否。www.office.de]，2 / [有效 4/1/2017。必需： Office 365 门户和共享。ExpressRoute: 否。office.de]，3 / [有效 4/1/2017。必需： Office 365 门户和共享。ExpressRoute: 否。officehome.msocdn.de]。 注释： 添加其他门户 Fqdn。 添加 2 IP_Sets;1 / [有效 4/1/2017。必需： Office 365 门户和共享。ExpressRoute: 否。 51.5.245.67/32]，2 / [有效 4/1/2017。必需： Office 365 门户和共享。ExpressRoute: 否。 51.4.227.178/32]。说明： 添加其他门户终结点。添加 2 IP_Sets;1 / [有效 4/1/2017。必需： Office 365 门户和共享。ExpressRoute: 否。 2a01:4180:2001::92]，2 / [有效 4/1/2017。必需： Office 365 门户和共享。ExpressRoute: 否。 2a01:4180:2401::11f]。说明： 添加其他门户终结点。  <br/> |
|3/8/2017  <br/> |添加 1 Fqdn;1 / [有效 3/8/2017。必需： OneDrive for Business。ExpressRoute: 否。spoprod-a.akamaihd.net]。说明： 添加其他 CDN 终结点。  <br/> |
|3/31/2017  <br/> |添加 3 Fqdn;1 / [有效 5/1/2017。必需： SharePoint Online 混合。\*。 search.production.de.azuretrafficmanager.de]，2 / [有效 5/1/2017。必需： SharePoint Online 混合。login.microsoftonline.de]，3 / [有效 5/1/2017。必需： SharePoint Online 混合。provisioningapi.microsoftonline.de]。 注释： 添加 Sharepoint 混合 Fqdn。  <br/> |
|6/1/2017  <br/> |添加 2 Fqdn 有效 7/1/2017年  <br/> shellprod.msocdn.de  <br/> r1.res.office365.com  <br/> |
|6/26/2017  <br/> |替换为自动发现\*。 Autodiscover.outlook.de 和自动发现 outlook.office.de outlook.de。  <br/> |
|9/29/2017  <br/> |添加 3 Fqdn;1 / [有效 11/1/2017。  <br/> cegsignup.microsoft.de  <br/> negsignup.microsoft.de  <br/> \*。 svc.ms  <br/> |
|1/16/2018  <br/> |添加 1 Fqdn;1 / [有效 2/1/2018。必需： Office 365 门户。ExpressRoute: 否。webshell.suite.office.de]。 注释： 添加其他 Office 365 套件命令行管理程序的 FQDN。添加 4 IP_Sets;1 / [有效 2/1/2018。必需： Office 365 门户。ExpressRoute: 否。 51.5.242.163/32]，2 / [有效 2/1/2018。必需： Office 365 门户。ExpressRoute: 否。 51.4.226.115/32]、 3 / [有效 2/1/2018。必需： Office 365 门户。ExpressRoute: 否。 2a01:4180:2401::33b / 4 / [有效 2/1/2018。必需： Office 365 门户。ExpressRoute: 否。 2a01:4180:2001::234 / 注释： 添加附加的 IP 地址的 Office 365 套件命令行管理程序。  <br/> |
|2/5/2018  <br/> |添加 1 FQDN; 1 / [有效 3/1/2018。必需： 门户和共享。ExpressRoute: 是。webshell.suite.office.de]。 注释： 添加用于门户网站和共享 Fqdn。 添加 2 IP_Sets; URL1 / [有效 3/1/2018。必需： 门户和共享。ExpressRoute: 是。51.5.242.163/32]。，2 / [有效 3/1/2018。必需： 门户和共享。ExpressRoute: 是。51.4.226.115/32]。说明： 添加新前缀门户和共享。添加 2 IP_Sets;1 / [有效 3/1/2018。必需： 门户和共享。ExpressRoute: 是。2a01:4180:2401::33b / 128]。，2 / [有效 3/1/2018。必需： 门户和共享。ExpressRoute: 是。2a01:4180:2001::234 / 128]。说明： 添加新前缀门户和共享。添加 1 IP_Sets;1 / [有效 3/1/2018。必需： Office Online。ExpressRoute: 是。51.18.16.0/23]。说明： 添加 Office Online 的新前缀。  <br/> |
|3/15/2018  <br/> |添加 1 IP_Set;1 / [有效 4/15/2018。必需： Office 365 ProPlus。ExpressRoute: 否。 51.18.0.0/21]。说明： 添加 Office 365 ProPlus 的终结点。  <br/> |
|7/2/2018  <br/> |删除 1 FQDN;1 / [有效 8/1/2018。必需： OneDrive for Business。ExpressRoute: 否。login.microsoftonline.de]。 说明： 删除 OneDrive for Business 终结点。删除 11 Fqdn;1 / [有效 8/1/2018。必需： Office Mobile。ExpressRoute: 否。 https://excelps.osi.office.de/exlps/excelprint.svc/exlPrint]，2 / [有效 8/1/2018。必需： Office Mobile。ExpressRoute: 否。 https://wordps.osi.office.de/wrdps/wordprint.svc/wrdprint]、 3 / [有效 8/1/2018。必需： Office Mobile。ExpressRoute: 否。 https://wordcs.osi.office.de/wordauto/wordautomation.svc/wordautomation]、 4 / [有效 8/1/2018。必需： Office Mobile。ExpressRoute: 否。 https://wordcs.osi.office.de/wordauto/wordautomation.svc/rest]，5 / [有效 8/1/2018。必需： Office Mobile。ExpressRoute: 否。 https://pptps.osi.office.de/pptps/powerpointprint.svc/PptPrint]、 6 / [有效 8/1/2018。必需： Office Mobile。ExpressRoute: 否。 https://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/PptAutomation]，7 / [有效 8/1/2018。必需： Office Mobile。ExpressRoute: 否。 https://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/rest]、 8 / [有效 8/1/2018。必需： Office Mobile。ExpressRoute: 否。 https://ols.osi.office.de/]、 9 / [有效 8/1/2018。必需： Office Mobile。ExpressRoute: 否。 https://ols.osi.office.de/olsc/OlsClient.svc/OlsClient]，10 / [有效 8/1/2018。必需： Office Mobile。ExpressRoute: 否。 https://excelcs.osi.office.de/xlauto/excelautomation.svc/XlAutomation]、 11 / [有效 8/1/2018。必需： Office Mobile。ExpressRoute: 否。 https://excelcs.osi.office.de/xlauto/excelautomation.svc/rest]。说明： 删除 Office Mobile 终结点。  <br/> |
   

