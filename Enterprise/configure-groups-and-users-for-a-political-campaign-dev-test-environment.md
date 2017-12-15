---
title: "配置组和用户对于政治市场开发/测试环境"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: "摘要： 使用政治市场开发/测试环境的用户和组创建 Office 365 和企业移动 + 安全 (EMS) 的试用版本。"
ms.openlocfilehash: 7faf428fc2225d3f31297ba6bf83a10a7682009a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a><span data-ttu-id="c454c-103">配置组和用户对于政治市场开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="c454c-103">Configure groups and users for a political campaign dev/test environment</span></span>

 <span data-ttu-id="c454c-104">**摘要：**与政治市场开发/测试环境的用户和组创建 Office 365 和企业移动 + 安全 (EMS) 的试用版本。</span><span class="sxs-lookup"><span data-stu-id="c454c-104">**Summary:** Create Office 365 and Enterprise Mobility + Security (EMS) trial subscriptions with users and groups for a political campaign dev/test environment.</span></span>
  
<span data-ttu-id="c454c-105">使用本文中的说明创建包括简化的用户帐户和组的[Microsoft 安全指南为政治运动、 非营利性组织和其他的敏捷组织](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)解决方案的开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="c454c-105">Use the instructions in this article to create a dev/test environment that includes simplified user accounts and groups for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="c454c-106">第 1 阶段：创建 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="c454c-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="c454c-107">在此阶段中，您将获得 Office 365 E5 和企业移动性 + 表示政治运动的虚拟组织的安全 (EMS) E5 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="c454c-107">In this phase, you obtain trial subscriptions for Office 365 E5 and Enterprise Mobility + Security (EMS) E5 for a fictional organization that represents a political campaign.</span></span>
  
<span data-ttu-id="c454c-108">首先，按照**第二阶段**的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c454c-108">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="c454c-109">接下来，EMS E5 试用订阅注册，即可将其添加到作为 Office 365 的试用订阅的同一组织。</span><span class="sxs-lookup"><span data-stu-id="c454c-109">Next, sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="c454c-p101">如果需要请登录到您的订购试用期的全局管理员帐户的凭据对 Office 365 门户。有关帮助信息，请参阅[登录到 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="c454c-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c454c-112">单击**管理**拼贴。</span><span class="sxs-lookup"><span data-stu-id="c454c-112">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="c454c-113">在浏览器中，在左边的导航中， **Office 管理中心**选项卡单击**计费 > 购买服务**。</span><span class="sxs-lookup"><span data-stu-id="c454c-113">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="c454c-p102">**购买服务**页上找到**企业移动 + 安全 E5**项。将鼠标指针悬停在其上，单击**启动免费试用版**。</span><span class="sxs-lookup"><span data-stu-id="c454c-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="c454c-116">在**确认订单**页中，单击**立即尝试**。</span><span class="sxs-lookup"><span data-stu-id="c454c-116">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="c454c-117">在**订单收据**页上，单击**继续**。</span><span class="sxs-lookup"><span data-stu-id="c454c-117">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="c454c-118">下一步，使您的全局管理员帐户的 EMS E5 许可证。</span><span class="sxs-lookup"><span data-stu-id="c454c-118">Next, enable the EMS E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="c454c-119">在浏览器中，在左边的导航中， **Office 365 管理中心**选项卡单击**用户 > 活动用户**。</span><span class="sxs-lookup"><span data-stu-id="c454c-119">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="c454c-120">单击您的全局管理员帐户，然后单击**编辑****产品**许可证。</span><span class="sxs-lookup"><span data-stu-id="c454c-120">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="c454c-121">**产品许可证**的窗格中，在打开产品许可证**的企业移动性 + 安全 E5**到**上**，单击**保存**，然后两次单击**关闭**。</span><span class="sxs-lookup"><span data-stu-id="c454c-121">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a><span data-ttu-id="c454c-122">第 2 阶段： 创建和配置 Azure 活动目录 (AD) 组</span><span class="sxs-lookup"><span data-stu-id="c454c-122">Phase 2: Create and configure your Azure Active Directory (AD) groups</span></span>

