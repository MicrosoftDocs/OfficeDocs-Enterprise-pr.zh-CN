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
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: 使用 IdFix 准备和清理您本地目录同步到 Office 365 之前提供指导。
ms.openlocfilehash: a4fc8af476ec8ffdd7d762796abe1ec210a1bacb
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539788"
---
# <a name="prepare-directory-attributes-for-synchronization-with-office-365-by-using-the-idfix-tool"></a>使用 IdFix 工具准备好与 Office 365 进行同步的目录属性
本主题包含有关运行 IdFix 工具，详细的说明一些您可能遇到的常见错误建议修补程序、 示例和要执行的操作如果您有大量的错误的最佳做法。
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>使用 IdFix GUI 修复您目录中的错误
[运行 Office 365 IdFix 工具](install-and-run-idfix.md)搜索目录中的问题，并然后修复图形用户界面中的错误，如本主题中所述。如果一个空白表返回工具，然后不发现任何错误。如果有大量的目录中的问题，请将很复杂时工具返回的错误。一种方法来处理这是首次修复的一种类型的所有错误，然后移到下一个类型。 
  
1. 在开始进行更改之前，要先看看 IdFix 给出的建议。
    
2. 查看 IdFix 返回的错误列表。您可以通过单击错误类型列顶部的“ERROR”****，按照错误类型对错误进行排序。如果有多个错误都与某个属性相关联，那么这些错误将被合并到同一列中。如有可能，IdFix 会在“UPDATE”**** 列中显示修复建议。修复建立在对与对象相关联的其他属性进行检查的基础上。虽然这些通常比目录中已经存在的要更好些，但只有您自己才能决定什么是真正准确的。 
    
3. 如果 IdFix 有重复错误修复建议，修复由标识**UPDATE**列中的值开头的三个标记之一，例如， `[E]john.doe@contoso.com`。如果应用此标志将不插入目录中的更改时，您可以接受建议。关注标记将应用，例如，建议值`john.doe@contoso.com`。如果您想要接受建议，请从**操作**列中选择匹配操作。标志指示操作，如下所示： 
    
 - **[C]** 表示的建议操作是“COMPLETE”****。不需要对该值进行编辑。
    
 - **[E]** 表示的建议操作是“EDIT”****。应更改该值，避免与目录中的另一个值相冲突。
    
 - **[R]** 表示的建议操作是“REMOVE”****。该值是针对启用了非邮件功能的对象的一个 SMTP 代理，且可以被安全地删除。
    
4. 一次您已阅读并理解错误，使用您的更改，更新**更新**列中的条目，然后**操作**中列选择希望 IdFix 执行的操作实现更改。例如，可能有两个用户`proxyAddress`标识为重复。只有一个用户可以使用`proxyAddress`针对邮件传递。若要解决此问题，标记的正确值的用户的**操作**列**完成**并标记**操作**列**中删除**为其他用户。删除`proxyAddress`属性从用户添加到其这`proxyAddress`不属于和不使任何变化对用户为其这`proxyAddress`正确无误。
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>IdFix 检测到的常见错误和修复建议
下表描述了由 IdFix 检测到的错误，提供了工具中最常见的修复建议，并且在某些情况下，提供了如何解决这些问题的示例。

|**错误**|**错误类型说明**|**修复建议**|**示例**|
|:-----|:-----|:-----|:-----|
|**character** | 非法字符。该值中包含无效字符。 | “UPDATE”**** 列中所示错误的修复建议显示已删除了无效字符的值。  <br/> | 有效的电子邮件地址结尾空格是非法字符，例如：  <br/> " `user@contoso.com` "  <br/> 前导空格开头的有效电子邮件地址是非法字符，例如：  <br/> " ` user@contoso.com `"  <br/>  `ú`字符是非法字符。 |
|**duplicate** | 重复的条目。值的查询范围内有重复项。所有重复的值都会显示为错误。 | 编辑或删除这些值来消除重复。该工具不会为重复项提供修复建议。相反，您必须在两个或多个重复之中选择正确的条目，并删除重复的条目。 ||
|**format** | 格式错误。该值违反对属性用法的格式要求。 | “更新”建议将显示已删除了无效字符的值。如果没有无效字符，则“更新”和“值”显示相同。您需要确定您真正需要更新的内容。该工具无法提供适用于所有格式错误的修复建议。 | 例如，SMTP 地址必须符合 RFC 2822 和 mailNickName 不能开头或结尾一段时间。有关目录属性的格式要求的详细信息，请参阅[Prepare to provision 用户通过目录同步到 Office 365](prepare-for-directory-synchronization.md)中的"目录对象和属性准备"。 |
|topleveldomain  <br/> |顶部级别的域。这适用于受到[RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464)格式的值。如果顶级域不是 internet 可路由然后这会被标识为错误。例如 SMTP 地址结束.local 中 internet 可路由并不会导致此错误。 |将该值更改为 internet 可路由域如`.com`或`.net`。 | 更改`myaddress@fourthcoffee.local`到`fourthcoffee.com`或其他 internet 可路由域。  <br/> 有关说明，请参阅[如何准备进行目录同步非可路由域 （如.local 域）](prepare-a-non-routable-domain-for-directory-synchronization.md)。 |
|**domainpart** | 域部分错误。这适用于符合 RFC 2822 格式的值。如果该值的域部分无效，并且不符合 RFC 2822，则会生成此错误。 | 将值更改为一个符合 RFC 2822。例如，请确保其不包含任何空格或非法字符。 | 更改`myaddress@fourth coffee.com`到`myaddress@fourthcoffee.com`。 |
|**domainpart_localpart** | Local-part 错误。这适用于符合 RFC 2822 格式的值。如果该值的本地部分无效，并且不符合 RFC 2822，则会生成此错误。 |将值更改为一个符合 RFC 2822。例如，请确保其不包含任何空格或非法字符。 |更改`my"work"address@fourthcoffee.com`到`myworkaddress@fourthcoffee.com`。 |
|**length** | 长度错误。该值违反了属性的长度限制。当目录架构发生了改变时，这种是最常遇到的错误。  | IdFix 的更新建议会将该值截断到可以接受的长度。  <br/> 请注意，这可能会产生意外的结果。在您单击“应用”**** 之前，必要时需要检查修复建议，并对其进行更改。 ||
|**blank**  | 空白或 null 错误。该值违反了对要进行同步的属性的 null 限制。只有少数的属性必须包含一个值。 | 如果可能的话，更新建议将利用其他属性值来生成一个可能的替代品。 ||
|**mailmatch** | 这仅适用于 Office 365 专用。值与 mail 属性不匹配。 | 建议的更新将是前缀的邮件属性值"SMTP:"。 ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>您可以使用 IdFix 执行的操作
若要修复错误，您可以从**操作**下拉列表中选择一个选项。下表描述了您可以在使用 IdFix 工具的属性执行的**操作**操作。如果将**操作**列保留为空，IdFix 工具将在目录中的特定错误不执行任何操作。 

