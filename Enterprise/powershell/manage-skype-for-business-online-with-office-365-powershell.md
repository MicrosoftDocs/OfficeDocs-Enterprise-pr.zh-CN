---
title: 使用 Office 365 PowerShell 管理 Skype for Business Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要：使用 Office 365 PowerShell 管理 Skype for Business Online 策略、每用户策略和会议设置。
ms.openlocfilehash: 33c7247686cc8eb308b8db6d4900c89f693004fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068728"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>使用 Office 365 PowerShell 管理 Skype for Business Online

 **摘要：** 使用 Office 365 PowerShell 管理 Skype for Business Online 策略、每用户策略和会议设置。
  
Skype for Business Online 管理员的一项主要任务就是管理策略。 虽然您可以在 Office 365 管理中心中完成其中一些任务, 但在 Office 365 PowerShell 中, 其他任务的速度更快、更轻松。 

## <a name="before-you-start"></a>准备工作

下载并安装[Skype For Business Online 连接器模块](https://www.microsoft.com/en-us/download/details.aspx?id=39366), 然后在出现提示时重新启动计算机。


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>使用 Skype for Business Online 管理员帐户名称和密码进行连接

1. 打开 Windows PowerShell 命令提示符, 并运行以下命令: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. 在 " **Windows PowerShell 凭据请求**" 对话框中, 键入您的 Skype For business Online 管理员帐户名称和密码, 然后单击 **"确定"**。


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>使用具有多重身份验证的 Skype for Business Online 管理员帐户进行连接

1. 打开 Windows PowerShell 命令提示符, 并运行以下命令:

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. 当**CsOnlineSession**命令出现提示时, 请输入你的 Skype For business Online 管理员帐户名称。

3. 在 "**登录帐户**" 对话框中, 键入您的 Skype For business Online 管理员密码, 然后单击 "**登录**"。

4. 按照 "**登录到帐户**" 对话框中的说明提供其他身份验证信息 (如验证码), 然后单击 "**验证**"。

有关详细信息，请参阅下列主题：
  
- [管理 Skype 与 Office 365 PowerShell 的在线业务策略](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [指定每个用户 Skype 的在线商业策略与 Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

[Skype for Business PowerShell cmdlet 参考](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

