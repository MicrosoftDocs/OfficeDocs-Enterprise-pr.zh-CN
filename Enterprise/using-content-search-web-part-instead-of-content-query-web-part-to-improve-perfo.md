---
title: 使用内容搜索 Web 部件而不是内容查询 Web 部件来提高 SharePoint Online 中的性能
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: 了解如何通过将内容查询 Web 部件替换为 SharePoint Server 2013 和 SharePoint Online 中的内容搜索 Web 部件来提高性能。
ms.openlocfilehash: 50706236c3ecdbdf915c257877990c4b9e51e22a
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46603534"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="b37d5-103">使用内容搜索 Web 部件而不是内容查询 Web 部件来提高 SharePoint Online 中的性能</span><span class="sxs-lookup"><span data-stu-id="b37d5-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="b37d5-104">本文介绍如何通过将内容查询 Web 部件替换为 SharePoint Server 2013 和 SharePoint Online 中的内容搜索 Web 部件来提高性能。</span><span class="sxs-lookup"><span data-stu-id="b37d5-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="b37d5-105">SharePoint Server 2013 和 SharePoint Online 的一项最强大的新功能是内容搜索 Web 部件 (CSWP) 。</span><span class="sxs-lookup"><span data-stu-id="b37d5-105">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP).</span></span> <span data-ttu-id="b37d5-106">此 Web 部件使用搜索索引快速检索向用户显示的结果。</span><span class="sxs-lookup"><span data-stu-id="b37d5-106">This Web Part uses the search index to quickly retrieve results which are shown to the user.</span></span> <span data-ttu-id="b37d5-107">使用内容搜索 Web 部件（而不是内容查询 Web 部件） (CQWP) 在页面中，为用户提高性能。</span><span class="sxs-lookup"><span data-stu-id="b37d5-107">Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="b37d5-108">在内容查询 Web 部件上使用内容搜索 Web 部件几乎总是能够在 SharePoint Online 上显著提高页面加载性能。</span><span class="sxs-lookup"><span data-stu-id="b37d5-108">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online.</span></span> <span data-ttu-id="b37d5-109">有一些额外的配置可实现正确的查询，但回报的性能和用户感到高兴更高。</span><span class="sxs-lookup"><span data-stu-id="b37d5-109">There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="b37d5-110">比较从使用内容搜索 Web 部件（而不是内容查询 Web 部件）获取的性能增益</span><span class="sxs-lookup"><span data-stu-id="b37d5-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="b37d5-111">下面的示例展示了使用内容搜索 Web 部件而不是内容查询 Web 部件时可能会收到的相对性能收益。</span><span class="sxs-lookup"><span data-stu-id="b37d5-111">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part.</span></span> <span data-ttu-id="b37d5-112">复杂的网站结构和非常广泛的内容查询效果更明显。</span><span class="sxs-lookup"><span data-stu-id="b37d5-112">The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="b37d5-113">此示例网站具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="b37d5-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="b37d5-114">8个子网站级别。</span><span class="sxs-lookup"><span data-stu-id="b37d5-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="b37d5-115">使用自定义 "水果" 内容类型的列表。</span><span class="sxs-lookup"><span data-stu-id="b37d5-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="b37d5-116">在 Web 部件中，内容查询是广泛的，返回内容类型为 "水果" 的所有项目。</span><span class="sxs-lookup"><span data-stu-id="b37d5-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="b37d5-117">该示例仅在8个网站中使用50个项目。</span><span class="sxs-lookup"><span data-stu-id="b37d5-117">The example only uses 50 items across the 8 sites.</span></span> <span data-ttu-id="b37d5-118">对于包含更多内容的网站，效果会更明显。</span><span class="sxs-lookup"><span data-stu-id="b37d5-118">The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="b37d5-119">下面是内容查询 Web 部件的结果的屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="b37d5-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![显示 Web 部件的内容查询的图形](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="b37d5-121">在 Internet Explorer 中，使用 F12 开发人员工具的 "**网络**" 选项卡查看响应标头的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b37d5-121">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header.</span></span> <span data-ttu-id="b37d5-122">在下面的屏幕截图中，此页面加载的**SPRequestDuration**的值为924毫秒。</span><span class="sxs-lookup"><span data-stu-id="b37d5-122">In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![显示请求持续时间为 924 的屏幕截图](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="b37d5-124">**SPRequestDuration**指示在服务器上完成的准备页面的工作量。</span><span class="sxs-lookup"><span data-stu-id="b37d5-124">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page.</span></span> <span data-ttu-id="b37d5-125">通过查询 Web 部件切换内容通过搜索 Web 部件的内容，可以大大减少呈现页面所需的时间。</span><span class="sxs-lookup"><span data-stu-id="b37d5-125">Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page.</span></span> <span data-ttu-id="b37d5-126">相比之下，具有等效内容搜索 Web 部件的页面，返回相同数量的结果的**SPRequestDuration**值为106毫秒，如以下屏幕截图所示：</span><span class="sxs-lookup"><span data-stu-id="b37d5-126">By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![显示请求持续时间为 106 的屏幕截图](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="b37d5-128">在 SharePoint Online 中添加内容搜索 Web 部件</span><span class="sxs-lookup"><span data-stu-id="b37d5-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="b37d5-129">添加内容搜索 Web 部件与常规内容查询 Web 部件非常相似。</span><span class="sxs-lookup"><span data-stu-id="b37d5-129">Adding a Content Search Web Part is very similar to a regular Content Query Web Part.</span></span> <span data-ttu-id="b37d5-130">请参阅在[SharePoint 中配置内容搜索 Web 部件](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)中的 *"添加内容搜索 web 部件"* 一节。</span><span class="sxs-lookup"><span data-stu-id="b37d5-130">See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="b37d5-131">为内容搜索 Web 部件创建正确的搜索查询</span><span class="sxs-lookup"><span data-stu-id="b37d5-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="b37d5-132">添加内容搜索 Web 部件后，可以优化搜索并返回所需的项目。</span><span class="sxs-lookup"><span data-stu-id="b37d5-132">Once you have added a Content Search Web Part, you can refine the search and return the items you want.</span></span> <span data-ttu-id="b37d5-133">有关如何执行此操作的详细说明，请参阅在[SharePoint 中配置内容搜索 Web 部件](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)中的 *"通过在内容搜索 web 部件中配置高级查询来显示内容"* 一节。</span><span class="sxs-lookup"><span data-stu-id="b37d5-133">For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="b37d5-134">查询生成和测试工具</span><span class="sxs-lookup"><span data-stu-id="b37d5-134">Query building and testing tool</span></span>

<span data-ttu-id="b37d5-135">有关生成和测试复杂查询的工具，请参阅 Codeplex 上的[搜索查询工具](https://sp2013searchtool.codeplex.com/)。</span><span class="sxs-lookup"><span data-stu-id="b37d5-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

