---
title: "使用 PowerShell 执行将 IMAP 迁移到 Office 365"
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
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: "摘要：了解如何使用 Windows PowerShell 执行到 Office 365 的 IMAP 迁移。"
ms.openlocfilehash: 6187207d57723c9c69fa6fdc7885c91de6d5080f
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="use-powershell-to-perform-an-imap-migration-to-office-365"></a>使用 PowerShell 执行将 IMAP 迁移到 Office 365

 **摘要：**了解如何使用 Windows PowerShell 执行 IMAP 迁移，以迁移到 Office 365。
  
作为部署 Office 365 的过程的一部分，您可以选择将 Internet 邮件访问协议 (IMAP) 电子邮件服务中用户邮箱的内容迁移到 Office 365。本文将向您介绍如何通过 Exchange Online PowerShell 执行电子邮件 IMAP 迁移的任务。 
  
> [!NOTE]
> 您还可以使用 Exchange 管理中心来执行 IMAP 迁移。请参阅[将您的 IMAP 邮箱迁移到 Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536685)。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>在开始之前，您需要知道什么？

估计完成该任务的时间：2-5 分钟，用于创建迁移批处理。迁移批处理启动后，迁移的持续时间会有所不同，具体取决于批处理中邮箱的数量、每个邮箱的大小和可用网络容量。有关影响将邮箱迁移到 Office 365 所需时间的其他因素的信息，请参阅[迁移性能](https://go.microsoft.com/fwlink/p/?LinkId=275079)。
  
您必须先获得权限，然后才能执行此过程。要查看您需要哪些权限，请参阅[收件人权限](https://go.microsoft.com/fwlink/p/?LinkId=534105)主题的一个表中的"迁移"条目。
  
若要使用 Exchange Online PowerShell cmdlet，您需要登录并将 cmdlet 导入您的本地 Windows PowerShell 会话。有关说明，请参阅[使用远程 PowerShell 连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。
  
有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。
  
以下限制适用于 IMAP 迁移：
  
- 只有在用户收件箱或其他邮件文件夹中的项目才会被迁移。您不能迁移联系人、日历项目或任务。
    
- 最多可以从用户邮箱迁移 500,000 个项目。
    
- 能够迁移的邮件最大大小为 35 MB。
    
## <a name="migration-steps"></a>迁移步骤

### <a name="step-1-prepare-for-an-imap-migration"></a>步骤 1：准备 IMAP 迁移
<a name="BK_Step1"> </a>

- **如果您有一个域用于 IMAP 组织，请将其添加为 Office 365 组织的接受域。**如果您要为 Office 365 邮箱使用已有的相同域，则首先需要将其作为接受域添加到 Office 365。添加域以后，您可以在 Office 365 中创建您的用户。有关更多信息，请参阅[在 Office 365 中验证您的域](https://go.microsoft.com/fwlink/p/?LinkId=534110)。
    
- **将每个用户添加到 Office 365，以便于他们都拥有一个 Office 365 邮箱。**有关说明，请参阅[向 Office 365 for Business 中添加用户](https://go.microsoft.com/fwlink/p/?LinkId=535065)。
    
- **获取 IMAP 服务器的 FQDN**。在创建 IMAP 迁移终结点时，您需要提供从中迁移邮箱数据的 IMAP 服务器的完全限定域名 (FQDN)（也称为完整的计算机名称）。可使用 IMAP 客户端或 PING 命令来验证您能否使用此 FQDN 通过 Internet 与 IMAP 服务器进行通信。
    
- **配置防火墙以允许 IMAP 连接**。您可能必须打开托管 IMAP 服务器的组织的防火墙中的端口，以便于迁移期间来自 Microsoft 数据中心的网络通信被允许进入托管 IMAP 服务器的组织。有关 Microsoft 数据中心使用的 IP 地址列表，请参阅 [Exchange Online URL 和 IP 地址范围](https://go.microsoft.com/fwlink/p/?LinkId=535066)。
    
- **分配管理员帐户权限以访问 IMAP 组织中的邮箱**。如果您在 CSV 文件中使用管理员凭据，则您使用的帐户必须具有必要的权限才能访问内部部署邮箱。访问用户邮箱所需的权限将由特定的 IMAP 服务器决定。 
    
- **要使用 Exchange Online PowerShell cmdlet**，您需要登录并将 cmdlet 导入到您的本机 Windows PowerShell 会话。有关说明，请参阅[使用远程 PowerShell 连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。
    
    有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。
    
- **验证您是否可以连接到 IMAP 服务器**。在 Exchange Online PowerShell 中运行以下命令以测试到 IMAP 服务器的连接设置。
    
  ```
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    对于 **Port** 参数的值，通常为未加密或传输层安全性 (TLS) 连接使用 143，为 SSL 连接使用 993。
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>步骤 2：为 IMAP 迁移批处理创建 CSV 文件
<a name="BK_Step2"> </a>

确定 IMAP 迁移批处理中您要迁移邮箱的用户组。CSV 文件中的每一行都包含连接到 IMAP 邮件系统中邮箱所需的信息。
  
以下是每个用户的必需特性： 
  
- **EmailAddress** 指定用户的 Office 365 邮箱的用户 ID。
    
- **UserName** 指定帐户用来访问 IMAP 服务器上邮箱的登录名。
    
- **Password** 指定 **UserName** 栏内帐户的密码。
    
以下是 CSV 文件格式的一个示例。在此示例中，将迁移三个邮箱：
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

对于 **UserName** 属性，除了用户名以外，您还可以使用具有已分配的必要权限的帐户的凭据来访问 IMAP 服务器上的邮箱，以下是用于一些 IMAP 服务器的某些特定格式：
  
 **Microsoft Exchange：**
  
如果从 Microsoft Exchange 的 IMAP 实现迁移电子邮件，请将格式 **Domain/Admin_UserName/User_UserName** 用于 CSV 文件中的 **UserName** 属性。假设您从 Exchange 迁移 Terry Adams、Ann Beebe 和 Paul Cannon 的电子邮件，您有一个邮件管理员帐户，其中用户名是 **mailadmin** ，密码是 **P@ssw0rd** 。您的 CSV 文件应如下所示：
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot：**
  
对于支持简单身份验证和安全层 (SASL) 的 IMAP 服务器（如 Dovecot IMAP 服务器），使用格式 **User_UserName*Admin_UserName** ，其中星号 ( * ) 为可配置的分隔符。假设您要使用管理员凭据 **mailadmin** 和 **P@ssw0rd** 从 Dovecot IMAP 服务器迁移这些用户的电子邮件。您的 CSV 文件应如下所示：
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint：**
  
如果从 Mirapoint Message Server 迁移电子邮件，请将格式 **#user@domain#Admin_UserName#** 用于管理员凭据。若要使用管理员凭据 **mailadmin** 和 **P@ssw0rd** 从 Mirapoint 迁移电子邮件，您的 CSV 文件应如下所示：
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP：**
  
Courier IMAP 等一些源电子邮件系统不支持使用邮箱管理员凭据将邮箱迁移到 Office 365。相反，您可以将源电子邮件系统设置为使用虚拟共享文件夹。通过使用虚拟共享文件夹，您可以使用邮箱管理员凭据来访问源电子邮件系统上的用户邮箱。有关如何配置 Courier IMAP 的虚拟共享文件夹的详细信息，请参阅[共享文件夹](https://go.microsoft.com/fwlink/p/?LinkId=398870)。
  
若要在源电子邮件系统上设置虚拟共享文件夹后迁移邮箱，您必须将可选的 **UserRoot** 属性包含在迁移文件中。此属性可指定每个用户的邮箱在源电子邮件系统上的虚拟共享文件夹结构中所处的位置。例如，指向 Terry 的邮箱的路径是 /users/terry.adams。
  
以下是包含 **UserRoot** 属性的 CSV 文件的示例：
  
```
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>步骤 3：创建 IMAP 迁移终结点
<a name="BK_Step3"> </a>

要成功迁移电子邮件，Office 365 需要与源电子邮件系统连接和通信。为此，Office 365 可使用迁移终结点。迁移终结点还定义同时迁移的邮箱数和每 24 小时执行一次的增量同步过程中同时同步的邮箱数。要创建用于 IMAP 迁移的迁移终结点，首先[连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。 
  
有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。
  
要在 Exchange Online PowerShell 中创建名为“IMAPEndpoint”的 IMAP 迁移终结点，运行以下命令：
  
```
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

您还可以添加参数以指定并发迁移、并发增量迁移和要使用的端口。以下 Exchange Online PowerShell 命令可创建一个名为"IMAPEndpoint"的 IMAP 迁移终结点，其支持 50 个并发迁移和最多 25 个并发增量同步。还要将终结点配置为对 TLS 加密使用 143 端口。
  
```
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

有关 **New-MigrationEndpoint** cmdlet 的详细信息，请参阅[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)。
  
#### <a name="verify-it-worked"></a>验证它是否起作用

在 Exchange Online PowerShell 中运行以下命令来显示有关“IMAPEndpoint”的信息：
  
```
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>步骤 4：创建并启动 IMAP 迁移批处理
<a name="BK_Step4"> </a>

您可以使用 [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) cmdlet 为 IMAP 迁移创建迁移批处理。您可以通过包括 _AutoStart_ 参数来创建迁移批处理并自动启动。或者，您可以创建迁移批处理，然后通过使用[Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) cmdlet 启动它。
  
以下 Exchange Online PowerShell 命令会自动使用名为“IMAPEndpoint”的 IMAP 终结点来启动名为“IMAPBatch1”的迁移批处理。
  
```
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\\Users\\Administrator\\Desktop\\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>验证它是否起作用

运行 [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) cmdlet 以显示有关"IMAPBatch1"的信息：
  
```
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

您还可以通过运行以下命令，验证该批处理是否已启动：
  
```
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a>步骤 5：将您的电子邮件路由到 Office 365
<a name="BK_Step5"> </a>

电子邮件系统使用名为 MX 记录的 DNS 记录找出传递电子邮件的位置。在电子邮件迁移过程中，您的 MX 记录会指向您的源电子邮件系统。现在电子邮件迁移到 Office 365 已完成，可以在 Office 365 中指向您的 MX 记录。这可以帮助您确保该电子邮件已传递到您的 Office 365 邮箱。通过移动 MX 记录，您还可以在准备就绪的时候关闭旧的电子邮件系统。 
  
对于很多 DNS 提供商而言，[更改您的 MX 记录](https://go.microsoft.com/fwlink/p/?LinkId=279163)需要遵循特定的说明。如果您的 DNS 提供商不包括在内或您要获取统一指导，我们也会提供 [MX 记录的统一说明](https://go.microsoft.com/fwlink/?LinkId=397449)。
  
您客户和合作伙伴的电子邮件系统可能需要 72 小时才能识别更改后的 MX 记录。请等待至少 72 个小时，然后才能继续执行下一项任务：步骤 6：删除 IMAP 迁移批处理。 
  
### <a name="step-6-delete-imap-migration-batch"></a>步骤 6：删除 IMAP 迁移批处理
<a name="BK_Step6"> </a>

更改 MX 记录并验证所有电子邮件已路由到 Office 365 邮箱以后，通知用户他们的邮件已进入到 Office 365。此后，您可以删除 IMAP 迁移批处理。在删除迁移批处理之前验证以下内容。
  
- 所有用户正在使用 Office 365 邮箱。删除该批处理后，发送到内部部署 Exchange Server 中邮箱的邮件将不会复制到相应的 Office 365 邮箱。
    
- 当邮件开始直接发送到 Office 365 邮箱以后，这些邮箱至少会同步一次。为此，确保迁移批处理的"上次同步时间"框中的值是最近时间，而不是邮件开始直接路由到 Office 365 邮箱的时间。
    
要从 Exchange Online PowerShell 中删除“IMAPBatch1”迁移批处理，请运行以下命令：
  
```
Remove-MigrationBatch -Identity IMAPBatch1
```

有关 **Remove-MigrationBatch** cmdlet 的详细信息，请参阅[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)。
  
#### <a name="verify-it-worked"></a>验证它是否起作用

在 Exchange Online PowerShell 中运行以下命令来显示有关“IMAPBatch1”的信息：
  
```
Get-MigrationBatch IMAPBatch1"
```

此命令会返回状态为 **Removing** 的迁移批处理或返回错误消息，指出未找到该迁移批处理，验证该批处理已删除。
  
有关 **Get-MigrationBatch** cmdlet 的详细信息，请参阅[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)。
  
## <a name="see-also"></a>另请参阅

#### 

[IMAP 迁移故障排除程序](https://go.microsoft.com/fwlink/p/?LinkId=536482)

