---
title: Azure bulut ve Windows kapsayıcıları Ile mevcut .NET uygulamalarını modernleştirin
description: Bu e-defterle, mevcut uygulamaları Azure bulutuna ve kapsayıcılara kaldırıp modernleştirin ve bunlarla aynı şekilde geçiş yapmayı öğrenin.
ms.date: 01/07/2021
ms.openlocfilehash: bf6e6dff75c939508947aabeda14955b880f5a89
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025483"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers"></a>Azure bulutu ve Windows Kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme

![Modernleştirin .NET uygulamaları kılavuzu 'nun kapak resmi.](./media/index/web-application-guide-cover-image.png)

**SÜRÜM v 5.0**

Kitap güncelleştirmeleri ve topluluk katkılarına yönelik [changelog](https://aka.ms/modernize-ebook-changelog) 'u inceleyin.

Microsoft Corporation One Microsoft tetetete98052-6399 i

Telif hakkı © 2021 Microsoft Corporation

All rights reserved. Bu kitabın içeriğinin bir kısmı herhangi bir biçimde veya herhangi bir şekilde, yayımcının yazılı izni olmadan çoğaltılamaz.

Bu kitap, Microsoft 'un gibi birden çok kanal aracılığıyla kullanılabilen elektronik kitap (e-kitap) biçiminde ücretsiz olarak kullanılabilir <https://dot.net/architecture> .

Bu kitap ile ilgili sorularınız varsa, adresine e-posta gönderin [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book) .

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır. Diğer tüm işaretler ilgili sahiplerinin mülkiyetindedir.

Yazar:
> **Cesar de La Torre**, SR. PM, .net ürün ekibi, Microsoft Corp.

Katılımcılar ve gözden geçirenler:
> **Scott Hunter**, Iş ortağı Müdürü, .NET ekibi, Microsoft **Paul Yuknewicz**, sorumlu PM Yöneticisi, Visual Studio Araçları ekibi, Microsoft **Lisa Guthrie**, SR. PM, Visual Studio Araçları ekibi, Microsoft **Ankit Asthana**, asıl PM Yöneticisi, .NET ekibi, Microsoft **Unaı Zorrilla**, geliştirici lideri, düz kavramlar **Javier Valero**, KRA solug

## <a name="introduction"></a>Giriş

Web uygulamalarınızı veya hizmetlerinizi modernleştirin ve buluta taşımaya karar verirken uygulamalarınızı tamamen yeniden mimarmaya gerek kalmaz. Mikro hizmetler gibi gelişmiş bir yaklaşım kullanarak bir uygulamayı yeniden tasarlama, maliyet ve zaman depolarından dolayı her zaman bir seçenek değildir. Uygulamanın türüne bağlı olarak, bir uygulamayı yeniden tasarlama de gerekli olmayabilir. Kuruluşunuzun bulut geçiş stratejisinin maliyet verimliliğini iyileştirmek için, işletmenizin ihtiyaçlarını ve uygulamalarınızın gereksinimlerini göz önünde bulundurmanız önemlidir. Şunları belirlemeniz gerekir:

- Hangi uygulamaların bir dönüştürme veya yeniden mimari olması gerekir.

- Hangi uygulamaların yalnızca kısmen modernlanmış olması gerekir.

- Uygulamaları doğrudan buluta "kaldırıp" taşıyabilmeniz için kullanabilirsiniz.

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz, birincil olarak, uygulamanın kodunu ve temel mimarisini önemli ölçüde değiştirmeksizin, bir iş yükünü daha yeni veya daha fazla modern bir ortama taşıma eylemini ifade eden mevcut Microsoft .NET Framework Web veya hizmet odaklı uygulamaların ilk moderniye odaklanmasını sağlar.

Bu kılavuzda ayrıca, Windows kapsayıcıları ve Windows kapsayıcıları destekleme ile ilgili işlem platformları gibi belirli bir yeni teknolojiler ve yaklaşımlar kullanarak uygulamalarınızı buluta taşıma ve uygulamaları kısmen modernme avantajları vurgulanmıştır.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Mevcut .NET uygulamaları için bulut yolu

Kuruluşlar, genellikle uygulamalarına yönelik çeviklerinin ve hızlı bir şekilde buluta taşımayı seçer. Bulutta, genellikle şirket içi sunucuları ayarlamak için gereken haftalarla karşılaştırıldığında, birkaç dakika içinde bulutta binlerce sunucu (VM) ayarlayabilirsiniz.

Uygulamaları buluta geçirmek için tek, tek boyutlu bir-uygun olmayan bir strateji yoktur. Sizin için doğru geçiş stratejisi, kuruluşunuzun ihtiyaçlarına ve önceliklerine ve geçirdiğiniz uygulamaların türüne bağlıdır. Tüm uygulamalar hizmet olarak platform ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) modeline geçme veya [bulut Yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) uygulama modeli geliştirme yatırımını garanti etmez. Birçok durumda, iş gereksinimlerinize göre varlıklarınızı buluta taşımaya yönelik aşamalı veya artımlı bir yaklaşım alabilirsiniz.

Kuruluşun en iyi uzun süreli çevikliği ve değeri olan modern uygulamalarda, *bulut Yerel* uygulama mimarilerinde yatırım yapmanız yararlı olabilirsiniz. Bununla birlikte, mevcut veya eski varlıklar olan uygulamalarda, önemli avantajlar elde etmek için anahtar en az zaman ve para (yeniden mimari veya kod değişikliği olmadan) harcaymaktır.

Şekil 1-1 ' de, mevcut .NET uygulamalarını artımlı aşamalarda buluta taşıdığınızda gerçekleştirebileceğiniz olası yollar gösterilmektedir.

 ![Mevcut .NET uygulamaları ve hizmetleri için modernleştirme yolları](./media/image1-1.png)

**Şekil 1-1**. Mevcut .NET uygulamaları ve hizmetleri için modernleştirme yolları

Her geçiş yaklaşımının kullanılmasına yönelik farklı avantajları ve nedenleri vardır. Uygulamaları buluta geçirdiğinizde tek bir yaklaşım seçebilirsiniz veya birden fazla yaklaşımdan belirli bileşenleri seçebilirsiniz. Bireysel uygulamalar tek bir yaklaşım veya vade durumuyla sınırlı değildir. Örneğin, yaygın bir karma yaklaşım belirli şirket içi bileşenlere ve buluttaki diğer bileşenlere sahip olabilir.

Her bir uygulama için tanım ve kısa açıklama aşağıdaki gibi verilmiştir:

**Düzey 1: bulut altyapısına** yönelik uygulamalar: Bu geçiş yaklaşımında, mevcut şirket içi uygulamalarınızı bir hizmet olarak altyapı ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)) platformuna geçirin veya yeniden barındırabilirsiniz. Uygulamalarınız daha önce olduğu gibi neredeyse aynı birleşimde sahiptir, ancak artık bunları buluttaki VM 'lere dağıtırsınız.
Bu basit geçiş türü genellikle sektörde "Yükselt & SHIFT" olarak bilinir.

