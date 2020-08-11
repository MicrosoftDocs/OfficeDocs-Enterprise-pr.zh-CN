---
title: 从 Skype for Business 和 Exchange 删除或禁用混合新式验证
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: 本文介绍如何从 Skype for Business 和 Exchange 中删除或禁用混合新式身份验证。
ms.openlocfilehash: 9c3dcb2f4bb8993964707a3f30c699bcea3f0dbb
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606168"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="b96dd-103">从 Skype for Business 和 Exchange 删除或禁用混合新式验证</span><span class="sxs-lookup"><span data-stu-id="b96dd-103">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="b96dd-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="b96dd-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="b96dd-105">如果已启用混合新式身份验证 (HMA) 仅在找不到适合您的当前环境的情况下，您可以禁用 HMA。</span><span class="sxs-lookup"><span data-stu-id="b96dd-105">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="b96dd-106">本文介绍如何操作。</span><span class="sxs-lookup"><span data-stu-id="b96dd-106">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="b96dd-107">本文的目标是什么？</span><span class="sxs-lookup"><span data-stu-id="b96dd-107">Who is this article for?</span></span>

<span data-ttu-id="b96dd-108">如果已在 Skype for Business Online 或内部部署中启用新式验证，以及/或 Exchange Online 或本地，并且发现您需要禁用 HMA，则这些步骤适用于您。</span><span class="sxs-lookup"><span data-stu-id="b96dd-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b96dd-109">如果你在 Skype for Business Online 或内部部署中，请参阅 "[使用新式身份验证支持的 Skype For business 拓扑](https://technet.microsoft.com/library/mt803262.aspx)" 一文具有混合拓扑 HMA，在开始之前，需要查看受支持的拓扑。</span><span class="sxs-lookup"><span data-stu-id="b96dd-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="b96dd-110">如何在 Exchange) 中禁用混合新式身份验证 (</span><span class="sxs-lookup"><span data-stu-id="b96dd-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="b96dd-111">**Exchange 本地**：打开 Exchange 命令行管理程序并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b96dd-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="b96dd-112">**Exchange online**：使用远程 PowerShell[连接到 Exchange online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。</span><span class="sxs-lookup"><span data-stu-id="b96dd-112">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="b96dd-113">运行以下命令，将您的*OAuth2ClientProfileEnabled*标志转换为 "false"：</span><span class="sxs-lookup"><span data-stu-id="b96dd-113">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="b96dd-114">如何禁用 (Skype for business) 的混合新式身份验证</span><span class="sxs-lookup"><span data-stu-id="b96dd-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="b96dd-115">**Skype**for business 本地：在 Skype For Business 命令行管理程序中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="b96dd-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="b96dd-116">**Skype for Business online**：使用远程 PowerShell[连接到 Skype for business online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) 。</span><span class="sxs-lookup"><span data-stu-id="b96dd-116">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="b96dd-117">运行以下命令以禁用新式验证：</span><span class="sxs-lookup"><span data-stu-id="b96dd-117">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="b96dd-118">[链接回新式验证概述](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b96dd-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

