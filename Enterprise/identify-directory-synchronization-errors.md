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
description: 了解如何在 Microsoft 365 管理中心中查看目录同步错误。
ms.openlocfilehash: 8450c2e26c9c9ae194be46d81018a20c91e35f29
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001805"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="f1dfd-103">查看 Office 365 中的目录同步错误</span><span class="sxs-lookup"><span data-stu-id="f1dfd-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="f1dfd-104">您可以在[Microsoft 365 管理中心](https://admin.microsoft.com)中查看目录同步错误。</span><span class="sxs-lookup"><span data-stu-id="f1dfd-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="f1dfd-105">仅显示用户对象错误。</span><span class="sxs-lookup"><span data-stu-id="f1dfd-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="f1dfd-106">若要使用 PowerShell 查看错误, 请参阅[使用 DirSyncProvisioningErrors 标识对象](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)。</span><span class="sxs-lookup"><span data-stu-id="f1dfd-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="f1dfd-107">查看后, 请参阅[解决 Office 365 的目录同步问题](fix-problems-with-directory-synchronization.md)以更正任何已确定的问题。</span><span class="sxs-lookup"><span data-stu-id="f1dfd-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="f1dfd-108">查看管理中心的目录同步错误</span><span class="sxs-lookup"><span data-stu-id="f1dfd-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="f1dfd-109">若要查看管理中心中的任何错误, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="f1dfd-110">使用工作或学校帐户登录 Office 365。</span><span class="sxs-lookup"><span data-stu-id="f1dfd-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="f1dfd-111">转到[有关管理中心](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)的 "关于"。</span><span class="sxs-lookup"><span data-stu-id="f1dfd-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="f1dfd-112">在**主页**上, 您将看到**DirSync 状态**磁贴。</span><span class="sxs-lookup"><span data-stu-id="f1dfd-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![管理员中心预览中的 DirSync 状态磁贴](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="f1dfd-114">在磁贴上, 选择 " **DirSync 状态**" 以转到 "**目录同步状态**" 页。</span><span class="sxs-lookup"><span data-stu-id="f1dfd-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="f1dfd-115">在页面底部, 您可以查看是否存在 DirSync 错误。</span><span class="sxs-lookup"><span data-stu-id="f1dfd-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![在 "目录同步状态" 页上, 您可以查看是否存在目录同步对象错误](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="f1dfd-117">选择**我们发现**了目录同步对象错误, 以转到目录同步错误的详细视图。</span><span class="sxs-lookup"><span data-stu-id="f1dfd-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="f1dfd-118">如果选择在**dirsync 状态**磁贴上**发现了 dirsync 对象错误**, 也可以转到 " **dirsync errors** " 页面。</span><span class="sxs-lookup"><span data-stu-id="f1dfd-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
!["DirSync 错误" 页](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="f1dfd-120">在 " **DirSync errors** " 页面上, 选择列出的任何错误, 以显示详细信息窗格, 其中包含有关错误的信息以及如何修复该错误的提示。</span><span class="sxs-lookup"><span data-stu-id="f1dfd-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