**Düzey 2: buluta iyileştirilmiş** uygulamalar: Bu düzeyde, ancak önemli bir kodu yeniden tasarlamadan veya değiştirmeden, uygulamanızı bulutta çalıştırmanın yanı sıra kapsayıcılar gibi modern teknolojiler ve bulut tarafından yönetilen ek hizmetler de elde edebilirsiniz. Kuruluşunuzun geliştirme işlemleri (DevOps) işlemlerinizi iyileştirerek uygulamalarınızın daha hızlı gönderim çevikliğini artırırsınız. Docker altyapısını temel alan Windows kapsayıcıları gibi teknolojileri kullanarak bu işlevselliği elde edersiniz. Kapsayıcılar, birden çok aşamada dağıtırken uygulama bağımlılıklarından kaynaklanan uçuşmayı kaldırır. Bu vade modelinde, veritabanları, hizmet olarak önbellek, izleme ve sürekli tümleştirme/sürekli dağıtım (CI/CD) işlem hatları ile ilgili ek Bulut Yönetimli hizmetler kullanırken IaaS veya PaaS üzerinde kapsayıcılar dağıtabilirsiniz.

Üçüncü vade düzeyi buluttaki son hedeftir, ancak bu kılavuzun ana odağa değil birçok uygulama için isteğe bağlıdır:

