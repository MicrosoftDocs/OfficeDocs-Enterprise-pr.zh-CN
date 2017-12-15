---
title: "指定每个用户 Skype 的在线商业策略与 Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: "摘要： 使用 Office 365 PowerShell 将每个用户分配与 Skype 的在线商业策略的通信设置。"
ms.openlocfilehash: 91916b41ba420a204ecabb27eea2e451a91f6f25
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>指定每个用户 Skype 的在线商业策略与 Office 365 PowerShell

 **摘要：**使用 Office 365 PowerShell 分配与 Skype 的在线商业策略的通信设置的每个用户。
  
使用 Office 365 PowerShell 是分配与 Skype 的在线商业策略的通信设置的每个用户的有效方法。
  
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
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>更新外部通信设置的用户帐户

假设您想要更改的用户帐户上的外部通信设置。例如，您想要允许 Alex 通信与联盟 （EnableFederationAccess 等于 True） 的用户，但不是能与 Windows Live 的用户 （EnablePublicCloudAccess 等于 False）。要做到这一点，您需要做两件事：
  
1. 找到符合我们的条件的外部访问策略。
    
2. 将该外部访问策略分配给 Alex。
    
> [!NOTE]
>  您不能创建所有的自定义策略我们自己。这是因为 Skype 的在线业务不允许您创建自定义策略。相反，您必须指定创建专为 Office 365 的策略之一。那些先前创建的策略包括： 4 个不同的客户端策略、 224 不同的会议策略、 5 不同的拨号计划、 5 个不同的外部访问策略、 1 承载语音邮件策略和 4 不同语音策略。
  
那么，如何确定要分配 Alex 的外部访问策略？下面的命令将返回所有外部访问策略位置设置为 True 时 EnableFederationAccess 和 EnablePublicCloudAccess 设置为 False:
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

该命令的作用是返回所有满足两个条件的策略： EnableFederationAccess 属性设置为 True，并将 EnablePublicCloudAccess 策略设置为 False。反过来，该命令将返回一个符合我们的标准 (FederationOnly) 的策略。下面是一个示例：
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> 该策略的身份说标记： FederationOnly。标记出事实： 前缀是 carryover 从 Microsoft Lync 2013 执行的早期预发行工作。向用户分配策略时，您应该删除标记： 前缀和只使用策略名称： FederationOnly。 
  
现在，您知道要将分配给 Alex 的策略，我们可以将此策略分配通过[授予 CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet。下面是一个示例：
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

分配策略是非常简单： 您只需指定用户的标识和分配策略的名称。 
  
并且对策略和策略分配时，您并不局限于处理用户帐户一次。例如，假设您需要允许与联盟伙伴和 Windows Live 用户进行通信的所有用户的列表。我们已经知道这些用户具有已分配的外部用户访问策略 FederationAndPICDefault。因为我们知道，您可以通过运行一个简单的命令显示所有这些用户的列表。以下是该命令：
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

换句话说，显示我们所有用户在将 ExternalAccessPolicy 属性设置为 FederationAndPICDefault。（而且，限制出现在屏幕上的信息，以便使用选择对象用于显示向我们显示只使用每个用户的显示名称。 
  
若要配置我们的所有用户帐户，使用该同一策略，请使用以下命令：
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

此命令使用 Get CsOnlineUser 返回的已启用的 Lync，然后将所有这些信息发送到授权-CsExternalAccessPolicy，FederationAndPICDefault 策略为集合中的每个用户的所有用户的集合。
  
作为一个附加的示例，假设您以前归入 Alex FederationAndPICDefault 策略，现在改变了主意并想要他由全球外部访问策略管理。任何人，不能明确指定全局策略。指定任何其他每用户策略时才使用它。因此，如果我们希望 Alex 通过全球政策进行管理，需要*取消指定*任何以前分配给他的每个用户策略。下面是一个示例命令：
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

该命令设置为空值 ($Null) 分配给 Alex 外部访问策略的名称。空值表示"没有"。换句话说，没有外部访问策略分配给 Alex。没有外部访问策略分配给用户后，该用户再获取全局策略管理。
  
若要禁用用户帐户使用 Windows PowerShell，使用 Azure Active Directory cmdlet 删除 Alex 的 Skype 的在线业务许可证。有关详细信息，请参阅[禁用 Office 365 PowerShell 的服务访问](assign-licenses-to-user-accounts-with-office-365-powershell.md)。
  
## <a name="see-also"></a>See also

#### 

[使用 Office 365 PowerShell 管理 Skype for Business Online](manage-skype-for-business-online-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

