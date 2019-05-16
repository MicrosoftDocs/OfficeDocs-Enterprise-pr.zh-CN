---
title: 使用 Office 365 PowerShell 查看许可证和服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
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
description: 说明如何使用 Office 365 PowerShell 查看有关 Office 365 组织中可用的许可计划、服务和许可证的信息。
ms.openlocfilehash: 9e84797de29337d9414d9a578a98f6799ee816cb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071088"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>使用 Office 365 PowerShell 查看许可证和服务

**摘要:** 说明如何使用 Office 365 PowerShell 查看有关 Office 365 组织中可用的许可计划、服务和许可证的信息。
  
每个 Office 365 订阅都包含以下元素:

- **许可计划**这些计划也称为许可证计划或 Office 365 计划。 许可计划定义可供用户使用的 Office 365 服务。 您的 Office 365 订阅可能包含多个许可计划。 Office 365 企业版 E3 是许可计划的一个示例。
    
- **服务**这些也称为服务计划。 服务是在每个许可计划中可用的 Office 365 产品、功能和功能, 例如 Exchange Online 和 Office Professional Plus。 可以从授予不同服务访问权限的不同许可计划向用户分配多个许可证。
    
- **许可证**每个许可计划包含您购买的许可证的数量。 您将许可证分配给用户, 以便他们可以使用由许可计划定义的 Office 365 服务。 每个用户帐户都需要一个许可计划中的至少一个许可证, 以便他们可以登录 Office 365 并使用服务。
    
您可以使用 Office 365 PowerShell 来查看有关 Office 365 组织中可用的许可计划、许可证和服务的详细信息。 有关在不同的 Office 365 订阅中提供的产品、功能和服务的详细信息, 请参阅[Office 365 计划选项](https://go.microsoft.com/fwlink/p/?LinkId=691147)。


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
若要查看有关当前许可计划和每个计划的可用许可证的摘要信息, 请运行以下命令:
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

结果包含以下信息：
  
- **SkuPartNumber:** 显示组织的可用许可计划。 例如, `ENTERPRISEPACK`是 Office 365 企业版 E3 的许可证计划名称。
    
- **Enabled:** 您为特定许可计划购买的许可证数量。
    
- **ConsumedUnits:** 您已从特定许可计划中分配给用户的许可证数量。
    
若要查看有关所有许可计划中可用的 Office 365 服务的详细信息, 请首先显示你的许可证计划的列表。

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

接下来, 将许可证计划信息存储在变量中。

````
$licenses = Get-AzureADSubscribedSku
````

接下来, 在特定的许可证计划中显示服务。

````
$licenses[<index>].ServicePlans
````

\<index> 是一个整数, 它指定从`Get-AzureADSubscribedSku | Select SkuPartNumber`命令的显示 (减 1) 开始的许可证计划的行号。

例如, 如果`Get-AzureADSubscribedSku | Select SkuPartNumber`命令的显示为:

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

然后, 显示 ENTERPRISEPREMIUM 许可证计划的服务的命令如下所示:

````
$licenses[2].ServicePlans
````

ENTERPRISEPREMIUM 是第三行。 因此, 索引值为 (3-1) 或2。

有关许可证计划 (也称为产品名称)、其包含的服务计划及其相应的友好名称的完整列表, 请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。

首先，[连接到 Office 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

>[!Note]
>PowerShell 脚本可自动执行本主题中描述的过程。 具体来说, 该脚本允许您查看和禁用 Office 365 组织中的服务, 包括 Sway。 有关详细信息，请参阅[Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)。
>
    
若要查看有关当前许可计划和每个计划的可用许可证的摘要信息, 请运行以下命令:
  
```
Get-MsolAccountSku
```

结果包含以下信息：
  
- **AccountSkuId:** 使用语法`<CompanyName>:<LicensingPlan>`显示您的组织可用的许可计划。  _<CompanyName>_ 是您在 Office 365 中注册时提供的值, 并且对于您的组织是唯一的。 对于_<LicensingPlan>_ 所有人而言, 值都是相同的。 例如, 在 "值`litwareinc:ENTERPRISEPACK`"、"公司名称`litwareinc`" 和 "许可计划名称`ENTERPRISEPACK`" 中, 是 Office 365 企业版 E3 的系统名称。
    
- **ActiveUnits:** 您为特定许可计划购买的许可证数量。
    
- **WarningUnits:** 尚未续订的许可计划中的许可证数量, 在30天的宽限期后将过期。
    
- **ConsumedUnits:** 您已从特定许可计划中分配给用户的许可证数量。
    
若要查看有关所有许可计划中可用的 Office 365 服务的详细信息, 请运行以下命令:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

下表显示了最常用服务的 Office 365 服务计划及其友好名称。 服务计划列表可能会有所不同。 
  
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
   
有关许可证计划 (也称为产品名称)、其包含的服务计划及其相应的友好名称的完整列表, 请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。

若要查看有关特定许可计划中可用的 Office 365 服务的详细信息, 请使用以下语法。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

本示例显示了 litwareinc: ENTERPRISEPACK (Office 365 企业版 E3) 许可计划中可用的 Office 365 服务。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a>刚开始接触 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>另请参阅


[使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
