---
title: "SharePoint Online 网站和文件保护"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: "摘要： 为保护 SharePoint Online Office 365 中的文件的配置建议。"
ms.openlocfilehash: 336dd4114e7853319fede88f9f3ea5aa613b2081
ms.sourcegitcommit: 4a347cfb16405d5213b28f332d80e244fca0fb8f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/18/2017
---
# <a name="secure-sharepoint-online-sites-and-files"></a>SharePoint Online 网站和文件保护

 **摘要：**为保护 SharePoint Online Office 365 中的文件的配置建议。
  
本文提供了有关配置 SharePoint Online 的工作组站点和平衡安全而且易于协作的文件保护的建议。本文定义了四种不同配置，最开放的共享策略与组织内的公用网站开始。每个其他配置表示一个有意义的步骤组成的保护，但能够访问和协作资源减少到相关集的用户。这些建议作为起点并调整配置以满足您组织的需要。 
  
这篇文章中的配置符合 Microsoft 对三个层次的数据、 身份和设备的保护的建议：
  
- 基线的保护
    
- 写保护
    
- 高度机密的保护
    
有关这些层和建议的每一层的功能的详细信息，请参阅以下资源。 
  
- [标识和 Office 365 的设备保护](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [Office 365 中的文件保护解决方案](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a>功能概述

SharePoint Online 团队站点的建议依靠各种 Office 365 提供功能。对于高度机密的站点，建议使用 Azure 的信息保护。这将包括在企业移动 + 安全 (EMS)。 
  
下图显示了四个 SharePoint Online 的团队站点的建议的配置。
  
![适用于 SharePoint 网站的推荐配置](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
图所示：
  
- 基线保护包括 SharePoint Online 团队站点的两个选项 — — 一个公共站点和专用站点。公共网站可以发现，并由组织中的任何人访问。只能发现和访问网站的成员的专用网站。同时这些站点配置允许共享组之外。 
    
- 敏感和高度机密保护的站点都是与访问仅限于特定组的成员的专用站点。
    
- Office 365 标签提供所需的保护级别的数据进行分类的方法。每个 SharePoint Online 的团队站点都配置为自动标签文件与默认标签的文档库中的网站。对应于四个站点配置，在此示例中的标志是内部公共、 私人、 敏感、 和高度机密。用户可以更改的标签，但这种配置可确保所有文件都获得一个默认标签。
    
- 数据丢失防护 (DLP) 策略配置的敏感和高度机密的 Office 365 的标签警告或阻止用户在尝试发送这些类型的组织外部文件时。
    
- 对于站点配置了高度机密的保护，Azure 信息保护进行加密和授予权限的文件。
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a>SharePoint Online 和业务的 OneDrive 的租户范围设置

SharePoint Online 和业务的 OneDrive 包括租户范围影响到所有站点和用户的设置。其中的某些设置也可以在网站级别为限制性更强 （但不是更少） 来调整。本部分讨论了影响安全和协作的租户范围设置。 
  
### <a name="sharing"></a>共享

对于本解决方案，我们建议以下的租户范围设置：
  
- 保持默认的共享策略，允许与所有帐户类型，包括匿名共享的所有共享。
    
- 如果需要，请设置过期，匿名的链接。
    
- 更改到内部共享的默认链接类型。这有助于防止数据意外泄漏，在您的组织之外。
    
虽然这可能看起来有悖常理，允许外部共享，这种方法提供了更好地控制文件共享到电子邮件中发送的文件进行比较。SharePoint Online 和 Outlook 协同工作以提供关于文件的安全协作。 
  
- 默认情况下，Outlook 共享文件，而是通过电子邮件发送该文件的链接。 
    
- SharePoint Online 和业务的 OneDrive 可以轻松与正在组织内外的参与者共享文件的链接
    
您还可以控制可帮助管理外部共享。例如，您可以：
  
- 禁用匿名来宾链接。
    
- 吊销用户对站点的访问。
    
- 谁有权访问特定的网站或文档，请参阅。
    
- 设置匿名共享链接过期 （租户设置）。
    
- 可以共享外部组织 （租户设置） 的限制。
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a>使用外部数据丢失防护 (DLP) 和共享

如果您不允许外部共享时，与业务用户需要了解备用工具和方法。Microsoft 建议您将合并外部共享与 DLP 策略来保护敏感和高度机密文件。
  
### <a name="device-access-settings"></a>设备访问设置

SharePoint Online 和 OneDrive 的业务设备访问设置使您可以确定是否限制为仅限于浏览器访问 （不能下载文件），或访问被阻止。这些设置目前在第一版，并且应用租户范围。即将是在站点级别配置设备访问策略的能力。对于本解决方案，建议不使用应用组织范围内的设备访问设置。
  
要使用设备访问设置，而这些在第一个版本是：[设置标准或 Office 365 中的第一个发布选项](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)。
  
### <a name="onedrive-for-business"></a>OneDrive for Business

请访问这些设置，以决定是否要更改业务网站的默认设置为 OneDrive。目前，共享和设备访问权限设置 SharePoint Online 管理中心从复制，并应用于这两种环境。
  
## <a name="sharepoint-team-site-configuration"></a>SharePoint 工作组网站配置

下表总结了每个团队站点在本文的前面部分中描述的配置。作为起始点建议使用这些配置和调整以满足组织的需要的网站类型和配置。不是每个组织都需要每种类型的网站。只有较少的组织需要高度机密的保护。
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||**基线保护 #1** <br/> |**基线保护 #2** <br/> |**写保护** <br/> |**高度机密** <br/> |
|说明  <br/> |打开搜索和组织内的协作。  <br/> |组与组外允许共享和专用网站。  <br/> |独立的网站，在其中定义的访问级别的特定组中的成员资格。只允许对网站的成员共享。DLP 将尝试发送在组织外部文件时警告用户。  <br/> |独立的网站 + 文件加密和权限 Azure 的信息保护。DLP 可防止用户发送该组织以外的文件。  <br/> |
|私有或公共的工作组站点  <br/> |公用的  <br/> |专用  <br/> |专用  <br/> |专用  <br/> |
|谁可以访问？  <br/> |每个人在组织中，包括 B2B 用户和来宾用户。  <br/> |只有网站的成员。其他人可以请求访问权限。  <br/> |只有网站的成员。其他人可以请求访问权限。  <br/> |仅限成员。其他人不能请求访问权限。  <br/> |
|站点级共享控制  <br/> |与任何人共享允许。默认设置。  <br/> |与任何人共享允许。默认设置。  <br/> |成员不能共享访问该网站。  <br/> 非成员可以请求访问该网站，但这些请求必须由网站管理员受到重视。  <br/> |成员不能共享访问该网站。  <br/> 非成员不能请求访问的站点或内容。  <br/> |
|站点级设备的访问控制  <br/> |没有其他的控件。  <br/> |没有其他的控件。  <br/> |网站级别控制即将推出，这将使用户将文件下载到不符合标准或非域联接的设备。这样，来自所有其他设备只能在浏览器的访问。  <br/> |网站级别控制即将推出，这将阻止下载到不符合标准或非域联接的设备文件。  <br/> |
|Office 365 标签  <br/> |内部公众  <br/> |专用  <br/> |敏感  <br/> |高度机密  <br/> |
|DLP 策略  <br/> |||在组织外部发送为敏感的标有时警告用户。  <br/> 阻止外部共享敏感数据类型，如信用卡号码或其他个人数据，您可以配置其他 DLP 策略用于这些数据类型 （包括自定义的数据类型，您将配置）。  <br/> |阻止用户发送标记为组织外部为高度机密的文件。允许用户通过提供理由，包括那些它们共享的文件重写。  <br/> |
|Azure 信息保护  <br/> ||||使用 Azure 信息保护自动加密并授予其权限的文件。它们泄漏的情况下，这种保护传输的文件。  <br/> Office 365 无法读取使用 Azure 信息保护加密的文件。此外，DLP 策略只能处理的元数据 （包括标签），但不是包括这些文件 （例如，信用卡号文件内） 的内容。  <br/> |
   
若要部署此解决方案中的 SharePoint Online 小组站点的四种不同类型的步骤，请参阅[部署 SharePoint Online 网站的三个层次的保护](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)。创建开发/测试环境的步骤，请参阅[安全 SharePoint Online 网站的开发/测试环境](secure-sharepoint-online-sites-in-a-dev-test-environment.md)。 
  
## <a name="office-365-classification-and-labels"></a>Office 365 分类和标签

环境中的敏感数据，建议使用 Office 365 标签。在您配置和发布 Office 365 标签：
  
- 可以应用于在线 SharePoint 的工作组网站中的文档库的默认标签以便该库中的所有文档的默认标签。 
    
- 您可以将标签应用于内容自动匹配特定条件。
    
- 您可以应用基于 Office 365 提供标签的 DLP 策略。
    
- 您组织中的人员可以应用标签手动内容在 web 上的 Outlook 中 2010年及更高版本的 Outlook，OneDrive 业务、 SharePoint Online 和 Office 365 的组。用户通常非常清楚地知道什么类型的内容他们正在使用，因此可以对其进行分类和应用适当的 DLP 策略。
    
![适用于 SharePoint 网站的推荐配置](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
如所示，这一解决方案包括创建以下标签：
  
- 高度机密
    
- 敏感
    
- 专用
    
- 内部公众
    
这些标签映射到图中的推荐的网站和本文中前面的图表。本解决方案建议配置 DLP 策略有助于防止文件标记为敏感和高度机密的泄露。
  
在此解决方案中配置 Office 365 标签和 DLP 策略的步骤，请参阅[Office 365 标签和 DLP 与保护 SharePoint Online 文件](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)。
  
## <a name="azure-information-protection"></a>Azure 信息保护

使用 Azure 信息保护应用标签和按照文件，无论它们的保护。对于本解决方案，我们建议使用的指定了作用域的 Azure 的信息保护策略和高度机密的标签的子标签进行加密和授权需要使用安全的最高级别保护的文件。 
  
请注意当 Azure 信息保护加密应用于存储在 Office 365 中的文件时，此服务无法处理这些文件的内容。共同创作、 eDiscovery、 搜索、 Delve 和其他协作功能不起作用。DLP 策略只能处理的元数据 （包括 Office 365 的标签），但不是包括这些文件 （例如，信用卡号文件内） 的内容。
  
![Azure 信息保护是在 Azure 中进行配置，标签显示在客户端工具栏中](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
图所示：
  
- 在 Microsoft Azure 门户配置了 Azure 的信息保护策略和标签。建议配置的指定了作用域的 Azure 的信息保护策略的子标签。
    
- Azure 的信息保护标签显示了作为 Office 应用程序中的**信息保护**栏。
    
### <a name="adding-permissions-for-external-users"></a>添加外部的用户的权限

有两种方法可以授予外部用户访问 Azure 的信息保护受保护的文件。在这两个这种情况下，外部用户必须拥有 Azure 的广告帐户。如果外部用户不能使用 Azure AD 的组织的成员，他们可以获取的 Azure 的广告帐户作为个人利用该注册页面： [https://aka.ms/aip-signup](https://aka.ms/aip-signup)。
  
- 将外部用户添加到用于配置的标签保护 Azure AD 组
    
     您将需要首先为您的目录中的 B2B 用户添加帐户。它可以需要几个小时的[组成员身份缓存的 Azure 权限管理](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management)。使用此方法，将权限授予设有标签 （即使文件保护到 Azure AD 组添加用户之前） 的所有现有文件。
    
- 外部用户将直接添加到标签保护
    
     可以从组织 (例如 Fabrikam.com)，（例如组织内部财务组） Azure AD 组或单个用户添加的所有用户。例如，您可以添加标签保护外部团队的管理机构。使用此方法，只对外部实体添加到保护后，保护带标签的文件授予权限。
    
### <a name="deploying-and-using-azure-information-protection"></a>部署和使用 Azure 的信息保护

将 Azure 信息保护配置此解决方案中的步骤，请参阅[保护 SharePoint Online Azure 的信息保护的文件](protect-sharepoint-online-files-with-azure-information-protection.md)。
  
## <a name="see-also"></a>See Also

[为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[安全解决方案](security-solutions.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
  
[开发/测试环境中的安全 SharePoint Online 网站](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



