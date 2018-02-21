---
title: "Office 365 开发/测试环境中的数据分类和标记"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: "摘要： 配置和展示数据分类和标记您 Office 365 的开发/测试环境中使用 Azure 信息保护 (AIP) 客户端。"
ms.openlocfilehash: 7243acecca0dd4c39ff6ef2aecd25091f25f2f53
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="19ef2-103">Office 365 开发/测试环境中的数据分类和标记</span><span class="sxs-lookup"><span data-stu-id="19ef2-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="19ef2-104">**摘要：**配置和展示数据分类和标记您 Office 365 的开发/测试环境中使用 Azure 信息保护 (AIP) 客户端。</span><span class="sxs-lookup"><span data-stu-id="19ef2-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="19ef2-p101">Azure 信息保护客户端使您可以将文档划分到之前将其上载到 SharePoint Online Office 365 中的文件夹。使用本文中的说明进行操作，您可以安装 Azure 信息保护客户端和演示数据分类。有关详细信息，请参阅[Azure 的信息保护](https://www.microsoft.com/cloud-platform/azure-information-protection)。</span><span class="sxs-lookup"><span data-stu-id="19ef2-p101">The Azure Information Protection client allows you to classify a document before you upload it to a SharePoint Online folder in Office 365. With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification. For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="19ef2-108">单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。</span><span class="sxs-lookup"><span data-stu-id="19ef2-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="19ef2-109">第 1 阶段：构建 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="19ef2-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="19ef2-110">按照在[Office 365 的开发/测试环境](office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="19ef2-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="19ef2-111">第 2 阶段：添加 Azure 信息保护试用订阅</span><span class="sxs-lookup"><span data-stu-id="19ef2-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="19ef2-p102">在此阶段中，您添加到 Office 365 开发/测试环境的 Azure 信息保护并使您的用户帐户。如果您已配置了[Office 365 和 EMS 开发/测试环境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)，则跳过这一阶段。企业移动套件试用订阅包括 Azure 信息保护许可证。</span><span class="sxs-lookup"><span data-stu-id="19ef2-p102">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts. If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase. The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="19ef2-115">首先，注册 Azure 信息保护试用订阅。</span><span class="sxs-lookup"><span data-stu-id="19ef2-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="19ef2-116">注册 Azure 信息保护试用订阅</span><span class="sxs-lookup"><span data-stu-id="19ef2-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="19ef2-117">在 Internet Explorer 或浏览器中，转到[http://portal.office.com](http://portal.office.com)并使用您的 Office 365 提供全局管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="19ef2-117">In Internet Explorer or your browser, go to [http://portal.office.com](http://portal.office.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="19ef2-118">**Microsoft Office 主页**选项卡上，单击**管理**拼贴。</span><span class="sxs-lookup"><span data-stu-id="19ef2-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="19ef2-119">在 Office 365 管理选项卡上的在左侧的导航，请单击**计费 > 购买服务**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="19ef2-p103">**购买服务**页上找到**Azure 信息保护津贴 P2**项。鼠标悬停并单击**开始免费试用版**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="19ef2-122">在“确认订单”页中，单击“立即试用”。</span><span class="sxs-lookup"><span data-stu-id="19ef2-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="19ef2-123">在“订单签收”页中，单击“继续”。</span><span class="sxs-lookup"><span data-stu-id="19ef2-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="19ef2-124">接下来，为所有用户帐户启用 Azure 信息保护许可证。</span><span class="sxs-lookup"><span data-stu-id="19ef2-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="19ef2-125">在 Office 365 管理中心选项卡上，单击**用户**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-125">On the Office 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="19ef2-126">在用户帐户的列表中，选择您的全局管理员帐户，然后单击**编辑****产品**许可证。</span><span class="sxs-lookup"><span data-stu-id="19ef2-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="19ef2-127">对**Azure 信息保护津贴 P2**到**上**打开产品许可证、 单击**保存**，然后单击**关闭**两次。</span><span class="sxs-lookup"><span data-stu-id="19ef2-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="19ef2-128">对其他用户帐户（用户 1 至用户 5）重复执行第 2 步和第 3 步。</span><span class="sxs-lookup"><span data-stu-id="19ef2-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="19ef2-129">此时，Office 365 开发/测试环境包含：</span><span class="sxs-lookup"><span data-stu-id="19ef2-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="19ef2-130">Office 365 E5 企业版和 Azure 信息保护试用订阅。</span><span class="sxs-lookup"><span data-stu-id="19ef2-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="19ef2-131">可使用 Office 365 E5 企业版和 Azure 信息保护的所有用户帐户。</span><span class="sxs-lookup"><span data-stu-id="19ef2-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="19ef2-132">第 3 阶段：演示数据分类</span><span class="sxs-lookup"><span data-stu-id="19ef2-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="19ef2-133">在此阶段中，你将使用 Azure 信息保护客户端和默认的 Azure 信息保护策略演示数据分类。</span><span class="sxs-lookup"><span data-stu-id="19ef2-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="19ef2-134">如果使用的是模拟企业 Office 365 开发/测试环境，必须先在 CLIENT1 上安装 Office 2016。</span><span class="sxs-lookup"><span data-stu-id="19ef2-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="19ef2-135">使用您的浏览器并转到[Azure 的门户](http://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="19ef2-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="19ef2-136">单击**资源组 >** [资源组名称] **> 客户端 1 > 连接**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="19ef2-137">从客户端 1，运行 Internet Explorer，转到[http://portal.office.com](http://portal.office.com)，在该办公室门户然后使用 User5 帐户名和密码登录。</span><span class="sxs-lookup"><span data-stu-id="19ef2-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://portal.office.com](http://portal.office.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="19ef2-138">在**Microsoft Office 主页**选项卡上，单击**安装 Office 2016**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="19ef2-p104">运行时系统提示，请单击**是**用户帐户控制提示时下载。等待安装 Office。完成后，单击**关闭**两次。</span><span class="sxs-lookup"><span data-stu-id="19ef2-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="19ef2-142">接下来，安装 Azure 信息保护客户端。</span><span class="sxs-lookup"><span data-stu-id="19ef2-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="19ef2-143">在浏览器或 Internet Explorer 中，转到[Microsoft Azure 信息保护下载页面](https://www.microsoft.com/download/details.aspx?id=53018)。</span><span class="sxs-lookup"><span data-stu-id="19ef2-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="19ef2-144">如果使用的是轻型 Office 365 开发/测试环境，请在本地计算机上运行浏览器。</span><span class="sxs-lookup"><span data-stu-id="19ef2-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="19ef2-145">如果使用的是模拟企业 Office 365 开发/测试环境，请在 CLIENT1 上运行 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="19ef2-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="19ef2-146">在**Microsoft Azure 信息保护**下载页上，单击**下载**，请单击**AzInfoProtection.exe**，，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="19ef2-147">出现提示时，运行 AzInfoProtection.exe。</span><span class="sxs-lookup"><span data-stu-id="19ef2-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="19ef2-148">在**安装 Azure 信息保护**客户端中，单击**我同意**，然后单击**是**用户帐户控制提示时。</span><span class="sxs-lookup"><span data-stu-id="19ef2-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="19ef2-149">在**已成功完成**框中，单击**关闭。**</span><span class="sxs-lookup"><span data-stu-id="19ef2-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="19ef2-150">接下来，演示文档分类。</span><span class="sxs-lookup"><span data-stu-id="19ef2-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="19ef2-151">单击任务栏中的**Word**图标。</span><span class="sxs-lookup"><span data-stu-id="19ef2-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="19ef2-152">当出现提示时，使用 User5 帐户名称和密码登录。</span><span class="sxs-lookup"><span data-stu-id="19ef2-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="19ef2-153">如果只安装 Office 2016 上客户端 1，**要事第一**框中，单击**接受**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="19ef2-154">单击**空白文档**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="19ef2-155">请注意在**主页**选项卡，文档分类的行功能区的**保护**部分。</span><span class="sxs-lookup"><span data-stu-id="19ef2-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="19ef2-156">在空白文档中，键入一些文本。</span><span class="sxs-lookup"><span data-stu-id="19ef2-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="19ef2-157">单击**文件 > 保存**，键入名称**BeforeAIP**，，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="19ef2-158">在行中的文档类，为**机密**，单击向下箭头，然后单击**全部公司**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="19ef2-159">单击**文件 > 另存为**，键入名称**AfterAIP**，，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="19ef2-160">在任务栏中，单击**文件资源管理器**，然后打开**文档**文件夹。</span><span class="sxs-lookup"><span data-stu-id="19ef2-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="19ef2-p105">请注意不同文件的**BeforeAIP**和**AfterAIP**文档的大小。AfterAIP 文档是较大的因为它包含分类信息。</span><span class="sxs-lookup"><span data-stu-id="19ef2-p105">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents. The AfterAIP document is larger because it contains the classification information.</span></span>
    
<span data-ttu-id="19ef2-163">接下来，允许每个人访问支持网站集。</span><span class="sxs-lookup"><span data-stu-id="19ef2-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="19ef2-164">在**Microsoft Office 主页**选项卡上，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="19ef2-165">从**SharePoint**选项卡上，单击**支持网站集**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="19ef2-166">右上角，单击**设置**图标，然后单击**共享的**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="19ef2-167">在**共享支持网站集**，单击**高级**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="19ef2-168">在列表的 SharePoint 组，请单击**支持站点集合成员**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="19ef2-169">在“人员和组”页中，单击“新建”。</span><span class="sxs-lookup"><span data-stu-id="19ef2-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="19ef2-170">在**共享支持网站集**，键入**每个人**，**每个人，除了外部用户**，请单击，然后单击**共享。**</span><span class="sxs-lookup"><span data-stu-id="19ef2-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="19ef2-171">关闭**用户和用户组**选项卡。</span><span class="sxs-lookup"><span data-stu-id="19ef2-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="19ef2-172">接下来，使用 User5 帐户登录，然后将受 AIP 保护的文档上载到支持网站集的“Documents”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="19ef2-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="19ef2-173">在**Microsoft Office 家庭**选项卡上的在右上角，单击用户图标，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="19ef2-174">转到[http://portal.office.com](http://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="19ef2-174">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="19ef2-175">在 * * 签名的 Office 365 * * 页上，单击 User5 帐户的名称，在每次登录。</span><span class="sxs-lookup"><span data-stu-id="19ef2-175">On the ** Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="19ef2-176">在**Microsoft Office 主页**选项卡，单击**SharePoint > 支持网站**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="19ef2-177">单击**文档**，单击**上载**、 **AfterAIP**文档，请单击，然后单击**打开**。</span><span class="sxs-lookup"><span data-stu-id="19ef2-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="19ef2-178">应该会在支持网站集上看到文档文件夹中的 AfterAIP.docx。</span><span class="sxs-lookup"><span data-stu-id="19ef2-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="19ef2-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19ef2-179">See Also</span></span>

[<span data-ttu-id="19ef2-180">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="19ef2-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="19ef2-181">Office 365 和 EMS 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="19ef2-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="19ef2-182">Azure 信息保护</span><span class="sxs-lookup"><span data-stu-id="19ef2-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


