---
title: 下载并运行 Microsoft 365 IdFix 工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Priority
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: 如何下载并运行 Microsoft 365 IdFix 工具，帮助清理你的 Active Directory 域服务 (AD DS)，然后再将其同步到 Microsoft 365。
ms.openlocfilehash: beef13857ad00806cc3e62aedd7a1b3c48bfe4c0
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502657"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a>下载并运行 Microsoft 365 IdFix 工具

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

IdFix 可标识在同步到 Microsoft 365 之前 Active Directory 域服务 (AD DS) 域中的错误，例如重复项和格式设置问题。 
  
要成功完成此任务，应该小心地使用 AD DS 中的用户、组和联系人对象。
  
如果无法完成此任务，可以执行一些其他操作。 这些方法可能更简单，但可能还会花费更长时间，也可能有一些其他缺点。 具体包括：
  
- **在不运行 IdFix 的情况下运行目录同步** 

  可以在不使用 IdFix 工具的情况下同步目录，但不建议这样做。 在同步之前修复错误花费的时间会少一些，这往往可以帮助顺利过渡到云。 

- **聘请顾问** 

  获得专家的帮助可以让你的用户正常工作并提高运行速度，使你的目录顺利实现同步。 
    
## <a name="what-you-need-to-run-idfix"></a>运行 IdFix 的前提条件

启动并运行 IdFix 最简单的方法是将其下载到已加入你的 AD DS 域中的计算机上。 如需要，可以在域控制器上运行它，但这不是必需的。
  
### <a name="idfix-hardware-requirements"></a>IdFix 硬件要求

用于下载 IdFix 的计算机需要满足以下最低硬件要求：
  
- 4 GB RAM
- 2 GB 的硬盘空间
   
### <a name="idfix-software-requirements"></a>IdFix 软件要求

你下载了 IdFix 的计算机需要加入到你要将用户同步到 Microsoft 365 所在的同一个 AD DS 域中。 

该计算机也需要安装有 .NET Framework 4.0。 如果你运行的是 Windows Server 2008 或更高版本，那么很可能已经安装了 .NET Framework。 如果没有，可以[从下载中心下载 .NET 4.0](https://go.microsoft.com/fwlink/p/?LinkId=400475) 或通过 Windows 更新进行下载。 
  
### <a name="idfix-permissions-requirements"></a>IdFix 权限要求

用于运行 IdFix 的用户帐户必须对 AD DS 域具有读取和写入访问权限。
  
如果你还不清楚你的用户帐户是否满足这些要求，也不知道要如何检查，仍可以下载和运行 IdFix。 如果你的用户帐户不具有正确的权限，当你尝试运行 IdFix 时，IdFix 只会显示一个错误。
  
## <a name="download-and-extract-idfix"></a>下载并提取 IdFix

按照以下说明操作。 
  
1. 登录到要运行 IdFix 工具的计算机。
    
2. 转到 [IdFix DirSync 错误修正工具](https://github.com/microsoft/idfix)网站。
    
3. 在“ClickOnce 启动”部分中单击“启动”以下载 zip 文件********。 打开 zip 文件。
    
4. 在“IdFix”窗口中，依次选择“提取”、“全部提取”************。 默认情况下，IdFix 将被提取到 `C:\Users\<your user name>\Documents\IdFix`。 
    
5. 选择“提取”****。

根据使用的 Windows 和 Internet 浏览器的版本，具体步骤可能会有所差异。
    
## <a name="run-the-idfix-tool"></a>运行 IdFix 工具

下载并提取 IdFix 后，运行它以搜索 AD DS 域中的问题。
  
1. 使用对 AD DS 域具有读取/写入访问权限的帐户，登录到已下载 IdFix 的计算机。
    
2. 在文件资源管理器中，转到你提取了 IdFix 的位置。 如果在提取过程中选择了默认文件夹，则转到 `C:\Users\<your user name>\Documents\IdFix`。 
    
3. 双击“IdFix.exe”****。 
  
4. 默认情况下，IdFix 使用多租户规则集来测试你的目录中的条目。 这是适用于大多数 Microsoft 365 客户的正确规则集。 但是，如果你是 Microsoft 365 专用客户，或是国际武器贸易条例 (ITAR) 客户，可以将 IdFix 配置为使用专用的规则集。 如果你不知道自己是什么类型的客户，可以跳过这一步。 要将规则集设置为专用规则集，请单击菜单栏上的齿轮图标，然后选择“专用”****。
    
5. 选择“查询”****。
    
    ![在 IdFix 中选择查询。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. 默认情况下，IdFix 将搜索整个目录中的错误。
    
    根据你的目录的大小，运行查询可能需要花些时间。 可以在工具的主窗口底部观察进度。 如果单击“取消”****，就需要从头重新开始。
  
7. IdFix 完成查询之后，如果没有错误，则可以同步目录。 如果你的目录中有错误，建议在同步之前先修复这些错误。 有关详细信息，请参阅[准备目录属性进行与 Microsoft 365 的同步](prepare-directory-attributes-for-synch-with-idfix.md)。
    
    虽然并不强制在同步之前修复错误，但强烈建议至少检查一下由 IdFix 返回的所有错误。
    
    每个错误均显示在工具主窗口中的单独行内。 
    
8. 如果你同意“更新”**** 列中的更改建议，请在“操作”**** 列中选择 IdFix 要实现此更改应执行的操作，然后单击“应用”****。 单击“应用”**** 时，工具将在目录中进行更改。
    
    不必在每次更新后都单击“应用”****。 相反，可以在单击“应用”**** 之前修复一些错误，IdFix 会同时对它们做出更改。 在列出错误类型的列的顶部，可单击“错误”**** 按错误类型进行错误排序。 
    
    一种策略是修复同一类型的所有错误；例如，首先修复所有重复错误，然后再应用它们。 接着，修复字符格式错误，等等。 每次应用更改时，IdFix 工具都会创建一个单独的日志文件，在出错时，就可以用它来撤消所做的更改。 [事务日志](idfix-transaction-log.md)存储在你提取了 IdFix 的文件夹中，默认情况下为 _C:\Users\<your user name>\Documents\IdFix_。 
    
    ![在 IdFix 中修正错误。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. 对目录执行完所有的更改之后，请再次运行 IdFix 以确保所做的修复没有引入新的错误。 可以根据需要多次重复这些步骤。 在进行同步之前，最好多次演练此过程。
    
## <a name="additional-resources-on-idfix"></a>IdFix 上的其他资源 

- [IdFix 排除和支持的对象和属性](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Microsoft 365 IdFix 事务日志](idfix-transaction-log.md)
    