<span data-ttu-id="c454c-123">在此阶段中，您创建和市场配置的 Azure AD 组。</span><span class="sxs-lookup"><span data-stu-id="c454c-123">In this phase, you create and configure the Azure AD groups for your campaign.</span></span>
  
<span data-ttu-id="c454c-124">首先，Azure 门户创建一组典型政治市场活动组。</span><span class="sxs-lookup"><span data-stu-id="c454c-124">First, create a set of groups for a typical political campaign with the Azure portal.</span></span>
  
1. <span data-ttu-id="c454c-125">您的浏览器在单独的选项卡，请转到 Azure 门户网站位于[https://portal.azure.com](https://portal.azure.com)。如果需要请为您的 Office 365 E5 试用订阅登录的全局管理员帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="c454c-125">On a separate tab in your browser, go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="c454c-126">在 Azure 的门户，单击**Azure Active Directory > 用户和组 > 所有组**。</span><span class="sxs-lookup"><span data-stu-id="c454c-126">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="c454c-127">请执行以下步骤在此列表中每个组的名称：</span><span class="sxs-lookup"><span data-stu-id="c454c-127">Do the following steps for each group name in this list:</span></span>
    
  - <span data-ttu-id="c454c-128">高级和战略性工作人员</span><span class="sxs-lookup"><span data-stu-id="c454c-128">Senior and strategic staff</span></span>
    
  - <span data-ttu-id="c454c-129">IT 人员</span><span class="sxs-lookup"><span data-stu-id="c454c-129">IT staff</span></span>
    
  - <span data-ttu-id="c454c-130">分析人员</span><span class="sxs-lookup"><span data-stu-id="c454c-130">Analytics staff</span></span>
    
  - <span data-ttu-id="c454c-131">常规的核心人员</span><span class="sxs-lookup"><span data-stu-id="c454c-131">Regular core staff</span></span>
    
  - <span data-ttu-id="c454c-132">操作人员</span><span class="sxs-lookup"><span data-stu-id="c454c-132">Operations staff</span></span>
    
  - <span data-ttu-id="c454c-133">现场员工</span><span class="sxs-lookup"><span data-stu-id="c454c-133">Field staff</span></span>
    
1. <span data-ttu-id="c454c-134">**所有组**刀片式服务器，请单击**+ 新组**。</span><span class="sxs-lookup"><span data-stu-id="c454c-134">On the **All groups** blade, click **+ New group**.</span></span>
    
2. <span data-ttu-id="c454c-135">在**名称**中键入列表中的组名称。</span><span class="sxs-lookup"><span data-stu-id="c454c-135">Type the group name from the list in **Name**.</span></span>
    
3. <span data-ttu-id="c454c-136">选择**动态的用户****成员身份**。</span><span class="sxs-lookup"><span data-stu-id="c454c-136">Select **Dynamic user** in **Membership**.</span></span>
    
4. <span data-ttu-id="c454c-137">**启用 Office 功能**，请单击**是**。</span><span class="sxs-lookup"><span data-stu-id="c454c-137">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="c454c-138">单击**添加动态查询**。</span><span class="sxs-lookup"><span data-stu-id="c454c-138">Click **Add dynamic query**.</span></span>
    
6. <span data-ttu-id="c454c-139">在**中添加用户，**，选择**部门**。</span><span class="sxs-lookup"><span data-stu-id="c454c-139">In **Add users where**, select **department**.</span></span>
    
7. <span data-ttu-id="c454c-140">在下一个字段中，选择**等于**。</span><span class="sxs-lookup"><span data-stu-id="c454c-140">In the next field, select **Equals**.</span></span>
    
8. <span data-ttu-id="c454c-141">在下一个字段中，键入列表中的组名称。</span><span class="sxs-lookup"><span data-stu-id="c454c-141">In the next field, type the group name from the list.</span></span>
    
9. <span data-ttu-id="c454c-142">单击**添加查询**，然后单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="c454c-142">Click **Add query**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="c454c-143">单击**用户和组的所有组**。</span><span class="sxs-lookup"><span data-stu-id="c454c-143">Click **Users and groups - All groups**.</span></span>
    
<span data-ttu-id="c454c-144">下一步，以便成员会自动分配 Office 365 E5 和 EMS E5 许可证配置组。</span><span class="sxs-lookup"><span data-stu-id="c454c-144">Next, you configure the groups so that members are automatically assigned Office 365 E5 and EMS E5 licenses.</span></span>
  
1. <span data-ttu-id="c454c-145">在 Azure 的门户，单击**Azure Active Directory > 许可证 > 所有产品**。</span><span class="sxs-lookup"><span data-stu-id="c454c-145">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="c454c-146">在列表中，选择**企业移动 + 安全 E5**和**Office 365 企业 E5**，然后单击**+ 分配**。</span><span class="sxs-lookup"><span data-stu-id="c454c-146">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **+ Assign**.</span></span>
    
3. <span data-ttu-id="c454c-147">在**分派许可证**刀片式服务器，单击**用户和组**。</span><span class="sxs-lookup"><span data-stu-id="c454c-147">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="c454c-148">在组列表中，选择下列设置：</span><span class="sxs-lookup"><span data-stu-id="c454c-148">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="c454c-149">分析人员</span><span class="sxs-lookup"><span data-stu-id="c454c-149">Analytics staff</span></span>
    
  - <span data-ttu-id="c454c-150">现场员工</span><span class="sxs-lookup"><span data-stu-id="c454c-150">Field staff</span></span>
    
  - <span data-ttu-id="c454c-151">IT 人员</span><span class="sxs-lookup"><span data-stu-id="c454c-151">IT staff</span></span>
    
  - <span data-ttu-id="c454c-152">操作人员</span><span class="sxs-lookup"><span data-stu-id="c454c-152">Operations staff</span></span>
    
  - <span data-ttu-id="c454c-153">常规的核心人员</span><span class="sxs-lookup"><span data-stu-id="c454c-153">Regular core staff</span></span>
    
  - <span data-ttu-id="c454c-154">高级和战略性工作人员</span><span class="sxs-lookup"><span data-stu-id="c454c-154">Senior and strategic staff</span></span>
    
5. <span data-ttu-id="c454c-155">单击**选择**，然后单击**分配**。</span><span class="sxs-lookup"><span data-stu-id="c454c-155">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="c454c-156">关闭您的浏览器中的 Azure 门户选项卡。</span><span class="sxs-lookup"><span data-stu-id="c454c-156">Close the Azure portal tab in your browser.</span></span>
    
## <a name="phase-3-add-your-user-accounts"></a><span data-ttu-id="c454c-157">阶段 3： 添加用户帐户</span><span class="sxs-lookup"><span data-stu-id="c454c-157">Phase 3: Add your user accounts</span></span>

<span data-ttu-id="c454c-158">在此阶段中，您添加示例用户帐户为您的政治运动。</span><span class="sxs-lookup"><span data-stu-id="c454c-158">In this phase, you add the example user accounts for your political campaign.</span></span>
  
<span data-ttu-id="c454c-159">首先，您[使用 Azure 活动目录 V2 PowerShell 模块连接](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="c454c-159">First, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="c454c-160">接下来，您填写您的组织名称、 您所在的位置和常见的密码，并从 PowerShell 命令提示符或脚本集成环境 (ISE) 运行这些命令：</span><span class="sxs-lookup"><span data-stu-id="c454c-160">Next, you fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE):</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> <span data-ttu-id="c454c-p103">使用常见是配置的密码的自动化和易于开发/测试环境。不推荐用于生产订阅。随着每个新用户帐户登录，系统会提示您更改密码。</span><span class="sxs-lookup"><span data-stu-id="c454c-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions. As you sign in with each of these new user accounts, you will be prompted to change the password.</span></span> 
  
<span data-ttu-id="c454c-164">使用下列步骤验证动态组成员关系和基于组的授权工作正常。</span><span class="sxs-lookup"><span data-stu-id="c454c-164">Use these steps to verify that dynamic group membership and group-based licensing are working correctly.</span></span>
  
1. <span data-ttu-id="c454c-165">从浏览器的**Microsoft Office 主页**选项卡上，单击**管理**拼贴。</span><span class="sxs-lookup"><span data-stu-id="c454c-165">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="c454c-166">您的浏览器的新**办公室管理中心**标签，单击**用户**。</span><span class="sxs-lookup"><span data-stu-id="c454c-166">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="c454c-167">在用户列表中，单击**候选**。</span><span class="sxs-lookup"><span data-stu-id="c454c-167">In the list of users, click **Candidate**.</span></span>
    
4. <span data-ttu-id="c454c-168">在列出**候选**用户帐户的属性窗格中，请验证：</span><span class="sxs-lookup"><span data-stu-id="c454c-168">In the pane that lists the properties of the **Candidate** user account, verify that:</span></span>
    
  - <span data-ttu-id="c454c-169">它是**高级和战略性工作人员**（在**组成员身份**） 组的成员。</span><span class="sxs-lookup"><span data-stu-id="c454c-169">It is a member of the **Senior and strategic staff** group (in **Group memberships**).</span></span>
    
  - <span data-ttu-id="c454c-170">它已分配**的企业移动性 + 安全 E5**和**Office 365 企业 E5**许可证 （在**产品许可证**）。</span><span class="sxs-lookup"><span data-stu-id="c454c-170">It has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
5. <span data-ttu-id="c454c-171">关闭**候选**用户帐户窗格。</span><span class="sxs-lookup"><span data-stu-id="c454c-171">Close the **Candidate** user account pane.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="c454c-172">记录值以供将来参考</span><span class="sxs-lookup"><span data-stu-id="c454c-172">Record values for future reference</span></span>

<span data-ttu-id="c454c-173">记录这些值使用 Office 365 和 EMS 试用版本，此开发/测试环境：</span><span class="sxs-lookup"><span data-stu-id="c454c-173">Record these values for working with the Office 365 and EMS trial subscriptions for this dev/test environment:</span></span>
  
- <span data-ttu-id="c454c-174">您的订购试用期的组织名称: ___</span><span class="sxs-lookup"><span data-stu-id="c454c-174">Your trial subscription organization name: _______________________________________________</span></span> 
    
    <span data-ttu-id="c454c-175">例如，contoso.onmicrosoft.com 的试用订阅域名，单位名称为"contoso"。</span><span class="sxs-lookup"><span data-stu-id="c454c-175">For example, for the trial subscription domain name of contoso.onmicrosoft.com, the organization name is "contoso".</span></span>
    
- <span data-ttu-id="c454c-176">Office 365 全局管理员名称： ___.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="c454c-176">The Office 365 global administrator name: ____________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="c454c-177">此帐户的密码和其他用户帐户的通用初始密码记录在一个安全的位置。</span><span class="sxs-lookup"><span data-stu-id="c454c-177">Record the password for this account and the common initial password for the other user accounts in a secure location.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="c454c-178">后续步骤</span><span class="sxs-lookup"><span data-stu-id="c454c-178">Next step</span></span>

<span data-ttu-id="c454c-179">构建四个不同类型的 SharePoint Online 工作组网站[创建工作组网站的政治运动开发/测试环境中](create-team-sites-in-a-political-campaign-dev-test-environment.md)具有此开发/测试环境中。</span><span class="sxs-lookup"><span data-stu-id="c454c-179">Build the four different types of SharePoint Online team sites in this dev/test environment with [Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c454c-180">See Also</span><span class="sxs-lookup"><span data-stu-id="c454c-180">See Also</span></span>

[<span data-ttu-id="c454c-181">为政治运动、 非营利性组织和其他敏捷组织的 Microsoft 安全指南</span><span class="sxs-lookup"><span data-stu-id="c454c-181">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="c454c-182">在政治运动的开发/测试环境中创建工作组网站</span><span class="sxs-lookup"><span data-stu-id="c454c-182">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="c454c-183">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="c454c-183">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c454c-184">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="c454c-184">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




