---
title: 用于 Office 365 开发/测试环境的联合身份
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/19/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: 摘要：为 Office 365 开发/测试环境配置联合身份验证。
ms.openlocfilehash: 9cee3ae308b5dc7e97b8711a9b021869478a47b4
ms.sourcegitcommit: ed9d80a7b4acc42065c94155122f0cdb86dccde6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "37046987"
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a><span data-ttu-id="97275-103">用于 Office 365 开发/测试环境的联合身份</span><span class="sxs-lookup"><span data-stu-id="97275-103">Federated identity for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="97275-104">**摘要：** 为 Office 365 开发/测试环境配置联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="97275-104">**Summary:** Configure federated authentication for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="97275-p101">Office 365 支持联合身份验证。也就是说，Office 365 将连接的用户转到 Office 365 信任的联合身份验证服务器，而不是自己执行凭据验证。如果用户的凭据正确，联合身份验证服务器会颁发安全令牌，然后客户端将此令牌作为通过身份验证的证明发送给 Office 365。借助联合身份，可以为 Office 365 订阅以及高级身份验证和安全方案卸载和扩展身份验证。</span><span class="sxs-lookup"><span data-stu-id="97275-p101">Office 365 supports federated identity. This means that instead of performing the validation of credentials itself, Office 365 refers the connecting user to a federated authentication server that Office 365 trusts. If the user's credentials are correct, the federated authentication server issues a security token that the client then sends to Office 365 as proof of authentication. Federated identity allows for the offloading and scaling up of authentication for an Office 365 subscription and advanced authentication and security scenarios.</span></span>
  
<span data-ttu-id="97275-109">本文介绍了如何为 Office 365 开发/测试环境配置联合身份验证，从而实现以下配置：</span><span class="sxs-lookup"><span data-stu-id="97275-109">This article describes how you can configure federated authentication for the Office 365 dev/test environment, resulting in the following:</span></span>
  
<span data-ttu-id="97275-110">**图 1：Office 365 开发/测试环境的联合身份验证**</span><span class="sxs-lookup"><span data-stu-id="97275-110">**Figure 1: The federated authentication for Office 365 dev/test environment**</span></span>

