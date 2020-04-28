---
title: WCF Veri Hizmetleri Geliştirme ve Dağıtma
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 1dc9f3d261738a6dff0339c094c7aba5e32680ee
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200060"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Geliştirme ve dağıtma WCF Veri Hizmetleri

Bu makalede WCF Veri Hizmetleri geliştirme ve dağıtma hakkında bilgi sağlanır. WCF Veri Hizmetleri hakkında daha fazla temel bilgi için bkz [Getting Started](getting-started-with-wcf-data-services.md) . Başlarken ve [genel bakış](wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>WCF Veri Hizmetleri geliştirin

Açık Veri Protokolü 'Nü (OData) destekleyen bir veri hizmeti oluşturmak için WCF Veri Hizmetleri kullandığınızda, geliştirme sırasında aşağıdaki temel görevleri gerçekleştirmeniz gerekir:

1. **Veri modelini tanımlama**

     WCF Veri Hizmetleri, ilişkisel veritabanlarından geç bağlanan veri türlerine kadar çeşitli veri kaynaklarından verileri temel alan veri modeli tanımlamanızı sağlayan çeşitli veri hizmeti sağlayıcılarını destekler. Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](data-services-providers-wcf-data-services.md).

2. **Veri hizmetini oluşturma**

     En temel veri hizmeti, varlık kapsayıcısının ad alanı nitelikli adı olan <xref:System.Data.Services.DataService%601> bir tür `T` ile sınıfından devralan bir sınıfı kullanıma sunar. Daha fazla bilgi için bkz. [tanımlama WCF veri Hizmetleri](defining-wcf-data-services.md).

3. **Veri hizmetini yapılandırma**

     Varsayılan olarak, WCF Veri Hizmetleri bir varlık kapsayıcısı tarafından açığa çıkarılan kaynaklara erişimi devre dışı bırakır. <xref:System.Data.Services.DataServiceConfiguration> Arabirim, kaynak ve hizmet işlemlerine erişimi yapılandırmanıza, desteklenen OData sürümünü belirtmenize ve toplu işlem davranışları ya da tek bir yanıt akışında döndürülebilecek maksimum varlık sayısı gibi diğer hizmet çapındaki davranışları tanımlamanızı sağlar. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md).

