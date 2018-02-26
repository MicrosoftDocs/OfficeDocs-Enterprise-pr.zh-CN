---
title: "针对 GDPR 的 Office 365 信息保护概述"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- Strat_O365_Enterprise
- GDPR
ms.assetid: 
description: "概述针对 GDPR 的 Office 365 信息保护。了解如何发现、分类、保护和监视个人数据。"
ms.openlocfilehash: b3af91608d545b221694b9e4a18db07b85d7541a
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="overview-of-office-365-information-protection-for-gdpr"></a><span data-ttu-id="0fe93-104">针对 GDPR 的 Office 365 信息保护概述</span><span class="sxs-lookup"><span data-stu-id="0fe93-104">Overview of Office 365 Information Protection for GDPR</span></span>

<span data-ttu-id="0fe93-p102">此解决方案演示了如何保护存储在 Office 365 服务中的敏感数据。其中包括针对发现、分类、保护和监视个人数据的指导性建议。该解决方案以一般数据保护条例 (GDPR) 为例，但用户可以采用同一流程实现对许多其他条例的符合性。</span><span class="sxs-lookup"><span data-stu-id="0fe93-p102">This solution demonstrates how to protect sensitive data that is stored in Office 365 services. It includes prescriptive recommendations for discovering, classifying, protecting, and monitoring personal data. This solution uses General Data Protection Regulation (GDPR) as an example, but you can apply the same process to achieve compliance with many other regulations.</span></span>

<span data-ttu-id="0fe93-p103">GDPR 对个人数据的收集、存储、处理和共享进行了规范化。个人数据在 GDPR 中的定义非常宽泛，即指属于欧盟 (EU) 居民的已确定身份的或可识别的自然人的任何相关数据。</span><span class="sxs-lookup"><span data-stu-id="0fe93-p103">GDPR regulates the collection, storage, processing, and sharing of personal data. Personal data is defined very broadly under the GDPR as any data that relates to an identified or identifiable natural person that is a resident of the European Union (EU).</span></span>

<span data-ttu-id="0fe93-110">第 4 条 – 定义</span><span class="sxs-lookup"><span data-stu-id="0fe93-110">Article 4 – Definitions</span></span>

> <span data-ttu-id="0fe93-111">“个人数据”表示已确定身份的或可识别的自然人（“数据主体”）的任何相关信息；可识别的自然人是指可被直接或间接识别出的自然人，尤其是通过参考姓名、证件号码、位置数据、网络标识等标识，或通过参考特定于该自然人的身体、生理、基因、精神、经济、文化或社会标识的一个或多个因素进行识别；</span><span class="sxs-lookup"><span data-stu-id="0fe93-111">‘personal data’ means any information relating to an identified or identifiable natural person (‘data subject’); an identifiable natural person is one who can be identified, directly or indirectly, in particular by reference to an identifier such as a name, an identification number, location data, an online identifier or to one or more factors specific to the physical, physiological, genetic, mental, economic, cultural or social identity of that natural person;</span></span>

<span data-ttu-id="0fe93-p104">该解决方案旨在帮助组织发现和保护 Office 365 中可能受 GDPR 制约的个人数据。它并不用作 GDPR 符合性证明。组织负责确保其自己的 GDPR 符合性，并且经建议咨询其法律和合规团队，或向专门致力于符合性的第三方寻求指导和建议。</span><span class="sxs-lookup"><span data-stu-id="0fe93-p104">This solution is intended to help organizations discover and protect personal data in Office 365 that might be subject to the GDPR. It is not offered as a GDPR compliance attestation. Organizations are responsible for ensuring their own GDPR compliance and are advised to consult their legal and compliance teams or to seek guidance and advice from third parties that specialize in compliance.</span></span>

