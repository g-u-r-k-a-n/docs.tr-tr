---
title: Main () ve komut satırı bağımsız değişkenleri-C# Programlama Kılavuzu
description: Ana () ve komut satırı bağımsız değişkenleri hakkında bilgi edinin. ' Main ' yöntemi çalıştırılabilir programın giriş noktasıdır.
ms.date: 03/08/2021
f1_keywords:
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: 05b2030133ca83cf87de7110f820eaad38fad756
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480192"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main () ve komut satırı bağımsız değişkenleri (C# Programlama Kılavuzu)

`Main`Yöntemi, bir C# uygulamasının giriş noktasıdır. (Kitaplıklar ve hizmetler bir `Main` giriş noktası olarak bir yöntem gerektirmez.) Uygulama başlatıldığında, `Main` yöntemi çağrılan ilk yöntemdir.

C# programında yalnızca bir giriş noktası olabilir. Yöntemine sahip birden fazla sınıfınız varsa `Main` , giriş noktası olarak hangi yöntemin kullanılacağını belirtmek için programınızı **StartupObject** derleyici seçeneğiyle derlemeniz gerekir `Main` . Daha fazla bilgi için bkz. [ **StartupObject** (C# derleyici seçenekleri)](../../language-reference/compiler-options/advanced.md#mainentrypoint-or-startupobject).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

C# 9 ' dan başlayarak, `Main` `Main` Aşağıdaki örnekte olduğu gibi yöntemini atlayabilir ve c# deyimlerini yönteminde olduğu gibi yazabilirsiniz:

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

Örtük bir giriş noktası yöntemiyle uygulama kodu yazma hakkında daha fazla bilgi için bkz. [üst düzey deyimler](top-level-statements.md).

## <a name="overview"></a>Genel Bakış

- `Main`Yöntemi, çalıştırılabilir programın giriş noktasıdır; program denetiminin başladığı ve bittiği yerdir.
- `Main` bir sınıf veya yapı içinde bildirilmiştir. `Main`[statik](../../language-reference/keywords/static.md) olmalı ve [genel](../../language-reference/keywords/public.md)olmamalıdır. (Önceki örnekte, [Private](../../language-reference/keywords/private.md)'ın varsayılan erişimini alır.) Kapsayan sınıf veya yapının statik olması gerekmez.
- `Main``void` `int` C# 7,1, `Task` veya dönüş türü ile başlayan, veya, ya da olabilir `Task<int>` .
- Ve yalnızca `Main` bir `Task` veya döndürürse `Task<int>` , bildirimi, `Main` [`async`](../../language-reference/keywords/async.md) değiştiricisini içerebilir. Bunun özellikle bir yöntemi dışladığı unutulmamalıdır `async void Main` .
- `Main`Yöntemi `string[]` komut satırı bağımsız değişkenleri içeren bir parametre ile veya olmadan bildirilemez. Windows uygulamaları oluşturmak için Visual Studio kullanırken, parametresini el ile ekleyebilir veya <xref:System.Environment.GetCommandLineArgs> [komut satırı bağımsız değişkenlerini](command-line-arguments.md)almak için yöntemini kullanabilirsiniz. Parametreler, sıfır dizinli komut satırı bağımsız değişkenleri olarak okunurdur. C ve C++ ' dan farklı olarak, programın adı dizideki ilk komut satırı bağımsız değişkeni olarak değerlendirilmez `args` , ancak yöntemin ilk öğesidir <xref:System.Environment.GetCommandLineArgs> .

Geçerli imzaların listesi aşağıda verilmiştir `Main` :

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

Yukarıdaki örneklerin hepsi ortak erişimci değiştiricisini kullanır. Bu tipik, ancak gerekli değildir.

`async`Ve ' nin eklenmesi `Task` , `Task<int>` konsol uygulamalarının `await` ' de başlaması ve zaman uyumsuz işlemler gerektiğinde program kodunu basitleştirir `Main` .

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Yöntemler](../classes-and-structs/methods.md)
- [C# programı içinde](../inside-a-program/index.md)
