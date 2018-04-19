---
title: 连接到 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 摘要：使用 Office 365 PowerShell 连接到 Office 365 组织，以通过命令行执行 Office 365 管理中心任务。
ms.openlocfilehash: 71b8c8d61a914fa7fd036fadb7e17ca3f66cd639
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="d4bbb-103">连接到 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d4bbb-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="d4bbb-104">**摘要：**使用 Office 365 PowerShell 连接到 Office 365 组织，以通过命令行执行 Office 365 管理中心任务。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="d4bbb-p101">借助 Office 365 PowerShell，可以通过命令行管理 Office 365 设置。连接到 Office 365 PowerShell 是一个非常简单的三步流程：安装必需软件，运行必需软件，再连接到 Office 365 组织。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

  
> [!TIP]
> <span data-ttu-id="d4bbb-p102">**刚开始接触 PowerShell？**请观看领英学习提供的 [PowerShell 概述](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)视频。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-p102">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="d4bbb-109">开始前，需要知道什么？</span><span class="sxs-lookup"><span data-stu-id="d4bbb-109">What do you need to know before you begin?</span></span>

- <span data-ttu-id="d4bbb-110">估计完成时间：5 分钟</span><span class="sxs-lookup"><span data-stu-id="d4bbb-110">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="d4bbb-111">可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="d4bbb-111">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="d4bbb-112">Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="d4bbb-112">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="d4bbb-113">Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d4bbb-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="d4bbb-p103">请使用 64 位版 Windows。2014 年 10 月，用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块已不再支持 32 位版。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="d4bbb-p104">这些步骤适用于 Office 365 管理角色的成员的用户。有关详细信息，请参阅[有关 Office 365 管理角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-p104">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d4bbb-118">与用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块连接</span><span class="sxs-lookup"><span data-stu-id="d4bbb-118">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d4bbb-119">用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块中的命令在其 cmdlet 名称中具有 **Msol**。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-119">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="d4bbb-120">步骤 1：安装所需软件</span><span class="sxs-lookup"><span data-stu-id="d4bbb-120">Step 1: Install required software</span></span>

<span data-ttu-id="d4bbb-p105">这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="d4bbb-123">安装 64 位版 Microsoft Online Services 登录助手：[适用于 IT 专业人员 RTW 的 Microsoft Online Services 登录助手](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-123">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="d4bbb-124">安装用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，具体步骤如下：</span><span class="sxs-lookup"><span data-stu-id="d4bbb-124">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="d4bbb-125">打开管理员级 PowerShell 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-125">Open an administrator-level PowerShell command prompt.</span></span>
  - <span data-ttu-id="d4bbb-126">运行 **Install-Module MSOnline** 命令。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-126">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="d4bbb-127">如果系统提示安装 NuGet 提供程序，请键入 **Y**，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-127">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="d4bbb-128">如果系统提示从 PSGallery 安装模块，请键入 **Y**，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-128">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="d4bbb-129">安装完成后，关闭 PowerShell 命令窗口。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-129">After installation, close the PowerShell command window.</span></span>
    
### <a name="step-2-connect-to-your-office-365-subscription"></a><span data-ttu-id="d4bbb-130">步骤 2：连接到 Office 365 订阅</span><span class="sxs-lookup"><span data-stu-id="d4bbb-130">Step 2: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="d4bbb-131"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="d4bbb-131"></span></span>

<span data-ttu-id="d4bbb-132">仅使用*帐户名和密码*连接：</span><span class="sxs-lookup"><span data-stu-id="d4bbb-132">To connect with just an *account name and password*:</span></span>
  
1. <span data-ttu-id="d4bbb-133">运行 Windows PowerShell 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-133">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="d4bbb-134">在 **Windows PowerShell** 命令窗口中，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d4bbb-134">In the **Windows PowerShell** command window, run the following commands:</span></span>
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. <span data-ttu-id="d4bbb-135">在"Windows PowerShell 凭据请求"对话框中，键入 Office 365工作或学校帐户 用户名和密码，再单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-135">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="d4bbb-136">使用*多重身份验证 (MFA)* 进行连接的具体步骤：</span><span class="sxs-lookup"><span data-stu-id="d4bbb-136">To connect with *multi-factor authentication (MFA)*:</span></span>
  
1. <span data-ttu-id="d4bbb-137">运行 Windows PowerShell 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-137">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="d4bbb-138">在“用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块”****命令窗口中，运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-138">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
```
Connect-MsolService
```

3. <span data-ttu-id="d4bbb-139">在"Azure Active Directory PowerShell"对话框中，键入你的 Office 365工作或学校帐户 用户名和密码，然后单击"登录"。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-139">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="d4bbb-140">按照"Azure Active Directory PowerShell"对话框中的说明提供其他身份验证信息（如验证码），然后单击"登录"。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-140">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="d4bbb-141">您如何知道这有效？</span><span class="sxs-lookup"><span data-stu-id="d4bbb-141">How do you know this worked?</span></span>
<span data-ttu-id="d4bbb-142"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="d4bbb-142"></span></span>

<span data-ttu-id="d4bbb-p106">如果未收到任何错误，则说明连接成功。一个快速测试是运行 Office 365 cmdlet（例如 **Get-MsolUser** ），然后查看结果。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-p106">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="d4bbb-145">如果收到错误，则查看以下要求：</span><span class="sxs-lookup"><span data-stu-id="d4bbb-145">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="d4bbb-p107">**常见问题是密码错误** 。重新运行步骤 3，并仔细查看您输入的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-p107">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="d4bbb-p108">* *Microsoft Azure 活动目录模块用于 Windows PowerShell 需要 Microsoft.NET Framework 3.5。*在您的计算机 * * 启用 x * 功能。很可能您的计算机已安装了较新的版本 (例如，4 或 4.5。*x *），但可以向后启用或禁用与.NET Framework 的早期版本的兼容性。有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="d4bbb-p108">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.*x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.*x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="d4bbb-151">对于 Windows Server 2012 或 Windows Server 2012 R2，请参阅[使用“添加角色和功能”向导启用 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="d4bbb-151">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="d4bbb-152">对于 Windows 8 或 Windows 8.1，请参阅[在 Windows 8 或 8.1 上安装 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="d4bbb-152">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="d4bbb-153">对于 Windows 7 或 Windows Server 2008 R2，请参阅[不能打开用于 Windows PowerShell 的 Azure Active Directory 模块](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="d4bbb-153">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="d4bbb-p109">**您的 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 版本可能已过期。** 若要进行检查，请在 Office 365 PowerShell 或 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d4bbb-p109">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="d4bbb-156">如果返回的版本号低于值 1.0.8070.2，请卸载 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，并通过第 1 步中的链接安装最新版本。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-156">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="d4bbb-157">**如果看到连接错误，请参阅以下主题：**[“Connect-MsolService：抛出类型异常”错误](https://go.microsoft.com/fwlink/p/?LinkId=532377)。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-157">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d4bbb-158">用图形模块 Azure 活动目录 PowerShell 连接</span><span class="sxs-lookup"><span data-stu-id="d4bbb-158">Connect with the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="d4bbb-159"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="d4bbb-159"></span></span>

<span data-ttu-id="d4bbb-160">中图模块 Azure 活动目录 PowerShell 命令其 cmdlet 名称中有"AzureAD"。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-160">Commands in the Azure Active Directory PowerShell for Graph module have "AzureAD" in their cmdlet name.</span></span>

<span data-ttu-id="d4bbb-161">有关图形模块需要在 Azure 活动目录 PowerShell 的新 cmdlet 的过程，使用这些步骤来安装模块和连接到您的 Office 365 订购。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-161">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="d4bbb-162">有关不同版本的 Microsoft Windows 的支持的信息，请参阅[图形模块 Azure 活动目录 PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) 。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-162">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="d4bbb-163">步骤 1：安装所需软件</span><span class="sxs-lookup"><span data-stu-id="d4bbb-163">Step 1: Install required software</span></span>

<span data-ttu-id="d4bbb-p110">这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>

  
1. <span data-ttu-id="d4bbb-166">打开提升的 Windows PowerShell 命令提示符（以管理员身份运行 Windows PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-166">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="d4bbb-167">在"管理员: Windows PowerShell"命令窗口中，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d4bbb-167">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="d4bbb-168">如果系统提示从不受信任的存储库安装模块，请键入 **Y**，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-168">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>


### <a name="step-2-connect-to-office-365"></a><span data-ttu-id="d4bbb-169">步骤 2：连接到 Office 365</span><span class="sxs-lookup"><span data-stu-id="d4bbb-169">Step 2: Connect to Office 365</span></span>

<span data-ttu-id="d4bbb-170">通过*帐户名和密码*连接到 Office 365 订阅：</span><span class="sxs-lookup"><span data-stu-id="d4bbb-170">To connect to your Office 365 subscription with an *account name and password*:</span></span>
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

<span data-ttu-id="d4bbb-171">在"Windows PowerShell 凭据请求"对话框中，键入 Office 365工作或学校帐户 用户名和密码，再单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-171">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="d4bbb-172">通过*多重身份验证 (MFA)* 连接到 Office 365 订阅：</span><span class="sxs-lookup"><span data-stu-id="d4bbb-172">To connect to your Office 365 subscription with *multi-factor authentication (MFA)*:</span></span>

```
Connect-AzureAD
```

<span data-ttu-id="d4bbb-173">在"Azure Active Directory PowerShell"对话框中，键入你的 Office 365工作或学校帐户 用户名和密码，然后单击"登录"。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-173">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="d4bbb-174">按照"Azure Active Directory PowerShell"对话框中的说明提供其他身份验证信息（如验证码），然后单击"登录"。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-174">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="d4bbb-175">连接后，您可以使用[Azure 的活动目录 PowerShell 图形模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)新 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d4bbb-175">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d4bbb-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4bbb-176">See also</span></span>

- [<span data-ttu-id="d4bbb-177">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="d4bbb-177">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="d4bbb-178">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="d4bbb-178">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="d4bbb-179">在单个 Windows PowerShell 窗口中连接所有 Office 365 服务</span><span class="sxs-lookup"><span data-stu-id="d4bbb-179">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="d4bbb-180">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="d4bbb-180">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="d4bbb-181">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="d4bbb-181">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

