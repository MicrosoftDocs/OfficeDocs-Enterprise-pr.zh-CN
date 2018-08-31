---
title: 管理 Office 365 PowerShell 组
ms.author: dianef
author: dianef77
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: 上次更新 18 年 4 月，2018
ms.openlocfilehash: 8def3b304a19ad57887c992aa6342ea2cf14ba28
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539884"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="0b78b-103">管理 Office 365 PowerShell 组</span><span class="sxs-lookup"><span data-stu-id="0b78b-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="0b78b-104">*上次更新 18 年 4 月，2018*</span><span class="sxs-lookup"><span data-stu-id="0b78b-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="0b78b-p101">本文提供的 Microsoft PowerShell 组执行常见管理任务的步骤。它还列出了组的 PowerShell cmdlet。有关管理 SharePoint 网站的信息，请参阅[管理工作组网站和使用 PowerShell 通信网站](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87)。</span><span class="sxs-lookup"><span data-stu-id="0b78b-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage team sites and communication sites by using PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87).</span></span>
  
## <a name="common-tasks-for-managing-office-365-groups"></a><span data-ttu-id="0b78b-108">管理 Office 365 组的常见任务</span><span class="sxs-lookup"><span data-stu-id="0b78b-108">Common tasks for managing Office 365 Groups</span></span>

- [<span data-ttu-id="0b78b-109">升级的通讯组列表向 Outlook 中的 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="0b78b-109">Upgrade distribution lists to Office 365 Groups in Outlook</span></span>](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f)
    
- [<span data-ttu-id="0b78b-110">管理谁可以创建 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="0b78b-110">Manage who can create Office 365 Groups</span></span>](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618)
    
- [<span data-ttu-id="0b78b-111">管理 Office 365 组来宾访问</span><span class="sxs-lookup"><span data-stu-id="0b78b-111">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96)
    
- [<span data-ttu-id="0b78b-112">动态在 Azure Active Directory 中管理组</span><span class="sxs-lookup"><span data-stu-id="0b78b-112">Manage groups dynamically in Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/?linkid=847632)
    
