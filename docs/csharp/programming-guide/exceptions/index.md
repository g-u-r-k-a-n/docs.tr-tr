---
title: Özel durumlar ve özel durum Işleme-C# Programlama Kılavuzu
description: Özel durumlar ve özel durum işleme hakkında bilgi edinin. Bu C# özellikleri, bir program çalışırken gerçekleşen beklenmedik veya olağanüstü durumlarla başa çıkmanıza yardımcı olur.
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: 245299707254c7bafb4589ee8031a107921ca2a7
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255408"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Özel Durumlar ve Özel Durum İşleme (C# Programlama Kılavuzu)

C# dilinin özel durum işleme özellikleri, bir program çalışırken oluşan beklenmedik veya olağanüstü durumlarla ilgilenmenize yardımcı olur. Özel durum işleme `try` , `catch` başarılı olmayan eylemleri denemek için,, ve anahtar kelimelerini kullanır, bu `finally` işlemin ne kadar uygun olduğuna karar verirken sorunları işleyebilir ve kaynakları daha sonra temizleyebiliriz. Özel durumlar ortak dil çalışma zamanı (CLR), .NET veya üçüncü taraf kitaplıkları tarafından veya uygulama kodu tarafından oluşturulabilir. Özel durumlar anahtar sözcüğü kullanılarak oluşturulur `throw` .

Çoğu durumda, kodunuzun doğrudan çağırdığı bir yöntem tarafından değil, çağrı yığınında daha sonra başka bir yöntem tarafından bir özel durum atılır. Bir özel durum oluştuğunda, CLR, belirli bir özel durum türü için blok içeren bir yöntemi arayarak yığını yeniden aşağı doğru `catch` çalıştırır ve bulduğu ilk bu `catch` blok yürütülür. `catch`Çağrı yığınında herhangi bir yerde uygun bir blok bulmaz, işlemi sonlandırır ve kullanıcıya bir ileti görüntüler.

Bu örnekte, bir yöntem sıfıra bölme için test eder ve hatayı yakalar. Özel durum işleme olmadan, bu program bir **Dividebysıfırlaması özel durumu** ile sonlandırılır ve işlenmemiş bir hatadır.

:::code language="csharp" source="snippets/exceptions/ExceptionTest.cs" ID="ExceptionTest":::

## <a name="exceptions-overview"></a>Özel durumlara genel bakış

Özel durumlar aşağıdaki özelliklere sahiptir:

- Özel durumlar, tüm sonunda türetilen türlerdir `System.Exception` .
- `try`Özel durumlar oluşturabilecek deyimler etrafında bir blok kullanın.
- Blokta bir özel durum oluştuktan sonra `try` Denetim akışı, çağrı yığınında herhangi bir yerde bulunan ilk ilişkili özel durum işleyicisine atlar. C# ' de, `catch` bir özel durum işleyicisini tanımlamak için anahtar sözcüğü kullanılır.
- Belirli bir özel durum için özel durum işleyicisi yoksa, program yürütmeyi bir hata iletisiyle sonlandırır.
- Bunu işleyebilmediğiniz ve uygulamayı bilinen bir durumda bırakarak bir özel durum yakalamayın. Yakalar `System.Exception` , `throw` bloğunun sonundaki anahtar sözcüğünü kullanarak yeniden oluşturun `catch` .
- Bir `catch` blok bir özel durum değişkeni tanımlıyorsa, oluşan özel durum türü hakkında daha fazla bilgi edinmek için onu kullanabilirsiniz.
- Özel durumlar, anahtar sözcüğü kullanılarak bir program tarafından açıkça oluşturulabilir `throw` .
- Özel durum nesneleri, hata hakkında, çağrı yığınının durumu ve hatanın metin açıklaması gibi ayrıntılı bilgiler içerir.
- Bir `finally` özel durum oluşsa bile bloktaki kod yürütülür. Kaynakları serbest bırakmak için bir `finally` blok kullanın, örneğin, bloğunda açılan tüm akışları veya dosyaları kapatmak `try` .
- .NET 'teki yönetilen özel durumlar, Win32 yapılandırılmış özel durum işleme mekanizmasının üzerine uygulanır. Daha fazla bilgi için, bkz. [yapılandırılmış özel durum işleme (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) ve [Win32 yapılandırılmış özel durum işleme derinlikleri üzerinde çökme kursu](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).

## <a name="c-language-specification"></a>C# Dil Belirtimi

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [özel durumlar](~/_csharplang/spec/exceptions.md) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SystemException>
- [C# anahtar sözcükleri](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Özel durumlar](../../../standard/exceptions/index.md)
