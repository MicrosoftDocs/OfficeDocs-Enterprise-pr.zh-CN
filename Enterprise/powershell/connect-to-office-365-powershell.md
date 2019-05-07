---
title: 连接到 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: '摘要: 使用 Office 365 PowerShell 连接到 Office 365 组织以通过命令行执行管理中心任务。'
ms.openlocfilehash: 4c70f067558773ce7e2a6e27bab78f5c64965872
ms.sourcegitcommit: 0516a15c72f4bc8423a1d8112fd4d3e5f69896c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2019
ms.locfileid: "33639773"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="87018-103">连接到 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="87018-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="87018-104">**摘要:** 使用 Office 365 PowerShell 连接到 Office 365 组织, 从命令行执行管理任务。</span><span class="sxs-lookup"><span data-stu-id="87018-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="87018-105">Office 365 PowerShell 允许您从命令行管理 Office 365 设置。</span><span class="sxs-lookup"><span data-stu-id="87018-105">Office 365 PowerShell lets you manage your Office 365 settings from the command line.</span></span> <span data-ttu-id="87018-106">连接到 Office 365 PowerShell 是一个简单的过程, 您可以在其中安装必需的软件, 然后连接到 Office 365 组织。</span><span class="sxs-lookup"><span data-stu-id="87018-106">Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="87018-107">有两个版本的 PowerShell 模块可用于连接到 Office 365 并管理用户帐户、组和许可证:</span><span class="sxs-lookup"><span data-stu-id="87018-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="87018-108">适用于 Graph 的 Azure Active Directory PowerShell (cmdlet 在其名称中包含**AzureAD** )</span><span class="sxs-lookup"><span data-stu-id="87018-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="87018-109">适用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 (cmdlet 在其名称中包含**MSol** )</span><span class="sxs-lookup"><span data-stu-id="87018-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="87018-110">从本文的日期起, Azure Active Directory PowerShell for Graph 模块未完全替换 Microsoft Azure Active Directory Module for Windows PowerShell 模块的 cmdlet 中的功能, 用于用户、组和许可证管理.</span><span class="sxs-lookup"><span data-stu-id="87018-110">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration.</span></span> <span data-ttu-id="87018-111">在许多情况下, 您需要使用这两个版本。</span><span class="sxs-lookup"><span data-stu-id="87018-111">In many cases, you need to use both versions.</span></span> <span data-ttu-id="87018-112">您可以安全地在同一台计算机上安装这两个版本。</span><span class="sxs-lookup"><span data-stu-id="87018-112">You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="87018-p103">**刚开始接触 PowerShell？** 请观看领英学习提供的 [PowerShell 概述](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)视频。</span><span class="sxs-lookup"><span data-stu-id="87018-p103">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="87018-115">开始前，有必要了解什么？</span><span class="sxs-lookup"><span data-stu-id="87018-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="87018-116">估计完成时间：5 分钟</span><span class="sxs-lookup"><span data-stu-id="87018-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="87018-117">可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="87018-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="87018-118">Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="87018-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="87018-119">Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="87018-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="87018-p104">请使用 64 位版 Windows。2014 年 10 月，用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块已不再支持 32 位版。</span><span class="sxs-lookup"><span data-stu-id="87018-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="87018-122">这些过程适用于作为 Office 365 管理员角色的成员的用户。</span><span class="sxs-lookup"><span data-stu-id="87018-122">These procedures are intended for users who are members of an Office 365 admin role.</span></span> <span data-ttu-id="87018-123">有关详细信息，请参阅[关于 Office 365 管理员角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。</span><span class="sxs-lookup"><span data-stu-id="87018-123">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="87018-124">与 Azure Active Directory PowerShell for Graph 模块进行连接</span><span class="sxs-lookup"><span data-stu-id="87018-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="87018-125">[用于 Graph 模块的 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)中的命令在其 cmdlet 名称中有**AzureAD** 。</span><span class="sxs-lookup"><span data-stu-id="87018-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="87018-126">对于需要 Azure Active Directory PowerShell for Graph 模块中的新 cmdlet 的过程, 请按照以下步骤操作, 以安装该模块并连接到 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="87018-126">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="87018-127">有关 Microsoft Windows 的不同版本支持的信息, 请参阅[Azure Active Directory PowerShell For Graph 模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)。</span><span class="sxs-lookup"><span data-stu-id="87018-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="87018-128">步骤 1：安装所需软件</span><span class="sxs-lookup"><span data-stu-id="87018-128">Step 1: Install required software</span></span>

