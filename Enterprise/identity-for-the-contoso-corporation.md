---
title: Contoso Corporation 的标识
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
ms.assetid: 78a407e4-2d8b-4561-b308-b22c95f60eeb
description: 摘要： 了解如何 Contoso 利用 IDaaS 提供地理位置分布和冗余其用户身份验证。
ms.openlocfilehash: 25e708147bda51fa8f8b4d0ea5e83eb4a9cd10b0
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915437"
---
# <a name="identity-for-the-contoso-corporation"></a><span data-ttu-id="a7d45-103">Contoso Corporation 的标识</span><span class="sxs-lookup"><span data-stu-id="a7d45-103">Identity for the Contoso Corporation</span></span>

 <span data-ttu-id="a7d45-104">**摘要：** 了解如何 Contoso 利用 IDaaS 并提供地理上分散和冗余其用户身份验证。</span><span class="sxs-lookup"><span data-stu-id="a7d45-104">**Summary:** Understand how Contoso takes advantage of IDaaS and provides geographically distributed and redundant authentication for its users.</span></span>
  
<span data-ttu-id="a7d45-p101">Microsoft 提供的跨其云产品作为 (IDaaS) 的服务标识。采用云之间的基础结构，Contoso 的 IDaaS 解决方案必须利用其本地标识提供程序，包括使用其现有的受信任的第三方身份提供程序的联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="a7d45-p101">Microsoft provides an Identity as a Service (IDaaS) across its cloud offerings. To adopt a cloud-inclusive infrastructure, Contoso's IDaaS solution must leverage their on-premises identity provider and include federated authentication with their existing trusted, third-party identity providers.</span></span>
  
## <a name="contosos-windows-server-ad-forest"></a><span data-ttu-id="a7d45-107">Contoso 的 Windows Server AD 林</span><span class="sxs-lookup"><span data-stu-id="a7d45-107">Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="a7d45-p102">Contoso 借助七个域将单个 Windows Server Active Directory (AD) 林用于 contoso.com，每个域对应世界上的一个地区。总部、区域中心办事处和分支办事处包含用于本地身份验证和授权的域控制器。
</span><span class="sxs-lookup"><span data-stu-id="a7d45-p102">Contoso uses a single Windows Server Active Directory (AD) forest for contoso.com with seven domains, one for each region of the world. The headquarters, regional hub offices, and satellite offices contain domain controllers for local authentication and authorization.</span></span>
  
<span data-ttu-id="a7d45-110">**图 1：全球的 Contoso 林和域**</span><span class="sxs-lookup"><span data-stu-id="a7d45-110">**Figure 1: Contoso's forest and domains worldwide**</span></span>

![Contoso 在世界范围的 Windows Server AD 林和域](media/Contoso-Poster/Contoso-WW-ID.png)
  
<span data-ttu-id="a7d45-112">图 1 显示 Contoso 林和世界各地包含区域中心的区域性域。</span><span class="sxs-lookup"><span data-stu-id="a7d45-112">Figure 1 shows the Contoso forest with regional domains for the different parts of the world that contain regional hubs.</span></span>
  
<span data-ttu-id="a7d45-113">Contoso 想要在 contoso.com 林中使用帐户和组来对其基于云的应用和工作负载进行身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="a7d45-113">Contoso wants to use the accounts and groups in the contoso.com forest for authentication and authorization for its cloud-based apps and workloads.</span></span>
  
## <a name="contosos-federated-authentication-infrastructure"></a><span data-ttu-id="a7d45-114">Contoso 的联合身份验证基础结构</span><span class="sxs-lookup"><span data-stu-id="a7d45-114">Contoso's federated authentication infrastructure</span></span>

<span data-ttu-id="a7d45-115">Contoso 允许：
 


</span><span class="sxs-lookup"><span data-stu-id="a7d45-115">Contoso allows:</span></span>
  
- <span data-ttu-id="a7d45-116">客户使用 Microsoft、Facebook 或 Google Mail 帐户登录其公共网站。</span><span class="sxs-lookup"><span data-stu-id="a7d45-116">Customers to use their Microsoft, Facebook, or Google Mail accounts to sign in to their public web site.</span></span>
    
- <span data-ttu-id="a7d45-117">供应商和合作伙伴使用 LinkedIn、Salesforce 或 Google Mail 帐户登录合作伙伴 Extranet。</span><span class="sxs-lookup"><span data-stu-id="a7d45-117">Vendors and partners to use their LinkedIn, Salesforce, or Google Mail accounts to sign in to the partner extranet.</span></span>
    
<span data-ttu-id="a7d45-118">**图 2：Contoso 对客户和合作伙伴的联合身份验证支持**</span><span class="sxs-lookup"><span data-stu-id="a7d45-118">**Figure 2: Contoso's support for federated authentication for customers and partners**</span></span>

