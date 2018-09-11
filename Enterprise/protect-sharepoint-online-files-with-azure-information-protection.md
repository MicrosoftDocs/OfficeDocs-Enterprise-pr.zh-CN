---
title: 使用 Azure 信息保护来保护 SharePoint Online 文件
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/08/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 摘要：应用 Azure 信息保护来保护高度机密的 SharePoint Online 团队网站中的文件。
ms.openlocfilehash: 4ea6c1da8b39f22a56ba4f4d555518b671f07b70
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915307"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>使用 Azure 信息保护来保护 SharePoint Online 文件

 **摘要：** 应用 Azure 信息保护来保护高度机密的 SharePoint Online 团队网站中的文件。
  
本文逐步介绍了如何将 Azure 信息保护配置为，加密文件和授予对文件的权限。可以将这些文件添加到配置了高度机密保护的 SharePoint 库。也可以直接从网站中打开文件，并使用 Azure 信息保护客户端添加加密。加密和权限保护与文件如影随形，即使从网站下载文件，也不例外。 

为 SharePoint 网站及其中文件配置高度机密保护的大型解决方案采用这些步骤。有关详细信息，请参阅[保护 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)。 

对 SharePoint Online 中的文件使用 Azure 信息保护不建议用于所有客户，但适用于部分文件需要这种保护级别的客户。

关于此解决方案，请务必注意以下几点：
- 将 Azure 信息保护加密应用于 Office 365 中存储的文件时，该服务无法处理这些文件的内容。 共同创作、电子数据展示、搜索、Delve 和其他协作功能将无法正常使用。 数据丢失防护 (DLP) 策略只适用于元数据（包括 Office 365 标签），但并不适用于这些文件的内容（如文件内的信用卡号）。
- 此解决方案要求，用户必须选择通过 Azure 信息保护应用保护的标签。如果需要自动加密并便于 SharePoint 能够将文件编入索引和检查文件，建议在 SharePoint Online 中使用信息权限管理 (IRM)。为 SharePoint 库配置 IRM 后，文件会在下载以供编辑时自动加密。SharePoint IRM 有可能会影响你决定的限制。有关详细信息，请参阅[在 SharePoint 管理中心内设置信息权限管理 (IRM)](https://support.office.com/zh-CN/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C)。

##<a name="admin-setup"></a>管理员设置
首先，对 Office 365 订阅按照[使用 Office 365 管理中心激活 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) 中的说明操作。
  
接下来，使用新作用域内的策略以及高度机密的 SharePoint Online 团队网站用于保护和权限的子标签来配置 Azure 信息保护。
  
1. 使用具有安全管理员或公司管理员角色的帐户登录到 Office 365 门户。有关帮助信息，请参阅[在何处登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在浏览器的单独标签页中，转到 Azure 门户 ([https://portal.azure.com](https://portal.azure.com))。
    
3. 如果是首次配置 Azure 信息保护，请参阅这些[说明](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。

4. 在列表窗格中，单击“**更多服务**”，键入“**信息**”，然后单击“**Azure 信息保护**”。

5. 单击“**标签**”。
    
6. 右键单击“高度机密”**** 标签，然后单击“添加子标签”****。
    
7. 在“名称”**** 中键入子标签的名称，并在“描述”**** 中键入子标签的描述。
    
8. 在“为包含此标签的文档和电子邮件设置权限”**** 中，单击“保护”****。
    
9. 在“保护”**** 部分中，单击“Azure (云密钥)”****。
    
10. 在“保护”**** 边栏选项卡中，在“保护设置”**** 下，单击“添加权限”****。
    
11. 在“添加权限”**** 边栏选项卡的“指定用户和组”**** 下，单击“浏览目录”****。
    
12. 在“AAD 用户和组”**** 窗格中，选择高度敏感的 SharePoint Online 团队网站的网站成员访问组，然后单击“选择”****。
    
13. 在“从预设或设置自定义中选择权限”**** 下，单击“自定义”****，然后依次单击“查看权限”****、“编辑内容”****、“保存”****、“答复”**** 和“全部答复”**** 复选框。
    
14. 单击“**确定**”两次。
    
15. 在“**子标签**”边栏选项卡上，单击“**保存**”，然后单击“**确定**”。

16. 在“Azure 信息保护”**** 边栏选项卡上，单击“策略”>“添加新策略”****。
    
17. 在“策略名称”**** 中键入新策略的名称，并在“描述”**** 中键入新策略的描述。
    
18. 单击“选择获取此策略的用户或组”>“用户/组”，然后选择高度敏感的 SharePoint Online 团队网站的网站成员访问组****。
    
19. 单击“选择”>“确定”****。

20. 单击“添加或删除标签”****。在“策略: 添加或删除标签”**** 窗格中，单击新子标签的名称，然后单击“确定”****。   

21. 单击“保存”****，然后单击“确定”****。
 
##<a name="client-setup"></a>客户端设置
现在可以开始创建文档，并使用 Azure 信息保护和新标签来保护它们。
  
你必须在设备或基于 Windows 的计算机上[安装 Azure 信息保护客户端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)。可以编写脚本，使安装自动化，也可手动安装客户端。请参阅以下资源：
  
- [Azure 信息保护的客户端](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [安装 Azure 信息保护客户端](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [手动安装的下载页](https://www.microsoft.com/download/details.aspx?id=53018)
    
安装后，用户就可以运行 Office 应用程序（如 Microsoft Word），然后使用其 Office 365 帐户登录。新的“信息保护”**** 栏允许用户选择新标签。请确保你的用户知道 SharePoint Online 团队网站，以及要使用哪个标签来保护其高度机密的文件。
  
> [!NOTE]
> 如果有多个高度敏感的 SharePoint Online 团队网站，应创建多个 Azure 信息保护作用域内策略以及多个包含上述设置的子标签，另外每个子标签的权限设置为特定 SharePoint Online 团队网站的网站成员访问组。 
  
##<a name="adding-permissions-for-external-users"></a>为外部用户添加权限
可通过两种方式向外部用户授予对 Azure 信息保护已保护文件的访问权限。在这两种情况下，外部用户都必须拥有 Azure AD 帐户。如果外部用户不属于使用 Azure AD 的组织，可以使用下面的注册页以个人身份获得 Azure AD 帐户：[https://aka.ms/aip-signup](https://aka.ms/aip-signup)。

 - 将外部用户添加到用于配置标签保护的 Azure AD 组。需要先以 B2B 用户身份在目录中添加此帐户。[Azure 权限管理缓存组成员资格](https://docs.microsoft.com/zh-CN/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection)可能需要几个小时才能完成。  
 - 将外部用户直接添加到标签保护设置中。可以添加组织（例如 Fabrikam.com）中的所有用户、Azure AD 组（如组织内的财务组）或单个用户。例如，可以将监管机构的外部团队添加到标签保护设置中。

## <a name="see-also"></a>另请参阅

[保护 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)
  
[在开发/测试环境中保护 SharePoint Online 网站](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[Microsoft 针对政治宣传活动、非营利组织和其他敏捷性组织的安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)




