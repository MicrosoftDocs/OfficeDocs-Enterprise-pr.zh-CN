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
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 列出 IdFix 工具排除并支持的属性。
ms.openlocfilehash: da9a59d60b1ae2f1f68803e5a10afba16207fc69
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711572"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="4bd05-103">IdFix 排除和支持的对象和属性</span><span class="sxs-lookup"><span data-stu-id="4bd05-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="4bd05-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="4bd05-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="4bd05-105">有两组由 IdFix 维护的规则;多租户和专用/ITAR。</span><span class="sxs-lookup"><span data-stu-id="4bd05-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="4bd05-106">此时，这两个规则集将从其搜索中排除相同的对象、属性和属性值。</span><span class="sxs-lookup"><span data-stu-id="4bd05-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="4bd05-107">这可能会在将来的版本中发生变化。</span><span class="sxs-lookup"><span data-stu-id="4bd05-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="4bd05-108">IdFix 使用的多租户和专用错误排除</span><span class="sxs-lookup"><span data-stu-id="4bd05-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="4bd05-109">此部分列出了 IdFix 从目录的搜索中排除的对象、属性和值。</span><span class="sxs-lookup"><span data-stu-id="4bd05-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="4bd05-110">星号（ \* ）是一个可替代其他字符的通配符。</span><span class="sxs-lookup"><span data-stu-id="4bd05-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="4bd05-111">在 IdFix 搜索过程中排除的对象、属性和值</span><span class="sxs-lookup"><span data-stu-id="4bd05-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="4bd05-112">**排除**</span><span class="sxs-lookup"><span data-stu-id="4bd05-112">**Exclusion**</span></span>|<span data-ttu-id="4bd05-113">**示例**</span><span class="sxs-lookup"><span data-stu-id="4bd05-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4bd05-114">Admini\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-114">Admini\*</span></span> |<span data-ttu-id="4bd05-115">管理员</span><span class="sxs-lookup"><span data-stu-id="4bd05-115">Administrator</span></span> |
|<span data-ttu-id="4bd05-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-116">CAS_{\*</span></span>  |<span data-ttu-id="4bd05-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="4bd05-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="4bd05-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="4bd05-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="4bd05-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="4bd05-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-120">FederatedEmail\*</span></span> |<span data-ttu-id="4bd05-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="4bd05-121">FederatedEmail.</span></span> <span data-ttu-id="4bd05-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="4bd05-122">*GUID*</span></span> |
|<span data-ttu-id="4bd05-123">Guest\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-123">Guest\*</span></span> ||
|<span data-ttu-id="4bd05-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-124">HTTPConnector\*</span></span>  |<span data-ttu-id="4bd05-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="4bd05-125">HTTPConnector</span></span> |
|<span data-ttu-id="4bd05-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-126">krbtgt\*</span></span> |<span data-ttu-id="4bd05-127">ms-DS-链接</span><span class="sxs-lookup"><span data-stu-id="4bd05-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="4bd05-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-128">iusr_\*</span></span> |<span data-ttu-id="4bd05-129">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="4bd05-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="4bd05-130">iwam\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-130">iwam\*</span></span>  |<span data-ttu-id="4bd05-131">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="4bd05-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="4bd05-132">msol\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-132">msol\*</span></span> |<span data-ttu-id="4bd05-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="4bd05-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="4bd05-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-134">support_\*</span></span> ||
|<span data-ttu-id="4bd05-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-135">SystemMailbox\*</span></span> |<span data-ttu-id="4bd05-136">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="4bd05-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="4bd05-137">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="4bd05-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="4bd05-138">distinguishedName 包含 "\0ACNF："</span><span class="sxs-lookup"><span data-stu-id="4bd05-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="4bd05-139">"\0ACNF： *GUID* "</span><span class="sxs-lookup"><span data-stu-id="4bd05-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="4bd05-140">对象包含 IsCriticalSystemObject 属性</span><span class="sxs-lookup"><span data-stu-id="4bd05-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="4bd05-141">请参阅[属性 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)。</span><span class="sxs-lookup"><span data-stu-id="4bd05-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="4bd05-142">由 IdFix 检查的多租户和专用对象和属性</span><span class="sxs-lookup"><span data-stu-id="4bd05-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="4bd05-143">IdFix 的 "目录对象和属性准备" 一节365中的 "目录对象和属性准备" 一节中介绍了如何[使用 IdFix 工具](prepare-directory-attributes-for-synch-with-idfix.md)检查是否存在的错误的属性。</span><span class="sxs-lookup"><span data-stu-id="4bd05-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Microsoft 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

