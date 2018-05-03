---
title: 检测和窗体注入修正 Outlook 规则和自定义 Office 365 中攻击
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 04/23/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: 了解如何识别和修正 Outlook 规则和 Office 365 中的自定义窗体注入攻击
ms.openlocfilehash: d0f54a0dc47d7a3602a7b4ce57a04c83d15d9301
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks-in-office-365"></a>检测和修正 Outlook 规则和 Office 365 中的自定义窗体注入攻击

**摘要**了解如何识别和修正 Outlook 规则和 Office 365 中的自定义窗体注入攻击。

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Outlook 规则和自定义窗体注入攻击是什么？
攻击者具有看见您的租户中的帐户，并获取中后，那里将尝试建立一种方法后发现并移除得到或留在的方法。这称为建立持久性机制。它们可以执行此操作的两种方法是通过利用 Outlook 规则或通过向 Outlook 中将自定义窗体。在这两种情况下，规则或窗体同步从云服务向桌面客户端，以便完全格式化和重新安装的客户端软件不消除注入机制。这是因为时的 Outlook 客户端软件重新连接到云中的邮箱它重新将下载的规则和从云中的表单。一旦措施，规则和窗体，攻击者将使用它们来执行远程或自定义代码，通常要在本地计算机上安装恶意软件。恶意软件然后重新窃取凭据，或执行其他非法活动。好的消息是，如果保留您修补到最新版本的客户端，您不会受到威胁，当前的 Outlook 客户端默认值阻止这两种机制。 

通常，攻击请遵循以下模式：

