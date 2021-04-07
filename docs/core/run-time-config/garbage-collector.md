---
title: Çöp toplayıcı yapılandırma ayarları
description: Çöp toplayıcının .NET Core uygulamaları için belleği nasıl yönettiğini yapılandırmak üzere çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 17df3ec8473750edfca4999972c56be1e8a5feec
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496663"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a>Çöp toplama için çalışma zamanı yapılandırma seçenekleri

Bu sayfa, çalışma zamanında değiştirilebilen çöp toplayıcı (GC) ayarları hakkında bilgi içerir. Çalışan bir uygulamanın en yüksek performans düzeyine ulaşmak istiyorsanız bu ayarları kullanmayı deneyin. Bununla birlikte, varsayılan olarak, çoğu uygulama için tipik durumlarda en iyi performansı sağlar.

Ayarlar bu sayfadaki gruplar halinde düzenlenir. Her grup içindeki ayarlar, belirli bir sonuca ulaşmak için genellikle birbirleriyle birlikte kullanılır.

> [!NOTE]
>
> - Bu ayarlar ayrıca uygulama çalışırken dinamik olarak değiştirilebilir, bu nedenle ayarladığınız tüm çalışma zamanı ayarları geçersiz kılınabilir.
> - [Gecikme düzeyi](../../standard/garbage-collection/latency.md)gibi bazı ayarlar tipik olarak yalnızca TASARıM zamanında API aracılığıyla ayarlanır. Bu tür ayarlar bu sayfadan çıkarılır.
> - Sayı değerleri için, dosyadaki *runtimeconfig.js* , ortam değişkeni ayarları için onaltılı gösterimdeki ayarlar için ondalık gösterimi kullanın. Onaltılık değerler için, bunları "0x" öneki olmadan veya olmadan belirtebilirsiniz.

## <a name="flavors-of-garbage-collection"></a>Çöp toplamanın türleri

Çöp toplamanın iki ana özellikleri, iş istasyonu GC ve sunucu GC ' dir. İkisi arasındaki farklılıklar hakkında daha fazla bilgi için bkz. [Workstation and Server çöp toplama](../../standard/garbage-collection/workstation-server-gc.md).

Çöp toplamanın alt türleri arka plan ve eş zamanlı değil.

Çöp toplamanın türlerini seçmek için aşağıdaki ayarları kullanın:

