---
title: 为政治宣传活动开发/测试环境配置组和用户
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
localization_priority: Priority
ms.custom: ''
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: 摘要：通过用户和组创建适用于政治宣传活动开发/测试环境的 Office 365 和 Microsoft 企业移动性 + 安全性 (EMS) 试用订阅。
ms.openlocfilehash: 8556040a648937d4c1bc338292be121e5d290dd9
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2018
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a><span data-ttu-id="eeafc-103">为政治宣传活动开发/测试环境配置组和用户</span><span class="sxs-lookup"><span data-stu-id="eeafc-103">Configure groups and users for a political campaign dev/test environment</span></span>

 <span data-ttu-id="eeafc-104">**摘要**：通过用户和组创建适用于政治宣传活动开发/测试环境的 Office 365 和 Microsoft 企业移动性 + 安全性 (EMS) 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="eeafc-104">**Configure groups and users**. Create Office 365 and Enterprise Mobility + Security (EMS) trial subscriptions with users and groups for a political campaign dev/test environment.</span></span>
  
<span data-ttu-id="eeafc-105">使用本文中的说明创建一个开发/测试环境，其中包含[面向政治宣传活动、非盈利组织和其他敏捷组织的 Microsoft 安全指南](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)解决方案的简化用户帐户和组。</span><span class="sxs-lookup"><span data-stu-id="eeafc-105">Use the instructions in this article to create a dev/test environment that includes simplified user accounts and groups for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="eeafc-106">第 1 阶段：创建 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="eeafc-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="eeafc-107">在此阶段，将获取用于虚拟组织（代表政治宣传活动）的 Office 365 E5 和企业移动性 + 安全性 (EMS) E5 的试用订阅。</span><span class="sxs-lookup"><span data-stu-id="eeafc-107">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="eeafc-108">首先，按照 [Office 365 开发/测试环境](office-365-dev-test-environment.md)的**阶段 2** 中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="eeafc-108">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="eeafc-109">下一步，注册 EMS E5 试用订阅，并将其作为 Office 365 试用订阅添加到同一组织。</span><span class="sxs-lookup"><span data-stu-id="eeafc-109">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription, and then follow these steps:</span></span>
  
