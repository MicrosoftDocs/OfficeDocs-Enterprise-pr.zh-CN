---
title: Office 365 搜索中的 office 365 租户隔离
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
description: 摘要： Office 365 搜索中的租户隔离说明。
ms.openlocfilehash: b35e26edc41689cfb6fded28249f71fbb72ffd11
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035759"
---
# <a name="tenant-isolation-in-office-365-search"></a>Office 365 搜索中的租户隔离

SharePoint Online 搜索使用租户分离模型来平衡共享数据结构的效率，并防止租户之间的信息泄露。 在此模型中，我们阻止搜索功能来自：

- 返回包含来自其他租户的文档的查询结果
- 在查询结果中公开足够的信息，训练有素的用户可以推断有关其他租户的信息
- 显示其他租户中的架构或设置
- 将分析处理信息混合在租户或存储结果中的错误租户中
- 使用其他租户中的字典条目

对于每种类型的租户数据，我们在代码中使用一个或多个保护层，以防止意外泄漏信息。 最关键的数据具有最多的保护层，以确保单个缺陷不会导致实际或感觉信息泄露。

## <a name="tenant-separation-for-the-search-index"></a>搜索索引的租户分离

搜索索引存储在磁盘上托管索引组件的服务器上，租户共享索引文件。 租户的已编制索引的文档仅对该租户的查询可见。 三种独立的机制防止信息泄露：

- 租户 ID 筛选
- 租户 ID 条款前缀
- ACL 检查

所有三种机制都必须失败，才能使搜索将文档返回到错误的租户。

## <a name="tenant-id-filtering-and-tenant-id-term-prefixing"></a>租户 ID 筛选和租户 ID 条款前缀

搜索将为使用租户 ID 在全文索引中编制索引的每个术语加上前缀。 例如，当 ID 为 "*123*" 的租户为术语编制索引时，全文本索引中的条目是 "*123foo"。***

每个查询都将转换为包含使用名为租户 ID 筛选的过程的租户 ID。 例如，查询 "*foo*" 将转换为 "<*guid*>。*foo*和*tenantID*： <*guid*> "，其中 <*guid*> 表示执行查询的租户。 此查询转换发生在每个索引节点中，并且不能对查询和内容处理进行影响。 由于租户 ID 已添加到每个查询中，因此无法通过在一个租户中查看最佳匹配排名来推断出其他租户中术语的频率。

租户 ID 条款前缀仅发生在全文本索引中。 上市搜索（如 "*title： foo*"）转到一个合成搜索索引，其中术语不以租户 ID 作为前缀。 相反，上市搜索将以字段名称作为前缀。 例如，查询 "*title： foo*" 将转换为 "fields：*foo 和 fields. tenantID*： <*guid*>"。 由于术语的频率不影响合成搜索索引中的命中排名，因此无需在术语 "前缀" 的情况下进行租户分隔。 对于上市搜索（如 "*title： foo*"），租户内容分离取决于租户 ID 筛选（通过查询转换）。

## <a name="document-access-control-list-checks"></a>文档访问控制列表检查

搜索控制通过在搜索索引中保存的 Acl 对文档的访问。 每个项目都使用特殊 ACL 字段中的一组术语编制索引。 ACL 字段包含可查看文档的每个组或用户一个术语。 每个查询都使用一系列访问控制项（ACE）术语进行扩充，每个查询已通过身份验证的用户所属的组一个。

例如，类似于 "<*guid*> 的查询。*FOO 和 tenantID*： <*guid*> "将变为：" <*guid*>。*foo 和 tenantID*： <*guid*> *和*（*docACL：*<*ace1*> *或 docACL*： <*ace2*> *or docACL*： <*ace3*> *...*） "

由于用户和组标识符，因此 Ace 是唯一的，因此这将为仅对某些用户可见的文档提供其他级别的安全性。 对于在租户中向常规用户授予访问权限的特殊 "除外部用户之外的任何人" ACE 也是如此。 但由于 "Everyone" 的 Ace 对于所有租户都是相同的，因此公共文档的租户分隔取决于租户 ID 筛选。 此外，还支持 Deny Ace。 当与 deny ACE 匹配时，查询扩充将添加从结果中删除文档的子句。

在 Exchange Online 搜索中，索引在邮箱 ID 上针对单个用户的邮箱（而不是租户 ID （订阅 ID））进行分区，就像在 SharePoint Online 中一样。 分区机制与 SharePoint Online 相同，但没有 ACL 筛选。
