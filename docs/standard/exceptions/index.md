---
title: .NET 'te özel durumları işleme ve atma
description: .NET ' te özel durumları nasıl işleyeceğinizi ve oluşturacağınızı öğrenin. Özel durumlar, .NET işlemlerinin uygulamalarda başarısız olduğunu gösterir.
ms.date: 06/19/2018
helpviewer_keywords:
- exceptions [.NET], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET], exceptions
- exceptions [.NET], throwing
- exceptions [.NET]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
ms.openlocfilehash: 3b64b9121cc784db7d76ff5501aedfd125d0002c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876480"
---
# <a name="handling-and-throwing-exceptions-in-net"></a>.NET 'te özel durumları işleme ve atma

Uygulamalar, yürütme sırasında oluşan hataları tutarlı bir şekilde işleyebilmelidir. .NET, hataların uygulamalarda tutarlı bir şekilde bildirimde bulunmak için bir model sağlar: .NET işlemleri özel durumlar oluşturarak hatanın başarısız olduğunu gösterir.

## <a name="exceptions"></a>Özel durumlar

Bir özel durum, çalıştırılan bir program tarafından karşılaşılan herhangi bir hata durumu veya beklenmedik davranıştır. Kodunuzda veya çağırdığınız kodda (örneğin, paylaşılan bir kitaplık), kullanılamayan işletim sistemi kaynaklarıyla, çalışma zamanının karşılaştığı beklenmeyen koşullar (doğrulanamayan kod gibi) veya benzeri bir hata nedeniyle özel durumlar oluşturulabilir. Uygulamanız bu koşullardan bazılarını kurtarabilir, ancak başkalarından daha fazlasını yapabilir. Çoğu uygulama özel durumundan kurtarabilseniz de, çoğu çalışma zamanı özel durumu ' nu kurtaramazsınız.

.NET ' te, özel durum sınıfından devralan bir nesnedir <xref:System.Exception?displayProperty=nameWithType> . Bir sorunun oluştuğu bir kod alanından bir özel durum oluşur. Özel durum, uygulama onu işleyene veya program sonlanana kadar yığını iletilir.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Özel durumlar ve geleneksel hata işleme yöntemleri karşılaştırması

Geleneksel olarak, bir dilin hata işleme modeli, hataların hataları tespit etme ve işleyicileri bulma ve işletim sistemi tarafından sunulan hata işleme mekanizması üzerinde, dilin benzersiz yolunu ortadan kaldırabilir. .NET özel durum işlemeyi uygulayan yol aşağıdaki avantajları sağlar:

- Özel durum oluşturma ve işleme, .NET programlama dilleri için aynı şekilde geçerlidir.

- Özel durumları işlemek için belirli bir dil sözdizimi gerektirmez, ancak her dilin kendi sözdizimini tanımlamasına izin verir.

- Özel durumlar işlem ve hatta makine sınırları arasında oluşturulabilir.

- Özel durum işleme kodu, program güvenilirliğini artırmak için bir uygulamaya eklenebilir.

Özel durumlar, dönüş kodları gibi diğer hata bildirimi yöntemlerine ilişkin avantajlar sunar. Bir özel durum oluşursa ve bu işlemi işlemezseniz, çalışma zamanı uygulamanızı sonlandırır. Geçersiz değerler, hata dönüş kodu denetimi başarısız olan kodun bir sonucu olarak sisteme yayılmaya devam eder.

## <a name="common-exceptions"></a>Sık karşılaşılan özel durumlar

Aşağıdaki tablo, bazı yaygın özel durumları, bunlara neden olabilecek örneklere örnek olarak listelemektedir.

| Özel durum türü | Açıklama | Örnek |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | Tüm özel durumlar için temel sınıf. | Hiçbiri (Bu özel durumun türetilmiş bir sınıfını kullanın). |
| <xref:System.IndexOutOfRangeException> | Çalışma zamanı tarafından yalnızca bir dizi yanlış dizin oluşturulduğunda oluşturulur. | Dizinin geçerli aralığının dışında dizin oluşturma: <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | Çalışma zamanı tarafından yalnızca null bir nesneye başvuruluyorsa oluşturulur. | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | Geçersiz bir durumda olan yöntemler tarafından oluşturuldu. | `Enumerator.MoveNext()`Temel alınan koleksiyondan bir öğe kaldırıldıktan sonra çağrılıyor. |
| <xref:System.ArgumentException> | Tüm bağımsız değişken özel durumları için temel sınıf. | Hiçbiri (Bu özel durumun türetilmiş bir sınıfını kullanın). |
| <xref:System.ArgumentNullException> | Bağımsız değişkenin null olması için izin verilmeyen yöntemler tarafından oluşturuldu. | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | Bağımsız değişkenlerin belirli bir aralıkta olduğunu doğrulayan yöntemler tarafından oluşturulur. | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durum sınıfı ve özellikleri](exception-class-and-properties.md)
- [Nasıl yapılır: Özel Durumları Yakalamak için Try-Catch Bloğu Kullanma](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [Nasıl yapılır: Bir Catch Bloğunda Belirli Özel Durumları Kullanma](how-to-use-specific-exceptions-in-a-catch-block.md)
- [Nasıl yapılır: Açıkça Özel Durumlar Oluşturma](how-to-explicitly-throw-exceptions.md)
- [Nasıl yapılır: Kullanıcı Tanımlı Özel Durumlar Oluşturma](how-to-create-user-defined-exceptions.md)
- [Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma](using-user-filtered-exception-handlers.md)
- [Nasıl yapılır: Finally Bloklarını Kullanma](how-to-use-finally-blocks.md)
- [COM Birlikte Çalışması Özel Durumlarını İşleme](handling-com-interop-exceptions.md)
- [Özel Durumlar için En İyi Yöntemler](best-practices-for-exceptions.md)
- [Çalışma zamanındaki özel durumları öğrenmek için her dev gerekir](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/botr/exceptions.md)
