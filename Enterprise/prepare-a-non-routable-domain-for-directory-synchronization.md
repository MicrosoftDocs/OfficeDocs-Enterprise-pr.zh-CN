---
title: 为目录同步准备不可路由的域
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_SetupDirSyncLocalDir
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: 如果您在与 Microsoft 365 同步之前拥有与本地用户关联的非 routale 域，请了解要执行的操作。
ms.openlocfilehash: 148d7e1abdeeeea11c838697bbc957e2937ea7f8
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "44736010"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a><span data-ttu-id="933ac-103">为目录同步准备不可路由的域</span><span class="sxs-lookup"><span data-stu-id="933ac-103">Prepare a non-routable domain for directory synchronization</span></span>
<span data-ttu-id="933ac-104">当您将本地目录与 Microsoft 365 同步时，您必须在 Azure Active Directory （Azure AD）中有一个经验证的域。</span><span class="sxs-lookup"><span data-stu-id="933ac-104">When you synchronize your on-premises directory with Microsoft 365 you have to have a verified domain in Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="933ac-105">仅同步与本地域关联的用户主体名称（UPN）。</span><span class="sxs-lookup"><span data-stu-id="933ac-105">Only the User Principal Names (UPN) that are associated with the on-premises domain are synchronized.</span></span> <span data-ttu-id="933ac-106">但是，任何包含非可路由域的 UPN （如 local billa@contoso）将同步到一个 onmicrosoft.com 域（如 billa@contoso.onmicrosoft.com）。</span><span class="sxs-lookup"><span data-stu-id="933ac-106">However, any UPN that contains an non-routable domain, for example .local (like billa@contoso.local), will be synchronized to an .onmicrosoft.com domain (like billa@contoso.onmicrosoft.com).</span></span> 

<span data-ttu-id="933ac-107">如果您当前在 Active Directory 域服务（AD DS）中为您的用户帐户使用了. 本地域，建议您将其更改为使用经验证的域（如 billa@contoso.com），以便与 Microsoft 365 域正确同步。</span><span class="sxs-lookup"><span data-stu-id="933ac-107">If you currently use a .local domain for your user accounts in Active Directory Domain Services (AD DS) it's recommended that you change them to use a verified domain (like billa@contoso.com) in order to properly sync with your Microsoft 365 domain.</span></span>
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a><span data-ttu-id="933ac-108">如果我只有一个本地域，该怎么办？</span><span class="sxs-lookup"><span data-stu-id="933ac-108">What if I only have a .local on-premises domain?</span></span>

<span data-ttu-id="933ac-109">你可用于将 AD DS 同步到 Azure AD 的最新工具称为 "Azure AD Connect"。</span><span class="sxs-lookup"><span data-stu-id="933ac-109">The most recent tool you can use for synchronizing your AD DS to Azure AD is named Azure AD Connect.</span></span> <span data-ttu-id="933ac-110">有关详细信息，请参阅[将本地标识与 AZURE AD 集成](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)。</span><span class="sxs-lookup"><span data-stu-id="933ac-110">For more information, see [Integrating your on-premises identities with Azure AD](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).</span></span>
  
<span data-ttu-id="933ac-111">Azure AD Connect 同步你的用户的 UPN 和密码，以便用户可以使用内部部署中使用的相同凭据登录。</span><span class="sxs-lookup"><span data-stu-id="933ac-111">Azure AD Connect synchronizes your users' UPN and password so that users can sign in with the same credentials they use on-premises.</span></span> <span data-ttu-id="933ac-112">但是，Azure AD Connect 仅将用户同步到 Microsoft 365 验证的域。</span><span class="sxs-lookup"><span data-stu-id="933ac-112">However, Azure AD Connect only synchronizes users to domains that are verified by Microsoft 365.</span></span> <span data-ttu-id="933ac-113">这意味着域也会由 Azure AD 验证，因为 Microsoft 365 身份由 Azure AD 管理。</span><span class="sxs-lookup"><span data-stu-id="933ac-113">This means that the domain also is verified by Azure AD because Microsoft 365 identities are managed by Azure AD.</span></span> <span data-ttu-id="933ac-114">换句话说，域必须是有效的 Internet 域（例如 .com、. org、.net、. us 等）。</span><span class="sxs-lookup"><span data-stu-id="933ac-114">In other words, the domain has to be a valid Internet domain (for example, .com, .org, .net, .us, etc.).</span></span> <span data-ttu-id="933ac-115">如果内部 AD DS 仅使用不可路由的域（例如，"本地"），则这不会与 Microsoft 365 中的已验证域相匹配。</span><span class="sxs-lookup"><span data-stu-id="933ac-115">If your internal AD DS only uses a non-routable domain (for example, .local), this can't possibly match the verified domain you have on Microsoft 365.</span></span> <span data-ttu-id="933ac-116">您可以通过在本地 AD DS 中更改主要域，或通过添加一个或多个 UPN 后缀来修复此问题。</span><span class="sxs-lookup"><span data-stu-id="933ac-116">You can fix this issue by either changing your primary domain in your on premises AD DS, or by adding one or more UPN suffixes.</span></span>
  
