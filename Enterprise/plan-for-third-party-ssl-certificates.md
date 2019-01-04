---
title: Office 365 第三方 SSL 证书计划
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 摘要：介绍了 Exchange 内部部署和混合部署、使用 AD FS 的 SSO、Exchange Online 服务和 Exchange Web 服务所需的 SSL 证书。
ms.openlocfilehash: c9e968ef7ec9015be398b4eef9184451dd316bea
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546513"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a><span data-ttu-id="af6f5-103">Office 365 第三方 SSL 证书计划</span><span class="sxs-lookup"><span data-stu-id="af6f5-103">Plan for third-party SSL certificates for Office 365</span></span>

 <span data-ttu-id="af6f5-104">**摘要：** 介绍 Exchange 内部部署和混合部署、 使用 AD FS 的 SSO 所需的 SSL 证书 Exchange Online 服务和 Exchange Web 服务。</span><span class="sxs-lookup"><span data-stu-id="af6f5-104">**Summary:** Describes the SSL certificates needed for Exchange on-premises and hybrid, SSO using AD FS, Exchange Online services, and Exchange Web Services.</span></span> 
  
<span data-ttu-id="af6f5-105">若要加密您的客户端与 Office 365 环境之间的通信，必须基础结构服务器上安装第三方安全套接字层 (SSL) 证书。</span><span class="sxs-lookup"><span data-stu-id="af6f5-105">To encrypt communications between your clients and the Office 365 environment, third-party Secure Socket Layer (SSL) certificates must be installed on your infrastructure servers.</span></span>

||
|:-----|
| <span data-ttu-id="af6f5-106">本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="af6f5-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|
   
<span data-ttu-id="af6f5-107">以下 Office 365 组件需要证书：</span><span class="sxs-lookup"><span data-stu-id="af6f5-107">Certificates are required for the following Office 365 components:</span></span>
  
- <span data-ttu-id="af6f5-108">本地 Exchange</span><span class="sxs-lookup"><span data-stu-id="af6f5-108">Exchange on-premises</span></span>
    
- <span data-ttu-id="af6f5-109">单一登录 (SSO)（针对 Active Directory 联合身份验证服务 (AD FS) 联合服务器和 AD FS 联合服务器代理）</span><span class="sxs-lookup"><span data-stu-id="af6f5-109">Single sign-on (SSO) (for both the Active Directory Federation Services (AD FS) federation servers and AD FS federation server proxies)</span></span>
    
- <span data-ttu-id="af6f5-110">Exchange Online 服务，例如自动发现、 Outlook Anywhere，和 Exchange Web 服务</span><span class="sxs-lookup"><span data-stu-id="af6f5-110">Exchange Online services, such as Autodiscover, Outlook Anywhere, and Exchange Web Services</span></span>
    
- <span data-ttu-id="af6f5-111">Exchange 混合服务器</span><span class="sxs-lookup"><span data-stu-id="af6f5-111">Exchange hybrid server</span></span>
    
## <a name="certificates-for-exchange-on-premises"></a><span data-ttu-id="af6f5-112">本地 Exchange 的证书</span><span class="sxs-lookup"><span data-stu-id="af6f5-112">Certificates for Exchange On-Premises</span></span>

