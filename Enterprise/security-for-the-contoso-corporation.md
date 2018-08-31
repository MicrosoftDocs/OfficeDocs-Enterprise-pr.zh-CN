---
title: Contoso Corporation 的安全
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: 摘要： 了解如何 Contoso Microsoft 云服务中的功能映射其安全要求以及确定用于云安全准备的路径。
ms.openlocfilehash: 722c01995c95c36b9975b0682858c38063f79d2c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914827"
---
# <a name="security-for-the-contoso-corporation"></a>Contoso Corporation 的安全

 **摘要：** 了解如何 Contoso Microsoft 云服务中的功能映射其安全要求和确定用于云安全准备的路径。
  
有关其信息安全和保护严重 Contoso。在转换到云包含一个其 IT 基础结构时，他们做确保其本地安全要求已支持并在 Microsoft 云服务中实现。
  
## <a name="contosos-security-requirements-in-the-cloud"></a>在云中的 Contoso 的安全要求

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

使用 Microsoft 的[数据分类工具包](https://msdn.microsoft.com/library/hh204743.aspx)中的信息，Contoso 执行其数据分析和确定以下级别。
  
|**级别 1：业务价值较低**|**级别 2：业务价值中等**|**级别 3：业务价值较高**|
|:-----|:-----|:-----|
|数据已加密，并且仅供已通过身份验证的用户使用

  <br/> 向存储在本地和基于云的存储空间和工作负载（例如 Office 365）中的所有数据提供。驻留在服务中和在服务与客户端设备之间传输时，数据处于加密状态。  <br/> 1 级数据的示例为正常的业务通信（电子邮件）和供管理、销售和支持工作人员使用的文件。  <br/> |1 级再加上强身份验证和数据丢失防护
  <br/> 强身份验证包括具有 SMS 验证的多重身份验证。数据丢失防护确保敏感或关键的信息不会在本地网络以外出现。
  <br/> 2 级数据的示例包括财务和法律信息，以及新产品的研发数据。  <br/> |2 级再加上最高级别的加密、身份验证和审核
  <br/> 对静态和云中的数据采用最高级别的加密，遵循区域法规，并结合具有智能卡以及精细审核和警报的多重身份验证。
  <br/> 3 级数据的示例是客户和合作伙伴的个人身份信息、产品工程规范以及专有的制造技术。  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a>映射到 Contoso 的数据级别的 Microsoft 云服务和功能

下表显示 Contoso 的数据级别在 Microsoft 的云产品功能中的映射：
  
||**SaaS**|**Azure PaaS**|**Azure IaaS**|
|:-----|:-----|:-----|:-----|
|级别 1：业务价值较低  <br/> | 所有连接的 HTTPS
 <br/>  静态加密 <br/> | 仅支持 HTTPS 连接
 <br/>  加密存储在 Azure 中的文件 <br/> | 需要 HTTPS 或 IPsec 进行服务器访问
 <br/>  Azure 磁盘加密 <br/> |
|级别 2：业务价值中等  <br/> | 具有 SMS 的 Azure AD 多重身份验证 (MFA) <br/> | 用于加密密钥的 Azure 密钥保管库
 <br/>  具有 SMS 的 Azure AD MFA <br/> | 具有 SMS 的 MFA <br/> |
|级别 3：业务价值较高  <br/> | Azure 权限管理系统 (RMS)

 <br/>  具有智能卡的 Azure AD MFA <br/>  Intune 条件访问 <br/> | Azure RMS <br/>  具有智能卡的 Azure AD MFA <br/> | 具有智能卡的 MFA <br/> |
   
## <a name="contosos-information-policies"></a>Contoso 的信息策略

下表列出了 Contoso 的信息策略。
  
||**访问**|**数据保留**|**信息保护**|
|:-----|:-----|:-----|:-----|
|级别 1：业务价值较低  <br/> | 允许访问所有 <br/> |6 个月  <br/> |使用加密  <br/> |
|级别 2：业务价值中等  <br/> | 允许访问 Contoso 员工、分包商和合作伙伴
 <br/>  使用 MFA、TLS 和 MAM <br/> |2 年  <br/> |使用哈希值实现数据完整性  <br/> |
|级别 3：业务价值较高  <br/> | 允许访问工程设计和制造中的执行人员和潜在客户
 <br/>  仅具有托管网络设备的 RMS <br/> |7 年  <br/> |使用数字签名实现不可否认性  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a>云安全准备 Contoso 的路径

Contoso 使用以下步骤为 Microsoft 云安全做准备：
  
1. 优化云的管理员帐户

    
    Contoso 对现有的 Windows Sever AD 管理员帐户进行了广泛审阅，并设置了一系列的云管理员帐户和组。
    
2. 按三个级别执行数据分类分析

    
    Contoso 执行进行仔细检查并确定的三个级别，用于确定 Microsoft 云提供功能，以保护 Contoso 最有价值的数据。
    
3. 确定数据级别的访问策略、保留策略和信息保护策略

    
    Contoso 已根据数据级别确定将用于限定转移到云的未来 IT 工作负载的详细要求。
    
## <a name="contosos-use-of-office-365-security-best-practices"></a>Contoso 的使用的 Office 365 安全性最佳实践

按照 Office 365 安全性最佳实践，Contoso 的安全管理员和 IT 部门已部署以下：
  
- **专用非常强密码的全局管理员帐户**
    
    而不是全局管理员角色分配日常的用户帐户，Contoso 具有创建三个，专用非常强密码的全局管理员帐户。有关特定的管理任务只进行登录时的全局管理员帐户和密码仅已知到指定的人员。Contoso 的安全管理员已分配给适用于 IT 人作业功能和责任的帐户的管理员角色。
    
    有关详细信息，请参阅[有关 Office 365 管理员角色](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)。
    
- **重要的用户帐户的多因素身份验证 (MFA)**
    
    MFA 通过要求用户确认电话呼叫、 短信或其智能电话上正确输入自己的密码后应用程序通知向登录过程额外的保护程序。MFA，与 Office 365 用户帐户会受到未授权登录即使帐户密码受到威胁。
    
  - 防止 Office 365 订阅的泄露，Contoso 上所有三个全局管理员帐户启用 MFA。
    
  - 保护网络钓鱼攻击，攻击损害组织中的受信任的个人的凭据，并发送恶意电子邮件，Contoso MFA 上启用所有用户帐户管理者，包括主管人员。
    
    有关详细信息，请参阅[规划的 Office 365 部署的多因素身份验证](https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)
    
- **高级的安全管理 (ASM)**
    
    ASM 使用配置策略以监视异常活动。Contoso 安全管理员设置与 ASM 通知，使 IT 管理员通知的不寻常或 risky 用户活动，如下载大量数据，多失败尝试登录时或登录来自未知或危险 IP 地址
    
    有关详细信息，请参阅[概述的高级安全管理 Office 365 中](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)。
    
- **安全电子邮件流和邮箱审核日志记录**
    
    Contoso 安全专家将 Exchange Online Protection 和高级威胁保护 (ATP) 防御未知的恶意软件、 病毒和恶意通过电子邮件传输的 Url。Contoso 也有启用的邮箱审核日志来确定用户登录用户邮箱发送的邮件，和邮箱所有者、 委派的用户或管理员执行的其他活动。
    
    有关详细信息，请参阅： 
    
  - [Office 365 电子邮件反垃圾邮件保护](https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586)
    
  - [安全附件和安全链接的高级威胁保护](https://technet.microsoft.com/library/mt148491.aspx)
    
  - [在 Office 365 中启用邮箱审核](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- **数据丢失防护 (DLP)**
    
    Contoso 具有标识其敏感数据，并配置了 Exchange Online、 SharePoint Online 和 OneDrive 有助于防止用户无意或有意共享数据的 DLP 策略。 
    
    有关详细信息，请参阅[数据丢失防护策略概述](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)。
    
## <a name="see-also"></a>See Also

[Microsoft 云中的 Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft 云 IT 体系结构资源](microsoft-cloud-it-architecture-resources.md)

[Microsoft 企业云路线图：IT 决策者的资源](https://sway.com/FJ2xsyWtkJc2taRD)
  
[Office 365 的安全最佳做法](https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3)




