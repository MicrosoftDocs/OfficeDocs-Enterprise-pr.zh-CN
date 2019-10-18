---
title: 基础配置开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
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
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 摘要：在 Microsoft Azure 中创建一个简化的内部网作为开发/测试环境。
ms.openlocfilehash: f6a9f2f2742b56ffb5f8a7521a14bfe48d3adc22
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162435"
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="2ecca-103">基础配置开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="2ecca-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="2ecca-104">\*\*\*\* 摘要：在 Microsoft Azure 中创建一个简化的 Intranet 作为开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="2ecca-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="2ecca-105">本文提供了在 Azure 中创建以下基础配置开发/测试环境的说明：</span><span class="sxs-lookup"><span data-stu-id="2ecca-105">This article provides you with instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
![Azure 中的基础配置](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="2ecca-107">**图 1：基础配置开发/测试环境**</span><span class="sxs-lookup"><span data-stu-id="2ecca-107">**Figure 1: The Base Configuration dev/test environment**</span></span>

<span data-ttu-id="2ecca-p101">图 1 中的基础配置开发/测试环境，由一个仅限云的 Azure 虚拟网络（名为 TestLab）中的 Corpnet 子网组成，可模拟连接到 Internet 的简化专用内部网。它包含三个运行 Windows Server 2016 的 Azure 虚拟机：</span><span class="sxs-lookup"><span data-stu-id="2ecca-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It has three Azure virtual machines running Windows Server 2016:</span></span>
  
- <span data-ttu-id="2ecca-110">DC1 被配置为内部网域控制器和域名系统 (DNS) 服务器</span><span class="sxs-lookup"><span data-stu-id="2ecca-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="2ecca-111">APP1 被配置为常规应用程序和 Web 服务器</span><span class="sxs-lookup"><span data-stu-id="2ecca-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="2ecca-112">CLIENT1 用作内部网客户端</span><span class="sxs-lookup"><span data-stu-id="2ecca-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="2ecca-113">这种配置使得 DC1、APP1、CLIENT1 以及其他企业网络子网计算机可以：</span><span class="sxs-lookup"><span data-stu-id="2ecca-113">This configuration lets DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="2ecca-114">连接到 Internet 来安装更新，访问实时 Internet 资源，并参与公有云技术，如 Microsoft Office 365 和其他 Azure 服务。</span><span class="sxs-lookup"><span data-stu-id="2ecca-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="2ecca-115">使用连接至 Internet 或组织网络的计算机中的远程桌面连接进行远程管理。</span><span class="sxs-lookup"><span data-stu-id="2ecca-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="2ecca-116">可以使用生成的测试环境：</span><span class="sxs-lookup"><span data-stu-id="2ecca-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="2ecca-117">用于应用程序开发和测试。</span><span class="sxs-lookup"><span data-stu-id="2ecca-117">For application development and testing.</span></span>
    
- <span data-ttu-id="2ecca-118">作为自己设计的扩展测试环境的初始配置，包括附加的虚拟机、Azure 服务或其他 Microsoft 云产品/服务，如 Office 365 和企业版移动性 + 安全性 (EMS)。</span><span class="sxs-lookup"><span data-stu-id="2ecca-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Mobility + Security (EMS).</span></span>
    
<span data-ttu-id="2ecca-119">创建此环境有两种方法：</span><span class="sxs-lookup"><span data-stu-id="2ecca-119">There are two methods to creating this environment:</span></span>

1. <span data-ttu-id="2ecca-120">Azure 资源管理器模板</span><span class="sxs-lookup"><span data-stu-id="2ecca-120">An Azure Resource Manager template</span></span>
2. <span data-ttu-id="2ecca-121">Azure Powershell</span><span class="sxs-lookup"><span data-stu-id="2ecca-121">Azure Powershell</span></span>

## <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a><span data-ttu-id="2ecca-122">方法 1：使用 Azure 资源管理器模板构建模拟 Intranet</span><span class="sxs-lookup"><span data-stu-id="2ecca-122">Method 1: Build your simulated intranet with an Azure Resource Manager template</span></span>

<span data-ttu-id="2ecca-p102">在此方法中，可以使用 Azure 资源管理器 (ARM) 模板来构建模拟 Intranet。ARM 模板包含有关创建和配置 Azure 网络基础结构和虚拟机的所有说明。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p102">In this method, you use an Azure Resource Manager (ARM) template to build out the simulated intranet. ARM templates contain all of the instructions to create and configure the Azure networking infrastructure and the virtual machines.</span></span>

<span data-ttu-id="2ecca-125">部署该模板之前，请通读“模板自述文件”[](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm)页面并准备好以下信息：</span><span class="sxs-lookup"><span data-stu-id="2ecca-125">Prior to deploying the template, read through the [template README page](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) and have the following information ready:</span></span>

- <span data-ttu-id="2ecca-p103">Azure 订阅名称。你需要在“自定义部署”\*\*\*\* 页的“订阅”\*\*\*\* 字段输入此标签。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p103">The Azure subscription name. You’ll need to enter this label in the **Subscription** field of the **Custom deployment** page.</span></span>
- <span data-ttu-id="2ecca-p104">Azure 资源组名称。你需要在“自定义部署”\*\*\*\* 页的“资源组”\*\*\*\* 字段输入此标签。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p104">The Azure resource group name. You’ll need to enter this label in the **Resource group** field of the **Custom deployment** page.</span></span>
- <span data-ttu-id="2ecca-p105">虚拟机公共 IP 地址 URL 的 DNS 标签前缀。你将需要在“**自定义部署**”页面的“**Dns 标签前缀**”字段中输入此标签。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p105">A DNS label prefix for the URLs of the public IP addresses of your virtual machines. You’ll need to enter this label in the **Dns Label Prefix** field of the **Custom deployment** page.</span></span>

<span data-ttu-id="2ecca-132">通读说明后，在“[模板自述文件](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm)”页面上单击“**部署到 Azure**”，以开始进行部署。</span><span class="sxs-lookup"><span data-stu-id="2ecca-132">After reading through the instructions, click **Deploy to Azure** on the [template README page](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) to get started.</span></span>

>[!Note]
><span data-ttu-id="2ecca-133">通过 ARM 模板构建的模拟 Intranet 需要付费 Azure 订阅。</span><span class="sxs-lookup"><span data-stu-id="2ecca-133">The simulated intranet built by the ARM template requires a paid Azure subscription.</span></span>
>

<span data-ttu-id="2ecca-134">模板完成后，会生成以下配置。</span><span class="sxs-lookup"><span data-stu-id="2ecca-134">Here is your configuration after the template is complete.</span></span>

![Azure 中的基础配置](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


## <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a><span data-ttu-id="2ecca-136">方法 2：使用 Azure PowerShell 构建模拟 Intranet</span><span class="sxs-lookup"><span data-stu-id="2ecca-136">Method 2: Build your simulated intranet with Azure PowerShell</span></span>

<span data-ttu-id="2ecca-137">在此方法中，你可以使用 Windows PowerShell 和 Azure PowerShell 模块来构建网络基础结构、虚拟机及其配置。</span><span class="sxs-lookup"><span data-stu-id="2ecca-137">In this method, you use Windows PowerShell and the Azure PowerShell module to build out the networking infrastructure, the virtual machines, and their configuration.</span></span>

<span data-ttu-id="2ecca-p106">如果想要体验通过 PowerShell 一次使用一个命令块创建 Azure 基础结构元素的过程，则可以使用此方法。然后可以自定义 PowerShell 命令块，以便自行在 Azure 中部署其他虚拟机。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p106">Use this method if you want to get experience creating elements of Azure infrastructure one command block at a time with PowerShell. You can then customize the PowerShell command blocks for your own deployment of other virtual machines in Azure.</span></span>

<span data-ttu-id="2ecca-140">使用 Azure PowerShell 设置基础配置测试环境有如下四个步骤：</span><span class="sxs-lookup"><span data-stu-id="2ecca-140">There are four steps to setting up the Base Configuration test environment using Azure PowerShell:</span></span>
  
1. <span data-ttu-id="2ecca-141">创建虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="2ecca-141">Create the virtual network.</span></span>
    
2. <span data-ttu-id="2ecca-142">配置 DC1。</span><span class="sxs-lookup"><span data-stu-id="2ecca-142">Configure DC1.</span></span>
    
3. <span data-ttu-id="2ecca-143">配置 APP1。</span><span class="sxs-lookup"><span data-stu-id="2ecca-143">Configure APP1.</span></span>
    
4. <span data-ttu-id="2ecca-144">配置 CLIENT1。</span><span class="sxs-lookup"><span data-stu-id="2ecca-144">Configure CLIENT1.</span></span>
    
<span data-ttu-id="2ecca-p107">如果还没有 Azure 订阅，可以在[试用 Azure](https://azure.microsoft.com/pricing/free-trial/) 上注册免费试用版。如果你有 MSDN 或 Visual Studio 订阅，请参阅 [Visual Studio 订阅者的每月 Azure 信用额度](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p107">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="2ecca-p108">Azure 中的虚拟机在运行时会持续产生费用。该项费用是针对运行免费试用版、MSDN 订阅或付费订阅收取的。关于运行 Azure 虚拟机成本的详细信息，请参阅[虚拟机定价详细信息](https://azure.microsoft.com/pricing/details/virtual-machines/)和 [Azure 定价计算器](https://azure.microsoft.com/pricing/calculator/)。为了节约成本，请参阅[最大限度降低 Azure 中测试环境虚拟机的成本](base-configuration-dev-test-environment.md#mincost)。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p108">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Microsoft 云中的测试实验室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="2ecca-152">单击[此处](http://aka.ms/catlgstack)可直观映射到 Office 365 测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="2ecca-152">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
### <a name="step-1-create-the-virtual-network"></a><span data-ttu-id="2ecca-153">步骤 1：创建虚拟网络</span><span class="sxs-lookup"><span data-stu-id="2ecca-153">Step 1: Create the virtual network</span></span>

<span data-ttu-id="2ecca-154">在此步骤中，将在 Azure 中创建 TestLab 虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="2ecca-154">In this step, you the TestLab virtual network in Azure.</span></span>

<span data-ttu-id="2ecca-155">首先，从 Azure PowerShell 提示符开始。</span><span class="sxs-lookup"><span data-stu-id="2ecca-155">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2ecca-p109">下面的命令集使用最新版 Azure PowerShell。请参阅 [Azure PowerShell cmdlet 使用入门](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="2ecca-158">使用以下命令登录 Azure 帐户。</span><span class="sxs-lookup"><span data-stu-id="2ecca-158">Sign in to your Azure account with the following command.</span></span>
  
```
Connect-AzAccount
```

> [!TIP]
> <span data-ttu-id="2ecca-159">单击[此处](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d)可获取包含本文中所有 PowerShell 命令的文本文件。</span><span class="sxs-lookup"><span data-stu-id="2ecca-159">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that has all the PowerShell commands in this article.</span></span>

<span data-ttu-id="2ecca-160">使用以下命令获取订阅名称。</span><span class="sxs-lookup"><span data-stu-id="2ecca-160">Get your subscription name using the following command.</span></span>
  
```
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="2ecca-p110">设置 Azure 订阅。使用正确的名称替换引号内的所有内容（包括 < 和 > 字符）。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p110">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="2ecca-p111">接下来，为基础配置测试实验室创建一个新的资源组。要确定一个唯一的资源组名称，请使用此命令列出现有的资源组。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p111">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="2ecca-p112">使用这些命令创建新的资源组。使用正确的名称替换引号内的所有内容（包括 < 和 > 字符）。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p112">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="2ecca-167">接下来，创建 TestLab 虚拟网络，它将托管基础配置的企业网络子网并通过网络安全组对其进行保护。</span><span class="sxs-lookup"><span data-stu-id="2ecca-167">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

<span data-ttu-id="2ecca-168">当前配置如下。</span><span class="sxs-lookup"><span data-stu-id="2ecca-168">This is your current configuration.</span></span>
  
![通过虚拟网络和子网在 Azure 中进行基础配置的第 1 步](media/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
### <a name="step-2-configure-dc1"></a><span data-ttu-id="2ecca-170">步骤 2：配置 DC1</span><span class="sxs-lookup"><span data-stu-id="2ecca-170">Step 2: Configure DC1</span></span>

<span data-ttu-id="2ecca-171">在此步骤中，我们需要创建 DC1 虚拟机，并将它配置为 corp.contoso.com Active Directory 域服务 (AD DS) 域的域控制器，以及 TestLab 虚拟网络中虚拟机的 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="2ecca-171">In this step, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Active Directory Domain Services (AD DS) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>

> [!NOTE]
> <span data-ttu-id="2ecca-p113">执行以下命令块前，请确保选择的 Azure 区域（位置）支持 Azure 虚拟机大小，默认情况下设置为“Standard_A1”。单击[此处](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)，查看有关 Azure 虚拟机大小和位置的最新信息。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p113">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="2ecca-174">要为 DC1 创建 Azure 虚拟机，请填写资源组名称，并在本地计算机上在 Azure PowerShell 命令提示符运行下面这些命令。</span><span class="sxs-lookup"><span data-stu-id="2ecca-174">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="2ecca-p114">系统将提示你为 DC1 上的本地管理员帐户输入用户名和密码。使用强密码，并在安全位置记录名称和密码。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p114">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="2ecca-177">接下来，连接到 DC1 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="2ecca-177">Next, connect to the DC1 virtual machine.</span></span>
  
1. <span data-ttu-id="2ecca-178">在 [Azure 门户](https://portal.azure.com)中，单击“**资源组”>** [新资源组的名称] \*\* > DC1 >“连接\*\*”。</span><span class="sxs-lookup"><span data-stu-id="2ecca-178">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [the name of your new resource group] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="2ecca-p115">在打开的窗格中，单击“**下载 RDP 文件**”。打开下载的 DC1.rdp 文件，然后单击“**连接**”。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p115">In the open pane, click **Download RDP file**. Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="2ecca-181">指定 DC1 本地管理员帐户名：</span><span class="sxs-lookup"><span data-stu-id="2ecca-181">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="2ecca-182">对于 Windows 7：</span><span class="sxs-lookup"><span data-stu-id="2ecca-182">For Windows 7:</span></span>
    
    <span data-ttu-id="2ecca-p116">在“Windows 安全性”\*\*\*\* 对话框中，单击“使用另一个帐户”\*\*\*\*。在“用户名称”\*\*\*\* 中，键入 **DC1\\**[本地管理员帐户名称]</span><span class="sxs-lookup"><span data-stu-id="2ecca-p116">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="2ecca-185">对于 Windows 8 或 Windows 10：</span><span class="sxs-lookup"><span data-stu-id="2ecca-185">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="2ecca-p117">在“Windows 安全性”\*\*\*\* 对话框中，单击“更多选择”\*\*\*\*，然后单击“使用不同帐户”\*\*\*\*。在“用户名”\*\*\*\* 中，键入 **DC1\\**[本地管理员帐户名称]。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p117">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="2ecca-188">在“密码”\*\*\*\* 中，键入本地管理员帐户密码，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ecca-188">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="2ecca-189">出现提示时，请单击“是”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ecca-189">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="2ecca-190">接下来，在 DC1 上管理员一级的 Windows PowerShell 命令提示符处，使用下面的命令将额外的数据磁盘添加为新卷，驱动器号为 F:。</span><span class="sxs-lookup"><span data-stu-id="2ecca-190">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="2ecca-p118">接下来，将 DC1 配置为 corp.contoso.com 域的域控制器和 DNS 服务器。在管理员级别 Windows PowerShell 命令提示符中，运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p118">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
<span data-ttu-id="2ecca-p119">需指定安全模式管理员密码。在安全的位置存储该密码。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p119">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="2ecca-195">请注意，这些命令可能需要几分钟才能完成。</span><span class="sxs-lookup"><span data-stu-id="2ecca-195">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="2ecca-196">DC1 重启后，使用域凭据重新连接到 DC1 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="2ecca-196">After DC1 restarts, reconnect to the DC1 virtual machine using domain credentials.</span></span>
  
1. <span data-ttu-id="2ecca-197">在 [Azure 门户](https://portal.azure.com)中，单击“资源组 > [你的资源组名称] \*\*\*\*> DC1 > 连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ecca-197">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [your resource group name] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="2ecca-198">运行下载的 DC1.rdp 文件，然后单击“连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ecca-198">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="2ecca-p120">在“Windows 安全性”\*\*\*\* 中，单击“使用另一个帐户”\*\*\*\*。在“用户名称”\*\*\*\* 中，键入 **CORP\\**[本地管理员帐户名称]。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p120">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="2ecca-201">在“密码”\*\*\*\* 中，键入本地管理员帐户密码，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ecca-201">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="2ecca-202">出现提示时，请单击“是”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ecca-202">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="2ecca-p121">接下来，在 Active Directory 中创建一个用户帐户，将使用该帐户登录到 CORP 域成员计算机。在管理员级别 Windows PowerShell 命令提示符中，运行此命令。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p121">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="2ecca-p122">请注意，此命令会提示你提供用户 1 帐户密码。由于此帐户将用于所有 CORP 域成员计算机的远程桌面连接，请选择强密码。记录 User1 帐户密码并将其存储在安全位置。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p122">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="2ecca-p123">接下来，将新的 User1 帐户配置为企业管理员。在管理员级别 Windows PowerShell 命令提示符处运行此命令。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p123">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="2ecca-210">关闭与 DC1 的远程桌面会话，然后使用 CORP\\User1 帐户重新连接。</span><span class="sxs-lookup"><span data-stu-id="2ecca-210">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="2ecca-211">接下来，若要允许 Ping 工具使用流量，请在管理员级别 Windows PowerShell 命令提示符处运行此命令。</span><span class="sxs-lookup"><span data-stu-id="2ecca-211">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="2ecca-212">当前配置如下。</span><span class="sxs-lookup"><span data-stu-id="2ecca-212">This is your current configuration.</span></span>
  
![使用 DC1 虚拟机在 Azure 中进行基础配置的第 2 步](media/49069908-29c3-4d73-87f7-debbea067261.png)
  
### <a name="step-3-configure-app1"></a><span data-ttu-id="2ecca-214">步骤 3：配置 APP1</span><span class="sxs-lookup"><span data-stu-id="2ecca-214">Step 3: Configure APP1</span></span>

<span data-ttu-id="2ecca-215">在这一步，创建和配置 APP1，它提供 Web 和文件共享服务。</span><span class="sxs-lookup"><span data-stu-id="2ecca-215">In this step, you create and configure APP1, which provides web and file sharing services.</span></span>

> [!NOTE]
> <span data-ttu-id="2ecca-p124">执行以下命令块前，请确保选择的 Azure 区域（位置）支持 Azure 虚拟机大小，默认情况下设置为“Standard_A1”。单击[此处](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)，查看有关 Azure 虚拟机大小和位置的最新信息。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p124">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="2ecca-218">若要为 APP1 创建 Azure 虚拟机，请填写资源组名称，并在本地计算机上的 Azure PowerShell 命令提示符处运行下面这些命令。</span><span class="sxs-lookup"><span data-stu-id="2ecca-218">To create an Azure Virtual Machine for APP1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="2ecca-219">接下来，使用 APP1 本地管理员帐户名称和密码连接到 APP1 虚拟机，然后打开 Windows PowerShell 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="2ecca-219">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="2ecca-220">若要检查 APP1 和 DC1 之间的名称解析和网络通信，请运行 **ping dc1.corp.contoso.com** 命令，并查看是否存在四个答复。</span><span class="sxs-lookup"><span data-stu-id="2ecca-220">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="2ecca-221">接下来，在 Windows PowerShell 提示符处使用这些命令将 APP1 虚拟机加入 CORP 域。</span><span class="sxs-lookup"><span data-stu-id="2ecca-221">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="2ecca-222">请注意，在运行 **Add-Computer** 命令后，你必须提供 CORP\\User1 域帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="2ecca-222">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="2ecca-223">App1 重启后，请使用 CORP\\User1 帐户进行连接，然后打开管理员级别 Windows PowerShell 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="2ecca-223">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="2ecca-224">下一步，在 APP1 上的 Windows PowerShell 命令提示符处使用此命令将 APP1 设置为 Web 服务器。</span><span class="sxs-lookup"><span data-stu-id="2ecca-224">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="2ecca-225">下一步，使用这些 PowerShell 命令在 APP1 的文件夹中创建一个共享文件夹和文本文件。</span><span class="sxs-lookup"><span data-stu-id="2ecca-225">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

<span data-ttu-id="2ecca-226">当前配置如下。</span><span class="sxs-lookup"><span data-stu-id="2ecca-226">This is your current configuration.</span></span>
  
![使用 APP1 虚拟机在 Azure 中进行基础配置的第 3 步](media/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
### <a name="step-4-configure-client1"></a><span data-ttu-id="2ecca-228">步骤 4：配置 CLIENT1</span><span class="sxs-lookup"><span data-stu-id="2ecca-228">Step 4: Configure CLIENT1</span></span>

<span data-ttu-id="2ecca-229">在这一步，创建和配置 CLIENT1，这是 Contoso Intranet 上的典型笔记本电脑、平板电脑或台式计算机。</span><span class="sxs-lookup"><span data-stu-id="2ecca-229">In this step, you create and configure CLIENT1, which acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>

> [!NOTE]  
> <span data-ttu-id="2ecca-p125">下面的命令集会创建运行 Windows Server 2016 Datacenter 的 CLIENT1，可对所有类型的 Azure 订阅执行此操作。若有基于 Visual Studio 的 Azure 订阅，可以通过 [Azure 门户](https://portal.azure.com)创建运行 Windows 10 的 CLIENT1。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p125">The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10 with the [Azure portal](https://portal.azure.com).</span></span> 
  

> [!NOTE]
> <span data-ttu-id="2ecca-p126">执行以下命令块前，请确保选择的 Azure 区域（位置）支持 Azure 虚拟机大小，默认情况下设置为“Standard_A1”。单击[此处](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)，查看有关 Azure 虚拟机大小和位置的最新信息。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p126">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="2ecca-234">若要为 CLIENT1 创建 Azure 虚拟机，请填写资源组名称，并在本地计算机上的 Azure PowerShell 命令提示符处运行下面这些命令。</span><span class="sxs-lookup"><span data-stu-id="2ecca-234">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="2ecca-235">接下来，使用 CLIENT1 本地管理员帐户名称和密码连接到 CLIENT1 虚拟机，然后打开管理员级别 Windows PowerShell 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="2ecca-235">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="2ecca-236">若要检查 CLIENT1 和 DC1 之间的名称解析和网络通信，请在 Windows PowerShell 命令提示符处运行 **ping dc1.corp.contoso.com** 命令，并查看是否存在四个答复。</span><span class="sxs-lookup"><span data-stu-id="2ecca-236">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and check that there are four replies.</span></span>
  
<span data-ttu-id="2ecca-237">接下来，在 Windows PowerShell 提示符处使用这些命令将 CLIENT1 虚拟机加入 CORP 域。</span><span class="sxs-lookup"><span data-stu-id="2ecca-237">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="2ecca-238">请注意，在运行 **Add-Computer** 命令后，你必须提供 CORP\\User1 域帐户凭据。</span><span class="sxs-lookup"><span data-stu-id="2ecca-238">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="2ecca-239">CLIENT1 重启后，请使用 CORP\\User1 帐户名称和密码进行连接，然后打开管理员级别 Windows PowerShell 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="2ecca-239">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="2ecca-240">接下来，查看能否从 CLIENT1 访问 APP1 上的 Web 和文件共享资源。</span><span class="sxs-lookup"><span data-stu-id="2ecca-240">Next, check that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
1. <span data-ttu-id="2ecca-241">在服务器管理器的树窗格中，单击“本地服务器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ecca-241">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="2ecca-242">在“CLIENT1 的属性”\*\*\*\* 中，单击“IE 增强的安全配置”\*\*\*\* 旁边的“打开”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ecca-242">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="2ecca-243">在“Internet Explorer 增强的安全性配置”\*\*\*\* 中，为**管理员**和**用户**单击“关闭”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ecca-243">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="2ecca-244">在“开始”屏幕中，单击“**Internet Explorer**”，然后单击“**确定**”。</span><span class="sxs-lookup"><span data-stu-id="2ecca-244">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="2ecca-p127">在地址栏中，键入 **http:\//app1.corp.contoso.com/**，然后按 ENTER 。应会看到 APP1 的默认 Internet Information Services 网页。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p127">In the Address bar, type **http:\//app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="2ecca-247">从桌面任务栏中，单击“文件资源管理器”图标。</span><span class="sxs-lookup"><span data-stu-id="2ecca-247">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="2ecca-p128">在地址栏中，键入 **\\\\app1\\Files**，然后按 ENTER 键。应该会看到带有文件共享文件夹内容的文件夹窗口。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p128">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="2ecca-p129">在“文件”\*\*\*\* 共享文件夹窗口中，双击“Example.txt”\*\*\*\* 文件。应该会看到 Example.txt 文件的内容。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p129">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="2ecca-252">关闭“example.txt - 记事本”\*\*\*\* 和“文件”\*\*\*\* 共享文件夹窗口。</span><span class="sxs-lookup"><span data-stu-id="2ecca-252">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="2ecca-253">最终配置如下。</span><span class="sxs-lookup"><span data-stu-id="2ecca-253">This is your final configuration.</span></span>
  
![使用 CLIENT1 虚拟机在 Azure 中进行基础配置的第 4 步](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="2ecca-255">Azure 中的基础配置现在已完成，可用于应用程序开发和测试或用于构建其他测试环境。</span><span class="sxs-lookup"><span data-stu-id="2ecca-255">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="2ecca-256">单击[此处](http://aka.ms/catlgstack)可直观映射到 Office 365 测试实验室指南堆栈中的所有文章。</span><span class="sxs-lookup"><span data-stu-id="2ecca-256">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the Office 365 Test Lab Guide stack.</span></span>
  
<span data-ttu-id="2ecca-257"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="2ecca-257"><a name="mincost"> </a></span></span>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="2ecca-258">最大限度降低 Azure 中测试环境虚拟机的成本</span><span class="sxs-lookup"><span data-stu-id="2ecca-258">Minimizing the costs of test environment virtual machines in Azure</span></span>

<span data-ttu-id="2ecca-259">若要将运行测试环境虚拟机的成本降至最低，可以执行以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="2ecca-259">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="2ecca-p130">创建测试环境，并尽快执行所需的测试和演示。完成后，删除测试环境的资源组。</span><span class="sxs-lookup"><span data-stu-id="2ecca-p130">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="2ecca-262">关闭测试环境虚拟机，进入已取消分配状态。</span><span class="sxs-lookup"><span data-stu-id="2ecca-262">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="2ecca-263">若要使用 Azure PowerShell 关闭虚拟机，请填写资源组名称并运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="2ecca-263">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="2ecca-264">若要确保所有虚拟机在从停止（已取消分配）状态启动时可以正常工作，则应按以下顺序进行启动：</span><span class="sxs-lookup"><span data-stu-id="2ecca-264">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="2ecca-265">DC1</span><span class="sxs-lookup"><span data-stu-id="2ecca-265">DC1</span></span>
2. <span data-ttu-id="2ecca-266">APP1</span><span class="sxs-lookup"><span data-stu-id="2ecca-266">APP1</span></span>
3. <span data-ttu-id="2ecca-267">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="2ecca-267">CLIENT1</span></span>
    
<span data-ttu-id="2ecca-268">若要使用 Azure PowerShell 按顺序启动虚拟机，请填写资源组名称并运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="2ecca-268">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzVM -ResourceGroupName $rgName -Name "DC1"
Start-AzVM -ResourceGroupName $rgName -Name "APP1"
Start-AzVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="2ecca-269">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ecca-269">See Also</span></span>

- [<span data-ttu-id="2ecca-270">Office 365 开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="2ecca-270">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
- [<span data-ttu-id="2ecca-271">用于 Office 365 开发/测试环境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="2ecca-271">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="2ecca-272">Office 365 开发/测试环境中的高级威胁防护</span><span class="sxs-lookup"><span data-stu-id="2ecca-272">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="2ecca-273">云应用和混合解决方案</span><span class="sxs-lookup"><span data-stu-id="2ecca-273">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
