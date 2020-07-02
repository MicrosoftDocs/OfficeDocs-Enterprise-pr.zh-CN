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
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户

> [!IMPORTANT]
> The procedures in this topic are only for Delegated Access Permission (DAP) partners. If you aren't a DAP partner, don't use the procedures in this topic. 
  
DAP 合作伙伴是整合和云解决方案提供商 (CSP) 合作伙伴。 它们通常是面向其他公司的网络或电信提供程序。 它们将订阅捆绑到为其客户提供的服务产品中。 他们拥有将代表（AOBO）权限自动授予给其 Microsoft 365 客户租赁的 "管理" 的合作伙伴租赁，以便他们可以管理和报告其所有客户租赁。

建立合作伙伴可以使用 Exchange Online PowerShell 管理客户 Exchange Online 设置，并从命令行获取 Microsoft 365 报告。 可以使用本地计算机上的 Windows PowerShell 创建到 Exchange Online 的远程 PowerShell 会话。 这是一个简单的三步骤过程，可在其中输入凭据、提供所需的连接设置，然后将 Exchange Online cmdlet 导入到您的本地 Windows PowerShell 会话中，以便您可以使用它们。

> [!NOTE]
> DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell. MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>开始前，有必要了解什么？

- 估计完成时间：5 分钟

- 可以使用下列 Windows 版本：
    
  - Windows 10

  - Windows 8.1

  - Windows Server 2016

  - Windows Server 2012 或 Windows Server 2012 R2

  - Windows 7 Service Pack 1 (SP1)<sup>*</sup>

  - Windows Server 2008 R2 SP1<sup>*</sup>

    <sup>*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one). For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).

- Windows PowerShell needs to be configured to run scripts, and by default, it isn't. You'll get the following error when you try to connect:

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
    
2. 将替换为 _\<customer tenant domain name\>_ 您要连接到的租户域的名称，然后运行以下命令：
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    此命令中的关键步骤指定哪个客户可访问报告的信息。 在_ConnectionURI_参数中执行此操作，可在其中提供作为的值的初始域名的 FQDN `?DelegatedOrg=` 。 此值指示要连接到的正确 Exchange Online PowerShell 终结点。 每次运行报告时，远程 PowerShell 必须连接到特定客户的上下文中的 Microsoft 365 报告。 在连接到 Exchange Online PowerShell 之后，所有随后的命令都将在客户的上下文中运行，从而使您可以访问客户的所有可用报告。
    
3. 运行以下命令。
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> There's a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote PowerShell session, run the following command:

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a>如何知道操作成功？

After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.
  
如果收到错误，则查看以下要求：
  
- A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.
    
- The account you use to connect to Exchange Online must be enabled for remote PowerShell. For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).
    
- TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>直接使用 Invoke-Command 调用 cmdlet

Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets. This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants). As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>更多报告 cmdlet

The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

