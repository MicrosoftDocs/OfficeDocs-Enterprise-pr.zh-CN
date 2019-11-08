---
title: 在团队中与来宾协作
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 了解如何与团队中的来宾进行协作。
ms.openlocfilehash: a3e34431b97e8f565d61470ddd55797981b837c8
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38029166"
---
# <a name="collaborate-with-guests-in-a-team"></a>在团队中与来宾协作

如果需要在文档、任务和对话中与来宾进行协作，我们建议使用 Microsoft 团队。 团队提供了 Office 和 SharePoint 中提供的所有协作功能，并在统一的用户体验中提供了持续聊天和可自定义且可扩展的协作工具集。

在本文中，我们将完成必要的 Microsoft 365 配置步骤，以设置一个团队以与来宾协作。

## <a name="video-demonstration"></a>视频演示

该视频显示了本文档中描述的配置步骤。</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

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
6. 如果进行了更改，请单击 "**保存**"。

请注意 "**协作限制**" 部分中的设置。 确保不会阻止您要与之进行协作的来宾域。

## <a name="teams-guest-access-settings"></a>团队来宾访问设置

团队具有用于来宾访问的主开/关开关，以及可用于控制来宾在团队中可执行的操作的各种设置。 主开关，**允许在团队中****进行来宾**访问，以便来宾访问能够在团队中工作。

检查以确保在团队中启用了来宾访问，并根据你的业务需求对来宾设置进行任何调整。 请记住，这些设置会影响所有团队。

![Teams 来宾访问切换的屏幕截图](media/teams-guest-access-toggle-on.png)

设置团队来宾访问设置

