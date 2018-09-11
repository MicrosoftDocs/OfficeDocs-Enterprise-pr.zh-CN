---
title: Office 365 开发/测试环境中的 GDPR 发现、保护和报告
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: ''
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: 演示 Office 365 中的 GDPR 功能。
ms.openlocfilehash: e58ddc36bf85d791451e2f8097ad65bef4c463e3
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915087"
---
# <a name="gdpr-discovery-protection-and-reporting-in-the-office-365-devtest-environment"></a><span data-ttu-id="af11f-103">Office 365 开发/测试环境中的 GDPR 发现、保护和报告</span><span class="sxs-lookup"><span data-stu-id="af11f-103">GDPR discovery, protection, and reporting in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="af11f-104">**摘要**：演示 Office 365 中的 GDPR 功能。</span><span class="sxs-lookup"><span data-stu-id="af11f-104">**Summary:** Demonstrate GDPR capabilities in Office 365.</span></span> 
  
<span data-ttu-id="af11f-105">本文介绍如何在 Office 365 开发/测试环境中配置和演示一般数据保护条例 (GDPR) 的个人身份信息 (PII) 发现、保护和报告。</span><span class="sxs-lookup"><span data-stu-id="af11f-105">This article describes how you configure and demonstrate personally identifiable information (PII) discovery, protection, and reporting for the General Data Protection Regulation (GDPR) in an Office 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-and-configure-your-trial-office-365-subscription"></a><span data-ttu-id="af11f-106">第 1 阶段：创建和配置试用版 Office 365 订阅</span><span class="sxs-lookup"><span data-stu-id="af11f-106">Phase 1: Create and configure your trial Office 365 subscription</span></span>

