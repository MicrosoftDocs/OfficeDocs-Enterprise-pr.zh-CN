---
title: 下载并运行 Microsoft 365 IdFix 工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Priority
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
description: 如何下载并运行 Microsoft 365 IdFix 工具，帮助清理你的 Active Directory 域服务 (AD DS)，然后再将其同步到 Microsoft 365。
ms.openlocfilehash: beef13857ad00806cc3e62aedd7a1b3c48bfe4c0
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502657"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a><span data-ttu-id="73d85-103">下载并运行 Microsoft 365 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="73d85-103">Download and run the Microsoft 365 IdFix tool</span></span>

<span data-ttu-id="73d85-104">*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*</span><span class="sxs-lookup"><span data-stu-id="73d85-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="73d85-105">IdFix 可标识在同步到 Microsoft 365 之前 Active Directory 域服务 (AD DS) 域中的错误，例如重复项和格式设置问题。</span><span class="sxs-lookup"><span data-stu-id="73d85-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Microsoft 365.</span></span> 
  
<span data-ttu-id="73d85-106">要成功完成此任务，应该小心地使用 AD DS 中的用户、组和联系人对象。</span><span class="sxs-lookup"><span data-stu-id="73d85-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="73d85-107">如果无法完成此任务，可以执行一些其他操作。</span><span class="sxs-lookup"><span data-stu-id="73d85-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="73d85-108">这些方法可能更简单，但可能还会花费更长时间，也可能有一些其他缺点。</span><span class="sxs-lookup"><span data-stu-id="73d85-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="73d85-109">具体包括：</span><span class="sxs-lookup"><span data-stu-id="73d85-109">They are:</span></span>
  
- <span data-ttu-id="73d85-110">**在不运行 IdFix 的情况下运行目录同步**</span><span class="sxs-lookup"><span data-stu-id="73d85-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="73d85-111">可以在不使用 IdFix 工具的情况下同步目录，但不建议这样做。</span><span class="sxs-lookup"><span data-stu-id="73d85-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="73d85-112">在同步之前修复错误花费的时间会少一些，这往往可以帮助顺利过渡到云。</span><span class="sxs-lookup"><span data-stu-id="73d85-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="73d85-113">**聘请顾问**</span><span class="sxs-lookup"><span data-stu-id="73d85-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="73d85-114">获得专家的帮助可以让你的用户正常工作并提高运行速度，使你的目录顺利实现同步。</span><span class="sxs-lookup"><span data-stu-id="73d85-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="73d85-115">运行 IdFix 的前提条件</span><span class="sxs-lookup"><span data-stu-id="73d85-115">What you need to run IdFix</span></span>

<span data-ttu-id="73d85-116">启动并运行 IdFix 最简单的方法是将其下载到已加入你的 AD DS 域中的计算机上。</span><span class="sxs-lookup"><span data-stu-id="73d85-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="73d85-117">如需要，可以在域控制器上运行它，但这不是必需的。</span><span class="sxs-lookup"><span data-stu-id="73d85-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="73d85-118">IdFix 硬件要求</span><span class="sxs-lookup"><span data-stu-id="73d85-118">IdFix hardware requirements</span></span>

<span data-ttu-id="73d85-119">用于下载 IdFix 的计算机需要满足以下最低硬件要求：</span><span class="sxs-lookup"><span data-stu-id="73d85-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="73d85-120">4 GB RAM</span><span class="sxs-lookup"><span data-stu-id="73d85-120">4 GB RAM</span></span>
- <span data-ttu-id="73d85-121">2 GB 的硬盘空间</span><span class="sxs-lookup"><span data-stu-id="73d85-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="73d85-122">IdFix 软件要求</span><span class="sxs-lookup"><span data-stu-id="73d85-122">IdFix software requirements</span></span>

<span data-ttu-id="73d85-123">你下载了 IdFix 的计算机需要加入到你要将用户同步到 Microsoft 365 所在的同一个 AD DS 域中。</span><span class="sxs-lookup"><span data-stu-id="73d85-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Microsoft 365.</span></span> 