**3. düzey: bulutta yerel** uygulamalar: Bu geçiş yaklaşımı genellikle iş gereksinimiyle ve görev açısından kritik uygulamalarınızın modernleştirilmesi için gereklidir. Bu düzeyde, uygulamalarınızı PaaS bilgi işlem platformlarına taşımak için PaaS hizmetlerini kullanırsınız. [Bulut Yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) uygulamaları ve mikro hizmet mimarisini, uzun süreli çeviklerle uygulamaları geliştirmek ve yeni sınırlara ölçeklendirmek için uygulanıyor. Bu tür bir modernleştirme genellikle bulut için özel olarak mimari gerektirir. Özellikle bulutta yerel uygulamaya ve mikro hizmet tabanlı modellere geçtiğinizde, yeni kod genellikle yazılmalıdır. Bu yaklaşım, tek parçalı ve şirket içi uygulama ortamınıza ulaşmak zor olan avantajlar elde etmenize yardımcı olabilir.

Tablo 1-1 ' nin başlıca avantajları ve her bir geçişi ya da modernleştirme yaklaşımını belirleme nedenleri açıklanmaktadır.

| **Bulut altyapısına hazırlanma** <br /> *Lift and shift* | **Buluta Iyileştirilmiş** <br /> *Modernleştirin* | **Bulutta yerel** <br /> *Modernleştirin, remimar ve yeniden yazma* |
|---|---|---|
| **Uygulamanın işlem hedefi** |
| Azure 'da VM 'lere dağıtılan uygulamalar | Azure App Service, Azure Container Instance (ACI), Kapsayıcılı VM 'Ler veya AKS (Azure Kubernetes hizmeti) için dağıtılan tek parçalı veya N katmanlı uygulamalar | Azure Işlevleri 'ni temel alan Azure Kubernetes Service (AKS) ve/veya sunucusuz mikro hizmetler üzerinde Kapsayıcılı mikro hizmetler. |
| **Veri hedefi** |
| Bir VM 'deki SQL veya herhangi bir ilişkisel veritabanı | Azure SQL veritabanı yönetilen örneği veya buluttaki başka bir yönetilen veritabanı. | Azure SQL veritabanı, Azure Cosmos DB veya buluttaki başka bir yönetilen veritabanını temel alan, mikro hizmet başına fined-gren veritabanları |
| **Avantajlar**|
| <li>Yeniden mimari yok, yeni kod yok <li> Hızlı geçiş için en az çaba <li> En az-Azure 'da desteklenen ortak payda <li> Temel kullanılabilirlik garantisi <li> Buluta taşıdıktan sonra daha modernleştirin daha da kolay | <li> Yeniden mimari yok <li> Minimum kod/yapılandırma değişiklikleri <li> Kapsayıcılar nedeniyle yayın için geliştirilmiş dağıtım ve DevOps çevikliği <li> Daha fazla yoğunluk ve daha düşük dağıtım maliyetleri <li> Uygulama ve bağımlılıkların taşınabilirliği <li> Konak hedeflerinin esnekliği: PaaS yaklaşımları veya IaaS | <li> Bulut mimarı, buluttan en iyi avantajları elde edersiniz, ancak yeni kod gerekiyor <li> Mikro hizmetler bulutu-yerel yaklaşımları <li> Modern görev açısından kritik uygulamalar, bulut açısından dayanıklı hiper ölçeklenebilir <li> Tam olarak yönetilen hizmetler <li> Ölçek için iyileştirildi <li> Alt sistem tarafından otonom çeviklik için iyileştirildi <li> Dağıtım ve DevOps üzerine inşa |
| **Zorluklar** |
| <li> İşletim giderleri veya kapanış veri merkezleri dışında daha küçük bir bulut değeri <li> Çok az yönetiliyor: işletim sistemi veya ara yazılım düzeltme eki uygulama; Terrayform, Spinnaker veya Pupevcil hayvan gibi altyapı çözümlerini kullanabilir | <li> Kapsayıcı, geliştiriciler ve BT Işlemleri için öğrenme eğrisinin ek bir adımdır <li> DevOps ve CI/CD işlem hatları bu yaklaşım için genellikle ' a gerekir '. Şu anda kuruluşun kültürüyle yoksa, ek bir zorluk olabilir| <li> Bulutta yerel uygulamalar ve mikro hizmet mimarileri için yeniden mimari gerektirir ve genellikle modernize (artan zaman ve bütçe) göre önemli kod yeniden düzenleme veya yeniden yazma gerektirir|
> **Tablo 1-1.** Mevcut .NET uygulamaları ve hizmetleri için modernleştirme yollarının avantajları ve güçlükleri

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Vade düzeyine göre anahtar teknolojileri ve mimarileri