- [İş istasyonu ile sunucu GC](#workstation-vs-server)
- [Arka Plan GC](#background-gc)

### <a name="workstation-vs-server"></a>İş istasyonu ile sunucu

- Uygulamanın iş istasyonu çöp toplamayı veya sunucu çöp toplamayı kullanıp kullanmadığını yapılandırır.
- Varsayılan: Iş Istasyonu atık toplama. Bu değeri değerine ayarlamaya eşdeğerdir `false` .

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.Server` | `false` -iş istasyonu<br/>`true` -sunucu | .NET Core 1,0 |
| **MSBuild özelliği** | `ServerGarbageCollection` | `false` -iş istasyonu<br/>`true` -sunucu | .NET Core 1,0 |
| **Ortam değişkeni** | `COMPlus_gcServer` | `0` -iş istasyonu<br/>`1` -sunucu | .NET Core 1,0 |
| **.NET Framework içinapp.config** | [GCServer](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | `false` -iş istasyonu<br/>`true` -sunucu |  |

#### <a name="examples"></a>Örnekler

*runtimeconfig.js* dosya:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="background-gc"></a>Arka Plan GC

- Arka plan (eşzamanlı) Çöp toplamanın etkinleştirilip etkinleştirilmeyeceğini yapılandırır.
- Varsayılan: arka plan GC kullanın. Bu değeri değerine ayarlamaya eşdeğerdir `true` .
- Daha fazla bilgi için bkz. [arka plan atık toplama](../../standard/garbage-collection/background-gc.md).

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.Concurrent` | `true` -arka plan GC<br/>`false` -eş zamanlı olmayan GC | .NET Core 1,0 |
| **MSBuild özelliği** | `ConcurrentGarbageCollection` | `true` -arka plan GC<br/>`false` -eş zamanlı olmayan GC | .NET Core 1,0 |
| **Ortam değişkeni** | `COMPlus_gcConcurrent` | `1` -arka plan GC<br/>`0` -eş zamanlı olmayan GC | .NET Core 1,0 |
| **.NET Framework içinapp.config** | [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | `true` -arka plan GC<br/>`false` -eş zamanlı olmayan GC |  |

#### <a name="examples"></a>Örnekler

*runtimeconfig.js* dosya:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a>Kaynak kullanımını yönetme

Çöp toplayıcının bellek ve işlemci kullanımını yönetmek için aşağıdaki ayarları kullanın:

- [Toplamak](#affinitize)
- [Maskeyi afleştir](#affinitize-mask)
- [Aralıkları afleştir](#affinitize-ranges)
- [CPU grupları](#cpu-groups)
- [Yığın sayısı](#heap-count)
- [Yığın sınırı](#heap-limit)
- [Yığın sınırı yüzdesi](#heap-limit-percent)
- [Yüksek bellek yüzdesi](#high-memory-percent)
- [Nesne başına yığın sınırları](#per-object-heap-limits)
- [Nesne başına yığın sınırı yüzdesi](#per-object-heap-limit-percents)
- [VM 'yi koruma](#retain-vm)

Bu ayarlardan bazıları hakkında daha fazla bilgi için, bkz. [iş istasyonu ve sunucu GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blogu girişi.

### <a name="heap-count"></a>Yığın sayısı

- Çöp toplayıcı tarafından oluşturulan Heap sayısını sınırlandırır.
- Yalnızca sunucu çöp toplama için geçerlidir.
- [GC işlemci benzeşimi](#affinitize) etkinse, varsayılan olarak, yığın sayısı ayarı `n` GC sayfa@@/iş parçacıklarını ilk işlemcilere göre sayar `n` . (Tam olarak hangi işlemcilerin olduğunu belirtmek için, bu [maskeyi](#affinitize-mask) seçin veya [aralıklar](#affinitize-ranges) ayarlarını kesin olarak belirleyin.)
- [GC işlemci benzeşimi](#affinitize) devre dışıysa, bu ayar GC yığınlarının sayısını sınırlar.
- Daha fazla bilgi için [Gcheapcount açıklamalarını](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)inceleyin.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.HeapCount` | *ondalık değer* | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapCount` | *onaltılık değer* | .NET Core 3.0 |
| **.NET Framework içinapp.config** | [GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | *ondalık değer* | .NET Framework 4.6.2 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> *Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin. Örneğin, Heap sayısını 16 ile sınırlamak için değerler JSON dosyası için 16, ortam değişkeni için 0x10 veya 10 olur.

### <a name="affinitize-mask"></a>Maskeyi afleştir

- Çöp toplayıcı iş parçacıklarının kullanması gereken tam işlemcileri belirtir.
- [GC işlemci benzeşimi](#affinitize) devre dışıysa, bu ayar yok sayılır.
- Yalnızca sunucu çöp toplama için geçerlidir.
- Değer, işlem için kullanılabilir olan işlemcileri tanımlayan bir bit maskesidir. Örneğin, bir 1023 ondalık değeri (veya ortam değişkenini kullanıyorsanız, 0x3FF veya 3FF onaltılı değeri), ikili gösterimde 0011 1111 1111 ' dir. Bu, ilk 10 işlemcinin kullanılacağını belirtir. Sıradaki 10 işlemciyi belirtmek için, işlemci 10-19 ' 1047552 nin ondalık değerini (veya 0xFFC00 ya da FFC00) bir 1111 1111 1100 0000 0000 ikili değere eşdeğer bir değere belirleyin.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.HeapAffinitizeMask` | *ondalık değer* | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapAffinitizeMask` | *onaltılık değer* | .NET Core 3.0 |
| **.NET Framework içinapp.config** | [GCHeapAffinitizeMask](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | *ondalık değer* | .NET Framework 4.6.2 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="affinitize-ranges"></a>Aralıkları afleştir

- Çöp toplayıcı iş parçacıkları için kullanılacak işlemcilerin listesini belirtir.
- Bu ayar [System. GC. Cenpaffinitizemask](#affinitize-mask)ile benzerdir, ancak 64 'den fazla işlemci belirtmenize izin verir.
- Windows işletim sistemleri için, işlemci numarasını veya aralığını karşılık gelen [CPU grubuyla](/windows/win32/procthread/processor-groups)önek olarak ekleyin, örneğin, "0:1-10, 0:12, 1:50-52, 1:70".
- [GC işlemci benzeşimi](#affinitize) devre dışıysa, bu ayar yok sayılır.
- Yalnızca sunucu çöp toplama için geçerlidir.
- Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.GCHeapAffinitizeRanges` | İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.<br/>UNIX örneği: "1-10, 12, 50-52, 70"<br/>Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70" | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapAffinitizeRanges` | İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.<br/>UNIX örneği: "1-10, 12, 50-52, 70"<br/>Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70" | .NET Core 3.0 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="cpu-groups"></a>CPU grupları

- Çöp toplayıcının [CPU grupları](/windows/win32/procthread/processor-groups) kullanıp kullanmadığını yapılandırır.

  64 bitlik bir Windows bilgisayarında birden çok CPU grubu olduğunda, diğer bir deyişle, 64 ' den fazla işlemci varsa, bu öğenin tüm CPU gruplarında çöp toplamayı genişletmelerini etkinleştirir. Çöp toplayıcı, Heap 'ler oluşturmak ve dengelemek için tüm çekirdekleri kullanır.

- Yalnızca 64-bit Windows işletim sistemlerinde sunucu çöp toplama için geçerlidir.
- Varsayılan: GC, CPU grupları arasında genişletilmez. Bu değeri değerine ayarlamaya eşdeğerdir `0` .
- Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.CpuGroup` | `0` -devre dışı<br/>`1` -etkin | .NET 5.0 |
| **Ortam değişkeni** | `COMPlus_GCCpuGroup` | `0` -devre dışı<br/>`1` -etkin | .NET Core 1,0 |
| **.NET Framework içinapp.config** | [GCCpuGroup](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | `false` -devre dışı<br/>`true` -etkin |  |

> [!NOTE]
> Ortak dil çalışma zamanını (CLR) tüm CPU grupları arasında iş parçacığı havuzundan da dağıtmak üzere yapılandırmak için, [Thread_UseAllCpuGroups öğesi](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) seçeneğini etkinleştirin. .NET Core uygulamaları için, ortam değişkeninin değerini olarak ayarlayarak bu seçeneği etkinleştirebilirsiniz `COMPlus_Thread_UseAllCpuGroups` `1` .

### <a name="affinitize"></a>Toplamak

- *Çöp toplama* iş parçacıklarının işlemcilerle kullanılıp kullanılmayacağını belirtir. Bir GC iş parçacığını eklemek için yalnızca belirli bir CPU üzerinde çalışabilen anlamına gelir. Her GC iş parçacığı için bir yığın oluşturulur.
- Yalnızca sunucu çöp toplama için geçerlidir.
- Varsayılan: işlemcilere sahip çöp toplama iş parçacıklarını ön olarak başlatma. Bu değeri değerine ayarlamaya eşdeğerdir `false` .

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.NoAffinitize` | `false` -afze<br/>`true` -yok etme | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCNoAffinitize` | `0` -afze<br/>`1` -yok etme | .NET Core 3.0 |
| **.NET Framework içinapp.config** | [GCNoAffinitize](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | `false` -afze<br/>`true` -yok etme | .NET Framework 4.6.2 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="heap-limit"></a>Yığın sınırı

- GC yığını ve GC booksaklanması için bayt cinsinden en fazla tamamlama boyutunu belirtir.
- Bu ayar yalnızca 64 bitlik bilgisayarlar için geçerlidir.
- [Nesne başına yığın sınırları](#per-object-heap-limits) yapılandırılırsa Bu ayar yoksayılır.
- Yalnızca belirli durumlarda geçerli olan varsayılan değer, kapsayıcıdaki bellek sınırının 20 MB veya %75 ' sinden daha fazladır. Varsayılan değer şu durumlarda geçerlidir:

  - İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyor.
  - [System. GC. HeapHardLimitPercent](#heap-limit-percent) ayarlanmadı.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.HeapHardLimit` | *ondalık değer* | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapHardLimit` | *onaltılık değer* | .NET Core 3.0 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> *Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin. Örneğin, 200 mebibytes (MIB) yığın sabit sınırı belirtmek için, değerler JSON dosyası için 209715200 ve ortam değişkeni için 0xC800000 veya C800000 olur.

### <a name="heap-limit-percent"></a>Yığın sınırı yüzdesi

- Toplam fiziksel belleğin yüzdesi olarak izin verilen GC yığın kullanımını belirtir.
- [System. GC. HeapHardLimit](#heap-limit) da ayarlandıysa, bu ayar yok sayılır.
- Bu ayar yalnızca 64 bitlik bilgisayarlar için geçerlidir.
- İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyorsa, yüzde bu bellek sınırının yüzdesi olarak hesaplanır.
- [Nesne başına yığın sınırları](#per-object-heap-limits) yapılandırılırsa Bu ayar yoksayılır.
- Yalnızca belirli durumlarda geçerli olan varsayılan değer, kapsayıcıdaki bellek sınırının 20 MB veya %75 ' sinden daha fazladır. Varsayılan değer şu durumlarda geçerlidir:

  - İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyor.
  - [System. GC. HeapHardLimit](#heap-limit) ayarlanmadı.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.HeapHardLimitPercent` | *ondalık değer* | .NET Core 3.0 |
| **Ortam değişkeni** | `COMPlus_GCHeapHardLimitPercent` | *onaltılık değer* | .NET Core 3.0 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> *Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin. Örneğin, yığın kullanımını %30 olarak sınırlandırmak için değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olur.

### <a name="per-object-heap-limits"></a>Nesne başına yığın sınırları

GC 'nin izin verilen yığın kullanımını nesne başına yığın temelinde belirtebilirsiniz. Farklı sayfa@@ 'ler büyük nesne yığını (LOH), küçük nesne yığını (SoH) ve sabitlenmiş nesne yığını (POH).

- , Veya ayarlarından herhangi biri için bir değer belirtirseniz `COMPLUS_GCHeapHardLimitSOH` `COMPLUS_GCHeapHardLimitLOH` `COMPLUS_GCHeapHardLimitPOH` , ve için bir değer de belirtmeniz gerekir `COMPLUS_GCHeapHardLimitSOH` `COMPLUS_GCHeapHardLimitLOH` . Aksi takdirde, çalışma zamanı başlatılamaz.
- İçin varsayılan değer `COMPLUS_GCHeapHardLimitPOH` 0 ' dır. `COMPLUS_GCHeapHardLimitSOH` ve `COMPLUS_GCHeapHardLimitLOH` varsayılan değerlere sahip değildir.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.HeapHardLimitSOH` | *ondalık değer* | .NET 5.0 |
| **Ortam değişkeni** | `COMPLUS_GCHeapHardLimitSOH` | *onaltılık değer* | .NET 5.0 |

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.HeapHardLimitLOH` | *ondalık değer* | .NET 5.0 |
| **Ortam değişkeni** | `COMPLUS_GCHeapHardLimitLOH` | *onaltılık değer* | .NET 5.0 |

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.HeapHardLimitPOH` | *ondalık değer* | .NET 5.0 |
| **Ortam değişkeni** | `COMPLUS_GCHeapHardLimitPOH` | *onaltılık değer* | .NET 5.0 |

> [!TIP]
> *Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin. Örneğin, 200 mebibytes (MIB) yığın sabit sınırı belirtmek için, değerler JSON dosyası için 209715200 ve ortam değişkeni için 0xC800000 veya C800000 olur.

### <a name="per-object-heap-limit-percents"></a>Nesne başına yığın sınırı yüzdesi

GC 'nin izin verilen yığın kullanımını nesne başına yığın temelinde belirtebilirsiniz. Farklı sayfa@@ 'ler büyük nesne yığını (LOH), küçük nesne yığını (SoH) ve sabitlenmiş nesne yığını (POH).

- , Veya ayarlarından herhangi biri için bir değer belirtirseniz `COMPLUS_GCHeapHardLimitSOHPercent` `COMPLUS_GCHeapHardLimitLOHPercent` `COMPLUS_GCHeapHardLimitPOHPercent` , ve için bir değer de belirtmeniz gerekir `COMPLUS_GCHeapHardLimitSOHPercent` `COMPLUS_GCHeapHardLimitLOHPercent` . Aksi takdirde, çalışma zamanı başlatılamaz.
- `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH` , Ve belirtildiğinde bu ayarlar yoksayılır `COMPLUS_GCHeapHardLimitPOH` .
- 1 değeri, GC 'nin bu nesne yığını için toplam fiziksel belleğin %1 ' i kullanması anlamına gelir.
- Her değerin sıfırdan büyük ve 100 ' den küçük olması gerekir. Ayrıca, üç yüzde değerinin toplamı 100 ' den az olmalıdır. Aksi takdirde, çalışma zamanı başlatılamaz.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.HeapHardLimitSOHPercent` | *ondalık değer* | .NET 5.0 |
| **Ortam değişkeni** | `COMPLUS_GCHeapHardLimitSOHPercent` | *onaltılık değer* | .NET 5.0 |

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.HeapHardLimitLOHPercent` | *ondalık değer* | .NET 5.0 |
| **Ortam değişkeni** | `COMPLUS_GCHeapHardLimitLOHPercent` | *onaltılık değer* | .NET 5.0 |

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.HeapHardLimitPOHPercent` | *ondalık değer* | .NET 5.0 |
| **Ortam değişkeni** | `COMPLUS_GCHeapHardLimitPOHPercent` | *onaltılık değer* | .NET 5.0 |

> [!TIP]
> *Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin. Örneğin, yığın kullanımını %30 olarak sınırlandırmak için değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olur.

### <a name="high-memory-percent"></a>Yüksek bellek yüzdesi

Bellek yükü, kullanımdaki fiziksel bellek yüzdesi ile belirtilir. Varsayılan olarak, fiziksel bellek yükü **%90**' a ulaştığında çöp toplama işlemi, sayfalama önlemek için atık koleksiyonları düzenleme konusunda daha agresif hale gelir. Bellek yükü %90 altındaysa, GC, daha kısa duraklamalar olan ancak toplam yığın boyutunu çok azalyan tüm çöp koleksiyonları için arka plan koleksiyonlarını tercih eder. Önemli miktarda belleğe (80GB veya daha fazla) sahip makinelerde, varsayılan yükleme eşiği %90 ile %97 arasındadır.

Yüksek bellek yükü eşiği, `COMPlus_GCHighMemPercent` ortam değişkeni veya `System.GC.HighMemoryPercent` JSON yapılandırma ayarı tarafından ayarlanabilir. Yığın boyutunu denetlemek istiyorsanız eşiği ayarlamayı düşünün. Örneğin, 64 GB bellek içeren bir makinedeki baskın işlem için, kullanılabilir belleğin %10 ' u olduğunda GC 'nin yeniden davranmasını sağlamak mantıklıdır. Ancak, daha küçük işlemler için, örneğin yalnızca 1 GB bellek tüketen bir işlem, kullanılabilir belleğin %10 ' dan az olan GC çalıştırılabilir. Bu daha küçük süreçler için eşiği daha yüksek olarak ayarlamayı düşünün. Öte yandan, büyük işlemlerin daha küçük yığın boyutlarına sahip olmasını istiyorsanız (kullanılabilir fiziksel bellek miktarı olsa bile), bu eşiği düşürmek GC 'nin yığını daha erken sıkıştırmak için etkili bir şekilde tepki vermesini sağlar.

> [!NOTE]
> Bir kapsayıcıda çalışan süreçler için, GC fiziksel belleği kapsayıcı sınırına göre değerlendirir.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.HighMemoryPercent` | *ondalık değer* | .NET 5.0 |
| **Ortam değişkeni** | `COMPlus_GCHighMemPercent` | *onaltılık değer* | .NET Core 3.0<br/> .NET Framework 4.7.2 |

> [!TIP]
> *Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin. Örneğin, yüksek bellek eşiğini %75 olarak ayarlamak için, değerler JSON dosyası için 75 ve ortam değişkeni için 0x4B veya 4B olacaktır.

### <a name="retain-vm"></a>VM 'yi koruma

- Silinmesi gereken segmentlerin ileride kullanılmak üzere bir bekleme listesine mi yerleştirileceğini, yoksa işletim sistemine (OS) geri mi bırakılacağını yapılandırır.
- Varsayılan: kesimleri işletim sistemine geri bırakın. Bu değeri değerine ayarlamaya eşdeğerdir `false` .

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.RetainVM` | `false` -işletim sistemine yayın<br/>`true` -bekleme durumuna koy | .NET Core 1,0 |
| **MSBuild özelliği** | `RetainVMGarbageCollection` | `false` -işletim sistemine yayın<br/>`true` -bekleme durumuna koy | .NET Core 1,0 |
| **Ortam değişkeni** | `COMPlus_GCRetainVM` | `0` -işletim sistemine yayın<br/>`1` -bekleme durumuna koy | .NET Core 1,0 |

#### <a name="examples"></a>Örnekler

*runtimeconfig.js* dosya:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a>Büyük sayfalar

- Bir yığın sabit sınırı ayarlandığında büyük sayfaların kullanılıp kullanılmayacağını belirtir.
- Varsayılan: bir yığın sabit sınırı ayarlandığında büyük sayfalar kullanmayın. Bu değeri değerine ayarlamaya eşdeğerdir `0` .
- Bu bir deneysel ayardır.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | Yok | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_GCLargePages` | `0` -devre dışı<br/>`1` -etkin | .NET Core 3.0 |

## <a name="allow-large-objects"></a>Büyük nesnelere izin ver

- Toplam boyuttaki 2 gigabayttan (GB) büyük olan diziler için 64 bitlik platformlarda çöp toplayıcı desteğini yapılandırır.
- Varsayılan: GC 2 GB 'tan büyük dizileri destekler. Bu değeri değerine ayarlamaya eşdeğerdir `1` .
- Bu seçenek, .NET 'in gelecek bir sürümünde kullanımdan kalkabilir.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | Yok | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_gcAllowVeryLargeObjects` | `1` -etkin<br/> `0` -devre dışı | .NET Core 1,0 |
| **.NET Framework içinapp.config** | [gcAllowVeryLargeObjects](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | `1` -etkin<br/> `0` -devre dışı | .NET Framework 4.5 |

## <a name="large-object-heap-threshold"></a>Büyük nesne yığın eşiği

- Nesnelerin büyük nesne yığınında (LOH) geçmesine neden olan eşik boyutunu bayt cinsinden belirtir.
- Varsayılan eşik 85.000 bayttır.
- Belirttiğiniz değer varsayılan eşikten büyük olmalıdır.

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | `System.GC.LOHThreshold` | *ondalık değer* | .NET Core 1,0 |
| **Ortam değişkeni** | `COMPlus_GCLOHThreshold` | *onaltılık değer* | .NET Core 1,0 |
| **.NET Framework içinapp.config** | [GCLOHThreshold](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | *ondalık değer* |  .NET Framework 4.8 |

Örnek:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> *Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin. Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin. Örneğin, 120.000 baytlık bir eşik boyutu ayarlamak için, değerler JSON dosyası için 120000, ve ortam değişkeni için 0x1D4C0 ya da 1D4C0 olur.

## <a name="standalone-gc"></a>Tek başına GC

- Çalışma zamanının yüklemeyi amaçladığı çöp toplayıcısını içeren kitaplığın yolunu belirtir.
- Daha fazla bilgi için bkz. [tek BAŞıNA GC yükleyici tasarımı](https://github.com/dotnet/runtime/blob/main/docs/design/features/standalone-gc-loading.md).

| | Ayar adı | Değerler | Sunulan sürüm |
| - | - | - | - |
| **Üzerinderuntimeconfig.js** | Yok | Yok | Yok |
| **Ortam değişkeni** | `COMPlus_GCName` | *string_path* | .NET Core 2.0 |
