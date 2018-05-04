---
title: 使用 Office 365 PowerShell 创建 SharePoint Online 网站并添加用户
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要： 使用 Office 365 PowerShell，可以创建新的 SharePoint Online 网站，并将这些网站中添加用户和组。
ms.openlocfilehash: 0a0438917f6e7010b56703ce0bf73e89e1db0533
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>使用 Office 365 PowerShell 创建 SharePoint Online 网站并添加用户

 **摘要：**使用 Office 365 PowerShell 中创建新的 SharePoint Online 网站，然后这些网站中添加用户和组。

当您使用 Office 365 PowerShell 中创建 SharePoint Online 网站和添加用户时，您可以快速反复执行任务比您可以在 Office 356 管理中心快得多。您还可以执行不能在 Office 356 管理中心执行的任务。 

## <a name="before-you-begin"></a>准备工作

本主题中的过程需要连接到 SharePoint Online。有关说明，请参阅[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>步骤 1：使用 Office 365 PowerShell 创建新的网站集

使用 Office 365 PowerShell 和你使用提供的示例代码和记事本创建的 .csv 文件创建多个网站。在此步骤中，你将使用你自己的网站和租户特定信息替换括号中显示的占位符信息。此过程使你能够创建单个文件并运行一个使用该文件的 Office 365 PowerShell 命令。这使得所采取的操作具有可重复性和可移植性，并可以减少许多（如果不是全部）因向 SharePoint Online 命令行管理程序键入长命令而导致的错误。此步骤包括两个部分。首先，你要创建一个 .csv 文件，然后使用 Office 365 PowerShell 引用该 .csv 文件，从而利用该文件的内容来创建网站。

Office 365 PowerShell cmdlet 导入 .csv 文件并将其通过管道传递到大括号内的循环中，该循环将读取文件的第一行作为列标题。然后，Office 365 PowerShell cmdlet 循环访问剩余的记录，为每个记录创建一个新的网站集，并根据列标题指定网站集的属性。

###<a name="create-a-csv-file"></a>创建 .csv 文件

1. 打开记事本，然后向其中粘贴以下文本块：</br>
```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```</br>Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</br>(You can press Ctrl+H when you use Notepad to bulk replace faster.)</br>
2. Save the file on your desktop as **SiteCollections.csv**.

 > [!TIP]
> Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.

### Run the Windows PowerShell command

1. At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</br>
```
导入 Csv C:\users\MyAlias\desktop\SiteCollections.csv |Foreach-object {新 SPOSite-所有者 $_。所有者-StorageQuota $_。StorageQuota-Url $_。Url 不等待-ResourceQuota $_。ResourceQuota-模板 $_。模板-TimeZoneID $_。TimeZoneID-Title $_。名称}
```
</br>Where *MyAlias* equals your user alias.</br>
2. Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</br>
3. At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</br>
```
Get-sposite-详细 |表格格式 AutoSize
```</br>
4. Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**.

That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.

## Step 2: Add users and groups

Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.

The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.

### Create .csv and .ps1 files

1. Open Notepad, and paste the following text block into it:</br>
```
网站、 组、 PermissionLevels https://tenant.sharepoint.com/sites/contosotest，Contoso Project Leads，完全控制https://tenant.sharepoint.com/sites/contosotest，Contoso Auditors 仅查看https://tenant.sharepoint.com/sites/contosotest，Contoso 设计器中，设计https://tenant.sharepoint.com/sites/TeamSite01，XT1000 工作组领导，完全控制https://tenant.sharepoint.com/sites/TeamSite01，XT1000 顾问编辑https://tenant.sharepoint.com/sites/Blog01，Contoso 博客 （英文)设计人员设计https://tenant.sharepoint.com/sites/Blog01，Contoso 博客编辑器，编辑https://tenant.sharepoint.com/sites/Project01Project Alpha 审批者、 完全控制
```
</br>Where *tenant* equals your tenant name.</br>
2. Save the file to your desktop as **GroupsAndPermissions.csv**.</br>
3. Open a new instance of Notepad, and paste the following text block into it:</br>
```
组中，使用 LoginName，网站 Contoso Project Leads，username@tenant.onmicrosoft.com，https://tenant.sharepoint.com/sites/contosotest Contoso 审核员、 username@tenant.onmicrosoft.com，https://tenant.sharepoint.com/sites/contosotest Contoso 设计器、 username@tenant.onmicrosoft.com，https://tenant.sharepoint.com/sites/contosotest XT1000 工作组负责人username@tenant.onmicrosoft.com，https://tenant.sharepoint.com/sites/TeamSite01 XT1000 顾问、 username@tenant.onmicrosoft.com，https://tenant.sharepoint.com/sites/TeamSite01 Contoso 博客设计器、 username@tenant.onmicrosoft.com，https://tenant.sharepoint.com/sites/Blog01 Contoso 博客编辑器中，username@tenant.onmicrosoft.com，https://tenant.sharepoint.com/sites/Blog01项目 Alpha 审批者、 username@tenant.onmicrosoft.com，https://tenant.sharepoint.com/sites/Project01
```
</br>Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</br>
4. Save the file to your desktop as **Users.csv**.</br>
5. Open a new instance of Notepad, and paste the following text block into it:</br>
```
导入 Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv |Foreach-object {新 SPOSiteGroup-组 $_。组-PermissionLevels $_。PermissionLevels-网站 $_。Site} 导入 Csv C:\users\MyAlias\desktop\Users.csv |其中 {添加 SPOUser-组 $_。$_组 – LoginName。使用 LoginName-网站 $_。Site}
```
</br>Where MyAlias equals the user name of the user that is currently logged on.</br>
6. Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.

You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.

### Run UsersAndGroups.ps1 script

1. Return to the SharePoint Online Management Shell.</br>
2. At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</br>
```
Set-executionpolicy 绕过
```</br>
3. At the confirmation prompt, press **Y**.</br>
4. At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</br>
```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
</br>Where *MyAlias* equals your user name.</br>
5. Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.

## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Manage SharePoint Online site groups Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

