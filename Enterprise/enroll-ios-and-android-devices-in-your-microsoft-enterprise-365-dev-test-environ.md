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
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "摘要： 使用此测试实验室指南注册 Microsoft 365 开发/测试环境中的设备，并对其进行远程管理。"
ms.openlocfilehash: 77b5074b083656fdfa2cd460510231dae0689d10
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a>IOS 和 Android 设备在 Microsoft 企业 365 开发/测试环境中注册

 **摘要：**此测试实验室指南用于注册 Microsoft 365 开发/测试环境中的设备并对其进行远程管理。
  
Microsoft 企业移动套件 (EMS) 有助于使您的员工提高工作效率的同时保护您组织的数据使用他们最喜欢的应用程序和设备。有关详细信息，请参阅[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)。
  
如果需要在设计级别应用安全性，则必须将设备注册到 Microsoft Intune。设备注册不仅有助于管理企业所有的设备，还可以根据组织的法律政策管理个人 (BYOD) 和共享设备。
  
通过遵循本文中提供的说明进行操作，您可以注册和 Microsoft 365 开发/测试环境中测试 iOS 和 Android 设备的基本移动设备管理功能。
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>阶段 1： 创建 Microsoft 365 开发/测试环境

按照[Microsoft 365 企业开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)中的说明进行操作。
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a>第 2 阶段：自定义 Microsoft Intune 公司门户应用

使用以下步骤为虚构的公司自定义 Microsoft Intune 公司门户应用：
  
