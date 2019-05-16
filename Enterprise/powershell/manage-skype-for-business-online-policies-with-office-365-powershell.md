---
title: 管理 Skype 与 Office 365 PowerShell 的在线业务策略
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: '摘要: 使用 Office 365 PowerShell, 通过策略管理 Skype for business Online 用户帐户属性。'
ms.openlocfilehash: 853d70a008a3e42c6fa1175a52cadab815a46dfe
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068838"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="050af-103">管理 Skype 与 Office 365 PowerShell 的在线业务策略</span><span class="sxs-lookup"><span data-stu-id="050af-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="050af-104">**摘要:** 使用 Office 365 PowerShell, 通过策略管理 Skype for business Online 用户帐户属性。</span><span class="sxs-lookup"><span data-stu-id="050af-104">**Summary:** Use Office 365 PowerShell to manage your Skype for Business Online user account properties with policies.</span></span>
  
<span data-ttu-id="050af-105">若要管理多个用户帐户的 Skype for Business Online 属性, 必须使用 Office 365 PowerShell 将其指定为策略的属性。</span><span class="sxs-lookup"><span data-stu-id="050af-105">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="050af-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="050af-106">Before you begin</span></span>

<span data-ttu-id="050af-107">使用以下说明设置运行命令 (跳过已完成的步骤):</span><span class="sxs-lookup"><span data-stu-id="050af-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="050af-108">下载并安装[Skype For Business Online 连接器模块](https://www.microsoft.com/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="050af-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="050af-109">打开 Windows PowerShell 命令提示符, 并运行以下命令:</span><span class="sxs-lookup"><span data-stu-id="050af-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="050af-110">出现提示时, 请输入你的 Skype for Business Online 管理员帐户名称和密码。</span><span class="sxs-lookup"><span data-stu-id="050af-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="050af-111">管理用户帐户策略</span><span class="sxs-lookup"><span data-stu-id="050af-111">Manage user account policies</span></span>

<span data-ttu-id="050af-112">许多 Skype for Business Online 用户帐户属性都是通过使用策略配置的。</span><span class="sxs-lookup"><span data-stu-id="050af-112">Many Skype for Business Online user account properties are configured by using policies.</span></span> <span data-ttu-id="050af-113">策略只是可应用于一个或多个用户的设置集合。</span><span class="sxs-lookup"><span data-stu-id="050af-113">Policies are simply collections of settings that can be applied to one or more users.</span></span> <span data-ttu-id="050af-114">若要了解如何配置策略, 可以对 FederationAndPICDefault 策略运行此示例命令:</span><span class="sxs-lookup"><span data-stu-id="050af-114">To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="050af-115">反过来, 您应返回类似于以下的内容:</span><span class="sxs-lookup"><span data-stu-id="050af-115">In turn, you should get back something similar to this:</span></span>
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="050af-116">在此示例中, 此策略中的值确定在与联合用户通信时可使用的功能或无法执行的操作。</span><span class="sxs-lookup"><span data-stu-id="050af-116">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users.</span></span> <span data-ttu-id="050af-117">例如, EnableOutsideAccess 属性必须设置为 True, 用户才能够与组织外部的人员进行通信。</span><span class="sxs-lookup"><span data-stu-id="050af-117">For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization.</span></span> <span data-ttu-id="050af-118">请注意, 此属性不会显示在 Office 365 管理中心中。</span><span class="sxs-lookup"><span data-stu-id="050af-118">Note that this property does not appear in the Office 365 Admin center.</span></span> <span data-ttu-id="050af-119">相反, 该属性将根据您所做的其他选择自动设置为 True 或 False。</span><span class="sxs-lookup"><span data-stu-id="050af-119">Instead, the property is automatically set to True or False based on the other selections that you make.</span></span> <span data-ttu-id="050af-120">其他两个感兴趣的属性为:</span><span class="sxs-lookup"><span data-stu-id="050af-120">The other two properties of interest are:</span></span>
  
- <span data-ttu-id="050af-121">**EnableFederationAccess** 指示用户是否可以与联合域的用户通信。</span><span class="sxs-lookup"><span data-stu-id="050af-121">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="050af-122">**EnablePublicCloudAccess** 指示用户是否可以与 Windows Live 用户通信。</span><span class="sxs-lookup"><span data-stu-id="050af-122">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="050af-123">因此, 不会直接更改用户帐户的与联合相关的属性 (例如, **get-csuser-EnableFederationAccess $True**)。</span><span class="sxs-lookup"><span data-stu-id="050af-123">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**).</span></span> <span data-ttu-id="050af-124">而是为帐户分配一个预先配置的所需属性值的外部访问策略。</span><span class="sxs-lookup"><span data-stu-id="050af-124">Instead, you assign an account an external access policy that has the desired property values preconfigured.</span></span> <span data-ttu-id="050af-125">如果我们希望用户能够与联合用户和 Windows Live 用户通信, 则必须为该用户帐户分配允许这些类型的通信的策略。</span><span class="sxs-lookup"><span data-stu-id="050af-125">If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="050af-126">如果您希望知道某人是否可以与组织外部的用户进行通信, 则必须执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="050af-126">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="050af-127">确定为此用户分配的是哪种外部访问策略。</span><span class="sxs-lookup"><span data-stu-id="050af-127">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="050af-128">确定此策略允许的许可范围。</span><span class="sxs-lookup"><span data-stu-id="050af-128">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="050af-129">例如, 您可以通过使用以下命令来执行此操作:</span><span class="sxs-lookup"><span data-stu-id="050af-129">For example, you can do that by using this command:</span></span>
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="050af-130">此命令可查找分配给用户的策略, 然后查找该策略中启用或禁用的功能。</span><span class="sxs-lookup"><span data-stu-id="050af-130">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="050af-131">请注意, 没有用于创建或修改策略的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="050af-131">Note that there are no cmdlets for creating or for modifying policies.</span></span> <span data-ttu-id="050af-132">您必须使用由 Office 365 预提供的策略。</span><span class="sxs-lookup"><span data-stu-id="050af-132">You must use the policies pre-supplied by Office 365.</span></span> <span data-ttu-id="050af-133">若要查看可用的不同策略, 可以使用以下命令:</span><span class="sxs-lookup"><span data-stu-id="050af-133">If you want to take a look at the different policies available, you can use these commands:</span></span>
  
