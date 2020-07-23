---
title: 使用 PowerShell 执行到 Microsoft 365 的 IMAP 迁移
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: 摘要：了解如何使用 Windows PowerShell 执行到 Microsoft 365 的 IMAP 迁移。
ms.openlocfilehash: fa53fd1829121bb697277805e4f07d25ec2179b9
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229768"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a><span data-ttu-id="b2c6d-103">使用 PowerShell 执行到 Microsoft 365 的 IMAP 迁移</span><span class="sxs-lookup"><span data-stu-id="b2c6d-103">Use PowerShell to perform an IMAP migration to Microsoft 365</span></span>

<span data-ttu-id="b2c6d-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="b2c6d-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="b2c6d-p101">作为部署 Microsoft 365 的过程的一部分，您可以选择将用户邮箱的内容从 Internet 邮件访问协议（IMAP）电子邮件服务迁移到 Microsoft 365。本文将引导您完成使用 Exchange Online PowerShell 进行电子邮件 IMAP 迁移的任务。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p101">As part of the process of deploying Microsoft 365, you can choose to migrate the contents of user mailboxes from an Internet Mail Access Protocol (IMAP) email service to Microsoft 365. This article walks you through the tasks for an email IMAP migration by using Exchange Online PowerShell.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="b2c6d-p102">您还可以使用 Exchange 管理中心执行 IMAP 迁移。请参阅[迁移 IMAP 邮箱](https://go.microsoft.com/fwlink/p/?LinkId=536685)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p102">You can also use the Exchange admin center to perform an IMAP migration. See [Migrate your IMAP mailboxes](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="b2c6d-109">在开始之前，你需要知道什么？</span><span class="sxs-lookup"><span data-stu-id="b2c6d-109">What do you need to know before you begin?</span></span>

<span data-ttu-id="b2c6d-p103">估计完成该任务的时间：2-5 分钟以创建迁移批处理。迁移批处理启动后，迁移的持续时间将根据批处理中的邮箱数、每个邮箱的大小和可用网络容量的不同而有所不同。有关影响将邮箱迁移到 Microsoft 365 所需时间的其他因素的信息，请参阅[迁移性能](https://go.microsoft.com/fwlink/p/?LinkId=275079)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Microsoft 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="b2c6d-p104">你必须先获得权限，然后才能执行此过程。要查看你需要哪些权限，请参阅[收件人权限](https://go.microsoft.com/fwlink/p/?LinkId=534105)主题的一个表中的"迁移"条目。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="b2c6d-p105">若要使用 Exchange Online PowerShell cmdlet，你需要登录并将 cmdlet 导入你的本地 Windows PowerShell 会话。有关说明，请参阅[使用远程 PowerShell 连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="b2c6d-117">有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-117">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="b2c6d-118">以下限制适用于 IMAP 迁移：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-118">The following restrictions apply to IMAP migrations:</span></span>
  
- <span data-ttu-id="b2c6d-p106">只有在用户收件箱或其他邮件文件夹中的项目才会被迁移。你不能迁移联系人、日历项目或任务。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p106">Only items in a user's inbox or other mail folders can be migrated. You can't migrate contacts, calendar items, or tasks.</span></span>
    
- <span data-ttu-id="b2c6d-121">最多可以从用户邮箱迁移 500,000 个项目。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-121">A maximum of 500,000 items can be migrated from a user's mailbox.</span></span>
    
- <span data-ttu-id="b2c6d-122">能够迁移的邮件最大大小为 35 MB。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-122">The maximum message size that can be migrated is 35 MB.</span></span>
    
## <a name="migration-steps"></a><span data-ttu-id="b2c6d-123">迁移步骤</span><span class="sxs-lookup"><span data-stu-id="b2c6d-123">Migration steps</span></span>

### <a name="step-1-prepare-for-an-imap-migration"></a><span data-ttu-id="b2c6d-124">步骤 1：准备 IMAP 迁移</span><span class="sxs-lookup"><span data-stu-id="b2c6d-124">Step 1: Prepare for an IMAP migration</span></span>
<span data-ttu-id="b2c6d-125"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="b2c6d-125"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="b2c6d-p107">**如果你有 IMAP 组织的域，请将其添加为 Microsoft 365 组织的接受域。** 如果要对 Microsoft 365 邮箱使用已拥有的相同域，首先必须将其作为接受域添加到 Microsoft 365。添加后，可以在 Microsoft 365 中创建用户。有关详细信息，请参阅[验证您的域](https://go.microsoft.com/fwlink/p/?LinkId=534110)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p107">**If you have a domain for you IMAP organization, add it as an accepted domain of your Microsoft 365 organization.** If you want to use the same domain you already own for your Microsoft 365 mailboxes, you first have to add it as an accepted domain to Microsoft 365. After you have added it, you can create your users in Microsoft 365. For more information, see[Verify your domain](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="b2c6d-p108">**将每个用户添加到 Microsoft 365，使其具有邮箱。** 有关说明，请参阅[向 Microsoft 365 for Business 添加用户](https://go.microsoft.com/fwlink/p/?LinkId=535065)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p108">**Add each user to Microsoft 365 so that they have a mailbox.** For instructions, see[Add users to Microsoft 365 for business](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span></span>
    
- <span data-ttu-id="b2c6d-p109">**获取 IMAP 服务器的 FQDN**。在创建 IMAP 迁移终结点时，你需要提供从中迁移邮箱数据的 IMAP 服务器的完全限定域名 (FQDN)（也称为完整的计算机名称）。可使用 IMAP 客户端或 PING 命令来验证你能否使用此 FQDN 通过 Internet 与 IMAP 服务器进行通信。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p109">**Obtain the FQDN of the IMAP server**. You need to provide the fully qualified domain name (FQDN) (also called the full computer name) of the IMAP server that you will migrate mailbox data from when you create an IMAP migration endpoint. Use an IMAP client or the PING command to verify that you can use the FQDN to communicate with the IMAP server over the Internet.</span></span>
    
- <span data-ttu-id="b2c6d-p110">**配置防火墙以允许 IMAP 连接**。你可能必须打开托管 IMAP 服务器的组织的防火墙中的端口，以便于迁移期间来自 Microsoft 数据中心的网络通信被允许进入托管 IMAP 服务器的组织。有关 Microsoft 数据中心使用的 IP 地址列表，请参阅 [Exchange Online URL 和 IP 地址范围](https://go.microsoft.com/fwlink/p/?LinkId=535066)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p110">**Configure the firewall to allow IMAP connections**. You might have to open ports in the firewall of the organization that hosts the IMAP server so network traffic originating from the Microsoft datacenter during the migration is allowed to enter the organization that hosts the IMAP server. For a list of IP addresses used by Microsoft datacenters, see [Exchange Online URLs and IP Address Ranges](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span></span>
    
- <span data-ttu-id="b2c6d-p111">**分配管理员帐户权限以访问 IMAP 组织中的邮箱**。如果你在 CSV 文件中使用管理员凭据，则你使用的帐户必须具有必要的权限才能访问内部部署邮箱。访问用户邮箱所需的权限将由特定的 IMAP 服务器决定。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p111">**Assign the administrator account permissions to access mailboxes in your IMAP organization**. If you use administrator credentials in the CSV file, the account that you use must have the necessary permissions to access the on-premises mailboxes. The permissions required to access user mailboxes is determined by the particular IMAP server.</span></span> 
    
- <span data-ttu-id="b2c6d-p112">**要使用 Exchange Online PowerShell cmdlet**，你需要登录并将 cmdlet 导入到你的本机 Windows PowerShell 会话。有关说明，请参阅[使用远程 PowerShell 连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p112">**To use the Exchange Online PowerShell cmdlets**, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
    
    <span data-ttu-id="b2c6d-143">有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-143">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
    
- <span data-ttu-id="b2c6d-p113">**验证你是否可以连接到 IMAP 服务器**。在 Exchange Online PowerShell 中运行以下命令以测试到 IMAP 服务器的连接设置。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p113">**Verify that you can connect to your IMAP server**. Run the following command in Exchange Online PowerShell to test the connection settings to your IMAP server.</span></span>
    
  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    <span data-ttu-id="b2c6d-146">对于 **Port** 参数的值，通常为未加密或传输层安全性 (TLS) 连接使用 143，为 SSL 连接使用 993。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-146">For the value of the **Port** parameter, it's typical to use 143 for unencrypted or Transport Layer Security (TLS) connections and to use 993 for SSL connections.</span></span>
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a><span data-ttu-id="b2c6d-147">步骤 2：为 IMAP 迁移批处理创建 CSV 文件</span><span class="sxs-lookup"><span data-stu-id="b2c6d-147">Step 2: Create a CSV file for an IMAP migration batch</span></span>
<span data-ttu-id="b2c6d-148"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="b2c6d-148"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="b2c6d-p114">确定 IMAP 迁移批处理中你要迁移邮箱的用户组。CSV 文件中的每一行都包含连接到 IMAP 邮件系统中邮箱所需的信息。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p114">Identify the group of users whose mailboxes you want to migrate in an IMAP migration batch. Each row in the CSV file contains information necessary to connect to a mailbox in the IMAP messaging system.</span></span>
  
<span data-ttu-id="b2c6d-151">以下是每个用户的必需特性：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-151">Here are the required attributes for each user:</span></span> 
  
- <span data-ttu-id="b2c6d-152">**EmailAddress**指定用户的 Microsoft 365 邮箱的用户 ID。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-152">**EmailAddress** specifies the user ID for the user's Microsoft 365 mailbox.</span></span>
    
- <span data-ttu-id="b2c6d-153">**UserName** 指定帐户用来访问 IMAP 服务器上邮箱的登录名。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-153">**UserName** specifies the logon name for the account to use to access the mailbox on the IMAP server.</span></span>
    
- <span data-ttu-id="b2c6d-154">**Password** 指定 **UserName** 栏内帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-154">**Password** specifies the password for the account in the **UserName** column.</span></span>
    
<span data-ttu-id="b2c6d-p115">以下是 CSV 文件格式的一个示例。在此示例中，将迁移三个邮箱：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p115">Here's an example of the format for the CSV file. In this example, three mailboxes are migrated:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

<span data-ttu-id="b2c6d-157">对于 **UserName** 属性，除了用户名以外，你还可以使用具有已分配的必要权限的帐户的凭据来访问 IMAP 服务器上的邮箱，以下是用于一些 IMAP 服务器的某些特定格式：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-157">For the **UserName** attribute, in addition to the user name, you can use the credentials of an account that has been assigned the necessary permissions to access mailboxes on the IMAP server, the following are some of the specific formats used for some of the IMAP servers:</span></span>
  
 <span data-ttu-id="b2c6d-158">**Microsoft Exchange：**</span><span class="sxs-lookup"><span data-stu-id="b2c6d-158">**Microsoft Exchange:**</span></span>
  
<span data-ttu-id="b2c6d-p116">如果从 Microsoft Exchange 的 IMAP 实现迁移电子邮件，请将格式 **Domain/Admin_UserName/User_UserName** 用于 CSV 文件中的 **UserName** 属性。假设你从 Exchange 迁移 Terry Adams、Ann Beebe 和 Paul Cannon 的电子邮件，你有一个邮件管理员帐户，其中用户名是 **mailadmin**，密码是 **P@ssw0rd**。你的 CSV 文件应如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p116">If you're migrating email from the IMAP implementation for Microsoft Exchange, use the format **Domain/Admin_UserName/User_UserName** for the **UserName** attribute in the CSV file. Let's say you're migrating email from Exchange for Terry Adams, Ann Beebe, and Paul Cannon. You have a mail administrator account, where the user name is **mailadmin** and the password is **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 <span data-ttu-id="b2c6d-163">**Dovecot：**</span><span class="sxs-lookup"><span data-stu-id="b2c6d-163">**Dovecot:**</span></span>
  
<span data-ttu-id="b2c6d-p117">对于支持简单身份验证和安全层 (SASL) 的 IMAP 服务器（如 Dovecot IMAP 服务器），使用格式 **User_UserName\*Admin_UserName**，其中星号 (\*) 为可配置的分隔符。假设你使用管理员凭据 **mailadmin** 和 **P@ssw0rd** 从 Dovecot IMAP 服务器迁移这些用户的电子邮件。你的 CSV 文件应如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p117">For IMAP servers that support Simple Authentication and Security Layer (SASL), such as a Dovecot IMAP server, use the format **User_UserName\*Admin_UserName**, where the asterisk ( \* ) is a configurable separator character. Let's say you're migrating those same users' email from a Dovecot IMAP server using the administrator credentials **mailadmin** and **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 <span data-ttu-id="b2c6d-167">**Mirapoint：**</span><span class="sxs-lookup"><span data-stu-id="b2c6d-167">**Mirapoint:**</span></span>
  
<span data-ttu-id="b2c6d-p118">如果从 Mirapoint Message Server 迁移电子邮件，请将格式 **#user@domain#Admin_UserName#** 用于管理员凭据。若要使用管理员凭据 **mailadmin** 和 **P@ssw0rd** 从 Mirapoint 迁移电子邮件，你的 CSV 文件应如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p118">If you're migrating email from Mirapoint Message Server, use the format **#user@domain#Admin_UserName#** for the administrator credentials. To migrate email from Mirapoint using the administrator credentials **mailadmin** and **P@ssw0rd**, your CSV file would look like this:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 <span data-ttu-id="b2c6d-170">**Courier IMAP：**</span><span class="sxs-lookup"><span data-stu-id="b2c6d-170">**Courier IMAP:**</span></span>
  
<span data-ttu-id="b2c6d-p119">一些源电子邮件系统（如 "宋体"）不支持使用邮箱管理员凭据将邮箱迁移到 Microsoft 365。相反，您可以将源电子邮件系统设置为使用虚拟共享文件夹。通过使用虚拟共享文件夹，您可以使用邮箱管理员凭据访问源电子邮件系统上的用户邮箱。有关如何为货运 IMAP 配置虚拟共享文件夹的详细信息，请参阅[共享文件夹](https://go.microsoft.com/fwlink/p/?LinkId=398870)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p119">Some source email systems, such as Courier IMAP, don't support using mailbox admin credentials to migrate mailboxes to Microsoft 365. Instead, you can set up your source email system to use virtual shared folders. By using virtual shared folders, you can use the mailbox admin credentials to access user mailboxes on the source email system. For more information about how to configure virtual shared folders for Courier IMAP, see [Shared Folders](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span></span>
  
<span data-ttu-id="b2c6d-p120">若要在源电子邮件系统上设置虚拟共享文件夹后迁移邮箱，你必须将可选的 **UserRoot** 属性包含在迁移文件中。此属性可指定每个用户的邮箱在源电子邮件系统上的虚拟共享文件夹结构中所处的位置。例如，指向 Terry 的邮箱的路径是 /users/terry.adams。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p120">To migrate mailboxes after you set up virtual shared folders on your source email system, you have to include the optional attribute **UserRoot** in the migration file. This attribute specifies the location of each user's mailbox in the virtual shared folder structure on the source email system. For example, the path to Terry's mailbox is /users/terry.adams.</span></span>
  
<span data-ttu-id="b2c6d-178">以下是包含 **UserRoot** 属性的 CSV 文件的示例：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-178">Here's an example of a CSV file that contains the **UserRoot** attribute:</span></span>
  
```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a><span data-ttu-id="b2c6d-179">步骤 3：创建 IMAP 迁移终结点</span><span class="sxs-lookup"><span data-stu-id="b2c6d-179">Step 3: Create an IMAP migration endpoint</span></span>
<span data-ttu-id="b2c6d-180"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="b2c6d-180"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="b2c6d-p121">若要成功迁移电子邮件，Microsoft 365 需要连接到源电子邮件系统并与之通信。为此，Microsoft 365 使用迁移终结点。迁移终结点还定义要同时迁移的邮箱数以及在增量同步期间同时同步的邮箱数（每24小时发生一次）。若要创建用于 IMAP 迁移的迁移终结点，请先[连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p121">To migrate email successfully, Microsoft 365 needs to connect to and communicate with the source email system. To do this, Microsoft 365 uses a migration endpoint. The migration endpoint also defines the number of mailboxes to migrate simultaneously and the number of mailboxes to synchronize simultaneously during incremental synchronization, which occurs once every 24 hours. To create a migration end point for IMAP migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="b2c6d-185">有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-185">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="b2c6d-186">要在 Exchange Online PowerShell 中创建名为“IMAPEndpoint”的 IMAP 迁移终结点，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-186">To create the IMAP migration endpoint called "IMAPEndpoint" in Exchange Online PowerShell, run the following command:</span></span>
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

<span data-ttu-id="b2c6d-p122">你还可以添加参数以指定并发迁移、并发增量迁移和要使用的端口。以下 Exchange Online PowerShell 命令可创建一个名为"IMAPEndpoint"的 IMAP 迁移终结点，其支持 50 个并发迁移和最多 25 个并发增量同步。还要将终结点配置为对 TLS 加密使用 143 端口。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p122">You can also add parameters to specify concurrent migrations, concurrent incremental migrations, and the port to use. The following Exchange Online PowerShell command creates an IMAP migration endpoint called "IMAPEndpoint" that supports 50 concurrent migrations and up to 25 concurrent incremental synchronizations. It also configures the endpoint to use port 143 for TLS encryption.</span></span>
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

<span data-ttu-id="b2c6d-190">有关 **New-MigrationEndpoint** cmdlet 的详细信息，请参阅[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-190">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="b2c6d-191">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="b2c6d-191">Verify it worked</span></span>

<span data-ttu-id="b2c6d-192">在 Exchange Online PowerShell 中运行以下命令来显示有关“IMAPEndpoint”的信息：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-192">Run the following command in Exchange Online PowerShell to display information about the "IMAPEndpoint":</span></span>
  
```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a><span data-ttu-id="b2c6d-193">步骤 4：创建并启动 IMAP 迁移批处理</span><span class="sxs-lookup"><span data-stu-id="b2c6d-193">Step 4: Create and start an IMAP migration batch</span></span>
<span data-ttu-id="b2c6d-194"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="b2c6d-194"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="b2c6d-p123">你可以使用 [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) cmdlet 为 IMAP 迁移创建迁移批处理。你可以通过包括 _AutoStart_ 参数来创建迁移批处理并自动启动。或者，你可以创建迁移批处理，然后通过使用[Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) cmdlet 启动它。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p123">You can use the [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) cmdlet to create a migration batch for an IMAP migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then start it afterwards by using the[Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) cmdlet.</span></span>
  
<span data-ttu-id="b2c6d-198">以下 Exchange Online PowerShell 命令会自动使用名为“IMAPEndpoint”的 IMAP 终结点来启动名为“IMAPBatch1”的迁移批处理。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-198">The following Exchange Online PowerShell command will automatically start the migration batch called "IMAPBatch1" using the IMAP endpoint called "IMAPEndpoint":</span></span>
  
```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a><span data-ttu-id="b2c6d-199">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="b2c6d-199">Verify it worked</span></span>

<span data-ttu-id="b2c6d-200">运行 [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) cmdlet 以显示有关"IMAPBatch1"的信息：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-200">Run the [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) cmdlet to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

<span data-ttu-id="b2c6d-201">你还可以通过运行以下命令，验证该批处理是否已启动：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-201">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a><span data-ttu-id="b2c6d-202">第5步：将电子邮件路由到 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="b2c6d-202">Step 5: Route your email to Microsoft 365</span></span>
<span data-ttu-id="b2c6d-203"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="b2c6d-203"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="b2c6d-p124">电子邮件系统使用称为 MX 记录的 DNS 记录来确定在何处传递电子邮件。在电子邮件迁移过程中，MX 记录指向源电子邮件系统。现在已完成将电子邮件迁移到 Microsoft 365，现在是时候将 MX 记录指向 Microsoft 365 了。这有助于确保将电子邮件传递到 Microsoft 365 邮箱。通过移动 MX 记录，您还可以在准备就绪时关闭旧的电子邮件系统。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p124">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Microsoft 365 is complete, it's time to point your MX record at Microsoft 365. This helps make sure that email is delivered to your Microsoft 365 mailboxes. By moving the MX record, you can also turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="b2c6d-p125">对于许多 DNS 提供商，有一些特定的说明可更改 MX 记录。如果不包含 DNS 提供商，或者如果您想要了解一般方向，还提供了[常规 MX 记录说明](https://go.microsoft.com/fwlink/?LinkId=397449)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p125">For many DNS providers, there are specific instructions to change your MX record. If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="b2c6d-p126">你客户和合作伙伴的电子邮件系统可能需要 72 小时才能识别更改后的 MX 记录。请等待至少 72 个小时，然后才能继续执行下一项任务：步骤 6：删除 IMAP 迁移批处理。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p126">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: Step 6: Delete IMAP migration batch.</span></span> 
  
### <a name="step-6-delete-imap-migration-batch"></a><span data-ttu-id="b2c6d-213">步骤 6：删除 IMAP 迁移批处理</span><span class="sxs-lookup"><span data-stu-id="b2c6d-213">Step 6: Delete IMAP migration batch</span></span>
<span data-ttu-id="b2c6d-214"><a name="BK_Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="b2c6d-214"><a name="BK_Step6"> </a></span></span>

<span data-ttu-id="b2c6d-p127">在更改 MX 记录并确认所有电子邮件都路由到 Microsoft 365 邮箱后，请通知用户其邮件将转到 Microsoft 365。在此之后，您可以删除 IMAP 迁移批处理。在删除迁移批处理之前验证以下各项。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p127">After you change the MX record and verify that all email is being routed to Microsoft 365 mailboxes, notify the users that their mail is going to Microsoft 365. After this, you can delete the IMAP migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="b2c6d-p128">所有用户都在使用 Microsoft 365 邮箱。删除批处理后，发送到内部部署 Exchange 服务器上的邮箱的邮件不会复制到相应的 Microsoft 365 邮箱中。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p128">All users are using Microsoft 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Microsoft 365 mailboxes.</span></span>
    
- <span data-ttu-id="b2c6d-p129">将邮件直接发送给这些邮箱后，至少已同步一次 Microsoft 365 邮箱。为此，请确保迁移批处理的 "上次同步时间" 框中的值比直接将邮件路由到 Microsoft 365 邮箱的时间更新。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-p129">Microsoft 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Microsoft 365 mailboxes.</span></span>
    
<span data-ttu-id="b2c6d-222">要从 Exchange Online PowerShell 中删除“IMAPBatch1”迁移批处理，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-222">To delete the "IMAPBatch1" migration batch from Exchange Online PowerShell, run the following command:</span></span>
  
```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

<span data-ttu-id="b2c6d-223">有关 **Remove-MigrationBatch** cmdlet 的详细信息，请参阅[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-223">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="b2c6d-224">验证它是否起作用</span><span class="sxs-lookup"><span data-stu-id="b2c6d-224">Verify it worked</span></span>

<span data-ttu-id="b2c6d-225">在 Exchange Online PowerShell 中运行以下命令来显示有关“IMAPBatch1”的信息：</span><span class="sxs-lookup"><span data-stu-id="b2c6d-225">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch IMAPBatch1"
```

<span data-ttu-id="b2c6d-226">此命令会返回状态为 **Removing** 的迁移批处理或返回错误消息，指出未找到该迁移批处理，验证该批处理已删除。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-226">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="b2c6d-227">有关 **Get-MigrationBatch** cmdlet 的详细信息，请参阅[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)。</span><span class="sxs-lookup"><span data-stu-id="b2c6d-227">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b2c6d-228">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2c6d-228">See also</span></span>

[<span data-ttu-id="b2c6d-229">IMAP 迁移故障排除程序</span><span class="sxs-lookup"><span data-stu-id="b2c6d-229">IMAP Migration Troubleshooter</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536482)

