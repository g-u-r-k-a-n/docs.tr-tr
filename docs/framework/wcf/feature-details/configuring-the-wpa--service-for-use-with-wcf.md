---
title: Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 2f84afba72e5260a44726dcc812401da5475679f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284101"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma

Bu konuda, Windows Vista 'da HTTP ağ protokolleri üzerinden iletişim kurmayan Windows Communication Foundation (WCF) hizmetlerini barındırmak için Windows Işlem etkinleştirme hizmeti 'ni (WAS olarak da bilinir) ayarlamak için gereken adımlar açıklanmaktadır. Aşağıdaki bölümlerde bu yapılandırma için adımlar ana hatlarıyla verilmiştir:  
  
- WCF etkinleştirme bileşenleri 'ni yükleme (veya yüklemesini onaylama) gereklidir.  
  
- Kullanmak istediğiniz ağ protokol bağlamalarıyla bir WAS sitesi oluşturun veya var olan bir siteye yeni bir protokol bağlaması ekleyin.  
  
- Hizmetlerinizi barındırmak için bir uygulama oluşturun ve gerekli ağ protokollerini kullanmak için bu uygulamayı etkinleştirin.  
  
- HTTP olmayan bir uç nokta sunan bir WCF hizmeti oluşturun.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>HTTP olmayan bağlamalarla bir siteyi yapılandırma  

 WAS ile HTTP olmayan bir bağlama kullanmak için, site bağlamasının WAS yapılandırmasına eklenmesi gerekir. İçin yapılandırma deposu,%windir%\system32\inetsrv\config dizininde bulunan applicationHost.config dosyasıdır. Bu yapılandırma deposu hem WAS hem de IIS 7,0 tarafından paylaşılır.  
  
 applicationHost.config, herhangi bir standart metin Düzenleyicisi (Not Defteri gibi) ile açılabilen bir XML metin dosyasıdır. Ancak, IIS 7,0 komut satırı yapılandırma aracı (appcmd.exe), HTTP olmayan site bağlamaları eklemenin tercih edilen yoludur.  
  
 Aşağıdaki komut, appcmd.exe kullanarak varsayılan Web sitesine bir net. TCP site bağlaması ekler (Bu komut tek bir satır olarak girilir).  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Bu komut, aşağıda belirtilen satırı applicationHost.config dosyasına ekleyerek varsayılan Web sitesine yeni net. TCP bağlamasını ekler.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Uygulamanın HTTP olmayan protokolleri kullanmasını sağlama  

 Uygulama düzeyini tek tek ağ protokolağını etkinleştirebilir veya devre dışı bırakabilirsiniz. Aşağıdaki komutta, içinde çalışan bir uygulama için hem HTTP hem de net. TCP protokollerinin nasıl etkinleştirileceği gösterilmektedir `Default Web Site` .  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 Etkin protokollerin listesi, Ayrıca, \<applicationDefaults> ApplicationHost.config depolanan SITENIN XML yapılandırmasının öğesinde de ayarlanabilir.  
  
 applicationHost.config aşağıdaki XML kodu, hem HTTP hem de HTTP olmayan protokollere yönelik bir siteyi gösterir. HTTP olmayan protokolleri desteklemek için gereken ek yapılandırmaya açıklamalarla birlikte denir.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
      <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
      </application>  
      <bindings>  
            <!-- The following two lines are added by the command. -->
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults
      applicationPool="DefaultAppPool"
      <!-- The following line is inserted by the command. -->
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 HTTP olmayan etkinleştirme için WAS kullanarak bir hizmeti etkinleştirmeye çalışırsanız ve yüklemediyseniz ve yapılandırmadıysanız, şu hatayı görebilirsiniz:  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Bu hatayı görürseniz, HTTP olmayan etkinleştirme için WAS 'nin yüklü ve düzgün şekilde yapılandırıldığından emin olun. Daha fazla bilgi için bkz. [nasıl yapılır: WCF etkinleştirme bileşenlerini yüklemek ve yapılandırmak](how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>HTTP olmayan etkinleştirme için WAS kullanan bir WCF hizmeti oluşturma  

 Uygulamasını yüklemek ve yapılandırmak için gereken adımları gerçekleştirdikten sonra (bkz [. nasıl yapılır: WCF etkinleştirme bileşenlerini yüklemek ve yapılandırmak](how-to-install-and-configure-wcf-activation-components.md)), kullanmak üzere bir hizmetin ETKINLEŞTIRILMESI, IIS 'de barındırılan bir hizmeti yapılandırmaya benzer.  
  
 WAS etkinleştirilmiş bir WCF hizmeti oluşturma hakkında ayrıntılı yönergeler için, bkz. [nasıl yapılır: BIR WCF hizmetini BARıNDıRMA was](how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows İşlem Etkinleştirme Hizmetinde Barındırma](hosting-in-windows-process-activation-service.md)
- [Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))
