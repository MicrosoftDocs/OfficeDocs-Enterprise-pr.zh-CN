---
title: 使用 PowerShell 管理 Skype for Business Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要：使用 PowerShell for Microsoft 365 管理 Skype for Business Online 策略、每用户策略和会议设置。
ms.openlocfilehash: 10587dad171c3df9de6985ad314bc1791080b8a1
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592206"
---
# <a name="manage-skype-for-business-online-with-powershell"></a><span data-ttu-id="ba079-103">使用 PowerShell 管理 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="ba079-103">Manage Skype for Business Online with PowerShell</span></span>

<span data-ttu-id="ba079-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="ba079-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="ba079-105">任何 Skype for Business Online 管理员的主要任务之一是管理策略。</span><span class="sxs-lookup"><span data-stu-id="ba079-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="ba079-106">虽然你可以在 Microsoft 365 管理中心中完成其中的一些任务，但通过 PowerShell 你可以更快、更轻松地完成其他任务。</span><span class="sxs-lookup"><span data-stu-id="ba079-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="ba079-107">准备工作</span><span class="sxs-lookup"><span data-stu-id="ba079-107">Before you start</span></span>

<span data-ttu-id="ba079-108">下载并安装 [Skype for Business Online 连接器模块](https://www.microsoft.com/download/details.aspx?id=39366)，然后重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="ba079-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="ba079-109">使用 Skype for Business Online 管理员帐户名称和密码进行连接</span><span class="sxs-lookup"><span data-stu-id="ba079-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="ba079-110">开启 Windows PowerShell 命令提示符并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ba079-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="ba079-111">在 **“Windows PowerShell 凭据请求”** 对话框中，键入你的 Skype for Business Online 管理员帐户名和密码，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="ba079-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="ba079-112">使用具有多重身份验证的 Skype for Business Online 管理员帐户进行连接</span><span class="sxs-lookup"><span data-stu-id="ba079-112">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="ba079-113">开启 Windows PowerShell 命令提示符并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ba079-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. <span data-ttu-id="ba079-114">当出现 **New-CsOnlineSession** 命令提示时，请输入 Skype for Business Online 管理员帐户名称。</span><span class="sxs-lookup"><span data-stu-id="ba079-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="ba079-115">在 **“登录到你的帐户”** 对话框中，键入你的 Skype for Business Online 管理员密码，然后单击 **“登录”**。</span><span class="sxs-lookup"><span data-stu-id="ba079-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="ba079-116">按照 **“登录到你的帐户”** 对话框中的说明提供其他验证信息（如验证码），然后单击 **“登录”**。</span><span class="sxs-lookup"><span data-stu-id="ba079-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="ba079-117">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="ba079-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="ba079-118">使用 PowerShell 管理 Skype for Business Online 策略</span><span class="sxs-lookup"><span data-stu-id="ba079-118">Manage Skype for Business Online policies with PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="ba079-119">使用 PowerShell 指定每个用户 Skype for Business Online 策略</span><span class="sxs-lookup"><span data-stu-id="ba079-119">Assign per-user Skype for Business Online policies with PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="ba079-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba079-120">See also</span></span>

[<span data-ttu-id="ba079-121">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ba079-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ba079-122">PowerShell for Microsoft 365 入门</span><span class="sxs-lookup"><span data-stu-id="ba079-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="ba079-123">Skype for Business PowerShell cmdlet 参考</span><span class="sxs-lookup"><span data-stu-id="ba079-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

