---
title: 为 Microsoft 365 的 PowerShell 分配每用户 Skype for Business Online 策略
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 摘要：使用适用于 Microsoft 365 的 PowerShell 为 Skype for Business Online 策略分配每用户通信设置。
ms.openlocfilehash: a5850c24f991161ec1de817d5b3f5037e9526767
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606458"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a><span data-ttu-id="c3d6a-103">为 Microsoft 365 的 PowerShell 分配每用户 Skype for Business Online 策略</span><span class="sxs-lookup"><span data-stu-id="c3d6a-103">Assign per-user Skype for Business Online policies with PowerShell for Microsoft 365</span></span>

<span data-ttu-id="c3d6a-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="c3d6a-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c3d6a-105">使用 PowerShell for Microsoft 365 是将每个用户的通信设置分配到 Skype for Business Online 策略的有效方式。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-105">Using PowerShell for Microsoft 365 is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="prepare-to-run-the-powershell-commands"></a><span data-ttu-id="c3d6a-106">准备运行 PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="c3d6a-106">Prepare to run the PowerShell commands</span></span>

<span data-ttu-id="c3d6a-107">使用以下说明设置运行命令 (跳过已完成的步骤) ：</span><span class="sxs-lookup"><span data-stu-id="c3d6a-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="c3d6a-108">下载并安装[Skype For Business Online 连接器模块](https://www.microsoft.com/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="c3d6a-109">开启 Windows PowerShell 命令提示符并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="c3d6a-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

<span data-ttu-id="c3d6a-110">出现提示时，请输入你的 Skype for Business Online 管理员帐户名称和密码。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="c3d6a-111">更新用户帐户的外部通信设置</span><span class="sxs-lookup"><span data-stu-id="c3d6a-111">Updating external communication settings for a user account</span></span>

<span data-ttu-id="c3d6a-112">假设您想要更改用户帐户上的外部通信设置。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-112">Suppose you want to change external communication settings on a user account.</span></span> <span data-ttu-id="c3d6a-113">例如，您希望允许 Alex 与联盟用户通信 (EnableFederationAccess 等于 True) 而不是 Windows Live 用户 (EnablePublicCloudAccess 等于 False) 。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-113">For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False).</span></span> <span data-ttu-id="c3d6a-114">若要执行此操作，您需要执行以下两项操作：</span><span class="sxs-lookup"><span data-stu-id="c3d6a-114">To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="c3d6a-115">找到符合我们的条件的外部访问策略。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-115">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="c3d6a-116">将该外部访问策略分配给 Alex。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-116">Assign that external access policy to Alex.</span></span>
    
<span data-ttu-id="c3d6a-117">如何确定要为其分配 Alex 的外部访问策略？</span><span class="sxs-lookup"><span data-stu-id="c3d6a-117">How do you determine which external access policy to assign Alex?</span></span> <span data-ttu-id="c3d6a-118">以下命令返回在 EnableFederationAccess 设置为 True 且 EnablePublicCloudAccess 设置为 False 时的所有外部访问策略：</span><span class="sxs-lookup"><span data-stu-id="c3d6a-118">The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="c3d6a-119">除非您已创建 ExternalAccessPolicy 的任何自定义实例，否则该命令将返回一个策略，该策略符合我们的标准 (FederationOnly) 。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-119">Unless you have created any custom instances of ExternalAccessPolicy, that command returns one policy that meets our criteria (FederationOnly).</span></span> <span data-ttu-id="c3d6a-120">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="c3d6a-120">Here is an example:</span></span>
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