- <span data-ttu-id="0b78b-113">将数百或数千个用户添加到 Office 365 组，请使用[添加 UnifiedGroupLinks cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=616191)。</span><span class="sxs-lookup"><span data-stu-id="0b78b-113">Add hundreds or thousands of users to Office 365 groups, use the [Add-UnifiedGroupLinks cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span></span>
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="0b78b-114">链接到您的 Office 365 组使用指南</span><span class="sxs-lookup"><span data-stu-id="0b78b-114">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="0b78b-115"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="0b78b-115"></span></span>

<span data-ttu-id="0b78b-p102">当用户[创建 Outlook 中的组](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102)，您可以显示其指向您的组织使用指南的链接。例如，如果您需要一个特定的前缀，或要添加到组名称后缀。</span><span class="sxs-lookup"><span data-stu-id="0b78b-p102">When users [Create a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="0b78b-p103">使用 Azure PowerShell Active Directory 用户指向 Office 365 组的组织使用指南。签出[Azure Active Directory cmdlet 配置组设置](https://go.microsoft.com/fwlink/?LinkID=827484)，并按照**创建目录级别的设置**以定义用法准则超链接中的步骤。一次运行 AAD cmdlet 时，用户将看到指南链接时不创建或编辑组在 Outlook 中。</span><span class="sxs-lookup"><span data-stu-id="0b78b-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![与使用准则链接创建新组](./../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![单击组使用指南，以查看组织 Office 365 组准则](./../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="0b78b-123">为 Office 365 组允许用户发送</span><span class="sxs-lookup"><span data-stu-id="0b78b-123">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="0b78b-124"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="0b78b-124"></span></span>

<span data-ttu-id="0b78b-p104">您也可以在 Exchange 管理中心中执行此操作。请参阅[允许成员作为发送或代表组发送邮件](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590)。</span><span class="sxs-lookup"><span data-stu-id="0b78b-p104">You can also do this in the Exchange Admin Center. See [Allow members to send as or send on behalf of a Group](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590).</span></span>
  
<span data-ttu-id="0b78b-p105">如果您想要启用"发送为"在 Office 365 组，使用[Add-recipientpermission](https://go.microsoft.com/fwlink/p/?LinkId=723960)和[Get RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cmdlet 可将其配置。一旦您启用此设置，Office 365 组用户可以使用 Outlook 或 Outlook web 上发送并答复电子邮件与 Office 365 组中。用户可以转到组中，创建新的电子邮件，并将"发送为"字段更改为组的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="0b78b-p105">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) and the [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="0b78b-130">您需要将组电子邮件地址添加到**抄送**字段中，在您撰写"发送作为"电子邮件，以便邮件发送到组，并显示在组对话中。</span><span class="sxs-lookup"><span data-stu-id="0b78b-130">You'll need to add the group email address to the **Cc** field when you compose the "send as" email, so that the message is sent to the Group and appears in group conversations.</span></span> 
  
<span data-ttu-id="0b78b-131">此时，更新邮箱策略的唯一方法是通过[PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0b78b-131">At this time, the only way to update the mailbox policy is through [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span></span>
  
- <span data-ttu-id="0b78b-132">使用此命令将设置组的别名。</span><span class="sxs-lookup"><span data-stu-id="0b78b-132">Use this command to set the group alias.</span></span>
    
  ```
  $groupAlias = "TestSendAs"
  ```

- <span data-ttu-id="0b78b-133">使用此命令将设置的用户别名。</span><span class="sxs-lookup"><span data-stu-id="0b78b-133">Use this command to set the user alias.</span></span>
    
  ```
  $userAlias = "User"
  ```

- <span data-ttu-id="0b78b-134">使用此命令将 groupalias 传递给 Get-recipient cmdlet，以获取收件人的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0b78b-134">Use this command to pass the groupalias to the Get-Recipient cmdlet to get the recipient details.</span></span>
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- <span data-ttu-id="0b78b-p106">然后目标收件人姓名 （组名称） 需要传递给 Add-recipientpermission cmdlet。会为其授予 sendas 权限 useralias 将分配给-受信任项参数。</span><span class="sxs-lookup"><span data-stu-id="0b78b-p106">Then the target recipient name (Group name) needs to be passed to the Add-RecipientPermission cmdlet. The useralias for whom the sendas permission will be given will be assigned to the -Trustee parameter.</span></span>
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- <span data-ttu-id="0b78b-137">后执行 cmdlet 时，用户可以转到 Outlook 或 Outlook web 上的为组中，通过**从**字段中添加组电子邮件地址发送。</span><span class="sxs-lookup"><span data-stu-id="0b78b-137">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="0b78b-138">在您的组织中创建 Office 组分类</span><span class="sxs-lookup"><span data-stu-id="0b78b-138">Create classifications for Office groups in your organization</span></span>
<span data-ttu-id="0b78b-139"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="0b78b-139"></span></span>

<span data-ttu-id="0b78b-p107">您可以创建您的组织中的用户创建 Office 365 组时可以设置的分类。例如，您可以允许用户为他们创建的组设置"标准"、"Secret"和"顶部机密"。组分类未设置默认情况下，您需要创建用户将其设置的顺序。使用 Azure Active Directory PowerShell 用户指向 Office 365 组的组织使用指南。</span><span class="sxs-lookup"><span data-stu-id="0b78b-p107">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="0b78b-144">签出[Azure Active Directory cmdlet 配置组设置](https://go.microsoft.com/fwlink/?LinkID=827484)，并按照**创建设置目录级别**定义的分类的 Office 365 组中的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="0b78b-144">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="0b78b-145">若要关联到您可以使用每个分类的说明设置属性*ClassificationDescriptions*定义。</span><span class="sxs-lookup"><span data-stu-id="0b78b-145">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions*  to define.</span></span> 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

<span data-ttu-id="0b78b-146">例如：</span><span class="sxs-lookup"><span data-stu-id="0b78b-146">For example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="0b78b-147">运行上述的 Azure Active Directory cmdlet，设置您的分类之后，运行[设置 UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet，如果您想要设置一组特定的分类。</span><span class="sxs-lookup"><span data-stu-id="0b78b-147">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="0b78b-148">或创建具有一个分类的新组。</span><span class="sxs-lookup"><span data-stu-id="0b78b-148">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="0b78b-149">检查出[与 Exchange Online Using PowerShell](https://go.microsoft.com/fwlink/?LinkID=402831)和[连接到 Exchange Online PowerShell 中](https://go.microsoft.com/fwlink/?LinkID=722415)使用 Exchange Online PowerShell 中的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="0b78b-149">Check out [Using PowerShell with Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) and [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="0b78b-150">一旦启用这些设置，则组的所有者将能够从在 Outlook 中的 Web 和 Outlook 中，在下拉菜单中选择一个分类并将其保存从**编辑**组页。</span><span class="sxs-lookup"><span data-stu-id="0b78b-150">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![选择 Office 365 组分类](./../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="0b78b-152">隐藏 GAL 中的 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="0b78b-152">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="0b78b-153"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="0b78b-153"></span></span>

<span data-ttu-id="0b78b-p108">您可以指定是否在全局地址列表 (GAL) 和您的组织中的其他列表中会出现一个 Office 365 组。例如，如果您不想要的地址列表中显示的法律部门组，可以停止在 GAL 中显示的组。运行 Set-Unified 组 commandlet 隐藏类似的地址列表的组：</span><span class="sxs-lookup"><span data-stu-id="0b78b-p108">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group commandlet to hide the group from address list like this:</span></span>
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="0b78b-157">只允许内部用户向 Office 365 组发送消息</span><span class="sxs-lookup"><span data-stu-id="0b78b-157">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="0b78b-158"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="0b78b-158"></span></span>

<span data-ttu-id="0b78b-p109">如果您不希望用户从其他组织到 Office 365 组发送电子邮件，您可以更改组的设置。它将只允许内部用户向组发送电子邮件。如果外部用户尝试向该组发送消息，它们将被拒绝。</span><span class="sxs-lookup"><span data-stu-id="0b78b-p109">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="0b78b-162">运行设置 UnifiedGroup commandlet 更新此设置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0b78b-162">Run the Set-UnifiedGroup commandlet to update this setting, like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="0b78b-163">向 Office 365 的组添加邮件提示</span><span class="sxs-lookup"><span data-stu-id="0b78b-163">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="0b78b-164"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="0b78b-164"></span></span>

<span data-ttu-id="0b78b-165">只要尝试向 Office 365 组发送电子邮件发件人，可向他显示邮件提示。</span><span class="sxs-lookup"><span data-stu-id="0b78b-165">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to him.</span></span>
  
<span data-ttu-id="0b78b-166">运行 Set-Unified 组 commandlet 向组添加邮件提示：</span><span class="sxs-lookup"><span data-stu-id="0b78b-166">Run the Set-Unified Group commandlet to add a mailTip to the group:</span></span>
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="0b78b-p110">邮件提示，以及您还可以设置 MailTipTranslations，从指定的其他语言邮件提示。假设您想要有西班牙语翻译，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0b78b-p110">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages fro the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="0b78b-169">更改 Office 365 组的显示名称</span><span class="sxs-lookup"><span data-stu-id="0b78b-169">Change Display name of the Office 365 group</span></span>
<span data-ttu-id="0b78b-170"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="0b78b-170"></span></span>

<span data-ttu-id="0b78b-p111">显示名称指定 Office 365 组的名称。Exchange 管理员中心或 o365 管理门户中，您可以看到此名称。您可以编辑组的显示名称，或通过运行设置 UnifiedGroup 命令分配现有 Office 365 组的显示名称：</span><span class="sxs-lookup"><span data-stu-id="0b78b-p111">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or o365 admin portal. You can edit the display name of the group or assign a display name to an exisiting Office 365 group by running Set-UnifiedGroup command:</span></span>
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a><span data-ttu-id="0b78b-174">管理 Office 365 组中的用户照片</span><span class="sxs-lookup"><span data-stu-id="0b78b-174">Manage user photos in Office 365 Groups</span></span>
<span data-ttu-id="0b78b-175"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="0b78b-175"></span></span>

<span data-ttu-id="0b78b-176">| |</span><span class="sxs-lookup"><span data-stu-id="0b78b-176"></span></span>
|<span data-ttu-id="0b78b-177">**Cmdlet 名称**</span><span class="sxs-lookup"><span data-stu-id="0b78b-177">**Cmdlet name**</span></span>|<span data-ttu-id="0b78b-178">**说明**</span><span class="sxs-lookup"><span data-stu-id="0b78b-178">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="0b78b-179">Get UserPhoto</span><span class="sxs-lookup"><span data-stu-id="0b78b-179">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="0b78b-p112">用于查看有关帐户相关联的用户照片的信息。用户照片存储在 Active Directory</span><span class="sxs-lookup"><span data-stu-id="0b78b-p112">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="0b78b-182">设置 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="0b78b-182">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="0b78b-p113">用于将用户照片关联的帐户。用户照片存储在 Active Directory</span><span class="sxs-lookup"><span data-stu-id="0b78b-p113">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="0b78b-185">删除 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="0b78b-185">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="0b78b-186">删除 Office 365 组中的照片</span><span class="sxs-lookup"><span data-stu-id="0b78b-186">Remove the photo for an Office 365 group</span></span>  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="0b78b-187">更改用于 Outlook 的 Office 365 组的默认设置为 Public 或 Private</span><span class="sxs-lookup"><span data-stu-id="0b78b-187">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="0b78b-188"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="0b78b-188"></span></span>

<span data-ttu-id="0b78b-p114">Office 365 在 Outlook 中创建组为私有默认情况下。如果您的组织的 Outlook 默认情况下 （或回专用） 创建公共为 Office 365 组，请使用以下 PowerShell cmdlet 的语法：</span><span class="sxs-lookup"><span data-stu-id="0b78b-p114">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups for Outlook to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="0b78b-191">若要设置为 Private:</span><span class="sxs-lookup"><span data-stu-id="0b78b-191">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="0b78b-192">若要验证设置：</span><span class="sxs-lookup"><span data-stu-id="0b78b-192">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="0b78b-193">若要了解详细信息，请参阅[Set-organizationconfig](https://go.microsoft.com/fwlink/?linkid=871816)和[Get-organizationconfig](https://go.microsoft.com/fwlink/?linkid=871817)。</span><span class="sxs-lookup"><span data-stu-id="0b78b-193">To learn more, see [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) and [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="0b78b-194">Office 365 组 cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b78b-194">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="0b78b-p115">以下 cmdlet 最近做可用到 Office 365 组。如果您不能使用这些，您的 Office 365 订阅尚未更新利用此功能您尚未。检查邮件中心和[Office 365 路线图](http://roadmap.office.com/en-us)。</span><span class="sxs-lookup"><span data-stu-id="0b78b-p115">The following cmdlets were recently made available to Office 365 Groups. If you aren't able to use these, your Office 365 subscription has not been updated with this functionality yet. Check your Message Center and the [Office 365 Roadmap](http://roadmap.office.com/en-us).</span></span>
  
<span data-ttu-id="0b78b-198">| |</span><span class="sxs-lookup"><span data-stu-id="0b78b-198"></span></span>
|<span data-ttu-id="0b78b-199">**Cmdlet 名称**</span><span class="sxs-lookup"><span data-stu-id="0b78b-199">**Cmdlet name**</span></span>|<span data-ttu-id="0b78b-200">**说明**</span><span class="sxs-lookup"><span data-stu-id="0b78b-200">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="0b78b-201">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="0b78b-201">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="0b78b-202">使用此 cmdlet，以查找现有 Office 365 组，并查看组对象的属性</span><span class="sxs-lookup"><span data-stu-id="0b78b-202">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="0b78b-203">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="0b78b-203">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="0b78b-204">更新特定的 Office 365 组的属性</span><span class="sxs-lookup"><span data-stu-id="0b78b-204">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="0b78b-205">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="0b78b-205">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="0b78b-p116">创建新的 Office 365 组。此 cmdlet 提供了一组最少的参数，设置扩展属性的值使用集 UnifiedGroup 创建新组后</span><span class="sxs-lookup"><span data-stu-id="0b78b-p116">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="0b78b-208">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="0b78b-208">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="0b78b-209">删除现有的 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="0b78b-209">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="0b78b-210">Get UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="0b78b-210">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="0b78b-211">检索为 Office 365 组的成员资格和所有者信息</span><span class="sxs-lookup"><span data-stu-id="0b78b-211">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="0b78b-212">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="0b78b-212">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="0b78b-213">添加十万或数千个用户或新的所有者，到现有 Office 365 组</span><span class="sxs-lookup"><span data-stu-id="0b78b-213">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="0b78b-214">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="0b78b-214">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="0b78b-215">删除现有的 Office 365 组的所有者和成员</span><span class="sxs-lookup"><span data-stu-id="0b78b-215">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
   
## <a name="for-more-information"></a><span data-ttu-id="0b78b-216">详细信息</span><span class="sxs-lookup"><span data-stu-id="0b78b-216">For more information</span></span>

- [<span data-ttu-id="0b78b-217">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b78b-217">Using PowerShell</span></span>](https://technet.microsoft.com/en-us/library/cc482986.aspx)
    
- [<span data-ttu-id="0b78b-218">向邮箱应用或删除 Outlook Web App 邮箱策略</span><span class="sxs-lookup"><span data-stu-id="0b78b-218">Apply or remove an Outlook Web App mailbox policy on a mailbox</span></span>](https://technet.microsoft.com/en-us/library/dd876884%28v=exchg.150%29.aspx)
    
- [<span data-ttu-id="0b78b-219">Office 365 组命名策略</span><span class="sxs-lookup"><span data-stu-id="0b78b-219">Office 365 Groups naming policy</span></span>](https://support.office.com/article/6ceca4d3-cad1-4532-9f0f-d469dfbbb552)
    

