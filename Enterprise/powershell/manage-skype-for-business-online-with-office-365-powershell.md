---
title: 使用 PowerShell 管理 Skype for Business Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要：使用 PowerShell for Microsoft 365 管理 Skype for Business Online 策略、每用户策略和会议设置。
ms.openlocfilehash: 10587dad171c3df9de6985ad314bc1791080b8a1
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592206"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>使用 PowerShell 管理 Skype for Business Online

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

任何 Skype for Business Online 管理员的主要任务之一是管理策略。 虽然你可以在 Microsoft 365 管理中心中完成其中的一些任务，但通过 PowerShell 你可以更快、更轻松地完成其他任务。 

## <a name="before-you-start"></a>准备工作

下载并安装 [Skype for Business Online 连接器模块](https://www.microsoft.com/download/details.aspx?id=39366)，然后重新启动计算机。


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>使用 Skype for Business Online 管理员帐户名称和密码进行连接

1. 开启 Windows PowerShell 命令提示符并运行以下命令： 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. 在 **“Windows PowerShell 凭据请求”** 对话框中，键入你的 Skype for Business Online 管理员帐户名和密码，然后单击 **“确定”**。


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a>使用具有多重身份验证的 Skype for Business Online 管理员帐户进行连接

1. 开启 Windows PowerShell 命令提示符并运行以下命令：

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. 当出现 **New-CsOnlineSession** 命令提示时，请输入 Skype for Business Online 管理员帐户名称。

3. 在 **“登录到你的帐户”** 对话框中，键入你的 Skype for Business Online 管理员密码，然后单击 **“登录”**。

4. 按照 **“登录到你的帐户”** 对话框中的说明提供其他验证信息（如验证码），然后单击 **“登录”**。

有关详细信息，请参阅下列主题：
  
- [使用 PowerShell 管理 Skype for Business Online 策略](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [使用 PowerShell 指定每个用户 Skype for Business Online 策略](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>另请参阅

[使用 PowerShell 管理 Microsoft 365](manage-office-365-with-office-365-powershell.md)
  
[PowerShell for Microsoft 365 入门](getting-started-with-office-365-powershell.md)

[Skype for Business PowerShell cmdlet 参考](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

