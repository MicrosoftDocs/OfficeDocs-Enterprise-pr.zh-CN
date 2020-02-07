---
title: 使用 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴将域添加到客户端租赁
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 摘要：使用适用于 Office 365 的 Windows PowerShell 将备用域名添加到现有的客户租户。
ms.openlocfilehash: 3097ac1574f946a8bd0c82eb25892107ce39b9be
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844273"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="64a6a-103">使用 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴将域添加到客户端租赁</span><span class="sxs-lookup"><span data-stu-id="64a6a-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="64a6a-104">**摘要：** 使用适用于 Office 365 的 Windows PowerShell 将备用域名添加到现有客户租户。</span><span class="sxs-lookup"><span data-stu-id="64a6a-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="64a6a-105">你可以使用适用于 Office 365 的 Windows PowerShell 创建新域并将其与您的客户租户相关联，其速度比使用 Microsoft 365 管理中心要快。</span><span class="sxs-lookup"><span data-stu-id="64a6a-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="64a6a-106">委派访问权限 (DAP) 合作伙伴是联合和云解决方案提供商 (CSP) 合作伙伴。</span><span class="sxs-lookup"><span data-stu-id="64a6a-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="64a6a-107">他们通常是面向其他公司的网络或电信提供商。</span><span class="sxs-lookup"><span data-stu-id="64a6a-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="64a6a-108">他们将 Office 365 订阅捆绑到为其客户提供的服务产品中。</span><span class="sxs-lookup"><span data-stu-id="64a6a-108">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="64a6a-109">当他们销售 Office 365 订阅时，会自动获得对客户租赁的“代表以下方管理”(AOBO) 权限，这样他们便可以管理客户租赁并生成相应报告。</span><span class="sxs-lookup"><span data-stu-id="64a6a-109">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="64a6a-110">在开始之前，您需要知道什么？</span><span class="sxs-lookup"><span data-stu-id="64a6a-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="64a6a-p102">本主题中的步骤需要您连接到适用于Office 365的Windows PowerShell。有关说明，请参阅[连接到 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="64a6a-p102">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="64a6a-113">您也需要您的合作伙伴租户管理员凭据。</span><span class="sxs-lookup"><span data-stu-id="64a6a-113">You also need your partner tenant administrator credentials.</span></span>
  
<span data-ttu-id="64a6a-114">您也需要以下信息：</span><span class="sxs-lookup"><span data-stu-id="64a6a-114">You also need the following information:</span></span>
  
