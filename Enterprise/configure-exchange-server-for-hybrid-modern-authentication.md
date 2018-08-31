---
title: 如何配置本地 Exchange Server 以使用混合新式验证
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 3/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
description: 混合现代身份验证 (HMA)，是一种身份管理提供更安全的用户身份验证和授权，并适用于 Exchange server 内部部署混合部署的方法。
ms.openlocfilehash: 871f03b8e776c694f7378f6905259d21516f7326
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539687"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>如何配置本地 Exchange Server 以使用混合新式验证

混合现代身份验证 (HMA)，是一种身份管理提供更安全的用户身份验证和授权，并适用于 Exchange server 内部部署混合部署的方法。
  
## <a name="fyi"></a>注意

我们开始之前，请调用：
  
- 混合现代身份验证\>HMA
    
- Exchange 内部部署\>EXCH
    
- Exchange Online \> EXO
    
此外，*如果中的图形本文具有已灰显或变暗这意味着，以灰色显示的元素未包括在 HMA 特定的配置对象*。 
  
## <a name="enabling-hybrid-modern-authentication"></a>启用混合现代身份验证

HMA 开启方法：
  
1. 要确保在开始之前满足先决条件。
    
1. 以来多个**必备组件**是常见的业务和 Exchange[混合现代身份验证概述和必备软件以便使用其本地 Skype 业务和 Exchange 服务器的](hybrid-modern-auth-overview.md)两个 Skype。在开始任何本文中的步骤之前执行此操作。
    
2. 添加内部部署 web 服务 Url 为服务主体名称 (Spn) 在 Azure AD。
    
3. 确保所有虚拟目录启用了 HMA
    
4. 检查 EvoSTS 身份验证服务器对象
    
5. 汇兑损益在启用 HMA
    
 **注释**您的 Office 版本是否支持 MA？请参阅[如何现代身份验证适用于 Office 2013 和 Office 2016 客户端应用程序](modern-auth-for-office-2013-and-2016.md)。
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>请确保您满足所有前要求

由于多个必备组件以针对常用于这两个 Skype 商业和 Exchange，查看[混合现代身份验证概述和使用它与业务和 Exchange 服务器的内部部署 Skype 的先决条件](hybrid-modern-auth-overview.md)。执行此*之前*开始任何本文中的步骤。 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>添加内部部署 Azure AD 中为 Spn web 服务 Url

运行命令的 Azure AD Spn。 Spn 的身份验证和授权过程中使用的客户端计算机和设备分配在本地 web 服务 Url。必须在 AAD （这包括内部和外部的命名空间） 中注册所有可能会用于从内部连接到 Azure Active Directory (AAD) 的 Url。
  
首先，收集所有 AAD 中添加所需的 Url。运行这些命令在本地：
  
- Get MapiVirtualDirectory |FL 服务器\*url\*
    
- Get-webservicesvirtualdirectory |FL 服务器\*url\*
    
- **Get-activesyncvirtualdirectory |FL 服务器\*url\***
    
- Get-oabvirtualdirectory |FL 服务器\*url\*
    
确保客户端可以连接到列为 HTTPS AAD 中的服务主体名称的 Url。
  
