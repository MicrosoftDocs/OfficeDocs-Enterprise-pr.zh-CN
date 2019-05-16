---
title: 安装和运行 Office 365 IdFix 工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: 如何在将 active directory 同步到 Office 365 之前安装和运行 Office 365 IdFix 工具以帮助清理 active directory。
ms.openlocfilehash: 4197694ce90ab600652aa729809ef0ddb0647e03
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067288"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="01425-103">安装和运行 Office 365 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="01425-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="01425-104">IdFix 在同步到 Office 365 之前识别目录中的错误 (如复制和格式问题)。</span><span class="sxs-lookup"><span data-stu-id="01425-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="01425-105">若要成功完成此任务, 您应该能够轻松处理 Active Directory 中的用户、组和联系人对象。</span><span class="sxs-lookup"><span data-stu-id="01425-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="01425-106">如果无法完成此任务, 您还可以执行几个其他操作。</span><span class="sxs-lookup"><span data-stu-id="01425-106">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="01425-107">这些方法可能更简单, 但它们可能会花费更长或其他缺点。</span><span class="sxs-lookup"><span data-stu-id="01425-107">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="01425-108">具体包括：</span><span class="sxs-lookup"><span data-stu-id="01425-108">They are:</span></span>
  
- <span data-ttu-id="01425-109">**在不运行 IdFix 的情况下运行目录同步。**</span><span class="sxs-lookup"><span data-stu-id="01425-109">**Run directory synchronization without running IdFix.**</span></span> <span data-ttu-id="01425-110">您可以在不运行 IdFix 工具的情况下同步目录, 但我们不建议这样做。</span><span class="sxs-lookup"><span data-stu-id="01425-110">You can synchronize your directory without running the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="01425-111">在同步之前修复错误需要较少的时间, 并且通常会使到云的过渡更平稳。</span><span class="sxs-lookup"><span data-stu-id="01425-111">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="01425-112">**雇用顾问。**</span><span class="sxs-lookup"><span data-stu-id="01425-112">**Hire a consultant.**</span></span> <span data-ttu-id="01425-113">获取专家帮助可以让你的用户快速启动并运行, 你的目录将同步。</span><span class="sxs-lookup"><span data-stu-id="01425-113">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="01425-114">运行 IdFix 所需的操作</span><span class="sxs-lookup"><span data-stu-id="01425-114">What you need to run IdFix</span></span>

<span data-ttu-id="01425-115">获取和运行 IdFix 的最简单方法是将其安装在加入您的域的计算机上。</span><span class="sxs-lookup"><span data-stu-id="01425-115">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain.</span></span> <span data-ttu-id="01425-116">如果需要, 可以在域控制器上运行它, 但这并不是必需的。</span><span class="sxs-lookup"><span data-stu-id="01425-116">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="01425-117">IdFix 硬件要求</span><span class="sxs-lookup"><span data-stu-id="01425-117">IdFix hardware requirements</span></span>

<span data-ttu-id="01425-118">您在其上安装 IdFix 的计算机需要满足以下最低硬件要求:</span><span class="sxs-lookup"><span data-stu-id="01425-118">The computer where you install IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="01425-119">4 GB RAM</span><span class="sxs-lookup"><span data-stu-id="01425-119">4 GB RAM</span></span>
- <span data-ttu-id="01425-120">2 GB 的硬盘空间</span><span class="sxs-lookup"><span data-stu-id="01425-120">2 GB of hard disk space</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="01425-121">IdFix 软件要求</span><span class="sxs-lookup"><span data-stu-id="01425-121">IdFix software requirements</span></span>

<span data-ttu-id="01425-122">需要将 IdFix 安装到的计算机连接到要将用户同步到 Office 365 的同一 Active Directory 域。</span><span class="sxs-lookup"><span data-stu-id="01425-122">The computer where you install IdFix needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365.</span></span> <span data-ttu-id="01425-123">计算机还需要安装 .NET Framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="01425-123">The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="01425-124">如果您运行的是 Windows Server 2008 或 Windows Server 2012, 则可能已安装 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="01425-124">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed.</span></span> <span data-ttu-id="01425-125">如果不是, 则可以从下载中心或通过 Windows Update[下载 .net 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475) 。</span><span class="sxs-lookup"><span data-stu-id="01425-125">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or via Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="01425-126">IdFix 权限要求</span><span class="sxs-lookup"><span data-stu-id="01425-126">IdFix permissions requirements</span></span>

