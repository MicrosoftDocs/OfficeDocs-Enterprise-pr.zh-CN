---
title: 使用 PowerShell 执行暂存迁移以迁移到 Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 摘要：了解如何使用 Windows PowerShell 执行到 Office 365 的暂存迁移。
ms.openlocfilehash: ca50edd079e17808c46ff5a956ed2efad34eb322
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052555"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a><span data-ttu-id="d88a5-103">使用 PowerShell 执行暂存迁移以迁移到 Office 365</span><span class="sxs-lookup"><span data-stu-id="d88a5-103">Use PowerShell to perform a staged migration to Office 365</span></span>

<span data-ttu-id="d88a5-104">随着时间的推移，您可以使用暂存迁移将源电子邮件系统中用户邮箱的内容迁移到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="d88a5-104">You can migrate the contents of user mailboxes from a source email system to Office 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="d88a5-105">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d88a5-105">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell.</span></span> <span data-ttu-id="d88a5-106">The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process.</span><span class="sxs-lookup"><span data-stu-id="d88a5-106">The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process.</span></span> <span data-ttu-id="d88a5-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span><span class="sxs-lookup"><span data-stu-id="d88a5-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d88a5-108">You can also use the Exchange admin center to perform staged migration.</span><span class="sxs-lookup"><span data-stu-id="d88a5-108">You can also use the Exchange admin center to perform staged migration.</span></span> <span data-ttu-id="d88a5-109">See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span><span class="sxs-lookup"><span data-stu-id="d88a5-109">See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="d88a5-110">在开始之前，您需要知道什么？</span><span class="sxs-lookup"><span data-stu-id="d88a5-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="d88a5-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span><span class="sxs-lookup"><span data-stu-id="d88a5-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span></span> <span data-ttu-id="d88a5-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span><span class="sxs-lookup"><span data-stu-id="d88a5-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span></span> <span data-ttu-id="d88a5-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="d88a5-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="d88a5-114">You need to be assigned permissions before you can perform this procedure or procedures.</span><span class="sxs-lookup"><span data-stu-id="d88a5-114">You need to be assigned permissions before you can perform this procedure or procedures.</span></span> <span data-ttu-id="d88a5-115">To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span><span class="sxs-lookup"><span data-stu-id="d88a5-115">To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="d88a5-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span><span class="sxs-lookup"><span data-stu-id="d88a5-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span></span> <span data-ttu-id="d88a5-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span><span class="sxs-lookup"><span data-stu-id="d88a5-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="d88a5-118">有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="d88a5-118">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="d88a5-119">迁移步骤</span><span class="sxs-lookup"><span data-stu-id="d88a5-119">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="d88a5-120">步骤 1：准备暂存迁移</span><span class="sxs-lookup"><span data-stu-id="d88a5-120">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="d88a5-121">在开始通过暂存迁移将邮箱迁移到 Office 365 之前，您必须对您的 Exchange 环境进行几处更改。</span><span class="sxs-lookup"><span data-stu-id="d88a5-121">Before you migrate mailboxes to Office 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="d88a5-122">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="d88a5-122">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server.</span></span> <span data-ttu-id="d88a5-123">For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span><span class="sxs-lookup"><span data-stu-id="d88a5-123">For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- [<span data-ttu-id="d88a5-124">Exchange 2007:如何启用 Outlook 无处不在</span><span class="sxs-lookup"><span data-stu-id="d88a5-124">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [<span data-ttu-id="d88a5-125">如何使用 Exchange 2003 配置 Outlook 无处不在</span><span class="sxs-lookup"><span data-stu-id="d88a5-125">How to configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> <span data-ttu-id="d88a5-126">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration.</span><span class="sxs-lookup"><span data-stu-id="d88a5-126">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration.</span></span> <span data-ttu-id="d88a5-127">Outlook Anywhere can't be configured with a self-signed certificate.</span><span class="sxs-lookup"><span data-stu-id="d88a5-127">Outlook Anywhere can't be configured with a self-signed certificate.</span></span> <span data-ttu-id="d88a5-128">For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="d88a5-128">For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="d88a5-129">**可选：确认您是否可以使用 Outlook 无处不在 连接到 Exchange 组织** 使用下列方法之一来测试您的连接设置。</span><span class="sxs-lookup"><span data-stu-id="d88a5-129">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="d88a5-130">使用公司网络外部的 Outlook 连接到您的内部部署 Exchange 邮箱。</span><span class="sxs-lookup"><span data-stu-id="d88a5-130">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="d88a5-131">使用[Microsoft 远程连接分析器](https://https://testconnectivity.microsoft.com/)测试您的连接设置。</span><span class="sxs-lookup"><span data-stu-id="d88a5-131">Use the [Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) to test your connection settings.</span></span> <span data-ttu-id="d88a5-132">使用 Outlook 无处不在 (RPC over HTTP) 或 Outlook 自动发现测试。</span><span class="sxs-lookup"><span data-stu-id="d88a5-132">Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="d88a5-133">在 Exchange Online PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d88a5-133">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="d88a5-134">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span><span class="sxs-lookup"><span data-stu-id="d88a5-134">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span></span> <span data-ttu-id="d88a5-135">This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span><span class="sxs-lookup"><span data-stu-id="d88a5-135">This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="d88a5-136">要迁移邮箱，管理员必须拥有以下权限集之一：</span><span class="sxs-lookup"><span data-stu-id="d88a5-136">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="d88a5-137">内部部署组织中 Active Directory 中的 **Domain Admins** 组成员。</span><span class="sxs-lookup"><span data-stu-id="d88a5-137">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="d88a5-138">或</span><span class="sxs-lookup"><span data-stu-id="d88a5-138">or</span></span>
    
