---
title: 用于 SharePoint Server 身份验证的 Azure AD
ms.author: tracyp
author: MSFTTracyP
ms.reviewer:
- kirke
- josephd
- kirks
manager: laurawi
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
ms.custom: Ent_Solutions
ms.assetid: ''
description: 摘要： 了解如何以绕过 Azure 访问控制服务，使用 SAML 1.1 与 Azure Active Directory 在 SharePoint Server 用户进行身份验证。
ms.openlocfilehash: dfaede331233444413d82b500e14fc68195eaca1
ms.sourcegitcommit: b6c8b044963d8df24ea7d63917e0203ba40fb822
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2018
ms.locfileid: "19702982"
---
# <a name="using-azure-ad-for-sharepoint-server-authentication"></a>用于 SharePoint Server 身份验证的 Azure AD

 **摘要：** 了解如何在 SharePoint Server 2016 用户与 Azure Active Directory 身份验证。 

<blockquote>
<p>本文是指与 Azure Active Directory 图形进行交互的代码示例。您可以下载代码示例[此处](https://github.com/kaevans/spsaml11/tree/master/scripts)。</p>
</blockquote>

SharePoint Server 2016 能够轻松地通过不同的身份提供程序的信任，但其他人管理对进行身份验证来管理您的用户使用基于声明的身份验证的用户进行身份验证。例如，而不是管理通过 Active Directory 域服务 (AD DS) 的用户身份验证，您无法使用户能够使用 Azure Active Directory (Azure AD) 进行身份验证。这样，具有中其用户名的 onmicrosoft.com 后缀的仅使用云的用户的身份验证，用户与内部部署目录同步和邀请来宾用户从其他目录。它还可以充分利用 Azure AD 功能，如多因素身份验证和高级报告功能。

> [!IMPORTANT]
> 也可以与 SharePoint Server 2013; 使用本文中所述的解决方案但是，记住 SharePoint Server 2013 已接近主流支持结束。有关详细信息，请参阅[Microsoft 生命周期策略](https://support.microsoft.com/en-us/lifecycle/search?alpha=SharePoint%20Server%202013)和[更新产品服务策略的 SharePoint 2013。](https://technet.microsoft.com/library/684173bb-e90a-4eb7-b268-b8d7458bc802(v=office.16).aspx)

本文介绍如何使用 Azure AD 以进行用户身份验证而不是您的内部部署 AD DS。在此配置中，Azure AD 将成为受信任的身份提供程序的 SharePoint Server 2016。此配置添加独立于所使用的 SharePoint Server 2016 安装本身的 AD DS 验证用户身份验证方法。这样可以受益这篇文章，您应熟悉 WS 联合身份验证。有关详细信息，请参阅[了解 WS 联合身份验证](https://go.microsoft.com/fwlink/p/?linkid=188052)。

![SharePoint 身份验证使用 Azure AD](images/SAML11/fig1-architecture.png)

以前，这种配置需要联合身份验证服务如 Azure 访问控制服务 (ACS) 在云中或环境中承载 Active Directory 联合身份验证服务 (AD FS) 转换为 SAML 1.1 SAML 2.0 令牌。Azure AD 现在可支持颁发的 SAML 1.1 令牌，该转换不再需要。上图显示 SharePoint 2016 用户在此配置中，演示不再媒介执行该转换的要求对身份验证的方式。

> [!NOTE]
> 此配置适用于是否在 Azure 虚拟机或内部部署承载于 SharePoint 场。它不需要打开确保用户之外的其他防火墙端口可以从其浏览器访问 Azure Active Directory。

有关 SharePoint 2016 辅助功能的信息，请参阅[SharePoint Server 2016 中的辅助功能准则](https://go.microsoft.com/fwlink/p/?LinkId=393123)。

## <a name="configuration-overview"></a>配置概述

按照以下常规步骤设置您的环境，以用作 SharePoint Server 2016 身份提供程序使用 Azure AD。

1. 创建新 Azure AD 目录或使用您现有的目录。
2. 确保您想要使用 Azure AD 安全的 web 应用程序的区域配置为使用 SSL。
3. 在 Azure AD 中创建新的企业应用程序。
4. 在 SharePoint Server 2016 中配置新的受信任的身份提供程序。
5. 设置 web 应用程序的权限。
6. 在 Azure AD 中添加的 SAML 1.1 令牌颁发策略。
7. 验证新的提供程序。

以下各节介绍如何执行这些任务。

## <a name="step-1-create-a-new-azure-ad-directory-or-use-your-existing-directory"></a>步骤 1： 创建一个新 Azure AD 目录或使用您现有的目录

Azure 门户中 ([https://portal.azure.com](https://portal.azure.com))，创建一个新目录。提供组织名称、 初始域名的国家或地区。

![创建一个目录](images/SAML11/fig2-createdirectory.png) 

 如果您已有一个目录，如用于 Microsoft Office 365 或 Microsoft Azure 订阅，则您可以改用该目录。您必须有权在目录中注册应用程序。

## <a name="step-2-ensure-the-zone-for-the-web-application-that-you-want-to-secure-with-azure-ad-is-configured-to-use-ssl"></a>步骤 2： 确保您想要使用 Azure AD 安全的 web 应用程序的区域配置为使用 SSL

本文是编写使用中[运行 SharePoint Server 2016 Azure 中的服务器场的高可用性](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)的参考体系结构。使用[本文](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/sharepoint)中所述将解决方案部署的文章的相应脚本创建在不使用 SSL 的网站。  

使用 SAML 要求应用程序配置为使用 SSL。如果您的 SharePoint web 应用程序未配置为使用 SSL，使用以下步骤创建新的自签名的证书配置 SSL 的 web 应用程序。此配置仅适用于实验室环境，并不是生产。生产环境应使用签名的证书。

1. 转到**管理中心** > **应用程序管理** > **管理 Web 应用程序**，并选择需要扩展，以使用 SSL 的 web 应用程序。选择 web 应用程序，然后单击**扩展功能区**按钮。扩展的 web 应用程序使用相同的 URL，但使用端口 443 使用 SSL。</br>![扩展到其他 IIS 网站的 web 应用程序](images/SAML11/fig3-extendwebapptoiis.png)</br>
2. 在 IIS 管理器 中，双击"服务器证书"。
3. 在**操作**窗格中，单击**创建自签名证书**。在指定的友好名称证书框中，键入证书的友好名称，然后单击**确定**。
4. 从**编辑网站绑定**对话框中，确保 host name 是相同的友好名称，如下图所示。</br>![在 IIS 中编辑网站绑定](images/SAML11/fig4-editsitebinding.png)</br>

每个 SharePoint 场中的 web 前端服务器将需要在 IIS 中配置网站绑定的证书。


## <a name="step-3-create-a-new-enterprise-application-in-azure-ad"></a>步骤 3: Azure AD 中创建新的企业应用程序

1. Azure 门户中 ([https://portal.azure.com](https://portal.azure.com))，打开 Azure AD 目录。单击**企业应用程序**，然后单击**新建应用程序**。选择**非库应用**程序。提供一个名称，如*SharePoint SAML 集成*并单击**添加**。</br>![添加新的非库应用程序](images/SAML11/fig5-addnongalleryapp.png)</br>
2. 单击的单一登录链接在导航窗格中配置应用程序。将**单一登录模式**下拉列表更改为**基于 SAML 的单一登录**以显示应用程序的 SAML 配置属性。配置具有以下属性：</br>
    - 标识符：`urn:sharepoint:portal.contoso.local`
    - 答复 URL:`https://portal.contoso.local/_trust/default.aspx`
    - 登录 URL:`https://portal.contoso.local/_trust/default.aspx`
    - 用户标识符：`user.userprincipalname`</br>
    - 注意： 请记住，更改*portal.contoso.local*替换要保护的 SharePoint 网站的 URL 的 Url。</br>
3. 设置表格 （类似于下面的表 1），包括以下行：</br> 
    - 领域
    - SAML 签名证书文件的完整路径
    - （替换 */wsfed* */saml2* ） SAML 单一登录服务 URL
    - 应用程序的对象 id。 </br>
将*Identifier*值复制到的*领域*属性表中 (请参见表 1 下方)。
4. 保存所做的更改。
5. 单击**配置 （应用程序名称）** 链接访问配置单一登录页。</br>![在页面上配置单一登录](images/SAML11/fig7-configssopage.png)</br> 
    -  单击**SAML 签名证书的原始**链接以下载扩展名.cer 文件 SAML 签名证书。复制并粘贴到数据表下载的文件的完整路径。
    - 复制并粘贴到 SAML 单一登录服务 URL 链接，替换 */wsfed*URL */saml2*部分。</br>
6.  导航到**属性**窗格中的应用程序。复制并粘贴到您在步骤 3 中设置的表的对象 ID 值。</br>![应用程序的属性窗格](images/SAML11/fig8-propertiespane.png)</br>
7. 使用您捕获的值，请确保您在步骤 3 中设置表类似于下面的表 1。


| 捕获的表 1： 值  |  |
|---------|---------|
|领域 | `urn:sharepoint:portal.contoso.local` |
|SAML 签名证书文件的完整路径 | `C:/temp/SharePoint SAML Integration.cer`  |
|SAML 单一登录服务 URL （替换 /wsfed /saml2） | `https://login.microsoftonline.com/b1726649-b616-460d-8d20-defab80d476c/wsfed` |
|应用程序对象 ID | `a812f48b-d1e4-4c8e-93be-e4808c8ca3ac` |

> [!IMPORTANT]
> 在 URL */saml2*值替换为 */wsfed*。*/Saml2*终结点将处理 SAML 2.0 令牌。*/Wsfed*终结点启用处理 SAML 1.1 令牌，并需要 SharePoint 2016 SAML 联合身份验证。

## <a name="step-4-configure-a-new-trusted-identity-provider-in-sharepoint-server-2016"></a>步骤 4： 在 SharePoint Server 2016 中配置新的受信任的身份提供程序

登录到 SharePoint Server 2016 服务器，然后打开 SharePoint 2016 命令行管理程序。填写 $realm、 $wsfedurl 和 $filepath 从表 1 的值并运行以下命令以配置新的受信任的身份提供程序。

> [!TIP]
> 如果您使用 PowerShell 新手，或要了解有关 PowerShell 的工作原理的详细信息，请参阅[SharePoint PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/overview?view=sharepoint-ps)。 

```
$realm = "<Realm from Table 1>"
$wsfedurl="<SAML single sign-on service URL from Table 1>"
$filepath="<Full path to SAML signing certificate file from Table 1>"
$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filepath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
$map = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" -IncomingClaimTypeDisplayName "name" -LocalClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"
$map2 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname" -IncomingClaimTypeDisplayName "GivenName" -SameAsIncoming
$map3 = New-SPClaimTypeMapping -IncomingClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname" -IncomingClaimTypeDisplayName "SurName" -SameAsIncoming
$ap = New-SPTrustedIdentityTokenIssuer -Name "AzureAD" -Description "SharePoint secured by Azure AD" -realm $realm -ImportTrustCertificate $cert -ClaimsMappings $map,$map2,$map3 -SignInUrl $wsfedurl -IdentifierClaim "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name"
```

接下来，执行以下步骤来启用的受信任的身份提供程序应用程序：
1. 在管理中心中，导航到**管理 Web 应用程序**，然后选择您希望与 Azure AD 安全的 web 应用程序。 
2. 在功能区中，单击**验证提供程序**，然后选择您想要使用的区域。
3. 选择**受信任标识提供程序**并选择的标识提供程序只需注册名为*AzureAD*。  
4. 登录页 URL 设置，请选择**自定义登录页**，并提供"/_trust/"的值。 
5. 单击“确定”****。

![配置验证提供程序](images/SAML11/fig10-configauthprovider.png)

> [!IMPORTANT]
> 务必执行所有步骤，包括自定义登录设置"/_trust/"页中，如下所示。除非时遵循所有步骤，配置将无法正常工作。

## <a name="step-5-set-the-permissions"></a>步骤 5： 设置权限

将登录到 Azure AD 和访问 SharePoint 的用户必须被授予访问应用程序。 

1. 在 Azure 门户中，打开 Azure AD 目录。单击**企业应用程序**，然后单击**所有应用程序**。单击以前创建的应用程序 （SharePoint SAML 集成）。
2. 单击**用户和组**。 
3. 单击**添加用户**以添加用户或组拥有权限登录到 SharePoint 使用 Azure AD。
4. 选择用户或组，然后单击**分配**。
 
用户已被授予在 Azure AD 权限，但还必须被授予 SharePoint 中的权限。使用以下步骤可设置访问 web 应用程序的权限。

1. 在管理中心中，单击“应用程序管理”****。
2. 在"应用程序管理"页上的"Web 应用程序"部分，单击"管理 Web 应用程序"。
3. 单击适当的 Web 应用程序，然后单击"用户策略"。
4. 在 Web 应用程序的策略，单击**添加用户**。</br>![按其名称声明搜索的用户](images/SAML11/fig11-searchbynameclaim.png)</br>
5. 在"添加用户"对话框中，单击"区域"中的适当区域，然后单击"下一步"。
6. 在**Web 应用程序的策略**对话框的**选择用户**部分中，单击**浏览**图标。
7. 在**查找**文本框中，键入您的目录中的用户的登录名并单击**搜索**。 </br>示例： *demouser@blueskyabove.onmicrosoft.com*。
8. 在列表视图中 AzureAD 标题下，选择名称属性，单击**添加**，然后单击**确定**关闭对话框。
9. 在权限中，单击**完全控制**。</br>![向声明用户授予完全控制](images/SAML11/fig12-grantfullcontrol.png)</br>
10. 单击“完成”****，然后单击“确定”****。

## <a name="step-6-add-a-saml-11-token-issuance-policy-in-azure-ad"></a>步骤 6: Azure AD 中添加的 SAML 1.1 令牌颁发策略

在门户中创建 Azure AD 应用程序后，它默认为使用 SAML 2.0。SharePoint Server 2016 需要的 SAML 1.1 令牌格式。以下脚本将删除默认 SAML 2.0 策略，并向问题 SAML 1.1 令牌中添加新的策略。 

> 此代码需要下载附带的[示例演示与 Azure Active Directory 图表交互](https://github.com/kaevans/spsaml11/tree/master/scripts)。如果您从 GitHub 到 Windows 桌面 ZIP 文件下载脚本，请确保取消阻止`MSGraphTokenLifetimePolicy.psm1`脚本模块文件和`Initialize.ps1`脚本文件 （右键单击属性、 选择取消阻止，请单击确定）。![阻塞下载文件](images/SAML11/fig17-unblock.png)

示例脚本下载后，创建新的 PowerShell 脚本使用下面的代码，将下载的文件路径替换为占位符`Initialize.ps1`本地计算机上。应用程序的对象 ID 占位符替换为您在表 1 中输入的应用程序对象 ID。创建后，执行 PowerShell 脚本。 

```
function AssignSaml11PolicyToAppPrincipal
{
    Param(
        [Parameter(Mandatory=$true)]
        [string]$pathToInitializeScriptFile, 
        [Parameter(Mandatory=$true)]
        [string]$appObjectid
    )

    $folder = Split-Path $pathToInitializeScriptFile
    Push-Location $folder

    #Loads the dependent ADAL module used to acquire tokens
    Import-Module $pathToInitializeScriptFile 

    #Gets the existing token issuance policy
    $existingTokenIssuancePolicy = Get-PoliciesAssignedToServicePrincipal -servicePrincipalId $appObjectid | ?{$_.type -EQ "TokenIssuancePolicy"} 
    Write-Host "The following TokenIssuancePolicy policies are assigned to the service principal." -ForegroundColor Green
    Write-Host $existingTokenIssuancePolicy -ForegroundColor White
    $policyId = $existingTokenIssuancePolicy.objectId

    #Removes existing token issuance policy
    Write-Host "Only a single policy can be assigned to the service principal. Removing the existing policy with ID $policyId" -ForegroundColor Green
    Remove-PolicyFromServicePrincipal -policyId $policyId -servicePrincipalId $appObjectid

    #Creates a new token issuance policy and assigns to the service principal
    Write-Host "Adding the new SAML 1.1 TokenIssuancePolicy" -ForegroundColor Green
    $policy = Add-TokenIssuancePolicy -DisplayName SPSAML11 -SigningAlgorithm "http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" -TokenResponseSigningPolicy TokenOnly -SamlTokenVersion "1.1"
    Write-Host "Assigning the new SAML 1.1 TokenIssuancePolicy $policy.objectId to the service principal $appObjectid" -ForegroundColor Green
    Set-PolicyToServicePrincipal -policyId $policy.objectId -servicePrincipalId $appObjectid
    Pop-Location
}

#Only edit the following two variables
$pathToInitializeScriptFile = "<file path of Initialize.ps1>"
$appObjectid = "<Application Object ID from Table 1>"

AssignSaml11PolicyToAppPrincipal $pathToInitializeScriptFile $appObjectid
```
> [!IMPORTANT]
> 未签名的 PowerShell 脚本，系统可能提示您设置执行策略。执行策略的详细信息，请参阅[有关执行策略](http://go.microsoft.com/fwlink/?LinkID=135170)。此外，您可能需要打开提升的命令提示符处，若要成功执行示例脚本中包含的命令。

这些示例 PowerShell 命令是如何对图形 API 执行查询的示例。使用 Azure AD 的令牌颁发策略的详细信息，请参阅[图 API 参考 （英文） 策略操作](https://msdn.microsoft.com/en-us/library/azure/ad/graph/api/policy-operations#create-a-policy)。

## <a name="step-7-verify-the-new-provider"></a>步骤 7： 确认新的提供程序

打开浏览器中为您在前面的步骤中配置的 web 应用程序的 URL。将重定向以登录到 Azure AD。

![登录为联盟配置的 Azure AD](images/SAML11/fig13-examplesignin.png)

系统要求您是否要保持登录状态。

![保持登录状态？](images/SAML11/fig14-staysignedin.png)

最后，您可以访问网站以从 Azure Active Directory 租户的用户身份登录。

![用户登录到 SharePoint](images/SAML11/fig15-signedinsharepoint.png)

## <a name="managing-certificates"></a>管理证书
务必要了解已配置为在第 4 步中的受信任的身份提供程序的签名证书已到期日期，并且必须进行更新。在续订证书，请参阅文章[管理联合单一登录 Azure Active Directory 中的证书](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-sso-certs)的信息。一旦在 Azure AD 中已经续订证书，下载到本地文件，并使用以下脚本续订签名证书配置受信任的身份提供程序。 

```
$filepath="<Full path to renewed SAML signing certificate file>"
$cert= New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($filePath)
New-SPTrustedRootAuthority -Name "AzureAD" -Certificate $cert
Get-SPTrustedIdentityTokenIssuer "AzureAD" | Set-SPTrustedIdentityTokenIssuer -ImportTrustCertificate $cert
```
## <a name="configuring-one-trusted-identity-provider-for-multiple-web-applications"></a>配置一个受信任的身份提供程序的多个 web 应用程序
配置适用于单个 web 应用程序，但如果您打算使用相同的受信任的身份提供程序的多个 web 应用程序需要其他配置。例如，假定我们已经扩展 web 应用程序使用的 URL `https://portal.contoso.local` ，现在要对用户进行身份验证`https://sales.contoso.local`以及。若要执行此操作，我们需要更新要服从 WReply 参数和 Azure AD 将答复 URL 中更新应用程序注册的标识提供程序。

1. 在 Azure 门户中，打开 Azure AD 目录。单击**应用程序注册**，然后单击**查看所有应用程序**。单击以前创建的应用程序 （SharePoint SAML 集成）。
2. 单击**设置**。
3. 在设置刀片中，单击**回复 Url**。 
4. 添加的其他 web 应用程序的 URL`/_trust/default.aspx`追加到 URL (如`https://sales.contoso.local/_trust/default.aspx`) 并单击**保存**。 
5. 在 SharePoint 服务器上，打开**SharePoint 2016 命令行管理程序**并执行以下命令，将使用您以前使用的受信任的身份令牌颁发者的名称。

```
$t = Get-SPTrustedIdentityTokenIssuer "AzureAD"
$t.UseWReplyParameter=$true
$t.Update()
```
6. 在管理中心，转到的 web 应用程序，并启用的现有的受信任的身份提供程序。请记住还配置为自定义登录页的登录页 URL `/_trust/`。
7. 在管理中心内，单击 web 应用程序，然后选择**用户策略**。添加具有适当权限的用户，如本文中前面所述。

## <a name="fixing-people-picker"></a>修复人员选取器
用户现在可以登录到 SharePoint 2016 使用从 Azure AD 的标识，但仍有机会改善用户体验。例如，搜索用户在人员选取器中显示多个搜索结果。没有为每个声明映射中创建的 3 的声明类型的搜索结果。若要选择使用人员选取器的用户，必须完全键入用户姓名并选择**名称**声明结果。

![声明搜索结果](images/SAML11/fig16-claimssearchresults.png)

这会导致拼写错误，搜索值没有验证或意外选择错误声明类型，如**姓**分配的用户声明。这样可以防止用户成功访问资源。

为了帮助这种情况下，没有打开源解决方案调用[AzureCP](https://yvand.github.io/AzureCP/) SharePoint 2016 提供自定义声明提供程序。它将使用 Azure AD 图形来解析用户输入并执行验证。有关详细信息[AzureCP](https://yvand.github.io/AzureCP/)。 

## <a name="additional-resources"></a>其他资源

[了解 WS-Federation](https://go.microsoft.com/fwlink/p/?linkid=188052)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
  
## <a name="join-the-discussion"></a>加入讨论

|**联系我们**|**说明**|
|:-----|:-----|
|**你需要什么样的解决方案？** <br/> |我们正在为跨多个 Microsoft 产品和服务的解决方案创建内容。请告诉我们你对我们的跨服务器解决方案的想法，或者发送电子邮件到 [MODAcontent@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20) 寻求具体的解决方案。<br/> |
|**参加解决方案讨论** <br/> |如果热衷于基于云的解决方案，请考虑加入云采用咨询委员会 (CAAB)，以便与充满活力的更大规模社区保持联络，其中包括 Microsoft 内容开发人员、行业专家和全球各地的客户。若要加入，请将自己添加为 Microsoft 技术社区的[云采用咨询委员会 (CAAB) 空间](https://aka.ms/caab)成员，并向我们 ([CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)) 发送电子邮件。任何人都可以阅读 [CAAB 博客](https://blogs.technet.com/b/solutions_advisory_board/)上与社区相关的内容。不过，CAAB 成员可获邀参加私人网络研讨会，了解新云采用资源和解决方案。<br/> |
|**获取您在此处看到的图片** <br/> |若要获取本文中图片的可编辑副本，请告诉我们，我们非常乐意发送副本。请通过电子邮件方式将请求（包括图片的 URL 和标题）发送到 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)。<br/> |
   

