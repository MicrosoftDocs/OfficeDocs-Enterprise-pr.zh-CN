---
title: 使用 Office 365 PowerShell 禁止访问服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/08/2018
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
description: 介绍如何使用 Office 365 PowerShell 中禁用对 Office 365 服务的组织中用户的访问。
ms.openlocfilehash: 44b0ed84bb8fd098412c69258834194b2b1eeb2f
ms.sourcegitcommit: f42ca73d23beb5770981e7a93995ef3be5e341bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "22196819"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>使用 Office 365 PowerShell 禁止访问服务

**摘要：** 介绍如何使用 Office 365 PowerShell 中禁用对 Office 365 服务的组织中用户的访问。
  
在 Office 365 帐户分配许可证从许可计划时，Office 365 服务可供用户从该许可证。但是，您可以控制用户可以访问 Office 365 服务。例如，即使许可证允许访问 SharePoint Online，您可以禁用对其进行访问。实际上，您可以使用 Office 365 PowerShell 中禁用对任意数量的服务的访问：

- 单个帐户。
    
- 一组帐户。
    
- 组织中的所有帐户。
    
## <a name="before-you-begin"></a>准备工作
<a name="RTT"> </a>

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 使用**Get-msolaccountsku** cmdlet 可以查看您可用的许可计划，以及这些计划中可用的 Office 365 服务。有关详细信息，请参阅[查看许可证和身份验证服务与 Office 365 PowerShell 中](view-licenses-and-services-with-office-365-powershell.md)。
    
- 若要查看之前和之后的此主题中的过程的结果，请参阅[查看帐户许可证和服务的详细信息与 Office 365 PowerShell 中](view-account-license-and-service-details-with-office-365-powershell.md)。
    
- PowerShell 脚本是可用的自动执行本主题中所述的过程。具体而言，该脚本，可以查看和 Office 365 组织，包括 Sway 中禁用这些服务。有关详细信息，请参阅[禁用对 Sway 与 Office 365 PowerShell 中的访问](disable-access-to-sway-with-office-365-powershell.md)。
    
- 如果不使用的_所有_参数的情况下使用**Get-msoluser** cmdlet，则返回仅的第一个 500 的用户帐户。
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a>特定的 Office 365 服务的特定用户的单个许可计划
  
若要禁用一组特定的 Office 365 服务的用户从单个许可计划，请执行以下步骤：
  
1. 许可计划中的不需要的服务标识使用以下语法：
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    下面的示例创建一个名为许可计划中禁用的 Office Online 和 SharePoint Online 服务的**LicenseOptions**对象`litwareinc:ENTERPRISEPACK`(Office 365 企业版 E3)。
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. 将步骤 1 中的 **LicenseOptions** 对象用于一个或多个用户。
    
  - 若要创建一个已禁用服务的新帐户，请使用以下语法：
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    下面的示例创建新帐户的 Allie Bellew 分配许可证和禁用在步骤 1 中所描述的服务。
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    有关 Office 365 PowerShell 中创建用户帐户的详细信息，请参阅[使用 Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)。
    
  - 若要禁用现有授权用户的服务，请使用下面的语法：
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    本示例对用户 BelindaN@litwareinc.com 禁用服务。
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - 若要禁用所有现有的授权用户在步骤 1 中所描述的服务，请指定从的**Get-msolaccountsku** cmdlet （如**litwareinc: enterprisepack**)，显示在 Office 365 计划的名称，然后运行以下命令：
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - 若要对一组现有用户禁用服务，请使用下列两种方法之一来确定用户：
    
  - **筛选器基于现有帐户属性的帐户**若要执行此操作，使用以下语法：
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    以下示例禁止在美国销售部门中的用户的服务。
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **使用特定帐户的列表**若要执行此操作，执行以下步骤：
    
1. 创建一个文本文件，在它的每一行上包含一个帐户，如下所示：
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    此示例中，在文本文件是 c:\\My Documents\\Accounts.txt。
    
2. 运行以下命令：
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

若要禁用 Office 365 服务的用户，而您要将其分配给许可计划，请参阅[禁用访问时分配用户许可证的服务](disable-access-to-services-while-assigning-user-licenses.md)。
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a>特定的 Office 365 服务的用户从所有许可计划
  
若要禁用的用户的 Office 365 服务中所有可用的许可计划，请执行以下步骤：
  
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
    
  -  _<UndesirableService>_ 本示例中，我们将使用 Office Online 和 SharePoint Online。
    
  -  _<Account>_ 本示例中，我们将使用 belindan@litwareinc.com。
    
    自定义的脚本如下所示：
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. 另存为脚本`RemoveO365Services.ps1`是您方便地查找的位置。此示例中，我们将保存的文件中`C:\\O365 Scripts`。
    
4. 使用以下命令，在 Office 365 PowerShell 中运行脚本。
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> 反向执行这些过程的任何效果 (即，以重新启用已禁用的服务)，再次运行的过程，但使用值`$null` _DisabledPlans_参数。
  
[Return to top](disable-access-to-services-with-office-365-powershell.md#RTT)



## <a name="new-to-office-365"></a>刚开始接触 Office 365？
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>另请参阅
<a name="SeeAlso"> </a>

请参阅下面有关使用 Office 365 PowerShell 管理用户的其他主题：
  
- [使用 Office 365 PowerShell 删除和还原用户账户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 删除和还原用户账户](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 冻结用户账户](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 向用户帐户分配许可证](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 创建用户帐户](create-user-accounts-with-office-365-powershell.md)
    
有关在这些步骤中使用的 cmdlet 的详细信息，请参阅下列主题：
  
- [获取内容](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-msolaccountsku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [新 MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Set-msoluserlicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

