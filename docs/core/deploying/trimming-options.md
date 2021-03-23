---
title: Kırpma seçenekleri
description: Kendi içindeki uygulamaların kırpılacağını nasıl denetleyeceğinizi öğrenin.
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: 93fee991cf218a52ad1d9a2597b1c9b2d442110a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874257"
---
# <a name="trimming-options"></a>Kırpma seçenekleri

Aşağıdaki MSBuild özellikleri ve öğeleri, [kırpılan kendi içindeki dağıtımların](trim-self-contained.md)davranışını etkiler. Bir kısmı `ILLink` , kırpmayı uygulayan temel aracın adı olan bahsetme seçenekleridir. Temel alınan araç hakkında daha fazla bilgi [bağlayıcı belgelerinde](https://github.com/mono/linker/tree/master/docs)bulunabilir.

## <a name="enable-trimming"></a>Kırpmayı etkinleştir

- `<PublishTrimmed>true</PublishTrimmed>`

   SDK tarafından tanımlanan varsayılan ayarlarla yayınlama sırasında kırpmayı etkinleştirin.

Kullanırken `Microsoft.NET.Sdk` , bu, netcoreapp çalışma zamanı paketinden çerçeve derlemelerinin derleme düzeyinde kırpmasını gerçekleştirir. Uygulama kodu ve Framework olmayan kitaplıklar kırpılmamış. Diğer SDK 'lar farklı varsayılanlar tanımlayabilir.

## <a name="trimming-granularity"></a>Parçalı yapısı kırpma

Aşağıdaki ayrıntı düzeyi ayarları, kullanılmamış olmayan Il 'nin nasıl atılma olduğunu denetler. Bu, bir özellik olarak veya [tek bir derlemede](#trimmed-assemblies)meta veriler olarak ayarlanabilir.

- `<TrimMode>copyused</TrimMode>`

   Derleme düzeyinde kırpmasını etkinleştirin ve bu, herhangi bir bölümü (statik olarak anlaşılmış bir şekilde) kullanılırsa tüm bütünleştirilmiş kodu saklar.

- `<TrimMode>link</TrimMode>`

    Kullanılmayan üyeleri türlerden kaldıran üye düzeyinde kırpmayı etkinleştirin.

`<IsTrimmable>true</IsTrimmable>`Meta veri içeren derlemeler, ancak açık olmaz `TrimMode` Global kullanır `TrimMode` . İçin varsayılandır `TrimMode` `Microsoft.NET.Sdk` `copyused` .

## <a name="trimmed-assemblies"></a>Kırpılan derlemeler

Kırpılan bir uygulamayı yayımlarken, SDK, `ItemGroup` `ManagedAssemblyToLink` kırpma için işlenecek dosya kümesini temsil eden bir çağrılan öğesini hesaplar. `ManagedAssemblyToLink` derleme başına kırpma davranışını denetleyen meta verilere sahip olabilir. Bu meta verileri ayarlamak için, yerleşik hedeften önce çalışan bir hedef oluşturun `PrepareForILLink` . Aşağıdaki örnek, kırpılacağını nasıl etkinleştireceğinizi gösterir `MyAssembly` .

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

`ManagedAssemblyToLink`SDK bu kümeyi yayımlama sırasında hesapladığı ve değişmemelidir beklediği için öğe ekleme veya kaldırma. Desteklenen meta veriler şunlardır:

- `<IsTrimmable>true</IsTrimmable>`

  Verilen derlemenin kırpılmadığını denetleyin.

- `<TrimMode>copyused</TrimMode>` veya `<TrimMode>link</TrimMode>`

  Bu derlemenin [kırpma parçalı yapısını](#trimming-granularity) denetleyin. Bu genel olarak önceliklidir `TrimMode` . `TrimMode`Bir derlemenin ayarlanması, ' i belirtir `<IsTrimmable>true</IsTrimmable>` .

## <a name="root-assemblies"></a>Kök derlemeler

Olmayan tüm derlemeler `<IsTrimmable>true</IsTrimmable>` analiz için kökleri olarak kabul edilir, bu da bunların ve statik olarak anladıkları bağımlılıkların tutulduğu anlamına gelir. Ek derlemeler ada göre "kökü belirtilmiş" olabilir (uzantı olmadan `.dll` ):

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a>Kök tanımlayıcıları

Analize yönelik kökleri belirtmenin başka bir yolu, bağlayıcı [tanımlayıcı biçimini](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format)kullanan bir XML dosyası kullanmaktır. Bu, tüm derleme yerine belirli üyeleri köklemenizi sağlar.

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

Örneğin, `MyRoots.xml` uygulama tarafından dinamik olarak erişilen belirli bir yöntemi kökleyebilir:

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a>Analiz uyarıları

Kırpma statik olarak erişilebilen Il 'yi kaldırır. Yansıma veya dinamik bağımlılıklar oluşturan diğer desenleri kullanan uygulamalar, kırparak kırılabilir. Bu tür desenler hakkında uyarı almak için:

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    Kırpma Analizi uyarılarını etkinleştirin.

Bu, kendi kodunuz, kitaplık kodu ve çerçeve kodunuz da dahil olmak üzere tüm uygulama hakkındaki uyarıları içerir.

## <a name="warning-versions"></a>Uyarı sürümleri

Kırpma analizi, [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) SDK genelinde analiz uyarıları sürümünü denetleyen özelliği uyar. Kırpma Analizi uyarılarının sürümünü bağımsız olarak denetleyen başka bir özellik vardır (derleyiciye benzer şekilde `WarningLevel` ):

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    Yalnızca verilen düzeyin veya daha düşük olan uyarıları yay. Bu, `9999` tüm uyarı sürümlerinin dahil olması olabilir.

## <a name="suppressing-warnings"></a>Gizleme uyarıları

Tek [uyarı kodları](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) ,,, ve dahil olmak üzere araç zinciri tarafından kullanılan olağan MSBuild özellikleri kullanılarak `NoWarn` gizlenebilir `WarningsAsErrors` `WarningsNotAsErrors` `TreatWarningsAsErrors` . Illınk hata durumu davranışını bağımsız olarak denetleyen ek bir seçenek vardır:

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    Illınk uyarılarını hata olarak değerlendirin. Bu durum, derleyici uyarılarını hata olarak bir genel olarak düşünerek uyarı çözümleme uyarılarını hatalara karşı açıp çözmemek için yararlı olabilir.

## <a name="removing-symbols"></a>Sembolleri kaldırma

Simgeler normalde kırpılan Derlemelerle eşleşecek şekilde kırpılacak. Tüm sembolleri de kaldırabilirsiniz:

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    Katıştırılmış pdb 'leri ve ayrı PDB dosyaları dahil olmak üzere kırpılan uygulamadan sembolleri kaldırın. Bu hem uygulama kodu hem de simgelerle gelen bağımlılıklar için geçerlidir.

SDK, özelliği kullanarak hata ayıklayıcı desteğini devre dışı bırakmayı da mümkün kılar `DebuggerSupport` . Hata ayıklayıcı desteği devre dışı bırakıldığında, kırpma sembolleri otomatik olarak kaldırır ( `TrimmerRemoveSymbols` Varsayılan olarak true olur).

## <a name="trimming-framework-library-features"></a>Çerçeve kitaplığı özelliklerini kırpma

Çerçeve kitaplıklarının birçok özellik alanı, devre dışı özellikler için kodu kaldırmayı olanaklı kılan bağlayıcı yönergeleri ile birlikte gelir.

- `<DebuggerSupport>false</DebuggerSupport>`

    Daha iyi hata ayıklama deneyimlerini sağlayan kodu kaldırın. Bu, [sembolleri de kaldırır](#removing-symbols).

- `<EnableUnsafeBinaryFormatterSerialization>false</EnableUnsafeBinaryFormatterSerialization>`

    BinaryFormatter serileştirme desteğini kaldırın. Daha fazla bilgi için bkz. [BinaryFormatter serileştirme yöntemleri artık kullanılmıyor](../compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete.md).

- `<EnableUnsafeUTF7Encoding>false</EnableUnsafeUTF7Encoding>`

    Güvenli olmayan UTF-7 kodlama kodunu kaldır. Daha fazla bilgi için bkz. [UTF-7 kod yolları artık kullanılmıyor](../compatibility/core-libraries/5.0/utf-7-code-paths-obsolete.md).

- `<EventSourceSupport>false</EventSourceSupport>`

    EventSource ile ilgili kodu veya mantığı kaldırın.

- `<HttpActivityPropagationSupport>false</HttpActivityPropagationSupport>`

    System .net. http için tanılama desteğiyle ilgili kodu kaldırın.

- `<InvariantGlobalization>true</InvariantGlobalization>`

    Genelleştirme 'ye özgü kodu ve verileri kaldırın. Daha fazla bilgi için bkz. [sabit mod](../run-time-config/globalization.md#invariant-mode).

- `<UseSystemResourceKeys>true</UseSystemResourceKeys>`

    Derlemeler için özel durum iletilerini şerit `System.*` . Bir derlemeden bir özel durum oluştuğunda `System.*` , ileti tam ileti yerine basitleştirilmiş kaynak kimliği olur.

 Bu özellikler ilgili kodun kırpılmasına neden olur ve ayrıca [runtimeconfig](../run-time-config/index.md) dosyası aracılığıyla özellikleri devre dışı bırakır. İlgili runtimeconfig seçenekleri de dahil olmak üzere bu özellikler hakkında daha fazla bilgi için bkz. [özellik anahtarları](https://github.com/dotnet/runtime/blob/main/docs/workflow/trimming/feature-switches.md). Bazı SDK 'lar bu özellikler için varsayılan değerlere sahip olabilir.
