---
title: 安装并运行 Office 365 IdFix 工具
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: 如何安装和运行 Office 365 IdFix 工具以帮助清理您的 active directory 同步到 Office 365 之前。
ms.openlocfilehash: 642273c0171603d627a19273a78fe66662f4caaf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539553"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="a576b-103">安装并运行 Office 365 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="a576b-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="a576b-104">同步到 Office 365 之前，IdFix 标识错误例如重复项和在您的目录的格式问题。</span><span class="sxs-lookup"><span data-stu-id="a576b-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="a576b-105">要成功完成此任务，您应该能够轻松处理用户、 组和 Active Directory 中的联系人对象。</span><span class="sxs-lookup"><span data-stu-id="a576b-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="a576b-p101">如果您不能完成该任务中，有几个您可以执行其他操作。这些方法可能更方便，但也可能还需要更长时间，或具有其他缺点。它们是：</span><span class="sxs-lookup"><span data-stu-id="a576b-p101">If you can't complete this task, there are a couple of other things you can do. These methods might be easier, but they might also take longer or have other drawbacks. They are:</span></span>
  
- <span data-ttu-id="a576b-p102">**运行目录同步时没有运行 IdFix。** 您可以将您的目录同步时没有运行 IdFix 工具，但我们不建议这样。同步之前修复错误的时间少并通常提供到云中更平稳转换。</span><span class="sxs-lookup"><span data-stu-id="a576b-p102">**Run directory synchronization without running IdFix.** You can synchronize your directory without running the IdFix tool, but we don't recommend it. Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="a576b-p103">**聘请顾问。** 获得专家的帮助可以让您的用户正常工作并提高运行速度，使您的目录顺利实现同步。</span><span class="sxs-lookup"><span data-stu-id="a576b-p103">**Hire a consultant.** Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="a576b-114">运行 IdFix 所需内容</span><span class="sxs-lookup"><span data-stu-id="a576b-114">What you need to run IdFix</span></span>

<span data-ttu-id="a576b-p104">最简单方式来获取 IdFix 和运行时将其安装在加入到域的计算机上。如果需要，但它并不需要，您可以在域控制器上运行它。</span><span class="sxs-lookup"><span data-stu-id="a576b-p104">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain. You can run it on the domain controller if you want to, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="a576b-117">IdFix 硬件要求</span><span class="sxs-lookup"><span data-stu-id="a576b-117">IdFix hardware requirements</span></span>

<span data-ttu-id="a576b-118">您安装了 IdFix 的计算机需要满足以下硬件要求：</span><span class="sxs-lookup"><span data-stu-id="a576b-118">The computer where you install IdFix needs to meet these hardware requirements:</span></span>
  
- <span data-ttu-id="a576b-119">4 GB RAM（最低）</span><span class="sxs-lookup"><span data-stu-id="a576b-119">4 GB RAM (minimum)</span></span>
- <span data-ttu-id="a576b-120">2 GB 的硬盘空间（最低）</span><span class="sxs-lookup"><span data-stu-id="a576b-120">2 GB of hard disk space (minimum)</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="a576b-121">IdFix 软件要求</span><span class="sxs-lookup"><span data-stu-id="a576b-121">IdFix software requirements</span></span>

<span data-ttu-id="a576b-p105">其中安装 IdFix 需求到的计算机需要加入到想要将用户同步到 Office 365 的同一个 Active Directory 域。计算机还需要有.NET Framework 4.0 安装。</span><span class="sxs-lookup"><span data-stu-id="a576b-p105">The computer where you install IdFix needs to needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365. The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="a576b-p106">如果您运行的 Windows Server 2008 或 Windows Server 2012，则可能已经安装.NET Framework。如果不需要，您可以[下载从下载中心下载.NET 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475)或使用 Windows Update。</span><span class="sxs-lookup"><span data-stu-id="a576b-p106">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed. If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or by using Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="a576b-126">IdFix 权限要求</span><span class="sxs-lookup"><span data-stu-id="a576b-126">IdFix permissions requirements</span></span>