![Office 365 开发/测试环境的联合身份验证](media/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="97275-112">图 1 中的配置包括：</span><span class="sxs-lookup"><span data-stu-id="97275-112">The configuration shown in Figure 1 consists of:</span></span> 
  
- <span data-ttu-id="97275-113">Office 365 E5 试用订阅，从你创建它起 30 天内过期。</span><span class="sxs-lookup"><span data-stu-id="97275-113">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="97275-p102">连接 Internet 的简化组织 Intranet，由 Azure 虚拟网络子网中的五个虚拟机（DC1、APP1、CLIENT1、ADFS1 和 PROXY1）组成。Azure AD Connect 在 APP1 上运行，以便将 Active Directory 域服务域中的帐户列表同步到 Office 365。PROXY1 接收传入的身份验证请求。ADFS1 使用 DC1 验证凭据并颁发安全令牌。</span><span class="sxs-lookup"><span data-stu-id="97275-p102">A simplified organization intranet connected to the Internet, consisting of five virtual machines on a subnet of an Azure virtual network (DC1, APP1, CLIENT1, ADFS1, and PROXY1). Azure AD Connect runs on APP1 to synchronize the list of accounts in the Active Directory Domain Services domain to Office 365. PROXY1 receives the incoming authentication requests. ADFS1 validates credentials with DC1 and issues security tokens.</span></span>
    
<span data-ttu-id="97275-118">设置此开发/测试环境分为五个阶段：</span><span class="sxs-lookup"><span data-stu-id="97275-118">There are five phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="97275-119">创建包含 DirSync 的模拟企业 Office 365 开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="97275-119">Create the simulated enterprise Office 365 dev/test environment with DirSync.</span></span>
    
2. <span data-ttu-id="97275-120">创建 AD FS 服务器 (ADFS1)。</span><span class="sxs-lookup"><span data-stu-id="97275-120">Create the AD FS server (ADFS1).</span></span>
    
3. <span data-ttu-id="97275-121">创建 Web 代理服务器 (PROXY1)。</span><span class="sxs-lookup"><span data-stu-id="97275-121">Create the web proxy server (PROXY1).</span></span>
    
4. <span data-ttu-id="97275-122">创建自签名证书并配置 ADFS1 和 PROXY1。</span><span class="sxs-lookup"><span data-stu-id="97275-122">Create a self-signed certificate and configure ADFS1 and PROXY1.</span></span>
    
5. <span data-ttu-id="97275-123">为 Office 365 配置联合身份。</span><span class="sxs-lookup"><span data-stu-id="97275-123">Configure Office 365 for federated identity.</span></span>
    
<span data-ttu-id="97275-124">若要在 Azure 中逐步执行 Office 365 联合身份验证的生产部署，请参阅[Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="97275-124">To step through a production deployment of federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="97275-125">无法使用 Azure 试用订阅配置此开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="97275-125">You cannot configure this dev/test environment with an Azure Trial subscription.</span></span> 
  
> [!TIP]
> <span data-ttu-id="97275-126">单击[此处](http://aka.ms/catlgstack)可直观映射到 Office 365 测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="97275-126">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a><span data-ttu-id="97275-127">阶段 1：创建包含 DirSync 的模拟企业 Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="97275-127">Phase 1: Create the simulated enterprise Office 365 dev/test environment with DirSync</span></span>

<span data-ttu-id="97275-128">按照[适用于 Office 365 开发/测试环境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md) 中的说明操作，创建模拟企业 Office 365 开发/测试环境，使用 APP1 作为 DirSync 服务器，并在 Office 365 和 DC1 上的 AD DS 帐户之间同步身份。</span><span class="sxs-lookup"><span data-stu-id="97275-128">Follow the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to create the simulated enterprise Office 365 dev/test environment with APP1 as the DirSync server and synchronized identity between Office 365 and the AD DS accounts on DC1.</span></span>
  
<span data-ttu-id="97275-p103">接下来，根据当前的域名新建一个公共 DNS 域名，然后将其添加到 Office 365 订阅中。建议命名为 **testlab.**\<公共域>。例如，如果你的公共域名是 contoso.com，请添加公共域名 testlab.contoso.com。</span><span class="sxs-lookup"><span data-stu-id="97275-p103">Next, create a new public DNS domain name based on your current domain name and add it to your Office 365 subscription. We recommend using the name **testlab.**\<your public domain>. For example, if your public domain name is contoso.com, add the public domain name testlab.contoso.com.</span></span>
  
<span data-ttu-id="97275-132">有关如何在 DNS 提供程序中创建正确的 DNS 记录，并将域添加到 Office 365 试用订阅的说明，请参阅[将用户和域添加到 Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)。</span><span class="sxs-lookup"><span data-stu-id="97275-132">For instructions on how to create the correct DNS records in your DNS provider and add the domain to your Office 365 trial subscription, see [Add users and domain to Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).</span></span> 
  
<span data-ttu-id="97275-133">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="97275-133">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="97275-134">**图 2：Office 365 开发/测试环境的目录同步**</span><span class="sxs-lookup"><span data-stu-id="97275-134">**Figure 2: Directory synchronization for the Office 365 dev/test environment**</span></span>

![具有目录同步的 Office 365 开发/测试环境](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="97275-136">图 2 展示了用于 Office 365 开发/测试环境的目录同步，其中包括 Office 365 和 Azure 虚拟网络中的 CLIENT1、APP1 和 DC1 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="97275-136">Figure 2 shows the directory synchronizationc for Office 365 dev/test environment, which includes Office 365 and CLIENT1, APP1, and DC1 virtual machines in an Azure virtual network.</span></span>
  
## <a name="phase-2-create-the-ad-fs-server"></a><span data-ttu-id="97275-137">阶段 2：创建 AD FS 服务器</span><span class="sxs-lookup"><span data-stu-id="97275-137">Phase 2: Create the AD FS server</span></span>

<span data-ttu-id="97275-138">AD FS 服务器在 Office 365 和 DC1 上托管的 corp.contoso.com 域中的帐户之间提供联合身份验证。</span><span class="sxs-lookup"><span data-stu-id="97275-138">An AD FS server provides federated authentication between Office 365 and the accounts in the corp.contoso.com domain hosted on DC1.</span></span>
  
<span data-ttu-id="97275-139">若要为 ADFS1 创建 Azure 虚拟机，请填写基础配置的订阅和资源组名称及 Azure 位置，然后在本地计算机上的 Azure PowerShell 命令提示符处运行下面这些命令。</span><span class="sxs-lookup"><span data-stu-id="97275-139">To create an Azure virtual machine for ADFS1, fill in the name of your subscription and the resource group and Azure location for your Base Configuration, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$subscrName="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
Connect-AzAccount
Select-AzSubscription -SubscriptionName $subscrName
$staticIP="10.0.0.100"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```
<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) for a text file that has all the PowerShell commands in this article.
-->
  
<span data-ttu-id="97275-140">接下来，通过 [Azure 门户](http://portal.azure.com)使用 ADFS1 本地管理员帐户名称和密码连接 ADFS1 虚拟机，然后打开 Windows PowerShell 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="97275-140">Next, use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the ADFS1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="97275-141">若要检查 ADFS1 和 DC1 之间的名称解析和网络通信，请运行 **ping dc1.corp.contoso.com** 命令，然后查看是否存在四个答复。</span><span class="sxs-lookup"><span data-stu-id="97275-141">To check name resolution and network communication between ADFS1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="97275-142">接下来，在 ADFS1 上的 Windows PowerShell 提示符处运行下面这些命令，将 ADFS1 虚拟机加入 CORP 域。</span><span class="sxs-lookup"><span data-stu-id="97275-142">Next, join the ADFS1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on ADFS1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="97275-143">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="97275-143">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="97275-144">**图 3：添加 AD FS 服务器**</span><span class="sxs-lookup"><span data-stu-id="97275-144">**Figure 3: Adding the AD FS server**</span></span>

![添加到用于 Office 365 开发/测试环境的 DirSync 的 AD FS 服务器](media/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
<span data-ttu-id="97275-146">图 3 展示了如何将 ADFS1 服务器添加到用于 Office 365 开发/测试环境的 DirSync 中。</span><span class="sxs-lookup"><span data-stu-id="97275-146">Figure 3 shows the addition of the ADFS1 server to the DirSync for Office 365 dev/test environment.</span></span>
  
## <a name="phase-3-create-the-web-proxy-server"></a><span data-ttu-id="97275-147">阶段 3：创建 Web 代理服务器</span><span class="sxs-lookup"><span data-stu-id="97275-147">Phase 3: Create the web proxy server</span></span>

<span data-ttu-id="97275-148">PROXY1 在尝试进行身份验证的用户和 ADFS1 之间提供身份验证消息代理。</span><span class="sxs-lookup"><span data-stu-id="97275-148">PROXY1 provides proxying of authentication messages between users trying to authenticate and ADFS1.</span></span>
  
<span data-ttu-id="97275-149">若要为 PROXY1 创建 Azure 虚拟机，请填写资源组名称和 Azure 位置，然后在本地计算机上的 Azure PowerShell 命令提示符处运行下面这些命令。</span><span class="sxs-lookup"><span data-stu-id="97275-149">To create an Azure virtual machine for PROXY1, fill in the name of your resource group and Azure location, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
$staticIP="10.0.0.101"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="97275-150">PROXY1 分配有一个静态公共 IP 地址，因为将创建一个指向它的公共 DNS 记录，并且它不得在 PROXY1 虚拟机重启时有变化。</span><span class="sxs-lookup"><span data-stu-id="97275-150">PROXY1 is assigned a static public IP address because you will create a public DNS record that points to it and it must not change when you restart the PROXY1 virtual machine.</span></span> 
  
<span data-ttu-id="97275-p104">接下来，将规则添加到 CorpNet 子网的网络安全组中，以允许来自 Internet 未经请求的入站流量流入 PROXY1 的专用 IP 地址和 TCP 端口 443。在本地计算机上的 Azure PowerShell 命令提示符处，运行下面这些命令。</span><span class="sxs-lookup"><span data-stu-id="97275-p104">Next, add a rule to the network security group for the CorpNet subnet to allow unsolicited inbound traffic from the Internet to PROXY1's private IP address and TCP port 443. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

<span data-ttu-id="97275-153">接下来，通过 [Azure 门户](http://portal.azure.com)，使用 PROXY1 本地管理员帐户名称和密码连接 PROXY1 虚拟机，然后在 PROXY1 上打开 Windows PowerShell 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="97275-153">Next, use the [Azure portal](http://portal.azure.com) to connect to the PROXY1 virtual machine using the PROXY1 local administrator account name and password, and then open a Windows PowerShell command prompt on PROXY1.</span></span>
  
<span data-ttu-id="97275-154">若要检查 PROXY1 和 DC1 之间的名称解析和网络通信，请运行 **ping dc1.corp.contoso.com** 命令，然后查看是否存在四个答复。</span><span class="sxs-lookup"><span data-stu-id="97275-154">To check name resolution and network communication between PROXY1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="97275-155">接下来，在 PROXY1 上的 Windows PowerShell 提示符处运行下面这些命令，将 PROXY1 虚拟机加入 CORP 域。</span><span class="sxs-lookup"><span data-stu-id="97275-155">Next, join the PROXY1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on PROXY1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="97275-156">在本地计算机上运行以下 Azure PowerShell 命令，显示 PROXY1 的公共 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="97275-156">Display the public IP address of PROXY1 with these Azure PowerShell commands on your local computer:</span></span>
  
```
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

<span data-ttu-id="97275-p105">接下来，结合使用公共 DNS 提供程序，为解析为 **Write-Host** 命令显示的 IP 地址的 **fs.testlab.**\<DNS 域名> 新建一个公共 DNS A 记录。**fs.testlab.**\<DNS 域名> 以下称为*联合身份验证服务 FQDN*。</span><span class="sxs-lookup"><span data-stu-id="97275-p105">Next, work with your public DNS provider and create a new public DNS A record for **fs.testlab.**\<your DNS domain name> that resolves to the IP address displayed by the **Write-Host** command. The **fs.testlab.**\<your DNS domain name> is hereafter referred to as the  *federation service FQDN*  .</span></span>
  
<span data-ttu-id="97275-159">接下来，通过 [Azure 门户](http://portal.azure.com)，使用 CORP\\User1 凭据连接 DC1 虚拟机，然后在管理员级 Windows PowerShell 命令提示符处运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="97275-159">Next, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then run the following commands at an administrator-level Windows PowerShell command prompt:</span></span>
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

<span data-ttu-id="97275-160">这些命令可为 Azure 虚拟网络上的虚拟机能够解析为 ADFS1 专用 IP 地址的联合身份验证服务 FQDN 创建 DNS A 记录。</span><span class="sxs-lookup"><span data-stu-id="97275-160">These commands create a DNS A record for your federation service FQDN that virtual machines on the Azure virtual network can resolve to ADFS1's private IP address.</span></span>
  
<span data-ttu-id="97275-161">下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="97275-161">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="97275-162">**图 4：添加 Web 应用程序代理服务器**</span><span class="sxs-lookup"><span data-stu-id="97275-162">**Figure 4: Adding the web application proxy server**</span></span>

![添加到用于 Office 365 开发/测试环境的 DirSync 的 Web 应用程序代理服务器](media/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="97275-164">图 4 展示了如何添加 PROXY1 服务器。</span><span class="sxs-lookup"><span data-stu-id="97275-164">Figure 4 shows the addition of the PROXY1 server.</span></span>
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a><span data-ttu-id="97275-165">阶段 4：创建自签名证书并配置 ADFS1 和 PROXY1</span><span class="sxs-lookup"><span data-stu-id="97275-165">Phase 4: Create a self-signed certificate and configure ADFS1 and PROXY1</span></span>

<span data-ttu-id="97275-166">在此阶段，将为联合身份验证服务 FQDN 创建自签名数字证书，并将 ADFS1 和 PROXY1 配置为 AD FS 场。</span><span class="sxs-lookup"><span data-stu-id="97275-166">In this phase, you create a self-signed digital certificate for your federation service FQDN and configure ADFS1 and PROXY1 as an AD FS farm.</span></span>
  
<span data-ttu-id="97275-167">首先，通过 [Azure 门户](http://portal.azure.com)，使用 CORP\\User1 凭据连接 DC1 虚拟机，然后打开管理员级 Windows PowerShell 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="97275-167">First, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="97275-168">接下来，在 DC1 上的 Windows PowerShell 命令提示符处运行以下命令，创建 AD FS 服务帐户：</span><span class="sxs-lookup"><span data-stu-id="97275-168">Next, create AD FS service account with this command at the Windows PowerShell command prompt on DC1:</span></span>
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="97275-p106">请注意，此命令会提示你提供帐户密码。选择强密码，然后在安全位置记录此密码。此阶段和阶段 5 都要用到它。</span><span class="sxs-lookup"><span data-stu-id="97275-p106">Note that this command prompts you to supply the account password. Choose a strong password and record it in a secured location. You will need it for this phase and Phase 5.</span></span>
  
<span data-ttu-id="97275-p107">通过 [Azure 门户](http://portal.azure.com)，使用 CORP\\User1 凭据连接 ADFS1 虚拟机。在 ADFS1 上打开管理员级 Windows PowerShell 命令提示符，填写联合身份验证服务 FQDN，然后运行下面这些命令，从而创建自签名证书：</span><span class="sxs-lookup"><span data-stu-id="97275-p107">Use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the CORP\\User1 credentials. Open an administrator-level Windows PowerShell command prompt on ADFS1, fill in your federation service FQDN, and then run these commands to create a self-signed certificate:</span></span>
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

<span data-ttu-id="97275-174">接下来，按下面这些步骤操作，将新建的自签名证书保存为文件。</span><span class="sxs-lookup"><span data-stu-id="97275-174">Next, use these steps to save the new self-signed certificate as a file.</span></span>
  
1. <span data-ttu-id="97275-175">单击“开始”，键入“mmc.exe”，然后按 Enter 键。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-175">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="97275-176">依次单击“文件”>“添加/删除管理单元”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-176">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="97275-177">在“添加或删除管理单元”中，双击可用管理单元列表中的“证书”，然后依次单击“计算机帐户”和“下一步”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-177">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="97275-178">在“选择计算机”中，依次单击“完成”和“确定”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-178">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="97275-179">在树窗格中，依次打开“证书(本地计算机)”>“个人”>“证书”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-179">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="97275-180">右键单击包含联合身份验证服务 FQDN 的证书，然后依次单击“所有任务”和“导出”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-180">Right-click the certificate with your federation service FQDN, click **All tasks**, and then click **Export**.</span></span>
    
7. <span data-ttu-id="97275-181">在“欢迎”页上，单击“下一步”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="97275-181">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="97275-182">在“导出私钥”页上，依次单击“是”和“下一步”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-182">On the **Export Private Key** page, click **Yes**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="97275-183">在“导出文件格式”页上，依次单击“导出所有扩展属性”和“下一步”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-183">On the **Export File Format** page, click **Export all extended properties**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="97275-184">在“安全性”页上，单击“密码”，然后在“密码”和“确认密码”中键入密码。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-184">On the **Security** page, click **Password** and type a password in **Password** and **Confirm password.**</span></span>
    
11. <span data-ttu-id="97275-185">在“要导出的文件”页上，单击“浏览”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-185">On the **File to Export** page, click **Browse**.</span></span>
    
12. <span data-ttu-id="97275-186">浏览至“C:\\Certs”文件夹，在“文件名”中键入“SSL”，然后单击“保存”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-186">Browse to the **C:\\Certs** folder, type **SSL** in **File name**, and then click **Save.**</span></span>
    
13. <span data-ttu-id="97275-187">在“要导出的文件”页上，单击“下一步”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-187">On the **File to Export** page, click **Next**.</span></span>
    
14. <span data-ttu-id="97275-p108">在“正在完成证书导出向导”页上，单击“完成”。当出现提示时，单击“确定”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-p108">On the **Completing the Certificate Export Wizard** page, click **Finish**. When prompted, click **OK**.</span></span>
    
<span data-ttu-id="97275-190">接下来，在 ADFS1 上的 Windows PowerShell 命令提示符处运行以下命令，安装 AD FS 服务：</span><span class="sxs-lookup"><span data-stu-id="97275-190">Next, install the AD FS service with this command at the Windows PowerShell command prompt on ADFS1:</span></span>
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

<span data-ttu-id="97275-191">等待安装完成。</span><span class="sxs-lookup"><span data-stu-id="97275-191">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="97275-192">接下来，按下面这些步骤操作，配置 AD FS 服务：</span><span class="sxs-lookup"><span data-stu-id="97275-192">Next, configure the AD FS service with these steps:</span></span>
  
1. <span data-ttu-id="97275-193">依次单击“开始”和“服务器管理器”图标。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-193">Click **Start**, and then click the **Server Manager** icon.</span></span>
    
2. <span data-ttu-id="97275-194">在“服务器管理器”树窗格中，单击“AD FS”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-194">In the tree pane of Server Manager, click **AD FS**.</span></span>
    
3. <span data-ttu-id="97275-195">在顶部工具栏中，依次单击橙色警告符号和“在此服务器上配置联合身份验证服务”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-195">In the tool bar at the top, click the orange caution symbol, and then click **Configure the federation service on this server**.</span></span>
    
4. <span data-ttu-id="97275-196">在“Active Directory 联合身份验证服务配置向导”的“欢迎”页上，单击“下一步”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-196">On the **Welcome** page of the Active Directory Federation Services Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="97275-197">在“连接到 AD DS”页上，单击“下一步”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-197">On the **Connect to AD DS** page, click **Next**.</span></span>
    
6. <span data-ttu-id="97275-198">在“指定服务属性”页上：\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-198">On the **Specify Service Properties** page:</span></span>
    
  - <span data-ttu-id="97275-199">对于“SSL 证书”，依次单击向下箭头和包含联合身份验证服务 FQDN 名称的证书。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-199">For **SSL Certificate**, click the down arrow, and then click the certificate with the name of your federation service FQDN.</span></span>
    
  - <span data-ttu-id="97275-200">在“联合身份验证服务显示名称”中，键入虚构组织的名称。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-200">In **Federation Service Display Name**, type the name of your fictional organization.</span></span>
    
  - <span data-ttu-id="97275-201">单击“下一步”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-201">Click **Next**.</span></span>
    
7. <span data-ttu-id="97275-202">在“指定服务帐户”页上，单击“选择”来选择“帐户名称”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-202">On the **Specify Service Account** page, click **Select** for **Account name**.</span></span>
    
8. <span data-ttu-id="97275-203">在“选择用户或服务帐户”中，键入“ADFS-Service”，然后依次单击“检查名称”和“确定”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-203">In **Select User or Service Account**, type **ADFS-Service**, click **Check Names**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="97275-204">在“帐户密码”中，键入 ADFS-Service 帐户密码，然后单击“下一步”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-204">In **Account Password**, type the password for the ADFS-Service account, and then click **Next**.</span></span>
    
10. <span data-ttu-id="97275-205">在“指定配置数据库”页上，单击“下一步”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-205">On the **Specify Configuration Database** page, click **Next**.</span></span>
    
11. <span data-ttu-id="97275-206">在“查看选项”页上，单击“下一步”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-206">On the **Review Options** page, click **Next**.</span></span>
    
12. <span data-ttu-id="97275-207">在“先决条件检查”页上，单击“配置”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-207">On the **Pre-requisite Checks** page, click **Configure**.</span></span>
    
13. <span data-ttu-id="97275-208">在“结果”页上，单击“关闭”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-208">On the **Results** page, click **Close**.</span></span>
    
14. <span data-ttu-id="97275-209">依次单击“开始”、电源图标、“重启”和“继续”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-209">Click **Start**, click the power icon, click **Restart**, and then click **Continue**.</span></span>
    
<span data-ttu-id="97275-210">通过 CORP\\User1 帐户凭据从 [Azure 门户](http://portal.azure.com)连接到 PROXY1。</span><span class="sxs-lookup"><span data-stu-id="97275-210">From the [Azure portal](http://portal.azure.com), connect to PROXY1 with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="97275-211">接下来，按下面这些步骤操作，安装自签名证书并配置 PROXY1。</span><span class="sxs-lookup"><span data-stu-id="97275-211">Next, use these steps to install the self-signed certificate and configure PROXY1.</span></span>
  
1. <span data-ttu-id="97275-212">单击“开始”，键入“mmc.exe”，然后按 Enter 键。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-212">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="97275-213">依次单击“文件”>“添加/删除管理单元”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-213">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="97275-214">在“添加或删除管理单元”中，双击可用管理单元列表中的“证书”，然后依次单击“计算机帐户”和“下一步”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-214">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="97275-215">在“选择计算机”中，依次单击“完成”和“确定”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-215">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="97275-216">在树窗格中，依次打开“证书(本地计算机)”>“个人”>“证书”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-216">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="97275-217">右键单击“个人”，然后依次单击“所有任务”和“导入”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-217">Right-click **Personal**, click **All tasks**, and then click **Import**.</span></span>
    
7. <span data-ttu-id="97275-218">在“欢迎”页上，单击“下一步”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="97275-218">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="97275-219">在“要导入的文件”页上，键入“**\\\\adfs1\\certs\\ssl.pfx**”，然后单击“下一步”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-219">On the **File to Import** page, type **\\\\adfs1\\certs\\ssl.pfx**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="97275-220">在“私钥保护”页上的“密码”中键入证书密码，然后单击“下一步”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-220">On the **Private key protection** page, type the certificate password in **Password**, and then click **Next.**</span></span>
    
10. <span data-ttu-id="97275-221">在“证书存储”页上，单击“下一步”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-221">On the **Certificate store** page, click **Next.**</span></span>
    
11. <span data-ttu-id="97275-222">在“正在完成”页上，单击“完成”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-222">On the **Completing** page, click **Finish**.</span></span>
    
12. <span data-ttu-id="97275-223">在“证书存储”页上，单击“下一步”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-223">On the **Certificate Store** page, click **Next**.</span></span>
    
13. <span data-ttu-id="97275-224">当出现提示时，单击“确定”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-224">When prompted, click **OK**.</span></span>
    
14. <span data-ttu-id="97275-225">单击树窗格中“证书”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-225">Click **Certificates** in the tree pane.</span></span>
    
15. <span data-ttu-id="97275-226">右键单击证书，然后单击“复制”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-226">Right-click the certificate, and then click **Copy**.</span></span>
    
16. <span data-ttu-id="97275-227">在树窗格中，依次打开“受信任的根证书颁发机构”>“证书”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-227">In the tree pane, open **Trusted Root Certification Authorities > Certificates**.</span></span>
    
17. <span data-ttu-id="97275-228">将鼠标指针移到已安装证书列表下方，右键单击，然后单击“粘贴”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-228">Move your mouse pointer below the list of installed certificates, right-click, and then click **Paste**.</span></span>
    
<span data-ttu-id="97275-229">打开管理员级 PowerShell 命令提示符，然后运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="97275-229">Open an administrator-level PowerShell command prompt and run the following command:</span></span>
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

<span data-ttu-id="97275-230">等待安装完成。</span><span class="sxs-lookup"><span data-stu-id="97275-230">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="97275-231">按下面这些步骤操作，将 Web 应用程序代理服务配置为使用 ADFS1 作为其联合服务器：</span><span class="sxs-lookup"><span data-stu-id="97275-231">Use these steps to configure the web application proxy service to use ADFS1 as its federation server:</span></span>
  
1. <span data-ttu-id="97275-232">单击“开始”，再单击“服务器管理器”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-232">Click **Start**, and then click **Server Manager**.</span></span>
    
2. <span data-ttu-id="97275-233">在树窗格中，单击“远程访问”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-233">In the tree pane, click **Remote Access**.</span></span>
    
3. <span data-ttu-id="97275-234">在顶部工具栏中，依次单击橙色警告符号和“打开‘Web 应用程序代理向导’”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-234">In the tool bar at the top, click the orange caution symbol, and then click **Open the Web Application Proxy Wizard**.</span></span>
    
4. <span data-ttu-id="97275-235">在“Web 应用程序代理配置向导”的“欢迎”页上，单击“下一步”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-235">On the **Welcome** page of the Web Application Proxy Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="97275-236">在“联合服务器”页上：\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-236">On the **Federation Server** page:</span></span>
    
  - <span data-ttu-id="97275-237">在“联合身份验证服务名称”中，键入联合身份验证服务 FQDN。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-237">Type your federation service FQDN in **Federation service name**.</span></span>
    
  - <span data-ttu-id="97275-238">在“用户名”中，键入“CORP\\User1”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-238">Type **CORP\\User1** in **User name**.</span></span>
    
  - <span data-ttu-id="97275-239">在“密码”中，键入 User1 帐户密码。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-239">Type the password for the User1 account in **Password**.</span></span>
    
  - <span data-ttu-id="97275-240">单击“下一步”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-240">Click **Next**.</span></span>
    
6. <span data-ttu-id="97275-241">在“AD FS 代理证书”页上，依次单击向下箭头、包含联合身份验证服务 FQDN 的证书和“下一步”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-241">On the **AD FS Proxy Certificate** page, click the down arrow, click the certificate with your federation service FQDN, and then click **Next**.</span></span>
    
7. <span data-ttu-id="97275-242">在“确认”页上，单击“配置”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-242">On the **Confirmation** page, click **Configure**.</span></span>
    
8. <span data-ttu-id="97275-243">在“结果”页上，单击“关闭”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-243">On the **Results** page, click **Close**.</span></span>
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a><span data-ttu-id="97275-244">阶段 5：为 Office 365 配置联合身份</span><span class="sxs-lookup"><span data-stu-id="97275-244">Phase 5: Configure Office 365 for federated identity</span></span>

<span data-ttu-id="97275-245">通过 [Azure 门户](http://portal.azure.com)，使用 CORP\\User1 帐户凭据连接 APP1 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="97275-245">Use the [Azure portal](http://portal.azure.com) to connect to the APP1 virtual machine with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="97275-246">按下面这些步骤操作，为 Azure AD Connect 和 Office 365 订阅配置联合身份验证：</span><span class="sxs-lookup"><span data-stu-id="97275-246">Use these steps to configure Azure AD Connect and your Office 365 subscription for federated authentication:</span></span>
  
1. <span data-ttu-id="97275-247">在桌面上，双击“Azure AD Connect”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="97275-247">From the desktop, double-click **Azure AD Connect**.</span></span>
    
2. <span data-ttu-id="97275-248">在“欢迎使用 Azure AD Connect”页上，单击“配置”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-248">On the **Welcome to Azure AD Connect** page, click **Configure**.</span></span>
    
3. <span data-ttu-id="97275-249">在“其他任务”页上，依次单击“更改用户登录”和“下一步”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-249">On the **Additional tasks** page, click **Change user sign-in**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="97275-250">在“连接到 Azure AD”页上，键入 Office 365 全局管理员帐户名称和密码，然后单击“下一步”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-250">On the **Connect to Azure AD** page, type your Office 365 global administrator account name and password, and then click **Next**.</span></span>
    
5. <span data-ttu-id="97275-251">在“用户登录”页上，依次单击“使用 AD FS 进行联合身份验证”和“下一步”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-251">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="97275-252">在“AD FS 场”页上，单击“使用现有 AD FS 场”，在“服务器名称”中键入“ADFS1”，然后单击“下一步”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-252">On the **AD FS farm** page, click **Use an existing AD FS farm**, type **ADFS1** in **Server Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="97275-253">当系统提示输入服务器凭据时，输入 CORP\\User1 帐户凭据，然后单击“确定”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-253">When prompted for server credentials, enter the credentials of the CORP\\User1 account, and then click **OK**.</span></span>
    
8. <span data-ttu-id="97275-254">在“域管理员”凭据页上，在“用户名”中键入“CORP\\User1”，在“密码”中键入帐户密码，然后单击“下一步”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-254">On the **Domain Administrator** credentials page, type **CORP\\User1** in **Username** and the account password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="97275-255">在“AD FS 服务帐户”页上，在“域用户名”中键入“CORP\\ADFS-Service”，在“域用户密码”中键入帐户密码，然后单击“下一步”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-255">On the **AD FS service account** page, type **CORP\\ADFS-Service** in **Domain Username** and the account password in **Domain User Password**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="97275-256">在“Azure AD 域”页上的“域”中，选择之前在阶段 1 创建并添加到 Office 365订阅的域名，然后单击“下一步”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-256">On the **Azure AD Domain** page, in **Domain**, select the name of the domain you previously created and added to your Office 365 subscription in Phase 1, and then click **Next**.</span></span>
    
11. <span data-ttu-id="97275-257">在“准备配置”页上，单击“配置”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-257">On the **Ready to configure** page, click **Configure**.</span></span>
    
12. <span data-ttu-id="97275-258">在“安装完成”页上，单击“验证”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-258">On the **Installation complete** page, click **Verify**.</span></span>
    
    <span data-ttu-id="97275-259">应该可以看到指明 Intranet 和 Internet 配置均已验证的消息。</span><span class="sxs-lookup"><span data-stu-id="97275-259">You should see messages indicating that both the intranet and Internet configuration was verified.</span></span>
    
13. <span data-ttu-id="97275-260">在“安装完成”页上，单击“退出”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-260">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="97275-261">若要证明联合身份验证能够正常运行，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="97275-261">To demonstrate that federated authentication is working:</span></span>
  
1. <span data-ttu-id="97275-262">在本地计算机上打开浏览器的新专用实例，然后转到 [https://admin.microsoft.com](https://admin.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="97275-262">Open a new private instance of your browser on your local computer and go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
2. <span data-ttu-id="97275-263">对于登录凭据，请键入 **user1@**\<在阶段 1 创建的域>。</span><span class="sxs-lookup"><span data-stu-id="97275-263">For the sign-in credentials, type **user1@**\<the domain created in Phase 1>.</span></span> 
    
    <span data-ttu-id="97275-p109">例如，如果你的测试域是 **testlab.contoso.com**，请键入 **user1@testlab.contoso.com**。按 TAB 或允许 Office 365 自动重定向。</span><span class="sxs-lookup"><span data-stu-id="97275-p109">For example, if your test domain is **testlab.contoso.com**, you would type **user1@testlab.contoso.com**. Press TAB or allow Office 365 to automatically redirect you.</span></span>
    
    <span data-ttu-id="97275-p110">现在应该可以看到“**你所用连接不是专用连接**”页。之所以会看到此页是因为你在 ADFS1 上安装了台式计算机无法验证的自签名证书。在联合身份验证的生产部署中，将使用受信任的证书颁发机构颁发的证书，你的用户将不会看到此页。</span><span class="sxs-lookup"><span data-stu-id="97275-p110">You should now see a **Your connection is not private** page. You are seeing this because you installed a self-signed certificate on ADFS1 that your desktop computer cannot validate. In a production deployment of federated authentication, you would use a certificate from a trusted certification authority and your users would not see this page.</span></span>
    
3. <span data-ttu-id="97275-269">在“你所用连接不是专用连接”页上，依次单击“高级”和“继续处理 \<联合身份验证服务 FQDN>”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-269">On the **Your connection is not private** page, click **Advanced**, and then click **Proceed to \<your federation service FQDN>**.</span></span> 
    
4. <span data-ttu-id="97275-270">在包含虚构组织名称的页上，使用以下凭据登录：</span><span class="sxs-lookup"><span data-stu-id="97275-270">On the page with the name of your fictional organization, sign in with the following:</span></span>
    
  - <span data-ttu-id="97275-271">该名称的 **CORP\\User1**</span><span class="sxs-lookup"><span data-stu-id="97275-271">**CORP\\User1** for the name</span></span>
    
  - <span data-ttu-id="97275-272">User1 帐户密码</span><span class="sxs-lookup"><span data-stu-id="97275-272">The password for the User1 account</span></span>
    
    <span data-ttu-id="97275-273">应该会看到“Microsoft Office 主页”页面。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="97275-273">You should see the **Microsoft Office Home** page.</span></span>
    
<span data-ttu-id="97275-p111">此过程证明了 Office 365 试用订阅与 DC1 上托管的 AD DS corp.contoso.com 域进行了联合。下面介绍基本的身份验证过程：</span><span class="sxs-lookup"><span data-stu-id="97275-p111">This procedure demonstrates that your Office 365 trial subscription is federated with the AD DS corp.contoso.com domain hosted on DC1. Here are the basics of the authentication process:</span></span>
  
1. <span data-ttu-id="97275-276">在登录帐户名称中使用在阶段 1 创建的联盟域后，Office 365 将浏览器重定向到联合身份验证服务 FQDN 和 PROXY1。</span><span class="sxs-lookup"><span data-stu-id="97275-276">When you use the federated domain that you created in Phase 1 within the sign-in account name, Office 365 redirects your browser to your federation service FQDN and PROXY1.</span></span>
    
2. <span data-ttu-id="97275-277">PROXY1 向本地计算机发送虚构的公司登录页。</span><span class="sxs-lookup"><span data-stu-id="97275-277">PROXY1 sends your local computer the fictional company sign-in page.</span></span>
    
3. <span data-ttu-id="97275-278">PROXY1 会将你发送给它的 CORP\\User1 和密码转发给 ADFS1。</span><span class="sxs-lookup"><span data-stu-id="97275-278">When you send CORP\\User1 and the password to PROXY1, it forwards them to ADFS1.</span></span>
    
4. <span data-ttu-id="97275-279">ADFS1 使用 DC1 验证 CORP\\User1 和密码，然后向本地计算机发送安全令牌。</span><span class="sxs-lookup"><span data-stu-id="97275-279">ADFS1 validates CORP\\User1 and the password with DC1 and sends your local computer a security token.</span></span>
    
5. <span data-ttu-id="97275-280">本地计算机向 Office 365 发送安全令牌。</span><span class="sxs-lookup"><span data-stu-id="97275-280">Your local computer sends the security token to Office 365.</span></span>
    
6. <span data-ttu-id="97275-281">Office 365 验证安全令牌是否由 ADFS1 创建，通过验证后允许访问。</span><span class="sxs-lookup"><span data-stu-id="97275-281">Office 365 validates that the security token was created by ADFS1 and allows access.</span></span>
    
<span data-ttu-id="97275-p112">现在，Office 365 试用订阅已配置了联合身份验证。可以将此开发/测试环境用于高级身份验证方案。</span><span class="sxs-lookup"><span data-stu-id="97275-p112">Your Office 365 trial subscription is now configured with federated authentication. You can use this dev/test environment for advanced authentication scenarios.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="97275-284">后续步骤</span><span class="sxs-lookup"><span data-stu-id="97275-284">Next Step</span></span>

<span data-ttu-id="97275-285">在 Azure 中准备好部署 Office 365 的生产就绪、高可用性联合身份验证时，请参阅[Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="97275-285">When you are ready to deploy production-ready, high availability federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="97275-286">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97275-286">See Also</span></span>

[<span data-ttu-id="97275-287">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="97275-287">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="97275-288">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="97275-288">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="97275-289">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="97275-289">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="97275-290">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="97275-290">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="97275-291">在 Azure 中部署 Office 365 的高可用性联合身份验证</span><span class="sxs-lookup"><span data-stu-id="97275-291">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


