---
title: 用于本地文件共享的 GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 了解如何解决本地 Windows Server 文件共享中的 GDPR 要求。
ms.openlocfilehash: d9d17f134d77ee03e11208744ba9a2e56d506b1f
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-on-premises-windows-server-file-shares"></a>用于本地 Windows Server 文件共享的 GDPR

推荐的基本文件共享方法是：

-   使用 Azure 信息保护来标记敏感数据。

-   使用 Azure 信息保护扫描程序来查找数据。

推荐的文件共享方法包括下列步骤：

1.  **安装并配置 Azure 信息保护扫描程序。**

    -   决定要使用的敏感数据类型。

    -   指定要使用的本地文件夹和网络共享。

2.  **完成发现周期。**

    -   以发现模式运行扫描程序并验证查找结果。

    -   如果需要，优化条件和敏感信息类型。

    -   评估自动应用标签的预期影响。

3.  **运行 Azure 信息保护扫描程序以便标记合格文档**

4.  **用于保护：**

    -   配置 Exchange 数据丢失防护规则以保护具有所需标签的文档。

    -   务必要使用权限来限制谁可以访问文件。

5.  **要进行监控，请使用 SIEM 工具集成 Windows Server 日志。**

    -   要为数据主体请求查找个人数据，请使用 Azure 信息保护扫描程序。还可以配置 SharePoint Server 搜索以爬网文件共享。

有关使用 Azure 信息保护扫描程序查找和标记个人数据的详细信息，请参阅位于 [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>) 中的 Microsoft GDPR 数据发现工具包。

有关配置条件扫描程序和使用 Office 365 数据丢失防护 (DLP) 敏感信息类型的信息，请参阅[如何配置 Azure 信息保护的自动和建议分类的条件](https://docs.microsoft.com/zh-CN/information-protection/deploy-use/configure-policy-classification)。请注意，新的 Office 365 敏感信息类型不会立即可供扫描程序使用，并且自定义敏感信息类型不能与扫描程序一起使用。
