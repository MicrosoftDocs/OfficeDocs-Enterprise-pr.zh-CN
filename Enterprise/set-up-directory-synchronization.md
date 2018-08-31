---
title: 设置 Office 365 的目录同步
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: 了解如何设置 Office 365 和内部部署 Active Directory 之间的目录同步。
ms.openlocfilehash: e406eec08b34a694602c756235533f8b1ff6651e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539565"
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
  
3. 在 * * 是最适合您的目录同步？* * 页上，两个首选的**1-10**和**11 50**结果"根据您的组织的大小，我们建议您创建和管理在云中的用户。使用目录同步将使您的安装程序更复杂。转到活动的用户，以添加您的用户。" 
    
    - 通过选择在页面底部的**此处继续**仍，但是，可以继续设置目录同步。 
    
    - 如果您选择的两个后一种选择， **51 250** **251 或更高版本**，同步安装程序将建议目录同步。选择**下一步**以继续。 
    
    ![选择下一步继续设置目录同步](media/359a1eb9-99ae-4b5b-a413-4de53037cceb.png)
  
4. 在**本地与云目录同步**，读取信息，然后如果您希望的详细信息，选择了解转到的更多链接：[准备通过目录同步到 Office 365 设置用户](prepare-for-directory-synchronization.md)，然后选择**下一步**. 
    
5. 在**让我们检查您的目录**页上，检查自动检查您的目录的要求。如果您满足要求，选择**下一步** \> **开始扫描**。如果您不能满足要求您仍可以继续通过选择**手动继续**。
    
    ![选择下一步或手动在继续让我们检查目录页](media/af4a6bd5-13aa-4bfa-9751-4464a32ca8db.png)
  
6. 如果您选择要扫描您的目录，请在**评估目录同步设置**页上选择**开始扫描**。 
    
    按照说明下载并运行扫描。
    
7. 扫描完成后，返回到安装向导中，并选择**下一步**以查看您的扫描结果。 
    
8. 按照在**验证域所有权**上的说明，请确认您的域。有关详细说明，请参阅[为 Office 365 管理 DNS 记录时创建 DNS 记录](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)。
    
    > [!IMPORTANT]
    > 添加 TXT 记录以验证您拥有您的域后，不会在域向导添加用户的下一步。目录同步将为您添加用户。 
  
    返回到**Office 365 Setup**页上，并选择**刷新**
    
    ![确认您的域后，选择刷新](media/9b5fb593-5ff7-49f0-80d0-18e36d39d669.png)
  
9. 在**您的域准备**页上，选择**下一步**。
    
10. 在**清理环境**页上，（可选） 按照说明下载 IDFix 检查您的 Active Directory。选择**下一步**以继续。 
    
11. 在 * * 运行 Azure Active Directory 连接 * * 页面上，选择**下载**以安装 Azure AD 连接向导。 
    
    > [!NOTE]
    > 此时您将在 Azure AD 连接向导。请确保您离开您是最后一次打开在浏览器中，因此 Azure AD 连接步骤已完成之后，可以返回到该目录同步向导页。 
  
    Azure AD 连接向导程序安装后将自动打开。也可以在从您的桌面，默认安装网站打开它。按照向导说明具体取决于您的方案：
    
  - 对于与密码哈希同步的目录同步，使用[使用 express 设置 Azure AD 连接](https://go.microsoft.com/fwlink/p/?LinkID=698537)。
    
  - 对于多个林，传递身份验证、 联合的身份和 SSO 选项，使用[自定义安装的 Azure AD 连接](https://go.microsoft.com/fwlink/p/?LinkId=698430)。
    
    选择要使用这些选项的**Express 设置**页上的**自定义**。 
    
12. Azure AD 连接向导完成后，返回到**Office 365 安装**向导中，并按照**使确保同步担任预期页**上的说明。选择**下一步**以继续。 
    
13. 在阅读说明 * * 激活用户 * * 页面，然后选择**下一步**。
    
14. 在**您所有的安装程序**页上选择**完成**。 
    
## <a name="assign-licences-to-synchronized-users"></a>将许可证分配给同步用户
已同步到 Office 365 用户后，则创建它们，但您需要将许可证分配给它们，以便他们可以使用 Office 365 功能，如邮件。有关说明，请参阅[分配对业务的 Office 365 中的用户的许可证](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。
    
## <a name="finish-setting-up-domains"></a>完成设置域
按照在[为 Office 365 管理 DNS 记录时创建 DNS 记录](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)以完成设置您的域中的步骤。