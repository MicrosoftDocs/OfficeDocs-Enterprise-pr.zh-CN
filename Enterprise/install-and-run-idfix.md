---
title: 下载并运行 Microsoft 365 IdFix 工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: 如何在将 Active Directory 域服务（AD DS）同步到 Microsoft 365 之前，下载并运行 Microsoft 365 IdFix 工具以帮助清理 Active Directory 域服务（AD DS）。
ms.openlocfilehash: c4df63e6162b1d53cb7a45f046542443177b25ff
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774857"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a><span data-ttu-id="a5596-103">下载并运行 Microsoft 365 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="a5596-103">Download and run the Microsoft 365 IdFix tool</span></span>

<span data-ttu-id="a5596-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="a5596-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="a5596-105">IdFix 在同步到 Microsoft 365 之前识别您的 Active Directory 域服务（AD DS）域中的错误（如复制和格式化问题）。</span><span class="sxs-lookup"><span data-stu-id="a5596-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Microsoft 365.</span></span> 
  
<span data-ttu-id="a5596-106">若要成功完成此任务，您应该能够轻松处理 AD DS 中的用户、组和联系人对象。</span><span class="sxs-lookup"><span data-stu-id="a5596-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="a5596-107">如果无法完成此任务，您还可以执行几个其他操作。</span><span class="sxs-lookup"><span data-stu-id="a5596-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="a5596-108">这些方法可能更简单，但它们可能会花费更长或其他缺点。</span><span class="sxs-lookup"><span data-stu-id="a5596-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="a5596-109">具体包括：</span><span class="sxs-lookup"><span data-stu-id="a5596-109">They are:</span></span>
  
- <span data-ttu-id="a5596-110">**在不运行 IdFix 的情况下运行目录同步**</span><span class="sxs-lookup"><span data-stu-id="a5596-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="a5596-111">您可以在不使用 IdFix 工具的情况下同步目录，但我们不建议这样做。</span><span class="sxs-lookup"><span data-stu-id="a5596-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="a5596-112">在同步之前修复错误需要较少的时间，并且通常会使到云的过渡更平稳。</span><span class="sxs-lookup"><span data-stu-id="a5596-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="a5596-113">**雇用顾问**</span><span class="sxs-lookup"><span data-stu-id="a5596-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="a5596-114">获取专家帮助可以让你的用户快速启动并运行，你的目录将同步。</span><span class="sxs-lookup"><span data-stu-id="a5596-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="a5596-115">运行 IdFix 所需的操作</span><span class="sxs-lookup"><span data-stu-id="a5596-115">What you need to run IdFix</span></span>

<span data-ttu-id="a5596-116">获取 IdFix 的最简单方法是将其下载到已加入 AD DS 域的计算机上。</span><span class="sxs-lookup"><span data-stu-id="a5596-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="a5596-117">如果需要，可以在域控制器上运行它，但这并不是必需的。</span><span class="sxs-lookup"><span data-stu-id="a5596-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="a5596-118">IdFix 硬件要求</span><span class="sxs-lookup"><span data-stu-id="a5596-118">IdFix hardware requirements</span></span>

<span data-ttu-id="a5596-119">您在其中下载 IdFix 的计算机需要满足以下最低硬件要求：</span><span class="sxs-lookup"><span data-stu-id="a5596-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="a5596-120">4 GB RAM</span><span class="sxs-lookup"><span data-stu-id="a5596-120">4 GB RAM</span></span>
- <span data-ttu-id="a5596-121">2 GB 的硬盘空间</span><span class="sxs-lookup"><span data-stu-id="a5596-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="a5596-122">IdFix 软件要求</span><span class="sxs-lookup"><span data-stu-id="a5596-122">IdFix software requirements</span></span>

<span data-ttu-id="a5596-123">需要将 IdFix 下载到的计算机连接到要将用户同步到 Microsoft 365 的同一 AD DS 域。</span><span class="sxs-lookup"><span data-stu-id="a5596-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Microsoft 365.</span></span> 

