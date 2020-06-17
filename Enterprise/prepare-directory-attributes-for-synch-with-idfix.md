---
title: 使用 IdFix 工具准备要与 Microsoft 365 同步的目录属性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: 497593cf-24c6-491c-940b-7c86dcde9de0
description: 提供有关如何使用 IdFix 在同步到 Microsoft 365 之前准备和清理本地目录的说明。
ms.openlocfilehash: cae1df048e58c65a3203ea39df18beb986adb0c8
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "44736000"
---
# <a name="prepare-directory-attributes-for-synchronization-with-microsoft-365-by-using-the-idfix-tool"></a>使用 IdFix 工具准备要与 Microsoft 365 同步的目录属性

*本文适用于 Microsoft 365 企业版和 Office 365 企业版。*

本主题包含有关运行 IdFix 工具的详细说明、可能遇到的一些常见错误、建议的修补程序、示例和最佳做法，以了解在遇到大量错误时应采取的操作。
  
## <a name="fixing-errors-in-your-directory-by-using-the-idfix-gui"></a>使用 IdFix GUI 修复目录中的错误

[运行 Microsoft 365 IdFix 工具](install-and-run-idfix.md)以搜索目录中的问题，然后按照本主题中所述修复 GUI 中的错误。 如果该工具返回一个空白表，则不会发现任何错误。 如果目录中存在很多问题，则当该工具返回错误时，可能会很困难。 解决此问题的一种方法是先修复一种类型的所有错误，然后再移到下一种类型。 
  
1. 在开始进行更改之前，请查看 IdFix 提供的建议。
    
2. 查看 IdFix 返回的错误列表。 您可以通过单击列出错误类型的列顶部的 "**错误**"，按错误类型对错误进行排序。 如果有多个错误与单个属性相关联，则这些错误将合并到一行中。 在可能的情况下，IdFix 会提供 "**更新**" 列中的修复建议。 该修补程序基于与对象关联的其他属性的检查。 虽然这些通常比目录中已有的内容更好，但只有您可以决定真正准确的内容。 
    
3. 如果 IdFix 对修补程序有重复错误的建议，则会通过 "**更新**" 列中值开头的三个标志之一来标识该修补程序（例如，） `[E]john.doe@contoso.com` 。 如果您接受建议，则在应用更改时，将不会在目录中插入标志。 例如，将仅应用建议标志后面的值 `john.doe@contoso.com` 。 如果要接受该建议，请从 "**操作**" 列中选择匹配的操作。 这些标志指示操作，如下所示： 
    
 - **[C]** 建议的操作**完成**。 不需要对值进行编辑。
    
 - **[E]** 建议的操作**编辑**。 应更改该值以避免与目录中的其他值发生冲突。
    
 - **[R]** 建议**删除**操作。 该值是启用了非邮件的对象上的 SMTP 代理，可能会安全地删除。
    
4. 阅读并了解错误后，请使用所做的更改更新 "**更新**" 列中的条目，然后在 "**操作**" 列中选择您希望 IdFix 实现更改所要执行的操作。 例如，两个用户可能会被 `proxyAddress` 标识为重复项。 只有一个用户可以使用 `proxyAddress` 进行邮件传递。 若要解决此问题，请将具有正确值的用户的 "**操作**" 列标记为 "已**完成**"，并为其他用户标记 "**操作**" 列**删除**。 这将 `proxyAddress` 从用户中删除该属性 `proxyAddress` 不属于的用户，并且不会对其正确的用户做出任何更改 `proxyAddress` 。
    
## <a name="common-errors-and-fixes-detected-by-idfix"></a>IdFix 检测到的常见错误和修复
下表介绍了 IdFix 检测到的错误，提供了该工具最常推荐的修补程序，在某些情况下，还提供了有关如何修复这些错误的示例。

