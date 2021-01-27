---
title: Özel oluşturucular-C# Programlama Kılavuzu
description: Özel Oluşturucu, bir nesnenin nasıl oluşturulabileceğini kısıtlamak için kullanılan C# içindeki özel bir örnek oluşturucudur. Bunlar, fabrika yöntemleriyle veya diğer yapım deyimleri ile kullanılabilir.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 980a638fbe6250b3d47a3effc7cbad5ec57fbcad
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899418"
---
# <a name="private-constructors-c-programming-guide"></a>Özel Oluşturucular (C# Programlama Kılavuzu)

Özel Oluşturucu özel bir örnek oluşturucudur. Genellikle yalnızca statik üyeler içeren sınıflarda kullanılır. Bir sınıfta bir veya daha fazla özel Oluşturucu varsa ve ortak oluşturucu yoksa, diğer sınıflar (iç içe sınıflar hariç) bu sınıfın örneklerini oluşturamaz. Örneğin:  
  
 [!code-csharp[ClassWithPrivateConstructorExample#1](snippets/private-constructors/Program.cs#1)]
  
 Boş oluşturucunun bildirimi parametresiz bir oluşturucunun otomatik olarak oluşturulmasını engeller. Oluşturucu ile bir erişim değiştiricisi kullanmıyorsanız, varsayılan olarak hala Private olacağını unutmayın. Ancak, [özel](../../language-reference/keywords/private.md) değiştirici genellikle sınıfın örneklendirilmediğini açık hale getirmek için açıkça kullanılır.  
  
 Özel oluşturucular, sınıf gibi örnek alan veya yöntem olmadığında <xref:System.Math> veya bir sınıfın örneğini almak için bir yöntem çağrıldığında bir sınıfın örneklerinin oluşturulmasını engellemek için kullanılır. Sınıftaki tüm yöntemler statikse, tüm sınıfı statik hale getirmeyi düşünün. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Örnek  

 Aşağıda özel Oluşturucu kullanan bir sınıf örneği verilmiştir.  
  
 [!code-csharp[CounterClassWithPrivateConstructor#2](snippets/private-constructors/Program.cs#2)]
  
 Aşağıdaki deyimin örnek olarak açıklama eklendiğinde, koruma düzeyi nedeniyle Oluşturucu erişilemediğinden bir hata üretir:  
  
 [!code-csharp[ErrorInstantiatingUsingPrivateConstructor#13](snippets/private-constructors/Program.cs#3)]
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [özel oluşturucular](~/_csharplang/spec/classes.md#private-constructors) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
- [özelleştirme](../../language-reference/keywords/private.md)
- [genel](../../language-reference/keywords/public.md)