<span data-ttu-id="a5596-124">计算机还需要安装 .NET Framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="a5596-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="a5596-125">如果您运行的是 Windows Server 2008 或更高版本，则可能已安装 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="a5596-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="a5596-126">如果不是，则可以从下载中心或 Windows Update[下载 .net 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475) 。</span><span class="sxs-lookup"><span data-stu-id="a5596-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="a5596-127">IdFix 权限要求</span><span class="sxs-lookup"><span data-stu-id="a5596-127">IdFix permissions requirements</span></span>

<span data-ttu-id="a5596-128">您用于运行 IdFix 的用户帐户必须具有对 AD DS 域的读取和写入权限。</span><span class="sxs-lookup"><span data-stu-id="a5596-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="a5596-129">如果您不确定您的用户帐户是否满足这些要求，并且不确定如何进行检查，您仍可以下载并运行 IdFix。</span><span class="sxs-lookup"><span data-stu-id="a5596-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="a5596-130">如果您的用户帐户没有适当的权限，则 IdFix 将在您尝试运行它时只显示错误。</span><span class="sxs-lookup"><span data-stu-id="a5596-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="a5596-131">下载并解压缩 IdFix</span><span class="sxs-lookup"><span data-stu-id="a5596-131">Download and extract IdFix</span></span>

