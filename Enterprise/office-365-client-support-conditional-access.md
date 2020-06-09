---
title: Office 365 客户端应用支持—条件访问
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
f1.keywords:
- NOCSH
description: 了解 Office 365 客户端应用程序支持条件访问
ms.openlocfilehash: 8911f6a0fcadcd261113c8b89f2154b59dda5a0f
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "44619338"
---
# <a name="office-365-client-app-support--conditional-access"></a>Office 365 客户端应用支持—条件访问

在新式工作区中，用户可以使用各种设备和应用从任意位置访问你的组织的资源。 因此，仅侧重于可以访问资源的人士再也无法满足的要求。 您的组织还必须支持在访问控制基础结构中访问资源的方式和位置。

使用 Azure Active Directory （Azure AD）设备、位置和基于多因素身份验证的条件访问，可以满足此新要求。 条件访问是 Azure AD 的一项功能，可用于强制执行对环境中的应用程序的访问控制，所有这些都基于特定条件并在中心位置进行管理。

了解有关 [Azure AD 条件访问](https://docs.microsoft.com/azure/active-directory/conditional-access/)的详细信息。

## <a name="supported-platforms"></a>支持的平台

 - Windows 10 桌面版
 - Windows 10 新式应用
 - Web 浏览器
 - Android
 - iOS
 - macOS<sup>1</sup>

有关 Office 365 中平台支持的详细信息，请参阅[office 365 的系统要求](https://products.office.com/office-system-requirements)。

## <a name="supported-clients"></a>支持的客户端

以下客户端的最新版本支持条件访问：

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 图标](media/o365-azure-64x64.png) <br> [Azure AD <br> 门户](https://azure.microsoft.com/features/azure-portal/) | ![Access 图标](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![公司门户图标](media/o365-microsoft-64x64.png) <br> [公司 <br> 门户](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)  | ![Cortana 图标](media/o365-cortana-64x64.png) <br> [Cortana](https://www.microsoft.com/cortana) | ![Delve 图标](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) 
| ![Dynamics 365 图标](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![边缘图标](media/o365-edge-64x64.png) <br> [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge) | ![Exchange 图标](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![Excel 图标](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![Forms 图标](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) 
| ![Kaizala 图标](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) | ![Office.com 图标](media/o365-office-64x64.png) <br> [Office.com](https://www.office.com/) | ![镜头图标](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Office 365 管理员图标](media/o365-o365admin-64x64.png) <br> [Office 365 <br> 管理员](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive for Business 图标](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>1</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) 
| ![OneNote 图标](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 图标](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![Planner 图标](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) | ![PowerApps 图标](media/o365-powerapps-64x64.png) <br> [PowerApps](https://powerapps.microsoft.com) | ![电源自动图标](media/o365-flow-64x64.png) <br> [电源 <br> 自动化](https://flow.microsoft.com)
| ![PowerBI 图标](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint 图标](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![Project 图标](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![Publisher 图标](media/o365-publisher-64x64.png) <br> [Publisher](https://products.office.com/publisher) | ![SharePoint 图标](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) 
| ![Skype for Business 图标](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> business](https://www.skype.com/business/) | ![粘滞便笺图标](media/o365-stickynotes-64x64.png) <br> [粘滞便笺](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![Stream 图标](media/o365-stream-64x64.png) <br> [Stream](https://stream.microsoft.com) | ![Sway 图标](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![Teams 图标](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) 
| ![To Do 图标](media/o365-todo-64x64.png) <br> [待办事项](https://todo.microsoft.com) | ![Visio 图标](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 图标](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 图标](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

## <a name="supported-powershell-modules"></a>支持的 PowerShell 模块

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 图标](media/o365-azure-64x64.png) <br> [Azure AD <br> PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | ![Exchange 图标](media/o365-exchange-64x64.png) <br> [Exchange Online <br> PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | ![SharePoint 图标](media/o365-sharepoint-64x64.png) <br> [SharePoint Online <br> PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <sup>1</sup>即将在 macOS 上提供对 OneDrive 的支持。

## <a name="see-also"></a>另请参阅

[Microsoft 365 企业版概述](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
