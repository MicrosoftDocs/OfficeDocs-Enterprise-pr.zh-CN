---
title: "将 Microsoft Azure Active Directory 用于 SharePoint 2013 身份验证"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: bef810a4-53f6-4962-878e-e20b5019baeb
description: "摘要：了解如何使用 Azure 访问控制服务，在 Azure Active Directory 中对 SharePoint Server 2013 用户进行身份验证。"
---

# 将 Microsoft Azure Active Directory 用于 SharePoint 2013 身份验证

 **摘要：**了解如何使用 Azure 访问控制服务，在 Azure Active Directory 中对 SharePoint Server 2013 用户进行身份验证。
  
通过使用不同的标识提供程序对用户进行身份验证，可以更轻松地管理用户。设想一下，使用您信任但是由其他人来管理的标识提供程序有多么方便。例如，您可能对访问云中的 SharePoint Server 2013 的用户使用一种身份验证类型，对内部部署环境中的 SharePoint 2013 用户使用另一种身份验证类型。Azure 访问控制服务使这些选择成为可能。
  
本文介绍如何使用 Azure 访问控制服务，在 Azure AD 中对 SharePoint 2013 用户进行身份验证，而不是您的内部部署 Active Directory。在此配置中，Azure AD 成为 SharePoint 2013 的受信任标识提供程序。此配置增加了一个与 SharePoint 2013 安装本身使用的 Active Directory 身份验证独立的用户身份验证方法。要从本文中受益，您应该熟悉 WS-Federation。有关详细信息，请参阅[了解 WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)。
  
下图显示了如何为此配置中的 SharePoint 2013 用户进行身份验证。
  
![已通过 Azure Active Directory 身份验证的用户](images/SP_AzureAD.png)
  
本文中使用的示例由 Azure 卓越中心 Microsoft 架构师 Kirk Evans 提供。
  
