---
title: 使用 SharePoint Online 的页面诊断工具
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/18/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
f1.keywords:
- NOCSH
description: 使用 SharePoint 工具的页面诊断工具，针对预定义的一组性能条件对 SharePoint Online 新式门户和经典发布页面进行分析。
ms.openlocfilehash: 191db3db459f12a922c47844af72511cc9bf2544
ms.sourcegitcommit: 27172140051c31f5cd3f28ffb4282669d561549a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "42155584"
---
# <a name="use-the-page-diagnostics-for-sharepoint-tool"></a>使用 "网页诊断程序" SharePoint 工具

本文介绍如何使用**sharepoint 工具的页面诊断工具**根据预定义的一组性能条件分析 sharepoint Online 新式和经典网站页面。  

>[!TIP]
>已**发布工具的版本 2.0.2**。 版本**2.0.0**和更高版本包括对新式页面以及经典网站页面的支持。 如果您不确定使用的是哪个版本的工具，则可以选择 "**关于**" 链接或省略号（...）来验证您的版本。 使用工具时，请始终更新到最新版本。

SharePoint 工具的页面诊断工具是新 Microsoft Edge （https://www.microsoft.com/edge)和同时分析 SharePoint Online 新式门户和经典发布网站页面的 Chrome 浏览器）的浏览器扩展。 此工具仅适用于 SharePoint Online，不能用于 SharePoint 系统页面。

该工具为每个分析页面生成一个报告，该页面显示页面如何针对预定义的规则集执行，并在测试的结果超出比较基准值时显示详细信息。 SharePoint Online 管理员和设计人员可以使用该工具解决性能问题，并确保新页面在发布之前进行了优化。

页面诊断工具专门用于分析 SharePoint 网站页面，而不是系统页面，如*allitems.aspx*或*default.aspx*。 如果尝试在系统页面或任何其他非网站页面上运行该工具，则会收到一条错误消息，提示该工具不能针对该类型的页面运行。

![必须在 SharePoint 页面上运行](media/page-diagnostics-for-spo/pagediag-Error-StartPage.png)

这不是工具中的错误，因为评估库或系统页面时没有任何价值。 请导航到 SharePoint 网站页面以使用该工具。 如果此错误发生在 SharePoint 页面上，请检查母版页以确保尚未删除 SharePoint metatags。

若要提供有关该工具的反馈，请选择该工具右上角的省略号，然后选择 "[提供反馈](https://go.microsoft.com/fwlink/?linkid=874109)"。

![提供反馈](media/page-diagnostics-for-spo/pagediag-feedback.png)
  
## <a name="install-the-page-diagnostics-for-sharepoint-tool"></a>安装用于 SharePoint 工具的页面诊断程序

本节中的安装过程将适用于 Chrome 和 Microsoft Edge 浏览器。

> [!IMPORTANT]
> Microsoft 不会读取由 SharePoint 工具的页面诊断功能分析的数据或页面内容，我们不会捕获任何个人信息、网站或下载信息。 该工具仅记录到 Microsoft 的可识别信息是租户名称、失败的规则数以及运行该工具的日期和时间。 Microsoft 使用此信息来更好地了解新式门户和发布网站使用率趋势和常见性能问题。

