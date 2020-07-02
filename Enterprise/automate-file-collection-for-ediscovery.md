---
title: 电子数据展示文件收集自动化
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 摘要：了解如何从用户计算机中自动收集文件以用于电子数据展示。
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997973"
---
# <a name="automate-file-collection-for-ediscovery"></a>电子数据展示文件收集自动化

All companies face the potential of lawsuits or other types of legal action. While legal departments work to reduce that exposure, litigation is a fact of business life. When a company faces legal action, they are required, through the process of legal discovery, to provide all relevant documentary materials to the court and to opposing counsel. 
  
eDiscovery is the process by which companies inventory, search, identify, preserve, filter, and make available the relevant documentary materials that exist in electronic form. SharePoint 2013, Exchange Server 2013, Lync Server 2013, SharePoint Online, and Exchange Online can hold large amounts of documentary content. Depending on the version, these products may support eDiscovery and in place holds (Lync via Exchange Server), making it easier for the legal teams to index, identify, hold, and filter the most relevant content for a given case.
  
Many documents are stored on users' (Custodians) local computers, not in a centralized location. This makes it essentially impossible for SharePoint 2013 to search, and if it can't be searched, it can't be included in eDiscovery. This solution shows you how to use logon scripts, System Center Orchestrator 2012 R2 and Windows PowerShell for Exchange Server to automate the identification and collection of documentary materials from users' computers.
  
## <a name="what-this-solution-does"></a>此解决方案的作用

This solution uses a global security group, Group Policy, and a Windows PowerShell script to locate, inventory, and collect content and Outlook personal store (PST) files from users local computers to a hidden file share. From there, the PST files can be imported into either Exchange Server 2013 or Exchange Online. All files are then moved using a System Center Orchestrator 2012 R2 runbook to another file share in Microsoft Azure for long-term storage and indexing by SharePoint 2013. You then use eDiscovery centers in your on-premises SharePoint 2013 deployment or in SharePoint Online as you regularly would to perform eDiscovery. 
  
> [!IMPORTANT]
> This solution uses robocopy to copy files from custodian's computers to a centralized file share. Because robocopy does not copy files that are open or locked, any files, including PST files, that the custodian has open will not be collected. You will have to collect them manually. This solution does provide you with a list that explicitly identifies the files it cannot copy and the full path to each file. 
  
下图向您展示了解决方案的所有步骤和元素。
  
