---
title: 将域添加到具有 Windows PowerShell 的客户租户中，以用于 "联盟" 合作伙伴
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 摘要：使用适用于 Microsoft 365 的 PowerShell 将备用域名添加到现有客户租户。
ms.openlocfilehash: 8b38caf72db57d5e80f0483062adb3bd2529672b
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606478"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>使用 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴将域添加到客户端租赁

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

您可以使用 Microsoft 365 管理中心，创建新域并将其与使用 microsoft 365 的 PowerShell 与客户的租户相关联。
  
委派访问权限 (DAP) 合作伙伴是联合和云解决方案提供商 (CSP) 合作伙伴。 他们通常是面向其他公司的网络或电信提供商。 他们将 Microsoft 365 订阅捆绑到其客户的服务产品中。 在销售 Microsoft 365 订阅时，会自动为他们代表 (AOBO) 权限授予对 customer 租赁的管理权限，以便他们可以管理和报告客户租赁。
## <a name="what-do-you-need-to-know-before-you-begin"></a>在开始之前，您需要知道什么？

本主题中的过程要求连接到[使用 PowerShell 的 Microsoft 365 连接](connect-to-office-365-powershell.md)。
  
您也需要您的合作伙伴租户管理员凭据。
  
您也需要以下信息：
  
- 您需要客户所需的完全限定的域名 (FQDN)。
    
- 您需要客户的 **TenantId** 。
    
- FQDN 必须在 Internet 域名服务 (DNS) 注册机构（如 GoDaddy）中注册。有关如何公开注册域名的详细信息，请参阅[如何购买域名](https://go.microsoft.com/fwlink/p/?LinkId=532541)。
    
- 您需要了解如何为您的 DNS 注册机构的注册 DNS 区域添加 TXT 记录。 有关如何添加 TXT 记录的详细信息，请参阅[添加 DNS 记录以连接到您的域](https://go.microsoft.com/fwlink/p/?LinkId=532542)。 如果这些步骤对您不适用，您需要查找适用于您的 DNS 注册机构的过程。
    
## <a name="create-domains"></a>创建域

 您的客户可能会要求您创建与其租赁关联的其他域，因为他们不想让默认的<domain>.onmicrosoft.com域成为向全世界展示其公司标识的主要域。此步骤将引导您创建与您的客户租赁相关联的新域。
  
> [!NOTE]
> 若要执行某些操作，必须将您登录时使用的合作伙伴管理员帐户设置为 "**完全管理**"，以便在 Microsoft 365 管理中心的 "管理员" 帐户详细信息中，"为**您支持的公司分配管理访问权限**" 设置为 "完全管理"。 有关管理合作伙伴管理员角色的详细信息，请参阅[合作伙伴：提供委派管理](https://go.microsoft.com/fwlink/p/?LinkId=532435)。 
  
### <a name="create-the-domain-in-azure-active-directory"></a>在 Azure Active Directory 中创建域

此命令在 Azure Active Directory 中创建域，但不会将其与公开注册的域相关联。 这是因为您证明您拥有公开注册的域到 Microsoft Microsoft Microsoft Microsoft Microsoft Microsoft 365 for 企业。
  
```powershell
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
>PowerShell Core 不支持用于 Windows PowerShell 模块和 cmdlet 的其名称中包含 **Msol** 的 Microsoft Azure Active Directory 模块。 若要继续使用这些 cmdlet，必须从 Windows PowerShell 运行它们。
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>获取 DNS TXT 验证记录的数据

 Microsoft 365 将生成您需要放入 DNS TXT 验证记录中的特定数据。 要获取数据，请运行以下命令。
  
```powershell
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

你将获得如下所示的输出：
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> 你将需要此文本以在公开注册的 DNS 区域中创建 TXT 记录。 请确保将其复制并保存。 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>在公开注册的 DNS 区域中添加 TXT 记录

在 Microsoft 365 开始接受定向到公开注册域名的流量之前，必须证明你拥有此域的管理员权限并拥有该域的管理员权限。 您可通过在域中创建 TXT 记录来证明您拥有该域。 TXT 记录不会在您的域中执行任何操作，并且可以在建立您对域的所有权后删除。 若要创建 TXT 记录，请按照[添加 DNS 记录](https://go.microsoft.com/fwlink/p/?LinkId=532542)中的过程连接您的域。 如果这些步骤对您不适用，您需要查找适用于您的 DNS 注册机构的过程。
  
通过 nslookup 确认已成功创建 TXT 记录。遵循下面的语法。
  
```console
nslookup -type=TXT <FQDN of registered domain>
```

您将获得如下所示的输出：
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-microsoft-365"></a>验证 Microsoft 365 中的域所有权

在此最后一步中，您将向 Microsoft 365 验证你拥有公开注册的域。 完成此步骤后，Microsoft 365 将开始接受路由到新域名的流量。 若要完成域创建和注册过程，请运行此命令。 
  
```powershell
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

此命令不会返回任何输出，因此要确认其有效，请运行此命令。
  
```powershell
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

这将返回如下所示的内容

```console
Name                   Status      Authentication
--------------------   ---------   --------------
FQDN of new domain     Verified    Managed
```

   
## <a name="see-also"></a>另请参阅

#### 

[适用于合作伙伴的帮助](https://go.microsoft.com/fwlink/p/?LinkID=533477)