![Contoso 的现有基础结构对客户和合作伙伴的联合身份验证的支持](media/Contoso-Poster/Federated-ID.png)
  
<span data-ttu-id="a7d45-p103">图 2 显示包含一个公共网站、一个合作伙伴 Extranet 和一组 AD FS 服务器的 Contoso DMZ。DMZ 已连接至包含客户和合作伙伴与 Internet 服务的 Internet。</span><span class="sxs-lookup"><span data-stu-id="a7d45-p103">Figure 2 shows the Contoso DMZ containing a public web site, a partner extranet, and a set of AD FS servers. The DMZ is connected to the Internet that contains customers and partners and Internet services.</span></span>
  
<span data-ttu-id="a7d45-122">DMZ 中的 Active Directory 联合身份验证服务 (AD FS) 服务器对客户凭据进行身份验证以访问公共网站，并对合作伙伴凭据进行身份验证以访问合作伙伴 Extranet。</span><span class="sxs-lookup"><span data-stu-id="a7d45-122">Active Directory Federation Services (AD FS) servers in the DMZ authenticate customer credentials for access to the public web site and partner credentials for access to the partner extranet.</span></span>
  
<span data-ttu-id="a7d45-p104">当 Contoso 转换到 Azure Web App 和合作伙伴 extranet Dynamics 365 到其公共网站时，他们希望继续使用这些第三方身份提供程序其客户和合作伙伴。这将通过配置 Contoso Azure AD 租户和这些第三方身份提供程序之间的联盟。</span><span class="sxs-lookup"><span data-stu-id="a7d45-p104">When Contoso transitions its public web site to an Azure Web App and partner extranet to Dynamics 365, they want to continue to use these third-party identity providers for their customers and partners. This will be accomplished by configuring federation between Contoso Azure AD tenants and these third-party identity providers.</span></span>
  
## <a name="directory-synchronization-for-contosos-windows-server-ad-forest"></a><span data-ttu-id="a7d45-125">Contoso 的 Windows Server AD 林目录同步</span><span class="sxs-lookup"><span data-stu-id="a7d45-125">Directory synchronization for Contoso's Windows Server AD forest</span></span>

<span data-ttu-id="a7d45-p105">Contoso 已部署 Azure AD 连接工具在其巴黎数据中心中的服务器群集。Azure AD 连接将与 Azure AD 租户 Contoso 的 Office 365、 EMS、 Dynamics 365 和 Azure 订阅由共享同步到 contoso.com Windows Server AD 林的更改。有关订阅、 许可证、 用户帐户和租户的详细信息，请参阅[订阅、 许可证和 Contoso Corporation 的用户帐户](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)。</span><span class="sxs-lookup"><span data-stu-id="a7d45-p105">Contoso has deployed the Azure AD Connect tool on a cluster of servers in its Paris datacenter. Azure AD Connect synchronizes changes to the contoso.com Windows Server AD forest with the Azure AD tenant shared by Contoso's Office 365, EMS, Dynamics 365, and Azure subscriptions. For more information about subscriptions, licenses, user accounts, and tenants, see [Subscriptions, licenses, and user accounts for the Contoso Corporation](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md).</span></span>
  
<span data-ttu-id="a7d45-129">**图 3：Contoso 的目录同步基础结构**</span><span class="sxs-lookup"><span data-stu-id="a7d45-129">**Figure 3: Contoso's directory synchronization infrastructure**</span></span>

![Contoso 的目录同步基础结构](media/Contoso-Poster/DirSync.png)
  
<span data-ttu-id="a7d45-131">图 3 显示运行 Azure AD Connect、将 Contoso Windows Server AD 林与 Azure AD 租户同步的服务器群集</span><span class="sxs-lookup"><span data-stu-id="a7d45-131">Figure 3 shows a cluster of servers running Azure AD Connect synchronizing the Contoso Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="a7d45-p106">Contoso 已配置联合身份验证，Contoso 的工作者提供单一登录。当用户具有已登录到 contoso.com Windows Server AD 林的访问 Microsoft SaaS 或 PaaS 云资源时，它们将不会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="a7d45-p106">Contoso has configured federated authentication, which provides single sign-on for Contoso's workers. When a user that has already signed in to the contoso.com Windows Server AD forest accesses a Microsoft SaaS or PaaS cloud resource, they will not be prompted for a password.</span></span>
  
## <a name="geographical-distribution-of-contoso-authentication-traffic"></a><span data-ttu-id="a7d45-134">Contoso 身份验证流量的地理分布情况</span><span class="sxs-lookup"><span data-stu-id="a7d45-134">Geographical distribution of Contoso authentication traffic</span></span>

