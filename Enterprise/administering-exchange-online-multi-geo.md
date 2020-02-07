---
title: 在多地理位置环境中管理 Exchange Online 邮箱
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: 了解如何使用 Microsoft PowerShell 管理 Exchange Online 多地理位置设置。
ms.openlocfilehash: 135d3af76e03dfb7e6fcc9f55ba3be8ab21a6906
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844653"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a><span data-ttu-id="4b5c7-103">在多地理位置环境中管理 Exchange Online 邮箱</span><span class="sxs-lookup"><span data-stu-id="4b5c7-103">Administering Exchange Online mailboxes in a multi-geo environment</span></span>

<span data-ttu-id="4b5c7-104">需要远程 PowerShell 才能在 Office 365 环境中查看和配置多地理位置属性。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-104">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment.</span></span> <span data-ttu-id="4b5c7-105">若要连接到 Exchange Online PowerShell，请参阅[连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-105">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>

<span data-ttu-id="4b5c7-106">你需要 [Microsoft Azure Active Directory PowerShell 模块](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 或 v1.x 中的更高版本才能查看用户对象的 **PreferredDataLocation** 属性。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-106">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects.</span></span> <span data-ttu-id="4b5c7-107">无法通过 AAD PowerShell 直接修改通过 AAD Connect 同步到 AAD 中的用户对象的 **PreferredDataLocation** 值。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-107">User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell.</span></span> <span data-ttu-id="4b5c7-108">可以通过 AAD PowerShell 修改仅限云的用户对象。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-108">Cloud-only user objects can be modified via AAD PowerShell.</span></span> <span data-ttu-id="4b5c7-109">若要连接到 Azure AD PowerShell，请参阅[连接到 Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-109">To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span>

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a><span data-ttu-id="4b5c7-110">使用 Exchange Online PowerShell 直接连接到某个地理位置</span><span class="sxs-lookup"><span data-stu-id="4b5c7-110">Connect directly to a geo location using Exchange Online PowerShell</span></span>

<span data-ttu-id="4b5c7-111">通常，Exchange Online PowerShell 将连接到中心地理位置。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-111">Typically, Exchange Online PowerShell will connect to the central geo location.</span></span> <span data-ttu-id="4b5c7-112">但你也可以直接连接到附属地理位置。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-112">But, you can also connect directly to satellite geo locations.</span></span> <span data-ttu-id="4b5c7-113">由于性能有所改进，因此，当你仅管理附属地理位置中的用户时，我们建议直接连接到该位置。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-113">Because of performance improvements, we recommend connecting directly to the satellite geo location when you only manage users in that location.</span></span>

<span data-ttu-id="4b5c7-114">用于连接到特定地理位置的 *ConnectionUri* 参数与常规连接指令不同。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-114">To connect to a specific geo location, the *ConnectionUri* parameter is different than the regular connection instructions.</span></span> <span data-ttu-id="4b5c7-115">命令和值的其余部分是相同的。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-115">The rest of the commands and values are the same.</span></span> <span data-ttu-id="4b5c7-116">步骤如下：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-116">The steps are:</span></span>

1. <span data-ttu-id="4b5c7-117">在本地计算机上，打开 Windows PowerShell 并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-117">On your local computer, open Windows PowerShell and run the following command:</span></span>

   ```powershell
   $UserCredential = Get-Credential
   ```

   <span data-ttu-id="4b5c7-118">在“**Windows PowerShell 凭据请求**”对话框中，键入工作或学校帐户用户名和密码，再单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-118">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>

2. <span data-ttu-id="4b5c7-119">将 `<emailaddress>` 替换为目标地理位置中的**任何**邮箱的电子邮件地址，并运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-119">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command.</span></span> <span data-ttu-id="4b5c7-120">你对邮箱的权限和与步骤 1 中凭据的关系并不重要；电子邮件地址只是告知 Exchange Online 连接到何处。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-120">Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="4b5c7-121">例如，如果 olga@contoso.onmicrosoft.com 是你想要连接的地理位置的有效邮箱地址，则运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-121">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the geo location where you want to connect, run the following command:</span></span>

   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

3. <span data-ttu-id="4b5c7-122">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-122">Run the following command:</span></span>

    ```powershell
    Import-PSSession $Session
    ```

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="4b5c7-123">查看在 Exchange Online 组织中配置的可用地理位置</span><span class="sxs-lookup"><span data-stu-id="4b5c7-123">View the available geo locations that are configured in your Exchange Online organization</span></span>

<span data-ttu-id="4b5c7-124">若要在 Office 365 多地理位置中查看配置的地理位置的列表，请在 Exchange Online PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-124">To see the list of configured geo locations in Office 365 Multi-Geo, run the following command in Exchange Online PowerShell:</span></span>

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a><span data-ttu-id="4b5c7-125">查看 Exchange Online 组织的中心地理位置</span><span class="sxs-lookup"><span data-stu-id="4b5c7-125">View the central geo location for your Exchange Online organization</span></span>

<span data-ttu-id="4b5c7-126">若要查看租户的中心地理位置，请在 Exchange Online PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-126">To view your tenant's central geo location, run the following command in Exchange Online PowerShell:</span></span>

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="4b5c7-127">查找邮箱的地理位置</span><span class="sxs-lookup"><span data-stu-id="4b5c7-127">Find the geo location of a mailbox</span></span>

<span data-ttu-id="4b5c7-128">Exchange Online PowerShell 中的 **Get-Mailbox** cmdlet 显示邮箱的以下多地理位置相关属性：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-128">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="4b5c7-129">**Database**：对地理位置代码对应的数据库名称的前 3 个字母，告知你邮箱当前位于何处。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-129">**Database**: The first 3 letters of the database name correspond to the geo code, which tells you where the mailbox is currently located.</span></span> <span data-ttu-id="4b5c7-130">对于在线存档邮箱，应使用 **ArchiveDatabase** 属性。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-130">For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="4b5c7-131">**MailboxRegion**：指定管理员设置的地理位置代码（从 Azure AD 中的 **PreferredDataLocation** 同步）。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-131">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="4b5c7-132">**MailboxRegionLastUpdateTime**：指明 MailboxRegion 的最后（自动或手动）更新时间。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-132">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="4b5c7-133">若要查看邮箱的这些属性，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-133">To see these properties for a mailbox, use the following syntax:</span></span>

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="4b5c7-134">例如，若要查看邮箱 chris@contoso.onmicrosoft.com 的地理位置信息，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-134">For example, to see the geo location information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="4b5c7-135">此命令的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-135">The output of the command looks like this:</span></span>

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> <span data-ttu-id="4b5c7-136">**注意：** 如果数据库名称中的地理位置代码与 **MailboxRegion** 值不匹配，则会将该邮箱自动放入重定位队列，并移动到 **MailboxRegion** 值指定的地理位置 （Exchange Online 会查找这些属性值的不匹配之处）。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-136">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a><span data-ttu-id="4b5c7-137">将现有的仅限云邮箱移动到特定地理位置</span><span class="sxs-lookup"><span data-stu-id="4b5c7-137">Move an existing cloud-only mailbox to a specific geo location</span></span>

<span data-ttu-id="4b5c7-138">仅限云的用户是未通过 AAD Connect 同步到租户的用户。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-138">A cloud-only user is a user not synchronized to the tenant via AAD Connect.</span></span> <span data-ttu-id="4b5c7-139">此用户是在 Azure AD 中直接创建的。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-139">This user was created directly in Azure AD.</span></span> <span data-ttu-id="4b5c7-140">使用用于 Windows PowerShell 的 Azure AD 模块中的 **Get-MsolUser** 和 **Set-MsolUser** cmdlet 来查看或指定将在其中存储仅限云的用户邮箱的地理位置。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-140">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the geo location where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="4b5c7-141">若要查看用户的 **PreferredDataLocation** 值，请在 Azure AD PowerShell 中使用此语法：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-141">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="4b5c7-142">例如，若要查看用户 michelle@contoso.onmicrosoft.com 的 **PreferredDataLocation** 值，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-142">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="4b5c7-143">若要修改仅限云的用户对象的 **PreferredDataLocation** 值，请在 Azure AD PowerShell 中使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-143">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

<span data-ttu-id="4b5c7-144">例如，若要为用户 michelle@contoso.onmicrosoft.com 将 **PreferredDataLocation** 值设置为欧盟 (EUR) 地理位置，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-144">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="4b5c7-145">**注意**：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-145">**Notes**:</span></span>

- <span data-ttu-id="4b5c7-146">如前所述，你不能为从本地 Active Directory 同步的用户对象使用此过程。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-146">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory.</span></span> <span data-ttu-id="4b5c7-147">你需要在 Active Directory 中更改 **PreferredDataLocation** 值，并使用 AAD Connect 进行同步。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-147">You need to change the **PreferredDataLocation** value in Active Directory and synchronize it using AAD Connect.</span></span> <span data-ttu-id="4b5c7-148">有关详细信息，请参阅 [Azure Active Directory Connect 同步：为 Office 365 资源配置首选数据位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-148">For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

- <span data-ttu-id="4b5c7-149">将邮箱重定位到新的地理位置所花费的时间取决于若干因素：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-149">How long it takes to relocate a mailbox to a new geo location depends on several factors:</span></span>

  - <span data-ttu-id="4b5c7-150">邮箱的大小和类型。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-150">The size and type of mailbox.</span></span>

  - <span data-ttu-id="4b5c7-151">正在移动的邮箱数量。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-151">The number of mailboxes being moved.</span></span>

  - <span data-ttu-id="4b5c7-152">移动资源的可用性。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-152">The availability of move resources.</span></span>

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="4b5c7-153">移动处于诉讼保留状态的已禁用邮箱</span><span class="sxs-lookup"><span data-stu-id="4b5c7-153">Move disabled mailboxes that are on Litigation Hold</span></span>

<span data-ttu-id="4b5c7-154">对于处于诉讼保留状态的已禁用邮箱，无法通过在已禁用状态下通过更改其 **PreferredDataLocation** 值来移动这些邮箱。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-154">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state.</span></span> <span data-ttu-id="4b5c7-155">若要移动处于诉讼保留状态的已禁用邮箱，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-155">To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="4b5c7-156">暂时为邮箱分配一个许可证。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-156">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="4b5c7-157">更改 **PreferredDataLocation**。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-157">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="4b5c7-158">在将邮箱移到所选地理位置之后从邮箱中删除许可证，将其重新置于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-158">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a><span data-ttu-id="4b5c7-159">在特定地理位置中创建新的云邮箱</span><span class="sxs-lookup"><span data-stu-id="4b5c7-159">Create new cloud mailboxes in a specific geo location</span></span>

<span data-ttu-id="4b5c7-160">若要在特定地理位置中创建新邮箱，你需要执行以下任一步骤：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-160">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="4b5c7-161">在 Exchange Online 中创建邮箱*之前*，按上一节中所述配置 **PreferredDataLocation** 值。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-161">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online.</span></span> <span data-ttu-id="4b5c7-162">例如，在分配许可证之前为用户配置 **PreferredDataLocation** 值。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-162">For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span>

- <span data-ttu-id="4b5c7-163">在设置 **PreferredDataLocation** 值的同时分配许可证。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-163">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="4b5c7-164">若要在特定地理位置中创建新的仅限云许可用户（未通过 AAD Connect 同步），请在 Azure AD PowerShell 中使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-164">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific geo location, use the following syntax in Azure AD PowerShell:</span></span>

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

<span data-ttu-id="4b5c7-165">此示例使用下面的值为 Elizabeth Brunner 创建新用户帐户：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-165">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="4b5c7-166">用户主体名称：ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="4b5c7-166">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="4b5c7-167">名字：Elizabeth</span><span class="sxs-lookup"><span data-stu-id="4b5c7-167">First name: Elizabeth</span></span>

- <span data-ttu-id="4b5c7-168">姓氏：Brunner</span><span class="sxs-lookup"><span data-stu-id="4b5c7-168">Last name: Brunner</span></span>

- <span data-ttu-id="4b5c7-169">显示名称：Elizabeth Brunner</span><span class="sxs-lookup"><span data-stu-id="4b5c7-169">Display name: Elizabeth Brunner</span></span>

- <span data-ttu-id="4b5c7-170">密码： 随机生成，并显示在命令的结果中（因为我们未使用 *Password* 参数）</span><span class="sxs-lookup"><span data-stu-id="4b5c7-170">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="4b5c7-171">许可证：`contoso:ENTERPRISEPREMIUM` (E5)</span><span class="sxs-lookup"><span data-stu-id="4b5c7-171">License: `contoso:ENTERPRISEPREMIUM` (E5)</span></span>

- <span data-ttu-id="4b5c7-172">位置：澳大利亚 (AUS)</span><span class="sxs-lookup"><span data-stu-id="4b5c7-172">Location: Australia (AUS)</span></span>

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="4b5c7-173">有关创建新用户帐户和在 Azure AD PowerShell 中查找 LicenseAssignment 值的详细信息，请参阅[使用 Office 365 PowerShell 创建用户帐户](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)和[使用 Office 365 PowerShell 查看许可证和服务](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-173">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="4b5c7-174">如果使用 Exchange Online PowerShell 启用邮箱并需要在 **PreferredDataLocation** 中所指定的地理位置中直接创建邮箱，你需要直接针对云服务使用诸如 **Enable-Mailbox** 或 **New-Mailbox** 等 Exchange Online cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-174">If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the geo location that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service.</span></span> <span data-ttu-id="4b5c7-175">如果在本地 Exchange PowerShell 中使用 **Enable-RemoteMailbox** cmdlet，则会在中心地理位置创建邮箱。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-175">If you use the **Enable-RemoteMailbox** cmdlet in on-premises Exchange PowerShell, the mailbox will be created in the central geo location.</span></span>

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a><span data-ttu-id="4b5c7-176">在特定地理位置中载入现有本地邮箱</span><span class="sxs-lookup"><span data-stu-id="4b5c7-176">Onboard existing on-premises mailboxes in a specific geo location</span></span>

<span data-ttu-id="4b5c7-177">你可以使用标准载入工具和流程将邮箱从本地 Exchange 组织迁移到 Exchange Online，这些工具和流程包括 [EAC 中的“迁移”仪表板](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)，以及 Exchange Online PowerShell 中的 [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-177">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="4b5c7-178">第一步是验证用户对象对于要载入的每个邮箱是否存在，并验证是否在 Azure AD 中配置了正确的 **PreferredDataLocation** 值。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-178">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD.</span></span> <span data-ttu-id="4b5c7-179">载入工具将考虑 **PreferredDataLocation** 值，并将邮箱直接迁移到指定地理位置。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-179">The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified geo location.</span></span>

<span data-ttu-id="4b5c7-180">或者，你可以使用以下步骤，通过 Exchange Online PowerShell 中 [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet 在特定地理位置中直接载入邮箱。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-180">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="4b5c7-181">验证用户对象对于要载入的每个邮箱是否存在，并且是否在 Azure AD 中将 **PreferredDataLocation** 设置为所需的值。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-181">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD.</span></span> <span data-ttu-id="4b5c7-182">**PreferredDataLocation** 的值将同步到 Exchange Online 中对应邮件用户对象的 **MailboxRegion** 属性。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-182">The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="4b5c7-183">使用本主题前面的连接说明直接连接到特定附属地理位置。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-183">Connect directly to the specific satellite geo location using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="4b5c7-184">在 Exchange Online PowerShell 中，通过运行以下命令，将用于执行邮箱迁移的本地管理员凭据存储在一个变量中：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-184">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

   ```powershell
   $RC = Get-Credential
   ```

4. <span data-ttu-id="4b5c7-185">在 Exchange Online PowerShell 中，创建一个类似于以下示例的新 **New-MoveRequest**：</span><span class="sxs-lookup"><span data-stu-id="4b5c7-185">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span>

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. <span data-ttu-id="4b5c7-186">为需要从本地 Exchange 迁移到当前连接的附属地理位置的每个邮箱重复步骤 4。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-186">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite geo location you are currently connected to.</span></span>

6. <span data-ttu-id="4b5c7-187">如果需要将其他邮箱迁移到不同的附属地理位置，请为每个特定位置重复步骤 2-4。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-187">If you need to migrate additional mailboxes to different satellite geo locations, repeat steps 2 through 4 for each specific location.</span></span>

## <a name="multi-geo-reporting"></a><span data-ttu-id="4b5c7-188">多地理位置报告</span><span class="sxs-lookup"><span data-stu-id="4b5c7-188">Multi-geo reporting</span></span>

<span data-ttu-id="4b5c7-189">Microsoft 365 管理中心中的“**多地理位置使用情况报告**”按地理位置显示用户计数。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-189">**Multi-Geo Usage Reports** in the Microsoft 365 admin center displays the user count by geo location.</span></span> <span data-ttu-id="4b5c7-190">该报告显示当前月份的用户分布，并提供过去 6 个月的历史数据。</span><span class="sxs-lookup"><span data-stu-id="4b5c7-190">The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b5c7-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b5c7-191">See also</span></span>

[<span data-ttu-id="4b5c7-192">使用 Windows PowerShell 管理 Office 365 和 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="4b5c7-192">Managing Office 365 and Exchange Online with Windows PowerShell</span></span>](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)
