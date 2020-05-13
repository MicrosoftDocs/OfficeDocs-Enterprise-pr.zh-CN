---
title: 在单个 Windows PowerShell 窗口中连接所有 Office 365 服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 摘要：将 Windows PowerShell 连接到单个 Windows PowerShell 窗口中的所有 Office 365 服务。
ms.openlocfilehash: 47fd2be814b446cf12b136e359cdadc9374a7ab6
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208803"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="bd1cc-103">在单个 Windows PowerShell 窗口中连接所有 Office 365 服务</span><span class="sxs-lookup"><span data-stu-id="bd1cc-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="bd1cc-104">使用 PowerShell 管理 Office 365 时，可以在与 Microsoft 365 管理中心、SharePoint Online、Exchange Online、Skype for Business Online、Microsoft 团队和安全合规中心相同的时间同时打开最长五个不同的 Windows PowerShell 会话 &amp; 。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-104">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="bd1cc-105">在单独的 Windows PowerShell 会话中有五种不同的连接方法，你的桌面可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="bd1cc-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![五个同时运行的 Windows PowerShell 控制台](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="bd1cc-107">这对管理 Office 365 不是最佳的，因为您无法在这五个 windows 之间交换跨服务管理的数据。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-107">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="bd1cc-108">本主题介绍如何使用 Windows PowerShell 的单个实例，您可从中管理 Office 365、Skype for Business Online、Exchange Online、SharePoint Online、Microsoft 团队和安全 &amp; 合规中心。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="bd1cc-109">本文当前只包含连接到 Office 365 全球（+ GCC）云的命令。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-109">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="bd1cc-110">其他说明提供了指向包含有关连接到其他 Office 365 云的信息的文章的链接。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-110">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="bd1cc-111">准备工作</span><span class="sxs-lookup"><span data-stu-id="bd1cc-111">Before you begin</span></span>

<span data-ttu-id="bd1cc-112">在可以从 Windows PowerShell 的单个实例管理所有 Office 365 之前，请考虑以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="bd1cc-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="bd1cc-113">在这些步骤中使用的 Office 365工作或学校帐户 须为 Office 365 管理员角色的成员。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-113">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role.</span></span> <span data-ttu-id="bd1cc-114">有关详细信息，请参阅[关于 Office 365 管理员角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-114">For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span> <span data-ttu-id="bd1cc-115">这是 Office 365 PowerShell 的要求，并不一定适用于所有其他 Office 365 服务。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-115">This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="bd1cc-116">您可以使用以下 64 位版本的 Windows：</span><span class="sxs-lookup"><span data-stu-id="bd1cc-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="bd1cc-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="bd1cc-117">Windows 10</span></span>
    
  - <span data-ttu-id="bd1cc-118">Windows 8.1 或 Windows 8</span><span class="sxs-lookup"><span data-stu-id="bd1cc-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="bd1cc-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="bd1cc-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="bd1cc-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="bd1cc-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="bd1cc-121">Windows Server 2012 R2 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="bd1cc-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="bd1cc-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="bd1cc-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="bd1cc-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="bd1cc-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="bd1cc-124">\*您需要安装 Microsoft .NET Framework 4.5。*x* ，然后是 Windows management framework 3.0 或 Windows management framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="bd1cc-125">有关详细信息，请参阅[安装 .Net Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[windows management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[windows management framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="bd1cc-126">由于 Skype for business Online 模块和其中一个 Office 365 模块的要求，您需要使用 Windows 的64位版本的 Windows。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="bd1cc-127">您需要安装 Azure Active Directory （Azure AD）、Exchange Online、SharePoint Online、Skype for Business Online 和团队所需的模块：</span><span class="sxs-lookup"><span data-stu-id="bd1cc-127">You need to install the modules that are required for Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="bd1cc-128">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="bd1cc-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="bd1cc-129">SharePoint Online 命令行管理程序</span><span class="sxs-lookup"><span data-stu-id="bd1cc-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="bd1cc-130">Skype for Business Online、Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="bd1cc-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="bd1cc-131">Exchange Online PowerShell V2</span><span class="sxs-lookup"><span data-stu-id="bd1cc-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="bd1cc-132">团队 PowerShell 概述</span><span class="sxs-lookup"><span data-stu-id="bd1cc-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="bd1cc-133">需要将 Windows PowerShell 配置为为 Skype for Business Online 和安全合规中心运行已签名的脚本 &amp; 。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="bd1cc-134">若要执行此操作，请在提升的 Windows PowerShell 会话（通过选择 "**以管理员身份运行**" 打开的 windows powershell 窗口）中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="bd1cc-135">使用密码时的连接步骤</span><span class="sxs-lookup"><span data-stu-id="bd1cc-135">Connection steps when using a password</span></span>

<span data-ttu-id="bd1cc-136">以下是在单个 PowerShell 窗口中连接到所有服务的步骤。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="bd1cc-137">打开 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="bd1cc-138">运行此命令并输入 Office 365 的工作或学校帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-138">Run this command and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="bd1cc-139">运行此命令以使用 Azure Active Directory PowerShell for Graph 模块连接到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-139">Run this command to connect to Azure AD using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="bd1cc-140">或者，如果您使用的是 Windows PowerShell 模块的 Microsoft Azure Active Directory 模块，请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="bd1cc-141">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="bd1cc-142">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="bd1cc-143">运行这些命令以连接到 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="bd1cc-144">将_ \< domainhost>_ 替换为您的域的实际值。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-144">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="bd1cc-145">例如，对于 "litwareinc.onmicrosoft.com"， _ \< domainhost>_ 值为 "litwareinc"。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-145">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="bd1cc-146">运行这些命令以连接到 Skype for Business Online。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-146">Run these commands to connect to Skype for Business Online.</span></span> <span data-ttu-id="bd1cc-147">`WSMan NetworkDelayms`第一次连接时需要增加值的警告，应将其忽略。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-147">A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="bd1cc-148">运行此命令以连接到 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-148">Run this command to connect to Exchange Online.</span></span>
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
><span data-ttu-id="bd1cc-149">若要连接到除全球版之外的 Office 365 云的 Exchange Online，请使用 **-ExchangeEnvironmentName**参数。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-149">To connect to Exchange Online for Office 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="bd1cc-150">有关详细信息，请参阅[ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) 。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>
>

7. <span data-ttu-id="bd1cc-151">运行这些命令以连接到团队 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-151">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="bd1cc-152">若要连接到全球以外的 Microsoft 团队云，请参阅[MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps)。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="bd1cc-153">运行这些命令以连接到安全 &amp; 合规性中心。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="bd1cc-154">若要连接到 &amp; 世界各地的 office 365 云的安全合规中心，请参阅[连接到 Office 365 安全性 & 合规性中心 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-154">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="bd1cc-155">以下是在使用 Azure Active Directory PowerShell for Graph 模块时，单个块中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="bd1cc-156">指定您的域主机的名称，然后一次运行所有域主机。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

<span data-ttu-id="bd1cc-157">此外，在使用适用于 Windows PowerShell 模块的 Microsoft Azure Active Directory 模块时，以下是单个块中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="bd1cc-158">指定您的域主机的名称，然后一次运行所有域主机。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

<span data-ttu-id="bd1cc-159">当您准备好关闭 Windows PowerShell 窗口时，运行此命令以删除 Skype for Business Online、SharePoint Online、安全 &amp; 合规性中心和团队的活动会话：</span><span class="sxs-lookup"><span data-stu-id="bd1cc-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="bd1cc-160">使用多重身份验证时的连接步骤</span><span class="sxs-lookup"><span data-stu-id="bd1cc-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="bd1cc-161">下面是使用 Azure Active Directory PowerShell for Graph 模块在单个窗口中通过多重身份验证连接到 Azure AD、SharePoint Online、Skype for Business、Exchange Online 和团队的单个块中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="bd1cc-162">指定用户帐户的用户主体名称（UPN）名称和您的域主机名，然后一次运行所有这些名称。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

<span data-ttu-id="bd1cc-163">此外，以下是使用适用于 Windows PowerShell 模块的 Microsoft Azure Active Directory 模块的所有命令。</span><span class="sxs-lookup"><span data-stu-id="bd1cc-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

<span data-ttu-id="bd1cc-164">有关安全 &amp; 合规中心，请参阅使用多重身份验证连接[到 Office 365 Security & 合规性中心 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) ，以使用多重身份验证进行连接：</span><span class="sxs-lookup"><span data-stu-id="bd1cc-164">For the Security &amp; Compliance Center, see [Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="bd1cc-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd1cc-165">See also</span></span>

- [<span data-ttu-id="bd1cc-166">连接到 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd1cc-166">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="bd1cc-167">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bd1cc-167">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="bd1cc-168">使用 Office 365 PowerShell 管理用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="bd1cc-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="bd1cc-169">使用 Windows PowerShell 在 Office 365 中创建报告</span><span class="sxs-lookup"><span data-stu-id="bd1cc-169">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
