---
title: "使用 Office 365 PowerShell 禁止访问服务"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "解释如何使用 Office 365 PowerShell 禁用 Office 365 提供服务，为您的组织中的用户访问。"
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>使用 Office 365 PowerShell 禁止访问服务

**摘要：**解释如何使用 Office 365 PowerShell 禁用 Office 365 提供服务，为您的组织中的用户访问。
  
在 Office 365 帐户从授权计划分配许可证，Office 365 提供服务可供用户从该许可证。但是，您可以控制用户可以访问 Office 365 提供服务。例如，即使许可证允许访问 SharePoint Online，您可以禁用对它的访问。事实上，您可以使用 Office 365 PowerShell 禁止任意数量的服务的访问：

- 单个帐户。
    
- 一组帐户。
    
- 组织中的所有帐户。
    
## <a name="before-you-begin"></a>准备工作
<a name="RTT"> </a>

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 使用**Get MsolAccountSku** cmdlet 以查看您可用的授权计划，并可在这些计划中的 Office 365 提供服务。有关详细信息，请参阅[查看许可证和 Office 365 PowerShell 的服务](view-licenses-and-services-with-office-365-powershell.md)。
    
- 若要查看之前和之后本主题中的过程的结果，请参阅[查看帐户许可证和服务的详细信息与 Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)。
    
- PowerShell 提供了一个脚本来自动执行本主题中描述的过程。具体来说，脚本允许您查看和您 Office 365 的组织，包括 Sway 中禁用这些服务。有关详细信息，请参阅[禁用 Office 365 PowerShell 的 Sway 访问](disable-access-to-sway-with-office-365-powershell.md)。
    
- 如果您不使用的_所有_参数使用**Get MsolUser** cmdlet，只有第一个 500 用户帐户返回。
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a>单个授权计划的特定用户的的特定 Office 365 提供服务
  
要禁用一组特定的用户从单个授权计划的 Office 365 提供服务，请执行以下步骤：
  
1. 通过使用下面的语法授权计划中确定的令人不快的服务：
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    下面的示例创建一个**LicenseOptions**对象，名为授权计划中禁用 Office Online 和 SharePoint Online 服务`litwareinc:ENTERPRISEPACK`(Office 365 企业 E3)。
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. 对一个或多个用户使用步骤 1 中的**LicenseOptions**对象。
    
  - 若要创建一个已禁用服务的新帐户，请使用以下语法：
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    下面的示例创建一个新帐户的 Allie Bellew 分配许可证和禁用在步骤 1 中所描述的服务。
    
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

  - 若要禁用所有现有的授权用户在步骤 1 中所描述的服务，指定 Office 365 计划从**Get MsolAccountSku** cmdlet （如**litwareinc:ENTERPRISEPACK**)，显示的名称，然后运行下面的命令：
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - 若要对一组现有用户禁用服务，请使用下列两种方法之一来确定用户：
    
  - **筛选器基于现有帐户属性的帐户**若要执行此操作，请使用下面的语法：
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    下面的示例禁用在美国销售部门中的用户服务。
    
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
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

要禁用 Office 365 提供服务的用户，而分配的授权计划，请参阅[禁止访问服务时指派用户许可证](disable-access-to-services-while-assigning-user-licenses.md)。
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a>用户能够从所有的授权计划的特定 Office 365 提供服务
  
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

3. 保存为脚本`RemoveO365Services.ps1`在易于查找的位置。对于本示例，我们将保存文件`C:\\O365 Scripts`。
    
4. 通过使用下面的命令在 Office 365 PowerShell 运行该脚本。
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> 若要反转这些过程的影响 (即以重新启用这些禁用的服务)，再次运行该过程，但使用的值`$null` _DisabledPlans_参数。
  
[返回页首](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a>所有 Office 365 提供服务的所有用户的单个许可计划
 
若要禁用所有 Office 365 提供服务的所有用户在某一特定的授权计划，授权计划为指定的名称 （如**litwareinc:ENTERPRISEPACK**)，$acctSKU，然后 PowerShell 命令窗口中运行以下命令：

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a>刚开始接触 Office 365？
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>另请参阅
<a name="SeeAlso"> </a>

请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：
  
- [使用 Office 365 PowerShell 删除和还原用户账户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除和还原用户帐户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 冻结用户账户](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 向用户帐户分配许可证](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)
    
有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：
  
- [获取内容](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [获得 MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [新 MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [一组 MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

