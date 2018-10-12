---
title: Exchange Online 中的多地理位置功能
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Exchange Online 中的多地理位置功能的多个地理区域中展开 Office 365 状态。
ms.openlocfilehash: aa83b5040cdc98a1c651388fa82d746b852c2313
ms.sourcegitcommit: 5cb4dbdd10ab399af414503cb518a9f530919ef5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "25498222"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Exchange Online 中的多地理位置功能

Office 365 中的多地理位置功能启用单个租户跨多个地理位置 (Geo)。启用多地理位置后，客户可以选择基于每个用户的 Exchange Online 邮箱内容 （静态数据） 的位置。

基于您的付费地址确定初始租户您的位置 （称为您"default"或"管理中心"位置）。启用多地理位置后，可以将邮箱置于由的其他"附属"位置：

- 直接在附属中创建新的 Exchange Online 邮箱。

- 将现有的 Exchange Online 邮箱移到附属。

- 加入从直接附属内部部署 Exchange 组织的邮箱。

以下 Geo 供多地理位置配置中的使用：

- 亚太地区

- 澳大利亚

- 加拿大

- 欧盟

- 法国

- 印度 (当前仅适用于使用在印度帐单地址客户)

- 日本

- 韩国

- 英国

- 美国

## <a name="prerequisite-configuration"></a>必备组件配置
然后才能开始联机 Exchange 中使用多地理位置功能 Microsoft 需要配置您的 Exchange Online 租户多地理支持。排序多地理位置和许可证显示在您的租户后，将触发本一次性配置进程。此一次性配置过程通常应小于 30 天才能完成。顺序多地理位置，请与 Microsoft 代表联系。有关详细信息，请参阅https://aka.ms/Multi-Geo。

完成您的配置后，您将在[Office 365 邮件中心](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093)收到通知。配置自动触发后多地理许可证显示在您的租户。

## <a name="mailbox-placement-and-moves"></a>邮箱位置和移动
Microsoft 完成的必备组件的多地理配置步骤之后，Exchange Online 也会授予对用户对象的**PreferredDataLocation**属性在 Azure AD。

Exchange Online 同步到 Exchange Online 的目录服务中的**MailboxRegion**属性 Azure AD 的**PreferredDataLocation**属性。**MailboxRegion**的值确定的 Geo 放置用户邮箱和任何关联的存档邮箱。不能配置用户的主邮箱和存档邮箱驻留在不同 Geo。只有一个地理位置可以配置每个用户对象。

- 上具有现有的邮箱的用户配置**PreferredDataLocation** ，则邮箱将放入重定位队列，并自动移动到指定的地理位置。 

- 时上没有现有邮箱的用户配置**PreferredDataLocation** ，则将设置邮箱到指定的地理位置。 

- 当用户在未指定**PreferredDataLocation** ，则邮箱都位于默认地理位置。

- 如果**PreferredDataLocation**代码不正确 （例如类型的而不是越南 NAN） 邮箱将位于默认地理位置。

**注意**： 多地理位置功能和两个业务联机地区组织承载会议的 Skype **PreferredDataLocation**属性用于在用户对象上查找服务。如果您的地区组织托管的会议的用户对象上配置**PreferredDataLocation**值，这些用户的邮箱将自动移动到指定的地理位置后的 Office 365 租户启用多地理位置。

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Exchange Online 中的多地理位置功能限制
1. 用户邮箱、 资源邮箱 （房间和设备邮箱） 和共享的邮箱支持多地理位置功能。公用文件夹邮箱和 Office 365 组保持客户的主地理位置。
 
2. 安全性和遵从性 （例如，审核和电子数据展示） 可用功能的 Exchange 管理员中心 (EAC) 中不可用多地理位置组织中。相反，您需要使用[Office 365 安全性和合规性中心](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)来配置安全性和遵从性功能。

3. 他们的邮箱移动到新的地理位置时，outlook for Mac 用户可能会遇到临时断开其联机存档文件夹的访问权限。发生这种情况时用户的主和存档邮箱都在不同 Geo，因为跨地理邮箱移动可能完成时间不同。

4. 用户无法在 web （以前称为，Outlook Web App 或 OWA） 上的 Outlook 中的 Geo 之间共享*邮箱文件夹*。例如，在欧盟用户不能使用 web 上的 Outlook 打开位于美国的邮箱中的共享的文件夹。但是，在 Web 用户的 Outlook 可以*其他邮箱*中打开不同 Geo 使用单独的浏览器窗口[打开 Outlook Web App 中的一个单独的浏览器窗口中的其他人的邮箱](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)中所述。

    **注意**： 在 Outlook 中为 Windows 上支持跨地理邮箱文件夹共享。

## <a name="administration"></a>管理 
远程 PowerShell 需要查看和 Office 365 环境中配置与地理位置相关的属性。有关各种用来管理 Office 365，请参阅[管理 Office 365 和 Exchange Online 使用 Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)的 PowerShell 模块的信息。

