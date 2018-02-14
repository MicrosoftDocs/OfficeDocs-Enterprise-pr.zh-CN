---
title: "在单个 Windows PowerShell 窗口中连接所有 Office 365 服务"
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
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: "摘要： 将 Windows PowerShell 连接到一个 Windows PowerShell 窗口中的所有 Office 365 提供服务。"
ms.openlocfilehash: d11487ae1c95cb0d36221e7ce572ed55052d98eb
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="d3564-103">在单个 Windows PowerShell 窗口中连接所有 Office 365 服务</span><span class="sxs-lookup"><span data-stu-id="d3564-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="d3564-104">**摘要：**而不是管理不同的 Office 365 服务单独 PowerShell 控制台窗口中，可以连接到所有的 Office 365 提供服务并从单个控制台窗口中对它们进行管理。</span><span class="sxs-lookup"><span data-stu-id="d3564-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="d3564-p101">当使用 PowerShell Office 365 管理时，很可能有最多五个不同的 Windows PowerShell 会话打开对应于 Office 365 管理中心、 SharePoint Online、 Exchange Online，Skype 的在线业务和&amp;符合性中心。在单独的 Windows PowerShell 会话中的五种不同的连接方法，与您的桌面可以如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3564-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![五个同时运行的 Windows PowerShell 控制台](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="d3564-p102">这不是最适合于管理 Office 365，因为不能交换跨服务管理这些五个窗口间的数据。本主题介绍如何使用与管理 Office 365、 为业务联机状态，Exchange Online，SharePoint Online，Skype 和安全的 Windows PowerShell 的单个实例&amp;法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="d3564-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="d3564-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="d3564-110">Before you begin</span></span>
<span data-ttu-id="d3564-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="d3564-111"></span></span>

<span data-ttu-id="d3564-112">您可以从 Windows PowerShell 的单个实例中管理所有 Office 365 的之前，请考虑以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="d3564-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="d3564-p103">Office 365 的工作或学校对使用这些过程需要 Office 365 管理角色的成员的帐户。有关详细信息，请参阅[有关 Office 365 管理角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。此 Office 365 PowerShell，不一定能为所有其他 Office 365 提供服务的要求。</span><span class="sxs-lookup"><span data-stu-id="d3564-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="d3564-116">您可以使用以下 64 位版本的 Windows：</span><span class="sxs-lookup"><span data-stu-id="d3564-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="d3564-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="d3564-117">Windows 10</span></span>
    
  - <span data-ttu-id="d3564-118">Windows 8.1 或 Windows 8</span><span class="sxs-lookup"><span data-stu-id="d3564-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="d3564-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="d3564-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="d3564-120">Windows Server 2012 R2 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d3564-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="d3564-121">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="d3564-121">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="d3564-122">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="d3564-122">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="d3564-p104">您需要安装 Microsoft.net 4.5。_x_ ，然后是 Windows 管理框架 3.0 或 Windows 管理框架 4.0。有关详细信息，请参阅[安装.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[Windows 管理框架 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[Windows 管理框架 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。</span><span class="sxs-lookup"><span data-stu-id="d3564-p104">You need to install the Microsoft .NET Framework 4.5. _x_ and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="d3564-126">您需要使用 64 位版本的 Windows 由于 Skype 的要求在线业务模块和 Office 365 模块之一。</span><span class="sxs-lookup"><span data-stu-id="d3564-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="d3564-127">您需要安装所需的 Office 365、 SharePoint Online 和 Skype 的在线业务的模块：</span><span class="sxs-lookup"><span data-stu-id="d3564-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
  - [<span data-ttu-id="d3564-128">Microsoft 在线服务登录助理为 IT 专业人士一项的</span><span class="sxs-lookup"><span data-stu-id="d3564-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [<span data-ttu-id="d3564-129">Windows Azure 活动目录模块用于 Windows PowerShell （64-位版本）</span><span class="sxs-lookup"><span data-stu-id="d3564-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version)</span></span>](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [<span data-ttu-id="d3564-130">SharePoint 在线管理外壳程序</span><span class="sxs-lookup"><span data-stu-id="d3564-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [<span data-ttu-id="d3564-131">Skype 的在线业务 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="d3564-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="d3564-p105">Windows PowerShell 需要配置运行 Skype 在线业务、 在线交换和安全签名的脚本&amp;法规遵从性中心。若要执行此操作，在提升的权限的 Windows PowerShell 会话中运行以下命令 （您选择**以管理员身份运行**，打开 Windows PowerShell 窗口）。</span><span class="sxs-lookup"><span data-stu-id="d3564-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="d3564-134">简版（说明不含解释）</span><span class="sxs-lookup"><span data-stu-id="d3564-134">The short version (instructions without explanations)</span></span>
<span data-ttu-id="d3564-135"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="d3564-135"></span></span>

<span data-ttu-id="d3564-p106">此部分介绍的连接步骤不作深入解释。如果你有疑问或想了解更多信息，你可以阅读本主题的其余部分。此处的步骤号匹配主题其余部分中按步骤编号的部分：</span><span class="sxs-lookup"><span data-stu-id="d3564-p106">This section presents the connection steps without in-depth explanations. If you have questions or want more information, you can read rest of the topic. The step numbers here match the step-numbered sections in the rest of the topic:</span></span>
  
1. <span data-ttu-id="d3564-139">以管理员身份 （使用**以管理员身份运行**） 打开 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d3564-139">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="d3564-140">运行此命令，并输入您的 Office 365 提供工作或学校帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="d3564-140">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="d3564-141">运行以下命令以连接到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="d3564-141">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="d3564-p107">运行以下命令以连接到 SharePoint Online。更换_\<domainhost >_与实际值为您的域。例如，对于`litwareinc.onmicrosoft.com`， _ \<domainhost >_值是`litwareinc`。</span><span class="sxs-lookup"><span data-stu-id="d3564-p107">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="d3564-p108">运行以下命令以连接到 Skype 的在线业务。有关增加警告`WSMan NetworkDelayms`的值应在第一次连接，可以忽略。</span><span class="sxs-lookup"><span data-stu-id="d3564-p108">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="d3564-147">运行以下命令以连接到 Exchange 联机。</span><span class="sxs-lookup"><span data-stu-id="d3564-147">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="d3564-148">运行以下命令以对安全连接&amp;法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="d3564-148">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="d3564-p109">"抄送"中的文本前缀添加到*所有*安全&amp;法规遵从性中心 cmdlet 名称以便您可以运行的 cmdlet，存在于 Exchange 联机和安全&amp;同一 Windows PowerShell 会话中的法规遵从性中心。例如， **Get RoleGroup**将成为安全**获取 ccRoleGroup** &amp;法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="d3564-p109">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="d3564-p110">下面是在一个块的所有命令。指定您的域主机的名称，然后一次运行所有这些。</span><span class="sxs-lookup"><span data-stu-id="d3564-p110">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```

<span data-ttu-id="d3564-153">准备就绪以关闭 Windows PowerShell 窗口后，运行以下命令来删除联机业务、 Exchange Online，SharePoint Online，和安全到 Skype 的活动会话&amp;法规遵从性中心：</span><span class="sxs-lookup"><span data-stu-id="d3564-153">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="d3564-154">长版（说明附有详细解释）</span><span class="sxs-lookup"><span data-stu-id="d3564-154">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="d3564-155"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="d3564-155"></span></span>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a><span data-ttu-id="d3564-156">步骤 1：以管理员身份打开 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3564-156">Step 1: Open Windows PowerShell as an administrator</span></span>
<span data-ttu-id="d3564-157"><a name="Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="d3564-157"></span></span>

<span data-ttu-id="d3564-158">如果您运行的 Windows 10，Windows 8、 Windows 8.1、 Windows 服务器 2016年、 Windows Server 2012 R2 或 Windows Server 2012 R2，执行此操作：</span><span class="sxs-lookup"><span data-stu-id="d3564-158">If you're running Windows 10, Windows 8, Windows 8.1, Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012 R2, do this:</span></span>
  
1. <span data-ttu-id="d3564-159">使用下列任一方法来查找**Windows PowerShell**的快捷方式：</span><span class="sxs-lookup"><span data-stu-id="d3564-159">Use any of these methods to find the shortcut for **Windows PowerShell**:</span></span>
    
  - <span data-ttu-id="d3564-160">在启动屏幕上，单击空白区域，然后键入 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d3564-160">On the Start screen, click an empty area, and type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="d3564-p111">在桌面或开始屏幕上，按下 Windows 键 + Q。在搜索超级按钮，键入 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d3564-p111">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Windows PowerShell.</span></span>
    
  - <span data-ttu-id="d3564-p112">在桌面或开始屏幕上，将光标移动到右上角或刷从右向左，从屏幕来显示魅力的右边缘。选择搜索超级按钮，并输入 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d3564-p112">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and enter Windows PowerShell.</span></span>
    
2. <span data-ttu-id="d3564-165">在结果中，用鼠标右键单击**Windows PowerShell**，并选择**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="d3564-165">In the results, right-click **Windows PowerShell**, and select **Run as administrator**.</span></span>
    
3. <span data-ttu-id="d3564-166">如果出现**用户帐户控制**对话框中，选择**是**以确认您想要在管理员凭据下运行 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d3564-166">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="d3564-167">如果运行的 Windows 7 SP1 （或 Windows Server 2008 R2 SP1），请执行此操作：</span><span class="sxs-lookup"><span data-stu-id="d3564-167">If you're running Windows 7 SP1 (or Windows Server 2008 R2 SP1), do this:</span></span>
  
1. <span data-ttu-id="d3564-p113">在**开始**菜单中，选择**所有程序** > **附件** > **Windows PowerShell**。**Windows PowerShell**，用鼠标右键单击，然后选择**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="d3564-p113">On the **Start** menu, select **All Programs** > **Accessories** > **Windows PowerShell**. Right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>
    
2. <span data-ttu-id="d3564-170">如果出现**用户帐户控制**对话框中，选择**是**以确认您想要在管理员凭据下运行 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d3564-170">If the **User Account Control** dialog box appears, select **Yes** to verify that you want to run Windows PowerShell under administrator credentials.</span></span>
    
<span data-ttu-id="d3564-p114">您必须以管理员身份运行 Windows PowerShell。如果不这样做，您将收到错误消息与此类似，当您尝试导入所需的模块之一。</span><span class="sxs-lookup"><span data-stu-id="d3564-p114">You must run Windows PowerShell as an administrator. If you don't, you're going to get an error message similar to this when you try to import one of the required modules.</span></span>
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

<span data-ttu-id="d3564-p115">要解决此问题的唯一方法是关闭 Windows PowerShell 并以管理员身份重新启动它。这里是告诉是否您以管理员身份运行 Windows PowerShell 的快速简便方法： 提示是`PS C:\Windows\System32>`， `PS C:\Users\YourUserName>`。</span><span class="sxs-lookup"><span data-stu-id="d3564-p115">The only way to remedy the situation is to close Windows PowerShell and restart it as an administrator. Here's a quick and easy way to tell if you're running Windows PowerShell as an administrator: the prompt is  `PS C:\Windows\System32>`, not  `PS C:\Users\YourUserName>`.</span></span>

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a><span data-ttu-id="d3564-175">步骤 2：创建 Windows PowerShell 凭据对象</span><span class="sxs-lookup"><span data-stu-id="d3564-175">Step 2: Create a Windows PowerShell credentials object</span></span>
<span data-ttu-id="d3564-176"><a name="Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="d3564-176"></span></span>

<span data-ttu-id="d3564-p116">该凭据对象提供一种加密的方法将您的用户名和密码传递给 Windows PowerShell。若要创建一个凭据，请在 Windows PowerShell 运行下面的命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-p116">The credentials object provides an encrypted way to pass your user name and password to Windows PowerShell. To create a credentials object, run the following command in Windows PowerShell.</span></span>
  
```
$credential = Get-Credential
```

> [!NOTE]
>  <span data-ttu-id="d3564-p117">`$credential`是将存储的凭据的对象的变量。您无需命名该变量`$credential`，但这样做可以在容易记住哪个变量包含凭据的对象。（，这很重要，因为我们将多次重用此变量）。也方便为您跟随我们的示例中，因为这篇文章将会始终使用`$credential`来表示凭据对象。</span><span class="sxs-lookup"><span data-stu-id="d3564-p117">`$credential` is a variable that will store the credentials object. You don't have to name the variable `$credential`, but doing so makes it easier to remember which variable contains the credentials object. (And that's important, because we'll reuse this variable several times.) That will also make it easier for you to follow our examples, because this article will always use  `$credential` to represent the credentials object.</span></span>
  
<span data-ttu-id="d3564-182">Windows PowerShell 将显示一个对话框，如下所示。</span><span class="sxs-lookup"><span data-stu-id="d3564-182">Windows PowerShell will then display a dialog box that looks like this.</span></span>
  
![空白“凭据”请求对话框。](images/o365_powershell_empty_credentials_box.png)
  
<span data-ttu-id="d3564-184">键入您的工作或学校帐户的**用户名**框中，使用用户名格式_username@domainname_ (例如，kenmyer@litwareinc.onmicrosoft.com);键入您的密码，在**密码**框中;然后单击**确定**:</span><span class="sxs-lookup"><span data-stu-id="d3564-184">Type your work or school account user name in the **User name** box, using the format _username@domainname_ (for example, kenmyer@litwareinc.onmicrosoft.com); type your password in the **Password** box; and then click **OK**:</span></span>
  
![已完成“凭据”请求对话框。](images/o365_powershell_completed_credentials_box.png)
  
<span data-ttu-id="d3564-p118">请注意，通常的情况一样，您不会看到确认已创建凭据对象的任何排序。（Windows PowerShell 通常告诉您当事情出错但不总是告诉您当事情转右。如果您想要验证已创建凭据的对象，在 Windows PowerShell 中键入以下内容，然后按 enter 键。</span><span class="sxs-lookup"><span data-stu-id="d3564-p118">Note that, as is often the case, you won't see any sort of confirmation that the credentials object was created. (Windows PowerShell typically tells you when things go wrong but doesn't always tell you when things go right.) If you want to verify that the credentials object was created, type the following in Windows PowerShell and then press Enter.</span></span>
  
```
$credential
```

<span data-ttu-id="d3564-188">然后，您应该会在屏幕上看到以下内容。</span><span class="sxs-lookup"><span data-stu-id="d3564-188">You should then see something similar to this on the screen.</span></span>
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

<span data-ttu-id="d3564-p119">一件事需要记住这里是[获取凭据](https://go.microsoft.com/fwlink/p/?LinkId=389618)cmdlet 仅创建凭据对象; 对象。它不验证您的身份或否则验证用户名和密码正确。例如，假设您输入正确的用户名为 kenmyer@litwareinc.onmicrosoft.com。如果这样做，**获取凭据**将创建凭据对象使用该用户的名称，并不会检查以查看是否该实际上是有效的用户名称。您不会知道直到实际使用该对象来尝试连接到 Office 365 提供服务是否已创建一个真正有效的凭据。</span><span class="sxs-lookup"><span data-stu-id="d3564-p119">One thing to keep in mind here is that the [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618) cmdlet only creates the credentials object; it does not authenticate you or otherwise verify that the user name and password you supplied are correct. For example, suppose you mistyped the user name as kenmyer@litwareinc.onmicrosoft.com. If you do that, **Get-Credential** will create a credentials object using that user name, and without checking to see if that is actually a valid user name. You won't know whether you have created a truly valid credentials object until you actually use that object to try to connect to the Office 365 services.</span></span>
  
### <a name="step-3-connect-to-office-365"></a><span data-ttu-id="d3564-192">步骤 3：连接到 Office 365</span><span class="sxs-lookup"><span data-stu-id="d3564-192">Step 3: Connect to Office 365</span></span>
<span data-ttu-id="d3564-193"><a name="Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="d3564-193"></span></span>

<span data-ttu-id="d3564-194">我们首先连接到 Office 365 本身。</span><span class="sxs-lookup"><span data-stu-id="d3564-194">We'll start by connecting to Office 365 itself.</span></span> 
  
<span data-ttu-id="d3564-p120">我们需要做的第一件事是导入 Office 365 模块 (Microsoft Azure 活动目录模块用于 Windows PowerShell)。为此，请在 Windows PowerShell 运行此命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-p120">The first thing we need to do here is import the Office 365 module (the Microsoft Azure Active Directory Module for Windows PowerShell). To do that, run this command in Windows PowerShell.</span></span>
  
```
Import-Module MsOnline
```

<span data-ttu-id="d3564-197">如果你想验证是否已导入该模块，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-197">If you want to verify that the module was imported, run this command.</span></span>
  
```
Get-Module
```

<span data-ttu-id="d3564-198">在您看到的内容应如下所示，此命令返回的模块列表中的某处： `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`。</span><span class="sxs-lookup"><span data-stu-id="d3564-198">Somewhere in the list of modules that are returned by this command you should see something that looks like this:  `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`.</span></span>
  
<span data-ttu-id="d3564-199">如果您看到`MSOnline`列出，这意味着一切按计划。</span><span class="sxs-lookup"><span data-stu-id="d3564-199">If you see  `MSOnline` listed, that means that everything went according to plan.</span></span>
  
<span data-ttu-id="d3564-200">与创建凭据的对象 (请参阅[步骤 2： 创建一个 Windows PowerShell 凭据](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) 与`MsOnline`加载的模块，我们现在可以连接到 Office 365 通过[连接 MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet 和下面的命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-200">With the credentials object created (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) and with the  `MsOnline` module loaded, we can now connect to Office 365 by using the [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet and the following command.</span></span>
  
```
Connect-MsolService -Credential $credential
```

<span data-ttu-id="d3564-p121">请注意，您必须提供将凭据对象 ( `$credential`)。根据这些凭据，Office 365 会自动将您连接到正确的域。您不需要运行**连接 MsolService**时指定的域名称。</span><span class="sxs-lookup"><span data-stu-id="d3564-p121">Notice that all you have to provide is the credentials object ( `$credential`). Based on those credentials, Office 365 will automatically connect you to the correct domain. You do not have to specify your domain name when running **Connect-MsolService**.</span></span>
  
<span data-ttu-id="d3564-204">若要验证您实际上*是*连接到 Office 365，运行此命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-204">To verify that you really  *are*  connected to Office 365, run this command.</span></span>
  
```
Get-MsolDomain
```

<span data-ttu-id="d3564-205">系统应该会返回以下内容。</span><span class="sxs-lookup"><span data-stu-id="d3564-205">In return, you should get back something similar to this.</span></span>
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a><span data-ttu-id="d3564-206">步骤 4：连接到 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d3564-206">Step 4: Connect to SharePoint Online</span></span>
<span data-ttu-id="d3564-207"><a name="Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="d3564-207"></span></span>

<span data-ttu-id="d3564-208">导入 SharePoint Online 模块使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="d3564-208">Import the SharePoint Online module with the following command:</span></span>
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

<span data-ttu-id="d3564-209">_DisableNameChecking_开关禁止显示此警告。</span><span class="sxs-lookup"><span data-stu-id="d3564-209">The  _DisableNameChecking_ switch suppresses this warning.</span></span>
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

<span data-ttu-id="d3564-p122">要连接到 SharePoint Online，您需要提供两条信息： 您的凭据和 SharePoint Online 管理员站点的 URL。凭据部件很容易： 我们已经已经在变量中存储的`$credential`(请参阅[步骤 2： 创建一个 Windows PowerShell 凭据](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2))。与您的问题很容易确定，以及管理网站的 URL。假设您 Office 365 的域名是`litwareinc.onmicrosoft.com`。</span><span class="sxs-lookup"><span data-stu-id="d3564-p122">In order to connect to SharePoint Online, you need to supply two pieces of information: your credentials and the URL of your SharePoint Online admin site. The credentials part is easy: we've already stored that in the variable  `$credential` (see [Step 2: Create a Windows PowerShell credentials object](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)). As for the URL of your admin site, that's easy enough to determine, as well. Suppose your Office 365 domain name is  `litwareinc.onmicrosoft.com`.</span></span>
  
<span data-ttu-id="d3564-214">若要确定管理网站 URL，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d3564-214">To determine the admin site URL, do this:</span></span>
  
1. <span data-ttu-id="d3564-215">开始使用前缀`https://`。</span><span class="sxs-lookup"><span data-stu-id="d3564-215">Start by using the prefix  `https://`.</span></span>
    
2. <span data-ttu-id="d3564-p123">添加您的域名的域主机部分。例如，对于`litwareinc.onmicrosoft.com`，主机域名是`litwareinc`。为`contoso.onmicrosoft.com`，主机域名是`contoso`。</span><span class="sxs-lookup"><span data-stu-id="d3564-p123">Add the domain host portion of your domain name. For example, for  `litwareinc.onmicrosoft.com`, the domain host name is  `litwareinc`. For  `contoso.onmicrosoft.com`, the domain host name is  `contoso`.</span></span>
    
3. <span data-ttu-id="d3564-219">添加跟一个连字符 （-） `admin.sharepoint.com`。</span><span class="sxs-lookup"><span data-stu-id="d3564-219">Add a hyphen (-) followed by  `admin.sharepoint.com`.</span></span>
    
<span data-ttu-id="d3564-220">也就是会返回以下内容：</span><span class="sxs-lookup"><span data-stu-id="d3564-220">In other words:</span></span>
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
<span data-ttu-id="d3564-p124">构造 URL 后，您可以使用该 URL 和您的凭据的对象连接到 SharePoint Online。只需调用[连接 SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) cmdlet，使用类似于此的命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-p124">After you've constructed the URL, you can then use that URL and your credentials object to connect to SharePoint Online. Just call the [Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) cmdlet, using a command similar to this one.</span></span>
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

<span data-ttu-id="d3564-223">要验证已建立连接，请在 Windows PowerShell 运行下面的命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-223">To verify that the connection has been made, run the following command in Windows PowerShell.</span></span>
  
```
Get-SPOSite
```

<span data-ttu-id="d3564-p125">您应该获得所有 SharePoint Online 网站的列表。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="d3564-p125">You should get a list of all your SharePoint Online sites. Here is an example:</span></span>
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

<span data-ttu-id="d3564-p126">Office 365 命令 (所述[第 3 步： 连接到 Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) 将仍然工作。（试着运行**Get MsolUser**，并亲自查看）。这意味着，现在可以管理 Office 365 和 SharePoint Online 从 Windows PowerShell 的同一个实例。</span><span class="sxs-lookup"><span data-stu-id="d3564-p126">Your Office 365 commands (the ones described in [Step 3: Connect to Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) will still work. (Try running **Get-MsolUser**, and see for yourself.) That means that you can now manage both Office 365 and SharePoint Online from the same instance of Windows PowerShell.</span></span>
  
### <a name="step-5-connect-to-skype-for-business-online"></a><span data-ttu-id="d3564-228">步骤 5：连接到 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="d3564-228">Step 5: Connect to Skype for Business Online</span></span>
<span data-ttu-id="d3564-229"><a name="Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="d3564-229"></span></span>

<span data-ttu-id="d3564-p127">连接到 Skype 的在线业务 (和 Exchange Online 或安全&amp;法规遵从性中心) 与连接到 Office 365 或 SharePoint Online 不同。这是因为像 Office 365 和 SharePoint Online cmdlet 在线业务和 Exchange Online cmdlet 的 Skype 不获取安装在计算机上。相反，每次登录的时，相应的 cmdlet 暂时复制到您的计算机。当您注销时，请这些 cmdlet 然后会从您的计算机。</span><span class="sxs-lookup"><span data-stu-id="d3564-p127">Connecting to Skype for Business Online (and to Exchange Online or the Security &amp; Compliance Center) is different than connecting to Office 365 or to SharePoint Online. That's because the Skype for Business Online and Exchange Online cmdlets don't get installed on your computer like the Office 365 and the SharePoint Online cmdlets do. Instead, each time you sign in, the appropriate cmdlets are temporarily copied to your computer. When you sign off, those cmdlets are then removed from your computer.</span></span>
  
<span data-ttu-id="d3564-p128">为了连接到 Skype 的在线业务时，您需要导入 Skype 的在线业务模块。要做到这一点，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-p128">In order to connect to Skype for Business Online, you need to import the Skype for Business Online module. To do that, run this command.</span></span>
  
```
Import-Module SkypeOnlineConnector
```

<span data-ttu-id="d3564-236">第一次执行此操作时，你可能会看到以下警告消息，你可以安全地忽略它。</span><span class="sxs-lookup"><span data-stu-id="d3564-236">The first time you do this, you might see the following warning message, which you can safely ignore.</span></span>
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

<span data-ttu-id="d3564-237">导入该模块后，运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-237">After the module has been imported, run this command.</span></span>
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

<span data-ttu-id="d3564-p129">我们已创建远程 PowerShell 会话。在这种情况下，这意味着我们已连接到实例的 Windows PowerShell 的某个 Office 365 提供服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="d3564-p129">We have created a remote PowerShell session. In this case, that means that we've connected to an instance of Windows PowerShell running on one of the Office 365 servers.</span></span> 
  
<span data-ttu-id="d3564-p130">我们已经建立了连接到 Office 365，虽然我们还没有下载脚本、 cmdlet 和管理 Skype 的在线业务所需的其他项。要做到这一点，我们必须运行此命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-p130">Although we've made a connection to Office 365, we haven't downloaded the scripts, cmdlets, and other items needed to manage Skype for Business Online. To do that, we have to run this command.</span></span>
  
```
Import-PSSession $sfboSession
```

<span data-ttu-id="d3564-242">导入 Windows PowerShell 会话时，您应该看到类似于以下内容，报告为正在导入到您的计算机的联机业务 cmdlet 的所有 Skype 的进度条进度条。</span><span class="sxs-lookup"><span data-stu-id="d3564-242">When you import the Windows PowerShell session, you should see a progress bar similar to the following, a progress bar that reports on all the Skype for Business Online cmdlets being imported to your computer.</span></span>
  
![Lync Online 进度栏。](images/o365_powershell_lync_progress_bar.png)
  
<span data-ttu-id="d3564-244">在进度栏消失后，您应该会看到类似下面的输出结果。</span><span class="sxs-lookup"><span data-stu-id="d3564-244">When the progress bar disappears, you should then see output similar to the following.</span></span>
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a><span data-ttu-id="d3564-245">步骤 6：连接到 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="d3564-245">Step 6: Connect to Exchange Online</span></span>
<span data-ttu-id="d3564-246"><a name="Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="d3564-246"></span></span>

<span data-ttu-id="d3564-247">运行此命令，使用 Exchange 联机创建远程 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="d3564-247">Run this command, which creates a remote Windows PowerShell session with Exchange Online.</span></span>
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> <span data-ttu-id="d3564-p131">为什么是连接到 Exchange Online 比命令以连接到 Skype 的在线业务更复杂的命令？它从技术上讲，不是： 这两个命令执行完全相同的操作。但是，Skype 的在线业务团队创建其自己的 cmdlet —**新建 CsOnlineSession** — — 它会隐藏一些连接到 Exchange 联机时使用的参数 （如_身份验证_和_AllowRedirection_）。而无需您可以自己键入该信息的_身份验证_和_AllowRedirection_参数有效内置于**新建 CsOnlineSession** cmdlet。您必须连接到 Exchange Online，因为 Exchange 联机使用标准[新建 PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) cmdlet 连接到 Office 365 时输入这些参数。缺点是您必须键入更多要做。优点是不需要下载并安装联机交换模块。</span><span class="sxs-lookup"><span data-stu-id="d3564-p131">Why is the command for connecting to Exchange Online more complicated than the command to connect to Skype for Business Online? Technically, it's not: both commands do the exact same thing. However, the Skype for Business Online team created its own cmdlet— **New-CsOnlineSession** —that hides some of the parameters (like _Authentication_ and _AllowRedirection_) that are used when connecting to Exchange Online. Instead of requiring you to type that information yourself, the  _Authentication_ and _AllowRedirection_ parameters are effectively built in to the **New-CsOnlineSession** cmdlet. You have to type those parameters when connecting to Exchange Online because Exchange Online uses the standard [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621) cmdlet to connect to Office 365. The disadvantage is that you have a little more typing to do. The advantage is that you don't have to download and install an Exchange Online module.</span></span>
  
<span data-ttu-id="d3564-255">所有您需要做现在是导入此远程会话，只需像 Skype 的在线业务。</span><span class="sxs-lookup"><span data-stu-id="d3564-255">All you have to do now is import this remote session, just like we did with Skype for Business Online.</span></span>
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

<span data-ttu-id="d3564-256">然后，你应该会在屏幕上看到类似下面的内容。</span><span class="sxs-lookup"><span data-stu-id="d3564-256">You should see something similar to this on the screen.</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

<span data-ttu-id="d3564-257">现在，尝试运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-257">Now try running this command.</span></span>
  
```
Get-AcceptedDomain
```

<span data-ttu-id="d3564-258">作为回报，您应该看到信息关于您 Office 365 配置域中的电子邮件地址在 Exchange 联机。</span><span class="sxs-lookup"><span data-stu-id="d3564-258">In return, you should see information about your Office 365 domains that are configured for email addresses in Exchange Online.</span></span>
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a><span data-ttu-id="d3564-259">第 7 步： 连接到安全&amp;法规遵从性中心</span><span class="sxs-lookup"><span data-stu-id="d3564-259">Step 7: Connect to the Security &amp; Compliance Center</span></span>
<span data-ttu-id="d3564-260"><a name="Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="d3564-260"></span></span>

<span data-ttu-id="d3564-p132">安全&amp;法规遵从性中心是允许您从一个位置管理法规遵从性功能的 Office 365 中的服务。有关详细信息，请参阅[Office 365 提供法规遵从性中心](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d3564-p132">The Security &amp; Compliance Center is a service in Office 365 that lets you to manage compliance features from one location. For more information, see [Office 365 compliance center](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx).</span></span>
  
<span data-ttu-id="d3564-263">安全连接说明&amp;法规遵从性中心是非常类似于 Exchange 联机状态，但与附加花样，您会看到在一段时间。</span><span class="sxs-lookup"><span data-stu-id="d3564-263">The connection instructions for the Security &amp; Compliance Center are very similar to those for Exchange Online, but with an added twist, which you'll see in a moment.</span></span>
  
<span data-ttu-id="d3564-264">运行以下命令，创建具有安全性的远程 PowerShell 会话&amp;法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="d3564-264">Run this command, which creates a remote PowerShell session with the Security &amp; Compliance Center.</span></span>
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

<span data-ttu-id="d3564-265">马上运行此命令：</span><span class="sxs-lookup"><span data-stu-id="d3564-265">Now run this command:</span></span>
  
```
Import-PSSession $ccSession -Prefix cc
```

<span data-ttu-id="d3564-p133">同样，该命令是与 Exchange Online 的命令非常相似。因为安全性不有任何未经批准的谓词， _DisableNameChecking_交换机不需要&amp;法规遵从性中心。但是呢，它更多`-Prefix cc`参数和值吗？这就是我们告诉您有关附加的花样。</span><span class="sxs-lookup"><span data-stu-id="d3564-p133">Again, this command is very similar to the command for Exchange Online. The  _DisableNameChecking_ switch isn't required because there are no unapproved verbs in the Security &amp; Compliance Center. But what about that additional `-Prefix cc` parameter and value? That's the added twist we told you about.</span></span>
  
<span data-ttu-id="d3564-p134">联机交换和安全&amp;法规遵从性中心共享某些 cmdlet 的具有相同的名称，并提供相同的功能。**获得 RoleGroup**是一个例子。</span><span class="sxs-lookup"><span data-stu-id="d3564-p134">Exchange Online and the Security &amp; Compliance Center share some cmdlets that have exactly the same names and provide the same functionality. **Get-RoleGroup** is an example.</span></span>
  
<span data-ttu-id="d3564-p135">所以怎么样如果您尝试导入包含具有相同名称的 cmdlet 的两个会话？它们会相互冲突。您将获得大的黄色警告消息，指出：`WARNING: Proxy creation has been skipped for the following command:`跟冲突 cmdlet 无法导入的列表。最终结果如何？因为您连接第一次，那里，但不是能以安全运行**Get RoleGroup** ，您可以在 Exchange 联机运行**Get RoleGroup** &amp;法规遵从性中心，因为您连接上一次出现，而冲突的 cmdlet 拒绝导入。</span><span class="sxs-lookup"><span data-stu-id="d3564-p135">So what happens if you try to import two sessions that contain cmdlets with the same name? They collide. You'll get a big yellow warning message that says,  `WARNING: Proxy creation has been skipped for the following command:` followed by the list of conflicting cmdlets that couldn't be imported. The end result? You can run **Get-RoleGroup** in Exchange Online because you connected there first, but you can't run **Get-RoleGroup** in the Security &amp; Compliance Center because you connected there last and the conflicting cmdlets refused to import.</span></span>
  
<span data-ttu-id="d3564-p136">处理这个问题的最简单方法是将任意文本前缀添加到导入的安全&amp;法规遵从性中心的 cmdlet。我们该使用_前缀_参数以及"抄送"上**导入 PSSession** cmdlet 的值。未，我们做什么？它通过 （稍微） 更改安全消除冲突&amp;为此会话的法规遵从性中心 cmdlet 名称。所有导入的安全&amp;法规遵从性中心的 cmdlet 现在开始使用"抄送"名词部分的 cmdlet 名称 (右边的"-")。例如，争议的**Get RoleGroup** cmdlet 安全成为**获取 ccRoleGroup** &amp;以便不冲突与**获取 RoleGroup**的 Exchange Online 的法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="d3564-p136">The easiest way to deal with this problem is to add an arbitrary text prefix to the imported Security &amp; Compliance Center cmdlets. We did that using the  _Prefix_ parameter with the value "cc" on the **Import-PSSession** cmdlet. What did that do for us? It eliminated the conflicts by (slightly) changing the Security &amp; Compliance Center cmdlet names for this session. All of the imported Security &amp; Compliance Center cmdlets now start with "cc" in the noun part of the cmdlet name (to the right of the "-"). For example, the contentious **Get-RoleGroup** cmdlet becomes **Get-ccRoleGroup** for the Security &amp; Compliance Center so it doesn't conflict with **Get-RoleGroup** for Exchange Online.</span></span>
  
<span data-ttu-id="d3564-p137">不足之处？ *所有* 安全&amp;法规遵从性中心 cmdlet 名称接收"cc"前缀 — — 甚至不需要它的唯一 cmdlet。例如， **Get ComplianceSearch**成为**获取 ccComplianceSearch**虽然有没有这种 cmdlet 在 Exchange 联机。当考虑一个 Windows PowerShell 会话中管理所有的 Office 365 提供服务的好处是有点痛，但不是算太坏。只需记住在所有过程中安全性的 cmdlet 名称添加"抄送"&amp;法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="d3564-p137">The downside?  *All*  Security &amp; Compliance Center cmdlet names receive the "cc" prefix—even unique cmdlets that don't need it. For example, **Get-ComplianceSearch** becomes **Get-ccComplianceSearch** even though there is no such cmdlet in Exchange Online. It's a bit of a pain, but not too bad when you consider the benefits of managing all Office 365 services in a single Windows PowerShell session. Just remember to add "cc" to the cmdlet names for all procedures in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="d3564-288">如果一切顺利，您将看到类似下面的信息：</span><span class="sxs-lookup"><span data-stu-id="d3564-288">If all goes well, you'll see something similar to this:</span></span>
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

<span data-ttu-id="d3564-289">现在您可以自由地在一个 Windows PowerShell 会话中管理所有 Office 365 提供服务。</span><span class="sxs-lookup"><span data-stu-id="d3564-289">Now you are free to manage all Office 365 services in a single Windows PowerShell session.</span></span>
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a><span data-ttu-id="d3564-290">步骤 8：顺利结束 PowerShell 会话</span><span class="sxs-lookup"><span data-stu-id="d3564-290">Step 8: Gracefully end your PowerShell sessions</span></span>
<span data-ttu-id="d3564-291"><a name="Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="d3564-291"></span></span>

<span data-ttu-id="d3564-p138">如果只关闭 Windows PowerShell 窗口，您 Skype 业务在线远程连接将保持活动状态为接下来的 15 分钟左右。Skype 的在线业务限制的同时，任何人或任何一个域可以具有打开的连接数，因为它可能是一个问题。Skype 的在线业务，与单独的管理员可以有，顶多三个打开的连接一次，一个域中可以存在九个打开的连接的最大。如果您在登录 Skype 的在线业务，然后退出而没有正确地关闭会话，该会话会保持打开接下来的 15 分钟左右。因此，这就是一个较少的连接提供给您或您的域中的其他管理员。</span><span class="sxs-lookup"><span data-stu-id="d3564-p138">If you just close the Windows PowerShell window, your Skype for Business Online remote connection will remain active for the next 15 minutes or so. Because Skype for Business Online limits the number of simultaneous connections that any one person or any one domain can have open, that could be a problem. With Skype for Business Online, an individual administrator can have, at most, three open connections at one time, and a domain can have a maximum of nine open connections. If you sign in to Skype for Business Online and then exit without properly closing the session, that session remains open for the next 15 minutes or so. As a result, that's one fewer connection available to you or to other administrators in your domain.</span></span>
  
<span data-ttu-id="d3564-p139">相反，让我们关闭远程会话 Skype 的在线业务、 在线交换和安全&amp;正常中心的法规遵从性。我们这样做之前，请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-p139">Instead, let's close the remote sessions for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center gracefully. Before we do that, run this command.</span></span>
  
```
Get-PSSession
```

<span data-ttu-id="d3564-p140">[获得 PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet 应该显示您有至少三个远程会话打开，分别为 Skype 的在线业务、 在线交换和安全&amp;（可能会有超过三个遥控器的法规遵从性中心正在运行的会话，这取决于是否已使用 Windows PowerShell 的此实例连接到其他 Office 365 提供服务之外）。您应看到类似于以下内容。</span><span class="sxs-lookup"><span data-stu-id="d3564-p140">The [Get-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet should show you that you have at least three remote sessions open, one for Skype for Business Online, one for Exchange Online and one for the Security &amp; Compliance Center (it's possible you could have more than three remote sessions running, depending on whether you've used this instance of Windows PowerShell to connect to something else besides the Office 365 services). You should see something similar to the following.</span></span>
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

<span data-ttu-id="d3564-p141">若要关闭这些三个会话，请运行这些命令一次。第一个命令关闭 Skype 业务联机会话，Exchange 联机会话时，该第二个关闭，第三个关闭安全&amp;法规遵从性中心会话。</span><span class="sxs-lookup"><span data-stu-id="d3564-p141">To close these three sessions, run these commands one at a time. The first command closes the Skype for Business Online session, the second closes the Exchange Online session, and the third closes the Security &amp; Compliance Center session.</span></span>
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

<span data-ttu-id="d3564-303">如果您现在运行**Get PSSession** cmdlet，您应看到任何根本 （除非您必须启动并运行其他远程会话）。</span><span class="sxs-lookup"><span data-stu-id="d3564-303">If you now run the **Get-PSSession** cmdlet, you should see nothing at all (unless you have other remote sessions up and running).</span></span>
  
![没有任何远程会话的 Windows PowerShell 控制台](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> <span data-ttu-id="d3564-305">如果您希望关闭所有在同一时间的远程会话，则可以使用此命令： >`Get-PSSession | Remove-PSSession`</span><span class="sxs-lookup"><span data-stu-id="d3564-305">If you'd prefer to close all your remote sessions at the same time, you can use this command: >  `Get-PSSession | Remove-PSSession`</span></span>
  
<span data-ttu-id="d3564-306">如果您现在尝试从任何这些关闭会话 (例如， **Get CsMeetingConfiguration**在 Skype 的在线业务) 运行 cmdlet 将类似于下面的错误消息。</span><span class="sxs-lookup"><span data-stu-id="d3564-306">If you now try running a cmdlet from any of these closed sessions (for example, **Get-CsMeetingConfiguration** in Skype for Business Online) you'll get an error message that's similar to this one.</span></span>
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="d3564-307">我们收到该错误信息，因为 Skype 在线业务、 在线交换和安全的 cmdlet&amp;我们关闭远程会话时删除了法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="d3564-307">We get that error message because the cmdlets for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center were deleted when we closed the remote sessions.</span></span>
  
<span data-ttu-id="d3564-308">若要关闭 SharePoint Online 的会话，请键入以下命令。</span><span class="sxs-lookup"><span data-stu-id="d3564-308">To close the SharePoint Online session, type this command.</span></span>
  
```
Disconnect-SPOService
```

<span data-ttu-id="d3564-309">如果您现在尝试运行**Get SPOSite** cmdlet，您将有类似下面的错误消息。</span><span class="sxs-lookup"><span data-stu-id="d3564-309">If you now try to run the **Get-SPOSite** cmdlet, you'll get an error message like this.</span></span>
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

<span data-ttu-id="d3564-310">无法检索网站信息，因为您不再连接到 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="d3564-310">You can't retrieve site information because you're no longer connected to SharePoint Online.</span></span>
  
<span data-ttu-id="d3564-p142">至于与 Office 365 的连接，尽管没有**连接 MsolService** cmdlet，没有相应的**断开连接 MsolService** cmdlet。因此对于 Office 365 只关闭 Windows PowerShell 窗口。尽管如此，它仍然是好办法，这最后一个，因此您可以正确地断开从 SharePoint 在线，Skype 在线业务、 在线交换和安全&amp;法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="d3564-p142">As for your connection to Office 365, although there's a **Connect-MsolService** cmdlet, there's no corresponding **Disconnect-MsolService** cmdlet. So for Office 365, just close the Windows PowerShell window. Nevertheless, it's still a good idea to do this last so you can properly disconnect from SharePoint Online, Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center.</span></span>
  
## <a name="new-to-office-365"></a><span data-ttu-id="d3564-314">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="d3564-314">New to Office 365?</span></span>
<span data-ttu-id="d3564-315"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="d3564-315"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="d3564-316">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3564-316">See also</span></span>

#### 

[<span data-ttu-id="d3564-317">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="d3564-317">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d3564-318">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="d3564-318">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="d3564-319">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d3564-319">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="d3564-320">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="d3564-320">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d3564-321">使用 Windows PowerShell 在 Office 365 中创建报告</span><span class="sxs-lookup"><span data-stu-id="d3564-321">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

