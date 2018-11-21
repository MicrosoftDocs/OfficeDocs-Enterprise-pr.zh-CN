---
title: OneDrive for Business 多地理位置租户配置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: 了解如何配置 OneDrive for Business 多地理位置。
ms.openlocfilehash: 5049904b1419935ed1d55eb73b74d2cd12edb3c0
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547164"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>OneDrive for Business 多地理位置租户配置

在配置 OneDrive for Business 多地理位置之前，请确保已阅读[规划 OneDrive for Business 多地理位置](plan-for-multi-geo.md)。若要执行本文中的步骤，你需要具有想要启用作为附属位置的地理位置的列表和要在这些位置中预配的测试用户。

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>将 Office 365 中的多地理位置功能计划添加到租户

要使用 OneDrive for Business 多地理位置，你需要有 _Office 365 的多地理位置功能_计划。与你的帐户团队合作，将此计划添加到你的租户。你的帐户团队会为你联系合适的许可专家，并配置你的租户。

请注意，_Office 365 的多地理位置功能_计划是一个用户级别的服务计划。你需要为每个想要托管在附属位置的用户提供许可证。随着你将用户添加到附属位置，你可以随时添加更多许可证。

你的租户配置了 _Office 365 的多地理位置功能_计划后，便可使用 [OneDrive 管理中心的](https://admin.onedrive.com)“地理位置”**** 选项卡。

## <a name="add-satellite-locations-to-your-tenant"></a>向租户添加附属地理位置

必须为想要使用 OneDrive for Business 的每个地理位置添加附属位置。下表显示了可用的地理位置：

<table>
<thead>
<tr class="header">
<th align="left"><strong>位置</strong></th>
<th align="left"><strong>代码</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">亚太地区</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">澳大利亚</td>
<td align="left">AUS</td>
</tr>
<tr class="even">
<td align="left">加拿大</td>
<td align="left">CAN</td>
</tr>
<tr class="even">
<td align="left">欧洲/中东/非洲</td>
<td align="left">EUR</td>
</tr>
<tr class="even">
<td align="left">法国</td>
<td align="left">FRA</td>
</tr>
<tr class="odd">
<td align="left">日本</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">韩国</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">北美</td>
<td align="left">NAM</td>
</tr>
<tr class="odd">
<td align="left">英国</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

添加附属位置

1. 打开 [OneDrive 管理中心](https://admin.onedrive.com)。

2. 导航到“地理位置”**** 选项卡。

3. 单击“添加位置”****。

4. 选择要添加的位置，然后单击“下一步”****。

5. 键入想要与地理位置一同使用的域，然后单击“添加”****。

6. 单击“关闭”****。

预配可能需要几小时到 72 小时，具体要取决于租户的大小。附属位置设置完成后，你将收到电子邮件确认。当新地理位置在 OneDrive 管理中心的“地理位置”**** 选项卡的地图上以蓝色显示时，你可以继续将用户的首选数据位置设置为该地理位置。 

> [!IMPORTANT]
> 你的新附属位置将使用默认设置进行设置。这可使你根据当地合规性要求来配置该附属位置。

## <a name="setting-users-preferred-data-location"></a>设置用户的首选数据位置
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

一旦启用了所需的附属位置，就可以更新你的用户帐户以使用适当的首选数据位置。我们建议你为每个用户设置一个首选数据位置，即使该用户处于中心位置。

> [!TIP]
> 我们建议你在组织内更广泛地推广多地理位置之前，请先以测试用户或少量用户来进行验证。

在 AAD 中，有两种类型的用户对象：仅限云的用户和同步用户。请按照针对用户类型的相应说明进行操作。

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>使用 AD Connect 同步用户的首选数据位置 

如果将公司的用户从本地 Active Directory 系统同步到 Azure Active Directory，则其 PreferredDataLocation 必须在 AD 中填充并同步到 AAD。请遵循 [Azure Active Directory Connect 同步：为 Office 365 资源配置首选数据位置](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation)中的过程，将首选数据位置同步从本地 Active Directory 配置为 Azure Active Directory。

我们建议你在标准用户创建工作流中加入设置用户的“首选数据位置”。

> [!IMPORTANT]
> 对于未预配 OneDrive 的新用户，请在用户的 PDL 同步到 Azure Active Directory 后至少等待 24 小时，以便在用户登录到 OneDrive for Business 之前传播更改。（在用户登录之前设置首选数据位置，以预配 OneDrive for Business，这可确保用户的新 OneDrive 将在正确的位置进行设置。）

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>为仅限云的用户设置首选数据位置 

如果公司的用户没有从本地 Active Directory 系统同步到 Azure Active Directory，这意味着它们是在 Office 365 或 Azure Active Directory 中创建的，必须使用 Azure Active Directory PowerShell 设置 PDL。

此部分中的步骤需要使用[用于 Windows PowerShell 模块的 Microsoft Azure Active Directory 模块](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)。如果已安装 Azure Active Directory PowerShell，请确保更新到最新版本。

1.  打开用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块。

2.  运行 `Connect-MsolService`，然后输入租户的全局管理员凭据。

3.  使用 [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet 来设置每位用户的首选数据位置。例如：

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    你可以使用 Get-MsolUser cmdlet 进行检查，以确认首选数据位置已正确更新。例如：

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

我们建议你在标准用户创建工作流中加入设置用户的“首选数据位置”。

> [!IMPORTANT]
> 对于未设置 OneDrive 的新用户，请在用户的 PDL 设置后至少等待 24 小时，以便在用户登录到 OneDrive 之前传播更改。（在用户登录之前设置首选数据位置，以预配 OneDrive for Business，这可确保用户的新 OneDrive 将在正确的位置进行设置。）

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive 设置和 PDL 效果

如果用户已拥有在租户中创建的 OneDrive 网站，则设置其 PDL 将不能自动移动其现有 OneDrive。若要移动该用户的 OneDrive，请参阅 [OneDrive for Business 地理位置移动](move-onedrive-between-geo-locations.md)，在地理位置之间移动 OneDrive 时，请按照其中的说明。

如果用户在租户内没有 OneDrive 网站，则假定用户的 PDL 与公司的附属位置之一相匹配，根据其 PDL 值为他们设置 OneDrive。

## <a name="configuring-multi-geo-search"></a>配置多地理位置搜索

你的多地理位置租户将具有聚合搜索功能，允许搜索查询从租户中的任何位置返回结果。

默认情况下，即使每个搜索索引位于其相关地理位置中，这些入口点的搜索也会返回聚合结果：

- OneDrive for Business

- Delve

- SharePoint 主页

- 搜索中心

此外，可为使用 SharePoint 搜索 API 的自定义搜索应用程序配置多地理位置搜索功能。

有关说明（包括任何限制和差异），请查看[为 OneDrive for Business 多地理位置配置搜索](configure-search-for-multi-geo.md)。

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>验证 OneDrive for Business 多地理位置配置

以下是在你向公司广泛推出 OneDrive for Business 多地理位置之前，可能希望将其纳入验证计划的一些基本用例。在完成了这些测试以及任何与公司相关的其他用例后，你可以选择继续添加初始试点组中的用户。

**OneDrive for Business**

从 Office 365 应用启动器中选择 OneDrive，并根据用户的 PDL 确认你已自动定向到用户的相应地理位置。OneDrive for Business 现在应该开始在该位置进行预配。完成预配后，可尝试上传和下载一些文件。

**OneDrive 移动应用**

使用测试帐户凭据登录 OneDrive 移动应用。确认你可以看到 OneDrive for business 文件，并可以通过移动设备与它们进行交互。

**OneDrive 同步客户端**

确认 OneDrive 同步客户端在登录后可自动检测你的 OneDrive for Business 地理位置。如果你需要下载同步客户端，则可单击 OneDrive 库中的“同步”****。

**Office 应用程序**

通过从 Office 应用程序（如 Word）登录，确认你可以访问 OneDrive for Business。打开 Office 应用程序，然后选择“OneDrive – <TenantName>”。Office 将检测你的 OneDrive 位置，并显示可打开的文件。

**共享**

尝试共享 OneDrive 文件。确认人员选取器向你显示所有 SharePoint 在线用户，而不管他们的地理位置如何。
