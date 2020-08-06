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
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="baf3b-103">修复 Microsoft 365 的目录同步问题</span><span class="sxs-lookup"><span data-stu-id="baf3b-103">Fixing problems with directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="baf3b-104">通过目录同步，你可以继续管理内部部署用户和组，并将添加、删除和更改同步到云。</span><span class="sxs-lookup"><span data-stu-id="baf3b-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="baf3b-105">但设置有点复杂，有时可能很难发现问题根源。</span><span class="sxs-lookup"><span data-stu-id="baf3b-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="baf3b-106">我们提供了各种资源，帮助你识别潜在问题并进行修复。</span><span class="sxs-lookup"><span data-stu-id="baf3b-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="baf3b-107">如何知道是否发生错误？</span><span class="sxs-lookup"><span data-stu-id="baf3b-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="baf3b-108">发生错误的第一个迹象是 Microsoft 365 管理中心的 DirSync 状态磁贴指示存在问题。</span><span class="sxs-lookup"><span data-stu-id="baf3b-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="baf3b-109">你还会收到来自 Microsoft 365 的邮件（发送到备用电子邮件地址和管理员电子邮件地址），指示租户遇到目录同步错误。</span><span class="sxs-lookup"><span data-stu-id="baf3b-109">You will also receive a mail (to the alternate email and to your admin email) from Microsoft 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="baf3b-110">有关详细信息，请参阅[识别 Microsoft 365 中的目录同步错误](identify-directory-synchronization-errors.md)。</span><span class="sxs-lookup"><span data-stu-id="baf3b-110">For details see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="baf3b-111">如何获取 Azure Active Directory Connect 工具？</span><span class="sxs-lookup"><span data-stu-id="baf3b-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="baf3b-112">在 [Microsoft 365 管理中心](https://admin.microsoft.com)，转到“**用户**”\>“**活动用户**”。</span><span class="sxs-lookup"><span data-stu-id="baf3b-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="baf3b-113">单击“**更多**”菜单（三个点），选择“**目录同步**”。</span><span class="sxs-lookup"><span data-stu-id="baf3b-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="baf3b-114">按照[向导中的说明](set-up-directory-synchronization.md)下载 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="baf3b-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="baf3b-115">如果仍然使用 Azure Active Directory (Azure AD) 同步 (DirSync)，请参阅[如何诊断 Microsoft 365 中的 Azure Active Directory 同步工具安装和配置向导错误消息](https://go.microsoft.com/fwlink/p/?LinkId=396717)，了解有关安装 dirsync 的系统要求、所需权限和如何诊断常见错误的信息。</span><span class="sxs-lookup"><span data-stu-id="baf3b-115">If you are still using Azure Active Directory (Azure AD) Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="baf3b-116">若要从 Azure AD Sync 更新到 Azure AD Connect，请参阅[升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。</span><span class="sxs-lookup"><span data-stu-id="baf3b-116">To update from Azure AD Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a><span data-ttu-id="baf3b-117">解决 Microsoft 365 中的目录同步问题的常见原因</span><span class="sxs-lookup"><span data-stu-id="baf3b-117">Resolving common causes of problems with directory synchronization in Microsoft 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="baf3b-118">同步对象未联机显示或更新，或我收到来自服务的同步错误报告。</span><span class="sxs-lookup"><span data-stu-id="baf3b-118">Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.</span></span>

- [<span data-ttu-id="baf3b-119">标识同步和重复的属性复原</span><span class="sxs-lookup"><span data-stu-id="baf3b-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="baf3b-120">我在管理中心收到警报，或收到自动发出的电子邮件，指示最近没有同步事件</span><span class="sxs-lookup"><span data-stu-id="baf3b-120">I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event</span></span>
- [<span data-ttu-id="baf3b-121">使用 Azure AD Connect 对连接问题进行故障排除</span><span class="sxs-lookup"><span data-stu-id="baf3b-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="baf3b-122">Azure AD Connect 帐户和权限</span><span class="sxs-lookup"><span data-stu-id="baf3b-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="baf3b-123">Azure AD Connect 同步：如何管理 Azure AD 服务帐户</span><span class="sxs-lookup"><span data-stu-id="baf3b-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="baf3b-124">到 Azure Active Directory 的目录同步停止，或收到警告，提示超过一天未注册同步</span><span class="sxs-lookup"><span data-stu-id="baf3b-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="baf3b-125">密码哈希未同步，或在管理中心收到警报，指示最近未进行密码哈希同步</span><span class="sxs-lookup"><span data-stu-id="baf3b-125">Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization</span></span>
- [<span data-ttu-id="baf3b-126">使用 Azure AD Connect 同步实施密码哈希同步</span><span class="sxs-lookup"><span data-stu-id="baf3b-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="baf3b-127">我看到一个警报，指示超出对象配额</span><span class="sxs-lookup"><span data-stu-id="baf3b-127">I'm seeing an alert that Object quota exceeded</span></span>
- <span data-ttu-id="baf3b-128">我们具有内置的对象配额以帮助保护服务。</span><span class="sxs-lookup"><span data-stu-id="baf3b-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="baf3b-129">如果你的目录中有太多需要同步到 Microsoft 365 的对象，你必须[联系商业版产品支持部门](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)以增加配额。</span><span class="sxs-lookup"><span data-stu-id="baf3b-129">If you have too many objects in your directory that need to sync to Microsoft 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="baf3b-130">我需要知道同步了哪些属性</span><span class="sxs-lookup"><span data-stu-id="baf3b-130">I need to know which attributes are synchronized</span></span>
- <span data-ttu-id="baf3b-131">你可以[就在这里](https://go.microsoft.com/fwlink/p/?LinkId=396719)找到在本地和云之间同步的所有属性的列表。</span><span class="sxs-lookup"><span data-stu-id="baf3b-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="baf3b-132">我无法管理或删除已同步到云中的对象</span><span class="sxs-lookup"><span data-stu-id="baf3b-132">I can't manage or remove objects that were synchronized to the cloud</span></span>
- <span data-ttu-id="baf3b-133">你是否已准备好仅管理云中的对象？</span><span class="sxs-lookup"><span data-stu-id="baf3b-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="baf3b-134">或者，是否有已在内部部署中删除，但仍滞留在云中的对象？</span><span class="sxs-lookup"><span data-stu-id="baf3b-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="baf3b-135">请查看此[解决同步过程中出现的错误](https://go.microsoft.com/fwlink/p/?linkid=842044)和[支持文章](https://go.microsoft.com/fwlink/p/?LinkId=396720)，获取有关如何解决这些问题的指导。</span><span class="sxs-lookup"><span data-stu-id="baf3b-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="baf3b-136">我收到一条错误消息，指明我的公司已超过可以同步的对象数量</span><span class="sxs-lookup"><span data-stu-id="baf3b-136">I got an error message that my company has exceeded the number of objects that can be synchronized</span></span>
- <span data-ttu-id="baf3b-137">你可以在[此处](https://go.microsoft.com/fwlink/p/?LinkId=396721)阅读有关此问题的详细信息。</span><span class="sxs-lookup"><span data-stu-id="baf3b-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="baf3b-138">其他资源</span><span class="sxs-lookup"><span data-stu-id="baf3b-138">Other resources</span></span>

- [<span data-ttu-id="baf3b-139">用于修复用户主体名称重复的脚本</span><span class="sxs-lookup"><span data-stu-id="baf3b-139">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="baf3b-140">如何准备不可路由域（如 .local 域）进行目录同步</span><span class="sxs-lookup"><span data-stu-id="baf3b-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="baf3b-141">用于计算同步对象总数的脚本</span><span class="sxs-lookup"><span data-stu-id="baf3b-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="baf3b-142">AD FS 2.0 疑难解答</span><span class="sxs-lookup"><span data-stu-id="baf3b-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="baf3b-143">使用 PowerShell 修复启用邮件的组的空 DisplayName 属性</span><span class="sxs-lookup"><span data-stu-id="baf3b-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="baf3b-144">使用 PowerShell 修复 UPN 重复</span><span class="sxs-lookup"><span data-stu-id="baf3b-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="baf3b-145">使用 PowerShell 修复电子邮件地址重复</span><span class="sxs-lookup"><span data-stu-id="baf3b-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
