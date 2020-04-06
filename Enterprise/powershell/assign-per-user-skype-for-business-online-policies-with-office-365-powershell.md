---
title: 指定每个用户 Skype 的在线商业策略与 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 摘要：使用 Office 365 PowerShell 将每个用户的通信设置分配到 Skype for Business Online 策略。
ms.openlocfilehash: 615deca2790e206e6cf117283321307aa01eac74
ms.sourcegitcommit: f2aefbc2dbbe969fea9db3a4c558651496532413
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2020
ms.locfileid: "43146807"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="99b7d-103">指定每个用户 Skype 的在线商业策略与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="99b7d-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

<span data-ttu-id="99b7d-104">使用 Office 365 PowerShell 是一种将每个用户的通信设置分配到 Skype for Business Online 策略的有效方式。</span><span class="sxs-lookup"><span data-stu-id="99b7d-104">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="99b7d-105">准备工作</span><span class="sxs-lookup"><span data-stu-id="99b7d-105">Before you begin</span></span>

<span data-ttu-id="99b7d-106">使用以下说明设置运行命令（跳过已完成的步骤）：</span><span class="sxs-lookup"><span data-stu-id="99b7d-106">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="99b7d-107">下载并安装[Skype For Business Online 连接器模块](https://www.microsoft.com/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="99b7d-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="99b7d-108">打开 Windows PowerShell 命令提示符，并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="99b7d-108">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

<span data-ttu-id="99b7d-109">出现提示时，请输入你的 Skype for Business Online 管理员帐户名称和密码。</span><span class="sxs-lookup"><span data-stu-id="99b7d-109">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="99b7d-110">更新用户帐户的外部通信设置</span><span class="sxs-lookup"><span data-stu-id="99b7d-110">Updating external communication settings for a user account</span></span>

<span data-ttu-id="99b7d-111">假设您想要更改用户帐户上的外部通信设置。</span><span class="sxs-lookup"><span data-stu-id="99b7d-111">Suppose you want to change external communication settings on a user account.</span></span> <span data-ttu-id="99b7d-112">例如，您希望允许 Alex 与联合用户通信（EnableFederationAccess 等于 True），而不是 Windows Live 用户（EnablePublicCloudAccess 等于 False）。</span><span class="sxs-lookup"><span data-stu-id="99b7d-112">For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False).</span></span> <span data-ttu-id="99b7d-113">若要执行此操作，您需要执行以下两项操作：</span><span class="sxs-lookup"><span data-stu-id="99b7d-113">To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="99b7d-114">找到符合我们的条件的外部访问策略。</span><span class="sxs-lookup"><span data-stu-id="99b7d-114">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="99b7d-115">将该外部访问策略分配给 Alex。</span><span class="sxs-lookup"><span data-stu-id="99b7d-115">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="99b7d-116">您无法创建自己的自定义策略。</span><span class="sxs-lookup"><span data-stu-id="99b7d-116">You can't create a custom policy all our own.</span></span> <span data-ttu-id="99b7d-117">这是因为 Skype for Business Online 不允许您创建自定义策略。</span><span class="sxs-lookup"><span data-stu-id="99b7d-117">That's because Skype for Business Online does not allow you to create custom policies.</span></span> <span data-ttu-id="99b7d-118">而是必须分配专为 Office 365 创建的策略之一。</span><span class="sxs-lookup"><span data-stu-id="99b7d-118">Instead, you must assign one of the policies that were created specifically for Office 365.</span></span> <span data-ttu-id="99b7d-119">这些预创建的策略包括：4个不同的客户端策略、224不同的会议策略、5个不同的拨号计划、5个不同的外部访问策略、1个托管的语音邮件策略和4种不同的语音策略。</span><span class="sxs-lookup"><span data-stu-id="99b7d-119">Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="99b7d-120">那么，如何确定要分配 Alex 的外部访问策略？</span><span class="sxs-lookup"><span data-stu-id="99b7d-120">So how do you determine which external access policy to assign Alex?</span></span> <span data-ttu-id="99b7d-121">以下命令返回在 EnableFederationAccess 设置为 True 且 EnablePublicCloudAccess 设置为 False 时的所有外部访问策略：</span><span class="sxs-lookup"><span data-stu-id="99b7d-121">The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```powershell
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="99b7d-122">该命令的作用是返回满足两个条件的所有策略： EnableFederationAccess 属性设置为 True，EnablePublicCloudAccess 策略设置为 False。</span><span class="sxs-lookup"><span data-stu-id="99b7d-122">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False.</span></span> <span data-ttu-id="99b7d-123">反过来，该命令将返回一个符合我们的条件（FederationOnly）的策略。</span><span class="sxs-lookup"><span data-stu-id="99b7d-123">In turn, that command returns one policy that meets our criteria (FederationOnly).</span></span> <span data-ttu-id="99b7d-124">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="99b7d-124">Here is an example:</span></span>
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> <span data-ttu-id="99b7d-125">策略标识显示标记： FederationOnly。</span><span class="sxs-lookup"><span data-stu-id="99b7d-125">The policy Identity says Tag:FederationOnly.</span></span> <span data-ttu-id="99b7d-126">事实上，“Tag:”前缀是从 Microsoft Lync 2013 上的早期预发布工作中沿袭而来。</span><span class="sxs-lookup"><span data-stu-id="99b7d-126">As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013.</span></span> <span data-ttu-id="99b7d-127">向用户分配策略时，您应该删除“Tag:”前缀，只使用策略名称：FederationOnly。</span><span class="sxs-lookup"><span data-stu-id="99b7d-127">When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="99b7d-128">现在，您知道要向 Alex 分配的策略，我们可以使用[set-csexternalaccesspolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet 分配该策略。</span><span class="sxs-lookup"><span data-stu-id="99b7d-128">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet.</span></span> <span data-ttu-id="99b7d-129">如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="99b7d-129">Here is an example:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="99b7d-130">分配策略相当简单：只需指定用户的标识和要分配的策略的名称即可。</span><span class="sxs-lookup"><span data-stu-id="99b7d-130">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="99b7d-131">在考虑策略和策略分配时，您并不局限于一次性使用用户帐户。</span><span class="sxs-lookup"><span data-stu-id="99b7d-131">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time.</span></span> <span data-ttu-id="99b7d-132">例如，假设您需要获得可与联盟伙伴和 Windows Live 用户通信的所有用户的列表。</span><span class="sxs-lookup"><span data-stu-id="99b7d-132">For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users.</span></span> <span data-ttu-id="99b7d-133">我们已经知道，这些用户已分配有外部用户访问策略 FederationAndPICDefault。</span><span class="sxs-lookup"><span data-stu-id="99b7d-133">We already know that those users have been assigned the external user access policy FederationAndPICDefault.</span></span> <span data-ttu-id="99b7d-134">由于我们知道，您可以通过运行一个简单的命令来显示所有这些用户的列表。</span><span class="sxs-lookup"><span data-stu-id="99b7d-134">Because we know that, you can display a list of all those users by running one simple command.</span></span> <span data-ttu-id="99b7d-135">命令如下：</span><span class="sxs-lookup"><span data-stu-id="99b7d-135">Here is the command:</span></span>
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="99b7d-136">换言之，向我们显示 ExternalAccessPolicy 属性设置为 FederationAndPICDefault 的所有用户。</span><span class="sxs-lookup"><span data-stu-id="99b7d-136">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault.</span></span> <span data-ttu-id="99b7d-137">（为了限制屏幕上显示的信息量，请使用 Select-Object cmdlet 显示 "仅显示每个用户的显示名称"。）</span><span class="sxs-lookup"><span data-stu-id="99b7d-137">(And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="99b7d-138">若要将所有用户帐户配置为使用相同的策略，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="99b7d-138">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="99b7d-139">此命令使用 Get-csonlineuser 返回已启用 Lync 的所有用户的集合，然后将所有这些信息发送给 Set-csexternalaccesspolicy，这会将 FederationAndPICDefault 策略分配给集合中的每个用户和每个用户。</span><span class="sxs-lookup"><span data-stu-id="99b7d-139">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="99b7d-140">作为另一个示例，假设您之前已将 Alex 分配给 FederationAndPICDefault 策略，现在您已改变了想法，并希望由全局外部访问策略管理他。</span><span class="sxs-lookup"><span data-stu-id="99b7d-140">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy.</span></span> <span data-ttu-id="99b7d-141">您不能将全局策略明确分配给任何人。</span><span class="sxs-lookup"><span data-stu-id="99b7d-141">You can't explicitly assign the global policy to anyone.</span></span> <span data-ttu-id="99b7d-142">仅在分配了其他每个用户的策略时才使用它。</span><span class="sxs-lookup"><span data-stu-id="99b7d-142">It is only used if no other per-user policy is assigned.</span></span> <span data-ttu-id="99b7d-143">因此，如果我们想要由全局策略管理 Alex，则需要*取消*分配之前分配给他的任何每用户策略。</span><span class="sxs-lookup"><span data-stu-id="99b7d-143">Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him.</span></span> <span data-ttu-id="99b7d-144">下面是一个示例命令：</span><span class="sxs-lookup"><span data-stu-id="99b7d-144">Here is an example command:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="99b7d-145">此命令将向 Alex 分配的外部访问策略的名称设置为一个 null 值（$Null）。</span><span class="sxs-lookup"><span data-stu-id="99b7d-145">This command sets the name of the external access policy assigned to Alex to a null value ($Null).</span></span> <span data-ttu-id="99b7d-146">空值表示 "nothing"。</span><span class="sxs-lookup"><span data-stu-id="99b7d-146">Null means "nothing".</span></span> <span data-ttu-id="99b7d-147">换言之，没有向 Alex 分配任何外部访问策略。</span><span class="sxs-lookup"><span data-stu-id="99b7d-147">In other words, no external access policy is assigned to Alex.</span></span> <span data-ttu-id="99b7d-148">如果没有向用户分配任何外部访问策略，则该用户将由全局策略进行管理。</span><span class="sxs-lookup"><span data-stu-id="99b7d-148">When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="99b7d-149">若要使用 Windows PowerShell 禁用用户帐户，请使用 Azure Active Directory cmdlet 删除 Alex 的 Skype for Business Online 许可证。</span><span class="sxs-lookup"><span data-stu-id="99b7d-149">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license.</span></span> <span data-ttu-id="99b7d-150">有关详细信息，请参阅[禁用对具有 Office 365 PowerShell 的服务的访问](assign-licenses-to-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="99b7d-150">For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>

## <a name="managing-large-numbers-of-users"></a><span data-ttu-id="99b7d-151">管理大量用户</span><span class="sxs-lookup"><span data-stu-id="99b7d-151">Managing large numbers of users</span></span>

<span data-ttu-id="99b7d-152">若要管理大量用户（1000或更多），您需要通过使用[调用命令](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7)cmdlet 的脚本块对命令进行批处理。</span><span class="sxs-lookup"><span data-stu-id="99b7d-152">To manage large numbers of users (1000 or more), you need to batch the commands via a script block using the [Invoke-Command](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) cmdlet.</span></span>  <span data-ttu-id="99b7d-153">在前面的示例中，每次执行 cmdlet 时，都必须先设置调用，然后等待结果，然后再将其发送回来。</span><span class="sxs-lookup"><span data-stu-id="99b7d-153">In previous examples, each time a cmdlet is executed, it must set up the call and then wait for the result before sending it back.</span></span>  <span data-ttu-id="99b7d-154">使用脚本块时，可以远程执行 cmdlet，并在完成后将数据发送回来。</span><span class="sxs-lookup"><span data-stu-id="99b7d-154">When using a script block, this allows the cmdlets to be executed remotely, and once completed, send the data back.</span></span> 

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

<span data-ttu-id="99b7d-155">这将在没有客户端策略的时候发现500个用户。</span><span class="sxs-lookup"><span data-stu-id="99b7d-155">This will find 500 users at a time who do not have a client policy.</span></span> <span data-ttu-id="99b7d-156">它将向他们授予客户端策略 "ClientPolicyNoIMURL" 和外部访问策略 "FederationAndPicDefault"。</span><span class="sxs-lookup"><span data-stu-id="99b7d-156">It will grant them the client policy "ClientPolicyNoIMURL" and the external access policy "FederationAndPicDefault".</span></span> <span data-ttu-id="99b7d-157">结果成批分组为50，每批50将被发送到远程计算机。</span><span class="sxs-lookup"><span data-stu-id="99b7d-157">The results are batched into groups of 50 and each batch of 50 is then sent to the remote machine.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="99b7d-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99b7d-158">See also</span></span>

[<span data-ttu-id="99b7d-159">使用 Office 365 PowerShell 管理 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="99b7d-159">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="99b7d-160">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="99b7d-160">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="99b7d-161">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="99b7d-161">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
