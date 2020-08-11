---
title: Microsoft 365 技术控件
ms.author: josephd
author: JoeDavies-MSFT
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
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: 本文概述了 microsoft 365 中 Microsoft 的技术控制使用的工具和技术。
ms.openlocfilehash: 4944fcdac1142344178d289be1e5699b80b47683
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606268"
---
# <a name="microsoft-365-technology-controls"></a>Microsoft 365 技术控件 

Microsoft 使用多种工具和技术来控制、管理和审核对其在线服务中的客户数据的访问。 这些应用于 Exchange Online、SharePoint Online、密码箱和客户密码箱、多重身份验证等。 Yammer 使用[Yammer Enterprise Access 控件](office-365-yammer-enterprise-access-controls.md)中所述的类似控件。

Microsoft 365 工程师对 Microsoft 365 客户数据具有零的访问权限。 在访问客户数据以进行服务操作之前，工程师必须先完成 Microsoft 审批流程。 如果客户对 Exchange Online 和 SharePoint Online 的客户密码箱功能进行了授权，则对客户数据的访问需要客户审批。 经过批准后，特定于服务的管理帐户将为服务请求所需的任务预配实时访问。

## <a name="lockbox-and-customer-lockbox"></a>密码箱和客户密码箱

虽然极少数情况下，客户可以从 Microsoft 向 Microsoft 工程师公开客户内容的帮助。 为了控制对 Exchange Online 的访问，Microsoft 使用名为 "密码箱" 的访问控制系统。 在 Microsoft 工程师访问任何 Exchange Online 或 SharePoint Online 系统或数据之前，必须使用密码箱提交访问请求。 Exchange Online 和 SharePoint Online 的所有服务请求都由密码箱系统处理。 通过密码箱和客户密码箱，所有批准的访问都可对唯一用户进行跟踪，使工程师对客户数据的处理负责。

> [!NOTE]
> Exchange Online 包括存储在用户邮箱中的任何 Skype for Business 数据。 Skype for business 覆盖范围不包括 Skype 会议广播录制或用户上载到会议的内容。 SharePoint Online 包括 OneDrive for Business。

密码箱处理授予工程师在服务中执行操作和管理功能的能力的权限请求。 工程师通过密码箱提交请求，Microsoft 管理员必须先批准请求，然后工程师才能访问客户数据。 在经理批准后，工程师对客户数据具有受时间限制和范围限制的访问权限，以处理客户问题。

Microsoft 365 的客户密码箱可帮助您满足法规遵从性义务（如果您需要实现显式数据访问授权的过程）。 这是对某些合规性标准（如 FedRAMP 和 HIPAA）的要求。 客户密码箱将你插入密码箱审批过程，并为你提供控制 Microsoft access 对 Exchange Online 或 SharePoint Online 内容的授权，以进行服务操作。

在 Microsoft 服务工程师需要访问您的数据时，在极少数的实例中，仅授予对解决问题所需的数据的访问权限以及有限的时间。 如果拒绝访问请求，Microsoft 工程师将无法访问你的内容，并且无法完成服务操作。 如果你批准请求，Microsoft 工程师通过受监控和约束的管理界面来限制你的内容的实时访问。

支持工程师采取的操作是出于审核目的而记录的，可通过[Office 365 管理活动 API](https://docs.microsoft.com/office/office-365-management-api/get-started-with-office-365-management-apis)和[安全与合规中心](https://protection.office.com/)进行访问。

>[!NOTE]
> 客户密码箱在[Microsoft 365 E5](https://products.office.com/business/office-365-enterprise-e5-business-software)中作为附加购买版提供。 有关详细信息，请参阅[Microsoft 365 客户密码箱请求](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2)。

## <a name="just-in-time-access"></a>实时访问

Microsoft 使用 Microsoft 365 的实时 (JIT) 访问原则来缓解凭据篡改风险和横向攻击。 JIT 可删除服务的持久管理访问权限，并将权限替换为根据需要提升为这些角色。 从管理员删除永久访问权限可确保凭据仅在需要时才可用，并可降低凭据窃取风险。

JIT 访问模型要求工程师在有限的时段内请求提升的权限，以执行管理任务。 此外，工程师使用使用计算机生成的复杂密码创建的临时帐户，并只授予那些允许他们执行必要任务的角色。 例如，由密码箱授予的管理访问权限是受时间限制的，并且访问权限的时间量取决于请求的角色。 工程师指定对密码箱系统的请求中所需的时间访问的持续时间。 当请求的时间超过提升的最长允许时间时，密码箱系统会拒绝请求。 过期后，将删除管理访问权限，并且临时帐户将过期。

当授权和批准访问时，工程师将收到由授权系统生成的一次性管理密码。 每次批准请求提升访问权限时，都会生成新密码。 密码将被复制到密码安全，与工程师为 Microsoft 公司环境的凭据分开，且仅适用于已批准的提升的访问会话。

## <a name="constrained-management-interfaces"></a>受约束的管理接口

工程师使用两个管理界面执行管理任务：通过安全的终端服务网关 (TSGs) 和远程 PowerShell 执行的远程桌面。 在这些管理界面中，软件策略和访问控制对所执行的应用程序以及可用的命令和 cmdlet 施加了很大的限制。

Microsoft 365 服务器将并发会话限制为每个服务的团队管理员，每个服务器一个会话。 TSGs 仅允许用户单个并发会话，不允许多个会话。 通过对每个服务器使用一个会话，TSGs 允许 Microsoft 365 服务团队管理员同时连接到多台服务器，以便管理员能够有效地执行其职责。 服务团队管理员对 TSGs 本身没有任何权限。 TSG 仅用于强制执行多重身份验证 (MFA) 和加密要求。 一旦服务团队管理员通过 TSG 连接到特定服务器，则该特定服务器会强制每个管理员一个会话限制为一个。

Microsoft 365 人员的使用限制和连接和配置要求由 Active Directory 组策略建立。 这些策略包括以下特征：

- TSGs 仅使用[FIPS](https://www.microsoft.com/TrustCenter/Compliance/FIPS) 140-2 验证的加密。
- 在30分钟不活动后断开的 TSG 会话。
- 在24小时后，TSG 会话将自动注销。

与 TSGs 的连接还需要使用单独的物理智能卡和帐户（与工程师的 Microsoft 公司凭据分开）进行 MFA。 为各种平台和机密管理平台颁发不同的智能卡的工程师可确保凭据的安全存储。 TSGs 使用 Active Directory 组策略来控制谁可以登录到远程服务器、允许的会话数和空闲超时设置。 其他策略将限制对允许的应用程序的访问，并限制 Internet 访问。

除了使用巧尽心思配置的 TSGs 的远程访问之外，Exchange Online 还允许具有服务工程师操作角色的用户使用远程 PowerShell 访问生产服务器上的特定管理功能。 若要执行此操作，必须向用户授予只读 (debug) 对 Microsoft 365 生产环境的访问权限。 启用权限提升的方式与使用密码箱进程为 TSGs 启用权限的方式相同。

对于远程访问，每个数据中心都有一个负载平衡的虚拟 IP，用作单一访问点。 可用的远程 PowerShell cmdlet 基于身份验证期间获取的访问声明中标识的权限级别。 这些 cmdlet 仅提供使用此方法进行连接的用户可访问的唯一管理功能。 远程 PowerShell 限制可用于工程师的命令的范围，并基于通过密码箱进程授予的访问级别。 例如，在 Exchange Online 中，可以使用 "获取邮箱"，但将 "邮箱" 设置为 "邮箱"。
