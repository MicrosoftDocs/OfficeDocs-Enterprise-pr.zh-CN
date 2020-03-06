---
title: 创建托管有来宾的 B2B 外联网
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
f1.keywords: NOCSH
description: 了解如何使用合作伙伴组织中的受管理的来宾用户创建 B2B extranet 网站或团队。
ms.openlocfilehash: cdf4470920a307d569fcfd650f40c77f4a5423a4
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549061"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a>创建托管有来宾的 B2B 外联网

您可以使用[Azure Active Directory 权限管理](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview)创建 B2B extranet，以与使用 Azure Active Directory 的合作伙伴组织进行协作。 这样，用户可以在 extranet 网站或团队中自行注册，并通过审批工作流接收访问权限。

通过这种共享资源进行协作的方法，合作伙伴组织可以帮助他们在他们的终端上维护和批准来宾用户，减少 IT 部门的负担，并允许最熟悉协作协议的人管理用户访问.

本文逐步介绍了如何创建可通过自助服务访问注册模型与合作伙伴组织共享的资源包（在此示例中为网站或团队）。 

在开始之前，请创建要与合作伙伴组织共享的网站或团队，并为其启用来宾共享。 有关详细信息，请参阅[在网站中与来宾进行协作](collaborate-in-a-site.md)或[与团队中的来宾协作](collaborate-as-a-team.md)。 我们还建议您查看 "[创建安全来宾共享环境](create-a-secure-guest-sharing-environment.md)"，以获取有关安全和合规性功能的信息，您可以使用这些功能来帮助维护与来宾协作时的管理策略。

## <a name="connect-the-partner-organization"></a>连接合作伙伴组织

为了从合作伙伴组织中邀请来宾，您需要在 Azure Active Directory 中将合作伙伴的域添加为连接的组织。

添加已连接的组织
1. 在 " [Azure Active Directory](https://aad.portal.azure.com)" 中，单击 "**身份治理**"。
2. 单击 "**连接的组织**"。
4. 单击 "**添加已连接的组织**"。
5. 键入组织的名称和说明，然后单击 "**下一步： Directory + 域**"。
6. 单击 "**添加目录 + 域**"。
7. 键入要连接的组织的域，然后单击 "**添加**"。
8. 单击 "**连接**"，然后单击 "**下一步：主办方**"。
9. 添加你的组织或你要连接到的组织中的人员，以批准来宾用户的访问权限。
10. 单击 "**下一步：审阅 + 创建**"。
11. 查看您选择的设置，然后单击 "**创建**"。

    ![Azure Active Directory 中的 "连接的组织" 页面的屏幕截图](media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a>选择要共享的资源

选择要与合作伙伴组织共享的资源的第一步是创建要包含它们的目录。

创建目录
1. 在 " [Azure Active Directory](https://aad.portal.azure.com)" 中，单击 "**身份治理**"。
2. 单击 "**目录**"。
3. 单击 "**新建目录**"。
4. 键入目录的名称和说明，并确保**为外部用户****启用**和启用两者都设置为 **"是"**。
5. 单击“**创建**”。

   ![Azure Active Directory 标识管理中的目录页面的屏幕截图](media/identity-governance-catalogs.png)

创建目录后，添加要与合作伙伴组织共享的 SharePoint 网站或团队。

将资源添加到目录
1. 在 Azure AD 标识管理中，单击 "**目录**"，然后单击要在其中添加资源的目录。
2. 单击 "**资源**"，然后单击 "**添加资源**"。
3. 选择要包含在 extranet 中的团队或 SharePoint 网站，然后单击 "**添加**"。

   ![Azure Active Directory 标识管理中的 "目录资源" 页面的屏幕截图](media/identity-governance-catalog-resource.png)

在定义了要共享的资源后，下一步是创建访问包，该程序包将定义合作伙伴用户授予的访问类型和请求访问的新合作伙伴用户的审批流程。

创建访问包
1. 在 Azure AD 标识管理中，单击 "**目录**"，然后单击要在其中创建访问包的目录。
2. 单击 "**访问包**"，然后单击 "**新建 Access 程序包**"。
3. 键入访问包的名称和说明，然后单击 "**下一步：资源角色**"。
4. 从目录中选择要用于 extranet 的资源。
5. 对于每个资源，在 "**角色**" 列中，选择要为使用 extranet 的来宾用户授予的用户角色。
6. 单击 "**下一步：请求**"。
7. 在 "**可请求访问权限的用户**" 下，选择 "**不在你的目录中的用户**"。
8. 确保选择了 "**连接的特定组织**" 选项，然后单击 "**添加目录**"。
9. 选择您之前添加的已连接的组织，然后单击 "**选择**"
10. 在 "**审批**" 下，选择 **"是" 以 "** **需要审批**"。
11. 在 "**首次审批者**" 下，选择您之前添加的某个发起人或选择特定用户。
12. 单击 "**添加回退**" 并选择一个回退审批者。
13. 在 "**启用**" 下，选择 **"是"**。
14. 单击 "**下一步：生命周期**"。
15. 选择要使用的过期和访问检查设置，然后单击 "**下一步：审阅 + 创建**"。
16. 查看您的设置，然后单击 "**创建**"。

    ![Azure Active Directory 标识管理中的 access 程序包屏幕的屏幕截图](media/identity-governance-access-packages.png)

如果要与大型组织合作，您可能希望隐藏该访问包。 如果包处于隐藏状态，则合作伙伴组织中的用户将不会在其 *"我的 Access* " 门户上看到该程序包。 相反，必须向其发送直接链接以注册该包。 隐藏访问包可以减少不适当的访问请求数，还可以帮助保留组织在合作伙伴组织门户中的可用访问包。

将访问包设置为隐藏
1. 在 Azure AD 标识管理中，单击 "**访问包**"，然后单击您的访问包。
2. 在 "**概述**" 页上，单击 "**编辑**"。
3. 在 "**属性**" 下，为 "**隐藏** **" 选择 "是"** ，然后单击 "**保存**"。

   ![编辑访问包属性屏幕的屏幕截图](media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a>邀请合作伙伴用户

如果将访问包设置为 "隐藏"，则需要向合作伙伴组织发送直接链接，以便他们可以请求访问您的网站或团队。

查找访问门户链接
1. 在 Azure AD 标识管理中，单击 "**访问包**"，然后单击您的访问包。
2. 在 "**概述**" 页上，单击 "**我的访问门户" 链接**的 "**复制到剪贴板**" 链接。

   ![具有访问门户链接的 access 程序包属性的屏幕截图](media/identity-governance-access-portal-link.png)

复制链接后，可以将其与合作伙伴组织的联系人共享，并可将其发送给协作团队中的用户。

## <a name="see-also"></a>另请参阅

[创建安全的来宾共享环境](create-a-secure-guest-sharing-environment.md)

