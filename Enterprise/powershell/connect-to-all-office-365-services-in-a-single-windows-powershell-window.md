---
title: 在单个 Windows PowerShell 窗口中连接所有 Office 365 服务
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/11/2018
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
description: 摘要： 将 Windows PowerShell 连接到单个 Windows PowerShell 窗口中的所有 Office 365 服务。
ms.openlocfilehash: b4d7b163bfba433196f46046030078c5559c4459
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915827"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>在单个 Windows PowerShell 窗口中连接所有 Office 365 服务

 **摘要：** 而不是管理在单独的 PowerShell 控制台窗口中的不同 Office 365 服务，您可以连接到所有 Office 365 服务，并从单个控制台窗口管理它们。
  
使用 PowerShell 管理 Office 365，时，可能需要与 Office 365 管理中心、 SharePoint Online、 Exchange Online、 Skype online 业务和安全&amp;合规性中心。使用单独的 Windows PowerShell 会话中的五个不同的连接方法，您的桌面无法如下所示：
  
![五个同时运行的 Windows PowerShell 控制台](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
这不是最佳用于管理 Office 365，因为您不能跨服务管理这些五个窗口之间进行数据交换。本主题介绍如何使用 Windows PowerShell 从其管理 Office 365、 业务联机状态，Exchange Online 中，SharePoint online，Skype 和安全性的单个实例&amp;合规性中心。

## <a name="before-you-begin"></a>准备工作

您可以从 Windows PowerShell 的单个实例来管理所有 Office 365 之前，请考虑以下先决条件：
  
- Office 365 工作或学校了用于这些过程需要为 Office 365 管理员角色的成员的帐户。有关详细信息，请参阅[有关 Office 365 管理员角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。此 Office 365 PowerShell 中，不一定是所有其他 Office 365 服务的要求。
    
- 您可以使用以下 64 位版本的 Windows：
    
  - Windows 10
    
  - Windows 8.1 或 Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 或 Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*您需要安装 Microsoft.NET Framework 4.5。*x* ，然后任一 Windows Management Framework 3.0 或 Windows Management Framework 4.0。有关详细信息，请参阅[安装.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。
    
    您需要业务 Online 模块和 Office 365 模块之一由于 Skype 的要求使用 64 位版本的 Windows。
    
- 您需要安装所需的 Azure AD 模块 SharePoint Online 和 Skype 业务 online:
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online 命令行管理程序](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype for Business 联机 Windows PowerShell 模块](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell 需要配置的业务 Online、 Exchange Online 和安全的 Skype 运行签名的脚本&amp;合规性中心。若要执行此操作，在提升的 Windows PowerShell 会话中运行以下命令 （通过选择**运行以管理员身份**打开 Windows PowerShell 窗口）。
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>使用密码时的连接步骤

下面是连接到单个 PowerShell 窗口中的所有服务的步骤。
  
1. 以管理员身份 （使用**以管理员身份运行**） 打开 Windows PowerShell。
    
2. 运行此命令，并输入您的 Office 365 工作或学校帐户凭据。
    
  ```
  $credential = Get-Credential
  ```

3. 运行此命令可连接到 Azure Active Directory (AD) 使用 Azure Active Directory PowerShell 图模块。
    
  ```
   Connect-AzureAD -Credential $credential
  ```
  
  另外，如果您正在使用 Microsoft Azure Active Directory 模块用于 Windows PowerShell 模块，则运行此命令。
      
  ```
   Connect-MsolService -Credential $credential
 ```

4. 运行以下命令以连接到 SharePoint Online。替换_\<domainhost >_ 与您的域的实际值。例如，对于"litwareinc.onmicrosoft.com" _ \<domainhost >_ 值是"litwareinc"。
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. 运行以下命令以连接到 Skype 业务 online。有关增加一条警告`WSMan NetworkDelayms`值应首次连接，并应忽略。
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. 运行以下命令以连接到 Exchange Online。
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. 运行以下命令以连接到安全性&amp;合规性中心。
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

以下在一个块是所有命令时使用 Azure Active Directory PowerShell 图模块。指定您的域主机的名称，然后一次运行所有这些。
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

另外，以下是所有命令在一个块时使用的 Microsoft Azure Active Directory 模块用于 Windows PowerShell 模块。指定您的域主机的名称，然后一次运行所有这些。
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

当您准备要关闭 Windows PowerShell 窗口时，运行此命令可删除到 Skype 活动会话业务 Online、 Exchange Online、 SharePoint Online 和安全性的&amp;合规性中心：
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>使用多因素身份验证时的连接步骤

下面是在一个块来连接到 Azure AD 的所有命令 SharePoint Online 和 Skype 的 Buiness 单个窗口中使用多因素身份验证。指定全局管理员帐户的用户主体名称 (UPN) 名称和域主机名，然后再一次运行所有这些。

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

另外，以下是出现使用 Microsoft Azure Active Directory 模块用于 Windows PowerShell 模块的所有命令。

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Exchange Online 和安全&amp;合规性中心，请参阅使用多因素身份验证进行连接的以下主题：

- [使用多重身份验证连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [连接到 Office 365 安全性和合规性中心 PowerShell 使用多因素身份验证](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
请注意，在两种情况下，必须使用单独的 Exchange Online 远程 PowerShell 模块会话进行连接。


## <a name="see-also"></a>另请参阅

- [连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理 SharePoint Online](manage-sharepoint-online-with-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [使用 Windows PowerShell 在 Office 365 中创建报告](use-windows-powershell-to-create-reports-in-office-365.md)
