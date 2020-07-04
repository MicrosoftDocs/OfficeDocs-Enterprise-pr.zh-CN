---
title: Office 365 的外部域名系统记录
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/21/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: 摘要：在计划 Office 365 部署时要使用的 DNS 记录的引用列表。
ms.openlocfilehash: d0804cec4ce2c15345a9c4ddc83525d1961f8db4
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996536"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Office 365 的外部域名系统记录

|||
|:-----|:-----|
|![域](media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)|**Want to see a customized list of DNS records for your Office 365 organization?** You can [find the info you need to create Office 365 DNS records](https://support.office.microsoft.com/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67) for your domain in Office 365.  <br/> **Need step-by-step help to add these records at your domain's DNS host, such as GoDaddy or eNom?** [Find links to step-by-step instructions for many popular DNS hosts](https://go.microsoft.com/fwlink/?LinkId=286745). <br/>  **Sticking around to use the reference list for your own custom deployment?** The below list should be used as a reference for your custom Office 365 deployment. You will need to select which records apply to your organization and fill in the appropriate values. <br/> **返回到** [Office 365 的网络规划和性能优化](https://aka.ms/tune)。  <br/> |

Often the SPF and MX records are the hardest to figure out. We've updated our SPF records guidance at the end of this article. The important thing to remember is that _you can only have a single SPF record for your domain_. You can have multiple MX records; however, that can cause problems for mail delivery. Having a single MX record that directs email to one mail system removes many potential problems.
  
The sections below are organized by service in Office 365. To see a customized list of the Office 365 DNS records for your domain, sign in to Office 365 and [Gather the information you need to create Office 365 DNS records](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Office 365（核心服务）所需的外部 DNS 记录
<a name="BKMK_ReqdCore"> </a>

Every Office 365 customer needs to add two records to their external DNS. The first CNAME record ensures that Office 365 can direct workstations to authenticate with the appropriate identity platform. The second required record is to prove you own your domain name.
  
||||
|:-----|:-----|:-----|
|**DNS 记录** <br/> |**用途** <br/> |**要使用的值** <br/> |
|**CNAME** <br/> **（套件）** <br/> |Used by Office 365 to direct authentication to the correct identity platform. [More information](https://go.microsoft.com/fwlink/p/?LinkId=322005) <br/> **注意：** 此 CNAME 仅适用于由世纪互联运营的 Office 365。   |**别名：** msoid  <br/> **目标：** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **（域验证）** <br/> |Used by Office 365 to verify only that you own your domain. It doesn't affect anything else.  <br/> |**主机：**@（或者，对于某些 DNS 托管提供程序，为你的域名）  <br/> **TXT 值：**_由 Office 365 提供的文本字符串_  <br/> Office 365 **域设置向导**提供了用于创建此记录的值。  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Office 365 (Exchange Online) 中的电子邮件所需的外部 DNS 记录
<a name="BKMK_ReqdCore"> </a>

Email in Office 365 requires several different records. The three primary records that all customers should use are the Autodiscover, MX, and SPF records.
  
- **自动发现记录**可允许客户端计算机自动查找 Exchange 并正确配置客户端。

- **The MX record** tells other mail systems where to send email for your domain. **Note:** When you change your email to Office 365, by updating your domain's MX record, ALL email sent to that domain will start coming to Office 365.  
你是否只是想要将几个电子邮件地址切换到 Office 365？ 你可以[通过在自定义域中使用少量电子邮件地址试行 Office 365](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7)。

- **SPF 的 TXT 记录**由收件人的电子邮件系统用于验证发送电子邮件的服务器是批准的服务器。 这将有助于防止电子邮件欺诈和钓鱼等问题。 请参阅本文中[SPF 所需的外部 DNS 记录](external-domain-name-system-records.md#BKMK_SPFrecords)，帮助了解记录中应包含的内容。

使用 Exchange Federation 的电子邮件客户也将需要使用其他 CNAME 和 TXT 记录（列于表格底部）。
  
||||
|:-----|:-----|:-----|
|**DNS 记录** <br/> |**用途** <br/> |**要使用的值** <br/> |
|**CNAME** <br/> **(Exchange Online)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for users.  <br/> |**别名：** Autodiscover  <br/> **目标：** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |将域的传入邮件发送到 Office 365 中的 Exchange Online 服务。  <br/> [!NOTE] 电子邮件流向 Exchange Online 后，应该删除指向你的旧版系统的 MX 记录。   |**域：** 例如，contoso.com  <br/> **目标电子邮件服务器：** \<MX token\> 。mail.protection.outlook.com  <br/> **首选项/优先级：** 低于其他任何 MX 记录（这会确保将邮件传递到 Exchange Online）- 例如，1 或“低”  <br/>  \<MX token\>按照以下步骤查找：  <br/>  登录到 Office 365，转到“Office 365 管理员”\>“域”。  <br/>  在你的域的“操作”列中，选择修复问题。  <br/>  在 MX 记录部分中，选择“我要修复什么？”  <br/>  按照此页面上的说明来更新你的 MX 记录。  <br/> [什么是 MX 优先级？](https://go.microsoft.com/fwlink/p/?LinkId=396471) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Helps to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.  <br/> |[SPF 所需的外部 DNS 记录](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **（Exchange 联合身份验证）** <br/> |用于混合部署的 Exchange 联合身份验证。  <br/> |**TXT 记录 1：** 例如，contoso.com 和相关自定义生成的域证明哈希文本（例如，Y96nu89138789315669824）  <br/> **TXT 记录 2：** 例如，exchangedelegation.contoso.com 和相关的自定义生成的域证明哈希文本（例如，Y3259071352452626169）  <br/> |
|**CNAME** <br/> **（Exchange 联合身份验证）** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service when your company is using Exchange federation. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for your users.  <br/> |**别名：** 例如，Autodiscover.service.contoso.com  <br/> **目标：** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Skype for Business Online 所需的外部 DNS 记录
<a name="BKMK_ReqdCore"> </a>

使用[Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO)时，需要执行特定步骤，以确保正确配置你的网络。

> [!NOTE]
> 这些 DNS 记录也适用于 Teams，尤其是在 Teams 和 Skype for Business Online 混合方案中，其中可能出现某些联合问题。
  
||||
|:-----|:-----|:-----|
|**DNS 记录** <br/> |**用途** <br/> |**要使用的值** <br/> |
|**SRV** <br/> **(Skype for Business Online)** <br/> |Allows your Office 365 domain to share instant messaging (IM) features with external clients by enabling SIP federation. Read more about [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**服务**：sipfederationtls  <br/> **协议：** TCP  <br/> **优先级：** 100  <br/> **权重：** 1  <br/> **端口：** 5061  <br/> **目标：** sipfed.online.lync.com  <br/> **注意：** 如果防火墙或代理服务器阻止在外部 DNS 上进行 SRV 查找，应将此记录添加到内部 DNS 记录。   |
|**SRV** <br/> **(Skype for Business Online)** <br/> |由 Skype for Business 用来协调 Lync 客户端之间的信息流。  <br/> |**服务：** sip  <br/> **协议：** TLS  <br/> **优先级：** 100  <br/> **权重：** 1  <br/> **端口：** 443  <br/> **目标：** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |由 Lync 客户端用来帮助查找 Skype for Business Online 服务和登录。  <br/> |**别名：** sip  <br/> **目标：** sipdir.online.lync.com  <br/> 有关详细信息，请参阅 [Office 365 URL 和 IP 地址范围](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO)。  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |由 Lync 移动客户端用来帮助查找 Skype for Business Online 服务和登录。  <br/> |**别名：** lyncdiscover  <br/> **目标：** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Office 365 单一登录所需的外部 DNS 记录
<a name="BKMK_ReqdCore"> </a>

||||
|:-----|:-----|:-----|
|**DNS 记录** <br/> |**用途** <br/> |**要使用的值** <br/> |
|**主机 (A)** <br/> |Used for single sign-on (SSO). It provides the endpoint for your off-premises users (and on-premises users, if you like) to connect to your Active Directory Federation Services (AD FS) federation server proxies or load-balanced virtual IP (VIP).  <br/> |**目标：** 例如，sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>SPF 所需的外部 DNS 记录
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against. In order to protect against these, once you have set up SPF, you should also configure DKIM and DMARC for Office 365. To get started, see [Use DKIM to validate outbound email sent from your domain in Office 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Next, see [Use DMARC to validate email in Office 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).
  
SPF records are TXT records that help to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.
  
You can only have one SPF record (that is, a TXT record that defines SPF) for your domain. That single record can have a few different inclusions but the total DNS lookups that result can't be more than 10 (this helps prevent denial of service attacks). See the table and other examples below to help you create or update the right SPF record values for your environment.
  
### <a name="structure-of-an-spf-record"></a>SPF 记录的结构

All SPF records contain three parts: the declaration that it is an SPF record, the domains, and IP addresses that should be sending email, and an enforcement rule. You need all three in a valid SPF record. Here's an example of a common SPF record for Office 365 when you use only Exchange Online email:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

从你的域接收电子邮件的电子邮件系统会查看 SPF 记录，如果发送邮件的电子邮件服务器是 Office 365 服务器，则将接受该邮件。 例如，如果发送邮件的服务器是旧的邮件系统或 Internet 上的恶意系统，SPF 检查可能会失败，并且不会递送该邮件。 类似的检查有助于防止欺诈和钓鱼邮件。
  
### <a name="choose-the-spf-record-structure-you-need"></a>选择所需的 SPF 记录结构

对于不只针对 Office 365 使用 Exchange Online 电子邮件的应用场景（例如，当你还使用源自 SharePoint Online 的电子邮件时），请使用下表来确定要在记录的值中包括的内容。
  
> [!NOTE]
> If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656). You can also learn much more about how SPF works with Office 365 by reading [How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787065).
  
|||||
|:-----|:-----|:-----|:-----|
||如果你使用的是...  <br/> |用途  <br/> |添加以下包含内容  <br/> |
|1   <br/> |所有电子邮件系统（必需）  <br/> |以此值开头的所有 SPF 记录  <br/> |v=spf1  <br/> |
|2   <br/> |Exchange Online（常见）  <br/> |仅使用 Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3   <br/> |第三方电子邮件系统（不太常见）  <br/> ||包括：\<email system like mail.contoso.com\>  <br/> |
|4   <br/> |本地邮件系统（不太常见）  <br/> |在使用 Exchange Online Protection 或 Exchange Online 以及其他邮件系统的情况下使用  <br/> |ip4：\<0.0.0.0\>  <br/> ip6：\< : : \>  <br/> 包括：\<mail.contoso.com\>  <br/> 括号 (\<\>) 中的值应是为你的域发送电子邮件的其他邮件系统。  <br/> |
|5   <br/> |所有电子邮件系统（必需）  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>示例：添加到现有 SPF 记录
<a name="bkmk_addtospf"> </a>

If you already have an SPF record, you'll need to add or update values for Office 365. For example, say your existing SPF record for contoso.com is this:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

现在，你正在更新适用于 Office 365 的 SPF 记录。 您将编辑当前记录，以便有一个包含所需值的 SPF 记录。 对于 Office 365，"spf.protection.outlook.com"。
  
正确：
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

不正确：
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>常见 SPF 值的更多示例
<a name="bkmk_addtospf"> </a>

如果使用的是完整的 Office 365 套件并使用 MailChimp 代表你发送营销电子邮件，则 contoso.com 上的 SPF 记录可能如下所示，它使用上表中的行1、3和5。 请记住，第1行和第5行是必需的。
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

另外，如果你具有 Exchange 混合配置，并且其中将发送来自 Office 365 和你的本地邮件系统的电子邮件，则 contoso.com 中的 SPF 记录可能看上去如下所示：
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

These are some common examples that can help you adapt your existing SPF record when you add your domain to Office 365 for email. If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656).
  
以下是可以用于返回的简短链接：[https://aka.ms/o365edns](https://aka.ms/o365edns)
