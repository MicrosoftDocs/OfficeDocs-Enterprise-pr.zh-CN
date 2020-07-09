---
title: Office 365 GCC High DNS 记录
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 摘要：适用于 Office 365 的 DNS 记录（GCC 高）
hideEdit: true
ms.openlocfilehash: 9bcaa71ab965f01481887d50a3e6ddbbbe3fadee
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "44339779"
---
# <a name="dns-records-for-office-365-gcc-high"></a><span data-ttu-id="6771b-103">Office 365 GCC High DNS 记录</span><span class="sxs-lookup"><span data-stu-id="6771b-103">DNS records for Office 365 GCC High</span></span>

<span data-ttu-id="6771b-104">*本文适用于 Office 365 GCC 高和 Microsoft 365 GCC 高*</span><span class="sxs-lookup"><span data-stu-id="6771b-104">*This article applies to Office 365 GCC High and Microsoft 365 GCC High*</span></span>

<span data-ttu-id="6771b-105">作为加入 Office 365 GCC 的一部分，你需要将 SMTP 和 SIP 域添加到你的在线服务租户。</span><span class="sxs-lookup"><span data-stu-id="6771b-105">As part of onboarding to Office 365 GCC High, you will need to add your SMTP and SIP domains to your Online Services tenant.</span></span>  <span data-ttu-id="6771b-106">你将使用 Azure AD PowerShell 中的 MsolDomain cmdlet 执行此操作，或使用[Azure 政府门户](https://portal.azure.us)启动添加域和证明所有权的过程。</span><span class="sxs-lookup"><span data-stu-id="6771b-106">You’ll do this using the New-MsolDomain cmdlet in Azure AD PowerShell or use the [Azure Government Portal](https://portal.azure.us) to start the process of adding the domain and proving ownership.</span></span>

<span data-ttu-id="6771b-107">将你的域添加到租户并进行验证后，请使用以下指南为以下服务添加适当的 DNS 记录。</span><span class="sxs-lookup"><span data-stu-id="6771b-107">Once you have your domains added to your tenant and validated, use the following guidance to add the appropriate DNS records for the services below.</span></span>  <span data-ttu-id="6771b-108">您可能需要修改下表，以适合组织的入站 MX 记录和任何现有的 Exchange 自动发现记录的相关需求。</span><span class="sxs-lookup"><span data-stu-id="6771b-108">You may need to modify the below table to fit your organization’s needs with respect to the inbound MX record(s) and any existing Exchange Autodiscover record(s) you have in place.</span></span>  <span data-ttu-id="6771b-109">强烈建议将这些 DNS 记录与邮件团队进行协调，以避免任何中断或电子邮件的误传递。</span><span class="sxs-lookup"><span data-stu-id="6771b-109">We strongly recommend coordinating these DNS records with your messaging team to avoid any outages or mis-delivery of email.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="6771b-110">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="6771b-110">Exchange Online</span></span>

| <span data-ttu-id="6771b-111">类型</span><span class="sxs-lookup"><span data-stu-id="6771b-111">Type</span></span> | <span data-ttu-id="6771b-112">优先级</span><span class="sxs-lookup"><span data-stu-id="6771b-112">Priority</span></span> | <span data-ttu-id="6771b-113">主机名</span><span class="sxs-lookup"><span data-stu-id="6771b-113">Host name</span></span> | <span data-ttu-id="6771b-114">指向 "地址" 或 "值"</span><span class="sxs-lookup"><span data-stu-id="6771b-114">Points to address or value</span></span> | <span data-ttu-id="6771b-115">TTL</span><span class="sxs-lookup"><span data-stu-id="6771b-115">TTL</span></span> |
| --- | --- | --- | --- | --- |
| <span data-ttu-id="6771b-116">MX</span><span class="sxs-lookup"><span data-stu-id="6771b-116">MX</span></span> | <span data-ttu-id="6771b-117">0</span><span class="sxs-lookup"><span data-stu-id="6771b-117">0</span></span> | @ | <span data-ttu-id="6771b-118">*tenant*mail.protection.office365.us （有关其他详细信息，请参阅下文）</span><span class="sxs-lookup"><span data-stu-id="6771b-118">*tenant*.mail.protection.office365.us (see below for additional details)</span></span> | <span data-ttu-id="6771b-119">1 Hour</span><span class="sxs-lookup"><span data-stu-id="6771b-119">1 Hour</span></span> |
| <span data-ttu-id="6771b-120">TXT</span><span class="sxs-lookup"><span data-stu-id="6771b-120">TXT</span></span> | - | @ | <span data-ttu-id="6771b-121">v = spf1 包括 include spf.protection.outlook.com-all</span><span class="sxs-lookup"><span data-stu-id="6771b-121">v=spf1 include:spf.protection.office365.us -all</span></span> | <span data-ttu-id="6771b-122">1 小时</span><span class="sxs-lookup"><span data-stu-id="6771b-122">1 Hour</span></span> |
| <span data-ttu-id="6771b-123">CNAME</span><span class="sxs-lookup"><span data-stu-id="6771b-123">CNAME</span></span> | - | <span data-ttu-id="6771b-124">autodiscover</span><span class="sxs-lookup"><span data-stu-id="6771b-124">autodiscover</span></span> | <span data-ttu-id="6771b-125">autodiscover.office365.us</span><span class="sxs-lookup"><span data-stu-id="6771b-125">autodiscover.office365.us</span></span> | <span data-ttu-id="6771b-126">1 Hour</span><span class="sxs-lookup"><span data-stu-id="6771b-126">1 Hour</span></span> |

### <a name="exchange-autodiscover-record"></a><span data-ttu-id="6771b-127">Exchange 自动发现记录</span><span class="sxs-lookup"><span data-stu-id="6771b-127">Exchange Autodiscover record</span></span>

<span data-ttu-id="6771b-128">如果您有本地 Exchange Server，我们建议您在迁移到 Exchange Online 时就地保留现有记录，并在完成迁移后立即更新该记录。</span><span class="sxs-lookup"><span data-stu-id="6771b-128">If you have Exchange Server on-premises, we recommend leaving your existing record in place while you migrate to Exchange Online, and update that record once you have completed your migration.</span></span> 

### <a name="exchange-online-mx-record"></a><span data-ttu-id="6771b-129">Exchange Online MX 记录</span><span class="sxs-lookup"><span data-stu-id="6771b-129">Exchange Online MX Record</span></span>

<span data-ttu-id="6771b-130">您的接受域的 MX 记录值遵循上面所述的标准*格式： mail.protection.office365.us*，将*租户*替换为默认租户名称的第一部分。</span><span class="sxs-lookup"><span data-stu-id="6771b-130">The MX record value for your accepted domains follows a standard format as noted above: *tenant*.mail.protection.office365.us, replacing *tenant* with the first part of your default tenant name.</span></span>

<span data-ttu-id="6771b-131">例如，如果您的租户名称为 contoso.onmicrosoft.us，则应使用**contoso.mail.protection.office365.us**作为 MX 记录的值。</span><span class="sxs-lookup"><span data-stu-id="6771b-131">For example, if your tenant name is contoso.onmicrosoft.us, you’d use **contoso.mail.protection.office365.us** as the value for your MX record.</span></span>

## <a name="skype-for-business-online"></a><span data-ttu-id="6771b-132">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="6771b-132">Skype for Business Online</span></span>

### <a name="cname-records"></a><span data-ttu-id="6771b-133">CNAME 记录</span><span class="sxs-lookup"><span data-stu-id="6771b-133">CNAME records</span></span>

| <span data-ttu-id="6771b-134">类型</span><span class="sxs-lookup"><span data-stu-id="6771b-134">Type</span></span> | <span data-ttu-id="6771b-135">主机名</span><span class="sxs-lookup"><span data-stu-id="6771b-135">Host name</span></span> | <span data-ttu-id="6771b-136">指向 "地址" 或 "值"</span><span class="sxs-lookup"><span data-stu-id="6771b-136">Points to address or value</span></span> | <span data-ttu-id="6771b-137">TTL</span><span class="sxs-lookup"><span data-stu-id="6771b-137">TTL</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="6771b-138">CNAME</span><span class="sxs-lookup"><span data-stu-id="6771b-138">CNAME</span></span> | <span data-ttu-id="6771b-139">sip</span><span class="sxs-lookup"><span data-stu-id="6771b-139">sip</span></span> | <span data-ttu-id="6771b-140">sipdir.online.gov.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="6771b-140">sipdir.online.gov.skypeforbusiness.us</span></span> | <span data-ttu-id="6771b-141">1 小时</span><span class="sxs-lookup"><span data-stu-id="6771b-141">1 Hour</span></span> |
| <span data-ttu-id="6771b-142">CNAME</span><span class="sxs-lookup"><span data-stu-id="6771b-142">CNAME</span></span> | <span data-ttu-id="6771b-143">lyncdiscover</span><span class="sxs-lookup"><span data-stu-id="6771b-143">lyncdiscover</span></span> | <span data-ttu-id="6771b-144">webdir.online.gov.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="6771b-144">webdir.online.gov.skypeforbusiness.us</span></span> | <span data-ttu-id="6771b-145">1 Hour</span><span class="sxs-lookup"><span data-stu-id="6771b-145">1 Hour</span></span> |

### <a name="srv-records"></a><span data-ttu-id="6771b-146">SRV 记录</span><span class="sxs-lookup"><span data-stu-id="6771b-146">SRV records</span></span>

| <span data-ttu-id="6771b-147">类型</span><span class="sxs-lookup"><span data-stu-id="6771b-147">Type</span></span> | <span data-ttu-id="6771b-148">服务</span><span class="sxs-lookup"><span data-stu-id="6771b-148">Service</span></span> | <span data-ttu-id="6771b-149">协议</span><span class="sxs-lookup"><span data-stu-id="6771b-149">Protocol</span></span> | <span data-ttu-id="6771b-150">端口</span><span class="sxs-lookup"><span data-stu-id="6771b-150">Port</span></span> | <span data-ttu-id="6771b-151">粗细</span><span class="sxs-lookup"><span data-stu-id="6771b-151">Weight</span></span> | <span data-ttu-id="6771b-152">Priority</span><span class="sxs-lookup"><span data-stu-id="6771b-152">Priority</span></span> | <span data-ttu-id="6771b-153">名称</span><span class="sxs-lookup"><span data-stu-id="6771b-153">Name</span></span> | <span data-ttu-id="6771b-154">Target</span><span class="sxs-lookup"><span data-stu-id="6771b-154">Target</span></span> | <span data-ttu-id="6771b-155">TTL</span><span class="sxs-lookup"><span data-stu-id="6771b-155">TTL</span></span> |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <span data-ttu-id="6771b-156">SRV</span><span class="sxs-lookup"><span data-stu-id="6771b-156">SRV</span></span> | <span data-ttu-id="6771b-157">\_sip</span><span class="sxs-lookup"><span data-stu-id="6771b-157">\_sip</span></span> | <span data-ttu-id="6771b-158">\_eap-tls</span><span class="sxs-lookup"><span data-stu-id="6771b-158">\_tls</span></span> | <span data-ttu-id="6771b-159">443</span><span class="sxs-lookup"><span data-stu-id="6771b-159">443</span></span> | <span data-ttu-id="6771b-160">1 </span><span class="sxs-lookup"><span data-stu-id="6771b-160">1</span></span> | <span data-ttu-id="6771b-161">100</span><span class="sxs-lookup"><span data-stu-id="6771b-161">100</span></span> | @ | <span data-ttu-id="6771b-162">sipdir.online.gov.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="6771b-162">sipdir.online.gov.skypeforbusiness.us</span></span> | <span data-ttu-id="6771b-163">1 Hour</span><span class="sxs-lookup"><span data-stu-id="6771b-163">1 Hour</span></span> |
| <span data-ttu-id="6771b-164">SRV</span><span class="sxs-lookup"><span data-stu-id="6771b-164">SRV</span></span> | <span data-ttu-id="6771b-165">\_sipfederationtls</span><span class="sxs-lookup"><span data-stu-id="6771b-165">\_sipfederationtls</span></span> | <span data-ttu-id="6771b-166">\_rdp-tcp</span><span class="sxs-lookup"><span data-stu-id="6771b-166">\_tcp</span></span> | <span data-ttu-id="6771b-167">5061</span><span class="sxs-lookup"><span data-stu-id="6771b-167">5061</span></span> | <span data-ttu-id="6771b-168">1 </span><span class="sxs-lookup"><span data-stu-id="6771b-168">1</span></span> | <span data-ttu-id="6771b-169">100</span><span class="sxs-lookup"><span data-stu-id="6771b-169">100</span></span> | @ | <span data-ttu-id="6771b-170">sipfed.online.gov.skypeforbusiness.us</span><span class="sxs-lookup"><span data-stu-id="6771b-170">sipfed.online.gov.skypeforbusiness.us</span></span> | <span data-ttu-id="6771b-171">1 Hour</span><span class="sxs-lookup"><span data-stu-id="6771b-171">1 Hour</span></span> |

## <a name="additional-dns-records"></a><span data-ttu-id="6771b-172">其他 DNS 记录</span><span class="sxs-lookup"><span data-stu-id="6771b-172">Additional DNS records</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6771b-173">如果您的 DNS 区域中有一个现有的*msoid* CNAME 记录，则您必须在此时**删除**dns 中的记录。</span><span class="sxs-lookup"><span data-stu-id="6771b-173">If you have an existing *msoid* CNAME record in your DNS zone, you must **remove** the record from DNS at this time.</span></span>  <span data-ttu-id="6771b-174">Msoid 记录与 Microsoft 365 企业版应用程序 *（以前称为 Office 365 专业增强版）* 不兼容，并将阻止激活成功。</span><span class="sxs-lookup"><span data-stu-id="6771b-174">The msoid record is incompatible with Microsoft 365 Enterprise Apps *(formerly Office 365 ProPlus)* and will prevent activation from succeeding.</span></span>
