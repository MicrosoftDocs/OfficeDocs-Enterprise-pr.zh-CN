---
title: 多地区能力在 Exchange 联机
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
description: 联机 Exchange 中的多个地区功能的多个地理区域展开您 Office 365 的状态。
ms.openlocfilehash: 6378f8a010b790674f07150aa39cbbc38c60b7fe
ms.sourcegitcommit: 63e2844daa2863dddcd84819966a708c434e8580
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="34564-103">多地区能力在 Exchange 联机</span><span class="sxs-lookup"><span data-stu-id="34564-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="34564-p101">Office 365 中的多个地区功能启用单个租户，若要跨越多个地理位置 (Geo)。启用多个地区后，客户可以在每用户基础上选择联机 Exchange 邮箱内容 （静态数据） 的位置。</span><span class="sxs-lookup"><span data-stu-id="34564-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations (Geos). When Multi-Geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="34564-p102">基于您的帐单地址确定初始租户位置 （称为您的"默认值"或"中心"位置）。启用多个地区后，可放入更多的"卫星"位置的邮箱：</span><span class="sxs-lookup"><span data-stu-id="34564-p102">Your initial tenant location (referred to as your "default" or "central" location) is determined based on your billing address. When Multi-Geo is enabled, you can place mailboxes in additional "satellite" locations by:</span></span>

- <span data-ttu-id="34564-108">在卫星中直接创建新的联机 Exchange 邮箱。</span><span class="sxs-lookup"><span data-stu-id="34564-108">Creating a new Exchange Online mailbox directly in a satellite.</span></span>

- <span data-ttu-id="34564-109">将现有的联机 Exchange 邮箱移动到卫星。</span><span class="sxs-lookup"><span data-stu-id="34564-109">Moving an existing Exchange Online mailbox into a satellite.</span></span>

- <span data-ttu-id="34564-110">板载直接在卫星内部 Exchange 组织中的邮箱。</span><span class="sxs-lookup"><span data-stu-id="34564-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite.</span></span>

<span data-ttu-id="34564-111">下面的 Geo 有在多个地区配置中使用：</span><span class="sxs-lookup"><span data-stu-id="34564-111">The following Geos are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="34564-112">亚太</span><span class="sxs-lookup"><span data-stu-id="34564-112">Asia Pacific</span></span>

- <span data-ttu-id="34564-113">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="34564-113">Australia</span></span>

- <span data-ttu-id="34564-114">加拿大</span><span class="sxs-lookup"><span data-stu-id="34564-114">Canada</span></span>

- <span data-ttu-id="34564-115">欧盟</span><span class="sxs-lookup"><span data-stu-id="34564-115">European Union</span></span>

- <span data-ttu-id="34564-116">印度 (目前仅适用于客户与在印度的账单地址)</span><span class="sxs-lookup"><span data-stu-id="34564-116">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="34564-117">日本</span><span class="sxs-lookup"><span data-stu-id="34564-117">Japan</span></span>

- <span data-ttu-id="34564-118">韩国</span><span class="sxs-lookup"><span data-stu-id="34564-118">Korea</span></span>

- <span data-ttu-id="34564-119">英国</span><span class="sxs-lookup"><span data-stu-id="34564-119">United Kingdom</span></span>

- <span data-ttu-id="34564-120">美国</span><span class="sxs-lookup"><span data-stu-id="34564-120">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="34564-121">必备配置</span><span class="sxs-lookup"><span data-stu-id="34564-121">Prerequisite configuration</span></span>
<span data-ttu-id="34564-p103">您可以开始使用在 Exchange 在在线多地区功能之前，Microsoft 需要配置多地区支持您 Exchange Online 租户。订购多地区许可证和通常应采取不超过 30 天，以完成时，将触发此一次性配置进程。</span><span class="sxs-lookup"><span data-stu-id="34564-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for Multi-Geo support. This one-time configuration process is triggered when you order Multi-Geo licenses and should typically take less than 30 days to complete.</span></span>

