---
title: 为什么需要使用适用于 Microsoft 365 的 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 摘要：了解为什么必须使用 PowerShell 来管理 Microsoft 365，在某些情况下，在某些情况下可以更有效地管理 Microsoft。
ms.openlocfilehash: ba786acd8b5ad08bad97b11812f0180004e55cb6
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229858"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>为什么需要使用适用于 Microsoft 365 的 PowerShell

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

使用 Microsoft 365 管理中心，不仅可以管理 Microsoft 365 用户帐户和许可证，还可以管理 Microsoft 365 服务，例如 Exchange Online、团队和 SharePoint Online。 不过，您还可以使用 PowerShell 命令管理这些元素，利用命令行和脚本语言环境实现速度、自动化和其他功能。
  
在本文中，我们将向你展示可使用 PowerShell 管理 Microsoft 365 的方法：
  
- 显示使用 Microsoft 365 管理中心无法看到的其他信息
    
- 仅配置 PowerShell 可能的功能和设置
    
- 执行批量操作
    
- 筛选数据
    
- 打印或保存数据
    
- 跨服务管理
    
在开始之前，请先了解 Microsoft 365 的 PowerShell，它是一组用于 Windows PowerShell 的模块，即基于 Windows 的服务和平台的命令行环境。 此环境创建一种命令行管理程序语言，可使用其他模块进行扩展，并提供执行简单或复杂命令或脚本的方法。 例如，在安装适用于 Microsoft 365 模块的 PowerShell 并连接到 Microsoft 365 订阅后，可以运行此命令，以列出 Microsoft Exchange Online 的所有用户邮箱：
  
```powershell
Get-Mailbox
```

使用 Microsoft 365 管理中心也可以轻松地获取邮箱的列表，但计算所有 web 应用程序的所有网站的所有列表中的项目数无法轻松完成。
  
请注意，适用于 Microsoft 365 的 PowerShell 旨在提高和增强管理 Microsoft 365 的能力，而不是替换 Microsoft 365 管理中心。 作为管理员，您必须至少为 Microsoft 365 使用 PowerShell，因为有一些配置过程只能在 PowerShell 中为 Microsoft 365 命令完成。 在这些情况下，需要了解如何：
  
- 为 Microsoft 365 模块安装 PowerShell （每台管理员计算机只能执行一次）。
    
- 连接到 Microsoft 365 订阅（为每个 PowerShell 会话完成一次）。
    
- 收集运行所需的 PowerShell for Microsoft 365 命令所需的信息。
    
- 成功运行适用于 Microsoft 365 命令的 PowerShell。
    
在学过这些基本技巧之后，您不需要使用 **Get-Mailbox** 命令列出您的邮箱用户，也不需要明白如何创建像前一个命令那样的新命令来计算您的所有 Web 应用的所有网站的所有列表中的项目数量。 Microsoft 和管理员社区可以根据需要为您提供帮助。
  
## <a name="powershell-for-microsoft-365-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a>PowerShell for Microsoft 365 可以显示你无法通过 Microsoft 365 管理中心看到的其他信息

Microsoft 365 管理中心显示了大量有用的信息，但这并不意味着它会显示 Microsoft 365 存储在用户、许可证、邮箱和网站上的所有可能的信息。 下面的示例展示了 Microsoft 365 管理中心中的**用户和组**：
  
![Microsoft 365 管理中心中的用户和组的显示示例。](media/o365-powershell-users-and-groups.png)
  
出于多种目的，这显示了你需要知道的信息。 但是，有时你需要了解更多。 例如，Microsoft 365 许可（和用户可使用的 Microsoft 365 功能）取决于该用户的地理位置。 向居住在美国的用户扩展的策略和功能可能与向居住在印度或比利时的用户扩展的策略和功能不同。 您可以使用 Microsoft 365 管理中心来确定用户的地理位置，步骤如下：
  
1. 双击用户的"显示名称"。
    
2. 在用户属性显示窗格中，单击"详细信息"。
    
3. 在显示的详细信息中，单击"其他详细信息"。
    
