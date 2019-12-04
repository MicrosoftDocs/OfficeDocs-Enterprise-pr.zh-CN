---
title: IdFix 排除和支持的对象和属性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 列出 IdFix 工具排除并支持的属性。
ms.openlocfilehash: e57507688fe1efd21bb629b4fad297129eff55d6
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813922"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>IdFix 排除和支持的对象和属性

*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*

有两组由 IdFix 维护的规则;多租户和专用/ITAR。 此时，这两个规则集将从其搜索中排除相同的对象、属性和属性值。 这可能会在将来的版本中发生变化。
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>IdFix 使用的多租户和专用错误排除
此部分列出了 IdFix 从目录的搜索中排除的对象、属性和值。 星号（\*）是一个可替代其他字符的通配符。
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>在 IdFix 搜索过程中排除的对象、属性和值

|**排除**|**示例**|
|:-----|:-----|
|Admini\* |管理员 |
|CAS_ {\*  |CAS_ {fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail. *GUID* |
|Guest\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms-DS-链接 |
|iusr_\* |iusr_ *machinename* |
|iwam\*  |IWAM_ *machinename* |
|msol\* |MSOL_AD_SYNC |
|support_\* ||
|SystemMailbox\* |Systemmailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName 包含 "\0ACNF："|"\0ACNF： *GUID* " |
|对象包含 IsCriticalSystemObject 属性 |请参阅[属性 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)。 |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>由 IdFix 检查的多租户和专用对象和属性
通过[使用 IdFix 工具在准备目录属性以与 Office 365 同步](prepare-directory-attributes-for-synch-with-idfix.md)中的 "目录对象和属性准备" 一节中介绍了 IdFix 检查是否有错误的属性。
  

