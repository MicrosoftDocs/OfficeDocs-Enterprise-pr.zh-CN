---
title: 电子数据展示文件收集自动化
ms.author: chrfox
author: chrfox
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 摘要：了解如何从用户计算机中自动收集文件以用于电子数据展示。
ms.openlocfilehash: ccea04f4573a16750f588295fca5621d5abd8498
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077715"
---
# <a name="automate-file-collection-for-ediscovery"></a>电子数据展示文件收集自动化

 **摘要：** 了解如何从用户计算机中自动收集文件以用于电子数据展示。
  
所有公司都有可能采取诉讼或其他类型的法律行动。尽管法律部门致力于减少曝光，但是诉讼是商业活动中的平常事。公司在法律发现过程中需采取法律行动，向法院和对方律师提供所有相关书面材料。 
  
电子数据展示是一个过程，通过此过程公司可以进行存储、搜索、识别、保留、筛选，以及提供以电子形式存在的相关书面材料。 SharePoint 2013、Exchange Server 2013、Lync Server 2013、SharePoint Online 和 Exchange Online 可以容纳大量的书面内容。 根据版本，这些产品可以支持eDiscovery和就地保留（Lync，通过 Exchange Server），这使得法律团队更易于对给定案例的最相关的内容进行索引编制、标识、保留和筛选。
  
许多文档存储在用户（保管人）的本地计算机上，而不是存储在某个集中位置。这使得 SharePoint 2013 基本上不可能进行搜索；如果无法搜索，则不能包含在eDiscovery中。此解决方案显示如何使用登录脚本、System Center Orchestrator 2012 R2 和 Windows PowerShell，使 Exchange Server 从用户的计算机中自动标识和收集书面材料。
  
## <a name="what-this-solution-does"></a>此解决方案的作用

此解决方案使用全局安全组、组策略和 Windows PowerShell 脚本来查找、存储和收集用户本地计算机中的内容和 Outlook 个人存储 (PST) 文件并存储到隐藏的文件共享中。在此处，PST 可能会导入到 Exchange Server 2013 或 Exchange Online。然后，所有文件使用 System Center Orchestrator 2012 R2 Runbook 移动到 Microsoft Azure 中的另一个文件共享，以便由 SharePoint 2013 长期存储和索引。然后您可以像平时一样使用本地 SharePoint 2013 部署或 SharePoint Online 中的eDiscovery中心执行eDiscovery。 
  
