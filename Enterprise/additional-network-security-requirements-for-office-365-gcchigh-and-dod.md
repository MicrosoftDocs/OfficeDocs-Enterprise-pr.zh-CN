---
title: Office 365 GCC 高和 DoD 的其他网络安全要求
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150m
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 摘要： Office 365 GCC 高和 DoD 具有额外的网络安全要求
hideEdit: true
ms.openlocfilehash: a79204809787391065ac833d9a3872af4cdc1528
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "44371628"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a><span data-ttu-id="fd842-103">Office 365 GCC 高和 DOD 的其他网络安全要求</span><span class="sxs-lookup"><span data-stu-id="fd842-103">Additional network security requirements for Office 365 GCC High and DOD</span></span>

<span data-ttu-id="fd842-104">*本文适用于 Office 365 GCC 高、Office 365 DOD、Microsoft 365 GCC 高和 Microsoft 365 DOD。*</span><span class="sxs-lookup"><span data-stu-id="fd842-104">*This article applies to Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High, and Microsoft 365 DOD.*</span></span>

<span data-ttu-id="fd842-105">Office 365 GCC High and DOD 是安全的云环境，可满足美国政府及其供应商和合同工的需求。</span><span class="sxs-lookup"><span data-stu-id="fd842-105">Office 365 GCC High and DOD are secure cloud environments to meet the needs of the United States Government and its suppliers and contractors.</span></span>  <span data-ttu-id="fd842-106">这些云环境对允许服务访问的外部终结点具有额外的网络限制。</span><span class="sxs-lookup"><span data-stu-id="fd842-106">These cloud environments have additional network restrictions on which external endpoints the services are permitted to access.</span></span>

<span data-ttu-id="fd842-107">使用联合身份或混合共存计划的 GCC 高和 DOD 客户可能需要 Microsoft 允许对现有本地部署的入站和/或出站访问权限。</span><span class="sxs-lookup"><span data-stu-id="fd842-107">GCC High and DOD customers planning to use federated identities or hybrid co-existence may require Microsoft to permit inbound and/or outbound access to your existing on-premises deployments.</span></span>  <span data-ttu-id="fd842-108">这些活动的示例包括：</span><span class="sxs-lookup"><span data-stu-id="fd842-108">Examples of these activities include:</span></span>

* <span data-ttu-id="fd842-109">联合身份（使用 Active Directory 联合身份验证服务或类似的受支持 STS）的使用</span><span class="sxs-lookup"><span data-stu-id="fd842-109">Use of federated identities (with Active Directory Federation Services or similar supported STS)</span></span>
* <span data-ttu-id="fd842-110">与本地 Exchange Server 或 Skype for Business 部署的混合共存</span><span class="sxs-lookup"><span data-stu-id="fd842-110">Hybrid coexistence with an on-premises Exchange Server or Skype for Business deployment</span></span>
* <span data-ttu-id="fd842-111">从本地系统迁移现有用户内容</span><span class="sxs-lookup"><span data-stu-id="fd842-111">Migration of existing user content from an on-premises system</span></span>

<span data-ttu-id="fd842-112">若要允许服务与本地终结点进行通信，您**必须**向 Office 365 工程部门发送电子邮件，以进行网络更改。</span><span class="sxs-lookup"><span data-stu-id="fd842-112">To permit the service to communicate with your on-premises endpoints, you **must** send an email to Office 365 engineering for network changes.</span></span>

> [!WARNING]
> <span data-ttu-id="fd842-113">所有请求都有一个**为期三周**的 SLA，由于所需的安全和合规性控件和部署管道，无法加速。</span><span class="sxs-lookup"><span data-stu-id="fd842-113">All requests have a **three-week** SLA and cannot be expedited due to the required security and compliance controls and deployment pipelines.</span></span>  <span data-ttu-id="fd842-114">这包括初始加入网络请求以及在迁移到服务后进行的任何更改。</span><span class="sxs-lookup"><span data-stu-id="fd842-114">This includes initial onboarding network requests as well as any changes after you have migrated to the service.</span></span>  <span data-ttu-id="fd842-115">请确保您的网络团队了解此日程表并将其包含在规划周期中。</span><span class="sxs-lookup"><span data-stu-id="fd842-115">Please ensure that your network teams are aware of this timeline and include it in their planning cycles.</span></span>

<span data-ttu-id="fd842-116">请向[Office 365 政府网络白名单](mailto:o365gwlt@microsoft.com)发送一封电子邮件，其中包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="fd842-116">Please send an email to [Office 365 Government Network Whitelist](mailto:o365gwlt@microsoft.com) with the following information:</span></span>

