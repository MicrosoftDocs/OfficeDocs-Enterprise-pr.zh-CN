---
title: 连接到 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
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
description: 摘要： 连接到 Office 365 组织使用 Office 365 PowerShell 从命令行执行 admin center 任务。
ms.openlocfilehash: 96406fbc23adadbf77a3cd02f8c167081f908977
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720398"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="ea279-103">连接到 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea279-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="ea279-104">**摘要：** 连接到 Office 365 组织使用 Office 365 PowerShell 从命令行执行管理任务。</span><span class="sxs-lookup"><span data-stu-id="ea279-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="ea279-p101">借助 Office 365 PowerShell，可以通过命令行管理 Office 365 设置。连接到 Office 365 PowerShell 是一个非常简单的三步流程：安装必需软件，运行必需软件，再连接到 Office 365 组织。</span><span class="sxs-lookup"><span data-stu-id="ea279-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

  
> [!TIP]
> <span data-ttu-id="ea279-p102">**刚开始接触 PowerShell？** 请观看领英学习提供的 [PowerShell 概述](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)视频。</span><span class="sxs-lookup"><span data-stu-id="ea279-p102">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="ea279-109">在开始之前，需要知道什么？</span><span class="sxs-lookup"><span data-stu-id="ea279-109">What do you need to know before you begin?</span></span>

