---
title: "使用 Office 365 PowerShell 查看许可证和服务"
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
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: "解释如何使用 Office 365 PowerShell 查看有关授权计划、 服务和 Office 365 提供组织中可用的许可证信息。"
ms.openlocfilehash: f43a1c20be157d26ec9cd1d98df2f5e17517b1d6
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>使用 Office 365 PowerShell 查看许可证和服务

**摘要：**解释如何使用 Office 365 PowerShell 查看有关授权计划、 服务和 Office 365 提供组织中可用的许可证信息。
  
每个 Office 365 预订由下列元素组成：
- **授权计划**这些也是已知的 aslicense 计划或 Office 365 计划。授权计划定义可供用户使用的 Office 365 提供服务。Office 365 订阅可能含有多个许可计划。示例授权计划将 Office 365 企业 E3。
    
- **服务**这些也是已知的 asservice 计划。服务是 Office 365 的产品、 功能和功能所提供的每个授权的计划，例如，Exchange 联机和 Office Professional Plus。用户可以具有分配给它们从不同的授权计划授予的访问权限不同服务的多个许可证。
    
- **许可证**每个授权计划包含您购买的许可证的数量。将许可证分配给用户以便他们可以使用 Office 365 提供服务所定义的授权计划。每个用户帐户要求从一个授权计划至少一个许可证，因此他们可以登录到 Office 365 提供和使用服务。
    
Office 365 PowerShell 可用于查看 Office 365 提供组织中可用的授权计划、 许可证和服务有关的详细信息。有关产品、 功能和 Office 365 的不同预订中提供的服务的详细信息，请参阅[Office 365 计划选项](https://go.microsoft.com/fwlink/p/?LinkId=691147)。
## <a name="before-you-begin"></a>开始之前
<a name="RTT"> </a>

- 若要执行此主题中的过程，必须连接到 Office 365 PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- PowerShell 提供了一个脚本来自动执行本主题中描述的过程。具体来说，脚本允许您查看和您 Office 365 的组织，包括 Sway 中禁用这些服务。有关详细信息，请参阅[禁用 Office 365 PowerShell 的 Sway 访问](disable-access-to-sway-with-office-365-powershell.md)。
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a>查看有关许可计划和可用的许可证的信息
<a name="ShortVersion"> </a>

若要查看有关您当前的授权计划和每个计划的可用许可证摘要信息，请在 Office 365 PowerShell 运行下面的命令：
  
```
Get-MsolAccountSku
```

结果包含以下信息：
  
- **AccountSkuId:**显示可用的授权计划为您的组织使用的语法`<CompanyName>:<LicensingPlan>`。 _<CompanyName>_为您提供当您注册 Office 365 并为您的组织中是唯一的。_<LicensingPlan>_值是相同的所有人。例如中值, `litwareinc:ENTERPRISEPACK`，公司名称是`litwareinc`，和授权计划名称`ENTERPRISEPACK`，即 Office 365 企业 E3 的系统名称。
    
- **ActiveUnits:**您已为特定的授权计划购买的许可证的数量。
    
- **WarningUnits:**您没有更新的且将过期 30 天宽限期过后的授权计划中的许可证数。
    
- **ConsumedUnits:**从某一特定的授权计划已经指派给用户的许可证的数量。
    
若要查看有关 Office 365 提供可用服务在所有许可证计划的详细信息，请运行以下命令：
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

下表显示 Office 365 提供服务的计划和他们最常见的服务的友好名称。您的服务计划列表可能会有所不同。服务计划和其友好名称的完整列表，请联系[办公室的支持](https://support.office.com/home/contact)。
  
|服务计划 ***|说明 ***|
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
   
若要查看有关 Office 365 提供服务所提供的某一特定的授权计划的详细信息，请使用下面的语法。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq " <AccountSkuId>"}).ServiceStatus
```

此示例演示 Office 365 提供服务所提供的 litwareinc:ENTERPRISEPACK (Office 365 企业 E3) 授权计划。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a>刚开始接触 Office 365？
<a name="ShortVersion"> </a>

||
|:-----|
|![LinkedIn 学习的短图标](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 提供指向新建？**        [Office 365 管理员和 IT 专业人员使用](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5)，LinkedIn 学习者发现免费视频课程。 |
   
## <a name="see-also"></a>另请参阅
<a name="ShortVersion"> </a>

#### 

[使用 Office 365 PowerShell 查看授权和未授权的用户](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 查看帐户许可证和服务详细信息](view-account-license-and-service-details-with-office-365-powershell.md)
#### 

[获得 MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)

