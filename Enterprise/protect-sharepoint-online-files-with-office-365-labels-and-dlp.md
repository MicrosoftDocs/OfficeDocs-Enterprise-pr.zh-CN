---
title: 使用 Office 365 标签和 DLP 保护 SharePoint Online 文件
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: 摘要：为具有各级别信息保护的 SharePoint Online 团队网站应用 Office 365 标签和数据丢失防护 (DLP) 策略。
ms.openlocfilehash: 439f59f683090d39ea98730854aa1ca5dc8db482
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319263"
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="e8ed6-103">使用 Office 365 标签和 DLP 保护 SharePoint Online 文件</span><span class="sxs-lookup"><span data-stu-id="e8ed6-103">Protect SharePoint Online files with Office 365 labels and DLP</span></span>

 <span data-ttu-id="e8ed6-104">**摘要：** 为具有各级别信息保护的 SharePoint Online 团队网站应用 Office 365 标签和数据丢失防护 (DLP) 策略。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="e8ed6-p101">使用本文中的步骤针对基线、敏感和高度机密的 SharePoint Online 团队网站设计并部署 Office 365 标签和 DLP 策略。有关三层保护的详细信息，请参阅[保护 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-p101">Use the steps in this article to design and deploy Office 365 labels and DLP policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="how-this-works"></a><span data-ttu-id="e8ed6-107">工作原理</span><span class="sxs-lookup"><span data-stu-id="e8ed6-107">How this solution works</span></span>
1. <span data-ttu-id="e8ed6-p102">创建并发布所需标签。最长可能需要 12 小时，才能发布这些标签。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-p102">Create the desired labels and publish these. It can take up to 12 hours for these to be published.</span></span>
2. <span data-ttu-id="e8ed6-110">对于所需 SharePoint 网站，将文档库设置编辑为，向库中项应用标签。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-110">For the desired SharePoint sites, edit the document library settings to apply a label to items in the library.</span></span>
3. <span data-ttu-id="e8ed6-111">创建根据标签执行操作的 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-111">Create DLP policies to take action based on the labels.</span></span>

<span data-ttu-id="e8ed6-p103">用户添加到库中的文档会默认获得已分配的标签。用户可以根据需要更改此标签。如果用户在组织外部共享文档，DLP 会检查是否已分配标签，并在 DLP 策略与标签匹配时执行操作。DLP 还会查找匹配的其他策略，如通过信用卡卡号保护文件（如果已配置此类策略的话）。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-p103">When users add a document to the library, the document will receive the assigned label by default. Users can change the label,if needed. When a user shares a document outside the organization, DLP will check to see if a label is assigned and take action if a DLP policy matches the label. DLP will look for other policy matches as well, such as protecting files with credit card numbers if this type of policy is configured.</span></span> 

## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="e8ed6-116">SharePoint Online 网站的 Office 365 标签</span><span class="sxs-lookup"><span data-stu-id="e8ed6-116">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="e8ed6-117">创建并向 SharePoint Online 团队网站分配 Office 365 标签分以下三个阶段。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-117">There are three phases to creating and then assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="e8ed6-118">阶段 1：确定 Office 365 标签名称</span><span class="sxs-lookup"><span data-stu-id="e8ed6-118">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="e8ed6-p104">在此阶段，对于应用到 SharePoint Online 团队网站的四个级别的信息保护，确定 Office 365 标签的名称。 下表列出了针对每个级别建议的名称。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-p104">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="e8ed6-121">**SharePoint Online 团队网站保护级别**</span><span class="sxs-lookup"><span data-stu-id="e8ed6-121">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="e8ed6-122">**标签名称**</span><span class="sxs-lookup"><span data-stu-id="e8ed6-122">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e8ed6-123">基线 - 公用</span><span class="sxs-lookup"><span data-stu-id="e8ed6-123">Baseline-Public</span></span>  <br/> |<span data-ttu-id="e8ed6-124">内部公用</span><span class="sxs-lookup"><span data-stu-id="e8ed6-124">Internal public</span></span>  <br/> |
|<span data-ttu-id="e8ed6-125">基线 - 专用</span><span class="sxs-lookup"><span data-stu-id="e8ed6-125">Baseline-Private</span></span>  <br/> |<span data-ttu-id="e8ed6-126">Private</span><span class="sxs-lookup"><span data-stu-id="e8ed6-126">Private</span></span>  <br/> |
|<span data-ttu-id="e8ed6-127">敏感</span><span class="sxs-lookup"><span data-stu-id="e8ed6-127">Sensitive</span></span>  <br/> |<span data-ttu-id="e8ed6-128">敏感</span><span class="sxs-lookup"><span data-stu-id="e8ed6-128">Sensitive</span></span>  <br/> |
|<span data-ttu-id="e8ed6-129">高度机密</span><span class="sxs-lookup"><span data-stu-id="e8ed6-129">Highly Confidential</span></span>  <br/> |<span data-ttu-id="e8ed6-130">高度机密</span><span class="sxs-lookup"><span data-stu-id="e8ed6-130">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="e8ed6-131">阶段 2：创建 Office 365 标签</span><span class="sxs-lookup"><span data-stu-id="e8ed6-131">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="e8ed6-132">在此阶段中，针对不同的信息保护级别创建并发布确定的标签。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-132">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="e8ed6-133">若要创建标签，可以使用 Office 365 管理中心或 Microsoft PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-133">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="e8ed6-134">使用 Office 365 管理中心创建 Office 365 标签</span><span class="sxs-lookup"><span data-stu-id="e8ed6-134">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="e8ed6-p105">使用具有安全管理员或公司管理员角色的帐户登录到 Office 365 门户。有关帮助信息，请参阅[在何处登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-p105">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e8ed6-137">在“Microsoft Office 主页”**** 标签页中，单击“管理员”磁贴****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-137">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="e8ed6-138">在浏览器的新“Office 管理中心”**** 标签页中，单击“管理中心”>“安全&amp;合规性”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-138">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="e8ed6-139">在浏览器的新“主页 -安全&amp;合规性”**** 标签页中，单击“分类”>“标签”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-139">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="e8ed6-140">在“主页”>“标签”**** 窗格中，单击“创建标签”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-140">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="e8ed6-141">在“命名标签”**** 窗格中，键入标签的名称，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-141">On the **Name your label** pane, type the name of the label, and then click **Next**.</span></span>
    
7. <span data-ttu-id="e8ed6-142">在“标签设置”窗格中，单击“下一步”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-142">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="e8ed6-143">在“查看设置”**** 窗格中，单击“创建此标签”****，然后单击“关闭”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-143">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="e8ed6-144">对其他标签重复步骤 5-8。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-144">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="e8ed6-145">使用 PowerShell 创建 Office 365 标签</span><span class="sxs-lookup"><span data-stu-id="e8ed6-145">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="e8ed6-146">[使用远程 PowerShell 连接到 Office 365 安全性&amp;合规性中心](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409)，并指定具有安全管理员或公司管理员角色的帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-146">[Connect to the Office 365 Security &amp; Compliance Center using remote PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="e8ed6-147">填写标签名称列表，然后在 PowerShell 命令提示符下运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="e8ed6-147">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="e8ed6-148">接下来，使用以下步骤发布新的 Office 365 标签。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-148">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="e8ed6-149">在“安全性&amp;合规性”中心的“开始”>“标签”**** 窗格中，单击“发布标签”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-149">From the **Home > Labels** pane the Security &amp; Compliance Center, click **Publish labels**.</span></span>
    
2. <span data-ttu-id="e8ed6-150">在“选择要发布的标签”窗格中，单击“选择要发布的标签”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-150">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="e8ed6-151">在“选择标签”窗格中，单击“添加”并选择全部四个标签********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-151">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="e8ed6-152">单击“完成”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-152">Click **Done**.</span></span>
    
5. <span data-ttu-id="e8ed6-153">在“选择要发布的标签”窗格中，单击“下一步”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-153">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="e8ed6-154">在“选择位置”窗格中，单击“下一步”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-154">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="e8ed6-155">在“命名策略”**** 窗格中，在“名称”**** 中键入标签组的名称，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-155">On the **Name your policy** pane, type a name for your set of labels in **Name**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e8ed6-156">在“查看设置”**** 窗格中，单击“发布标签”****，然后单击“关闭”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-156">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="e8ed6-157">阶段 3：将 Office 365 标签应用到 SharePoint Online 网站</span><span class="sxs-lookup"><span data-stu-id="e8ed6-157">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="e8ed6-158">使用这些步骤将 Office 365 标签应用到 SharePoint Online 团队网站的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-158">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="e8ed6-159">在浏览器的“Microsoft Office 主页”标签页中，单击“SharePoint”磁贴********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-159">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="e8ed6-160">在浏览器的新“SharePoint”标签页中，单击需要分配 Office 365 标签的网站****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-160">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="e8ed6-161">在浏览器的新“SharePoint 网站”标签页中，单击“文档”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-161">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="e8ed6-162">单击设置图标，然后单击“库设置”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-162">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="e8ed6-163">在“权限和管理”下，单击“向此库中的项应用标签”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-163">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="e8ed6-164">在“设置-应用标签”**** 中，选择相应的标签，然后单击“保存”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-164">In **Settings-Apply Label**, select the appropriate label, and then click **Save**.</span></span>
    
7. <span data-ttu-id="e8ed6-165">关闭 SharePoint Online 网站的选项卡。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-165">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="e8ed6-166">重复步骤 3-8，将 Office 365 标签分配给其他 SharePoint Online 网站。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-166">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="e8ed6-167">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-167">Here is your resulting configuration.</span></span>
  
![四种类型的 SharePoint Online 团队网站的 Office 365 标签。](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="e8ed6-169">适用于 SharePoint Online 网站的 DLP 策略</span><span class="sxs-lookup"><span data-stu-id="e8ed6-169">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="e8ed6-170">使用以下步骤配置 DLP 策略，该策略可在用户在组织外共享关于 SharePoint Online 敏感团队网站的文档时进行通知。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-170">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="e8ed6-171">在浏览器的“Microsoft Office 主页”**** 标签页中，单击“安全&amp;合规性”**** 磁贴。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-171">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="e8ed6-172">在浏览器的新“安全&amp;合规性”**** 标签页中，单击“数据丢失防护”>“策略”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-172">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="e8ed6-173">在“数据丢失防护”窗格中，单击“+ 创建策略”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-173">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="e8ed6-174">在“从模板开始或创建自定义策略”**** 窗格中，单击“自定义”****，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-174">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="e8ed6-175">在“命名策略”**** 窗格中，在“名称”**** 中键入敏感级别 DLP 策略的名称，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-175">In the **Name your policy** pane, type the name for the sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="e8ed6-176">在“选择位置”窗格中，单击“允许选择特定位置”，然后单击“下一步”************。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-176">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="e8ed6-177">在位置列表中，禁用“Exchange 电子邮件”**** 和“OneDrive 帐户位置”****，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-177">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e8ed6-178">在“自定义要保护的敏感信息类型”窗格中，单击“编辑”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-178">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="e8ed6-179">在“选择要保护的内容类型”**** 窗格中，单击下拉框中的“添加”****，然后单击“标签”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-179">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="e8ed6-180">在“标签”**** 窗格中，单击“+ 添加”****，选择“敏感”**** 标签，然后依次单击“添加”**** 和“完成”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-180">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="e8ed6-181">在“选择要保护的内容类型”窗格中，单击“保存”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-181">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="e8ed6-182">在“自定义要保护的敏感信息类型”窗格中，单击“下一步”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-182">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="e8ed6-183">在“如果检测到敏感信息，希望采取什么操作?”窗格中，单击“自定义提示和电子邮件”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-183">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="e8ed6-184">在“自定义策略提示和电子邮件通知”**** 窗格中，单击“自定义策略提示文本”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-184">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="e8ed6-185">在文本框中，键入或粘贴以下提示之一，具体取决于是否已实现 Azure 信息保护来保护高度机密文件：</span><span class="sxs-lookup"><span data-stu-id="e8ed6-185">In the text box, type or paste in one of the following tips, depending on if you implemented Azure Information Protection to protect highly confidential files:</span></span>
    
  - <span data-ttu-id="e8ed6-p106">要与组织外部的用户共享，请下载并打开文件。 依次单击“文件”、“保护文档”、“使用密码加密”，然后指定强密码。 通过单独的电子邮件或其他通信方式发送密码。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-p106">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
  - <span data-ttu-id="e8ed6-p107">高度机密文件已获加密保护。只有 IT 部门向其授予对这些文件的相应权限的外部用户，才能读取这些文件。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-p107">Highly confidential files are protected with encryption. Only external users who are granted permissions to these files by your IT department can read them.</span></span>
    
    <span data-ttu-id="e8ed6-p108">或者，键入或粘贴自己的策略提示，告知用户如何在组织外部共享文件。若要详细了解如何向外部用户授予对 Azure 信息保护已保护文件的权限，请参阅“为外部用户添加权限”。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-p108">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization. For more information on giving external users permissions to files protected wiht Azure Information Protection, see Adding permissions for external users.</span></span>
    
16. <span data-ttu-id="e8ed6-193">单击“确定”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-193">Click **OK**.</span></span>
    
17. <span data-ttu-id="e8ed6-194">在“如果检测到敏感信息，希望采取什么操作?”**** 窗格中，取消勾选“阻止共享并将访问限于共享内容”**** 复选框，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-194">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="e8ed6-195">在“是否希望立即启用策略或先进行测试?”**** 窗格中，单击“是，立即启用”****，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-195">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="e8ed6-196">在“查看设置”**** 窗格中，单击“创建”****，然后单击“关闭”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-196">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="e8ed6-197">以下为敏感 SharePoint Online 团队网站的配置结果。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-197">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![使用敏感 Office 365 标签的独立 SharePoint Online 团队网站的 DLP 策略。](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="e8ed6-199">接下来，使用以下步骤配置 DLP 策略，该策略可在用户在组织外共享关于 SharePoint Online 高度机密团队网站的文档时阻止用户。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-199">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="e8ed6-200">在浏览器的“Microsoft Office 主页”**** 标签页中，单击“安全&amp;合规性”**** 磁贴。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-200">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="e8ed6-201">在浏览器的新“安全&amp;合规性”**** 标签页中，单击“数据丢失防护”>“策略”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-201">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="e8ed6-202">在“数据丢失防护”窗格中，单击“+ 创建策略”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-202">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="e8ed6-203">在“从模板开始或创建自定义策略”**** 窗格中，单击“自定义”****，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-203">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="e8ed6-204">在“命名策略”**** 窗格中，在“名称”**** 中键入高度敏感级别 DLP 策略的名称，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-204">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="e8ed6-205">在“选择位置”窗格中，单击“允许选择特定位置”，然后单击“下一步”************。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-205">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="e8ed6-206">在位置列表中，禁用“Exchange 电子邮件”**** 和“OneDrive 帐户位置”****，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-206">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e8ed6-207">在“自定义要保护的敏感信息类型”窗格中，单击“编辑”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-207">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="e8ed6-208">在“选择要保护的内容类型”**** 窗格中，单击下拉框中的“添加”****，然后单击“标签”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-208">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="e8ed6-209">在“标签”**** 窗格中，单击“+ 添加”****，选择“高度机密”标签****，然后依次单击“添加”**** 和“完成”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-209">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="e8ed6-210">在“选择要保护的内容类型”窗格中，单击“保存”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-210">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="e8ed6-211">在“自定义要保护的敏感信息类型”窗格中，单击“下一步”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-211">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="e8ed6-212">在“如果检测到敏感信息，希望采取什么操作?”窗格中，单击“自定义提示和电子邮件”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-212">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="e8ed6-213">在“自定义策略提示和电子邮件通知”窗格中，单击“自定义策略提示文本”********。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-213">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="e8ed6-214">在文本框中，键入或粘贴以下内容：</span><span class="sxs-lookup"><span data-stu-id="e8ed6-214">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="e8ed6-p109">要与组织外部的用户共享，请下载并打开文件。 依次单击“文件”、“保护文档”、“使用密码加密”，然后指定强密码。 通过单独的电子邮件或其他通信方式发送密码。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-p109">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="e8ed6-218">或者，键入或粘贴自己的策略提示，指示用户如何在组织外共享文件。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-218">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="e8ed6-219">单击“确定”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="e8ed6-220">在“如果检测到敏感信息，希望采取什么操作?”**** 窗格中，选择“需要业务理由进行重写”****，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-220">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
18. <span data-ttu-id="e8ed6-221">在“是否希望立即启用策略或先进行测试?”**** 窗格中，单击“是，立即启用”****，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="e8ed6-222">在“查看设置”**** 窗格中，单击“创建”****，然后单击“关闭”****。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="e8ed6-223">以下为高度机密的 SharePoint Online 团队网站的配置结果。</span><span class="sxs-lookup"><span data-stu-id="e8ed6-223">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![使用高度机密 Office 365 标签的独立 SharePoint Online 团队网站的 DLP 策略。](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="e8ed6-225">后续步骤</span><span class="sxs-lookup"><span data-stu-id="e8ed6-225">Next step</span></span>

[<span data-ttu-id="e8ed6-226">使用 Azure 信息保护来保护 SharePoint Online 文件</span><span class="sxs-lookup"><span data-stu-id="e8ed6-226">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="e8ed6-227">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8ed6-227">See Also</span></span>

[<span data-ttu-id="e8ed6-228">保护 SharePoint Online 网站和文件</span><span class="sxs-lookup"><span data-stu-id="e8ed6-228">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="e8ed6-229">在开发/测试环境中保护 SharePoint Online 网站</span><span class="sxs-lookup"><span data-stu-id="e8ed6-229">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="e8ed6-230">Microsoft 针对政治宣传活动、非营利组织和其他敏捷性组织的安全指南</span><span class="sxs-lookup"><span data-stu-id="e8ed6-230">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="e8ed6-231">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="e8ed6-231">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


