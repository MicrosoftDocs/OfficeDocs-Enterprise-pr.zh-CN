---
title: "Office 365 开发/测试环境"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: "摘要： 使用此测试实验室指南创建 Office 365 提供试用版订购评估或开发/测试。"
ms.openlocfilehash: b3c9e83dfab3aaf02ad598021e11965657e877bb
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2018
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="2eb6a-103">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="2eb6a-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="2eb6a-104">**摘要：**此测试实验室指南用于创建 Office 365 提供试用版订购评估或开发/测试。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="2eb6a-p101">可以使用 Office 365 试用订阅并创建应用程序的 Office 365 开发/测试环境，或演示 Office 365 的特性和功能。有两个版本：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="2eb6a-107">轻型 Office 365 开发/测试环境包含从你的主计算机进行访问的 Office 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="2eb6a-p102">想在快速演示功能时使用此环境。对于轻量级的 Office 365 开发/测试环境，请完成本文中的阶段 2 和阶段 3。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="2eb6a-p103">模拟企业 Office 365 开发/测试环境包含一个 Office 365 试用订阅和一个连接到 Internet 的简化的组织 Intranet（托管在 Microsoft Azure 基础结构服务中）。你可以完全在云中生成此配置。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="2eb6a-p104">在以下情况下使用此环境：演示功能，或演示类似于连接到 Internet 的典型的组织网络的环境中的应用，或演示需要此类环境的功能。对于模拟的企业 Office 365 开发/测试环境，请完成本文中的阶段 1、阶段 2 和阶段 3。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="2eb6a-p105">不妨打印这篇文章，以便记录在 30 天的 Office 365 试用订阅期内需要对此环境使用的特定值。可以轻松地将该订阅的试用期再延长 30 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Microsoft 云中的测试实验室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="2eb6a-118">单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="2eb6a-119">第 1 阶段：在 Azure 中创建基本配置</span><span class="sxs-lookup"><span data-stu-id="2eb6a-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="2eb6a-120">按照[基本配置开发/测试环境](base-configuration-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="2eb6a-p106">您将需要 Azure 的订阅。对于此配置，可以使用[Azure 免费试用版](https://azure.microsoft.com/pricing/free-trial/)。如果您订阅了 MSDN 或 Visual Studio，请参见[为 Visual Studio 订户每月 Azure 信用](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="2eb6a-124">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-124">Here is the resulting configuration.</span></span>
  
![Azure 中的基础配置开发/测试环境](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
<span data-ttu-id="2eb6a-126">该配置包括 Azure 虚拟网络子网中的 DC1、APP1 和 CLIENT1 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="2eb6a-127">第 2 阶段：创建 Office 365 试用订阅</span><span class="sxs-lookup"><span data-stu-id="2eb6a-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="2eb6a-128">要启动 Office 365 E5 试用订阅，你首先需要一个虚构公司名称和一个新的 Microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="2eb6a-p107">我们建议，Contoso 的公司名称变量，该变量用于您公司的名称，它是 Microsoft 示例内容中使用虚构的公司，但它并不是必需。记录您的虚构公司名称: ___</span><span class="sxs-lookup"><span data-stu-id="2eb6a-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: _____________________________________</span></span>
    
2. <span data-ttu-id="2eb6a-p108">若要注册新的 Microsoft 帐户，转到[https://outlook.com](https://outlook.com)并使用新的电子邮件帐户和地址创建一个帐户。此帐户将用于注册 Office 365。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="2eb6a-133">在此记录新帐户的名字和姓氏：_______________________________</span><span class="sxs-lookup"><span data-stu-id="2eb6a-133">Record the first and last name of your new account here: _______________________________</span></span>
    
  - <span data-ttu-id="2eb6a-134">在此记录新的电子邮件帐户地址：_____________________________@outlook.com</span><span class="sxs-lookup"><span data-stu-id="2eb6a-134">Record the new email account address here: _____________________________@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="2eb6a-135">注册 Office 365 E5 试用订阅</span><span class="sxs-lookup"><span data-stu-id="2eb6a-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="2eb6a-136">轻量的 Office 365 开发/测试环境，打开互联网浏览器在您的计算机上，并转到[https://aka.ms/e5trial](https://aka.ms/e5trial)。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="2eb6a-137">为模拟的企业 Office 365 的开发/测试环境：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-137">For the simulated enterprise Office 365 dev/test environment:</span></span>
    
  - <span data-ttu-id="2eb6a-138">从[Azure 的门户](https://portal.azure.com)，连接到客户端 1 CORP 与\\User1 帐户。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-138">From the [Azure portal](https://portal.azure.com), connect to CLIENT1 with the CORP\\User1 account.</span></span>
    
  - <span data-ttu-id="2eb6a-139">打开管理员级别的 Windows PowerShell 命令提示符，然后运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-139">Open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force
  ```

    > [!TIP]
    > <span data-ttu-id="2eb6a-140">单击[此处](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34)以获取包含本文中的所有 PowerShell 命令的文本文件。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-140">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
  - <span data-ttu-id="2eb6a-141">从开始屏幕中，单击**Internet Explorer** ，然后转到[https://aka.ms/e5trial](https://aka.ms/e5trial)。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-141">From the Start screen, click **Internet Explorer** and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="2eb6a-142">在**欢迎，让我们知道您**的页中，指定：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-142">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="2eb6a-143">你的实际位置</span><span class="sxs-lookup"><span data-stu-id="2eb6a-143">Your physical location</span></span>
    
  - <span data-ttu-id="2eb6a-144">你新的 Microsoft 帐户的名字和姓氏</span><span class="sxs-lookup"><span data-stu-id="2eb6a-144">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="2eb6a-145">你新的电子邮件帐户地址</span><span class="sxs-lookup"><span data-stu-id="2eb6a-145">Your new email account address</span></span>
    
  - <span data-ttu-id="2eb6a-146">业务电话号码</span><span class="sxs-lookup"><span data-stu-id="2eb6a-146">A business phone number</span></span>
    
  - <span data-ttu-id="2eb6a-147">你虚构的公司名称</span><span class="sxs-lookup"><span data-stu-id="2eb6a-147">Your fictional company name</span></span>
    
  - <span data-ttu-id="2eb6a-148">规模达 250-999 人的组织</span><span class="sxs-lookup"><span data-stu-id="2eb6a-148">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="2eb6a-149">单击**只是一个更多的步骤**。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-149">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="2eb6a-150">在**创建您的用户 ID**页中，键入用户名称基于您新的电子邮件地址，您之后的虚构公司 @ 符号 （删除所有名称中包含空格），然后针对此新的 Office 365 提供帐户密码 （两次）。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-150">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="2eb6a-151">将你键入的密码记录在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-151">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="2eb6a-152">记录您的虚构的公司名称，作为该**组织名称**，此处被称为: ___</span><span class="sxs-lookup"><span data-stu-id="2eb6a-152">Record your fictional company name, to be referred to as the **organization name**, here: ________________________________________</span></span>
    
5. <span data-ttu-id="2eb6a-153">单击**我的帐户**。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-153">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="2eb6a-p109">在**上证明。你。不。答： 机器人。**页上，键入的文本功能手机的电话号码，然后单击**文本我**。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="2eb6a-156">键入接收的文本消息的验证代码，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-156">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="2eb6a-157">在此记录登录页面 URL（选择并复制）：___________________________________________</span><span class="sxs-lookup"><span data-stu-id="2eb6a-157">Record the sign-in page URL here (select and copy): ___________________________________________</span></span>
    
9. <span data-ttu-id="2eb6a-158">在此记录用户 ID（选择并复制）：__________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="2eb6a-158">Record the user ID here (select and copy): __________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="2eb6a-159">此值称为**Office 365 全局管理员名称**。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-159">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="2eb6a-160">当看到**你准备就绪**时，请单击它。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-160">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="2eb6a-161">在下一页上，等待，直到 Office 365 提供了完成设置和所有拼块都可用。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-161">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="2eb6a-162">应该可以看到 Office 365 门户主页面，你可以从该页面访问 Office Online 服务和 Office 365 管理中心。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-162">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="2eb6a-163">在模拟的企业 Office 365 的开发/测试环境中，以下是你的结果配置。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-163">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Office 365 开发/测试环境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="2eb6a-165">此配置包括： </span><span class="sxs-lookup"><span data-stu-id="2eb6a-165">This configuration consists of:</span></span> 
  
- <span data-ttu-id="2eb6a-166">Azure 虚拟网络子网中的 DC1、APP1 和 CLIENT1 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-166">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="2eb6a-167">Office 365 E5 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-167">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="2eb6a-168">第 3 阶段：配置 Office 365 试用订阅</span><span class="sxs-lookup"><span data-stu-id="2eb6a-168">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="2eb6a-169">在这个阶段，配置包含其他用户和 SharePoint Online 团队网站的 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-169">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="2eb6a-170">首先，添加四个新用户并为他们分配 E5 许可证。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-170">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="2eb6a-171">使用中的说明[连接到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) PowerShell 模块安装并连接到您新的 Office 365 订阅：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-171">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="2eb6a-172">你的计算机（对于轻量级的 Office 365 开发/测试环境）。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-172">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="2eb6a-173">CLIENT1 虚拟机（对于企业 Office 365 开发/测试环境）。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-173">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="2eb6a-174">在 Windows PowerShell 凭据请求对话框中，键入 Office 365 全局管理员名称 (示例： jdoe@contosotoycompany.onmicrosoft.com) 和密码。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-174">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="2eb6a-175">填写组织名称（示例：contosotoycompany），你所在位置的两位字符的国家/地区代码，然后从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-175">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="2eb6a-176">从**新建 MsolUser**命令显示时，请注意用户 2 帐户生成的密码并将其记录在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-176">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="2eb6a-177">从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="2eb6a-178">从**新建 MsolUser**命令显示时，请注意用户 3 帐户生成的密码并将其记录在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-178">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="2eb6a-179">从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="2eb6a-180">从**新建 MsolUser**命令显示时，请注意用户 4 帐户生成的密码并将其记录在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-180">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="2eb6a-181">从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-181">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="2eb6a-182">从**新建 MsolUser**命令显示时，请注意用户 5 帐户生成的密码并将其记录在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-182">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="2eb6a-183">接下来，为销售、生产和支持部门创建三个新的 SharePoint Online 团队网站。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-183">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="2eb6a-184">创建三个新的 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="2eb6a-184">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="2eb6a-185">安装[SharePoint 在线管理外壳](https://go.microsoft.com/fwlink/p/?LinkId=255251)(x64 版本)。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-185">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="2eb6a-186">单击**开始**，键入**sharepoint**，，然后单击**SharePoint 在线管理外壳**。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-186">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="2eb6a-187">填写你的组织名称（示例：contosotoycompany），然后从 SharePoint Online Management Shell 提示符中运行以下命令以连接到 SharePoint Online 服务</span><span class="sxs-lookup"><span data-stu-id="2eb6a-187">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="2eb6a-188">在**Microsoft SharePoint 在线管理程序**对话框中，键入 Office 365 全局管理员名称 (示例： jdoe@contosotoycompany.onmicrosoft.com) 和密码，然后单击**登录**。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-188">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="2eb6a-189">创建三个新的工作组站点 （销售、 生产和支持），填入 Office 365 全局管理员名称，然后在 SharePoint 在线管理外壳提示符下运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-189">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="2eb6a-190">运行此命令以列出这些新网站的 URL：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-190">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="2eb6a-191">在 Internet Explorer 中输入生产网站的 URL，以查看生产部门的默认 SharePoint Online 团队网站。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-191">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="2eb6a-192">记录值以供将来参考</span><span class="sxs-lookup"><span data-stu-id="2eb6a-192">Record values for future reference</span></span>

<span data-ttu-id="2eb6a-193">记录这些值以便用于或部署此测试环境中的其他测试实验室指南：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-193">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="2eb6a-194">Office 365 全局管理员名称：____________________________________.onmicrosoft.com（在第 2 阶段的第 9 步中）</span><span class="sxs-lookup"><span data-stu-id="2eb6a-194">Office 365 global administrator name: ____________________________________.onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="2eb6a-195">还应将此帐户的密码记录在安全位置。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-195">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="2eb6a-196">试用订阅组织名称：______________________________________________（在第 2 阶段的第 4 步中）</span><span class="sxs-lookup"><span data-stu-id="2eb6a-196">Your trial subscription organization name: _______________________________________________ (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="2eb6a-197">要列出 User 2、User 3、User 4 和 User 5 的帐户，从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-197">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="2eb6a-198">在此记录帐户名：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-198">Record the account names here:</span></span>
    
  - <span data-ttu-id="2eb6a-199">User 2 的帐户名：user2@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="2eb6a-199">User 2 account name: user2@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="2eb6a-200">User 3 的帐户名：user3@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="2eb6a-200">User 3 account name: user3@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="2eb6a-201">User 4 的帐户名：user4@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="2eb6a-201">User 4 account name: user4@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="2eb6a-202">User 5 的帐户名：user5@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="2eb6a-202">User 5 account name: user5@_______________________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="2eb6a-203">还应将这些帐户的密码记录在安全位置。</span><span class="sxs-lookup"><span data-stu-id="2eb6a-203">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="2eb6a-204">若要列出销售、生产和支持团队网站的 URL，从 SharePoint Online Management Shell 提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-204">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="2eb6a-205">生产站点 URL: https://___.sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="2eb6a-205">Production site URL: https://______________________________________________.sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="2eb6a-206">销售网站 URL：https://______________________________________________.sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="2eb6a-206">Sales site URL: https://______________________________________________.sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="2eb6a-207">支持网站 URL：https://______________________________________________.sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="2eb6a-207">Support site URL: https://______________________________________________.sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="2eb6a-208">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2eb6a-208">Next steps</span></span>

<span data-ttu-id="2eb6a-209">在 Office 365 开发/测试环境中使用这些附加的文章：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-209">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="2eb6a-210">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="2eb6a-210">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="2eb6a-211">您的 Office 365 开发/测试环境的的多因素身份验证</span><span class="sxs-lookup"><span data-stu-id="2eb6a-211">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="2eb6a-212">用于 Office 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="2eb6a-212">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="2eb6a-213">Office 365 开发/测试环境的云应用程序安全性</span><span class="sxs-lookup"><span data-stu-id="2eb6a-213">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="2eb6a-214">为您的 Office 365 开发/测试环境高级威胁防护</span><span class="sxs-lookup"><span data-stu-id="2eb6a-214">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="2eb6a-215">高级的 eDiscovery 您 Office 365 的开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="2eb6a-215">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="2eb6a-216">在 Office 365 的开发/测试环境中的敏感文件保护</span><span class="sxs-lookup"><span data-stu-id="2eb6a-216">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="2eb6a-217">SharePoint Online 的团队站点开发/测试环境的独立</span><span class="sxs-lookup"><span data-stu-id="2eb6a-217">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="2eb6a-218">数据分类和标记在 Office 365 的开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="2eb6a-218">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="2eb6a-219">扩展 Office 365 开发/测试环境，将其他 Microsoft 云产品包含在内：</span><span class="sxs-lookup"><span data-stu-id="2eb6a-219">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="2eb6a-220">Microsoft 365 企业开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="2eb6a-220">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="2eb6a-221">Office 365 和 Dynamics 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="2eb6a-221">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="2eb6a-222">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2eb6a-222">See Also</span></span>

[<span data-ttu-id="2eb6a-223">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="2eb6a-223">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="2eb6a-224">Office 365 和 Dynamics 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="2eb6a-224">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="2eb6a-225">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="2eb6a-225">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