<span data-ttu-id="a5596-132">请按照以下说明操作。</span><span class="sxs-lookup"><span data-stu-id="a5596-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="a5596-133">登录到您要在其中运行 IdFix 工具的计算机。</span><span class="sxs-lookup"><span data-stu-id="a5596-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="a5596-134">转到[IdFix DirSync 错误修正工具](https://github.com/microsoft/idfix)网站。</span><span class="sxs-lookup"><span data-stu-id="a5596-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="a5596-135">单击 " **ClickOnce 启动**" 部分中的 "**启动**" 以下载 zip 文件。</span><span class="sxs-lookup"><span data-stu-id="a5596-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="a5596-136">打开 zip 文件。</span><span class="sxs-lookup"><span data-stu-id="a5596-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="a5596-137">在 " **IdFix** " 窗口中，选择 "**提取**"，然后 "**全部提取**"。</span><span class="sxs-lookup"><span data-stu-id="a5596-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="a5596-138">默认情况下，IdFix 被提取到 `C:\Users\<your user name>\Documents\IdFix` 。</span><span class="sxs-lookup"><span data-stu-id="a5596-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="a5596-139">选择“**提取**”。</span><span class="sxs-lookup"><span data-stu-id="a5596-139">Choose **Extract**.</span></span>

<span data-ttu-id="a5596-140">你的步骤可能因你的 Windows 和 Internet 浏览器的版本而异。</span><span class="sxs-lookup"><span data-stu-id="a5596-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="a5596-141">运行 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="a5596-141">Run the IdFix tool</span></span>

<span data-ttu-id="a5596-142">下载并解压缩 IdFix 后，运行它以搜索 AD DS 域中的问题。</span><span class="sxs-lookup"><span data-stu-id="a5596-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="a5596-143">使用具有对 AD DS 域的读/写访问权限的帐户登录到已下载 IdFix 的计算机。</span><span class="sxs-lookup"><span data-stu-id="a5596-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="a5596-144">在文件资源管理器中，转到您在其中提取 IdFix 的位置。</span><span class="sxs-lookup"><span data-stu-id="a5596-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="a5596-145">如果在提取过程中选择了默认文件夹，请转到 `C:\Users\<your user name>\Documents\IdFix` 。</span><span class="sxs-lookup"><span data-stu-id="a5596-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="a5596-146">双击 " **IdFix.exe**"。</span><span class="sxs-lookup"><span data-stu-id="a5596-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="a5596-147">默认情况下，IdFix 使用多租户规则集测试目录中的条目。</span><span class="sxs-lookup"><span data-stu-id="a5596-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="a5596-148">这是大多数 Microsoft 365 客户的正确规则集。</span><span class="sxs-lookup"><span data-stu-id="a5596-148">This is the right rule set for most Microsoft 365 customers.</span></span> <span data-ttu-id="a5596-149">但是，如果您是一台 Microsoft 365 专用或国际流量（在 Arm 规章（ITAR））客户，则可以将 IdFix 配置为改用专用规则集。</span><span class="sxs-lookup"><span data-stu-id="a5596-149">However, if you are a Microsoft 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="a5596-150">如果您不确定您是哪种类型的客户，则可以安全地跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="a5596-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="a5596-151">若要将规则集设置为专用，请单击菜单栏中的齿轮图标，然后选择 "**专用**"。</span><span class="sxs-lookup"><span data-stu-id="a5596-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="a5596-152">选择 "**查询**"。</span><span class="sxs-lookup"><span data-stu-id="a5596-152">Choose **Query**.</span></span>
    
    ![在 IdFix 中选择 "查询"。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="a5596-154">默认情况下，IdFix 会搜索整个目录中是否有错误。</span><span class="sxs-lookup"><span data-stu-id="a5596-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="a5596-155">运行查询可能需要一段时间，具体取决于目录的大小。</span><span class="sxs-lookup"><span data-stu-id="a5596-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="a5596-156">您可以在该工具的主窗口的底部观看进度。</span><span class="sxs-lookup"><span data-stu-id="a5596-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="a5596-157">如果单击 "**取消**"，则需要从头开始重新启动。</span><span class="sxs-lookup"><span data-stu-id="a5596-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="a5596-158">在 IdFix 完成查询后，如果没有任何错误，则可以同步您的目录。</span><span class="sxs-lookup"><span data-stu-id="a5596-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="a5596-159">如果目录中有错误，建议您在同步之前对其进行修复。</span><span class="sxs-lookup"><span data-stu-id="a5596-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="a5596-160">有关详细信息，请参阅[准备与 Microsoft 365 同步的目录属性](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="a5596-160">See [prepare directory attributes for synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="a5596-161">虽然不强制在同步之前修复这些错误，但强烈建议您至少查看 IdFix 返回的所有错误。</span><span class="sxs-lookup"><span data-stu-id="a5596-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="a5596-162">每个错误都显示在该工具的主窗口中的单独行中。</span><span class="sxs-lookup"><span data-stu-id="a5596-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="a5596-163">如果您同意 "**更新**" 列中的 "建议的更改"，则在 "**操作**" 列中选择您希望 IdFix 实现更改所要执行的操作，然后单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="a5596-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="a5596-164">当您单击 "**应用**" 时，该工具会在目录中进行更改。</span><span class="sxs-lookup"><span data-stu-id="a5596-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="a5596-165">无需在每次更新后单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="a5596-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="a5596-166">相反，您可以先修复几个错误，然后再单击 "**应用**"，IdFix 将同时更改所有这些错误。</span><span class="sxs-lookup"><span data-stu-id="a5596-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="a5596-167">您可以通过单击列出错误类型的列顶部的 "**错误**"，按错误类型对错误进行排序。</span><span class="sxs-lookup"><span data-stu-id="a5596-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="a5596-168">一种策略是修复相同类型的所有错误;例如，先修复所有重复项，并应用它们。</span><span class="sxs-lookup"><span data-stu-id="a5596-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="a5596-169">接下来，修复字符格式错误，等等。</span><span class="sxs-lookup"><span data-stu-id="a5596-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="a5596-170">每次应用更改时，IdFix 工具都会创建一个单独的日志文件，您可以使用该文件来撤消所做的更改，以防您犯错误。</span><span class="sxs-lookup"><span data-stu-id="a5596-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="a5596-171">[事务日志](idfix-transaction-log.md)存储在提取 IdFix 的文件夹中，默认情况下为_C:\Users \<your user name> \Documents\IdFix_ 。</span><span class="sxs-lookup"><span data-stu-id="a5596-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![修正 IdFix 中的错误。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="a5596-173">对目录进行所有更改后，再次运行 IdFix 以确保您所做的修补程序未引入新的错误。</span><span class="sxs-lookup"><span data-stu-id="a5596-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="a5596-174">您可以根据需要多次重复这些步骤。</span><span class="sxs-lookup"><span data-stu-id="a5596-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="a5596-175">在同步之前，最好先完成几次此过程。</span><span class="sxs-lookup"><span data-stu-id="a5596-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="a5596-176">IdFix 上的其他资源</span><span class="sxs-lookup"><span data-stu-id="a5596-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="a5596-177">IdFix 排除和支持的对象和属性</span><span class="sxs-lookup"><span data-stu-id="a5596-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="a5596-178">Microsoft 365 IdFix 事务日志</span><span class="sxs-lookup"><span data-stu-id="a5596-178">Microsoft 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
