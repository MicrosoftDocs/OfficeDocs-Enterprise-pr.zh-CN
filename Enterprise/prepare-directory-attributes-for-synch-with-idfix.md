---
title: 使用 IdFix 工具准备好与 Office 365 进行同步的目录属性
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: 提供有关如何使用 IdFix 在同步到 Office 365 之前准备和清理本地目录的说明。
ms.openlocfilehash: cdfee8178f731d20c799f550d1dacb0a04a72cae
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085091"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>使用 IdFix 工具准备好与 Office 365 进行同步的目录属性
本主题包含有关运行 IdFix 工具的详细说明、可能遇到的一些常见错误、建议的修补程序、示例和最佳做法, 以了解在遇到大量错误时应采取的操作。
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>使用 IdFix GUI 修复您目录中的错误
[运行 Office 365 IdFix 工具](install-and-run-idfix.md)以搜索目录中的问题, 然后按照本主题中所述修复 GUI 中的错误。如果该工具返回一个空白表, 则不会发现任何错误。如果目录中存在很多问题, 则当该工具返回错误时, 可能会很困难。解决此问题的一种方法是先修复一种类型的所有错误, 然后再移到下一种类型。 
  
1. 在开始进行更改之前，要先看看 IdFix 给出的建议。
    
2. 查看 IdFix 返回的错误列表。您可以通过单击错误类型列顶部的“ERROR”****，按照错误类型对错误进行排序。如果有多个错误都与某个属性相关联，那么这些错误将被合并到同一列中。如有可能，IdFix 会在“UPDATE”**** 列中显示修复建议。修复建立在对与对象相关联的其他属性进行检查的基础上。虽然这些通常比目录中已经存在的要更好些，但只有您自己才能决定什么是真正准确的。 
    
3. 如果 IdFix 对修补程序有重复错误的建议, 则会通过 "**更新**" 列中值开头的三个标志之一来标识该修补程序 (例如,) `[E]john.doe@contoso.com`。如果您接受建议, 则在应用更改时, 将不会在目录中插入标志。例如, `john.doe@contoso.com`将仅应用建议标志后面的值。如果要接受该建议, 请从 "**操作**" 列中选择匹配的操作。这些标志指示操作, 如下所示: 
    
 - **[C]** 表示的建议操作是“COMPLETE”****。不需要对该值进行编辑。
    
 - **[E]** 表示的建议操作是“EDIT”****。应更改该值，避免与目录中的另一个值相冲突。
    
 - **[R]** 表示的建议操作是“REMOVE”****。该值是针对启用了非邮件功能的对象的一个 SMTP 代理，且可以被安全地删除。
    
4. 阅读并了解错误后, 请使用所做的更改更新 "**更新**" 列中的条目, 然后在 "**操作**" 列中选择您希望 IdFix 实现更改所要执行的操作。例如, 两个用户可能会被`proxyAddress`标识为重复项。只有一个用户可以使用`proxyAddress`进行邮件传递。若要解决此问题, 请将具有正确值的用户的 "**操作**" 列标记为 "已**完成**", 并为其他用户标记 "**操作**" 列**删除**。这将从`proxyAddress`用户中删除该`proxyAddress`属性不属于的用户, 并且不会对其`proxyAddress`正确的用户做出任何更改。
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>IdFix 检测到的常见错误和修复建议
下表描述了由 IdFix 检测到的错误，提供了工具中最常见的修复建议，并且在某些情况下，提供了如何解决这些问题的示例。

