---
title: 激活 Office 365 管理中心的权限管理
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/11/2016
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 5b6d3ac7-b1ac-428e-b03e-50e882f85a6e
description: 指向介绍如何在 Office 365 中激活和使用 Rights Management service 的主题。
ms.openlocfilehash: b3df1f7ff39214d5ab7ab8f5c730299c1c22f30b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487780"
---
# <a name="activate-rights-management-in-the-office-365-admin-center"></a><span data-ttu-id="66d28-103">激活 Office 365 管理中心的权限管理</span><span class="sxs-lookup"><span data-stu-id="66d28-103">Activate Rights Management in the Office 365 admin center</span></span>

<span data-ttu-id="66d28-104">本主题指向介绍如何在 Office 365 中启用和使用 RMS 的主题。</span><span class="sxs-lookup"><span data-stu-id="66d28-104">This topic points to topics that describe how to enable and use RMS with Office 365.</span></span>
  
<span data-ttu-id="66d28-105">必须先激活权限管理服务 (RMS), 然后才能使用 Office 365 应用程序和服务的信息权限管理 (IRM) 功能。</span><span class="sxs-lookup"><span data-stu-id="66d28-105">You must activate the Rights Management service (RMS) before you can use the Information Rights Management (IRM) features of Office 365 applications and services.</span></span> <span data-ttu-id="66d28-106">激活 RMS 后, 组织可以使用 Azure RMS 开始保护重要的文档和电子邮件。</span><span class="sxs-lookup"><span data-stu-id="66d28-106">After you activate RMS, your organization can start to protect important documents and emails by using Azure RMS.</span></span> <span data-ttu-id="66d28-107">此信息保护解决方案可保护所有文件类型并与客户端应用程序 (如 Excel、microsoft Word 和其他用户、Exchange online 和 sharepoint online) 以及 microsoft exchange 和 microsoft sharepoint 等服务器集成。</span><span class="sxs-lookup"><span data-stu-id="66d28-107">This information protection solution can protect all file types and integrates with client applications like Excel, Microsoft Word, and others, Exchange Online and SharePoint Online, and servers such as Microsoft Exchange and Microsoft SharePoint.</span></span>
  
> [!TIP]
> <span data-ttu-id="66d28-108">如果你不确定是否需要权限管理, 请检查你的组织是否有一个或多个[这些业务问题或要求](https://docs.microsoft.com/rights-management/understand-explore/azure-rms-problems-it-solves), 并查看[操作中的权限管理示例](https://docs.microsoft.com/rights-management/understand-explore/what-admins-users-see)。</span><span class="sxs-lookup"><span data-stu-id="66d28-108">If you're not sure whether you need Rights Management, check whether your organization has one or more of [these business problems or requirements](https://docs.microsoft.com/rights-management/understand-explore/azure-rms-problems-it-solves), and see some [examples of Rights Management in action](https://docs.microsoft.com/rights-management/understand-explore/what-admins-users-see).</span></span> 
  
<span data-ttu-id="66d28-109">有关 RMS 的详细信息, 请使用以下链接:</span><span class="sxs-lookup"><span data-stu-id="66d28-109">Use these links for more information on RMS:</span></span>
  
- <span data-ttu-id="66d28-110">若要了解有关 RMS 的详细信息, 请参阅[什么是 Azure 权限管理](https://docs.microsoft.com/rights-management/understand-explore/what-is-azure-rms)。</span><span class="sxs-lookup"><span data-stu-id="66d28-110">To learn more about RMS, see [What is Azure Rights Management](https://docs.microsoft.com/rights-management/understand-explore/what-is-azure-rms).</span></span>
    
- <span data-ttu-id="66d28-111">如果你不熟悉 RMS, 请参阅[Azure 权限管理概述](https://docs.microsoft.com/rights-management/understand-explore/azure-rights-management)。</span><span class="sxs-lookup"><span data-stu-id="66d28-111">If you're new to RMS, see [Overview of Azure Rights Management](https://docs.microsoft.com/rights-management/understand-explore/azure-rights-management).</span></span>
    
- <span data-ttu-id="66d28-112">有关部署步骤的概述, 请参阅[Azure 权限管理部署路线图](https://docs.microsoft.com/rights-management/plan-design/deployment-roadmap)。</span><span class="sxs-lookup"><span data-stu-id="66d28-112">For an overview of the deployment steps see the [Azure Rights Management deployment roadmap](https://docs.microsoft.com/rights-management/plan-design/deployment-roadmap).</span></span>
    
- <span data-ttu-id="66d28-113">有关激活适用于 Office 365 的 RMS 的说明, 请参阅[激活 Azure 权限管理](https://technet.microsoft.com/library/jj658941.aspx)。</span><span class="sxs-lookup"><span data-stu-id="66d28-113">For instructions about activating RMS for Office 365, see [Activating Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx).</span></span>
    
- <span data-ttu-id="66d28-114">对 Office 中的 Azure RMS 和 IRM 之间的区别有了困惑吗？</span><span class="sxs-lookup"><span data-stu-id="66d28-114">Confused about the difference between Azure RMS and IRM in Office?</span></span> <span data-ttu-id="66d28-115">想要有关其他权限管理条款的帮助吗？</span><span class="sxs-lookup"><span data-stu-id="66d28-115">Want help with other Rights Management terms?</span></span> <span data-ttu-id="66d28-116">请参阅[Rights Management 术语](https://technet.microsoft.com/library/dn595132.aspx)。</span><span class="sxs-lookup"><span data-stu-id="66d28-116">See [Terminology for Rights Management](https://technet.microsoft.com/library/dn595132.aspx).</span></span>
    

