---
title: 设置 Office 365 目录同步
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
description: 了解如何设置 Office 365 和本地 Active Directory 之间的目录同步。
ms.openlocfilehash: d549d2b56ef1d642e5dfc16b747e6eb909dd7337
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844043"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>设置 Office 365 目录同步

*此文章适用于 Office 365 企业版和 Microsoft 365 企业版。*

Office 365 使用 Azure Active Directory （Azure AD）租户存储和管理用于访问基于云的资源的身份验证和权限的标识。 

如果你具有本地 Active Directory 域服务（AD DS），则可以将 AD DS 用户帐户、组和联系人与 Office 365 订阅的 Azure AD 租户同步。 这是 Office 365 的混合标识。 以下是它的组件。

![Office 365 的目录同步组件](./media/about-office-365-identity/hybrid-identity.png)

Azure AD Connect 在本地服务器上运行，并将 AD DS 与 Azure AD 租户同步。 除了目录同步，您还可以指定以下身份验证选项：

- 密码哈希同步（PHS）

  Azure AD 执行身份验证本身。

- 直通身份验证 (PTA)

  Azure AD 具有 AD DS 执行身份验证。

- 联合身份验证

  Azure AD 重定向请求身份验证的客户端计算机，以联系另一个标识提供程序。

有关详细信息，请参阅[混合标识](plan-for-directory-synchronization.md)。
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. 查看 Azure AD Connect 的先决条件

您可以使用 Office 365 订阅获取免费的 Azure AD 订阅。 设置目录同步时，将在其中一台本地服务器上安装 Azure AD Connect。
  
对于 Office 365，你需要执行以下操作：
  
- 验证您的内部部署域。 Azure AD Connect 向导将指导你完成此步骤。
- 获取 Office 365 租户和 AD DS 的管理员帐户的用户名和密码。

对于您在其上安装 Azure AD Connect 的本地服务器，你将需要：
  
|**服务器操作系统**|**其他软件**|
|:-----|:-----|
|Windows Server 2012 R2 及更高版本 | -默认情况下，安装了 PowerShell，无需执行任何操作。  <br> -通过 Windows 更新提供 Net 4.5.1 及更高版本。 确保已在控制面板中将最新的更新安装到 Windows Server。 |
|Windows Server 2008 R2 Service Pack 1 （SP1） * * 或 Windows Server 2012 | -Windows Management Framework 4.0 中提供了最新版本的 PowerShell。 在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)搜索它。  <br> -.Net 4.5.1 及更高版本在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)提供。 |
|Windows Server 2008 | -支持的最新版本的 PowerShell 可在 Windows Management Framework 3.0 中提供，可在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)上找到。  <br> -.Net 4.5.1 及更高版本在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)提供。 |

有关 azure AD Connect 的硬件、软件、帐户和权限要求、SSL 证书要求和对象限制的详细信息，请参阅[Azure Active Directory connect 的先决条件](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites)。
  
您还可以查看 Azure AD Connect[版本的历史记录](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)，以查看每个版本中包含和修复的内容。

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. 安装 Azure AD Connect 和配置目录同步

在开始之前，请确保您具有：

- Office 365 全局管理员的用户名和密码
- AD DS 域管理员的用户名和密码
- 哪种身份验证方法（PHS、PTA、联合）
- 是否要使用[AZURE AD 无缝单一登录（SSO）](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)

请按以下步骤操作：

1. 登录到[Microsoft 365 管理中心](https://admin.microsoft.com)（https://admin.microsoft.com)并选择左侧导航栏中的 "**用户** \> **活动用户**"。
2. 在 "**活动用户**" 页上，选择 "**更多**（三个点） \> **目录同步**"。
  
3. 在 " **Azure Active Directory 准备**" 页上，选择 "**转到下载中心" 以获取 Azure AD Connect 工具**链接开始。 
4. 按照[AZURE Ad connect 和 AZURE Ad Connect Health 安装路线图](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)中的步骤操作。

## <a name="3-finish-setting-up-domains"></a>3. 完成域设置

当您管理 DNS 记录以完成域设置时，请按照[为 Office 365 创建 dns 记录](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider)中的步骤操作。

## <a name="next-step"></a>后续步骤

[向用户帐户分配许可证](assign-licenses-to-user-accounts.md)
