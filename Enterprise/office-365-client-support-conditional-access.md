---
title: Office 365 客户端应用程序支持的条件的访问
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/17/2018
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: 了解 Office 365 客户端应用程序支持的条件的访问
ms.openlocfilehash: 215b97daf532e22eb37618d66779378e37accb31
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915297"
---
# <a name="office-365-client-app-support---conditional-access"></a>Office 365 客户端应用程序支持的条件的访问

在现代工作区中，用户可以访问您组织的资源从任意虚拟地点使用各种设备和应用程序。因此，只需将重点放在谁可以访问的资源不足不再。如何和资源到您的访问控制基础结构访问的位置，还必须支持您的组织。使用 Azure AD 设备、 位置和多因素身份验证基于条件的访问，您可以满足此新的要求。条件访问是的使您能够强制在环境中，都是基于特定条件的应用程序的访问上的控件，并从一个中心位置管理 Azure Active Directory 的功能。 

了解有关[基于设备的](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-policy-connected-applications)、[基于位置的](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-locations)和[MFA 基于](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-conditions#users-and-groups)条件访问的详细信息。

## <a name="supported-platforms"></a>支持的平台

 - Windows 10 桌面
 - Windows 10 现代应用程序
 - Web 浏览器
 - Android
 - iOS
 - macOS<sup>1</sup>

## <a name="supported-clients"></a>支持的客户端

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![深入图标](media/o365-delve-64x64.png) <br> [Delve](https://products.office.com/business/intelligent-search) | ![Excel 图标](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![流图标](media/o365-flow-64x64.png) <br> [Flow](https://flow.microsoft.com) | ![表单图标](media/o365-forms-64x64.png) <br> [Forms](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala 图标](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![Office 365 管理图标](media/o365-o365admin-64x64.png) <br> [Office 365<br>管理](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive for Business 图标](media/o365-OneDrive-64x64.png) <br> [OneDrive](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 图标](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 图标](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) | ![计划工具图标](media/o365-planner-64x64.png) <br> [Planner](https://products.office.com/business/task-management-software) 
| ![PowerBI 图标](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint 图标](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![项目图标](media/o365-project-64x64.png) <br> [Project](https://products.office.com/project) | ![SharePoint 图标](media/o365-sharepoint-64x64.png) <br> [Sharepoint<sup>1</sup>](https://products.office.com/sharepoint) | ![Skype 业务图标](media/o365-skypeforbusiness-64x64.png) <br> [Skype 的<br>业务](https://www.skype.com/business/) 
| ![StaffHub 图标](media/o365-staffhub-64x64.png) <br> [StaffHub](https://products.office.com/microsoft-staffhub/staff-scheduling-software) | ![流图标](media/o365-stream-64x64.png) <br> [流](https://stream.microsoft.com) | ![Sway 图标](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) | ![团队图标](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![待办事项图标](media/o365-todo-64x64.png) <br> [微软待办](https://todo.microsoft.com) 
| ![Visio 图标](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 图标](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 图标](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup>上 macOS 即将发布的 SharePoint 应用程序支持。