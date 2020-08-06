---
title: 修复 Microsoft 365 的目录同步问题
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Priority
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: 介绍 Office 365 中目录同步问题的常见原因，并提供一些方法帮助进行故障诊断和解决这些问题。
ms.openlocfilehash: faf0f061b8f2798054e63f3338b8076c0ec88f73
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "46570965"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>修复 Microsoft 365 的目录同步问题

通过目录同步，你可以继续管理内部部署用户和组，并将添加、删除和更改同步到云。 但设置有点复杂，有时可能很难发现问题根源。 我们提供了各种资源，帮助你识别潜在问题并进行修复。
  
## <a name="how-do-i-know-if-something-is-wrong"></a>如何知道是否发生错误？

发生错误的第一个迹象是 Microsoft 365 管理中心的 DirSync 状态磁贴指示存在问题。
  
你还会收到来自 Microsoft 365 的邮件（发送到备用电子邮件地址和管理员电子邮件地址），指示租户遇到目录同步错误。 有关详细信息，请参阅[识别 Microsoft 365 中的目录同步错误](identify-directory-synchronization-errors.md)。
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>如何获取 Azure Active Directory Connect 工具？

在 [Microsoft 365 管理中心](https://admin.microsoft.com)，转到“**用户**”\>“**活动用户**”。 单击“**更多**”菜单（三个点），选择“**目录同步**”。 
  
按照[向导中的说明](set-up-directory-synchronization.md)下载 Azure AD Connect。 
  
如果仍然使用 Azure Active Directory (Azure AD) 同步 (DirSync)，请参阅[如何诊断 Microsoft 365 中的 Azure Active Directory 同步工具安装和配置向导错误消息](https://go.microsoft.com/fwlink/p/?LinkId=396717)，了解有关安装 dirsync 的系统要求、所需权限和如何诊断常见错误的信息。 
  
若要从 Azure AD Sync 更新到 Azure AD Connect，请参阅[升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>解决 Microsoft 365 中的目录同步问题的常见原因

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>同步对象未联机显示或更新，或我收到来自服务的同步错误报告。

- [标识同步和重复的属性复原](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>我在管理中心收到警报，或收到自动发出的电子邮件，指示最近没有同步事件
- [使用 Azure AD Connect 对连接问题进行故障排除](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect 帐户和权限](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD Connect 同步：如何管理 Azure AD 服务帐户](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [到 Azure Active Directory 的目录同步停止，或收到警告，提示超过一天未注册同步](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>密码哈希未同步，或在管理中心收到警报，指示最近未进行密码哈希同步
- [使用 Azure AD Connect 同步实施密码哈希同步](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>我看到一个警报，指示超出对象配额
- 我们具有内置的对象配额以帮助保护服务。 如果你的目录中有太多需要同步到 Microsoft 365 的对象，你必须[联系商业版产品支持部门](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)以增加配额。

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>我需要知道同步了哪些属性
- 你可以[就在这里](https://go.microsoft.com/fwlink/p/?LinkId=396719)找到在本地和云之间同步的所有属性的列表。

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>我无法管理或删除已同步到云中的对象
- 你是否已准备好仅管理云中的对象？ 或者，是否有已在内部部署中删除，但仍滞留在云中的对象？ 请查看此[解决同步过程中出现的错误](https://go.microsoft.com/fwlink/p/?linkid=842044)和[支持文章](https://go.microsoft.com/fwlink/p/?LinkId=396720)，获取有关如何解决这些问题的指导。

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>我收到一条错误消息，指明我的公司已超过可以同步的对象数量
- 你可以在[此处](https://go.microsoft.com/fwlink/p/?LinkId=396721)阅读有关此问题的详细信息。
   
## <a name="other-resources"></a>其他资源

- [用于修复用户主体名称重复的脚本](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [如何准备不可路由域（如 .local 域）进行目录同步](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [用于计算同步对象总数的脚本](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [AD FS 2.0 疑难解答](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [使用 PowerShell 修复启用邮件的组的空 DisplayName 属性](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [使用 PowerShell 修复 UPN 重复](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [使用 PowerShell 修复电子邮件地址重复](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
