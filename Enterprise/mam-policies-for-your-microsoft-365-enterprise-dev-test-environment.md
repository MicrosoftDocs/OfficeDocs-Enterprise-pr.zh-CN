---
title: "您的 Microsoft 365 企业开发/测试环境的 MAM 策略"
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: "摘要： 使用此测试实验室指南 EMS 移动应用程序管理 (MAM) 策略添加到 Microsoft 365 开发/测试环境。"
ms.openlocfilehash: d088970dca1ec55212642f16d0519e89bd9591e5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="40c29-103">您的 Microsoft 365 企业开发/测试环境的 MAM 策略</span><span class="sxs-lookup"><span data-stu-id="40c29-103">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="40c29-104">**摘要：**此测试实验室指南用于 EMS 移动应用程序管理 (MAM) 策略添加到 Microsoft 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="40c29-104">**Summary:** Use this Test Lab Guide to add EMS mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
<span data-ttu-id="40c29-p101">Microsoft 的企业移动性 + 安全 (EMS) 可帮助使您的员工提高工作效率的同时保护您组织的数据使用他们最喜欢的应用程序和设备。有关详细信息，请参阅[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。</span><span class="sxs-lookup"><span data-stu-id="40c29-p101">The Microsoft Enterprise Mobility + Security (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="40c29-107">使用本文中的说明进行操作，移动应用程序管理 (MAM) 策略添加到 Microsoft 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="40c29-107">With the instructions in this article, you add mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a><span data-ttu-id="40c29-108">第 1 阶段： 构建您的 Microsoft 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="40c29-108">Phase 1: Build out your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="40c29-109">按照[Microsoft 365 企业开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="40c29-109">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a><span data-ttu-id="40c29-110">第 2 阶段：为 iOS 和 Android 设备创建和部署 MAM 策略</span><span class="sxs-lookup"><span data-stu-id="40c29-110">Phase 2: Create and deploy MAM policies for iOS and Android devices</span></span>

<span data-ttu-id="40c29-111">在此阶段中，创建和部署两个不同的 MAM 策略：一个适用于 iOS 设备的策略和一个适用于 Android 设备的策略。</span><span class="sxs-lookup"><span data-stu-id="40c29-111">In this phase, you create and deploy two different MAM policies: one for iOS devices and one for Android devices.</span></span>
  
1. <span data-ttu-id="40c29-112">请转到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com)) 并登录到您的 Office 365 试用预订使用全局管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="40c29-112">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="40c29-113">您的浏览器的新建选项卡上，打开 Azure 门户网站 ([https://azure.portal.com](https://azure.portal.com))，使用 Office 365 的全局管理员帐户进行登录。</span><span class="sxs-lookup"><span data-stu-id="40c29-113">On a new tab of your browser, open the Azure portal ([https://azure.portal.com](https://azure.portal.com)) and sign in using your Office 365 global administrator account.</span></span>
    
3. <span data-ttu-id="40c29-114">在 Azure 门户中的选项卡在 Internet Explorer 中的导航窗格中，单击**更多的服务**（或右箭头），键入**Intune**，，然后单击**Intune**。</span><span class="sxs-lookup"><span data-stu-id="40c29-114">On the Azure portal tab in Internet Explorer, in the navigation pane, click **More services** (or the right arrow), type **Intune**, and then click **Intune**.</span></span>
    
4. <span data-ttu-id="40c29-115">在左侧导航窗格中，单击“组”****。</span><span class="sxs-lookup"><span data-stu-id="40c29-115">In the left navigation pane, click **Groups**.</span></span>
    
5. <span data-ttu-id="40c29-116">在**用户和组的所有组**刀片式服务器，单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="40c29-116">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
6. <span data-ttu-id="40c29-117">在**组**刀片式服务器，在**名称**中键入**管理 iOS 设备用户**选择**分配****成员资格类型**中，选择**是**的**启用 Office 功能？**，然后单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="40c29-117">On the **Group** blade, type **Managed iOS device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span> 
    
7. <span data-ttu-id="40c29-118">关闭**组**刀片。</span><span class="sxs-lookup"><span data-stu-id="40c29-118">Close the **Group** blade.</span></span>
    
8. <span data-ttu-id="40c29-119">在**用户和组的所有组**刀片式服务器，单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="40c29-119">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
9. <span data-ttu-id="40c29-120">在**组**刀片式服务器，在**名称**中键入**托管 Android 设备用户****已分配**字段中选择**成员资格类型**，请选择**是**的**启用 Office 功能？**，然后单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="40c29-120">On the **Group** blade, type **Managed Android device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="40c29-121">关闭**的用户和组的所有组**刀片。</span><span class="sxs-lookup"><span data-stu-id="40c29-121">Close the **Users and groups-All groups** blade.</span></span>
    
11. <span data-ttu-id="40c29-122">在**Intune**刀片式服务器，在**快速的任务**列表中，单击**创建一个法规遵从性策略**。</span><span class="sxs-lookup"><span data-stu-id="40c29-122">On the **Intune** blade, in the **Quick tasks** list, click **Create a compliance policy**.</span></span>
    
12. <span data-ttu-id="40c29-123">**法规遵从性策略配置文件**刀片式服务器，请单击**创建策略**。</span><span class="sxs-lookup"><span data-stu-id="40c29-123">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
13. <span data-ttu-id="40c29-p102">**创建策略**刀片式服务器，在**名称**中，键入**iOS**。在**平台**选择**iOS**， **iOS 的法规遵从性策略**刀片式服务器，单击**确定**，然后单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="40c29-p102">On the **Create Policy** blade, in **Name**, type **iOS**. In **Platform**, select **iOS**, click **OK** on the **iOS compliance policy** blade, and then click **Create**.</span></span>
    
14. <span data-ttu-id="40c29-126">**法规遵从性策略配置文件**刀片式服务器，请单击**创建策略**。</span><span class="sxs-lookup"><span data-stu-id="40c29-126">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
15. <span data-ttu-id="40c29-p103">在**创建策略**刀片式服务器，在**名称**中，键入**Android**。在**平台**选择**Android**， **Android 的法规遵从性策略**刀片式服务器，单击**确定**，然后单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="40c29-p103">On the **Create Policy** blade, in **Name**, type **Android**. In **Platform**, select **Android**, click **OK** on the **Android compliance policy** blade, and then click **Create**.</span></span>
    
16. <span data-ttu-id="40c29-129">**法规遵从性策略配置文件**刀片式服务器，请单击**Android**的策略名称。</span><span class="sxs-lookup"><span data-stu-id="40c29-129">On the **Compliance Policy Profiles** blade, click the **Android** policy name.</span></span>
    
17. <span data-ttu-id="40c29-130">**Android 的属性**刀片的左导航，**工作分配**，请单击，然后单击**选择组**。</span><span class="sxs-lookup"><span data-stu-id="40c29-130">In the left navigation of the **Android - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
18. <span data-ttu-id="40c29-131">在**组中选择**刀片式服务器，**管理 Android 设备用户**组中，单击，再单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="40c29-131">On the **Select groups** blade, click the **Managed Android device users** group, and then click **Select**.</span></span>
    
19. <span data-ttu-id="40c29-132">单击**保存**，然后关闭**Android 的分配**刀片式服务器。</span><span class="sxs-lookup"><span data-stu-id="40c29-132">Click **Save**, and then close the **Android - Assignments** blade.</span></span>
    
20. <span data-ttu-id="40c29-133">**法规遵从性策略配置文件**刀片式服务器，请单击**Io**策略名称。</span><span class="sxs-lookup"><span data-stu-id="40c29-133">On the **Compliance Policy Profiles** blade, click the **iOS** policy name.</span></span>
    
21. <span data-ttu-id="40c29-134">在左侧导航的**iOS 的属性**刀片式服务器，单击**分配**，，然后单击**选择组**。</span><span class="sxs-lookup"><span data-stu-id="40c29-134">In the left navigation of the **iOS - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
22. <span data-ttu-id="40c29-135">在**组中选择**刀片式服务器，**管理 iOS 设备用户**组中，单击，再单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="40c29-135">On the **Select groups** blade, click the **Managed iOS device users** group, and then click **Select**.</span></span>
    
23. <span data-ttu-id="40c29-136">单击**保存**，然后关闭刀片式服务器**iOS 的分配**。</span><span class="sxs-lookup"><span data-stu-id="40c29-136">Click **Save**, and then close the **iOS - Assignments** blade.</span></span>
    
24. <span data-ttu-id="40c29-137">关闭刀片式服务器**的法规遵从性策略的配置文件**。</span><span class="sxs-lookup"><span data-stu-id="40c29-137">Close the **Compliance Policy Profiles** blade.</span></span>
    
25. <span data-ttu-id="40c29-138">**Intune**刀片式服务器，请单击在左侧导航窗格中的**管理应用程序**。</span><span class="sxs-lookup"><span data-stu-id="40c29-138">On the **Intune** blade, click **Manage apps** in the left navigation.</span></span>
    
26. <span data-ttu-id="40c29-139">在**移动应用程序**刀片式服务器，单击**应用程序**。</span><span class="sxs-lookup"><span data-stu-id="40c29-139">On the **Mobile Apps** blade, click **Apps**.</span></span>
    
27. <span data-ttu-id="40c29-140">在应用程序的列表中，请单击**PowerPoint**，</span><span class="sxs-lookup"><span data-stu-id="40c29-140">In the list of apps, click **PowerPoint**,</span></span> 
    
28. <span data-ttu-id="40c29-p104">在**PowerPoint 概述**刀片式服务器，请单击**分配 > 选择组 > 管理的 iOS 设备 > 选择**。在**类型**框中，选择**可用**，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="40c29-p104">On the **PowerPoint Overview** blade, click **Assignments > Select groups > Managed iOS devices > Select**. In **Type**, select **Available**, and then click **Save**.</span></span>
    
29. <span data-ttu-id="40c29-143">对以下应用重复执行第 28 步：</span><span class="sxs-lookup"><span data-stu-id="40c29-143">Repeat step 28 for the following apps:</span></span>
    
  - <span data-ttu-id="40c29-144">Outlook for Android</span><span class="sxs-lookup"><span data-stu-id="40c29-144">Outlook for Android</span></span>
    
  - <span data-ttu-id="40c29-145">Word for iOS</span><span class="sxs-lookup"><span data-stu-id="40c29-145">Word for iOS</span></span>
    
  - <span data-ttu-id="40c29-146">Excel for iOS</span><span class="sxs-lookup"><span data-stu-id="40c29-146">Excel for iOS</span></span>
    
  - <span data-ttu-id="40c29-147">Outlook iOS</span><span class="sxs-lookup"><span data-stu-id="40c29-147">Outlook for iOS</span></span>
    
  - <span data-ttu-id="40c29-148">适用于 iOS iPad 的 Microsoft Dynamics CRM</span><span class="sxs-lookup"><span data-stu-id="40c29-148">Microsoft Dynamics CRM on iPad for iOS</span></span>
    
  - <span data-ttu-id="40c29-149">适用于 iOS iPhone 的 Microsoft Dynamics CRM</span><span class="sxs-lookup"><span data-stu-id="40c29-149">Microsoft Dynamics CRM on iPhone for iOS</span></span>
    
  - <span data-ttu-id="40c29-150">适用于 Android 手机的 Dynamics CRM</span><span class="sxs-lookup"><span data-stu-id="40c29-150">Dynamics CRM for Phones for Android</span></span>
    
  - <span data-ttu-id="40c29-151">适用于 Android 平板电脑的 Dynamics CRM</span><span class="sxs-lookup"><span data-stu-id="40c29-151">Dynamics CRM for Tablets for Android</span></span>
    
  - <span data-ttu-id="40c29-152">Excel for Android</span><span class="sxs-lookup"><span data-stu-id="40c29-152">Excel for Android</span></span>
    
  - <span data-ttu-id="40c29-153">Word for Android</span><span class="sxs-lookup"><span data-stu-id="40c29-153">Word for Android</span></span>
    
  - <span data-ttu-id="40c29-154">OneNote for iOS</span><span class="sxs-lookup"><span data-stu-id="40c29-154">OneNote for iOS</span></span>
    
30. <span data-ttu-id="40c29-155">关闭刀片式服务器**移动应用程序的应用程序**。</span><span class="sxs-lookup"><span data-stu-id="40c29-155">Close the **Mobile Apps - Apps** blade.</span></span>
    
31. <span data-ttu-id="40c29-156">在**移动应用程序**刀片式服务器，单击**应用程序保护策略**。</span><span class="sxs-lookup"><span data-stu-id="40c29-156">On the **Mobile Apps** blade, click **App Protection Policies**.</span></span>
    
32. <span data-ttu-id="40c29-157">在**应用程序保护策略**刀片式服务器，请单击**添加策略**。</span><span class="sxs-lookup"><span data-stu-id="40c29-157">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
33. <span data-ttu-id="40c29-158">**策略添加**刀片式服务器，在**iOS**中，键入，然后单击**选择所需的应用程序**。</span><span class="sxs-lookup"><span data-stu-id="40c29-158">On the **Add a policy** blade, type **iOS**, and then click **Select required apps**.</span></span>
    
34. <span data-ttu-id="40c29-159">在**应用程序**刀片式服务器，单击**PowerPoint**， **iPhone 上的 Microsoft Dynamics CRM**、 **Excel**、**在 iPhone 上的 Microsoft Dynamics CRM**、**字**、 **OneNote**和**Outlook**，，然后单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="40c29-159">On the **Apps** blade, click **PowerPoint**, **Microsoft Dynamics CRM on iPhone**, **Excel**, **Microsoft Dynamics CRM on iPhone**, **Word**, **OneNote**, and **Outlook**, and then click **Select**.</span></span>
    
35. <span data-ttu-id="40c29-160">在**策略添加**刀片式服务器，请单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="40c29-160">On the **Add a policy** blade, click **Create**.</span></span>
    
36. <span data-ttu-id="40c29-161">在**应用程序保护策略**刀片式服务器，请单击**添加策略**。</span><span class="sxs-lookup"><span data-stu-id="40c29-161">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
37. <span data-ttu-id="40c29-162">**策略添加**刀片式服务器，键入**Android**， **Android** **平台**，选择，然后单击**选择所需的应用程序**。</span><span class="sxs-lookup"><span data-stu-id="40c29-162">On the **Add a policy** blade, type **Android**, select **Android** in **Platform**, and then click **Select required apps**.</span></span>
    
38. <span data-ttu-id="40c29-163">在**应用程序**刀片式服务器，单击**PowerPoint**， **Dynamics CRM 的平板电脑**、 **Excel**、 **Word**、 **Outlook**，然后**Dynamics CRM 的电话**，，然后单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="40c29-163">On the **Apps** blade, click **PowerPoint**, **Dynamics CRM for tablets**, **Excel**, **Word**, **Outlook**, and **Dynamics CRM for phones**, and then click **Select**.</span></span>
    
39. <span data-ttu-id="40c29-164">在**策略添加**刀片式服务器，请单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="40c29-164">On the **Add a policy** blade, click **Create**.</span></span>
    
<span data-ttu-id="40c29-165">现在你有两个 MAM 策略，一个适用于 iOS 设备的策略和一个适用于 Android 设备的策略，并已准备好对所选应用的测试设置进行测试。</span><span class="sxs-lookup"><span data-stu-id="40c29-165">You now have two MAM policies, one for iOS devices and one for Android devices, and are ready to experiment with testing settings for the selected apps.</span></span>
  
> [!TIP]
> <span data-ttu-id="40c29-166">单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的项目的所有。</span><span class="sxs-lookup"><span data-stu-id="40c29-166">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="40c29-167">See Also</span><span class="sxs-lookup"><span data-stu-id="40c29-167">See Also</span></span>

[<span data-ttu-id="40c29-168">Microsoft 365 企业开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="40c29-168">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="40c29-169">IOS 和 Android 设备在 Microsoft 企业 365 开发/测试环境中注册</span><span class="sxs-lookup"><span data-stu-id="40c29-169">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[<span data-ttu-id="40c29-170">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="40c29-170">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="40c29-171">企业移动 + 安全 (EMS)</span><span class="sxs-lookup"><span data-stu-id="40c29-171">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