- <span data-ttu-id="ea279-110">估计完成时间：5 分钟</span><span class="sxs-lookup"><span data-stu-id="ea279-110">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="ea279-111">可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="ea279-111">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="ea279-112">Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="ea279-112">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="ea279-113">Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="ea279-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="ea279-p103">请使用 64 位版 Windows。2014 年 10 月，用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块已不再支持 32 位版。</span><span class="sxs-lookup"><span data-stu-id="ea279-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="ea279-p104">这些过程适用于 Office 365 管理员角色的成员的用户。有关详细信息，请参阅[有关 Office 365 管理员角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。</span><span class="sxs-lookup"><span data-stu-id="ea279-p104">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ea279-118">使用图模块 Azure Active Directory PowerShell 连接</span><span class="sxs-lookup"><span data-stu-id="ea279-118">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ea279-119">[图形 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)模块中的命令其 cmdlet 名称中具有**AzureAD** 。</span><span class="sxs-lookup"><span data-stu-id="ea279-119">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="ea279-120">有关图模块需要在 Azure Active Directory PowerShell 中的新 cmdlet 的过程，使用以下步骤安装模块并连接到 Office 365 订阅。</span><span class="sxs-lookup"><span data-stu-id="ea279-120">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="ea279-121">有关不同版本的 Microsoft Windows 支持的信息，请参阅[Azure Active Directory PowerShell for 图模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)。</span><span class="sxs-lookup"><span data-stu-id="ea279-121">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="ea279-122">步骤 1：安装所需软件</span><span class="sxs-lookup"><span data-stu-id="ea279-122">Step 1: Install required software</span></span>

<span data-ttu-id="ea279-p105">这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。</span><span class="sxs-lookup"><span data-stu-id="ea279-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="ea279-125">打开提升的 Windows PowerShell 命令提示符（以管理员身份运行 Windows PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="ea279-125">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="ea279-126">在"管理员: Windows PowerShell"命令窗口中，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ea279-126">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="ea279-127">如果系统提示从不受信任的存储库安装模块，请键入 **Y**，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="ea279-127">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="ea279-128">步骤 2： 连接到 Office 365 订阅 Azure AD</span><span class="sxs-lookup"><span data-stu-id="ea279-128">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="ea279-129">连接到 Azure AD 的 Office 365 订阅与帐户名和密码或*多重身份验证 (MFA)* 从 Windows PowerShell 命令提示符 （它没有要提升的权限） 运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ea279-129">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)* run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-AzureAD
```

<span data-ttu-id="ea279-130">**登录到您的帐户**对话框中，键入您的 Office 365 工作或学校帐户的用户名和密码，，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="ea279-130">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="ea279-131">如果您使用 MFA，请按照其他对话框中的说明提供身份验证中的详细信息，如验证代码。</span><span class="sxs-lookup"><span data-stu-id="ea279-131">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>
    
<span data-ttu-id="ea279-132">连接后，可以为[Azure Active Directory PowerShell for 图模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)使用的新 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ea279-132">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ea279-133">与用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块连接</span><span class="sxs-lookup"><span data-stu-id="ea279-133">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ea279-134">用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块中的命令在其 cmdlet 名称中具有 **Msol**。</span><span class="sxs-lookup"><span data-stu-id="ea279-134">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="ea279-135">步骤 1：安装所需软件</span><span class="sxs-lookup"><span data-stu-id="ea279-135">Step 1: Install required software</span></span>

<span data-ttu-id="ea279-p106">这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。</span><span class="sxs-lookup"><span data-stu-id="ea279-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="ea279-138">安装 64 位版 Microsoft Online Services 登录助手：[适用于 IT 专业人员 RTW 的 Microsoft Online Services 登录助手](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="ea279-138">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="ea279-139">安装用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，具体步骤如下：</span><span class="sxs-lookup"><span data-stu-id="ea279-139">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="ea279-140">打开提升的 Windows PowerShell 命令提示符（以管理员身份运行 Windows PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="ea279-140">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="ea279-141">运行 **Install-Module MSOnline** 命令。</span><span class="sxs-lookup"><span data-stu-id="ea279-141">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="ea279-142">如果系统提示安装 NuGet 提供程序，请键入 **Y**，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="ea279-142">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="ea279-143">如果系统提示从 PSGallery 安装模块，请键入 **Y**，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="ea279-143">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="ea279-144">步骤 2： 连接到 Office 365 订阅 Azure AD</span><span class="sxs-lookup"><span data-stu-id="ea279-144">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="ea279-145">要连接到您的帐户名和密码或具有*多因素身份验证 (MFA)* 的 Office 365 订阅 Azure AD，请从 Windows PowerShell 命令提示符 （它没有要提升的权限） 运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ea279-145">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-MsolService
```

<span data-ttu-id="ea279-146">**登录到您的帐户**对话框中，键入您的 Office 365 工作或学校帐户的用户名和密码，，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="ea279-146">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="ea279-147">如果您使用 MFA，请按照其他对话框中的说明提供身份验证中的详细信息，如验证代码。</span><span class="sxs-lookup"><span data-stu-id="ea279-147">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="ea279-148">您如何知道操作成功？</span><span class="sxs-lookup"><span data-stu-id="ea279-148">How do you know this worked?</span></span>

<span data-ttu-id="ea279-p107">如果未收到任何错误，则说明连接成功。一个快速测试是运行 Office 365 cmdlet（例如 **Get-MsolUser** ），然后查看结果。</span><span class="sxs-lookup"><span data-stu-id="ea279-p107">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="ea279-151">如果收到错误，则查看以下要求：</span><span class="sxs-lookup"><span data-stu-id="ea279-151">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="ea279-p108">**常见问题是密码错误** 。重新运行步骤 3，并仔细查看您输入的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="ea279-p108">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="ea279-p109">* *Microsoft Azure Active Directory 的 Windows PowerShell 模块需要 Microsoft.NET Framework 3.5。* 对您计算机 * * 启用 x * 功能。很可能计算机具有安装新版本 (例如，4 或 4.5。* x *），但向后启用或禁用与旧版本的.NET framework 兼容。有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="ea279-p109">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="ea279-157">对于 Windows Server 2012 或 Windows Server 2012 R2，请参阅[使用“添加角色和功能”向导启用 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span><span class="sxs-lookup"><span data-stu-id="ea279-157">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="ea279-158">对于 Windows 8 或 Windows 8.1，请参阅[在 Windows 8 或 8.1 上安装 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span><span class="sxs-lookup"><span data-stu-id="ea279-158">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="ea279-159">对于 Windows 7 或 Windows Server 2008 R2，请参阅[不能打开用于 Windows PowerShell 的 Azure Active Directory 模块](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span><span class="sxs-lookup"><span data-stu-id="ea279-159">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="ea279-160">有关 Windows 10、 Windows 8.1 和 Windows 8，请参阅[安装.NET Framework 3.5 Windows 10、 Windows 8.1 和 Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span><span class="sxs-lookup"><span data-stu-id="ea279-160">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="ea279-p110">**您的 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 版本可能已过期。** 若要进行检查，请在 Office 365 PowerShell 或 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ea279-p110">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="ea279-163">如果返回的版本号低于值 1.0.8070.2，请卸载 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，并通过第 1 步中的链接安装最新版本。</span><span class="sxs-lookup"><span data-stu-id="ea279-163">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="ea279-164">**如果看到连接错误，请参阅以下主题：**[“Connect-MsolService：抛出类型异常”错误](https://go.microsoft.com/fwlink/p/?LinkId=532377)。</span><span class="sxs-lookup"><span data-stu-id="ea279-164">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="ea279-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea279-165">See also</span></span>

- [<span data-ttu-id="ea279-166">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="ea279-166">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="ea279-167">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="ea279-167">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="ea279-168">在单个 Windows PowerShell 窗口中连接所有 Office 365 服务</span><span class="sxs-lookup"><span data-stu-id="ea279-168">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="ea279-169">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="ea279-169">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="ea279-170">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="ea279-170">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

