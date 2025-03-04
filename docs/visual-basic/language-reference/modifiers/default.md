---
description: 'Hakkında daha fazla bilgi: varsayılan (Visual Basic)'
title: Varsayılan
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: fe135df4f29ae3c4064c97d4f2789be7f4f3d8f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774609"
---
# <a name="default-visual-basic"></a>Varsayılan (Visual Basic)

Bir özelliği sınıfının, yapısının veya arabirimin varsayılan özelliği olarak tanımlar.  
  
## <a name="remarks"></a>Açıklamalar  

 Bir sınıf, yapı veya arabirim, özelliğin en az bir parametre almasını sağlayan *varsayılan özellik* olarak özelliklerinden en çok birini belirtebilir. Kod, bir üye belirtmeden bir sınıfa veya yapıya bir başvuru yapıyorsa Visual Basic, bu başvuruyu varsayılan özelliğe çözer.  
  
 Varsayılan Özellikler, kaynak kodu karakterlerinin küçük bir azalmasına neden olabilir, ancak kodunuzun okunmasını zorlaşabilir. Çağıran kod sınıfınız veya yapınız hakkında bilgi sahibi değilse, sınıf veya yapı adına bir başvuru yaptığında, başvurunun sınıfa veya yapıya ya da bir varsayılan özelliğe erişim izni verip etmediği kesin olamaz. Bu, derleyici hatalarına veya hafif çalışma zamanı mantığı hatalarına neden olabilir.  
  
 Derleyici türü denetimini olarak ayarlamak için, her zaman [katı deyimin seçeneğini](../statements/option-strict-statement.md) kullanarak varsayılan özellik hatalarının olasılığını azaltabilirsiniz `On` .  
  
 Kodunuzda önceden tanımlanmış bir sınıf veya yapı kullanmayı planlıyorsanız, bunun varsayılan bir özelliği olup olmadığını ve varsa adının ne olduğunu belirlemelisiniz.  
  
 Bu dezavantajlar nedeniyle varsayılan özellikleri tanımlamamalısınız. Kod okunabilirlik için, her zaman tüm özelliklere, hatta varsayılan özelliklere de her zaman başvurmanız gerekir.  
  
 `Default`Değiştirici Bu bağlamda kullanılabilir:  
  
 [Property Deyimi](../statements/property-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma](../../programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [Anahtar sözcükler](../keywords/index.md)
