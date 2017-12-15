---
title: "Office 365 开发/测试环境中的数据分类和标记"
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
- jan17entnews
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: "摘要： 配置和展示数据分类和标记您 Office 365 的开发/测试环境中使用 Azure 信息保护 (AIP) 客户端。"
ms.openlocfilehash: 2784f4105903855de89c6c45f7a643279bb4dfbf
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Office 365 开发/测试环境中的数据分类和标记

 **摘要：**配置和展示数据分类和标记您 Office 365 的开发/测试环境中使用 Azure 信息保护 (AIP) 客户端。
  
Azure 信息保护客户端使您可以将文档划分到之前将其上载到 SharePoint Online Office 365 中的文件夹。使用本文中的说明进行操作，您可以安装 Azure 信息保护客户端和演示数据分类。有关详细信息，请参阅[Azure 的信息保护](https://www.microsoft.com/cloud-platform/azure-information-protection)。
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>第 1 阶段：构建 Office 365 开发/测试环境

按照在[Office 365 的开发/测试环境](office-365-dev-test-environment.md)中的说明进行操作。
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>第 2 阶段：添加 Azure 信息保护试用订阅

在此阶段中，您添加到 Office 365 开发/测试环境的 Azure 信息保护并使您的用户帐户。如果您已配置了[Office 365 和 EMS 开发/测试环境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)，则跳过这一阶段。企业移动套件试用订阅包括 Azure 信息保护许可证。
  
首先，注册 Azure 信息保护试用订阅。
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>注册 Azure 信息保护试用订阅

1. 在 Internet Explorer 或浏览器中，转到[http://portal.office.com](http://portal.office.com)并使用您的 Office 365 提供全局管理员帐户登录。
    
2. **Microsoft Office 主页**选项卡上，单击**管理**拼贴。
    
3. 在 Office 365 管理选项卡上的在左侧的导航，请单击**计费 > 购买服务**。
    
4. **购买服务**页上找到**Azure 信息保护津贴 P2**项。鼠标悬停并单击**开始免费试用版**。
    
5. 在**确认订单**页中，单击**立即尝试**。
    
6. 在**订单收据**页上，单击**继续**。
    
接下来，为所有用户帐户启用 Azure 信息保护许可证。
  
1. 在 Office 365 管理中心选项卡上，单击**用户**。
    
2.  在用户帐户的列表中，选择您的全局管理员帐户，然后单击**编辑****产品**许可证。
    
3. 对**Azure 信息保护津贴 P2**到**上**打开产品许可证、 单击**保存**，然后单击**关闭**两次。
    
4. 对其他用户帐户（用户 1 至用户 5）重复执行第 2 步和第 3 步。
    
此时，Office 365 开发/测试环境包含：
  
- Office 365 E5 企业版和 Azure 信息保护试用订阅。
    
- 可使用 Office 365 E5 企业版和 Azure 信息保护的所有用户帐户。
    
## <a name="phase-3-demonstrate-data-classification"></a>第 3 阶段：演示数据分类

在此阶段中，你将使用 Azure 信息保护客户端和默认的 Azure 信息保护策略演示数据分类。
  
如果使用的是模拟企业 Office 365 开发/测试环境，必须先在 CLIENT1 上安装 Office 2016。
  
1. 使用您的浏览器并转到[Azure 的门户](http://portal.azure.com)。
    
2. 单击**资源组 >** [资源组名称] **> 客户端 1 > 连接**。
    
3. 从客户端 1，运行 Internet Explorer，转到[http://portal.office.com](http://portal.office.com)，在该办公室门户然后使用 User5 帐户名和密码登录。
    
4. 在**Microsoft Office 主页**选项卡上，单击**安装 Office 2016**。
    
5. 运行时系统提示，请单击**是**用户帐户控制提示时下载。等待安装 Office。完成后，单击**关闭**两次。
    
接下来，安装 Azure 信息保护客户端。
  
1. 在浏览器或 Internet Explorer 中，转到[Microsoft Azure 信息保护下载页面](https://www.microsoft.com/download/details.aspx?id=53018)。
    
  - 如果使用的是轻型 Office 365 开发/测试环境，请在本地计算机上运行浏览器。
    
  - 如果使用的是模拟企业 Office 365 开发/测试环境，请在 CLIENT1 上运行 Internet Explorer。
    
2. 在**Microsoft Azure 信息保护**下载页上，单击**下载**，请单击**AzInfoProtection.exe**，，然后单击**下一步**。
    
3. 出现提示时，运行 AzInfoProtection.exe。
    
4. 在**安装 Azure 信息保护**客户端中，单击**我同意**，然后单击**是**用户帐户控制提示时。
    
5. 在**已成功完成**框中，单击**关闭。**
    
接下来，演示文档分类。
  
1. 单击任务栏中的**Word**图标。
    
2. 当出现提示时，使用 User5 帐户名称和密码登录。
    
3. 如果只安装 Office 2016 上客户端 1，**要事第一**框中，单击**接受**。
    
4. 单击**空白文档**。 
    
    请注意在**主页**选项卡，文档分类的行功能区的**保护**部分。
    
5. 在空白文档中，键入一些文本。
    
6. 单击**文件 > 保存**，键入名称**BeforeAIP**，，然后单击**确定**。 
    
7. 在行中的文档类，为**机密**，单击向下箭头，然后单击**全部公司**。
    
8. 单击**文件 > 另存为**，键入名称**AfterAIP**，，然后单击**确定**。
    
9. 在任务栏中，单击**文件资源管理器**，然后打开**文档**文件夹。
    
    请注意不同文件的**BeforeAIP**和**AfterAIP**文档的大小。AfterAIP 文档是较大的因为它包含分类信息。
    
接下来，允许每个人访问支持网站集。
  
1. 在**Microsoft Office 主页**选项卡上，单击**SharePoint**。
    
2. 从**SharePoint**选项卡上，单击**支持网站集**。
    
3. 右上角，单击**设置**图标，然后单击**共享的**。
    
4. 在**共享支持网站集**，单击**高级**。
    
5. 在列表的 SharePoint 组，请单击**支持站点集合成员**。
    
6. 在**用户和用户组**页上，单击**新建**。
    
7. 在**共享支持网站集**，键入**每个人**，**每个人，除了外部用户**，请单击，然后单击**共享。**
    
8. 关闭**用户和用户组**选项卡。
    
接下来，使用 User5 帐户登录，然后将受 AIP 保护的文档上载到支持网站集的“Documents”文件夹中。
  
1. 在**Microsoft Office 家庭**选项卡上的在右上角，单击用户图标，然后单击**注销**。
    
2. 转到[http://portal.office.com](http://portal.office.com)。
    
3. 在 * * 签名的 Office 365 * * 页上，单击 User5 帐户的名称，在每次登录。
    
4. 在**Microsoft Office 主页**选项卡，单击**SharePoint > 支持网站**。
    
5. 单击**文档**，单击**上载**、 **AfterAIP**文档，请单击，然后单击**打开**。
    
    应该会在支持网站集上看到文档文件夹中的 AfterAIP.docx。
    
## <a name="see-also"></a>See Also

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 和 EMS 开发/测试环境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure 的信息保护](https://www.microsoft.com/cloud-platform/azure-information-protection)


