---
title: 结合使用 Office 365 内容分发网络和 SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: 介绍如何使用 Office 365 内容传送网络 (CDN) 加快将 SharePoint Online 资产传递给所有用户, 无论它们位于何处或如何访问你的内容。
ms.openlocfilehash: de8c02b44405260aa7379ab0a881ba72f73c7a6b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070628"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a><span data-ttu-id="47e04-103">结合使用 Office 365 内容分发网络和 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="47e04-103">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>

<span data-ttu-id="47e04-104">可以使用内置的 Office 365 内容分发网络 (CDN) 来托管静态资产，以便提高 SharePoint Online 页面的性能。</span><span class="sxs-lookup"><span data-stu-id="47e04-104">You can use the built-in Office 365 Content Delivery Network (CDN) to host static assets to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="47e04-105">Office 365 CDN 将静态资产缓存到距离请求这些资产的浏览器更近的位置，这样可以加快下载速度并减少延迟，进而提高性能。</span><span class="sxs-lookup"><span data-stu-id="47e04-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="47e04-106">此外, Office 365 CDN 使用[HTTP/2 协议](https://en.wikipedia.org/wiki/HTTP/2)改进了压缩和 HTTP 流水线功能。</span><span class="sxs-lookup"><span data-stu-id="47e04-106">Also, the Office 365 CDN uses the [HTTP/2 protocol](https://en.wikipedia.org/wiki/HTTP/2) for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="47e04-107">Office 365 CDN 服务被归入 SharePoint Online 订阅。</span><span class="sxs-lookup"><span data-stu-id="47e04-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

<span data-ttu-id="47e04-108">Office 365 CDN 由多个 CDN 组成，用户可以在多个位置（即_源_）托管静态资产，并从全局高速网络提供这些资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-108">The Office 365 CDN is composed of multiple CDNs that allow you to host static assets in multiple locations, or _origins_, and serve them from global high-speed networks.</span></span> <span data-ttu-id="47e04-109">可以添加**公共**源、**私有**源或同时添加这两种源，具体取决于想要托管在 Office 365 CDN 中的内容种类。</span><span class="sxs-lookup"><span data-stu-id="47e04-109">Depending on the kind of content you want to host in the Office 365 CDN, you can add **public** origins, **private** origins or both.</span></span> <span data-ttu-id="47e04-110">若要详细了解公共和专用来源之间的差异, 请参阅[选择每个来源是否应为公共的或专用](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)的。</span><span class="sxs-lookup"><span data-stu-id="47e04-110">See [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) for more information on the difference between public and private origins.</span></span>

<span data-ttu-id="47e04-111">![Office 365 CDN 概念图](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN 概念图")</span><span class="sxs-lookup"><span data-stu-id="47e04-111">![Office 365 CDN conceptual diagram](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN conceptual diagram")</span></span>

<span data-ttu-id="47e04-112">如果您已经熟悉 Cdn 的工作方式, 则只需完成几个步骤即可为租户启用 Office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="47e04-112">If you are already familiar with the way that CDNs work, you only need to complete a few steps to enable the Office 365 CDN for your tenant.</span></span> <span data-ttu-id="47e04-113">本主题介绍如何操作。</span><span class="sxs-lookup"><span data-stu-id="47e04-113">This topic describes how.</span></span> <span data-ttu-id="47e04-114">请参阅, 了解有关如何开始托管静态资产的信息。</span><span class="sxs-lookup"><span data-stu-id="47e04-114">Read on for information about how to get started hosting your static assets.</span></span>