1. <span data-ttu-id="eeafc-p101">如有需要，请使用试用订阅的全局管理员帐户的凭据登录 Office 365 门户。如需帮助，请参阅[在哪里登录 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="eeafc-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="eeafc-112">单击“管理员”磁贴****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-112">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="eeafc-113">在浏览器的“Office 管理中心”标签页的左侧导航中，单击“帐单”>“购买服务”********。</span><span class="sxs-lookup"><span data-stu-id="eeafc-113">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="eeafc-p102">在“购买服务”**** 页上，找到“企业移动性 + 安全性 E5”**** 项。将鼠标指针悬停在此项之上，然后单击“开始免费试用”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="eeafc-116">在“确认订单”页上，单击“立即试用”********。</span><span class="sxs-lookup"><span data-stu-id="eeafc-116">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="eeafc-117">在“订单签收”页上，单击“继续”********。</span><span class="sxs-lookup"><span data-stu-id="eeafc-117">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="eeafc-118">接下来，为全局管理员帐户启用 EMS E5 许可证。</span><span class="sxs-lookup"><span data-stu-id="eeafc-118">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="eeafc-119">在浏览器的“Office 365 管理中心”**** 标签页的左侧导航中，单击“用户”>“活动用户”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-119">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="eeafc-120">单击全局管理员帐户，然后针对“产品许可证”单击“编辑”********。</span><span class="sxs-lookup"><span data-stu-id="eeafc-120">Click your global administrator account, and then click Edit for Product licenses.</span></span>
    
3. <span data-ttu-id="eeafc-121">在“产品许可证”**** 窗格，将“企业移动 +安全 E5”**** 的产品许可证设置为“打开”****，单击“保存”****，然后单击“关闭”**** 两次。</span><span class="sxs-lookup"><span data-stu-id="eeafc-121">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a><span data-ttu-id="eeafc-122">第 2 阶段：创建和配置 Azure Active Directory (AD) 组</span><span class="sxs-lookup"><span data-stu-id="eeafc-122">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="eeafc-123">在此阶段，为活动创建和配置 Azure AD 组。</span><span class="sxs-lookup"><span data-stu-id="eeafc-123">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="eeafc-124">首先，通过 Azure 门户为典型政治宣传活动创建一系列组。</span><span class="sxs-lookup"><span data-stu-id="eeafc-124">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="eeafc-125">在浏览器的单独标签页上，转到 Azure 门户 ([https://portal.azure.com](https://portal.azure.com))。如有需要，请使用 Office 365 E5 试用订阅的全局管理员帐户凭据登录。</span><span class="sxs-lookup"><span data-stu-id="eeafc-125">Create a separate tab in your browser, and then go to the Azure portal at https://portal.azure.com. If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="eeafc-126">在 Azure 门户中，单击“Azure Active Directory”>“用户和组”>“所有组”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-126">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="eeafc-127">对此列表中的每个组名称执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="eeafc-127">Do the following steps for each group name in this list:</span></span>
    
  - <span data-ttu-id="eeafc-128">高级和战略人员</span><span class="sxs-lookup"><span data-stu-id="eeafc-128">Senior and strategic staff</span></span>
    
  - <span data-ttu-id="eeafc-129">IT 人员</span><span class="sxs-lookup"><span data-stu-id="eeafc-129">IT staff</span></span>
    
  - <span data-ttu-id="eeafc-130">分析人员</span><span class="sxs-lookup"><span data-stu-id="eeafc-130">Analytics staff</span></span>
    
  - <span data-ttu-id="eeafc-131">常规核心人员</span><span class="sxs-lookup"><span data-stu-id="eeafc-131">Regular core staff</span></span>
    
  - <span data-ttu-id="eeafc-132">运营人员</span><span class="sxs-lookup"><span data-stu-id="eeafc-132">Operations staff</span></span>
    
  - <span data-ttu-id="eeafc-133">现场人员</span><span class="sxs-lookup"><span data-stu-id="eeafc-133">Field staff</span></span>
    
1. <span data-ttu-id="eeafc-134">在“所有组”边栏选项卡上，单击“+ 新建组”********。</span><span class="sxs-lookup"><span data-stu-id="eeafc-134">On the **All groups** blade, click **+ New group**.</span></span>
    
2. <span data-ttu-id="eeafc-135">在“名称”**** 中键入列表中的组名称。</span><span class="sxs-lookup"><span data-stu-id="eeafc-135">Type the group name from the list in **Name**.</span></span>
    
3. <span data-ttu-id="eeafc-136">在“成员资格”**** 中选择“动态用户”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-136">Select **Dynamic user** in **Membership**.</span></span>
    
4. <span data-ttu-id="eeafc-137">对“启用 Office 功能”单击“是”********。</span><span class="sxs-lookup"><span data-stu-id="eeafc-137">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="eeafc-138">单击“添加动态查询”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-138">Click **Add dynamic query**.</span></span>
    
6. <span data-ttu-id="eeafc-139">在“添加以下位置的用户”**** 中，选择“部门”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-139">In **Add users where**, select **department**.</span></span>
    
7. <span data-ttu-id="eeafc-140">在下一个字段中，选择“等于”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-140">In the next field, select **Equals**.</span></span>
    
8. <span data-ttu-id="eeafc-141">在下一个字段中，键入列表中的组名称。</span><span class="sxs-lookup"><span data-stu-id="eeafc-141">In the next field, type the group name from the list.</span></span>
    
9. <span data-ttu-id="eeafc-142">单击“添加查询”****，然后单击“创建”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-142">Click **Add query**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="eeafc-143">单击“用户和组 - 所有组”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-143">Click **Users and groups - All groups**.</span></span>
    
<span data-ttu-id="eeafc-144">接下来，配置组以便成员被自动分配 Office 365 E5 和 EMS E5 许可证。</span><span class="sxs-lookup"><span data-stu-id="eeafc-144">Next, you configure the groups so that members are automatically assigned Office 365 E5 and EMS E5 licenses.</span></span>
  
1. <span data-ttu-id="eeafc-145">在 Azure 门户中，单击“Azure Active Directory”>“许可证”>“所有产品”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-145">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="eeafc-146">在列表中，选择“企业移动性 + 安全性 E5”**** 和“Office 365 企业版 E5”****，然后单击“+ 分配”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-146">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and click **Assign**.</span></span>
    
3. <span data-ttu-id="eeafc-147">在“分配许可证”边栏选项卡中，单击“用户和组”********。</span><span class="sxs-lookup"><span data-stu-id="eeafc-147">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="eeafc-148">在组列表中，选择以下各项：</span><span class="sxs-lookup"><span data-stu-id="eeafc-148">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="eeafc-149">分析人员</span><span class="sxs-lookup"><span data-stu-id="eeafc-149">Analytics staff</span></span>
    
  - <span data-ttu-id="eeafc-150">现场人员</span><span class="sxs-lookup"><span data-stu-id="eeafc-150">Field staff</span></span>
    
  - <span data-ttu-id="eeafc-151">IT 人员</span><span class="sxs-lookup"><span data-stu-id="eeafc-151">IT staff</span></span>
    
  - <span data-ttu-id="eeafc-152">运营人员</span><span class="sxs-lookup"><span data-stu-id="eeafc-152">Operations staff</span></span>
    
  - <span data-ttu-id="eeafc-153">常规核心人员</span><span class="sxs-lookup"><span data-stu-id="eeafc-153">Regular core staff</span></span>
    
  - <span data-ttu-id="eeafc-154">高级和战略人员</span><span class="sxs-lookup"><span data-stu-id="eeafc-154">Senior and strategic staff</span></span>
    
5. <span data-ttu-id="eeafc-155">单击“选择”****，然后单击“分配”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-155">Click **Select**, and click **Assign**.</span></span>
    
6. <span data-ttu-id="eeafc-156">关闭浏览器中的 Azure 门户选项卡。</span><span class="sxs-lookup"><span data-stu-id="eeafc-156">Close the Azure portal tab in your browser.</span></span>
    
## <a name="phase-3-add-your-user-accounts"></a><span data-ttu-id="eeafc-157">第 3 阶段：添加用户帐户</span><span class="sxs-lookup"><span data-stu-id="eeafc-157">Phase 3: Add your user accounts</span></span>

<span data-ttu-id="eeafc-158">在这一阶段，为政治宣传活动添加示例用户帐户。</span><span class="sxs-lookup"><span data-stu-id="eeafc-158">In this phase, you add the example user accounts for your political campaign.</span></span>
  
<span data-ttu-id="eeafc-159">首先，[连接到 Azure Active Directory V2 PowerShell 模块](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="eeafc-159">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="eeafc-160">接下来，填写你的组织名称、位置和常用密码，然后从 PowerShell 命令提示符或集成的脚本环境 (ISE) 运行这些命令：</span><span class="sxs-lookup"><span data-stu-id="eeafc-160">Next, you fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE):</span></span>
  
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
> <span data-ttu-id="eeafc-p103">此处使用常用密码是为了自动化和方便配置开发/测试环境。但是对于生产订阅，不建议这样做。在登录这些新用户帐户时，系统将提示你更改密码。</span><span class="sxs-lookup"><span data-stu-id="eeafc-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions. As you sign in with each of these new user accounts, you will be prompted to change the password.</span></span> 
  
<span data-ttu-id="eeafc-164">使用这些步骤验证动态组成员资格和基于组的许可是否工作正常。</span><span class="sxs-lookup"><span data-stu-id="eeafc-164">Use these steps to verify that dynamic group membership and group-based licensing are working correctly.</span></span>
  
1. <span data-ttu-id="eeafc-165">在浏览器的“Microsoft Office 主页”标签页中，单击“管理员”磁贴********。</span><span class="sxs-lookup"><span data-stu-id="eeafc-165">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="eeafc-166">在浏览器的新“Office 管理中心”标签页中，单击“用户”********。</span><span class="sxs-lookup"><span data-stu-id="eeafc-166">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="eeafc-167">在用户列表中，单击“候选人”****。</span><span class="sxs-lookup"><span data-stu-id="eeafc-167">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="eeafc-168">在列出“候选人”**** 用户帐户属性的窗格中，确保：</span><span class="sxs-lookup"><span data-stu-id="eeafc-168">In the pane that lists the properties of the **Candidate** user account, verify that:</span></span>
    
  - <span data-ttu-id="eeafc-169">它是“高级和战略人员”**** 组（位于“组成员资格”****）的成员。</span><span class="sxs-lookup"><span data-stu-id="eeafc-169">It is a member of the **Senior and strategic staff** group (in **Group memberships**).</span></span>
    
  - <span data-ttu-id="eeafc-170">它已被分配“企业移动性 + 安全性 E5”**** 和“Office 365 企业 E5”**** 许可证（位于“产品许可证”**** 中）。</span><span class="sxs-lookup"><span data-stu-id="eeafc-170">In the pane that lists the properties of the CEO user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
5. <span data-ttu-id="eeafc-171">关闭“候选人”**** 用户帐户窗格。</span><span class="sxs-lookup"><span data-stu-id="eeafc-171">Close the **Candidate** user account pane.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="eeafc-172">记录这些值以供将来参考</span><span class="sxs-lookup"><span data-stu-id="eeafc-172">Record values for future reference</span></span>

<span data-ttu-id="eeafc-173">记录此开发/测试环境的这些值以用于 Office 365 和 EMS 试用订阅：</span><span class="sxs-lookup"><span data-stu-id="eeafc-173">Record these values for working with the Office 365 and EMS trial subscriptions for this dev/test environment:</span></span>
  
- <span data-ttu-id="eeafc-174">试用订阅组织名称：_______________________________________________</span><span class="sxs-lookup"><span data-stu-id="eeafc-174">Your trial subscription organization name: _______________________________________________ (from step 4 of Phase 2)</span></span> 
    
    <span data-ttu-id="eeafc-175">例如，对于 contoso.onmicrosoft.com 的试用订阅域名，组织名称是“contoso”。</span><span class="sxs-lookup"><span data-stu-id="eeafc-175">For example, for the trial subscription domain name of contoso.onmicrosoft.com, the organization name is "contoso".</span></span>
    
- <span data-ttu-id="eeafc-176">Office 365 全局管理员名称：____________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="eeafc-176">Office 365 global administrator name: ____________________________________.onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="eeafc-177">在安全位置记录此帐户的密码和其他用户帐户的常用初始密码。</span><span class="sxs-lookup"><span data-stu-id="eeafc-177">Record the password for this account and the common initial password for the other user accounts in a secure location.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="eeafc-178">后续步骤</span><span class="sxs-lookup"><span data-stu-id="eeafc-178">Next step</span></span>

<span data-ttu-id="eeafc-179">通过[在政治宣传活动开发/测试环境中创建团队网站](create-team-sites-in-a-political-campaign-dev-test-environment.md)，在此开发/测试环境中构建四种不同类型的 SharePoint Online 团队网站。</span><span class="sxs-lookup"><span data-stu-id="eeafc-179">Build the four different types of SharePoint Online team sites in this dev/test environment with [Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="eeafc-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eeafc-180">See Also</span></span>

[<span data-ttu-id="eeafc-181">Microsoft 针对政治宣传活动、非营利组织和其他敏捷性组织的安全指南</span><span class="sxs-lookup"><span data-stu-id="eeafc-181">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="eeafc-182">在政治宣传活动开发/测试环境中创建团队网站</span><span class="sxs-lookup"><span data-stu-id="eeafc-182">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="eeafc-183">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="eeafc-183">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="eeafc-184">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="eeafc-184">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




