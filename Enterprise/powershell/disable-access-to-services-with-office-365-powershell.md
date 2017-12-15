---
title: "使用 Office 365 PowerShell 禁止访问服务"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "解释如何使用 Office 365 PowerShell 添加或删除组织中用户的 Office 365 提供服务的访问。"
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>使用 Office 365 PowerShell 禁止访问服务

**摘要：**解释如何使用 Office 365 PowerShell 添加或删除组织中用户的 Office 365 提供服务的访问。
  
在 Office 365 帐户从授权计划分配许可证，Office 365 提供服务可供用户从该许可证。但是，您可以控制用户可以访问 Office 365 提供服务。例如，即使许可证允许访问 SharePoint Online，您可以禁用对它的访问。事实上，您可以使用 Office 365 PowerShell 禁止任意数量的服务的访问：
- 单个帐户。
    
- 一组帐户。
    
- 组织中的所有帐户。
    
 **内容：**[简短的版本 （无需解释的说明）](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[长版 （详细的解释与说明）](disable-access-to-services-with-office-365-powershell.md#LongVersion)[请参见](disable-access-to-services-with-office-365-powershell.md#SeeAlso)
## <a name="before-you-begin"></a>开始之前
<a name="RTT"> </a>

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 使用**Get MsolAccountSku** cmdlet 以查看您可用的授权计划，并可在这些计划中的 Office 365 提供服务。有关详细信息，请参阅[查看许可证和 Office 365 PowerShell 的服务](view-licenses-and-services-with-office-365-powershell.md)。
    
- 若要查看之前和之后本主题中的过程的结果，请参阅[查看帐户许可证和服务的详细信息与 Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)。
    
- PowerShell 提供了一个脚本来自动执行本主题中描述的过程。具体来说，脚本允许您查看和您 Office 365 的组织，包括 Sway 中禁用这些服务。有关详细信息，请参阅[禁用 Office 365 PowerShell 的 Sway 访问](disable-access-to-sway-with-office-365-powershell.md)。
    
- 如果您使用 **Get-MsolUser** cmdlet 而无需使用 _All_ 参数，仅可返回前 500 个帐户。
    
## <a name="the-short-version-instructions-without-explanations"></a>简版（说明不含解释）
<a name="ShortVersion"> </a>

此部分介绍的步骤未经任何渲染或过多解释。如果您有任何疑问或想了解更多信息，可以阅读本主题的其余部分。
  
要禁用 Office 365 提供服务的用户从单个授权计划，请执行以下步骤：
  
1. 通过使用下面的语法授权计划中确定的令人不快的服务：
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    本示例创建一个**LicenseOptions**对象，名为授权计划中禁用 Office Online 和 SharePoint Online 服务`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3)。
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. 对一个或多个用户使用步骤 1 中的**LicenseOptions**对象。
    
  - 若要创建一个已禁用服务的新帐户，请使用以下语法：
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    本示例为 Allie Bellew 创建一个新帐户，用来分配许可证和禁用步骤 1 中所述的服务。
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    有关在 Office 365 PowerShell 创建用户帐户的详细信息，请参阅[Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)。
    
  - 若要禁用现有授权用户的服务，请使用下面的语法：
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    本示例对用户 BelindaN@litwareinc.com 禁用服务。
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - 若要禁用所有现有的授权用户在步骤 1 中所描述的服务，指定 Office 365 计划从**Get MsolAccountSku** cmdlet （如**litwareinc:ENTERPRISEPACK** )，显示的名称，然后运行下面的命令：
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - 若要对一组现有用户禁用服务，请使用下列两种方法之一来确定用户：
    
  - **筛选器基于现有帐户属性的帐户**若要执行此操作，请使用下面的语法：
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    本示例对美国销售部门的用户禁用服务。
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **使用特定的帐户列表**若要执行此操作，请执行以下步骤：
    
1. 创建一个文本文件，在它的每一行上包含一个帐户，如下所示：
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    在此示例中，该文本文件是 c:\\我的文档\\Accounts.txt。
    
2. 运行以下命令：
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

要禁用 Office 365 提供服务的用户，而分配的授权计划，请参阅[禁止访问服务时指派用户许可证](disable-access-to-services-while-assigning-user-licenses.md)。
  
若要禁用用户的 Office 365 提供服务中所有可用的授权计划，请执行以下步骤：
  
1. 将此脚本复制并粘贴到记事本。
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. 为您的环境自定义以下值：
    
  -  _<UndesirableService>_在此示例中，我们将使用 Office 联机和 SharePoint Online。
    
  -  _<Account>_在此示例中，我们将使用 belindan@litwareinc.com。
    
    自定义的脚本如下所示：
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. 保存为脚本`RemoveO365Services.ps1`在易于查找的位置。对于本示例，我们将保存文件" `C:\\O365 Scripts`"。
    
4. 通过使用下面的命令在 Office 365 PowerShell 运行该脚本。
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> 若要反转这些过程的影响 (即以重新启用这些禁用的服务)，再次运行该过程，但使用的值`$null` _DisabledPlans_参数。
  
[返回页首](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a>长版（说明附有详细解释）
<a name="LongVersion"> </a>

默认情况下，当您通过使用 Office 365 PowerShell 颁发许可证启用所有服务。通常这就是一件好事： 这意味着，您可以快速而轻松地分配许可证用户而无需指定启用前进路上的每个服务。
  
虽然这样说，但是，它也是如此，您可能想要限制可用的服务您的部分用户;例如，也许某些用户能够访问 Office Professional Plus，Skype 在线业务和 Exchange 联机，但那些相同的用户无权访问到 SharePoint Online 或 Office 联机。您可以限制以该方式的帐户？事实证明，也可以。为了帮助说明该方法的原理，让我们处理此问题采取一种两步的方法：
  
1. 为该用户指派的所有服务将自动都启用 Office 365 提供许可证。
    
2. 运行 Office 365 PowerShell 命令，禁用该用户指定的服务的一对。
    
我们已经采取关心的第 1 步： 我们的用户 (Belinda Newman) 已经为她提供了对所有 Office 365 提供服务的访问 Office 365 提供许可证。然而，我们想要修改 Belinda 的帐户，以使她不能访问 SharePoint Online ( `SHAREPOINTENTERPRISE`) 或 Office Online ( `SHAREPOINTWAC`)。但是，我们应如何做到这一点呢？
  
下面是如何。开头的我们将使用**新建 MsolLicenseOptions** cmdlet 来创建一个**LicenseOption**对象，该对象包含了我们想要禁用的服务。在 Belinda 的情况下，我们想要禁用`SHAREPOINTENTERPRISE`， `SHAREPOINTWAC`，因此我们使用以下命令：
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

看到它的工作原理吗？指定的授权计划 ( `litwareinc:ENTERPRISEPACK`)，然后指明每个禁用的服务所需，用逗号隔开这些服务。
  
> [!NOTE]
> 请确保将您的新**LicenseOption**对象存储在变量中。在前面的示例中，我们使用`$x`，但您可以使用任何有效的 Windows PowerShell 变量名称。 
  
此时我们可以使用下面的命令以禁用 Belinda 的对这两项服务的访问权限：
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

没有什么特别在这里，或者： 我们只是调用**一组 MsolUserLicense** cmdlet 和_LicenseOptions_参数，以及变量包括 ( `$x`) 包含要禁用的计划。然后我们看到了什么现在是否我们看一下 Belinda 的许可证信息通过运行命令： `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`？我们看到：
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

很酷吧？而且，当然，我们可以做同一问题给多个用户如果我们想的话。例如，以下命令禁用为所有许可用户相同的两个服务。指定的名称 （如**litwareinc:ENTERPRISEPACK** )，**获得 MsolAccountSku** cmdlet 的显示 Office 365 计划并运行它们。
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

请记住 Belinda 仍有有效的 Office 365 许可证;它就是现在，她有权访问更少服务。我们禁用这两项服务之前，Belinda 有新闻、 OneDrive 和 SharePoint 访问联机站点：
  
![具有 SharePoint 访问权限的用户。](images/o365_powershell_with_sharepoint.png)
  
现在这些选项对她不再可用：
  
![没有 SharePoint 访问权限的用户。](images/o365_powershell_without_sharepoint.png)
  
这正是我们希望发生的。
  
并且如果我们改变我们的主意以后： 是否可以重新启用这些服务？当然可以。要重新启用所有用户的服务，只需使用此命令创建下面的**LicenseOption**对象：
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

该命令的作用是什么？以开头的 Windows PowerShell 常数`$null`表示"没有"。（或者，在稍有更多的技术语言，它意味着"空值"。）作为您回想一下，当我们使用**New MsolLicenseOptions** cmdlet 我们必须表示我们想要禁用的服务。在这种情况下，我们不希望任何服务被禁用。它可能会导致您相信我们可以使用如下所示，在其中我们不指定_DisabledPlans_参数的值的命令的命令：
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

但是，它将不起作用。相反，则会生成一条错误消息：
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
幸运的是我们，将参数值设置为`$null`可以正常工作：
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

这只意味着，当我们运行**一组 MsolUserLicense** cmdlet，我们会告诉**集 MsolUserLicense** ，我们不希望 Belinda 具有任何已禁用的服务：
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

如果没有禁用任何服务，这必须意味着所有服务都已启用，这很合理。
  
既然您了解了整个工作原理，让我们向您展示如何颁发许可证并禁用指定的服务，并且都具备相同的命令。听起来非常深刻的印象，但老实说，其实没什么对它： 您只需包括_AddLicenses_和_LicenseOptions_参数在相同的命令。换句话说，您首先创建**LicenseOption**对象：
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

然后，然后，正如前述，使用_AddLicenses_和_LicenseOptions_参数在您的命令：
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

命令将发出 Belinda Newman 新的许可证，但许可证的 Skype 的在线业务 ( `SHAREPOINTWAC`) 和 SharePoint Online ( `SHAREPOINTENTERPRISE`) 都被禁用。
  
[返回页首](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a>刚开始接触 Office 365？
<a name="LongVersion"> </a>

||
|:-----|
|![LinkedIn 学习的短图标](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 提供指向新建？**        **Office 365 管理员和 IT 专业人员使用**，LinkedIn 学习者发现免费视频课程。 |
   
## <a name="see-also"></a>See also
<a name="SeeAlso"> </a>

请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：
  
- [使用 Office 365 PowerShell 删除和还原用户账户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除和还原用户账户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 冻结用户账户](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 向用户帐户分配许可证](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)
    
有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：
  
- [获取内容](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [获得 MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [新 MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [获得 MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [新 MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [一组 MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach 对象](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[返回页首](disable-access-to-services-with-office-365-powershell.md#RTT)
  

