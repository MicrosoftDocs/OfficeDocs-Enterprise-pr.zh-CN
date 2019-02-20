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
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="77df1-103">IdFix 排除和支持的对象和属性</span><span class="sxs-lookup"><span data-stu-id="77df1-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="77df1-p101">IdFix 保持有两套规则；多租户和专用/ITAR。此时，这两个规则集都会从其搜索中排除相同的对象、属性和属性值。这在将来的版本中或许会有更改。</span><span class="sxs-lookup"><span data-stu-id="77df1-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="77df1-107">IdFix 使用的多租户和专用的错误排除项</span><span class="sxs-lookup"><span data-stu-id="77df1-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="77df1-p102">此部分列出了 IdFix 从目录的搜索中排除的对象、属性和值。星号 (\*) 是一个可替代其他字符的通配符。</span><span class="sxs-lookup"><span data-stu-id="77df1-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="77df1-110">在 IdFix 搜索过程中会被排除的对象、属性和值</span><span class="sxs-lookup"><span data-stu-id="77df1-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="77df1-111">**排除**</span><span class="sxs-lookup"><span data-stu-id="77df1-111">**Exclusion**</span></span>|<span data-ttu-id="77df1-112">**示例**</span><span class="sxs-lookup"><span data-stu-id="77df1-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="77df1-113">Admini\*</span><span class="sxs-lookup"><span data-stu-id="77df1-113">Admini\*</span></span> |<span data-ttu-id="77df1-114">管理员</span><span class="sxs-lookup"><span data-stu-id="77df1-114">Administrator</span></span> |
|<span data-ttu-id="77df1-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="77df1-115">CAS_{\*</span></span>  |<span data-ttu-id="77df1-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="77df1-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="77df1-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="77df1-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="77df1-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="77df1-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="77df1-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="77df1-119">FederatedEmail\*</span></span> |<span data-ttu-id="77df1-p103">FederatedEmail。*GUID*</span><span class="sxs-lookup"><span data-stu-id="77df1-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="77df1-122">操作系统\*</span><span class="sxs-lookup"><span data-stu-id="77df1-122">Guest\*</span></span> ||
|<span data-ttu-id="77df1-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="77df1-123">HTTPConnector\*</span></span>  |<span data-ttu-id="77df1-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="77df1-124">HTTPConnector</span></span> |
|<span data-ttu-id="77df1-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="77df1-125">krbtgt\*</span></span> |<span data-ttu-id="77df1-126">ms-DS-链接</span><span class="sxs-lookup"><span data-stu-id="77df1-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="77df1-127">iusr\*</span><span class="sxs-lookup"><span data-stu-id="77df1-127">iusr_\*</span></span> |<span data-ttu-id="77df1-128">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="77df1-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="77df1-129">iwam\*</span><span class="sxs-lookup"><span data-stu-id="77df1-129">iwam\*</span></span>  |<span data-ttu-id="77df1-130">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="77df1-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="77df1-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="77df1-131">msol\*</span></span> |<span data-ttu-id="77df1-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="77df1-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="77df1-133">支持\*</span><span class="sxs-lookup"><span data-stu-id="77df1-133">support_\*</span></span> ||
|<span data-ttu-id="77df1-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="77df1-134">SystemMailbox\*</span></span> |<span data-ttu-id="77df1-135">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="77df1-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="77df1-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="77df1-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="77df1-137">distinguishedName 包含 "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="77df1-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="77df1-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="77df1-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="77df1-139">对象包含 IsCriticalSystemObject 属性</span><span class="sxs-lookup"><span data-stu-id="77df1-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="77df1-140">请参阅[属性 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)。</span><span class="sxs-lookup"><span data-stu-id="77df1-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="77df1-141">IdFix 检查的多租户和专用对象和属性</span><span class="sxs-lookup"><span data-stu-id="77df1-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="77df1-142">通过[使用 IdFix 工具在准备目录属性以与 Office 365 同步](prepare-directory-attributes-for-synch-with-idfix.md)中的 "目录对象和属性准备" 一节中介绍了 IdFix 检查是否有错误的属性。</span><span class="sxs-lookup"><span data-stu-id="77df1-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

