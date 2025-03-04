---
title: 'Nasıl yapılır: Olaylar Oluşturma ve Kullanma'
description: .NET ' te & tüketme olayları yükseltin. Özel bir temsilciyi & EventHandler temsilcisini kullanan örneklere bakın <TEventArgs> .
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET], raising
- raising events
- events [.NET], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 22e62dd8e14696273923873353b1bd19d8507ab7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697460"
---
# <a name="how-to-raise-and-consume-events"></a>Nasıl yapılır: Olaylar Oluşturma ve Kullanma

Bu konudaki örneklerde, olaylarla nasıl çalışılacağı gösterilmektedir. Bu kişiler, <xref:System.EventHandler> <xref:System.EventHandler%601> verileri içeren ve olmayan olayları göstermek için temsilci, temsilci ve özel bir temsilci örnekleri içerir.  
  
 Örnekler, [Olaylar](index.md) makalesinde açıklanan kavramları kullanır.  
  
## <a name="example"></a>Örnek  

 İlk örnek, verileri olmayan bir olayın nasıl oluşturulduğunu ve kullanıldığını gösterir. Adında bir olayı olan adlı bir sınıfı içerir `Counter` `ThresholdReached` . Bu olay, bir sayaç değeri bir eşik değerini eşitse veya aştığında tetiklenir. <xref:System.EventHandler>Olay verileri sağlanmadığından temsilci olayla ilişkilendirilir.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Örnek  

 Sonraki örnekte, veri sağlayan bir olayın nasıl oluşturulduğu ve kullanılacağı gösterilmektedir. <xref:System.EventHandler%601>Temsilci olayla ilişkilendirilir ve bir özel olay veri nesnesi örneği sağlanır.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Örnek  

 Sonraki örnekte bir olay için nasıl temsilci bildirireceğiniz gösterilmektedir. Temsilcinin adı `ThresholdReachedEventHandler` . Bu yalnızca bir çizim. Genellikle, ya da temsilcisini kullanabilmeniz için bir olay için temsilci bildirmeniz gerekmez <xref:System.EventHandler> <xref:System.EventHandler%601> . Bir temsilciyi yalnızca nadir senaryolar halinde bildirmeniz gerekir. Örneğin, sınıfınızın genel türler kullanamaz eski kod için kullanılabilir hale getirilmesi.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](index.md)
