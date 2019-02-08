---
title: Office 365 开发/测试环境的多重身份验证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 摘要：使用发送到 Office 365 开发/测试环境中的智能手机的短信来配置多重身份验证。
ms.openlocfilehash: 6e2aefa9309e7e268c937055f7fe59600f8c87da
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897445"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="5e025-103">Office 365 开发/测试环境的多重身份验证</span><span class="sxs-lookup"><span data-stu-id="5e025-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="5e025-104">**摘要：** 使用发送到 Office 365 开发/测试环境中的智能手机的短信来配置多重身份验证。</span><span class="sxs-lookup"><span data-stu-id="5e025-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="5e025-p101">登录到 Office 365 订阅的安全性的其他级别，您可以让 Azure 多因素身份验证，这要求远不止用户名和密码进行身份验证帐户。使用 Office 365 的多因素身份验证，用户所需确认电话呼叫，键入验证代码发送文本消息，或在其智能手机上正确输入自己的密码之后指定应用程序密码。在此第二个身份验证因素已得到满足之后，才可以登录状态。</span><span class="sxs-lookup"><span data-stu-id="5e025-p101">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to authenticate an account. With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords. They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="5e025-108">本文介绍如何为特定 Office 365 帐户启用和测试基于短信的身份验证。</span><span class="sxs-lookup"><span data-stu-id="5e025-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="5e025-109">在开发/测试环境中，设置 Office 365 多重身份验证包含两个阶段：</span><span class="sxs-lookup"><span data-stu-id="5e025-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="5e025-110">创建 Office 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="5e025-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="5e025-111">为 User 2 帐户启用并测试多重身份验证。</span><span class="sxs-lookup"><span data-stu-id="5e025-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="5e025-112">单击[此处](http://aka.ms/catlgstack)可以在 One Microsoft 云测试实验室指南堆栈图中直观转到相应的任何文章。</span><span class="sxs-lookup"><span data-stu-id="5e025-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="5e025-113">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="5e025-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="5e025-114">如果您只想要测试的最低硬件要求与轻型方式中的多因素身份验证，请在阶段 2 和 3 的[Office 365 开发/测试环境](office-365-dev-test-environment.md)中按照说明。</span><span class="sxs-lookup"><span data-stu-id="5e025-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="5e025-115">如果您想要测试模拟企业中的多因素身份验证，请按照[目录同步的 Office 365 开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="5e025-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="5e025-p102">测试多重身份验证不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server AD 林的目录同步。它在此处作为一个选项提供，以便你可以测试多重身份验证，并在代表典型组织的环境中对其进行试验。</span><span class="sxs-lookup"><span data-stu-id="5e025-p102">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="5e025-118">阶段 2：启用和测试 User 2 帐户的多重身份验证</span><span class="sxs-lookup"><span data-stu-id="5e025-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="5e025-119">通过以下步骤为 User 2 帐户启用多重身份验证：</span><span class="sxs-lookup"><span data-stu-id="5e025-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="5e025-120">打开一个单独的浏览器实例，请转到 Office 365 门户 ([https://portal.office.com](https://portal.office.com))，然后向 Office 365 试用版订阅与全局管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="5e025-120">Open a separate instance of your browser, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="5e025-121">在主门户页上，单击“管理员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5e025-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="5e025-122">在左侧导航栏中，依次单击“用户”和“活动用户”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5e025-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="5e025-123">在活动用户窗格中，单击**更多 > 安装 Azure 多因素身份验证**。</span><span class="sxs-lookup"><span data-stu-id="5e025-123">In the Active users pane, click **More > Setup Azure multi-factor auth**.</span></span>
    
5. <span data-ttu-id="5e025-124">在列表中，选择的**用户 2**帐户。</span><span class="sxs-lookup"><span data-stu-id="5e025-124">In the list, select the **User 2** account.</span></span>
    
6. <span data-ttu-id="5e025-125">在**用户 2**部分中，单击**快速步骤**下的**启用**。</span><span class="sxs-lookup"><span data-stu-id="5e025-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="5e025-126">在**有关启用多重身份验证**对话框中，单击**启用多重身份验证**。</span><span class="sxs-lookup"><span data-stu-id="5e025-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="5e025-127">在**更新成功**对话框中，单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="5e025-127">In the **Update successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="5e025-128">在**Microsoft Office Home**选项卡上，单击右上方中的用户帐户图标，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="5e025-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="5e025-129">关闭浏览器实例。</span><span class="sxs-lookup"><span data-stu-id="5e025-129">Close your browser instance.</span></span>
    
<span data-ttu-id="5e025-130">完成 User 2 帐户的配置，通过以下步骤，使用短信对其进行验证和测试：</span><span class="sxs-lookup"><span data-stu-id="5e025-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="5e025-131">打开浏览器的新实例。</span><span class="sxs-lookup"><span data-stu-id="5e025-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="5e025-132">转到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 和使用用户 2 帐户的登录 (user2 @\<组织 name>.onmicrosoft.com) 和密码。</span><span class="sxs-lookup"><span data-stu-id="5e025-132">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="5e025-p103">在登录后被提示设置的其他安全验证的帐户。单击**立即设置**。</span><span class="sxs-lookup"><span data-stu-id="5e025-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="5e025-135">在**其他安全验证**页上：</span><span class="sxs-lookup"><span data-stu-id="5e025-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="5e025-136">选择你所在的国家或地区。</span><span class="sxs-lookup"><span data-stu-id="5e025-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="5e025-137">键入接收短信的智能手机的电话号码。</span><span class="sxs-lookup"><span data-stu-id="5e025-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="5e025-138">在**方法**中，单击**给我发送的短信代码**。</span><span class="sxs-lookup"><span data-stu-id="5e025-138">in **Method**, click **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="5e025-139">单击"下一步"。</span><span class="sxs-lookup"><span data-stu-id="5e025-139">Click **Next**.</span></span>
    
6. <span data-ttu-id="5e025-140">输入介于智能手机上收到的文本消息验证代码，然后单击**验证**。</span><span class="sxs-lookup"><span data-stu-id="5e025-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="5e025-141">在**步骤 3： 保留现有的应用程序**页上，在安全的位置，记录用户 2 帐户的显示应用程序密码，然后单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="5e025-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="5e025-p104">如果这是首次您使用登录用户 2 帐户后，在系统提示您要更改的密码。两次，键入原始密码和新密码，然后单击**更新密码和登录**。记录在安全位置的新密码。</span><span class="sxs-lookup"><span data-stu-id="5e025-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="5e025-145">您应在浏览器的**Microsoft Office Home**选项卡上看到用户 2 的 Office 365 门户。</span><span class="sxs-lookup"><span data-stu-id="5e025-145">You should see the Office 365 portal for User 2 on the **Microsoft Office Home** tab of your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="5e025-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e025-146">See Also</span></span>

[<span data-ttu-id="5e025-147">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="5e025-147">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="5e025-148">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="5e025-148">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="5e025-149">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="5e025-149">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="5e025-150">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="5e025-150">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="5e025-151">Office 365 部署的多重身份验证计划</span><span class="sxs-lookup"><span data-stu-id="5e025-151">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

