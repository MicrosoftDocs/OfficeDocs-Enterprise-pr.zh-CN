---
title: 使用 PowerShell 执行直接转换迁移以迁移到 Office 365
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: 摘要：了解如何使用 Windows PowerShell 执行到 Office 365 的直接转换迁移。
ms.openlocfilehash: b40c6ac53a173f700c6b931781d98d7965a2be7c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998567"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a><span data-ttu-id="cadc1-103">使用 PowerShell 执行直接转换迁移以迁移到 Office 365</span><span class="sxs-lookup"><span data-stu-id="cadc1-103">Use PowerShell to perform a cutover migration to Office 365</span></span>

<span data-ttu-id="cadc1-104">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="cadc1-104">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration.</span></span> <span data-ttu-id="cadc1-105">This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cadc1-105">This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="cadc1-106">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process.</span><span class="sxs-lookup"><span data-stu-id="cadc1-106">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process.</span></span> <span data-ttu-id="cadc1-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span><span class="sxs-lookup"><span data-stu-id="cadc1-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="cadc1-108">You can also use the Exchange admin center to perform a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="cadc1-108">You can also use the Exchange admin center to perform a cutover migration.</span></span> <span data-ttu-id="cadc1-109">See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span><span class="sxs-lookup"><span data-stu-id="cadc1-109">See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="cadc1-110">在开始之前，您需要知道什么？</span><span class="sxs-lookup"><span data-stu-id="cadc1-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="cadc1-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span><span class="sxs-lookup"><span data-stu-id="cadc1-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span></span> <span data-ttu-id="cadc1-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span><span class="sxs-lookup"><span data-stu-id="cadc1-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span></span> <span data-ttu-id="cadc1-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="cadc1-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="cadc1-114">You need to be assigned permissions before you can perform this procedure or procedures.</span><span class="sxs-lookup"><span data-stu-id="cadc1-114">You need to be assigned permissions before you can perform this procedure or procedures.</span></span> <span data-ttu-id="cadc1-115">To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span><span class="sxs-lookup"><span data-stu-id="cadc1-115">To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="cadc1-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span><span class="sxs-lookup"><span data-stu-id="cadc1-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span></span> <span data-ttu-id="cadc1-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span><span class="sxs-lookup"><span data-stu-id="cadc1-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="cadc1-118">有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="cadc1-118">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="cadc1-119">迁移步骤</span><span class="sxs-lookup"><span data-stu-id="cadc1-119">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="cadc1-120">步骤 1：准备直接转换迁移</span><span class="sxs-lookup"><span data-stu-id="cadc1-120">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="cadc1-121"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="cadc1-121"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="cadc1-122">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.**</span><span class="sxs-lookup"><span data-stu-id="cadc1-122">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.**</span></span> <span data-ttu-id="cadc1-123">The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="cadc1-123">The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes.</span></span> <span data-ttu-id="cadc1-124">Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="cadc1-124">Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization.</span></span> <span data-ttu-id="cadc1-125">For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="cadc1-125">For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="cadc1-126">**Configure Outlook Anywhere on your on-premises Exchange server.**</span><span class="sxs-lookup"><span data-stu-id="cadc1-126">**Configure Outlook Anywhere on your on-premises Exchange server.**</span></span> <span data-ttu-id="cadc1-127">The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server.</span><span class="sxs-lookup"><span data-stu-id="cadc1-127">The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server.</span></span> <span data-ttu-id="cadc1-128">For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span><span class="sxs-lookup"><span data-stu-id="cadc1-128">For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>
    
  - [<span data-ttu-id="cadc1-129">Exchange 2010:启用 Outlook 无处不在</span><span class="sxs-lookup"><span data-stu-id="cadc1-129">Exchange 2010: Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [<span data-ttu-id="cadc1-130">Exchange 2007:如何启用 Outlook 无处不在</span><span class="sxs-lookup"><span data-stu-id="cadc1-130">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [<span data-ttu-id="cadc1-131">Exchange 2003:RPC over HTTP 的部署方案</span><span class="sxs-lookup"><span data-stu-id="cadc1-131">Exchange 2003: Deployment Scenarios for RPC over HTTP</span></span>](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [<span data-ttu-id="cadc1-132">如何使用 Exchange 2003 配置 Outlook 无处不在</span><span class="sxs-lookup"><span data-stu-id="cadc1-132">How to Configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > <span data-ttu-id="cadc1-133">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA).</span><span class="sxs-lookup"><span data-stu-id="cadc1-133">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA).</span></span> <span data-ttu-id="cadc1-134">It can't be configured with a self-signed certificate.</span><span class="sxs-lookup"><span data-stu-id="cadc1-134">It can't be configured with a self-signed certificate.</span></span> <span data-ttu-id="cadc1-135">For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="cadc1-135">For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
- <span data-ttu-id="cadc1-136">**Verify that you can connect to your Exchange organization using Outlook Anywhere.**</span><span class="sxs-lookup"><span data-stu-id="cadc1-136">**Verify that you can connect to your Exchange organization using Outlook Anywhere.**</span></span> <span data-ttu-id="cadc1-137">Try one of these methods to test your connection settings:</span><span class="sxs-lookup"><span data-stu-id="cadc1-137">Try one of these methods to test your connection settings:</span></span>
    
  - <span data-ttu-id="cadc1-138">使用 Microsoft Outlook 从企业网络外部连接到内部部署 Exchange 邮箱。</span><span class="sxs-lookup"><span data-stu-id="cadc1-138">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
  - <span data-ttu-id="cadc1-139">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings.</span><span class="sxs-lookup"><span data-stu-id="cadc1-139">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings.</span></span> <span data-ttu-id="cadc1-140">Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span><span class="sxs-lookup"><span data-stu-id="cadc1-140">Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
  - <span data-ttu-id="cadc1-141">在 Exchange Online PowerShell 中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="cadc1-141">Run the following commands in Exchange Online PowerShell.</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="cadc1-142">**为内部部署用户帐户分配访问 Exchange 组织中的邮箱所需的权限。**</span><span class="sxs-lookup"><span data-stu-id="cadc1-142">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.**</span></span> <span data-ttu-id="cadc1-143">用于连接到内部部署 Exchange 组织的本地用户帐户（也称为迁移管理员）必须具有访问要迁移到 Office 365 的本地邮箱的必要权限。。</span><span class="sxs-lookup"><span data-stu-id="cadc1-143">The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span></span> <span data-ttu-id="cadc1-144">该用户帐户用于创建内部部署组织的迁移终结点。</span><span class="sxs-lookup"><span data-stu-id="cadc1-144">This user account is used to create a migration endpoint to your on-premises organization.</span></span>
    
    <span data-ttu-id="cadc1-145">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="cadc1-145">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration.</span></span> <span data-ttu-id="cadc1-146">There are three possible options.</span><span class="sxs-lookup"><span data-stu-id="cadc1-146">There are three possible options.</span></span>
    
  - <span data-ttu-id="cadc1-147">迁移管理员必须是内部部署组织的 Active Directory 中的 **Domain Admins** 组成员。</span><span class="sxs-lookup"><span data-stu-id="cadc1-147">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="cadc1-148">或</span><span class="sxs-lookup"><span data-stu-id="cadc1-148">Or</span></span>
    
  - <span data-ttu-id="cadc1-149">必须为迁移管理员分配对每个内部部署邮箱的 **FullAccess** 权限。</span><span class="sxs-lookup"><span data-stu-id="cadc1-149">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>
    
    <span data-ttu-id="cadc1-150">或</span><span class="sxs-lookup"><span data-stu-id="cadc1-150">Or</span></span>
    
  - <span data-ttu-id="cadc1-151">必须为迁移管理员分配对存储用户邮箱的内部部署邮箱数据库的 **代理接收**权限。</span><span class="sxs-lookup"><span data-stu-id="cadc1-151">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>
    
- <span data-ttu-id="cadc1-152">**Disable Unified Messaging.**</span><span class="sxs-lookup"><span data-stu-id="cadc1-152">**Disable Unified Messaging.**</span></span> <span data-ttu-id="cadc1-153">If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them.</span><span class="sxs-lookup"><span data-stu-id="cadc1-153">If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them.</span></span> <span data-ttu-id="cadc1-154">You can then enable UM on the mailboxes after the migration is complete.</span><span class="sxs-lookup"><span data-stu-id="cadc1-154">You can then enable UM on the mailboxes after the migration is complete.</span></span>
    
- <span data-ttu-id="cadc1-155">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365.</span><span class="sxs-lookup"><span data-stu-id="cadc1-155">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365.</span></span> <span data-ttu-id="cadc1-156">If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration.</span><span class="sxs-lookup"><span data-stu-id="cadc1-156">If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration.</span></span> <span data-ttu-id="cadc1-157">Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups.</span><span class="sxs-lookup"><span data-stu-id="cadc1-157">Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups.</span></span> <span data-ttu-id="cadc1-158">If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span><span class="sxs-lookup"><span data-stu-id="cadc1-158">If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>
    
### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="cadc1-159">步骤 2：创建迁移终结点</span><span class="sxs-lookup"><span data-stu-id="cadc1-159">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="cadc1-160"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="cadc1-160"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="cadc1-161">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span><span class="sxs-lookup"><span data-stu-id="cadc1-161">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span></span> <span data-ttu-id="cadc1-162">To do this, Office 365 uses a migration endpoint.</span><span class="sxs-lookup"><span data-stu-id="cadc1-162">To do this, Office 365 uses a migration endpoint.</span></span> <span data-ttu-id="cadc1-163">To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="cadc1-163">To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="cadc1-164">有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="cadc1-164">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="cadc1-165">在 Exchange Online PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="cadc1-165">Run the following commands in Exchange Online PowerShell:</span></span>
  
```
$Credentials = Get-Credential
```

<span data-ttu-id="cadc1-166">该示例使用 [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet 获取并测试对内部部署 Exchange 服务器的连接设置，然后使用这些连接设置来创建名为"CutoverEndpoint"的迁移终结点。</span><span class="sxs-lookup"><span data-stu-id="cadc1-166">The example uses the [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="cadc1-167">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span><span class="sxs-lookup"><span data-stu-id="cadc1-167">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span></span> <span data-ttu-id="cadc1-168">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span><span class="sxs-lookup"><span data-stu-id="cadc1-168">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="cadc1-169">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="cadc1-169">Verify it worked</span></span>

<span data-ttu-id="cadc1-170">在 Exchange Online PowerShell 中，运行以下命令来显示有关“CutoverEndpoint”迁移终结点的信息：</span><span class="sxs-lookup"><span data-stu-id="cadc1-170">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="cadc1-171">步骤 3：创建直接转换迁移批处理</span><span class="sxs-lookup"><span data-stu-id="cadc1-171">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="cadc1-172"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="cadc1-172"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="cadc1-173">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="cadc1-173">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span></span> <span data-ttu-id="cadc1-174">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span><span class="sxs-lookup"><span data-stu-id="cadc1-174">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span></span> <span data-ttu-id="cadc1-175">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cadc1-175">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="cadc1-176">This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="cadc1-176">This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="cadc1-177">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="cadc1-177">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span> <span data-ttu-id="cadc1-178">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cadc1-178">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="cadc1-179">As previously stated, only one cutover migration batch can exist at a time.</span><span class="sxs-lookup"><span data-stu-id="cadc1-179">As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="cadc1-180">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="cadc1-180">Verify it worked</span></span>

<span data-ttu-id="cadc1-181">要验证您是否已成功为直接转换迁移创建了迁移批处理，请在 Exchange Online PowerShell 中运行以下命令来显示有关新迁移批处理的信息：</span><span class="sxs-lookup"><span data-stu-id="cadc1-181">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="cadc1-182">步骤 4：启动直接转换迁移批处理</span><span class="sxs-lookup"><span data-stu-id="cadc1-182">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="cadc1-183"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="cadc1-183"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="cadc1-184">To start the migration batch in Exchange Online PowerShell, run the following command.</span><span class="sxs-lookup"><span data-stu-id="cadc1-184">To start the migration batch in Exchange Online PowerShell, run the following command.</span></span> <span data-ttu-id="cadc1-185">This will create a migration batch called "CutoverBatch".</span><span class="sxs-lookup"><span data-stu-id="cadc1-185">This will create a migration batch called "CutoverBatch".</span></span>
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="cadc1-186">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="cadc1-186">Verify it worked</span></span>

<span data-ttu-id="cadc1-187">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing.</span><span class="sxs-lookup"><span data-stu-id="cadc1-187">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing.</span></span> <span data-ttu-id="cadc1-188">To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span><span class="sxs-lookup"><span data-stu-id="cadc1-188">To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="cadc1-189">步骤 5：将你的电子邮件路由到 Office 365</span><span class="sxs-lookup"><span data-stu-id="cadc1-189">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="cadc1-190"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="cadc1-190"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="cadc1-191">Email systems use a DNS record called an MX record to figure out where to deliver emails.</span><span class="sxs-lookup"><span data-stu-id="cadc1-191">Email systems use a DNS record called an MX record to figure out where to deliver emails.</span></span> <span data-ttu-id="cadc1-192">During the email migration process, your MX record was pointing to your source email system.</span><span class="sxs-lookup"><span data-stu-id="cadc1-192">During the email migration process, your MX record was pointing to your source email system.</span></span> <span data-ttu-id="cadc1-193">Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365.</span><span class="sxs-lookup"><span data-stu-id="cadc1-193">Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365.</span></span> <span data-ttu-id="cadc1-194">This helps make sure that email is delivered to your Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="cadc1-194">This helps make sure that email is delivered to your Office 365 mailboxes.</span></span> <span data-ttu-id="cadc1-195">By moving the MX record, you can also you turn off your old email system when you're ready.</span><span class="sxs-lookup"><span data-stu-id="cadc1-195">By moving the MX record, you can also you turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="cadc1-196">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163).</span><span class="sxs-lookup"><span data-stu-id="cadc1-196">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163).</span></span> <span data-ttu-id="cadc1-197">If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span><span class="sxs-lookup"><span data-stu-id="cadc1-197">If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="cadc1-198">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record.</span><span class="sxs-lookup"><span data-stu-id="cadc1-198">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record.</span></span> <span data-ttu-id="cadc1-199">Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span><span class="sxs-lookup"><span data-stu-id="cadc1-199">Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span></span> 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="cadc1-200">步骤 6：删除直接转换迁移批处理</span><span class="sxs-lookup"><span data-stu-id="cadc1-200">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="cadc1-201"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="cadc1-201"><a name="Bk_step6"> </a></span></span>

<span data-ttu-id="cadc1-202">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365.</span><span class="sxs-lookup"><span data-stu-id="cadc1-202">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365.</span></span> <span data-ttu-id="cadc1-203">After this, you can delete the cutover migration batch.</span><span class="sxs-lookup"><span data-stu-id="cadc1-203">After this, you can delete the cutover migration batch.</span></span> <span data-ttu-id="cadc1-204">Verify the following before you delete the migration batch.</span><span class="sxs-lookup"><span data-stu-id="cadc1-204">Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="cadc1-205">All users are using Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="cadc1-205">All users are using Office 365 mailboxes.</span></span> <span data-ttu-id="cadc1-206">After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="cadc1-206">After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="cadc1-207">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them.</span><span class="sxs-lookup"><span data-stu-id="cadc1-207">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them.</span></span> <span data-ttu-id="cadc1-208">To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="cadc1-208">To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="cadc1-209">要在 Exchange Online PowerShell 中删除“CutoverBatch”迁移批处理，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="cadc1-209">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="cadc1-210">第 7 部分：分配用户许可证</span><span class="sxs-lookup"><span data-stu-id="cadc1-210">Section 7: Assign user licenses</span></span>
<span data-ttu-id="cadc1-211"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="cadc1-211"><a name="BK_Step7"> </a></span></span>

 <span data-ttu-id="cadc1-212">**通过分配许可证，激活迁移后帐户的 Office 365 用户帐户。**</span><span class="sxs-lookup"><span data-stu-id="cadc1-212">**Activate Office 365 user accounts for the migrated accounts by assigning licenses.**</span></span> <span data-ttu-id="cadc1-213">如果不分配许可证，则当宽限期（30 天）结束时，邮箱将处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="cadc1-213">If you don't assign a license, the mailbox is disabled when the grace period ends (30 days).</span></span> <span data-ttu-id="cadc1-214">若要在 Microsoft 365 管理中心中分配许可证，请参阅为[Office 365 for Business 分配或取消分配许可证](https://go.microsoft.com/fwlink/?LinkId=536681)。</span><span class="sxs-lookup"><span data-stu-id="cadc1-214">To assign a license in the Microsoft 365 admin center, see[Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="cadc1-215">步骤 8：完成迁移后任务</span><span class="sxs-lookup"><span data-stu-id="cadc1-215">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="cadc1-216"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="cadc1-216"><a name="BK_Step8"> </a></span></span>

- <span data-ttu-id="cadc1-217">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span><span class="sxs-lookup"><span data-stu-id="cadc1-217">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="cadc1-218">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="cadc1-218">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="cadc1-219">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="cadc1-219">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span></span> <span data-ttu-id="cadc1-220">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="cadc1-220">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="cadc1-221">如果您保留 Exchange Server，则还应确保在迁移后自动发现 DNS CNAME 记录必须在内部和外部 DNS 中指向 Office 365，以便 Outlook 客户端能够连接到正确的邮箱。</span><span class="sxs-lookup"><span data-stu-id="cadc1-221">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Office 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>
    
    > [!NOTE]
    >  <span data-ttu-id="cadc1-222">在 Exchange 2007、Exchange 2010 和 Exchange 2013 中，您还应将  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` 设置为 `Null`。</span><span class="sxs-lookup"><span data-stu-id="cadc1-222">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span> 
  
    <span data-ttu-id="cadc1-223">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="cadc1-223">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="cadc1-224">The Autodiscover CNAME record must contain the following information:</span><span class="sxs-lookup"><span data-stu-id="cadc1-224">The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="cadc1-225">**别名：** autodiscover</span><span class="sxs-lookup"><span data-stu-id="cadc1-225">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="cadc1-226">**目标：** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="cadc1-226">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="cadc1-227">有关更多信息，请参阅[管理 DNS 记录时为 Office 365 创建 DNS 记录](https://go.microsoft.com/fwlink/p/?LinkId=535028)。</span><span class="sxs-lookup"><span data-stu-id="cadc1-227">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="cadc1-228">**Decommission on-premises Exchange servers.**</span><span class="sxs-lookup"><span data-stu-id="cadc1-228">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="cadc1-229">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span><span class="sxs-lookup"><span data-stu-id="cadc1-229">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="cadc1-230">有关详细信息，请参阅以下资源：</span><span class="sxs-lookup"><span data-stu-id="cadc1-230">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="cadc1-231">修改或删除 Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="cadc1-231">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="cadc1-232">如何删除 Exchange 2007 组织</span><span class="sxs-lookup"><span data-stu-id="cadc1-232">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="cadc1-233">如何卸载 Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="cadc1-233">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

