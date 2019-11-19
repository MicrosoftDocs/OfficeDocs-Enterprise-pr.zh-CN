---
title: 设置 Office 365 目录同步
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
description: 了解如何设置 Office 365 和本地 Active Directory 之间的目录同步。
ms.openlocfilehash: a51abf7dcca0a9edc4ecf233ea67fdeb80070a70
ms.sourcegitcommit: 23c8781d1a2b0472612c3a2cb6e5d13edb03e236
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "38702243"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="2ac0d-103">设置 Office 365 目录同步</span><span class="sxs-lookup"><span data-stu-id="2ac0d-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="2ac0d-104">Office 365 使用 Azure Active Directory （Azure AD）租户存储和管理用于访问基于云的资源的身份验证和权限的标识。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-104">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="2ac0d-105">如果你具有本地 Active Directory 域服务（AD DS），则可以将 AD DS 用户帐户、组和联系人与 Office 365 订阅的 Azure AD 租户同步。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-105">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="2ac0d-106">这是 Office 365 的混合标识。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-106">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="2ac0d-107">以下是它的组件。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-107">Here are its components.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="2ac0d-108">Azure AD Connect 在本地服务器上运行，并将 AD DS 与 Azure AD 租户同步。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-108">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="2ac0d-109">除了目录同步，您还可以指定以下身份验证选项：</span><span class="sxs-lookup"><span data-stu-id="2ac0d-109">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="2ac0d-110">密码哈希同步（PHS）</span><span class="sxs-lookup"><span data-stu-id="2ac0d-110">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="2ac0d-111">Azure AD 执行身份验证本身。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-111">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="2ac0d-112">直通身份验证 (PTA)</span><span class="sxs-lookup"><span data-stu-id="2ac0d-112">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="2ac0d-113">Azure AD 具有 AD DS 执行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-113">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="2ac0d-114">联合身份验证</span><span class="sxs-lookup"><span data-stu-id="2ac0d-114">Federated authentication</span></span>

  <span data-ttu-id="2ac0d-115">Azure AD 重定向请求身份验证的客户端计算机，以联系另一个标识提供程序。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-115">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="2ac0d-116">有关详细信息，请参阅[混合标识](plan-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-116">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="2ac0d-117">1. 查看 Azure AD Connect 的先决条件</span><span class="sxs-lookup"><span data-stu-id="2ac0d-117">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="2ac0d-118">您可以使用 Office 365 订阅获取免费的 Azure AD 订阅。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-118">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="2ac0d-119">设置目录同步时，将在其中一台本地服务器上安装 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-119">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="2ac0d-120">对于 Office 365，你需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2ac0d-120">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="2ac0d-121">验证您的内部部署域。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-121">Verify your on-premises domain.</span></span> <span data-ttu-id="2ac0d-122">Azure AD Connect 向导将指导你完成此步骤。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-122">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="2ac0d-123">获取 Office 365 租户和 AD DS 的管理员帐户的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-123">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="2ac0d-124">对于您在其上安装 Azure AD Connect 的本地服务器，你将需要：</span><span class="sxs-lookup"><span data-stu-id="2ac0d-124">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="2ac0d-125">**服务器操作系统**</span><span class="sxs-lookup"><span data-stu-id="2ac0d-125">**Server OS**</span></span>|<span data-ttu-id="2ac0d-126">**其他软件**</span><span class="sxs-lookup"><span data-stu-id="2ac0d-126">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2ac0d-127">Windows Server 2012 R2 及更高版本</span><span class="sxs-lookup"><span data-stu-id="2ac0d-127">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="2ac0d-128">-默认情况下，安装了 PowerShell，无需执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-128">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="2ac0d-129">-通过 Windows 更新提供 Net 4.5.1 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-129">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="2ac0d-130">确保已在控制面板中将最新的更新安装到 Windows Server。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-130">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="2ac0d-131">Windows Server 2008 R2 Service Pack 1 （SP1） \* \* 或 Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="2ac0d-131">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="2ac0d-132">-Windows Management Framework 4.0 中提供了最新版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-132">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="2ac0d-133">在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)搜索它。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-133">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="2ac0d-134">-.Net 4.5.1 及更高版本在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)提供。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-134">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="2ac0d-135">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="2ac0d-135">Windows Server 2008</span></span> | <span data-ttu-id="2ac0d-136">-支持的最新版本的 PowerShell 可在 Windows Management Framework 3.0 中提供，可在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)上找到。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-136">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="2ac0d-137">-.Net 4.5.1 及更高版本在[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)提供。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-137">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="2ac0d-138">有关 azure AD Connect 的硬件、软件、帐户和权限要求、SSL 证书要求和对象限制的详细信息，请参阅[Azure Active Directory connect 的先决条件](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-138">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="2ac0d-139">您还可以查看 Azure AD Connect[版本的历史记录](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)，以查看每个版本中包含和修复的内容。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="2ac0d-140">2. 安装 Azure AD Connect 和配置目录同步</span><span class="sxs-lookup"><span data-stu-id="2ac0d-140">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="2ac0d-141">在开始之前，请确保您具有：</span><span class="sxs-lookup"><span data-stu-id="2ac0d-141">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="2ac0d-142">Office 365 全局管理员的用户名和密码</span><span class="sxs-lookup"><span data-stu-id="2ac0d-142">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="2ac0d-143">AD DS 域管理员的用户名和密码</span><span class="sxs-lookup"><span data-stu-id="2ac0d-143">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="2ac0d-144">哪种身份验证方法（PHS、PTA、联合）</span><span class="sxs-lookup"><span data-stu-id="2ac0d-144">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="2ac0d-145">是否要使用[AZURE AD 无缝单一登录（SSO）](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span><span class="sxs-lookup"><span data-stu-id="2ac0d-145">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="2ac0d-146">请按以下步骤操作：</span><span class="sxs-lookup"><span data-stu-id="2ac0d-146">Follow these steps:</span></span>

1. <span data-ttu-id="2ac0d-147">登录到[Microsoft 365 管理中心](https://admin.microsoft.com)（https://admin.microsoft.com)并选择左侧导航栏中的 "**用户** \> **活动用户**"。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-147">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="2ac0d-148">在 "**活动用户**" 页上，选择 "**更多**（三个点） \> **目录同步**"。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-148">On the **Active users** page, choose **More** (three dots) \> **Directory synchronization**.</span></span>
  
3. <span data-ttu-id="2ac0d-149">在 " **Azure Active Directory 准备**" 页上，选择 "**转到下载中心" 以获取 Azure AD Connect 工具**链接开始。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-149">On the **Azure Active Directory preparation** page, select the **Go to the Download center to get the Azure AD Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="2ac0d-150">按照[AZURE Ad connect 和 AZURE Ad Connect Health 安装路线图](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)中的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-150">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="2ac0d-151">3. 完成域设置</span><span class="sxs-lookup"><span data-stu-id="2ac0d-151">3. Finish setting up domains</span></span>

<span data-ttu-id="2ac0d-152">当您管理 DNS 记录以完成域设置时，请按照[为 Office 365 创建 dns 记录](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)中的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-152">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="2ac0d-153">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2ac0d-153">Next step</span></span>

<span data-ttu-id="2ac0d-154">[将许可证分配给用户帐户](assign-licenses-to-user-accounts.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac0d-154">[Assign licenses to user accounts](assign-licenses-to-user-accounts.md).</span></span>
