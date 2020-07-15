---
title: Microsoft 365 多地理位置
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 利用 Microsoft 365 多地理位置将 Microsoft 365 触及范围扩展到多个地理区域。
ms.openlocfilehash: a49ba9b9b5109972a6b0a631d34d14acb189f484
ms.sourcegitcommit: 6b12e3ab76809d5632923def7ee367cd48ef3ccc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2020
ms.locfileid: "45117274"
---
# <a name="microsoft-365-multi-geo"></a>Microsoft 365 多地理位置

利用 Microsoft 365 多地理位置，你的组织可将其 Microsoft 365 触及范围扩展到你的现有租户内的多个地理区域和/或国家或地区。 请联系 Microsoft 帐户团队，为 Microsoft 365 多地理位置注册你的跨国公司。
  
通过 Microsoft 365 多地理位置，你可以在选择的地理位置中预配和存储静态数据，以满足数据驻留要求，与此同时，开启面向员工的现代生产力体验的全球推广。

#### <a name="video-introducing-microsoft-365-multi-geo"></a>视频：介绍 Microsoft 365 多地理位置

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1Yk6B?autoplay=false]

在多地理位置环境中，Microsoft 365 租户由（最初在其中设置了 Microsoft 365 订阅）的中心位置以及一个或多个附属位置组成。 在多地理位置租户中，有关地理位置、组和用户信息的信息是在 Azure Active Directory (Azure AD) 中进行管控。 由于系统会集中管理你的租户信息并同步到每个地理位置中，因此共享操作以及涉及到公司中任何人的体验均包含全局意识。

![SharePoint 管理中心中多地理位置地图的屏幕截图](media/multi-geo-world-map.png)

请注意，Microsoft 365 多地理位置旨在满足数据驻留需求，而不是优化性能。 若要了解 Microsoft 365 性能优化，请参阅 [Microsoft 365 的网络计划和性能调整](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)，或与支持群组联系。

## <a name="terminology"></a>术语

下面是用于描述 Microsoft 365 多地理位置的关键术语：

- **中心位置** - 最初在其中设置你的租户的地理位置。
- **地理位置管理员** - 可管理一个或多个指定附属位置的管理员。
- **地理位置代码** - 给定地理位置的三个字母的代码。
- **地理位置** - 可在多地理位置租户中用于托管数据的地理位置，包括 Exchange 邮箱以及 OneDrive 和 SharePoint 站点。
- **首选数据位置 (PDL)** - 管理员设置的一个用户属性，指明应在其中设置 Exchange 邮箱和 OneDrive 的地理位置。 PDL 还确定在何处设置用户创建的 SharePoint 站点。
- **附属位置** – 多地理位置租户中在其中启用地理位置感知 Microsoft 365 工作负载（SharePoint、OneDrive 和 Exchange）的地理位置。
- **租户** - 组织在 Microsoft 365 中的表示形式，通常有一个或多个关联域（例如，contoso.com）。

## <a name="licensing"></a>许可

将 Microsoft 365 多地理位置作为以下 Microsoft 365 订阅计划的附加功能，向其租户中最少有 250 个 Microsoft 365 席位并且这些席位中至少有 5% 使用多地理位置的 EA 客户提供。 有关详细信息，请与 Microsoft 帐户团队联系。

- Microsoft 365 F1、E1、E3 或 E5
- Exchange Online 计划 1 或计划 2
- OneDrive for Business 计划 1 或计划 2
- SharePoint Online 计划 1 或计划 2

## <a name="microsoft-365-multi-geo-availability"></a>Microsoft 365 多地理位置可用性

Microsoft 365 多地理位置当前在以下国家和地区提供：

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a>入门

请按照以下步骤开始使用多地理位置：

1. 与你的帐户团队协作，_在 Microsoft 365 服务计划中添加多地理位置功能_。 他们将指导你添加需要的许可证数量。 Microsoft 365 订阅数至少为 250 个的 EA 客户可以使用多地理位置功能。

   Microsoft 需要为多地理位置支持配置你的 Exchange Online 租户，然后你才能开始使用 Microsoft 365 多地理位置。 这个一次性配置流程在你订购“*Microsoft 365 中的多地理位置功能*”服务计划之后触发，并且许可证将显示在你的租户中。 应用了多地理位置许可证之后，你将在 [Microsoft 365 消息中心](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093)中收到通知，你随后就可以开始配置和使用 Microsoft 365 多地理位置功能。

2. 阅读[规划多地理位置环境](plan-for-multi-geo.md)。

3. 了解[管理多地理位置环境](administering-a-multi-geo-environment.md)和[你的用户将对环境有怎样的体验](multi-geo-user-experience.md)。

4. 准备好设置 Microsoft 365 多地理位置时，请[为多地理位置配置你的租户](multi-geo-tenant-configuration.md)。

5. [设置搜索](configure-search-for-multi-geo.md)。

## <a name="see-also"></a>另请参阅

[Exchange Online 和 OneDrive 中的多地理位置功能](https://Aka.ms/GoMultiGeo)

[OneDrive 和 SharePoint Online 中的多地理位置功能](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)

[Exchange Online 中的多地理位置功能](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-exchange-online)

[多地理位置环境中的 Teams 体验](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo)
