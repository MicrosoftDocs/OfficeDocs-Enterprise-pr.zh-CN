---
title: 如何将 Exchange Server 本地配置为使用混合新式身份验证
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
description: 混合新式身份验证 (HMA) 是一种身份管理方法, 它提供更安全的用户身份验证和授权, 并可用于 Exchange server 本地混合部署。
ms.openlocfilehash: 364f95bbbc06f477d258ed55a8711864e7a87e69
ms.sourcegitcommit: 1d84e2289fc87717f8a9cd12c68ab27c84405348
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "30372859"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>如何将 Exchange Server 本地配置为使用混合新式身份验证

混合新式身份验证 (HMA) 是一种身份管理方法, 它提供更安全的用户身份验证和授权, 并可用于 Exchange server 本地混合部署。
  
## <a name="fyi"></a>仅供参考

在开始之前, 我称之为:
  
- 混合新式身份\>验证 HMA
    
- Exchange 本地\> EXCH
    
- Exchange Online \> EXO
    
此外,*如果本文中的图形有一个 "灰显" 或 "变暗" 的对象, 则表示以灰色显示的元素不包含在 HMA 的特定配置中*。 
  
## <a name="enabling-hybrid-modern-authentication"></a>启用混合新式身份验证

启用 HMA 的打开方式:
  
1. 在开始之前, 请务必满足先决条件。
    
1. 由于很多**先决条件**对于 Skype for business 和 exchange 都是常见的, 因此[混合新式身份验证概述和用于在本地 Skype for business 和 exchange 服务器上使用它的先决条件](hybrid-modern-auth-overview.md)。 在开始本文中的任何步骤之前, 请执行此操作。
    
2. 在 Azure AD 中将本地 web 服务 url 添加为服务主体名称 (spn)。
    
3. 确保为 HMA 启用所有虚拟目录
    
4. 检查 EvoSTS Auth Server 对象
    
5. 在 EXCH 中启用 HMA。
    
 **注释**您的 Office 版本是否支持 MA？ 请参阅[如何在 office 2013 和 office 2016 客户端应用程序中运行新式验证](modern-auth-for-office-2013-and-2016.md)。
  
## <a name="make-sure-you-meet-all-the-pre-reqs"></a>请确保满足所有预 reqs

由于很多先决条件对于 Skype for business 和 exchange 都是常见的, 因此请参阅[混合新式身份验证概述和在本地 skype for business 和 exchange 服务器上使用它的先决条件](hybrid-modern-auth-overview.md)。 在开始本文中的任何步骤*之前*, 请执行此操作。 
  
## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>在 Azure AD 中将本地 web 服务 url 添加为 spn

运行将本地 web 服务 url 分配为 Azure AD spn 的命令。 在身份验证和授权过程中, 客户端计算机和设备使用 spn。 所有可用于从本地连接到 Azure Active Directory (AAD) 的 url 都必须在 AAD 中注册 (这包括内部和外部命名空间)。
  
首先, 收集您需要在 AAD 中添加的所有 url。 在本地运行以下命令:
  
```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ActiveSyncVirtualDirectory | FL server,*url*
Get-OABVirtualDirectory | FL server,*url*
```
    
确保客户端可以连接的 url 在 AAD 中列为 HTTPS 服务主体名称。
  
1. 首先, 使用[这些说明](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)连接到 AAD。 

 **注释**您需要使用此页面中的 connect-msolservice 选项, 才能使用下面的命令。 
    
2. 对于与 Exchange 相关的 url, 请键入以下命令:
    
```powershell
Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
```

记下 (和屏幕截图以供稍后比较) 此命令的输出应包括 https:// *autodiscover.yourdomain.com*和 https:// *mail.yourdomain.com* URL, 但主要由以以下开头的 spn 组成00000002-0000-0ff1-ce00-000000000000/。 如果缺少内部部署中的 https://url, 我们需要将这些特定记录添加到此列表中。 
  
3. 如果您在此列表中看不到内部和外部 MAPI/HTTP、EWS、ActiveSync、OAB 和自动发现记录, 则必须使用下面的命令添加它们 (示例 url 是`mail.corp.contoso.com`' ' and`owa.contoso.com`' ', 但您需要将**示例 url 替换为您自己的 url** ): <br/>
```powershell
$x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000   
$x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
$x.ServicePrincipalnames.Add("https://owa.contoso.com/")
$x.ServicePrincipalnames.Add("https://eas.contoso.com/")
Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
```
 
4. 再次运行步骤2中的 new-msolserviceprincipal 命令, 并查看输出, 以验证新记录是否已添加。 将列表/屏幕截图从早到新的 spn 列表进行比较 (您还可能会为您的记录提供新列表的屏幕截图)。 如果成功, 您将在列表中看到两个新的 url。 根据我们的示例, spn 列表现在将包含特定的 url `https://mail.corp.contoso.com`和。 `https://owa.contoso.com` 
  
## <a name="verify-virtual-directories-are-properly-configured"></a>验证是否正确配置了虚拟目录

现在, 验证是否已在 Outlook 的所有虚拟目录上通过运行以下命令, 正确启用了 OAuth:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth* 
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

检查输出以确保每个 VDirs 上启用了**OAuth** , 它将如下所示 (要查看的关键内容是 ' OAuth '); 

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*
```

```
Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```
  
如果任何服务器和四个虚拟目录中的任何一个都缺少 OAuth, 则需要先使用相关命令添加它, 然后再继续。
  
## <a name="confirm-the-evosts-auth-server-object-is-present"></a>确认 EvoSTS Auth Server 对象是否存在

返回到此最后一个命令的内部部署 Exchange 命令行管理程序。 现在, 您可以验证您的内部部署是否具有 evoSTS 身份验证提供程序的条目:
  
```powershell
Get-AuthServer | where {$_.Name -eq "EvoSts"}
```

您的输出应显示名称 EvoSts 的 get-authserver, 并且 "已启用" 状态应为 True。 如果看不到此内容, 应下载并运行 "混合配置" 向导的最新版本。
  
 **重要说明**如果您的环境中运行的是 Exchange 2010, 则不会创建 EvoSTS 身份验证提供程序。 
  
## <a name="enable-hma"></a>启用 HMA

在 Exchange 命令行管理程序 (本地) 中运行以下命令:

```powershell
Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true  
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```
    
## <a name="verify"></a>Verify

启用 HMA 后, 客户端的下一次登录将使用新的身份验证流。 请注意, 仅打开 HMA 不会触发任何客户端的重新身份验证。 客户端将根据身份验证令牌和/或证书的有效期重新进行身份验证。
  
您还应按住 CTRL 键, 同时右键单击 Outlook 客户端的图标 (也在 Windows 通知栏中), 然后单击 "连接状态"。 针对 "身份验证" 类型的 "载荷\*" 查找客户端的 SMTP 地址, 该类型表示在 OAuth 中使用的持有者令牌。
  
 **注释**是否需要使用 HMA 配置 Skype for business？ 您将需要两个文章: 一个列出[受支持的拓扑](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), 另一个演示[如何执行配置](configure-skype-for-business-for-hybrid-modern-authentication.md)。
  

## <a name="related-topics"></a>相关主题

[混合新式身份验证概述和在本地 Skype for business 和 Exchange 服务器上使用它的先决条件](hybrid-modern-auth-overview.md) 
  

