---
title: "用于 Office 365 开发/测试环境的 DirSync"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, TLG, Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "摘要： 需要配置目录同步为您 Office 365 的开发/测试环境。"
ms.openlocfilehash: fc3a28d52781ba5a541d223c9f8bc081251a2b07
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2018
---
# <a name="dirsync-for-your-office-365-devtest-environment"></a>用于 Office 365 开发/测试环境的 DirSync

 **摘要：**配置目录同步为您 Office 365 的开发/测试环境。
  
许多组织使用 Azure AD Connect 和目录同步 (DirSync)，将其本地 Windows Server Active Directory (AD) 林中的帐户集同步到 Office 365 中的帐户集。本文介绍了如何通过与 Office 365 开发/测试环境的密码同步添加 DirSync，从而生成以下配置。
  
![DirSync 的 Office 365 开发/测试环境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
此配置包括：  
  
- Office 365 E5 试用订阅，从你创建它起 30 天内过期。
    
- 连接到 Internet 的简化的组织 Intranet，包含 Azure 虚拟网络子网中的三个虚拟机（DC1、APP1 和 CLIENT1）。Azure AD Connect 在 APP1 上运行以便使 Windows Server AD 域同步到 Office 365。
    
设置此开发/测试环境包含两个阶段：
  
1. 创建 Office 365 开发/测试环境（Azure 虚拟网络中的 DC1、APP1 和 CLIENT1 虚拟机，有 Office 365 E5 试用订阅）。
    
2. 在 APP1 上安装和配置 Azure AD Connect。
    
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a>第 1 阶段：创建 Office 365 开发/测试环境

按照分阶段 1、 2 和 3 的[Office 365 的开发/测试环境](office-365-dev-test-environment.md)文章的说明。下面是生成的配置。
  
![Office 365 开发/测试环境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
此配置包括：  
  
- Office 365 E5 试用订阅。
    
- 连接到 Internet 的简化的组织 Intranet，包含 Azure 虚拟网络子网中的 DC1、APP1 和 CLIENT1 虚拟机。
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a>第 2 阶段：在 APP1 上安装 Azure AD Connect

安装和配置后，Azure AD Connect 将 CORP Windows Server AD 域中的帐户集与 Office 365 试用订阅中的帐户集同步。下面的过程将引导你完成在 APP1 上安装 Azure AD Connect 并验证它是否可以工作的步骤。
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a>安装和配置上 APP1 Azure AD 连接

1. 从[Azure 的门户](https://portal.azure.com)，连接到与 CORP APP1\\User1 帐户。
    
2. 在 APP1 中打开管理员级别的 Windows PowerShell 命令提示符，然后运行下面的命令：
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. 从任务栏中，单击**Internet Explorer** ，然后转到[https://aka.ms/aadconnect](https://aka.ms/aadconnect)。
    
4. 在 Microsoft Azure 活动目录连接页面上，单击**下载**，，然后单击**运行**。
    
5. 在**欢迎使用 Azure AD 连接**页面上，单击**我同意**，然后单击**继续**。
    
6. 在**快速设置**页上，单击**使用快速设置**。
    
7. 在**连接到 Azure 的广告**页上，在**用户名，**键入在**密码**的密码键入全局管理员帐户名称，然后单击**下一步**。
    
8. 在**连接到 AD DS**页上，键入**CORP\\User1**在**用户名，**请在**密码**框中，键入其密码，然后单击**下一步**。
    
9. 在**Azure 广告登录配置**页上，单击**不经验证的任何域的情况下继续**，然后单击**下一步**。
    
10. 在"准备配置"页上，单击"安装"。
    
11. 在**完成配置**页上，单击**退出**。
    
12. 在 Internet Explorer 中，请转到 Office 365 门户网站 ([https://portal.office.com](https://portal.office.com)) 和 Office 365 试用订阅使用全局管理员帐户登录。
    
13. 从主门户页面中，单击**管理**。
    
14. 在左边的导航，请单击**用户 > 活动用户**。
    
    请注意名为**User1**的帐户。此帐户是从 Windows 服务器 CORP AD 域，工作目录同步的证明。
    
15. 单击**User1**帐户。产品许可证，请单击**编辑**。
    
16. **产品许可证**，选择您的国家/地区，并**关闭**控件然后单击**Office 365 企业 E5** （切换为**On**）。单击**保存**底部的页，然后单击**关闭**。
    
下面是生成的配置。
  
![DirSync 的 Office 365 开发/测试环境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
此配置包括：  
  
- Office 365 E5 试用订阅。
    
- 连接到 Internet 的简化的组织 Intranet，包含 Azure 虚拟网络子网中的 DC1、APP1 和 CLIENT1 虚拟机。Azure AD Connect 在 APP1 上运行以便每隔 30 分钟使 Windows Server AD 域同步到 Office 365。
    
## <a name="next-step"></a>下一步

现在可以为您的组织中部署目录同步，请参阅[部署 Office 365 目录同步 （目录同步） Microsoft Azure 中](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)。

## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[Office 365 开发/测试环境的云应用程序安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[为您的 Office 365 开发/测试环境高级威胁防护](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)




