---
title: 非路由的域准备进行目录同步
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_SetupDirSyncLocalDir
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: 了解您有一个非 routale 域与 Office 365 同步之前与内部部署用户相关联时如何操作。
ms.openlocfilehash: 9ec96c34e1dc4a6c755ea97fce3f5f2a5ba21bb3
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674436"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>非路由的域准备进行目录同步
将内部部署目录同步与 Office 365 时必须具有 Azure Active Directory 中的已验证的域。仅用户主体名称 (UPN) 与内部部署域同步。但是，包含非路由的域，例如.local （如 billa@contoso.local)，任何 UPN 将同步到。 onmicrosoft.com 域 （如 billa@contoso.onmicrosoft.com)。 

如果您当前使用.local 域用户帐户在 Active Directory 中建议您更改它们以正确同步您的 Office 365 域与使用已验证的域 （如 billa@contoso.com)。
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>如果只需.local 内部部署域？

最近工具可用于将您的 Active Directory 与 Azure Active Directory 同步名为 Azure AD 连接。有关详细信息，请参阅[将您的本地标识与 Azure Active Directory 集成](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)。
  
Azure AD 连接同步用户的 UPN 和密码，以便用户可以对这些用户使用在本地使用相同的凭据。但是，Azure AD 连接仅同步到 Office 365 验证的域的用户。这意味着，还验证域的 Azure Active Directory 因为由 Azure Active Directory 管理 Office 365 标识。换句话说，域必须是有效的 Internet 域 （例如，.com、.org、.net、.us 等。）。如果内部 Active Directory 只使用不可路由的域 (例如，.local)，这可能不能与 Office 365 具有的已验证的域匹配。通过更改您的主域您本地 Active Directory 中或通过添加一个或多个 UPN 后缀，可以解决此问题。
  
### <a name="change-your-primary-domain"></a>**更改您的主域**

更改为已验证在 Office 365 中，例如，contoso.com 域的主要域。每个用户都具有域 contoso.local 然后更新为 contoso.com。有关说明，请参阅[域重命名的工作方式](https://go.microsoft.com/fwlink/p/?LinkId=624174)。但是，这是一个非常所涉及的过程，并且更简单的解决方案是到[添加的 UPN 后缀，并更新其对用户](prepare-a-non-routable-domain-for-directory-synchronization.md#bk_register)，如下节中所示。
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**添加的 UPN 后缀和为其更新您的用户**

您可以解决.local 问题您在 Office 365 中通过在 Active Directory 以匹配 （或多个域） 中注册新的 UPN 后缀或后缀的验证。注册新的后缀后，您将更新用户的 Upn，使用户帐户类似 billa@contoso.com.local 替换示例的新域名。
  
更新 Upn 用于的已验证的域后，即可将您的本地 Active Directory 与 Office 365 同步。
  
 **步骤 1： 添加新的 UPN 后缀**
  
1. 在服务器上的 Active Directory 域服务 (AD DS) 上运行，在服务器管理器中选择**工具** \> **Active Directory 域和信任关系**。
    
    **或者，如果您没有 Windows Server 2012**
    
    按**Windows 密钥 + R**以打开**运行**对话框中，并 Domain.msc，然后键入，然后选择**确定**。
    
    ![选择 Active Directory 域和信任关系。](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. 在**Active Directory 域和信任关系**窗口中，右键单击**Active Directory 域和信任关系**，，然后选择**属性**。
    
    ![右键单击与 active Directory 域和信任关系，然后选择属性](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. 在**UPN 后缀**选项卡上，在**备用 UPN 后缀**框中，键入新的 UPN 后缀或后缀，并选择**添加** \> **应用**。
    
    ![添加新的 UPN 后缀](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    当您完成时添加后缀，请选择**确定**。 
    
 **步骤 2： 更改现有用户的 UPN 后缀**
  
1. 在服务器上的 Active Directory 域服务 (AD DS) 上运行，在服务器管理器中选择**工具** \> **Active Directory Active Directory 用户和计算机**。
    
    **或者，如果您没有 Windows Server 2012**
    
    按**Windows 密钥 + R**以打开**运行**对话框中，然后键入 Dsa.msc，，然后单击**确定**
    
2. 选择一个用户，右键单击，然后选择**属性**。
    
3. **帐户**选项卡上，在 UPN 后缀下拉列表，选择新的 UPN 后缀，，然后选择**确定**。
    
    ![添加新的用户的 UPN 后缀](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. 完成这些步骤的每个用户。
    
    另外，您可以批量更新 UPN 后缀[还可以使用 Windows PowerShell，可以更改所有用户的 UPN 后缀](prepare-a-non-routable-domain-for-directory-synchronization.md#BK_Posh)。
    
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**您还可以使用 Windows PowerShell 更改所有用户的 UPN 后缀**

如果您有大量的用户更新，则更轻松地使用 Windows PowerShell。下面的示例使用[Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312)和[设置 ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) cmdlet 更改为 contoso.com 的所有 contoso.local 后缀。 

运行下面的 Windows PowerShell 命令，以更新为 contoso.com 的所有 contoso.local 后缀：
    
  ```
  $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*contoso.local'} -Properties userPrincipalName -ResultSetSize $null
  ```

  ```
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("contoso.local","contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```
请参阅[Active Directory Windows PowerShell 模块](https://go.microsoft.com/fwlink/p/?LinkId=624314)，若要了解有关在 Active Directory 中使用 Windows PowerShell 的详细信息。 

