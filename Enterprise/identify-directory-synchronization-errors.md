---
title: 在 Microsoft 365 中查看目录同步错误
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
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
description: 了解如何在 Microsoft 365 管理中心中查看目录同步错误和可能的修补程序。
ms.openlocfilehash: 344cc71d192e6a73826c66c8bcbf8569d10e45d8
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605704"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a><span data-ttu-id="277fa-103">在 Microsoft 365 中查看目录同步错误</span><span class="sxs-lookup"><span data-stu-id="277fa-103">View directory synchronization errors in Microsoft 365</span></span>

<span data-ttu-id="277fa-104">您可以在 Microsoft 365 管理中心中查看目录同步错误。</span><span class="sxs-lookup"><span data-stu-id="277fa-104">You can view directory synchronization errors in the Microsoft 365 admin center.</span></span> <span data-ttu-id="277fa-105">仅显示用户对象错误。</span><span class="sxs-lookup"><span data-stu-id="277fa-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="277fa-106">若要查看 PowerShell 中的错误，请参阅[使用 DirSyncProvisioningErrors 标识对象](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)。</span><span class="sxs-lookup"><span data-stu-id="277fa-106">To view errors with PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a><span data-ttu-id="277fa-107">在 Microsoft 365 管理中心中查看目录同步错误</span><span class="sxs-lookup"><span data-stu-id="277fa-107">View directory synchronization errors in the Microsoft 365 admin center</span></span>

<span data-ttu-id="277fa-108">若要查看 Microsoft 365 管理中心中的任何错误，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="277fa-108">To view any errors in the Microsoft 365 admin center:</span></span>
  
1. <span data-ttu-id="277fa-109">使用全局管理员帐户登录到[Microsoft 365 管理中心](https://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="277fa-109">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) with a global administrator account.</span></span> 
    
2. <span data-ttu-id="277fa-110">在**主页**上，您将看到 "**用户管理**卡"。</span><span class="sxs-lookup"><span data-stu-id="277fa-110">On the **Home** page, you'll see the **User management** card.</span></span> 
    
    ![Microsoft 365 管理中心中的用户管理卡](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. <span data-ttu-id="277fa-112">在卡片上，选择 " **AZURE AD Connect** " 下的 "**同步错误**" 以查看 "**目录同步错误**" 页上的错误。</span><span class="sxs-lookup"><span data-stu-id="277fa-112">On the card, choose **Sync errors** under **Azure AD Connect** to see the errors on the **Directory sync errors** page.</span></span>   
    
    !["目录同步错误" 页的示例](media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. <span data-ttu-id="277fa-114">选择任何错误以显示详细信息窗格，其中包含有关错误的信息以及如何修复该错误的提示。</span><span class="sxs-lookup"><span data-stu-id="277fa-114">Choose any of the errors to display the details pane with information about the error and tips on how to fix it.</span></span>

   ![目录同步错误的详细信息示例](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
<span data-ttu-id="277fa-116">查看后，请参阅[解决 Microsoft 365 的目录同步问题](fix-problems-with-directory-synchronization.md)以更正任何已确定的问题。</span><span class="sxs-lookup"><span data-stu-id="277fa-116">After viewing, see [fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>

