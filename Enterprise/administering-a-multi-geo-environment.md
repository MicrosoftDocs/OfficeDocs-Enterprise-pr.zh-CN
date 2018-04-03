---
title: 管理多个地理环境
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解有关管理 SharePoint 和 OneDrive 多地理环境中的服务。
ms.openlocfilehash: f49cf35503ee6495b5982dc7d72f9b1936f564c6
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2018
---
# <a name="administering-a-multi-geo-environment"></a>管理多个地理环境

下面我们来看 OneDrive 和 SharePoint 服务多地理环境中的工作方式。

#### <a name="onedrive-administrator-experience"></a>OneDrive 管理员体验

[OneDrive 管理中心](https://admin.onedrive.com)有**地理位置**选项卡在左边的导航功能地理位置映射，您可以查看和管理您的地理位置。使用此页面可添加或删除您组织的地理位置。

#### <a name="taxonomy"></a>分类

我们支持统一的[分类](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)企业托管元数据跨地理位置与主所驻留在您的公司的集中位置。我们建议您从中心位置管理您的全局分类，并仅将特定位置术语添加到卫星地理位置分类。全局分类条款将同步到附属的地理位置。

#### <a name="sharing"></a>共享

管理员可以设置并管理其位置的每个共享策略。在每个地理位置的 OneDrive 网站将履行只相应地区特定共享设置。例如，您可以允许[外部共享](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)有关您的中心位置，而不是您的附属位置，反之亦然。对于 OneDrive 多的地区，因为这些都不会同步跨租户必须管理共享设置在每个地理位置。

若要管理共享访问[共享设置的 OneDrive 管理中心](https://admin.onedrive.com/?v=SharingSettings)页。默认情况下与任何人在每个卫星位置启用外部共享。

#### <a name="user-profile-application"></a>用户配置文件应用程序

每个地理位置处于一个[用户配置文件应用程序](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)。在它们的地理位置和地理位置的管理员可以承载每个用户的配置文件信息。

如果您有自定义配置文件属性，那么建议您跨地区使用相同的配置文件架构并填充您的自定义配置文件属性可在所有地理位置或者在需要的地方。

#### <a name="bcs-secure-store-apps"></a>BCS，安全的存储应用程序

BCS、 安全存储和应用程序所有具有独立的地理实例，因此 SharePoint Online 管理员应管理和配置这些服务与它们希望这些存在每个 geo 实例。

#### <a name="security-and-compliance-admin-center"></a>安全性和法规遵从性管理中心

没有一个中央法规遵从性中心多地区租户： [Office 365 安全和法规遵从性中心](https://protection.office.com/?rfr=AdminCenter\#/homepage)。

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>信息 (IP) 的保护数据丢失防护 (DLP) 策略

您可以设置 IP DLP 策略业务的 OneDrive 在安全性和法规遵从性中心，根据需要为整个组织或适用的用户范围的策略。例如： 如果您想要为用户选择策略 OneDrive 卫星位置，选择该选项可以将该策略应用于特定的 OneDrive，输入用户的 OneDrive url。[数据丢失防护策略概述](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)在创建 DLP 策略的一般指南，请参见

DLP 策略将自动同步根据每个地理位置对其适用性。

在地理位置实现对所有用户的信息保护和数据丢失防护策略不在用户界面中可用的选项，而必须选择策略适用的 OneDrive 帐户或全局将策略应用到所有的 OneDrive 帐户。

#### <a name="ediscovery"></a>电子数据展示 

默认情况下，电子数据展示的经理或管理员的多个地区组织将能够执行 eDiscovery 仅在该组织的中心位置。为支持开展卫星位置的 eDiscovery 的能力，一个新的法规遵从性安全筛选器参数，称为"区域"可通过 PowerShell。

Office 365 全局管理员必须将分配 eDiscovery 经理权限以允许其他用户执行 eDiscovery 和分配其适用的法规遵从性安全筛选来指定执行 eDiscovery 作为附属的区域中的"区域"参数位置，否则为没有 eDiscovery 执行的附属位置。

当 eDiscovery 的经理或管理员角色设置为特定地理位置时，eDiscovery 的经理或管理员仅能执行 eDiscovery 搜索操作的 SharePoint 网站和地理位置的 OneDrive 站点。如果 eDiscovery 经理或管理员尝试搜索指定区域之外的 OneDrive 站点，则将不返回任何结果。此外，当区域经理或管理员 eDiscovery 触发一个导出，该地区的 Azure 实例导出数据。这可以帮助企业保持法规遵从性，从而不受控制的界限要导出的内容。

> [!NOTE]
> 如果有必要为 eDiscovery 经理在 SharePoint 中的多个区域进行搜索，需要为 eDiscovery 指定 OneDrive 或 SharePoint 网站的位置的备用区域服务控制管理器创建另一个用户帐户。

<table>
<thead>
<tr class="header">
<th align="left"><strong>多地区支持地理位置</strong></th>
<th align="left"><strong>eDiscovery SharePoint 导出的数据将处于此 Azure Blob 数据的位置...</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>名称</strong></td>
<td align="left">美国数据中心</td>
</tr>
<tr class="even">
<td align="left"><strong>欧元</strong></td>
<td align="left">欧洲数据中心</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC 公司</strong></td>
<td align="left">东南方向或东亚太地区数据中心</td>
</tr>
<tr class="even">
<td align="left"><strong>可以</strong></td>
<td align="left">美国数据中心</td>
</tr>
<tr class="odd">
<td align="left"><strong>澳大利亚</strong></td>
<td align="left">东南方向或东亚太地区数据中心</td>
</tr>
<tr class="even">
<td align="left"><strong>韩文</strong></td>
<td align="left">租户的默认数据位置</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">欧洲数据中心</td>
</tr>
<tr class="even">
<td align="left"><strong>日文</strong></td>
<td align="left">东南方向或东亚太地区数据中心</td>
</tr>
</tbody>
</table>

要为区域设置遵从安全筛选器：

1.  打开 Windows PowerShell

2.  输入  
    $s = New PSSession 配置名 Microsoft.Exchange-ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -$cred 凭据-基本身份验证 AllowRedirection-SessionOption (New PSSessionOption SkipCACheck-SkipCNCheck-SkipRevocationCheck)

    $ = 导入 PSSession $s AllowClobber  

3.  **新 ComplianceSecurityFilter****-操作**所有**-FilterName** EnterTheNameYouWantToAssign **-地区**EnterTheRegionParameter **-用户**EnterTheUserPrincipalName

    例如：**新 ComplianceSecurityFilter-操作**所有**-FilterName** NAMEDISCOVERYMANAGERS **-地区**名称**-用户**adwood@contosodemosx.onmicrosoft.com

请参阅附加的参数和语法的[新 ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx)文章

#### <a name="audit-log-search"></a>审核日志搜索

Office 365 审核日志搜索页面提供了统一[审核日志](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)的所有您的地理位置。您可以看到中的所有审核日志项跨 geo、 例如，名称和欧元地区用户的活动中将会显示一个组织视图，然后可以应用现有的筛选器以都查看特定用户的活动。
