---
title: Hangi .NET sürümünün kullanılacağını seçin
description: .NET 'in programınızın çalışma zamanı sürümlerini otomatik olarak bulmasını ve tercih etme hakkında bilgi edinin. Ayrıca, bu makalede belirli bir sürümün nasıl zorlanacağı öğretilir.
author: adegeo
ms.author: adegeo
ms.date: 02/05/2021
ms.openlocfilehash: 2fe30041cbf85de644d9ba17330884961fcf7504
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792004"
---
# <a name="select-the-net-version-to-use"></a>Kullanılacak .NET sürümünü seçin

Bu makalede, sürümleri seçmek için .NET araçları, SDK ve çalışma zamanı tarafından kullanılan ilkeler açıklanmaktadır. Bu ilkeler, belirtilen sürümleri kullanarak çalışan uygulamalar arasında bir denge sağlar ve hem geliştirici hem de Son Kullanıcı makinelerini yükseltme kolaylığını etkinleştirir. Bu ilkeler aşağıdaki eylemleri gerçekleştirir:

- Güvenlik ve güvenilirlik güncelleştirmeleri dahil olmak üzere kolay ve verimli .NET dağıtımı.
- Hedef çalışma zamanından bağımsız olarak en son araçları ve komutları kullanın.

Sürüm seçimi meydana gelir:

