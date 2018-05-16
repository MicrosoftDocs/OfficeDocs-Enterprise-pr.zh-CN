---
title: Exchange Online 中的多地理位置功能
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Exchange Online 中的多地理位置功能的多个地理区域中展开 Office 365 状态。
ms.openlocfilehash: ea00ab52142e92e122273ab4ba718e98bd94b572
ms.sourcegitcommit: 12d3223cc2d6bf39a8960409a923254e1790fd2f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="eae1c-103">Exchange Online 中的多地理位置功能</span><span class="sxs-lookup"><span data-stu-id="eae1c-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="eae1c-p101">Office 365 中的多地理位置功能启用单个租户跨多个地理位置 (Geo)。启用多地理位置后，客户可以选择基于每个用户的 Exchange Online 邮箱内容 （静态数据） 的位置。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations (Geos). When Multi-Geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="eae1c-p102">基于您的付费地址确定初始租户您的位置 （称为您"default"或"管理中心"位置）。启用多地理位置后，可以将邮箱置于由的其他"附属"位置：</span><span class="sxs-lookup"><span data-stu-id="eae1c-p102">Your initial tenant location (referred to as your "default" or "central" location) is determined based on your billing address. When Multi-Geo is enabled, you can place mailboxes in additional "satellite" locations by:</span></span>

- <span data-ttu-id="eae1c-108">直接在附属中创建新的 Exchange Online 邮箱。</span><span class="sxs-lookup"><span data-stu-id="eae1c-108">Creating a new Exchange Online mailbox directly in a satellite.</span></span>

- <span data-ttu-id="eae1c-109">将现有的 Exchange Online 邮箱移到附属。</span><span class="sxs-lookup"><span data-stu-id="eae1c-109">Moving an existing Exchange Online mailbox into a satellite.</span></span>

- <span data-ttu-id="eae1c-110">加入从直接附属内部部署 Exchange 组织的邮箱。</span><span class="sxs-lookup"><span data-stu-id="eae1c-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite.</span></span>

<span data-ttu-id="eae1c-111">以下 Geo 供多地理位置配置中的使用：</span><span class="sxs-lookup"><span data-stu-id="eae1c-111">The following Geos are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="eae1c-112">亚太地区</span><span class="sxs-lookup"><span data-stu-id="eae1c-112">Asia Pacific</span></span>

- <span data-ttu-id="eae1c-113">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="eae1c-113">Australia</span></span>

- <span data-ttu-id="eae1c-114">加拿大</span><span class="sxs-lookup"><span data-stu-id="eae1c-114">Canada</span></span>

- <span data-ttu-id="eae1c-115">欧盟</span><span class="sxs-lookup"><span data-stu-id="eae1c-115">European Union</span></span>

- <span data-ttu-id="eae1c-116">印度 (当前仅适用于使用在印度帐单地址客户)</span><span class="sxs-lookup"><span data-stu-id="eae1c-116">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="eae1c-117">日本</span><span class="sxs-lookup"><span data-stu-id="eae1c-117">Japan</span></span>

- <span data-ttu-id="eae1c-118">韩国</span><span class="sxs-lookup"><span data-stu-id="eae1c-118">Korea</span></span>

- <span data-ttu-id="eae1c-119">英国</span><span class="sxs-lookup"><span data-stu-id="eae1c-119">United Kingdom</span></span>

- <span data-ttu-id="eae1c-120">美国</span><span class="sxs-lookup"><span data-stu-id="eae1c-120">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="eae1c-121">必备组件配置</span><span class="sxs-lookup"><span data-stu-id="eae1c-121">Prerequisite configuration</span></span>
<span data-ttu-id="eae1c-p103">然后才能开始联机 Exchange 中使用多地理位置功能 Microsoft 需要配置您的 Exchange Online 租户多地理支持。订购多地理许可证和通常应小于 30 天才能完成时，将触发此一次性配置过程。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for Multi-Geo support. This one-time configuration process is triggered when you order Multi-Geo licenses and should typically take less than 30 days to complete.</span></span>

