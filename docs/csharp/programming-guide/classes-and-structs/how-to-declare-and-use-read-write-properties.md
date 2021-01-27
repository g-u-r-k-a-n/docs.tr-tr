---
title: Okuma yazma özelliklerini bildirme ve kullanma-C# Programlama Kılavuzu
description: C# ' de okuma/yazma özelliklerini kullanmayı öğrenin. Bu örnek, her biri get ve set erişimcilerine sahip olan iki özelliği içerir, bu nedenle Özellikler okuma/yazma olur.
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 75f3b4d6fa8595734cf1310c08281c26c829fd84
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899028"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Okuma yazma özelliklerini bildirme ve kullanma (C# Programlama Kılavuzu)

Özellikler, bir nesnenin verilerine korumasız, denetlenmeyen ve doğrulanmamış erişimle gelen riskler olmadan ortak veri üyelerinin rahatlığını sağlar. Bu, *erişimciler* aracılığıyla gerçekleştirilir: temel alınan veri üyesine değerler atayan ve alan özel yöntemler. [Set](../../language-reference/keywords/set.md) erişimcisi veri üyelerinin atanmasını sağlar ve [Get](../../language-reference/keywords/get.md) erişimcisi veri üyesi değerlerini alır.  
  
 Bu örnek `Person` , iki özelliği olan bir sınıfı gösterir: `Name` (dize) ve `Age` (int). Her iki özellik de `get` ve `set` erişimcileri sağlar, bu nedenle okuma/yazma özellikleri olarak değerlendirilir.  
  
## <a name="example"></a>Örnek  

 [!code-csharp[properties#1](snippets/how-to-declare-and-use-read-write-properties/Program.cs#1)]
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Önceki örnekte, `Name` ve `Age` özellikleri [geneldir](../../language-reference/keywords/public.md) ve hem hem de `get` erişimcisi içerir `set` . Bu, herhangi bir nesnenin bu özellikleri okumasına ve yazmasına izin verir. Ancak erişimcilerinin birini dışlamak bazen tercih edilir. Erişimci atlanırsa `set` , örneğin, özelliği salt okunurdur:  
  
 [!code-csharp[properties#2](snippets/how-to-declare-and-use-read-write-properties/Program.cs#2)]
  
 Alternatif olarak, bir erişimciye genel kullanıma sunabilirsiniz, ancak diğerini özel veya korumalı hale getirebilirsiniz. Daha fazla bilgi için bkz. [asimetrik erişimci erişilebilirliği](./restricting-accessor-accessibility.md).  
  
 Özellikler doğrulandıktan sonra, sınıfının alanları gibi kullanılabilirler. Bu, aşağıdaki deyimlerde olduğu gibi bir özelliğin değerini alırken ve ayarlarken çok doğal bir sözdizimi sağlar:  
  
 [!code-csharp[properties#3](snippets/how-to-declare-and-use-read-write-properties/Program.cs#3)]
  
 Bir özellik `set` yönteminde özel bir değişken bulunduğunu unutmayın `value` . Bu değişken, kullanıcının belirttiği değeri içerir, örneğin:  
  
 [!code-csharp[properties#4](snippets/how-to-declare-and-use-read-write-properties/Program.cs#4)]
  
 `Age`Bir nesne üzerindeki özelliği arttırmadan ilgili Temizleme sözdizimine dikkat edin `Person` :  
  
 [!code-csharp[properties#5](snippets/how-to-declare-and-use-read-write-properties/Program.cs#5)]
  
 `set` `get` Özellikleri modellemek için ayrı ve Yöntemler kullanılmışsa, eşdeğer kod şöyle görünebilir:  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 `ToString`Yöntemi bu örnekte geçersiz kılınır:  
  
 [!code-csharp[properties#6](snippets/how-to-declare-and-use-read-write-properties/Program.cs#6)]
  
 `ToString`Programda açıkça kullanılmadığına dikkat edin. Çağrılar tarafından varsayılan olarak çağrılır `WriteLine` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikler](./properties.md)
- [Sınıflar ve Yapılar](./index.md)
