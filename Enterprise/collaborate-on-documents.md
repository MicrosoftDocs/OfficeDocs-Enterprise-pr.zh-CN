---
title: 在文档中与来宾协作
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
ms.collection: SPO_Content
localization_priority: Normal
f1.keywords: NOCSH
description: 了解如何通过 SharePoint 和 OneDrive 中的文档与来宾进行协作。
ms.openlocfilehash: 6646a3b11d9acbc01b998d90e6ff836533e4545c
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549041"
---
# <a name="collaborate-with-guests-on-a-document"></a>在文档中与来宾协作

如果需要与组织外部的人员协作处理 SharePoint 或 OneDrive 中的文档，则可以向其发送指向文档的共享链接。 在本文中，我们将完成必要的 Microsoft 365 配置步骤，以设置 SharePoint 和 OneDrive 的共享链接，以满足组织的需求。

## <a name="video-demonstration"></a>视频演示

该视频显示了本文档中描述的配置步骤。</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE450Vt?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a>Azure 组织关系设置

Microsoft 365 中的共享受 Azure Active Directory 中的组织关系设置的最高级别的管辖。 如果在 Azure AD 中禁用或限制来宾共享，这将替代您在 Microsoft 365 中配置的任何共享设置。

检查组织关系设置以确保不会阻止与来宾共享。

![Azure Active Directory 组织关系设置页面的屏幕截图](media/azure-ad-organizational-relationships-settings.png)

设置组织关系设置

1. 登录到 Microsoft Azure [https://portal.azure.com](https://portal.azure.com)。
2. 在左侧导航中，单击 " **Azure Active Directory**"。
3. 在 "**概述**" 窗格中，单击 "**组织关系**"。
4. 在 "**组织关系**" 窗格中，单击 "**设置**"。
5. 确保**来宾邀请者角色中的管理员和用户可以邀请**和**成员**都可以邀请都设置为 **"是"**。
6. 如果进行了任何更改，请单击 **“保存”**。

请注意 "**协作限制**" 部分中的设置。 确保不会阻止您要与之进行协作的来宾域。

## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint 组织级别的共享设置

为使组织外部的人员能够访问 SharePoint 或 OneDrive 中的文档，SharePoint 和 OneDrive 组织级共享设置必须允许与组织外部的人员共享。

SharePoint 的组织级设置决定了各个 SharePoint 网站可用的设置。 网站设置不能比组织级别设置更具有更好的许可。 OneDrive 的组织级别设置决定了用户的 OneDrive 库中可用的共享级别。

对于 SharePoint 和 OneDrive，如果要允许未经身份验证的文件和文件夹共享，请选择 "**任何人**"。 如果您想要确保组织外部的人员必须进行身份验证，请选择 "**新建" 和 "现有来宾**"。 *任何*链接都是最简单的共享方式：组织外部的人员可以在不进行身份验证的情况下打开链接，并且可以自由地将其传递给其他人。

对于 SharePoint，选择组织中的任何网站将需要的 "最高" 设置。

![SharePoint 组织级别共享设置的屏幕截图](media/sharepoint-organization-external-sharing-controls.png)


设置 SharePoint 组织级别的共享设置

1. 在 Microsoft 365 管理中心的左侧导航栏中，在 "**管理中心**" 下，单击 " **SharePoint**"。
2. 在 SharePoint 管理中心的左侧导航栏中，单击“**共享**”。
3. 确保将 SharePoint 或 OneDrive 的外部共享设置为 "**任何人**" 或**新的和现有的来宾**。 （请注意，OneDrive 设置不能比 SharePoint 设置更具许可。）
4. 如果进行了任何更改，请单击 **“保存”**。

## <a name="sharepoint-organization-level-default-link-settings"></a>SharePoint 组织级别的默认链接设置

默认的文件和文件夹链接设置确定在用户共享文件或文件夹时，默认情况下向用户显示的链接选项。 如果需要，用户可以在共享之前将链接类型更改为其他选项之一。

请注意，此设置会影响组织中的 SharePoint 网站以及 OneDrive。

选择当用户共享文件和文件夹时默认选择的链接类型：

- **任何具有链接的人**-如果您想要执行大量未经身份验证的文件和文件夹共享，请选择此选项。 如果要允许*任何人*链接，但担心意外的共享，请考虑其他选项之一作为默认选项。 仅当您已启用**任何**共享时，此链接类型才可用。
- **仅限组织中的人员**-如果您希望大多数文件和文件夹共享与组织内部的人员共享，请选择此选项。
- **特定人员**-如果您希望对来宾执行大量文件和文件夹共享，请考虑此选项。 此类型的链接可与来宾配合使用，并要求用户进行身份验证。
 
![SharePoint 组织级别文件和文件夹共享设置的屏幕截图](media/sharepoint-organization-files-folders-sharing-settings.png)


设置 SharePoint 和 OneDrive 组织级别默认链接设置

1. 导航到 SharePoint 管理中心中的 "共享" 页面。
2. 在 "**文件和文件夹链接**" 下，选择要使用的默认共享链接。
3. 如果进行了任何更改，请单击 **“保存”**。

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint 网站级别共享设置

如果要共享 SharePoint 网站中的文件和 fodlers，则还需要检查该网站的网站级共享设置。

![SharePoint 网站外部共享设置的屏幕截图](media/sharepoint-site-external-sharing-settings.png)

设置网站级共享设置
1. 在 SharePoint 管理中心的左侧导航栏中，展开 **“站点”**，然后单击 **“活动站点”**。
2. 选择您刚刚创建的网站。
3. 在功能区中，单击 **“共享”**。
4. 确保将 "共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。
5. 如果进行了任何更改，请单击 **“保存”**。

## <a name="invite-users"></a>邀请用户

现在已配置来宾共享设置，因此用户现在可以与组织外部的人员共享文件和文件夹。 有关详细信息，请参阅[共享 OneDrive 文件和文件夹](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07)以及[共享 SharePoint 文件或文件夹](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c)。

## <a name="see-also"></a>另请参阅

[有关与未经认证用户共享文件和文件夹的最佳做法](best-practices-anonymous-sharing.md)

[与来宾共享时限制文件意外曝光](sharing-limit-accidental-exposure.md)