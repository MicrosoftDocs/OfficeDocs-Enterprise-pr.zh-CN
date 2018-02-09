---
title: "使用 PowerShell 执行直接转换迁移以迁移到 Office 365"
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: "摘要：了解如何使用 Windows PowerShell 执行到 Office 365 的直接转换迁移。"
ms.openlocfilehash: 8181d59f53464034a584724dcb53956976c917dd
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a>使用 PowerShell 执行直接转换迁移以迁移到 Office 365

 **摘要：**了解如何使用 Windows PowerShell 执行直接转换迁移，以迁移到 Office 365。
  
通过直接转换迁移，您可以一次性将源电子邮件系统中用户邮箱的内容迁移到 Office 365。本文将向您介绍如何通过 Exchange Online PowerShell 执行电子邮件直接转换迁移的任务。 
  
通过查看[有关直接转换电子邮件迁移到 Office 365 您需要了解的信息](https://go.microsoft.com/fwlink/p/?LinkId=536688)主题，您可以获得迁移过程的概述。当您了解本文的内容之后，则可以借此机会开始将一个电子邮件系统中的邮箱迁移到另一个电子邮件系统。
  
> [!NOTE]
> 您还可以使用 Exchange 管理中心来执行直接转换迁移。请参阅[使用直接转换迁移将电子邮件迁移到 Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689)。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>在开始之前，您需要知道什么？

估计完成该任务的时间：2-5 分钟，用于创建迁移批处理。迁移批处理启动后，迁移的持续时间会有所不同，具体取决于批处理中邮箱的数量、每个邮箱的大小和可用网络容量。有关影响将邮箱迁移到 Office 365 所需时间的其他因素的信息，请参阅[迁移性能](https://go.microsoft.com/fwlink/p/?LinkId=275079)。
  
您必须先获得权限，然后才能执行此过程。要查看您需要哪些权限，请参阅[收件人权限](https://go.microsoft.com/fwlink/p/?LinkId=534105)主题的一个表中的"迁移"条目。
  
若要使用 Exchange Online PowerShell cmdlet，您需要登录并将 cmdlet 导入您的本地 Windows PowerShell 会话。有关说明，请参阅[使用远程 PowerShell 连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。
  
有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。
  
## <a name="migration-steps"></a>迁移步骤

### <a name="step-1-prepare-for-a-cutover-migration"></a>步骤 1：准备直接转换迁移
<a name="BK_Step1"> </a>

- **将内部部署 Exchange 组织添加为 Office 365 组织的接受域** 迁移服务使用内部部署邮箱的 SMTP 地址为新的 Office 365 邮箱创建 Microsoft Online Services 用户 ID 和电子邮件地址。如果 Exchange 域不是 Office 365 组织的接受域或主域，则迁移将失败。有关更多信息，请参阅[在 Office 365 中验证您的域](https://go.microsoft.com/fwlink/p/?LinkId=534110)。
    
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

- **为内部部署用户帐户分配访问 Exchange 组织中的邮箱所需的权限。** 用于连接到内部部署 Exchange 组织的内部部署用户帐户（也称为迁移管理员）必须拥有访问要迁移到 Office 365 的邮箱所需的权限。该用户帐户用于创建内部部署组织的迁移终结点。
    
    以下列表显示了使用直接转换迁移迁移邮箱所需的管理权限。有三个可能的选项。
    
  - 迁移管理员必须是内部部署组织的 Active Directory 中的 **Domain Admins** 组成员。
    
    或
    
  - 必须为迁移管理员分配对每个内部部署邮箱的 **FullAccess** 权限。
    
    或
    
  - 必须为迁移管理员分配对存储用户邮箱的内部部署邮箱数据库的 **代理接收**权限。
    
- **禁用统一消息。** 如果为要迁移的内部部署邮箱启用了统一消息 (UM)，则您必须先禁用这些邮箱上的 UM，然后再进行迁移。之后，您可以在完成迁移后为邮箱启用 UM。
    
- **安全组和代理** 电子邮件迁移服务无法检测本地 Active Directory 组是否为安全组，因此它无法在 Office 365 中将任何已迁移组设置为安全组。如果您希望在 Office 365 租户中拥有安全组，必须首先在 Office 365 租户中设置一个空的启用了邮件的安全组，然后再开始直接转换迁移。此外，此迁移方法仅移动邮箱、邮箱用户、邮箱联系人和启用了邮件的组。如果已将任何其他 Active Directory 对象（如未迁移到 Office 365 的用户）作为管理员或代理分配给要迁移的对象，则必须在迁移之前将其从对象中删除。
    
### <a name="step-2-create-a-migration-endpoint"></a>步骤 2：创建迁移终结点
<a name="BK_Step2"> </a>

要成功迁移电子邮件，Office 365 需要与源电子邮件系统连接和通信。为此，Office 365 可使用迁移终结点。要创建适用于直接转换迁移的 Outlook 无处不在迁移终结点，首先[连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。 
  
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

### <a name="step-5-route-your-email-to-office-365"></a>步骤 5：将您的电子邮件路由到 Office 365
<a name="BK_Step5"> </a>

电子邮件系统使用名为 MX 记录的 DNS 记录找出传递电子邮件的位置。在电子邮件迁移过程中，您的 MX 记录会指向您的源电子邮件系统。现在电子邮件迁移到 Office 365 已完成，可以在 Office 365 中指向您的 MX 记录。这可以帮助您确保该电子邮件已传递到您的 Office 365 邮箱。通过移动 MX 记录，您还可以在准备就绪的时候关闭旧的电子邮件系统。 
  
对于很多 DNS 提供商而言，[更改您的 MX 记录](https://go.microsoft.com/fwlink/p/?LinkId=279163)需要遵循特定的说明。如果您的 DNS 提供商不包括在内或您要获取统一指导，我们也会提供 [MX 记录的统一说明](https://go.microsoft.com/fwlink/?LinkId=397449)。
  
您客户和合作伙伴的电子邮件系统可能需要 72 小时才能识别更改后的 MX 记录。请等待至少 72 个小时，然后才能继续执行下一项任务： [步骤 6：删除直接转换迁移批处理](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>步骤 6：删除直接转换迁移批处理
<a name="Bk_step6"> </a>

更改 MX 记录并验证所有电子邮件已路由到 Office 365 邮箱以后，通知用户他们的邮件已进入到 Office 365。此后，您可以删除直接转换迁移批处理。在删除迁移批处理之前验证以下内容。
  
- 所有用户正在使用 Office 365 邮箱。删除该批处理后，发送到内部部署 Exchange Server 中邮箱的邮件将不会复制到相应的 Office 365 邮箱。
    
- 当邮件开始直接发送到 Office 365 邮箱以后，这些邮箱至少会同步一次。为此，确保迁移批处理的"上次同步时间"框中的值是最近时间，而不是邮件开始直接路由到 Office 365 邮箱的时间。
    
要在 Exchange Online PowerShell 中删除“CutoverBatch”迁移批处理，请运行以下命令：
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>第 7 部分：分配用户许可证
<a name="BK_Step7"> </a>

 **通过分配许可证，激活迁移后帐户的 Office 365 用户帐户。**如果您不分配许可证，则在宽限期（30 天）结束后将禁用该邮箱。若要在 Office 365 管理中心 中分配许可证，请参阅[为 Office 365 商业版分配或取消分配许可证](https://go.microsoft.com/fwlink/?LinkId=536681)。
  
### <a name="step-8-complete-post-migration-tasks"></a>步骤 8：完成迁移后任务
<a name="BK_Step8"> </a>

- **创建自动发现 DNS 记录，以便用户可以轻松地访问他们的邮箱。**所有内部部署邮箱都迁移到 Office 365 以后，您可以为您的 Office 365 组织配置自动发现 DNS 记录，使用户可以轻松地使用 Outlook 和移动客户端连接到他们的新 Office 365 邮箱。此新自动发现 DNS 记录必须使用对 Office 365 组织使用的相同命名空间。例如，如果您基于云的命名空间是 cloud.contoso.com，则您需要创建的自动发现 DNS 记录是 autodiscover.cloud.contoso.com。
    
    如果您保留 Exchange Server，则还应确保在迁移后自动发现 DNS CNAME 记录必须在内部和外部 DNS 中指向 Office 365，以便 Outlook 客户端能够连接到正确的邮箱。
    
    > [!NOTE]
    >  在 Exchange 2007、Exchange 2010 和 Exchange 2013 中，您还应将  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` 设置为 `Null`。 
  
    Office 365 使用 CNAME 记录为 Outlook 和移动客户端实现自动发现服务。自动发现 CNAME 记录必须包含以下信息：
    
  - **别名：**autodiscover
    
  - **目标：**autodiscover.outlook.com
    
    有关更多信息，请参阅[管理 DNS 记录时为 Office 365 创建 DNS 记录](https://go.microsoft.com/fwlink/p/?LinkId=535028)。
    
- **停止使用内部部署 Exchange 服务器。**当您验证所有电子邮件都可以直接被路由到 Office 365 邮箱，并且您不再需要维护内部部署电子邮件组织或不用计划实施单点登录 (SSO) 解决方案以后，您可以从服务器中卸载 Exchange 并删除内部部署 Exchange 组织。
    
    有关详细信息，请参阅以下资源：
    
  - [修改或删除 Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [如何删除 Exchange 2007 组织](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [如何卸载 Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

