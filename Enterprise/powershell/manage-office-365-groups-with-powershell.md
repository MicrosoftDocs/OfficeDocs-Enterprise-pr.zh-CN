---
title: 使用 PowerShell 管理 Office 365 组
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: 了解如何在 Microsoft PowerShell 中执行 Office 365 组的常见管理任务。
ms.openlocfilehash: 7e07041516acd3c2038dd92b464073279c49d1a6
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017340"
---
# <a name="manage-office-365-groups-with-powershell"></a>使用 PowerShell 管理 Office 365 组

 *最后更新了18年4月2018* 
  
本文提供在 Microsoft PowerShell 中对组执行常见管理任务的步骤。 此外，它还列出了组的 PowerShell cmdlet。 有关管理 SharePoint 网站的信息，请参阅[使用 PowerShell 管理 Sharepoint Online 网站](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)。

## <a name="link-to-your-office-365-groups-usage-guidelines"></a>链接到 Office 365 组使用指南
<a name="BK_LinkToGuideLines"> </a>

当用户[在 Outlook 中创建或编辑组](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)时，您可以向他们显示您的组织使用指南的链接。 例如，如果需要将特定的前缀或后缀添加到组名称中。
  
使用 Azure Active Directory PowerShell 将用户指向组织的 Office 365 组的使用指南。 请查看[Azure Active Directory cmdlet 以配置组设置](https://go.microsoft.com/fwlink/?LinkID=827484)，并按照在**目录级别创建设置**中的步骤定义使用情况准则超链接。 一旦运行 AAD cmdlet，当用户在 Outlook 中创建或编辑组时，用户将看到指向您的指导方针的链接。 
  
![创建具有使用指南链接的新组](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![单击 "组使用指南" 查看组织的 Office 365 组指南](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a>允许用户以 Office 365 组的形式发送
<a name="BK_LinkToGuideLines"> </a>
  
如果要将 Office 365 组启用为 "代理发送"，请使用[add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission)和[add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlet 对此进行配置。 启用此设置后，Office 365 组用户可以使用 Outlook 或 web 上的 Outlook 以电子邮件的形式发送和回复电子邮件作为 Office 365 组。 用户可以转到组，创建新的电子邮件，并将 "代理发送" 字段更改为组的电子邮件地址。 

（[也可以在 Exchange 管理中心中执行此操作](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)。）
  
使用以下脚本，将* \<GroupAlias\> *替换为您要更新的组的别名，并* \<\> *使用要向其授予 permssions 的用户的别名 UserAlias。 [连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)以运行此脚本。

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

一旦执行 cmdlet，用户就可以通过将组电子邮件地址添加到 "**发件**人" 字段，转到要作为组发送的 outlook 或 web 上的 outlook。 

## <a name="create-classifications-for-office-groups-in-your-organization"></a>为组织中的 Office 组创建分类

您可以创建组织中的用户在创建 Office 365 组时可以设置的分类。 例如，您可以允许用户在其创建的组上设置 "Standard"、"Secret" 和 "Top Secret"。 默认情况下，不会设置组分类，您需要创建它才能使用户对其进行设置。 使用 Azure Active Directory PowerShell 将用户指向组织的 Office 365 组的使用指南。
  
查看[用于配置组设置的 Azure Active Directory cmdlet](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) ，并按照在**目录级别创建设置**中的步骤定义 Office 365 组的分类。 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

为了将说明与每个分类相关联，您可以使用 settings 属性*ClassificationDescriptions*来定义。
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

其中，分类与 ClassificationList 中的字符串匹配。

示例：
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

在运行上述 Azure Active Directory cmdlet 以设置分类之后，如果您想要为特定组设置分类，请运行[remove-unifiedgroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet。 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

或创建一个具有分类的新组。
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

请查看[使用 PowerShell With Exchange online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) ，并[连接到 Exchange online powershell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) ，了解有关使用 exchange online powershell 的更多详细信息。 
  
启用这些设置后，组所有者将能够从 Web 上的 Outlook 和 Outlook 中的下拉菜单中选择一个分类，并将其保存在 "**编辑**组" 页面中。 
  
![选择 Office 365 组分类](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a>隐藏 GAL 中的 Office 365 组
<a name="BKMK_CreateClassification"> </a>

您可以指定是否在全局地址列表（GAL）和组织中的其他列表中显示 Office 365 组。 例如，如果您有一个您不想在地址列表中显示的法律部门组，您可以阻止该组出现在 GAL 中。 运行 "设置统一组" cmdlet 以将组从地址列表中隐藏，如下所示：
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>仅允许内部用户向 Office 365 组发送邮件
<a name="BKMK_CreateClassification"> </a>

如果不希望其他组织中的用户向 Office 365 组发送电子邮件，则可以更改该组的设置。 仅允许内部用户向你的组发送电子邮件。 如果外部用户尝试向该组发送邮件，则会被拒绝。
  
运行 Remove-unifiedgroup cmdlet 以更新此设置，如下所示：

```
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a>向 Office 365 组添加邮件提示
<a name="BKMK_CreateClassification"> </a>

当发件人尝试向 Office 365 组发送电子邮件时，可以向其显示邮件提示。
  
运行 "设置统一组" cmdlet 以将邮件提示添加到组中：

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

除了邮件提示，还可以设置 MailTipTranslations，后者为邮件提示指定其他语言。 假设您想要进行西班牙语转换，然后运行以下命令：
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a>更改 Office 365 组的显示名称

"显示名称" 指定 Office 365 组的名称。 您可以在 exchange 管理中心或 Office 365 管理门户中看到此名称。 您可以编辑组的显示名称，或通过运行 Remove-unifiedgroup 命令为现有的 Office 365 组分配显示名称：

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>将适用于 Outlook 的 Office 365 组的默认设置更改为公共或专用
<a name="BKMK_CreateClassification"> </a>

默认情况下，Outlook 中的 Office 365 组创建为私有。 如果您的组织希望在默认情况下（或返回到私有）将 Office 365 组创建为 Public，请使用以下 PowerShell cmdlet 语法：
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
设置为专用：
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
若要验证设置，请执行以下操作： 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
若要了解详细信息，请参阅[set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig)和[set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig)。
  
## <a name="office-365-groups-cmdlets"></a>Office 365 组 cmdlet

以下 cmdlet 可与 Office 365 组一起使用。
  
|**Cmdlet 名称**|**说明**|
|:-----|:-----|
|[Remove-unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |使用此 cmdlet 可查找现有的 Office 365 组，并查看组对象的属性  <br/> |
|[Remove-unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |更新特定 Office 365 组的属性  <br/> |
|[新 Remove-unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |创建新的 Office 365 组。 此 cmdlet 提供了一组最少的参数，用于设置扩展属性的值在创建新组后使用 Remove-unifiedgroup  <br/> |
|[Remove-unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |删除现有的 Office 365 组  <br/> |
|[UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |检索 Office 365 组的成员资格和所有者信息  <br/> |
|[外接 UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |向现有 Office 365 组添加成百上千个用户或新所有者  <br/> |
|[UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |从现有 Office 365 组中删除所有者和成员  <br/> |
|[Set-userphoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |用于查看有关与帐户关联的用户照片的信息。 用户照片存储在 Active Directory 中  <br/> |
|[Set-userphoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |用于将用户照片与帐户关联。 用户照片存储在 Active Directory 中  <br/> |
|[Set-userphoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |删除 Office 365 组的照片  <br/> |

## <a name="related-topics"></a>相关主题

[将通讯组列表升级到 Office 365 组](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[管理可以创建 Office 365 组的用户](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[管理对 Office 365 组的来宾访问](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[将静态组成员身份更改为中的动态](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
