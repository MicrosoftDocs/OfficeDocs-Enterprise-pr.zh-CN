---
title: 使用 PowerShell 执行分步迁移以迁移到 Microsoft 365
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
ms.custom: seo-marvel-apr2020
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 了解如何使用 PowerShell 将暂存迁移到 Microsoft 365，从而在一段时间后通过源电子邮件系统移动内容。
ms.openlocfilehash: a50966f65bbec5e4b453c4caf02e4b89fa7d04b5
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606208"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>使用 PowerShell 执行分步迁移以迁移到 Microsoft 365

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

您可以使用暂存迁移将用户邮箱的内容从源电子邮件系统迁移到 Microsoft 365。
  
本文将引导您完成使用 Exchange Online PowerShell 进行暂存电子邮件迁移所涉及的任务。主题：[有关暂存电子邮件迁移所需了解的内容](https://go.microsoft.com/fwlink/p/?LinkId=536487)，提供了迁移过程的概述。当您熟悉该文章的内容时，请使用此程序开始将邮箱从一个电子邮件系统迁移到另一个。
  
> [!NOTE]
> 您还可以使用 Exchange 管理中心执行暂存迁移。请参阅[执行将电子邮件暂存迁移到 Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536687)。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>在开始之前，您需要知道什么？

估计完成该任务的时间：2-5 分钟以创建迁移批处理。迁移批处理启动后，迁移的持续时间将根据批处理中的邮箱数、每个邮箱的大小和可用网络容量的不同而有所不同。有关影响将邮箱迁移到 Microsoft 365 所需时间的其他因素的信息，请参阅[迁移性能](https://go.microsoft.com/fwlink/p/?LinkId=275079)。
  
您必须先获得权限，然后才能执行此过程。要查看您需要哪些权限，请参阅[收件人权限](https://go.microsoft.com/fwlink/p/?LinkId=534105)主题中的"迁移"条目。
  
若要使用 Exchange Online PowerShell cmdlet，您需要登录并将 cmdlet 导入您的本地 Windows PowerShell 会话。有关说明，请参阅[使用远程 PowerShell 连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。
  
有关迁移命令的完整列表，请参阅[移动和迁移 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=534750)。
  
## <a name="migration-steps"></a>迁移步骤

### <a name="step-1-prepare-for-a-staged-migration"></a>步骤 1：准备暂存迁移

在使用暂存迁移将邮箱迁移到 Microsoft 365 之前，您必须对 Exchange 环境进行几处更改。
  
 **在您的内部部署 Exchange Server 上配置 Outlook 无处不在** 电子邮件迁移服务使用 Outlook 无处不在（也称为 RPC over HTTP）连接到您的内部部署 Exchange Server。有关如何为 Exchange Server 2007 和 Exchange 2003 设置 Outlook 无处不在 设置的信息，请参阅以下内容：
  
- [Exchange 2007:如何启用 Outlook 无处不在](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [如何使用 Exchange 2003 配置 Outlook 无处不在](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> 您必须在 Outlook 无处不在 配置中使用受信任的证书颁发机构 (CA) 颁发的证书。Outlook 无处不在 不能通过自签名的证书进行配置。有关详细信息，请参阅[如何为 Outlook 无处不在配置 SSL](https://go.microsoft.com/fwlink/?LinkID=80875)。 
  
 **可选：确认您是否可以使用 Outlook 无处不在 连接到 Exchange 组织** 使用下列方法之一来测试您的连接设置。
  
- 使用公司网络外部的 Outlook 连接到您的内部部署 Exchange 邮箱。
    
- 使用[Microsoft 远程连接分析器](https://https://testconnectivity.microsoft.com/)测试您的连接设置。使用 Outlook Anywhere (RPC over HTTP) 或 Outlook 自动发现测试。
    
- 在 Exchange Online PowerShell 中运行以下命令：
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **设置权限**用于连接到内部部署 Exchange 组织的本地用户帐户也称为迁移管理员) 必须具有访问要迁移到 Microsoft 365 中的本地邮箱的必要权限 (。在此过程中，通过在此过程的后面创建迁移终结点来连接到电子邮件系统时，将使用此用户帐户 ([步骤3：创建迁移终结点](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint)) 。
  
要迁移邮箱，管理员必须拥有以下权限集之一：
  
- 内部部署组织中 Active Directory 中的 **Domain Admins** 组成员。
    
    或
    
- 分配了对每个内部部署邮箱的 **FullAccess** 权限以及可修改内部部署用户帐户上的 **TargetAddress** 属性的 **WriteProperty** 权限。
    
    或
    
- 分配了对存储用户邮箱的内部部署邮箱数据库上的 **Receive As** 权限以及可修改内部部署用户帐户上的 **TargetAddress** 属性的 **WriteProperty** 权限。
    
有关如何设置这些权限的说明，请参阅[分配权限以将邮箱迁移到 Microsoft 365](https://go.microsoft.com/fwlink/?LinkId=521656)。
  
 **禁用统一消息 (UM)** 如果您要迁移的内部部署邮箱上开启了 UM，请先将其关闭，然后再执行迁移。迁移完成以后，打开邮箱的 UM。有关具体的操作方法步骤，请参阅[禁用统一消息](https://go.microsoft.com/fwlink/?LinkId=521891)。
  
 **使用目录同步在 Microsoft 365 中创建新用户。** 您可以使用目录同步在 Microsoft 365 组织中创建所有本地用户。
  
创建用户以后，您需要对他们授予许可。您可以在创建用户之后的 30 天内添加许可证。有关添加许可证的步骤，请参阅[步骤 8：完成迁移后任务](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration)。
  
 您可以使用 Microsoft Azure Active Directory (Azure AD) 同步工具或 Microsoft Azure AD 同步服务在 Microsoft 365 中同步和创建本地用户。将邮箱迁移到 Microsoft 365 后，可以在内部部署组织中管理用户帐户，并将其与您的 Microsoft 365 组织同步。有关详细信息，请参阅[目录集成](https://go.microsoft.com/fwlink/?LinkId=521788)。
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>步骤 2：为暂存迁移批处理创建 CSV 文件

在确定要将其本地邮箱迁移到 Microsoft 365 的用户后，使用逗号分隔的值 (CSV ) 文件来创建迁移批处理。CSV 文件中的每一行（由 Microsoft 365 用于运行迁移）包含有关本地邮箱的信息。 
  
> [!NOTE]
> 使用暂存迁移可迁移到 Microsoft 365 的邮箱数没有限制。迁移批处理的 CSV 文件最多可包含2000行。若要迁移超过2000的邮箱，请创建其他 CSV 文件，并使用每个文件创建新的迁移批处理。 
  
 **支持的属性**
  
暂存迁移的 CSV 文件支持下列三个属性。CSV 文件中的每一行对应于一个邮箱并且必须包含属性的相应值。
  
|**属性**|**说明**|**是否必需？**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |为内部部署邮箱指定一个主要的 SMTP 电子邮件地址，例如，pilarp@contoso.com。  <br/> 将主 SMTP 地址用于本地邮箱，而不是 Microsoft 365 中的用户 Id。例如，如果内部部署域的名称为 contoso.com，但 Microsoft 365 电子邮件域名为 service.contoso.com，则可以在 CSV 文件中使用电子邮件地址的 contoso.com 域名。  <br/> |必需  <br/> |
|密码  <br/> |要为新的 Microsoft 365 邮箱设置的密码。适用于 Microsoft 365 组织的任何密码限制也适用于 CSV 文件中包含的密码。  <br/> |可选  <br/> |
|ForceChangePassword  <br/> |指定用户首次登录到其新的 Microsoft 365 邮箱时是否必须更改密码。对此参数的值使用**True**或**False** 。<br/> > [!NOTE]> 如果已通过在本地组织中部署 Active Directory 联合身份验证服务 (AD FS) 或更高版本来实现单一登录 (SSO) 解决方案，必须将 **ForceChangePassword** 属性值设为 **False**。          |可选  <br/> |
   
 **CSV 文件格式**
  
下面是 CSV 文件格式的示例。在此示例中，将三个本地邮箱迁移到 Microsoft 365。
  
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

若要成功迁移电子邮件，Microsoft 365 需要连接源电子邮件系统并与之通信。为此，Microsoft 365 使用迁移终结点。若要使用 PowerShell 创建 Outlook 无处不在迁移终结点，请先[连接到 Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121)。 
  
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

成功迁移一批邮箱后，您需要某种方式让用户能够访问其邮件。已迁移其邮箱的用户现在在本地和 Microsoft 365 中都有一个邮箱。在 Microsoft 365 中拥有邮箱的用户将停止在其本地邮箱中接收新邮件。 
  
由于你未完成迁移，你尚未准备好将所有用户定向到 Microsoft 365 以获取其电子邮件。那么，对于同时拥有这两个用户的人，该怎么办呢？您可以执行的操作是，将已迁移的本地邮箱更改为启用邮件的用户。当您从邮箱更改为启用邮件的用户时，您可以将该用户定向到 Microsoft 365，而不是转到其本地邮箱。 
  
将本地邮箱转换为启用邮件的用户的另一个重要原因是，通过将代理地址复制到启用邮件的用户来保留 Microsoft 365 邮箱中的代理地址。这样，您就可以使用 Active Directory 管理本地组织中基于云的用户。此外，如果您决定在将所有邮箱迁移到 Microsoft 365 之后停止本地 Exchange 服务器组织，则已复制到启用邮件的用户的代理地址将保留在本地 Active Directory 中。
    
### <a name="step-6-delete-a-staged-migration-batch"></a>步骤 6：删除暂存迁移批处理
<a name="BK_Endpoint"> </a>

 在迁移批处理中的所有邮箱都已成功迁移并且将批处理中的内部部署邮箱转换为启用邮件的用户之后，可以准备删除暂存迁移批处理。 请务必确认要将邮件转发到迁移批处理中的 Microsoft 365 邮箱。 当您删除暂存迁移批处理时，迁移服务将清除任何与迁移批处理相关的记录，同时删除迁移批处理。
  
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
  
### <a name="step7-assign-licenses-to-microsoft-365-users"></a>Step7：将许可证分配给 Microsoft 365 用户
<a name="BK_Endpoint"> </a>

通过分配许可证为迁移的帐户激活 Microsoft 365 用户帐户。 如果您不分配许可证，则在宽限期（30 天）结束后将禁用该邮箱。 若要在 Microsoft 365 管理中心中分配许可证，请参阅[分配或取消分配许可证](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)。
  
### <a name="step-8-complete-post-migration-tasks"></a>步骤 8：完成迁移后任务
<a name="BK_Postmigration"> </a>

- **创建自动发现 DNS 记录，以便用户可以轻松地访问他们的邮箱。** 在将所有内部部署邮箱迁移到 Microsoft 365 之后，可以为 Microsoft 365 组织配置自动发现 DNS 记录，使用户可以使用 Outlook 和移动客户端轻松连接到其新的 Microsoft 365 邮箱。 这一新的自动发现 DNS 记录必须使用您的 Microsoft 365 组织所使用的相同命名空间。 例如，如果您的基于云的命名空间是 cloud.contoso.com，那么您需要创建的自动发现 DNS 记录是 autodiscover.cloud.contoso.com。
    
    Microsoft 365 使用 CNAME 记录来实现 Outlook 和移动客户端的自动发现服务。 自动发现 CNAME 记录必须包含以下信息：
    
  - **别名：** autodiscover
    
  - **目标：** autodiscover.outlook.com
    
    有关详细信息，请参阅[添加 DNS 记录以连接到您的域](https://go.microsoft.com/fwlink/p/?LinkId=535028)。
    
- **停止使用内部部署 Exchange 服务器。** 确认所有电子邮件都直接路由到 Microsoft 365 邮箱，并且不再需要维护内部部署电子邮件组织或不计划实施 SSO 解决方案时，可以从服务器中卸载 Exchange 并删除内部部署 Exchange 组织。
    
    有关详细信息，请参阅以下资源：
    
  - [修改或删除 Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [如何删除 Exchange 2007 组织](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [如何卸载 Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

