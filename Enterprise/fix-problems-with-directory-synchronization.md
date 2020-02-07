---
title: 修复 Office 365 的目录同步问题
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
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
description: 介绍了 Office 365 中的目录同步问题的常见原因，并提供了几种帮助排除和解决这些问题的方法。
ms.openlocfilehash: 658f1649d0a4b9bf109bbb35593d4c64092e1cf8
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840329"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="4ac1a-103">修复 Office 365 的目录同步问题</span><span class="sxs-lookup"><span data-stu-id="4ac1a-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="4ac1a-104">通过目录同步，您可以继续管理本地用户和组，并同步对云的添加、删除和更改。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="4ac1a-105">但安装程序有点复杂，有时可能很难确定问题的根源。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="4ac1a-106">我们有一些资源，可帮助你找出潜在问题并解决这些问题。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="4ac1a-107">如何知道是否出现了问题？</span><span class="sxs-lookup"><span data-stu-id="4ac1a-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="4ac1a-108">如果 Microsoft 365 管理中心中的 DirSync 状态磁贴指示存在问题，则第一表明出现了错误。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="4ac1a-109">你还将收到来自 Office 365 的邮件（到备用电子邮件和管理员电子邮件），指示你的租户遇到目录同步错误。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-109">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="4ac1a-110">有关详细信息，请参阅[识别 Office 365 中的目录同步错误](identify-directory-synchronization-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-110">For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="4ac1a-111">如何获取 Azure Active Directory Connect 工具？</span><span class="sxs-lookup"><span data-stu-id="4ac1a-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="4ac1a-112">在[Microsoft 365 管理中心](https://admin.microsoft.com)，导航到 "**用户** \> **活动用户**"。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="4ac1a-113">单击 "**更多**" 菜单（三个点），然后选择 "**目录同步**"。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="4ac1a-114">按照[向导中的说明](set-up-directory-synchronization.md)下载 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="4ac1a-115">如果仍在使用 Azure Active Directory 同步（DirSync），请参阅[如何对 Office 365 中的 Azure Active Directory 同步工具安装和配置向导错误消息进行故障排除](https://go.microsoft.com/fwlink/p/?LinkId=396717)，以了解有关安装目录同步、所需权限以及如何对常见错误进行故障排除的信息。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-115">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="4ac1a-116">若要从 Azure Active Directory 同步更新到 Azure AD Connect，请参阅[升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-116">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="4ac1a-117">解决 Office 365 中的目录同步问题的常见原因</span><span class="sxs-lookup"><span data-stu-id="4ac1a-117">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="4ac1a-118">**同步的对象不会显示或联机更新，或者我将从服务中获取同步错误报告。**</span><span class="sxs-lookup"><span data-stu-id="4ac1a-118">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="4ac1a-119">标识同步和重复属性弹性</span><span class="sxs-lookup"><span data-stu-id="4ac1a-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="4ac1a-120">**我在管理中心发出通知，或者收到最近未进行同步事件的自动电子邮件**</span><span class="sxs-lookup"><span data-stu-id="4ac1a-120">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="4ac1a-121">解决 Azure AD Connect 的连接问题</span><span class="sxs-lookup"><span data-stu-id="4ac1a-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="4ac1a-122">Azure AD Connect 帐户和权限</span><span class="sxs-lookup"><span data-stu-id="4ac1a-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="4ac1a-123">Azure AD Connect sync：如何管理 Azure AD 服务帐户</span><span class="sxs-lookup"><span data-stu-id="4ac1a-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="4ac1a-124">到 Azure Active Directory 的目录同步停止，或者你收到同步未在一天内注册的警告</span><span class="sxs-lookup"><span data-stu-id="4ac1a-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="4ac1a-125">**密码哈希未同步，或者我在管理中心内看到一个警报，表明最近密码哈希同步**</span><span class="sxs-lookup"><span data-stu-id="4ac1a-125">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="4ac1a-126">使用 Azure AD Connect 同步实现密码哈希同步</span><span class="sxs-lookup"><span data-stu-id="4ac1a-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="4ac1a-127">**我看到一个警报，指出对象配额已超出**</span><span class="sxs-lookup"><span data-stu-id="4ac1a-127">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="4ac1a-128">我们有一个内置的对象配额，可帮助保护服务。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="4ac1a-129">如果目录中的对象太多，需要同步到 Office 365，您必须[联系支持人员以获取业务产品](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)，以增加配额。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-129">If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="4ac1a-130">**我需要知道哪些属性是同步的**</span><span class="sxs-lookup"><span data-stu-id="4ac1a-130">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="4ac1a-131">您可以在[此处](https://go.microsoft.com/fwlink/p/?LinkId=396719)找到在内部部署和云之间同步的所有属性的列表。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="4ac1a-132">**我无法管理或删除已同步到云的对象**</span><span class="sxs-lookup"><span data-stu-id="4ac1a-132">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="4ac1a-133">你是否已准备好仅在云中管理对象？</span><span class="sxs-lookup"><span data-stu-id="4ac1a-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="4ac1a-134">或者是否存在本地删除的对象，但它在云中被卡住？</span><span class="sxs-lookup"><span data-stu-id="4ac1a-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="4ac1a-135">请查看同步和[支持文章](https://go.microsoft.com/fwlink/p/?LinkId=396720)中的此[故障排除错误](https://go.microsoft.com/fwlink/p/?linkid=842044)，以获取有关如何解决这些问题的指南。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="4ac1a-136">**我收到一条错误消息，指出我的公司已超出可同步的对象数**</span><span class="sxs-lookup"><span data-stu-id="4ac1a-136">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="4ac1a-137">你可以在[此处](https://go.microsoft.com/fwlink/p/?LinkId=396721)阅读有关此问题的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="4ac1a-138">其他资源</span><span class="sxs-lookup"><span data-stu-id="4ac1a-138">Other resources</span></span>

- [<span data-ttu-id="4ac1a-139">用于修复用户主体名称重复的脚本</span><span class="sxs-lookup"><span data-stu-id="4ac1a-139">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="4ac1a-140">如何为目录同步准备不可路由的域（例如，本地域）</span><span class="sxs-lookup"><span data-stu-id="4ac1a-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="4ac1a-141">计算同步对象总数的脚本</span><span class="sxs-lookup"><span data-stu-id="4ac1a-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="4ac1a-142">AD FS 2.0 故障排除</span><span class="sxs-lookup"><span data-stu-id="4ac1a-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="4ac1a-143">使用 PowerShell 为已启用邮件的组修复空的 DisplayName 属性</span><span class="sxs-lookup"><span data-stu-id="4ac1a-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="4ac1a-144">使用 PowerShell 修复重复的 UPN</span><span class="sxs-lookup"><span data-stu-id="4ac1a-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="4ac1a-145">使用 PowerShell 修复重复的电子邮件地址</span><span class="sxs-lookup"><span data-stu-id="4ac1a-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="4ac1a-146">诊断工具</span><span class="sxs-lookup"><span data-stu-id="4ac1a-146">Diagnostic tools</span></span>

<span data-ttu-id="4ac1a-147">[IDFix 工具](prepare-directory-attributes-for-synch-with-idfix.md)用于在准备迁移到 Office 365 时，在本地 Active Directory 环境中执行 identity 对象及其属性的发现和修正。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-147">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365.</span></span> <span data-ttu-id="4ac1a-148">IDFix 适用于负责与 Office 365 服务进行目录同步的 Active Directory 管理员。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-148">IDFix is intended for the Active Directory administrators responsible for directory synchronization with the Office 365 service.</span></span> 

<span data-ttu-id="4ac1a-149">从 Microsoft 下载中心[下载 IDFix 工具](https://go.microsoft.com/fwlink/p/?LinkId=396718)。</span><span class="sxs-lookup"><span data-stu-id="4ac1a-149">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>