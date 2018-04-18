---
title: 多地区能力在 Exchange 联机
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: 联机 Exchange 中的多个地区功能的多个地理区域展开您 Office 365 的状态。
ms.openlocfilehash: 6378f8a010b790674f07150aa39cbbc38c60b7fe
ms.sourcegitcommit: 63e2844daa2863dddcd84819966a708c434e8580
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>多地区能力在 Exchange 联机

Office 365 中的多个地区功能启用单个租户，若要跨越多个地理位置 (Geo)。启用多个地区后，客户可以在每用户基础上选择联机 Exchange 邮箱内容 （静态数据） 的位置。

基于您的帐单地址确定初始租户位置 （称为您的"默认值"或"中心"位置）。启用多个地区后，可放入更多的"卫星"位置的邮箱：

- 在卫星中直接创建新的联机 Exchange 邮箱。

- 将现有的联机 Exchange 邮箱移动到卫星。

- 板载直接在卫星内部 Exchange 组织中的邮箱。

下面的 Geo 有在多个地区配置中使用：

- 亚太

- 澳大利亚

- 加拿大

- 欧盟

- 印度 (目前仅适用于客户与在印度的账单地址)

- 日本

- 韩国

- 英国

- 美国

## <a name="prerequisite-configuration"></a>必备配置
您可以开始使用在 Exchange 在在线多地区功能之前，Microsoft 需要配置多地区支持您 Exchange Online 租户。订购多地区许可证和通常应采取不超过 30 天，以完成时，将触发此一次性配置进程。

当您的配置已经启动和完成，您将收到通知[Office 365 邮件中心](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093)。购买多地区许可证时，将自动触发配置。

## <a name="mailbox-placement-and-moves"></a>邮箱放置和移动
Microsoft 完成必要多地区配置步骤后，Exchange Online 将履行在用户对象上的**PreferredDataLocation**属性在 Azure AD。

Exchange 联机同步到在线 Exchange 目录服务中的**MailboxRegion**属性从 Azure 广告**PreferredDataLocation**属性。**MailboxRegion**的值确定的 Geo 放置用户邮箱和任何相关的存档邮箱。它不可能来配置用户的主邮箱和存档邮箱驻留在不同的 Geo。只有一个地区可以配置每个用户对象。

- 在**PreferredDataLocation**配置上具有现有邮箱的用户时，该邮箱将自动移到指定的地区。 

- 在**PreferredDataLocation**配置上不具有现有邮箱的用户时，邮箱将调配到指定的地区。 

- 如果未不指定任何地区，邮箱将被置于默认地区。

**注意**： 多地区能力和 Skype 业务联机地区组织主持会议这两个**PreferredDataLocation**属性用于在用户对象上找到服务。如果您在用户对象的承载地区组织会议上配置**PreferredDataLocation**值，邮箱和 OneDrive 的用户将自动移动到指定的地区多地区启用 Office 365 租户在后。

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>联机 Exchange 中的多个地区的功能限制
1. 用户邮箱、 资源邮箱 （房间和设备邮箱） 和共享的邮箱支持多个地理特征。仅可以将公用文件夹的邮箱和 Office 365 组放在客户的家乡地区。
 
2. 安全性和法规遵从功能 （例如，审核和 eDiscovery） Exchange 管理员中心 (EAC) 中的可用不可用在多个地区组织。相反，您需要使用[Office 365 安全和法规遵从性中心](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)配置安全性和法规遵从性功能。

3. 他们的邮箱移动到新的地区时，对于 Mac 用户的 outlook 可能会遇到暂时失去他们的在线存档文件夹的访问权限。出现这种情况时用户的主和存档邮箱位于不同的 Geo，因为跨地区邮箱移动可能会在不同的时间完成。

4. 用户不能通过在 Outlook 中 （以前称为 Outlook Web App 或 OWA） 网站在 Geo 共享*邮箱文件夹*。例如，欧盟中的用户不能使用 Outlook web 上的位于美国邮箱中打开一个共享的文件夹。但是，在 web 用户的 Outlook 可以打开*其他邮箱*不同 Geo 中使用一个单独的浏览器窗口[打开 Outlook Web App 在单独的浏览器窗口中的其他人的邮箱](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)中所述。

    **注意**： 在 Outlook 窗口中支持跨地区邮箱文件夹共享。

5. 目前，跨地区日历委派不支持在 web 上的 Outlook 中。在 Windows 上的 Outlook 中支持跨地区日历委派。

