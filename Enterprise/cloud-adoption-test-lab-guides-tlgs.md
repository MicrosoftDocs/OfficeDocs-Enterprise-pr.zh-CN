---
title: 云应用测试实验室指南 (TLG)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 摘要：使用这些云应用测试实验室指南 (TLG) 设置演示、概念证明或 Office 365、企业移动性 + 安全性 (EMS)、Dynamics 365 和 Office Server 产品的开发/测试环境。
ms.openlocfilehash: 1ca74f7fdb83cf730c4f6d003c9f9e325299f33d
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2018
ms.locfileid: "19193672"
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a>云应用测试实验室指南 (TLG)

 **摘要：** 使用这些云应用测试实验室指南 (TLG) 设置演示、概念证明或 Office 365、企业移动性 + 安全性 (EMS)、Dynamics 365 和 Office Server 产品的开发/测试环境。
  
TLG 可帮助你快速了解 Microsoft 产品。当你需要先评估某种技术或配置，然后再决定它是否适合你或将其推广给用户时，这些指南非常有用。“我自己构建，它可运行”的亲身体验有助于了解新产品或解决方案的部署需求，以便更好地规划将其托管在生产中。
  
TLG 还允许你创建用于开发和测试应用程序的代表性环境，也称为开发/测试环境。
  
