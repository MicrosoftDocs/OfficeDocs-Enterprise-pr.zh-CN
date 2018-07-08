---
title: 在 Microsoft 365 企业版开发/测试环境中注册 iOS 和 Android 设备
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: 摘要： 使用此测试实验室指南注册 Microsoft 365 开发/测试环境中的设备和远程管理它们。
ms.openlocfilehash: a5d43a0ef3ed090f84c8415de3ac26f53fdafe0a
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188100"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>在 Microsoft 365 企业版开发/测试环境中注册 iOS 和 Android 设备

 **摘要：** 使用此测试实验室指南注册 Microsoft 365 开发/测试环境中的设备和远程管理它们。
  
Microsoft 企业移动套件 (EMS) 可帮助保持员工提高生产效率的同时保护组织的数据使用他们喜欢的应用程序和设备。有关详细信息，请参阅[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。
  
如果您需要将应用设备级别的安全性，您必须注册到 Microsoft Intune 设备。设备注册不仅可帮助您管理组织负责设备，但还个人 (BYOD) 和共享的设备，具体取决于组织的法律策略。
  
按照本文中提供的说明进行操作，您将能够注册和 Microsoft 365 开发/测试环境中测试用于 iOS 和 Android 设备的基本的移动设备管理功能。
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>阶段 1： 创建 Microsoft 365 开发/测试环境

按照[Microsoft 365 企业版开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)中的说明。
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>阶段 2： 注册您的 iOS 和 Android 设备

首先，使用中的说明[安装和登录到的公司门户应用程序](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios)开发/测试租户自定义 Microsoft Intune 的公司门户应用程序。

注册 iOS 设备，接下来，使用[设置访问公司资源](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)中的说明。

注册 Android 设备，接下来，使用[注册中 Intune Android 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)中的说明。

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a>第 2 阶段： 远程管理您的 iOS 和 Android 设备

Microsoft Intune 提供远程锁定和密码重置两种功能。如果有人丢失了自己的设备，则可以远程锁定设备。如果有人忘记了自己的密码，则可以远程删除密码。
  
远程锁定 iOS 设备：
  
1.  打开新选项卡并转到http://manage.microsoft.com（如果需要）。 

2.  从浏览器的 Microsoft Intune 管理控制台中，单击左侧导航窗格中的**组**。

3. 在“**组**”窗格中，打开“**所有设备>所有移动设备>所有直接托管设备**”。
    
4. 在“**所有直接托管设备**”窗格中，单击“**设备**”选项卡。
    
5. 在设备列表中，单击自己的 iOS 设备。  
    
6. 在自己的 iOS 设备中，请确保其位于主屏幕上。  
    
7. 在自己的管理计算机中的任务栏中，单击“ **远程任务>远程锁定**”。在 iOS 设备切换到锁定屏幕时观察设备变化。
    
删除密码：
  
1. 从自己的管理计算机的“**所有直接托管设备**”窗格中，单击“**设备**”选项卡。
    
2. 在列表中，单击你的 iOS 设备。在任务栏上单击“**远程任务>密码重置**”。等待一分钟。
    
3. 在你的 iOS 设备中将其解锁，注意此时不再存在密码。若要恢复密码，则依次进入“**设置**”、“**密码**”。
    
远程锁定 Android 设备：
  
1. 从浏览器的 Microsoft Intune 管理控制台中，单击左侧导航窗格中的**组**。
    
2. 在“**组**”窗格中，打开“**所有设备>所有移动设备>所有直接托管设备**”。
    
3. 在“**所有直接托管设备**”窗格中，单击“**设备**”选项卡。
    
4. 在设备列表中，单击自己的 Android 设备。  
    
5. 在自己的 Android 设备中，请确保其位于主屏幕上。  
    
6. 在自己的管理计算机中的任务栏中，单击“ **远程任务>远程锁定**”。出现提示时，请单击“**是**”。
    
7. Android 设备切换到锁定屏幕时观察其变化。
    
重置 Android 设备密码时，生成 Intune 管理门户，并配置强密码。
  
远程重置密码：
  
1. 在自己的管理计算机中，从浏览器的“Microsoft Intune 管理控制台”选项卡中的“**所有直接托管设备**”窗格中单击自己的 Android 设备。
    
2. 在任务栏上单击“**远程任务>密码重置**”。
    
3. 在“**远程任务:密码重置**”提示符上，单击“**是**”。等待一分钟。
    
4. 在“**所有直接托管设备**”窗格中，单击“**查看属性**”。
    
5. 在“**密码重置**”中，写入新的密码。
    
6. 在自己的 Android 设备的锁屏中输入新密码。  
    
7. 若要恢复密码，则进入“**设置**”，点按“**设备**”，然后点按“**锁屏**”，然后再次输入新密码，然后依次点按“**屏幕锁定**”和自己选择的密码。
    

> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。
  
## <a name="see-also"></a>另请参阅

[Microsoft 365 企业版开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[用于 Microsoft 365 企业版开发/测试环境的 MAM 策略](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


