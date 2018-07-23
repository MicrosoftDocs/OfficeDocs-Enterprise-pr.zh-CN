---
title: 在 Microsoft 365 企业版开发/测试环境中注册 iOS 和 Android 设备
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 摘要： 使用此测试实验室指南注册 Microsoft 365 开发/测试环境中的设备和远程管理它们。
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720408"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="3574f-103">在 Microsoft 365 企业版开发/测试环境中注册 iOS 和 Android 设备</span><span class="sxs-lookup"><span data-stu-id="3574f-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="3574f-104">**摘要：** 使用此测试实验室指南注册 Microsoft 365 开发/测试环境中的设备和远程管理它们。</span><span class="sxs-lookup"><span data-stu-id="3574f-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="3574f-p101">Microsoft 企业移动套件 (EMS) 可帮助保持员工提高生产效率的同时保护组织的数据使用他们喜欢的应用程序和设备。有关详细信息，请参阅[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。</span><span class="sxs-lookup"><span data-stu-id="3574f-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="3574f-p102">如果您需要将应用设备级别的安全性，您必须注册到 Microsoft Intune 设备。设备注册不仅可帮助您管理组织负责设备，但还个人 (BYOD) 和共享的设备，具体取决于组织的法律策略。</span><span class="sxs-lookup"><span data-stu-id="3574f-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="3574f-109">按照本文中提供的说明进行操作，您将能够注册和 Microsoft 365 开发/测试环境中测试用于 iOS 和 Android 设备的基本的移动设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="3574f-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="3574f-110">阶段 1： 创建 Microsoft 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="3574f-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="3574f-111">按照[Microsoft 365 企业版开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="3574f-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="3574f-112">阶段 2： 注册您的 iOS 和 Android 设备</span><span class="sxs-lookup"><span data-stu-id="3574f-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="3574f-113">首先，使用中的说明[安装和登录到的公司门户应用程序](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios)自定义 Microsoft Intune 的公司门户应用程序的测试环境。</span><span class="sxs-lookup"><span data-stu-id="3574f-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your test environment.</span></span>

<span data-ttu-id="3574f-114">注册 iOS 设备，接下来，使用[设置访问公司资源](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)中的说明。</span><span class="sxs-lookup"><span data-stu-id="3574f-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="3574f-115">注册 Android 设备，接下来，使用[注册中 Intune Android 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)中的说明。</span><span class="sxs-lookup"><span data-stu-id="3574f-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="3574f-116">第 3 阶段： 远程管理您的 iOS 和 Android 设备</span><span class="sxs-lookup"><span data-stu-id="3574f-116">Phase 3: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="3574f-p103">Microsoft Intune 提供远程锁定和密码重置功能。如果某人丢失其设备，您可以远程锁定设备。如果某人忘记其密码，您可以重置密码远程。</span><span class="sxs-lookup"><span data-stu-id="3574f-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset it remotely.</span></span>
  
<span data-ttu-id="3574f-120">远程锁定 iOS 或 Android 设备：</span><span class="sxs-lookup"><span data-stu-id="3574f-120">To lock an iOS or Android device remotely:</span></span>

1. <span data-ttu-id="3574f-121">登录到 Azure 门户在[https://portal.azure.com](https://portal.azure.com)的全局管理员帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="3574f-121">Sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="3574f-122">单击**所有服务**，键入**Intune**，，然后都单击**Intune**。</span><span class="sxs-lookup"><span data-stu-id="3574f-122">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="3574f-123">单击**设备 > 所有设备**。</span><span class="sxs-lookup"><span data-stu-id="3574f-123">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="3574f-124">在设备的列表中，单击 iOS 或 Android 设备，然后单击**远程锁定**操作。</span><span class="sxs-lookup"><span data-stu-id="3574f-124">In the list of devices, click an iOS or Android device, and then click the **Remote lock** action.</span></span>

    
<span data-ttu-id="3574f-125">远程重置密码：</span><span class="sxs-lookup"><span data-stu-id="3574f-125">To reset the passcode remotely:</span></span>

1. <span data-ttu-id="3574f-126">如果需要登录到 Azure 门户在[https://portal.azure.com](https://portal.azure.com)的全局管理员帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="3574f-126">If needed, sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="3574f-127">单击**所有服务**，键入**Intune**，，然后都单击**Intune**。</span><span class="sxs-lookup"><span data-stu-id="3574f-127">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="3574f-128">单击**设备 > 所有设备**。</span><span class="sxs-lookup"><span data-stu-id="3574f-128">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="3574f-p104">从设备列表中，您将管理、 单击 iOS 或 Android 设备，并选择 **...更多**。然后选择**删除密码**设备远程操作。</span><span class="sxs-lookup"><span data-stu-id="3574f-p104">From the list of devices you manage, click an iOS or Android device, and choose **...More**. Then choose the **Remove passcode** device remote action.</span></span>

<span data-ttu-id="3574f-131">有关其他实验，请参阅[可用设备操作](https://docs.microsoft.com/intune/device-management#available-device-actions)。</span><span class="sxs-lookup"><span data-stu-id="3574f-131">For additional experimentation, see [Available device actions](https://docs.microsoft.com/intune/device-management#available-device-actions).</span></span>

    

> [!TIP]
> <span data-ttu-id="3574f-132">单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="3574f-132">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3574f-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3574f-133">See Also</span></span>

[<span data-ttu-id="3574f-134">Microsoft 365 企业版开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="3574f-134">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="3574f-135">用于 Microsoft 365 企业版开发/测试环境的 MAM 策略</span><span class="sxs-lookup"><span data-stu-id="3574f-135">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="3574f-136">云应用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="3574f-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="3574f-137">企业移动 + 安全 (EMS)</span><span class="sxs-lookup"><span data-stu-id="3574f-137">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


