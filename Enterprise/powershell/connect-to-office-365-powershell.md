---
title: 连接到 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: 摘要： 连接到 Office 365 单位使用 Office 365 PowerShell 从命令行执行管理的中心任务。
ms.openlocfilehash: 65ddb3c66d2cd69ad1ecb468ec762667a0b07a84
ms.sourcegitcommit: 3b474e0b9f0c12bb02f8439fb42b80c2f4798ce1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-office-365-powershell"></a>连接到 Office 365 PowerShell

 **摘要：**连接到您的 Office 365 组织使用 Office 365 PowerShell 命令行中执行管理任务。
  
借助 Office 365 PowerShell，可以通过命令行管理 Office 365 设置。连接到 Office 365 PowerShell 是一个非常简单的三步流程：安装必需软件，运行必需软件，再连接到 Office 365 组织。 

  
> [!TIP]
> **刚开始接触 PowerShell？**请观看领英学习提供的 [PowerShell 概述](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)视频。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>开始前，需要知道什么？

- 估计完成时间：5 分钟
    
- 可以使用下列 Windows 版本：
    
  - Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >请使用 64 位版 Windows。2014 年 10 月，用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块已不再支持 32 位版。
    
-  这些步骤适用于 Office 365 管理角色的成员的用户。有关详细信息，请参阅[有关 Office 365 管理角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>与用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块连接

用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块中的命令在其 cmdlet 名称中具有 **Msol**。
    
### <a name="step-1-install-required-software"></a>步骤 1：安装所需软件

这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。
  
1.  安装 64 位版 Microsoft Online Services 登录助手：[适用于 IT 专业人员 RTW 的 Microsoft Online Services 登录助手](https://go.microsoft.com/fwlink/p/?LinkId=286152)。
    
2. 安装用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，具体步骤如下：
    
  - 打开管理员级 PowerShell 命令提示符。
  - 运行 **Install-Module MSOnline** 命令。
  - 如果系统提示安装 NuGet 提供程序，请键入 **Y**，然后按 Enter 键。
  - 如果系统提示从 PSGallery 安装模块，请键入 **Y**，然后按 Enter 键。
  - 安装完成后，关闭 PowerShell 命令窗口。
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>步骤 2： 连接到 Azure 广告为您的 Office 365 订阅

仅使用*帐户名和密码*连接：
  
1. 运行 Windows PowerShell 命令提示符。
2. 在 **Windows PowerShell** 命令窗口中，运行以下命令：
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. 在"Windows PowerShell 凭据请求"对话框中，键入 Office 365工作或学校帐户 用户名和密码，再单击"确定"。
    
使用*多重身份验证 (MFA)* 进行连接的具体步骤：
  
1. 运行 Windows PowerShell 命令提示符。
2. 在“用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块”**** 命令窗口中，运行以下命令。
    
```
Connect-MsolService
```

3. 在"Azure Active Directory PowerShell"对话框中，键入你的 Office 365工作或学校帐户 用户名和密码，然后单击"登录"。
    
4. 按照"Azure Active Directory PowerShell"对话框中的说明提供其他身份验证信息（如验证码），然后单击"登录"。
    
### <a name="how-do-you-know-this-worked"></a>您如何知道这有效？

如果未收到任何错误，则说明连接成功。一个快速测试是运行 Office 365 cmdlet（例如 **Get-MsolUser** ），然后查看结果。
  
如果收到错误，则查看以下要求：
  
- **常见问题是密码错误** 。重新运行步骤 3，并仔细查看您输入的用户名和密码。
    
- * *Microsoft Azure 活动目录模块用于 Windows PowerShell 需要 Microsoft.NET Framework 3.5。*在您的计算机 * * 启用 x * 功能。很可能您的计算机已安装了较新的版本 (例如，4 或 4.5。*x *），但可以向后启用或禁用与.NET Framework 的早期版本的兼容性。有关详细信息，请参阅下列主题：
    
  - 对于 Windows Server 2012 或 Windows Server 2012 R2，请参阅[使用“添加角色和功能”向导启用 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - 对于 Windows 8 或 Windows 8.1，请参阅[在 Windows 8 或 8.1 上安装 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532369)
    
  - 对于 Windows 7 或 Windows Server 2008 R2，请参阅[不能打开用于 Windows PowerShell 的 Azure Active Directory 模块](https://go.microsoft.com/fwlink/p/?LinkId=532370)
    
- **您的 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 版本可能已过期。** 若要进行检查，请在 Office 365 PowerShell 或 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 中运行以下命令：
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    如果返回的版本号低于值 1.0.8070.2，请卸载 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，并通过第 1 步中的链接安装最新版本。
    
- **如果看到连接错误，请参阅以下主题：**[“Connect-MsolService：抛出类型异常”错误](https://go.microsoft.com/fwlink/p/?LinkId=532377)。
    
<a name="ConnectV2"> </a>
## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>用图形模块 Azure 活动目录 PowerShell 连接

在[Azure 的活动目录 PowerShell 图模块的](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)模块中的命令其 cmdlet 名称中有"AzureAD"。

有关图形模块需要在 Azure 活动目录 PowerShell 的新 cmdlet 的过程，使用这些步骤来安装模块和连接到您的 Office 365 订购。

>[!Note]
>有关不同版本的 Microsoft Windows 的支持的信息，请参阅[图形模块 Azure 活动目录 PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) 。
>

### <a name="step-1-install-required-software"></a>步骤 1：安装所需软件

这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。

  
1. 打开提升的 Windows PowerShell 命令提示符（以管理员身份运行 Windows PowerShell）。
    
2. 在"管理员: Windows PowerShell"命令窗口中，运行以下命令：
    
  ```
  Install-Module -Name AzureAD 
  ```

如果系统提示从不受信任的存储库安装模块，请键入 **Y**，然后按 Enter 键。


### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>步骤 2： 连接到 Azure 广告为您的 Office 365 订阅

通过*帐户名和密码*连接到 Office 365 订阅：
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

在"Windows PowerShell 凭据请求"对话框中，键入 Office 365工作或学校帐户 用户名和密码，再单击"确定"。
    
通过*多重身份验证 (MFA)* 连接到 Office 365 订阅：

```
Connect-AzureAD
```

在"Azure Active Directory PowerShell"对话框中，键入你的 Office 365工作或学校帐户 用户名和密码，然后单击"登录"。
    
按照"Azure Active Directory PowerShell"对话框中的说明提供其他身份验证信息（如验证码），然后单击"登录"。
    
连接后，您可以使用[Azure 的活动目录 PowerShell 图形模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)新 cmdlet。
  
## <a name="see-also"></a>另请参阅

- [使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
- [在单个 Windows PowerShell 窗口中连接所有 Office 365 服务](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

