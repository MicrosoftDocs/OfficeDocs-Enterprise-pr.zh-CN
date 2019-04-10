---
title: Office 365 开发/测试环境的多重身份验证
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
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
ms.openlocfilehash: 091b82132b407cfd25b18c3ba8e424e29df58910
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741218"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="636f4-103">Office 365 开发/测试环境的多重身份验证</span><span class="sxs-lookup"><span data-stu-id="636f4-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="636f4-104">**摘要：** 使用发送到 Office 365 开发/测试环境中的智能手机的短信来配置多重身份验证。</span><span class="sxs-lookup"><span data-stu-id="636f4-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="636f4-105">有关登录到 Office 365 订阅的其他安全级别, 可以启用 Azure 多重身份验证, 这需要使用用户名和密码才能对帐户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="636f4-105">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to authenticate an account.</span></span> <span data-ttu-id="636f4-106">使用适用于 Office 365 的多重身份验证时，用户需要在正确输入密码后确认智能手机上的电话呼叫、键入通过短信发送的验证码或指定应用密码。</span><span class="sxs-lookup"><span data-stu-id="636f4-106">With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords.</span></span> <span data-ttu-id="636f4-107">仅在满足第二个身份验证因素时才能登录。</span><span class="sxs-lookup"><span data-stu-id="636f4-107">They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="636f4-108">本文介绍如何为特定 Office 365 帐户启用和测试基于短信的身份验证。</span><span class="sxs-lookup"><span data-stu-id="636f4-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="636f4-109">在开发/测试环境中，设置 Office 365 多重身份验证包含两个阶段：</span><span class="sxs-lookup"><span data-stu-id="636f4-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="636f4-110">创建 Office 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="636f4-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="636f4-111">为 User 2 帐户启用并测试多重身份验证。</span><span class="sxs-lookup"><span data-stu-id="636f4-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="636f4-112">单击[此处](http://aka.ms/catlgstack)可查看 Office 365 测试实验室指南堆栈中所有文章的直观映射。</span><span class="sxs-lookup"><span data-stu-id="636f4-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="636f4-113">第 1 阶段：构建轻型或模拟的企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="636f4-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="636f4-114">如果只想使用最低要求以轻型方式测试多重身份验证, 请按照[Office 365 开发/测试环境](office-365-dev-test-environment.md)的第2阶段和第3阶段中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="636f4-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="636f4-115">如果要在模拟的企业中测试多重身份验证, 请按照[DirSync for Office 365 开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="636f4-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="636f4-116">测试多重身份验证不需要模拟企业开发/测试环境, 其中包括连接到 Internet 的模拟 intranet 和 Active directory 域服务 (AD DS) 林的目录同步。</span><span class="sxs-lookup"><span data-stu-id="636f4-116">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="636f4-117">它在此处作为一个选项提供，以便你可以测试多重身份验证，并在代表典型组织的环境中对其进行试验。</span><span class="sxs-lookup"><span data-stu-id="636f4-117">It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="636f4-118">阶段 2：启用和测试 User 2 帐户的多重身份验证</span><span class="sxs-lookup"><span data-stu-id="636f4-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="636f4-119">通过以下步骤为 User 2 帐户启用多重身份验证：</span><span class="sxs-lookup"><span data-stu-id="636f4-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="636f4-120">打开浏览器的单独实例, 转到 office 365 门户 ([https://www.office.com](https://www.office.com)), 然后使用全局管理员帐户登录到 office 365 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="636f4-120">Open a separate instance of your browser, go to the Office 365 portal ([https://www.office.com](https://www.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="636f4-121">在主门户页上，单击“管理员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="636f4-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="636f4-122">在左侧导航栏中，单击“用户”>“活动用户”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="636f4-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="636f4-123">在 "活动用户" 窗格中, 单击 "**更多 > 多重身份验证设置**"。</span><span class="sxs-lookup"><span data-stu-id="636f4-123">In the Active users pane, click **More > Multi-factor authentication setup**.</span></span>
    
5. <span data-ttu-id="636f4-124">在列表中, 选择 "**用户 2** " 帐户。</span><span class="sxs-lookup"><span data-stu-id="636f4-124">In the list, select the **User 2** account.</span></span>
    
6. <span data-ttu-id="636f4-125">在“User 2”\*\*\*\* 部分的“快速步骤”\*\*\*\* 下，单击“启用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="636f4-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="636f4-126">在“关于启用多重身份验证”\*\*\*\* 对话框中，单击“启用多重身份验证”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="636f4-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="636f4-127">在 "**更新成功**" 对话框中, 单击 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="636f4-127">In the **Updates successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="636f4-128">在“Microsoft Office 主页”\*\*\*\* 选项卡上，单击右上方的用户帐户图标，然后单击“注销”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="636f4-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="636f4-129">关闭浏览器实例。</span><span class="sxs-lookup"><span data-stu-id="636f4-129">Close your browser instance.</span></span>
    
<span data-ttu-id="636f4-130">完成 User 2 帐户的配置，通过以下步骤，使用短信对其进行验证和测试：</span><span class="sxs-lookup"><span data-stu-id="636f4-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="636f4-131">打开浏览器的新实例。</span><span class="sxs-lookup"><span data-stu-id="636f4-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="636f4-132">转到 Office 365 门户 ([https://www.office.com](https://www.office.com)), 并使用 User 2 帐户 (用户2、\<组织 name>) 和密码登录。</span><span class="sxs-lookup"><span data-stu-id="636f4-132">Go to the Office 365 portal ([https://www.office.com](https://www.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="636f4-p103">登录后，系统将提示你设置帐户以进行其他安全验证。单击“立即设置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="636f4-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="636f4-135">在“其他安全性验证”\*\*\*\* 页上： </span><span class="sxs-lookup"><span data-stu-id="636f4-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="636f4-136">选择你所在的国家或地区。</span><span class="sxs-lookup"><span data-stu-id="636f4-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="636f4-137">键入接收短信的智能手机的电话号码。</span><span class="sxs-lookup"><span data-stu-id="636f4-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="636f4-138">在**方法**中, 单击 "**通过短信向我发送代码**"。</span><span class="sxs-lookup"><span data-stu-id="636f4-138">in **Method**, click **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="636f4-139">单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="636f4-139">Click **Next**.</span></span>
    
6. <span data-ttu-id="636f4-140">输入智能手机收到的短信中的验证码，然后单击“验证”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="636f4-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="636f4-141">在“第 3 步: 保留现有应用程序”\*\*\*\* 页上，将显示的 User 2 帐户的应用密码记录在安全位置，然后单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="636f4-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="636f4-p104">如果这是你第一次使用 User 2 帐户登录，那么系统将提示你更改密码。键入原始密码和新密码两次，然后单击“更新密码并登录”\*\*\*\*。将新密码记录在安全位置。</span><span class="sxs-lookup"><span data-stu-id="636f4-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="636f4-145">您应在浏览器的 " **Microsoft Office 主页**" 选项卡上看到 "用户 2" 的 Office 365 门户。</span><span class="sxs-lookup"><span data-stu-id="636f4-145">You should see the Office 365 portal for User 2 on the **Microsoft Office Home** tab of your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="636f4-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="636f4-146">See Also</span></span>

[<span data-ttu-id="636f4-147">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="636f4-147">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="636f4-148">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="636f4-148">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="636f4-149">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="636f4-149">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="636f4-150">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="636f4-150">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="636f4-151">Office 365 部署的多重身份验证计划</span><span class="sxs-lookup"><span data-stu-id="636f4-151">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

