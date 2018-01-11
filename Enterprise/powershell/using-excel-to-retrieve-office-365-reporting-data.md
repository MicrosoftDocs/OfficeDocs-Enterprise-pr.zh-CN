---
title: "使用 Excel 检索 Office 365 报告数据"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 510d5528-ac00-4f54-9d38-75fa043d0a06
description: "摘要：使用 Microsoft Excel 中的 oData 功能检索 Office 365 部署的详细报告信息。"
ms.openlocfilehash: a4245029c337450f5f5ac3655e0b60a301ea80ec
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2018
---
# <a name="using-excel-to-retrieve-office-365-reporting-data"></a>使用 Excel 检索 Office 365 报告数据

 **摘要：**使用 Microsoft Excel 中的 oData 功能检索 Office 365 部署的详细报表信息。
  
报告功能是系统管理的一个关键部分。Office 365 管理中心包含大量预定义的报告，你可以通过左侧导航的" **报告**"部分访问它们。有使用情况报告以及安全性和合规性报告。
  
您可用的报告取决于您使用的 Office 365 版本以及您启用的 Office 365 服务。有关详细信息，请参阅[报告]((https://technet.microsoft.com/zh-CN/library/office-365-reports.aspx))页。
  
预定义的管理中心报告是非常不错的资源。它们便于查看邮箱使用情况或用户在在线会议上花费的分钟数等事项。但是，在 Office 365 域的详细分析方面，报告确实有其局限性。
  
解决此局限性的一种方法是使用 Windows PowerShell 或其他开发语言访问 Office 365 报告服务并创建自定义报告；您可以通过自定义报告指定从 Office 365 报告服务返回的数据（及数据量）。通过编写自定义报告，您还可以指定数据排序和分组的方式，以及保存数据的方式（如果适用）；例如，您可以将数据保存为 XML 格式或在 Excel 中可轻松导入的逗号分隔值格式。 
  
此外，通过自定义脚本/应用程序，你可以访问 Office 365 管理中心内不提供的报告。例如，管理中心可以向你说明你拥有多少个过时（非活动）邮箱，但不会告诉你在过去 30 天内哪些邮箱没人访问。自定义的 PowerShell 脚本可以告诉你这些信息。总体来说，虽然必须编写简短而且相对简单的 Windows PowerShell 小脚本，但作为回报，灵活性却得到显著提高。
  
> [!VISUAL BASIC NOTE] 有关详细信息，请参阅 Office 365 报告服务的[主页](https://msdn.microsoft.com/en-us/library/office/jj984325%28v=office.15%29.aspx)。
  
为检索此数据，不必编写某种类型的代码。如果你的组织规模较大，并且需要限制返回的信息量和类型，那么这样做是值得的。但是，如果你的组织规模较小，且无需限制返回的信息量和类型，你可以考虑从 Excel 中打开 Office 365 报告。
  
但是，此处存在一些限制，主要限制是：你不能在数据返回之前筛选、分类、选择或以其他方式处理数据。你只能获取报告返回的默认数据集。在一些数据可能不够的情况下：例如，报告可能仅返回上月的数据，而不返回全年的数据。反之，在数据可能太多的一些情况下：你仅需要上月的数据，但可能返回全年的数据。
  
要直接从 Excel 中打开 Office 365 报告，请完成以下过程：
  
1. 首先在 Excel 中打开一个新工作表。在工作表中，依次单击" **数据** "、" **来自其他来源** "和" **来自 OData 数据馈送** "。将弹出" **数据连接向导** "对话框：
    
     ![数据连接向导中的“连接到数据源”对话框的示例。](images/o365_reporting_connect_data_feed.png)
  
2. 在" **连接到数据馈送** "页上，输入 **https://reports.office365.com/ecp/reportingwebservice/reporting.svc/** 作为数据馈送位置。请注意，你只能输入所示的基本 URL；不能添加任何 Select、Filter 或 Format 语句。如果你输入的是除基 URL 之外的其他信息，将不会返回任何数据；而只会看到下面的错误消息：
    
     ![添加 Select、Filter 或 Format 语句时的错误消息的示例。](images/o365_reporting_incorrect_data_feed.png)
  
3. 输入报告服务 URL 后，选择"登录凭据"下的"使用此用户名和密码"。在"用户名"框中，输入您的 Office 365 登录名（例如，admin@litwareinc.onmicrosoft.com）。在"密码"框中，输入您的 Office 365 登录密码，然后单击"下一步"。然后，Excel 将尝试使用提供的凭据连接到报告服务。
    
4. 经过身份验证后，将看到“选择表”****页。选择要查看的报表（例如，“MailTrafficTop”****），再单击“下一步”****：
    
     ![数据连接向导中的“选择表”页的示例。](images/o365_reporting_select_tables.png)
  
    > [!NOTE]
    > 可以选择多个报告；这会将多个表格/图表添加到你的 Excel 电子表格中。你甚至可以创建一个组合多个报告中的数据的表格/图表；但我们在本篇介绍性文章中不进行讨论。 
  
5. 单击"下一步"之后，将显示"保存数据连接文件并完成"页：
    
     ![数据连接向导中的“保存数据连接文件并完成”页的示例。](images/o365_reporting_odata_finish.png)
  
    你无需输入任何信息。要检索数据，只需单击" **完成** "。但是，值得注意的是，默认情况下，Excel 会保存有关你所进行的每个数据连接的信息，此数据存储在" **我的数据源** "文件夹中：
    
     ![“我的数据源”文件夹的“文件保存”对话框的示例。](images/o365_reporting_save_data_source.png)
  
    这就是对话框为何包含具有"友好名称"和"搜索关键字"之类标签的文本框的原因；这些选项使您可以自定义这些数据连接。通过这种方式，您最终不会获取如下所示的全部数据源：
    
  ```
  DataFeed_1_reports-office365-com ClientSoftwareBrowserDetail.odc
DataFeed_1_reports-office365-com MailTrafficTop.odc
DataFeed_1_reports-office365-com Multiple Tables.odc
DataFeed_2_reports-office365-com MailboxActivityWeekly.odc
DataFeed_2_reports-office365-com MailTrafficTop.odc
DataFeed_3_reports-office365-com ClientSoftwareBrowserDetail.odc
  ```

如果你选中" **在文件中保存密码** "复选框，你将能够重新使用这些数据源。例如，假设你将数据连接保存为" **客户端浏览器报告** "。下次你需要有关用于访问 Office 365 域的 Web 浏览器的信息时，无需完成数据连接向导的所有操作。而只需打开 Excel，单击" **数据** "，然后单击" **现有源** "。在" **现有连接** "对话框中，选择所需的数据连接，然后单击" **确定** "：
    
![在“现有连接”对话框中选择所需的数据连接的示例。](images/o365_reporting_select_connection.png)
  
在这种情况下，Excel 将为您进行连接并检索数据。
    
请注意，这些 .ODC 文件是纯文本 XML 文件。这些纯文本 XML 文件中包含了你的 Office 365 用户名和密码：
    
\<odc:ConnectionString>Data Source=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/;Namespaces to Include=*;Max Received Message Size=4398046511104;Integrated Security=Basic; **User ID=admin@litwareinc.onmicrosoft.com;Password=MYpassw0rd!**;Persist Security Info=false;Service Document Url=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/\</odc:ConnectionString>
    
如果你不希望将用户名和密码保存在纯文本文件中，则取消勾选标记为" **在文件中保存密码** "的框。但是，请注意，如果执行此操作，将无法重新使用这些数据连接。这是因为，如果没有用户名和密码，Office 365 将无法对你尝试登录服务进行身份验证。
    
6. 单击"保存数据连接文件并完成"页上的"完成"，将显示"导入数据"对话框：
    
     ![“导入数据”对话框的示例。](images/o365_reporting_import_data.png)
  
7. 选择视图选项（例如，“数据透视表”****），再单击“确定”****。如果一切顺利，数据将会导入，并显示在任意选定视图选项中：
    
     ![已成功导入到 Excel 工作表中的数据的示例。](images/o365_reporting_sample_spreadsheet.png)
  
如何处理这些数据完全由你决定。作为建议，你可以看一看[使用 OData 数据源创建 Excel Services 仪表板](https://technet.microsoft.com/en-us/library/jj873965%28v=office.15%29.aspx)。尽管该文章未使用 Office 365 报告服务，但提供了向新的仪表板添加筛选器和切片器等操作的一些有用技巧。
  
## <a name="see-also"></a>另请参阅

#### 

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
  
[使用 Windows PowerShell 在 Office 365 中创建报告](use-windows-powershell-to-create-reports-in-office-365.md)

