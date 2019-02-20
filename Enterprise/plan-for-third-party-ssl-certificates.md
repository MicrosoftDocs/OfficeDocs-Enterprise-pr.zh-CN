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
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 摘要：介绍了 Exchange 内部部署和混合部署、使用 AD FS 的 SSO、Exchange Online 服务和 Exchange Web 服务所需的 SSL 证书。
ms.openlocfilehash: 3c22daa2315e36c45b5b5dd6271842168c90726d
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085321"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a><span data-ttu-id="1a637-103">Office 365 第三方 SSL 证书计划</span><span class="sxs-lookup"><span data-stu-id="1a637-103">Plan for third-party SSL certificates for Office 365</span></span>

 <span data-ttu-id="1a637-104">**摘要:** 介绍了 exchange 内部部署和混合部署、使用 AD FS 的 SSO、exchange Online services 和 exchange Web 服务所需的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="1a637-104">**Summary:** Describes the SSL certificates needed for Exchange on-premises and hybrid, SSO using AD FS, Exchange Online services, and Exchange Web Services.</span></span> 
  
<span data-ttu-id="1a637-105">若要对客户端和 Office 365 环境之间的通信进行加密, 必须在基础结构服务器上安装第三方安全套接字层 (SSL) 证书。</span><span class="sxs-lookup"><span data-stu-id="1a637-105">To encrypt communications between your clients and the Office 365 environment, third-party Secure Socket Layer (SSL) certificates must be installed on your infrastructure servers.</span></span>

