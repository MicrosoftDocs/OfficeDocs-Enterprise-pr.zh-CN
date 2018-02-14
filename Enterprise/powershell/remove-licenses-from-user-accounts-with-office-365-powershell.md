---
title: "使用 Office 365 PowerShell 删除用户帐户的许可证"
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "解释如何使用 Office 365 PowerShell 删除先前已指派给用户的 Office 365 提供许可证。"
ms.openlocfilehash: c02d5a6cac029ce9beb8077da98418734d935ded
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 删除用户帐户的许可证

**摘要：**解释如何使用 Office 365 PowerShell 删除先前已指派给用户的 Office 365 提供许可证。
  
## <a name="before-you-begin"></a>开始之前

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 若要查看组织中的授权计划 ( **AccountSkuID** ) 信息，请参阅以下主题：
    
  - [使用 Office 365 PowerShell 查看许可证和服务](view-licenses-and-services-with-office-365-powershell.md)
    
  - [使用 Office 365 PowerShell 查看帐户许可证和服务详细信息](view-account-license-and-service-details-with-office-365-powershell.md)
    
- 如果使用 **Get-MsolUser** cmdlet，而未使用 _-All_ 参数，只返回前 500 个帐户。
    
## <a name="the-short-version-instructions-without-explanations"></a>简版（说明不含解释）
<a name="ShortVersion"> </a>

此部分介绍的步骤未经任何渲染或过多解释。如果您有任何疑问或想了解更多信息，可以阅读本主题的其余部分。
  
要从现有的用户帐户中删除许可证，请使用以下语法：
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

本示例删除`litwareinc:ENTERPRISEPACK`BelindaN@litwareinc.com 的用户帐户 (Office 365 企业 E3) 许可证。
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

要从一组现有的授权用户中删除许可证，请使用下列方法之一：
  
- **筛选器基于现有帐户属性的帐户**若要执行此操作，请使用下面的语法：
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

本示例删除`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3) 许可证从众所周知的美国销售部门中的用户。
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **使用特定的帐户列表**若要执行此操作，请执行以下步骤：
    
1. 创建并保存一个文本文件，其中每一行都有一个帐户，如下所示：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. 使用以下语法：
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

本示例删除`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3) 许可证 C:\My Documents\Accounts.txt 文件中定义的用户帐户。
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

要从所有现有的用户帐户中删除许可证，请使用以下语法：
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

本示例删除`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3) 从所有现有的许可证授权用户帐户。
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>长版（说明附有详细解释）
<a name="LongVersion"> </a>

不会永远持续下去，并包含 Office 365 许可证： 迟早会同时那里一次当您需要从用户帐户中移除许可证。也许用户怎么回事请假;也许用户不再需要许可证;也许-好吧，有显然因多种原因为什么您可能希望移除用户许可证。
  
我们进一步转很重要，请注意，删除许可证要求您，好之前，删除该许可证： 禁用许可证上的所有服务不是不同于删除许可证。例如，假设我们已经耗尽我们所有 Office 365 许可证;换句话说，我们没有任何可用许可证。如果决定采用中[禁止访问 Office 365 PowerShell 的服务](disable-access-to-services-with-office-365-powershell.md)来禁用所有服务，比如 Belinda Newman 帐户上的过程。我们所做，多少许可证后将我们有提供给我们？没错： 零。是的从该主题中的过程将*禁用*Belinda 的许可证上的所有服务，但它不都会禁用 （即删除） 许可证本身。许可证将仍然是有效的而且它仍将分配给 Belinda Newman。她只是不能使用该许可证访问 Office 365 提供的任何服务。
  
这一点很重要： 如果您想要删除用户的许可证，您必须实际*删除*许可证。禁用所有服务将阻止用户登录到 Office 365，但它不会释放他或她的许可。如果您想要收回一个许可证，当前分配给您需要运行与此类似，使用_RemoveLicenses_参数来实际删除以前分配给 Belinda 许可的命令的命令的用户：
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

运行该命令，并不再将授权 Belinda Newman 使用 Office 365。
  
> [!NOTE]
> 如您所见，当您使用_RemoveLicenses_参数必须指定要删除的许可证的名称。如果您不确定使用了哪些许可计划将许可证分配给用户只运行如下命令：`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`
  
若要确定许可证确实已删除，可使用 Get-MsolUser 检查提及的用户帐户：
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

如果一切按计划，将立即被 Belinda 的**isLicensed**属性设置`False`:
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

另一种方式来释放许可证是删除用户帐户。有关详细信息，请参阅[删除和还原 Office 365 PowerShell 的用户帐户](delete-and-restore-user-accounts-with-office-365-powershell.md)。
  
## <a name="see-also"></a>另请参阅

请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：
  
- [使用 Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除和还原用户帐户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 冻结用户账户](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 向用户帐户分配许可证](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：
  
- [获取内容](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [一组 MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a>刚开始接触 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

