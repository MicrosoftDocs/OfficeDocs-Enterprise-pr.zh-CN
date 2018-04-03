---
title: 通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 摘要：使用 DelegatedOrg 参数，通过远程 Windows PowerShell 连接到 Exchange Online。
ms.openlocfilehash: d8cbb6640419ba2f1de868ae88b0a273c3f71ae7
ms.sourcegitcommit: f3f81d2c2e8290948d93f3f787a679c804840256
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2018
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="70d0b-103">通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户</span><span class="sxs-lookup"><span data-stu-id="70d0b-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="70d0b-104">**摘要：**使用 _DelegatedOrg_ 参数，通过远程 Windows PowerShell 连接到 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="70d0b-104">**Summary:** Use remote Windows PowerShell to connect to Exchange Online by using the _DelegatedOrg_ parameter.</span></span>
  
<span data-ttu-id="70d0b-p101">远程 Windows PowerShell 允许您从命令行管理您的 Exchange Online 设置。您在本地计算机上使用 Windows PowerShell 创建到 Exchange Online 的远程会话。这个过程只需三个步骤：输入 Exchange Online 凭据，提供所需的连接设置，然后将 Exchange Online cmdlet 导入到本地 Windows PowerShell 会话以便您可以使用。</span><span class="sxs-lookup"><span data-stu-id="70d0b-p101">Remote Windows PowerShell lets you manage your Exchange Online settings from the command line. You use Windows PowerShell on your local computer to create a remote session to Exchange Online. It's a three-step process where you enter your Exchange Online credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="70d0b-108">在开始之前，您需要知道什么？</span><span class="sxs-lookup"><span data-stu-id="70d0b-108">What do you need to know before you begin?</span></span>

