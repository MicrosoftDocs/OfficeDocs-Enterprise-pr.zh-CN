---
title: Microsoft 365 中的管理访问控制
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- NOCSH
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom: seo-marvel-apr2020
description: 本文提供了 Microsoft 365 中的管理访问控制和数据分类的概述。
ms.openlocfilehash: 58cbc7ebea3edb66f5d48d282a3e6995b247a044
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606708"
---
# <a name="administrative-access-controls-in-microsoft-365"></a>Microsoft 365 中的管理访问控制 

Microsoft 已在系统和控件中进行了大量投资，以自动化 microsoft 365 的大多数操作，同时有意限制 Microsoft 对客户内容的访问。 人类控制服务，软件运行服务。 这使 Microsoft 能够在规模扩展时管理 Microsoft 365，并管理对客户内容的内部威胁的风险。

默认情况下，Microsoft 工程师拥有零的管理权限，并在 Microsoft 365 中提供对客户内容的零访问权限。 Microsoft 工程师可在有限的时间段中对客户的内容进行有限的审核和安全访问。 只有在服务操作必要时才进行访问，并且仅当由 Microsoft 高级管理的成员批准时才能访问。 对于客户密码箱许可的客户，客户提供对其在 Microsoft 365 上托管的内容的访问审批。

Microsoft 使用多种形式的云传递提供了在线服务：

- **公共云：** 包括在北美、南美洲、欧洲、亚洲、澳大利亚等托管的 Microsoft 365、Azure 和其他服务的多租户版本。
- **国家/地区云：** 包括 (美国以外的所有 sovereign 和第三方运营云，除了之前) 之外的所有和第三方运行的云（如中国 () 运营的中国 365 Microsoft 365）和德语中的 Microsoft (由 Microsoft 运营，但在一种模型中，在德语数据受信者、德国电信中，控制并监控 Microsoft 对包含客户数据) 的客户数据
- **政府群：** 包含适用于美国政府客户的 Microsoft 365 和 Azure 服务。

出于本文的目的，Microsoft 365 服务包括：

- [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online)
- [Exchange Online Protection](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [SharePoint Online](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [OneDrive for Business](https://docs.microsoft.com/OneDrive/onedrive)
- [Skype for Business](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [Yammer](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="microsoft-365-access-controls"></a>Microsoft 365 访问控制

出于访问控制目的，Microsoft 将 Microsoft 365 数据分类为客户数据或其他类型的数据。

### <a name="customer-data"></a>客户数据

客户数据是在使用 Microsoft 365 服务时代表客户提供或代表客户提供的所有数据。 这是由 Microsoft 365 用户直接创建或上载的客户内容，包括：

- 电子邮件
- SharePoint Online 内容
- 即时消息
- 日历项目
- 文档
- 联系人
- 最终用户可识别的信息 (EUII) 用户特有或 linkable 给个人用户但不包含客户内容的数据 (数据) 

### <a name="other-types-of-data"></a>其他类型的数据

其他类型的数据包括：

- **帐户数据：** 包括管理员在注册或购买服务) 时提供的管理数据 (信息，以及付款数据 (有关付款仪器的信息，如信用卡详细信息) 。
- **组织的可识别信息：** 包含用于标识租户、使用情况数据，而不是 linkable 给个人用户或包含在客户内容中的数据。
- **系统元数据：** 包括包含配置设置、系统状态、Microsoft IP 地址和订阅和租户的技术信息的服务日志。

Microsoft 已建立了访问控制机制，以确保没有人撤销对客户数据或访问控制数据的访问权限。 访问控制数据管理对环境中其他类型的数据或函数的访问，包括对客户内容或 EUII、Microsoft 密码、安全证书和其他与身份验证相关的数据的访问。 访问控制机制还可防止对 Microsoft 365 生产环境进行未批准的物理、逻辑或远程访问。

Microsoft 为 microsoft 365 提供了三种访问控制类别：

- 隔离控件
- 人员控制
- 技术控制

结合后，这些控制措施有助于防止和检测 Microsoft 365 中的恶意操作。 除了 Microsoft 使用的隔离、人员和技术控件之外，还有第四个类别的控件：由客户实施的控件。

Microsoft 365 允许您以与在本地环境中管理数据的方式管理数据。 将组织注册为 Microsoft 365 的人员将自动成为全局管理员。 全局管理员可以访问管理门户中的所有功能，并且可以：

- 创建或编辑用户
- 向其他人分配管理员角色
- 重置用户密码
- 管理用户许可证
- 管理域
- 批准客户密码箱请求

建议每个组织至少配置两个管理员帐户。 对于大型企业组织，我们建议专门的管理员帐户来提供不同的功能。

有关分配管理员角色和权限的信息，请参阅[分配管理员角色](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles)和[关于管理员角色](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles)。

## <a name="related-links"></a>相关链接

- [隔离控件](office-365-isolation-controls.md)
- [人员控制](office-365-personnel-controls.md)
- [技术控制](office-365-technology-controls.md)
- [监视和审核访问控制](office-365-monitoring-and-auditing-access-controls.md)
- [Yammer Enterprise 访问控制](office-365-yammer-enterprise-access-controls.md)