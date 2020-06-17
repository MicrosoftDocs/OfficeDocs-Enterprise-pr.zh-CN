---
title: 准备将目录同步到 Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: 介绍如何通过使用此方法来准备将用户预配到 Microsoft 365 （使用目录同步）和长期优点。
ms.openlocfilehash: 2a4b5f54d7b5aafd5e5eb7a43859e49caa57a519
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735690"
---
# <a name="prepare-for-directory-synchronization-to-microsoft-365"></a><span data-ttu-id="c34b3-103">准备将目录同步到 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c34b3-103">Prepare for directory synchronization to Microsoft 365</span></span>

<span data-ttu-id="c34b3-104">*本文适用于 Microsoft 365 企业版和 Microsoft 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="c34b3-104">*This article applies to both Microsoft 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="c34b3-105">您的组织的混合标识和目录同步的好处包括：</span><span class="sxs-lookup"><span data-stu-id="c34b3-105">The benefits to hybrid identity and directory synchronization your organization include:</span></span>
  
- <span data-ttu-id="c34b3-106">减少组织中的管理程序</span><span class="sxs-lookup"><span data-stu-id="c34b3-106">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="c34b3-107">（可选）启用单一登录方案</span><span class="sxs-lookup"><span data-stu-id="c34b3-107">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="c34b3-108">在 Microsoft 365 中自动执行帐户更改</span><span class="sxs-lookup"><span data-stu-id="c34b3-108">Automating account changes in Microsoft 365</span></span>
    
