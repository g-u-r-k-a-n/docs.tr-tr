---
title: Tek yapılı uygulamalar
description: Tek parçalı uygulamalar kapsayıca yönelik temel kavramları anlayın.
ms.date: 01/06/2021
ms.openlocfilehash: a66c76c473c116b303975040d893348182b96713
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970544"
---
# <a name="monolithic-applications"></a>Tek yapılı uygulamalar

Bu senaryoda, tek ve tek parçalı bir Web uygulaması veya hizmeti oluşturuyor ve bir kapsayıcı olarak dağıtayorsunuz. Uygulama içinde, yapı tek parçalı olabilir; çeşitli kitaplıkları, bileşenleri, hatta katmanları (uygulama katmanı, etki alanı katmanı, veri erişim katmanı vb.) içerebilir. Dışarıdan, tek bir işlem, tek bir Web uygulaması veya tek hizmet gibi tek bir kapsayıcıdır.

Bu modeli yönetmek için, uygulamayı temsil etmek üzere tek bir kapsayıcı dağıtırsınız. Ölçeği ölçeklendirmek için, yalnızca bir yük dengeleyiciyi içeren birkaç kopya daha ekleyin. Kolaylık, tek bir kapsayıcıda veya sanal makinede (VM) tek bir dağıtımı yönetmekten gelir.

Bir kapsayıcının yalnızca bir şeyi yaptığı ve tek bir işlemde yaptığı sorumlusu takip eden tek parçalı bir model çakışıyor. Şekil 4-1 ' de gösterildiği gibi, her bir kapsayıcı içinde birden çok bileşen/kitaplık veya iç katman ekleyebilirsiniz.

![Uygulamanın klonlanması yoluyla ölçeklendirilen tek parçalı bir uygulamayı gösteren diyagram.](./media/monolithic-applications/monolithic-application-architecture-example.png)

**Şekil 4-1.** Tek parçalı uygulama mimarisine bir örnek

Tek parçalı bir uygulama, işlevselliğinin tek bir işlem ya da kapsayıcı içinde tamamen veya büyük bir kısmının yanı sıra iç katmanlarda veya kitaplıklarda yer alan bir uygulamadır. Bu yaklaşımın dezavantajı, uygulamanın ne zaman büyüdüğü ve ölçeklendirilmesi gereken durumlarda gelir. Uygulamanın tamamı ölçeklenirse, aslında sorun yoktur. Ancak çoğu durumda, uygulamanın birkaç bölümü ölçeklendirmeyi gerektiren bir sıkıştırma noktalarken diğer bileşenler daha az kullanılır.

Genel e-ticaret örneğini kullanarak, büyük ihtimalle ürün bilgileri bileşenini ölçeklendirmeniz gerekir. Birçok müşteri, ürünleri satın almanızdan daha fazla sayıda müşteriye gözatmasını Daha fazla müşteri, kendi sepetini ödeme işlem hattını kullanmından kullanıyor. Daha az müşteri, yorum ekler veya satın alma geçmişini görüntüler. Ve muhtemelen, tek bir bölgede, içerik ve pazarlama kampanyalarını yönetmesi gereken birkaç çalışanın olması olasıdır. Tek parçalı tasarımı ölçeklendirerek tüm kod birden çok kez dağıtılır.

"Her şeyi ölçeklendirin" sorununa ek olarak, tek bir bileşendeki değişiklikler tüm uygulamanın tam olarak yeniden test edilmesini ve tüm örneklerin tam yeniden dağıtım yapılmasını gerektirir.

Tek parçalı yaklaşım yaygındır ve birçok kuruluş bu mimari yöntemiyle geliştirmektedir. Birçok konuda çok daha fazla sayıda sonuç, diğerleri de sınırlara karşılaşıyor. Bu modelde birçok uygulama tasarlanıyor çünkü araçlar ve altyapı SOAs oluşturmak için çok zordu ve bu, gereksinimi görmedik.

