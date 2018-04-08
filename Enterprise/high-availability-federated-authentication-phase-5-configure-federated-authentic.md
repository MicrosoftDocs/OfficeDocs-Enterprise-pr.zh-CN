---
title: 高可用性联合身份验证阶段 5：为 Office 365 配置联合身份验证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: 摘要：在 Microsoft Azure 中为 Office 365 的高可用性联合身份验证配置 Azure AD Connect。
ms.openlocfilehash: 93e872098b31326de67fb0557354e9f4fc1de9ed
ms.sourcegitcommit: a337ac253054f571a8304e18e426f74bcd385857
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2018
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-office-365"></a><span data-ttu-id="a42dd-103">高可用性联合身份验证阶段 5：为 Office 365 配置联合身份验证</span><span class="sxs-lookup"><span data-stu-id="a42dd-103">High availability federated authentication Phase 5: Configure federated authentication for Office 365</span></span>

 <span data-ttu-id="a42dd-104">**摘要：**在 Microsoft Azure 中为 Office 365 的高可用性联合身份验证配置 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="a42dd-104">**Summary:** Configure Azure AD Connect for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
 
<span data-ttu-id="a42dd-p101">此部署高可用性联合身份验证针对 Office 365 提供在 Azure 的基础结构服务的最后一个阶段，在您获得和安装公共证书颁发机构所颁发的证书、 验证您的配置，安装和运行 Azure 的广告目录同步服务器上的连接。Azure AD 连接配置 Office 365 订阅和 Active Directory 联合身份验证服务 (AD FS) 联合身份验证的 web 应用程序代理服务器。</span><span class="sxs-lookup"><span data-stu-id="a42dd-p101">In this final phase of deploying high availability federated authentication for Office 365 in Azure infrastructure services, you get and install a certificate issued by a public certification authority, verify your configuration, and then install and run Azure AD Connect on the directory synchronization server. Azure AD Connect configures your Office 365 subscription and your Active Directory Federation Services (AD FS) and web application proxy servers for federated authentication.</span></span>
  
<span data-ttu-id="a42dd-107">请参阅[在 Azure 中部署 Office 365 的高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)，了解所有阶段。</span><span class="sxs-lookup"><span data-stu-id="a42dd-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a><span data-ttu-id="a42dd-108">获取公钥的证书并将其复制到目录同步服务器</span><span class="sxs-lookup"><span data-stu-id="a42dd-108">Get a public certificate and copy it to the directory synchronization server</span></span>

<span data-ttu-id="a42dd-109">从具有以下属性的公共证书颁发机构获取数字证书：</span><span class="sxs-lookup"><span data-stu-id="a42dd-109">Get a digital certificate from a public certification authority with the following properties:</span></span>
  
- <span data-ttu-id="a42dd-110">适合于创建 SSL 连接的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="a42dd-110">An X.509 certificate suitable for creating SSL connections.</span></span>
    
- <span data-ttu-id="a42dd-111">将使用者可选名称 (SAN) 扩展属性设置为联合身份验证服务 FQDN（示例：fs.contoso.com）。</span><span class="sxs-lookup"><span data-stu-id="a42dd-111">The Subject Alternative Name (SAN) extended property is set to your federation service FQDN (example: fs.contoso.com).</span></span>
    
- <span data-ttu-id="a42dd-112">证书必须具有私钥并以 PFX 格式存储。</span><span class="sxs-lookup"><span data-stu-id="a42dd-112">The certificate must have the private key and be stored in PFX format.</span></span>
    
<span data-ttu-id="a42dd-p102">此外，组织计算机和设备必须信任颁发数字证书的公共证书颁发机构。通过将公共证书颁发机构的一个根证书安装在计算机和设备上的受信任根证书颁发机构存储中来建立这种信任。运行 Microsoft Windows 的计算机通常会安装常用证书颁发机构颁发的这些类型的一系列证书。如果尚未安装公共证书颁发机构提供的根证书，则必须将该证书部署到组织的计算机和设备。</span><span class="sxs-lookup"><span data-stu-id="a42dd-p102">Additionally, your organization computers and devices must trust the public certification authority that is issuing the digital certificate. This trust is established by having a root certificate from the public certification authority installed in the trusted root certification authorities store on your computers and devices. Computers running Microsoft Windows typically have a set of these types of certificates installed from commonly-used certification authorities. If the root certificate from your public certification authority is not already installed, you must deploy this to the computers and devices of your organization.</span></span>
  
