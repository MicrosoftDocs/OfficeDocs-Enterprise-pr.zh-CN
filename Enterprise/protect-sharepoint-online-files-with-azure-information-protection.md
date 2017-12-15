---
title: "SharePoint Online Azure 的信息保护文件保护"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "摘要： 应用 Azure 的信息保护，以保护高度机密的在线 SharePoint 工作组网站中的文件。"
ms.openlocfilehash: bc2c7dbbcc254270cf2c7db3d3eed98b3f7872f6
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>SharePoint Online Azure 的信息保护文件保护

 **摘要：**应用 Azure 的信息保护，以保护高度机密的在线 SharePoint 工作组网站中的文件。
  
使用本文中的步骤配置 Azure 信息保护提供加密和高度机密的 SharePoint Online 工作组站点中的文件的权限。即使从网站上下载，使用文件传输时加密和权限保护。关于高度机密的在线 SharePoint 工作组网站的详细信息，请参阅[安全 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)。
  
> [!NOTE]
> 当 Azure 信息保护加密应用于存储在 Office 365 中的文件时，该服务无法处理这些文件的内容。共同创作、 eDiscovery、 搜索、 Delve 和其他协作功能不起作用。数据丢失防护 (DLP) 策略只能处理的元数据 （包括 Office 365 的标签），但不是包括这些文件 （例如，信用卡号文件内） 的内容。 
  
首先，使用中的说明[将 Azure RMS 激活 Office 365 管理中心](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)为您 Office 365 的订阅。
  
接下来，使用一个指定了作用域的新策略和子标签保护和高度机密 SharePoint Online 工作组站点的权限配置 Azure 的信息保护。
  
1. Office 365 门户拥有安全管理员或公司管理员角色的帐户登录。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。
    
2. 在浏览器的单独的选项卡，请转到 Azure 门户网站 ([https://portal.azure.com](https://portal.azure.com))。
    
3. 如果这是首次配置 Azure 信息保护，请参见以下[说明](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。
    
4. 在列表窗格中，单击**更多服务**，键入**信息**，，然后单击**Azure 信息保护**。
    
5. **Azure 信息保护**刀片式服务器，，单击**范围策略 > 添加新策略 +**。
    
6. 键入**策略的名称**和**描述**中的说明新策略的名称。
    
7. 单击**选择哪些用户或组获取该策略 > 用户/用户组**，然后选择网站成员访问高度敏感联机 SharePoint 工作组网站用户组。 
    
8. 单击**选择 > 确定**。
    
9. **高度机密**的标签，请单击省略号 （...），然后单击**添加子标签**。
    
10. 键入**名称**和说明中**说明**的标签的子标签的名称。
    
11. 在**设置权限的文档和电子邮件包含此标签**，请单击**保护**。
    
12. 在**保护**部分中，单击**Azure （云键）**。
    
13. 在**保护**刀片式服务器下**保护设置**，, 单击**+ 添加权限**。
    
14. **添加权限**刀片式服务器，在**指定用户和组**，请单击**+ 浏览目录**。
    
15. 在**AAD 的用户和组**窗格中，选择高度敏感 SharePoint Online 工作组站点，站点成员访问组，然后单击**选择**。
    
16. 在**选择权限从预设**清除**打印**、**复制和内容的提取**和**转发**复选框。
    
17. 单击**确定**两次。
    
18. 在**子标签**刀片式服务器，单击**保存**。
    
19. 关闭新的指定了作用域的策略刀片。
    
20. 在**Azure 信息保护的指定了作用域策略**刀片式服务器，单击**发布**。
    
这是高度机密 SharePoint Online 工作组站点为您生成配置。
  
![独立 SharePoint Online 团队网站的 Azure 信息保护标签。](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
现在您可以开始创建文档，并加以保护利用 Azure 的信息保护和新的标签。
  
您必须在您的设备或基于 Windows 的计算机上[安装 Azure 信息保护客户端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)。您可以编写脚本和自动安装，或者用户可以手动安装客户端。请参阅以下资源：
  
- [客户端的 Azure 的信息保护](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [安装 Azure 信息保护客户端](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [下载页面的手动安装](https://www.microsoft.com/download/details.aspx?id=53018)
    
安装后，您的用户运行，然后登录某个 Office 应用程序 （如 Microsoft Word) 与他们 Office 365 的帐户。新的**信息保护**栏，用户可选择的新标签。请确保您的用户知道在线 SharePoint 工作组网站和其标签使用，来保护他们的高度机密文件。
  
> [!NOTE]
> 如果您有多个高度敏感的 SharePoint Online 工作组网站，应创建多个范围的 Azure 的信息保护策略的子标签，上面的设置，与每个子标签设置为网站成员访问权限组的权限SharePoint Online 的特定工作组站点。 
  
## <a name="see-also"></a>See Also

[SharePoint Online 网站和文件保护](secure-sharepoint-online-sites-and-files.md)
  
[开发/测试环境中的安全 SharePoint Online 网站](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)




