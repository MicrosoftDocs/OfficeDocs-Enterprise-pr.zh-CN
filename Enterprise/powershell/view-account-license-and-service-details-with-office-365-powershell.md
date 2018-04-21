---
title: 使用 Office 365 PowerShell 查看帐户许可证和服务详细信息
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/19/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: 解释如何使用 Office 365 PowerShell 确定已指派给用户的 Office 365 提供服务。
ms.openlocfilehash: 5286a581a67b39d5d5ca921b998d6ea14b3ff50f
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>使用 Office 365 PowerShell 查看帐户许可证和服务详细信息

**摘要：**解释如何使用 Office 365 PowerShell 确定已指派给用户的 Office 365 提供服务。
  
Office 365 中许可证的授权计划 （也称为的 Sku 或 Office 365 计划） 允许用户访问的计划，这些计划定义 Office 365 提供服务。但是，用户可能不具有访问中当前分配给它们的许可证提供的所有服务。Office 365 PowerShell 可用于对用户帐户查看服务的状态。 

## <a name="before-you-begin"></a>开始之前
<a name="RTT"> </a>

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 使用命令`Get-MsolAccountSku`和`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`查找以下信息：
    
  - 您的组织中提供的许可计划。
    
  - 每个许可计划中提供的服务以及列出它们的顺序（索引号）。
    
     有关授权计划、 许可和服务的详细信息，请参阅[查看许可证和服务与 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)。
    
- 使用命令`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`若要查找分配给用户，并在订单的许可证所列 （索引号）。
    
- 如果您使用 **Get-MsolUser** cmdlet 而无需使用 _All_ 参数，仅可返回前 500 个帐户。
    
<a name="ShortVersion"> </a>
## <a name="the-short-version-instructions-without-explanations"></a>简版（说明不含解释）

若要查看用户有权访问的所有 Office 365 PowerShell 的服务，请使用下面的语法：
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

本示例显示 BelindaN@litwareinc.com 的用户有权访问的服务。这将显示与所有许可证分配给她的帐户相关联的服务。
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

本示例说明了用户 BelindaN@litwareinc.com 使用向她的帐户（索引号是 0）分配的第一个许可证有权访问的服务。
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

若要查找已启用或未启用特定服务的所有授权用户，请使用下面的语法：
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

这些示例使用下面的信息：
  
- 使我们感兴趣的 Office 365 服务访问的许可证是第一个许可证分配给所有用户 （索引号为 0）。
    
- 我们感兴趣的 Office 365 提供服务是 Skype 的在线业务和在线交换。对于与授权计划关联的许可证，Skype 的在线业务是列出六个服务 （索引号为 5），且 Exchange Online 9 日服务列出 （索引号为 8）。
    
本示例返回所有获得许可的用户启用了 Skype 的在线业务和在线交换。
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

本示例返回所有授权的用户未启用 Skype 的在线业务或 Exchange 联机。
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<a name="LongVersion"> </a>
## <a name="the-long-version-instructions-with-detailed-explanations"></a>长版（说明附有详细解释）

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a>查找用户有权访问 Office 365 PowerShell 服务

很显然一定要知道哪些用户已签发 Office 365 的许可证以及哪些用户还没有。（请参阅文章[使用 Office 365 PowerShell 的授权和未授权用户查看](view-licensed-and-unlicensed-users-with-office-365-powershell.md)详细信息）。但是，仅有一个 Office 365 许可证并没有告诉您的任何有关该用户实际上如何使用 Office 365。可以他或她使用 Exchange 联机或 Skype 的在线业务？此用户可以访问 SharePoint Online 吗？他或她是否有权访问 Office Professional Plus？没有许可证只是意味着用户都有可能来访问这些服务。但是，提供给用户的功能取决于他或她的许可证已启用的服务。
  
我们如何可以确定哪些 Office 365 功能用户具有访问权限？为此，我们需要运行一个与此类似的命令：
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

在此命令中，我们使用**Get MsolUser** cmdlet 返回有关 BelindaN@litwareinc.com 的帐户信息。一旦我们已经返回该信息，然后管道为**选择对象**cmdlet 的帐户数据，提出要"展开"**许可证**属性的值的**选择对象**：
  
 `Select-Object -ExpandProperty Licenses`
  
这么做的原因？好的默认情况下，**许可证**属性只告诉我们 Belinda 的许可证来自何处的许可包的名称：
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

"展开"**许可证**属性为我们提供了一些详细信息：
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

然后通过扩展的**ServiceStatus**属性我们可以得到更多的信息：
  
