---
title: 诊断 SharePoint Online 的性能问题
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: 本文说明如何使用您使用 Internet Explorer 开发人员工具的 SharePoint Online 网站诊断的常见问题。
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539688"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="66355-103">诊断 SharePoint Online 的性能问题</span><span class="sxs-lookup"><span data-stu-id="66355-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="66355-104">本文说明如何使用您使用 Internet Explorer 开发人员工具的 SharePoint Online 网站诊断的常见问题。</span><span class="sxs-lookup"><span data-stu-id="66355-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="66355-105">您可以使用三种不同的方法来识别 SharePoint Online 网站上某个页面的自定义项是否存在性能问题。</span><span class="sxs-lookup"><span data-stu-id="66355-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="66355-106">F12 工具栏网络监视器</span><span class="sxs-lookup"><span data-stu-id="66355-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="66355-107">与非自定义基准的比较</span><span class="sxs-lookup"><span data-stu-id="66355-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="66355-108">SharePoint Online 响应头指标</span><span class="sxs-lookup"><span data-stu-id="66355-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="66355-p101">本主题介绍如何使用这些方法的每个诊断性能问题。一旦您已经确定问题的原因，您可以向使用提高 SharePoint 性能的上可以找到有关的文章的解决方案中处理http://aka.ms/tune。</span><span class="sxs-lookup"><span data-stu-id="66355-p101">This topic describes how to use each of these methods to diagnose performance issues. Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="66355-111">使用 F12 工具栏来诊断 SharePoint Online 中的性能</span><span class="sxs-lookup"><span data-stu-id="66355-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="66355-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="66355-112"></span></span>

<span data-ttu-id="66355-p102">在本文中，我们将使用 Internet Explorer 11。虽然可能看起来稍有不同，其他浏览器上的 F12 开发人员工具的各个版本也具有类似功能。有关 F12 开发人员工具的信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="66355-p102">In this article we use Internet Explorer 11. Versions of the F12 developer tools on other browsers have similar features though they may look slightly different. For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="66355-116">What's new in F12 工具</span><span class="sxs-lookup"><span data-stu-id="66355-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [<span data-ttu-id="66355-117">使用 F12 开发人员工具</span><span class="sxs-lookup"><span data-stu-id="66355-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
<span data-ttu-id="66355-118">若要显示开发人员工具，请按“F12”****，然后单击 Wi-Fi 图标： 
</span><span class="sxs-lookup"><span data-stu-id="66355-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![F12 开发人员工具 wifi 图标的屏幕截图](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="66355-p103">在“网络”**** 选项卡上，按绿色播放按钮以加载页面。该工具返回浏览器请求的所有文件，以获取您要求的页面。下面的屏幕截图显示了一个此类列表。</span><span class="sxs-lookup"><span data-stu-id="66355-p103">On the **Network** tab, press the green play button to load a page. The tool returns all of the files that the browser requests in order to get the page you asked for. The following screen shot shows one such list.</span></span> 
  
