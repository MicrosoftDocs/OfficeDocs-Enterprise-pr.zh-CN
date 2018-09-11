---
title: Office 365 开发/测试环境中的 GDPR 发现、保护和报告
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: ''
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: 演示 Office 365 中的 GDPR 功能。
ms.openlocfilehash: e58ddc36bf85d791451e2f8097ad65bef4c463e3
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915087"
---
# <a name="gdpr-discovery-protection-and-reporting-in-the-office-365-devtest-environment"></a>Office 365 开发/测试环境中的 GDPR 发现、保护和报告

 **摘要**：演示 Office 365 中的 GDPR 功能。 
  
本文介绍如何在 Office 365 开发/测试环境中配置和演示一般数据保护条例 (GDPR) 的个人身份信息 (PII) 发现、保护和报告。
  
## <a name="phase-1-create-and-configure-your-trial-office-365-subscription"></a>第 1 阶段：创建和配置试用版 Office 365 订阅

首先，按照 [Office 365 开发/测试环境的第 2 阶段](office-365-dev-test-environment.md#phase-2-create-an-office-365-trial-subscription)一文中的步骤操作。

接下来，使用这些步骤来配置电子数据展示管理器：

1. 使用全局管理员帐户登录到 Office 365 试用版租户。
2. 在 Office 365 主页上，单击“安全与合规性”****。
3. 在新的“安全与合规性”选项卡中，单击“权限”**** > “电子数据展示管理器”****。
4. 单击电子数据展示管理器的“编辑”****，然后单击“选择电子数据展示管理器”****。
5. 单击“+ 添加”****，搜索全局管理员帐户名称，并添加全局管理员帐户作为电子数据展示管理器。
6. 单击“完成”**** > “保存”**** > “关闭”****。
  
## <a name="phase-2-add-personally-identifiable-information-to-your-tenant"></a>第 2 阶段：将个人身份信息添加到租户

在此阶段，将使用 PII 为一组示例国际银行帐号 (IBAN) 创建一个文档，并将其存储在 Office 365 开发/测试环境中的 SharePoint Online 网站上。

1. 在本地计算机上打开 Microsoft Word。
2. 将下表粘贴到 Word 文件中，并在本地计算机上将其另存为“IBANs.docx”。
    
    帐号  |国家/地区  |代码 |IBAN  |
    |---------|---------|---------|---------|
    |1     |  奥地利 SEPA      | AT            |AT611904300234573201       |
    |2     |  保加利亚 SEPA       |BG    |BG80BNBG96611020345678      |
    |3     |  丹麦 SEPA      |   DK      |DK5000400440116243      |
    |4     |  芬兰 SEPA      |   FI      |FI2112345600000785         |
    |5     |  法国 SEPA       |   FR      |FR1420041010050500013M02606         |
    |6     |  德国 SEPA      |   DE      |DE89370400440532013000         |
    |7     |  希腊 SEPA       |   GR      |GR1601101250000000012300695         |
    |8     |  意大利 SEPA       |    IT     |GR1601101250000000012300695         |
    |9     |  荷兰 SEPA      |   NL      |    NL91ABNA0417164300     |
    |10     | 波兰 SEPA       |  PL       | PL27114020040000300201355387        |

请注意：此示例数据集源自公开信息，仅用于测试目的。

3. 在浏览器新选项卡中，键入以下内容：**https://**\<YourTenantName\>**.sharepoint.com**
4. 单击“文档”**** 打开此网站的文档库。如果系统提示你体验新的列表，请单击“下一步”**** 直至其完成。
5.  单击“上传”**** > “文件”**** 并选择在步骤 2 中创建的 IBANs.docx。

  
## <a name="phase-3-demonstrate-data-discovery"></a>第 3 阶段：演示数据发现

在此阶段，将演示根据包含 IBAN 的文档内容进行搜索，以查找在第 2 阶段创建和存储的文档。

1. 在“安全与合规性”选项卡中，单击“主页”****，然后单击“搜索和调查”**** > “内容搜索”****。
2. 单击“+”**** 以创建新的搜索项。
3. 在新窗口中，提供以下信息：  
    a. 名称：IBAN 搜索  
    b. 想要我们查找什么?：**选择要搜索的特定网站**（单击“+”****），然后输入网站 URL：**https://**\<YourTenantName\>**.sharepoint.com/**  
    c. 单击“添加”****，然后单击“确认”****。如果看到一条警告，请单击“确认”****。  
    d. 单击“新搜索”**** 窗口中的“下一步”****。  
    e. 对于**想要我们查找什么?**：**SensitiveType:“International Banking Account Number (IBAN)”**，然后单击“搜索”****。

4. 确保在“IBAN 搜索”**** 结果中至少列出一项。


## <a name="phase-4-create-a-custom-sensitive-information-type-via-powershell"></a>第 4 阶段：通过 PowerShell 创建自定义敏感信息类型

在此阶段，将使用 Microsoft PowerShell 为虚构的 Contoso 公司创建一个自定义敏感信息类型。Contoso 使用 Contoso 客户编号 (CCN) 来识别其客户数据库中的每个客户。CCN 包含以下结构：
- 表示创建记录的年份的两位数字。
    - Contoso 成立于 2002 年，因此，最早的可能值为 02。 
- 表示创建记录的合作伙伴机构的三位数字。
    - 可能的机构值的范围是 000 到 999。 
- 表示业务线的字母字符。
    - 可能的值为 a 到 z，且应区分大小写。
- 四位数的序列号。 
    - 可能的序列号值的范围是 0000 到 9999。   

在内部通信、外部通信、文档和其他表单中，Contoso 通常使用 CCN 指代客户。Contoso 需要自定义敏感项类型来检测 Office 365 内容中使用的 CCN，以便对这种个人身份信息形式的使用应用保护。

1. 借助[使用多重身份验证连接到 Office 365 安全与合规中心 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) 中的说明，使用全局管理员帐户的 UPN 连接到安全与合规中心。
2. 运行以下 PowerShell 命令。

     ```
    #Create & start search for sample data
    $searchName = "Sample Customer Information Search"
    $searchQuery = "15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118"
    New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery
    Start-ComplianceSearch -Identity $searchName#Create & start search for sample data
    $searchName = "Sample Customer Information Search"
    $searchQuery = "15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118"
    New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery
    Start-ComplianceSearch -Identity $searchName
    ```
3. 运行以下 PowerShell 命令，并将生成的 GUID 按其所列顺序复制到计算机上打开的记事本实例中。
    ```
    #Generate three unique GUIDs
    Write-Host "GUID1 = "([guid]::NewGuid().Guid)
    Write-Host "GUID2 = "([guid]::NewGuid().Guid)
    Write-Host "GUID3 = "([guid]::NewGuid().Guid)
    ```
4. 在本地计算机上，打开记事本的另一个实例，并粘贴以下内容：

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce"> 
    <RulePack id="GUID1">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id="GUID2" />
    <Details defaultLangCode="en"> 
    <LocalizedDetails langcode="en"> 
    <PublisherName>Contoso Ltd.</PublisherName> 
    <Name>Contoso Rule Package</Name> 
    <Description>Defines Contoso's custom set of classification rules</Description>
    </LocalizedDetails>
    </Details>
    </RulePack>
    <Rules>
    <!-- Contoso Customer Number (CCN) -->
    <Entity id="GUID3" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
    <IdMatch idRef="Regex_contoso_ccn" />
    <Match idRef="Keyword_contoso_ccn" />
    <Match idRef="Regex_eu_date" />
    </Pattern>
    </Entity>
    <Regex id="Regex_contoso_ccn">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</Regex>
    <Keyword id="Keyword_contoso_ccn">
    <Group matchStyle="word">
    <Term caseSensitive="false">customer number</Term>
    <Term caseSensitive="false">customer no</Term>
    <Term caseSensitive="false">customer #</Term>
    <Term caseSensitive="false">customer#</Term>
    <Term caseSensitive="false">Contoso customer</Term>
    </Group>
    </Keyword>
    <Regex id="Regex_eu_date"> (0?[1-9]|[12][0-9]|3[0-1])[\/-](0?[1-9]|1[0-2]|j\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)? |feb(ruary|ruari|rero|braio|ruar|br)?|f\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\x00e4rz|maart|apr(ile|il)?|abr(il)?|avril |may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)? |nov(ember|iembre|embre|embro)?|dec(ember)?|dic(iembre|embre)?|dez(ember|embro)?|d\x00e9c(embre)?)[ \/-](19|20)?[0-9]{2}</Regex>
    <LocalizedStrings>
    <Resource idRef="GUID3">
    <Name default="true" langcode="en-us">Contoso Customer Number (CCN)</Name>
    <Description default="true" langcode="en-us">Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date</Description>
    </Resource>
    </LocalizedStrings>
    </Rules>
    </RulePackage>
    ```
5. 将步骤 4 的 XML 文本中的 GUID1、GUID2 和 GUID3 的值替换为步骤 3 中的值，然后将该内容保存在本地计算机上，并命名为 ContosoCCN.xml。
6. 填写 ContosoCCN.xml 文件的路径并运行以下命令。
    ```
    #Create new Sensitive Information Type
    $path="<path to the ContosoCCN.xml file, such as C:\Scripts\ContosoCCN.xml>"
    New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path $path -Encoding Byte -ReadCount 0)
    ```
7. 在“安全与合规性”选项卡中，单击“分类”**** > “敏感信息类型”****。应该能看到列表中的 Contoso 客户编号 (CCN)。

## <a name="phase-5-demonstrate-data-protection"></a>第 5 阶段：演示数据保护

对 Office 365 中的个人信息的保护包括使用数据丢失防护 (DLP) 功能。借助 Office 365 安全与合规中心中的 DLP 策略，可以自动保护 Office 365 内的敏感信息。

有多种方式可以应用保护。引导和提高在你的环境中存储欧盟常驻数据的位置的意识以及允许员工处理该数据的方式，这表示使用 Office 365 DLP 进行信息保护的一个级别。

在此阶段，将创建一个新的 DLP 策略，并演示它是如何应用于第 2 阶段中存储在 SharePoint Online 中的 IBANs.docx 文件，以及何时尝试发送包含 IBAN 的电子邮件。

1. 在浏览器的“安全与合规性”选项卡中，单击“主页”****。
2. 单击“数据丢失防护”**** > “策略”****。
3. 单击“+ 创建策略”****。
4. 在“从模板开始或创建自定义策略”**** 中，单击“自定义”**** > “自定义策略”**** > “下一步”****。
5. 在“为策略命名”**** 中，提供以下详细信息，然后单击“下一步”****：a. 名称：“欧盟公民 PII 策略”**** b.说明：“保护欧洲公民的个人身份信息”****
6. 在“选择位置”**** 中，选择“Office 365 中的所有位置”****。这将包含 Exchange 电子邮件中的内容以及 OneDrive 和 SharePoint 文档。然后单击“下一步”****。
7. 在“自定义想要保护的内容类型”**** 中，单击“查找包含以下内容的信息:”****，然后单击“编辑”****。
8. 在“选择要保护的内容类型”**** 中，单击“添加”**** > “敏感信息类型”****。
9. 在“敏感信息类型”**** 中，单击“+ 添加”****。
10. 在“敏感信息类型”**** 中，搜索“IBAN”****，选中“国际银行帐号(IBAN)”**** 复选框，然后单击“添加”****。
11. 确认已添加“国际银行帐号(IBAN)”**** 敏感信息类型，然后单击“完成”****。
12. 在“内容包含”**** 中，确认已添加敏感信息类型，然后单击“保存”****。
13. 在“自定义想要保护的内容类型”**** 中，确认“查找包含以下内容的信息:”**** 包含“国际银行帐号(IBAN)”****，然后单击“下一步”****。
14. 在“当共享的内容包含以下值时检测:”**** 中，将值从“10”**** 更改为“1”****，然后单击“下一步”****。
15. 在“要启用策略还是先进行测试?”**** 中，选择以下设置，然后单击“下一步”****。  
    a. 选择“我想先进行测试”**** 选项  
    b. 选中“在测试模式下显示策略提示”**** 复选框 
16. 在“查看设置”**** 中，在查看设置后单击“创建”****。注意：创建新的 DLP 策略后，需要一段时间才能生效。
17. 在本地计算机上打开浏览器的专用实例。
18. 在地址栏中，键入 **https://**\<YourTenantName\>**.sharepoint.com**，然后使用全局管理员帐户登录。
19. 单击“文档”****。
20. 单击名为“IBANs.docx”的文件。可以看到“Policy tip for IBANs.docx”。IBANs.docx 文件与外部收件人进行了共享，这违反了 DLP 策略。 
21. 在地址栏中，键入：**https://outlook.office365.com**
22. 单击“新建”**** - “电子邮件”****，并提供以下内容：  
    - **收件人**：\<个人电子邮件地址\>  
    - **主题**：GDPR 测试  
    - **正文**：复制下面显示的表中的值。
  
        |帐号  |国家/地区  |代码 |IBAN  |
        |---------|---------|---------|---------|
        |1     |  奥地利 SEPA      | AT            |AT611904300234573201       |
        |2     |  保加利亚 SEPA       |BG    |BG80BNBG96611020345678      |
        |3     |  丹麦 SEPA      |   DK      |DK5000400440116243      |
        |4     |  芬兰 SEPA      |   FI      |FI2112345600000785         |
        |5     |  法国 SEPA       |   FR      |FR1420041010050500013M02606         |
        |6     |  德国 SEPA      |   DE      |DE89370400440532013000         |
        |7     |  希腊 SEPA       |   GR      |GR1601101250000000012300695         |
        |8     |  意大利 SEPA       |    IT     |GR1601101250000000012300695         |
        |9     |  荷兰 SEPA      |   NL      |   NL91ABNA0417164300      |
        |10     | 波兰 SEPA       |  PL       | PL27114020040000300201355387        |

请注意：此示例数据集源自公开信息，仅用于测试目的。

23. 可以看到，DLP 策略识别了包含 IBAN 的电子邮件的正文，并在邮件窗口顶部提供了策略提示。
24. 关闭浏览器专用实例。


## <a name="phase-6-demonstrate-reporting"></a>第 6 阶段：演示报告
 
在此阶段，将基于在第 5 阶段配置的 DLP 策略来演示 Office 365 报告。

   1. 在浏览器的“安全与合规性”选项卡中，单击“主页”****。
   2. 单击“报告”**** > “仪表板”**** > “DLP 策略匹配项”****。
   3. DLP 策略可帮助识别和保护组织的敏感信息。例如，在报告中可以看到，策略标识了存储在 SharePoint Online 中的包含 IBAN 的文档。
  
## <a name="see-also"></a>另请参阅

[针对 GDPR 的 Office 365 信息保护](office-365-information-protection-for-gdpr.md)

[GDPR for Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/gdpr?toc=/microsoft-365/enterprise/toc.json)
