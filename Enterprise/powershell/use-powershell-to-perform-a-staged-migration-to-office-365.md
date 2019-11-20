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
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 摘要：了解如何使用 Windows PowerShell 执行到 Office 365 的暂存迁移。
ms.openlocfilehash: d60145c7dd25fc7cf6be51a891b8fae8e67ccc2b
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747528"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a>使用 PowerShell 执行暂存迁移以迁移到 Office 365

随着时间的推移，您可以使用暂存迁移将源电子邮件系统中用户邮箱的内容迁移到 Office 365。
  
本文将向您介绍涉及到使用 Exchange Online PowerShell 进行暂存电子邮件迁移的任务。[有关使用暂存迁移将电子邮件迁移到 Office 365 的注意事项](https://go.microsoft.com/fwlink/p/?LinkId=536487)主题向您提供了迁移过程的概述。当您了解本文的内容之后，则可以借此机会开始将一个电子邮件系统中的邮箱迁移到另一个电子邮件系统。
  
> [!NOTE]
> 您还可以使用 Exchange 管理中心来执行暂存迁移。请参阅[使用暂存迁移将电子邮件迁移到 Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687)。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>在开始之前，您需要知道什么？

估计完成该任务的时间：2-5 分钟，用于创建迁移批处理。迁移批处理启动后，迁移的持续时间会有所不同，具体取决于批处理中邮箱的数量、每个邮箱的大小和可用网络容量。有关影响将邮箱迁移到 Office 365 所需时间的其他因素的信息，请参阅[迁移性能](https://go.microsoft.com/fwlink/p/?LinkId=275079)。
  
您必须先获得权限，然后才能执行此过程。要查看您需要哪些权限，请参阅[收件人权限](https://go.microsoft.com/fwlink/p/?LinkId=534105)主题中的"迁移"条目。
  
若要使用 Exchange Online PowerShell cmdlet，您需要登录并将 cmdlet 导入您的本地 Windows PowerShell 会话。有关说明，请参阅[使用远程 PowerShell 连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。
  
有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。
  
## <a name="migration-steps"></a>迁移步骤

### <a name="step-1-prepare-for-a-staged-migration"></a>步骤 1：准备暂存迁移

在开始通过暂存迁移将邮箱迁移到 Office 365 之前，您必须对您的 Exchange 环境进行几处更改。
  
 **在您的内部部署 Exchange Server 上配置 Outlook 无处不在** 电子邮件迁移服务使用 Outlook 无处不在（也称为 RPC over HTTP）连接到您的内部部署 Exchange Server。有关如何为 Exchange Server 2007 和 Exchange 2003 设置 Outlook 无处不在 设置的信息，请参阅以下内容：
  
- [Exchange 2007:如何启用 Outlook 无处不在](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [如何使用 Exchange 2003 配置 Outlook 无处不在](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> 您必须在 Outlook 无处不在 配置中使用受信任的证书颁发机构 (CA) 颁发的证书。Outlook 无处不在 不能通过自签名的证书进行配置。有关详细信息，请参阅[如何为 Outlook 无处不在配置 SSL](https://go.microsoft.com/fwlink/?LinkID=80875)。 
  
 **可选：确认您是否可以使用 Outlook 无处不在 连接到 Exchange 组织** 使用下列方法之一来测试您的连接设置。
  
- 使用公司网络外部的 Outlook 连接到您的内部部署 Exchange 邮箱。
    
- 使用 [Microsoft Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) 测试连接设置。使用 Outlook 无处不在 (RPC over HTTP) 或 Outlook 自动发现测试。
    
- 在 Exchange Online PowerShell 中运行以下命令：
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **设置权限** 您用于连接到内部部署 Exchange 组织的内部部署用户帐户（也称为迁移管理员）必须拥有必要的权限才能访问您要迁移到 Office 365 的内部部署邮箱。当您稍后在本过程（[步骤 3：创建迁移终结点](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint)）中通过创建迁移终结点来连接到您的电子邮件系统时，需要使用此用户帐户。
  
要迁移邮箱，管理员必须拥有以下权限集之一：
  
- 内部部署组织中 Active Directory 中的 **Domain Admins** 组成员。
    
    或
    
- 分配了对每个内部部署邮箱的 **FullAccess** 权限以及可修改内部部署用户帐户上的 **TargetAddress** 属性的 **WriteProperty** 权限。
    
    或
    
- 分配了对存储用户邮箱的内部部署邮箱数据库上的 **Receive As** 权限以及可修改内部部署用户帐户上的 **TargetAddress** 属性的 **WriteProperty** 权限。
    
有关如何设置这些权限的说明，请参阅[分配权限以将邮箱迁移到 Office 365](https://go.microsoft.com/fwlink/?LinkId=521656)。
  
 **禁用统一消息 (UM)** 如果您要迁移的内部部署邮箱上开启了 UM，请先将其关闭，然后再执行迁移。迁移完成以后，打开邮箱的 UM。有关具体的操作方法步骤，请参阅[禁用统一消息](https://go.microsoft.com/fwlink/?LinkId=521891)。
  
 **使用目录同步在 Office 365 中新建用户。** 您可以使用目录同步在您的 Office 365 组织中创建所有内部部署用户。
  
创建用户以后，您需要对他们授予许可。您可以在创建用户之后的 30 天内添加许可证。有关添加许可证的步骤，请参阅[步骤 8：完成迁移后任务](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration)。
  
 您可以使用 Microsoft Azure Active Directory 同步工具或 Microsoft Azure Active Directory 同步服务（AAD 同步）来同步并在 Office 365 中创建您的内部部署用户。当邮箱被迁移到 Office 365 之后，您可以在内部部署组织中管理用户帐户，而且它们会与 Office 365 组织同步。有关更多信息，请参阅[目录集成](https://go.microsoft.com/fwlink/?LinkId=521788)。
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>步骤 2：为暂存迁移批处理创建 CSV 文件

确定您要将其内部部署邮箱迁移到 Office 365 的用户之后，您可以使用逗号分隔值 (CSV) 文件来创建迁移批处理。Office 365 用于运行迁移的 CSV 文件中的每一行都包含有关内部部署邮箱的信息。 
  
> [!NOTE]
> 对于使用暂存迁移来迁移到 Office 365 的邮箱数没有限制。迁移批处理的 CSV 文件最多可包含 2,000 行。若要迁移 2000 个以上邮箱，请创建额外的 CSV 文件并使用每个文件来创建新的迁移批处理。 
  
 **支持的属性**
  
暂存迁移的 CSV 文件支持下列三个属性。CSV 文件中的每一行对应于一个邮箱并且必须包含属性的相应值。
  
|**属性**|**说明**|**是否必需？**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |为内部部署邮箱指定一个主要的 SMTP 电子邮件地址，例如，pilarp@contoso.com。  <br/> 为内部部署邮箱使用该主要的 SMTP 地址，而非 Office 365 中的用户 ID。例如，如果将内部部署域命名为 contoso.com，但是将 Office 365 电子邮件域命名为 service.contoso.com，则您应该为 CSV 文件中的电子邮件地址使用 contoso.com 域名。  <br/> |必需  <br/> |
|密码  <br/> |需要为新的 Office 365 邮箱设置的密码。适用于 Office 365 组织的任何密码限制也适用于该 CSV 文件中包括的密码。  <br/> |可选  <br/> |
|ForceChangePassword  <br/> |指定用户在首次登录自己的新 Office 365 邮箱时是否必须更改密码。对此参数的值使用 **True** 或 **False** 。<br/> > [!NOTE]> 如果已通过在本地组织中部署 Active Directory 联合身份验证服务 (AD FS) 或更高版本来实现单一登录 (SSO) 解决方案，必须将 **ForceChangePassword** 属性值设为 **False**。          |可选  <br/> |
   
 **CSV 文件格式**
  
以下是 CSV 文件格式的一个示例。在此示例中，会将三个内部部署邮箱迁移到 Office 365。
  
CSV 文件的第一行（即标题行）列出了在后续行中指定的属性（或字段）的名称。每个属性名称都用逗号分隔开。
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

标题行下面的每行都表示一个用户，并提供将用于迁移该用户邮箱的信息。每行中属性值的顺序必须与标题行中属性名的顺序相同。 
  
使用任何文本编辑器或 Excel 等应用程序创建 CSV 文件。将该文件另存为 .csv 或 .txt 文件。
  
> [!NOTE]
> 如果 CSV 文件包含非 ASCII 字符或特殊字符，请使用 UTF-8 或其他 Unicode 编码保存 CSV 文件。根据应用程序的不同，如果计算机的系统区域设置与 CSV 文件中使用的语言相匹配，则使用 UTF-8 或其他 Unicode 编码保存 CSV 文件可能会更容易。 
  
### <a name="step-3-create-a-migration-endpoint"></a>步骤 3：创建迁移终结点
<a name="BK_Endpoint"> </a>

要成功迁移电子邮件，Office 365 需要与源电子邮件系统连接和通信。为此，Office 365 可使用迁移终结点。要使用 PowerShell 创建适用于暂存迁移的 Outlook 无处不在迁移终结点，首先[连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。 
  
有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。
  
要在 Exchange Online PowerShell 中创建名为“StagedEndpoint”的 Outlook 无处不在迁移终结点，请运行以下命令：
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

有关 **New-MigrationEndpoint** cmdlet 的详细信息，请参阅[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)。
  
> [!NOTE]
> 可以使用 **New-MigrationEndpoint** cmdlet 指定服务要通过 **-TargetDatabase** 选项使用的数据库。在其他情况下，系统会从管理邮箱所在的 Active Directory 联合身份验证服务 (AD FS) 2.0 站点中随机分配数据库。
  
#### <a name="verify-it-worked"></a>验证它是否起作用

在 Exchange Online PowerShell 中，运行以下命令来显示有关“StagedEndpoint”迁移终结点的信息：
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>步骤 4：创建并启动暂存迁移批处理
<a name="BK_Endpoint"> </a>

您可以在 Exchange Online PowerShell 中使用 **New-MigrationBatch** cmdlet 为直接转换迁移创建迁移批处理。您可以通过包括 _AutoStart_ 参数来创建迁移批处理并自动启动。或者，您可以通过使用 **Start-MigrationBatch** cmdlet 创建迁移批处理，然后手动启动。此示例创建名为"StagedBatch1"的迁移批处理并使用之前步骤中创建的迁移终结点。
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

此示例还会创建名为"StagedBatch1"的迁移批处理并使用之前步骤中创建的迁移终结点。由于未包括  _AutoStart_ 参数，因此必须在迁移主控板中手动启动迁移批处理或者通过使用 **Start-MigrationBatch** cmdlet 手动启动迁移批处理。如前所述，一次只能存在一个直接转换迁移批处理。
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>验证它是否起作用

在 Exchange Online PowerShell 中运行以下命令来显示有关“StagedBatch1”的信息：
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

您还可以通过运行以下命令，验证该批处理是否已启动：
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

有关 **Get-MigrationBatch** cmdlet 的详细信息，请参阅[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)。
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>步骤 5：将内部部署邮箱转换为启用邮件的用户
<a name="BK_Endpoint"> </a>

成功迁移一批邮箱以后，您需要某种方法使用户可以访问他们的邮件。已迁移邮箱的用户现在既有一个内部部署邮箱，又有一个 Office 365 邮箱。在 Office 365 中有邮箱的用户将停止在内部部署邮箱中接收新邮件。 
  
由于您尚未完成迁移，因此目前无法将所有用户定向到 Office 365 接收其电子邮件。那么，可以为这些拥有两个邮箱的用户做些什么呢？您可以做的是更改您已迁移到邮件启用的用户的内部部署邮箱。当您从一个邮箱更改为邮件启用的用户时，可以将该用户定向到其电子邮件的 Office 365，而非内部部署邮箱。 
  
将内部部署邮箱转换为启用邮件的用户的另一个重要原因是通过将代理地址复制到启用邮件的用户，来保留 Office 365 邮箱中的代理地址。这使您可以使用 Active Directory 管理来自内部部署组织的基于云的用户。此外，如果您决定在所有邮箱都迁移到 Office 365 之后停止使用内部部署 Exchange Server 组织，则复制到启用邮件的用户的代理地址仍会保留在内部部署 Active Directory 中。
  
若要获取详细信息并下载为将邮箱转换为已启用邮件的用户而可以运行的脚本，请参阅以下内容：
  
- [将 Exchange 2007 邮箱转换为启用邮件的用户](https://go.microsoft.com/fwlink/p/?LinkId=233648)
    
- [将 Exchange 2003 邮箱转换为启用邮件的用户](https://go.microsoft.com/fwlink/p/?LinkId=233647)
    
### <a name="step-6-delete-a-staged-migration-batch"></a>步骤 6：删除暂存迁移批处理
<a name="BK_Endpoint"> </a>

 在迁移批处理中的所有邮箱都已成功迁移并且将批处理中的内部部署邮箱转换为启用邮件的用户之后，可以准备删除暂存迁移批处理。确保验证邮件正在转发到迁移批处理中的 Office 365 邮箱。当您删除暂存迁移批处理时，迁移服务将清除任何与迁移批处理相关的记录，同时删除迁移批处理。
  
要在 Exchange Online PowerShell 中删除“StagedBatch1”迁移批处理，请运行以下命令。
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

有关 **Remove-MigrationBatch** cmdlet 的详细信息，请参阅[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)。
  
#### <a name="verify-it-worked"></a>验证它是否起作用

在 Exchange Online PowerShell 中运行以下命令来显示有关“IMAPBatch1”的信息：
  
```powershell
Get-MigrationBatch StagedBatch1
```

此命令会返回状态为 **Removing** 的迁移批处理或返回错误消息，指出未找到该迁移批处理，验证该批处理已删除。
  
有关 **Get-MigrationBatch** cmdlet 的详细信息，请参阅[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)。
  
### <a name="step7-assign-licenses-to-office-365-users"></a>步骤 7：将许可证分配给 Office 365 用户
<a name="BK_Endpoint"> </a>

通过分配许可证，激活迁移帐户的 Office 365 用户帐户。 如果您不分配许可证，则在宽限期（30 天）结束后将禁用该邮箱。 若要在 Microsoft 365 管理中心分配许可证，请参阅[分配或取消分配 Office 365 商业版许可证](https://go.microsoft.com/fwlink/?LinkId=536681)。
  
### <a name="step-8-complete-post-migration-tasks"></a>步骤 8：完成迁移后任务
<a name="BK_Postmigration"> </a>

- **创建自动发现 DNS 记录，以便用户可以轻松地访问他们的邮箱。** 所有内部部署邮箱都迁移到 Office 365 以后，您可以为您的 Office 365 组织配置自动发现 DNS 记录，使用户可以轻松地使用 Outlook 和移动客户端连接到他们的新 Office 365 邮箱。此新自动发现 DNS 记录必须使用对 Office 365 组织使用的相同命名空间。例如，如果您基于云的命名空间是 cloud.contoso.com，则您需要创建的自动发现 DNS 记录是 autodiscover.cloud.contoso.com。
    
    Office 365 使用 CNAME 记录为 Outlook 和移动客户端实现自动发现服务。自动发现 CNAME 记录必须包含以下信息：
    
  - **别名：** autodiscover
    
  - **目标：** autodiscover.outlook.com
    
    有关更多信息，请参阅[管理 DNS 记录时为 Office 365 创建 DNS 记录](https://go.microsoft.com/fwlink/p/?LinkId=535028)。
    
- **停止使用内部部署 Exchange 服务器。** 当您验证所有电子邮件都可以直接被路由到 Office 365 邮箱，并且您不再需要维护内部部署电子邮件组织或不用计划实施 SSO 解决方案以后，您可以从服务器中卸载 Exchange 并删除内部部署 Exchange 组织。
    
    有关详细信息，请参阅以下资源：
    
  - [修改或删除 Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [如何删除 Exchange 2007 组织](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [如何卸载 Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

