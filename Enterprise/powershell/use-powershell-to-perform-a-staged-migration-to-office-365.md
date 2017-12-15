---
title: "使用 PowerShell 执行暂存迁移以迁移到 Office 365"
ms.author: sirkkuw
author: sirkkuw
manager: scotv
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: "摘要：了解如何使用 Windows PowerShell 执行到 Office 365 的暂存迁移。"
ms.openlocfilehash: 6c3ed6c0e37f7b99d3f26056dfe1b9d989388ff3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a><span data-ttu-id="90749-103">使用 PowerShell 执行暂存迁移以迁移到 Office 365</span><span class="sxs-lookup"><span data-stu-id="90749-103">Use PowerShell to perform a staged migration to Office 365</span></span>

 <span data-ttu-id="90749-104">**摘要：**了解如何使用 Windows PowerShell 执行分阶段的迁移到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="90749-104">**Summary:** Learn how to use Windows PowerShell to perform a staged migration to Office 365.</span></span>
  
<span data-ttu-id="90749-105">随着时间的推移，您可以使用暂存迁移将源电子邮件系统中用户邮箱的内容迁移到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="90749-105">You can migrate the contents of user mailboxes from a source email system to Office 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="90749-p101">本文将向您介绍涉及到使用 Exchange Online PowerShell 进行暂存电子邮件迁移的任务。[有关使用暂存迁移将电子邮件迁移到 Office 365 的注意事项](https://go.microsoft.com/fwlink/p/?LinkId=536487)主题向您提供了迁移过程的概述。当您了解本文的内容之后，则可以借此机会开始将一个电子邮件系统中的邮箱迁移到另一个电子邮件系统。</span><span class="sxs-lookup"><span data-stu-id="90749-p101">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="90749-p102">您还可以使用 Exchange 管理中心来执行暂存迁移。请参阅[使用暂存迁移将电子邮件迁移到 Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687)。</span><span class="sxs-lookup"><span data-stu-id="90749-p102">You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="90749-111">在开始之前，您需要知道什么？</span><span class="sxs-lookup"><span data-stu-id="90749-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="90749-p103">估计完成该任务的时间：2-5 分钟，用于创建迁移批处理。迁移批处理启动后，迁移的持续时间会有所不同，具体取决于批处理中邮箱的数量、每个邮箱的大小和可用网络容量。有关影响将邮箱迁移到 Office 365 所需时间的其他因素的信息，请参阅[迁移性能](https://go.microsoft.com/fwlink/p/?LinkId=275079)。</span><span class="sxs-lookup"><span data-stu-id="90749-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="90749-p104">您必须先获得权限，然后才能执行此过程。要查看您需要哪些权限，请参阅[收件人权限](https://go.microsoft.com/fwlink/p/?LinkId=534105)主题中的"迁移"条目。</span><span class="sxs-lookup"><span data-stu-id="90749-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="90749-p105">若要使用 Exchange Online PowerShell cmdlet，您需要登录并将 cmdlet 导入您的本地 Windows PowerShell 会话。有关说明，请参阅[使用远程 PowerShell 连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。</span><span class="sxs-lookup"><span data-stu-id="90749-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="90749-119">有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="90749-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="90749-120">迁移步骤</span><span class="sxs-lookup"><span data-stu-id="90749-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="90749-121">步骤 1：准备暂存迁移</span><span class="sxs-lookup"><span data-stu-id="90749-121">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="90749-122">在开始通过暂存迁移将邮箱迁移到 Office 365 之前，您必须对您的 Exchange 环境进行几处更改。</span><span class="sxs-lookup"><span data-stu-id="90749-122">Before you migrate mailboxes to Office 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="90749-p106">**在您的内部部署 Exchange Server 上配置 Outlook 无处不在** 电子邮件迁移服务使用 Outlook 无处不在（也称为 RPC over HTTP）连接到您的内部部署 Exchange Server。有关如何为 Exchange Server 2007 和 Exchange 2003 设置 Outlook 无处不在 设置的信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="90749-p106">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- [<span data-ttu-id="90749-125">Exchange 2007:如何启用 Outlook 无处不在</span><span class="sxs-lookup"><span data-stu-id="90749-125">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [<span data-ttu-id="90749-126">如何使用 Exchange 2003 配置 Outlook 无处不在</span><span class="sxs-lookup"><span data-stu-id="90749-126">How to configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> <span data-ttu-id="90749-p107">您必须在 Outlook 无处不在 配置中使用受信任的证书颁发机构 (CA) 颁发的证书。Outlook 无处不在 不能通过自签名的证书进行配置。有关详细信息，请参阅[如何为 Outlook 无处不在配置 SSL](https://go.microsoft.com/fwlink/?LinkID=80875)。</span><span class="sxs-lookup"><span data-stu-id="90749-p107">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="90749-130">**可选：确认您是否可以使用 Outlook 无处不在 连接到 Exchange 组织** 使用下列方法之一来测试您的连接设置。</span><span class="sxs-lookup"><span data-stu-id="90749-130">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="90749-131">使用公司网络外部的 Outlook 连接到您的内部部署 Exchange 邮箱。</span><span class="sxs-lookup"><span data-stu-id="90749-131">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="90749-p108">使用 [Microsoft Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) 测试连接设置。使用 Outlook 无处不在 (RPC over HTTP) 或 Outlook 自动发现测试。</span><span class="sxs-lookup"><span data-stu-id="90749-p108">Use the [Microsoft Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="90749-134">在 Exchange Online PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="90749-134">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="90749-p109">**设置权限** 您用于连接到内部部署 Exchange 组织的内部部署用户帐户（也称为迁移管理员）必须拥有必要的权限才能访问您要迁移到 Office 365 的内部部署邮箱。当您稍后在本过程（[步骤 3：创建迁移终结点](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint)）中通过创建迁移终结点来连接到您的电子邮件系统时，需要使用此用户帐户。</span><span class="sxs-lookup"><span data-stu-id="90749-p109">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="90749-137">要迁移邮箱，管理员必须拥有以下权限集之一：</span><span class="sxs-lookup"><span data-stu-id="90749-137">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="90749-138">内部部署组织中 Active Directory 中的 **Domain Admins** 组成员。</span><span class="sxs-lookup"><span data-stu-id="90749-138">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="90749-139">或</span><span class="sxs-lookup"><span data-stu-id="90749-139">or</span></span>
    
- <span data-ttu-id="90749-140">分配了对每个内部部署邮箱的 **FullAccess** 权限以及可修改内部部署用户帐户上的 **TargetAddress** 属性的 **WriteProperty** 权限。</span><span class="sxs-lookup"><span data-stu-id="90749-140">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="90749-141">或</span><span class="sxs-lookup"><span data-stu-id="90749-141">or</span></span>
    
- <span data-ttu-id="90749-142">分配了对存储用户邮箱的内部部署邮箱数据库上的 **Receive As** 权限以及可修改内部部署用户帐户上的 **TargetAddress** 属性的 **WriteProperty** 权限。</span><span class="sxs-lookup"><span data-stu-id="90749-142">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="90749-143">有关如何设置这些权限的说明，请参阅[分配权限以将邮箱迁移到 Office 365](https://go.microsoft.com/fwlink/?LinkId=521656)。</span><span class="sxs-lookup"><span data-stu-id="90749-143">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="90749-p110">**禁用统一消息 (UM)** 如果您要迁移的内部部署邮箱上开启了 UM，请先将其关闭，然后再执行迁移。迁移完成以后，打开邮箱的 UM。有关具体的操作方法步骤，请参阅[禁用统一消息](https://go.microsoft.com/fwlink/?LinkId=521891)。</span><span class="sxs-lookup"><span data-stu-id="90749-p110">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="90749-p111">**使用目录同步在 Office 365 中新建用户。**您可以使用目录同步在您的 Office 365 组织中创建所有内部部署用户。</span><span class="sxs-lookup"><span data-stu-id="90749-p111">**Use directory synchronization to create new users in Office 365.** You use directory synchronization to create all the on-premises users in your Office 365 organization.</span></span>
  
<span data-ttu-id="90749-p112">创建用户以后，您需要对他们授予许可。您可以在创建用户之后的 30 天内添加许可证。有关添加许可证的步骤，请参阅[步骤 8：完成迁移后任务](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration)。</span><span class="sxs-lookup"><span data-stu-id="90749-p112">You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="90749-p113">您可以使用 Microsoft Azure Active Directory 同步工具或 Microsoft Azure Active Directory 同步服务（AAD 同步）来同步并在 Office 365 中创建您的内部部署用户。当邮箱被迁移到 Office 365 之后，您可以在内部部署组织中管理用户帐户，而且它们会与 Office 365 组织同步。有关更多信息，请参阅[目录集成](https://go.microsoft.com/fwlink/?LinkId=521788)。</span><span class="sxs-lookup"><span data-stu-id="90749-p113">You can use either the Microsoft Azure Active Directory Synchronization Tool or the Microsoft Azure Active Directory Sync Services (AAD Sync) to synchronize and create your on-premises users in Office 365. After mailboxes are migrated to Office 365, you manage user accounts in your on-premises organization, and they're synchronized with your Office 365 organization. For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="90749-155">步骤 2：为暂存迁移批处理创建 CSV 文件</span><span class="sxs-lookup"><span data-stu-id="90749-155">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="90749-p114">确定您要将其内部部署邮箱迁移到 Office 365 的用户之后，您可以使用逗号分隔值 (CSV) 文件来创建迁移批处理。Office 365 用于运行迁移的 CSV 文件中的每一行都包含有关内部部署邮箱的信息。</span><span class="sxs-lookup"><span data-stu-id="90749-p114">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="90749-p115">对于使用暂存迁移来迁移到 Office 365 的邮箱数没有限制。迁移批处理的 CSV 文件最多可包含 2,000 行。若要迁移 2000 个以上邮箱，请创建额外的 CSV 文件并使用每个文件来创建新的迁移批处理。</span><span class="sxs-lookup"><span data-stu-id="90749-p115">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="90749-161">**支持的属性**</span><span class="sxs-lookup"><span data-stu-id="90749-161">**Supported attributes**</span></span>
  
<span data-ttu-id="90749-p116">暂存迁移的 CSV 文件支持下列三个属性。CSV 文件中的每一行对应于一个邮箱并且必须包含属性的相应值。</span><span class="sxs-lookup"><span data-stu-id="90749-p116">The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="90749-164">**属性**</span><span class="sxs-lookup"><span data-stu-id="90749-164">**Attribute**</span></span>|<span data-ttu-id="90749-165">**描述**</span><span class="sxs-lookup"><span data-stu-id="90749-165">**Description**</span></span>|<span data-ttu-id="90749-166">**是否必需？**</span><span class="sxs-lookup"><span data-stu-id="90749-166">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="90749-167">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="90749-167">EmailAddress</span></span>  <br/> |<span data-ttu-id="90749-168">为内部部署邮箱指定一个主要的 SMTP 电子邮件地址，例如，pilarp@contoso.com。</span><span class="sxs-lookup"><span data-stu-id="90749-168">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="90749-p117">为内部部署邮箱使用该主要的 SMTP 地址，而非 Office 365 中的用户 ID。例如，如果将内部部署域命名为 contoso.com，但是将 Office 365 电子邮件域命名为 service.contoso.com，则您应该为 CSV 文件中的电子邮件地址使用 contoso.com 域名。</span><span class="sxs-lookup"><span data-stu-id="90749-p117">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365. For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="90749-171">必需</span><span class="sxs-lookup"><span data-stu-id="90749-171">Required</span></span>  <br/> |
|<span data-ttu-id="90749-172">Password</span><span class="sxs-lookup"><span data-stu-id="90749-172">Password</span></span>  <br/> |<span data-ttu-id="90749-p118">需要为新的 Office 365 邮箱设置的密码。适用于 Office 365 组织的任何密码限制也适用于该 CSV 文件中包括的密码。</span><span class="sxs-lookup"><span data-stu-id="90749-p118">The password to be set for the new Office 365 mailbox. Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="90749-175">可选</span><span class="sxs-lookup"><span data-stu-id="90749-175">Optional</span></span>  <br/> |
|<span data-ttu-id="90749-176">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="90749-176">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="90749-p119">指定用户在首次登录自己的新 Office 365 邮箱时是否必须更改密码。对此参数的值使用 **True** 或 **False** 。</span><span class="sxs-lookup"><span data-stu-id="90749-p119">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox. Use **True** or **False** for the value of this parameter. </span></span><br/> <span data-ttu-id="90749-179">> [!NOTE]> 如果您已通过部署 Active Directory 联合身份验证服务 (AD FS) 实现单一登录 (SSO) 解决方案或更高版本在您的内部组织，则必须使用**False** **ForceChangePassword**属性的值。</span><span class="sxs-lookup"><span data-stu-id="90749-179">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="90749-180">可选</span><span class="sxs-lookup"><span data-stu-id="90749-180">Optional</span></span>  <br/> |
   
 <span data-ttu-id="90749-181">**CSV 文件格式**</span><span class="sxs-lookup"><span data-stu-id="90749-181">**CSV file format**</span></span>
  
<span data-ttu-id="90749-p120">以下是 CSV 文件格式的一个示例。在此示例中，会将三个内部部署邮箱迁移到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="90749-p120">Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Office 365.</span></span>
  
<span data-ttu-id="90749-p121">CSV 文件的第一行（即标题行）列出了在后续行中指定的属性（或字段）的名称。每个属性名称都用逗号分隔开。</span><span class="sxs-lookup"><span data-stu-id="90749-p121">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.</span></span>
  
```
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="90749-p122">标题行下面的每行都表示一个用户，并提供将用于迁移该用户邮箱的信息。每行中属性值的顺序必须与标题行中属性名的顺序相同。</span><span class="sxs-lookup"><span data-stu-id="90749-p122">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="90749-p123">使用任何文本编辑器或 Excel 等应用程序创建 CSV 文件。将该文件另存为 .csv 或 .txt 文件。</span><span class="sxs-lookup"><span data-stu-id="90749-p123">Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="90749-p124">如果 CSV 文件包含非 ASCII 字符或特殊字符，请使用 UTF-8 或其他 Unicode 编码保存 CSV 文件。根据应用程序的不同，如果计算机的系统区域设置与 CSV 文件中使用的语言相匹配，则使用 UTF-8 或其他 Unicode 编码保存 CSV 文件可能会更容易。</span><span class="sxs-lookup"><span data-stu-id="90749-p124">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="90749-192">步骤 3：创建迁移终结点</span><span class="sxs-lookup"><span data-stu-id="90749-192">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="90749-193"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="90749-193"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="90749-p125">要成功迁移电子邮件，Office 365 需要与源电子邮件系统连接和通信。为此，Office 365 可使用迁移终结点。要使用 PowerShell 创建适用于暂存迁移的 Outlook 无处不在迁移终结点，首先[连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。</span><span class="sxs-lookup"><span data-stu-id="90749-p125">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="90749-197">有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="90749-197">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="90749-198">要在 Exchange Online PowerShell 中创建名为"StagedEndpoint"的 Outlook 无处不在迁移终结点，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="90749-198">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```
$Credentials = Get-Credential
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="90749-199">有关 **New-MigrationEndpoint** cmdlet 的详细信息，请参阅[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)。</span><span class="sxs-lookup"><span data-stu-id="90749-199">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="90749-p126">可以使用 **New-MigrationEndpoint** cmdlet 指定服务要通过 **-TargetDatabase** 选项使用的数据库。在其他情况下，系统会从管理邮箱所在的 Active Directory 联合身份验证服务 (AD FS) 2.0 站点中随机分配数据库。</span><span class="sxs-lookup"><span data-stu-id="90749-p126">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="90749-202">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="90749-202">Verify it worked</span></span>

<span data-ttu-id="90749-203">在 Exchange Online PowerShell 中，运行以下命令来显示有关"StagedEndpoint"迁移终结点的信息：</span><span class="sxs-lookup"><span data-stu-id="90749-203">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="90749-204">步骤 4：创建并启动暂存迁移批处理</span><span class="sxs-lookup"><span data-stu-id="90749-204">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="90749-205"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="90749-205"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="90749-p127">您可以在 Exchange Online PowerShell 中使用 **New-MigrationBatch** cmdlet 为直接转换迁移创建迁移批处理。您可以通过包括 _AutoStart_ 参数来创建迁移批处理并自动启动。或者，您可以通过使用 **Start-MigrationBatch** cmdlet 创建迁移批处理，然后手动启动。此示例创建名为"StagedBatch1"的迁移批处理并使用之前步骤中创建的迁移终结点。</span><span class="sxs-lookup"><span data-stu-id="90749-p127">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="90749-p128">此示例还会创建名为"StagedBatch1"的迁移批处理并使用之前步骤中创建的迁移终结点。由于未包括  _AutoStart_ 参数，因此必须在迁移主控板中手动启动迁移批处理或者通过使用 **Start-MigrationBatch** cmdlet 手动启动迁移批处理。如前所述，一次只能存在一个直接转换迁移批处理。</span><span class="sxs-lookup"><span data-stu-id="90749-p128">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="90749-213">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="90749-213">Verify it worked</span></span>

<span data-ttu-id="90749-214">在 Exchange Online PowerShell 中运行以下命令来显示有关"StagedBatch1"的信息：</span><span class="sxs-lookup"><span data-stu-id="90749-214">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="90749-215">您还可以通过运行以下命令，验证该批处理是否已启动：</span><span class="sxs-lookup"><span data-stu-id="90749-215">You can also verify that the batch has started by running the following command:</span></span>
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="90749-216">有关 **Get-MigrationBatch** cmdlet 的详细信息，请参阅[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)。</span><span class="sxs-lookup"><span data-stu-id="90749-216">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="90749-217">步骤 5：将内部部署邮箱转换为启用邮件的用户</span><span class="sxs-lookup"><span data-stu-id="90749-217">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="90749-218"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="90749-218"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="90749-p129">成功迁移一批邮箱以后，您需要某种方法使用户可以访问他们的邮件。已迁移邮箱的用户现在既有一个内部部署邮箱，又有一个 Office 365 邮箱。在 Office 365 中有邮箱的用户将停止在内部部署邮箱中接收新邮件。</span><span class="sxs-lookup"><span data-stu-id="90749-p129">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365. Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="90749-p130">由于您尚未完成迁移，因此目前无法将所有用户定向到 Office 365 接收其电子邮件。那么，可以为这些拥有两个邮箱的用户做些什么呢？您可以做的是更改您已迁移到邮件启用的用户的内部部署邮箱。当您从一个邮箱更改为邮件启用的用户时，可以将该用户定向到其电子邮件的 Office 365，而非内部部署邮箱。</span><span class="sxs-lookup"><span data-stu-id="90749-p130">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="90749-p131">将内部部署邮箱转换为启用邮件的用户的另一个重要原因是通过将代理地址复制到启用邮件的用户，来保留 Office 365 邮箱中的代理地址。这使您可以使用 Active Directory 管理来自内部部署组织的基于云的用户。此外，如果您决定在所有邮箱都迁移到 Office 365 之后停止使用内部部署 Exchange Server 组织，则复制到启用邮件的用户的代理地址仍会保留在内部部署 Active Directory 中。</span><span class="sxs-lookup"><span data-stu-id="90749-p131">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
  
<span data-ttu-id="90749-229">若要获取详细信息并下载为将邮箱转换为已启用邮件的用户而可以运行的脚本，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="90749-229">For more information, and to download scripts that you can run to convert mailboxes to mail-enabled users, see the following:</span></span>
  
- [<span data-ttu-id="90749-230">将 Exchange 2007 邮箱转换为启用邮件的用户</span><span class="sxs-lookup"><span data-stu-id="90749-230">Convert Exchange 2007 mailboxes to mail-enabled users</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=233648)
    
- [<span data-ttu-id="90749-231">将 Exchange 2003 邮箱转换为启用邮件的用户</span><span class="sxs-lookup"><span data-stu-id="90749-231">Convert Exchange 2003 mailboxes to mail-enabled users</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=233647)
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="90749-232">步骤 6：删除暂存迁移批处理</span><span class="sxs-lookup"><span data-stu-id="90749-232">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="90749-233"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="90749-233"><a name="BK_Endpoint"> </a></span></span>

 <span data-ttu-id="90749-p132">在迁移批处理中的所有邮箱都已成功迁移并且将批处理中的内部部署邮箱转换为启用邮件的用户之后，可以准备删除暂存迁移批处理。确保验证邮件正在转发到迁移批处理中的 Office 365 邮箱。当您删除暂存迁移批处理时，迁移服务将清除任何与迁移批处理相关的记录，同时删除迁移批处理。</span><span class="sxs-lookup"><span data-stu-id="90749-p132">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch. Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch. When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="90749-237">要在 Exchange Online PowerShell 中删除"StagedBatch1"迁移批处理，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="90749-237">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="90749-238">有关 **Remove-MigrationBatch** cmdlet 的详细信息，请参阅[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)。</span><span class="sxs-lookup"><span data-stu-id="90749-238">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="90749-239">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="90749-239">Verify it worked</span></span>

<span data-ttu-id="90749-240">在 Exchange Online PowerShell 中运行以下命令来显示有关"IMAPBatch1"的信息：</span><span class="sxs-lookup"><span data-stu-id="90749-240">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="90749-241">此命令会返回状态为"正在删除"的迁移批处理或返回错误消息，指出未找到该迁移批处理，验证该批处理已删除。</span><span class="sxs-lookup"><span data-stu-id="90749-241">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="90749-242">有关 **Get-MigrationBatch** cmdlet 的详细信息，请参阅[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)。</span><span class="sxs-lookup"><span data-stu-id="90749-242">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-office-365-users"></a><span data-ttu-id="90749-243">步骤 7：将许可证分配给 Office 365 用户</span><span class="sxs-lookup"><span data-stu-id="90749-243">Step7: Assign licenses to Office 365 users</span></span>
<span data-ttu-id="90749-244"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="90749-244"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="90749-p133">通过分配许可证，激活迁移帐户的 Office 365 用户帐户。如果您不分配许可证，则在宽限期（30 天）结束后将禁用该邮箱。若要在 Office 365 管理中心 中分配许可证，请参阅[为 Office 365 商业版分配或取消分配许可证](https://go.microsoft.com/fwlink/?LinkId=536681)。</span><span class="sxs-lookup"><span data-stu-id="90749-p133">Activate Office 365 user accounts for the migrated accounts by assigning licenses. If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends. To assign a license in the Office 365 admin center, see [Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="90749-248">步骤 8：完成迁移后任务</span><span class="sxs-lookup"><span data-stu-id="90749-248">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="90749-249"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="90749-249"><a name="BK_Postmigration"> </a></span></span>

- <span data-ttu-id="90749-p134">**创建自动发现 DNS 记录，以便用户可以轻松地访问他们的邮箱。**所有内部部署邮箱都迁移到 Office 365 以后，您可以为您的 Office 365 组织配置自动发现 DNS 记录，使用户可以轻松地使用 Outlook 和移动客户端连接到他们的新 Office 365 邮箱。此新自动发现 DNS 记录必须使用对 Office 365 组织使用的相同命名空间。例如，如果您基于云的命名空间是 cloud.contoso.com，则您需要创建的自动发现 DNS 记录是 autodiscover.cloud.contoso.com。</span><span class="sxs-lookup"><span data-stu-id="90749-p134">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="90749-p135">Office 365 使用 CNAME 记录为 Outlook 和移动客户端实现自动发现服务。自动发现 CNAME 记录必须包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="90749-p135">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="90749-256">**别名：**autodiscover</span><span class="sxs-lookup"><span data-stu-id="90749-256">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="90749-257">**目标：**autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="90749-257">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="90749-258">有关更多信息，请参阅[管理 DNS 记录时为 Office 365 创建 DNS 记录](https://go.microsoft.com/fwlink/p/?LinkId=535028)。</span><span class="sxs-lookup"><span data-stu-id="90749-258">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="90749-p136">**停止使用内部部署 Exchange 服务器。**当您验证所有电子邮件都可以直接被路由到 Office 365 邮箱，并且您不再需要维护内部部署电子邮件组织或不用计划实施 SSO 解决方案以后，您可以从服务器中卸载 Exchange 并删除内部部署 Exchange 组织。</span><span class="sxs-lookup"><span data-stu-id="90749-p136">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="90749-261">有关详细信息，请参阅下列内容：</span><span class="sxs-lookup"><span data-stu-id="90749-261">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="90749-262">修改或删除 Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="90749-262">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="90749-263">如何删除 Exchange 2007 组织</span><span class="sxs-lookup"><span data-stu-id="90749-263">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="90749-264">如何卸载 Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="90749-264">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

