---
title: Office 365 开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: 摘要：使用此测试实验室指南创建用于评估或开发/测试的 Office 365 试用订阅。
ms.openlocfilehash: 57fdf66f11d9c71faf81e2a88482093f8f17dfbd
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2018
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="9663e-103">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="9663e-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="9663e-104">**摘要：** 使用此测试实验室指南创建用于评估或开发/测试的 Office 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="9663e-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="9663e-p101">可以使用 Office 365 试用订阅并创建应用程序的 Office 365 开发/测试环境，或演示 Office 365 的特性和功能。有两个版本：</span><span class="sxs-lookup"><span data-stu-id="9663e-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="9663e-107">轻型 Office 365 开发/测试环境包含从你的主计算机进行访问的 Office 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="9663e-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="9663e-p102">当希望快速演示功能时使用此环境。对于轻量级的 Office 365 开发/测试环境，请仅完成本文中的阶段 2 和阶段 3。</span><span class="sxs-lookup"><span data-stu-id="9663e-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="9663e-p103">模拟企业 Office 365 开发/测试环境包含一个 Office 365 试用订阅和一个连接到 Internet 的简化的组织 Intranet（托管在 Microsoft Azure 基础结构服务中）。你可以完全在云中生成此配置。</span><span class="sxs-lookup"><span data-stu-id="9663e-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="9663e-p104">在以下情况下使用此环境：演示功能，或演示类似于连接到 Internet 的典型的组织网络的环境中的应用，或演示需要此类环境的功能。对于模拟的企业 Office 365 开发/测试环境，请完成本文中的阶段 1、阶段 2 和阶段 3。</span><span class="sxs-lookup"><span data-stu-id="9663e-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="9663e-p105">不妨打印这篇文章，以便记录在 30 天的 Office 365 试用订阅期内需要对此环境使用的特定值。可以轻松地将该订阅的试用期再延长 30 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。</span><span class="sxs-lookup"><span data-stu-id="9663e-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Microsoft 云中的测试实验室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="9663e-118">单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="9663e-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="9663e-119">第 1 阶段：在 Azure 中创建基本配置</span><span class="sxs-lookup"><span data-stu-id="9663e-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="9663e-120">按照[基本配置开发/测试环境](base-configuration-dev-test-environment.md)中的说明执行操作。</span><span class="sxs-lookup"><span data-stu-id="9663e-120">Follow the instructions in [Base Configuration Test Environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="9663e-p106">你将需要有一个 Azure 订阅。你可以使用 [Azure 免费试用版](https://azure.microsoft.com/pricing/free-trial/)进行此设置。如果你有 MSDN 或 Visual Studio 订阅，请参阅 [Visual Studio 订阅者的每月 Azure 额度](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。</span><span class="sxs-lookup"><span data-stu-id="9663e-p106">You will need an Azure subscription. You can use the [Azure Free Trialhttps://azure.microsoft.com/pricing/free-trial/](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribershttps://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="9663e-124">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="9663e-124">Here is the resulting configuration.</span></span>
  
![Azure 中的基础配置开发/测试环境](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
<span data-ttu-id="9663e-126">该配置包括 Azure 虚拟网络子网中的 DC1、APP1 和 CLIENT1 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="9663e-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="9663e-127">第 2 阶段：创建 Office 365 试用订阅</span><span class="sxs-lookup"><span data-stu-id="9663e-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="9663e-128">要启动 Office 365 E5 试用订阅，你首先需要一个虚构公司名称和一个新的 Microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="9663e-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="9663e-p107">我们建议你将公司名称 Contoso 的变体用作你的公司名称，它是 Microsoft 示例内容中使用的虚构公司，但这并不是必需的。在此记录虚构的公司名称：![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="9663e-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn’t required. Record your fictitious company name here: _____________________________________![](./images/Common_Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="9663e-p108">要注册新的 Microsoft 帐户，请转到 [https://outlook.com](https://outlook.com)，然后使用新的电子邮件帐户和地址创建一个帐户。此帐户将用于注册 Office 365。</span><span class="sxs-lookup"><span data-stu-id="9663e-p108">To sign up for a new Microsoft account, go to  https://outlook.com https://outlook.com  and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="9663e-133">在此记录新帐户的名字和姓氏：![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="9663e-133">Record the first and last name of your new account here: _______________________________![](./images/Common_Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="9663e-134">在此记录新的电子邮件帐户地址：![](./images/Common_Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="9663e-134">Record the new email account address here: _____________________________@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="9663e-135">注册 Office 365 E5 试用订阅</span><span class="sxs-lookup"><span data-stu-id="9663e-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="9663e-136">对于轻量级的 Office 365 开发/测试环境，打开你的计算机上的 Internet 浏览器并转到 [https://aka.ms/e5trial](https://aka.ms/e5trial)。</span><span class="sxs-lookup"><span data-stu-id="9663e-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to  https://aka.ms/e5trial https://aka.ms/e5trial .</span></span> 
    
    <span data-ttu-id="9663e-137">对于模拟的企业 Office 365 开发/测试环境，请使用 CORP\User1 帐户从 Azure 门户连接到 CLIENT1。</span><span class="sxs-lookup"><span data-stu-id="9663e-137">For the simulated enterprise Office 365 dev/test environment, connect to CLIENT1 with the CORP\User1 account from the Azure portal.</span></span>

    <span data-ttu-id="9663e-138">从“开始”屏幕中，运行 Microsoft Edge 然后转到 [https://aka.ms/e5trial](https://aka.ms/e5trial)。</span><span class="sxs-lookup"><span data-stu-id="9663e-138">From the Start screen, run Microsoft Edge and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="9663e-139">在“欢迎，很高兴认识你”**** 页上，请指定：</span><span class="sxs-lookup"><span data-stu-id="9663e-139">On the **Welcome, let’s get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="9663e-140">你的实际位置</span><span class="sxs-lookup"><span data-stu-id="9663e-140">Your physical location</span></span>
    
  - <span data-ttu-id="9663e-141">你新的 Microsoft 帐户的名字和姓氏</span><span class="sxs-lookup"><span data-stu-id="9663e-141">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="9663e-142">你新的电子邮件帐户地址</span><span class="sxs-lookup"><span data-stu-id="9663e-142">Your new email account address</span></span>
    
  - <span data-ttu-id="9663e-143">业务电话号码</span><span class="sxs-lookup"><span data-stu-id="9663e-143">A business phone number</span></span>
    
  - <span data-ttu-id="9663e-144">你虚构的公司名称</span><span class="sxs-lookup"><span data-stu-id="9663e-144">Your fictional company name</span></span>
    
  - <span data-ttu-id="9663e-145">规模达 250-999 人的组织</span><span class="sxs-lookup"><span data-stu-id="9663e-145">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="9663e-146">单击“只需再执行一步”****。</span><span class="sxs-lookup"><span data-stu-id="9663e-146">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="9663e-147">在“**创建你的用户 ID**”页上，基于你新的电子邮件地址、@ 符号之后你的虚构公司（删除名称中的所有空格）键入用户名，然后为此新的 Office 365 帐户键入密码（两次）。</span><span class="sxs-lookup"><span data-stu-id="9663e-147">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="9663e-148">将你键入的密码记录在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="9663e-148">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="9663e-149">在此记录你的虚构公司名称，将其称为“组织名称”****：![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="9663e-149">Record your fictional company name, to be referred to as the **organization name**, here: ________________________________________</span></span>
    
5. <span data-ttu-id="9663e-150">单击“创建我的帐户”****。</span><span class="sxs-lookup"><span data-stu-id="9663e-150">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="9663e-p109">在“证明你不是机器人”**** 页上，键入可发短信的手机号码，然后单击“给我发短信”****。</span><span class="sxs-lookup"><span data-stu-id="9663e-p109">On the **Prove. You’re. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="9663e-153">键入短信中收到的验证代码，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="9663e-153">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="9663e-154">在此记录登录页面 URL（选择并复制）：![](./images/Common_Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="9663e-154">Record the sign-in page URL here (select and copy): ___________________________________________![](./images/Common_Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="9663e-155">在此记录用户 ID（选择并复制）：![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="9663e-155">Record the user ID here (select and copy): __________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="9663e-156">此值将被称为“Office 365 全局管理员名称”****。</span><span class="sxs-lookup"><span data-stu-id="9663e-156">This value will  be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="9663e-157">看到“你已准备就绪”**** 时，请单击它。</span><span class="sxs-lookup"><span data-stu-id="9663e-157">When you see **You’re ready to go**, click it.</span></span>
    
11. <span data-ttu-id="9663e-158">在下一页，等到 Office 365 完成设置并且显示所有标题。</span><span class="sxs-lookup"><span data-stu-id="9663e-158">On the next page, wait until Office 365 completes setting up and all the tiles under Collaborate with Office Online are visible.</span></span>
    
<span data-ttu-id="9663e-159">你应可看到 Office 365 门户主页，可从该页访问 Office Online 服务和 Office 365 管理中心。</span><span class="sxs-lookup"><span data-stu-id="9663e-159">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="9663e-160">对于模拟的企业 Office 365 的开发/测试环境，以下是你的结果配置。</span><span class="sxs-lookup"><span data-stu-id="9663e-160">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Office 365 开发/测试环境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="9663e-162">此配置包括：</span><span class="sxs-lookup"><span data-stu-id="9663e-162">This configuration consists of:</span></span> 
  
- <span data-ttu-id="9663e-163">Azure 虚拟网络子网中的 DC1、APP1 和 CLIENT1 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="9663e-163">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="9663e-164">Office 365 E5 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="9663e-164">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="9663e-165">第 3 阶段：配置 Office 365 试用订阅</span><span class="sxs-lookup"><span data-stu-id="9663e-165">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="9663e-166">在这个阶段，配置包含其他用户和 SharePoint Online 团队网站的 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="9663e-166">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="9663e-167">首先，添加 4 个新用户并为他们分配 E5 许可证。</span><span class="sxs-lookup"><span data-stu-id="9663e-167">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="9663e-168">使用[连接到 Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) 中的说明，从以下位置安装 PowerShell 模块并连接到新的 Office 365 订阅：</span><span class="sxs-lookup"><span data-stu-id="9663e-168">Use the instructions in [Connect to Office 365 PowerShellhttps://technet.microsoft.com/library/dn975125.aspx](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="9663e-169">你的计算机（对于轻量级的 Office 365 开发/测试环境）。</span><span class="sxs-lookup"><span data-stu-id="9663e-169">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="9663e-170">CLIENT1 虚拟机（对于模拟的企业 Office 365 开发/测试环境）。</span><span class="sxs-lookup"><span data-stu-id="9663e-170">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="9663e-171">在“Windows PowerShell 凭据请求”对话框中，键入 Office 365 全局管理员名称（示例：jdoe@contosotoycompany.onmicrosoft.com）和密码。</span><span class="sxs-lookup"><span data-stu-id="9663e-171">In the Windows PowerShell Credential Request dialog box, type the Office  365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="9663e-172">填写组织名称（示例：contosotoycompany），你所在位置的两位字符的国家/地区代码，然后从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9663e-172">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```
> [!TIP]
> <span data-ttu-id="9663e-173">单击[此处](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34)，可获取包含本文中所有 PowerShell 命令的文本文件。</span><span class="sxs-lookup"><span data-stu-id="9663e-173">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all of the PowerShell commands in this article.</span></span>

<span data-ttu-id="9663e-174">在显示的 **New-MsolUser** 命令中，请注意为 User 2 帐户生成的密码并将其记录在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="9663e-174">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="9663e-175">从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9663e-175">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="9663e-176">在显示的 **New-MsolUser** 命令中，请注意为 User 3 帐户生成的密码并将其记录在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="9663e-176">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="9663e-177">从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9663e-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="9663e-178">在显示的 **New-MsolUser** 命令中，请注意为 User 4 帐户生成的密码并将其记录在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="9663e-178">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="9663e-179">从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9663e-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="9663e-180">在显示的 **New-MsolUser** 命令中，请注意为 User 5 帐户生成的密码并将其记录在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="9663e-180">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="9663e-181">接下来，为销售、生产和支持部门创建三个新的 SharePoint Online 团队网站。</span><span class="sxs-lookup"><span data-stu-id="9663e-181">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="9663e-182">创建 3 个新的 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="9663e-182">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="9663e-183">安装 [SharePoint Online 命令行管理程序](https://go.microsoft.com/fwlink/p/?LinkId=255251)（x64 版本）。</span><span class="sxs-lookup"><span data-stu-id="9663e-183">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="9663e-184">单击“启动”****，键入 **sharepoint**，然后单击“SharePoint Online 命令行管理程序”****。</span><span class="sxs-lookup"><span data-stu-id="9663e-184">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="9663e-185">填写你的组织名称（示例：contosotoycompany），然后从 SharePoint Online Management Shell 提示符中运行以下命令以连接到 SharePoint Online 服务</span><span class="sxs-lookup"><span data-stu-id="9663e-185">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="9663e-186">在“Microsoft SharePoint Online 命令行管理程序”**** 对话框中，键入 Office 365 全局管理员名称（示例：jdoe@contosotoycompany.onmicrosoft.com）和密码，然后单击“登录”****。</span><span class="sxs-lookup"><span data-stu-id="9663e-186">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office  365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="9663e-187">若要创建 3 个新的团队网站（销售、生产和支持），请填入 Office 365 全局管理员名称，然后从 SharePoint Online 命令行管理程序提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9663e-187">To create three new team sites (Sales, Production, and Support), fill in the Office  365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="9663e-188">运行此命令以列出这些新网站的 URL：</span><span class="sxs-lookup"><span data-stu-id="9663e-188">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="9663e-189">在 Internet Explorer 中输入生产网站的 URL，以查看生产部门的默认 SharePoint Online 团队网站。</span><span class="sxs-lookup"><span data-stu-id="9663e-189">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="9663e-190">记录这些值以供将来参考</span><span class="sxs-lookup"><span data-stu-id="9663e-190">Record values for future reference</span></span>

<span data-ttu-id="9663e-191">记录这些值，以便用于或部署此测试环境中的其他测试实验室指南：</span><span class="sxs-lookup"><span data-stu-id="9663e-191">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="9663e-192">Office 365 全局管理员名称：![](./images/Common_Images/TableLine.png).onmicrosoft.com（在第 2 阶段的第 9 步中）</span><span class="sxs-lookup"><span data-stu-id="9663e-192">Office 365 global administrator name: ____________________________________.onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="9663e-193">此外，还应将此帐户的密码记录在安全位置。</span><span class="sxs-lookup"><span data-stu-id="9663e-193">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="9663e-194">试用订阅组织名称：![](./images/Common_Images/TableLine.png)（在第 2 阶段的第 4 步中）</span><span class="sxs-lookup"><span data-stu-id="9663e-194">Your trial subscription organization name: _______________________________________________ (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="9663e-195">要列出 User 2、User 3、User 4 和 User 5 的帐户，从用于 Windows PowerShell 的 Windows Azure Active Directory 模块提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9663e-195">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="9663e-196">在此记录帐户名称：</span><span class="sxs-lookup"><span data-stu-id="9663e-196">Record the account names here:</span></span>
    
  - <span data-ttu-id="9663e-197">User 2 的帐户名称：user2@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="9663e-197">User 2 account name: user2@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="9663e-198">User 3 的帐户名称：user3@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="9663e-198">User 3 account name: user3@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="9663e-199">User 4 的帐户名称：user4@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="9663e-199">User 4 account name: user4@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="9663e-200">User 5 的帐户名称：user5@![](./images/Common_Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="9663e-200">User 5 account name: user5@_______________________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="9663e-201">此外，还应将这些帐户的密码记录在安全位置。</span><span class="sxs-lookup"><span data-stu-id="9663e-201">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="9663e-202">若要列出销售、生产和支持团队网站的 URL，从 SharePoint Online 命令行管理程序提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9663e-202">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="9663e-203">生产网站 URL：https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="9663e-203">Production site URL:  https://______________________________________________.sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="9663e-204">销售网站 URL：https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="9663e-204">Sales site URL: https://______________________________________________.sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="9663e-205">支持网站 URL：https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="9663e-205">Support site URL: https://______________________________________________.sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="9663e-206">后续步骤</span><span class="sxs-lookup"><span data-stu-id="9663e-206">Next steps</span></span>

<span data-ttu-id="9663e-207">在 Office 365 开发/测试环境中使用这些附加的文章：</span><span class="sxs-lookup"><span data-stu-id="9663e-207">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="9663e-208">Office 365 开发/测试环境的目录同步</span><span class="sxs-lookup"><span data-stu-id="9663e-208">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="9663e-209">用于 Office 365 开发/测试环境的多重身份验证</span><span class="sxs-lookup"><span data-stu-id="9663e-209">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="9663e-210">用于 Office 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="9663e-210">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="9663e-211">用于 Office 365 开发/测试环境的云应用安全</span><span class="sxs-lookup"><span data-stu-id="9663e-211">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="9663e-212">Office 365 开发/测试环境中的高级威胁防护</span><span class="sxs-lookup"><span data-stu-id="9663e-212">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="9663e-213">用于 Office 365 开发/测试环境的高级电子数据展示</span><span class="sxs-lookup"><span data-stu-id="9663e-213">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="9663e-214">Office 365 开发/测试环境中的敏感文件保护</span><span class="sxs-lookup"><span data-stu-id="9663e-214">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="9663e-215">独立的 SharePoint Online 团队网站开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="9663e-215">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="9663e-216">Office 365 开发/测试环境中的数据分类和标记</span><span class="sxs-lookup"><span data-stu-id="9663e-216">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="9663e-217">扩展 Office 365 开发/测试环境，将其他 Microsoft 云产品/服务包含在内：</span><span class="sxs-lookup"><span data-stu-id="9663e-217">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="9663e-218">Microsoft 365 企业版开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="9663e-218">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="9663e-219">Office 365 和 Dynamics 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="9663e-219">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="9663e-220">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9663e-220">See Also</span></span>

- [<span data-ttu-id="9663e-221">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="9663e-221">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="9663e-222">Office 365 和 Dynamics 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="9663e-222">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
- [<span data-ttu-id="9663e-223">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="9663e-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


