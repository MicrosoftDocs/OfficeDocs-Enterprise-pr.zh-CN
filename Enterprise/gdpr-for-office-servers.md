---
title: 用于 Office Server 的 GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 了解如何解决本地 Office 服务器中的 GDPR 要求。
ms.openlocfilehash: dc1150361db6a28f011e4890a2770f4a6b607a91
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-office-on-premises-servers"></a><span data-ttu-id="a3eda-103">用于本地 Office 服务器的 GDPR</span><span class="sxs-lookup"><span data-stu-id="a3eda-103">GDPR for Office on-premises Servers</span></span>

<span data-ttu-id="a3eda-p101">一般数据保护条例 (GDPR) 为组织提供了保护个人数据和适当回应数据主体请求的要求。本系列文章为本地工作负载提供了推荐的方法：</span><span class="sxs-lookup"><span data-stu-id="a3eda-p101">The General Data Protection Regulation (GDPR) introduces requirements for organizations to protect personal data and respond appropriately to data subject requests. This series of articles provides recommended approaches for on-premises workloads:</span></span>

-   [<span data-ttu-id="a3eda-106">Exchange Server</span><span class="sxs-lookup"><span data-stu-id="a3eda-106">Exchange Server</span></span>](gdpr-for-exchange-server.md)

-   [<span data-ttu-id="a3eda-107">Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="a3eda-107">Skype for Business Server</span></span>](gdpr-for-skype-for-business-server.md)

-   [<span data-ttu-id="a3eda-108">Project Server</span><span class="sxs-lookup"><span data-stu-id="a3eda-108">Project Server</span></span>](gdpr-for-project-server.md)

-   [<span data-ttu-id="a3eda-109">Office Web Apps Server 和 Office Online Server</span><span class="sxs-lookup"><span data-stu-id="a3eda-109">Office Web Apps Server and Office Online Server</span></span>](gdpr-for-office-online-server.md)

-   [<span data-ttu-id="a3eda-110">本地文件共享</span><span class="sxs-lookup"><span data-stu-id="a3eda-110">On-premises file shares</span></span>](gdpr-for-on-premises-file-shares.md)

