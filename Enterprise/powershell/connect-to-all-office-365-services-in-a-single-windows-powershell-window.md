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
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>在单个 Windows PowerShell 窗口中连接所有 Office 365 服务

 **摘要：**而不是管理不同的 Office 365 服务单独 PowerShell 控制台窗口中，可以连接到所有的 Office 365 提供服务并从单个控制台窗口中对它们进行管理。
  
当使用 PowerShell Office 365 管理时，很可能有最多五个不同的 Windows PowerShell 会话打开对应于 Office 365 管理中心、 SharePoint Online、 Exchange Online，Skype 的在线业务和&amp;符合性中心。在单独的 Windows PowerShell 会话中的五种不同的连接方法，与您的桌面可以如下所示：
  
![五个同时运行的 Windows PowerShell 控制台](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
这不是最适合于管理 Office 365，因为不能交换跨服务管理这些五个窗口间的数据。本主题介绍如何使用与管理 Office 365、 为业务联机状态，Exchange Online，SharePoint Online，Skype 和安全的 Windows PowerShell 的单个实例&amp;法规遵从性中心。

>[!Note]
>本文是在过程中被更新，以使用 Azure 活动目录 V2 PowerShell 模块并进行多因素身份验证 (MFA)。
>
  
## <a name="before-you-begin"></a>开始之前
<a name="BeforeYouBegin"> </a>

您可以从 Windows PowerShell 的单个实例中管理所有 Office 365 的之前，请考虑以下先决条件：
  
- Office 365 的工作或学校对使用这些过程需要 Office 365 管理角色的成员的帐户。有关详细信息，请参阅[有关 Office 365 管理角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。此 Office 365 PowerShell，不一定能为所有其他 Office 365 提供服务的要求。
    
- 您可以使用以下 64 位版本的 Windows：
    
  - Windows 10
    
  - Windows 8.1 或 Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 或 Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * 您需要安装 Microsoft.net 4.5。*x* ，然后是 Windows 管理框架 3.0 或 Windows 管理框架 4.0。有关详细信息，请参阅[安装.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[Windows 管理框架 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[Windows 管理框架 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。
    
    您需要使用 64 位版本的 Windows 由于 Skype 的要求在线业务模块和 Office 365 模块之一。
    
- 您需要安装所需的 Office 365、 SharePoint Online 和 Skype 的在线业务的模块：
    
   - [Microsoft 在线服务登录助理为 IT 专业人士一项的](https://go.microsoft.com/fwlink/p/?LinkId=286152)
   - Windows Azure 活动目录模块用于 Windows PowerShell （64-位版本） 用在提升 PowerShell 命令提示符**安装模块 MSOnline**命令。
   - [SharePoint 在线管理外壳程序](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype 的在线业务 Windows PowerShell 模块](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell 需要配置运行 Skype 在线业务、 在线交换和安全签名的脚本&amp;法规遵从性中心。若要执行此操作，在提升的权限的 Windows PowerShell 会话中运行以下命令 （您选择**以管理员身份运行**，打开 Windows PowerShell 窗口）。
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps"></a>连接的步骤
<a name="BeforeYouBegin"> </a>

这里是连接到一个 PowerShell 窗口中的所有服务的步骤。
  
1. 以管理员身份 （使用**以管理员身份运行**） 打开 Windows PowerShell。
    
2. 运行此命令，并输入您的 Office 365 提供工作或学校帐户凭据。
    
  ```
  $credential = Get-Credential
  ```

3. 运行以下命令以连接到 Office 365。
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. 运行以下命令以连接到 SharePoint Online。更换_\<domainhost >_与实际值为您的域。例如，对于`litwareinc.onmicrosoft.com`， _ \<domainhost >_值是`litwareinc`。
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. 运行以下命令以连接到 Skype 的在线业务。有关增加警告`WSMan NetworkDelayms`的值应在第一次连接，可以忽略。
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. 运行以下命令以连接到 Exchange 联机。
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. 运行以下命令以对安全连接&amp;法规遵从性中心。
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> "抄送"中的文本前缀添加到*所有*安全&amp;法规遵从性中心 cmdlet 名称以便您可以运行的 cmdlet，存在于 Exchange 联机和安全&amp;同一 Windows PowerShell 会话中的法规遵从性中心。例如， **Get RoleGroup**将成为安全**获取 ccRoleGroup** &amp;法规遵从性中心。
  
下面是在一个块的所有命令。指定您的域主机的名称，然后一次运行所有这些。
  
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
准备就绪以关闭 Windows PowerShell 窗口后，运行以下命令来删除联机业务、 Exchange Online，SharePoint Online，和安全到 Skype 的活动会话&amp;法规遵从性中心：
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="new-to-office-365"></a>刚开始接触 Office 365？
<a name="LongVersion"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>另请参阅

- [使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理 SharePoint Online](manage-sharepoint-online-with-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理用户帐户和许可证](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [使用 Windows PowerShell 在 Office 365 中创建报告](use-windows-powershell-to-create-reports-in-office-365.md)
