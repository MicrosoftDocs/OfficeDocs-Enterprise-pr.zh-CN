---
title: Office 365 中的管理访问权限
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: 使用本主题可了解有关 Office 365 中的访问权限的管理功能的详细信息
ms.openlocfilehash: b2db3e16e53cca7deb2bf8fbff61b5b981f42fa6
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319203"
---
# <a name="privileged-access-management-in-office-365"></a>Office 365 中的管理访问权限

> [!IMPORTANT]
> 本主题介绍了部署和配置指南 public beta 功能仅当前 Office 365 E5 和高级合规性 Sku 中可用。

特权访问管理 Office 365 中允许精细的访问控制拥有权限的管理员任务。 它可以帮助保护您的组织可以使用现有拥有权限的管理员帐户所访问敏感数据或关键的配置设置的访问权限的破坏。启用访问权限的管理后, 用户将需要请求中实时访问完成审批工作流高度范围和限制时间内通过提升和特权任务。这使用户刚刚-足够-访问执行的任务，而冒泄露敏感数据或关键的配置设置。启用访问权限的管理 Office 365 中将启用您的组织具有零个位置权限并提供防御下，因为此类所管理的访问权限的安全漏洞的层。 

本主题将指导您完成启用和配置 Office 365 组织中的访问权限的管理并充当参考指南请求、 批准，和管理功能。 

## <a name="before-you-begin"></a>准备工作

### <a name="limited-functionality"></a>有限的功能
期间公开 beta 版，特权访问管理功能才可用通过 Office 365 中的[Exchange Online PowerShell 中](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps)。管理介绍 Exchange 管理 cmdlet 级别的任务定义访问权限。在将来 Office 365 的版本，功能可通过管理门户，并将涵盖其他 Office 365 工作负荷服务授权的访问权限。

### <a name="connecting-to-exchange-online-powershell"></a>连接到 Exchange Online PowerShell 中
本主题中的配置步骤将指导您启用并使用 Exchange Online PowerShell 中的 Office 365 中使用授权访问权限。 

按照[连接到 Exchange Online PowerShell 中使用多因素身份验证](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps)连接到 Exchange Online PowerShell 中使用您的 Office 365 凭据启用和配置特权的访问您的组织中的步骤。

> [!NOTE]
> 不需要启用多重身份验证您的 Office 365 组织使用的步骤同时连接到 Exchange Online PowerShell 中启用访问权限。将与多因素身份验证连接创建由授权的访问权限，登录您的请求的 OAuth 令牌。

## <a name="enable-and-configure-privileged-access-management"></a>启用和配置访问权限的管理

### <a name="step-1---create-an-approvers-group"></a>步骤 1-创建审批者组
从 Office 365 管理门户，选择**组** > **添加组**，然后为特权的默认访问审批者创建启用邮件的安全组。完成后，选择**添加**来创建和保存审批者组。

![访问权限的 Office 365 管理门户中的审批者屏幕](images/privileged-access-approvers-ui.png)

> [!NOTE] 
> 此时，允许仅具有管理访问权限的用户批准来自 Office 365 特权访问请求。在将来的审批者的组的一部分的任何用户都将能够批准访问请求。

### <a name="step-2---enable-privileged-access-in-office-365"></a>步骤 2-启用 Office 365 中的授权访问权限
需要显式打开与默认审批者组和包括要排除的访问权限的管理访问控制从系统帐户的一组访问权限。 

若要启用访问权限，并将审批者的组分配 Exchange Online PowerShell 中运行以下命令：
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
示例：
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> 系统帐户由可用于确保组织内的特定自动化功能可以处理不依赖项的情况下访问权限，但建议的此类排除在极那些允许应核准和审核定期。

### <a name="step-3---create-an-approval-policy"></a>步骤 3-创建审批策略
审批策略允许您定义的范围限制在各项任务的特定审批要求。**自动**或**手动**了审批类型选项。 

运行以下命令在 Exchange Online PowerShell，可以定义一个审批策略：
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
示例：
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a>在 Office 365 组织中使用授权访问权限

### <a name="requesting-elevation-authorization-to-execute-tasks"></a>请求提升授权能够执行任务
启用之后，特权访问需要执行任何任务已定义的关联的审批策略审批。无需执行中包含的任务的用户的审批策略必须请求，并让执行任务所需的权限授予访问审核。

运行以下命令在 Exchange Online PowerShell 来创建和提交给审批者的组的审批请求：
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
示例：
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a>查看提升请求的状态
创建审批请求后，可以使用请求 ID 关联审阅提升请求状态

