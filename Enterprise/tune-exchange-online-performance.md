---
title: 优化 Exchange Online 性能
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: 本文包含一般提示和指向其他资源的链接，这些链接告诉您如何提高 Exchange Online 的性能。
ms.openlocfilehash: 4ef0276345a3d7f1c9aeba016824f9cb06c475cb
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841079"
---
# <a name="tune-exchange-online-performance"></a>优化 Exchange Online 性能

本文包含的常规提示和指向其他资源的链接，这些链接告诉您如何提高 Exchange Online 的性能（尤其是在迁移之前）。 本文是 Office 365 项目的[网络规划和性能调整](https://aka.ms/tune)的一部分。
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>为了改进 Exchange Online 性能，需要考虑的事项

若要提高迁移速度并减少组织的 Exchange Online 带宽限制，请考虑以下事项：
  
- **减小邮箱大小。** 邮箱大小较小可提高迁移速度。 
    
- **将邮箱移动功能与 Exchange 混合部署结合使用。** 使用 Exchange 混合部署时，脱机邮件（格式为）。OST 文件）在迁移到 Exchange Online 时不需要重新下载。 这极大地降低了下载带宽要求。 
    
- **将邮箱移动安排在 Internet 流量较低和本地 Exchange 使用较低的时段发生。** 在安排移动时，迁移请求将提交到邮箱复制代理，并且不会立即生效。 
    
- **对 web 上的 Outlook 使用精益弹出内容。** 精益弹出内容通过在服务器上呈现一些组件，在 Microsoft Edge 或 Internet Explorer 中提供特定电子邮件的较小、占用大量内存的版本。 有关详细信息，请参阅[使用精益弹出内容以减少阅读邮件时使用的内存](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)。


## <a name="general-advice"></a>一般建议

- 确保 outlook.office.com 的 DNS 查找在你的位置的逻辑入口位置输入 MS 数据中心。

- 研究邮箱缓存并选择适当的选项（re）。 缓存期，共享邮箱缓存，et。

- 将 Outlook 数据传递到 Internet 之前，请保留 VPN 连接（到中央办公室）。

- 请确保您的邮箱数据符合对文件夹、项目、数量的限制。
    
有关 Exchange 迁移性能的详细信息，请参阅[Office 365 迁移性能和最佳实践](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)。
  