<span data-ttu-id="eae1c-p104">当您配置已启动并完成，您将在[Office 365 邮件中心](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093)收到通知。配置自动触发时购买多地理许可证。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has started and completed. Configuration is automatically triggered when you buy Multi-Geo licenses.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="eae1c-126">邮箱位置和移动</span><span class="sxs-lookup"><span data-stu-id="eae1c-126">Mailbox placement and moves</span></span>
<span data-ttu-id="eae1c-127">Microsoft 完成的必备组件的多地理配置步骤之后，Exchange Online 也会授予对用户对象的**PreferredDataLocation**属性在 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="eae1c-127">After Microsoft completes the prerequisite Multi-Geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="eae1c-p105">Exchange Online 同步到 Exchange Online 的目录服务中的**MailboxRegion**属性 Azure AD 的**PreferredDataLocation**属性。**MailboxRegion**的值确定的 Geo 放置用户邮箱和任何关联的存档邮箱。无法配置用户的主邮箱和存档邮箱驻留在不同 Geo。只有一个地理位置可以配置每个用户对象。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It isn't possible to configure a user's primary mailbox and archive mailboxes to reside in different Geos. Only one Geo may be configured per user object.</span></span>

- <span data-ttu-id="eae1c-132">当上具有现有的邮箱的用户配置**PreferredDataLocation** ，则邮箱将自动移动到指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="eae1c-132">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be automatically moved to the specified Geo.</span></span> 

- <span data-ttu-id="eae1c-133">时上没有现有邮箱的用户配置**PreferredDataLocation** ，则将设置邮箱到指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="eae1c-133">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified Geo.</span></span> 

- <span data-ttu-id="eae1c-134">如果未不指定任何地理位置，则邮箱都位于默认地理位置。</span><span class="sxs-lookup"><span data-stu-id="eae1c-134">If no Geo is specified, the mailbox will be placed in the default Geo.</span></span>

<span data-ttu-id="eae1c-p106">**注意**： 多地理位置功能和两个业务联机地区组织承载会议的 Skype **PreferredDataLocation**属性用于在用户对象上查找服务。如果您的地区组织托管的会议的用户对象上配置**PreferredDataLocation**值，这些用户的邮箱将自动移动到指定的地理位置后的 Office 365 租户启用多地理位置。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p106">**Note**: Multi-Geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified Geo after Multi-Geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="eae1c-137">Exchange Online 中的多地理位置功能限制</span><span class="sxs-lookup"><span data-stu-id="eae1c-137">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="eae1c-p107">用户邮箱、 资源邮箱 （房间和设备邮箱） 和共享的邮箱支持多地理位置功能。仅可以将公用文件夹邮箱和 Office 365 组放入客户的主地理位置。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support Multi-Geo features. You can only place public folder mailboxes and Office 365 Groups in the customer's home Geo.</span></span>
 
2. <span data-ttu-id="eae1c-p108">安全性和遵从性 （例如，审核和电子数据展示） 可用功能的 Exchange 管理员中心 (EAC) 中不可用多地理位置组织中。相反，您需要使用[Office 365 安全性和合规性中心](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)来配置安全性和遵从性功能。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in Multi-Geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="eae1c-p109">他们的邮箱移动到新的地理位置时，outlook for Mac 用户可能会遇到临时断开其联机存档文件夹的访问权限。发生这种情况时用户的主和存档邮箱都在不同 Geo，因为跨地理邮箱移动可能完成时间不同。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new Geo. This condition occurs when the user's the primary and archive mailboxes are in different Geos, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="eae1c-p110">用户无法在 web （以前称为，Outlook Web App 或 OWA） 上的 Outlook 中的 Geo 之间共享*邮箱文件夹*。例如，在欧盟用户不能使用 web 上的 Outlook 打开位于美国的邮箱中的共享的文件夹。但是，在 web 用户的 Outlook 可以*其他邮箱*中打开不同 Geo 使用单独的浏览器窗口[打开 Outlook Web App 中的一个单独的浏览器窗口中的其他人的邮箱](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)中所述。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p110">Users can't share *mailbox folders* across Geos in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="eae1c-147">**注意**： 在 Outlook 中为 Windows 上支持跨地理邮箱文件夹共享。</span><span class="sxs-lookup"><span data-stu-id="eae1c-147">**Note**: Cross-Geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

