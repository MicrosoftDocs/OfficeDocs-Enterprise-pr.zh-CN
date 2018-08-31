---
title: 使用精益 popouts 减少阅读邮件时使用的内存
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: 本文包含提高在 web 上的 Outlook 中的消息下载性能的信息。
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539609"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="17925-103">使用精益 popouts 减少阅读邮件时使用的内存</span><span class="sxs-lookup"><span data-stu-id="17925-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="17925-p101">本文包含提高在 web 上的 Outlook 中的消息下载性能的信息。本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)项目的一部分。</span><span class="sxs-lookup"><span data-stu-id="17925-p101">This article contains information for improving message download performance in Outlook on the web. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="17925-p102">作为 Office 365 全局管理员，您可以配置 web 上的 Outlook 以提供*精益 popouts* ，较小，减少占用大量内存的版本的 Microsoft 边缘或 Internet Explorer 中特定电子邮件。为 web 上的 Outlook 配置精益 popouts 时, 服务器端呈现组件加载的优化性能。</span><span class="sxs-lookup"><span data-stu-id="17925-p102">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer. When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="17925-108">从年 3 月 2018年精益 popouts 不当前可用于指定使用权限限制，如信息权限管理 (IRM) 的邮件。</span><span class="sxs-lookup"><span data-stu-id="17925-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="17925-109">这些功能将继续在主窗口中工作，但在精益 popouts 中不可用：</span><span class="sxs-lookup"><span data-stu-id="17925-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="17925-110">Outlook 加载项</span><span class="sxs-lookup"><span data-stu-id="17925-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="17925-111">Skype 业务状态</span><span class="sxs-lookup"><span data-stu-id="17925-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="17925-112">**若要配置的 Office 365 组织内的所有用户的精益 popouts**</span><span class="sxs-lookup"><span data-stu-id="17925-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="17925-113">[连接到 Exchange Online 使用远程 PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )。</span><span class="sxs-lookup"><span data-stu-id="17925-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="17925-114">如下所示使用 LeanPopoutEnabled 参数运行[Set-organizationconfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet:</span><span class="sxs-lookup"><span data-stu-id="17925-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    <span data-ttu-id="17925-115">例如，若要启用精益 popouts 您的组织中的所有用户：</span><span class="sxs-lookup"><span data-stu-id="17925-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    <span data-ttu-id="17925-116">若要禁用精益 popouts 您的组织中的所有用户：</span><span class="sxs-lookup"><span data-stu-id="17925-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


