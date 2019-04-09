---
title: Office 365 客户端应用支持-条件访问
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
description: 了解 Office 365 客户端应用程序支持条件访问
ms.openlocfilehash: 3212d15f2df68256fc80e4544fc7e61cdccc82c2
ms.sourcegitcommit: 80bc767a9c88a259facb3894b9a168c85d35eb70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "31517556"
---
# <a name="office-365-client-app-support---conditional-access"></a>Office 365 客户端应用支持-条件访问

在新式工作区中, 用户可以使用几乎任何位置的各种设备和应用来访问你的组织的资源。 因此, 仅侧重于可以访问资源的人士再也无法满足的要求。 您的组织还必须支持在访问控制基础结构中访问资源的方式和位置。 使用 Azure AD 设备、位置和基于多因素身份验证的条件访问, 可以满足此新要求。 条件访问是 Azure Active Directory 的一项功能, 使您能够在对环境中的应用程序的访问上强制实施控制, 所有这些都基于特定条件并从一个中心位置进行管理。

了解有关[条件访问](https://docs.microsoft.com/azure/active-directory/conditional-access/)的详细信息。

## <a name="supported-platforms"></a>支持的平台

 - Windows 10 桌面版
 - Windows 10 新式应用
 - Web 浏览器
 - Android<sup>1</sup>
 - iOS
 - macOS<sup>2</sup>

有关 office 365 中平台支持的详细信息, 请参阅[office 365 的系统要求](https://products.office.com/office-system-requirements)。

## <a name="supported-clients"></a>支持的客户端

以下客户端的最新版本支持条件访问:

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![Azure 图标](media/o365-azure-64x64.png) <br> [Azure AD <br>门户 ](https://azure.microsoft.com/features/azure-portal/) | ![访问图标](media/o365-access-64x64.png) <br> [Access](https://products.office.com/access) | ![Delve 图标](media/o365-delve-64x64.png) <br> [Delve<sup>1</sup>](https://products.office.com/business/intelligent-search) | ![Dynamics 365 图标](media/o365-dynamics365-64x64.png) <br> [Dynamics 365](https://dynamics.microsoft.com) | ![边缘图标](media/o365-edge-64x64.png) <br> [边线](https://www.microsoft.com/windows/microsoft-edge) 
| ![Exchange 图标](media/o365-exchange-64x64.png) <br> [Exchange](https://products.office.com/exchange/exchange-online) | ![Excel 图标](media/o365-excel-64x64.png) <br> [Excel](https://products.office.com/excel) | ![流图标](media/o365-flow-64x64.png) <br> [流程](https://flow.microsoft.com) | ![表单图标](media/o365-forms-64x64.png) <br> [表单](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | ![Kaizala 图标](media/o365-kaizala-64x64.png) <br> [Kaizala](https://products.office.com/en/business/microsoft-kaizala) 
| ![镜头图标](media/o365-lens-64x64.png) <br> [Office Lens](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | ![Office 365 管理员图标](media/o365-o365admin-64x64.png) <br> [Office 365 <br>管理员](https://products.office.com/business/manage-office-365-admin-app) | ![OneDrive for business 图标](media/o365-OneDrive-64x64.png) <br> [OneDrive<sup>2</sup>](https://products.office.com/onedrive-for-business/online-cloud-storage) | ![OneNote 图标](media/o365-OneNote-64x64.png) <br> [OneNote](https://products.office.com/onenote) | ![Outlook 图标](media/o365-outlook-64x64.png) <br> [Outlook](https://products.office.com/outlook) |
| ![Planner 图标](media/o365-planner-64x64.png) <br> [规划器](https://products.office.com/business/task-management-software) | ![PowerBI 图标](media/o365-powerbi-64x64.png) <br> [Power BI](https://powerbi.microsoft.com) | ![PowerPoint 图标](media/o365-powerpoint-64x64.png) <br> [PowerPoint](https://products.office.com/powerpoint) | ![项目图标](media/o365-project-64x64.png) <br> [项目](https://products.office.com/project) | ![Publisher 图标](media/o365-publisher-64x64.png) <br> [发行商](https://products.office.com/publisher)
| ![SharePoint 图标](media/o365-sharepoint-64x64.png) <br> [Sharepoint](https://products.office.com/sharepoint) | ![Skype for business 图标](media/o365-skypeforbusiness-64x64.png) <br> [Skype for <br> business](https://www.skype.com/business/) | ![粘滞便笺图标](media/o365-stickynotes-64x64.png) <br> [粘滞便笺](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) | ![流图标](media/o365-stream-64x64.png) <br> [流](https://stream.microsoft.com) | ![Sway 图标](media/o365-sway-64x64.png) <br> [Sway](https://sway.com) 
| ![团队图标](media/o365-teams-64x64.png) <br> [Teams](https://products.office.com/microsoft-teams/group-chat-software) | ![待办情况图标](media/o365-todo-64x64.png) <br> [微软待办](https://todo.microsoft.com) | ![Visio 图标](media/o365-visio-64x64.png) <br> [Visio](https://products.office.com/visio/flowchart-software) | ![Word 图标](media/o365-word-64x64.png) <br> [Word](https://products.office.com/word) | ![Yammer 图标](media/o365-yammer-64x64.png) <br> [Yammer](https://products.office.com/yammer/yammer-overview)

> [!NOTE]
> <sup>1</sup>即将在 Android 上对 Delve 提供支持。 <br>
> <sup>2</sup>即将在 macOS 上支持 OneDrive。