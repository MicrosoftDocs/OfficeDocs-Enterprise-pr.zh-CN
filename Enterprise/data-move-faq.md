---
title: 数据移动常见问题解答
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/20/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: 以下是有关将核心数据移动到新的数据中心地理位置的常见问题的解答。
ms.openlocfilehash: fd133dfb28ae99115198977e2e6d637a872078d8
ms.sourcegitcommit: 6639b0f0171f7552111267a64d6b199755bf34fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "38756581"
---
# <a name="data-move-general-faq"></a>数据移动常见问题解答

以下是有关将核心数据移动到新的数据中心地理位置的常见问题的解答。
  
## <a name="what-customers-are-eligible-to-request-a-move"></a>哪些客户有资格请求移动？
  
选择符合新数据中心地理位置的国家/地区的现有 Office 365 商业客户将能够请求移动。  此程序仅适用于分配有符合条件的国家/地区代码的租户，可将核心客户数据迁移到 Office 365 租户，以将适用工作负载的核心客户数据迁移到相应的 Office 365 数据中心地理位置。  请参阅 how [to request the data move](request-your-data-move.md) page，确认国家/地区的资格。   

## <a name="how-do-we-define-core-customer-data"></a>如何定义核心客户数据？
 
Core customer data 是一个术语，指的是在[Microsoft Online Services 术语](https://aka.ms/ost)中定义的客户数据子集： 
- Exchange Online 邮箱内容（电子邮件正文、日历条目和电子邮件附件的内容）
- SharePoint Online 网站内容和该网站中存储的文件
- 上载到 OneDrive for business 的文件 

## <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>在什么时候完成了我的迁移，以便我的租户的核心客户数据存储在我的新 geo 中的地方？

由于 Exchange Online 和 SharePoint Online/OneDrive for Business 之间存在共享依赖关系，因此在迁移这两个服务之前，不能将任何迁移都视为已完成。  Exchange Online 和 SharePoint Online/OneDrive for Business 通常分别以不同的时间进行迁移，且相互独立。  在每个服务迁移完成时，租户管理员会在邮件中心中接收确认，并且可以随时查看管理中心中的数据位置卡，以确认每个服务的 rest 位置的核心客户数据。

## <a name="will-my-tenant-automatically-be-moved-to-the-new-datacenter-geo"></a>我的租户是否会自动移到新的数据中心地理位置？
 
您可以将两个操作作为租户管理员来执行。

- 选择加入。注册 Office 365 移动程序并接收服务的承诺截止时间，以将 rest 上的核心客户数据迁移到新的数据中心地理位置。请参阅 how [to request the data move](request-your-data-move.md) page，获取有关如何选择程序的说明。
- 不执行任何操作。不执行任何操作，这将导致 Microsoft 能够将您的核心客户数据同时移动到新的数据中心地理位置，作为服务管理和优化的一部分。您的数据只能移动到新的数据中心地理位置，而不能移动到任何其他地理位置。当此类服务管理移动完成时，我们会通过消息中心通知。

## <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>如何确保移动过程中的客户数据是安全的，并且不会经历停机时间？
  
数据移动是一种后端服务操作，对最终用户影响最小。 在[数据移动期间和之后](during-and-after-your-data-move.md)会列出受影响的功能。 我们遵循[Microsoft Online Services 服务级别协议（SLA）](https://go.microsoft.com/fwlink/p/?LinkId=523897)的可用性，以便客户无需准备或在移动过程中进行监视。 
  
所有 Office 365 服务在数据中心中运行相同的版本，因此您可以确保功能的一致性。 您的服务在整个过程中完全受支持。
  
## <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>在不同的信息中具有不同的服务会有什么影响？

某些 Office 365 服务可能位于不同的信息中，用于某些现有客户和移动过程中间的客户。  我们的服务独立运行，在这种情况下，不会对用户体验产生任何影响。但是，出于数据驻留目的，在 Exchange Online 和 SharePoint Online/OneDrive for business 都迁移到同一数据中心地理位置之前，不能认为租户迁移已完成。
  
## <a name="will-new-office-365-customers-be-automatically-provisioned-in-the-new-datacenter-geos"></a>在新的数据中心信息中是否会自动预配新的 Office 365 客户？
  
可以。 在新的数据中心地理位置可用后，在注册过程中选择符合新地理位置的国家/地区的企业客户的新 Office 365 将把其核心客户数据存储在新的数据中心地理位置。
  
 ## <a name="where-is-my-core-customer-data-is-located"></a>我的核心客户数据位于何处？

租户管理员可随时查看管理中心内的数据位置卡，以确认每个服务的 rest 位置的核心客户数据，尤其针对其租户。我们还发布了 [office 365 交互式数据中心](https://office.com/datamaps)的数据中心信息、数据中心和365位置的位置，作为对新租户的当前默认核心客户数据的参考。  您可以通过 Microsoft 365 管理中心内组织配置文件下的 "数据位置" 部分，验证 rest 上的客户数据的位置。  
 
## <a name="when-will-i-be-able-to-request-a-move"></a>何时我将能够请求移动？
  
请参阅 how [to request the data move](request-your-data-move.md) page for a datacenter geo 支持的时间段。
  
## <a name="how-can-i-request-to-be-moved"></a>如何请求移动？
  
符合条件的客户将在其[Office 365 管理门户](https://portal.office.com/)中看到一个页面。 请参阅[如何请求数据移动](request-your-data-move.md)以获取有关如何请求移动的说明。 
  
## <a name="can-i-change-my-selection-after-requesting-a-move"></a>在请求移动后，是否可以更改我的选定内容？
  
提交请求后，我们无法将您从进程中删除。
  
## <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>如果我在最后期限之前未请求移动，会发生什么情况？
  
 我们可能会根据异常接受请求，以向你的租户授予完成移动的承诺期限。请 联系[Office 365 支持部门](https://go.microsoft.com/fwlink/p/?LinkID=522459)以发出请求。  请注意，即使不采取自愿加入请求，一些工作负载也可能会移到你的新地理位置，因为 Microsoft 能够在服务管理和优化过程中将你的核心客户数据同时移到新的数据中心地理位置。您的数据只能移动到新的数据中心地理位置，而不能移动到任何其他地理位置。  当此类服务管理移动完成时，我们会通过消息中心通知。
  
 ## <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>如果我想要移动数据以便获得更好的网络性能，该怎么办？
  
接近于 Office 365 datacenter 不能保证更好的网络性能。 有许多因素和组件会影响最终用户与 Office 365 服务之间的网络性能。 有关此和性能调整的详细信息，请参阅[Office 365 的网络规划和性能调整](network-planning-and-performance.md)。
  
 ## <a name="do-all-the-services-move-their-data-on-the-same-day"></a>所有服务是否都在同一天移动其数据？
 
每个服务都独立移动，并且可能会在不同时间移动其数据。
  
 ## <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>我是否可以选择何时移动数据？
 
 客户无法选择特定日期，它们不能延迟移动，也不能共享特定的移动日期或时间范围。
  
 ## <a name="can-you-share-when-my-data-will-be-be-moved"></a>是否可以在移动数据时共享？
  
数据移动是一种后端操作，对最终用户影响最小。 我们需要在全局运营和自动环境中执行数据移动的复杂性、精度和规模将禁止我们在对你的租户或任何其他单一租户完成数据移动时进行共享。 客户在其数据移动完成后，每个参与的服务都会在邮件中心收到一条确认消息。 
  
 ## <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>如果用户在移动数据时访问服务，会发生什么情况？

在[数据移动过程中和之后，请参阅数据移动](during-and-after-your-data-move.md)的完整列表，在每个服务的部分数据移动过程中可能会受到限制。 
  
 ## <a name="how-do-i-know-the-move-is-complete"></a>如何知道移动已完成？
  
观看 Office 365 消息中心，以确认每个服务的数据移动是否已完成。 移动每个服务的数据后，我们将发布一个完成通知，以便您将获得三个完成通知：每个完成通知分别对应于 Exchange Online、SharePoint Online 和 Skype for Business Online。  您还可以通过 Microsoft 365 管理中心中组织配置文件下的 "数据位置" 部分，验证 rest 上的客户数据的位置。  
  
## <a name="i-am-an-office-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>我是一个新的数据中心信息中的 Office 365 客户，但当我注册时，我选择了其他国家/地区。 如何将移动到新的数据中心地理位置？

无法更改与你的租户关联的注册国家/地区。 而是需要使用新订阅创建新的 Office 365 租户，并将用户和数据手动移动到新的租户。
  
## <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-office-365-during-the-exchange-online-move"></a>如果我们在 Exchange Online 移动过程中将电子邮件数据迁移到 Office 365，会发生什么情况？

这是一种非常常见的方案，完全受支持。  Datacenter 信息之间的云迁移不会干扰任何 on premisis to 云邮箱迁移。
  
 ## <a name="can-i-pilot-some-users"></a>我可以试运行某些用户吗？
  
您可以创建单独的试用租户来测试连接，但不能以任何方式将试用租户与现有租户组合在一起。

## <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>我不想等待 Microsoft 移动我的数据。 我是否可以只创建一个新的租户并移动自己？
  
是的，但是此过程不会像 Microsoft 执行数据移动那样顺畅。
  
如果在新的数据中心地理位置之后创建新租户，新租户将托管在新地理位置。 此新租户完全独立于以前的租户，您将负责移动所有用户邮箱、网站内容、域名和其他任何数据。 请注意，不能将租户名称从一个租户移动到另一个租户。 我们建议您等待 Microsoft 提供的移动程序，因为我们将负责移动用户的所有设置、数据和订阅。
  
 ## <a name="im-not-ready-to-be-moved-can-i-pick-a-specific-move-date"></a>我不准备移动，是否可以选择特定的移动日期？
  
否，不能更改每个服务的核心客户数据的移动时间。
  
 ## <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>我的客户数据已移动到新的数据中心地理位置。 我可以向后移动吗？
 
否，这是不可能的。 已移动到新 geo 数据中心的客户不能移动回来。 作为任何地区的客户，你将体验到以前所做的相同质量的服务、性能和安全控制。  [Office 365 多地理](https://aka.ms/multi-geo)位置可供某些客户作为加载项，让单个租户可以创建多个附属信息，并可将用户数据移动到具有数据派驻服务承诺的这些信息中。
  
 ## <a name="do-the-new-datacenter-geos-use-the-same-versions-of-office-365-services-as-the-current-datacenter-geos"></a>新的数据中心信息是否使用与当前数据中心信息相同版本的 Office 365 服务？

可以。
  
## <a name="will-office-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>在新数据中心托管的 Office 365 租户是否适用于该国家/地区之外的用户？
  
A. 可以。 Microsoft 在全球范围内的35国家/地区内的国家/地区的多达130个位置维护一个大型的全球网络，其 Internet 服务提供商（Isp）数量超过2700的对等协议。 用户将能够从 Internet 上的任何位置访问数据中心。

## <a name="my-tenant-is-configured-for-office-365-multi-geohttpsakamsmulti-geo--can-i-still-enroll-in-my-tenant-in-the-office-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>我的租户是为[Office 365 多地理](https://aka.ms/multi-geo)位置配置的。  我是否可以在 Office 365 移动程序中注册我的租户以更改我的默认地理位置并将任何用户不在附属区域中移动到新的默认地理位置？

是的，你的租户符合注册条件。  我们会将所有 EXO 邮箱从当前的默认地理位置移动到新的本地数据中心地理位置。  我们不会移动在 "多地理" 卫星区域中配置的任何 EXO 邮箱，而是按预期继续遵循卫星区域数据派驻服务。  SharePoint Online 和 OneDrive for business 无法迁移到新的数据中心地理位置作为移动程序的一部分，但您可以通过多地理程序将 OneDrive for Business 共享配置为移动到您想要的任何区域。
  
## <a name="related-topics"></a>相关主题

[将核心数据移动到新的 Office 365 数据中心信息](moving-data-to-new-datacenter-geos.md)

[如何请求数据移动](request-your-data-move.md)

[Office 365 多地理位置](https://aka.ms/multi-geo)

[Office 365 交互式数据中心映射](https://office.com/datamaps)

[Office 365 支持](https://go.microsoft.com/fwlink/p/?LinkID=522459)

[适用于 Microsoft Dynamics CRM Online 的新数据中心信息](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[按区域的 Azure 服务](https://azure.microsoft.com/regions/)
