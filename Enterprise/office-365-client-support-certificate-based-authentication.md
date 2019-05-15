---
title: Office 365 客户端应用程序支持—基于证书的身份验证
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
description: Office 365 客户端应用程序支持基于证书的身份验证。
ms.openlocfilehash: 88bc59934399588f0a5c682c6b136ad0948ecd52
ms.sourcegitcommit: 9c6e31204aa326c31d60befe80e610f702e65800
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2019
ms.locfileid: "33990905"
---
# <a name="office-365-client-app-support--certificate-based-authentication"></a>Office 365 客户端应用程序支持—基于证书的身份验证

通过基于证书的身份验证, 您可以使用 Windows、Android 或 iOS 设备上的客户端证书对 Azure Active Directory 进行身份验证。 配置此功能后, 无需在移动设备上将用户名和密码组合输入到某些邮件和 Microsoft Office 应用程序中。

了解有关[基于证书的身份验证](https://docs.microsoft.com/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started)的详细信息。

## <a name="supported-platforms"></a>支持的平台

 - Windows 10 桌面版<sup>2</sup>
 - Windows 10 新式应用
 - Web 浏览器
 - Android
 - iOS
 - macOS<sup>1</sup> <sup>2</sup>

有关 Office 365 中平台支持的详细信息, 请参阅[office 365 的系统要求](https://products.office.com/office-system-requirements)。

## <a name="supported-clients"></a>支持的客户端

以下客户端的最新版本支持基于证书的身份验证:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![访问图标](media/o365-access-64x64.png) <br> [访问](https://products.office.com/access) | ![Azure 图标](media/o365-azure-64x64.png) <br> [Azure AD <br>门户](https://azure.microsoft.com/features/azure-portal/) | ![公司门户图标](media/o365-microsoft-64x64.png) <br> [公司<br>门户](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | ![Delve 图标](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Dynamics 365 图标](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) 
| ![边缘图标](media/o365-edge-64x64.png) <br> [距](https://www.microsoft.com/windows/microsoft-edge) | ![Excel 图标](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![流图标](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![表单图标](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala 图标](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Office 365 管理员图标](media/o365-o365admin-64x64.png) <br> [Office 365 <br>管理员](https://products.office.com/business/manage-office-365-admin-app) | ![镜头图标](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![OneDrive for Business 图标](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) |  ![OneNote 图标](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 图标](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) 
| ![Planner 图标](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerApps 图标](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![PowerBI 图标](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com)| ![PowerPoint 图标](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![项目图标](media/o365-project-64x64.png) <br> [项目](https://products.office.com/project) 
| ![Publisher 图标](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint 图标](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![Skype for Business 图标](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> business](https://www.skype.com/business/) | ![粘滞便笺图标](media/o365-stickynotes-64x64.png) <br> [粘滞便笺](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![流图标](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) 
| ![Sway 图标](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![团队图标](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![待办情况图标](media/o365-todo-64x64.png) <br> [微软待办](https://todo.microsoft.com) | ![Visio 图标](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 图标](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) 
| ![Yammer 图标](media/o365-yammer-64x64.png) <br> [Yammer<sup>2</sup>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a>支持的 PowerShell 模块

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 图标](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange 图标](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint 图标](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

> [!NOTE]
> <sup>1</sup>即将在 macOS 上提供对 OneDrive 的支持。 <br>
> <sup>2</sup>对 Windows Desktop 和 macOS 上的 Yammer 提供了更快的支持。