> [!TIP]
> <span data-ttu-id="47e04-115">还有其他 Microsoft 托管的 Cdn, 可用于专门使用方案的 Office 365, 但不会在本主题中进行讨论, 因为它们超出了 Office 365 CDN 的范围。</span><span class="sxs-lookup"><span data-stu-id="47e04-115">There are other Microsoft-hosted CDNs that can be used with Office 365 for specialized usage scenarios, but are not discussed in this topic because they fall outside the scope of the Office 365 CDN.</span></span> <span data-ttu-id="47e04-116">有关详细信息, 请参阅[其他 Microsoft cdn](content-delivery-networks.md#other-microsoft-cdns)。</span><span class="sxs-lookup"><span data-stu-id="47e04-116">For more information, see [Other Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns).</span></span>

 <span data-ttu-id="47e04-117">**[面向 Office 365 的网络规划和性能调整的](https://aka.ms/tune)封底。**</span><span class="sxs-lookup"><span data-stu-id="47e04-117">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a><span data-ttu-id="47e04-118">在 SharePoint Online 中使用 Office 365 CDN 的概述</span><span class="sxs-lookup"><span data-stu-id="47e04-118">Overview of working with the Office 365 CDN in SharePoint Online</span></span>

<span data-ttu-id="47e04-119">若要为您的组织设置 Office 365 CDN, 请按照以下基本步骤操作:</span><span class="sxs-lookup"><span data-stu-id="47e04-119">To set up the Office 365 CDN for your organization, you follow these basic steps:</span></span>

- [<span data-ttu-id="47e04-120">规划 Office 365 CDN 的部署</span><span class="sxs-lookup"><span data-stu-id="47e04-120">Plan for deployment of the Office 365 CDN</span></span>](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - <span data-ttu-id="47e04-121">[确定要在 CDN 上托管的静态资产](use-office-365-cdn-with-spo.md#CDNAssets)。</span><span class="sxs-lookup"><span data-stu-id="47e04-121">[Determine which static assets you want to host on the CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span></span>
  - <span data-ttu-id="47e04-122">[确定要存储资产的位置](use-office-365-cdn-with-spo.md#CDNStoreAssets)。</span><span class="sxs-lookup"><span data-stu-id="47e04-122">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span></span> <span data-ttu-id="47e04-123">此位置可以是 SharePoint 网站、库或文件夹, 也可以称为 "_源_"。</span><span class="sxs-lookup"><span data-stu-id="47e04-123">This location can be a SharePoint site, library or folder and is called an _origin_.</span></span>
  - <span data-ttu-id="47e04-124">[选择每个源应该是公共的还是私有](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)的。</span><span class="sxs-lookup"><span data-stu-id="47e04-124">[Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span> <span data-ttu-id="47e04-125">您可以添加公共类型和私有类型的多个源。</span><span class="sxs-lookup"><span data-stu-id="47e04-125">You can add multiple origins of both public and private types.</span></span>

- <span data-ttu-id="47e04-126">使用 PowerShell 或 SharePoint Online CLI 设置和配置 CDN</span><span class="sxs-lookup"><span data-stu-id="47e04-126">Set up and configure the CDN, using either PowerShell or the SharePoint Online CLI</span></span>

  - [<span data-ttu-id="47e04-127">使用 SharePoint Online 命令行管理程序设置和配置 CDN</span><span class="sxs-lookup"><span data-stu-id="47e04-127">Set up and configure the CDN by using the SharePoint Online Management Shell</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [<span data-ttu-id="47e04-128">使用 Office 365 CLI 设置和配置 CDN</span><span class="sxs-lookup"><span data-stu-id="47e04-128">Set up and configure the CDN by using the Office 365 CLI</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  <span data-ttu-id="47e04-129">完成此步骤后, 您将拥有:</span><span class="sxs-lookup"><span data-stu-id="47e04-129">When you complete this step, you will have:</span></span>

  - <span data-ttu-id="47e04-130">已为你的组织启用 CDN。</span><span class="sxs-lookup"><span data-stu-id="47e04-130">Enabled the CDN for your organization.</span></span>
  - <span data-ttu-id="47e04-131">添加了将每个源标识为公用或专用的来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-131">Added your origins, identifying each origin as public or private.</span></span>

<span data-ttu-id="47e04-132">完成设置后, 可以通过以下方式[管理 Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage)一段时间:</span><span class="sxs-lookup"><span data-stu-id="47e04-132">Once you're done with setup, you can [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span>
  
- <span data-ttu-id="47e04-133">添加、更新和删除资产</span><span class="sxs-lookup"><span data-stu-id="47e04-133">Adding, updating, and removing assets</span></span>
- <span data-ttu-id="47e04-134">添加和删除源</span><span class="sxs-lookup"><span data-stu-id="47e04-134">Adding and removing origins</span></span>
- <span data-ttu-id="47e04-135">配置 CDN 策略</span><span class="sxs-lookup"><span data-stu-id="47e04-135">Configuring CDN policies</span></span>
- <span data-ttu-id="47e04-136">如有必要, 禁用 CDN</span><span class="sxs-lookup"><span data-stu-id="47e04-136">If necessary, disabling the CDN</span></span>

<span data-ttu-id="47e04-137">最后, 请参阅[使用 cdn 资产](use-office-365-cdn-with-spo.md#using-your-cdn-assets)了解如何从公共来源和专用来源访问 cdn 资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-137">Finally, see [Using your CDN assets](use-office-365-cdn-with-spo.md#using-your-cdn-assets) to learn about accessing your CDN assets from both public and private origins.</span></span>

<span data-ttu-id="47e04-138">有关解决常见问题的指南, 请参阅[Office 365 CDN 故障排除](use-office-365-cdn-with-spo.md#CDNTroubleshooting)。</span><span class="sxs-lookup"><span data-stu-id="47e04-138">See [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) for guidance on resolving common issues.</span></span>

## <a name="plan-for-deployment-of-the-office-365-cdn"></a><span data-ttu-id="47e04-139">规划 Office 365 CDN 的部署</span><span class="sxs-lookup"><span data-stu-id="47e04-139">Plan for deployment of the Office 365 CDN</span></span>

<span data-ttu-id="47e04-140">在部署 Office 365 租户的 Office 365 CDN 之前, 应考虑以下因素作为规划过程的一部分。</span><span class="sxs-lookup"><span data-stu-id="47e04-140">Before you deploy the Office 365 CDN for your Office 365 tenant, you should consider the following factors as part of your planning process.</span></span>

  - [<span data-ttu-id="47e04-141">确定要在 CDN 上托管的静态资产</span><span class="sxs-lookup"><span data-stu-id="47e04-141">Determine which static assets you want to host on the CDN</span></span>](use-office-365-cdn-with-spo.md#CDNAssets)
  - [<span data-ttu-id="47e04-142">确定要存储资产的位置</span><span class="sxs-lookup"><span data-stu-id="47e04-142">Determine where you want to store your assets</span></span>](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - [<span data-ttu-id="47e04-143">选择每个来源是公共还是私有</span><span class="sxs-lookup"><span data-stu-id="47e04-143">Choose whether each origin should be public or private</span></span>](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a><span data-ttu-id="47e04-144">确定要在 CDN 上托管的静态资产</span><span class="sxs-lookup"><span data-stu-id="47e04-144">Determine which static assets you want to host on the CDN</span></span>
<span data-ttu-id="47e04-145"><a name="CDNAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-145"></span></span>

<span data-ttu-id="47e04-146">通常情况下, Cdn 在承载_静态资产_或不经常更改的资产时最为有效。</span><span class="sxs-lookup"><span data-stu-id="47e04-146">In general, CDNs are most effective for hosting _static assets_, or assets that don't change very often.</span></span> <span data-ttu-id="47e04-147">最好的经验法则是确定满足部分或所有条件的文件:</span><span class="sxs-lookup"><span data-stu-id="47e04-147">A good rule of thumb is to identify files that meet some or all of these conditions:</span></span>

- <span data-ttu-id="47e04-148">嵌入在页面中的静态文件 (如脚本和图像) 可能会对页面加载时间产生重大的增量影响</span><span class="sxs-lookup"><span data-stu-id="47e04-148">Static files embedded in a page (like scripts and images) that may have a significant incremental impact on page load times</span></span>
- <span data-ttu-id="47e04-149">可执行文件和安装文件等大型文件</span><span class="sxs-lookup"><span data-stu-id="47e04-149">Large files like executables and installation files</span></span>
- <span data-ttu-id="47e04-150">流式媒体文件</span><span class="sxs-lookup"><span data-stu-id="47e04-150">Streaming media files</span></span>
- <span data-ttu-id="47e04-151">支持客户端代码的资源库</span><span class="sxs-lookup"><span data-stu-id="47e04-151">Resource libraries that support client-side code</span></span>

<span data-ttu-id="47e04-152">例如, 在将 SharePoint Online 网站添加到 CDN 源时, 重复请求的小型文件 (如网站图像和脚本) 可以显著改进网站呈现性能, 并在您的 SharePoint Online 网站上以增量方式减少负载。</span><span class="sxs-lookup"><span data-stu-id="47e04-152">For example, small files that are repeatedly requested like site images and scripts can significantly improve site rendering performance and incrementally reduce the load on your SharePoint Online sites when you add them to a CDN origin.</span></span> <span data-ttu-id="47e04-153">可以从 CDN 下载或流式处理更大的文件 (如安装可执行文件或视频文件), 从而对 SharePoint Online 网站上的负载进行积极的性能影响和后续缩减, 即使不经常访问这些文件也是如此。</span><span class="sxs-lookup"><span data-stu-id="47e04-153">Larger files such as installation executables or video files can be downloaded or streamed from the CDN, delivering a positive performance impact and subsequent reduction of the load on your SharePoint Online site, even if they are not accessed as often.</span></span>

<span data-ttu-id="47e04-154">每个文件的性能改进取决于许多因素, 包括客户端离最近的 CDN 终结点、本地网络中的暂时条件等等。</span><span class="sxs-lookup"><span data-stu-id="47e04-154">Performance improvement on a per-file basis is dependent on many factors, including the client's proximity to the nearest CDN endpoint, transient conditions on the local network, and so forth.</span></span> <span data-ttu-id="47e04-155">许多静态文件非常小, 可以从 Office 365 下载, 不应超过一秒钟。</span><span class="sxs-lookup"><span data-stu-id="47e04-155">Many static files are quite small, and can be downloaded from Office 365 in less than a second.</span></span> <span data-ttu-id="47e04-156">但是, 网页可能包含多个嵌入文件, 累积下载时间为几秒。</span><span class="sxs-lookup"><span data-stu-id="47e04-156">However, a web page may contain many embedded files with a cumulative download time of several seconds.</span></span> <span data-ttu-id="47e04-157">从 CDN 提供这些文件可显著缩短总页面加载时间。</span><span class="sxs-lookup"><span data-stu-id="47e04-157">Serving these files from the CDN can significantly reduce the overall page load time.</span></span> <span data-ttu-id="47e04-158">请参阅[CDN 提供了哪些性能增益？](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)示例。</span><span class="sxs-lookup"><span data-stu-id="47e04-158">See [What performance gains does a CDN provide?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) for an example.</span></span>

### <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="47e04-159">确定要存储资产的位置</span><span class="sxs-lookup"><span data-stu-id="47e04-159">Determine where you want to store your assets</span></span>
<span data-ttu-id="47e04-160"><a name="CDNStoreAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-160"></span></span>

<span data-ttu-id="47e04-161">CDN 从称为 "_来源_" 的位置提取资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-161">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="47e04-162">来源可以是可通过 URL 访问的 SharePoint 网站、文档库或文件夹。</span><span class="sxs-lookup"><span data-stu-id="47e04-162">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span> <span data-ttu-id="47e04-163">为您的组织指定源时具有极大的灵活性。</span><span class="sxs-lookup"><span data-stu-id="47e04-163">You have great flexibility when you specify origins for your organization.</span></span> <span data-ttu-id="47e04-164">例如, 您可以指定多个来源或要放置所有 CDN 资产的单个原点。</span><span class="sxs-lookup"><span data-stu-id="47e04-164">For example, you can specify multiple origins or a single origin where you want to put all your CDN assets.</span></span> <span data-ttu-id="47e04-165">您可以选择同时为您的组织提供公共来源或专用来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-165">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="47e04-166">大多数组织将选择实现这两个的组合。</span><span class="sxs-lookup"><span data-stu-id="47e04-166">Most organizations will choose to implement a combination of the two.</span></span>

<span data-ttu-id="47e04-167">您可以为您的起源 (如文件夹或文档库) 创建新的容器, 并添加要从 CDN 中获取的文件。</span><span class="sxs-lookup"><span data-stu-id="47e04-167">You can create new container for your origins such as folders or document libraries, and add files you want to make available from the CDN.</span></span> <span data-ttu-id="47e04-168">如果要从 CDN 中获取一组特定的资产, 并且希望仅将一组 CDN 资产限制为容器中的那些文件, 这是一种很棒的方法。</span><span class="sxs-lookup"><span data-stu-id="47e04-168">This is a good approach if you have a specific set of assets you want to be available from the CDN, and want to restrict the set of CDN assets to only those files in the container.</span></span>

<span data-ttu-id="47e04-169">您还可以将现有网站集、网站、库或文件夹配置为源, 这将使容器中的所有符合条件的资产都可从 CDN 中获取。</span><span class="sxs-lookup"><span data-stu-id="47e04-169">You can also configure an existing site collection, site, library or folder as an origin, which will make all eligible assets in the container available from the CDN.</span></span> <span data-ttu-id="47e04-170">在将现有容器添加为源之前, 请务必确保您了解其内容和权限, 以便不会无意中将资产暴露给匿名访问或未经授权的用户。</span><span class="sxs-lookup"><span data-stu-id="47e04-170">Before you add an existing container as an origin, it's important to make sure you are aware of its contents and permissions so you do not inadvertently expose assets to anonymous access or unauthorized users.</span></span>

<span data-ttu-id="47e04-171">您可以定义_cdn 策略_以从 CDN 中排除来源的内容。</span><span class="sxs-lookup"><span data-stu-id="47e04-171">You can define _CDN policies_ to exclude content in your origins from the CDN.</span></span> <span data-ttu-id="47e04-172">CDN 策略通过属性 (如_文件类型_和_网站分类_) 排除公用或专用来源的资产, 并将其应用于您在策略中指定的 CdnType (private 或 public) 的所有来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-172">CDN policies exclude assets in public or private origins by attributes such as _file type_ and _site classification_, and are applied to all origins of the CdnType (private or public) you specify in the policy.</span></span> <span data-ttu-id="47e04-173">例如, 如果添加了包含多个子网站的网站的专用源, 则可以定义一个策略以排除标记为**机密**的网站, 以便不会从 CDN 为应用了该分类的网站提供内容。</span><span class="sxs-lookup"><span data-stu-id="47e04-173">For example, if you add a private origin consisting of a site that contains multiple subsites, you can define a policy to exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span> <span data-ttu-id="47e04-174">该策略将应用于已添加到 CDN 的_所有_私人来源的内容。</span><span class="sxs-lookup"><span data-stu-id="47e04-174">The policy will apply to content from _all_ private origins you have added to the CDN.</span></span>
  
<span data-ttu-id="47e04-175">请注意, 源数量越多, 对 CDN 服务处理请求的时间会产生更大的影响。</span><span class="sxs-lookup"><span data-stu-id="47e04-175">Keep in mind that the greater the number of origins, the greater the impact on the time it takes the CDN service to process requests.</span></span> <span data-ttu-id="47e04-176">建议尽可能多地限制源的数量。</span><span class="sxs-lookup"><span data-stu-id="47e04-176">We recommend that you limit the number of origins as much as possible.</span></span>
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="47e04-177">选择每个来源是公共还是私有</span><span class="sxs-lookup"><span data-stu-id="47e04-177">Choose whether each origin should be public or private</span></span>
<span data-ttu-id="47e04-178"><a name="CDNOriginChoosePublicPrivate"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-178"></span></span>

<span data-ttu-id="47e04-179">在标识原点时, 指定是应将其设为_公共_的还是_私有_的。</span><span class="sxs-lookup"><span data-stu-id="47e04-179">When you identify an origin, you specify whether it should be made _public_ or _private_.</span></span> <span data-ttu-id="47e04-180">对公共起源中的 CDN 资产的访问权限是匿名的, 并且专用来源的 CDN 内容通过动态生成的令牌进行保护以实现更高的安全性。</span><span class="sxs-lookup"><span data-stu-id="47e04-180">Access to CDN assets in public origins is anonymous, and CDN content in private origins is secured by dynamically generated tokens for greater security.</span></span> <span data-ttu-id="47e04-181">无论您选择哪个选项, 当涉及 CDN 本身的管理时, Microsoft 都会为你执行所有繁重的操作。</span><span class="sxs-lookup"><span data-stu-id="47e04-181">Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself.</span></span> <span data-ttu-id="47e04-182">此外, 您还可以在设置完 CDN 并确定来源之后, 再改变主意。</span><span class="sxs-lookup"><span data-stu-id="47e04-182">Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>

<span data-ttu-id="47e04-183">公用和专用选项都提供了类似的性能提升, 但各自具有独特的特性和优势。</span><span class="sxs-lookup"><span data-stu-id="47e04-183">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span>

<span data-ttu-id="47e04-184">可以以匿名方式访问 Office 365 CDN 内的**公共**来源, 拥有该资产的 URL 的任何人都可以访问托管资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-184">**Public** origins within the Office 365 CDN are accessible anonymously, and hosted assets can be accessed by anyone who has the URL to the asset.</span></span> <span data-ttu-id="47e04-185">由于对公共源中内容的访问属于匿名访问，因此只能使用它们缓存非敏感的常规内容，如 javascript 文件、脚本、图标和图片。</span><span class="sxs-lookup"><span data-stu-id="47e04-185">Because access to content in public origins is anonymous, you should only use them to cache non-sensitive generic content such as javascript files, scripts, icons and images.</span></span>

<span data-ttu-id="47e04-186">Office 365 CDN 内的**私有**源提供对用户内容的专用访问权限，这些内容包括 SharePoint Online 文档库、站点和媒体（如视频）。</span><span class="sxs-lookup"><span data-stu-id="47e04-186">**Private** origins within the Office 365 CDN provide private access to user content such as SharePoint Online document libraries, sites and media such as videos.</span></span> <span data-ttu-id="47e04-187">对私人来源中的内容的访问受动态生成的令牌的保护, 因此只能由对原始文档库或存储位置具有权限的用户访问。</span><span class="sxs-lookup"><span data-stu-id="47e04-187">Access to content in private origins is secured by dynamically generated tokens so it can only be accessed by users with permissions to the original document library or storage location.</span></span> <span data-ttu-id="47e04-188">Office 365 CDN 中的专用来源仅可用于 SharePoint Online 内容, 并且您只能通过重定向从 SharePoint Online 租户访问私人来源的资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-188">Private origins in the Office 365 CDN can only be used for SharePoint Online content, and you can only access assets in private origins through redirection from your SharePoint Online tenant.</span></span>

<span data-ttu-id="47e04-189">您可以详细了解如何在专用来源中[使用资产](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)的 CDN 访问在专用资源中的工作方式。</span><span class="sxs-lookup"><span data-stu-id="47e04-189">You can read more about how CDN access to assets in a private origin works in [Using assets in private origins](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a><span data-ttu-id="47e04-190">托管资产在公共起源中的特性和优势</span><span class="sxs-lookup"><span data-stu-id="47e04-190">Attributes and advantages of hosting assets in public origins</span></span>
  
- <span data-ttu-id="47e04-191">每个人都能匿名访问公用源中公开的资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-191">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="47e04-192">永远不应将包含用户信息或被视为对您的组织敏感的资源置于公共来源中。</span><span class="sxs-lookup"><span data-stu-id="47e04-192">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>
- <span data-ttu-id="47e04-193">如果从公用源中删除某资产，缓存会继续保留此资产最多 30 天；但此 CDN 资产的链接会在 15 分钟内失效。</span><span class="sxs-lookup"><span data-stu-id="47e04-193">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
- <span data-ttu-id="47e04-194">如果将样式表（CSS 文件）托管到公用源，可以在代码内使用相对路径和 URI。</span><span class="sxs-lookup"><span data-stu-id="47e04-194">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code.</span></span> <span data-ttu-id="47e04-195">也就是说，可以引用背景图像和其他对象相对于调用它的资产的位置。</span><span class="sxs-lookup"><span data-stu-id="47e04-195">This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
- <span data-ttu-id="47e04-196">虽然可以硬编码公用源的 URL，但并不建议这样做。</span><span class="sxs-lookup"><span data-stu-id="47e04-196">While you can hard code a public origin's URL, doing so is not recommended.</span></span> <span data-ttu-id="47e04-197">这是因为，如果无法访问 CDN，URL 就不会在 SharePoint Online 中自动解析为相应组织，进而可能会导致链接失效和其他错误抛出。</span><span class="sxs-lookup"><span data-stu-id="47e04-197">The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
- <span data-ttu-id="47e04-198">默认情况下，支持向公用源添加下列类型的文件：.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf 和 .woff。</span><span class="sxs-lookup"><span data-stu-id="47e04-198">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff.</span></span> <span data-ttu-id="47e04-199">您可以指定其他文件类型。</span><span class="sxs-lookup"><span data-stu-id="47e04-199">You can specify additional file types.</span></span>
- <span data-ttu-id="47e04-200">您可以配置策略以排除已由指定的网站分类标识的资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-200">You can configure a policy to exclude assets that have been identified by site classifications that you specify.</span></span> <span data-ttu-id="47e04-201">例如，可以选择排除所有标记为“机密”或“受限”的资产，即使它们的文件类型受支持且位于公用源中，也不例外。</span><span class="sxs-lookup"><span data-stu-id="47e04-201">For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a><span data-ttu-id="47e04-202">托管资产在专用来源中的属性和优点</span><span class="sxs-lookup"><span data-stu-id="47e04-202">Attributes and advantages of hosting assets in private origins</span></span>

- <span data-ttu-id="47e04-203">专用来源仅可用于 SharePoint Online 资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-203">Private origins can only be used for SharePoint Online assets.</span></span>
- <span data-ttu-id="47e04-204">如果用户具有访问容器的权限, 则用户只能从私有来源访问资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-204">Users can only access the assets from a private origin if they have permissions to access the container.</span></span> <span data-ttu-id="47e04-205">禁止匿名访问这些资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-205">Anonymous access to these assets is prevented.</span></span>
- <span data-ttu-id="47e04-206">私人来源中的资产必须从 SharePoint Online 租户中引用。</span><span class="sxs-lookup"><span data-stu-id="47e04-206">Assets in private origins must be referred from the SharePoint Online tenant.</span></span> <span data-ttu-id="47e04-207">对专用 CDN 资产的直接访问不起作用。</span><span class="sxs-lookup"><span data-stu-id="47e04-207">Direct access to private CDN assets does not work.</span></span>
- <span data-ttu-id="47e04-208">如果从专用来源中删除资产, 该资产可能会从缓存中持续到一小时的可用状态;但是, 在资产删除的15分钟内, 我们将使 CDN 中的资产链接无效。</span><span class="sxs-lookup"><span data-stu-id="47e04-208">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes of the asset's removal.</span></span>
- <span data-ttu-id="47e04-209">默认情况下，支持为专用源添加下列类型的文件：.gif、.ico、.jpeg、.jpg、.js 和 .png。</span><span class="sxs-lookup"><span data-stu-id="47e04-209">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png.</span></span> <span data-ttu-id="47e04-210">您可以指定其他文件类型。</span><span class="sxs-lookup"><span data-stu-id="47e04-210">You can specify additional file types.</span></span>
- <span data-ttu-id="47e04-211">与公共起源一样, 您可以将策略配置为排除已由您指定的网站分类标识的资产, 即使您使用通配符来包含文件夹或文档库中的所有资产也是如此。</span><span class="sxs-lookup"><span data-stu-id="47e04-211">Just like with public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or document library.</span></span>

<span data-ttu-id="47e04-212">有关使用 Office 365 CDN 的原因的详细信息, 请参阅常规 CDN 概念和可与 Office 365 租户一起使用的其他 Microsoft Cdn。请参阅[Content 传递网络](content-delivery-networks.md)。</span><span class="sxs-lookup"><span data-stu-id="47e04-212">For more information about why to use the Office 365 CDN, general CDN concepts, and other Microsoft CDNs you can use with your Office 365 tenant, see [Content Delivery Networks](content-delivery-networks.md).</span></span>

### <a name="default-cdn-origins"></a><span data-ttu-id="47e04-213">默认 CDN 来源</span><span class="sxs-lookup"><span data-stu-id="47e04-213">Default CDN origins</span></span>

<span data-ttu-id="47e04-214">除非另行指定, 否则 Office 365 会在您启用 Office 365 CDN 时为您设置一些默认来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-214">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN.</span></span> <span data-ttu-id="47e04-215">如果最初选择不设置它们, 则可以在完成安装后添加这些来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-215">If you initially opt not to provision them, you can add these origins after you complete setup.</span></span> <span data-ttu-id="47e04-216">除非您了解跳过默认来源设置并有特定原因需要执行此操作, 否则应允许在启用 CDN 时创建这些后果。</span><span class="sxs-lookup"><span data-stu-id="47e04-216">Unless you understand the consequences of skipping the setup of default origins and have a specific reason for doing so, you should allow them to be created when you enable the CDN.</span></span>
  
<span data-ttu-id="47e04-217">默认专用 CDN 来源:</span><span class="sxs-lookup"><span data-stu-id="47e04-217">Default private CDN origins:</span></span>
  
- <span data-ttu-id="47e04-218">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="47e04-218">\*/userphoto.aspx</span></span>
- <span data-ttu-id="47e04-219">\*/siteassets</span><span class="sxs-lookup"><span data-stu-id="47e04-219">\*/siteassets</span></span>

<span data-ttu-id="47e04-220">默认公共 CDN 来源:</span><span class="sxs-lookup"><span data-stu-id="47e04-220">Default public CDN origins:</span></span>
  
- <span data-ttu-id="47e04-221">\*/masterpage</span><span class="sxs-lookup"><span data-stu-id="47e04-221">\*/masterpage</span></span>
- <span data-ttu-id="47e04-222">\*/style 库</span><span class="sxs-lookup"><span data-stu-id="47e04-222">\*/style library</span></span>
- <span data-ttu-id="47e04-223">\*/clientsideassets</span><span class="sxs-lookup"><span data-stu-id="47e04-223">\*/clientsideassets</span></span>

> [!NOTE]
> <span data-ttu-id="47e04-224">_clientsideassets_是在12月2017的 OFFICE 365 CDN 服务中添加的默认公共来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-224">_clientsideassets_ is a default public origin that was added to the Office 365 CDN service in December 2017.</span></span> <span data-ttu-id="47e04-225">为使 CDN 中的 SharePoint 框架解决方案正常工作, 必须存在此来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-225">This origin must be present in order for SharePoint Framework solutions in the CDN to work.</span></span> <span data-ttu-id="47e04-226">如果在12月2017之前启用了 Office 365 CDN, 或者在启用 CDN 时跳过了默认来源的设置, 则可以手动添加此来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-226">If you enabled the Office 365 CDN prior to December 2017, or if you skipped setup of default origins when you enabled the CDN, you can manually add this origin.</span></span> <span data-ttu-id="47e04-227">有关详细信息, 请参阅[我的客户端 web 部件或 SharePoint 框架解决方案不起作用](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working)。</span><span class="sxs-lookup"><span data-stu-id="47e04-227">For more information, see [My client-side web part or SharePoint Framework solution isn't working](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="47e04-228">使用 SharePoint Online 命令行管理程序设置和配置 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="47e04-228">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>
<span data-ttu-id="47e04-229"><a name="CDNSetupinPShell"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-229"></span></span>

<span data-ttu-id="47e04-230">本节中的过程要求您使用 SharePoint Online 命令行管理程序连接到 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="47e04-230">The procedures in this section require you to use the SharePoint Online Management Shell to connect to SharePoint Online.</span></span> <span data-ttu-id="47e04-231">有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="47e04-231">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="47e04-232">完成这些步骤, 在 sharepoint online 中使用 SharePoint Online 命令行管理程序设置和配置 CDN 以托管你的资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-232">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the SharePoint Online Management Shell.</span></span>
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="47e04-233">使你的组织能够使用 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="47e04-233">Enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="47e04-234">在对租户 CDN 设置进行更改之前, 应在 Office 365 租户中检索专用 CDN 配置的当前状态。</span><span class="sxs-lookup"><span data-stu-id="47e04-234">Before you make changes to the tenant CDN settings, you should retrieve the current status of the private CDN configuration in your Office 365 tenant.</span></span> <span data-ttu-id="47e04-235">使用 SharePoint Online 命令行管理程序连接到你的租户:</span><span class="sxs-lookup"><span data-stu-id="47e04-235">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

<span data-ttu-id="47e04-236">现在, 使用**SPOTenantCdnEnabled** cmdlet 检索租户中的 CDN 状态设置:</span><span class="sxs-lookup"><span data-stu-id="47e04-236">Now use the **Get-SPOTenantCdnEnabled** cmdlet to retrieve the CDN status settings from the tenant:</span></span>

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

<span data-ttu-id="47e04-237">指定 CdnType 的 CDN 状态将输出到屏幕上。</span><span class="sxs-lookup"><span data-stu-id="47e04-237">The status of the CDN for the specified CdnType will output to the screen.</span></span>

<span data-ttu-id="47e04-238">使用**SPOTenantCdnEnabled** cmdlet 可使您的组织使用 OFFICE 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="47e04-238">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN.</span></span> <span data-ttu-id="47e04-239">您可以让您的组织同时使用公用来源、私人来源或同时使用这两者。</span><span class="sxs-lookup"><span data-stu-id="47e04-239">You can enable your organization to use public origins, private origins, or both at once.</span></span> <span data-ttu-id="47e04-240">您还可以将 CDN 配置为在启用时跳过默认来源的设置。</span><span class="sxs-lookup"><span data-stu-id="47e04-240">You can also configure the CDN to skip the setup of default origins when you enable it.</span></span> <span data-ttu-id="47e04-241">您随时可以按照本主题中所述, 在以后添加这些来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-241">You can always add these origins later as described in this topic.</span></span>
  
<span data-ttu-id="47e04-242">在 Windows Powershell for SharePoint Online 中:</span><span class="sxs-lookup"><span data-stu-id="47e04-242">In Windows Powershell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="47e04-243">例如, 若要使组织能够使用公共来源和专用来源, 请键入以下命令:</span><span class="sxs-lookup"><span data-stu-id="47e04-243">For example, to enable your organization to use both public and private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="47e04-244">若要使组织能够使用公共来源和专用来源, 但跳过设置默认来源, 请键入以下命令:</span><span class="sxs-lookup"><span data-stu-id="47e04-244">To enable your organization to use both public and private origins but skip setting up the default origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="47e04-245">有关在启用 Office 365 CDN 时默认设置的来源的信息以及跳过默认来源设置的潜在影响, 请参阅[默认 CDN 来源](use-office-365-cdn-with-spo.md#default-cdn-origins)。</span><span class="sxs-lookup"><span data-stu-id="47e04-245">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.</span></span>

<span data-ttu-id="47e04-246">若要使组织能够使用公共来源, 请键入以下命令:</span><span class="sxs-lookup"><span data-stu-id="47e04-246">To enable your organization to use public origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="47e04-247">若要使您的组织使用专用来源, 请键入以下命令:</span><span class="sxs-lookup"><span data-stu-id="47e04-247">To enable your organization to use private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="47e04-248">有关此 cmdlet 的详细信息, 请参阅[SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)。</span><span class="sxs-lookup"><span data-stu-id="47e04-248">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a><span data-ttu-id="47e04-249">更改要包含在 Office 365 CDN 中的文件类型列表 (可选)</span><span class="sxs-lookup"><span data-stu-id="47e04-249">Change the list of file types to include in the Office 365 CDN (Optional)</span></span>
<span data-ttu-id="47e04-250"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-250"></span></span>

> [!TIP]
> <span data-ttu-id="47e04-251">使用**运行 set-spotenantcdnpolicy** cmdlet 定义文件类型时, 将覆盖当前定义的列表。</span><span class="sxs-lookup"><span data-stu-id="47e04-251">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="47e04-252">如果要向列表中添加其他文件类型, 请先使用 cmdlet 找出已允许的文件类型, 并将它们包含在列表中以及新的文件类型。</span><span class="sxs-lookup"><span data-stu-id="47e04-252">If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span>
  
<span data-ttu-id="47e04-253">使用**运行 set-spotenantcdnpolicy** cmdlet 可以定义可由 CDN 中的公共和专用来源承载的静态文件类型。</span><span class="sxs-lookup"><span data-stu-id="47e04-253">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN.</span></span> <span data-ttu-id="47e04-254">默认情况下, 允许使用常见资产类型, 例如 .css、.gif、.jpg 和 .js。</span><span class="sxs-lookup"><span data-stu-id="47e04-254">By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span>

<span data-ttu-id="47e04-255">在 Windows PowerShell for SharePoint Online 中:</span><span class="sxs-lookup"><span data-stu-id="47e04-255">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="47e04-256">例如, 若要启用 CDN 以承载 .css 和 .png 文件, 您需要输入以下命令:</span><span class="sxs-lookup"><span data-stu-id="47e04-256">For example, to enable the CDN to host .css and .png files, you would enter the command:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

<span data-ttu-id="47e04-257">若要查看 CDN 当前允许的文件类型, 请使用**请运行 get-spotenantcdnpolicies** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="47e04-257">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="47e04-258">有关这些 cmdlet 的详细信息, 请参阅[运行 set-spotenantcdnpolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)和[请运行 get-spotenantcdnpolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)。</span><span class="sxs-lookup"><span data-stu-id="47e04-258">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a><span data-ttu-id="47e04-259">更改要从 Office 365 CDN 中排除的网站分类列表 (可选)</span><span class="sxs-lookup"><span data-stu-id="47e04-259">Change the list of site classifications you want to exclude from the Office 365 CDN (Optional)</span></span>
<span data-ttu-id="47e04-260"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-260"></span></span>

> [!TIP]
> <span data-ttu-id="47e04-261">当您使用**运行 set-spotenantcdnpolicy** cmdlet 排除网站分类时, 将覆盖当前定义的列表。</span><span class="sxs-lookup"><span data-stu-id="47e04-261">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="47e04-262">如果要排除其他网站分类, 请先使用 cmdlet 找出已排除的分类, 然后将其添加到新的分类中。</span><span class="sxs-lookup"><span data-stu-id="47e04-262">If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span>

<span data-ttu-id="47e04-263">运行 **Set-SPOTenantCdnPolicy** cmdlet 可以排除不想通过 CDN 提供的网站分类。</span><span class="sxs-lookup"><span data-stu-id="47e04-263">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="47e04-264">默认情况下，不排除任何网站分类。</span><span class="sxs-lookup"><span data-stu-id="47e04-264">By default, no site classifications are excluded.</span></span>

<span data-ttu-id="47e04-265">在 Windows PowerShell for SharePoint Online 中:</span><span class="sxs-lookup"><span data-stu-id="47e04-265">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="47e04-266">若要查看当前受限制的网站分类, 请使用**请运行 get-spotenantcdnpolicies** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="47e04-266">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="47e04-267">将返回的属性为_IncludeFileExtensions_、 _ExcludeRestrictedSiteClassifications_和_ExcludeIfNoScriptDisabled_。</span><span class="sxs-lookup"><span data-stu-id="47e04-267">The properties that will be returned are _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ and _ExcludeIfNoScriptDisabled_.</span></span>

<span data-ttu-id="47e04-268">_IncludeFileExtensions_属性包含将从 CDN 提供服务的文件扩展名的列表。</span><span class="sxs-lookup"><span data-stu-id="47e04-268">The _IncludeFileExtensions_ property contains the list of file extensions that will be served from the CDN.</span></span>

> [!NOTE]
> <span data-ttu-id="47e04-269">公用和专用的默认文件扩展名是不同的。</span><span class="sxs-lookup"><span data-stu-id="47e04-269">The default file extensions are different between public and private.</span></span>

<span data-ttu-id="47e04-270">_ExcludeRestrictedSiteClassifications_属性包含要从 CDN 中排除的网站分类。</span><span class="sxs-lookup"><span data-stu-id="47e04-270">The _ExcludeRestrictedSiteClassifications_ property contains the site classifications that you want to exclude from the CDN.</span></span> <span data-ttu-id="47e04-271">例如, 您可以排除标记为**机密**的网站, 以便不会从 CDN 为应用了该分类的网站中的内容提供服务。</span><span class="sxs-lookup"><span data-stu-id="47e04-271">For example, you can exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span>

<span data-ttu-id="47e04-272">_ExcludeIfNoScriptDisabled_属性基于网站级_NoScript_属性设置从 CDN 中排除内容。</span><span class="sxs-lookup"><span data-stu-id="47e04-272">The _ExcludeIfNoScriptDisabled_ property excludes content from the CDN based on the site-level _NoScript_ attribute settings.</span></span> <span data-ttu-id="47e04-273">默认情况下, _NoScript_属性设置为 "为_新式_网站**启用**", 并对_经典_网站**禁用**。</span><span class="sxs-lookup"><span data-stu-id="47e04-273">By default, the _NoScript_ attribute is set to **Enabled** for _Modern_ sites and **Disabled** for _Classic_ sites.</span></span> <span data-ttu-id="47e04-274">这取决于租户设置。</span><span class="sxs-lookup"><span data-stu-id="47e04-274">This depends on your tenant settings.</span></span>

<span data-ttu-id="47e04-275">有关这些 cmdlet 的详细信息, 请参阅[运行 set-spotenantcdnpolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx)和[请运行 get-spotenantcdnpolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)。</span><span class="sxs-lookup"><span data-stu-id="47e04-275">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="add-an-origin-for-your-assets"></a><span data-ttu-id="47e04-276">为你的资产添加来源</span><span class="sxs-lookup"><span data-stu-id="47e04-276">Add an origin for your assets</span></span>
<span data-ttu-id="47e04-277"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-277"></span></span>

<span data-ttu-id="47e04-278">使用**SPOTenantCdnOrigin** cmdlet 可以定义原点。</span><span class="sxs-lookup"><span data-stu-id="47e04-278">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin.</span></span> <span data-ttu-id="47e04-279">可以定义多个源。</span><span class="sxs-lookup"><span data-stu-id="47e04-279">You can define multiple origins.</span></span> <span data-ttu-id="47e04-280">源是 SharePoint 库或文件夹的 URL，其中包含要由 CDN 托管的资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-280">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="47e04-281">永远不应将包含用户信息或被视为对您的组织敏感的资源置于公共来源中。</span><span class="sxs-lookup"><span data-stu-id="47e04-281">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

<span data-ttu-id="47e04-282">_Path_的值是包含这些资产的库或文件夹的相对路径。</span><span class="sxs-lookup"><span data-stu-id="47e04-282">The value of _path_ is the relative path to the library or folder that contains the assets.</span></span> <span data-ttu-id="47e04-283">除了相对路径之外，还可以使用通配符。</span><span class="sxs-lookup"><span data-stu-id="47e04-283">You can use wildcards in addition to relative paths.</span></span> <span data-ttu-id="47e04-284">来源支持附加到 URL 的通配符。</span><span class="sxs-lookup"><span data-stu-id="47e04-284">Origins support wildcards prepended to the URL.</span></span> <span data-ttu-id="47e04-285">这使您可以创建跨多个网站的来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-285">This allows you to create origins that span multiple sites.</span></span> <span data-ttu-id="47e04-286">例如, 若要将所有网站的 masterpages 文件夹中的所有资源作为 CDN 中的公共来源包括在内, 请键入以下命令:</span><span class="sxs-lookup"><span data-stu-id="47e04-286">For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- <span data-ttu-id="47e04-287">通配符修饰符 \***/** 仅可在路径的开头使用, 并将与指定 URL 下的所有 URL 段匹配。</span><span class="sxs-lookup"><span data-stu-id="47e04-287">The wildcard modifier \***/** can only be used at the beginning of the path, and will match all URL segments under the specified URL.</span></span>
- <span data-ttu-id="47e04-288">路径可以指向文档库、文件夹或网站。</span><span class="sxs-lookup"><span data-stu-id="47e04-288">The path can point to a document library, folder or site.</span></span> <span data-ttu-id="47e04-289">例如, 路径 _\*/site1_将与网站下的所有文档库相匹配。</span><span class="sxs-lookup"><span data-stu-id="47e04-289">For example, the path _\*/site1_ will match all the document libraries under the site.</span></span>

<span data-ttu-id="47e04-290">您可以添加具有特定相对路径的原点。</span><span class="sxs-lookup"><span data-stu-id="47e04-290">You can add an origin with a specific relative path.</span></span> <span data-ttu-id="47e04-291">您不能使用完整路径添加原点。</span><span class="sxs-lookup"><span data-stu-id="47e04-291">You cannot add an origin using the full path.</span></span>

<span data-ttu-id="47e04-292">本示例在特定网站上添加 siteassets 库的专用原点:</span><span class="sxs-lookup"><span data-stu-id="47e04-292">This example adds a private origin of the siteassets library on a specific site:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="47e04-293">本示例在网站集的 "网站资产" 库中添加 " _folder1_ " 文件夹的专用原点:</span><span class="sxs-lookup"><span data-stu-id="47e04-293">This example adds a private origin of the _folder1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl “/sites/test/siteassets/folder1”
```

<span data-ttu-id="47e04-294">有关此命令及其语法的详细信息, 请参阅[外接程序 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)。</span><span class="sxs-lookup"><span data-stu-id="47e04-294">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="47e04-295">在专用来源中, 从来源共享的资产必须先发布主要版本, 然后才能从 CDN 访问它们。</span><span class="sxs-lookup"><span data-stu-id="47e04-295">In private origins, assets being shared from an origin must have a major version published before they can be accessed from the CDN.</span></span>
  
<span data-ttu-id="47e04-296">运行命令后, 系统将同步整个数据中心的配置。</span><span class="sxs-lookup"><span data-stu-id="47e04-296">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="47e04-297">这最长可能需要15分钟。</span><span class="sxs-lookup"><span data-stu-id="47e04-297">This can take up to 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="47e04-298">示例: 为您的母版页和为 SharePoint Online 的样式库配置公共原点</span><span class="sxs-lookup"><span data-stu-id="47e04-298">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<span data-ttu-id="47e04-299"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-299"></span></span>

<span data-ttu-id="47e04-300">通常情况下, 当您启用 Office 365 CDN 时, 将为您设置这些来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-300">Normally, these origins are set up for you by default when you enable the Office 365 CDN.</span></span> <span data-ttu-id="47e04-301">但是, 如果要手动启用它们, 请按照以下步骤操作。</span><span class="sxs-lookup"><span data-stu-id="47e04-301">However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="47e04-302">使用**SPOTenantCdnOrigin** cmdlet 可将样式库定义为公共来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-302">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="47e04-303">使用**SPOTenantCdnOrigin** cmdlet 可将母版页定义为公共源。</span><span class="sxs-lookup"><span data-stu-id="47e04-303">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

<span data-ttu-id="47e04-304">有关此命令及其语法的详细信息, 请参阅[外接程序 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)。</span><span class="sxs-lookup"><span data-stu-id="47e04-304">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="47e04-305">运行命令后, 系统将同步整个数据中心的配置。</span><span class="sxs-lookup"><span data-stu-id="47e04-305">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="47e04-306">这最长可能需要15分钟。</span><span class="sxs-lookup"><span data-stu-id="47e04-306">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="47e04-307">示例: 为 SharePoint Online 的网站资产、网站页面和发布图像配置专用来源</span><span class="sxs-lookup"><span data-stu-id="47e04-307">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<span data-ttu-id="47e04-308"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-308"></span></span>

- <span data-ttu-id="47e04-309">使用**SPOTenantCdnOrigin** cmdlet 可以将 "网站资产" 文件夹定义为专用来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-309">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="47e04-310">使用**SPOTenantCdnOrigin** cmdlet 可将 "网站页面" 文件夹定义为专用来源。</span><span class="sxs-lookup"><span data-stu-id="47e04-310">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="47e04-311">使用**SPOTenantCdnOrigin** cmdlet 可以将发布映像文件夹定义为专用源。</span><span class="sxs-lookup"><span data-stu-id="47e04-311">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

<span data-ttu-id="47e04-312">有关此命令及其语法的详细信息, 请参阅[外接程序 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)。</span><span class="sxs-lookup"><span data-stu-id="47e04-312">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="47e04-313">运行命令后, 系统将同步整个数据中心的配置。</span><span class="sxs-lookup"><span data-stu-id="47e04-313">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="47e04-314">这最长可能需要15分钟。</span><span class="sxs-lookup"><span data-stu-id="47e04-314">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="47e04-315">示例: 为 SharePoint Online 的网站集配置专用来源</span><span class="sxs-lookup"><span data-stu-id="47e04-315">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<span data-ttu-id="47e04-316"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-316"></span></span>

<span data-ttu-id="47e04-317">使用**SPOTenantCdnOrigin** cmdlet 可将网站集定义为私有源。</span><span class="sxs-lookup"><span data-stu-id="47e04-317">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin.</span></span> <span data-ttu-id="47e04-318">例如：</span><span class="sxs-lookup"><span data-stu-id="47e04-318">For example:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="47e04-319">有关此命令及其语法的详细信息, 请参阅[外接程序 SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)。</span><span class="sxs-lookup"><span data-stu-id="47e04-319">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="47e04-320">运行命令后, 系统将同步整个数据中心的配置。</span><span class="sxs-lookup"><span data-stu-id="47e04-320">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="47e04-321">您可能会看到一个预期的_配置挂起_消息, 因为 SharePoint Online 租户连接到 CDN 服务。</span><span class="sxs-lookup"><span data-stu-id="47e04-321">You may see a _Configuration pending_ message which is expected as the SharePoint Online tenant connects to the CDN service.</span></span> <span data-ttu-id="47e04-322">这最长可能需要15分钟。</span><span class="sxs-lookup"><span data-stu-id="47e04-322">This can take up to 15 minutes.</span></span>

### <a name="manage-the-office-365-cdn"></a><span data-ttu-id="47e04-323">管理 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="47e04-323">Manage the Office 365 CDN</span></span>
<span data-ttu-id="47e04-324"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-324"></span></span>

<span data-ttu-id="47e04-325">设置 CDN 后, 您可以在更新内容或需要更改时对配置进行更改, 如本节中所述。</span><span class="sxs-lookup"><span data-stu-id="47e04-325">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="47e04-326">在 Office 365 CDN 中添加、更新或删除资产</span><span class="sxs-lookup"><span data-stu-id="47e04-326">Add, update, or remove assets from the Office 365 CDN</span></span>
<span data-ttu-id="47e04-327"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-327"></span></span>

<span data-ttu-id="47e04-328">完成设置步骤后, 可以在需要时添加新资产, 并更新或删除现有资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-328">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want.</span></span> <span data-ttu-id="47e04-329">只需对您标识为来源的文件夹或 SharePoint 库中的资产进行更改即可。</span><span class="sxs-lookup"><span data-stu-id="47e04-329">Just make your changes to the assets in the folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="47e04-330">如果添加新资产, 可立即通过 CDN 使用它。</span><span class="sxs-lookup"><span data-stu-id="47e04-330">If you add a new asset, it is available through the CDN immediately.</span></span> <span data-ttu-id="47e04-331">但是, 如果您更新资产, 最长需要15分钟才能在 CDN 中传播并变为可用的新副本。</span><span class="sxs-lookup"><span data-stu-id="47e04-331">However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="47e04-332">如果需要检索原点的位置, 则可以使用**运行 get-spotenantcdnorigins** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="47e04-332">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet.</span></span> <span data-ttu-id="47e04-333">有关如何使用此 cmdlet 的信息, 请参阅[运行 get-spotenantcdnorigins](https://technet.microsoft.com/en-us/library/mt790770.aspx)。</span><span class="sxs-lookup"><span data-stu-id="47e04-333">For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="47e04-334">从 Office 365 CDN 中删除源</span><span class="sxs-lookup"><span data-stu-id="47e04-334">Remove an origin from the Office 365 CDN</span></span>
<span data-ttu-id="47e04-335"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-335"></span></span>

<span data-ttu-id="47e04-336">您可以删除您标识为来源的文件夹或 SharePoint 库的访问权限。</span><span class="sxs-lookup"><span data-stu-id="47e04-336">You can remove access to a folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="47e04-337">为此, 请使用**SPOTenantCdnOrigin** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="47e04-337">To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet.</span></span>

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

<span data-ttu-id="47e04-338">有关如何使用此 cmdlet 的信息, 请参阅[SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx)。</span><span class="sxs-lookup"><span data-stu-id="47e04-338">For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="47e04-339">在 Office 365 CDN 中修改原点</span><span class="sxs-lookup"><span data-stu-id="47e04-339">Modify an origin in the Office 365 CDN</span></span>
<span data-ttu-id="47e04-340"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-340"></span></span>

<span data-ttu-id="47e04-341">您不能修改已创建的原点。</span><span class="sxs-lookup"><span data-stu-id="47e04-341">You cannot modify an origin you've created.</span></span> <span data-ttu-id="47e04-342">相反, 请删除该原点, 然后添加一个新的原点。</span><span class="sxs-lookup"><span data-stu-id="47e04-342">Instead, remove the origin and then add a new one.</span></span> <span data-ttu-id="47e04-343">有关详细信息, 请参阅[从 Office 365 CDN 中删除原点](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin)和[为资产添加来源](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)。</span><span class="sxs-lookup"><span data-stu-id="47e04-343">For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
#### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="47e04-344">禁用 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="47e04-344">Disable the Office 365 CDN</span></span>
<span data-ttu-id="47e04-345"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-345"></span></span>

<span data-ttu-id="47e04-346">使用**SPOTenantCdnEnabled** cmdlet 为您的组织禁用 CDN。</span><span class="sxs-lookup"><span data-stu-id="47e04-346">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization.</span></span> <span data-ttu-id="47e04-347">如果您同时启用了 CDN 的公共和专用来源, 则需要运行 cmdlet 两次, 如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="47e04-347">If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span>
  
<span data-ttu-id="47e04-348">若要禁用 CDN 中的公共来源, 请输入以下命令:</span><span class="sxs-lookup"><span data-stu-id="47e04-348">To disable use of public origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="47e04-349">若要禁用 CDN 中的专用来源的使用, 请输入以下命令:</span><span class="sxs-lookup"><span data-stu-id="47e04-349">To disable use of the private origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="47e04-350">有关此 cmdlet 的详细信息, 请参阅[SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)。</span><span class="sxs-lookup"><span data-stu-id="47e04-350">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a><span data-ttu-id="47e04-351">使用 Office 365 CLI 设置和配置 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="47e04-351">Set up and configure the Office 365 CDN using the Office 365 CLI</span></span>
<span data-ttu-id="47e04-352"><a name="CDNSetupinCLI"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-352"></span></span>

<span data-ttu-id="47e04-353">本节中的过程要求您已安装[Office 365 CLI](https://aka.ms/o365cli)。</span><span class="sxs-lookup"><span data-stu-id="47e04-353">The procedures in this section require that you have installed the [Office 365 CLI](https://aka.ms/o365cli).</span></span> <span data-ttu-id="47e04-354">接下来，运行 [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) 命令，连接到 SharePoint Online 租户。</span><span class="sxs-lookup"><span data-stu-id="47e04-354">Next, connect to your SharePoint Online tenant using the [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) command.</span></span>

<span data-ttu-id="47e04-355">完成这些步骤, 在 SharePoint Online 中使用 Office 365 CLI 设置和配置 CDN 以托管你的资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-355">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the Office 365 CLI.</span></span>

### <a name="enable-the-office-365-cdn"></a><span data-ttu-id="47e04-356">启用 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="47e04-356">Enable the Office 365 CDN</span></span>

<span data-ttu-id="47e04-357">可以运行 [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) 命令，在租户中管理 Office 365 CDN 的状态。</span><span class="sxs-lookup"><span data-stu-id="47e04-357">You can manage the state of the Office 365 CDN in your tenant using the [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) command.</span></span>

<span data-ttu-id="47e04-358">若要在租户中启用 Office 365 公用 CDN，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="47e04-358">To enable the Office 365 Public CDN in your tenant execute:</span></span>

```sh
spo cdn set --type Public --enabled true
```

<span data-ttu-id="47e04-359">若要启用 Office 365 SharePoint CDN, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="47e04-359">To enable the Office 365 SharePoint CDN, execute:</span></span>

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a><span data-ttu-id="47e04-360">查看 Office 365 CDN 的当前状态</span><span class="sxs-lookup"><span data-stu-id="47e04-360">View the current status of the Office 365 CDN</span></span>

<span data-ttu-id="47e04-361">若要检查是否已启用或禁用特定类型的 Office 365 CDN, 请使用[spo CDN get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/)命令。</span><span class="sxs-lookup"><span data-stu-id="47e04-361">To check if the particular type of Office 365 CDN is enabled or disabled, use the [spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) command.</span></span>

<span data-ttu-id="47e04-362">若要检查 Office 365 公用 CDN 是否已启用，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="47e04-362">To check if the Office 365 Public CDN is enabled, execute:</span></span>

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a><span data-ttu-id="47e04-363">查看 Office 365 CDN 来源</span><span class="sxs-lookup"><span data-stu-id="47e04-363">View the Office 365 CDN origins</span></span>

<span data-ttu-id="47e04-364">若要查看当前配置的 Office 365 公用 CDN 源，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="47e04-364">To view the currently configured Office 365 Public CDN origins execute:</span></span>

```sh
spo cdn origin list --type Public
```

<span data-ttu-id="47e04-365">有关启用 Office 365 CDN 时默认设置的来源的信息, 请参阅[默认 CDN 来源](use-office-365-cdn-with-spo.md#default-cdn-origins)。</span><span class="sxs-lookup"><span data-stu-id="47e04-365">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN.</span></span>

### <a name="add-an-office-365-cdn-origin"></a><span data-ttu-id="47e04-366">添加 Office 365 CDN 源</span><span class="sxs-lookup"><span data-stu-id="47e04-366">Add an Office 365 CDN origin</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47e04-367">永远不要在配置为公共来源的 SharePoint 文档库中将被视为对您的组织敏感的资源放置。</span><span class="sxs-lookup"><span data-stu-id="47e04-367">You should never place resources that are considered sensitive to your organization in a SharePoint document library configured as a public origin.</span></span>

<span data-ttu-id="47e04-368">运行 [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) 命令可以定义 CDN 源。</span><span class="sxs-lookup"><span data-stu-id="47e04-368">Use the [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) command to define a CDN origin.</span></span> <span data-ttu-id="47e04-369">可以定义多个源。</span><span class="sxs-lookup"><span data-stu-id="47e04-369">You can define multiple origins.</span></span> <span data-ttu-id="47e04-370">源是 SharePoint 库或文件夹的 URL，其中包含要由 CDN 托管的资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-370">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

<span data-ttu-id="47e04-371">其中`path` , 是包含资产的文件夹的相对路径。</span><span class="sxs-lookup"><span data-stu-id="47e04-371">Where `path` is the relative path to the folder that contains the assets.</span></span> <span data-ttu-id="47e04-372">除了相对路径之外，还可以使用通配符。</span><span class="sxs-lookup"><span data-stu-id="47e04-372">You can use wildcards in addition to relative paths.</span></span>

<span data-ttu-id="47e04-373">若要将所有网站的**母版页样式库**中的所有资产包含为公共来源, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="47e04-373">To include all assets in the **Master Page Gallery** of all sites as a public origin, execute:</span></span>

```sh
spo cdn origin add --type Public --origin */masterpage
```

<span data-ttu-id="47e04-374">若要配置特定网站集的专用源，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="47e04-374">To configure a private origin for a specific site collection, execute:</span></span>

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> <span data-ttu-id="47e04-375">添加 CDN 源后，最长可能需要 15 分钟，才能通过 CDN 服务检索文件。</span><span class="sxs-lookup"><span data-stu-id="47e04-375">After adding a CDN origin, it might take up to 15 minutes for you to be able to retrieve files via the CDN service.</span></span> <span data-ttu-id="47e04-376">可以运行 [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) 命令，验证特定源是否已启用。</span><span class="sxs-lookup"><span data-stu-id="47e04-376">You can verify if the particular origin has already been enabled using the [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command.</span></span>

### <a name="remove-an-office-365-cdn-origin"></a><span data-ttu-id="47e04-377">删除 Office 365 CDN 源</span><span class="sxs-lookup"><span data-stu-id="47e04-377">Remove an Office 365 CDN origin</span></span>

<span data-ttu-id="47e04-378">运行 [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) 命令可以删除指定类型 CDN 的 CDN 源。</span><span class="sxs-lookup"><span data-stu-id="47e04-378">Use the [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) command to remove a CDN origin for the specified CDN type.</span></span>

<span data-ttu-id="47e04-379">若要从 CDN 配置中删除公用源, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="47e04-379">To remove a public origin from the CDN configuration, execute:</span></span>

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> <span data-ttu-id="47e04-380">删除 CDN 源不会影响与该来源相匹配的任何文档库中存储的文件。</span><span class="sxs-lookup"><span data-stu-id="47e04-380">Removing a CDN origin doesn't affect the files stored in any document library matching that origin.</span></span> <span data-ttu-id="47e04-381">如果使用 SharePoint URL 引用这些资产, SharePoint 将自动切换回指向文档库的原始 URL。</span><span class="sxs-lookup"><span data-stu-id="47e04-381">If these assets have been referenced using their SharePoint URL, SharePoint will automatically switch back to the original URL pointing to the document library.</span></span> <span data-ttu-id="47e04-382">但是, 如果已使用公用 CDN URL 引用资产, 则删除该原点将断开链接, 您将需要手动更改它们。</span><span class="sxs-lookup"><span data-stu-id="47e04-382">If, however, assets have been referenced using a public CDN URL, then removing the origin will break the link and you will need to manually change them.</span></span>

### <a name="modify-an-office-365-cdn-origin"></a><span data-ttu-id="47e04-383">修改 Office 365 CDN 源</span><span class="sxs-lookup"><span data-stu-id="47e04-383">Modify an Office 365 CDN origin</span></span>

<span data-ttu-id="47e04-384">无法修改现有 CDN 源。</span><span class="sxs-lookup"><span data-stu-id="47e04-384">It's not possible to modify an existing CDN origin.</span></span> <span data-ttu-id="47e04-385">而应运行 `spo cdn origin remove` 命令删除以前定义的 CDN 源，并运行 `spo cdn origin add` 命令添加新源。</span><span class="sxs-lookup"><span data-stu-id="47e04-385">Instead, you should remove the previously defined CDN origin using the `spo cdn origin remove` command and add a new one using the `spo cdn origin add` command.</span></span>

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a><span data-ttu-id="47e04-386">更改要包含在 Office 365 CDN 中的文件类型</span><span class="sxs-lookup"><span data-stu-id="47e04-386">Change the types of files to include in the Office 365 CDN</span></span>

<span data-ttu-id="47e04-387">默认情况下，支持向 CDN 添加下列类型的文件：_.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf 和 .woff_。</span><span class="sxs-lookup"><span data-stu-id="47e04-387">By default, the following file types are included in the CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff_.</span></span> <span data-ttu-id="47e04-388">如果需要在 CDN 中添加其他类型的文件，可以运行 [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) 命令更改 CDN 配置。</span><span class="sxs-lookup"><span data-stu-id="47e04-388">If you need to include additional file types in the CDN, you can change the CDN configuration using the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command.</span></span>

> [!NOTE]
> <span data-ttu-id="47e04-389">如果更改文件类型列表，也就是覆盖当前定义的列表。</span><span class="sxs-lookup"><span data-stu-id="47e04-389">When changing the list of file types, you overwrite the currently defined list.</span></span> <span data-ttu-id="47e04-390">若要添加其他文件类型，请先运行 [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) 命令，确定当前配置的文件类型。</span><span class="sxs-lookup"><span data-stu-id="47e04-390">If you want to include additional file types, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command to find out which file types are currently configured.</span></span>

<span data-ttu-id="47e04-391">若要将_JSON_文件类型添加到公用 CDN 中包含的文件类型的默认列表中, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="47e04-391">To add the _JSON_ file type to the default list of file types included in the public CDN, execute:</span></span>

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="47e04-392">更改要从 Office 365 CDN 中排除的网站分类列表</span><span class="sxs-lookup"><span data-stu-id="47e04-392">Change the list of site classifications you want to exclude from the Office 365 CDN</span></span>

<span data-ttu-id="47e04-393">运行 [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) 命令可以排除不想通过 CDN 提供的网站分类。</span><span class="sxs-lookup"><span data-stu-id="47e04-393">Use the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="47e04-394">默认情况下，不排除任何网站分类。</span><span class="sxs-lookup"><span data-stu-id="47e04-394">By default, no site classifications are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="47e04-395">如果更改已排除的网站分类列表，也就是覆盖当前定义的列表。</span><span class="sxs-lookup"><span data-stu-id="47e04-395">When changing the list of excluded site classifications, you overwrite the currently defined list.</span></span> <span data-ttu-id="47e04-396">若要排除其他分类，请先运行 [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) 命令，确定当前配置的分类。</span><span class="sxs-lookup"><span data-stu-id="47e04-396">If you want to exclude additional classifications, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) command to find out which classifications are currently configured.</span></span>

<span data-ttu-id="47e04-397">若要从公用 CDN 中排除作为_HBI_分类的站点, 请执行</span><span class="sxs-lookup"><span data-stu-id="47e04-397">To exclude sites classified as _HBI_ from the public CDN, execute</span></span>

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="47e04-398">禁用 Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="47e04-398">Disable the Office 365 CDN</span></span>

<span data-ttu-id="47e04-399">若要禁用 Office 365 CDN，请运行 `spo cdn set` 命令。例如：</span><span class="sxs-lookup"><span data-stu-id="47e04-399">To disable the Office 365 CDN use the `spo cdn set` command, for example:</span></span>

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a><span data-ttu-id="47e04-400">使用 CDN 资产</span><span class="sxs-lookup"><span data-stu-id="47e04-400">Using your CDN assets</span></span>

<span data-ttu-id="47e04-401">现在, 您已启用 CDN 和已配置的来源和策略, 您可以开始使用 CDN 资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-401">Now that you have enabled the CDN and configured origins and policies, you can begin using your CDN assets.</span></span>

<span data-ttu-id="47e04-402">本部分将帮助您了解如何在 SharePoint 页面和内容中使用 CDN Url, 以便 SharePoint 将公用源和专用来源的资产的请求重定向到 CDN。</span><span class="sxs-lookup"><span data-stu-id="47e04-402">This section will help you understand how to use CDN URLs in your SharePoint pages and content so that SharePoint redirects requests for assets in both public and private origins to the CDN.</span></span>

- [<span data-ttu-id="47e04-403">更新与 CDN 资产的链接</span><span class="sxs-lookup"><span data-stu-id="47e04-403">Updating links to CDN assets</span></span>](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [<span data-ttu-id="47e04-404">在公共来源中使用资产</span><span class="sxs-lookup"><span data-stu-id="47e04-404">Using assets in public origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [<span data-ttu-id="47e04-405">在专用来源中使用资产</span><span class="sxs-lookup"><span data-stu-id="47e04-405">Using assets in private origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

<span data-ttu-id="47e04-406">有关如何使用 CDN 来承载客户端 web 部件的信息, 请参阅[从 Office 365 CDN 托管客户端 web 部件 (Hello World 第4部分)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)。</span><span class="sxs-lookup"><span data-stu-id="47e04-406">For information on how to use the CDN for hosting client-side web parts, see the topic [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span></span>

### <a name="updating-links-to-cdn-assets"></a><span data-ttu-id="47e04-407">更新与 CDN 资产的链接</span><span class="sxs-lookup"><span data-stu-id="47e04-407">Updating links to CDN assets</span></span>

<span data-ttu-id="47e04-408">若要使用已添加到源中的资产, 只需将指向原始文件的链接与原始文件的路径一起更新到原始文件。</span><span class="sxs-lookup"><span data-stu-id="47e04-408">To use assets that you have added to an origin, you simply update links to the original file with the path to the file in the origin.</span></span>

- <span data-ttu-id="47e04-409">编辑包含已添加到来源的资产链接的页面或内容。</span><span class="sxs-lookup"><span data-stu-id="47e04-409">Edit the page or content that contains links to assets you have added to an origin.</span></span> <span data-ttu-id="47e04-410">如果要更新指向给定资产的链接, 则可以使用以下几种方法之一在进入网站或网站集中进行全局搜索和替换链接。</span><span class="sxs-lookup"><span data-stu-id="47e04-410">You can also use one of several methods to globally search and replace links across an enter site or site collection if you want to update the link to a given asset everywhere it appears.</span></span>
- <span data-ttu-id="47e04-411">对于指向源中的资产的每个链接, 将路径替换为 CDN 源中的文件路径。</span><span class="sxs-lookup"><span data-stu-id="47e04-411">For each link to an asset in an origin, replace the path with the path to the file in the CDN origin.</span></span> <span data-ttu-id="47e04-412">您可以使用相对路径。</span><span class="sxs-lookup"><span data-stu-id="47e04-412">You can use relative paths.</span></span>
- <span data-ttu-id="47e04-413">保存页面或内容。</span><span class="sxs-lookup"><span data-stu-id="47e04-413">Save the page or content.</span></span>

<span data-ttu-id="47e04-414">例如, 请考虑已复制到文档库文件夹 _/site/CDN_origins/public/_ 的图像 _/site/SiteAssets/images/image.png_。</span><span class="sxs-lookup"><span data-stu-id="47e04-414">For example, consider the image _/site/SiteAssets/images/image.png_, which you have copied to the document library folder _/site/CDN_origins/public/_.</span></span> <span data-ttu-id="47e04-415">若要使用 CDN 资产, 请将原始路径替换为指向原始路径的图像文件位置, 以使新的 URL _/site/CDN_origins/public/image.png_。</span><span class="sxs-lookup"><span data-stu-id="47e04-415">To use the CDN asset, replace the original path to the image file location with the path to the origin to make the new URL _/site/CDN_origins/public/image.png_.</span></span>

<span data-ttu-id="47e04-416">如果要将完整 URL 用于资产而不是相对路径, 请按如下所示构造链接:</span><span class="sxs-lookup"><span data-stu-id="47e04-416">If you want to use the full URL to the asset instead of a relative path, construct the link like so:</span></span>

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> <span data-ttu-id="47e04-417">通常情况下, 不应直接将 Url 硬编码到 CDN 中的资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-417">In general, you should not hardcode URLs directly to assets in the CDN.</span></span> <span data-ttu-id="47e04-418">但是, 如果需要, 您可以在公用源中手动构造资产的 Url。</span><span class="sxs-lookup"><span data-stu-id="47e04-418">However, you can manually construct URLs for assets in public origins if needed.</span></span> <span data-ttu-id="47e04-419">有关详细信息, 请参阅[HARDCODING CDN url for 公共资产](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets)。</span><span class="sxs-lookup"><span data-stu-id="47e04-419">For more information, see [Hardcoding CDN URLs for public assets](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span></span>

<span data-ttu-id="47e04-420">若要了解如何验证资产是否通过 CDN 提供, 请参阅[如何确认资产是否受 cdn 的服务？](use-office-365-cdn-with-spo.md#CDNConfirm)在 " [Office 365 CDN 的疑难解答](use-office-365-cdn-with-spo.md#CDNTroubleshooting)" 部分中。</span><span class="sxs-lookup"><span data-stu-id="47e04-420">To learn about how to verify that assets are being served from the CDN, see [How do I confirm that assets are being served by the CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) in the [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) section.</span></span>

### <a name="using-assets-in-public-origins"></a><span data-ttu-id="47e04-421">在公共来源中使用资产</span><span class="sxs-lookup"><span data-stu-id="47e04-421">Using assets in public origins</span></span>

<span data-ttu-id="47e04-422">SharePoint Online 中的**发布功能**会自动将公共起源中存储的资产的 url 重写为其 CDN 等效项, 以便从 cdn 服务而不是 SharePoint 提供资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-422">The **Publishing feature** in SharePoint Online automatically rewrites URLs of assets stored in public origins to their CDN equivalents so that assets are served from the CDN service instead of SharePoint.</span></span>

<span data-ttu-id="47e04-423">如果您的源位于启用了 "发布" 功能的网站中, 并且您要向 CDN 中转移的资产属于以下类别之一, 则 SharePoint 将自动重写源中资产的 Url, 前提是该资产尚未被 CDN 排除 政策.</span><span class="sxs-lookup"><span data-stu-id="47e04-423">If your origin is in a site with the Publishing feature enabled, and the assets you want to offload to the CDN are in one of the following categories, SharePoint will automatically rewrite URLs for assets in the origin, provided that the asset has not been excluded by a CDN policy.</span></span>

<span data-ttu-id="47e04-424">下面概述了 SharePoint 发布功能自动重写的链接：</span><span class="sxs-lookup"><span data-stu-id="47e04-424">The following is an overview of which links are automatically rewritten by the SharePoint Publishing feature:</span></span>

- <span data-ttu-id="47e04-425">经典发布页面 HTML 响应中的 IMG/LINK/CSS URL</span><span class="sxs-lookup"><span data-stu-id="47e04-425">IMG/LINK/CSS URLs in classic publishing page HTML responses</span></span>
  - <span data-ttu-id="47e04-426">这包括作者在页面的 HTML 内容中添加的图像</span><span class="sxs-lookup"><span data-stu-id="47e04-426">This includes images added by authors within the HTML content of a page</span></span>
- <span data-ttu-id="47e04-427">图片库幻灯片 Web 部件图像 URL</span><span class="sxs-lookup"><span data-stu-id="47e04-427">Picture Library SlideShow webpart image URLs</span></span>
- <span data-ttu-id="47e04-428">SPList REST API (RenderListDataAsStream) 结果中的图像字段</span><span class="sxs-lookup"><span data-stu-id="47e04-428">Image fields in SPList REST API (RenderListDataAsStream) results</span></span>
  - <span data-ttu-id="47e04-429">使用新的属性_ImageFieldsToTryRewriteToCdnUrls_提供以逗号分隔的字段列表</span><span class="sxs-lookup"><span data-stu-id="47e04-429">Use the new property _ImageFieldsToTryRewriteToCdnUrls_ to provide a comma separated list of fields</span></span>
  - <span data-ttu-id="47e04-430">支持 hyperlink 字段和 PublishingImage 字段</span><span class="sxs-lookup"><span data-stu-id="47e04-430">Supports hyperlink fields and PublishingImage fields</span></span>
- <span data-ttu-id="47e04-431">SharePoint 图像呈现形式</span><span class="sxs-lookup"><span data-stu-id="47e04-431">SharePoint image renditions</span></span>

<span data-ttu-id="47e04-432">下图演示了 SharePoint 收到来自公共来源的资产的页面请求时的工作流。</span><span class="sxs-lookup"><span data-stu-id="47e04-432">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a public origin.</span></span>

<span data-ttu-id="47e04-433">![工作流图表: 从公共来源检索 Office 365 CDN 资产](media/O365-CDN/o365-cdn-public-steps-transparent.svg "工作流: 从公共来源检索 Office 365 CDN 资产")</span><span class="sxs-lookup"><span data-stu-id="47e04-433">![Workflow diagram: Retrieving Office 365 CDN assets from a public origin](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a public origin")</span></span>

> [!TIP]
> <span data-ttu-id="47e04-434">如果要对页面上的特定 Url 禁用自动重写, 则可以签出该页面, 并将查询字符串参数 **?NoAutoReWrites = true**添加到要禁用的每个链接的末尾。</span><span class="sxs-lookup"><span data-stu-id="47e04-434">If you want to disable auto-rewriting for specific URLs on a page, you can check out the page and add the query string parameter **?NoAutoReWrites=true** to the end of each link you want to disable.</span></span>

#### <a name="hardcoding-cdn-urls-for-public-assets"></a><span data-ttu-id="47e04-435">Hardcoding 适用于公共资产的 CDN Url</span><span class="sxs-lookup"><span data-stu-id="47e04-435">Hardcoding CDN URLs for public assets</span></span>

<span data-ttu-id="47e04-436">如果没有为公用源启用_发布_功能, 或者资产不是 cdn 服务自动重写功能支持的链接类型之一, 则可以手动构建指向资产的 CDN 位置的 url, 并在内容中使用这些 url。</span><span class="sxs-lookup"><span data-stu-id="47e04-436">If the _Publishing_ feature is not enabled for a public origin, or the asset is not one of the link types supported by the auto-rewrite feature of the CDN service, you can manually construct URLs to the CDN location of the assets and use these URLs in your content.</span></span>

> [!NOTE]
> <span data-ttu-id="47e04-437">您不能将 CDN Url 硬编码到私有源中的资产, 因为在请求资源时, 会生成构成 URL 最后一部分的必需访问令牌。</span><span class="sxs-lookup"><span data-stu-id="47e04-437">You cannot hardcode CDN URLs to assets in a private origin because the required access token that forms the last section of the URL is generated at the time the resource is requested.</span></span>

<span data-ttu-id="47e04-438">对于公共 CDN 资产, URL 格式将如下所示:</span><span class="sxs-lookup"><span data-stu-id="47e04-438">For public CDN assets, the URL format will look like the following:</span></span>

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

<span data-ttu-id="47e04-439">将**TenantHostName**替换为你的租户名称。</span><span class="sxs-lookup"><span data-stu-id="47e04-439">Replace **TenantHostName** with your tenant name.</span></span> <span data-ttu-id="47e04-440">示例：</span><span class="sxs-lookup"><span data-stu-id="47e04-440">Example:</span></span>

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a><span data-ttu-id="47e04-441">在专用来源中使用资产</span><span class="sxs-lookup"><span data-stu-id="47e04-441">Using assets in private origins</span></span>

<span data-ttu-id="47e04-442">使用专用来源的资产不需要额外的配置。</span><span class="sxs-lookup"><span data-stu-id="47e04-442">No additional configuration is required to use assets in private origins.</span></span> <span data-ttu-id="47e04-443">SharePoint Online 会自动为私人来源中的资产重写 Url, 因此这些资产的请求将始终通过 CDN 提供。</span><span class="sxs-lookup"><span data-stu-id="47e04-443">SharePoint Online automatically rewrites URLs for assets in private origins so requests for those assets will always be served from the CDN.</span></span> <span data-ttu-id="47e04-444">无法在专用来源中手动生成 CDN 资产的 Url, 因为这些 Url 包含在请求资产时必须由 SharePoint Online 自动生成的令牌。</span><span class="sxs-lookup"><span data-stu-id="47e04-444">You cannot manually build URLs to CDN assets in private origins because these URLs contain tokens that must be auto-generated by SharePoint Online at the time the asset is requested.</span></span>

<span data-ttu-id="47e04-445">对私人来源资产的访问受基于用户权限对源的动态生成令牌的保护, 以及以下各节中介绍的注意事项。</span><span class="sxs-lookup"><span data-stu-id="47e04-445">Access to assets in private origins is protected by dynamically generated tokens based on user permissions to the origin, with the caveats described in the following sections.</span></span> <span data-ttu-id="47e04-446">用户必须至少具有对 CDN 的**读取**访问权限才能呈现内容。</span><span class="sxs-lookup"><span data-stu-id="47e04-446">Users must have at least **read** access to the origins for the CDN to render content.</span></span>

<span data-ttu-id="47e04-447">下图说明了在 SharePoint 收到来自专用来源的资产的请求时, 该工作流的工作流。</span><span class="sxs-lookup"><span data-stu-id="47e04-447">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a private origin.</span></span>

<span data-ttu-id="47e04-448">![工作流图表: 从私有源检索 Office 365 CDN 资产](media/O365-CDN/o365-cdn-private-steps-transparent.svg "工作流: 从私有源检索 Office 365 CDN 资产")</span><span class="sxs-lookup"><span data-stu-id="47e04-448">![Workflow diagram: Retrieving Office 365 CDN assets from a private origin](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a private origin")</span></span>

#### <a name="token-based-authorization-in-private-origins"></a><span data-ttu-id="47e04-449">专用来源的基于令牌的授权</span><span class="sxs-lookup"><span data-stu-id="47e04-449">Token-based authorization in private origins</span></span>

<span data-ttu-id="47e04-450">在 Office 365 CDN 中对私人来源的资产的访问权限由 SharePoint Online 生成的令牌授予。</span><span class="sxs-lookup"><span data-stu-id="47e04-450">Access to assets in private origins in the Office 365 CDN is granted by tokens generated by SharePoint Online.</span></span> <span data-ttu-id="47e04-451">如果用户已有权访问由来源指定的文件夹或库, 则会自动向其授予允许用户根据其权限级别访问文件的令牌。</span><span class="sxs-lookup"><span data-stu-id="47e04-451">Users who already have permission to access to the folder or library designated by the origin are automatically granted tokens that permit the user to access the file based on their permission level.</span></span> <span data-ttu-id="47e04-452">这些访问令牌在生成后有效期为30至90分钟, 以帮助防止令牌重播攻击。</span><span class="sxs-lookup"><span data-stu-id="47e04-452">These access tokens are valid for 30 to 90 minutes after they are generated to help prevent token replay attacks.</span></span>

<span data-ttu-id="47e04-453">在生成访问令牌后, SharePoint Online 将向客户端返回一个自定义 URI, 其中包含两个授权参数_吃_(边缘授权令牌) 和_oat_ (原始授权令牌)。</span><span class="sxs-lookup"><span data-stu-id="47e04-453">Once the access token is generated, SharePoint Online returns a custom URI to the client containing two authorization parameters _eat_ (edge authorization token) and _oat_ (origin authorization token).</span></span> <span data-ttu-id="47e04-454">每个令牌的结构是 _<'expiration Time Format'>__<'secure signature'>_。</span><span class="sxs-lookup"><span data-stu-id="47e04-454">The structure of each token is _<'expiration time in Epoch time format'>__<'secure signature'>_.</span></span> <span data-ttu-id="47e04-455">例如：</span><span class="sxs-lookup"><span data-stu-id="47e04-455">For example:</span></span>

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> <span data-ttu-id="47e04-456">拥有令牌的任何人都可以访问 CDN 中的资源。</span><span class="sxs-lookup"><span data-stu-id="47e04-456">Anyone in possession of the token can access the resource in the CDN.</span></span> <span data-ttu-id="47e04-457">但是, 包含这些访问令牌的 Url 仅通过 HTTPS 共享, 因此, 除非最终用户在令牌过期之前显式共享该 URL, 否则, 未经授权的用户将无法访问该资源。</span><span class="sxs-lookup"><span data-stu-id="47e04-457">However, URLs containing these access tokens are only shared over HTTPS, so unless the URL is explicitly shared by an end user before the token expires, the asset won’t be accessible to unauthorized users.</span></span>

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a><span data-ttu-id="47e04-458">私人来源的资产不支持项目级权限</span><span class="sxs-lookup"><span data-stu-id="47e04-458">Item-level permissions are not supported for assets in private origins</span></span>

<span data-ttu-id="47e04-459">请务必注意, SharePoint Online 不支持私人来源资产的项目级权限。</span><span class="sxs-lookup"><span data-stu-id="47e04-459">It is important to note that SharePoint Online does not support item-level permissions for assets in private origins.</span></span> <span data-ttu-id="47e04-460">例如, 对于位于的文件, 在`https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`以下情况下, 用户可以有效访问文件:</span><span class="sxs-lookup"><span data-stu-id="47e04-460">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, users have effective access to the file given the following conditions:</span></span>

|<span data-ttu-id="47e04-461">用户</span><span class="sxs-lookup"><span data-stu-id="47e04-461">User</span></span>  |<span data-ttu-id="47e04-462">权限</span><span class="sxs-lookup"><span data-stu-id="47e04-462">Permissions</span></span>  |<span data-ttu-id="47e04-463">有效访问</span><span class="sxs-lookup"><span data-stu-id="47e04-463">Effective access</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="47e04-464">用户1</span><span class="sxs-lookup"><span data-stu-id="47e04-464">User 1</span></span>     |<span data-ttu-id="47e04-465">有权访问 folder1</span><span class="sxs-lookup"><span data-stu-id="47e04-465">Has access to folder1</span></span>         |<span data-ttu-id="47e04-466">可以从 CDN 访问 image1</span><span class="sxs-lookup"><span data-stu-id="47e04-466">Can access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="47e04-467">用户2</span><span class="sxs-lookup"><span data-stu-id="47e04-467">User 2</span></span>     |<span data-ttu-id="47e04-468">不具有对 folder1 的访问权限</span><span class="sxs-lookup"><span data-stu-id="47e04-468">Does not have access to folder1</span></span>         |<span data-ttu-id="47e04-469">无法从 CDN 访问 image1</span><span class="sxs-lookup"><span data-stu-id="47e04-469">Cannot access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="47e04-470">用户3</span><span class="sxs-lookup"><span data-stu-id="47e04-470">User 3</span></span>     |<span data-ttu-id="47e04-471">不具有对 folder1 的访问权限, 但被授予了在 SharePoint Online 中访问 image1 的显式权限</span><span class="sxs-lookup"><span data-stu-id="47e04-471">Does not have access to folder1, but is granted explicit permission to access image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="47e04-472">可以直接从 SharePoint Online 访问资产 image1, 但不能从 CDN 访问</span><span class="sxs-lookup"><span data-stu-id="47e04-472">Can access the asset image1.jpg directly from SharePoint Online, but not from the CDN</span></span>         |
|<span data-ttu-id="47e04-473">用户4</span><span class="sxs-lookup"><span data-stu-id="47e04-473">User 4</span></span>     |<span data-ttu-id="47e04-474">有权访问 folder1, 但已明确拒绝对 SharePoint Online 中的 image1 的访问</span><span class="sxs-lookup"><span data-stu-id="47e04-474">Has access to folder1, but has been explicitly denied access to image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="47e04-475">无法从 SharePoint Online 访问资产, 但可以从 CDN 访问资产, 尽管在 SharePoint Online 中拒绝对文件的访问</span><span class="sxs-lookup"><span data-stu-id="47e04-475">Cannot access the asset from SharePoint Online, but can access the asset from the CDN despite being denied access to the file in SharePoint Online</span></span>         |

## <a name="troubleshooting-the-office-365-cdn"></a><span data-ttu-id="47e04-476">Office 365 CDN 故障排除</span><span class="sxs-lookup"><span data-stu-id="47e04-476">Troubleshooting the Office 365 CDN</span></span>
<span data-ttu-id="47e04-477"><a name="CDNTroubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-477"></span></span>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a><span data-ttu-id="47e04-478">如何确认 CDN 是否正在为资产提供服务？</span><span class="sxs-lookup"><span data-stu-id="47e04-478">How do I confirm that assets are being served by the CDN?</span></span>
<span data-ttu-id="47e04-479"><a name="CDNConfirm"> </a></span><span class="sxs-lookup"><span data-stu-id="47e04-479"></span></span>

<span data-ttu-id="47e04-480">将 CDN 资产的链接添加到页面后, 您可以通过浏览页面来确认是否已从 CDN 提供资产, 在呈现并查看图像 URL 后, 右键单击该图像。</span><span class="sxs-lookup"><span data-stu-id="47e04-480">Once you have added links to CDN assets to a page, you can confirm that the asset is being served from the CDN by browsing to the page, right clicking on the image once it has rendered and reviewing the image URL.</span></span>

<span data-ttu-id="47e04-481">您还可以使用浏览器的开发人员工具来查看页面上每个资源的 URL, 或使用第三方网络跟踪工具。</span><span class="sxs-lookup"><span data-stu-id="47e04-481">You can also use your browser's developer tools to view the URL for each asset on a page, or use a 3rd party network trace tool.</span></span>

> [!NOTE]
> <span data-ttu-id="47e04-482">如果使用网络工具 (例如 Fiddler) 在从 SharePoint 页面呈现资产的外部测试您的资产, 您必须手动将引用的邮件头 "定位: `https://yourdomain.sharepoint.com`" 添加到 URL 为 sharepoint Online 租户的根 URL 的 GET 请求中。</span><span class="sxs-lookup"><span data-stu-id="47e04-482">If you use a network tool such as Fiddler to test your assets outside of rendering the asset from a SharePoint page, you must manually add the referrer header “Referrer: `https://yourdomain.sharepoint.com`” to the GET request where the URL is the root URL of your SharePoint Online tenant.</span></span>

<span data-ttu-id="47e04-483">您不能直接在 web 浏览器中测试 CDN Url, 因为您必须具有来自 SharePoint Online 的引用。</span><span class="sxs-lookup"><span data-stu-id="47e04-483">You cannot test CDN URLs directly in a web browser because you must have a referrer coming from SharePoint Online.</span></span> <span data-ttu-id="47e04-484">但是, 如果将 CDN 资产 URL 添加到 SharePoint 页面, 然后在浏览器中打开该页面, 则会看到页面上呈现的 CDN 资产。</span><span class="sxs-lookup"><span data-stu-id="47e04-484">However, if you add the CDN asset URL to a SharePoint page and then open the page in a browser, you will see the CDN asset rendered on the page.</span></span>

<span data-ttu-id="47e04-485">有关在 Microsoft Edge 浏览器中使用开发人员工具的详细信息, 请参阅[Microsoft Edge 开发人员工具](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide)。</span><span class="sxs-lookup"><span data-stu-id="47e04-485">For more information on using the developer tools in the Microsoft Edge browser, see [Microsoft Edge Developer Tools](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).</span></span>

### <a name="why-are-assets-from-a-new-origin-unavailable"></a><span data-ttu-id="47e04-486">为什么来自新来源的资产不可用？</span><span class="sxs-lookup"><span data-stu-id="47e04-486">Why are assets from a new origin unavailable?</span></span>
<span data-ttu-id="47e04-487">新资源源中的资产不会立即可供使用, 因为注册通过 CDN 传播以及将资产从来源上载到 CDN 存储需要花费时间。</span><span class="sxs-lookup"><span data-stu-id="47e04-487">Assets in new origins will not immediately be available for use, as it takes time for the registration to propagate through the CDN and for the assets to be uploaded from the origin to CDN storage.</span></span> <span data-ttu-id="47e04-488">在 CDN 中提供资产所需的时间取决于资产和文件的大小。</span><span class="sxs-lookup"><span data-stu-id="47e04-488">The time required for assets to be available in the CDN depends on how many assets and the files sizes.</span></span>

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a><span data-ttu-id="47e04-489">我的客户端 web 部件或 SharePoint 框架解决方案不起作用</span><span class="sxs-lookup"><span data-stu-id="47e04-489">My client-side web part or SharePoint Framework solution isn't working</span></span>

<span data-ttu-id="47e04-490">为公共起源启用 Office 365 CDN 时, CDN 服务会自动创建以下默认来源:</span><span class="sxs-lookup"><span data-stu-id="47e04-490">When you enable the Office 365 CDN for public origins, the CDN service automatically creates these default origins:</span></span>

- <span data-ttu-id="47e04-491">\*/MASTERPAGE</span><span class="sxs-lookup"><span data-stu-id="47e04-491">\*/MASTERPAGE</span></span>
- <span data-ttu-id="47e04-492">\*/STYLE 库</span><span class="sxs-lookup"><span data-stu-id="47e04-492">\*/STYLE LIBRARY</span></span>
- <span data-ttu-id="47e04-493">\*/CLIENTSIDEASSETS</span><span class="sxs-lookup"><span data-stu-id="47e04-493">\*/CLIENTSIDEASSETS</span></span>

<span data-ttu-id="47e04-494">如果缺少 \*/clientsideassets 原点, SharePoint 框架解决方案将失败, 并且不会生成警告或错误消息。</span><span class="sxs-lookup"><span data-stu-id="47e04-494">If the \*/clientsideassets origin is missing, SharePoint Framework solutions will fail, and no warning or error messages are generated.</span></span> <span data-ttu-id="47e04-495">由于启用了 _-NoDefaultOrigins_参数设置为 **$true**, 或者已手动删除了来源, 因此此来源可能丢失。</span><span class="sxs-lookup"><span data-stu-id="47e04-495">This origin may be missing either because the CDN was enabled with the _-NoDefaultOrigins_ parameter set to **$true**, or because the origin was manually deleted.</span></span>

<span data-ttu-id="47e04-496">您可以使用以下 PowerShell 命令查看 \*/CLIENTSIDEASSETS 源是否存在:</span><span class="sxs-lookup"><span data-stu-id="47e04-496">You can check to see if the \*/CLIENTSIDEASSETS origin is present with the following PowerShell command:</span></span>

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="47e04-497">或者, 您可以使用 Office 365 CLI 进行检查:</span><span class="sxs-lookup"><span data-stu-id="47e04-497">Or you can check with the Office 365 CLI:</span></span>

``` powershell
spo cdn origin list
```

<span data-ttu-id="47e04-498">若要在 PowerShell 中添加源, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="47e04-498">To add the origin in PowerShell:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="47e04-499">若要在 Office 365 CLI 中添加原点, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="47e04-499">To add the origin in the Office 365 CLI:</span></span>

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a><span data-ttu-id="47e04-500">我需要哪些 PowerShell 模块和 CLI shell 才能与 Office 365 CDN 配合使用？</span><span class="sxs-lookup"><span data-stu-id="47e04-500">What PowerShell modules and CLI shells do I need to work with the Office 365 CDN?</span></span>

<span data-ttu-id="47e04-501">您可以使用**SharePoint Online 命令行管理**程序 PowerShell 模块或**office 365 CLI**选择使用 office 365 CDN。</span><span class="sxs-lookup"><span data-stu-id="47e04-501">You can choose to work with the Office 365 CDN using either the **SharePoint Online Management Shell** PowerShell module or the **Office 365 CLI**.</span></span>

- [<span data-ttu-id="47e04-502">SharePoint Online 命令行管理程序入门</span><span class="sxs-lookup"><span data-stu-id="47e04-502">Getting started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [<span data-ttu-id="47e04-503">安装 Office 365 CLI</span><span class="sxs-lookup"><span data-stu-id="47e04-503">Installing the Office 365 CLI</span></span>](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a><span data-ttu-id="47e04-504">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47e04-504">See also</span></span>

[<span data-ttu-id="47e04-505">内容分发网络</span><span class="sxs-lookup"><span data-stu-id="47e04-505">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="47e04-506">Office 365 网络计划和性能优化</span><span class="sxs-lookup"><span data-stu-id="47e04-506">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

