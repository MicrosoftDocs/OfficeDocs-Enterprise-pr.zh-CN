---
title: Microsoft 365 来宾共享设置参考
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 了解 Microsoft 365 中提供的来宾共享设置。
ms.openlocfilehash: 8c067374b960ff2cec7cdce87f67da0104697ff3
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782272"
---
# <a name="microsoft-365-guest-sharing-settings-reference"></a>Microsoft 365 来宾共享设置参考

本文提供了可能影响 Microsoft 365 工作负载的来宾共享的各种设置参考：Teams、Office 365 组、SharePoint 和 OneDrive。 这些设置位于 Azure Active Directory、Microsoft 365、Teams 和 SharePoint 管理中心。

## <a name="azure-active-directory"></a>Azure Active Directory

**管理员角色：** 全局管理员

Azure Active Directory 是 Microsoft 365 使用的目录服务。 Azure Active Directory 组织关系设置直接影响 Teams、Office 365 组、SharePoint 和 OneDrive 中的共享。

> [!NOTE]
> 仅当已配置 [Azure AD B2B 的 SharePoint 和 OneDrive 集成（预览）](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)时，这些设置才会影响 SharePoint。 下表假定已对此进行了配置。

### <a name="organizational-relationships-settings"></a>组织关系设置

**导航：**[Azure Active Directory 管理中心](https://aad.portal.azure.com) > Azure Active Directory > 组织关系 > 设置

![Azure Active Directory 组织关系设置页面的屏幕截图](media/azure-ad-organizational-relationships-settings.png)

|**设置**|**默认**|**说明**|
|:-----|:-----|:-----|
|来宾用户权限处于限制状态|是|此设置会影响来宾可以执行的目录任务。|
|管理员和具有“来宾邀请者”角色的用户可以邀请|是|设置为“**是**”时，管理员可以通过 Azure AD 和 Microsoft 365 共享体验（如 Teams 和 SharePoint）邀请来宾；设置为“**否**”时，则不能邀请。|
|成员可以邀请|是|设置为“**是**”时，Azure AD 成员可以通过 Azure AD 来邀请来宾；设置为“**否**”时，则不能邀请。 设置为“**是**”时，Office 365 组成员可以在所有者批准的情况下邀请来宾；设置为“**否**”时，Office 365 组成员也可以在所有者批准的情况下邀请来宾，但这些所有者必须是全局管理员才能批准。 <br><br>请注意，“**成员可以邀请**”是指 Azure AD 中的成员（与来宾相对），而不是 Microsoft 365 中的网站或组成员。 <br><br>这与 Microsoft 365 安全和隐私中的“**允许用户将新的来宾添加到组织**”设置相同。|
|来宾可以邀请|是|设置为“**是**”时，目录中的来宾可以邀请其他来宾协作处理 Azure AD 资源以及 SharePoint 和 OneDrive 中的文件和文件夹；设置为“**否**”时，则不能邀请。 <br><br>请注意，必须在 SharePoint 管理中心启用“**允许外部用户通过键入精确的电子邮件地址匹配项在目录中查找用户帐户**”，以便来宾与其他来宾共享文件和文件夹。|
|为来宾启用电子邮件一次性密码(预览)|否|设置为“**是**”时，没有 MSA 或工作或学校帐户的来宾可以[使用一次性密码对 Azure AD 进行身份验证](https://docs.microsoft.com/azure/active-directory/b2b/one-time-passcode)；设置为“**否**”时，用户需要创建 Microsoft 帐户才能进行身份验证。 必须将此设置设为“**是**”，这样“[Azure AD B2B 的 SharePoint 和 OneDrive 集成（预览）](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)”才能工作。|
|协作限制|允许向任何域发送邀请|此设置允许你为共享指定允许或阻止的域列表。 如果指定了允许的域，则只能将共享邀请发送到这些域。 如果指定了拒绝的域，则不能将共享邀请发送到这些域。<br><br> 此设置会影响 Microsoft 365 共享体验，例如 Teams 和 SharePoint。 你可以通过使用 SharePoint 或 Teams 中的域筛选功能来更精确地允许或阻止域。|

这些设置会影响邀请用户加入目录的方式。 它们不会影响与目录中已有的来宾进行共享。

## <a name="microsoft-365"></a>Microsoft 365

**管理员角色：** 全局管理员

Microsoft 365 管理中心具有用于共享和 Office 365 组的组织级别设置。

### <a name="sharing"></a>共享

**导航：**[Microsoft 365 管理中心](https://admin.microsoft.com) > 设置 > 安全和隐私 > 共享

![Microsoft 365 管理中心中的安全和隐私来宾共享设置的屏幕截图](media/sharepoint-security-privacy-sharing-setting.png)

|**设置**|**默认**|**说明**|
|:-----|:-----|:-----|
|允许用户将新的来宾添加到组织|打开|设置为“**是**”时，Azure AD 成员可以通过 Azure AD 来邀请来宾；设置为“**否**”时，则不能邀请。 设置为“**是**”时，Office 365 组成员可以在所有者批准的情况下邀请来宾；设置为“**否**”时，Office 365 组成员也可以在所有者批准的情况下邀请来宾，但这些所有者必须是全局管理员才能批准。 <br><br>请注意，“**成员可以邀请**”是指 Azure AD 中的成员（与来宾相对），而不是 Microsoft 365 中的网站或组成员。 <br><br>这与 Azure Active Directory 组织关系设置中的“**成员可以邀请**”设置相同。|

### <a name="office-365-groups"></a>Office 365 组

**导航：**[Microsoft 365 管理中心](https://admin.microsoft.com) > 设置 > 服务和加载项 > Office 365 组

![Microsoft 365 管理中心中的 Office 365 组来宾设置的屏幕截图](media/office-365-groups-guest-settings.png)

|**设置**|**默认**|**说明**|
|:-----|:-----|:-----|
|允许组织外部的组成员访问组内容|打开|设置为“**打开**”时，来宾可以访问组内容；设置为“**关闭**”时，则不能访问。 对于来宾用户与 Office 365 组或 Teams 进行交互的任何情况，此设置应为“**打开**”。|
|允许组所有者将组织外部的人员添加到组|打开|设置为“**打开**”时，Office 365 组或 Teams 的所有者可邀请新来宾加入组。 设置为“**关闭**”时，所有者只能邀请目录中已有的来宾。|

## <a name="teams"></a>Teams

必须将 Teams 主来宾访问开关“**在 Teams 中允许访客访问**”设置为“**打开**”，这样才能使其他来宾设置可用。

**管理员角色：** Teams 服务管理员

### <a name="guest-access"></a>来宾访问

**导航：**[Teams 管理中心](https://admin.teams.microsoft.com) > 组织范围的设置 > 来宾访问

![Teams 来宾访问切换的屏幕截图](media/teams-guest-access-toggle.png)

|**设置**|**默认**|**说明**|
|:-----|:-----|:-----|
|在 Teams 中允许访客访问|关闭|打开或关闭整个 Teams 的来宾访问。 更改后，此设置可能需要 24 小时才能生效。|

### <a name="guest-calling"></a>来宾呼叫

**导航：**[Teams 管理中心](https://admin.teams.microsoft.com) > 组织范围的设置 > 来宾访问

![Teams 来宾呼叫选项的屏幕截图](media/teams-guest-calling-setting.png)

|**设置**|**默认**|**说明**|
|:-----|:-----|:-----|
|拨打私人电话|打开|设置为“**打开**”时，来宾可以在 Teams 中进行对等呼叫；设置为“**关闭**”时，则不能执行此操作。|

### <a name="guest-meeting"></a>来宾会议

**导航：**[Teams 管理中心](https://admin.teams.microsoft.com) > 组织范围的设置 > 来宾访问

![Teams 来宾会议设置的屏幕截图](media/teams-guest-meeting-settings.png)

|**设置**|**默认**|**说明**|
|:-----|:-----|:-----|
|允许 IP 视频|打开|设置为“**打开**”时，来宾可以在电话和会议中使用视频；设置为“**关闭**”时，则不能执行此操作。|
|屏幕共享模式|整个屏幕|设置为“**已禁用**”时，来宾无法在 Teams 中共享其屏幕。 设置为“**单个应用程序**”时，来宾只能在其屏幕上共享一个应用程序。 设置为“**整个屏幕**”时，来宾可以选择共享应用程序或其整个屏幕。|
|允许立即开会|打开|设置为“**打开**”时，来宾可以使用 Teams 中的“立即开会”功能；设置为“**关闭**”时，则不能使用该功能。|

### <a name="guest-messaging"></a>来宾消息传递

**导航：**[Teams 管理中心](https://admin.teams.microsoft.com) > 组织范围的设置 > 来宾访问

![Teams 来宾消息传递设置的屏幕截图](media/teams-guest-messaging-settings.png)

|**设置**|**默认**|**说明**|
|:-----|:-----|:-----|
|编辑已发送的消息|打开|设置为“**打开**”时，来宾可以编辑他们之前发送的消息；设置为“**关闭**”时，则无法执行此操作。|
|删除已发送的消息|打开|设置为“**打开**”时，来宾可以删除他们之前发送的消息；设置为“**关闭**”时，则无法执行此操作。|
|聊天|打开|设置为“**打开**”时，来宾可以使用 Teams 中的聊天功能；设置为“**关闭**”时，则不能使用该功能。|
|在对话中使用 Giphy|打开|设置为“**打开**”时，来宾可以在对话中使用 Giphy；设置为“**关闭**”时，则不能使用它。|
|Giphy 内容评级|适度|设置为“**允许所有内容**”时，无论内容评级如何，来宾都可以在聊天中插入所有 Giphys。 设置为“**适度**”时，来宾可以在聊天中插入 Giphys，但会适度限制成人内容。 设置为“**严格**”时，来宾可以在聊天中插入 Giphys，但会限制插入成人内容。|
|在对话中使用 Meme|打开|设置为“**打开**”时，来宾可以在对话中使用 Meme；设置为“**关闭**”时，则不能使用它。|
|对话中的用户贴纸|打开|设置为“**打开**”时，来宾可以在对话中使用贴纸；设置为“**关闭**”时，则不能使用它。|
|允许沉浸式阅读器以查看消息|打开|设置为“**打开**”时，来宾可以在沉浸式阅读器中查看消息；设置为“**关闭**”时，则无法执行此操作。|

## <a name="sharepoint-and-onedrive-organization-level"></a>SharePoint 和 OneDrive（组织级别）

**管理员角色：** SharePoint 管理员

这些设置会影响组织中的所有网站。 它们不会直接影响 Office 365 组或 Teams，但建议使这些设置与 Office 365 组和 Teams 的设置保持一致，以避免用户体验问题。 （例如，如果在 Teams 而非 SharePoint 中允许来宾共享，则 Teams 中的来宾将无法访问“文件”选项卡，因为 Teams 文件存储在 SharePoint 中。）

### <a name="sharepoint-and-onedrive-sharing-settings"></a>SharePoint 和 OneDrive 共享设置

由于 OneDrive 是 SharePoint 中的网站层次结构，因此组织级别共享设置将直接影响 OneDrive，如同影响其他 SharePoint 网站一样。

**导航：** SharePoint 管理中心 > 共享

![SharePoint 组织级别共享设置的屏幕截图](media/sharepoint-organization-external-sharing-controls.png)

|**设置**|**默认**|**说明**|
|:-----|:-----|:-----|
|SharePoint|任何人|指定 SharePoint 网站允许的最宽松共享权限。|
|OneDrive|任何人|指定 OneDrive 网站允许的最宽松共享权限。 此设置不能比 SharePoint 设置更宽松。|

### <a name="sharepoint-and-onedrive-advanced-sharing-settings"></a>SharePoint 和 OneDrive 高级共享设置

**导航：** SharePoint 管理中心 > 共享

![SharePoint 组织级别的其他共享设置的屏幕截图](media/sharepoint-organization-advanced-sharing-settings.png)

|**设置**|**默认**|**说明**|
|:-----|:-----|:-----|
|按域限制外部共享|关闭|此设置允许你为共享指定允许或阻止的域列表。 如果指定了允许的域，则只能将共享邀请发送到这些域。 如果指定了拒绝的域，则不能将共享邀请发送到这些域。<br><br> 此设置会影响组织中的所有 SharePoint 和 OneDrive 网站。|
|来宾必须使用发送共享邀请的同一帐户登录|关闭|阻止来宾使用与接收邀请的电子邮件地址不同的地址来兑换网站共享邀请。<br><br>[Azure AD B2B 的 SharePoint 和 OneDrive 集成（预览）](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)不使用此设置，因为所有来宾都将根据接收邀请的电子邮件地址添加到目录中。 备选电子邮件地址无法用于访问网站。|
|允许来宾共享不属于他们的项目|打开|设置为“**打开**”时，来宾可以与其他用户或来宾共享不属于他们的项目；设置为“**关闭**”时，则无法执行此操作。 来宾始终可以共享其拥有完全控制权的项目。|

### <a name="sharepoint-and-onedrive-file-and-folder-link-settings"></a>SharePoint 和 OneDrive 文件和文件夹链接设置

在 SharePoint 和 OneDrive 中共享文件和文件夹时，系统会向共享收件人发送一个具有该文件或文件夹权限的链接，而不是授予对文件或文件夹本身的直接访问权限。 提供了多种类型的链接，你可以选择在共享文件或文件夹时向用户显示的默认链接类型。 你还可以为“*任何人*”链接设置权限和到期选项。

**导航：** SharePoint 管理中心 > 共享

![SharePoint 组织级别文件和文件夹共享设置的屏幕截图](media/sharepoint-organization-files-folders-sharing-settings.png)

|**设置**|**默认**|**说明**|
|:-----|:-----|:-----|
|文件和文件夹链接|使用此链接的任何人|指定用户共享文件或文件夹时默认显示的共享链接。 如果需要，用户可以在共享前更改此选项。 如果将默认设置设为“**使用此链接的任何人**”并且指定的网站不允许“*任何人*”共享，则“**仅限组织中的人员**”将显示为该网站的默认设置。|
|这些链接必须在该天数内过期|关闭（无过期期限）|指定“*任何人*”链接在创建后的多少天内过期。 无法续订已过期的链接。 如果需要在过期后继续共享，请创建新链接。|
|文件权限|查看和编辑|指定创建“*任何人*”链接时向用户提供的文件权限级别。 如果已选择“**查看**”，则用户只能创建具有查看权限的“*任何人*”文件链接。 如果已选择“**查看和编辑**”，则用户可以在创建链接时选择查看权限或查看和编辑权限。|
|文件夹权限|查看、编辑和上传|指定创建“*任何人*”链接时向用户提供的文件夹权限级别。 如果已选择“**查看**”，则用户只能创建具有查看权限的“*任何人*”文件夹链接。 如果已选择“**查看、编辑和上传**”，则用户可以在创建链接时选择查看权限或查看、编辑和上传权限。|

### <a name="sharepoint-and-onedrive-security-group-settings"></a>SharePoint 和 OneDrive 安全组设置

如果想要在 SharePoint 和 OneDrive 中限制可与来宾进行共享的人员，则可以通过将共享限制为指定安全组中的人员来实现这一点。 这些设置不会影响通过 Office 365 组或 Teams 进行共享。 尽管只能由指定安全组中的人员来共享文档和文件夹，但通过组或团队邀请的来宾还有权访问关联的网站。

**导航：** SharePoint 管理中心 > 共享 > 将外部共享的范围限制到特定安全组

![SharePoint 组织级别共享安全组设置的屏幕截图](media/sharepoint-organization-external-sharing-security-groups.png)

|**设置**|**默认**|**说明**|
|:-----|:-----|:-----|
|仅让所选安全组中的用户与已验证的外部用户共享|关闭|设置为“**打开**”时，只有指定安全组中的人员才能与外部用户共享。 仅提供“*特定人员*”链接。 除非“**仅让所选安全组中的用户使用匿名链接与已验证的外部用户共享**”也设置为“**打开**”，才会有效禁用“*任何人*”链接。|
|仅让所选安全组中的用户使用匿名链接与已验证的外部用户共享|关闭|设置为“**打开**”时，只有指定安全组中的人员才能与来宾共享。 提供“*任何人*”和“*特定人员*”链接。|

可同时使用这两个设置。 如果用户位于为这两个设置指定的安全组中，则以更高权限级别为准（“*任何人*”加“*特定用户*”）。

## <a name="sharepoint-site-level"></a>SharePoint（网站级别）

**管理员角色：** SharePoint 管理员

### <a name="site-sharing"></a>网站共享

可为 SharePoint 中的每个网站设置来宾共享权限。 此设置适用于网站共享以及文件和文件夹共享。 （“*任何人*”共享不可用于网站共享。 如果你选择“**任何人**”，则用户可以使用“*任何人*”链接来共享文件和文件夹，并且网站本身可以与新来宾和现有来宾共享。）

**导航：** SharePoint 管理中心 > 活动网站 > 选择网站 > 共享

![SharePoint 网站外部共享设置的屏幕截图](media/sharepoint-site-external-sharing-settings.png)

|**设置**|**默认**|**说明**|
|:-----|:-----|:-----|
|网站内容可与以下人员共享|因网站类型而异（参见下表）|指示此网站允许的外部共享类型。 此处提供的选项取决于 SharePoint 的组织级别共享设置。|

由于这些设置取决于 SharePoint 的组织范围设置，如果组织级别设置发生更改，则网站的有效共享设置可能会随之更改。 如果你在此处选择设置，并且组织级别随后设置为更严格的值，则此网站将以这一更严格的值运行。 例如，如果你选择“**任何人**”，并且组织级别设置随后设为“**新来宾和现有来宾**”，则此网站将仅允许新来宾和现有来宾进行共享。 如果组织级别设置随后设置回“**任何人**”，则此网站将再次允许使用“*任何人*”链接。

下表显示了每种网站类型的默认共享设置。

|**网站类型**|**默认共享设置**|
|:-----|:-----|
|经典|**仅组织内部人员**|
|OneDrive|**任何人**|
|与组连接的网站（包括 Teams）|**新来宾和现有来宾** — 如果 Office 365 组设置“**允许组所有者将组织外部的人员添加到组**”设置为“**打开**”；否则为“**仅现有来宾**”|
|通信|**仅组织内部人员**|
|不含组的新式网站 (#STS3 TeamSite)|**仅组织内部人员**|

## <a name="see-also"></a>另请参阅

[SharePoint 和 OneDrive 外部共享概述](https://docs.microsoft.com/sharepoint/external-sharing-overview)

[Microsoft Teams 中的来宾访问](https://docs.microsoft.com/MicrosoftTeams/guest-access)

[将来宾添加到 Office 365 组](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)
