---
title: "管理 Skype 与 Office 365 PowerShell 的在线业务策略"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "摘要： 使用 Office 365 PowerShell 来管理您的 Skype 的在线业务策略的用户帐户属性。"
ms.openlocfilehash: 6698bd43b2a55e1c98fbe8e536a46e2de604b4d2
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="b82cf-103">管理 Skype 与 Office 365 PowerShell 的在线业务策略</span><span class="sxs-lookup"><span data-stu-id="b82cf-103">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="b82cf-104">**摘要：**使用 Office 365 PowerShell 来管理您的 Skype 的在线业务策略的用户帐户属性。</span><span class="sxs-lookup"><span data-stu-id="b82cf-104">**Summary:** Use Office 365 PowerShell to manage your Skype for Business Online user account properties with policies.</span></span>
  
<span data-ttu-id="b82cf-105">若要管理用户帐户的多个属性 Skype 的在线业务，必须先将它们指定为属性与 Office 365 PowerShell 的策略。</span><span class="sxs-lookup"><span data-stu-id="b82cf-105">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with Office 365 PowerShell.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="b82cf-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="b82cf-106">Before you begin</span></span>

<span data-ttu-id="b82cf-107">使用下列步骤来获取或设置到运行命令 （跳过您已完成的步骤）：</span><span class="sxs-lookup"><span data-stu-id="b82cf-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="b82cf-108">下载并安装[Skype 业务联机接口模块](https://www.microsoft.com/en-us/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="b82cf-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="b82cf-109">打开 Windows PowerShell 命令提示窗口并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b82cf-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="b82cf-110">出现提示时，输入您 Skype 的在线业务管理员帐户名和密码。</span><span class="sxs-lookup"><span data-stu-id="b82cf-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="b82cf-111">管理用户帐户策略</span><span class="sxs-lookup"><span data-stu-id="b82cf-111">Manage user account policies</span></span>

<span data-ttu-id="b82cf-p101">通过使用策略配置许多 Skype 的在线业务的用户帐户属性。策略是简单的可以应用到一个或多个用户的设置的集合。来看一看如何已配置策略，您可以运行此 FederationAndPICDefault 策略的示例命令：</span><span class="sxs-lookup"><span data-stu-id="b82cf-p101">Many Skype for Business Online user account properties are configured by using policies. Policies are simply collections of settings that can be applied to one or more users. To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="b82cf-115">反过来，您应该会收到与以下类似的内容：</span><span class="sxs-lookup"><span data-stu-id="b82cf-115">In turn, you should get back something similar to this:</span></span>
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="b82cf-p102">在此示例中，此策略中的值确定使用的可以或不能执行与联盟用户进行通信时。例如，EnableOutsideAccess 属性必须设置为 True，用户能够与组织外的人进行通讯。请注意，此属性不显示在 Office 365 管理中心。相反，属性自动设置为 True 或 False 基于您所做的其他选择。感兴趣的其他两个属性是：</span><span class="sxs-lookup"><span data-stu-id="b82cf-p102">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users. For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization. Note that this property does not appear in the Office 365 Admin center. Instead, the property is automatically set to True or False based on the other selections that you make. The other two properties of interest are:</span></span>
  
- <span data-ttu-id="b82cf-121">**EnableFederationAccess**表示用户是否可以与人的联盟域进行通信。</span><span class="sxs-lookup"><span data-stu-id="b82cf-121">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="b82cf-122">**EnablePublicCloudAccess**表示用户是否可以与 Windows Live 用户通信。</span><span class="sxs-lookup"><span data-stu-id="b82cf-122">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="b82cf-p103">因此，不要直接更改用户帐户 (例如，**集 CsUser EnableFederationAccess $True**) 与联合身份验证相关的属性。相反，您指定的帐户具有所需的属性值的预配置外部访问策略。我们希望用户能够与联盟用户和 Windows Live 用户进行通信，必须将该用户帐户分配策略允许的通信类型。</span><span class="sxs-lookup"><span data-stu-id="b82cf-p103">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**). Instead, you assign an account an external access policy that has the desired property values preconfigured. If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="b82cf-126">如果您想要知道有人可以与来自组织外部的用户进行通信，必须：</span><span class="sxs-lookup"><span data-stu-id="b82cf-126">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="b82cf-127">确定为此用户分配的是哪种外部访问策略。</span><span class="sxs-lookup"><span data-stu-id="b82cf-127">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="b82cf-128">确定此策略允许的许可范围。</span><span class="sxs-lookup"><span data-stu-id="b82cf-128">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="b82cf-129">例如，可以使用此命令执行的操作：</span><span class="sxs-lookup"><span data-stu-id="b82cf-129">For example, you can do that by using this command:</span></span>
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="b82cf-130">此命令查找指派给用户，然后查找功能启用或禁用该策略中的策略。</span><span class="sxs-lookup"><span data-stu-id="b82cf-130">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="b82cf-p104">请注意，有没有 cmdlet 用于创建或修改策略。您必须使用预先由 Office 365 提供的策略。如果您想要看一看不同的策略可用，您可以使用这些命令：</span><span class="sxs-lookup"><span data-stu-id="b82cf-p104">Note that there are no cmdlets for creating or for modifying policies. You must use the policies pre-supplied by Office 365. If you want to take a look at the different policies available, you can use these commands:</span></span>
  
