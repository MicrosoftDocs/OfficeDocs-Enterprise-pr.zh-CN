---
title: 在多地理位置环境中管理 Exchange Online 邮箱
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: 了解如何使用 Microsoft PowerShell 管理 Exchange Online 多地理位置设置。
ms.openlocfilehash: 5dac890d2b0d5a797f8c2507c115c14147add7ff
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057648"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>在多地理位置环境中管理 Exchange Online 邮箱

需要远程 PowerShell 才能在 Microsoft 365 环境中查看和配置多地理位置属性。 若要连接到 Exchange Online PowerShell，请参阅[连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。

你需要 [Microsoft Azure Active Directory PowerShell 模块](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 或 v1.x 中的更高版本才能查看用户对象的 **PreferredDataLocation** 属性。 无法通过 AAD PowerShell 直接修改通过 AAD Connect 同步到 AAD 中的用户对象的 **PreferredDataLocation** 值。 可以通过 AAD PowerShell 修改仅限云的用户对象。 若要连接到 Azure AD PowerShell，请参阅[连接到 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)。

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>使用 Exchange Online PowerShell 直接连接到某个地理位置

通常，Exchange Online PowerShell 将连接到中心地理位置。 但你也可以直接连接到附属地理位置。 由于性能有所改进，因此，当你仅管理附属地理位置中的用户时，我们建议直接连接到该位置。

用于连接到特定地理位置的 *ConnectionUri* 参数与常规连接指令不同。 命令和值的其余部分是相同的。 步骤如下：

1. 在本地计算机上，打开 Windows PowerShell 并运行以下命令：

   ```powershell
   $UserCredential = Get-Credential
   ```

   在“**Windows PowerShell 凭据请求**”对话框中，键入工作或学校帐户用户名和密码，再单击“**确定**”。

2. 将 `<emailaddress>` 替换为目标地理位置中的**任何**邮箱的电子邮件地址，并运行以下命令。 你对邮箱的权限和与步骤 1 中凭据的关系并不重要；电子邮件地址只是告知 Exchange Online 连接到何处。
  
   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   例如，如果 olga@contoso.onmicrosoft.com 是你想要连接的地理位置的有效邮箱地址，则运行以下命令：

   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

3. 运行以下命令：

    ```powershell
    Import-PSSession $Session
    ```

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>查看在 Exchange Online 组织中配置的可用地理位置

若要在 Microsoft 365 多地理位置中查看配置的地理位置的列表，请在 Exchange Online PowerShell 中运行以下命令：

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>查看 Exchange Online 组织的中心地理位置

若要查看租户的中心地理位置，请在 Exchange Online PowerShell 中运行以下命令：

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>查找邮箱的地理位置

Exchange Online PowerShell 中的 **Get-Mailbox** cmdlet 显示邮箱的以下多地理位置相关属性：

- **Database**：对地理位置代码对应的数据库名称的前 3 个字母，告知你邮箱当前位于何处。 对于在线存档邮箱，应使用 **ArchiveDatabase** 属性。

- **MailboxRegion**：指定管理员设置的地理位置代码（从 Azure AD 中的 **PreferredDataLocation** 同步）。

- **MailboxRegionLastUpdateTime**：指明 MailboxRegion 的最后（自动或手动）更新时间。

若要查看邮箱的这些属性，请使用以下语法：

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

例如，若要查看邮箱 chris@contoso.onmicrosoft.com 的地理位置信息，请运行以下命令：

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

此命令的输出如下所示：

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> **注意：** 如果数据库名称中的地理位置代码与 **MailboxRegion** 值不匹配，则会将该邮箱自动放入重定位队列，并移动到 **MailboxRegion** 值指定的地理位置 （Exchange Online 会查找这些属性值的不匹配之处）。

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>将现有的仅限云邮箱移动到特定地理位置

仅限云的用户是未通过 AAD Connect 同步到租户的用户。 此用户是在 Azure AD 中直接创建的。 使用用于 Windows PowerShell 的 Azure AD 模块中的 **Get-MsolUser** 和 **Set-MsolUser** cmdlet 来查看或指定将在其中存储仅限云的用户邮箱的地理位置。

若要查看用户的 **PreferredDataLocation** 值，请在 Azure AD PowerShell 中使用此语法：

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

例如，若要查看用户 michelle@contoso.onmicrosoft.com 的 **PreferredDataLocation** 值，请运行以下命令：

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

若要修改仅限云的用户对象的 **PreferredDataLocation** 值，请在 Azure AD PowerShell 中使用以下语法：

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

例如，若要为用户 michelle@contoso.onmicrosoft.com 将 **PreferredDataLocation** 值设置为欧盟 (EUR) 地理位置，请运行以下命令：

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**注意**：

- 如前所述，你不能为从本地 Active Directory 同步的用户对象使用此过程。 你需要在 Active Directory 中更改 **PreferredDataLocation** 值，并使用 AAD Connect 进行同步。 有关详细信息，请参阅 [Azure Active Directory Connect 同步：为 Microsoft 365 资源配置首选数据位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。

- 将邮箱重定位到新的地理位置所花费的时间取决于若干因素：

  - 邮箱的大小和类型。

  - 正在移动的邮箱数量。

  - 移动资源的可用性。

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>移动处于诉讼保留状态的已禁用邮箱

对于处于诉讼保留状态的已禁用邮箱，无法通过在已禁用状态下通过更改其 **PreferredDataLocation** 值来移动这些邮箱。 若要移动处于诉讼保留状态的已禁用邮箱，请执行以下操作：

1. 暂时为邮箱分配一个许可证。

2. 更改 **PreferredDataLocation**。

3. 在将邮箱移到所选地理位置之后从邮箱中删除许可证，将其重新置于禁用状态。

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>在特定地理位置中创建新的云邮箱

若要在特定地理位置中创建新邮箱，你需要执行以下任一步骤：

- 在 Exchange Online 中创建邮箱*之前*，按上一节中所述配置 **PreferredDataLocation** 值。 例如，在分配许可证之前为用户配置 **PreferredDataLocation** 值。

- 在设置 **PreferredDataLocation** 值的同时分配许可证。

若要在特定地理位置中创建新的仅限云许可用户（未通过 AAD Connect 同步），请在 Azure AD PowerShell 中使用以下语法：

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

此示例使用下面的值为 Elizabeth Brunner 创建新用户帐户：

- 用户主体名称：ebrunner@contoso.onmicrosoft.com

- 名字：Elizabeth

- 姓氏：Brunner

- 显示名称：Elizabeth Brunner

- 密码： 随机生成，并显示在命令的结果中（因为我们未使用 *Password* 参数）

- 许可证：`contoso:ENTERPRISEPREMIUM` (E5)

- 位置：澳大利亚 (AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

有关创建新用户帐户和在 Azure AD PowerShell 中查找 LicenseAssignment 值的详细信息，请参阅[使用 PowerShell 创建用户帐户](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)和[使用 PowerShell 查看许可证和服务](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)。

> [!NOTE]
> 如果使用 Exchange Online PowerShell 启用邮箱并需要在 **PreferredDataLocation** 中所指定的地理位置中直接创建邮箱，你需要直接针对云服务使用诸如 **Enable-Mailbox** 或 **New-Mailbox** 等 Exchange Online cmdlet。 如果在本地 Exchange PowerShell 中使用 **Enable-RemoteMailbox** cmdlet，则会在中心地理位置创建邮箱。

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>在特定地理位置中载入现有本地邮箱

你可以使用标准载入工具和流程将邮箱从本地 Exchange 组织迁移到 Exchange Online，这些工具和流程包括 [EAC 中的“迁移”仪表板](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)，以及 Exchange Online PowerShell 中的 [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet。

第一步是验证用户对象对于要载入的每个邮箱是否存在，并验证是否在 Azure AD 中配置了正确的 **PreferredDataLocation** 值。 载入工具将考虑 **PreferredDataLocation** 值，并将邮箱直接迁移到指定地理位置。

或者，你可以使用以下步骤，通过 Exchange Online PowerShell 中 [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet 在特定地理位置中直接载入邮箱。

1. 验证用户对象对于要载入的每个邮箱是否存在，并且是否在 Azure AD 中将 **PreferredDataLocation** 设置为所需的值。 **PreferredDataLocation** 的值将同步到 Exchange Online 中对应邮件用户对象的 **MailboxRegion** 属性。

2. 使用本主题前面的连接说明直接连接到特定附属地理位置。

3. 在 Exchange Online PowerShell 中，通过运行以下命令，将用于执行邮箱迁移的本地管理员凭据存储在一个变量中：

   ```powershell
   $RC = Get-Credential
   ```

4. 在 Exchange Online PowerShell 中，创建一个类似于以下示例的新 **New-MoveRequest**：

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. 为需要从本地 Exchange 迁移到当前连接的附属地理位置的每个邮箱重复步骤 4。

6. 如果需要将其他邮箱迁移到不同的附属地理位置，请为每个特定位置重复步骤 2-4。

## <a name="multi-geo-reporting"></a>多地理位置报告

Microsoft 365 管理中心中的“**多地理位置使用情况报告**”按地理位置显示用户计数。 该报告显示当前月份的用户分布，并提供过去 6 个月的历史数据。

## <a name="see-also"></a>另请参阅

[使用 Windows PowerShell 管理 Microsoft 365 和 Exchange Online](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)