* <span data-ttu-id="fd842-117">**到**： [Office 365 政府网络白名单](mailto:o365gwlt@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="fd842-117">**To**: [Office 365 Government Network Whitelist](mailto:o365gwlt@microsoft.com)</span></span>
* <span data-ttu-id="fd842-118">**发件人**：租户管理员-发送电子邮件**必须**与租户中的全局管理员联系人匹配</span><span class="sxs-lookup"><span data-stu-id="fd842-118">**From**: A tenant administrator - the send email **must** match a Global Administrator contact in your tenant</span></span>
* <span data-ttu-id="fd842-119">**电子邮件主题**： OFFICE 365 GCC 高网络请求-contoso.onmicrosoft.us （将其替换为你的租户名称）</span><span class="sxs-lookup"><span data-stu-id="fd842-119">**Email subject**: Office 365 GCC High Network Request - contoso.onmicrosoft.us (replace this with your tenant name)</span></span>

<span data-ttu-id="fd842-120">您的邮件正文应包含以下数据：</span><span class="sxs-lookup"><span data-stu-id="fd842-120">The body of your message should include the following data:</span></span>

* <span data-ttu-id="fd842-121">你的 Microsoft Online Services 租户名称（例如，contoso.onmicrosoft.com、fabrikam.onmicrosoft.us）</span><span class="sxs-lookup"><span data-stu-id="fd842-121">Your Microsoft Online Services tenant name (i.e. contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)</span></span>
* <span data-ttu-id="fd842-122">一个电子邮件通讯组列表，Microsoft 将与网络更改和/或跟踪无效子网的持续通信进行通信</span><span class="sxs-lookup"><span data-stu-id="fd842-122">An email distribution list that Microsoft will communicate with for on-going communications related to network changes and/or follow up for invalid subnets</span></span>
* <span data-ttu-id="fd842-123">指示是否计划将 Microsoft 团队混合与本地部署结合使用</span><span class="sxs-lookup"><span data-stu-id="fd842-123">Indicate whether you plan to use Microsoft Teams hybrid co-existence with your on-premises deployments</span></span>
* <span data-ttu-id="fd842-124">联合身份系统外部可访问 URL （例如，sts.contoso.com）和 CIDR 表示法中的 IP 地址范围（例如，10.1.1.0/28）</span><span class="sxs-lookup"><span data-stu-id="fd842-124">Federated identity system externally accessible URL (e.g. sts.contoso.com) and IP address range in CIDR notation (e.g. 10.1.1.0/28)</span></span>
* <span data-ttu-id="fd842-125">以 CIDR 表示法表示的本地 PKI 证书吊销列表 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="fd842-125">On-Premises PKI Certificate Revocation List URL and IP address range in CIDR notation</span></span>
* <span data-ttu-id="fd842-126">以 CIDR 表示法表示的 Exchange Server 本地部署的外部可访问 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="fd842-126">Externally accessible URL and IP address range for Exchange Server on-premises deployment in CIDR notation</span></span>
* <span data-ttu-id="fd842-127">以 CIDR 表示法表示的 Skype for Business 本地部署的外部可访问 URL 和 IP 地址范围</span><span class="sxs-lookup"><span data-stu-id="fd842-127">Externally accessible URL and IP address range for Skype for Business on-premises deployment in CIDR notation</span></span>

<span data-ttu-id="fd842-128">出于安全和合规性原因，请牢记对你的请求的以下限制：</span><span class="sxs-lookup"><span data-stu-id="fd842-128">For security and compliance reasons, please keep in mind the following restrictions on your request:</span></span>

* <span data-ttu-id="fd842-129">每个租户有四个子网限制</span><span class="sxs-lookup"><span data-stu-id="fd842-129">There is a four subnet limitation per tenant</span></span>
* <span data-ttu-id="fd842-130">子网必须在 CIDR 表示法中（例如 10.1.1.0/28）</span><span class="sxs-lookup"><span data-stu-id="fd842-130">Subnets must be in CIDR Notation (e.g. 10.1.1.0/28)</span></span>
* <span data-ttu-id="fd842-131">子网范围不能大于/24</span><span class="sxs-lookup"><span data-stu-id="fd842-131">Subnet ranges cannot be larger than /24</span></span>
* <span data-ttu-id="fd842-132">我们**无法**适应允许访问商业云服务（商业 Office 365、Google G 套件、Amazon Web 服务等）的请求。</span><span class="sxs-lookup"><span data-stu-id="fd842-132">We **cannot** accommodate requests to allow access to commercial cloud services (commercial Office 365, Google G-Suite, Amazon Web Services, etc.)</span></span>

<span data-ttu-id="fd842-133">在 Microsoft 收到您的请求并得到批准后，就会有为期三周的实施 SLA，且不能加速。</span><span class="sxs-lookup"><span data-stu-id="fd842-133">Once your request has been received and approved by Microsoft, there is a three-week SLA for implementation and cannot be expedited.</span></span>  <span data-ttu-id="fd842-134">收到请求并在最终确认完成后，你将收到初始确认。</span><span class="sxs-lookup"><span data-stu-id="fd842-134">You will receive an initial acknowledgment when we’ve received your request and a final acknowledgement once it has been completed.</span></span>
