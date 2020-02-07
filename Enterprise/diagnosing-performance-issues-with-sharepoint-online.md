---
title: 诊断 SharePoint Online 的性能问题
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/9/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: 本文介绍如何使用 Internet Explorer 开发人员工具诊断 SharePoint Online 网站的常见问题。
ms.openlocfilehash: 6061af0f3fa032274f03d0d531b42d1f8db05b70
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840429"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="2eca4-103">诊断 SharePoint Online 的性能问题</span><span class="sxs-lookup"><span data-stu-id="2eca4-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="2eca4-104">本文介绍如何使用 Internet Explorer 开发人员工具诊断 SharePoint Online 网站的常见问题。</span><span class="sxs-lookup"><span data-stu-id="2eca4-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="2eca4-105">您可以使用三种不同的方法来确定 SharePoint Online 网站上的页面在自定义项中存在性能问题。</span><span class="sxs-lookup"><span data-stu-id="2eca4-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="2eca4-106">F12 工具栏网络监视器</span><span class="sxs-lookup"><span data-stu-id="2eca4-106">The F12 tool bar network monitor</span></span>

- <span data-ttu-id="2eca4-107">与非自定义基线的比较</span><span class="sxs-lookup"><span data-stu-id="2eca4-107">Comparison to a non-customized baseline</span></span>

- <span data-ttu-id="2eca4-108">SharePoint Online 响应标头指标</span><span class="sxs-lookup"><span data-stu-id="2eca4-108">SharePoint Online response header metrics</span></span>

<span data-ttu-id="2eca4-109">本主题介绍如何使用上述每种方法来诊断性能问题。</span><span class="sxs-lookup"><span data-stu-id="2eca4-109">This topic describes how to use each of these methods to diagnose performance issues.</span></span> <span data-ttu-id="2eca4-110">一旦您发现问题的原因，您可以使用有关改进 SharePoint 性能的文章来解决问题https://aka.ms/tune。</span><span class="sxs-lookup"><span data-stu-id="2eca4-110">Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on https://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="2eca4-111">使用 F12 工具条诊断 SharePoint Online 中的性能</span><span class="sxs-lookup"><span data-stu-id="2eca4-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="2eca4-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="2eca4-112"><a name="F12ToolInfo"> </a></span></span>

<span data-ttu-id="2eca4-113">在本文中，我们将使用 Internet Explorer 11。</span><span class="sxs-lookup"><span data-stu-id="2eca4-113">In this article we use Internet Explorer 11.</span></span> <span data-ttu-id="2eca4-114">其他浏览器上的 F12 开发人员工具的版本具有类似的功能，尽管它们看起来可能略有不同。</span><span class="sxs-lookup"><span data-stu-id="2eca4-114">Versions of the F12 developer tools on other browsers have similar features though they may look slightly different.</span></span> <span data-ttu-id="2eca4-115">有关 F12 开发人员工具的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="2eca4-115">For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="2eca4-116">F12 工具的新增功能</span><span class="sxs-lookup"><span data-stu-id="2eca4-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)