<span data-ttu-id="c3d6a-121">现在，您知道要向 Alex 分配的策略，我们可以使用[set-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet 分配该策略。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-121">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet.</span></span> <span data-ttu-id="c3d6a-122">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="c3d6a-122">Here is an example:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="c3d6a-123">分配策略相当简单：只需指定用户的标识和要分配的策略的名称即可。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-123">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="c3d6a-124">在考虑策略和策略分配时，您并不局限于一次性使用用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-124">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time.</span></span> <span data-ttu-id="c3d6a-125">例如，假设您需要获得可与联盟伙伴和 Windows Live 用户通信的所有用户的列表。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-125">For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users.</span></span> <span data-ttu-id="c3d6a-126">我们已经知道，这些用户已分配有外部用户访问策略 FederationAndPICDefault。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-126">We already know that those users have been assigned the external user access policy FederationAndPICDefault.</span></span> <span data-ttu-id="c3d6a-127">由于我们知道，您可以通过运行一个简单的命令来显示所有这些用户的列表。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-127">Because we know that, you can display a list of all those users by running one simple command.</span></span> <span data-ttu-id="c3d6a-128">命令如下：</span><span class="sxs-lookup"><span data-stu-id="c3d6a-128">Here is the command:</span></span>
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="c3d6a-129">换言之，向我们显示 ExternalAccessPolicy 属性设置为 FederationAndPICDefault 的所有用户。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-129">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault.</span></span> <span data-ttu-id="c3d6a-130"> (，为了限制屏幕上显示的信息量，请使用 Select-Object cmdlet 显示 "仅显示每个用户的显示名称"。 ) </span><span class="sxs-lookup"><span data-stu-id="c3d6a-130">(And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="c3d6a-131">若要将所有用户帐户配置为使用相同的策略，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="c3d6a-131">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="c3d6a-132">此命令使用 Get-csonlineuser 返回已启用 Lync 的所有用户的集合，然后将所有这些信息发送给 Set-csexternalaccesspolicy，这会将 FederationAndPICDefault 策略分配给集合中的每个用户和每个用户。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-132">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="c3d6a-133">作为另一个示例，假设您之前已将 Alex 分配给 FederationAndPICDefault 策略，现在您已改变了想法，并希望由全局外部访问策略管理他。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-133">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy.</span></span> <span data-ttu-id="c3d6a-134">您不能将全局策略明确分配给任何人。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-134">You can't explicitly assign the global policy to anyone.</span></span> <span data-ttu-id="c3d6a-135">相反，如果没有为用户分配每用户策略，则将全局策略用于指定的用户。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-135">Instead, the global policy is used for a given user if no per-user policy is assigned to that user.</span></span> <span data-ttu-id="c3d6a-136">因此，如果我们想要由全局策略管理 Alex，则需要*取消*分配之前分配给他的任何每用户策略。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-136">Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him.</span></span> <span data-ttu-id="c3d6a-137">下面是一个示例命令：</span><span class="sxs-lookup"><span data-stu-id="c3d6a-137">Here is an example command:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="c3d6a-138">此命令将向 Alex 分配的外部访问策略的名称设置为 $Null)  (null 值。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-138">This command sets the name of the external access policy assigned to Alex to a null value ($Null).</span></span> <span data-ttu-id="c3d6a-139">空值表示 "nothing"。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-139">Null means "nothing".</span></span> <span data-ttu-id="c3d6a-140">换言之，没有向 Alex 分配任何外部访问策略。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-140">In other words, no external access policy is assigned to Alex.</span></span> <span data-ttu-id="c3d6a-141">如果没有向用户分配任何外部访问策略，则该用户将由全局策略进行管理。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-141">When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  

## <a name="managing-large-numbers-of-users"></a><span data-ttu-id="c3d6a-142">管理大量用户</span><span class="sxs-lookup"><span data-stu-id="c3d6a-142">Managing large numbers of users</span></span>

<span data-ttu-id="c3d6a-143">若要管理大量用户 (1000 或更多) ，您需要通过使用[调用命令](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7)cmdlet 的脚本块对命令进行批处理。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-143">To manage large numbers of users (1000 or more), you need to batch the commands via a script block using the [Invoke-Command](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) cmdlet.</span></span>  <span data-ttu-id="c3d6a-144">在前面的示例中，每次执行 cmdlet 时，都必须先设置调用，然后等待结果，然后再将其发送回来。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-144">In previous examples, each time a cmdlet is executed, it must set up the call and then wait for the result before sending it back.</span></span>  <span data-ttu-id="c3d6a-145">使用脚本块时，可以远程执行 cmdlet，并在完成后将数据发送回来。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-145">When using a script block, this allows the cmdlets to be executed remotely, and once completed, send the data back.</span></span> 

```powershell
Import-Module LyncOnlineConnector
$sfbSession = New-CsOnlineSession
$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

<span data-ttu-id="c3d6a-146">这将在没有客户端策略的时候发现500个用户。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-146">This will find 500 users at a time who do not have a client policy.</span></span> <span data-ttu-id="c3d6a-147">它将向他们授予客户端策略 "ClientPolicyNoIMURL" 和外部访问策略 "FederationAndPicDefault"。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-147">It will grant them the client policy "ClientPolicyNoIMURL" and the external access policy "FederationAndPicDefault".</span></span> <span data-ttu-id="c3d6a-148">结果成批分组为50，每批50将被发送到远程计算机。</span><span class="sxs-lookup"><span data-stu-id="c3d6a-148">The results are batched into groups of 50 and each batch of 50 is then sent to the remote machine.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c3d6a-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3d6a-149">See also</span></span>

[<span data-ttu-id="c3d6a-150">使用 PowerShell 管理 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="c3d6a-150">Manage Skype for Business Online with PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="c3d6a-151">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c3d6a-151">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c3d6a-152">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="c3d6a-152">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