<span data-ttu-id="a7d45-p107">为了更好地支持其移动和远程工作人员，Contoso 已在其区域办事处中部署了数个身份验证服务器集。此基础结构分散负载，并在对用户凭据进行身份验证以访问使用常见的 Azure AD 租户的 Microsoft 云产品时提供冗余和更高的性能。
</span><span class="sxs-lookup"><span data-stu-id="a7d45-p107">To better support its mobile and remote workforce, Contoso has deployed sets of authentication servers in its regional offices. This infrastructure distributes the load and provides redundancy and higher performance when authenticating user credentials for access to Microsoft cloud offerings that use the common Azure AD tenant.</span></span>
  
<span data-ttu-id="a7d45-137">为分散身份验证请求的负载，Contoso 已通过使用性能路由方法的配置文件来配置 Azure 流量管理器，该方法将身份验证客户端引入区域上最近的身份验证服务器集。 </span><span class="sxs-lookup"><span data-stu-id="a7d45-137">To distribute the load of authentication requests, Contoso has configured Azure Traffic Manager with a profile that uses the performance routing method, which refers authenticating clients to the regionally closest set of authentication servers.</span></span> 
  
<span data-ttu-id="a7d45-138">**图 4：Contoso 区域办事处身份验证流量的地理分布情况**</span><span class="sxs-lookup"><span data-stu-id="a7d45-138">**Figure 4: Geographical distribution of authentication traffic for regional offices**</span></span>

![Contoso 区域办事处身份验证流量的地理分布情况](media/Contoso-Poster/Auth-GeoDist.png)
  
<span data-ttu-id="a7d45-p108">图 4 显示区域办事处的客户端计算机层、Azure 流量管理器和身份验证服务器。每个区域办事处都使用 Web 代理和 AD FS 服务器来通过 Windows Server AD 域控制器对用户凭据进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="a7d45-p108">Figure 4 shows the layers of client computers, Azure Traffic Manager, and authentication servers in regional offices. Each regional office uses web proxies and AD FS servers to authenticate user credentials with Windows Server AD domain controllers.</span></span>
  
<span data-ttu-id="a7d45-142">身份验证过程示例：</span><span class="sxs-lookup"><span data-stu-id="a7d45-142">Authentication process example:</span></span>
  
1. <span data-ttu-id="a7d45-143">客户端计算机启动与欧洲 Office 365 租赁中某个网页（如 sharepoint.contoso.com）的通信。


</span><span class="sxs-lookup"><span data-stu-id="a7d45-143">The client computer initiates communication with a web page in the Office 365 tenancy in Europe (such as sharepoint.contoso.com).</span></span>
    
2. <span data-ttu-id="a7d45-p109">Office 365 发回发送身份验证证明的请求。该请求包含联系身份验证的 URL。</span><span class="sxs-lookup"><span data-stu-id="a7d45-p109">Office 365 sends back a request to send proof of authentication. The request contains the URL to contact for authentication.</span></span>
    
3. <span data-ttu-id="a7d45-146">客户端计算机尝试将 URL 中的 DNS 名称解析为 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a7d45-146">The client computer attempts to resolve the DNS name in the URL to an IP address.</span></span>
    
4. <span data-ttu-id="a7d45-147">Azure 流量管理器通过最接近客户端计算机的区域办事处的 Web 应用程序代理服务器的 IP 地址来接收 DNS 查询并响应客户端计算机。</span><span class="sxs-lookup"><span data-stu-id="a7d45-147">Azure Traffic Manager receives the DNS query and responds to the client computer with the IP address of a web application proxy server in the regional office that is closest to the client computer.</span></span>
    
5.  <span data-ttu-id="a7d45-148"> 客户端计算机向 Web 应用程序代理服务器发送身份验证请求，代理服务器会将此请求转发到 AD FS 服务器。



</span><span class="sxs-lookup"><span data-stu-id="a7d45-148">The client computer sends an authentication request to a web application proxy server, which forwards the request to an AD FS server.</span></span>
    
6. <span data-ttu-id="a7d45-149">AD FS 服务器从客户端计算机请求用户凭据。</span><span class="sxs-lookup"><span data-stu-id="a7d45-149">The AD FS server requests the user credentials from the client computer.</span></span>
    
7. <span data-ttu-id="a7d45-150">客户端计算机发送用户凭据，而不提示用户。</span><span class="sxs-lookup"><span data-stu-id="a7d45-150">The client computer sends the user credentials without prompting the user.</span></span>
    
8. <span data-ttu-id="a7d45-151">AD FS 服务器使用区域办事处中的 Windows Server AD 域控制器来验证凭据，并向客户端计算机返回安全令牌。</span><span class="sxs-lookup"><span data-stu-id="a7d45-151">The AD FS server validates the credentials with a Windows Server AD domain controller in the regional office and returns a security token to the client computer.</span></span>
    