1. 首先，连接到 AAD 与[这些说明](https://docs.microsoft.com/en-us/office365/enterprise/powershell/connect-to-office-365-powershell)。
    
2. 对于 Exchange 相关的 Url，键入以下命令：
    
- Get MsolServicePrincipal-AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 |选择-ExpandProperty ServicePrincipalNames
    
执行此命令，应包括 https:// 的输出的注释 （和更高版本比较的屏幕快照） * 自动发现。*yourdomain* .com * 和 https:// *mail.yourdomain.com* URL，但主要包含开头 00000002-0000-0ff1-ce00-000000000000 的 Spn /。从内部部署的缺少的 https:// Url 时我们将需要这些特定记录添加到此列表。 
  
3. 如果看不到您内部和外部 MAPI/HTTP、 EWS、 ActiveSync、 OAB 和自动发现记录此列表中的，您必须添加它们使用下面的命令 (示例 Url 是`mail.corp.contoso.com`和`owa.contoso.com`，但您必须**替换为您自己的示例 Url** ): </br>
```
- $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
- $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
- $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
- $x.ServicePrincipalnames.Add("https://eas.contoso.com/")
- Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. 确认通过 Get MsolServicePrincipal 命令从步骤 2 再次运行，并将输出通过查找已添加新记录。比较列表 / 屏幕截图从之前对新列表的 Spn （您还可以屏幕截图新列表的记录）。如果您已成功完成，您将看到列表中的两个新 Url。通过我们的示例转，Spn 的列表将现已包括特定的 Url`https://mail.corp.contoso.com`和`https://owa.contoso.com`。 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>确认正确配置虚拟目录

现在验证中正确启用 OAuth 在所有虚拟目录 Outlook 上的 Exchange 可能使用通过运行以下命令：

```
Get-MapiVirtualDirectory | FL server,\*url\*,\*auth\* 
Get-WebServicesVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-OABVirtualDirectory | FL server,\*url\*,\*oauth\*
Get-AutoDiscoverVirtualDirectory | FL server,\*oauth\*
```

检查以确保**OAuth**的输出启用每个这些 VDirs，它看起来如下所示 （和需要查看的重要一点是 OAuth）; 
  
 **[PS]C:\Windows\system32\>Get MapiVirtualDirectory |fl 服务器\*url\*，\*身份验证\***
  
 **服务器： EX1**
  
 **InternalUrl:`https://mail.contoso.com/mapi`**
  
 **ExternalUrl:`https://mail.contoso.com/mapi`**
  
 **IISAuthenticationMethods: {Ntlm、 OAuth、 Negotiate}**
  
 **InternalAuthenticationMethods: {Ntlm、 OAuth、 Negotiate}**
  
 **ExternalAuthenticationMethods: {Ntlm、 OAuth、 Negotiate}**
  
如果您需将其使用相关的命令，然后再继续添加 OAuth 缺少来自任何服务器和任何四个虚拟目录。
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>确认存在 EvoSTS 身份验证服务器对象

返回到此最后一个命令的本地 Exchange 命令行管理程序。现在您可以验证本地 evoSTS 身份验证提供程序有一项：
  
`Get-AuthServer | where {$_.Name -eq "EvoSts"}`
    
输出应显示的名称 EvoSts 认证服务器和已启用状态应该为 True。如果您看不到此，您应下载并运行混合配置向导的最新版本。
  
 **重要**如果您在您的环境中运行 Exchange 2010，不会创建 EvoSTS 身份验证提供程序。 
  
## <a name="enable-hma"></a>启用 HMA

在 Exchange Management Shell 中，在本地运行以下命令：

```
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>“验证”

一旦您启用 HMA，下次登录时的客户端将使用新的身份验证流。请注意刚打开 HMA 不会触发重新进行身份验证的任何客户端。客户端重新进行身份验证基于身份验证令牌和/或拥有的证书的生存期。
  
您还应右键单击该图标的 Outlook 客户端 （还在 Windows 通知任务栏中） 的同时按住 CTRL 键，然后单击连接状态。查找针对的身份验证类型的客户端的 SMTP 地址持有者\*，它代表用于 OAuth 持有者令牌。
  
 **注释**需要配置 HMA Skype for Business？您将需要两篇文章： 一个列出了[受支持的拓扑](https://technet.microsoft.com/en-us/library/mt803262.aspx)，，另一个演示[如何执行配置](configure-skype-for-business-for-hybrid-modern-authentication.md)。
  

## <a name="related-topics"></a>相关主题

[混合现代身份验证概述和使用内部部署 Skype 使用的业务和 Exchange 服务器的先决条件](hybrid-modern-auth-overview.md) 
  

