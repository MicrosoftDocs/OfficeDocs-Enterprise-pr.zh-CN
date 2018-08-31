---
title: 如何配置本地 Skype for Business 以使用混合新式验证
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 6/4/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
description: 现代身份验证，是一种身份管理提供更安全的用户身份验证和授权，适用于 Skype 用于业务服务器本地和 Exchange server 内部部署，以及业务混合的拆分域 Skype 方法。
ms.openlocfilehash: 48ce10022e384ec88b88c0e8ec038bf201adc707
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539883"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>如何配置本地 Skype for Business 以使用混合新式验证

现代身份验证，是一种身份管理提供更安全的用户身份验证和授权，适用于 Skype 用于业务服务器本地和 Exchange server 内部部署，以及业务混合的拆分域 Skype 方法。
  
 **重要**若要了解有关现代身份验证 (MA) 和为什么您可能希望在贵公司或组织中使用它的详细信息吗？检查[本文档](hybrid-modern-auth-overview.md)概述。如果您需要了解哪些 Skype 的业务拓扑支持与 MA，此处介绍的 ！ 
  
 **我们在开始之前**，请调用： 
  
- 现代身份验证\>MA
    
- 混合现代身份验证\>HMA
    
- Exchange 内部部署\>EXCH
    
- Exchange Online \> EXO
    
- 为业务本地 Skype \> SFB
    
- 和 Skype for Business 联机\>SFBO
    
此外，* 本文中的图形是否具有灰显或变暗的对象，该对象表示灰色**不**包括特定于 MA 的配置中所示的元素。 * 
  
## <a name="read-the-summary"></a>阅读摘要

这段摘要最终过程是： 到步骤，可能否则迷失执行期间，并且最好使用以跟踪您在何处过程中的总体检查的列表。
  
1. 首先，请确保您满足所有先决条件。
    
1. 以来多个**必备组件**是针对常用于这两个 Skype 商业和 Exchange，[请参阅此概述文章以必备项检查表](hybrid-modern-auth-overview.md)。执行此*之前*开始任何本文中的步骤。 
    
2. 收集您将需要一个文件或 OneNote 中的特定于 HMA 的信息。
    
3. 打开 ON 现代的身份验证 EXO （如果尚未打开）。
    
4. 打开 ON 现代的身份验证 SFBO （如果尚未打开）。
    
5. 打开 Exchange 内部部署混合现代身份验证。
    
6. 打开业务本地混合 Skype 现代的身份验证。
    
请注意以下步骤打开 MA SFB、 SFBO、 EXCH，和 EXO-，即可以参与了 HMA 配置 SFB 和 SFBO （包括依赖 EXCH/EXO） 的所有产品。换句话说，如果用户驻留在 / 混合 （EXO + SFBO、 EXO + SFB、 EXCH + SFBO，或 EXCH + SFB） 的任何部分中创建邮箱，完成的产品将如下所示：
  
![业务 HMA 拓扑的混合 6 Skype 对 MA 中所有四个可能的位置。](media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)
  
您可以看到有四个不同的位置打开 MA ！获得最佳用户体验，我们建议您打开 MA 中所有四个这些位置。如果所有这些位置中，不能打开 MA，调整的步骤，以便您打开 MA 仅在所需的环境的位置。
  