|**误差**|**错误类型说明**|**建议的修补程序**|**示例**|
|:-----|:-----|:-----|:-----|
|**通配符** | 非法字符。 值包含无效的字符。 | "**更新**" 列中显示的错误的建议修补程序将显示值为删除的无效字符。  <br/> | 有效邮件地址末尾的尾部空格是非法字符，例如：  <br/> " `user@contoso.com` "  <br/> 有效邮件地址开头的前导空格是非法字符，例如：  <br/> " ` user@contoso.com `"  <br/>  `ú`字符是非法字符。 |
|**直接** | 重复条目。 值在查询的范围内重复。 所有重复值将显示为错误。 | 编辑或删除值以消除重复。 该工具不会为重复项提供建议的修补程序。 相反，您必须选择两个或更多个重复项中的哪一个是正确的，并删除重复的项。 ||
|**format** | 格式错误。 此值违反了属性用法的格式要求。 | 建议的更新将显示删除了任何无效字符的值。 如果没有无效字符，更新和值将显示相同。 您需要在更新中确定您真正需要的内容。 该工具不会为所有格式设置错误提供建议的修补程序。 | 例如，SMTP 地址必须符合 RFC 2822，并且 mailNickName 不能以句点开头或结尾。 有关目录属性的格式要求的详细信息，请参阅[准备通过目录同步将用户预配到 Microsoft 365](prepare-for-directory-synchronization.md)中的 "目录对象和属性准备"。 |
|topleveldomain  <br/> |顶级域。 这适用于受[RFC 2822](https://go.microsoft.com/fwlink/p/?LinkId=401464)格式设置的值。 如果顶级域不是 internet 可路由的，则会将其标识为错误。 例如，以结尾的 SMTP 地址。本地不是 internet 路由的，将导致此错误。 |将值更改为 internet 可路由的域，例如 `.com` 或 `.net` 。 | 更改 `myaddress@fourthcoffee.local` 为 `fourthcoffee.com` 或其他 internet 可路由域。  <br/> 有关说明，请参阅[如何为目录同步准备不可路由的域（例如，本地域）](prepare-a-non-routable-domain-for-directory-synchronization.md)。 |
|**domainpart** | 域部件错误。 这适用于受 RFC 2822 格式设置的值。 如果值的域部分无效且不符合 RFC 2822，则将生成此值。 | 将值更改为符合 RFC 2822 的值。 例如，请确保它不包含任何空格或非法字符。 | 更改 `myaddress@fourth coffee.com` 为 `myaddress@fourthcoffee.com` 。 |
|**domainpart_localpart** | 本地错误。 这适用于受 RFC 2822 格式设置的值。 如果值的本地部分无效且不符合 RFC 2822，则将生成此值。 |将值更改为符合 RFC 2822 的值。 例如，请确保它不包含任何空格或非法字符。 |更改 `my"work"address@fourthcoffee.com` 为 `myworkaddress@fourthcoffee.com` 。 |
|**Length** | 长度错误。 值违反属性的长度限制。 当目录架构已更改时，通常会遇到这种情况。  | IdFix 建议的更新会将值截断为可接受的长度。  <br/> 请注意，这可能会产生不理想的结果。 您应查看建议的修补程序并在需要时更改它，然后再单击 "**应用**"。 ||
|**空字符**  | 空或 null 错误。 值违反了要同步的属性的 null 限制。 只有少数几个属性必须包含一个值。 | 如果可能，建议的更新将利用其他属性值来生成可能的替代项。 ||
|**mailmatch** | 这适用于仅适用于 Microsoft 365 的专用版。 值与 mail 属性不匹配。 | 建议的更新将是前缀为 "SMTP：" 的邮件属性值。 ||
    
## <a name="operations-you-can-perform-by-using-idfix"></a>您可以使用 IdFix 执行的操作
若要修复错误，请从 "**操作**" 下拉列表中选择一个选项。 下表介绍了您可以使用 IdFix 工具对属性执行的**操作**操作。 如果将 "**操作**" 列保留为空，则 IdFix 工具将不会对目录中的特定错误执行任何操作。 

|**退货**|**操作说明**|**示例**|
|:-----|:-----|:-----|
|**全面** | 原始值是可接受的，即使被标识为错误，也不应更改。 | 两个用户有一个被标识为重复的 proxyAddress。 只有一种情况可以使用邮件传递的值。 将具有正确值的用户标记为 "已**完成**"。 |
|**删除** | 属性值将从源对象中删除。 对于多值属性，例如， `proxyAddresses` 只有显示的单个值将被删除。 | 两个用户有一个被标识为重复的 proxyAddress。 只有一种情况可以使用邮件传递的值。 将具有重复值的用户标记为 "**删除**"。 |
|**编辑** | 将使用 "**更新**" 列中的信息修改属性值。 如果已通过 IdFix 建议了有效的**更新**值，则从 "**操作**" 列中选择 "**编辑**"，然后继续执行下一个错误。 如果不喜欢该建议，请在 "**更新**" 列中键入新的，然后从 "**操作**" 列中选择 "**编辑**"。 ||
|**取消** | 仅当您从事务日志中还原时，此选项才可用。 如果选择 "**撤消**"，则会将属性值还原为原始值。 ||
|**FAIL** | 仅当**更新**值与 AD DS 规则发生未知冲突时，才会返回此值。 在这种情况下，如果您知道故障是什么，则可以再次编辑 "**更新**" 列中的值。 可能需要使用 ADSI Edit 分析对象中的值。 有关详细信息，请参阅[ADSI Edit （adsi .msc）](https://go.microsoft.com/fwlink/p/?LinkId=401170)。 ||

为错误或错误批处理选择**操作**后，单击 "**应用**"。 当您单击 "**应用**" 时，该工具会在目录中进行更改。 您可以在单击 "**应用**" 之前提供多个错误的修复程序，IdFix 将同时更改所有这些错误。

再次运行 IdFix 以确保您所做的修补程序未引入新的错误。 您可以根据需要多次重复这些步骤。 在同步之前，最好先完成几次此过程。
    
## <a name="changing-the-rule-set-used-by-idfix"></a>更改 IdFix 使用的规则集
默认情况下，IdFix 使用多租户规则集测试目录中的条目。 这是大多数 Microsoft 365 客户的正确规则集。 但是，如果您是 Microsoft 365 专用或 ITAR （Arm 规章中的国际流量）客户，则可以将 IdFix 配置为改用专用规则集。 如果您不确定您是哪种类型的客户，则可以安全地跳过此步骤。 若要将规则集设置为专用，请单击菜单栏中的齿轮图标，然后单击 "**专用**"。
  
## <a name="changing-the-scope-of-the-search-used-by-idfix"></a>更改 IdFix 使用的搜索范围
默认情况下，IdFix 搜索整个目录。 如果需要，您可以将工具配置为搜索特定子树（而不是搜索）。 若要执行此操作，请在菜单栏中，单击 "筛选器" 图标，然后输入一个有效的子树。
  
## <a name="rolling-back-your-changes-by-using-the-idfix-gui"></a>通过使用 IdFix GUI 回滚您的更改
每次单击 "**应用**" 以应用更改时，IdFix 工具将创建一个名为 "事务日志" 的单独文件，其中列出了刚才所做的更改。 您可以使用事务日志回滚在最近的日志中进行的更改，以防您犯错误。 如果在更新过程中出现错误，则可以通过单击 "**撤消**" 来撤消最近应用的更改。 当您单击 "**撤消**" 时，IdFix 将使用事务日志回滚在最近的事务日志中的更改。 有关使用事务日志的详细信息，请参阅[Microsoft 365 IdFix transaction log](idfix-transaction-log.md)。

## <a name="next-step"></a>后续步骤

[设置目录同步](set-up-directory-synchronization.md)
