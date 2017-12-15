---
title: "连接到 Office 365 PowerShell"
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
- LIL_Placement
- O365ITProTrain
- DecEntMigration
- apr17entnews
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: "摘要： 连接到 Office 365 单位使用 Office 365 PowerShell 从命令行执行 Office 365 管理的中心任务。"
ms.openlocfilehash: 3ac368a3d3584c15e1d0c26104616e8258a78e7b
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-office-365-powershell"></a>连接到 Office 365 PowerShell

 **摘要：**连接到您的 Office 365 组织使用 Office 365 PowerShell 从命令行执行 Office 365 管理任务。
  
Office 365 PowerShell 允许您从命令行管理您 Office 365 的设置。连接到 Office 365 PowerShell 是一个简单的三步过程，安装必需的软件，运行所需的软件，然后连接到您的 Office 365 组织。 

请注意，这些连接的说明主题[Azure 与 active Directory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113)中的相同。
  
> [!TIP]
> **新到 PowerShell？**请参阅[视频 PowerShell 概述](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)，LinkedIn 学习者。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>在开始之前，您需要知道什么？

- 估计完成时间：5 分钟
    
- 可以使用下列 Windows 版本：
    
  - Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >使用 64 位版本的 Windows。在 10 月的 2014年已停产的 32 位版本 Microsoft Azure 活动目录模块用于 Windows PowerShell 支持。
    
-  Office 365 的工作或学校对使用这些过程需要 Office 365 管理角色的成员的帐户。有关详细信息，请参阅[有关 Office 365 管理角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。
    
## <a name="step-1-install-required-software"></a>步骤 1：安装所需软件

这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。
  
1.  安装 64 位版本的 Microsoft 联机服务注册助理： [Microsoft 在线服务登录的助手为 IT 专业人员的一项](https://go.microsoft.com/fwlink/p/?LinkId=286152)。
    
2. 使用以下步骤安装 64 位版本的 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块：
    
  - 打开 [Azure Active Directory 连接](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185)网页。
    
  - 在页面底部的**下载中的文件**， **AdministrationConfig-V1.1.166.0-GA.msi**文件中，单击**下载**，然后安装它。
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a>步骤 2：打开 Windows Azure Active Directory 模块

1. 使用以下某个基于 Windows 版本的方法查找并打开 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块：
    
  - **「 开始 」 菜单**在桌面上，单击**开始**，然后键入 Azure。
    
  - **没有"开始"菜单** 使用下列任一方法搜索"Azure"：
    
  - 在"开始"屏幕中，单击空白区域，并键入"Azure"。
    
  - 在桌面或"开始"屏幕上，按下 Windows 键 + Q。在"搜索"超级按钮中，键入"Azure"。
    
  - 在桌面或开始屏幕上，将光标移动到右上角或刷从右向左，从屏幕来显示魅力的右边缘。选择搜索超级按钮，然后键入**Azure**。
    
2. 在结果中，单击"用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块"。
    
## <a name="step-3-connect-to-your-office-365-subscription"></a>步骤 3：连接到 Office 365 订阅
<a name="step3"> </a>

仅使用 *帐户名和密码*  连接：
  
1. 在"用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块"命令窗口中，运行以下命令。
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. 在"Windows PowerShell 凭据请求"对话框中，键入您的 Office 365工作或学校帐户 用户名和密码，然后单击"确定"。
    
使用 *多重身份验证 (MFA)*  进行连接的具体步骤：
  
1. 在"用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块"命令窗口中，运行以下命令。
    
  ```
  Connect-MsolService
  ```

2. 在"Azure Active Directory PowerShell"对话框中，键入你的 Office 365工作或学校帐户 用户名和密码，然后单击"登录"。
    
3. 按照"Azure Active Directory PowerShell"对话框中的说明提供其他身份验证信息（如验证码），然后单击"登录"。
    
## <a name="how-do-you-know-this-worked"></a>您如何知道这有效？
<a name="step3"> </a>

如果未收到任何错误，则说明连接成功。一个快速测试是运行 Office 365 cmdlet（例如 **Get-MsolUser** ），然后查看结果。
  
如果收到错误，则查看以下要求：
  
- **常见问题是密码错误** 。重新运行步骤 3，并仔细查看您输入的用户名和密码。
    
- **用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 要求在您的计算机上启用 Microsoft .NET Framework 3.5. _x_ 功能。** 很可能您的计算机已安装了较新的版本（例如 4 或 4.5. _x_），但可以启用或禁用与 .NET Framework 的早期版本的向后兼容性。有关详细信息，请参阅下列主题：
    
  - 对于 Windows Server 2012 或 Windows Server 2012 R2，请参阅[通过使用添加角色和功能向导中启用.NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - 对于 Windows 8 或 Windows 8.1，请参阅[安装.NET Framework 3.5 版 Windows 8 上 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)
    
  - 对于 Windows 7 或 Windows Server 2008 R2，请参阅[您无法打开 Azure 活动目录模块用于 Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)
    
- **您的 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 版本可能已过期。** 若要进行检查，请在 Office 365 PowerShell 或 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 中运行以下命令：
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    如果返回的版本号低于值 1.0.8070.2，请卸载 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，并通过第 1 步中的链接安装最新版本。
    
- **如果您收到一个连接错误，请参阅以下主题：**["连接 MsolService： 类型的异常"错误](https://go.microsoft.com/fwlink/p/?LinkId=532377)。
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a>与 Azure Active Directory V2 PowerShell 模块连接
<a name="ConnectV2"> </a>

有关 [Azure Active Directory V2 PowerShell 模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)中需要新 cmdlet 的过程，请使用以下步骤安装该模块并连接到 Office 365 订阅：
  
1. 打开提升的 Windows PowerShell 命令提示符（以管理员身份运行 Windows PowerShell）。
    
2. 在"管理员: Windows PowerShell"命令窗口中，运行以下命令：
    
  ```
  Install-Module -Name AzureAD 
  ```

如果系统提示从不受信任的存储库安装模块，请键入"Y"，再按 ENTER。
    
3. 新模块安装完成后，使用以下命令连接到 Office 365 订阅：
    
  -  通过 *帐户名称和密码*  ：
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 在"Windows PowerShell 凭据请求"对话框中，键入 Office 365工作或学校帐户 用户名和密码，再单击"确定"。
    
  - 通过 *多重身份验证 (MFA)*  ：
    
  ```
  Connect-AzureAD
  ```

在"Azure Active Directory PowerShell"对话框中，键入你的 Office 365工作或学校帐户 用户名和密码，然后单击"登录"。
    
按照"Azure Active Directory PowerShell"对话框中的说明提供其他身份验证信息（如验证码），然后单击"登录"。
    
连接后，可以对 [Azure Active Directory V2 PowerShell 模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)使用这些新的 cmdlet。
  
## <a name="see-also"></a>See also

#### 

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
  
[在单个 Windows PowerShell 窗口中连接所有 Office 365 服务](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[连接 MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

