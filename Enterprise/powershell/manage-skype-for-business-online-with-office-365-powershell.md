---
title: 使用 PowerShell 管理 Skype for Business Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要：使用适用于 Microsoft 365 的 PowerShell 管理 Skype for Business Online 策略、每用户策略和会议设置。
ms.openlocfilehash: f66b3186a5b29bbf0756a629b85c626caf2c1e36
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230438"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>使用 PowerShell 管理 Skype for Business Online

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

Skype for Business Online 管理员的一项主要任务就是管理策略。 虽然您可以在 Microsoft 365 管理中心完成其中的部分任务，但在 PowerShell 中，其他任务的工作速度更快、更轻松。 

## <a name="before-you-start"></a>准备工作

下载并安装[Skype For Business Online 连接器模块](https://www.microsoft.com/download/details.aspx?id=39366)，然后重新启动计算机。


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>使用 Skype for Business Online 管理员帐户名称和密码进行连接

1. 打开 Windows PowerShell 命令提示符，并运行以下命令： 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. 在 " **Windows PowerShell 凭据请求**" 对话框中，键入您的 Skype For business Online 管理员帐户名称和密码，然后单击 **"确定"**。


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a>使用具有多因素身份验证的 Skype for Business Online 管理员帐户进行连接

1. 打开 Windows PowerShell 命令提示符，并运行以下命令：

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. 当**CsOnlineSession**命令出现提示时，请输入你的 Skype For business Online 管理员帐户名称。

3. 在 "**登录帐户**" 对话框中，键入您的 Skype For business Online 管理员密码，然后单击 "**登录**"。

4. 按照 "**登录到帐户**" 对话框中的说明提供其他身份验证信息（如验证码），然后单击 "**验证**"。

有关详细信息，请参阅下列主题：
  
- [使用 PowerShell 管理 Skype for Business Online 策略](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [使用 PowerShell 分配每用户 Skype for Business Online 策略](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>另请参阅

[使用 PowerShell 管理 Microsoft 365](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 的 PowerShell 入门](getting-started-with-office-365-powershell.md)

[Skype for Business PowerShell cmdlet 参考](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