<span data-ttu-id="c34b3-109">有关使用目录同步的优势的详细信息，请参阅 Microsoft 365 的[目录同步路线图]( https://go.microsoft.com/fwlink/p/?LinkId=525398)和[混合标识](plan-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="c34b3-109">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Hybrid identity for Microsoft 365](plan-for-directory-synchronization.md).</span></span>

<span data-ttu-id="c34b3-110">但是，目录同步需要进行规划和准备，以确保您的 Active Directory 域服务（AD DS）同步到 Microsoft 365 订阅的 Azure Active Directory （Azure AD）租户，其中至少有错误。</span><span class="sxs-lookup"><span data-stu-id="c34b3-110">However, directory synchronization requires planning and preparation to ensure that your Active Directory Domain Services (AD DS) synchronizes to the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription with a minimum of errors.</span></span> 

<span data-ttu-id="c34b3-111">请按照以下步骤操作，以获得最佳效果。</span><span class="sxs-lookup"><span data-stu-id="c34b3-111">Follow these steps in order for the best results.</span></span>
  
## <a name="1-directory-cleanup-tasks"></a><span data-ttu-id="c34b3-112">1. 目录清理任务</span><span class="sxs-lookup"><span data-stu-id="c34b3-112">1. Directory cleanup tasks</span></span>

<span data-ttu-id="c34b3-113">在将 AD DS 同步到 Azure AD 租户之前，需要清理 AD DS。</span><span class="sxs-lookup"><span data-stu-id="c34b3-113">Before you synchronize your AD DS to your Azure AD tenant, you need to clean up your AD DS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c34b3-114">如果在同步之前不执行 AD DS 清理，则部署过程可能会产生严重的负面影响。</span><span class="sxs-lookup"><span data-stu-id="c34b3-114">If you don't perform AD DS cleanup before you synchronize, there can be a significant negative effect on the deployment process.</span></span> <span data-ttu-id="c34b3-115">可能需要数天甚至数周才能完成目录同步的循环、识别错误和重新同步。</span><span class="sxs-lookup"><span data-stu-id="c34b3-115">It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="c34b3-116">在 AD DS 中，为每个要分配了 Microsoft 365 许可证的用户帐户完成以下清理任务：</span><span class="sxs-lookup"><span data-stu-id="c34b3-116">In your AD DS, complete the following clean-up tasks for each user account that will be assigned a Microsoft 365 license:</span></span>
  
1. <span data-ttu-id="c34b3-117">确保**proxyAddresses**属性中有一个有效且唯一的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="c34b3-117">Ensure a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
  
2. <span data-ttu-id="c34b3-118">删除**proxyAddresses**属性中的任何重复值。</span><span class="sxs-lookup"><span data-stu-id="c34b3-118">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="c34b3-119">如果可能，请确保用户的**用户**对象中的**userPrincipalName**属性具有有效且唯一的值。</span><span class="sxs-lookup"><span data-stu-id="c34b3-119">If possible, ensure a valid and unique value for the **userPrincipalName** attribute in the user's **user** object.</span></span> <span data-ttu-id="c34b3-120">为了获得最佳同步体验，请确保 AD DS UPN 与 Azure AD UPN 相匹配。</span><span class="sxs-lookup"><span data-stu-id="c34b3-120">For the best synchronization experience, ensure that the AD DS UPN matches the Azure AD UPN.</span></span> <span data-ttu-id="c34b3-121">如果用户不具有**userPrincipalName**属性的值，则**user**对象必须包含**sAMAccountName**属性的有效且唯一的值。</span><span class="sxs-lookup"><span data-stu-id="c34b3-121">If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute.</span></span> <span data-ttu-id="c34b3-122">删除**userPrincipalName**属性中的任何重复值。</span><span class="sxs-lookup"><span data-stu-id="c34b3-122">Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="c34b3-123">若要优化全局地址列表（GAL）的使用，请确保 AD DS 用户帐户的以下属性中的信息正确：</span><span class="sxs-lookup"><span data-stu-id="c34b3-123">For optimal use of the global address list (GAL), ensure the information in the following attributes of the AD DS user account is correct:</span></span>
    
  - <span data-ttu-id="c34b3-124">givenName</span><span class="sxs-lookup"><span data-stu-id="c34b3-124">givenName</span></span>
  - <span data-ttu-id="c34b3-125">surname</span><span class="sxs-lookup"><span data-stu-id="c34b3-125">surname</span></span>
  - <span data-ttu-id="c34b3-126">displayName</span><span class="sxs-lookup"><span data-stu-id="c34b3-126">displayName</span></span>
  - <span data-ttu-id="c34b3-127">职务</span><span class="sxs-lookup"><span data-stu-id="c34b3-127">Job Title</span></span>
  - <span data-ttu-id="c34b3-128">部门</span><span class="sxs-lookup"><span data-stu-id="c34b3-128">Department</span></span>
  - <span data-ttu-id="c34b3-129">办公室</span><span class="sxs-lookup"><span data-stu-id="c34b3-129">Office</span></span>
  - <span data-ttu-id="c34b3-130">办公室电话</span><span class="sxs-lookup"><span data-stu-id="c34b3-130">Office Phone</span></span>
  - <span data-ttu-id="c34b3-131">移动电话</span><span class="sxs-lookup"><span data-stu-id="c34b3-131">Mobile Phone</span></span>
  - <span data-ttu-id="c34b3-132">传真号码</span><span class="sxs-lookup"><span data-stu-id="c34b3-132">Fax Number</span></span>
  - <span data-ttu-id="c34b3-133">街道地址</span><span class="sxs-lookup"><span data-stu-id="c34b3-133">Street Address</span></span>
  - <span data-ttu-id="c34b3-134">City</span><span class="sxs-lookup"><span data-stu-id="c34b3-134">City</span></span>
  - <span data-ttu-id="c34b3-135">省/自治区/直辖市</span><span class="sxs-lookup"><span data-stu-id="c34b3-135">State or Province</span></span>
  - <span data-ttu-id="c34b3-136">邮政编码</span><span class="sxs-lookup"><span data-stu-id="c34b3-136">Zip or Postal Code</span></span>
  - <span data-ttu-id="c34b3-137">国家或地区</span><span class="sxs-lookup"><span data-stu-id="c34b3-137">Country or Region</span></span>
    
## <a name="2-directory-object-and-attribute-preparation"></a><span data-ttu-id="c34b3-138">2. 目录对象和属性准备</span><span class="sxs-lookup"><span data-stu-id="c34b3-138">2. Directory object and attribute preparation</span></span>

<span data-ttu-id="c34b3-139">AD DS 和 Microsoft 365 之间的目录同步成功需要正确准备 AD DS 属性。</span><span class="sxs-lookup"><span data-stu-id="c34b3-139">Successful directory synchronization between your AD DS and Microsoft 365 requires that your AD DS attributes are properly prepared.</span></span> <span data-ttu-id="c34b3-140">例如，您需要确保在与 Microsoft 365 环境同步的某些属性中不使用特定字符。</span><span class="sxs-lookup"><span data-stu-id="c34b3-140">For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Microsoft 365 environment.</span></span> <span data-ttu-id="c34b3-141">意外字符不会导致目录同步失败，但可能会返回警告。</span><span class="sxs-lookup"><span data-stu-id="c34b3-141">Unexpected characters do not cause directory synchronization to fail but might return a warning.</span></span> <span data-ttu-id="c34b3-142">无效字符将导致目录同步失败。</span><span class="sxs-lookup"><span data-stu-id="c34b3-142">Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="c34b3-143">如果某些 AD DS 用户具有一个或多个重复的属性，则目录同步也会失败。</span><span class="sxs-lookup"><span data-stu-id="c34b3-143">Directory synchronization will also fail if some of your AD DS users have one or more duplicate attributes.</span></span> <span data-ttu-id="c34b3-144">每个用户都必须具有唯一的属性。</span><span class="sxs-lookup"><span data-stu-id="c34b3-144">Each user must have unique attributes.</span></span>
  
<span data-ttu-id="c34b3-145">您需要准备的属性如下所示：</span><span class="sxs-lookup"><span data-stu-id="c34b3-145">The attributes that you need to prepare are listed here:</span></span>
  
- <span data-ttu-id="c34b3-146">**displayName**</span><span class="sxs-lookup"><span data-stu-id="c34b3-146">**displayName**</span></span>
    
  - <span data-ttu-id="c34b3-147">如果该属性存在于用户对象中，它将与 Microsoft 365 同步。</span><span class="sxs-lookup"><span data-stu-id="c34b3-147">If the attribute exists in the user object, it will be synchronized with Microsoft 365.</span></span>
  - <span data-ttu-id="c34b3-148">如果此属性存在于 user 对象中，则它必须具有值。</span><span class="sxs-lookup"><span data-stu-id="c34b3-148">If this attribute exists in the user object, there must be a value for it.</span></span> <span data-ttu-id="c34b3-149">也就是说，属性不得为空。</span><span class="sxs-lookup"><span data-stu-id="c34b3-149">That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="c34b3-150">最大字符数：256</span><span class="sxs-lookup"><span data-stu-id="c34b3-150">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="c34b3-151">**givenName**</span><span class="sxs-lookup"><span data-stu-id="c34b3-151">**givenName**</span></span>
    
  - <span data-ttu-id="c34b3-152">如果该属性存在于用户对象中，它将与 Microsoft 365 同步，但 Microsoft 365 不需要或使用它。</span><span class="sxs-lookup"><span data-stu-id="c34b3-152">If the attribute exists in the user object, it will be synchronized with Microsoft 365, but Microsoft 365 does not require or use it.</span></span>
  - <span data-ttu-id="c34b3-153">最大字符数：64</span><span class="sxs-lookup"><span data-stu-id="c34b3-153">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="c34b3-154">**信箱**</span><span class="sxs-lookup"><span data-stu-id="c34b3-154">**mail**</span></span>
    
  - <span data-ttu-id="c34b3-155">属性值在目录中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="c34b3-155">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="c34b3-156">如果存在重复值，则将同步第一个值为的用户。</span><span class="sxs-lookup"><span data-stu-id="c34b3-156">If there are duplicate values, the first user with the value is synchronized.</span></span> <span data-ttu-id="c34b3-157">随后的用户不会出现在 Microsoft 365 中。</span><span class="sxs-lookup"><span data-stu-id="c34b3-157">Subsequent users will not appear in Microsoft 365.</span></span> <span data-ttu-id="c34b3-158">您必须修改 Microsoft 365 中的值或修改 AD DS 中的两个值，以使这两个用户都显示在 Microsoft 365 中。</span><span class="sxs-lookup"><span data-stu-id="c34b3-158">You must modify either the value in Microsoft 365 or modify both of the values in AD DS in order for both users to appear in Microsoft 365.</span></span> 
  
- <span data-ttu-id="c34b3-159">**mailNickname** （Exchange 别名）</span><span class="sxs-lookup"><span data-stu-id="c34b3-159">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="c34b3-160">属性值不能以句点（.）开头。</span><span class="sxs-lookup"><span data-stu-id="c34b3-160">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="c34b3-161">属性值在目录中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="c34b3-161">The attribute value must be unique within the directory.</span></span>
  
    > [!NOTE]
    > <span data-ttu-id="c34b3-162">同步名称中的下划线（"_"）表示此属性的原始值包含无效字符。</span><span class="sxs-lookup"><span data-stu-id="c34b3-162">Underscores ("_") in the synchronized name indicates that the original value of this attribute contains invalid characters.</span></span> <span data-ttu-id="c34b3-163">有关此属性的详细信息，请参阅[Exchange alias 属性](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps)。</span><span class="sxs-lookup"><span data-stu-id="c34b3-163">For more information on this attribute, see [Exchange alias attribute](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps).</span></span>
    >
      
- <span data-ttu-id="c34b3-164">**proxyAddresses**</span><span class="sxs-lookup"><span data-stu-id="c34b3-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="c34b3-165">多值属性</span><span class="sxs-lookup"><span data-stu-id="c34b3-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="c34b3-166">每个值的最大字符数：256</span><span class="sxs-lookup"><span data-stu-id="c34b3-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="c34b3-167">属性值不能包含空格。</span><span class="sxs-lookup"><span data-stu-id="c34b3-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="c34b3-168">属性值在目录中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="c34b3-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="c34b3-169">无效字符： \< \> （）;，[] ""</span><span class="sxs-lookup"><span data-stu-id="c34b3-169">Invalid characters: \< \> ( ) ; , [ ] " '</span></span>
    
    <span data-ttu-id="c34b3-170">请注意，无效字符适用于类型分隔符后面的字符和 "："，因此允许 SMTP:User@contso.com，但 SMTP:user:M@contoso.com 不是。</span><span class="sxs-lookup"><span data-stu-id="c34b3-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="c34b3-171">所有简单邮件传输协议（SMTP）地址都应遵守电子邮件邮件传递标准。</span><span class="sxs-lookup"><span data-stu-id="c34b3-171">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span> <span data-ttu-id="c34b3-172">如果存在重复或不需要的地址，请参阅帮助主题[删除 Exchange 中的重复和不需要的代理地址](https://go.microsoft.com/fwlink/?LinkId=293860)。</span><span class="sxs-lookup"><span data-stu-id="c34b3-172">If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="c34b3-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="c34b3-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="c34b3-174">最大字符数：20</span><span class="sxs-lookup"><span data-stu-id="c34b3-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="c34b3-175">属性值在目录中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="c34b3-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="c34b3-176">无效字符： [\ "|，/： \< \> + =;？</span><span class="sxs-lookup"><span data-stu-id="c34b3-176">Invalid characters: [ \ " | , / : \< \> + = ; ?</span></span> <span data-ttu-id="c34b3-177">\* ']</span><span class="sxs-lookup"><span data-stu-id="c34b3-177">\* ']</span></span>
  - <span data-ttu-id="c34b3-178">如果用户具有无效的**sAMAccountName**属性，但具有有效的**userPrincipalName**属性，则将在 Microsoft 365 中创建用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c34b3-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Microsoft 365.</span></span> 
  - <span data-ttu-id="c34b3-179">如果**sAMAccountName**和**userPrincipalName**都无效，则必须更新 AD DS **userPrincipalName**属性。</span><span class="sxs-lookup"><span data-stu-id="c34b3-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the AD DS **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="c34b3-180">**sn** （姓）</span><span class="sxs-lookup"><span data-stu-id="c34b3-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="c34b3-181">如果该属性存在于用户对象中，它将与 Microsoft 365 同步，但 Microsoft 365 不需要或使用它。</span><span class="sxs-lookup"><span data-stu-id="c34b3-181">If the attribute exists in the user object, it will be synchronized with Microsoft 365, but Microsoft 365 does not require or use it.</span></span>
    
- <span data-ttu-id="c34b3-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="c34b3-182">**targetAddress**</span></span>
    
    <span data-ttu-id="c34b3-183">必须在 Microsoft 365 GAL 中显示为用户填充的**targetAddress**属性（例如，SMTP:tom@contoso.com）。</span><span class="sxs-lookup"><span data-stu-id="c34b3-183">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Microsoft 365 GAL.</span></span> <span data-ttu-id="c34b3-184">在第三方邮件迁移方案中，这将需要用于 AD DS 的 Microsoft 365 架构扩展。</span><span class="sxs-lookup"><span data-stu-id="c34b3-184">In third-party messaging migration scenarios, this would require the Microsoft 365 schema extension for the AD DS.</span></span> <span data-ttu-id="c34b3-185">Microsoft 365 架构扩展还将添加其他有用的属性来管理使用 AD DS 中的目录同步工具填充的 Microsoft 365 对象。</span><span class="sxs-lookup"><span data-stu-id="c34b3-185">The Microsoft 365 schema extension would also add other useful attributes to manage Microsoft 365 objects that are populated by using a directory synchronization tool from AD DS.</span></span> <span data-ttu-id="c34b3-186">例如，将添加用于管理隐藏邮箱或通讯组的**msExchHideFromAddressLists**属性。</span><span class="sxs-lookup"><span data-stu-id="c34b3-186">For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="c34b3-187">最大字符数：256</span><span class="sxs-lookup"><span data-stu-id="c34b3-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="c34b3-188">属性值不能包含空格。</span><span class="sxs-lookup"><span data-stu-id="c34b3-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="c34b3-189">属性值在目录中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="c34b3-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="c34b3-190">无效字符： \ \< \> （）;，[] "</span><span class="sxs-lookup"><span data-stu-id="c34b3-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="c34b3-191">所有简单邮件传输协议（SMTP）地址都应遵守电子邮件邮件传递标准。</span><span class="sxs-lookup"><span data-stu-id="c34b3-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="c34b3-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="c34b3-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="c34b3-193">**UserPrincipalName**属性必须为 Internet 样式的登录格式，其中用户名后跟 "at" 符号（@）和域名：例如，user@contoso.com。</span><span class="sxs-lookup"><span data-stu-id="c34b3-193">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com.</span></span> <span data-ttu-id="c34b3-194">所有简单邮件传输协议（SMTP）地址都应遵守电子邮件邮件传递标准。</span><span class="sxs-lookup"><span data-stu-id="c34b3-194">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="c34b3-195">**UserPrincipalName**属性的最大字符数为113。</span><span class="sxs-lookup"><span data-stu-id="c34b3-195">The maximum number of characters for the **userPrincipalName** attribute is 113.</span></span> <span data-ttu-id="c34b3-196">在 at 符号（@）的前面和后面允许使用特定数量的字符，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c34b3-196">A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="c34b3-197">位于 at 符号（@）前面的用户名的最大字符数（@）：64</span><span class="sxs-lookup"><span data-stu-id="c34b3-197">Maximum number of characters for the username that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="c34b3-198">At 符号（@）后面的域名的最大字符数：48</span><span class="sxs-lookup"><span data-stu-id="c34b3-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="c34b3-199">无效字符： \% &amp; \* +/=？</span><span class="sxs-lookup"><span data-stu-id="c34b3-199">Invalid characters: \ % &amp; \* + / = ?</span></span> <span data-ttu-id="c34b3-200">{ } | \< \> ( ) ; : , [ ] " '</span><span class="sxs-lookup"><span data-stu-id="c34b3-200">{ } | \< \> ( ) ; : , [ ] " '</span></span>
  - <span data-ttu-id="c34b3-201">元音变音符也是一个无效字符。</span><span class="sxs-lookup"><span data-stu-id="c34b3-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="c34b3-202">每个**userPrincipalName**值中都需要 @ 字符。</span><span class="sxs-lookup"><span data-stu-id="c34b3-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="c34b3-203">@ 符在每个 **userPrincipalName** 值中不能作为第一个字符。</span><span class="sxs-lookup"><span data-stu-id="c34b3-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="c34b3-204">用户名不能以句点（.）、与号（ &amp; ）、空格或 at 符号（@）结尾。</span><span class="sxs-lookup"><span data-stu-id="c34b3-204">The username cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="c34b3-205">用户名不能包含任何空格。</span><span class="sxs-lookup"><span data-stu-id="c34b3-205">The username cannot contain any spaces.</span></span>
  - <span data-ttu-id="c34b3-206">必须使用可路由的域;例如，不能使用本地或内部域。</span><span class="sxs-lookup"><span data-stu-id="c34b3-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="c34b3-207">Unicode 将转换为下划线字符。</span><span class="sxs-lookup"><span data-stu-id="c34b3-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="c34b3-208">**userPrincipalName**不能包含目录中的任何重复值。</span><span class="sxs-lookup"><span data-stu-id="c34b3-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 

<span data-ttu-id="c34b3-209">请参阅使用[IdFix 工具准备目录属性](prepare-directory-attributes-for-synch-with-idfix.md)，以使用 IdFix 工具识别 AD DS 的属性中的错误。</span><span class="sxs-lookup"><span data-stu-id="c34b3-209">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to use the IdFIx tool to identify errors in the attributes of your AD DS.</span></span>
    
## <a name="3-prepare-the-userprincipalname-attribute"></a><span data-ttu-id="c34b3-210">3. 准备 userPrincipalName 属性</span><span class="sxs-lookup"><span data-stu-id="c34b3-210">3. Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="c34b3-211">Active Directory 旨在允许组织中的最终用户使用**sAMAccountName**或**userPrincipalName**登录到您的目录。</span><span class="sxs-lookup"><span data-stu-id="c34b3-211">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**.</span></span> <span data-ttu-id="c34b3-212">同样，最终用户可以使用其工作或学校帐户的用户主体名称（UPN）登录 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="c34b3-212">Similarly, end users can sign in to Microsoft 365 by using the user principal name (UPN) of their work or school account.</span></span> <span data-ttu-id="c34b3-213">目录同步尝试使用 AD DS 中的同一个 UPN 在 Azure Active Directory 中创建新用户。</span><span class="sxs-lookup"><span data-stu-id="c34b3-213">Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your AD DS.</span></span> <span data-ttu-id="c34b3-214">UPN 的格式类似于电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="c34b3-214">The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="c34b3-215">在 Microsoft 365 中，UPN 是用于生成电子邮件地址的默认属性。</span><span class="sxs-lookup"><span data-stu-id="c34b3-215">In Microsoft 365, the UPN is the default attribute that's used to generate the email address.</span></span> <span data-ttu-id="c34b3-216">可以轻松获取**userPrincipalName** （在 ad DS 和 Azure AD 中）和**proxyAddresses**中的主电子邮件地址设置为不同的值。</span><span class="sxs-lookup"><span data-stu-id="c34b3-216">It's easy to get **userPrincipalName** (in AD DS and in Azure AD) and the primary email address in **proxyAddresses** set to different values.</span></span> <span data-ttu-id="c34b3-217">当它们设置为不同的值时，管理员和最终用户可能会感到困惑。</span><span class="sxs-lookup"><span data-stu-id="c34b3-217">When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="c34b3-218">最好对齐这些属性以减少混淆。</span><span class="sxs-lookup"><span data-stu-id="c34b3-218">It's best to align these attributes to reduce confusion.</span></span> <span data-ttu-id="c34b3-219">若要满足单一登录与 Active Directory 联合身份验证服务（AD FS）2.0 的要求，您需要确保 Azure Active Directory 和 AD DS 中的 Upn 匹配且使用有效的域命名空间。</span><span class="sxs-lookup"><span data-stu-id="c34b3-219">To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your AD DS match and are using a valid domain namespace.</span></span>
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="c34b3-220">4. 向 AD DS 添加备用 UPN 后缀</span><span class="sxs-lookup"><span data-stu-id="c34b3-220">4. Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="c34b3-221">您可能需要添加其他 UPN 后缀以将用户的公司凭据与 Microsoft 365 环境相关联。</span><span class="sxs-lookup"><span data-stu-id="c34b3-221">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Microsoft 365 environment.</span></span> <span data-ttu-id="c34b3-222">UPN 后缀是 @ 字符右侧的 UPN 的一部分。</span><span class="sxs-lookup"><span data-stu-id="c34b3-222">A UPN suffix is the part of a UPN to the right of the @ character.</span></span> <span data-ttu-id="c34b3-223">用于单一登录的 UPN 可能包含字母、数字、句点、短划线和下划线，但不包含任何其他类型的字符。</span><span class="sxs-lookup"><span data-stu-id="c34b3-223">UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="c34b3-224">有关如何将其他 UPN 后缀添加到 Active Directory 的详细信息，请参阅[Prepare for Directory 同步]( https://go.microsoft.com/fwlink/p/?LinkId=525430)。</span><span class="sxs-lookup"><span data-stu-id="c34b3-224">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="5-match-the-ad-ds-upn-with-the-microsoft-365-upn"></a><span data-ttu-id="c34b3-225">5. 将 AD DS UPN 与 Microsoft 365 UPN 匹配</span><span class="sxs-lookup"><span data-stu-id="c34b3-225">5. Match the AD DS UPN with the Microsoft 365 UPN</span></span>

<span data-ttu-id="c34b3-226">如果已设置目录同步，则用户的 Microsoft 365 UPN 可能与 AD DS 中定义的用户的 AD DS UPN 不匹配。</span><span class="sxs-lookup"><span data-stu-id="c34b3-226">If you've already set up directory synchronization, the user's UPN for Microsoft 365 may not match the user's AD DS UPN that's defined in your AD DS.</span></span> <span data-ttu-id="c34b3-227">如果在验证域前已为用户分配了许可证，则可能发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="c34b3-227">This can occur when a user was assigned a license before the domain was verified.</span></span> <span data-ttu-id="c34b3-228">若要解决此问题，请使用[PowerShell 修复重复的 upn](https://go.microsoft.com/fwlink/p/?LinkId=396730)以更新用户的 upn，以确保 MICROSOFT 365 UPN 与公司用户名和域相匹配。</span><span class="sxs-lookup"><span data-stu-id="c34b3-228">To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Microsoft 365 UPN matches the corporate user name and domain.</span></span> <span data-ttu-id="c34b3-229">如果要在 AD DS 中更新 UPN，并希望它与 Azure Active Directory 标识同步，则需要先在 Microsoft 365 中删除用户的许可证，然后再在 AD DS 中进行更改。</span><span class="sxs-lookup"><span data-stu-id="c34b3-229">If you are updating the UPN in the AD DS and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Microsoft 365 prior to making the changes in AD DS.</span></span> 
  
<span data-ttu-id="c34b3-230">另请参阅[如何为目录同步准备不可路由的域（例如，本地域）](prepare-a-non-routable-domain-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="c34b3-230">Also see [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>


## <a name="next-steps"></a><span data-ttu-id="c34b3-231">后续步骤</span><span class="sxs-lookup"><span data-stu-id="c34b3-231">Next steps</span></span>

<span data-ttu-id="c34b3-232">请参阅[使用 IdFix 工具准备目录属性](prepare-directory-attributes-for-synch-with-idfix.md)，以帮助您在目录同步之前更正 AD DS 的属性中的错误。</span><span class="sxs-lookup"><span data-stu-id="c34b3-232">See [Prepare directory attributes with the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) to help you correct errors in the attributes of your AD DS prior to directory synchronization.</span></span>

<span data-ttu-id="c34b3-233">如果更正了使用 IdFix 工具识别的所有属性错误，并已完成上面的步骤1到步骤5，请参阅[设置目录同步](set-up-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="c34b3-233">If you have corrected all the attribute errors identified with the IdFix tool and have done steps 1 through 5 above, see [Set up directory synchronization](set-up-directory-synchronization.md).</span></span>
