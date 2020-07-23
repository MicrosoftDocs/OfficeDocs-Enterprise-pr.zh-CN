---
title: 为 Microsoft 365 的 PowerShell 分配每用户 Skype for Business Online 策略
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 摘要：使用适用于 Microsoft 365 的 PowerShell 为 Skype for Business Online 策略分配每用户通信设置。
ms.openlocfilehash: 4522cfd877355794c32d9b9bdf14fb11cd0e71b4
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229838"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a>为 Microsoft 365 的 PowerShell 分配每用户 Skype for Business Online 策略

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

使用 PowerShell for Microsoft 365 是将每个用户的通信设置分配到 Skype for Business Online 策略的有效方式。
  
## <a name="before-you-begin"></a>准备工作

使用以下说明设置运行命令（跳过已完成的步骤）：
  
1. 下载并安装[Skype For Business Online 连接器模块](https://www.microsoft.com/download/details.aspx?id=39366)。
    
2. 打开 Windows PowerShell 命令提示符，并运行以下命令： 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

出现提示时，请输入你的 Skype for Business Online 管理员帐户名称和密码。
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>更新用户帐户的外部通信设置

假设您想要更改用户帐户上的外部通信设置。 例如，您希望允许 Alex 与联合用户通信（EnableFederationAccess 等于 True），而不是 Windows Live 用户（EnablePublicCloudAccess 等于 False）。 若要执行此操作，您需要执行以下两项操作：
  
1. 找到符合我们的条件的外部访问策略。
    
2. 将该外部访问策略分配给 Alex。
    
如何确定要为其分配 Alex 的外部访问策略？ 以下命令返回在 EnableFederationAccess 设置为 True 且 EnablePublicCloudAccess 设置为 False 时的所有外部访问策略：
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

除非您已创建 ExternalAccessPolicy 的任何自定义实例，否则该命令将返回一个符合我们的条件（FederationOnly）的策略。 如以下示例所示：
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

现在，您知道要向 Alex 分配的策略，我们可以使用[set-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet 分配该策略。 如以下示例所示：
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

分配策略相当简单：只需指定用户的标识和要分配的策略的名称即可。 
  
在考虑策略和策略分配时，您并不局限于一次性使用用户帐户。 例如，假设您需要获得可与联盟伙伴和 Windows Live 用户通信的所有用户的列表。 我们已经知道，这些用户已分配有外部用户访问策略 FederationAndPICDefault。 由于我们知道，您可以通过运行一个简单的命令来显示所有这些用户的列表。 命令如下：
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

换言之，向我们显示 ExternalAccessPolicy 属性设置为 FederationAndPICDefault 的所有用户。 （为了限制屏幕上显示的信息量，请使用 Select-Object cmdlet 显示 "仅显示每个用户的显示名称"。） 
  
若要将所有用户帐户配置为使用相同的策略，请使用以下命令：
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

此命令使用 Get-csonlineuser 返回已启用 Lync 的所有用户的集合，然后将所有这些信息发送给 Set-csexternalaccesspolicy，这会将 FederationAndPICDefault 策略分配给集合中的每个用户和每个用户。
  
作为另一个示例，假设您之前已将 Alex 分配给 FederationAndPICDefault 策略，现在您已改变了想法，并希望由全局外部访问策略管理他。 您不能将全局策略明确分配给任何人。 相反，如果没有为用户分配每用户策略，则将全局策略用于指定的用户。 因此，如果我们想要由全局策略管理 Alex，则需要*取消*分配之前分配给他的任何每用户策略。 下面是一个示例命令：
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

此命令将向 Alex 分配的外部访问策略的名称设置为一个 null 值（$Null）。 空值表示 "nothing"。 换言之，没有向 Alex 分配任何外部访问策略。 如果没有向用户分配任何外部访问策略，则该用户将由全局策略进行管理。
  

## <a name="managing-large-numbers-of-users"></a>管理大量用户

若要管理大量用户（1000或更多），您需要通过使用[调用命令](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7)cmdlet 的脚本块对命令进行批处理。  在前面的示例中，每次执行 cmdlet 时，都必须先设置调用，然后等待结果，然后再将其发送回来。  使用脚本块时，可以远程执行 cmdlet，并在完成后将数据发送回来。 

```powershell
Import-Module LyncOnlineConnector
$sfbSession = New-CsOnlineSession
$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

这将在没有客户端策略的时候发现500个用户。 它将向他们授予客户端策略 "ClientPolicyNoIMURL" 和外部访问策略 "FederationAndPicDefault"。 结果成批分组为50，每批50将被发送到远程计算机。
  
## <a name="see-also"></a>另请参阅

[使用 PowerShell 管理 Skype for Business Online](manage-skype-for-business-online-with-office-365-powershell.md)
  
[使用 PowerShell 管理 Microsoft 365](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 的 PowerShell 入门](getting-started-with-office-365-powershell.md)
