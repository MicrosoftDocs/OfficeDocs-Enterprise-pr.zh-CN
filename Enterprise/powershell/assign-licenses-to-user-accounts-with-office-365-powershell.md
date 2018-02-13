---
title: "使用 Office 365 PowerShell 向用户帐户分配许可证"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other, LIL_Placement, PowerShell, O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "解释如何使用 Office 365 PowerShell 分派给未经授权的用户的 Office 365 提供许可证。"
ms.openlocfilehash: 11724e7f295079b76bbb9006bad1fb5487087bd8
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 向用户帐户分配许可证

**摘要：** 解释如何使用 Office 365 PowerShell 分派给未经授权的用户的 Office 365 提供许可证。
  
Office 365 中的用户帐户授权很重要，因为用户不能使用任何 Office 365 提供服务，直到他们的帐户被授予使用许可。您可以使用 Office 365 PowerShell 高效地将许可证分配给未授权的帐户，尤其是多个帐户。 

## <a name="before-you-begin"></a>开始之前
<a name="RTT"> </a>

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 使用**Get MsolAccountSku** cmdlet 可以在组织中的每个计划中查看可用的授权计划和可用的许可证数。每个计划中的可用许可证数量是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。有关授权计划、 许可协议和服务的详细信息，请参阅[查看许可证和服务与 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)。
    
- 若要查找未授权的帐户您的组织中，运行命令`Get-MsolUser -All -UnlicensedUsersOnly`
    
- 您可以仅对具有**UsageLocation**属性设置为有效的 ISO 3166-1-2 字母的国家/地区代码的用户帐户分配许可证。例如，我们的美国和法国的 FR。在某些国家，某些 Office 365 服务不可用。有关详细信息，请参阅[关于许可限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。
    
    若要查找帐户没有一个**UsageLocation**值，运行命令`Get-MsolUser -All | where {$_.UsageLocation -eq $null}`。若要在某个帐户上设置**UsageLocation**值，请使用语法`Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`。例如， `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`。
    
- 如果您使用**Get MsolUser** cmdlet 而无需使用`-All`参数，返回前 500 个客户。
    
## <a name="the-short-version-instructions-without-explanations"></a>简版（说明不含解释）
<a name="ShortVersion"> </a>

此部分介绍了没有详细说明的过程。如果您有疑问或想了解更多信息，您可以阅读本主题的其余部分。
  
要将许可证分配给用户，请在 Office 365 PowerShell 中使用下面的语法：
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

本示例指定从许可证`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3) 给未经授权的用户的授权计划`belindan@litwareinc.com`。
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

若要向多个未授权用户分配许可证，请使用以下句法：
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **备注**
  
- 您无法使用相同的许可计划为用户分配多个许可证。
    
- 如果没有足够可用的许可证，许可证分配给用户他们正在**获取 MsolUser** cmdlet 返回之前的可用许可证不足的顺序。
    
本示例指定许可证`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3) 对所有未经授权的用户的授权计划。
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

本示例向美国销售部门的未授权用户分配这些相同的许可证。
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>长版（说明附有详细解释）
<a name="LongVersion"> </a>

[查看授权和未授权用户使用 Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md)文章中所述，就可能让用户拥有有效的 Office 365 提供用户帐户，但谁不发动了哪些 Office 365 提供许可证。这意味着，有效的帐户或任何有效的帐户，这些用户不能登录到 Office 365。然后，如果您无法登录，则不能利用任何 Office 365 提供服务。
  
上述文章还说明了我们可以通过运行此命令返回未许可用户帐户的列表：
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

该命令将返回任何用户的 Office 365 目前尚未得到有关的信息：
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

正如您所看到的我们有一个未授权的用户： Belinda Newman。因此我们如何分配 Belinda Office 365 许可证？
  
对于初学者，我们将运行**Get MsolAccountSku** cmdlet[查看许可证和服务与 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)文章所述：
  
```
Get-MsolAccountSku
```

此命令将返回类似于以下的数据：
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

