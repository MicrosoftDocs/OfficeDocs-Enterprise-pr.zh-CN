---
title: 使用 Office 365 PowerShell 管理 Skype for Business Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要：使用 Office 365 PowerShell 管理 Skype for Business Online 策略、每用户策略和会议设置。
ms.openlocfilehash: 699f799e823df6192a65147210130ae6493f52eb
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844223"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="fc287-103">使用 Office 365 PowerShell 管理 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="fc287-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

<span data-ttu-id="fc287-104">Skype for Business Online 管理员的一项主要任务就是管理策略。</span><span class="sxs-lookup"><span data-stu-id="fc287-104">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="fc287-105">虽然你可以在 Microsoft 365 管理中心中完成其中的一些任务，但通过 Office 365 PowerShell 你可以更快、更轻松地完成其他任务。</span><span class="sxs-lookup"><span data-stu-id="fc287-105">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="fc287-106">准备工作</span><span class="sxs-lookup"><span data-stu-id="fc287-106">Before you start</span></span>

<span data-ttu-id="fc287-107">下载并安装[Skype For Business Online 连接器模块](https://www.microsoft.com/download/details.aspx?id=39366)，然后在出现提示时重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="fc287-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="fc287-108">使用 Skype for Business Online 管理员帐户名称和密码进行连接</span><span class="sxs-lookup"><span data-stu-id="fc287-108">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="fc287-109">打开 Windows PowerShell 命令提示符，并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="fc287-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="fc287-110">在 " **Windows PowerShell 凭据请求**" 对话框中，键入您的 Skype For business Online 管理员帐户名称和密码，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="fc287-110">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="fc287-111">使用具有多重身份验证的 Skype for Business Online 管理员帐户进行连接</span><span class="sxs-lookup"><span data-stu-id="fc287-111">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="fc287-112">打开 Windows PowerShell 命令提示符，并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="fc287-112">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="fc287-113">当**CsOnlineSession**命令出现提示时，请输入你的 Skype For business Online 管理员帐户名称。</span><span class="sxs-lookup"><span data-stu-id="fc287-113">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="fc287-114">在 "**登录帐户**" 对话框中，键入您的 Skype For business Online 管理员密码，然后单击 "**登录**"。</span><span class="sxs-lookup"><span data-stu-id="fc287-114">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="fc287-115">按照 "**登录到帐户**" 对话框中的说明提供其他身份验证信息（如验证码），然后单击 "**验证**"。</span><span class="sxs-lookup"><span data-stu-id="fc287-115">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="fc287-116">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="fc287-116">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="fc287-117">管理 Skype 与 Office 365 PowerShell 的在线业务策略</span><span class="sxs-lookup"><span data-stu-id="fc287-117">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="fc287-118">指定每个用户 Skype 的在线商业策略与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc287-118">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="fc287-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc287-119">See also</span></span>

[<span data-ttu-id="fc287-120">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="fc287-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="fc287-121">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="fc287-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="fc287-122">Skype for Business PowerShell cmdlet 参考</span><span class="sxs-lookup"><span data-stu-id="fc287-122">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