9. <span data-ttu-id="a7d45-152">客户端计算机向 Office 365 发送安全令牌。</span><span class="sxs-lookup"><span data-stu-id="a7d45-152">The client computer sends the security token to Office 365.</span></span>
    
10. <span data-ttu-id="a7d45-153">成功验证之后，Office 365 缓存安全令牌并向客户端计算机发送在步骤 1 中请求的网页。</span><span class="sxs-lookup"><span data-stu-id="a7d45-153">After successful validation, Office 365 caches the security token and sends the web page requested in step 1 to the client computer.</span></span>
    
## <a name="redundancy-for-the-headquarters-authentication-infrastructure-in-azure-iaas"></a><span data-ttu-id="a7d45-154">Azure IaaS 中总部身份验证基础结构的冗余</span><span class="sxs-lookup"><span data-stu-id="a7d45-154">Redundancy for the headquarters authentication infrastructure in Azure IaaS</span></span>

<span data-ttu-id="a7d45-155">为了给包含 15,000 名工作人员的巴黎总部的远程和移动工作人员提供冗余，Contoso 已在 Azure IaaS 中部署第二组应用程序代理和 AD FS 服务器。
</span><span class="sxs-lookup"><span data-stu-id="a7d45-155">To provide redundancy for the remote and mobile workers of the Paris headquarters that contains 15,000 workers, Contoso has deployed a second set of application proxies and AD FS servers in Azure IaaS.</span></span>
  
<span data-ttu-id="a7d45-156">**图 5：Azure IaaS 中的冗余身份验证基础结构**</span><span class="sxs-lookup"><span data-stu-id="a7d45-156">**Figure 5: Redundant authentication infrastructure in Azure IaaS**</span></span>

![Azure IaaS 中巴黎总部的冗余身份验证基础结构](media/Contoso-Poster/Paris-Auth-Redun.png)
  
<span data-ttu-id="a7d45-158">图 5 显示 DMZ 中的 Web 代理和 AD FS 服务器，以及跨界 Azure 虚拟网络中一个额外的 Web 代理和 AD FS 服务器组。</span><span class="sxs-lookup"><span data-stu-id="a7d45-158">Figure 5 shows web proxies and AD FS servers in the DMZ and an additional set of each in a cross-premises Azure virtual network.</span></span>
  
<span data-ttu-id="a7d45-p110">当总部 DMZ 中的主要身份验证服务器不可用时，IT 人员就切换到部署在 Azure IaaS 中的冗余组。来自巴黎办事处计算机的后续身份验证请求使用 Azure IaaS 中的组，直到对可用性问题进行修正。</span><span class="sxs-lookup"><span data-stu-id="a7d45-p110">When the primary authentication servers in the headquarters DMZ become unavailable, IT staff switch over to the redundant set deployed in Azure IaaS. Subsequent authentication requests from Paris office computers use the set in Azure IaaS until the availability problem is corrected.</span></span>
  
<span data-ttu-id="a7d45-161">若要进行来回切换，Contoso 需要更新巴黎区域的 Azure 流量管理器配置文件，来为 Web 应用程序代理使用一组不同的 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="a7d45-161">To switch over and switch back, Contoso updates the Azure Traffic Manager profile for the Paris region to use a different set of IP addresses for the web application proxies:</span></span>
  
- <span data-ttu-id="a7d45-162">DMZ 身份验证服务器可用时，请使用 DMZ 中服务器的 IP 地址。
</span><span class="sxs-lookup"><span data-stu-id="a7d45-162">When the DMZ authentication servers are available, use the IP addresses of the servers in the DMZ.</span></span>
    
- <span data-ttu-id="a7d45-163">DMZ 身份验证服务器不可用时，请使用 Azure IaaS 中服务器的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a7d45-163">When the DMZ authentication servers are not available, use the IP addresses of the servers in Azure IaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="a7d45-164">See Also</span><span class="sxs-lookup"><span data-stu-id="a7d45-164">See Also</span></span>

[<span data-ttu-id="a7d45-165">Microsoft 云中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="a7d45-165">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="a7d45-166">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="a7d45-166">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="a7d45-167">面向企业架构师的 Microsoft 云标识</span><span class="sxs-lookup"><span data-stu-id="a7d45-167">Microsoft Cloud Identity for Enterprise Architects</span></span>](http://aka.ms/cloudarchidentity)
  
[<span data-ttu-id="a7d45-168">Office 365 的标识和设备保护</span><span class="sxs-lookup"><span data-stu-id="a7d45-168">Identity and Device Protection for Office 365</span></span>](http://aka.ms/o365protect_device)
  
[<span data-ttu-id="a7d45-169">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="a7d45-169">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



