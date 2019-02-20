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
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 列出 IdFix 工具排除并支持的属性。
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085081"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>IdFix 排除和支持的对象和属性
IdFix 保持有两套规则；多租户和专用/ITAR。此时，这两个规则集都会从其搜索中排除相同的对象、属性和属性值。这在将来的版本中或许会有更改。
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>IdFix 使用的多租户和专用的错误排除项
此部分列出了 IdFix 从目录的搜索中排除的对象、属性和值。星号 (\*) 是一个可替代其他字符的通配符。
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>在 IdFix 搜索过程中会被排除的对象、属性和值

|**排除**|**示例**|
|:-----|:-----|
|Admini\* |管理员 |
|CAS_ {\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail。*GUID* |
|操作系统\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms-DS-链接 |
|iusr\* |iusr_ *machinename* |
|iwam\*  |IWAM_ *machinename* |
|msol\* |MSOL_AD_SYNC |
|支持\* ||
|SystemMailbox\* |Systemmailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|distinguishedName 包含 "\0ACNF:"|"\0ACNF: *GUID* " |
|对象包含 IsCriticalSystemObject 属性 |请参阅[属性 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)。 |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>IdFix 检查的多租户和专用对象和属性
通过[使用 IdFix 工具在准备目录属性以与 Office 365 同步](prepare-directory-attributes-for-synch-with-idfix.md)中的 "目录对象和属性准备" 一节中介绍了 IdFix 检查是否有错误的属性。
  

