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
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="e9bd7-103">IdFix 排除和支持的对象和属性</span><span class="sxs-lookup"><span data-stu-id="e9bd7-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="e9bd7-104">*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="e9bd7-105">有两组由 IdFix 维护的规则;多租户和专用/ITAR。</span><span class="sxs-lookup"><span data-stu-id="e9bd7-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="e9bd7-106">此时，这两个规则集将从其搜索中排除相同的对象、属性和属性值。</span><span class="sxs-lookup"><span data-stu-id="e9bd7-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="e9bd7-107">这可能会在将来的版本中发生变化。</span><span class="sxs-lookup"><span data-stu-id="e9bd7-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="e9bd7-108">IdFix 使用的多租户和专用错误排除</span><span class="sxs-lookup"><span data-stu-id="e9bd7-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="e9bd7-109">此部分列出了 IdFix 从目录的搜索中排除的对象、属性和值。</span><span class="sxs-lookup"><span data-stu-id="e9bd7-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="e9bd7-110">星号（\*）是一个可替代其他字符的通配符。</span><span class="sxs-lookup"><span data-stu-id="e9bd7-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="e9bd7-111">在 IdFix 搜索过程中排除的对象、属性和值</span><span class="sxs-lookup"><span data-stu-id="e9bd7-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="e9bd7-112">**排除**</span><span class="sxs-lookup"><span data-stu-id="e9bd7-112">**Exclusion**</span></span>|<span data-ttu-id="e9bd7-113">**示例**</span><span class="sxs-lookup"><span data-stu-id="e9bd7-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e9bd7-114">Admini\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-114">Admini\*</span></span> |<span data-ttu-id="e9bd7-115">管理员</span><span class="sxs-lookup"><span data-stu-id="e9bd7-115">Administrator</span></span> |
|<span data-ttu-id="e9bd7-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-116">CAS_{\*</span></span>  |<span data-ttu-id="e9bd7-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="e9bd7-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="e9bd7-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="e9bd7-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="e9bd7-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="e9bd7-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-120">FederatedEmail\*</span></span> |<span data-ttu-id="e9bd7-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="e9bd7-121">FederatedEmail.</span></span> <span data-ttu-id="e9bd7-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-122">*GUID*</span></span> |
|<span data-ttu-id="e9bd7-123">Guest\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-123">Guest\*</span></span> ||
|<span data-ttu-id="e9bd7-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-124">HTTPConnector\*</span></span>  |<span data-ttu-id="e9bd7-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="e9bd7-125">HTTPConnector</span></span> |
|<span data-ttu-id="e9bd7-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-126">krbtgt\*</span></span> |<span data-ttu-id="e9bd7-127">ms-DS-链接</span><span class="sxs-lookup"><span data-stu-id="e9bd7-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="e9bd7-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-128">iusr_\*</span></span> |<span data-ttu-id="e9bd7-129">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="e9bd7-130">iwam\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-130">iwam\*</span></span>  |<span data-ttu-id="e9bd7-131">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="e9bd7-132">msol\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-132">msol\*</span></span> |<span data-ttu-id="e9bd7-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="e9bd7-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="e9bd7-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-134">support_\*</span></span> ||
|<span data-ttu-id="e9bd7-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-135">SystemMailbox\*</span></span> |<span data-ttu-id="e9bd7-136">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="e9bd7-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="e9bd7-137">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="e9bd7-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="e9bd7-138">distinguishedName 包含 "\0ACNF："</span><span class="sxs-lookup"><span data-stu-id="e9bd7-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="e9bd7-139">"\0ACNF： *GUID* "</span><span class="sxs-lookup"><span data-stu-id="e9bd7-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="e9bd7-140">对象包含 IsCriticalSystemObject 属性</span><span class="sxs-lookup"><span data-stu-id="e9bd7-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="e9bd7-141">请参阅[属性 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)。</span><span class="sxs-lookup"><span data-stu-id="e9bd7-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="e9bd7-142">由 IdFix 检查的多租户和专用对象和属性</span><span class="sxs-lookup"><span data-stu-id="e9bd7-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="e9bd7-143">通过[使用 IdFix 工具在准备目录属性以与 Office 365 同步](prepare-directory-attributes-for-synch-with-idfix.md)中的 "目录对象和属性准备" 一节中介绍了 IdFix 检查是否有错误的属性。</span><span class="sxs-lookup"><span data-stu-id="e9bd7-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

