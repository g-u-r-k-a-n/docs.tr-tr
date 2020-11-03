---
title: Bağımlılıklar ve .NET kitaplıkları
description: .NET kitaplıklarında NuGet bağımlılıklarını yönetmeye yönelik en iyi yöntem önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: d189a3364b501272e29de72b6018844877bf2128
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189309"
---
# <a name="dependencies"></a>Bağımlılıklar

.NET kitaplığına bağımlılık eklemenin birincil yolu NuGet paketlerine başvuruyorlardır. NuGet paket başvuruları, zaten yazılmış işlevselliği hızlı bir şekilde yeniden kullanmanıza ve bu işlevselliği kullanmanıza olanak tanır, ancak .NET geliştiricileri için yaygın bir savunma kaynağıdır. Bağımlılıkları doğru şekilde yönetmek, diğer .NET kitaplıklarında bulunan değişikliklerin .NET kitaplığınızı bozmasını engellemek için önemlidir, tersi de geçerlidir!

## <a name="diamond-dependencies"></a>Elmas bağımlılıkları

.NET projesinin, bağımlılık ağacında bir paketin birden fazla sürümüne sahip olması yaygın bir durumdur. Örneğin, bir uygulama, her biri aynı paketin farklı sürümlerine bağlı olan iki NuGet paketine bağımlıdır. Bir elmas bağımlılığı artık uygulamanın bağımlılık grafiğinde bulunur.

![Elmas bağımlılığı](./media/dependencies/diamond-dependency.png "Elmas bağımlılığı")

Derleme zamanında, NuGet, bağımlılıkların bağımlılıkları da dahil olmak üzere bir projenin bağımlı olduğu tüm paketleri analiz eder. Bir paketin birden çok sürümü algılandığında, kurallar bir tane seçmek üzere değerlendirilir. Aynı uygulamadaki bir derlemenin yan yana sürümlerini çalıştırmak .NET 'te sorunlu olduğundan paketlerin kaldırılması gerekir.

Çoğu elmas bağımlılığı kolayca çözülür; Ancak, belirli koşullarda sorunlar oluşturabilirler:

- **Çakışan NuGet paket başvuruları** , paketin geri yükleme sırasında bir sürümün çözümlenmesini engelliyor.
- **Sürümler arasındaki son değişiklikler** çalışma zamanında hatalara ve özel durumlara neden olur.
- **Paket derlemesinin tanımlayıcı adlı** , derleme sürümü değiştiği ve uygulama .NET Framework üzerinde çalışıyor. Derleme bağlama yeniden yönlendirmeleri gereklidir.

Hangi paketlerin sizin de birlikte kullanılacağını Bileme olanaksızdır. Bir elmas bağımlılığını düşürmenin olasılığını azaltmanın iyi bir yolu, bağlı olduğunuz paket sayısını en aza indirmektir.

✔️, .NET kitaplığınızı gereksiz bağımlılıklar için gözden geçirin.

## <a name="nuget-dependency-version-ranges"></a>NuGet bağımlılığı sürüm aralıkları

Paket başvurusu, izin verdiği geçerli paketlerin aralığını belirtir. Genellikle proje dosyasındaki paket başvuru sürümü en düşük sürümdür ve en fazla bir değer yoktur.

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