- <span data-ttu-id="050af-134">Set-csclientpolicy</span><span class="sxs-lookup"><span data-stu-id="050af-134">Get-CsClientPolicy</span></span>       
- <span data-ttu-id="050af-135">Set-csconferencingpolicy</span><span class="sxs-lookup"><span data-stu-id="050af-135">Get-CsConferencingPolicy</span></span>        
- <span data-ttu-id="050af-136">Grant-csdialplan</span><span class="sxs-lookup"><span data-stu-id="050af-136">Get-CsDialPlan</span></span>            
- <span data-ttu-id="050af-137">Set-csexternalaccesspolicy</span><span class="sxs-lookup"><span data-stu-id="050af-137">Get-CsExternalAccessPolicy</span></span>                         
- <span data-ttu-id="050af-138">CsHostedVoicemailPolicy</span><span class="sxs-lookup"><span data-stu-id="050af-138">Get-CsHostedVoicemailPolicy</span></span>                        
- <span data-ttu-id="050af-139">CsPresencePolicy</span><span class="sxs-lookup"><span data-stu-id="050af-139">Get-CsPresencePolicy</span></span>                               
- <span data-ttu-id="050af-140">Set-csvoicepolicy</span><span class="sxs-lookup"><span data-stu-id="050af-140">Get-CsVoicePolicy</span></span>                                  

> [!NOTE]
> <span data-ttu-id="050af-141">Skype for Business Online 拨号计划是除了名称之外的每个方面的策略。</span><span class="sxs-lookup"><span data-stu-id="050af-141">A Skype for Business Online dial plan is a policy in every respect except the name.</span></span> <span data-ttu-id="050af-142">已选择名称 "拨号计划", 而不是 "拨号策略", 以便提供与 Office 通信服务器和 Exchange 的向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="050af-142">The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="050af-143">例如, 若要查看所有可供使用的语音策略, 请运行以下命令:</span><span class="sxs-lookup"><span data-stu-id="050af-143">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="050af-144">将返回所有可用的语音策略的列表。</span><span class="sxs-lookup"><span data-stu-id="050af-144">That returns a list of all the voice policies available to you.</span></span> <span data-ttu-id="050af-145">但请记住, 并非所有策略都可以分配给所有用户。</span><span class="sxs-lookup"><span data-stu-id="050af-145">Keep in mind, however, that not all policies can be assigned to all users.</span></span> <span data-ttu-id="050af-146">这是由于涉及许可和地理位置的各种限制导致的。</span><span class="sxs-lookup"><span data-stu-id="050af-146">This is due to various restrictions involving licensing and geographic location.</span></span> <span data-ttu-id="050af-147">(所谓的 "[使用位置](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx)")。如果要了解可分配给特定用户的外部访问策略和会议策略, 请使用与以下命令类似的命令:</span><span class="sxs-lookup"><span data-stu-id="050af-147">(The so-called "[usage location](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="050af-p107">ApplicableTo 参数可将返回的数据限制为可分配到特定用户的策略（例如，Alex Darrow）。根据不同的授权和使用位置限制，可能会代表所有可用策略的子集。</span><span class="sxs-lookup"><span data-stu-id="050af-p107">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="050af-150">在某些情况下, 不会将策略的属性用于 Office 365, 而有些则只能由 Microsoft 支持人员管理。</span><span class="sxs-lookup"><span data-stu-id="050af-150">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="050af-151">使用 Skype for Business Online, 用户必须由某种类型的策略进行管理。</span><span class="sxs-lookup"><span data-stu-id="050af-151">With Skype for Business Online, users must be managed by a policy of some kind.</span></span> <span data-ttu-id="050af-152">如果与策略相关的有效属性为空, 则表示有问题的用户将由全局策略管理, 这是一个策略, 该策略将自动应用于用户, 除非专门为其分配了每用户策略。</span><span class="sxs-lookup"><span data-stu-id="050af-152">If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy.</span></span> <span data-ttu-id="050af-153">由于我们看不到为用户帐户列出的客户端策略, 因此它由全局策略管理。</span><span class="sxs-lookup"><span data-stu-id="050af-153">Because we don't see a client policy listed for a user account, it is managed by the global policy.</span></span> <span data-ttu-id="050af-154">您可以使用此命令确定全局客户端策略:</span><span class="sxs-lookup"><span data-stu-id="050af-154">You can determine the global client policy with this command:</span></span>
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="050af-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="050af-155">See also</span></span>

#### 

[<span data-ttu-id="050af-156">使用 Office 365 PowerShell 管理 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="050af-156">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="050af-157">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="050af-157">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="050af-158">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="050af-158">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