Altyapı açısından, her sunucu aynı ana bilgisayar içinde birçok uygulama çalıştırabilir ve Şekil 4-2 ' de gösterildiği gibi, kaynak kullanımınız için kabul edilebilir bir verimlilik sağlayabilir.

![Ayrı kapsayıcılarda birden çok uygulama içeren bir konağı gösteren diyagram.](./media/monolithic-applications/host-with-multiple-apps-containers.png)

**Şekil 4-2.** Birden çok uygulama/kapsayıcı çalıştıran bir konak

Son olarak, bir kullanılabilirlik perspektifinden, tek parçalı uygulamalar bir bütün olarak dağıtılmalıdır; diğer bir deyişle, *durdurmanız ve başlatmanız* gereken durumlarda, tüm işlevler ve tüm kullanıcılar dağıtım penceresi sırasında etkilenecektir. Bazı durumlarda, Azure ve kapsayıcıları kullanımı bu durumları en aza indirebilir ve Şekil 4-3 ' de görebileceğiniz gibi uygulamanızın kapalı kalma süresini azaltabilir.

Her örnek için adanmış VM 'Ler kullanarak Azure 'da tek parçalı uygulamalar dağıtabilirsiniz. [Azure VM Ölçek kümelerini](/azure/virtual-machine-scale-sets/)kullanarak VM 'leri kolayca ölçeklendirebilirsiniz.

