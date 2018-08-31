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
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="611e5-103">设置 Office 365 的目录同步</span><span class="sxs-lookup"><span data-stu-id="611e5-103">Set up directory synchronization for Office 365</span></span>
<span data-ttu-id="611e5-p101">Office 365 使用 Azure Active Directory 的基于云的用户标识管理服务来管理用户。通过将您的内部部署环境与 Office 365 同步，还可以将您的本地 Active Directory 集成与 Azure AD。设置同步后可以决定要进行 Azure AD 中或您的本地目录中其用户身份验证。</span><span class="sxs-lookup"><span data-stu-id="611e5-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="611e5-107">Office 365 目录同步</span><span class="sxs-lookup"><span data-stu-id="611e5-107">Office 365 directory synchronization</span></span>
<span data-ttu-id="611e5-p102">您可以使用同步的标识或您的内部部署组织与 Office 365 之间的联合的身份。与同步的标识，管理用户内部部署，并进行身份验证由在它们使用相同的密码在云中为内部部署的 Azure AD。这是最常见的目录同步方案。传递身份验证或联盟标识，允许您管理您的用户的内部部署和由您的本地目录经过身份验证。联合的标识需要其他配置，并使用户仅一次登录。有关详细信息，阅读[Understanding Office 365 标识和 Azure Active Directory](about-office-365-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="611e5-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="611e5-114">要从 Windows Azure Active Directory 同步 (DirSync) 升级到 Azure Active Directory 连接？</span><span class="sxs-lookup"><span data-stu-id="611e5-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>
<span data-ttu-id="611e5-115">如果您正在使用目录同步，并需要进行升级，头转移到[azure.com](https://azure.com)的[升级说明](https://go.microsoft.com/fwlink/p/?LinkId=733240)。</span><span class="sxs-lookup"><span data-stu-id="611e5-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="611e5-116">先决条件 Azure AD 连接</span><span class="sxs-lookup"><span data-stu-id="611e5-116">Prerequisites for Azure AD Connect</span></span>
<span data-ttu-id="611e5-p103">获取与您的 Office 365 订阅免费订阅 Azure AD。当您设置目录同步时，您将安装 Azure Active Directory 连接上的一个内部部署服务器。</span><span class="sxs-lookup"><span data-stu-id="611e5-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="611e5-119">Office 365 您将需要：</span><span class="sxs-lookup"><span data-stu-id="611e5-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="611e5-120">验证您 （该过程将指导您完成这） 的内部部署域。</span><span class="sxs-lookup"><span data-stu-id="611e5-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="611e5-121">具有[分配管理角色的业务的 Office 365 中](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)的 Office 365 租户的权限和内部部署 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="611e5-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span> 
    
<span data-ttu-id="611e5-122">对于您在其安装 Azure AD 连接的内部部署服务器，您将需要以下软件：</span><span class="sxs-lookup"><span data-stu-id="611e5-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="611e5-123">**服务器操作系统**</span><span class="sxs-lookup"><span data-stu-id="611e5-123">**Server OS**</span></span>|<span data-ttu-id="611e5-124">**其他软件**</span><span class="sxs-lookup"><span data-stu-id="611e5-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="611e5-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="611e5-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="611e5-126">默认情况下安装 PowerShell，不不需要任何操作。</span><span class="sxs-lookup"><span data-stu-id="611e5-126">- PowerShell is installed by default, no action is required.</span></span>  <br/> <span data-ttu-id="611e5-p104">-Net 4.5.1 和以后的发行版时通过 Windows Update 提供。请确保您安装到控制面板中的 Windows Server 最新的更新。</span><span class="sxs-lookup"><span data-stu-id="611e5-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="611e5-129">**Windows Server 2008 R2 Service Pack 1 (SP1)** 或**Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="611e5-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="611e5-p105">的 Windows Management Framework 4.0 中可用最新版本的 PowerShell。[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)上的搜索。</span><span class="sxs-lookup"><span data-stu-id="611e5-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br/> <span data-ttu-id="611e5-132">-.Net 4.5.1 和更高版本位于[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)。</span><span class="sxs-lookup"><span data-stu-id="611e5-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="611e5-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="611e5-133">**Windows Server 2008**</span></span> | <span data-ttu-id="611e5-134">PowerShell-最新支持的版本是 Windows Management Framework 3.0，位于[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)中可用。</span><span class="sxs-lookup"><span data-stu-id="611e5-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br/> <span data-ttu-id="611e5-135">-.Net 4.5.1 和更高版本位于[Microsoft 下载中心](https://go.microsoft.com/fwlink/p/?LinkId=717996)。</span><span class="sxs-lookup"><span data-stu-id="611e5-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
   
> [!NOTE]
> <span data-ttu-id="611e5-p106">如果您正在使用 Azure Active Directory 目录同步，您可以从您的本地 Active Directory 同步到 Azure Active Directory 的通讯组成员的最大数量为 15000。Azure AD 连接，该号码为 50000。</span><span class="sxs-lookup"><span data-stu-id="611e5-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="611e5-138">若要更仔细查看 Azure AD 连接硬件、 软件、 帐户和权限要求、 SSL 证书要求和对象限制，请阅读[Azure Active Directory 连接的先决条件](https://go.microsoft.com/fwlink/p/?LinkId=716896)。</span><span class="sxs-lookup"><span data-stu-id="611e5-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="611e5-139">您还可以查看 Azure AD 连接[版本版本历史记录](https://go.microsoft.com/fwlink/p/?LinkId=733238)是包括，并在每个版本中修复。</span><span class="sxs-lookup"><span data-stu-id="611e5-139">You can also review the Azure AD Connect [version release history](https://go.microsoft.com/fwlink/p/?LinkId=733238) to see what is included and fixed in each release.</span></span> 

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="611e5-140">若要设置目录同步</span><span class="sxs-lookup"><span data-stu-id="611e5-140">To set up directory synchronization</span></span>
1. <span data-ttu-id="611e5-141">登录到 Office 365 管理中心，并选择**用户**\>在左侧导航栏上的**活动用户**。</span><span class="sxs-lookup"><span data-stu-id="611e5-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span> 
2. <span data-ttu-id="611e5-142">在 Office 365 管理中心的**活动用户**页上，选择 * * 多 * * \> **目录同步**。</span><span class="sxs-lookup"><span data-stu-id="611e5-142">In the Office 365 admin center, on the **Active users** page, choose ** More ** \> **Directory synchronization**.</span></span>
    
    ![在详细菜单中，选择目录同步](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="611e5-p107">在 * * 是最适合您的目录同步？* * 页上，两个首选的**1-10**和**11 50**结果"根据您的组织的大小，我们建议您创建和管理在云中的用户。使用目录同步将使您的安装程序更复杂。转到活动的用户，以添加您的用户。"</span><span class="sxs-lookup"><span data-stu-id="611e5-p107">On the ** Is directory sync right for you? ** page, the two first choices of **1-10**, and **11-50** result in "Based on the size of your organization, we recommend that you create and manage users in the cloud. Using directory synchronization will make your setup more complex. Go to Active users to add your users."</span></span> 
    
    - <span data-ttu-id="611e5-148">通过选择在页面底部的**此处继续**仍，但是，可以继续设置目录同步。</span><span class="sxs-lookup"><span data-stu-id="611e5-148">You can still, however, continue setting up directory synchronization by choosing **Continue here** on the bottom of the page.</span></span> 
    
    - <span data-ttu-id="611e5-p108">如果您选择的两个后一种选择， **51 250** **251 或更高版本**，同步安装程序将建议目录同步。选择**下一步**以继续。</span><span class="sxs-lookup"><span data-stu-id="611e5-p108">If you select the two latter choices, **51-250** or **251 or greater**, the synchronization setup will recommend directory synchronization. Choose **Next** to continue.</span></span> 
    
    ![选择下一步继续设置目录同步](media/359a1eb9-99ae-4b5b-a413-4de53037cceb.png)
  
4. <span data-ttu-id="611e5-152">在**本地与云目录同步**，读取信息，然后如果您希望的详细信息，选择了解转到的更多链接：[准备通过目录同步到 Office 365 设置用户](prepare-for-directory-synchronization.md)，然后选择**下一步**.</span><span class="sxs-lookup"><span data-stu-id="611e5-152">On the **Sync your local directory with the cloud**, read the information, and if you want more information, choose the learn more link that goes to: [Prepare to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md), and then choose **Next**.</span></span> 
    
5. <span data-ttu-id="611e5-p109">在**让我们检查您的目录**页上，检查自动检查您的目录的要求。如果您满足要求，选择**下一步** \> **开始扫描**。如果您不能满足要求您仍可以继续通过选择**手动继续**。</span><span class="sxs-lookup"><span data-stu-id="611e5-p109">On the **Let's check your directory** page, review the requirements for automatically checking your directory. If you meet the requirements, choose **Next** \> **Start scan**. If you can't meet the requirements you can still continue by choosing **continue manually**.</span></span>
    
    ![选择下一步或手动在继续让我们检查目录页](media/af4a6bd5-13aa-4bfa-9751-4464a32ca8db.png)
  
6. <span data-ttu-id="611e5-157">如果您选择要扫描您的目录，请在**评估目录同步设置**页上选择**开始扫描**。</span><span class="sxs-lookup"><span data-stu-id="611e5-157">If you select to scan your directories, choose **Start scan** on the **Evaluating directory synchronization setup** page.</span></span> 
    
    <span data-ttu-id="611e5-158">按照说明下载并运行扫描。</span><span class="sxs-lookup"><span data-stu-id="611e5-158">Follow the instructions to download and run the scan.</span></span>
    
7. <span data-ttu-id="611e5-159">扫描完成后，返回到安装向导中，并选择**下一步**以查看您的扫描结果。</span><span class="sxs-lookup"><span data-stu-id="611e5-159">Once the scan is complete, return to the setup wizard, and choose **Next** to see your scan results.</span></span> 
    
8. <span data-ttu-id="611e5-p110">按照在**验证域所有权**上的说明，请确认您的域。有关详细说明，请参阅[为 Office 365 管理 DNS 记录时创建 DNS 记录](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)。</span><span class="sxs-lookup"><span data-stu-id="611e5-p110">Verify your domains as instructed on the **Verify Ownership of your domains** page. For detailed instructions, see [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23).</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="611e5-p111">添加 TXT 记录以验证您拥有您的域后，不会在域向导添加用户的下一步。目录同步将为您添加用户。</span><span class="sxs-lookup"><span data-stu-id="611e5-p111">After you have added a TXT record to verify you own your domain, do not go to the next step of adding users in the domains wizard. The directory synchronization will add users for you.</span></span> 
  
    <span data-ttu-id="611e5-164">返回到**Office 365 Setup**页上，并选择**刷新**</span><span class="sxs-lookup"><span data-stu-id="611e5-164">Return to the **Office 365 Setup** page and choose **Refresh**</span></span>
    
    ![确认您的域后，选择刷新](media/9b5fb593-5ff7-49f0-80d0-18e36d39d669.png)
  
9. <span data-ttu-id="611e5-166">在**您的域准备**页上，选择**下一步**。</span><span class="sxs-lookup"><span data-stu-id="611e5-166">On the **Your domains are ready** page, choose **Next**.</span></span>
    
10. <span data-ttu-id="611e5-p112">在**清理环境**页上，（可选） 按照说明下载 IDFix 检查您的 Active Directory。选择**下一步**以继续。</span><span class="sxs-lookup"><span data-stu-id="611e5-p112">On the **Clean up your environment** page, optionally follow the instructions to download IDFix to check your Active Directory. Choose **Next** to continue.</span></span> 
    
11. <span data-ttu-id="611e5-169">在 * * 运行 Azure Active Directory 连接 * * 页面上，选择**下载**以安装 Azure AD 连接向导。</span><span class="sxs-lookup"><span data-stu-id="611e5-169">On the ** Run Azure Active Directory Connect ** page, choose **Download** to install Azure AD Connect wizard.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="611e5-p113">此时您将在 Azure AD 连接向导。请确保您离开您是最后一次打开在浏览器中，因此 Azure AD 连接步骤已完成之后，可以返回到该目录同步向导页。</span><span class="sxs-lookup"><span data-stu-id="611e5-p113">At this point you will be in the Azure AD Connect wizard. Make sure you leave the directory synchronization wizard page you were last on open in your browser, so you can return to it after the Azure AD Connect steps are done.</span></span> 
  
    <span data-ttu-id="611e5-p114">Azure AD 连接向导程序安装后将自动打开。也可以在从您的桌面，默认安装网站打开它。按照向导说明具体取决于您的方案：</span><span class="sxs-lookup"><span data-stu-id="611e5-p114">After Azure AD Connect wizard has installed it will automatically open. You can also open it from your desktop, the default install site. Follow the wizard instructions depending on your scenario:</span></span>
    
  - <span data-ttu-id="611e5-175">对于与密码哈希同步的目录同步，使用[使用 express 设置 Azure AD 连接](https://go.microsoft.com/fwlink/p/?LinkID=698537)。</span><span class="sxs-lookup"><span data-stu-id="611e5-175">For directory synchronization with password hash synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>
    
  - <span data-ttu-id="611e5-176">对于多个林，传递身份验证、 联合的身份和 SSO 选项，使用[自定义安装的 Azure AD 连接](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="611e5-176">For multiple forests, pass-through authentication, federated identity and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
    
    <span data-ttu-id="611e5-177">选择要使用这些选项的**Express 设置**页上的**自定义**。</span><span class="sxs-lookup"><span data-stu-id="611e5-177">Select **Customize** on the **Express Settings** page to use these options.</span></span> 
    
12. <span data-ttu-id="611e5-p115">Azure AD 连接向导完成后，返回到**Office 365 安装**向导中，并按照**使确保同步担任预期页**上的说明。选择**下一步**以继续。</span><span class="sxs-lookup"><span data-stu-id="611e5-p115">After the Azure AD Connect wizard is done, return to the **Office 365 Setup** wizard, and follow the instructions on the **Make sure sync worked as expected page**. Choose **Next** to continue.</span></span> 
    
13. <span data-ttu-id="611e5-180">在阅读说明 * * 激活用户 * * 页面，然后选择**下一步**。</span><span class="sxs-lookup"><span data-stu-id="611e5-180">Read the instructions on the ** Activate users ** page and then choose **Next**.</span></span>
    
14. <span data-ttu-id="611e5-181">在**您所有的安装程序**页上选择**完成**。</span><span class="sxs-lookup"><span data-stu-id="611e5-181">Choose **Finish** on the **You're all setup** page.</span></span> 
    
## <a name="assign-licences-to-synchronized-users"></a><span data-ttu-id="611e5-182">将许可证分配给同步用户</span><span class="sxs-lookup"><span data-stu-id="611e5-182">Assign licences to synchronized users</span></span>
<span data-ttu-id="611e5-p116">已同步到 Office 365 用户后，则创建它们，但您需要将许可证分配给它们，以便他们可以使用 Office 365 功能，如邮件。有关说明，请参阅[分配对业务的 Office 365 中的用户的许可证](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)。</span><span class="sxs-lookup"><span data-stu-id="611e5-p116">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
    
## <a name="finish-setting-up-domains"></a><span data-ttu-id="611e5-185">完成设置域</span><span class="sxs-lookup"><span data-stu-id="611e5-185">Finish setting up domains</span></span>
<span data-ttu-id="611e5-186">按照在[为 Office 365 管理 DNS 记录时创建 DNS 记录](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)以完成设置您的域中的步骤。</span><span class="sxs-lookup"><span data-stu-id="611e5-186">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>