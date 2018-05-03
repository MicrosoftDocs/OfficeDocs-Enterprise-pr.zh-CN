---
title: Office 365 安全事件响应
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 04/27/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: 此解决方案告诉您哪些最常见计算机安全攻击可能类似于在 Office 365 以及如何对其进行响应
ms.openlocfilehash: b9800070bde662603c731e2b8d64609b4f821cce
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="office-365-security-incident-response"></a><span data-ttu-id="66ca5-103">Office 365 安全事件响应</span><span class="sxs-lookup"><span data-stu-id="66ca5-103">Office 365 Security Incident Response</span></span>

 <span data-ttu-id="66ca5-104">**摘要：**此解决方案将向您介绍什么是 Office 365 中最常见的网络安全攻击指标、 如何产生积极确认任何给定的攻击，以及如何对其做出响应。</span><span class="sxs-lookup"><span data-stu-id="66ca5-104">**Summary:** This solution tells you what the indicators are for the most common cyber-security attacks in Office 365, how to positively confirm any given attack, and how to respond to it.</span></span>
  
## <a name="overview"></a><span data-ttu-id="66ca5-105">概述</span><span class="sxs-lookup"><span data-stu-id="66ca5-105">Overview</span></span>
<span data-ttu-id="66ca5-p101">不是所有网络攻击都将被都阻止。攻击者一直在寻找在防御策略中的新劣势或他们在利用旧的。了解如何识别攻击允许您以更快地响应，这就缩短安全事件的持续时间。</span><span class="sxs-lookup"><span data-stu-id="66ca5-p101">Not all cyber attacks can be thwarted. Attackers are constantly looking for new weaknesses in your defensive strategy or they are exploiting old ones. Knowing how to recognize an attack allows you to respond to it faster, which shortens the duration of the security incident.</span></span>

<span data-ttu-id="66ca5-p102">本系列文章帮助您了解特定类型攻击的可能外观 Office 365 中，并为您提供了您可以采取响应的步骤。了解快速入口点，这些文件：</span><span class="sxs-lookup"><span data-stu-id="66ca5-p102">This series of article helps you understand what a particular type of attack might look like in Office 365 and gives you steps you can take to respond. They are quick entry points to understanding:</span></span>
 
- <span data-ttu-id="66ca5-111">哪些攻击是及其工作原理。</span><span class="sxs-lookup"><span data-stu-id="66ca5-111">What the attack is and how it works.</span></span>
- <span data-ttu-id="66ca5-112">对内容进行签名，调用威胁 (IOC)，以查找以及如何查找这些指标。</span><span class="sxs-lookup"><span data-stu-id="66ca5-112">What signs, called indicators of compromise (IOC), to look for and how to look for them.</span></span>
- <span data-ttu-id="66ca5-113">如何产生积极确认攻击。</span><span class="sxs-lookup"><span data-stu-id="66ca5-113">How to positively confirm the attack.</span></span>
- <span data-ttu-id="66ca5-114">要执行截断攻击和更好的步骤保护您的组织将来。</span><span class="sxs-lookup"><span data-stu-id="66ca5-114">Steps to take to cut off the attack and better protect your organization in the future.</span></span>
- <span data-ttu-id="66ca5-115">在每台上的深入信息的链接攻击类型。</span><span class="sxs-lookup"><span data-stu-id="66ca5-115">Links to in-depth information on each attack type.</span></span>

<span data-ttu-id="66ca5-116">这里检查每月会随着时间的推移添加更多文章。</span><span class="sxs-lookup"><span data-stu-id="66ca5-116">Check back here monthly as more articles will be added over time.</span></span>

## <a name="detect-and-remediate-articles"></a><span data-ttu-id="66ca5-117">检测和修正文章</span><span class="sxs-lookup"><span data-stu-id="66ca5-117">Detect and Remediate Articles</span></span>
- [<span data-ttu-id="66ca5-118">检测和修正 Office 365 中的非法同意授予</span><span class="sxs-lookup"><span data-stu-id="66ca5-118">Detect and Remediate Illicit Consent Grants in Office 365</span></span>](detect-and-remediate-illicit-consent-grants.md)
- [<span data-ttu-id="66ca5-119">检测和修正 Outlook 规则和 Office 365 中的自定义窗体注入攻击</span><span class="sxs-lookup"><span data-stu-id="66ca5-119">Detect and Remediate Outlook Rules and Custom Forms Injections Attacks in Office 365</span></span>](detect-and-remediate-outlook-rules-forms-attack.md)
 
## <a name="secure-office-365-like-a-cybersecurity-pro"></a><span data-ttu-id="66ca5-120">像网络专业人员的安全保护 Office 365</span><span class="sxs-lookup"><span data-stu-id="66ca5-120">Secure Office 365 like a cybersecurity pro</span></span>
<span data-ttu-id="66ca5-p103">Office 365 订阅附带了强大的可用于保护您的数据和用户的安全功能集。 使用[Office 365 安全路线图： Top 优先级的前 30 天，90 天及其他认证实战](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352)实现 Microsoft 建议的用于保护 Office 365 租户的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="66ca5-p103">Your Office 365 subscription comes with a powerful set of security capabilities that you can use to protect your data and your users.  Use the [Office 365 security roadmap: Top priorities for the first 30 days, 90 days, and beyond](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) to implement Microsoft recommended best practices for securing your Office 365 tenant.</span></span>
- <span data-ttu-id="66ca5-p104">第一个 30 天内完成的任务。 这些没有直接影响，因此低影响到您的用户。</span><span class="sxs-lookup"><span data-stu-id="66ca5-p104">Tasks to accomplish in the first 30 days.  These have immediate affect and are low-impact to your users.</span></span>
- <span data-ttu-id="66ca5-p105">若要在 90 天内完成的任务。这些需要更多时间规划和实现，但会显著提高安全状况</span><span class="sxs-lookup"><span data-stu-id="66ca5-p105">Tasks to accomplish in 90 days. These take a bit more time to plan and implement but greatly improve your security posture</span></span>
- <span data-ttu-id="66ca5-p106">90 天前。在您的第一个 90 天工作中构建这些增强功能。</span><span class="sxs-lookup"><span data-stu-id="66ca5-p106">Beyond 90 days. These enhancements build in your first 90 days work.</span></span>






