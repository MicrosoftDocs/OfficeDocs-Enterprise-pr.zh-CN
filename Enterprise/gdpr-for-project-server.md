---
title: 适用于 Project Server 的 GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 了解如何解决本地 Project Server 中的 GDPR 要求。
ms.openlocfilehash: 6a630dc4cef2c4117e0ba25497f898d0b8da221b
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-project-server"></a>适用于 Project Server 的 GDPR

Project Server 使用自定义脚本在 Project Web App 中导出和修订用户数据。基本过程是：

1.  在服务器场中找到 Project Web App 网站。

2.  在包含此用户的每个网站中找到项目。

3.  导出并查看想要查看的数据类型。

4.  根据需要修订数据。

下文详细介绍了这些步骤：

- [从 Project Server 中导出用户数据](/Project/export-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)

- [从 Project Server 中删除用户数据](/Project/delete-user-data-from-project-server?toc=/Office365/Enterprise/toc.json)


请注意，Project Server 构建于 SharePoint Server 之上，并将事件记录到 SharePoint ULS 日志和使用情况数据库中。
