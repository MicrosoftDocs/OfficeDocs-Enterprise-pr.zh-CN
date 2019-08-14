---
title: 使用测试实验室指南 (TLG) 测试 Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
audience: ITPro
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
description: 摘要：使用这些测试实验室指南 (TLG) 设置演示、概念证明或 Office 365 的开发/测试环境。
ms.openlocfilehash: 32675683846789f1e7be0e398e5b140d25d7ba80
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302734"
---
# <a name="test-office-365-with-test-lab-guides-tlgs"></a>使用测试实验室指南 (TLG) 测试 Office 365

 **摘要：** 使用这些文章设置演示、概念证明或 Office 365 的开发/测试环境。
  
TLG 可帮助你快速了解 Microsoft 产品。当你需要先评估某种技术或配置，然后再决定它是否适合你并开始设计、规划和将其推广给用户时，这些指南非常有用。“我自己构建，它可运行”的亲身体验有助于了解新产品或解决方案的部署需求，以便更好地规划将其托管在生产中。
  
TLG 还允许你创建用于开发和测试应用程序的代表性环境，也称为开发/测试环境。
  
![Microsoft 云中的测试实验室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
## <a name="office-365-devtest-environment"></a>Office 365 开发/测试环境

使用这些文章构建 Office 365 开发/测试环境：
  
- [基础配置开发/测试环境](base-configuration-dev-test-environment.md)
    
    创建在 Microsoft Azure 基础结构服务中运行的简化的 Intranet。如要生成模拟的企业配置，此为可选步骤。
    
- [Office 365 开发/测试环境](office-365-dev-test-environment.md)
    
    创建 Office 365 企业版 E5 试用订阅，可从计算机或从 Azure 基础结构服务中运行的简化 Intranet 执行此操作。
    
- [目录同步](dirsync-for-your-office-365-dev-test-environment.md)
    
    安装并配置 Azure AD Connect，以便通过密码哈希同步来实现目录同步。如要生成模拟的企业配置，此为可选步骤。
    
针对你的 Office 365 开发/测试环境，可使用这些文章来演示 Office 365 的企业功能：
  
- [多重身份验证](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    使用发送到智能手机的短信，为 Office 365 订阅中的帐户配置和测试辅助身份验证。
    
- [联合标识](federated-identity-for-your-office-365-dev-test-environment.md)
    
    使用 Active Directory 域服务 (AD DS) 域帐户配置并演示联合身份验证。
    
- [高级威胁防护](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    配置和演示高级威胁防护是 Exchange Online Protection (EOP) 的一种功能，可帮助电子邮件阻止恶意软件。

## <a name="simulated-cross-premises-devtest-environment"></a>模拟的跨界开发/测试环境

在混合云配置中创建连接 Azure 虚拟网络的[模拟 Intranet](simulated-cross-premises-virtual-network-in-azure.md)。
    
## <a name="sharepoint-server-2016-devtest-environment"></a>SharePoint Server 2016 开发/测试环境

在 Azure 基础结构服务中生成[单个服务器的 SharePoint Server 2016 场](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)。

## <a name="microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 企业版开发/测试环境

创建 [Microsoft 365 企业版](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)开发/测试环境。  
    
## <a name="see-also"></a>另请参阅

[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)
  
[SharePoint、Exchange、Skype for Business 和 Lync 的体系结构模型](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[混合解决方案](hybrid-solutions.md)