<span data-ttu-id="a3eda-111">有关 GDPR 以及 Microsoft 如何为你提供帮助的详细信息，请参阅 [Microsoft 信任中心](https://www.microsoft.com/zh-CN/TrustCenter/Privacy/gdpr/default.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a3eda-111">For more information about the GDPR and how Microsoft can help you, see the [Microsoft Trust Center](https://www.microsoft.com/zh-CN/TrustCenter/Privacy/gdpr/default.aspx).</span></span>

<span data-ttu-id="a3eda-p102">在开展有关本地数据的任何工作之前，请咨询你的法律和合规性团队以寻求指导并了解现有分类架构和处理个人数据的方法。Microsoft 提供了有关在 Microsoft GDPR 数据发现工具包（位于 [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>)）中开发和扩展分类架构的建议。此工具包还介绍了将本地数据移动到云的方法，可以使用更复杂的数据治理功能（如果需要）。该部分中的文章提供了有关保留在本地的数据的建议。</span><span class="sxs-lookup"><span data-stu-id="a3eda-p102">Before doing any work with on-premises data, consult with your legal and compliance teams to seek guidance and to learn about existing classification schemas and approaches to working with personal data. Microsoft provides recommendations for developing and extending classifications schemas in the Microsoft GDPR Data Discovery Toolkit at [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>). This toolkit also describes approaches for moving on-premises data to the cloud where you can use more sophisticated data governance capabilities, if this is desired. The articles in this section provide recommendations for data that is intended to remain on premises.</span></span>

<span data-ttu-id="a3eda-p103">下图列出了在各个工作负载中使用的推荐功能，用于发现、保护和监视个人数据并对其进行分类。有关更多信息，请参阅该部分中的文章。</span><span class="sxs-lookup"><span data-stu-id="a3eda-p103">The following illustration lists recommended capabilities to use across each of these workloads to discover, classify, protect, and monitor personal data. See the articles in this section for more information.</span></span>

![](media/gdpr-for-office-servers_image1.png)

## <a name="illustration-description"></a><span data-ttu-id="a3eda-118">图示说明</span><span class="sxs-lookup"><span data-stu-id="a3eda-118">Illustration description</span></span>

<span data-ttu-id="a3eda-119">为便于访问，下表提供了上图中的相同示例。</span><span class="sxs-lookup"><span data-stu-id="a3eda-119">For accessibility, the following table provides the same examples in the illustration.</span></span>

|             |<span data-ttu-id="a3eda-120">Windows Server 文件共享</span><span class="sxs-lookup"><span data-stu-id="a3eda-120">Windows Server file shares</span></span>|<span data-ttu-id="a3eda-121">SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="a3eda-121">SharePoint Server</span></span>|<span data-ttu-id="a3eda-122">Exchange Server</span><span class="sxs-lookup"><span data-stu-id="a3eda-122">Exchange Server</span></span>|<span data-ttu-id="a3eda-123">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="a3eda-123">Skype for Business</span></span>|<span data-ttu-id="a3eda-124">Project Server</span><span class="sxs-lookup"><span data-stu-id="a3eda-124">Project Server</span></span>|
|:------------|:-------------------------|:----------------|:--------------|:-----------------|:-------------|
|<span data-ttu-id="a3eda-125">发现</span><span class="sxs-lookup"><span data-stu-id="a3eda-125">discover
</span></span>|<span data-ttu-id="a3eda-126">Azure 信息保护扫描程序\*</span><span class="sxs-lookup"><span data-stu-id="a3eda-126">Azure Information Protection</span></span>|<span data-ttu-id="a3eda-127">搜索中心或电子数据展示（数据分类后）；Azure 信息保护扫描程序\*</span><span class="sxs-lookup"><span data-stu-id="a3eda-127">Search Center or eDiscovery (after data is classified); Azure Information Protection scanner\*</span></span>|<span data-ttu-id="a3eda-128">Exchange 电子数据展示门户</span><span class="sxs-lookup"><span data-stu-id="a3eda-128">Exchange eDiscovery Portal</span></span>|<span data-ttu-id="a3eda-129">Exchange 电子数据展示门户</span><span class="sxs-lookup"><span data-stu-id="a3eda-129">Exchange eDiscovery portal</span></span>|<span data-ttu-id="a3eda-130">用于发现和导出的 SQL 脚本</span><span class="sxs-lookup"><span data-stu-id="a3eda-130">SQL scripts for discovery and exporting</span></span>|
|<span data-ttu-id="a3eda-131">分类</span><span class="sxs-lookup"><span data-stu-id="a3eda-131">Classify</span></span>|<span data-ttu-id="a3eda-132">Azure 信息保护扫描程序\*；Office 365 敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="a3eda-132">Azure Information Protection scanner\*; Office 365 sensitive information types</span></span>|<span data-ttu-id="a3eda-133">Azure 信息保护扫描程序\*；Office 365 敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="a3eda-133">Azure Information Protection scanner\*; Office 365 sensitive information types</span></span>|<span data-ttu-id="a3eda-134">Exchange 保留标记和保留策略</span><span class="sxs-lookup"><span data-stu-id="a3eda-134">Exchange retention tags and retention policies</span></span>|<span data-ttu-id="a3eda-135">Exchange 保留标记和保留策略</span><span class="sxs-lookup"><span data-stu-id="a3eda-135">Exchange retention tags and retention policies</span></span>||
|<span data-ttu-id="a3eda-136">保护</span><span class="sxs-lookup"><span data-stu-id="a3eda-136">protect</span></span>||<span data-ttu-id="a3eda-137">Exchange Server 数据丢失防护规则；权限，库的 IRM 保护</span><span class="sxs-lookup"><span data-stu-id="a3eda-137">Exchange Server data loss prevention rules; Permissions, IRM-protection for libraries</span></span>|<span data-ttu-id="a3eda-138">Exchange Server 数据丢失防护规则；与 Exchange Server 的 IRM 集成</span><span class="sxs-lookup"><span data-stu-id="a3eda-138">Exchange Server data loss prevention rules; IRM integration with Exchange Server</span></span>|||
|<span data-ttu-id="a3eda-139">监视</span><span class="sxs-lookup"><span data-stu-id="a3eda-139">Monitor</span></span>|<span data-ttu-id="a3eda-140">将日志与 SIEM 工具集成</span><span class="sxs-lookup"><span data-stu-id="a3eda-140">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="a3eda-141">将日志与 SIEM 工具集成</span><span class="sxs-lookup"><span data-stu-id="a3eda-141">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="a3eda-142">将日志与 SIEM 工具集成</span><span class="sxs-lookup"><span data-stu-id="a3eda-142">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="a3eda-143">将日志与 SIEM 工具集成</span><span class="sxs-lookup"><span data-stu-id="a3eda-143">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="a3eda-144">将日志与 SIEM 工具集成</span><span class="sxs-lookup"><span data-stu-id="a3eda-144">Integrate logs with SIEM tools</span></span>|

<span data-ttu-id="a3eda-p104">\*对于 GDPR，应用不包含保护的标签。保护功能可以加密文件。因此，SharePoint Server 无法在这些文件中找到敏感信息类型。</span><span class="sxs-lookup"><span data-stu-id="a3eda-p104">\*For GDPR, apply labels that do not include protection. Protection encrypts the file. Consequently, SharePoint Server can't find the sensitive information types in these files.</span></span>
