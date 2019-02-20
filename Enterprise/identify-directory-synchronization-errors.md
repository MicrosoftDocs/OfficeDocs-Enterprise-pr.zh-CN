---
title: 查看 Office 365 中的目录同步错误
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: 了解如何在 Office 365 管理中心中查看目录同步错误。
ms.openlocfilehash: 8b7bb16aeddbf1765426c3725cd1f670524ef6d1
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085031"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="68fa1-103">查看 Office 365 中的目录同步错误</span><span class="sxs-lookup"><span data-stu-id="68fa1-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="68fa1-p101">您可以在 Office 365 管理中心中查看目录同步错误。仅显示用户对象错误。若要使用 PowerShell 查看错误, 请参阅[使用 DirSyncProvisioningErrors 标识对象](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)。</span><span class="sxs-lookup"><span data-stu-id="68fa1-p101">You can view directory synchronization errors in the Office 365 admin center. Only the User object errors are displayed. To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="68fa1-107">查看后, 请参阅[解决 Office 365 的目录同步问题](fix-problems-with-directory-synchronization.md)以更正任何已确定的问题。</span><span class="sxs-lookup"><span data-stu-id="68fa1-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="68fa1-108">查看管理中心的目录同步错误</span><span class="sxs-lookup"><span data-stu-id="68fa1-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="68fa1-109">若要查看管理中心中的任何错误, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="68fa1-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="68fa1-110">使用工作或学校帐户登录 Office 365。</span><span class="sxs-lookup"><span data-stu-id="68fa1-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="68fa1-111">请转到[关于 Office 365 管理中心的信息](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)。</span><span class="sxs-lookup"><span data-stu-id="68fa1-111">Go to the [About the Office 365 admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="68fa1-112">在**主页**上, 您将看到**DirSync 状态**磁贴。</span><span class="sxs-lookup"><span data-stu-id="68fa1-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![管理员中心预览中的 DirSync 状态磁贴](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="68fa1-114">在磁贴上, 选择 " **DirSync 状态**" 以转到 "**目录同步状态**" 页。</span><span class="sxs-lookup"><span data-stu-id="68fa1-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="68fa1-115">在页面底部, 您可以查看是否存在 DirSync 错误。</span><span class="sxs-lookup"><span data-stu-id="68fa1-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![在 "目录同步状态" 页上, 您可以查看是否存在目录同步对象错误](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="68fa1-117">选择**我们发现**了目录同步对象错误, 以转到目录同步错误的详细视图。</span><span class="sxs-lookup"><span data-stu-id="68fa1-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="68fa1-118">如果选择在**dirsync 状态**磁贴上**发现了 dirsync 对象错误**, 也可以转到 " **dirsync errors** " 页面。</span><span class="sxs-lookup"><span data-stu-id="68fa1-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
!["DirSync 错误" 页](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="68fa1-120">在 " **DirSync errors** " 页面上, 选择列出的任何错误, 以显示详细信息窗格, 其中包含有关错误的信息以及如何修复该错误的提示。</span><span class="sxs-lookup"><span data-stu-id="68fa1-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
