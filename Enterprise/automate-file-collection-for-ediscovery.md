---
title: 电子数据展示文件收集自动化
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 摘要：了解如何从用户计算机中自动收集文件以用于电子数据展示。
ms.openlocfilehash: bfbe3b9218ed81727f2cc6ad9fabcb02e76d486b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490772"
---
# <a name="automate-file-collection-for-ediscovery"></a><span data-ttu-id="c2a85-103">电子数据展示文件收集自动化</span><span class="sxs-lookup"><span data-stu-id="c2a85-103">Automate file collection for eDiscovery</span></span>

 <span data-ttu-id="c2a85-104">**摘要：** 了解如何从用户计算机中自动收集文件以用于电子数据展示。</span><span class="sxs-lookup"><span data-stu-id="c2a85-104">**Summary:** Learn how to automate file collection from user computers for eDiscovery.</span></span>
  
<span data-ttu-id="c2a85-p101">所有公司都有可能采取诉讼或其他类型的法律行动。尽管法律部门致力于减少曝光，但是诉讼是商业活动中的平常事。公司在法律发现过程中需采取法律行动，向法院和对方律师提供所有相关书面材料。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p101">All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel.</span></span> 
  
<span data-ttu-id="c2a85-p102">电子数据展示是一个过程，通过此过程公司可以进行存储、搜索、识别、保留、筛选，以及提供以电子形式存在的相关书面材料。 SharePoint 2013、Exchange Server 2013、Lync Server 2013、SharePoint Online 和 Exchange Online 可以容纳大量的书面内容。 根据版本，这些产品可以支持eDiscovery和就地保留（Lync，通过 Exchange Server），这使得法律团队更易于对给定案例的最相关的内容进行索引编制、标识、保留和筛选。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p102">eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.</span></span>
  
<span data-ttu-id="c2a85-p103">许多文档存储在用户（保管人）的本地计算机上，而不是存储在某个集中位置。这使得 SharePoint 2013 基本上不可能进行搜索；如果无法搜索，则不能包含在eDiscovery中。此解决方案显示如何使用登录脚本、System Center Orchestrator 2012 R2 和 Windows PowerShell，使 Exchange Server 从用户的计算机中自动标识和收集书面材料。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p103">Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.</span></span>
  
## <a name="what-this-solution-does"></a><span data-ttu-id="c2a85-114">此解决方案的作用</span><span class="sxs-lookup"><span data-stu-id="c2a85-114">What this solution does</span></span>

<span data-ttu-id="c2a85-p104">此解决方案使用全局安全组、组策略和 Windows PowerShell 脚本来查找、存储和收集用户本地计算机中的内容和 Outlook 个人存储 (PST) 文件并存储到隐藏的文件共享中。在此处，PST 可能会导入到 Exchange Server 2013 或 Exchange Online。然后，所有文件使用 System Center Orchestrator 2012 R2 Runbook 移动到 Microsoft Azure 中的另一个文件共享，以便由 SharePoint 2013 长期存储和索引。然后您可以像平时一样使用本地 SharePoint 2013 部署或 SharePoint Online 中的eDiscovery中心执行eDiscovery。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p104">This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="c2a85-p105">此解决方案使用 robocopy 将文件从保管人的计算机中复制到一个集中的文件共享。因为 robocopy 不复制打开或锁定的文件，所以不会收集保管人打开的任意文件，其中包括 PST 文件。您需要手动收集这些文件。此解决方案确实为您提供一个列表，明确标识了它无法复制的文件和每个文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p105">This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file.</span></span> 
  
<span data-ttu-id="c2a85-123">下图向您展示了解决方案的所有步骤和元素。</span><span class="sxs-lookup"><span data-stu-id="c2a85-123">The following diagram walks you through all the steps and elements of the solution.</span></span>
  
