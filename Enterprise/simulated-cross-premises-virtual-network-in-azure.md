---
title: Azure 中的模拟跨界虚拟网络
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: 摘要：在 Microsoft Azure 中创建模拟跨界虚拟网络作为开发/测试环境。
ms.openlocfilehash: 9ef0424bad831294066e4ff4b5f7d602babc0a48
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948593"
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a><span data-ttu-id="12774-103">Azure 中的模拟跨界虚拟网络</span><span class="sxs-lookup"><span data-stu-id="12774-103">Simulated cross-premises virtual network in Azure</span></span>

 <span data-ttu-id="12774-104">**摘要：** 在 Microsoft Azure 中创建模拟跨界虚拟网络作为开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="12774-104">**Summary:** Create a simulated cross-premises virtual network in Microsoft Azure as a dev/test environment.</span></span>
  
<span data-ttu-id="12774-p101">本文逐步介绍了如何使用两个 Azure 虚拟网络来创建 Microsoft Azure 模拟混合云环境。下面是生成的配置。</span><span class="sxs-lookup"><span data-stu-id="12774-p101">This article steps you through creating a simulated hybrid cloud environment with Microsoft Azure using two Azure virtual networks. Here is the resulting configuration.</span></span> 
  
![第 3 阶段的模拟跨界虚拟网络开发/测试环境，XPrem VNet 中有 DC2 虚拟机](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
<span data-ttu-id="12774-108">此配置模拟 Azure IaaS 混合云生产环境，具体包括：</span><span class="sxs-lookup"><span data-stu-id="12774-108">This simulates an Azure IaaS hybrid cloud production environment and consists of:</span></span>
  
- <span data-ttu-id="12774-109">Azure 虚拟网络中托管的模拟简化本地网络（TestLab 虚拟网络）。</span><span class="sxs-lookup"><span data-stu-id="12774-109">A simulated and simplified on-premises network hosted in an Azure virtual network (the TestLab virtual network).</span></span>
    
- <span data-ttu-id="12774-110">Azure 中托管的模拟跨界虚拟网络 (XPrem)。</span><span class="sxs-lookup"><span data-stu-id="12774-110">A simulated cross-premises virtual network hosted in Azure (XPrem).</span></span>
    
- <span data-ttu-id="12774-111">两个虚拟网络之间的 VNet 对等关系。</span><span class="sxs-lookup"><span data-stu-id="12774-111">A VNet peering relationship between the two virtual networks.</span></span>
    
- <span data-ttu-id="12774-112">XPrem 虚拟网络中辅助域控制器。</span><span class="sxs-lookup"><span data-stu-id="12774-112">A secondary domain controller in the XPrem virtual network.</span></span>
    
<span data-ttu-id="12774-113">这是你执行以下操作的常见基础入手配置：</span><span class="sxs-lookup"><span data-stu-id="12774-113">This provides a basis and common starting point from which you can:</span></span> 
  
- <span data-ttu-id="12774-114">在模拟 Azure IaaS 混合云环境中开发和测试应用程序。</span><span class="sxs-lookup"><span data-stu-id="12774-114">Develop and test applications in a simulated Azure IaaS hybrid cloud environment.</span></span>
    
- <span data-ttu-id="12774-115">创建计算机的测试配置（一些位于 TestLab 虚拟网络中，一些位于 XPrem 虚拟网络中），以模拟基于混合云的 IT 工作负荷。</span><span class="sxs-lookup"><span data-stu-id="12774-115">Create test configurations of computers, some within the TestLab virtual network and some within the XPrem virtual network, to simulate hybrid cloud-based IT workloads.</span></span>
    
<span data-ttu-id="12774-116">设置此开发/测试环境包含三个主要阶段：</span><span class="sxs-lookup"><span data-stu-id="12774-116">There are three major phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="12774-117">配置 TestLab 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="12774-117">Configure the TestLab virtual network.</span></span>
    
2. <span data-ttu-id="12774-118">创建跨界虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="12774-118">Create the cross-premises virtual network.</span></span>
    
3. <span data-ttu-id="12774-119">配置 DC2。</span><span class="sxs-lookup"><span data-stu-id="12774-119">Configure DC2.</span></span>
    
> [!NOTE]
> <span data-ttu-id="12774-120">此配置需要付费的 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="12774-120">This configuration requires a paid Azure subscription.</span></span> 
  
![Microsoft 云中的测试实验室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="12774-122">单击[此处](http://aka.ms/catlgstack)可直观映射到 One Microsoft 云测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="12774-122">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a><span data-ttu-id="12774-123">第 1 阶段：配置 TestLab 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="12774-123">Phase 1: Configure the TestLab virtual network</span></span>

<span data-ttu-id="12774-124">请按[基础配置开发/测试环境](base-configuration-dev-test-environment.md)中的说明操作，在名为 TestLab 的 Azure 虚拟网络中配置 DC1、APP1 和 CLIENT1 计算机。</span><span class="sxs-lookup"><span data-stu-id="12774-124">Use the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md) to configure the DC1, APP1, and CLIENT1 computers in the Azure virtual network named TestLab.</span></span>
  
<span data-ttu-id="12774-125">这是你的当前配置。</span><span class="sxs-lookup"><span data-stu-id="12774-125">This is your current configuration.</span></span> 
  
![CLIENT1 虚拟机的 Azure 中的基础配置的阶段 4](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a><span data-ttu-id="12774-127">第 2 阶段：创建 XPrem 虚拟网络</span><span class="sxs-lookup"><span data-stu-id="12774-127">Phase 2: Create the XPrem virtual network</span></span>

<span data-ttu-id="12774-128">在此阶段，你需要创建和配置新的 XPrem 虚拟网络，然后通过 VNet 对等关系将其连接到 TestLab 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="12774-128">In this phase, you create and configure the new XPrem virtual network and then connect it to the TestLab virtual network with VNet peering.</span></span>
  
<span data-ttu-id="12774-129">首先，在本地计算机上启动 Azure PowerShell 提示符。</span><span class="sxs-lookup"><span data-stu-id="12774-129">First, start an Azure PowerShell prompt on your local computer.</span></span>
  
> [!NOTE]
> <span data-ttu-id="12774-p102">下面的命令集使用最新版 Azure PowerShell。请参阅 [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/zh-CN/powershell/azureps-cmdlets-docs/)（Azure PowerShell cmdlet 使用入门）。</span><span class="sxs-lookup"><span data-stu-id="12774-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/zh-CN/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="12774-132">使用此命令登录 Azure 帐户。</span><span class="sxs-lookup"><span data-stu-id="12774-132">Sign in to your Azure account with this command.</span></span>
  
```
Connect-AzAccount
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0) to get a text file that has all of the PowerShell commands in this article.
-->
  
<span data-ttu-id="12774-133">使用此命令获取订阅名称。</span><span class="sxs-lookup"><span data-stu-id="12774-133">Get your subscription name using this command.</span></span>
  
```
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="12774-p103">设置 Azure 订阅。使用正确的名称替换引号内的所有内容（包括 \< 和 > 字符）。</span><span class="sxs-lookup"><span data-stu-id="12774-p103">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct names.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="12774-136">接下来，创建 XPrem 虚拟网络，然后使用这些命令通过网络安全组保护此虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="12774-136">Next, create the XPrem virtual network and protect it with a network security group with these commands.</span></span>
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$Testnet=New-AzVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
```

<span data-ttu-id="12774-137">接下来，使用下面这些命令在 TestLab 和 XPrem VNet 之间创建 VNet 对等关系。</span><span class="sxs-lookup"><span data-stu-id="12774-137">Next, you create the VNet peering relationship between the TestLab and XPrem VNets with these commands.</span></span>
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

<span data-ttu-id="12774-138">这是你的当前配置。</span><span class="sxs-lookup"><span data-stu-id="12774-138">This is your current configuration.</span></span> 
  
![第 2 阶段的模拟跨界虚拟网络开发/测试环境，包含 XPrem VNet 和 VNet 对等关系](media/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a><span data-ttu-id="12774-140">第 3 阶段：配置 DC2</span><span class="sxs-lookup"><span data-stu-id="12774-140">Phase 3: Configure DC2</span></span>

<span data-ttu-id="12774-141">在此阶段，你需要在 XPrem 虚拟网络中创建 DC2 虚拟机，然后将其配置为副本域控制器。</span><span class="sxs-lookup"><span data-stu-id="12774-141">In this phase, you create the DC2 virtual machine in the XPrem virtual network and then configure it as a replica domain controller.</span></span>
  
<span data-ttu-id="12774-p104">首先，创建 DC2 虚拟机。在本地计算机上的 Azure PowerShell 命令提示符处，运行下面这些命令。</span><span class="sxs-lookup"><span data-stu-id="12774-p104">First, create a virtual machine for DC2. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<your resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzVMConfig -VMName DC2 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="12774-144">接下来，在 [Azure 门户](https://portal.azure.com)中使用本地管理员帐户名称和密码连接到新的 DC2 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="12774-144">Next, connect to the new DC2 virtual machine from the [Azure portal](https://portal.azure.com) using its local administrator account name and password.</span></span>
  
<span data-ttu-id="12774-p105">接下来，将 Windows 防火墙规则配置为允许通信以进行基本的连接测试。在 DC 2 上的管理员级别 Windows PowerShell 命令提示符处，运行下面这些命令。</span><span class="sxs-lookup"><span data-stu-id="12774-p105">Next, configure a Windows Firewall rule to allow traffic for basic connectivity testing. From an administrator-level Windows PowerShell command prompt on DC2, run these commands.</span></span> 
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

<span data-ttu-id="12774-p106">ping 命令应获得从 IP 地址 10.0.0.4 发出的四个成功响应。这是跨 VNet 对等关系的通信测试。</span><span class="sxs-lookup"><span data-stu-id="12774-p106">The ping command should result in four successful replies from IP address 10.0.0.4. This is a test of traffic across the VNet peering relationship.</span></span> 
  
<span data-ttu-id="12774-149">接下来，在 DC2 上的 Windows PowerShell 命令提示符处，使用下面的命令将额外的数据磁盘添加为新卷，驱动器号为 F:。</span><span class="sxs-lookup"><span data-stu-id="12774-149">Next, add the extra data disk as a new volume with the drive letter F: with this command from the Windows PowerShell command prompt on DC2.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="12774-p107">接下来，将 DC2 配置为 corp.contoso.com 域的副本域控制器。在 DC2 上的 Windows PowerShell 命令提示符处，运行下面这些命令。</span><span class="sxs-lookup"><span data-stu-id="12774-p107">Next, configure DC2 as a replica domain controller for the corp.contoso.com domain. Run these commands from the Windows PowerShell command prompt on DC2.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

<span data-ttu-id="12774-152">请注意，系统会提示你输入 CORP\\User1 密码和目录服务还原模式 (DSRM) 密码，并重启 DC2。</span><span class="sxs-lookup"><span data-stu-id="12774-152">Note that you are prompted to supply both the CORP\\User1 password and a Directory Services Restore Mode (DSRM) password, and to restart DC2.</span></span> 
  
<span data-ttu-id="12774-p108">至此，XPrem 虚拟网络已拥有自己的 DNS 服务器 (DC2)。你必须将 XPrem 虚拟网络配置为使用此 DNS 服务器。在本地计算机上的 Azure PowerShell 命令提示符处，运行下面这些命令。</span><span class="sxs-lookup"><span data-stu-id="12774-p108">Now that the XPrem virtual network has its own DNS server (DC2), you must configure the XPrem virtual network to use this DNS server. Run these commands from the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

<span data-ttu-id="12774-p109">在本地计算机上的 Azure 门户中，使用 CORP\\User1 凭据连接到 DC1。要配置 CORP 域以便计算机和用户可以使用其本地域控制器进行身份验证，请在 DC1 上的管理员级别 Windows PowerShell 命令提示符处，运行下面这些命令。</span><span class="sxs-lookup"><span data-stu-id="12774-p109">From the Azure portal on your local computer, connect to DC1 with the CORP\\User1 credentials. To configure the CORP domain so that computers and users use their local domain controller for authentication, run these commands from an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

<span data-ttu-id="12774-157">这是你的当前配置。</span><span class="sxs-lookup"><span data-stu-id="12774-157">This is your current configuration.</span></span> 
  
![第 3 阶段的模拟跨界虚拟网络开发/测试环境，XPrem VNet 中有 DC2 虚拟机](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
<span data-ttu-id="12774-159">此时，你的模拟 Azure 混合云环境就可供测试了。</span><span class="sxs-lookup"><span data-stu-id="12774-159">Your simulated Azure hybrid cloud environment is now ready for testing.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="12774-160">后续步骤</span><span class="sxs-lookup"><span data-stu-id="12774-160">Next step</span></span>

<span data-ttu-id="12774-161">使用此开发/测试环境模拟 [Azure 中托管的 SharePoint Server 2016 Intranet 场](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="12774-161">Use this dev/test environment to simulate a [SharePoint Server 2016 intranet farm hosted in Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="12774-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12774-162">See Also</span></span>

[<span data-ttu-id="12774-163">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="12774-163">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="12774-164">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="12774-164">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="12774-165">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="12774-165">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="12774-166">用于 Office 365 开发/测试环境的云应用安全</span><span class="sxs-lookup"><span data-stu-id="12774-166">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="12774-167">Office 365 开发/测试环境中的高级威胁防护</span><span class="sxs-lookup"><span data-stu-id="12774-167">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="12774-168">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="12774-168">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


