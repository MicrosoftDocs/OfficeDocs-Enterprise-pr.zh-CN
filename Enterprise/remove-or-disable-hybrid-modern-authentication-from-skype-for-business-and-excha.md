---
title: 从 Skype for Business 和 Exchange 删除或禁用混合新式验证
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
description: 如果已启用混合现代身份验证 (HMA) 仅要查找其不适用于您当前的环境，您可以禁用 HMA。本文介绍如何。
ms.openlocfilehash: fff9599641630386183ab9e1a0b8f597f0ba6e5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539775"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="6279a-104">从 Skype for Business 和 Exchange 删除或禁用混合新式验证</span><span class="sxs-lookup"><span data-stu-id="6279a-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="6279a-p102">如果已启用混合现代身份验证 (HMA) 仅要查找其不适用于您当前的环境，您可以禁用 HMA。本文介绍如何。</span><span class="sxs-lookup"><span data-stu-id="6279a-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="6279a-107">谁是本文？</span><span class="sxs-lookup"><span data-stu-id="6279a-107">Who is this article for?</span></span>

<span data-ttu-id="6279a-108">如果您已启用业务联机或本地和/或 Exchange Online 或内部部署中 Skype 的现代身份验证并找到您需要禁用 HMA，这些步骤是为您。</span><span class="sxs-lookup"><span data-stu-id="6279a-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>
  
 <span data-ttu-id="6279a-109">**重要**如果您正在 Skype 业务联机或内部部署，请参阅[Skype 的业务拓扑支持现代身份验证](https://technet.microsoft.com/en-us/library/mt803262.aspx)文章、 具有混合拓扑 HMA，并且需要您在开始之前查看受支持的拓扑。</span><span class="sxs-lookup"><span data-stu-id="6279a-109">**Important** See the ' [Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="6279a-110">如何禁用混合现代身份验证 (Exchange)</span><span class="sxs-lookup"><span data-stu-id="6279a-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="6279a-111">**Exchange 内部部署**： 打开 Exchange Management Shell 并运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="6279a-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following command.</span></span> 
    
1. <span data-ttu-id="6279a-112">Set-organizationconfig-OAuth2ClientProfileEnabled $false</span><span class="sxs-lookup"><span data-stu-id="6279a-112">Set-OrganizationConfig -OAuth2ClientProfileEnabled $false</span></span>
    
2. <span data-ttu-id="6279a-113">Set-authserver-Identity evoSTS-IsDefaultAuthorizationEndpoint $false</span><span class="sxs-lookup"><span data-stu-id="6279a-113">Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false</span></span>
    
2. <span data-ttu-id="6279a-p103">**Exchange Online**： 连接到 Exchange Online 与 Remote PowerShell。运行以下命令以打开您*OAuth2ClientProfileEnabled*标志为 false。</span><span class="sxs-lookup"><span data-stu-id="6279a-p103">**Exchange Online**: Connect to Exchange Online with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false'.</span></span> 
    
1. <span data-ttu-id="6279a-116">Set-organizationconfig-OAuth2ClientProfileEnabled: $false</span><span class="sxs-lookup"><span data-stu-id="6279a-116">Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false</span></span>
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="6279a-117">如何禁用混合现代身份验证 (for Business 的 Skype)</span><span class="sxs-lookup"><span data-stu-id="6279a-117">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="6279a-118">**Skype 业务本地**： 业务命令行管理程序 Skype 中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="6279a-118">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell.</span></span>
    
1. <span data-ttu-id="6279a-119">Set-csoauthconfiguration ClientAuthorizationOAuthServerIdentity""</span><span class="sxs-lookup"><span data-stu-id="6279a-119">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""</span></span>
    
2. <span data-ttu-id="6279a-p104">**Skype for Business Online**： 业务联机使用远程 PowerShell 连接到 Skype。运行以下命令以禁用现代身份验证。</span><span class="sxs-lookup"><span data-stu-id="6279a-p104">**Skype for Business Online**: Connect to Skype for Business Online with Remote PowerShell. Run the following command to disable Modern Authentication.</span></span> 
    
1. <span data-ttu-id="6279a-122">Set-csoauthconfiguration ClientAdalAuthOverride 不允许</span><span class="sxs-lookup"><span data-stu-id="6279a-122">Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed</span></span>
    
<span data-ttu-id="6279a-123">[现代身份验证概述的反向链接](hybrid-modern-auth-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6279a-123">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

