---
title: 在网站中与来宾协作
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: 了解如何在 SharePoint 网站中与来宾进行协作。
ms.openlocfilehash: 746e592a027c05f489e9f5dfe819cfb107c6b1f5
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886481"
---
# <a name="collaborate-with-guests-in-a-site"></a>在网站中与来宾协作

如果需要在文档、数据和列表之间与来宾进行协作，则可以使用 SharePoint 网站。 新式 SharePoint 网站连接到可管理网站成员身份的 Office 365 组，并提供其他协作工具（如共享邮箱和日历）。

在本文中，我们将逐步完成为与来宾协作设置 SharePoint 网站所必需的 Microsoft 365 配置步骤。

## <a name="video-demonstration"></a>视频演示

该视频显示了本文档中描述的配置步骤。</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

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

## <a name="office-365-groups-guest-settings"></a>Office 365 组来宾设置

新式 SharePoint 网站使用 Office 365 组来控制网站访问。 必须打开 Office 365 组来宾设置，才能使 SharePoint 网站中的来宾访问能够正常工作。

![Microsoft 365 管理中心中的 Office 365 组来宾设置的屏幕截图](media/office-365-groups-guest-settings.png)

设置 Office 365 组来宾设置

1. 在 Microsoft 365 管理中心的左侧导航栏中，展开 "**设置**"。
2. 单击 "**服务" & 外接程序**。
3. 在列表中，单击 " **Office 365 组**"。
4. 确保将**组织外部的成员访问组内容**和**允许组所有者将组织外部的人员添加到组**复选框均选中。
5. 如果进行了更改，请单击 "**保存更改**"。


## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint 组织级别的共享设置

为使来宾能够访问 SharePoint 网站，SharePoint 组织级别的共享设置必须允许与来宾共享。

组织级别设置确定了哪些设置可用于单个网站。 网站设置不能比组织级别设置更具有更好的许可。

如果要允许未经身份验证的文件和文件夹共享，请选择 "**任何人**"。 如果要确保所有来宾都必须进行身份验证，请选择 "**新建" 和 "现有来宾**"。 选择组织中的任何网站将需要的 "最高" 设置。

![SharePoint 组织级别共享设置的屏幕截图](media/sharepoint-organization-external-sharing-controls.png)


设置 SharePoint 组织级别的共享设置

1. 在 Microsoft 365 管理中心的左侧导航栏中，在 "**管理中心**" 下，单击 " **SharePoint**"。
2. 在 SharePoint 管理中心的左侧导航栏中，单击“**共享**”。
3. 确保将 SharePoint 的 "外部共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。
4. 如果进行了更改，请单击 "**保存**"。

## <a name="create-a-site"></a>创建网站

下一步是创建您计划用于与来宾协作的网站。

创建网站
1. 在 SharePoint 管理中心中的 "**网站**" 下，单击 "**活动网站**"。
2. 单击“**创建**”。
3. 单击 "**团队网站**"。
4. 键入网站名称并输入组所有者的名称（网站所有者）。
5. 在 "**高级设置**" 下，选择是否希望它成为公用或专用网站。
6. 单击"下一步"。
7. 单击“完成”****。

我们将稍后邀请用户。 接下来，请务必检查此网站的网站级共享设置。

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint 网站级别共享设置

检查网站级别的共享设置以确保它们允许您对此网站所需的访问类型。 例如，如果将组织级别设置设置为 "**任何人**"，但希望所有来宾都对此网站进行身份验证，请确保将网站级别的共享设置设置为 "**新建" 和 "现有来宾**"。

请注意，不能将网站与未经身份验证的人员（**任何人**设置）共享，但可以对各个文件和文件夹进行共享。

![SharePoint 网站外部共享设置的屏幕截图](media/sharepoint-site-external-sharing-settings.png)

设置网站级共享设置
1. 在 SharePoint 管理中心中，在左侧导航栏中，展开 "**网站**"，然后单击 "**活动网站**"。
2. 选择您刚刚创建的网站。
3. 在功能区中，单击 "**共享**"。
4. 确保将 "共享" 设置为 "**任何人**" 或 "**新的和现有的来宾**"。
5. 如果进行了更改，请单击 "**保存**"。

## <a name="invite-users"></a>邀请用户

现在已配置来宾共享设置，因此您可以开始向网站添加内部用户和来宾。 网站访问通过关联的 Office 365 组进行控制，因此我们将在此处添加用户。

向组邀请内部用户
1. 导航到要在其中添加用户的网站。
2. 单击右上角的 "**成员**"。
3. 单击“**添加成员**”。
4. 键入要邀请到网站的用户的名称或电子邮件地址，然后单击 "**保存**"。

无法从网站添加来宾用户。 您需要在 web 上使用 Outlook 添加它们。

将来宾邀请到网站
1. 在 web 上的 Outlook 中的 "**组**" 下，单击要在其中添加成员的组。
2. 打开组联系人卡片，然后在 "**更多选项**（...）" 下，单击 "**添加成员**"。
3. 键入要邀请的来宾的电子邮件地址，然后单击 "**添加**"。
4. 单击“关闭”****。

## <a name="see-also"></a>另请参阅

[使用未经身份验证的用户共享文件和文件夹的最佳做法](best-practices-anonymous-sharing.md)

[与来宾共享时限制文件意外曝光](sharing-limit-accidental-exposure.md)

[创建安全来宾共享环境](create-a-secure-guest-sharing-environment.md)）

