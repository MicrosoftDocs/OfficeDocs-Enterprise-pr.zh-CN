---
title: "Office 365 和 Dynamics 365 开发/测试环境的 Exchange Online 集成"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: "摘要：使用此测试实验室指南可以实现 Office 365 试用订阅中 Exchange Online 的 Dynamics 365 集成。"
ms.openlocfilehash: b297c3e461b5695b323c619145df64524989d58a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="af8ff-103">Office 365 和 Dynamics 365 开发/测试环境的 Exchange Online 集成</span><span class="sxs-lookup"><span data-stu-id="af8ff-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="af8ff-104">**摘要：**使用此测试实验室指南可以实现 Office 365 试用订阅中 Exchange Online 的 Dynamics 365 集成。</span><span class="sxs-lookup"><span data-stu-id="af8ff-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="af8ff-p101">Microsoft Dynamics 365 的一个重要作用是将所有客户通信都存储在同一个位置，因此具有相应权限的任何人都可以查看所有相关的客户记录。例如，查看与特定联系人、帐户、 商机或案例关联的所有电子邮件。</span><span class="sxs-lookup"><span data-stu-id="af8ff-p101">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="af8ff-p102">若要将电子邮件和其他邮件记录存储在 Dynamics 365 中，需要与 Dynamics 365 同步你的电子邮件系统。服务器端同步是选择电子邮件同步的方法。</span><span class="sxs-lookup"><span data-stu-id="af8ff-p102">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365. Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="af8ff-109">此测试实验室指南用于配置和演示 Exchange Online 和 Outlook Online 客户端如何利用 Dynamics 365 中存储的信息。</span><span class="sxs-lookup"><span data-stu-id="af8ff-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="af8ff-110">第 1 阶段：扩展 Office 365 和 Dynamics 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="af8ff-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="af8ff-111">请按照 [Office 365 和 Dynamics 365 开发/测试环境](office-365-and-dynamics-365-dev-test-environment.md) 中的说明创建一个轻型或模拟的企业版 Office 365 和 Dynamics 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="af8ff-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="af8ff-p103">本文中的配置不需要模拟的企业开发/测试环境，该环境中包括连接到 Internet 的模拟内部网和 Windows Server Active Directory (AD) 林的目录同步。它在此处作为一个选项提供，以便你可以测试 Office 365 和 Dynamics 365，并在代表典型组织的环境中对其进行试验</span><span class="sxs-lookup"><span data-stu-id="af8ff-p103">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server Active Directory (AD) forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="af8ff-114">第 2 阶段：配置和演示 Exchange Online 中的 Dynamics 365 集成</span><span class="sxs-lookup"><span data-stu-id="af8ff-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="af8ff-115">使用下列步骤配置 Dynamics 365 和 Exchange Online 集成的全局管理员邮箱：</span><span class="sxs-lookup"><span data-stu-id="af8ff-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="af8ff-116">使用浏览器的专用会话，转到 [(http://portal.office.com)]((http://portal.office.com))，再使用 Office 365 全局管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="af8ff-116">Using a private session of your browser, go to [((http://portal.office.com))]((http://portal.office.com)) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="af8ff-117">在"Microsoft Office 主页"页上，单击"邮件"磁贴。</span><span class="sxs-lookup"><span data-stu-id="af8ff-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="af8ff-118">在浏览器中的新"邮件"选项卡上，单击"新建"并注意用于键入消息的框下方窗格的底角如何显示"我的模板"图标。</span><span class="sxs-lookup"><span data-stu-id="af8ff-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message contains an icon for My Templates.</span></span>
    
     ![空白的新电子邮件未与 Dynamics 365 集成。](images/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="af8ff-120">单击"放弃"，并使"邮件"选项卡保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="af8ff-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="af8ff-121">单击浏览器中的"Microsoft Office 主页"选项卡，然后单击"管理"磁贴。</span><span class="sxs-lookup"><span data-stu-id="af8ff-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="af8ff-122">在"Office 管理中心"选项卡的左侧导航中，单击"管理中心">"Dynamics 365"。</span><span class="sxs-lookup"><span data-stu-id="af8ff-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="af8ff-123">在浏览器中新的"Dynamics 365"选项卡上的 Dynamics 365 实例列表中，单击"打开"。</span><span class="sxs-lookup"><span data-stu-id="af8ff-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="af8ff-124">在浏览器中新的"管理"选项卡中，在导航栏上单击"设置"旁边的下箭头，然后单击"系统"下方的"电子邮件配置"。</span><span class="sxs-lookup"><span data-stu-id="af8ff-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="af8ff-125">在"电子邮件配置"页上，单击"电子邮件配置设置"。</span><span class="sxs-lookup"><span data-stu-id="af8ff-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="af8ff-126">在"系统设置"对话框上的"电子邮件"选项卡中，将"约会、联系人和任务"更改为"服务器端同步"，然后单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="af8ff-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="af8ff-127">在"电子邮件配置"页上，单击"邮箱"。</span><span class="sxs-lookup"><span data-stu-id="af8ff-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="af8ff-128">在左侧复选标记列中选择 Office 365 全局管理员名称，单击工具栏上的"应用默认电子邮件设置"，然后单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="af8ff-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="af8ff-129">单击工具栏上的"批准电子邮件"，然后单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="af8ff-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="af8ff-130">在左侧复选标记列中选择 Office 365 全局管理员名称，单击工具栏上的"测试和启用邮箱"，然后单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="af8ff-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="af8ff-131">单击打开"邮件"选项卡，并确认全局管理员收到一封测试邮件。</span><span class="sxs-lookup"><span data-stu-id="af8ff-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="af8ff-p104">返回到浏览器中的"邮箱">"我的可用邮箱"选项卡，然后刷新此页。"传入电子邮件状态"和"传出电子邮件状态"列应针对全局管理员帐户名称设置为"成功"。请注意，可能需要 15 分钟来完成这两个测试。</span><span class="sxs-lookup"><span data-stu-id="af8ff-p104">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page. The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name. Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="af8ff-135">使用以下步骤安装适用于 Outlook 的 Dynamics 365 应用并在全局管理员邮箱内演示 Dynamics 365 功能：</span><span class="sxs-lookup"><span data-stu-id="af8ff-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="af8ff-136">在浏览器中的"邮箱">"我的可用邮箱"选项卡上，单击"设置"旁边的下箭头，然后单击"系统"下的"适用于 Outlook 的 Dynamics 365 应用"。</span><span class="sxs-lookup"><span data-stu-id="af8ff-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="af8ff-p105">在"开始使用适用于 Outlook 的 Microsoft Dynamics 365 应用"页上，单击全局管理员名称，然后单击"将应用添加到 Outlook"。"状态"列将更改为"挂起"。</span><span class="sxs-lookup"><span data-stu-id="af8ff-p105">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**. The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="af8ff-p106">刷新页面，直到状态更改为"添加到 Outlook"。请注意，可能需要 15 分钟来完成此配置。</span><span class="sxs-lookup"><span data-stu-id="af8ff-p106">Refresh the page until the status changes to **Added to Outlook**. Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="af8ff-141">单击浏览器中的"邮件"选项卡，然后将其关闭。</span><span class="sxs-lookup"><span data-stu-id="af8ff-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="af8ff-142">单击浏览器中的"Microsoft Office 主页"选项卡，然后单击"邮件"磁贴。</span><span class="sxs-lookup"><span data-stu-id="af8ff-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="af8ff-p107">在浏览器中新的"邮件"选项卡上，单击"新建"。请注意，用于键入消息的框下方窗格的底角现在显示 Dynamics 365 的图标。</span><span class="sxs-lookup"><span data-stu-id="af8ff-p107">On the new **Mail** tab in your browser, click **New**. Notice that the bottom corner of the pane below the box for typing a message now contains an icon for Dynamics 365.</span></span>
    
     ![空白的新电子邮件与 Dynamics 365 集成，显示新图标。](images/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="af8ff-p108">单击 Dynamics 365 图标。应该会看到"Dynamics 365" 窗格，你可以在其中跟踪此电子邮件或访问模板、销售宣传资料或文章。</span><span class="sxs-lookup"><span data-stu-id="af8ff-p108">Click the Dynamics 365 icon. You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="af8ff-p109">在电子邮件的“收件人”****字段中，键入“alex.y.wu@outlook.com”****，再单击“Dynamics 365”****窗格中的“重试”****。在“Dynamics 365”****窗格中，应能看到“收件人”****部分，其中包含 Alex Wu（销售应用的联系人）的相关信息，此信息与试用订阅的示例数据一起提供。</span><span class="sxs-lookup"><span data-stu-id="af8ff-p109">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane. You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![存储在 Dynamics 365 中的销售联系人的 Dynamics 365 信息窗格。](images/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="af8ff-151">单击"放弃"。</span><span class="sxs-lookup"><span data-stu-id="af8ff-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="af8ff-152">单击[此处]((http://aka.ms/catlgstack))可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="af8ff-152">Click [here]((http://aka.ms/catlgstack)) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="af8ff-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af8ff-153">See Also</span></span>

[<span data-ttu-id="af8ff-154">Office 365 和 Dynamics 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="af8ff-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="af8ff-155">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="af8ff-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="af8ff-156">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="af8ff-156">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="af8ff-157">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="af8ff-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="af8ff-158">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="af8ff-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

<span data-ttu-id="af8ff-159">[Dynamics 365（联机）的订阅管理]((https://technet.microsoft.com/library/jj679903.aspx))</span><span class="sxs-lookup"><span data-stu-id="af8ff-159">[Subscription Management for Dynamics 365 (online)]((https://technet.microsoft.com/library/jj679903.aspx))</span></span>
  
<span data-ttu-id="af8ff-160">[管理 Dynamics 365]((https://technet.microsoft.com/library/dn531101.aspx))</span><span class="sxs-lookup"><span data-stu-id="af8ff-160">[Administering Dynamics 365]((https://technet.microsoft.com/library/dn531101.aspx))</span></span>