> [!IMPORTANT]
> 此解决方案使用 robocopy 将文件从保管人的计算机中复制到一个集中的文件共享。因为 robocopy 不复制打开或锁定的文件，所以不会收集保管人打开的任意文件，其中包括 PST 文件。您需要手动收集这些文件。此解决方案确实为您提供一个列表，明确标识了它无法复制的文件和每个文件的完整路径。 
  
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
|![洋红色标注 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|（选项 B）使用 Office 365 导入工具和过程，将收集的 PST 文件导入到 Exchange Online。  <br/> |
|![洋红色标注 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|将所有收集的文件移至 Azure 文件共享，以便在 MoveToColdStorageSystem Center Orchestrator 2012 R2 Runbook 中长期存储。 <br/> |
|![洋红色标注 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|使用 SharePoint 2013 对冷存储文件共享中的文件编制索引。  <br/> |
|![洋红色标注 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|对冷存储和本地 Exchange Server 2013 中的内容执行eDiscovery。  <br/> |
|![洋红色标注 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|对 Office 365 中的内容执行eDiscovery。  <br/> |
   
## <a name="prerequisites"></a>先决条件

如果您正在考虑 eDiscovery，此解决方案的配置需要很多 元素，其中大部分您可能已经具备并已配置。对于您可能不具备或者需要特定配置的元素，我们将为您提供生成基本配置所需的链接。您必须在配置解决方案之前就已具备基本配置。
  
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
|具有 Exchange Online 和 SharePoint Online 的 Office 365（E3 计划）（选项 B 所必需）  <br/> |若要注册 Office 365 E3 订阅，请参阅 [Office 365 E3 订阅](https://go.microsoft.com/fwlink/p/?LinkId=613504)。  <br/> |
|对虚拟机的 Azure 订阅  <br/> |若要注册 Azure，请参阅[订阅 Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010) <br/> |
|本地网络和 Azure 订阅之间的 VPN 连接  <br/> |若要在 Azure 订阅和本地网络之间设置 VPN 隧道，请参阅[将本地网络连接到 Microsoft Azure 虚拟网络](https://go.microsoft.com/fwlink/p/?LinkId=613507)。  <br/> |
|SharePoint 2013 已配置 eDiscovery 以搜索 SharePoint 和 Exchange Server 2013 以及（可选）Lync Server 2013  <br/> |若要以这种方式配置eDiscovery，请参阅[在 SharePoint Server 2013 中配置电子数据展示](https://go.microsoft.com/fwlink/p/?LinkId=613508)和[测试实验室指南：为 Exchange、Lync、SharePoint 和 Windows 文件共享测试实验室配置电子数据展示](https://go.microsoft.com/fwlink/p/?LinkId=393130)。  <br/> |
|Office 365 中的eDiscovery用于 SharePoint Online 和 Exchange Online  <br/> |若要在 Office 365 中配置eDiscovery，请参阅[在 SharePoint Online 中设置电子数据展示中心](https://go.microsoft.com/fwlink/p/?LinkId=613628)。  <br/> |
   
## <a name="configure-the-environment"></a>配置环境

现在您已具备基本配置， 可以继续配置解决方案本身。 
  
### <a name="staging-file-share"></a>暂存文件共享

1. 在本地域中创建一个名为 Custodians 的全局安全组。
    
2. 为从保管人计算机中收集的文件创建一个隐藏文件共享。这应在本地服务器上。例如，在名为 Staging 的服务器上，创建一个名为 Cases$ 的文件共享。必须包含 **$** 才能使该共享成为隐藏共享。
    
3. 设置下列共享权限：
    
  - 保管人：更改、读取
    
  - 管理员：完全控制
    
  - Exchange 受信任子系统：更改、读取
    
4. 打开"安全"选项卡，添加 Custodians 组，然后单击"高级"。为 Custodians 组设置以下权限：
    
  - **类型：拒绝**
    
  - **适用于：此文件夹及其子文件夹和文件**
    
5. 单击"高级权限"并选择以下项：
    
  - **读取属性**
    
  - **读取扩展属性**
    
  - **读取权限**
    
6. 通过执行以下操作测试对 Cases$ 文件共享的访问权限：
    
1. 将用户添加到 Custodians 组。
    
2. 将文件放在 Cases$ 文件夹中。
    
3. 作为用户，浏览到暂存服务器，例如浏览到 \\\\Staging 共享以查看提供了哪些共享。不应看到 **Cases$** 共享列出。
    
4. 将 Cases$ 共享的完整路径手动键入到资源管理器中。这应该会打开 Cases$ 共享。
    
5. 尝试打开您之前放在共享中的文件，这应该会失败。
    
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
    
3. 使用记事本中的“转到”功能。根据需要进行以下更改：
    
|**行号**|**需更改的内容**|**必需/可选**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes** 变量。包括您希望脚本在数组变量中存储和收集的所有文件类型扩展名。<br/> |可选  <br/> |
|76 和 77  <br/> |更改 **$CaseNo** 变量构建的方式以满足您的需求。脚本捕获当前日期和时间并向其附加用户名。<br/> |可选  <br/> |
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

2. 在易于您查找的位置将脚本另存为 PSTImportScript.ps1。例如，为易于使用，在暂存服务器上创建一个名为 \\\\Staging\\AFCScripts 的文件夹并将脚本保存在其中。
    
3. 使用记事本中的“转到”功能，根据需要进行以下更改：
    
|**行号**|**需更改的内容**|**必需/可选**|
|:-----|:-----|:-----|
|12  <br/> |**$FolderIdentifier** 标记在其中导入 PST 的邮箱文件夹。根据需要更改此变量。<br/> |可选  <br/> |
|×  <br/> |**$ConnectionUri** 需设置为您自己的服务器。 <br/> > [!IMPORTANT]> 确保您的 **$ConnectionUri** 指向 http 位置，而不是 https。它不适用于 https:。          |必需  <br/> |
   
4. 确认 Exchange 受信任子系统帐户具有 \\\\Staging\\Cases$ 共享的读取、写入和执行权限。
    
5. PST 导入脚本需要以下两个输入参数：
    
  - **$SourcePath** ，要导入的 PST 文件的位置，例如 \\\\Staging\\Cases$。
    
  - **$MailboxAlias** ，将接收导入的电子邮件的目标邮箱的别名。
    
6. 例如，如果您想将路径 \\Staging\Cases$ 中的所有 PST 文件都导入到别名为 eDiscoveryMailbox 的邮箱，您需要运行与此类似的脚本 `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`。
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST 导入选项 B，用于 Exchange Online

-  创建将放置导入的 PST 文件的邮箱结构。有关在 Exchange Online 中如何创建用户邮箱的详细信息，请参阅[在 Exchange Online 中创建用户邮箱](https://go.microsoft.com/fwlink/p/?LinkId=615118)。
    
### <a name="cold-storage"></a>冷存储

1. 在放置所有收集的文件的 Azure 虚拟机 上创建一个文件共享，例如，\\\\AZFile1\\ContentColdStorage。
    
2. 向默认内容访问帐户至少授予对共享以及所有子文件夹和文件的读取权限。有关配置 SharePoint 2013 Search 的详细信息，请参阅[在 SharePoint Server 2013 中创建和配置 Search Service 应用程序](https://go.microsoft.com/fwlink/p/?LinkId=614940)。
    
3. 如果您预计从 \\\\AZFile1\\ContentColdStorage 导入 PST 文件，请向 Exchange 受信任子系统授予对共享的读取、写入和执行权限。
    
### <a name="orchestrator"></a>Orchestrator

1. 从 Microsoft 下载中心下载 [MoveToColdStorage Runbook](https://go.microsoft.com/fwlink/?LinkId=616095)。
    
2. 打开"Runbook Designer"，在"连接"窗格中，单击您想要在其中导入 Runbook 的文件夹。单击"操作"菜单，然后单击"导入"。此时将出现"导入"对话框。
    
3. 在“文件位置”**** 框中，键入要导入的 Runbook 的路径和文件名，或单击省略号 (**...**) 转到要导入的文件。 
    
4. 依次选择"导入 Runbook"和"导入 Orchestrator 加密数据"。清除"计数器"、"计划"、"变量"、"计算机组"、"导入全局配置"和"覆盖现有全局配置"。
    
5. 单击“完成”****。
    
6. 编辑 **MoveFilesToColdStorage** 运行手册，如下所述：
    
1. **移动文件**活动 - 将“源文件”**** 路径设置为集合文件共享（例如，\\\\Staging\\cases$）。将“目标文件夹”**** 设置为 Azure 中的冷存储文件共享（例如，\\\\AZFile1\\ContentColdStorage）。选择“创建具有唯一名称的文件”****。
    
2. **删除文件夹**活动 - 将“路径:”**** 设置为集合文件共享（例如，\\\\Staging\\cases$\\*），再选择“删除所有文件和子文件夹”****。 
    
7. 使用[部署 Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615120) 中的过程部署 **MoveToColdStorage** Runbook。
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>冷存储的 SharePoint 本地搜索

1. 在 SharePoint 2013 服务器场中为 Azure 中的冷存储共享创建一个新的内容源，例如 \\\\AZFile1\\ContentColdStorage。有关管理内容源的详细信息，请参阅[在 SharePoint Server 2013 中添加、编辑或删除内容源](https://go.microsoft.com/fwlink/p/?LinkId=615004)
    
2. 启动完整爬网。有关详细信息，请参阅[在 SharePoint Server 2013 中启动、暂停、继续或停止爬网](https://go.microsoft.com/fwlink/p/?LinkId=615005)。
    
## <a name="using-the-solution"></a>使用解决方案

使用此解决方案有五个主要步骤，假定您不希望将 PST 文件导入到 Exchange Server 2013 和 Exchange Online。本部分为您提供了所有这些步骤的过程。您主要在执行以下操作时与解决方案交互：
  
1. 管理 Custodians 组中的用户成员资格。
    
2. 错误
    
3. 管理 PST 导入过程。
    
4. 将集合文件移至冷存储。
    
所有其他步骤并非此解决方案所特有。这是您在 SharePoint 2013、Office 365 和 Azure 中执行的标准管理任务。有一些项目此解决方案未提供任何指导，您将需要根据公司的需求进行规划，例如：
  
1. 跟踪您的eDiscovery案例，以及哪些保管人与哪个案例关联。
    
2. 跟踪哪些文件集与哪个eDiscovery案例关联。
    
3. 协调导入的时间并转至冷存储步骤。
    
4. 管理 Azure 中所用的文件空间。
    
5. 管理向其中导入 PST 的邮箱。
    
6. 备份和还原所有本地数据。
    
### <a name="custodian-management"></a>保管人管理

- 要启动单个用户的自动化文件收集过程，请将其添加到 Custodians 组。 下次用户登录时，将运行通过组策略分配到 Custodians 组的登录脚本。 
    
### <a name="monitor-collected-files-and-review-log-files"></a>监控收集的文件和检查日志文件

1. 观察集合文件共享，例如 \\\\Staging\\cases$\\*，查找用户的集合文件夹。文件夹的名称将为以下格式： *yyyyMMddHHmm_UserName*  。
    
2. 收集完成后，打开集合文件夹并浏览到 _Log 文件夹。在 _Log 文件夹中，您将看到以下内容：
    
  - 用户的计算机上每个本地驱动器的一个 XML 文件，例如 **A.xml** 、 **C.xml** 。这些文件包含按其命名的库存驱动器，且它们用于 robocopy 操作。
    
    > [!NOTE]
    > 收集脚本将仅在您在脚本本身定义的文件类型的清单文件中创建一个条目。它不会为用户的计算机上的每个文件都创建一个清单条目。 
  
  - 将运行每个集合的一个名为 FileCopyErrors.log 的日志文件。此文件包含 robocopy 不会复制到文件集合共享的文件列表，例如 \\\\Staging\\cases$\\*。您将需要审核此文件，并确定为这些缺少的文件采取的操作。通常，如果您需要这些文件，您应手动收集它们；您也可以决定不需要它们，因此可将其从收集中忽略。
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>PST 导入选项 A，用于 Exchange Server 2013

1. 登录到承载集合文件共享的服务器上，例如 **Staging** ，然后打开 Windows PowerShell。有关启动 Windows PowerShell 的详细信息，请参阅[在 Windows Server 上启动 Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=615115)。
    
2. 将执行策略设置为无限制。将  `Set-ExecutionPolicy Unrestricted -Scope Process` 键入到 Windows PowerShell 中并按 Enter。
    
3. 运行 PSTImportScript.ps1 文件，并提供 **$SourcePath** 和 **$MailboxAlias** 参数。有关运行 Windows PowerShell 脚本的详细信息，请参阅[运行脚本](https://go.microsoft.com/fwlink/p/?LinkID=615117)。
    
4. 查看针对错误的输出。
    
5. 在尝试将一个同名的 PST 文件导入到同一个邮箱之前，必须删除邮箱导入请求。为此，请运行下列命令： `Get-MailboxImportRequest | Remove-MailboxImportRequest`。系统将提示您从队列中删除每个单独的请求。根据需要响应。
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST 导入选项 B，用于 Exchange Online

- 若要将收集的 PST 文件放到 Exchange Online 中，请执行 [Office 365 导入服务](https://go.microsoft.com/fwlink/p/?LinkId=614938)的"通过网络上载将文件导入到 Office 365"部分中的步骤。
    
### <a name="move-to-cold-storage"></a>移至冷存储

1. 使用[运行 Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123) 中的步骤运行 **MoveToColdStorage** Runbook。
    
2. 观察用于长期存储的 Azure 文件共享（例如 \\\\AZFile1\\ContentColdStorage）和本地集合文件共享（例如 \\\\Staging\\cases$）。您应该会看到文件和文件夹出现在冷存储文件共享中，并从集合文件共享中消失。
    
### <a name="ediscovery"></a>电子数据展示

1. 允许冷存储文件共享的完全爬网按计划运行，或者启动爬网。有关启动完全或增量爬网的详细信息，请参阅[在 SharePoint Server 2013 中启动、暂停、继续或停止爬网](https://go.microsoft.com/fwlink/p/?LinkId=615005)。
    
2. 如果您使用选项 A 进行 PST 文件导入，请在 SharePoint 2013 中创建eDiscovery案例；或者如果您使用选项 B，请在 SharePoint Online 中创建eDiscovery案例。
    