### <a name="change-your-primary-domain"></a><span data-ttu-id="933ac-117">**更改你的主要域**</span><span class="sxs-lookup"><span data-stu-id="933ac-117">**Change your primary domain**</span></span>

<span data-ttu-id="933ac-118">将您的主域更改为在 Microsoft 365 中验证的域（例如，contoso.com）。</span><span class="sxs-lookup"><span data-stu-id="933ac-118">Change your primary domain to a domain you have verified in Microsoft 365, for example, contoso.com.</span></span> <span data-ttu-id="933ac-119">然后，会将拥有域 contoso. 本地的每个用户更新为 contoso.com。</span><span class="sxs-lookup"><span data-stu-id="933ac-119">Every user that has the domain contoso.local is then updated to contoso.com.</span></span> <span data-ttu-id="933ac-120">有关说明，请参阅[域重命名的工作原理](https://go.microsoft.com/fwlink/p/?LinkId=624174)。</span><span class="sxs-lookup"><span data-stu-id="933ac-120">For instructions, see [How Domain Rename Works](https://go.microsoft.com/fwlink/p/?LinkId=624174).</span></span> <span data-ttu-id="933ac-121">这是一个非常涉及的过程，但在下一节中介绍了更简单的解决方案。</span><span class="sxs-lookup"><span data-stu-id="933ac-121">This is a very involved process, however, and an easier solution is described in the following section.</span></span>
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a><span data-ttu-id="933ac-122">**添加 UPN 后缀并将你的用户更新到这些后缀**</span><span class="sxs-lookup"><span data-stu-id="933ac-122">**Add UPN suffixes and update your users to them**</span></span>

<span data-ttu-id="933ac-123">您可以通过在 AD DS 中注册新的 UPN 后缀或后缀以匹配在 Microsoft 365 中验证的域（或域）来解决本地问题。</span><span class="sxs-lookup"><span data-stu-id="933ac-123">You can solve the .local problem by registering new UPN suffix or suffixes in AD DS to match the domain (or domains) you verified in Microsoft 365.</span></span> <span data-ttu-id="933ac-124">注册新后缀后，使用新域名更新用户 Upn 以将局部变量替换为示例，以便用户帐户看起来像 billa@contoso.com。</span><span class="sxs-lookup"><span data-stu-id="933ac-124">After you register the new suffix, you update the user UPNs to replace the .local with the new domain name for example so that a user account looks like billa@contoso.com.</span></span>
  
<span data-ttu-id="933ac-125">将 Upn 更新为使用已验证的域后，即可将本地 AD DS 与 Microsoft 365 同步。</span><span class="sxs-lookup"><span data-stu-id="933ac-125">After you have updated the UPNs to use the verified domain,you are ready to synchronize your on-premises AD DS with Microsoft 365.</span></span>
  
 <span data-ttu-id="933ac-126">**步骤1：添加新的 UPN 后缀**</span><span class="sxs-lookup"><span data-stu-id="933ac-126">**Step 1: Add the new UPN suffix**</span></span>
  
1. <span data-ttu-id="933ac-127">在 AD DS 域控制器上，在 "服务器管理器" 中选择 "**工具** \> **Active Directory 域和信任**"。</span><span class="sxs-lookup"><span data-stu-id="933ac-127">On the AD DS domain controller, in the Server Manager choose **Tools** \> **Active Directory Domains and Trusts**.</span></span>
    
    <span data-ttu-id="933ac-128">**或者，如果您没有 Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="933ac-128">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="933ac-129">按**Windows 键 + R**以打开 "**运行**" 对话框，然后在 "services.msc" 中键入，然后选择 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="933ac-129">Press **Windows key + R** to open the **Run** dialog, and then type in Domain.msc, and then choose **OK**.</span></span>
    
    ![选择 "Active Directory 域和信任"。](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. <span data-ttu-id="933ac-131">在 " **Active Directory 域和信任**" 窗口中，右键单击 " **active Directory 域和信任关系**"，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="933ac-131">On the **Active Directory Domains and Trusts** window, right-click **Active Directory Domains and Trusts**, and then choose **Properties**.</span></span>
    
    ![右键单击 "Active Directory 域和信任关系"，然后选择 "属性"](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. <span data-ttu-id="933ac-133">在 " **UPN 后缀**" 选项卡上的 "**备用 upn 后缀**" 框中，键入新的 upn 后缀或后缀，然后选择 "**添加** \> **应用**"。</span><span class="sxs-lookup"><span data-stu-id="933ac-133">On the **UPN Suffixes** tab, in the **Alternative UPN Suffixes** box, type your new UPN suffix or suffixes, and then choose **Add** \> **Apply**.</span></span>
    
    ![添加新的 UPN 后缀](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    <span data-ttu-id="933ac-135">完成添加后缀后，选择 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="933ac-135">Choose **OK** when you're done adding suffixes.</span></span> 
    
 <span data-ttu-id="933ac-136">**步骤2：更改现有用户的 UPN 后缀**</span><span class="sxs-lookup"><span data-stu-id="933ac-136">**Step 2: Change the UPN suffix for existing users**</span></span>
  
1. <span data-ttu-id="933ac-137">在 AD DS 域控制器上，在 "服务器管理器" 中选择 "**工具**" " \> **Active Directory 用户和计算机**"。</span><span class="sxs-lookup"><span data-stu-id="933ac-137">On the AD DS domain controller, in the Server Manager choose **Tools** \> **Active Directory Users and Computers**.</span></span>
    
    <span data-ttu-id="933ac-138">**或者，如果您没有 Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="933ac-138">**Or, if you don't have Windows Server 2012**</span></span>
    
    <span data-ttu-id="933ac-139">按**Windows 键 + R**以打开 "**运行**" 对话框，然后在 "dsa.msc" 中键入，然后单击 **"确定"**</span><span class="sxs-lookup"><span data-stu-id="933ac-139">Press **Windows key + R** to open the **Run** dialog, and then type in Dsa.msc, and then click **OK**</span></span>
    
2. <span data-ttu-id="933ac-140">选择一个用户，单击鼠标右键，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="933ac-140">Select a user, right-click, and then choose **Properties**.</span></span>
    
3. <span data-ttu-id="933ac-141">在 "**帐户**" 选项卡上的 "UPN 后缀" 下拉列表中，选择新的 upn 后缀，然后选择 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="933ac-141">On the **Account** tab, in the UPN suffix drop-down list, choose the new UPN suffix, and then choose **OK**.</span></span>
    
    ![为用户添加新的 UPN 后缀](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. <span data-ttu-id="933ac-143">为每个用户完成这些步骤。</span><span class="sxs-lookup"><span data-stu-id="933ac-143">Complete these steps for every user.</span></span>
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a><span data-ttu-id="933ac-144">**您还可以使用 Windows PowerShell 为所有用户更改 UPN 后缀**</span><span class="sxs-lookup"><span data-stu-id="933ac-144">**You can also use Windows PowerShell to change the UPN suffix for all users**</span></span>

<span data-ttu-id="933ac-145">如果有大量用户要更新，则使用 Windows PowerShell 更为简单。</span><span class="sxs-lookup"><span data-stu-id="933ac-145">If you have a lot of users to update, it is easier to use Windows PowerShell.</span></span> <span data-ttu-id="933ac-146">下面的示例使用 cmdlet [microsoft.rtc.management.adconnect.schema.aduser](https://go.microsoft.com/fwlink/p/?LinkId=624312)和[microsoft.rtc.management.adconnect.schema.aduser](https://go.microsoft.com/fwlink/p/?LinkId=624313)将所有 contoso. 本地后缀更改为 contoso.com。</span><span class="sxs-lookup"><span data-stu-id="933ac-146">The following example uses the cmdlets [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) and [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) to change all contoso.local suffixes to contoso.com.</span></span> 

<span data-ttu-id="933ac-147">场景例如，您可以运行以下 Windows PowerShell 命令将所有 contoso. 本地后缀更新到 contoso.com：</span><span class="sxs-lookup"><span data-stu-id="933ac-147">Foe example, you could run the following Windows PowerShell commands to update all contoso.local suffixes to contoso.com:</span></span>
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter "UserPrincipalName -like '*contoso.local'" -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("@contoso.local","@contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

<span data-ttu-id="933ac-148">若要详细了解如何在 AD DS 中使用 Windows PowerShell，请参阅[Active Directory Windows PowerShell 模块](https://go.microsoft.com/fwlink/p/?LinkId=624314)。</span><span class="sxs-lookup"><span data-stu-id="933ac-148">See [Active Directory Windows PowerShell module](https://go.microsoft.com/fwlink/p/?LinkId=624314) to learn more about using Windows PowerShell in AD DS.</span></span> 

