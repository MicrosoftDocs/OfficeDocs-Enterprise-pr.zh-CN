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
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="a0ea6-103">IdFix 排除和支持的对象和属性</span><span class="sxs-lookup"><span data-stu-id="a0ea6-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="a0ea6-p101">IdFix 保持有两套规则；多租户和专用/ITAR。此时，这两个规则集都会从其搜索中排除相同的对象、属性和属性值。这在将来的版本中或许会有更改。</span><span class="sxs-lookup"><span data-stu-id="a0ea6-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="a0ea6-107">IdFix 使用的多租户和专用的错误排除项</span><span class="sxs-lookup"><span data-stu-id="a0ea6-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="a0ea6-p102">本节列出了对象、 属性和 IdFix 排除的目录搜索的值。星号 (\*) 是可以替换为其他字符的通配符。</span><span class="sxs-lookup"><span data-stu-id="a0ea6-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="a0ea6-110">在 IdFix 搜索过程中会被排除的对象、属性和值</span><span class="sxs-lookup"><span data-stu-id="a0ea6-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="a0ea6-111">**排除**</span><span class="sxs-lookup"><span data-stu-id="a0ea6-111">**Exclusion**</span></span>|<span data-ttu-id="a0ea6-112">**示例**</span><span class="sxs-lookup"><span data-stu-id="a0ea6-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a0ea6-113">Admini\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-113">Admini\*</span></span> |<span data-ttu-id="a0ea6-114">管理员</span><span class="sxs-lookup"><span data-stu-id="a0ea6-114">Administrator</span></span> |
|<span data-ttu-id="a0ea6-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-115">CAS_{\*</span></span>  |<span data-ttu-id="a0ea6-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="a0ea6-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="a0ea6-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="a0ea6-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="a0ea6-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="a0ea6-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-119">FederatedEmail\*</span></span> |<span data-ttu-id="a0ea6-p103">FederatedEmail。*GUID*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="a0ea6-122">来宾\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-122">Guest\*</span></span> ||
|<span data-ttu-id="a0ea6-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-123">HTTPConnector\*</span></span>  |<span data-ttu-id="a0ea6-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="a0ea6-124">HTTPConnector</span></span> |
|<span data-ttu-id="a0ea6-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-125">krbtgt\*</span></span> |<span data-ttu-id="a0ea6-126">ms DS KrbTgt 链接</span><span class="sxs-lookup"><span data-stu-id="a0ea6-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="a0ea6-127">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-127">iusr_\*</span></span> |<span data-ttu-id="a0ea6-128">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="a0ea6-129">iwam\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-129">iwam\*</span></span>  |<span data-ttu-id="a0ea6-130">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="a0ea6-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-131">msol\*</span></span> |<span data-ttu-id="a0ea6-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="a0ea6-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="a0ea6-133">support_\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-133">support_\*</span></span> ||
|<span data-ttu-id="a0ea6-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-134">SystemMailbox\*</span></span> |<span data-ttu-id="a0ea6-135">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="a0ea6-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="a0ea6-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="a0ea6-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="a0ea6-137">distinguishedName 包含"\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="a0ea6-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="a0ea6-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="a0ea6-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="a0ea6-139">对象包含 IsCriticalSystemObject 属性</span><span class="sxs-lookup"><span data-stu-id="a0ea6-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="a0ea6-140">请参阅[isCriticalSystemObject 属性](https://go.microsoft.com/fwlink/p/?LinkId=401169)。</span><span class="sxs-lookup"><span data-stu-id="a0ea6-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="a0ea6-141">IdFix 检查的多租户和专用对象和属性</span><span class="sxs-lookup"><span data-stu-id="a0ea6-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="a0ea6-142">Idfix 检查错误的属性节"目录对象和属性准备"[与使用 IdFix 工具的 Office 365 进行同步准备目录属性](prepare-directory-attributes-for-synch-with-idfix.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="a0ea6-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

