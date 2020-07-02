---
title: Microsoft 365 搜索中的租户隔离
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: 摘要： Microsoft 365 搜索中的租户隔离说明。
ms.openlocfilehash: 2c57b5610fd1a59f2cff2001981e77e354226452
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998252"
---
# <a name="tenant-isolation-in-microsoft-365-search"></a><span data-ttu-id="2bfa5-103">Microsoft 365 搜索中的租户隔离</span><span class="sxs-lookup"><span data-stu-id="2bfa5-103">Tenant Isolation in Microsoft 365 Search</span></span>

<span data-ttu-id="2bfa5-104">SharePoint Online 搜索使用租户分离模型来平衡共享数据结构的效率，并防止租户之间的信息泄露。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-104">SharePoint Online search uses a tenant separation model that balances the efficiency of shared data structures with protection against information leaking between tenants.</span></span> <span data-ttu-id="2bfa5-105">在此模型中，我们阻止搜索功能来自：</span><span class="sxs-lookup"><span data-stu-id="2bfa5-105">With this model, we prevent the Search features from:</span></span>

- <span data-ttu-id="2bfa5-106">返回包含来自其他租户的文档的查询结果</span><span class="sxs-lookup"><span data-stu-id="2bfa5-106">Returning query results that contain documents from other tenants</span></span>
- <span data-ttu-id="2bfa5-107">在查询结果中公开足够的信息，训练有素的用户可以推断有关其他租户的信息</span><span class="sxs-lookup"><span data-stu-id="2bfa5-107">Exposing sufficient information in query results that a skilled user could infer information about other tenants</span></span>
- <span data-ttu-id="2bfa5-108">显示其他租户中的架构或设置</span><span class="sxs-lookup"><span data-stu-id="2bfa5-108">Showing schema or settings from another tenant</span></span>
- <span data-ttu-id="2bfa5-109">将分析处理信息混合在租户或存储结果中的错误租户中</span><span class="sxs-lookup"><span data-stu-id="2bfa5-109">Mixing analytics processing information between tenants or store results in the wrong tenant</span></span>
- <span data-ttu-id="2bfa5-110">使用其他租户中的字典条目</span><span class="sxs-lookup"><span data-stu-id="2bfa5-110">Using dictionary entries from another tenant</span></span>

<span data-ttu-id="2bfa5-111">对于每种类型的租户数据，我们在代码中使用一个或多个保护层，以防止意外泄漏信息。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-111">For each type of tenant data, we use one or more layers of protection in the code to prevent accidental leaking of information.</span></span> <span data-ttu-id="2bfa5-112">最关键的数据具有最多的保护层，以确保单个缺陷不会导致实际或感觉信息泄露。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-112">The most critical data has the most layers of protection to make sure that a single defect doesn't result in actual or perceived information leakage.</span></span>

## <a name="tenant-separation-for-the-search-index"></a><span data-ttu-id="2bfa5-113">搜索索引的租户分离</span><span class="sxs-lookup"><span data-stu-id="2bfa5-113">Tenant Separation for the Search Index</span></span>

<span data-ttu-id="2bfa5-114">搜索索引存储在磁盘上托管索引组件的服务器上，租户共享索引文件。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-114">The search index is stored on disk in the servers hosting the index components and the tenants share the index files.</span></span> <span data-ttu-id="2bfa5-115">租户的已编制索引的文档仅对该租户的查询可见。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-115">A tenant's indexed documents are visible only for queries for that tenant.</span></span> <span data-ttu-id="2bfa5-116">三种独立的机制防止信息泄露：</span><span class="sxs-lookup"><span data-stu-id="2bfa5-116">Three independent mechanisms prevent information leakage:</span></span>

