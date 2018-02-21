---
title: "Contoso Corporation 的安全"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: "摘要： 了解 Contoso 微软云服务中的功能映射其安全要求，并确定一个路径以云安全准备工作。"
ms.openlocfilehash: f8df7f6437159aefe88851a22cc8da8b19c3838c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="security-for-the-contoso-corporation"></a>Contoso Corporation 的安全

 **摘要：**了解如何 Contoso 微软云服务中的功能映射其安全要求和确定的路径来云安全准备工作。
  
Contoso 非常注重他们的信息安全和保护。在转换到一个云非独占其 IT 基础架构时，他们已确保他们内部的安全需求所支持，Microsoft 的云服务中实现。
  
## <a name="contosos-security-requirements-in-the-cloud"></a>在云中 Contoso 的安全要求

下面是 Contoso 对云的安全要求：
  
- 对云资源的强身份验证
    
    云资源访问必须经过身份验证，并在可能的情况下利用多重身份验证。
    
- 通过 Internet 的流量加密
    
    在 Internet 中没有以纯文本形式发送的数据。始终使用 HTTPS 连接、IPsec 或其他端到端数据加密方法。
    
- 云中静态数据的加密
    
    存储在磁盘上或云中其他地方的所有数据都必须采用加密形式。
    
- 进行最小特权访问的 ACL
    
    访问云中资源的帐户权限以及允许的操作都必须遵循最小特权原则。
    
## <a name="contosos-data-sensitivity-classification"></a>Contoso 的数据敏感度分类

