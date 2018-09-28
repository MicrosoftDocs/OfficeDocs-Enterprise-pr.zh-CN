---
title: 使用 Office 365 PowerShell 管理 Skype for Business Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要：使用 Office 365 PowerShell 管理 Skype for Business Online 策略、每用户策略和会议设置。
ms.openlocfilehash: a91803316972337aa31e2b979f841ac1cfbe8566
ms.sourcegitcommit: 053db5479f93478a65d4c36ffe44c6a7bcb60e3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "23965189"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>使用 Office 365 PowerShell 管理 Skype for Business Online

 **摘要：** 使用 Office 365 PowerShell 管理 Skype for Business Online 策略、每用户策略和会议设置。
  
主要任务的业务 Online 管理员任何 Skype 之一管理策略。尽管您可以完成的一些 Office 365 管理中心中的这些任务，其他任务是更快、 更轻松地在 Office 365 PowerShell。 

## <a name="before-you-start"></a>准备工作

下载并安装[Skype for Business Online Connector 模块](https://www.microsoft.com/en-us/download/details.aspx?id=39366)，然后重新启动计算机，如果系统提示您。


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>使用 Skype 业务 Online 管理员帐户名和密码连接

1. 打开 Windows PowerShell 命令提示符并运行以下命令： 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. **Windows PowerShell 凭据请求**对话框中，键入业务 Online 管理员帐户名和密码，您 Skype，然后单击**确定**。


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>使用 Skype 业务 Online 管理员帐户具有多重身份验证的连接

1. 打开 Windows PowerShell 命令提示符并运行以下命令：

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. 当提示**新建 CsOnlineSession**命令时，输入您 Skype 业务 Online 管理员帐户名称。

3. 在**登录到您的帐户**对话框中，键入您的业务 Online 管理员密码，Skype，然后单击**登录**。

4. 按照**登录到您的帐户**对话框中的说明，以提供其他身份验证信息，请验证代码，如，然后单击**验证**。

有关详细信息，请参阅下列主题：
  
- [使用 Office 365 PowerShell 管理 Skype for Business Online 策略](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [指定每个用户 Skype 的在线商业策略与 Office 365 PowerShell](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>另请参阅

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

[Skype 的业务 PowerShell cmdlet 参考](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

