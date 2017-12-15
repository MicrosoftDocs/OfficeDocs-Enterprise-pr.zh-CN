---
title: "云采用测试实验室指南 (TLG)"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: "摘要： 使用这些云采用测试实验室指南 (TLGs) 设置的演示中，证据的概念或开发/测试环境为 Office 365、 企业移动性 + 安全性 (EMS)、 Dynamics 365 办公室服务器产品。"
ms.openlocfilehash: 532215a08e28a9d67cd19ef60d60419b06df4957
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="cloud-adoption-test-lab-guides-tlgs"></a>云采用测试实验室指南 (TLG)

 **摘要：**这些云采用测试实验室指南 (TLGs) 用于设置演示，证明的概念或开发/测试环境为 Office 365、 企业移动性 + 安全性 (EMS)、 Dynamics 365 办公室服务器产品。
  
TLGs 可帮助您快速了解有关 Microsoft 产品。它们非常的情况下，您需要决定它是否为您或您推出它给用户之前右前评估技术或配置。"构建出自己和它的工作原理"的亲身体验可以帮助您了解新产品或解决方案的部署要求，因此您可以更好地规划其生产环境中承载。
  
TLG 还允许你创建用于开发和测试应用程序的代表性环境，也称为开发/测试环境。
  
![Microsoft 云中的测试实验室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
在深入探查前参阅以下这些附加资源：
  
- 查看[Microsoft 云与云采用测试实验室指南体验](https://mva.microsoft.com/en-US/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881 )Microsoft 虚拟学院会话 （仅 22 分钟）。
    
- 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。
    
## <a name="office-365-devtest-environment"></a>Office 365 开发/测试环境
<a name="O365"> </a>

使用这些文章构建 Office 365 开发/测试环境：
  
- [基础配置开发/测试环境](base-configuration-dev-test-environment.md)
    
    创建在 Microsoft Azure 基础结构服务中运行的简化的 Intranet。如要生成模拟的企业配置，此为可选步骤。
    
- [Office 365 开发/测试环境](office-365-dev-test-environment.md)
    
    创建 Office 365 企业 E5 试用订阅，您从您的计算机或运行在 Azure 的基础结构服务的简化内部网可以做到这一点。
    
- [用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
    
    安装并配置 Azure AD Connect，以便通过密码同步来实现目录同步。如要生成模拟的企业配置，此为可选步骤。
    
对于 Office 365 开发/测试环境中，使用这些文章来说明企业功能的 Office 365:
  
- [您的 Office 365 开发/测试环境的的多因素身份验证](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    使用发送到智能手机的短信为 Office 365 订阅中的帐户配置和测试辅助身份验证。
    
- [用于 Office 365 开发/测试环境的联合身份](federated-identity-for-your-office-365-dev-test-environment.md)
    
    使用 Windows Server Active Directory 域帐户配置并演示联合身份验证。
    
- [Office 365 开发/测试环境的云应用程序安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    配置并演示 Office 365 云应用程序安全性，以便您可以创建用于监视和通知您在您的 Office 365 订阅的可疑活动的策略。
    
- [为您的 Office 365 开发/测试环境高级威胁防护](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    配置和演示高级威胁防护是一种 Exchange Online Protection (EOP) 功能，可帮助电子邮件阻止恶意软件。
    
- [高级的 eDiscovery 您 Office 365 的开发/测试环境](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    添加示例数据并演示高级电子数据展示以支持快速查找并分析 Office 365 中所存储的数据（包括电子邮件和文档）。
    
- [在 Office 365 的开发/测试环境中的敏感文件保护](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    演示如何使用 Office 365 信息权限管理保护敏感文档中的数据，即便不小心张贴在错误的文档文件夹中。
    
- [数据分类和标记在 Office 365 的开发/测试环境](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    演示如何使用 Azure 信息保护 (AIP) 客户端进行分类具有各种安全级别的文档。
    
- [SharePoint Online 的团队站点开发/测试环境的独立](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    演示如何创建独立于敏感或高度机密的资源组织中的其余的 SharePoint Online 工作组网站。
    
## <a name="the-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 企业开发/测试环境
<a name="O365"> </a>

使用这些文章创建用于[Microsoft 365 企业](https://docs.microsoft.com/microsoft-365-enterprise/)方案的开发/测试环境：
  
- [Microsoft 365 企业开发/测试环境](the-microsoft-365-enterprise-dev-test-environment.md)
    
    创建初始环境，包括 Office 365 E5、 EMS E5 和计算机运行 Windows 10 企业。
    
- [您的 Microsoft 365 企业开发/测试环境的 MAM 策略](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
    创建适用于 iOS 和 Android 设备的用户组和移动应用程序管理 (MAM) 策略。
    
- [IOS 和 Android 设备在 Microsoft 企业 365 开发/测试环境中注册](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
    
    注册 iOS 或 Android 设备，并对其进行远程管理。
    
## <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 和 Dynamics 365 开发/测试环境
<a name="O365_D365"> </a>

使用以下文章添加 Dynamics 365 试用订阅并测试 Office 365 和 Dynamics 365 的集成功能和方案：
  
- [Office 365 和 Dynamics 365 开发/测试环境](office-365-and-dynamics-365-dev-test-environment.md)
    
    将 Dynamics 365 试用订阅、 Dynamics 365 许可证和相关权限添加到用户帐户。
    
- [Office 365 和 Dynamics 365 开发/测试环境的 Exchange 联机集成](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)
    
    配置，然后演示 Office 365 和 Dynamics 365 如何协作在 Exchange 在线邮箱。
    
## <a name="the-one-microsoft-cloud-devtest-environment"></a>一个 Microsoft 云开发/测试环境
<a name="O365_D365"> </a>

创建包含所有微软云产品开发/测试环境： Office 365、 Azure、 EMS 和 Dynamics 365。[一个 Microsoft 云开发/测试环境](the-one-microsoft-cloud-dev-test-environment.md)的分步说明，请参见
  
## <a name="simulated-cross-premises-devtest-environments"></a>模拟的跨界开发/测试环境
<a name="O365_D365"> </a>

可以参阅以下文章来创建跨界开发/测试环境，其中包括 Azure 虚拟网络和模拟的本地网络：
  
- [在 Azure 中模拟的跨部署虚拟网络](simulated-cross-premises-virtual-network-in-azure.md)
    
    创建连接到混合云配置中的 Azure 虚拟网络的模拟内部网。
    
- [在 Azure 开发/测试环境中的 intranet SharePoint 服务器 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    在 Azure 虚拟网络中创建单个服务器 SharePoint Server 2016 场，并从模拟的本地网络测试连接性和管理。
    
## <a name="additional-cloud-based-devtest-environments"></a>其他基于云的开发/测试环境
<a name="ADD_TLGs"> </a>

以下是你可以在 Azure 基础结构服务中创建的其他基于云的开发/测试环境：
  
- [在 Azure 中的 SharePoint 服务器 2016年开发/测试环境](https://technet.microsoft.com/library/mt723354.aspx)
    
    在 Azure 基础结构服务中生成单个服务器 SharePoint Server 2016 场。
    
- [在 Azure 中的交换 2016年开发/测试环境](https://technet.microsoft.com/library/mt733070%28v=exchg.160%29.aspx)
    
    在 Azure 的基础结构服务中，构建单个Exchange 2016 服务器。
    
- [在 Azure 中的 SharePoint Server 2013 开发/测试环境](http://technet.microsoft.com/library/165de4d5-8fe6-4fbb-a15b-39a8b0a0eb23.aspx)
    
    在 Azure 基础结构服务中生成基本和高可用性 SharePoint Server 2013 场。
    
**参加讨论**

|**联系我们**|**说明**|
|:-----|:-----|
|**您需要什么样的解决方案？** <br/> |我们正在为跨多个 Microsoft 产品和服务的解决方案创建内容。请告诉我们您对我们的跨服务器解决方案的想法，或者发送电子邮件到 [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) 寻求具体的解决方案。<br/> |
|**参加解决方案讨论** <br/> |如果您热衷于基于云的解决方案，请考虑加入云采用咨询委员会 (CAAB) 进行连接的 Microsoft 内容开发人员，业内专业人士和来自全球各地的客户更大的、 充满活力的社区。加入，将自己添加为 Microsoft 技术社区的[空间 CAAB （云采用咨询委员会）](https://aka.ms/caab)的成员，向我们发送快速电子邮件在[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)。任何人都可以读取与团体相关的内容，在[CAAB 博客](https://blogs.technet.com/b/solutions_advisory_board/)上。但是，CAAB 成员获取描述新的云应用资源和解决方案的专用网络研讨会的邀请。<br/> |
|**获取您在此处看到的图片** <br/> |如果您希望您在这篇文章中看到的画的可编辑副本，我们将很高兴地向您发送它。通过电子邮件发送您的请求，包括 URL 和[cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)的图片，标题。<br/> |
   
## <a name="see-also"></a>See Also

<a name="ADD_TLGs"> </a>

[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)
  
[SharePoint、 交换、 业务、 和 Lync Skype 的体系结构模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[混合解决方案](hybrid-solutions.md)


