---
title: 在单个 Windows PowerShell 窗口中连接所有 Office 365 服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
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
description: '摘要: 将 windows powershell 连接到单个 Windows powershell 窗口中的所有 Office 365 服务。'
ms.openlocfilehash: 3f6153d5ea8b88d8c6853dbbe597f2cf7cc62fab
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573966"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>在单个 Windows PowerShell 窗口中连接所有 Office 365 服务

 **摘要:** 无需在单独的 PowerShell 控制台窗口中管理不同的 office 365 服务, 您可以连接到所有 Office 365 服务并从单个控制台窗口管理这些服务。
  
使用 PowerShell 管理 Office 365 时, 可以在与 Microsoft 365 管理中心、SharePoint online、Exchange online、Skype for business Online 和安全性相关的同时同时打开最长五个不同的 Windows PowerShell 会话&amp;合规性中心。 在单独的 Windows PowerShell 会话中有五种不同的连接方法, 你的桌面可能如下所示:
  
![五个同时运行的 Windows PowerShell 控制台](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
这对管理 Office 365 不是最佳的, 因为您无法在这五个 windows 之间交换跨服务管理的数据。 本主题介绍如何使用 Windows PowerShell 的单个实例, 可以从该实例管理 Office 365、Skype for business Online、Exchange online、SharePoint online 和安全&amp;合规性中心。

>[!Note]
>本文当前只包含连接到 Office 365 全球 (+ GCC) 云的命令。 其他说明提供了指向包含有关连接到其他 Office 365 云的信息的文章的链接。
>

## <a name="before-you-begin"></a>准备工作

在可以从 Windows PowerShell 的单个实例管理所有 Office 365 之前, 请考虑以下先决条件:
  
- 在这些步骤中使用的 Office 365工作或学校帐户 须为 Office 365 管理员角色的成员。 有关详细信息，请参阅[关于 Office 365 管理员角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。 这是 Office 365 PowerShell 的要求, 并不一定适用于所有其他 office 365 服务。
    
- 您可以使用以下 64 位版本的 Windows：
    
  - Windows 10
    
  - Windows 8.1 或 Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 或 Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*您需要安装 Microsoft .net Framework 4.5。*x* , 然后是 windows management framework 3.0 或 windows management framework 4.0。 有关详细信息, 请参阅[安装 .net Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[windows management framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[windows management framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。
    
    由于 Skype for business Online 模块和其中一个 Office 365 模块的要求, 您需要使用 Windows 的64位版本的 Windows。
    
- 您需要安装 Azure AD、SharePoint Online 和 Skype for business Online 所需的模块:
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online 命令行管理程序](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype for business Online、Windows PowerShell 模块](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  需要将 Windows PowerShell 配置为为 Skype for business Online、Exchange Online 和安全&amp;合规中心运行已签名的脚本。 若要执行此操作, 请在提升的 windows powershell 会话 (通过选择 "**以管理员身份运行**" 打开的 windows powershell 窗口) 中运行以下命令。
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>使用密码时的连接步骤

以下是在单个 PowerShell 窗口中连接到所有服务的步骤。
  
1. 以管理员身份打开 Windows PowerShell (使用 "**以管理员身份运行**")。
    
2. 运行此命令, 并输入 Office 365 的工作或学校帐户凭据。
    
  ```
  $credential = Get-Credential
  ```

3. 运行此命令以使用 azure active directory PowerShell for Graph 模块连接到 azure active directory (AD)。
    
  ```
  Connect-AzureAD -Credential $credential
  ```
  
  或者, 如果您使用的是 Windows PowerShell 模块的 Microsoft Azure Active Directory 模块, 请运行此命令。
      
  ```
  Connect-MsolService -Credential $credential
 ```

4. 运行这些命令以连接到 SharePoint Online。 将_ \<domainhost>_ 替换为您的域的实际值。 例如, 对于 "litwareinc.onmicrosoft.com", _ \<domainhost>_ 值为 "litwareinc"。
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. 运行这些命令以连接到 Skype for business Online。 第一次连接时`WSMan NetworkDelayms`需要增加值的警告, 应将其忽略。
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. 运行这些命令以连接到 Exchange Online。
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
>若要连接到除全球版之外的 Office 365 云的 Exchange online, 请参阅[连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。
>

7. 运行这些命令以连接到安全&amp;合规性中心。
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>若要连接到世界&amp;各地的 Office 365 云的安全合规中心, 请参阅[连接到 Office 365 Security & 合规中心 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)。
>

以下是在使用 Azure Active Directory PowerShell for Graph 模块时, 单个块中的所有命令。 指定您的域主机的名称, 然后一次运行所有域主机。
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

此外, 在使用适用于 Windows PowerShell 模块的 Microsoft Azure Active Directory 模块时, 以下是单个块中的所有命令。 指定您的域主机的名称, 然后一次运行所有域主机。
  
```
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

当您准备好关闭 Windows PowerShell 窗口时, 运行此命令以删除 Skype for business Online、Exchange online、SharePoint online 和安全&amp;合规性中心的活动会话:
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>使用多重身份验证时的连接步骤

下面是通过使用 azure Active Directory PowerShell for Graph 模块在单个窗口中使用多重身份验证在单个块中连接到 Azure AD、SharePoint Online 和 Skype for Buiness 的所有命令。 指定用户帐户的用户主体名称 (UPN) 名称和您的域主机名, 然后一次运行所有这些名称。

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

此外, 以下是使用适用于 Windows PowerShell 模块的 Microsoft Azure Active Directory 模块的所有命令。

````
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

对于 Exchange Online 和安全&amp;合规中心, 请参阅下列主题以使用多重身份验证进行连接:

- [使用多重身份验证连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [使用多重身份验证连接到 Office 365 Security & 合规中心 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
请注意, 在这两种情况下, 都必须使用 Exchange Online 远程 PowerShell 模块的单独会话进行连接。


## <a name="see-also"></a>另请参阅

- [连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理 SharePoint Online](manage-sharepoint-online-with-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [使用 Windows PowerShell 在 Office 365 中创建报告](use-windows-powershell-to-create-reports-in-office-365.md)
