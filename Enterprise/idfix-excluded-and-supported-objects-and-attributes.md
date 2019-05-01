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
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487178"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="799b9-103">IdFix 排除和支持的对象和属性</span><span class="sxs-lookup"><span data-stu-id="799b9-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="799b9-104">有两组由 IdFix 维护的规则;多租户和专用/ITAR。</span><span class="sxs-lookup"><span data-stu-id="799b9-104">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="799b9-105">此时, 这两个规则集将从其搜索中排除相同的对象、属性和属性值。</span><span class="sxs-lookup"><span data-stu-id="799b9-105">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="799b9-106">这可能会在将来的版本中发生变化。</span><span class="sxs-lookup"><span data-stu-id="799b9-106">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="799b9-107">IdFix 使用的多租户和专用错误排除</span><span class="sxs-lookup"><span data-stu-id="799b9-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="799b9-108">此部分列出了 IdFix 从目录的搜索中排除的对象、属性和值。</span><span class="sxs-lookup"><span data-stu-id="799b9-108">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="799b9-109">星号 (\*) 是一个可替代其他字符的通配符。</span><span class="sxs-lookup"><span data-stu-id="799b9-109">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="799b9-110">在 IdFix 搜索过程中排除的对象、属性和值</span><span class="sxs-lookup"><span data-stu-id="799b9-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="799b9-111">**排除**</span><span class="sxs-lookup"><span data-stu-id="799b9-111">**Exclusion**</span></span>|<span data-ttu-id="799b9-112">**示例**</span><span class="sxs-lookup"><span data-stu-id="799b9-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="799b9-113">Admini\*</span><span class="sxs-lookup"><span data-stu-id="799b9-113">Admini\*</span></span> |<span data-ttu-id="799b9-114">管理员</span><span class="sxs-lookup"><span data-stu-id="799b9-114">Administrator</span></span> |
|<span data-ttu-id="799b9-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="799b9-115">CAS_{\*</span></span>  |<span data-ttu-id="799b9-116">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="799b9-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="799b9-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="799b9-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="799b9-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="799b9-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="799b9-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="799b9-119">FederatedEmail\*</span></span> |<span data-ttu-id="799b9-120">FederatedEmail。</span><span class="sxs-lookup"><span data-stu-id="799b9-120">FederatedEmail.</span></span> <span data-ttu-id="799b9-121">*GUID*</span><span class="sxs-lookup"><span data-stu-id="799b9-121">*GUID*</span></span> |
|<span data-ttu-id="799b9-122">Guest\*</span><span class="sxs-lookup"><span data-stu-id="799b9-122">Guest\*</span></span> ||
|<span data-ttu-id="799b9-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="799b9-123">HTTPConnector\*</span></span>  |<span data-ttu-id="799b9-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="799b9-124">HTTPConnector</span></span> |
|<span data-ttu-id="799b9-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="799b9-125">krbtgt\*</span></span> |<span data-ttu-id="799b9-126">ms-DS-链接</span><span class="sxs-lookup"><span data-stu-id="799b9-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="799b9-127">iusr\*</span><span class="sxs-lookup"><span data-stu-id="799b9-127">iusr_\*</span></span> |<span data-ttu-id="799b9-128">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="799b9-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="799b9-129">iwam\*</span><span class="sxs-lookup"><span data-stu-id="799b9-129">iwam\*</span></span>  |<span data-ttu-id="799b9-130">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="799b9-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="799b9-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="799b9-131">msol\*</span></span> |<span data-ttu-id="799b9-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="799b9-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="799b9-133">支持\*</span><span class="sxs-lookup"><span data-stu-id="799b9-133">support_\*</span></span> ||
|<span data-ttu-id="799b9-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="799b9-134">SystemMailbox\*</span></span> |<span data-ttu-id="799b9-135">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="799b9-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="799b9-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="799b9-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="799b9-137">distinguishedName 包含 "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="799b9-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="799b9-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="799b9-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="799b9-139">对象包含 IsCriticalSystemObject 属性</span><span class="sxs-lookup"><span data-stu-id="799b9-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="799b9-140">请参阅[属性 isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)。</span><span class="sxs-lookup"><span data-stu-id="799b9-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="799b9-141">由 IdFix 检查的多租户和专用对象和属性</span><span class="sxs-lookup"><span data-stu-id="799b9-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="799b9-142">通过[使用 IdFix 工具在准备目录属性以与 Office 365 同步](prepare-directory-attributes-for-synch-with-idfix.md)中的 "目录对象和属性准备" 一节中介绍了 IdFix 检查是否有错误的属性。</span><span class="sxs-lookup"><span data-stu-id="799b9-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

