---
title: "通过 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴聚合客户报告数据"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: "摘要：使用适用于 Office 365 的 Windows PowerShell 检索关于所有客户租赁的报告并将数据聚合到一个位置。"
ms.openlocfilehash: 825f0519b97522f664c34462c441d190cac4bb8e
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="d51ec-103">通过 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴聚合客户报告数据</span><span class="sxs-lookup"><span data-stu-id="d51ec-103">Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="d51ec-104">**摘要：**使用适用于 Office 365 的 Windows PowerShell 检索所有客户租赁上的报表，并将数据聚合到一个位置中。</span><span class="sxs-lookup"><span data-stu-id="d51ec-104">**Summary:** Use Windows PowerShell for Office 365 to retrieve reports on all customer tenancies and aggregate the data into a single location.</span></span>
  
<span data-ttu-id="d51ec-p101">默认情况下，适用于 Office 365 的 Windows PowerShell 不具备针对多个客户租赁的报告数据的内置聚合功能。但是，您可以使用适用于 Office 365 的 Windows PowerShell 的此示例脚本循环访问您的所有客户租赁，检索每个客户的单个报告，然后将报告数据聚合到一个位置。结果是所有客户租户将聚合在一个报告中。</span><span class="sxs-lookup"><span data-stu-id="d51ec-p101">By default, Windows PowerShell for Office 365 does not have a built-in aggregation of reporting data from multiple customer tenancies. However, you can use this sample Windows PowerShell for Office 365 script to iterate through all your customer tenancies to retrieve a single report for each of your customers and then aggregate the reporting data into a single location. The result is that you'll have a single report for all your customer tenants.</span></span> 
  
<span data-ttu-id="d51ec-p102">委派访问权限 (DAP) 合作伙伴是联合和云解决方案提供商 (CSP) 合作伙伴。他们通常是面向其他公司的网络或电信提供商。他们将 Office 365 订阅捆绑到为其客户提供的服务产品中。 当他们销售 Office 365 订阅时，会自动获得对客户租赁的"代表以下方管理"(AOBO) 权限，这样他们便可以管理客户租赁并生成相应报告。</span><span class="sxs-lookup"><span data-stu-id="d51ec-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="d51ec-112">准备工作</span><span class="sxs-lookup"><span data-stu-id="d51ec-112">Before you begin</span></span>

<span data-ttu-id="d51ec-113">若要使用此脚本，请替换这些变量中的特定值：</span><span class="sxs-lookup"><span data-stu-id="d51ec-113">To use this script, substitute your particular values in for these variables:</span></span>
  
- <span data-ttu-id="d51ec-p103">**$UserName** - 这是您的合作伙伴管理员用户名。这些凭据将用于连接到您的所有客户租赁。</span><span class="sxs-lookup"><span data-stu-id="d51ec-p103">**$UserName** - This is your partner administrator user name. These credentials will be used to connect to all your customer tenancies.</span></span>
    
- <span data-ttu-id="d51ec-116">**$OutputFile** - 这是报告数据将聚合到的逗号分隔值文件。</span><span class="sxs-lookup"><span data-stu-id="d51ec-116">**$OutputFile** - This is the comma-separated value file that reporting data will be aggregated to.</span></span>
    
- <span data-ttu-id="d51ec-117">**$ErrorFile** - 这是错误的文本日志文件。</span><span class="sxs-lookup"><span data-stu-id="d51ec-117">**$ErrorFile** - This is the text log file for errors.</span></span>
    
- <span data-ttu-id="d51ec-p104">**$ScriptBlock** - 此示例脚本使用 **Get-MailboxActivityReport** 和参数（例如开始和结束日期），以便您可以通过某种方式开始。如果您需要其他报告，用所需的报告名称和必要的参数来代替 **Get-MailboxActivityReport** 。</span><span class="sxs-lookup"><span data-stu-id="d51ec-p104">**$ScriptBlock** - This sample script uses **Get-MailboxActivityReport** and parameters (such as start and end dates) so you have a way to get started. If you want other reports, substitute the report name that you want and necessary parameters for **Get-MailboxActivityReport**.</span></span>
    
