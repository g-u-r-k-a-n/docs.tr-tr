---
description: 'Daha fazla bilgi edinin: nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme'
title: 'Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], deserializing
- time zones [.NET], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: 593fb392c073ca0a3b557b7d82d430b024b3d13a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702489"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme

Bu konuda, bir kaynak dosyasına kaydedilmiş saat dilimlerinin nasıl geri yükleneceği açıklanmaktadır. Saat dilimlerini kaydetme hakkında bilgi ve yönergeler için bkz. [nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Bir TimeZoneInfo nesnesinin katıştırılmış bir kaynaktan serisini kaldırma

1. Alınacak saat dilimi özel bir saat dilimi değilse, yöntemini kullanarak örneğini oluşturmaya çalışın <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> .

2. <xref:System.Resources.ResourceManager>Katıştırılmış kaynak dosyanın tam adını ve kaynak dosyasını içeren derlemeye bir başvuru geçirerek bir nesne oluşturun.

   Gömülü kaynak dosyasının tam adını belirleyemeziz, derlemenin bildirimini incelemek için [Ildasm.exe (Il ayırıcı)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanın. Bir `.mresource` giriş, kaynağı tanımlar. Örnekte, kaynağın tam adı `SerializeTimeZoneData.SerializedTimeZones` .

   Kaynak dosyası saat dilimi örnek oluşturma kodunu içeren bütünleştirilmiş koda katıştırılmışsa, `static` ( `Shared` Visual Basic) metodunu çağırarak buna bir başvuru alabilirsiniz <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> .

3. Yöntemine yapılan çağrı <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> başarısız olursa veya özel bir saat dilimi örneklenilmelidir, yöntemini çağırarak serileştirilmiş saat dilimini içeren bir dize alın <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> .

4. Yöntemini çağırarak saat dilimi verilerinin serisini kaldırma <xref:System.TimeZoneInfo.FromSerializedString%2A> .

## <a name="example"></a>Örnek

Aşağıdaki örnek <xref:System.TimeZoneInfo> gömülü bir .NET XML kaynak dosyasında depolanan bir nesneyi seri durumdan çıkarır.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Bu kod <xref:System.TimeZoneInfo> , uygulamanın gerektirdiği bir nesnenin mevcut olduğundan emin olmak için özel durum işleme gösterir. İlk olarak <xref:System.TimeZoneInfo> , yöntemini kullanarak kayıt defterinden alarak bir nesnesi örneğini oluşturmaya çalışır <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> . Saat dilimi örneklenemez, kod onu katıştırılmış kaynak dosyasından alır.

Özel saat dilimlerinin (yöntemi kullanılarak oluşturulan saat dilimleri <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> ) verileri kayıt defterinde depolanmadığı için, kod, <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> Palmer için saat dilimini oluşturmak üzere öğesini çağırmaz, Antarktika. Bunun yerine, yöntemi çağırmadan önce saat diliminin verilerini içeren bir dizeyi almak için hemen gömülü kaynak dosyasına bakar <xref:System.TimeZoneInfo.FromSerializedString%2A> .

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek şunları gerektirir:

- System.Windows.Forms.dll ve System.Core.dll bir başvuru projeye eklenir.

- Aşağıdaki ad alanları içeri aktarılmalıdır:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
- [Saat dilimine genel bakış](time-zone-overview.md)
- [Nasıl yapılır: Saat dilimlerini eklenmiş kaynağa kaydetme](save-time-zones-to-an-embedded-resource.md)
