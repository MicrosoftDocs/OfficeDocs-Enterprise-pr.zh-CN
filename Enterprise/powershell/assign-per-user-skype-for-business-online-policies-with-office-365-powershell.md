---
title: "指定每个用户 Skype 的在线商业策略与 Office 365 PowerShell"
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
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: "摘要： 使用 Office 365 PowerShell 将每个用户分配与 Skype 的在线商业策略的通信设置。"
ms.openlocfilehash: 7f819b619c5b3607c98c10791fe30c3944e862a4
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="90af5-103">指定每个用户 Skype 的在线商业策略与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="90af5-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

 <span data-ttu-id="90af5-104">**摘要：**使用 Office 365 PowerShell 分配与 Skype 的在线商业策略的通信设置的每个用户。</span><span class="sxs-lookup"><span data-stu-id="90af5-104">**Summary:** Use Office 365 PowerShell to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
<span data-ttu-id="90af5-105">使用 Office 365 PowerShell 是分配与 Skype 的在线商业策略的通信设置的每个用户的有效方法。</span><span class="sxs-lookup"><span data-stu-id="90af5-105">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="90af5-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="90af5-106">Before you begin</span></span>

<span data-ttu-id="90af5-107">使用下列步骤来获取或设置到运行命令 （跳过您已完成的步骤）：</span><span class="sxs-lookup"><span data-stu-id="90af5-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="90af5-108">下载并安装[Skype 业务联机接口模块](https://www.microsoft.com/en-us/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="90af5-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="90af5-109">打开 Windows PowerShell 命令提示窗口并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="90af5-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
<span data-ttu-id="90af5-110">出现提示时，输入您 Skype 的在线业务管理员帐户名和密码。</span><span class="sxs-lookup"><span data-stu-id="90af5-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="90af5-111">更新外部通信设置的用户帐户</span><span class="sxs-lookup"><span data-stu-id="90af5-111">Updating external communication settings for a user account</span></span>