<span data-ttu-id="87018-p106">这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。</span><span class="sxs-lookup"><span data-stu-id="87018-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="87018-131">打开提升的 Windows PowerShell 命令提示符（以管理员身份运行 Windows PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="87018-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="87018-132">在“管理员: Windows PowerShell”\*\*\*\* 命令窗口中，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="87018-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="87018-133">如果系统提示从不受信任的存储库安装模块，请键入“Y”\*\*\*\*，再按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="87018-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="87018-134">步骤 2: 连接到 Office 365 订阅的 Azure AD</span><span class="sxs-lookup"><span data-stu-id="87018-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="87018-135">若要使用帐户名和密码或*多重身份验证 (MFA)* 连接到 Office 365 订阅的 Azure AD, 请从 Windows PowerShell 命令提示符运行以下命令之一 (无需提升)。</span><span class="sxs-lookup"><span data-stu-id="87018-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="87018-136">**Office 365 云**</span><span class="sxs-lookup"><span data-stu-id="87018-136">**Office 365 cloud**</span></span> | <span data-ttu-id="87018-137">**Command**</span><span class="sxs-lookup"><span data-stu-id="87018-137">**Command**</span></span> |
| <span data-ttu-id="87018-138">Office 365 全球版本 (+ GCC)</span><span class="sxs-lookup"><span data-stu-id="87018-138">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="87018-139">由 21 Vianet 运营的 Office 365</span><span class="sxs-lookup"><span data-stu-id="87018-139">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="87018-140">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="87018-140">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="87018-141">Office 365 美国政府 DoD 和 Office 365 美国政府版 (GCC) 高</span><span class="sxs-lookup"><span data-stu-id="87018-141">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="87018-142">在 "**登录帐户**" 对话框中, 键入 Office 365 的工作或学校帐户用户名和密码, 然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="87018-142">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="87018-143">如果使用的是 MFA, 请按照其他对话框中的说明操作, 以提供更多的身份验证信息, 如验证代码。</span><span class="sxs-lookup"><span data-stu-id="87018-143">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="87018-144">连接后, 可以对[Azure Active Directory PowerShell For Graph 模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)使用新 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="87018-144">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="87018-145">与用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块连接</span><span class="sxs-lookup"><span data-stu-id="87018-145">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="87018-146">用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块中的命令在其 cmdlet 名称中具有 **Msol**。</span><span class="sxs-lookup"><span data-stu-id="87018-146">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="87018-147">步骤 1：安装所需软件</span><span class="sxs-lookup"><span data-stu-id="87018-147">Step 1: Install required software</span></span>

