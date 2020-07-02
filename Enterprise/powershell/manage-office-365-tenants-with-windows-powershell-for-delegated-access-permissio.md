---
title: 使用 Windows PowerShell 为委派访问权限（分配）合作伙伴管理 Microsoft 365 租户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 摘要：使用适用于 Microsoft 365 的 Windows PowerShell 管理客户租赁。
ms.openlocfilehash: a57f66ec02f5ba69006c17a9cf734e622017b8fb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998228"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>使用 Windows PowerShell 为委派访问权限（分配）合作伙伴管理 Microsoft 365 租户

Windows PowerShell 允许联合和云解决方案提供商（CSP）合作伙伴轻松管理和报告 Microsoft 365 管理中心中不可用的客户租赁设置。 请注意，合作伙伴管理员帐户要连接到其客户租赁，需要代表以下方管理 (AOBO) 权限。
  
委派访问权限 (DAP) 合作伙伴是联合和云解决方案提供商 (CSP) 合作伙伴。 他们通常是面向其他公司的网络或电信提供商。 他们将 Microsoft 365 订阅捆绑到其客户的服务产品中。 在销售 Microsoft 365 订阅时，会自动将代表（AOBO）权限的 "管理" 授予 "客户" 租赁，以便他们可以管理和报告客户租赁。
## <a name="what-do-you-need-to-know-before-you-begin"></a>在开始之前，您需要知道什么？

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
您也需要您的合作伙伴租户管理员凭据。
  
## <a name="what-do-you-want-to-do"></a>要执行什么操作？

### <a name="list-all-tenant-ids"></a>列出所有租户 ID

> [!NOTE]
> If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.
  
若要列出您有权访问的所有客户租户 ID，请运行此命令。
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

这将按 **TenantId** 列出所有客户租户。

>[!Note]
>PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。 若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>使用域名获取租户 ID

To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>列出租户的所有域

To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

如果您已注册其他域，这将返回与客户 **TenantId** 关联的所有域。
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>获取所有租户和已注册的域的映射

The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>获取租户的所有用户

This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>获取有关用户的所有详细信息

If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>添加用户、设置选项并分配许可证

Microsoft 365 用户的批量创建、配置和许可对于使用适用于 Office 365 的 Windows PowerShell 尤其有效。 在此两步过程中，您首先为要添加到逗号分隔值 (CSV) 文件中的所有用户创建条目，然后使用适用于 Office 365 的 Windows PowerShell 导入该文件。 
  
#### <a name="create-a-csv-file"></a>创建 CSV 文件

使用此格式创建 CSV 文件：
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
其中：
  
- **UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR. 
    
- **LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>导入 CSV 文件并创建用户

After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>另请参阅

#### 

[适用于合作伙伴的帮助](https://go.microsoft.com/fwlink/p/?LinkId=533477)

