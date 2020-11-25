---
title: Yapı Tasarımı
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: 7bb7e63004df2eb7541ba8d4f1118ea2272db126
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730909"
---
# <a name="struct-design"></a>Yapı Tasarımı

Genel amaçlı değer türü genellikle struct, C# anahtar sözcüğü olarak adlandırılır. Bu bölüm, genel yapı tasarımı için yönergeler sağlar.

 ❌ Struct için parametresiz bir Oluşturucu sağlamakmayın.

 Bu kılavuzdan sonra, dizinin her öğesinde oluşturucuyu çalıştırmak zorunda kalmadan yapıların dizilerinin oluşturulmasına izin verir. C# ' nin yapıların parametresiz oluşturuculara sahip olduğundan emin olun.

 ❌ Kesilebilir değer türlerini tanımlamayın.

 Kesilebilir değer türlerinde birçok sorun vardır. Örneğin, bir özellik alıcısı bir değer türü döndürdüğünde, çağıran bir kopyasını alır. Kopya örtük olarak oluşturulduğundan, geliştiriciler özgün değeri değil, kopyayı değiştirmez gibi farkında olmayabilir. Ayrıca, bazı dillerin (özellikle de dinamik diller) değişebilir değer türlerini kullanarak sorunlar vardır, çünkü başvuru yapıldığında yerel değişkenler de bir kopyanın oluşturulmasına neden olur.

 ✔️ Tüm örnek verilerinin sıfıra, yanlış veya null (uygun şekilde) olarak ayarlandığı bir durumun geçerli olduğundan emin olun.

 Bu, yapıların bir dizisi oluşturulduğunda geçersiz örneklerin yanlışlıkla oluşturulmasını önler.

 <xref:System.IEquatable%601>değer türlerinde uygulama ✔️.

 <xref:System.Object.Equals%2A?displayProperty=nameWithType>Değer türlerindeki yöntemi kutulama sağlar ve yansıma kullandığından, varsayılan uygulama çok verimli değildir. <xref:System.IEquatable%601.Equals%2A> çok daha iyi performansa sahip olabilir ve bu, kutulamayı neden olmayacak şekilde uygulanabilir.

 ❌ Açıkça genişlemeyin <xref:System.ValueType> . Aslında çoğu dil bunu engeller.

 Genel olarak, yapılar çok faydalı olabilir, ancak yalnızca sık kutulanmamış küçük, tek, sabit değerler için kullanılmalıdır.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Tür tasarım yönergeleri](type.md)
- [Çerçeve tasarım yönergeleri](index.md)
- [Sınıf ile Yapı Arasında Seçim Yapma](choosing-between-class-and-struct.md)
