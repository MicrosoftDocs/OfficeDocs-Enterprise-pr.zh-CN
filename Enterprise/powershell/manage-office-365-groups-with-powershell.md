---
title: 使用 PowerShell 管理 Office 365 组
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: Admin
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
description: 了解如何执行常见管理任务的 PowerShell 的 Microsoft Office 365 组。
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 662d75796991bac4e959348ded4999008875422e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2019
ms.locfileid: "29760054"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="49b1d-103">使用 PowerShell 管理 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="49b1d-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="49b1d-104">*上次更新 18 年 4 月，2018*</span><span class="sxs-lookup"><span data-stu-id="49b1d-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="49b1d-p101">本文提供的 Microsoft PowerShell 组执行常见管理任务的步骤。它还列出了组的 PowerShell cmdlet。有关管理 SharePoint 网站的信息，请参阅[使用 PowerShell 管理 SharePoint Online 网站](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)。</span><span class="sxs-lookup"><span data-stu-id="49b1d-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="49b1d-108">链接到您的 Office 365 组使用指南</span><span class="sxs-lookup"><span data-stu-id="49b1d-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="49b1d-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="49b1d-109"></span></span>

<span data-ttu-id="49b1d-p102">当用户[创建或编辑 Outlook 中的组](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)，您可以显示了其指向您的组织使用指南的链接。例如，如果您需要一个特定的前缀，或要添加到组名称后缀。</span><span class="sxs-lookup"><span data-stu-id="49b1d-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="49b1d-p103">使用 Azure PowerShell Active Directory 用户指向 Office 365 组的组织使用指南。签出[Azure Active Directory cmdlet 配置组设置](https://go.microsoft.com/fwlink/?LinkID=827484)，并按照**创建目录级别的设置**以定义用法准则超链接中的步骤。一次运行 AAD cmdlet 时，用户将看到指南链接时不创建或编辑组在 Outlook 中。</span><span class="sxs-lookup"><span data-stu-id="49b1d-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![与使用准则链接创建新组](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![单击组使用指南，以查看组织 Office 365 组准则](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="49b1d-117">为 Office 365 组允许用户发送</span><span class="sxs-lookup"><span data-stu-id="49b1d-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="49b1d-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="49b1d-118"></span></span>
  
<span data-ttu-id="49b1d-p104">如果您想要启用"发送为"在 Office 365 组，使用[Add-recipientpermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission)和[Get RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlet 可将其配置。一旦您启用此设置，Office 365 组用户可以使用 Outlook 或 Outlook web 上发送并答复电子邮件与 Office 365 组中。用户可以转到组中，创建新的电子邮件，并将"发送为"字段更改为组的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="49b1d-p104">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="49b1d-122">([您还可以这在 Exchange 管理中心中](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group))。</span><span class="sxs-lookup"><span data-stu-id="49b1d-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="49b1d-p105">使用以下脚本，替换*\<GroupAlias\>* 与您要更新的组的别名和*\<UserAlias\>* 与您要向其授予权限的用户的别名。[连接到 Exchange Online PowerShell 中](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)运行此脚本。</span><span class="sxs-lookup"><span data-stu-id="49b1d-p105">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="49b1d-125">后执行 cmdlet 时，用户可以转到 Outlook 或 Outlook web 上的为组中，通过**从**字段中添加组电子邮件地址发送。</span><span class="sxs-lookup"><span data-stu-id="49b1d-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="49b1d-126">在您的组织中创建 Office 组分类</span><span class="sxs-lookup"><span data-stu-id="49b1d-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="49b1d-p106">您可以创建您的组织中的用户创建 Office 365 组时可以设置的分类。例如，您可以允许用户为他们创建的组设置"标准"、"Secret"和"顶部机密"。组分类未设置默认情况下，您需要创建用户将其设置的顺序。使用 Azure Active Directory PowerShell 用户指向 Office 365 组的组织使用指南。</span><span class="sxs-lookup"><span data-stu-id="49b1d-p106">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="49b1d-131">签出[Azure Active Directory cmdlet 配置组设置](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets)，并按照**创建设置目录级别**定义的分类的 Office 365 组中的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="49b1d-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="49b1d-132">若要关联到您可以使用每个分类的说明设置属性*ClassificationDescriptions*定义。</span><span class="sxs-lookup"><span data-stu-id="49b1d-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="49b1d-133">其中分类匹配 ClassificationList 中的字符串。</span><span class="sxs-lookup"><span data-stu-id="49b1d-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="49b1d-134">示例：</span><span class="sxs-lookup"><span data-stu-id="49b1d-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="49b1d-135">运行上述的 Azure Active Directory cmdlet，设置您的分类之后，运行[设置 UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet，如果您想要设置一组特定的分类。</span><span class="sxs-lookup"><span data-stu-id="49b1d-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="49b1d-136">或创建具有一个分类的新组。</span><span class="sxs-lookup"><span data-stu-id="49b1d-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="49b1d-137">检查出[与 Exchange Online Using PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)和[连接到 Exchange Online PowerShell 中](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)使用 Exchange Online PowerShell 中的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="49b1d-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="49b1d-138">一旦启用这些设置，则组的所有者将能够从在 Outlook 中的 Web 和 Outlook 中，在下拉菜单中选择一个分类并将其保存从**编辑**组页。</span><span class="sxs-lookup"><span data-stu-id="49b1d-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![选择 Office 365 组分类](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="49b1d-140">隐藏 GAL 中的 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="49b1d-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="49b1d-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="49b1d-141"></span></span>

<span data-ttu-id="49b1d-p107">您可以指定是否在全局地址列表 (GAL) 和您的组织中的其他列表中会出现一个 Office 365 组。例如，如果您不想要的地址列表中显示的法律部门组，可以停止在 GAL 中显示的组。运行 Set-Unified 组 cmdlet 来隐藏组地址列表如下所示：</span><span class="sxs-lookup"><span data-stu-id="49b1d-p107">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="49b1d-145">只允许内部用户向 Office 365 组发送消息</span><span class="sxs-lookup"><span data-stu-id="49b1d-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="49b1d-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="49b1d-146"></span></span>

<span data-ttu-id="49b1d-p108">如果您不希望用户从其他组织到 Office 365 组发送电子邮件，您可以更改组的设置。它将只允许内部用户向组发送电子邮件。如果外部用户尝试向该组发送消息，它们将被拒绝。</span><span class="sxs-lookup"><span data-stu-id="49b1d-p108">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="49b1d-150">运行设置 UnifiedGroup cmdlet 以更新此设置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="49b1d-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="49b1d-151">向 Office 365 的组添加邮件提示</span><span class="sxs-lookup"><span data-stu-id="49b1d-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="49b1d-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="49b1d-152"></span></span>

<span data-ttu-id="49b1d-153">只要尝试向 Office 365 组发送电子邮件发件人，可向其显示邮件提示。</span><span class="sxs-lookup"><span data-stu-id="49b1d-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="49b1d-154">运行 Set-Unified 组 cmdlet，以向组添加邮件提示：</span><span class="sxs-lookup"><span data-stu-id="49b1d-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="49b1d-p109">邮件提示，以及您还可以设置 MailTipTranslations，指定其他语言的邮件提示。假设您想要有西班牙语翻译，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="49b1d-p109">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="49b1d-157">更改 Office 365 组的显示名称</span><span class="sxs-lookup"><span data-stu-id="49b1d-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="49b1d-p110">显示名称指定 Office 365 组的名称。您可以看到您的 exchange 管理中心或 Office 365 管理门户中此名称。您可以编辑组的显示名称或通过运行设置 UnifiedGroup 命令分配现有 Office 365 组的显示名称：</span><span class="sxs-lookup"><span data-stu-id="49b1d-p110">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or Office 365 admin portal. You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="49b1d-161">更改用于 Outlook 的 Office 365 组的默认设置为 Public 或 Private</span><span class="sxs-lookup"><span data-stu-id="49b1d-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="49b1d-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="49b1d-162"></span></span>

<span data-ttu-id="49b1d-p111">Office 365 在 Outlook 中创建组为私有默认情况下。如果您的组织希望 Office 365 组创建为公共默认情况下 （或回专用），使用以下 PowerShell cmdlet 的语法：</span><span class="sxs-lookup"><span data-stu-id="49b1d-p111">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="49b1d-165">若要设置为 Private:</span><span class="sxs-lookup"><span data-stu-id="49b1d-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="49b1d-166">若要验证设置：</span><span class="sxs-lookup"><span data-stu-id="49b1d-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="49b1d-167">若要了解详细信息，请参阅[Set-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig)和[Get-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig)。</span><span class="sxs-lookup"><span data-stu-id="49b1d-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="49b1d-168">Office 365 组 cmdlet</span><span class="sxs-lookup"><span data-stu-id="49b1d-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="49b1d-169">以下 cmdlet 可用于 Office 365 组。</span><span class="sxs-lookup"><span data-stu-id="49b1d-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="49b1d-170">**Cmdlet 名称**</span><span class="sxs-lookup"><span data-stu-id="49b1d-170">**Cmdlet name**</span></span>|<span data-ttu-id="49b1d-171">**说明**</span><span class="sxs-lookup"><span data-stu-id="49b1d-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="49b1d-172">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="49b1d-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="49b1d-173">使用此 cmdlet，以查找现有 Office 365 组，并查看组对象的属性</span><span class="sxs-lookup"><span data-stu-id="49b1d-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="49b1d-174">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="49b1d-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="49b1d-175">更新特定的 Office 365 组的属性</span><span class="sxs-lookup"><span data-stu-id="49b1d-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="49b1d-176">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="49b1d-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="49b1d-p112">创建新的 Office 365 组。此 cmdlet 提供了一组最少的参数，设置扩展属性的值使用集 UnifiedGroup 创建新组后</span><span class="sxs-lookup"><span data-stu-id="49b1d-p112">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="49b1d-179">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="49b1d-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="49b1d-180">删除现有的 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="49b1d-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="49b1d-181">Get UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="49b1d-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="49b1d-182">检索为 Office 365 组的成员资格和所有者信息</span><span class="sxs-lookup"><span data-stu-id="49b1d-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="49b1d-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="49b1d-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="49b1d-184">添加十万或数千个用户或新的所有者，到现有 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="49b1d-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="49b1d-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="49b1d-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="49b1d-186">删除现有的 Office 365 组的所有者和成员</span><span class="sxs-lookup"><span data-stu-id="49b1d-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="49b1d-187">Get UserPhoto</span><span class="sxs-lookup"><span data-stu-id="49b1d-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="49b1d-p113">用于查看有关帐户相关联的用户照片的信息。用户照片存储在 Active Directory</span><span class="sxs-lookup"><span data-stu-id="49b1d-p113">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="49b1d-190">设置 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="49b1d-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="49b1d-p114">用于将用户照片关联的帐户。用户照片存储在 Active Directory</span><span class="sxs-lookup"><span data-stu-id="49b1d-p114">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="49b1d-193">删除 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="49b1d-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="49b1d-194">删除 Office 365 组中的照片</span><span class="sxs-lookup"><span data-stu-id="49b1d-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="49b1d-195">相关主题</span><span class="sxs-lookup"><span data-stu-id="49b1d-195">Related topics</span></span>

[<span data-ttu-id="49b1d-196">向 Office 365 组升级的通讯组列表</span><span class="sxs-lookup"><span data-stu-id="49b1d-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="49b1d-197">管理可创建 Office 365 组的人员</span><span class="sxs-lookup"><span data-stu-id="49b1d-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="49b1d-198">管理对 Office 365 组的来宾访问</span><span class="sxs-lookup"><span data-stu-id="49b1d-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="49b1d-199">更改静态组成员身份为动态中</span><span class="sxs-lookup"><span data-stu-id="49b1d-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