||
|:-----|
| <span data-ttu-id="1a637-106">本文是[Office 365 的网络规划和性能调整](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="1a637-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|
   
<span data-ttu-id="1a637-107">以下 Office 365 组件需要证书：</span><span class="sxs-lookup"><span data-stu-id="1a637-107">Certificates are required for the following Office 365 components:</span></span>
  
- <span data-ttu-id="1a637-108">本地 Exchange</span><span class="sxs-lookup"><span data-stu-id="1a637-108">Exchange on-premises</span></span>
    
- <span data-ttu-id="1a637-109">单一登录 (SSO)（针对 Active Directory 联合身份验证服务 (AD FS) 联合服务器和 AD FS 联合服务器代理）</span><span class="sxs-lookup"><span data-stu-id="1a637-109">Single sign-on (SSO) (for both the Active Directory Federation Services (AD FS) federation servers and AD FS federation server proxies)</span></span>
    
- <span data-ttu-id="1a637-110">exchange Online 服务, 例如自动发现、Outlook 无处不在和 exchange Web 服务</span><span class="sxs-lookup"><span data-stu-id="1a637-110">Exchange Online services, such as Autodiscover, Outlook Anywhere, and Exchange Web Services</span></span>
    
- <span data-ttu-id="1a637-111">Exchange 混合服务器</span><span class="sxs-lookup"><span data-stu-id="1a637-111">Exchange hybrid server</span></span>
    
## <a name="certificates-for-exchange-on-premises"></a><span data-ttu-id="1a637-112">本地 Exchange 的证书</span><span class="sxs-lookup"><span data-stu-id="1a637-112">Certificates for Exchange On-Premises</span></span>

<span data-ttu-id="1a637-113">有关如何使用数字证书在本地 exchange 组织和 Exchange Online 之间进行通信的概述, 请参阅 TechNet 文章 "[了解证书要求](https://go.microsoft.com/fwlink/p/?LinkID=243657)"。</span><span class="sxs-lookup"><span data-stu-id="1a637-113">For an overview about how to use digital certificates to make the communication between the on-premises Exchange organization and Exchange Online secure, see the TechNet article [Understanding Certificate Requirements](https://go.microsoft.com/fwlink/p/?LinkID=243657).</span></span>
  
## <a name="certificates-for-single-sign-on"></a><span data-ttu-id="1a637-114">单一登录的证书</span><span class="sxs-lookup"><span data-stu-id="1a637-114">Certificates for Single Sign-On</span></span>

<span data-ttu-id="1a637-p101">若要向您的用户提供简化的单一登录体验, 其中包括强健的安全性, 联合服务器或联合服务器代理需要下表中所示的证书。下表重点介绍了 Active Directory 联合身份验证服务 (AD FS), 此外, 我们还提供了有关[使用第三方标识提供程序](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1a637-p101">To provide your users with a simplified single sign-on experience that includes robust security, the certificates shown in the following table are required on either the federation servers or the federation server proxies. The table below focuses on Active Directory Federation Services (AD FS), we also have more information on [using third-party identity providers](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="1a637-117">**证书类型**</span><span class="sxs-lookup"><span data-stu-id="1a637-117">**Certificate Type**</span></span> <br/> |<span data-ttu-id="1a637-118">**说明**</span><span class="sxs-lookup"><span data-stu-id="1a637-118">**Description**</span></span> <br/> |<span data-ttu-id="1a637-119">**在部署之前，您需要知道什么？**</span><span class="sxs-lookup"><span data-stu-id="1a637-119">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="1a637-120">**SSL 证书（也称为服务器身份验证证书）**</span><span class="sxs-lookup"><span data-stu-id="1a637-120">**SSL certificate (also called a server authentication certificate)**</span></span> <br/> |<span data-ttu-id="1a637-121">这是标准 SSL 证书，用于确保联合服务器、客户端和联合服务器代理计算机之间的通信的安全。</span><span class="sxs-lookup"><span data-stu-id="1a637-121">This is a standard SSL certificate that is used to make communications between federation servers, clients, and federation server proxy computers secure.</span></span>  <br/> |<span data-ttu-id="1a637-p102">AD FS 需要 SSL 证书。默认情况下, AD FS 使用在 Internet information Services (IIS) 中为默认网站配置的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="1a637-p102">AD FS requires an SSL certificate. By default, AD FS uses the SSL certificate that is configured for the default website in Internet Information Services (IIS).  </span></span><br/> <span data-ttu-id="1a637-p103">此 SSL 证书的使用者名称用于为您部署的每个 AD FS 实例确定联合身份验证服务 (FS) 名称。请考虑为任何新证书颁发机构 (CA) 颁发的证书选择一个使用者名称, 这些证书最能代表您的公司或组织的名称到 Office 365。此名称必须是可通过 Internet 路由的。</span><span class="sxs-lookup"><span data-stu-id="1a637-p103">The subject name of this SSL certificate is used to determine the Federation Service (FS) name for each instance of AD FS that you deploy. Consider choosing a subject name for any new certification authority (CA)-issued certificates that best represents the name of your company or organization to Office 365. This name must be Internet-routable.  </span></span><br/><span data-ttu-id="1a637-127">**警告:** AD FS 要求此 SSL 证书没有无点 (短名称) 使用者名称。</span><span class="sxs-lookup"><span data-stu-id="1a637-127">**Caution:** AD FS requires that this SSL certificate have no dotless (short-name) subject name.</span></span>          <br/> <span data-ttu-id="1a637-128">**建议:** 由于 AD FS 的客户端必须信任此证书, 因此我们建议使用由公用 (第三方) CA 颁发的 SSL 证书, 或由属于公共受信任根的 ca 颁发;例如, VeriSign 或 Thawte。</span><span class="sxs-lookup"><span data-stu-id="1a637-128">**Recommendation:** Because this certificate must be trusted by clients of AD FS, we recommend that you use an SSL certificate issued by a public (third-party) CA or by a CA that is subordinate to a publicly trusted root; for example, VeriSign or Thawte.</span></span>  <br/> |
|<span data-ttu-id="1a637-129">**令牌签名证书**</span><span class="sxs-lookup"><span data-stu-id="1a637-129">**Token-signing certificate**</span></span> <br/> |<span data-ttu-id="1a637-130">这是标准的 x.509 证书, 用于对联合服务器所颁发的所有令牌进行安全签名, 以及 Office 365 接受和验证。</span><span class="sxs-lookup"><span data-stu-id="1a637-130">This is a standard X.509 certificate that's used for securely signing all tokens that the federation server issues and that Office 365 accepts and validates.</span></span>  <br/> |<span data-ttu-id="1a637-p104">令牌签名证书必须包含链接到 FS 中的受信任根的私钥。默认情况下, AD FS 将创建自签名证书。但是, 根据组织的需要, 可以使用 AD FS 管理单元将此证书更改为 CA 颁发的证书。</span><span class="sxs-lookup"><span data-stu-id="1a637-p104">The token-signing certificate must contain a private key that chains to a trusted root in the FS. By default, AD FS creates a self-signed certificate. However, depending on the needs of your organization, you can change this certificate to a CA-issued certificate by using the AD FS management snap-in.  </span></span><br/><span data-ttu-id="1a637-p105">**警告:** 令牌签名证书对 FS 稳定性至关重要。如果证书已更改, 则必须通知 Office 365 的更改。如果未提供通知, 则用户将无法登录到其 Office 365 服务产品。</span><span class="sxs-lookup"><span data-stu-id="1a637-p105">**Caution:** The token-signing certificate is critical to the stability of the FS. If the certificate is changed, Office 365 must be notified of the change. If notification is not provided, users can't sign in to their Office 365 service offerings.</span></span><br/><span data-ttu-id="1a637-p106">**建议:** 建议使用 AD FS 生成的自签名令牌签名证书。这样一来, 它将默认为您管理此证书。例如, 当此证书即将过期时, AD FS 将生成一个新的自签名证书。</span><span class="sxs-lookup"><span data-stu-id="1a637-p106">**Recommendation:** We recommend that you use the self-signed token-signing certificate that is generated by AD FS. By doing so, it manages this certificate for you by default. For example, when this certificate is about to expire, AD FS will generate a new self-signed certificate.  </span></span><br/> |
   
<span data-ttu-id="1a637-140">联合服务器代理需要下表中描述的证书。</span><span class="sxs-lookup"><span data-stu-id="1a637-140">Federation server proxies require the certificate that is described in the following table.</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="1a637-141">**证书类型**</span><span class="sxs-lookup"><span data-stu-id="1a637-141">**Certificate Type**</span></span> <br/> |<span data-ttu-id="1a637-142">**说明**</span><span class="sxs-lookup"><span data-stu-id="1a637-142">**Description**</span></span> <br/> |<span data-ttu-id="1a637-143">**在部署之前，您需要知道什么？**</span><span class="sxs-lookup"><span data-stu-id="1a637-143">**What you need to know before you deploy**</span></span> <br/> |
|<span data-ttu-id="1a637-144">SSL 证书</span><span class="sxs-lookup"><span data-stu-id="1a637-144">SSL certificate</span></span>  <br/> |<span data-ttu-id="1a637-145">这是标准 SSL 证书，用于确保联合服务器、联合服务器代理和 Internet 客户端计算机之间的通信的安全。</span><span class="sxs-lookup"><span data-stu-id="1a637-145">This is a standard SSL certificate that is used for securing communications between a federation server, a federation server proxy, and Internet client computers.</span></span>  <br/> |<span data-ttu-id="1a637-146">必须先将此 SSL 证书绑定到 IIS 中的默认网站, 然后才能成功运行 AD FS 联合服务器代理配置向导。</span><span class="sxs-lookup"><span data-stu-id="1a637-146">This SSL certificate must be bound to the default website in IIS before you can successfully run the AD FS Federation Server Proxy Configuration wizard.</span></span>  <br/> <span data-ttu-id="1a637-147">此证书必须具有与公司网络中联合服务器上配置的 SSL 证书相同的主题名称。</span><span class="sxs-lookup"><span data-stu-id="1a637-147">This certificate must have the same subject name as the SSL certificate that was configured on the federation server in the corporate network.</span></span>  <br/> <span data-ttu-id="1a637-148">**建议：** 建议您使用此联合服务器代理连接到的联合服务器上配置的服务器身份验证证书。</span><span class="sxs-lookup"><span data-stu-id="1a637-148">**Recommendation:** We recommend that you use the same server authentication certificate that is configured on the federation server that this federation server proxy connects to.</span></span>  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a><span data-ttu-id="1a637-149">用于自动发现、Outlook 无处不在和 Active Directory 同步的证书</span><span class="sxs-lookup"><span data-stu-id="1a637-149">Certificates for Autodiscover, Outlook Anywhere, and Active Directory Synchronization</span></span>

<span data-ttu-id="1a637-p107">面向外部的 exchange 2013、exchange 2010、exchange 2007 和 exchange 2003 客户端访问服务器 (CASs) 需要第三方 SSL 证书, 以实现自动发现、Outlook 无处不在和 Active Directory 同步服务的安全连接。您可能已在您的本地环境中安装了此证书。</span><span class="sxs-lookup"><span data-stu-id="1a637-p107">Your external-facing Exchange 2013, Exchange 2010, Exchange 2007, and Exchange 2003 Client Access servers (CASs) require a third-party SSL certificate for secure connections for Autodiscover, Outlook Anywhere, and Active Directory synchronization services. You may already have this certificate installed in your on-premises environment.</span></span>
  
## <a name="certificate-for-an-exchange-hybrid-server"></a><span data-ttu-id="1a637-152">Exchange 混合服务器的证书</span><span class="sxs-lookup"><span data-stu-id="1a637-152">Certificate for an Exchange Hybrid Server</span></span>

<span data-ttu-id="1a637-p108">面向外部的 Exchange 混合服务器需要第三方 SSL 证书, 以实现与 Exchange Online 服务的安全连接。您需要从第三方 SSL 提供商获取此证书。</span><span class="sxs-lookup"><span data-stu-id="1a637-p108">Your external-facing Exchange hybrid server or servers require a third-party SSL certificate for secure connectivity with the Exchange Online service. You need to get this certificate from your third-party SSL provider.</span></span>
  
## <a name="office-365-certificate-chains"></a><span data-ttu-id="1a637-155">Office 365 证书链</span><span class="sxs-lookup"><span data-stu-id="1a637-155">Office 365 Certificate Chains</span></span>

<span data-ttu-id="1a637-p109">本文介绍了您可能需要在基础结构上安装的证书。有关安装在我们的 office 365 服务器上的证书的详细信息, 请参阅[office 365 证书链](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)。</span><span class="sxs-lookup"><span data-stu-id="1a637-p109">This article describes the certificates you may need to install on your infrastructure. For more information on the certificates installed on our Office 365 servers, see [Office 365 Certificate Chains](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).</span></span>
  

