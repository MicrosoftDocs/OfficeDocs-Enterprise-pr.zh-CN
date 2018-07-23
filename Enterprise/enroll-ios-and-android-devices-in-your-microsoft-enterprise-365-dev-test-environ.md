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
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>在 Microsoft 365 企业版开发/测试环境中注册 iOS 和 Android 设备

 **摘要：** 使用此测试实验室指南注册 Microsoft 365 开发/测试环境中的设备和远程管理它们。
  
Microsoft 企业移动套件 (EMS) 可帮助保持员工提高生产效率的同时保护组织的数据使用他们喜欢的应用程序和设备。有关详细信息，请参阅[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。
  
如果您需要将应用设备级别的安全性，您必须注册到 Microsoft Intune 设备。设备注册不仅可帮助您管理组织负责设备，但还个人 (BYOD) 和共享的设备，具体取决于组织的法律策略。
  
按照本文中提供的说明进行操作，您将能够注册和 Microsoft 365 开发/测试环境中测试用于 iOS 和 Android 设备的基本的移动设备管理功能。
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>阶段 1： 创建 Microsoft 365 开发/测试环境

按照[Microsoft 365 企业版开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)中的说明。
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>阶段 2： 注册您的 iOS 和 Android 设备

首先，使用中的说明[安装和登录到的公司门户应用程序](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios)自定义 Microsoft Intune 的公司门户应用程序的测试环境。

注册 iOS 设备，接下来，使用[设置访问公司资源](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)中的说明。

注册 Android 设备，接下来，使用[注册中 Intune Android 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)中的说明。

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>第 3 阶段： 远程管理您的 iOS 和 Android 设备

Microsoft Intune 提供远程锁定和密码重置功能。如果某人丢失其设备，您可以远程锁定设备。如果某人忘记其密码，您可以重置密码远程。
  
远程锁定 iOS 或 Android 设备：

1. 登录到 Azure 门户在[https://portal.azure.com](https://portal.azure.com)的全局管理员帐户凭据。
2. 单击**所有服务**，键入**Intune**，，然后都单击**Intune**。
3. 单击**设备 > 所有设备**。
4. 在设备的列表中，单击 iOS 或 Android 设备，然后单击**远程锁定**操作。

    
远程重置密码：

1. 如果需要登录到 Azure 门户在[https://portal.azure.com](https://portal.azure.com)的全局管理员帐户凭据。
2. 单击**所有服务**，键入**Intune**，，然后都单击**Intune**。
3. 单击**设备 > 所有设备**。
4. 从设备列表中，您将管理、 单击 iOS 或 Android 设备，并选择 **...更多**。然后选择**删除密码**设备远程操作。

有关其他实验，请参阅[可用设备操作](https://docs.microsoft.com/intune/device-management#available-device-actions)。

    

> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。
  
## <a name="see-also"></a>另请参阅

[Microsoft 365 企业版开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[用于 Microsoft 365 企业版开发/测试环境的 MAM 策略](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[云应用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


