---
title: Office 365 开发/测试环境中的数据分类和标记
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: '摘要: 使用 Office 365 开发/测试环境中的 Azure 信息保护 (AIP) 客户端配置和演示数据分类和标记。'
ms.openlocfilehash: 66bdbb74ae88e10d5aa4fce2173f9a2b88a15e9b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490059"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="0b21e-103">Office 365 开发/测试环境中的数据分类和标记</span><span class="sxs-lookup"><span data-stu-id="0b21e-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="0b21e-104">**摘要:** 使用 Office 365 开发/测试环境中的 Azure 信息保护 (AIP) 客户端配置和演示数据分类和标记。</span><span class="sxs-lookup"><span data-stu-id="0b21e-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="0b21e-105">Azure 信息保护客户端允许您在将文档上载到 Office 365 中的 SharePoint Online 文件夹之前对文档进行分类。</span><span class="sxs-lookup"><span data-stu-id="0b21e-105">The Azure Information Protection client lets you classify a document before you upload it to a SharePoint Online folder in Office 365.</span></span> <span data-ttu-id="0b21e-106">使用本文中的说明, 您可以安装 Azure 信息保护客户端并演示数据分类。</span><span class="sxs-lookup"><span data-stu-id="0b21e-106">With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification.</span></span> <span data-ttu-id="0b21e-107">有关详细信息, 请参阅[Azure 信息保护](https://www.microsoft.com/cloud-platform/azure-information-protection)。</span><span class="sxs-lookup"><span data-stu-id="0b21e-107">For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="0b21e-108">单击[此处](http://aka.ms/catlgstack)可直观映射到 Office 365 测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="0b21e-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="0b21e-109">第 1 阶段：构建 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="0b21e-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="0b21e-110">按照[Office 365 开发/测试环境](office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="0b21e-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="0b21e-111">第2阶段: 添加 Azure 信息保护试用订阅</span><span class="sxs-lookup"><span data-stu-id="0b21e-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="0b21e-112">在此阶段中, 将 Azure 信息保护添加到 Office 365 开发/测试环境中, 并为您的用户帐户启用它。</span><span class="sxs-lookup"><span data-stu-id="0b21e-112">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts.</span></span> <span data-ttu-id="0b21e-113">如果您已配置了[Office 365 和 EMS 开发/测试环境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), 请跳过此阶段。</span><span class="sxs-lookup"><span data-stu-id="0b21e-113">If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase.</span></span> <span data-ttu-id="0b21e-114">企业移动性套件试用订阅包括 Azure 信息保护许可证。</span><span class="sxs-lookup"><span data-stu-id="0b21e-114">The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="0b21e-115">首先, 注册 Azure 信息保护试用订阅。</span><span class="sxs-lookup"><span data-stu-id="0b21e-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="0b21e-116">注册 Azure 信息保护试用订阅</span><span class="sxs-lookup"><span data-stu-id="0b21e-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="0b21e-117">在 Internet Explorer 或浏览器中, 转[http://admin.microsoft.com](http://admin.microsoft.com)到并使用 Office 365 全局管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="0b21e-117">In Internet Explorer or your browser, go to [http://admin.microsoft.com](http://admin.microsoft.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="0b21e-118">在 " **Microsoft Office 主页**" 选项卡上, 单击 "**管理**" 磁贴。</span><span class="sxs-lookup"><span data-stu-id="0b21e-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="0b21e-119">在左侧导航栏中的 "Office 365 管理" 选项卡上, 单击 "**付费 > 购买服务**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="0b21e-120">在 "**购买服务**" 页上, 找到 " **Azure 信息保护高级 P2** " 项。</span><span class="sxs-lookup"><span data-stu-id="0b21e-120">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item.</span></span> <span data-ttu-id="0b21e-121">将鼠标悬停在它上, 然后单击 "**开始免费试用**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-121">Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="0b21e-122">在“确认订单”页上，单击“立即试用”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0b21e-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="0b21e-123">在“订单签收”页上，单击“继续”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0b21e-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="0b21e-124">接下来, 为所有用户帐户启用 Azure 信息保护许可证。</span><span class="sxs-lookup"><span data-stu-id="0b21e-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="0b21e-125">在 "Microsoft 365 管理中心" 选项卡上, 单击 "**用户**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-125">On the Microsoft 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="0b21e-126">在用户帐户列表中, 选择全局管理员帐户, 然后单击 "**产品许可证**" 的 "**编辑**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="0b21e-127">将**Azure 信息保护高级 P2**的产品许可证转换为 **"开**", 单击 "**保存",** 然后单击 "**关闭**" 两次。</span><span class="sxs-lookup"><span data-stu-id="0b21e-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="0b21e-128">对其他用户帐户 (用户1到用户 5) 重复步骤2和3。</span><span class="sxs-lookup"><span data-stu-id="0b21e-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="0b21e-129">您的 Office 365 开发/测试环境现在具有:</span><span class="sxs-lookup"><span data-stu-id="0b21e-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="0b21e-130">Office 365 E5 企业和 Azure 信息保护试用订阅。</span><span class="sxs-lookup"><span data-stu-id="0b21e-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="0b21e-131">启用了所有用户帐户以使用 Office 365 E5 企业版和 Azure 信息保护。</span><span class="sxs-lookup"><span data-stu-id="0b21e-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="0b21e-132">第3阶段: 演示数据分类</span><span class="sxs-lookup"><span data-stu-id="0b21e-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="0b21e-133">在此阶段中, 您将使用 Azure 信息保护客户端和默认的 azure 信息保护策略演示数据分类。</span><span class="sxs-lookup"><span data-stu-id="0b21e-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="0b21e-134">如果使用的是模拟企业 Office 365 开发/测试环境, 则必须先在 CLIENT1 上安装 Office 2016。</span><span class="sxs-lookup"><span data-stu-id="0b21e-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="0b21e-135">使用你的浏览器, 然后转到[Azure 门户](http://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="0b21e-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="0b21e-136">单击 "**资源组 >** [您的资源组名称] **> CLIENT1 > Connect**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="0b21e-137">从 CLIENT1 中, 运行 Internet Explorer, 转到 Office 门户, [http://admin.microsoft.com](http://admin.microsoft.com)网址为, 然后使用 User5 帐户名称和密码登录。</span><span class="sxs-lookup"><span data-stu-id="0b21e-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="0b21e-138">在“Microsoft Office 主页”\*\*\*\* 标签页上，单击“安装 Office 2016”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0b21e-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="0b21e-139">在收到提示时运行下载, 并在用户帐户控制提示时单击 **"是"** 。</span><span class="sxs-lookup"><span data-stu-id="0b21e-139">Run the download when prompted and click **Yes** when prompted by User Account Control.</span></span> <span data-ttu-id="0b21e-140">等待 Office 安装。</span><span class="sxs-lookup"><span data-stu-id="0b21e-140">Wait for Office to install.</span></span> <span data-ttu-id="0b21e-141">完成后, 单击 "**关闭**" 两次。</span><span class="sxs-lookup"><span data-stu-id="0b21e-141">When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="0b21e-142">接下来, 安装 Azure 信息保护客户端。</span><span class="sxs-lookup"><span data-stu-id="0b21e-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="0b21e-143">在浏览器或 Internet Explorer 中, 转到 " [Microsoft Azure 信息保护下载" 页面](https://www.microsoft.com/download/details.aspx?id=53018)。</span><span class="sxs-lookup"><span data-stu-id="0b21e-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="0b21e-144">如果使用的是轻型版本的 Office 365 开发/测试环境, 请使用本地计算机上的浏览器。</span><span class="sxs-lookup"><span data-stu-id="0b21e-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="0b21e-145">如果使用的是模拟企业 Office 365 开发/测试环境, 请从 CLIENT1 运行 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="0b21e-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="0b21e-146">在 " **Microsoft Azure 信息保护**下载" 页上, 单击 "**下载**", 单击 " **azinfoprotection.exe**", 然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="0b21e-147">出现提示时, 运行 azinfoprotection.exe。</span><span class="sxs-lookup"><span data-stu-id="0b21e-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="0b21e-148">在 "**安装 Azure 信息保护**客户端" 框中, 单击 "**我同意**", 然后在出现用户帐户控制提示时单击 **"是"** 。</span><span class="sxs-lookup"><span data-stu-id="0b21e-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="0b21e-149">在 "已**成功完成**" 框中, 单击 "**关闭"。**</span><span class="sxs-lookup"><span data-stu-id="0b21e-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="0b21e-150">接下来, 演示文档分类。</span><span class="sxs-lookup"><span data-stu-id="0b21e-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="0b21e-151">单击任务栏中的 " **Word** " 图标。</span><span class="sxs-lookup"><span data-stu-id="0b21e-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="0b21e-152">出现提示时, 使用 User5 帐户名称和密码登录。</span><span class="sxs-lookup"><span data-stu-id="0b21e-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="0b21e-153">如果您刚刚在 CLIENT1 上安装了 Office 2016, 请在 "第一**项**" 框中, 单击 "**接受**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="0b21e-154">单击 "**空白文档**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="0b21e-155">请注意 "**主页**" 选项卡上的功能区的 "**保护**" 部分和文档分类行。</span><span class="sxs-lookup"><span data-stu-id="0b21e-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="0b21e-156">在空白文档中, 键入一些文本。</span><span class="sxs-lookup"><span data-stu-id="0b21e-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="0b21e-157">单击 "**文件 > 保存**", 键入名称**BeforeAIP**, 然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="0b21e-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="0b21e-158">在文档类的行中, 单击 "**机密**" 的下箭头, 然后单击 "**所有公司**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="0b21e-159">单击 "**文件 > 保存为**", 键入名称**AfterAIP**, 然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="0b21e-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="0b21e-160">单击任务栏中的 "**文件资源管理器**", 然后打开 "**文档**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="0b21e-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="0b21e-161">记下**BeforeAIP**和**AfterAIP**文档的不同文件大小。</span><span class="sxs-lookup"><span data-stu-id="0b21e-161">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents.</span></span> <span data-ttu-id="0b21e-162">AfterAIP 文档较大, 因为它具有分类信息。</span><span class="sxs-lookup"><span data-stu-id="0b21e-162">The AfterAIP document is larger because it has the classification information.</span></span>
    
<span data-ttu-id="0b21e-163">接下来, 允许每个人访问支持网站集。</span><span class="sxs-lookup"><span data-stu-id="0b21e-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="0b21e-164">在 " **Microsoft Office 主页**" 选项卡上, 单击 " **SharePoint**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="0b21e-165">在 " **SharePoint** " 选项卡上, 单击 "**支持网站集**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="0b21e-166">在右上方, 单击 "**设置**" 图标, 然后单击 "**共享方式**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="0b21e-167">在**共享 "支持网站集"** 中, 单击 "**高级**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="0b21e-168">在 SharePoint 组列表中, 单击 "**支持网站集成员**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="0b21e-169">在“人员和组”页中，单击“新建”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0b21e-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="0b21e-170">在**共享 "支持网站集"** 中, 键入**everyone**, 单击 "**除外部用户之外的所有人**", 然后单击 "**共享"。**</span><span class="sxs-lookup"><span data-stu-id="0b21e-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="0b21e-171">关闭 "**人员和组**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="0b21e-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="0b21e-172">接下来, 使用 User5 帐户登录, 并将受 AIP 保护的文档上载到支持网站集的 Documents 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0b21e-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="0b21e-173">在 " **Microsoft Office 主页**" 选项卡上的右上方, 单击 "用户" 图标, 然后\*\*\*\* 单击 "注销"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="0b21e-174">转到 [http://admin.microsoft.com](http://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="0b21e-174">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="0b21e-175">在 " **Office 365 登录**" 页上, 单击 User5 帐户名并登录。</span><span class="sxs-lookup"><span data-stu-id="0b21e-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="0b21e-176">在 " **Microsoft Office 主页**" 选项卡上, 单击 " **SharePoint > 支持网站集**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="0b21e-177">单击 "**文档**", 单击 "**上载**", 再单击 " **AfterAIP** " 文档, 然后单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="0b21e-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="0b21e-178">您应该会在支持网站集上的 Documents 文件夹中看到 AfterAIP。</span><span class="sxs-lookup"><span data-stu-id="0b21e-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="0b21e-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b21e-179">See Also</span></span>

[<span data-ttu-id="0b21e-180">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="0b21e-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="0b21e-181">Office 365 和 EMS 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="0b21e-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
<span data-ttu-id="0b21e-182">[Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)（Azure 信息保护）</span><span class="sxs-lookup"><span data-stu-id="0b21e-182">[Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)</span></span>


