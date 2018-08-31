---
title: 安装并运行 Office 365 IdFix 工具
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: 如何安装和运行 Office 365 IdFix 工具以帮助清理您的 active directory 同步到 Office 365 之前。
ms.openlocfilehash: 642273c0171603d627a19273a78fe66662f4caaf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539553"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>安装并运行 Office 365 IdFix 工具

同步到 Office 365 之前，IdFix 标识错误例如重复项和在您的目录的格式问题。 
  
要成功完成此任务，您应该能够轻松处理用户、 组和 Active Directory 中的联系人对象。
  
如果您不能完成该任务中，有几个您可以执行其他操作。这些方法可能更方便，但也可能还需要更长时间，或具有其他缺点。它们是：
  
- **运行目录同步时没有运行 IdFix。** 您可以将您的目录同步时没有运行 IdFix 工具，但我们不建议这样。同步之前修复错误的时间少并通常提供到云中更平稳转换。 
- **聘请顾问。** 获得专家的帮助可以让您的用户正常工作并提高运行速度，使您的目录顺利实现同步。 
    
## <a name="what-you-need-to-run-idfix"></a>运行 IdFix 所需内容

最简单方式来获取 IdFix 和运行时将其安装在加入到域的计算机上。如果需要，但它并不需要，您可以在域控制器上运行它。
  
### <a name="idfix-hardware-requirements"></a>IdFix 硬件要求

您安装了 IdFix 的计算机需要满足以下硬件要求：
  
- 4 GB RAM（最低）
- 2 GB 的硬盘空间（最低）
    
### <a name="idfix-software-requirements"></a>IdFix 软件要求

其中安装 IdFix 需求到的计算机需要加入到想要将用户同步到 Office 365 的同一个 Active Directory 域。计算机还需要有.NET Framework 4.0 安装。 
  
如果您运行的 Windows Server 2008 或 Windows Server 2012，则可能已经安装.NET Framework。如果不需要，您可以[下载从下载中心下载.NET 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475)或使用 Windows Update。 
  
### <a name="idfix-permissions-requirements"></a>IdFix 权限要求

您用来运行 IdFix 的用户帐户需要具有对目录的读/写访问权限。
  
如果您不确定您的用户帐户满足这些要求，并且您不确定如何检查，如果仍然可以安装并继续运行 IdFix。如果您的用户帐户没有正确的权限，IdFix 将只会显示错误，当您尝试运行它。
  
## <a name="install-idfix"></a>安装 IdFix

要安装 IdFix，您可以下载并解压缩“IdFix.exe”****，如以下步骤所述： 
  
1. 登录到您要安装 IdFix 工具的计算机。
    
2. 转到 Microsoft 下载网站 for [IdFix 目录同步错误修复工具](https://go.microsoft.com/fwlink/?linkid=867219)。
    
3. 选择“下载”****。
    
4. 出现提示时，选择**运行**。
    
5. 在**WinZip 自动解压缩程序**对话框中**解压缩到文件夹**文本框中，键入或浏览到要安装 IdFix 工具的位置。默认情况下，IdFix 安装到 C:\Deployment 工具\. 
    
6. 选择**解压缩**。
    
## <a name="run-the-idfix-tool"></a>运行 IdFix 工具

安装了 IdFix 之后，运行该工具搜索目录中的问题：
  
1. 使用对目录具有读/写访问权限的帐户登录到您安装 IdFix 的计算机。
    
2. 在文件资源管理器中，转到您安装了 IdFix 的位置。如果您在安装过程中选择了默认文件夹，请转到 C:\Deployment Tools\IdFix。
    
3. 双击“IdFix.exe”****。 
    
    ![选择 IdFix.exe 文件。](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. 默认情况下，IdFix 使用的多租户规则集测试您的目录中的条目。这是为 Office 365 的大多数客户的右规则。但是，如果您是 Office 365 专用或 ITAR （国际流量 Arm 法规） 客户，您可以配置 IdFix 使用专用的规则设置而不是。如果不确定哪种类型的客户后，您可以安全跳过此步骤。要设置设置为专用的规则，请单击菜单栏中的齿轮图标，然后选择**专用**。
    
5. 选择**查询**。
    
    ![在 IdFix 中选择查询。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. 默认情况下，IdFix 对整个目录搜索错误。
    
    根据您的目录的大小，运行查询可能需要一段。您可以观看该工具主窗口底部的进度。如果单击**取消**，您需要重新启动从头开始。
    
    ![IdFix 查询和错误数。](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. IdFix 完成查询之后，且目录中没有错误，则可以继续同步目录。如果您的目录中有错误，建议您在同步之前先修复这些错误。如果您想了解有关错误类型以及对解决每个错误的最佳方法的建议的详细信息，请参阅本主题结尾的链接。 
    
    虽然对同步之前修复错误的做法不是强制性的，但我们还是强烈建议您至少检查一下由 IdFix 返回的所有错误。
    
    每个错误显示在该工具主窗口中单独的行中。 
    
8. 如果您同意“UPDATE”**** 列中的更改建议，请在“ACTION”**** 列中选择 IdFix 要实现此更改应执行的操作，然后单击“应用”****。当您单击“应用”**** 时，该工具会在目录中做出更改。
    
    您无需在每个更新后单击**应用**。相反，可以解决几个错误之前单击**应用**，IdFix 将所有在同时更改它们。可以通过单击**错误**顶部列出了错误类型的列的排序错误类型的错误。 
    
    一种策略是修复的相同类型; 所有错误例如，首先，修复所有重复项，并应用这些更改。接下来，修复字符格式错误，等等。每次应用所做的更改，IdFix 工具创建单独的日志文件可用于犯的情况下撤消所做的更改。[事务日志](idfix-transaction-log.md)存储在您安装 IdFix 中的文件夹。 默认情况下_C:\Deployment Tools\IdFix_ 。 
    
    ![解决 IdFix 中的错误。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. 毕竟所做更改的所做的目录，并运行 IdFix 再次以确保您所做的修补程序未引入了新的错误。您可以重复这些步骤，根据需要多次。最好进入流程几次同步之前。
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>我想优化我的搜索或深入研究错误，我还能用 IdFix 来做些什么？

以下主题可提供更深入的信息：
  
- [准备目录属性与通过使用 IdFix 工具的 Office 365 进行同步](prepare-directory-attributes-for-synch-with-idfix.md)。您已安装的工具，跳转到本主题的更详细说明有关运行该工具之后, 会遇到的常见错误建议的修补程序、 示例和要执行的操作数量较大的错误后的最佳做法。 
- [参考：IdFix 排除和支持的对象和属性](idfix-excluded-and-supported-objects-and-attributes.md)  
- [参考：Office 365 IdFix 事务日志](idfix-transaction-log.md)
    
## <a name="video-training"></a>视频培训

有关详细信息，请参阅进入您的 LinkedIn 学习课[安装和使用 IDFix 工具](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx)。
  

