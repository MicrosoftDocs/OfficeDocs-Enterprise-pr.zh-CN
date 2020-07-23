---
title: 使用 PowerShell 管理 Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 932d57c0-1520-4f0f-8ec9-9966d646480f
description: 摘要：了解如何使用 PowerShell 管理 Microsoft 365 用户和许可证、Skype for Business Online、SharePoint Online、Exchange Online 和安全 & 合规性中心。
ms.openlocfilehash: 741ec15a78db9393e11ba6d06720457e20741581
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230508"
---
# <a name="manage-microsoft-365-with-powershell"></a><span data-ttu-id="be01b-103">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="be01b-103">Manage Microsoft 365 with PowerShell</span></span>

<span data-ttu-id="be01b-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="be01b-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="be01b-105">PowerShell for Microsoft 365 是一种功能强大的管理工具，可补充 Microsoft 365 管理中心。</span><span class="sxs-lookup"><span data-stu-id="be01b-105">PowerShell for Microsoft 365 is a powerful management tool that complements the Microsoft 365 admin center.</span></span> <span data-ttu-id="be01b-106">例如，您可以使用 PowerShell 自动化更快地管理多个用户帐户和许可证并创建报告。</span><span class="sxs-lookup"><span data-stu-id="be01b-106">For example, you can use PowerShell automation to more quickly manage multiple user accounts and licenses and create reports.</span></span> <span data-ttu-id="be01b-107">了解如何使用适用于 Microsoft 365 用户和许可证、Skype for Business Online、SharePoint Online、Exchange Online 和安全 & 合规性中心的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="be01b-107">Learn how to use PowerShell for Microsoft 365 users and licenses, Skype for Business Online, SharePoint Online, Exchange Online, and the Security & Compliance Center.</span></span>
  
<span data-ttu-id="be01b-108">根据您的需求选择主题：</span><span class="sxs-lookup"><span data-stu-id="be01b-108">Select the topic based on your needs:</span></span>
  
- [<span data-ttu-id="be01b-109">入门</span><span class="sxs-lookup"><span data-stu-id="be01b-109">Get started</span></span>](getting-started-with-office-365-powershell.md)

    <span data-ttu-id="be01b-110">如果你不熟悉适用于 Microsoft 365 的 PowerShell，并希望安装 Microsoft 365 模块并连接到 Microsoft 365 订阅，请从这里开始。</span><span class="sxs-lookup"><span data-stu-id="be01b-110">Start here if you are not familiar with PowerShell for Microsoft 365 and want to install the Microsoft 365 modules and connect to your Microsoft 365 subscription.</span></span>

- [<span data-ttu-id="be01b-111">用户帐户、许可证和组</span><span class="sxs-lookup"><span data-stu-id="be01b-111">User accounts, licenses, and groups</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)

    <span data-ttu-id="be01b-112">如果已安装 Microsoft 365 模块，并且想要了解有关使用自动化命令来管理用户帐户、许可证和组的详细信息，请从这里开始。</span><span class="sxs-lookup"><span data-stu-id="be01b-112">Start here if you have installed the Microsoft 365 modules and want to learn more about using automation commands to manage user accounts, licenses, and groups.</span></span>

- [<span data-ttu-id="be01b-113">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="be01b-113">SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-sharepoint-online-with-office-365-powershell)

    <span data-ttu-id="be01b-114">如果已安装 Microsoft 365 模块，并且想要使用自动化命令来管理 SharePoint Online，请从这里开始。</span><span class="sxs-lookup"><span data-stu-id="be01b-114">Start here if you have installed the Microsoft 365 modules and want to use automation commands to perform management of SharePoint Online.</span></span>

- [<span data-ttu-id="be01b-115">Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="be01b-115">Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)

    <span data-ttu-id="be01b-116">若要使用自动化命令来管理 Exchange Online，请从本主题入手。</span><span class="sxs-lookup"><span data-stu-id="be01b-116">Start here if you want to use automation commands to manage Exchange Online.</span></span>

- [<span data-ttu-id="be01b-117">电子邮件迁移</span><span class="sxs-lookup"><span data-stu-id="be01b-117">Email migration</span></span>](use-powershell-for-email-migration-to-office-365.md)

    <span data-ttu-id="be01b-118">如果您已安装 PowerShell 365 模块并希望从现有系统迁移您的电子邮件，请从这里开始。</span><span class="sxs-lookup"><span data-stu-id="be01b-118">Start here if you have installed the PowerShell 365 modules and want to migrate your email from existing systems.</span></span>

- [<span data-ttu-id="be01b-119">安全与合规中心</span><span class="sxs-lookup"><span data-stu-id="be01b-119">Security & Compliance Center</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell)

    <span data-ttu-id="be01b-120">若要使用自动化命令来管理安全与合规中心，请从本主题入手。</span><span class="sxs-lookup"><span data-stu-id="be01b-120">Start here if you want to use automation commands to manage the Security & Compliance Center.</span></span>

- [<span data-ttu-id="be01b-121">委派访问权限（分配）合作伙伴</span><span class="sxs-lookup"><span data-stu-id="be01b-121">Delegated Access Permissions (DAP) partners</span></span>](manage-office-365-with-windows-powershell-for-delegated-access-permissions-dap-p.md)

    <span data-ttu-id="be01b-122">如果您想要使用联合和云解决方案提供商（CSP）合作伙伴来管理 Microsoft 365 客户租户，请从这里开始。</span><span class="sxs-lookup"><span data-stu-id="be01b-122">Start here if you want to use Syndication and Cloud Solution Provider (CSP) partners to manage your Microsoft 365 customer tenants.</span></span>

- [<span data-ttu-id="be01b-123">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="be01b-123">Skype for Business Online</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)

    <span data-ttu-id="be01b-124">如果已安装 PowerShell 模块并希望对 Skype for Business Online 进行管理，请从这里开始。</span><span class="sxs-lookup"><span data-stu-id="be01b-124">Start here if you have installed the PowerShell modules and want to perform management of Skype for Business Online.</span></span>
