---
title: Office 365 视频中的租户隔离
ms.author: josephd
author: JoeDavies-MSFT
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
f1.keywords:
- NOCSH
description: 摘要： Office 365 视频中的租户隔离说明。
ms.openlocfilehash: d3d7f71260d74d598a8cc72962c2ab1ea1f2e6c3
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998695"
---
# <a name="tenant-isolation-in-office-365-video"></a><span data-ttu-id="df8b0-103">Office 365 视频中的租户隔离</span><span class="sxs-lookup"><span data-stu-id="df8b0-103">Tenant Isolation in Office 365 Video</span></span>

> [!NOTE]
> <span data-ttu-id="df8b0-104">Office 365 视频将替换为 Microsoft Stream。</span><span class="sxs-lookup"><span data-stu-id="df8b0-104">Office 365 Video will be replaced by Microsoft Stream.</span></span> <span data-ttu-id="df8b0-105">若要详细了解将智能添加到视频协作的新企业视频服务并了解当前 Microsoft 365 视频客户的过渡计划，请参阅[Office 365 视频转换为 Microsoft Stream 概述](https://docs.microsoft.com/stream/migrate-from-office-365)。</span><span class="sxs-lookup"><span data-stu-id="df8b0-105">To learn more about the new enterprise video service that adds intelligence to video collaboration and learn about the transition plans for current Microsoft 365 Video customers, see [Office 365 Video transition to Microsoft Stream overview](https://docs.microsoft.com/stream/migrate-from-office-365).</span></span>

## <a name="introduction"></a><span data-ttu-id="df8b0-106">简介</span><span class="sxs-lookup"><span data-stu-id="df8b0-106">Introduction</span></span>

<span data-ttu-id="df8b0-107">Azure 存储用于存储多个 Office 365 服务（包括 Office 365 视频和 Sway）的数据。</span><span class="sxs-lookup"><span data-stu-id="df8b0-107">Azure Storage is used to store data for multiple Office 365 services, including Office 365 Video and Sway.</span></span> <span data-ttu-id="df8b0-108">Azure 存储包括 Blob 存储，它是一个用于存储非结构化数据的高可缩放、基于 REST 的云对象存储。</span><span class="sxs-lookup"><span data-stu-id="df8b0-108">Azure Storage includes Blob storage, which is a highly-scalable, REST-based, cloud object store that is used for storing unstructured data.</span></span> <span data-ttu-id="df8b0-109">Azure 存储使用简单的访问控制模型;每个 Azure 订阅都可以创建一个或多个存储帐户。</span><span class="sxs-lookup"><span data-stu-id="df8b0-109">Azure Storage uses a simple access control model; each Azure subscription can create one or more Storage Accounts.</span></span> <span data-ttu-id="df8b0-110">每个存储帐户都有一个密钥，用于控制对该存储帐户中的所有数据的访问。</span><span class="sxs-lookup"><span data-stu-id="df8b0-110">Each Storage Account has a single secret key that is used to control access to all data in that Storage Account.</span></span> <span data-ttu-id="df8b0-111">这支持存储与应用程序相关联的典型方案，这些应用程序可以完全控制其关联的数据;例如，Sway 将内容存储在 Azure 存储中。</span><span class="sxs-lookup"><span data-stu-id="df8b0-111">This supports the typical scenario where storage is associated with applications and those applications have full control over their associated data; for example, Sway storing content in Azure Storage.</span></span> <span data-ttu-id="df8b0-112">Sway 的所有客户内容都存储在共享的 Azure 存储帐户中。</span><span class="sxs-lookup"><span data-stu-id="df8b0-112">All customer content for Sway is stored in shared Azure storage accounts.</span></span> <span data-ttu-id="df8b0-113">每个用户的内容都位于 Azure 存储中的 blob 的单独目录树中。</span><span class="sxs-lookup"><span data-stu-id="df8b0-113">Each user's content is in a separate directory tree of blobs in Azure storage.</span></span>

<span data-ttu-id="df8b0-114">管理对客户环境的访问（例如，Azure 门户、SMAPI 等）的系统在由 Microsoft 运营的 Azure 应用程序中隔离。</span><span class="sxs-lookup"><span data-stu-id="df8b0-114">The systems managing access to customer environments (e.g., the Azure Portal, SMAPI, etc.) are isolated within an Azure application operated by Microsoft.</span></span> <span data-ttu-id="df8b0-115">这将在逻辑上将客户访问基础结构与客户应用程序和存储层分开。</span><span class="sxs-lookup"><span data-stu-id="df8b0-115">This logically separates the customer access infrastructure from the customer applications and storage layer.</span></span>

## <a name="tenant-isolation-in-office-365-video"></a><span data-ttu-id="df8b0-116">Office 365 视频中的租户隔离</span><span class="sxs-lookup"><span data-stu-id="df8b0-116">Tenant Isolation in Office 365 Video</span></span>

<span data-ttu-id="df8b0-117">[Office 365 视频](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)是一个企业门户，它为组织提供了用于发布、共享和发现视频内容的高度安全的组织范围的目标。</span><span class="sxs-lookup"><span data-stu-id="df8b0-117">[Office 365 Video](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6) is an enterprise portal that provides organizations with a highly secure, organization-wide destination for posting, sharing, and discovering video content.</span></span> <span data-ttu-id="df8b0-118">在 Office 365 视频中，每个租户的视频在所有位置中保持独立和加密，并且仅对对组织视频具有访问权限和权限的经过身份验证的用户可用。</span><span class="sxs-lookup"><span data-stu-id="df8b0-118">In Office 365 Video, each tenant's videos are kept isolated and encrypted in all locations, and are only available to authenticated users that have access and permissions to the organization's videos.</span></span> <span data-ttu-id="df8b0-119">Office 365 视频使用多种技术来实现此目的：</span><span class="sxs-lookup"><span data-stu-id="df8b0-119">Office 365 Video uses a combination of technologies to accomplish this:</span></span>

- <span data-ttu-id="df8b0-120">SharePoint Online 用于存储视频文件和元数据（视频标题、说明等）。</span><span class="sxs-lookup"><span data-stu-id="df8b0-120">SharePoint Online is used for storing the video file and metadata (video title, description, etc.).</span></span> <span data-ttu-id="df8b0-121">它还提供了安全性和合规性层（包括身份验证）和搜索功能。</span><span class="sxs-lookup"><span data-stu-id="df8b0-121">It also provides the security and compliance layer (including authentication), and search features.</span></span>
- <span data-ttu-id="df8b0-122">Azure 媒体服务提供了转码、自适应流、安全传递（使用 AES 加密）和缩略图功能。</span><span class="sxs-lookup"><span data-stu-id="df8b0-122">Azure Media Services provides transcoding, adaptive streaming, secure delivery (using AES encryption), and thumbnail features.</span></span>

<span data-ttu-id="df8b0-123">[Azure 媒体服务](https://azure.microsoft.com/services/media-services/)是一种平台即服务，用于在云中启用端到端媒体工作流。</span><span class="sxs-lookup"><span data-stu-id="df8b0-123">[Azure Media Services](https://azure.microsoft.com/services/media-services/) is a platform-as-a-service offering for enabling end-to-end media workflows in the cloud.</span></span> <span data-ttu-id="df8b0-124">该平台提供了 REST API，用于上载、编码、加密（使用 PlayReady）以及通过全球的 Azure 数据中心传递媒体。</span><span class="sxs-lookup"><span data-stu-id="df8b0-124">The platform provides a REST API for uploading, encoding, encrypting (with PlayReady), and delivery of media through Azure datacenters around the world.</span></span>

<span data-ttu-id="df8b0-125">所有上载的 Office 365 视频通过 HTTPS 进行。</span><span class="sxs-lookup"><span data-stu-id="df8b0-125">All uploads for Office 365 Video occur via HTTPS.</span></span> <span data-ttu-id="df8b0-126">在上载视频文件时，会将其存储在 SharePoint Online 中，并将该文件的副本通过加密通道发送到 Azure 媒体服务。</span><span class="sxs-lookup"><span data-stu-id="df8b0-126">When a video file is uploaded, it is stored in SharePoint Online, and a copy of the file is sent via an encrypted channel to Azure Media Services.</span></span> <span data-ttu-id="df8b0-127">Azure 媒体服务将视频 transcodes 为多种格式，这些格式针对查看体验（例如，移动、低带宽、高带宽等）进行了优化。</span><span class="sxs-lookup"><span data-stu-id="df8b0-127">Azure Media Services transcodes the video into multiple formats that are optimized for viewing experience (e.g., mobile, low-bandwidth, high-bandwidth, etc.).</span></span> <span data-ttu-id="df8b0-128">这些文件以及上载过程中获取的原始文件都存储在 Azure Blob 存储中。</span><span class="sxs-lookup"><span data-stu-id="df8b0-128">These files, along with the original file acquired during upload, are stored in Azure Blob storage.</span></span> <span data-ttu-id="df8b0-129">这些文件128使用每个 MPEG 通用加密打包算法（或更早的 PlayReady 版本）进行播放，并在存储在 Azure Blob 存储中之前使用 AES 256 存储加密进行加密，从而对这些文件进行加密。</span><span class="sxs-lookup"><span data-stu-id="df8b0-129">The files are encrypted using AES 128 per the MPEG Common Encryption packaging algorithm (or an earlier PlayReady version) for playback, and encrypted using AES 256 storage encryption before being stored in Azure Blob storage.</span></span> <span data-ttu-id="df8b0-130">（使用 Azure 媒体服务客户端 SDK，客户可以控制使用哪些加密。</span><span class="sxs-lookup"><span data-stu-id="df8b0-130">(Using the Azure Media Services Client SDK, customers can control which encryption is used.</span></span> <span data-ttu-id="df8b0-131">例如，在上载 it Azure Blob 存储之前，客户可以将 Azure 媒体服务存储加密（AES 256）应用到高价值媒体资产。</span><span class="sxs-lookup"><span data-stu-id="df8b0-131">For example, a customer could apply Azure Media Services storage encryption (AES 256) to a high-value media asset before uploading it Azure Blob storage.)</span></span>

<span data-ttu-id="df8b0-132">Azure 媒体服务还会生成视频的缩略图，它会通过加密通道将其连同缩略图元数据一起传输到 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="df8b0-132">Azure Media Services also generates a thumbnail for the video, which it transmits along with thumbnail metadata to SharePoint Online via an encrypted channel.</span></span>
