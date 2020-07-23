---
title: 使用 PowerShell 执行到 Microsoft 365 的直接转换迁移
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
description: 摘要：了解如何使用 Windows PowerShell 执行到 Microsoft 365 的直接转换迁移。
ms.openlocfilehash: 203c041e0bd5fe58d697d074e94b749726bb22bf
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229846"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>使用 PowerShell 执行到 Microsoft 365 的直接转换迁移

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

您可以通过使用直接转换迁移将用户邮箱的内容从源电子邮件系统迁移到 Microsoft 365。 本文将向您介绍如何通过 Exchange Online PowerShell 执行电子邮件直接转换迁移的任务。 
  
通过查看主题，[您需要了解有关直接转换将电子邮件迁移到 Microsoft 365 的内容](https://go.microsoft.com/fwlink/p/?LinkId=536688)，您可以获取迁移过程的概述。 当您了解本文的内容之后，则可以借此机会开始将一个电子邮件系统中的邮箱迁移到另一个电子邮件系统。
  
> [!NOTE]
> 您还可以使用 Exchange 管理中心来执行直接转换迁移。 请参阅[执行将电子邮件迁移到 Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536689)的转换。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>在开始之前，您需要知道什么？

估计完成该任务的时间：2-5 分钟，用于创建迁移批处理。 迁移批处理启动后，迁移的持续时间会有所不同，具体取决于批处理中邮箱的数量、每个邮箱的大小和可用网络容量。 有关影响将邮箱迁移到 Microsoft 365 所需时间的其他因素的信息，请参阅[迁移性能](https://go.microsoft.com/fwlink/p/?LinkId=275079)。
  
你必须先获得权限，然后才能执行此过程。要查看你需要哪些权限，请参阅[收件人权限](https://go.microsoft.com/fwlink/p/?LinkId=534105)主题的一个表中的"迁移"条目。
  
若要使用 Exchange Online PowerShell cmdlet，你需要登录并将 cmdlet 导入你的本地 Windows PowerShell 会话。有关说明，请参阅[使用远程 PowerShell 连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。
  
有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。
  
## <a name="migration-steps"></a>迁移步骤

### <a name="step-1-prepare-for-a-cutover-migration"></a>步骤 1：准备直接转换迁移
<a name="BK_Step1"> </a>

- **将您的本地 Exchange 组织添加为 Microsoft 365 组织的接受域。** 迁移服务使用本地邮箱的 SMTP 地址为新的 Microsoft 365 邮箱创建 Microsoft Online Services 用户 ID 和电子邮件地址。 如果您的 Exchange 域不是您的 Microsoft 365 组织的接受域或主域，迁移将失败。 有关详细信息，请参阅[验证您的域](https://go.microsoft.com/fwlink/p/?LinkId=534110)。
    
- **在内部部署 Exchange 服务器上配置 Outlook 无处不在。** 电子邮件迁移服务使用 RPC over HTTP 或 Outlook 无处不在连接到内部部署 Exchange 服务器。有关如何设置 Outlook 无处不在 for Exchange 2010、Exchange 2007 和 Exchange 2003 的信息，请参阅以下内容：
    
  - [Exchange 2010:启用 Outlook 无处不在](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [Exchange 2007:如何启用 Outlook 无处不在](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [Exchange 2003:RPC over HTTP 的部署方案](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [如何使用 Exchange 2003 配置 Outlook 无处不在](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > 必须使用受信任的证书颁发机构 (CA) 颁发的证书配置 Outlook 无处不在配置。不能使用自签名证书配置它。有关详细信息，请参阅[如何为 Outlook 无处不在配置 SSL](https://go.microsoft.com/fwlink/?LinkID=80875)。 
  
- **确认是否可以使用 Outlook 无处不在连接到 Exchange 组织。** 尝试以下这些方法之一来测试连接设置：
    
  - 使用 Microsoft Outlook 从企业网络外部连接到内部部署 Exchange 邮箱。
    
  - 使用 Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) 测试连接设置。使用 Outlook 无处不在 (RPC over HTTP) 或 Outlook 自动发现测试。
    
  - 在 Exchange Online PowerShell 中运行以下命令。
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **为内部部署用户帐户分配访问 Exchange 组织中的邮箱所需的权限。** 用于连接到内部部署 Exchange 组织的本地用户帐户（也称为迁移管理员）必须具有访问要迁移到 Microsoft 365 的本地邮箱的必要权限。。 该用户帐户用于创建内部部署组织的迁移终结点。
    
    以下列表显示了使用直接转换迁移迁移邮箱所需的管理权限。有三个可能的选项。
    
  - 迁移管理员必须是内部部署组织的 Active Directory 中的 **Domain Admins** 组成员。
    
    或
    
  - 必须为迁移管理员分配对每个内部部署邮箱的 **FullAccess** 权限。
    
    或
    
  - 必须为迁移管理员分配对存储用户邮箱的内部部署邮箱数据库的 **代理接收**权限。
    
- **禁用统一消息。** 如果为要迁移的内部部署邮箱启用了统一消息 (UM)，则您必须先禁用这些邮箱上的 UM，然后再进行迁移。之后，您可以在完成迁移后为邮箱启用 UM。
    
- **安全组和代理**电子邮件迁移服务无法检测本地 Active Directory 组是否为安全组，因此无法将任何迁移的组配置为 Microsoft 365 中的安全组。 如果您希望在 Microsoft 365 租户中拥有安全组，则必须先在 Microsoft 365 租户中设置一个空的已启用邮件的安全组，然后才能开始直接转换迁移。 此外，此迁移方法仅移动邮箱、邮件用户、邮件联系人和启用邮件的组。 如果有任何其他 Active Directory 对象（例如未迁移到 Microsoft 365 的用户）被分配为要迁移的对象的管理员或委派，则必须在迁移之前将其从对象中删除。
    
### <a name="step-2-create-a-migration-endpoint"></a>步骤 2：创建迁移终结点
<a name="BK_Step2"> </a>

若要成功迁移电子邮件，Microsoft 365 需要连接源电子邮件系统并与之通信。 为此，Microsoft 365 使用迁移终结点。 要创建适用于直接转换迁移的 Outlook 无处不在迁移终结点，首先[连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。 
  
有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。
  
在 Exchange Online PowerShell 中运行以下命令：
  
```
$Credentials = Get-Credential
```

该示例使用 [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet 获取并测试对内部部署 Exchange 服务器的连接设置，然后使用这些连接设置来创建名为"CutoverEndpoint"的迁移终结点。
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> 可以使用 **New-MigrationEndpoint** cmdlet 指定服务要通过 **-TargetDatabase** 选项使用的数据库。在其他情况下，系统会从管理邮箱所在的 Active Directory 联合身份验证服务 (AD FS) 2.0 站点中随机分配数据库。
  
#### <a name="verify-it-worked"></a>验证它是否起作用

在 Exchange Online PowerShell 中，运行以下命令来显示有关“CutoverEndpoint”迁移终结点的信息：
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>步骤 3：创建直接转换迁移批处理
<a name="BK_Step3"> </a>

您可以在 Exchange Online PowerShell 中使用 **New-MigrationBatch** cmdlet 为直接转换迁移创建迁移批处理。您可以通过包括 _AutoStart_ 参数来创建迁移批处理并自动启动。或者，您可以通过使用 **Start-MigrationBatch** cmdlet 创建迁移批处理，然后手动启动。此示例创建名为"CutoverBatch"的迁移批处理并使用之前步骤中创建的迁移终结点。
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

此示例还会创建名为"CutoverBatch"的迁移批处理并使用之前步骤中创建的迁移终结点。由于未包括  _AutoStart_ 参数，因此必须在迁移主控板中手动启动迁移批处理或者通过使用 **Start-MigrationBatch** cmdlet 手动启动迁移批处理。如前所述，一次只能存在一个直接转换迁移批处理。
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>验证它是否起作用

要验证您是否已成功为直接转换迁移创建了迁移批处理，请在 Exchange Online PowerShell 中运行以下命令来显示有关新迁移批处理的信息：
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>步骤 4：启动直接转换迁移批处理
<a name="BK_Step4"> </a>

要在 Exchange Online PowerShell 中启动迁移批处理，请运行以下命令。这将创建名为“CutoverBatch”的迁移批处理。
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>验证它是否起作用

如果迁移批处理已成功启动，其在迁移主控板中的状态指定为“正在同步”。要验证您是否已通过 Exchange Online PowerShell 成功启动迁移批处理，请运行以下命令：
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>第5步：将电子邮件路由到 Microsoft 365
<a name="BK_Step5"> </a>

电子邮件系统使用称为 MX 记录的 DNS 记录来查明电子邮件的传递位置。 在电子邮件迁移过程中，MX 记录指向您的源电子邮件系统。 现在已完成将电子邮件迁移到 Microsoft 365，现在是时候将 MX 记录指向 Microsoft 365 了。 这有助于确保将电子邮件传递到 Microsoft 365 邮箱。 通过移动 MX 记录，您还可以在准备就绪的时候关闭旧的电子邮件系统。 
  
对于很多 DNS 提供商而言，[更改你的 MX 记录](https://go.microsoft.com/fwlink/p/?LinkId=279163)需要遵循特定的说明。如果你的 DNS 提供商不包括在内或你要获取统一指导，我们也会提供 [MX 记录的统一说明](https://go.microsoft.com/fwlink/?LinkId=397449)。
  
您客户和合作伙伴的电子邮件系统可能需要 72 小时才能识别更改后的 MX 记录。请等待至少 72 个小时，然后才能继续执行下一项任务： [步骤 6：删除直接转换迁移批处理](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>步骤 6：删除直接转换迁移批处理
<a name="Bk_step6"> </a>

在更改 MX 记录并确认所有电子邮件都路由到 Microsoft 365 邮箱后，请通知用户其邮件将转到 Microsoft 365。 此后，您可以删除直接转换迁移批处理。 在删除迁移批处理之前验证以下内容。
  
- 所有用户都在使用 Microsoft 365 邮箱。 删除批处理后，发送到内部部署 Exchange 服务器上的邮箱的邮件不会复制到相应的 Microsoft 365 邮箱中。
    
- 将邮件直接发送给这些邮箱后，至少已同步一次 Microsoft 365 邮箱。 为此，请确保迁移批处理的 "上次同步时间" 框中的值比直接将邮件路由到 Microsoft 365 邮箱的时间更新。
    
要在 Exchange Online PowerShell 中删除“CutoverBatch”迁移批处理，请运行以下命令：
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>第 7 部分：分配用户许可证
<a name="BK_Step7"> </a>

 **通过分配许可证为迁移的帐户激活 Microsoft 365 用户帐户。** 如果不分配许可证，则当宽限期（30 天）结束时，邮箱将处于禁用状态。 若要在 Microsoft 365 管理中心中分配许可证，请参阅[分配或取消分配许可证](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)。
  
### <a name="step-8-complete-post-migration-tasks"></a>步骤 8：完成迁移后任务
<a name="BK_Step8"> </a>

- **创建自动发现 DNS 记录，以便用户可以轻松地访问他们的邮箱。** 在将所有内部部署邮箱迁移到 Microsoft 365 之后，可以为 Microsoft 365 组织配置自动发现 DNS 记录，使用户可以使用 Outlook 和移动客户端轻松连接到其新的 Microsoft 365 邮箱。 这一新的自动发现 DNS 记录必须使用您的 Microsoft 365 组织所使用的相同命名空间。 例如，如果您的基于云的命名空间是 cloud.contoso.com，那么您需要创建的自动发现 DNS 记录是 autodiscover.cloud.contoso.com。
    
    如果保留 Exchange Server，还应确保在迁移后，自动发现 DNS CNAME 记录必须指向内部和外部 DNS 中的 Microsoft 365，这样 Outlook 客户端才能连接到正确的邮箱。
    
    > [!NOTE]
    >  在 Exchange 2007、Exchange 2010 和 Exchange 2013 中，您还应将  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` 设置为 `Null`。 
  
    Microsoft 365 使用 CNAME 记录来实现 Outlook 和移动客户端的自动发现服务。 自动发现 CNAME 记录必须包含以下信息：
    
  - **别名：** autodiscover
    
  - **目标：** autodiscover.outlook.com
    
    有关详细信息，请参阅[添加 DNS 记录以连接到您的域](https://go.microsoft.com/fwlink/p/?LinkId=535028)。
    
- **停止使用内部部署 Exchange 服务器。** 确认所有电子邮件都直接路由到 Microsoft 365 邮箱，并且不再需要维护内部部署电子邮件组织或未计划实施单一登录（SSO）解决方案时，可以从服务器中卸载 Exchange 并删除内部部署 Exchange 组织。
    
    有关详细信息，请参阅以下资源：
    
  - [修改或删除 Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [如何删除 Exchange 2007 组织](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [如何卸载 Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