Bu makalede öncelikle Visual Studio kullanılarak veri hizmetlerinin geliştirilmesi ve dağıtılması ele alınmaktadır. Verilerinizi OData akışları olarak göstermek için WCF Veri Hizmetleri tarafından sağlanan esneklik hakkında daha fazla bilgi için bkz. [WCF veri Hizmetleri tanımlama](defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Geliştirme Web sunucusu seçin

Visual Studio 2015 kullanarak bir ASP.NET uygulaması veya ASP.NET Web sitesi olarak bir WCF veri hizmeti geliştirirken, geliştirme sırasında veri hizmetinin çalıştırılacağı bir Web sunucuları seçeneğiniz vardır. Aşağıdaki Web sunucuları, yerel bilgisayarda veri hizmetlerinizin test ve hata ayıklamanızı kolaylaştırmak için Visual Studio ile tümleşir.

1. **Yerel IIS sunucusu**

     Internet Information Services (IIS) üzerinde çalışan bir ASP.NET uygulaması veya ASP.NET Web sitesi olan bir veri hizmeti oluşturduğunuzda, veri hizmetinizi yerel bilgisayarda IIS kullanarak geliştirmenizi ve test etmenizi öneririz. IIS üzerinde veri hizmetinin çalıştırılması, hata ayıklama sırasında HTTP isteklerinin izlenmesini kolaylaştırır. Bu Ayrıca, IIS 'in veri hizmeti için gerekli olan dosyalara, veritabanlarına ve diğer kaynaklara erişmesi için gerekli hakları önceden belirlemenizi de sağlar. Veri hizmetinizi IIS 'de çalıştırmak için hem IIS 'nin hem de Windows Communication Foundation (WCF) doğru bir şekilde yüklendiğinden ve yapılandırıldığından emin olun ve dosya sistemi ve veritabanlarındaki IIS hesaplarına erişim izni verin. Daha fazla bilgi için bkz. [nasıl yapılır: IIS 'de çalışan BIR WCF veri hizmeti geliştirme](how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Yerel IIS sunucusunu yapılandırmak için geliştirme ortamını etkinleştirmek üzere Visual Studio 'Yu yönetici haklarıyla çalıştırmanız gerekir.

2. **Visual Studio geliştirme sunucusu**

     Visual Studio, ASP.NET projelerine yönelik varsayılan Web sunucusu olan Visual Studio geliştirme sunucusu olan yerleşik bir Web sunucusu içerir. Bu Web sunucusu, geliştirme sırasında yerel bilgisayarda ASP.NET projelerini çalıştırmak için tasarlanmıştır. [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md) başlangıçta, Visual Studio geliştirme sunucusunda çalışan bir veri hizmetinin nasıl oluşturulacağı gösterilmektedir.

     Veri hizmetini geliştirmek için Visual Studio geliştirme sunucusunu kullandığınızda aşağıdaki sınırlamalara dikkat edin:

    - Bu sunucuya yalnızca yerel bilgisayar üzerinde erişilebilir.

    - Bu sunucu, HTTP `localhost` iletileri için varsayılan bağlantı noktası olan 80 numaralı bağlantı noktası üzerinde değil, belirli bir bağlantı noktasını dinler. Daha fazla bilgi için bkz. [ASP.NET Web projeleri Için Visual Studio 'Da Web sunucuları](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

    - Bu sunucu, geçerli kullanıcı hesabınızın bağlamında veri hizmetini çalıştırır. Örneğin, yönetici düzeyi Kullanıcı olarak çalıştırıyorsanız, Visual Studio geliştirme sunucusunda çalışan bir veri hizmeti yönetici düzeyinde ayrıcalıklara sahip olur. Bu, veri hizmetinin IIS sunucusuna dağıtıldığında erişim hakkı olmayan kaynaklara erişebilmesini sağlar.

    - Bu sunucu, IIS'nin kimlik doğrulama gibi ek özelliklerini içermez.

    - Bu sunucu, veri hizmetinden büyük ikili verilere erişirken, varsayılan olarak WCF Veri Hizmetleri istemcisi tarafından gönderilen öbekli HTTP akışlarını işleyemez. Daha fazla bilgi için bkz. [Akış sağlayıcısı](streaming-provider-wcf-data-services.md).

    - Bu sunucu, bu karakter anahtar değerlerinde WCF Veri Hizmetleri desteklenmesine rağmen, bir URL 'de nokta (`.`) karakterini işlemeye yönelik sorunlar içeriyor.

    > [!TIP]
    > Geliştirme sırasında veri hizmetlerinizi test etmek için Visual Studio geliştirme sunucusunu da kullanabilirsiniz, ancak bunları IIS çalıştıran bir Web sunucusuna dağıttıktan sonra yeniden sınamanız gerekir.

3. **Azure geliştirme ortamı**

     Visual Studio için Azure Araçları, Visual Studio 'da Azure hizmetleri geliştirmeye yönelik tümleşik bir araç kümesi içerir. Bu araçlarla, Azure 'a dağıtılabilecek bir veri hizmeti geliştirebilirsiniz ve dağıtımdan önce yerel bilgisayarda veri hizmetini test edebilirsiniz. Azure platformunda çalışan bir veri hizmeti geliştirmek için Visual Studio 'Yu kullanırken bu araçları kullanın. Araçları yükleme hakkında bilgi için bkz. [Visual Studio Için Azure araçları 2015](../../../azure/sdk/vs2015-install.md). Azure 'da çalışan bir veri hizmeti geliştirme hakkında daha fazla bilgi için bkz. [Azure 'Da OData hizmetini dağıtma](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="development-tips"></a>Geliştirme İpuçları

Bir veri hizmeti geliştirirken aşağıdakileri göz önünde bulundurun:

- Kullanıcıların kimliğini doğrulamayı veya belirli kullanıcılar için erişimi kısıtlamayı planlıyorsanız, veri hizmetinizin güvenlik gereksinimlerini saptayın. Daha fazla bilgi için bkz. [güvenliği WCF veri Hizmetleri](securing-wcf-data-services.md).

- HTTP inceleme programı, istek ve yanıt iletilerinin içeriğini incelemenizi sağlayarak bir veri hizmetinde hata ayıklarken yararlı olabilir. Veri hizmetine yapılan HTTP isteklerini ve veri hizmetinden alınan yanıtları denetlemek için ham paketleri görüntüleyebilen herhangi bir ağ paketi çözümleyicisi kullanılabilir.

- Veri hizmetinde hata ayıklarken, normal işlem sırasında veri hizmetinden bir hata hakkında daha fazla bilgi edinmek isteyebilirsiniz. <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> ' De <xref:System.Data.Services.DataServiceConfiguration> özelliğini olarak ayarlayarak `true` ve veri hizmeti sınıfındaki <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> <xref:System.ServiceModel.Description.ServiceDebugBehavior> özniteliğinin özelliğini olarak ayarlayarak veri hizmetinden ek hata bilgileri alabilirsiniz. `true` Daha fazla bilgi için bkz. Post [hata ayıklama WCF veri Hizmetleri](https://docs.microsoft.com/archive/blogs/phaniraj/debugging-wcf-data-services). Ayrıca, HTTP mesajlaşma katmanında oluşturulan özel durumları görüntülemek için WCF 'de izlemeyi etkinleştirebilirsiniz. Daha fazla bilgi için bkz. [Izlemeyi yapılandırma](../../wcf/diagnostics/tracing/configuring-tracing.md).

- Bir veri hizmeti genellikle bir ASP.NET uygulama projesi olarak geliştirilir, ancak Visual Studio 'da da bir ASP.NET Web sitesi projesi olarak veri hizmeti oluşturabilirsiniz. İki tür proje arasındaki farklar hakkında daha fazla bilgi için bkz. [Web uygulaması projeleri ve Visual Studio 'Da Web sitesi projelerine karşı](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110)).

- Visual Studio 'da **Yeni öğe Ekle** iletişim kutusunu kullanarak bir veri hizmeti oluşturduğunuzda, VERI hizmeti ııs 'de ASP.NET tarafından barındırılır. ASP.NET ve IIS, bir veri hizmeti için varsayılan ana bilgisayar olduğunda, diğer barındırma seçenekleri de desteklenir. Daha fazla bilgi için bkz. [veri hizmetini barındırma](hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>WCF Veri Hizmetleri dağıt

WCF Veri Hizmeti, veri hizmetini barındıran işlemi seçmede esneklik sağlar. Aşağıdaki platformlara bir veri hizmeti dağıtmak için Visual Studio kullanabilirsiniz:

- **IIS tarafından barındırılan Web sunucusu**

    Bir veri hizmeti bir ASP.NET projesi olarak geliştirildiğinde, standart ASP.NET dağıtım süreçlerini kullanarak bir IIS Web sunucusuna dağıtılabilir. Visual Studio, dağıttığınız veri hizmetini barındıran ASP.NET projesinin türüne bağlı olarak, ASP.NET için aşağıdaki dağıtım teknolojilerini sağlar.

  - **ASP.NET Web uygulamaları için dağıtım teknolojileri**

    - [Nasıl yapılır: Visual Studio 'da Web dağıtım paketi oluşturma](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

    - [Nasıl yapılır: Visual Studio 'da tek tıklamayla yayımlama kullanarak Web projesi dağıtma](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

  - **ASP.NET Web siteleri için dağıtım teknolojileri**

    - [Nasıl yapılır: Web sitesi dosyalarını web sitesi kopyalama aracı ile kopyalama](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

    - [Nasıl yapılır: Web sitelerini yayımlama](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [İzlenecek yol: XCOPY kullanarak ASP.NET Web uygulaması dağıtma](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     Bir ASP.NET uygulamasının dağıtım seçenekleri hakkında daha fazla bilgi için bkz. [Visual Studio ve ASP.net Için Web dağıtımına genel bakış](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110)).

    > [!TIP]
    > Veri hizmetini IIS'ye dağıtmayı denemeden önce, IIS çalıştıran Web sunucusuna dağıtımı test ettiğinizden emin olun. Daha fazla bilgi için bkz. [nasıl yapılır: IIS 'de çalışan BIR WCF veri hizmeti geliştirme](how-to-develop-a-wcf-data-service-running-on-iis.md).

- **Azure**

     [Visual Studio Için Azure Araçları](../../../azure/sdk/vs2015-install.md)'nı kullanarak bir veri hizmetini Azure 'a dağıtabilirsiniz. Azure 'a veri hizmeti dağıtma hakkında daha fazla bilgi için bkz. [Azure 'Da OData hizmeti dağıtma](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="deployment-considerations"></a>Dağıtım Hakkında Önemli Noktalar

Veri hizmetini dağıttığınızda aşağıdakileri göz önünde bulundurun:

- Bir SQL Server veritabanına erişmek için Entity Framework sağlayıcıyı kullanan bir veri hizmetini dağıttığınızda veri yapıları, verileri veya her ikisini de veri hizmeti dağıtımınızla yayabilirsiniz. Visual Studio, bunu hedef veritabanında yapmak için otomatik olarak komut dosyaları (. SQL dosyaları) oluşturabilir ve bu betikler bir ASP.NET uygulamasının Web dağıtım paketine dahil edilebilir. Daha fazla bilgi için bkz. [nasıl yapılır: bir Web uygulaması projesiyle veritabanı dağıtma](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100)). Bir ASP.NET Web sitesi için, Visual Studio 'da **veritabanı Yayımlama Sihirbazı** 'nı kullanarak bunu yapabilirsiniz. Daha fazla bilgi için bkz. [SQL veritabanı yayımlama](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100)).

- WCF Veri Hizmetleri temel bir WCF uygulamasını içerdiğinden, Windows Server 'da çalışan IIS 'e dağıtılan bir veri hizmetini izlemek için Windows Server AppFabric 'i kullanabilirsiniz. Veri hizmetini izlemek üzere Windows Server AppFabric kullanma hakkında daha fazla bilgi için bkz. [Windows Server AppFabric ile post Tracking WCF veri Hizmetleri](https://docs.microsoft.com/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric).

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmeti Barındırma](hosting-the-data-service-wcf-data-services.md)
- [WCF Veri Hizmetlerinin Güvenliğini Sağlama](securing-wcf-data-services.md)
- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
