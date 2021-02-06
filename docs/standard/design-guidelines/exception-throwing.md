---
description: 'Hakkında daha fazla bilgi edinin: özel durum atma'
title: Özel Durum Oluşturma
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: b1cf7a4eecc32a9f76ea06c47dd6c16d3afe5470
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642143"
---
# <a name="exception-throwing"></a>Özel Durum Oluşturma

Özel durum-bu bölümde açıklanan oluşturma yönergeleri, yürütme hatası anlamı için iyi bir tanım gerektirir. Yürütme hatası, bir üye için tasarlandıkları şeyi (üye adının ne kadar gösterdiği) yapamayacağı zaman oluşur. Örneğin, `OpenFile` Yöntem çağırana bir açık dosya tutamacı döndüremez, bir yürütme hatası olarak kabul edilir.

 Çoğu geliştirici, sıfıra bölme veya null başvurular gibi kullanım hataları için özel durumları kullanma konusunda rahat hale gelmiştir. Çerçevede, yürütme hataları da dahil olmak üzere tüm hata koşulları için özel durumlar kullanılır.

 ❌ Hata kodlarını döndürmeyin.

 Özel durumlar, çerçeveler içindeki hataların bildirilme yöntemidir.

 özel durumlar oluşturarak rapor yürütme hatalarıyla ✔️.

 ✔️, `System.Environment.FailFast` kodunuz daha fazla yürütme için güvenli olmayan bir durumla karşılaştığında bir özel durum oluşturmak yerine (.NET Framework 2,0 özelliği) işlemi SONLANDıRARAK deneyin.

 ❌ Mümkünse normal denetim akışı için özel durumlar kullanmayın.

 Olası yarış koşullarına sahip sistem arızaları ve işlemler haricinde, çerçeve tasarımcıları, kullanıcıların özel durum oluşturmayan kodlar yazabilmesi için API 'Ler tasarlaması gerekir. Örneğin, kullanıcılar özel durum oluşturmayan bir kod yazabilmesi için bir üyeyi çağırmadan önce önkoşulları denetlemek için bir yol sağlayabilirsiniz.

 Başka bir üyenin ön koşulları 'nı denetlemek için kullanılan üye, genellikle test edici olarak adlandırılır ve işi gerçekten yapan üyeye bir doer denir.

 Tester-Doer deseninin kabul edilemez bir performans yükü olduğu durumlar vardır. Bu gibi durumlarda, bu şekilde çağrılan Try-Parse deseninin göz önünde bulundurulmaları gerekir (daha fazla bilgi için bkz. [özel durumlar ve performans](exceptions-and-performance.md) ).

 ✔️ özel durum oluşturma performansı etkilerini göz önünde bulundurun. Saniyede 100 ' den yüksek olan throw ücretleri, çoğu uygulamanın performansını önemli ölçüde etkileyebilir.

 ✔️, üye sözleşmesinin ihlal edildiği (sistem hatası yerine) ve bunları sözleşmenin bir parçası olarak kabul eden, genel olarak çağrılabilir Üyeler tarafından oluşturulan tüm özel durumları belgeleyin.

 Sözleşmenin bir parçası olan özel durumlar bir sürümden sonrakine değişmemelidir (yani, özel durum türü değişmemelidir ve yeni özel durumlar eklenmemelidir).

 ❌ Herhangi bir seçeneğe göre oluşturabilecek veya olmayan ortak üyelere sahip değilsiniz.

 ❌ Dönüş değeri veya bir parametre olarak özel durumlar döndüren ortak üyelere sahip DEĞILDIR `out` .

 Özel durum tabanlı hata raporlama avantajlarının çoğunu yapmak yerine ortak API 'lerden özel durumlar döndürme.

 ✔️ özel durum Oluşturucu yöntemleri kullanmayı düşünün.

 Farklı yerlerden aynı özel durumu oluşturmak yaygındır. Kod blobunun önüne geçmek için özel durumlar oluşturan ve özelliklerini başlatacak yardımcı yöntemleri kullanın.

 Ayrıca, özel durum oluşturan Üyeler satır içine alınır. Throw deyiminizi oluşturucunun içinde taşımak üyenin satır içine eklenmesine izin verebilir.

 ❌ Özel durum filtresi bloklarından özel durumlar atamayın.

 Özel durum filtresi bir özel durum harekete geçirirse, özel durum CLR tarafından yakalanır ve filtre false değerini döndürür. Bu davranış, yürütülen filtreden ayırt edilemez ve açıkça false döndürüyor ve bu nedenle hata ayıklama çok zor.

 ❌ Finally bloklarından özel durumları açıkça oluşturmaktan kaçının. Oluşturulan çağırma yöntemlerinin sonucu olarak, örtülü olarak oluşan özel durumlar kabul edilebilir.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Özel Durumlar için Tasarım Yönergeleri](exceptions.md)