- [<span data-ttu-id="2eca4-117">使用 F12 开发人员工具</span><span class="sxs-lookup"><span data-stu-id="2eca4-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)

<span data-ttu-id="2eca4-118">若要显示开发人员工具，请按**F12**键，然后单击 wi-fi 图标：</span><span class="sxs-lookup"><span data-stu-id="2eca4-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span>
  
![F12 开发人员工具 wifi 图标的屏幕截图](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="2eca4-120">在 "**网络**" 选项卡上，按绿色的 "播放" 按钮以加载一个页面。</span><span class="sxs-lookup"><span data-stu-id="2eca4-120">On the **Network** tab, press the green play button to load a page.</span></span> <span data-ttu-id="2eca4-121">该工具将返回浏览器请求的所有文件，以便获取您要求的页面。</span><span class="sxs-lookup"><span data-stu-id="2eca4-121">The tool returns all of the files that the browser requests in order to get the page you asked for.</span></span> <span data-ttu-id="2eca4-122">下面的屏幕截图显示了一个这样的列表。</span><span class="sxs-lookup"><span data-stu-id="2eca4-122">The following screen shot shows one such list.</span></span>
  
![返回页面请求的文件列表的屏幕截图。](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="2eca4-124">您还可以查看右侧文件的下载时间，如此屏幕截图中所示。</span><span class="sxs-lookup"><span data-stu-id="2eca4-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![显示从 SharePoint 加载请求页面所需时间的图表](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="2eca4-126">这使您能够直观地表示文件加载所需的时间。</span><span class="sxs-lookup"><span data-stu-id="2eca4-126">This gives you a visual representation of how long the file took to load.</span></span> <span data-ttu-id="2eca4-127">绿色线表示浏览器准备呈现页面的时间。</span><span class="sxs-lookup"><span data-stu-id="2eca4-127">The green line represents when the page is ready to be rendered by the browser.</span></span> <span data-ttu-id="2eca4-128">这可让你快速查看可能导致你的网站上的页面负载缓慢的不同文件。</span><span class="sxs-lookup"><span data-stu-id="2eca4-128">This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="2eca4-129">为 SharePoint Online 设置非自定义基准</span><span class="sxs-lookup"><span data-stu-id="2eca4-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="2eca4-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="2eca4-130"><a name="F12ToolInfo"> </a></span></span>

<span data-ttu-id="2eca4-131">确定网站性能薄弱点的最佳方式是在 SharePoint Online 中设置完全开箱即用的网站集。</span><span class="sxs-lookup"><span data-stu-id="2eca4-131">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online.</span></span> <span data-ttu-id="2eca4-132">通过这种方式，您可以将网站的各个方面与在页面上没有自定义的内容进行比较。</span><span class="sxs-lookup"><span data-stu-id="2eca4-132">This way you can compare all the various aspects of your site with what you would get with no customization on the page.</span></span> <span data-ttu-id="2eca4-133">OneDrive for Business 主页是一个不太可能具有任何自定义项的单独网站集的一个很有用的示例。</span><span class="sxs-lookup"><span data-stu-id="2eca4-133">The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="2eca4-134">查看 SharePoint 响应头信息</span><span class="sxs-lookup"><span data-stu-id="2eca4-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="2eca4-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="2eca4-135"><a name="F12ToolInfo"> </a></span></span>

<span data-ttu-id="2eca4-136">在 SharePoint Online 中，您可以访问发送回每个文件的响应头中的浏览器的信息。</span><span class="sxs-lookup"><span data-stu-id="2eca4-136">In SharePoint Online, you can access the information that is sent back to the browser in the response header for each file.</span></span> <span data-ttu-id="2eca4-137">诊断性能问题最有用的值是**SPRequestDuration**，它显示请求对服务器进行处理的时间量。</span><span class="sxs-lookup"><span data-stu-id="2eca4-137">The most useful value for diagnosing performance issues is **SPRequestDuration**, which displays the amount of time that the request took on the server to be processed.</span></span> <span data-ttu-id="2eca4-138">这有助于确定请求是否非常繁重且占用大量资源。</span><span class="sxs-lookup"><span data-stu-id="2eca4-138">This can help determine if the request is very heavy and resource intensive.</span></span> <span data-ttu-id="2eca4-139">这是您对服务器为页面提供服务所需的最大的洞察力。</span><span class="sxs-lookup"><span data-stu-id="2eca4-139">This is the best insight you have into how much work the server is doing to serve the page.</span></span>

### <a name="to-view-sharepoint-response-header-information"></a><span data-ttu-id="2eca4-140">查看 SharePoint 响应头信息</span><span class="sxs-lookup"><span data-stu-id="2eca4-140">To view SharePoint response header information</span></span>
  
1. <span data-ttu-id="2eca4-141">确保已安装 F12 工具。</span><span class="sxs-lookup"><span data-stu-id="2eca4-141">Ensure that you have the F12 tools installed.</span></span> <span data-ttu-id="2eca4-142">有关下载和安装这些工具的详细信息，请参阅[F12 工具中的新增功能](https://go.microsoft.com/fwlink/p/?LinkId=522545)。</span><span class="sxs-lookup"><span data-stu-id="2eca4-142">For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>

2. <span data-ttu-id="2eca4-143">在 F12 工具的 "**网络**" 选项卡上，按绿色的 "播放" 按钮以加载页面。</span><span class="sxs-lookup"><span data-stu-id="2eca4-143">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span>

3. <span data-ttu-id="2eca4-144">单击工具返回的 .aspx 文件之一，然后单击 "**详细信息**"。</span><span class="sxs-lookup"><span data-stu-id="2eca4-144">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span>

    ![显示响应头的详细信息](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="2eca4-146">单击 "**响应头**"。</span><span class="sxs-lookup"><span data-stu-id="2eca4-146">Click **Response headers**.</span></span>

    ![显示响应头的 URL 的图表](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="2eca4-148">SharePoint Online 中导致性能问题的原因是什么？</span><span class="sxs-lookup"><span data-stu-id="2eca4-148">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="2eca4-149"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="2eca4-149"><a name="F12ToolInfo"> </a></span></span>

<span data-ttu-id="2eca4-150">[SharePoint Online 的文章导航选项](navigation-options-for-sharepoint-online.md)显示了使用 SPRequestDuration 值来确定复杂的结构导航导致页面在服务器上进行处理的时间较长的示例。</span><span class="sxs-lookup"><span data-stu-id="2eca4-150">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server.</span></span> <span data-ttu-id="2eca4-151">通过为基线网站（而不是自定义）获取值，可以确定是否有任何给定的文件需要很长时间才能加载。</span><span class="sxs-lookup"><span data-stu-id="2eca4-151">By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load.</span></span> <span data-ttu-id="2eca4-152">[SharePoint Online 的导航选项](navigation-options-for-sharepoint-online.md)中使用的示例是主要 .aspx 文件。</span><span class="sxs-lookup"><span data-stu-id="2eca4-152">The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file.</span></span> <span data-ttu-id="2eca4-153">该文件包含为您的页面加载运行的大部分 ASP.NET 代码。</span><span class="sxs-lookup"><span data-stu-id="2eca4-153">That file contains most of the ASP.NET code that runs for your page load.</span></span> <span data-ttu-id="2eca4-154">根据您使用的网站模板，可以启动 .aspx、default.aspx、default.aspx 或其他名称（如果自定义主页）。</span><span class="sxs-lookup"><span data-stu-id="2eca4-154">Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page.</span></span> <span data-ttu-id="2eca4-155">如果此数字比您的基准网站大得多，则表明页面中存在导致性能问题的复杂内容。</span><span class="sxs-lookup"><span data-stu-id="2eca4-155">If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span>
  
<span data-ttu-id="2eca4-156">确定了特定于网站的问题后，建议的方法是找出导致性能不佳的原因是消除了所有可能的原因（如页面自定义），然后将它们逐个添加回网站。</span><span class="sxs-lookup"><span data-stu-id="2eca4-156">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one.</span></span> <span data-ttu-id="2eca4-157">在删除了足够的自定义项后，页面的运行状况很好后，即可逐个添加特定的自定义项。</span><span class="sxs-lookup"><span data-stu-id="2eca4-157">Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="2eca4-158">例如，如果您有一个非常复杂的导航，请尝试将导航更改为 "不显示子网站"，然后检查开发人员工具以查看这是否会产生差异。</span><span class="sxs-lookup"><span data-stu-id="2eca4-158">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference.</span></span> <span data-ttu-id="2eca4-159">或者，如果您有大量的内容汇总，请尝试从页面中删除它们，并查看这是否会提高内容。</span><span class="sxs-lookup"><span data-stu-id="2eca4-159">Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things.</span></span> <span data-ttu-id="2eca4-160">如果您消除了所有可能的原因并一次将其重新添加到一个中，则可以轻松地确定哪些功能是最大的问题，然后再向解决方案中进行操作。</span><span class="sxs-lookup"><span data-stu-id="2eca4-160">If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
