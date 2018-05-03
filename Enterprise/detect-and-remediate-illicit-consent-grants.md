---
title: 检测和修正 Office 365 中的非法同意授予
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 4/23/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: 了解如何识别和修正 Office 365 中的非法同意授予攻击。
ms.openlocfilehash: f6576fccd7cac49dbbf2e9ea359e08257ddc42d0
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="detect-and-remediate-illicit-consent-grants-in-office-365"></a>检测和修正 Office 365 中的非法同意授予

**摘要** 了解如何识别和修正 Office 365 中的非法同意授予攻击。

## <a name="what-is-the-illicit-consent-grant-attack-in-office-365"></a>Office 365 中的非法同意授予攻击是什么？
在非法同意授予攻击，攻击者创建的 Azure 注册应用程序请求访问数据，例如电子邮件的联系人信息或文档。然后，攻击者授予该应用程序许可通过网络钓鱼攻击中，或通过到受信任网站注入非法代码访问其数据到技巧最终用户。非法的应用程序已被授予许可后，它有权无需组织帐户的数据访问帐户级别。因为这些组件是第三方应用程序及向组织外部，常规补救步骤，如重置受损帐户的密码或帐户，需要多因素身份验证 (MFA) 不是有效针对此类攻击，显示的值。这些攻击利用其假定调用信息的实体是自动化和不 human 交互模型。

## <a name="what-does-an-illicit-consent-grant-attack-look-like-in-office-365"></a>非法同意授予攻击外观 Office 365 中采用什么？
您需要搜索 Office 365**审核日志**以查找迹象，也称为指示器的威胁 (IOC) 的此类攻击。对于具有多个 Azure 注册应用程序和大型用户群的组织，最佳做法是查看每周基于您组织同意授予。
### <a name="steps-for-finding-signs-of-this-attack"></a>查找此类攻击的迹象的步骤
1. 在 Office 365 租户中打开的**安全性和合规性中心**。
2. 导航到**搜索和调查**节点，然后选择**审核日志**搜索。
3. 创建搜索 （所有活动和所有用户） 和筛选的同意的结果，向应用程序，并添加 OAuth2PermissionGrant。
4. 检查扩展属性并检查，以查看是否 IsAdminContent 设置为 True。


