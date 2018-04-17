---
title: 向 Office 365 中的个人数据应用保护
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: ''
description: 了解如何使用 DLP 策略保护 Office 365 中的个人数据。
ms.openlocfilehash: 8753ffe2b051e18e0790fba14c7a063200a74758
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="apply-protection-to-personal-data-in-office-365"></a><span data-ttu-id="623f7-103">向 Office 365 中的个人数据应用保护</span><span class="sxs-lookup"><span data-stu-id="623f7-103">Apply protection to personal data in Office 365</span></span>

<span data-ttu-id="623f7-p101">对 Office 365 中的个人信息的保护包括使用数据丢失防护功能。借助 Office 365 安全与合规中心中的数据丢失防护 (DLP) 策略，可以识别、监视和自动保护 Office 365 内的敏感信息。</span><span class="sxs-lookup"><span data-stu-id="623f7-p101">Protection of personal information in Office 365 includes using data loss prevention capabilities. With data loss prevention (DLP) policies in the Office 365 Security & Compliance Center, you can identify, monitor, and automatically protect sensitive information across Office 365.</span></span>

<span data-ttu-id="623f7-p102">本主题介绍了如何使用 DLP 保护个人数据。本主题还列出了可用于实现 GDPR 符合性的其他保护功能，其中包括在 SharePoint 库中设置权限及使用设备访问策略。</span><span class="sxs-lookup"><span data-stu-id="623f7-p102">This topic describes how to use DLP to protect personal data. This topic also lists other protection capabilities that can be used to achieve GDPR compliance, including setting permissions in SharePoint libraries and using device access policies.</span></span>

## <a name="apply-protection-using-data-loss-prevention-in-office-365"></a><span data-ttu-id="623f7-108">在 Office 365 中使用数据丢失防护应用保护</span><span class="sxs-lookup"><span data-stu-id="623f7-108">Apply protection using data loss prevention in Office 365</span></span>

<span data-ttu-id="623f7-109">借助 DLP，可以：</span><span class="sxs-lookup"><span data-stu-id="623f7-109">With DLP, you can:</span></span>

-   <span data-ttu-id="623f7-110">识别许多位置中的敏感信息。</span><span class="sxs-lookup"><span data-stu-id="623f7-110">Identify sensitive information across many locations.</span></span>

-   <span data-ttu-id="623f7-111">防止意外共享敏感信息。</span><span class="sxs-lookup"><span data-stu-id="623f7-111">Prevent accidental sharing of sensitive information.</span></span>

-   <span data-ttu-id="623f7-112">帮助用户了解如何保持符合性，同时不会中断工作流。</span><span class="sxs-lookup"><span data-stu-id="623f7-112">Help users learn how to stay compliant without interrupting their workflow.</span></span>

-   <span data-ttu-id="623f7-113">查看显示符合组织 DLP 策略的内容的 DLP 报告。</span><span class="sxs-lookup"><span data-stu-id="623f7-113">View DLP reports showing content that matches your organization’s DLP policies.</span></span>