4. 向下滚动，直到看见"国家或地区"标题：
    
     ![Microsoft 365 管理中心中用户的区域信息示例。](media/o365-powershell-usage-location.png)
  
5. 在一张纸上记下用户的显示名称和位置，或将其复制并粘贴至记事本中。 
    
您必须为每个用户重复此过程。 对于许多用户来说，这可能是一项繁琐的任务。 对于适用于 Microsoft 365 的 PowerShell，你可以使用以下命令为所有用户显示此信息：
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。 若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。
>

下面展示了显示内容示例：
  
```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的所有用户（ **AzureADUser** ），但仅显示每个用户的名称和位置（**选择 DisplayName、UsageLocation** ）。
  
由于适用于 Microsoft 365 的 PowerShell 支持命令行管理程序语言，因此您可以进一步处理从**AzureADUser**命令获取的信息。 例如，您可能希望按照用户的位置对这些用户进行排序，将所有巴西用户组合在一起，将所有美国用户组合在一起，等等。下面是命令：
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

下面展示了显示内容示例：
  
```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的所有用户，但仅显示每个用户的名称和位置，并首先按其位置以及它们的名称（ **Sort UsageLocation，DisplayName** ）对其进行排序。
  
还可以使用其他筛选条件。例如，如果只想查看巴西用户的信息，请使用下面的命令：
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

下面展示了显示内容示例：
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的位置是巴西的所有用户（**其中 {$） \_ 。UsageLocation-eq "BR"}** ），然后显示每个用户的名称和位置。
  
 **有关较大域的快速说明**
  
如果您的域非常大，有数万个用户，那么尝试此文章中介绍的某些示例可能会带来"限制"。 这说明，基于计算能力和可用网络带宽等因素，您每次尝试的操作有点多。 因此，较大的组织可能希望将这些 PowerShell 中的某些 365 PowerShell 拆分成两个命令。 例如，这一个命令将返回所有用户帐户，并显示每个用户的名称和位置。
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

这对于较小的域非常有用。但在大型组织中，您可能需要将此命令拆分为两个命令：一个命令用于将用户帐户信息存储在一个变量中，另一个命令用于显示所需信息。如以下示例所示：
  