![自动化文件收集解决方案概述](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|<span data-ttu-id="c2a85-125">\*\*\*\*图例\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c2a85-125">\*\*\*\*Legend\*\*\*\*</span></span>||
|:-----|:-----|
|![洋红色标注 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|<span data-ttu-id="c2a85-127">创建一个组策略对象 (GPO) 并将其与收集登录脚本相关联。</span><span class="sxs-lookup"><span data-stu-id="c2a85-127">Create a Group Policy object (GPO), and associate it with the collection logon script.</span></span>  <br/> |
|![洋红色标注 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| <span data-ttu-id="c2a85-129">  配置 GPO 安全筛选器，仅将 GPO 应用到保管人组</span><span class="sxs-lookup"><span data-stu-id="c2a85-129">Configure the GPO security filter to apply the GPO only to the Custodians group.</span></span> <br/> |
|![洋红色标注 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|<span data-ttu-id="c2a85-131">保管人登录和 GPO 运行，调用收集登录脚本。</span><span class="sxs-lookup"><span data-stu-id="c2a85-131">A Custodian logs on and the GPO runs, calling the collection logon script.</span></span>  <br/> |
|![洋红色标注 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|<span data-ttu-id="c2a85-133">收集登录脚本清单均本地挂载到保管人计算机上的驱动器，搜索您需要的文件并记录其位置。</span><span class="sxs-lookup"><span data-stu-id="c2a85-133">The collection logon script inventories all locally attached drives on the Custodians computer, searching for the files you want, and recording their location.</span></span>  <br/> |
|![洋红色标注 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|<span data-ttu-id="c2a85-135">收集登录脚本将清单文件复制到暂存服务器上的隐藏文件共享中。</span><span class="sxs-lookup"><span data-stu-id="c2a85-135">The collection logon script copies the inventoried files to a hidden file share on the staging server.</span></span>  <br/> |
|![洋红色标注 6](media/99589726-0c7e-406b-a276-44301a135768.png)| <span data-ttu-id="c2a85-137">（选项 A）手动运行 PST 导入脚本，将收集的 PST 文件导入到 Exchange Server 2013。</span><span class="sxs-lookup"><span data-stu-id="c2a85-137">(Option A) Manually run the PST import script to import the collected PST files into Exchange Server 2013.</span></span> <br/> |
|![洋红色标注 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|<span data-ttu-id="c2a85-139">（选项 B）使用 Office 365 导入工具和过程，将收集的 PST 文件导入到 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="c2a85-139">(Option B) Using the Office 365 Import tool and process, import the collected PST files into Exchange Online.</span></span>  <br/> |
|![洋红色标注 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|<span data-ttu-id="c2a85-141">将所有收集的文件移至 Azure 文件共享，以便在 MoveToColdStorageSystem Center Orchestrator 2012 R2 Runbook 中长期存储。</span><span class="sxs-lookup"><span data-stu-id="c2a85-141">Move all collected files to an Azure file share for long term storage with the MoveToColdStorage System Center Orchestrator 2012 R2 runbook.</span></span> <br/> |
|![洋红色标注 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|<span data-ttu-id="c2a85-143">使用 SharePoint 2013 对冷存储文件共享中的文件编制索引。</span><span class="sxs-lookup"><span data-stu-id="c2a85-143">Index the files in the cold storage file share with SharePoint 2013.</span></span>  <br/> |
|![洋红色标注 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|<span data-ttu-id="c2a85-145">对冷存储和本地 Exchange Server 2013 中的内容执行eDiscovery。</span><span class="sxs-lookup"><span data-stu-id="c2a85-145">Perform eDiscovery on content in cold storage and in the on-premises Exchange Server 2013.</span></span>  <br/> |
|![洋红色标注 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|<span data-ttu-id="c2a85-147">对 Office 365 中的内容执行eDiscovery。</span><span class="sxs-lookup"><span data-stu-id="c2a85-147">Perform eDiscovery on content in Office 365.</span></span>  <br/> |
   
## <a name="prerequisites"></a><span data-ttu-id="c2a85-148">先决条件</span><span class="sxs-lookup"><span data-stu-id="c2a85-148">Prerequisites</span></span>

<span data-ttu-id="c2a85-p106">如果您正在考虑 eDiscovery，此解决方案的配置需要很多 元素，其中大部分您可能已经具备并已配置。对于您可能不具备或者需要特定配置的元素，我们将为您提供生成基本配置所需的链接。您必须在配置解决方案之前就已具备基本配置。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p106">The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.</span></span>
  
### <a name="base-configuration"></a><span data-ttu-id="c2a85-152">基本配置</span><span class="sxs-lookup"><span data-stu-id="c2a85-152">Base configuration</span></span>

|<span data-ttu-id="c2a85-153">**元素**</span><span class="sxs-lookup"><span data-stu-id="c2a85-153">**Element**</span></span>|<span data-ttu-id="c2a85-154">**链接**</span><span class="sxs-lookup"><span data-stu-id="c2a85-154">**Link**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c2a85-155">Active Directory 域服务 (AD DS) 域</span><span class="sxs-lookup"><span data-stu-id="c2a85-155">Active Directory Domain Services (AD DS) domain</span></span>  <br/> ||
|<span data-ttu-id="c2a85-156">从本地网络的 Internet 连接</span><span class="sxs-lookup"><span data-stu-id="c2a85-156">Internet connectivity from your on-premises network</span></span>  <br/> ||
|<span data-ttu-id="c2a85-157">支持 SharePoint 2013 和 System Center Orchestrator 2012 R2 的 SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="c2a85-157">SQL Server 2012 to support SharePoint 2013 and System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="c2a85-158">部署 System Center Orchestrator - 2012</span><span class="sxs-lookup"><span data-stu-id="c2a85-158">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| <span data-ttu-id="c2a85-159">用于eDiscovery的本地或基于 Azure 的 SharePoint 2013（选项 A 所必需）</span><span class="sxs-lookup"><span data-stu-id="c2a85-159">On-premises or Azure based SharePoint 2013 for eDiscovery (required for Option A)</span></span> <br/> ||
|<span data-ttu-id="c2a85-160">用于暂存的本地文件共享服务器</span><span class="sxs-lookup"><span data-stu-id="c2a85-160">On-premises file share server for staging</span></span>  <br/> ||
|<span data-ttu-id="c2a85-161">用于选项 A PST 导入的本地 Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="c2a85-161">On-premises Exchange Server 2013 for Option A PST import</span></span>  <br/> |<span data-ttu-id="c2a85-162">CU5 (15.913.22) 位于 [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)。</span><span class="sxs-lookup"><span data-stu-id="c2a85-162">CU5 (15.913.22) is available at [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426).</span></span>  <br/> |
|<span data-ttu-id="c2a85-163">System Center Orchestrator 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c2a85-163">System Center Orchestrator 2012 R2</span></span>  <br/> |[<span data-ttu-id="c2a85-164">部署 System Center Orchestrator - 2012</span><span class="sxs-lookup"><span data-stu-id="c2a85-164">Deploying System Center Orchestrator - 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|<span data-ttu-id="c2a85-165">具有 Exchange Online 和 SharePoint Online 的 Office 365（E3 计划）（选项 B 所必需）</span><span class="sxs-lookup"><span data-stu-id="c2a85-165">Office 365 (E3 Plan) with Exchange Online and SharePoint Online (required for Option B)</span></span>  <br/> |<span data-ttu-id="c2a85-166">若要注册 Office 365 E3 订阅，请参阅 [Office 365 E3 订阅](https://go.microsoft.com/fwlink/p/?LinkId=613504)。</span><span class="sxs-lookup"><span data-stu-id="c2a85-166">To sign up for an Office 365 E3 subscription, see [Office 365 E3 subscription](https://go.microsoft.com/fwlink/p/?LinkId=613504).</span></span>  <br/> |
|<span data-ttu-id="c2a85-167">对虚拟机的 Azure 订阅</span><span class="sxs-lookup"><span data-stu-id="c2a85-167">Azure subscription with a virtual machine</span></span>  <br/> |<span data-ttu-id="c2a85-168">若要注册 Azure，请参阅[订阅 Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span><span class="sxs-lookup"><span data-stu-id="c2a85-168">To sign up for a Azure, see [Subscribe to Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010)</span></span> <br/> |
|<span data-ttu-id="c2a85-169">本地网络和 Azure 订阅之间的 VPN 连接</span><span class="sxs-lookup"><span data-stu-id="c2a85-169">A VPN connection between your on-premises network and your Azure subscription</span></span>  <br/> |<span data-ttu-id="c2a85-170">若要在 Azure 订阅和本地网络之间设置 VPN 隧道，请参阅[将本地网络连接到 Microsoft Azure 虚拟网络](https://go.microsoft.com/fwlink/p/?LinkId=613507)。</span><span class="sxs-lookup"><span data-stu-id="c2a85-170">To set up a VPN tunnel between your Azure subscription and your on-premises network, see [Connect an on-premises network to a Microsoft Azure virtual network](https://go.microsoft.com/fwlink/p/?LinkId=613507).</span></span>  <br/> |
|<span data-ttu-id="c2a85-171">SharePoint 2013 已配置 eDiscovery 以搜索 SharePoint 和 Exchange Server 2013 以及（可选）Lync Server 2013</span><span class="sxs-lookup"><span data-stu-id="c2a85-171">SharePoint 2013 eDiscovery configured to search across SharePoint and Exchange Server 2013 and optionally Lync Server 2013</span></span>  <br/> |<span data-ttu-id="c2a85-172">若要以这种方式配置eDiscovery，请参阅[在 SharePoint Server 2013 中配置电子数据展示](https://go.microsoft.com/fwlink/p/?LinkId=613508)和[测试实验室指南：为 Exchange、Lync、SharePoint 和 Windows 文件共享测试实验室配置电子数据展示](https://go.microsoft.com/fwlink/p/?LinkId=393130)。</span><span class="sxs-lookup"><span data-stu-id="c2a85-172">To configure eDiscovery in this fashion, see [Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508) and[Test Lab Guide: Configure eDiscovery for an Exchange, Lync, SharePoint and Windows File Shares Test Lab](https://go.microsoft.com/fwlink/p/?LinkId=393130).</span></span>  <br/> |
|<span data-ttu-id="c2a85-173">Office 365 中的eDiscovery用于 SharePoint Online 和 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c2a85-173">eDiscovery in Office 365 for SharePoint Online and Exchange Online</span></span>  <br/> |<span data-ttu-id="c2a85-174">若要在 Office 365 中配置eDiscovery，请参阅[在 SharePoint Online 中设置电子数据展示中心](https://go.microsoft.com/fwlink/p/?LinkId=613628)。</span><span class="sxs-lookup"><span data-stu-id="c2a85-174">To configure eDiscovery in Office 365, see [Set up an eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=613628).</span></span>  <br/> |
   
## <a name="configure-the-environment"></a><span data-ttu-id="c2a85-175">配置环境</span><span class="sxs-lookup"><span data-stu-id="c2a85-175">Configure the environment</span></span>

<span data-ttu-id="c2a85-176">现在您已具备基本配置， 可以继续配置解决方案本身。</span><span class="sxs-lookup"><span data-stu-id="c2a85-176">Now that you have the base configuration in place, you can move ahead to configuring the solution itself.</span></span> 
  
### <a name="staging-file-share"></a><span data-ttu-id="c2a85-177">暂存文件共享</span><span class="sxs-lookup"><span data-stu-id="c2a85-177">Staging file share</span></span>

1. <span data-ttu-id="c2a85-178">在本地域中创建一个名为 Custodians 的全局安全组。</span><span class="sxs-lookup"><span data-stu-id="c2a85-178">In the on-premises domain, create a global security group named Custodians.</span></span>
    
2. <span data-ttu-id="c2a85-p107">为从保管人计算机中收集的文件创建一个隐藏文件共享。这应在本地服务器上。例如，在名为 Staging 的服务器上，创建一个名为 Cases$ 的文件共享。必须包含 **$** 才能使该共享成为隐藏共享。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p107">Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.</span></span>
    
3. <span data-ttu-id="c2a85-183">设置下列共享权限：</span><span class="sxs-lookup"><span data-stu-id="c2a85-183">Set the following share permissions:</span></span>
    
  - <span data-ttu-id="c2a85-184">保管人：更改、读取</span><span class="sxs-lookup"><span data-stu-id="c2a85-184">Custodians: Change, Read</span></span>
    
  - <span data-ttu-id="c2a85-185">管理员：完全控制</span><span class="sxs-lookup"><span data-stu-id="c2a85-185">Administrators: Full Control</span></span>
    
  - <span data-ttu-id="c2a85-186">Exchange 受信任子系统：更改、读取</span><span class="sxs-lookup"><span data-stu-id="c2a85-186">Exchange Trusted Subsystem: Change, Read</span></span>
    
4. <span data-ttu-id="c2a85-p108">打开"安全"选项卡，添加 Custodians 组，然后单击"高级"。为 Custodians 组设置以下权限：</span><span class="sxs-lookup"><span data-stu-id="c2a85-p108">Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:</span></span>
    
  - <span data-ttu-id="c2a85-189">**类型：拒绝**</span><span class="sxs-lookup"><span data-stu-id="c2a85-189">**Type: Deny**</span></span>
    
  - <span data-ttu-id="c2a85-190">**适用于：此文件夹及其子文件夹和文件**</span><span class="sxs-lookup"><span data-stu-id="c2a85-190">**Applies to: This folder, subfolders and files**</span></span>
    
5. <span data-ttu-id="c2a85-191">单击"高级权限"并选择以下项：</span><span class="sxs-lookup"><span data-stu-id="c2a85-191">Click **Advanced Permissions** and select the following:</span></span>
    
  - <span data-ttu-id="c2a85-192">**读取属性**</span><span class="sxs-lookup"><span data-stu-id="c2a85-192">**Read attributes**</span></span>
    
  - <span data-ttu-id="c2a85-193">**读取扩展属性**</span><span class="sxs-lookup"><span data-stu-id="c2a85-193">**Read extended attributes**</span></span>
    
  - <span data-ttu-id="c2a85-194">**读取权限**</span><span class="sxs-lookup"><span data-stu-id="c2a85-194">**Read permissions**</span></span>
    
6. <span data-ttu-id="c2a85-195">通过执行以下操作测试对 Cases$ 文件共享的访问权限：</span><span class="sxs-lookup"><span data-stu-id="c2a85-195">Test access to the Cases$ file share by doing the following:</span></span>
    
1. <span data-ttu-id="c2a85-196">将用户添加到 Custodians 组。</span><span class="sxs-lookup"><span data-stu-id="c2a85-196">Add a user to the Custodians group.</span></span>
    
2. <span data-ttu-id="c2a85-197">将文件放在 Cases$ 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="c2a85-197">Place a file in the Cases$ folder.</span></span>
    
3. <span data-ttu-id="c2a85-p109">作为用户，浏览到暂存服务器，例如浏览到 \\\\Staging 共享以查看提供了哪些共享。不应看到 **Cases$** 共享列出。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p109">As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.</span></span>
    
4. <span data-ttu-id="c2a85-p110">将 Cases$ 共享的完整路径手动键入到资源管理器中。这应该会打开 Cases$ 共享。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p110">Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.</span></span>
    
5. <span data-ttu-id="c2a85-p111">尝试打开您之前放在共享中的文件，这应该会失败。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p111">Try to open the file you previously placed in the share. This should fail.</span></span>
    
### <a name="logon-script"></a><span data-ttu-id="c2a85-204">登录脚本</span><span class="sxs-lookup"><span data-stu-id="c2a85-204">Logon script</span></span>

1. <span data-ttu-id="c2a85-205">将此 Windows PowerShell 脚本复制并粘贴到记事本：</span><span class="sxs-lookup"><span data-stu-id="c2a85-205">Copy and paste this Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. <span data-ttu-id="c2a85-206">在易于您查找的位置将上述脚本另存为 CollectionScript.ps1，例如，C:\\AFCScripts。</span><span class="sxs-lookup"><span data-stu-id="c2a85-206">Save the above script as CollectionScript.ps1 in a location that's easy for you to find, for example, C:\\AFCScripts.</span></span>
    
3. <span data-ttu-id="c2a85-p112">使用记事本中的“转到”功能。根据需要进行以下更改：</span><span class="sxs-lookup"><span data-stu-id="c2a85-p112">Use the Go To feature in Notepad. Make the following changes, as needed:</span></span>
    
|<span data-ttu-id="c2a85-209">**行号**</span><span class="sxs-lookup"><span data-stu-id="c2a85-209">**Line #**</span></span>|<span data-ttu-id="c2a85-210">**需更改的内容**</span><span class="sxs-lookup"><span data-stu-id="c2a85-210">**What you need to change**</span></span>|<span data-ttu-id="c2a85-211">**必需/可选**</span><span class="sxs-lookup"><span data-stu-id="c2a85-211">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="c2a85-212">71</span><span class="sxs-lookup"><span data-stu-id="c2a85-212">71</span></span>  <br/> |<span data-ttu-id="c2a85-p113">**$FileTypes** 变量。包括您希望脚本在数组变量中存储和收集的所有文件类型扩展名。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p113">**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. </span></span><br/> |<span data-ttu-id="c2a85-215">可选</span><span class="sxs-lookup"><span data-stu-id="c2a85-215">Optional</span></span>  <br/> |
|<span data-ttu-id="c2a85-216">76 和 77</span><span class="sxs-lookup"><span data-stu-id="c2a85-216">76 and 77</span></span>  <br/> |<span data-ttu-id="c2a85-p114">更改 **$CaseNo** 变量构建的方式以满足您的需求。脚本捕获当前日期和时间并向其附加用户名。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p114">Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. </span></span><br/> |<span data-ttu-id="c2a85-219">可选</span><span class="sxs-lookup"><span data-stu-id="c2a85-219">Optional</span></span>  <br/> |
|<span data-ttu-id="c2a85-220">80</span><span class="sxs-lookup"><span data-stu-id="c2a85-220">80</span></span>  <br/> |<span data-ttu-id="c2a85-221">**$CaseRootLocation** 变量需设置为您的暂存服务器集合文件共享，例如， **\\\\Staging\\Cases$** 。</span><span class="sxs-lookup"><span data-stu-id="c2a85-221">**$CaseRootLocation** variable needs to be set to your staging servers collection file share, for example **\\\\Staging\\Cases$**.</span></span> <br/> |<span data-ttu-id="c2a85-222">必需</span><span class="sxs-lookup"><span data-stu-id="c2a85-222">Required</span></span>  <br/> |
   
4. <span data-ttu-id="c2a85-223">将 CollectionScript.ps1 文件放在域控制器上的 Netlogon 文件共享中。</span><span class="sxs-lookup"><span data-stu-id="c2a85-223">Place the CollectionScript.ps1 file in the Netlogon file share on a domain controller.</span></span> 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a><span data-ttu-id="c2a85-224">为登录脚本和 Custodians 组配置 GPO</span><span class="sxs-lookup"><span data-stu-id="c2a85-224">Configure GPO for the logon script and Custodians Group</span></span>

1. <span data-ttu-id="c2a85-225">按照[使用组策略中的启动、关机、登录和注销脚本](https://go.microsoft.com/fwlink/p/?LinkId=614844)主题中的"如何分配用户登录脚本"部分为 Custodians 组配置登录脚本。</span><span class="sxs-lookup"><span data-stu-id="c2a85-225">Configure a logon script for the Custodians group by following the "How to assign user logon scripts" section in the topic, [Using Startup, Shutdown, Logon, and Logoff Scripts in Group Policy](https://go.microsoft.com/fwlink/p/?LinkId=614844).</span></span>
    
2. <span data-ttu-id="c2a85-226">从"安全筛选"中移除经过身份验证的用户并添加 Custodians 组。</span><span class="sxs-lookup"><span data-stu-id="c2a85-226">Remove authenticated users from **Security Filtering**, and add the Custodians group.</span></span>
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a><span data-ttu-id="c2a85-227">PST 导入选项 A，Exchange Server 2013 的脚本</span><span class="sxs-lookup"><span data-stu-id="c2a85-227">PST import Option A, script for Exchange Server 2013</span></span>

1.  <span data-ttu-id="c2a85-228">将以下 Windows PowerShell 脚本复制并粘贴到记事本中：</span><span class="sxs-lookup"><span data-stu-id="c2a85-228">Copy and paste the following Windows PowerShell script into Notepad:</span></span>
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format http://<exchange server FQDN>/Powershell

$ConnectionUri = 'http://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. <span data-ttu-id="c2a85-p115">在易于您查找的位置将脚本另存为 PSTImportScript.ps1。例如，为易于使用，在暂存服务器上创建一个名为 \\\\Staging\\AFCScripts 的文件夹并将脚本保存在其中。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p115">Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.</span></span>
    
3. <span data-ttu-id="c2a85-231">使用记事本中的“转到”功能，根据需要进行以下更改：</span><span class="sxs-lookup"><span data-stu-id="c2a85-231">Use the Go To feature in Notepad, and make the following changes, as needed:</span></span>
    
|<span data-ttu-id="c2a85-232">**行号**</span><span class="sxs-lookup"><span data-stu-id="c2a85-232">**Line #**</span></span>|<span data-ttu-id="c2a85-233">**需更改的内容**</span><span class="sxs-lookup"><span data-stu-id="c2a85-233">**What you need to change**</span></span>|<span data-ttu-id="c2a85-234">**必需/可选**</span><span class="sxs-lookup"><span data-stu-id="c2a85-234">**Required/optional**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="c2a85-235">12 </span><span class="sxs-lookup"><span data-stu-id="c2a85-235">12</span></span>  <br/> |<span data-ttu-id="c2a85-p116">**$FolderIdentifier** 标记在其中导入 PST 的邮箱文件夹。根据需要更改此变量。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p116">**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. </span></span><br/> |<span data-ttu-id="c2a85-238">可选</span><span class="sxs-lookup"><span data-stu-id="c2a85-238">Optional</span></span>  <br/> |
|<span data-ttu-id="c2a85-239">×</span><span class="sxs-lookup"><span data-stu-id="c2a85-239">17</span></span>  <br/> |<span data-ttu-id="c2a85-240">**$ConnectionUri** 需设置为您自己的服务器。</span><span class="sxs-lookup"><span data-stu-id="c2a85-240">**$ConnectionUri** needs to be set to your own server.</span></span> <br/> <span data-ttu-id="c2a85-p117">> [!IMPORTANT]> 确保您的 **$ConnectionUri** 指向 http 位置，而不是 https。它不适用于 https:。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p117">> [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.</span></span>          |<span data-ttu-id="c2a85-243">必需</span><span class="sxs-lookup"><span data-stu-id="c2a85-243">Required</span></span>  <br/> |
   
4. <span data-ttu-id="c2a85-244">确认 Exchange 受信任子系统帐户具有 \\\\Staging\\Cases$ 共享的读取、写入和执行权限。</span><span class="sxs-lookup"><span data-stu-id="c2a85-244">Verify that the Exchange Trusted Subsystem account has Read, Write, and Execute permissions to the \\\\Staging\\Cases$ share.</span></span>
    
5. <span data-ttu-id="c2a85-245">PST 导入脚本需要以下两个输入参数：</span><span class="sxs-lookup"><span data-stu-id="c2a85-245">The PST import script requires the following two input parameters:</span></span>
    
  - <span data-ttu-id="c2a85-246">**$SourcePath** ，要导入的 PST 文件的位置，例如 \\\\Staging\\Cases$。</span><span class="sxs-lookup"><span data-stu-id="c2a85-246">**$SourcePath** The location of the PST files to be imported, for example \\\\Staging\\Cases$.</span></span>
    
  - <span data-ttu-id="c2a85-247">**$MailboxAlias** ，将接收导入的电子邮件的目标邮箱的别名。</span><span class="sxs-lookup"><span data-stu-id="c2a85-247">**$MailboxAlias** The alias of the target mailbox that will receive the imported email items.</span></span>
    
6. <span data-ttu-id="c2a85-248">例如，如果您想将路径 \\Staging\Cases$ 中的所有 PST 文件都导入到别名为 eDiscoveryMailbox 的邮箱，您需要运行与此类似的脚本 `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`。</span><span class="sxs-lookup"><span data-stu-id="c2a85-248">For example, if you want to import all the PST files from the path \\Staging\Cases$ into a mailbox with the alias eDiscoveryMailbox, you would run the script like this `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="c2a85-249">PST 导入选项 B，用于 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c2a85-249">PST Import Option B, for Exchange Online</span></span>

-  <span data-ttu-id="c2a85-p118">创建将放置导入的 PST 文件的邮箱结构。有关在 Exchange Online 中如何创建用户邮箱的详细信息，请参阅[在 Exchange Online 中创建用户邮箱](https://go.microsoft.com/fwlink/p/?LinkId=615118)。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p118">Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).</span></span>
    
### <a name="cold-storage"></a><span data-ttu-id="c2a85-252">冷存储</span><span class="sxs-lookup"><span data-stu-id="c2a85-252">Cold storage</span></span>

1. <span data-ttu-id="c2a85-253">在放置所有收集的文件的 Azure 虚拟机 上创建一个文件共享，例如，\\\\AZFile1\\ContentColdStorage。</span><span class="sxs-lookup"><span data-stu-id="c2a85-253">Create a file share on the Azure Virtual Machine, where all the collected files will be placed, for example, \\\\AZFile1\\ContentColdStorage.</span></span>
    
2. <span data-ttu-id="c2a85-p119">向默认内容访问帐户至少授予对共享以及所有子文件夹和文件的读取权限。有关配置 SharePoint 2013 Search 的详细信息，请参阅[在 SharePoint Server 2013 中创建和配置 Search Service 应用程序](https://go.microsoft.com/fwlink/p/?LinkId=614940)。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p119">Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).</span></span>
    
3. <span data-ttu-id="c2a85-256">如果您预计从 \\\\AZFile1\\ContentColdStorage 导入 PST 文件，请向 Exchange 受信任子系统授予对共享的读取、写入和执行权限。</span><span class="sxs-lookup"><span data-stu-id="c2a85-256">If you anticipate importing PST files from \\\\AZFile1\\ContentColdStorage, grant the Exchange Trusted Subsystem Read, Write, and Execute permissions to the share.</span></span>
    
### <a name="orchestrator"></a><span data-ttu-id="c2a85-257">Orchestrator</span><span class="sxs-lookup"><span data-stu-id="c2a85-257">Orchestrator</span></span>

1. <span data-ttu-id="c2a85-258">从 Microsoft 下载中心下载 [MoveToColdStorage Runbook](https://go.microsoft.com/fwlink/?LinkId=616095)。</span><span class="sxs-lookup"><span data-stu-id="c2a85-258">Download the[ MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) from the Microsoft Download Center.</span></span>
    
2. <span data-ttu-id="c2a85-p120">打开"Runbook Designer"，在"连接"窗格中，单击您想要在其中导入 Runbook 的文件夹。单击"操作"菜单，然后单击"导入"。此时将出现"导入"对话框。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p120">Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.</span></span>
    
3. <span data-ttu-id="c2a85-262">在“文件位置”\*\*\*\* 框中，键入要导入的 Runbook 的路径和文件名，或单击省略号 (**...**) 转到要导入的文件。</span><span class="sxs-lookup"><span data-stu-id="c2a85-262">In the **File Location** box, type the path and file name of the runbook you want to import, or click the ellipsis ( **...**) to browse to the file you want to import.</span></span> 
    
4. <span data-ttu-id="c2a85-p121">依次选择"导入 Runbook"和"导入 Orchestrator 加密数据"。清除"计数器"、"计划"、"变量"、"计算机组"、"导入全局配置"和"覆盖现有全局配置"。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p121">Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.</span></span>
    
5. <span data-ttu-id="c2a85-265">单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c2a85-265">Click **Finish**.</span></span>
    
6. <span data-ttu-id="c2a85-266">编辑 **MoveFilesToColdStorage** 运行手册，如下所述：</span><span class="sxs-lookup"><span data-stu-id="c2a85-266">Edit the **MoveFilesToColdStorage** runbook as follows:</span></span>
    
1. <span data-ttu-id="c2a85-p122">**移动文件**活动 - 将“源文件”\*\*\*\* 路径设置为集合文件共享（例如，\\\\Staging\\cases$）。将“目标文件夹”\*\*\*\* 设置为 Azure 中的冷存储文件共享（例如，\\\\AZFile1\\ContentColdStorage）。选择“创建具有唯一名称的文件”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p122">**Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.</span></span>
    
2. <span data-ttu-id="c2a85-270">**删除文件夹**活动 - 将“路径:”\*\*\*\* 设置为集合文件共享（例如，\\\\Staging\\cases$\\*），再选择“删除所有文件和子文件夹”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c2a85-270">**Delete Folder** activity - Set the **Path:** to the collection file share, for example \\\\Staging\\cases$\\*, and select **Delete all files and sub-folders**.</span></span> 
    
7. <span data-ttu-id="c2a85-271">使用[部署 Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615120) 中的过程部署 **MoveToColdStorage** Runbook。</span><span class="sxs-lookup"><span data-stu-id="c2a85-271">Deploy the **MoveToColdStorage** runbook using the procedures in[Deploying Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120).</span></span>
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a><span data-ttu-id="c2a85-272">冷存储的 SharePoint 本地搜索</span><span class="sxs-lookup"><span data-stu-id="c2a85-272">SharePoint on-premises search for cold storage</span></span>

1. <span data-ttu-id="c2a85-p123">在 SharePoint 2013 服务器场中为 Azure 中的冷存储共享创建一个新的内容源，例如 \\\\AZFile1\\ContentColdStorage。有关管理内容源的详细信息，请参阅[在 SharePoint Server 2013 中添加、编辑或删除内容源](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span><span class="sxs-lookup"><span data-stu-id="c2a85-p123">Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)</span></span>
    
2. <span data-ttu-id="c2a85-p124">启动完整爬网。有关详细信息，请参阅[在 SharePoint Server 2013 中启动、暂停、继续或停止爬网](https://go.microsoft.com/fwlink/p/?LinkId=615005)。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p124">Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
## <a name="using-the-solution"></a><span data-ttu-id="c2a85-277">使用解决方案</span><span class="sxs-lookup"><span data-stu-id="c2a85-277">Using the solution</span></span>

<span data-ttu-id="c2a85-p125">使用此解决方案有五个主要步骤，假定您不希望将 PST 文件导入到 Exchange Server 2013 和 Exchange Online。本部分为您提供了所有这些步骤的过程。您主要在执行以下操作时与解决方案交互：</span><span class="sxs-lookup"><span data-stu-id="c2a85-p125">There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:</span></span>
  
1. <span data-ttu-id="c2a85-281">管理 Custodians 组中的用户成员资格。</span><span class="sxs-lookup"><span data-stu-id="c2a85-281">Manage user membership in the Custodians group.</span></span>
    
2. <span data-ttu-id="c2a85-p126">错误</span><span class="sxs-lookup"><span data-stu-id="c2a85-p126">Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them</span></span>
    
3. <span data-ttu-id="c2a85-285">管理 PST 导入过程。</span><span class="sxs-lookup"><span data-stu-id="c2a85-285">Managing the PST import process.</span></span>
    
4. <span data-ttu-id="c2a85-286">将集合文件移至冷存储。</span><span class="sxs-lookup"><span data-stu-id="c2a85-286">Moving the collection files to cold storage.</span></span>
    
<span data-ttu-id="c2a85-p127">所有其他步骤并非此解决方案所特有。这是您在 SharePoint 2013、Office 365 和 Azure 中执行的标准管理任务。有一些项目此解决方案未提供任何指导，您将需要根据公司的需求进行规划，例如：</span><span class="sxs-lookup"><span data-stu-id="c2a85-p127">All the other steps are not specific to this solution. They are standard administrative tasks that you perform in SharePoint 2013, and Office 365 and Azure. There are items that this solution does not provide any guidance that you will need to work out based on your company's needs, such as:</span></span>
  
1. <span data-ttu-id="c2a85-290">跟踪您的eDiscovery案例，以及哪些保管人与哪个案例关联。</span><span class="sxs-lookup"><span data-stu-id="c2a85-290">Tracking your eDiscovery cases, and which Custodians are associated with which case.</span></span>
    
2. <span data-ttu-id="c2a85-291">跟踪哪些文件集与哪个eDiscovery案例关联。</span><span class="sxs-lookup"><span data-stu-id="c2a85-291">Tracking which sets of file collections are associate with which eDiscovery case.</span></span>
    
3. <span data-ttu-id="c2a85-292">协调导入的时间并转至冷存储步骤。</span><span class="sxs-lookup"><span data-stu-id="c2a85-292">Coordinating the timing of the Import and move to cold storage steps.</span></span>
    
4. <span data-ttu-id="c2a85-293">管理 Azure 中所用的文件空间。</span><span class="sxs-lookup"><span data-stu-id="c2a85-293">Managing the file space used in Azure.</span></span>
    
5. <span data-ttu-id="c2a85-294">管理向其中导入 PST 的邮箱。</span><span class="sxs-lookup"><span data-stu-id="c2a85-294">Managing the mailboxes that PSTs are imported into.</span></span>
    
6. <span data-ttu-id="c2a85-295">备份和还原所有本地数据。</span><span class="sxs-lookup"><span data-stu-id="c2a85-295">Backup and restoration of all on-premises data.</span></span>
    
### <a name="custodian-management"></a><span data-ttu-id="c2a85-296">保管人管理</span><span class="sxs-lookup"><span data-stu-id="c2a85-296">Custodian management</span></span>

- <span data-ttu-id="c2a85-p128">要启动单个用户的自动化文件收集过程，请将其添加到 Custodians 组。 下次用户登录时，将运行通过组策略分配到 Custodians 组的登录脚本。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p128">To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run.</span></span> 
    
### <a name="monitor-collected-files-and-review-log-files"></a><span data-ttu-id="c2a85-299">监控收集的文件和检查日志文件</span><span class="sxs-lookup"><span data-stu-id="c2a85-299">Monitor collected files and review log files</span></span>

1. <span data-ttu-id="c2a85-p129">观察集合文件共享，例如 \\\\Staging\\cases$\\*，查找用户的集合文件夹。文件夹的名称将为以下格式： *yyyyMMddHHmm_UserName*  。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p129">Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .</span></span>
    
2. <span data-ttu-id="c2a85-p130">收集完成后，打开集合文件夹并浏览到 _Log 文件夹。在 _Log 文件夹中，您将看到以下内容：</span><span class="sxs-lookup"><span data-stu-id="c2a85-p130">When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:</span></span>
    
  - <span data-ttu-id="c2a85-p131">用户的计算机上每个本地驱动器的一个 XML 文件，例如 **A.xml** 、 **C.xml** 。这些文件包含按其命名的库存驱动器，且它们用于 robocopy 操作。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p131">One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="c2a85-p132">收集脚本将仅在您在脚本本身定义的文件类型的清单文件中创建一个条目。它不会为用户的计算机上的每个文件都创建一个清单条目。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p132">The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer.</span></span> 
  
  - <span data-ttu-id="c2a85-p133">将运行每个集合的一个名为 FileCopyErrors.log 的日志文件。此文件包含 robocopy 不会复制到文件集合共享的文件列表，例如 \\\\Staging\\cases$\\*。您将需要审核此文件，并确定为这些缺少的文件采取的操作。通常，如果您需要这些文件，您应手动收集它们；您也可以决定不需要它们，因此可将其从收集中忽略。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p133">One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.</span></span>
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a><span data-ttu-id="c2a85-312">PST 导入选项 A，用于 Exchange Server 2013</span><span class="sxs-lookup"><span data-stu-id="c2a85-312">PST import option A for Exchange Server 2013</span></span>

1. <span data-ttu-id="c2a85-p134">登录到承载集合文件共享的服务器上，例如 **Staging** ，然后打开 Windows PowerShell。有关启动 Windows PowerShell 的详细信息，请参阅[在 Windows Server 上启动 Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=615115)。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p134">Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).</span></span>
    
2. <span data-ttu-id="c2a85-p135">将执行策略设置为无限制。将  `Set-ExecutionPolicy Unrestricted -Scope Process` 键入到 Windows PowerShell 中并按 Enter。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p135">Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.</span></span>
    
3. <span data-ttu-id="c2a85-p136">运行 PSTImportScript.ps1 文件，并提供 **$SourcePath** 和 **$MailboxAlias** 参数。有关运行 Windows PowerShell 脚本的详细信息，请参阅[运行脚本](https://go.microsoft.com/fwlink/p/?LinkID=615117)。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p136">Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).</span></span>
    
4. <span data-ttu-id="c2a85-319">查看针对错误的输出。</span><span class="sxs-lookup"><span data-stu-id="c2a85-319">Review the output for errors.</span></span>
    
5. <span data-ttu-id="c2a85-p137">在尝试将一个同名的 PST 文件导入到同一个邮箱之前，必须删除邮箱导入请求。为此，请运行下列命令： `Get-MailboxImportRequest | Remove-MailboxImportRequest`。系统将提示您从队列中删除每个单独的请求。根据需要响应。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p137">Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.</span></span>
    
### <a name="pst-import-option-b-for-exchange-online"></a><span data-ttu-id="c2a85-324">PST 导入选项 B，用于 Exchange Online</span><span class="sxs-lookup"><span data-stu-id="c2a85-324">PST import option B, for Exchange Online</span></span>

- <span data-ttu-id="c2a85-325">若要将收集的 PST 文件放到 Exchange Online 中，请执行 [Office 365 导入服务](https://go.microsoft.com/fwlink/p/?LinkId=614938)的"通过网络上载将文件导入到 Office 365"部分中的步骤。</span><span class="sxs-lookup"><span data-stu-id="c2a85-325">To place the collected PST files into Exchange Online, follow the procedures in the Import files into Office 365 through the network upload section of [Office 365 Import Service](https://go.microsoft.com/fwlink/p/?LinkId=614938).</span></span>
    
### <a name="move-to-cold-storage"></a><span data-ttu-id="c2a85-326">移至冷存储</span><span class="sxs-lookup"><span data-stu-id="c2a85-326">Move to cold storage</span></span>

1. <span data-ttu-id="c2a85-327">使用[运行 Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123) 中的步骤运行 **MoveToColdStorage** Runbook。</span><span class="sxs-lookup"><span data-stu-id="c2a85-327">Run the **MoveToColdStorage** runbook using the procedures in[Running Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123).</span></span>
    
2. <span data-ttu-id="c2a85-p138">观察用于长期存储的 Azure 文件共享（例如 \\\\AZFile1\\ContentColdStorage）和本地集合文件共享（例如 \\\\Staging\\cases$）。您应该会看到文件和文件夹出现在冷存储文件共享中，并从集合文件共享中消失。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p138">Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.</span></span>
    
### <a name="ediscovery"></a><span data-ttu-id="c2a85-330">电子数据展示</span><span class="sxs-lookup"><span data-stu-id="c2a85-330">eDiscovery</span></span>

1. <span data-ttu-id="c2a85-p139">允许冷存储文件共享的完全爬网按计划运行，或者启动爬网。有关启动完全或增量爬网的详细信息，请参阅[在 SharePoint Server 2013 中启动、暂停、继续或停止爬网](https://go.microsoft.com/fwlink/p/?LinkId=615005)。</span><span class="sxs-lookup"><span data-stu-id="c2a85-p139">Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).</span></span>
    
2. <span data-ttu-id="c2a85-333">如果您使用选项 A 进行 PST 文件导入，请在 SharePoint 2013 中创建eDiscovery案例；或者如果您使用选项 B，请在 SharePoint Online 中创建eDiscovery案例。</span><span class="sxs-lookup"><span data-stu-id="c2a85-333">Create an eDiscovery case in SharePoint 2013 if you used option A for a PST file import or create an eDiscovery case in SharePoint Online if you used option B.</span></span>
    

