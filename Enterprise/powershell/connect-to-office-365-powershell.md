---
title: 连接到 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
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
description: 摘要： 连接到 Office 365 组织使用 Office 365 PowerShell 从命令行执行 admin center 任务。
ms.openlocfilehash: 96406fbc23adadbf77a3cd02f8c167081f908977
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720398"
---
# <a name="connect-to-office-365-powershell"></a>连接到 Office 365 PowerShell

 **摘要：** 连接到 Office 365 组织使用 Office 365 PowerShell 从命令行执行管理任务。
  
借助 Office 365 PowerShell，可以通过命令行管理 Office 365 设置。连接到 Office 365 PowerShell 是一个非常简单的三步流程：安装必需软件，运行必需软件，再连接到 Office 365 组织。 

  
> [!TIP]
> **刚开始接触 PowerShell？** 请观看领英学习提供的 [PowerShell 概述](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)视频。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>在开始之前，需要知道什么？

- 估计完成时间：5 分钟
    
- 可以使用下列 Windows 版本：
    
  - Windows 10、Windows 8.1、Windows 8 或 Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >请使用 64 位版 Windows。2014 年 10 月，用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块已不再支持 32 位版。
    
-  这些过程适用于 Office 365 管理员角色的成员的用户。有关详细信息，请参阅[有关 Office 365 管理员角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。

## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>使用图模块 Azure Active Directory PowerShell 连接

[图形 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)模块中的命令其 cmdlet 名称中具有**AzureAD** 。

有关图模块需要在 Azure Active Directory PowerShell 中的新 cmdlet 的过程，使用以下步骤安装模块并连接到 Office 365 订阅。

>[!Note]
>有关不同版本的 Microsoft Windows 支持的信息，请参阅[Azure Active Directory PowerShell for 图模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)。
>

### <a name="step-1-install-required-software"></a>步骤 1：安装所需软件

这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。
  
1. 打开提升的 Windows PowerShell 命令提示符（以管理员身份运行 Windows PowerShell）。
    
2. 在"管理员: Windows PowerShell"命令窗口中，运行以下命令：
    
  ```
  Install-Module -Name AzureAD
  ```

如果系统提示从不受信任的存储库安装模块，请键入 **Y**，然后按 Enter 键。

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>步骤 2： 连接到 Office 365 订阅 Azure AD

连接到 Azure AD 的 Office 365 订阅与帐户名和密码或*多重身份验证 (MFA)* 从 Windows PowerShell 命令提示符 （它没有要提升的权限） 运行以下命令：
    
```
Connect-AzureAD
```

**登录到您的帐户**对话框中，键入您的 Office 365 工作或学校帐户的用户名和密码，，然后单击**确定**。

如果您使用 MFA，请按照其他对话框中的说明提供身份验证中的详细信息，如验证代码。
    
连接后，可以为[Azure Active Directory PowerShell for 图模块](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)使用的新 cmdlet。
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>与用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块连接

用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块中的命令在其 cmdlet 名称中具有 **Msol**。
    
### <a name="step-1-install-required-software"></a>步骤 1：安装所需软件

这些步骤只需在您的计算机上执行一次即可，而不是在每次连接时都要求执行。但是，您可能需要定期安装较新版本的软件。
  
1.  安装 64 位版 Microsoft Online Services 登录助手：[适用于 IT 专业人员 RTW 的 Microsoft Online Services 登录助手](https://go.microsoft.com/fwlink/p/?LinkId=286152)。
    
2. 安装用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，具体步骤如下：
    
  - 打开提升的 Windows PowerShell 命令提示符（以管理员身份运行 Windows PowerShell）。
  - 运行 **Install-Module MSOnline** 命令。
  - 如果系统提示安装 NuGet 提供程序，请键入 **Y**，然后按 Enter 键。
  - 如果系统提示从 PSGallery 安装模块，请键入 **Y**，然后按 Enter 键。
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>步骤 2： 连接到 Office 365 订阅 Azure AD

要连接到您的帐户名和密码或具有*多因素身份验证 (MFA)* 的 Office 365 订阅 Azure AD，请从 Windows PowerShell 命令提示符 （它没有要提升的权限） 运行以下命令：
    
```
Connect-MsolService
```

**登录到您的帐户**对话框中，键入您的 Office 365 工作或学校帐户的用户名和密码，，然后单击**确定**。

如果您使用 MFA，请按照其他对话框中的说明提供身份验证中的详细信息，如验证代码。

    
### <a name="how-do-you-know-this-worked"></a>您如何知道操作成功？

如果未收到任何错误，则说明连接成功。一个快速测试是运行 Office 365 cmdlet（例如 **Get-MsolUser** ），然后查看结果。
  
如果收到错误，则查看以下要求：
  
- **常见问题是密码错误** 。重新运行步骤 3，并仔细查看您输入的用户名和密码。
    
- * *Microsoft Azure Active Directory 的 Windows PowerShell 模块需要 Microsoft.NET Framework 3.5。* 对您计算机 * * 启用 x * 功能。很可能计算机具有安装新版本 (例如，4 或 4.5。* x *），但向后启用或禁用与旧版本的.NET framework 兼容。有关详细信息，请参阅以下主题：
    
  - 对于 Windows Server 2012 或 Windows Server 2012 R2，请参阅[使用“添加角色和功能”向导启用 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532368)
    
  - 对于 Windows 8 或 Windows 8.1，请参阅[在 Windows 8 或 8.1 上安装 .NET Framework 3.5](https://go.microsoft.com/fwlink/p/?LinkId=532369)
    
  - 对于 Windows 7 或 Windows Server 2008 R2，请参阅[不能打开用于 Windows PowerShell 的 Azure Active Directory 模块](https://go.microsoft.com/fwlink/p/?LinkId=532370)

  - 有关 Windows 10、 Windows 8.1 和 Windows 8，请参阅[安装.NET Framework 3.5 Windows 10、 Windows 8.1 和 Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)

  
- **您的 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 版本可能已过期。** 若要进行检查，请在 Office 365 PowerShell 或 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块 中运行以下命令：
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    如果返回的版本号低于值 1.0.8070.2，请卸载 用于 Windows PowerShell 的 Microsoft Azure Active Directory 模块，并通过第 1 步中的链接安装最新版本。
    
- **如果看到连接错误，请参阅以下主题：**[“Connect-MsolService：抛出类型异常”错误](https://go.microsoft.com/fwlink/p/?LinkId=532377)。
    

## <a name="see-also"></a>另请参阅

- [使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell 入门](getting-started-with-office-365-powershell.md)
- [在单个 Windows PowerShell 窗口中连接所有 Office 365 服务](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