```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

此 PowerShell 命令集的解释如下：
- 获取当前 Microsoft 365 订阅中的所有用户，并将信息存储在名为 $x 的变量中（ **$x = AzureADUser** ）。
- 显示变量 $x 的内容，但只包含每个用户的用户名和地理位置 (**$x | Select DisplayName, UsageLocation**)。
  
## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>Microsoft 365 具有仅可为 Microsoft 365 配置 PowerShell 的功能

Microsoft 365 管理中心旨在提供对大多数用户适用的最常见或有意义的管理任务的访问权限。 换句话说，Microsoft 365 管理中心的设计是为了使典型管理员可以使用该工具执行最常见的管理任务。 通过此定义，意味着有一些任务无法使用 Microsoft 365 管理中心完成。
  
例如，Skype for Business Online 管理中心提供用于创建自定义会议邀请的几个选项：
  
![用于在 Skype for Business Online 管理中心内显示自定义会议邀请的示例。](media/o365-powershell-meeting-invitation.png)
  
借助这些设置，您可以为会议邀请添加少许个性化和专业化。但是，与仅创建自定义会议邀请相比，它对会议配置设置的帮助更多。例如，默认情况下，会议允许：
  
- 匿名用户获取自动参与每个会议的权限。
    
- 与会者记录会议。
    
- 您组织中的所有用户在加入会议时被指定为演示者。
    
这些设置不是从 Skype for Business Online 管理中心提供。 但是，可以从 PowerShell for Microsoft 365 中控制它们。 下面是一个禁用这三项设置的命令：
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> 此命令要求必须安装 [Skype for Business Online PowerShell 模块](https://www.microsoft.com/download/details.aspx?id=39366)。 
  
> [!TIP]
>  此 PowerShell 命令的解释为：对于新的 Skype for Business Online 会议（ **get-csmeetingconfiguration** ）的设置，禁用允许匿名用户获取会议的自动进入（ **-AdmitAnonymousUsersByDefault $False** ），禁用与会者录制会议的能力（ **-AllowConferenceRecording $False** ），不要将组织中的所有用户指定为演示者（ **-DesignateAsPresenter "None"** ）。
  
如果改变了主意且希望还原这些默认设置（即启用所有设置），请运行下面的命令：
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

这仅是一个示例。 还有其他一些原因，作为管理员，您需要熟悉为 Microsoft 365 命令运行 PowerShell。
  
## <a name="powershell-for-microsoft-365-is-great-at-carrying-out-bulk-operations"></a>PowerShell for Microsoft 365 非常适合执行批量操作

以往，当你执行一个操作时，像 Microsoft 365 管理中心这样的可视界面非常有用。 例如，如果您需要禁用一个用户帐户，则可以使用 Microsoft 365 管理中心快速查找并清除复选框。 这可能比在 PowerShell 中执行类似的操作更简单。
  
但是，如果您必须在一大范围的其他内容中更改许多内容或所选的内容，Microsoft 365 管理中心可能无法充分利用你的时间。 例如，如果您必须更改数以千计的电话号码前缀，或者您需要从所有 SharePoint Online 网站中删除特定用户（Ken Myer），那么如何在 Microsoft 365 管理中心中执行此操作？
  
关于后一个示例，你拥有数百个 SharePoint Online 网站，但甚至不知道 Ken Meyer 是哪个群组的成员。 这意味着您必须从 Microsoft 365 管理中心开始，然后对每个网站执行此过程：
  
1. 单击网站的"URL"。
    
2. 在"网站集属性"框中，单击"网站地址"链接以打开该网站。
    
3. 在网站上，单击"共享"。
    
4. 在"共享"对话框中，单击显示有权访问该网站的所有用户的链接：
    
     ![在 SharePoint Online 管理中心内查看 SharePoint Online 站点成员的示例。](media/o365-powershell-view-permissions.png)
  
5. 在"共享对象"对话框中，单击"高级"。
    
6. 向下滚动用户列表，找到并选择 Ken Myer（假设他有权访问该网站），然后单击"删除用户权限"。
    
对于数百个网站来说，这可能需要很长时间。
  
另一种方法是使用适用于 Microsoft 365 的 PowerShell 和以下命令从所有网站中删除 Ken Myer：
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> 此命令要求您安装[SharePoint Online PowerShell 模块](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。 
  
> [!TIP]
>  此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的所有 SharePoint 网站（ **get-sposite** ），并为每个网站删除 Ken Meyer （该列表中的用户可以访问它）（ **ForEach {remove-get-spouser-site $） \_ 。Url-Person.loginname "kenmyer@litwareinc.com"}** ）。
  
由于我们要告知 Microsoft 365 从每个站点中删除 Ken Meyer （包括用户不具有访问权限的站点），因此此命令的显示将显示他目前没有访问权限的那些站点的错误。 我们可以对此命令使用一个附加条件，使其仅从其登录列表中有 Key Meyer 的网站中删除他，但所列错误对网站本身没有任何坏处。 此命令可能需要几分钟的时间才能运行数百个网站，而不是通过 Microsoft 365 管理中心工作数小时。
  
下面是另一个批量操作示例。使用此命令将新 SharePoint 管理员 Bonnie Kearney 添加到组织中的所有网站：
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的所有 SharePoint 网站，并为每个网站提供 Bonnie Kearney 访问，方法是将其登录名添加到网站的 "成员" 组（ **ForEach {get-spouser-site $ \_ 。Url-Person.loginname "bkearney@litwareinc.com"-Group "Members"}** ）。
  
## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>适用于 Microsoft 365 的 PowerShell 非常适合筛选数据

Microsoft 365 管理中心提供了几种不同的筛选数据的方法，以便快速轻松地找到目标信息子集。 例如，可以通过 Exchange 轻松筛选用户邮箱的几乎所有属性。 例如，下面是居住在布卢明顿市的所有用户的邮箱列表：
  
![在 Microsoft 365 管理中心中执行高级搜索的示例，用于居住在布卢明顿城市的所有用户的邮箱列表。](media/o365-powershell-advanced-search.png)
  
Exchange 管理中心还允许您组合筛选条件。例如，您可以查找居住在布卢明顿和在财务部门工作的所有用户的邮箱。 
  
但是，在 Exchange 管理中心有一些操作限制。例如，也许您想要查找居住在布卢明顿或圣地亚哥的用户的邮箱或所有不居住在布卢明顿的用户的邮箱。 
  
对于适用于 Microsoft 365 的 PowerShell，你可以使用此命令获取居住在布卢明顿或圣地亚哥城市的所有人员的邮箱列表：
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

下面展示了显示内容示例：
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的所有用户，这些用户在圣地亚哥或布卢明顿（**其中 {$）的城市中拥有邮箱。 \_RecipientTypeDetails-eq "UserMailbox"-和（$ \_ 。City-eq "圣地亚哥"-或 $ \_ 。City-eq "布卢明顿"）}** ），然后显示每个名称和城市（**选择 "DisplayName"、"city** "）。
  
若要列出居住在布卢明顿之外的用户的所有邮箱，可以运行下面的命令：
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

下面展示了显示内容示例：
  
```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的邮箱不位于布卢明顿城市（其中 {$）的所有用户** \_ 。RecipientTypeDetails-eq "UserMailbox" 和 $ \_ 。City-ne "布卢明顿"}** ），然后显示每个城市的姓名和城市。
  
