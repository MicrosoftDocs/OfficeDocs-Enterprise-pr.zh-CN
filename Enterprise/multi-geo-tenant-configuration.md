---
title: OneDrive 业务多地区租户配置
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 了解如何配置 OneDrive 业务多的地区。
ms.openlocfilehash: 4ef31df802eeaedf2eecbdd295d2e359816e4909
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>OneDrive 业务多地区租户配置

配置您的 OneDrive 的租户业务多的地区之前，请确保您已经阅读了[规划 OneDrive 业务多的地区](plan-for-multi-geo.md)。按照本文中的步骤操作，您将需要您想要启用的位置和您要在其中配置这些位置的测试用户的列表。

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>将 Office 365 计划多地区功能添加到您的租户

若要使用 OneDrive 业务多的地区，需要_Office 365 中的多个地区功能_计划。使用您的帐户小组将该计划添加到您的租户。您的客户小组将连接您具有适当的授权专家并获得您配置的租户。

请注意， _Office 365 中的多个地区能力_计划的用户级服务计划。您需要为每个用户所需的 setellite 位置设立的许可证。您可以添加更多许可证随着时间的推移，因为卫星位置中添加用户。

一旦您租户已配置_Office 365 中的多个地区能力_计划，**地理位置**选项卡将变为可用的[OneDrive 管理中心](https://admin.onedrive.com)。

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>将允许数据位置 (ADL) 设置为您的租户

您必须设置允许数据位置的 SharePoint 为每个地理位置想要使用 OneDrive 业务。下表显示可用的地理位置：

<table>
<thead>
<tr class="header">
<th align="left"><strong>位置</strong></th>
<th align="left"><strong>代码</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">北美洲</td>
<td align="left">名称</td>
</tr>
<tr class="even">
<td align="left">欧洲 / 中东 / 非洲</td>
<td align="left">欧元</td>
</tr>
<tr class="odd">
<td align="left">亚太</td>
<td align="left">APC 公司</td>
</tr>
<tr class="even">
<td align="left">澳大利亚</td>
<td align="left">澳大利亚</td>
</tr>
<tr class="odd">
<td align="left">日本</td>
<td align="left">日文</td>
</tr>
<tr class="even">
<td align="left">加拿大</td>
<td align="left">可以</td>
</tr>
<tr class="odd">
<td align="left">英国</td>
<td align="left">GBR</td>
</tr>
<tr class="even">
<td align="left">韩国</td>
<td align="left">韩文</td>
</tr>
</tbody>
</table>

若要添加一个附属的地理位置

1. 打开[OneDrive 管理中心](https://admin.onedrive.com)。

2. 导航到**地理位置**选项卡。

3. 单击**添加位置**。

4. 选择要添加的位置，然后单击**下一步**。

5. 键入您想要使用的地理位置，域，然后单击**添加**。

6. 单击"关闭"。

完成资源调配的附属位置后，您将收到电子邮件确认。当新的地理位置出现在蓝色上 OneDrive 管理中心中的**地理位置**选项卡上的映射时，您可以继续该地理位置设置用户的首选的数据位置。 

> [!IMPORTANT]
> 使用默认设置，将设置新卫星地理位置。这将允许您配置该地理位置适合于您的本地法规遵从性需要。

## <a name="setting-users-preferred-data-location"></a>设置用户首选的数据位置
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

一旦您启用所需的数据的位置，您可以更新您的用户帐户以使用适当的数据的位置。建议您设置每个用户的首选的数据位置，即使该用户保持在默认数据位置。

> [!TIP]
> 我们建议您多地区功能推广到更广泛组织之前开始验证与测试用户或用户组小。

在 AAD 有两种类型的用户对象： 云只有用户和同步的用户。请按照相应说明，您的用户类型。

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>同步用户的首选数据位置使用 AD 连接 

如果您的公司用户从内部活动目录 (AD) 系统同步到 Azure 活动目录 (AAD)，必须在广告中填充并同步到 AAD 他们 PreferredDataLocation。请按照中的过程， [Azure AD 连接同步： 更改了默认配置](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration)配置首选数据位置同步从内部到 AAD 的广告。

我们建议，包括设置用户的首选数据位置作为标准用户创建工作流的一部分。

> [!IMPORTANT]
> 为新用户设置没有 OneDrive，等待至少 24 小时之后用户的 PDL 同步到所做的更改的 AAD 传播之前该用户在登录到 OneDrive 的业务。（设置首选的数据位置之前用户登录时提供的业务及其 OneDrive 可确保在正确的位置，将提供用户的新 OneDrive。）

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>为云只有用户设置首选数据位置 

如果您的公司用户不同步从内部活动目录 (AD) 系统到 Azure 活动目录 (AAD)，即用 Office 365 或 AAD，然后 PDL 必须设置使用 AAD PowerShell。

本节中的步骤需要[Microsoft Azure 活动目录的 Windows PowerShell 模块](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)。如果您已经安装的 AAD PowerShell，请确保您更新为最新版本。

1.  打开 Windows PowerShell Microsoft Azure Active Directory 模块。

2.  运行`Connect-MsolService`为您的租户输入全局管理员凭据。

3.  使用[组 MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet 来设置每个用户的首选的数据位置。例如：

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    您可以检查以确认首选的数据位置已正确更新，可以使用 Get MsolUser cmdlet。例如：

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

我们建议，包括设置用户的首选数据位置作为标准用户创建工作流的一部分。

> [!IMPORTANT]
> 为新用户设置没有 OneDrive，等待至少 24 小时之后用户的 PDL 设置的更改将传播到 SharePoint OneDrive 在用户登录之前。（设置首选的数据位置之前用户登录时提供的业务及其 OneDrive 可确保在正确的位置，将提供用户的新 OneDrive。）

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive 资源调配以及 PDL 的效果

如果用户已在组织中创建的 OneDrive 网站，设置其 PDL 不会自动移动他们现有的 OneDrive。若要移动用户的 OneDrive，请参阅[OneDrive 移动业务地区的](move-onedrive-between-geo-locations.md)地理位置之间请按照移动 OneDrive 中的说明进行操作。

如果用户不具有组织内的 OneDrive 网站，OneDrive 中将提供它们为 PDL 值，根据假设用户 PDL 匹配的公司允许的数据位置 (ADLs) 之一。

## <a name="configuring-multi-geo-search"></a>配置多地区搜索

多个地区组织将具有聚合搜索功能允许搜索查询返回结果，从任何地方组织内。

默认情况下，从这些入口点的搜索将返回聚合结果，即使每个搜索索引在其相关的地理位置：

- OneDrive 为公司的

- Delve

- SharePoint 主页

- 搜索中心

此外，多地区搜索功能可以配置为自定义搜索应用程序使用 SharePoint 搜索 API。

请包括任何限制和差异的说明，查看[配置搜索 OneDrive 业务多的地区](configure-search-for-multi-geo.md)。

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>验证业务多地区配置 OneDrive

下面是您可能希望验证计划之前广泛推出 OneDrive 业务多的地区为您的公司中包括一些基本的用例。一旦完成这些测试，与贵公司相关的任何其他使用用例，您可以选择将上移动到初始实验组中添加用户。

**OneDrive 为公司的**

从 Office 365 提供应用程序启动程序中选择 OneDrive，并确认被自动定向到合适的地理位置的用户，根据用户的 PDL。OneDrive 为企业现在应该开始在该位置设置。一次调配，重试上载和下载某些文档。

**OneDrive 移动应用程序**

登录到您的测试帐户凭据与您 OneDrive 移动应用程序。请确认您可以看到您的业务文件 OneDrive，并可以从您的移动设备与它们进行交互。

**OneDrive 同步客户端**

请确认 OneDrive 同步客户端会自动检测您的业务的地理位置在登录时的 OneDrive。如果您需要下载同步客户端，您可以单击 OneDrive 库中的**同步**。

**Office 应用程序**

请确认您可以访问 OneDrive 业务为通过从 Office 应用程序 （如 Word) 记录。打开 Office 应用程序，然后选择"OneDrive- <TenantName>"。办公室将检测您的 OneDrive 位置并显示您可以打开的文件。

**Sharing**

尝试共享 OneDrive 文件。确认人员选取器显示您所有 SharePoint 联机用户无论其地理位置如何。
