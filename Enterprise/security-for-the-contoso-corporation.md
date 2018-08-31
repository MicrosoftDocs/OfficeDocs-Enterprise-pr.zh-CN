---
title: Contoso Corporation 的安全
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: 摘要： 了解如何 Contoso Microsoft 云服务中的功能映射其安全要求以及确定用于云安全准备的路径。
ms.openlocfilehash: 722c01995c95c36b9975b0682858c38063f79d2c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914827"
---
# <a name="security-for-the-contoso-corporation"></a><span data-ttu-id="56887-103">Contoso Corporation 的安全</span><span class="sxs-lookup"><span data-stu-id="56887-103">Security for the Contoso Corporation</span></span>

 <span data-ttu-id="56887-104">**摘要：** 了解如何 Contoso Microsoft 云服务中的功能映射其安全要求和确定用于云安全准备的路径。</span><span class="sxs-lookup"><span data-stu-id="56887-104">**Summary:** Understand how Contoso mapped their security requirements to features in Microsoft's cloud offerings and determined a path to cloud security readiness.</span></span>
  
<span data-ttu-id="56887-p101">有关其信息安全和保护严重 Contoso。在转换到云包含一个其 IT 基础结构时，他们做确保其本地安全要求已支持并在 Microsoft 云服务中实现。</span><span class="sxs-lookup"><span data-stu-id="56887-p101">Contoso is serious about their information security and protection. When transitioning their IT infrastructure to a cloud-inclusive one, they made sure that their on-premises security requirements were supported and implemented in Microsoft's cloud offerings.</span></span>
  
## <a name="contosos-security-requirements-in-the-cloud"></a><span data-ttu-id="56887-107">在云中的 Contoso 的安全要求</span><span class="sxs-lookup"><span data-stu-id="56887-107">Contoso's security requirements in the cloud</span></span>

<span data-ttu-id="56887-108">下面是 Contoso 对云的安全要求：</span><span class="sxs-lookup"><span data-stu-id="56887-108">Here are Contoso's security requirements for the cloud:</span></span>
  
- <span data-ttu-id="56887-109">对云资源的强身份验证</span><span class="sxs-lookup"><span data-stu-id="56887-109">Strong authentication to cloud resources</span></span>
    
    <span data-ttu-id="56887-110">云资源访问必须经过身份验证，并在可能的情况下利用多重身份验证。</span><span class="sxs-lookup"><span data-stu-id="56887-110">Cloud resource access must be authenticated and, where possible, leverage multi-factor authentication.</span></span>
    
- <span data-ttu-id="56887-111">通过 Internet 的流量加密</span><span class="sxs-lookup"><span data-stu-id="56887-111">Encryption for traffic across the Internet</span></span>
    
    <span data-ttu-id="56887-p102">在 Internet 中没有以纯文本形式发送的数据。始终使用 HTTPS 连接、IPsec 或其他端到端数据加密方法。</span><span class="sxs-lookup"><span data-stu-id="56887-p102">No data sent across the Internet is in plain text form. Always use HTTPS connections, IPsec, or other end-to-end data encryption methods.</span></span>
    
- <span data-ttu-id="56887-114">云中静态数据的加密</span><span class="sxs-lookup"><span data-stu-id="56887-114">Encryption for data at rest in the cloud</span></span>
    
    <span data-ttu-id="56887-115">存储在磁盘上或云中其他地方的所有数据都必须采用加密形式。</span><span class="sxs-lookup"><span data-stu-id="56887-115">All data stored on disks or elsewhere in the cloud must be in an encrypted form.</span></span>
    
- <span data-ttu-id="56887-116">进行最小特权访问的 ACL</span><span class="sxs-lookup"><span data-stu-id="56887-116">ACLs for least privilege access</span></span>
    
    <span data-ttu-id="56887-117">访问云中资源的帐户权限以及允许的操作都必须遵循最小特权原则。</span><span class="sxs-lookup"><span data-stu-id="56887-117">Account permissions to access resources in the cloud and what they are allowed to do must follow least-privilege guidelines.</span></span>
    
## <a name="contosos-data-sensitivity-classification"></a><span data-ttu-id="56887-118">Contoso 的数据敏感度分类</span><span class="sxs-lookup"><span data-stu-id="56887-118">Contoso's data sensitivity classification</span></span>