规则漏洞攻击
1. 攻击者窃取的用户名和密码之一的用户。
2. 攻击者然后登录到该用户的 Exchange 邮箱。邮箱可以是在 Exchange online 或 Exchange 内部部署。
3. 攻击者然后邮箱接收电子邮件的规则条件相匹配时触发的邮箱中创建转接规则。规则的条件和触发器电子邮件的内容是为每个其他定制。
4. 攻击者将触发电子邮件发送到通常使用他们的邮箱的用户。
5. 当收到电子邮件时，将触发规则。规则操作是通常以启动远程 (WebDAV) 服务器上的应用程序。
6. 应用程序通常安装恶意软件、 [Powershell 帝国](https://www.powershellempire.com/)，如本地用户的计算机上。
7. 恶意软件允许攻击者重新窃取用户的用户名和密码或其他凭据从本地计算机并执行其他恶意活动。

窗体漏洞攻击
1. 攻击者窃取的用户名和密码之一的用户。
2. 攻击者然后登录到该用户的 Exchange 邮箱中。邮箱可以是在 Exchange online 或 Exchange 内部部署。
3. 然后，攻击者创建的自定义邮件表单模板，并将其插入到用户的邮箱。 邮箱接收电子邮件所需的邮箱加载自定义窗体时，将触发自定义窗体。自定义窗体和电子邮件的格式是为每个其他定制。
4. 攻击者将触发电子邮件发送到用户，用户通常使用他们的邮箱。
5. 当收到电子邮件时，加载窗体。窗体启动远程 (WebDAV) 服务器上的应用程序。
6. 应用程序通常安装恶意软件、 [Powershell 帝国](https://www.powershellempire.com/)，如本地用户的计算机上。
7. 恶意软件允许攻击者重新窃取用户的用户名和密码或其他凭据从本地计算机并执行其他恶意活动。


## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>哪些规则和自定义窗体注入攻击可能类似于 Office 365？

这些持久性机制不太可能被用户注意到，在某些情况下甚至可能看不到这些。 本文介绍如何查找下面列出的七个记号 （指示器的威胁） 的任何。如果找到下列任一操作时，您需要执行的补救步骤。

- 规则危害的指示符
    - 规则操作是要启动的应用程序。
    - 规则引用 EXE、 ZIP 或 URL。
    - 在本地计算机上查找源自 Outlook PID 的新过程开始。
- 自定义窗体的指示符危害 
    - 自定义窗体存在另存为自己的邮件类。
    - 邮件类包含可执行代码。
    - 通常存储在个人窗体库或收件箱文件夹中。
    - IPM 命名表单。请注意。[自定义名称]。

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>查找此类攻击的迹象，并确认它的步骤
您可以使用这两种方法之一来确认攻击。
- 手动检查的规则和使用 Outlook 客户端每个邮箱的表单。 全面，此方法，但只能检查邮箱用户一次可以是非常耗时如果您有很多用户能够检查。 它还会导致的计算机的运行从签违反。
- 使用[Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell 脚本来自动转储转发规则和自定义窗体的所有用户在您的租户中的所有邮件。这是开销的最少最快和最安全的方法。


### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>确认规则攻击使用 Outlook 客户端
1. 用户打开用户的 Outlook 客户端。 用户可能需要检查其邮箱上的规则的帮助。
2. 请参阅[管理电子邮件使用规则](https://support.office.com/en-us/article/manage-email-messages-by-using-rules-c24f5dea-9465-4df4-ad17-a50704d66c59#ID0EAABAAA=2010)文章如何打开规则接口的 Outlook 2007、 2010年或 2013年版本中的过程。
3. 查找未创建用户的规则或任何意外的规则或使用可疑名称的规则。
4. 规则操作的规则说明中查找的开始和应用程序或引用。EXE。ZIP 文件或启动一个 URL。
5. 查找任何新的进程的开始使用 Outlook 进程 id。 请参阅[找到进程 ID](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/finding-the-process-id)。

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>步骤确认表单攻击使用 Outlook 客户端
1. 用户打开用户的 Outlook 客户端。
2. 按照用户的 Outlook 版本中，[显示开发人员选项卡](https://support.office.com/en-us/article/show-the-developer-tab-e1192344-5e56-4d45-931b-e5fd9bea2d45)的步骤。
3. 在 Outlook 中打开现在可见的开发人员选项卡，单击**设计窗体**。
4. 从**查找范围**列表中选择**收件箱**。查找任何自定义表单。 自定义窗体很少，足够，如果您在所有有任何自定义表单，值得深入。
5. 调查任何自定义表单，尤其是标记为隐藏。
6. 打开任何自定义表单，并在**窗体**组中，单击**查看代码**以查看哪些运行时加载窗体。

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>步骤确认使用 PowerShell 规则和窗体攻击
验证规则的最简单方式或自定义窗体攻击是运行[Get AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell 脚本。 此脚本连接到租户中的每个邮箱和转储所有规则和窗体为两个.csv 文件。

#### <a name="pre-requisites"></a>必备组件
您需要具有全局管理员权限运行脚本，因为该脚本连接到租赁读取的规则和窗体中的每个邮箱。

1. 登录到将运行脚本从具有本地管理员权限的计算机。
2. 下载，或将从 GitHub Get AllTenantRulesAndForms.ps1 脚本复制到从中将运行它的文件夹。 该脚本将创建两个日期戳文件添加到此文件夹、 MailboxFormsExport-yyyy-mm-dd.csv 和 MailboxRulesExport yyyy-mm dd.csv。
3. 打开作为管理员的 PowerShell 实例，并打开保存到脚本的文件夹。
4. 运行以下 PowerShell 命令行，如下所示`.\Get-AllTenantRulesAndForms.ps1`.\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>解释输出

MailboxRulesExport-*yyyy-月-日*.csv – 包括应用程序或可执行文件的操作条件检查的规则 （每行一个）。
- ActionType (A 列) – 如果您看到"ID_ACTION_CUSTOM"的值的规则是可能恶意。
- IsPotentiallyMalicious （列 D） – 此值为"TRUE"，该规则是否可能恶意。
- ActionCommand （G 列） – 如果列出应用程序或.exe、.zip 扩展名或 URL，不应存在，是指一个条目具有的任何文件规则很可能恶意。

MailboxFormsExport-*yyyy-月-日*.csv – 一般情况下，使用自定义窗体是很少见。 如果您发现任何此工作簿中，您打开该用户的邮箱，并检查窗体本身。 如果您的组织未不会将该有有意，很可能恶意。



## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>如何停止和修正 Outlook 规则和窗体攻击
如果您发现之一这些攻击的迹象，修正简单，只需从邮箱中删除规则或窗体。您可以与 Outlook 客户端或使用远程 PowerShell 删除规则来执行此操作。

### <a name="using-outlook"></a>使用 Outlook
1. 标识用户有与 Outlook 中使用的所有设备。 所有需要的潜在的恶意软件清除它们。 不允许用户登录并使用电子邮件，直到清除所有设备。
2. 按照每个设备中[删除规则](https://support.office.com/en-us/article/Delete-a-rule-2F0E7139-F696-4422-8498-44846DB9067F)的步骤。
3. 如果您不确定有关其他恶意软件的状态，您可以设置的格式和重新安装在设备上的所有软件。 为移动设备可以按照制造商步骤设备重置为出厂映像。
4. 安装最新版本的 Outlook。 请记住的当前版本的 Outlook 默认情况下阻止两种类型的此类攻击。
5. 已删除的邮箱的所有脱机副本后, 重置用户的密码 （使用一个高质量），并且如果尚未启用 MFA 按照中[为 Office 365 用户设置多因素身份验证](https://support.office.com/en-us/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)的步骤。这样可确保不会通过其他方式 （例如网络钓鱼或密码重新使用） 公开用户的凭据。

### <a name="using-powershell"></a>使用 PowerShell
有两个远程 PowerShell cmdlet 可用于删除或禁用危险的规则。只需遵循的步骤。
 
Exchange 服务器上的邮箱的步骤

1. 连接到 Exchange 服务器使用远程 PowerShell。按照[连接到 Exchange 服务器使用远程 PowerShell](https://docs.microsoft.com/en-us/powershell/exchange/exchange-server/connect-to-exchange-servers-using-remote-powershell?view=exchange-ps)中的步骤。
2. 如果您想要从邮箱使用[Remove-收件箱规则 cmdlet ](https://docs.microsoft.com/en-us/powershell/module/exchange/mailboxes/Remove-InboxRule?view=exchange-ps)-完全删除单个规则、 多个规则或所有规则从邮箱使用完全删除一个，多，对此或所有规则。
3. 如果您想要保留规则，并进一步调查其内容使用[Disable-inboxrule cmdlet](https://technet.microsoft.com/en-us/library/dd298120(v=exchg.160).aspx)。 

Exchange Online 中的邮箱的步骤
1. 按照[连接到 Exchange Online 使用 PowerShell](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps)中的步骤。
2.  如果您想要完全删除单个规则，多个规则或从邮箱的所有规则将使用[Remove-收件箱规则 cmdlet](https://docs.microsoft.com/en-us/powershell/module/exchange/mailboxes/Remove-InboxRule?view=exchange-ps)。
3.  如果您想要保留规则，并进一步调查其内容使用[Disable-inboxrule cmdlet](https://technet.microsoft.com/en-us/library/dd298120(v=exchg.160).aspx)。 

## <a name="how-to-minimize-future-attacks"></a>如何最小化将来攻击

### <a name="first-protect-your-accounts"></a>第一个： 保护您的帐户

已被盗或看见您的用户帐户之一后，攻击者仅使用规则和窗体攻击。因此，防止这些攻击针对您的组织使用第一步是主动保护您的用户帐户。 采用的一些最常见方式帐户被破坏通过网络钓鱼或[密码表面喷](http://www.dabcc.com/microsoft-defending-against-password-spray-attacks/)是攻击。



保护您的用户帐户，并特别是您的管理员帐户的最佳方式是[设置为 Office 365 用户的多因素身份验证](https://support.office.com/en-us/article/set-up-multi-factor-authentication-for-office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)。 您还应该：
<ol>
    <li>监视您的用户帐户是如何<a href="https://docs.microsoft.com/en-us/azure/active-directory/active-directory-view-access-usage-reports">访问和使用</a>。您可能不会防止初始违反，但将更快地检测缩短持续时间和违反的影响。您可以使用这些： <a href="https://support.office.com/en-us/article/overview-of-office-365-cloud-app-security-81f0ee9a-9645-45ab-ba56-de9cbccab475">Office 365 云应用程序安全策略</a>，以监视您的帐户和通知异常活动。<ol type="a">
            <li><b>多个失败的登录尝试次数</b>当用户在相对于学习基线，可能表示尝试的违反单个会话中执行多个失败的登录活动，此策略配置文件您的环境和触发器通知。</li>
            <li><b>Impossible 出差</b>-此策略配置文件环境和两个位置之间的预期的差旅时间比短时间段内的不同位置的同一用户从检测到活动时触发通知。这可能表示其他用户正在使用相同的凭据。检测此异常行为，必须初始学习期期间其学习新的用户活动模式的七天。</li>
            <li><b>发生异常模拟活动 （由用户）</b>-此策略配置文件环境和当用户执行多个模拟的活动相对于基线教训，单个会话中无法指示尝试的违反触发通知。</li>
        </ol>
    </li>
    <li>利用<a href="https://securescore.office.com/">Office 365 安全分数</a>管理帐户的安全配置和行为类似工具。 
    </li>
</ol> 

### <a name="second-keep-your-outlook-clients-current"></a>第二个： 保留您的 Outlook 客户端当前
Outlook 2013 和 2016年完全更新和修补程序版本默认情况下禁用"启动应用程序"规则中的表单操作。 这将确保，即使攻击破坏了帐户，则规则和表单操作将被阻止。 您可以通过[安装 Office 更新](https://support.office.com/en-us/article/Install-Office-updates-2ab296f3-7f03-43a2-8e50-46de917611c5)中的步骤安装最新的更新和安全修补程序。

下面是 Outlook 2013 和 2016年客户端的修补程序版本：
- Outlook 2013: 15.0.4937.1000 或更高版本
- Outlook 2016: 16.0.4534.1001 或更高版本

在各个安全修补程序的详细信息，请参阅：

- [Outlook 2013 安全修补程序](https://support.microsoft.com/en-us/help/3191938) 
- [Outlook 2016 安全修补程序](https://support.microsoft.com/en-us/help/3191883)

### <a name="third-monitor-your-outlook-clients"></a>第三个： 监视您的 Outlook 客户端
请注意，即使使用修补程序和安装更新，则可能攻击者更改本地计算机配置要重新启用"启动应用程序"的行为。[高级组策略管理](https://docs.microsoft.com/en-us/microsoft-desktop-optimization-pack/agpm/)用于监视和强制实施在客户端上的本地计算机策略。  
您可以查看如果"启动应用程序"已被重新启用在注册表中重写通过使用[如何查看系统使用 64 位版本的 Windows 注册表](https://support.microsoft.com/en-us/help/305097/how-to-view-the-system-registry-by-using-64-bit-versions-of-windows)中的信息。 检查这些子项： 

- Outlook 2016: HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\
- Outlook 2013: HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\

查找 EnableUnsafeClientMailRules 键。如果它存在并且设置为 1 时，Outlook 安全修补程序已被重写和计算机就受到窗体中的规则攻击。如果值为 0，则会禁用"启动应用程序"操作。 如果安装 Outlook 的更新和修补程序版本，并且此注册表项不存在，则系统不是很容易受到这些攻击。

内部部署 Exchange 安装的客户应考虑阻止较旧版本的 Outlook 没有可用的修补程序。可以[配置 Outlook 客户端阻止](https://technet.microsoft.com/en-us/library/dd335207(v=exchg.150).aspx)一文中找到此过程的详细信息。

## <a name="secure-office-365-like-a-cybersecurity-pro"></a>像网络专业人员的安全保护 Office 365
Office 365 订阅附带了强大的可用于保护您的数据和用户的安全功能集。 使用[Office 365 安全路线图： Top 优先级的前 30 天，90 天及其他认证实战](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352)实现 Microsoft 建议的用于保护 Office 365 租户的最佳做法。
- 第一个 30 天内完成的任务。 这些没有直接影响，因此低影响到您的用户。
- 若要在 90 天内完成的任务。这些需要更多时间规划和实现但大大提高安全状况。
- 90 天前。在您的第一个 90 天工作中构建这些增强功能。

## <a name="see-also"></a>另请参阅：
- [恶意 Outlook 规则](https://silentbreaksecurity.com/malicious-outlook-rules/)的有关规则向量 SilentBreak 安全文章提供了详细的复查 how Outlook 规则。 
- 有关 Mailrule Pwnage Sensepost 博客上的[MAPI over HTTP 和 Mailrule Pwnage](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/)讨论调用可以利用通过 Outlook 规则的邮箱的标尺的工具。
- [Outlook 窗体和 shells](https://sensepost.com/blog/2017/outlook-forms-and-shells/)有关窗体威胁向量 Sensepost 博客 （英文）。 
- [标尺基本代码](https://github.com/sensepost/ruler)
- [标尺指示符的威胁](https://github.com/sensepost/notruler/blob/master/iocs.md)