- <span data-ttu-id="70d0b-109">估计完成时间：5 分钟</span><span class="sxs-lookup"><span data-stu-id="70d0b-109">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="70d0b-110">可以使用下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="70d0b-110">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="70d0b-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="70d0b-111">Windows 10</span></span>
    
  - <span data-ttu-id="70d0b-112">Windows 8.1 或 Windows 8</span><span class="sxs-lookup"><span data-stu-id="70d0b-112">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="70d0b-113">Windows Server 2012 R2 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="70d0b-113">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="70d0b-114">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="70d0b-114">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="70d0b-115">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="70d0b-115">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="70d0b-p102">\* 需要先安装 .NET Framework 4.5.1 或 4.5，再安装 Windows Management Framework 4.0 或 3.0。有关详细信息，请参阅以下资源：</span><span class="sxs-lookup"><span data-stu-id="70d0b-p102">\*You need to install the .NET Framework 4.5.1 or the .NET Framework 4.5 and then either the Windows Management Framework 4.0 or the Windows Management Framework 3.0 . For more information, see the following resources:</span></span>
    
    - [<span data-ttu-id="70d0b-118">安装 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="70d0b-118">Installing the .NET Framework</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
    - <span data-ttu-id="70d0b-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 或 [4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span><span class="sxs-lookup"><span data-stu-id="70d0b-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span></span>
    
- <span data-ttu-id="70d0b-120">有关可能适用于本主题中的过程的键盘快捷键的信息，请参阅 [Exchange 管理中心内的键盘快捷键](https://go.microsoft.com/fwlink/p/?LinkId=534017)。</span><span class="sxs-lookup"><span data-stu-id="70d0b-120">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>
    
## 

> [!IMPORTANT]
> <span data-ttu-id="70d0b-p103">此过程仅适用于委派访问权限 (DAP) 合作伙伴。如果您不是 DAP 合作伙伴，请勿使用此过程。</span><span class="sxs-lookup"><span data-stu-id="70d0b-p103">This procedure is only for Delegated Access Permission (DAP) partners. If you are not a DAP partner, do not use this procedure.</span></span> 
  
<span data-ttu-id="70d0b-p104">DAP 合作伙伴是整合和云解决方案提供商 (CSP) 合作伙伴。它们通常是面向其他公司的网络或电信提供程序。它们将订阅捆绑到为其客户提供的服务产品中。其拥有的合作伙伴租赁是对其 Office 365客户租赁自动授予的代表以下方管理 (AOBO) 权限，以便能够对其所有的客户租赁进行管理和报告。</span><span class="sxs-lookup"><span data-stu-id="70d0b-p104">DAP partners are Syndication and Cloud Solution Providers (CSP) partners. They are frequently network or telecom providers to other companies. They bundle subscriptions into their service offerings to their customers. They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Office 365customer tenancies so they can administer and report on all of their customer tenancies.</span></span>
  
## <a name="connect-to-exchange-online"></a><span data-ttu-id="70d0b-127">连接到 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="70d0b-127">Connect to Exchange Online</span></span>

1. <span data-ttu-id="70d0b-128">在本地计算机上，打开 Windows PowerShell 并运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="70d0b-128">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
  ```
  $UserCredential = Get-Credential
  ```

    <span data-ttu-id="70d0b-129">在"Windows PowerShell 凭据请求"窗口中，输入您的 DAP 管理员用户名和密码，然后单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="70d0b-129">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="70d0b-130">运行以下命令，将 _<customer tenant domain name>_ 替换为要连接到的租户域的域名。</span><span class="sxs-lookup"><span data-stu-id="70d0b-130">Run the following command, replacing  _<customer tenant domain name>_ with the name of the tenant domain that you want to connect to.</span></span>
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    <span data-ttu-id="70d0b-p105">此命令中的关键步骤指定哪个客户可访问报告的信息。您可在  _ConnectionURI_ 参数中执行此操作，其中，您可提供初始域名的 FQDN 作为 _DelegatedOrg_ 参数的值。这会告知远程 Windows PowerShell，对于 Exchange Online PowerShell，终结点要连接到的远程 Windows PowerShell。在每次运行报告时特定客户的上下文中，远程 Windows PowerShell 必须连接到 Office 365 报告。指定此客户后，以下所有命令都将在该客户的上下文中运行。这样，合作伙伴即可访问此客户的所有可用报告。</span><span class="sxs-lookup"><span data-stu-id="70d0b-p105">The key step in this command is specifying which customer to access for the reporting information. You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value to the _DelegatedOrg_ parameter. This tells remote Windows PowerShell for Exchange Online PowerShell remote Windows PowerShell the endpoint to connect to. remote Windows PowerShell must connect to Office 365 reporting in the context of a specific customer each time a report is run. After this customer is specified, all of the following commands are run in the context of that customer. This lets the partner to access all the available reports for this customer.</span></span>
    
3. <span data-ttu-id="70d0b-137">运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="70d0b-137">Run the following command.</span></span>
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> <span data-ttu-id="70d0b-p106">一个帐户下限制可运行三个并发会话。完成后务必断开与远程 Windows PowerShell 会话的连接。如果在不断开会话连接的情况下关闭 Windows PowerShell 窗口，您可能会用完可用的所有远程 Windows PowerShell 会话，然后您需要等待这些会话过期。若要断开远程 Windows PowerShell 会话连接，请运行以下命令。 >  `Remove-PSSession $Session`</span><span class="sxs-lookup"><span data-stu-id="70d0b-p106">There is a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote Windows PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote Windows PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote Windows PowerShell session, run the following command. >  `Remove-PSSession $Session`</span></span>
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="70d0b-142">您如何知道这有效？</span><span class="sxs-lookup"><span data-stu-id="70d0b-142">How do you know this worked?</span></span>

<span data-ttu-id="70d0b-p107">执行步骤 3 后，Exchange Online cmdlet 将导入到您的本地 Windows PowerShell 会话，此时会显示一个进度条以便于跟踪。如果未收到任何错误，则说明连接成功。一个快速测试是运行 Exchange Online cmdlet（例如 **Get-Mailbox** ），然后查看结果。</span><span class="sxs-lookup"><span data-stu-id="70d0b-p107">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="70d0b-146">如果收到错误，则查看以下要求：</span><span class="sxs-lookup"><span data-stu-id="70d0b-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="70d0b-p108">常见问题是密码错误。重新运行上述三个步骤，并仔细查看在步骤 1 中输入的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="70d0b-p108">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="70d0b-149">为了帮助防止受到拒绝服务 (DoS) 攻击，您最多只能打开三个与 Exchange Online 组织的远程 Windows PowerShell 连接。</span><span class="sxs-lookup"><span data-stu-id="70d0b-149">To help prevent denial-of-service (DoS) attacks, you're limited to three open remote Windows PowerShell connections to your Exchange Online organization.</span></span>
    
- <span data-ttu-id="70d0b-p109">Windows PowerShell 需要进行相关配置，以运行脚本。只需在计算机上配置一次此设置即可，无需每次连接时都进行配置。为了使 Windows PowerShell 能够运行已签名脚本，请在提升的 Windows PowerShell 窗口（通过选择"以管理员身份运行"打开的 Windows PowerShell 窗口）中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="70d0b-p109">Windows PowerShell needs to be configured to run scripts. You need to configure this setting only once on your computer, not every time you connect. To enable Windows PowerShell to run signed scripts, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you opened by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- <span data-ttu-id="70d0b-p110">必须为远程 Windows PowerShell 启用用于连接到 Exchange Online 的帐户。有关详细信息，请参阅[在 Exchange Online 中管理远程 PowerShell 访问](https://go.microsoft.com/fwlink/p/?LinkId=534018)。</span><span class="sxs-lookup"><span data-stu-id="70d0b-p110">The account you use to connect to Exchange Online must be enabled for remote Windows PowerShell. For more information, see [Manage Remote PowerShell Access in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="70d0b-p111">需要打开本地计算机和 Exchange Online 之间的 TCP 端口 80 通信。它可能已经打开了，但是要考虑您的组织是否存在严格的 Internet 访问政策。</span><span class="sxs-lookup"><span data-stu-id="70d0b-p111">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="70d0b-157">直接使用 Invoke-Command 调用 cmdlet</span><span class="sxs-lookup"><span data-stu-id="70d0b-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="70d0b-p112">导入远程 Windows PowerShell 会话可能需要很长时间，因为它会引入所有 Exchange Online cmdlet。这可能会导致在进行批处理时出现问题  例如，当您运行报告或对不同租户进行批量更改时。除了使用 **Import-PSSession** 之外，您可以直接使用 **Invoke-Command** 调用您想使用的 cmdlet。例如，要调用 **get-mailbox** cmdlet，请替换 `Import-PSSession $Session` 的此语法。</span><span class="sxs-lookup"><span data-stu-id="70d0b-p112">Importing a remote Windows PowerShell session can be a lengthy process because it brings in all Exchange Online cmdlets. This can be an issue in batch processing—for example, when you are running reports or making bulk changes for different tenants. As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **get-mailbox** cmdlet, substitute this syntax for `Import-PSSession $Session`.</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="70d0b-162">更多报告 cmdlet</span><span class="sxs-lookup"><span data-stu-id="70d0b-162">More reporting cmdlets</span></span>

<span data-ttu-id="70d0b-p113">您在本主题中使用的 cmdlet 是 Windows PowerShell cmdlet。有关这些 cmdlet 的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="70d0b-p113">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="70d0b-165">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="70d0b-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="70d0b-166">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="70d0b-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="70d0b-167">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="70d0b-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="70d0b-168">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="70d0b-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="70d0b-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="70d0b-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

