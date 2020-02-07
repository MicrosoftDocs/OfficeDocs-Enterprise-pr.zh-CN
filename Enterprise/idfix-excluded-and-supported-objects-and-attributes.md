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
ms.openlocfilehash: 0203f47864dc4222cd2f95a4e67b2f10bec44f71
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840139"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="342a8-103">IdFix 排除和支持的对象和属性</span><span class="sxs-lookup"><span data-stu-id="342a8-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="342a8-104">*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="342a8-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="342a8-105">有两组由 IdFix 维护的规则;多租户和专用/ITAR。</span><span class="sxs-lookup"><span data-stu-id="342a8-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="342a8-106">此时，这两个规则集将从其搜索中排除相同的对象、属性和属性值。</span><span class="sxs-lookup"><span data-stu-id="342a8-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="342a8-107">这可能会在将来的版本中发生变化。</span><span class="sxs-lookup"><span data-stu-id="342a8-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="342a8-108">IdFix 使用的多租户和专用错误排除</span><span class="sxs-lookup"><span data-stu-id="342a8-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="342a8-109">此部分列出了 IdFix 从目录的搜索中排除的对象、属性和值。</span><span class="sxs-lookup"><span data-stu-id="342a8-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="342a8-110">星号（\*）是一个可替代其他字符的通配符。</span><span class="sxs-lookup"><span data-stu-id="342a8-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="342a8-111">在 IdFix 搜索过程中排除的对象、属性和值</span><span class="sxs-lookup"><span data-stu-id="342a8-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="342a8-112">**排除**</span><span class="sxs-lookup"><span data-stu-id="342a8-112">**Exclusion**</span></span>|<span data-ttu-id="342a8-113">**示例**</span><span class="sxs-lookup"><span data-stu-id="342a8-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="342a8-114">Admini\*</span><span class="sxs-lookup"><span data-stu-id="342a8-114">Admini\*</span></span> |<span data-ttu-id="342a8-115">管理员</span><span class="sxs-lookup"><span data-stu-id="342a8-115">Administrator</span></span> |
|<span data-ttu-id="342a8-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="342a8-116">CAS_{\*</span></span>  |<span data-ttu-id="342a8-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="342a8-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="342a8-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="342a8-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="342a8-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="342a8-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="342a8-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="342a8-120">FederatedEmail\*</span></span> |<span data-ttu-id="342a8-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="342a8-121">FederatedEmail.</span></span> <span data-ttu-id="342a8-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="342a8-122">*GUID*</span></span> |
|<span data-ttu-id="342a8-123">Guest\*</span><span class="sxs-lookup"><span data-stu-id="342a8-123">Guest\*</span></span> ||
|<span data-ttu-id="342a8-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="342a8-124">HTTPConnector\*</span></span>  |<span data-ttu-id="342a8-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="342a8-125">HTTPConnector</span></span> |
|<span data-ttu-id="342a8-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="342a8-126">krbtgt\*</span></span> |<span data-ttu-id="342a8-127">ms-DS-链接</span><span class="sxs-lookup"><span data-stu-id="342a8-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="342a8-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="342a8-128">iusr_\*</span></span> |<span data-ttu-id="342a8-129">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="342a8-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="342a8-130">iwam\*</span><span class="sxs-lookup"><span data-stu-id="342a8-130">iwam\*</span></span>  |<span data-ttu-id="342a8-131">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="342a8-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="342a8-132">msol\*</span><span class="sxs-lookup"><span data-stu-id="342a8-132">msol\*</span></span> |<span data-ttu-id="342a8-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="342a8-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="342a8-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="342a8-134">support_\*</span></span> ||
|<span data-ttu-id="342a8-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="342a8-135">SystemMailbox\*</span></span> |<span data-ttu-id="342a8-136">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="342a8-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="342a8-137">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="342a8-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="342a8-138">distinguishedName 包含 "\0ACNF："</span><span class="sxs-lookup"><span data-stu-id="342a8-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="342a8-139">"\0ACNF： *GUID* "</span><span class="sxs-lookup"><span data-stu-id="342a8-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="342a8-140">对象包含 IsCriticalSystemObject 属性</span><span class="sxs-lookup"><span data-stu-id="342a8-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="342a8-141">请参阅[属性 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)。</span><span class="sxs-lookup"><span data-stu-id="342a8-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="342a8-142">由 IdFix 检查的多租户和专用对象和属性</span><span class="sxs-lookup"><span data-stu-id="342a8-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="342a8-143">通过[使用 IdFix 工具在准备目录属性以与 Office 365 同步](prepare-directory-attributes-for-synch-with-idfix.md)中的 "目录对象和属性准备" 一节中介绍了 IdFix 检查是否有错误的属性。</span><span class="sxs-lookup"><span data-stu-id="342a8-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

