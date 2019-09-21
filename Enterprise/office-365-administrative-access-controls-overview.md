---
title: Office 365 中的管理访问控制
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 摘要： Office 365 的管理访问控制和数据分类概述。
ms.openlocfilehash: e8cc470c617deea7435841f276b772b0a8ef17a3
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067259"
---
# <a name="administrative-access-controls-in-office-365"></a>Office 365 中的管理访问控制 

Microsoft 已在系统和控件中进行了大量投资，以自动化大多数 Office 365 操作，同时有意限制 Microsoft 对客户内容的访问权限。 人类控制服务，软件运行服务。 这使 Microsoft 能够在规模扩展时管理 Office 365，并管理对客户内容的内部威胁的风险。

By default, Microsoft engineers have zero standing administrative privileges and zero standing access to customer content in Office 365. Microsoft 工程师可在有限的时间段中对客户的内容进行有限的审核和安全访问。 只有在服务操作必要时才进行访问，并且仅当由 Microsoft 高级管理的成员批准时才能访问。 对于客户密码箱许可的客户，客户将提供对 Office 365 上托管内容的访问审批。

Microsoft 使用多种形式的云传递提供了在线服务：

- **公共云：** 包括在北美、南美洲、欧洲、亚洲、澳大利亚等托管的 Office 365、Azure 和其他服务的多租户版本。
- **国家/地区云：** 包括美国以外的所有 sovereign 和第三方运营云（前面提到的云除外），例如中国（由世纪互联运营）的 Office 365 和德国的 Office 365 （由 Microsoft 使用，但在一个采用德语数据受托者的模型下）。德国电信，控制和监控 Microsoft 对客户数据和包含客户数据的系统的访问。
- **政府群：** 包含适用于美国政府客户的 Office 365 和 Azure 服务。

出于本文的目的，Office 365 服务包括：

- [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online)
- [Exchange Online Protection](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [SharePoint Online](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [OneDrive for Business](https://docs.microsoft.com/OneDrive/onedrive)
- [Skype for Business](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [Yammer](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a>Office 365 访问控制

出于访问控制目的，Microsoft 将 Office 365 数据分类为客户数据或其他类型的数据。

### <a name="customer-data"></a>客户数据

客户数据是使用 Office 365 服务时代表客户提供或代表客户提供的所有数据。 这是由 Office 365 用户直接创建或上载的客户内容，包括：

- 电子邮件
- SharePoint Online 内容
- 即时消息
- 日历项目
- Documents
- 联系人
- 最终用户身份信息（EUII）（对用户而言是唯一的，或对单个用户而言是 linkable 但不包含客户内容的数据）。

### <a name="other-types-of-data"></a>其他类型的数据

其他类型的数据包括：

- **帐户数据：** 包括管理数据（管理员在注册或购买服务时提供的信息）和付款数据（有关付款仪器的信息，如信用卡详细信息）。
- **组织的可识别信息：** 包含用于标识租户、使用情况数据，而不是 linkable 给个人用户或包含在客户内容中的数据。
- **系统元数据：** 包括包含配置设置、系统状态、Microsoft IP 地址和订阅和租户的技术信息的服务日志。

Microsoft 已建立了访问控制机制，以确保没有人撤销对客户数据或访问控制数据的访问权限。 访问控制数据管理对环境中其他类型的数据或函数的访问，包括对客户内容或 EUII、Microsoft 密码、安全证书和其他与身份验证相关的数据的访问。 访问控制机制还可防止对 Office 365 生产环境进行未批准的物理、逻辑或远程访问。

Microsoft 使用的 access 控件有三个类别，用于运行 Office 365：

- 隔离控件
- 人员控制
- 技术控制

组合后，这些控件有助于防止和检测 Office 365 中的恶意操作。 除了 Microsoft 使用的隔离、人员和技术控件之外，还有第四个类别的控件：由客户实施的控件。

Office 365 允许您以与在本地环境中管理数据的方式管理数据。 注册 Office 365 组织的人员将自动成为全局管理员。 全局管理员可以访问管理门户中的所有功能，并且可以：

- 创建或编辑用户
- 向其他人分配管理员角色
- 重置用户密码
- 管理用户许可证
- 管理域
- 批准客户密码箱请求

建议每个组织至少配置两个管理员帐户。 对于大型企业组织，我们建议专门的管理员帐户来提供不同的功能。

有关分配管理员角色和权限的信息，请参阅[在 office 365 中分配管理员角色](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504)和[关于 Office 365 管理员角色](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D)。

## <a name="related-links"></a>相关链接

- [隔离控件](office-365-isolation-controls.md)
- [人员控制](office-365-personnel-controls.md)
- [技术控制](office-365-technology-controls.md)
- [监视和审核访问控制](office-365-monitoring-and-auditing-access-controls.md)
- [Yammer Enterprise访问控制](office-365-yammer-enterprise-access-controls.md)