- <span data-ttu-id="d88a5-139">分配了对每个内部部署邮箱的 **FullAccess** 权限以及可修改内部部署用户帐户上的 **TargetAddress** 属性的 **WriteProperty** 权限。</span><span class="sxs-lookup"><span data-stu-id="d88a5-139">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="d88a5-140">或</span><span class="sxs-lookup"><span data-stu-id="d88a5-140">or</span></span>
    
- <span data-ttu-id="d88a5-141">分配了对存储用户邮箱的内部部署邮箱数据库上的 **Receive As** 权限以及可修改内部部署用户帐户上的 **TargetAddress** 属性的 **WriteProperty** 权限。</span><span class="sxs-lookup"><span data-stu-id="d88a5-141">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="d88a5-142">有关如何设置这些权限的说明，请参阅[分配权限以将邮箱迁移到 Office 365](https://go.microsoft.com/fwlink/?LinkId=521656)。</span><span class="sxs-lookup"><span data-stu-id="d88a5-142">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="d88a5-143">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration.</span><span class="sxs-lookup"><span data-stu-id="d88a5-143">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration.</span></span> <span data-ttu-id="d88a5-144">Turn on UM for the mailboxes after migration is complete.</span><span class="sxs-lookup"><span data-stu-id="d88a5-144">Turn on UM for the mailboxes after migration is complete.</span></span> <span data-ttu-id="d88a5-145">For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span><span class="sxs-lookup"><span data-stu-id="d88a5-145">For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="d88a5-146">**Use directory synchronization to create new users in Office 365.**</span><span class="sxs-lookup"><span data-stu-id="d88a5-146">**Use directory synchronization to create new users in Office 365.**</span></span> <span data-ttu-id="d88a5-147">You use directory synchronization to create all the on-premises users in your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="d88a5-147">You use directory synchronization to create all the on-premises users in your Office 365 organization.</span></span>
  
<span data-ttu-id="d88a5-148">You need to license the users after they're created.</span><span class="sxs-lookup"><span data-stu-id="d88a5-148">You need to license the users after they're created.</span></span> <span data-ttu-id="d88a5-149">You have 30 days to add licenses after the users are created.</span><span class="sxs-lookup"><span data-stu-id="d88a5-149">You have 30 days to add licenses after the users are created.</span></span> <span data-ttu-id="d88a5-150">For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span><span class="sxs-lookup"><span data-stu-id="d88a5-150">For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="d88a5-151">您可以使用 Microsoft Azure Active Directory （Azure AD）同步工具或 Microsoft Azure AD 同步服务在 Office 365 中同步和创建本地用户。</span><span class="sxs-lookup"><span data-stu-id="d88a5-151">You can use either the Microsoft Azure Active Directory (Azure AD) Synchronization Tool or the Microsoft Azure AD Sync Services  to synchronize and create your on-premises users in Office 365.</span></span> <span data-ttu-id="d88a5-152">当邮箱被迁移到 Office 365 之后，您可以在内部部署组织中管理用户帐户，而且它们会与 Office 365 组织同步。</span><span class="sxs-lookup"><span data-stu-id="d88a5-152">After mailboxes are migrated to Office 365, you manage user accounts in your on-premises organization, and they're synchronized with your Office 365 organization.</span></span> <span data-ttu-id="d88a5-153">有关更多信息，请参阅[目录集成](https://go.microsoft.com/fwlink/?LinkId=521788)。</span><span class="sxs-lookup"><span data-stu-id="d88a5-153">For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="d88a5-154">步骤 2：为暂存迁移批处理创建 CSV 文件</span><span class="sxs-lookup"><span data-stu-id="d88a5-154">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="d88a5-155">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch.</span><span class="sxs-lookup"><span data-stu-id="d88a5-155">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch.</span></span> <span data-ttu-id="d88a5-156">Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span><span class="sxs-lookup"><span data-stu-id="d88a5-156">Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="d88a5-157">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration.</span><span class="sxs-lookup"><span data-stu-id="d88a5-157">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration.</span></span> <span data-ttu-id="d88a5-158">The CSV file for a migration batch can contain a maximum of 2,000 rows.</span><span class="sxs-lookup"><span data-stu-id="d88a5-158">The CSV file for a migration batch can contain a maximum of 2,000 rows.</span></span> <span data-ttu-id="d88a5-159">To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span><span class="sxs-lookup"><span data-stu-id="d88a5-159">To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="d88a5-160">**支持的属性**</span><span class="sxs-lookup"><span data-stu-id="d88a5-160">**Supported attributes**</span></span>
  
<span data-ttu-id="d88a5-161">The CSV file for a staged migration supports the following three attributes.</span><span class="sxs-lookup"><span data-stu-id="d88a5-161">The CSV file for a staged migration supports the following three attributes.</span></span> <span data-ttu-id="d88a5-162">Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span><span class="sxs-lookup"><span data-stu-id="d88a5-162">Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="d88a5-163">**属性**</span><span class="sxs-lookup"><span data-stu-id="d88a5-163">**Attribute**</span></span>|<span data-ttu-id="d88a5-164">**说明**</span><span class="sxs-lookup"><span data-stu-id="d88a5-164">**Description**</span></span>|<span data-ttu-id="d88a5-165">**是否必需？**</span><span class="sxs-lookup"><span data-stu-id="d88a5-165">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d88a5-166">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="d88a5-166">EmailAddress</span></span>  <br/> |<span data-ttu-id="d88a5-167">为内部部署邮箱指定一个主要的 SMTP 电子邮件地址，例如，pilarp@contoso.com。</span><span class="sxs-lookup"><span data-stu-id="d88a5-167">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="d88a5-168">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365.</span><span class="sxs-lookup"><span data-stu-id="d88a5-168">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365.</span></span> <span data-ttu-id="d88a5-169">For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span><span class="sxs-lookup"><span data-stu-id="d88a5-169">For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="d88a5-170">必需</span><span class="sxs-lookup"><span data-stu-id="d88a5-170">Required</span></span>  <br/> |
|<span data-ttu-id="d88a5-171">密码</span><span class="sxs-lookup"><span data-stu-id="d88a5-171">Password</span></span>  <br/> |<span data-ttu-id="d88a5-172">The password to be set for the new Office 365 mailbox.</span><span class="sxs-lookup"><span data-stu-id="d88a5-172">The password to be set for the new Office 365 mailbox.</span></span> <span data-ttu-id="d88a5-173">Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span><span class="sxs-lookup"><span data-stu-id="d88a5-173">Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="d88a5-174">可选</span><span class="sxs-lookup"><span data-stu-id="d88a5-174">Optional</span></span>  <br/> |
|<span data-ttu-id="d88a5-175">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="d88a5-175">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="d88a5-176">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox.</span><span class="sxs-lookup"><span data-stu-id="d88a5-176">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox.</span></span> <span data-ttu-id="d88a5-177">Use **True** or **False** for the value of this parameter.</span><span class="sxs-lookup"><span data-stu-id="d88a5-177">Use **True** or **False** for the value of this parameter.</span></span> <br/> <span data-ttu-id="d88a5-178">> [!NOTE]> 如果已通过在本地组织中部署 Active Directory 联合身份验证服务 (AD FS) 或更高版本来实现单一登录 (SSO) 解决方案，必须将 **ForceChangePassword** 属性值设为 **False**。</span><span class="sxs-lookup"><span data-stu-id="d88a5-178">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="d88a5-179">可选</span><span class="sxs-lookup"><span data-stu-id="d88a5-179">Optional</span></span>  <br/> |
   
 <span data-ttu-id="d88a5-180">**CSV 文件格式**</span><span class="sxs-lookup"><span data-stu-id="d88a5-180">**CSV file format**</span></span>
  
<span data-ttu-id="d88a5-181">Here's an example of the format for the CSV file.</span><span class="sxs-lookup"><span data-stu-id="d88a5-181">Here's an example of the format for the CSV file.</span></span> <span data-ttu-id="d88a5-182">In this example, three on-premises mailboxes are migrated to Office 365.</span><span class="sxs-lookup"><span data-stu-id="d88a5-182">In this example, three on-premises mailboxes are migrated to Office 365.</span></span>
  
<span data-ttu-id="d88a5-183">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow.</span><span class="sxs-lookup"><span data-stu-id="d88a5-183">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow.</span></span> <span data-ttu-id="d88a5-184">Each attribute name is separated by a comma.</span><span class="sxs-lookup"><span data-stu-id="d88a5-184">Each attribute name is separated by a comma.</span></span>
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="d88a5-185">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox.</span><span class="sxs-lookup"><span data-stu-id="d88a5-185">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox.</span></span> <span data-ttu-id="d88a5-186">The attribute values in each row must be in the same order as the attribute names in the header row.</span><span class="sxs-lookup"><span data-stu-id="d88a5-186">The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="d88a5-187">Use any text editor, or an application like Excel , to create the CSV file.</span><span class="sxs-lookup"><span data-stu-id="d88a5-187">Use any text editor, or an application like Excel , to create the CSV file.</span></span> <span data-ttu-id="d88a5-188">Save the file as a .csv or .txt file.</span><span class="sxs-lookup"><span data-stu-id="d88a5-188">Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d88a5-189">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding.</span><span class="sxs-lookup"><span data-stu-id="d88a5-189">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding.</span></span> <span data-ttu-id="d88a5-190">Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span><span class="sxs-lookup"><span data-stu-id="d88a5-190">Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="d88a5-191">步骤 3：创建迁移终结点</span><span class="sxs-lookup"><span data-stu-id="d88a5-191">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="d88a5-192"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="d88a5-192"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="d88a5-193">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span><span class="sxs-lookup"><span data-stu-id="d88a5-193">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span></span> <span data-ttu-id="d88a5-194">To do this, Office 365 uses a migration endpoint.</span><span class="sxs-lookup"><span data-stu-id="d88a5-194">To do this, Office 365 uses a migration endpoint.</span></span> <span data-ttu-id="d88a5-195">To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="d88a5-195">To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="d88a5-196">有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="d88a5-196">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="d88a5-197">要在 Exchange Online PowerShell 中创建名为“StagedEndpoint”的 Outlook 无处不在迁移终结点，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d88a5-197">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="d88a5-198">有关 **New-MigrationEndpoint** cmdlet 的详细信息，请参阅[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)。</span><span class="sxs-lookup"><span data-stu-id="d88a5-198">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="d88a5-199">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span><span class="sxs-lookup"><span data-stu-id="d88a5-199">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span></span> <span data-ttu-id="d88a5-200">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span><span class="sxs-lookup"><span data-stu-id="d88a5-200">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="d88a5-201">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="d88a5-201">Verify it worked</span></span>

<span data-ttu-id="d88a5-202">在 Exchange Online PowerShell 中，运行以下命令来显示有关“StagedEndpoint”迁移终结点的信息：</span><span class="sxs-lookup"><span data-stu-id="d88a5-202">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="d88a5-203">步骤 4：创建并启动暂存迁移批处理</span><span class="sxs-lookup"><span data-stu-id="d88a5-203">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="d88a5-204"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="d88a5-204"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="d88a5-205">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="d88a5-205">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span></span> <span data-ttu-id="d88a5-206">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span><span class="sxs-lookup"><span data-stu-id="d88a5-206">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span></span> <span data-ttu-id="d88a5-207">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d88a5-207">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="d88a5-208">This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="d88a5-208">This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="d88a5-209">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="d88a5-209">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span> <span data-ttu-id="d88a5-210">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d88a5-210">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="d88a5-211">As previously stated, only one cutover migration batch can exist at a time.</span><span class="sxs-lookup"><span data-stu-id="d88a5-211">As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="d88a5-212">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="d88a5-212">Verify it worked</span></span>

<span data-ttu-id="d88a5-213">在 Exchange Online PowerShell 中运行以下命令来显示有关“StagedBatch1”的信息：</span><span class="sxs-lookup"><span data-stu-id="d88a5-213">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="d88a5-214">您还可以通过运行以下命令，验证该批处理是否已启动：</span><span class="sxs-lookup"><span data-stu-id="d88a5-214">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="d88a5-215">有关 **Get-MigrationBatch** cmdlet 的详细信息，请参阅[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)。</span><span class="sxs-lookup"><span data-stu-id="d88a5-215">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="d88a5-216">步骤 5：将内部部署邮箱转换为启用邮件的用户</span><span class="sxs-lookup"><span data-stu-id="d88a5-216">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="d88a5-217"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="d88a5-217"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="d88a5-218">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail.</span><span class="sxs-lookup"><span data-stu-id="d88a5-218">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail.</span></span> <span data-ttu-id="d88a5-219">A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365.</span><span class="sxs-lookup"><span data-stu-id="d88a5-219">A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365.</span></span> <span data-ttu-id="d88a5-220">Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span><span class="sxs-lookup"><span data-stu-id="d88a5-220">Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="d88a5-221">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email.</span><span class="sxs-lookup"><span data-stu-id="d88a5-221">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email.</span></span> <span data-ttu-id="d88a5-222">So what do you do for those people who have both?</span><span class="sxs-lookup"><span data-stu-id="d88a5-222">So what do you do for those people who have both?</span></span> <span data-ttu-id="d88a5-223">What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users.</span><span class="sxs-lookup"><span data-stu-id="d88a5-223">What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users.</span></span> <span data-ttu-id="d88a5-224">When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span><span class="sxs-lookup"><span data-stu-id="d88a5-224">When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="d88a5-225">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users.</span><span class="sxs-lookup"><span data-stu-id="d88a5-225">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users.</span></span> <span data-ttu-id="d88a5-226">This lets you manage cloud-based users from your on-premises organization by using Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d88a5-226">This lets you manage cloud-based users from your on-premises organization by using Active Directory.</span></span> <span data-ttu-id="d88a5-227">Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d88a5-227">Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="d88a5-228">步骤 6：删除暂存迁移批处理</span><span class="sxs-lookup"><span data-stu-id="d88a5-228">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="d88a5-229"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="d88a5-229"><a name="BK_Endpoint"> </a></span></span>

 <span data-ttu-id="d88a5-230">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch.</span><span class="sxs-lookup"><span data-stu-id="d88a5-230">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch.</span></span> <span data-ttu-id="d88a5-231">Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch.</span><span class="sxs-lookup"><span data-stu-id="d88a5-231">Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch.</span></span> <span data-ttu-id="d88a5-232">When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span><span class="sxs-lookup"><span data-stu-id="d88a5-232">When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="d88a5-233">要在 Exchange Online PowerShell 中删除“StagedBatch1”迁移批处理，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d88a5-233">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="d88a5-234">有关 **Remove-MigrationBatch** cmdlet 的详细信息，请参阅[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)。</span><span class="sxs-lookup"><span data-stu-id="d88a5-234">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="d88a5-235">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="d88a5-235">Verify it worked</span></span>

<span data-ttu-id="d88a5-236">在 Exchange Online PowerShell 中运行以下命令来显示有关“IMAPBatch1”的信息：</span><span class="sxs-lookup"><span data-stu-id="d88a5-236">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="d88a5-237">此命令会返回状态为 **Removing** 的迁移批处理或返回错误消息，指出未找到该迁移批处理，验证该批处理已删除。</span><span class="sxs-lookup"><span data-stu-id="d88a5-237">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="d88a5-238">有关 **Get-MigrationBatch** cmdlet 的详细信息，请参阅[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)。</span><span class="sxs-lookup"><span data-stu-id="d88a5-238">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-office-365-users"></a><span data-ttu-id="d88a5-239">步骤 7：将许可证分配给 Office 365 用户</span><span class="sxs-lookup"><span data-stu-id="d88a5-239">Step7: Assign licenses to Office 365 users</span></span>
<span data-ttu-id="d88a5-240"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="d88a5-240"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="d88a5-241">通过分配许可证，激活迁移帐户的 Office 365 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d88a5-241">Activate Office 365 user accounts for the migrated accounts by assigning licenses.</span></span> <span data-ttu-id="d88a5-242">如果您不分配许可证，则在宽限期（30 天）结束后将禁用该邮箱。</span><span class="sxs-lookup"><span data-stu-id="d88a5-242">If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends.</span></span> <span data-ttu-id="d88a5-243">若要在 Microsoft 365 管理中心分配许可证，请参阅[分配或取消分配 Office 365 商业版许可证](https://go.microsoft.com/fwlink/?LinkId=536681)。</span><span class="sxs-lookup"><span data-stu-id="d88a5-243">To assign a license in the Microsoft 365 admin center, see [Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="d88a5-244">步骤 8：完成迁移后任务</span><span class="sxs-lookup"><span data-stu-id="d88a5-244">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="d88a5-245"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="d88a5-245"><a name="BK_Postmigration"> </a></span></span>

- <span data-ttu-id="d88a5-246">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span><span class="sxs-lookup"><span data-stu-id="d88a5-246">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="d88a5-247">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="d88a5-247">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="d88a5-248">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="d88a5-248">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span></span> <span data-ttu-id="d88a5-249">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="d88a5-249">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="d88a5-250">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="d88a5-250">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="d88a5-251">The Autodiscover CNAME record must contain the following information:</span><span class="sxs-lookup"><span data-stu-id="d88a5-251">The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="d88a5-252">**别名：** autodiscover</span><span class="sxs-lookup"><span data-stu-id="d88a5-252">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="d88a5-253">**目标：** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="d88a5-253">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="d88a5-254">有关更多信息，请参阅[管理 DNS 记录时为 Office 365 创建 DNS 记录](https://go.microsoft.com/fwlink/p/?LinkId=535028)。</span><span class="sxs-lookup"><span data-stu-id="d88a5-254">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="d88a5-255">**Decommission on-premises Exchange servers.**</span><span class="sxs-lookup"><span data-stu-id="d88a5-255">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="d88a5-256">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span><span class="sxs-lookup"><span data-stu-id="d88a5-256">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="d88a5-257">有关详细信息，请参阅以下资源：</span><span class="sxs-lookup"><span data-stu-id="d88a5-257">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="d88a5-258">修改或删除 Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="d88a5-258">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="d88a5-259">如何删除 Exchange 2007 组织</span><span class="sxs-lookup"><span data-stu-id="d88a5-259">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="d88a5-260">如何卸载 Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="d88a5-260">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

