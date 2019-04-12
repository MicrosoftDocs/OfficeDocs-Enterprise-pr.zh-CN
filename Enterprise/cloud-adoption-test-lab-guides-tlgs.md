---
title: 使用云应用测试实验室指南 (TLG) 测试 Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/09/2019
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 摘要：使用这些云应用测试实验室指南 (TLG) 设置演示、概念证明或 Office 365 的开发/测试环境。
ms.openlocfilehash: 3531a3185cd52044ee59391d676fff1a7f4a5f64
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741168"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a>使用云应用测试实验室指南 (TLG) 测试 Office 365

 **摘要：** 使用这些云应用测试实验室指南 (TLG) 设置演示、概念证明或 Office 365 的开发/测试环境。
  
TLG 可帮助你快速了解 Microsoft 产品。当你需要先评估某种技术或配置，然后再决定它是否适合你并开始设计、规划和将其推广给用户时，这些指南非常有用。“我自己构建，它可运行”的亲身体验有助于了解新产品或解决方案的部署需求，以便更好地规划将其托管在生产中。
  
TLG 还允许你创建用于开发和测试应用程序的代表性环境，也称为开发/测试环境。
  
![Microsoft 云中的测试实验室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
单击[此处](http://aka.ms/catlgstack)可直观映射到 Office 365 测试实验室指南堆栈中的所有文章。
    
## <a name="office-365-devtest-environment"></a>Office 365 开发/测试环境

使用这些文章构建 Office 365 开发/测试环境：
  
- [基础配置开发/测试环境](base-configuration-dev-test-environment.md)
    
    创建在 Microsoft Azure 基础结构服务中运行的简化的 Intranet。如要生成模拟的企业配置，此为可选步骤。
    
- [Office 365 开发/测试环境](office-365-dev-test-environment.md)
    
    创建 Office 365 企业版 E5 试用订阅，可从计算机或从 Azure 基础结构服务中运行的简化 Intranet 执行此操作。
    
- [用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
    
    安装并配置 Azure AD Connect，以便通过密码哈希同步来实现目录同步。如要生成模拟的企业配置，此为可选步骤。
    
针对你的 Office 365 开发/测试环境，可使用这些文章来演示 Office 365 的企业功能：
  
- [Office 365 开发/测试环境的多重身份验证](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    使用发送到智能手机的短信，为 Office 365 订阅中的帐户配置和测试辅助身份验证。
    
- [用于 Office 365 开发/测试环境的联合身份](federated-identity-for-your-office-365-dev-test-environment.md)
    
    使用 Active Directory 域服务 (AD DS) 域帐户配置并演示联合身份验证。
    
- [用于 Office 365 开发/测试环境的云应用安全](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    通过配置和演示 Office 365 云应用安全，用户可以创建策略来监视 Office 365 订阅中的可疑活动并发送通知。
    
- [Office 365 开发/测试环境中的高级威胁防护](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    配置和演示高级威胁防护是 Exchange Online Protection (EOP) 的一种功能，可帮助电子邮件阻止恶意软件。
    
- [用于 Office 365 开发/测试环境的高级电子数据展示](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    通过添加示例数据并演示高级电子数据展示，用户可以快速查找并分析 Office 365 中所存储的数据（包括电子邮件和文档）。
    
- [Office 365 开发/测试环境中的敏感文件保护](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    演示如何使用 Office 365 信息权限管理保护敏感文档中的数据，即便不小心张贴在错误的文档文件夹中。
    
- [Office 365 开发/测试环境中的数据分类和标记](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    演示如何使用 Azure 信息保护客户端对具有不同安全级别的文档进行分类。
    
- [独立的 SharePoint Online 团队网站开发/测试环境](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    演示如何创建因敏感或高度机密资源而与组织其他部分隔离的 SharePoint Online 团队网站。
    

## <a name="simulated-cross-premises-devtest-environments"></a>模拟的跨界开发/测试环境

可以参阅以下文章来创建跨界开发/测试环境，其中包括 Azure 虚拟网络和模拟的本地网络：
  
- [Azure 中的模拟跨界虚拟网络](simulated-cross-premises-virtual-network-in-azure.md)
    
    在混合云配置中创建连接 Azure 虚拟网络的模拟 Intranet。
    
- [Azure 开发/测试环境中的 Intranet SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    在 Azure 虚拟网络中创建单个服务器的 SharePoint Server 2016 场，并从模拟的本地网络测试连接性和管理。
    
## <a name="sharepoint-server-2016-devtest-environments"></a>SharePoint Server 2016 开发/测试环境

以下是你可以在 Azure 基础结构服务中创建的 SharePoint Server 2016 开发/测试环境：
  
- [Azure 中的 SharePoint Server 2016 开发/测试环境](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)
    
    在 Azure 基础结构服务中生成单个服务器的 SharePoint Server 2016 场。

- [Azure 开发/测试环境中的 Intranet SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)
    
    在 Azure 基础结构服务中生成单个服务器的 SharePoint Server 2016 场，并从模拟的 Intranet 访问它。


## <a name="the-microsoft-365-enterprise-devtest-environments"></a>Microsoft 365 企业版开发/测试环境

使用[这些文章](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)创建适用于 [Microsoft 365 企业版](https://docs.microsoft.com/microsoft-365-enterprise/)的开发/测试环境。  
    
## <a name="see-also"></a>另请参阅

[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)
  
[SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[混合解决方案](hybrid-solutions.md)
