---
title: 指定每个用户 Skype 的在线商业策略与 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: '摘要: 使用 Office 365 PowerShell 将每个用户的通信设置分配到 Skype for Business Online 策略。'
ms.openlocfilehash: 3c6c869874329d7efb6d8c417c797c9f81df6bf8
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069288"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>指定每个用户 Skype 的在线商业策略与 Office 365 PowerShell

 **摘要:** 使用 Office 365 PowerShell 将每个用户的通信设置分配到 Skype for Business Online 策略。
  
使用 Office 365 PowerShell 是一种将每个用户的通信设置分配到 Skype for Business Online 策略的有效方式。
  
## <a name="before-you-begin"></a>开始之前

使用以下说明设置运行命令 (跳过已完成的步骤):
  
1. 下载并安装[Skype For Business Online 连接器模块](https://www.microsoft.com/en-us/download/details.aspx?id=39366)。
    
2. 打开 Windows PowerShell 命令提示符, 并运行以下命令: 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
出现提示时, 请输入你的 Skype for Business Online 管理员帐户名称和密码。
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>更新用户帐户的外部通信设置

假设您想要更改用户帐户上的外部通信设置。 例如, 您希望允许 Alex 与联合用户通信 (EnableFederationAccess 等于 True), 而不是 Windows Live 用户 (EnablePublicCloudAccess 等于 False)。 若要执行此操作, 您需要执行以下两项操作:
  
1. 找到符合我们的条件的外部访问策略。
    
2. 将该外部访问策略分配给 Alex。
    
> [!NOTE]
>  您无法创建自己的自定义策略。 这是因为 Skype for Business Online 不允许您创建自定义策略。 而是必须分配专为 Office 365 创建的策略之一。 这些预创建的策略包括: 4 个不同的客户端策略、224不同的会议策略、5个不同的拨号计划、5个不同的外部访问策略、1个托管的语音邮件策略和4种不同的语音策略。
  
那么, 如何确定要分配 Alex 的外部访问策略？ 以下命令返回在 EnableFederationAccess 设置为 True 且 EnablePublicCloudAccess 设置为 False 时的所有外部访问策略：
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

该命令的作用是返回满足两个条件的所有策略: EnableFederationAccess 属性设置为 True, EnablePublicCloudAccess 策略设置为 False。 反过来, 该命令将返回一个符合我们的条件 (FederationOnly) 的策略。 如以下示例所示：
  
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
> 策略标识显示标记: FederationOnly。 事实上，“Tag:”前缀是从 Microsoft Lync 2013 上的早期预发布工作中沿袭而来。 向用户分配策略时，您应该删除“Tag:”前缀，只使用策略名称：FederationOnly。 
  
现在, 您知道要向 Alex 分配的策略, 我们可以使用[set-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet 分配该策略。 如以下示例所示：
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

分配策略相当简单: 只需指定用户的标识和要分配的策略的名称即可。 
  
在考虑策略和策略分配时, 您并不局限于一次性使用用户帐户。 例如，假设您需要获得可与联盟伙伴和 Windows Live 用户通信的所有用户的列表。 我们已经知道，这些用户已分配有外部用户访问策略 FederationAndPICDefault。 由于我们知道, 您可以通过运行一个简单的命令来显示所有这些用户的列表。 命令如下：
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

换言之, 向我们显示 ExternalAccessPolicy 属性设置为 FederationAndPICDefault 的所有用户。 (为了限制屏幕上显示的信息量, 请使用 Select-Object cmdlet 显示 "仅显示每个用户的显示名称"。) 
  
若要将所有用户帐户配置为使用相同的策略, 请使用以下命令:
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

此命令使用 Get-csonlineuser 返回已启用 Lync 的所有用户的集合, 然后将所有这些信息发送给 Set-csexternalaccesspolicy, 这会将 FederationAndPICDefault 策略分配给集合中的每个用户和每个用户。
  
作为另一个示例, 假设您之前已将 Alex 分配给 FederationAndPICDefault 策略, 现在您已改变了想法, 并希望由全局外部访问策略管理他。 您不能将全局策略明确分配给任何人。 仅在分配了其他每个用户的策略时才使用它。 因此, 如果我们想要由全局策略管理 Alex, 则需要*取消*分配之前分配给他的任何每用户策略。 下面是一个示例命令：
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

此命令将向 Alex 分配的外部访问策略的名称设置为一个 null 值 ($Null)。 空值表示 "nothing"。 换言之, 没有向 Alex 分配任何外部访问策略。 如果没有向用户分配任何外部访问策略, 则该用户将由全局策略进行管理。
  
若要使用 Windows PowerShell 禁用用户帐户, 请使用 Azure Active Directory cmdlet 删除 Alex 的 Skype for Business Online 许可证。 有关详细信息, 请参阅[禁用对具有 Office 365 PowerShell 的服务的访问](assign-licenses-to-user-accounts-with-office-365-powershell.md)。
  
## <a name="see-also"></a>另请参阅

#### 

[使用 Office 365 PowerShell 管理 Skype for Business Online](manage-skype-for-business-online-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)

