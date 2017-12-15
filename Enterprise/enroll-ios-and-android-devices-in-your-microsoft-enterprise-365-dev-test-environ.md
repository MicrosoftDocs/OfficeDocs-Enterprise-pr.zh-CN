---
title: "IOS 和 Android 设备在 Microsoft 企业 365 开发/测试环境中注册"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "摘要： 使用此测试实验室指南注册 Microsoft 365 开发/测试环境中的设备，并对其进行远程管理。"
ms.openlocfilehash: 8ad22ed62d8e7cac8aca225af42e389dc05cb2b5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="6bd17-103">IOS 和 Android 设备在 Microsoft 企业 365 开发/测试环境中注册</span><span class="sxs-lookup"><span data-stu-id="6bd17-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="6bd17-104">**摘要：**此测试实验室指南用于注册 Microsoft 365 开发/测试环境中的设备并对其进行远程管理。</span><span class="sxs-lookup"><span data-stu-id="6bd17-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="6bd17-p101">Microsoft 企业移动套件 (EMS) 有助于使您的员工提高工作效率的同时保护您组织的数据使用他们最喜欢的应用程序和设备。有关详细信息，请参阅[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="6bd17-p102">如果需要在设计级别应用安全性，则必须将设备注册到 Microsoft Intune。设备注册不仅有助于管理企业所有的设备，还可以根据组织的法律政策管理个人 (BYOD) 和共享设备。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage corporate-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="6bd17-109">通过遵循本文中提供的说明进行操作，您可以注册和 Microsoft 365 开发/测试环境中测试 iOS 和 Android 设备的基本移动设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="6bd17-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="6bd17-110">阶段 1： 创建 Microsoft 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="6bd17-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="6bd17-111">按照[Microsoft 365 企业开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="6bd17-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a><span data-ttu-id="6bd17-112">第 2 阶段：自定义 Microsoft Intune 公司门户应用</span><span class="sxs-lookup"><span data-stu-id="6bd17-112">Phase 2: Customize the Microsoft Intune Company Portal app</span></span>

<span data-ttu-id="6bd17-113">使用以下步骤为虚构的公司自定义 Microsoft Intune 公司门户应用：</span><span class="sxs-lookup"><span data-stu-id="6bd17-113">Use these steps to customize the Microsoft Intune Company Portal app for your fictional company:</span></span>
  
1. <span data-ttu-id="6bd17-114">在新的选项卡上，打开 Microsoft Intune 管理控制台 ([https://manage.microsoft.com](https://manage.microsoft.com))。</span><span class="sxs-lookup"><span data-stu-id="6bd17-114">On a new tab, open the Microsoft Intune administration console ([https://manage.microsoft.com](https://manage.microsoft.com)).</span></span>
    
2. <span data-ttu-id="6bd17-115">请在导航窗格中单击**管理员**，然后单击**管理**窗格中的**移动设备管理**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-115">Click **Admin** in the navigation pane, and then click **Mobile Device Management** in the **Administration** pane.</span></span>
    
3. <span data-ttu-id="6bd17-p103">在**任务**列表中，选择**设置移动设备管理机构**。请确保它被设置为**Microsoft Intune**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p103">In the **Tasks** list, select **Set Mobile Device Management Authority**. Ensure that it is set to **Microsoft Intune**.</span></span>
    
4. <span data-ttu-id="6bd17-118">在**管理**窗格中，单击**公司入口**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-118">In the **Administration** pane, click **Company Portal**.</span></span>
    
5. <span data-ttu-id="6bd17-119">**公司门户**的窗格中，配置下列设置：</span><span class="sxs-lookup"><span data-stu-id="6bd17-119">In the **Company Portal** pane, configure the following settings:</span></span>
    
  - <span data-ttu-id="6bd17-120">公司名称：\<虚构的公司名 ></span><span class="sxs-lookup"><span data-stu-id="6bd17-120">Company name: \<your fictional company name></span></span>
    
  - <span data-ttu-id="6bd17-121">IT 部门联系人名称： **User5**</span><span class="sxs-lookup"><span data-stu-id="6bd17-121">IT department contact name: **User5**</span></span>
    
  - <span data-ttu-id="6bd17-122">IT 部门的电话号码： **555-1234**</span><span class="sxs-lookup"><span data-stu-id="6bd17-122">IT department phone number: **555-1234**</span></span>
    
  - <span data-ttu-id="6bd17-123">IT 部门的电子邮件地址： **User5 @**\<虚构的单位名称 > **。 onmicrosoft.com** （User5 帐户的电子邮件地址）</span><span class="sxs-lookup"><span data-stu-id="6bd17-123">IT department e-mail address: **User5@**\<fictional organization name> **.onmicrosoft.com** (the email address of the User5 account)</span></span>
    
6. <span data-ttu-id="6bd17-124">在**自定义**，选择**主题颜色**中的**绿色**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-124">In **Customization**, select **Green** in **Theme color**.</span></span>
    
7. <span data-ttu-id="6bd17-125">单击"保存"。</span><span class="sxs-lookup"><span data-stu-id="6bd17-125">Click **Save**.</span></span>
    
<span data-ttu-id="6bd17-126">接下来要安装 Microsoft Intune 公司门户应用并注册 iOS 或 Android 设备，然后测试 Microsoft Intune 管理控制台中的基本管理功能。</span><span class="sxs-lookup"><span data-stu-id="6bd17-126">Next, you will install the Microsoft Intune Company Portal app and enroll an iOS or Android device, and then test basic management functionality from the Microsoft Intune administration console.</span></span>
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a><span data-ttu-id="6bd17-127">第 3 阶段（仅适用于 iOS 设备）：注册并管理 iOS 设备</span><span class="sxs-lookup"><span data-stu-id="6bd17-127">Phase 3 (for iOS devices only): Enroll and manage an iOS device</span></span>

<span data-ttu-id="6bd17-128">若要注册 iOS 设备以通过 Intune 进行管理，需要具备以下条件：</span><span class="sxs-lookup"><span data-stu-id="6bd17-128">To enroll an iOS device for management by Intune, you will need the following:</span></span>
  
- <span data-ttu-id="6bd17-129">一台 iOS设备，例如 Apple iPad 或 iPhone。</span><span class="sxs-lookup"><span data-stu-id="6bd17-129">An iOS device such as an Apple iPad or iPhone.</span></span>
    
- <span data-ttu-id="6bd17-130">IOS 设备通行码的知识。</span><span class="sxs-lookup"><span data-stu-id="6bd17-130">Knowledge of the iOS device's passcode.</span></span>
    
- <span data-ttu-id="6bd17-p104">一个苹果 ID （帐户名和密码）。如果您没有一个，转到[苹果 ID 网站](https://appleid.apple.com/#!&amp;page=signin)，然后单击**创建您的苹果 ID**。创建苹果 ID 对应于您的 Office 365 订购的全局管理员帐户。在一个安全的位置中记录您的新的苹果 ID 帐户名和密码。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p104">An Apple ID (an account name and password). If you do not already have one, go to the [Apple ID website](https://appleid.apple.com/#!&amp;page=signin) and click **Create your Apple ID**. Create an Apple ID corresponding to the global administrator account of your Office 365 subscription. Record your new Apple ID account name and password in a secure location.</span></span>
    
<span data-ttu-id="6bd17-p105">Intune 管理 iOS 和 Mac 设备需具备 Apple 推送通知服务 (APNs) 证书。将该证书添加到 Intune 后，用户即可安装 Microsoft Intune 公司门户应用来注册自己的设备，管理员则可以设置对企业所有的 iOS 设备的管理。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p105">An Apple Push Notification service (APNs) certificate is required for Intune to manage iOS and Mac devices. Once the certificate is added to Intune, users can install the Microsoft Intune Company Portal app to enroll their devices or the administrator can set up corporate-owned iOS device management.</span></span>
  
<span data-ttu-id="6bd17-p106">需要一个证书签名请求文件来向 Apple 推送证书门户请求信任关系证书。获取证书签名请求文件：</span><span class="sxs-lookup"><span data-stu-id="6bd17-p106">You need a certificate signing request file to request a trust relationship certificate from the Apple Push Certificates Portal. To get a certificate signing request file:</span></span>
  
1. <span data-ttu-id="6bd17-139">在 Microsoft Intune 管理控制台中，请单击导航窗格中的**管理员**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-139">In the Microsoft Intune administration console, click **Admin** in the navigation pane.</span></span>
    
    <span data-ttu-id="6bd17-140">在**管理**窗格中，打开**移动设备管理 > iOS 和 Mac OS X**，然后单击**上载 APNs 证书****任务**中。</span><span class="sxs-lookup"><span data-stu-id="6bd17-140">In the **Administration** pane, open **Mobile Device Management > iOS and Mac OS X**, and then click **Upload an APNs Certificate** in **Tasks**.</span></span> 
    
2. <span data-ttu-id="6bd17-p107">在**上载 APNs 证书**窗格中，单击**下载 APNs 证书申请**。保存证书签名请求 (.csr) 文件本地名称**开发测试**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p107">In the **Upload an APNs Certificate** pane, click **Download the APNs certificate request**. Save the certificate signing request (.csr) file locally with the name **dev-test**.</span></span>
    
<span data-ttu-id="6bd17-143">获取 Apple 推送通知服务证书：</span><span class="sxs-lookup"><span data-stu-id="6bd17-143">To get an Apple Push Notification service certificate:</span></span>
  
1. <span data-ttu-id="6bd17-144">打开一个新标签，转到了[苹果将推证书门户](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)，登录您的苹果 id。</span><span class="sxs-lookup"><span data-stu-id="6bd17-144">Open a new tab, go to the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2), and sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="6bd17-145">在**开始**页中，单击**证书**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-145">On the **Get Started** page, click **Create a Certificate**.</span></span>
    
3. <span data-ttu-id="6bd17-146">在**使用条款的**页上，选择**我已阅读并同意这些条款和条件**，然后单击**接受**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-146">On the **Terms of Use** page, select **I have read and agree to these terms and conditions**, and then click **Accept**.</span></span>
    
4. <span data-ttu-id="6bd17-p108">**创建一个新的推证书**页上单击**浏览**并选择保存在上一过程中，**开发 test.csr**文件，然后单击**上载**。当系统提示您打开一个 json 文件，则将其保存到同一开发 test.csr 文件所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p108">On the **Create a New Push Certificate** page, click **Browse** and select the **dev-test.csr** file saved in the previous procedure, and then click **Upload**. When prompted to open a json file, save it to the same folder where the dev-test.csr file is stored.</span></span>
    
5. <span data-ttu-id="6bd17-149">打开[苹果将推证书门户网站](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)在不同的选项卡上，对于**第三方服务器的证书**，单击**下载**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-149">Open the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in a different tab and for **Certificates for Third-Party Servers**, click **Download**.</span></span>
    
6. <span data-ttu-id="6bd17-p109">当系统提示您打开.pem 文件，保存与开发 test.csr 文件的存储位置的相同文件夹名称**开发 test.pem** 。这是 APNs 证书。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p109">When prompted to open a .pem file, save it with the name **dev-test.pem** to the same folder where the dev-test.csr file is stored. This is your APNs certificate.</span></span>
    
<span data-ttu-id="6bd17-152">将 APNs 证书上载到 Intune：</span><span class="sxs-lookup"><span data-stu-id="6bd17-152">To upload the APNs certificate into Intune:</span></span>
  
1. <span data-ttu-id="6bd17-153">在 Microsoft Intune 管理控制台选项卡，在**传 APNs 证书**页上单击**上载 APNs 证书**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-153">On the Microsoft Intune administration console tab, on the **Upload an APNs Certificate** page, click **Upload the APNs certificate**.</span></span>
    
2. <span data-ttu-id="6bd17-154">单击**浏览**，然后指定**开发 test.pem**文件。</span><span class="sxs-lookup"><span data-stu-id="6bd17-154">Click **Browse** and specify the **dev-test.pem** file.</span></span>
    
3. <span data-ttu-id="6bd17-p110">单击**打开**，键入您的苹果 ID 帐户名，然后单击**上载**。**IOS 和 MaxOS X 移动设备管理组件安装程序**页上，您应该看到**准备注册**消息。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p110">Click **Open**, type your Apple ID account name, and then click **Upload**. You should see a **Ready for enrollment** message on the **iOS and MaxOS X Mobile Device Management Setup** page.</span></span>
    
<span data-ttu-id="6bd17-157">安装 APNs 证书后，Intune 现在则可以通过向已注册的移动设备推送政策来注册和管理 iOS 设备。</span><span class="sxs-lookup"><span data-stu-id="6bd17-157">With the APNs certificate installed, Intune can now enroll and manage iOS devices by pushing policy to enrolled mobile devices.</span></span>
  
<span data-ttu-id="6bd17-158">下载 Microsoft Intune 公司门户应用并注册 iOS 设备：</span><span class="sxs-lookup"><span data-stu-id="6bd17-158">To download the Microsoft Intune Company portal app and enroll the iOS device:</span></span>
  
1. <span data-ttu-id="6bd17-159">在 iOS 设备中使用 Apple ID 登录。</span><span class="sxs-lookup"><span data-stu-id="6bd17-159">From your iOS device, sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="6bd17-160">打开**苹果商店**应用程序。</span><span class="sxs-lookup"><span data-stu-id="6bd17-160">Open the **Apple Store** app.</span></span>
    
3. <span data-ttu-id="6bd17-161">在搜索框中键入**intune**并点击**Microsoft Intune 公司门户网站**，**获取**，然后再**安装**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-161">Type **intune** in the search box and tap **Microsoft Intune Company Portal**, then **Get**, and then **Install**.</span></span>
    
4. <span data-ttu-id="6bd17-162">安装后，点击**打开**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-162">After it installs, tap **Open**.</span></span>
    
5. <span data-ttu-id="6bd17-163">在**Intune 公司门户**屏幕上，使用您 Office 365 的全局管理员帐户进行登录。</span><span class="sxs-lookup"><span data-stu-id="6bd17-163">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
6. <span data-ttu-id="6bd17-164">在**公司访问安装程序**屏幕上，点击**开始**，然后点击**继续**两次。</span><span class="sxs-lookup"><span data-stu-id="6bd17-164">On the **Company Access Setup** screen, tap **Begin**, and then tap **Continue** twice.</span></span>
    
7. <span data-ttu-id="6bd17-165">在**下来？**屏幕上，点击**注册**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-165">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
8. <span data-ttu-id="6bd17-166">在**激活设备管理员？**屏幕上，点击**激活**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-166">On the **Activate device administrator?** screen, tap **Activate**.</span></span>
    
9. <span data-ttu-id="6bd17-167">在**管理配置文件**屏幕中，单击**安装**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-167">On the **Management Profile** screen, tap **Install**.</span></span>
    
10. <span data-ttu-id="6bd17-168">在**输入密码**，键入 iOS 设备通行码。</span><span class="sxs-lookup"><span data-stu-id="6bd17-168">In **Enter Passcode**, type your iOS device passcode.</span></span>
    
11. <span data-ttu-id="6bd17-169">在**种下一**屏幕上，点击**注册**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-169">On the **What comes next** screen, tap **Enroll**.</span></span>
    
12. <span data-ttu-id="6bd17-170">在**安装配置文件**，点击**安装**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-170">In **Install Profile**, tap **Install**.</span></span>
    
13. <span data-ttu-id="6bd17-171">在**警告**页面中，点击**安装**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-171">On the **Warning** page, tap **Install**.</span></span>
    
14. <span data-ttu-id="6bd17-172">在**远程管理**，点击**信任**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-172">In **Remote Management**, tap **Trust**.</span></span>
    
15. <span data-ttu-id="6bd17-173">点击**完成**以完成注册过程。</span><span class="sxs-lookup"><span data-stu-id="6bd17-173">Tap **Done** to complete the enrollment process.</span></span>
    
16. <span data-ttu-id="6bd17-174">当系统提示**打开此页面在"复合门户"？**，点击**打开**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-174">When prompted to **Open this page in "Comp Portal"?**, tap **Open**.</span></span>
    
17. <span data-ttu-id="6bd17-175">在**公司访问安装程序**屏幕上，点击**开始**，，然后点击**完成**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-175">On the **Company Access Setup** screen, tap **Begin**, and then tap **Done**.</span></span>
    
18. <span data-ttu-id="6bd17-176">会在 Microsoft Intune 公司门户应用的主屏幕中看到以下内容：</span><span class="sxs-lookup"><span data-stu-id="6bd17-176">On the main screen of the Microsoft Intune Company Portal app, you should see:</span></span>
    
  - <span data-ttu-id="6bd17-177">绿色的横幅。</span><span class="sxs-lookup"><span data-stu-id="6bd17-177">A green banner.</span></span>
    
  - <span data-ttu-id="6bd17-178">虚构的公司名称位于左上方。</span><span class="sxs-lookup"><span data-stu-id="6bd17-178">Your fictional company name in the upper left.</span></span>
    
  - <span data-ttu-id="6bd17-179">**我的设备**中列出您 iOS 设备名称。</span><span class="sxs-lookup"><span data-stu-id="6bd17-179">Your iOS device name listed in **My Devices**.</span></span>
    
  - <span data-ttu-id="6bd17-180">在**帮助台**部分， **User5**与**555-1234年**和按钮**通过电子邮件的联系人**的电话号码的**联系人姓名**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-180">In the **Helpdesk** section, the **Contact Name** of **User5** with the phone number of **555-1234** and a **Contact by email** button.</span></span>
    
<span data-ttu-id="6bd17-p111">Microsoft Intune 提供远程锁定和密码重置两种功能。如果有人丢失了自己的设备，则可以远程锁定设备。如果有人忘记了自己的密码，则可以远程删除密码。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p111">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="6bd17-184">远程锁定 iOS 设备：</span><span class="sxs-lookup"><span data-stu-id="6bd17-184">To lock an iOS device remotely:</span></span>
  
1. <span data-ttu-id="6bd17-185">您管理的计算机，Microsoft Intune 管理控制台选项卡上的浏览器中，从左侧导航区域中单击**组**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-185">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="6bd17-186">在**组**窗格中，打开**所有设备 > 所有移动设备 > 所有直接受控设备**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-186">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="6bd17-187">在**所有直接受控设备**窗格中，单击**设备**选项卡。</span><span class="sxs-lookup"><span data-stu-id="6bd17-187">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="6bd17-188">在设备列表中，单击自己的 iOS 设备。 </span><span class="sxs-lookup"><span data-stu-id="6bd17-188">In the devices list, click your iOS device.</span></span> 
    
5. <span data-ttu-id="6bd17-189">在自己的 iOS 设备中，请确保其位于主屏幕上。 </span><span class="sxs-lookup"><span data-stu-id="6bd17-189">From your iOS device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="6bd17-p112">从管理计算机，在任务栏上，单击**远程任务 > 远程锁定**。切换锁定屏幕为 iOS 设备进行观察。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p112">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="6bd17-192">删除密码：</span><span class="sxs-lookup"><span data-stu-id="6bd17-192">To remove the passcode:</span></span>
  
1. <span data-ttu-id="6bd17-193">从您的管理计算机的**所有直接受控设备**窗格中，单击**设备**选项卡。</span><span class="sxs-lookup"><span data-stu-id="6bd17-193">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="6bd17-p113">在列表中，单击您的 iOS 设备。在任务栏上，单击**远程任务 > 密码重置**。等待一分钟。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p113">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="6bd17-p114">从 iOS 设备，解除其锁定，请注意是不能再通行码。若要更改密码后，进入**设置**，然后再**通行码**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p114">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a><span data-ttu-id="6bd17-199">第 3 阶段（仅适用于 Android 设备）：注册并管理 Android 设备</span><span class="sxs-lookup"><span data-stu-id="6bd17-199">Phase 3 (for Android devices only): Enroll and manage an Android device</span></span>

<span data-ttu-id="6bd17-200">若要注册 Android 设备以通过 Intune 进行管理，需要具备以下条件：</span><span class="sxs-lookup"><span data-stu-id="6bd17-200">You will need the following to enroll an Android device for management by Intune:</span></span>
  
- <span data-ttu-id="6bd17-201">一台 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="6bd17-201">An Android device.</span></span>
    
- <span data-ttu-id="6bd17-202">设备通行码的知识。</span><span class="sxs-lookup"><span data-stu-id="6bd17-202">Knowledge of the device's passcode.</span></span>
    
<span data-ttu-id="6bd17-203">下载 Intune 公司门户应用并注册 Android 设备：</span><span class="sxs-lookup"><span data-stu-id="6bd17-203">To download the Intune Company portal app and enroll the Android device:</span></span>
  
1. <span data-ttu-id="6bd17-204">从 Android 设备，转到**Google 播放存储**，然后点击**开始**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-204">From your Android device, go to the **Google Play Store**, and then tap **Get Started**.</span></span>
    
2. <span data-ttu-id="6bd17-205">在搜索框中，键入**intune** ，然后点击**intune 公司门户网站**在搜索结果中。</span><span class="sxs-lookup"><span data-stu-id="6bd17-205">Type **intune** in the search box, and then tap **intune company portal** in the search results.</span></span>
    
3. <span data-ttu-id="6bd17-206">点击**Intune 公司门户**项目中，然后点击**安装**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-206">Tap the **Intune Company Portal** item, and then tap **Install**.</span></span>
    
4. <span data-ttu-id="6bd17-207">在**完整的帐户安装程序**屏幕上，点击**继续**，然后选择**跳过**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-207">On the **For Complete account setup** screen, tap **Continue**, and then **Skip**.</span></span>
    
5. <span data-ttu-id="6bd17-p115">在**Intune 公司门户网站**，点击**接受**。应用程序安装。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p115">In **Intune Company Portal**, tap **Accept**. The app installs.</span></span>
    
6. <span data-ttu-id="6bd17-210">点击**打开**，然后点击**登录**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-210">Tap **Open**, and then tap **Sign in**.</span></span>
    
7. <span data-ttu-id="6bd17-211">在**Intune 公司门户**屏幕上，使用您 Office 365 的全局管理员帐户进行登录。</span><span class="sxs-lookup"><span data-stu-id="6bd17-211">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="6bd17-212">在**公司访问安装程序**屏幕上，点击**开始**，然后**继续**两次。</span><span class="sxs-lookup"><span data-stu-id="6bd17-212">On the **Company Access Setup** screen, tap **Begin**, and then **Continue** twice.</span></span>
    
9. <span data-ttu-id="6bd17-213">在**下来？**屏幕上，点击**注册**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-213">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
10. <span data-ttu-id="6bd17-214">在**激活设备管理员？**屏幕上，点击**激活。**</span><span class="sxs-lookup"><span data-stu-id="6bd17-214">On the **Activate device administrator?** screen, tap **Activate.**</span></span>
    
11. <span data-ttu-id="6bd17-p116">在**隐私策略**屏幕中，选择**我确认**，然后点击**确认**。等待完成注册过程。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p116">On the **Privacy Policy** screen, select **I acknowledge** and then tap **Confirm**. Wait for the enrollment process to complete.</span></span>
    
12. <span data-ttu-id="6bd17-217">在**公司访问安装程序**屏幕上，点击**继续**，，然后点击**完成**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-217">In the **Company Access Setup** screen, tap **Continue**, and then tap **Done**.</span></span>
    
13. <span data-ttu-id="6bd17-218">在 Microsoft Intune 公司门户应用的主屏幕上，应该可以看到一个绿色的横幅和位于左上方的虚构的公司名称。</span><span class="sxs-lookup"><span data-stu-id="6bd17-218">On the main screen of the Microsoft Intune Company Portal app, you should see a green banner and your fictional company name in the upper left.</span></span>
    
14. <span data-ttu-id="6bd17-p117">请点击**我的设备**。您应该看到 Android 设备名称列表中。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p117">Tap **My devices**. You should see your Android device name in the list.</span></span>
    
15. <span data-ttu-id="6bd17-p118">请点击**请联系 IT 部门**。您应该看到的电话号码是**555-1234年**，**联系通过电子邮件**的按钮，和它联系的**User5**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p118">Tap **Contact IT**. You should see the phone number of **555-1234**, a **Contact by email** button, and the IT contact of **User5**.</span></span>
    
<span data-ttu-id="6bd17-p119">Microsoft Intune 提供远程锁定和密码重置两种功能。如果有人丢失了自己的设备，则可以远程锁定设备。如果有人忘记了自己的密码，则可以远程重置密码。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p119">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset the passcode remotely.</span></span>
  
<span data-ttu-id="6bd17-226">远程锁定 Android 设备：</span><span class="sxs-lookup"><span data-stu-id="6bd17-226">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="6bd17-227">您管理的计算机，Microsoft Intune 管理控制台选项卡上的浏览器中，从左侧导航区域中单击**组**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-227">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="6bd17-228">在**组**窗格中，打开**所有设备 > 所有移动设备 > 所有直接受控设备**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-228">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="6bd17-229">在**所有直接受控设备**窗格中，单击**设备**选项卡。</span><span class="sxs-lookup"><span data-stu-id="6bd17-229">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="6bd17-230">在设备列表中，单击自己的 Android 设备。 </span><span class="sxs-lookup"><span data-stu-id="6bd17-230">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="6bd17-231">在自己的 Android 设备中，请确保其位于主屏幕上。 </span><span class="sxs-lookup"><span data-stu-id="6bd17-231">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="6bd17-p120">从管理计算机，在任务栏上，单击**远程任务 > 远程锁定**。出现提示时，请单击**是**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p120">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="6bd17-234">Android 设备切换到锁定屏幕时观察其变化。</span><span class="sxs-lookup"><span data-stu-id="6bd17-234">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="6bd17-235">当您重置密码的 Android 设备时，Intune 管理门户生成并配置一个强密码。</span><span class="sxs-lookup"><span data-stu-id="6bd17-235">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="6bd17-236">远程重置密码：</span><span class="sxs-lookup"><span data-stu-id="6bd17-236">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="6bd17-237">从您的管理计算机，Microsoft Intune 管理控制台选项卡上的浏览器中，在**所有直接受控设备**窗格中，单击您的 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="6bd17-237">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="6bd17-238">在任务栏上，单击**远程任务 > 密码重置**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-238">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="6bd17-p121">在**远程任务： 密码重置**提示下，单击**是**。等待一分钟。</span><span class="sxs-lookup"><span data-stu-id="6bd17-p121">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="6bd17-241">在**所有直接受控设备**窗格中，单击**查看属性**。</span><span class="sxs-lookup"><span data-stu-id="6bd17-241">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="6bd17-242">在**密码重置**，记下新的密码。</span><span class="sxs-lookup"><span data-stu-id="6bd17-242">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="6bd17-243">在自己的 Android 设备的锁屏中输入新密码。 </span><span class="sxs-lookup"><span data-stu-id="6bd17-243">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="6bd17-244">若要更改密码后，进入**设置**、 点击**设备**，点击**锁定屏幕**、 密码中输入新的密码，点击**屏幕锁**，并选择。</span><span class="sxs-lookup"><span data-stu-id="6bd17-244">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    
> [!TIP]
> <span data-ttu-id="6bd17-245">单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的项目的所有。</span><span class="sxs-lookup"><span data-stu-id="6bd17-245">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6bd17-246">See Also</span><span class="sxs-lookup"><span data-stu-id="6bd17-246">See Also</span></span>

[<span data-ttu-id="6bd17-247">Microsoft 365 企业开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="6bd17-247">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="6bd17-248">您的 Microsoft 365 企业开发/测试环境的 MAM 策略</span><span class="sxs-lookup"><span data-stu-id="6bd17-248">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="6bd17-249">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="6bd17-249">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="6bd17-250">企业移动 + 安全 (EMS)</span><span class="sxs-lookup"><span data-stu-id="6bd17-250">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


