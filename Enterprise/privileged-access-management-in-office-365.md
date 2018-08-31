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
search.appverid:
- MET150
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: 使用本主题可了解有关 Office 365 中的访问权限的管理功能的详细信息
ms.openlocfilehash: 22286d4f91ffa0bd3c49f028681d20e36d14283d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915387"
---
# <a name="privileged-access-management-in-office-365"></a><span data-ttu-id="659bc-103">Office 365 中的管理访问权限</span><span class="sxs-lookup"><span data-stu-id="659bc-103">Privileged access management in Office 365</span></span>

> [!IMPORTANT]
> <span data-ttu-id="659bc-104">本主题介绍了部署和配置指南 public beta 功能仅当前 Office 365 E5 和高级合规性 Sku 中可用。</span><span class="sxs-lookup"><span data-stu-id="659bc-104">This topic covers deployment and configuration guidance for public beta features only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="659bc-p101">特权访问管理 Office 365 中允许精细的访问控制拥有权限的管理员任务。 它可以帮助保护您的组织可以使用现有拥有权限的管理员帐户所访问敏感数据或关键的配置设置的访问权限的破坏。启用访问权限的管理后, 用户将需要请求中实时访问完成审批工作流高度范围和限制时间内通过提升和特权任务。这使用户刚刚-足够-访问执行的任务，而冒泄露敏感数据或关键的配置设置。启用访问权限的管理 Office 365 中将启用您的组织具有零个位置权限并提供防御下，因为此类所管理的访问权限的安全漏洞的层。</span><span class="sxs-lookup"><span data-stu-id="659bc-p101">Privileged access management allows granular access control over privileged admin tasks in Office 365.  It can help protect your organization from breaches that may use existing privileged admin accounts with standing access to sensitive data or access to critical configuration settings. After enabling privileged access management, users will need to request just-in-time access to complete elevated and privileged tasks through an approval workflow that is highly scoped and time-bound. This gives users just-enough-access to perform the task at hand, without risking exposure of sensitive data or critical configuration settings. Enabling privileged access management in Office 365 will enable your organization to operate with zero standing privileges and provide a layer of defense against vulnerabilities arising because of such standing administrative access.</span></span> 

<span data-ttu-id="659bc-110">本主题将指导您完成启用和配置 Office 365 组织中的访问权限的管理并充当参考指南请求、 批准，和管理功能。</span><span class="sxs-lookup"><span data-stu-id="659bc-110">This topic will guide you through enabling and configuring privileged access management in your Office 365 organization and serve as a reference guide for requesting, approving, and managing the feature.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="659bc-111">准备工作</span><span class="sxs-lookup"><span data-stu-id="659bc-111">Before you begin</span></span>

