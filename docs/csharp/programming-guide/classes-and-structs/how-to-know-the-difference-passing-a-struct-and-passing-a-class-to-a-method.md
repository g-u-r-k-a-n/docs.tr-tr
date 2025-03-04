---
title: Bir struct geçirme ve bir yönteme sınıf başvurusu geçirme arasındaki farkı nasıl anlarsınız-C# Programlama Kılavuzu
description: Bir yapının bir yönteme geçirilmesi, sınıf örneğini C# içindeki bir yönteme geçirmekten farklıdır. Bu örnek, değer ile geçirilen struct ve sınıf örneğini gösterir.
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: a4d969617b450fcd788764e97afe3aa1ff19a48c
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898807"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Bir struct geçirme ve bir yönteme sınıf başvurusu geçirme arasındaki farkı nasıl anlarsınız (C# Programlama Kılavuzu)

Aşağıdaki örnek bir [yapının](../../language-reference/builtin-types/struct.md) bir yönteme nasıl geçtiğini gösterir bir yönteme nasıl bir [sınıf](../../language-reference/keywords/class.md) örneği geçirmekten farklıdır. Örnekte, bağımsız değişkenlerin (struct ve sınıf örneği) her ikisi de değere göre geçirilir ve her iki yöntem de bağımsız değişkenin bir alanının değerini değiştirir. Ancak, bir yapı geçirdiğinizde geçirilen özellikler, bir sınıfın örneğini geçirdiğinizde geçirilen verilerden farklı olduğundan, iki yöntemin sonuçları aynı değildir.  
  
 Bir struct bir [değer türü](../../language-reference/builtin-types/value-types.md)olduğundan, bir yapıya [değere göre](./passing-value-type-parameters.md) bir yönteme geçirdiğinizde, yöntemi struct bağımsız değişkeninin bir kopyası üzerinde alır ve çalışır. Yöntemi çağıran yöntemde orijinal yapıya erişemez ve bu nedenle herhangi bir şekilde değiştirilemez. Yöntemi yalnızca kopyayı değiştirebilir.  
  
 Bir sınıf örneği, bir değer türü değil [başvuru türüdür](../../language-reference/keywords/reference-types.md). Bir [başvuru türü değere göre](./passing-reference-type-parameters.md) bir yönteme geçirildiğinde, yöntemi sınıf örneğine başvurunun bir kopyasını alır. Diğer bir deyişle, çağrılan yöntem örneğin adresinin bir kopyasını alır ve çağırma yöntemi örneğin özgün adresini korur. Çağıran yöntemdeki sınıf örneği bir adrese sahiptir, çağrılan yöntemdeki parametresi adresin bir kopyasına sahiptir ve her iki adres de aynı nesneye başvurur. Parametresi yalnızca adresin bir kopyasını içerdiğinden, çağrılan yöntem çağıran yöntemde sınıf örneğinin adresini değiştiremiyor. Ancak çağrılan yöntem, sınıf üyelerine hem özgün adresin hem de adres başvurusunun kopyasına erişmek için adresin kopyasını kullanabilir. Çağrılan yöntem bir sınıf üyesini değiştirirse, çağıran yöntemdeki özgün sınıf örneği de değişir.  
  
 Aşağıdaki örnek çıktıda fark gösterilmektedir. `willIChange`Sınıf örneği alanının değeri, `ClassTaker` metodu, sınıf örneğinin belirtilen alanını bulmak için parametresindeki adresi kullandığından yöntemi çağrısıyla değiştirilir. `willIChange` `StructTaker` Bağımsız değişkenin değeri, kendi adresinin bir kopyası değil, yapısının bir kopyası olduğundan, çağırma yöntemindeki yapının alanı, yöntemi çağrısıyla değiştirilmez. `StructTaker` kopyayı değiştirir ve çağrısı tamamlandığında kopya kaybedilir `StructTaker` .  
  
## <a name="example"></a>Örnek  

 [!code-csharp[PassingStructVsClass](snippets/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method/Program.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar](./classes.md)
- [Yapı türleri](../../language-reference/builtin-types/struct.md)
- [Parametreleri Geçirme](./passing-parameters.md)
