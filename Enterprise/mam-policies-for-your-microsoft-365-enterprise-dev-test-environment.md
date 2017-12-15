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
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>您的 Microsoft 365 企业开发/测试环境的 MAM 策略

 **摘要：**此测试实验室指南用于 EMS 移动应用程序管理 (MAM) 策略添加到 Microsoft 365 开发/测试环境。
  
Microsoft 的企业移动性 + 安全 (EMS) 可帮助使您的员工提高工作效率的同时保护您组织的数据使用他们最喜欢的应用程序和设备。有关详细信息，请参阅[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。
  
使用本文中的说明进行操作，移动应用程序管理 (MAM) 策略添加到 Microsoft 365 开发/测试环境。
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>第 1 阶段： 构建您的 Microsoft 365 开发/测试环境

按照[Microsoft 365 企业开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)中的说明进行操作。
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>第 2 阶段：为 iOS 和 Android 设备创建和部署 MAM 策略

在此阶段中，创建和部署两个不同的 MAM 策略：一个适用于 iOS 设备的策略和一个适用于 Android 设备的策略。
  
1. 请转到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com)) 并登录到您的 Office 365 试用预订使用全局管理员帐户。
    
2. 您的浏览器的新建选项卡上，打开 Azure 门户网站 ([https://azure.portal.com](https://azure.portal.com))，使用 Office 365 的全局管理员帐户进行登录。
    
3. 在 Azure 门户中的选项卡在 Internet Explorer 中的导航窗格中，单击**更多的服务**（或右箭头），键入**Intune**，，然后单击**Intune**。
    
4. 在左侧导航窗格中，单击“组”****。
    
5. 在**用户和组的所有组**刀片式服务器，单击**添加**。
    
6. 在**组**刀片式服务器，在**名称**中键入**管理 iOS 设备用户**选择**分配****成员资格类型**中，选择**是**的**启用 Office 功能？**，然后单击**创建**。 
    
7. 关闭**组**刀片。
    
8. 在**用户和组的所有组**刀片式服务器，单击**添加**。
    
9. 在**组**刀片式服务器，在**名称**中键入**托管 Android 设备用户****已分配**字段中选择**成员资格类型**，请选择**是**的**启用 Office 功能？**，然后单击**创建**。
    
10. 关闭**的用户和组的所有组**刀片。
    
11. 在**Intune**刀片式服务器，在**快速的任务**列表中，单击**创建一个法规遵从性策略**。
    
12. **法规遵从性策略配置文件**刀片式服务器，请单击**创建策略**。
    
13. **创建策略**刀片式服务器，在**名称**中，键入**iOS**。在**平台**选择**iOS**， **iOS 的法规遵从性策略**刀片式服务器，单击**确定**，然后单击**创建**。
    
14. **法规遵从性策略配置文件**刀片式服务器，请单击**创建策略**。
    
15. 在**创建策略**刀片式服务器，在**名称**中，键入**Android**。在**平台**选择**Android**， **Android 的法规遵从性策略**刀片式服务器，单击**确定**，然后单击**创建**。
    
16. **法规遵从性策略配置文件**刀片式服务器，请单击**Android**的策略名称。
    
17. **Android 的属性**刀片的左导航，**工作分配**，请单击，然后单击**选择组**。
    
18. 在**组中选择**刀片式服务器，**管理 Android 设备用户**组中，单击，再单击**选择**。
    
19. 单击**保存**，然后关闭**Android 的分配**刀片式服务器。
    
20. **法规遵从性策略配置文件**刀片式服务器，请单击**Io**策略名称。
    
21. 在左侧导航的**iOS 的属性**刀片式服务器，单击**分配**，，然后单击**选择组**。
    
22. 在**组中选择**刀片式服务器，**管理 iOS 设备用户**组中，单击，再单击**选择**。
    
23. 单击**保存**，然后关闭刀片式服务器**iOS 的分配**。
    
24. 关闭刀片式服务器**的法规遵从性策略的配置文件**。
    
25. **Intune**刀片式服务器，请单击在左侧导航窗格中的**管理应用程序**。
    
26. 在**移动应用程序**刀片式服务器，单击**应用程序**。
    
27. 在应用程序的列表中，请单击**PowerPoint**， 
    
28. 在**PowerPoint 概述**刀片式服务器，请单击**分配 > 选择组 > 管理的 iOS 设备 > 选择**。在**类型**框中，选择**可用**，然后单击**保存**。
    
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
    
30. 关闭刀片式服务器**移动应用程序的应用程序**。
    
31. 在**移动应用程序**刀片式服务器，单击**应用程序保护策略**。
    
32. 在**应用程序保护策略**刀片式服务器，请单击**添加策略**。
    
33. **策略添加**刀片式服务器，在**iOS**中，键入，然后单击**选择所需的应用程序**。
    
34. 在**应用程序**刀片式服务器，单击**PowerPoint**， **iPhone 上的 Microsoft Dynamics CRM**、 **Excel**、**在 iPhone 上的 Microsoft Dynamics CRM**、**字**、 **OneNote**和**Outlook**，，然后单击**选择**。
    
35. 在**策略添加**刀片式服务器，请单击**创建**。
    
36. 在**应用程序保护策略**刀片式服务器，请单击**添加策略**。
    
37. **策略添加**刀片式服务器，键入**Android**， **Android** **平台**，选择，然后单击**选择所需的应用程序**。
    
38. 在**应用程序**刀片式服务器，单击**PowerPoint**， **Dynamics CRM 的平板电脑**、 **Excel**、 **Word**、 **Outlook**，然后**Dynamics CRM 的电话**，，然后单击**选择**。
    
39. 在**策略添加**刀片式服务器，请单击**创建**。
    
现在你有两个 MAM 策略，一个适用于 iOS 设备的策略和一个适用于 Android 设备的策略，并已准备好对所选应用的测试设置进行测试。
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的项目的所有。
  
## <a name="see-also"></a>See Also

[Microsoft 365 企业开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[IOS 和 Android 设备在 Microsoft 企业 365 开发/测试环境中注册](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