- 您需要[Microsoft Azure Active Directory PowerShell 模块](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx)v1.1.166.0 或更高版本中 1.x 版在用户对象上看到**PreferredDataLocation**属性。通过 AAD 连接同步到 AAD 的用户对象不能直接通过 AAD PowerShell 修改其**PreferredDataLocation**值。仅限云用户对象可以通过 AAD PowerShell 进行修改。要连接到 Azure AD PowerShell，请参阅[Connect to Office 365 PowerShell 中](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)。 

- 要连接到 Exchange Online PowerShell 中，请参阅[Connect to Exchange Online PowerShell 中](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>直接连接到 Exchange Online PowerShell 中使用的特定地理位置
通常情况下，Exchange Online PowerShell 中将连接到默认地理位置。但是，您还可以直接向非默认 Geo 连接。由于性能改进，我们建议直接连接到非默认地理位置时仅管理中的地理位置的用户。

要连接到特定的地理位置，则正则连接说明以外的其他*ConnectionUri*参数。其余的命令和值都相同。步骤如下：

1. 在本地计算机上打开 Windows PowerShell 并运行以下命令：
    
    ```
    $UserCredential = Get-Credential
    ```
   **Windows PowerShell 凭据请求**对话框中，键入您的工作或学校帐户和密码，，然后单击**确定**。
    
2. 替换`<emailaddress>`替换**任何**目标地理位置中的邮箱并运行以下命令的电子邮件地址。不因素; 您对邮箱和向您在步骤 1 中的凭据的关系的权限。电子邮件地址仅仅告诉 Exchange Online 连接的位置。
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   例如，如果 olga@contoso.onmicrosoft.com 是您想要连接的地理位置中的有效邮箱的电子邮件地址，请运行以下命令：

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. 运行以下命令：
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Azure AD 连接版本要求
AAD 连接版本 1.1.524.0 或更高版本用于从内部部署 Active Directory 用户对象同步的设置的**PreferredDataLocation**属性是唯一受支持的方法。通过 AAD 连接同步到 AAD 的用户对象不能直接通过 AAD PowerShell 修改其**PreferredDataLocation**值。仅限云用户对象可以通过 AAD PowerShell 进行修改。有关详细说明，请参阅[Azure Active Directory 连接同步： 配置 Office 365 资源的首选的数据位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。

### <a name="geo-codes"></a>地理位置代码
三个字母代码用于**PreferredDataLocation**属性中指定的地理位置。下表列出了可用 Geo 的代码：

|地域 |代码 |
|---------|---------|
|亚太地区 |APC |
|澳大利亚 |AUS |
|加拿大 |CAN |
|欧盟 |EUR |
|法国 |FRA|
|印度 |IND |
|日本 |JPN |
|韩国 |KOR |
|英国 |GBR |
|美国 |NAM |

**注意**： 的**PreferredDataLocation**和**MailboxRegion**属性是与没有错误检查的字符串。如果输入值无效 (例如，NAN) 邮箱都位于默认地理位置。

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>查看可用 Geo 在 Exchange Online 组织中配置
若要配置 Geo Exchange Online 组织中的列表，请参阅，运行以下命令在 Exchange Online PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

此命令的输出如下所示：

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a>查看 Exchange Online 组织的默认地理位置
若要查看您的 Exchange Online 组织的默认地理位置，请运行以下命令在 Exchange Online PowerShell:

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

此命令的输出如下所示：

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a>查找邮箱的地理位置
Exchange Online PowerShell 中的**Get-mailbox** cmdlet 显示邮箱上的地理位置相关的以下属性：

- **数据库**： 数据库名称的前 3 个字母对应告诉您邮箱所在的位置当前的地理位置代码。联机存档邮箱**ArchiveDatabase**应使用属性。

- **MailboxRegion**： 指定由管理员 （Azure AD 中从**PreferredDataLocation**同步） 所设置的地理位置代码。

- **MailboxRegionLastUpdateTime**： 指示当 MailboxRegion 上次更新 （自动或手动）。

若要查看邮箱的这些属性，请使用以下语法：

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

例如，若要查看邮箱 chris@contoso.onmicrosoft.com 的地理信息，请运行以下命令：

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

此命令的输出如下所示：

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> **注意：** 如果在数据库名称的地理位置代码与**MailboxRegion**值不匹配，邮箱将被自动放入重定位队列和移动到指定的**MailboxRegion**值 （Exchange Online 看起来这些不匹配的地理位置属性值）。

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a>将现有仅使用云的邮箱移动到特定的地理位置
仅限云用户是用户不到通过 AAD 连接租户的同步。直接在 Azure AD 中创建此用户。使用 Windows PowerShell 的 Azure AD 模块中**Get-msoluser**和**Set-msoluser** cmdlet 查看或指定存储仅使用云的用户的邮箱地理位置。

若要查看用户的**PreferredDataLocation**值，请在 Azure AD PowerShell 中使用以下语法：

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

例如，若要查看用户 michelle@contoso.onmicrosoft.com **PreferredDataLocation**值，请运行以下命令：

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

此命令的输出如下所示：

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

若要修改的仅云用户对象的**PreferredDataLocation**值，请在 Azure AD PowerShell 中使用以下语法：

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

例如，若要将**PreferredDataLocation**值设置为用户 michelle@contoso.onmicrosoft.com 欧盟 (EUR) 地理位置，运行以下命令：

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**注意**：

- 提到过之前不能使用此过程从内部部署 Active Directory 同步的用户对象。您需要更改**PreferredDataLocation**值使用 AAD 连接。有关详细信息，请参阅[Azure Active Directory 连接同步： 配置 Office 365 资源的首选的数据位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。 

- 它所需的时间重定位到新的所需地理其当前地理位置取决于多个因素 mailboxfrom:
 
  - 大小和类型的邮箱。
 
  - 要移动的邮箱数。
 
  - 移动资源的可用性。

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>移动禁用在诉讼保留的邮箱
禁用邮箱诉讼保留的保留电子数据展示不能通过更改其禁用状态中的其**PreferredDataLocation**值移动目的。将禁用的邮箱置于诉讼保留：

1. 临时分派到邮箱的许可证。

2. 更改**PreferredDataLocation**。

3. 它已移至所选的地理位置以将其放回禁用状态后，请从邮箱中删除许可证。

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>在特定的地理位置中创建新的云邮箱 
若要在特定的地理位置创建一个新的邮箱，您需要执行以下步骤之一：

- 上一节*之前*的邮箱创建在 Exchange Online 中所述配置**PreferredDataLocation**值。例如，将许可证分配之前对用户配置**PreferredDataLocation**值。 

- 设置**PreferredDataLocation**值的同时分配许可证。

要在特定的地理位置创建新仅使用云的授权的用户 （不 AAD 连接同步），请在 Azure AD PowerShell 中使用以下语法：

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
本示例创建新的用户帐户的李大 Brunner 具有以下值：

- 用户主体名称： ebrunner@contoso.onmicrosoft.com

- 名字： 李大

- 姓： Brunner

- 显示名称李大 Brunner

- 密码： 随机生成所示命令的结果，（因为我们不使用*Password*参数）

- 许可证： contoso:ENTERPRISEPREMIUM (E5)

- 位置： 澳大利亚 （澳大利亚）

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

有关创建新的用户帐户并在 Azure AD PowerShell 中查找 LicenseAssignment 值的详细信息，请参阅[使用 Office 365 PowerShell 创建用户帐户](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)和[查看许可证和服务与 Office 365 PowerShell 中](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)。

> **注意：** 如果使用 Exchange Online PowerShell 中启用邮箱和需要直接在 Geo **PreferredDataLocation**中指定要创建的邮箱，您需要使用如**Enable-mailbox**或**New-mailbox Exchange Online cmdlet**直接针对云服务。如果您使用**Enable-remotemailbox**内部部署 Exchange cmdlet，将默认地理位置中创建邮箱。

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>板载现有内部部署邮箱中的特定地理位置
您可以使用的标准入职培训工具和流程将邮箱从本地 Exchange 组织迁移到 Exchange Online，包括[在 EAC 中的迁移主控板](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)上，并使用[New-migrationbatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet 在 Exchange OnlinePowerShell。

第一步是验证的用户对象存在 onboarded，并确认正确的**PreferredDataLocation**值在 Azure AD 中配置每个邮箱。入职培训工具将尊重**PreferredDataLocation**值，并会将邮箱迁移直接到指定的地理位置。

或者，您可以使用以下步骤来直接在 Exchange Online PowerShell 中使用[New-moverequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet 的特定地理位置的板载邮箱。

1. 验证每个邮箱 onboarded 和 Azure AD 中的设置为所需的值包含**PreferredDataLocation**存在用户对象。**PreferredDataLocation**的值将同步到相应的邮件用户对象的**MailboxRegion**属性在 Exchange Online。

2. 直接连接到特定的附属从连接说明使用本主题中前面的地理位置。

3. 在 Exchange Online PowerShell 中，存储用于通过运行以下命令执行的变量中的邮箱迁移的本地管理员凭据：

    ```
    $RC = Get-Credential
    ```

4. 在 Exchange Online PowerShell 中，创建新**New-moverequest**类似于下面的示例： 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. 您需要从内部部署 Exchange 迁移到附属地理您当前连接到每个邮箱重复步骤 4。

6. 如果您需要将其他邮箱迁移到不同的附属地理位置，请对每个特定的附属地理重复步骤 2 到 4。

### <a name="multi-geo-reporting"></a>多地理位置报告
在 Office 365 管理中心中的**多地理使用率报告**按地理位置显示用户计数。报告显示当前月份用户分布，并提供过去 6 个月的历史数据。
