---
title: 用于 Office 365 开发/测试环境的高级电子数据展示
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
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: 摘要：在 Office 365 开发/测试环境中使用示例数据配置并演示 Office 365 高级电子数据展示。
ms.openlocfilehash: b1cf2714f79d38e5a3349b331cee0862cd6aac52
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491218"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="f1502-103">用于 Office 365 开发/测试环境的高级电子数据展示</span><span class="sxs-lookup"><span data-stu-id="f1502-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="f1502-104">**摘要：** 在 Office 365 开发/测试环境中使用示例数据配置并演示 Office 365 高级电子数据展示。</span><span class="sxs-lookup"><span data-stu-id="f1502-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="f1502-105">office 365 高级电子数据展示使您能够快速查找和分析存储在 Office 365 中的数据 (包括电子邮件和文档) 中的相关信息。</span><span class="sxs-lookup"><span data-stu-id="f1502-105">Office 365 Advanced eDiscovery lets you quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents.</span></span> <span data-ttu-id="f1502-106">这样则可以节省大量时间和费用，尤其是在诉讼情景中。</span><span class="sxs-lookup"><span data-stu-id="f1502-106">This can save enormous amounts of time and expense, especially in litigation situations.</span></span> <span data-ttu-id="f1502-107">有关详细信息，请参阅 [Office 365 高级电子数据展示](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)。</span><span class="sxs-lookup"><span data-stu-id="f1502-107">For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="f1502-108">借助本文中的说明可以创建一个虚构的合同纠纷的一小组数据，并使用高级电子数据展示对数据进行分析。</span><span class="sxs-lookup"><span data-stu-id="f1502-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="f1502-109">单击[此处](http://aka.ms/catlgstack)可直观映射到 Office 365 测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="f1502-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="f1502-110">第 1 阶段：创建 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="f1502-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="f1502-111">如果只想使用最低要求以轻型方式测试高级电子数据展示, 请按照第2阶段和第3阶段的[Office 365 开发/测试环境](office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f1502-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="f1502-112">如果要在模拟企业版中测试高级电子数据展示, 请按照[Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f1502-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="f1502-113">测试高级电子数据展示不需要模拟的企业环境, 其中包括连接到 Internet 的模拟 intranet 和 Active directory 域服务 (AD DS) 林的目录同步。</span><span class="sxs-lookup"><span data-stu-id="f1502-113">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="f1502-114">此处提供了此选项, 以便您可以在代表典型组织的环境中执行测试和实验。</span><span class="sxs-lookup"><span data-stu-id="f1502-114">It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="f1502-115">第 2 阶段：创建高级电子数据展示的示例数据</span><span class="sxs-lookup"><span data-stu-id="f1502-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="f1502-116">在此过程中，创建电子邮件，稍后会在高级电子数据展示案例中对这些电子邮件进行分析。</span><span class="sxs-lookup"><span data-stu-id="f1502-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="f1502-117">打开 Internet Explorer, 并登录[https://outlook.com](https://outlook.com)到在[Office 365 开发/测试环境](office-365-dev-test-environment.md)的第2阶段中创建的 Outlook 帐户。</span><span class="sxs-lookup"><span data-stu-id="f1502-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="f1502-118">如果使用的是轻型开发/测试环境，请打开 Internet Explorer 的专用会话并从本地计算机登录。</span><span class="sxs-lookup"><span data-stu-id="f1502-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="f1502-119">如果使用的是模拟企业开发/测试环境, 请使用 Azure 门户 ([https://portal.azure.com](https://portal.azure.com)) 连接到 CLIENT1 虚拟机, 然后从 CLIENT1 登录。</span><span class="sxs-lookup"><span data-stu-id="f1502-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="f1502-120">在“**Outlook 邮件**”选项卡上，单击“**新建**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="f1502-121">在 " **To**" 中, 键入试用订阅的 User6 帐户的电子邮件地址 ( **User6 @。**<organization name></span><span class="sxs-lookup"><span data-stu-id="f1502-121">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name></span></span> <span data-ttu-id="f1502-122">**. onmicrosoft.com**)。</span><span class="sxs-lookup"><span data-stu-id="f1502-122">**.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="f1502-123">在主题中，键入“**测试电子邮件 1**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="f1502-124">在正文中，键入“**Tailspin 合同草案**”，然后单击“**发送**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="f1502-125">在“**Outlook 邮件**”选项卡上，单击“**新建**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="f1502-126">在“**收件人**”中，键入试用订阅的 User6 帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="f1502-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="f1502-127">在主题中，键入“**测试电子邮件 2**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="f1502-128">在正文中，键入“**Tailspin 午餐会议**”，然后单击“**发送**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="f1502-129">在“**Outlook 邮件**”选项卡上，单击“**新建**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="f1502-130">在“**收件人**”中，键入试用订阅的 User6 帐户的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="f1502-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="f1502-131">在主题中，键入“**测试电子邮件 3**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="f1502-132">在正文中，键入“**Tailspin 合同争议**”，然后单击“**发送**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="f1502-133">单击右上角的用户图标，然后单击“**注销**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="f1502-134">打开一个新的选项卡, 并使用试用订阅的 User6[https://www.office.com](https://www.office.com)帐户的帐户名称和密码登录 Office 365 门户 ()。</span><span class="sxs-lookup"><span data-stu-id="f1502-134">Open a new tab and sign in to the Office 365 portal ([https://www.office.com](https://www.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="f1502-135">在“**Office 365 门户l**”选项卡上，单击“**邮件**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="f1502-136">在 " **User6-outlook** " 选项卡上, 检查 User6 收到的所有三封电子邮件是否来自 Outlook 电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="f1502-136">On the **Mail - User6 - Outlook** tab, check that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="f1502-137">返回到 User6 的“**Office 365 门户**”选项卡。</span><span class="sxs-lookup"><span data-stu-id="f1502-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="f1502-138">单击右上角的用户图标，然后单击“**注销**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="f1502-139">在此过程中，创建两个 Word 文档，稍后会在高级电子数据展示案例中对这些文档进行分析。</span><span class="sxs-lookup"><span data-stu-id="f1502-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="f1502-140">在“**Office**”页面上，单击“**登录**”，然后使用全局管理员帐户的凭据登录。</span><span class="sxs-lookup"><span data-stu-id="f1502-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="f1502-141">在新选项卡上, 访问您的生产 SharePoint 网站的 URL: **https://** <fictional organization name> **。 sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="f1502-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="f1502-142">在“**生产网站集**”选项卡的“**文档**”下，单击“**新建 > Word 文档**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="f1502-143">在“**Word Online**”页面，键入“**Tailspin 草案合同**”，等待标题中显示“**已保存**”，然后关闭“**Word Online**”页面选项卡。</span><span class="sxs-lookup"><span data-stu-id="f1502-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="f1502-144">在“**生产网站集**”选项卡的“**文档**”下，单击“**新建 > Word 文档**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="f1502-145">	在“*\*Word Online*\*”选项卡上，键入“*\*Tailspin 合同争议说明*\*”，等待标题中显示“*\*已保存*\*”，然后关闭“*\*Word Online*\*”选项卡。</span><span class="sxs-lookup"><span data-stu-id="f1502-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="f1502-146">在“**生产网站集**”选项卡上，你应该会在文档列表中看到“**文档**”和“**文档1**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="f1502-147">关闭“**生产网站集**”选项卡。</span><span class="sxs-lookup"><span data-stu-id="f1502-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="f1502-148">第3阶段: 将高级电子数据展示用于法律纠纷</span><span class="sxs-lookup"><span data-stu-id="f1502-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="f1502-149">很遗憾，贵组织与 Tailspin Toys 间的合同争议已到达法律诉讼的阶段。</span><span class="sxs-lookup"><span data-stu-id="f1502-149">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action.</span></span> <span data-ttu-id="f1502-150">在此过程中, 您将创建并配置高级电子数据展示事例, 以搜索和分析包含文本 "Tailspin 合同" 的电子邮件和文档。</span><span class="sxs-lookup"><span data-stu-id="f1502-150">In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="f1502-151">使用高级电子数据展示的流程如下：</span><span class="sxs-lookup"><span data-stu-id="f1502-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="f1502-152">在安全&amp;合规中心中创建搜索, 分析其结果, 然后准备高级电子数据展示的结果。</span><span class="sxs-lookup"><span data-stu-id="f1502-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="f1502-153">在高级电子数据展示中创建并配置案例，并分析相应的搜索结果。</span><span class="sxs-lookup"><span data-stu-id="f1502-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="f1502-154">在此过程中, 您将在 "Tailspin 合同&amp; " 的安全合规性中心中创建搜索, 查看结果, 然后准备高级电子数据展示的结果。</span><span class="sxs-lookup"><span data-stu-id="f1502-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="f1502-155">在“**Office 365 门户**”选项卡上，单击“**管理员**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="f1502-156">在“管理中心”选项卡的左侧导航中，单击“**管理中心>合规性**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="f1502-157">在 "**安全&amp;合规性**" 选项卡上, 单击 "**权限**"。</span><span class="sxs-lookup"><span data-stu-id="f1502-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="f1502-158">在“**权限**”列表中，双击“**组织管理**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="f1502-159">在“**角色组**”窗口的“**成员**”下，单击加号。</span><span class="sxs-lookup"><span data-stu-id="f1502-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="f1502-160">在“**选择成员**”窗口中，双击管理员帐户的名称，然后单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="f1502-161">在“**角色组**”窗口中，单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="f1502-162">在“**权限**”列表中，双击“**电子数据展示管理器**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="f1502-163">在“**角色组**”窗口的“**电子数据展示管理员**”下，单击加号。</span><span class="sxs-lookup"><span data-stu-id="f1502-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="f1502-164">在“**选择成员**”窗口中，双击管理员帐户的名称，然后单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="f1502-165">在“**角色组**”窗口中，单击“**保存**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="f1502-166">在左侧导航栏中, 单击 "**搜索&amp;调查 > 内容搜索**"。</span><span class="sxs-lookup"><span data-stu-id="f1502-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="f1502-167">单击加号添加搜索。</span><span class="sxs-lookup"><span data-stu-id="f1502-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="f1502-168">在“**新建搜索**”窗口中的“**名称**”中键入“**Tailspin 合同搜索**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="f1502-169">在“**您希望我们在哪里查找?**”中，单击“**搜索所有位置**”并选中“**Exchange**”、“**SharePoint**”和“**公用文件夹**”，然后单击“**下一步**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="f1502-170">在“**您希望我们查找哪些内容?**”中，键入“**Tailspin 合同**”，然后单击“**搜索**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="f1502-171">在搜索列表中，单击“**Tailspin 合同搜索**”名称。</span><span class="sxs-lookup"><span data-stu-id="f1502-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="f1502-172">在“**Tailspin 合同搜索**”窗格中，单击“**结果**”下的“**预览搜索结果**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-172">In the **Tailspin contract search** pane, click **Preview search results** under **Results**.</span></span> <span data-ttu-id="f1502-173">您应该会看到一个窗口, 其中列出了生产 SharePoint 网站 ( **Document**和**Document1**) 上的两个文档和**测试电子邮件 1** , 并将**电子邮件 3**电子邮件测试到 User6。</span><span class="sxs-lookup"><span data-stu-id="f1502-173">You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6.</span></span> <span data-ttu-id="f1502-174">关闭该窗口。</span><span class="sxs-lookup"><span data-stu-id="f1502-174">Close the window.</span></span>
    
19. <span data-ttu-id="f1502-175">在“**内容搜索**”窗格的“**使用高级电子数据展示分析结果**”下，单击“**预览用于分析的结果**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="f1502-176">在“**准备用于 Tailspin 合同搜索的搜索结果**”窗口中，单击“**准备**”，然后等待此过程完成。</span><span class="sxs-lookup"><span data-stu-id="f1502-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="f1502-177">在此过程中，创建高级电子数据展示的新案例并对 Tailspin 合同搜索结果进行分析。</span><span class="sxs-lookup"><span data-stu-id="f1502-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="f1502-178">在左侧导航中, 单击 "**搜索&amp;调查**" 下的 "**电子数据展示**"。</span><span class="sxs-lookup"><span data-stu-id="f1502-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="f1502-179">在“**电子数据展示**”窗格中，单击“**进入高级电子数据展示**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="f1502-180">在“**高级电子数据展示**”选项卡，单击加号添加新案例。</span><span class="sxs-lookup"><span data-stu-id="f1502-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="f1502-p106">	在“*\*添加案例*\*”窗格中的“*\*名称*\*”中键入“*\*Tailspin 合同争议*\*”，然后单击“*\*确定*\*”。等待案例创建完成。</span><span class="sxs-lookup"><span data-stu-id="f1502-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="f1502-183">双击列表中的“**Tailspin 合同争议**”。 </span><span class="sxs-lookup"><span data-stu-id="f1502-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="f1502-184">在 "**容器**" 列表中, 单击 " **Tailspin 合同搜索**" 容器, 然后单击 "**处理**"。</span><span class="sxs-lookup"><span data-stu-id="f1502-184">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**.</span></span> <span data-ttu-id="f1502-185">等待完成处理。</span><span class="sxs-lookup"><span data-stu-id="f1502-185">Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="f1502-186">当窗口底部显示“**处理: 完成**”时，单击左侧导航窗格中的“**处理摘要**”进行查看。</span><span class="sxs-lookup"><span data-stu-id="f1502-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="f1502-187">在顶部导航中单击“**分析**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="f1502-188">在“**设置**”页面“**主题**”下的“**最大主题数**”中键入“**3**”。</span><span class="sxs-lookup"><span data-stu-id="f1502-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="f1502-189">单击“**分析**”，然后等待分析完成。</span><span class="sxs-lookup"><span data-stu-id="f1502-189">Click **Analyze** and wait for the analysis to complete.</span></span> <span data-ttu-id="f1502-190">应该会看到一系列包含目标总体、文档、电子邮件和附件的饼图。</span><span class="sxs-lookup"><span data-stu-id="f1502-190">You should see a series of pie charts with analysis of the target population, documents, emails, and attachments.</span></span> <span data-ttu-id="f1502-191">有关详细信息, 请参阅[查看分析结果](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)。</span><span class="sxs-lookup"><span data-stu-id="f1502-191">For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="f1502-192">现在可以使用此环境创建新内容、新搜索和新案例，并在 Office 365 中进一步对高级电子数据展示进行试验。</span><span class="sxs-lookup"><span data-stu-id="f1502-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f1502-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1502-193">See Also</span></span>

[<span data-ttu-id="f1502-194">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="f1502-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="f1502-195">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="f1502-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="f1502-196">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="f1502-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="f1502-197">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="f1502-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="f1502-198">用于 Office 365 开发/测试环境的云应用安全</span><span class="sxs-lookup"><span data-stu-id="f1502-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="f1502-199">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="f1502-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="f1502-200">Office 365 高级电子数据展示</span><span class="sxs-lookup"><span data-stu-id="f1502-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