|**误差**|**错误类型说明**|**修复建议**|**示例**|
|:-----|:-----|:-----|:-----|
|**character** | 非法字符。该值中包含无效字符。 | “UPDATE”**** 列中所示错误的修复建议显示已删除了无效字符的值。  <br/> | 有效邮件地址末尾的尾部空格是非法字符, 例如:  <br/> " `user@contoso.com` "  <br/> 有效邮件地址开头的前导空格是非法字符, 例如:  <br/> " ` user@contoso.com `"  <br/>  `ú`字符是非法字符。 |
|**duplicate** | 重复的条目。值的查询范围内有重复项。所有重复的值都会显示为错误。 | 编辑或删除这些值来消除重复。该工具不会为重复项提供修复建议。相反，您必须在两个或多个重复之中选择正确的条目，并删除重复的条目。 ||
|**format** | 格式错误。该值违反对属性用法的格式要求。 | “更新”建议将显示已删除了无效字符的值。如果没有无效字符，则“更新”和“值”显示相同。您需要确定您真正需要更新的内容。该工具无法提供适用于所有格式错误的修复建议。 | 例如, SMTP 地址必须符合 RFC 2822, 并且 mailNickName 不能以句点开头或结尾。有关目录属性的格式要求的详细信息, 请参阅[准备通过目录同步将用户预配到 Office 365](prepare-for-directory-synchronization.md)中的 "目录对象和属性准备"。 |
|topleveldomain  <br/> |顶级域。这适用于受[RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464)格式设置的值。如果顶级域不是 internet 可路由的, 则会将其标识为错误。例如, 以结尾的 SMTP 地址。本地不是 internet 路由的, 将导致此错误。 |将值更改为 internet 可路由的域, `.com`例如`.net`或。 | 更改`myaddress@fourthcoffee.local`为`fourthcoffee.com`或其他 internet 可路由域。  <br/> 有关说明, 请参阅[如何为目录同步准备不可路由的域 (例如, 本地域)](prepare-a-non-routable-domain-for-directory-synchronization.md)。 |
|**domainpart** | 域部分错误。这适用于符合 RFC 2822 格式的值。如果该值的域部分无效，并且不符合 RFC 2822，则会生成此错误。 | 将值更改为符合 RFC 2822 的值。例如, 请确保它不包含任何空格或非法字符。 | 更改`myaddress@fourth coffee.com`为`myaddress@fourthcoffee.com`。 |
|**domainpart_localpart** | Local-part 错误。这适用于符合 RFC 2822 格式的值。如果该值的本地部分无效，并且不符合 RFC 2822，则会生成此错误。 |将值更改为符合 RFC 2822 的值。例如, 请确保它不包含任何空格或非法字符。 |更改`my"work"address@fourthcoffee.com`为`myworkaddress@fourthcoffee.com`。 |
|**length** | 长度错误。该值违反了属性的长度限制。当目录架构发生了改变时，这种是最常遇到的错误。  | IdFix 的更新建议会将该值截断到可以接受的长度。  <br/> 请注意，这可能会产生意外的结果。在您单击“应用”**** 之前，必要时需要检查修复建议，并对其进行更改。 ||
|**blank**  | 空白或 null 错误。该值违反了对要进行同步的属性的 null 限制。只有少数的属性必须包含一个值。 | 如果可能的话，更新建议将利用其他属性值来生成一个可能的替代品。 ||
|**mailmatch** | 这适用于仅专用于 Office 365 的。值与 mail 属性不匹配。 | 建议的更新将是前缀为 "SMTP:" 的邮件属性值。 ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>您可以使用 IdFix 执行的操作
若要修复错误, 请从 "**操作**" 下拉列表中选择一个选项。下表介绍了您可以使用 IdFix 工具对属性执行的**操作**操作。如果将 "**操作**" 列保留为空, 则 IdFix 工具将不会对目录中的特定错误执行任何操作。 

|**退货**|**操作说明**|**示例**|
|:-----|:-----|:-----|
|**COMPLETE** | 原始值是可以接受的，即使被标识为错误也不应改变。 | 两个用户都有标识为重复的 proxyAddress。只有一个用户可以将该值用于邮件传递。将使用正确值的用户标记为“COMPLETE”****。 |
|**删除** | 属性值将从源对象中删除。对于多值属性, 例如`proxyAddresses`, 只有显示的单个值将被删除。 | 两个用户都有标识为重复的 proxyAddress。只有一个用户可以将该值用于邮件传递。将使用重复值的用户标记为“REMOVE”****。 |
|**编辑** | 将使用 "**更新**" 列中的信息修改属性值。如果已通过 IdFix 建议了有效的**更新**值, 则从 "**操作**" 列中选择 "**编辑**", 然后继续执行下一个错误。如果不喜欢该建议, 请在 "**更新**" 列中键入新的, 然后从 "**操作**" 列中选择 "**编辑**"。 ||
|**取消** | 仅当您已从事务日志中还原时，此选项才可用。如果您选择“撤消”****，属性值将还原为原始值。 ||
|**FAIL** | 仅当**更新**值与 AD DS 规则发生未知冲突时, 才会返回此值。在这种情况下, 如果您知道故障是什么, 则可以再次编辑 "**更新**" 列中的值。可能需要使用 ADSI Edit 分析对象中的值。有关详细信息, 请参阅[ADSI Edit (adsi .msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170)。 ||

在对一个错误或一批错误选择了某个“ACTION”**** 之后，请单击“应用”****。当您单击“应用”**** 时，该工具会在目录中做出更改。在您单击“应用”**** 之前可以对多个错误进行修复，IdFix 会同时对它们进行更改。

再次运行 IdFix 以确保您所做的修补程序未引入新的错误。您可以根据需要多次重复这些步骤。在同步之前, 最好先完成几次此过程。
    
## <a name="changing-the-rule-set-used-by-idfix"></a>更改 IdFix 使用的规则集
默认情况下, IdFix 使用多租户规则集测试目录中的条目。这是大多数 Office 365 = 客户的正确规则集。但是, 如果您是 Office 365 专用或 ITAR (arm 规章中的国际流量) 客户, 则可以将 IdFix 配置为改用专用规则集。如果您不确定您是哪种类型的客户, 则可以安全地跳过此步骤。若要将规则集设置为专用, 请单击菜单栏中的齿轮图标, 然后单击 "**专用**"。
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>更改 IdFix 使用的搜索范围
默认情况下，IdFix 搜索整个目录。如果您愿意，您可以将该工具配置为搜索一个特定的子树。为此，在菜单栏中，单击筛选器图标，然后输入一个有效的子树。
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>通过使用 IdFix GUI 回滚您的更改
每次单击 "**应用**" 以应用更改时, IdFix 工具将创建一个名为 "事务日志" 的单独文件, 其中列出了刚才所做的更改。您可以使用事务日志回滚在最近的日志中进行的更改, 以防您犯错误。如果在更新过程中出现错误, 则可以通过单击 "**撤消**" 来撤消最近应用的更改。当您单击 "**撤消**" 时, IdFix 将使用事务日志回滚在最近的事务日志中的更改。有关使用事务日志的详细信息, 请参阅[Reference: Office 365 IdFix transaction log](idfix-transaction-log.md)。