<span data-ttu-id="56887-119">使用 Microsoft 的[数据分类工具包](https://msdn.microsoft.com/library/hh204743.aspx)中的信息，Contoso 执行其数据分析和确定以下级别。</span><span class="sxs-lookup"><span data-stu-id="56887-119">Using the information in Microsoft's [Data Classification Toolkit](https://msdn.microsoft.com/library/hh204743.aspx), Contoso performed an analysis of their data and determined the following levels.</span></span>
  
|<span data-ttu-id="56887-120">**级别 1：业务价值较低**</span><span class="sxs-lookup"><span data-stu-id="56887-120">**Level 1: Low business value**</span></span>|<span data-ttu-id="56887-121">**级别 2：业务价值中等**</span><span class="sxs-lookup"><span data-stu-id="56887-121">**Level 2: Medium business value**</span></span>|<span data-ttu-id="56887-122">**级别 3：业务价值较高**</span><span class="sxs-lookup"><span data-stu-id="56887-122">**Level 3: High business value**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="56887-123">数据已加密，并且仅供已通过身份验证的用户使用

</span><span class="sxs-lookup"><span data-stu-id="56887-123">Data is encrypted and available only to authenticated users</span></span>  <br/> <span data-ttu-id="56887-p103">向存储在本地和基于云的存储空间和工作负载（例如 Office 365）中的所有数据提供。驻留在服务中和在服务与客户端设备之间传输时，数据处于加密状态。</span><span class="sxs-lookup"><span data-stu-id="56887-p103">Provided for all data stored on premises and in cloud-based storage and workloads, such as Office 365. Data is encrypted while it resides in the service and in transit between the service and client devices.</span></span>  <br/> <span data-ttu-id="56887-126">1 级数据的示例为正常的业务通信（电子邮件）和供管理、销售和支持工作人员使用的文件。</span><span class="sxs-lookup"><span data-stu-id="56887-126">Examples of Level 1 data are normal business communications (email) and files for administrative, sales, and support workers.</span></span>  <br/> |<span data-ttu-id="56887-127">1 级再加上强身份验证和数据丢失防护
</span><span class="sxs-lookup"><span data-stu-id="56887-127">Level 1 plus strong authentication and data loss protection</span></span>  <br/> <span data-ttu-id="56887-p104">强身份验证包括具有 SMS 验证的多重身份验证。数据丢失防护确保敏感或关键的信息不会在本地网络以外出现。
</span><span class="sxs-lookup"><span data-stu-id="56887-p104">Strong authentication includes multi-factor authentication with SMS validation. Data loss prevention ensures that sensitive or critical information does not travel outside the on-premises network.</span></span>  <br/> <span data-ttu-id="56887-130">2 级数据的示例包括财务和法律信息，以及新产品的研发数据。</span><span class="sxs-lookup"><span data-stu-id="56887-130">Examples of Level 2 data are financial and legal information and research and development data for new products.</span></span>  <br/> |<span data-ttu-id="56887-131">2 级再加上最高级别的加密、身份验证和审核
</span><span class="sxs-lookup"><span data-stu-id="56887-131">Level 2 plus the highest levels of encryption, authentication, and auditing</span></span>  <br/> <span data-ttu-id="56887-132">对静态和云中的数据采用最高级别的加密，遵循区域法规，并结合具有智能卡以及精细审核和警报的多重身份验证。
</span><span class="sxs-lookup"><span data-stu-id="56887-132">The highest levels of encryption for data at rest and in the cloud, compliant with regional regulations, combined with multi-factor authentication with smart cards and granular auditing and alerting.</span></span>  <br/> <span data-ttu-id="56887-133">3 级数据的示例是客户和合作伙伴的个人身份信息、产品工程规范以及专有的制造技术。</span><span class="sxs-lookup"><span data-stu-id="56887-133">Examples of Level 3 data are customer and partner personally identifiable information and product engineering specifications and proprietary manufacturing techniques.</span></span>  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a><span data-ttu-id="56887-134">映射到 Contoso 的数据级别的 Microsoft 云服务和功能</span><span class="sxs-lookup"><span data-stu-id="56887-134">Mapping Microsoft cloud offerings and features to Contoso's data levels</span></span>

<span data-ttu-id="56887-135">下表显示 Contoso 的数据级别在 Microsoft 的云产品功能中的映射：</span><span class="sxs-lookup"><span data-stu-id="56887-135">The following table shows the mapping of Contoso's data levels to features in Microsoft's cloud offerings:</span></span>
  
||<span data-ttu-id="56887-136">**SaaS**</span><span class="sxs-lookup"><span data-stu-id="56887-136">**SaaS**</span></span>|<span data-ttu-id="56887-137">**Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="56887-137">**Azure PaaS**</span></span>|<span data-ttu-id="56887-138">**Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="56887-138">**Azure IaaS**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="56887-139">级别 1：业务价值较低</span><span class="sxs-lookup"><span data-stu-id="56887-139">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="56887-140">所有连接的 HTTPS
</span><span class="sxs-lookup"><span data-stu-id="56887-140">HTTPS for all connections</span></span> <br/>  <span data-ttu-id="56887-141">静态加密</span><span class="sxs-lookup"><span data-stu-id="56887-141">Encryption at rest</span></span> <br/> | <span data-ttu-id="56887-142">仅支持 HTTPS 连接
</span><span class="sxs-lookup"><span data-stu-id="56887-142">Support only HTTPS connections</span></span> <br/>  <span data-ttu-id="56887-143">加密存储在 Azure 中的文件</span><span class="sxs-lookup"><span data-stu-id="56887-143">Encrypt files stored in Azure</span></span> <br/> | <span data-ttu-id="56887-144">需要 HTTPS 或 IPsec 进行服务器访问
</span><span class="sxs-lookup"><span data-stu-id="56887-144">Require HTTPS or IPsec for server access</span></span> <br/>  <span data-ttu-id="56887-145">Azure 磁盘加密</span><span class="sxs-lookup"><span data-stu-id="56887-145">Azure disk encryption</span></span> <br/> |
|<span data-ttu-id="56887-146">级别 2：业务价值中等</span><span class="sxs-lookup"><span data-stu-id="56887-146">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="56887-147">具有 SMS 的 Azure AD 多重身份验证 (MFA)</span><span class="sxs-lookup"><span data-stu-id="56887-147">Azure AD multi-factor authentication (MFA) with SMS</span></span> <br/> | <span data-ttu-id="56887-148">用于加密密钥的 Azure 密钥保管库
</span><span class="sxs-lookup"><span data-stu-id="56887-148">Use Azure Key Vault for encryption keys</span></span> <br/>  <span data-ttu-id="56887-149">具有 SMS 的 Azure AD MFA</span><span class="sxs-lookup"><span data-stu-id="56887-149">Azure AD MFA with SMS</span></span> <br/> | <span data-ttu-id="56887-150">具有 SMS 的 MFA</span><span class="sxs-lookup"><span data-stu-id="56887-150">MFA with SMS</span></span> <br/> |
|<span data-ttu-id="56887-151">级别 3：业务价值较高</span><span class="sxs-lookup"><span data-stu-id="56887-151">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="56887-152">Azure 权限管理系统 (RMS)

</span><span class="sxs-lookup"><span data-stu-id="56887-152">Azure Rights Management System (RMS)</span></span> <br/>  <span data-ttu-id="56887-153">具有智能卡的 Azure AD MFA</span><span class="sxs-lookup"><span data-stu-id="56887-153">Azure AD MFA with smart cards</span></span> <br/>  <span data-ttu-id="56887-154">Intune 条件访问</span><span class="sxs-lookup"><span data-stu-id="56887-154">Intune conditional access</span></span> <br/> | <span data-ttu-id="56887-155">Azure RMS</span><span class="sxs-lookup"><span data-stu-id="56887-155">Azure RMS</span></span> <br/>  <span data-ttu-id="56887-156">具有智能卡的 Azure AD MFA</span><span class="sxs-lookup"><span data-stu-id="56887-156">Azure AD MFA with smart cards</span></span> <br/> | <span data-ttu-id="56887-157">具有智能卡的 MFA</span><span class="sxs-lookup"><span data-stu-id="56887-157">MFA with smart cards</span></span> <br/> |
   
## <a name="contosos-information-policies"></a><span data-ttu-id="56887-158">Contoso 的信息策略</span><span class="sxs-lookup"><span data-stu-id="56887-158">Contoso's information policies</span></span>

<span data-ttu-id="56887-159">下表列出了 Contoso 的信息策略。</span><span class="sxs-lookup"><span data-stu-id="56887-159">The following table lists Contoso's information policies.</span></span>
  
||<span data-ttu-id="56887-160">**访问**</span><span class="sxs-lookup"><span data-stu-id="56887-160">**Access**</span></span>|<span data-ttu-id="56887-161">**数据保留**</span><span class="sxs-lookup"><span data-stu-id="56887-161">**Data retention**</span></span>|<span data-ttu-id="56887-162">**信息保护**</span><span class="sxs-lookup"><span data-stu-id="56887-162">**Information protection**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="56887-163">级别 1：业务价值较低</span><span class="sxs-lookup"><span data-stu-id="56887-163">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="56887-164">允许访问所有</span><span class="sxs-lookup"><span data-stu-id="56887-164">Allow access to all</span></span> <br/> |<span data-ttu-id="56887-165">6 个月</span><span class="sxs-lookup"><span data-stu-id="56887-165">6 months</span></span>  <br/> |<span data-ttu-id="56887-166">使用加密</span><span class="sxs-lookup"><span data-stu-id="56887-166">Use encryption</span></span>  <br/> |
|<span data-ttu-id="56887-167">级别 2：业务价值中等</span><span class="sxs-lookup"><span data-stu-id="56887-167">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="56887-168">允许访问 Contoso 员工、分包商和合作伙伴
</span><span class="sxs-lookup"><span data-stu-id="56887-168">Allow access to Contoso employees, subcontractors, and partners</span></span> <br/>  <span data-ttu-id="56887-169">使用 MFA、TLS 和 MAM</span><span class="sxs-lookup"><span data-stu-id="56887-169">Use MFA, TLS, and MAM</span></span> <br/> |<span data-ttu-id="56887-170">2 年</span><span class="sxs-lookup"><span data-stu-id="56887-170">2 years</span></span>  <br/> |<span data-ttu-id="56887-171">使用哈希值实现数据完整性</span><span class="sxs-lookup"><span data-stu-id="56887-171">Use hash values for data integrity</span></span>  <br/> |
|<span data-ttu-id="56887-172">级别 3：业务价值较高</span><span class="sxs-lookup"><span data-stu-id="56887-172">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="56887-173">允许访问工程设计和制造中的执行人员和潜在客户
</span><span class="sxs-lookup"><span data-stu-id="56887-173">Allow access to executives and leads in engineering and manufacturing</span></span> <br/>  <span data-ttu-id="56887-174">仅具有托管网络设备的 RMS</span><span class="sxs-lookup"><span data-stu-id="56887-174">RMS with managed network devices only</span></span> <br/> |<span data-ttu-id="56887-175">7 年</span><span class="sxs-lookup"><span data-stu-id="56887-175">7 years</span></span>  <br/> |<span data-ttu-id="56887-176">使用数字签名实现不可否认性</span><span class="sxs-lookup"><span data-stu-id="56887-176">Use digital signatures for non-repudiation</span></span>  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a><span data-ttu-id="56887-177">云安全准备 Contoso 的路径</span><span class="sxs-lookup"><span data-stu-id="56887-177">Contoso's path to cloud security readiness</span></span>

<span data-ttu-id="56887-178">Contoso 使用以下步骤为 Microsoft 云安全做准备：</span><span class="sxs-lookup"><span data-stu-id="56887-178">Contoso used the following steps to ready their security for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="56887-179">优化云的管理员帐户
</span><span class="sxs-lookup"><span data-stu-id="56887-179">Optimize administrator accounts for the cloud</span></span>
    
    <span data-ttu-id="56887-180">Contoso 对现有的 Windows Sever AD 管理员帐户进行了广泛审阅，并设置了一系列的云管理员帐户和组。</span><span class="sxs-lookup"><span data-stu-id="56887-180">Contoso did an extensive review of the existing Windows Server AD administrator accounts and set up a series of cloud administrator accounts and groups.</span></span>
    
2. <span data-ttu-id="56887-181">按三个级别执行数据分类分析
</span><span class="sxs-lookup"><span data-stu-id="56887-181">Perform data classification analysis into three levels</span></span>
    
    <span data-ttu-id="56887-182">Contoso 执行进行仔细检查并确定的三个级别，用于确定 Microsoft 云提供功能，以保护 Contoso 最有价值的数据。</span><span class="sxs-lookup"><span data-stu-id="56887-182">Contoso performed a careful review and determined the three levels, which was used to determine the Microsoft cloud offering features to protect Contoso's most valuable data.</span></span>
    
3. <span data-ttu-id="56887-183">确定数据级别的访问策略、保留策略和信息保护策略
</span><span class="sxs-lookup"><span data-stu-id="56887-183">Determine access, retention, and information protection policies for data levels</span></span>
    
    <span data-ttu-id="56887-184">Contoso 已根据数据级别确定将用于限定转移到云的未来 IT 工作负载的详细要求。</span><span class="sxs-lookup"><span data-stu-id="56887-184">Based on the data levels, Contoso determined detailed requirements, which will be used to qualify future IT workloads being moved to the cloud.</span></span>
    
## <a name="contosos-use-of-office-365-security-best-practices"></a><span data-ttu-id="56887-185">Contoso 的使用的 Office 365 安全性最佳实践</span><span class="sxs-lookup"><span data-stu-id="56887-185">Contoso's use of Office 365 security best practices</span></span>

<span data-ttu-id="56887-186">按照 Office 365 安全性最佳实践，Contoso 的安全管理员和 IT 部门已部署以下：</span><span class="sxs-lookup"><span data-stu-id="56887-186">In accordance with Office 365 security best practices, Contoso's security administrators and IT department have deployed the following:</span></span>
  
- <span data-ttu-id="56887-187">**专用非常强密码的全局管理员帐户**</span><span class="sxs-lookup"><span data-stu-id="56887-187">**Dedicated global administrator accounts with very strong passwords**</span></span>
    
    <span data-ttu-id="56887-p105">而不是全局管理员角色分配日常的用户帐户，Contoso 具有创建三个，专用非常强密码的全局管理员帐户。有关特定的管理任务只进行登录时的全局管理员帐户和密码仅已知到指定的人员。Contoso 的安全管理员已分配给适用于 IT 人作业功能和责任的帐户的管理员角色。</span><span class="sxs-lookup"><span data-stu-id="56887-p105">Rather than assign the global admin role to everyday user accounts, Contoso has create three, dedicated global administrator accounts with very strong passwords. Signing in with a global administrator account is only done for specific administrative tasks and the passwords are only known to designated staff. Contoso's security administrators have assigned admin roles to accounts that are appropriate to that IT person's job function and responsibility.</span></span>
    
    <span data-ttu-id="56887-191">有关详细信息，请参阅[有关 Office 365 管理员角色](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)。</span><span class="sxs-lookup"><span data-stu-id="56887-191">For more information, see [About Office 365 admin roles](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
- <span data-ttu-id="56887-192">**重要的用户帐户的多因素身份验证 (MFA)**</span><span class="sxs-lookup"><span data-stu-id="56887-192">**Multi-factor authentication (MFA) for important user accounts**</span></span>
    
    <span data-ttu-id="56887-p106">MFA 通过要求用户确认电话呼叫、 短信或其智能电话上正确输入自己的密码后应用程序通知向登录过程额外的保护程序。MFA，与 Office 365 用户帐户会受到未授权登录即使帐户密码受到威胁。</span><span class="sxs-lookup"><span data-stu-id="56887-p106">MFA adds an additional layer of protection to the sign-in process by requiring users to acknowledge a phone call, text message, or an app notification on their smart phone after correctly entering their password. With MFA, Office 365 user accounts are protected against unauthorized sign-in even if an account password is compromised.</span></span>
    
  - <span data-ttu-id="56887-195">防止 Office 365 订阅的泄露，Contoso 上所有三个全局管理员帐户启用 MFA。</span><span class="sxs-lookup"><span data-stu-id="56887-195">To protect against a compromise of the Office 365 subscription, Contoso enabled MFA on all three global administrator accounts.</span></span>
    
  - <span data-ttu-id="56887-196">保护网络钓鱼攻击，攻击损害组织中的受信任的个人的凭据，并发送恶意电子邮件，Contoso MFA 上启用所有用户帐户管理者，包括主管人员。</span><span class="sxs-lookup"><span data-stu-id="56887-196">To protect against phishing attacks, in which an attacker compromises the credentials of a trusted person in the organization and sends malicious emails, Contoso enabled MFA on all user accounts for managers, including the executive staff.</span></span>
    
    <span data-ttu-id="56887-197">有关详细信息，请参阅[规划的 Office 365 部署的多因素身份验证](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span><span class="sxs-lookup"><span data-stu-id="56887-197">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)</span></span>
    
- <span data-ttu-id="56887-198">**高级的安全管理 (ASM)**</span><span class="sxs-lookup"><span data-stu-id="56887-198">**Advanced Security Management (ASM)**</span></span>
    
    <span data-ttu-id="56887-p107">ASM 使用配置策略以监视异常活动。Contoso 安全管理员设置与 ASM 通知，使 IT 管理员通知的不寻常或 risky 用户活动，如下载大量数据，多失败尝试登录时或登录来自未知或危险 IP 地址</span><span class="sxs-lookup"><span data-stu-id="56887-p107">ASM uses configured policies to monitor for anomalous activity. Contoso security administrators set up alerts with ASM so that IT administrators are notified of unusual or risky user activity, such as downloading large amounts of data, multiple failed sign-in attempts, or sign-ins from unknown or dangerous IP addresses</span></span>
    
    <span data-ttu-id="56887-201">有关详细信息，请参阅[概述的高级安全管理 Office 365 中](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。</span><span class="sxs-lookup"><span data-stu-id="56887-201">For more information, see [Overview of Advanced Security Management in Office 365 ](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
    
- <span data-ttu-id="56887-202">**安全电子邮件流和邮箱审核日志记录**</span><span class="sxs-lookup"><span data-stu-id="56887-202">**Secure email flow and mailbox audit logging**</span></span>
    
    <span data-ttu-id="56887-p108">Contoso 安全专家将 Exchange Online Protection 和高级威胁保护 (ATP) 防御未知的恶意软件、 病毒和恶意通过电子邮件传输的 Url。Contoso 也有启用的邮箱审核日志来确定用户登录用户邮箱发送的邮件，和邮箱所有者、 委派的用户或管理员执行的其他活动。</span><span class="sxs-lookup"><span data-stu-id="56887-p108">Contoso security specialists are using Exchange Online Protection and Advanced Threat Protection (ATP) to protect against unknown malware, viruses, and malicious URLs transmitted through emails. Contoso has also enabled mailbox audit logging to determine who has logged into user mailboxes, sent messages, and other activities performed by the mailbox owner, a delegated user, or an administrator.</span></span>
    
    <span data-ttu-id="56887-205">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="56887-205">For more information, see:</span></span> 
    
  - [<span data-ttu-id="56887-206">Office 365 电子邮件反垃圾邮件保护</span><span class="sxs-lookup"><span data-stu-id="56887-206">Office 365 Email Anti-Spam Protection</span></span>](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [<span data-ttu-id="56887-207">安全附件和安全链接的高级威胁保护</span><span class="sxs-lookup"><span data-stu-id="56887-207">Advanced threat protection for safe attachments and safe links</span></span>](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [<span data-ttu-id="56887-208">在 Office 365 中启用邮箱审核</span><span class="sxs-lookup"><span data-stu-id="56887-208">Enable mailbox auditing in Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- <span data-ttu-id="56887-209">**数据丢失防护 (DLP)**</span><span class="sxs-lookup"><span data-stu-id="56887-209">**Data Loss Prevention (DLP)**</span></span>
    
    <span data-ttu-id="56887-210">Contoso 具有标识其敏感数据，并配置了 Exchange Online、 SharePoint Online 和 OneDrive 有助于防止用户无意或有意共享数据的 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="56887-210">Contoso has identified its sensitive data and configured DLP policies for Exchange Online, SharePoint Online, and OneDrive to help prevent users from accidentally or intentionally sharing the data.</span></span> 
    
    <span data-ttu-id="56887-211">有关详细信息，请参阅[数据丢失防护策略概述](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)。</span><span class="sxs-lookup"><span data-stu-id="56887-211">For more information, see [Overview of data loss prevention policies](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="56887-212">See Also</span><span class="sxs-lookup"><span data-stu-id="56887-212">See Also</span></span>

[<span data-ttu-id="56887-213">Microsoft 云中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="56887-213">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="56887-214">Microsoft 云 IT 体系结构资源</span><span class="sxs-lookup"><span data-stu-id="56887-214">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="56887-215">Microsoft 企业云路线图：IT 决策者的资源</span><span class="sxs-lookup"><span data-stu-id="56887-215">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)
  
[<span data-ttu-id="56887-216">Office 365 的安全最佳做法</span><span class="sxs-lookup"><span data-stu-id="56887-216">Security best practices for Office 365</span></span>](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