<span data-ttu-id="90af5-p101">假设您想要更改的用户帐户上的外部通信设置。例如，您想要允许 Alex 通信与联盟 （EnableFederationAccess 等于 True） 的用户，但不是能与 Windows Live 的用户 （EnablePublicCloudAccess 等于 False）。要做到这一点，您需要做两件事：</span><span class="sxs-lookup"><span data-stu-id="90af5-p101">Suppose you want to change external communication settings on a user account. For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False). To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="90af5-115">找到符合我们的条件的外部访问策略。</span><span class="sxs-lookup"><span data-stu-id="90af5-115">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="90af5-116">将该外部访问策略分配给 Alex。</span><span class="sxs-lookup"><span data-stu-id="90af5-116">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="90af5-p102">您不能创建所有的自定义策略我们自己。这是因为 Skype 的在线业务不允许您创建自定义策略。相反，您必须指定创建专为 Office 365 的策略之一。那些先前创建的策略包括： 4 个不同的客户端策略、 224 不同的会议策略、 5 不同的拨号计划、 5 个不同的外部访问策略、 1 承载语音邮件策略和 4 不同语音策略。</span><span class="sxs-lookup"><span data-stu-id="90af5-p102">You can't create a custom policy all our own. That's because Skype for Business Online does not allow you to create custom policies. Instead, you must assign one of the policies that were created specifically for Office 365. Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="90af5-p103">那么，如何确定要分配 Alex 的外部访问策略？下面的命令将返回所有外部访问策略位置设置为 True 时 EnableFederationAccess 和 EnablePublicCloudAccess 设置为 False:</span><span class="sxs-lookup"><span data-stu-id="90af5-p103">So how do you determine which external access policy to assign Alex? The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="90af5-p104">该命令的作用是返回所有满足两个条件的策略： EnableFederationAccess 属性设置为 True，并将 EnablePublicCloudAccess 策略设置为 False。反过来，该命令将返回一个符合我们的标准 (FederationOnly) 的策略。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="90af5-p104">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False. In turn, that command returns one policy that meets our criteria (FederationOnly). Here is an example:</span></span>
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> <span data-ttu-id="90af5-p105">该策略的身份说标记： FederationOnly。标记出事实： 前缀是 carryover 从 Microsoft Lync 2013 执行的早期预发行工作。向用户分配策略时，您应该删除标记： 前缀和只使用策略名称： FederationOnly。</span><span class="sxs-lookup"><span data-stu-id="90af5-p105">The policy Identity says Tag:FederationOnly. As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013. When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="90af5-p106">现在，您知道要将分配给 Alex 的策略，我们可以将此策略分配通过[授予 CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet。下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="90af5-p106">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet. Here is an example:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="90af5-131">分配策略是非常简单： 您只需指定用户的标识和分配策略的名称。</span><span class="sxs-lookup"><span data-stu-id="90af5-131">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="90af5-p107">并且对策略和策略分配时，您并不局限于处理用户帐户一次。例如，假设您需要允许与联盟伙伴和 Windows Live 用户进行通信的所有用户的列表。我们已经知道这些用户具有已分配的外部用户访问策略 FederationAndPICDefault。因为我们知道，您可以通过运行一个简单的命令显示所有这些用户的列表。以下是该命令：</span><span class="sxs-lookup"><span data-stu-id="90af5-p107">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time. For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users. We already know that those users have been assigned the external user access policy FederationAndPICDefault. Because we know that, you can display a list of all those users by running one simple command. Here is the command:</span></span>
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="90af5-p108">换句话说，显示我们所有用户在将 ExternalAccessPolicy 属性设置为 FederationAndPICDefault。（而且，限制出现在屏幕上的信息，以便使用选择对象用于显示向我们显示只使用每个用户的显示名称。</span><span class="sxs-lookup"><span data-stu-id="90af5-p108">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault. (And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="90af5-139">若要配置我们的所有用户帐户，使用该同一策略，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="90af5-139">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="90af5-140">此命令使用 Get CsOnlineUser 返回的已启用的 Lync，然后将所有这些信息发送到授权-CsExternalAccessPolicy，FederationAndPICDefault 策略为集合中的每个用户的所有用户的集合。</span><span class="sxs-lookup"><span data-stu-id="90af5-140">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="90af5-p109">作为一个附加的示例，假设您以前归入 Alex FederationAndPICDefault 策略，现在改变了主意并想要他由全球外部访问策略管理。任何人，不能明确指定全局策略。指定任何其他每用户策略时才使用它。因此，如果我们希望 Alex 通过全球政策进行管理，需要*取消指定*任何以前分配给他的每个用户策略。下面是一个示例命令：</span><span class="sxs-lookup"><span data-stu-id="90af5-p109">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy. You can't explicitly assign the global policy to anyone. It is only used if no other per-user policy is assigned. Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him. Here is an example command:</span></span>
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="90af5-p110">该命令设置为空值 ($Null) 分配给 Alex 外部访问策略的名称。空值表示"没有"。换句话说，没有外部访问策略分配给 Alex。没有外部访问策略分配给用户后，该用户再获取全局策略管理。</span><span class="sxs-lookup"><span data-stu-id="90af5-p110">This command sets the name of the external access policy assigned to Alex to a null value ($Null). Null means "nothing". In other words, no external access policy is assigned to Alex. When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="90af5-p111">若要禁用用户帐户使用 Windows PowerShell，使用 Azure Active Directory cmdlet 删除 Alex 的 Skype 的在线业务许可证。有关详细信息，请参阅[禁用 Office 365 PowerShell 的服务访问](assign-licenses-to-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="90af5-p111">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license. For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="90af5-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90af5-152">See also</span></span>

#### 

[<span data-ttu-id="90af5-153">使用 Office 365 PowerShell 管理 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="90af5-153">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="90af5-154">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="90af5-154">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="90af5-155">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="90af5-155">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