- <span data-ttu-id="2bfa5-117">租户 ID 筛选</span><span class="sxs-lookup"><span data-stu-id="2bfa5-117">Tenant ID filtering</span></span>
- <span data-ttu-id="2bfa5-118">租户 ID 条款前缀</span><span class="sxs-lookup"><span data-stu-id="2bfa5-118">Tenant ID term prefixing</span></span>
- <span data-ttu-id="2bfa5-119">ACL 检查</span><span class="sxs-lookup"><span data-stu-id="2bfa5-119">ACL checks</span></span>

<span data-ttu-id="2bfa5-120">所有三种机制都必须失败，才能使搜索将文档返回到错误的租户。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-120">All three mechanisms would have to fail for Search to return documents to the wrong tenant.</span></span>

## <a name="tenant-id-filtering-and-tenant-id-term-prefixing"></a><span data-ttu-id="2bfa5-121">租户 ID 筛选和租户 ID 条款前缀</span><span class="sxs-lookup"><span data-stu-id="2bfa5-121">Tenant ID Filtering and Tenant ID Term Prefixing</span></span>

<span data-ttu-id="2bfa5-122">搜索将为使用租户 ID 在全文索引中编制索引的每个术语加上前缀。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-122">Search prefixes every term that is indexed in the full-text index with the tenant ID.</span></span> <span data-ttu-id="2bfa5-123">例如，当 ID 为 "*123*" 的租户为术语编制索引时，全文本索引中的条目是 "*123foo"。\*\*foo*</span><span class="sxs-lookup"><span data-stu-id="2bfa5-123">For example, when the term "*foo*" is indexed for a tenant with an ID of "*123*", the entry in the full-text index is "*123foo.*"</span></span>

<span data-ttu-id="2bfa5-124">每个查询都将转换为包含使用名为租户 ID 筛选的过程的租户 ID。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-124">Every query is converted to include the tenant ID using a process called tenant ID filtering.</span></span> <span data-ttu-id="2bfa5-125">例如，查询 "*foo*" 将转换为 "<*guid*>。*foo*和*tenantID*： <*guid*> "，其中 <*guid*> 表示执行查询的租户。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-125">For example, the query "*foo*" is converted to "<*guid*>.*foo* AND *tenantID*:<*guid*>", where <*guid*> represents the tenant performing the query.</span></span> <span data-ttu-id="2bfa5-126">此查询转换发生在每个索引节点中，并且不能对查询和内容处理进行影响。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-126">This query conversion occurs within each index node and neither query nor content processing can influence it.</span></span> <span data-ttu-id="2bfa5-127">由于租户 ID 已添加到每个查询中，因此无法通过在一个租户中查看最佳匹配排名来推断出其他租户中术语的频率。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-127">Because the tenant ID is added to every query, the frequency of a term in other tenants can't be inferred by looking at best match ranking in one tenant.</span></span>

<span data-ttu-id="2bfa5-128">租户 ID 条款前缀仅发生在全文本索引中。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-128">Tenant ID term prefixing occurs only in the full-text index.</span></span> <span data-ttu-id="2bfa5-129">上市搜索（如 "*title： foo*"）转到一个合成搜索索引，其中术语不以租户 ID 作为前缀。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-129">Fielded searches, such as "*title:foo*", go to a synthetic search index where terms aren't prefixed by tenant ID.</span></span> <span data-ttu-id="2bfa5-130">相反，上市搜索将以字段名称作为前缀。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-130">Instead, fielded searches are prefixed with the field name.</span></span> <span data-ttu-id="2bfa5-131">例如，查询 "*title： foo*" 将转换为 "fields：*foo 和 fields. tenantID*： <*guid*>"。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-131">For example, the query "*title:foo*" is converted to "*fields.title:foo AND fields.tenantID*:<*guid*>."</span></span> <span data-ttu-id="2bfa5-132">由于术语的频率不影响合成搜索索引中的命中排名，因此无需在术语 "前缀" 的情况下进行租户分隔。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-132">Because the frequency of a term doesn't influence ranking of hits in the synthetic search index, there's no need for tenant separation by term prefixing.</span></span> <span data-ttu-id="2bfa5-133">对于上市搜索（如 "*title： foo*"），租户内容分离取决于租户 ID 筛选（通过查询转换）。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-133">For a fielded search like "*title:foo*", tenant content separation depends on tenant ID filtering by query conversion.</span></span>

