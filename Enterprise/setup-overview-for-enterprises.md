---
title: 为组织部署 Office 365 企业版
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: Adm_O365
ms.assetid: ee73dafb-be54-492e-bcfd-0fbfb5f65e94
description: 这些概述步骤旨在帮助你部署 Office 365、连接 Active Directory、迁移数据以及帮助组织中的人员开始使用最新版本的 Office 2016。
ms.openlocfilehash: 76421a7870358e48798f21866d69672509084c6a
ms.sourcegitcommit: fd137a68c516379a9f09e06987e8d45d92de7ed6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/27/2019
ms.locfileid: "30303596"
---
# <a name="deploy-office-365-enterprise-for-your-organization"></a><span data-ttu-id="b59c2-103">为组织部署 Office 365 企业版</span><span class="sxs-lookup"><span data-stu-id="b59c2-103">Deploy Office 365 Enterprise for your organization</span></span>
<span data-ttu-id="b59c2-p101">准备部署 Office 365 企业版并将其与本地基础结构集成？这些概述步骤旨在帮助你连接目录、迁移数据并帮助组织中的人员开始使用最新版本的 Office 2016。</span><span class="sxs-lookup"><span data-stu-id="b59c2-p101">Ready to deploy and integrate Office 365 Enterprise with your on-premises infrastructure? These overview steps are designed to help you connect your directory, migrate your data, and help the people in your organization begin using the latest version of Office 2016.</span></span>
  
