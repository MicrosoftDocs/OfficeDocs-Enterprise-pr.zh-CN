---
title: Office 365 SharePoint Online 数据删除
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
description: 对 SharePoint Online 中的数据删除的说明。
ms.openlocfilehash: 3f00e88c8d0e2bc10f6468b843385753ef864297
ms.sourcegitcommit: 4f465f690c6563cfa9f6029d3e7e9e3cace96671
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "41658319"
---
# <a name="sharepoint-online-data-deletion-in-office-365"></a>Office 365 中的 SharePoint Online 数据删除

SharePoint Online 将对象存储为应用程序数据库中的抽象代码。 当用户将文件上传到 SharePoint Online 时，会反汇编该文件并将其转换为应用程序代码，并将其存储在多个数据库的多个表中。 在 SharePoint Online 中，客户上传的所有内容都被分成多个块，并进行了加密（可能包含多个 AES 256 位密钥），并分布在整个数据中心中。 有关分块和加密过程的具体详细信息，请参阅[Microsoft 云中的加密](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview)。 

在 SharePoint Online 中，项目会从从其原始位置删除时起的93天保留一段时间。 它们将在整个时间内保持在网站回收站中，除非有人将其从那里删除或清空回收站。 在这种情况下，这些项将转到网站集的回收站，这些项将在剩余的93天内保留。 有关还原已删除项目的信息，请参阅[在 SharePoint 网站的回收站中还原项目](https://support.office.com/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
)和[从网站集回收站还原已删除的项目](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b)。 无法在 SharePoint Online 中配置回收站保留时间。

删除网站集时，还会删除集合中的网站层次结构，以及其中的所有内容：

- 文档和文档库
- 列表和列表数据
- 网站配置设置
- 与网站或其子网站相关的角色和安全信息
- 顶级网站的子网站、其内容和用户信息

如果意外删除了网站集，则可以使用 SharePoint 管理中心通过全局或 SharePoint 管理来还原网站集。

已删除的网站集将保留93天。 在93天后，将永久删除网站及其所有内容和设置，包括列表、库、页面和任何子网站。

当用户清除网站集回收站中的已删除项目、保留和备份期间过期时，或者管理员使用[remove-spodeletedsite cmdlet](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps)永久删除网站集时，将发生硬删除。 当用户硬删除（永久删除或清除） SharePoint Online 中的内容时，已删除的区块的所有加密密钥也将被删除。 以前存储已删除的区块的磁盘上的块被标记为未使用，可供重复使用。