.NET Framework uygulamalar başlangıçta, geç 2001 ' de yayınlanan .NET Framework sürüm 1,0 ile başlatılır. Daha sonra, şirketler yeni sürümlere (2,0, 3,5 ve .NET Framework 4. x) taşınır. Bu uygulamaların çoğu Windows Server ve Internet Information Server (IIS) üzerinde çalışır ve SQL Server, Oracle, MySQL veya diğer RDBMS gibi ilişkisel bir veritabanı kullanır.

Birçok mevcut .NET uygulaması günümüzde .NET Framework 4. x veya hatta .NET Framework 3,5 ' i temel alabilir ve ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API 'SI, Windows Communication Foundation (WCF), ASP.NET SignalR ve ASP.NET Web sayfaları gibi Web çerçeveleri kullanabilirsiniz. Bu .NET Framework teknolojiler Windows 'a bağımlıdır. Bu bağımlılık, yalnızca eski uygulamaları geçiriyorsanız ve uygulama altyapınızda minimum değişiklikler yapmak istiyorsanız göz önünde bulundurmanız önemlidir.

Şekil 1-2, üç bulut vade düzeyinin her birinde kullanılan birincil teknolojileri ve mimari stillerini gösterir:

![Mevcut .NET Web uygulamalarını modernize etmek için her bir vade düzeyi için birincil teknolojiler](./media/image1-2.png)

**Şekil 1-2.** Mevcut .NET Web uygulamalarını modernize etmek için her bir vade düzeyi için birincil teknolojiler

Şekil 1-2, en yaygın senaryoları vurgular, ancak mimariye geldiğinde birçok karma ve karışık değişim mümkündür. Örneğin, vade modeller yalnızca mevcut Web uygulamalarındaki tek parçalı mimarilere değil, aynı zamanda hizmet yönü, N katmanı ve diğer mimari stili çeşitlemelerini da uygular. Bir veya başka bir mimari türü ve ilgili teknolojilerin üzerindeki daha yüksek odak veya yüzde, uygulamalarınızın genel vade düzeyini belirler.

Modernleştirme işlemindeki her bir vade düzeyi aşağıdaki anahtar teknolojileriyle ve yaklaşımlar ile ilişkilendirilir:

- **Bulut altyapısına Ready** (yeniden barındırma veya temel kaldırma & SHIFT): ilk bir adım olarak, birçok kuruluş yalnızca bir bulut geçişi stratejisini hızla yürütmek istiyor. Bu durumda, uygulamalar yeniden barındırılır. En iyi şekilde barındırma, [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) ve [Azure veritabanı geçiş hizmeti](https://azure.microsoft.com/campaigns/database-migration/)gibi bulut araçlarına dayalı olarak Azure 'a geçiş yaparken size yardımcı olmak için gereken yönergeler, Öngörüler ve mekanizmaları sağlayan [Azure geçişi](https://aka.ms/azuremigrate)kullanılarak otomatikleştirilebilir. Ayrıca, eski uygulamaları buluta taşırken varlıklarınızla ilgili altyapı ayrıntılarını öğrenmenize olanak sağlamak için el ile yeniden barındırma ayarlayabilirsiniz. Örneğin, uygulamalarınızı Azure 'daki VM 'lere, büyük olasılıkla yalnızca küçük yapılandırma değişiklikleriyle taşıyabilirsiniz. Bu durumda ağ, özellikle Azure 'da sanal ağlar oluşturursanız, şirket içi bir ortama benzer.

- **Buluta iyileştirilmiş** (yönetilen hizmetler ve Windows kapsayıcıları): Bu model, uygulamanın çekirdek mimarisini değiştirmeden, buluttan bazı önemli avantajlar kazanmak için birkaç önemli dağıtım iyileştirmesi yapmayı sağlar. Buradaki temel adım, mevcut .NET Framework uygulamalarınıza [Windows kapsayıcıları](/virtualization/windowscontainers/about/) desteği eklemektir. Bu önemli adım (kapsayıcılama) koda dokunmasını gerektirmez, bu nedenle, genel kaldırma ve kaydırma çabasının açık olması gerekir. [Image2Docker](https://github.com/docker/communitytools-image2docker-win) veya Visual Studio gibi araçları [Docker](https://www.docker.com/)araçları ile birlikte kullanabilirsiniz. Visual Studio, ASP.NET uygulamaları ve Windows kapsayıcıları görüntüleri için otomatik olarak akıllı varsayılanlar seçer. Bu araçlar bir hızlı iç döngü ve kapsayıcıları Azure 'a almak için hızlı bir yol sunar. Birden çok ortama dağıtırken çevikliği geliştirilmiştir.
Ardından, üretime geçiş yapmak için Windows Kapsayıcılarınızı [azure kapsayıcılar için Web App](https://azure.microsoft.com/services/app-service/containers/), [Azure Container Instances (aci)](https://azure.microsoft.com/services/container-instances/)ve Azure VM 'Lerine ve bir IaaS yaklaşımını tercih ediyorsanız Windows Server 2016 ve kapsayıcılarına dağıtabilirsiniz. Daha karmaşık çok Kapsayıcılı uygulamalar için [Azure Kubernetes hizmeti (AKS/ACS)](https://azure.microsoft.com/services/container-service/)gibi düzenleyicilerinin kullanımını göz önünde bulundurun.

Bu ilk modernleştirme sırasında, buluttan [Azure Application Insights](/azure/application-insights/app-insights-overview)gibi araçlarla izleme gibi varlıklar da ekleyebilirsiniz; [Azure DevOps Services](https://azure.microsoft.com/services/devops/); uygulama yaşam DÖNGÜLERINIZIN CI/CD işlem hatları ve Azure 'da kullanılabilen pek çok daha fazla veri kaynağı hizmeti. Örneğin, başlangıçta geleneksel [ASP.NET Web Forms](https://www.asp.net/web-forms) veya [ASP.NET MVC](https://www.asp.net/mvc)kullanılarak geliştirilmiş tek parçalı bir Web uygulamasını değiştirebilir, ancak şimdi Windows kapsayıcıları kullanarak dağıtırsınız. Windows kapsayıcıları kullandığınızda, uygulamanızın çekirdek mimarisini değiştirmeden verilerinizi [Azure SQL veritabanı yönetilen örneği](/azure/sql-database/)' nde bir veritabanına geçirmeniz gerekir.

- **Bulutta yerel**: sunulan farklı mikro Hizmetlerde çalışan birden fazla bağımsız geliştirme ekiple büyük ve karmaşık uygulamaları hedeflerken, [bulutta yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) uygulamalarda mimari oluşturma hakkında düşünmeniz gerekir. olarak çalışabilen. Ayrıca, mikro hizmet başına granleştirilmiş ve bağımsız ölçeklenebilirlik nedeniyle. Bu mimari yaklaşımlar, çok önemli zorluk ve karmaşıklıklarla, ancak [Azure Kubernetes hizmeti (AKS/ACS)](https://azure.microsoft.com/services/container-service/) (yönetilen Kubernetes) gibi bulut PaaS ve düzenleme işlemleri ile sunucusuz bir yaklaşım Için [Azure işlevleri](https://azure.microsoft.com/services/functions/) kullanılarak önemli ölçüde basitleştirilebilir. Tüm bu yaklaşımlar (mikro hizmetler ve sunucusuz gibi) genellikle bulut için mimarunuzu ve yeni kod yazmanızı, belirli PaaS platformlarına uyarlanan kodu veya mikro hizmetler gibi belirli mimarilere göre uygulanan kodu ister.

Şekil 1-3 her bir vade düzeyi için kullanabileceğiniz iç teknolojileri gösterir:

![Her bir modernleştirme vade düzeyi için iç teknolojiler](./media/image1-3.png)

**Şekil 1-3.** Her bir modernleştirme vade düzeyi için iç teknolojiler

## <a name="lift-and-shift-scenario"></a>Asansör ve kaydırma senaryosu

Yükseltme ve kaydırma geçişleri için uygulama senaryolarınızda birçok farklı yükseltme ve kaydırma çeşitlemelerini kullanabileceğiniz göz önünde bulundurun. Uygulamanızı yalnızca yeniden barındırıyorsanız, Şekil 1-4 ' de gösterildiği gibi bir senaryoya sahip olabilirsiniz; burada, bulutta VM 'Leri yalnızca uygulamanız ve veritabanı sunucunuz için kullanırsınız.

![Bulutta saf IaaS senaryosu örneği](./media/image1-4.png)

**Şekil 1-4**. Bulutta saf IaaS senaryosu örneği

## <a name="modernization-scenarios"></a>Modernleştirme senaryoları

Modernleştirme senaryolarında yalnızca söz konusu vade düzeyindeki öğeleri kullanan bir saf Cloud-Optimized uygulamasına sahip olabilirsiniz. Veya şekil 1-5 ' de olduğu gibi, bulut Infrastructure-Ready ve diğer Cloud-Optimized öğelerden ("seçim ve seçim" veya karma model) bazı öğelere sahip bir ara durum uygulamanız olabilir.

!["Seçme ve seçme" senaryosu, IaaS, DevOps ve kapsayıcılama varlıkları üzerinde veritabanıyla birlikte](./media/image1-5.png)

**Şekil 1-5.** "Seçme ve seçme" senaryosu, IaaS, DevOps ve kapsayıcılama varlıkları üzerinde veritabanıyla birlikte

Daha sonra, çok sayıda mevcut .NET Framework uygulamasının geçirilmesi için ideal senaryo olarak, küçük çalışmalardan önemli avantajlar elde etmek için bir Cloud-Optimized uygulamasına geçiş yapabilirsiniz. Bu yaklaşım ayrıca, olası gelecek bir evrimi olarak Cloud-Native için de ayar yapar. Şekil 1-6 bir örnek gösterir.

![Windows kapsayıcıları ve yönetilen hizmetlerle örnek Cloud-Optimized uygulamalar senaryosu](./media/image1-6.png)

**Şekil 1-6.** Windows kapsayıcıları ve yönetilen hizmetlerle örnek Cloud-Optimized uygulamalar senaryosu

Daha da fazla, belirli senaryolar için birkaç mikro hizmet ekleyerek mevcut Cloud-Optimized uygulamanızı genişletebilirsiniz. Bu yaklaşım, sizi, mevcut yönergelerin ana odağı olmayan Cloud-Native modeli düzeyine taşır.

## <a name="what-this-guide-does-not-cover"></a>Bu kılavuzun kapsamayan

Bu kılavuz, Şekil 1-7 ' de gösterildiği gibi örnek senaryoların belirli bir alt kümesini içerir. Bu kılavuz yalnızca, kaldırma ve kaydırma senaryolarına ve son olarak Cloud-Optimized modeline odaklanır. Cloud-Optimized modelinde, bir .NET Framework uygulama Windows kapsayıcıları ve izleme ve CI/CD işlem hatları gibi ek bileşenler kullanılarak modernlanmış olur. Her bileşen, buluta, daha hızlı ve çeviklik ile uygulama dağıtmaya yönelik temel uygulamalardır.

![Cloud-Native bu kılavuzda Kapsanmadı](./media/image1-7.png)

**Şekil 1-7.** Cloud-Native bu kılavuzda Kapsanmadı

Bu kılavuzun odağı özeldir. Bu, mevcut .NET uygulamalarınızın, yeniden mimari ve kod değişikliği olmadan bir yükseltme ve kaydırma işlemlerini gerçekleştirmek için uygulayabileceğiniz yolu gösterir. Son olarak, uygulamanızı nasıl Iyileştirecağınızı gösterir.

Bu kılavuzda, mikro hizmetler mimarisine nasıl geliştikçe gibi Cloud-Native uygulamaları nasıl oluşturacağınız gösterilmez. Uygulamalarınızı yeniden mimaride veya mikro hizmetleri temel alan yepyeni uygulamalar oluşturmak için, bkz. e-book [.net mikro hizmetleri: Kapsayıcılı .NET uygulamaları Için mimari](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Ek kaynaklar

- **Microsoft platformu ve araçları Ile Kapsayıcılı Docker uygulaması yaşam döngüsü** (indirilebilir e-kitap) \
  <https://aka.ms/dockerlifecycleebook>

- **.Net mikro hizmetleri: Kapsayıcılı .NET uygulamaları Için mimari** (indirilebilir e-kitap) \
  <https://aka.ms/microservicesebook>

- **ASP.NET Core ve Azure ile modern web uygulamaları tasarlama** (indirilebilir e-kitap) \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalıdır?

Bu kılavuz, uygulamaları teslim etme ve serbest bırakma çevikliği için .NET Framework tabanlı mevcut ASP.NET Web uygulamalarını veya WCF hizmetlerini modernleştirin etmek isteyen geliştiriciler ve çözüm mimarları için yazılmıştır.

Ayrıca, bir kuruluş mimarı veya Windows kapsayıcıları kullanarak alabileceğiniz avantajlara genel bakış isteyen bir geliştirme lideri/müdürü gibi teknik bir karar veren ve Microsoft Azure kullanırken buluta dağıtarak bu kılavuzu yararlı bulabilirsiniz.

## <a name="how-to-use-this-guide"></a>Bu kılavuz nasıl kullanılır?

Bu kılavuzda, "Neden", mevcut uygulamalarınızı nasıl modernleştirin isteyebileceğiniz ve uygulamalarınızı buluta taşırken Windows kapsayıcıları kullanarak aldığınız belirli avantajlar ele alınmaktadır. Kılavuzun ilk birkaç bölümünde yer alan içerik, genel bakış isteyen mimarlara ve teknik karar mekanizmalarının yanı sıra uygulama ve teknik, adım adım ayrıntılara odaklanmayı gerektirmeyen bir tasarıma yöneliktir.

Bu kılavuzun son bölümü, belirli dağıtım senaryolarına odaklanabilecek birden çok izlenecek yolu tanıtır. Bu kılavuz, senaryoları özetlemek ve avantajlarını vurgulamak için izlenecek yolların daha kısa sürümlerini sunar. Tam izlenecek yollar kurulum ve uygulama ayrıntılarının detayına gidebilir ve ilgili örnek uygulamaların bulunduğu genel [GitHub](https://github.com/dotnet-architecture/eShopModernizing) deposunda bir [wiki gönderisi](https://github.com/dotnet-architecture/eShopModernizing/wiki) kümesi olarak yayımlanır (bir sonraki bölümde ele alınmıştır). GitHub 'daki son bölüm ve adım adım wiki talimatları, uygulama ayrıntılarına odaklanmak isteyen geliştiricilerle ve mimarilerden daha ilgi çekici olacaktır.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Eski uygulamaları modernize yönelik örnek uygulamalar: Eshopmodernize

GitHub 'daki [Eshopmodernize](https://github.com/dotnet-architecture/eShopModernizing) deposu, eski monoparçalı Web uygulamalarına benzetilen iki örnek uygulama sunmaktadır. Bir Web uygulaması ASP.NET MVC kullanılarak geliştirilmiştir; ikinci Web uygulaması, ASP.NET Web Forms kullanılarak geliştirilmiştir ve üçüncü uygulama, bir WCF hizmeti arka ucu kullanan bir WinForms istemci masaüstü uygulaması olan N katmanlı bir uygulamadır. Tüm bu uygulamalar geleneksel .NET Framework dayanır. Bu örnek uygulamalar, .NET Core veya .NET 5,0 veya ASP.NET Core, mevcut/eski .NET Framework uygulamaların modernlanmış olmaları gerektiği için kullanmaz.

Bu örnek uygulamalar, modernlanmış kod ile ikinci bir sürüme sahiptir ve bunlar oldukça basittir. Uygulama sürümleri arasındaki en önemli fark, ikinci sürümlerin dağıtım seçimi olarak Windows kapsayıcıları kullanmanızdır. Ayrıca, örneğin, görüntüleri yönetmek için Azure depolama Blobları, güvenlik yönetimi için Azure Active Directory ve uygulamaları izlemek ve denetlemek için Azure Application Insights gibi ikinci sürümlere yönelik birkaç ekleme vardır.

## <a name="send-your-feedback"></a>Geri bildiriminizi gönderin

Bu kılavuz, mevcut .NET Web uygulamalarını geliştirme ve Moderasyonu için seçeneklerinizi anlamanıza yardımcı olmak üzere yazılmıştır. Kılavuz ve ilgili örnek uygulamalar gelişiyor. Geri bildiriminiz bizim için çok önemlidir! Bu kılavuzun nasıl daha yararlı olabileceği hakkında açıklamalarınız varsa, lütfen ' e gönderin [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book) .

>[!div class="step-by-step"]
>[Sonraki](lift-and-shift-existing-apps-azure-iaas.md) <!-- Next Chapter -->
