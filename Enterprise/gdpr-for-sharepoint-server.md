---
title: 适用于 SharePoint Server 的 GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: 了解如何解决本地 SharePoint Server 中的 GDPR 要求。
ms.openlocfilehash: 81ee339748923af835f88f73f5cf891d01212a17
ms.sourcegitcommit: 53a57b0617b5bb22beea766e515873d14b3a4783
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-sharepoint-server"></a>适用于 SharePoint Server 的 GDPR

作为保护个人信息的一部分，建议进行以下操作：

-   使用 Azure 信息保护对数据进行分类。

-   在最低特权配置中运行 SharePoint Server。如需详细信息，请参阅[在 SharePoint Server 中规划最低权限管理](https://docs.microsoft.com/SharePoint/security-for-sharepoint-server/plan-for-least-privileged-administration)和 [SharePoint Server 的安全性](https://docs.microsoft.com/zh-CN/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server)。

-   [在服务器上启用 BitLocker 加密](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server)。

## <a name="user-generated-content"></a>用户生成的内容

对于 SharePoint Server 站点和库中包含的用户生成的内容，建议使用以下基本方法：

-   使用 Azure 信息保护来标记敏感数据。

-   使用 [SharePoint Server 搜索](https://docs.microsoft.com/SharePoint/search/search)和[电子数据展示](https://docs.microsoft.com/SharePoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server)，检索敏感数据。

对于文件共享和 SharePoint 站点和库，推荐的方法包括下列步骤：

1.  **安装并配置 Azure 信息保护扫描程序。**

    -   决定要使用的敏感数据类型。

    -   指定要使用的 SharePoint 站点。

2.  **完成发现周期。**

    -   以发现模式运行扫描程序并验证查找结果。

    -   如果需要，优化条件和敏感信息类型。

    -   评估自动应用标签的预期影响。

3.  **运行 Azure 信息保护扫描程序以便标记合格文档**。

4.  **对于保护：**

    a. 配置 Exchange 数据丢失防护规则以保护具有所需标签的文档。

    b. 务必要使用权限来限制可访问文件的人员。

    c. 对于 SharePoint，使用 IRM 保护对库进行保护。

5.  **要进行监控，请使用 SIEM 工具集成 Windows Server 日志。**

    a. 若要查找数据主体请求，请使用搜索中心或电子数据展示。

如果对敏感数据应用标签，请务必使用未配置保护的标签。保护包括可阻止服务检测文件中的敏感数据的加密。

有关使用 Azure 信息保护扫描程序查找和标记个人数据的详细信息，请参阅 [Microsoft GDPR 数据发现工具包](http://aka.ms/gdprpartners) (http://aka.ms/gdprpartners))。

有关配置条件扫描程序和使用 Office 365 数据丢失防护 (DLP) 敏感信息类型的信息，请参阅[如何为 Azure 信息保护的自动推荐分类配置条件](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-classification)。请注意，新的 Office 365 敏感信息类型不会立即可供扫描程序使用，并且自定义敏感信息类型不能与扫描程序一起使用。

## <a name="removing-personal-information-from-office-files"></a>从 Office 文件中删除个人信息

必须手动从存储于 SharePoint 文档库中的 Office 文件中删除个人信息（例如 Word 文档中的元数据和批注）。请按照以下步骤操作：

1.  将文档副本从 SharePoint Server 中下载到本地磁盘。

2.  从 SharePoint 文档库中删除文档。

3.  按照[通过检查文档删除隐藏数据和个人信息](https://support.office.com/article/356B7B5D-77AF-44FE-A07F-9AA4D085966F)中的步骤操作。

4.  将文档上传到 SharePoint 文档库。

## <a name="telemetry-and-log-files"></a>遥测和日志文件

### <a name="uls-logs"></a>ULS 日志

SharePoint Server 中的统一日志记录服务 (ULS) 和使用情况日志记录可跟踪各种系统功能并包含用户信息。ULS 日志和使用情况日志为文本文件，可使用各种搜索工具进行搜索。[Merge-SPLogFile PowerShell cmdlet](https://docs.microsoft.com/zh-CN/powershell/module/sharepoint-server/merge-splogfile) 提供了一种从场中多台服务器上的 ULS 日志中返回记录的方式。

考虑将日志保留策略设置为业务目的所需的最小值。有关如何在 SharePoint Server 中配置日志记录的信息，请参阅[在 SharePoint Server 中配置诊断日志记录](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging)。

请注意，部分系统事件也记录在 Windows 事件日志中。

### <a name="usage-database"></a>使用情况数据库

SharePoint Server 使用情况数据库（默认名称为 WSS_Logging）包含 ULS 日志中所找到信息的子集。此数据库中的最大数据保留时间为 30 天。建议配置为业务需求允许的最短持续时间。有关详细信息，请参阅[在 SharePoint Server 中配置诊断日志记录](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging)。

## <a name="personal-information-and-search"></a>个人信息和搜索

搜索查询历史记录和使用情况记录包含对用户名的引用。

### <a name="query-history-and-favorite-queries"></a>查询历史记录和收藏的查询

在 SharePoint Server 2013 和 SharePoint Server 2016 中，查询历史记录和收藏的查询在 365 天后自动到期。如果用户离开你的组织，可使用以下步骤从查询历史记录中删除对用户名的引用。

下列 SQL 查询适用于 SharePoint 2013 和 SharePoint 2016，并且可以：

-   导出用户的查询历史记录或收藏的查询

-   删除查询历史记录中对用户名的引用

#### <a name="export-a-users-queries-since-a-specific-date"></a>导出自特定日期以来的用户查询 

使用以下步骤，从 Link Store 查询日志表中导出 @UserName 自 @StartTime 以来执行的查询。

```sql
[In dbo].[LinkStore_<ID>]:
CREATE PROCEDURE proc_MSS_GetQueryTermsForUser 
( 
    @UserName nvarchar(256), 
    @StartTime datetime 
) 
AS 
BEGIN 
    SET NOCOUNT ON; 
    SELECT searchTime, queryString 
    FROM 
        dbo.MSSQLogPageImpressionQuery 
    WITH 
        (NOLOCK) 
    WHERE 
        userName = @UserName AND 
        searchTime > @StartTime 
END 
GO 
```

#### <a name="export-a-users-queries-from-the-past-100-days"></a>导出用户过去 100 天的查询

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetQueryTermsForUser '0#.w|domain\username', @FROMDATE 
```

#### <a name="export-a-users-favorite-queries"></a>导出用户收藏的查询

使用以下步骤，从 Search Admin DB 个人结果表中导出 @UserName 自 <DateTime> 以来执行的用户收藏的查询。

```sql
In [dbo].[Search_<ID>]:
CREATE PROCEDURE proc_MSS_GetPersonalFavoriteQueries 
( 
    @UserName nvarchar(256), 
    @SearchTime datetime 
) 
AS 
BEGIN 
    SET NOCOUNT ON; 
    SELECT max(queries.SearchTime) as SearchTime, 
           max(queries.querystring) as queryString, 
           max(url.url) as URL 
    FROM MSSQLogOwner owners WITH(NOLOCK) 
    JOIN MSSQLogPersonalResults results WITH(NOLOCK) on owners.OwnerId = results.OwnerId 
    JOIN MSSQLogUrl url WITH(NOLOCK) on results.ClickedUrlId = url.urlId 
    JOIN MSSQLogPersonalQueries queries WITH(NOLOCK) on results.OwnerId = queries.OwnerId 
    WHERE queries.SearchTime > @SearchTime 
        AND queries.UserName = @UserName 
        GROUP BY queries.QueryString,url.url 
END 
GO 
```

#### <a name="export-a-users-favorite-queries-from-the-past-100-days"></a>导出用户过去 100 天收藏的查询 

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetPersonalFavoriteQueries '0#.w|domain\username', @FROMDATE 
```

#### <a name="remove-references-to-user-names-that-are-more-than-x-days-old"></a>删除超过 X 天的用户名引用

使用以下步骤，从 Links Store 查询日志表中删除超过 @Days 的*所有*用户名引用。该过程仅删除时间倒退到 @LastCleanupTime 之前的引用。

```sql
In [dbo].[LinksStore_<ID>]:  
CREATE PROCEDURE proc_MSS_QLog_Cleanup_Users 
( 
    @LastCleanupTime datetime, 
    @Days int 
) 
AS 
BEGIN 
    DECLARE @TooOld datetime 
    SET @TooOld = DATEADD(day, -@Days, GETUTCDATE()) 
    DECLARE @FromLast datetime 
    SET @FromLast = DATEADD(day, -@Days, @LastCleanupTime) 
    BEGIN TRANSACTION 
         UPDATE MSSQLogPageImpressionQuery 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld 
    UPDATE MSSQLogO14PageClick 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld 
    COMMIT TRANSACTION 
END 
GO 
```

#### <a name="remove-references-to-a-specific-user-name-thats-more-than-x-days-old"></a>删除超过 X 天的特定用户名引用

使用以下步骤，从 Links Store 查询日志表中删除超过 @Days 的*特定*用户名引用。该过程仅删除时间倒退到 @LastCleanupTime 之前的引用。

```sql
In [dbo].[LinksStore_<ID>]:
CREATE PROCEDURE proc_MSS_QLog_Cleanup_Users 
( 
    @UserName nvarchar(256),
    @LastCleanupTime datetime, 
    @Days int 
) 
AS 
BEGIN 
    DECLARE @TooOld datetime 
    SET @TooOld = DATEADD(day, -@Days, GETUTCDATE()) 
    DECLARE @FromLast datetime 
    SET @FromLast = DATEADD(day, -@Days, @LastCleanupTime) 
    BEGIN TRANSACTION 
         UPDATE MSSQLogPageImpressionQuery 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld AND userName = @UserName
    UPDATE MSSQLogO14PageClick 
    SET userName = 'NA' 
    WHERE @FromLast <= searchTime AND searchTime < @TooOld AND userName = @UserName
    COMMIT TRANSACTION 
END 
GO 
```

#### <a name="remove-references-to-all-user-names-in-the-query-history-from-a-date-and-up-to-the-past-30-days"></a>从查询历史记录中删除自某个日期起到过去 30 天内的所有用户名引用

```sql
EXECUTE proc_MSS_QLog_Cleanup_Users '1-1-2017', 30 
```

### <a name="delete-usage-records"></a>删除使用情况记录

SharePoint Server 2013 和 SharePoint Server 2016 自动在 3 年后删除使用情况记录。可使用以下步骤手动删除此类记录：

删除与已删除文档相关联的所有使用情况记录： 

1.  确保已安装最新 SharePoint 更新。 

2.  启动 SharePoint 命令行管理程序。

3.  停止并清除“使用情况分析”分析： 

    ```powershell
    $tj = Get-SPTimerJob -Type Microsoft.Office.Server.Search.Analytics.UsageAnalyticsJobDefinition 
    $tj.StopAnalysis() 
    $tj.ClearAnalysis() 
    ```

4.  等待分析再次启动（可能最多需要 24 小时）。 

5.  下一次运行分析时，它会转储分析报告数据库中的所有记录。对于包含许多条目的大型数据库，这一完整转储可能需要一段时间。

6.  等待 10 天。分析每日运行，并且与已删除文档相关联的记录将在运行 10 次后删除。如果需要删除许多记录，此运行所花费的时间可能会比平时长。 

### <a name="personal-information-and-search-in-sharepoint-server-2010"></a>SharePoint Server 2010 中的个人信息和搜索

#### <a name="fast-search-server-2010-for-sharepoint"></a>FAST Search Server 2010 for SharePoint 

除了存储索引中的文件，FAST Search Server 2010 加载项还以 FixML 中间格式存储文件。FixML 文件定期在每晚 3 点到 5 点之间压缩。压缩可自动从 FiXML 文件中删除已删除的文件。若要确保及时删除属于已删除用户或文档的信息，请确保始终启用压缩。

### <a name="hybrid-search"></a>混合搜索 

混合搜索解决方案的建议操作与 SharePoint Server 或 SharePoint Online 中的搜索相同。存在两种混合搜索解决方案：

**云混合搜索解决方案 -** 借助 SharePoint 的云混合搜索解决方案，你可以将所有爬网内容（包括本地内容）索引到 Office 365 中的搜索索引中。当用户在 Office 365 中查询你的搜索索引时，他们可以同时获取本地和 Office 365 内容中的搜索结果。当从 SharePoint Server 环境中删除文档时，他们也会从 Office 365 的搜索索引中删除。请参阅[深入了解云混合搜索解决方案](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint)和[搜索组件和数据库在云混合搜索中的交互方式](https://docs.microsoft.com/sharepoint/hybrid/plan-cloud-hybrid-search-for-sharepoint)，更好地了解 GDPR 如何影响混合环境。

**混合联合搜索解决方案 -** 借助混合联合搜索解决方案，你既可以在 SharePoint Server 中使用索引，也可以在 Office 365 中使用索引。SharePoint Server 和 SharePoint Online Search 服务都可以查询其他环境中的搜索索引并返回联合结果。当用户从搜索中心搜索时，搜索结果将来自 SharePoint Server 中的搜索索引和 Office 365 中的搜索索引。请参阅[深入了解混合联合搜索解决方案](https://docs.microsoft.com/sharepoint/hybrid/learn-about-hybrid-federated-search-for-sharepoint)，以更好地了解 GDPR 如何影响混合环境。

## <a name="on-prem-to-cloud-migrations"></a>本地到云的迁移

将数据从 SharePoint Server 迁移到 SharePoint Online 时，一段时间内，重复数据可能同时存在于这两个位置。如有需要删除正在迁移中的数据，建议首先完成迁移，然后从这两个位置删除该数据。可从任一位置查询要导出的数据。

## <a name="user-profile-data"></a>用户配置文件数据

User Profile Service 支持从各种外部源导入配置文件数据。应在掌握此类用户配置文件数据的系统中处理数据的查询和更新。如果对外部系统进行更新，请务必在 SharePoint Server 中再次同步用户配置文件。

按照以下基本步骤操作，从用户的 SharePoint Server 用户配置文件中删除其个人信息。

1.  从馈送到 SharePoint Server 用户配置文件的任何外部系统中删除用户信息。如果要使用目录同步，必须从本地 Active Directory 环境中删除用户。

2.  在 SharePoint Server 上运行[配置文件同步](https://docs.microsoft.com/sharepoint/administration/start-profile-synchronization-manually)。

3.  从 SharePoint Server 中删除配置文件。该操作完成后，SharePoint Server 将在 30 天内从用户配置文件数据库中彻底删除该配置文件。用户配置文件页和个人网站将被删除。

删除用户配置文件后，该用户访问过的网站集中可能仍记录有有限的一些信息（如用户 ID）。如果限制从给定网站集中删除此数据，可使用 CSOM 完成。示例脚本如下所示：

```powershell
$username = "<admin@company.sharepoint.com>"
$password = "password"
$url = "<https://site.sharepoint.com>"
$securePassword = ConvertTo-SecureString $Password -AsPlainText -Force

# the path here may need to change if you used e.g. C:Lib.
Add-Type -Path "c:\Program Files\Common Files\microsoft shared\Web Server Extensions\16ISAPIMicrosoft.SharePoint.Client.dll"
Add-Type -Path "c:\Program Files\Common Files\microsoft shared\Web Server Extensions\16ISAPIMicrosoft.SharePoint.Client.Runtime.dll"

# connect/authenticate to SharePoint Online and get ClientContext object.
$clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($url)
$credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($username, $securePassword)
$clientContext.Credentials = $credentials
if (!$clientContext.ServerObjectIsNull.Value)
{
    Write-Host "Connected to SharePoint Online site: '$Url'" -ForegroundColor Green
}

# Get user
$user = $clientContext.Web.SiteUsers.GetByLoginName("i:0#.f|membership|user@company.sharepoint.com")

# Redact user
$user.Email = "Redacted"
$user.Title = "Redacted"
$user.Update()
$clientContext.Load($user)
$clientContext.ExecuteQuery()

# Get users
$users = $clientContext.Web.SiteUsers

# Remove user from site
$users.RemoveById($user.Id)
$clientContext.Load($users)
$clientContext.ExecuteQuery()
```