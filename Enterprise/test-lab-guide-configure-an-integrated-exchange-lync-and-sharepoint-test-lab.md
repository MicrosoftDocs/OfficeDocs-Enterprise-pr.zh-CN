---
title: 测试实验室指南配置集成的 Exchange、Lync 和 SharePoint 测试实验室
ms.author: jhendr
author: JoanneHendrickson
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 48e16935-3429-456a-8fe6-50afa257924c
f1.keywords:
- NOCSH
description: 摘要：了解如何创建包含运行 Exchange Server 2013 的服务器、运行 Lync Server 2013 的服务器以及运行 SharePoint Server 2013 的服务器的集成测试实验室。
ms.openlocfilehash: 6041f47520f7a02efe08d05835ca0f15dfd6633a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841099"
---
# <a name="test-lab-guide-configure-an-integrated-exchange-lync-and-sharepoint-test-lab"></a><span data-ttu-id="887ca-103">测试实验室指南：配置集成的 Exchange、Lync 和 SharePoint 测试实验室</span><span class="sxs-lookup"><span data-stu-id="887ca-103">Test Lab Guide: Configure an integrated Exchange, Lync, and SharePoint test lab</span></span>

 <span data-ttu-id="887ca-104">**摘要：** 了解如何创建包含运行 Exchange Server 2013 的服务器、运行 Lync Server 2013 的服务器以及运行 SharePoint Server 2013 的服务器的集成测试实验室。</span><span class="sxs-lookup"><span data-stu-id="887ca-104">**Summary:** Learn how to create an integrated test lab that contains a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
 
<span data-ttu-id="887ca-105">**观看集成的 Exchange、Lync 和 SharePoint 测试实验室指南概述视频**</span><span class="sxs-lookup"><span data-stu-id="887ca-105">**Watch the integrated Exchange, Lync, and SharePoint test lab guide overview video**</span></span>

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=8d1f00cc-b8b1-4394-9367-0cc9765e380a&AutoPlayVideo=false]
 
<span data-ttu-id="887ca-106">此配置产生的测试实验室（包括所有三种类型的服务器之间的服务器到服务器身份验证）可用于构建并演示使用运行 Exchange Server 2013 的服务器的多产品方案和解决方案。运行 Lync Server 2013 的服务器以及运行 SharePoint Server 2013 的服务器。</span><span class="sxs-lookup"><span data-stu-id="887ca-106">The test lab that results from this configuration, which includes server-to-server authentication between all three types of servers, can be used to build out and demonstrate multi-product scenarios and solutions that use a server that runs Exchange Server 2013, a server that runs Lync Server 2013, and a server that runs SharePoint Server 2013.</span></span>
  
<span data-ttu-id="887ca-107">本文档包含以下各项的说明：</span><span class="sxs-lookup"><span data-stu-id="887ca-107">This document contains instructions for:</span></span>
  
1. <span data-ttu-id="887ca-108">配置 Windows Server 2012 基本配置测试实验室。</span><span class="sxs-lookup"><span data-stu-id="887ca-108">Configuring the Windows Server 2012 Base Configuration test lab.</span></span>
    
2. <span data-ttu-id="887ca-109">安装和配置名为 SQL1 的新服务器。</span><span class="sxs-lookup"><span data-stu-id="887ca-109">Installing and configuring a new server named SQL1.</span></span>
    
3. <span data-ttu-id="887ca-110">在 SQL1 服务器上安装 SQL Server 2012。</span><span class="sxs-lookup"><span data-stu-id="887ca-110">Installing SQL Server 2012 on the SQL1 server.</span></span>
    
4. <span data-ttu-id="887ca-111">安装和配置名为 CLIENT2 的新客户端计算机。</span><span class="sxs-lookup"><span data-stu-id="887ca-111">Installing and configuring a new client computer named CLIENT2.</span></span>
    
5. <span data-ttu-id="887ca-112">在 EX1 上安装和配置 Exchange Server 2013。</span><span class="sxs-lookup"><span data-stu-id="887ca-112">Installing and configuring Exchange Server 2013 on EX1.</span></span>
    
6. <span data-ttu-id="887ca-113">安装和配置名为 LYNC1 的新服务器。</span><span class="sxs-lookup"><span data-stu-id="887ca-113">Installing and configuring a new server named LYNC1.</span></span>
    
7. <span data-ttu-id="887ca-114">在 LYNC1 上安装 Lync Server 2013 Standard Edition。</span><span class="sxs-lookup"><span data-stu-id="887ca-114">Installing Lync Server 2013 Standard Edition on LYNC1.</span></span>
    
8. <span data-ttu-id="887ca-115">在 SP1 上安装 SharePoint Server 2013。</span><span class="sxs-lookup"><span data-stu-id="887ca-115">Installing SharePoint Server 2013 on SP1.</span></span>
    
9. <span data-ttu-id="887ca-116">配置 EX1、LYNC1 和 SP1 之间的集成。</span><span class="sxs-lookup"><span data-stu-id="887ca-116">Configuring integration between EX1, LYNC1, and SP1.</span></span>
    
<span data-ttu-id="887ca-117">有关如何在 Hyper-v 中配置此测试实验室的信息，请参阅[使用 Windows Server 2012 Hyper-v 托管集成 Exchange、Lync 和 SharePoint 测试实验室](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx)。</span><span class="sxs-lookup"><span data-stu-id="887ca-117">For information about how to configure this test lab in Hyper-V, see [Hosting the integrated Exchange, Lync, and SharePoint test lab with Windows Server 2012 Hyper-V](https://social.technet.microsoft.com/wiki/contents/articles/18483.hosting-the-integrated-exchange-lync-and-sharepoint-test-lab-with-windows-server-2012-hyper-v.aspx).</span></span>
  
## <a name="download-the-test-lab-guide"></a><span data-ttu-id="887ca-118">下载测试实验室指南</span><span class="sxs-lookup"><span data-stu-id="887ca-118">Download the test lab guide</span></span>

<span data-ttu-id="887ca-119">[测试实验室指南：配置集成的 Exchange、Lync 和 SharePoint 测试实验室](https://go.microsoft.com/fwlink/p/?LinkId=313670)（https://go.microsoft.com/fwlink/p/?LinkId=313670)</span><span class="sxs-lookup"><span data-stu-id="887ca-119">[Test Lab Guide: Configure an Integrated Exchange, Lync, and SharePoint Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=313670) (https://go.microsoft.com/fwlink/p/?LinkId=313670)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="887ca-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="887ca-120">See Also</span></span>

[<span data-ttu-id="887ca-121">测试实验室指南</span><span class="sxs-lookup"><span data-stu-id="887ca-121">Test Lab Guides</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=202817)




