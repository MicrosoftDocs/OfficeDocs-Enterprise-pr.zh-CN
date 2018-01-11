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
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a>通过 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴聚合客户报告数据

 **摘要：**使用适用于 Office 365 的 Windows PowerShell 检索所有客户租赁上的报表，并将数据聚合到一个位置中。
  
默认情况下，适用于 Office 365 的 Windows PowerShell 不具备针对多个客户租赁的报告数据的内置聚合功能。但是，您可以使用适用于 Office 365 的 Windows PowerShell 的此示例脚本循环访问您的所有客户租赁，检索每个客户的单个报告，然后将报告数据聚合到一个位置。结果是所有客户租户将聚合在一个报告中。 
  
委派访问权限 (DAP) 合作伙伴是联合和云解决方案提供商 (CSP) 合作伙伴。他们通常是面向其他公司的网络或电信提供商。他们将 Office 365 订阅捆绑到为其客户提供的服务产品中。 当他们销售 Office 365 订阅时，会自动获得对客户租赁的"代表以下方管理"(AOBO) 权限，这样他们便可以管理客户租赁并生成相应报告。
## <a name="before-you-begin"></a>准备工作

若要使用此脚本，请替换这些变量中的特定值：
  
- **$UserName** - 这是您的合作伙伴管理员用户名。这些凭据将用于连接到您的所有客户租赁。
    
- **$OutputFile** - 这是报告数据将聚合到的逗号分隔值文件。
    
- **$ErrorFile** - 这是错误的文本日志文件。
    
- **$ScriptBlock** - 此示例脚本使用 **Get-MailboxActivityReport** 和参数（例如开始和结束日期），以便您可以通过某种方式开始。如果您需要其他报告，用所需的报告名称和必要的参数来代替 **Get-MailboxActivityReport** 。
    
- 按照[通过远程 Windows PowerShell 为委派访问权限 (DAP) 合作伙伴连接到 Exchange Online 租户](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)中的步骤，打开到 Exchange Online 的远程 Windows PowerShell 会话。
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a>使用 Windows PowerShell 将客户租户报告聚合到一个位置

1. 将此脚本复制并粘贴到记事本。
    
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

2. 在易于您查找的位置将脚本另存为 GetMailboxActivityReport.ps1。例如，将文件保存在 C:\\O365 Scripts 中。 
    
3. 按照下面的语法，在远程 Windows PowerShell 中运行该脚本。
    
  ```
  &amp; "C:\\O365 Scripts\\GetMailboxActivityReport.ps1"
  ```

此示例脚本将聚合的报告放在 ReportOutput.csv 文件中。
  
## <a name="see-also"></a>另请参阅

#### 

[适于合作伙伴的帮助](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[Office 365 报告 Web 服务](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Exchange Online 中的报告 cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=526430)

