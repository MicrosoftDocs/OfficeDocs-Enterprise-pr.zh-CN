---
title: 注册 iOS 和 Microsoft 企业 365 开发/测试环境中的 Android 设备
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 摘要： 使用此测试实验室指南注册 Microsoft 365 开发/测试环境中的设备和远程管理它们。
ms.openlocfilehash: b5ceecd74ac010d787bc580054d5dd43db952fef
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="63c72-103">注册 iOS 和 Microsoft 企业 365 开发/测试环境中的 Android 设备</span><span class="sxs-lookup"><span data-stu-id="63c72-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="63c72-104">**摘要：** 使用此测试实验室指南注册 Microsoft 365 开发/测试环境中的设备和远程管理它们。</span><span class="sxs-lookup"><span data-stu-id="63c72-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="63c72-p101">Microsoft 企业移动套件 (EMS) 可帮助保持员工提高生产效率的同时保护组织的数据使用他们喜欢的应用程序和设备。有关详细信息，请参阅[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。</span><span class="sxs-lookup"><span data-stu-id="63c72-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="63c72-p102">如果您需要将应用设备级别的安全性，您必须注册到 Microsoft Intune 设备。设备注册不仅可帮助您管理组织负责设备，但还个人 (BYOD) 和共享的设备，具体取决于组织的法律策略。</span><span class="sxs-lookup"><span data-stu-id="63c72-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="63c72-109">按照本文中提供的说明进行操作，您将能够注册和 Microsoft 365 开发/测试环境中测试用于 iOS 和 Android 设备的基本的移动设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="63c72-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="63c72-110">阶段 1： 创建 Microsoft 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="63c72-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="63c72-111">按照[Microsoft 365 企业版开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="63c72-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="63c72-112">阶段 2： 注册您的 iOS 和 Android 设备</span><span class="sxs-lookup"><span data-stu-id="63c72-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="63c72-113">首先，使用中的说明[安装和登录到的公司门户应用程序](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios)开发/测试租户自定义 Microsoft Intune 的公司门户应用程序。</span><span class="sxs-lookup"><span data-stu-id="63c72-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your dev/test tenant.</span></span>

<span data-ttu-id="63c72-114">注册 iOS 设备，接下来，使用[设置访问公司资源](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)中的说明。</span><span class="sxs-lookup"><span data-stu-id="63c72-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="63c72-115">注册 Android 设备，接下来，使用[注册中 Intune Android 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)中的说明。</span><span class="sxs-lookup"><span data-stu-id="63c72-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="63c72-116">第 2 阶段： 远程管理您的 iOS 和 Android 设备</span><span class="sxs-lookup"><span data-stu-id="63c72-116">Phase 2: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="63c72-p103">Microsoft Intune 提供远程锁定和密码重置两种功能。如果有人丢失了自己的设备，则可以远程锁定设备。如果有人忘记了自己的密码，则可以远程删除密码。</span><span class="sxs-lookup"><span data-stu-id="63c72-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="63c72-120">远程锁定 iOS 设备：</span><span class="sxs-lookup"><span data-stu-id="63c72-120">To lock an iOS device remotely:</span></span>
  
1.  <span data-ttu-id="63c72-121">打开新选项卡并转到http://manage.microsoft.com（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="63c72-121">Open a new tab and go to http://manage.microsoft.com (if needed).</span></span> 

2.  <span data-ttu-id="63c72-122">从浏览器的 Microsoft Intune 管理控制台中，单击左侧导航窗格中的**组**。</span><span class="sxs-lookup"><span data-stu-id="63c72-122">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>

3. <span data-ttu-id="63c72-123">在**组**窗格中，打开**所有设备 > 所有的移动设备 > 所有直接管理设备**。</span><span class="sxs-lookup"><span data-stu-id="63c72-123">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
4. <span data-ttu-id="63c72-124">在**所有直接管理设备**窗格中，单击**设备**选项卡。</span><span class="sxs-lookup"><span data-stu-id="63c72-124">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
5. <span data-ttu-id="63c72-125">在设备列表中，单击自己的 iOS 设备。 </span><span class="sxs-lookup"><span data-stu-id="63c72-125">In the devices list, click your iOS device.</span></span> 
    
6. <span data-ttu-id="63c72-126">在自己的 iOS 设备中，请确保其位于主屏幕上。 </span><span class="sxs-lookup"><span data-stu-id="63c72-126">From your iOS device, make sure it is at the main screen.</span></span> 
    
7. <span data-ttu-id="63c72-p104">从管理计算机，在任务栏上，单击**远程任务 > 远程锁定**。它将切换到锁定屏幕上看 iOS 设备。</span><span class="sxs-lookup"><span data-stu-id="63c72-p104">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="63c72-129">删除密码：</span><span class="sxs-lookup"><span data-stu-id="63c72-129">To remove the passcode:</span></span>
  
1. <span data-ttu-id="63c72-130">从管理计算机，在**所有直接管理设备**窗格中，单击**设备**选项卡。</span><span class="sxs-lookup"><span data-stu-id="63c72-130">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="63c72-p105">在列表中，单击 iOS 设备。在任务栏上，单击**远程任务 > 密码重置**。等待一分钟。</span><span class="sxs-lookup"><span data-stu-id="63c72-p105">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="63c72-p106">从 iOS 设备，解除锁定，请注意，有不再密码。若要更改密码后，转到**设置**，然后**密码**。</span><span class="sxs-lookup"><span data-stu-id="63c72-p106">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
<span data-ttu-id="63c72-136">远程锁定 Android 设备：</span><span class="sxs-lookup"><span data-stu-id="63c72-136">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="63c72-137">从浏览器的 Microsoft Intune 管理控制台中，单击左侧导航窗格中的**组**。</span><span class="sxs-lookup"><span data-stu-id="63c72-137">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="63c72-138">在**组**窗格中，打开**所有设备 > 所有的移动设备 > 所有直接管理设备**。</span><span class="sxs-lookup"><span data-stu-id="63c72-138">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="63c72-139">在**所有直接管理设备**窗格中，单击**设备**选项卡。</span><span class="sxs-lookup"><span data-stu-id="63c72-139">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="63c72-140">在设备列表中，单击自己的 Android 设备。 </span><span class="sxs-lookup"><span data-stu-id="63c72-140">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="63c72-141">在自己的 Android 设备中，请确保其位于主屏幕上。 </span><span class="sxs-lookup"><span data-stu-id="63c72-141">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="63c72-p107">从管理计算机，在任务栏上，单击**远程任务 > 远程锁定**。出现提示时，单击**是**。</span><span class="sxs-lookup"><span data-stu-id="63c72-p107">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="63c72-144">Android 设备切换到锁定屏幕时观察其变化。</span><span class="sxs-lookup"><span data-stu-id="63c72-144">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="63c72-145">重置 Android 设备密码时，生成 Intune 管理门户，并配置强密码。</span><span class="sxs-lookup"><span data-stu-id="63c72-145">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="63c72-146">远程重置密码：</span><span class="sxs-lookup"><span data-stu-id="63c72-146">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="63c72-147">从管理计算机上的浏览器中，在**所有直接管理设备**窗格中，Microsoft Intune 管理控制台选项卡中，单击 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="63c72-147">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="63c72-148">在任务栏上，单击**远程任务 > 密码重置**。</span><span class="sxs-lookup"><span data-stu-id="63c72-148">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="63c72-p108">在**远程任务： 密码重置**提示下，单击**是**。等待一分钟。</span><span class="sxs-lookup"><span data-stu-id="63c72-p108">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="63c72-151">在**所有直接管理设备**窗格中，单击**查看属性**。</span><span class="sxs-lookup"><span data-stu-id="63c72-151">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="63c72-152">在**密码重置**，记下新密码。</span><span class="sxs-lookup"><span data-stu-id="63c72-152">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="63c72-153">在自己的 Android 设备的锁屏中输入新密码。 </span><span class="sxs-lookup"><span data-stu-id="63c72-153">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="63c72-154">若要更改密码后，转到**设置**、 点击**设备**、 点击**锁定屏幕**、 输入新密码再次、 点击**屏幕锁定**然后所选的密码。</span><span class="sxs-lookup"><span data-stu-id="63c72-154">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    

> [!TIP]
> <span data-ttu-id="63c72-155">单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="63c72-155">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="63c72-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63c72-156">See Also</span></span>

[<span data-ttu-id="63c72-157">Microsoft 365 企业版开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="63c72-157">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="63c72-158">用于 Microsoft 365 企业版开发/测试环境的 MAM 策略</span><span class="sxs-lookup"><span data-stu-id="63c72-158">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="63c72-159">云应用测试实验室指南 (TLGs)</span><span class="sxs-lookup"><span data-stu-id="63c72-159">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="63c72-160">企业移动 + 安全 (EMS)</span><span class="sxs-lookup"><span data-stu-id="63c72-160">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