<span data-ttu-id="34564-p104">当您的配置已经启动和完成，您将收到通知[Office 365 邮件中心](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093)。购买多地区许可证时，将自动触发配置。</span><span class="sxs-lookup"><span data-stu-id="34564-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has started and completed. Configuration is automatically triggered when you buy Multi-Geo licenses.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="34564-126">邮箱放置和移动</span><span class="sxs-lookup"><span data-stu-id="34564-126">Mailbox placement and moves</span></span>
<span data-ttu-id="34564-127">Microsoft 完成必要多地区配置步骤后，Exchange Online 将履行在用户对象上的**PreferredDataLocation**属性在 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="34564-127">After Microsoft completes the prerequisite Multi-Geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="34564-p105">Exchange 联机同步到在线 Exchange 目录服务中的**MailboxRegion**属性从 Azure 广告**PreferredDataLocation**属性。**MailboxRegion**的值确定的 Geo 放置用户邮箱和任何相关的存档邮箱。它不可能来配置用户的主邮箱和存档邮箱驻留在不同的 Geo。只有一个地区可以配置每个用户对象。</span><span class="sxs-lookup"><span data-stu-id="34564-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It isn't possible to configure a user's primary mailbox and archive mailboxes to reside in different Geos. Only one Geo may be configured per user object.</span></span>

- <span data-ttu-id="34564-132">在**PreferredDataLocation**配置上具有现有邮箱的用户时，该邮箱将自动移到指定的地区。</span><span class="sxs-lookup"><span data-stu-id="34564-132">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be automatically moved to the specified Geo.</span></span> 

- <span data-ttu-id="34564-133">在**PreferredDataLocation**配置上不具有现有邮箱的用户时，邮箱将调配到指定的地区。</span><span class="sxs-lookup"><span data-stu-id="34564-133">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified Geo.</span></span> 

- <span data-ttu-id="34564-134">如果未不指定任何地区，邮箱将被置于默认地区。</span><span class="sxs-lookup"><span data-stu-id="34564-134">If no Geo is specified, the mailbox will be placed in the default Geo.</span></span>

<span data-ttu-id="34564-p106">**注意**： 多地区能力和 Skype 业务联机地区组织主持会议这两个**PreferredDataLocation**属性用于在用户对象上找到服务。如果您在用户对象的承载地区组织会议上配置**PreferredDataLocation**值，邮箱和 OneDrive 的用户将自动移动到指定的地区多地区启用 Office 365 租户在后。</span><span class="sxs-lookup"><span data-stu-id="34564-p106">**Note**: Multi-Geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox and OneDrive for those users will be automatically moved to the specified Geo after Multi-Geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="34564-137">联机 Exchange 中的多个地区的功能限制</span><span class="sxs-lookup"><span data-stu-id="34564-137">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="34564-p107">用户邮箱、 资源邮箱 （房间和设备邮箱） 和共享的邮箱支持多个地理特征。仅可以将公用文件夹的邮箱和 Office 365 组放在客户的家乡地区。</span><span class="sxs-lookup"><span data-stu-id="34564-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support Multi-Geo features. You can only place public folder mailboxes and Office 365 Groups in the customer's home Geo.</span></span>
 