<span data-ttu-id="73d85-124">该计算机也需要安装有 .NET Framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="73d85-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="73d85-125">如果你运行的是 Windows Server 2008 或更高版本，那么很可能已经安装了 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="73d85-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="73d85-126">如果没有，可以[从下载中心下载 .NET 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475) 或通过 Windows 更新进行下载。</span><span class="sxs-lookup"><span data-stu-id="73d85-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="73d85-127">IdFix 权限要求</span><span class="sxs-lookup"><span data-stu-id="73d85-127">IdFix permissions requirements</span></span>

<span data-ttu-id="73d85-128">用于运行 IdFix 的用户帐户必须对 AD DS 域具有读取和写入访问权限。</span><span class="sxs-lookup"><span data-stu-id="73d85-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="73d85-129">如果你还不清楚你的用户帐户是否满足这些要求，也不知道要如何检查，仍可以下载和运行 IdFix。</span><span class="sxs-lookup"><span data-stu-id="73d85-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="73d85-130">如果你的用户帐户不具有正确的权限，当你尝试运行 IdFix 时，IdFix 只会显示一个错误。</span><span class="sxs-lookup"><span data-stu-id="73d85-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="73d85-131">下载并提取 IdFix</span><span class="sxs-lookup"><span data-stu-id="73d85-131">Download and extract IdFix</span></span>

