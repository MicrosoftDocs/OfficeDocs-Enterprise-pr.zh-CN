---
title: 修复 Office 365 的目录同步问题
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: 介绍了 Office 365 中的目录同步问题的常见原因，并提供了几种帮助排除和解决这些问题的方法。
ms.openlocfilehash: cc0fe15d0d49542489ac1e586efbe99d0846b3ab
ms.sourcegitcommit: fbd2f3fb297c508212baed3ee9d1ce51765cc8bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/25/2019
ms.locfileid: "39254521"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>修复 Office 365 的目录同步问题

通过目录同步，您可以继续管理本地用户和组，并同步对云的添加、删除和更改。 但安装程序有点复杂，有时可能很难确定问题的根源。 我们有一些资源，可帮助你找出潜在问题并解决这些问题。
  
## <a name="how-do-i-know-if-something-is-wrong"></a>如何知道是否出现了问题？

如果 Microsoft 365 管理中心中的 DirSync 状态磁贴指示存在问题，则第一表明出现了错误。
  
你还将收到来自 Office 365 的邮件（到备用电子邮件和管理员电子邮件），指示你的租户遇到目录同步错误。 有关详细信息，请参阅[识别 Office 365 中的目录同步错误](identify-directory-synchronization-errors.md)。
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>如何获取 Azure Active Directory Connect 工具？

在[Microsoft 365 管理中心](https://admin.microsoft.com)，导航到 "**用户** \> **活动用户**"。 单击 "**更多**" 菜单（三个点），然后选择 "**目录同步**"。 
  
按照[向导中的说明](set-up-directory-synchronization.md)下载 Azure AD Connect。 
  
如果仍在使用 Azure Active Directory 同步（DirSync），请参阅[如何对 Office 365 中的 Azure Active Directory 同步工具安装和配置向导错误消息进行故障排除](https://go.microsoft.com/fwlink/p/?LinkId=396717)，以了解有关安装目录同步、所需权限以及如何对常见错误进行故障排除的信息。 
  
若要从 Azure Active Directory 同步更新到 Azure AD Connect，请参阅[升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>解决 Office 365 中的目录同步问题的常见原因

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**同步的对象不会显示或联机更新，或者我将从服务中获取同步错误报告。**

- [标识同步和重复属性弹性](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**我在管理中心发出通知，或者收到最近未进行同步事件的自动电子邮件**
- [解决 Azure AD Connect 的连接问题](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect 帐户和权限](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD Connect sync：如何管理 Azure AD 服务帐户](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [到 Azure Active Directory 的目录同步停止，或者你收到同步未在一天内注册的警告](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**密码哈希未同步，或者我在管理中心内看到一个警报，表明最近密码哈希同步**
- [使用 Azure AD Connect 同步实现密码哈希同步](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**我看到一个警报，指出对象配额已超出**
- 我们有一个内置的对象配额，可帮助保护服务。 如果目录中的对象太多，需要同步到 Office 365，您必须[联系支持人员以获取业务产品](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)，以增加配额。

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**我需要知道哪些属性是同步的**
- 您可以在[此处](https://go.microsoft.com/fwlink/p/?LinkId=396719)找到在内部部署和云之间同步的所有属性的列表。

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**我无法管理或删除已同步到云的对象**
- 你是否已准备好仅在云中管理对象？ 或者是否存在本地删除的对象，但它在云中被卡住？ 请查看同步和[支持文章](https://go.microsoft.com/fwlink/p/?LinkId=396720)中的此[故障排除错误](https://go.microsoft.com/fwlink/p/?linkid=842044)，以获取有关如何解决这些问题的指南。

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**我收到一条错误消息，指出我的公司已超出可同步的对象数**
- 你可以在[此处](https://go.microsoft.com/fwlink/p/?LinkId=396721)阅读有关此问题的详细信息。
   
## <a name="other-resources"></a>其他资源

- [用于修复用户主体名称重复的脚本](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [如何为目录同步准备不可路由的域（例如，本地域）](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [计算同步对象总数的脚本](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [AD FS 2.0 故障排除](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [使用 PowerShell 为已启用邮件的组修复空的 DisplayName 属性](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [使用 PowerShell 修复重复的 UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [使用 PowerShell 修复重复的电子邮件地址](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>诊断工具

[IDFix 工具](prepare-directory-attributes-for-synch-with-idfix.md)用于在准备迁移到 Office 365 时，在本地 Active Directory 环境中执行 identity 对象及其属性的发现和修正。 IDFix 适用于负责与 Office 365 服务进行目录同步的 Active Directory 管理员。 

从 Microsoft 下载中心[下载 IDFix 工具](https://go.microsoft.com/fwlink/p/?LinkId=396718)。