如果此值为 true，则表明全局管理员访问具有可能已授予对数据的广泛访问。如果这是意外，需要对[确认攻击](detect-and-remediate-illicit-consent-grants.md#confirmattack)的步骤。

<a name="confirmattack"> </a>
## <a name="how-to-confirm-an-attack"></a>如何确认攻击
如果您拥有一个或多个实例 IOCs 上面所列，则需要执行进一步调查产生积极确认攻击发生。您可以使用任何这三种方法以确认攻击。
- 库存应用程序和使用 Azure Active Directory 门户其权限。全面，此方法，但只能检查一个用户一次可以是非常耗时如果您有很多用户能够检查。
- 库存应用程序和使用 PowerShell 其权限。这是开销的最快而最全面的方法，以最少。
- 让您的用户单独检查其应用程序和权限并将结果报告为修正管理员。

## <a name="inventory-apps-with-access-in-your-organization"></a>库存与您的组织中访问的应用程序
您可以执行此操作为您的用户与 Azure Active Directory 门户或 PowerShell 或让您的用户单独枚举其应用程序访问。

### <a name="steps-for-using-the-azure-active-directory-portal"></a>使用 Azure Active Directory 门户的步骤
您可以查找到任意单个用户已通过使用[Azure Active Directory 门户](https://portal.azure.com/)授予权限的应用程序。 
1. 登录到 Azure 门户具有管理权限。
2. 选择 Azure Active Directory 刀片。
3. 选择**用户**。
4. 选择您想要查看的用户。
5. 选择**应用程序**。

这将显示您的应用程序分配给用户和 applcations 拥有的权限。

### <a name="steps-for-having-your-users-enumerate-their-application-access"></a>让用户步骤枚举其应用程序访问
让您的用户转到https://myapps.microsoft.com并查看那里其自己的应用程序访问。他们应能够看到具有访问权限的所有应用程序，查看有关其 （包括的访问范围） 的详细信息，并能够取消可疑或非法的应用程序的权限。

### <a name="steps-for-doing-this-with-powershell"></a>使用 PowerShell 进行此操作的步骤
若要验证非法 Consent 授予攻击的最简单方式是运行[Get AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09)，其中将转储所有 OAuth 同意授予和应用程序权限的所有用户在您的租户成一个.csv 文件。 

#### <a name="pre-requisites"></a>必备组件
- 安装 Azure AD PowerShell 库。
- 将对运行该脚本租户上的全局管理员权限。
- 从中将运行脚本的计算机上的本地管理员。

> [!IMPORTANT]
> 我们强烈建议您在您的管理帐户需要多因素身份验证。 此脚本支持 MFA 身份验证。

1. 登录到将运行脚本从具有本地管理员权限的计算机。
2. 下载，或将从 GitHub [Get AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09)脚本复制到从中将运行 scruipt 文件夹。 这将输出"permissions.csv"文件将写入的同一个文件夹。
3. 打开作为管理员的 PowerShell 实例，并打开保存到脚本的文件夹。
4. 连接到您的目录使用[连接 AzureAD](https://docs.microsoft.com/en-us/powershell/module/azuread/connect-azuread?view=azureadps-2.0) cmdlet。
5. 运行以下 PowerShell 命令行，如下所示：`.Get-AzureASPSPermissions.ps1 | Export-csv -path "Permissions.csv" -NoTypeInformation`

该脚本将生成一个名为 Permissions.csv 的文件。请按照下列步骤以查找非法的应用程序权限授予： 
1. ConsentType 列 （列 G） 中搜索"AllPrinciples"的值。AllPrincipals 权限允许客户端应用程序访问租赁中的每个人的内容。本机 Office 365 应用程序需要此权限，以便它们正确运行。拥有此权限的每个非 Microsoft 应用程序应仔细检查。
2.  在权限列 （F 列） 查看每个委派应用程序的权限具有内容。查找"Read"和"写入"权限或"*。所有"权限，并查看这些仔细因为它们可能不适用。
3.  查看已同意授予的特定用户。如果高配置文件或高影响用户拥有授予不当同意，您应该进一步调查。
4.  在 ClientDisplayName 列 （C 列） 查找似乎可疑的应用程序。应仔细检查拼写错误的名称、 超级看起来不够鲜明的名称或黑客发音相近名称与应用程序。

## <a name="determine-the-scope-of-the-attack"></a>确定攻击的范围
清点应用程序访问后，查看 Office 365**审核日志**来确定违反的完整范围。 搜索在受影响的用户，时间范围的非法的应用程序具有访问您的组织，以及应用程序具有的权限。您可以在[Office 365 安全性和合规性中心](https://support.office.com/en-us/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c)中搜索**审核日志**。 

> [!IMPORTANT]
> [邮箱审核](https://support.office.com/en-us/article/Enable-mailbox-auditing-in-Office-365-aaca8987-5b62-458b-9882-c28476a66918)和[活动审核管理员和用户](https://support.office.com/en-us/article/turn-office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014)必须已启用之前，用于获取此信息攻击。

## <a name="how-to-stop-and-remediate-an-illicit-consent-grant--attack"></a>如何停止和修正非法同意授予攻击
在确定具有非法权限的应用程序之后，您具有几种方法可以删除该访问权限。
- 您可以取消的 Azure Active Directory 门户中的应用程序的权限：
    - 导航到**Azure Active Directory 用户**刀片中受影响的用户。
    - 选择**应用程序**。
    - 选择非法的应用程序。
    - **删除**中单击钻取下。
- 通过[删除 AzureADOAuth2PermissionGrant](https://docs.microsoft.com/en-us/powershell/module/azuread/Remove-AzureADOAuth2PermissionGrant?view=azureadps-2.0)中的步骤，您可以撤消 OAuth 同意授予使用 PowerShell。
- 通过[删除 AzureADServiceAppRoleAssignment](https://docs.microsoft.com/en-us/powershell/module/azuread/Remove-AzureADServiceAppRoleAssignment?view=azureadps-2.0)中的步骤，您可以撤消 PowerShell 与该服务应用程序角色分配。
- 您还可以禁用登录受影响的帐户完全，其中将反过来禁用应用程序访问该帐户中的数据。当然，这不是理想的最终用户的工作效率，但如果您正在快速限制影响，它可以是可行的短期修复。
- 您可以关闭您的租户的集成的应用程序。这是禁用的最终用户授予在租户范围内的许可功能的重大步骤。这将防止无意中授予对恶意应用程序访问您的用户。这不是强烈建议，它会严重影响用户能够高效与第三方应用程序。 您可以按照[关闭集成的应用程序](https://support.office.com/en-us/article/Turning-Integrated-Apps-on-or-off-7e453a40-66df-44ab-92a1-96786cb7fb34)中打开或关闭的步骤来执行此操作。

## <a name="secure-office-365-like-a-cybersecurity-pro"></a>像网络专业人员的安全保护 Office 365
Office 365 订阅附带了强大的可用于保护您的数据和用户的安全功能集。 使用[Office 365 安全路线图： Top 优先级的前 30 天，90 天及其他认证实战](https://support.office.com/en-us/article/office-365-security-roadmap-top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352)实现 Microsoft 建议的用于保护 Office 365 租户的最佳做法。
- 第一个 30 天内完成的任务。 这些没有直接影响，因此低影响到您的用户。
- 若要在 90 天内完成的任务。这些需要更多时间规划和实现但大大提高安全状况。
- 90 天前。在您的第一个 90 天工作中构建这些增强功能。

## <a name="see-also"></a>另请参阅：
- [意外的应用程序，我的应用程序列表中](https://docs.microsoft.com/en-us/azure/active-directory/application-access-unexpected-application)指导管理员完成他们可能想要实现有意外的访问应用程序数据之后执行的各种操作。
- [将应用程序集成与 Azure Active Directory] (https://docs.microsoft.com/en-us/azure/active-directory/active-directory-apps-permissions-consent)是同意和权限的高级概述。 应特别注意到[consent framework 概述](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#overview-of-the-consent-framework)部分。
- [问题开发我的应用程序](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-application-dev-development-content-map)提供了指向各种 consent 相关的文章。
- [应用程序和 Azure Active Directory (Azure AD) 中的服务主体对象](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-application-objects)提供的应用程序和服务的主体对象的核心到应用程序模型的概述。
- [应用程序的管理访问](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-managing-access-to-apps)是管理员具有管理应用程序的用户访问的功能的概述。