<span data-ttu-id="a576b-127">您用来运行 IdFix 的用户帐户需要具有对目录的读/写访问权限。</span><span class="sxs-lookup"><span data-stu-id="a576b-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="a576b-p107">如果您不确定您的用户帐户满足这些要求，并且您不确定如何检查，如果仍然可以安装并继续运行 IdFix。如果您的用户帐户没有正确的权限，IdFix 将只会显示错误，当您尝试运行它。</span><span class="sxs-lookup"><span data-stu-id="a576b-p107">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix anyway. If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="a576b-130">安装 IdFix</span><span class="sxs-lookup"><span data-stu-id="a576b-130">Install IdFix</span></span>

<span data-ttu-id="a576b-131">要安装 IdFix，您可以下载并解压缩“IdFix.exe”****，如以下步骤所述：</span><span class="sxs-lookup"><span data-stu-id="a576b-131">To install IdFix, you download and unzip **IdFix.exe** as described in these steps:</span></span> 
  
1. <span data-ttu-id="a576b-132">登录到您要安装 IdFix 工具的计算机。</span><span class="sxs-lookup"><span data-stu-id="a576b-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="a576b-133">转到 Microsoft 下载网站 for [IdFix 目录同步错误修复工具](https://go.microsoft.com/fwlink/?linkid=867219)。</span><span class="sxs-lookup"><span data-stu-id="a576b-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="a576b-134">选择“下载”****。</span><span class="sxs-lookup"><span data-stu-id="a576b-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="a576b-135">出现提示时，选择**运行**。</span><span class="sxs-lookup"><span data-stu-id="a576b-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="a576b-p108">在**WinZip 自动解压缩程序**对话框中**解压缩到文件夹**文本框中，键入或浏览到要安装 IdFix 工具的位置。默认情况下，IdFix 安装到 C:\Deployment 工具\.</span><span class="sxs-lookup"><span data-stu-id="a576b-p108">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool. By default, IdFix is installed into C:\Deployment Tools\.</span></span> 
    
6. <span data-ttu-id="a576b-138">选择**解压缩**。</span><span class="sxs-lookup"><span data-stu-id="a576b-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="a576b-139">运行 IdFix 工具</span><span class="sxs-lookup"><span data-stu-id="a576b-139">Run the IdFix tool</span></span>

<span data-ttu-id="a576b-140">安装了 IdFix 之后，运行该工具搜索目录中的问题：</span><span class="sxs-lookup"><span data-stu-id="a576b-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="a576b-141">使用对目录具有读/写访问权限的帐户登录到您安装 IdFix 的计算机。</span><span class="sxs-lookup"><span data-stu-id="a576b-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="a576b-p109">在文件资源管理器中，转到您安装了 IdFix 的位置。如果您在安装过程中选择了默认文件夹，请转到 C:\Deployment Tools\IdFix。</span><span class="sxs-lookup"><span data-stu-id="a576b-p109">In File Explorer, go to the location where you installed IdFix. If you chose the default folder during installation, go to C:\Deployment Tools\IdFix.</span></span>
    
