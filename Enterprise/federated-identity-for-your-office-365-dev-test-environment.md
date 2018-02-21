---
title: "用于 Office 365 开发/测试环境的联合身份"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: "摘要： 配置联合身份验证为您的 Office 365 开发/测试环境。"
ms.openlocfilehash: 8458e8e11547c14e479a64d037707d5292afcc02
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a>用于 Office 365 开发/测试环境的联合身份

 **摘要：**配置联合身份验证为您的 Office 365 开发/测试环境。
  
Office 365 支持联合的身份。这意味着，而不是执行本身的凭据验证，Office 365 指连接用户 Office 365 提供信任的联合身份验证服务器。如果用户的凭据正确无误，联合身份验证服务器颁发安全令牌的客户端会发送到 Office 365 作为身份验证的凭据。联合的身份允许卸载和纵深的 Office 365 订阅和高级身份验证和安全方案的身份验证。
  
本文介绍了如何为 Office 365 开发/测试环境配置联合身份验证，从而实现以下配置：
  
**图 1: 联合身份验证为 Office 365 的开发/测试环境的**

![添加到用于 Office 365 开发/测试环境的 DirSync 的 Web 应用程序代理服务器](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
图 1 中的配置包括：  
  
- Office 365 E5 试用订阅，从你创建它起 30 天内过期。
    
- 连接 Internet 的简化组织 Intranet，由 Azure 虚拟网络子网中的五个虚拟机（DC1、APP1、CLIENT1、ADFS1 和 PROXY1）组成。Azure AD Connect 在 APP1 上运行，以便将 Windows Server AD 域中的帐户列表同步到 Office 365。PROXY1 接收传入的身份验证请求。ADFS1 使用 DC1 验证凭据并颁发安全令牌。
    
设置此开发/测试环境分为五个阶段：
  
1. 创建包含 DirSync 的模拟企业 Office 365 开发/测试环境。
    
2. 创建 AD FS 服务器 (ADFS1)。
    
3. 创建 Web 代理服务器 (PROXY1)。
    
4. 创建自签名证书并配置 ADFS1 和 PROXY1。
    
5. 为 Office 365 配置联合身份。
    
若要单步执行生产环境中部署 Office 365 Azure 中的联合身份验证，请参阅[Office 365 Azure 中部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。
  
> [!NOTE]
> 无法使用 Azure 试用订阅配置此开发/测试环境。 
  
> [!TIP]
> 单击[此处](http://aka.ms/catlgstack)为可视化映射到一个 Microsoft 云测试实验室指南堆栈中的所有项目。
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a>阶段 1：创建包含 DirSync 的模拟企业 Office 365 开发/测试环境

请按照[您 Office 365 的开发/测试环境的目录同步](dirsync-for-your-office-365-dev-test-environment.md)的说明进行操作以 APP1 作为目录同步服务器和同步的标识 Office 365 和 Windows 服务器 AD 之间创建 Office 365 的模拟的企业开发/测试环境在 DC1 上的帐户。
  
接下来，创建新公共 DNS 域的名称基于您当前域的名称并将其添加到您的 Office 365 订购。我们建议使用名称**测试实验室。**\<公共域 >。例如，如果 contoso.com 公共域名，则添加公共域的名称 testlab.contoso.com。
  
有关如何在您的 DNS 提供商创建了正确的 DNS 记录和域添加到 Office 365 的试用订阅的说明，请参阅[添加用户和域添加到 Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)。 
  
生成的配置如下。
  
**图 2： 为 Office 365 的开发/测试环境的的目录同步**

![DirSync 的 Office 365 开发/测试环境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
图 2 展示了用于 Office 365 开发/测试环境的 DirSync，其中包括 Office 365 和 Azure 虚拟网络中的 CLIENT1、APP1 和 DC1 虚拟机。
  
## <a name="phase-2-create-the-ad-fs-server"></a>阶段 2：创建 AD FS 服务器

AD FS 服务器在 Office 365 和 DC1 上托管的 corp.contoso.com 域中的帐户之间提供联合身份验证。
  
要创建为 ADFS1 Azure 的虚拟机，请填入您的订购的资源组和 Azure 位置您的基本配置，然后在 Azure PowerShell 命令提示符下运行这些命令，您的本地计算机上。
  
```
$subscr="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
Login-AzureRMAccount
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
$staticIP="10.0.0.100"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzureRMNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!TIP]
> 单击[此处](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0)以获取包含本文中的所有 PowerShell 命令的文本文件。
  
接下来，使用[Azure 门户](http://portal.azure.com)连接到 ADFS1 虚拟机使用 ADFS1 本地管理员帐户名和密码，然后再打开 Windows PowerShell 命令提示符。
  
若要检查 ADFS1 和 DC1 之间的名称解析和网络通信，请运行**ping dc1.corp.contoso.com**命令，验证存在四个答复。
  
接下来，在 ADFS1 上的 Windows PowerShell 提示符处运行下面这些命令，将 ADFS1 虚拟机加入 CORP 域。
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

下面是生成的配置。
  
**图 3： 添加 AD FS 服务器**

![添加到用于 Office 365 开发/测试环境的 DirSync 的 AD FS 服务器](images/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
图 3 展示了如何将 ADFS1 服务器添加到用于 Office 365 开发/测试环境的 DirSync 中。
  
## <a name="phase-3-create-the-web-proxy-server"></a>阶段 3：创建 Web 代理服务器

PROXY1 在尝试进行身份验证的用户和 ADFS1 之间提供身份验证消息代理。
  
若要为 PROXY1 创建 Azure 虚拟机，请填写资源组名称和 Azure 位置，然后在本地计算机上的 Azure PowerShell 命令提示符处运行下面这些命令。
  
```
$rgName="<the resource group name of your Base Configuration>"
$staticIP="10.0.0.101"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzureRMNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> PROXY1 分配有一个静态公共 IP 地址，因为将创建一个指向它的公共 DNS 记录，并且它不得在 PROXY1 虚拟机重启时有变化。 
  
接下来，添加一个规则，为企业网络子网的网络安全组允许未经请求的入站的通信从互联网 PROXY1 的专用 IP 地址和 TCP 端口 443。在 Azure PowerShell 命令提示符下运行这些命令，您的本地计算机上。
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzureRmNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzureRmNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzureRmNetworkSecurityGroup
```

接下来，使用[Azure 门户](http://portal.azure.com)连接到 PROXY1 虚拟机使用 PROXY1 本地管理员帐户名和密码，然后再打开 Windows PowerShell 命令提示符上 PROXY1。
  
若要检查 PROXY1 和 DC1 之间的名称解析和网络通信，请运行**ping dc1.corp.contoso.com**命令，验证存在四个答复。
  
接下来，在 PROXY1 上的 Windows PowerShell 提示符处运行下面这些命令，将 PROXY1 虚拟机加入 CORP 域。
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

在本地计算机上运行以下 Azure PowerShell 命令，显示 PROXY1 的公共 IP 地址：
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

接下来，使用公用 DNS 提供程序并创建新的公用 DNS A 记录的**fs.testlab。**\<您的 DNS 域名 >**写主机**命令所显示的 IP 地址解析。**Fs.testlab。**\<您的 DNS 域名 > 此后称为*联合身份验证服务 FQDN* 。
  
接下来，使用[Azure 门户](http://portal.azure.com)连接到 DC1 虚拟机使用 CORP\\在管理员级别的 Windows PowerShell 命令提示符的 User1 凭据，然后运行以下命令：
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

这些命令可为 Azure 虚拟网络上的虚拟机能够解析为 ADFS1 专用 IP 地址的联合身份验证服务 FQDN 创建 DNS A 记录。
  
下面是生成的配置。
  
**图 4： 添加 web 应用程序代理服务器**

![添加到用于 Office 365 开发/测试环境的 DirSync 的 Web 应用程序代理服务器](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
图 4 展示了如何添加 PROXY1 服务器。
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>阶段 4：创建自签名证书并配置 ADFS1 和 PROXY1

在此阶段，将为联合身份验证服务 FQDN 创建自签名数字证书，并将 ADFS1 和 PROXY1 配置为 AD FS 场。
  
首先，使用[Azure 门户](http://portal.azure.com)连接到 DC1 虚拟机使用 CORP\\User1 凭据，然后打开管理员级 Windows PowerShell 命令提示符。
  
接下来，在 DC1 上的 Windows PowerShell 命令提示符处运行以下命令，创建 AD FS 服务帐户：
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

请注意，此命令会提示你提供帐户密码。选择强密码，然后在安全位置记录此密码。此阶段和阶段 5 都要用到它。
  
使用[Azure 门户](http://portal.azure.com)连接到 ADFS1 虚拟机使用 CORP\\User1 凭据。打开管理员级别的 Windows PowerShell 命令提示符上 ADFS1，填写您的联合身份验证服务 FQDN，然后运行以下命令以创建一个自签名的证书：
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\\LocalMachine\\My"
New-Item -path c:\\Certs -type directory
New-SmbShare -name Certs -path c:\\Certs -changeaccess CORP\\User1
```

接下来，按下面这些步骤操作，将新建的自签名证书保存为文件。
  
1. 单击**开始**，键入**mmc.exe**，，然后按**enter 键**。
    
2. 单击**文件 > 添加/删除管理单元**。
    
3. 在中**添加或删除管理单元**，可用的管理单元的列表中双击**证书**、 单击**计算机帐户**，然后单击**下一步**。
    
4. 在**选择计算机**，单击**完成**，然后单击**确定**。
    
5. 在树窗格中，打开**证书 （本地计算机） > 个人 > 证书**。
    
6. 用鼠标右键单击带有您联合身份验证服务 FQDN 的证书，单击**所有任务**，然后单击**导出**。
    
7. 在**欢迎**页上，单击**下一步**。
    
8. 在**导出私钥**页中，单击**是**，，然后单击**下一步**。
    
9. 在**导出文件格式**页中，单击**导出所有扩展的属性**，然后单击**下一步**。
    
10. 在**安全**页中，单击**密码**并在**密码**中键入的密码和**确认密码。**
    
11. 在**导出文件**页中，单击**浏览**。
    
12. 浏览到**c:\\证书**文件夹中，在**文件名**中键入**SSL** ，然后单击**保存。**
    
13. 在**导出文件**页中，单击**下一步**。
    
14. 在**正在完成证书导出向导**页上，单击**完成**。出现提示时，单击**确定**。
    
接下来，在 ADFS1 上的 Windows PowerShell 命令提示符处运行以下命令，安装 AD FS 服务：
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

等待安装完成。
  
接下来，按下面这些步骤操作，配置 AD FS 服务：
  
1. 单击**开始**，然后单击**服务器管理器**图标。
    
2. 在树窗格中的服务器管理器中，单击**AD FS**。
    
3. 在顶部的工具栏，橙色警告符号，请单击，然后单击**配置联合身份验证服务在此服务器上**。
    
4. 在 Active Directory 联合身份验证服务配置向导的**欢迎**页上，单击**下一步**。
    
5. 在**连接到 AD DS**页上，单击**下一步**。
    
6. 在**指定服务属性**页上：
    
  - **SSL 证书**，请单击向下箭头，然后单击具有您联合身份验证服务 FQDN 名称的证书。
    
  - 在**联合身份验证服务显示名称**中，键入虚拟组织的名称。
    
  - 单击"下一步"。
    
7. 在**指定服务帐户**页上的**帐户名称**单击**选择**。
    
8. 在中**选择的用户或服务帐户**，键入**ADFS 服务**，单击**检查名称**，然后单击**确定**。
    
9. 在**帐户密码**，键入 ADFS 服务帐户的密码，然后单击**下一步**。
    
10. 在**指定配置数据库**页上，单击**下一步**。
    
11. 在**查看选项**页中，单击**下一步**。
    
12. 在**先决条件检查**页上，单击**配置**。
    
13. 在**结果**页上，单击**关闭**。
    
14. 单击**开始**，单击该电源图标，**请重新启动**，请单击，然后单击**继续**。
    
从[Azure 的门户](http://portal.azure.com)，连接到 PROXY1 公司与\\User1 帐户凭据。
  
接下来，按下面这些步骤操作，安装自签名证书并配置 PROXY1。
  
1. 单击**开始**，键入**mmc.exe**，，然后按**enter 键**。
    
2. 单击**文件 > 添加/删除管理单元**。
    
3. 在中**添加或删除管理单元**，可用的管理单元的列表中双击**证书**、 单击**计算机帐户**，然后单击**下一步**。
    
4. 在**选择计算机**，单击**完成**，然后单击**确定**。
    
5. 在树窗格中，打开**证书 （本地计算机） > 个人 > 证书**。
    
6. 右键单击**个人**，单击**所有任务**，然后单击**导入**。
    
7. 在**欢迎**页上，单击**下一步**。
    
8. 在**导入的文件**页中，键入**\\ \\adfs1\\证书\\ssl.pfx**，然后单击**下一步**。
    
9. 在**私钥保护**页上，在**密码**框中，键入证书密码，然后单击**下一步。**
    
10. 在**证书存储**页上，单击**下一步。**
    
11. 在**完成**页上，单击**完成**。
    
12. 在**证书存储**页上，单击**下一步**。
    
13. 出现提示时，单击**确定**。
    
14. 在树窗格中，单击**证书**。
    
15. 用鼠标右键单击证书，然后单击**复制**。
    
16. 在树窗格中，打开**受信任的根证书颁发机构 > 证书**。
    
17. 移动鼠标指针下方列表中的已安装的证书，单击鼠标右键，然后单击**粘贴**。
    
打开管理员级 PowerShell 命令提示符，然后运行以下命令：
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

等待安装完成。
  
按下面这些步骤操作，将 Web 应用程序代理服务配置为使用 ADFS1 作为其联合服务器：
  
1. 单击**开始**，然后单击**服务器管理器**。
    
2. 在树窗格中，单击**远程访问**。
    
3. 在顶部的工具栏，橙色警告符号，请单击，然后单击**打开 Web 应用程序代理服务器向导**。
    
4. 在 Web 应用程序代理服务器配置向导的**欢迎**页上，单击**下一步**。
    
5. 在**联合身份验证服务器**页上：
    
  - 在**联合身份验证服务名称**中键入联合身份验证服务 FQDN。
    
  - 类型**CORP\\User1**中**的用户名**。
    
  - 在**密码**中键入 User1 帐户的密码。
    
  - 单击"下一步"。
    
6. 在**AD FS 代理证书**页面上，单击向下箭头，单击证书与联合身份验证服务 FQDN，然后单击**下一步**。
    
7. 在**确认**页上，单击**配置**。
    
8. 在**结果**页上，单击**关闭**。
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a>阶段 5：为 Office 365 配置联合身份

CORP app1 发出虚拟机连接使用[Azure 的门户网站](http://portal.azure.com)\\User1 帐户凭据。
  
按下面这些步骤操作，为 Azure AD Connect 和 Office 365 订阅配置联合身份验证：
  
1. 在桌面上，双击**Azure AD 连接**。
    
2. 在**欢迎使用 Azure AD 连接**页面上，单击**配置**。
    
3. 在**附加任务**页中，单击**更改用户登录**，，然后单击**下一步**。
    
4. 在**连接到 Azure 的广告**页上，您 Office 365 提供全局管理员帐户名和密码，键入，然后单击**下一步**。
    
5. 在"用户登录"页上，依次单击"使用 AD FS 进行联合身份验证"和"下一步"。
    
6. 在**AD FS 服务器场**页上，单击**使用现有 AD FS 场**，在**服务器名称**中键入**ADFS1** ，然后单击**下一步**。
    
7. 当系统提示您输入服务器凭据，输入的凭据 CORP\\User1 帐户，然后再单击**确定**。
    
8. 在**域管理员**凭据页上，键入**CORP\\User1**中**的用户名**和**密码**，该帐户密码，然后单击**下一步**。
    
9. 在**AD FS 服务帐户**页上，键入**CORP\\ADFS 服务**中**域用户名**和帐户密码在**域用户的密码**，然后单击**下一步**。
    
10. 在**Azure AD 域**页面上，在**域**中，选择以前创建并添加到 Office 365 订阅在阶段 1 中的域的名称，然后单击**下一步**。
    
11. 在**开始配置**页上，单击**配置**。
    
12. 在**安装完成**页面中，单击**验证**。
    
    应该可以看到指明 Intranet 和 Internet 配置均已验证的消息。
    
13. 在"安装完成"页上，单击"退出"。
    
若要证明联合身份验证能够正常运行，请执行以下操作：
  
1. 打开一个新的专用实例的您在您的本地计算机上的浏览器并转到[https://portal.office.com](https://portal.office.com)。
    
2. 在登录凭据中，键入**用户 1 @**\<在阶段 1 中创建的域 >。 
    
    例如，如果测试域是**testlab.contoso.com**，则应键入**user1@testlab.contoso.com**。按 tab 键，或者允许 Office 365 可以自动将您重定向。
    
    您现在应该看到**您的连接是没有专用**页面。因为 ADFS1 不能验证您的桌面计算机上安装自签名的证书程序出现此错误。在生产部署中的联合身份验证，您将使用来自受信任的证书颁发机构的证书，您的用户不会看到此页。
    
3. 在**您的连接是没有专用的**页面上，单击**高级**，然后单击**进入\<联合身份验证服务 FQDN >**。 
    
4. 在包含虚构组织名称的页上，使用以下凭据登录：
    
  - **CORP\\用户 1**的名称
    
  - User1 帐户密码
    
    您应该看到**Microsoft Office**主页。
    
此过程演示 Office 365 的试用订阅与 Windows 服务器 AD corp.contoso.com 域承载在 DC1 上的联盟。这是基本的身份验证过程：
  
1. 在登录帐户名称中使用在阶段 1 创建的联盟域后，Office 365 将浏览器重定向到联合身份验证服务 FQDN 和 PROXY1。
    
2. PROXY1 向本地计算机发送虚构的公司登录页。
    
3. 当您发送 CORP\\User1 和 PROXY1 的密码，它将它们转发到 ADFS1。
    
4. ADFS1 验证 CORP\\User1 和 DC1 的密码并发送您的本地计算机的安全令牌。
    
5. 本地计算机向 Office 365 发送安全令牌。
    
6. Office 365 验证安全令牌是否由 ADFS1 创建，通过验证后允许访问。
    
现在，Office 365 试用订阅已配置了联合身份验证。可以将此开发/测试环境用于高级身份验证方案。
  
## <a name="next-step"></a>下一步

当准备好部署生产就绪后时，针对在 Azure，Office 365 提供高可用性联合身份验证请参见[Office 365 Azure 中部署高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。
  
## <a name="see-also"></a>另请参阅

[云采用测试实验室指南 (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基础配置开发/测试环境](base-configuration-dev-test-environment.md)
  
[Office 365 开发/测试环境](office-365-dev-test-environment.md)
  
[云应用和混合解决方案](cloud-adoption-and-hybrid-solutions.md)
  
[在 Azure 中部署 Office 365 的高可用性联合身份验证](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


