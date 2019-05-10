---
title: 使用精益弹出内容减少阅读邮件时使用的内存
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
description: 本文包含有关在 web 上的 Outlook 中改进邮件下载性能的信息。
ms.openlocfilehash: 55cbdec3dc994f3301afaf1bf0a261de446d522a
ms.sourcegitcommit: a35d23929bfbfd956ee853b5e828b36e2978bf36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "33655776"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="b8053-103">使用精益弹出内容减少阅读邮件时使用的内存</span><span class="sxs-lookup"><span data-stu-id="b8053-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="b8053-104">本文包含有关在 web 上的 Outlook 中改进邮件下载性能的信息。</span><span class="sxs-lookup"><span data-stu-id="b8053-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="b8053-105">本文是 Office 365 项目的[网络规划和性能调整](https://aka.ms/tune)的一部分。</span><span class="sxs-lookup"><span data-stu-id="b8053-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="b8053-106">作为 Office 365 全局管理员, 你可以将 web 上的 Outlook 配置为在 Microsoft Edge 或 Internet Explorer 中的特定电子邮件的较小、占用大量内存的版本中提供*精益弹出内容*。</span><span class="sxs-lookup"><span data-stu-id="b8053-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="b8053-107">当为 web 上的 Outlook 配置了精益弹出内容时, 将加载服务器端呈现的组件以优化性能。</span><span class="sxs-lookup"><span data-stu-id="b8053-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="b8053-108">从2018年3月起, 精益弹出内容当前不适用于指定使用权限限制的邮件, 如信息权限管理 (IRM)。</span><span class="sxs-lookup"><span data-stu-id="b8053-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="b8053-109">这些功能将继续在主窗口中运行, 但在精益弹出内容中不可用:</span><span class="sxs-lookup"><span data-stu-id="b8053-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="b8053-110">Outlook 加载项</span><span class="sxs-lookup"><span data-stu-id="b8053-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="b8053-111">Skype for business 状态</span><span class="sxs-lookup"><span data-stu-id="b8053-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="b8053-112">**为 Office 365 组织中的所有用户配置精益弹出内容**</span><span class="sxs-lookup"><span data-stu-id="b8053-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="b8053-113">[使用远程 PowerShell 连接到 Exchange Online](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx )。</span><span class="sxs-lookup"><span data-stu-id="b8053-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="b8053-114">使用 LeanPopoutEnabled 参数运行[set-organizationconfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="b8053-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="b8053-115">例如, 若要为组织中的所有用户启用精益弹出内容, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="b8053-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="b8053-116">若要为组织中的所有用户禁用精益弹出内容, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="b8053-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


