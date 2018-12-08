---
title: 管理多地理位置环境
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 学习如何在多地理位置环境中管理 SharePoint 和 OneDrive 服务。
ms.openlocfilehash: 09f8816fc0ba748ced5bd104710677829d893198
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200695"
---
# <a name="administering-a-multi-geo-environment"></a>管理多地理位置环境

下面介绍 OneDrive 和 SharePoint 服务在多地理位置环境中的工作方式。

#### <a name="onedrive-administrator-experience"></a>OneDrive 管理员体验

[OneDrive 管理中心](https://admin.onedrive.com)的左侧导航栏中有一个“地理位置”**** 选项卡，其中包含地理位置地图，你可在其中查看和管理地理位置。使用此页面可添加或删除租户的地理位置。

#### <a name="taxonomy"></a>分类

对于跨多地理位置的企业托管元数据，我们支持统一[分类](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)，同时将主数据托管在公司的中心位置。建议从中心位置管理全局分类，并只在附属位置的分类中添加特定于位置的术语。全局分类术语将同步到附属位置。

#### <a name="sharing"></a>共享

管理员可以为他们的每个位置设置共享策略并对其进行管理。每个地理位置的 OneDrive 网站只会接受相应地理位置特定的共享设置。（例如，可以将[外部共享](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)用于中心位置，但不可用于附属位置，反之亦然。）请注意，共享设置不允许配置地理位置之间的共享限制。

对于 OneDrive 多地理位置，必须在每个地理位置管理你的共享设置，因为这些设置在租户之间不同步。要管理共享，请访问 [OneDrive 管理中心共享设置](https://admin.onedrive.com/?v=SharingSettings)页。默认情况下，每个附属位置中的任何人都可以使用外部共享。

#### <a name="user-profile-application"></a>用户配置文件应用程序

每个地理位置都有一个[用户配置文件应用程序](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)。每个用户的配置文件信息都托管在其地理位置中，并可供该地理位置的管理员使用。

如果你有自定义配置文件属性，建议跨地区使用同一配置文件架构并在所有地理位置或所需的位置填充自定义配置文件属性。有关如何以编程方式填充用户配置文件数据的指导，请参阅[批量用户配置文件更新 API](https://docs.microsoft.com/zh-CN/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)

#### <a name="bcs-secure-store-apps"></a>BCS、安全存储、应用

BCS、安全存储和应用在每个附属位置都具有单独的实例，因此，SharePoint Online 管理员应从每个附属位置单独管理和配置这些服务。

#### <a name="security-and-compliance-admin-center"></a>安全与合规管理中心

还有一个多地理位置租户的中央合规中心：[Office 365 安全与合规中心](https://protection.office.com/?rfr=AdminCenter\#/homepage)。

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>信息保护 (IP) 数据丢失防护 (DLP) 策略

可以在安全与合规中心为 OneDrive for Business 设置 IP DLP 策略，根据需要将策略范围设置为整个租户或适用用户。例如，如果希望选择适用于附属位置中 OneDrive 用户的策略，请选择将策略应用到特定 OneDrive 并输入用户的 OneDrive URL。有关创建 DLP 策略的常规指导，请参阅[数据丢失防护策略概述](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)。

DLP 策略将基于每个地理位置的适用性自动同步。

在 UI 中，无法为地理位置中的所有用户实施信息保护和数据丢失防护策略，你必须为策略选择适用的 OneDrive 帐户，或将策略全局应用于所有 OneDrive 帐户。

#### <a name="ediscovery"></a>电子数据展示 

默认情况下，多地理位置租户的电子数据展示管理者或管理员只能在该租户所在的中心位置实施电子数据展示。若要支持在附属位置实施电子数据展示，可通过 PowerShell 获取一个名为“Region”的新合规性安全筛选器参数。

Office 365 全局管理员必须分配电子数据展示管理者权限，以允许其他人员执行电子数据展示，并在其适用的合规性安全筛选器中分配“Region”参数，以便将要进行电子数据展示的区域指定为附属位置，否则，不会对该附属位置执行任何电子数据展示。

当为特定附属位置设置电子数据展示管理者或管理员角色时，电子数据展示管理者或管理员将只能对位于该附属位置的 SharePoint 网站和 OneDrive 网站执行电子数据展示搜索操作。如果电子数据展示管理者或管理员尝试搜索指定附属位置以外的 SharePoint 或 OneDrive 网站，将不返回任何结果。此外，当某个附属位置的电子数据展示管理者或管理员触发导出时，数据将导出到该地区的 Azure 实例。通过禁止跨受控界限导出内容，将有助于组织保持合规性。

> [!NOTE]
> 如果需要电子数据展示管理者搜索多个 SharePoint 附属位置，将需要为电子数据展示管理者创建另一个用户帐户，以指定 OneDrive 或 SharePoint 网站所在的备用附属位置。

<table>
<thead>
<tr class="header">
<th align="left"><strong>支持多地理位置的地理位置</strong></th>
<th align="left"><strong>SharePoint 导出数据的电子数据展示将会在此 Azure Blob 数据位置中...</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">东南亚或东亚数据中心</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUS</strong></td>
<td align="left">东南亚或东亚数据中心</td>
</tr>
<tr class="even">
<td align="left"><strong>CAN</strong></td>
<td align="left">美国数据中心</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">欧洲数据中心</td>
</tr>
<tr class="odd">
<td align="left"><strong>FRA</strong></td>
<td align="left">欧洲数据中心</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">欧洲数据中心</td>
</tr>
<tr class="even">
<td align="left"><strong>IND</strong></td>
<td align="left">东南亚或东亚数据中心</td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">东南亚或东亚数据中心</td>
</tr>
<tr class="even">
<td align="left"><strong>JPN </strong></td>
<td align="left">东南亚或东亚数据中心</td>
</tr>
<tr class="odd">
<td align="left"><strong>NAM</strong></td>
<td align="left">美国数据中心</td>
</tr>
</tbody>
</table>

针对区域设置合规性安全筛选器：

1.  打开 Windows PowerShell

2.  输入  
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName

    例如：**New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

请参阅 [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) 一文了解其他参数和语法

#### <a name="audit-log-search"></a>审核日志搜索

所有附属位置的统一[审核日志](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)均可从 Office 365 审核日志搜索页找到。你可以查看跨地理位置的所有审核日志条目，例如，NAM 和 EUR 地理位置用户的活动将显示在一个组织视图中，然后你可以应用现有筛选器，查看特定用户的活动。
