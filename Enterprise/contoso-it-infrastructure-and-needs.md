---
title: Contoso 的 IT 基础结构和需求
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: 摘要： 了解 Contoso 的本地 IT 基础结构的基本结构，以及 Microsoft 云产品满足其业务需求的方式。
ms.openlocfilehash: e500aa1f3105c1e605d0d3c1d5f66651acb82b34
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915727"
---
# <a name="contosos-it-infrastructure-and-needs"></a><span data-ttu-id="0ca13-103">Contoso 的 IT 基础结构和需求</span><span class="sxs-lookup"><span data-stu-id="0ca13-103">Contoso's IT infrastructure and needs</span></span>

 <span data-ttu-id="0ca13-104">**摘要：** 了解 Contoso 的本地 IT 基础结构的基本结构，以及 Microsoft 云产品满足其业务需求的方式。</span><span class="sxs-lookup"><span data-stu-id="0ca13-104">**Summary:** Understand the basic structure of Contoso's on-premises IT infrastructure and how its business needs can be met by Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="0ca13-105">Contoso 正在从本地集中式 IT 基础结构转换到一个合并了基于云的个人生产率工作负载、应用程序和混合方案的包含云的 IT 基础结构。</span><span class="sxs-lookup"><span data-stu-id="0ca13-105">Contoso is in the process of transitioning from an on-premises, centralized IT infrastructure to a cloud-inclusive one that incorporates cloud-based personal productivity workloads, applications, and hybrid scenarios.</span></span>
  
## <a name="contosos-existing-it-infrastructure"></a><span data-ttu-id="0ca13-106">Contoso 的现有 IT 基础结构</span><span class="sxs-lookup"><span data-stu-id="0ca13-106">Contoso's existing IT infrastructure</span></span>

<span data-ttu-id="0ca13-107">Contoso 通过将应用程序数据中心置于巴黎总部，来使用最集中的本地 IT 基础结构。</span><span class="sxs-lookup"><span data-stu-id="0ca13-107">Contoso uses a mostly centralized on-premises IT infrastructure, with application datacenters in the Paris headquarters.</span></span>
  
<span data-ttu-id="0ca13-108">**图 1：Contoso 的现有 IT 基础结构**</span><span class="sxs-lookup"><span data-stu-id="0ca13-108">**Figure 1: Contoso's existing IT infrastructure**</span></span>

![Contoso 的现有 IT 基础结构](media/Contoso-Poster/Existing-IT.png)
  
<span data-ttu-id="0ca13-110">图 1 显示总部办事处的应用程序数据中心、DMZ 和 Internet。</span><span class="sxs-lookup"><span data-stu-id="0ca13-110">Figure 1 shows a headquarters office with application datacenters, a DMZ, and the Internet.</span></span>
  
<span data-ttu-id="0ca13-111">在 Contoso 的 DMZ 中，不同的服务器集提供不同的功能：</span><span class="sxs-lookup"><span data-stu-id="0ca13-111">In Contoso's DMZ, different sets of servers provide:</span></span>
  
- <span data-ttu-id="0ca13-112">巴黎总部的工作人员对 Contoso Intranet 和 Web 代理的远程访问。</span><span class="sxs-lookup"><span data-stu-id="0ca13-112">Remote access to the Contoso intranet and web proxying for workers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="0ca13-113">对 Contoso 公共网站的托管，客户可以在其中订购产品、部件或配件。</span><span class="sxs-lookup"><span data-stu-id="0ca13-113">Hosting for the Contoso public web site, from which customers can order products, parts, or supplies.</span></span>
    
- <span data-ttu-id="0ca13-114">对 Contoso 合作伙伴 Extranet 的托管，用于合作伙伴的通信和协作。</span><span class="sxs-lookup"><span data-stu-id="0ca13-114">Hosting for the Contoso partner extranet for partner communication and collaboration.</span></span>
    
## <a name="contosos-business-needs"></a><span data-ttu-id="0ca13-115">Contoso 的业务需求</span><span class="sxs-lookup"><span data-stu-id="0ca13-115">Contoso's business needs</span></span>

<span data-ttu-id="0ca13-116">下面是按优先级顺序排列的 Contoso 的业务需求：</span><span class="sxs-lookup"><span data-stu-id="0ca13-116">Here are Contoso's business needs in priority order:</span></span>
  
