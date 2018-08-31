---
title: IdFix 排除和支持的对象和属性
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 列出要排除和支持的 IdFix 工具的属性。
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539682"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>IdFix 排除和支持的对象和属性
IdFix 保持有两套规则；多租户和专用/ITAR。此时，这两个规则集都会从其搜索中排除相同的对象、属性和属性值。这在将来的版本中或许会有更改。
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>IdFix 使用的多租户和专用的错误排除项
本节列出了对象、 属性和 IdFix 排除的目录搜索的值。星号 (\*) 是可以替换为其他字符的通配符。
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>在 IdFix 搜索过程中会被排除的对象、属性和值

|**排除**|**示例**|
|:-----|:-----|
|Admini\* |管理员 |
|CAS_ {\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail。*GUID* |
|来宾\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms DS KrbTgt 链接 |
|iusr_\* |iusr_ *machinename* |
|iwam\*  |IWAM_ *machinename* |
|msol\* |MSOL_AD_SYNC |
|support_\* ||
|SystemMailbox\* |Systemmailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName 包含"\0ACNF:"|"\0ACNF: *GUID* " |
|对象包含 IsCriticalSystemObject 属性 |请参阅[isCriticalSystemObject 属性](https://go.microsoft.com/fwlink/p/?LinkId=401169)。 |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>IdFix 检查的多租户和专用对象和属性
Idfix 检查错误的属性节"目录对象和属性准备"[与使用 IdFix 工具的 Office 365 进行同步准备目录属性](prepare-directory-attributes-for-synch-with-idfix.md)中所述。
  

