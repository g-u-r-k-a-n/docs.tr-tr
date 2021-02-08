---
description: "Hakkında daha fazla bilgi edinin: Windows Communication Foundation ile kullanmak üzere Windows Işlem etkinleştirme hizmeti 'Ni yapılandırma"
title: Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: b98cc776b3a0bd860b4837ba70d58d10a83827dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780628"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="36ede-103">Windows Süreç Etkinleştirme Hizmetini Windows Communication Foundation ile Kullanmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="36ede-103">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>

<span data-ttu-id="36ede-104">Bu konuda, Windows Vista 'da HTTP ağ protokolleri üzerinden iletişim kurmayan Windows Communication Foundation (WCF) hizmetlerini barındırmak için Windows Işlem etkinleştirme hizmeti 'ni (WAS olarak da bilinir) ayarlamak için gereken adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36ede-104">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="36ede-105">Aşağıdaki bölümlerde bu yapılandırma için adımlar ana hatlarıyla verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="36ede-105">The following sections outline the steps for this configuration:</span></span>  
  
- <span data-ttu-id="36ede-106">WCF etkinleştirme bileşenleri 'ni yükleme (veya yüklemesini onaylama) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="36ede-106">Install (or confirm the installation of) the WCF activation components required.</span></span>  
  
- <span data-ttu-id="36ede-107">Kullanmak istediğiniz ağ protokol bağlamalarıyla bir WAS sitesi oluşturun veya var olan bir siteye yeni bir protokol bağlaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="36ede-107">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
- <span data-ttu-id="36ede-108">Hizmetlerinizi barındırmak için bir uygulama oluşturun ve gerekli ağ protokollerini kullanmak için bu uygulamayı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="36ede-108">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
- <span data-ttu-id="36ede-109">HTTP olmayan bir uç nokta sunan bir WCF hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36ede-109">Build a WCF service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="36ede-110">HTTP olmayan bağlamalarla bir siteyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="36ede-110">Configuring a Site with Non-HTTP bindings</span></span>  

 <span data-ttu-id="36ede-111">WAS ile HTTP olmayan bir bağlama kullanmak için, site bağlamasının WAS yapılandırmasına eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="36ede-111">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="36ede-112">İçin yapılandırma deposu,%windir%\system32\inetsrv\config dizininde bulunan applicationHost.config dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="36ede-112">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="36ede-113">Bu yapılandırma deposu hem WAS hem de IIS 7,0 tarafından paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="36ede-113">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="36ede-114">applicationHost.config, herhangi bir standart metin Düzenleyicisi (Not Defteri gibi) ile açılabilen bir XML metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="36ede-114">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="36ede-115">Ancak, IIS 7,0 komut satırı yapılandırma aracı (appcmd.exe), HTTP olmayan site bağlamaları eklemenin tercih edilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="36ede-115">However, the IIS 7.0 command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="36ede-116">Aşağıdaki komut, appcmd.exe kullanarak varsayılan Web sitesine bir net. TCP site bağlaması ekler (Bu komut tek bir satır olarak girilir).</span><span class="sxs-lookup"><span data-stu-id="36ede-116">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="36ede-117">Bu komut, aşağıda belirtilen satırı applicationHost.config dosyasına ekleyerek varsayılan Web sitesine yeni net. TCP bağlamasını ekler.</span><span class="sxs-lookup"><span data-stu-id="36ede-117">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="36ede-118">Uygulamanın HTTP olmayan protokolleri kullanmasını sağlama</span><span class="sxs-lookup"><span data-stu-id="36ede-118">Enabling an Application to Use Non-HTTP Protocols</span></span>  

 <span data-ttu-id="36ede-119">Uygulama düzeyini tek tek ağ protokolağını etkinleştirebilir veya devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36ede-119">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="36ede-120">Aşağıdaki komutta, içinde çalışan bir uygulama için hem HTTP hem de net. TCP protokollerinin nasıl etkinleştirileceği gösterilmektedir `Default Web Site` .</span><span class="sxs-lookup"><span data-stu-id="36ede-120">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="36ede-121">Etkin protokollerin listesi, Ayrıca, \<applicationDefaults> ApplicationHost.config depolanan SITENIN XML yapılandırmasının öğesinde de ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="36ede-121">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="36ede-122">applicationHost.config aşağıdaki XML kodu, hem HTTP hem de HTTP olmayan protokollere yönelik bir siteyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="36ede-122">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="36ede-123">HTTP olmayan protokolleri desteklemek için gereken ek yapılandırmaya açıklamalarla birlikte denir.</span><span class="sxs-lookup"><span data-stu-id="36ede-123">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
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
  
 <span data-ttu-id="36ede-124">HTTP olmayan etkinleştirme için WAS kullanarak bir hizmeti etkinleştirmeye çalışırsanız ve yüklemediyseniz ve yapılandırmadıysanız, şu hatayı görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="36ede-124">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="36ede-125">Bu hatayı görürseniz, HTTP olmayan etkinleştirme için WAS 'nin yüklü ve düzgün şekilde yapılandırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="36ede-125">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> <span data-ttu-id="36ede-126">Daha fazla bilgi için bkz. [nasıl yapılır: WCF etkinleştirme bileşenlerini yüklemek ve yapılandırmak](how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="36ede-126">For more information, see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="36ede-127">HTTP olmayan etkinleştirme için WAS kullanan bir WCF hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="36ede-127">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  

 <span data-ttu-id="36ede-128">Uygulamasını yüklemek ve yapılandırmak için gereken adımları gerçekleştirdikten sonra (bkz [. nasıl yapılır: WCF etkinleştirme bileşenlerini yüklemek ve yapılandırmak](how-to-install-and-configure-wcf-activation-components.md)), kullanmak üzere bir hizmetin ETKINLEŞTIRILMESI, IIS 'de barındırılan bir hizmeti yapılandırmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="36ede-128">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="36ede-129">WAS etkinleştirilmiş bir WCF hizmeti oluşturma hakkında ayrıntılı yönergeler için, bkz. [nasıl yapılır: BIR WCF hizmetini BARıNDıRMA was](how-to-host-a-wcf-service-in-was.md).</span><span class="sxs-lookup"><span data-stu-id="36ede-129">For detailed instructions about building a WAS-activated WCF service, see [How to: Host a WCF Service in WAS](how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ede-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36ede-130">See also</span></span>

- [<span data-ttu-id="36ede-131">Windows İşlem Etkinleştirme Hizmetinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="36ede-131">Hosting in Windows Process Activation Service</span></span>](hosting-in-windows-process-activation-service.md)
- <span data-ttu-id="36ede-132">[Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="36ede-132">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