<span data-ttu-id="a42dd-117">有关联合身份验证的证书要求的详细信息，请参阅[联合身份验证安装和配置的先决条件](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration)。</span><span class="sxs-lookup"><span data-stu-id="a42dd-117">For more information about certificate requirements for federated authentication, see [Prerequisites for federation installation and configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).</span></span>
  
<span data-ttu-id="a42dd-p103">当您收到该证书时，请将其复制到 c： 驱动器中的目录同步服务器上的文件夹。例如，命名为 SSL.pfx 的文件并将其存储在 c:\\证书目录同步服务器上的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a42dd-p103">When you receive the certificate, copy it to a folder on the C: drive of the directory synchronization server. For example, name the file SSL.pfx and store it in the C:\\Certs folder on the directory synchronization server.</span></span>
  
## <a name="verify-your-configuration"></a><span data-ttu-id="a42dd-120">验证配置</span><span class="sxs-lookup"><span data-stu-id="a42dd-120">Verify your configuration</span></span>

<span data-ttu-id="a42dd-p104">现在，应该准备就绪，可以配置 Azure AD Connect 和 Office 365 的联合身份验证。为确保已就绪，请检查以下清单：</span><span class="sxs-lookup"><span data-stu-id="a42dd-p104">You should now be ready to configure Azure AD Connect and federated authentication for Office 365. To ensure that you are, here is a checklist:</span></span>
  
- <span data-ttu-id="a42dd-123">组织的公共域已添加到 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="a42dd-123">Your organization's public domain is added to your Office 365 subscription.</span></span>
    
- <span data-ttu-id="a42dd-124">组织的 Office 365 用户帐户已配置为组织的公共域名并可以成功登录。</span><span class="sxs-lookup"><span data-stu-id="a42dd-124">Your organization's Office 365 user accounts are configured to your organization's public domain name and can successfully sign in.</span></span>
    
- <span data-ttu-id="a42dd-125">已基于公共域名确定联合身份验证服务 FQDN。</span><span class="sxs-lookup"><span data-stu-id="a42dd-125">You have determined a federation service FQDN based your public domain name.</span></span>
    
- <span data-ttu-id="a42dd-126">联合身份验证服务 FQDN 的公用 DNS A 记录指向用于 Web 应用程序代理服务器的面向 Internet 的 Azure 负载均衡器的公用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a42dd-126">A public DNS A record for your federation service FQDN points to the public IP address of the Internet-facing Azure load balancer for the web application proxy servers.</span></span>
    
- <span data-ttu-id="a42dd-127">联合身份验证服务 FQDN 的专用 DNS A 记录指向用于 AD FS 服务器的内部 Azure 负载均衡器的专用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a42dd-127">A private DNS A record for your federation service FQDN points to the private IP address of the internal Azure load balancer for the AD FS servers.</span></span>
    
- <span data-ttu-id="a42dd-128">公共证书颁发机构 isssued 数码证书适用于与 SAN 到联合身份验证服务设置 SSL 连接 FQDN 将 PFX 文件存储在您的目录同步服务器上。</span><span class="sxs-lookup"><span data-stu-id="a42dd-128">A public certification authority-isssued digital certificate suitable for SSL connections with the SAN set to your federation service FQDN is a PFX file stored on your directory synchronization server.</span></span>
    
- <span data-ttu-id="a42dd-129">公共证书颁发机构的根证书安装在计算机和设备上受信任根证书颁发机构存储中。</span><span class="sxs-lookup"><span data-stu-id="a42dd-129">The root certificate for the public certification authority is installed in the Trusted Root Certification Authorities store on your computers and devices.</span></span>
    
<span data-ttu-id="a42dd-130">下面是 Contoso 组织的一个示例：</span><span class="sxs-lookup"><span data-stu-id="a42dd-130">Here is an example for the Contoso organization:</span></span>
  
<span data-ttu-id="a42dd-131">**Azure 中高可用性联合身份验证基础结构的示例配置**</span><span class="sxs-lookup"><span data-stu-id="a42dd-131">**An example configuration for a high availability federated authentication infrastructure in Azure**</span></span>

