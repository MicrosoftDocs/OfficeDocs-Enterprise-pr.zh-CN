---
title: Office 365 GCC 高和 DoD 的其他网络安全要求
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150m
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 摘要： Office 365 GCC 高和 DoD 具有额外的网络安全要求
hideEdit: true
ms.openlocfilehash: a79204809787391065ac833d9a3872af4cdc1528
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "44371628"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Office 365 GCC 高和 DOD 的其他网络安全要求

*本文适用于 Office 365 GCC 高、Office 365 DOD、Microsoft 365 GCC 高和 Microsoft 365 DOD。*

Office 365 GCC High and DOD 是安全的云环境，可满足美国政府及其供应商和合同工的需求。  这些云环境对允许服务访问的外部终结点具有额外的网络限制。

使用联合身份或混合共存计划的 GCC 高和 DOD 客户可能需要 Microsoft 允许对现有本地部署的入站和/或出站访问权限。  这些活动的示例包括：

* 联合身份（使用 Active Directory 联合身份验证服务或类似的受支持 STS）的使用
* 与本地 Exchange Server 或 Skype for Business 部署的混合共存
* 从本地系统迁移现有用户内容

若要允许服务与本地终结点进行通信，您**必须**向 Office 365 工程部门发送电子邮件，以进行网络更改。

> [!WARNING]
> 所有请求都有一个**为期三周**的 SLA，由于所需的安全和合规性控件和部署管道，无法加速。  这包括初始加入网络请求以及在迁移到服务后进行的任何更改。  请确保您的网络团队了解此日程表并将其包含在规划周期中。

请向[Office 365 政府网络白名单](mailto:o365gwlt@microsoft.com)发送一封电子邮件，其中包含以下信息：

* **到**： [Office 365 政府网络白名单](mailto:o365gwlt@microsoft.com)
* **发件人**：租户管理员-发送电子邮件**必须**与租户中的全局管理员联系人匹配
* **电子邮件主题**： OFFICE 365 GCC 高网络请求-contoso.onmicrosoft.us （将其替换为你的租户名称）

您的邮件正文应包含以下数据：

* 你的 Microsoft Online Services 租户名称（例如，contoso.onmicrosoft.com、fabrikam.onmicrosoft.us）
* 一个电子邮件通讯组列表，Microsoft 将与网络更改和/或跟踪无效子网的持续通信进行通信
* 指示是否计划将 Microsoft 团队混合与本地部署结合使用
* 联合身份系统外部可访问 URL （例如，sts.contoso.com）和 CIDR 表示法中的 IP 地址范围（例如，10.1.1.0/28）
* 以 CIDR 表示法表示的本地 PKI 证书吊销列表 URL 和 IP 地址范围
* 以 CIDR 表示法表示的 Exchange Server 本地部署的外部可访问 URL 和 IP 地址范围
* 以 CIDR 表示法表示的 Skype for Business 本地部署的外部可访问 URL 和 IP 地址范围

出于安全和合规性原因，请牢记对你的请求的以下限制：

* 每个租户有四个子网限制
* 子网必须在 CIDR 表示法中（例如 10.1.1.0/28）
* 子网范围不能大于/24
* 我们**无法**适应允许访问商业云服务（商业 Office 365、Google G 套件、Amazon Web 服务等）的请求。

在 Microsoft 收到您的请求并得到批准后，就会有为期三周的实施 SLA，且不能加速。  收到请求并在最终确认完成后，你将收到初始确认。
