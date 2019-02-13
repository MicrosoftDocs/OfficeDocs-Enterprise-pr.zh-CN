---
title: Office 365 第三方 SSL 证书计划
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 10/24/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 摘要：介绍了 Exchange 内部部署和混合部署、使用 AD FS 的 SSO、Exchange Online 服务和 Exchange Web 服务所需的 SSL 证书。
ms.openlocfilehash: 1746cf5059ba83e225e4a2d55c8eebc082366362
ms.sourcegitcommit: bdd0083dc9dc62994de29421a1f4056ebe27f15f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "29952468"
---
# <a name="plan-for-third-party-ssl-certificates-for-office-365"></a>Office 365 第三方 SSL 证书计划

 **摘要：** 介绍 Exchange 内部部署和混合部署、 使用 AD FS 的 SSO 所需的 SSL 证书 Exchange Online 服务和 Exchange Web 服务。 
  
若要加密您的客户端与 Office 365 环境之间的通信，必须基础结构服务器上安装第三方安全套接字层 (SSL) 证书。

||
|:-----|
| 本文是[网络规划和性能优化 Office 365](https://aka.ms/tune)的一部分。|
   
以下 Office 365 组件需要证书：
  
- 本地 Exchange
    
- 单一登录 (SSO)（针对 Active Directory 联合身份验证服务 (AD FS) 联合服务器和 AD FS 联合服务器代理）
    
- Exchange Online 服务，例如自动发现、 Outlook Anywhere，和 Exchange Web 服务
    
- Exchange 混合服务器
    
## <a name="certificates-for-exchange-on-premises"></a>本地 Exchange 的证书

有关如何使用数字证书确保内部部署 Exchange 组织和 Exchange Online 之间的通信安全，请参阅 TechNet 文章[了解证书要求](https://go.microsoft.com/fwlink/p/?LinkID=243657)的概述。
  
## <a name="certificates-for-single-sign-on"></a>单一登录的证书

若要为用户提供的简化单一登录体验，其中包括可靠的安全性，联合服务器或联合服务器代理上需要下表中所示的证书。下表重点介绍 Active Directory 联合身份验证服务 (AD FS)，我们还必须[使用第三方身份提供程序](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility)的详细信息。
  
||||
|:-----|:-----|:-----|
|**证书类型** <br/> |**说明** <br/> |**在部署之前，您需要知道什么？** <br/> |
|**SSL 证书（也称为服务器身份验证证书）** <br/> |这是标准 SSL 证书，用于确保联合服务器、客户端和联合服务器代理计算机之间的通信的安全。  <br/> |AD FS 需要 SSL 证书。默认情况下，AD FS 使用 Internet 信息服务 (IIS) 中的默认网站配置 SSL 证书。<br/> 此 SSL 证书的使用者名称用于确定您部署的 AD FS 的每个实例的联合身份验证服务 (FS) 名称。请考虑选择任何新的证书颁发机构 (CA) 的使用者名称-颁发的证书最佳代表贵公司或组织到 Office 365 的名称。此名称必须是 Internet 可路由。<br/>**注意：** AD FS 要求此 SSL 证书没有无句点 （短名称） 主题名称。          <br/> **建议：** 由于此证书必须由客户端的 AD FS 受信任，我们建议您使用由公共 CA （第三方） 或属于公共受信任的根; CA 颁发的 SSL 证书例如，VeriSign 或 Thawte。  <br/> |
|**令牌签名证书** <br/> |这是标准 X.509 证书，用于安全地签名的所有令牌进行联合服务器颁发的且 Office 365 所接受和验证。  <br/> |令牌签名证书必须包含链接到在 FS 受信任的根的私钥。默认情况下，AD FS 创建自签名的证书。但是，具体取决于您的组织的需要，可以使用 AD FS 管理单元来更改此证书 CA 颁发的证书。<br/>**注意：** 非常重要的 FS 稳定性的令牌签名证书。如果更改证书，Office 365 必须更改的通知。如果未提供通知，则用户无法登录到其 Office 365 服务产品。<br/>**建议：** 我们建议您使用的 AD FS 生成的自签名的令牌签名证书。这样，它管理此证书，默认情况下。例如，当此证书即将过期，AD FS 会生成新的自签名的证书。<br/> |
   
联合服务器代理需要下表中描述的证书。
  
||||
|:-----|:-----|:-----|
|**证书类型** <br/> |**说明** <br/> |**在部署之前，您需要知道什么？** <br/> |
|SSL 证书  <br/> |这是标准 SSL 证书，用于确保联合服务器、联合服务器代理和 Internet 客户端计算机之间的通信的安全。  <br/> |您可以成功运行 AD FS 联合服务器代理配置向导之前，此 SSL 证书必须绑定到 IIS 中的默认网站。  <br/> 此证书必须具有与公司网络中联合服务器上配置的 SSL 证书相同的主题名称。  <br/> **建议：** 建议您使用此联合服务器代理连接到的联合服务器上配置的服务器身份验证证书。  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>自动发现、 Outlook 无处不和 Active Directory 同步的证书

面向外部的 Exchange 2013 和 Exchange 2010，Exchange 2007 和 Exchange 2003 客户端访问服务器 (CASs) 的自动发现、 Outlook Anywhere，和 Active Directory 同步服务的安全连接需要第三方 SSL 证书。您可能已经在您的本地环境中安装此证书。
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Exchange 混合服务器的证书

面向外部的 Exchange 混合服务器要求安全连接与 Exchange Online 服务的第三方 SSL 证书。您需要从第三方 SSL 提供商获取此证书。
  
## <a name="office-365-certificate-chains"></a>Office 365 证书链

本文介绍您可能需要在您的基础结构上安装的证书。我们 Office 365 服务器上安装了证书的详细信息，请参阅[Office 365 证书链](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)。
  