5. <span data-ttu-id="eae1c-p111">目前，跨地理日历委派不支持在 web 上的 Outlook 中。Windows 上的 Outlook 支持跨地理日历委派。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p111">Currently, cross-Geo calendar delegation isn't supported in Outlook on the web. Cross-Geo calendar delegation is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="eae1c-150">管理</span><span class="sxs-lookup"><span data-stu-id="eae1c-150">Administration</span></span> 
<span data-ttu-id="eae1c-p112">远程 PowerShell 需要查看和 Office 365 环境中配置与地理位置相关的属性。有关各种用来管理 Office 365，请参阅[管理 Office 365 和 Exchange Online 使用 Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)的 PowerShell 模块的信息。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p112">Remote PowerShell is required to view and configure Geo-related properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="eae1c-p113">您需要[Microsoft Azure Active Directory PowerShell 模块](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx)v1.1.166.0 或更高版本中 1.x 版在用户对象上看到**PreferredDataLocation**属性。要连接到 Azure AD PowerShell，请参阅[Connect to Office 365 PowerShell 中](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p113">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="eae1c-155">要连接到 Exchange Online PowerShell 中，请参阅[Connect to Exchange Online PowerShell 中](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。</span><span class="sxs-lookup"><span data-stu-id="eae1c-155">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="eae1c-156">直接连接到 Exchange Online PowerShell 中使用的特定地理位置</span><span class="sxs-lookup"><span data-stu-id="eae1c-156">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="eae1c-p114">通常情况下，Exchange Online PowerShell 中将连接到默认地理位置。但是，您还可以直接向非默认 Geo 连接。由于性能改进，我们建议直接连接到非默认地理位置时仅管理中的地理位置的用户。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p114">Typically, Exchange Online PowerShell will connect to the default Geo. But, you can also connect directly to non-default Geos. Because of performance improvements, we recommend connecting directly to the non-default Geo when you only manage users in that Geo.</span></span>

<span data-ttu-id="eae1c-p115">要连接到特定的地理位置，则正则连接说明以外的其他*ConnectionUri*参数。其余的命令和值都相同。步骤如下：</span><span class="sxs-lookup"><span data-stu-id="eae1c-p115">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="eae1c-163">在本地计算机上打开 Windows PowerShell 并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="eae1c-163">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="eae1c-164">**Windows PowerShell 凭据请求**对话框中，键入您的工作或学校帐户和密码，，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="eae1c-164">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="eae1c-p116">替换`<emailaddress>`替换**任何**目标地理位置中的邮箱并运行以下命令的电子邮件地址。不因素; 您对邮箱和向您在步骤 1 中的凭据的关系的权限。电子邮件地址仅仅告诉 Exchange Online 连接的位置。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p116">Replace `<emailaddress>` with the email address of **any** mailbox in the target Geo and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="eae1c-167">例如，如果 olga@contoso.onmicrosoft.com 是您想要连接的地理位置中的有效邮箱的电子邮件地址，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="eae1c-167">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="eae1c-168">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="eae1c-168">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="eae1c-169">Azure AD 连接版本要求</span><span class="sxs-lookup"><span data-stu-id="eae1c-169">Azure AD Connect version requirements</span></span>
<span data-ttu-id="eae1c-p117">AAD 连接版本 1.1.524.0 或更高版本用于从内部部署 Active Directory 用户对象同步的设置的**PreferredDataLocation**属性是唯一受支持的方法。有关详细说明，请参阅[Azure Active Directory 连接同步： 配置 Office 365 资源的首选的数据位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p117">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="eae1c-172">地理位置代码</span><span class="sxs-lookup"><span data-stu-id="eae1c-172">Geo Codes</span></span>
<span data-ttu-id="eae1c-p118">三个字母代码用于**PreferredDataLocation**属性中指定的地理位置。下表列出了可用 Geo 的代码：</span><span class="sxs-lookup"><span data-stu-id="eae1c-p118">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="eae1c-175">地域</span><span class="sxs-lookup"><span data-stu-id="eae1c-175">Geo</span></span> |<span data-ttu-id="eae1c-176">代码</span><span class="sxs-lookup"><span data-stu-id="eae1c-176">Code</span></span> |
|---------|---------|
|<span data-ttu-id="eae1c-177">亚太地区</span><span class="sxs-lookup"><span data-stu-id="eae1c-177">Asia/Pacific</span></span> |<span data-ttu-id="eae1c-178">APC</span><span class="sxs-lookup"><span data-stu-id="eae1c-178">APC</span></span> |
|<span data-ttu-id="eae1c-179">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="eae1c-179">Australia</span></span> |<span data-ttu-id="eae1c-180">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="eae1c-180">AUS</span></span> |
|<span data-ttu-id="eae1c-181">加拿大</span><span class="sxs-lookup"><span data-stu-id="eae1c-181">Canada</span></span> |<span data-ttu-id="eae1c-182">可以</span><span class="sxs-lookup"><span data-stu-id="eae1c-182">CAN</span></span> |
|<span data-ttu-id="eae1c-183">欧盟</span><span class="sxs-lookup"><span data-stu-id="eae1c-183">European Union</span></span> |<span data-ttu-id="eae1c-184">EUR</span><span class="sxs-lookup"><span data-stu-id="eae1c-184">EUR</span></span> |
|<span data-ttu-id="eae1c-185">印度</span><span class="sxs-lookup"><span data-stu-id="eae1c-185">India</span></span> |<span data-ttu-id="eae1c-186">IND</span><span class="sxs-lookup"><span data-stu-id="eae1c-186">IND</span></span> |
|<span data-ttu-id="eae1c-187">日本</span><span class="sxs-lookup"><span data-stu-id="eae1c-187">Japan</span></span> |<span data-ttu-id="eae1c-188">日文</span><span class="sxs-lookup"><span data-stu-id="eae1c-188">JPN</span></span> |
|<span data-ttu-id="eae1c-189">韩国</span><span class="sxs-lookup"><span data-stu-id="eae1c-189">Korea</span></span> |<span data-ttu-id="eae1c-190">韩文</span><span class="sxs-lookup"><span data-stu-id="eae1c-190">KOR</span></span> |
|<span data-ttu-id="eae1c-191">英国</span><span class="sxs-lookup"><span data-stu-id="eae1c-191">United Kingdom</span></span> |<span data-ttu-id="eae1c-192">GBR</span><span class="sxs-lookup"><span data-stu-id="eae1c-192">GBR</span></span> |
|<span data-ttu-id="eae1c-193">美国</span><span class="sxs-lookup"><span data-stu-id="eae1c-193">United States</span></span> |<span data-ttu-id="eae1c-194">越南</span><span class="sxs-lookup"><span data-stu-id="eae1c-194">NAM</span></span> |

<span data-ttu-id="eae1c-p119">**注意**： 的**PreferredDataLocation**和**MailboxRegion**属性是与没有错误检查的字符串。如果输入值无效 (例如，NAN) 邮箱都位于默认地理位置。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p119">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="eae1c-197">查看可用 Geo 在 Exchange Online 组织中配置</span><span class="sxs-lookup"><span data-stu-id="eae1c-197">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="eae1c-198">若要配置 Geo Exchange Online 组织中的列表，请参阅，运行以下命令在 Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="eae1c-198">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

<span data-ttu-id="eae1c-199">命令输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="eae1c-199">The output of the command looks like this:</span></span>

```
Region
------
APC
AUS
CAN
EUR
GBR
JPN
KOR
NAM
```

### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="eae1c-200">查找邮箱的地理位置</span><span class="sxs-lookup"><span data-stu-id="eae1c-200">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="eae1c-201">Exchange Online PowerShell 中的**Get-mailbox** cmdlet 显示邮箱上的地理位置相关的以下属性：</span><span class="sxs-lookup"><span data-stu-id="eae1c-201">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following Geo-related properties on mailboxes:</span></span>

- <span data-ttu-id="eae1c-202">**数据库**： 数据库名称的前 3 个字母对应告诉您邮箱所在的位置当前的地理位置代码。</span><span class="sxs-lookup"><span data-stu-id="eae1c-202">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located.</span></span>

- <span data-ttu-id="eae1c-203">**MailboxRegion**： 指定由管理员 （Azure AD 中从**PreferredDataLocation**同步） 所设置的地理位置代码。</span><span class="sxs-lookup"><span data-stu-id="eae1c-203">**MailboxRegion**: Specifies the Geo code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="eae1c-204">**MailboxRegionLastUpdateTime**： 指示当 MailboxRegion 上次更新 （自动或手动）。</span><span class="sxs-lookup"><span data-stu-id="eae1c-204">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="eae1c-205">若要查看邮箱的这些属性，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="eae1c-205">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="eae1c-206">例如，若要查看邮箱 chris@contoso.onmicrosoft.com 的地理信息，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="eae1c-206">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="eae1c-207">命令输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="eae1c-207">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> [!NOTE]
> <span data-ttu-id="eae1c-208">如果在数据库名称的地理位置代码与**MailboxRegion**值不匹配，邮箱将自动移动到由**MailboxRegion**值 （这些属性值不匹配的 Exchange Online 看起来） 指定地理位置。</span><span class="sxs-lookup"><span data-stu-id="eae1c-208">If the Geo code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically moved to the Geo specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a><span data-ttu-id="eae1c-209">将现有云邮箱移动到特定的地理位置</span><span class="sxs-lookup"><span data-stu-id="eae1c-209">Move an existing cloud mailbox to a specific Geo</span></span>
<span data-ttu-id="eae1c-210">使用 Windows PowerShell 的 Azure AD 模块中**Get-msoluser**和**Set-msoluser** cmdlet 查看或指定用于存储用户邮箱的地理位置。</span><span class="sxs-lookup"><span data-stu-id="eae1c-210">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a user's mailbox will be stored.</span></span>

<span data-ttu-id="eae1c-211">若要查看用户的**PreferredDataLocation**值，请在 Azure AD PowerShell 中使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="eae1c-211">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="eae1c-212">例如，若要查看用户 michelle@contoso.onmicrosoft.com **PreferredDataLocation**值，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="eae1c-212">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="eae1c-213">命令输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="eae1c-213">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="eae1c-214">若要修改的仅云用户对象的**PreferredDataLocation**值，请在 Azure AD PowerShell 中使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="eae1c-214">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="eae1c-215">例如，若要将**PreferredDataLocation**值设置为欧盟 (EUR) 的用户 michelle@contoso.onmicrosoft.com，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="eae1c-215">For example, to set the **PreferredDataLocation** value to the European Union (EUR) for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="eae1c-216">**说明**：</span><span class="sxs-lookup"><span data-stu-id="eae1c-216">**Notes**:</span></span>

- <span data-ttu-id="eae1c-p120">如前所述用于从内部部署 Active Directory 同步的用户对象，不能使用此过程。您需要更改**PreferredDataLocation**值使用 AAD 连接。有关详细信息，请参阅[Azure Active Directory 连接同步： 配置 Office 365 资源的首选的数据位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p120">As mentioned previously for synchronized user objects from on-premises Active Directory, you can't use this procedure. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="eae1c-220">将邮箱移所需的时间长度取决于多个因素：</span><span class="sxs-lookup"><span data-stu-id="eae1c-220">How long it takes to move a mailbox depends on several factors:</span></span>
 
  - <span data-ttu-id="eae1c-221">大小和类型的邮箱。</span><span class="sxs-lookup"><span data-stu-id="eae1c-221">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="eae1c-222">要移动的邮箱数。</span><span class="sxs-lookup"><span data-stu-id="eae1c-222">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="eae1c-223">移动资源的可用性。</span><span class="sxs-lookup"><span data-stu-id="eae1c-223">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="eae1c-224">移动禁用在诉讼保留的邮箱</span><span class="sxs-lookup"><span data-stu-id="eae1c-224">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="eae1c-p121">禁用邮箱诉讼保留的保留电子数据展示不能通过更改其禁用状态中的其**PreferredDataLocation**值移动目的。将禁用的邮箱置于诉讼保留：</span><span class="sxs-lookup"><span data-stu-id="eae1c-p121">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes can't be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="eae1c-227">临时分派到邮箱的许可证。</span><span class="sxs-lookup"><span data-stu-id="eae1c-227">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="eae1c-228">更改**PreferredDataLocation**。</span><span class="sxs-lookup"><span data-stu-id="eae1c-228">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="eae1c-229">它已移至所选的地理位置以将其放回禁用状态后，请从邮箱中删除许可证。</span><span class="sxs-lookup"><span data-stu-id="eae1c-229">Remove the license from the mailbox after it has been moved to the selected Geo to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="eae1c-230">在特定的地理位置中创建新的云邮箱</span><span class="sxs-lookup"><span data-stu-id="eae1c-230">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="eae1c-231">若要在特定的地理位置创建一个新的邮箱，您需要执行以下步骤之一：</span><span class="sxs-lookup"><span data-stu-id="eae1c-231">To create a new mailbox in a specific Geo, you need to do either of these steps:</span></span>

- <span data-ttu-id="eae1c-232">在上一中所述配置**PreferredDataLocation**值部分*之前*（例如，通过将许可证分配之前对用户配置**PreferredDataLocation**值） 在 Exchange Online 中创建邮箱。</span><span class="sxs-lookup"><span data-stu-id="eae1c-232">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online (for example, by configuring the **PreferredDataLocation** value on a user before assigning a license).</span></span> 

- <span data-ttu-id="eae1c-233">设置**PreferredDataLocation**值的同时分配许可证。</span><span class="sxs-lookup"><span data-stu-id="eae1c-233">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="eae1c-234">要在特定的地理位置创建新仅使用云的授权的用户 （不 AAD 连接同步），请在 Azure AD PowerShell 中使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="eae1c-234">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="eae1c-235">本示例创建新的用户帐户的李大 Brunner 具有以下值：</span><span class="sxs-lookup"><span data-stu-id="eae1c-235">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="eae1c-236">用户主体名称： ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="eae1c-236">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="eae1c-237">名字： 李大</span><span class="sxs-lookup"><span data-stu-id="eae1c-237">First name: Elizabeth</span></span>

- <span data-ttu-id="eae1c-238">姓： Brunner</span><span class="sxs-lookup"><span data-stu-id="eae1c-238">Last name: Brunner</span></span>

- <span data-ttu-id="eae1c-239">显示名称李大 Brunner</span><span class="sxs-lookup"><span data-stu-id="eae1c-239">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="eae1c-240">密码： 随机生成所示命令的结果，（因为我们不使用*Password*参数）</span><span class="sxs-lookup"><span data-stu-id="eae1c-240">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="eae1c-241">许可证： contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="eae1c-241">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

<span data-ttu-id="eae1c-242">3-位置： 澳大利亚 （澳大利亚）</span><span class="sxs-lookup"><span data-stu-id="eae1c-242">3- Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="eae1c-243">有关创建新的用户帐户并在 Azure AD PowerShell 中查找 LicenseAssignment 值的详细信息，请参阅[使用 Office 365 PowerShell 创建用户帐户](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)和[查看许可证和服务与 Office 365 PowerShell 中](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)。</span><span class="sxs-lookup"><span data-stu-id="eae1c-243">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="eae1c-p122">如果使用 Exchange PowerShell 中启用邮箱和需要直接在 Geo **PreferredDataLocation**中指定要创建的邮箱，您需要使用如**Enable-mailbox**或**New-mailbox** Exchange Online cmdlet直接对云服务。如果您使用**Enable-remotemailbox**内部部署 Exchange cmdlet，将默认地理位置中创建邮箱。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p122">If you are using Exchange PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="eae1c-246">板载现有内部部署邮箱中的特定地理位置</span><span class="sxs-lookup"><span data-stu-id="eae1c-246">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="eae1c-247">您可以使用的标准入职培训工具和流程将邮箱从本地 Exchange 组织迁移到 Exchange Online，包括[在 EAC 中的迁移主控板](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)上，并使用[New-migrationbatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet 在 Exchange OnlinePowerShell。</span><span class="sxs-lookup"><span data-stu-id="eae1c-247">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="eae1c-p123">第一步是验证的用户对象存在 onboarded，并确认正确的**PreferredDataLocation**值在 Azure AD 中配置每个邮箱。入职培训工具将尊重**PreferredDataLocation**值，并会将邮箱迁移直接到指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p123">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="eae1c-250">或者，您可以使用以下步骤来直接在 Exchange Online PowerShell 中使用[New-moverequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet 的特定地理位置的板载邮箱。</span><span class="sxs-lookup"><span data-stu-id="eae1c-250">Or, you can use the following steps to onboard mailboxes directly in a specific Geo using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="eae1c-p124">验证每个邮箱 onboarded 和 Azure AD 中的设置为所需的值包含**PreferredDataLocation**存在用户对象。**PreferredDataLocation**的值将同步到相应的邮件用户对象的**MailboxRegion**属性在 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p124">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="eae1c-253">直接连接到特定的附属从连接说明使用本主题中前面的地理位置。</span><span class="sxs-lookup"><span data-stu-id="eae1c-253">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="eae1c-254">在 Exchange Online PowerShell 中，存储用于通过运行以下命令执行的变量中的邮箱迁移的本地管理员凭据：</span><span class="sxs-lookup"><span data-stu-id="eae1c-254">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="eae1c-255">在 Exchange Online PowerShell 中，创建新**New-moverequest**类似于下面的示例：</span><span class="sxs-lookup"><span data-stu-id="eae1c-255">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="eae1c-256">您需要从内部部署 Exchange 迁移到附属地理您当前连接到每个邮箱重复步骤 4。</span><span class="sxs-lookup"><span data-stu-id="eae1c-256">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite Geo you are currently connected to.</span></span>

6. <span data-ttu-id="eae1c-257">如果您需要将其他邮箱迁移到不同的附属地理位置，请对每个特定的附属地理重复步骤 2 到 4。</span><span class="sxs-lookup"><span data-stu-id="eae1c-257">If you need to migrate additional mailboxes to a different satellite Geo, repeat steps 2 through 4 for each specific satellite Geo.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="eae1c-258">多地理位置报告</span><span class="sxs-lookup"><span data-stu-id="eae1c-258">Multi-Geo Reporting</span></span>
<span data-ttu-id="eae1c-p125">在 Office 365 管理中心中的**多地理使用率报告**按地理位置显示用户计数。报告显示当前月份用户分布，并提供过去 6 个月的历史数据。</span><span class="sxs-lookup"><span data-stu-id="eae1c-p125">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by Geo. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
 