1. 为**Microsoft Edge** [（边缘扩展）](https://microsoftedge.microsoft.com/addons/detail/ocemkolpnamjcacndljdfmhlpcaoipji)或**chrome** [（Chrome Extension）](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi)的 SharePoint 工具安装页面诊断工具。 请查看 store 中的 "说明" 页上提供的用户隐私策略。 向浏览器添加工具时，您将看到以下权限通知。

    ![扩展权限](media/page-diagnostics-for-spo/pagediag-add-to-edge.png)

    由于页面上的 web 部件和自定义项可能包含来自 SharePoint 之外的位置的内容，因此此通知已生效。 这意味着，在单击 "开始" 按钮时，该工具将读取请求和响应，并且仅针对运行该工具的活动 SharePoint 选项卡。 此信息由 web 浏览器在本地捕获，可通过工具的 "_网络跟踪_" 选项卡中的 "**导出到 JSON** " 或 "**导出到 HAR** " 按钮供您使用。**这些信息不会发送给 Microsoft 或由 Microsoft 捕获**。 （此工具尊重[此处](https://go.microsoft.com/fwlink/p/?linkid=857875)可访问的 Microsoft 隐私策略。）

    "_管理您的下载_" 权限涵盖了该工具的**导出到 JSON**功能的使用。 在您的组织外部共享 JSON 文件之前，请按照贵公司自己的隐私准则进行操作，因为结果中包含 Url，并且可以归类为 PII （个人身份信息）。
1. 如果要在 Incognito 或 InPrivate 模式中使用该工具，请按照浏览器的过程操作：
    1. 在 Microsoft Edge 中，导航到 "**扩展**" 或在 URL 栏中键入 " _edge://extensions_ "，然后选择扩展的 "**详细信息**"。 在扩展设置中，选中 "**允许在 InPrivate 中**" 复选框。
    1. 在 Chrome 中，导航到 "**扩展**" 或在 URL 栏中键入 " _chrome://extensions_ "，然后选择扩展的**详细信息**。 在 "扩展设置" 中，选择 "**允许在 Incognito 中**" 滑块。
1. 导航到 SharePoint Online 上您要查看的 SharePoint 网站页面。 我们允许对页面上的项目进行 "延迟加载";因此，该工具不会自动停止（这是设计以适应所有页面加载方案）。 若要停止收集，请选择 "**停止**"。 在停止数据收集之前，请确保页面加载已完成，否则将只捕获部分跟踪。
1. 单击扩展的工具栏按钮 ![SharePoint 徽标的页面诊断](media/page-diagnostics-for-spo/pagediag-icon32.png) 加载工具时，将显示以下扩展名弹出窗口：

    ![页面诊断工具弹出菜单](media/page-diagnostics-for-spo/pagediag-Landing.png)

选择 "**开始**" 以开始收集数据以供分析。

## <a name="what-youll-see-in-the-page-diagnostics-for-sharepoint-tool"></a>您将在 SharePoint 的页面诊断工具中看到的内容

1. 单击工具右上角的省略号（...）以查找以下链接：
   1. "**其他资源**" 链接提供了有关该工具的一般指导和详细信息，其中包括返回到本文的链接。
   1. "**提供反馈**" 链接提供了指向_SharePoint 网站和协作用户语音_网站的链接。
   1. "**关于**" 链接包括当前安装的工具版本以及指向该工具的第三方通知的直接链接。  
1. **相关 ID、SPRequestDuration、SPIISLatency**、**页面加载时间**和**URL**详细信息都是信息，可用于以下几个用途。

    ![页面诊断详细信息](media/page-diagnostics-for-spo/pagediag-details.PNG)

   - **CorrelationID**是使用 Microsoft 支持时的重要元素，因为它允许他们收集特定页面的其他诊断数据。
   - **SPRequestDuration**是 SharePoint 处理页面所用的时间。 结构化导航、大型图像、大量 API 调用都可能会导致更长的持续时间。
   - **SPIISLatency**是在 SharePoint Online 开始加载页面时所用的时间（以毫秒为单位）。 此值不包括 web 应用程序响应所用的时间。
   - **页面加载时间**是在请求收到并在浏览器中呈现响应时，页面记录的总时间。 此值受多种因素的影响，包括网络延迟、计算机的性能以及浏览器加载页面所需的时间。
   - **页面 URL** （统一资源定位器）是当前页面的 web 地址。

1. "[**诊断测试**](#how-to-use-the-diagnostic-tests-tab)" 选项卡将分析结果显示为三个类别;**无需任何操作**、**改进机会**和**注意事项**。 每个测试结果由其中一个类别中的项表示，如下表中所述：

    |类别  |颜色  |说明  |
    |---------|---------|---------|
    |**注意事项** |红色 |测试结果不在比较基准值的范围之内，因而会影响页面性能。 遵循更正指南。|
    |**改进机会** |黄色 |测试结果不在比较基准值的范围之内，可能会引起性能问题。 可能应用特定于测试的条件。|
    |**不需要执行任何操作** |绿色 |测试结果在测试的比较基准值范围内。|

    ![页面诊断](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

1. "[**网络跟踪**](#how-to-use-the-network-trace-tab)" 选项卡提供有关页面生成请求和响应的详细信息。

## <a name="how-to-use-the-diagnostic-tests-tab"></a>如何使用 "诊断测试" 选项卡

在使用 SharePoint 工具的页面诊断工具分析 SharePoint 新式门户或经典发布网站页面时，将使用预定义的规则对结果进行分析，这些规则将比较比较基准值和 "**诊断测试**" 选项卡中显示的结果。某些测试的规则可能对新式门户和经典发布网站使用不同的比较基准值，具体取决于两者之间的特定性能特征不同。

"**改善机会**" 或 "**注意事项**" 类别中显示的测试结果指明应针对建议的做法评审的区域，并且可以选择此选项以显示有关结果的其他信息。 每个项目的详细信息包括一个 "_了解更多_" 链接，它将直接转到与测试相关的相应指南。 "**无需任何操作**" 类别中显示的测试结果指示符合相关规则，并且在选中时不显示其他详细信息。

"诊断测试" 选项卡中的信息不会告诉您如何设计页面，但会突出显示可能影响页面性能的因素。 某些页面功能和自定义对页面性能的影响不可避免，应检查它们的可能修正或从页面中省略（如果它们的影响是重大的）。

红色或黄色结果也可能表示刷新数据过于频繁的 web 部件。 例如，公司新闻不会每秒更新一次，但自定义 web 部件通常是为每秒提取最新新闻，而不是实施可以改善总体用户体验的缓存元素。 在页面上添加 web 部件时，请注意，通过评估每个可用参数的值来降低它们的性能影响，以确保将其设置为适合其预期目的的简单方法。

>[!NOTE]
>如果经典工作组网站未启用发布功能，则无法使用 Cdn。 当您在这些网站上运行此工具时，CDN 测试应会失败，并且可以忽略，但其余所有测试均适用。 SharePoint 发布功能的其他功能可能会增加页面加载时间，因此不应只为允许 CDN 功能而启用此功能。

>[!IMPORTANT]
>将定期添加和更新测试规则，请参阅最新版本的工具，了解有关当前规则和测试结果中包含的特定信息的详细信息。 您可以通过管理您的扩展来验证版本，扩展将告知是否有更新可用。

## <a name="how-to-use-the-network-trace-tab"></a>如何使用网络跟踪选项卡

"**网络跟踪**" 选项卡提供了用于生成页面的两个请求的详细信息以及从 SharePoint 收到的响应。

1. **查找标记为红色的项目加载时间**。 每个请求和响应都采用颜色编码，以指示其对总体页面性能的影响使用以下延迟指标：
    - 绿色： \< 500ms
    - 黄色： 500-1000ms
    - 红色： \> 1000ms

    ![网络跟踪](media/page-diagnostics-for-spo/pagediag-networktrace-red.png)

    在上面显示的图像中，红色项目与默认页面相关。 除非在1000ms （小于1秒）内\<加载页面，否则它将始终显示红色。

2. **测试项加载时间**。 在某些情况下，由于浏览器已缓存这些项，因此不会有任何时间或颜色指示器。 若要正确测试此设置，请打开页面，清除浏览器缓存，然后单击 "**启动**"，这将强制 "冷" 页面加载，并成为初始页面加载的真正反映。 此操作应与 "感兴趣" 页面加载进行比较，这将有助于确定要在页面上缓存的项目。

3. **与可帮助调查问题的其他人共享相关详细信息**。 若要与您的开发人员或技术支持人员共享工具中提供的详细信息或信息，请单击 "**导出到 JSON** " （如上图所示）。 这将使您能够通过 JSON 文件查看器进行查看，从而下载结果。

    如果你已选择使用预览功能，请将*导出到 har* ，导出类型将显示为 "**导出到 har**"。

    ![网络跟踪](media/page-diagnostics-for-spo/pagediag-NetworkTraceHAR.PNG)

> [!IMPORTANT]
> 这些结果包含 Url 和可归类为 PII （个人身份信息）的 Url。 在分发该信息之前，请确保遵守组织的准则。

## <a name="engaging-with-microsoft-support"></a>与 Microsoft 支持人员接洽

我们已加入**Microsoft 支持级别功能**，仅当直接在支持案例中工作时才能使用此功能。 如果使用此功能，则在不支持团队合作的情况下使用时不会对你带来任何好处，并且可以使页面的执行速度显著降低。 在工具中使用此功能时，在将其他信息添加到服务中的日志记录中时，不会提供任何其他信息。

不显示任何更改，只是系统会通知您已启用该功能，并且您的页面性能会显著下降2-3 倍的性能，同时启用速度降低。 它将仅与特定页面和活动会话相关。 出于此原因，应谨慎使用，仅在主动参与支持时使用。

### <a name="to-enable-the-microsoft-support-level-feature"></a>启用 Microsoft 支持级别功能

1. 打开 "页面诊断" "SharePoint 工具"。
2. 在键盘上，按**ALT + Shift-L**。 这将显示 "**启用支持日志记录**" 复选框。
3. 选中 "" 复选框，然后单击 "**开始**" 以重新加载页面并生成详细日志记录。

    ![启用了支持选项](media/page-diagnostics-for-spo/pagediag-support.png)
  
    应注意 CorrelationID （显示在工具顶部），并将其提供给支持代表，以使其能够收集有关诊断会话的其他信息。

## <a name="related-topics"></a>相关主题

[优化 SharePoint Online 性能](tune-sharepoint-online-performance.md)

[优化 Office 365 性能](tune-office-365-performance.md)

[内容分发网络](content-delivery-networks.md)