<span data-ttu-id="af11f-107">首先，按照 [Office 365 开发/测试环境的第 2 阶段](office-365-dev-test-environment.md#phase-2-create-an-office-365-trial-subscription)一文中的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="af11f-107">First, follow the steps in [Phase 2 of the Office 365 dev/test environment](office-365-dev-test-environment.md#phase-2-create-an-office-365-trial-subscription) article.</span></span>

<span data-ttu-id="af11f-108">接下来，使用这些步骤来配置电子数据展示管理器：</span><span class="sxs-lookup"><span data-stu-id="af11f-108">Next, use these steps to configure the eDiscovery manager:</span></span>

1. <span data-ttu-id="af11f-109">使用全局管理员帐户登录到 Office 365 试用版租户。</span><span class="sxs-lookup"><span data-stu-id="af11f-109">Sign in to your Office 365 trial tenant with your global administrator account.</span></span>
2. <span data-ttu-id="af11f-110">在 Office 365 主页上，单击“安全与合规性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-110">From the Office 365 home page, click **Security & Compliance**.</span></span>
3. <span data-ttu-id="af11f-111">在新的“安全与合规性”选项卡中，单击“权限”\*\*\*\* > “电子数据展示管理器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-111">From the new Security & Compliance tab, click **Permissions** > **eDiscovery Manager**.</span></span>
4. <span data-ttu-id="af11f-112">单击电子数据展示管理器的“编辑”\*\*\*\*，然后单击“选择电子数据展示管理器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-112">Click **Edit** for eDiscovery Manager, and then click **Choose eDiscovery Manager**.</span></span>
5. <span data-ttu-id="af11f-113">单击“+ 添加”\*\*\*\*，搜索全局管理员帐户名称，并添加全局管理员帐户作为电子数据展示管理器。</span><span class="sxs-lookup"><span data-stu-id="af11f-113">Click **+ Add**, search for your global administrator account name and add your global administrator account as an eDiscovery Manager.</span></span>
6. <span data-ttu-id="af11f-114">单击“完成”\*\*\*\* > “保存”\*\*\*\* > “关闭”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-114">Click **Done** > **Save** > **Close**.</span></span>
  
## <a name="phase-2-add-personally-identifiable-information-to-your-tenant"></a><span data-ttu-id="af11f-115">第 2 阶段：将个人身份信息添加到租户</span><span class="sxs-lookup"><span data-stu-id="af11f-115">Phase 2: Add personally identifiable information to your tenant</span></span>

<span data-ttu-id="af11f-116">在此阶段，将使用 PII 为一组示例国际银行帐号 (IBAN) 创建一个文档，并将其存储在 Office 365 开发/测试环境中的 SharePoint Online 网站上。</span><span class="sxs-lookup"><span data-stu-id="af11f-116">In this phase, you create a document with PII for a set of example International Banking Account Numbers (IBANs) and store it on a SharePoint Online site in your Office 365 dev/test environment.</span></span>

1. <span data-ttu-id="af11f-117">在本地计算机上打开 Microsoft Word。</span><span class="sxs-lookup"><span data-stu-id="af11f-117">On your local computer, open Microsoft Word.</span></span>
2. <span data-ttu-id="af11f-118">将下表粘贴到 Word 文件中，并在本地计算机上将其另存为“IBANs.docx”。</span><span class="sxs-lookup"><span data-stu-id="af11f-118">Paste the following table in the Word file and save it as ‘IBANs.docx’ on your local computer.</span></span>
    
    <span data-ttu-id="af11f-119">帐号</span><span class="sxs-lookup"><span data-stu-id="af11f-119">Number</span></span>  |<span data-ttu-id="af11f-120">国家/地区</span><span class="sxs-lookup"><span data-stu-id="af11f-120">Country</span></span>  |<span data-ttu-id="af11f-121">代码</span><span class="sxs-lookup"><span data-stu-id="af11f-121">Code</span></span> |<span data-ttu-id="af11f-122">IBAN</span><span class="sxs-lookup"><span data-stu-id="af11f-122">IBAN</span></span>  |
    |---------|---------|---------|---------|
    |<span data-ttu-id="af11f-123">1</span><span class="sxs-lookup"><span data-stu-id="af11f-123">1</span></span>     |  <span data-ttu-id="af11f-124">奥地利 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-124">Austria SEPA</span></span>      | <span data-ttu-id="af11f-125">AT</span><span class="sxs-lookup"><span data-stu-id="af11f-125">AT</span></span>            |<span data-ttu-id="af11f-126">AT611904300234573201</span><span class="sxs-lookup"><span data-stu-id="af11f-126">AT611904300234573201</span></span>       |
    |<span data-ttu-id="af11f-127">2</span><span class="sxs-lookup"><span data-stu-id="af11f-127">2</span></span>     |  <span data-ttu-id="af11f-128">保加利亚 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-128">Bulgaria SEPA</span></span>       |<span data-ttu-id="af11f-129">BG</span><span class="sxs-lookup"><span data-stu-id="af11f-129">BG</span></span>    |<span data-ttu-id="af11f-130">BG80BNBG96611020345678</span><span class="sxs-lookup"><span data-stu-id="af11f-130">BG80BNBG96611020345678</span></span>      |
    |<span data-ttu-id="af11f-131">3</span><span class="sxs-lookup"><span data-stu-id="af11f-131">3</span></span>     |  <span data-ttu-id="af11f-132">丹麦 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-132">Denmark SEPA</span></span>      |   <span data-ttu-id="af11f-133">DK</span><span class="sxs-lookup"><span data-stu-id="af11f-133">DK</span></span>      |<span data-ttu-id="af11f-134">DK5000400440116243</span><span class="sxs-lookup"><span data-stu-id="af11f-134">DK5000400440116243</span></span>      |
    |<span data-ttu-id="af11f-135">4</span><span class="sxs-lookup"><span data-stu-id="af11f-135">4</span></span>     |  <span data-ttu-id="af11f-136">芬兰 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-136">Finland SEPA</span></span>      |   <span data-ttu-id="af11f-137">FI</span><span class="sxs-lookup"><span data-stu-id="af11f-137">FI</span></span>      |<span data-ttu-id="af11f-138">FI2112345600000785</span><span class="sxs-lookup"><span data-stu-id="af11f-138">FI2112345600000785</span></span>         |
    |<span data-ttu-id="af11f-139">5</span><span class="sxs-lookup"><span data-stu-id="af11f-139">5</span></span>     |  <span data-ttu-id="af11f-140">法国 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-140">France SEPA</span></span>       |   <span data-ttu-id="af11f-141">FR</span><span class="sxs-lookup"><span data-stu-id="af11f-141">FR</span></span>      |<span data-ttu-id="af11f-142">FR1420041010050500013M02606</span><span class="sxs-lookup"><span data-stu-id="af11f-142">FR1420041010050500013M02606</span></span>         |
    |<span data-ttu-id="af11f-143">6</span><span class="sxs-lookup"><span data-stu-id="af11f-143">6</span></span>     |  <span data-ttu-id="af11f-144">德国 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-144">Germany SEPA</span></span>      |   <span data-ttu-id="af11f-145">DE</span><span class="sxs-lookup"><span data-stu-id="af11f-145">DE</span></span>      |<span data-ttu-id="af11f-146">DE89370400440532013000</span><span class="sxs-lookup"><span data-stu-id="af11f-146">DE89370400440532013000</span></span>         |
    |<span data-ttu-id="af11f-147">7</span><span class="sxs-lookup"><span data-stu-id="af11f-147">7</span></span>     |  <span data-ttu-id="af11f-148">希腊 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-148">Greece SEPA</span></span>       |   <span data-ttu-id="af11f-149">GR</span><span class="sxs-lookup"><span data-stu-id="af11f-149">GR</span></span>      |<span data-ttu-id="af11f-150">GR1601101250000000012300695</span><span class="sxs-lookup"><span data-stu-id="af11f-150">GR1601101250000000012300695</span></span>         |
    |<span data-ttu-id="af11f-151">8</span><span class="sxs-lookup"><span data-stu-id="af11f-151">8</span></span>     |  <span data-ttu-id="af11f-152">意大利 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-152">Italy SEPA</span></span>       |    <span data-ttu-id="af11f-153">IT</span><span class="sxs-lookup"><span data-stu-id="af11f-153">IT</span></span>     |<span data-ttu-id="af11f-154">GR1601101250000000012300695</span><span class="sxs-lookup"><span data-stu-id="af11f-154">GR1601101250000000012300695</span></span>         |
    |<span data-ttu-id="af11f-155">9</span><span class="sxs-lookup"><span data-stu-id="af11f-155">9</span></span>     |  <span data-ttu-id="af11f-156">荷兰 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-156">Netherlands SEPA</span></span>      |   <span data-ttu-id="af11f-157">NL</span><span class="sxs-lookup"><span data-stu-id="af11f-157">NL</span></span>      |    <span data-ttu-id="af11f-158">NL91ABNA0417164300</span><span class="sxs-lookup"><span data-stu-id="af11f-158">NL91ABNA0417164300</span></span>     |
    |<span data-ttu-id="af11f-159">10</span><span class="sxs-lookup"><span data-stu-id="af11f-159">10</span></span>     | <span data-ttu-id="af11f-160">波兰 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-160">Poland SEPA</span></span>       |  <span data-ttu-id="af11f-161">PL</span><span class="sxs-lookup"><span data-stu-id="af11f-161">PL</span></span>       | <span data-ttu-id="af11f-162">PL27114020040000300201355387</span><span class="sxs-lookup"><span data-stu-id="af11f-162">PL27114020040000300201355387</span></span>        |

<span data-ttu-id="af11f-163">请注意：此示例数据集源自公开信息，仅用于测试目的。</span><span class="sxs-lookup"><span data-stu-id="af11f-163">Note:- This sample data set is derived from publicly available information and is intended to be used for test purposes only.</span></span>

3. <span data-ttu-id="af11f-164">在浏览器新选项卡中，键入以下内容：**https://**\<YourTenantName\>**.sharepoint.com**</span><span class="sxs-lookup"><span data-stu-id="af11f-164">In a new tab of your browser, type:  **https://**\<YourTenantName\>**.sharepoint.com**</span></span>
4. <span data-ttu-id="af11f-p101">单击“文档”\*\*\*\* 打开此网站的文档库。如果系统提示你体验新的列表，请单击“下一步”\*\*\*\* 直至其完成。</span><span class="sxs-lookup"><span data-stu-id="af11f-p101">Click **Documents** to open the document library for this site. If you’re prompted for a new list experience tour, click **Next** until it’s finished.</span></span>
5.  <span data-ttu-id="af11f-167">单击“上传”\*\*\*\* > “文件”\*\*\*\* 并选择在步骤 2 中创建的 IBANs.docx。</span><span class="sxs-lookup"><span data-stu-id="af11f-167">Click **Upload** > **Files** and select the IBANs.docx you created in step 2.</span></span>

  
## <a name="phase-3-demonstrate-data-discovery"></a><span data-ttu-id="af11f-168">第 3 阶段：演示数据发现</span><span class="sxs-lookup"><span data-stu-id="af11f-168">Phase 3: Demonstrate data discovery</span></span>

<span data-ttu-id="af11f-169">在此阶段，将演示根据包含 IBAN 的文档内容进行搜索，以查找在第 2 阶段创建和存储的文档。</span><span class="sxs-lookup"><span data-stu-id="af11f-169">In this phase, you demonstrate search to find the document created and stored in Phase 2, based on its content containing IBANs.</span></span>

1. <span data-ttu-id="af11f-170">在“安全与合规性”选项卡中，单击“主页”\*\*\*\*，然后单击“搜索和调查”\*\*\*\* > “内容搜索”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-170">From the Security & Compliance tab, click **Home**, and then click **Search & investigation** > **Content search**.</span></span>
2. <span data-ttu-id="af11f-171">单击“+”\*\*\*\* 以创建新的搜索项。</span><span class="sxs-lookup"><span data-stu-id="af11f-171">Create a new search item by clicking on **+**.</span></span>
3. <span data-ttu-id="af11f-172">在新窗口中，提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="af11f-172">In a new window, provide the following information:</span></span>  
    <span data-ttu-id="af11f-p102">a. 名称：IBAN 搜索</span><span class="sxs-lookup"><span data-stu-id="af11f-p102">a. Name: IBAN Search</span></span>  
    <span data-ttu-id="af11f-p103">b. 想要我们查找什么?：**选择要搜索的特定网站**（单击“+”\*\*\*\*），然后输入网站 URL：**https://**\<YourTenantName\>**.sharepoint.com/**</span><span class="sxs-lookup"><span data-stu-id="af11f-p103">b. Where do you want us to look?: **Choose specific sites to search** (click **+**), and then enter the site's URL: **https://**\<YourTenantName\>**.sharepoint.com/**</span></span>  
    <span data-ttu-id="af11f-p104">c. 单击“添加”\*\*\*\*，然后单击“确认”\*\*\*\*。如果看到一条警告，请单击“确认”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-p104">c. Click **Add**, and then click **OK**. If you see a Warning, click **OK**.</span></span>  
    <span data-ttu-id="af11f-p105">d. 单击“新搜索”\*\*\*\* 窗口中的“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-p105">d. Click **Next** on a **New search** window.</span></span>  
    <span data-ttu-id="af11f-p106">e. 对于**想要我们查找什么?**：**SensitiveType:“International Banking Account Number (IBAN)”**，然后单击“搜索”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-p106">e. For **What do you want us to look for?**: **SensitiveType:"International Banking Account Number (IBAN)"**, and then click **Search**.</span></span>

4. <span data-ttu-id="af11f-184">确保在“IBAN 搜索”\*\*\*\* 结果中至少列出一项。</span><span class="sxs-lookup"><span data-stu-id="af11f-184">Make sure you see at least one item listed in the **IBAN Search** results.</span></span>


## <a name="phase-4-create-a-custom-sensitive-information-type-via-powershell"></a><span data-ttu-id="af11f-185">第 4 阶段：通过 PowerShell 创建自定义敏感信息类型</span><span class="sxs-lookup"><span data-stu-id="af11f-185">Phase 4: Create a custom sensitive information type via PowerShell</span></span>

<span data-ttu-id="af11f-p107">在此阶段，将使用 Microsoft PowerShell 为虚构的 Contoso 公司创建一个自定义敏感信息类型。Contoso 使用 Contoso 客户编号 (CCN) 来识别其客户数据库中的每个客户。CCN 包含以下结构：</span><span class="sxs-lookup"><span data-stu-id="af11f-p107">In this phase, you create a custom sensitive information type for the fictional Contoso Corporation using Microsoft PowerShell.  Contoso uses a Contoso Customer Number (CCN) to identify each customer in their customer database. A CCN consists of the following structure:</span></span>
- <span data-ttu-id="af11f-189">表示创建记录的年份的两位数字。</span><span class="sxs-lookup"><span data-stu-id="af11f-189">Two digits to represent the year that the record was created.</span></span>
    - <span data-ttu-id="af11f-190">Contoso 成立于 2002 年，因此，最早的可能值为 02。</span><span class="sxs-lookup"><span data-stu-id="af11f-190">Contoso was founded in 2002; therefore, the earliest possible value would be 02.</span></span> 
- <span data-ttu-id="af11f-191">表示创建记录的合作伙伴机构的三位数字。</span><span class="sxs-lookup"><span data-stu-id="af11f-191">Three digits to represent the partner agency that created the record.</span></span>
    - <span data-ttu-id="af11f-192">可能的机构值的范围是 000 到 999。</span><span class="sxs-lookup"><span data-stu-id="af11f-192">Possible agency values range from 000 to 999.</span></span> 
- <span data-ttu-id="af11f-193">表示业务线的字母字符。</span><span class="sxs-lookup"><span data-stu-id="af11f-193">An alphabetic character to represent the line of business.</span></span>
    - <span data-ttu-id="af11f-194">可能的值为 a 到 z，且应区分大小写。</span><span class="sxs-lookup"><span data-stu-id="af11f-194">Possible values are a-z and should be case insensitive.</span></span>
- <span data-ttu-id="af11f-195">四位数的序列号。</span><span class="sxs-lookup"><span data-stu-id="af11f-195">A four-digit serial number.</span></span> 
    - <span data-ttu-id="af11f-196">可能的序列号值的范围是 0000 到 9999。</span><span class="sxs-lookup"><span data-stu-id="af11f-196">Possible serial number values range from 0000 to 9999.</span></span>   

<span data-ttu-id="af11f-p108">在内部通信、外部通信、文档和其他表单中，Contoso 通常使用 CCN 指代客户。Contoso 需要自定义敏感项类型来检测 Office 365 内容中使用的 CCN，以便对这种个人身份信息形式的使用应用保护。</span><span class="sxs-lookup"><span data-stu-id="af11f-p108">Contoso always refers to customers by using a CCN in internal correspondence, external correspondence, documents, and other forms. Contoso needs a custom sensitive item type to detect the use of CCNs in Office 365 content so that they may apply protection to the use of this form of personal identifiable information.</span></span>

1. <span data-ttu-id="af11f-199">借助[使用多重身份验证连接到 Office 365 安全与合规中心 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) 中的说明，使用全局管理员帐户的 UPN 连接到安全与合规中心。</span><span class="sxs-lookup"><span data-stu-id="af11f-199">Use the instructions in [Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) and connect to the Security & Compliance Center with UPN of your global administrator account.</span></span>
2. <span data-ttu-id="af11f-200">运行以下 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="af11f-200">Run the following PowerShell commands.</span></span>

     ```
    #Create & start search for sample data
    $searchName = "Sample Customer Information Search"
    $searchQuery = "15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118"
    New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery
    Start-ComplianceSearch -Identity $searchName#Create & start search for sample data
    $searchName = "Sample Customer Information Search"
    $searchQuery = "15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118"
    New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery
    Start-ComplianceSearch -Identity $searchName
    ```
3. <span data-ttu-id="af11f-201">运行以下 PowerShell 命令，并将生成的 GUID 按其所列顺序复制到计算机上打开的记事本实例中。</span><span class="sxs-lookup"><span data-stu-id="af11f-201">Run the following PowerShell commands and copy the generated GUIDs to an open instance of Notepad on your computer in the order in which they are listed.</span></span>
    ```
    #Generate three unique GUIDs
    Write-Host "GUID1 = "([guid]::NewGuid().Guid)
    Write-Host "GUID2 = "([guid]::NewGuid().Guid)
    Write-Host "GUID3 = "([guid]::NewGuid().Guid)
    ```
4. <span data-ttu-id="af11f-202">在本地计算机上，打开记事本的另一个实例，并粘贴以下内容：</span><span class="sxs-lookup"><span data-stu-id="af11f-202">On your local computer, open another instance of Notepad and paste in the following content:</span></span>

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce"> 
    <RulePack id="GUID1">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id="GUID2" />
    <Details defaultLangCode="en"> 
    <LocalizedDetails langcode="en"> 
    <PublisherName>Contoso Ltd.</PublisherName> 
    <Name>Contoso Rule Package</Name> 
    <Description>Defines Contoso's custom set of classification rules</Description>
    </LocalizedDetails>
    </Details>
    </RulePack>
    <Rules>
    <!-- Contoso Customer Number (CCN) -->
    <Entity id="GUID3" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
    <IdMatch idRef="Regex_contoso_ccn" />
    <Match idRef="Keyword_contoso_ccn" />
    <Match idRef="Regex_eu_date" />
    </Pattern>
    </Entity>
    <Regex id="Regex_contoso_ccn">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</Regex>
    <Keyword id="Keyword_contoso_ccn">
    <Group matchStyle="word">
    <Term caseSensitive="false">customer number</Term>
    <Term caseSensitive="false">customer no</Term>
    <Term caseSensitive="false">customer #</Term>
    <Term caseSensitive="false">customer#</Term>
    <Term caseSensitive="false">Contoso customer</Term>
    </Group>
    </Keyword>
    <Regex id="Regex_eu_date"> (0?[1-9]|[12][0-9]|3[0-1])[\/-](0?[1-9]|1[0-2]|j\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)? |feb(ruary|ruari|rero|braio|ruar|br)?|f\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\x00e4rz|maart|apr(ile|il)?|abr(il)?|avril |may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)? |nov(ember|iembre|embre|embro)?|dec(ember)?|dic(iembre|embre)?|dez(ember|embro)?|d\x00e9c(embre)?)[ \/-](19|20)?[0-9]{2}</Regex>
    <LocalizedStrings>
    <Resource idRef="GUID3">
    <Name default="true" langcode="en-us">Contoso Customer Number (CCN)</Name>
    <Description default="true" langcode="en-us">Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date</Description>
    </Resource>
    </LocalizedStrings>
    </Rules>
    </RulePackage>
    ```
5. <span data-ttu-id="af11f-203">将步骤 4 的 XML 文本中的 GUID1、GUID2 和 GUID3 的值替换为步骤 3 中的值，然后将该内容保存在本地计算机上，并命名为 ContosoCCN.xml。</span><span class="sxs-lookup"><span data-stu-id="af11f-203">Replace the values of GUID1, GUID2, and GUID3 in the XML text of step 4 with their values from step 3, and then save the contents on your local computer with the name ContosoCCN.xml.</span></span>
6. <span data-ttu-id="af11f-204">填写 ContosoCCN.xml 文件的路径并运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="af11f-204">Fill in the path to your ContosoCCN.xml file and run the following commands.</span></span>
    ```
    #Create new Sensitive Information Type
    $path="<path to the ContosoCCN.xml file, such as C:\Scripts\ContosoCCN.xml>"
    New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path $path -Encoding Byte -ReadCount 0)
    ```
7. <span data-ttu-id="af11f-p109">在“安全与合规性”选项卡中，单击“分类”\*\*\*\* > “敏感信息类型”\*\*\*\*。应该能看到列表中的 Contoso 客户编号 (CCN)。</span><span class="sxs-lookup"><span data-stu-id="af11f-p109">From the Security & Compliance tab, click **Classifications** > **Sensitive information types**. You should see the Contoso Customer Number (CCN) in the list.</span></span>

## <a name="phase-5-demonstrate-data-protection"></a><span data-ttu-id="af11f-207">第 5 阶段：演示数据保护</span><span class="sxs-lookup"><span data-stu-id="af11f-207">Phase 5: Demonstrate data protection</span></span>

<span data-ttu-id="af11f-p110">对 Office 365 中的个人信息的保护包括使用数据丢失防护 (DLP) 功能。借助 Office 365 安全与合规中心中的 DLP 策略，可以自动保护 Office 365 内的敏感信息。</span><span class="sxs-lookup"><span data-stu-id="af11f-p110">Protection of personal information in Office 365 includes using data loss prevention (DLP) capabilities.  With DLP policies in the Office 365 Security & Compliance Center, you can automatically protect sensitive information across Office 365.</span></span>

<span data-ttu-id="af11f-p111">有多种方式可以应用保护。引导和提高在你的环境中存储欧盟常驻数据的位置的意识以及允许员工处理该数据的方式，这表示使用 Office 365 DLP 进行信息保护的一个级别。</span><span class="sxs-lookup"><span data-stu-id="af11f-p111">There are multiple ways you can apply the protection. Educating and raising awareness to where EU resident data is stored in your environment and how your employees are permitted to handle it represents one level of information protection using Office 365 DLP.</span></span>

<span data-ttu-id="af11f-212">在此阶段，将创建一个新的 DLP 策略，并演示它是如何应用于第 2 阶段中存储在 SharePoint Online 中的 IBANs.docx 文件，以及何时尝试发送包含 IBAN 的电子邮件。</span><span class="sxs-lookup"><span data-stu-id="af11f-212">In this phase, you create a new DLP policy and demonstrate how it gets applied to the IBANs.docx file you stored in SharePoint Online in Phase 2 and when you attempt to send an email containing IBANs.</span></span>

1. <span data-ttu-id="af11f-213">在浏览器的“安全与合规性”选项卡中，单击“主页”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-213">From the Security & Compliance tab of your browser, click **Home**.</span></span>
2. <span data-ttu-id="af11f-214">单击“数据丢失防护”\*\*\*\* > “策略”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-214">Click **Data loss prevention** > **Policy**.</span></span>
3. <span data-ttu-id="af11f-215">单击“+ 创建策略”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-215">Click **+ Create a policy**.</span></span>
4. <span data-ttu-id="af11f-216">在“从模板开始或创建自定义策略”\*\*\*\* 中，单击“自定义”\*\*\*\* > “自定义策略”\*\*\*\* > “下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-216">In **Start with a template or create a custom policy**, click **Custom** > **Custom policy** > **Next**.</span></span>
5. <span data-ttu-id="af11f-p112">在“为策略命名”\*\*\*\* 中，提供以下详细信息，然后单击“下一步”\*\*\*\*：a. 名称：“欧盟公民 PII 策略”\*\*\*\* b.说明：“保护欧洲公民的个人身份信息”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="af11f-p112">In **Name your policy**, provide the following details and then click **Next**:  a. Name: **EU Citizen PII Policy** b. Description: **Protect the personally identifiable information of European citizens**</span></span>
6. <span data-ttu-id="af11f-p113">在“选择位置”\*\*\*\* 中，选择“Office 365 中的所有位置”\*\*\*\*。这将包含 Exchange 电子邮件中的内容以及 OneDrive 和 SharePoint 文档。然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-p113">In **Choose locations**, select **All locations in Office 365**. This will include content in Exchange email and OneDrive and SharePoint documents. And then click **Next**.</span></span>
7. <span data-ttu-id="af11f-223">在“自定义想要保护的内容类型”\*\*\*\* 中，单击“查找包含以下内容的信息:”\*\*\*\*，然后单击“编辑”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-223">In **Customize the type of content you want to protect**, click **Find content that contains:** and then click **Edit**.</span></span>
8. <span data-ttu-id="af11f-224">在“选择要保护的内容类型”\*\*\*\* 中，单击“添加”\*\*\*\* > “敏感信息类型”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-224">In **Choose the types of content to protect**, click **Add** > **Sensitive info types**.</span></span>
9. <span data-ttu-id="af11f-225">在“敏感信息类型”\*\*\*\* 中，单击“+ 添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-225">In **Sensitive info types**, click **+ Add**.</span></span>
10. <span data-ttu-id="af11f-226">在“敏感信息类型”\*\*\*\* 中，搜索“IBAN”\*\*\*\*，选中“国际银行帐号(IBAN)”\*\*\*\* 复选框，然后单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-226">In **Sensitive info types**, search for **IBAN**, select the check box for **International Banking Account Number (IBAN)**, and then click **Add**.</span></span>
11. <span data-ttu-id="af11f-227">确认已添加“国际银行帐号(IBAN)”\*\*\*\* 敏感信息类型，然后单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-227">Confirm that the **International Banking Account Number (IBAN)** sensitive information type was added, and then click **Done**.</span></span>
12. <span data-ttu-id="af11f-228">在“内容包含”\*\*\*\* 中，确认已添加敏感信息类型，然后单击“保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-228">In **Content contains**, confirm that the sensitive information types were added and then click **Save**.</span></span>
13. <span data-ttu-id="af11f-229">在“自定义想要保护的内容类型”\*\*\*\* 中，确认“查找包含以下内容的信息:”\*\*\*\* 包含“国际银行帐号(IBAN)”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-229">In **Customize the type of content you want to protect**, confirm  **Find content that contains:** contains the **International Banking Account Number (IBAN)**, and then click **Next**.</span></span>
14. <span data-ttu-id="af11f-230">在“当共享的内容包含以下值时检测:”\*\*\*\* 中，将值从“10”\*\*\*\* 更改为“1”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-230">In **Detect when content that's being shared contains:**, change the value from **10** to **1**, and then click **Next**.</span></span>
15. <span data-ttu-id="af11f-231">在“要启用策略还是先进行测试?”\*\*\*\* 中，选择以下设置，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-231">In **Do you want to turn on the policy or test things out first?**, choose the following settings, and then click **Next**.</span></span>  
    <span data-ttu-id="af11f-p114">a. 选择“我想先进行测试”\*\*\*\* 选项</span><span class="sxs-lookup"><span data-stu-id="af11f-p114">a. Select the option for **I'd like to test it out first**</span></span>  
    <span data-ttu-id="af11f-p115">b. 选中“在测试模式下显示策略提示”\*\*\*\* 复选框</span><span class="sxs-lookup"><span data-stu-id="af11f-p115">b. Select the check box for **Show policy tips while in test mode**</span></span> 
16. <span data-ttu-id="af11f-p116">在“查看设置”\*\*\*\* 中，在查看设置后单击“创建”\*\*\*\*。注意：创建新的 DLP 策略后，需要一段时间才能生效。</span><span class="sxs-lookup"><span data-stu-id="af11f-p116">In **Review your settings**, click **Create** after reviewing the settings. NOTE: After you create a new DLP policy, it will take a while for it to take effect.</span></span>
17. <span data-ttu-id="af11f-238">在本地计算机上打开浏览器的专用实例。</span><span class="sxs-lookup"><span data-stu-id="af11f-238">On your local computer, open a private instance of your browser.</span></span>
18. <span data-ttu-id="af11f-239">在地址栏中，键入 **https://**\<YourTenantName\>**.sharepoint.com**，然后使用全局管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="af11f-239">In the address bar, type **https://**\<YourTenantName\>**.sharepoint.com** and sign in using your global administrator account.</span></span>
19. <span data-ttu-id="af11f-240">单击“文档”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-240">Click **Documents**.</span></span>
20. <span data-ttu-id="af11f-p117">单击名为“IBANs.docx”的文件。可以看到“Policy tip for IBANs.docx”。IBANs.docx 文件与外部收件人进行了共享，这违反了 DLP 策略。</span><span class="sxs-lookup"><span data-stu-id="af11f-p117">Click the file named ‘IBANs.docx’. You should see ‘Policy tip for IBANs.docx’.  The IBANs.docx file was shared with external recipients, which violates the DLP policy.</span></span> 
21. <span data-ttu-id="af11f-244">在地址栏中，键入：**https://outlook.office365.com**</span><span class="sxs-lookup"><span data-stu-id="af11f-244">In the address bar, type: **https://outlook.office365.com**</span></span>
22. <span data-ttu-id="af11f-245">单击“新建”\*\*\*\* - “电子邮件”\*\*\*\*，并提供以下内容：</span><span class="sxs-lookup"><span data-stu-id="af11f-245">Click **New** - **Email message** and provide the following:</span></span>  
    - <span data-ttu-id="af11f-246">**收件人**：\<个人电子邮件地址\></span><span class="sxs-lookup"><span data-stu-id="af11f-246">**To:** \<a personal email address\></span></span>  
    - <span data-ttu-id="af11f-247">**主题**：GDPR 测试</span><span class="sxs-lookup"><span data-stu-id="af11f-247">**Subject:** GDPR Test</span></span>  
    - <span data-ttu-id="af11f-248">**正文**：复制下面显示的表中的值。</span><span class="sxs-lookup"><span data-stu-id="af11f-248">**Body:** Copy in the table of values shown below.</span></span>
  
        |<span data-ttu-id="af11f-249">帐号</span><span class="sxs-lookup"><span data-stu-id="af11f-249">Number</span></span>  |<span data-ttu-id="af11f-250">国家/地区</span><span class="sxs-lookup"><span data-stu-id="af11f-250">Country</span></span>  |<span data-ttu-id="af11f-251">代码</span><span class="sxs-lookup"><span data-stu-id="af11f-251">Code</span></span> |<span data-ttu-id="af11f-252">IBAN</span><span class="sxs-lookup"><span data-stu-id="af11f-252">IBAN</span></span>  |
        |---------|---------|---------|---------|
        |<span data-ttu-id="af11f-253">1</span><span class="sxs-lookup"><span data-stu-id="af11f-253">::1</span></span>     |  <span data-ttu-id="af11f-254">奥地利 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-254">Austria SEPA</span></span>      | <span data-ttu-id="af11f-255">AT</span><span class="sxs-lookup"><span data-stu-id="af11f-255">AT</span></span>            |<span data-ttu-id="af11f-256">AT611904300234573201</span><span class="sxs-lookup"><span data-stu-id="af11f-256">AT611904300234573201</span></span>       |
        |<span data-ttu-id="af11f-257">2</span><span class="sxs-lookup"><span data-stu-id="af11f-257">2</span></span>     |  <span data-ttu-id="af11f-258">保加利亚 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-258">Bulgaria SEPA</span></span>       |<span data-ttu-id="af11f-259">BG</span><span class="sxs-lookup"><span data-stu-id="af11f-259">BG</span></span>    |<span data-ttu-id="af11f-260">BG80BNBG96611020345678</span><span class="sxs-lookup"><span data-stu-id="af11f-260">BG80BNBG96611020345678</span></span>      |
        |<span data-ttu-id="af11f-261">3</span><span class="sxs-lookup"><span data-stu-id="af11f-261">3</span></span>     |  <span data-ttu-id="af11f-262">丹麦 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-262">Denmark SEPA</span></span>      |   <span data-ttu-id="af11f-263">DK</span><span class="sxs-lookup"><span data-stu-id="af11f-263">DK</span></span>      |<span data-ttu-id="af11f-264">DK5000400440116243</span><span class="sxs-lookup"><span data-stu-id="af11f-264">DK5000400440116243</span></span>      |
        |<span data-ttu-id="af11f-265">4</span><span class="sxs-lookup"><span data-stu-id="af11f-265">4</span></span>     |  <span data-ttu-id="af11f-266">芬兰 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-266">Finland SEPA</span></span>      |   <span data-ttu-id="af11f-267">FI</span><span class="sxs-lookup"><span data-stu-id="af11f-267">FI</span></span>      |<span data-ttu-id="af11f-268">FI2112345600000785</span><span class="sxs-lookup"><span data-stu-id="af11f-268">FI2112345600000785</span></span>         |
        |<span data-ttu-id="af11f-269">5</span><span class="sxs-lookup"><span data-stu-id="af11f-269">5</span></span>     |  <span data-ttu-id="af11f-270">法国 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-270">France SEPA</span></span>       |   <span data-ttu-id="af11f-271">FR</span><span class="sxs-lookup"><span data-stu-id="af11f-271">FR</span></span>      |<span data-ttu-id="af11f-272">FR1420041010050500013M02606</span><span class="sxs-lookup"><span data-stu-id="af11f-272">FR1420041010050500013M02606</span></span>         |
        |<span data-ttu-id="af11f-273">6</span><span class="sxs-lookup"><span data-stu-id="af11f-273">6</span></span>     |  <span data-ttu-id="af11f-274">德国 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-274">Germany SEPA</span></span>      |   <span data-ttu-id="af11f-275">DE</span><span class="sxs-lookup"><span data-stu-id="af11f-275">DE</span></span>      |<span data-ttu-id="af11f-276">DE89370400440532013000</span><span class="sxs-lookup"><span data-stu-id="af11f-276">DE89370400440532013000</span></span>         |
        |<span data-ttu-id="af11f-277">7</span><span class="sxs-lookup"><span data-stu-id="af11f-277">7</span></span>     |  <span data-ttu-id="af11f-278">希腊 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-278">Greece SEPA</span></span>       |   <span data-ttu-id="af11f-279">GR</span><span class="sxs-lookup"><span data-stu-id="af11f-279">GR</span></span>      |<span data-ttu-id="af11f-280">GR1601101250000000012300695</span><span class="sxs-lookup"><span data-stu-id="af11f-280">GR1601101250000000012300695</span></span>         |
        |<span data-ttu-id="af11f-281">8</span><span class="sxs-lookup"><span data-stu-id="af11f-281">8</span></span>     |  <span data-ttu-id="af11f-282">意大利 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-282">Italy SEPA</span></span>       |    <span data-ttu-id="af11f-283">IT</span><span class="sxs-lookup"><span data-stu-id="af11f-283">IT</span></span>     |<span data-ttu-id="af11f-284">GR1601101250000000012300695</span><span class="sxs-lookup"><span data-stu-id="af11f-284">GR1601101250000000012300695</span></span>         |
        |<span data-ttu-id="af11f-285">9</span><span class="sxs-lookup"><span data-stu-id="af11f-285">9</span></span>     |  <span data-ttu-id="af11f-286">荷兰 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-286">Netherlands SEPA</span></span>      |   <span data-ttu-id="af11f-287">NL</span><span class="sxs-lookup"><span data-stu-id="af11f-287">NL</span></span>      |   <span data-ttu-id="af11f-288">NL91ABNA0417164300</span><span class="sxs-lookup"><span data-stu-id="af11f-288">NL91ABNA0417164300</span></span>      |
        |<span data-ttu-id="af11f-289">10</span><span class="sxs-lookup"><span data-stu-id="af11f-289">10</span></span>     | <span data-ttu-id="af11f-290">波兰 SEPA</span><span class="sxs-lookup"><span data-stu-id="af11f-290">Poland SEPA</span></span>       |  <span data-ttu-id="af11f-291">PL</span><span class="sxs-lookup"><span data-stu-id="af11f-291">PL</span></span>       | <span data-ttu-id="af11f-292">PL27114020040000300201355387</span><span class="sxs-lookup"><span data-stu-id="af11f-292">PL27114020040000300201355387</span></span>        |

<span data-ttu-id="af11f-293">请注意：此示例数据集源自公开信息，仅用于测试目的。</span><span class="sxs-lookup"><span data-stu-id="af11f-293">Note:- This sample data set is derived from publicly available information and is intended to be used for test purposes only.</span></span>

23. <span data-ttu-id="af11f-294">可以看到，DLP 策略识别了包含 IBAN 的电子邮件的正文，并在邮件窗口顶部提供了策略提示。</span><span class="sxs-lookup"><span data-stu-id="af11f-294">You will see that the DLP policy recognized that body of the email contains IBANs and provides you with the policy tip at the top of the message window.</span></span>
24. <span data-ttu-id="af11f-295">关闭浏览器专用实例。</span><span class="sxs-lookup"><span data-stu-id="af11f-295">Close the private instance of your browser.</span></span>


## <a name="phase-6-demonstrate-reporting"></a><span data-ttu-id="af11f-296">第 6 阶段：演示报告</span><span class="sxs-lookup"><span data-stu-id="af11f-296">Phase 6: Demonstrate reporting</span></span>
 
<span data-ttu-id="af11f-297">在此阶段，将基于在第 5 阶段配置的 DLP 策略来演示 Office 365 报告。</span><span class="sxs-lookup"><span data-stu-id="af11f-297">In this phase, you demonstrate Office 365 reporting based on the DLP policy configured in Phase 5.</span></span>

   1. <span data-ttu-id="af11f-298">在浏览器的“安全与合规性”选项卡中，单击“主页”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-298">From the Security & Compliance tab of your browser, click **Home**.</span></span>
   2. <span data-ttu-id="af11f-299">单击“报告”\*\*\*\* > “仪表板”\*\*\*\* > “DLP 策略匹配项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="af11f-299">Click **Reports** > **Dashboard** > **DLP policy matches**.</span></span>
   3. <span data-ttu-id="af11f-p118">DLP 策略可帮助识别和保护组织的敏感信息。例如，在报告中可以看到，策略标识了存储在 SharePoint Online 中的包含 IBAN 的文档。</span><span class="sxs-lookup"><span data-stu-id="af11f-p118">Your DLP policy helps identify and protect organization's sensitive information. For example, in the report you will see that the policy identified the document that contains IBANs stored in SharePoint Online.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="af11f-302">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af11f-302">See Also</span></span>

[<span data-ttu-id="af11f-303">针对 GDPR 的 Office 365 信息保护</span><span class="sxs-lookup"><span data-stu-id="af11f-303">Office 365 Information Protection for GDPR</span></span>](office-365-information-protection-for-gdpr.md)

[<span data-ttu-id="af11f-304">GDPR for Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="af11f-304">GDPR for Microsoft 365</span></span>](https://docs.microsoft.com/microsoft-365/compliance/gdpr?toc=/microsoft-365/enterprise/toc.json)
