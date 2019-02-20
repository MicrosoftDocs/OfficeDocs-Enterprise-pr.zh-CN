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
ms.openlocfilehash: 5f6e5be2a2137ee183a7d592d9a3e6b086e5be9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085261"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="2eeca-103">设置 Office 365 的目录同步</span><span class="sxs-lookup"><span data-stu-id="2eeca-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="2eeca-p101">Office 365 使用基于云的用户标识管理服务 Azure Active Directory 来管理用户。您还可以通过将本地环境与 Office 365 同步, 将本地 Active Directory 与 Azure AD 集成。设置同步后, 您可以决定在 Azure AD 中或在本地目录中进行用户身份验证。</span><span class="sxs-lookup"><span data-stu-id="2eeca-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="2eeca-107">Office 365 目录同步</span><span class="sxs-lookup"><span data-stu-id="2eeca-107">Office 365 directory synchronization</span></span>

<span data-ttu-id="2eeca-p102">您可以使用本地组织与 Office 365 之间的同步标识或联合身份。使用同步标识, 可以在本地管理用户, 并在 Azure AD 在本地使用云中的相同密码时对它们进行身份验证。这是最常见的目录同步方案。传递身份验证或联合身份允许您在本地管理用户, 并通过本地目录进行身份验证。联合身份需要进行额外的配置, 并允许用户仅登录一次。有关详细信息, 请阅读[了解 Office 365 标识和 Azure Active Directory](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="2eeca-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="2eeca-114">要从 Windows azure active directory 同步 (DirSync) 升级到 Azure active directory Connect？</span><span class="sxs-lookup"><span data-stu-id="2eeca-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>

<span data-ttu-id="2eeca-115">如果你当前正在使用 DirSync 并希望升级, 请转到[azure.com](https://azure.com)以获取[升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。</span><span class="sxs-lookup"><span data-stu-id="2eeca-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="2eeca-116">Azure AD Connect 的先决条件</span><span class="sxs-lookup"><span data-stu-id="2eeca-116">Prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="2eeca-p103">你可以使用 Office 365 订阅获取 Azure AD 的免费订阅。设置目录同步时, 将在其中一台本地服务器上安装 Azure Active directory Connect。</span><span class="sxs-lookup"><span data-stu-id="2eeca-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="2eeca-119">对于 Office 365, 你将需要:</span><span class="sxs-lookup"><span data-stu-id="2eeca-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="2eeca-120">验证您的内部部署域 (此过程将指导您完成此过程)。</span><span class="sxs-lookup"><span data-stu-id="2eeca-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="2eeca-121">在[office 365 中分配管理员角色](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504), 以获取 office 365 租户和本地 Active Directory 的业务权限。</span><span class="sxs-lookup"><span data-stu-id="2eeca-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span>

<span data-ttu-id="2eeca-122">对于您在其上安装 Azure AD Connect 的本地服务器, 你将需要以下软件:</span><span class="sxs-lookup"><span data-stu-id="2eeca-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="2eeca-123">**服务器操作系统**</span><span class="sxs-lookup"><span data-stu-id="2eeca-123">**Server OS**</span></span>|<span data-ttu-id="2eeca-124">**其他软件**</span><span class="sxs-lookup"><span data-stu-id="2eeca-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2eeca-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="2eeca-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="2eeca-126">-默认情况下, 安装了 PowerShell, 无需执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="2eeca-126">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="2eeca-p104">-通过 Windows 更新提供 Net 4.5.1 及更高版本。确保已在控制面板中将最新的更新安装到 Windows Server。</span><span class="sxs-lookup"><span data-stu-id="2eeca-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="2eeca-129">**windows server 2008 R2 Service Pack 1 (SP1)** 或**windows server 2012**</span><span class="sxs-lookup"><span data-stu-id="2eeca-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="2eeca-p105">-Windows Management Framework 4.0 中提供了最新版本的 PowerShell。在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)搜索它。</span><span class="sxs-lookup"><span data-stu-id="2eeca-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br> <span data-ttu-id="2eeca-132">-.net 4.5.1 及更高版本在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)提供。</span><span class="sxs-lookup"><span data-stu-id="2eeca-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="2eeca-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="2eeca-133">**Windows Server 2008**</span></span> | <span data-ttu-id="2eeca-134">-支持的最新版本的 PowerShell 可在 Windows Management Framework 3.0 中提供, 可在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)上找到。</span><span class="sxs-lookup"><span data-stu-id="2eeca-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="2eeca-135">-.net 4.5.1 及更高版本在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)提供。</span><span class="sxs-lookup"><span data-stu-id="2eeca-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

> [!NOTE]
> <span data-ttu-id="2eeca-p106">如果使用的是 Azure active directory DirSync, 可以从本地 Active directory 同步到 Azure active directory 的通讯组成员的最大数量为15000。对于 Azure AD Connect, 该号码为50000。</span><span class="sxs-lookup"><span data-stu-id="2eeca-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="2eeca-138">若要更仔细地查看硬件、软件、帐户和权限要求、SSL 证书要求以及 azure AD connect 的对象限制, 请阅读[azure Active Directory connect 的先决条件](https://go.microsoft.com/fwlink/p/?LinkId=716896)。</span><span class="sxs-lookup"><span data-stu-id="2eeca-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="2eeca-139">您还可以查看 Azure AD Connect[版本的历史记录](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history), 以查看每个版本中包含和修复的内容。</span><span class="sxs-lookup"><span data-stu-id="2eeca-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="2eeca-140">设置目录同步</span><span class="sxs-lookup"><span data-stu-id="2eeca-140">To set up directory synchronization</span></span>

1. <span data-ttu-id="2eeca-141">登录到 Office 365 管理中心, 然后选择左侧导航栏中的 "**用户** \> **活动用户**"。</span><span class="sxs-lookup"><span data-stu-id="2eeca-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="2eeca-142">在 Office 365 管理中心的 "**活动用户**" 页上, 选择 "**更多** \> **目录同步**"。</span><span class="sxs-lookup"><span data-stu-id="2eeca-142">In the Office 365 admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![在 "更多" 菜单中选择 "目录同步"](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="2eeca-p107">在 " **Active directory 准备**" 页上, 选择 "**下载 Microsoft Azure Active Directory Connect 工具**" 链接开始。有关 azure Active Directory Connect 安装过程的详细信息, 请参阅[azure ad connect 和 azure AD connect Health 安装路线图](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)。</span><span class="sxs-lookup"><span data-stu-id="2eeca-p107">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started. For more information about the Azure Active Directory Connect installation process, see [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="assign-licenses-to-synchronized-users"></a><span data-ttu-id="2eeca-146">将许可证分配给同步用户</span><span class="sxs-lookup"><span data-stu-id="2eeca-146">Assign licenses to synchronized users</span></span>

<span data-ttu-id="2eeca-p108">将用户同步到 Office 365 之后, 将会创建这些用户, 但需要向其分配许可证, 以便它们可以使用 Office 365 功能 (如 mail)。有关说明, 请参阅[在 Office 365 for business 中向用户分配许可证](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。</span><span class="sxs-lookup"><span data-stu-id="2eeca-p108">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>

## <a name="finish-setting-up-domains"></a><span data-ttu-id="2eeca-149">完成域设置</span><span class="sxs-lookup"><span data-stu-id="2eeca-149">Finish setting up domains</span></span>

<span data-ttu-id="2eeca-150">当您管理 DNS 记录以完成域设置时, 请按照[为 Office 365 创建 dns 记录](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)中的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="2eeca-150">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>