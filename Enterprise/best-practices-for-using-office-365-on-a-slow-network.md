---
title: 在慢速网络上使用 Office 365 的最佳实践
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: End User
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
description: 如果 Internet 连接已始终 fast 和永远不会向下不是很好？可能的一天的将到来。但同时，有可执行解决 balky 网络和仍获取您完成的日常工作的实践操作。
ms.openlocfilehash: 52c3bde04aa58f9e24a49d2034e6b6433c44f21c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539789"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>在慢速网络上使用 Office 365 的最佳实践

如果 Internet 连接已始终 fast 和永远不会向下不是很好？可能的一天的将到来。但同时，有可执行解决 balky 网络和仍获取您完成的日常工作的实践操作。虽然 Office 365 与基于云的服务，但它还提供了许多方法处理您的内容脱机和顺利地保留更改同步。此外，可以很多高效以使用脱机内容，只是因为应用程序运行速度更快且更快地响应用户界面。这是点： Office 365 为您提供了两个领域的优势。下面是如何充分利用的。 
  
> [!TIP]
> 要查看您的网络连接是如何速度较慢 （或 fast）？尝试[OOKLA 速度测试](https://www.speedtest.net/)或[网络速度测试应用程序](https://www.windowsphone.com/en-us/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70)。 
     
## <a name="why-is-my-network-so-slow"></a>为什么是我的网络速度很慢？

虽然您没有网络性能本身的控制，但它有助于了解了什么事在后台。Internet 极其复杂，但有一些可帮助您了解更好的情况的概念。按照本文中的最佳做法可以帮助解决性能问题，并减少失望。
  
**影响网络性能的主要因素**

![网络性能因素](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 **带宽和延迟**网络性能的两个最重要度量的带宽和延迟： 
  
- 带宽是吞吐量的以位 / 秒为单位的速率。越大越好。带宽就像水管道。管道越大，您可以"通过"将它们放的多个水量。
    
- 延迟是它采用地从服务器或服务向设备获取内容并以毫秒为单位的时间。更快更佳。延迟可能是由许多因素包括带宽较低、 稀疏连接或传输时间导致的。
    
 **常见问题**除了带宽和延迟，其他问题会影响网络性能，并且通常是不可预知。网络性能可以波动基于某一天或您的物理地址的时间。某些事件发生的出现峰值使用 Internet，如自然灾害或主要公共事件时，可以被堵塞网络。大小和加载页上的复杂性和的数量和要传输的文件的大小对性能产生直接关系。暂时会降低 WiFi 连接： 例如，投票通过请求每个人都同时 tweet 千位的大型会议会议。 
  
 **附属网络注意事项**附属网络陆地网络不可行，如后的国家/地区、 游轮或远程科学区域时很有用。这些网络依赖于卫星上定位在上方赤道 22000 英里 geosynchronous 通道。但是，传输实际上是大约 90,000 英里，具有因此附属网络速度较慢的延迟 （500 ms 或更多） 比陆地网络 （20 到 50 毫秒）。下最好的条件，不可能会注意到此延迟，但下载大型文件、 流视频和游戏，您可能会。另一个问题是中的大量的天气，如雷暴和 blizzards，可以暂时中断附属传输的"雨淡出"。
  
## <a name="are-you-sure-its-the-network"></a>是否确实是网络？

时遇到性能问题，首先请确保您的设备不是问题的根源。有可执行的可能会使一大改进的两个操作：
  
- 请确保您的设备能够正常运行，并且您的计算机上没有任何恶意软件。
    
- 如果可能，购买更多内存。添加内存是最简单、 通常最有效的方式来提高在设备上的性能。处理大型文件和视频时，它将非常有用。
    
有关详细信息，请参阅[Windows 性能和维护](https://windows.microsoft.com/en-us/windows/performance-maintenance-help#performance-maintenance-help)和[修复 Windows 系统性能问题](https://support.microsoft.com/mats/slow_windows_performance/)。
   
## <a name="best-practices-for-using-your-browser"></a>使用您的浏览器的最佳实践

您的浏览器到 Office 365 网关，因此它会对性能，尤其是加载所需时间影响页面和频率舍入触发到 Office 365 服务。 
  
 **一般的浏览器**
  
通常是一些建议的浏览器：
  
- 禁用浏览器加载项的可能会影响性能或实际上您不需要。
    
- 增加缓存大小的 internet 临时文件。
    
-  一旦您已登录到您的工作或学校帐户后，在浏览器窗口保持打开状态全天。无需再次登录，可以打开其他选项卡和 windows。如果您需要登录到另一个帐户，请使用专用浏览。 
    
- 下载并打开每一页后，其保持打开状态使用选项卡。很容易地选项卡之间导航和更高版本上某一天使用的页。仅当您需要该页面上的最新数据刷新页面。
    
- 如果正在太长，无法打开页面，停止页面下载 （按 ESC），然后刷新页 （按 F5）。 
    
-  如果可能，减少往返行程到 Office 365。例如，而不是通过列表或库的分页，使用搜索中的大型库和筛选直接进入所需的结果列表中查找文件。或者，创建的视图，减少页面加载时间。有关详细信息，请参阅[管理大型列表和 Office 365 中的库](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES)。
    
- 如果视频性能不佳，您可能能够下载视频并观看在设备上。可能可用的下载链接，或者您可能能够右键单击视频链接，然后选择**另存为的目标**。 
    
 **浏览器特定**
  
下面是一些建议的特定浏览器：
  
- **Internet Explorer**通过早期版本升级到 Internet Explorer 版本 11 或更高版本的大量性能改进。有关详细信息，请参阅[修复 Internet Explorer 问题](https://support.microsoft.com/mats/ie_performance_and_safety)。
    
- **FireFox**有关详细信息，请参阅[Firefox 太慢或停止工作](https://support.mozilla.org/en-US/products/firefox/fix-problems/slowness-or-hanging)。
    
- **Safari**有关详细信息，请参阅[Apple-Safari](https://www.apple.com/safari/)。
    
- **部件版式**有关详细信息，请参阅[Chrome 帮助](https://support.google.com/chrome/?hl=en)。
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>使用 Outlook 和 Outlook Web App 的最佳实践

读取、 写入，和组织的电子邮件是每个人的一天的重要部分。Outlook 和 Outlook Web App (OWA) 提供脱机支持。使用智能电话上的电子邮件应用程序是另一个很好的替代。使用以下选项最适合您的需求：
  
- 通过早期版本升级到 Outlook 2013 SP1 或更高版本的大量性能改进。 
    
-  Outlook Web App，您可以创建脱机邮件、 联系人和日历事件当 OWA 下一次上载的能够连接到 Office 365。有关设置和使用 OWA 在脱机模式下的详细信息，请参阅[使用 Outlook Web App 脱机](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36)。
    
- Outlook 中，可以在缓存模式下，在其中它都会自动连接尽可能工作。您可以下载您的整个邮箱或它的一部分的 Outlook。有关详细信息，请参阅[启用缓存 Exchange 模式](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c)和[脱机在 Outlook 中工作](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633)。 
    
- Outlook 还提供脱机模式。若要使用此，您必须先设置缓存模式，以便从您的帐户的信息复制到您的计算机。在脱机模式下，Outlook 将尝试连接使用发送和接收设置，或当您手动将其设置为联机工作。有关详细信息，请参阅[脱机工作，以避免数据连接费用](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282)、[更改发送和接收设置脱机工作时](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a)和[从联机到脱机工作的开关](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9)。 
    
- 如果您有智能电话，可用于通过电话运营商网络会审您的电子邮件和日历。 
    
> [!NOTE]
> 下面是一些有关何时使用 Outlook 或 OWA 指导。如果磁盘空间不是在设备上的问题，Outlook 将具有一组完整的功能，并可能适合于您。如果磁盘空间为在设备上的问题，请考虑使用 OWA 其功能的子集，但也在联机的情况下，非常有效。当然，您可以使用因为它们也协同工作。 
  
## <a name="best-practices-for-using-onedrive-for-business"></a>使用 OneDrive for Business 的最佳实践

OneDrive for Business 旨在从头联机和脱机使用您的文件。一旦您设置它的更改同步发生自动可靠地随时随地您使它们。如果网络速度较慢，您可以使用脱机版的文件。
  
OneDrive for Business 同步应用程序是适用于 Office 2013 （Professional Plus 或标准版），还是包含 Office 2013 应用程序的 Office 365 订阅。如果您没有 Office 2013，您可以[下载](https://support.microsoft.com/kb/2903984)OneDrive for Business 同步应用程序免费。此应用程序也是比使用**资源管理器中打开**或**上载**命令。有关详细信息，请参阅[将计算机同步您的 OneDrive for Business 文件在 Office 365 中设置](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16)。
  
下面是使用 OneDrive for Business 同步应用程序的一些其他指导：
  
- 如果您第一次同步大型库，启动同步过程中的关闭时间，例如，夜间。 
    
- [停止同步 OneDrive for Business 应用程序包含的库](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330)功能可用于暂时停止同步更新。但是，此功能短时间内使用，如几个小时一次，以避免队列大数字更新，并将合并发生冲突的风险降至最低多人处理在同一文档。 
  
## <a name="best-practices-for-using-onenote"></a>使用 OneNote 的最佳实践

每个 SharePoint 工作组网站具有内置的 OneNote 笔记本，您可以轻松创建您自己。OneNote 是好方法来收集及时获取所需每天即可完成的任务的信息。例如，很多团队用作 OneNote 收集点每周会议、 项目备注、 想法、 计划和状态报告。使用页、 部分中，和选项卡，您可以整齐组织这些分散的信息。
  
但 OneNote 的好处是，您可以访问其内容从几乎任何设备，是否桌面、 笔记本电脑、 平板电脑或智能手机。和您不必担心保存或同步因为 OneNote 会为您。 
  
有关详细信息，请参阅[Microsoft OneNote](https://office.microsoft.com/en-us/onenote/)。
  
## <a name="best-practices-for-using-lync-online"></a>使用 Lync Online 的最佳实践

以下是使用 Lync Online，您的网络太慢时的一般原则：
  
- 使用即时消息，只要可能因为它也在低速网络中工作。
    
- 避免通过虚拟专用网络 (VPN) 或远程访问服务 (RAS) 连接进行电话呼叫。
    
- 请确保您的音频设备已获得批准。有关详细信息，请参阅[电话和设备的 Microsoft Lync](https://technet.microsoft.com/en-us/office/dn788944)。
    
-  联机演示文稿中使用 PowerPoint，减少的大小和复杂性的幻灯片。有关详细信息，请参阅[改进您的演示文稿的性能的提示](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949)。
    
- 只要有可能，共享监视器，而不是程序或桌面。有关详细信息，请参阅[共享您的桌面或程序在 Lync](https://support.office.com/article/33aaa965-eb32-42a9-8a9b-cdfffa364842)。
    
- 而不必共享，发送提前为会议的 PowerPoint 幻灯片中请求附件，以便与会者在其客户端设备上查看的幻灯片。有关详细信息，请参阅[Set up Lync 会议](https://support.office.com/article/258f9d20-f06c-49a4-a77f-7f5ac635bb5d)。
    
-  视频性能是非常依赖于网络性能。避免使用视频，如果您的网络速度较慢。 
    
有关详细信息，请参阅[差音频或 Lync Online 中的视频质量](https://support.microsoft.com/kb/2386655)和[更新 Lync 2013 中的低屏幕](https://support.microsoft.com/kb/2958375)。
  
## <a name="best-practices-for-using-sharepoint-lists"></a>使用 SharePoint 列表的最佳实践

使用列表数据脱机"清理"、 分析、 或报告数据真的大程度地减少在低速网络中的影响。您可以读取和写入 Microsoft Access 2013 中的大多数列表，通过将链接到它们。您还可以将列表导出到 Excel 表格，这会创建 Excel 表格和列表之间的单向数据连接。
  
此外，如果已激活的 Access Services 功能，然后您可以使用相当详细数据超过列表视图阈值，默认情况下最多 50,000 个项目。Access 2013 and Excel 2013 自动处理小型批次中的列表数据和然后重新复原数据，允许使用更多数据超过列表视图阈值，而且不产生不利影响的服务性能的技术其他用户。 
  
有关详细信息，请参阅[管理大型列表和 Office 365 中的库](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784)中的"更多有关管理大型列表"部分。
  
## <a name="best-practices-for-customizing-web-pages"></a>自定义网页的最佳实践

自定义网页时，您可能无意中导致与页的性能不佳。多种因素可能会影响，如的复杂性和页、 多少 web 部件均已添加，最初显示列表或库项目的数量，以及代码页的方式的大小。
  
有关详细信息，请参阅[优化 SharePoint Online 的性能](https://technet.microsoft.com/library/f97c2f06-0426-443d-8a16-d98abb0da252#TuneSharePoint)。
  
## <a name="best-practices-for-using-project-online"></a>使用 Project Online 的最佳实践

以下准则可帮助提高网络性能。
  
- Project Online 和 SharePoint Online 需要同步，可能会非常耗时。如果您的项目团队低周转，禁用项目网站同步，以提高项目发布和项目详细信息页面的性能。限制到的资源的实际需要使用系统，并监视大型组的同步后的潜在的任何权限问题的组的 Active Directory 同步。 
    
- 如果您的组织使用项目网站，创建它们按需而不是自动。这加快首次发布体验，并避免了创建不必要的网站和内容。
    
- 项目详细信息页面 (PDP) 可以触发整个项目重新计算并启动工作流操作，这两种可性能密集型操作。若要避免同时在相同的 PDP 上触发两个更新流程，避免更新日历字段 （开始日期、 完成日期、 状态日期和当前日期） 和非计划字段 （项目名称、 说明和所有者）。 
    
- 减少 Web 部件和显示在每个 PDP 的自定义字段的数量。使用需要更新来提高负载和节省时间的唯一字段创建专用的 PDP。 
    
- 当您为报告使用 OData 时，限制使用服务器端筛选查询在运行时的数据量。
    
有关详细信息，请参阅[优化 Project Online 的性能](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)。
  
## <a name="whats-the-best-way-to-report-problems"></a>报告问题的最佳方式是什么？

Microsoft 不断地提高了 Office 365 by 监控网络，测量带宽的总体性能和延迟，提高页面加载时间，减少磁盘 I/O 使用，重新设计页面以使用最少下载策略，添加到数据中心的硬件和添加更多数据中心。有关检查您的当前状态以及报告问题的详细信息，请参阅[查看您的服务的状态](https://office.microsoft.com/en-us/office365-suite-help/view-the-status-of-your-services-HA102817837.aspx)。
  
## <a name="see-also"></a>另请参阅

[Office 365 的网络规划和性能优化](network-planning-and-performance.md)
  
[Microsoft 虚拟学院课程 — Office 365 性能管理](https://blogs.office.com/2014/12/03/microsoft-virtual-academy-course-office-365-performance-management/)
  
[管理 Office 365 终结点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 终结点常见问题](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

