---
title: 设置 Office 365 的目录同步
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: 了解如何设置 Office 365 和本地 Active directory 之间的目录同步。
ms.openlocfilehash: 03f824da6feb41791e12818d8da2e298dc633f4e
ms.sourcegitcommit: 7814d01db4d7618fc2f9381faef1a6a45ea063fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2019
ms.locfileid: "30492942"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>设置 Office 365 的目录同步

Office 365 使用基于云的用户标识管理服务 Azure Active Directory 来管理用户。 您还可以通过将本地环境与 Office 365 同步, 将本地 Active Directory 与 Azure AD 集成。 设置同步后, 您可以决定在 Azure AD 中或在本地目录中进行用户身份验证。
  
## <a name="office-365-directory-synchronization"></a>Office 365 目录同步

您可以使用本地组织与 Office 365 之间的同步标识或联合身份。 使用同步标识, 可以在本地管理用户, 并在 Azure AD 在本地使用云中的相同密码时对它们进行身份验证。 这是最常见的目录同步方案。 传递身份验证或联合身份允许您在本地管理用户, 并通过本地目录进行身份验证。 联合身份需要进行额外的配置, 并允许用户仅登录一次。 有关详细信息, 请阅读[了解 Office 365 标识和 Azure Active Directory](about-office-365-identity.md)。
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>要从 Windows azure active directory 同步 (DirSync) 升级到 Azure active directory Connect？

如果你当前正在使用 DirSync 并希望升级, 请转到[azure.com](https://azure.com)以获取[升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。
  
## <a name="prerequisites-for-azure-ad-connect"></a>Azure AD Connect 的先决条件

你可以使用 Office 365 订阅获取 Azure AD 的免费订阅。 设置目录同步时, 将在其中一台本地服务器上安装 Azure Active directory Connect。
  
对于 Office 365, 你将需要:
  
- 验证您的内部部署域 (此过程将指导您完成此过程)。
- 在[office 365 中分配管理员角色](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504), 以获取 office 365 租户和本地 Active Directory 的业务权限。

对于您在其上安装 Azure AD Connect 的本地服务器, 你将需要以下软件:
  
|**服务器操作系统**|**其他软件**|
|:-----|:-----|
|**Windows Server 2012 R2** | -默认情况下, 安装了 PowerShell, 无需执行任何操作。  <br> -通过 Windows 更新提供 Net 4.5.1 及更高版本。 确保已在控制面板中将最新的更新安装到 Windows Server。 |
|**windows server 2008 R2 Service Pack 1 (SP1)** 或**windows server 2012** | -Windows Management Framework 4.0 中提供了最新版本的 PowerShell。 在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)搜索它。  <br> -.net 4.5.1 及更高版本在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)提供。 |
|**Windows Server 2008** | -支持的最新版本的 PowerShell 可在 Windows Management Framework 3.0 中提供, 可在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)上找到。  <br> -.net 4.5.1 及更高版本在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)提供。 |

> [!NOTE]
> 如果使用的是 Azure active directory DirSync, 可以从本地 Active directory 同步到 Azure active directory 的通讯组成员的最大数量为15000。 对于 Azure AD Connect, 该号码为50000。 
  
若要更仔细地查看硬件、软件、帐户和权限要求、SSL 证书要求以及 azure AD connect 的对象限制, 请阅读[azure Active Directory connect 的先决条件](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites)。
  
您还可以查看 Azure AD Connect[版本的历史记录](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history), 以查看每个版本中包含和修复的内容。

## <a name="to-set-up-directory-synchronization"></a>设置目录同步

1. 登录到 Office 365 管理中心, 然后选择左侧导航栏中的 "**用户** \> **活动用户**"。
2. 在 Office 365 管理中心的 "**活动用户**" 页上, 选择 "**更多** \> **目录同步**"。

    ![在 "更多" 菜单中选择 "目录同步"](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. 在 " **Active directory 准备**" 页上, 选择 "**下载 Microsoft Azure Active Directory Connect 工具**" 链接开始。 有关 azure Active Directory Connect 安装过程的详细信息, 请参阅[azure ad connect 和 azure AD connect Health 安装路线图](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)。

## <a name="assign-licenses-to-synchronized-users"></a>将许可证分配给同步用户

将用户同步到 Office 365 之后, 将会创建这些用户, 但需要向其分配许可证, 以便它们可以使用 Office 365 功能 (如 mail)。 有关说明, 请参阅[在 Office 365 for business 中向用户分配许可证](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。

## <a name="finish-setting-up-domains"></a>完成域设置

当您管理 DNS 记录以完成域设置时, 请按照[为 Office 365 创建 dns 记录](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)中的步骤操作。