## <a name="administration"></a>管理 
远程 PowerShell 需要查看和配置 Office 365 环境中与地理相关的属性。用来管理 Office 365 的各种 PowerShell 模块的信息，请参阅[管理 Office 365 和 Exchange 联机，使用 Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)。

- 您需要[Microsoft Azure 活动目录 PowerShell 模块](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx)v1.1.166.0 或以后在 1.x 版以查看在用户对象上的**PreferredDataLocation**属性。若要连接到 Azure AD PowerShell，请参阅[连接到 Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)。 

- 要连接到 Exchange 联机 PowerShell，请参阅[连接到 Exchange 联机 PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>直接连接到使用 Exchange 联机 PowerShell 特定地理
通常情况下，Exchange 联机 PowerShell 将连接到默认的地区。但是，也可以直接到非默认 Geo 连接。由于改进了性能，我们建议将直接连接到非默认地区时只能管理在该地区的用户。

要连接到特定的地区， *ConnectionUri*参数，是不同于常规的连接说明。其余的命令和值是相同的。步骤如下：

1. 在本地计算机上打开 Windows PowerShell 并运行以下命令：
    
    ```
    $UserCredential = Get-Credential
    ```
   **Windows PowerShell 凭据请求**对话框中键入您的工作或学校的帐户和密码，然后单击**确定**。
    
2. 更换`<emailaddress>`在目标地区中的**任何**邮箱存储和运行下面的命令的电子邮件地址。邮箱，并向您的凭据在步骤 1 中的关系的权限不是一个因素;电子邮件地址仅仅告诉 Exchange Online 的连接位置。
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   例如，如果 olga@contoso.onmicrosoft.com 是在您想要连接地区一个有效邮箱的电子邮件地址，请运行以下命令：

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. 运行以下命令：
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Azure AD 连接版本要求
AAD 连接版本 1.1.524.0 或更高版本为从内部部署 Active Directory 同步的用户对象上设置**PreferredDataLocation**属性是唯一受支持的方法。有关详细说明，请参阅[Azure 活动目录连接同步： 配置 Office 365 提供资源的首选的数据位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。

### <a name="geo-codes"></a>地区代码
三个字母的代码用于在**PreferredDataLocation**属性中指定的地区。下表列出可用的 Geo 的代码：

|地域 |代码 |
|---------|---------|
|亚太 |APC 公司 |
|澳大利亚 |澳大利亚 |
|加拿大 |可以 |
|欧盟 |欧元 |
|印度 |IND |
|日本 |日文 |
|韩国 |韩文 |
|英国 |GBR |
|美国 |名称 |

**注**： **PreferredDataLocation**和**MailboxRegion**属性是与没有错误检查的字符串。如果您输入了无效的值 (例如，NAN) 邮箱将放置在默认的地区。

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>查看联机 Exchange 组织中配置可用 Geo
若要查看已配置 Geo 联机 Exchange 组织中的列表，请运行下面的命令在 Exchange 联机 PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

命令输出如下所示：

```
Region
------
APC
AUS
CAN
EUR
GBR
JPN
KOR
NAM
```

### <a name="find-the-geo-location-of-a-mailbox"></a>找到一个邮箱的地理位置
**获取邮箱**cmdlet Exchange 联机继续显示邮箱与地理相关的以下属性：

- **数据库**： 数据库名称的前 3 个字母对应于地区代码中，告诉您邮箱是当前所在的位置。

- **MailboxRegion**： 指定由管理员 （同步是**PreferredDataLocation**在 Azure AD） 设置了的地区代码。

- **MailboxRegionLastUpdateTime**： 指示当 MailboxRegion 上次更新 （自动或手动）。

要查看这些邮箱属性，请使用下面的语法：

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

例如，若要查看邮箱 chris@contoso.onmicrosoft.com 的地理信息，运行以下命令：

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

命令输出如下所示：

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> [!NOTE]
> 如果数据库名称中的地区代码与**MailboxRegion**值不匹配，邮箱将自动移到指定的**MailboxRegion**值 （Exchange 联机查找这些属性值之间的不匹配） 地区。

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a>将现有的云邮箱移动到特定的地理
使用**Get MsolUser**和**一组 MsolUser** cmdlet Windows PowerShell Azure AD 模块中查看或指定用户的邮箱存储地理。

若要查看用户的**PreferredDataLocation**值，请在 Azure AD PowerShell 中使用以下语法：

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

例如，若要查看用户 michelle@contoso.onmicrosoft.com 的**PreferredDataLocation**值，请运行以下命令：

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

命令输出如下所示：

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

若要修改仅云用户对象的**PreferredDataLocation**值，请在 Azure AD PowerShell 使用以下语法：

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

例如，若要将**PreferredDataLocation**值设置为欧盟 （欧元） 的用户 michelle@contoso.onmicrosoft.com，运行以下命令：

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**注释**：

- 前面已提到为从内部部署 Active Directory 同步的用户对象，您不能使用此过程。您需要更改使用 AAD 连接的**PreferredDataLocation**值。有关详细信息，请参阅[Azure 活动目录连接同步： 配置 Office 365 提供资源的首选的数据位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。 

- 移动邮箱所需的时间取决于几个因素：
 
  - 大小和类型的邮箱。
 
  - 要移动的邮箱数。
 
  - 移动资源的可用性。

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>在诉讼封存禁用移动邮箱
禁用为 eDiscovery 目的不能移动通过更改它们处于禁用状态的**PreferredDataLocation**值保留在诉讼封存的邮箱。诉讼封存在移动被禁用的邮箱：

1. 暂时将许可证分配给该邮箱。

2. 更改**PreferredDataLocation**。

3. 从邮箱中删除许可证后它已被移动到选定的地区要将其放回禁用状态。

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>在特定地区中创建新的云邮箱 
要在特定地区创建一个新的邮箱，您需要执行下列步骤之一：

- 如前面所述配置的**PreferredDataLocation**值部分*之前*（例如，通过配置用户分配许可证之前的**PreferredDataLocation**值） 在 Exchange 联机创建邮箱。 

- 在同一时间将**PreferredDataLocation**值设置分派许可证。

若要在特定地区创建新云仅授权的用户 （AAD 连接同步），请在 Azure AD PowerShell 使用以下语法：

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
本示例创建新的用户帐户的李大 Brunner 具有以下值：

- 用户主体名称： ebrunner@contoso.onmicrosoft.com

- 第一名： 李大

- 姓名： Brunner

- 显示名称李大 Brunner

- 密码： 随机生成和显示该命令的结果中，（因为我们不使用*密码*参数）

- 许可： contoso:ENTERPRISEPREMIUM (E5)

3 位置： 澳大利亚 （澳大利亚）

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

有关如何创建新的用户帐户和 Azure 广告继续查找 LicenseAssignment 值的详细信息，请参阅[Office 365 PowerShell 创建用户帐户](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)并[查看许可证和服务与 Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)。

> [!NOTE]
> 如果使用的 Exchange PowerShell 启用邮箱，需要直接在 Geo 在**PreferredDataLocation**中指定要创建的邮箱，您需要使用诸如**启用邮箱**或**新建邮箱**的 Exchange Online cmdlet直接对云服务。如果您使用**启用 RemoteMailbox**内部 Exchange cmdlet，将在默认的地区创建邮箱。

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>板载现有部署的邮箱中特定地理
可以使用标准的板载工具和进程将从内部 Exchange 组织的邮箱迁移到 Exchange Online，包括[迁移中 EAC 的仪表板](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)和[新建 MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet 在 Exchange 联机PowerShell。

第一步是验证一个用户对象存在于每个邮箱是 onboarded，并验证在 Azure AD 中配置正确的**PreferredDataLocation**值。板载工具将尊重的**PreferredDataLocation**值，并将直接到指定的地区迁移邮箱。

或者，可以使用以下步骤在使用 Exchange 联机 PowerShell[新建 MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet 特定地区中直接板载邮箱。

1. 验证用户对象存在于每个邮箱为 onboarded 和**PreferredDataLocation** Azure AD 中设置为所需的值。**PreferredDataLocation**的值将被同步到相应的邮件用户对象的**MailboxRegion**特性在 Exchange 联机。

2. 直接连接到特定的附属地区使用本主题中前面的连接说明。

3. 在 Exchange 联机 PowerShell 存储用于通过运行下面的命令在一个变量中执行邮箱迁移的本地管理员凭据：

    ```
    $RC = Get-Credential
    ```

4. 在 Exchange 联机 PowerShell 创建新**新建 MoveRequest**与以下示例类似： 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. 重复步骤 4，您需要从内部 Exchange 迁移到您当前连接到的 Geo 卫星每个邮箱。

6. 如果您需要将其他邮箱迁移到不同的附属地区，为每个特定附属地区重复步骤 2 到 4。

### <a name="multi-geo-reporting"></a>多地区报告
在 Office 365 管理中心**多地区使用率报告**按地区显示用户计数。该报告显示当前月份的用户分布，为过去 6 个月提供的历史数据。
 