您还可以在 PowerShell 筛选器中使用通配符，以匹配名称的一部分。 例如，假设您正在查找某个用户帐户，但是只记得其姓氏是 Anderson，或也许是 Henderson 或 Jorgenson。
  
您可以使用搜索工具在 Microsoft 365 管理中心内跟踪该用户并执行三种不同的搜索：
  
- 一次是搜索  *Anderson* 
    
- 一次是搜索  *Henderson* 
    
- 一次是搜索  *Jorgenson* 
    
由于所有这三个名称都以 "儿子" 结束，因此您可以告知 PowerShell 显示姓名以 "儿子" 结尾的所有用户。 命令如下：
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  此 PowerShell 命令的解释为：获取当前 Microsoft 365 订阅中的所有用户，但使用仅列出姓氏以 "儿子" 结尾的用户的筛选器（ **-筛选器 "{LastName-like" \* 儿子 "}"** ）。 \*代表任意一组字符，这些字符是用户的姓的字母。
  
## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>适用于 Microsoft 365 的 PowerShell 可轻松打印或保存数据

Microsoft 365 管理中心允许你查看数据列表。 下面是显示已启用 Skype for Business Online 的用户列表的 Skype for Business Online 管理中心的一个示例：
  
![用于显示已为 Skype for Business Online 启用的用户列表的 Skype for Business Online 管理中心的示例。](media/o365-powershell-lync-users.png)
  
若要将该信息保存到一个文件，必须复制并将其粘贴到一个文档或 Excel。 在任一种情况下，该副本可能需要附加的格式设置。 此外，Microsoft 365 管理中心不提供直接打印显示列表的方法。
  
幸运的是，您可以使用 PowerShell 不仅显示列表，还可以将其保存到可轻松导入 Excel 的文件中。 下面是一个将 Skype for Business Online 用户数据保存为逗号分隔值 (CSV) 文件（一个可轻松导入为 Excel 工作表中的表的文件）的示例命令：
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

下面是显示的一个示例：
  
