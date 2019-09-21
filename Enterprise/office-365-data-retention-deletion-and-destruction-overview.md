---
title: Office 365 中的数据保留、删除和销毁
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
description: 有关针对数据保留、删除和销毁的 Office 365 的 Microsoft 策略的概述。
ms.openlocfilehash: 08b04e4fec762249208acb626fa20562ffecb82f
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067246"
---
# <a name="data-retention-deletion-and-destruction-in-office-365"></a>Office 365 中的数据保留、删除和销毁

Microsoft 具有 Office 365 的数据处理标准策略，用于指定客户数据在删除后保留多长时间。 在以下两种情况下，将删除客户数据：

- **主动删除：** 租户具有活动订阅，用户删除数据，或管理员删除用户提供的数据。
- **被动删除：** 租户订阅结束。

## <a name="data-retention"></a>数据保留

对于每个删除方案，下表显示了数据类别和分类的最大数据保留期：

| 数据类别 | 数据分类 | 说明 | 示例 | 保留期 |
|-----------------|-----------------|-----------------|----------------------------------|-------------------------------|
| 客户数据 | 客户内容| 由管理员和用户直接提供/创建的内容 <br><br> 使用 Office 365 中的服务时，包括所有文本、声音、视频、图像文件以及软件在 Microsoft 数据中心内创建和存储的软件 | 最常用的 Office 365 应用程序的示例，这些应用程序允许用户创作数据包括 Word、Excel、PowerPoint、Outlook 和 OneNote <br><br> 客户内容还包括由客户拥有/提供的机密（密码、证书、加密密钥、存储密钥） | **主动删除方案：** 最多30天 <br><br> **被动删除方案：** 最多180天 |
| 客户数据 | 最终用户身份信息（EUII） | 标识或可用于标识 Microsoft 服务用户的数据。 EUII 不包含客户内容 | 用户名或显示名称（域 \ 用户名） <br><br> 用户主体名称（name @ domain） <br><br>  特定于用户的 IP 地址 | **主动删除方案：** 最多180天（仅租户管理员操作） <br><br> **被动删除方案：** 最多180天 |
| 个人数据 <br> （客户数据中未包含的数据） | 最终用户匿名标识符（EUPI） | Microsoft 创建的与 Microsoft 服务用户关联的标识符。 与其他信息（如 mapping 表）结合使用时，EUPI 标识最终用户 <br><br> EUPI 不包含由客户上传或创建的信息 | 用户 Guid、PUIDs 或 Sid <br><br> 会话 Id | **主动删除方案：** 最多30天 <br><br> **被动删除方案：** 最多180天 |

## <a name="subscription-retention"></a>订阅保留

在活动订阅的期限内，订阅者可以访问、提取或删除存储在 Office 365 中的客户数据。 如果付费订阅结束或终止，Microsoft 会在90天内将存储在 Office 365 中的客户数据保留为天，以使订阅者能够提取数据。 在90天的保留期结束后，Microsoft 将禁用该帐户并删除客户数据。 在过期或终止对 Office 365 的订阅后，不超过180天，Microsoft 将禁用该帐户并删除帐户中的所有客户数据。 一旦所有数据的最大保留期已过，数据将以商业方式呈现，从而无法恢复。

对于免费试用版，你的帐户在大多数国家和地区中的30天内将转入宽限期状态。 在此宽限期期间，您可以购买 Office 365。 如果您决定不购买 Office 365，您可以取消试用或让宽限期过期，并删除试用版帐户信息和数据。

## <a name="expedited-deletion"></a>加速删除

对于任何订阅，订阅者都可以与 Microsoft 支持人员联系，并请求加速订阅的取消设置。 在此过程中，管理员输入 Microsoft 提供的锁定代码后，将在三天内删除所有用户数据。 这包括 SharePoint Online 中的数据和 Exchange Online 中的 "保留" 或 "存储在非活动邮箱中"。

有关加速取消设置的详细信息，请参阅[取消 Office 365](https://support.office.com/article/Cancel-Office-365-for-business-b1bc0bef-4608-4601-813a-cdd9f746709a)。

## <a name="related-links"></a>相关链接
- [数据销毁](office-365-data-destruction.md)
- [Office 365 中的永久性](office-365-data-immutability.md)
- [Exchange Online 数据删除](office-365-exchange-online-data-deletion.md)
- [SharePoint Online 数据删除](office-365-sharepoint-online-data-deletion.md)
- [Skype for Business 数据删除](office-365-skype-data-deletion.md)