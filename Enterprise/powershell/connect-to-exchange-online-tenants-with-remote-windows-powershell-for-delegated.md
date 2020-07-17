---
title: 通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 摘要：使用 DelegatedOrg 值，通过远程 Windows PowerShell 连接到 Exchange Online。
ms.openlocfilehash: 4a9f08325fc56308b27467423b047375985562c5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997368"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="52b63-103">通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户</span><span class="sxs-lookup"><span data-stu-id="52b63-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52b63-p101">本主题中的过程仅适用于委派访问权限 (DAP) 合作伙伴。如果你不是 DAP 合作伙伴，请不要使用此主题中的过程。</span><span class="sxs-lookup"><span data-stu-id="52b63-p101">The procedures in this topic are only for Delegated Access Permission (DAP) partners. If you aren't a DAP partner, don't use the procedures in this topic.</span></span> 
  
<span data-ttu-id="52b63-106">DAP 合作伙伴是整合和云解决方案提供商 (CSP) 合作伙伴。</span><span class="sxs-lookup"><span data-stu-id="52b63-106">DAP partners are Syndication and Cloud Solution Providers (CSP) partners.</span></span> <span data-ttu-id="52b63-107">它们通常是面向其他公司的网络或电信提供程序。</span><span class="sxs-lookup"><span data-stu-id="52b63-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="52b63-108">它们将订阅捆绑到为其客户提供的服务产品中。</span><span class="sxs-lookup"><span data-stu-id="52b63-108">They bundle subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="52b63-109">他们拥有将代表（AOBO）权限自动授予给其 Microsoft 365 客户租赁的 "管理" 的合作伙伴租赁，以便他们可以管理和报告其所有客户租赁。</span><span class="sxs-lookup"><span data-stu-id="52b63-109">They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Microsoft 365 customer tenancies so they can administer and report on all of their customer tenancies.</span></span>

<span data-ttu-id="52b63-110">建立合作伙伴可以使用 Exchange Online PowerShell 管理客户 Exchange Online 设置，并从命令行获取 Microsoft 365 报告。</span><span class="sxs-lookup"><span data-stu-id="52b63-110">DAP partners can use Exchange Online PowerShell to manage customer Exchange Online settings and get Microsoft 365 reports from the command line.</span></span> <span data-ttu-id="52b63-111">可以使用本地计算机上的 Windows PowerShell 创建到 Exchange Online 的远程 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="52b63-111">You use Windows PowerShell on your local computer to create a remote PowerShell session to Exchange Online.</span></span> <span data-ttu-id="52b63-112">这是一个简单的三步骤过程，可在其中输入凭据、提供所需的连接设置，然后将 Exchange Online cmdlet 导入到您的本地 Windows PowerShell 会话中，以便您可以使用它们。</span><span class="sxs-lookup"><span data-stu-id="52b63-112">It's a simple three-step process where you enter your credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>

> [!NOTE]
> <span data-ttu-id="52b63-p104">DAP 合作伙伴无法使用[使用多重身份验证连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) 中的过程连接到其在 Exchange Online PowerShell 中的客户租户组织。MFA 和 Exchange Online 远程 PowerShell 模块无法使用委派身份验证。</span><span class="sxs-lookup"><span data-stu-id="52b63-p104">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell. MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="52b63-115">开始前，有必要了解什么？</span><span class="sxs-lookup"><span data-stu-id="52b63-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="52b63-116">估计完成时间：5 分钟</span><span class="sxs-lookup"><span data-stu-id="52b63-116">Estimated time to complete: 5 minutes</span></span>

