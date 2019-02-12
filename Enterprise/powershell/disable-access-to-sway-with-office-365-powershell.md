---
title: 使用 Office 365 PowerShell 禁止访问 Sway
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 7221a4c9-ae03-4598-81fe-a655c02f40ab
description: 了解从何处下载 ManageSway.ps1 PowerShell 脚本，使用此脚本，可以禁用对 Office 365 组织中的 Sway 的访问。
ms.openlocfilehash: 38f50a483f7bb42ad2d944cf95c49050cf35bfb1
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897085"
---
# <a name="disable-access-to-sway-with-office-365-powershell"></a><span data-ttu-id="dba09-103">使用 Office 365 PowerShell 禁止访问 Sway</span><span class="sxs-lookup"><span data-stu-id="dba09-103">Disable access to Sway with Office 365 PowerShell</span></span>

<span data-ttu-id="dba09-104">**摘要：** 使用 ManageSway.ps1 PowerShell 脚本禁止在 Office 365 组织中访问 Sway。</span><span class="sxs-lookup"><span data-stu-id="dba09-104">**Summary** Use the ManageSway.ps1 PowerShell script to disable access to Sway in your Office 365 organization.</span></span>
  
<span data-ttu-id="dba09-p101">借助 ManageSway.ps1 PowerShell 脚本，用户可以查看和禁用 Office 365 组织中的服务，包括 Sway。此脚本可以自动执行以下主题中描述的过程：</span><span class="sxs-lookup"><span data-stu-id="dba09-p101">The ManageSway.ps1 PowerShell script allows you to view and disable services in your Office 365 organization, including Sway. This script automates the procedures that are described in the following topics:</span></span>
  
- [<span data-ttu-id="dba09-107">使用 Office 365 PowerShell 查看许可证和服务</span><span class="sxs-lookup"><span data-stu-id="dba09-107">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="dba09-108">使用 Office 365 PowerShell 禁止访问服务</span><span class="sxs-lookup"><span data-stu-id="dba09-108">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
<span data-ttu-id="dba09-109">你需要下载与此脚本相关联的两个文件：</span><span class="sxs-lookup"><span data-stu-id="dba09-109">You need to download the two files that are associated with the script:</span></span>
  
- <span data-ttu-id="dba09-110">ManageSway.ps1 脚本（位于 [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)）</span><span class="sxs-lookup"><span data-stu-id="dba09-110">The ManageSway.ps1 script at https://go.microsoft.com/fwlink/p/?LinkId=785070</span></span>
    
- <span data-ttu-id="dba09-111">该脚本的帮助文件（位于 [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)）</span><span class="sxs-lookup"><span data-stu-id="dba09-111">The help file for the script at https://go.microsoft.com/fwlink/p/?LinkId=785072</span></span>
    

