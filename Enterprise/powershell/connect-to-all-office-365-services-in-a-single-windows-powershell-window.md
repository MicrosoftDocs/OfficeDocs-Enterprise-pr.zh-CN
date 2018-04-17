---
title: 在单个 Windows PowerShell 窗口中连接所有 Office 365 服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/10/2018
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
ms.openlocfilehash: ffa603ec50c95f5800315eee07b4d01e058852f3
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="99a0c-103">在单个 Windows PowerShell 窗口中连接所有 Office 365 服务</span><span class="sxs-lookup"><span data-stu-id="99a0c-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="99a0c-104">**摘要：**而不是管理不同的 Office 365 服务单独 PowerShell 控制台窗口中，可以连接到所有的 Office 365 提供服务并从单个控制台窗口中对它们进行管理。</span><span class="sxs-lookup"><span data-stu-id="99a0c-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="99a0c-p101">当使用 PowerShell Office 365 管理时，很可能有最多五个不同的 Windows PowerShell 会话打开对应于 Office 365 管理中心、 SharePoint Online、 Exchange Online，Skype 的在线业务和&amp;符合性中心。在单独的 Windows PowerShell 会话中的五种不同的连接方法，与您的桌面可以如下所示：</span><span class="sxs-lookup"><span data-stu-id="99a0c-p101">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Office 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center. With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![五个同时运行的 Windows PowerShell 控制台](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="99a0c-p102">这不是最适合于管理 Office 365，因为不能交换跨服务管理这些五个窗口间的数据。本主题介绍如何使用与管理 Office 365、 为业务联机状态，Exchange Online，SharePoint Online，Skype 和安全的 Windows PowerShell 的单个实例&amp;法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="99a0c-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="99a0c-110">准备工作</span><span class="sxs-lookup"><span data-stu-id="99a0c-110">Before you begin</span></span>
<span data-ttu-id="99a0c-111"><a name="BeforeYouBegin"> </a></span><span class="sxs-lookup"><span data-stu-id="99a0c-111"></span></span>

<span data-ttu-id="99a0c-112">您可以从 Windows PowerShell 的单个实例中管理所有 Office 365 的之前，请考虑以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="99a0c-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="99a0c-p103">Office 365 的工作或学校对使用这些过程需要 Office 365 管理角色的成员的帐户。有关详细信息，请参阅[有关 Office 365 管理角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。此 Office 365 PowerShell，不一定能为所有其他 Office 365 提供服务的要求。</span><span class="sxs-lookup"><span data-stu-id="99a0c-p103">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="99a0c-116">您可以使用以下 64 位版本的 Windows：</span><span class="sxs-lookup"><span data-stu-id="99a0c-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="99a0c-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="99a0c-117">Windows 10</span></span>
    
  - <span data-ttu-id="99a0c-118">Windows 8.1 或 Windows 8</span><span class="sxs-lookup"><span data-stu-id="99a0c-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="99a0c-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="99a0c-119">Windows Server 2016</span></span>
    
  - <span data-ttu-id="99a0c-120">Windows Server 2012 R2 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="99a0c-120">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="99a0c-121">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="99a0c-121">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="99a0c-122">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="99a0c-122">Windows Server 2008 R2 SP1\*</span></span>
    
    * <span data-ttu-id="99a0c-p104">您需要安装 Microsoft.net 4.5。*x* ，然后是 Windows 管理框架 3.0 或 Windows 管理框架 4.0。有关详细信息，请参阅[安装.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[Windows 管理框架 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[Windows 管理框架 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。</span><span class="sxs-lookup"><span data-stu-id="99a0c-p104">You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0. For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="99a0c-125">您需要使用 64 位版本的 Windows 由于 Skype 的要求在线业务模块和 Office 365 模块之一。</span><span class="sxs-lookup"><span data-stu-id="99a0c-125">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="99a0c-126">您需要安装所需的 Office 365、 SharePoint Online 和 Skype 的在线业务的模块：</span><span class="sxs-lookup"><span data-stu-id="99a0c-126">You need to install the modules that are required for Office 365, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="99a0c-127">Microsoft 在线服务登录助理为 IT 专业人士一项的</span><span class="sxs-lookup"><span data-stu-id="99a0c-127">Microsoft Online Service Sign-in Assistant for IT Professionals RTW</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - <span data-ttu-id="99a0c-128">Windows Azure 活动目录模块用于 Windows PowerShell （64-位版本） 用在提升 PowerShell 命令提示符**安装模块 MSOnline**命令。</span><span class="sxs-lookup"><span data-stu-id="99a0c-128">Windows Azure Active Directory Module for Windows PowerShell (64-bit version) with the **Install-Module MSOnline** command at an elevated PowerShell command prompt.</span></span>
   - [<span data-ttu-id="99a0c-129">SharePoint 在线管理外壳程序</span><span class="sxs-lookup"><span data-stu-id="99a0c-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="99a0c-130">Skype 的在线业务 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="99a0c-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="99a0c-p105">Windows PowerShell 需要配置运行 Skype 在线业务、 在线交换和安全签名的脚本&amp;法规遵从性中心。若要执行此操作，在提升的权限的 Windows PowerShell 会话中运行以下命令 （您选择**以管理员身份运行**，打开 Windows PowerShell 窗口）。</span><span class="sxs-lookup"><span data-stu-id="99a0c-p105">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="99a0c-133">连接时使用的密码的步骤</span><span class="sxs-lookup"><span data-stu-id="99a0c-133">Connection steps when using a password</span></span>
<span data-ttu-id="99a0c-134"><a name="ConnStepsPassword"> </a></span><span class="sxs-lookup"><span data-stu-id="99a0c-134"></span></span>

<span data-ttu-id="99a0c-135">这里是连接到一个 PowerShell 窗口中的所有服务的步骤。</span><span class="sxs-lookup"><span data-stu-id="99a0c-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="99a0c-136">以管理员身份 （使用**以管理员身份运行**） 打开 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="99a0c-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="99a0c-137">运行此命令，并输入您的 Office 365 提供工作或学校帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="99a0c-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```
  $credential = Get-Credential
  ```

3. <span data-ttu-id="99a0c-138">运行以下命令以连接到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="99a0c-138">Run these commands to connect to Office 365.</span></span>
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. <span data-ttu-id="99a0c-p106">运行以下命令以连接到 SharePoint Online。更换_\<domainhost >_与实际值为您的域。例如，对于`litwareinc.onmicrosoft.com`， _ \<domainhost >_值是`litwareinc`。</span><span class="sxs-lookup"><span data-stu-id="99a0c-p106">Run these commands to connect to SharePoint Online. Replace  _\<domainhost>_ with the actual value for your domain. For example, for `litwareinc.onmicrosoft.com`, the  _\<domainhost>_ value is `litwareinc`.</span></span>
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="99a0c-p107">运行以下命令以连接到 Skype 的在线业务。有关增加警告`WSMan NetworkDelayms`的值应在第一次连接，可以忽略。</span><span class="sxs-lookup"><span data-stu-id="99a0c-p107">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="99a0c-144">运行以下命令以连接到 Exchange 联机。</span><span class="sxs-lookup"><span data-stu-id="99a0c-144">Run these commands to connect to Exchange Online.</span></span>
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. <span data-ttu-id="99a0c-145">运行以下命令以对安全连接&amp;法规遵从性中心。</span><span class="sxs-lookup"><span data-stu-id="99a0c-145">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
  Import-PSSession $SccSession
  ```

<span data-ttu-id="99a0c-p108">下面是在一个块的所有命令。指定您的域主机的名称，然后一次运行所有这些。</span><span class="sxs-lookup"><span data-stu-id="99a0c-p108">Here are all the commands in a single block. Specify the name of your domain host, and then run them all at one time.</span></span>
  
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
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $SccSession
```
<span data-ttu-id="99a0c-148">准备就绪以关闭 Windows PowerShell 窗口后，运行以下命令来删除联机业务、 Exchange Online，SharePoint Online，和安全到 Skype 的活动会话&amp;法规遵从性中心：</span><span class="sxs-lookup"><span data-stu-id="99a0c-148">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="99a0c-149">连接时使用多因素身份验证的步骤</span><span class="sxs-lookup"><span data-stu-id="99a0c-149">Connection steps when using multi-factor authentication</span></span>
<span data-ttu-id="99a0c-150"><a name="ConnStepsMFA"> </a></span><span class="sxs-lookup"><span data-stu-id="99a0c-150"></span></span>

<span data-ttu-id="99a0c-p109">在一个块连接到 Azure 的广告，还有所有命令 SharePoint Online 和 Skype 的 Buiness 在单个窗口中使用多因素身份验证。指定的全局管理员帐户的用户主体名称 (UPN) 名称和域名主机，然后再一次运行所有这些。</span><span class="sxs-lookup"><span data-stu-id="99a0c-p109">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window. Specify the user principal name (UPN) name of a global administrator account and your domain host name, and then run them all at one time.</span></span>

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
#If you are running Office 365 commands that contain "AzureAd" in their name, use this command:
Connect-AzureAD
#If you are running Office 365 commands that contain "Msol" in their name, comment the preceding command and un-comment the following command:
#Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

<span data-ttu-id="99a0c-153">为 Exchange 联机和安全&amp;法规遵从性中心，请参阅下面的主题使用多因素身份验证进行连接：</span><span class="sxs-lookup"><span data-stu-id="99a0c-153">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- <span data-ttu-id="99a0c-154">[连接到 Exchange 联机 PowerShell 使用多因素身份验证](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)。</span><span class="sxs-lookup"><span data-stu-id="99a0c-154">[Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell).</span></span>
- [<span data-ttu-id="99a0c-155">连接到 Office 365 安全和法规遵从性中心 PowerShell 使用多因素身份验证</span><span class="sxs-lookup"><span data-stu-id="99a0c-155">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="99a0c-156">请注意，在两种情况下，必须使用 Exchange 联机远程 PowerShell 模块的单独会话连接。</span><span class="sxs-lookup"><span data-stu-id="99a0c-156">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="99a0c-157">刚开始接触 Office 365？</span><span class="sxs-lookup"><span data-stu-id="99a0c-157">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="99a0c-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99a0c-158">See also</span></span>

- [<span data-ttu-id="99a0c-159">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="99a0c-159">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="99a0c-160">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="99a0c-160">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="99a0c-161">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="99a0c-161">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="99a0c-162">使用 Office 365 PowerShell 管理用户帐户和许可证</span><span class="sxs-lookup"><span data-stu-id="99a0c-162">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="99a0c-163">使用 Windows PowerShell 在 Office 365 中创建报告</span><span class="sxs-lookup"><span data-stu-id="99a0c-163">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