Bir yandan,, bağımlılıkları çözümlerken NuGet tarafından kullanılan kurallar [karmaşıktır](/nuget/consume-packages/dependency-resolution), ancak [Varsayılan olarak](/nuget/consume-packages/install-use-packages-visual-studio#install-and-update-options) NuGet, en düşük uygun sürümü arar. En düşük uyumluluk sorunlarına sahip olacağı için NuGet, en yüksek kullanılabilir sürümü kullanarak en düşük uygun sürümü tercih eder.

NuGet 'in en düşük geçerli sürüm kuralı nedeniyle, en son sürümü almayı önlemek için paket başvurularına bir üst sürüm veya tam Aralık yerleştirmeniz gerekli değildir. NuGet, sizin için en düşük, en uyumlu sürümü bulmayı zaten deniyor.

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

Çakışma varsa, üst sürüm sınırları NuGet 'in başarısız olmasına neden olur. Örneğin, bir kitaplık, farklı bir kitaplık 2,0 veya üzeri gerektirdiğinden tam olarak 1,0 kabul eder. Sürüm 2,0 ' de önemli değişiklikler sunulurken, katı veya üst sınır sürümü bağımlılığı bir hata garanti eder.

![Elmas bağımlılığı çakışması](./media/dependencies/diamond-dependency-conflict.png "Elmas bağımlılığı çakışması")

❌ En düşük sürüm olmadan NuGet paketi başvuruları yoktur.

❌ Tam bir sürümü talep eden NuGet paket başvurularından KAÇıNıN.

❌ Sürüm üst sınırı olan NuGet paket başvurularından KAÇıNıN.

## <a name="nuget-shared-source-packages"></a>NuGet paylaşılan kaynak paketleri

Dış NuGet paket bağımlılıklarını azaltmanın bir yolu, paylaşılan kaynak paketlerine başvurmaktır. Paylaşılan bir kaynak paketi, başvuruluyorsa bir projede yer alan [kaynak kodu dosyaları](/nuget/reference/nuspec#including-content-files) içerir. Yalnızca projenizin geri kalanı ile derlenen kaynak kodu dosyalarını dahil ettiğinden, dış bağımlılık ve çakışma şansı yoktur.

Paylaşılan kaynak paketleri, küçük işlevsellik parçaları için harika. Örneğin, HTTP çağrıları yapmak için bir yardımcı yöntem paylaşılan kaynak paketidir.

![Paylaşılan kaynak paketi](./media/dependencies/shared-source-package.png "Paylaşılan kaynak paketi")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![Paylaşılan kaynak proje](./media/dependencies/shared-source-project.png "Paylaşılan kaynak proje")

Paylaşılan kaynak paketlerinde bazı sınırlamalar vardır. Yalnızca tarafından başvurulabilirler, bu `PackageReference` nedenle eski `packages.config` projeler hariç tutulur. Ayrıca, paylaşılan kaynak paketleri yalnızca aynı dil türüne sahip projeler tarafından kullanılabilir. Bu sınırlamalar nedeniyle, paylaşılan kaynak paketleri, bir açık kaynak proje içindeki işlevselliği paylaşmak için en iyi şekilde kullanılır.

✔️ küçük, iç işlevsellik parçaları için paylaşılan kaynak paketlerine başvurmayı göz önünde bulundurun.

✔️, küçük, iç işlevsellik parçaları sağlıyorsa paketinizi paylaşılan bir kaynak paketi yapmayı düşünün.

✔️ Paylaşılan kaynak paketlerine başvuru YAPıN `PrivateAssets="All"` .

> Bu ayar NuGet 'e paketin yalnızca geliştirme zamanında kullanılacağını ve genel bağımlılık olarak sunulmayacağını söyler.

❌ Ortak API 'niz içinde paylaşılan kaynak paketi türleri yok.

> Paylaşılan kaynak türleri, başvurulan derlemeye derlenir ve derleme sınırları arasında değiştirilemez. Örneğin, `IRepository` bir projedeki paylaşılan kaynak türü, başka bir projede aynı paylaşılan kaynaktan ayrı bir tür `IRepository` . Paylaşılan kaynak paketlerindeki türlerin görünürlüğe sahip olması gerekir `internal` .

❌ Paylaşılan kaynak paketlerini NuGet.org 'e yayımlamayın.

> Paylaşılan kaynak paketleri kaynak kodu içerir ve yalnızca aynı dil türüne sahip projeler tarafından kullanılabilir. Örneğin, bir C# paylaşılan kaynak paketi bir F # uygulaması tarafından kullanılamaz.
>
> Paylaşılan kaynak paketlerini yerel bir akışa yayımlayın veya bunları projenizde dahili olarak tüketmek üzere [MyGet](./publish-nuget-package.md) yapın.

>[!div class="step-by-step"]
>[Önceki](nuget.md) 
> [Sonraki](sourcelink.md)
