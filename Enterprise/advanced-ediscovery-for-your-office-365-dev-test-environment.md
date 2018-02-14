---
title: "用于 Office 365 开发/测试环境的高级电子数据展示"
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
- TLG-
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: "摘要： 配置和演示 Office 365 高级的 eDiscovery Office 365 开发/测试环境中的示例数据。"
ms.openlocfilehash: a118ec2753d04afb60d13890b7d5da8c07701721
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="e7b7a-103">用于 Office 365 开发/测试环境的高级电子数据展示</span><span class="sxs-lookup"><span data-stu-id="e7b7a-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="e7b7a-104">**摘要：**演示 Office 365 高级的 eDiscovery Office 365 开发/测试环境中的示例数据和配置。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="e7b7a-p101">Office 365 高级的 eDiscovery 可以快速找到并分析整个 Office 365，包括电子邮件和文档中存储的数据的相关信息。这样可以节省大量的时间和费用，特别是在诉讼情形。有关详细信息，请参阅[Office 365 高级 eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-p101">Office 365 Advanced eDiscovery allows you to quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents. This can save enormous amounts of time and expense, especially in litigation situations. For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="e7b7a-108">借助本文中的说明可以创建一个虚构的合同纠纷的一小组数据，并使用高级电子数据展示对数据进行分析。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="e7b7a-109">单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="e7b7a-110">第 1 阶段：创建 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="e7b7a-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="e7b7a-111">如果您只需要达到最低要求的轻量方式测试高级的 eDiscovery，按照第二阶段和第 3 阶段的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="e7b7a-112">如果您想要测试模拟企业中的高级的 eDiscovery，按照[目录同步为您 Office 365 的开发/测试环境](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e7b7a-p102">测试高级的 eDiscovery 不需要模拟的企业环境中，其中包括连接到 Internet 的模拟内部网和 Windows 服务器 AD 林中的目录同步。它提供此处作为一个选项，以便您可以代表典型的组织的环境中执行测试和试验。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-p102">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="e7b7a-115">第 2 阶段：创建高级电子数据展示的示例数据</span><span class="sxs-lookup"><span data-stu-id="e7b7a-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="e7b7a-116">在此过程中，创建电子邮件，稍后会在高级电子数据展示案例中对这些电子邮件进行分析。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="e7b7a-117">打开 Internet Explorer 并登录到 Outlook 帐户在[Office 365 开发/测试环境](office-365-dev-test-environment.md)的阶段 2 中创建的[https://outlook.com](https://outlook.com) 。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="e7b7a-118">如果使用的是轻型开发/测试环境，请打开 Internet Explorer 的专用会话并从本地计算机登录。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="e7b7a-119">如果您使用的模拟的企业开发/测试环境，使用 Azure 门户网站 ([https://portal.azure.com](https://portal.azure.com)) 连接到客户端 1 虚拟机，然后从客户端 1 登录。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="e7b7a-120">在**Outlook 邮件**选项卡上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="e7b7a-p103">**对**，键入您的订购试用期的 User6 帐户的电子邮件地址 ( **user6 @。**<organization name> **。 onmicrosoft.com**)。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-p103">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name> **.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="e7b7a-123">该主题中，键入**测试电子邮件 1**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="e7b7a-124">在正文中，键入**Tailspin 合同草稿**，然后单击**发送**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="e7b7a-125">在**Outlook 邮件**选项卡上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="e7b7a-126">**对**，键入您的订购试用期的 User6 帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="e7b7a-127">该主题中，键入**测试电子邮件 2**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="e7b7a-128">在正文中，键入**Tailspin 午宴**，然后单击**发送**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="e7b7a-129">在**Outlook 邮件**选项卡上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="e7b7a-130">**对**，键入您的订购试用期的 User6 帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="e7b7a-131">该主题中，键入**测试电子邮件 3**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="e7b7a-132">在正文中，键入**Tailspin 合同不一致**，，然后单击**发送**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="e7b7a-133">单击右上角的用户图标，然后单击**注销**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="e7b7a-134">打开一个新的选项卡和登录到的帐户名和密码您的订购试用期的 User6 帐户与 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com))。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-134">Open a new tab and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="e7b7a-135">**Office 365 门户**选项卡上，单击**邮件**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="e7b7a-136">**邮件-User6-Outlook**选项卡上，验证 User6 收到所有三封电子邮件从 Outlook 电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-136">On the **Mail - User6 - Outlook** tab, verify that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="e7b7a-137">切换回至**Office 365 门户选项卡**为 User6。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="e7b7a-138">单击右上角的用户图标，然后单击**注销。**</span><span class="sxs-lookup"><span data-stu-id="e7b7a-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="e7b7a-139">在此过程中，创建两个 Word 文档，稍后会在高级电子数据展示案例中对这些文档进行分析。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="e7b7a-140">在**Office**页中，单击**登录，**登录您的全局管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="e7b7a-141">在新的选项卡，访问生产 SharePoint 站点的 URL: **https://** <fictional organization name> **.sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="e7b7a-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="e7b7a-142">在**生产站点集合**选项卡上的**文档**，请单击**新建 > Word 文档**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="e7b7a-143">在**单词在线**页面上，键入**Tailspin 草稿合同**，等待，直到它在标题将显示**已保存**，然后关闭**单词在线**页面选项卡。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="e7b7a-144">在**生产站点集合**选项卡上的**文档**，请单击**新建 > Word 文档**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="e7b7a-145">在**单词在线**选项卡上，键入**Tailspin 合同争议备注**、 等待，直到它在标题将显示**已保存**，然后关闭**单词在线**选项卡。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="e7b7a-146">**生产站点集合**选项卡上，您应该看到**文档**和**文档 1**中的文档的列表。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="e7b7a-147">关闭**生产站点集合**选项卡。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="e7b7a-148">阶段 3： 使用高级的 eDiscovery 的法律争议</span><span class="sxs-lookup"><span data-stu-id="e7b7a-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="e7b7a-p104">遗憾的是，您的组织和乖宝贝玩具公司之间的合同争端已达到的点的法律诉讼。在此过程中，您可以创建和配置高级的 eDiscovery 案例来搜索和分析电子邮件和文档包含文本"Tailspin 协定"。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-p104">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action. In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="e7b7a-151">使用高级电子数据展示的流程如下：</span><span class="sxs-lookup"><span data-stu-id="e7b7a-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="e7b7a-152">在安全创建搜索&amp;法规遵从性中心，分析其结果，和高级 eDiscovery 准备的结果。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="e7b7a-153">在高级电子数据展示中创建并配置案例，并分析相应的搜索结果。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="e7b7a-154">在此过程中，您创建的搜索结果中安全&amp;法规遵从性中心对于"Tailspin 合同"，查看结果，和高级 eDiscovery 准备的结果。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="e7b7a-155">**Office 365 门户**选项卡中，单击**管理**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="e7b7a-156">在 Admin 中心选项卡左侧导航，请单击**中心管理 > 法规遵从性**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="e7b7a-157">在**安全&amp;法规遵从性**选项卡上，单击**权限**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="e7b7a-158">在**权限**列表中，双击**组织管理**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="e7b7a-159">在**角色组**窗口中，在**成员**下单击加号。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="e7b7a-160">在**选择成员**窗口中，双击您的管理员帐户的名称，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="e7b7a-161">在**角色组**窗口中，单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="e7b7a-162">在**权限**列表中，双击**数据展示管理器**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="e7b7a-163">在**角色组**窗口下**eDiscovery 管理员**，单击加号图标。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="e7b7a-164">在**选择成员**窗口中，双击您的管理员帐户的名称，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="e7b7a-165">在**角色组**窗口中，单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="e7b7a-166">在左边的导航，请单击**搜索&amp;调查 > 内容搜索**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="e7b7a-167">单击加号添加搜索。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="e7b7a-168">在**新的搜索**窗口中，键入**Tailspin 合同搜索**范围**名称**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="e7b7a-169">在**您，希望我们看？**，**无处不在搜索**选择**交换**、 **SharePoint**以及**公用文件夹**，请单击，然后单击**下一步。**</span><span class="sxs-lookup"><span data-stu-id="e7b7a-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="e7b7a-170">在**要我们寻找？**， **Tailspin 合同**，键入，然后单击**搜索**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="e7b7a-171">在搜索列表中，单击**Tailspin 合同搜索**名称。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="e7b7a-p105">在**Tailspin 合同搜索**窗格中，单击**预览搜索结果**下**的结果**。您应该看到一个窗口，列出在生产 SharePoint 网站 （**文档**和**文档 1**） 和**测试电子邮件 1**和**3 的测试电子邮件**电子邮件发送给 User6 的两个文档。关闭该窗口。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-p105">In the **Tailspin contract search** pane, click **Preview search results** under **Results**. You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6. Close the window.</span></span>
    
19. <span data-ttu-id="e7b7a-175">在**内容搜索**窗格中，**用高级的 eDiscovery 的分析结果**下**预览结果进行分析**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="e7b7a-176">在**准备搜索 Tailspin 合同搜索结果**窗口中，单击**准备**并等待其完成。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="e7b7a-177">在此过程中，创建高级电子数据展示的新案例并对 Tailspin 合同搜索结果进行分析。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="e7b7a-178">在左边的导航，请单击下的**eDiscovery** **搜索&amp;调查**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="e7b7a-179">**EDiscovery**的窗格中，单击**转到高级 eDiscovery**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="e7b7a-180">**EDiscovery 高级**选项卡中，单击加号图标，添加新的用例。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="e7b7a-p106">**加载情况下**的窗格中，在**名称**中键入**Tailspin 合同纠纷**，然后单击**确定**。要创建用例等。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="e7b7a-183">双击**Tailspin 合同纠纷**案例的列表中。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="e7b7a-p107">在**容器**列表中，单击**Tailspin 合同搜索**容器，然后单击**过程**。等待此处理完成。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-p107">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**. Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="e7b7a-186">当**进程： 完成**出现在窗口的底部，单击**进程摘要**查看摘要左侧导航中。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="e7b7a-187">在顶部的导航中，单击**分析**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="e7b7a-188">在**安装程序**页中的**主题**下，键入**3**中**主题的最大数目**。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="e7b7a-p108">单击**分析**，并等待要完成的分析。您应该看到一连串饼形图与分析的目标人口、 文档、 电子邮件和附件。有关详细信息，请参阅[查看分析结果](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-p108">Click **Analyze** and wait for the analysis to complete. You should see a series of pie charts with analysis of the target population, documents, emails, and attachments. For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="e7b7a-192">现在可以使用此环境创建新内容、新搜索和新案例，并在 Office 365 中进一步对高级电子数据展示进行试验。</span><span class="sxs-lookup"><span data-stu-id="e7b7a-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e7b7a-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7b7a-193">See Also</span></span>

[<span data-ttu-id="e7b7a-194">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="e7b7a-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="e7b7a-195">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="e7b7a-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="e7b7a-196">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="e7b7a-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="e7b7a-197">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="e7b7a-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="e7b7a-198">Office 365 开发/测试环境的云应用程序安全性</span><span class="sxs-lookup"><span data-stu-id="e7b7a-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="e7b7a-199">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="e7b7a-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="e7b7a-200">Office 365 高级的 eDiscovery</span><span class="sxs-lookup"><span data-stu-id="e7b7a-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


