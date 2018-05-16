---
title: Microsoft 365 企业版开发/测试环境的 MAM 策略
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: 摘要： 使用此测试实验室指南添加到 Microsoft 365 开发/测试环境 EMS 移动应用程序管理 (MAM) 策略。
ms.openlocfilehash: 1d4ede9b5757d4adce8909586790bcad51f7433f
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 企业版开发/测试环境的 MAM 策略

 **摘要：** 使用此测试实验室指南添加到 Microsoft 365 开发/测试环境 EMS 移动应用程序管理 (MAM) 策略。
  
Microsoft 企业移动 + 安全 (EMS) 有助于您的员工提高生产效率的同时保护组织的数据使用他们喜欢的应用程序和设备。有关详细信息，请参阅[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。
  
使用本文中的说明，您添加到 Microsoft 365 开发/测试环境移动应用程序管理 (MAM) 策略。
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>第 1 阶段： 构建 Microsoft 365 开发/测试环境

按照[Microsoft 365 企业版开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)中的说明。
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>第 2 阶段：为 iOS 和 Android 设备创建和部署 MAM 策略

在此阶段中，创建和部署两个不同的 MAM 策略：一个适用于 iOS 设备的策略和一个适用于 Android 设备的策略。
  
1. 转到 Office 365 门户 ([https://portal.office.com](https://portal.office.com)) 和 Office 365 试用版订阅与全局管理员帐户登录。
    
2. 在浏览器的新建选项卡上，打开 Azure 门户网站 ([https://azure.portal.com](https://azure.portal.com)) 和使用 Office 365 全局管理员帐户登录。
    
3. Azure 门户选项卡在 Internet Explorer 中，在导航窗格中，单击**所有服务**，键入**Intune**，，然后都单击**Intune**。
    
4. 在左侧导航窗格中，单击“组”****。
    
5. 在**组所有组**刀片中，单击 **+ 新建组**。
    
6. 在**组**刀片中，选择**Office 365** **组类型？**，请在**名称**框中，键入**托管 iOS 设备用户**在**成员资格类型**，选择**已分配**，然后单击**创建**。 
    
7. 关闭**组**刀片。
    
8. 在**组所有组**刀片中，单击**添加**。
    
9. 在**组**刀片中，选择**Office 365** **组类型？**，请在**名称**框中，键入**托管 Android 设备用户**在**成员资格类型**，选择**已分配**，然后单击**创建**。
    
10. 关闭**组所有组**刀片。
    
11. 在**Intune**刀片，在**快速的任务**列表中，单击**创建合规性策略**。
    
12. 在**合规性策略配置文件**刀片中，单击**创建策略**。
    
13. 在**创建策略**刀片，在**名称**框中，键入**iOS**。在**平台**中，选择**iOS**、 **iOS 合规性策略**刀片上, 单击**确定**，然后单击**创建**。
    
14. 在**合规性策略配置文件**刀片中，单击**创建策略**。
    
15. 在**创建策略**刀片，在**名称**框中，键入**Android**。**平台**中, 选择**Android**， **Android 合规性策略**刀片上, 单击**确定**，然后单击**创建**。
    
16. 在**合规性策略配置文件**刀片中，单击**Android**的策略名称。
    
17. **Android-属性**刀片的左侧导航中，单击**分配**，，然后单击**选择组**。
    
18. **选择组**刀片上,**托管 Android 设备用户**的组中，单击，然后单击**选择**。
    
19. 单击**保存**，然后关闭**Android-分配**刀片。
    
20. 在**合规性策略配置文件**刀片中，单击**iOS**策略名称。
    
21. 在**iOS-属性**刀片左侧导航窗格中，单击**工作分配**，然后单击**选择组**。
    
22. 在**选择组**刀片中，单击**托管 iOS 设备用户**组中，，然后单击**选择**。
    
23. 单击**保存**，然后关闭**iOS-分配**刀片。
    
24. 关闭**合规性策略配置文件**刀片。
    
25. 在**Intune**刀片，单击左侧导航窗格中的**管理应用程序**。
    
26. 在**移动应用程序**刀片中，单击**应用程序**。
    
27. 在应用程序列表中，单击**PowerPoint** 
    
28. 在**PowerPoint 概述**刀片中，单击**分配 > 选择组 > 托管 iOS 设备 > 选择**。在**类型**中，选择**有空**，，然后单击**保存**。
    
29. 对以下应用重复执行第 28 步：
    
  - Outlook for Android
    
  - Word for iOS
    
  - Excel for iOS
    
  - Outlook iOS
    
  - 适用于 iOS iPad 的 Microsoft Dynamics CRM
    
  - 适用于 iOS iPhone 的 Microsoft Dynamics CRM
    
  - 适用于 Android 手机的 Dynamics CRM
    
  - 适用于 Android 平板电脑的 Dynamics CRM
    
  - Excel for Android
    
  - Word for Android
    
  - OneNote for iOS
    
30. 关闭**移动应用程序的应用程序**刀片。
    
31. 在**移动应用程序**刀片中，单击**应用程序保护策略**。
    
32. 在**应用程序保护策略**刀片中，单击**添加策略**。
    
33. 在**添加策略**刀片中，键入**iOS**，，然后单击**选择所需的应用程序**。
    
34. 在**应用程序**刀片， **PowerPoint**、 **iPhone 上的 Microsoft Dynamics CRM**、 **Excel**、 **iPhone 上的 Microsoft Dynamics CRM**、 **Word**、 **OneNote**和**Outlook**中，单击，然后单击**选择**。
    
35. 在**添加策略**刀片中，单击**创建**。
    
36. 在**应用程序保护策略**刀片中，单击**添加策略**。
    
37. **添加策略**刀片上, 键入**Android**，在**平台**选择**Android** ，然后单击**选择所需的应用程序**。
    
38. 在**应用程序**刀片中，单击**PowerPoint**、**平板电脑的 Dynamics CRM**、 **Excel**、 **Word**、 **Outlook**和**电话的 Dynamics CRM**、，然后单击**选择**。
    
39. 在**添加策略**刀片中，单击**创建**。
    
现在你有两个 MAM 策略，一个适用于 iOS 设备的策略和一个适用于 Android 设备的策略，并已准备好对所选应用的测试设置进行测试。
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。
  
## <a name="see-also"></a>另请参阅

[Microsoft 365 企业版开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[在 Microsoft 企业版 365 开发/测试环境中注册 iOS 和 Android 设备](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[云应用测试实验室指南 (TLGs)](cloud-adoption-test-lab-guides-tlgs.md)

[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