<span data-ttu-id="87018-p107">这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。</span><span class="sxs-lookup"><span data-stu-id="87018-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="87018-150">安装 64 位版 Microsoft Online Services 登录助手：[适用于 IT 专业人员 RTW 的 Microsoft Online Services 登录助手](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="87018-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="87018-151">安装用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，具体步骤如下：</span><span class="sxs-lookup"><span data-stu-id="87018-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="87018-152">打开提升的 Windows PowerShell 命令提示符（以管理员身份运行 Windows PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="87018-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="87018-153">运行 **Install-Module MSOnline** 命令。</span><span class="sxs-lookup"><span data-stu-id="87018-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="87018-154">如果系统提示安装 NuGet 提供程序，请键入 **Y**，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="87018-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="87018-155">如果系统提示从 PSGallery 安装模块，请键入 **Y**，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="87018-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="87018-156">步骤 2: 连接到 Office 365 订阅的 Azure AD</span><span class="sxs-lookup"><span data-stu-id="87018-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="87018-157">若要使用帐户名和密码或*多重身份验证 (MFA)* 连接到 Office 365 订阅的 Azure AD, 请从 Windows PowerShell 命令提示符运行以下命令之一 (无需提升)。</span><span class="sxs-lookup"><span data-stu-id="87018-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="87018-158">**Office 365 云**</span><span class="sxs-lookup"><span data-stu-id="87018-158">**Office 365 cloud**</span></span> | <span data-ttu-id="87018-159">**Command**</span><span class="sxs-lookup"><span data-stu-id="87018-159">**Command**</span></span> |
| <span data-ttu-id="87018-160">Office 365 全球版本 (+ GCC)</span><span class="sxs-lookup"><span data-stu-id="87018-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="87018-161">由 21 Vianet 运营的 Office 365</span><span class="sxs-lookup"><span data-stu-id="87018-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="87018-162">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="87018-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="87018-163">Office 365 美国政府 DoD 和 Office 365 美国政府版 (GCC) 高</span><span class="sxs-lookup"><span data-stu-id="87018-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="87018-164">在 "**登录帐户**" 对话框中, 键入 Office 365 的工作或学校帐户用户名和密码, 然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="87018-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="87018-165">如果使用的是 MFA, 请按照其他对话框中的说明操作, 以提供更多的身份验证信息, 如验证代码。</span><span class="sxs-lookup"><span data-stu-id="87018-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="87018-166">如何知道操作成功？</span><span class="sxs-lookup"><span data-stu-id="87018-166">How do you know this worked?</span></span>

<span data-ttu-id="87018-p108">如果未收到任何错误，则说明连接成功。一个快速测试是运行 Office 365 cmdlet（例如 **Get-MsolUser** ），然后查看结果。</span><span class="sxs-lookup"><span data-stu-id="87018-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="87018-169">如果收到错误，则查看以下要求：</span><span class="sxs-lookup"><span data-stu-id="87018-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="87018-170">**一个常见的问题是不正确的密码**。</span><span class="sxs-lookup"><span data-stu-id="87018-170">**A common problem is an incorrect password**.</span></span> <span data-ttu-id="87018-171">再次运行步骤2。</span><span class="sxs-lookup"><span data-stu-id="87018-171">Run Step 2 again.</span></span> <span data-ttu-id="87018-172">, 请密切注意你输入的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="87018-172">and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="87018-173">\**适用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块要求安装 Microsoft .net Framework 3.5。* x \* 功能在计算机上启用 \* *。您的计算机可能安装了更新的版本 (例如, 4 或4.5。* x \*), 但可以启用或禁用与 .NET Framework 早期版本的向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="87018-173">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled.</span></span> <span data-ttu-id="87018-174">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="87018-174">For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="87018-175">对于 Windows Server 2012 或 Windows Server 2012 R2，请参阅[使用“添加角色和功能”向导启用 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="87018-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="87018-176">对于 Windows 7 或 Windows Server 2008 R2，请参阅[不能打开用于 Windows PowerShell 的 Azure Active Directory 模块](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="87018-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="87018-177">对于 Windows 10、Windows 8.1 和 Windows 8, 请参阅[在 windows 10、windows 8.1 和 windows 8 上安装 .Net Framework 3.5](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="87018-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="87018-p111">**您的 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 版本可能已过期。** 若要进行检查，请在 Office 365 PowerShell 或 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="87018-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="87018-180">如果返回的版本号低于值 1.0.8070.2，请卸载 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，并通过第 1 步中的链接安装最新版本。</span><span class="sxs-lookup"><span data-stu-id="87018-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="87018-181">**如果看到连接错误，请参阅以下主题：**[“Connect-MsolService：抛出类型异常”错误](https://go.microsoft.com/fwlink/p/?LinkId=532377)。</span><span class="sxs-lookup"><span data-stu-id="87018-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="87018-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87018-182">See also</span></span>

- [<span data-ttu-id="87018-183">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="87018-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="87018-184">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="87018-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="87018-185">在单个 Windows PowerShell 窗口中连接所有 Office 365 服务</span><span class="sxs-lookup"><span data-stu-id="87018-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="87018-186">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="87018-186">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="87018-187">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="87018-187">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