![Azure 中高可用性 Office 365 联合身份验证基础结构的示例配置](images/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a><span data-ttu-id="a42dd-133">运行 Azure AD Connect 以配置联合身份验证</span><span class="sxs-lookup"><span data-stu-id="a42dd-133">Run Azure AD Connect to configure federated authentication</span></span>

<span data-ttu-id="a42dd-134">Azure AD Connect 工具通过以下步骤配置 AD FS 服务器、Web 应用程序代理服务器和用于联合身份验证的 Office 365：</span><span class="sxs-lookup"><span data-stu-id="a42dd-134">The Azure AD Connect tool configures the AD FS servers, the web application proxy servers, and Office 365 for federated authentication with these steps:</span></span>
  
1. <span data-ttu-id="a42dd-135">使用具有本地管理员特权的域帐户创建到您的目录同步服务器的远程桌面连接。</span><span class="sxs-lookup"><span data-stu-id="a42dd-135">Create a remote desktop connection to your directory synchronization server with a domain account that has local administrator privileges.</span></span>
    
2. <span data-ttu-id="a42dd-136">从目录同步服务器的桌面，打开 Internet Explorer，并转到[https://aka.ms/aadconnect](https://aka.ms/aadconnect)。</span><span class="sxs-lookup"><span data-stu-id="a42dd-136">From the desktop of the directory synchronization server, open Internet Explorer and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
3. <span data-ttu-id="a42dd-137">在"Microsoft Azure Active Directory Connect"页上，单击"下载"，然后单击"运行"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-137">On the **Microsoft Azure Active Directory Connect** page, click **Download**, and then click **Run**.</span></span>
    
4. <span data-ttu-id="a42dd-138">在"欢迎使用 Azure AD Connect"页上，请依次单击"我同意"、"继续"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-138">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue.**</span></span>
    
5. <span data-ttu-id="a42dd-139">在"快速设置"页上，单击"自定义"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-139">On the **Express Settings** page, click **Customize**.</span></span>
    
6. <span data-ttu-id="a42dd-140">在"安装所需的组件"页上，单击"安装"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-140">On the **Install required components** page, click **Install**.</span></span>
    
7. <span data-ttu-id="a42dd-141">在"用户登录"页上，依次单击"使用 AD FS 进行联合身份验证"和"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-141">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="a42dd-142">在"连接到 Azure AD"页上，键入 Office 365 订阅全局管理员帐户的名称和密码，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-142">On the **Connect to Azure AD** page, type the name and password of a global administrator account for your Office 365 subscription, and then click **Next**.</span></span>
    
9. <span data-ttu-id="a42dd-143">在"连接目录"页上，确保在"林"中选择内部 Windows Server AD 林，键入域管理员帐户的名称和密码，并依次单击"添加目录"和"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-143">On the **Connect your directories** page, ensure that your on-premises Windows Server AD forest is selected in **Forest**, type the name and password of a domain administrator account, click **Add Directory**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="a42dd-144">在"Azure AD 登录配置"页上，单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-144">On the **Azure AD sign-in configuration** page, click **Next**.</span></span>
    
11. <span data-ttu-id="a42dd-145">在"域和 OU 筛选"页上，单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-145">On the **Domain and OU filtering** page, click **Next**.</span></span>
    
12. <span data-ttu-id="a42dd-146">在"唯一标识用户"页上，单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-146">On the **Uniquely identifying your users** page, click **Next**.</span></span>
    
13. <span data-ttu-id="a42dd-147">在"筛选用户和设备"页上，单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-147">On the **Filter users and devices** page, click **Next**.</span></span>
    
14. <span data-ttu-id="a42dd-148">在"可选功能"页上，单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-148">On the **Optional features** page, click **Next**.</span></span>
    
15. <span data-ttu-id="a42dd-149">在"AD FS 场"页上，单击"配置新的 AD FS 场"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-149">On the **AD FS farm** page, click **Configure a new AD FS farm**.</span></span>
    
16. <span data-ttu-id="a42dd-150">单击"浏览"并指定公共证书颁发机构的 SSL 证书的位置和名称。</span><span class="sxs-lookup"><span data-stu-id="a42dd-150">Click **Browse** and specify the location and name of the SSL certificate from the public certification authority.</span></span>
    
17. <span data-ttu-id="a42dd-151">出现提示时，键入证书密码，然后单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-151">When prompted, type the certificate password, and then click **OK**.</span></span>
    
18. <span data-ttu-id="a42dd-152">确认"使用者名称"和"联合身份验证服务名称"已设置为联合身份验证服务 FQDN，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-152">Verify that the **Subject Name** and **Federation Service Name** are set to your federation service FQDN, and then click **Next**.</span></span>
    
19. <span data-ttu-id="a42dd-153">在"AD FS 服务器"页上，键入第一个 AD FS 服务器的名称（表 M - 第 4 项 - 虚拟机名称列），然后单击"添加"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-153">On the **AD FS servers** page, type your first AD FS server's name (Table M - Item 4 - Virtual machine name column), and then click **Add**.</span></span>
    
20. <span data-ttu-id="a42dd-154">键入第二个 AD FS 服务器的名称（表 M - 第 5 项 - 虚拟机名称列），依次单击"添加"、"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-154">Type your second AD FS server's name (Table M - Item 5 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
21. <span data-ttu-id="a42dd-155">在"Web 应用程序代理服务器"页上，键入第一个 Web 应用程序代理服务器的名称（表 M - 第 6 项 - 虚拟机名称列），然后单击"添加"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-155">On the **Web Application Proxy servers** page, type your first web application proxy server's name (Table M - Item 6 - Virtual machine name column), and then click **Add**.</span></span>
    
22. <span data-ttu-id="a42dd-156">键入第二个 Web 应用程序代理服务器的名称（表 M - 第 7 项 - 虚拟机名称列），依次单击"添加"、"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-156">Type your second web application proxy server's name (Table M - Item 7 - Virtual machine name column), click **Add**, and then click **Next**.</span></span>
    
23. <span data-ttu-id="a42dd-157">在"域管理员凭据"页上，键入域管理员帐户的用户名和密码，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-157">On the **Domain Administrator credentials** page, type the user name and password of a domain administrator account, and then click **Next**.</span></span>
    
24. <span data-ttu-id="a42dd-158">在"AD FS 服务帐户"页上，键入企业管理员帐户的用户名和密码，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-158">On the **AD FS service account** page, type the user name and password of an enterprise administrator account, and then click **Next**.</span></span>
    
25. <span data-ttu-id="a42dd-159">在"Azure AD 域"页的"域"中，选择组织的 DNS 域名，然后单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-159">On the **Azure AD Domain** page, in **Domain**, select your organization's DNS domain name, and then click **Next**.</span></span>
    
26. <span data-ttu-id="a42dd-160">在"准备配置"页上，单击"安装"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-160">On the **Ready to configure** page, click **Install**.</span></span>
    
27. <span data-ttu-id="a42dd-p105">在"安装完成"页上，单击"验证"。应该可以看到两条指明 Intranet 和 Internet 配置均已成功验证的消息。</span><span class="sxs-lookup"><span data-stu-id="a42dd-p105">On the **Installation complete** page, click **Verify**. You should see two messages indicating that both the intranet and Internet configuration was successfully verified.</span></span>
    
  - <span data-ttu-id="a42dd-163">Intranet 消息应为 AD FS 服务器列出 Azure 内部负载均衡器的专用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a42dd-163">The intranet message should list the private IP address of your Azure internal load balancer for your AD FS servers.</span></span>
    
  - <span data-ttu-id="a42dd-164">Internet 消息应为 Web 应用程序代理服务器列出面向 Internet 的 Azure 负载均衡器的公用 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="a42dd-164">The Internet message should list the public IP address of your Azure Internet-facing load balancer for your web application proxy servers.</span></span>
    
28. <span data-ttu-id="a42dd-165">在"安装完成"页上，单击"退出"。</span><span class="sxs-lookup"><span data-stu-id="a42dd-165">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="a42dd-166">下面是服务器具有占位符名称的最终配置。</span><span class="sxs-lookup"><span data-stu-id="a42dd-166">Here is the final configuration, with placeholder names for the servers.</span></span>
  
<span data-ttu-id="a42dd-167">**阶段 5：Azure 中高可用性联合身份验证基础结构的最终配置**</span><span class="sxs-lookup"><span data-stu-id="a42dd-167">**Phase 5: The final configuration of a high availability federated authentication infrastructure in Azure**</span></span>

![Azure 中高可用性 Office 365 联合身份验证基础结构的最终配置](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="a42dd-169">Azure 中 Office 365 的高可用性联合身份验证基础结构已完成。</span><span class="sxs-lookup"><span data-stu-id="a42dd-169">Your high availability federated authentication infrastructure for Office 365 in Azure is complete.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a42dd-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a42dd-170">See Also</span></span>

[<span data-ttu-id="a42dd-171">在 Azure 中部署 Office 365 的高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="a42dd-171">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="a42dd-172">用于 Office 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="a42dd-172">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="a42dd-173">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="a42dd-173">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="a42dd-174">Office 365 的联合标识</span><span class="sxs-lookup"><span data-stu-id="a42dd-174">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