- <span data-ttu-id="b82cf-134">获得 CsClientPolicy</span><span class="sxs-lookup"><span data-stu-id="b82cf-134">Get-CsClientPolicy</span></span>       
- <span data-ttu-id="b82cf-135">获得 CsConferencingPolicy</span><span class="sxs-lookup"><span data-stu-id="b82cf-135">Get-CsConferencingPolicy</span></span>        
- <span data-ttu-id="b82cf-136">获得 CsDialPlan</span><span class="sxs-lookup"><span data-stu-id="b82cf-136">Get-CsDialPlan</span></span>            
- <span data-ttu-id="b82cf-137">获得 CsExternalAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="b82cf-137">Get-CsExternalAccessPolicy</span></span>                         
- <span data-ttu-id="b82cf-138">获得 CsHostedVoicemailPolicy</span><span class="sxs-lookup"><span data-stu-id="b82cf-138">Get-CsHostedVoicemailPolicy</span></span>                        
- <span data-ttu-id="b82cf-139">获得 CsPresencePolicy</span><span class="sxs-lookup"><span data-stu-id="b82cf-139">Get-CsPresencePolicy</span></span>                               
- <span data-ttu-id="b82cf-140">获得 CsVoicePolicy</span><span class="sxs-lookup"><span data-stu-id="b82cf-140">Get-CsVoicePolicy</span></span>                                  

> [!NOTE]
> <span data-ttu-id="b82cf-p105">Skype 的在线业务的拨号计划是在除名称之外的每个方面的策略。"拨号计划"的名称选择而不是说，"拨号策略"与办公室通讯服务器和 Exchange 提供向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="b82cf-p105">A Skype for Business Online dial plan is a policy in every respect except the name. The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="b82cf-143">例如，要查找所有语音策略可供您使用，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b82cf-143">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="b82cf-p106">给您返回所有可用的语音策略的列表。请记住，但是，并非所有的策略可以指派给所有用户。这是由于各种涉及许可和地理位置的限制。（所谓"[使用位置](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx)。"）如果您想要知道的外部访问策略，可以分配给特定用户的会议策略，请使用类似如下的命令：</span><span class="sxs-lookup"><span data-stu-id="b82cf-p106">That returns a list of all the voice policies available to you. Keep in mind, however, that not all policies can be assigned to all users. This is due to various restrictions involving licensing and geographic location. (The so-called "[usage location](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="b82cf-p107">ApplicableTo 参数可将返回的数据限制为可分配到特定用户的策略（例如，Alex Darrow）。根据不同的授权和使用位置限制，可能会代表所有可用策略的子集。</span><span class="sxs-lookup"><span data-stu-id="b82cf-p107">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="b82cf-150">在某些情况下，属性策略不使用 Office 365，而其他人可以通过 Microsoft 技术支持人员进行管理。</span><span class="sxs-lookup"><span data-stu-id="b82cf-150">In some cases, properties of policies are not used with Office 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="b82cf-p108">与 Skype 的在线业务，必须由某种类型的策略管理用户。如果有效策略相关的属性为空，这意味着当前用户管理的全局策略，除非他或她专门分配的每个用户策略自动应用于用户的策略。因为我们看不到列出的用户帐户的客户端策略，它是由全球政策进行管理。您可以确定此命令的全局客户端策略：</span><span class="sxs-lookup"><span data-stu-id="b82cf-p108">With Skype for Business Online, users must be managed by a policy of some kind. If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy. Because we don't see a client policy listed for a user account, it is managed by the global policy. You can determine the global client policy with this command:</span></span>
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="b82cf-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b82cf-155">See also</span></span>

#### 

[<span data-ttu-id="b82cf-156">使用 Office 365 PowerShell 管理 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="b82cf-156">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="b82cf-157">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="b82cf-157">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b82cf-158">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="b82cf-158">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

