---
title: .NET Web uygulamanızı veya hizmetinizi Azure App Service geçirin
description: Bir .NET Web uygulamasını veya hizmetini Şirket içinden Azure App Service geçirme hakkında bilgi edinin.
ms.topic: conceptual
ms.date: 07/08/2020
ms.openlocfilehash: 0e2aaa23aedabef007878901ec7297711f140533
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189258"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a>.NET Web uygulamanızı veya hizmetinizi Azure App Service geçirin

[App Service](/azure/app-service/overview) , ölçeklenebilir Web sitelerini ve Web uygulamalarını barındırmak için optimize edilmiş, tam olarak yönetilen bir işlem platformu hizmetidir. Bu makalede, var olan bir uygulamanın Azure App Service, göz önünde bulundurulması gereken değişiklikler ve buluta geçiş için ek kaynaklar için nasıl [taşınması](https://azure.microsoft.com/migration/web-applications/)ve kaydırılabilmesi hakkında bilgiler sağlanmaktadır. Çoğu ASP.NET Web sitesi (WebForms, MVC) ve Hizmetleri (Web API 'SI, WCF), hiçbir değişiklik yapmadan doğrudan Azure App Service taşıyabilir. Bazılarında küçük değişiklikler yapmanız gerekebilir, diğerleri bazı yeniden düzenleme gerektirebilir.

Başlamaya hazır mısınız? [Azure App Service için ASP.NET + SQL uygulamanızı yayımlayın](https://tutorials.visualstudio.com/azure-webapp-migrate/intro).

## <a name="considerations"></a>Dikkat edilmesi gerekenler

### <a name="on-premises-resources-including-sql-server"></a>Şirket içi kaynaklar (SQL Server dahil)

Bunların geçirilmesi veya değiştirilmesi gerekebilmesi için şirket içi kaynaklara erişimi doğrulayın. Şirket içi kaynaklara erişimi azaltıcı seçenekler şunlardır:

* [Azure sanal ağları](/azure/app-service/web-sites-integrate-with-vnet)'nı kullanarak şirket içi kaynaklara App SERVICE bir VPN bağlantısı oluşturun.
* [Azure Relay](/azure/service-bus-relay/relay-what-is-it)kullanarak güvenlik duvarı değişiklikleri olmadan şirket içi hizmetleri güvenle buluta sunun.
* [SQL veritabanı](./sql.md) gibi bağımlılıkları Azure 'a geçirin.
* Bağımlılıkları azaltmak için bulutta hizmet olarak platform teklifleri kullanın. Örneğin, şirket içi posta sunucusuna bağlanmak yerine [SendGrid](/azure/sendgrid-dotnet-how-to-send-email)kullanmayı düşünün.

### <a name="port-bindings"></a>Bağlantı noktası bağlamaları

Azure App Service, HTTP için 80 bağlantı noktasını ve HTTPS trafiği için 443 numaralı bağlantı noktasını destekler.

WCF için aşağıdaki bağlamalar desteklenir:

| Bağlama | Notlar |
|--|--|
| `BasicHttp` |  |
| `WSHttp` |  |
| `WSDualHttpBinding` | [Web yuvası desteğinin](/azure/app-service/web-sites-configure) etkinleştirilmesi gerekir. | [Web yuvası desteğinin](/azure/app-service/web-sites-configure) etkinleştirilmesi gerekir. |
| `NetHttpBinding` | Çift yönlü sözleşmeler için [Web yuvası desteğinin](/azure/app-service/web-sites-configure) etkinleştirilmesi gerekir. | Çift yönlü sözleşmeler için [Web yuvası desteğinin](/azure/app-service/web-sites-configure) etkinleştirilmesi gerekir. |
| `NetHttpsBinding` | Çift yönlü sözleşmeler için [Web yuvası desteğinin](/azure/app-service/web-sites-configure) etkinleştirilmesi gerekir. | Çift yönlü sözleşmeler için [Web yuvası desteğinin](/azure/app-service/web-sites-configure) etkinleştirilmesi gerekir. |
| `BasicHttpContextBinding` |  |
| `WebHttpBinding` |  |
| `WSHttpContextBinding` |  |

### <a name="authentication"></a>Kimlik Doğrulaması

Azure App Service, varsayılan olarak anonim kimlik doğrulamasını ve hedeflenen durumlarda form kimlik doğrulamasını destekler. Windows kimlik doğrulaması yalnızca Azure Active Directory ve ADFS ile tümleştirilirken kullanılabilir. [Şirket içi dizinlerinizi Azure Active Directory tümleştirme hakkında daha fazla bilgi edinin](/azure/active-directory/connect/active-directory-aadconnect).

### <a name="assemblies-in-the-gac-global-assembly-cache"></a>GAC içindeki derlemeler (genel derleme önbelleği)

Bu özellik desteklenmez. Gerekli derlemeleri uygulamanın *\Bin* klasörüne kopyalamayı göz önünde bulundurun. Sunucuda yüklü olan özel *. msi* dosyaları (ÖRNEĞIN, PDF oluşturucuları) kullanılamaz.

### <a name="iis-settings"></a>IIS ayarları

Uygulamanızda applicationHost.config aracılığıyla yapılandırılan her şey artık Azure portal aracılığıyla yapılandırılabilir. Bu, AppPool bit durumu için geçerlidir, WebSockets, yönetilen işlem hattı sürümü, .NET Framework sürümü (2.0/4.0) vb. için geçerlidir. [Uygulama ayarlarınızı](/azure/app-service/web-sites-configure)değiştirmek için [Azure Portal](https://portal.azure.com)gidin, Web uygulamanızın dikey penceresini açın ve **uygulama ayarları** sekmesini seçin.

#### <a name="iis5-compatibility-mode"></a>IıS5 uyumluluk modu

IıS5 uyumluluk modu desteklenmez. Azure App Service, her bir Web uygulaması ve altındaki tüm uygulamalar, belirli bir [uygulama havuzları](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc735247(v=ws.10))kümesiyle aynı çalışan işlemde çalışır.

#### <a name="iis7-schema-compliance"></a>IıS7 + şema uyumluluğu

Bazı öğeler ve öznitelikler Azure App Service IIS şemasında tanımlı değildir. Sorunlarla karşılaşırsanız [xdt dönüştürmeleri](/azure/app-service/configure-common)kullanmayı düşünün.

#### <a name="single-application-pool-per-site"></a>Site başına tek uygulama havuzu

Azure App Service, her bir Web uygulaması ve altındaki tüm uygulamalar aynı uygulama havuzunda çalışır. Her uygulama için ortak ayarlarla tek bir uygulama havuzu oluşturmayı veya ayrı bir Web uygulaması oluşturmayı düşünün.

### <a name="com-and-com-components"></a>COM ve COM+ bileşenleri

Azure App Service platformda COM bileşenlerinin kaydedilmesine izin vermez. Uygulamanız herhangi bir COM bileşeni kullanıyorsa, bunun yönetilen kodda yeniden yazılması ve site ya da uygulamayla dağıtılması gerekir.

### <a name="physical-directories"></a>Fiziksel dizinler

Azure App Service fiziksel sürücüye erişime izin vermez. SMB aracılığıyla dosyalara erişmek için [Azure dosyalarını](/azure/storage/files/storage-files-introduction) kullanmanız gerekebilir. [Azure Blob depolama](/azure/storage/blobs/storage-blobs-introduction) , dosyaları https üzerinden erişim için saklayabilir.

### <a name="isapi-filters"></a>ISAPI filtreleri

Azure App Service, ISAPI filtrelerinin kullanımını destekleyebilir, ancak ISAPI DLL 'nin sitenize dağıtılması ve web.config aracılığıyla kaydedilmesi gerekir.

### <a name="https-bindings-and-ssl"></a>HTTPS bağlamaları ve SSL

HTTPS bağlamaları geçirilmez veya Web sitelerinizle ilişkili SSL sertifikaları değildir. Ancak, site geçişi tamamlandıktan sonra [SSL sertifikaları el ile karşıya](/azure/app-service/app-service-web-tutorial-custom-ssl) yüklenebilir.

### <a name="sharepoint-and-frontpage"></a>SharePoint ve FrontPage

SharePoint ve FrontPage Sunucu Uzantıları (FPSE) desteklenmez.

### <a name="web-site-size"></a>Web sitesi boyutu

Ücretsiz siteler, 1 GB 'lık içerik boyut sınırına sahiptir. Siteniz 1 GB 'den büyükse ücretli bir SKU 'ya yükseltmeniz gerekir. [App Service fiyatlandırmasına](https://azure.microsoft.com/pricing/details/app-service/windows/)bakın.

### <a name="database-size"></a>Veritabanı boyutu

SQL Server veritabanları için lütfen geçerli [SQL veritabanı fiyatlandırmasını](https://azure.microsoft.com/pricing/details/sql-database)denetleyin.

### <a name="azure-active-directory-aad-integration"></a>Azure Active Directory (AAD) Tümleştirmesi

AAD, ücretsiz uygulamalarla çalışmaz. AAD 'yi kullanmak için uygulama SKU 'sunu yükseltmeniz gerekir. [App Service fiyatlandırmasına](https://azure.microsoft.com/pricing/details/app-service/windows/)bakın.

### <a name="monitoring-and-diagnostics"></a>İzleme ve tanılama

İzleme ve Tanılama için geçerli şirket içi çözümlerinizin bulutta çalışması düşüktür. Ancak Azure, Web Apps ile ilgili sorunları belirleyebilmeniz ve bunların hatalarını ayıklamanıza olanak tanımak için günlüğe kaydetme, izleme ve tanılama araçları sağlar. Kendi yapılandırmasında Web uygulamanız için tanılamayı kolayca etkinleştirebilir ve Azure Application Insights kayıtlı günlükleri görüntüleyebilirsiniz. [Web Apps için tanılama günlüğünü etkinleştirme hakkında daha fazla bilgi edinin](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="connection-strings-and-application-settings"></a>Bağlantı dizeleri ve uygulama ayarları

Uygulamanızda kullanılan hassas bilgileri güvenli bir şekilde depolayan bir hizmet olan [Azure Keykasasını](/azure/key-vault/)kullanmayı düşünün. Alternatif olarak, bu verileri bir App Service ayarı olarak da saklayabilirsiniz.

### <a name="dns"></a>DNS

Uygulamanızın gereksinimlerine bağlı olarak DNS yapılandırmasını güncelleştirmeniz gerekebilir. Bu DNS ayarları App Service [özel etki alanı ayarlarından](/azure/app-service/app-service-web-tutorial-custom-domain)yapılandırılabilir.

## <a name="azure-app-service-with-windows-containers"></a>Windows kapsayıcıları ile Azure App Service

Uygulamanız App Service doğrudan geçirilemez, GAC, COM bileşenleri, MSIs kullanımı, .NET FX API 'Lerine, DirectX ve daha fazlasına yönelik kullanımı sağlayan Windows kapsayıcıları kullanarak App Service düşünün.

## <a name="see-also"></a>Ayrıca bkz.

* [Uygulamanızın App Service için uygun olup olmadığını belirleme](https://appmigration.microsoft.com/)
* [Veritabanınızı buluta taşıma](sql.md)
* [Azure Web uygulaması korumalı alanı ayrıntıları ve kısıtlamaları](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)
