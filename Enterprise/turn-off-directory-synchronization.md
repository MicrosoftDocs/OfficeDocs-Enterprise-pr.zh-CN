---
title: 关闭 Microsoft 365 的目录同步
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
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: 在本文中，查找有关使用 PowerShell 关闭 Microsoft 365 的目录同步的信息。
ms.openlocfilehash: 815d20ff6a0697f1533e44305e20e61a9282312b
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "46603644"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>关闭 Microsoft 365 的目录同步
您可以使用 PowerShell 关闭目录同步。 但是，不建议您将目录同步作为故障排除步骤关闭。 如果您需要有关对目录同步进行故障排除的帮助，请参阅[解决 Microsoft 365 文章的目录同步问题](fix-problems-with-directory-synchronization.md)。 
  
如果需要，[请联系](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)业务产品支持人员。
  
## <a name="turn-off-directory-synchronization"></a>关闭目录同步  
若要关闭目录同步，请执行以下操作：
  
1. 首先，安装所需的软件并连接到 Microsoft 365 订阅。 有关说明，请参阅[连接到适用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。
    
2. 使用[MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)禁用目录同步： 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>如果使用此命令，则必须等待72小时，然后才能重新打开目录同步。
>
 
