---
title: "开发/测试环境中的安全 SharePoint Online 网站"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "摘要： 在开发/测试环境中创建公共、 私人、 敏感和高度机密 SharePoint Online 的工作组网站。"
ms.openlocfilehash: 17abee7a293996194a097693607b4b4d9c117046
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="96774-103">开发/测试环境中的安全 SharePoint Online 网站</span><span class="sxs-lookup"><span data-stu-id="96774-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="96774-104">**摘要：**开发/测试环境中创建公共、 私人、 敏感和高度机密 SharePoint Online 的工作组网站。</span><span class="sxs-lookup"><span data-stu-id="96774-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="96774-105">本文提供了分步说明创建包含四种不同类型的[安全 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)解决方案的 SharePoint Online 工作组站点的开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="96774-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span></span>
  
![安全 SharePoint Online 开发/测试环境中的所有四个团队网站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="96774-107">使用这种开发/测试环境试验信息保护行为和微调您的特定需求部署 SharePoint Online 的工作组站点，在生产前的设置。</span><span class="sxs-lookup"><span data-stu-id="96774-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="96774-108">阶段 1： 创建您的开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="96774-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="96774-109">在此阶段中，您将获得试用版本 Office 365 和企业移动性 + 安全为虚构的组织。</span><span class="sxs-lookup"><span data-stu-id="96774-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="96774-110">首先，按照**第二阶段**的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="96774-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="96774-111">接下来，EMS 试用订阅注册，即可将其添加到作为 Office 365 的试用订阅的同一组织。</span><span class="sxs-lookup"><span data-stu-id="96774-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="96774-p101">如果需要请登录到您的订购试用期的全局管理员帐户的凭据对 Office 365 门户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="96774-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="96774-114">单击**管理**拼贴。</span><span class="sxs-lookup"><span data-stu-id="96774-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="96774-115">在浏览器中，在左边的导航中， **Office 管理中心**选项卡单击**计费 > 购买服务**。</span><span class="sxs-lookup"><span data-stu-id="96774-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="96774-p102">**购买服务**页上找到**企业移动 + 安全 E5**项。将鼠标指针悬停在其上，单击**启动免费试用版**。</span><span class="sxs-lookup"><span data-stu-id="96774-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="96774-118">在**确认订单**页中，单击**立即尝试**。</span><span class="sxs-lookup"><span data-stu-id="96774-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="96774-119">在**订单收据**页上，单击**继续**。</span><span class="sxs-lookup"><span data-stu-id="96774-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="96774-120">下一步，使企业移动性 + 您的全局管理员帐户的安全 E5 许可证。</span><span class="sxs-lookup"><span data-stu-id="96774-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="96774-121">在浏览器中，在左边的导航中， **Office 365 管理中心**选项卡单击**用户 > 活动用户**。</span><span class="sxs-lookup"><span data-stu-id="96774-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="96774-122">单击您的全局管理员帐户，然后单击**编辑****产品**许可证。</span><span class="sxs-lookup"><span data-stu-id="96774-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="96774-123">**产品许可证**的窗格中，在打开产品许可证**的企业移动性 + 安全 E5**到**上**，单击**保存**，然后两次单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="96774-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="96774-124">第 2 阶段： 创建和配置您的 Azure 活动目录 (AD) 组和用户</span><span class="sxs-lookup"><span data-stu-id="96774-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="96774-125">在此阶段中，您将创建和配置虚拟组织 Azure AD 组和用户。</span><span class="sxs-lookup"><span data-stu-id="96774-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="96774-126">首先，Azure 门户创建一组典型组织为组。</span><span class="sxs-lookup"><span data-stu-id="96774-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="96774-127">在浏览器中，创建一个单独的选项卡，然后转到在[https://portal.azure.com](https://portal.azure.com)Azure 的门户。如果需要请为您的 Office 365 E5 试用订阅登录的全局管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="96774-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="96774-128">在 Azure 的门户，单击**Azure Active Directory > 用户和组 > 所有组**。</span><span class="sxs-lookup"><span data-stu-id="96774-128">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="96774-129">**所有组**刀片式服务器，请单击**+ 新组**。</span><span class="sxs-lookup"><span data-stu-id="96774-129">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="96774-130">在**组**刀片具有：</span><span class="sxs-lookup"><span data-stu-id="96774-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="96774-131">在**名称**类型**C 套件**。</span><span class="sxs-lookup"><span data-stu-id="96774-131">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="96774-132">在**成员资格**，请选择**分配**。</span><span class="sxs-lookup"><span data-stu-id="96774-132">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="96774-133">**启用 Office 功能**，请单击**是**。</span><span class="sxs-lookup"><span data-stu-id="96774-133">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="96774-134">单击**创建**，然后关闭**组**刀片。</span><span class="sxs-lookup"><span data-stu-id="96774-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="96774-135">重复步骤 3-5 下面的组名：</span><span class="sxs-lookup"><span data-stu-id="96774-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="96774-136">IT 人员</span><span class="sxs-lookup"><span data-stu-id="96774-136">IT staff</span></span>
    
  - <span data-ttu-id="96774-137">调查人员</span><span class="sxs-lookup"><span data-stu-id="96774-137">Research staff</span></span>
    
  - <span data-ttu-id="96774-138">定期的员工</span><span class="sxs-lookup"><span data-stu-id="96774-138">Regular staff</span></span>
    
  - <span data-ttu-id="96774-139">市场营销人员</span><span class="sxs-lookup"><span data-stu-id="96774-139">Marketing staff</span></span>
    
  - <span data-ttu-id="96774-140">销售人员</span><span class="sxs-lookup"><span data-stu-id="96774-140">Sales staff</span></span>
    
7. <span data-ttu-id="96774-141">请在您的浏览器打开 Azure 门户选项卡。</span><span class="sxs-lookup"><span data-stu-id="96774-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="96774-142">接下来，您将配置自动授权，使您的组的成员会自动分配为 Office 365 和 EMS 订阅许可证。</span><span class="sxs-lookup"><span data-stu-id="96774-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="96774-143">在 Azure 的门户，单击**Azure Active Directory > 许可证 > 所有产品**。</span><span class="sxs-lookup"><span data-stu-id="96774-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="96774-144">在列表中，选择**企业移动 + 安全 E5**和**Office 365 企业 E5**，然后单击**分配**。</span><span class="sxs-lookup"><span data-stu-id="96774-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="96774-145">在**分派许可证**刀片式服务器，单击**用户和组**。</span><span class="sxs-lookup"><span data-stu-id="96774-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="96774-146">在组列表中，选择下列设置：</span><span class="sxs-lookup"><span data-stu-id="96774-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="96774-147">C 套件</span><span class="sxs-lookup"><span data-stu-id="96774-147">C-Suite</span></span>
    
  - <span data-ttu-id="96774-148">IT 人员</span><span class="sxs-lookup"><span data-stu-id="96774-148">IT staff</span></span>
    
  - <span data-ttu-id="96774-149">调查人员</span><span class="sxs-lookup"><span data-stu-id="96774-149">Research staff</span></span>
    
  - <span data-ttu-id="96774-150">定期的员工</span><span class="sxs-lookup"><span data-stu-id="96774-150">Regular staff</span></span>
    
  - <span data-ttu-id="96774-151">市场营销人员</span><span class="sxs-lookup"><span data-stu-id="96774-151">Marketing staff</span></span>
    
  - <span data-ttu-id="96774-152">销售人员</span><span class="sxs-lookup"><span data-stu-id="96774-152">Sales staff</span></span>
    
5. <span data-ttu-id="96774-153">单击**选择**，然后单击**分配**。</span><span class="sxs-lookup"><span data-stu-id="96774-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="96774-154">关闭您的浏览器中的 Azure 门户选项卡。</span><span class="sxs-lookup"><span data-stu-id="96774-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="96774-155">然后，您[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="96774-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="96774-156">填写您的组织名称、 您所在的位置和常见的密码，并再从 PowerShell 命令提示符或集成脚本环境 (ISE) 来创建用户帐户并将其添加到它们的组运行这些命令：</span><span class="sxs-lookup"><span data-stu-id="96774-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span></span>
  
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
> <span data-ttu-id="96774-p103">使用常见是配置的密码的自动化和易于开发/测试环境。不推荐用于生产订阅。</span><span class="sxs-lookup"><span data-stu-id="96774-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="96774-159">使用下列步骤验证基于组的授权正常工作。</span><span class="sxs-lookup"><span data-stu-id="96774-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="96774-160">从浏览器的**Microsoft Office 主页**选项卡上，单击**管理**拼贴。</span><span class="sxs-lookup"><span data-stu-id="96774-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="96774-161">您的浏览器的新**办公室管理中心**标签，单击**用户**。</span><span class="sxs-lookup"><span data-stu-id="96774-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="96774-162">在用户列表中，单击**首席执行官**。</span><span class="sxs-lookup"><span data-stu-id="96774-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="96774-163">在列出的**首席执行官**的用户帐户的属性窗格中，验证其具有已分配的 （在**产品许可证**） 的**企业移动 + 安全 E5**和**Office 365 企业 E5**许可证。</span><span class="sxs-lookup"><span data-stu-id="96774-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="96774-164">阶段 3： 创建 Office 365 的标签</span><span class="sxs-lookup"><span data-stu-id="96774-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="96774-165">在此阶段中，您创建的标签进行不同级别的 SharePoint Online 团队站点的文档文件夹的安全性。</span><span class="sxs-lookup"><span data-stu-id="96774-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="96774-p104">如果需要请使用 Internet 浏览器的专用实例并登录到您的 Office 365 E5 试用的全局管理员帐户具有 Office 365 门户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="96774-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="96774-168">**Microsoft Office 主页**选项卡中，单击**管理**拼贴。</span><span class="sxs-lookup"><span data-stu-id="96774-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="96774-169">您的浏览器的新**办公室管理中心**标签，请单击**中心管理 > 安全&amp;法规遵从性**。</span><span class="sxs-lookup"><span data-stu-id="96774-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="96774-170">从新**家庭-安全&amp;法规遵从性**选项卡上的浏览器中，单击**分类 > 标签**。</span><span class="sxs-lookup"><span data-stu-id="96774-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="96774-171">从**主页 > 标签**窗格中，单击**创建一个标签**。</span><span class="sxs-lookup"><span data-stu-id="96774-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="96774-172">在**标签名称**窗格中，键入**内部公共**的，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="96774-173">在**标签设置**窗格中，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="96774-174">上的**查看设置**窗格中，单击**创建此标签**，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="96774-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="96774-175">这些附加的标签，请重复步骤 5 到 8:</span><span class="sxs-lookup"><span data-stu-id="96774-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="96774-176">专用</span><span class="sxs-lookup"><span data-stu-id="96774-176">Private</span></span>
    
  - <span data-ttu-id="96774-177">敏感</span><span class="sxs-lookup"><span data-stu-id="96774-177">Sensitive</span></span>
    
  - <span data-ttu-id="96774-178">高度机密</span><span class="sxs-lookup"><span data-stu-id="96774-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="96774-179">从**主页 > 标签**窗格中，单击**发布标签**。</span><span class="sxs-lookup"><span data-stu-id="96774-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="96774-180">在**选择要发布的标签**窗格上，单击**发布选择标志**。</span><span class="sxs-lookup"><span data-stu-id="96774-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="96774-181">在**选择标签**窗格中，单击**添加**，选择所有四个标签。</span><span class="sxs-lookup"><span data-stu-id="96774-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="96774-182">单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="96774-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="96774-183">在**选择要发布的标签**窗格上，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="96774-184">在**选择位置**窗格中，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="96774-185">在**您的策略名称**窗格中，在**名称**中键入**示例组织中**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="96774-186">上的**查看设置**窗格中，单击**发布标签**，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="96774-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="96774-187">阶段 4： 创建 SharePoint Online 团队站点</span><span class="sxs-lookup"><span data-stu-id="96774-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="96774-188">在此阶段中，您将创建和配置示例组织在线 SharePoint 工作组网站的四种类型。</span><span class="sxs-lookup"><span data-stu-id="96774-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="96774-189">组织范围的工作组站点</span><span class="sxs-lookup"><span data-stu-id="96774-189">Organization wide team site</span></span>

<span data-ttu-id="96774-190">要创建基准公共联机 SharePoint 工作组网站，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="96774-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="96774-p105">如果需要请使用本地计算机上的浏览器和登录到 Office 365 门户使用全局管理员帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="96774-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="96774-193">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="96774-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="96774-194">在您的浏览器新**SharePoint**选项卡上，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="96774-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="96774-195">在**创建网站**页上，单击**工作组网站**。</span><span class="sxs-lookup"><span data-stu-id="96774-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="96774-196">在**站点名称**中，键入**组织范围**。</span><span class="sxs-lookup"><span data-stu-id="96774-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="96774-197">在**团队站点的说明**中，键入**整个组织的 SharePoint 网站**。</span><span class="sxs-lookup"><span data-stu-id="96774-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="96774-198">在**隐私设置**选择**公用-组织中的任何人都可以访问该网站**，，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="96774-199">在**谁您想要添加？**窗格中，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="96774-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="96774-200">接下来，配置内部公共标签组织范围的工作组网站的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="96774-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="96774-201">在您的浏览器**组织总部范围**选项卡上，单击**文档**。</span><span class="sxs-lookup"><span data-stu-id="96774-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="96774-202">单击设置图标，然后单击**库设置**。</span><span class="sxs-lookup"><span data-stu-id="96774-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="96774-203">在**权限和管理**，请单击**应用于此库中的项目的标签**。</span><span class="sxs-lookup"><span data-stu-id="96774-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="96774-204">在**设置应用标签**，选择**内部公共**的，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="96774-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span></span>
    
<span data-ttu-id="96774-205">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="96774-205">Here is your resulting configuration.</span></span>
  
![适用于全组织公共 SharePoint Online 团队网站的基线级保护。](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="96774-207">项目 1 工作组网站</span><span class="sxs-lookup"><span data-stu-id="96774-207">Project 1 team site</span></span>

<span data-ttu-id="96774-208">若要创建比较基准专用 SharePoint 联机工作组网站在组织内的项目，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="96774-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="96774-p106">如果需要请使用本地计算机上的浏览器和登录到 Office 365 门户使用全局管理员帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="96774-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="96774-211">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="96774-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="96774-212">在您的浏览器新**SharePoint**选项卡上，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="96774-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="96774-213">在**创建网站**页上，单击**工作组网站**。</span><span class="sxs-lookup"><span data-stu-id="96774-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="96774-214">在**站点名称**中，键入**项目 1**。</span><span class="sxs-lookup"><span data-stu-id="96774-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="96774-215">在**团队站点说明，**键入**项目 1 的 SharePoint 网站**。</span><span class="sxs-lookup"><span data-stu-id="96774-215">In **Team site description,** type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="96774-216">在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="96774-217">在**谁您想要添加？**窗格中，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="96774-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="96774-218">接下来，配置专用标签项目 1 工作组网站的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="96774-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="96774-219">在您的浏览器**项目 1-主页**选项卡上，单击**文档**。</span><span class="sxs-lookup"><span data-stu-id="96774-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="96774-220">单击设置图标，然后单击**库设置**。</span><span class="sxs-lookup"><span data-stu-id="96774-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="96774-221">在**权限和管理**，请单击**应用于此库中的项目的标签**。</span><span class="sxs-lookup"><span data-stu-id="96774-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="96774-222">在**设置应用标签**，选择**专用**，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="96774-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="96774-223">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="96774-223">Here is your resulting configuration.</span></span>
  
![适用于 Project1 专用 SharePoint Online 团队网站的基线级保护。](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="96774-225">市场营销活动团队站点</span><span class="sxs-lookup"><span data-stu-id="96774-225">Marketing campaigns team site</span></span>

<span data-ttu-id="96774-226">若要创建区分级别独立的 SharePoint Online 工作组站点使用市场活动资源的市场营销活动，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="96774-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="96774-p107">在您的本地计算机上使用浏览器，登录到 Office 365 门户使用全局管理员帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="96774-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="96774-229">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="96774-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="96774-230">在您的浏览器新**SharePoint**选项卡上，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="96774-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="96774-231">在**创建网站**页上，单击**工作组网站**。</span><span class="sxs-lookup"><span data-stu-id="96774-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="96774-232">在**团队站点名称**，键入**营销活动**。</span><span class="sxs-lookup"><span data-stu-id="96774-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="96774-233">在**团队站点的说明**中，键入**（敏感） 的市场营销活动资源的 SharePoint 网站**。</span><span class="sxs-lookup"><span data-stu-id="96774-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="96774-234">在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="96774-235">在**谁您想要添加？**窗格中，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="96774-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="96774-236">在您的浏览器工具条中，在新的**市场营销活动**选项卡上单击设置图标，然后单击**网站权限**。</span><span class="sxs-lookup"><span data-stu-id="96774-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="96774-237">在**网站权限**窗格中，单击**高级的权限设置**。</span><span class="sxs-lookup"><span data-stu-id="96774-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="96774-238">在新**权限**选项卡浏览器中，单击**访问请求设置**。</span><span class="sxs-lookup"><span data-stu-id="96774-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="96774-239">在**访问请求设置**对话框中，清除**允许成员共享的网站和个别文件和文件夹**和**允许成员若要邀请其他人到网站用户组成员**复选框，键入**ITAdmin1 @**\<您组织名称 >**。 onmicrosoft.com**在**将所有访问请求都发送**，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="96774-239">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="96774-240">单击列表中的**成员的市场营销活动**。</span><span class="sxs-lookup"><span data-stu-id="96774-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="96774-241">在**用户和用户组**页上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="96774-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="96774-242">在**共享**对话框中，键入**市场营销人员**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="96774-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="96774-243">**Researcher1**用户帐户，请重复步骤 14 和 15。</span><span class="sxs-lookup"><span data-stu-id="96774-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="96774-244">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="96774-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="96774-245">单击列表中的**市场营销活动的所有者**。</span><span class="sxs-lookup"><span data-stu-id="96774-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="96774-246">在**用户和用户组**页上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="96774-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="96774-247">在**共享**对话框中，键入**的 IT 人员**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="96774-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="96774-248">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="96774-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="96774-249">关闭您的浏览器中的**用户和用户组**选项卡，单击在浏览器中，**市场营销活动主页**选项卡上，然后关闭**网站权限**窗格。</span><span class="sxs-lookup"><span data-stu-id="96774-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="96774-250">下面介绍了权限配置结果：</span><span class="sxs-lookup"><span data-stu-id="96774-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="96774-251">**市场营销活动成员**SharePoint 组包含只有**市场营销活动**组 （其中包含全局管理员用户帐号）、**市场营销人员**组 （其中包含 Marketing1 和 Marketing2 的用户帐户），和**Researcher1**的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="96774-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="96774-252">**市场活动负责人**SharePoint 组包含仅**IT staff**组 （其中包含仅 ITAdmin1 和 ITAdmin2 用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="96774-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="96774-253">**市场活动者**SharePoint 组中包含任何组或用户帐户。</span><span class="sxs-lookup"><span data-stu-id="96774-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="96774-254">成员不能修改网站级别的权限 （仅进行这种**营销活动所有者**组的成员）。</span><span class="sxs-lookup"><span data-stu-id="96774-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="96774-255">其他用户帐户无法访问网站或它的资源，但可以请求访问该网站，将电子邮件发送给 ITAdmin1 用户帐户邮箱。</span><span class="sxs-lookup"><span data-stu-id="96774-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="96774-256">接下来，配置敏感标签的市场营销活动工作组网站的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="96774-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="96774-257">在浏览器的**营销活动主页**选项卡上，单击**文档**。</span><span class="sxs-lookup"><span data-stu-id="96774-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="96774-258">单击设置图标，然后单击**库设置**。</span><span class="sxs-lookup"><span data-stu-id="96774-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="96774-259">在**权限和管理**，请单击**应用于此库中的项目的标签**。</span><span class="sxs-lookup"><span data-stu-id="96774-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="96774-260">在**设置应用标签**，选择**敏感**，，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="96774-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="96774-261">接下来，将他们与敏感的标签，其中包括市场营销活动站点，组织外的共享联机 SharePoint 工作组网站上的文档时通知用户的数据丢失防护 (DLP) 策略的配置。</span><span class="sxs-lookup"><span data-stu-id="96774-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="96774-262">从**Microsoft Office 主页**选项卡上的在浏览器中，单击**安全&amp;法规遵从性**平铺。</span><span class="sxs-lookup"><span data-stu-id="96774-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="96774-263">对新**安全&amp;法规遵从性**在您的浏览器选项卡上，单击**数据丢失防范 > 策略**。</span><span class="sxs-lookup"><span data-stu-id="96774-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="96774-264">在**数据丢失防范**窗格中，单击**+ 创建策略**。</span><span class="sxs-lookup"><span data-stu-id="96774-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="96774-265">在**从模板开始创建自定义策略或**窗格中，单击**自定义**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="96774-266">**名称您的策略**中，在**名称**中键入**敏感标签 SharePoint Online 工作组站点**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="96774-267">在**选择位置**窗格中，**让我来选择特定的位置**，请单击，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="96774-268">在位置列表中，禁用**Exchange 电子邮件**帐户和**OneDrive 帐户**位置，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="96774-269">在**自定义类型您想要保护的敏感信息**窗格中，单击**编辑**。</span><span class="sxs-lookup"><span data-stu-id="96774-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="96774-270">在**选择要保护的内容的类型**窗格中，单击下拉列表框中，**添加**，然后单击**标签**。</span><span class="sxs-lookup"><span data-stu-id="96774-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="96774-271">在**标签**窗格中，单击**+ 添加**，选择**敏感**标签，单击**添加**，然后单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="96774-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="96774-272">在**选择要保护的内容的类型**窗格中，单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="96774-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="96774-273">在**自定义类型您想要保护的敏感信息**窗格中，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="96774-274">在**您想要我们检测敏感信息办？**窗格中，单击**自定义提示和电子邮件**。</span><span class="sxs-lookup"><span data-stu-id="96774-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="96774-275">在**自定义策略的提示和电子邮件通知**窗格中，单击**自定义策略提示文本**。</span><span class="sxs-lookup"><span data-stu-id="96774-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="96774-276">在文本框中，键入或粘贴以下：</span><span class="sxs-lookup"><span data-stu-id="96774-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="96774-p108">若要与组织外部的用户共享，下载该文件，然后将其打开。单击文件然后保护文档，然后使用密码加密和再指定一个强密码。在另一个电子邮件或其他通讯手段发送密码。</span><span class="sxs-lookup"><span data-stu-id="96774-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="96774-280">单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="96774-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="96774-281">在**您想要我们检测敏感信息办？**窗格中，清除**阻止某些人共享，并限制对内容的访问**复选框，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="96774-282">在**所需的策略或测试的事情，首先打开？**窗格中，单击**是，立即启用**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="96774-283">在**查看设置**窗格上，单击**创建**，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="96774-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="96774-284">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="96774-284">Here is your resulting configuration.</span></span>
  
![适用于市场营销活动专用独立 SharePoint Online 团队网站的敏感级保护。](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="96774-286">公司战略工作组网站</span><span class="sxs-lookup"><span data-stu-id="96774-286">Company strategy team site</span></span>

<span data-ttu-id="96774-287">组织的首席执行官的公司战略资源的高度机密级别创建独立的在线 SharePoint 工作组网站，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="96774-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="96774-p109">如果需要请使用本地计算机上的浏览器和登录到 Office 365 门户使用全局管理员帐户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="96774-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="96774-290">在图块的列表中，单击**SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="96774-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="96774-291">在您的浏览器新**SharePoint**选项卡上，单击**+ 创建网站**。</span><span class="sxs-lookup"><span data-stu-id="96774-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="96774-292">在**创建网站**页上，单击**工作组网站**。</span><span class="sxs-lookup"><span data-stu-id="96774-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="96774-293">在**团队站点名称**框中，键入**公司战略**。</span><span class="sxs-lookup"><span data-stu-id="96774-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="96774-294">在**团队站点的说明**中，键入**SharePoint 网站上 （高度机密） 的公司战略**。</span><span class="sxs-lookup"><span data-stu-id="96774-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="96774-295">在**隐私设置**，选择**专用的只有成员才能访问此网站**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="96774-296">在**谁您想要添加？**窗格中，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="96774-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="96774-297">在您的浏览器工具条中，在新的**公司策略**选项卡上单击设置图标，然后单击**网站权限**。</span><span class="sxs-lookup"><span data-stu-id="96774-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="96774-298">在**网站权限**窗格中，单击**高级的权限设置**。</span><span class="sxs-lookup"><span data-stu-id="96774-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="96774-299">在新**权限**选项卡浏览器中，单击**访问请求设置**。</span><span class="sxs-lookup"><span data-stu-id="96774-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="96774-300">在**访问请求设置**对话框中，清除**允许成员共享的网站和个别文件和文件夹**，并**允许成员要邀请到网站的成员组的其他人**（以便所有三个复选框都被清除），然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="96774-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="96774-301">单击列表中的**成员的公司战略**。</span><span class="sxs-lookup"><span data-stu-id="96774-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="96774-302">在**用户和用户组**页上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="96774-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="96774-303">在**共享**对话框中，键入**C 套件**，选择它，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="96774-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="96774-304">单击列表中的**公司策略的所有者**。</span><span class="sxs-lookup"><span data-stu-id="96774-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="96774-305">在**用户和用户组**页上，单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="96774-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="96774-306">在**共享**对话框中，键入**的 IT 人员**，选择它，，然后单击**共享**。</span><span class="sxs-lookup"><span data-stu-id="96774-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="96774-307">单击浏览器上的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="96774-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="96774-308">关闭您的浏览器中的**用户和用户组**选项卡，单击您的浏览器中的**公司战略总部**选项卡，然后关闭**网站权限**窗格。</span><span class="sxs-lookup"><span data-stu-id="96774-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="96774-309">下面介绍了权限配置结果：</span><span class="sxs-lookup"><span data-stu-id="96774-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="96774-310">**公司战略成员**SharePoint 组包含只有**C 套件**组 （其中包含只有首席执行官和首席财务官、 首席信息官用户帐户） 和**公司战略**组 （其中包含只有全局管理员用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="96774-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="96774-311">**公司战略负责人**SharePoint 组包含仅**IT staff**组 （其中包含仅 ITAdmin1 和 ITAdmin2 用户帐户）。</span><span class="sxs-lookup"><span data-stu-id="96774-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="96774-312">**公司战略者**SharePoint 组包含任何组或用户帐户。</span><span class="sxs-lookup"><span data-stu-id="96774-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="96774-313">成员不能修改网站级别的权限 （这只能由**公司策略所有者**组的成员）。</span><span class="sxs-lookup"><span data-stu-id="96774-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="96774-p110">其他用户帐户无法访问该站点或其资源或请求访问该网站。必须由全局管理员或**公司策略的所有者**组的成员对网站的其他权限。</span><span class="sxs-lookup"><span data-stu-id="96774-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="96774-316">接下来，配置为高度机密的标签公司战略工作组网站的文档文件夹。</span><span class="sxs-lookup"><span data-stu-id="96774-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="96774-317">在您的浏览器**公司总部策略**选项卡上，单击**文档**。</span><span class="sxs-lookup"><span data-stu-id="96774-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="96774-318">单击设置图标，然后单击**库设置**。</span><span class="sxs-lookup"><span data-stu-id="96774-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="96774-319">在**权限和管理**，请单击**应用于此库中的项目的标签**。</span><span class="sxs-lookup"><span data-stu-id="96774-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="96774-320">在**设置应用标签**，选择**高度机密**，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="96774-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="96774-321">当他们与高度机密的标签，其中包括公司战略网站，在组织外部共享联机 SharePoint 工作组网站上的文档，接下来，配置 DLP 策略阻止用户。</span><span class="sxs-lookup"><span data-stu-id="96774-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="96774-p111">如果需要请使用本地计算机上的浏览器，到 Office 365 门户拥有安全管理员或公司管理员角色的帐户登录。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="96774-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="96774-324">从**Microsoft Office 主页**选项卡上的在浏览器中，单击**安全&amp;法规遵从性**平铺。</span><span class="sxs-lookup"><span data-stu-id="96774-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="96774-325">对新**安全&amp;法规遵从性**在您的浏览器选项卡上，单击**数据丢失防范 > 策略**。</span><span class="sxs-lookup"><span data-stu-id="96774-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="96774-326">在**数据丢失防范**窗格中，单击**+ 创建策略**。</span><span class="sxs-lookup"><span data-stu-id="96774-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="96774-327">在**从模板开始创建自定义策略或**窗格中，单击**自定义**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="96774-328">**名称您的策略**中，在**名称**中键入**高度机密的标签 SharePoint Online 工作组站点**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="96774-329">在**选择位置**窗格中，**让我来选择特定的位置**，请单击，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="96774-330">在位置列表中，禁用**Exchange 电子邮件**帐户和**OneDrive 帐户**位置，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="96774-331">在**自定义类型您想要保护的敏感信息**窗格中，单击**编辑**。</span><span class="sxs-lookup"><span data-stu-id="96774-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="96774-332">在**选择要保护的内容的类型**窗格中，单击下拉列表框中，**添加**，然后单击**标签**。</span><span class="sxs-lookup"><span data-stu-id="96774-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="96774-333">**标签**的窗格中，单击**+ 添加**，选择**高度机密**标签，单击**添加**，然后单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="96774-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="96774-334">在**选择要保护的内容的类型**窗格中，单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="96774-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="96774-335">在**自定义类型您想要保护的敏感信息**窗格中，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="96774-336">在**您想要我们检测敏感信息办？**窗格中，单击**自定义提示和电子邮件**。</span><span class="sxs-lookup"><span data-stu-id="96774-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="96774-337">在**自定义策略的提示和电子邮件通知**窗格中，单击**自定义策略提示文本**。</span><span class="sxs-lookup"><span data-stu-id="96774-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="96774-338">在文本框中，键入或粘贴以下：</span><span class="sxs-lookup"><span data-stu-id="96774-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="96774-p112">若要与组织外部的用户共享，下载该文件，然后将其打开。单击文件然后保护文档，然后使用密码加密和再指定一个强密码。在另一个电子邮件或其他通讯手段发送密码。</span><span class="sxs-lookup"><span data-stu-id="96774-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="96774-342">单击"确定"。</span><span class="sxs-lookup"><span data-stu-id="96774-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="96774-343">在**您想要我们检测敏感信息办？**窗格中，选择**需要重写的理由**，然后再单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="96774-344">在**所需的策略或测试的事情，首先打开？**窗格中，单击**是，立即启用**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="96774-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="96774-345">在**查看设置**窗格上，单击**创建**，然后单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="96774-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="96774-346">接下来，按照[与 Office 365 管理中心激活 Azure RMS](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="96774-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="96774-347">接下来，使用一个指定了作用域的新策略和子标签保护和权限与以下步骤配置 Azure 信息保护：</span><span class="sxs-lookup"><span data-stu-id="96774-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="96774-p113">Office 365 门户拥有安全管理员或公司管理员角色的帐户登录。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="96774-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="96774-350">在浏览器的单独的选项卡，请转到 Azure 门户网站 ([https://portal.azure.com](https://portal.azure.com))。</span><span class="sxs-lookup"><span data-stu-id="96774-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="96774-351">如果这是首次配置 Azure 信息保护，请参见以下[说明](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)。</span><span class="sxs-lookup"><span data-stu-id="96774-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="96774-352">在列表窗格中，单击**更多服务**，键入**信息**，，然后单击**Azure 信息保护**。</span><span class="sxs-lookup"><span data-stu-id="96774-352">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="96774-353">**Azure 信息保护**刀片式服务器，，单击**范围策略 > 添加新策略 +**。</span><span class="sxs-lookup"><span data-stu-id="96774-353">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="96774-354">**策略名称**和**公司战略工作组网站中的文档的标签**在**描述**中键入**CompanyStrategy** 。</span><span class="sxs-lookup"><span data-stu-id="96774-354">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="96774-355">单击**选择哪些用户或组获取该策略 > 用户/用户组**，然后选择**C 套件**。</span><span class="sxs-lookup"><span data-stu-id="96774-355">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="96774-356">单击**选择 > 确定**。</span><span class="sxs-lookup"><span data-stu-id="96774-356">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="96774-357">**高度机密**的标签，请单击省略号 （...），然后单击**添加子标签**。</span><span class="sxs-lookup"><span data-stu-id="96774-357">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="96774-358">键入**名称**和说明中**说明**的标签的子标签的名称。</span><span class="sxs-lookup"><span data-stu-id="96774-358">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="96774-359">在**设置权限的文档和电子邮件包含此标签**，请单击**保护**。</span><span class="sxs-lookup"><span data-stu-id="96774-359">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="96774-360">在**保护**部分中，单击**Azure （云键）**。</span><span class="sxs-lookup"><span data-stu-id="96774-360">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="96774-361">在**保护**刀片式服务器下**保护设置**，, 单击**+ 添加权限**。</span><span class="sxs-lookup"><span data-stu-id="96774-361">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="96774-362">**添加权限**刀片式服务器，在**指定用户和组**，请单击**+ 浏览目录**。</span><span class="sxs-lookup"><span data-stu-id="96774-362">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="96774-363">在**AAD 的用户和组**窗格中，选择**C 套件**，，然后单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="96774-363">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="96774-364">在**选择权限从预设**清除**打印**、**复制和内容的提取**和**转发**复选框。</span><span class="sxs-lookup"><span data-stu-id="96774-364">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="96774-365">单击**确定**两次。</span><span class="sxs-lookup"><span data-stu-id="96774-365">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="96774-366">在**子标签**刀片式服务器，单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="96774-366">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="96774-367">关闭新的指定了作用域的策略刀片。</span><span class="sxs-lookup"><span data-stu-id="96774-367">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="96774-368">在**Azure 信息保护的指定了作用域策略**刀片式服务器，单击**发布**，然后单击**是**。</span><span class="sxs-lookup"><span data-stu-id="96774-368">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="96774-369">要保护与 Azure 的信息保护和此新的标签文档，则必须在测试机器上[安装 Azure 信息保护客户端](https://docs.microsoft.com/information-protection/rms-client/install-client-app)、 从 Office 365 管理门户安装 Office，**中的帐户然后登录从 Microsoft WordC 套件**组您的订购试用期。</span><span class="sxs-lookup"><span data-stu-id="96774-369">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **C-Suite** group of your trial subscription.</span></span>
  
<span data-ttu-id="96774-370">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="96774-370">Here is your resulting configuration.</span></span>
  
![适用于公司策略专用独立 SharePoint Online 团队网站的高度机密级保护。](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="96774-372">现在您可以在以下四个网站中创建文档并在您的订购试用期中测试使用不同用户帐户对它们的访问。</span><span class="sxs-lookup"><span data-stu-id="96774-372">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="96774-373">这是所有四个 SharePoint Online 团队站点的整体配置。</span><span class="sxs-lookup"><span data-stu-id="96774-373">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![安全 SharePoint Online 开发/测试环境中的所有四个团队网站。](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="96774-375">后续步骤</span><span class="sxs-lookup"><span data-stu-id="96774-375">Next step</span></span>

<span data-ttu-id="96774-376">用于生产环境中部署安全的 SharePoint Online 站点准备就绪后，请参阅[安全 SharePoint Online 网站和文件](secure-sharepoint-online-sites-and-files.md)的详细的信息和分步部署文章的链接。</span><span class="sxs-lookup"><span data-stu-id="96774-376">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="96774-377">See Also</span><span class="sxs-lookup"><span data-stu-id="96774-377">See Also</span></span>

[<span data-ttu-id="96774-378">SharePoint Online 网站和文件保护</span><span class="sxs-lookup"><span data-stu-id="96774-378">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="96774-379">安全解决方案</span><span class="sxs-lookup"><span data-stu-id="96774-379">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="96774-380">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="96774-380">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="96774-381">为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南</span><span class="sxs-lookup"><span data-stu-id="96774-381">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