<span data-ttu-id="73d85-132">按照以下说明操作。</span><span class="sxs-lookup"><span data-stu-id="73d85-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="73d85-133">登录到要运行 IdFix 工具的计算机。</span><span class="sxs-lookup"><span data-stu-id="73d85-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="73d85-134">转到 [IdFix DirSync 错误修正工具](https://github.com/microsoft/idfix)网站。</span><span class="sxs-lookup"><span data-stu-id="73d85-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="73d85-135">在“ClickOnce 启动”部分中单击“启动”以下载 zip 文件\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73d85-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="73d85-136">打开 zip 文件。</span><span class="sxs-lookup"><span data-stu-id="73d85-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="73d85-137">在“IdFix”窗口中，依次选择“提取”、“全部提取”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73d85-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="73d85-138">默认情况下，IdFix 将被提取到 `C:\Users\<your user name>\Documents\IdFix`。</span><span class="sxs-lookup"><span data-stu-id="73d85-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="73d85-139">选择“提取”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73d85-139">Choose **Extract**.</span></span>

<span data-ttu-id="73d85-140">根据使用的 Windows 和 Internet 浏览器的版本，具体步骤可能会有所差异。</span><span class="sxs-lookup"><span data-stu-id="73d85-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="73d85-141">运行 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="73d85-141">Run the IdFix tool</span></span>

<span data-ttu-id="73d85-142">下载并提取 IdFix 后，运行它以搜索 AD DS 域中的问题。</span><span class="sxs-lookup"><span data-stu-id="73d85-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="73d85-143">使用对 AD DS 域具有读取/写入访问权限的帐户，登录到已下载 IdFix 的计算机。</span><span class="sxs-lookup"><span data-stu-id="73d85-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="73d85-144">在文件资源管理器中，转到你提取了 IdFix 的位置。</span><span class="sxs-lookup"><span data-stu-id="73d85-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="73d85-145">如果在提取过程中选择了默认文件夹，则转到 `C:\Users\<your user name>\Documents\IdFix`。</span><span class="sxs-lookup"><span data-stu-id="73d85-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="73d85-146">双击“IdFix.exe”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73d85-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="73d85-147">默认情况下，IdFix 使用多租户规则集来测试你的目录中的条目。</span><span class="sxs-lookup"><span data-stu-id="73d85-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="73d85-148">这是适用于大多数 Microsoft 365 客户的正确规则集。</span><span class="sxs-lookup"><span data-stu-id="73d85-148">This is the right rule set for most Microsoft 365 customers.</span></span> <span data-ttu-id="73d85-149">但是，如果你是 Microsoft 365 专用客户，或是国际武器贸易条例 (ITAR) 客户，可以将 IdFix 配置为使用专用的规则集。</span><span class="sxs-lookup"><span data-stu-id="73d85-149">However, if you are a Microsoft 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="73d85-150">如果你不知道自己是什么类型的客户，可以跳过这一步。</span><span class="sxs-lookup"><span data-stu-id="73d85-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="73d85-151">要将规则集设置为专用规则集，请单击菜单栏上的齿轮图标，然后选择“专用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73d85-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="73d85-152">选择“查询”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73d85-152">Choose **Query**.</span></span>
    
    ![在 IdFix 中选择查询。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="73d85-154">默认情况下，IdFix 将搜索整个目录中的错误。</span><span class="sxs-lookup"><span data-stu-id="73d85-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="73d85-155">根据你的目录的大小，运行查询可能需要花些时间。</span><span class="sxs-lookup"><span data-stu-id="73d85-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="73d85-156">可以在工具的主窗口底部观察进度。</span><span class="sxs-lookup"><span data-stu-id="73d85-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="73d85-157">如果单击“取消”\*\*\*\*，就需要从头重新开始。</span><span class="sxs-lookup"><span data-stu-id="73d85-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="73d85-158">IdFix 完成查询之后，如果没有错误，则可以同步目录。</span><span class="sxs-lookup"><span data-stu-id="73d85-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="73d85-159">如果你的目录中有错误，建议在同步之前先修复这些错误。</span><span class="sxs-lookup"><span data-stu-id="73d85-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="73d85-160">有关详细信息，请参阅[准备目录属性进行与 Microsoft 365 的同步](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="73d85-160">See [prepare directory attributes for synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="73d85-161">虽然并不强制在同步之前修复错误，但强烈建议至少检查一下由 IdFix 返回的所有错误。</span><span class="sxs-lookup"><span data-stu-id="73d85-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="73d85-162">每个错误均显示在工具主窗口中的单独行内。</span><span class="sxs-lookup"><span data-stu-id="73d85-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="73d85-163">如果你同意“更新”\*\*\*\* 列中的更改建议，请在“操作”\*\*\*\* 列中选择 IdFix 要实现此更改应执行的操作，然后单击“应用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73d85-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="73d85-164">单击“应用”\*\*\*\* 时，工具将在目录中进行更改。</span><span class="sxs-lookup"><span data-stu-id="73d85-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="73d85-165">不必在每次更新后都单击“应用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="73d85-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="73d85-166">相反，可以在单击“应用”\*\*\*\* 之前修复一些错误，IdFix 会同时对它们做出更改。</span><span class="sxs-lookup"><span data-stu-id="73d85-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="73d85-167">在列出错误类型的列的顶部，可单击“错误”\*\*\*\* 按错误类型进行错误排序。</span><span class="sxs-lookup"><span data-stu-id="73d85-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="73d85-168">一种策略是修复同一类型的所有错误；例如，首先修复所有重复错误，然后再应用它们。</span><span class="sxs-lookup"><span data-stu-id="73d85-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="73d85-169">接着，修复字符格式错误，等等。</span><span class="sxs-lookup"><span data-stu-id="73d85-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="73d85-170">每次应用更改时，IdFix 工具都会创建一个单独的日志文件，在出错时，就可以用它来撤消所做的更改。</span><span class="sxs-lookup"><span data-stu-id="73d85-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="73d85-171">[事务日志](idfix-transaction-log.md)存储在你提取了 IdFix 的文件夹中，默认情况下为 _C:\Users\<your user name>\Documents\IdFix_。</span><span class="sxs-lookup"><span data-stu-id="73d85-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![在 IdFix 中修正错误。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="73d85-173">对目录执行完所有的更改之后，请再次运行 IdFix 以确保所做的修复没有引入新的错误。</span><span class="sxs-lookup"><span data-stu-id="73d85-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="73d85-174">可以根据需要多次重复这些步骤。</span><span class="sxs-lookup"><span data-stu-id="73d85-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="73d85-175">在进行同步之前，最好多次演练此过程。</span><span class="sxs-lookup"><span data-stu-id="73d85-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="73d85-176">IdFix 上的其他资源</span><span class="sxs-lookup"><span data-stu-id="73d85-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="73d85-177">IdFix 排除和支持的对象和属性</span><span class="sxs-lookup"><span data-stu-id="73d85-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="73d85-178">Microsoft 365 IdFix 事务日志</span><span class="sxs-lookup"><span data-stu-id="73d85-178">Microsoft 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
