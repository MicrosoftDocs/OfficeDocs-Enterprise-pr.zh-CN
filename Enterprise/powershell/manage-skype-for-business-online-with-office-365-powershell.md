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
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要：使用 Office 365 PowerShell 管理 Skype for Business Online 策略、每用户策略和会议设置。
ms.openlocfilehash: 48b10038e396953469f4b0732103671cbc6b0d75
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030937"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="2dafa-103">使用 Office 365 PowerShell 管理 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="2dafa-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="2dafa-104">**摘要：** 使用 Office 365 PowerShell 管理 Skype for Business Online 策略、每用户策略和会议设置。</span><span class="sxs-lookup"><span data-stu-id="2dafa-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="2dafa-105">Skype for Business Online 管理员的一项主要任务就是管理策略。</span><span class="sxs-lookup"><span data-stu-id="2dafa-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="2dafa-106">虽然你可以在 Microsoft 365 管理中心中完成其中的一些任务，但通过 Office 365 PowerShell 你可以更快、更轻松地完成其他任务。</span><span class="sxs-lookup"><span data-stu-id="2dafa-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="2dafa-107">准备工作</span><span class="sxs-lookup"><span data-stu-id="2dafa-107">Before you start</span></span>

<span data-ttu-id="2dafa-108">下载并安装[Skype For Business Online 连接器模块](https://www.microsoft.com/download/details.aspx?id=39366)，然后在出现提示时重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="2dafa-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="2dafa-109">使用 Skype for Business Online 管理员帐户名称和密码进行连接</span><span class="sxs-lookup"><span data-stu-id="2dafa-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="2dafa-110">打开 Windows PowerShell 命令提示符，并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2dafa-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="2dafa-111">在 " **Windows PowerShell 凭据请求**" 对话框中，键入您的 Skype For business Online 管理员帐户名称和密码，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="2dafa-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="2dafa-112">使用具有多重身份验证的 Skype for Business Online 管理员帐户进行连接</span><span class="sxs-lookup"><span data-stu-id="2dafa-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="2dafa-113">打开 Windows PowerShell 命令提示符，并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2dafa-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="2dafa-114">当**CsOnlineSession**命令出现提示时，请输入你的 Skype For business Online 管理员帐户名称。</span><span class="sxs-lookup"><span data-stu-id="2dafa-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="2dafa-115">在 "**登录帐户**" 对话框中，键入您的 Skype For business Online 管理员密码，然后单击 "**登录**"。</span><span class="sxs-lookup"><span data-stu-id="2dafa-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="2dafa-116">按照 "**登录到帐户**" 对话框中的说明提供其他身份验证信息（如验证码），然后单击 "**验证**"。</span><span class="sxs-lookup"><span data-stu-id="2dafa-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="2dafa-117">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="2dafa-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="2dafa-118">管理 Skype 与 Office 365 PowerShell 的在线业务策略</span><span class="sxs-lookup"><span data-stu-id="2dafa-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="2dafa-119">指定每个用户 Skype 的在线商业策略与 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2dafa-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="2dafa-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2dafa-120">See also</span></span>

[<span data-ttu-id="2dafa-121">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="2dafa-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2dafa-122">Office 365 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="2dafa-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="2dafa-123">Skype for Business PowerShell cmdlet 参考</span><span class="sxs-lookup"><span data-stu-id="2dafa-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