在 Microsoft 的[数据分类 Toolkit](https://msdn.microsoft.com/library/hh204743.aspx)中使用的信息，Contoso 执行对其数据的分析，确定以下级别。
  
|**1 级： 较低的业务价值**|**2 级： 中等的业务价值**|**3 级： 高业务价值**|
|:-----|:-----|:-----|
|数据被加密，仅允许已通过身份验证的用户  <br/> 向存储在本地和基于云的存储空间和工作负载（例如 Office 365）中的所有数据提供。驻留在服务中和在服务与客户端设备之间传输时，数据处于加密状态。  <br/> 1 级数据的示例为正常的业务通信（电子邮件）和供管理、销售和支持工作人员使用的文件。  <br/> |1 级，再加上强身份验证和数据丢失保护  <br/> 强身份验证包括 SMS 验证的多因素身份验证。数据丢失防范确保敏感或关键的信息不会不出国的内部网络。  <br/> 2 级数据的示例包括财务和法律信息，以及新产品的研发数据。  <br/> |2 级，再加上最高级别的加密、 身份验证和审核  <br/> 最高级别的加密的数据存放在云中，符合区域法规，结合多因素身份验证的智能卡和细致审核和报警。  <br/> 3 级数据的示例是客户和合作伙伴的个人身份信息、产品工程规范以及专有的制造技术。  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a>将 Microsoft 云产品和功能映射到 Contoso 的数据级别

下表显示 Contoso 的数据级别在 Microsoft 的云产品功能中的映射：
  
||**SaaS**|**Azure PaaS**|**Azure IaaS**|
|:-----|:-----|:-----|:-----|
|级别 1：业务价值较低  <br/> | HTTPS 的所有连接 <br/>  静态加密 <br/> | 支持仅 HTTPS 连接 <br/>  加密存储在 Azure 中的文件 <br/> | 需要 HTTPS 或 IPsec 的服务器访问权限 <br/>  Azure 磁盘加密 <br/> |
|级别 2：业务价值中等  <br/> | 具有 SMS 的 Azure AD 多重身份验证 (MFA) <br/> | 用于加密密钥的 Azure 密钥存储库 <br/>  具有 SMS 的 Azure AD MFA <br/> | 具有 SMS 的 MFA <br/> |
|级别 3：业务价值较高  <br/> | Azure 的权限管理系统 (RMS) <br/>  具有智能卡的 Azure AD MFA <br/>  Intune 条件访问 <br/> | Azure RMS <br/>  具有智能卡的 Azure AD MFA <br/> | 具有智能卡的 MFA <br/> |
   
## <a name="contosos-information-policies"></a>Contoso 的信息策略

下表列出了 Contoso 的信息策略。
  
||**访问**|**数据保留**|**信息保护**|
|:-----|:-----|:-----|:-----|
|级别 1：业务价值较低  <br/> | 允许访问所有 <br/> |6 个月  <br/> |使用加密  <br/> |
|级别 2：业务价值中等  <br/> | 允许访问 Contoso 雇员、 分包商和合作伙伴 <br/>  使用 MFA、TLS 和 MAM <br/> |2 年  <br/> |使用哈希值实现数据完整性  <br/> |
|级别 3：业务价值较高  <br/> | 允许访问高级管理人员和工程设计和制造中的潜在顾客 <br/>  仅具有托管网络设备的 RMS <br/> |7 年  <br/> |使用数字签名实现不可否认性  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a>Contoso 的云安全准备工作路径

Contoso 使用以下步骤为 Microsoft 云安全做准备：
  
1. 优化的云管理员帐户
    
    Contoso 对现有的 Windows Sever AD 管理员帐户进行了广泛审阅，并设置了一系列的云管理员帐户和组。
    
2. 分为三个级别执行数据分类分析
    
    Contoso 执行进行仔细检查，已确定的三个级别，用来确定 Microsoft 云环境提供功能，以保护 Contoso 的最有价值的数据。
    
3. 确定数据级别的访问、 保留和信息保护策略
    
    Contoso 已根据数据级别确定将用于限定转移到云的未来 IT 工作负载的详细要求。
    
## <a name="contosos-use-of-office-365-security-best-practices"></a>Contoso 的使用的 Office 365 安全最佳做法

根据 Office 365 安全最佳做法，Contoso 的安全管理员和 IT 部门已经部署如下：
  
- **专用的全局管理员帐户具有非常强的密码**
    
    而不是日常的用户帐户分配全局管理员角色，Contoso 创建有三个，专用的全局管理员帐户具有非常强的密码。针对特定管理任务只完成一个全局管理员帐户进行登录和密码只已知给指定人员。Contoso 的安全管理员为适用于该 IT 人员的工作职能和职责的帐户分配了管理员角色。
    
    有关详细信息，请参阅[有关 Office 365 管理角色](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)。
    
- **重要的用户帐户的多因素身份验证 (MFA)**
    
    MFA 通过要求用户确认电话通话、 短信或其智能手机应用程序通知后正确地输入自己的密码登录过程添加附加的保护层。MFA，与 Office 365 的用户帐户不会受到未经授权的登录即使帐户密码被泄露。
    
  - 为了防止 Office 365 订阅的危害，Contoso 在所有三个全局管理员帐户上启用 MFA。
    
  - 以抵御网络钓鱼攻击，攻击破坏组织中受信任的个人的凭据，然后发送恶意电子邮件，Contoso MFA 上启用所有用户帐户经理，包括管理层人员。
    
    有关详细信息，请参阅[Office 365 部署的多因素身份验证计划](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)
    
- **高级的安全管理 (ASM)**
    
    ASM 使用配置策略以监视的反常活动。设置警报和 ASM，使 IT 管理员会收到通知的不寻常的或危险的用户活动，例如下载大量数据，Contoso 安全管理员多失败的登录尝试或符号接来自未知或危险的 IP 地址
    
    有关详细信息，请参阅[概述的高级安全管理 Office 365 中](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。
    
- **安全电子邮件流和邮箱审核日志记录**
    
    Contoso 安全专家正在使用 Exchange 在线保护和高级威胁防护 (ATP) 来防止未知的恶意软件、 病毒和恶意 Url 通过电子邮件传输。Contoso 还具有已启用的邮箱审核日志，以确定谁已登录到发送邮件，用户邮箱和邮箱所有者、 委派的用户或管理员执行的其他活动。
    
    有关详细信息，请参阅： 
    
  - [Office 365 的电子邮件的反垃圾邮件保护](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [安全的附件以及安全链接的高级的威胁防护](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [启用审核 Office 365 中的邮箱](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- **数据丢失防护 (DLP)**
    
    Contoso 已识别其敏感数据，并配置的 Exchange 联机、 SharePoint Online，和 OneDrive 可以帮助防止用户无意或有意地共享数据的 DLP 策略。 
    
    有关详细信息，请参阅[数据丢失防护策略的概述](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)。
    
## <a name="see-also"></a>See Also

[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)
  
[Office 365 的安全最佳做法](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




