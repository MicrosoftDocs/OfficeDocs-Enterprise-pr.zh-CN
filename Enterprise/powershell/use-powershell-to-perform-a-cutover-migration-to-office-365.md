---
title: 使用 PowerShell 执行直接转换迁移以迁移到 Office 365
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: 摘要：了解如何使用 Windows PowerShell 执行到 Office 365 的直接转换迁移。
ms.openlocfilehash: 0f284e2dcccd3d7fc6958922ac4e87da4fc086ec
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574076"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a><span data-ttu-id="e23e2-103">使用 PowerShell 执行直接转换迁移以迁移到 Office 365</span><span class="sxs-lookup"><span data-stu-id="e23e2-103">Use PowerShell to perform a cutover migration to Office 365</span></span>

 <span data-ttu-id="e23e2-104">**摘要：** 了解如何使用 Windows PowerShell 执行直接转换迁移，以迁移到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="e23e2-104">**Summary:** Learn how to use Windows PowerShell to perform a cutover migration to Office 365.</span></span>
  
<span data-ttu-id="e23e2-p101">通过直接转换迁移，您可以一次性将源电子邮件系统中用户邮箱的内容迁移到 Office 365。本文将向您介绍如何通过 Exchange Online PowerShell 执行电子邮件直接转换迁移的任务。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p101">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration. This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="e23e2-p102">通过查看[有关直接转换电子邮件迁移到 Office 365 您需要了解的信息](https://go.microsoft.com/fwlink/p/?LinkId=536688)主题，您可以获得迁移过程的概述。当您了解本文的内容之后，则可以借此机会开始将一个电子邮件系统中的邮箱迁移到另一个电子邮件系统。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p102">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e23e2-p103">您还可以使用 Exchange 管理中心来执行直接转换迁移。请参阅[使用直接转换迁移将电子邮件迁移到 Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689)。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p103">You can also use the Exchange admin center to perform a cutover migration. See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="e23e2-111">在开始之前，您需要知道什么？</span><span class="sxs-lookup"><span data-stu-id="e23e2-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="e23e2-p104">估计完成该任务的时间：2-5 分钟，用于创建迁移批处理。迁移批处理启动后，迁移的持续时间会有所不同，具体取决于批处理中邮箱的数量、每个邮箱的大小和可用网络容量。有关影响将邮箱迁移到 Office 365 所需时间的其他因素的信息，请参阅[迁移性能](https://go.microsoft.com/fwlink/p/?LinkId=275079)。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p104">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="e23e2-p105">您必须先获得权限，然后才能执行此过程。要查看您需要哪些权限，请参阅[收件人权限](https://go.microsoft.com/fwlink/p/?LinkId=534105)主题的一个表中的"迁移"条目。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p105">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="e23e2-p106">若要使用 Exchange Online PowerShell cmdlet，您需要登录并将 cmdlet 导入您的本地 Windows PowerShell 会话。有关说明，请参阅[使用远程 PowerShell 连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p106">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="e23e2-119">有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="e23e2-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="e23e2-120">迁移步骤</span><span class="sxs-lookup"><span data-stu-id="e23e2-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="e23e2-121">步骤 1：准备直接转换迁移</span><span class="sxs-lookup"><span data-stu-id="e23e2-121">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="e23e2-122"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="e23e2-122"></span></span>

- <span data-ttu-id="e23e2-p107">**将内部部署 Exchange 组织添加为 Office 365 组织的接受域** 迁移服务使用内部部署邮箱的 SMTP 地址为新的 Office 365 邮箱创建 Microsoft Online Services 用户 ID 和电子邮件地址。如果 Exchange 域不是 Office 365 组织的接受域或主域，则迁移将失败。有关更多信息，请参阅[在 Office 365 中验证您的域](https://go.microsoft.com/fwlink/p/?LinkId=534110)。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p107">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.** The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes. Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="e23e2-p108">**在内部部署 Exchange 服务器上配置 Outlook 无处不在。** 电子邮件迁移服务使用 RPC over HTTP 或 Outlook 无处不在连接到内部部署 Exchange 服务器。有关如何设置 Outlook 无处不在 for Exchange 2010、Exchange 2007 和 Exchange 2003 的信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="e23e2-p108">**Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>
    
  - [<span data-ttu-id="e23e2-130">Exchange 2010:启用 Outlook 无处不在</span><span class="sxs-lookup"><span data-stu-id="e23e2-130">Exchange 2010: Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [<span data-ttu-id="e23e2-131">Exchange 2007:如何启用 Outlook 无处不在</span><span class="sxs-lookup"><span data-stu-id="e23e2-131">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [<span data-ttu-id="e23e2-132">Exchange 2003:RPC over HTTP 的部署方案</span><span class="sxs-lookup"><span data-stu-id="e23e2-132">Exchange 2003: Deployment Scenarios for RPC over HTTP</span></span>](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [<span data-ttu-id="e23e2-133">如何使用 Exchange 2003 配置 Outlook 无处不在</span><span class="sxs-lookup"><span data-stu-id="e23e2-133">How to Configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > <span data-ttu-id="e23e2-p109">必须使用受信任的证书颁发机构 (CA) 颁发的证书配置 Outlook 无处不在配置。不能使用自签名证书配置它。有关详细信息，请参阅[如何为 Outlook 无处不在配置 SSL](https://go.microsoft.com/fwlink/?LinkID=80875)。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p109">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
- <span data-ttu-id="e23e2-p110">**确认是否可以使用 Outlook 无处不在连接到 Exchange 组织。** 尝试以下这些方法之一来测试连接设置：</span><span class="sxs-lookup"><span data-stu-id="e23e2-p110">**Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:</span></span>
    
  - <span data-ttu-id="e23e2-139">使用 Microsoft Outlook 从企业网络外部连接到内部部署 Exchange 邮箱。</span><span class="sxs-lookup"><span data-stu-id="e23e2-139">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
  - <span data-ttu-id="e23e2-p111">使用 Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) 测试连接设置。使用 Outlook 无处不在 (RPC over HTTP) 或 Outlook 自动发现测试。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p111">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
  - <span data-ttu-id="e23e2-142">在 Exchange Online PowerShell 中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="e23e2-142">Run the following commands in Exchange Online PowerShell.</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="e23e2-143">**为内部部署用户帐户分配访问 Exchange 组织中的邮箱所需的权限。**</span><span class="sxs-lookup"><span data-stu-id="e23e2-143">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.**</span></span> <span data-ttu-id="e23e2-144">用于连接到内部部署 Exchange 组织的本地用户帐户 (也称为迁移管理员) 必须具有访问要迁移到 Office 365 的本地邮箱的必要权限。。</span><span class="sxs-lookup"><span data-stu-id="e23e2-144">The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span></span> <span data-ttu-id="e23e2-145">该用户帐户用于创建内部部署组织的迁移终结点。</span><span class="sxs-lookup"><span data-stu-id="e23e2-145">This user account is used to create a migration endpoint to your on-premises organization.</span></span>
    
    <span data-ttu-id="e23e2-p113">以下列表显示了使用直接转换迁移迁移邮箱所需的管理权限。有三个可能的选项。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p113">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.</span></span>
    
  - <span data-ttu-id="e23e2-148">迁移管理员必须是内部部署组织的 Active Directory 中的 **Domain Admins** 组成员。</span><span class="sxs-lookup"><span data-stu-id="e23e2-148">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="e23e2-149">或者</span><span class="sxs-lookup"><span data-stu-id="e23e2-149">Or</span></span>
    
  - <span data-ttu-id="e23e2-150">必须为迁移管理员分配对每个内部部署邮箱的 **FullAccess** 权限。</span><span class="sxs-lookup"><span data-stu-id="e23e2-150">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>
    
    <span data-ttu-id="e23e2-151">或</span><span class="sxs-lookup"><span data-stu-id="e23e2-151">Or</span></span>
    
  - <span data-ttu-id="e23e2-152">必须为迁移管理员分配对存储用户邮箱的内部部署邮箱数据库的 **代理接收**权限。</span><span class="sxs-lookup"><span data-stu-id="e23e2-152">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>
    
- <span data-ttu-id="e23e2-p114">**禁用统一消息。** 如果为要迁移的内部部署邮箱启用了统一消息 (UM)，则您必须先禁用这些邮箱上的 UM，然后再进行迁移。之后，您可以在完成迁移后为邮箱启用 UM。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p114">**Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.</span></span>
    
- <span data-ttu-id="e23e2-p115">**安全组和代理** 电子邮件迁移服务无法检测本地 Active Directory 组是否为安全组，因此它无法在 Office 365 中将任何已迁移组设置为安全组。如果您希望在 Office 365 租户中拥有安全组，必须首先在 Office 365 租户中设置一个空的启用了邮件的安全组，然后再开始直接转换迁移。此外，此迁移方法仅移动邮箱、邮箱用户、邮箱联系人和启用了邮件的组。如果已将任何其他 Active Directory 对象（如未迁移到 Office 365 的用户）作为管理员或代理分配给要迁移的对象，则必须在迁移之前将其从对象中删除。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p115">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365. If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration. Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups. If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>
    
### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="e23e2-160">步骤 2：创建迁移终结点</span><span class="sxs-lookup"><span data-stu-id="e23e2-160">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="e23e2-161"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="e23e2-161"></span></span>

<span data-ttu-id="e23e2-p116">要成功迁移电子邮件，Office 365 需要与源电子邮件系统连接和通信。为此，Office 365 可使用迁移终结点。要创建适用于直接转换迁移的 Outlook 无处不在迁移终结点，首先[连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p116">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="e23e2-165">有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="e23e2-165">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="e23e2-166">在 Exchange Online PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="e23e2-166">Run the following commands in Exchange Online PowerShell:</span></span>
  
```
$Credentials = Get-Credential
```

<span data-ttu-id="e23e2-167">该示例使用 [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet 获取并测试对内部部署 Exchange 服务器的连接设置，然后使用这些连接设置来创建名为"CutoverEndpoint"的迁移终结点。</span><span class="sxs-lookup"><span data-stu-id="e23e2-167">The example uses the [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="e23e2-p117">可以使用 **New-MigrationEndpoint** cmdlet 指定服务要通过 **-TargetDatabase** 选项使用的数据库。在其他情况下，系统会从管理邮箱所在的 Active Directory 联合身份验证服务 (AD FS) 2.0 站点中随机分配数据库。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p117">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="e23e2-170">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="e23e2-170">Verify it worked</span></span>

<span data-ttu-id="e23e2-171">在 Exchange Online PowerShell 中，运行以下命令来显示有关“CutoverEndpoint”迁移终结点的信息：</span><span class="sxs-lookup"><span data-stu-id="e23e2-171">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="e23e2-172">步骤 3：创建直接转换迁移批处理</span><span class="sxs-lookup"><span data-stu-id="e23e2-172">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="e23e2-173"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="e23e2-173"></span></span>

<span data-ttu-id="e23e2-p118">您可以在 Exchange Online PowerShell 中使用 **New-MigrationBatch** cmdlet 为直接转换迁移创建迁移批处理。您可以通过包括 _AutoStart_ 参数来创建迁移批处理并自动启动。或者，您可以通过使用 **Start-MigrationBatch** cmdlet 创建迁移批处理，然后手动启动。此示例创建名为"CutoverBatch"的迁移批处理并使用之前步骤中创建的迁移终结点。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p118">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="e23e2-p119">此示例还会创建名为"CutoverBatch"的迁移批处理并使用之前步骤中创建的迁移终结点。由于未包括  _AutoStart_ 参数，因此必须在迁移主控板中手动启动迁移批处理或者通过使用 **Start-MigrationBatch** cmdlet 手动启动迁移批处理。如前所述，一次只能存在一个直接转换迁移批处理。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p119">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="e23e2-181">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="e23e2-181">Verify it worked</span></span>

<span data-ttu-id="e23e2-182">要验证您是否已成功为直接转换迁移创建了迁移批处理，请在 Exchange Online PowerShell 中运行以下命令来显示有关新迁移批处理的信息：</span><span class="sxs-lookup"><span data-stu-id="e23e2-182">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="e23e2-183">步骤 4：启动直接转换迁移批处理</span><span class="sxs-lookup"><span data-stu-id="e23e2-183">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="e23e2-184"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="e23e2-184"></span></span>

<span data-ttu-id="e23e2-p120">要在 Exchange Online PowerShell 中启动迁移批处理，请运行以下命令。这将创建名为“CutoverBatch”的迁移批处理。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p120">To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".</span></span>
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="e23e2-187">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="e23e2-187">Verify it worked</span></span>

<span data-ttu-id="e23e2-p121">如果迁移批处理已成功启动，其在迁移主控板中的状态指定为“正在同步”。要验证您是否已通过 Exchange Online PowerShell 成功启动迁移批处理，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="e23e2-p121">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="e23e2-190">步骤 5：将您的电子邮件路由到 Office 365</span><span class="sxs-lookup"><span data-stu-id="e23e2-190">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="e23e2-191"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="e23e2-191"></span></span>

<span data-ttu-id="e23e2-p122">电子邮件系统使用名为 MX 记录的 DNS 记录找出传递电子邮件的位置。在电子邮件迁移过程中，您的 MX 记录会指向您的源电子邮件系统。现在电子邮件迁移到 Office 365 已完成，可以在 Office 365 中指向您的 MX 记录。这可以帮助您确保该电子邮件已传递到您的 Office 365 邮箱。通过移动 MX 记录，您还可以在准备就绪的时候关闭旧的电子邮件系统。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p122">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also you turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="e23e2-p123">对于很多 DNS 提供商而言，[更改您的 MX 记录](https://go.microsoft.com/fwlink/p/?LinkId=279163)需要遵循特定的说明。如果您的 DNS 提供商不包括在内或您要获取统一指导，我们也会提供 [MX 记录的统一说明](https://go.microsoft.com/fwlink/?LinkId=397449)。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p123">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="e23e2-p124">您客户和合作伙伴的电子邮件系统可能需要 72 小时才能识别更改后的 MX 记录。请等待至少 72 个小时，然后才能继续执行下一项任务： [步骤 6：删除直接转换迁移批处理](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span><span class="sxs-lookup"><span data-stu-id="e23e2-p124">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span></span> 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="e23e2-201">步骤 6：删除直接转换迁移批处理</span><span class="sxs-lookup"><span data-stu-id="e23e2-201">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="e23e2-202"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="e23e2-202"></span></span>

<span data-ttu-id="e23e2-p125">更改 MX 记录并验证所有电子邮件已路由到 Office 365 邮箱以后，通知用户他们的邮件已进入到 Office 365。此后，您可以删除直接转换迁移批处理。在删除迁移批处理之前验证以下内容。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p125">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the cutover migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="e23e2-p126">所有用户正在使用 Office 365 邮箱。删除该批处理后，发送到内部部署 Exchange Server 中邮箱的邮件将不会复制到相应的 Office 365 邮箱。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p126">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="e23e2-p127">当邮件开始直接发送到 Office 365 邮箱以后，这些邮箱至少会同步一次。为此，确保迁移批处理的"上次同步时间"框中的值是最近时间，而不是邮件开始直接路由到 Office 365 邮箱的时间。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p127">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="e23e2-210">要在 Exchange Online PowerShell 中删除“CutoverBatch”迁移批处理，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="e23e2-210">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="e23e2-211">第 7 部分：分配用户许可证</span><span class="sxs-lookup"><span data-stu-id="e23e2-211">Section 7: Assign user licenses</span></span>
<span data-ttu-id="e23e2-212"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="e23e2-212"></span></span>

 <span data-ttu-id="e23e2-213">**通过分配许可证，激活迁移后帐户的 Office 365 用户帐户。**</span><span class="sxs-lookup"><span data-stu-id="e23e2-213">**Activate Office 365 user accounts for the migrated accounts by assigning licenses.**</span></span> <span data-ttu-id="e23e2-214">如果不分配许可证，则当宽限期（30 天）结束时，邮箱将处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="e23e2-214">If you don't assign a license, the mailbox is disabled when the grace period ends (30 days).</span></span> <span data-ttu-id="e23e2-215">若要在 Microsoft 365 管理中心中分配许可证, 请参阅为[Office 365 for business 分配或取消分配许可证](https://go.microsoft.com/fwlink/?LinkId=536681)。</span><span class="sxs-lookup"><span data-stu-id="e23e2-215">To assign a license in the Microsoft 365 admin center, see[Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="e23e2-216">步骤 8：完成迁移后任务</span><span class="sxs-lookup"><span data-stu-id="e23e2-216">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="e23e2-217"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="e23e2-217"></span></span>

- <span data-ttu-id="e23e2-p129">**创建自动发现 DNS 记录，以便用户可以轻松地访问他们的邮箱。** 所有内部部署邮箱都迁移到 Office 365 以后，您可以为您的 Office 365 组织配置自动发现 DNS 记录，使用户可以轻松地使用 Outlook 和移动客户端连接到他们的新 Office 365 邮箱。此新自动发现 DNS 记录必须使用对 Office 365 组织使用的相同命名空间。例如，如果您基于云的命名空间是 cloud.contoso.com，则您需要创建的自动发现 DNS 记录是 autodiscover.cloud.contoso.com。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p129">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="e23e2-222">如果您保留 Exchange Server，则还应确保在迁移后自动发现 DNS CNAME 记录必须在内部和外部 DNS 中指向 Office 365，以便 Outlook 客户端能够连接到正确的邮箱。</span><span class="sxs-lookup"><span data-stu-id="e23e2-222">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Office 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>
    
    > [!NOTE]
    >  <span data-ttu-id="e23e2-223">在 Exchange 2007、Exchange 2010 和 Exchange 2013 中，您还应将  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` 设置为 `Null`。</span><span class="sxs-lookup"><span data-stu-id="e23e2-223">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span> 
  
    <span data-ttu-id="e23e2-p130">Office 365 使用 CNAME 记录为 Outlook 和移动客户端实现自动发现服务。自动发现 CNAME 记录必须包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="e23e2-p130">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="e23e2-226">**别名：** autodiscover</span><span class="sxs-lookup"><span data-stu-id="e23e2-226">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="e23e2-227">**目标：** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="e23e2-227">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="e23e2-228">有关更多信息，请参阅[管理 DNS 记录时为 Office 365 创建 DNS 记录](https://go.microsoft.com/fwlink/p/?LinkId=535028)。</span><span class="sxs-lookup"><span data-stu-id="e23e2-228">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="e23e2-p131">**停止使用内部部署 Exchange 服务器。** 当您验证所有电子邮件都可以直接被路由到 Office 365 邮箱，并且您不再需要维护内部部署电子邮件组织或不用计划实施单点登录 (SSO) 解决方案以后，您可以从服务器中卸载 Exchange 并删除内部部署 Exchange 组织。</span><span class="sxs-lookup"><span data-stu-id="e23e2-p131">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="e23e2-231">有关详细信息，请参阅以下资源：</span><span class="sxs-lookup"><span data-stu-id="e23e2-231">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="e23e2-232">修改或删除 Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="e23e2-232">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="e23e2-233">如何删除 Exchange 2007 组织</span><span class="sxs-lookup"><span data-stu-id="e23e2-233">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="e23e2-234">如何卸载 Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="e23e2-234">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