1. <span data-ttu-id="0ca13-117">遵守区域法规要求</span><span class="sxs-lookup"><span data-stu-id="0ca13-117">Adhere to regional regulatory requirements</span></span>
    
    <span data-ttu-id="0ca13-118">若要防止罚款并与地方政府保持良好的关系，Contoso 必须确保数据存储和加密规则的合规性。</span><span class="sxs-lookup"><span data-stu-id="0ca13-118">To prevent fines and maintain good relations with local governments, Contoso must ensure compliance with data storage and encryption regulations.</span></span>
    
2. <span data-ttu-id="0ca13-119">改进供应商和合作伙伴管理</span><span class="sxs-lookup"><span data-stu-id="0ca13-119">Improve vendor and partner management</span></span>
    
    <span data-ttu-id="0ca13-p101">合作伙伴 Extranet 不断老化并且维护费用高昂。Contoso 想要将其替换为使用联合身份验证的基于云的解决方案。</span><span class="sxs-lookup"><span data-stu-id="0ca13-p101">The partner extranet is aging and expensive to maintain. Contoso wants to replace it with a cloud-based solution that uses federated authentication.</span></span>
    
3. <span data-ttu-id="0ca13-122">提高移动工作人员的工作效率，改善设备管理及访问</span><span class="sxs-lookup"><span data-stu-id="0ca13-122">Improve mobile workforce productivity, device management, and access</span></span>
    
    <span data-ttu-id="0ca13-123">Contoso 的移动工作人员不断增加，并且需要进行设备管理，以确保保护知识产权并更有效地访问资源。</span><span class="sxs-lookup"><span data-stu-id="0ca13-123">Contoso's mobile-only workforce is expanding and needs device management to ensure intellectual property protection and more efficient access to resources.</span></span>
    
4. <span data-ttu-id="0ca13-124">减少远程访问基础结构</span><span class="sxs-lookup"><span data-stu-id="0ca13-124">Reduce remote access infrastructure</span></span>
    
    <span data-ttu-id="0ca13-125">通过将远程工作人员经常访问的资源移动到云，Contoso 可减少远程访问解决方案的维护和支持成本以节约资金。</span><span class="sxs-lookup"><span data-stu-id="0ca13-125">By moving resources commonly accessed by remote workers to the cloud, Contoso will save money by reducing maintenance and support costs for their remote access solution.</span></span>
    
5. <span data-ttu-id="0ca13-126">缩小本地数据中心</span><span class="sxs-lookup"><span data-stu-id="0ca13-126">Scale down on-premises datacenters</span></span>
    
    <span data-ttu-id="0ca13-127">Contoso 数据中心包含数百个服务器，其中一些正在运行旧版或存档功能，这会干扰 IT 人员，使他们难以维护高业务价值工作负载。</span><span class="sxs-lookup"><span data-stu-id="0ca13-127">The Contoso datacenters contain hundreds of servers, some of which are running legacy or archival functions that distract IT staff from maintaining high business value workloads.</span></span>
    
6. <span data-ttu-id="0ca13-128">扩展用于季度末处理的计算和存储资源</span><span class="sxs-lookup"><span data-stu-id="0ca13-128">Scale-up computing and storage resources for end-of-quarter processing</span></span>
    
    <span data-ttu-id="0ca13-129">季度末财务核算和预测处理及库存管理要求短期增加服务器和存储空间。</span><span class="sxs-lookup"><span data-stu-id="0ca13-129">End-of-quarter financial accounting and projection processing along with inventory management requires short-term increases in servers and storage.</span></span>
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a><span data-ttu-id="0ca13-130">将 Contoso 业务需求映射到 Microsoft 云产品</span><span class="sxs-lookup"><span data-stu-id="0ca13-130">Mapping Contoso's business needs to Microsoft's cloud offerings</span></span>

<span data-ttu-id="0ca13-131">根据微软云产品的分析，Contoso 的 IT 部门确定了以下映射：</span><span class="sxs-lookup"><span data-stu-id="0ca13-131">Based on an analysis of Microsoft's cloud offerings, Contoso's IT department determined the following mapping:</span></span>
  