- <span data-ttu-id="d51ec-120">按照[通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)中的步骤，打开到 Exchange Online 的远程 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="d51ec-120">Open a remote Windows PowerShell session to Exchange Online by using the steps in [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a><span data-ttu-id="d51ec-121">使用 Windows PowerShell 将客户租户报告聚合到一个位置</span><span class="sxs-lookup"><span data-stu-id="d51ec-121">Use Windows PowerShell to aggregate customer tenant reports to a single location</span></span>

1. <span data-ttu-id="d51ec-122">将此脚本复制并粘贴到记事本。</span><span class="sxs-lookup"><span data-stu-id="d51ec-122">Copy and paste this script into Notepad.</span></span>
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\\ReportOutput.csv"

$ErrorFile = ".\\Errors.txt"

# This is the report to run and all the necessary parameters.

$ScriptBlock = {Get-MailboxActivityReport -ReportType Daily -StartDate 03/18/2015 -EndDate 03/18/2015}

$LinesToSkip = 0

# This is the prompt for the password of the partner admin user name.

$Cred = get-credential -Credential $UserName

# Establish a Windows PowerShell session with Office 365.

Connect-MsolService -Credential $Cred

# Get all the contracts for the signed-in partner.  
# Contracts define the AOBO/DAP relationship between the partner and the customers.

$Contracts = Get-MsolPartnerContract -All

Write-Host "Found $($Contracts.Count) customers for this Partner."

# For each of the contracts (customers), run the specified report and output the information.

foreach ($c in $contracts) { 

    # Get the initial domain for the customer.

    $InitialDomain = Get-MsolDomain -TenantId $c.TenantId | Where {$_.IsInitial -eq $true}

    # Construct the URL with the DelegatedOrg parameter.
    
    $DelegatedOrgURL = "https://ps.outlook.com/powershell-liveid?DelegatedOrg=" + $InitialDomain.Name
        
    Write-Host "Running report for $($InitialDomain.Name)"

    # Invoke-Command establishes a Windows PowerShell session based on the URL,
    # runs the command, and closes the Windows PowerShell session.
    
    $ReportInfo = Invoke-Command -ConnectionUri $DelegatedOrgURL -Credential $Cred -Authentication Basic -ConfigurationName Microsoft.Exchange -AllowRedirection -ScriptBlock $ScriptBlock -HideComputerName

    # If Invoke-Command returned information (that is, it's not NULL), format and output the information.
    
    If ($ReportInfo) {

        Write-Host "Writing report information for $($InitialDomain.Name) to $OutputFile"  -foregroundcolor green

        # Convert the report data to CSV format.
        # For the first time, don't skip any lines, so include the header.
        # For all other times, skip the first line (so don't rewrite the header).
        
        $OutputInfo = $ReportInfo |  ConvertTo-CSV -NoTypeInformation | Select -Skip $LinesToSkip

        Out-File $OutputFile -InputObject $OutputInfo -Append

        $LinesToSkip = 1

    } else {

        # If Invoke-Command didn't return and report data, log an error.
        
        Write-Host "No report information for $($InitialDomain.Name)." -foregroundcolor yellow
           
        Out-File $ErrorFile  -InputObject @("No report information for $($InitialDomain.Name).") -Append
    }

}

  ```

2. <span data-ttu-id="d51ec-p105">在易于您查找的位置将脚本另存为 GetMailboxActivityReport.ps1。例如，将文件保存在 C:\\O365 Scripts 中。</span><span class="sxs-lookup"><span data-stu-id="d51ec-p105">Save the script as GetMailboxActivityReport.ps1 in a location that's easy for you to find. For the example, the file is saved in C:\\O365 Scripts.</span></span> 
    
3. <span data-ttu-id="d51ec-125">按照下面的语法，在远程 Windows PowerShell 中运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="d51ec-125">Run the script in remote Windows PowerShell by following this syntax.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

<span data-ttu-id="d51ec-126">此示例脚本将聚合的报告放在 ReportOutput.csv 文件中。</span><span class="sxs-lookup"><span data-stu-id="d51ec-126">This sample script places the aggregated report in the ReportOutput.csv file.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d51ec-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d51ec-127">See also</span></span>

#### 

[<span data-ttu-id="d51ec-128">适于合作伙伴的帮助</span><span class="sxs-lookup"><span data-stu-id="d51ec-128">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[<span data-ttu-id="d51ec-129">Office 365 报告 Web 服务</span><span class="sxs-lookup"><span data-stu-id="d51ec-129">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="d51ec-130">Exchange Online 中的报告 cmdlet</span><span class="sxs-lookup"><span data-stu-id="d51ec-130">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)

