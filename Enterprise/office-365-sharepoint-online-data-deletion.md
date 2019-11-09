---
title: Office 365 SharePoint Online 数据删除
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
description: 对 SharePoint Online 中的数据删除的说明。
ms.openlocfilehash: 94b70d34cb05f98dfa560761dec87a919720dca9
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078151"
---
# <a name="sharepoint-online-data-deletion-in-office-365"></a><span data-ttu-id="b6c9b-103">Office 365 中的 SharePoint Online 数据删除</span><span class="sxs-lookup"><span data-stu-id="b6c9b-103">SharePoint Online Data Deletion in Office 365</span></span>

<span data-ttu-id="b6c9b-104">SharePoint Online 将对象存储为应用程序数据库中的抽象代码。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-104">SharePoint Online stores objects as abstracted code within application databases.</span></span> <span data-ttu-id="b6c9b-105">当用户将文件上传到 SharePoint Online 时，会反汇编该文件并将其转换为应用程序代码，并将其存储在多个数据库的多个表中。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-105">When a user uploads a file to SharePoint Online, that file is disassembled and translated into application code and stored in multiple tables across multiple databases.</span></span> <span data-ttu-id="b6c9b-106">在 SharePoint Online 中，客户上传的所有内容都被分成多个块，并进行了加密（可能包含多个 AES 256 位密钥），并分布在整个数据中心中。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-106">In SharePoint Online, all content that a customer uploads is broken into chunks, encrypted (potentially with multiple AES 256-bit keys), and distributed across the datacenter.</span></span> <span data-ttu-id="b6c9b-107">有关分块和加密过程的具体详细信息，请参阅[Microsoft 云中的加密](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview)。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-107">For specific details about the chunking and encryption process, see [Encryption in the Microsoft Cloud](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview).</span></span> 

<span data-ttu-id="b6c9b-108">在 SharePoint Online 中，项目会从从其原始位置删除时起的93天保留一段时间。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-108">In SharePoint Online, items are retained for 93 days from the time you delete them from their original location.</span></span> <span data-ttu-id="b6c9b-109">它们将在整个时间内保持在网站回收站中，除非有人将其从那里删除或清空回收站。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-109">They stay in the site Recycle Bin the entire time, unless someone deletes them from there or empties that Recycle Bin.</span></span> <span data-ttu-id="b6c9b-110">在这种情况下，这些项将转到网站集的回收站，这些项将在剩余的93天内保留。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-110">In that case, the items go to the site collection Recycle Bin, where they stay for the remainder of the 93 days.</span></span> <span data-ttu-id="b6c9b-111">有关还原已删除项目的信息，请参阅[在 SharePoint 网站的回收站中还原项目](https://support.office.com/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
)和[从网站集回收站还原已删除的项目](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b)。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-111">For info about restoring deleted items, see [Restore items in the Recycle Bin of a SharePoint site](https://support.office.com/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
) and [Restore deleted items from the site collection recycle bin](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b).</span></span> <span data-ttu-id="b6c9b-112">无法在 SharePoint Online 中配置回收站保留时间。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-112">The Recycle Bin retention time is not configurable in SharePoint Online.</span></span>

<span data-ttu-id="b6c9b-113">删除网站集时，还会删除集合中的网站层次结构，以及其中的所有内容：</span><span class="sxs-lookup"><span data-stu-id="b6c9b-113">When you delete a site collection, you're also deleting the hierarchy of sites in the collection, and all content within them:</span></span>

- <span data-ttu-id="b6c9b-114">文档和文档库</span><span class="sxs-lookup"><span data-stu-id="b6c9b-114">Documents and document libraries</span></span>
- <span data-ttu-id="b6c9b-115">列表和列表数据</span><span class="sxs-lookup"><span data-stu-id="b6c9b-115">Lists and list data</span></span>
- <span data-ttu-id="b6c9b-116">网站配置设置</span><span class="sxs-lookup"><span data-stu-id="b6c9b-116">Site configuration settings</span></span>
- <span data-ttu-id="b6c9b-117">与网站或其子网站相关的角色和安全信息</span><span class="sxs-lookup"><span data-stu-id="b6c9b-117">Role and security information that is related to the site or its subsites</span></span>
- <span data-ttu-id="b6c9b-118">顶级网站的子网站、其内容和用户信息</span><span class="sxs-lookup"><span data-stu-id="b6c9b-118">Subsites of the top-level website, their contents, and user information</span></span>

<span data-ttu-id="b6c9b-119">如果意外删除了网站集，则可以使用 SharePoint 管理中心通过全局或 SharePoint 管理来还原网站集。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-119">If you accidentally delete a site collection, it can be restored by a global or SharePoint admin using the SharePoint admin center.</span></span> 

<span data-ttu-id="b6c9b-120">当用户清除网站集回收站中的已删除项目、保留和备份期间过期时，或者管理员使用[remove-spodeletedsite cmdlet](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps)永久删除网站集时，将发生硬删除。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-120">Hard deletion occurs when a user purges deleted items from the site collection Recycle Bin, when the retention and backup periods expire, or when an administrator permanently deletes a site collection using the [Remove-SPODeletedSite cmdlet](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps).</span></span> <span data-ttu-id="b6c9b-121">当用户硬删除（永久删除或清除） SharePoint Online 中的内容时，已删除的区块的所有加密密钥也将被删除。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-121">When a user hard deletes (permanently deletes, or purges) content from SharePoint Online, all encryption keys for the deleted chunks are also deleted.</span></span> <span data-ttu-id="b6c9b-122">以前存储已删除的区块的磁盘上的块被标记为未使用，可供重复使用。</span><span class="sxs-lookup"><span data-stu-id="b6c9b-122">The blocks on the disks that previously stored the deleted chunks are marked as unused and available for re-use.</span></span>