我们是为什么运行**获取 MsolAccountSku**的？("Sku，"如果您想知道，是的缩写"库存单元。对于我们来说，它是只是业务-说出的"产品。）有两个原因为什么我们运行**Get MsolAccountSku**。首先，我们需要确保我们实际上有一个许可证分配 Belinda。我们有，我们可以将其分配任何许可证吗？若要确定，我们会**ActiveUnits**属性 (25) 的值，并减去**WarningUnits** (0) 和**ConsumedUnits** (24) 属性的值：
  
 `25 - 0 - 24 = 1`
  
**ActiveUnits**属性告诉我们我们购买的许可证数量和组合的值的**WarningUnits**和**ConsumedUnits**告诉我们多少个许可证目前正在使用。如果我们减去已说的从我们购买的许可证数量的许可证的数量，我们将知道多少个许可证是否仍然可用。会让它，因为我们有一个许可证可用于分发：
  
 `25 - 0 - 24 = 1`
  
第二，为了新的许可证，我们需要知道我们授权计划的名称分配 Belinda （这就是说，我们需要知道**AccountSkuId** ）。在这种情况下，这很简单： 我们只有一个单一的授权计划 ( `litwareinc:ENTERPRISEPACK`)。但是请注意，可能会对组织有多个授权计划。在这种情况下， **Get MsolAccountSku**将返回两个不同**AccountSkuIds**，您将需要选择相应的授权计划分配许可证时。现在，不过，我们要坚持使用最简单的情况，假设我们只是一个授权的计划。
  
那么如何**我们分配 Belinda Newman 新的许可证？喜欢这个：
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

也是您需要做： 只需调用**一组 MsolUserLicense** cmdlet，确保您指定的用户和相应的授权计划的_范围内_参数。
  
当**一组 MsolUserLicense**完成运行时，您会看到类似于此屏幕上：
  
 `PS C:\\windows\\system32>`
  
换句话说，它不会看起来有的事情。验证用户具有已分配的许可，运行如下命令：
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

如果一切运行正常，您应看到现在将 Belinda 的 isLicensed 属性设置为 True:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [!安全说明]: 问得好： 如果您犯了一个并尝试向已有许可证的用户分派许可证？您最终会为单个用户提供两个许可证？> 快速的答案吗？没有;Office 365 不允许您分配给同一用户的多个许可证。（好吧，从相同的授权计划的多个许可证，这就是。如果您尝试这样做您的命令将失败并显示以下错误消息： > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> 不可否认，此错误消息是稍微有点令人误解： 许可证不是真的无效，它只是分配给用户谁已经*有*一个许可证。但是，放在一边，错误消息的重要的事情是一个用户不会得到多个许可证。
  
如刚才所见，它是非常容易使用的 Office 365 PowerShell 将单个许可证分配给单个用户。和这产生了一个明显的问题： 岂不是一样简单，也许更容易，使用 Office 365 管理中心为单个用户分配单个许可证？嗯，有可能;这取决于，在情况下，无论您是使用 Windows PowerShell 更舒适或更娴熟地使用 Office 365 管理中心。其中 Windows PowerShell 确实非常出色，但是，是当您需要分配给多个用户的多个许可证。例如，此命令将 Office 365 许可证分配给任何没有许可证的用户：
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

在上述命令中，我们使用**Get MsolUser**和_UnlicensedUsersOnly_参数来返回所有未授权的用户帐户的集合。我们然后将该集合传递到**一组 MsolUserLicense** cmdlet;反过来，**集 MsolUserLicense**分配许可证 (来自`litwareinc:ENTERPRISEPACK`授权计划) 为集合中的每个用户。
  
不过，如果有 5 个未经许可的用户，但只有一个可用的许可证？在这种情况下**设置 MsolUserLicense**将**获得 MsolUser**返回的第一个用户提供可用的许可证。**集 MsolUserLicense**将尽职尽责地试图向其他四个用户分派许可证，但这些尝试的所有四个会失败以及下面的错误消息：
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
换句话说，一组 MsolUserLicense 不会只是失败。相反，它将指定任意多个许可证，因为它可以。那时将会失败。
  
让我们尝试另一个示例。也许您想要向销售部门中的所有用户分派许可证。没关系：
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

或者，如果您想要来点新奇的，想将错误消息和计算处理保持在最低水平，只需将许可证分配给销售部门中的未许可用户。
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

毕竟，没有尝试已有许可证的许可证用户点。因为我们已经看到，它不起作用。
  
这里是另一个示例。也许您想要所有美国用户的当前没有 Office 365 都许可证的都许可证。在这种情况下：
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

等等。
  
> [!NOTE]
> 若要运行的命令说，对所有未经授权的用户颁发许可证需要多长时间？这是难以说： 这取决于您有为您的网络连接速度的用户数，无所不包。如果您有几个用户许可证这会相当快速地转到 （即，它不会花费超过一分钟或两个）。如果有 10000 个用户许可它显然需要稍长的时间。但远，只要它能够通过使用 Office 365 管理中心将许可证分配给 10000 个用户。 
  
只要我们在主题上，以下是您需要提防的分配许可证时： 如果用户没有配置为**UsageLocation**属性的值则不能将该用户指派一个 Office 365 提供许可证。相反，将收到错误信息类似于这样：
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
有点迂回的方式，此错误消息告诉我们，问题中的用户不具备**UsageLocation**。您可能已经猜到， **UsageLocation**属性 （这表明该地区或国家用户通常使用 Office 365） 是极其重要的。为什么？这是因为用户可用的服务不只取决于用户所在的位置还购买许可包： 由于局部规则和法规，有些服务可能不能给某些用户。如果用户没有**UsageLocation**，Office 365 已无法知道哪些服务可以依法公开给该用户。因此，Office 365 无法提供任何服务用于该用户，至少不直到指定了**UsageLocation** 。
  
> [!NOTE]
> 配置用户帐户时您将立即知道是否有与世界上的指定部分的所有许可限制。例如，如果将**UsageLocation**为已授权的用户更改为伊朗 ( `IR`)，该命令将失败，出现此错误消息： `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> 这是因为 Office 365 不是当前可供用户在伊朗。有关详细信息，请参阅[关于许可限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。顺便说一下，Office 365 使用标准化 (ISO) 由国际组织的双字母国家/地区代码。您可以在[ISO 网站](https://go.microsoft.com/fwlink/p/?LinkId=84073)上找到这些代码。 
  
如果您想要验证给定的用户有**UsageLocation** ，您可以使用类似下面的命令：
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

或者，可以返回使用此命令没有**UsageLocation**的所有用户的列表：
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> 当您分派许可证给用户，用户，默认情况下允许访问到您的组织有权访问的所有 Office 365 提供服务。例如，如果您的 Office 365 企业 E3 购买许可证，新授权用户将自动授予访问 Exchange 联机、 Skype 等服务的在线业务和 SharePoint Online。如果您希望限制对这些服务的用户的访问权限 (例如，您可能希望用户能够访问 SharePoint Online 但*不是*到 Exchange 联机和 Skype 的在线业务) 然后，请参阅文章[禁用访问 Office 365 的服务PowerShell](disable-access-to-services-with-office-365-powershell.md)。 
  
## <a name="new-to-office-365"></a>刚开始接触 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>另请参阅
<a name="SeeAlso"> </a>

请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：
  
- [使用 Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除和还原用户帐户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 冻结用户账户](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除用户帐户的许可证](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：
  
- [获得 MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [一组 MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [选择对象](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

