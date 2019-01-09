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
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: 了解如何设置 Office 365 和内部部署 Active Directory 之间的目录同步。
ms.openlocfilehash: 95f138a0a11f14a1036d7d48983f4c88bc965fd0
ms.sourcegitcommit: 0fdb6e470342a98ba164db627fe3dd02cfe8aa0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2019
ms.locfileid: "27768821"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>设置 Office 365 的目录同步
Office 365 使用 Azure Active Directory 的基于云的用户标识管理服务来管理用户。通过将您的内部部署环境与 Office 365 同步，还可以将您的本地 Active Directory 集成与 Azure AD。设置同步后可以决定要进行 Azure AD 中或您的本地目录中其用户身份验证。
  
## <a name="office-365-directory-synchronization"></a>Office 365 目录同步
您可以使用同步的标识或您的内部部署组织与 Office 365 之间的联合的身份。与同步的标识，管理用户内部部署，并进行身份验证由在它们使用相同的密码在云中为内部部署的 Azure AD。这是最常见的目录同步方案。传递身份验证或联盟标识，允许您管理您的用户的内部部署和由您的本地目录经过身份验证。联合的标识需要其他配置，并使用户仅一次登录。有关详细信息，阅读[Understanding Office 365 标识和 Azure Active Directory](about-office-365-identity.md)。
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>要从 Windows Azure Active Directory 同步 (DirSync) 升级到 Azure Active Directory 连接？
如果您正在使用目录同步，并需要进行升级，头转移到[azure.com](https://azure.com)的[升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。
  
## <a name="prerequisites-for-azure-ad-connect"></a>先决条件 Azure AD 连接
获取与您的 Office 365 订阅免费订阅 Azure AD。当您设置目录同步时，您将安装 Azure Active Directory 连接上的一个内部部署服务器。
  
Office 365 您将需要：
  
- 验证您 （该过程将指导您完成这） 的内部部署域。
- 具有[分配管理角色的业务的 Office 365 中](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)的 Office 365 租户的权限和内部部署 Active Directory。 
    
对于您在其安装 Azure AD 连接的内部部署服务器，您将需要以下软件：
  
|**服务器操作系统**|**其他软件**|
|:-----|:-----|
|**Windows Server 2012 R2** | 默认情况下安装 PowerShell，不不需要任何操作。  <br/> -Net 4.5.1 和以后的发行版时通过 Windows Update 提供。请确保您安装到控制面板中的 Windows Server 最新的更新。 |
|**Windows Server 2008 R2 Service Pack 1 (SP1)** 或**Windows Server 2012** | 的 Windows Management Framework 4.0 中可用最新版本的 PowerShell。[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)上的搜索。<br/> -.Net 4.5.1 和更高版本位于[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)。 |
|**Windows Server 2008** | PowerShell-最新支持的版本是 Windows Management Framework 3.0，位于[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)中可用。  <br/> -.Net 4.5.1 和更高版本位于[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)。 |
   
> [!NOTE]
> 如果您正在使用 Azure Active Directory 目录同步，您可以从您的本地 Active Directory 同步到 Azure Active Directory 的通讯组成员的最大数量为 15000。Azure AD 连接，该号码为 50000。 
  
若要更仔细查看 Azure AD 连接硬件、 软件、 帐户和权限要求、 SSL 证书要求和对象限制，请阅读[Azure Active Directory 连接的先决条件](https://go.microsoft.com/fwlink/p/?LinkId=716896)。
  
您还可以查看 Azure AD 连接[版本版本历史记录](https://go.microsoft.com/fwlink/p/?LinkId=733238)是包括，并在每个版本中修复。 

## <a name="to-set-up-directory-synchronization"></a>若要设置目录同步
1. 登录到 Office 365 管理中心，并选择**用户**\>在左侧导航栏上的**活动用户**。 
2. 在 Office 365 管理中心的**活动用户**页上，选择 * * 多 * * \> **目录同步**。
    
    ![在详细菜单中，选择目录同步](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. 在**Active Directory 准备**页上，选择**下载 Microsoft Azure Active Directory 连接工具**的链接开始。关于 Azure Active Directory 连接安装过程的详细信息，请参阅[Azure AD 连接和 Azure AD 连接运行状况安装指南](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)。
    
## <a name="assign-licences-to-synchronized-users"></a>将许可证分配给同步用户
已同步到 Office 365 用户后，则创建它们，但您需要将许可证分配给它们，以便他们可以使用 Office 365 功能，如邮件。有关说明，请参阅[分配对业务的 Office 365 中的用户的许可证](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。
    
## <a name="finish-setting-up-domains"></a>完成设置域
按照在[为 Office 365 管理 DNS 记录时创建 DNS 记录](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)以完成设置您的域中的步骤。