|服务计划 ***|****Description****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure 权限管理 (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online 计划 2  <br/> |
   
> [!NOTE]
> 您说这是太多键入？好吧，如果您可以用很少的 Windows PowerShell obtuseness 拍卖中，您可以运行命令此精简的版本相反： >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`
  
如果您想知道，我们可以"展开"**许可证**属性因为**许可证**是多值的属性： 它是单个属性，可以存储多个值。当我们展开一个属性值，我们只是向下钻取获得下列附加属性值，默认情况下，则不会显示在屏幕上。
  
> [!NOTE]
> 因此是您是如何知道一个值是多值的属性？嗯，要查找出的问题，请尝试运行与以下类似的命令： > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`>**获取成员**cmdlet 返回信息的对象，然后重试。在这种情况下，属性信息值组成用户帐户对象。这里是说有关**许可证**属性**获取成员**有： > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> 如果有关集合的属性定义说点什么 (在这种情况下， `System.Collections.Generic.List`) 则可以确定要处理的多值属性。 
  
那么什么？ 所有这是否意味着要回答此问题，让我们首先看另一个**Get MsolUser** cmdlet 返回的信息看：
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

然后，让我们也看一看表，解释这些奇怪命名服务计划的真正代表：
  
|服务计划 ***|****Description****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure 权限管理 (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online 计划 2  <br/> |
   
都清楚了吗？ `MCOSTANDARD`是在线业务只是为 Skype 的内部编程名称时`OFFICESUSBCRIPTION`只是 Office Professional Plus 的内部编程名称。它不是最直观明了，但只要您保留此表方便使用 Office 365 提供服务时不会有很多问题。
  
但等待： 还有更多。当我们[查看许可证和服务与 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)，文章中都学到，如果将**ProvisioningStatus**设置为`Success`则表示，已完全启用服务;例如如果`MCOSTANDARD`设置为`Success`，意味着用户可以访问 Skype 的在线业务。如果将**ProvisioningStatus**设置为`PendingInput`，意味着 Office 365 仍在处理服务请求;但是，用户通常可以登录并访问服务，而该请求完成处理。(`YAMMER_ENTERPRISE`将始终显示为`PendingInput`，但这也没关系:，不会阻止用户登录到 Yammer)。
  
> [!IMPORTANT]
> 用户可以安装并激活新的 Office Professional Plus 安装时`OFFICESUBSCRIPTION`在`PendingInput`状态。
  
并且，毫无疑问，是一项服务设置为`Disabled`，意味着讨论的服务的不是向用户提供。
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a>查找用户有权访问特定的 Office 365 PowerShell 服务

在单独的文章中，我们看到了如何使用 Office 365 PowerShell 禁用用户对服务的访问。（如果您错过了这篇文章，请参阅[禁用访问 Office 365 PowerShell 的服务](disable-access-to-services-with-office-365-powershell.md)）。这产生了一个明显的问题： 有什么办法可以确定哪些*用户*(即多个用户) 已启用或禁用的服务？
  
我们希望有人会问这个问题。为了回答这个问题，让我们回顾一下我们第一次看文章[查看许可证和服务与 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)中我们唯一可用的授权计划的服务的表`litwareinc:ENTERPRISEPACK`:
  
|服务计划 ***|****Description****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure 权限管理 (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online 计划 2  <br/> |
   
您可能还记得，服务计划只是一种产品; 的内部编程名称例如， `OFFICESUBSCRIPTION`，为一个名称，则 Office Professional Plus 的内部编程名称。如果`OFFICESUBSCRIPTION`显示为`SUCCESS`对用户的服务计划，则意味着允许用户访问 Office Professional Plus。如果`EXCHANGE_S_ENTERPRISE`被列为`DISABLED`，意味着用户不能使用 Exchange 联机。
  
> [!IMPORTANT]
> 用户可以安装并激活新的 Office Professional Plus 安装时`OFFICESUBSCRIPTION`在`PendingInput`状态。
  
现在是时间服务的顺序是极其重要的位置。Windows PowerShell 将分配给列表中的每一项的索引号。第一项是 0 下, 一项为 1，依此类推。结果详见下表：
  
|索引号 ***|服务计划 ***|
|:-----|:-----|
|0  <br/> | `SWAY` <br/> |
|1  <br/> | `INTUNE_O365` <br/> |
|2  <br/> | `YAMMER_ENTERPRISE` <br/> |
|3  <br/> | `RMS_S_ENTERPRISE` <br/> |
|4  <br/> | `OFFICESUBSCRIPTION` <br/> |
|5  <br/> | `MCOSTANDARD` <br/> |
|6  <br/> | `SHAREPOINTWAC` <br/> |
|7  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|8  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
正如您所看到的`SWAY`第一个服务列出，因此，它获取指定索引号是 0。
  
> [!CAUTION]
> 为什么 0 和 1 的不？这就是编程的事情。编程语言中索引告诉您远一项从数组的开头"偏移"。第一项*为*数组，因此其偏移量为 0 开头。第二项是从一开始的 1 项的数组，因此其偏移量为 1。
  
我们可以试一个示例。假设我们想要的所有授权用户都尚未启用 Exchange 联机列表。要做到这一点，我们可以使用下面的命令：
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

不可否认，正是般简单的命令，让我们花点时间来解释它的工作原理。这是实际上分为两部分的命令，并且第一部分非常简单： 我们使用**Get MsolUser** cmdlet 返回我们 Office 365 中的所有用户的集合 （有许可证的和无许可证的）：
  
```
Get-MsolUser
```

然后，这些信息被输送到**位置对象**cmdlet。**位置对象**经历的所有用户帐户并寻找这些帐户符合下列要求：
  
- **IsLicensed**属性等于 ( `-eq`) `True` ( `$true`)。它使我们能够滤出的未经授权的用户。
    
- **许可证 [0] 的值。ServiceStatus [8]。ProvisioningStatus**属性等于 ( `-eq`) `Disabled`。我们的直接目的，为此笨拙的属性名称的重要部分是：
    
     `ServiceStatus[8]`
    
    `[8]`表示 Exchange 联机索引号。（我们知道，从几分钟前查看表）。如果我们想怎么查找启用 Skype 的在线业务的所有用户？嗯，Skype 业务联机索引号是 5，因此我们将使用下面的语法：
    
     `ServiceStatus[5]`
    
    等等。
    
    顺便说一下，`Licenses[0]`表示我们想要看的授权计划。由于我们测试域中只有一个授权计划这不重要得多。但是，假设我们有已从两个不同的许可证计划许可证分配的用户。在这种情况下，`Licenses[0]`则表示第一个授权计划，和`Licenses[1]`则表示第二个的授权计划。
    
    若要查找分配给用户的许可证以及列出它们的顺序，请运行以下命令：
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

您看到了所有的工作原理？Office Professional Plus 的索引号是 4;因此，此命令会返回尚未为 Office Professional Plus 启用所有用户的列表：
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

并且要是我们想已*启用*Office Professional Plus 的用户的列表？好吧，如果您已启用了然后您**ServiceStatus**将`PendingInput`或`Success`;换句话说，您的**ServiceStatus**将*不*等 ( `-ne`) `Disabled`。这意味着我们所要做的就是采取我们前一个命令和换出`-eq`运算符，用于`-ne`运算符：
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

俗话说离时，代码可能不会赢得很多美妙的比赛。而且，事实告诉他们，该代码可以获取更多 tangled。例如，假设我们想要查找的用户已启用这两种 Skype 的在线业务和 Exchange Online 的：
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

但不要担心太多关于如何麻烦，可能看起来： 重要的是，与相对较少的工作，您可以检索此信息。无法获取同样的信息使用 Office 365 管理中心？从理论上讲，可以，但，在实际情况下，则不。若要获取同样的信息使用 Office 365 管理中心将需要查看每个用户的授权信息，一次，一个用户，然后手动跟踪的那些先前已启用*x*和谁没有。它会起作用，但让我们坦白： 如果您有多个 10 或 11 的用户，您不打算这样做。它是太乏味而耗时。
  
这，当然，这是为什么我们有 Windows PowerShell: Windows PowerShell 有助于节省您从乏味而耗时的任务，例如。
  
下面是用于查看一组指定服务的服务信息，由 Office 365 E5 订阅及其许可证和 ServiceStatus 的索引命令的示例：
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[12].ProvisioningStatus}}, @{Name="Teams";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[20].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[19].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[21].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[22].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[24].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[23].ProvisioningStatus}} | ConvertTo-CSV > "C:\Service Info.csv"
```

此命令创建 CSV 文件显示的所有用户和服务 （团队、 Yammer、 AD RMS、 OfficePro、 Skype、 SharePoint 和 Exchange） 的指定设置及其服务状态。

>[!Note]
>可以获取的服务列表中从订购`(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus`命令。在输出中，您开始编排服务索引为 0。上面的命令只是一个示例。随着时间的推移可以更改服务的索引号。
>

  
<a name="SeeAlso"> </a>
## <a name="see-also"></a>另请参阅

请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：
  
- [使用 Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除和还原用户账户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 冻结用户账户](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 向用户帐户分配许可证](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除用户帐户的许可证](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：
  
- [ConvertTo Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [格式列表](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [选择对象](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>刚开始接触 Office 365？


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]