### <a name="limited-functionality"></a><span data-ttu-id="659bc-112">有限的功能</span><span class="sxs-lookup"><span data-stu-id="659bc-112">Limited functionality</span></span>
<span data-ttu-id="659bc-p102">期间公开 beta 版，特权访问管理功能才可用通过 Office 365 中的[Exchange Online PowerShell 中](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps)。管理介绍 Exchange 管理 cmdlet 级别的任务定义访问权限。在将来 Office 365 的版本，功能可通过管理门户，并将涵盖其他 Office 365 工作负荷服务授权的访问权限。</span><span class="sxs-lookup"><span data-stu-id="659bc-p102">During the public beta, privileged access management features are only available through [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Privileged access management covers the task definitions at the level of Exchange management cmdlets. In future Office 365 releases, privileged access features will be available through the admin portal and will cover other Office 365 workloads services.</span></span>

### <a name="connecting-to-exchange-online-powershell"></a><span data-ttu-id="659bc-116">连接到 Exchange Online PowerShell 中</span><span class="sxs-lookup"><span data-stu-id="659bc-116">Connecting to Exchange Online PowerShell</span></span>
<span data-ttu-id="659bc-117">本主题中的配置步骤将指导您启用并使用 Exchange Online PowerShell 中的 Office 365 中使用授权访问权限。</span><span class="sxs-lookup"><span data-stu-id="659bc-117">The configuration steps in this topic will walk you through enabling and using privileged access in Office 365 using Exchange Online PowerShell.</span></span> 

<span data-ttu-id="659bc-118">按照[连接到 Exchange Online PowerShell 中使用多因素身份验证](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps)连接到 Exchange Online PowerShell 中使用您的 Office 365 凭据启用和配置特权的访问您的组织中的步骤。</span><span class="sxs-lookup"><span data-stu-id="659bc-118">Follow the steps in [Connect to Exchange Online PowerShell using Multi-Factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) to connect to Exchange Online PowerShell with your Office 365 credentials to enable and configure privileged access for your organization.</span></span>

> [!NOTE]
> <span data-ttu-id="659bc-p103">不需要启用多重身份验证您的 Office 365 组织使用的步骤同时连接到 Exchange Online PowerShell 中启用访问权限。将与多因素身份验证连接创建由授权的访问权限，登录您的请求的 OAuth 令牌。</span><span class="sxs-lookup"><span data-stu-id="659bc-p103">You do not need to enable multi-factor authentication for your Office 365 organization to use the steps to enable privileged access while connecting to Exchange Online PowerShell. Connecting with multi-factor authentication creates an OAuth token that is used by privileged access for signing your requests.</span></span>

## <a name="enable-and-configure-privileged-access-management"></a><span data-ttu-id="659bc-121">启用和配置访问权限的管理</span><span class="sxs-lookup"><span data-stu-id="659bc-121">Enable and configure privileged access management</span></span>

### <a name="step-1---create-an-approvers-group"></a><span data-ttu-id="659bc-122">步骤 1-创建审批者组</span><span class="sxs-lookup"><span data-stu-id="659bc-122">Step 1 - Create an approver's group</span></span>
<span data-ttu-id="659bc-p104">从 Office 365 管理门户，选择**组** > **添加组**，然后为特权的默认访问审批者创建启用邮件的安全组。完成后，选择**添加**来创建和保存审批者组。</span><span class="sxs-lookup"><span data-stu-id="659bc-p104">From Office 365 Admin Portal, select **Groups** > **Add a group**, then create a mail enabled security group for the default privileged access approvers. When complete, select **Add** to create and save the approver group.</span></span>

![访问权限的 Office 365 管理门户中的审批者屏幕](media/privileged-access-approvers-ui.png)

> [!NOTE] 
> <span data-ttu-id="659bc-p105">此时，允许仅具有管理访问权限的用户批准来自 Office 365 特权访问请求。在将来的审批者的组的一部分的任何用户都将能够批准访问请求。</span><span class="sxs-lookup"><span data-stu-id="659bc-p105">At this time, only users with administrative access are allowed to approve requests from Office 365 priviledged access. In future any user who is part of the Approvers’ group will be able to approve access requests.</span></span>

### <a name="step-2---enable-privileged-access-in-office-365"></a><span data-ttu-id="659bc-128">步骤 2-启用 Office 365 中的授权访问权限</span><span class="sxs-lookup"><span data-stu-id="659bc-128">Step 2 - Enable privileged access in Office 365</span></span>
<span data-ttu-id="659bc-129">需要显式打开与默认审批者组和包括要排除的访问权限的管理访问控制从系统帐户的一组访问权限。</span><span class="sxs-lookup"><span data-stu-id="659bc-129">Privileged access needs to be explicitly turned on with the default approver group and including a set of system accounts that you’d want to be excluded from the privileged access management access control.</span></span> 

<span data-ttu-id="659bc-130">若要启用访问权限，并将审批者的组分配 Exchange Online PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="659bc-130">Run the following command in Exchange Online PowerShell to enable privileged access and to assign the approver's group:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
<span data-ttu-id="659bc-131">示例：</span><span class="sxs-lookup"><span data-stu-id="659bc-131">Example:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> <span data-ttu-id="659bc-132">系统帐户由可用于确保组织内的特定自动化功能可以处理不依赖项的情况下访问权限，但建议的此类排除在极那些允许应核准和审核定期。</span><span class="sxs-lookup"><span data-stu-id="659bc-132">System accounts feature is made available to ensure certain automations within your organizations can work without dependency on privileged access, however it is recommended that such exclusions be exceptional and those allowed should be approved and audited regularly.</span></span>

### <a name="step-3---create-an-approval-policy"></a><span data-ttu-id="659bc-133">步骤 3-创建审批策略</span><span class="sxs-lookup"><span data-stu-id="659bc-133">Step 3 - Create an approval policy</span></span>
<span data-ttu-id="659bc-p106">审批策略允许您定义的范围限制在各项任务的特定审批要求。**自动**或**手动**了审批类型选项。</span><span class="sxs-lookup"><span data-stu-id="659bc-p106">An approval policy allows you to define the specific approval requirements scoped at individual tasks. The approval type options are **Auto** or **Manual**.</span></span> 

<span data-ttu-id="659bc-136">运行以下命令在 Exchange Online PowerShell，可以定义一个审批策略：</span><span class="sxs-lookup"><span data-stu-id="659bc-136">Run the following command in Exchange Online PowerShell to define an approval policy:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
<span data-ttu-id="659bc-137">示例：</span><span class="sxs-lookup"><span data-stu-id="659bc-137">Example:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a><span data-ttu-id="659bc-138">在 Office 365 组织中使用授权访问权限</span><span class="sxs-lookup"><span data-stu-id="659bc-138">Using privileged access in your Office 365 organization</span></span>

### <a name="requesting-elevation-authorization-to-execute-tasks"></a><span data-ttu-id="659bc-139">请求提升授权能够执行任务</span><span class="sxs-lookup"><span data-stu-id="659bc-139">Requesting elevation authorization to execute tasks</span></span>
<span data-ttu-id="659bc-p107">启用之后，特权访问需要执行任何任务已定义的关联的审批策略审批。无需执行中包含的任务的用户的审批策略必须请求，并让执行任务所需的权限授予访问审核。</span><span class="sxs-lookup"><span data-stu-id="659bc-p107">Once enabled, privileged access requires approvals for executing any task that has an associated approval policy defined. Users needing to execute tasks included in the an approval policy must request and be granted access approval in order to have permissions necessary to execute the task.</span></span>

<span data-ttu-id="659bc-142">运行以下命令在 Exchange Online PowerShell 来创建和提交给审批者的组的审批请求：</span><span class="sxs-lookup"><span data-stu-id="659bc-142">Run the following command in Exchange Online PowerShell to create and submit an approval request to the approver's group:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
<span data-ttu-id="659bc-143">示例：</span><span class="sxs-lookup"><span data-stu-id="659bc-143">Example:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a><span data-ttu-id="659bc-144">查看提升请求的状态</span><span class="sxs-lookup"><span data-stu-id="659bc-144">View status of elevation requests</span></span>
<span data-ttu-id="659bc-145">创建审批请求后，可以使用请求 ID 关联审阅提升请求状态</span><span class="sxs-lookup"><span data-stu-id="659bc-145">After an approval request is created, elevation request status can be reviewed using the associated with request ID.</span></span>

<span data-ttu-id="659bc-146">运行以下命令在 Exchange Online PowerShell，可以查看特定的请求 ID 审批请求状态：</span><span class="sxs-lookup"><span data-stu-id="659bc-146">Run the following command in Exchange Online PowerShell to view a approval request status for a specific request ID:</span></span>
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
<span data-ttu-id="659bc-147">示例：</span><span class="sxs-lookup"><span data-stu-id="659bc-147">Example:</span></span>
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a><span data-ttu-id="659bc-148">批准提升授权请求</span><span class="sxs-lookup"><span data-stu-id="659bc-148">Approving an elevation authorization request</span></span>
<span data-ttu-id="659bc-149">当创建审批请求时，相关的审批者组的成员将收到的电子邮件通知和可以批准请求 ID 与关联的请求</span><span class="sxs-lookup"><span data-stu-id="659bc-149">When an approval request is created, members of the relevant approver group will receive an email notification and can approve the request associated with the request ID.</span></span> 

<span data-ttu-id="659bc-150">运行以下命令在 Exchange Online PowerShell 批准提升授权请求：</span><span class="sxs-lookup"><span data-stu-id="659bc-150">Run the following command in Exchange Online PowerShell to approve an elevation authorization request:</span></span>
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="659bc-151">示例：</span><span class="sxs-lookup"><span data-stu-id="659bc-151">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a><span data-ttu-id="659bc-152">拒绝提升授权请求</span><span class="sxs-lookup"><span data-stu-id="659bc-152">Denying an elevation authorization request</span></span>
<span data-ttu-id="659bc-153">当创建审批请求时，相关的审批者组的成员可以拒绝请求 ID 与关联的请求</span><span class="sxs-lookup"><span data-stu-id="659bc-153">When an approval request is created, members of the relevant approver group can deny the request associated with the request ID.</span></span> 

<span data-ttu-id="659bc-154">运行以下命令在 Exchange Online PowerShell 拒绝提升授权请求：</span><span class="sxs-lookup"><span data-stu-id="659bc-154">Run the following command in Exchange Online PowerShell to deny an elevation authorization request:</span></span>
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
<span data-ttu-id="659bc-155">示例：</span><span class="sxs-lookup"><span data-stu-id="659bc-155">Example:</span></span>
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a><span data-ttu-id="659bc-156">运行任务</span><span class="sxs-lookup"><span data-stu-id="659bc-156">Running the task</span></span>
<span data-ttu-id="659bc-p108">授予审批后，请求的用户可以执行预期的任务并特权的 access 将授权，并对代表用户执行任务。审批保持有效的请求持续时间 （默认持续时间是 4 个小时），在此期间请求者可以预期的任务多次执行。所有此类执行的记录，并使其可供安全性和合规性审核。</span><span class="sxs-lookup"><span data-stu-id="659bc-p108">After approval is granted, the requesting user can execute the intended task and privileged access will authorize and execute the task on users’ behalf. The approval remains valid for the requested duration (default duration is 4 hours), during which the requester can execute the intended task multiple times. All such executions are logged and made available for security and compliance auditing.</span></span> 

### <a name="disable-privileged-access-in-office-365"></a><span data-ttu-id="659bc-160">禁用 Office 365 中的特权的访问</span><span class="sxs-lookup"><span data-stu-id="659bc-160">Disable privileged access in Office 365</span></span>
<span data-ttu-id="659bc-p109">如果需要您可以禁用 Office 365 中的访问权限的管理。禁用权限访问不会删除任何关联的审批策略或审批者组。</span><span class="sxs-lookup"><span data-stu-id="659bc-p109">If needed, you can disable privileged access management in Office 365. Disabling privileged access does not delete any associated approval policies or approver groups.</span></span>

<span data-ttu-id="659bc-163">运行以下命令在 Exchange Online Powershell，可以禁用授权访问权限：</span><span class="sxs-lookup"><span data-stu-id="659bc-163">Run the following command in Exchange Online Powershell to disable privileged access:</span></span>

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a><span data-ttu-id="659bc-164">管理 Microsoft Azure 中的 Microsoft Graph 访问</span><span class="sxs-lookup"><span data-stu-id="659bc-164">Managed access to Microsoft Graph in Microsoft Azure</span></span>

> [!IMPORTANT]
> <span data-ttu-id="659bc-165">本节涵盖有关当前仅适用于预览功能的详细信息。</span><span class="sxs-lookup"><span data-stu-id="659bc-165">This section covers details about a feature currently available only in preview.</span></span>

<span data-ttu-id="659bc-p110">到 Microsoft Azure 中的 Microsoft Graph 托管的 access 是一种服务，可帮助组织施加控制其 Office 365 数据粒度级别。此系统允许应用程序开发人员伪造见解与该数据。</span><span class="sxs-lookup"><span data-stu-id="659bc-p110">Managed access to Microsoft Graph in Microsoft Azure is a service that helps organizations exert a granular level of control over their Office 365 data. This system allows application developers to forge insights with that data.</span></span> 

<span data-ttu-id="659bc-p111">此系统使用 Office 365 特权访问断言控制通过其审批工作流，并允许 Office 365 管理员监督数据范围的访问其数据。应用程序安装后，需要访问 Office 365 数据的数据的请求进入。</span><span class="sxs-lookup"><span data-stu-id="659bc-p111">This system uses Office 365 privileged access to assert control over their data through its approval workflow, allowing scoped access to Office 365 data with admin oversight. Requests for data come in when applications are installed and require access to Office 365 data.</span></span>

### <a name="view-request-details"></a><span data-ttu-id="659bc-170">查看请求的详细信息</span><span class="sxs-lookup"><span data-stu-id="659bc-170">View request details</span></span>
<span data-ttu-id="659bc-171">查看 Office 365 数据访问请求的详细信息。</span><span class="sxs-lookup"><span data-stu-id="659bc-171">View details of the access requests for Office 365 data.</span></span>

<span data-ttu-id="659bc-172">运行以下命令在 Exchange Online Powershell，可以查看数据请求：</span><span class="sxs-lookup"><span data-stu-id="659bc-172">Run the following command in Exchange Online Powershell to view data requests:</span></span>
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
<span data-ttu-id="659bc-173">示例输出：</span><span class="sxs-lookup"><span data-stu-id="659bc-173">Example output:</span></span>
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a><span data-ttu-id="659bc-174">批准数据访问请求</span><span class="sxs-lookup"><span data-stu-id="659bc-174">Approve data access requests</span></span>
<span data-ttu-id="659bc-175">可以通过标准的特权的访问审批 cmdlet 审核所有数据访问请求。</span><span class="sxs-lookup"><span data-stu-id="659bc-175">All data access requests can be approved through the standard privileged access approval cmdlets.</span></span>

<span data-ttu-id="659bc-176">运行以下命令在 Exchange Online Powershell，可以为特定的请求者批准所有数据请求：</span><span class="sxs-lookup"><span data-stu-id="659bc-176">Run the following command in Exchange Online Powershell to approve all data requests for specific requestor:</span></span>

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="659bc-177">示例：</span><span class="sxs-lookup"><span data-stu-id="659bc-177">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a><span data-ttu-id="659bc-178">获取帮助，并提供反馈</span><span class="sxs-lookup"><span data-stu-id="659bc-178">Getting help and providing feedback</span></span>
<span data-ttu-id="659bc-p112">但我们知道期间 public beta 您可能会遇到偶尔 bug 或有反馈和如何改进访问权限的管理的建议。我们将您的反馈，并鼓励您共享与我们：</span><span class="sxs-lookup"><span data-stu-id="659bc-p112">We recognize that during the public beta you may come across an occasional bug or have feedback and suggestions on how we can improve privileged access management. We value your feedback and encourage you to share it with us:</span></span>
- <span data-ttu-id="659bc-181">[Office 预览 Yammer 组](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206)中发布您的反馈 ad 建议。</span><span class="sxs-lookup"><span data-stu-id="659bc-181">Post your feedback ad suggestions in the [Office Preview Yammer Group](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span></span>
- <span data-ttu-id="659bc-182">文件 bug 报表区域路径"Office 365 特权访问管理"下[Office 预览 VSO](https://office-previews.visualstudio.com/previews)上。</span><span class="sxs-lookup"><span data-stu-id="659bc-182">File your bug reports under area path “Office 365 Privileged Access Management” on the [Office Preview VSO](https://office-previews.visualstudio.com/previews).</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="659bc-183">常见问题</span><span class="sxs-lookup"><span data-stu-id="659bc-183">Frequently asked questions</span></span>

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a><span data-ttu-id="659bc-184">使用 Office 365 中的访问权限时，需要哪些 Sku？</span><span class="sxs-lookup"><span data-stu-id="659bc-184">What SKUs do I need to use privileged access in Office 365?</span></span>
<span data-ttu-id="659bc-185">特权访问 Office 365 中的管理是当前仅适用于以 E5 和高级合规性 Sku 客户。</span><span class="sxs-lookup"><span data-stu-id="659bc-185">Privileged access management in Office 365 is currently only available for customers with E5 and Advanced Compliance SKUs.</span></span>

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a><span data-ttu-id="659bc-186">何时适用于 Office 365 工作负载超过 Exchange 访问权限？</span><span class="sxs-lookup"><span data-stu-id="659bc-186">When will privileged access be available for Office 365 workloads beyond Exchange?</span></span>
<span data-ttu-id="659bc-p113">我们计划推出提供此功能的其他 Office 365 工作负载。我们准备好共享一个日程表，它将提供通过 Office 365 路线图。</span><span class="sxs-lookup"><span data-stu-id="659bc-p113">We plan to offer this feature in other Office 365 workloads soon. When we’re ready to share a timeline, it will be available through the Office 365 roadmap.</span></span>

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a><span data-ttu-id="659bc-189">如何这是不同 Azure Active Directory 特权身份管理的？</span><span class="sxs-lookup"><span data-stu-id="659bc-189">How is this different from Azure Active Directory’s Privileged Identity Management?</span></span>
<span data-ttu-id="659bc-p114">在不同的范围中实时访问 Office 365 和[Azure AD 特权身份管理](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)补充通过提供访问每个其他控件中的管理访问权限。共同它们提供强大的一组控件用于保护数据。</span><span class="sxs-lookup"><span data-stu-id="659bc-p114">Privileged access management in Office 365 and [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complement each other by providing access control with just-in-time access at different scopes. Together they provide a robust set of controls for protecting your data.</span></span>

<span data-ttu-id="659bc-p115">特权访问 Office 365 中的管理可以定义和时角色级别应用能够执行多个任务的 Azure AD 特权标识管理任务级别范围。 Azure AD 特权身份管理主要允许管理 AD 角色和特权时的角色组的访问 Office 365 中的访问管理应用于任务级别。</span><span class="sxs-lookup"><span data-stu-id="659bc-p115">Privileged access management in Office 365 can be defined and scoped at the task level, while Azure AD Privileged Identity Management applies at the role level with the ability to execute multiple tasks.  Azure AD Privileged Identity Management primarily allows managing accesses for AD roles and role groups while privileged access management in Office 365 is applied at the task level.</span></span>

 - <span data-ttu-id="659bc-194">**启用特权已在使用 Azure AD 特权身份管理时，访问 Office 365 中的管理：** Office 365 中添加特权的访问管理可以提供其他粒度层保护并审核功能特权访问 Office 365 数据。</span><span class="sxs-lookup"><span data-stu-id="659bc-194">**Enabling privileged access management in Office 365 while already using Azure AD Privileged Identity Management:** Adding privileged access management in Office 365 can provide another granular layer of protection and audit capabilities for privileged access to Office 365 data.</span></span>

- <span data-ttu-id="659bc-195">**启用 Azure AD 特权时已使用的身份管理特权访问管理 Office 365 中：** 向特权特权 Azure AD 身份管理 Office 365 中的访问管理可以扩展特权的访问由用户的角色或标识主要定义的 Office 365 以外的数据。</span><span class="sxs-lookup"><span data-stu-id="659bc-195">**Enabling Azure AD Privileged Identity Management while already using privileged access management in Office 365:**  Adding Azure AD Privileged Identity Management to privileged access management in Office 365 can extend privileged access to data outside of Office 365 that’s primarily defined by a user’s role or identity.</span></span> 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a><span data-ttu-id="659bc-196">是否需要为全局管理员管理 Office 365 中的授权访问权限？</span><span class="sxs-lookup"><span data-stu-id="659bc-196">Do I need to be a Global Admin to manage privileged access in Office 365?</span></span>
<span data-ttu-id="659bc-p116">在预览期间，您需要具有能够管理特权的访问 Office 365 中的全局管理员特权。包括在审批者组中的用户不需要是全局管理员才能查看和批准请求。</span><span class="sxs-lookup"><span data-stu-id="659bc-p116">During the preview you need to have Global Admin privilege to be able to manage privileged access in Office 365. Users who are included in an approvers’ group don't need to be a Global Admin to review and approve requests.</span></span> 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a><span data-ttu-id="659bc-199">是与客户密码箱的 Office 365 中的访问权限的管理如何？</span><span class="sxs-lookup"><span data-stu-id="659bc-199">How is privileged access management in Office 365 related to Customer Lockbox?</span></span>
<span data-ttu-id="659bc-p117">[客户密码箱](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2)允许访问由其服务提供商，即 Microsoft 的数据的组织的访问控制的级别。特权访问 Office 365 中的管理允许的所有特权的 Office 365 任务组织内的精细的访问控制。</span><span class="sxs-lookup"><span data-stu-id="659bc-p117">[Customer Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) allows a level of access control for organizations for access to to data by their service provider, i.e. Microsoft. Privileged access management in Office 365 allows granular access control within an organization for all Office 365 privileged tasks.</span></span>