---
title: 管理 Office 365 终结点
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 7/18/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: 一些网络旨在限制访问到 internet，以确保像这些可以访问 Office 365 的网络和代理管理员需要管理的 Fqdn，Url、 列表和 IP 地址的网络上的计算机组成的 Office 365 终结点列表。要添加到代理服务器或防火墙规则和 PAC 文件，以确保网络请求这些需要是能够访问 Office 365。
ms.openlocfilehash: a1a658ff04bc7306cb953477798d3e32d894d695
ms.sourcegitcommit: 854653f927c9515024a1c9e0a86fd5f2fadb92f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "25359494"
---
# <a name="managing-office-365-endpoints"></a>管理 Office 365 终结点

## <a name="office-365-network-connectivity"></a>Office 365 网络连接

 连接到 Office 365 包含较大，它们通过靠近用户低延迟出口正在进行时，请执行最佳的受信任的网络请求。某些 Office 365 连接可以受益于优化连接。 
  
1. 确保您的防火墙允许列表允许连接到 Office 365 终结点。
    
2. 使用代理服务器基础结构允许 Internet 连接到通配符和未发布的目标。
    
3. 维护最佳外围网络配置。
    
4. [确保您将获得最佳的连接](https://aka.ms/o365perfprinciples)。
    
5. 阅读[Office 365 网络连接原则](office-365-network-connectivity-principles.md)了解用于安全地管理 Office 365 流量和获取最佳性能的连接原则。 
    
![通过防火墙和代理连接到 Office 365。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)
  
## <a name="update-your-firewalls-outbound-allow-lists"></a>更新您的防火墙的出站允许列表

您可以通过发送所有受信任的 Office 365 网络请求直接通过防火墙、 绕过所有其他数据包级别检查或处理优化您的网络。这会减少从延迟性能太慢，并减少外围容量要求。选择要信任的网络请求的最简单方式是使用我们的[预建的 PAC 文件](managing-office-365-endpoints.md#pacfiles)。 
  
如果您的防火墙块出站通信中，您需要确保的所有 IP 和 Fqdn 作为此[XML 文件](https://go.microsoft.com/fwlink/?LinkId=533185)中的**所需**列出位于允许列表。识别所有服务都需要使用一些第三方服务。我们不提供的证书提供商，内容交付网络，DNS 提供程序，如这些第三方服务的 IP 地址等等。获得完整的 Office 365 功能，您必须能够访问请求的 Office 365，无论多少信息我们发布目标的所有目标。 
  
多个目标未发布的 IP 地址或作为与任何特定的完全限定的域名的通配符域列出，若要使用此功能您必须能够解析这些网络请求到当前的 IP 地址所请求并发送通过 Internet 的网络请求。
  
通过使用防火墙分析替您该 XML 文件和更新您根据服务或功能自动您打算通过防火墙直接路由的规则的自动化过程。您还可以使用由社区建立和用于 Cisco XE 路由或 ACL 列表配置、 纯文本或 CSV 导出选项供您分析 XML 的[Azure 范围](https://azurerange.azurewebsites.net/)工具。 
  
网络目标的更长时间说明了以及我们的[引用网站](urls-and-ip-address-ranges.md)上可通过我们的[RSS 基于更改日志](https://go.microsoft.com/fwlink/p/?linkid=236301)，以便您可以订阅的更改。 
  
<a name="pacfiles"> </a>
## <a name="configure-outbound-paths-with-pac-files"></a>使用 PAC 文件配置出站路径

使用 PAC 或 WPAD 文件管理网络请求与 Office 365 相关联，但不具有提供的 IP 地址。通过代理服务器或外围设备发送的典型网络请求会引发其他延迟。时代理身份验证产生最大税费，如信誉查找服务器和尝试检查数据包其他服务可能会导致不佳的用户体验。此外，这些外围网络设备需要足够的容量来处理的所有网络请求。我们建议绕过代理服务器或检查基础结构的直接 Office 365 网络请求。
  
用作我们 PAC 文件之一来确定哪些网络流量将发送到代理并将发送到防火墙的起始位置。如果您不熟悉 PAC 或 WPAD 文件，从我们的 Office 365 顾问之一，请阅读此文章有关[部署 PAC 文件](https://blogs.technet.microsoft.com/undocumentedfeatures/2016/04/06/deploying-the-office-365-proxy-pac-to-manage-your-users/)。您需要查看以下内容作为起点和编辑以符合您的环境。 
  
 **更新 7/10/2018 PAC 文件**。 
  
### <a name="1---pac-file-separates-required-internet-fqdns-from-known-office-365-fqdn"></a>#1-PAC 文件： 分隔所需从已知的 Office 365 FQDN Internet Fqdn。

第一个示例是通过 Internet 仅管理终结点我们推荐方法的演示。绕过 Office 365 目标其中的 IP 地址发布，并将剩余网络请求发送到代理的代理。
  
代码段：

```javascript
// JavaScript source code
//July 2018 - Updates go live 1st August2018
//This PAC file contains all FQDNs needed for all services and splits the traffic between those which Microsoft can provide IPs for (so can be sent through a managed firewall with conditional access if desired) and those which IPs cannot be provided for, so need to go to an unrestricted proxy or egress. 
//Due to the use of wildcards, some extra logic is provided to send traffic to the proxy before a 'direct' wildcard is hit.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    var proxyserver2 = "PROXY 10.10.10.11:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //Catch explicit FQDNs which need the proxy but are covered under wildcarded FQDNs which have IPs. This has to be done first before the wildcard is hit
    if ((shExpMatch(host, "quicktips.skypeforbusiness.com"))    
        || (shExpMatch(host, "*.um.outlook.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r1.res.office365.com")))
    {
        return proxyserver;
    }
        //Send FQDNs which Microsoft provide IPs for direct, so they can be sent via a firewall
    else if ((isPlainHostName(host))
    || (shExpMatch(host, "*.aria.microsoft.com"))    
    || (shExpMatch(host, "*.dc.trouter.io"))
    || (shExpMatch(host, "*.lync.com"))
    || (shExpMatch(host, "*.manage.office.com"))
    || (shExpMatch(host, "*.office365.com"))
    || (shExpMatch(host, "*.onenote.com"))
    || (shExpMatch(host, "*.outlook.com"))
    || (shExpMatch(host, "*.outlook.office.com"))
    || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
    || (shExpMatch(host, "*.protection.office.com"))
    || (shExpMatch(host, "*.sharepoint.com"))
    || (shExpMatch(host, "*.skype.com"))
    || (shExpMatch(host, "*.skypeforbusiness.com"))
    || (shExpMatch(host, "*.svc.ms"))
    || (shExpMatch(host, "*.teams.microsoft.com"))
    || (shExpMatch(host, "*.yammer.com"))
    || (shExpMatch(host, "*.yammerusercontent.com"))    
    || (shExpMatch(host, "*broadcast.officeapps.live.com"))
    || (shExpMatch(host, "*excel.officeapps.live.com"))
    || (shExpMatch(host, "*onenote.officeapps.live.com"))
    || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
    || (shExpMatch(host, "*view.officeapps.live.com"))
    || (shExpMatch(host, "*visio.officeapps.live.com"))
    || (shExpMatch(host, "*word-edit.officeapps.live.com"))
    || (shExpMatch(host, "*word-view.officeapps.live.com"))
    || (shExpMatch(host, "admin.microsoft.com"))    
    || (shExpMatch(host, "account.office.net"))
    || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
    || (shExpMatch(host, "agent.office.net"))
    || (shExpMatch(host, "api.login.microsoftonline.com"))
    || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "apc.delve.office.com"))
    || (shExpMatch(host, "aus.delve.office.com"))
    || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
    || (shExpMatch(host, "becws.microsoftonline.com"))
    || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
    || (shExpMatch(host, "can.delve.office.com"))
    || (shExpMatch(host, "ccs.login.microsoftonline.com"))
    || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
    || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
    || (shExpMatch(host, "clientlog.portal.office.com"))
    || (shExpMatch(host, "companymanager.microsoftonline.com"))
    || (shExpMatch(host, "cus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "delve.office.com"))
    || (shExpMatch(host, "device.login.microsoftonline.com"))    
    || (shExpMatch(host, "ea-000.tasks.osi.office.net"))
    || (shExpMatch(host, "eur.delve.office.com"))
    || (shExpMatch(host, "eus-zzz.tasks.osi.office.net"))
    || (shExpMatch(host, "gbr.delve.office.com"))    
    || (shExpMatch(host, "hip.microsoftonline-p.net"))
    || (shExpMatch(host, "hipservice.microsoftonline.com"))
    || (shExpMatch(host, "home.office.com"))
    || (shExpMatch(host, "ind.delve.office.com"))
    || (shExpMatch(host, "jpn.delve.office.com"))
    || (shExpMatch(host, "kor.delve.office.com"))
    || (shExpMatch(host, "lam.delve.office.com"))
    || (shExpMatch(host, "login.microsoft.com"))
    || (shExpMatch(host, "login.microsoftonline.com"))
    || (shExpMatch(host, "login.microsoftonline-p.com"))
    || (shExpMatch(host, "login.windows.net"))
    || (shExpMatch(host, "logincert.microsoftonline.com"))
    || (shExpMatch(host, "loginex.microsoftonline.com"))
    || (shExpMatch(host, "login-us.microsoftonline.com"))     
    || (shExpMatch(host, "manage.office.com"))
    || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
    || (shExpMatch(host, "nam.delve.office.com"))
    || (shExpMatch(host, "neu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "nexus.microsoftonline-p.com"))
    || (shExpMatch(host, "nexus.officeapps.live.com"))
    || (shExpMatch(host, "nexusrules.officeapps.live.com"))
    || (shExpMatch(host, "office.live.com"))
    || (shExpMatch(host, "officeapps.live.com"))
    || (shExpMatch(host, "passwordreset.microsoftonline.com"))
    || (shExpMatch(host, "portal.microsoftonline.com"))
    || (shExpMatch(host, "portal.office.com"))
    || (shExpMatch(host, "protection.office.com"))
    || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
    || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net"))   
    || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
    || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))
    || (shExpMatch(host, "sea-000.tasks.osi.office.net"))    
    || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
    || (shExpMatch(host, "suite.office.net"))    
    || (shExpMatch(host, "tasks.office.com"))
    || (shExpMatch(host, "teams.microsoft.com"))
    || (shExpMatch(host, "testconnectivity.microsoft.com"))
    || (shExpMatch(host, "webshell.suite.office.com"))
    || (shExpMatch(host, "weu-000.tasks.osi.office.net"))
    || (shExpMatch(host, "wus-000.tasks.osi.office.net"))
    || (shExpMatch(host, "www.office.com")))

    {
        return "DIRECT";
    }
    else
        // Send all unknown IP traffic to Proxy for unrestricted access. This section is not necessary if you have a catchall for all other traffic to go to an unfiltered proxy. 
        //However the fqdns required, but for which we dont have IPs for, are listed here incase you need an explicit list.
   if          ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com")) 
        || (shExpMatch(host, "*.adl.windows.com"))   
        || (shExpMatch(host, "*.api.microsoftstream.com"))      
        || (shExpMatch(host, "*.assets-yammer.com"))   
        || (shExpMatch(host, "*.azureedge.net"))            
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))   
        || (shExpMatch(host, "*.helpshift.com"))   
        || (shExpMatch(host, "*.hockeyapp.net"))    
        || (shExpMatch(host, "*.localytics.com"))    
        || (shExpMatch(host, "*.log.optimizely.com"))    
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))      
        || (shExpMatch(host, "*.msocdn.com")) 
        || (shExpMatch(host, "*.mstea.ms"))    
        || (shExpMatch(host, "*.notification.api.microsoftstream.com")) 
        || (shExpMatch(host, "*.o365weve.com"))     
        || (shExpMatch(host, "*.office.com"))   
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.phonefactor.net"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))  
        || (shExpMatch(host, "*.sfbassets.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.teams.microsoft.com"))  
        || (shExpMatch(host, "*.tenor.com"))  
        || (shExpMatch(host, "*.symcd.com"))     
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))  
        || (shExpMatch(host, "apps.identrust.com"))  
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))        
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com")) 
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))
        || (shExpMatch(host, "connect.facebook.net"))        
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))          
        || (shExpMatch(host, "ecn.dev.virtualearth.net "))   
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))             
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))        
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))   
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))   
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))        
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))      
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))       
        || (shExpMatch(host, "ocsp2.globalsign.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))            
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))              
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net")) 
        || (shExpMatch(host, "r1.res.office365.com"))
        || (shExpMatch(host, "r3.res.office365.com"))
        || (shExpMatch(host, "r4.res.office365.com"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))         
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))   
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))  
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "sway.com")) 
        || (shExpMatch(host, "teams.microsoft.com"))              
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))         
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))    
        || (shExpMatch(host, "web.microsoftstream.com"))         
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))         
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))   
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com"))
        || (shExpMatch(host, "xsi.outlook.com")))

    {
        return proxyserver;
    }
    //Catchall for all other traffic to another proxy 
else return proxyserver;
}

```

### <a name="2---pac-file-connect-to-office-365-over-the-internet-and-expressroute"></a>#2-PAC 文件： Internet 和 ExpressRoute 通过连接到 Office 365
<a name="bkmk_inet-aer"> </a>

第二个示例是方法的我们建议与 ExpressRoute 和 Internet 电路可用时管理连接的演示。发送 ExpressRoute 公布到 ExpressRoute 电路目标和 Internet 仅公布到代理的目标。
  
代码段：

```javascript
// JavaScript source code
//July 2018 Update
// Consolidated FQDNs of URLS which are reachable via Microsoft peering over ExpressRoute. All other traffic sent to a proxy in this example. 
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your traffic flow needs and the Office 365 URL &amp; IP page. 
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
//PAC presumes all Office 365 BGP communities/route filters are allowed.
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
    //SUB-FQDNs of ExpressRoutable wildcards which need to be explicitly sent to the proxy at the top of the PAC because they arent ER routable
    if ((shExpMatch(host, "xsi.outlook.com"))
        || (shExpMatch(host, "r3.res.outlook.com"))
        || (shExpMatch(host, "quicktips.skypeforbusiness.com"))
        || (shExpMatch(host, "*.um.outlook.com")))                  
    {
        return proxyserver;
    }
        //EXPRESS ROUTE DIRECT
    else if ((isPlainHostName(host))  
            || (shExpMatch(host, "*.aria.microsoft.com"))             
            || (shExpMatch(host, "*.dc.trouter.io"))
            || (shExpMatch(host, "*.lync.com"))
            || (shExpMatch(host, "*.manage.office.com"))
            || (shExpMatch(host, "*.outlook.com"))
            || (shExpMatch(host, "*.outlook.office.com"))
            || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
            || (shExpMatch(host, "*.protection.office.com"))
            || (shExpMatch(host, "*.protection.outlook.com"))
            || (shExpMatch(host, "*.sharepoint.com")) 
            || (shExpMatch(host, "*.skype.com")) 
            || (shExpMatch(host, "*.skypeforbusiness.com")) 
            || (shExpMatch(host, "*.svc.ms"))   
            || (shExpMatch(host, "*.teams.microsoft.com"))  
            || (shExpMatch(host, "*broadcast.officeapps.live.com"))
            || (shExpMatch(host, "*excel.officeapps.live.com"))
            || (shExpMatch(host, "*onenote.officeapps.live.com"))
            || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
            || (shExpMatch(host, "*view.officeapps.live.com"))                                 
            || (shExpMatch(host, "*visio.officeapps.live.com"))
            || (shExpMatch(host, "*word-edit.officeapps.live.com"))
            || (shExpMatch(host, "*word-view.officeapps.live.com"))
            || (shExpMatch(host, "account.office.net"))
            || (shExpMatch(host, "adminwebservice.microsoftonline.com"))
            || (shExpMatch(host, "agent.office.net"))  
            || (shExpMatch(host, "apc.delve.office.com"))
            || (shExpMatch(host, "api.login.microsoftonline.com"))
            || (shExpMatch(host, "api.passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "aus.delve.office.com"))
            || (shExpMatch(host, "autologon.microsoftazuread-sso.com")) 
            || (shExpMatch(host, "becws.microsoftonline.com"))
            || (shExpMatch(host, "browser.pipe.aria.microsoft.com"))  
            || (shExpMatch(host, "can.delve.office.com")) 
            || (shExpMatch(host, "ccs.login.microsoftonline.com"))  
            || (shExpMatch(host, "ccs-sdf.login.microsoftonline.com"))
            || (shExpMatch(host, "clientconfig.microsoftonline-p.net"))
            || (shExpMatch(host, "companymanager.microsoftonline.com"))
            || (shExpMatch(host, "delve.office.com"))
            || (shExpMatch(host, "device.login.microsoftonline.com"))
            || (shExpMatch(host, "domains.live.com")) 
            || (shExpMatch(host, "eur.delve.office.com"))
            || (shExpMatch(host, "gbr.delve.office.com"))
            || (shExpMatch(host, "hip.microsoftonline-p.net"))
            || (shExpMatch(host, "hipservice.microsoftonline.com"))
            || (shExpMatch(host, "home.office.com"))
            || (shExpMatch(host, "ind.delve.office.com"))
            || (shExpMatch(host, "jpn.delve.office.com"))
            || (shExpMatch(host, "kor.delve.office.com"))
            || (shExpMatch(host, "lam.delve.office.com"))
            || (shExpMatch(host, "login.microsoft.com"))
            || (shExpMatch(host, "login.microsoftonline.com"))
            || (shExpMatch(host, "login.microsoftonline-p.net"))
            || (shExpMatch(host, "login.windows.net"))
            || (shExpMatch(host, "logincert.microsoftonline.com"))
            || (shExpMatch(host, "loginex.microsoftonline.com"))
            || (shExpMatch(host, "login-us.microsoftonline.com"))
            || (shExpMatch(host, "manage.office.com"))
            || (shExpMatch(host, "mobile.pipe.aria.microsoft.com"))
            || (shExpMatch(host, "nam.delve.office.com"))
            || (shExpMatch(host, "nexus.microsoftonline-p.net"))
            || (shExpMatch(host, "office.live.com")) 
            || (shExpMatch(host, "officeapps.live.com")) 
            || (shExpMatch(host, "outlook.office365.com")) 
            || (shExpMatch(host, "passwordreset.microsoftonline.com"))
            || (shExpMatch(host, "portal.office.com"))
            || (shExpMatch(host, "protection.office.com"))
            || (shExpMatch(host, "provisioningapi.microsoftonline.com"))
            || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
            || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
            || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net"))  
            || (shExpMatch(host, "signup.microsoft.com"))
            || (shExpMatch(host, "smtp.office365.com"))  
            || (shExpMatch(host, "stamp2.login.microsoftonline.com"))
            || (shExpMatch(host, "suite.office.net")) 
            || (shExpMatch(host, "teams.microsoft.com")) 
            || (shExpMatch(host, "webshell.suite.office.com")) 
            || (shExpMatch(host, "www.office.com")))             
       
    {
        return "DIRECT";
    }
        //Catchall for all other traffic to proxy
    else
    {
        return proxyserver;
    }
}

```

### <a name="3---pac-file-manage-all-office-365-destinations-collectively"></a>#3-PAC 文件： 共同管理所有 Office 365 目标
<a name="bkmk_inet-direct"> </a>

第三个示例演示如何发送到单个目标与 Office 365 相关联的所有网络请求。这通常用于绕过的 Office 365 网络请求的所有检查，并提供了您所有在其中发布终结点的格式是在列表中要用于您的自定义的 PAC 格式。
  
代码段：

```javascript
// JavaScript source code
//July 2018 Update new URLS go live 1st August 2018 -
//Consolidated FQDNs required to access Office 365 - All services including optional components covered and elements covered under wildcards removed. 
//Some repeated domains have been consoliodated into unpublished wildcards in order to keep the file as small as possible.
//Includes Core ProPlus URLs but not Office Mobile/IPAD/IOS/ANDROID fqdns from https://support.office.com/en-gb/article/Network-requests-in-Office-365-ProPlus-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d
//Every Effort is made to ensure 100% accuracy but this PAC should be used as an example and cross-checked with your needs and the Office 365 URL &amp; IP page
//Intended only for Worldwide Office 365 instances, which the vast majority of customers will be using
function FindProxyForURL(url, host)
{
    // Define proxy server
    var proxyserver = "PROXY 10.10.10.10:8080";
    // Make host lowercase
    var lhost = host.toLowerCase();
    host = lhost;
   if  ((shExpMatch(host, "*.aadrm.com"))
        || (shExpMatch(host, "*.adhybridhealth.azure.com"))
        || (shExpMatch(host, "*.adl.windows.com"))
        || (shExpMatch(host, "*.api.microsoftstream.com"))  
        || (shExpMatch(host, "*.assets-yammer.com"))
        || (shExpMatch(host, "autologon.microsoftazuread-sso.com"))  
        || (shExpMatch(host, "*.azureedge.net"))   
        || (shExpMatch(host, "*.azurerms.com"))
        || (shExpMatch(host, "*.cloudapp.net")) 
        || (shExpMatch(host, "*.dc.trouter.io"))
        || (shExpMatch(host, "*.entrust.net")) 
        || (shExpMatch(host, "*.geotrust.com"))
        || (shExpMatch(host, "*.helpshift.com"))
        || (shExpMatch(host, "*.hockeyapp.net"))       
        || (shExpMatch(host, "*.localytics.com"))
        || (shExpMatch(host, "*.log.optimizely.com"))     
        || (shExpMatch(host, "*.lync.com"))
        || (shExpMatch(host, "*.microsoft.com"))
        || (shExpMatch(host, "*.microsoftonline.com"))
        || (shExpMatch(host, "*.microsoftonline-p.com"))
        || (shExpMatch(host, "*.microsoftonline-p.net"))
        || (shExpMatch(host, "*.msecnd.net"))
        || (shExpMatch(host, "*.msedge.net"))
        || (shExpMatch(host, "*.msocdn.com"))
        || (shExpMatch(host, "*.mstea.ms"))
        || (shExpMatch(host, "*.o365weve.com"))
        || (shExpMatch(host, "*.office.com"))
        || (shExpMatch(host, "*.office.net"))
        || (shExpMatch(host, "*.office365.com"))
        || (shExpMatch(host, "*.omniroot.com"))
        || (shExpMatch(host, "*.onenote.com"))
        || (shExpMatch(host, "*.onmicrosoft.com"))
        || (shExpMatch(host, "*.outlook.com"))
        || (shExpMatch(host, "*.phonefactor.net")) 
        || (shExpMatch(host, "*.portal.cloudappsecurity.com"))
        || (shExpMatch(host, "*.public-trust.com"))
        || (shExpMatch(host, "*.search.production.apac.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.emea.trafficmanager.net"))
        || (shExpMatch(host, "*.search.production.us.trafficmanager.net"))
        || (shExpMatch(host, "*.secure.skypeassets.com"))
        || (shExpMatch(host, "*.sfbassets.com"))  
        || (shExpMatch(host, "*.sharepoint.com"))
        || (shExpMatch(host, "*.sharepointonline.com"))
        || (shExpMatch(host, "*.skype.com"))
        || (shExpMatch(host, "*.skypeforbusiness.com"))
        || (shExpMatch(host, "*.svc.ms")) 
        || (shExpMatch(host, "*.sway.com"))
        || (shExpMatch(host, "*.symcb.com"))
        || (shExpMatch(host, "*.symcd.com"))
        || (shExpMatch(host, "*.tenor.com"))
        || (shExpMatch(host, "*.users.storage.live.com"))
        || (shExpMatch(host, "*.verisign.com"))
        || (shExpMatch(host, "*.verisign.net"))
        || (shExpMatch(host, "*.windows.net"))
        || (shExpMatch(host, "*.yammer.com"))
        || (shExpMatch(host, "*.yammerusercontent.com"))         
        || (shExpMatch(host, "*broadcast.officeapps.live.com"))
        || (shExpMatch(host, "*cdn.onenote.net"))
        || (shExpMatch(host, "*excel.officeapps.live.com"))
        || (shExpMatch(host, "*onenote.officeapps.live.com"))
        || (shExpMatch(host, "*powerpoint.officeapps.live.com"))
        || (shExpMatch(host, "*view.officeapps.live.com"))
        || (shExpMatch(host, "*visio.officeapps.live.com"))
        || (shExpMatch(host, "*word-edit.officeapps.live.com"))
        || (shExpMatch(host, "*word-view.officeapps.live.com"))    
        || (shExpMatch(host, "account.activedirectory.windowsazure.com"))
        || (shExpMatch(host, "ad.atdmt.com"))
        || (shExpMatch(host, "admin.onedrive.com"))
        || (shExpMatch(host, "ajax.aspnetcdn.com"))
        || (shExpMatch(host, "aka.ms"))
        || (shExpMatch(host, "amp.azure.net"))
        || (shExpMatch(host, "api.microsoftstream.com"))
        || (shExpMatch(host, "apis.live.net"))
        || (shExpMatch(host, "apps.identrust.com")) 
        || (shExpMatch(host, "assets.onestore.ms"))
        || (shExpMatch(host, "auth.gfx.ms"))
        || (shExpMatch(host, "cacerts.digicert.com"))    
        || (shExpMatch(host, "cdn.odc.officeapps.live.com"))  
        || (shExpMatch(host, "cdn.onenote.net"))
        || (shExpMatch(host, "cdn.optimizely.com"))
        || (shExpMatch(host, "cert.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "client.hip.live.com"))     
        || (shExpMatch(host, "connect.facebook.net"))
        || (shExpMatch(host, "crl.globalsign.com"))
        || (shExpMatch(host, "crl.globalsign.net"))
        || (shExpMatch(host, "crl.identrust.com"))    
        || (shExpMatch(host, "crl3.digicert.com"))  
        || (shExpMatch(host, "crl4.digicert.com"))
        || (shExpMatch(host, "cus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "cus-roaming.officeapps.live.com"))      
        || (shExpMatch(host, "dc.services.visualstudio.com"))
        || (shExpMatch(host, "domains.live.com"))
        || (shExpMatch(host, "ea-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "ea-roaming.officeapps.live.com"))           
        || (shExpMatch(host, "ecn.dev.virtualearth.net"))
        || (shExpMatch(host, "eus2-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "eus2-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "eus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "eus-www.sway-cdn.com"))
        || (shExpMatch(host, "eus-www.sway-extensions.com"))
        || (shExpMatch(host, "firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "g.live.com"))
        || (shExpMatch(host, "groupsapi2-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi3-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi4-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "groupsapi-prod.outlookgroups.ms"))  
        || (shExpMatch(host, "isrg.trustid.ocsp.identrust.com"))
        || (shExpMatch(host, "liverdcxstorage.blob.core.windowsazure.com"))
        || (shExpMatch(host, "management.azure.com"))
        || (shExpMatch(host, "mem.gfx.ms"))
        || (shExpMatch(host, "mrodevicemgr.officeapps.live.com"))               
        || (shExpMatch(host, "ncus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "ncus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "neu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "neu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "neu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "nexus.officeapps.live.com"))
        || (shExpMatch(host, "nexusrules.officeapps.live.com"))
        || (shExpMatch(host, "nps.onyx.azure.net"))   
        || (shExpMatch(host, "ocsa.officeapps.live.com"))
        || (shExpMatch(host, "ocsp.digicert.com"))
        || (shExpMatch(host, "ocsp.globalsign.com"))
        || (shExpMatch(host, "ocsp.int-x3.letsencrypt.org"))
        || (shExpMatch(host, "ocsp.msocsp.com"))     
        || (shExpMatch(host, "ocsp2.globalsign.com")) 
        || (shExpMatch(host, "ocspx.digicert.com"))
        || (shExpMatch(host, "ocsredir.officeapps.live.com"))
        || (shExpMatch(host, "ocws.officeapps.live.com"))
        || (shExpMatch(host, "odc.officeapps.live.com"))  
        || (shExpMatch(host, "office.live.com"))
        || (shExpMatch(host, "officeapps.live.com"))
        || (shExpMatch(host, "officecdn.microsoft.com.edgekey.net"))              
        || (shExpMatch(host, "officecdn.microsoft.com.edgesuite.net"))
        || (shExpMatch(host, "ols.officeapps.live.com"))  
        || (shExpMatch(host, "oneclient.sfx.ms"))
        || (shExpMatch(host, "outlook.uservoice.com"))
        || (shExpMatch(host, "platform.linkedin.com"))
        || (shExpMatch(host, "policykeyservice.dc.ad.msft.net"))
        || (shExpMatch(host, "prod.firstpartyapps.oaspapps.com.akadns.net"))
        || (shExpMatch(host, "s.ytimg.com"))
        || (shExpMatch(host, "s0.assets-yammer.com"))  
        || (shExpMatch(host, "scsinstrument-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-asia.trafficmanager.net"))
        || (shExpMatch(host, "scsquery-ss-eu.trafficmanager.net")) 
        || (shExpMatch(host, "scsquery-ss-us.trafficmanager.net")) 
        || (shExpMatch(host, "scus-000.ocws.officeapps.live.com"))
        || (shExpMatch(host, "scus-odc.officeapps.live.com"))         
        || (shExpMatch(host, "scus-roaming.officeapps.live.com"))                 
        || (shExpMatch(host, "sea-odc.officeapps.live.com"))              
        || (shExpMatch(host, "sea-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "secure.globalsign.com"))
        || (shExpMatch(host, "site-cdn.onenote.net"))
        || (shExpMatch(host, "skydrive.wns.windows.com"))
        || (shExpMatch(host, "skypemaprdsitus.trafficmanager.net"))
        || (shExpMatch(host, "spoprod-a.akamaihd.net"))
        || (shExpMatch(host, "ssw.live.com"))
        || (shExpMatch(host, "staffhub.ms"))
        || (shExpMatch(host, "staffhub.uservoice.com"))    
        || (shExpMatch(host, "storage.live.com"))
        || (shExpMatch(host, "telemetry.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "telemetryservice.firstpartyapps.oaspapps.com"))
        || (shExpMatch(host, "web.microsoftstream.com"))   
        || (shExpMatch(host, "weu-000.ocws.officeapps.live.com")) 
        || (shExpMatch(host, "weu-odc.officeapps.live.com"))              
        || (shExpMatch(host, "weu-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wu.client.hip.live.com"))
        || (shExpMatch(host, "wus-000.ocws.officeapps.live.com"))  
        || (shExpMatch(host, "wus-firstpartyapps.oaspapps.com"))  
        || (shExpMatch(host, "wus-odc.officeapps.live.com"))              
        || (shExpMatch(host, "wus-roaming.officeapps.live.com"))              
        || (shExpMatch(host, "wus-www.sway-cdn.com"))
        || (shExpMatch(host, "wus-www.sway-extensions.com"))        
        || (shExpMatch(host, "www.digicert.com"))
        || (shExpMatch(host, "www.google-analytics.com"))
        || (shExpMatch(host, "www.onedrive.com"))
        || (shExpMatch(host, "www.remoteapp.windowsazure.com"))
        || (shExpMatch(host, "www.youtube.com")))
    {
        return proxyserver;
    }
        //Catchall for all other traffic to another proxy
    else return "PROXY 10.10.10.11:8080";
}

```

### <a name="use-custom-scripts-or-manually-create-your-own-pac-files"></a>使用自定义脚本或手动创建您自己的 PAC 文件
<a name="pacfiles_manual"> </a>

下面是一些更多工具从社区，如果您已生成您想要共享保留内容的注释的注释。无的社区本文中引用的工具是正式支持或由 Microsoft 维护和为方便起见此处提供。
  
- 这是最早的社区生成工具，可帮助管理过程，生成的 Office 365 社区成员的工具。下面是指向[下载](https://gallery.technet.microsoft.com/Office-365-Proxy-Pac-60fb28f7)的链接。
    
- 使用可导出的防火墙规则证明： [Microsoft 云 IP API](https://mscloudips.azurewebsites.net/)。
    
- [从 IT Praktyk: RSS 转换](https://gallery.technet.microsoft.com/Convert-the-RSS-channel-5efe18b7)和[XML 转换](https://gallery.technet.microsoft.com/Convert-the-O365IPAddresses-9890d896)。
    
- 从 Peter Abele：[下载](https://gallery.technet.microsoft.com/How-to-create-an-up-to-b1fc33f3)。
    
- 可以使用您的网络分析，以确定哪些网络请求应绕过代理服务器基础结构。用于绕过客户代理的最常见 Fqdn 包括由于的发送和接收来自这些终结点的网络流量。
    
  ```
  outlook.office365.com
  outlook.office.com
  <tenant-name>.sharepoint.com
  <tenant-name>-my.sharepoint.com
  <tenant-name>-<app>.sharepoint.com
  *.Lync.com
  ```

- 确保所有网络请求直接发送到您的防火墙都没有对应项，在防火墙中允许列表，以允许通过的请求。

## <a name="perimeter-network-integration"></a>外围网络集成
<a name="BKMK_Perimeter"> </a>

您知道 Microsoft 的 WAN 是世界上的最大中枢之一？
  
它为 true，此大规模网络是什么使 Office 365 和其他云服务在世界上您无论在何处工作。我们网络组成高带宽、 延迟低、 故障转移能够链接与数千路由英里私下拥有暗光纤，和多 Terabit 数据中心和边缘节点，所有以方便您使用云服务之间的连接。
  
使用如下所示在网络中，您希望贵组织的设备尽可能快地连接到我们的网络。具有超过 2500 ISP 对等关系全局和 70 磅，从您的网络中获取与我们应该是状态的无缝。吧花几分钟，确保您的 ISP 的对等关系最最佳，[下面是一些示例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__)的良好和不好对等 hand 利弊权衡到我们网络。 
  
您可以手动或自动配置网络以最佳方式处理 Office 365 应用程序网络请求，具体取决于您的设备上的设备。您需要做出以最佳方式处理 Office 365 网络流量哪些配置更改将取决于您的环境。Office 365 网络请求可能会受益允许以下的网络配置：
  
- 通过不重要的网络通信的优先级。
    
- 路由到本地出口以避免 backhauling 通过慢 WAN 链接时利用 Microsoft 网络上的可用的低延迟。[下面是讨论](https://blogs.technet.microsoft.com/onthewire/2017/05/03/office-365-connectivity-guidance-part-2/)基于客户服务。 
    
- 使用 DNS 附近本地出口以确保离开本地出口网络请求到达最接近的 Microsoft 对等位置。
    
- 从深度数据包检查或处理以满足规模的延迟要求其他密集型网络数据包排除。
    
现代网络设备包括不同一般的不受信任的 Internet 通信管理网络请求受信任的应用程序，如 Office 365 的功能。与新兴横向方面的 SD WAN 解决方案，流量和路径所选内容的此类区别还可以执行与更改状态的网络，如时间可用性、 延迟或性能的各种连接路径中的点的认知之间用户和云。
  
规划您的网络配置的其他指导信息，请参阅[网络和规划 Office 365 迁移](network-and-migration-planning.md)、[性能疑难解答 for Office 365 计划](performance-troubleshooting-plan.md)和[Office 365 部署计划清单](deployment-planning-checklist.md)。 
  
### <a name="to-implement-this-scenario"></a>若要实现此方案：

如果这些用户可以使用 Office 365 URL 和 IP 定义从 XML 以加快开销本地 （用户）、 低网络的 Office 365 流量出口、 管理其优先级相对于其他应用程序和调整，请与您的网络解决方案或服务提供商Office 365 连接到具体取决于网络条件改变 Microsoft 网络的网络路径。某些解决方案下载和自动化 Office 365 URL 和 IP XMLs 定义其堆栈中。
  
始终确保已实施的解决方案有必要程度恢复能力，Office 365 流量的网络路径的相应地理位置冗余成为发布可容纳对 Office 365 Url 和 Ip 的更改。

## <a name="faq"></a>常见问题解答

常见问题： 管理员疑问连接：
  
### <a name="how-do-i-submit-a-question"></a>如何提交问题？

单击位于底部以指示文章或不是非常有用的链接，并提交任何其他问题。我们监控反馈，使用最常见问题进行了更新此处的问题。
  
### <a name="when-is-the-xml-file-updated"></a>何时更新 XML 文件？

新的终结点宣布时, 通常会有 30 + 天缓冲区它们是有效和网络请求开始转到其之前。此缓冲区是确保客户和合作伙伴已更新其系统的机会。FQDN 和 IP 前缀添加和删除的通知中，这意味着新的 FQDN 将在 XML 文件中使用前 30 天的同时处理 XML 文件中。因为我们停止了网络请求发送到我们之前宣布其删除，当我们删除终结点的 XML 作为通知同时删除的终结点已未使用。
  
### <a name="how-can-i-be-notified-of-changes"></a>如何可以会通知的更改？
<a name="bkmk_changes"> </a>

Office 365 终结点发布每月 30 天通知的末尾。有时会更改，则会发生一次以上一个月或较短的通知期。添加终结点后， [RSS 源](https://go.microsoft.com/fwlink/p/?linkid=236301)中列出的有效日期是其后网络请求将发送到终结点的日期。如果您不熟悉 RSS，下面是对[订阅通过 Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416)或您如何[具有 RSS 源获取更新发送给您](https://go.microsoft.com/fwlink/p/?LinkId=532417)。
  
### <a name="how-do-i-read-the-rss-change-log"></a>如何阅读 RSS 更改日志？
<a name="bkmk_changes"> </a>

订阅 RSS 源后，您可以分析信息自己或脚本。下表描述的格式的 rss 源 o 更加轻松。
  
|**部分**|**第 1 部分**|**第 2 部分**|**第 3 部分**|**第 4 部分**|**第 5 部分**|**第 6 部分**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|**说明** <br/> |计数  <br/> |之后，您可以预期网络请求发送到终结点的日期。  <br/> |功能或服务所需终结点的基本说明。  <br/> |您可以连接到此终结点 ExpressRoute 电路除了 internet 上？  <br/> |**是**-您可以连接到此终结点上的 internet 和 ExpressRoute。  <br/> **无**-仅可以连接到 internet 上的此终结点。  <br/> |目标 FQDN 或 IP 范围正在添加或删除。  <br/> |
|**示例** <br/> |1 /  <br/> |[有效 xx/xx/xxx。  <br/> |必需：\<说明\>。  <br/> |ExpressRoute:  <br/> |\<是/否\>。  <br/> |\<FQDN/IP\>]，  <br/> |

一些其他事情要注意，每个条目都有一的分隔符的常见：
  
- **/**-后计数
- **[** -以指示计数的项
- **.**-使用之间条目的每个不同部分
- **]，** -以指示单输入末尾
- **].**-要指示的所有条目的结束

### <a name="how-do-i-determine-the-location-of-my-tenant"></a>如何确定我租户的位置？

 使用我们的[数据中心映射](https://o365datacentermap.azurewebsites.net/)最佳确定**租户位置**。
  
### <a name="am-i-peering-appropriately-with-microsoft"></a>我我对等适当地与 Microsoft？

 [与 Microsoft 对等](https://www.microsoft.com/peering)更加详细地描述了**Peering 位置**。
  
具有超过 2500 ISP 对等关系全局和 70 磅，从您的网络中获取与我们应该是状态的无缝。吧花几分钟，确保您的 ISP 的对等关系最最佳，[下面是一些示例](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__)的良好和不好对等 hand 利弊权衡到我们网络。 
  
### <a name="how-do-i-determine-which-ip-addresses-to-accept-over-expressroute"></a>如何确定哪些 IP 地址来接受通过 ExpressRoute？

 由[Microsoft 的 IP 范围](https://www.microsoft.com/download/details.aspx?id=53602)和特定的 Office 365 [BGP 社区](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)定义**接受 ExpressRoute 路由**。
  
### <a name="how-do-i-determine-which-endpoints-i-need"></a>如何确定我需要哪些终结点？

我们定期添加新功能和服务到 Office 365 套件中，展开连接横向。如果您已 E3 或 E5 SKU 订阅，需要考虑的事项的终结点列表的简单方式是，您将需要所有这些套件获取完整功能。如果您不到这些 Sku 以下任一订阅的区别是方面终结点数量最少。
  
阅读[Office 365 网络连接原则](office-365-network-connectivity-principles.md)获取 Office 365 终结点类别的详细信息并了解用于安全地管理 Office 365 流量和获取最佳性能的连接原则。 
  
图所示，您可以看到 Office Online 部分中的 FQDN 表的部分中的一个示例。按功能和连接的差异，行进行排列。Office Online 依赖标记的终结点的前两行指示需要在 Office 365 身份验证和标识和门户和共享部分。这是典型的依赖于这些共享服务的 Office 365 中的服务。第三行指示客户端计算机必须能够访问\*。 officeapps.live.com 使用 Office Online 和第四行指示计算机还必须能够访问\*。 cdn.office.net 用于 Office Online。
  
即使两行第三和四个需要使用 Office Online，它们已分离以指示目标是不同：
  
1. \*。 officeapps.live.com 不代表 CDN，对此命名空间的含义请求将直接转到 Microsoft 数据中心。
2. \*。 officeapps.live.com 是在使用 Microsoft Peering ExpressRoute 电路可访问。
3. Office Online 相关联的 IP 地址和\*。 officeapps.live.com 可以找到按照此链接。
4. \*。 cdn.office.net 表示由 Akamai 承载的 CDN，对此命名空间的含义请求将转到 Akamai 数据中心。
5. \*。 cdn.office.net 不可访问 ExpressRoute 电路上。
6. Office Online 相关联的 IP 地址和\*。 cdn.office.net 不可用。

![终结点页的屏幕截图](media/42b487f3-24f3-48fe-9885-f97aae3194f3.png)
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a>我不在发布列表中查看网络请求到 IP 地址，我需要提供对这些访问吗？
<a name="bkmk_MissingIP"> </a>

我们仅向您应通过 Internet 或 ExpressRoute 路由直接向 Office 365 服务器的 IP 地址。这不是您将看到网络请求的所有 IP 地址的完整列表。您将看到对 Microsoft 和第三方拥有、 未发布，IP 地址的网络请求。动态生成或托管方式的更改时，它们阻止及时通知这些 IP 地址。如果您的防火墙无法允许访问基于这些网络请求的 Fqdn，使用 PAC 或 WPAD 文件管理请求。
  
请参阅 IP 与 Office 365 上所需的详细信息？
  
1. 检查使用[CIDR 计算器](http://jodies.de/ipcalc)的较大发布区域中是否包括 IP 地址。
2. 请参阅合作伙伴是否拥有[whois 查询](https://dnsquery.org/)与 IP。如果是 Microsoft 拥有，可能为内部伙伴。
3. 检查证书，在浏览器中连接到 IP 地址使用*HTTPS://\<ip 地址\>*，检查证书以了解哪些域将关联的 IP 地址上列出的域。如果它是 Microsoft 拥有 IP 地址，不在列表中的 Office 365 IP 地址，它是可能的 IP 地址是与 Microsoft CDN 如*MSOCDN.NET*或没有 IP 的已发布信息的另一个 Microsoft 域相关联。如果找到此证书的域是我们声明列出的 IP 地址，请让我们知道。

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a>为什么我看如 nsatc.net 或 akadns.net 中的 Microsoft 域名的名称？
<a name="bkmk_akamai"> </a>

Office 365 和其他 Microsoft 服务使用多个第三方服务，如 Akamai 和 MarkMonitor 来提高 Office 365 体验。若要保留为您提供最佳体验，我们可以更改这些服务将来。这样，我们通常发布此问题的第三方拥有的域、 record 或 IP 地址的 CNAME 记录。第三方域可能承载内容，例如 CDN 或它们可能承载服务，如地理流量管理服务。当您看到这些第三方的连接时，正在重定向或参考，不从客户端的初始请求的窗体。有些客户需要确保这种形式的参考和重定向允许通过显式添加潜在 Fqdn 第三方服务的长列表可能使用。
  
在任何时候恕服务列表中。当前正在使用的服务的一些包括：
  
当您看到包括的请求时，正在使用[MarkMonitor](https://www.markmonitor.com/) * \*。 nsatc.net* 。此服务提供域名称保护和监控防御恶意行为。
  
当您看到对请求[ExactTarget](https://www.marketingcloud.com/)正在使用*\*。 exacttarget.com* 。此服务提供电子邮件链接管理和监视针对恶意行为。
  
当您看到包含以下 Fqdn 之一的请求， [Akamai](https://www.akamai.com/)正在使用中。此服务提供了地理 DNS 和内容交付网络服务。
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="what-are-the-three-types-of-office-365-endpoints"></a>什么是 Office 365 终结点的三种类型？
<a name="bkmk_akamai"> </a>

- 您连接到第三方服务若要检索基本 internet 服务，如 DNS 查找和检索 CDN 内容。您还连接到第三方服务集成，如引入 OneNote 笔记本中的 YouTube 视频。
- 您连接到辅助服务承载和运行 microsoft 如启用您输入您的计算机在最接近的 internet 位置 Microsoft 的全局网络的网络请求的边缘节点。作为地球上的第三个最大网络，这提高了您连接的体验。您还连接到 Microsoft Azure 服务，如 Azure 媒体服务所使用的各种 Office 365 服务。
- 您连接到主例如 Exchange Online 的邮箱服务器或 Skype 的唯一和专有数据所在的位置的业务联机服务器的 Office 365 服务。您可以通过 FQDN 或 IP 地址连接到主 Office 365 服务，并使用 internet 或 ExpressRoute 电路。您只能连接到第三方和辅助服务上 internet 电路使用 Fqdn。

下图显示了这些服务区域之间的差异。在此图中的左下角中的客户的本地网络都有多个网络设备，以帮助管理网络连接。以下内容类似的配置是常见的企业客户。如果您的网络仅有防火墙之间客户端计算机和 internet，也支持，并且您需要确保您的防火墙可以在规则允许列表中支持 Fqdn 和通配符。
  
阅读[Office 365 网络连接原则](office-365-network-connectivity-principles.md)获取 Office 365 终结点类别的详细信息并了解用于安全地管理 Office 365 流量和获取最佳性能的连接原则。 
  
![使用 Office 365 时显示三个不同类型的网络终结点](media/6582bcfa-11ba-4ac2-9b69-14bef0437670.png)
  
### <a name="i-cant-or-dont-want-to-use-any-third-party-service"></a>我无法或不想使用任何第三方服务
<a name="bkmk_thirdparty"> </a>

Office 365 是一套函数构建通过 internet 的服务、 可靠性和可用性承诺基于许多标准 internet 服务不可用。例如，如 DNS、 CRL 和 Cdn 的标准 internet 服务必须可访问以使用 Office 365，就像他们必须使用最先进的 internet 服务，可访问。
  
除了这些基本的 internet 服务，可以使用第三方服务仅用于将功能集成。例如，使用中的 Microsoft 团队 Giphy.com 允许客户无缝包括团队中的 gif 图像。同样，YouTube 和 Flickr 是用于紧密集成到 Office 客户端从 internet 的视频和图像的第三方服务。虽然这些所需的集成，它们被标记为可选这意味着服务的核心功能仍可正常工作，如果终结点无法访问 Office 365 终结点文章中。
  
如果您正在尝试使用 Office 365 和第三方服务就不会访问发现您需要[确保所有标记必需或可选本文中的 Fqdn 允许通过代理和防火墙](urls-and-ip-address-ranges.md)。
  
### <a name="i-cant-or-dont-want-to-use-any-secondary-services"></a>我无法或不想使用任何辅助服务
<a name="bkmk_secondary"> </a>

辅助服务是 Office 365 控件不属于的 Microsoft 服务。这些是诸如边缘网络、 Azure 媒体服务和 Azure 内容交付网络。这些所有需要使用 Office 365，并且必须可访问。
  
如果您正在尝试使用 Office 365 和第三方服务就不会访问发现您需要[确保所有标记必需或可选本文中的 Fqdn 允许通过代理和防火墙](urls-and-ip-address-ranges.md)。
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a>如何阻止访问 Microsoft 的使用者服务？
<a name="bkmk_consumer"> </a>

限制对我们的使用者服务访问应该执行需要您自担风险，阻止使用者服务仅可靠的方式是限制对*login.live.com* FQDN 的访问。广泛的服务，包括非消费服务，例如 MSDN、 TechNet 和其他人使用此 FQDN。限制对此 FQDN 访问可能会导致需要还包括与这些服务关联的网络请求规则例外情况。
  
请记住，阻止访问单独的 Microsoft 客户服务不会阻止的人在您的网络到使用 Office 365 租户或其他服务的 exfiltrate 信息。
  
## <a name="related-topics"></a>相关主题

[Office 365 IP 地址和 URL Web 服务](office-365-ip-web-service.md)

[Microsoft Azure 数据中心 IP 范围](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft 公共 IP 空间](https://www.microsoft.com/download/details.aspx?id=53602)
  
[Microsoft Intune 的网络基础结构要求](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[Power BI 和 ExpressRoute](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[Office 365 URL 和 IP 地址范围](urls-and-ip-address-ranges.md)
  
[管理 ExpressRoute for Office 365 连接](managing-expressroute-for-connectivity.md)
  
[Office 365 网络连接原则](office-365-network-connectivity-principles.md)