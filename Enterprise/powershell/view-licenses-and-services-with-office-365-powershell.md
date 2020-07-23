---
title: 使用 PowerShell 查看 Microsoft 365 许可证和服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: 说明如何使用 PowerShell 查看有关 Microsoft 365 组织中可用的许可计划、服务和许可证的信息。
ms.openlocfilehash: f0b7d6cd5981bec09e7773d10d82ff81c0f34d4e
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230208"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>使用 PowerShell 查看 Microsoft 365 许可证和服务

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

每个 Microsoft 365 订阅都包含以下元素：

- **许可计划**这些计划也称为许可证计划或 Microsoft 365 计划。 许可计划定义可供用户使用的 Microsoft 365 服务。 你的 Microsoft 365 订阅可能包含多个许可计划。 许可证计划的一个示例是 Microsoft 365 E3。
    
- **服务**这些也称为服务计划。 服务是在每个许可计划中可用的 Microsoft 365 产品、功能和功能，例如，Exchange Online 和适用于企业的 Microsoft 365 应用程序（以前称为 Office 365 专业增强版）。 可以从授予不同服务访问权限的不同许可计划向用户分配多个许可证。
    
- **许可证**每个许可计划包含您购买的许可证的数量。 您将许可证分配给用户，以便他们可以使用由许可计划定义的 Microsoft 365 服务。 每个用户帐户都需要一个许可计划中的至少一个许可证，以便他们可以登录到 Microsoft 365 并使用服务。
    
可以使用适用于 Microsoft 365 的 PowerShell 查看有关 Microsoft 365 组织中可用的许可计划、许可证和服务的详细信息。 有关在不同的 Office 365 订阅中提供的产品、功能和服务的详细信息，请参阅[Office 365 计划选项](https://go.microsoft.com/fwlink/p/?LinkId=691147)。


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用用于图表模块的 Azure Active Directory PowerShell

首先，[连接到 Microsoft 365 租户](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
若要查看有关当前许可计划和每个计划的可用许可证的摘要信息，请运行以下命令：
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

结果中包含：
  
- **SkuPartNumber：** 显示组织的可用许可计划。 例如， `ENTERPRISEPACK` 是 Office 365 企业版 E3 的许可证计划名称。
    
- **Enabled：** 您为特定许可计划购买的许可证数量。
    
- **ConsumedUnits：** 您已从特定许可计划中分配给用户的许可证数量。
    
若要查看有关所有许可计划中可用的 Microsoft 365 服务的详细信息，请首先显示你的许可证计划的列表。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下来，将许可证计划信息存储在变量中。

```powershell
$licenses = Get-AzureADSubscribedSku
```

接下来，在特定的许可证计划中显示服务。

```powershell
$licenses[<index>].ServicePlans
```

\<index>是一个整数，它指定从命令的显示 `Get-AzureADSubscribedSku | Select SkuPartNumber` （减1）开始的许可证计划的行号。

例如，如果命令的显示 `Get-AzureADSubscribedSku | Select SkuPartNumber` 为：

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

然后，显示 ENTERPRISEPREMIUM 许可证计划的服务的命令如下所示：

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM 是第三行。 因此，索引值为（3-1）或2。

有关许可证计划（也称为产品名称）、其包含的服务计划及其相应的友好名称的完整列表，请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块

首先，[连接到 Microsoft 365 租户](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

>[!Note]
>PowerShell 脚本可自动执行本主题中描述的过程。 具体来说，该脚本允许您查看和禁用 Microsoft 365 组织中的服务，包括 Sway。 有关详细信息，请参阅[使用 PowerShell 禁用对 Sway 的访问](disable-access-to-sway-with-office-365-powershell.md)。
>
    
若要查看有关当前许可计划和每个计划的可用许可证的摘要信息，请运行以下命令：
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。 若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。
>

结果包含以下信息：
  
- **AccountSkuId：** 使用语法显示您的组织可用的许可计划 `<CompanyName>:<LicensingPlan>` 。  _\<CompanyName>_ 是您在 Microsoft 365 中注册时提供的值，并且对于您的组织是唯一的。 _\<LicensingPlan>_ 对于所有人而言，值都是相同的。 例如，在 "值"、 `litwareinc:ENTERPRISEPACK` "公司名称" `litwareinc` 和 "许可计划名称 `ENTERPRISEPACK` " 中，是 Office 365 企业版 E3 的系统名称。
    
- **ActiveUnits：** 您为特定许可计划购买的许可证数量。
    
- **WarningUnits：** 尚未续订的许可计划中的许可证数量，在30天的宽限期后将过期。
    
- **ConsumedUnits：** 您已从特定许可计划中分配给用户的许可证数量。
    
若要查看有关所有许可计划中可用的 Microsoft 365 服务的详细信息，请运行以下命令：
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

下表显示了最常用服务的 Microsoft 365 服务计划及其友好名称。 服务计划列表可能会有所不同。 
  
|**服务计划**|**描述**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure 权限管理 (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |适用于企业的 Microsoft 365 应用程序 *（以前称为 Office 365 专业增强版）*  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online 计划 2  <br/> |
   
有关许可证计划（也称为产品名称）、其包含的服务计划及其相应的友好名称的完整列表，请参阅[产品名称和服务计划标识符以获取许可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。

若要查看有关特定许可计划中可用的 Microsoft 365 服务的详细信息，请使用以下语法。
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

本示例显示了 litwareinc： ENTERPRISEPACK （Office 365 企业版 E3）许可计划中可用的服务。
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>另请参阅

[使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 PowerShell 管理 Microsoft 365](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 的 PowerShell 入门](getting-started-with-office-365-powershell.md)