<span data-ttu-id="af6f5-113">有关如何使用数字证书确保内部部署 Exchange 组织和 Exchange Online 之间的通信安全，请参阅 TechNet 文章[了解证书要求](https://go.microsoft.com/fwlink/p/?LinkID=243657)的概述。</span><span class="sxs-lookup"><span data-stu-id="af6f5-113">For an overview about how to use digital certificates to make the communication between the on-premises Exchange organization and Exchange Online secure, see the TechNet article [Understanding Certificate Requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).</span></span>
  
## <a name="certificates-for-single-sign-on"></a><span data-ttu-id="af6f5-114">单一登录的证书</span><span class="sxs-lookup"><span data-stu-id="af6f5-114">Certificates for Single Sign-On</span></span>

<span data-ttu-id="af6f5-p101">若要为用户提供的简化单一登录体验，其中包括可靠的安全性，联合服务器或联合服务器代理上需要下表中所示的证书。下表重点介绍 Active Directory 联合身份验证服务 (AD FS)，我们还必须[使用第三方身份提供程序](https://go.microsoft.com/fwlink/?LinkId=532869)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="af6f5-p101">To provide your users with a simplified single sign-on experience that includes robust security, the certificates shown in the following table are required on either the federation servers or the federation server proxies. The table below focuses on Active Directory Federation Services (AD FS), we also have more information on [using third-party identity providers](https://go.microsoft.com/fwlink/?LinkId=532869).</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="af6f5-117">**证书类型**</span><span class="sxs-lookup"><span data-stu-id="af6f5-117">**Certificate Type**</span></span> <br/> |<span data-ttu-id="af6f5-118">**说明**</span><span class="sxs-lookup"><span data-stu-id="af6f5-118">**Description**</span></span> <br/> |<span data-ttu-id="af6f5-119">**在部署之前，您需要知道什么？**</span><span class="sxs-lookup"><span data-stu-id="af6f5-119">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="af6f5-120">**SSL 证书（也称为服务器身份验证证书）**</span><span class="sxs-lookup"><span data-stu-id="af6f5-120">**SSL certificate (also called a server authentication certificate)**</span></span> <br/> |<span data-ttu-id="af6f5-121">这是标准 SSL 证书，用于确保联合服务器、客户端和联合服务器代理计算机之间的通信的安全。</span><span class="sxs-lookup"><span data-stu-id="af6f5-121">This is a standard SSL certificate that is used to make communications between federation servers, clients, and federation server proxy computers secure.</span></span>  <br/> |<span data-ttu-id="af6f5-p102">AD FS 需要 SSL 证书。默认情况下，AD FS 使用 Internet 信息服务 (IIS) 中的默认网站配置 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="af6f5-p102">AD FS requires an SSL certificate. By default, AD FS uses the SSL certificate that is configured for the default website in Internet Information Services (IIS).  </span></span><br/> <span data-ttu-id="af6f5-p103">此 SSL 证书的使用者名称用于确定您部署的 AD FS 的每个实例的联合身份验证服务 (FS) 名称。请考虑选择任何新的证书颁发机构 (CA) 的使用者名称-颁发的证书最佳代表贵公司或组织到 Office 365 的名称。此名称必须是 Internet 可路由。</span><span class="sxs-lookup"><span data-stu-id="af6f5-p103">The subject name of this SSL certificate is used to determine the Federation Service (FS) name for each instance of AD FS that you deploy. Consider choosing a subject name for any new certification authority (CA)-issued certificates that best represents the name of your company or organization to Office 365. This name must be Internet-routable.  </span></span><br/><span data-ttu-id="af6f5-127">**注意：** AD FS 要求此 SSL 证书没有无句点 （短名称） 主题名称。</span><span class="sxs-lookup"><span data-stu-id="af6f5-127">**Caution:** AD FS requires that this SSL certificate have no dotless (short-name) subject name.</span></span>          <br/> <span data-ttu-id="af6f5-128">**建议：** 由于此证书必须由客户端的 AD FS 受信任，我们建议您使用由公共 CA （第三方） 或属于公共受信任的根; CA 颁发的 SSL 证书例如，VeriSign 或 Thawte。</span><span class="sxs-lookup"><span data-stu-id="af6f5-128">**Recommendation:** Because this certificate must be trusted by clients of AD FS, we recommend that you use an SSL certificate issued by a public (third-party) CA or by a CA that is subordinate to a publicly trusted root; for example, VeriSign or Thawte.</span></span>  <br/> |
|<span data-ttu-id="af6f5-129">**令牌签名证书**</span><span class="sxs-lookup"><span data-stu-id="af6f5-129">**Token-signing certificate**</span></span> <br/> |<span data-ttu-id="af6f5-130">这是标准 X.509 证书，用于安全地签名的所有令牌进行联合服务器颁发的且 Office 365 所接受和验证。</span><span class="sxs-lookup"><span data-stu-id="af6f5-130">This is a standard X.509 certificate that's used for securely signing all tokens that the federation server issues and that Office 365 accepts and validates.</span></span>  <br/> |<span data-ttu-id="af6f5-p104">令牌签名证书必须包含链接到在 FS 受信任的根的私钥。默认情况下，AD FS 创建自签名的证书。但是，具体取决于您的组织的需要，可以使用 AD FS 管理单元来更改此证书 CA 颁发的证书。</span><span class="sxs-lookup"><span data-stu-id="af6f5-p104">The token-signing certificate must contain a private key that chains to a trusted root in the FS. By default, AD FS creates a self-signed certificate. However, depending on the needs of your organization, you can change this certificate to a CA-issued certificate by using the AD FS management snap-in.  </span></span><br/><span data-ttu-id="af6f5-p105">**注意：** 非常重要的 FS 稳定性的令牌签名证书。如果更改证书，Office 365 必须更改的通知。如果未提供通知，则用户无法登录到其 Office 365 服务产品。</span><span class="sxs-lookup"><span data-stu-id="af6f5-p105">**Caution:** The token-signing certificate is critical to the stability of the FS. If the certificate is changed, Office 365 must be notified of the change. If notification is not provided, users can't sign in to their Office 365 service offerings.</span></span><br/><span data-ttu-id="af6f5-p106">**建议：** 我们建议您使用的 AD FS 生成的自签名的令牌签名证书。这样，它管理此证书，默认情况下。例如，当此证书即将过期，AD FS 会生成新的自签名的证书。</span><span class="sxs-lookup"><span data-stu-id="af6f5-p106">**Recommendation:** We recommend that you use the self-signed token-signing certificate that is generated by AD FS. By doing so, it manages this certificate for you by default. For example, when this certificate is about to expire, AD FS will generate a new self-signed certificate.  </span></span><br/> |
   
<span data-ttu-id="af6f5-140">联合服务器代理需要下表中描述的证书。</span><span class="sxs-lookup"><span data-stu-id="af6f5-140">Federation server proxies require the certificate that is described in the following table.</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="af6f5-141">**证书类型**</span><span class="sxs-lookup"><span data-stu-id="af6f5-141">**Certificate Type**</span></span> <br/> |<span data-ttu-id="af6f5-142">**说明**</span><span class="sxs-lookup"><span data-stu-id="af6f5-142">**Description**</span></span> <br/> |<span data-ttu-id="af6f5-143">**在部署之前，您需要知道什么？**</span><span class="sxs-lookup"><span data-stu-id="af6f5-143">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="af6f5-144">SSL 证书</span><span class="sxs-lookup"><span data-stu-id="af6f5-144">SSL certificate</span></span>  <br/> |<span data-ttu-id="af6f5-145">这是标准 SSL 证书，用于确保联合服务器、联合服务器代理和 Internet 客户端计算机之间的通信的安全。</span><span class="sxs-lookup"><span data-stu-id="af6f5-145">This is a standard SSL certificate that is used for securing communications between a federation server, a federation server proxy, and Internet client computers.</span></span>  <br/> |<span data-ttu-id="af6f5-146">您可以成功运行 AD FS 联合服务器代理配置向导之前，此 SSL 证书必须绑定到 IIS 中的默认网站。</span><span class="sxs-lookup"><span data-stu-id="af6f5-146">This SSL certificate must be bound to the default website in IIS before you can successfully run the AD FS Federation Server Proxy Configuration wizard.</span></span>  <br/> <span data-ttu-id="af6f5-147">此证书必须具有与公司网络中联合服务器上配置的 SSL 证书相同的主题名称。</span><span class="sxs-lookup"><span data-stu-id="af6f5-147">This certificate must have the same subject name as the SSL certificate that was configured on the federation server in the corporate network.</span></span>  <br/> <span data-ttu-id="af6f5-148">**建议：** 建议您使用此联合服务器代理连接到的联合服务器上配置的服务器身份验证证书。</span><span class="sxs-lookup"><span data-stu-id="af6f5-148">**Recommendation:** We recommend that you use the same server authentication certificate that is configured on the federation server that this federation server proxy connects to.</span></span>  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a><span data-ttu-id="af6f5-149">自动发现、 Outlook 无处不和 Active Directory 同步的证书</span><span class="sxs-lookup"><span data-stu-id="af6f5-149">Certificates for Autodiscover, Outlook Anywhere, and Active Directory Synchronization</span></span>

<span data-ttu-id="af6f5-p107">面向外部的 Exchange 2013 和 Exchange 2010，Exchange 2007 和 Exchange 2003 客户端访问服务器 (CASs) 的自动发现、 Outlook Anywhere，和 Active Directory 同步服务的安全连接需要第三方 SSL 证书。您可能已经在您的本地环境中安装此证书。</span><span class="sxs-lookup"><span data-stu-id="af6f5-p107">Your external-facing Exchange 2013, Exchange 2010, Exchange 2007, and Exchange 2003 Client Access servers (CASs) require a third-party SSL certificate for secure connections for Autodiscover, Outlook Anywhere, and Active Directory synchronization services. You may already have this certificate installed in your on-premises environment.</span></span>
  
## <a name="certificate-for-an-exchange-hybrid-server"></a><span data-ttu-id="af6f5-152">Exchange 混合服务器的证书</span><span class="sxs-lookup"><span data-stu-id="af6f5-152">Certificate for an Exchange Hybrid Server</span></span>

<span data-ttu-id="af6f5-p108">面向外部的 Exchange 混合服务器要求安全连接与 Exchange Online 服务的第三方 SSL 证书。您需要从第三方 SSL 提供商获取此证书。</span><span class="sxs-lookup"><span data-stu-id="af6f5-p108">Your external-facing Exchange hybrid server or servers require a third-party SSL certificate for secure connectivity with the Exchange Online service. You need to get this certificate from your third-party SSL provider.</span></span>
  
## <a name="office-365-certificate-chains"></a><span data-ttu-id="af6f5-155">Office 365 证书链</span><span class="sxs-lookup"><span data-stu-id="af6f5-155">Office 365 Certificate Chains</span></span>

<span data-ttu-id="af6f5-p109">本文介绍您可能需要在您的基础结构上安装的证书。我们 Office 365 服务器上安装了证书的详细信息，请参阅[Office 365 证书链](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)。</span><span class="sxs-lookup"><span data-stu-id="af6f5-p109">This article describes the certificates you may need to install on your infrastructure. For more information on the certificates installed on our Office 365 servers, see [Office 365 Certificate Chains](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).</span></span>
  

