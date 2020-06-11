---
title: 同时将多个用户添加到 Microsoft 365-管理员帮助
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
ms.assetid: 1f5767ed-e717-4f24-969c-6ea9d412ca88
description: '了解如何从电子表格或其他 CSV 格式的文件中的列表向 Microsoft 365 for business 中添加多个用户。 观看 YouTube 上的视频，说明如何将帐户添加到 Microsoft 365。 在此过程结束时，拥有帐户的每位用户都将拥有一个 Microsoft 365 邮箱。 '
ms.openlocfilehash: 88c83b7163bfa6d389995704595d80458ddc8198
ms.sourcegitcommit: ff1d21fe5eb8eba7a65d250aa37aadc8f503a10a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "44699239"
---
# <a name="add-several-users-at-the-same-time-to-microsoft-365---admin-help"></a>同时将多个用户添加到 Microsoft 365-管理员帮助

团队中的每个人都需要用户帐户，才能登录并访问 Microsoft 365 服务，例如电子邮件和 Office。 如果有很多人，则可以从 Excel 电子表格或以 CSV 格式保存的其他文件中一次添加所有帐户。 [不确定哪种 CSV 格式？](add-several-users-at-the-same-time.md#__toc316652088)
  
> [!NOTE] 
> 如果未使用新的 Microsoft 365 管理中心，可通过选择“**试用新的管理中心**”切换按钮（位于主页顶部）将其打开。

## <a name="add-multiple-users-in-the-microsoft-365-admin-center"></a>在 Microsoft 365 管理中心中添加多个用户

1. 使用工作或学校帐户登录 Microsoft 365。 
    
2. 在 "管理中心" 中，选择 "**用户** \> **活动用户**"。

3. 选择 "**添加多个用户**"。

4. 在 "**导入多个用户**" 面板上，您可以选择下载带有或不带填充样本数据的示例 CSV 文件。 
    
    您的电子表格需要包含与样本1（用户名、名字等）**完全相同的列标题**。如果使用模板，请在文本编辑工具（如记事本）中打开它，并考虑仅保留第1行中的所有数据，并且仅在第2行和更低的行中输入数据。 
    
    您的电子表格还需要包含用户名的值（如 bob@contoso.com）和每个用户的显示名称（如 Bob 凯利）。 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. 在框中输入文件路径，或选择 "**浏览**" 浏览 CSV 文件位置，然后选择 "**验证**"。
  
    如果文件有问题，则会在面板中显示该问题。 您还可以下载日志文件。
    
5. 在 "**设置用户选项**" 对话框中，您可以设置登录状态，并选择将分配给所有用户的产品许可证。 
    
6. 在 "**查看您的结果**" 对话框中，您可以选择将结果发送给您自己或其他用户（密码将为纯文本），您可以查看创建的用户数，以及是否需要购买更多许可证以分配给某些新用户。 

## <a name="next-steps"></a>后续步骤
<a name="bk_preview"> </a>

- 现在，这些人拥有帐户，需要在[电脑或 Mac 上下载并安装或重新安装 Microsoft 365 或 Office 2016](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658)。 你的团队中的每个人都可以在最高5台电脑或 Mac 上安装 Microsoft 365。 
    
- 每个人还可以在最大5个平板电脑和5个电话（例如 Iphone、Ipad 和 Android 电话和平板电脑）上的[移动设备上设置 Office 应用和电子邮件](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f)。 这样一来，他们就可以从任何位置编辑 Office 文件。 
    
    有关安装步骤的端到端列表，请参阅[设置 Microsoft 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) 。 
    
## <a name="more-information-about-how-to-add-users-to-microsoft-365"></a>有关如何将用户添加到 Microsoft 365 的详细信息
<a name="bk_preview"> </a>

### <a name="not-sure-what-csv-format-is"></a>不确定哪种 CSV 格式？
<a name="__toc316652088"> </a>

CSV 文件是一个包含以逗号分隔的值的文件。 您可以使用任何文本编辑器或电子表格程序（如 Excel）创建或编辑此类文件。
  
您可以将[此示例电子表格](https://www.microsoft.com/download/details.aspx?id=45485)作为起始点下载。 请记住，Microsoft 365 要求在第一行中有列标题，因此不要将其替换为其他内容。 
  
使用新名称保存该文件，并指定 CSV 格式。
  
![如何将 Excel 中的文件保存为 CSV 格式的图像](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
保存文件时，您可能会收到提示，如果您以 CSV 格式保存文件，则工作簿中的某些功能将丢失。 这没关系。 单击" **是**"即可继续。 
  
![您可能会收到的提示的图片，询问您是否确实要将文件保存为 CSV 格式](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>有关设置电子表格格式的提示
<a name="__toc314595848"> </a>

- **是否需要与示例电子表格中的列标题相同？** 是的。 示例电子表格在第一行中包含列标题。 这些标题是必需的。 对于要添加到 Microsoft 365 中的每个用户，在标题下创建一行。 如果添加、更改或删除任何列标题，Microsoft 365 可能无法从文件中的信息创建用户。 
    
- **如果我没有每个用户所需的全部信息，该怎么办？** 用户名和显示名称是必需的，并且您无法添加不包含此信息的新用户。 如果没有其他信息（如传真），您可以使用空格加上逗号，以指示该字段应保留为空。 
    
- **电子表格是否可以小到多？** 电子表格必须至少有两行。 一个用于列标题（用户数据列标签），另一个用于用户。 行数不能超过251。 如果需要导入多于250个用户，可以创建多个电子表格。 
    
- **我可以使用哪些语言？** 创建电子表格时，可以输入任何语言或字符形式的用户数据列标签，但不能更改标签的顺序，如示例中所示。 然后，可以使用任何语言或字符将条目输入到字段中，并将文件保存为 Unicode 或 UTF-8 格式。 
    
- **如果我要从不同的国家或地区添加用户，该怎么办？** 为每个区域创建单独的电子表格。 您需要逐步完成每个电子表格的 "批量添加用户" 向导，为所使用的文件中包含的所有用户提供一个位置。 
    
- **对我可以使用的字符数是否有限制？** 下表显示了示例电子表格中每个用户数据列标签和最大字符长度。 
    
|**用户数据列标签**|**最大字符长度**|
|:-----|:-----|
|User Name （必需）  <br/> |79，其中包含 name@domain 格式的 at 符号（@ \<extension\> ）。 用户的别名不能超过50个字符，并且域名不能超过48个字符。  <br/> |
|名字  <br/> |64  <br/> |
|姓氏  <br/> |64  <br/> |
|显示名称（必需）  <br/> |256  <br/> |
|职务  <br/> |64  <br/> |
|Department  <br/> |64  <br/> |
|办公室号码  <br/> |128  <br/> |
|办公室电话  <br/> |64  <br/> |
|Mobile Phone － 移动电话  <br/> |64  <br/> |
|传真  <br/> |64  <br/> |
|地址  <br/> |1023  <br/> |
|City  <br/> |128  <br/> |
|省/自治区/直辖市  <br/> |128  <br/> |
|邮政编码  <br/> |40  <br/> |
|国家或地区  <br/> |128  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-microsoft-365"></a>将用户添加到 Microsoft 365 时仍遇到问题？

- **请仔细检查电子表格的格式是否正确。** 检查列标题以确保它们与示例文件中的标题相匹配。 请确保遵循字符长度的规则，并使用逗号分隔每个字段。 
    
- **如果你在 Microsoft 365 中未立即看到新用户，请等待几分钟。** 在 Microsoft 365 中的所有服务之间进行更改可能需要一些时间。 
    
## <a name="related-articles"></a>相关文章

[将用户逐个或批量添加到 Microsoft 365](https://docs.microsoft.com/office365/admin/add-users/add-users)




