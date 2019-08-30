---
title: Office 365 客户端应用程序支持—新式验证
ms.author: robmazz
author: robmazz
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
description: 适用于新式验证的 Office 365 客户端应用程序支持。
ms.openlocfilehash: d5d17f3395b7eec736403c75b4e2b571c1123fe7
ms.sourcegitcommit: 27614632a0ceccbd5a4083cefa822187417f02a6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2019
ms.locfileid: "36672932"
---
# <a name="office-365-client-app-support---modern-authentication"></a>Office 365 客户端应用程序支持-新式验证

新式验证为跨不同平台的 Office 客户端应用启用基于 Active Directory 身份验证库 (ADAL) 的登录。 这将启用多因素身份验证 (MFA)、智能卡和基于证书的身份验证等登录功能。

了解有关[多因素身份验证](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)和[基于证书的身份验证](https://docs.microsoft.com/azure/active-directory/active-directory-certificate-based-authentication-get-started)的详细信息。

## <a name="supported-platforms"></a>支持的平台

 - Windows 10 桌面版
 - Windows 10 新式应用
 - Web 浏览器<sup>1</sup>
 - Android<sup>2</sup>
 - iOS
 - macOS

有关 Office 365 中平台支持的详细信息, 请参阅[office 365 的系统要求](https://products.office.com/office-system-requirements)。

## <a name="supported-clients"></a>支持的客户端

以下客户端的最新版本支持新式验证:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![访问图标](media/o365-access-64x64.png) <br> [访问](https://products.office.com/access) | ![Azure 图标](media/o365-azure-64x64.png) <br> [Azure <br>门户](https://azure.microsoft.com/features/azure-portal/) | ![公司门户图标](media/o365-microsoft-64x64.png) <br> [公司<br>门户](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Delve 图标](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365 图标](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![边缘图标](media/o365-edge-64x64.png) <br> [距](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 图标](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![流图标](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![表单图标](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala 图标](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Office.com 图标](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![Office 365 管理员图标](media/o365-o365admin-64x64.png) <br> [Office 365 <br>管理员](https://products.office.com/business/manage-office-365-admin-app) | ![镜头图标](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![OneDrive for Business 图标](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote 图标](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) 
| ![Outlook 图标](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Planner 图标](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerApps 图标](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![PowerBI 图标](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![PowerPoint 图标](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) 
| ![项目图标](media/o365-project-64x64.png) <br> [项目](https://products.office.com/project) | ![Publisher 图标](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint 图标](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![Skype for Business 图标](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> business<sup>1</sup>](https://www.skype.com/business/) | ![StaffHub 图标](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software)
| ![粘滞便笺图标](media/o365-stickynotes-64x64.png) <br> [粘滞便笺](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![流图标](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway 图标](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![团队图标](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![待办情况图标](media/o365-todo-64x64.png) <br> [微软待办](https://todo.microsoft.com) 
| ![Visio 图标](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![白板图标](media/o365-whiteboard-64x64.png) <br> [白板<sup>1</sup>、<sup>2</sup>](https://whiteboard.microsoft.com/) | ![Word 图标](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 图标](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview) | ![Yammer 图标](media/o365-yammer-64x64.png) <br> [Yammer <br>通知程序](https://products.office.com/yammer/yammer-overview) |  |

## <a name="supported-powershell-modules"></a>支持的 PowerShell 模块

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 图标](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange 图标](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint 图标](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup>对白板和 Skype for business 的 web 应用程序的支持即将推出。 <br>
> <sup>2</sup>对 Android 上的白板支持很快可用。