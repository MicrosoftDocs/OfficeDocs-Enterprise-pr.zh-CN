---
title: Office 365 的性能疑难解答计划
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
ms.collection:
- M365-security-compliance
- Ent_O365
description: 您需要了解在 SharePoint Online、OneDrive for business、Exchange Online 或 Skype for business Online 和您的客户端计算机之间识别和修复滞后、挂起和降低性能的步骤吗？ 在致电支持之前，本文可帮助您解决 Office 365 性能问题，甚至修复一些最常见的问题。
ms.openlocfilehash: e0117cebc80acbd2b29ce319002dbd3dccafb764
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031127"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a>Office 365 的性能疑难解答计划

您需要了解在 SharePoint Online、OneDrive for business、Exchange Online 或 Skype for business Online 和您的客户端计算机之间识别和修复滞后、挂起和降低性能的步骤吗？ 在致电支持之前，本文可帮助您解决 Office 365 性能问题，甚至修复一些最常见的问题。
  
本文实际上是一个示例操作计划，可用于在发生性能问题时捕获有价值的数据。 本文还包括一些主要问题。

如果你不熟悉网络性能，并且想要制定长期计划来监视客户端计算机和 Office 365 之间的性能，请查看[Office 365 性能调整和故障排除-管理员和 IT 专业人员](performance-tuning-using-baselines-and-history.md)。
  
## <a name="sample-performance-troubleshooting-action-plan"></a>性能故障排除操作计划示例

此操作计划包含两个部分;准备阶段和日志记录阶段。 如果现在遇到性能问题，并且需要进行数据收集，则可以立即开始使用此计划。
  
### <a name="prepare-the-client-computer"></a>准备客户端计算机
  
