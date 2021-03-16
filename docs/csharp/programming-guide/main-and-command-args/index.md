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
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="450d6-104">Main () ve komut satırı bağımsız değişkenleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="450d6-104">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="450d6-105">`Main`Yöntemi, bir C# uygulamasının giriş noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="450d6-105">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="450d6-106">(Kitaplıklar ve hizmetler bir `Main` giriş noktası olarak bir yöntem gerektirmez.) Uygulama başlatıldığında, `Main` yöntemi çağrılan ilk yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="450d6-106">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

<span data-ttu-id="450d6-107">C# programında yalnızca bir giriş noktası olabilir.</span><span class="sxs-lookup"><span data-stu-id="450d6-107">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="450d6-108">Yöntemine sahip birden fazla sınıfınız varsa `Main` , giriş noktası olarak hangi yöntemin kullanılacağını belirtmek için programınızı **StartupObject** derleyici seçeneğiyle derlemeniz gerekir `Main` .</span><span class="sxs-lookup"><span data-stu-id="450d6-108">If you have more than one class that has a `Main` method, you must compile your program with the **StartupObject** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="450d6-109">Daha fazla bilgi için bkz. [ **StartupObject** (C# derleyici seçenekleri)](../../language-reference/compiler-options/advanced.md#mainentrypoint-or-startupobject).</span><span class="sxs-lookup"><span data-stu-id="450d6-109">For more information, see [**StartupObject** (C# Compiler Options)](../../language-reference/compiler-options/advanced.md#mainentrypoint-or-startupobject).</span></span>

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

<span data-ttu-id="450d6-110">C# 9 ' dan başlayarak, `Main` `Main` Aşağıdaki örnekte olduğu gibi yöntemini atlayabilir ve c# deyimlerini yönteminde olduğu gibi yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="450d6-110">Starting in C# 9, you can omit the `Main` method, and write C# statements as if they were in the `Main` method, as in the following example:</span></span>

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

<span data-ttu-id="450d6-111">Örtük bir giriş noktası yöntemiyle uygulama kodu yazma hakkında daha fazla bilgi için bkz. [üst düzey deyimler](top-level-statements.md).</span><span class="sxs-lookup"><span data-stu-id="450d6-111">For information about how to write application code with an implicit entry point method, see [Top-level statements](top-level-statements.md).</span></span>

## <a name="overview"></a><span data-ttu-id="450d6-112">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="450d6-112">Overview</span></span>

- <span data-ttu-id="450d6-113">`Main`Yöntemi, çalıştırılabilir programın giriş noktasıdır; program denetiminin başladığı ve bittiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="450d6-113">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="450d6-114">`Main` bir sınıf veya yapı içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="450d6-114">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="450d6-115">`Main`[statik](../../language-reference/keywords/static.md) olmalı ve [genel](../../language-reference/keywords/public.md)olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="450d6-115">`Main` must be [static](../../language-reference/keywords/static.md) and it need not be [public](../../language-reference/keywords/public.md).</span></span> <span data-ttu-id="450d6-116">(Önceki örnekte, [Private](../../language-reference/keywords/private.md)'ın varsayılan erişimini alır.) Kapsayan sınıf veya yapının statik olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="450d6-116">(In the earlier example, it receives the default access of [private](../../language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="450d6-117">`Main``void` `int` C# 7,1, `Task` veya dönüş türü ile başlayan, veya, ya da olabilir `Task<int>` .</span><span class="sxs-lookup"><span data-stu-id="450d6-117">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="450d6-118">Ve yalnızca `Main` bir `Task` veya döndürürse `Task<int>` , bildirimi, `Main` [`async`](../../language-reference/keywords/async.md) değiştiricisini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="450d6-118">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="450d6-119">Bunun özellikle bir yöntemi dışladığı unutulmamalıdır `async void Main` .</span><span class="sxs-lookup"><span data-stu-id="450d6-119">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="450d6-120">`Main`Yöntemi `string[]` komut satırı bağımsız değişkenleri içeren bir parametre ile veya olmadan bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="450d6-120">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="450d6-121">Windows uygulamaları oluşturmak için Visual Studio kullanırken, parametresini el ile ekleyebilir veya <xref:System.Environment.GetCommandLineArgs> [komut satırı bağımsız değişkenlerini](command-line-arguments.md)almak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="450d6-121">When using Visual Studio to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment.GetCommandLineArgs> method to obtain the [command-line arguments](command-line-arguments.md).</span></span> <span data-ttu-id="450d6-122">Parametreler, sıfır dizinli komut satırı bağımsız değişkenleri olarak okunurdur.</span><span class="sxs-lookup"><span data-stu-id="450d6-122">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="450d6-123">C ve C++ ' dan farklı olarak, programın adı dizideki ilk komut satırı bağımsız değişkeni olarak değerlendirilmez `args` , ancak yöntemin ilk öğesidir <xref:System.Environment.GetCommandLineArgs> .</span><span class="sxs-lookup"><span data-stu-id="450d6-123">Unlike C and C++, the name of the program is not treated as the first command-line argument in the `args` array, but it is the first element of the <xref:System.Environment.GetCommandLineArgs> method.</span></span>

<span data-ttu-id="450d6-124">Geçerli imzaların listesi aşağıda verilmiştir `Main` :</span><span class="sxs-lookup"><span data-stu-id="450d6-124">The following is a list of valid `Main` signatures:</span></span>

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

<span data-ttu-id="450d6-125">Yukarıdaki örneklerin hepsi ortak erişimci değiştiricisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="450d6-125">The preceding examples all use the public accessor modifier.</span></span> <span data-ttu-id="450d6-126">Bu tipik, ancak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="450d6-126">That is typical, but not required.</span></span>

<span data-ttu-id="450d6-127">`async`Ve ' nin eklenmesi `Task` , `Task<int>` konsol uygulamalarının `await` ' de başlaması ve zaman uyumsuz işlemler gerektiğinde program kodunu basitleştirir `Main` .</span><span class="sxs-lookup"><span data-stu-id="450d6-127">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="450d6-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="450d6-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="450d6-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="450d6-129">See also</span></span>

- [<span data-ttu-id="450d6-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="450d6-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="450d6-131">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="450d6-131">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="450d6-132">C# programı içinde</span><span class="sxs-lookup"><span data-stu-id="450d6-132">Inside a C# Program</span></span>](../inside-a-program/index.md)
