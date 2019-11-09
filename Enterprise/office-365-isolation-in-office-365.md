---
title: Office 365 中的 office 365 隔离和访问控制
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
- SPO_Content
description: 摘要： Office 365 的各种应用程序中的隔离和访问控制说明。
ms.openlocfilehash: 5855828faafaf12e609e93a1a4f0ec7419e0a9d6
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078161"
---
# <a name="isolation-and-access-control-in-office-365"></a>Office 365 中的隔离和访问控制

Azure Active Directory 和 Office 365 使用高度复杂的数据模型，其中包括数十个服务、数百个实体、数千个关系和数十个属性。 在较高级别，Azure Active Directory 和服务目录是使用基于状态的复制协议保持同步的租户和收件人的容器。 除了 Azure Active Directory 中保留的目录信息外，每个服务工作负载都有自己的目录服务基础结构。
 
![Office 365 租户数据同步](media/office-365-isolation-tenant-data-sync.png)

在此模型中，没有一个目录数据源。 特定系统拥有单独的数据片段，但没有单个系统保存所有数据。 在此数据模型中，Office 365 服务与 Azure Active Directory 合作。 Azure Active Directory 是共享数据的 "真实系统"，它通常是每个服务使用的小型和静态数据。 Office 365 和 Azure Active Directory 中使用的联合模型提供了数据的共享视图。

Office 365 同时使用物理存储和 Azure 云存储。 Exchange Online （包括 Exchange Online Protection）和 Skype for Business 将自己的存储用于客户数据。 SharePoint Online 同时使用 SQL Server 存储和 Azure 存储，因此需要在存储级别对客户数据进行额外的隔离。

## <a name="exchange-online"></a>Exchange Online

Exchange Online 将客户数据存储在邮箱中。 邮箱托管在称为 "邮箱数据库" 的可扩展存储引擎（ESE）数据库中。 这包括用户邮箱、链接邮箱、共享邮箱和公用文件夹邮箱。 用户邮箱包括保存的 Skype for Business 内容，如对话历史记录。

用户邮箱内容包括：

- 电子邮件和电子邮件附件
- 日历和忙/闲信息
- 联系人
- 任务
- 注释
- 组
- 推理数据

Exchange Online 中的每个邮箱数据库包含来自多个租户的邮箱。 授权代码可保护每个邮箱，包括租赁内。 默认情况下，只有分配的用户才有权访问邮箱。 保护邮箱的访问控制列表（ACL）包含在租户级别通过 Azure Active Directory 进行身份验证的标识。 每个租户的邮箱仅限于对租户的身份验证提供程序的身份进行身份验证，其中仅包含来自该租户的用户。 租户 A 中的用户无法以任何方式获取租户 B 中的内容，除非租户 A 明确批准。

## <a name="skype-for-business"></a>Skype for Business

Skype for Business 将数据存储在不同的位置：

- 用户和帐户信息（包括连接终结点、租户 Id、拨号计划、漫游设置、状态状态、联系人列表等）存储在 Skype for Business Active Directory 服务器和各种 Skype for Business 数据库服务器中。 如果为用户启用了这两个产品或 Skype for business 服务器（如果用户不是这样），则联系人列表存储在用户的 Exchange Online 邮箱中。 Skype for Business 数据库服务器不按租户分区，但通过基于角色的访问控制（RBAC）强制实施多租户数据隔离。
- 会议内容和上载的数据存储在分布式文件系统（DFS）共享上。 如果启用此内容，还可以将其存档在 Exchange Online 中。 DFS 共享不按租户分区。 内容是通过 RBAC 强制实施的，而多租户则通过 RBAC 进行保护。
- 呼叫详细信息记录（如呼叫历史记录、IM 会话、应用程序共享、IM 历史记录等）也可以存储在 Exchange Online 中，但大多数呼叫详细信息记录临时存储在呼叫详细信息记录（CDR）服务器上。 不对每个租户对内容进行分区，但通过 RBAC 强制实施了多租户。

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online 具有几种独立的机制，可提供数据隔离。 它将对象存储为应用程序数据库中的抽象代码。 例如，当用户将文件上传到 SharePoint Online 时，文件将被反汇编，转换为应用程序代码，并存储在多个数据库中的多个表中。

如果用户可以直接访问包含数据的存储，则不会将内容 interpretable 到 SharePoint Online 之外的人或任何系统。 这些机制包括安全访问控制和属性。 所有 SharePoint Online 资源均由授权代码和 RBAC 策略（包括租赁中的）进行保护。 保护资源的访问控制列表（ACL）包含在租户级别进行身份验证的标识。 租户的 SharePoint Online 数据仅限于由租户的身份验证提供程序身份验证的标识。

除了 Acl 之外，指定身份验证提供程序（即租户特定的 Azure Active Directory）的租户级别属性只写入一次，并且在设置后不能更改。 为租户设置身份验证提供程序租户属性后，将无法使用公开给租户的任何 Api 对其进行更改。

每个租户都使用唯一的*SubscriptionId* 。 所有客户网站均由租户拥有，并向其分配了对租户唯一的*订阅*。 网站上的*SubscriptionId*属性只写入一次，并且是永久的。 一旦分配给租户，便无法将网站移至其他租户。 *SubscriptionId*是用于为身份验证提供程序创建安全作用域并与租户关联的密钥。

SharePoint Online 使用 SQL Server 和 Azure 存储来存储内容元数据。 内容存储的分区键是在 SQL 中*SiteId* 。 运行 SQL 查询时，SharePoint Online 将使用验证为租户级别*SubscriptionId*检查的一部分的*SiteId* 。

SharePoint Online 将加密文件内容存储在 Microsoft Azure blob 中。 每个 SharePoint Online 场都有自己的 Microsoft Azure 帐户，保存在 Azure 中的所有 blob 都使用存储在 SQL 内容存储中的密钥进行单独加密。 加密密钥受授权层在代码中保护，且不会直接向最终用户公开。 SharePoint Online 具有实时监控，可在 HTTP 请求读取或写入多个租户的数据时进行检测。 将针对访问的资源的*SubscriptionId*跟踪请求标识*SubscriptionId* 。 最终用户永远不应发生访问多个租户的资源的请求。 多租户环境中的服务请求是唯一的例外。 例如，搜索爬网程序一次性提取整个数据库的内容更改。 这通常涉及在单个服务请求中查询多个租户的网站，这是出于提高效率的原因而完成的。
