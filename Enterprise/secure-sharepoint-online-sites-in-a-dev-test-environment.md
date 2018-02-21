---
title: "在开发/测试环境中保护 SharePoint Online 网站"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Normal
ms.custom: Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "摘要： 在开发/测试环境中创建公共、 私人、 敏感和高度机密 SharePoint Online 的工作组网站。"
ms.openlocfilehash: a79ba4aa5dea043884d8540fb642bbb742d08222
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="dd780-103">在开发/测试环境中保护 SharePoint Online 网站</span><span class="sxs-lookup"><span data-stu-id="dd780-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="dd780-104">**摘要：**开发/测试环境中创建公共、 私人、 敏感和高度机密 SharePoint Online 的工作组网站。</span><span class="sxs-lookup"><span data-stu-id="dd780-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="dd780-105">本文提供了分步说明创建包含四种不同类型的[安全 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)解决方案的 SharePoint Online 工作组站点的开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="dd780-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span></span>
  
![安全 SharePoint Online 开发/测试环境中的所有四个团队网站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="dd780-107">使用此开发/测试环境来试验信息保护行为，并根据具体要求微调设置，然后在生产中部署 SharePoint Online 团队网站。</span><span class="sxs-lookup"><span data-stu-id="dd780-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="dd780-108">阶段 1：创建开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="dd780-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="dd780-109">在此阶段，将获取用于虚拟组织的 Office 365 和企业移动性 + 安全性的试用订阅。</span><span class="sxs-lookup"><span data-stu-id="dd780-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="dd780-110">首先，按照**第二阶段**的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="dd780-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="dd780-111">接下来，EMS 试用订阅注册，即可将其添加到作为 Office 365 的试用订阅的同一组织。</span><span class="sxs-lookup"><span data-stu-id="dd780-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="dd780-p101">如果需要请登录到您的订购试用期的全局管理员帐户的凭据对 Office 365 门户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="dd780-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dd780-114">单击“管理”磁贴。</span><span class="sxs-lookup"><span data-stu-id="dd780-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="dd780-115">在浏览器的“Office 管理中心”选项卡的左侧导航中，单击“帐单”>“购买服务”。</span><span class="sxs-lookup"><span data-stu-id="dd780-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="dd780-p102">**购买服务**页上找到**企业移动 + 安全 E5**项。将鼠标指针悬停在其上，单击**启动免费试用版**。</span><span class="sxs-lookup"><span data-stu-id="dd780-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="dd780-118">在“确认订单”页中，单击“立即试用”。</span><span class="sxs-lookup"><span data-stu-id="dd780-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="dd780-119">在“订单签收”页中，单击“继续”。</span><span class="sxs-lookup"><span data-stu-id="dd780-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="dd780-120">接下来，为全局管理员帐户启用企业移动性 + 安全性 E5 许可证。</span><span class="sxs-lookup"><span data-stu-id="dd780-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="dd780-121">在浏览器的“Office 365 管理中心”选项卡的左侧导航中，单击“用户”>“活动用户”。</span><span class="sxs-lookup"><span data-stu-id="dd780-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="dd780-122">单击您的全局管理员帐户，然后单击**编辑****产品**许可证。</span><span class="sxs-lookup"><span data-stu-id="dd780-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="dd780-123">**产品许可证**的窗格中，在打开产品许可证**的企业移动性 + 安全 E5**到**上**，单击**保存**，然后两次单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="dd780-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="dd780-124">阶段 2：创建和配置 Azure Active Directory (AD) 组和用户</span><span class="sxs-lookup"><span data-stu-id="dd780-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="dd780-125">此阶段为虚构组织创建和配置 Azure AD 组和用户。</span><span class="sxs-lookup"><span data-stu-id="dd780-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="dd780-126">首先，通过 Azure 门户为典型组织创建一系列组。</span><span class="sxs-lookup"><span data-stu-id="dd780-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="dd780-127">在浏览器中，创建一个单独的选项卡，然后转到在[https://portal.azure.com](https://portal.azure.com)Azure 的门户。如果需要请为您的 Office 365 E5 试用订阅登录的全局管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="dd780-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="dd780-128">在 Azure 门户中，单击“Azure Active Directory”>“用户和组”>“所有组”。</span><span class="sxs-lookup"><span data-stu-id="dd780-128">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="dd780-129">在“所有组”边栏选项卡上，单击“+ 新建组”。</span><span class="sxs-lookup"><span data-stu-id="dd780-129">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="dd780-130">在“组”边栏选项卡上：</span><span class="sxs-lookup"><span data-stu-id="dd780-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="dd780-131">在“名称”中键入“高层管理人员”。</span><span class="sxs-lookup"><span data-stu-id="dd780-131">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="dd780-132">在“成员身份”中选择“已分配”。</span><span class="sxs-lookup"><span data-stu-id="dd780-132">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="dd780-133">对“启用 Office 功能”单击“是”。</span><span class="sxs-lookup"><span data-stu-id="dd780-133">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="dd780-134">单击“创建”，然后关闭“组”边栏选项卡。</span><span class="sxs-lookup"><span data-stu-id="dd780-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="dd780-135">对以下组名称重复步骤 3-5：</span><span class="sxs-lookup"><span data-stu-id="dd780-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="dd780-136">IT 人员</span><span class="sxs-lookup"><span data-stu-id="dd780-136">IT staff</span></span>
    
  - <span data-ttu-id="dd780-137">研究人员</span><span class="sxs-lookup"><span data-stu-id="dd780-137">Research staff</span></span>
    
  - <span data-ttu-id="dd780-138">正式员工</span><span class="sxs-lookup"><span data-stu-id="dd780-138">Regular staff</span></span>
    
  - <span data-ttu-id="dd780-139">市场营销人员</span><span class="sxs-lookup"><span data-stu-id="dd780-139">Marketing staff</span></span>
    
  - <span data-ttu-id="dd780-140">销售人员</span><span class="sxs-lookup"><span data-stu-id="dd780-140">Sales staff</span></span>
    
7. <span data-ttu-id="dd780-141">使浏览器中的 Azure 门户选项卡保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="dd780-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="dd780-142">接下来，您将配置自动授权，使您的组的成员会自动分配为 Office 365 和 EMS 订阅许可证。</span><span class="sxs-lookup"><span data-stu-id="dd780-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="dd780-143">在 Azure 门户中，单击“Azure Active Directory”>“许可证”>“所有产品”。</span><span class="sxs-lookup"><span data-stu-id="dd780-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="dd780-144">在列表中，选择**企业移动 + 安全 E5**和**Office 365 企业 E5**，然后单击**分配**。</span><span class="sxs-lookup"><span data-stu-id="dd780-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="dd780-145">在“分配许可证”边栏选项卡中，单击“用户和组”。</span><span class="sxs-lookup"><span data-stu-id="dd780-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="dd780-146">在组列表中，选择以下各项：</span><span class="sxs-lookup"><span data-stu-id="dd780-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="dd780-147">高层管理人员</span><span class="sxs-lookup"><span data-stu-id="dd780-147">C-Suite</span></span>
    
  - <span data-ttu-id="dd780-148">IT 人员</span><span class="sxs-lookup"><span data-stu-id="dd780-148">IT staff</span></span>
    
  - <span data-ttu-id="dd780-149">研究人员</span><span class="sxs-lookup"><span data-stu-id="dd780-149">Research staff</span></span>
    
  - <span data-ttu-id="dd780-150">正式员工</span><span class="sxs-lookup"><span data-stu-id="dd780-150">Regular staff</span></span>
    
  - <span data-ttu-id="dd780-151">市场营销人员</span><span class="sxs-lookup"><span data-stu-id="dd780-151">Marketing staff</span></span>
    
  - <span data-ttu-id="dd780-152">销售人员</span><span class="sxs-lookup"><span data-stu-id="dd780-152">Sales staff</span></span>
    
5. <span data-ttu-id="dd780-153">单击**选择**，然后单击**分配**。</span><span class="sxs-lookup"><span data-stu-id="dd780-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="dd780-154">关闭浏览器中的 Azure 门户选项卡。</span><span class="sxs-lookup"><span data-stu-id="dd780-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="dd780-155">接下来，[连接到 Azure Active Directory V2 PowerShell 模块](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="dd780-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="dd780-156">填写您的组织名称、 您所在的位置和常见的密码，并再从 PowerShell 命令提示符或集成脚本环境 (ISE) 来创建用户帐户并将其添加到它们的组运行这些命令：</span><span class="sxs-lookup"><span data-stu-id="dd780-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> <span data-ttu-id="dd780-p103">此处使用公用密码旨在自动配置开发/测试环境，简化配置过程。 但不建议生产订阅这样做。</span><span class="sxs-lookup"><span data-stu-id="dd780-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="dd780-159">使用下列步骤验证基于组的授权正常工作。</span><span class="sxs-lookup"><span data-stu-id="dd780-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="dd780-160">在浏览器的“Microsoft Office 主页”标签页中，单击“管理”磁贴。</span><span class="sxs-lookup"><span data-stu-id="dd780-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="dd780-161">在浏览器的新“Office 管理中心”标签页中，单击“用户”。</span><span class="sxs-lookup"><span data-stu-id="dd780-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="dd780-162">在用户列表中，单击“CEO”。</span><span class="sxs-lookup"><span data-stu-id="dd780-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="dd780-163">在列出 CEO 用户帐户属性的窗格中，验证已向其分配“企业移动性 + 安全性 E5”和“Office 365 企业版 E5”许可证（位于“产品许可证”中）。</span><span class="sxs-lookup"><span data-stu-id="dd780-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="dd780-164">阶段 3：创建 Office 365 标签</span><span class="sxs-lookup"><span data-stu-id="dd780-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="dd780-165">此阶段将针对 SharePoint Online 团队网站文档文件夹的不同安全级别创建标签。</span><span class="sxs-lookup"><span data-stu-id="dd780-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="dd780-p104">如果需要请使用 Internet 浏览器的专用实例并登录到您的 Office 365 E5 试用的全局管理员帐户具有 Office 365 门户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="dd780-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dd780-168">在“Microsoft Office 主页”标签页中，单击“管理”磁贴。</span><span class="sxs-lookup"><span data-stu-id="dd780-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="dd780-169">您的浏览器的新**办公室管理中心**标签，请单击**中心管理 > 安全&amp;法规遵从性**。</span><span class="sxs-lookup"><span data-stu-id="dd780-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="dd780-170">从新**家庭-安全&amp;法规遵从性**选项卡上的浏览器中，单击**分类 > 标签**。</span><span class="sxs-lookup"><span data-stu-id="dd780-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="dd780-171">在“开始”>“标签”窗格中，单击“创建标签”。</span><span class="sxs-lookup"><span data-stu-id="dd780-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="dd780-172">在**标签名称**窗格中，键入**内部公共**的，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="dd780-173">在“标签设置”窗格中，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="dd780-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="dd780-174">上的**查看设置**窗格中，单击**创建此标签**，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="dd780-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="dd780-175">对以下标签重复步骤 5-8：</span><span class="sxs-lookup"><span data-stu-id="dd780-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="dd780-176">Private</span><span class="sxs-lookup"><span data-stu-id="dd780-176">Private</span></span>
    
  - <span data-ttu-id="dd780-177">敏感</span><span class="sxs-lookup"><span data-stu-id="dd780-177">Sensitive</span></span>
    
  - <span data-ttu-id="dd780-178">高度机密</span><span class="sxs-lookup"><span data-stu-id="dd780-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="dd780-179">在“开始”>“标签”窗格中，单击“发布标签”。</span><span class="sxs-lookup"><span data-stu-id="dd780-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="dd780-180">在“选择要发布的标签”窗格中，单击“选择要发布的标签”。</span><span class="sxs-lookup"><span data-stu-id="dd780-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="dd780-181">在“选择标签”窗格中，单击“添加”并选择全部四个标签。</span><span class="sxs-lookup"><span data-stu-id="dd780-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="dd780-182">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="dd780-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="dd780-183">在“选择要发布的标签”窗格中，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="dd780-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="dd780-184">在“选择位置”窗格中，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="dd780-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="dd780-185">在**您的策略名称**窗格中，在**名称**中键入**示例组织中**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="dd780-186">上的**查看设置**窗格中，单击**发布标签**，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="dd780-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="dd780-187">阶段 4：创建 SharePoint Online 团队网站</span><span class="sxs-lookup"><span data-stu-id="dd780-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="dd780-188">在此阶段中，将为示例组织创建和配置四种类型的 SharePoint Online 团队网站。</span><span class="sxs-lookup"><span data-stu-id="dd780-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="dd780-189">组织范围团队网站</span><span class="sxs-lookup"><span data-stu-id="dd780-189">Organization wide team site</span></span>

<span data-ttu-id="dd780-190">要创建基线公共 SharePoint Online 团队网站，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="dd780-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="dd780-p105">如果需要，请使用本地计算机上的浏览器，并使用全局管理员帐户登录 Office 365 门户。 如需帮助，请参阅[如何登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="dd780-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dd780-193">在磁贴列表中，单击“SharePoint”。</span><span class="sxs-lookup"><span data-stu-id="dd780-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="dd780-194">在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。</span><span class="sxs-lookup"><span data-stu-id="dd780-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="dd780-195">在“创建网站”页中，单击“团队网站”。</span><span class="sxs-lookup"><span data-stu-id="dd780-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="dd780-196">在“网站名称”中，键入“组织范围”。</span><span class="sxs-lookup"><span data-stu-id="dd780-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="dd780-197">在“团队网站描述”中，键入“用于整个组织的 SharePoint 网站”。</span><span class="sxs-lookup"><span data-stu-id="dd780-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="dd780-198">在**隐私设置**选择**公用-组织中的任何人都可以访问该网站**，，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dd780-199">在“希望添加哪些人员?”窗格中，单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="dd780-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="dd780-200">接下来，针对内部公共标签配置组织范围团队网站的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="dd780-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="dd780-201">在您的浏览器**组织总部范围**选项卡上，单击**文档**。</span><span class="sxs-lookup"><span data-stu-id="dd780-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="dd780-202">单击设置图标，然后单击“库设置”。</span><span class="sxs-lookup"><span data-stu-id="dd780-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="dd780-203">在“权限和管理”下，单击“向此库中的项应用标签”。</span><span class="sxs-lookup"><span data-stu-id="dd780-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="dd780-204">在**设置应用标签**，选择**内部公共**的，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="dd780-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span></span>
    
<span data-ttu-id="dd780-205">生成的配置如下。</span><span class="sxs-lookup"><span data-stu-id="dd780-205">Here is your resulting configuration.</span></span>
  
![适用于全组织公共 SharePoint Online 团队网站的基线级保护。](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="dd780-207">项目 1 团队网站</span><span class="sxs-lookup"><span data-stu-id="dd780-207">Project 1 team site</span></span>

<span data-ttu-id="dd780-208">要为组织内的项目创建基线专用 SharePoint Online 团队网站，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="dd780-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="dd780-p106">如果需要，请使用本地计算机上的浏览器，并使用全局管理员帐户登录 Office 365 门户。 如需帮助，请参阅[如何登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="dd780-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dd780-211">在磁贴列表中，单击“SharePoint”。</span><span class="sxs-lookup"><span data-stu-id="dd780-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="dd780-212">在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。</span><span class="sxs-lookup"><span data-stu-id="dd780-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="dd780-213">在“创建网站”页中，单击“团队网站”。</span><span class="sxs-lookup"><span data-stu-id="dd780-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="dd780-214">在“网站名称”中，键入“项目 1”。</span><span class="sxs-lookup"><span data-stu-id="dd780-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="dd780-215">在**团队站点说明，**键入**项目 1 的 SharePoint 网站**。</span><span class="sxs-lookup"><span data-stu-id="dd780-215">In **Team site description,** type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="dd780-216">在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dd780-217">在“希望添加哪些人员?”窗格中，单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="dd780-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="dd780-218">接下来，针对专用标签配置项目 1 团队网站的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="dd780-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="dd780-219">在浏览器的“项目 1 - 主页”标签页中，单击“文档”。</span><span class="sxs-lookup"><span data-stu-id="dd780-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="dd780-220">单击设置图标，然后单击“库设置”。</span><span class="sxs-lookup"><span data-stu-id="dd780-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="dd780-221">在“权限和管理”下，单击“向此库中的项应用标签”。</span><span class="sxs-lookup"><span data-stu-id="dd780-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="dd780-222">在**设置应用标签**，选择**专用**，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="dd780-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="dd780-223">生成的配置如下。</span><span class="sxs-lookup"><span data-stu-id="dd780-223">Here is your resulting configuration.</span></span>
  
![适用于 Project1 专用 SharePoint Online 团队网站的基线级保护。](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="dd780-225">市场营销活动团队网站</span><span class="sxs-lookup"><span data-stu-id="dd780-225">Marketing campaigns team site</span></span>

<span data-ttu-id="dd780-226">要为市场营销活动资源创建敏感级别的独立 SharePoint Online 团队网站，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="dd780-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="dd780-p107">在您的本地计算机上使用浏览器，登录到 Office 365 门户使用全局管理员帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="dd780-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dd780-229">在磁贴列表中，单击“SharePoint”。</span><span class="sxs-lookup"><span data-stu-id="dd780-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="dd780-230">在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。</span><span class="sxs-lookup"><span data-stu-id="dd780-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="dd780-231">在“创建网站”页中，单击“团队网站”。</span><span class="sxs-lookup"><span data-stu-id="dd780-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="dd780-232">在“团队网站名称”中，键入“市场营销活动”。</span><span class="sxs-lookup"><span data-stu-id="dd780-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="dd780-233">在“团队网站描述”中，键入“用于市场营销活动资源的 SharePoint 网站(敏感)”。</span><span class="sxs-lookup"><span data-stu-id="dd780-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="dd780-234">在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dd780-235">在“希望添加哪些人员?”窗格中，单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="dd780-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="dd780-236">在您的浏览器工具条中，在新的**市场营销活动**选项卡上单击设置图标，然后单击**网站权限**。</span><span class="sxs-lookup"><span data-stu-id="dd780-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="dd780-237">在“网站权限”窗格中，单击“高级权限设置”。</span><span class="sxs-lookup"><span data-stu-id="dd780-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="dd780-238">在浏览器的新“权限”标签页中，单击“访问请求设置”。</span><span class="sxs-lookup"><span data-stu-id="dd780-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="dd780-239">在**访问请求设置**对话框中，清除**允许成员共享的网站和个别文件和文件夹**和**允许成员若要邀请其他人到网站用户组成员**复选框，键入**ITAdmin1 @**\<您组织名称 >**。 onmicrosoft.com**在**将所有访问请求都发送**，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="dd780-239">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="dd780-240">单击列表中的“市场营销活动成员”。</span><span class="sxs-lookup"><span data-stu-id="dd780-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="dd780-241">在“人员和组”页中，单击“新建”。</span><span class="sxs-lookup"><span data-stu-id="dd780-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="dd780-242">在**共享**对话框中，键入**市场营销人员**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="dd780-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="dd780-243">**Researcher1**用户帐户，请重复步骤 14 和 15。</span><span class="sxs-lookup"><span data-stu-id="dd780-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="dd780-244">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="dd780-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="dd780-245">单击列表中的**市场营销活动的所有者**。</span><span class="sxs-lookup"><span data-stu-id="dd780-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="dd780-246">在“人员和组”页中，单击“新建”。</span><span class="sxs-lookup"><span data-stu-id="dd780-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="dd780-247">在**共享**对话框中，键入**的 IT 人员**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="dd780-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="dd780-248">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="dd780-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="dd780-249">关闭您的浏览器中的**用户和用户组**选项卡，单击在浏览器中，**市场营销活动主页**选项卡上，然后关闭**网站权限**窗格。</span><span class="sxs-lookup"><span data-stu-id="dd780-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="dd780-250">权限的配置结果如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd780-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="dd780-251">市场营销活动-成员：SharePoint 组仅包含“市场营销活动”组（其中包含全局管理员用户帐户）、“市场营销人员”组（其中包含 Marketing1 和 Marketing2 用户帐户）以及 Researcher1 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="dd780-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="dd780-252">市场营销活动-所有者：SharePoint 组仅包含“IT 人员”组（其中仅包含 ITAdmin1 和 ITAdmin2 用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="dd780-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="dd780-253">市场营销活动-访问者：SharePoint 组不包含任何组或用户帐户。</span><span class="sxs-lookup"><span data-stu-id="dd780-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="dd780-254">成员不能修改网站级权限（此设置只能由营销活动-所有者组的成员执行）。</span><span class="sxs-lookup"><span data-stu-id="dd780-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="dd780-255">其他用户帐户无法访问网站或它的资源，但可以请求访问该网站，将电子邮件发送给 ITAdmin1 用户帐户邮箱。</span><span class="sxs-lookup"><span data-stu-id="dd780-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="dd780-256">接下来，针对敏感标签配置市场营销活动团队网站的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="dd780-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="dd780-257">在浏览器的“市场营销活动 - 主页”标签页中，单击“文档”。</span><span class="sxs-lookup"><span data-stu-id="dd780-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="dd780-258">单击设置图标，然后单击“库设置”。</span><span class="sxs-lookup"><span data-stu-id="dd780-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="dd780-259">在“权限和管理”下，单击“向此库中的项应用标签”。</span><span class="sxs-lookup"><span data-stu-id="dd780-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="dd780-260">在**设置应用标签**，选择**敏感**，，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="dd780-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="dd780-261">接下来，配置数据丢失防护 (DLP) 策略，以便在用户共享关于含敏感标签的 SharePoint Online 团队网站（包括组织外的营销活动网站）的文档时进行通知。</span><span class="sxs-lookup"><span data-stu-id="dd780-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="dd780-262">从**Microsoft Office 主页**选项卡上的在浏览器中，单击**安全&amp;法规遵从性**平铺。</span><span class="sxs-lookup"><span data-stu-id="dd780-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="dd780-263">对新**安全&amp;法规遵从性**在您的浏览器选项卡上，单击**数据丢失防范 > 策略**。</span><span class="sxs-lookup"><span data-stu-id="dd780-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="dd780-264">在“数据丢失防护”窗格中，单击“+ 创建策略”。</span><span class="sxs-lookup"><span data-stu-id="dd780-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="dd780-265">在**从模板开始创建自定义策略或**窗格中，单击**自定义**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="dd780-266">**名称您的策略**中，在**名称**中键入**敏感标签 SharePoint Online 工作组站点**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="dd780-267">在“选择位置”窗格中，单击“允许选择特定位置”，然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="dd780-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="dd780-268">在位置列表中，禁用**Exchange 电子邮件**帐户和**OneDrive 帐户**位置，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dd780-269">在“自定义要保护的敏感信息类型”窗格中，单击“编辑”。</span><span class="sxs-lookup"><span data-stu-id="dd780-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="dd780-270">在**选择要保护的内容的类型**窗格中，单击下拉列表框中，**添加**，然后单击**标签**。</span><span class="sxs-lookup"><span data-stu-id="dd780-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="dd780-271">在**标签**窗格中，单击**+ 添加**，选择**敏感**标签，单击**添加**，然后单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="dd780-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="dd780-272">在“选择要保护的内容类型”窗格中，单击“保存”。</span><span class="sxs-lookup"><span data-stu-id="dd780-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="dd780-273">在“自定义要保护的敏感信息类型”窗格中，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="dd780-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="dd780-274">在“如果检测到敏感信息，希望采取什么操作?”窗格中，单击“自定义提示和电子邮件”。</span><span class="sxs-lookup"><span data-stu-id="dd780-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="dd780-275">在“自定义策略提示和电子邮件通知”窗格中，单击“自定义策略提示文本”。</span><span class="sxs-lookup"><span data-stu-id="dd780-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="dd780-276">在文本框中，键入或粘贴以下内容：</span><span class="sxs-lookup"><span data-stu-id="dd780-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="dd780-p108">要与组织外部的用户共享，请下载并打开文件。 依次单击“文件”、“保护文档”、“使用密码加密”，然后指定强密码。 通过单独的电子邮件或其他通信方式发送密码。</span><span class="sxs-lookup"><span data-stu-id="dd780-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="dd780-280">单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="dd780-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="dd780-281">在**您想要我们检测敏感信息办？**窗格中，清除**阻止某些人共享，并限制对内容的访问**复选框，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="dd780-282">在**所需的策略或测试的事情，首先打开？**窗格中，单击**是，立即启用**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="dd780-283">在**查看设置**窗格上，单击**创建**，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="dd780-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="dd780-284">生成的配置如下。</span><span class="sxs-lookup"><span data-stu-id="dd780-284">Here is your resulting configuration.</span></span>
  
![适用于市场营销活动专用独立 SharePoint Online 团队网站的敏感级保护。](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="dd780-286">公司策略团队网站</span><span class="sxs-lookup"><span data-stu-id="dd780-286">Company strategy team site</span></span>

<span data-ttu-id="dd780-287">若要针对组织首席执行官的公司战略资源创建高度机密级别的独立 SharePoint Online 团队网站，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="dd780-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="dd780-p109">如果需要，请使用本地计算机上的浏览器，并使用全局管理员帐户登录 Office 365 门户。 如需帮助，请参阅[如何登录到 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="dd780-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dd780-290">在磁贴列表中，单击“SharePoint”。</span><span class="sxs-lookup"><span data-stu-id="dd780-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="dd780-291">在浏览器的新“SharePoint”标签页中，单击“+ 创建网站”。</span><span class="sxs-lookup"><span data-stu-id="dd780-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="dd780-292">在“创建网站”页中，单击“团队网站”。</span><span class="sxs-lookup"><span data-stu-id="dd780-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="dd780-293">在“团队网站名称”中，键入“公司战略”。</span><span class="sxs-lookup"><span data-stu-id="dd780-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="dd780-294">在“团队网站描述”中，键入“针对公司战略的 SharePoint 网站(高度机密)”。</span><span class="sxs-lookup"><span data-stu-id="dd780-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="dd780-295">在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dd780-296">在“希望添加哪些人员?”窗格中，单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="dd780-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="dd780-297">在您的浏览器工具条中，在新的**公司策略**选项卡上单击设置图标，然后单击**网站权限**。</span><span class="sxs-lookup"><span data-stu-id="dd780-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="dd780-298">在“网站权限”窗格中，单击“高级权限设置”。</span><span class="sxs-lookup"><span data-stu-id="dd780-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="dd780-299">在浏览器的新“权限”标签页中，单击“访问请求设置”。</span><span class="sxs-lookup"><span data-stu-id="dd780-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="dd780-300">在**访问请求设置**对话框中，清除**允许成员共享的网站和个别文件和文件夹**，并**允许成员要邀请到网站的成员组的其他人**（以便所有三个复选框都被清除），然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="dd780-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="dd780-301">单击列表中的**成员的公司战略**。</span><span class="sxs-lookup"><span data-stu-id="dd780-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="dd780-302">在“人员和组”页中，单击“新建”。</span><span class="sxs-lookup"><span data-stu-id="dd780-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="dd780-303">在**共享**对话框中，键入**C 套件**，选择它，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="dd780-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="dd780-304">单击列表中的**公司策略的所有者**。</span><span class="sxs-lookup"><span data-stu-id="dd780-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="dd780-305">在“人员和组”页中，单击“新建”。</span><span class="sxs-lookup"><span data-stu-id="dd780-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="dd780-306">在**共享**对话框中，键入**的 IT 人员**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="dd780-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="dd780-307">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="dd780-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="dd780-308">关闭您的浏览器中的**用户和用户组**选项卡，单击您的浏览器中的**公司战略总部**选项卡，然后关闭**网站权限**窗格。</span><span class="sxs-lookup"><span data-stu-id="dd780-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="dd780-309">权限的配置结果如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd780-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="dd780-310">公司战略-成员：SharePoint 组仅包含“高层管理人员”组（其中仅包含 CEO、CFO和 CIO 用户帐户）和“公司战略”组（其中仅包含全局管理员用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="dd780-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="dd780-311">**公司战略负责人**SharePoint 组包含仅**IT staff**组 （其中包含仅 ITAdmin1 和 ITAdmin2 用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="dd780-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="dd780-312">公司战略-访问者：SharePoint 组不包含任何组或用户帐户。</span><span class="sxs-lookup"><span data-stu-id="dd780-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="dd780-313">成员不能修改网站级别权限（仅“公司战略-所有者”组的成员才可进行修改）。</span><span class="sxs-lookup"><span data-stu-id="dd780-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="dd780-p110">其他用户帐户无法访问网站或其资源，也无法请求访问网站。 网站的其他权限必须由全局管理员或“公司战略-所有者”组的成员履行。</span><span class="sxs-lookup"><span data-stu-id="dd780-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="dd780-316">接下来，针对高度机密标签配置公司战略团队网站的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="dd780-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="dd780-317">在浏览器的“公司战略-主页”标签页中，单击“文档”。</span><span class="sxs-lookup"><span data-stu-id="dd780-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="dd780-318">单击设置图标，然后单击“库设置”。</span><span class="sxs-lookup"><span data-stu-id="dd780-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="dd780-319">在“权限和管理”下，单击“向此库中的项应用标签”。</span><span class="sxs-lookup"><span data-stu-id="dd780-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="dd780-320">在**设置应用标签**，选择**高度机密**，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="dd780-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="dd780-321">接下来，配置 DLP 策略，当用户在具有“高度机密”标签的 SharePoint Online 团队网站（包括组织外的公司战略网站）上共享文档时，该策略会阻止用户。</span><span class="sxs-lookup"><span data-stu-id="dd780-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="dd780-p111">如果需要请使用本地计算机上的浏览器，到 Office 365 门户拥有安全管理员或公司管理员角色的帐户登录。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="dd780-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dd780-324">从**Microsoft Office 主页**选项卡上的在浏览器中，单击**安全&amp;法规遵从性**平铺。</span><span class="sxs-lookup"><span data-stu-id="dd780-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="dd780-325">对新**安全&amp;法规遵从性**在您的浏览器选项卡上，单击**数据丢失防范 > 策略**。</span><span class="sxs-lookup"><span data-stu-id="dd780-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="dd780-326">在“数据丢失防护”窗格中，单击“+ 创建策略”。</span><span class="sxs-lookup"><span data-stu-id="dd780-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="dd780-327">在**从模板开始创建自定义策略或**窗格中，单击**自定义**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="dd780-328">**名称您的策略**中，在**名称**中键入**高度机密的标签 SharePoint Online 工作组站点**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="dd780-329">在“选择位置”窗格中，单击“允许选择特定位置”，然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="dd780-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="dd780-330">在位置列表中，禁用**Exchange 电子邮件**帐户和**OneDrive 帐户**位置，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="dd780-331">在“自定义要保护的敏感信息类型”窗格中，单击“编辑”。</span><span class="sxs-lookup"><span data-stu-id="dd780-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="dd780-332">在**选择要保护的内容的类型**窗格中，单击下拉列表框中，**添加**，然后单击**标签**。</span><span class="sxs-lookup"><span data-stu-id="dd780-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="dd780-333">**标签**的窗格中，单击**+ 添加**，选择**高度机密**标签，单击**添加**，然后单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="dd780-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="dd780-334">在“选择要保护的内容类型”窗格中，单击“保存”。</span><span class="sxs-lookup"><span data-stu-id="dd780-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="dd780-335">在“自定义要保护的敏感信息类型”窗格中，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="dd780-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="dd780-336">在“如果检测到敏感信息，希望采取什么操作?”窗格中，单击“自定义提示和电子邮件”。</span><span class="sxs-lookup"><span data-stu-id="dd780-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="dd780-337">在“自定义策略提示和电子邮件通知”窗格中，单击“自定义策略提示文本”。</span><span class="sxs-lookup"><span data-stu-id="dd780-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="dd780-338">在文本框中，键入或粘贴以下内容：</span><span class="sxs-lookup"><span data-stu-id="dd780-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="dd780-p112">要与组织外部的用户共享，请下载并打开文件。 依次单击“文件”、“保护文档”、“使用密码加密”，然后指定强密码。 通过单独的电子邮件或其他通信方式发送密码。</span><span class="sxs-lookup"><span data-stu-id="dd780-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="dd780-342">单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="dd780-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="dd780-343">在**您想要我们检测敏感信息办？**窗格中，选择**需要重写的理由**，然后再单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="dd780-344">在**所需的策略或测试的事情，首先打开？**窗格中，单击**是，立即启用**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="dd780-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="dd780-345">在**查看设置**窗格上，单击**创建**，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="dd780-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="dd780-346">接下来，按照[使用 Office 365 管理中心激活 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) 中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="dd780-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="dd780-347">接下来，通过执行以下步骤，使用新作用域内策略以及保护和权限的子标签来配置 Azure 信息保护：</span><span class="sxs-lookup"><span data-stu-id="dd780-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="dd780-p113">Office 365 门户拥有安全管理员或公司管理员角色的帐户登录。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="dd780-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="dd780-350">在浏览器的单独选项卡中，转到 Azure 门户 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="dd780-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="dd780-351">如果这是首次配置 Azure 信息保护，请参见以下[说明](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。</span><span class="sxs-lookup"><span data-stu-id="dd780-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="dd780-352">在列表窗格中，单击**更多服务**，键入**信息**，，然后单击**Azure 信息保护**。</span><span class="sxs-lookup"><span data-stu-id="dd780-352">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="dd780-353">**Azure 信息保护**刀片式服务器，，单击**范围策略 > 添加新策略 +**。</span><span class="sxs-lookup"><span data-stu-id="dd780-353">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="dd780-354">在“策略名称”中键入“CompanyStrategy”，并在“描述”中键入“公司策略团队网站中文档的标签”。</span><span class="sxs-lookup"><span data-stu-id="dd780-354">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="dd780-355">单击“选择获取此策略的用户或组”>“用户/组”，然后选择“高层管理人员”。</span><span class="sxs-lookup"><span data-stu-id="dd780-355">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="dd780-356">单击“选择”>“确定”。</span><span class="sxs-lookup"><span data-stu-id="dd780-356">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="dd780-357">对于“高度机密”标签，请单击省略号 (…)，然后单击“添加子标签”。</span><span class="sxs-lookup"><span data-stu-id="dd780-357">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="dd780-358">在“名称”中键入子标签的名称，并在“描述”中键入标签的描述。</span><span class="sxs-lookup"><span data-stu-id="dd780-358">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="dd780-359">在“为包含此标签的文档和电子邮件设置权限”中，单击“保护”。</span><span class="sxs-lookup"><span data-stu-id="dd780-359">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="dd780-360">在“保护”部分中，单击“Azure (云密钥)”。</span><span class="sxs-lookup"><span data-stu-id="dd780-360">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="dd780-361">在“保护”边栏选项卡中，在“保护设置”下，单击“+ 添加权限”。</span><span class="sxs-lookup"><span data-stu-id="dd780-361">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="dd780-362">在“添加权限”边栏选项卡的“指定用户和组”下，单击“+ 浏览目录”。</span><span class="sxs-lookup"><span data-stu-id="dd780-362">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="dd780-363">在**AAD 的用户和组**窗格中，选择**C 套件**，，然后单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="dd780-363">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="dd780-364">在**选择权限从预设**清除**打印**、**复制和内容的提取**和**转发**复选框。</span><span class="sxs-lookup"><span data-stu-id="dd780-364">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="dd780-365">单击**确定**两次。</span><span class="sxs-lookup"><span data-stu-id="dd780-365">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="dd780-366">在“子标签”边栏选项卡上，单击“保存”。</span><span class="sxs-lookup"><span data-stu-id="dd780-366">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="dd780-367">关闭“新作用域内策略”边栏选项卡。</span><span class="sxs-lookup"><span data-stu-id="dd780-367">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="dd780-368">在**Azure 信息保护的指定了作用域策略**刀片式服务器，单击**发布**，然后单击**是**。</span><span class="sxs-lookup"><span data-stu-id="dd780-368">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="dd780-369">要保护与 Azure 的信息保护和此新的标签文档，则必须在测试机器上[安装 Azure 信息保护客户端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)、 从 Office 365 管理门户安装 Office，**中的帐户然后登录从 Microsoft WordC 套件**组您的订购试用期。</span><span class="sxs-lookup"><span data-stu-id="dd780-369">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **C-Suite** group of your trial subscription.</span></span>
  
<span data-ttu-id="dd780-370">生成的配置如下。</span><span class="sxs-lookup"><span data-stu-id="dd780-370">Here is your resulting configuration.</span></span>
  
![适用于公司策略专用独立 SharePoint Online 团队网站的高度机密级保护。](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="dd780-372">现在，可以在这四个网站中创建文档，并使用试用订阅中的各种用户帐户进行访问测试。</span><span class="sxs-lookup"><span data-stu-id="dd780-372">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="dd780-373">下面是针对全部四个 SharePoint Online 团队网站的整体配置。</span><span class="sxs-lookup"><span data-stu-id="dd780-373">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![安全 SharePoint Online 开发/测试环境中的所有四个团队网站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="dd780-375">后续步骤</span><span class="sxs-lookup"><span data-stu-id="dd780-375">Next step</span></span>

<span data-ttu-id="dd780-376">如果已准备好进行安全 SharePoint Online 网站的生产部署，请参阅[保护 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)，了解详细信息，获取分步部署文章的链接。</span><span class="sxs-lookup"><span data-stu-id="dd780-376">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dd780-377">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd780-377">See Also</span></span>

[<span data-ttu-id="dd780-378">SharePoint Online 网站和文件保护</span><span class="sxs-lookup"><span data-stu-id="dd780-378">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="dd780-379">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="dd780-379">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="dd780-380">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="dd780-380">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="dd780-381">为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南</span><span class="sxs-lookup"><span data-stu-id="dd780-381">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