- <span data-ttu-id="64a6a-115">您需要客户所需的完全限定的域名 (FQDN)。</span><span class="sxs-lookup"><span data-stu-id="64a6a-115">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="64a6a-116">您需要客户的 **TenantId** 。</span><span class="sxs-lookup"><span data-stu-id="64a6a-116">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="64a6a-p103">FQDN 必须在 Internet 域名服务 (DNS) 注册机构（如 GoDaddy）中注册。有关如何公开注册域名的详细信息，请参阅[如何购买域名](https://go.microsoft.com/fwlink/p/?LinkId=532541)。</span><span class="sxs-lookup"><span data-stu-id="64a6a-p103">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="64a6a-p104">您需要了解如何为您的 DNS 注册机构的注册 DNS 区域添加 TXT 记录。有关如何添加 TXT 记录的详细信息，请参阅[在任何 DNS 托管提供商处为 Office 365 创建 DNS 记录](https://go.microsoft.com/fwlink/p/?LinkId=532542)。如果这些步骤对您不适用，您需要查找适用于您的 DNS 注册机构的过程。</span><span class="sxs-lookup"><span data-stu-id="64a6a-p104">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="64a6a-122">创建域</span><span class="sxs-lookup"><span data-stu-id="64a6a-122">Create domains</span></span>

 <span data-ttu-id="64a6a-p105">您的客户可能会要求您创建与其租赁关联的其他域，因为他们不想让默认的<domain>.onmicrosoft.com域成为向全世界展示其公司标识的主要域。此步骤将引导您创建与您的客户租赁相关联的新域。</span><span class="sxs-lookup"><span data-stu-id="64a6a-p105">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="64a6a-125">若要执行某些操作，必须将您登录时使用的合作伙伴管理员帐户设置为 "**完全管理**"，以便在 Microsoft 365 管理中心的 "管理员" 帐户详细信息中，"为**您支持的公司分配管理访问权限**" 设置为 "完全管理"。</span><span class="sxs-lookup"><span data-stu-id="64a6a-125">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Microsoft 365 admin center.</span></span> <span data-ttu-id="64a6a-126">For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span><span class="sxs-lookup"><span data-stu-id="64a6a-126">For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="64a6a-127">在 Azure Active Directory 中创建域</span><span class="sxs-lookup"><span data-stu-id="64a6a-127">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="64a6a-128">此命令在 Azure Active Directory 中创建域，但不会将其与公开注册的域相关联。</span><span class="sxs-lookup"><span data-stu-id="64a6a-128">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="64a6a-129">当你向 Microsoft Office 365 企业版证明你拥有公开注册的域时，这一问题将随之而来。</span><span class="sxs-lookup"><span data-stu-id="64a6a-129">That comes when you prove that you own the publicly registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
><span data-ttu-id="64a6a-130">PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。</span><span class="sxs-lookup"><span data-stu-id="64a6a-130">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="64a6a-131">若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="64a6a-131">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="64a6a-132">获取 DNS TXT 验证记录的数据</span><span class="sxs-lookup"><span data-stu-id="64a6a-132">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="64a6a-p109">Office 365 将生成您需要放入 DNS TXT 验证记录中的特定数据。要获取数据，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="64a6a-p109">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

<span data-ttu-id="64a6a-135">你将获得如下所示的输出：</span><span class="sxs-lookup"><span data-stu-id="64a6a-135">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="64a6a-136">你将需要此文本以在公开注册的 DNS 区域中创建 TXT 记录。</span><span class="sxs-lookup"><span data-stu-id="64a6a-136">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="64a6a-137">请确保将其复制并保存。</span><span class="sxs-lookup"><span data-stu-id="64a6a-137">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="64a6a-138">在公开注册的 DNS 区域中添加 TXT 记录</span><span class="sxs-lookup"><span data-stu-id="64a6a-138">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="64a6a-139">在 Office 365 开始接受定向到公开注册的域名的流量之前，你必须证明你拥有域并且具有域的管理员权限。</span><span class="sxs-lookup"><span data-stu-id="64a6a-139">Before Office 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="64a6a-140">您可通过在域中创建 TXT 记录来证明您拥有该域。</span><span class="sxs-lookup"><span data-stu-id="64a6a-140">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="64a6a-141">TXT 记录不会在您的域中执行任何操作，并且可以在建立您对域的所有权后删除。</span><span class="sxs-lookup"><span data-stu-id="64a6a-141">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="64a6a-142">若要创建 TXT 记录，请按照[在任何 DNS 托管提供商处为 Office 365 创建 DNS 记录](https://go.microsoft.com/fwlink/p/?LinkId=532542)中的过程执行操作。</span><span class="sxs-lookup"><span data-stu-id="64a6a-142">To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="64a6a-143">如果这些步骤对您不适用，您需要查找适用于您的 DNS 注册机构的过程。</span><span class="sxs-lookup"><span data-stu-id="64a6a-143">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="64a6a-p112">通过 nslookup 确认已成功创建 TXT 记录。遵循下面的语法。</span><span class="sxs-lookup"><span data-stu-id="64a6a-p112">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="64a6a-146">您将获得如下所示的输出：</span><span class="sxs-lookup"><span data-stu-id="64a6a-146">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="64a6a-147">验证 Office 365 中的域所有权</span><span class="sxs-lookup"><span data-stu-id="64a6a-147">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="64a6a-p113">在此最后一步，您向 Office 365 验证您拥有公开注册的域。在此步骤之后，Office 365 将开始接受路由到新域名的流量。若要完成域创建和注册过程，请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="64a6a-p113">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="64a6a-151">此命令不会返回任何输出，因此要确认其有效，请运行此命令。</span><span class="sxs-lookup"><span data-stu-id="64a6a-151">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="64a6a-152">这将返回如下所示的内容</span><span class="sxs-lookup"><span data-stu-id="64a6a-152">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="64a6a-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64a6a-153">See also</span></span>

#### 

[<span data-ttu-id="64a6a-154">适用于合作伙伴的帮助</span><span class="sxs-lookup"><span data-stu-id="64a6a-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