## <a name="document-access-control-list-checks"></a><span data-ttu-id="2bfa5-134">文档访问控制列表检查</span><span class="sxs-lookup"><span data-stu-id="2bfa5-134">Document Access Control List Checks</span></span>

<span data-ttu-id="2bfa5-135">搜索控制通过在搜索索引中保存的 Acl 对文档的访问。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-135">Search controls access to documents through ACLs that are saved in the search index.</span></span> <span data-ttu-id="2bfa5-136">每个项目都使用特殊 ACL 字段中的一组术语编制索引。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-136">Every item is indexed with a set of terms in a special ACL field.</span></span> <span data-ttu-id="2bfa5-137">ACL 字段包含可查看文档的每个组或用户一个术语。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-137">The ACL field contains one term per group or user that can view the document.</span></span> <span data-ttu-id="2bfa5-138">每个查询都使用一系列访问控制项（ACE）术语进行扩充，每个查询已通过身份验证的用户所属的组一个。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-138">Every query is augmented with a list of access control entry (ACE) terms, one for each group to which the authenticated user belongs.</span></span>

<span data-ttu-id="2bfa5-139">例如，类似于 "<*guid*> 的查询。*FOO 和 tenantID*： <*guid*> "将变为：" <*guid*>。*foo 和 tenantID*： <*guid* >  *和*（*docACL：* < *ace1* >  *或 docACL*： <*ace2* >  *or docACL*： <*ace3* >  *...*） "</span><span class="sxs-lookup"><span data-stu-id="2bfa5-139">For example, a query like "<*guid*>.*foo AND tenantID*:<*guid*>" becomes: "<*guid*>.*foo AND tenantID*:<*guid*> *AND* (*docACL:*<*ace1*> *OR docACL*:<*ace2*> *OR docACL*:<*ace3*> *...*)"</span></span>

<span data-ttu-id="2bfa5-140">由于用户和组标识符，因此 Ace 是唯一的，因此这将为仅对某些用户可见的文档提供其他级别的安全性。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-140">Because user and group identifiers and hence ACEs are unique, this provides an extra level of security between tenants for documents that are only visible to some users.</span></span> <span data-ttu-id="2bfa5-141">对于在租户中向常规用户授予访问权限的特殊 "除外部用户之外的任何人" ACE 也是如此。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-141">The same is the case for the special "Everyone except external users" ACE that grants access to regular users in the tenant.</span></span> <span data-ttu-id="2bfa5-142">但由于 "Everyone" 的 Ace 对于所有租户都是相同的，因此公共文档的租户分隔取决于租户 ID 筛选。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-142">But since ACEs for "Everyone" are the same for all tenants, tenant separation for public documents depends on tenant ID filtering.</span></span> <span data-ttu-id="2bfa5-143">此外，还支持 Deny Ace。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-143">Deny ACEs are also supported.</span></span> <span data-ttu-id="2bfa5-144">当与 deny ACE 匹配时，查询扩充将添加从结果中删除文档的子句。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-144">The query augmentation adds a clause that removes a document from the result when there is a match with a deny ACE.</span></span>

<span data-ttu-id="2bfa5-145">在 Exchange Online 搜索中，索引在邮箱 ID 上针对单个用户的邮箱（而不是租户 ID （订阅 ID））进行分区，就像在 SharePoint Online 中一样。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-145">In Exchange Online search, the index is partitioned on mailbox ID for individual user's mailboxes instead of tenant ID (subscription ID) as in SharePoint Online.</span></span> <span data-ttu-id="2bfa5-146">分区机制与 SharePoint Online 相同，但没有 ACL 筛选。</span><span class="sxs-lookup"><span data-stu-id="2bfa5-146">The partitioning mechanism is the same as SharePoint Online, but there is no ACL filtering.</span></span>
