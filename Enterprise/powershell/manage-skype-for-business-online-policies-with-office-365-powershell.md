---
title: "管理 Skype 与 Office 365 PowerShell 的在线业务策略"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "摘要： 使用 Office 365 PowerShell 来管理您的 Skype 的在线业务策略的用户帐户属性。"
ms.openlocfilehash: 6698bd43b2a55e1c98fbe8e536a46e2de604b4d2
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a>管理 Skype 与 Office 365 PowerShell 的在线业务策略

 **摘要：**使用 Office 365 PowerShell 来管理您的 Skype 的在线业务策略的用户帐户属性。
  
若要管理用户帐户的多个属性 Skype 的在线业务，必须先将它们指定为属性与 Office 365 PowerShell 的策略。
  
## <a name="before-you-begin"></a>开始之前

使用下列步骤来获取或设置到运行命令 （跳过您已完成的步骤）：
  
1. 下载并安装[Skype 业务联机接口模块](https://www.microsoft.com/en-us/download/details.aspx?id=39366)。
    
2. 打开 Windows PowerShell 命令提示窗口并运行以下命令： 
    
```
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

出现提示时，输入您 Skype 的在线业务管理员帐户名和密码。
    
## <a name="manage-user-account-policies"></a>管理用户帐户策略

通过使用策略配置许多 Skype 的在线业务的用户帐户属性。策略是简单的可以应用到一个或多个用户的设置的集合。来看一看如何已配置策略，您可以运行此 FederationAndPICDefault 策略的示例命令：
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

反过来，您应该会收到与以下类似的内容：
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

在此示例中，此策略中的值确定使用的可以或不能执行与联盟用户进行通信时。例如，EnableOutsideAccess 属性必须设置为 True，用户能够与组织外的人进行通讯。请注意，此属性不显示在 Office 365 管理中心。相反，属性自动设置为 True 或 False 基于您所做的其他选择。感兴趣的其他两个属性是：
  
- **EnableFederationAccess**表示用户是否可以与人的联盟域进行通信。
    
- **EnablePublicCloudAccess**表示用户是否可以与 Windows Live 用户通信。
    
因此，不要直接更改用户帐户 (例如，**集 CsUser EnableFederationAccess $True**) 与联合身份验证相关的属性。相反，您指定的帐户具有所需的属性值的预配置外部访问策略。我们希望用户能够与联盟用户和 Windows Live 用户进行通信，必须将该用户帐户分配策略允许的通信类型。
  
如果您想要知道有人可以与来自组织外部的用户进行通信，必须：
  
- 确定为此用户分配的是哪种外部访问策略。
    
- 确定此策略允许的许可范围。
    
例如，可以使用此命令执行的操作：
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

此命令查找指派给用户，然后查找功能启用或禁用该策略中的策略。
  
请注意，有没有 cmdlet 用于创建或修改策略。您必须使用预先由 Office 365 提供的策略。如果您想要看一看不同的策略可用，您可以使用这些命令：
  
- 获得 CsClientPolicy       
- 获得 CsConferencingPolicy        
- 获得 CsDialPlan            
- 获得 CsExternalAccessPolicy                         
- 获得 CsHostedVoicemailPolicy                        
- 获得 CsPresencePolicy                               
- 获得 CsVoicePolicy                                  

> [!NOTE]
> Skype 的在线业务的拨号计划是在除名称之外的每个方面的策略。"拨号计划"的名称选择而不是说，"拨号策略"与办公室通讯服务器和 Exchange 提供向后兼容性。 
  
例如，要查找所有语音策略可供您使用，运行以下命令：
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> 给您返回所有可用的语音策略的列表。请记住，但是，并非所有的策略可以指派给所有用户。这是由于各种涉及许可和地理位置的限制。（所谓"[使用位置](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx)。"）如果您想要知道的外部访问策略，可以分配给特定用户的会议策略，请使用类似如下的命令： 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

ApplicableTo 参数可将返回的数据限制为可分配到特定用户的策略（例如，Alex Darrow）。根据不同的授权和使用位置限制，可能会代表所有可用策略的子集。 
  
在某些情况下，属性策略不使用 Office 365，而其他人可以通过 Microsoft 技术支持人员进行管理。 
  
与 Skype 的在线业务，必须由某种类型的策略管理用户。如果有效策略相关的属性为空，这意味着当前用户管理的全局策略，除非他或她专门分配的每个用户策略自动应用于用户的策略。因为我们看不到列出的用户帐户的客户端策略，它是由全球政策进行管理。您可以确定此命令的全局客户端策略：
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>另请参阅

#### 

[使用 Office 365 PowerShell 管理 Skype for Business Online](manage-skype-for-business-online-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

