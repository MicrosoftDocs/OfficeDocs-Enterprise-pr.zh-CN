---
title: 调整 Exchange Online 性能
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: 本文包含一般的提示和告诉您如何提高 Exchange online 的性能的其他资源的链接。
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539899"
---
# <a name="tune-exchange-online-performance"></a>调整 Exchange Online 性能

本文包含一般的提示和告诉您如何提高 Exchange online 的性能的其他资源的链接。本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)项目的一部分。
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>为了提高 Exchange Online 的性能注意事项

若要提高迁移速度并减少组织的带宽限制的 Exchange Online，考虑下列问题：
  
- **减小邮箱大小。** 减小邮箱大小可提高迁移速度。 
    
- **将邮箱移动功能与 Exchange 混合部署一起使用。** 在 Exchange 混合部署中，脱机邮件（.OST 文件格式）在迁移到 Exchange Online 时不需要重新下载。这可以大大降低下载带宽要求。 
    
- **将邮箱移动安排在低 Internet 通信和低内部部署 Exchange 使用的时间段内进行。** 当计划移动时，迁移请求将提交到邮箱复制代理，并且可能不会立即发生。 
    
- **使用 web 上的 Outlook 精益 popouts。** 精益 popouts 更小，请提供更少内存密集型版本的 Microsoft 边缘或 Internet Explorer 中的呈现服务器上的某些组件某些电子邮件。有关详细信息，请参阅[使用精益 popouts 以减少内存使用阅读邮件时](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)。
    
有关 Exchange 迁移性能的详细信息，请参阅[Office 365 迁移性能和最佳做法](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)。
  

