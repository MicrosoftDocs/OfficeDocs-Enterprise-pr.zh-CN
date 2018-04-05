---
title: 在单个 Windows PowerShell 窗口中连接所有 Office 365 服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
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
description: 摘要： 将 Windows PowerShell 连接到一个 Windows PowerShell 窗口中的所有 Office 365 提供服务。
ms.openlocfilehash: ccd8ed1dc53d306aa77d79ac0270f5bd24dd9298
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="3fafe-103">在单个 Windows PowerShell 窗口中连接所有 Office 365 服务</span><span class="sxs-lookup"><span data-stu-id="3fafe-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="3fafe-104">**摘要：**而不是管理不同的 Office 365 服务单独 PowerShell 控制台窗口中，可以连接到所有的 Office 365 提供服务并从单个控制台窗口中对它们进行管理。</span><span class="sxs-lookup"><span data-stu-id="3fafe-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="3fafe-p101">当使用 PowerShell Office 365 管理时，很可能有最多五个不同的 Windows PowerShell 会话打开对应于 Office 365 管理中心、 SharePoint Online、 Exchange Online，Skype 的在线业务和&amp;符合性中心。在单独的 Windows PowerShell 会话中的五种不同的连接方法，与您的桌面可以如下所示：</span><span class="sxs-lookup"><span data-stu-id="3fafe-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![五个同时运行的 Windows PowerShell 控制台](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="3fafe-p102">这不是最适合于管理 Office 365，因为不能交换跨服务管理这些五个窗口间的数据。本主题介绍如何使用与管理 Office 365、 为业务联机状态，Exchange Online，SharePoint Online，Skype 和安全的 Windows PowerShell 的单个实例&amp;法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="3fafe-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="3fafe-110">本文是在过程中被更新，以使用 Azure 活动目录 V2 PowerShell 模块并进行多因素身份验证 (MFA)。</span><span class="sxs-lookup"><span data-stu-id="3fafe-110">This article is in the process of being updated to use the Azure Active Directory V2 PowerShell module and for multifactor authentication (MFA).</span></span>
>
  
## <a name="before-you-begin"></a><span data-ttu-id="3fafe-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="3fafe-111">Before you begin</span></span>
<span data-ttu-id="3fafe-112"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="3fafe-112"></span></span>

