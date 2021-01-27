---
title: Oluşturucular kullanma-C# Programlama Kılavuzu
description: Bu örnek, C# ' deki New işleci kullanılarak bir sınıfın nasıl örneklendiği gösterilmektedir. Basit Oluşturucu, bellek yeni nesne için ayrıldıktan sonra çağrılır.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 161c243f16f6705fa8fcf79360f92a74e4d0b27b
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899262"
---
# <a name="using-constructors-c-programming-guide"></a>Oluşturucular Kullanma (C# Programlama Kılavuzu)

Bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/builtin-types/struct.md) oluşturulduğunda, Oluşturucusu çağırılır. Oluşturucular, sınıf veya struct ile aynı ada sahiptir ve genellikle yeni nesnenin veri üyelerini başlatır.  
  
 Aşağıdaki örnekte, adlı bir sınıf `Taxi` basit bir Oluşturucu kullanılarak tanımlanmıştır. Bu sınıf daha sonra [New](../../language-reference/operators/new-operator.md) işleciyle oluşturulur. `Taxi`Oluşturucu, `new` Yeni nesne için bellek ayrıldıktan hemen sonra operatör tarafından çağrılır.  
  
 [!code-csharp[TaxiExample#1](snippets/using-constructors/Program.cs#1)]
  
 *Parametresiz Oluşturucu* olarak hiçbir parametre alan bir oluşturucuya. Parametresiz oluşturucular, bir nesne işleci kullanılarak oluşturulduğunda `new` ve için bağımsız değişken sağlanamadığında çağrılır `new` . Daha fazla bilgi için bkz. [örnek oluşturucular](./instance-constructors.md).  
  
 Sınıf [statik](../../language-reference/keywords/static.md)olmadığı takdirde, oluşturucuları olmayan sınıflara sınıf örneğini etkinleştirmek Için C# derleyicisi tarafından ortak parametresiz bir Oluşturucu verilirler. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).  
  
 Aşağıdaki gibi, oluşturucuyu özel yaparak bir sınıfın örneğinin oluşturulmasını engelleyebilirsiniz:  
  
 [!code-csharp[PrivateConstructor#2](snippets/using-constructors/Program.cs#2)]
  
 Daha fazla bilgi için bkz. [özel oluşturucular](./private-constructors.md).  
  
 [Yapı](../../language-reference/builtin-types/struct.md) türleri için oluşturucular Sınıf oluşturuculara benzer, ancak `structs` derleyici tarafından otomatik olarak sağlandığı için açık bir parametresiz oluşturucu içeremez. Bu Oluşturucu, içindeki her alanı `struct` [varsayılan değere](../../language-reference/builtin-types/default-values.md)başlatır. Ancak, parametresiz Oluşturucu yalnızca `struct` ile örneği belirtilmişse çağrılır `new` . Örneğin, bu kod, için parametresiz oluşturucuyu kullanır <xref:System.Int32> , böylece tamsayı başlatılmış olduğundan emin olmanız gerekir:  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Ancak, aşağıdaki kod, bir derleyici hatasına neden olur çünkü kullanmaz `new` ve başlatılmamış bir nesneyi kullanmaya çalışır:  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 Alternatif olarak, `structs` (tüm yerleşik sayısal türler dahil) tabanlı nesneler başlatılabilir veya atanabilir ve sonra aşağıdaki örnekte olduğu gibi kullanılabilir:  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Bu nedenle, bir değer türü için parametresiz oluşturucunun çağrılması gerekli değildir.  
  
 Her iki sınıf de, `structs` parametreleri alan oluşturucular tanımlayabilir. Parametreleri alan oluşturucuların bir `new` ifade veya bir [temel](../../language-reference/keywords/base.md) deyimden çağrılması gerekir. Sınıflar ve `structs` Ayrıca birden çok Oluşturucu tanımlayabilir ve parametresiz bir Oluşturucu tanımlamak gerekmez. Örneğin:  
  
 [!code-csharp[EmployeeExample#3](snippets/using-constructors/Program.cs#3)]
  
 Bu sınıf aşağıdaki deyimlerden herhangi biri kullanılarak oluşturulabilir:  
  
 [!code-csharp[InstantiatingEmployeeConstructors#4](snippets/using-constructors/Program.cs#4)]
  
 Bir Oluşturucu, `base` bir temel sınıfın yapıcısını çağırmak için anahtar sözcüğünü kullanabilir. Örneğin:  
  
 [!code-csharp[ManagerInheritingEmployee#5](snippets/using-constructors/Program.cs#5)]
  
 Bu örnekte, Oluşturucu için blok yürütülmeden önce temel sınıfın Oluşturucusu çağırılır. `base`Anahtar sözcüğü parametresiz ya da olmadan kullanılabilir. Oluşturucuya yönelik parametreler `base` , bir ifadenin parçası olarak veya için parametre olarak kullanılabilir. Daha fazla bilgi için bkz. [Base](../../language-reference/keywords/base.md).  
  
 Türetilmiş bir sınıfta, bir temel sınıf Oluşturucu anahtar sözcüğü kullanılarak açıkça çağrılmamasından, varsa `base` parametresiz Oluşturucu örtük olarak çağırılır. Bu, aşağıdaki Oluşturucu bildirimlerinin etkili bir şekilde aynı olduğu anlamına gelir:  
  
 [!code-csharp[ManagerImplicitlyCallingParameterlessBaseConstructor#6](snippets/using-constructors/Program.cs#6)]
  
 [!code-csharp[ManagerExplicitlyCallingParameterlessBaseConstructor#7](snippets/using-constructors/Program.cs#7)]
  
 Bir temel sınıf parametresiz bir Oluşturucu sunmuyor ise, türetilmiş sınıf kullanarak temel oluşturucuya açık bir çağrı yapmalıdır `base` .  
  
 [Bu](../../language-reference/keywords/this.md) anahtar sözcüğünü kullanarak bir Oluşturucu aynı nesnede başka bir Oluşturucu çağırabilir. Benzer şekilde `base` , parametresiz veya parametresiz olarak kullanılabilir `this` ve kurucudaki tüm parametreler, için parametre olarak `this` veya bir ifadenin parçası olarak kullanılabilir. Örneğin, önceki örnekteki ikinci Oluşturucu kullanılarak yeniden yazılabilir `this` :  
  
 [!code-csharp[EmployeeCallingConstructorInSameClass#8](snippets/using-constructors/Program.cs#8)]
  
 `this`Önceki örnekte anahtar sözcüğünün kullanılması, bu oluşturucunun çağrılmasına neden olur:  
  
 [!code-csharp[ConstructorBeingCalledByThisKeyword#9](snippets/using-constructors/Program.cs#9)]
  
 Oluşturucular [ortak](../../language-reference/keywords/public.md), [özel](../../language-reference/keywords/private.md), [korunan](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir. Bu erişim değiştiricileri, sınıfın kullanıcılarının sınıfı nasıl oluşturabileceğinize ilişkin tanımlar. Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).  
  
 Bir Oluşturucu [static](../../language-reference/keywords/static.md) anahtar sözcüğü kullanılarak statik olarak bildirilemez. Statik oluşturucular, herhangi bir statik alana erişildikten hemen önce otomatik olarak çağrılır ve genellikle statik sınıf üyelerini başlatmak için kullanılır. Daha fazla bilgi için bkz. [statik oluşturucular](./static-constructors.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [örnek oluşturucular](~/_csharplang/spec/classes.md#instance-constructors) ve [statik oluşturucular](~/_csharplang/spec/classes.md#static-constructors) bölümüne bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