<span data-ttu-id="b59c2-106">这些步骤适用于希望从 Office 365 企业版自定义部署开始的企业和[非盈利组织](https://go.microsoft.com/fwlink/?LinkId=627221)。</span><span class="sxs-lookup"><span data-stu-id="b59c2-106">These steps are for businesses and [nonprofits](https://go.microsoft.com/fwlink/?LinkId=627221) that want to start with a custom deployment of Office 365 Enterprise.</span></span> 
  
<span data-ttu-id="b59c2-p102">没有 Office 365 企业版？有关小型企业的说明，请参阅[设置 Office 365 商业版](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)。</span><span class="sxs-lookup"><span data-stu-id="b59c2-p102">Don't have Office 365 Enterprise? See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for instructions for small businesses.</span></span> 
  
## <a name="guided-enterprise-office-365-setup-process-with-fasttrack"></a><span data-ttu-id="b59c2-109">使用 FastTrack 引导企业 Office 365 设置过程</span><span class="sxs-lookup"><span data-stu-id="b59c2-109">Guided enterprise Office 365 setup process with FastTrack</span></span>
<span data-ttu-id="b59c2-p103">Office 365 **[FastTrack](https://docs.microsoft.com/fasttrack)** 是部署 Office 365 的最佳方法。FastTrack 将指导你完成最常见的部署配置，并可以回答此过程中的问题。如果想获得来自合作伙伴的自助式帮助或指导，请使用 [Office 365 设置指南](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa)、[Office 365 设置向导](https://aka.ms/o365fasttrack)或[找到合格的合作伙伴](https://partnercenter.microsoft.com/zh-CN/pcv/search)。</span><span class="sxs-lookup"><span data-stu-id="b59c2-p103">Office 365 **[FastTrack](https://docs.microsoft.com/fasttrack)** is the best method for deploying Office 365. FastTrack guides you through the most common deployment configurations and can answer questions along the way. If you want to self-help or guidance from a partner, use our [Office 365 setup guide](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa), our [Office 365 setup wizards](https://aka.ms/o365fasttrack), or [find a qualified partner](https://partnercenter.microsoft.com/zh-CN/pcv/search).</span></span>

## <a name="self-deployment-of-office-365"></a><span data-ttu-id="b59c2-113">Office 365 自助部署</span><span class="sxs-lookup"><span data-stu-id="b59c2-113">Self-deployment of Office 365</span></span>
<span data-ttu-id="b59c2-114">如果要自行部署 Office 365，可通过以下部署步骤来获取帮助。</span><span class="sxs-lookup"><span data-stu-id="b59c2-114">If you want to deploy Office 365 on your own, the following deployment steps are here to help.</span></span>

1. <span data-ttu-id="b59c2-p104">**[准备好设置 Office 365](get-your-organization-ready-for-office-365.md)**。这些工具和资源将帮助你在网络、目录和最终用户各方面准备好设置 Office 365。</span><span class="sxs-lookup"><span data-stu-id="b59c2-p104">**[Get ready for Office 365](get-your-organization-ready-for-office-365.md)**. These tools and resources will help you get your network, directory, and end users ready for Office 365.</span></span>

2. <span data-ttu-id="b59c2-p105">**[登录并将 Internet 域添加到 Office 365](https://portal.office.com/Domains/AddDomainWizard.aspx?Scenario=AdvancedSetup)**。登录门户并将一个或多个域添加到 Office 365 订阅，而无需添加用户或迁移电子邮件。如果想同时配置所有用户和服务，请按照[基本设置说明](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa)进行操作。</span><span class="sxs-lookup"><span data-stu-id="b59c2-p105">**[Sign in and add your internet domain(s) to Office 365](https://portal.office.com/Domains/AddDomainWizard.aspx?Scenario=AdvancedSetup)**. Sign into the portal and add one or more domains to your Office 365 subscription without adding users or migrating email. If you want to configure all your users and services at the same time, follow our [basic set up instructions](https://support.office.com/article/Set-up-Office-365-for-business-6a3a29a0-e616-4713-99d1-15eda62d04fa).</span></span>

>[!IMPORTANT] 
><span data-ttu-id="b59c2-120">如果要从本地目录同步用户或使用单一登录，则基本设置说明将不起作用。</span><span class="sxs-lookup"><span data-stu-id="b59c2-120">The basic set up instructions won't work if you want to synchronize your users from an on-premises directory or utilize Single Sign-On.</span></span>

3. <span data-ttu-id="b59c2-p106">**[将目录连接到 Office 365](https://support.office.com/article/Understanding-Office-365-Identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9)**。标识同步和/或单一登录配置选项指南。使用 [AAD Connect 顾问](https://aka.ms/aadconnectpwsync)和 [Azure AD Premium 设置指南](https://aka.ms/aadpguidance)获取自定义的设置指南。</span><span class="sxs-lookup"><span data-stu-id="b59c2-p106">**[Connect your directory to Office 365](https://support.office.com/article/Understanding-Office-365-Identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9)**. Guide to the identity synchronization and/or single sign-on configuration options. Use the [AAD Connect advisor](https://aka.ms/aadconnectpwsync) and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance) to get customized set up guidance.</span></span>
4. <span data-ttu-id="b59c2-p107">**[配置 Office 365 服务和应用程序](configure-services-and-applications.md)**。从此处开始配置电子邮件、文件共享、即时消息或任何其他 Office 365 服务和应用程序。</span><span class="sxs-lookup"><span data-stu-id="b59c2-p107">**[Configure Office 365 services and applications](configure-services-and-applications.md)**. Start here to configure email, file sharing, instant messaging, or any of the other Office 365 services and applications.</span></span>
5. <span data-ttu-id="b59c2-p108">**[将数据迁移到 Office 365 ](migrate-data-to-office-365.md)**。配置服务后，就可以开始迁移数据了。</span><span class="sxs-lookup"><span data-stu-id="b59c2-p108">**[Migrate data to Office 365](migrate-data-to-office-365.md)**. Once the services are configured, you can start migrating data.</span></span>
6. <span data-ttu-id="b59c2-p109">**[让员工使用 Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**。通过这些资源，使用 Office 365 帮助组织中的人员树立信心。</span><span class="sxs-lookup"><span data-stu-id="b59c2-p109">**[Get people using Office 365](https://support.office.com/article/Get-started-with-Office-365-for-business-d6466f0d-5d13-464a-adcb-00906ae87029)**. Help people in your organization build confidence using Office 365 with these resources.</span></span>