Ayrıca, [Azure Uygulama Hizmetleri](https://azure.microsoft.com/services/app-service/) 'ni kullanarak tek parçalı uygulamalar çalıştırabilir ve VM 'leri yönetmeye gerek kalmadan örnekleri kolayca ölçeklendirebilirsiniz. Azure Uygulama Hizmetleri, tek tek Docker Kapsayıcıları örnekleri çalıştırabilir ve dağıtımı basitleştirir.

Birden çok sanal makineyi Docker konakları olarak dağıtabilir ve sanal makine başına istediğiniz sayıda kapsayıcı çalıştırabilirsiniz. Ardından, Şekil 4-3 ' de gösterildiği gibi bir Azure Load Balancer kullanarak ölçeklendirmeyi yönetebilirsiniz.

![Farklı konaklara ölçeklendirilen tek parçalı bir uygulamayı gösteren diyagram.](./media/monolithic-applications/multiple-hosts-from-single-docker-container.png)

**Şekil 4-3**. Tek bir Docker uygulamasını ölçeklendirerek birden çok ana bilgisayar

Ana bilgisayarların dağıtımını geleneksel dağıtım teknikleri aracılığıyla yönetebilirsiniz.

Ve gibi komutları kullanarak Docker kapsayıcılarını komut satırından yönetebilir `docker run` `docker-compose up` ve ayrıca, sürekli teslım (CD) işlem hatlarında otomatikleştirebilir ve örneğin Azure DevOps Services ' den Docker konaklarına dağıtabilirsiniz.

## <a name="monolithic-application-deployed-as-a-container"></a>Kapsayıcı olarak dağıtılan tek parçalı uygulama

Tek parçalı dağıtımları yönetmek için kapsayıcıları kullanmanın avantajları vardır. Kapsayıcı örneklerinin ölçeklendirilmesi, ek VM 'Leri dağıtmaktan daha hızlı ve daha kolaydır.

Docker görüntüsü olarak güncelleştirmelerin dağıtımı, çok daha hızlı ve daha verimlidir. Docker Kapsayıcıları genellikle Saniyeler içinde başlar, piyasaya çıkarma hızlandırın. Bir Docker kapsayıcısını aşağı doğru çağırmak `docker stop` , genellikle bir saniyeden daha az tamamlanarak komutu çağırmak kadar kolaydır.

Kapsayıcılar doğal olarak sabit olduğundan, Tasarım gereği, bir güncelleştirme betiği diskte kalan belirli bir yapılandırma veya dosya için hesaba izin vermetiğinden, bozuk VM 'Lerde endişelenmeniz gerekmez.

Tek parçalı uygulamalar Docker 'tan faydalanabilir, ancak avantajların yalnızca ipuçlarına dokunuyoruz. Kapsayıcıları yönetmenin büyük avantajları, her bir kapsayıcı örneğinin çeşitli örneklerini ve yaşam döngüsünü yöneten kapsayıcı düzenleyicilerinin dağıtımıyla gelir. Tek parçalı uygulamayı, ölçeklendirilebilir, geliştirilmiş ve dağıtılan alt sistemlere bölmek, mikro hizmetler bölgesine giriş noktanşa noktasıdır.

Kapsayıcılarla tek parçalı uygulamalar modernleştirin ve uygulamalarınızı nasıl kullanabileceğiniz hakkında bilgi edinmek için bu ek Microsoft Kılavuzu, [Azure bulut ve Windows kapsayıcılarıyla modernleştirin var olan .NET uygulamalarını](../../modernize-with-azure-containers/index.md)okuyabilir ve bu sayede PDF olarak da indirebilirsiniz <https://aka.ms/LiftAndShiftWithContainersEbook> .

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a>Azure App Service için tek bir Docker kapsayıcı uygulaması yayımlama

Azure 'a dağıtılan bir kapsayıcının hızlı bir şekilde doğrulanmasını sağlamak istiyorsanız veya uygulama yalnızca tek kapsayıcılı bir uygulama olduğu için Azure Uygulama Hizmetleri ölçeklenebilir tek Kapsayıcılı hizmetler sağlamak için harika bir yol sağlar.

Azure App Service kullanımı sezgisel olur ve kodunuzu almak için harika git tümleştirmesi sağladığından, Microsoft Visual Studio oluşturmak ve doğrudan Azure 'a dağıtmak için hızlı bir şekilde çalışmaya başlamanızı sağlayabilirsiniz. Ancak, geleneksel olarak (Docker olmadan), uygulama hizmetlerinde desteklenmeyen diğer yetenekler, çerçeveler veya bağımlılıklara ihtiyaç duymanız durumunda, Azure ekibi App Service içinde bu bağımlılıkları güncelleştirene veya daha fazla denetime sahip olduğunuz ve uygulamanız için gerekli bir bileşeni veya çerçeveyi yükleyebilen Service Fabric, Cloud Services, hatta düz VM 'Ler gibi diğer hizmetlere geçene kadar beklemeniz gerekir.

Şekil 4-4 ' de gösterildiği gibi, Visual Studio 2019 kullanırken Azure App Service içindeki kapsayıcı desteği, uygulama ortamınıza istediğiniz şeyi dahil etmenizi sağlar. Uygulamanıza bir bağımlılık eklediyseniz, onu bir kapsayıcıda çalıştırdığınız için, bu bağımlılıkları Dockerfile veya Docker yansımanıza dahil etme özelliğini alırsınız.

![Container Registry gösteren App Service oluştur iletişim kutusunun ekran görüntüsü.](./media/monolithic-applications/publish-azure-app-service-container.png)

**Şekil 4-4**. Visual Studio uygulamalarından/kapsayıcılarından Azure App Service bir kapsayıcı yayımlama

Şekil 4-4 Ayrıca, yayımlama akışının bir Container Registry aracılığıyla bir görüntü ileterek, Azure Container Registry (Azure 'daki dağıtımlarınıza yakın ve Azure Active Directory grupları ve hesapları ile güvenliği sağlanmış) ya da Docker Hub veya şirket içi kayıt defterleri gibi başka bir Docker kayıt defteri olabilir.

>[!div class="step-by-step"]
>[Önceki](common-container-design-principles.md) 
> [Sonraki](state-and-data-in-docker-applications.md)
