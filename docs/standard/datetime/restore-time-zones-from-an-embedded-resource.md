---
title: 'Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: cd2119d6d22f3f676b7167ed545aeb058123cfb5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122197"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme

Bu konuda, bir kaynak dosyasına kaydedilmiş saat dilimlerinin nasıl geri yükleneceği açıklanmaktadır. Saat dilimlerini kaydetme hakkında bilgi ve yönergeler için bkz. [nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Bir TimeZoneInfo nesnesinin katıştırılmış bir kaynaktan serisini kaldırma

1. Alınacak saat dilimi özel bir saat dilimi değilse, <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metodunu kullanarak örneğini oluşturmaya çalışın.

2. Katıştırılmış kaynak dosyasının tam adını ve kaynak dosyasını içeren derlemeye bir başvuru geçirerek bir <xref:System.Resources.ResourceManager> nesnesi örneği oluşturun.

   Gömülü kaynak dosyasının tam adını belirleyemeziz, derlemenin bildirimini incelemek için [ıldadsm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) kullanın. Bir `.mresource` girdisi kaynağı tanımlar. Örnekte, kaynağın tam adı `SerializeTimeZoneData.SerializedTimeZones`.

   Kaynak dosyası saat dilimi örnek oluşturma kodunu içeren bütünleştirilmiş koda katıştırılmışsa, `static` (`Shared` Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntemini çağırarak buna bir başvuru alabilirsiniz.

3. <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemine yapılan çağrı başarısız olursa veya özel bir saat dilimi örneklenilmelidir, <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> yöntemini çağırarak serileştirilmiş saat dilimini içeren bir dize alın.

4. <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemini çağırarak saat dilimi verilerinin serisini kaldırma.

## <a name="example"></a>Örnek

Aşağıdaki örnek gömülü bir .NET XML kaynak dosyasında depolanan bir <xref:System.TimeZoneInfo> nesnesini serileştirir.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Bu kod, uygulamanın gerektirdiği bir <xref:System.TimeZoneInfo> nesnesinin mevcut olduğundan emin olmak için özel durum işleme gösterir. İlk olarak, <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metodunu kullanarak kayıt defterinden alarak bir <xref:System.TimeZoneInfo> nesnesi örneğini oluşturmaya çalışır. Saat dilimi örneklenemez, kod onu katıştırılmış kaynak dosyasından alır.

Özel saat dilimlerinin (<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kullanılarak oluşturulan saat dilimleri) verileri kayıt defterinde depolanmadığı için, kod, Palmer, Antarktika için saat dilimini başlatmak üzere <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> çağırmaz. Bunun yerine, <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemini çağırmadan önce saat diliminin verilerini içeren bir dizeyi almak için hemen gömülü kaynak dosyasına bakar.

## <a name="compiling-the-code"></a>Kodu derleme

Bu örnek şunları gerektirir:

- System. Windows. Forms. dll ve System. Core. dll ' ye bir başvuru projeye eklenir.

- Aşağıdaki ad alanları içeri aktarılmalıdır:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
- [Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
