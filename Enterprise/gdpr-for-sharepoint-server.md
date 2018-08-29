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
ms.openlocfilehash: 392b83b080ea111a5be070e9b9383caefe05d0be
ms.sourcegitcommit: 2ffe998e58ce1466366d697d99f0dd3e85b0605c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "23240607"
---
# <a name="gdpr-for-sharepoint-server"></a><span data-ttu-id="39a2e-103">适用于 SharePoint Server 的 GDPR</span><span class="sxs-lookup"><span data-stu-id="39a2e-103">GDPR for SharePoint Server</span></span>

<span data-ttu-id="39a2e-104">作为保护个人信息的一部分，建议进行以下操作：</span><span class="sxs-lookup"><span data-stu-id="39a2e-104">As part of safeguarding personal information, we recommend the following:</span></span>

-   <span data-ttu-id="39a2e-105">使用 Azure 信息保护对数据进行分类。</span><span class="sxs-lookup"><span data-stu-id="39a2e-105">Classify your data, using Azure Information Protection.</span></span>

-   <span data-ttu-id="39a2e-p101">在最低特权配置中运行 SharePoint Server。如需详细信息，请参阅[在 SharePoint Server 中规划最低权限管理](https://docs.microsoft.com/SharePoint/security-for-sharepoint-server/plan-for-least-privileged-administration)和 [SharePoint Server 的安全性](https://docs.microsoft.com/zh-CN/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server)。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p101">Run SharePoint Server in a least-privileged configuration. See [Plan for least-privileged administration in SharePoint Server](https://docs.microsoft.com/SharePoint/security-for-sharepoint-server/plan-for-least-privileged-administration) and [Security for SharePoint Server](https://docs.microsoft.com/zh-CN/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server) for more information.</span></span>

-   <span data-ttu-id="39a2e-108">[在服务器上启用 BitLocker 加密](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server)。</span><span class="sxs-lookup"><span data-stu-id="39a2e-108">[Enable BitLocker encryption on your servers](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server).</span></span>

## <a name="user-generated-content"></a><span data-ttu-id="39a2e-109">用户生成的内容</span><span class="sxs-lookup"><span data-stu-id="39a2e-109">User Generated content</span></span>

<span data-ttu-id="39a2e-110">对于 SharePoint Server 站点和库中包含的用户生成的内容，建议使用以下基本方法：</span><span class="sxs-lookup"><span data-stu-id="39a2e-110">The basic recommended approach for user generated content contained in SharePoint Server sites and libraries is:</span></span>

-   <span data-ttu-id="39a2e-111">使用 Azure 信息保护来标记敏感数据。</span><span class="sxs-lookup"><span data-stu-id="39a2e-111">Use Azure Information Protection to label sensitive data.</span></span>

-   <span data-ttu-id="39a2e-112">使用 [SharePoint Server 搜索](https://docs.microsoft.com/SharePoint/search/search)和[电子数据展示](https://docs.microsoft.com/SharePoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server)，检索敏感数据。</span><span class="sxs-lookup"><span data-stu-id="39a2e-112">Use [SharePoint Server search](https://docs.microsoft.com/SharePoint/search/search) and [eDiscovery](https://docs.microsoft.com/SharePoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server) to retrieve sensitive data.</span></span>

<span data-ttu-id="39a2e-113">对于文件共享和 SharePoint 站点和库，推荐的方法包括下列步骤：</span><span class="sxs-lookup"><span data-stu-id="39a2e-113">The recommended approach for files shares and SharePoint sites and libraries includes these steps:</span></span>

1.  <span data-ttu-id="39a2e-114">**安装并配置 Azure 信息保护扫描程序。**</span><span class="sxs-lookup"><span data-stu-id="39a2e-114">**Install and configure Azure Information Protection scanner.**</span></span>

    -   <span data-ttu-id="39a2e-115">决定要使用的敏感数据类型。</span><span class="sxs-lookup"><span data-stu-id="39a2e-115">Decide which sensitive data types to use.</span></span>

    -   <span data-ttu-id="39a2e-116">指定要使用的 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="39a2e-116">Specify which SharePoint sites to use.</span></span>

2.  <span data-ttu-id="39a2e-117">**完成发现周期。**</span><span class="sxs-lookup"><span data-stu-id="39a2e-117">**Complete a discovery cycle.**</span></span>

    -   <span data-ttu-id="39a2e-118">以发现模式运行扫描程序并验证查找结果。</span><span class="sxs-lookup"><span data-stu-id="39a2e-118">Run the scanner in discovery mode and validate the findings.</span></span>

    -   <span data-ttu-id="39a2e-119">如果需要，优化条件和敏感信息类型。</span><span class="sxs-lookup"><span data-stu-id="39a2e-119">If needed, optimize the conditions and sensitive information types.</span></span>

    -   <span data-ttu-id="39a2e-120">评估自动应用标签的预期影响。</span><span class="sxs-lookup"><span data-stu-id="39a2e-120">Assess the expected impact of automatically applying labels.</span></span>

3.  <span data-ttu-id="39a2e-121">**运行 Azure 信息保护扫描程序以便标记合格文档**。</span><span class="sxs-lookup"><span data-stu-id="39a2e-121">**Run the Azure Information Protection scanner to apply labels to qualifying documents**.</span></span>

4.  <span data-ttu-id="39a2e-122">**对于保护：**</span><span class="sxs-lookup"><span data-stu-id="39a2e-122">**For protection:**</span></span>

    <span data-ttu-id="39a2e-p102">a. 配置 Exchange 数据丢失防护规则以保护具有所需标签的文档。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p102">a.  Configure Exchange data loss prevention rules to protect documents with the desired label.</span></span>

    <span data-ttu-id="39a2e-p103">b. 务必要使用权限来限制可访问文件的人员。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p103">b.  Be sure permissions to limit who can access files.</span></span>

    <span data-ttu-id="39a2e-p104">c. 对于 SharePoint，使用 IRM 保护对库进行保护。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p104">c.  For SharePoint, use IRM-protection for libraries.</span></span>

5.  <span data-ttu-id="39a2e-129">**要进行监控，请使用 SIEM 工具集成 Windows Server 日志。**</span><span class="sxs-lookup"><span data-stu-id="39a2e-129">**For monitoring, integrate Windows Server logs with a SIEM tool.**</span></span>

    <span data-ttu-id="39a2e-p105">a. 若要查找数据主体请求，请使用搜索中心或电子数据展示。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p105">a.  To find personal data for data subject requests, use Search Center or eDiscovery.</span></span>

<span data-ttu-id="39a2e-p106">如果对敏感数据应用标签，请务必使用未配置保护的标签。保护包括可阻止服务检测文件中的敏感数据的加密。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p106">When applying labels to sensitive data, be sure to use a label that is not configured with protection. Protection includes encryption which prevents services from detecting sensitive data in the files.</span></span>

<span data-ttu-id="39a2e-134">有关使用 Azure 信息保护扫描程序查找和标记个人数据的详细信息，请参阅 [Microsoft GDPR 数据发现工具包](http://aka.ms/gdprpartners) (http://aka.ms/gdprpartners))。</span><span class="sxs-lookup"><span data-stu-id="39a2e-134">For more information on using Azure Information Protection scanner to find and label personal data, see the [Microsoft GDPR Data Discovery Toolkit](http://aka.ms/gdprpartners) (http://aka.ms/gdprpartners).</span></span>

<span data-ttu-id="39a2e-p107">有关配置条件扫描程序和使用 Office 365 数据丢失防护 (DLP) 敏感信息类型的信息，请参阅[如何为 Azure 信息保护的自动推荐分类配置条件](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-classification)。请注意，新的 Office 365 敏感信息类型不会立即可供扫描程序使用，并且自定义敏感信息类型不能与扫描程序一起使用。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p107">For information on configuring the scanner for conditions and using the Office 365 data loss prevention (DLP) sensitive information types, see [How to configure conditions for automatic and recommended classification for Azure Information Protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-classification). Note that new Office 365 sensitive information types will not be immediately available to use with the scanner and custom sensitive information types cannot be used with the scanner.</span></span>

## <a name="removing-personal-information-from-office-files"></a><span data-ttu-id="39a2e-137">从 Office 文件中删除个人信息</span><span class="sxs-lookup"><span data-stu-id="39a2e-137">Removing personal information from Office files</span></span>

<span data-ttu-id="39a2e-p108">必须手动从存储于 SharePoint 文档库中的 Office 文件中删除个人信息（例如 Word 文档中的元数据和批注）。请按照以下步骤操作：</span><span class="sxs-lookup"><span data-stu-id="39a2e-p108">Removing personal information (such as metadata or comments in a Word document) from Office files that are stored in a SharePoint document library must be done manually. Follow these steps:</span></span>

1.  <span data-ttu-id="39a2e-140">将文档副本从 SharePoint Server 中下载到本地磁盘。</span><span class="sxs-lookup"><span data-stu-id="39a2e-140">Download a copy of the document from SharePoint Server to your local disk.</span></span>

2.  <span data-ttu-id="39a2e-141">从 SharePoint 文档库中删除文档。</span><span class="sxs-lookup"><span data-stu-id="39a2e-141">Delete the document from the SharePoint document library.</span></span>

3.  <span data-ttu-id="39a2e-142">按照[通过检查文档删除隐藏数据和个人信息](https://support.office.com/article/356B7B5D-77AF-44FE-A07F-9AA4D085966F)中的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="39a2e-142">Follow the steps in [Remove hidden data and personal information by inspecting documents](https://support.office.com/article/356B7B5D-77AF-44FE-A07F-9AA4D085966F).</span></span>

4.  <span data-ttu-id="39a2e-143">将文档上传到 SharePoint 文档库。</span><span class="sxs-lookup"><span data-stu-id="39a2e-143">Upload the document back to the SharePoint document library.</span></span>

## <a name="telemetry-and-log-files"></a><span data-ttu-id="39a2e-144">遥测和日志文件</span><span class="sxs-lookup"><span data-stu-id="39a2e-144">Telemetry and log files</span></span>

### <a name="uls-logs"></a><span data-ttu-id="39a2e-145">ULS 日志</span><span class="sxs-lookup"><span data-stu-id="39a2e-145">ULS Logs</span></span>

<span data-ttu-id="39a2e-p109">SharePoint Server 中的统一日志记录服务 (ULS) 和使用情况日志记录可跟踪各种系统功能并包含用户信息。ULS 日志和使用情况日志为文本文件，可使用各种搜索工具进行搜索。[Merge-SPLogFile PowerShell cmdlet](https://docs.microsoft.com/zh-CN/powershell/module/sharepoint-server/merge-splogfile) 提供了一种从场中多台服务器上的 ULS 日志中返回记录的方式。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p109">Unified Logging Service (ULS) and Usage logging in SharePoint Server track a variety of system functions and can contain user information. ULS logs and usage logs are text files and can be searched using a variety of searching tools. The [Merge-SPLogFile PowerShell cmdlet](https://docs.microsoft.com/zh-CN/powershell/module/sharepoint-server/merge-splogfile) provides a way to return records from the ULS logs on multiple servers in a farm.</span></span>

<span data-ttu-id="39a2e-p110">考虑将日志保留策略设置为业务目的所需的最小值。有关如何在 SharePoint Server 中配置日志记录的信息，请参阅[在 SharePoint Server 中配置诊断日志记录](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging)。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p110">Consider setting log retention policies to the minimum value needed for your business purposes. For information about configuring logging in SharePoint Server, see [Configure diagnostic logging in SharePoint Server](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging).</span></span>

<span data-ttu-id="39a2e-151">请注意，部分系统事件也记录在 Windows 事件日志中。</span><span class="sxs-lookup"><span data-stu-id="39a2e-151">Note that some system events are also logged to the Windows Event Log.</span></span>

### <a name="usage-database"></a><span data-ttu-id="39a2e-152">使用情况数据库</span><span class="sxs-lookup"><span data-stu-id="39a2e-152">Usage Database</span></span>

<span data-ttu-id="39a2e-p111">SharePoint Server 使用情况数据库（默认名称为 WSS_Logging）包含 ULS 日志中所找到信息的子集。此数据库中的最大数据保留时间为 30 天。建议配置为业务需求允许的最短持续时间。有关详细信息，请参阅[在 SharePoint Server 中配置诊断日志记录](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging)。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p111">The SharePoint Server Usage database (default name WSS_Logging) contains a subset of the information found in the ULS logs. The maximum retention of data in this database is 30 days. We recommend that you configure it for the shortest duration allowable by your business needs. For more information, see [Configure diagnostic logging in SharePoint Server](https://docs.microsoft.com/SharePoint/administration/configure-diagnostic-logging).</span></span>

## <a name="personal-information-and-search"></a><span data-ttu-id="39a2e-157">个人信息和搜索</span><span class="sxs-lookup"><span data-stu-id="39a2e-157">Personal information and search</span></span>

<span data-ttu-id="39a2e-158">搜索查询历史记录和使用情况记录包含对用户名的引用。</span><span class="sxs-lookup"><span data-stu-id="39a2e-158">The search query history and usage records contain references to user names.</span></span>

### <a name="query-history-and-favorite-queries"></a><span data-ttu-id="39a2e-159">查询历史记录和收藏的查询</span><span class="sxs-lookup"><span data-stu-id="39a2e-159">Query history and favorite queries</span></span>

<span data-ttu-id="39a2e-p112">在 SharePoint Server 中，查询历史记录和收藏的查询在 365 天后自动到期。如果用户离开你的组织，可使用以下步骤从查询历史记录中删除对用户名的引用。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p112">In SharePoint Server 2013 and SharePoint Server 2016, query histories and ‘favorite’ queries automatically expire after 365 days. If a user leaves your organization, it is possible to remove references to a user's name from the query history using the steps below..</span></span>

<span data-ttu-id="39a2e-162">下列 SQL 查询适用于 SharePoint Server，并且可以：</span><span class="sxs-lookup"><span data-stu-id="39a2e-162">The following SQL queries apply to SharePoint 2013 and SharePoint 2016 and make it possible to:</span></span>

-   <span data-ttu-id="39a2e-163">导出用户的查询历史记录或收藏的查询</span><span class="sxs-lookup"><span data-stu-id="39a2e-163">Export a user’s query history or favorite queries</span></span>

-   <span data-ttu-id="39a2e-164">删除查询历史记录中对用户名的引用</span><span class="sxs-lookup"><span data-stu-id="39a2e-164">Remove references to user names in the query history</span></span>

#### <a name="export-a-users-queries-since-a-specific-date"></a><span data-ttu-id="39a2e-165">导出自特定日期以来的用户查询</span><span class="sxs-lookup"><span data-stu-id="39a2e-165">Export a user’s queries since a specific date</span></span> 

<span data-ttu-id="39a2e-166">使用以下步骤，从 Link Store 查询日志表中导出 @UserName 自 @StartTime 以来执行的查询。</span><span class="sxs-lookup"><span data-stu-id="39a2e-166">Use the following procedure to export queries from the Link Store query log tables, performed by @UserName since @StartTime.</span></span>

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

#### <a name="export-a-users-queries-from-the-past-100-days"></a><span data-ttu-id="39a2e-167">导出用户过去 100 天的查询</span><span class="sxs-lookup"><span data-stu-id="39a2e-167">Export a user’s queries from the past 100 days</span></span>

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetQueryTermsForUser '0#.w|domain\username', @FROMDATE 
```

#### <a name="export-a-users-favorite-queries"></a><span data-ttu-id="39a2e-168">导出用户收藏的查询</span><span class="sxs-lookup"><span data-stu-id="39a2e-168">Export a user’s favorite queries</span></span>

<span data-ttu-id="39a2e-169">使用以下步骤，从 Search Admin DB 个人结果表中导出 @UserName 自 <DateTime> 以来执行的用户收藏的查询。</span><span class="sxs-lookup"><span data-stu-id="39a2e-169">Use the following procedure to export a user's favorite queries from the Search Admin DB personal result tables, performed by @UserName, since <DateTime>.</span></span>

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

#### <a name="export-a-users-favorite-queries-from-the-past-100-days"></a><span data-ttu-id="39a2e-170">导出用户过去 100 天收藏的查询</span><span class="sxs-lookup"><span data-stu-id="39a2e-170">Export a user’s favorite queries from the past 100 days</span></span> 

```sql
DECLARE @FROMDATE datetime 
SET @FROMDATE = DATEADD(day, -100, GETUTCDATE()) 
EXECUTE proc_MSS_GetPersonalFavoriteQueries '0#.w|domain\username', @FROMDATE 
```

#### <a name="remove-references-to-user-names-that-are-more-than-x-days-old"></a><span data-ttu-id="39a2e-171">删除超过 X 天的用户名引用</span><span class="sxs-lookup"><span data-stu-id="39a2e-171">Remove references to user names that are more than X days old</span></span>

<span data-ttu-id="39a2e-p113">使用以下步骤，从 Links Store 查询日志表中删除超过 @Days 的*所有*用户名引用。该过程仅删除时间倒退到 @LastCleanupTime 之前的引用。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p113">Use the following procedure to remove references to *all* user names that are more than @Days old, from the Links Store query log tables. The procedure only removes references backwards in time until it reaches the @LastCleanupTime.</span></span>

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

#### <a name="remove-references-to-a-specific-user-name-thats-more-than-x-days-old"></a><span data-ttu-id="39a2e-174">删除超过 X 天的特定用户名引用</span><span class="sxs-lookup"><span data-stu-id="39a2e-174">Remove references to a specific user name that’s more than X days old</span></span>

<span data-ttu-id="39a2e-p114">使用以下步骤，从 Links Store 查询日志表中删除超过 @Days 的*特定*用户名引用。该过程仅删除时间倒退到 @LastCleanupTime 之前的引用。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p114">Use the following procedure to remove references to a *specific* user name from the Links Store query log tables, where the references are more than @Days old. The procedure only removes references backwards in time until it reaches the @LastCleanupTime.</span></span>

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

#### <a name="remove-references-to-all-user-names-in-the-query-history-from-a-date-and-up-to-the-past-30-days"></a><span data-ttu-id="39a2e-177">从查询历史记录中删除自某个日期起到过去 30 天内的所有用户名引用</span><span class="sxs-lookup"><span data-stu-id="39a2e-177">Remove references to all user names in the query history from a date and up to the past 30 days</span></span>

```sql
EXECUTE proc_MSS_QLog_Cleanup_Users '1-1-2017', 30 
```

### <a name="delete-usage-records"></a><span data-ttu-id="39a2e-178">删除使用情况记录</span><span class="sxs-lookup"><span data-stu-id="39a2e-178">Delete usage records</span></span>

<span data-ttu-id="39a2e-p115">SharePoint Server 自动在 3 年后删除使用情况记录。可使用以下步骤手动删除此类记录：</span><span class="sxs-lookup"><span data-stu-id="39a2e-p115">SharePoint Server 2013 and SharePoint Server 2016 automatically deletes usage records after 3 years. You can manually delete such records using the procedure below:</span></span>

<span data-ttu-id="39a2e-181">删除与已删除文档相关联的所有使用情况记录：</span><span class="sxs-lookup"><span data-stu-id="39a2e-181">To delete all usage records associated with deleted documents:</span></span> 

1.  <span data-ttu-id="39a2e-182">确保已安装最新 SharePoint 更新。</span><span class="sxs-lookup"><span data-stu-id="39a2e-182">Ensure that you have the latest SharePoint update installed.</span></span> 

2.  <span data-ttu-id="39a2e-183">启动 SharePoint 命令行管理程序。</span><span class="sxs-lookup"><span data-stu-id="39a2e-183">Start a SharePoint Management shell.</span></span>

3.  <span data-ttu-id="39a2e-184">停止并清除“使用情况分析”分析：</span><span class="sxs-lookup"><span data-stu-id="39a2e-184">Stop and Clear the Usage Analytics analysis:</span></span> 

    ```powershell
    $tj = Get-SPTimerJob -Type Microsoft.Office.Server.Search.Analytics.UsageAnalyticsJobDefinition 
    $tj.StopAnalysis() 
    $tj.ClearAnalysis() 
    ```

4.  <span data-ttu-id="39a2e-185">等待分析再次启动（可能最多需要 24 小时）。</span><span class="sxs-lookup"><span data-stu-id="39a2e-185">Wait for the analysis to start again (might take up to 24 hours).</span></span> 

5.  <span data-ttu-id="39a2e-p116">下一次运行分析时，它会转储分析报告数据库中的所有记录。对于包含许多条目的大型数据库，这一完整转储可能需要一段时间。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p116">On the next run of the analysis, it will dump all records from the Analytics Reporting database. This full dump may take a while for a large database with many entries.</span></span>

6.  <span data-ttu-id="39a2e-p117">等待 10 天。分析每日运行，并且与已删除文档相关联的记录将在运行 10 次后删除。如果需要删除许多记录，此运行所花费的时间可能会比平时长。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p117">Wait for 10 days. The analysis runs daily, and records associated with deleted documents will be removed after the 10^th^ run. This run may take longer than normal if many records need to be deleted.</span></span> 

### <a name="personal-information-and-search-in-sharepoint-server-2010"></a><span data-ttu-id="39a2e-191">SharePoint Server 2010 中的个人信息和搜索</span><span class="sxs-lookup"><span data-stu-id="39a2e-191">Personal information and search in SharePoint Server 2010</span></span>

#### <a name="fast-search-server-2010-for-sharepoint"></a><span data-ttu-id="39a2e-192">FAST Search Server 2010 for SharePoint</span><span class="sxs-lookup"><span data-stu-id="39a2e-192">FAST Search Server 2010 for SharePoint</span></span> 

<span data-ttu-id="39a2e-p118">除了存储索引中的文件，FAST Search Server 2010 加载项还以 FixML 中间格式存储文件。FixML 文件定期在每晚 3 点到 5 点之间压缩。压缩可自动从 FiXML 文件中删除已删除的文件。若要确保及时删除属于已删除用户或文档的信息，请确保始终启用压缩。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p118">In addition to storing files in the index, the FAST Search Server 2010 Add-On also stores files in an intermediate format called FixML. FiXML files are compacted regularly, by default between 3 am and 5 am every night. Compaction removes deleted files from the FiXML files automatically. To ensure timely removal of information belonging to deleted users or documents, ensure that compaction is always enabled.</span></span>

### <a name="hybrid-search"></a><span data-ttu-id="39a2e-197">混合搜索</span><span class="sxs-lookup"><span data-stu-id="39a2e-197">Hybrid Search</span></span> 

<span data-ttu-id="39a2e-p119">混合搜索解决方案的建议操作与 SharePoint Server 或 SharePoint Online 中的搜索相同。存在两种混合搜索解决方案：</span><span class="sxs-lookup"><span data-stu-id="39a2e-p119">The recommended actions for hybrid search solutions are the same as for search in SharePoint Server or SharePoint Online. There are two hybrid search solutions:</span></span>

<span data-ttu-id="39a2e-p120">**云混合搜索解决方案 -** 借助 SharePoint 的云混合搜索解决方案，你可以将所有爬网内容（包括本地内容）索引到 Office 365 中的搜索索引中。当用户在 Office 365 中查询你的搜索索引时，他们可以同时获取本地和 Office 365 内容中的搜索结果。当从 SharePoint Server 环境中删除文档时，他们也会从 Office 365 的搜索索引中删除。请参阅[深入了解云混合搜索解决方案](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint)和[搜索组件和数据库在云混合搜索中的交互方式](https://docs.microsoft.com/sharepoint/hybrid/plan-cloud-hybrid-search-for-sharepoint)，更好地了解 GDPR 如何影响混合环境。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p120">**The cloud hybrid search solution -** With the cloud hybrid search solution for SharePoint, you index all your crawled content, including on-premises content, in your search index in Office 365. When users query your search index in Office 365, they get search results from both on-premises and Office 365 content. When documents are deleted from the SharePoint Server environment, they are also deleted from the search index in Office 365. [Read more about the cloud hybrid search solution](https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint) and [how search components and databases interact in cloud hybrid search](https://docs.microsoft.com/sharepoint/hybrid/plan-cloud-hybrid-search-for-sharepoint) to understand better how GDPR affects the hybrid environment.</span></span>

<span data-ttu-id="39a2e-p121">**混合联合搜索解决方案 -** 借助混合联合搜索解决方案，你既可以在 SharePoint Server 中使用索引，也可以在 Office 365 中使用索引。SharePoint Server 和 SharePoint Online Search 服务都可以查询其他环境中的搜索索引并返回联合结果。当用户从搜索中心搜索时，搜索结果将来自 SharePoint Server 中的搜索索引和 Office 365 中的搜索索引。请参阅[深入了解混合联合搜索解决方案](https://docs.microsoft.com/sharepoint/hybrid/learn-about-hybrid-federated-search-for-sharepoint)，以更好地了解 GDPR 如何影响混合环境。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p121">**The hybrid federated search solution -** With the hybrid federated search solution, you use both your index in SharePoint Server and your index in Office 365. Both SharePoint Server and SharePoint Online Search services can query the search index in the other environment and return federated results. When users search from a Search Center, the search results come from both your search index in SharePoint Server and your search index in Office 365. [Read more about the hybrid federated search solution](https://docs.microsoft.com/sharepoint/hybrid/learn-about-hybrid-federated-search-for-sharepoint) to understand better how GDPR affects the hybrid environment.</span></span>

## <a name="on-prem-to-cloud-migrations"></a><span data-ttu-id="39a2e-208">本地到云的迁移</span><span class="sxs-lookup"><span data-stu-id="39a2e-208">On Prem to Cloud Migrations</span></span>

<span data-ttu-id="39a2e-p122">将数据从 SharePoint Server 迁移到 SharePoint Online 时，一段时间内，重复数据可能同时存在于这两个位置。如有需要删除正在迁移中的数据，建议首先完成迁移，然后从这两个位置删除该数据。可从任一位置查询要导出的数据。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p122">While migrating data from SharePoint Server to SharePoint Online, duplicate data may exist in both locations for a time. If you have data that you need to delete that is in mid-migration, we recommend that you complete the migration first, and then delete the data from both locations. You can query data for export from either location.</span></span>

## <a name="user-profile-data"></a><span data-ttu-id="39a2e-212">用户配置文件数据</span><span class="sxs-lookup"><span data-stu-id="39a2e-212">User Profile data</span></span>

<span data-ttu-id="39a2e-p123">User Profile Service 支持从各种外部源导入配置文件数据。应在掌握此类用户配置文件数据的系统中处理数据的查询和更新。如果对外部系统进行更新，请务必在 SharePoint Server 中再次同步用户配置文件。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p123">The User Profile Service allows for import of profile data from a variety of external sources. Queries for and update of such user profile data should be handled in the systems in which the data is mastered. If you make updates to the external system, be sure to synchronize the user profiles in SharePoint Server again.</span></span>

<span data-ttu-id="39a2e-216">按照以下基本步骤操作，从用户的 SharePoint Server 用户配置文件中删除其个人信息。</span><span class="sxs-lookup"><span data-stu-id="39a2e-216">Follow these basic steps to remove a user’s personal information from their SharePoint Server user profile:</span></span>

1.  <span data-ttu-id="39a2e-p124">从馈送到 SharePoint Server 用户配置文件的任何外部系统中删除用户信息。如果要使用目录同步，必须从本地 Active Directory 环境中删除用户。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p124">Remove the user information from any external systems that feed into the SharePoint Server user profile. If you are using directory synchronization, the user must be removed from the on-premises Active Directory environment.</span></span>

2.  <span data-ttu-id="39a2e-219">在 SharePoint Server 上运行[配置文件同步](https://docs.microsoft.com/sharepoint/administration/start-profile-synchronization-manually)。</span><span class="sxs-lookup"><span data-stu-id="39a2e-219">Run a [profile synchronization](https://docs.microsoft.com/sharepoint/administration/start-profile-synchronization-manually) on SharePoint Server.</span></span>

3.  <span data-ttu-id="39a2e-p125">从 SharePoint Server 中删除配置文件。该操作完成后，SharePoint Server 将在 30 天内从用户配置文件数据库中彻底删除该配置文件。用户配置文件页和个人网站将被删除。</span><span class="sxs-lookup"><span data-stu-id="39a2e-p125">Delete the profile from SharePoint Server. Once this is done, SharePoint Server will fully remove the profile from the User Profile Database in 30 days. The user’s profile page and personal site will be deleted.</span></span>

<span data-ttu-id="39a2e-p126">删除用户配置文件后，该用户访问过的网站集中可能仍记录有有限的一些信息（如用户 ID）。如果限制从给定网站集中删除此数据，可使用 CSOM 完成。示例脚本如下所示：</span><span class="sxs-lookup"><span data-stu-id="39a2e-p126">After deleting a user’s profile, some limited information (such as user ID) may still be recorded in site collections that the user has visited. If you choose to delete this data from a given site collection, this can be done using CSOM. A sample script is provided below:</span></span>

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