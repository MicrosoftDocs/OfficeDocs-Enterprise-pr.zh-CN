---
title: 查看 Office 365 中目录同步错误
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: 了解如何在 Office 365 管理中心中查看目录同步错误。
ms.openlocfilehash: 62f1135568261eccf0e7e66b78c5aaff966c7281
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539683"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="798d1-103">查看 Office 365 中目录同步错误</span><span class="sxs-lookup"><span data-stu-id="798d1-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="798d1-p101">您可以在 Office 365 管理中心查看目录同步错误。显示用户的对象错误。若要查看使用 PowerShell 错误，请参阅[DirSyncProvisioningErrors 标识对象](https://go.microsoft.com/fwlink/p/?LinkId=798300)。</span><span class="sxs-lookup"><span data-stu-id="798d1-p101">You can view directory synchronization errors in the Office 365 admin center. Only the User object errors are displayed. To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://go.microsoft.com/fwlink/p/?LinkId=798300).</span></span>

<span data-ttu-id="798d1-107">后查看，请参阅[修复 Office 365 的目录同步问题](fix-problems-with-directory-synchronization.md)更正发现的任何问题。</span><span class="sxs-lookup"><span data-stu-id="798d1-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="798d1-108">在管理中心查看目录同步错误</span><span class="sxs-lookup"><span data-stu-id="798d1-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="798d1-109">在管理中心查看任何错误：</span><span class="sxs-lookup"><span data-stu-id="798d1-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="798d1-110">使用您的工作或学校帐户登录 Office 365。</span><span class="sxs-lookup"><span data-stu-id="798d1-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="798d1-111">转到[有关 Office 365 管理中心](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)。</span><span class="sxs-lookup"><span data-stu-id="798d1-111">Go to the [About the Office 365 admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="798d1-112">在**主页**页上，您将看到**目录同步状态**图块。</span><span class="sxs-lookup"><span data-stu-id="798d1-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![目录同步状态平铺在管理中心预览](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="798d1-114">在图块，选择要转到**目录同步状态**页上的**目录同步状态**。</span><span class="sxs-lookup"><span data-stu-id="798d1-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="798d1-115">在页面底部，您可以看到是否有目录同步错误。</span><span class="sxs-lookup"><span data-stu-id="798d1-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![在目录同步状态页上您可以查看是否有目录同步对象错误](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="798d1-117">选择**我们发现 DirSync 对象错误**转到目录同步错误的详细视图。</span><span class="sxs-lookup"><span data-stu-id="798d1-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="798d1-118">您可以还转到**目录同步错误**页上如果您选择上**目录同步状态**图块**我们发现 DirSync 对象错误**。</span><span class="sxs-lookup"><span data-stu-id="798d1-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![目录同步错误页](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="798d1-120">在**目录同步错误**页中，选择任一列出要显示的错误和如何解决此问题的提示信息与详细信息窗格中的错误。</span><span class="sxs-lookup"><span data-stu-id="798d1-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