- SDK komutunu çalıştırdığınızda, [SDK en son yüklenen sürümü kullanır](#the-sdk-uses-the-latest-installed-version).
- Bir derleme oluşturduğunuzda, [hedef çerçeve takma adları derleme süresi API 'lerini tanımlar](#target-framework-monikers-define-build-time-apis).
- Bir .NET uygulaması çalıştırdığınızda, [hedef Framework bağımlı uygulamalar ileri sarma](#framework-dependent-apps-roll-forward).
- Kendi içinde olan bir uygulamayı yayımladığınızda, [kendi içinde kapsanan dağıtımlar seçili çalışma zamanını içerir](#self-contained-deployments-include-the-selected-runtime).

Bu belgenin geri kalanında bu dört senaryo incededir.

## <a name="the-sdk-uses-the-latest-installed-version"></a>SDK en son yüklü sürümü kullanıyor

SDK komutları `dotnet new` ve içerir `dotnet run` . .NET CLı her komut için bir SDK sürümü seçmelidir `dotnet` . Şu durumlarda bile varsayılan olarak makinede yüklü olan en son SDK 'yi kullanır:

- Proje .NET çalışma zamanının önceki bir sürümünü hedefler.
- .NET SDK 'sının en son sürümü bir önizleme sürümüdür.

Önceki .NET çalışma zamanı sürümlerini hedeflerken en son SDK özelliklerinden ve geliştirmelerinden yararlanabilirsiniz. Tüm projeler için aynı SDK araçlarını kullanarak .NET 'in birden fazla çalışma zamanı sürümünü farklı projelerde hedefleyebilirsiniz.

Nadir durumlarda, SDK 'nın önceki bir sürümünü kullanmanız gerekebilir. Bu sürümü dosyadaki bir [ *global.js*](../tools/global-json.md)belirlersiniz. "En son kullanım" ilkesi, en son yüklenen sürümden önceki bir .NET SDK sürümünü belirtmek için yalnızca *global.js* kullanacağınızı gösterir.

*global.js* , dosya hiyerarşisinde herhangi bir yere yerleştirilebilir. CLı, bulduğu ilk *global.js* için proje dizininden yukarı doğru arama yapar. Belirli bir *global.js* hangi projelerin dosya sistemindeki yerine uygulanacağını kontrol edersiniz. .NET CLı, yolda geçerli çalışma dizininden yukarı doğru gezinerek bir *global.js* dosya arar. Bulunan dosyadaki ilk *global.js* kullanılan sürümü belirtiyor. Bu SDK sürümü yüklüyse, bu sürüm kullanılır. *global.js* belirtilen SDK bulunamazsa, .net CLI uyumlu bir SDK seçmek için [eşleşen kuralları](../tools/global-json.md#matching-rules) kullanır veya Hiçbiri bulunmazsa başarısız olur.

Aşağıdaki örnek sözdiziminde *global.js* gösterir:

``` json
{
  "sdk": {
    "version": "3.0.0"
  }
}
```

SDK sürümü seçme işlemi şu şekilde yapılır:

1. `dotnet` dosyada yinelenen bir *global.js* arar ve yolun geçerli çalışma dizininden yukarı doğru gezinilmesini ister.
1. `dotnet` bulunan ilk *global.js* belirtilen SDK 'yı kullanır.
1. `dotnet`*global.json* yoksa en son yüklenen SDK 'yı kullanır.

*global.js* üzerindeki makalenin [eşleştirme KURALLARı](../tools/global-json.md#matching-rules) bölümünde bir SDK sürümü seçme hakkında daha fazla bilgi edinebilirsiniz.

## <a name="target-framework-monikers-define-build-time-apis"></a>Hedef çerçeve takma adları derleme süresi API 'Lerini tanımlar

Projenizi bir **hedef çerçeve bilinen** adı 'nda (tfd) tanımlanan API 'lerle derleyin. [Hedef çerçevesini](../../standard/frameworks.md) proje dosyasında belirtirsiniz. `TargetFramework`Aşağıdaki örnekte gösterildiği gibi proje dosyanızdaki öğesini ayarlayın:

``` xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

Projenizi birden çok TFMs 'ye karşı derleyebilirsiniz. Birden çok hedef çerçeveyi ayarlamak kitaplıklar için daha yaygındır, ancak uygulamalarla da gerçekleştirilebilir. Bir `TargetFrameworks` Özellik (çoğul `TargetFramework` ) belirlersiniz. Hedef çerçeveler, aşağıdaki örnekte gösterildiği gibi noktalı virgülle ayrılmıştır:

``` xml
<TargetFrameworks>netcoreapp3.0;net47</TargetFrameworks>
```

Belirli bir SDK, birlikte geldiği çalışma zamanının hedef çerçevesine katıp sabit bir çerçeve kümesini destekler. Örneğin, .NET Core 3,1 SDK 'Sı, hedef Framework 'ün uygulanması olan .NET Core 3,1 çalışma zamanını içerir `netcoreapp3.0` . .NET Core 3,1 SDK,,,, `netcoreapp2.1` `netcoreapp2.2` `netcoreapp3.0` ancak değil `net5.0` (veya üzeri). İçin derlemek üzere .NET 5,0 SDK 'sını yüklersiniz `net5.0` .

.NET Standard hedef çerçeveler, SDK 'nın birlikte geldiği çalışma zamanının hedef çerçevesine de dönüştürülür. .NET 5,0 SDK 'Sı `netstandard2.1` . Daha fazla bilgi için bkz. [.NET Standard](../../standard/net-standard.md).

## <a name="framework-dependent-apps-roll-forward"></a>Çerçeveye bağımlı uygulamalar ileri alma

İle kaynağından [`dotnet run`](../tools/dotnet-run.md) , [**çerçevesine bağlı bir dağıtımdan**](../deploying/index.md#publish-framework-dependent) [`dotnet myapp.dll`](../tools/dotnet.md#description) veya ile [**çerçeveye bağlı bir yürütülebilirden**](../deploying/index.md#publish-framework-dependent) uygulama çalıştırdığınızda, `myapp.exe` `dotnet` çalıştırılabilir dosya uygulamanın **ana bilgisayarı** olur.

Konak makinede yüklü en son düzeltme eki sürümünü seçer. Örneğin, `netcoreapp3.0` proje dosyanızda belirttiyseniz ve `3.0.2` en son .NET çalışma zamanı yüklüyse, `3.0.2` çalışma zamanı kullanılır.

Kabul edilebilir `3.0.*` bir sürüm bulunamazsa yeni bir `3.*` sürüm kullanılır. Örneğin, belirtilmişse `netcoreapp3.0` ve yalnızca `3.1.0` yüklüyse, uygulama `3.1.0` çalışma zamanını kullanarak çalışır. Bu davranış, "ikincil sürüm alma" olarak adlandırılır. Alt sürümler de göz önünde bulundurulmaz. Kabul edilebilir çalışma zamanı yüklü olmadığında uygulama çalıştırılmaz.

Birkaç kullanım örneği, 3,0 hedefliyorsanız davranışı gösterir:

- ✔️ 3,0 belirtildi. 3.0.3, en yüksek düzeltme eki sürümüdür. 3.0.3 kullanılır.
- ❌ 3,0 belirtildi. 3,0. * sürüm yüklendi. 2.1.1, en yüksek çalışma zamanının yüklü olduğunu. Bir hata iletisi görüntülenir.
- ✔️ 3,0 belirtildi. 3,0. * sürüm yüklendi. 3.1.0, en yüksek çalışma zamanı sürümüdür. 3.1.0 kullanılır.
- ❌ 2,0 belirtildi. 2. x sürümü yüklü değil. 3.0.0, en yüksek çalışma zamanının yüklü olduğunu. Bir hata iletisi görüntülenir.

İkincil sürüm al-ileri, son kullanıcıları etkileyebilecek bir yan etkiye sahiptir. Şu senaryoyu göz önünde bulundurun:

1. Uygulama, 3,0 'in gerekli olduğunu belirtir.
2. Çalıştırıldığında, 3,0. * sürümü yüklü değildir, ancak 3.1.0. Sürüm 3.1.0 kullanılacak.
3. Daha sonra, Kullanıcı 3.0.3 yükleyip uygulamayı yeniden çalıştırdığında 3.0.3 artık kullanılacaktır.

Özellikle ikili verileri serileştirme gibi senaryolar için 3.0.3 ve 3.1.0 farklı şekilde davranması olasıdır.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Kendi içindeki dağıtımlar seçili çalışma zamanını içerir

Bir uygulamayı [**kendi kendine dahil**](../deploying/index.md#publish-self-contained)edilen bir dağıtım olarak yayımlayabilirsiniz. Bu yaklaşım, uygulamanızla birlikte .NET çalışma zamanını ve kitaplıklarını paketler. Kendi içinde olan dağıtımlar çalışma zamanı ortamlarına bağımlılığı yoktur. Çalışma zamanı sürüm seçimi yayımlama zamanında gerçekleşir, çalışma zamanı değildir.

Yayımlama işlemi, belirtilen çalışma zamanı ailesinin en son düzeltme eki sürümünü seçer. Örneğin, `dotnet publish` .net core 3,0 çalışma zamanı ailesindeki en son düzeltme eki sürümledir, .NET Core 3.0.3 ' ı seçer. Hedef Framework (en son yüklenen güvenlik düzeltme ekleri dahil) uygulamayla birlikte paketlenir.

Bir uygulama için belirtilen minimum sürüm karşılanmazsa, bu bir hatadır. `dotnet publish` en son çalışma zamanı düzeltme eki sürümüne bağlar (belirli bir ana. ikincil sürüm ailesi içinde). `dotnet publish` , ' ın geri iletme semantiğini desteklemez `dotnet run` . Düzeltme ekleri ve bağımsız dağıtımlar hakkında daha fazla bilgi için .NET uygulamaları dağıtma konusunda [çalışma zamanı düzeltme eki seçimi](../deploying/runtime-patch-selection.md) başlıklı makaleye bakın.

Kendi içinde olan dağıtımlar belirli bir düzeltme eki sürümü gerektirebilir. Aşağıdaki örnekte gösterildiği gibi, proje dosyasında en düşük çalışma zamanı düzeltme eki sürümünü (daha yüksek veya daha düşük sürümlere) geçersiz kılabilirsiniz:

``` xml
<RuntimeFrameworkVersion>3.0.3</RuntimeFrameworkVersion>
```

`RuntimeFrameworkVersion`Öğesi varsayılan sürüm ilkesini geçersiz kılar. Kendi içinde olan dağıtımlar için, `RuntimeFrameworkVersion` *tam* çalışma zamanı çerçevesi sürümünü belirtir. Çerçeveye bağımlı uygulamalar için `RuntimeFrameworkVersion` gereken *En düşük* çalışma zamanı çerçevesi sürümünü belirtir.

## <a name="see-also"></a>Ayrıca bkz.

- [.Net indirin ve yükleyin](../install/index.yml).
- [.NET çalışma zamanını ve SDK 'yı kaldırma](../install/remove-runtime-sdk-versions.md).
