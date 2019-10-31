---
title: 'Nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: f988616a4b2a5d8202c87e3be3cb23c7f9f1f130
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122271"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver

Belirsiz bir zaman, birden fazla Eşgüdümlü Evrensel Saat (UTC) ile eşleşen bir süredir. Saat diliminin gün ışığından yararlanma saatinden standart saate geçiş sırasında olduğu gibi saat içinde saat olarak ayarlandığında meydana gelir. Belirsiz bir süre işlenirken aşağıdakilerden birini yapabilirsiniz:

- Belirsiz saat Kullanıcı tarafından girilen bir veri öğesi ise, belirsizliği çözümlemek için bunu kullanıcıya bırakabilirsiniz.

- Saatin UTC 'ye nasıl eşlendiğini varsayımını unutmayın. Örneğin, saat diliminin standart saatinde belirsiz bir zamanın her zaman ifade edildiği varsayıladır.

Bu konu başlığı altında, kullanıcının belirsiz bir süre çözümlenme yöntemi gösterilmektedir.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Kullanıcının belirsiz bir süre çözmesine izin vermek için

1. Kullanıcı tarafından tarih ve saat girişi al.

2. Saatin belirsiz olup olmadığını anlamak için <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> yöntemini çağırın.

3. Zaman belirsiz ise, <xref:System.TimeSpan> nesne dizisini almak için <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> yöntemini çağırın. Dizideki her öğe, belirsiz saatin eşleyebileceğiniz UTC sapmasını içerir.

4. Kullanıcının istenen sapmayı seçmesini sağlayın.

5. Kullanıcı tarafından seçilen sapmayı yerel saatten çıkararak UTC Tarih ve saatini elde edin.

6. UTC Tarih ve saat değerinin <xref:System.DateTime.Kind%2A> özelliğini ayarlamak için `static` (Visual Basic .NET 'te`Shared`) <xref:System.DateTime.SpecifyKind%2A> yöntemini çağırın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, kullanıcıdan bir tarih ve saat girmesini ister ve belirsiz ise kullanıcının belirsiz saatin eşlendiği UTC saatini seçmesini sağlar.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Örnek kodun çekirdeği, UTC 'den belirsiz sürenin olası uzaklıklarını göstermek için <xref:System.TimeSpan> nesneleri dizisini kullanır. Ancak, bu uzaklıklar Kullanıcı için anlamlı değildir. Kaydırmanın anlamını netleştirmek için, kod ayrıca bir uzaklığın yerel saat diliminin standart saatini mi yoksa gün ışığından yararlanma saatini mi temsil ettiğini de not eder. Kod, <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliğinin değeriyle SAPMAYı karşılaştırarak hangi zamanın standart olduğunu ve ne zaman gündüz olduğunu belirler. Bu özellik UTC ve saat diliminin standart saati arasındaki farkı gösterir.

Bu örnekte, yerel saat dilimine yapılan tüm başvurular <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği aracılığıyla yapılır; Yerel Saat dilimi hiçbir zaman bir nesne değişkenine atanmaz. Bu önerilen bir uygulamadır çünkü <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrı, yerel saat diliminin atandığı nesneleri geçersiz kılar.

## <a name="compiling-the-code"></a>Kodu derleme

Bu örnek şunları gerektirir:

- <xref:System> ad alanı `using` ifadesiyle içeri aktarılmalıdır ( C# kodda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Nasıl yapılır: Belirsiz saatleri çözme](../../../docs/standard/datetime/resolve-ambiguous-times.md)