2. <span data-ttu-id="34564-p108">安全性和法规遵从功能 （例如，审核和 eDiscovery） Exchange 管理员中心 (EAC) 中的可用不可用在多个地区组织。相反，您需要使用[Office 365 安全和法规遵从性中心](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)配置安全性和法规遵从性功能。</span><span class="sxs-lookup"><span data-stu-id="34564-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in Multi-Geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="34564-p109">他们的邮箱移动到新的地区时，对于 Mac 用户的 outlook 可能会遇到暂时失去他们的在线存档文件夹的访问权限。出现这种情况时用户的主和存档邮箱位于不同的 Geo，因为跨地区邮箱移动可能会在不同的时间完成。</span><span class="sxs-lookup"><span data-stu-id="34564-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new Geo. This condition occurs when the user's the primary and archive mailboxes are in different Geos, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="34564-p110">用户不能通过在 Outlook 中 （以前称为 Outlook Web App 或 OWA） 网站在 Geo 共享*邮箱文件夹*。例如，欧盟中的用户不能使用 Outlook web 上的位于美国邮箱中打开一个共享的文件夹。但是，在 web 用户的 Outlook 可以打开*其他邮箱*不同 Geo 中使用一个单独的浏览器窗口[打开 Outlook Web App 在单独的浏览器窗口中的其他人的邮箱](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)中所述。</span><span class="sxs-lookup"><span data-stu-id="34564-p110">Users can't share *mailbox folders* across Geos in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="34564-147">**注意**： 在 Outlook 窗口中支持跨地区邮箱文件夹共享。</span><span class="sxs-lookup"><span data-stu-id="34564-147">**Note**: Cross-Geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

