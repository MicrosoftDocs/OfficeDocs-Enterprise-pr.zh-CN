---
title: 在慢速网络上使用 Office 365 的最佳实践
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
audience: End User
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MET150
- MOP150
- MEW150
- BCS160
ms.assetid: fd16c8d2-4799-4c39-8fd7-045f06640166
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: 本文将指导您完成在慢速网络上使用 Office 365 时可采用的最佳实践。
ms.openlocfilehash: b4b81826dfca4c5962cc6aef026c3878e3b52304
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605778"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>在慢速网络上使用 Office 365 的最佳实践

如果你的 Internet 连接始终快速且永不停机，不是很棒？ 可能会出现这一天。 但在这种情况下，您可以执行一些可行的操作来解决 balky 网络，但仍能实现日常工作。 虽然 Office 365 是基于云的服务，但它还提供了多种方法来脱机处理内容，并使更改保持同步。 此外，仅由于应用程序运行速度更快且用户界面的响应速度更快，有时可以更有效地脱机处理内容。 这一点是： Office 365 为你提供了这两个领域的最佳优势。 下面介绍了如何利用这一点。 
  
> [!TIP]
> 想要了解 (或快速) 网络连接的速度如何？ 尝试[OOKLA 速度测试](https://www.speedtest.net/)或[网络速度测试应用](https://www.windowsphone.com/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70)。 

## <a name="why-is-my-network-so-slow"></a>为什么我的网络速度太慢？

虽然您不能控制网络性能本身，但它有助于了解幕后发生的事情。 Internet enormously 复杂，但有几个概念可以帮助您更好地理解这种情况。 按照本文中的最佳实践，可帮助解决性能问题并降低不满。
  
**影响网络性能的主要因素**

![网络性能因素](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 **带宽和延迟**网络性能的两个最重要的措施是带宽和延迟： 
  
- 带宽是以位/秒为单位衡量的吞吐量的速率。 越大越好。 带宽类似于水管道。 管道越大，可以 "放入" 的水越多。

- 延迟是从服务器或服务向设备获取内容所需的时间，以毫秒为单位。 更快越好。 延迟可能由多种因素导致，包括低带宽、稀疏连接或传输时间。

 **常见问题**除了带宽和延迟之外，其他问题也会影响网络性能，并且通常是不可预知的。 网络性能可能会基于一天中的时间或你的物理位置波动。 当某些事件发生，导致使用 Internet （如自然灾害或主要公共事件）时，网络可能会被堵塞。 正在加载的页面的大小和复杂程度以及要转移的文件的数量和大小与性能是直接的。 WiFi 连接可能会暂时下降：例如，您可以通过请求所有人同时 twitter 来轮询数以千计的会议会议。 
  
 **卫星网络的注意事项**当陆地网络不可行时，卫星网络很有用，例如，后端国家/地区、巡航船或远程科学领域。 这些网络依赖于位于 equator 上方的 geosynchronous 轨道22000英里内的卫星。 但是，传输实际上传播了大约90000英里，因此卫星网络的延迟速度较慢 (500 毫秒或更多) 低于地面网络 (20 到50毫秒) 。 在最佳条件下，您可能不会注意到此延迟，但在下载大型文件、流式视频和玩游戏时，您可能会这样做。 另一个问题是 "rain 淡出"，在这种情况下，可能会暂时中断卫星传输的天气（如 thunderstorms 和 blizzards）。
  
## <a name="are-you-sure-its-the-network"></a>是否确定网络？

只要遇到性能问题，首先确保设备不是问题的根本原因。 您可以执行以下两项操作，这可能会产生显著改进：
  
- 请确保你的设备运行良好且你的计算机上没有恶意软件。

- 如果可能，请购买更多内存。 添加内存是改善设备性能的最简单且通常是最有效的方法。 它在处理大型文件和视频时尤其有用。

有关详细信息，请参阅[Windows 性能和维护](https://windows.microsoft.com/windows/performance-maintenance-help#performance-maintenance-help)以及[在 Windows 10 中改进电脑性能的提示](https://support.microsoft.com/en-za/help/4002019/windows-10-improve-pc-performance)。

## <a name="best-practices-for-using-your-browser"></a>使用浏览器的最佳实践

你的浏览器是到 Office 365 的网关，因此它可能会对性能产生影响，尤其是在加载页面和向 Office 365 服务进行往返行程的过程中需要多长时间。
  
 **浏览器常规**
  
下面是一些一般浏览器的建议：
  
- 禁用可能会影响性能或您不真正需要的浏览器加载项。

- 增加临时 internet 文件的缓存大小。

- 登录到工作或学校帐户后，请始终在一天内打开浏览器窗口。 您可以打开其他选项卡和窗口，而无需再次登录。 如果需要登录到其他帐户，请使用专用浏览。 

- 下载并打开每个页面后，请使用选项卡将其打开。 很容易在选项卡之间导航，并在一天中的以后使用页面。 仅当您需要该页面上的最新数据时才刷新页面。

- 如果打开页面的时间过长，请停止页面下载 (按 ESC) 然后刷新页面 (按 F5) 。 

-  如果可能，请减少到 Office 365 的往返行程。 例如，可以使用 "搜索" 来查找大型库中的文件，并在列表中筛选以直接转到所需的结果，而不是通过列表或库进行分页。 或者，创建最小化页面加载时间的视图。 有关详细信息，请参阅[在 Office 365 中管理大型列表和库](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES)。

- 如果视频性能较差，你可以下载视频并在你的设备上观看它。 可以使用下载链接，或者可以右键单击视频链接，然后选择 "**目标另存为**"。

 **特定于浏览器**
  
下面是针对特定浏览器的一些建议：
  
- **Internet Explorer**升级到 Internet Explorer 版本11或更高版本，以获得对早期版本的显著性能改进。 有关详细信息，请参阅[Internet Explorer 故障排除指南](https://support.microsoft.com/help/2437121/troubleshooting-guide-for-internet-explorer-when-you-access-office-365)。

- **FireFox**有关详细信息，请参阅[Firefox 缓慢或停止工作](https://support.mozilla.org/products/firefox/fix-problems/slowness-or-hanging)。

- **Safari**有关详细信息，请参阅[Apple-Safari](https://www.apple.com/safari/)。

- **Chrome**有关详细信息，请参阅[Chrome Help](https://support.google.com/chrome/?hl=en)。
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>使用 Outlook 和 Outlook Web App 的最佳实践

阅读、写入和组织电子邮件是每个人的一大部分。 Outlook 和 Outlook Web App (OWA) 提供脱机支持。 在智能手机上使用电子邮件应用程序是另一种有用的替代方法。 使用最适合您的需求的以下选项：
  
- 升级到最新版本的 Outlook，以实现对早期版本的显著性能改进。 

-  Outlook Web App 允许您创建在 OWA 下次能够连接到 Office 365 时上载的脱机邮件、联系人和日历事件。 有关在脱机模式下设置和使用 OWA 的详细信息，请参阅[脱机使用 Outlook Web App](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36)。

- Outlook 允许您在缓存模式下工作，只要可能，它就会自动连接。 您可以让 Outlook 下载整个邮箱，或只下载其中的一部分。 有关详细信息，请参阅[打开缓存 Exchange 模式](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c)和[在 Outlook 中脱机工作](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633)。

- Outlook 还提供脱机模式。 若要使用此设置，您必须首先设置缓存模式，以便将帐户中的信息复制到您的计算机。 在脱机模式下，Outlook 将尝试使用 "发送" 和 "接收" 设置进行连接，或者在手动将其设置为 "联机工作" 时进行连接。 有关详细信息，请参阅[脱机工作以避免数据连接费用](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282)，在[脱机工作时更改发送和接收设置](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a)，以及[从脱机工作切换到联机](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9)状态。

- 如果你有智能手机，则可以使用它通过电话运营商的网络诊断你的电子邮件和日历。

> [!NOTE]
> 下面是有关何时使用 Outlook 或 OWA 的一些指导。 如果你的设备上的磁盘空间不是问题，Outlook 将拥有一组完整的功能，并且可能最适合你。 如果磁盘空间在你的设备上存在问题，请考虑使用具有功能子集的 OWA，但在联机情况下也能发挥最佳效果。 当然，您可以使用这两个方法，因为它们在一起很好地协同工作。
  
## <a name="best-practices-for-using-onedrive-for-business"></a>使用 OneDrive for Business 的最佳实践

OneDrive for Business 是从头开始设计的，可用于联机和脱机处理文件。 完成设置后，无论何时何地进行更改，都会自动且可靠地进行同步。 如果网络速度较慢，则可以使用文件的脱机版本。
  
OneDrive for Business 同步应用程序附带有 SharePoint Online 和 Office 365 商业版订阅，你也可以免费[下载](https://support.microsoft.com/kb/2903984)onedrive for business 同步应用。 此应用程序还比使用**在资源管理器**或**上传**命令中打开的速度更快。 有关详细信息，请参阅[将计算机设置为同步 Office 365 中的 OneDrive for business 文件](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16)。
  
下面是使用 OneDrive for Business 同步应用程序的其他一些指南：
  
- 如果是首次同步大型库，请在非工作时间（例如，整夜）内启动同步。

- 您可以使用 "[停止将库与 OneDrive For business 应用功能同步](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330)" 功能来暂时停止同步更新。 但是，此功能可用于简短的时间段（例如，一次几个小时），以避免对大量更新进行排队，并在多个用户处理同一文档时将合并冲突风险降至最低。
  
## <a name="best-practices-for-using-onenote"></a>使用 OneNote 的最佳实践

每个 SharePoint 团队网站都有一个内置的 OneNote 笔记本，您可以轻松创建自己的 OneNote 笔记本。 OneNote 是一种很好的方法，可收集每天所需的信息，以完成任务。 例如，许多团队将 OneNote 用作每周会议、项目备注、想法、计划和状态报告的集合点。 您可以使用页面、节和选项卡整齐地整理这些全异的信息。
  
OneNote 的优点是，可以从几乎所有设备（无论是台式机、笔记本电脑、平板电脑还是智能手机）访问内容。 您不必担心保存或同步，因为 OneNote 为你做。
  
有关详细信息，请参阅[Microsoft OneNote](https://office.microsoft.com/onenote)。

## <a name="best-practices-for-using-skype-for-business-and-lync-online"></a>使用 Skype for Business 和 Lync Online 的最佳实践

以下是在网络速度较慢时使用 Skype for Business 或 Lync Online 的一般准则：

- 在你可以时使用即时消息，因为它在低速网络中运行良好。

- 避免通过虚拟专用网络进行电话呼叫 (VPN) 或远程访问服务 (RAS) 连接。

- 请确保你的音频设备已获得批准。 有关详细信息，请参阅适用[于 Microsoft Lync 的电话和设备](https://docs.microsoft.com/skypeforbusiness/lync-cert/ip-phones)。

- 在联机演示文稿中使用 PowerPoint 时，请减小幻灯片的大小和复杂程度。 有关详细信息，请参阅[改善演示文稿性能的提示](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949)。

- 视频性能非常依赖于网络性能。 如果网络速度较慢，请避免使用视频。

有关详细信息，请参阅[Lync Online 中的音频或视频质量差](https://support.microsoft.com/kb/2386655)或如何[解决 Skype for business 中的连接问题](https://support.office.com/article/troubleshoot-connection-issues-in-skype-for-business-ca302828-783f-425c-bbe2-356348583771)。
  
## <a name="best-practices-for-using-sharepoint-lists"></a>使用 SharePoint 列表的最佳实践

将列表数据脱机处理为 "擦除"、"分析" 或 "报告数据" 是最大限度地减少慢速网络的影响的一种极好的方法。 您可以通过链接到 Microsoft Access 2019 和 Microsoft Access 2016 中的大多数列表来读取和写入这些列表。 您还可以将列表导出到 Excel 表，这将在 Excel 表和列表之间创建单向数据连接。 了解如何[脱机处理链接到 SharePoint 列表的表](https://support.office.com/article/work-offline-with-tables-that-are-linked-to-sharepoint-lists-5d66594a-6176-4a25-a198-320f13ccf41e)。
  
有关详细信息，请参阅在[Office 365 中管理大型列表和库](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784)中的 "管理大型列表的详细信息" 部分。
  
## <a name="best-practices-for-customizing-web-pages"></a>自定义网页的最佳实践

自定义网页时，可能会在无意中导致页面性能较差。 许多因素可能会产生影响，如页面的复杂程度和大小、添加的 web 部件数、最初显示的列表或库项目数以及编码页面的方式。
  
有关详细信息，请参阅[优化 SharePoint Online 性能](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance)。
  
## <a name="best-practices-for-using-project-online"></a>使用 Project Online 的最佳实践

以下指南可帮助改善网络性能。
  
- Project Online 和 SharePoint Online 需要同步，这可能需要很长时间。 如果您的项目团队的营业额较低，则禁用项目网站同步以改进项目发布和项目详细信息页面性能。 将 Active Directory 同步限制为实际需要使用系统的资源组，并在同步大型组后监视任何潜在的权限问题。

- 如果您的组织使用项目网站，请根据需要创建它们，而不是自动创建。 这将加快首次发布体验的速度，并避免创建不必要的网站和内容。

- 项目详细信息页面 (PDP) 可以触发整个项目的重新计算并启动工作流操作，这两种操作可能会导致性能密集型操作。 若要避免同时在同一 PDP 上触发两个更新过程，请避免更新日历字段 (开始日期、完成日期、状态日期和当前日期) 和非计划字段 (项目名称、说明和所有者) 。

- 减少每个 PDP 上显示的 Web 部件和自定义域的数量。 创建专用的 PDP，其中仅有需要更新的字段，以改进加载和节省时间。

- 在使用 OData 进行报告时，请使用服务器端筛选来限制在运行时查询的数据量。

有关详细信息，请参阅[优化 Project Online 性能](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)。
  
## <a name="whats-the-best-way-to-report-problems"></a>报告问题的最佳方法是什么？

Microsoft 通过监控网络、衡量带宽和延迟、改进页面加载时间、减少磁盘 i/o、重新设计页面以使用最少的下载策略、向数据中心添加硬件和添加更多数据中心，来不断提高 Office 365 的整体性能。 有关检查当前状态和报告问题的详细信息，请参阅 how [to 检查 Office 365 服务运行状况](https://docs.microsoft.com/office365/enterprise/view-service-health)。
  
## <a name="see-also"></a>另请参阅

[Office 365 网络计划和性能优化](network-planning-and-performance.md)
  
[Office 365 网络连接原则](office-365-network-connectivity-principles.md)
  
[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 终结点 FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
 