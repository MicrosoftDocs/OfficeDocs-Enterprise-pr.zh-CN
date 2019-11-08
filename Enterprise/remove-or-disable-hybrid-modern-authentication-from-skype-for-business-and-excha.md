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
description: 如果您已启用混合新式身份验证（HMA），则可以禁用 HMA。 本文介绍如何操作。
ms.openlocfilehash: 9f1236775f60fdb37ab12cd7cfb7eabd9763466d
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031597"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="a7e5f-104">从 Skype for Business 和 Exchange 删除或禁用混合新式验证</span><span class="sxs-lookup"><span data-stu-id="a7e5f-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="a7e5f-105">如果您已启用混合新式身份验证（HMA），则可以禁用 HMA。</span><span class="sxs-lookup"><span data-stu-id="a7e5f-105">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="a7e5f-106">本文介绍如何操作。</span><span class="sxs-lookup"><span data-stu-id="a7e5f-106">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="a7e5f-107">本文的目标是什么？</span><span class="sxs-lookup"><span data-stu-id="a7e5f-107">Who is this article for?</span></span>

<span data-ttu-id="a7e5f-108">如果已在 Skype for Business Online 或内部部署中启用新式验证，以及/或 Exchange Online 或本地，并且发现您需要禁用 HMA，则这些步骤适用于您。</span><span class="sxs-lookup"><span data-stu-id="a7e5f-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a7e5f-109">如果你在 Skype for Business Online 或内部部署中，请参阅 "[使用新式身份验证支持的 Skype For business 拓扑](https://technet.microsoft.com/library/mt803262.aspx)" 一文具有混合拓扑 HMA，在开始之前，需要查看受支持的拓扑。</span><span class="sxs-lookup"><span data-stu-id="a7e5f-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="a7e5f-110">如何禁用混合新式身份验证（Exchange）</span><span class="sxs-lookup"><span data-stu-id="a7e5f-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="a7e5f-111">**Exchange 本地**：打开 Exchange 命令行管理程序并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a7e5f-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="a7e5f-112">**Exchange online**：使用远程 PowerShell[连接到 Exchange online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) 。</span><span class="sxs-lookup"><span data-stu-id="a7e5f-112">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="a7e5f-113">运行以下命令，将您的*OAuth2ClientProfileEnabled*标志转换为 "false"：</span><span class="sxs-lookup"><span data-stu-id="a7e5f-113">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="a7e5f-114">如何禁用混合新式身份验证（Skype for Business）</span><span class="sxs-lookup"><span data-stu-id="a7e5f-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="a7e5f-115">**Skype**for business 本地：在 Skype For Business 命令行管理程序中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a7e5f-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="a7e5f-116">**Skype for Business online**：使用远程 PowerShell[连接到 Skype for business online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) 。</span><span class="sxs-lookup"><span data-stu-id="a7e5f-116">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="a7e5f-117">运行以下命令以禁用新式验证：</span><span class="sxs-lookup"><span data-stu-id="a7e5f-117">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="a7e5f-118">[链接回新式验证概述](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a7e5f-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