|<span data-ttu-id="0ca13-132">**软件即服务 (SaaS)**</span><span class="sxs-lookup"><span data-stu-id="0ca13-132">**Software as a Service (SaaS)**</span></span>|<span data-ttu-id="0ca13-133">**平台即服务 (Azure PaaS )**</span><span class="sxs-lookup"><span data-stu-id="0ca13-133">**Platform as a Service (Azure PaaS )**</span></span>|<span data-ttu-id="0ca13-134">**基础结构即服务 (Azure IaaS )**</span><span class="sxs-lookup"><span data-stu-id="0ca13-134">**Infrastructure as a Service (Azure IaaS )**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="0ca13-135">**Office 365：** 云中的主要个人和组工作效率应用程序。</span><span class="sxs-lookup"><span data-stu-id="0ca13-135">**Office 365:** Primary personal and group productivity applications in the cloud.</span></span> <br/> <span data-ttu-id="0ca13-136">业务需求：1 3 5</span><span class="sxs-lookup"><span data-stu-id="0ca13-136">Business needs: 1 3 5</span></span>  <br/> |<span data-ttu-id="0ca13-137">使用基于云的应用托管销售和支持文档及信息系统。</span><span class="sxs-lookup"><span data-stu-id="0ca13-137">Host sales and support documents and information systems using cloud-based apps.</span></span>  <br/> <span data-ttu-id="0ca13-138">业务需求：3</span><span class="sxs-lookup"><span data-stu-id="0ca13-138">Business need: 3</span></span>  <br/> |<span data-ttu-id="0ca13-139">将存档和旧系统移动到基于云的服务器。</span><span class="sxs-lookup"><span data-stu-id="0ca13-139">Move archival and legacy systems to cloud-based servers.</span></span>  <br/> <span data-ttu-id="0ca13-140">业务需求：5</span><span class="sxs-lookup"><span data-stu-id="0ca13-140">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="0ca13-p102">**Dynamics 365：** 使用基于云的客户和供应商管理。删除 DMZ 中的合作伙伴 Extranet。</span><span class="sxs-lookup"><span data-stu-id="0ca13-p102">**Dynamics 365:** Use cloud-based customer and vendor management. Remove partner extranet in the DMZ. </span></span><br/> <span data-ttu-id="0ca13-143">业务需求：2</span><span class="sxs-lookup"><span data-stu-id="0ca13-143">Business need: 2</span></span>  <br/> |<span data-ttu-id="0ca13-144">移动应用程序基于云，而不是基于巴黎数据中心。</span><span class="sxs-lookup"><span data-stu-id="0ca13-144">Mobile applications are cloud-based, rather than Paris datacenter-based.</span></span>  <br/> <span data-ttu-id="0ca13-145">业务需求：3 4</span><span class="sxs-lookup"><span data-stu-id="0ca13-145">Business needs: 3 4</span></span>  <br/> |<span data-ttu-id="0ca13-146">将使用率较低的应用和数据迁移出本地数据中心。</span><span class="sxs-lookup"><span data-stu-id="0ca13-146">Migrate low-use apps and data out of on-premises datacenters.</span></span>  <br/> <span data-ttu-id="0ca13-147">业务需求：5</span><span class="sxs-lookup"><span data-stu-id="0ca13-147">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="0ca13-148">**Intune/EMS：** 管理 iOS 和 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="0ca13-148">**Intune/EMS:** Manage iOS and Android devices.</span></span> <br/> <span data-ttu-id="0ca13-149">业务需求：3</span><span class="sxs-lookup"><span data-stu-id="0ca13-149">Business need: 3</span></span>  <br/> ||<span data-ttu-id="0ca13-150">为季度末处理需求增加临时服务器和存储空间。</span><span class="sxs-lookup"><span data-stu-id="0ca13-150">Add temporary servers and storage for end-of-quarter processing needs.</span></span>  <br/> <span data-ttu-id="0ca13-151">业务需求：6</span><span class="sxs-lookup"><span data-stu-id="0ca13-151">Business need: 6</span></span>  <br/> |
   
## <a name="see-also"></a><span data-ttu-id="0ca13-152">See Also</span><span class="sxs-lookup"><span data-stu-id="0ca13-152">See Also</span></span>

[<span data-ttu-id="0ca13-153">Microsoft 云中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="0ca13-153">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="0ca13-154">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="0ca13-154">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="0ca13-155">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="0ca13-155">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


