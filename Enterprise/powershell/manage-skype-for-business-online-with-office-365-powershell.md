---
title: 使用 PowerShell 管理 Skype for Business Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 摘要：使用适用于 Microsoft 365 的 PowerShell 管理 Skype for Business Online 策略、每用户策略和会议设置。
ms.openlocfilehash: f66b3186a5b29bbf0756a629b85c626caf2c1e36
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230438"
---
# <a name="manage-skype-for-business-online-with-powershell"></a><span data-ttu-id="d0ba9-103">使用 PowerShell 管理 Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="d0ba9-103">Manage Skype for Business Online with PowerShell</span></span>

<span data-ttu-id="d0ba9-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="d0ba9-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="d0ba9-105">Skype for Business Online 管理员的一项主要任务就是管理策略。</span><span class="sxs-lookup"><span data-stu-id="d0ba9-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="d0ba9-106">虽然您可以在 Microsoft 365 管理中心完成其中的部分任务，但在 PowerShell 中，其他任务的工作速度更快、更轻松。</span><span class="sxs-lookup"><span data-stu-id="d0ba9-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="d0ba9-107">准备工作</span><span class="sxs-lookup"><span data-stu-id="d0ba9-107">Before you start</span></span>

<span data-ttu-id="d0ba9-108">下载并安装[Skype For Business Online 连接器模块](https://www.microsoft.com/download/details.aspx?id=39366)，然后重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="d0ba9-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="d0ba9-109">使用 Skype for Business Online 管理员帐户名称和密码进行连接</span><span class="sxs-lookup"><span data-stu-id="d0ba9-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="d0ba9-110">打开 Windows PowerShell 命令提示符，并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d0ba9-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="d0ba9-111">在 " **Windows PowerShell 凭据请求**" 对话框中，键入您的 Skype For business Online 管理员帐户名称和密码，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="d0ba9-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="d0ba9-112">使用具有多因素身份验证的 Skype for Business Online 管理员帐户进行连接</span><span class="sxs-lookup"><span data-stu-id="d0ba9-112">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="d0ba9-113">打开 Windows PowerShell 命令提示符，并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d0ba9-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="d0ba9-114">当**CsOnlineSession**命令出现提示时，请输入你的 Skype For business Online 管理员帐户名称。</span><span class="sxs-lookup"><span data-stu-id="d0ba9-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="d0ba9-115">在 "**登录帐户**" 对话框中，键入您的 Skype For business Online 管理员密码，然后单击 "**登录**"。</span><span class="sxs-lookup"><span data-stu-id="d0ba9-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="d0ba9-116">按照 "**登录到帐户**" 对话框中的说明提供其他身份验证信息（如验证码），然后单击 "**验证**"。</span><span class="sxs-lookup"><span data-stu-id="d0ba9-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="d0ba9-117">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="d0ba9-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="d0ba9-118">使用 PowerShell 管理 Skype for Business Online 策略</span><span class="sxs-lookup"><span data-stu-id="d0ba9-118">Manage Skype for Business Online policies with PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="d0ba9-119">使用 PowerShell 分配每用户 Skype for Business Online 策略</span><span class="sxs-lookup"><span data-stu-id="d0ba9-119">Assign per-user Skype for Business Online policies with PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="d0ba9-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0ba9-120">See also</span></span>

[<span data-ttu-id="d0ba9-121">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d0ba9-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d0ba9-122">Microsoft 365 的 PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="d0ba9-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="d0ba9-123">Skype for Business PowerShell cmdlet 参考</span><span class="sxs-lookup"><span data-stu-id="d0ba9-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

