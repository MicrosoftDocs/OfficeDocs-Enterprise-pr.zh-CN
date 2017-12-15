---
title: "连接到 Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- DecEntMigration
- apr17entnews
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "摘要： 连接到 Office 365 单位使用 Office 365 PowerShell 从命令行执行 Office 365 管理的中心任务。"
ms.openlocfilehash: 3ac368a3d3584c15e1d0c26104616e8258a78e7b
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="95ddd-103">连接到 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="95ddd-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="95ddd-104">**摘要：**连接到您的 Office 365 组织使用 Office 365 PowerShell 从命令行执行 Office 365 管理任务。</span><span class="sxs-lookup"><span data-stu-id="95ddd-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="95ddd-p101">Office 365 PowerShell 允许您从命令行管理您 Office 365 的设置。连接到 Office 365 PowerShell 是一个简单的三步过程，安装必需的软件，运行所需的软件，然后连接到您的 Office 365 组织。</span><span class="sxs-lookup"><span data-stu-id="95ddd-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="95ddd-107">请注意，这些连接的说明主题[Azure 与 active Directory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113)中的相同。</span><span class="sxs-lookup"><span data-stu-id="95ddd-107">Note that these connection instructions are the same as those in the topic [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span></span>
  
> [!TIP]
> <span data-ttu-id="95ddd-p102">**新到 PowerShell？**请参阅[视频 PowerShell 概述](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)，LinkedIn 学习者。</span><span class="sxs-lookup"><span data-stu-id="95ddd-p102">**New to PowerShell?** See a [video Overview of PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="95ddd-110">在开始之前，您需要知道什么？</span><span class="sxs-lookup"><span data-stu-id="95ddd-110">What do you need to know before you begin?</span></span>

- <span data-ttu-id="95ddd-111">估计完成时间：5 分钟</span><span class="sxs-lookup"><span data-stu-id="95ddd-111">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="95ddd-112">可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="95ddd-112">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="95ddd-113">Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="95ddd-113">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="95ddd-114">Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="95ddd-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="95ddd-p103">使用 64 位版本的 Windows。在 10 月的 2014年已停产的 32 位版本 Microsoft Azure 活动目录模块用于 Windows PowerShell 支持。</span><span class="sxs-lookup"><span data-stu-id="95ddd-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="95ddd-p104">Office 365 的工作或学校对使用这些过程需要 Office 365 管理角色的成员的帐户。有关详细信息，请参阅[有关 Office 365 管理角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。</span><span class="sxs-lookup"><span data-stu-id="95ddd-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>
    
## <a name="step-1-install-required-software"></a><span data-ttu-id="95ddd-119">步骤 1：安装所需软件</span><span class="sxs-lookup"><span data-stu-id="95ddd-119">Step 1: Install required software</span></span>

<span data-ttu-id="95ddd-p105">这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。</span><span class="sxs-lookup"><span data-stu-id="95ddd-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="95ddd-122">安装 64 位版本的 Microsoft 联机服务注册助理： [Microsoft 在线服务登录的助手为 IT 专业人员的一项](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="95ddd-122">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="95ddd-123">使用以下步骤安装 64 位版本的 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块：</span><span class="sxs-lookup"><span data-stu-id="95ddd-123">Install the 64-bit version of the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="95ddd-124">打开 [Azure Active Directory 连接](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185)网页。</span><span class="sxs-lookup"><span data-stu-id="95ddd-124">Open the [Azure Active Directory Connection](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) web page.</span></span>
    
  - <span data-ttu-id="95ddd-125">在页面底部的**下载中的文件**， **AdministrationConfig-V1.1.166.0-GA.msi**文件中，单击**下载**，然后安装它。</span><span class="sxs-lookup"><span data-stu-id="95ddd-125">In **Files in Download** at the bottom of the page, click **Download** for the **AdministrationConfig-V1.1.166.0-GA.msi** file, and then install it.</span></span>
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a><span data-ttu-id="95ddd-126">步骤 2：打开 Windows Azure Active Directory 模块</span><span class="sxs-lookup"><span data-stu-id="95ddd-126">Step 2: Open the Windows Azure Active Directory Module</span></span>

1. <span data-ttu-id="95ddd-127">使用以下某个基于 Windows 版本的方法查找并打开 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块：</span><span class="sxs-lookup"><span data-stu-id="95ddd-127">Find and open the Microsoft Azure Active Directory Module for Windows PowerShell by using one of the following methods based on your version of Windows:</span></span>
    
  - <span data-ttu-id="95ddd-128">**「 开始 」 菜单**在桌面上，单击**开始**，然后键入 Azure。</span><span class="sxs-lookup"><span data-stu-id="95ddd-128">**Start menu** From the desktop, click **Start**, and then type Azure.</span></span>
    
  - <span data-ttu-id="95ddd-129">**没有"开始"菜单** 使用下列任一方法搜索"Azure"：</span><span class="sxs-lookup"><span data-stu-id="95ddd-129">**No Start menu** Search forAzure using any of these methods:</span></span>
    
  - <span data-ttu-id="95ddd-130">在"开始"屏幕中，单击空白区域，并键入"Azure"。</span><span class="sxs-lookup"><span data-stu-id="95ddd-130">On the Start screen, click an empty area, and type Azure.</span></span>
    
  - <span data-ttu-id="95ddd-p106">在桌面或"开始"屏幕上，按下 Windows 键 + Q。在"搜索"超级按钮中，键入"Azure"。</span><span class="sxs-lookup"><span data-stu-id="95ddd-p106">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Azure.</span></span>
    
  - <span data-ttu-id="95ddd-p107">在桌面或开始屏幕上，将光标移动到右上角或刷从右向左，从屏幕来显示魅力的右边缘。选择搜索超级按钮，然后键入**Azure**。</span><span class="sxs-lookup"><span data-stu-id="95ddd-p107">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and type **Azure**.</span></span>
    
2. <span data-ttu-id="95ddd-135">在结果中，单击"用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块"。</span><span class="sxs-lookup"><span data-stu-id="95ddd-135">In the results, click **Microsoft Azure Active Directory Module for Windows PowerShell**.</span></span>
    
## <a name="step-3-connect-to-your-office-365-subscription"></a><span data-ttu-id="95ddd-136">步骤 3：连接到 Office 365 订阅</span><span class="sxs-lookup"><span data-stu-id="95ddd-136">Step 3: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="95ddd-137"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="95ddd-137"><a name="step3"> </a></span></span>

<span data-ttu-id="95ddd-138">仅使用 *帐户名和密码*  连接：</span><span class="sxs-lookup"><span data-stu-id="95ddd-138">To connect with just an  *account name and password*  :</span></span>
  
1. <span data-ttu-id="95ddd-139">在"用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块"命令窗口中，运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="95ddd-139">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following commands.</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. <span data-ttu-id="95ddd-140">在"Windows PowerShell 凭据请求"对话框中，键入您的 Office 365工作或学校帐户 用户名和密码，然后单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="95ddd-140">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="95ddd-141">使用 *多重身份验证 (MFA)*  进行连接的具体步骤：</span><span class="sxs-lookup"><span data-stu-id="95ddd-141">To connect with  *multi-factor authentication (MFA)*  :</span></span>
  
1. <span data-ttu-id="95ddd-142">在"用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块"命令窗口中，运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="95ddd-142">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
  ```
  Connect-MsolService
  ```

2. <span data-ttu-id="95ddd-143">在"Azure Active Directory PowerShell"对话框中，键入你的 Office 365工作或学校帐户 用户名和密码，然后单击"登录"。</span><span class="sxs-lookup"><span data-stu-id="95ddd-143">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
3. <span data-ttu-id="95ddd-144">按照"Azure Active Directory PowerShell"对话框中的说明提供其他身份验证信息（如验证码），然后单击"登录"。</span><span class="sxs-lookup"><span data-stu-id="95ddd-144">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="95ddd-145">您如何知道这有效？</span><span class="sxs-lookup"><span data-stu-id="95ddd-145">How do you know this worked?</span></span>
<span data-ttu-id="95ddd-146"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="95ddd-146"><a name="step3"> </a></span></span>

<span data-ttu-id="95ddd-p108">如果未收到任何错误，则说明连接成功。一个快速测试是运行 Office 365 cmdlet（例如 **Get-MsolUser** ），然后查看结果。</span><span class="sxs-lookup"><span data-stu-id="95ddd-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="95ddd-149">如果收到错误，则查看以下要求：</span><span class="sxs-lookup"><span data-stu-id="95ddd-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="95ddd-p109">**常见问题是密码错误** 。重新运行步骤 3，并仔细查看您输入的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="95ddd-p109">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="95ddd-p110">**用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 要求在您的计算机上启用 Microsoft .NET Framework 3.5. _x_ 功能。** 很可能您的计算机已安装了较新的版本（例如 4 或 4.5. _x_），但可以启用或禁用与 .NET Framework 的早期版本的向后兼容性。有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="95ddd-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5. _x_ feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5. _x_), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="95ddd-157">对于 Windows Server 2012 或 Windows Server 2012 R2，请参阅[通过使用添加角色和功能向导中启用.NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="95ddd-157">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="95ddd-158">对于 Windows 8 或 Windows 8.1，请参阅[安装.NET Framework 3.5 版 Windows 8 上 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="95ddd-158">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="95ddd-159">对于 Windows 7 或 Windows Server 2008 R2，请参阅[您无法打开 Azure 活动目录模块用于 Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="95ddd-159">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="95ddd-p111">**您的 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 版本可能已过期。** 若要进行检查，请在 Office 365 PowerShell 或 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="95ddd-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="95ddd-162">如果返回的版本号低于值 1.0.8070.2，请卸载 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，并通过第 1 步中的链接安装最新版本。</span><span class="sxs-lookup"><span data-stu-id="95ddd-162">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="95ddd-163">**如果您收到一个连接错误，请参阅以下主题：**["连接 MsolService： 类型的异常"错误](https://go.microsoft.com/fwlink/p/?LinkId=532377)。</span><span class="sxs-lookup"><span data-stu-id="95ddd-163">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a><span data-ttu-id="95ddd-164">与 Azure Active Directory V2 PowerShell 模块连接</span><span class="sxs-lookup"><span data-stu-id="95ddd-164">Connect with the Azure Active Directory V2 PowerShell module</span></span>
<span data-ttu-id="95ddd-165"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="95ddd-165"><a name="ConnectV2"> </a></span></span>

<span data-ttu-id="95ddd-166">有关 [Azure Active Directory V2 PowerShell 模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)中需要新 cmdlet 的过程，请使用以下步骤安装该模块并连接到 Office 365 订阅：</span><span class="sxs-lookup"><span data-stu-id="95ddd-166">For procedures that require the new cmdlets in the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), use these steps to install the module and connect to your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="95ddd-167">打开提升的 Windows PowerShell 命令提示符（以管理员身份运行 Windows PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="95ddd-167">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="95ddd-168">在"管理员: Windows PowerShell"命令窗口中，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="95ddd-168">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="95ddd-169">如果系统提示从不受信任的存储库安装模块，请键入"Y"，再按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="95ddd-169">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>
    
3. <span data-ttu-id="95ddd-170">新模块安装完成后，使用以下命令连接到 Office 365 订阅：</span><span class="sxs-lookup"><span data-stu-id="95ddd-170">When the installation of the new module is complete, use these commands to connect to your Office 365 subscription:</span></span>
    
  -  <span data-ttu-id="95ddd-171">通过 *帐户名称和密码*  ：</span><span class="sxs-lookup"><span data-stu-id="95ddd-171">With an *account name and password*  :</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 <span data-ttu-id="95ddd-172">在"Windows PowerShell 凭据请求"对话框中，键入 Office 365工作或学校帐户 用户名和密码，再单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="95ddd-172">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
  - <span data-ttu-id="95ddd-173">通过 *多重身份验证 (MFA)*  ：</span><span class="sxs-lookup"><span data-stu-id="95ddd-173">With  *multi-factor authentication (MFA)*  :</span></span>
    
  ```
  Connect-AzureAD
  ```

<span data-ttu-id="95ddd-174">在"Azure Active Directory PowerShell"对话框中，键入你的 Office 365工作或学校帐户 用户名和密码，然后单击"登录"。</span><span class="sxs-lookup"><span data-stu-id="95ddd-174">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="95ddd-175">按照"Azure Active Directory PowerShell"对话框中的说明提供其他身份验证信息（如验证码），然后单击"登录"。</span><span class="sxs-lookup"><span data-stu-id="95ddd-175">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="95ddd-176">连接后，可以对 [Azure Active Directory V2 PowerShell 模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)使用这些新的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="95ddd-176">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="95ddd-177">See also</span><span class="sxs-lookup"><span data-stu-id="95ddd-177">See also</span></span>

#### 

[<span data-ttu-id="95ddd-178">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="95ddd-178">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="95ddd-179">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="95ddd-179">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="95ddd-180">在单个 Windows PowerShell 窗口中连接所有 Office 365 服务</span><span class="sxs-lookup"><span data-stu-id="95ddd-180">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[<span data-ttu-id="95ddd-181">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="95ddd-181">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[<span data-ttu-id="95ddd-182">连接 MsolService</span><span class="sxs-lookup"><span data-stu-id="95ddd-182">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