运行以下命令在 Exchange Online PowerShell，可以查看特定的请求 ID 审批请求状态：
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
示例：
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>批准提升授权请求
当创建审批请求时，相关的审批者组的成员将收到的电子邮件通知和可以批准请求 ID 与关联的请求 

运行以下命令在 Exchange Online PowerShell 批准提升授权请求：
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
示例：
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a>拒绝提升授权请求
当创建审批请求时，相关的审批者组的成员可以拒绝请求 ID 与关联的请求 

运行以下命令在 Exchange Online PowerShell 拒绝提升授权请求：
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
示例：
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a>运行任务
授予审批后，请求的用户可以执行预期的任务并特权的 access 将授权，并对代表用户执行任务。审批保持有效的请求持续时间 （默认持续时间是 4 个小时），在此期间请求者可以预期的任务多次执行。所有此类执行的记录，并使其可供安全性和合规性审核。 

### <a name="disable-privileged-access-in-office-365"></a>禁用 Office 365 中的特权的访问
如果需要您可以禁用 Office 365 中的访问权限的管理。禁用权限访问不会删除任何关联的审批策略或审批者组。

运行以下命令在 Exchange Online Powershell，可以禁用授权访问权限：

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a>管理 Microsoft Azure 中的 Microsoft Graph 访问

> [!IMPORTANT]
> 本节介绍用于公开 beta 版的 Microsoft Graph 功能仅当前 Office 365 E5 和高级合规性 Sku 中可用的部署和配置指南。

到 Microsoft Azure 中的 Microsoft Graph 托管的 access 是一种服务，可帮助组织施加控制其 Office 365 数据粒度级别。此系统允许应用程序开发人员伪造见解与该数据。 

此系统使用 Office 365 特权访问断言控制通过其审批工作流，并允许 Office 365 管理员监督数据范围的访问其数据。应用程序安装后，需要访问 Office 365 数据的数据的请求进入。

### <a name="view-request-details"></a>查看请求的详细信息
查看 Office 365 数据访问请求的详细信息。

运行以下命令在 Exchange Online Powershell，可以查看数据请求：
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
示例输出：
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a>批准数据访问请求
可以通过标准的特权的访问审批 cmdlet 审核所有数据访问请求。

运行以下命令在 Exchange Online Powershell，可以为特定的请求者批准所有数据请求：

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
示例：
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a>获取帮助，并提供反馈
但我们知道期间 public beta 您可能会遇到偶尔 bug 或有反馈和如何改进访问权限的管理的建议。我们将您的反馈，并鼓励您共享与我们：
- [Office 预览 Yammer 组](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206)中发布您的反馈 ad 建议。
- 文件 bug 报表区域路径"Office 365 特权访问管理"下[Office 预览 VSO](https://office-previews.visualstudio.com/previews)上。

## <a name="frequently-asked-questions"></a>常见问题

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a>使用 Office 365 中的访问权限时，需要哪些 Sku？
特权访问 Office 365 中的管理是当前仅适用于以 E5 和高级合规性 Sku 客户。

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a>何时适用于 Office 365 工作负载超过 Exchange 访问权限？
我们计划推出提供此功能的其他 Office 365 工作负载。我们准备好共享一个日程表，它将提供通过 Office 365 路线图。

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a>如何这是不同 Azure Active Directory 特权身份管理的？
在不同的范围中实时访问 Office 365 和[Azure AD 特权身份管理](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)补充通过提供访问每个其他控件中的管理访问权限。共同它们提供强大的一组控件用于保护数据。

特权访问 Office 365 中的管理可以定义和时角色级别应用能够执行多个任务的 Azure AD 特权标识管理任务级别范围。 Azure AD 特权身份管理主要允许管理 AD 角色和特权时的角色组的访问 Office 365 中的访问管理应用于任务级别。

 - **启用特权已在使用 Azure AD 特权身份管理时，访问 Office 365 中的管理：** Office 365 中添加特权的访问管理可以提供其他粒度层保护并审核功能特权访问 Office 365 数据。

- **启用 Azure AD 特权时已使用的身份管理特权访问管理 Office 365 中：** 向特权特权 Azure AD 身份管理 Office 365 中的访问管理可以扩展特权的访问由用户的角色或标识主要定义的 Office 365 以外的数据。 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>是否需要为全局管理员管理 Office 365 中的授权访问权限？
在预览期间，您需要具有能够管理特权的访问 Office 365 中的全局管理员特权。包括在审批者组中的用户不需要是全局管理员才能查看和批准请求。 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a>是与客户密码箱的 Office 365 中的访问权限的管理如何？
[客户密码箱](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2)允许访问由其服务提供商，即 Microsoft 的数据的组织的访问控制的级别。特权访问 Office 365 中的管理允许的所有特权的 Office 365 任务组织内的精细的访问控制。