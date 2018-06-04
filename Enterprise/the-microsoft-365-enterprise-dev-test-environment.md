---
title: Microsoft 365 企业版开发/测试环境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 简介：使用此测试实验室指南创建包含 Office 365 E5、企业移动性+安全性 (EMS) E5 和运行 Windows 10 企业版的计算机的开发/测试环境。
ms.openlocfilehash: 03fa8e0a4e8d90fcb834eeb2491d3dd39b67ff05
ms.sourcegitcommit: 771f227d3049498fcbd7cfbeaf649e3d77e73c86
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "19178644"
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="c5f0a-103">Microsoft 365 企业版开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="c5f0a-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="c5f0a-104">**摘要：** 使用此测试实验室指南创建包含 Office 365 E5、企业移动性+安全性 (EMS) E5 和运行 Windows 10 企业版的计算机的开发/测试环境。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="c5f0a-105">本文通过分步说明，指导你创建一个简化的环境来测试 [Microsoft 365 企业版](https://www.microsoft.com/microsoft-365/enterprise)的特性和功能。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="c5f0a-106">第 1 阶段：创建 Office 365 E5 订阅</span><span class="sxs-lookup"><span data-stu-id="c5f0a-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="c5f0a-107">按照 [Office 365 开发/测试环境](office-365-dev-test-environment.md)的第 2 和 第 3 阶段的步骤，创建轻型 Office 365 开发/测试环境，如图 1 中所示。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-107">Follow the steps in Phase 2 and Phase 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="c5f0a-108">**图 1：带 Azure Active Directory (AD) 租户和用户帐户的 Office 365 E5 订阅**</span><span class="sxs-lookup"><span data-stu-id="c5f0a-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Microsoft 365 企业版开发/测试环境的第 1 阶段](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> <span data-ttu-id="c5f0a-p101">Office 365 E5 订阅试用期是 30 天，可以轻松地将该订阅的试用期扩展为 60 天。对于永久性开发/测试环境，请使用少量许可证创建新的付费订阅。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p101">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="c5f0a-112">第 2 阶段：添加 EMS</span><span class="sxs-lookup"><span data-stu-id="c5f0a-112">Phase 2: Add EMS</span></span>

<span data-ttu-id="c5f0a-113">在此阶段，注册 EMS E5 试用订阅，并将其作为 Office 365 E5 试用订阅添加到同一组织。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-113">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="c5f0a-114">首先，添加 EMS E5 试用订阅，向全局管理员帐户分配 EMS 许可证。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-114">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="c5f0a-p102">通过 Internet 浏览器的专用实例，使用全局管理员帐户凭据登录到 Office 365 门户。如需帮助，请参阅[在哪里登录 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p102">With a private instance of an Internet browser, sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c5f0a-117">单击“管理员”磁贴****。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-117">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="c5f0a-118">在浏览器的“Office 管理中心”标签页的左侧导航中，单击“帐单”>“购买服务”********。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-118">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="c5f0a-p103">在“购买服务”页上，找到“企业移动性 + 安全性 E5”项。将鼠标指针悬停在此项之上，然后单击“开始免费试用”************。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="c5f0a-121">在“确认订单”页上，单击“立即试用”********。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-121">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="c5f0a-122">在“订单签收”页上，单击“继续”********。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-122">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="c5f0a-123">在浏览器的“Office 365 管理中心”标签页的左侧导航中，单击“用户”>“活动用户”********。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-123">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="c5f0a-124">单击全局管理员帐户，然后针对“产品许可证”单击“编辑”********。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-124">Click your global administrator account, and then click Edit for Product licenses.</span></span>
    
9. <span data-ttu-id="c5f0a-125">在“产品许可证”窗格上，将“企业移动性 + 安全性 E5”的产品许可证设置为“打开”，单击“保存”，然后单击“关闭”两次********************。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-125">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c5f0a-p104">企业移动性 + 安全性 E5 的试订阅期为 90 天。对于永久性开发/测试环境，请使用少量许可证新建付费订阅。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="c5f0a-128">****** 如果完成了 [Office 365 开发/测试环境](office-365-dev-test-environment.md)的第 3 阶段，请为所有其他帐户（用户 2、用户 3、用户 4 和用户 5）重复前述过程的步骤 8 和 9。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-128">***If you completed Phase 3 of the*** [Office 365 dev/test environment](office-365-dev-test-environment.md), repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="c5f0a-129">开发/测试环境目前包含：</span><span class="sxs-lookup"><span data-stu-id="c5f0a-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="c5f0a-130">与你列表中的用户帐户共享相同 Azure AD 租户的 Office 365 E5 企业版和 EMS E5 试用订阅。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-130">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
- <span data-ttu-id="c5f0a-131">所有适当的用户帐户（无论是全局管理员帐户还是全部五个用户帐户）都可以使用 Office 365 E5 和 EMS E5。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-131">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="c5f0a-132">图 2 显示添加 EMS 的生成配置。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-132">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="c5f0a-133">**图 2：添加 EMS 试用订阅**</span><span class="sxs-lookup"><span data-stu-id="c5f0a-133">**Figure 2: Adding the EMS trial subscription**</span></span>

![Microsoft 365 企业版开发/测试环境的第 2 阶段](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="c5f0a-135">第 3 阶段：创建 Windows 10 企业版计算机</span><span class="sxs-lookup"><span data-stu-id="c5f0a-135">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="c5f0a-136">在这一阶段，你创建运行 Windows 10 企业版的独立计算机。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-136">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="c5f0a-137">物理计算机</span><span class="sxs-lookup"><span data-stu-id="c5f0a-137">Physical computer</span></span>

<span data-ttu-id="c5f0a-p105">获取个人计算机并在其上安装 Windows 10 企业版。你可在[此处](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)下载 Windows 10 企业版试用。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p105">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="c5f0a-140">虚拟机</span><span class="sxs-lookup"><span data-stu-id="c5f0a-140">Virtual machine</span></span>

<span data-ttu-id="c5f0a-p106">使用你选择的虚拟机监控程序创建一个虚拟机并在其上安装 Windows 10 企业版。你可在[此处](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)下载 Windows 10 企业版试用。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p106">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="c5f0a-143">Azure 中的虚拟机</span><span class="sxs-lookup"><span data-stu-id="c5f0a-143">Virtual machine size in Azure</span></span>

<span data-ttu-id="c5f0a-p107">要在 Microsoft Azure 中创建 Windows 10 虚拟机，***你必须拥有基于 Visual Studio 的订阅***，以便有权访问 Windows 10 企业版的映像。其他类型的 Azure 订阅（如试用版和付费订阅）均无权访问此映像。有关最新信息，请参阅[在 Azure 中使用 Windows 客户端实现开发/测试方案](https://docs.microsoft.com/azure/virtual-machines/windows/client-images)。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p107">To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image. For the latest information, see [Use Windows client in Azure for dev/test scenarios](https://docs.microsoft.com/azure/virtual-machines/windows/client-images).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c5f0a-p108">下面的命令集使用最新版 Azure PowerShell。请参阅 [Azure PowerShell cmdlet 入门](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)。这些命令集构建了名为 WIN10 的 Windows 10 企业版虚拟机及其所需的全部基础架构，其中包括资源组、存储帐户和虚拟网络。如果你已熟悉 Azure 基础架构服务，请修改这些说明以适应当前部署的基础架构。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p108">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="c5f0a-151">首先，启动 Microsoft PowerShell 提示符。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-151">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="c5f0a-152">使用以下命令登录 Azure 帐户。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-152">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="c5f0a-153">使用以下命令获得订阅名称。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-153">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="c5f0a-p109">设置 Azure 订阅。使用正确的名称替换引号内的所有内容（包括 \< 和 > 字符）。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p109">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="c5f0a-p110">接下来，创建一个新的资源组。要确定一个唯一的资源组名称，请使用此命令列出你现有的资源组。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p110">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="c5f0a-p111">使用这些命令创建新的资源组。使用正确的名称替换引号内的所有内容（包括 \< 和 > 字符）。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p111">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="c5f0a-p112">接下来，使用这些命令创建新的虚拟网络和 WIN10 虚拟机。出现提示时，为 WIN10 提供本地管理员帐户的名称和密码，并将这些名称和密码存储在安全位置。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p112">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="c5f0a-162">第 4 阶段：将 Windows 10 计算机加入到 Azure AD</span><span class="sxs-lookup"><span data-stu-id="c5f0a-162">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="c5f0a-163">在创建具有 Windows 10 企业版的物理计算机或虚拟机之后，使用本地管理员帐户登录。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-163">After the physical or virtual machine with Windows 10 Enterprise is created, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c5f0a-p113">对于 Azure 中的虚拟机，使用[这些说明](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)进行连接。使用本地管理员帐户的凭据登录。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p113">For a virtual machine in Azure, connect to it using [these instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="c5f0a-166">接下来，将 WIN10 计算机加入到 Office 365 和 EMS 订阅的 Azure AD 租户。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-166">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="c5f0a-167">在 WIN10 计算机的桌面上，依次单击“开始”>“设置”>“帐户”>“访问单位或学校”>“连接”****。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-167">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="c5f0a-168">在“设置工作或学校帐户”**** 对话框中，单击“将此设备加入到 Azure Active Directory”****。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-168">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="c5f0a-169">在“工作或学校帐户”**** 中，键入 Office 365 订阅的全局管理员帐户名称，然后单击“下一步”****。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-169">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="c5f0a-170">在“输入密码”**** 中，键入全局管理员帐户的密码，然后单击“登录”****。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-170">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="c5f0a-171">当提示你确定这是你的组织时，单击“加入”****，然后单击“完成”****。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-171">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="c5f0a-172">关闭“设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-172">Close the Help window.</span></span>
    
<span data-ttu-id="c5f0a-173">接下来，在 WIN10 计算机上安装 Office 365 专业增强版。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-173">Next, install Office 365 ProPlus on the WIN10 computer.</span></span>
  
1. <span data-ttu-id="c5f0a-p114">打开 Microsoft Edge 浏览器，使用全局管理员帐户凭据登录到 Office 365 门户。如需帮助，请参阅[在哪里登录 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p114">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c5f0a-176">在“Microsoft Office 主页”**** 标签页上，单击“安装 Office 2016”****。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-176">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="c5f0a-177">出现应执行的操作提示时，单击“运行”****，然后针对“用户帐户控制”单击“是”********。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-177">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="c5f0a-p115">等待 Office 完成安装。当看到“**你已设置完毕!**”时，单击“**关闭**”两次。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-p115">Wait for Office to complete its installation. When you see **You're all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="c5f0a-180">图 3 显示生成的环境，其中包括具有以下内容的 WIN10 计算机：</span><span class="sxs-lookup"><span data-stu-id="c5f0a-180">Figure 3 shows your resulting environment, which includes the WIN10 computer that has:</span></span>

- <span data-ttu-id="c5f0a-181">已联接到 Office 365 和 EMS 订阅的 Azure AD 租户。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-181">Joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
- <span data-ttu-id="c5f0a-182">已注册为 Intune 中的 Azure AD 设备 (EMS)。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-182">Enrolled as an Azure AD device in Intune (EMS).</span></span>
- <span data-ttu-id="c5f0a-183">已安装 Office 365 专业增强版。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-183">Has Office 365 ProPlus installed.</span></span>
  
<span data-ttu-id="c5f0a-184">**图 3：Microsoft 365 开发/测试环境最终配置**</span><span class="sxs-lookup"><span data-stu-id="c5f0a-184">**Figure 3: The final configuration of the Microsoft 365 dev/test environment**</span></span>

![Microsoft 365 企业版开发/测试环境的第 4 阶段](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="c5f0a-186">现在你可以试验 [Microsoft 365 企业版](https://www.microsoft.com/microsoft-365/enterprise)的其他功能。</span><span class="sxs-lookup"><span data-stu-id="c5f0a-186">You are now ready to experiment with additional features of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="c5f0a-187">后续步骤</span><span class="sxs-lookup"><span data-stu-id="c5f0a-187">Next steps</span></span>

<span data-ttu-id="c5f0a-188">使用这些附加文章来探索 Microsoft 365 企业版的功能：</span><span class="sxs-lookup"><span data-stu-id="c5f0a-188">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="c5f0a-189">添加移动应用管理 (MAM) 策略</span><span class="sxs-lookup"><span data-stu-id="c5f0a-189">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- <span data-ttu-id="c5f0a-190">[注册 iOS 和 Android 设备](https://technet.microsoft.com/library/mt743077.aspx)</span><span class="sxs-lookup"><span data-stu-id="c5f0a-190">[Intune/EMS:](https://technet.microsoft.com/library/mt743077.aspx) Manage iOS and Android devices.</span></span>
    
- [<span data-ttu-id="c5f0a-191">配置并测试高级安全管理</span><span class="sxs-lookup"><span data-stu-id="c5f0a-191">Configure and test Advanced Security Management</span></span>](https://technet.microsoft.com/library/mt757250.aspx)
    
- [<span data-ttu-id="c5f0a-192">配置和测试高级威胁防护</span><span class="sxs-lookup"><span data-stu-id="c5f0a-192">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="c5f0a-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5f0a-193">See also</span></span>

- [<span data-ttu-id="c5f0a-194">Microsoft 365 企业版文档</span><span class="sxs-lookup"><span data-stu-id="c5f0a-194">Microsoft 365 Enterprise documentation and resources</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)
- [<span data-ttu-id="c5f0a-195">部署 Microsoft 365 企业版</span><span class="sxs-lookup"><span data-stu-id="c5f0a-195">Deploy Microsoft 365 Enterprise</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)
- [<span data-ttu-id="c5f0a-196">One Microsoft 云开发/测试环境</span><span class="sxs-lookup"><span data-stu-id="c5f0a-196">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)
- [<span data-ttu-id="c5f0a-197">云采用测试实验室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="c5f0a-197">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
