---
title: 通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 摘要：使用 DelegatedOrg 值，通过远程 Windows PowerShell 连接到 Exchange Online。
ms.openlocfilehash: d14726a2983bf3f2d569305e1a7e2e1a86811ff5
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849898"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户

 **摘要：** 使用 `DelegatedOrg` 值，通过远程 PowerShell 连接到 Exchange Online。

> [!IMPORTANT]
> 本主题中的过程仅适用于委派访问权限 (DAP) 合作伙伴。如果你不是 DAP 合作伙伴，请不要使用此主题中的过程。 
  
DAP 合作伙伴是整合和云解决方案提供商 (CSP) 合作伙伴。它们通常是面向其他公司的网络或电信提供程序。它们将订阅捆绑到为其客户提供的服务产品中。其拥有的合作伙伴租赁是对其 Office 365 客户租赁自动授予的代表管理 (AOBO) 权限，以便能够对其所有的客户租赁进行管理和报告。

DAP 合作伙伴可以使用 Exchange Online PowerShell 来管理客户 Exchange Online 设置和从命令行中获取 Office 365 报告。可以使用本地计算机上的 Windows PowerShell 创建到 Exchange Online 的远程 PowerShell 会话。只需简单三个步骤：输入凭据、提供所需的连接设置，然后将 Exchange Online cmdlet 导入你的本地 Windows PowerShell 会话。接下来，就可以开始使用了。

> [!NOTE]
> DAP 合作伙伴无法使用[使用多重身份验证连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) 中的过程连接到其在 Exchange Online PowerShell 中的客户租户组织。MFA 和 Exchange Online 远程 PowerShell 模块无法使用委派身份验证。
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>开始前，有必要了解什么？

- 估计完成时间：5 分钟

- 可以使用下列 Windows 版本：
    
  - Windows 10

  - Windows 8.1

  - Windows Server 2016

  - Windows Server 2012 或 Windows Server 2012 R2

  - Windows 7 Service Pack 1 (SP1)<sup>*</sup>

  - Windows Server 2008 R2 SP1<sup>*</sup>

    <sup>*</sup>对于 Windows 的早期版本，需要安装 Microsoft.NET Framework 4.5 或更高版本，然后安装 Windows Management Framework 的更新版本：3.0、4.0 或 5.1（其中一个）。有关详细信息，请参阅[安装 .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)、[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)、[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344) 和 [Windows Management Framework 5.1](https://aka.ms/wmf5download)。

- Windows PowerShell 需要进行相关配置，才能运行脚本。默认情况下，它并没有进行配置。你会在尝试连接时看到以下错误消息：

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  为了使从 Internet 下载的所有 PowerShell 脚本能够由受信任的发布者签名，请在提升的 Windows PowerShell 窗口（通过选择“以管理员身份运行”**** 打开的 Windows PowerShell 窗口）中运行以下命令。

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  只需在计算机上配置一次此设置，无需每次连接时都进行配置。

- 有关可能适用于本主题中的过程的键盘快捷键的信息，请参阅 [Exchange 管理中心内的键盘快捷键](https://go.microsoft.com/fwlink/p/?LinkId=534017)。

## <a name="connect-to-exchange-online-for-customer-organizations"></a>连接到客户组织的 Exchange Online

1. 在本地计算机上，打开 Windows PowerShell 并运行以下命令。
    
    ```
    $UserCredential = Get-Credential
    ```

    在“Windows PowerShell 凭据请求”**** 对话框中，输入你的 DAP 管理员用户名和密码，然后单击“确定”****。
    
2. 将 _\<客户租户域名\>_ 替换为你想要连接到的租户域的名称，并运行以下命令：
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    此命令中的关键步骤指定哪个客户可访问报告的信息。你可在 _ConnectionURI_ 参数中执行此操作，其中，你可提供初始域名的 FQDN 作为 `?DelegatedOrg=` 的值。该值指示要连接到的正确的 Exchange Online PowerShell 终结点。在每次运行报告时的特定客户的上下文中，远程 PowerShell 必须连接到 Office 365 报告。连接到 Exchange Online PowerShell 后，以下所有命令都将在该客户的上下文中运行，使你能够访问此客户的所有可用报告。
    
3. 运行以下命令。
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> 一个帐户下具有可运行三个并发会话的限制。完成后务必断开与远程 PowerShell 会话的连接。如果在不断开会话连接的情况下关闭 PowerShell 窗口，你可能会用完可用的所有远程 PowerShell 会话，然后你需要等待这些会话过期。若要断开远程 PowerShell 会话连接，请运行以下命令：

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a>如何知道操作成功？

执行步骤 3 后，Exchange Online cmdlet 将导入到你的本地 Windows PowerShell 会话，此时会显示一个进度条以便于跟踪。如果未收到任何错误，则说明连接成功。一个快速测试是运行 Exchange Online cmdlet（例如 **Get-Mailbox**），然后查看结果。
  
如果收到错误，则查看以下要求：
  
- 常见问题是密码错误。重新运行上述三个步骤，并仔细查看在步骤 1 中输入的用户名和密码。
    
- 必须为远程 PowerShell 启用用于连接到 Exchange Online 的帐户。有关详细信息，请参阅[启用或禁用对 Exchange Online PowerShell 的访问](https://go.microsoft.com/fwlink/p/?LinkId=534018)。
    
- 需要打开本地计算机和 Exchange Online 之间的 TCP 端口 80 通信。它可能已经打开了，但是要考虑您的组织是否存在严格的 Internet 访问政策。
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>直接使用 Invoke-Command 调用 cmdlet

导入远程 PowerShell 会话（步骤 3）可能需要很长时间，因为它会引入_所有_ Exchange Online cmdlet。这可能会导致在进行批处理时出现问题（例如，当你运行报告或对不同租户进行批量更改时）。除了使用 **Import-PSSession** 之外，你可以直接使用 **Invoke-Command** 调用你想使用的 cmdlet。例如，要调用 **Get-Milbox** cmdlet，请替换步骤 3 中的 `Import-PSSession $Session` 命令的此语法：
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>更多报告 cmdlet

您在本主题中使用的 cmdlet 是 Windows PowerShell cmdlet。有关这些 cmdlet 的详细信息，请参阅下列主题：
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