- 查找可能会再现性能问题的客户端计算机。 此计算机将在故障排除过程中使用。
- 记下导致性能问题发生的步骤，以便在测试时做好准备。
- 安装用于收集和录制信息的工具：
  - 安装[Netmon 3.4](https://www.microsoft.com/download/details.aspx?id=4865) （或使用等效的网络跟踪工具）。
  - 安装[HTTPWatch](https://www.httpwatch.com/download/)的免费基本版本（或使用等效的网络跟踪工具）。
  - 使用屏幕录制器或运行 Windows Vista 及更高版本附带的步骤记录器（PSR），以保留在测试过程中执行的步骤的记录。

### <a name="log-the-performance-issue"></a>记录性能问题
  
- 关闭所有多余的 Internet 浏览器。
- 启动步骤记录器或另一个屏幕录制器。
- 启动 Netmon 捕获（或网络跟踪工具）。
- 通过在命令行中键入 ipconfig/flushdns. 来清除客户端计算机上的 DNS 缓存
- 启动新的浏览器会话并打开 HTTPWatch。
- 可选：如果要测试 Exchange Online，请从 Office 365 管理控制台运行 Exchange 客户端性能分析器工具。
- 重现导致性能问题的确切步骤。
- 停止 Netmon 或其他工具的跟踪。
- 在命令行中，键入以下命令并按 ENTER，以运行指向 Office 365 订阅的跟踪路由：

  ``` cmd
  tracert <subscriptionname>.onmicrosoft.com
  ```

- 停止步骤记录器并保存视频。 请务必包括捕获的日期和时间以及它是正常还是坏的性能。
- 保存跟踪文件。 此外，请务必包含捕获的日期和时间，以及它是正常还是坏的性能。

如果您不熟悉本文中提到的工具的运行，请不要担心，因为我们在下一步提供这些步骤。 如果您习惯于执行此类网络捕获，则可以跳转到[如何收集比较基准](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines)（描述了筛选和读取日志）。
  
### <a name="flush-the-dns-cache-first"></a>先刷新 DNS 缓存

为什么？ 通过刷新 DNS 缓存，你将使用干净的盖板启动测试。 通过清除缓存，您要将 DNS 解析程序内容重置为最新的条目。 请注意，刷新不会删除主机文件条目。 如果频繁使用主机文件条目，则应将这些条目复制到另一个目录中的文件中，然后清空主机文件。
  
#### <a name="flush-your-dns-resolver-cache"></a>刷新 DNS 解析器缓存
  
1. 打开命令提示符（"**开始** \> **运行** \> **cmd** or **Windows key** \> **cmd**"）。
2. 键入下面的命令，并按 Enter：

    ``` cmd
    ipconfig /flushdns
    ```

## <a name="netmon"></a>Netmon

Microsoft 网络监控工具（[Netmon](https://www.microsoft.com/download/details.aspx?id=4865)）分析在网络上的计算机之间传递的数据包（即流量）。 通过使用 Netmon 来跟踪使用 Office 365 的流量，您可以捕获、查看和读取数据包标头、标识介入的设备、检查网络硬件上的重要设置、查找丢弃的数据包，并遵循公司中计算机之间的流量流量。网络和 Office 365。 由于流量的实际正文已加密，即它（通过 SSL/TLS 在端口443上传输，无法读取正在发送的文件。 而是获取对数据包所采用的路径的未筛选跟踪，从而帮助您跟踪问题行为。
  
请务必现在不应用筛选器。 而是在停止跟踪和保存之前，先执行步骤并演示问题。
  
安装 Netmon 3.4 后，打开该工具并执行以下步骤：
  
### <a name="take-a-netmon-trace-and-reproduce-the-issue"></a>获取 Netmon 跟踪并再现问题
  
1. 启动 Netmon 3.4。
**起始**页上有三个窗格： "**最近捕获**"、"**选择网络**" 和 " **Microsoft 网络监视器3.4 入门"。通知**。 "选择网络" 面板还将提供可从中捕获的默认网络的列表。 确保在此处选择了网卡。

2. 单击**起始**页顶部的 "**新建捕获**"。 这将在 "**起始**页" 选项卡（称为**捕获 1**）旁边添加一个新选项卡。
![显示新的 "捕获"、"启动" 和 "停止" 按钮的 Netmon 用户界面。](media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)

3. 若要获取简单的捕获，请单击工具栏上的 "**开始**"。

4. 重现出现性能问题的步骤。

5. 单击 "**停止** \> **文件** \> **另存为**"。 请记住，请提供时区的日期和时间，并注明它是否演示了坏的或好的性能。

## <a name="httpwatch"></a>HTTPWatch

[HTTPWatch](https://www.httpwatch.com/download/)的费用和免费版本。 免费的基本版本涵盖了此测试所需的一切。 HTTPWatch 在浏览器窗口中直接监视网络流量和页面加载时间。 HTTPWatch 是以图形方式描述性能的 Internet Explorer 的插件。 可以在 HTTPWatch Studio 中保存和查看分析。
  
> [!NOTE]
> 如果您使用其他浏览器（如 Firefox、Google Chrome 或无法在 Internet Explorer 中安装 HTTPWatch，则打开一个新的浏览器窗口并在键盘上按 F12。 您应该会看到浏览器底部的 "开发工具" 弹出窗口。 如果使用了 Opera，请按 CTRL + SHIFT + I for Web Inspector，然后单击 "**网络**" 选项卡并完成下面所述的测试。 信息会略有不同，但加载时间仍将以毫秒为单位显示。 > HTTPWatch 对 SharePoint Online 页面加载时间的问题也非常有用。
  
### <a name="run-httpwatch-and-reproduce-the-issue"></a>运行 HTTPWatch 并再现问题
  
HTTPWatch 是一个浏览器插件，因此在浏览器中公开此工具会因 Internet Explorer 的每个版本而略有不同。 通常情况下，您可以在 Internet Explorer 浏览器中的命令栏下找到 HTTPWatch。 如果您在浏览器窗口中看不到 HTTPWatch 插件，请单击 "**帮助** \> **"，或**在 Internet explorer 的更高版本中查看浏览器的版本，然后单击齿轮符号和 "**关于 internet explorer**"。 若要启动**命令**栏，请在 Internet Explorer 中右键单击菜单栏，然后单击 "**命令栏**"。

过去，HTTPWatch 已与命令和浏览器栏相关联，因此在安装后，如果您不立即看到图标（即使在重新启动后），请检查**工具**以及您的工具栏上的图标。 请注意，可以自定义工具栏，并且可以向其添加选项。

![显示 HTTPWatch 图标的 Internet Explorer 的命令工具栏。](media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)
  
1. 在 Internet Explorer 浏览器窗口中启动 HTTPWatch。 它将停靠在该窗口底部的浏览器中。 单击 "**记录**"。

2. 重现性能问题中涉及的确切步骤。 单击 HTTPWatch 中的 "**停止**" 按钮。

3. **保存**HTTPWatch 或**通过电子邮件发送**。 请记住为该文件命名，以使其包含日期和时间信息，并指示您的监视是否包含正常或坏性能的演示。

![HTTPWatch，显示 Office 365 主页的页面加载的“网络”选项卡。](media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)

此屏幕截图来自 HTTPWatch 的专业版。 您可以打开在具有专业版的计算机上的基本版本中拍摄的跟踪，并在其中阅读。 可通过该方法在跟踪中获取额外信息。

## <a name="problem-steps-recorder"></a>问题步骤记录器

通过步骤记录器或 PSR，可以在出现问题时记录这些问题。 它是一个非常有用的工具，并且运行起来非常简单。
  
### <a name="run-problem-steps-recorder-psrexe-to-record-your-work"></a>运行问题步骤记录器（PSR）记录您的工作
  
1. 使用 "**启动** \> **运行** \>类型" **PSR** \> **"确定"**，或者单击 " **Windows 键** \>类型**PSR** \> "，然后按 enter。

2. 当出现小型 PSR 窗口时，请单击 "**开始记录**" 并重现再现性能问题的步骤。 您可以根据需要添加注释，方法是单击 "**添加注释**"。

3. 完成这些步骤后，单击 "**停止录制**"。 如果性能问题是页面呈现，请在停止录制之前等待页面呈现。

4. 单击“**保存**”。

![步骤记录器或 PSR 的屏幕截图。](media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)
  
为您记录日期和时间。 这会及时将您的 PSR 链接到 Netmon 跟踪和 HTTPWatch，并有助于精确的故障排除。 PSR 记录中的日期和时间可以显示在 URL 的登录和浏览和管理网站的部分呈现之间传递的分钟数，例如。
  
## <a name="read-your-traces"></a>阅读跟踪

无法通过一篇文章了解有关网络和性能疑难解答的所有内容。 在性能方面取得出色的体验，并了解网络的工作原理以及通常的执行情况。 但可以对首要问题列表进行舍入，并显示工具如何使您更轻松地消除最常见的问题。
  
如果您想要为您的 Office 365 网站挑选阅读网络跟踪的技能，则没有更好的教师定期创建页面加载的跟踪，并获得阅读体验。 例如，当你有机会时，请加载 Office 365 服务并跟踪进程。 筛选 DNS 通信的跟踪，或在 FrameData 中搜索您浏览的服务的名称。 扫描跟踪以了解服务加载时发生的步骤。 这将帮助您了解正常页面加载的外观，在进行故障排除的情况下，尤其是在性能方面，比较好的对坏跟踪可能会很多。
  
Netmon 在显示筛选器字段中使用 Microsoft Intellisense。 智能感知或智能代码完成是指在一段时间内键入句点和所有可用选项的技巧显示在下拉选项框中。 例如，如果你担心 TCP 窗口缩放，你可以通过这种方式查找筛选器（如`.protocol.tcp.window < 100`）。
  
![显示 "显示筛选器" 字段使用 intellisense 的 Netmon 屏幕截图。](media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)
  
Netmon 跟踪可以在其中包含大量流量。 如果你不熟悉阅读这些文件，可能会在首次打开跟踪时淹没过重。 要做的第一件事就是将来自跟踪的背景噪音的信号分开。 您针对 Office 365 进行了测试，这就是您想要查看的流量。 如果您用于浏览跟踪，则可能不需要此列表。
  
您的客户端和 Office 365 之间的流量通过 TLS 传播，这意味着在常规 Netmon 跟踪中，流量的正文将被加密且不可读。 您的性能分析不需要知道数据包中的信息的细节。 但是，它非常关注数据包标头及其包含的信息。
  
### <a name="tips-to-get-a-good-trace"></a>获取正确跟踪的提示
  
- 了解客户端计算机的 IPv4 或 IPv6 地址的值。 您可以在命令提示符下，键入**IPConfig** ，然后按 enter 获取。 了解此地址将使您能够一目了然地了解跟踪中的流量是否直接涉及客户端计算机。 如果有已知代理，请将其 ping 并获取其 IP 地址。

- 刷新 DNS 解析器缓存，并在可能的情况下关闭运行测试的所有浏览器之外的其他所有浏览器。 如果您无法执行此操作，例如，如果支持使用一些基于浏览器的工具来查看您的客户端计算机的桌面，请准备筛选您的跟踪。

- 在繁忙跟踪中，找到您正在使用的 Office 365 服务。 如果以前从未或很少看到你的流量，则在将性能问题与其他网络噪音区分开来时，这是一个非常有用的步骤。 有几种方法可以实现此目的。 在测试之前，您可以将_ping_或_PsPing_用于特定服务的 URL （`ping outlook.office365.com` `psping -4 microsoft-my.sharepoint.com:443`例如）。 您还可以轻松地在 Netmon 跟踪（按进程名称）中找到 ping 或 PsPing。 这将为您提供开始查看的位置。

如果在出现问题时仅使用 Netmon 跟踪，那也没关系。 若要自己定位，请使用类似`ContainsBin(FrameData, ASCII, "office")`于`ContainsBin(FrameData, ASCII, "outlook")`或的筛选器。 您可以从跟踪文件中记录您的帧编号。 您可能还需要将 "_帧摘要_" 窗格一直滚动到右侧，并查找 "会话 ID" 列。 此特定对话的 ID 指示有一个数字，您还可以在以后记录和查看。 请记住在应用任何其他筛选之前删除此筛选器。

> [!TIP]
> Netmon 有许多有用的内置筛选器。 尝试_显示_筛选窗格顶部的 "**加载筛选器**" 按钮。
  
![在客户端计算机上的命令行中使用 PSPing 查找您的 IP。](media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)
  
![来自客户端的 Netmon 跟踪通过筛选器 TCP 显示相同的 PSPing 命令。标记（Syn = = 1）。](media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)
  
熟悉您的流量，并了解如何查找所需的信息。 例如，了解如何确定跟踪中的哪个数据包具有对所使用的 Office 365 服务的第一个引用（如 "Outlook"）。

以 Office 365 Outlook Online 为例，流量的开始部分如下所示：
  
- 具有匹配 QueryIDs 的 outlook.office365.com 的 DNS 标准查询和 DNS 响应。 请务必注意此转换的时间偏移量，以及 Office 365 全局 DNS 发送请求进行名称解析的位置。 理想情况下，尽量在本地进行，而不是世界的一半。

- 其状态报告被永久移动的 HTTP GET 请求（301）

- X-RWS-VERSION 流量包括 X-RWS-VERSION Connect 请求和连接答复。 （这是远程 Winsock 为你建立连接。）

- TCP SYN 和 TCP SYN/ACK 对话。 此对话中的很多设置会影响性能。

- 然后，一系列 TLS： tls 流量，即 TLS 握手和 TLS 证书对话发生的位置。 （请记住，数据是通过 SSL/TLS 进行加密的。）

流量的所有部分都很重要且已连接，但跟踪量的较小部分包含有关性能故障排除的信息。因此，我们将重点放在这些区域。 此外，由于我们在 Microsoft 完成了足够多的 Office 365 性能故障排除，因此，我们将重点介绍这些问题，以及如何使用我们必须将其排除在下一步下的各种工具。
  
如果尚未将其安装就绪，则下面的矩阵将使用多个工具。 如果可能。 向安装点提供了链接。 此列表包含常见的网络跟踪工具，如[Netmon](https://www.microsoft.com/download/details.aspx?id=4865)和[Wireshark](https://www.wireshark.org/)，但使用您熟悉的任何跟踪工具，并且您习惯于筛选网络流量。 在测试时，请记住：
  
- *关闭浏览器并在仅运行一个浏览器的情况下进行测试*-这将减少捕获的总体流量。 它可用于较差的跟踪。
- *在客户端计算机上刷新您的 DNS 解析器缓存*-这将在你开始获取捕获时为你提供干净的盖板，以获取更干净的跟踪。

## <a name="common-issues"></a>常见问题

你可能会遇到的一些常见问题以及如何在网络跟踪中查找这些问题。

### <a name="tcp-windows-scaling"></a>TCP 窗口缩放

在 SYN-SYN/ACK 中找到。 旧的或过时的硬件可能无法利用 TCP windows 缩放。  如果没有正确的 TCP 窗口缩放设置，TCP 标头中的默认16位缓冲区将以毫秒为单位填充。  在客户端收到已收到原始数据的确认后，流量将无法继续发送，从而导致延迟。

#### <a name="tools"></a>工具

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>要查找的内容

在网络跟踪中查找 SYN-SYN/ACK 流量。  在 Netmon 中，使用类似`tcp.flags.syn == 1`的筛选器。 此筛选器在 Wireshark 中是相同的。  

![在 Netmon 或 Wireshark 中筛选两个工具的 Syn 数据包： TCP。标记（Syn = = 1）。](media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)

请注意，对于每个 SYN，都会在相关确认（SYN/ACK）的目标端口（Udp.dstport）中匹配一个源端口（Udp.srcport）编号。

若要查看你的网络连接使用的 Windows 缩放值，请先展开 SYN，然后再展开相关的 SYN/ACK。  

![显示如何将 Udp.srcport 匹配到跟踪中的 Udp.dstport 的图形，以获取时间增量。](media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)  

### <a name="tcp-idle-time-settings"></a>TCP 空闲时间设置

在过去，大多数外围网络都配置为暂时连接，这意味着空闲连接通常会终止。 在超过100到300秒的代理和防火墙可以终止空闲的 TCP 会话。 这对于 Outlook Online 来说是有问题的，因为它会创建和使用长期连接（无论它们是否处于空闲状态）。  

当代理或防火墙设备终止连接时，将不会通知客户端，并且尝试使用 Outlook Online 意味着客户端计算机将在 revive 连接之前尝试进行新的连接，然后再创建一个新的连接。 在页面加载时，您可能会看到产品挂起、提示或降低性能。

#### <a name="tools"></a>工具

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>要查找的内容

在 Netmon 中，查看往返行程的 "时间偏移量" 字段。 往返行程是客户端向服务器发送请求并接收响应的时间。 在客户端和传出点之间进行检查（例如 客户端-\> -代理）或客户端到 Office 365 （客户端-\> ---------office 365）。 您可以在多种类型的数据包中看到此情况。

例如，Netmon 中的筛选器可能如下所示`.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`，或在 Wireshark 中`ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`。  

> [!TIP]
> 不知道跟踪中的 IP 地址是否属于您的 DNS 服务器？ 请尝试在命令行上进行查找。 单击 "**开始** \> **运行** \> " 并键入**cmd**，或按**Windows 键** \>并键入**cmd**。 在提示符处，键入`nslookup <the IP address from the network trace>`。 若要进行测试，请对自己的计算机的 IP 地址使用 nslookup。 > 若要查看 Microsoft IP 范围的列表，请参阅[Office 365 url 和 IP 地址范围](https://technet.microsoft.com/library/hh373144.aspx)。

如果出现问题，则预计会出现长时间偏移，在此示例中（Outlook Online），尤其是在 TLS：显示应用程序数据的这一阶段的 TLS 数据包（例如，在 Netmon 中，可以通过`.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`）查找应用程序数据。 您应该会在会话过程中看到进展顺利。 如果您在刷新 Outlook Online 时看到长时间延迟，则可能是由于发送的重置次数过高而导致的。

### <a name="latencyround-trip-time"></a>延迟/往返时间

延迟是一种可根据许多变量（如升级老化设备、向网络中添加大量用户以及网络连接上的其他任务消耗的总体带宽百分比）来更改大量的度量。

在此[网络规划和 "office 365 的性能调整](network-planning-and-performance.md)" 页面中，有适用于 office 365 的带宽计算器。  

需要衡量你的连接速度，还是你的 ISP 连接的带宽？ 尝试此网站（或网站，如网站）： [Speedtest 官方网站](https://www.speedtest.net/)和[Pingtest](https://www.pingtest.net/)。

#### <a name="tools"></a>工具

- Ping
- PsPing
- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>要查找的内容

若要跟踪跟踪中的延迟，您将受益于在 Office 365 中记录了客户端计算机 IP 地址和 DNS 服务器的 IP 地址。 这旨在简化跟踪筛选的目的。 如果通过代理连接，将需要客户端计算机 IP 地址、代理/传出 IP 地址和 Office 365 DNS IP 地址，以使工作更容易。  

发送到 outlook.office365.com 的 ping 请求将告知您接收请求的数据中心的名称，即使 ping*可能*无法连接以发送商标连续 ICMP 数据包。 如果使用 PsPing （用于下载的免费工具），并且特定端口（443），并且可能使用 IPv4 （-4），则会为发送的数据包获取平均往返时间。 这将对 Office 365 服务中的其他 Url （如`psping -4 yourSite.sharepoint.com:443`）执行此操作。 事实上，您可以指定多个 ping 以获取更大的采样示例，请尝试类似`psping -4 -n 20 yourSite-my.sharepoint.com:443`的操作。  

> [!NOTE]
> PsPing 不发送 ICMP 数据包。 通过特定端口对 TCP 数据包执行 ping 操作，以便您可以使用任何已知的打开方式。 在使用 SSL/TLS 的 Office 365 中，尝试将端口：443附加到你的 PsPing。

![显示 ping 解析 outlook.office365.com 的屏幕截图和443的 PSPing 执行相同的操作，同时还报告6.5 毫秒平均 RTT。](media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)

如果在执行网络跟踪时已加载 "执行速度较慢的 Office 365" 页面，则应筛选 Netmon 或`DNS`Wireshark 跟踪。 这是我们要查找的 IPs 之一。  

下面是筛选 Netmon 以获取 IP 地址的步骤（并查看 DNS 延迟）。 此示例使用 outlook.office365.com，但也可以使用 SharePoint Online 租户的 URL （例如，hithere.sharepoint.com）。  

1. Ping URL `ping outlook.office365.com` ，并在结果中记录向其发送 ping 请求的 DNS 服务器的名称和 IP 地址。
2. 网络跟踪打开页面，或执行性能问题的操作，或者，如果你在 ping 上看到过高的延迟，它本身就是网络跟踪。
3. 在 Netmon 中打开跟踪并筛选 DNS （此筛选器也适用于 Wireshark，但区分大小写`-- dns`）。 由于你知道你的 ping 中的 DNS 服务器的名称，因此你也可以在 Netmon 中筛选更多`DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`的 speedily，如下所示：，在 Wireshark DNS 中和 frame 包含 "namnorthwest" 这种情况下。<br/>打开响应数据包，并在 "Netmon**帧详细信息**" 窗口中，单击 " **DNS** " 以展开以获取详细信息。 在 DNS 信息中，您将找到在 Office 365 中请求进入的 DNS 服务器的 IP 地址。 下一步（PsPing 工具）将需要此 IP 地址。 删除筛选器，请右键单击 Netmon 中的 dns 响应（**帧摘要** \> "**查找对话** \> **DNS**"）以查看 DNS 查询和响应并行。
4. 在 Netmon 中，还请注意 DNS 请求和响应之间的时间偏移列。 在下一步中，易于安装和使用的[PsPing](https://technet.microsoft.com/sysinternals/jj729731.aspx)工具非常方便，这是因为 ICMP 通常在防火墙上被阻止，并且 PsPing elegantly 跟踪延迟（以毫秒为单位）。 PsPing 完成到地址和端口的 TCP 连接（在我们的示例中，打开端口443）。
5. 安装 PsPing。
6. 打开命令提示符（启动\> "运行\>类型 Cmd" 或 "Windows \>键类型 cmd"），并将目录更改为您在其中安装 PsPing 的目录以运行 PsPing 命令。 在我的示例中，您可以看到我在 C 的根目录上建立了 ' Perf ' 文件夹。您可以进行相同的快速访问。
7. 键入命令，以便您可以根据早期 Netmon 跟踪（包括端口号）对 Office 365 DNS 服务器的 IP 地址进行 PsPing `psping -n 20 132.245.24.82:445`。 这将为您提供20个 ping 采样和平均延迟在 PsPing 停止时的采样。

如果通过代理服务器转到 Office 365，则步骤略有不同。 您将首先 PsPing 代理服务器，以毫秒为单位获取代理/传出和回退的平均延迟值，然后在代理上运行 PsPing，或者在具有直接 Internet 连接的计算机上运行以获取缺少的值（即 Office 365 和后端）。  

如果您选择从代理运行 PsPing，则会有两个毫秒的值：客户端计算机到代理服务器或传出点，以及代理服务器到 Office 365。 你已经完成了！ 当然，仍应记录值。  

如果在连接到 Internet 的直接连接的另一台客户端计算机上运行 PsPing （即，没有代理），则会有两个毫秒的值：客户端计算机到代理服务器或传出点，以及客户端计算机到 Office 365。 在这种情况下，将客户端计算机的值从客户端365计算机的值中减去到代理服务器或传出点，并将 RTT 编号从客户端计算机到代理服务器或传出点，以及从代理服务器或传出点到 Office 365。

但是，如果您可以在受影响的直接连接位置找到客户端计算机，或者绕过代理，您可以选择是否在此处重现问题，以开始使用，并在此后进行测试。

延迟（如 Netmon 跟踪中所示），如果任何给定会话中有足够的时间，则这些额外的毫秒数可能会增加。  

![Netmon 中的常规延迟，其中包括添加到“帧摘要”的 Netmon 默认“时间差”列。](media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> 你的 IP 地址可能与此处显示的 IPs 不同，例如，你的 ping 可能会返回更像 157.56.0.0/16 或类似范围的内容。 有关 Office 365 使用的范围列表，请查看[office 365 url 和 IP 地址范围](https://technet.microsoft.com/library/hh373144.aspx)。

如果要搜索，请记住展开所有节点（顶部有一个按钮），例如，132.245。

### <a name="proxy-authentication"></a>代理身份验证

这仅适用于您正在通过代理服务器的情况。 如果不是，则可以跳过这些步骤。 正常工作时，代理身份验证应以毫秒为单位持续进行。 在高峰使用时段内不应看到间歇性的坏性能（例如）。  

如果启用了代理身份验证，则每次建立到 Office 365 的新 TCP 连接以获取信息时，您需要通过幕后的身份验证过程进行传递。 因此，例如，当从 Outlook Online 中的 "日历" 切换到 "邮件" 时，您将进行身份验证。 在 SharePoint Online 中，如果页面显示来自多个网站或位置的媒体或数据，则将针对呈现数据所需的每个不同 TCP 连接进行身份验证。  

在 Outlook Online 中，只要您在 "日历" 和 "邮箱" 之间切换或在 SharePoint Online 中缓慢页面加载，就可能会遇到负载缓慢的情况。 但是，还有其他一些症状未在此处列出。

代理身份验证是您的出口代理服务器上的一项设置。 如果它导致 Office 365 出现性能问题，则必须咨询网络团队。  

#### <a name="tools"></a>工具

- Netmon
- Wireshark

#### <a name="what-to-look-for"></a>要查找的内容

无论何时新的 TCP 会话都必须旋转（通常是从服务器请求文件或信息）或提供信息，都会发生代理身份验证。 例如，您可能会看到有关 HTTP GET 或 HTTP POST 请求的代理身份验证。 如果要查看在跟踪中对请求进行身份验证的帧，请将 "NTLMSSP 摘要" 列添加到 Netmon 并筛选`.property.NTLMSSPSummary`。 若要查看身份验证所花费的时间，请添加时间增量列。

将列添加到 Netmon：

1. 右键单击某个列，如 "**说明**"。
2. 单击 "**选择列**"。
3. 在列表中找到_NTLMSSP Summary_和_Time Delta_ ，然后单击 "**添加**"。
4. 将新列移到 "_说明_" 列之前或之后，以便您可以并排阅读它们。
5. 单击“**确定**”。

即使不添加列，Netmon 筛选也能正常运行。 但是，如果你可以看到你的身份验证阶段，你的故障排除将会大大简化。

在查找代理身份验证的实例时，请务必研究存在 NTLM 质询的所有帧，或者存在身份验证消息。 如有必要，请右键单击特定的流量，然后查找 " \>对话 TCP"。 请注意这些对话中的时间增量值。

![显示按对话筛选的代理身份验证的 Netmon 跟踪。](media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)

代理身份验证中的四秒延迟，如 Wireshark 中所示。 通过在 "帧详细信息" 中右键单击具有相同名称的字段，然后选择 "添加为列"，可在**以前显示的框架**列中进行时间增量。  <br/> ![在 Wireshark 中，可以通过在 "帧详细信息" 中右键单击具有相同名称的字段，然后选择 "添加为列" 来生成 "上一次显示的帧的时间增量" 列。](media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)

### <a name="dns-performance"></a>DNS 性能

在尽可能接近客户端国家/地区时，名称解析的工作速度最佳。

如果 DNS 名称解析在海外进行，则可以在页面负载中添加秒数。 理想情况下，名称解析发生在100毫秒下。 如果不是，则应进行进一步调查。

> [!TIP]
> 不确定客户端连接在 Office 365 中的工作原理是什么？ 请查看[此处](https://technet.microsoft.com/library/dn741250.aspx)的客户端连接参考文档。

#### <a name="tools"></a>工具

- Netmon
- Wireshark
- PsPing

#### <a name="what-to-look-for"></a>要查找的内容

分析 DNS 性能通常是网络跟踪的另一个作业。 但是，PsPing 在可能的原因中或可能的原因中也很有帮助。

DNS 流量基于 TCP，并且 UDP 请求和响应使用 ID 进行清楚标记，以帮助将特定请求与特定的响应匹配。 例如，当 SharePoint Online 在网页上使用网络名称或 URL 时，您将看到 DNS 通信。 作为经验的规则，除了在传输区域时，通过 UDP 运行之外的大部分流量。

在 Netmon 和 Wireshark 中，最基本的筛选器只`dns`允许您查看 DNS 流量。 指定筛选器时，请务必使用小写字母。 在开始在客户端计算机上重现问题之前，请务必刷新 DNS 解析器缓存。 例如，如果主页的 SharePoint Online 页面加载速度较慢，则应关闭所有浏览器、打开新的浏览器、启动跟踪、刷新 DNS 解析器缓存，然后浏览到 SharePoint Online 网站。 整个页面解析后，应停止并保存该跟踪。

![在 Netmon 中，DNS 的基本筛选器是 DNS。](media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

您想要查看此处的时间偏移量。 将 "**时间增量**" 列添加到 Netmon 中可能会有所帮助，具体方法是通过完成以下步骤来完成：

1. 右键单击某个列，如 "**说明**"。
2. 单击 "**选择列**"。
3. 在列表中找到_时间 Delta_ ，然后单击 "**添加**"。
4. 将新列移到 "_说明_" 列之前或之后，以便您可以并排阅读它们。
5. 单击“**确定**”。

如果找到感兴趣的查询，请考虑将其隔离，具体方法是在 "框架详细信息" 面板中右键单击该查询，然后选择 "**查找对话** \> **DNS**"。 请注意，网络对话面板将直接跳转到其 UDP 流量日志中的特定对话。

![通过 DNS 筛选出的 Outlook Online 负载的 Netmon 跟踪，并使用 "查找对话" DNS 来缩小结果范围。](media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)

在 Wireshark 中，可以将列用于 DNS 时间。 将跟踪（或打开跟踪）放在 Wireshark 中，然后按`dns`、或，更 helpfully 的`dns.time`方式进行筛选。 单击任意 DNS 查询，并在显示详细信息的面板中展开`Domain Name System (response)`详细信息。 你将看到 "时间" 字段（例如，" `[Time: 0.001111100 seconds]`"。 右键单击此时间并选择 "**应用为列**"。 这将为您提供一个**时间**栏，以便更快地对跟踪进行排序。 单击 "新建" 列按降序排列值，以查看哪个 DNS 调用所用时间最长。

[按照 dns.time（小写）在 Wireshark 中筛选的 SharePoint Online 的浏览，其中包含将详细信息插入到某个列以及按升序进行排序的时间。](media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

如果要对 DNS 解析时间进行更多调查，请尝试使用 TCP 使用的 DNS 端口的 PsPing （例如， `psping <IP address of DNS server>:53`）。 您是否仍会看到性能问题？ 如果这样做，则问题更可能比特定的要解决的 DNS 应用程序的问题更广泛：网络问题更大。 此外，还值得一提的一点是，ping 到 outlook.office365.com 将告诉你发生 Outlook Online 的 DNS 名称解析的位置（例如，outlook-namnorthwest.office365.com）。

如果问题看起来是 DNS 特定的，则可能需要联系 IT 部门以查看 DNS 配置和 DNS 转发器，以便进一步调查此问题。

### <a name="proxy-scalability"></a>代理可伸缩性

Office 365 中的 Outlook Online 之类的服务向客户端授予多个长期连接。 因此，每个用户可能会使用需要较长寿命的更多连接。  

#### <a name="tools"></a>工具

数学  

#### <a name="what-to-look-for"></a>要查找的内容

没有特定于此的网络跟踪或故障排除工具。 相反，它基于给定限制和其他变量的带宽计算。  

### <a name="tcp-max-segment-size"></a>TCP 最大段大小

在 SYN-SYN/ACK 中找到。  在您采取的任何性能网络跟踪中执行此操作，以确保将 TCP 数据包配置为尽可能地携带最大数据量。

目标是查看用于传输数据的 MSS 为1460字节的 MSS。 如果您使用的是代理，或者您使用的是 NAT，请务必从客户端到代理/传出/NAT 运行此测试，以及从代理/传出/NAT 到 Office 365，以获得最佳结果！ 这些是不同的 TCP 会话。

#### <a name="tools"></a>工具

Netmon

#### <a name="what-to-look-for"></a>要查找的内容

TCP Max 段大小（MSS）是网络跟踪中的三向握手的另一个参数，这意味着您将在 SYN-SYN/ACK 数据包中找到所需的数据。 MSS 实际上相当简单，可以查看。

打开您拥有的任何性能网络跟踪，并查找您想要了解的连接，或者演示性能问题。

> [!NOTE]
> 如果要查看跟踪，并需要查找与对话相关的流量，请按客户端 IP 或代理服务器或传出点的 IP 或代理服务器或传出点的 IP 进行筛选。 直接执行此操作，您需要在跟踪中 ping 正在测试的 Office 365 的 IP 地址的 URL，并按其进行筛选。

是否要再次查看跟踪？ 请尝试使用筛选器来为你的方向定位。 在 Netmon 中，根据 URL 运行搜索，例如`Containsbin(framedata, ascii, "sphybridExample")`，记下帧编号。

在 Wireshark 中使用类似`frame contains "sphybridExample"`的内容。 如果您发现已找到远程 Winsock （X-RWS-VERSION）流量（它可能在 Wireshark 中显示为 [PSH，ACK]），请记住，在相关的 SYN-SYN/Ack 之前，可能会看到 X-RWS-VERSION 连接，如前文所述。

此时，您可以记录帧编号，删除筛选器，单击 Netmon 中的 "网络对话" 窗口中的 "**所有通信**" 以查看最接近的 SYN。

重要的是，如果在跟踪时没有收到任何 IP 地址信息，则在跟踪中查找您的 URL （例如`sphybridExample-my.sharepoint.com`，部分）将为您提供用于筛选的 ip 地址。

在跟踪中查找您想要查看的连接。 为此，可以扫描跟踪、按 IP 地址筛选，或通过 Netmon 中的 "网络对话" 窗口选择特定的对话 Id。 在发现 SYN 数据包后，展开 "帧详细信息" 面板中的 "TCP （Netmon）" 或 "传输控制协议（在 Wireshark 中）"。 展开 "TCP 选项" 和 "MaxSegmentSize"。 找到相关的 SYN ACK 帧，并展开 "TCP 选项" 和 "MaxSegmentSize"。 这两个值中较小的值将成为最大线段大小。 在此图中，我使用了名为 TCP 故障排除的 Netmon 中的内置列。  

![使用内置列在 Netmon 中筛选网络跟踪。](media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

内置列在 "**框架详细信息**" 面板的顶部。 （若要切换回普通视图，请再次单击 "**列**"，然后选择 "**时区**"。）

![查找“TCP 疑难解答”选项（在“帧摘要”上方）的“列”下拉列表的位置。](media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)

以下是 Wireshark 中的已筛选跟踪。 有一个特定于 MSS 值（ `tcp.options.mss`）的筛选器。 SYN、SYN/ACK、ACK 握手的帧在 Wireshark 的底部链接，后者相当于帧详细信息（例如，帧 47 ACK、指向 46 SYN/ACK 的链接、指向 43 SYN 的链接），从而使这种工作更容易。

![在 Wireshark 中筛选的跟踪的 tcp. mss 为最大段大小（MSS）。](media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)

如果需要检查**选择性确认**（此矩阵中的下一个主题），请不要关闭您的跟踪！

### <a name="selective-acknowledgment"></a>选择性确认

在 SYN-SYN/ACK 中找到。 必须在 SYN 和 SYN/ACK 中都以允许的形式报告。 选择性确认（SACK）允许在缺少数据包或数据包时以更流畅的量传输数据。 设备可以禁用此功能，这可能会导致性能问题。

如果您使用的是代理，或者您使用的是 NAT，请务必从客户端到代理/传出/NAT 运行此测试，以及从代理/传出/NAT 到 Office 365，以获得最佳结果！ 这些是不同的 TCP 会话。

#### <a name="tools"></a>工具

Netmon

#### <a name="what-to-look-for"></a>要查找的内容

选择性确认（SACK）是 SYN-SYN/ACK 握手中的另一个参数。 您可以通过多种方式筛选跟踪的 SYN-SYN/ACK。

通过扫描跟踪、按 IP 地址筛选或通过使用 Netmon 中的 "网络对话" 窗口单击会话 ID，找到您想要查看的跟踪中的连接。 在发现 SYN 数据包后，展开 Netmon 中的 TCP 或 Wireshark 中的 "帧详细信息" 部分中的 "传输控制协议"。 展开 "TCP 选项"，然后展开 "SACK"。 找到相关的 SYN ACK 帧并展开 "TCP 选项" 和 "SACK" 字段。 确保在 SYN 和 SYN/ACK 中都允许使用某些 SACK。 以下是在 Netmon 和 Wireshark 中看到的 SACK 值。

![在 Netmon 中由于 tcp. flags = = 1 而选择性的确认（SACK）。](media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)

![如在 Wireshark 中所见，SACK 含有筛选器 tcp.flags.syn == 1。](media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)

### <a name="dns-geolocation"></a>DNS 地理位置

在世界各地的 Office 365 中，在哪里尝试解析您的 DNS 呼叫会影响您的连接速度。

在 Outlook Online 中，在第一次 DNS 查找完成后，将使用该 DNS 的位置连接到最接近的数据中心。 你将连接到 Outlook Online CAS 服务器，该服务器将使用中枢网络连接到存储数据的数据中心（dC）。 这速度更快。

在访问 SharePoint Online 时，会将位于国外的用户定向到其活动数据中心--该 dC 的位置基于其 SPO 租户的主址（如果用户基于美国，则为 USA 中的 dC）。

Lync online 一次在多个 dC 中具有活动节点。 当为 Lync online 实例发送请求时，Microsoft 的 DNS 将确定请求来自何处，并返回最近的区域 dC 中的 IP 地址（Lync online 处于活动状态）。

> [!TIP]
> 需要了解有关客户端如何连接到 Office 365 的详细信息？ 查看 "[客户端连接](https://technet.microsoft.com/library/dn741250.aspx)参考" 一文（及其有用的图形）。

#### <a name="tools"></a>工具

- Ping
- PsPing

#### <a name="what-to-look-for"></a>要查找的内容

从客户端的 DNS 服务器到 Microsoft DNS 服务器进行名称解析的请求应在大多数情况下导致 Microsoft DNS 返回区域数据中心（dC）的 IP 地址。 这对你意味着什么？ 如果你的总部在 Bangalore、印度，但你在美国出差，当浏览器发出 Outlook Online 请求时，Microsoft 的 DNS 服务器应将你的 IP 地址交给美国的数据中心--区域数据中心。 如果需要来自 Outlook 的邮件，则该数据将在数据中心之间跨 Microsoft 的快速主干网络传输。

当名称解析在尽可能接近用户位置时，DNS 工作速度最快。 如果你在欧洲，你想要转到欧洲的 Microsoft DNS，并（理想）处理欧洲的数据中心。 在欧洲的客户端转到 DNS 和北美的数据中心的性能将会降低。

对 outlook.office365.com 运行 Ping 工具，以确定您的 DNS 请求在全球的路由。 如果你在欧洲，你应该会看到类似 outlook-emeawest.office365.com 的答复。 在美洲，期待的类似 outlook-namnorthwest.office365.com。

在客户端计算机上打开命令提示符（通过 " \>开始\>运行 Cmd" 或\> "Windows 键类型" cmd）。 键入 ping outlook.office365.com，然后按 ENTER。 请记住，若要通过 IPv4 指定 ping，请指定-4。 您可能无法从 ICMP 数据包中获取答复，但应该会看到向其路由请求的 DNS 的名称。 如果要查看此连接的延迟号码，请尝试 PsPing 到 ping 返回的服务器的 IP 地址。  

![显示 Outlook-namnorthwest 中的解决方案的 outlook.office365.com 的 Ping。](media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)

![PSPing 到由 ping 返回到 outlook.office365.com 的 IP 地址，显示平均28毫秒延迟。](media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)

### <a name="office-365-application-troubleshooting"></a>Office 365 应用程序故障排除

#### <a name="tools"></a>工具

- Netmon
- HTTPWatch
- 浏览器中的 F12 控制台

在此特定于网络的文章中，我们不会讨论在特定于应用程序的故障排除中使用的工具。 但你会发现*可*[在此页面上使用的](https://support.office.com/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848)资源。

## <a name="related-topics"></a>相关主题

[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 终结点 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