![Microsoft 云中的测试实验室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
深入了解前请参阅其他资源：
  
- 观看 Microsoft Virtual Academy 教程（仅 22 分钟）- [使用云应用测试实验室指南体验 Microsoft 云](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 )。
    
- 单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。
    
## <a name="office-365-devtest-environment"></a>Office 365 开发/测试环境

使用这些文章构建 Office 365 开发/测试环境：
  
- [基础配置开发/测试环境](base-configuration-dev-test-environment.md)
    
    创建在 Microsoft Azure 基础结构服务中运行的简化的 Intranet。如要生成模拟的企业配置，此为可选步骤。
    
- [Office 365 开发/测试环境](office-365-dev-test-environment.md)
    
    创建 Office 365 企业版 E5 试用订阅，可从计算机或从 Azure 基础结构服务中运行的简化 Intranet 执行此操作。
    
- [用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
    
    安装并配置 Azure AD Connect，以便通过密码同步来实现目录同步。如要生成模拟的企业配置，此为可选步骤。
    
针对你的 Office 365 开发/测试环境，可使用这些文章来演示 Office 365 的企业功能：
  
- [用于 Office 365 开发/测试环境的多重身份验证](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    使用发送到智能手机的短信，为 Office 365 订阅中的帐户配置和测试辅助身份验证。
    
- [用于 Office 365 开发/测试环境的联合身份](federated-identity-for-your-office-365-dev-test-environment.md)
    
    使用 Windows Server Active Directory 域帐户配置并演示联合身份验证。
    
- [用于 Office 365 开发/测试环境的云应用安全](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    通过配置和演示 Office 365 云应用安全，你可以创建策略来监视 Office 365 订阅中的可疑活动并发送通知。
    
- [Office 365 开发/测试环境中的高级威胁防护](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    配置和演示高级威胁防护是 Exchange Online Protection (EOP) 的一种功能，可帮助电子邮件阻止恶意软件。
    
- [用于 Office 365 开发/测试环境的高级电子数据展示](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    添加示例数据并演示高级电子数据展示以支持快速查找并分析 Office 365 中所存储的数据（包括电子邮件和文档）。
    
- [Office 365 开发/测试环境中的敏感文件保护](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    演示如何使用 Office 365 信息权限管理保护敏感文档中的数据，即便不小心张贴在错误的文档文件夹中。
    
- [Office 365 开发/测试环境中的数据分类和标记](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    演示如何使用 Azure 信息保护客户端 (AIP) 对具有不同安全级别的文档进行分类。
    
- [独立的 SharePoint Online 团队网站开发/测试环境](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    演示如何创建因敏感或高度机密资源而与组织其他部分隔离的 SharePoint Online 团队网站。
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 企业版开发/测试环境

使用以下文章创建适用于 [Microsoft 365 企业版](https://docs.microsoft.com/microsoft-365-enterprise/)方案的开发/测试环境：
  
- [Microsoft 365 企业版开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)
    
    创建包括 Office 365 E5、EMS E5 和运行 Windows 10 企业版的计算机的初始环境。
    
- [用于 Microsoft 365 企业版开发/测试环境的 MAM 策略](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    创建适用于 iOS 和 Android 设备的用户组和移动应用程序管理 (MAM) 策略。
    
- [在 Microsoft 企业版 365 开发/测试环境中注册 iOS 和 Android 设备](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    注册 iOS 或 Android 设备，并对其进行远程管理。
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 和 Dynamics 365 开发/测试环境

使用以下文章添加 Dynamics 365 试用订阅并测试 Office 365 和 Dynamics 365 的集成功能和应用场景：
  
- [Office 365 和 Dynamics 365 开发/测试环境](office-365-and-dynamics-365-dev-test-environment.md)
    
    将 Dynamics 365 试用订阅、Dynamics 365 许可证和相关权限添加到用户帐户。
    
- [Office 365 和 Dynamics 365 开发/测试环境的 Exchange Online 集成](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    配置然后演示 Office 365 和 Dynamics 365 如何在 Exchange Online 邮箱中协作。
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>One Microsoft 云开发/测试环境

创建包括所有 Microsoft 云产品/服务的开发/测试环境：Office 365、Azure、EMS 和 Dynamics 365。有关分步说明，请参阅 [One Microsoft 云开发/测试环境](the-one-microsoft-cloud-dev-test-environment.md)。
  
## <a name="simulated-cross-premises-devtest-environments"></a>模拟的跨界开发/测试环境

可以参阅以下文章来创建跨界开发/测试环境，其中包括 Azure 虚拟网络和模拟的本地网络：
  
- [Azure 中的模拟跨界虚拟网络](simulated-cross-premises-virtual-network-in-azure.md)
    
    在混合云配置中创建连接 Azure 虚拟网络的模拟 Intranet。
    
- [Azure 开发/测试环境中的 Intranet SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    在 Azure 虚拟网络中创建单个服务器的 SharePoint Server 2016 场，并从模拟的本地网络测试连接性和管理。
    
## <a name="additional-cloud-based-devtest-environments"></a>其他基于云的开发/测试环境

以下是你可以在 Azure 基础结构服务中创建的其他基于云的开发/测试环境：
  
- [Azure 中的 SharePoint Server 2016 开发/测试环境](https://technet.microsoft.com/library/mt723354.aspx)
    
    在 Azure 基础结构服务中生成单个服务器的 SharePoint Server 2016 场。
    
- [Azure 中的 Exchange 2016 开发/测试环境](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    在 Azure 基础结构服务中构建单个 Exchange 2016 服务器。
    
- [Azure 中的 SharePoint Server 2013 开发/测试环境](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    在 Azure 基础结构服务中构建基本和高可用性 SharePoint Server 2013 场。
    
**加入讨论**

|**联系我们**|**说明**|
|:-----|:-----|
|**你需要什么样的解决方案？** <br/> |我们正在为跨多个 Microsoft 产品和服务的解决方案创建内容。请告诉我们你对我们的跨服务器解决方案的想法，或者发送电子邮件到 [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) 寻求具体的解决方案。<br/> |
|**参加解决方案讨论** <br/> |如果热衷于基于云的解决方案，请考虑加入云采用咨询委员会 (CAAB)，以便与充满活力的更大规模社区保持联络，其中包括 Microsoft 内容开发人员、行业专家和全球各地的客户。若要加入，请将自己添加为 Microsoft 技术社区的[云采用咨询委员会 (CAAB) 空间](https://aka.ms/caab)成员，并向我们 ([CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)) 发送电子邮件。任何人都可以阅读 [CAAB 博客](https://blogs.technet.com/b/solutions_advisory_board/)上与社区相关的内容。不过，CAAB 成员可获邀参加私人网络研讨会，了解新云采用资源和解决方案。<br/> |
|**获取您在此处看到的图片** <br/> |若要获取本文中图片的可编辑副本，请告诉我们，我们非常乐意发送副本。请通过电子邮件方式将请求（包括图片的 URL 和标题）发送到 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)。<br/> |
   
## <a name="see-also"></a>另请参阅

<a name="ADD_TLGs"> </a>

[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)
  
[SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[混合解决方案](hybrid-solutions.md)