<span data-ttu-id="623f7-114">有关详细信息，请参阅[数据丢失防护策略概述](https://support.office.com/zh-CN/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)。</span><span class="sxs-lookup"><span data-stu-id="623f7-114">For more information, see [Overview of data loss prevention policies](https://support.office.com/zh-CN/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span></span>

![用于创建数据丢失防护策略的选项](Media/Apply-protection-to-personal-data-in-Office-365-image1.png)

<span data-ttu-id="623f7-116">此图显示了用于创建 DLP 策略的选项。</span><span class="sxs-lookup"><span data-stu-id="623f7-116">This illustration shows the options for creating a DLP policy:</span></span>

-   <span data-ttu-id="623f7-p103">选择要应用的保护。保护功能可以是：</span><span class="sxs-lookup"><span data-stu-id="623f7-p103">Choose the protection to apply. Protection can include:</span></span>

    -   <span data-ttu-id="623f7-119">针对用户的策略提示</span><span class="sxs-lookup"><span data-stu-id="623f7-119">Policy tips for users</span></span>

    -   <span data-ttu-id="623f7-120">针对管理员的电子邮件报告</span><span class="sxs-lookup"><span data-stu-id="623f7-120">Email report for admins</span></span>

    -   <span data-ttu-id="623f7-121">防止外部和/或内部共享</span><span class="sxs-lookup"><span data-stu-id="623f7-121">Prevent sharing externally, internally, or both</span></span>

-   <span data-ttu-id="623f7-p104">选择应用保护的条件。向包含此内容类型的文档应用保护：可以将策略配置为使用敏感信息类型和/或标签。</span><span class="sxs-lookup"><span data-stu-id="623f7-p104">Choose the criteria for applying the protection. Apply the protection to documents with this type of content: you can configure the policy to use sensitive information types and/or labels.</span></span>

### <a name="using-dlp-for-gdpr-compliance"></a><span data-ttu-id="623f7-124">使用 DLP 实现 GDPR 符合性</span><span class="sxs-lookup"><span data-stu-id="623f7-124">Using DLP for GDPR compliance</span></span>

<span data-ttu-id="623f7-p105">Office 365 DLP 的主要用途之一是识别出 Office 365 环境中与欧盟数据主体相关的个人数据。Office 365 DLP 可以告知合规性团队 SharePoint Online 和 OneDrive for Business 中存储的个人信息位于何处，或者用户何时发送了包含个人信息的电子邮件。当员工使用与欧盟居民有关的个人信息时，DLP 还可以为他们提供策略提示。</span><span class="sxs-lookup"><span data-stu-id="623f7-p105">One of the primary uses of Office 365 DLP is to identify personal data related to EU data subjects in your Office 365 environment. Office 365 DLP can notify your compliance teams of where personal information is stored in SharePoint Online and OneDrive for Business, or when users send email containing personal information. DLP can also provide policy tips to your employees when working with personal information related to EU residents.</span></span>

<span data-ttu-id="623f7-p106">环境中存储的欧盟居民数据位于何处，以及允许员工对其进行哪些处理，对这些感知度的培养和提高代表使用 Office 365 DLP 进行的信息保护级别。通常，已具有此信息类型访问权限的员工需要该访问权限来执行其日常工作。强制执行 DLP 策略有助于遵循 GDPR，此方式可以不限制访问权限。</span><span class="sxs-lookup"><span data-stu-id="623f7-p106">Educating and raising awareness to where EU resident data is stored in your environment and how your employees are permitted to handle it represents one level of information protection using Office 365 DLP. Often, employees who already have access to this type of information require this access to perform their day to day work. Enforcing DLP policies to help comply with GDPR may not require restricting access.</span></span>

<span data-ttu-id="623f7-p107">但是，若要遵循 GDPR，通常会涉及到从法律和信息安全角度对组织进行风险评估、对所存储的个人信息的类型及所在位置进行识别，以及是否有存储和处理该信息的正当理由。基于该评估实现策略来保护组织并遵循 GDPR 的过程可能需要删除员工对包含欧盟数据主体个人信息的文档的访问权限。如需进一步的保护，可配置其他 DLP 保护。</span><span class="sxs-lookup"><span data-stu-id="623f7-p107">However, complying with GDPR typically involves a risk based assessment of the organization from both a legal and information security perspective, identification of what type and where personal information is stored, as well as if there is a legal justification to store and process that information. Based on this assessment, implementing policies to protect the organization and comply with GDPR might require removing access for employees to documents that contain personal information for EU data subjects. In cases where further protection is required, additional DLP protection can be configured.</span></span>

<span data-ttu-id="623f7-p108">下表列出了使用 DLP 增强保护的三个配置项。第一个配置项（感知度）可用作针对 GDPR 的保护的起点和最低级别。</span><span class="sxs-lookup"><span data-stu-id="623f7-p108">The following table lists three configurations of increasing protection using DLP. The first configuration, awareness, can be used as a starting point and minimum level of protection for GDPR.</span></span>

### <a name="example-protection-levels-that-can-be-configured-with-dlp-policies-and-used-for-gdpr-compliance"></a><span data-ttu-id="623f7-136">可使用 DLP 策略配置的用于实现 GDPR 符合性的保护级别示例</span><span class="sxs-lookup"><span data-stu-id="623f7-136">Example protection levels that can be configured with DLP policies and used for GDPR compliance</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="623f7-137"><strong>保护级别</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-137"><strong>Protection level</strong></span></span></th>
<th align="left"><span data-ttu-id="623f7-138"><strong>对包含与欧盟数据主体相关个人信息的文档的 DLP 配置</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-138"><strong>DLP configuration for documents with personal information related to EU data subjects</strong></span></span></th>
<th align="left"><span data-ttu-id="623f7-139"><strong>优势和风险</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-139"><strong>Benefits and risks</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-140">感知度</span><span class="sxs-lookup"><span data-stu-id="623f7-140">Awareness</span></span></td>
<td align="left"><p><span data-ttu-id="623f7-141">在 SharePoint Online 和 OneDrive for Business 中的文档内发现此数据时，向合规性团队发送电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="623f7-141">Send email notifications to compliance teams when this data is found in documents in SharePoint Online and OneDrive for Business.</span></span></p>
<p><span data-ttu-id="623f7-142">在员工访问包含此数据的文档时，在 SharePoint 和 OneDrive for Business 中自定义策略提示并向员工显示相应的提示。</span><span class="sxs-lookup"><span data-stu-id="623f7-142">Customize and display Policy Tips to employees in SharePoint and OneDrive for Business when accessing documents containing this data.</span></span></p>
<p><span data-ttu-id="623f7-143">此数据被共享时，进行检测和报告。</span><span class="sxs-lookup"><span data-stu-id="623f7-143">Detect and report when this data is being shared.</span></span></p></td>
<td align="left"><p><span data-ttu-id="623f7-144">提高合规性团队及员工对该数据存储位置的感知度。</span><span class="sxs-lookup"><span data-stu-id="623f7-144">Raise awareness with compliance teams as well as employees regarding where this data is stored.</span></span></p>
<p><span data-ttu-id="623f7-145">指导员工学习用于处理包含该数据的文档的公司策略。</span><span class="sxs-lookup"><span data-stu-id="623f7-145">Educate employees on corporate policy for handling documents containing this data.</span></span></p>
<p><span data-ttu-id="623f7-146">无法防止员工对该数据进行内部或外部共享。</span><span class="sxs-lookup"><span data-stu-id="623f7-146">Does not prevent employees from sharing this data internally or externally.</span></span></p>
<p><span data-ttu-id="623f7-147">可以查看 DLP 报告以获取共享数据，从而决定是否需要增强保护。</span><span class="sxs-lookup"><span data-stu-id="623f7-147">You can review DLP reports for shared data and decide if you need to increase the protection.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="623f7-148">阻止外部共享</span><span class="sxs-lookup"><span data-stu-id="623f7-148">Prevent external sharing</span></span></td>
<td align="left"><p><span data-ttu-id="623f7-149">在将 SharePoint Online 和 OneDrive for Business 中包含该数据的文档内容与外部用户共享后，限制访问该内容。</span><span class="sxs-lookup"><span data-stu-id="623f7-149">Restrict access to documents that contain this data in SharePoint Online and OneDrive for Business when that content is shared with external users.</span></span></p>
<p><span data-ttu-id="623f7-150">防止向外部收件人发送附带包含该数据的文档的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="623f7-150">Prevent sending emails with documents that contain this data to external recipients.</span></span></p>
<p><span data-ttu-id="623f7-151">此数据被共享时，进行检测和报告。</span><span class="sxs-lookup"><span data-stu-id="623f7-151">Detect and report when this data is being shared.</span></span></p></td>
<td align="left"><p><span data-ttu-id="623f7-152">防止对该数据进行外部共享。同时允许员工在内部使用该数据。</span><span class="sxs-lookup"><span data-stu-id="623f7-152">Prevents external sharing of this data while allowing for employees to work with this data internally.</span></span></p>
<p><span data-ttu-id="623f7-153">可以查看 DLP 报告来获取内部共享数据，从而决定是否需要增强保护。</span><span class="sxs-lookup"><span data-stu-id="623f7-153">You can review DLP reports for internally shared data and decide if you need to increase this protection.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-154">阻止内部和外部共享</span><span class="sxs-lookup"><span data-stu-id="623f7-154">Prevent internal and external sharing</span></span></td>
<td align="left"><p><span data-ttu-id="623f7-155">在对 SharePoint Online 和 OneDrive for Business 中包含该数据的文档进行内部或外部共享后，限制访问该内容。</span><span class="sxs-lookup"><span data-stu-id="623f7-155">Restrict access to documents that contain this data in SharePoint Online and OneDrive for Business when that content is shared internally or externally.</span></span></p>
<p><span data-ttu-id="623f7-156">防止向内部和外部收件人发送包含该数据的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="623f7-156">Prevent sending emails which contain this data to both internal and external recipients.</span></span></p></td>
<td align="left"><p><span data-ttu-id="623f7-157">防止对该数据进行内部和外部共享。</span><span class="sxs-lookup"><span data-stu-id="623f7-157">Prevents internal and external sharing of this data.</span></span></p>
<p><span data-ttu-id="623f7-158">员工可能无法完成需要使用该数据的任务。</span><span class="sxs-lookup"><span data-stu-id="623f7-158">Employees might not be able to complete tasks that require working with this data.</span></span></p>
<p><span data-ttu-id="623f7-159">可以查看 DLP 报告以获取内部或外部共享数据，从而决定是否需要进行最终用户培训。</span><span class="sxs-lookup"><span data-stu-id="623f7-159">You can review DLP reports for internally or externally shared data and decide if end user training is needed.</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="623f7-p109">注意：在某些情况下，随着保护级别的提高，用户访问信息的能力会下降，进而可能会对用户的效率或完成日常任务的能力产生潜在的影响。通过实施可对员工产生影响的策略提高保护级别通常会与最终用户培训双管齐下，指导用户学习新的安全策略和流程，帮助他们在更加安全的环境中继续保持高效率。</span><span class="sxs-lookup"><span data-stu-id="623f7-p109">Note: As the levels of protection increase, the ability of users to access information will decrease in some cases, and could potentially impact their productivity or ability to complete day to day tasks. Increasing protection levels by implementing policies that impact employees is typically accompanied by end user training, educating users on new security policies and procedures to help them continue to be productive in a more secure environment.</span></span>

### <a name="example-dlp-policy-for-gdpr--awareness"></a><span data-ttu-id="623f7-162">针对 GDPR 的 DLP 策略示例 — 感知度</span><span class="sxs-lookup"><span data-stu-id="623f7-162">Example DLP policy for GDPR — Awareness</span></span> 

<span data-ttu-id="623f7-163">名称：对受 GDPR 制约的个人数据的感知度</span><span class="sxs-lookup"><span data-stu-id="623f7-163">Name: Awareness for personal data that is subject to GDPR.</span></span>

<span data-ttu-id="623f7-164">说明：向员工显示策略提示、在 SharePoint Online 和 OneDrive for Business 中的文档内发现该数据时通知合规性团队，在该数据在组织外部共享时进行检测和报告。</span><span class="sxs-lookup"><span data-stu-id="623f7-164">Description: Display policy tips to employees, notify compliance teams when this data is found in documents in SharePoint Online and OneDrive for Business, detect and report when this data is being shared outside your organization.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="623f7-165"><strong>控制</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-165"><strong>Control</strong></span></span></th>
<th align="left"><span data-ttu-id="623f7-166"><strong>设置</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-166"><strong>Settings</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-167">选择要保护的信息</span><span class="sxs-lookup"><span data-stu-id="623f7-167">Choose information to protect</span></span></td>
<td align="left"><span data-ttu-id="623f7-168">选择自定义策略模板。</span><span class="sxs-lookup"><span data-stu-id="623f7-168">Select a Custom policy template.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="623f7-169">位置</span><span class="sxs-lookup"><span data-stu-id="623f7-169">Locations</span></span></td>
<td align="left"><span data-ttu-id="623f7-170">Office 365 中的所有位置</span><span class="sxs-lookup"><span data-stu-id="623f7-170">All locations in Office 365</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-171">查找所包含的内容</span><span class="sxs-lookup"><span data-stu-id="623f7-171">Find content that contains</span></span></td>
<td align="left"><span data-ttu-id="623f7-172">单击“编辑”，然后添加为环境策展的所有敏感信息类型。</span><span class="sxs-lookup"><span data-stu-id="623f7-172">Click ‘Edit’ and add all the sensitive information types you curated for your environment.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="623f7-173">共享此内容时进行检测</span><span class="sxs-lookup"><span data-stu-id="623f7-173">Detect when this content is shared</span></span></td>
<td align="left"><span data-ttu-id="623f7-174">选中此框，然后选择“与组织外部人员”。</span><span class="sxs-lookup"><span data-stu-id="623f7-174">Check this box and select ‘with people outside my organization.’</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-175">当内容符合策略设置时通知用户</span><span class="sxs-lookup"><span data-stu-id="623f7-175">Notify users when content matches the policy settings</span></span></td>
<td align="left"><p><span data-ttu-id="623f7-176">选中此框（“向用户显示策略提示并向他们发送电子邮件通知。”）</span><span class="sxs-lookup"><span data-stu-id="623f7-176">Check this box (“Show policy tips to users and send them an email notification.”)</span></span></p>
<p><span data-ttu-id="623f7-p110">单击“自定义提示和电子邮件”，然后针对所在的环境进行更新。请参阅下文中的默认通知：<a href="https://support.office.com/en-us/article/Send-email-notifications-and-show-policy-tips-for-DLP-policies-87496bc5-9601-4473-8021-cb05c71369c1?ui=en-US&amp;rs=en-US&amp;ad=US">发送电子邮件通知并显示 DLP 策略的策略提示</a>。</span><span class="sxs-lookup"><span data-stu-id="623f7-p110">Click ‘Customize the tip and email’ and update these for your environment. See the default notifications in this article: <a href="https://support.office.com/en-us/article/Send-email-notifications-and-show-policy-tips-for-DLP-policies-87496bc5-9601-4473-8021-cb05c71369c1?ui=en-US&amp;rs=en-US&amp;ad=US">Send email notifications and show policy tips for DLP policies</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="623f7-179">共享特定数量的敏感信息时进行检测</span><span class="sxs-lookup"><span data-stu-id="623f7-179">Detect when a specific amount of sensitive info is being shared at one time</span></span></td>
<td align="left"><p><span data-ttu-id="623f7-180">“被共享的内容包含: 至少 ____ 个同种敏感信息类型的实例时进行检测” — 将其设置为 1。</span><span class="sxs-lookup"><span data-stu-id="623f7-180">‘Detect when content that’s being shared contains: At least ____ instances of the same sensitive info type’ — Set this to 1.</span></span></p>
<p><span data-ttu-id="623f7-p111">“在电子邮件中发送事件报告” — 选中此框。单击“选择要在报告中包含的内容及收件人”。务必添加合规性团队。</span><span class="sxs-lookup"><span data-stu-id="623f7-p111">‘Send incident reports in email’ — check this box. Click ‘Choose what to include in the report and who receives it.’ Be sure to add your compliance team.</span></span></p>
<p><span data-ttu-id="623f7-184">“限制可以访问此内容及可覆盖此策略的人员” — 取消选中此复选框，允许接收关于敏感信息的通知，不阻止用户访问该信息。</span><span class="sxs-lookup"><span data-stu-id="623f7-184">‘Restrict who can access the content and override the policy’ — clear this checkbox to receive notifications about sensitive information without preventing users from access that information.</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="623f7-185">所有位置包括：</span><span class="sxs-lookup"><span data-stu-id="623f7-185">All locations includes:</span></span>

-   <span data-ttu-id="623f7-186">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="623f7-186">SharePoint Online</span></span>

-   <span data-ttu-id="623f7-187">OneDrive for Business 帐户</span><span class="sxs-lookup"><span data-stu-id="623f7-187">OneDrive for Business accounts</span></span>

-   <span data-ttu-id="623f7-188">Exchange 邮箱</span><span class="sxs-lookup"><span data-stu-id="623f7-188">Exchange mailboxes</span></span>

<span data-ttu-id="623f7-189">由于内容搜索当前不允许通过电子邮件检测敏感信息类型，因此请考虑使用各个策略中的敏感信息类型的子集为 Exchange 创建单独的策略，并监视这些策略的执行情况。</span><span class="sxs-lookup"><span data-stu-id="623f7-189">Because Content Search doesn’t currently let you test sensitive information types with email,consider creating separate policies for Exchange with a subset of sensitive information types in each policy and monitoring the rollout of these policies.</span></span>

## <a name="additional-protection-you-can-apply-to-protect-personal-data-in-office-365"></a><span data-ttu-id="623f7-190">可以应用于保护 Office 365 中的个人数据的其他保护</span><span class="sxs-lookup"><span data-stu-id="623f7-190">Additional protection you can apply to protect personal data in Office 365</span></span>

<span data-ttu-id="623f7-p112">敏感信息类型、标签和数据丢失防护策略有助于识别包含特定数据的文档，并应用保护。但是，这些保护以针对数据访问权限设置了适当的权限、用户拥有的帐户未被攻击及设备正常运行为基础。</span><span class="sxs-lookup"><span data-stu-id="623f7-p112">Sensitive information types, labels, and data loss protection policies help you identify documents containing specific data and apply protection. However, these protections depend on appropriate permissions being set for access to data, users with accounts that are not compromised, and devices that are healthy.</span></span>

<span data-ttu-id="623f7-193">下图详细说明了为保护个人数据访问可以应用的其他保护。</span><span class="sxs-lookup"><span data-stu-id="623f7-193">The following illustration details additional protection you can apply to protect access to personal data.</span></span>

![用于保护个人数据访问的其他保护](Media/Apply-protection-to-personal-data-in-Office-365-image2.png)

<span data-ttu-id="623f7-195">为便于访问，下表提供了上图中的相同信息。</span><span class="sxs-lookup"><span data-stu-id="623f7-195">For accessibility, the following table provides the same information in the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="623f7-196"><strong>保护范围</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-196"><strong>Scope of protection</strong></span></span></th>
<th align="left"><span data-ttu-id="623f7-197"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-197"><strong>Capabilities</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-198">文档和电子邮件级别的保护（包括传输中的邮件，但当前不包括静态邮箱）</span><span class="sxs-lookup"><span data-stu-id="623f7-198">Document and email-level protection (includes mail in transit, but not currently mailboxes at rest)</span></span></td>
<td align="left"><p><span data-ttu-id="623f7-199">敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="623f7-199">Sensitive information types</span></span></p>
<p><span data-ttu-id="623f7-200">Office 标签</span><span class="sxs-lookup"><span data-stu-id="623f7-200">Office labels</span></span></p>
<p><span data-ttu-id="623f7-201">数据丢失防护策略</span><span class="sxs-lookup"><span data-stu-id="623f7-201">Data loss prevention policies</span></span></p>
<p><span data-ttu-id="623f7-202">适用于电子邮件的 Office 365 邮件加密</span><span class="sxs-lookup"><span data-stu-id="623f7-202">Office 365 Message Encryption for email</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="623f7-203">网站和库级别的保护（包括 SharePoint Online 和 OneDrive for Business 网站）</span><span class="sxs-lookup"><span data-stu-id="623f7-203">Site and library-level protection (includes SharePoint Online and OneDrive for Business sites)</span></span></td>
<td align="left"><p><span data-ttu-id="623f7-204">SharePoint Online 和 OneDrive for Business 网站和库的权限</span><span class="sxs-lookup"><span data-stu-id="623f7-204">Permissions for SharePoint Online and OneDrive for Business sites and libraries</span></span></p>
<p><span data-ttu-id="623f7-205">适用于 SharePoint Online 和 OneDrive for Business 的外部共享策略（网站级别）</span><span class="sxs-lookup"><span data-stu-id="623f7-205">External sharing policies for SharePoint Online and OneDrive for Business (site-level)</span></span></p>
<p><span data-ttu-id="623f7-206">网站级别的设备访问策略</span><span class="sxs-lookup"><span data-stu-id="623f7-206">Site-level device access policies</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-207">服务访问保护（包括对 Office 365 中的所有服务的访问）</span><span class="sxs-lookup"><span data-stu-id="623f7-207">Service access protection (includes access to all services in Office 365)</span></span></td>
<td align="left"><p><span data-ttu-id="623f7-208">企业移动性 + 安全性 (EMS) 套件中的标识和设备访问保护</span><span class="sxs-lookup"><span data-stu-id="623f7-208">Identity and device access protection in Enterprise Mobility + Security (EMS) suite</span></span></p>
<p><span data-ttu-id="623f7-209">特权访问管理</span><span class="sxs-lookup"><span data-stu-id="623f7-209">Privileged access management</span></span></p>
<p><span data-ttu-id="623f7-210">Windows 10 安全功能</span><span class="sxs-lookup"><span data-stu-id="623f7-210">Windows 10 security capabilities</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="623f7-211">本文的剩余部分详细介绍了上述各个保护类别。</span><span class="sxs-lookup"><span data-stu-id="623f7-211">The rest of this article provides more information on each of these categories of protection.</span></span>

### <a name="capabilities-that-are-ok-to-use-with-gdpr"></a><span data-ttu-id="623f7-212">适用于 GDPR 的功能</span><span class="sxs-lookup"><span data-stu-id="623f7-212">Capabilities that are OK to use with GDPR</span></span>

<span data-ttu-id="623f7-p113">可以在针对 GDPR 符合性配置的环境中使用下列功能。这些功能不是 GDPR 符合性所必需的，但是可以使用它们，并且不会对发现、保护、监视和报告与 GDPR 符合性有关数据的功能产生不良影响。</span><span class="sxs-lookup"><span data-stu-id="623f7-p113">You can use the following capabilities in an environment configured for GDPR compliance. These capabilities are not necessary for GDPR compliance, but they can be used without adversely affecting your ability to discover, protect, monitor, and report on data related to GDPR compliance.</span></span>

<span data-ttu-id="623f7-p114">客户密钥 — 允许客户始终控制用于加密 Office 365 内的静态数据的加密密钥。建议仅为具有管理自身加密密钥管理需求的客户启用此功能。</span><span class="sxs-lookup"><span data-stu-id="623f7-p114">Customer Key — Allows customers to provide and retain control over the encryption keys that are used to encrypt data at rest within Office 365. Recommended only for customers with a regulatory need to manage their own encryption keys.</span></span>

<span data-ttu-id="623f7-p115">客户密码箱 — 使用客户密码箱可以控制 Microsoft 支持工程师访问你的数据的方式，在必要时根据具体情况解决技术问题。可以控制是否向支持工程师提供数据访问权限。为每个请求提供了到期时间。</span><span class="sxs-lookup"><span data-stu-id="623f7-p115">Customer Lockbox — Customer lockbox allows you to control how a Microsoft support engineer accesses your data, if needed, to fix a technical issue on a case by case basis. You can control whether to give the support engineer access to your data or not. An expiration time is provided with each request.</span></span>

## <a name="site-and-library-level-protection"></a><span data-ttu-id="623f7-220">网站和库级别的保护</span><span class="sxs-lookup"><span data-stu-id="623f7-220">Site and library-level protection</span></span>

### <a name="permissions-for-sharepoint-and-onedrive-for-business-libraries"></a><span data-ttu-id="623f7-221">SharePoint 和 OneDrive for Business 库的权限</span><span class="sxs-lookup"><span data-stu-id="623f7-221">Permissions for SharePoint and OneDrive for Business libraries</span></span>

<span data-ttu-id="623f7-p116">使用 SharePoint 中的权限提供或限制用户对网站或其内容的访问权限。向默认的 SharePoint 组中添加单个用户或 Azure Active Directory 组。或者，创建自定义组并进行更细化的控制。</span><span class="sxs-lookup"><span data-stu-id="623f7-p116">Use permissions in SharePoint to provide or restrict user access to the site or its contents. Add individual users or Azure Active Directory groups to the default SharePoint groups. Or, create a custom group for finer-grain control.</span></span>

![从“完全控制”到“仅查看”的权限级别](Media/Apply-protection-to-personal-data-in-Office-365-image3.png)

<span data-ttu-id="623f7-p117">此图绘制了从“完全控制”到“仅查看”的权限级别。下表包含相同的信息。</span><span class="sxs-lookup"><span data-stu-id="623f7-p117">The illustration plots permission levels from Full control to View Only. The following table includes the same information.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="623f7-228"><strong>完全控制</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-228"><strong>Full Control</strong></span></span></th>
<th align="left"><span data-ttu-id="623f7-229"><strong>设计</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-229"><strong>Design</strong></span></span></th>
<th align="left"><span data-ttu-id="623f7-230"><strong>编辑</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-230"><strong>Edit</strong></span></span></th>
<th align="left"><span data-ttu-id="623f7-231"><strong>参与</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-231"><strong>Contribute</strong></span></span></th>
<th align="left"><span data-ttu-id="623f7-232"><strong>读取</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-232"><strong>Read</strong></span></span></th>
<th align="left"><span data-ttu-id="623f7-233"><strong>仅查看</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-233"><strong>View Only</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="623f7-234">参与 + 审核和自定义</span><span class="sxs-lookup"><span data-stu-id="623f7-234">Contribute + approve and customize</span></span></td>
<td align="left"><span data-ttu-id="623f7-235">参与 + 添加、编辑和删除列表（不只是列表项）</span><span class="sxs-lookup"><span data-stu-id="623f7-235">Contribute + add, edit and delete lists (not just list items)</span></span></td>
<td align="left"><span data-ttu-id="623f7-236">查看、添加、更新、删除列表项和文档</span><span class="sxs-lookup"><span data-stu-id="623f7-236">View, add, update, delete list items and documents</span></span></td>
<td align="left"><span data-ttu-id="623f7-237">查看和下载</span><span class="sxs-lookup"><span data-stu-id="623f7-237">View and download</span></span></td>
<td align="left"><span data-ttu-id="623f7-238">查看，不能下载</span><span class="sxs-lookup"><span data-stu-id="623f7-238">View, no download</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="623f7-239">详细信息：</span><span class="sxs-lookup"><span data-stu-id="623f7-239">More information:</span></span>

-   [<span data-ttu-id="623f7-240">了解 SharePoint 中的权限级别</span><span class="sxs-lookup"><span data-stu-id="623f7-240">Understanding permission levels in SharePoint</span></span>](https://support.office.com/zh-CN/article/Understanding-permission-levels-in-SharePoint-87ecbb0e-6550-491a-8826-c075e4859848)

-   [<span data-ttu-id="623f7-241">了解 SharePoint 组</span><span class="sxs-lookup"><span data-stu-id="623f7-241">Understanding SharePoint groups</span></span>](https://support.office.com/zh-CN/article/Understanding-SharePoint-groups-94d9b261-161e-4ace-829e-eca1c8cd2eb8)

### <a name="external-sharing-policies-for-sharepoint-and-onedrive-for-business-libraries"></a><span data-ttu-id="623f7-242">适用于 SharePoint 和 OneDrive for Business 库的外部共享策略</span><span class="sxs-lookup"><span data-stu-id="623f7-242">External sharing policies for SharePoint and OneDrive for Business libraries</span></span>

<span data-ttu-id="623f7-p118">许多组织允许进行外部共享，以便支持协作。查看租户范围的设置是如何配置的。然后查看对包含个人数据的网站的外部共享设置。</span><span class="sxs-lookup"><span data-stu-id="623f7-p118">Many organizations allow external sharing to support collaboration. Find out how your tenant-wide settings are configured. Then review the external sharing settings for sites that contain personal data.</span></span>

<span data-ttu-id="623f7-246">外部用户是指已邀请其访问你的 SharePoint Online 网站和文档，但不具备你的 SharePoint Online 或 Microsoft Office 365 订阅的许可证的组织外部人员。</span><span class="sxs-lookup"><span data-stu-id="623f7-246">An external user is someone outside of your organization who is invited to access your SharePoint Online sites and documents but does not have a license for your SharePoint Online or Microsoft Office 365 subscription.</span></span>

<span data-ttu-id="623f7-247">外部共享策略适用于 SharePoint Online 和 OneDrive for Business。</span><span class="sxs-lookup"><span data-stu-id="623f7-247">External sharing policies apply to both SharePoint Online and OneDrive for Business.</span></span>

-   <span data-ttu-id="623f7-248">必须是 SharePoint Online 管理员才能配置共享策略。</span><span class="sxs-lookup"><span data-stu-id="623f7-248">You must be a SharePoint Online admin to configure sharing policies.</span></span>

-   <span data-ttu-id="623f7-249">必须是网站所有者或具有完全控制权限才能与外部用户共享网站或文档。</span><span class="sxs-lookup"><span data-stu-id="623f7-249">You must be a Site Owner or have full control permissions to share a site or document with external users.</span></span>

<span data-ttu-id="623f7-250">下表总结了可以配置的控制。</span><span class="sxs-lookup"><span data-stu-id="623f7-250">The following table summarizes the controls you can configure.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="623f7-251"><strong>控制类别</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-251"><strong>Control category</strong></span></span></th>
<th align="left"><span data-ttu-id="623f7-252"><strong>选项</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-252"><strong>Options</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-253">共享类型</span><span class="sxs-lookup"><span data-stu-id="623f7-253">Type of sharing</span></span></td>
<td align="left"><p><span data-ttu-id="623f7-254">不允许在组织外部共享（可以为单个网站集设置）</span><span class="sxs-lookup"><span data-stu-id="623f7-254">Don’t allow sharing outside your organization (can be set for individual site collections)</span></span></p>
<p><span data-ttu-id="623f7-255">仅允许向经过身份验证的外部用户共享（允许向新的此类用户共享，或仅限于现有的此类用户，可以为单个网站集设置）\*</span><span class="sxs-lookup"><span data-stu-id="623f7-255">Allow sharing to authenticated external users only (allow new or limit to existing, can be set for individual site collections)\*</span></span></p>
<p><span data-ttu-id="623f7-256">允许通过匿名访问链接向外部用户共享（可以为单个网站集设置）</span><span class="sxs-lookup"><span data-stu-id="623f7-256">Allow sharing to external users with an anonymous access link (can be set for individual site collections)</span></span></p>
<p><span data-ttu-id="623f7-257">使用域限制外部共享（允许或拒绝列表）</span><span class="sxs-lookup"><span data-stu-id="623f7-257">Limit external sharing using domains (allow and deny list)</span></span></p>
<p><span data-ttu-id="623f7-258">选择默认的链接类型（匿名、公司可共享或受限）</span><span class="sxs-lookup"><span data-stu-id="623f7-258">Choose the default link type (anonymous, company shareable, or restricted)</span></span></p>
</td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="623f7-259">外部用户可以执行的操作</span><span class="sxs-lookup"><span data-stu-id="623f7-259">What external users can do</span></span></td>
<td align="left"><p><span data-ttu-id="623f7-260">阻止外部用户共享不属于他们的文件、文件夹、网站</span><span class="sxs-lookup"><span data-stu-id="623f7-260">Prevent external users from sharing files, folders, sites they don’t own</span></span></p>
<p><span data-ttu-id="623f7-261">要求外部用户使用接收邀请的同一帐户来接受共享邀请</span><span class="sxs-lookup"><span data-stu-id="623f7-261">Require external users to accept sharing invitations with the same account the invitation was sent to</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-262">通知</span><span class="sxs-lookup"><span data-stu-id="623f7-262">Notifications</span></span></td>
<td align="left"><p><span data-ttu-id="623f7-p119">目前仅在 OneDrive for Business 中可用。以下情况发生时通知所有者：</span><span class="sxs-lookup"><span data-stu-id="623f7-p119">Currently only available in OneDrive for Business. Notify owners when:</span></span></p>
- <p><span data-ttu-id="623f7-265">用户邀请其他外部用户访问共享文件</span><span class="sxs-lookup"><span data-stu-id="623f7-265">Users invite additional external users to shared files</span></span></p>
- <p><span data-ttu-id="623f7-266">外部用户接受访问文件的邀请</span><span class="sxs-lookup"><span data-stu-id="623f7-266">External users accept invitations to access files</span></span></p>
- <p><span data-ttu-id="623f7-267">创建或更改了匿名访问链接</span><span class="sxs-lookup"><span data-stu-id="623f7-267">An anonymous access link is created or changed</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="623f7-268">详细信息：</span><span class="sxs-lookup"><span data-stu-id="623f7-268">More information:</span></span>

-   <span data-ttu-id="623f7-269">
  [管理 SharePoint Online 环境的外部共享](https://support.office.com/en-us/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&rs=en-US&ad=US)</span><span class="sxs-lookup"><span data-stu-id="623f7-269">[Manage external sharing for your SharePoint Online environment](https://support.office.com/en-us/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&rs=en-US&ad=US)</span></span>

-   [<span data-ttu-id="623f7-270">与组织外部的用户共享站点或文档</span><span class="sxs-lookup"><span data-stu-id="623f7-270">Share sites or documents with people outside your organization</span></span>](https://support.office.com/zh-CN/article/Share-sites-or-documents-with-people-outside-your-organization-80e49744-e30f-44db-8d51-16661b1d4232)

### <a name="site-level-device-access-policies"></a><span data-ttu-id="623f7-271">网站级别的设备访问策略</span><span class="sxs-lookup"><span data-stu-id="623f7-271">Site-level device access policies</span></span>

<span data-ttu-id="623f7-p120">可通过 SharePoint Online 和 OneDrive for Business 配置网站级别的设备访问策略。由此可为包含敏感数据的网站配置更多保护功能。</span><span class="sxs-lookup"><span data-stu-id="623f7-p120">SharePoint Online and OneDrive for Business let you configure device access policies at the site level. This lets you configure more protection for sites with sensitive data.</span></span>

<span data-ttu-id="623f7-274">若要配置网站级别的设备访问策略，请务必将这些策略与租户级别的策略以及已在 Azure Active Directory、Intune 和 Intune 应用管理中配置的访问策略进行协调。</span><span class="sxs-lookup"><span data-stu-id="623f7-274">If you configure site-level device access policies, be sure to coordinate these with tenant-level policies and also with access policies that are configured in Azure Active Directory, Intune, and Intune App Management.</span></span>

<span data-ttu-id="623f7-p121">SharePoint 和 OneDrive for Business 的设备访问策略需要支持 Azure Active Directory 和 Microsoft Intune 中的策略，具体取决于正在实现的方案。下表总结了可以通过设备访问策略实现的目标，并说明了哪些产品需要支持策略。</span><span class="sxs-lookup"><span data-stu-id="623f7-p121">Device access policies for SharePoint and OneDrive for Business require supporting policies in Azure Active Directory and Microsoft Intune depending on the scenario you are implementing. The following table summarizes objectives you can achieve with device access policies and indicates which products require supporting policies.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left"><span data-ttu-id="623f7-277">仅允许来自指定 IP 地址位置的访问</span><span class="sxs-lookup"><span data-stu-id="623f7-277">Only allow access from specific IP address locations</span></span></th>
<th align="left"><span data-ttu-id="623f7-278">阻止用户将文件下载到未加入域的设备</span><span class="sxs-lookup"><span data-stu-id="623f7-278">Prevent users from downloading files to non-domain joined devices</span></span></th>
<th align="left"><span data-ttu-id="623f7-279">阻止在未加入域的设备上进行的访问</span><span class="sxs-lookup"><span data-stu-id="623f7-279">Block access on non-domain joined devices</span></span></th>
<th align="left"><span data-ttu-id="623f7-280">阻止用户将文件下载到不符合的设备</span><span class="sxs-lookup"><span data-stu-id="623f7-280">Prevent users from downloading files to non-compliant devices</span></span></th>
<th align="left"><span data-ttu-id="623f7-281">阻止在不符合的设备上进行的访问</span><span class="sxs-lookup"><span data-stu-id="623f7-281">Block access on non-compliant devices</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-282">SharePoint 管理中心</span><span class="sxs-lookup"><span data-stu-id="623f7-282">SharePoint admin center</span></span></td>
<td align="left"><span data-ttu-id="623f7-283">是</span><span class="sxs-lookup"><span data-stu-id="623f7-283">Yes</span></span></td>
<td align="left"><span data-ttu-id="623f7-284">是</span><span class="sxs-lookup"><span data-stu-id="623f7-284">Yes</span></span></td>
<td align="left"><span data-ttu-id="623f7-285">是</span><span class="sxs-lookup"><span data-stu-id="623f7-285">Yes</span></span></td>
<td align="left"><span data-ttu-id="623f7-286">是</span><span class="sxs-lookup"><span data-stu-id="623f7-286">Yes</span></span></td>
<td align="left"><span data-ttu-id="623f7-287">是</span><span class="sxs-lookup"><span data-stu-id="623f7-287">Yes</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="623f7-288">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="623f7-288">Azure Active Directory</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="623f7-289">是</span><span class="sxs-lookup"><span data-stu-id="623f7-289">Yes</span></span></td>
<td align="left"><span data-ttu-id="623f7-290">是</span><span class="sxs-lookup"><span data-stu-id="623f7-290">Yes</span></span></td>
<td align="left"><span data-ttu-id="623f7-291">是</span><span class="sxs-lookup"><span data-stu-id="623f7-291">Yes</span></span></td>
<td align="left"><span data-ttu-id="623f7-292">是</span><span class="sxs-lookup"><span data-stu-id="623f7-292">Yes</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-293">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="623f7-293">Microsoft Intune</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="623f7-294">是</span><span class="sxs-lookup"><span data-stu-id="623f7-294">Yes</span></span></td>
<td align="left"><span data-ttu-id="623f7-295">是</span><span class="sxs-lookup"><span data-stu-id="623f7-295">Yes</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="623f7-296">详细信息：[SharePoint Online 管理中心：控制来自非托管设备的访问](https://support.office.com/en-us/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622?ui=en-US&rs=en-US&ad=US)。</span><span class="sxs-lookup"><span data-stu-id="623f7-296">More information: [SharePoint Online admin center: Control access from unmanaged devices](https://support.office.com/en-us/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622?ui=en-US&rs=en-US&ad=US).</span></span>

## <a name="service-access-protection-for-identities-and-devices"></a><span data-ttu-id="623f7-297">对标识和设备的服务访问保护</span><span class="sxs-lookup"><span data-stu-id="623f7-297">Service access protection for identities and devices</span></span>

<span data-ttu-id="623f7-p122">Microsoft 建议为访问服务的标识和设备配置保护。用于保护 Office 365 服务访问的功能也可用于保护对其他 SaaS 服务、PaaS 服务甚至是其他云提供程序中的应用的访问。</span><span class="sxs-lookup"><span data-stu-id="623f7-p122">Microsoft recommends you configure protection for identities and devices that access the service. The work you put into protecting access to Office 365 services can also be used to protect access to other SaaS services, PaaS services, and even apps in other cloud providers.</span></span>

<span data-ttu-id="623f7-300">对标识和设备的访问保护提供了基准保护，确保标识不被攻击、设备安全且在设备上访问的组织数据已隔离并受到保护。</span><span class="sxs-lookup"><span data-stu-id="623f7-300">Access protection for identities and devices provides a baseline of protection to ensure that identities are not compromised, devices are safe, and organization data that is accessed on devices is isolated and protected.</span></span>

<span data-ttu-id="623f7-301">有关入门建议和配置指南，请参阅 [Microsoft 针对政治宣传活动、非营利组织和其他敏捷型组织的安全指南](https://docs.microsoft.com/zh-CN/microsoft-365-enterprise/microsoft-security-guidance)。</span><span class="sxs-lookup"><span data-stu-id="623f7-301">For starting point recommendations and configuration guidance, see [Microsoft security guidance for political campaigns, nonprofits, and other agile organizations](https://docs.microsoft.com/zh-CN/microsoft-365-enterprise/microsoft-security-guidance).</span></span>

<span data-ttu-id="623f7-302">对于使用 AD FS 的混合标识环境，请参阅[建议的安全策略和配置](https://docs.microsoft.com/zh-CN/microsoft-365-enterprise/microsoft-security-guidance)。</span><span class="sxs-lookup"><span data-stu-id="623f7-302">For hybrid identity environments with AD FS, see [Recommended security policies and configurations](https://docs.microsoft.com/zh-CN/microsoft-365-enterprise/microsoft-security-guidance).</span></span>

<span data-ttu-id="623f7-p123">下图说明了云服务（SaaS、PaaS）、帐户类型（租户域帐户与 B2B 帐户）和服务访问功能之间的关联。请务必注意哪些功能可用于 B2B 帐户。</span><span class="sxs-lookup"><span data-stu-id="623f7-p123">The following illustration describes how cloud services (SaaS, PaaS), account types (tenant domain accounts vs. B2B accounts) and service access capabilities relate. It’s important to note which capabilities can be used with B2B accounts.</span></span>

![云服务、帐户类型和访问功能](Media/Apply-protection-to-personal-data-in-Office-365-image4.png)

<span data-ttu-id="623f7-306">为便于访问，本节的剩余部分对此图进行了说明。</span><span class="sxs-lookup"><span data-stu-id="623f7-306">For accessibility, the rest of this section describes this illustration.</span></span>

### <a name="cloud-services"></a><span data-ttu-id="623f7-307">云服务</span><span class="sxs-lookup"><span data-stu-id="623f7-307">Cloud services</span></span>

<span data-ttu-id="623f7-p124">Azure Active Directory 提供对任意云服务的标识访问权限，包括非 Microsoft 提供程序（如 Amazon Web Services）。此图显示了 Office 365、“其他 SaaS 应用”和“PaaS 应用”。箭头从 Azure Active Directory 指向上述各个服务，表示 Azure Active Directory 可用于对上述所有应用类型的身份验证。</span><span class="sxs-lookup"><span data-stu-id="623f7-p124">Azure Active Directory provides identity access to any cloud service, including non-Microsoft providers such as Amazon Web Services. The illustration shows Office 365, “Other SaaS app,” and “PaaS app.” Arrows point from Azure Active Directory to each of these services, showing that Azure Active Directory can be used for authentication to all of these app types.</span></span>

### <a name="types-of-accounts"></a><span data-ttu-id="623f7-311">帐户类型</span><span class="sxs-lookup"><span data-stu-id="623f7-311">Types of accounts</span></span>

<span data-ttu-id="623f7-p125">租户域帐户是指添加到租户并直接管理的帐户。B2B 帐户是指你邀请与之进行协作的组织外部的用户的帐户。它们可以是其他 Office 365 帐户、其他组织帐户或使用者帐户（例如 Gmail）。此图显示了 Azure Active Directory 内的这两种帐户类型。</span><span class="sxs-lookup"><span data-stu-id="623f7-p125">Tenant domain accounts are account you add to your tenant and manage directly. B2B accounts are accounts for users outside your organization you invite to collaborate with. These can be other Office 365 accounts, other organization accounts, or consumer accounts (such as Gmail). The illustration shows both account types within Azure Active Directory.</span></span>

### <a name="capabilities"></a><span data-ttu-id="623f7-316">功能</span><span class="sxs-lookup"><span data-stu-id="623f7-316">Capabilities</span></span>

<span data-ttu-id="623f7-p126">下表中的功能可保护标识和设备。此表说明了哪些功能还可用于 B2B 帐户，与此图类似。</span><span class="sxs-lookup"><span data-stu-id="623f7-p126">The capabilities in the following table protect identities and devices. The table indicates which capabilities can also be used with B2B accounts, similar to the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="623f7-319"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-319"><strong>Capability</strong></span></span></th>
<th align="left"><span data-ttu-id="623f7-320"><strong>用于租户域帐户</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-320"><strong>Works with tenant domain accounts</strong></span></span></th>
<th align="left"><span data-ttu-id="623f7-321"><strong>用于 Azure B2B 帐户（没有其他许可）</strong></span><span class="sxs-lookup"><span data-stu-id="623f7-321"><strong>Works with Azure B2B accounts (without additional licensing)</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-322">多重身份验证和条件访问</span><span class="sxs-lookup"><span data-stu-id="623f7-322">Multi-factor authentication and conditional access</span></span></td>
<td align="left"><span data-ttu-id="623f7-323">是</span><span class="sxs-lookup"><span data-stu-id="623f7-323">Yes</span></span></td>
<td align="left"><span data-ttu-id="623f7-324">是</span><span class="sxs-lookup"><span data-stu-id="623f7-324">Yes</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="623f7-325">Azure AD Identity Protection</span><span class="sxs-lookup"><span data-stu-id="623f7-325">Azure AD Identity Protection</span></span></td>
<td align="left"><span data-ttu-id="623f7-326">是</span><span class="sxs-lookup"><span data-stu-id="623f7-326">Yes</span></span></td>
<td align="left"><span data-ttu-id="623f7-327">是</span><span class="sxs-lookup"><span data-stu-id="623f7-327">Yes</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-328">Azure AD Privileged Identity Management</span><span class="sxs-lookup"><span data-stu-id="623f7-328">Azure AD Privileged Identity Management</span></span></td>
<td align="left"><span data-ttu-id="623f7-329">是</span><span class="sxs-lookup"><span data-stu-id="623f7-329">Yes</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="623f7-330">移动应用管理 (MAM)</span><span class="sxs-lookup"><span data-stu-id="623f7-330">Mobile Application Management (MAM)</span></span></td>
<td align="left"><span data-ttu-id="623f7-331">是</span><span class="sxs-lookup"><span data-stu-id="623f7-331">Yes</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="623f7-332">设备注册和管理</span><span class="sxs-lookup"><span data-stu-id="623f7-332">Device enrollment and management</span></span></td>
<td align="left"><span data-ttu-id="623f7-333">是</span><span class="sxs-lookup"><span data-stu-id="623f7-333">Yes</span></span></td>
<td align="left"><span data-ttu-id="623f7-334">只有一个组织可以管理设备</span><span class="sxs-lookup"><span data-stu-id="623f7-334">Only one organization can manage a device</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="623f7-335">Windows 10 安全功能（基于设备符合性的条件访问需要进行设备管理）</span><span class="sxs-lookup"><span data-stu-id="623f7-335">Windows 10 security capabilities (conditional access based on device compliance requires device management)</span></span></td>
<td align="left"><span data-ttu-id="623f7-336">是</span><span class="sxs-lookup"><span data-stu-id="623f7-336">Yes</span></span></td>
<td align="left"><span data-ttu-id="623f7-337">是</span><span class="sxs-lookup"><span data-stu-id="623f7-337">Yes</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="623f7-338">可以向 B2B 帐户添加许可证，为这些用户提供其他功能，从而在必要时保护对环境中的个人数据的访问。</span><span class="sxs-lookup"><span data-stu-id="623f7-338">You can add licenses to B2B accounts to give these users additional capabilities, if needed, to protect access to personal data in your environment.</span></span>
