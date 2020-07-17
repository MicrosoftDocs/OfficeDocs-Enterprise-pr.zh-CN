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

本主题中的步骤需要您连接到适用于Office 365的Windows PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
  
您也需要您的合作伙伴租户管理员凭据。
  
## <a name="what-do-you-want-to-do"></a>要执行什么操作？

### <a name="list-all-tenant-ids"></a>列出所有租户 ID

> [!NOTE]
> 如果您有 500 多个租户，使用  _-All_ 或 _-MaxResultsParameter_ 确定 cmdlet 语法的范围。这适用于可以提供大型输出的其他 cmdlet，如 **Get-MsolUser** 。
  
若要列出您有权访问的所有客户租户 ID，请运行此命令。
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

这将按 **TenantId** 列出所有客户租户。

>[!Note]
>PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。 若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>使用域名获取租户 ID

要按域名获取特定客户租户的 **TenantId** ，请运行此命令。将 _<domainname.onmicrosoft.com>_ 替换为您需要的客户租户的实际域名。
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>列出租户的所有域

若要获取任一客户租户的所有域，请运行以下命令。将 _<customer TenantId value>_ 替换为实际值。
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

如果您已注册其他域，这将返回与客户 **TenantId** 关联的所有域。
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>获取所有租户和已注册的域的映射

适用于 Office 365 的 Windows PowerShell 之前命令向您演示了如何在它们之间没有明确映射时检索租户 ID 或域，但并非同时检索两者。此命令会生成您的所有客户租户 ID 及其域的列表。
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>获取租户的所有用户

这会显示特定租户的所有用户的 **UserPrincipalName**、**DisplayName** 和 **isLicensed** 状态。将 _<customer TenantId value>_ 替换为实际值。
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>获取有关用户的所有详细信息

若要查看特定用户的所有属性，请运行此命令。将 _<customer TenantId value>_ 和 _<user principal name value>_ 替换为实际值。
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>添加用户、设置选项并分配许可证

Microsoft 365 用户的批量创建、配置和许可对于使用适用于 Office 365 的 Windows PowerShell 尤其有效。 在此两步过程中，您首先为要添加到逗号分隔值 (CSV) 文件中的所有用户创建条目，然后使用适用于 Office 365 的 Windows PowerShell 导入该文件。 
  
#### <a name="create-a-csv-file"></a>创建 CSV 文件

使用此格式创建 CSV 文件：
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
其中：
  
- **UsageLocation** ：此值是用户的两个字母的 ISO 国家/地区代码。国家/地区代码可以在[ISO 联机浏览平台](https://go.microsoft.com/fwlink/p/?LinkId=532703)中查找。例如，美国的代码为 US，巴西的代码为 BR。 
    
- **LicenseAssignment** ：此值使用以下格式： `syndication-account:<PROVISIONING_ID>`。例如，如果您要向客户租户用户分配 O365_Business_Premium 许可证， **LicenseAssignment** 值将如下所示： **syndication-account:O365_Business_Premium** 。您将在您有权作为联合或 CSP 合作伙伴访问的联合合作伙伴门户中找到 PROVISIONING_ID。
    
#### <a name="import-the-csv-file-and-create-the-users"></a>导入 CSV 文件并创建用户

创建您的 CSV 文件后，运行此命令，使用不会过期的密码创建用户帐户。此密码分配您指定的许可证，用户必须在第一次登录时进行更改。请确保替换为正确的 CSV 文件名。
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>另请参阅

#### 

[适用于合作伙伴的帮助](https://go.microsoft.com/fwlink/p/?LinkId=533477)