![保存到逗号分隔值 (CSV) 文件的 Skype for Business Online 用户数据的导入到 Excel 工作表的表示例。](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  此 PowerShell 命令的解释为：在当前 Microsoft 365 订阅中获取所有 Skype for Business Online 用户（ **get-csonlineuser** ），仅获取用户名、UPN 和位置（**选择 DisplayName、UserPrincipalName、UsageLocation** ），然后将该信息保存在名为 C： logsSfBUsers.csv 的 CSV 文件中 \\ \\ （ **Export-CSV-Path "C： \\ logs \\SfBUsers.csv"-NoTypeInformation** ）。
  
您可以使用选项将此列表另存为 XML 文件或 HTML 页。事实上，通过其他 PowerShell 命令，您可以将其直接保存为 Excel 文件，该文件具有所需的所有自定义格式。 
  
您还可以向 Windows 中的默认打印机发送直接显示列表的 PowerShell 命令的输出。 下面是一个示例命令：
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

打印的文档如下所示：
  
![将在 Windows 中直接列出的 PowerShell 命令输出到默认打印机的已打印文档的示例。](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  此 PowerShell 命令的解释为：在当前 Microsoft 365 订阅中获取所有 Skype for Business Online 用户，仅获取用户名、UPN 和位置，然后将该信息发送到默认的 Windows 打印机（**传出打印机**）。
  
打印的文档与 PowerShell 命令窗口中显示的简单格式相同，但在创建 PowerShell 命令以列出所需的内容后，只需添加 **|Out-打印机**到命令的末尾，以获取要从其进行工作的硬副本。
  
## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>PowerShell for Microsoft 365 允许您跨服务器产品进行管理

组成 Microsoft 365 的不同组件设计为协同工作。 例如，假设您向 Microsoft 365 添加了一个新用户，在您执行此操作时，您可以将此类信息指定为用户的部门和电话号码。 如果使用任何 Microsoft 365 服务访问用户信息，则该信息将可用： Skype for Business Online、Exchange 或 SharePoint Online。
  
不过，此规则适用于跨产品套件的一般信息。特定于产品的信息 - 例如，用户的 Exchange 邮箱的有关信息 - 通常无法跨套件提供。例如，如果您想要知道用户邮箱是否启用，该信息将仅可在 Exchange 管理中心获得。 
  
假设您要为您的所有用户生成显示以下信息的报告：
  
- 用户的显示名称
    
- 用户是否已获得适用于 Microsoft 365 的许可
    
- 用户的 Exchange 邮箱是否已启用
    
- 用户是否已启用 Skype for Business Online
    
您当前无法使用 Microsoft 365 管理中心来轻松生成此类报告。 相反，您必须创建单独的文档来存储信息（如 Excel 工作表），并从 Microsoft 365 管理中心获取所有用户名和许可信息，从 Exchange 管理中心获取邮箱信息，从 Skype for business Online 管理中心获取 Skype for Business Online 信息，然后逐份打印并合并该信息。
  
另一种方法是使用 PowerShell 脚本编译该报告。
  
以下示例脚本会比到目前为止在本文中看到的命令更复杂。 但是，它展示了使用 PowerShell 创建信息视图的潜在可能性，这一点也非常困难。 下面是可以编译并显示所需列表的脚本：
  
```powershell
$x = Get-AzureADUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

下面展示了显示内容示例：
  
```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

此 PowerShell 脚本的解释如下：  

- 获取当前 Microsoft 365 订阅中的所有用户，并将信息存储在名为 $x 的变量中（ **$x = AzureADUser** ）。
- 启动对 $x 变量中的所有用户运行的循环 (**foreach ($i in $x)**)。  
- 定义 $y 变量，并将用户的邮箱信息存储在其中 (**$y = Get-Mailbox -Identity $i.UserPrincipalName**)。
- 将新属性添加到 IsMailBoxEnabled 用户信息，并将它设置为用户邮箱的 IsMailBoxEnabled 属性值(**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**)。
- 定义 $y 变量，并将用户的 Skype for Business Online 信息存储在其中 (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**)。
- 将新属性添加到 EnabledForSfB 用户信息，并将它设置为用户的 Skype for Business Online 信息的 Enabled 属性值 (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**)。
- 显示用户列表，但仅包括用户名、是否获得许可，以及两个指示是否已启用邮箱和是否已启用 Skype for Business Online 的新属性 (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**)。
  
## <a name="see-also"></a>另请参阅

[Microsoft 365 的 PowerShell 入门](getting-started-with-office-365-powershell.md)
  
[使用 PowerShell 管理 Microsoft 365 用户帐户、许可证和组](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[在 Microsoft 365 中使用 Windows PowerShell 创建报告](use-windows-powershell-to-create-reports-in-office-365.md)

