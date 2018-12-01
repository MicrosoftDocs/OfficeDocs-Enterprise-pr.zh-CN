---
title: Azure PaaS 的混合云方案
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 摘要： 了解在 Azure 中基于 Microsoft 平台即服务 (PaaS) 云产品的混合体系结构和方案。
ms.openlocfilehash: e536d81b6b14b05bef49d7c91b0404faec64303b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123329"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="da31a-103">Azure PaaS 的混合云方案</span><span class="sxs-lookup"><span data-stu-id="da31a-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="da31a-104">**摘要：** 了解在 Azure 中基于 Microsoft 平台即服务 (PaaS) 云产品的混合体系结构和方案。</span><span class="sxs-lookup"><span data-stu-id="da31a-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="da31a-105">将本地数据或计算资源与在 Azure PaaS 中运行的新的或已转换的应用程序结合使用，可以充分利用云的性能、可靠性和规模，为移动用户提供更好的支持。</span><span class="sxs-lookup"><span data-stu-id="da31a-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="da31a-106">Azure PaaS 混合方案体系结构</span><span class="sxs-lookup"><span data-stu-id="da31a-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="da31a-107">图 1 显示了适用于 Azure 的 基于 Microsoft PaaS 的混合方案的体系结构。</span><span class="sxs-lookup"><span data-stu-id="da31a-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="da31a-108">**图 1：Azure 中基于 Microsoft PaaS 的混合方案**</span><span class="sxs-lookup"><span data-stu-id="da31a-108">**Figure 1: Microsoft PaaS-based hybrid scenarios in Azure**</span></span>

![Azure 中基于 Microsoft PaaS 的混合方案](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="da31a-110">针对体系结构的每一层：</span><span class="sxs-lookup"><span data-stu-id="da31a-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="da31a-111">应用和方案</span><span class="sxs-lookup"><span data-stu-id="da31a-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="da31a-112">混合 PaaS 应用程序在 Azure 中运行，并使用本地计算或存储资源。</span><span class="sxs-lookup"><span data-stu-id="da31a-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="da31a-113">标识</span><span class="sxs-lookup"><span data-stu-id="da31a-113">Identity</span></span>
    
    <span data-ttu-id="da31a-114">由目录同步或与第三方标识提供程序的联合组成。</span><span class="sxs-lookup"><span data-stu-id="da31a-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="da31a-115">网络</span><span class="sxs-lookup"><span data-stu-id="da31a-115">Network</span></span>
    
    <span data-ttu-id="da31a-p101">由现有的 Internet 管道或通过到 Azure PaaS 的公共对等建立的 ExpressRoute 连接组成。必须包括 Azure PaaS 应用程序访问本地计算或存储资源的方法。</span><span class="sxs-lookup"><span data-stu-id="da31a-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="da31a-118">本地</span><span class="sxs-lookup"><span data-stu-id="da31a-118">On-premises</span></span>
    
    <span data-ttu-id="da31a-119">由标识和安全基础结构及现有的业务线 (LOB) 应用程序或数据库服务器组成，Azure PaaS 应用程序可以对其进行安全访问。</span><span class="sxs-lookup"><span data-stu-id="da31a-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="da31a-120">Azure PaaS 混合应用程序</span><span class="sxs-lookup"><span data-stu-id="da31a-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="da31a-121">图 2 显示了在 Azure 中运行的混合应用程序的配置。</span><span class="sxs-lookup"><span data-stu-id="da31a-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
<span data-ttu-id="da31a-122">**图 2：基于 Azure PaaS 的混合应用程序**</span><span class="sxs-lookup"><span data-stu-id="da31a-122">**Figure 2: Azure PaaS-based hybrid application**</span></span>

![基于 Azure PaaS 的混合应用程序](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="da31a-p102">在图 2 中，本地网络在服务器上承载存储或应用程序以及包含代理服务器的 DMZ。它通过 Internet 或使用 ExpressRoute 连接来连接到 Azure PaaS 服务。</span><span class="sxs-lookup"><span data-stu-id="da31a-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="da31a-126">组织可以通过以下方式使其计算或存储资源对 Azure PaaS 混合应用程序可用：</span><span class="sxs-lookup"><span data-stu-id="da31a-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="da31a-127">托管 DMZ 中服务器上的资源。</span><span class="sxs-lookup"><span data-stu-id="da31a-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="da31a-128">在 DMZ 中托管反向代理服务器，这将允许对位于本地的资源执行经身份验证的请求、入站请求和基于 HTTPS 的请求。</span><span class="sxs-lookup"><span data-stu-id="da31a-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="da31a-129">Azure 应用可以使用以下程序提供的凭据：</span><span class="sxs-lookup"><span data-stu-id="da31a-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="da31a-130">Azure AD，它可以与本地标识提供程序（如 Windows Server AD）同步。</span><span class="sxs-lookup"><span data-stu-id="da31a-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Windows Server AD.</span></span>
    
- <span data-ttu-id="da31a-131">第三方标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="da31a-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="da31a-132">示例 Azure PaaS 混合应用程序</span><span class="sxs-lookup"><span data-stu-id="da31a-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="da31a-133">图 3 显示了在 Azure 中运行的混合应用程序的示例。</span><span class="sxs-lookup"><span data-stu-id="da31a-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
<span data-ttu-id="da31a-134">**图 3：基于 Azure PaaS 的混合应用程序示例**</span><span class="sxs-lookup"><span data-stu-id="da31a-134">**Figure 3: An example Azure PaaS-based hybrid application**</span></span>

![基于 Azure PaaS 的混合应用程序示例](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="da31a-p103">在图 3 中，本地网络承载 LOB 应用程序。Azure PaaS 承载自定义的移动应用。Internet 上的智能电话访问 Azure 中的自定义移动应用，它将数据请求发送到本地 LOB 应用程序。</span><span class="sxs-lookup"><span data-stu-id="da31a-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="da31a-p104">本示例中的 Azure PaaS 混合应用程序是提供有关员工最新联系信息的自定义移动应用。端到端的混合方案由以下各项组成：</span><span class="sxs-lookup"><span data-stu-id="da31a-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="da31a-141">需要经验证的本地凭据才能运行的智能电话应用。</span><span class="sxs-lookup"><span data-stu-id="da31a-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="da31a-142">在 Azure PaaS 中运行的自定义移动应用，它根据用户智能电话应用的查询，请求有关特定员工的信息。</span><span class="sxs-lookup"><span data-stu-id="da31a-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="da31a-143">DMZ 中的反向代理服务器，验证自定义移动应用，并将转发该请求。</span><span class="sxs-lookup"><span data-stu-id="da31a-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="da31a-144">LOB 应用程序服务器场，根据用户帐户的权限，为联系人请求提供服务。</span><span class="sxs-lookup"><span data-stu-id="da31a-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="da31a-145">由于本地标识提供程序已与 Azure AD 同步，自定义移动应用和 LOB 应用都可以验证请求用户的帐户名称。</span><span class="sxs-lookup"><span data-stu-id="da31a-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="da31a-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da31a-146">See Also</span></span>

[<span data-ttu-id="da31a-147">面向企业架构师的 Microsoft 混合云</span><span class="sxs-lookup"><span data-stu-id="da31a-147">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="da31a-148">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="da31a-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

