---
title: Office 365 数据销毁
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
description: 有关回收、处置或销毁 Office 365 数据中心磁盘驱动器和服务器的 Microsoft 策略的概述。
ms.openlocfilehash: 1fca278dd23e84db2c6591eefc45d0b75265cf17
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032087"
---
# <a name="office-365-data-destruction"></a>Office 365 数据销毁

## <a name="physical-data-destruction"></a>物理数据销毁

Microsoft 具有数据处理标准策略，这些策略可解决磁盘驱动器的回收和处置故障，以及服务器的故障或淘汰。 在重用任何 Office 365 磁盘驱动器之前，Microsoft 将执行物理净化过程，与美国国家标准和技术专用出版物800-88 （[NIST SP 800-88 For Media 净化指南](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-88r1.pdf)）一致。 由于 Office 365 中的所有磁盘驱动器都使用 BitLocker 卷级加密进行了加密，因此在技术上不需要 NIST SP 800-88 兼容的擦除。 尽管如此，Microsoft 也会执行此过程。

在 Office 365 数据中心内使用的故障磁盘是通过 ISO 进程物理销毁和审核的。 资产类型决定了适当的处置方法。 对于无法擦除的硬驱，Microsoft 使用销毁过程来销毁媒体，并无法恢复信息。 例如，磁盘实际损坏、pulverized 或 incinerated。 Microsoft 保留销毁的所有记录，并在 Office 365 中重用的服务器上执行类似的清理过程。 这些准则包含电子和物理净化。

每个数据中心都使用现场实际销毁进程来释放其磁盘。 为磁盘处置指定的存储媒体的安全容器位于数据中心的每个区域。 每个安全的 bin 工作站都具有视频监控监控。 一旦处置空间达到约50% 的容量，网站服务团队将与物理安全团队联系以协调删除。 网站服务人员和安全办公室删除安全处置 bin 并将其放在指定的安全存储区域中。 在处理过程中管理数据贴出设备处理的策略和程序将定期进行测试，包括确保机械销毁的设备条件的过程。

在数据销毁过程中，将以符合 NIST 800-88 的方式清除磁盘（如果可能），然后将其置于行业清除程序和物理 demolished 中。 Microsoft 为那些离开数据中心的资产提供责任，即使用 NIST SP 800-88 一致的清理/清除、资产销毁、加密、准确清查、跟踪和保护在传输过程中的保管链。 此过程通过闭合电路电视进行监控，并在完成后发出销毁证书。

Microsoft 使用来自[极限协议解决方案](https://www.enterprisedataerasure.com/)（EPS）的数据擦除单元。 EPS 软件支持对清理和清除/安全擦除的 NIST SP 800-88 要求。 在清理或销毁之前，清单由 Microsoft 资产管理器创建。 如果供应商用于销毁，供应商为销毁的每个资产提供一个销毁证书，该证书由资产管理者进行验证。

## <a name="virtual-data-destruction"></a>虚拟数据销毁

Microsoft 拥有的数据处理策略和过程可解决有效的数据虚拟数据销毁，以防止在服务租户之间不正当地共享数据或在服务中进行硬删除后可供访问的可能性。 其他服务租户无法访问从一个租户中的服务中删除的数据，即使任何基础物理存储已重新分配也是如此。 这是用于扩展虚拟环境的多个虚拟化和碎片技术的复合效果的结果，每个服务租户中应用程序的活动删除行为（如[页清零](https://docs.microsoft.com/office365/securitycompliance/office-365-exchange-online-data-deletion#page-zeroing)），以及所需的媒体和应用程序内容加密过程。