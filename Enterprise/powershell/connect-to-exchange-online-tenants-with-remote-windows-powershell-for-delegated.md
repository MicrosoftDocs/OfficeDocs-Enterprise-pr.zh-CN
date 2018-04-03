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
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户

 **摘要：**使用 _DelegatedOrg_ 参数，通过远程 Windows PowerShell 连接到 Exchange Online。
  
远程 Windows PowerShell 允许您从命令行管理您的 Exchange Online 设置。您在本地计算机上使用 Windows PowerShell 创建到 Exchange Online 的远程会话。这个过程只需三个步骤：输入 Exchange Online 凭据，提供所需的连接设置，然后将 Exchange Online cmdlet 导入到本地 Windows PowerShell 会话以便您可以使用。
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>在开始之前，您需要知道什么？

- 估计完成时间：5 分钟
    
- 可以使用下列 Windows 版本：
    
  - Windows 10
    
  - Windows 8.1 或 Windows 8
    
  - Windows Server 2012 R2 或 Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \* 需要先安装 .NET Framework 4.5.1 或 4.5，再安装 Windows Management Framework 4.0 或 3.0。有关详细信息，请参阅以下资源：
    
    - [安装 .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
    - [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) 或 [4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)
    
- 有关可能适用于本主题中的过程的键盘快捷键的信息，请参阅 [Exchange 管理中心内的键盘快捷键](https://go.microsoft.com/fwlink/p/?LinkId=534017)。
    
## 

> [!IMPORTANT]
> 此过程仅适用于委派访问权限 (DAP) 合作伙伴。如果您不是 DAP 合作伙伴，请勿使用此过程。 
  
DAP 合作伙伴是整合和云解决方案提供商 (CSP) 合作伙伴。它们通常是面向其他公司的网络或电信提供程序。它们将订阅捆绑到为其客户提供的服务产品中。其拥有的合作伙伴租赁是对其 Office 365客户租赁自动授予的代表以下方管理 (AOBO) 权限，以便能够对其所有的客户租赁进行管理和报告。
  
## <a name="connect-to-exchange-online"></a>连接到 Exchange Online

1. 在本地计算机上，打开 Windows PowerShell 并运行以下命令。
    
  ```
  $UserCredential = Get-Credential
  ```

    在"Windows PowerShell 凭据请求"窗口中，输入您的 DAP 管理员用户名和密码，然后单击"确定"。
    
2. 运行以下命令，将 _<customer tenant domain name>_ 替换为要连接到的租户域的域名。
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    此命令中的关键步骤指定哪个客户可访问报告的信息。您可在  _ConnectionURI_ 参数中执行此操作，其中，您可提供初始域名的 FQDN 作为 _DelegatedOrg_ 参数的值。这会告知远程 Windows PowerShell，对于 Exchange Online PowerShell，终结点要连接到的远程 Windows PowerShell。在每次运行报告时特定客户的上下文中，远程 Windows PowerShell 必须连接到 Office 365 报告。指定此客户后，以下所有命令都将在该客户的上下文中运行。这样，合作伙伴即可访问此客户的所有可用报告。
    
3. 运行以下命令。
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> 一个帐户下限制可运行三个并发会话。完成后务必断开与远程 Windows PowerShell 会话的连接。如果在不断开会话连接的情况下关闭 Windows PowerShell 窗口，您可能会用完可用的所有远程 Windows PowerShell 会话，然后您需要等待这些会话过期。若要断开远程 Windows PowerShell 会话连接，请运行以下命令。 >  `Remove-PSSession $Session`
  
## <a name="how-do-you-know-this-worked"></a>您如何知道这有效？

执行步骤 3 后，Exchange Online cmdlet 将导入到您的本地 Windows PowerShell 会话，此时会显示一个进度条以便于跟踪。如果未收到任何错误，则说明连接成功。一个快速测试是运行 Exchange Online cmdlet（例如 **Get-Mailbox** ），然后查看结果。
  
如果收到错误，则查看以下要求：
  
- 常见问题是密码错误。重新运行上述三个步骤，并仔细查看在步骤 1 中输入的用户名和密码。
    
- 为了帮助防止受到拒绝服务 (DoS) 攻击，您最多只能打开三个与 Exchange Online 组织的远程 Windows PowerShell 连接。
    
- Windows PowerShell 需要进行相关配置，以运行脚本。只需在计算机上配置一次此设置即可，无需每次连接时都进行配置。为了使 Windows PowerShell 能够运行已签名脚本，请在提升的 Windows PowerShell 窗口（通过选择"以管理员身份运行"打开的 Windows PowerShell 窗口）中运行以下命令。
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- 必须为远程 Windows PowerShell 启用用于连接到 Exchange Online 的帐户。有关详细信息，请参阅[在 Exchange Online 中管理远程 PowerShell 访问](https://go.microsoft.com/fwlink/p/?LinkId=534018)。
    
- 需要打开本地计算机和 Exchange Online 之间的 TCP 端口 80 通信。它可能已经打开了，但是要考虑您的组织是否存在严格的 Internet 访问政策。
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>直接使用 Invoke-Command 调用 cmdlet

导入远程 Windows PowerShell 会话可能需要很长时间，因为它会引入所有 Exchange Online cmdlet。这可能会导致在进行批处理时出现问题  例如，当您运行报告或对不同租户进行批量更改时。除了使用 **Import-PSSession** 之外，您可以直接使用 **Invoke-Command** 调用您想使用的 cmdlet。例如，要调用 **get-mailbox** cmdlet，请替换 `Import-PSSession $Session` 的此语法。
  
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
    

