---
title: 查看 Office 365 中的目录同步错误
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
ms.openlocfilehash: b1cda68590131967ea2fe91506c8e71769f4c32b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067518"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>查看 Office 365 中的目录同步错误

您可以在[Microsoft 365 管理中心](https://admin.microsoft.com)中查看目录同步错误。 仅显示用户对象错误。 若要使用 PowerShell 查看错误, 请参阅[使用 DirSyncProvisioningErrors 标识对象](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)。

查看后, 请参阅[解决 Office 365 的目录同步问题](fix-problems-with-directory-synchronization.md)以更正任何已确定的问题。
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>查看管理中心的目录同步错误

若要查看管理中心中的任何错误, 请执行以下操作:
  
1. 使用工作或学校帐户登录 Office 365。 
    
2. 转到[有关管理中心](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)的 "关于"。
    
3. 在**主页**上, 您将看到**DirSync 状态**磁贴。 
    
    ![管理员中心预览中的 DirSync 状态磁贴](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. 在磁贴上, 选择 " **DirSync 状态**" 以转到 "**目录同步状态**" 页。 
    
    在页面底部, 您可以查看是否存在 DirSync 错误。
    
    ![在 "目录同步状态" 页上, 您可以查看是否存在目录同步对象错误](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    选择**我们发现**了目录同步对象错误, 以转到目录同步错误的详细视图。 
    
    > [!NOTE]
    > 如果选择在**dirsync 状态**磁贴上**发现了 dirsync 对象错误**, 也可以转到 " **dirsync errors** " 页面。 
  
!["DirSync 错误" 页](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. 在 " **DirSync errors** " 页面上, 选择列出的任何错误, 以显示详细信息窗格, 其中包含有关错误的信息以及如何修复该错误的提示。 