<span data-ttu-id="3fafe-113">您可以从 Windows PowerShell 的单个实例中管理所有 Office 365 的之前，请考虑以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="3fafe-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="3fafe-p103">Office 365 的工作或学校对使用这些过程需要 Office 365 管理角色的成员的帐户。有关详细信息，请参阅[有关 Office 365 管理角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。此 Office 365 PowerShell，不一定能为所有其他 Office 365 提供服务的要求。</span><span class="sxs-lookup"><span data-stu-id="3fafe-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="3fafe-117">您可以使用以下 64 位版本的 Windows：</span><span class="sxs-lookup"><span data-stu-id="3fafe-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="3fafe-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3fafe-118">Windows 10</span></span>
    
  - <span data-ttu-id="3fafe-119">Windows 8.1 或 Windows 8</span><span class="sxs-lookup"><span data-stu-id="3fafe-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="3fafe-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3fafe-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="3fafe-121">Windows Server 2012 R2 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3fafe-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="3fafe-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="3fafe-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="3fafe-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="3fafe-123">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="3fafe-p104">您需要安装 Microsoft.net 4.5。*x* ，然后是 Windows 管理框架 3.0 或 Windows 管理框架 4.0。有关详细信息，请参阅[安装.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[Windows 管理框架 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[Windows 管理框架 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。</span><span class="sxs-lookup"><span data-stu-id="3fafe-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="3fafe-126">您需要使用 64 位版本的 Windows 由于 Skype 的要求在线业务模块和 Office 365 模块之一。</span><span class="sxs-lookup"><span data-stu-id="3fafe-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="3fafe-127">您需要安装所需的 Office 365、 SharePoint Online 和 Skype 的在线业务的模块：</span><span class="sxs-lookup"><span data-stu-id="3fafe-127">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="3fafe-128">Microsoft 在线服务登录助理为 IT 专业人士一项的</span><span class="sxs-lookup"><span data-stu-id="3fafe-128">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - <span data-ttu-id="3fafe-129">Windows Azure 活动目录模块用于 Windows PowerShell （64-位版本） 用在提升 PowerShell 命令提示符**安装模块 MSOnline**命令。</span><span class="sxs-lookup"><span data-stu-id="3fafe-129">Windows Azure Active Directory Module for Windows PowerShell (64-bit version) with the **Install-Module MSOnline** command at an elevated PowerShell command prompt.</span></span>
   - [<span data-ttu-id="3fafe-130">SharePoint 在线管理外壳程序</span><span class="sxs-lookup"><span data-stu-id="3fafe-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="3fafe-131">Skype 的在线业务 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="3fafe-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="3fafe-p105">Windows PowerShell 需要配置运行 Skype 在线业务、 在线交换和安全签名的脚本&amp;法规遵从性中心。若要执行此操作，在提升的权限的 Windows PowerShell 会话中运行以下命令 （您选择**以管理员身份运行**，打开 Windows PowerShell 窗口）。</span><span class="sxs-lookup"><span data-stu-id="3fafe-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps"></a><span data-ttu-id="3fafe-134">连接的步骤</span><span class="sxs-lookup"><span data-stu-id="3fafe-134">Connection steps</span></span>
<span data-ttu-id="3fafe-135"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="3fafe-135"></span></span>

<span data-ttu-id="3fafe-136">这里是连接到一个 PowerShell 窗口中的所有服务的步骤。</span><span class="sxs-lookup"><span data-stu-id="3fafe-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="3fafe-137">以管理员身份 （使用**以管理员身份运行**） 打开 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3fafe-137">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="3fafe-138">运行此命令，并输入您的 Office 365 提供工作或学校帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="3fafe-138">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="3fafe-139">运行以下命令以连接到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="3fafe-139">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="3fafe-p106">运行以下命令以连接到 SharePoint Online。更换_\<domainhost >_与实际值为您的域。例如，对于`litwareinc.onmicrosoft.com`， _ \<domainhost >_值是`litwareinc`。</span><span class="sxs-lookup"><span data-stu-id="3fafe-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="3fafe-p107">运行以下命令以连接到 Skype 的在线业务。有关增加警告`WSMan NetworkDelayms`的值应在第一次连接，可以忽略。</span><span class="sxs-lookup"><span data-stu-id="3fafe-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="3fafe-145">运行以下命令以连接到 Exchange 联机。</span><span class="sxs-lookup"><span data-stu-id="3fafe-145">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. <span data-ttu-id="3fafe-146">运行以下命令以对安全连接&amp;法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="3fafe-146">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> <span data-ttu-id="3fafe-p108">"抄送"中的文本前缀添加到*所有*安全&amp;法规遵从性中心 cmdlet 名称以便您可以运行的 cmdlet，存在于 Exchange 联机和安全&amp;同一 Windows PowerShell 会话中的法规遵从性中心。例如， **Get RoleGroup**将成为安全**获取 ccRoleGroup** &amp;法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="3fafe-p108">The text prefix "cc" is added to  *all*  Security &amp; Compliance Center cmdlet names so you can run cmdlets that exist in both Exchange Online and the Security &amp; Compliance Center in the same Windows PowerShell session. For example, **Get-RoleGroup** becomes **Get-ccRoleGroup** in the Security &amp; Compliance Center.</span></span>
  
<span data-ttu-id="3fafe-p109">下面是在一个块的所有命令。指定您的域主机的名称，然后一次运行所有这些。</span><span class="sxs-lookup"><span data-stu-id="3fafe-p109">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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
<span data-ttu-id="3fafe-151">准备就绪以关闭 Windows PowerShell 窗口后，运行以下命令来删除联机业务、 Exchange Online，SharePoint Online，和安全到 Skype 的活动会话&amp;法规遵从性中心：</span><span class="sxs-lookup"><span data-stu-id="3fafe-151">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="new-to-office-365"></a><span data-ttu-id="3fafe-152">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="3fafe-152">New to Office 365?</span></span>
<span data-ttu-id="3fafe-153"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="3fafe-153"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="3fafe-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3fafe-154">See also</span></span>

- [<span data-ttu-id="3fafe-155">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="3fafe-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="3fafe-156">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="3fafe-156">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="3fafe-157">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3fafe-157">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="3fafe-158">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="3fafe-158">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="3fafe-159">使用 Windows PowerShell 在 Office 365 中创建报告</span><span class="sxs-lookup"><span data-stu-id="3fafe-159">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