5. <span data-ttu-id="34564-p111">目前，跨地区日历委派不支持在 web 上的 Outlook 中。在 Windows 上的 Outlook 中支持跨地区日历委派。</span><span class="sxs-lookup"><span data-stu-id="34564-p111">Currently, cross-Geo calendar delegation isn't supported in Outlook on the web. Cross-Geo calendar delegation is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="34564-150">管理</span><span class="sxs-lookup"><span data-stu-id="34564-150">Administration</span></span> 
<span data-ttu-id="34564-p112">远程 PowerShell 需要查看和配置 Office 365 环境中与地理相关的属性。用来管理 Office 365 的各种 PowerShell 模块的信息，请参阅[管理 Office 365 和 Exchange 联机，使用 Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)。</span><span class="sxs-lookup"><span data-stu-id="34564-p112">Remote PowerShell is required to view and configure Geo-related properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="34564-p113">您需要[Microsoft Azure 活动目录 PowerShell 模块](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx)v1.1.166.0 或以后在 1.x 版以查看在用户对象上的**PreferredDataLocation**属性。若要连接到 Azure AD PowerShell，请参阅[连接到 Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)。</span><span class="sxs-lookup"><span data-stu-id="34564-p113">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="34564-155">要连接到 Exchange 联机 PowerShell，请参阅[连接到 Exchange 联机 PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。</span><span class="sxs-lookup"><span data-stu-id="34564-155">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="34564-156">直接连接到使用 Exchange 联机 PowerShell 特定地理</span><span class="sxs-lookup"><span data-stu-id="34564-156">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="34564-p114">通常情况下，Exchange 联机 PowerShell 将连接到默认的地区。但是，也可以直接到非默认 Geo 连接。由于改进了性能，我们建议将直接连接到非默认地区时只能管理在该地区的用户。</span><span class="sxs-lookup"><span data-stu-id="34564-p114">Typically, Exchange Online PowerShell will connect to the default Geo. But, you can also connect directly to non-default Geos. Because of performance improvements, we recommend connecting directly to the non-default Geo when you only manage users in that Geo.</span></span>

<span data-ttu-id="34564-p115">要连接到特定的地区， *ConnectionUri*参数，是不同于常规的连接说明。其余的命令和值是相同的。步骤如下：</span><span class="sxs-lookup"><span data-stu-id="34564-p115">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="34564-163">在本地计算机上打开 Windows PowerShell 并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="34564-163">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="34564-164">**Windows PowerShell 凭据请求**对话框中键入您的工作或学校的帐户和密码，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="34564-164">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="34564-p116">更换`<emailaddress>`在目标地区中的**任何**邮箱存储和运行下面的命令的电子邮件地址。邮箱，并向您的凭据在步骤 1 中的关系的权限不是一个因素;电子邮件地址仅仅告诉 Exchange Online 的连接位置。</span><span class="sxs-lookup"><span data-stu-id="34564-p116">Replace `<emailaddress>` with the email address of **any** mailbox in the target Geo and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="34564-167">例如，如果 olga@contoso.onmicrosoft.com 是在您想要连接地区一个有效邮箱的电子邮件地址，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="34564-167">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="34564-168">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="34564-168">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="34564-169">Azure AD 连接版本要求</span><span class="sxs-lookup"><span data-stu-id="34564-169">Azure AD Connect version requirements</span></span>
<span data-ttu-id="34564-p117">AAD 连接版本 1.1.524.0 或更高版本为从内部部署 Active Directory 同步的用户对象上设置**PreferredDataLocation**属性是唯一受支持的方法。有关详细说明，请参阅[Azure 活动目录连接同步： 配置 Office 365 提供资源的首选的数据位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。</span><span class="sxs-lookup"><span data-stu-id="34564-p117">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="34564-172">地区代码</span><span class="sxs-lookup"><span data-stu-id="34564-172">Geo Codes</span></span>
<span data-ttu-id="34564-p118">三个字母的代码用于在**PreferredDataLocation**属性中指定的地区。下表列出可用的 Geo 的代码：</span><span class="sxs-lookup"><span data-stu-id="34564-p118">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="34564-175">地域</span><span class="sxs-lookup"><span data-stu-id="34564-175">Geo</span></span> |<span data-ttu-id="34564-176">代码</span><span class="sxs-lookup"><span data-stu-id="34564-176">Code</span></span> |
|---------|---------|
|<span data-ttu-id="34564-177">亚太</span><span class="sxs-lookup"><span data-stu-id="34564-177">Asia/Pacific</span></span> |<span data-ttu-id="34564-178">APC 公司</span><span class="sxs-lookup"><span data-stu-id="34564-178">APC</span></span> |
|<span data-ttu-id="34564-179">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="34564-179">Australia</span></span> |<span data-ttu-id="34564-180">澳大利亚</span><span class="sxs-lookup"><span data-stu-id="34564-180">AUS</span></span> |
|<span data-ttu-id="34564-181">加拿大</span><span class="sxs-lookup"><span data-stu-id="34564-181">Canada</span></span> |<span data-ttu-id="34564-182">可以</span><span class="sxs-lookup"><span data-stu-id="34564-182">CAN</span></span> |
|<span data-ttu-id="34564-183">欧盟</span><span class="sxs-lookup"><span data-stu-id="34564-183">European Union</span></span> |<span data-ttu-id="34564-184">欧元</span><span class="sxs-lookup"><span data-stu-id="34564-184">EUR</span></span> |
|<span data-ttu-id="34564-185">印度</span><span class="sxs-lookup"><span data-stu-id="34564-185">India</span></span> |<span data-ttu-id="34564-186">IND</span><span class="sxs-lookup"><span data-stu-id="34564-186">IND</span></span> |
|<span data-ttu-id="34564-187">日本</span><span class="sxs-lookup"><span data-stu-id="34564-187">Japan</span></span> |<span data-ttu-id="34564-188">日文</span><span class="sxs-lookup"><span data-stu-id="34564-188">JPN</span></span> |
|<span data-ttu-id="34564-189">韩国</span><span class="sxs-lookup"><span data-stu-id="34564-189">Korea</span></span> |<span data-ttu-id="34564-190">韩文</span><span class="sxs-lookup"><span data-stu-id="34564-190">KOR</span></span> |
|<span data-ttu-id="34564-191">英国</span><span class="sxs-lookup"><span data-stu-id="34564-191">United Kingdom</span></span> |<span data-ttu-id="34564-192">GBR</span><span class="sxs-lookup"><span data-stu-id="34564-192">GBR</span></span> |
|<span data-ttu-id="34564-193">美国</span><span class="sxs-lookup"><span data-stu-id="34564-193">United States</span></span> |<span data-ttu-id="34564-194">名称</span><span class="sxs-lookup"><span data-stu-id="34564-194">NAM</span></span> |

<span data-ttu-id="34564-p119">**注**： **PreferredDataLocation**和**MailboxRegion**属性是与没有错误检查的字符串。如果您输入了无效的值 (例如，NAN) 邮箱将放置在默认的地区。</span><span class="sxs-lookup"><span data-stu-id="34564-p119">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="34564-197">查看联机 Exchange 组织中配置可用 Geo</span><span class="sxs-lookup"><span data-stu-id="34564-197">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="34564-198">若要查看已配置 Geo 联机 Exchange 组织中的列表，请运行下面的命令在 Exchange 联机 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="34564-198">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

<span data-ttu-id="34564-199">命令输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="34564-199">The output of the command looks like this:</span></span>

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

### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="34564-200">找到一个邮箱的地理位置</span><span class="sxs-lookup"><span data-stu-id="34564-200">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="34564-201">**获取邮箱**cmdlet Exchange 联机继续显示邮箱与地理相关的以下属性：</span><span class="sxs-lookup"><span data-stu-id="34564-201">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following Geo-related properties on mailboxes:</span></span>

- <span data-ttu-id="34564-202">**数据库**： 数据库名称的前 3 个字母对应于地区代码中，告诉您邮箱是当前所在的位置。</span><span class="sxs-lookup"><span data-stu-id="34564-202">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located.</span></span>

- <span data-ttu-id="34564-203">**MailboxRegion**： 指定由管理员 （同步是**PreferredDataLocation**在 Azure AD） 设置了的地区代码。</span><span class="sxs-lookup"><span data-stu-id="34564-203">**MailboxRegion**: Specifies the Geo code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="34564-204">**MailboxRegionLastUpdateTime**： 指示当 MailboxRegion 上次更新 （自动或手动）。</span><span class="sxs-lookup"><span data-stu-id="34564-204">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="34564-205">要查看这些邮箱属性，请使用下面的语法：</span><span class="sxs-lookup"><span data-stu-id="34564-205">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="34564-206">例如，若要查看邮箱 chris@contoso.onmicrosoft.com 的地理信息，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="34564-206">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="34564-207">命令输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="34564-207">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> [!NOTE]
> <span data-ttu-id="34564-208">如果数据库名称中的地区代码与**MailboxRegion**值不匹配，邮箱将自动移到指定的**MailboxRegion**值 （Exchange 联机查找这些属性值之间的不匹配） 地区。</span><span class="sxs-lookup"><span data-stu-id="34564-208">If the Geo code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically moved to the Geo specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a><span data-ttu-id="34564-209">将现有的云邮箱移动到特定的地理</span><span class="sxs-lookup"><span data-stu-id="34564-209">Move an existing cloud mailbox to a specific Geo</span></span>
<span data-ttu-id="34564-210">使用**Get MsolUser**和**一组 MsolUser** cmdlet Windows PowerShell Azure AD 模块中查看或指定用户的邮箱存储地理。</span><span class="sxs-lookup"><span data-stu-id="34564-210">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a user's mailbox will be stored.</span></span>

<span data-ttu-id="34564-211">若要查看用户的**PreferredDataLocation**值，请在 Azure AD PowerShell 中使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="34564-211">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="34564-212">例如，若要查看用户 michelle@contoso.onmicrosoft.com 的**PreferredDataLocation**值，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="34564-212">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="34564-213">命令输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="34564-213">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="34564-214">若要修改仅云用户对象的**PreferredDataLocation**值，请在 Azure AD PowerShell 使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="34564-214">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="34564-215">例如，若要将**PreferredDataLocation**值设置为欧盟 （欧元） 的用户 michelle@contoso.onmicrosoft.com，运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="34564-215">For example, to set the **PreferredDataLocation** value to the European Union (EUR) for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="34564-216">**注释**：</span><span class="sxs-lookup"><span data-stu-id="34564-216">**Notes**:</span></span>

- <span data-ttu-id="34564-p120">前面已提到为从内部部署 Active Directory 同步的用户对象，您不能使用此过程。您需要更改使用 AAD 连接的**PreferredDataLocation**值。有关详细信息，请参阅[Azure 活动目录连接同步： 配置 Office 365 提供资源的首选的数据位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。</span><span class="sxs-lookup"><span data-stu-id="34564-p120">As mentioned previously for synchronized user objects from on-premises Active Directory, you can't use this procedure. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="34564-220">移动邮箱所需的时间取决于几个因素：</span><span class="sxs-lookup"><span data-stu-id="34564-220">How long it takes to move a mailbox depends on several factors:</span></span>
 
  - <span data-ttu-id="34564-221">大小和类型的邮箱。</span><span class="sxs-lookup"><span data-stu-id="34564-221">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="34564-222">要移动的邮箱数。</span><span class="sxs-lookup"><span data-stu-id="34564-222">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="34564-223">移动资源的可用性。</span><span class="sxs-lookup"><span data-stu-id="34564-223">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="34564-224">在诉讼封存禁用移动邮箱</span><span class="sxs-lookup"><span data-stu-id="34564-224">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="34564-p121">禁用为 eDiscovery 目的不能移动通过更改它们处于禁用状态的**PreferredDataLocation**值保留在诉讼封存的邮箱。诉讼封存在移动被禁用的邮箱：</span><span class="sxs-lookup"><span data-stu-id="34564-p121">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes can't be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="34564-227">暂时将许可证分配给该邮箱。</span><span class="sxs-lookup"><span data-stu-id="34564-227">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="34564-228">更改**PreferredDataLocation**。</span><span class="sxs-lookup"><span data-stu-id="34564-228">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="34564-229">从邮箱中删除许可证后它已被移动到选定的地区要将其放回禁用状态。</span><span class="sxs-lookup"><span data-stu-id="34564-229">Remove the license from the mailbox after it has been moved to the selected Geo to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="34564-230">在特定地区中创建新的云邮箱</span><span class="sxs-lookup"><span data-stu-id="34564-230">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="34564-231">要在特定地区创建一个新的邮箱，您需要执行下列步骤之一：</span><span class="sxs-lookup"><span data-stu-id="34564-231">To create a new mailbox in a specific Geo, you need to do either of these steps:</span></span>

- <span data-ttu-id="34564-232">如前面所述配置的**PreferredDataLocation**值部分*之前*（例如，通过配置用户分配许可证之前的**PreferredDataLocation**值） 在 Exchange 联机创建邮箱。</span><span class="sxs-lookup"><span data-stu-id="34564-232">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online (for example, by configuring the **PreferredDataLocation** value on a user before assigning a license).</span></span> 

- <span data-ttu-id="34564-233">在同一时间将**PreferredDataLocation**值设置分派许可证。</span><span class="sxs-lookup"><span data-stu-id="34564-233">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="34564-234">若要在特定地区创建新云仅授权的用户 （AAD 连接同步），请在 Azure AD PowerShell 使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="34564-234">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="34564-235">本示例创建新的用户帐户的李大 Brunner 具有以下值：</span><span class="sxs-lookup"><span data-stu-id="34564-235">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="34564-236">用户主体名称： ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="34564-236">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="34564-237">第一名： 李大</span><span class="sxs-lookup"><span data-stu-id="34564-237">First name: Elizabeth</span></span>

- <span data-ttu-id="34564-238">姓名： Brunner</span><span class="sxs-lookup"><span data-stu-id="34564-238">Last name: Brunner</span></span>

- <span data-ttu-id="34564-239">显示名称李大 Brunner</span><span class="sxs-lookup"><span data-stu-id="34564-239">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="34564-240">密码： 随机生成和显示该命令的结果中，（因为我们不使用*密码*参数）</span><span class="sxs-lookup"><span data-stu-id="34564-240">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="34564-241">许可： contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="34564-241">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

<span data-ttu-id="34564-242">3 位置： 澳大利亚 （澳大利亚）</span><span class="sxs-lookup"><span data-stu-id="34564-242">3- Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="34564-243">有关如何创建新的用户帐户和 Azure 广告继续查找 LicenseAssignment 值的详细信息，请参阅[Office 365 PowerShell 创建用户帐户](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)并[查看许可证和服务与 Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)。</span><span class="sxs-lookup"><span data-stu-id="34564-243">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="34564-p122">如果使用的 Exchange PowerShell 启用邮箱，需要直接在 Geo 在**PreferredDataLocation**中指定要创建的邮箱，您需要使用诸如**启用邮箱**或**新建邮箱**的 Exchange Online cmdlet直接对云服务。如果您使用**启用 RemoteMailbox**内部 Exchange cmdlet，将在默认的地区创建邮箱。</span><span class="sxs-lookup"><span data-stu-id="34564-p122">If you are using Exchange PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="34564-246">板载现有部署的邮箱中特定地理</span><span class="sxs-lookup"><span data-stu-id="34564-246">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="34564-247">可以使用标准的板载工具和进程将从内部 Exchange 组织的邮箱迁移到 Exchange Online，包括[迁移中 EAC 的仪表板](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)和[新建 MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet 在 Exchange 联机PowerShell。</span><span class="sxs-lookup"><span data-stu-id="34564-247">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="34564-p123">第一步是验证一个用户对象存在于每个邮箱是 onboarded，并验证在 Azure AD 中配置正确的**PreferredDataLocation**值。板载工具将尊重的**PreferredDataLocation**值，并将直接到指定的地区迁移邮箱。</span><span class="sxs-lookup"><span data-stu-id="34564-p123">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="34564-250">或者，可以使用以下步骤在使用 Exchange 联机 PowerShell[新建 MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet 特定地区中直接板载邮箱。</span><span class="sxs-lookup"><span data-stu-id="34564-250">Or, you can use the following steps to onboard mailboxes directly in a specific Geo using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="34564-p124">验证用户对象存在于每个邮箱为 onboarded 和**PreferredDataLocation** Azure AD 中设置为所需的值。**PreferredDataLocation**的值将被同步到相应的邮件用户对象的**MailboxRegion**特性在 Exchange 联机。</span><span class="sxs-lookup"><span data-stu-id="34564-p124">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="34564-253">直接连接到特定的附属地区使用本主题中前面的连接说明。</span><span class="sxs-lookup"><span data-stu-id="34564-253">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="34564-254">在 Exchange 联机 PowerShell 存储用于通过运行下面的命令在一个变量中执行邮箱迁移的本地管理员凭据：</span><span class="sxs-lookup"><span data-stu-id="34564-254">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="34564-255">在 Exchange 联机 PowerShell 创建新**新建 MoveRequest**与以下示例类似：</span><span class="sxs-lookup"><span data-stu-id="34564-255">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="34564-256">重复步骤 4，您需要从内部 Exchange 迁移到您当前连接到的 Geo 卫星每个邮箱。</span><span class="sxs-lookup"><span data-stu-id="34564-256">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite Geo you are currently connected to.</span></span>

6. <span data-ttu-id="34564-257">如果您需要将其他邮箱迁移到不同的附属地区，为每个特定附属地区重复步骤 2 到 4。</span><span class="sxs-lookup"><span data-stu-id="34564-257">If you need to migrate additional mailboxes to a different satellite Geo, repeat steps 2 through 4 for each specific satellite Geo.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="34564-258">多地区报告</span><span class="sxs-lookup"><span data-stu-id="34564-258">Multi-Geo Reporting</span></span>
<span data-ttu-id="34564-p125">在 Office 365 管理中心**多地区使用率报告**按地区显示用户计数。该报告显示当前月份的用户分布，为过去 6 个月提供的历史数据。</span><span class="sxs-lookup"><span data-stu-id="34564-p125">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by Geo. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
 
