---
title: 恢复用户邮箱中已删除的项目 - 管理员帮助
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: eb15194b-63ec-41b0-8d90-1823d3f558e4
description: '本文是针对管理员。未用户永久删除项目从其 Outlook 邮箱？用户后希望其，但无法恢复。您可以恢复清除的邮件，如果其尚未已从用户的邮箱永久删除。 '
ms.openlocfilehash: abfc0a1a35d8e694197e12d05a2206dd4e3eb37a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539596"
---
# <a name="recover-deleted-items-in-a-user-mailbox---admin-help"></a>恢复用户邮箱中已删除的项目 - 管理员帮助

**本文是针对管理员。您正在尝试恢复已删除的项目在您自己的邮箱？** 请尝试下列选项之一：
- [在 Outlook for Windows 中恢复已删除项目](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
- [在 Outlook Web App 中恢复已删除项目或电子邮件](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
- [在 web 上的 Outlook 中还原已删除电子邮件](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
- [Outlook.com](https://go.microsoft.com/fwlink/p/?LinkID=623435)
   
未用户永久删除项目从其 Outlook 邮箱？用户后希望其，但无法恢复。您可以恢复清除的邮件，如果其尚未已从用户的邮箱永久删除。执行此操作使用就地电子数据展示工具在 Exchange Online 中搜索已删除电子邮件和其他项目 — 和如联系人、 日历约会和任务 — 用户的邮箱中。如果您发现的已删除的项目，可以将其导出到 PST 文件 （也称为 Outlook 数据文件），用户可以用它返回到其邮箱还原项目。
  
下面是恢复已删除邮件用户的邮箱中的步骤。将此花费？第一次可能需要 20 或 30 分钟才能完成所有正尝试恢复的步骤，具体取决于您的项目数。
  
> [!NOTE]
> 您必须是**Exchange 管理员**或 Office 365 中的**全局管理员**也是 Organization Management 角色组的成员在 Exchange Online 以执行本文中的步骤。有关详细信息，请参阅[有关 Office 365 管理员角色](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)。 
  
## <a name="step-1-assign-yourself-ediscovery-permissions"></a>步骤 1： 将自己分配电子数据展示权限
<a name="step1"> </a>

第一步是将自己分配所需的权限在 Exchange Online，以便您可以使用就地电子数据展示工具搜索用户的邮箱。您只需执行一次。如果您必须在将来搜索另一个邮箱，则可以跳过此步骤。
  
1. 使用您的工作或学校帐户[从何处登录到 Office 365 的业务](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4)。 
    
2. 选择应用程序启动器图标![Office 365 中的应用程序启动器图标](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)左上角中，单击**管理**。
    
3. 在 Office 365 管理中心的左侧导航中，展开**管理中心**，，然后单击**Exchange**。
    
    ![Admin center 列表](media/7d308eb7-ba63-4156-a845-3770facc5de4.PNG)
  
4. 在 Exchange 管理中心中，单击**权限**，然后单击**管理员角色**。
    
5. 在列表视图中，选择**发现管理**，，然后单击**编辑**![编辑图标](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)。
    
    ![将自己添加到在 EAC 中的发现管理角色组](media/e5c98e93-d6a0-40c5-a143-bac956eedaa7.png)
  
6. **角色组**中，在**成员**下单击**添加**![添加图标](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。
    
7. 在**选择成员**，从名称的列表中选择您自己，单击**添加**，然后单击**确定**。
    
    > [!NOTE]
    > 您还可以添加您是成员，如组织管理或 TenantAdmins 组。如果您将添加一个组，该组的其他成员将分配所需的权限运行就地电子数据展示工具。 
  
8. **角色组**中，单击**保存**。
    
9. 注销 Office 365。
    
    您必须先注销，使新的权限生效开始下一步之前。
    
> [!CAUTION]
> 发现管理角色组的成员可以访问敏感的消息内容。这包括在您的组织中搜索所有邮箱和预览搜索结果 （和其他邮箱项目），将结果复制到发现邮箱，将搜索结果导出到 PST 文件。 
  
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-2-search-the-users-mailbox-for-deleted-items"></a>步骤 2： 搜索已删除邮件的用户的邮箱
<a name="step2"> </a>

当您运行就地电子数据展示搜索时，您所搜索的邮箱中可恢复邮件文件夹都会自动包括在搜索。可恢复邮件文件夹是永久删除的项目存储在何处直到他们正在清除 （永久性删除） 从邮箱。因此，如果尚未已清除项目，您应能够找到使用就地电子数据展示工具。
  
1. 使用您的工作或学校帐户[从何处登录到 Office 365 的业务](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4)。 
    
2. 选择应用程序启动器图标![Office 365 中的应用程序启动器图标](media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png)左上角中，单击**管理**。
    
3. 在 Office 365 管理中心的左侧导航中，展开**管理**，然后单击**Exchange**。
    
4. 在 Exchange 管理中心中，单击**合规性管理**，单击**就地电子数据展示&amp;保留**，然后单击**新建**和![添加图标](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。
    
    ![单击在 EAC 中，在合规性管理页上的就地电子数据展示和保留](media/9d9ff0f5-b9be-45b8-8b5e-6037a856b0a8.png)
  
5. 在**名称和说明**页上，键入名称 （如正在恢复电子邮件的用户的名称） 的搜索和可选说明，然后单击**下一步**。
    
6. 在**邮箱**页上，单击**指定邮箱搜索**，，然后单击**添加**![添加图标](media/8ee52980-254b-440b-99a2-18d068de62d3.gif)。
    
    ![单击指定邮箱搜索来搜索特定邮箱](media/83879a40-5e5c-49a8-be3b-c0023d197588.png)
  
7. 查找和选择要恢复已删除电子邮件的用户的名称，单击**添加**，然后单击**确定**。
    
8. 单击"下一步"。
    
    将显示**搜索查询**页。这是在其中定义将帮助您在用户的邮箱中查找丢失的项目的搜索条件。 
    
9. 在**搜索查询**页上，填写以下字段： 
    
  - **包含所有内容**选择此选项可在搜索结果中的用户的邮箱中包含所有内容。如果选择此选项，则无法指定附加搜索条件。 
    
  - **筛选器基于条件**选择此选项可指定搜索条件，包括关键字，开始和结束日期、 发件人和收件人地址和邮件类型。 
    
    ![构建基于条件，如关键字、 日期范围、 收件人和邮件类型搜索](media/ee47b833-9122-46a0-85e6-fcbe25be0dd5.png)
  
|**字段**|**使用此到...**|
|:-----|:-----|
|![粉红色圆中的第一](media/a4da261d-2516-48c5-b58a-9c452b9086b8.png)           <br/> |指定关键字、 日期范围、 收件人和邮件类型。  <br/> |
|![第二粉红色圆中。](media/de3c1ab4-4f01-4026-b1ba-3265bdb32a89.png)           <br/> |搜索的关键字或短语的邮件并使用逻辑运算符，如**AND**或**OR**。  <br/> |
|![第三步中粉红色圆。](media/60fa378c-6ac1-4cbd-a782-2fa7ca619dc6.png)           <br/> |搜索的邮件发送或接收日期范围内。  <br/> |
|![粉红色圆中的 4 号。](media/1a0ff2ce-0942-405a-94e3-9bfeb1e5059e.png)           <br/> |搜索从收到或发送到特定的某个人的邮件。  <br/> |
|![数字五粉红色圆。](media/878cc815-0165-49ba-a1ee-9236e5980403.png)           <br/> |搜索所有消息类型，或选择特定的。  <br/> |
   
    > [!TIP]
    >  Here's a few tips about how to build a search query to find missing items. Try to get as much information from the user to help you create a search query so you can find what you're looking for. >  If you not sure how to find a missing message, consider using the **Include all content** option. The search results will include all items in the user's Recoverable Items folder, including the hidden folder (called the Purges folder) that contain items that have been purged by the user. Then you can go to Step 3, copy the results to a discovery mailbox, and look at the message in the hidden folder. >  If you know approximately when the missing message was originally sent or received by the user, use the **Specify start date** and **Specify end date** options to provide a date range. This will return all messages sent or received by the user within that date range. Specifying a date range is a really good way to narrow the search results. >  If you know who sent the missing email, use the **From** box to specify this sender. >  If you want to narrow the search results to different types of mailbox items, click **Select message types**, click **Select the message types to search**, and then choose a specific message type to search for. For example, you can search only for calendar items or contacts. Here's a screenshot of the different message types you can search for; the default is to search for all message types. 
  
    Click **Next** when you've completed the **Search query** page. 
    
10. 在**就地保留设置**页上单击**完成**开始搜索。若要恢复已删除电子邮件，没有理由将置于保持状态的用户的邮箱。 
    
    开始搜索后，Exchange 将显示估计的总大小和将返回您指定的条件基于搜索的项目数。
    
11. 选择您刚刚创建的搜索，然后单击**刷新**![刷新](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)以更新的详细信息窗格中显示的信息。**估计成功**的状态指示搜索已完成。Exchange 还会显示总项目数 （和尺寸） 中找到的搜索将基于您在步骤 9 中指定的搜索条件的估计值。 
    
12. 在详细信息窗格中，单击**预览搜索结果**，以查看找到的项目。这可以帮助您找到所需的项。如果您发现您尝试恢复的项，请转到步骤 4，将搜索结果导出到 PST 文件。 
    
    ![单击要查看您正在尝试恢复的项目的预览搜索结果](media/a2cea921-dafa-45d6-97d4-ae45a226b8d3.png)
  
13. 如果没有找到所需，您可以修改搜索条件通过选择搜索，单击**编辑**![编辑图标](media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)，然后单击**搜索查询**。更改搜索条件，然后重新运行搜索。
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="optional-step-3-copy-the-search-results-to-a-discovery-mailbox"></a>（可选）步骤 3： 将搜索结果复制到发现邮箱
<a name="step3"> </a>

如果您无法通过预览搜索结果中查找项目或想要查看用户的可恢复项目文件夹中的哪些项目，然后您可以将搜索结果复制到 （称为发现邮箱） 的特殊邮箱，然后打开该邮箱在 Outlook web t 上o 查看实际的项目。复制搜索结果的最佳原因是使您可以查看用户的可恢复项目文件夹中的项目。多个可能的您尝试恢复的项目位于清除子文件夹中。 
  
1. 在 Exchange 管理中心，转到**合规性管理** \> **就地电子数据展示&amp;保留**。
    
2. 在搜索的列表中，选择您在步骤 2 中创建的搜索。
    
3. 单击**搜索**![搜索](media/c94e8591-7044-4650-a0d1-c57c0633ab4f.png)，然后从下拉列表中单击**复制搜索结果**。 
    
    ![单击搜索，然后单击复制搜索结果](media/7888df82-94b4-4e44-8a53-f66854dc7c86.png)
  
4. 在**复制搜索结果**页上，单击**浏览**。
    
    ![保留未选择时恢复已删除项的复选框](media/37f27999-a5b2-4fed-87e2-bad6dc23cdae.png)
  
5. **显示名称**，下单击**发现搜索邮箱**，然后单击**确定**。
    
    ![将搜索结果复制到默认发现搜索邮箱](media/36e8ef47-0035-4982-9ed6-426719c5f9ec.png)
  
    > [!NOTE]
    > 发现搜索邮箱是自动创建 Office 365 组织中的默认发现邮箱。 
  
6. 返回在**复制搜索结果**页上，单击**复制**启动的过程将搜索结果复制到发现搜索邮箱。 
    
    ![单击复制以将搜索结果复制到发现搜索邮箱](media/71307a9d-f7a1-4e01-ae37-1d49040cc3fd.png)
  
7. 单击**刷新**![刷新](media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png)要更新的详细信息窗格中显示的复制状态的信息。 
    
8. 复制完成后，请单击**打开**以打开要查看搜索结果的发现搜索邮箱。 
    
    ![单击打开以转到要查看搜索结果的发现搜索邮箱](media/6cc81e0f-ceed-4464-9040-79b6f920de35.png)
  
    搜索结果复制到发现搜索邮箱放在具有相同名称的就地电子数据展示搜索的文件夹中。您可以单击该文件夹中显示的项目文件夹。
    
    ![发现搜索邮箱; 中的搜索结果只能由管理员进行恢复清除文件夹中的项目](media/2ef8e5fb-3e63-4f62-938e-307efe9f6998.gif)
  
    搜索运行时，还搜索用户的可恢复项目文件夹。也就是说，如果可恢复邮件文件夹中的项目满足搜索条件，它们都包含在搜索结果中。删除文件夹中项目是用户 （通过从已删除邮件文件夹中删除项目或通过选择它，按**Shift + Delete**永久删除项目。用户可以使用 Outlook 或 Outlook web 上的恢复已删除邮件工具恢复删除文件夹中的项目。清除文件夹中的项目是用户使用恢复已删除邮件工具清除的项目或他们已自动清除应用于邮箱的策略的项目。在任一情况下，只有管理员可以恢复清除文件夹中的项目。 
    
    > [!TIP]
    > 如果用户找不到已删除的项使用可恢复项目工具中，但该项目是仍然可以恢复 （这意味着，它不起作用已从永久删除邮箱），它很有可能位于清除文件夹。因此，请务必查看您正在尝试恢复的用户的已删除项目清除文件夹中。 
  
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-4-export-the-search-results-to-a-pst-file"></a>步骤 4： 将搜索结果导出到 PST 文件
<a name="step4"> </a>

找到您尝试恢复的用户的项目后下, 一步是将结果导出到 PST 文件在步骤 2 中运行的搜索。用户将使用的下一步此 PST 文件还原到其邮箱已删除的项。
  
1. 在 Exchange 管理中心，转到**合规性管理** \> **就地电子数据展示&amp;保留**。
    
2. 在搜索的列表中，选择您在步骤 2 中创建的搜索。
    
3. 单击**导出到 PST 文件**。
    
    ![单击导出到 PST 文件](media/4e59ae17-4541-43f4-a6d1-1f8b9ba9404b.png)
  
4. 如果提示您安装电子数据展示导出工具，请单击**运行**。
    
5. 在电子数据展示 PST 导出工具，单击**浏览**以指定要下载 PST 文件的位置。 
    
    ![电子数据展示 PST 导出工具](media/17274d27-992e-4034-8133-8f793f554e6c.png)
  
    选项以启用消除并包括不可搜索的项目，则可将其忽略。
    
6. 单击**启动**PST 文件下载到您的计算机。 
    
    **电子数据展示 PST 导出工具**显示有关导出过程的状态信息。导出完成后，您可以访问它已下载的位置中的文件。 
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="step-5-restore-the-recovered-items-to-the-users-mailbox"></a>步骤 5： 还原到用户邮箱的已恢复的项目
<a name="step5"> </a>

最后一步是使用已导出步骤 4 到用户的邮箱还原已恢复的项目中的 PST 文件。向用户发送的 PST 文件后，由用户打开 PST 文件，然后将已恢复的项目移至另一个文件夹中其邮箱执行此步骤中的其余部分。有关分步说明，您还可以发送用户链接到本主题：[打开和关闭 Outlook 数据文件 (.pst)](https://support.office.com/article/381b776d-7511-45a0-953a-0935c79d24f2)。也可以向用户发送到下面的[还原删除的邮箱使用 PST 文件的项目](recover-deleted-items-in-a-mailbox.md#restoredeleteditems)部分的链接并请求其将执行这些步骤。 
  
 **向用户发送的 PST 文件**
  
您需要执行的最后一步向用户，第 4 步中发送已导出的 PST 文件。有几种方法来执行此操作：
  
- 附加到电子邮件的 PST 文件。如果 Outlook 配置为阻止 PST 文件，然后您将需要 zip 文件，然后将其附加到邮件。下面是如何：
    
1. 在 Windows 资源管理器或文件资源管理器中，浏览到 PST 文件。
    
2. 右键单击该文件中，，然后选择**发送到** \> **压缩 (zip) 文件夹**。Windows 创建一个新的 zip 文件，并为其为 PST 文件相同的名称。
    
3. 将压缩的 PST 文件附加至的电子邮件，并将其发送到的用户，然后可以通过单击它解压缩的文件。
    
- 将 PST 文件复制到用户可以访问和检索的共享文件夹。
    
若要还原到其邮箱已删除的项目的用户执行下一节中的步骤。
  
 **邮箱 PST 文件中还原已删除的项目**
  
您必须使用 Outlook 桌面应用程序使用 PST 文件中还原已删除的邮件。您不能使用 Outlook Web App 或 Outlook web 上的打开 PST 文件。
  
1. 在 Outlook 2013 或 Outlook 2016 中，单击**文件**选项卡。 
    
2. 单击**打开&amp;导出**，，然后单击**打开 Outlook 数据文件**。
    
3. 浏览到保存您的管理员发送的 PST 文件的位置。
    
4. 选择 PST，然后单击**打开**。
    
    在 Outlook 中的左侧导航栏中显示的 PST 文件。
    
    ![在 Outlook 中的左侧导航栏中显示的 PST 文件](media/c9389392-d08a-4aa7-848c-4986d448b0f2.png)
  
5. 单击箭头以展开 PST 文件，以找到您想要恢复的项目下的文件夹。
    
    ![在您想要恢复的项目清除文件夹中查找](media/d4e372d9-ac23-4e95-8639-d8da690fefa7.png)
  
    > [!TIP]
    > 在您想要恢复的项目的清除文件夹中查找。这是一个隐藏的文件夹中清除项目移动到。它可能是管理员恢复位于该文件夹中的项目。 
  
6. 右键单击您想要恢复，然后单击**移动**的项目\>**其他文件夹**。
    
    ![单击移动，然后选择其他文件夹](media/090063df-2aa0-444a-8e47-abd6fe6cf7a8.png)
  
7. 若要将项目移至收件箱，单击**收件箱**，然后单击**确定**。
    
    **提示：** 若要恢复其他类型的项，请执行下列选项之一： 
    
  - 要恢复的日历项目，请右键单击它，，然后单击**移动** \> **其他文件夹** \> **日历**。
    
  - 要恢复联系人，请右键单击它，，然后单击**移动** \> **其他文件夹** \> **联系人**。
    
  - 要恢复任务，请右键单击它，，然后单击**移动** \> **其他文件夹** \> **任务**。
    
![选择要移动其他类型的项的文件夹](media/f8290131-43f2-46f1-bc07-228c2d83b96c.png)
  
    Note that calendar items, contacts, and tasks are located directly in the Purges folder, and not in a Calendar, Contacts, or Tasks subfolder. However, you can sort by **Type** to group similar types of items. 
    
8. 完成后恢复已删除邮件，右键单击的 PST 文件中的左侧导航栏和**关闭"PST 文件的名称"** 选择。
    
[返回顶部](recover-deleted-items-in-a-mailbox.md#__top)
  
## <a name="more-information"></a>详细信息
<a name="moreinfo"> </a>

- 有可能，用户可以恢复永久删除的项目，如果没有过期项目已删除的邮件保留期限。管理员可以为可恢复邮件文件夹中的指定长项目供恢复。例如，可能有删除任何已在 30 天，用户的已删除邮件文件夹中的策略和允许用户在恢复到另一个 14 天为止可恢复项目文件夹中的项目的其他策略。但是，此 14 天后，您仍可以恢复使用本主题中介绍的过程的用户的邮箱中的项目。
    
- 如果它尚未已清除，并且该项目已删除的邮件保留期限没有过期，用户可以恢复已删除的邮件。为了帮助恢复已删除的项目在他们的邮箱的用户，其指向以下主题之一：
    
  - [在 Outlook for Windows 中恢复已删除项目](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)
    
  - [在 Outlook 2010 中的恢复已删除邮件](https://support.office.com/article/cd9dfe12-8e8c-4a21-bbbf-4bd103a3f1fe)
    
  - [在 Outlook Web App 中恢复已删除项目或电子邮件](https://support.office.com/article/c3d8fc15-eeef-4f1c-81df-e27964b7edd4)
    
  - [在 web 上的 Outlook 中还原已删除电子邮件](https://support.office.com/article/a8ca78ac-4721-4066-95dd-571842e9fb11)
    
  - [恢复在 Outlook 中的删除的联系人](https://support.office.com/article/51c83288-6888-4dcd-8c99-4932daabf643)
    
  - [在 Outlook.com 中还原已删除电子邮件](https://go.microsoft.com/fwlink/p/?LinkID=623435)
    
[Return to top](recover-deleted-items-in-a-mailbox.md#__top)
  