- <span data-ttu-id="52b63-117">可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="52b63-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="52b63-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="52b63-118">Windows 10</span></span>

  - <span data-ttu-id="52b63-119">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="52b63-119">Windows 8.1</span></span>

  - <span data-ttu-id="52b63-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="52b63-120">Windows Server 2016</span></span>

  - <span data-ttu-id="52b63-121">Windows Server 2012 或 Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="52b63-121">Windows Server 2012 or Windows Server 2012 R2</span></span>

  - <span data-ttu-id="52b63-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="52b63-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span></span>

  - <span data-ttu-id="52b63-123">Windows Server 2008 R2 SP1<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="52b63-123">Windows Server 2008 R2 SP1<sup>\*</sup></span></span>

    <span data-ttu-id="52b63-p105"><sup>\*</sup>对于 Windows 的早期版本，需要安装 Microsoft.NET Framework 4.5 或更高版本，然后安装 Windows Management Framework 的更新版本：3.0、4.0 或 5.1（其中一个）。有关详细信息，请参阅[安装 .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)、[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)、[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344) 和 [Windows Management Framework 5.1](https://aka.ms/wmf5download)。</span><span class="sxs-lookup"><span data-stu-id="52b63-p105"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one). For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span></span>

- <span data-ttu-id="52b63-p106">Windows PowerShell 需要进行相关配置，才能运行脚本。默认情况下，它并没有进行配置。你会在尝试连接时看到以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="52b63-p106">Windows PowerShell needs to be configured to run scripts, and by default, it isn't. You'll get the following error when you try to connect:</span></span>

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  <span data-ttu-id="52b63-128">为了使从 Internet 下载的所有 PowerShell 脚本能够由受信任的发布者签名，请在提升的 Windows PowerShell 窗口（通过选择“以管理员身份运行”\*\*\*\* 打开的 Windows PowerShell 窗口）中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="52b63-128">To require all PowerShell scripts that you download from the internet are signed by a trusted publisher, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you open by selecting **Run as administrator**):</span></span>

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  <span data-ttu-id="52b63-129">只需在计算机上配置一次此设置，无需每次连接时都进行配置。</span><span class="sxs-lookup"><span data-stu-id="52b63-129">You need to configure this setting only once on your computer, not every time you connect.</span></span>