|**操作**|**操作说明**|**示例**|
|:-----|:-----|:-----|
|**COMPLETE** | 原始值是可以接受的，即使被标识为错误也不应改变。 | 两个用户都有标识为重复的 proxyAddress。只有一个用户可以将该值用于邮件传递。将使用正确值的用户标记为“COMPLETE”****。 |
|**删除** | 源对象中，属性值将被删除。对于多值属性，例如， `proxyAddresses`，仅显示的单个值将被删除。 | 两个用户都有标识为重复的 proxyAddress。只有一个用户可以将该值用于邮件传递。将使用重复值的用户标记为“REMOVE”****。 |
|**编辑** | **UPDATE**列中的信息将用于修改属性值。如果已 idfix 建议有效的**更新**值，然后从**操作**列中，选择**编辑**并转到下一个错误。如果您不希望建议，键入一个新的**更新**列，然后选择从**操作**列的**编辑**。 ||
|**撤消** | 仅当您已从事务日志中还原时，此选项才可用。如果您选择“撤消”****，属性值将还原为原始值。 ||
|**FAIL** | 如果**更新**值具有与 AD DS 规则冲突的未知，则只会返回此值。在这种情况下，您可以再次编辑**UPDATE**列中的值，如果您知道什么是故障。可能需要分析中使用 ADSI Edit 的对象的值。有关详细信息，请参阅[ADSI Edit (adsiedit.msc)](https://go.microsoft.com/fwlink/p/?LinkId=401170)。 ||

在对一个错误或一批错误选择了某个“ACTION”**** 之后，请单击“应用”****。当您单击“应用”**** 时，该工具会在目录中做出更改。在您单击“应用”**** 之前可以对多个错误进行修复，IdFix 会同时对它们进行更改。

运行 IdFix 再次以确保您所做的修补程序未引入了新的错误。您可以重复这些步骤，根据需要多次。最好进入流程几次同步之前。
    
## <a name="changing-the-rule-set-used-by-idfix"></a>更改 IdFix 使用的规则集
默认情况下，IdFix 使用的多租户规则集测试您的目录中的条目。这是为大多数 Office 365 的右规则 = 客户。但是，如果您是 Office 365 专用或 ITAR （国际流量 Arm 法规） 客户，您可以配置 IdFix 使用专用的规则设置而不是。如果不确定哪种类型的客户后，您可以安全跳过此步骤。要设置设置为专用的规则，请单击菜单栏中的齿轮图标，然后单击**专用**。
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>更改 IdFix 使用的搜索范围
默认情况下，IdFix 搜索整个目录。如果您愿意，您可以将该工具配置为搜索一个特定的子树。为此，在菜单栏中，单击筛选器图标，然后输入一个有效的子树。
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>通过使用 IdFix GUI 回滚您的更改
单击**应用**以应用更改，每次 IdFix 工具创建名为列出了您刚才所做的更改的事务日志的单独文件。您可以使用的事务日志，回滚的最新日志中出现错误的情况下只这些更改。如果要更新时的错误，您可以通过单击**撤消**撤消最近所应用的更改。时单击**撤消**后，IdFix 使用的事务日志，回滚只是最新的事务日志中的这些更改。有关使用事务日志的详细信息，请参阅[参考： Office 365 IdFix 事务日志](idfix-transaction-log.md)。