<span data-ttu-id="0fe93-115">[GDPR 评估](https://www.gdprbenchmark.com)是可免费使用的快速在线自评工具，它可帮助组织检查其为符合 GDPR 要求而达到的整体就绪程度 (<http://aka.ms/gdprassessment>)。</span><span class="sxs-lookup"><span data-stu-id="0fe93-115">[GDPR Assessment](https://www.gdprbenchmark.com) is a quick, online self-evaluation tool available at no cost to help your organization review its overall level of readiness to comply with the GDPR (<http://aka.ms/gdprassessment>).</span></span>

## <a name="assess-and-manage-your-compliance-risk"></a><span data-ttu-id="0fe93-116">评估和管理符合性风险</span><span class="sxs-lookup"><span data-stu-id="0fe93-116">Assess and manage your compliance risk</span></span>

<span data-ttu-id="0fe93-p105">实现 GDPR 符合性的第一步是评估 GDPR 是否适用于组织，如果适用，适用程度如何。此分析包括了解组织所处理的数据及此数据所在的位置。</span><span class="sxs-lookup"><span data-stu-id="0fe93-p105">The first step towards GDPR compliance is to assess whether the GDPR applies to your organization, and, if so, to what extent. This analysis includes understanding the data your organization processes and where it resides.</span></span>

### <a name="step-1--use-compliance-manager-to-view-the-regulation-requirements-and-track-your-progress"></a><span data-ttu-id="0fe93-119">步骤 1 — 使用合规性管理器查看法规要求并跟踪进度</span><span class="sxs-lookup"><span data-stu-id="0fe93-119">Step 1 — Use Compliance Manager to view the regulation requirements and track your progress</span></span>

<span data-ttu-id="0fe93-120">合规性管理器提供用于跟踪、实现和管理审核控制的工具，可帮助组织实现各种标准的符合性，其中包括 GDPR。</span><span class="sxs-lookup"><span data-stu-id="0fe93-120">Compliance Manager provides tools to track, implement, and manage the auditing controls to help your organization reach compliance against various standards, including GDPR.</span></span>

![使用合规性管理器查看要求并跟踪进度](Media/Overview-image1.png)

<span data-ttu-id="0fe93-122">有关详细信息，请参阅[使用服务信任门户中的合规性管理器](https://support.office.com/zh-CN/article/Use-Compliance-Manager-in-the-Service-Trust-Portal-Preview-5756d342-5af9-4496-82e8-4dd50fa39942)。</span><span class="sxs-lookup"><span data-stu-id="0fe93-122">For more information, see [Use Compliance Manager in the Service Trust Portal](https://support.office.com/zh-CN/article/Use-Compliance-Manager-in-the-Service-Trust-Portal-Preview-5756d342-5af9-4496-82e8-4dd50fa39942).</span></span> 

### <a name="step-2--use-content-search-and-sensitive-information-types-to-find-personal-data"></a><span data-ttu-id="0fe93-123">步骤 2 — 使用内容搜索和敏感信息类型查找个人数据</span><span class="sxs-lookup"><span data-stu-id="0fe93-123">Step 2 — Use Content Search and sensitive information types to find personal data</span></span> 

<span data-ttu-id="0fe93-p106">发现环境中受 GDPR 制约的个人数据。结合使用内容搜索和敏感信息类型执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="0fe93-p106">Discover personal data in your environment that is subject to the GDPR. Use Content Search together with sensitive information types to:</span></span>

-   <span data-ttu-id="0fe93-126">在个人数据所在的位置进行查找和报告。</span><span class="sxs-lookup"><span data-stu-id="0fe93-126">Find and report on where personal data resides.</span></span>

-   <span data-ttu-id="0fe93-127">优化敏感数据类型及其他查询，查找环境中的所有个人数据。</span><span class="sxs-lookup"><span data-stu-id="0fe93-127">Optimize sensitive data types and other queries to find all personal data in your environment.</span></span>

![使用内容搜索和敏感信息类型查找个人数据](Media/Overview-image2.png)

<span data-ttu-id="0fe93-p107">敏感信息类型定义了自动进程识别特定信息类型（例如卫生服务号码和信用卡号码）的方式。本文附带了一组敏感信息类型，可以从这些类型入手。即将推出适用于欧盟国家/地区的个人数据的更多敏感信息类型。</span><span class="sxs-lookup"><span data-stu-id="0fe93-p107">Sensitive information types define how the automated process recognizes specific information types such as health service numbers and credit card numbers. This article includes a set you can use as a starting point. Many more sensitive information types are coming soon for personal data in EU countries.</span></span>

<span data-ttu-id="0fe93-132">有关详细信息，请参阅[搜索和查找个人数据](search-for-and-find-personal-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe93-132">For more information, see [Search for and find personal data](search-for-and-find-personal-data.md).</span></span> 

## <a name="classify-protect-and-monitor-personal-data-in-office-365-and-other-saas-apps"></a><span data-ttu-id="0fe93-133">分类、保护和监视 Office 365 及其他 SaaS 应用中的个人数据</span><span class="sxs-lookup"><span data-stu-id="0fe93-133">Classify, protect, and monitor personal data in Office 365 and other SaaS apps</span></span>

<span data-ttu-id="0fe93-134">用于 Office 365 信息保护的一些功能也可用于保护其他 SaaS 应用程序中的敏感数据。</span><span class="sxs-lookup"><span data-stu-id="0fe93-134">Some of the capabilities used for information protection in Office 365 can also be used to protect sensitive data in other SaaS applications.</span></span>

![分类、保护和监视个人数据](Media/Overview-image3.png)

<span data-ttu-id="0fe93-136">本节的剩余部分（步骤 3-5）对此图进行了说明。</span><span class="sxs-lookup"><span data-stu-id="0fe93-136">This illustration is described by the rest this section (steps 3-5).</span></span>

### <a name="step-3--decide-if-you-want-to-use-labels-in-addition-to-sensitive-information-types"></a><span data-ttu-id="0fe93-137">步骤 3 — 决定是否使用除敏感信息类型之外的其他标签</span><span class="sxs-lookup"><span data-stu-id="0fe93-137">Step 3 — Decide if you want to use labels in addition to sensitive information types</span></span>

<span data-ttu-id="0fe93-p108">敏感信息类型是一种分类形式。请参阅[为个人数据构建分类架构](architect-a-classification-schema-for-personal-data.md)，以决定是否还要使用标签。若要应用标签，请参阅[向 Office 365 中的个人数据应用标签](apply-labels-to-personal-data-in-office-365.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe93-p108">Sensitive information types are a form of classification. See [Architect a classification schema for personal data](architect-a-classification-schema-for-personal-data.md), to decide if you also want to implement labels. To apply labels, see [Apply labels to personal data in Office 365](apply-labels-to-personal-data-in-office-365.md).</span></span>

<span data-ttu-id="0fe93-p109">在此图中，敏感信息类型和标签应用到了 Office 365。即将可以结合使用这些内容和 Cloud App Security 来查找其他 SaaS 应用（例如 Box 和 Salesforce）中的敏感数据。</span><span class="sxs-lookup"><span data-stu-id="0fe93-p109">In the illustration, sensitive information types and labels work across Office 365. Coming soon, you can use these with Cloud App Security to find sensitive data in other SaaS apps, such as Box and Salesforce.</span></span>

### <a name="step-4--protect-personal-data-in-office-365"></a><span data-ttu-id="0fe93-143">步骤 4 — 保护 Office 365 中的个人数据</span><span class="sxs-lookup"><span data-stu-id="0fe93-143">Step 4 — Protect personal data in Office 365</span></span> 

<span data-ttu-id="0fe93-p110">个人数据保护始于 Office 365 数据丢失防护。有若干个其他功能被推荐用于保护个人数据的访问，其中包括适用于电子邮件的 Office 365 邮件加密功能。</span><span class="sxs-lookup"><span data-stu-id="0fe93-p110">Protection for personal data starts with Office 365 data loss prevention. There are several other capabilities recommended for protecting access to personal data, including Office 365 Message Encryption for email.</span></span>

<span data-ttu-id="0fe93-146">这些保护功能可针对特定数据集：</span><span class="sxs-lookup"><span data-stu-id="0fe93-146">These protections can be targeted to specific data sets:</span></span>

-   <span data-ttu-id="0fe93-147">网站和库级别的权限</span><span class="sxs-lookup"><span data-stu-id="0fe93-147">Site and library-level permissions</span></span>

-   <span data-ttu-id="0fe93-148">网站级别的外部共享策略</span><span class="sxs-lookup"><span data-stu-id="0fe93-148">Site-level external sharing policies</span></span>

-   <span data-ttu-id="0fe93-149">网站级别的设备访问策略</span><span class="sxs-lookup"><span data-stu-id="0fe93-149">Site-level device access controls</span></span>

<span data-ttu-id="0fe93-150">对 Office 365 和其他云服务访问的保护包括：</span><span class="sxs-lookup"><span data-stu-id="0fe93-150">Protection for access to Office 365 and other cloud services include:</span></span>

-   <span data-ttu-id="0fe93-151">企业移动性 + 安全性 (EMS) 中的标识和设备访问保护</span><span class="sxs-lookup"><span data-stu-id="0fe93-151">Identity and device access protection in Enterprise Mobility + Security (EMS)</span></span>

-   <span data-ttu-id="0fe93-152">特权访问管理</span><span class="sxs-lookup"><span data-stu-id="0fe93-152">Privileged access management</span></span>

-   <span data-ttu-id="0fe93-153">Windows 10 安全功能</span><span class="sxs-lookup"><span data-stu-id="0fe93-153">Windows 10 security capabilities</span></span>

<span data-ttu-id="0fe93-154">有关应用保护的详细信息，请参阅[向 Office 365 中的个人数据应用保护](apply-protection-to-personal-data-in-office-365.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe93-154">For more information about applying proteciton, see [Apply protection to personal data in Office 365](apply-protection-to-personal-data-in-office-365.md).</span></span>

### <a name="step-5--monitor-for-leaks-of-personal-data"></a><span data-ttu-id="0fe93-155">步骤 5 — 监视个人数据泄露</span><span class="sxs-lookup"><span data-stu-id="0fe93-155">Step 5 — Monitor for leaks of personal data</span></span>

<span data-ttu-id="0fe93-p111">Office 365 数据丢失防护报告提供了监视敏感数据的最详细的信息。可以使用 Office 365 审核日志设置自动警报并调查违规行为。Cloud App Security 将查找和监视敏感数据的功能扩展到了其他 SaaS 提供程序。有关这些工具的详细信息，请参阅[监视个人数据违规行为](monitor-for-leaks-of-personal-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe93-p111">Office 365 data loss prevention reports provide the greatest level of detail for monitoring sensitive data. You can setup automated alerts and investigate breaches by using the Office 365 audit log. Cloud App Security extends the ability to find and monitor sensitive data to other SaaS providers. For more information on these tools, see [Monitor for breaches of personal data](monitor-for-leaks-of-personal-data.md).</span></span>
