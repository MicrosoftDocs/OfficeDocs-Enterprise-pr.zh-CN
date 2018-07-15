---
title: 使用 Office 365 PowerShell 查看许可证和服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/20/2018
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
ms.openlocfilehash: 4ee4a5d0173f97520075f146e50bd234e767cc95
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319253"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>使用 Office 365 PowerShell 查看许可证和服务

**摘要：** 介绍如何使用 Office 365 PowerShell 中查看许可计划、 服务和 Office 365 组织中可用的许可证的信息。
  
每个 Office 365 订阅包括以下元素：

- **许可计划**这些也称为 aslicense 计划或 Office 365 plans。许可计划定义适用于用户的 Office 365 服务。Office 365 订阅可能包含多个许可计划。示例许可计划将为 Office 365 企业版 E3。
    
- **服务**这些是已知的 asservice 计划。服务是 Office 365 产品、 功能和功能所提供的每个许可计划，例如 Exchange Online 和 Office Professional Plus。用户可以具有多个许可证分配给它们从不同的许可计划授予的访问权限不同的服务。
    
- **许可证**每个许可计划包含您购买的许可证数量。以便他们可以使用 Office 365 服务所定义的许可计划，可以向用户分配许可证。每个用户帐户需要至少一个许可证从一个许可计划，以便他们可以登录到 Office 365，并使用服务。
    
Office 365 PowerShell 中可用于在 Office 365 组织中查看有关可用许可计划、 许可证和服务的详细信息。有关产品、 功能和在不同的 Office 365 订阅中可用的服务的详细信息，请参阅[Office 365 计划选项](https://go.microsoft.com/fwlink/p/?LinkId=691147)。

## <a name="before-you-begin"></a>准备工作

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- PowerShell 脚本是可用的自动执行本主题中所述的过程。具体而言，该脚本，可以查看和 Office 365 组织，包括 Sway 中禁用这些服务。有关详细信息，请参阅[禁用对 Sway 与 Office 365 PowerShell 中的访问](disable-access-to-sway-with-office-365-powershell.md)。
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a>查看有关许可计划和可用的许可证的信息

若要查看有关您当前的许可计划和每个计划可用的许可证的摘要信息，请在 Office 365 PowerShell 中运行以下命令：
  
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

下表显示了 Office 365 服务计划和其最常见的服务的友好名称。您的服务计划列表可能会有所不同。服务计划和其友好名称的完整列表，请与[业务用户的支持选项](https://support.microsoft.com/gp/support-options-for-business)。
  
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

- [使用 Office 365 PowerShell 查看授权和未授权的用户](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [使用 Office 365 PowerShell 查看帐户许可证和服务详细信息](view-account-license-and-service-details-with-office-365-powershell.md)
- [Get-msolaccountsku](https://go.microsoft.com/fwlink/p/?LinkId=691549)

