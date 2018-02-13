---
title: "用于 Office 365 开发/测试环境的 DirSync"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, TLG, Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "摘要： 需要配置目录同步为您 Office 365 的开发/测试环境。"
ms.openlocfilehash: fc3a28d52781ba5a541d223c9f8bc081251a2b07
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2018
---
# <a name="dirsync-for-your-office-365-devtest-environment"></a><span data-ttu-id="acd93-103">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="acd93-103">DirSync for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="acd93-104">**摘要：**配置目录同步为您 Office 365 的开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="acd93-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="acd93-p101">许多组织使用 Azure AD Connect 和目录同步 (DirSync)，将其本地 Windows Server Active Directory (AD) 林中的帐户集同步到 Office 365 中的帐户集。本文介绍了如何通过与 Office 365 开发/测试环境的密码同步添加 DirSync，从而生成以下配置。</span><span class="sxs-lookup"><span data-stu-id="acd93-p101">Many organizations use Azure AD Connect and directory synchronization (DirSync) to synchronize the set of accounts in their on-premises Windows Server Active Directory (AD) forest to the set of accounts in Office 365. This article describes how you can add DirSync with password synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![DirSync 的 Office 365 开发/测试环境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="acd93-108">此配置包括： </span><span class="sxs-lookup"><span data-stu-id="acd93-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="acd93-109">Office 365 E5 试用订阅，从你创建它起 30 天内过期。</span><span class="sxs-lookup"><span data-stu-id="acd93-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="acd93-p102">连接到 Internet 的简化的组织 Intranet，包含 Azure 虚拟网络子网中的三个虚拟机（DC1、APP1 和 CLIENT1）。Azure AD Connect 在 APP1 上运行以便使 Windows Server AD 域同步到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="acd93-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the Windows Server AD domain to Office 365.</span></span>
    
<span data-ttu-id="acd93-112">设置此开发/测试环境包含两个阶段：</span><span class="sxs-lookup"><span data-stu-id="acd93-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="acd93-113">创建 Office 365 开发/测试环境（Azure 虚拟网络中的 DC1、APP1 和 CLIENT1 虚拟机，有 Office 365 E5 试用订阅）。</span><span class="sxs-lookup"><span data-stu-id="acd93-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
    