有关 SharePoint 2013 辅助功能的信息，请参阅 [SharePoint 2013 的辅助功能](https://go.microsoft.com/fwlink/p/?LinkId=393123)。
  
## 配置概述

按照下列常规步骤，将您的环境设置为使用 Azure AD 作为 SharePoint 2013 标识提供程序。
  
1. 创建新的 Azure AD 租户和命名空间。
    
2. 添加 WS-Federation 标识提供程序。
    
3. 将 SharePoint 添加为信赖方应用程序。
    
4. 创建自签名的证书以用于 SSL。
    
5. 创建用于基于声明的身份验证的规则组。
    
6. 配置 X.509 证书。
    
7. 创建声明映射。
    
8. 为新的标识提供程序配置 SharePoint。
    
9. 设置权限。
    
10. 验证新的提供程序。
    
## 创建 Azure AD 租户和命名空间

执行下列步骤，创建一个新的 Azure AD 租户和关联的命名空间。在此示例中，我们使用命名空间"blueskyabove"。
  
1. 在 Azure 管理门户中，单击"Active Directory"，然后创建一个新的 Azure AD 租户。
    
2. 单击"访问控制命名空间"，并创建新的命名空间。
    
3. 单击底部栏中的"管理"。这应该会打开此位置：https://blueskyabove.accesscontrol.windows.net/v2/mgmt/web。
    
4. 打开 Windows PowerShell。使用 Windows PowerShell 的 Microsoft Online Services 模块，这是为 Windows PowerShell cmdlet 安装 Azure 的先决条件。
    
5. 从 Windows PowerShell 命令提示符处，键入以下命令： `Connect-Msolservice`，然后键入您的凭据。
    
    > [!NOTE]
    > 有关如何将 Azure 用于 Windows PowerShell cmdlet 的其他信息，请参阅[使用 Windows PowerShell 管理 Azure AD](https://go.microsoft.com/fwlink/p/?LinkId=393124)。 
  
6. 在 Windows PowerShell 命令提示符处，键入以下命令：
    
  ```
  Import-Module MSOnlineExtended -Force
  ```

  ```
  $replyUrl = New-MsolServicePrincipalAddresses -Address "https://blueskyabove.accesscontrol.windows.net/"
  ```

  ```
  New-MsolServicePrincipal -ServicePrincipalNames @("https://blueskyabove.accesscontrol.windows.net/") -DisplayName "BlueSkyAbove ACS Namespace" -Addresses $replyUrl
  ```

    下图说明了输出结果。
    
     ![创建服务主体名称](images/ServicePrincipalNames.jpg)
  
## 将 WS-Federation 标识提供程序添加到命名空间

执行下列步骤，将 WS-Federation 标识提供程序添加到 blueskyabove 命名空间。
  
1. 在 Azure 管理门户中，转到"Active Directory">"访问控制命名空间"，单击"新建实例"，然后单击"管理"。
    
2. 在 Azure 访问控制门户上，单击"标识提供程序">"添加"，如下图中所示。
    
     ![Azure 中的'标识提供程序'对话框](images/Identity.jpg)
  
3. 单击"WS-Federation 标识提供程序"（如下图中所示），然后单击"下一步"。
    
     !['添加标识提供程序'设置](images/AddIdentity.jpg)
  
4. 填写显示名称和登录链接文本，然后单击"保存" 。对于 WS-Federation 元数据 URL，键入 https://accounts.accesscontrol.windows.net/blueskyabove.onmicrosoft.com/FederationMetadata/2007-06/FederationMetadata.xml。下图说明了该设置。
    
     ![联合身份提供程序](images/FederationIdentity.jpg)
  
## 将 SharePoint 添加为信赖方应用程序

执行下列步骤，将 SharePoint 添加为信赖方应用程序。
  
有关信赖方应用程序设置的其他信息，请参阅[信赖方应用程序](https://go.microsoft.com/fwlink/p/?LinkId=393125)。
  
1. 在 Azure 访问控制门户上，单击"信赖方应用程序"，然后单击"添加"，如下图中所示。
    
     !['信赖方应用程序'设置](images/RelyingPartyApplications.jpg)
  
## 创建自签名的证书以用于 SSL

执行下列步骤，创建一个新的自签名证书，以用于通过 SSL 的安全通信。
  
1. 将 Web 应用程序扩展为使用相同的 URL 作为 PublishingSite，但使用端口为 443 的 SSL，如下图中所示。
    
     ![扩展应用程序的设置](images/ExtendWebApp.jpg)
  
2. 在 IIS 管理器 中，双击"服务器证书"。
    
3. 在"操作"窗格中，单击"创建自签名证书"。在"为证书指定一个好记名称"框中为证书键入一个好记名称，然后单击"确定"。
    
4. 从"编辑网站绑定"对话框中，确保主机名与指定的好记名称相同，如以下各图中所示。
    
     ![自签名证书向导](images/SelfSignedCert.jpg)
  
     !['编辑绑定'对话框中的主机名](images/SelfSignedCert1.jpg)
  
5. 在 Azure 管理门户上，单击您想要配置的虚拟机，然后单击"终结点"。
    
6. 单击"添加"，然后单击"-->"（对于"下一步"）。
    
7. 在"名称"中，为该终结点键入一个名称。
    
8. 在"公用端口"和"专用端口"中，键入您想要使用的端口号，然后单击复选标记以完成。这些数字可能会有所不同。出于本文的目的，我们将使用 443，如下图中所示。
    
     ![Azure 中的终结点设置](images/AddEndpoint.jpg)
  
    > [!NOTE]
    > 有关如何将终结点添加到 Azure 中的虚拟机的其他信息，请参阅[如何将终结点安装到虚拟机上](https://go.microsoft.com/fwlink/p/?LinkId=393126)。 
  
9. 从访问控制服务门户中，添加信赖方，如下图中所示。
    
     !['添加信赖方'应用程序设置](images/AddRelyingParty.jpg)
  
## 创建用于基于声明的身份验证的规则组

执行下列步骤，创建一个新的规则组，以控制基于声明的身份验证。
  
1. 在左侧窗格中，单击"规则组"，然后单击"添加"。
    
2. 为规则组键入一个名称，单击"保存"，然后单击"生成"。出于本文的目的，我们使用 **Default Rule Group for. spvms.cloudapp.net** ，如下图中所示。
    
     ![Azure 中的'规则组'设置](images/RuleGroup.jpg)
  
     ![选择'生成'后的规则](images/GenerateRules.jpg)
  
    > [!NOTE]
    > 有关如何创建规则组的其他信息，请参阅[规则组和规则](https://go.microsoft.com/fwlink/p/?LinkId=393128)。 
  
3. 单击您想要更改的规则组，然后单击您想要更改的声明规则。出于本文的目的，我们将声明规则添加到组，以将 **name** 传递为 **upn** ，如下图中所示。
    
     ![Azure 访问控制的声明规则](images/ClaimRules.jpg)
  
4. 删除名为 **upn** 的现有声明规则并保留 **Name Claim to UPN** 规则，如下图中所示。
    
     ![Azure 访问控制的规则设置](images/ClaimToUPN.jpg)
  
## 配置 X.509 证书

执行下列步骤，将 X.509 证书配置为用于令牌签名。
  
1. 在访问控制服务窗格中，在"开发"下单击"应用程序集成"。
    
2. 在"终结点引用"中，找到与 Azure 租户关联的 **Federation.xml**，然后在浏览器的地址栏中复制该位置。
    
3. 在 **Federation.xml** 文件中，找到 **RoleDescriptor** 部分，并复制 _<X509Certificate>_ 元素中的信息，如下图中所示。
    
     ![Federation.xml 文件的 X509 Certificate 元素](images/X509Cert.jpg)
  
4. 从驱动器 C:\\ 的根目录中，创建一个名为 **Certificates** 的文件夹。
    
5. 将 X509Certificate 信息保存到文件夹 C:\\Certificates 中，文件名为 **AcsTokenSigning.cer** 。
    
    > [!NOTE]
    > 必须使用 .cer 扩展名保存文件名。 
  
     ![将 X509Certificate 元素另存为文件](images/X509Cert_Save.jpg)
  
## 使用 Windows PowerShell 创建声明映射

执行下列步骤，使用 Windows PowerShell 创建声明映射。
  
确认您具有以下成员身份：
  
1. SQL Server 实例上的 **securityadmin** 固定服务器角色。
    
2. 要更新的所有数据库上的 **db_owner** 固定数据库角色。
    
3. 运行 Windows PowerShell cmdlet 的服务器上的 Administrators 组。
    
管理员可使用 **Add-SPShellAdmin** cmdlet 来授予使用 SharePoint 2013 cmdlet 的权限。
  
> [!NOTE]
> 如果您不具有这些权限，请联系您的安装管理员或 SQL Server 管理员来请求权限。有关 Windows PowerShell 权限的其他信息，请参阅 [Add-SPShellAdmin](http://technet.microsoft.com/library/2ddfad84-7ca8-409e-878b-d09cb35ed4aa.aspx)。 
  
1. 在"开始"菜单上，单击"所有程序"。
    
2. 单击"Microsoft SharePoint 2013 产品"。
    
3. 单击"SharePoint 2013 命令行管理程序"</ui>。
    
4. 在 Windows PowerShell 命令提示符处，键入以下命令以创建声明映射：
    
  ```
  $cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2("c:\\certificates\\AcsTokenSigning.cer")
  ```

  ```
  New-SPTrustedRootAuthority -Name "ACS BlueSkyAbove Token Signing" -Certificate $cert
  ```

  ```
  $map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -IncomingClaimTypeDisplayName "UPN" -SameAsIncoming
  ```

  ```
  $map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
  ```

  ```
  $map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
  ```

  ```
  $realm = "urn:sharepoint:spvms"
  ```

  ```
  $ap = New-SPTrustedIdentityTokenIssuer -Name "ACS Provider" -Description "SharePoint secured by SAML in ACS" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl "https://blueskyabove.accesscontrol.windows.net/v2/wsfederation" -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
  ```

## 为新的标识提供程序配置 SharePoint

执行下列步骤，将您的 SharePoint 安装配置为 Azure AD 的新标识提供程序。
  
1. 确认执行此过程的用户帐户是 SharePoint 组"服务器场管理员"的成员。
    
2. 在管理中心的主页上，单击"应用程序管理"。
    
3. 在"应用程序管理"页上的"Web 应用程序"部分，单击"管理 Web 应用程序"。
    
4. 单击适当的 Web 应用程序。
    
5. 从功能区中单击"身份验证提供程序"。
    
6. 在"区域"下单击区域的名称，例如"Default"。
    
7. 在"编辑身份验证"页上的"声明身份验证类型"部分，选择"信任的标识提供程序"，然后单击您的提供程序的名称，出于本文的目的为 **ACS Provider** 。单击"确定"。
    
8. 下图说明了 **Trusted Provider** 设置。
    
![Web 应用程序中的'受信任提供程序'设置](images/AddProvider_Azure.jpg)
  
## 设置权限

执行下列步骤，设置访问 Web 应用程序的权限。
  
1. 在管理中心的主页上，单击"应用程序管理"。
    
2. 在"应用程序管理"页上的"Web 应用程序"部分，单击"管理 Web 应用程序"。
    
3. 单击适当的 Web 应用程序，然后单击"用户策略"。
    
4. 在"Web 应用程序的策略"中，单击"添加用户"。
    
5. 在"添加用户" 对话框中，单击"区域"中的适当区域，然后单击"下一步"。
    
6. 在"添加用户" 对话框中，键入 user2@blueskyabove.onmicrosoft.com (ACS Provider)。
    
7. 在"权限"中，单击"完全控制"。
    
8. 单击"完成"，然后单击"确定"。
    
下图显示了现有 Web 应用程序的"添加用户"部分。
  
![将用户添加到现有 Web 应用程序](images/AddUsers_Azure.jpg)
  
## 验证新的提供程序

执行下列步骤，确保新的身份验证提供程序在出现登录提示时显示，确认新的标识提供程序正常运行。
  
1. 使用名为 **Blue Sky Above** 的新提供程序登录，如下图中所示。
    
     ![登录对话框显示了受信任的新提供程序](images/BlueSkyAbove.jpg)
  
## 其他资源

[了解 WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
  
**参加讨论**

|**联系我们**|**说明**|
|:-----|:-----|
|**您需要什么样的解决方案？** <br/> |我们正在为跨多个 Microsoft 产品和服务的解决方案创建内容。请告诉我们您对我们的跨服务器解决方案的想法，或者发送电子邮件到 [MODAcontent@microsoft.com](mailto:modacontent@microsoft.com?Subject=[Solution%20Feedback]:%2) 寻求具体的解决方案。 <br/> |
|**参加解决方案讨论** <br/> |如果您热衷于解决方案，请考虑加入解决方案顾问团 (SAB)，加入由 Microsoft 解决方案内容开发人员、行业专业人士和全球客户共同参与的充满活力的大型社区。发送电子邮件到 [SAB@microsoft.com](mailto:sab@microsoft.com?Subject=Request%20to%20join%20the%20Solutions%20Advisory%20Boar) 即可加入。任何人都可以阅读[SAB 博客](https://blogs.technet.microsoft.com/solutions_advisory_board/)上有关社区的内容，但只有 SAB 成员可以参加私人解决方案网络研讨会并参与 SAB Yammer 网络。  <br/> |
|**获取您在此处看到的图片** <br/> |如果您想要在[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)内容中看到的图片的一个可编辑副本，我们将很高兴发送给您。请通过电子邮件将您的请求（包括图片的 URL 和标题）发送到 [MODAcontent@microsoft.com](mailto:modacontent@microsoft.com?subject=[Art%20Request]:%2)。  <br/> |
   