3. <span data-ttu-id="a576b-144">双击“IdFix.exe”****。</span><span class="sxs-lookup"><span data-stu-id="a576b-144">Double-click **IdFix.exe**.</span></span> 
    
    ![选择 IdFix.exe 文件。](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="a576b-p110">默认情况下，IdFix 使用的多租户规则集测试您的目录中的条目。这是为 Office 365 的大多数客户的右规则。但是，如果您是 Office 365 专用或 ITAR （国际流量 Arm 法规） 客户，您可以配置 IdFix 使用专用的规则设置而不是。如果不确定哪种类型的客户后，您可以安全跳过此步骤。要设置设置为专用的规则，请单击菜单栏中的齿轮图标，然后选择**专用**。</span><span class="sxs-lookup"><span data-stu-id="a576b-p110">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory. This is the right rule set for most Office 365 customers. However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead. If you aren't sure what type of customer you are, you can safely skip this step. To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="a576b-151">选择**查询**。</span><span class="sxs-lookup"><span data-stu-id="a576b-151">Choose **Query**.</span></span>
    
    ![在 IdFix 中选择查询。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="a576b-153">默认情况下，IdFix 对整个目录搜索错误。</span><span class="sxs-lookup"><span data-stu-id="a576b-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="a576b-p111">根据您的目录的大小，运行查询可能需要一段。您可以观看该工具主窗口底部的进度。如果单击**取消**，您需要重新启动从头开始。</span><span class="sxs-lookup"><span data-stu-id="a576b-p111">Depending on the size of your directory, running the query can take a while. You can watch the progress at the bottom of the tool's main window. If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![IdFix 查询和错误数。](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="a576b-p112">IdFix 完成查询之后，且目录中没有错误，则可以继续同步目录。如果您的目录中有错误，建议您在同步之前先修复这些错误。如果您想了解有关错误类型以及对解决每个错误的最佳方法的建议的详细信息，请参阅本主题结尾的链接。</span><span class="sxs-lookup"><span data-stu-id="a576b-p112">After IdFix completes the query, and if there are no errors in your directory, you can go ahead and synchronize your directory. If there are errors in your directory, it is recommended that you fix them before you synchronize. If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="a576b-161">虽然对同步之前修复错误的做法不是强制性的，但我们还是强烈建议您至少检查一下由 IdFix 返回的所有错误。</span><span class="sxs-lookup"><span data-stu-id="a576b-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="a576b-162">每个错误显示在该工具主窗口中单独的行中。</span><span class="sxs-lookup"><span data-stu-id="a576b-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="a576b-p113">如果您同意“UPDATE”**** 列中的更改建议，请在“ACTION”**** 列中选择 IdFix 要实现此更改应执行的操作，然后单击“应用”****。当您单击“应用”**** 时，该工具会在目录中做出更改。</span><span class="sxs-lookup"><span data-stu-id="a576b-p113">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="a576b-p114">您无需在每个更新后单击**应用**。相反，可以解决几个错误之前单击**应用**，IdFix 将所有在同时更改它们。可以通过单击**错误**顶部列出了错误类型的列的排序错误类型的错误。</span><span class="sxs-lookup"><span data-stu-id="a576b-p114">You don't have to click **Apply** after each update. Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time. You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="a576b-p115">一种策略是修复的相同类型; 所有错误例如，首先，修复所有重复项，并应用这些更改。接下来，修复字符格式错误，等等。每次应用所做的更改，IdFix 工具创建单独的日志文件可用于犯的情况下撤消所做的更改。[事务日志](idfix-transaction-log.md)存储在您安装 IdFix 中的文件夹。 默认情况下_C:\Deployment Tools\IdFix_ 。</span><span class="sxs-lookup"><span data-stu-id="a576b-p115">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them. Next, fix the character format errors, and so on. Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake. The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.  _C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![解决 IdFix 中的错误。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="a576b-p116">毕竟所做更改的所做的目录，并运行 IdFix 再次以确保您所做的修补程序未引入了新的错误。您可以重复这些步骤，根据需要多次。最好进入流程几次同步之前。</span><span class="sxs-lookup"><span data-stu-id="a576b-p116">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors. You can repeat these steps as many times as you need to. It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="a576b-177">我想优化我的搜索或深入研究错误，我还能用 IdFix 来做些什么？</span><span class="sxs-lookup"><span data-stu-id="a576b-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="a576b-178">以下主题可提供更深入的信息：</span><span class="sxs-lookup"><span data-stu-id="a576b-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="a576b-p117">[准备目录属性与通过使用 IdFix 工具的 Office 365 进行同步](prepare-directory-attributes-for-synch-with-idfix.md)。您已安装的工具，跳转到本主题的更详细说明有关运行该工具之后, 会遇到的常见错误建议的修补程序、 示例和要执行的操作数量较大的错误后的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="a576b-p117">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) . After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="a576b-181">参考：IdFix 排除和支持的对象和属性</span><span class="sxs-lookup"><span data-stu-id="a576b-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="a576b-182">参考：Office 365 IdFix 事务日志</span><span class="sxs-lookup"><span data-stu-id="a576b-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="a576b-183">视频培训</span><span class="sxs-lookup"><span data-stu-id="a576b-183">Video training</span></span>

<span data-ttu-id="a576b-184">有关详细信息，请参阅进入您的 LinkedIn 学习课[安装和使用 IDFix 工具](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a576b-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx), brought to you by LinkedIn Learning.</span></span>
  

