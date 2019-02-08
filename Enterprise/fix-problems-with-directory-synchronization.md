---
title: 修复 Office 365 的目录同步问题
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: 介绍 Office 365 中目录同步问题的常见原因并提供一些方法，以帮助用户排除和解决这些问题。
ms.openlocfilehash: 2d567daa370d651a6eb9180db2f729d09b380226
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897305"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>修复 Office 365 的目录同步问题

通过目录同步，您可以继续管理用户和组内部部署和同步添加、 删除或更改到云中。安装程序有点复杂，但它有时可能很难确定问题的根源。我们有资源可帮助您识别潜在问题和解决这些问题。
  
## <a name="how-do-i-know-if-something-is-wrong"></a>如何知道是否有问题？

在 Office 365 管理中心中的目录同步状态平铺指示问题时出错的第一个提示：
  
![目录同步状态平铺在管理中心预览](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
您还将指示您的租户遇到目录同步错误的 Office 365 中收到邮件 （到备选电子邮件和管理电子邮件）。有关详细信息，请参阅[Office 365 中的标识目录同步错误](identify-directory-synchronization-errors.md)。
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>如何获取 Azure Active Directory 连接工具？

在 Office 365 管理中心中，导航到 * * 用户 * * \> **活动用户**。单击**详细**菜单并选择**目录同步**。 
  
![在详细菜单中，选择目录同步](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
在旧的 Office 365 管理中心，导航到**用户** \> **活动用户**，并选择**设置** **Active Directory 同步**旁边。 
  
![选择设置 Active Directory 同步旁边](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
按照[向导中的说明](set-up-directory-synchronization.md)下载 Azure AD 连接。 
  
如果您仍在使用 Azure Active Directory 同步 (DirSync)，看看[如何解决 Azure Active Directory 同步工具安装和配置向导在 Office 365 中的错误消息](https://go.microsoft.com/fwlink/p/?LinkId=396717)有关安装的系统要求的信息目录同步、 所需，权限和如何解决常见错误。 
  
若要从 Azure Active Directory 同步更新到 Azure AD 连接，请参阅[的升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Office 365 中目录同步问题的解决常见原因

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**同步的对象不显示或联机，更新或从服务都得到同步错误报告。**

- [标识同步和重复属性恢复能力](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**我在 Office 365 管理中心中，有通知或我接到尚未被新的同步事件的自动电子邮件**
- [解决与 Azure AD 连接的连接问题](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD 连接帐户和权限](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD 连接同步： 如何管理 Azure AD 服务帐户](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [目录同步到 Azure Active Directory 停止或您正在同步不起作用注册多个一天中收到警告](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**密码哈希值不同步，或我能看到不起作用已最新的密码哈希同步在 Office 365 管理中心内通知**
- [实现与 Azure AD 连接同步的密码哈希同步](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**我能看到一条警报，超出对象配额**
- 我们有内置对象配额以帮助保护本服务。如果您有太多的对象，您需要同步到 Office 365 的目录中，您必须对[业务产品支持的联系人](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)以增加配额。

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**我需要知道哪些属性已同步**
- 您可以找到所有内部部署和云[此处](https://go.microsoft.com/fwlink/p/?LinkId=396719)之间同步的属性的列表。

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**我无法管理或删除已同步到云的对象**
- 是否已准备好管理中仅限云对象？或者是存在的对象已删除内部部署，但在云中陷入？了解一下此[同步过程中解决错误](https://go.microsoft.com/fwlink/p/?linkid=842044)和指南[支持文章](https://go.microsoft.com/fwlink/p/?LinkId=396720)如何解决这些问题。

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**当公司超过可同步的对象数量时，收到错误消息。**
- 您可以阅读更多有关此问题[此处](https://go.microsoft.com/fwlink/p/?LinkId=396721)。
   
## <a name="other-resources"></a>其他资源

- [用于修复用户主体名称重复的脚本](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [如何准备目录同步非可路由域 （如.local 域）](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [脚本来计算总同步的对象](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [排除 AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [使用 PowerShell 修复启用邮件的组的空 DisplayName 属性](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [使用 PowerShell 修复重复 UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [使用 PowerShell 修复重复电子邮件地址](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>诊断工具

[IDFix 工具](prepare-directory-attributes-for-synch-with-idfix.md)用于在迁移到 Office 365 准备本地 Active Directory 环境中执行发现和修复标识对象及其属性。IDFix 适用于负责与 Office 365 服务目录同步的 Active Directory 管理员。 

从 Microsoft 下载中心下载[下载 IDFix 工具](https://go.microsoft.com/fwlink/p/?LinkId=396718)。