1. 在新的选项卡上，打开 Microsoft Intune 管理控制台 ([https://manage.microsoft.com](https://manage.microsoft.com))。
    
2. 请在导航窗格中单击**管理员**，然后单击**管理**窗格中的**移动设备管理**。
    
3. 在**任务**列表中，选择**设置移动设备管理机构**。请确保它被设置为**Microsoft Intune**。
    
4. 在**管理**窗格中，单击**公司入口**。
    
5. **公司门户**的窗格中，配置下列设置：
    
  - 公司名称：\<虚构的公司名 >
    
  - IT 部门联系人名称： **User5**
    
  - IT 部门的电话号码： **555-1234**
    
  - IT 部门的电子邮件地址： **User5 @**\<虚构的单位名称 > **。 onmicrosoft.com** （User5 帐户的电子邮件地址）
    
6. 在**自定义**，选择**主题颜色**中的**绿色**。
    
7. 单击“**保存**”。
    
接下来要安装 Microsoft Intune 公司门户应用并注册 iOS 或 Android 设备，然后测试 Microsoft Intune 管理控制台中的基本管理功能。
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a>第 3 阶段（仅适用于 iOS 设备）：注册并管理 iOS 设备

若要注册 iOS 设备以通过 Intune 进行管理，需要具备以下条件：
  
- 一台 iOS设备，例如 Apple iPad 或 iPhone。
    
- IOS 设备通行码的知识。
    
- 一个苹果 ID （帐户名和密码）。如果您没有一个，转到[苹果 ID 网站](https://appleid.apple.com/#!&amp;page=signin)，然后单击**创建您的苹果 ID**。创建苹果 ID 对应于您的 Office 365 订购的全局管理员帐户。在一个安全的位置中记录您的新的苹果 ID 帐户名和密码。
    
Intune 管理 iOS 和 Mac 设备需具备 Apple 推送通知服务 (APNs) 证书。将该证书添加到 Intune 后，用户即可安装 Microsoft Intune 公司门户应用来注册自己的设备，管理员则可以设置对企业所有的 iOS 设备的管理。
  
需要一个证书签名请求文件来向 Apple 推送证书门户请求信任关系证书。获取证书签名请求文件：
  
1. 在 Microsoft Intune 管理控制台中，请单击导航窗格中的**管理员**。
    
    在**管理**窗格中，打开**移动设备管理 > iOS 和 Mac OS X**，然后单击**上载 APNs 证书****任务**中。 
    
2. 在**上载 APNs 证书**窗格中，单击**下载 APNs 证书申请**。保存证书签名请求 (.csr) 文件本地名称**开发测试**。
    
获取 Apple 推送通知服务证书：
  
1. 打开一个新标签，转到了[苹果将推证书门户](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)，登录您的苹果 id。
    
2. 在**开始**页中，单击**证书**。
    
3. 在**使用条款的**页上，选择**我已阅读并同意这些条款和条件**，然后单击**接受**。
    
4. **创建一个新的推证书**页上单击**浏览**并选择保存在上一过程中，**开发 test.csr**文件，然后单击**上载**。当系统提示您打开一个 json 文件，则将其保存到同一开发 test.csr 文件所在的文件夹。
    
5. 打开[苹果将推证书门户网站](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)在不同的选项卡上，对于**第三方服务器的证书**，单击**下载**。
    
6. 当系统提示您打开.pem 文件，保存与开发 test.csr 文件的存储位置的相同文件夹名称**开发 test.pem** 。这是 APNs 证书。
    
将 APNs 证书上载到 Intune：
  
1. 在 Microsoft Intune 管理控制台选项卡，在**传 APNs 证书**页上单击**上载 APNs 证书**。
    
2. 单击**浏览**，然后指定**开发 test.pem**文件。
    
3. 单击**打开**，键入您的苹果 ID 帐户名，然后单击**上载**。**IOS 和 MaxOS X 移动设备管理组件安装程序**页上，您应该看到**准备注册**消息。
    
安装 APNs 证书后，Intune 现在则可以通过向已注册的移动设备推送政策来注册和管理 iOS 设备。
  
下载 Microsoft Intune 公司门户应用并注册 iOS 设备：
  
1. 在 iOS 设备中使用 Apple ID 登录。
    
2. 打开**苹果商店**应用程序。
    
3. 在搜索框中键入**intune**并点击**Microsoft Intune 公司门户网站**，**获取**，然后再**安装**。
    
4. 安装后，点击**打开**。
    
5. 在**Intune 公司门户**屏幕上，使用您 Office 365 的全局管理员帐户进行登录。
    
6. 在**公司访问安装程序**屏幕上，点击**开始**，然后点击**继续**两次。
    
7. 在**下来？**屏幕上，点击**注册**。
    
8. 在**激活设备管理员？**屏幕上，点击**激活**。
    
9. 在**管理配置文件**屏幕中，单击**安装**。
    
10. 在**输入密码**，键入 iOS 设备通行码。
    
11. 在**种下一**屏幕上，点击**注册**。
    
12. 在**安装配置文件**，点击**安装**。
    
13. 在**警告**页面中，点击**安装**。
    
14. 在**远程管理**，点击**信任**。
    
15. 点击**完成**以完成注册过程。
    
16. 当系统提示**打开此页面在"复合门户"？**，点击**打开**。
    
17. 在**公司访问安装程序**屏幕上，点击**开始**，，然后点击**完成**。
    
18. 会在 Microsoft Intune 公司门户应用的主屏幕中看到以下内容：
    
  - 绿色的横幅。
    
  - 虚构的公司名称位于左上方。
    
  - **我的设备**中列出您 iOS 设备名称。
    
  - 在**帮助台**部分， **User5**与**555-1234年**和按钮**通过电子邮件的联系人**的电话号码的**联系人姓名**。
    
Microsoft Intune 提供远程锁定和密码重置两种功能。如果有人丢失了自己的设备，则可以远程锁定设备。如果有人忘记了自己的密码，则可以远程删除密码。
  
远程锁定 iOS 设备：
  
1. 您管理的计算机，Microsoft Intune 管理控制台选项卡上的浏览器中，从左侧导航区域中单击**组**。
    
2. 在**组**窗格中，打开**所有设备 > 所有移动设备 > 所有直接受控设备**。
    
3. 在**所有直接受控设备**窗格中，单击**设备**选项卡。
    
4. 在设备列表中，单击自己的 iOS 设备。  
    
5. 在自己的 iOS 设备中，请确保其位于主屏幕上。  
    
6. 从管理计算机，在任务栏上，单击**远程任务 > 远程锁定**。切换锁定屏幕为 iOS 设备进行观察。
    
删除密码：
  
1. 从您的管理计算机的**所有直接受控设备**窗格中，单击**设备**选项卡。
    
2. 在列表中，单击您的 iOS 设备。在任务栏上，单击**远程任务 > 密码重置**。等待一分钟。
    
3. 从 iOS 设备，解除其锁定，请注意是不能再通行码。若要更改密码后，进入**设置**，然后再**通行码**。
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a>第 3 阶段（仅适用于 Android 设备）：注册并管理 Android 设备

若要注册 Android 设备以通过 Intune 进行管理，需要具备以下条件：
  
- 一台 Android 设备。
    
- 设备通行码的知识。
    
下载 Intune 公司门户应用并注册 Android 设备：
  
1. 从 Android 设备，转到**Google 播放存储**，然后点击**开始**。
    
2. 在搜索框中，键入**intune** ，然后点击**intune 公司门户网站**在搜索结果中。
    
3. 点击**Intune 公司门户**项目中，然后点击**安装**。
    
4. 在**完整的帐户安装程序**屏幕上，点击**继续**，然后选择**跳过**。
    
5. 在**Intune 公司门户网站**，点击**接受**。应用程序安装。
    
6. 点击**打开**，然后点击**登录**。
    
7. 在**Intune 公司门户**屏幕上，使用您 Office 365 的全局管理员帐户进行登录。
    
8. 在**公司访问安装程序**屏幕上，点击**开始**，然后**继续**两次。
    
9. 在**下来？**屏幕上，点击**注册**。
    
10. 在**激活设备管理员？**屏幕上，点击**激活。**
    
11. 在**隐私策略**屏幕中，选择**我确认**，然后点击**确认**。等待完成注册过程。
    
12. 在**公司访问安装程序**屏幕上，点击**继续**，，然后点击**完成**。
    
13. 在 Microsoft Intune 公司门户应用的主屏幕上，应该可以看到一个绿色的横幅和位于左上方的虚构的公司名称。
    
14. 请点击**我的设备**。您应该看到 Android 设备名称列表中。
    
15. 请点击**请联系 IT 部门**。您应该看到的电话号码是**555-1234年**，**联系通过电子邮件**的按钮，和它联系的**User5**。
    
Microsoft Intune 提供远程锁定和密码重置两种功能。如果有人丢失了自己的设备，则可以远程锁定设备。如果有人忘记了自己的密码，则可以远程重置密码。
  
远程锁定 Android 设备：
  
1. 您管理的计算机，Microsoft Intune 管理控制台选项卡上的浏览器中，从左侧导航区域中单击**组**。
    
2. 在**组**窗格中，打开**所有设备 > 所有移动设备 > 所有直接受控设备**。
    
3. 在**所有直接受控设备**窗格中，单击**设备**选项卡。
    
4. 在设备列表中，单击自己的 Android 设备。  
    
5. 在自己的 Android 设备中，请确保其位于主屏幕上。  
    
6. 从管理计算机，在任务栏上，单击**远程任务 > 远程锁定**。出现提示时，请单击**是**。
    
7. Android 设备切换到锁定屏幕时观察其变化。
    
当您重置密码的 Android 设备时，Intune 管理门户生成并配置一个强密码。
  
远程重置密码：
  
1. 从您的管理计算机，Microsoft Intune 管理控制台选项卡上的浏览器中，在**所有直接受控设备**窗格中，单击您的 Android 设备。
    
2. 在任务栏上，单击**远程任务 > 密码重置**。
    
3. 在**远程任务： 密码重置**提示下，单击**是**。等待一分钟。
    
4. 在**所有直接受控设备**窗格中，单击**查看属性**。
    
5. 在**密码重置**，记下新的密码。
    
6. 在自己的 Android 设备的锁屏中输入新密码。  
    
7. 若要更改密码后，进入**设置**、 点击**设备**，点击**锁定屏幕**、 密码中输入新的密码，点击**屏幕锁**，并选择。
    
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。
  
## <a name="see-also"></a>另请参阅

[Microsoft 365 企业开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[您的 Microsoft 365 企业开发/测试环境的 MAM 策略](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[企业移动 + 安全 (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


