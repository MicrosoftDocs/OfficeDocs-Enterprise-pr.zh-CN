---
title: 管理 Skype 与 Office 365 PowerShell 的在线业务策略
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 摘要：使用 Office 365 PowerShell，通过策略管理 Skype for business Online 用户帐户属性。
ms.openlocfilehash: aed7e3929a41dec69803a5b73bdf29fb23b4ba05
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841329"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="a63d0-103">管理 Skype 与 Office 365 PowerShell 的在线业务策略</span><span class="sxs-lookup"><span data-stu-id="a63d0-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

<span data-ttu-id="a63d0-104">若要管理多个用户帐户的 Skype for Business Online 属性，必须使用 Office 365 PowerShell 将其指定为策略的属性。</span><span class="sxs-lookup"><span data-stu-id="a63d0-104">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="a63d0-105">准备工作</span><span class="sxs-lookup"><span data-stu-id="a63d0-105">Before you begin</span></span>

<span data-ttu-id="a63d0-106">使用以下说明设置运行命令（跳过已完成的步骤）：</span><span class="sxs-lookup"><span data-stu-id="a63d0-106">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="a63d0-107">下载并安装[Skype For Business Online 连接器模块](https://www.microsoft.com/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="a63d0-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="a63d0-108">打开 Windows PowerShell 命令提示符，并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a63d0-108">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="a63d0-109">出现提示时，请输入你的 Skype for Business Online 管理员帐户名称和密码。</span><span class="sxs-lookup"><span data-stu-id="a63d0-109">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="a63d0-110">管理用户帐户策略</span><span class="sxs-lookup"><span data-stu-id="a63d0-110">Manage user account policies</span></span>

<span data-ttu-id="a63d0-111">许多 Skype for Business Online 用户帐户属性都是通过使用策略配置的。</span><span class="sxs-lookup"><span data-stu-id="a63d0-111">Many Skype for Business Online user account properties are configured by using policies.</span></span> <span data-ttu-id="a63d0-112">策略只是可应用于一个或多个用户的设置集合。</span><span class="sxs-lookup"><span data-stu-id="a63d0-112">Policies are simply collections of settings that can be applied to one or more users.</span></span> <span data-ttu-id="a63d0-113">若要了解如何配置策略，可以对 FederationAndPICDefault 策略运行此示例命令：</span><span class="sxs-lookup"><span data-stu-id="a63d0-113">To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="a63d0-114">反过来，您应返回类似于以下的内容：</span><span class="sxs-lookup"><span data-stu-id="a63d0-114">In turn, you should get back something similar to this:</span></span>
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="a63d0-115">在此示例中，此策略中的值确定在与联合用户通信时可使用的功能或无法执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a63d0-115">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users.</span></span> <span data-ttu-id="a63d0-116">例如，EnableOutsideAccess 属性必须设置为 True，用户才能够与组织外部的人员进行通信。</span><span class="sxs-lookup"><span data-stu-id="a63d0-116">For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization.</span></span> <span data-ttu-id="a63d0-117">请注意，此属性不会显示在 Microsoft 365 管理中心中。</span><span class="sxs-lookup"><span data-stu-id="a63d0-117">Note that this property does not appear in the Microsoft 365 admin center.</span></span> <span data-ttu-id="a63d0-118">相反，该属性将根据您所做的其他选择自动设置为 True 或 False。</span><span class="sxs-lookup"><span data-stu-id="a63d0-118">Instead, the property is automatically set to True or False based on the other selections that you make.</span></span> <span data-ttu-id="a63d0-119">其他两个感兴趣的属性为：</span><span class="sxs-lookup"><span data-stu-id="a63d0-119">The other two properties of interest are:</span></span>
  
- <span data-ttu-id="a63d0-120">**EnableFederationAccess** 指示用户是否可以与联合域的用户通信。</span><span class="sxs-lookup"><span data-stu-id="a63d0-120">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="a63d0-121">**EnablePublicCloudAccess** 指示用户是否可以与 Windows Live 用户通信。</span><span class="sxs-lookup"><span data-stu-id="a63d0-121">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="a63d0-122">因此，不会直接更改用户帐户的与联合相关的属性（例如， **get-csuser-EnableFederationAccess $True**）。</span><span class="sxs-lookup"><span data-stu-id="a63d0-122">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**).</span></span> <span data-ttu-id="a63d0-123">而是为帐户分配一个预先配置的所需属性值的外部访问策略。</span><span class="sxs-lookup"><span data-stu-id="a63d0-123">Instead, you assign an account an external access policy that has the desired property values preconfigured.</span></span> <span data-ttu-id="a63d0-124">如果我们希望用户能够与联合用户和 Windows Live 用户通信，则必须为该用户帐户分配允许这些类型的通信的策略。</span><span class="sxs-lookup"><span data-stu-id="a63d0-124">If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="a63d0-125">如果您希望知道某人是否可以与组织外部的用户进行通信，则必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a63d0-125">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="a63d0-126">确定为此用户分配的是哪种外部访问策略。</span><span class="sxs-lookup"><span data-stu-id="a63d0-126">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="a63d0-127">确定此策略允许的许可范围。</span><span class="sxs-lookup"><span data-stu-id="a63d0-127">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="a63d0-128">例如，您可以通过使用以下命令来执行此操作：</span><span class="sxs-lookup"><span data-stu-id="a63d0-128">For example, you can do that by using this command:</span></span>
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="a63d0-129">此命令可查找分配给用户的策略，然后查找该策略中启用或禁用的功能。</span><span class="sxs-lookup"><span data-stu-id="a63d0-129">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="a63d0-130">若要使用 PowerShell 管理 Skype for Business Online 策略，请参阅以下 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="a63d0-130">To manage Skype for Business Online policies with PowerShell, see the cmdlets for:</span></span>

