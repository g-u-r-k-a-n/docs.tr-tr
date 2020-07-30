---
title: Temsilcileri kullanma-C# Programlama Kılavuzu
description: Temsilcileri nasıl kullanacağınızı öğrenin. Temsilciler, bir yöntemi güvenli bir şekilde kapsülleyen nesne odaklı, tür güvenli ve güvenli bir tür.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: a9b625b8c0785ed2f446be27c11dc76108bc4bce
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302158"
---
# <a name="using-delegates-c-programming-guide"></a>Temsilcileri Kullanma (C# Programlama Kılavuzu)

[Temsilci](../../language-reference/builtin-types/reference-types.md) , bir yöntemi güvenli bir şekilde kapsülleyen, C ve C++ içindeki bir işlev işaretçisine benzer bir türdür. C işlev işaretçilerinden farklı olarak, temsilciler nesne odaklı, tür kullanımı güvenli ve güvenli. Temsilcinin türü, temsilcinin adı tarafından tanımlanır. Aşağıdaki örnek, `Del` bağımsız değişken olarak bir [dize](../../language-reference/builtin-types/reference-types.md) alan ve [void](../../language-reference/builtin-types/void.md)döndüren bir yöntemi kapsülleyen adlı bir temsilci bildirir:

[!code-csharp[csProgGuideDelegates#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#21)]

Temsilci nesnesi normalde, temsilcinin kaydıralacağı yöntemin adı veya [anonim bir işlevle](../statements-expressions-operators/anonymous-functions.md)oluşturulur. Bir temsilci örneği oluşturulduktan sonra temsilciye yapılan bir yöntem çağrısı, bu yönteme verilen temsilci tarafından geçirilir. Çağıran tarafından temsilciye geçirilen parametreler yöntemine geçirilir ve yöntem, varsa dönüş değeri, temsilci tarafından çağırana döndürülür. Bu, temsilciyi çağırmak olarak bilinir. Örneklenen bir temsilci, Sarmalanan yöntemin kendisi gibi çağrılabilir. Örneğin:

[!code-csharp[csProgGuideDelegates#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#22)]  

[!code-csharp[csProgGuideDelegates#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#23)]

Temsilci türleri <xref:System.Delegate> .net 'teki sınıfından türetilir. Temsilci türleri [mühürlenmiş](../../language-reference/keywords/sealed.md)—, öğesinden türetilemez ve ' den özel sınıflar türetmek mümkün değildir <xref:System.Delegate> . Örneklenmiş temsilci bir nesne olduğundan, parametre olarak geçirilebilir veya bir özelliğe atanabilir. Bu, bir yöntemin bir temsilciyi bir parametre olarak kabul etmesine izin verir ve daha sonra temsilciyi daha sonra çağırabilir. Bu, zaman uyumsuz geri arama olarak bilinir ve uzun bir işlem tamamlandığında bir çağrıyı bildirmeye yönelik yaygın bir yöntemdir. Bu şekilde bir temsilci kullanıldığında, temsilciyi kullanan koda, kullanılmakta olan yöntemin uygulanması hakkında herhangi bir bilgi gerekmez. İşlevselliği, kapsülleme arabirimlerine benzer.

Geri aramaların diğer yaygın kullanımları özel bir karşılaştırma yöntemi tanımlayarak bu temsilciyi bir sıralama yöntemine geçirmektir. Çağıran kodun sıralama algoritmasının bir parçası haline gelmesine izin verir. Aşağıdaki örnek yöntem `Del` türü bir parametre olarak kullanır:

[!code-csharp[csProgGuideDelegates#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#24)]

Daha sonra, yukarıda oluşturulan temsilciyi Bu metoda geçirebilirsiniz:

[!code-csharp[csProgGuideDelegates#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#25)]

ve konsola aşağıdaki çıktıyı alın:

```console
The number is: 3
```

Temsilciyi bir soyutlama olarak kullanmanın, `MethodWithCallback` Konsolu doğrudan çağırması gerekmez; bir konsol göz önünde bulundurularak tasarlanmamalıdır. `MethodWithCallback`Yalnızca bir dizeyi hazırlayın ve dizeyi başka bir yönteme geçirin. Bu, temsilci bir yöntemin herhangi bir sayıda parametreyi kullanabilmesi nedeniyle özellikle güçlüdür.

Bir temsilci bir örnek yöntemini kaydırmak üzere oluşturulduğunda, temsilci hem örneğe hem de yöntemine başvurur. Bir temsilcinin, sarmaladığı yöntemden farklı olarak örnek türü bilgisi yoktur, bu nedenle bir temsilci, bu nesnede temsilci imzasıyla eşleşen bir yöntem olduğu sürece herhangi bir nesne türüne başvurabilir. Statik bir yöntemi kaydırmak için bir temsilci oluşturulduğunda, yalnızca yöntemine başvurur. Aşağıdaki bildirimleri dikkate alın:

[!code-csharp[csProgGuideDelegates#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#26)]

`DelegateMethod`Daha önce gösterilen statik ile birlikte, artık bir örnek tarafından sarmalanabilir üç yöntem sunuyoruz `Del` .

Bir temsilci, çağrıldığında birden fazla yöntem çağırabilir. Bu, çok noktaya yayın olarak adlandırılır. Temsilcinin Yöntemler listesine ek bir yöntem eklemek için — çağırma listesi — ekleme veya ekleme atama işleçlerini (' + ' veya ' + = ') kullanarak yalnızca iki temsilci eklenmesini gerektirir. Örneğin:

[!code-csharp[csProgGuideDelegates#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#27)]

Bu noktada,, `allMethodsDelegate` ve, çağırma listesinde üç yöntem bulunur —, `Method1` `Method2` ve `DelegateMethod` . Özgün üç temsilci,, `d1` `d2` ve, `d3` değişmeden kalır. `allMethodsDelegate`Çağrıldığında, üç yöntemin tümü sırasıyla çağrılır. Temsilci başvuru parametreleri kullanıyorsa, başvuru her üç yöntemin her birine sırayla geçirilir ve bir yönteme göre yapılan değişiklikler sonraki yönteme göre görünür. Metotlardan herhangi biri, yöntemi içinde yakalanmayan bir özel durum oluşturduğunda, bu özel durum temsilci çağıranına geçirilir ve çağrı listesinde sonraki Yöntemler çağrılmaz. Temsilcinin dönüş değeri ve/veya out parametreleri varsa, çağrılan son yöntemin dönüş değerini ve parametrelerini döndürür. Çağırma listesinden bir yöntemi kaldırmak için [çıkarma veya çıkarma atama işleçlerini](../../language-reference/operators/subtraction-operator.md) ( `-` veya `-=` ) kullanın. Örneğin:

[!code-csharp[csProgGuideDelegates#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#28)]

Temsilci türleri öğesinden türetildiğinden `System.Delegate` , bu sınıf tarafından tanımlanan Yöntemler ve Özellikler temsilci üzerinde çağrılabilir. Örneğin, bir temsilcinin çağrı listesindeki Yöntem sayısını bulmak için şunu yazabilirsiniz:

[!code-csharp[csProgGuideDelegates#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#29)]

Çağırma listesinde birden fazla metodu olan temsilciler <xref:System.MulticastDelegate> , bir alt sınıfı olan öğesinden türetilir `System.Delegate` . Yukarıdaki kod, her iki sınıf de desteklediği için her iki durumda da çalışmaktadır `GetInvocationList` .

Çok noktaya yayın temsilcileri, yoğun şekilde olay İşlemede kullanılır. Olay kaynak nesneleri olay bildirimlerini, bu olayı almak için kaydedilen alıcı nesnelerine gönderir. Bir olaya kaydolmak için alıcı, olayı işlemek için tasarlanan bir yöntem oluşturur, ardından bu yöntem için bir temsilci oluşturur ve temsilciyi olay kaynağına geçirir. Kaynak, olay gerçekleştiğinde temsilciyi çağırır. Temsilci daha sonra olay verilerini teslim eden, alıcı üzerinde olay işleme yöntemini çağırır. Belirli bir olayın temsilci türü olay kaynağı tarafından tanımlanır. Daha fazla bilgi için bkz. [Olaylar](../events/index.md).

Derleme zamanında atanan iki farklı türün temsilcilerin karşılaştırılması, derleme hatasına neden olur. Temsilci örnekleri türü statik olarak varsa `System.Delegate` , karşılaştırmaya izin verilir, ancak çalışma zamanında false döndürür. Örneğin:

[!code-csharp[csProgGuideDelegates#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#30)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Temsilciler](./index.md)
- [Temsilcilerde Varyans Kullanma](../concepts/covariance-contravariance/using-variance-in-delegates.md)
- [Temsilcilerde Varyans](../concepts/covariance-contravariance/variance-in-delegates.md)
- [İşlev ve Eylem Genel Temsilcileri için Varyans Kullanma](../concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
- [Ekinlikler](../events/index.md)