![返回页面请求的文件列表的屏幕截图。](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="66355-124">如该屏幕截图中所示，您还可以在文件右侧查看文件的下载时间。</span><span class="sxs-lookup"><span data-stu-id="66355-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![显示从 SharePoint 加载请求页面所需时间的图表](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="66355-p104">这让您可以清楚地看到加载文件所用的时间。绿线表示页面何时准备好由浏览器呈现。这可以使您快速查看可能导致您的网站上页面加载较慢的各种文件。

</span><span class="sxs-lookup"><span data-stu-id="66355-p104">This gives you a visual representation of how long the file took to load. The green line represents when the page is ready to be rendered by the browser. This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="66355-129">设置 SharePoint online 的非自定义的比较基准</span><span class="sxs-lookup"><span data-stu-id="66355-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="66355-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="66355-130"></span></span>

<span data-ttu-id="66355-p105">确定网站的性能薄弱点的最佳方式是设置 SharePoint Online 中完全--开网站集。这样可以进行比较所有您会在上无自定义的站点的各个方面。OneDrive for Business 主页是一个很好的单独的网站集可能遇到的任何自定义的示例。</span><span class="sxs-lookup"><span data-stu-id="66355-p105">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online. This way you can compare all the various aspects of your site with what you would get with no customization on the page. The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="66355-134">查看 SharePoint 响应头信息</span><span class="sxs-lookup"><span data-stu-id="66355-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="66355-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="66355-135"></span></span>

<span data-ttu-id="66355-p106">在 SharePoint Online 和 SharePoint Server 2013 中，您可以在每个文件的响应头中访问发回给浏览器的信息。用于诊断性能问题最有用的两个值是 SPRequestDuration 和 X-SharePointHealthScore：</span><span class="sxs-lookup"><span data-stu-id="66355-p106">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file. The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="66355-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="66355-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="66355-p107">表示在服务器上处理请求所用的时间。这可以帮助确定请求是否为极重负载并会占用大量资源。这能让您最清楚地了解服务器为提供页面所完成的工作量。</span><span class="sxs-lookup"><span data-stu-id="66355-p107">This is the amount of time that the request took on the server to be processed. This can help determine if the request is very heavy and resource intensive. This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="66355-142">**X SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="66355-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="66355-p108">这指示服务器或在其运行 SharePoint 实例的 CPU 的利用率。此号码范围是从 0 到 10 其中 0 表示服务器处于空闲状态，10 表示服务器是很忙。始终 9 或 10 HealthScore 可能表明服务器正在进行的性能问题。任何其他数字指示该服务器操作系统预期范围内。</span><span class="sxs-lookup"><span data-stu-id="66355-p108">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs. This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy. A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server. Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="66355-147">**查看 SharePoint 响应头信息**</span><span class="sxs-lookup"><span data-stu-id="66355-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="66355-p109">确保您已安装的 F12 工具。有关下载和安装这些工具的详细信息，请参阅[What's new in F12 工具](https://go.microsoft.com/fwlink/p/?LinkId=522545)。</span><span class="sxs-lookup"><span data-stu-id="66355-p109">Ensure that you have the F12 tools installed. For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="66355-150">在 F12 工具的“网络”**** 选项卡上，按绿色播放按钮以加载页面。</span><span class="sxs-lookup"><span data-stu-id="66355-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="66355-151">单击工具返回的一个 .aspx 文件，然后单击“详细信息”****。</span><span class="sxs-lookup"><span data-stu-id="66355-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![显示响应头的详细信息](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="66355-153">单击“响应头”****。</span><span class="sxs-lookup"><span data-stu-id="66355-153">Click **Response headers**.</span></span> 
    
    ![显示响应头的 URL 的图表](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="66355-155">什么原因导致 SharePoint Online 中出现性能问题？</span><span class="sxs-lookup"><span data-stu-id="66355-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="66355-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="66355-156"></span></span>

<span data-ttu-id="66355-p110">文章[SharePoint online 的导航选项](navigation-options-for-sharepoint-online.md)显示使用 SPRequestDuration 值确定复杂结构导航已导致页需要很长时间处理服务器上的示例。按照基线网站 （不带自定义项） 的值，就可以确定任何给定的文件是否花费很长时间才能加载。[导航选项 SharePoint online](navigation-options-for-sharepoint-online.md)中使用的示例是主要的.aspx 文件。该文件包含运行的页面加载的 ASP.NET 代码的大部分。根据您使用的网站模板，这可能是 start.aspx、 home.aspx、 default.aspx 或其他名称如果自定义主页。如果此号码相当高于基线网站，它是充分表明没有某些内容复杂事在导致性能问题的页面中。</span><span class="sxs-lookup"><span data-stu-id="66355-p110">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server. By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load. The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file. That file contains most of the ASP.NET code that runs for your page load. Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page. If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="66355-p111">当您确定您的网站的特定问题后，找出导致性能不佳的原因的建议方式是消除所有可能的原因（例如页面自定义设置），然后将它们逐一添加回网站。当您删除足够的自定义项使页面运行良好之后，就可以逐一添加回特定自定义项。</span><span class="sxs-lookup"><span data-stu-id="66355-p111">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one. Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="66355-p112">例如，如果您有一个非常复杂的导航尝试将导航更改为不显示子网站，请检查开发人员工具查看是否有任何区别。或者，如果您有大量的内容更新汇总，请尝试从您的页面中删除，并检查性能是否有所改善。如果您消除了所有可能的原因，并将其逐一添加回页面中，您就可以轻松地识别哪些功能是最大的问题，并制定出解决方案。 
</span><span class="sxs-lookup"><span data-stu-id="66355-p112">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference. Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things. If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