- <span data-ttu-id="a63d0-131">[客户端策略](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="a63d0-131">[Client policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span></span>
- <span data-ttu-id="a63d0-132">[会议策略](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="a63d0-132">[Conferencing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span></span>
- <span data-ttu-id="a63d0-133">[移动策略](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="a63d0-133">[Mobile policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span></span>
- <span data-ttu-id="a63d0-134">[联机语音邮件策略](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="a63d0-134">[Online Voicemail policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span></span>
- <span data-ttu-id="a63d0-135">[语音路由策略](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="a63d0-135">[Voice Routing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span></span>


> [!NOTE]
> <span data-ttu-id="a63d0-136">Skype for Business Online 拨号计划是除了名称之外的每个方面的策略。</span><span class="sxs-lookup"><span data-stu-id="a63d0-136">A Skype for Business Online dial plan is a policy in every respect except the name.</span></span> <span data-ttu-id="a63d0-137">已选择名称 "拨号计划"，而不是 "拨号策略"，以便提供与 Office 通信服务器和 Exchange 的向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="a63d0-137">The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="a63d0-138">例如，若要查看所有可供使用的语音策略，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a63d0-138">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="a63d0-139">将返回所有可用的语音策略的列表。</span><span class="sxs-lookup"><span data-stu-id="a63d0-139">That returns a list of all the voice policies available to you.</span></span> <span data-ttu-id="a63d0-140">但请记住，并非所有策略都可以分配给所有用户。</span><span class="sxs-lookup"><span data-stu-id="a63d0-140">Keep in mind, however, that not all policies can be assigned to all users.</span></span> <span data-ttu-id="a63d0-141">这是由于涉及许可和地理位置的各种限制导致的。</span><span class="sxs-lookup"><span data-stu-id="a63d0-141">This is due to various restrictions involving licensing and geographic location.</span></span> <span data-ttu-id="a63d0-142">（所谓的 "[使用位置](https://msdn.microsoft.com/library/azure/dn194136.aspx)"）。如果要了解可分配给特定用户的外部访问策略和会议策略，请使用与以下命令类似的命令：</span><span class="sxs-lookup"><span data-stu-id="a63d0-142">(The so-called "[usage location](https://msdn.microsoft.com/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="a63d0-p106">ApplicableTo 参数可将返回的数据限制为可分配到特定用户的策略（例如，Alex Darrow）。根据不同的授权和使用位置限制，可能会代表所有可用策略的子集。</span><span class="sxs-lookup"><span data-stu-id="a63d0-p106">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="a63d0-145">在某些情况下，不会将策略的属性用于 Office 365，而有些则只能由 Microsoft 支持人员管理。</span><span class="sxs-lookup"><span data-stu-id="a63d0-145">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="a63d0-146">使用 Skype for Business Online，用户必须由某种类型的策略进行管理。</span><span class="sxs-lookup"><span data-stu-id="a63d0-146">With Skype for Business Online, users must be managed by a policy of some kind.</span></span> <span data-ttu-id="a63d0-147">如果与策略相关的有效属性为空，则表示有问题的用户将由全局策略管理，这是一个策略，该策略将自动应用于用户，除非专门为其分配了每用户策略。</span><span class="sxs-lookup"><span data-stu-id="a63d0-147">If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy.</span></span> <span data-ttu-id="a63d0-148">由于我们看不到为用户帐户列出的客户端策略，因此它由全局策略管理。</span><span class="sxs-lookup"><span data-stu-id="a63d0-148">Because we don't see a client policy listed for a user account, it is managed by the global policy.</span></span> <span data-ttu-id="a63d0-149">您可以使用此命令确定全局客户端策略：</span><span class="sxs-lookup"><span data-stu-id="a63d0-149">You can determine the global client policy with this command:</span></span>
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="a63d0-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a63d0-150">See also</span></span>

[<span data-ttu-id="a63d0-151">使用 Office 365 PowerShell 管理 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="a63d0-151">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="a63d0-152">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="a63d0-152">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a63d0-153">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="a63d0-153">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