1. 登录到 Microsoft 365 管理中心[https://admin.microsoft.com](https://admin.microsoft.com)。
2. 在左侧导航中，单击 "**全部显示**"。
3. 在 "**管理中心**" 下，单击 "**团队**"。
4. 在团队管理中心的左侧导航栏中，展开 "**组织范围的设置**"，然后单击 "**来宾访问**"。
5. 确保将 "**允许在团队中进行来宾访问**" 设置为 **"开"**。
6. 对其他来宾设置进行所需的更改，然后单击 "**保存**"。

> [!NOTE]
> "团队来宾" 设置可能需要24小时才能在打开后变为活动状态。

## <a name="office-365-groups-guest-settings"></a>Office 365 组来宾设置

团队使用适用于团队成员资格的 Office 365 组。 必须打开 Office 365 组来宾设置，才能使团队中的来宾访问能够正常工作。

![Microsoft 365 管理中心中的 Office 365 组来宾设置的屏幕截图](media/office-365-groups-guest-settings.png)

设置 Office 365 组来宾设置

1. 在 Microsoft 365 管理中心的左侧导航栏中，展开 "**设置**"。
2. 单击 "**服务" & 外接程序**。
3. 在列表中，单击 " **Office 365 组**"。
4. 确保将**组织外部的成员访问组内容**和**允许组所有者将组织外部的人员添加到组**复选框均选中。
5. 如果进行了更改，请单击 "**保存更改**"。


## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint 组织级别的共享设置

工作组内容（如文件、文件夹和列表）都存储在 SharePoint 中。 为使来宾能够访问团队中的这些项目，SharePoint 组织级别的共享设置必须允许与来宾共享。

组织级别设置决定了可用于单个网站的设置，包括与团队相关的网站。 网站设置不能比组织级别设置更具有更好的许可。

如果要允许与匿名用户共享文件和文件夹，请选择 "**任何人**"。 如果要确保所有来宾都必须进行身份验证，请选择 "**新建" 和 "现有来宾**"。 选择组织中的任何网站将需要的 "最高" 设置。

![SharePoint 组织级别共享设置的屏幕截图](media/sharepoint-organization-external-sharing-controls.png)


设置 SharePoint 组织级别的共享设置

1. 在 Microsoft 365 管理中心的左侧导航栏中，在 "**管理中心**" 下，单击 " **SharePoint**"。
2. 在 SharePoint 管理中心的左侧导航栏中，单击“**共享**”。
3. 确保将 SharePoint 的 "外部共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。
4. 如果进行了更改，请单击 "**保存**"。


## <a name="sharepoint-organization-level-default-link-settings"></a>SharePoint 组织级别的默认链接设置

默认的文件和文件夹链接设置确定在用户共享文件或文件夹时，默认情况下向用户显示的链接选项。 如果需要，用户可以在共享之前将链接类型更改为其他选项之一。

请注意，此设置会影响组织中的所有团队和 SharePoint 网站。

选择当用户共享文件和文件夹时默认选择的链接类型：

- **任何具有链接的人**-如果您希望与匿名用户共享大量文件和文件夹，请选择此选项。 如果您希望允许*任何人*链接，但担心意外匿名共享，请将其他选项之一作为默认值。 仅当您已启用**任何**共享时，此链接类型才可用。
- **仅限组织中的人员**-如果您希望大多数文件和文件夹共享与组织内部的人员共享，请选择此选项。
- **特定人员**-如果您希望对来宾执行大量文件和文件夹共享，请考虑此选项。 此类型的链接可与来宾配合使用，并要求用户进行身份验证。
 
![SharePoint 组织级别文件和文件夹共享设置的屏幕截图](media/sharepoint-organization-files-folders-sharing-settings.png)


设置 SharePoint 组织级别的默认链接设置

1. 导航到 SharePoint 管理中心中的 "共享" 页面。
2. 在 "**文件和文件夹链接**" 下，选择要使用的默认共享链接。
3. 如果进行了更改，请单击 "**保存**"。

## <a name="create-a-team"></a>创建团队

下一步是创建计划用于与来宾协作的团队。

创建团队
1. 在团队中的 "**团队**" 选项卡上，单击 "加入" 或 "在左窗格底部**创建团队**"。
2. 单击 "**创建团队**"。
3. 单击 "**从头开始构建团队**"。
4. 选择 "**专用**" 或 "**公共**"。
5. 键入团队的名称和说明，然后单击 "**创建**"。
6. 单击 "**跳过**"。

我们将稍后邀请用户。 接下来，请务必检查与团队关联的 SharePoint 网站的网站级别共享设置。

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint 网站级别共享设置

检查网站级别的共享设置以确保它们允许此团队的访问类型。 例如，如果将组织级别设置设置为 "**任何人**"，但希望所有来宾都对此团队进行身份验证，请确保将网站级别的共享设置设置为 "**新建" 和 "现有来宾**"。

![SharePoint 网站外部共享设置的屏幕截图](media/sharepoint-site-external-sharing-settings.png)


设置网站级共享设置
1. 在 SharePoint 管理中心中，在左侧导航栏中，展开 "**网站**"，然后单击 "**活动网站**"。
2. 为您刚创建的团队选择网站。
3. 在功能区中，单击 "**共享**"。
4. 确保将 "共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。
5. 如果进行了更改，请单击 "**保存**"。

## <a name="invite-users"></a>邀请用户

现在已配置来宾共享设置，因此您可以开始向团队添加内部用户和来宾。 

向团队邀请内部用户
1. 在团队中，单击 "**更多选项**" （**\*\***），然后单击 "**添加成员**"。
2. 键入要邀请的人员的姓名。
3. 单击“**添加**”，然后单击“**关闭**”。

向团队邀请来宾
1. 在团队中，单击 "**更多选项**" （**\*\***），然后单击 "**添加成员**"。
2. 键入要邀请的来宾的电子邮件地址。
3. 单击 "**编辑来宾信息**"。
4. 键入来宾的全名并单击复选标记。
5. 单击“**添加**”，然后单击“**关闭**”。

## <a name="see-also"></a>另请参阅

[有关与匿名用户共享文件和文件夹的最佳做法](best-practices-anonymous-sharing.md)

[与来宾共享时限制文件意外曝光](sharing-limit-accidental-exposure.md)

[创建安全来宾共享环境](create-a-secure-guest-sharing-environment.md)）


