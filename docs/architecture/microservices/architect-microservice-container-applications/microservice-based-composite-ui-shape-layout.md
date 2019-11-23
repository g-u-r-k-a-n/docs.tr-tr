---
title: Mikro hizmetlere dayalı bileşik UI oluşturma
description: Mikro hizmetler mimarisi yalnızca arka uç için değil. Ön uçta kullanmak için bir göz atma görünümü alın.
ms.date: 09/20/2018
ms.openlocfilehash: 1861d3bb6e5d4a0226aa8f3f72a2e0d3e83be56f
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275734"
---
# <a name="creating-composite-ui-based-on-microservices"></a>Mikro hizmetlere dayalı bileşik UI oluşturma

Mikro hizmetler mimarisi genellikle sunucu tarafı işleme verileriyle ve mantığıyla başlar, ancak çoğu durumda Kullanıcı arabirimi hala tek bir şekilde ele alınır. Ancak, [mikro ön uçlar](https://martinfowler.com/articles/micro-frontends.html)adlı daha gelişmiş bir yaklaşım da mikro hizmetlere göre uygulama kullanıcı arabirimini tasarlayamalıdır. Bu, sunucu üzerinde mikro hizmetler ve mikro hizmetleri kullanan tek parçalı bir istemci uygulaması yerine mikro hizmetler tarafından oluşturulan bileşik bir kullanıcı arabirimine sahip olma anlamına gelir. Bu yaklaşımda, oluşturduğunuz mikro hizmetler hem Logic hem de görsel gösterimiyle tamamlanabilir.

Şekil 4-20, tek parçalı bir istemci uygulamasından yalnızca mikro hizmetlerin tüketen daha basit bir yaklaşım gösterir. Kuşkusuz, HTML ve JavaScript üreten bir ASP.NET MVC hizmetine sahip olabilirsiniz. Bu şekilde, mikro hizmetleri kullanan tek bir (tek parçalı) istemci kullanıcı arabirimine sahip olduğunuz ve Kullanıcı arabirimi şeklinin (HTML ve JavaScript) değil Logic ve verilere odaklandığınız bir basitlik basitleştirılmıştır.

![Mikro hizmetlere bağlanan bir tek parçalı kullanıcı arabirimi uygulamasının diyagramı.](./media/microservice-based-composite-ui-shape-layout/monolith-ui-consume-microservices.png)

**Şekil 4-20**. Arka uç mikro hizmetlerini kullanan tek parçalı bir kullanıcı arabirimi uygulaması

Buna karşılık, karma bir kullanıcı arabirimi tam olarak oluşturulur ve mikro hizmetler tarafından oluşturulur. Mikro hizmetlerden bazıları, Kullanıcı arabiriminin belirli alanlarının görsel şeklini barındırır. Temel fark, şablonları temel alan istemci kullanıcı arabirimi bileşenleri (örneğin TypeScript sınıfları) ve bu şablonlar için veri şekillendirme-UI ViewModel her mikro hizmetten gelir.

İstemci uygulaması Başlangıç zamanında istemci kullanıcı arabirimi bileşenleri (örneğin, TypeScript sınıfları), belirli bir senaryo için ViewModel sağlayabilen bir altyapı mikro hizmeti ile kendisini kaydeder. Mikro hizmet şekli değiştirirse, Kullanıcı arabirimi de değişir.

Şekil 4-21, bu bileşik UI yaklaşımının bir sürümünü gösterir. Bu basitleştirilerek, farklı tekniklerin temel alınarak parçalı parçalar oluşturan başka mikro hizmetlerden sahip olabilirsiniz. Bu, geleneksel bir Web yaklaşımı (ASP.NET MVC) veya SPA (tek sayfalı uygulama) oluşturmaya göre değişir.

![Birçok görünüm modelinden oluşan bileşik bir kullanıcı arabirimi diyagramı.](./media/microservice-based-composite-ui-shape-layout/microservice-generate-composite-ui.png)

**Şekil 4-21**. Arka uç mikro hizmetleri tarafından şekillendirilmiş bir bileşik UI uygulaması örneği

Bu UI Composition mikro hizmetlerinin her biri, küçük bir API ağ geçidine benzer. Ancak bu durumda, her biri küçük bir kullanıcı arabirimi alanından sorumludur.

Mikro hizmetler tarafından yönetilen bileşik bir kullanıcı arabirimi yaklaşımı, kullanmakta olduğunuz UI teknolojilerine bağlı olarak daha zor veya daha az olabilir. Örneğin, bir SPA veya yerel mobil uygulama oluşturmak için kullandığınız geleneksel bir Web uygulaması oluşturmak için aynı teknikleri kullanamazsınız (Bu yaklaşım için daha zor olabilecek Xamarin uygulamaları geliştirilirken olduğu gibi).

[Eshoponcontainers](https://aka.ms/MicroservicesArchitecture) örnek uygulaması, birden çok nedenden dolayı tek parçalı kullanıcı arabirimi yaklaşımını kullanır. İlk olarak, mikro hizmetler ve kapsayıcılar için bir giriş niteliğindedir. Bileşik bir kullanıcı arabirimi daha gelişmiş olmakla kalmaz, Kullanıcı arabirimini tasarlarken ve geliştirirken de daha fazla karmaşıklık gerektirir. İkinci olarak, eShopOnContainers, Xamarin 'e dayalı yerel bir mobil uygulama de sağlar ve bu da istemci C\# tarafında daha karmaşık hale gelir.

Ancak, mikro hizmetlere dayalı bileşik UI hakkında daha fazla bilgi edinmek için aşağıdaki başvuruları kullanmanız önerilir.

## <a name="additional-resources"></a>Ek kaynaklar

- **Mikro ön uçlar (Marwler 'in blogu)**  
  <https://martinfowler.com/articles/micro-frontends.html>
  
- **Mikro ön uçlar (Michael geers sitesi)**  
  <https://micro-frontends.org/>
  
- **ASP.NET kullanarak bileşik Kullanıcı arabirimi (belirli bir Atölyesi)**  
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- **Ruben Oostinga. Mikro hizmetler mimarisinde tek parçalı ön uç**  
  <https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/>

- **Mauro Servienti. Daha iyi kullanıcı arabirimi kompozisyonunun gizli dizisi**  
  <https://particular.net/blog/secret-of-better-ui-composition>

- **Viktor Farcic. Ön uç Web bileşenlerini mikro hizmetlere ekleme**  
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- **Mikro hizmet mimarisinde ön uç yönetimi**  
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
>[Önceki](microservices-addressability-service-registry.md)
>[İleri](resilient-high-availability-microservices.md)
