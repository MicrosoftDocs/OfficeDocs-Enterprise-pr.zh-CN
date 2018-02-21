---
title: "测试实验室指南配置集成的交换，Lync 和 SharePoint 测试实验室"
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
description: "摘要： 了解如何创建包含运行 Exchange Server 2013年的服务器、 运行 Lync Server 2013，服务器和服务器运行 SharePoint Server 2013 集成的测试实验室。"
ms.openlocfilehash: 4bc9c48782c7693368c304f5f9d5bae56242111d
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="328d2-103">测试实验室指南：配置集成的 Exchange、Lync 和 SharePoint 测试实验室</span><span class="sxs-lookup"><span data-stu-id="328d2-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="328d2-104">**摘要：**了解如何创建包含运行 Exchange Server 2013年的服务器、 运行 Lync Server 2013，服务器和服务器运行 SharePoint Server 2013 集成的测试实验室。</span><span class="sxs-lookup"><span data-stu-id="328d2-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="328d2-105">测试实验室得出这种配置，其中包括服务器的所有三种类型的服务器之间的身份验证，可用于构建并展示多产品方案和解决方案使用的服务器上运行 Exchange Server 2013，Lync Server 2013，运行服务器和服务器运行 SharePoint Server 2013。</span><span class="sxs-lookup"><span data-stu-id="328d2-105">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="328d2-106">本文档包含如下说明：</span><span class="sxs-lookup"><span data-stu-id="328d2-106">This document contains instructions for the following:</span></span>
  
1. <span data-ttu-id="328d2-107">配置 Windows Server 2012 基本配置测试实验室。</span><span class="sxs-lookup"><span data-stu-id="328d2-107">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="328d2-108">安装和配置名为 SQL1 的新服务器。</span><span class="sxs-lookup"><span data-stu-id="328d2-108">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="328d2-109">SQL1 在服务器上安装 SQL Server 2012年。</span><span class="sxs-lookup"><span data-stu-id="328d2-109">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="328d2-110">安装和配置名为 CLIENT2 的新客户端计算机。</span><span class="sxs-lookup"><span data-stu-id="328d2-110">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="328d2-111">上安装和配置 Exchange Server 2013 EX1。</span><span class="sxs-lookup"><span data-stu-id="328d2-111">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="328d2-112">安装和配置名为 LYNC1 的新服务器。</span><span class="sxs-lookup"><span data-stu-id="328d2-112">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="328d2-113">在 LYNC1 上安装 Lync Server 2013 标准版。</span><span class="sxs-lookup"><span data-stu-id="328d2-113">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="328d2-114">有关 SP1 安装 SharePoint Server 2013。</span><span class="sxs-lookup"><span data-stu-id="328d2-114">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="328d2-115">配置 EX1、LYNC1 和 SP1 之间的集成。</span><span class="sxs-lookup"><span data-stu-id="328d2-115">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="328d2-116">**Lync，集成的交换，SharePoint 测试实验室指南概述视频观看**</span><span class="sxs-lookup"><span data-stu-id="328d2-116">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

![视频（播放按钮）图标](images/mod_icon_video_M.png)
  
<span data-ttu-id="328d2-118">有关如何配置测试实验室在 Hyper-V 中的信息，请参阅[宿主集成的交换，Lync 和 SharePoint 测试实验室使用 Windows Server 2012 Hyper-V 中](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx)。</span><span class="sxs-lookup"><span data-stu-id="328d2-118">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="328d2-119">下载测试实验室指南</span><span class="sxs-lookup"><span data-stu-id="328d2-119">Download the test lab guide</span></span>

<span data-ttu-id="328d2-120">[测试实验室指南： 配置集成的交换、 Lync 和 SharePoint 测试实验室](https://go.microsoft.com/fwlink/p/?LinkId=313670)(https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="328d2-120">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="328d2-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="328d2-121">See Also</span></span>

[<span data-ttu-id="328d2-122">测试实验室指南</span><span class="sxs-lookup"><span data-stu-id="328d2-122">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




