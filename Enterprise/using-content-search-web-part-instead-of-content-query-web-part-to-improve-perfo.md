---
title: 使用内容搜索 Web 部件而不内容查询 Web 部件在 SharePoint Online 中提高性能
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: 本文介绍如何通过将 SharePoint Server 2013 和 SharePoint Online 中的内容搜索 Web 部件替换为内容查询 Web 部件来提高性能。
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539851"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="00aaa-103">使用内容搜索 Web 部件而不内容查询 Web 部件在 SharePoint Online 中提高性能</span><span class="sxs-lookup"><span data-stu-id="00aaa-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="00aaa-104">本文介绍如何通过将 SharePoint Server 2013 和 SharePoint Online 中的内容搜索 Web 部件替换为内容查询 Web 部件来提高性能。</span><span class="sxs-lookup"><span data-stu-id="00aaa-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="00aaa-p101">SharePoint Server 2013 和 SharePoint Online 的最强大的新功能之一是内容搜索 Web 部件 (CSWP)。此 Web 部件使用搜索索引来快速检索其向用户显示的结果。使用内容搜索 Web 部件而不是内容查询 Web 部件 (CQWP) 在页面中来提高您的用户的性能。</span><span class="sxs-lookup"><span data-stu-id="00aaa-p101">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP). This Web Part uses the search index to quickly retrieve results which are shown to the user. Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="00aaa-p102">通过内容查询 Web 部件中使用内容搜索 Web 部件始终将导致在 SharePoint Online 的长足页面加载性能。没有很少的其他配置，以获取正确的查询，但奖励提高的性能和 happier 用户。</span><span class="sxs-lookup"><span data-stu-id="00aaa-p102">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online. There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="00aaa-110">比较获得而不内容查询 Web 部件中使用内容搜索 Web 部件的性能提升</span><span class="sxs-lookup"><span data-stu-id="00aaa-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="00aaa-p103">下面的示例演示当您使用而不是为内容查询 Web 部件的内容搜索 Web 部件时可能会收到相对的性能提升。效果是更复杂的网站结构和非常广泛的内容查询明显。</span><span class="sxs-lookup"><span data-stu-id="00aaa-p103">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part. The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="00aaa-113">此示例网站具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="00aaa-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="00aaa-114">8 级别的子网站。</span><span class="sxs-lookup"><span data-stu-id="00aaa-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="00aaa-115">列出了使用自定义"果"内容类型。</span><span class="sxs-lookup"><span data-stu-id="00aaa-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="00aaa-116">在 Web 部件中，内容查询是广泛，返回与"果"的内容类型的所有项。</span><span class="sxs-lookup"><span data-stu-id="00aaa-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="00aaa-p104">该示例仅 8 网站之间使用 50 个项。效果将会更多明显网站具有更多的内容。</span><span class="sxs-lookup"><span data-stu-id="00aaa-p104">The example only uses 50 items across the 8 sites. The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="00aaa-119">下面是结果的内容查询 Web 部件的屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="00aaa-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![显示 Web 部件的内容查询的图形](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="00aaa-p105">在 Internet Explorer 中，使用 F12 开发人员工具的**网络**选项卡查看在响应标头的详细信息。以下屏幕截图中, **SPRequestDuration**此页面负载的值为 924 毫秒。</span><span class="sxs-lookup"><span data-stu-id="00aaa-p105">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header. In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![显示请求持续时间为 924 的屏幕截图](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="00aaa-p106">**SPRequestDuration**指示准备页面在服务器上完成的工时量。显著切换内容搜索 Web 部件内容查询 Web 部件可减少呈现页面的时间。相比之下，与等效的内容搜索 Web 部件页，返回相同的结果数其**SPRequestDuration**值的 106 毫秒此屏幕截图中所示：</span><span class="sxs-lookup"><span data-stu-id="00aaa-p106">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page. Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page. By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![显示请求持续时间为 106 的屏幕截图](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="00aaa-128">在 SharePoint Online 添加内容搜索 Web 部件</span><span class="sxs-lookup"><span data-stu-id="00aaa-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="00aaa-p107">添加内容搜索 Web 部件是非常类似于普通的内容查询 Web 部件。请参阅部分中[配置内容搜索 Web 部件在 SharePoint 中](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)的 *"添加内容搜索 Web 部件"* 。</span><span class="sxs-lookup"><span data-stu-id="00aaa-p107">Adding a Content Search Web Part is very similar to a regular Content Query Web Part. See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="00aaa-131">创建内容搜索 Web 部件右侧的搜索查询</span><span class="sxs-lookup"><span data-stu-id="00aaa-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="00aaa-p108">添加内容搜索 Web 部件后，您可以优化搜索，并返回所需的项目。有关如何执行此操作的详细说明，请参阅部分，在[配置内容搜索 Web 部件在 SharePoint 中](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)的 *"通过配置高级的查询内容搜索 Web 部件中显示内容"* 。</span><span class="sxs-lookup"><span data-stu-id="00aaa-p108">Once you have added a Content Search Web Part, you can refine the search and return the items you want. For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="00aaa-134">查询构建和测试工具</span><span class="sxs-lookup"><span data-stu-id="00aaa-134">Query building and testing tool</span></span>

<span data-ttu-id="00aaa-135">用于生成和测试复杂查询的工具，请参阅 Codeplex 上的[搜索查询工具](https://sp2013searchtool.codeplex.com/)。</span><span class="sxs-lookup"><span data-stu-id="00aaa-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

