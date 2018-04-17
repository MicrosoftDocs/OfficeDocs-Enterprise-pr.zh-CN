---
title: 保护 SharePoint Online 网站和文件
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: 摘要： 为保护 SharePoint Online Office 365 中的文件的配置建议。
ms.openlocfilehash: 800d81d657164b2a936b95764d57fd092cfa21cc
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="secure-sharepoint-online-sites-and-files"></a>保护 SharePoint Online 网站和文件

 **摘要：**为保护 SharePoint Online Office 365 中的文件的配置建议。
  
本文提供了有关配置 SharePoint Online 的工作组站点和平衡安全而且易于协作的文件保护的建议。本文定义了四种不同配置，最开放的共享策略与组织内的公用网站开始。每个其他配置表示一个有意义的步骤组成的保护，但能够访问和协作资源减少到相关集的用户。这些建议作为起点并调整配置以满足您组织的需要。 
  
本文中的配置符合 Microsoft 针对数据、标识和设备的三层保护的建议：
  
- 基线保护
    
- 敏感保护
    
- 高度机密保护
    
有关这些保护层以及针对每层建议的功能的详细信息，请参阅以下资源。 
  
- [Office 365 的标识和设备保护](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [Office 365 中的文件保护解决方案](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a>功能概述

针对各种 Office 365 功能的 SharePoint Online 团队网站绘制的建议。 对于高度机密的网站，建议使用 Azure 信息保护。 这包括在企业移动性 + 安全性 (EMS) 中。 
  
下图显示了四个 SharePoint Online 的团队站点的建议的配置。
  
![适用于 SharePoint 网站的推荐配置](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
如图所示：
  
- 基线保护包含针对 SharePoint Online 团队网站的两个选项 - 公共网站和专用网站。 组织中的任何人均可发现和访问公共网站。 只有网站成员可以发现和访问专用网站。 这两个网站配置均允许组外共享。 
    
- 敏感保护和高度机密的保护的网站是专用网站，只有特定组的成员才具有相关访问权限。
    
- Office 365 标签提供根据所需保护级别对数据进行分类的方法。 每个 SharePoint Online 团队网站均被配置为使用网站的默认标签自动标记文档库中的文件。 与四个网站配置相对应，此示例中的标签分别为内部公开、专用、敏感和高度机密。 用户可以更改标签，但此配置可确保所有文件均接收默认的标签。
    
- 为敏感和高度机密 Office 365 标签配置数据丢失防护 (DLP)，在其试图向组织外部发送这些类型的文件时警告或阻止用户。
    
- 对于配置有高度机密保护的网站，Azure 信息保护将对文件进行加密，并授予相应权限。
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a>SharePoint Online 和 OneDrive for Business 的租户范围内设置

SharePoint Online 和 OneDrive for Business 包括影响所有网站和用户的租户范围内设置。 其中一些设置也可在网站级别进行调整，使其更具有（而不是更不具有）限制性。 本部分讨论影响安全性和协作的租户范围内设置。 
  
### <a name="sharing"></a>共享

对于此解决方案，建议使用以下租户范围内设置：
  
- 保留允许所有与所有帐户类型共享（包括匿名共享）的默认共享策略。
    
- 如果需要，请将匿名链接设置为过期。
    
- 将共享的默认链接类型更改为“内部”。 这有助于防止数据意外泄露到组织外部。
    
虽然允许外部共享可能看起来有悖常理，但相较于通过电子邮件发送文件，此方法可更好地控制文件共享。 SharePoint Online 和 Outlook 彼此协作，提供安全的文件协作。 
  
- 默认情况下，Outlook 共享文件链接，而不是通过电子邮件发送文件。 
    
- SharePoint Online 和业务的 OneDrive 可以轻松与正在组织内外的参与者共享文件的链接
    
用户还可进行控制，帮助管理外部共享。 例如，你能够：
  
- 禁用匿名来宾链接。
    
- 撤销用户对网站的访问权限。
    
- 查看谁有权访问特定网站或文档。
    
- 将匿名共享链接设置为过期（租户设置）。
    
- 限制可与之共享的组织外部用户（租户设置）。
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a>配合使用外部共享与数据丢失预防 (DLP)

如果您不允许外部共享时，与业务用户需要了解备用工具和方法。Microsoft 建议您将合并外部共享与 DLP 策略来保护敏感和高度机密文件。
  
### <a name="device-access-settings"></a>设备访问设置

SharePoint Online 和 OneDrive 的业务设备访问设置使您可以确定是否限制为仅限于浏览器访问 （不能下载文件），或访问被阻止。这些设置目前在第一版，并且应用租户范围。即将是在站点级别配置设备访问策略的能力。对于本解决方案，建议不使用应用组织范围内的设备访问设置。
  
要使用处于首次发布状态的设备访问设置，请参阅：[在 Office 365 中设置标准发布或首次发布选项](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)。
  
### <a name="onedrive-for-business"></a>OneDrive for Business

访问这些设置，确定是否要更改 OneDrive for Business 网站的默认设置。 目前，共享和设备访问设置与 SharePoint Online 管理中心重复，并适用于这两个环境。
  
## <a name="sharepoint-team-site-configuration"></a>SharePoint 团队网站配置

下表总结了本文前面所述的每个团队网站的配置。 使用这些配置作为起点建议并调整网站类型和配置，以满足组织的需求。 不是每个组织都需要每种类型的网站。 只有少许组织需要高度机密的保护。
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**基线保护 #1** <br/> |**基线保护 #2** <br/> |**敏感保护** <br/> |**高度机密** <br/> |
|描述  <br/> |组织内的开放式发现和协作。  <br/> |允许在组外部共享的专用网站和组。  <br/> |独立网站，该网站中的访问级别由特定组中的成员身份进行定义。 仅允许网站成员进行共享。 DLP 在用户试图向组织外发送文件时警告用户。  <br/> |启用 Azure 信息保护的独立网站和文件及权限。 DLP 阻止用户向组织外发送文件。  <br/> |
|专用或公用团队网站  <br/> |公用  <br/> |Private  <br/> |Private  <br/> |Private  <br/> |
|谁可以访问？  <br/> |组织中的任何人，包括 B2B 用户和来宾用户。  <br/> |仅限网站成员。 其他人可以请求访问。  <br/> |仅限网站成员。 其他人可以请求访问。  <br/> |仅限成员。 其他人无法请求访问。  <br/> |
|网站级共享控制  <br/> |允许与任何人共享。 默认设置。  <br/> |允许与任何人共享。 默认设置。  <br/> |成员无法共享对网站的访问权限。  <br/> 非成员可以请求访问该网站，但需要由网站管理员对这些请求进行寻址。  <br/> |成员无法共享对网站的访问权限。  <br/> 非成员无法请求访问网站或内容。  <br/> |
|网站级别的设备访问控制  <br/> |无任何额外控制。  <br/> |无任何额外控制。  <br/> |即将推出网站级别控制，可防止用户将文件下载到不符合或未加入域的设备。 使所有其他设备仅限浏览器访问。  <br/> |即将推出网站级别控制，可阻止将文件下载到不符合或未加入域的设备。  <br/> |
|Office 365 标签  <br/> |内部公用  <br/> |Private  <br/> |敏感  <br/> |高度机密  <br/> |
|DLP 策略  <br/> |||在用户向组织外发送标记为“敏感”的文件时进行警告。  <br/> 要阻止外部共享敏感数据类型，如信用卡号或其他个人数据，可以针对这些数据类型（包括所配置的自定义数据类型）配置其他 DLP 策略。  <br/> |阻止用户向组织外发送标记为“高度机密”的文件。 允许用户通过提供他们与之共享的对象等理由来替代此行为。  <br/> |
|Azure 信息保护  <br/> ||||使用 Azure 信息保护自动加密并授予其权限的文件。它们泄漏的情况下，这种保护传输的文件。  <br/> Office 365 无法读取使用 Azure 信息保护加密的文件。此外，DLP 策略只能处理的元数据 （包括标签），但不是包括这些文件 （例如，信用卡号文件内） 的内容。  <br/> |
   
若要部署此解决方案中的 SharePoint Online 小组站点的四种不同类型的步骤，请参阅[部署 SharePoint Online 网站的三个层次的保护](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)。创建开发/测试环境的步骤，请参阅[安全 SharePoint Online 网站的开发/测试环境](secure-sharepoint-online-sites-in-a-dev-test-environment.md)。 
  
## <a name="office-365-classification-and-labels"></a>Office 365 分类和标签

环境中的敏感数据，建议使用 Office 365 标签。在您配置和发布 Office 365 标签：
  
- 可以应用于在线 SharePoint 的工作组网站中的文档库的默认标签以便该库中的所有文档的默认标签。 
    
- 您可以将标签应用于内容自动匹配特定条件。
    
- 您可以应用基于 Office 365 提供标签的 DLP 策略。
    
- 您组织中的人员可以应用标签手动内容在 web 上的 Outlook 中 2010年及更高版本的 Outlook，OneDrive 业务、 SharePoint Online 和 Office 365 的组。用户通常非常清楚地知道什么类型的内容他们正在使用，因此可以对其进行分类和应用适当的 DLP 策略。
    
![适用于 SharePoint 网站的推荐配置](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
如图所示，此解决方案包括创建以下标签：
  
- 高度机密
    
- 敏感
    
- Private
    
- 内部公用
    
这些标签映射到图中的推荐的网站和本文中前面的图表。本解决方案建议配置 DLP 策略有助于防止文件标记为敏感和高度机密的泄露。
  
有关如何配置此解决方案中的 Office 365 标签和 DLP 策略的步骤，请参阅[使用 Office 365 标签和 DLP 保护 SharePoint Online 文件](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)。
  
## <a name="azure-information-protection"></a>Azure 信息保护

使用 Azure 信息保护应用标签和与文件如影随形的保护。 对于此解决方案，建议使用作用域内 Azure 信息保护策略和“高度机密”标签的子标签来加密需要最高级别安全性保护的文件并授予相应权限。 
  
请注意，将 Azure 信息保护加密应用于 Office 365 中存储的文件时，该服务无法处理这些文件的内容。 共同创作、电子数据展示、搜索、Delve 和其他协作功能将无法正常使用。 DLP 策略只适用于元数据（包括 Office 365 标签），但并不适用于这些文件的内容（如文件内的信用卡号）。
  
![Azure 信息保护是在 Azure 中进行配置，标签显示在客户端工具栏中](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
如图所示：
  
- 在 Microsoft Azure 门户配置了 Azure 的信息保护策略和标签。建议配置的指定了作用域的 Azure 的信息保护策略的子标签。
    
- Azure 的信息保护标签显示了作为 Office 应用程序中的**信息保护**栏。
    
### <a name="adding-permissions-for-external-users"></a>添加外部用户的权限

有两种方法可以授予外部用户访问 Azure 的信息保护受保护的文件。在这两个这种情况下，外部用户必须拥有 Azure 的广告帐户。如果外部用户不能使用 Azure AD 的组织的成员，他们可以获取的 Azure 的广告帐户作为个人利用该注册页面： [https://aka.ms/aip-signup](https://aka.ms/aip-signup)。
  
- 将外部用户添加到用于配置的标签保护 Azure AD 组
    
     您将需要首先为您的目录中的 B2B 用户添加帐户。它可以需要几个小时的[组成员身份缓存的 Azure 权限管理](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management)。使用此方法，将权限授予设有标签 （即使文件保护到 Azure AD 组添加用户之前） 的所有现有文件。
    
- 外部用户将直接添加到标签保护
    
     可以从组织 (例如 Fabrikam.com)，（例如组织内部财务组） Azure AD 组或单个用户添加的所有用户。例如，您可以添加标签保护外部团队的管理机构。使用此方法，只对外部实体添加到保护后，保护带标签的文件授予权限。
    
### <a name="deploying-and-using-azure-information-protection"></a>部署并使用 Azure 信息保护

有关配置此解决方案中的 Azure 信息保护的步骤，请参阅[使用 Azure 信息保护来保护 SharePoint Online 文件](protect-sharepoint-online-files-with-azure-information-protection.md)。
  
## <a name="see-also"></a>另请参阅

[Microsoft 针对政治宣传活动、非营利组织和其他敏捷性组织的安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[安全解决方案](security-solutions.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
  
[开发/测试环境中保护 SharePoint Online 站点](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