2. <span data-ttu-id="acd93-114">在 APP1 上安装和配置 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="acd93-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="acd93-115">单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。</span><span class="sxs-lookup"><span data-stu-id="acd93-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="acd93-116">第 1 阶段：创建 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="acd93-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="acd93-p103">按照分阶段 1、 2 和 3 的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)文章的说明。下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="acd93-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![Office 365 开发/测试环境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="acd93-120">此配置包括： </span><span class="sxs-lookup"><span data-stu-id="acd93-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="acd93-121">Office 365 E5 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="acd93-121">An Office 365 E5 Trial Subscription.</span></span>
    
- <span data-ttu-id="acd93-122">连接到 Internet 的简化的组织 Intranet，包含 Azure 虚拟网络子网中的 DC1、APP1 和 CLIENT1 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="acd93-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="acd93-123">第 2 阶段：在 APP1 上安装 Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="acd93-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="acd93-p104">安装和配置后，Azure AD Connect 将 CORP Windows Server AD 域中的帐户集与 Office 365 试用订阅中的帐户集同步。下面的过程将引导你完成在 APP1 上安装 Azure AD Connect 并验证它是否可以工作的步骤。</span><span class="sxs-lookup"><span data-stu-id="acd93-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP Windows Server AD domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and verifying that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="acd93-126">安装和配置上 APP1 Azure AD 连接</span><span class="sxs-lookup"><span data-stu-id="acd93-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="acd93-127">从[Azure 的门户](https://portal.azure.com)，连接到与 CORP APP1\\User1 帐户。</span><span class="sxs-lookup"><span data-stu-id="acd93-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="acd93-128">在 APP1 中打开管理员级别的 Windows PowerShell 命令提示符，然后运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="acd93-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="acd93-129">从任务栏中，单击**Internet Explorer** ，然后转到[https://aka.ms/aadconnect](https://aka.ms/aadconnect)。</span><span class="sxs-lookup"><span data-stu-id="acd93-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="acd93-130">在 Microsoft Azure 活动目录连接页面上，单击**下载**，，然后单击**运行**。</span><span class="sxs-lookup"><span data-stu-id="acd93-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="acd93-131">在**欢迎使用 Azure AD 连接**页面上，单击**我同意**，然后单击**继续**。</span><span class="sxs-lookup"><span data-stu-id="acd93-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="acd93-132">在**快速设置**页上，单击**使用快速设置**。</span><span class="sxs-lookup"><span data-stu-id="acd93-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="acd93-133">在**连接到 Azure 的广告**页上，在**用户名，**键入在**密码**的密码键入全局管理员帐户名称，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="acd93-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="acd93-134">在**连接到 AD DS**页上，键入**CORP\\User1**在**用户名，**请在**密码**框中，键入其密码，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="acd93-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="acd93-135">在**Azure 广告登录配置**页上，单击**不经验证的任何域的情况下继续**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="acd93-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="acd93-136">在"准备配置"页上，单击"安装"。</span><span class="sxs-lookup"><span data-stu-id="acd93-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="acd93-137">在**完成配置**页上，单击**退出**。</span><span class="sxs-lookup"><span data-stu-id="acd93-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="acd93-138">在 Internet Explorer 中，请转到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com)) 和 Office 365 试用订阅使用全局管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="acd93-138">In Internet Explorer, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="acd93-139">从主门户页面中，单击**管理**。</span><span class="sxs-lookup"><span data-stu-id="acd93-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="acd93-140">在左边的导航，请单击**用户 > 活动用户**。</span><span class="sxs-lookup"><span data-stu-id="acd93-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="acd93-p105">请注意名为**User1**的帐户。此帐户是从 Windows 服务器 CORP AD 域，工作目录同步的证明。</span><span class="sxs-lookup"><span data-stu-id="acd93-p105">Note the account named **User1**. This account is from the CORP Windows Server AD domain and is proof that DirSync has worked.</span></span>
    
15. <span data-ttu-id="acd93-p106">单击**User1**帐户。产品许可证，请单击**编辑**。</span><span class="sxs-lookup"><span data-stu-id="acd93-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="acd93-p107">**产品许可证**，选择您的国家/地区，并**关闭**控件然后单击**Office 365 企业 E5** （切换为**On**）。单击**保存**底部的页，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="acd93-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="acd93-147">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="acd93-147">This is the resulting configuration.</span></span>
  
![DirSync 的 Office 365 开发/测试环境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="acd93-149">此配置包括： </span><span class="sxs-lookup"><span data-stu-id="acd93-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="acd93-150">Office 365 E5 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="acd93-150">An Office 365 E5 Trial Subscription.</span></span>
    
- <span data-ttu-id="acd93-p108">连接到 Internet 的简化的组织 Intranet，包含 Azure 虚拟网络子网中的 DC1、APP1 和 CLIENT1 虚拟机。Azure AD Connect 在 APP1 上运行以便每隔 30 分钟使 Windows Server AD 域同步到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="acd93-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP Windows Server AD domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="acd93-153">下一步</span><span class="sxs-lookup"><span data-stu-id="acd93-153">Next Step</span></span>

<span data-ttu-id="acd93-154">现在可以为您的组织中部署目录同步，请参阅[部署 Office 365 目录同步 （目录同步） Microsoft Azure 中](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="acd93-154">When you are ready to deploy DirSync for your organization, see [Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="acd93-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="acd93-155">See Also</span></span>

[<span data-ttu-id="acd93-156">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="acd93-156">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="acd93-157">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="acd93-157">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="acd93-158">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="acd93-158">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="acd93-159">Office 365 开发/测试环境的云应用程序安全性</span><span class="sxs-lookup"><span data-stu-id="acd93-159">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="acd93-160">为您的 Office 365 开发/测试环境高级威胁防护</span><span class="sxs-lookup"><span data-stu-id="acd93-160">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="acd93-161">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="acd93-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