<span data-ttu-id="01425-127">您用于运行 IdFix 的用户帐户需要具有对该目录的读/写访问权限。</span><span class="sxs-lookup"><span data-stu-id="01425-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="01425-128">如果您不确定您的用户帐户是否满足这些要求, 并且不确定如何进行检查, 则仍可以安装和运行 IdFix。</span><span class="sxs-lookup"><span data-stu-id="01425-128">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix.</span></span> <span data-ttu-id="01425-129">如果您的用户帐户没有适当的权限, 则 IdFix 将在您尝试运行它时只显示错误。</span><span class="sxs-lookup"><span data-stu-id="01425-129">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="01425-130">安装 IdFix</span><span class="sxs-lookup"><span data-stu-id="01425-130">Install IdFix</span></span>

<span data-ttu-id="01425-131">若要安装 IdFix, 请下载并解压缩**IdFix**:</span><span class="sxs-lookup"><span data-stu-id="01425-131">To install IdFix, download and unzip **IdFix.exe**:</span></span> 
  
1. <span data-ttu-id="01425-132">登录到要安装 IdFix 工具的计算机。</span><span class="sxs-lookup"><span data-stu-id="01425-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="01425-133">请转到 Microsoft 下载中心网站, 获取[IdFix DirSync 错误修正工具](https://go.microsoft.com/fwlink/?linkid=867219)。</span><span class="sxs-lookup"><span data-stu-id="01425-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="01425-134">选择“下载”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="01425-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="01425-135">出现提示时, 选择 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="01425-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="01425-136">在 " **WinZip 自动解压缩程序**" 对话框的 "**解压缩到文件夹**" 文本框中, 键入或浏览到要安装 IdFix 工具的位置。</span><span class="sxs-lookup"><span data-stu-id="01425-136">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool.</span></span> <span data-ttu-id="01425-137">默认情况下, IdFix 安装到`C:\Deployment Tools\`。</span><span class="sxs-lookup"><span data-stu-id="01425-137">By default, IdFix is installed into `C:\Deployment Tools\`.</span></span> 
    
6. <span data-ttu-id="01425-138">选择 "**解压缩**"。</span><span class="sxs-lookup"><span data-stu-id="01425-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="01425-139">运行 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="01425-139">Run the IdFix tool</span></span>

<span data-ttu-id="01425-140">安装 IdFix 后, 运行该工具以搜索目录中的问题:</span><span class="sxs-lookup"><span data-stu-id="01425-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="01425-141">使用具有对目录的读/写访问权限的帐户登录到安装了 IdFix 的计算机。</span><span class="sxs-lookup"><span data-stu-id="01425-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="01425-142">在文件资源管理器中, 转到安装 IdFix 的位置。</span><span class="sxs-lookup"><span data-stu-id="01425-142">In File Explorer, go to the location where you installed IdFix.</span></span> <span data-ttu-id="01425-143">如果您在安装过程中选择了默认文件夹, `C:\Deployment Tools\IdFix`请转到。</span><span class="sxs-lookup"><span data-stu-id="01425-143">If you chose the default folder during installation, go to `C:\Deployment Tools\IdFix`.</span></span>
    
3. <span data-ttu-id="01425-144">双击 " **IdFix**"。</span><span class="sxs-lookup"><span data-stu-id="01425-144">Double-click **IdFix.exe**.</span></span> 
    
    ![选择 "IdFix" 文件。](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="01425-146">默认情况下, IdFix 使用多租户规则集测试目录中的条目。</span><span class="sxs-lookup"><span data-stu-id="01425-146">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="01425-147">这是大多数 Office 365 客户的正确规则集。</span><span class="sxs-lookup"><span data-stu-id="01425-147">This is the right rule set for most Office 365 customers.</span></span> <span data-ttu-id="01425-148">但是, 如果您是 Office 365 专用或 ITAR (Arm 规章中的国际流量) 客户, 则可以将 IdFix 配置为改用专用规则集。</span><span class="sxs-lookup"><span data-stu-id="01425-148">However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="01425-149">如果您不确定您是哪种类型的客户, 则可以安全地跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="01425-149">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="01425-150">若要将规则集设置为专用, 请单击菜单栏中的齿轮图标, 然后选择 "**专用**"。</span><span class="sxs-lookup"><span data-stu-id="01425-150">To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="01425-151">选择 "**查询**"。</span><span class="sxs-lookup"><span data-stu-id="01425-151">Choose **Query**.</span></span>
    
    ![在 IdFix 中选择 "查询"。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="01425-153">默认情况下, IdFix 会搜索整个目录中是否有错误。</span><span class="sxs-lookup"><span data-stu-id="01425-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="01425-154">运行查询可能需要一段时间, 具体取决于目录的大小。</span><span class="sxs-lookup"><span data-stu-id="01425-154">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="01425-155">您可以在该工具的主窗口的底部观看进度。</span><span class="sxs-lookup"><span data-stu-id="01425-155">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="01425-156">如果单击 "**取消**", 则需要从头开始重新启动。</span><span class="sxs-lookup"><span data-stu-id="01425-156">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![IdFix 查询和错误计数。](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="01425-158">完成查询后, 如果没有任何错误, 则可以继续并同步您的目录。</span><span class="sxs-lookup"><span data-stu-id="01425-158">After IdFix completes the query, you can go ahead and synchronize your directory if there are no errors.</span></span> <span data-ttu-id="01425-159">如果目录中有错误, 建议您在同步之前对其进行修复。</span><span class="sxs-lookup"><span data-stu-id="01425-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="01425-160">如果您需要有关错误类型的更多具体信息, 以及有关修复每个错误的最佳方法的建议, 请参阅本主题末尾的链接。</span><span class="sxs-lookup"><span data-stu-id="01425-160">If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="01425-161">虽然不强制在同步之前修复这些错误, 但强烈建议您至少查看 IdFix 返回的所有错误。</span><span class="sxs-lookup"><span data-stu-id="01425-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="01425-162">每个错误都显示在该工具的主窗口中的单独行中。</span><span class="sxs-lookup"><span data-stu-id="01425-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="01425-163">如果您同意 "**更新**" 列中的 "建议的更改", 则在 "**操作**" 列中选择您希望 IdFix 实现更改所要执行的操作, 然后单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="01425-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="01425-164">当您单击 "**应用**" 时, 该工具会在目录中进行更改。</span><span class="sxs-lookup"><span data-stu-id="01425-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="01425-165">无需在每次更新后单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="01425-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="01425-166">相反, 您可以先修复几个错误, 然后再单击 "**应用**", IdFix 将同时更改所有这些错误。</span><span class="sxs-lookup"><span data-stu-id="01425-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="01425-167">您可以通过单击列出错误类型的列顶部的 "**错误**", 按错误类型对错误进行排序。</span><span class="sxs-lookup"><span data-stu-id="01425-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="01425-168">一种策略是修复相同类型的所有错误;例如, 先修复所有重复项, 并应用它们。</span><span class="sxs-lookup"><span data-stu-id="01425-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="01425-169">接下来, 修复字符格式错误, 等等。</span><span class="sxs-lookup"><span data-stu-id="01425-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="01425-170">每次应用更改时, IdFix 工具都会创建一个单独的日志文件, 您可以使用该文件来撤消所做的更改, 以防您犯错误。</span><span class="sxs-lookup"><span data-stu-id="01425-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="01425-171">[事务日志](idfix-transaction-log.md)存储在 IdFix 中安装的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="01425-171">The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.</span></span>  <span data-ttu-id="01425-172">默认情况下, _C:\Deployment Tools\IdFix_ 。</span><span class="sxs-lookup"><span data-stu-id="01425-172">_C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![修正 IdFix 中的错误。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="01425-174">对目录进行所有更改后, 再次运行 IdFix 以确保您所做的修补程序未引入新的错误。</span><span class="sxs-lookup"><span data-stu-id="01425-174">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="01425-175">您可以根据需要多次重复这些步骤。</span><span class="sxs-lookup"><span data-stu-id="01425-175">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="01425-176">在同步之前, 最好先完成几次此过程。</span><span class="sxs-lookup"><span data-stu-id="01425-176">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="01425-177">我想要精简我的搜索或深入研究错误, 我还可以使用 IdFix 进行哪些操作？</span><span class="sxs-lookup"><span data-stu-id="01425-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="01425-178">以下主题提供了更深入的信息:</span><span class="sxs-lookup"><span data-stu-id="01425-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="01425-179">[使用 IdFix 工具准备要与 Office 365 同步的目录属性](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="01425-179">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) .</span></span> <span data-ttu-id="01425-180">安装该工具后, 请跳转到本主题, 以获取有关运行该工具的更多详细说明、您将遇到的常见错误、建议的修补程序、示例和最佳做法, 以了解在遇到大量错误时应采取的操作。</span><span class="sxs-lookup"><span data-stu-id="01425-180">After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="01425-181">参考：IdFix 排除和支持的对象和属性</span><span class="sxs-lookup"><span data-stu-id="01425-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="01425-182">参考：Office 365 IdFix 事务日志</span><span class="sxs-lookup"><span data-stu-id="01425-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="01425-183">视频培训</span><span class="sxs-lookup"><span data-stu-id="01425-183">Video training</span></span>

<span data-ttu-id="01425-184">有关详细信息, 请参阅 LinkedIn[安装和使用 IDFix 工具, 此](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US)课程由 LinkedIn 学习版提供。</span><span class="sxs-lookup"><span data-stu-id="01425-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