![自动化文件收集解决方案概述](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|****图例****||
|:-----|:-----|
|![洋红色标注 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|创建一个组策略对象 (GPO) 并将其与收集登录脚本相关联。  <br/> |
|![洋红色标注 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)|   配置 GPO 安全筛选器，仅将 GPO 应用到保管人组 <br/> |
|![洋红色标注 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|保管人登录和 GPO 运行，调用收集登录脚本。  <br/> |
|![洋红色标注 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|收集登录脚本清单均本地挂载到保管人计算机上的驱动器，搜索您需要的文件并记录其位置。  <br/> |
|![洋红色标注 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|收集登录脚本将清单文件复制到暂存服务器上的隐藏文件共享中。  <br/> |
|![洋红色标注 6](media/99589726-0c7e-406b-a276-44301a135768.png)| （选项 A）手动运行 PST 导入脚本，将收集的 PST 文件导入到 Exchange Server 2013。 <br/> |
|![洋红色标注 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|（选项 B）使用 Microsoft 365 导入工具和过程，将收集的 PST 文件导入到 Exchange Online。  <br/> |
|![洋红色标注 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|将所有收集的文件移至 Azure 文件共享，以便在 MoveToColdStorageSystem Center Orchestrator 2012 R2 Runbook 中长期存储。 <br/> |
|![洋红色标注 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|使用 SharePoint 2013 对冷存储文件共享中的文件编制索引。  <br/> |
|![洋红色标注 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|对冷存储和本地 Exchange Server 2013 中的内容执行eDiscovery。  <br/> |
|![洋红色标注 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|对 Microsoft 365 中的内容执行电子数据展示。  <br/> |
   
## <a name="prerequisites"></a>先决条件

The configuration of this solution requires many elements, most of which you likely have in place and configured if you're thinking about eDiscovery. For the elements that you may not have or ones that require a specific configuration, we'll provide you with the links you need build out your base configuration. You must have the base configuration in place before you configure the solution itself.
  
### <a name="base-configuration"></a>基本配置

|**元素**|**链接**|
|:-----|:-----|
|Active Directory 域服务 (AD DS) 域  <br/> ||
|从本地网络的 Internet 连接  <br/> ||
|支持 SharePoint 2013 和 System Center Orchestrator 2012 R2 的 SQL Server 2012  <br/> |[部署 System Center Orchestrator - 2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| 用于eDiscovery的本地或基于 Azure 的 SharePoint 2013（选项 A 所必需） <br/> ||
|用于暂存的本地文件共享服务器  <br/> ||
|用于选项 A PST 导入的本地 Exchange Server 2013  <br/> |CU5 (15.913.22) 位于 [CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)。  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[部署 System Center Orchestrator - 2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|使用 Exchange Online 和 SharePoint Online 的 Microsoft 365 E3 （Option B 所必需）  <br/> |若要注册 Microsoft 365 E3 订阅，请参阅[microsoft 365 e3 订阅](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab)。  <br/> |
|对虚拟机的 Azure 订阅  <br/> |若要注册 Azure，请参阅[订阅 Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010) <br/> |
|本地网络和 Azure 订阅之间的 VPN 连接  <br/> |若要在 Azure 订阅和本地网络之间设置 VPN 隧道，请参阅[将本地网络连接到 Microsoft Azure 虚拟网络](https://go.microsoft.com/fwlink/p/?LinkId=613507)。  <br/> |
|SharePoint 2013 已配置 eDiscovery 以搜索 SharePoint 和 Exchange Server 2013 以及（可选）Lync Server 2013  <br/> |若要以这种方式配置eDiscovery，请参阅[在 SharePoint Server 2013 中配置电子数据展示](https://go.microsoft.com/fwlink/p/?LinkId=613508)和[测试实验室指南：为 Exchange、Lync、SharePoint 和 Windows 文件共享测试实验室配置电子数据展示](https://go.microsoft.com/fwlink/p/?LinkId=393130)。  <br/> |
|Microsoft 365 for SharePoint Online 和 Exchange Online 中的电子数据展示  <br/> |若要在 Microsoft 365 中配置电子数据展示，请参阅[在 SharePoint Online 中设置电子数据展示中心](https://go.microsoft.com/fwlink/p/?LinkId=613628)。  <br/> |
   
## <a name="configure-the-environment"></a>配置环境

现在您已具备基本配置， 可以继续配置解决方案本身。 
  
### <a name="staging-file-share"></a>暂存文件共享

1. 在本地域中创建一个名为 Custodians 的全局安全组。
    
2. Create a hidden file share for the files that are collected from Custodians computers. This should be on an on-premises server. For example, on a server called Staging, create a file share called Cases$. The **$** is required to make this a hidden share.
    
3. 设置下列共享权限：
    
  - 保管人：更改、读取
    
  - 管理员：完全控制
    
  - Exchange 受信任子系统：更改、读取
    
4. Open the **Security** tab, add the Custodians group, and click **Advanced**. Set the following permissions for the Custodians group:
    
  - **类型：拒绝**
    
  - **适用于：此文件夹及其子文件夹和文件**
    
5. 单击"高级权限"并选择以下项：
    
  - **读取属性**
    
  - **读取扩展属性**
    
  - **读取权限**
    
6. 通过执行以下操作测试对 Cases$ 文件共享的访问权限：
    
1. 将用户添加到 Custodians 组。
    
2. 将文件放在 Cases$ 文件夹中。
    
3. As the user, browse to the staging server, for example browse to the \\\\Staging share to see what shares are available. You shouldn't see the **Cases$** share listed.
    
4. Manually type the full path to the Cases$ share into Explorer. This should open the Cases$ share.
    
5. Try to open the file you previously placed in the share. This should fail.
    
### <a name="logon-script"></a>登录脚本

1. 将此 Windows PowerShell 脚本复制并粘贴到记事本：
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. 在易于您查找的位置将上述脚本另存为 CollectionScript.ps1，例如，C:\\AFCScripts。
    
3. Use the Go To feature in Notepad. Make the following changes, as needed:
    
|**行号**|**需更改的内容**|**必需/可选**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes** variable. Include all the file type extensions that you want the script to inventory and collect in the array variable. <br/> |可选  <br/> |
|76 和 77  <br/> |Change the way the **$CaseNo** variable is built to suit your needs. The script captures the current date and time and appends the user name to it. <br/> |可选  <br/> |
|80  <br/> |**$CaseRootLocation** 变量需设置为您的暂存服务器集合文件共享，例如， **\\\\Staging\\Cases$** 。 <br/> |必需  <br/> |
   
4. 将 CollectionScript.ps1 文件放在域控制器上的 Netlogon 文件共享中。 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>为登录脚本和 Custodians 组配置 GPO

1. 按照[使用组策略中的启动、关机、登录和注销脚本](https://go.microsoft.com/fwlink/p/?LinkId=614844)主题中的"如何分配用户登录脚本"部分为 Custodians 组配置登录脚本。
    
2. 从"安全筛选"中移除经过身份验证的用户并添加 Custodians 组。
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>PST 导入选项 A，Exchange Server 2013 的脚本

1.  将以下 Windows PowerShell 脚本复制并粘贴到记事本中：
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. Save the script as PSTImportScript.ps1 in a location that's easy for you to find. For example and ease of use, create a folder on your staging server called \\\\Staging\\AFCScripts, and save it there.
    
3. 使用记事本中的“转到”功能，根据需要进行以下更改：
    
|**行号**|**需更改的内容**|**必需/可选**|
|:-----|:-----|:-----|
|12   <br/> |**$FolderIdentifier** tags the mailbox folders that PSTs are imported into. Change this if necessary. <br/> |可选  <br/> |
|17   <br/> |**$ConnectionUri** 需设置为您自己的服务器。 <br/> > [!IMPORTANT]> Make sure your **$ConnectionUri** points to a http location, not https. It won't work with https:.          |必需  <br/> |
   
4. 确认 Exchange 受信任子系统帐户具有 \\\\Staging\\Cases$ 共享的读取、写入和执行权限。
    
5. PST 导入脚本需要以下两个输入参数：
    
  - **$SourcePath** ，要导入的 PST 文件的位置，例如 \\\\Staging\\Cases$。
    
  - **$MailboxAlias** ，将接收导入的电子邮件的目标邮箱的别名。
    
6. 例如，如果您想将路径 \\Staging\Cases$ 中的所有 PST 文件都导入到别名为 eDiscoveryMailbox 的邮箱，您需要运行与此类似的脚本 `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`。
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST 导入选项 B，用于 Exchange Online

-  Create the mailbox structure to place the imported PST files into. For more information on how to create a user mailbox in Exchange Online, see[Create User Mailboxes in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=615118).
    
### <a name="cold-storage"></a>冷存储

1. 在放置所有收集的文件的 Azure 虚拟机 上创建一个文件共享，例如，\\\\AZFile1\\ContentColdStorage。
    
2. Grant the default content access account at least Read permissions to the share and all subfolders and files. For more information about configuring SharePoint 2013 Search, see [Create and configure a Search service application in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=614940).
    
3. 如果您预计从 \\\\AZFile1\\ContentColdStorage 导入 PST 文件，请向 Exchange 受信任子系统授予对共享的读取、写入和执行权限。
    
### <a name="orchestrator"></a>Orchestrator

1. 从 Microsoft 下载中心下载 [MoveToColdStorage Runbook](https://go.microsoft.com/fwlink/?LinkId=616095)。
    
2. Open the **Runbook Designer**, in the **Connections** pane, click the folder that you want to import the runbook into. Click the **Actions** menu, and the click **Import**. The **Import** dialog box appears.
    
3. 在“文件位置”**** 框中，键入要导入的 Runbook 的路径和文件名，或单击省略号 (**...**) 转到要导入的文件。 
    
4. Select **Import runbooks** and **Import Orchestrator encrypted data**. Clear **Counters**, **Schedules**, **Variables**, **Computer Groups**, **Import global configurations**, and **Overwrite existing global configurations**.
    
5. 单击“完成”****。
    
6. 编辑 **MoveFilesToColdStorage** 运行手册，如下所述：
    
1. **Move File** activity - set the **Source File** path to the collection file share, for example \\\\Staging\\cases$. Set the **Destination Folder** to the cold storage file share in Azure, for example \\\\AZFile1\\ContentColdStorage. Select **Create a file with a unique name**.
    
2. **删除文件夹**活动 - 将“路径:”**** 设置为集合文件共享（例如，\\\\Staging\\cases$\\*），再选择“删除所有文件和子文件夹”****。 
    
7. 使用[部署 Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615120) 中的过程部署 **MoveToColdStorage** Runbook。
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>冷存储的 SharePoint 本地搜索

1. Create an new content source in your SharePoint 2013 farm for the cold storage share in Azure, for example \\\\AZFile1\\ContentColdStorage. For more information about managing content sources, see [Add, edit, or delete a content source in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615004)
    
2. Start a full crawl. For more information see, [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
## <a name="using-the-solution"></a>使用解决方案

There are five major steps in using this solution, assuming you don't want to import the PST files into both Exchange Server 2013 and Exchange Online. This section provides you with the procedures for all of them. Your primary interaction with the solution will be in doing the following:
  
1. 管理 Custodians 组中的用户成员资格。
    
2. Review the log files generated by the logon script. The FileCopyErrors.log lists all the files that were not successfully copied. You need to decide what you want to do with them
    
3. 管理 PST 导入过程。
    
4. 将集合文件移至冷存储。
    
所有其他步骤并非此解决方案所特有。 它们是您在 SharePoint 2013、Microsoft 365 和 Azure 中执行的标准管理任务。 有一些项目此解决方案未提供任何指导，您将需要根据公司的需求进行规划，例如：
  
1. 跟踪您的eDiscovery案例，以及哪些保管人与哪个案例关联。
    
2. 跟踪哪些文件集与哪个eDiscovery案例关联。
    
3. 协调导入的时间并转至冷存储步骤。
    
4. 管理 Azure 中所用的文件空间。
    
5. 管理向其中导入 PST 的邮箱。
    
6. 备份和还原所有本地数据。
    
### <a name="custodian-management"></a>保管人管理

- To start the automated file collection process for an individual user, add them to the Custodians group. The next time that the user logs on, the logon script assigned to the Custodians group through Group Policy will run. 
    
### <a name="monitor-collected-files-and-review-log-files"></a>监控收集的文件和检查日志文件

1. Watch the collection file share, for example \\\\Staging\\cases$\\*, for the collection folder from the user. The name of the folder will be formatted like this:  *yyyyMMddHHmm_UserName*  .
    
2. When the collection is completed, open the collection folder, and browse to the _Log folder. In the _Log folder, you will see the following:
    
  - One XML file for every local drive on the user's computer, for example **A.xml**, **C.xml**. These files contain the inventory drives that they are named after, and they are used for the robocopy operation.
    
    > [!NOTE]
    > The collection script will only create an entry in the inventory file for the file types that you defined in the script itself. It will not create an inventory entry for every file on the user's computer. 
  
  - One log file named FileCopyErrors.log for each collection run. This file contains a listing of the files that robocopy could not copy to the file collection share, for example, \\\\Staging\\cases$\\*. You will need to review this and decide what actions to take for these missed files. Usually, you either need to collect them manually if you want them, or you may decide that they are not required and can therefore be omitted from the collection.
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>PST 导入选项 A，用于 Exchange Server 2013

1. Log on to the server that hosts the collection file share, for example **Staging**, and open Windows PowerShell. For more information about starting Windows PowerShell, see[Starting Windows PowerShell on Windows Server](https://go.microsoft.com/fwlink/p/?LinkId=615115).
    
2. Set the Execution policy to Unrestricted . Type  `Set-ExecutionPolicy Unrestricted -Scope Process` into Windows PowerShell, and press Enter.
    
3. Run the PSTImportScript.ps1 file, and provide the **$SourcePath** and **$MailboxAlias** parameters. For more information about running Windows PowerShell scripts, see[Running Scripts](https://go.microsoft.com/fwlink/p/?LinkID=615117).
    
4. 查看针对错误的输出。
    
5. Before you attempt to import an identically named PST file into the same mailbox, you have to remove the mailbox import request. Run the following command to do that:  `Get-MailboxImportRequest | Remove-MailboxImportRequest`. You will be prompted to remove each individual request from the queue. Respond as needed.
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST 导入选项 B，用于 Exchange Online

- 若要将收集的 PST 文件置于 Exchange Online 中，请按照将文件导入到 Microsoft 365 中的过程中的步骤进行[网络上载](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files)。
    
### <a name="move-to-cold-storage"></a>移至冷存储

1. 使用[运行 runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123)中的过程运行**MoveToColdStorage** runbook。
    
2. Watch the Azure file share you are using for long term storage, for example \\\\AZFile1\\ContentColdStorage and the on-premises collection file share, for example \\\\Staging\\cases$. You should see the files and folders appear in the cold storage file share and disappear from the collection file share.
    
### <a name="ediscovery"></a>电子数据展示

1. Either allow the full crawl of the cold storage file share to run as schedules, or initiate a crawl. For more information on starting full or incremental crawls, see [Start, pause, resume, or stop a crawl in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=615005).
    
2. 如果您使用选项 A 进行 PST 文件导入，请在 SharePoint 2013 中创建eDiscovery案例；或者如果您使用选项 B，请在 SharePoint Online 中创建eDiscovery案例。
    

