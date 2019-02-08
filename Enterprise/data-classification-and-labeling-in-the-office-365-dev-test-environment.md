---
title: Office 365 开发/测试环境中的数据分类和标记
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 摘要：在 Office 365 开发/测试环境中使用 Azure 信息保护 (AIP) 客户端配置和演示数据分类和标记。
ms.openlocfilehash: 69526f8bf0ae0b6cc7509653cfaa72581e10dbfe
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897435"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Office 365 开发/测试环境中的数据分类和标记

 **摘要：** 在 Office 365 开发/测试环境中使用 Azure 信息保护 (AIP) 客户端配置和演示数据分类和标记。
  
Azure 信息保护客户端允许您将其上载到 Office 365 中的 SharePoint Online 文件夹之前对文档进行分类。使用本文中的说明，您可以安装 Azure 信息保护客户端和演示数据分类。有关详细信息，请参阅[Azure 信息保护](https://www.microsoft.com/cloud-platform/azure-information-protection)。
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>第 1 阶段：构建 Office 365 开发/测试环境

请按 [Office 365 dev/test environment](office-365-dev-test-environment.md)中的说明操作。
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>第 2 阶段：添加 Azure 信息保护试用订阅

在此阶段，将 Azure 信息保护添加到 Office 365 开发/测试环境，并为用户帐户启用该功能。如果已配置 [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)，请跳过此阶段。企业移动性套件试用订阅包括 Azure 信息保护许可证。
  
首先，注册 Azure 信息保护试用订阅。
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>注册 Azure 信息保护试用订阅

1. 在 Internet Explorer 或您的浏览器中，转到[http://portal.office.com](http://portal.office.com)和使用您的 Office 365 全局管理员帐户登录。
    
2. 在“**Microsoft Office 主页**”标签页上，单击“**管理员**”磁贴。
    
3. 在“Office 365 管理中心”标签页上的左侧导航栏中，依次单击 **“计费”>“购买服务”**。
    
4. 在“**购买服务**”页上，找到“**Azure 信息保护高级版 P2**”项。将鼠标悬停在其上，然后单击“**开始免费试用**”。
    
5. 在“确认订单”页上，单击“立即试用”********。
    
6. 在“订单签收”页上，单击“继续”********。
    
接下来，为所有用户帐户启用 Azure 信息保护许可证。
  
1. 	在“Office 365 管理中心”标签页上，单击“**用户**”。
    
2.   在用户帐户列表中，选择全局管理员帐户，然后单击“**产品许可证**”旁边的“**编辑**”。
    
3. 	将“**Azure 信息保护高级版 P2**”的产品许可证设为“**开**”，单击“**保存**”，然后单击“**关闭**”两次。
    
4. 对其他用户帐户（用户 1 至用户 5）重复执行第 2 步和第 3 步。
    
此时，Office 365 开发/测试环境包含：
  
- Office 365 E5 企业版和 Azure 信息保护试用订阅。
    
- 可使用 Office 365 E5 企业版和 Azure 信息保护的所有用户帐户。
    
## <a name="phase-3-demonstrate-data-classification"></a>第 3 阶段：演示数据分类

在此阶段中，你将使用 Azure 信息保护客户端和默认的 Azure 信息保护策略演示数据分类。
  
如果使用的是模拟企业 Office 365 开发/测试环境，必须先在 CLIENT1 上安装 Office 2016。
  
1. 使用您的浏览器并转到[Azure 门户](http://portal.azure.com)。
    
2. 	单击“**资源组 >** [资源组名称] **> CLIENT1 > 连接**”。
    
3. 从 CLIENT1，运行 Internet Explorer，转到 Office 门户[http://portal.office.com](http://portal.office.com)，然后使用 User5 帐户名和密码登录。
    
4. 在“Microsoft Office 主页”**** 标签页上，单击“安装 Office 2016”****。
    
5. 	出现提示时运行下载，并在出现用户帐户控制提示时单击“**是**”。等待安装 Office。完成后，单击“**关闭**”两次。
    
接下来，安装 Azure 信息保护客户端。
  
1. 在浏览器或 Internet Explorer，转到[Microsoft Azure Information Protection 下载页面](https://www.microsoft.com/download/details.aspx?id=53018)。
    
  - 如果使用的是轻型 Office 365 开发/测试环境，请在本地计算机上运行浏览器。
    
  - 如果使用的是模拟企业 Office 365 开发/测试环境，请在 CLIENT1 上运行 Internet Explorer。
    
2. 在“**Microsoft Azure 信息保护**”下载页，单击“**下载**”，单击“**AzInfoProtection.exe**”，然后单击“**下一个**”。
    
3. 出现提示时，运行 AzInfoProtection.exe。
    
4. 在“**安装 Azure 信息保护**”客户端框中，单击“**我同意**”，然后在出现用户帐户控制提示时单击“**是**”。
    
5. 在“**已成功完成**”框中，单击“**关闭**”。
    
接下来，演示文档分类。
  
1. 单击任务栏中的“**Word**”图标。
    
2. 当出现提示时，使用 User5 帐户名称和密码登录。
    
3. 如果只在 CLIENT1 上安装 Office 2016，在“**首要事务**”框中，单击“**接受**”。
    
4. 单击“**空白文档**”。  
    
    注意“**主页**”选项卡上功能区的“**保护**”部分和文档分类行。
    
5. 在空白文档中，键入一些文本。
    
6. 单击“**文件 > 保存**”，键入名称 **BeforeAIP**，然后单击“**确定**”。  
    
7. 在文档分类行中，单击“**保密**”的向下箭头，然后单击“**所有公司**”。
    
8. 单击“**文件 > 另存为**”，键入名称 **AfterAIP**，然后单击“**确定**”。
    
9. 单击任务栏中的“**文件资源管理器**”，然后打开“**文档**”文件夹。
    
    注意**BeforeAIP**和**AfterAIP**文档的不同文件大小。AfterAIP 文档是较大，因为它包含分类信息。
    
接下来，允许每个人访问支持网站集。
  
1. 	在“**Microsoft Office 主页**”选项卡上，单击“**SharePoint**”。
    
2. 在“**SharePoint**”选项卡上，单击“**支持网站集**”。
    
3. 在右上角，单击“**设置**”图标，然后单击“**共享**”。
    
4. 在**共享支持网站集**，单击**高级**。
    
5. 在 SharePoint 组列表中，单击“**支持网站集成员**”。
    
6. 在“**人员和组**”页中，单击“**新建**”。
    
7. 在**共享支持网站集**，键入**Everyone**，单击**除外部用户**，然后单击**共享。**
    
8. 关闭“**人员和组**”选项卡。
    
接下来，使用 User5 帐户登录，然后将受 AIP 保护的文档上载到支持网站集的“Documents”文件夹中。
  
1. 在“**Microsoft Office 主页**”选项卡上，单击右上方的用户图标，然后单击“**注销**”。
    
2. 转到 [http://portal.office.com](http://portal.office.com)。
    
3. 在**Office 365 登录**页上，单击 User5 帐户名和登录。
    
4. 在“**Microsoft Office 主页**”选项卡上，单击“**SharePoint > 支持网站集**”。
    
5. 单击“**文档**”，单击“**上载**”，单击“**AfterAIP**”文档，然后单击“**打开**”。
    
    应该会在支持网站集上看到文档文件夹中的 AfterAIP.docx。
    
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 和 EMS 开发/测试环境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)（Azure 信息保护）


