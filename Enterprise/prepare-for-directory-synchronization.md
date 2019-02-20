---
title: 准备通过目录同步到 Office 365 来设置用户
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 介绍如何准备使用目录同步将用户预配到 Office 365, 以及使用此方法的长期好处。
ms.openlocfilehash: af402950b3681285898d0d87b897d363a693bf98
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085101"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="4157c-103">准备通过目录同步到 Office 365 来设置用户</span><span class="sxs-lookup"><span data-stu-id="4157c-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="4157c-p101">与在 Office 365 中直接管理工作或学校帐户相比, 使用目录同步设置用户需要进行更多的规划和准备。需要执行其他规划和准备任务, 以确保您的内部部署 active directory 正确同步到 Azure Active directory。为您的组织增加的好处包括:</span><span class="sxs-lookup"><span data-stu-id="4157c-p101">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365. The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory. The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="4157c-107">减少了组织中的管理程序</span><span class="sxs-lookup"><span data-stu-id="4157c-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="4157c-108">(可选) 启用单一登录方案</span><span class="sxs-lookup"><span data-stu-id="4157c-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="4157c-109">在 Office 365 中自动执行帐户的更改</span><span class="sxs-lookup"><span data-stu-id="4157c-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="4157c-110">有关使用目录同步的优势的详细信息, 请参阅[目录同步路线图]( https://go.microsoft.com/fwlink/p/?LinkId=525398)和[了解 Office 365 标识和 Azure Active directory](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="4157c-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="4157c-111">若要确定哪种方案最适合您的组织, 请查看[目录集成工具比较](https://go.microsoft.com/fwlink/p/?LinkId=525320)。</span><span class="sxs-lookup"><span data-stu-id="4157c-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="4157c-112">目录清理任务</span><span class="sxs-lookup"><span data-stu-id="4157c-112">Directory cleanup tasks</span></span>

<span data-ttu-id="4157c-113">在开始同步您的目录之前, 需要清理您的目录。</span><span class="sxs-lookup"><span data-stu-id="4157c-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="4157c-114">另请查看[azure AD Connect 同步到 azure Active Directory 的属性](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)。</span><span class="sxs-lookup"><span data-stu-id="4157c-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="4157c-p102">如果在同步之前不执行目录清理, 则部署过程可能会产生严重的负面影响。可能需要数天甚至数周才能完成目录同步的循环、识别错误和重新同步。</span><span class="sxs-lookup"><span data-stu-id="4157c-p102">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process. It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="4157c-117">在您的本地目录中, 完成以下清理任务:</span><span class="sxs-lookup"><span data-stu-id="4157c-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="4157c-118">确保每个将分配有 Office 365 服务的用户都在 **proxyAddresses** 属性中具有有效的唯一电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="4157c-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="4157c-119">删除 **proxyAddresses** 属性中所有重复的值。</span><span class="sxs-lookup"><span data-stu-id="4157c-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="4157c-p103">如果可能, 请确保将为其分配 Office 365 服务的每个用户都具有用户**用户**对象中的**userPrincipalName**属性的有效且唯一的值。为了获得最佳同步体验, 请确保本地 Active Directory UPN 与云 UPN 相匹配。如果用户不具有**userPrincipalName**属性的值, 则**user**对象必须包含**sAMAccountName**属性的有效且唯一的值。删除**userPrincipalName**属性中的任何重复值。</span><span class="sxs-lookup"><span data-stu-id="4157c-p103">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object. For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN. If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute. Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="4157c-124">为了更好地使用全局地址列表 (GAL)，请确保下列属性中的信息正确：</span><span class="sxs-lookup"><span data-stu-id="4157c-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="4157c-125">givenName </span><span class="sxs-lookup"><span data-stu-id="4157c-125">givenName</span></span>
  - <span data-ttu-id="4157c-126">姓氏</span><span class="sxs-lookup"><span data-stu-id="4157c-126">surname</span></span>
  - <span data-ttu-id="4157c-127">displayName</span><span class="sxs-lookup"><span data-stu-id="4157c-127">displayName</span></span>
  - <span data-ttu-id="4157c-128">职务</span><span class="sxs-lookup"><span data-stu-id="4157c-128">Job Title</span></span>
  - <span data-ttu-id="4157c-129">部门</span><span class="sxs-lookup"><span data-stu-id="4157c-129">Department</span></span>
  - <span data-ttu-id="4157c-130">办公室</span><span class="sxs-lookup"><span data-stu-id="4157c-130">Office</span></span>
  - <span data-ttu-id="4157c-131">办公室电话</span><span class="sxs-lookup"><span data-stu-id="4157c-131">Office Phone</span></span>
  - <span data-ttu-id="4157c-132">移动电话</span><span class="sxs-lookup"><span data-stu-id="4157c-132">Mobile Phone</span></span>
  - <span data-ttu-id="4157c-133">传真号码</span><span class="sxs-lookup"><span data-stu-id="4157c-133">Fax Number</span></span>
  - <span data-ttu-id="4157c-134">街道地址</span><span class="sxs-lookup"><span data-stu-id="4157c-134">Street Address</span></span>
  - <span data-ttu-id="4157c-135">城市</span><span class="sxs-lookup"><span data-stu-id="4157c-135">City</span></span>
  - <span data-ttu-id="4157c-136">省/市/自治区</span><span class="sxs-lookup"><span data-stu-id="4157c-136">State or Province</span></span>
  - <span data-ttu-id="4157c-137">邮政编码</span><span class="sxs-lookup"><span data-stu-id="4157c-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="4157c-138">国家或地区</span><span class="sxs-lookup"><span data-stu-id="4157c-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="4157c-139">目录对象和属性的准备</span><span class="sxs-lookup"><span data-stu-id="4157c-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="4157c-p104">您的本地目录和 Office 365 之间的成功目录同步要求您的本地目录属性已正确准备就绪。例如, 您需要确保在与 Office 365 环境同步的某些属性中不使用特定的字符。意外字符不会导致目录同步失败, 但可能会返回警告。无效字符将导致目录同步失败。</span><span class="sxs-lookup"><span data-stu-id="4157c-p104">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared. For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment. Unexpected characters do not cause directory synchronization to fail but might return a warning. Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="4157c-p105">如果某些 Active Directory 用户具有一个或多个重复的属性, 则目录同步也会失败。每个用户都必须具有唯一的属性。</span><span class="sxs-lookup"><span data-stu-id="4157c-p105">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes. Each user must have unique attributes.</span></span>
  
<span data-ttu-id="4157c-146">您需要准备的属性如下所示:</span><span class="sxs-lookup"><span data-stu-id="4157c-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="4157c-147">**注意:** 您还可以使用[IdFix 工具](install-and-run-idfix.md), 使此过程变得更加轻松。</span><span class="sxs-lookup"><span data-stu-id="4157c-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="4157c-148">**displayName**</span><span class="sxs-lookup"><span data-stu-id="4157c-148">**displayName**</span></span>
    
  - <span data-ttu-id="4157c-149">如果该属性存在于用户对象中，它会与 Office 365 进行同步。</span><span class="sxs-lookup"><span data-stu-id="4157c-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="4157c-p106">如果此属性在用户对象中，就必须有一个对应它的值。也就是说，该属性不能为空。</span><span class="sxs-lookup"><span data-stu-id="4157c-p106">If this attribute exists in the user object, there must be a value for it. That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="4157c-152">最大字符数：256</span><span class="sxs-lookup"><span data-stu-id="4157c-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="4157c-153">\*\*givenName \*\*</span><span class="sxs-lookup"><span data-stu-id="4157c-153">**givenName**</span></span>
    
  - <span data-ttu-id="4157c-154">如果该属性在用户对象中，它会与 Office 365 同步，但 Office 365 并不需要或使用它。</span><span class="sxs-lookup"><span data-stu-id="4157c-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="4157c-155">最大字符数：64</span><span class="sxs-lookup"><span data-stu-id="4157c-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="4157c-156">**mail**</span><span class="sxs-lookup"><span data-stu-id="4157c-156">**mail**</span></span>
    
  - <span data-ttu-id="4157c-157">在目录中，属性值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4157c-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="4157c-p107">如果存在重复值, 则将同步第一个值为的用户。随后的用户将不会出现在 Office 365 中。您必须修改 office 365 中的值, 或修改本地目录中的两个值, 以使两个用户都显示在 office 365 中。</span><span class="sxs-lookup"><span data-stu-id="4157c-p107">If there are duplicate values, the first user with the value is synchronized. Subsequent users will not appear in Office 365. You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="4157c-161">**mailNickname**（Exchange 别名）</span><span class="sxs-lookup"><span data-stu-id="4157c-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="4157c-162">属性值不能以句点 (.) 开头。</span><span class="sxs-lookup"><span data-stu-id="4157c-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="4157c-163">在目录中，属性值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4157c-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="4157c-164">\*\*proxyAddresses \*\*</span><span class="sxs-lookup"><span data-stu-id="4157c-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="4157c-165">多值属性</span><span class="sxs-lookup"><span data-stu-id="4157c-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="4157c-166">每个值的最大字符数：256</span><span class="sxs-lookup"><span data-stu-id="4157c-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="4157c-167">属性值不能包含空格。</span><span class="sxs-lookup"><span data-stu-id="4157c-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="4157c-168">在目录中，属性值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4157c-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="4157c-169">无效字符: \< \> ();, [ ] "</span><span class="sxs-lookup"><span data-stu-id="4157c-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="4157c-170">请注意, 无效字符适用于类型分隔符后面的字符和 ":", 因此允许 SMTP:User@contso.com, 但 SMTP:user:M@contoso.com 不是。</span><span class="sxs-lookup"><span data-stu-id="4157c-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="4157c-p108">所有简单邮件传输协议 (SMTP) 地址都应遵守电子邮件邮件传递标准。如果存在重复或不需要的地址, 请参阅帮助主题[删除 Exchange 中的重复和不需要的代理地址](https://go.microsoft.com/fwlink/?LinkId=293860)。</span><span class="sxs-lookup"><span data-stu-id="4157c-p108">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards. If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="4157c-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="4157c-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="4157c-174">最大字符数：20</span><span class="sxs-lookup"><span data-stu-id="4157c-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="4157c-175">在目录中，属性值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4157c-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="4157c-p109">无效字符: [\ "|,/: \< \> + =;？\* ]</span><span class="sxs-lookup"><span data-stu-id="4157c-p109">Invalid characters: [ \ " | , / : \< \> + = ; ? \* ]</span></span>
  - <span data-ttu-id="4157c-178">如果用户具有无效 **sAMAccountName** 属性，但具有有效 **userPrincipalName** 属性，则在 Office 365 中创建用户帐户。</span><span class="sxs-lookup"><span data-stu-id="4157c-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="4157c-179">如果**sAMAccountName**和**userPrincipalName**都无效, 则必须更新内部部署 Active Directory **userPrincipalName**属性。</span><span class="sxs-lookup"><span data-stu-id="4157c-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="4157c-180">**sn**（姓氏）</span><span class="sxs-lookup"><span data-stu-id="4157c-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="4157c-181">如果该属性在用户对象中，它会与 Office 365 同步，但 Office 365 并不需要或使用它。</span><span class="sxs-lookup"><span data-stu-id="4157c-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="4157c-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="4157c-182">**targetAddress**</span></span>
    
    <span data-ttu-id="4157c-p110">需要为用户填充的**targetAddress**属性 (例如, SMTP:tom@contoso.com) 必须出现在 Office 365 GAL 中。在第三方邮件迁移方案中, 这将需要本地目录的 Office 365 架构扩展。office 365 架构扩展还将添加其他有用的属性来管理 Office 365 对象, 这些对象是使用本地目录中的目录同步工具填充的。例如, 将添加用于管理隐藏邮箱或通讯组的**msExchHideFromAddressLists**属性。</span><span class="sxs-lookup"><span data-stu-id="4157c-p110">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL. In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory. The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory. For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="4157c-187">最大字符数：256</span><span class="sxs-lookup"><span data-stu-id="4157c-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="4157c-188">属性值不能包含空格。</span><span class="sxs-lookup"><span data-stu-id="4157c-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="4157c-189">在目录中，属性值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4157c-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="4157c-190">无效字符: \ \< \> ();, [ ] "</span><span class="sxs-lookup"><span data-stu-id="4157c-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="4157c-191">所有简单邮件传输协议 (SMTP) 地址都应符合电子邮件消息标准。</span><span class="sxs-lookup"><span data-stu-id="4157c-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="4157c-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="4157c-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="4157c-p111">**userPrincipalName**属性必须为 Internet 样式的登录格式, 其中用户名后跟 "at" 符号 (@) 和域名: 例如, user@contoso.com。所有简单邮件传输协议 (SMTP) 地址都应遵守电子邮件邮件传递标准。</span><span class="sxs-lookup"><span data-stu-id="4157c-p111">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com. All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="4157c-p112">**userPrincipalName** 属性的最大字符数是 113。允许在 at 符号 (@) 的前后使用一定数量的字符，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4157c-p112">The maximum number of characters for the **userPrincipalName** attribute is 113. A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="4157c-197">at 符号 (@) 前用户名的最大字符数：64</span><span class="sxs-lookup"><span data-stu-id="4157c-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="4157c-198">at 符号 (@) 后域名的最大字符数：48</span><span class="sxs-lookup"><span data-stu-id="4157c-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="4157c-p113">无效字符: \% &amp; \* +/=？{ } |\< \> ( ) ;: , [ ] "</span><span class="sxs-lookup"><span data-stu-id="4157c-p113">Invalid characters: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "</span></span>
  - <span data-ttu-id="4157c-201">元音变音符也是一个无效字符。</span><span class="sxs-lookup"><span data-stu-id="4157c-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="4157c-202">每个**userPrincipalName**值中都需要 @ 字符。</span><span class="sxs-lookup"><span data-stu-id="4157c-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="4157c-203">@ 符在每个 **userPrincipalName** 值中不能作为第一个字符。</span><span class="sxs-lookup"><span data-stu-id="4157c-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="4157c-204">用户名不能以句点 (.)、与号 (&amp;)、空格或 at 符号 (@) 结尾。</span><span class="sxs-lookup"><span data-stu-id="4157c-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="4157c-205">用户名中不能包含任何空格。</span><span class="sxs-lookup"><span data-stu-id="4157c-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="4157c-206">必须使用可路由的域;例如, 不能使用本地或内部域。</span><span class="sxs-lookup"><span data-stu-id="4157c-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="4157c-207">Unicode 将转换为下划线字符。</span><span class="sxs-lookup"><span data-stu-id="4157c-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="4157c-208">在目录中，**userPrincipalName** 不能包含任何重复值。</span><span class="sxs-lookup"><span data-stu-id="4157c-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="4157c-209">准备 userPrincipalName 属性</span><span class="sxs-lookup"><span data-stu-id="4157c-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="4157c-p114">Active Directory 旨在允许组织中的最终用户使用**sAMAccountName**或**userPrincipalName**登录到您的目录。同样, 最终用户可以使用其工作或学校帐户的用户主体名称 (UPN) 登录 Office 365。目录同步尝试使用本地目录中的同一 UPN 在 Azure Active Directory 中创建新用户。UPN 的格式类似于电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="4157c-p114">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**. Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account. Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory. The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="4157c-p115">在 Office 365 中, UPN 是用于生成电子邮件地址的默认属性。很容易获取**userPrincipalName** (内部部署和 Azure Active Directory 中) 和**proxyAddresses**中的主电子邮件地址设置为不同的值。当它们设置为不同的值时, 管理员和最终用户可能会感到困惑。</span><span class="sxs-lookup"><span data-stu-id="4157c-p115">In Office 365, the UPN is the default attribute that's used to generate the email address. It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values. When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="4157c-p116">最好对齐这些属性以减少混淆。若要满足使用 Active Directory 联合身份验证服务 (AD FS) 2.0 的单一登录要求, 您需要确保 Azure active directory 和内部部署 Active directory 中的 upn 匹配, 并且使用的是有效的域命名空间。</span><span class="sxs-lookup"><span data-stu-id="4157c-p116">It's best to align these attributes to reduce confusion. To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="4157c-219">向 AD DS 添加备用 UPN 后缀</span><span class="sxs-lookup"><span data-stu-id="4157c-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="4157c-p117">您可能需要添加其他 UPN 后缀以将用户的公司凭据与 Office 365 环境相关联。upn 后缀是 upn 在 @ 字符右侧的部分。用于单一登录的 upn 可以包含字母、数字、句点、短划线和下划线, 但不能包含其他类型的字符。</span><span class="sxs-lookup"><span data-stu-id="4157c-p117">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment. A UPN suffix is the part of a UPN to the right of the @ character. UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="4157c-223">有关如何将其他 UPN 后缀添加到 Active Directory 的详细信息, 请参阅[Prepare for Directory 同步]( https://go.microsoft.com/fwlink/p/?LinkId=525430)。</span><span class="sxs-lookup"><span data-stu-id="4157c-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="4157c-224">将本地 UPN 与 Office 365 UPN 匹配</span><span class="sxs-lookup"><span data-stu-id="4157c-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="4157c-p118">如果已设置目录同步, 则用户的 Office 365 upn 可能与本地目录服务中定义的用户本地 upn 不匹配。在对域进行验证之前分配了许可证时, 可能会发生这种情况。若要解决此问题, 请使用[PowerShell 修复重复的 upn](https://go.microsoft.com/fwlink/p/?LinkId=396730)以更新用户的 upn, 以确保 Office 365 UPN 与公司用户名和域相匹配。如果要在本地目录服务中更新 UPN, 并希望它与 Azure Active directory 标识同步, 则需要先删除 Office 365 中的用户许可证, 然后再进行本地更改。</span><span class="sxs-lookup"><span data-stu-id="4157c-p118">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service. This can occur when a user was assigned a license before the domain was verified. To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain. If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="4157c-229">另请参阅[如何为目录同步准备不可路由的域 (例如, 本地域)](prepare-a-non-routable-domain-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="4157c-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="4157c-230">目录集成工具</span><span class="sxs-lookup"><span data-stu-id="4157c-230">Directory integration tools</span></span>

<span data-ttu-id="4157c-p119">目录同步是将目录对象 (用户、组和联系人) 从本地 Active directory 环境同步到 Office 365 目录基础结构 (Azure Active directory)。有关可用工具及其功能的列表, 请参阅[目录集成工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)。推荐的工具是[Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956)。有关 azure active directory Connect 的详细信息, 请参阅[将本地标识与 Azure active directory 集成](https://go.microsoft.com/fwlink/p/?LinkId=527969)。</span><span class="sxs-lookup"><span data-stu-id="4157c-p119">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory. See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="4157c-p120">当用户帐户首次与 Office 365 目录同步时, 它们将被标记为 "未激活"。他们不能发送或接收电子邮件, 也不会使用订阅许可证。当您准备好将 office 365 订阅分配给特定用户时, 您必须通过向[Office 365 for business 中的用户分配许可证](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)来选择并激活这些订阅。</span><span class="sxs-lookup"><span data-stu-id="4157c-p120">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="4157c-p121">您还可以使用[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097)分配许可证。有关自动解决方案, 请参阅[如何使用 PowerShell 自动将许可证分配给 Office 365 用户](https://go.microsoft.com/fwlink/p?LinkID=329805)。</span><span class="sxs-lookup"><span data-stu-id="4157c-p121">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses. See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>