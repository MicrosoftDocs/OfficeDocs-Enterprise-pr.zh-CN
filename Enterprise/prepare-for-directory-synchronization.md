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
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 介绍如何准备以设置到 Office 365 的用户使用目录同步和使用此方法的长期优势。
ms.openlocfilehash: 8e84f4602b79ce321cd9a71e6c35331baf40f7f0
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371116"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="46286-103">准备通过目录同步到 Office 365 来设置用户</span><span class="sxs-lookup"><span data-stu-id="46286-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="46286-p101">设置目录同步的用户需要更多的规划和准备比只需管理您直接在 Office 365 中的工作或学校的帐户。其他规划和准备任务所需确保您的本地 Active Directory 同步正确到 Azure Active Directory。添加到您的组织优点包括：</span><span class="sxs-lookup"><span data-stu-id="46286-p101">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365. The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory. The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="46286-107">减少了组织中的管理程序</span><span class="sxs-lookup"><span data-stu-id="46286-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="46286-108">（可选） 启用单一登录方案</span><span class="sxs-lookup"><span data-stu-id="46286-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="46286-109">在 Office 365 中自动执行帐户的更改</span><span class="sxs-lookup"><span data-stu-id="46286-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="46286-110">有关使用目录同步的优点的详细信息，请参阅[目录同步路线图]( https://go.microsoft.com/fwlink/p/?LinkId=525398)和[了解 Office 365 标识和 Azure Active Directory](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="46286-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="46286-111">若要确定您的组织的最佳方案，请查看[目录集成工具比较](https://go.microsoft.com/fwlink/p/?LinkId=525320)。</span><span class="sxs-lookup"><span data-stu-id="46286-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="46286-112">目录清理任务</span><span class="sxs-lookup"><span data-stu-id="46286-112">Directory cleanup tasks</span></span>

<span data-ttu-id="46286-113">在开始同步您的目录之前，您需要清理您的目录。</span><span class="sxs-lookup"><span data-stu-id="46286-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="46286-114">查看还[属性同步到 Azure Active Directory 的 Azure AD 连接](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)。</span><span class="sxs-lookup"><span data-stu-id="46286-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="46286-p102">如果您不执行目录清理同步之前，，可以显著负面影响的部署过程。它可能需要数天，或几周内，通过目录同步，确定错误，以及重新同步周期。</span><span class="sxs-lookup"><span data-stu-id="46286-p102">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process. It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="46286-117">在您的本地目录中，完成以下清理任务：</span><span class="sxs-lookup"><span data-stu-id="46286-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="46286-118">确保每个将分配有 Office 365 服务的用户都在 **proxyAddresses** 属性中具有有效的唯一电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="46286-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="46286-119">删除 **proxyAddresses** 属性中所有重复的值。</span><span class="sxs-lookup"><span data-stu-id="46286-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="46286-p103">如果可能，请确保每个用户都将分配给 Office 365 服务产品的用户的**用户**对象中具有**userPrincipalName**属性的有效且唯一值。为了最佳同步体验，请确保在本地 Active Directory UPN 与云 UPN 匹配。如果用户不具有**userPrincipalName**属性的值，**用户**对象必须包含**sAMAccountName**属性的有效且唯一值。**UserPrincipalName**属性中删除任何重复值。</span><span class="sxs-lookup"><span data-stu-id="46286-p103">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object. For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN. If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute. Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="46286-124">为了更好地使用全局地址列表 (GAL)，请确保下列属性中的信息正确：</span><span class="sxs-lookup"><span data-stu-id="46286-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="46286-125">givenName </span><span class="sxs-lookup"><span data-stu-id="46286-125">givenName</span></span>
  - <span data-ttu-id="46286-126">姓氏</span><span class="sxs-lookup"><span data-stu-id="46286-126">surname</span></span>
  - <span data-ttu-id="46286-127">displayName</span><span class="sxs-lookup"><span data-stu-id="46286-127">displayName</span></span>
  - <span data-ttu-id="46286-128">职务</span><span class="sxs-lookup"><span data-stu-id="46286-128">Job Title</span></span>
  - <span data-ttu-id="46286-129">部门</span><span class="sxs-lookup"><span data-stu-id="46286-129">Department</span></span>
  - <span data-ttu-id="46286-130">办公室</span><span class="sxs-lookup"><span data-stu-id="46286-130">Office</span></span>
  - <span data-ttu-id="46286-131">办公室电话</span><span class="sxs-lookup"><span data-stu-id="46286-131">Office Phone</span></span>
  - <span data-ttu-id="46286-132">移动电话</span><span class="sxs-lookup"><span data-stu-id="46286-132">Mobile Phone</span></span>
  - <span data-ttu-id="46286-133">传真号码</span><span class="sxs-lookup"><span data-stu-id="46286-133">Fax Number</span></span>
  - <span data-ttu-id="46286-134">街道地址</span><span class="sxs-lookup"><span data-stu-id="46286-134">Street Address</span></span>
  - <span data-ttu-id="46286-135">城市</span><span class="sxs-lookup"><span data-stu-id="46286-135">City</span></span>
  - <span data-ttu-id="46286-136">省/市/自治区</span><span class="sxs-lookup"><span data-stu-id="46286-136">State or Province</span></span>
  - <span data-ttu-id="46286-137">邮政编码</span><span class="sxs-lookup"><span data-stu-id="46286-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="46286-138">国家或地区</span><span class="sxs-lookup"><span data-stu-id="46286-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="46286-139">目录对象和属性的准备</span><span class="sxs-lookup"><span data-stu-id="46286-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="46286-p104">您的本地目录和 Office 365 之间的成功的目录同步需要您的本地目录属性正确准备好。例如，您需要确保在与 Office 365 环境同步的某些属性中不使用的特定字符。意外的字符不会导致目录同步失败，但可能返回一条警告。无效字符将导致目录同步失败。</span><span class="sxs-lookup"><span data-stu-id="46286-p104">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared. For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment. Unexpected characters do not cause directory synchronization to fail but might return a warning. Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="46286-p105">如果您的 Active Directory 用户的一些具有一个或多个重复属性，也将失败目录同步。每个用户必须拥有唯一的属性。</span><span class="sxs-lookup"><span data-stu-id="46286-p105">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes. Each user must have unique attributes.</span></span>
  
<span data-ttu-id="46286-146">下面列出了您需要准备的属性：</span><span class="sxs-lookup"><span data-stu-id="46286-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="46286-147">**注意：** 您还可以使用[IdFix 工具](install-and-run-idfix.md)以使此过程容易得多。</span><span class="sxs-lookup"><span data-stu-id="46286-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="46286-148">**displayName**</span><span class="sxs-lookup"><span data-stu-id="46286-148">**displayName**</span></span>
    
  - <span data-ttu-id="46286-149">如果该属性存在于用户对象中，它会与 Office 365 进行同步。</span><span class="sxs-lookup"><span data-stu-id="46286-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="46286-p106">如果此属性在用户对象中，就必须有一个对应它的值。也就是说，该属性不能为空。</span><span class="sxs-lookup"><span data-stu-id="46286-p106">If this attribute exists in the user object, there must be a value for it. That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="46286-152">最大字符数：256</span><span class="sxs-lookup"><span data-stu-id="46286-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="46286-153">\*\*givenName \*\*</span><span class="sxs-lookup"><span data-stu-id="46286-153">**givenName**</span></span>
    
  - <span data-ttu-id="46286-154">如果该属性在用户对象中，它会与 Office 365 同步，但 Office 365 并不需要或使用它。</span><span class="sxs-lookup"><span data-stu-id="46286-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="46286-155">最大字符数：64</span><span class="sxs-lookup"><span data-stu-id="46286-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="46286-156">**mail**</span><span class="sxs-lookup"><span data-stu-id="46286-156">**mail**</span></span>
    
  - <span data-ttu-id="46286-157">在目录中，属性值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="46286-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="46286-p107">如果有重复值，将同步的第一个用户的值。后续的用户不会出现在 Office 365。您必须修改 Office 365 中的值或修改同时为这两个用户在 Office 365 中显示的顺序中的本地目录中的值。</span><span class="sxs-lookup"><span data-stu-id="46286-p107">If there are duplicate values, the first user with the value is synchronized. Subsequent users will not appear in Office 365. You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="46286-161">**mailNickname**（Exchange 别名）</span><span class="sxs-lookup"><span data-stu-id="46286-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="46286-162">属性值不能以句点 （.） 开头。</span><span class="sxs-lookup"><span data-stu-id="46286-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="46286-163">在目录中，属性值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="46286-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="46286-164">\*\*proxyAddresses \*\*</span><span class="sxs-lookup"><span data-stu-id="46286-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="46286-165">多值属性</span><span class="sxs-lookup"><span data-stu-id="46286-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="46286-166">每个值的最大字符数：256</span><span class="sxs-lookup"><span data-stu-id="46286-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="46286-167">属性值不能包含空格。</span><span class="sxs-lookup"><span data-stu-id="46286-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="46286-168">在目录中，属性值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="46286-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="46286-169">无效字符： \< \> （);, [ ] "</span><span class="sxs-lookup"><span data-stu-id="46286-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="46286-170">请注意无效字符，用于关注类型分隔符的字符和":"，以便允许 SMTP:User@contso.com，但不是 SMTP:user:M@contoso.com。</span><span class="sxs-lookup"><span data-stu-id="46286-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="46286-p108">所有简单邮件传输协议 (SMTP) 地址都应符合电子邮件消息标准。如果存在重复或不需要的地址，请参阅帮助主题[Exchange 中删除重复的和不必要的代理地址](https://go.microsoft.com/fwlink/?LinkId=293860)。</span><span class="sxs-lookup"><span data-stu-id="46286-p108">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards. If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="46286-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="46286-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="46286-174">最大字符数：20</span><span class="sxs-lookup"><span data-stu-id="46286-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="46286-175">在目录中，属性值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="46286-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="46286-p109">无效字符: [\"|，/: \< \> + =;？\* ]</span><span class="sxs-lookup"><span data-stu-id="46286-p109">Invalid characters: [ \ " | , / : \< \> + = ; ? \* ]</span></span>
  - <span data-ttu-id="46286-178">如果用户具有无效 **sAMAccountName** 属性，但具有有效 **userPrincipalName** 属性，则在 Office 365 中创建用户帐户。</span><span class="sxs-lookup"><span data-stu-id="46286-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="46286-179">如果**sAMAccountName**和**userprincipalname 属性**均无效，则必须更新本地 Active Directory **userPrincipalName**属性。</span><span class="sxs-lookup"><span data-stu-id="46286-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="46286-180">**sn**（姓氏）</span><span class="sxs-lookup"><span data-stu-id="46286-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="46286-181">如果该属性在用户对象中，它会与 Office 365 同步，但 Office 365 并不需要或使用它。</span><span class="sxs-lookup"><span data-stu-id="46286-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="46286-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="46286-182">**targetAddress**</span></span>
    
    <span data-ttu-id="46286-p110">需要填充用户的**targetAddress**属性 (例如，SMTP:tom@contoso.com) 必须出现在 Office 365 GAL。在第三方消息迁移方案中，这将需要为内部部署目录的 Office 365 架构扩展。Office 365 架构扩展还将添加其他有用的属性，用于管理 Office 365 对象使用目录同步工具从内部部署目录进行填充。例如，将添加**msExchHideFromAddressLists**属性来管理隐藏的邮箱或通讯组。</span><span class="sxs-lookup"><span data-stu-id="46286-p110">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL. In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory. The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory. For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="46286-187">最大字符数：256</span><span class="sxs-lookup"><span data-stu-id="46286-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="46286-188">属性值不能包含空格。</span><span class="sxs-lookup"><span data-stu-id="46286-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="46286-189">在目录中，属性值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="46286-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="46286-190">无效字符: \ \< \> （);, [ ] "</span><span class="sxs-lookup"><span data-stu-id="46286-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="46286-191">所有简单邮件传输协议 (SMTP) 地址都应符合电子邮件消息标准。</span><span class="sxs-lookup"><span data-stu-id="46286-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="46286-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="46286-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="46286-p111">**UserPrincipalName**属性必须是格式为 Internet 风格登录用户名后跟 at 符号 (@) 和域名： 例如，user@contoso.com。所有简单邮件传输协议 (SMTP) 地址都应符合电子邮件消息标准。</span><span class="sxs-lookup"><span data-stu-id="46286-p111">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com. All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="46286-p112">**userPrincipalName** 属性的最大字符数是 113。允许在 at 符号 (@) 的前后使用一定数量的字符，如下所示：</span><span class="sxs-lookup"><span data-stu-id="46286-p112">The maximum number of characters for the **userPrincipalName** attribute is 113. A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="46286-197">at 符号 (@) 前用户名的最大字符数：64</span><span class="sxs-lookup"><span data-stu-id="46286-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="46286-198">at 符号 (@) 后域名的最大字符数：48</span><span class="sxs-lookup"><span data-stu-id="46286-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="46286-p113">无效字符: \ % &amp; \* + / =？{ } |\< \> ( ) ;: , [ ] "</span><span class="sxs-lookup"><span data-stu-id="46286-p113">Invalid characters: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "</span></span>
  - <span data-ttu-id="46286-201">Umlaut 也是无效的字符。</span><span class="sxs-lookup"><span data-stu-id="46286-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="46286-202">每个**userPrincipalName**值中都需要 @ 符。</span><span class="sxs-lookup"><span data-stu-id="46286-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="46286-203">@ 符在每个 **userPrincipalName** 值中不能作为第一个字符。</span><span class="sxs-lookup"><span data-stu-id="46286-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="46286-204">用户名不能以句点 （.）、 & 符号结尾 (&amp;)、 空格或 at 符号 (@)。</span><span class="sxs-lookup"><span data-stu-id="46286-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="46286-205">用户名中不能包含任何空格。</span><span class="sxs-lookup"><span data-stu-id="46286-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="46286-206">必须使用可路由域;例如，不能使用本地域或内部域。</span><span class="sxs-lookup"><span data-stu-id="46286-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="46286-207">Unicode 将转换为下划线字符。</span><span class="sxs-lookup"><span data-stu-id="46286-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="46286-208">在目录中，**userPrincipalName** 不能包含任何重复值。</span><span class="sxs-lookup"><span data-stu-id="46286-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="46286-209">准备 userPrincipalName 属性</span><span class="sxs-lookup"><span data-stu-id="46286-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="46286-p114">Active Directory 旨在允许组织使用**sAMAccountName**或**userPrincipalName**登录到您的目录中的最终用户。同样，最终用户可以使用其工作的用户主体名称 (UPN) 登录到 Office 365 或学校帐户。目录同步将尝试使用位于您的本地目录中的同一 UPN 在 Azure Active Directory 中创建新用户。UPN 的格式与电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="46286-p114">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**. Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account. Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory. The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="46286-p115">在 Office 365 UPN 是用于生成的电子邮件地址的默认属性。可以轻松获取**userPrincipalName** (内部部署和 Azure Active Directory 中) 和**proxyAddresses**设置为不同的值中的主电子邮件地址。时被设置为不同的值可以是为管理员和最终用户的混乱。</span><span class="sxs-lookup"><span data-stu-id="46286-p115">In Office 365, the UPN is the default attribute that's used to generate the email address. It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values. When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="46286-p116">最好对齐这些属性，以减少了混淆情况。以满足要求的单一登录与 Active Directory 联合身份验证服务 (AD FS) 2.0，您需要确保在 Azure Active Directory 和您的本地 Active Directory 中的 Upn 匹配项，并使用有效的域命名空间。</span><span class="sxs-lookup"><span data-stu-id="46286-p116">It's best to align these attributes to reduce confusion. To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="46286-219">向 AD DS 添加备用 UPN 后缀</span><span class="sxs-lookup"><span data-stu-id="46286-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="46286-p117">您可能需要添加备用 UPN 后缀，以将用户的企业凭据与 Office 365 环境相关联。UPN 后缀属于右侧的 UPN @ 符。字母、 数字、 阶段、 短划线，和下划线，但没有其他类型的字符，可以包含用于单一登录的 Upn。</span><span class="sxs-lookup"><span data-stu-id="46286-p117">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment. A UPN suffix is the part of a UPN to the right of the @ character. UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="46286-223">有关如何向 Active Directory 添加备用 UPN 后缀的详细信息，请参阅[准备进行目录同步]( https://go.microsoft.com/fwlink/p/?LinkId=525430)。</span><span class="sxs-lookup"><span data-stu-id="46286-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="46286-224">匹配的内部部署 UPN 与 Office 365 UPN</span><span class="sxs-lookup"><span data-stu-id="46286-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="46286-p118">如果您已经设置了目录同步，Office 365 的用户的 UPN 可能不匹配的本地目录服务中定义的用户的内部部署 UPN。用户已分配了许可证的之前已验证域时会发生该错误。若要解决此问题，使用[PowerShell 修复重复 UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730)更新以确保 Office 365 UPN 匹配的公司的用户名和域的用户的 UPN。如果您要更新的本地目录服务中的 UPN，并且想要其 identity 为 Azure Active Directory 同步，您需要进行更改本地之前在 Office 365 中删除用户的许可证。</span><span class="sxs-lookup"><span data-stu-id="46286-p118">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service. This can occur when a user was assigned a license before the domain was verified. To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain. If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="46286-229">请参阅[如何准备进行目录同步非可路由域 （如.local 域）](prepare-a-non-routable-domain-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="46286-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="46286-230">目录集成工具</span><span class="sxs-lookup"><span data-stu-id="46286-230">Directory integration tools</span></span>

<span data-ttu-id="46286-p119">目录同步的目录对象 （用户、 组和联系人） 的本地 Active Directory 环境中到 Office 365 的目录基础结构，Azure Active Directory 同步。可用工具和其功能的列表，请参阅[目录集成工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)。推荐的工具是[Microsoft Azure Active Directory 连接](https://go.microsoft.com/fwlink/p/?LinkID=510956)。Azure Active Directory 连接的详细信息，请参阅[将您的本地标识与 Azure Active Directory 集成](https://go.microsoft.com/fwlink/p/?LinkId=527969)。</span><span class="sxs-lookup"><span data-stu-id="46286-p119">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory. See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="46286-p120">当用户帐户与 Office 365 目录同步的第一次时，它们标记为未激活。他们无法发送或接收电子邮件、 和它们不使用订阅许可证。时便可以分配给特定用户的 Office 365 订阅，必须选择并激活这些由[分配给为企业的 Office 365 中的用户的许可证](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。</span><span class="sxs-lookup"><span data-stu-id="46286-p120">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="46286-p121">您还可以使用[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097)将许可证分配。自动化解决方案，请参阅[如何使用 PowerShell 将许可证自动分配给您的 Office 365 用户](https://go.microsoft.com/fwlink/p?LinkID=329805)。</span><span class="sxs-lookup"><span data-stu-id="46286-p121">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses. See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>