---
title: Microsoft 365 客户端应用支持—单一登录
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: 适用于单一登录的 Microsoft 365 客户端应用程序支持。
ms.openlocfilehash: beb0ae405b9c365da0faa64e31a36f7b571ce1aa
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998510"
---
# <a name="microsoft-365-client-app-support--single-sign-on"></a>Microsoft 365 客户端应用支持—单一登录

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

当用户登录到 Azure Active Directory （Azure AD）中的应用程序时，单一登录（SSO）将增加安全性和方便性。 通过单一登录，用户可使用一个帐户登录一次，以访问加入域的设备、公司资源、软件即服务（SaaS）应用程序和 web 应用程序。

了解有关[单一登录](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)的详细信息。

## <a name="supported-platforms"></a>支持的平台

 - Windows 10 桌面版<sup>2</sup>
 - Windows 10 新式应用
 - Web 浏览器
 - Android<sup>3</sup>
 - iOS<sup>1</sup>
 - macOS<sup>4</sup>

有关 Microsoft 365 中平台支持的详细信息，请参阅[microsoft 365 的系统要求](https://products.office.com/office-system-requirements)。

## <a name="supported-clients"></a>支持的客户端

以下客户端的最新版本支持单一登录：

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Access 图标](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![公司门户图标](media/o365-microsoft-64x64.png) <br> [公司 <br> 门户<sup>3、4</sup>](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Delve 图标](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![边缘图标](media/o365-edge-64x64.png) <br> [Edge<sup>1</sup>](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 图标](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) 
| ![Kaizala 图标](media/o365-kaizala-64x64.png) <br> [Kaizala<sup>1</sup>](https://products.office.com/en/business/microsoft-kaizala) | ![Office.com 图标](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![镜头图标](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![OneDrive for Business 图标](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 图标](media/o365-OneNote-64x64.png) <br> [OneNote<sup>2</sup>](https://products.office.com/onenote) 
| ![Outlook 图标](media/o365-outlook-64x64.png) <br> [Outlook<sup>4</sup>](https://products.office.com/outlook) | ![Planner 图标](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![电源自动图标](media/o365-flow-64x64.png) <br> [电源 <br> 自动化](https://flow.microsoft.com) | ![PowerBI 图标](media/o365-powerbi-64x64.png) <br> [Power BI<sup>2</sup>](https://powerbi.microsoft.com)| ![PowerPoint 图标](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![Project 图标](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Publisher 图标](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint 图标](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![粘滞便笺图标](media/o365-stickynotes-64x64.png) <br> [粘滞便笺](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw)  | ![Sway 图标](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![Teams 图标](media/o365-teams-64x64.png) <br> [团队<sup>2、4</sup>](https://products.office.com/microsoft-teams/group-chat-software) | ![To Do 图标](media/o365-todo-64x64.png) <br> [待办事项](https://todo.microsoft.com) | ![Visio 图标](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Whiteboard 图标](media/o365-whiteboard-64x64.png) <br> [白板<sup>3</sup>](https://whiteboard.microsoft.com/) | ![Word 图标](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) 
| ![Yammer 图标](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>支持的 PowerShell 模块

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 图标](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange 图标](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint 图标](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup>对 iOS 上的边缘和 Kaizala 的支持即将推出。 <br>
> <sup>2</sup>对 Windows 10 桌面版上的 OneNote、PowerBI、团队和 Yammer 的支持即将推出。 <br>
> <sup>3</sup>对 Android 上的白板功能的支持即将推出。 <br>
> <sup>4</sup>在 macOS 上提供对 Outlook、团队和公司门户的支持。 <br>

## <a name="see-also"></a>另请参阅

[Microsoft 365 企业版概述](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
