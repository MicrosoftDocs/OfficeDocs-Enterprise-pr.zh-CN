---
title: 用于本地文件共享的 GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 了解如何解决本地 Windows Server 文件共享中的 GDPR 要求。
ms.openlocfilehash: d9d17f134d77ee03e11208744ba9a2e56d506b1f
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-on-premises-windows-server-file-shares"></a><span data-ttu-id="80ec6-103">用于本地 Windows Server 文件共享的 GDPR</span><span class="sxs-lookup"><span data-stu-id="80ec6-103">GDPR for on-premises Windows Server file shares</span></span>

<span data-ttu-id="80ec6-104">推荐的基本文件共享方法是：</span><span class="sxs-lookup"><span data-stu-id="80ec6-104">The basic recommended approach for file shares is:</span></span>

-   <span data-ttu-id="80ec6-105">使用 Azure 信息保护来标记敏感数据。</span><span class="sxs-lookup"><span data-stu-id="80ec6-105">Use Azure Information Protection to label sensitive data.</span></span>

-   <span data-ttu-id="80ec6-106">使用 Azure 信息保护扫描程序来查找数据。</span><span class="sxs-lookup"><span data-stu-id="80ec6-106">Use Azure Information Protection scanner to find data.</span></span>

<span data-ttu-id="80ec6-107">推荐的文件共享方法包括下列步骤：</span><span class="sxs-lookup"><span data-stu-id="80ec6-107">The recommended approach for files shares includes these steps:</span></span>

1.  <span data-ttu-id="80ec6-108">**安装并配置 Azure 信息保护扫描程序。**</span><span class="sxs-lookup"><span data-stu-id="80ec6-108">**Install and configure Azure Information Protection scanner.**</span></span>

    -   <span data-ttu-id="80ec6-109">决定要使用的敏感数据类型。</span><span class="sxs-lookup"><span data-stu-id="80ec6-109">Decide which sensitive data types to use.</span></span>

    -   <span data-ttu-id="80ec6-110">指定要使用的本地文件夹和网络共享。</span><span class="sxs-lookup"><span data-stu-id="80ec6-110">Specify local folders and network shares to use.</span></span>

2.  <span data-ttu-id="80ec6-111">**完成发现周期。**</span><span class="sxs-lookup"><span data-stu-id="80ec6-111">**Complete a discovery cycle.**</span></span>

    -   <span data-ttu-id="80ec6-112">以发现模式运行扫描程序并验证查找结果。</span><span class="sxs-lookup"><span data-stu-id="80ec6-112">Run the scanner in discovery mode and validate the findings.</span></span>

    -   <span data-ttu-id="80ec6-113">如果需要，优化条件和敏感信息类型。</span><span class="sxs-lookup"><span data-stu-id="80ec6-113">If needed, optimize the conditions and sensitive information types.</span></span>

    -   <span data-ttu-id="80ec6-114">评估自动应用标签的预期影响。</span><span class="sxs-lookup"><span data-stu-id="80ec6-114">Assess the expected impact of automatically applying labels.</span></span>

3.  <span data-ttu-id="80ec6-115">**运行 Azure 信息保护扫描程序以便标记合格文档**</span><span class="sxs-lookup"><span data-stu-id="80ec6-115">**Run the Azure Information Protection scanner to apply labels to qualifying documents**.</span></span>

4.  <span data-ttu-id="80ec6-116">**用于保护：**</span><span class="sxs-lookup"><span data-stu-id="80ec6-116">**For protection:**</span></span>

    -   <span data-ttu-id="80ec6-117">配置 Exchange 数据丢失防护规则以保护具有所需标签的文档。</span><span class="sxs-lookup"><span data-stu-id="80ec6-117">Configure Exchange data loss prevention rules to protect documents with the desired label.</span></span>

    -   <span data-ttu-id="80ec6-118">务必要使用权限来限制谁可以访问文件。</span><span class="sxs-lookup"><span data-stu-id="80ec6-118">Be sure to use permissions to limit who can access files.</span></span>

5.  <span data-ttu-id="80ec6-119">**要进行监控，请使用 SIEM 工具集成 Windows Server 日志。**</span><span class="sxs-lookup"><span data-stu-id="80ec6-119">**For monitoring, integrate Windows Server logs with a SIEM tool.**</span></span>

    -   <span data-ttu-id="80ec6-p101">要为数据主体请求查找个人数据，请使用 Azure 信息保护扫描程序。还可以配置 SharePoint Server 搜索以爬网文件共享。</span><span class="sxs-lookup"><span data-stu-id="80ec6-p101">To find personal data for data subject requests, use Azure Information Protection scanner. You can also configure SharePoint Server search to crawl file shares.</span></span>

<span data-ttu-id="80ec6-122">有关使用 Azure 信息保护扫描程序查找和标记个人数据的详细信息，请参阅位于 [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>) 中的 Microsoft GDPR 数据发现工具包。</span><span class="sxs-lookup"><span data-stu-id="80ec6-122">For more information on using Azure Information Protection scanner to find and label personal data, see the Microsoft GDPR Data Discovery Toolkit at [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>).</span></span>

<span data-ttu-id="80ec6-p102">有关配置条件扫描程序和使用 Office 365 数据丢失防护 (DLP) 敏感信息类型的信息，请参阅[如何配置 Azure 信息保护的自动和建议分类的条件](https://docs.microsoft.com/zh-CN/information-protection/deploy-use/configure-policy-classification)。请注意，新的 Office 365 敏感信息类型不会立即可供扫描程序使用，并且自定义敏感信息类型不能与扫描程序一起使用。</span><span class="sxs-lookup"><span data-stu-id="80ec6-p102">For information on configuring the scanner for conditions and using the Office 365 data loss prevention (DLP) sensitive information types, see [How to configure conditions for automatic and recommended classification for Azure Information Protection](https://docs.microsoft.com/zh-CN/information-protection/deploy-use/configure-policy-classification). Note that new Office 365 sensitive information types will not be immediately available to use with the scanner and custom sensitive information types cannot be used with the scanner.</span></span>
