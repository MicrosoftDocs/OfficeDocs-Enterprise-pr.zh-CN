---
title: Azure Active Directory 中的 Office 365 隔离和访问控制
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
description: 摘要：隔离和访问控制如何在 Azure Active Directory 中工作。
ms.openlocfilehash: d1f3a10d44a949511236d5adce38693ad2ad5c04
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067222"
---
# <a name="isolation-and-access-control-in-azure-active-directory"></a>Azure Active Directory 中的隔离和访问控制

Azure Active Directory 旨在通过逻辑数据隔离以一种高度安全的方式托管多个租户。 对 Azure Active Directory 的访问通过授权层进行了封闭。 Azure Active Directory 将租户容器的客户与安全边界相隔离，以保护客户的内容，以使其无法通过共同租户访问或泄露内容。 由 Azure Active Directory 的授权层执行三项检查：
- 是否为主体启用了对 Azure Active Directory 租户的访问权限？
- 是否为主体启用了对此租户中的数据的访问权限？
- 此租户中的主体角色是否已授权用于请求的数据访问类型？

没有适当的身份验证和令牌或证书，无需应用程序、用户、服务器或服务即可访问 Azure Active Directory。 如果请求未附带正确的凭据，则会被拒绝。

实际上，Azure Active Directory 将每个租户托管在其自己的受保护容器中，并将策略和权限包含在由租户完全拥有和管理的容器中。
 
![Azure 容器](media/office-365-isolation-azure-container.png)

租户容器的概念在所有层的目录服务中深度 ingrained，从门户一直到永久存储。 即使将多个 Azure Active Directory 租户元数据存储在同一物理磁盘上，在目录服务定义的其他容器之间没有任何关系，后者又由租户管理员决定。 在没有事先通过授权层的情况下，可以从任何请求的应用程序或服务中直接连接到 Azure Active Directory 存储。

在下面的示例中，Contoso 和 Fabrikam 都有独立的专用容器，即使这些容器可以共享一些相同的基本基础结构（如服务器和存储），它们仍然彼此独立且相互独立，并通过授权和访问控制层。
 
![Azure 专用容器](media/office-365-isolation-azure-dedicated-containers.png)

此外，没有可以从 Azure Active Directory 中执行的应用程序组件，并且一个租户无法强制实施另一个租户的完整性、访问其他租户的加密密钥或从服务器读取原始数据。

默认情况下，Azure Active Directory 不允许由其他租户中的标识颁发的所有操作。 每个租户通过基于声明的访问控制在 Azure Active Directory 中逻辑隔离。 目录数据的读取和写入作用域为租户容器，并由内部抽象层和基于角色的访问控制（RBAC）层（共同将租户强制为安全边界）封闭。 每个目录数据访问请求都由这些层处理，Office 365 中的每个访问请求都是通过上述逻辑 policed 的。

Azure Active Directory 具有北美、美国政府、欧洲联合、德国和全球通用分区。 一个租户存在于单个分区中，分区可以包含多个租户。 对分区信息进行抽象，使其远离用户。 给定分区（包括其中的所有租户）将复制到多个数据中心中。 租户的分区是根据租户的属性（例如，国家/地区代码）选择的。 使用专用密钥对每个分区中的机密和其他敏感信息进行加密。 创建新分区时，会自动生成密钥。

Azure Active Directory 系统功能是每个用户会话的唯一实例。 此外，Azure Active Directory 使用加密技术在网络级别提供共享系统资源的隔离，以防止未经授权和无意的信息传输。
