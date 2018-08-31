---
title: 修复 Office 365 的目录同步问题
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
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
ms.openlocfilehash: ad3b6e27439354a2ede9b1a4b100e0f9e06148d3
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539604"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="255f8-103">修复 Office 365 的目录同步问题</span><span class="sxs-lookup"><span data-stu-id="255f8-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="255f8-p101">通过目录同步，您可以继续管理用户和组内部部署和同步添加、 删除或更改到云中。安装程序有点复杂，但它有时可能很难确定问题的根源。我们有资源可帮助您识别潜在问题和解决这些问题。</span><span class="sxs-lookup"><span data-stu-id="255f8-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="255f8-107">如何知道是否有问题？</span><span class="sxs-lookup"><span data-stu-id="255f8-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="255f8-108">在 Office 365 管理中心中的目录同步状态平铺指示问题时出错的第一个提示：</span><span class="sxs-lookup"><span data-stu-id="255f8-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![目录同步状态平铺在管理中心预览](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="255f8-p102">您还将指示您的租户遇到目录同步错误的 Office 365 中收到邮件 （到备选电子邮件和管理电子邮件）。有关详细信息，请参阅[Office 365 中的标识目录同步错误](identify-directory-synchronization-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="255f8-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="255f8-112">如何获取 Azure Active Directory 连接工具？</span><span class="sxs-lookup"><span data-stu-id="255f8-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="255f8-p103">在 Office 365 管理中心中，导航到 * * 用户 * * \> **活动用户**。单击**详细**菜单并选择**目录同步**。</span><span class="sxs-lookup"><span data-stu-id="255f8-p103">In the Office 365 admin center, navigate to ** Users ** \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![在详细菜单中，选择目录同步](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="255f8-116">在旧的 Office 365 管理中心，导航到**用户** \> **活动用户**，并选择**设置** **Active Directory 同步**旁边。</span><span class="sxs-lookup"><span data-stu-id="255f8-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![选择设置 Active Directory 同步旁边](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="255f8-118">按照[向导中的说明](set-up-directory-synchronization.md)下载 Azure AD 连接。</span><span class="sxs-lookup"><span data-stu-id="255f8-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="255f8-119">如果您仍在使用 Azure Active Directory 同步 (DirSync)，看看[如何解决 Azure Active Directory 同步工具安装和配置向导在 Office 365 中的错误消息](https://go.microsoft.com/fwlink/p/?LinkId=396717)有关安装的系统要求的信息目录同步、 所需，权限和如何解决常见错误。</span><span class="sxs-lookup"><span data-stu-id="255f8-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="255f8-120">若要从 Azure Active Directory 同步更新到 Azure AD 连接，请参阅[的升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。</span><span class="sxs-lookup"><span data-stu-id="255f8-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="255f8-121">Office 365 中目录同步问题的解决常见原因</span><span class="sxs-lookup"><span data-stu-id="255f8-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="255f8-122">**同步的对象不显示或联机，更新或从服务都得到同步错误报告。**</span><span class="sxs-lookup"><span data-stu-id="255f8-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="255f8-123">标识同步和重复属性恢复能力</span><span class="sxs-lookup"><span data-stu-id="255f8-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=798300)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="255f8-124">**我在 Office 365 管理中心中，有通知或我接到尚未被新的同步事件的自动电子邮件**</span><span class="sxs-lookup"><span data-stu-id="255f8-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="255f8-125">解决与 Azure AD 连接的连接问题</span><span class="sxs-lookup"><span data-stu-id="255f8-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820597)
- [<span data-ttu-id="255f8-126">Azure AD 连接帐户和权限</span><span class="sxs-lookup"><span data-stu-id="255f8-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="255f8-127">Azure AD 连接同步： 如何管理 Azure AD 服务帐户</span><span class="sxs-lookup"><span data-stu-id="255f8-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820599)
- [<span data-ttu-id="255f8-128">目录同步到 Azure Active Directory 停止或您正在同步不起作用注册多个一天中收到警告</span><span class="sxs-lookup"><span data-stu-id="255f8-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="255f8-129">**密码哈希值不同步，或我能看到不起作用已最新的密码哈希同步在 Office 365 管理中心内通知**</span><span class="sxs-lookup"><span data-stu-id="255f8-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="255f8-130">实现与 Azure AD 连接同步的密码哈希同步</span><span class="sxs-lookup"><span data-stu-id="255f8-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820600)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="255f8-131">**我能看到一条警报，超出对象配额**</span><span class="sxs-lookup"><span data-stu-id="255f8-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="255f8-p104">我们有内置对象配额以帮助保护本服务。如果您有太多的对象，您需要同步到 Office 365 的目录中，您必须对[业务产品支持的联系人](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)以增加配额。</span><span class="sxs-lookup"><span data-stu-id="255f8-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="255f8-134">**我需要知道哪些属性已同步**</span><span class="sxs-lookup"><span data-stu-id="255f8-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="255f8-135">您可以找到所有内部部署和云[此处](https://go.microsoft.com/fwlink/p/?LinkId=396719)之间同步的属性的列表。</span><span class="sxs-lookup"><span data-stu-id="255f8-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="255f8-136">**我无法管理或删除已同步到云的对象**</span><span class="sxs-lookup"><span data-stu-id="255f8-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="255f8-p105">是否已准备好管理中仅限云对象？或者是存在的对象已删除内部部署，但在云中陷入？了解一下此[同步过程中解决错误](https://go.microsoft.com/fwlink/p/?linkid=842044)和指南[支持文章](https://go.microsoft.com/fwlink/p/?LinkId=396720)如何解决这些问题。</span><span class="sxs-lookup"><span data-stu-id="255f8-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="255f8-140">**当公司超过可同步的对象数量时，收到错误消息。**</span><span class="sxs-lookup"><span data-stu-id="255f8-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="255f8-141">您可以阅读更多有关此问题[此处](https://go.microsoft.com/fwlink/p/?LinkId=396721)。</span><span class="sxs-lookup"><span data-stu-id="255f8-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="255f8-142">其他资源</span><span class="sxs-lookup"><span data-stu-id="255f8-142">Other resources</span></span>

- [<span data-ttu-id="255f8-143">脚本以修复重复用户主体名称</span><span class="sxs-lookup"><span data-stu-id="255f8-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="255f8-144">如何准备目录同步非可路由域 （如.local 域）</span><span class="sxs-lookup"><span data-stu-id="255f8-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="255f8-145">脚本来计算总同步的对象</span><span class="sxs-lookup"><span data-stu-id="255f8-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="255f8-146">排除 AD FS 2.0</span><span class="sxs-lookup"><span data-stu-id="255f8-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="255f8-147">使用 PowerShell 修复启用邮件的组的空 DisplayName 属性</span><span class="sxs-lookup"><span data-stu-id="255f8-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="255f8-148">使用 PowerShell 修复重复 UPN</span><span class="sxs-lookup"><span data-stu-id="255f8-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="255f8-149">使用 PowerShell 修复重复电子邮件地址</span><span class="sxs-lookup"><span data-stu-id="255f8-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="255f8-150">诊断工具</span><span class="sxs-lookup"><span data-stu-id="255f8-150">Diagnostic tools</span></span>

<span data-ttu-id="255f8-p106">[IDFix 工具](prepare-directory-attributes-for-synch-with-idfix.md)用于在迁移到 Office 365 准备本地 Active Directory 环境中执行发现和修复标识对象及其属性。IDFix 适用于负责与 Office 365 服务目录同步的 Active Directory 管理员。</span><span class="sxs-lookup"><span data-stu-id="255f8-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="255f8-153">从 Microsoft 下载中心下载[下载 IDFix 工具](https://go.microsoft.com/fwlink/p/?LinkId=396718)。</span><span class="sxs-lookup"><span data-stu-id="255f8-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>