请参阅[可支持性主题 Business MA 的 Skype](https://technet.microsoft.com/en-us/library/mt803262.aspx)受支持的拓扑。 
  
 **重要**仔细检查之前您已满足所有必备组件。您可以找到该信息[此处](hybrid-modern-auth-overview.md)。
  
## <a name="collect-all-hma-specific-info-youll-need"></a>收集所需的所有 HMA 特有信息

双重的检查后满足用于现代身份验证的[先决条件](hybrid-modern-auth-overview.md)（请参阅上面的说明），您应创建文件来保存所需的步骤提前中的 configuring HMA 的信息。使用本文中的示例： 
  
- **SIP/SMTP 域**
    
  - 例如 contoso.com （与 Office 365 联盟）
    
- **租户 ID**
    
  - GUID 值，该值代表 Office 365 租户 （在的 contoso.onmicrosoft.com 登录）。
    
- **SFB 2015 CU5 Web 服务 Url**
    
为所有 SfB 2015 池部署，您将需要内部和外部 web 服务 URL。若要获得这些，运行以下命令从 Skype 的业务命令行管理程序：
  
Get-csservice-WebServer |选择对象 PoolFqdn，InternalFqdn，外部 |FL
  
- 例如内部：https://lyncwebint01.contoso.com
    
- 例如外部：https://lyncwebext01.contoso.com
    
如果您使用的 Standard Edition server，该内部 URL 将为空。在这种情况下，使用内部 URL 池 fqdn。
  
## <a name="turn-on-modern-authentication-for-exo"></a>打开 EXO 现代身份验证

按照说明进行操作： [Exchange Online： 如何启用现代身份验证您的租户。](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)
  
## <a name="turn-on-modern-authentication-for-sfbo"></a>打开 SFBO 现代身份验证

按照说明进行操作： [Skype 业务 online： 启用您的租户的现代身份验证](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)。
  
## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>打开 Exchange 内部部署混合现代身份验证

按照说明进行操作：[如何配置 Exchange Server 内部部署用于混合现代身份验证](configure-exchange-server-for-hybrid-modern-authentication.md)。
  
## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>打开业务本地混合 Skype 现代的身份验证

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>添加内部部署 Azure AD 中为 Spn web 服务 Url

现在，您需要运行命令以将 （收集更早版本） 的 Url 添加为 SFBO 中的服务主体。
  
 **注释**服务主体名称 (Spn) 确定 web 服务，并将其与安全主体 （如帐户名或组中） 关联，以便该服务可充当授权用户替。客户端到服务器身份验证发出信息的使用的中包含的 Spn。 
  
1. 首先，连接到 AAD 与[这些说明](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0)。
    
2. 运行此命令中，内部部署，以获取 SFB web 服务 Url 的列表。
    
  - Get MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 |选择-ExpandProperty ServicePrincipalNames
    
    请注意，AppPrincipalId 开头"00000004"。这对应于 Skype 的业务联机。
    
    执行此命令，其中将包括 SE 和 WS URL，但主要包含开头 00000004-0000-0ff1-ce00-000000000000 的 Spn 的输出的注释 （和更高版本比较的屏幕快照） /。
    
3. 如果内部**或**外部丢失了从本地 SFB Url (例如，https://lyncwebint01.contoso.com和https://lyncwebext01.contoso.com)我们需要这些特定记录添加到此列表。 
    
    请务必下面的*示例 Url* ，替换中添加命令您实际 Url ！ 
    
  - $x = get MsolServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebint01.contoso.com/* ") 
    
  - $x.ServicePrincipalnames.Add (" *https://lyncwebext01.contoso.com/* ") 
    
  - 设置 MSOLServicePrincipal-AppPrincipalId 00000004-0000-0ff1-ce00-000000000000-ServicePrincipalNames $x.ServicePrincipalNames
    
4. 确认通过 Get MsolServicePrincipal 命令从步骤 2 再次运行，并将输出通过查找已添加新记录。比较列表 / 屏幕截图从之前对新列表的 Spn （您还可以屏幕截图新列表的记录）。如果您已成功完成，您将看到列表中的两个新 Url。通过我们的示例转，Spn 的列表将现已包括特定的 Urlhttps://lyncweb01.contoso.com和https://autodiscover.contoso.com。
    
### <a name="create-the-evosts-auth-server-object"></a>创建 EvoSTS 身份验证服务器对象

为业务命令行管理程序 Skype 中运行以下命令。
  
- New-csoauthserver-Identity evoSTS-MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true-类型 AzureAD
    
### <a name="enable-hybrid-modern-authentication"></a>启用混合现代身份验证

这是实际开启 MA 的步骤。可以提早制定运行上述所有步骤，而不更改客户端身份验证流程。若要更改身份验证流程，准备就绪后，运行此命令中 Skype 的业务命令行管理程序。 
  
- Set-csoauthconfiguration-ClientAuthorizationOAuthServerIdentity evoSTS
    
## <a name="verify"></a>“验证”

一旦您启用 HMA，下次登录时的客户端将使用新的身份验证流。请注意刚打开 HMA 不会触发重新进行身份验证的任何客户端。客户端重新进行身份验证基于身份验证令牌和/或拥有的证书的生存期。
  
若要测试 HMA 正常启用此功能后，注销测试 SFB Windows 客户端，并确保单击删除我的凭据。再次登录。客户端现在应使用的现代身份验证流程和您的登录将现已包括一个**Office 365**提示符 '工作或学校看到右之前客户端与服务器联系，并登录您的帐户。 
  
您还应检查配置信息的 Skype 业务客户端的 OAuth 颁发机构。若要在客户端计算机上执行此操作，请按住 CTRL 键的同时右键 Skype 业务图标单击 Windows 通知托盘中。在出现的菜单中，单击配置信息。在桌面上将出现 Skype 的业务配置信息窗口中，查找以下问题：
  
![使用现代身份验证的业务客户端的配置信息的 Skype 显示 Lync 和 EWS OAUTH 证书颁发机构 URL https://login.windows.net/common/oauth2/authorize。](media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png)
  
您还应右键单击该图标的 Outlook 客户端 （还在 Windows 通知任务栏中） 的同时按住 CTRL 键，然后单击连接状态。查找针对的身份验证类型的客户端的 SMTP 地址持有者\*，它代表用于 OAuth 持有者令牌。
  
## <a name="related-articles"></a>相关的文章

[现代身份验证概述的反向链接](hybrid-modern-auth-overview.md)。 
  
您是否需要知道如何用于现代身份验证 (ADAL) 您 Skype 业务客户端？我们提供了步骤[此处](https://technet.microsoft.com/en-us/library/mt710548.aspx)。
  
是否要阅读这些步骤，显示为 Exchange Server、 本地、 SFB 的情况下运行？这些步骤在此处可用。
  

