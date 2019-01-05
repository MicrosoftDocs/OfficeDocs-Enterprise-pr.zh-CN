---
title: 使用 Office 365 PowerShell 查看许可证和服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: 介绍如何使用 Office 365 PowerShell 中查看许可计划、 服务和 Office 365 组织中可用的许可证的信息。
ms.openlocfilehash: f673ac984e504a740dfac474821366d34de5ccbc
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730327"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>使用 Office 365 PowerShell 查看许可证和服务

**摘要：** 介绍如何使用 Office 365 PowerShell 中查看许可计划、 服务和 Office 365 组织中可用的许可证的信息。
  
每个 Office 365 订阅包括以下元素：

- **许可计划**这些是也称为许可计划或 Office 365 plans。许可计划定义适用于用户的 Office 365 服务。Office 365 订阅可能包含多个许可计划。示例许可计划将为 Office 365 企业版 E3。
    
- **服务**这些是也称为服务计划。服务是 Office 365 产品、 功能和功能所提供的每个许可计划，例如 Exchange Online 和 Office Professional Plus。用户可以具有多个许可证分配给它们从不同的许可计划授予的访问权限不同的服务。
    
- **许可证**每个许可计划包含您购买的许可证数量。以便他们可以使用 Office 365 服务所定义的许可计划，可以向用户分配许可证。每个用户帐户需要至少一个许可证从一个许可计划，以便他们可以登录到 Office 365，并使用服务。
    
Office 365 PowerShell 中可用于在 Office 365 组织中查看有关可用许可计划、 许可证和服务的详细信息。有关产品、 功能和在不同的 Office 365 订阅中可用的服务的详细信息，请参阅[Office 365 计划选项](https://go.microsoft.com/fwlink/p/?LinkId=691147)。


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用 Azure Active Directory PowerShell 图模块

第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
若要查看有关您当前的许可计划和每个计划可用的许可证的摘要信息，请运行以下命令：
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

结果包含以下信息：
  
- **SkuPartNumber:** 显示为您的组织可用的许可计划。例如，`ENTERPRISEPACK`是 Office 365 企业版 E3 的系统名称。
    
- **启用：** 您已为特定的许可计划购买的许可证数量。
    
- **ConsumedUnits:** 从特定的许可计划已分配给用户的许可证数量。
    
若要查看有关所有许可计划中可用的 Office 365 服务的详细信息，请首先显示许可计划的列表。

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

接下来，在一个变量中存储的许可计划信息。

````
$licenses = Get-AzureADSubscribedSku
````

接下来，在特定的许可计划中显示服务。

````
$licenses[<index>].ServicePlan
````

\<索引 > 是一个整数，指定的行数的许可计划从显示的`Get-AzureADSubscribedSku | Select SkuPartNumber`命令，减 1 之间。

例如，如果显示的`Get-AzureADSubscribedSku | Select SkuPartNumber`命令这是：

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

然后命令来显示 ENTERPRISEPREMIUM 许可计划的服务是：

````
$licenses[2].ServicePlan
````

ENTERPRISEPREMIUM 是第三行。因此，索引值是 (3-1），或 2。

有关许可计划 （也称为产品名称） 的完整列表，其包含的服务计划和其相应的友好名称，请参阅[产品名称和授权的服务计划标识符](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用 Windows PowerShell 的 Microsoft Azure Active Directory 模块

第一个、[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

>[!Note]
>PowerShell 脚本是可用的自动执行本主题中所述的过程。具体而言，该脚本允许您查看和 Office 365 组织，包括 Sway 中禁用这些服务。有关详细信息，请参阅[禁用对 Sway 与 Office 365 PowerShell 中的访问](disable-access-to-sway-with-office-365-powershell.md)。
>
    
若要查看有关您当前的许可计划和每个计划可用的许可证的摘要信息，请运行以下命令：
  
```
Get-MsolAccountSku
```

结果包含以下信息：
  
- **AccountSkuId:** 显示为您的组织可用的许可计划使用语法`<CompanyName>:<LicensingPlan>`。 _<CompanyName>_ 是注册 Office 365 中，为您的组织都是唯一时提供的值。_<LicensingPlan>_ 值是相同的每个人。例如，在值`litwareinc:ENTERPRISEPACK`，公司名为`litwareinc`，许可计划名称和`ENTERPRISEPACK`，这是 Office 365 企业版 E3 的系统名称。
    
- **ActiveUnits:** 您已为特定的许可计划购买的许可证数量。
    
- **WarningUnits:** 您还未更新的且将过期后 30 天的宽限期的许可计划中的许可证数量。
    
- **ConsumedUnits:** 从特定的许可计划已分配给用户的许可证数量。
    
若要查看有关所有许可计划中可用的 Office 365 服务的详细信息，请运行以下命令：
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

下表显示了 Office 365 服务计划和其最常见的服务的友好名称。您的服务计划列表可能会有所不同。 
  
|**服务计划**|**说明**|
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
   
有关许可计划 （也称为产品名称） 的完整列表，其包含的服务计划和其相应的友好名称，请参阅[产品名称和授权的服务计划标识符](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。

若要查看有关特定的许可计划中可用的 Office 365 服务的详细信息，请使用以下语法。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

本示例显示 litwareinc: enterprisepack (Office 365 企业版 E3) 许可计划中可用的 Office 365 服务。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a>刚开始接触 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>另请参阅


[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