- <span data-ttu-id="52b63-130">有关可能适用于本主题中的过程的键盘快捷键的信息，请参阅 [Exchange 管理中心内的键盘快捷键](https://go.microsoft.com/fwlink/p/?LinkId=534017)。</span><span class="sxs-lookup"><span data-stu-id="52b63-130">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>

## <a name="connect-to-exchange-online-for-customer-organizations"></a><span data-ttu-id="52b63-131">连接到客户组织的 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="52b63-131">Connect to Exchange Online for customer organizations</span></span>

1. <span data-ttu-id="52b63-132">在本地计算机上，打开 Windows PowerShell 并运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="52b63-132">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```

    <span data-ttu-id="52b63-133">在“Windows PowerShell 凭据请求”\*\*\*\* 对话框中，输入你的 DAP 管理员用户名和密码，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="52b63-133">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="52b63-134">将替换为 _\<customer tenant domain name\>_ 您要连接到的租户域的名称，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="52b63-134">Replace _\<customer tenant domain name\>_ with the name of the tenant domain that you want to connect to, and run the following command:</span></span>
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    <span data-ttu-id="52b63-135">此命令中的关键步骤指定哪个客户可访问报告的信息。</span><span class="sxs-lookup"><span data-stu-id="52b63-135">The key step in this command is specifying which customer to access for the reporting information.</span></span> <span data-ttu-id="52b63-136">在_ConnectionURI_参数中执行此操作，可在其中提供作为的值的初始域名的 FQDN `?DelegatedOrg=` 。</span><span class="sxs-lookup"><span data-stu-id="52b63-136">You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value for `?DelegatedOrg=`.</span></span> <span data-ttu-id="52b63-137">此值指示要连接到的正确 Exchange Online PowerShell 终结点。</span><span class="sxs-lookup"><span data-stu-id="52b63-137">This value indicates the correct Exchange Online PowerShell endpoint to connect to.</span></span> <span data-ttu-id="52b63-138">每次运行报告时，远程 PowerShell 必须连接到特定客户的上下文中的 Microsoft 365 报告。</span><span class="sxs-lookup"><span data-stu-id="52b63-138">Remote PowerShell must connect to Microsoft 365 reporting in the context of a specific customer each time a report is run.</span></span> <span data-ttu-id="52b63-139">在连接到 Exchange Online PowerShell 之后，所有随后的命令都将在客户的上下文中运行，从而使您可以访问客户的所有可用报告。</span><span class="sxs-lookup"><span data-stu-id="52b63-139">After you connect to Exchange Online PowerShell, all subsequent commands are run in the context of the customer, which gives you access to all of the available reports for the customer.</span></span>
    
3. <span data-ttu-id="52b63-140">运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="52b63-140">Run the following command.</span></span>
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> <span data-ttu-id="52b63-p108">一个帐户下具有可运行三个并发会话的限制。完成后务必断开与远程 PowerShell 会话的连接。如果在不断开会话连接的情况下关闭 PowerShell 窗口，你可能会用完可用的所有远程 PowerShell 会话，然后你需要等待这些会话过期。若要断开远程 PowerShell 会话连接，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="52b63-p108">There's a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote PowerShell session, run the following command:</span></span>

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="52b63-145">如何知道操作成功？</span><span class="sxs-lookup"><span data-stu-id="52b63-145">How do you know this worked?</span></span>

<span data-ttu-id="52b63-p109">执行步骤 3 后，Exchange Online cmdlet 将导入到你的本地 Windows PowerShell 会话，此时会显示一个进度条以便于跟踪。如果未收到任何错误，则说明连接成功。一个快速测试是运行 Exchange Online cmdlet（例如 **Get-Mailbox**），然后查看结果。</span><span class="sxs-lookup"><span data-stu-id="52b63-p109">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span></span>
  
<span data-ttu-id="52b63-149">如果收到错误，则查看以下要求：</span><span class="sxs-lookup"><span data-stu-id="52b63-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="52b63-p110">常见问题是密码错误。重新运行上述三个步骤，并仔细查看在步骤 1 中输入的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="52b63-p110">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="52b63-p111">必须为远程 PowerShell 启用用于连接到 Exchange Online 的帐户。有关详细信息，请参阅[启用或禁用对 Exchange Online PowerShell 的访问](https://go.microsoft.com/fwlink/p/?LinkId=534018)。</span><span class="sxs-lookup"><span data-stu-id="52b63-p111">The account you use to connect to Exchange Online must be enabled for remote PowerShell. For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="52b63-p112">需要打开本地计算机和 Exchange Online 之间的 TCP 端口 80 通信。它可能已经打开了，但是要考虑您的组织是否存在严格的 Internet 访问政策。</span><span class="sxs-lookup"><span data-stu-id="52b63-p112">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="52b63-156">直接使用 Invoke-Command 调用 cmdlet</span><span class="sxs-lookup"><span data-stu-id="52b63-156">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="52b63-p113">导入远程 PowerShell 会话（步骤 3）可能需要很长时间，因为它会引入_所有_ Exchange Online cmdlet。这可能会导致在进行批处理时出现问题（例如，当你运行报告或对不同租户进行批量更改时）。除了使用 **Import-PSSession** 之外，你可以直接使用 **Invoke-Command** 调用你想使用的 cmdlet。例如，要调用 **Get-Milbox** cmdlet，请替换步骤 3 中的 `Import-PSSession $Session` 命令的此语法：</span><span class="sxs-lookup"><span data-stu-id="52b63-p113">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets. This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants). As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="52b63-161">更多报告 cmdlet</span><span class="sxs-lookup"><span data-stu-id="52b63-161">More reporting cmdlets</span></span>

<span data-ttu-id="52b63-p114">您在本主题中使用的 cmdlet 是 Windows PowerShell cmdlet。有关这些 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="52b63-p114">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="52b63-164">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="52b63-164">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="52b63-165">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="52b63-165">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="52b63-166">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="52b63-166">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="52b63-167">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="52b63-167">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="52b63-168">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="52b63-168">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

