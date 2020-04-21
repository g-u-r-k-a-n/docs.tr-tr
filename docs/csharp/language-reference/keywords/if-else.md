---
title: if-else - C# Referans
ms.date: 07/20/2015
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
ms.openlocfilehash: 61b60674d3b5de4649a52d2a165265ae0a27e0be
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738859"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="a6139-102">if-else (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a6139-102">if-else (C# Reference)</span></span>

<span data-ttu-id="a6139-103">Bir `if` deyim, Boolean ifadesinin değerine göre hangi ifadenin çalıştırılalaaçıklamasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a6139-103">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="a6139-104">Aşağıdaki örnekte, `bool` değişken `condition` ayarlanır `true` ve daha sonra `if` deyiminde işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="a6139-104">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="a6139-105">Çıktı. `The variable is set to true.`</span><span class="sxs-lookup"><span data-stu-id="a6139-105">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="a6139-106">Bu konudaki örnekleri bir konsol uygulaması `Main` yöntemine yerleştirerek çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6139-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="a6139-107">`if` Aşağıdaki örnekte görüldüğü gibi, C# ifadesi iki biçim alabilir.</span><span class="sxs-lookup"><span data-stu-id="a6139-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>

```csharp
// if-else statement
if (condition)
{
    then-statement;
}
else
{
    else-statement;
}
// Next statement in the program.

// if statement without an else
if (condition)
{
    then-statement;
}
// Next statement in the program.
```

<span data-ttu-id="a6139-108">Bir `if-else` açıklamada, `condition` doğru değerlendirirse, `then-statement` çalışır.</span><span class="sxs-lookup"><span data-stu-id="a6139-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="a6139-109">Eğer `condition` yanlışsa, `else-statement` çalışır.</span><span class="sxs-lookup"><span data-stu-id="a6139-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="a6139-110">Aynı `condition` anda doğru ve yanlış olamaz, `else-statement` çünkü `if-else` bir ifadenin `then-statement` ve ifadenin her ikisi de çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="a6139-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="a6139-111">Çalıştırmaveya `then-statement` çalıştırmadan `else-statement` sonra, denetim deyimden `if` sonra bir sonraki ifadeye aktarılır.</span><span class="sxs-lookup"><span data-stu-id="a6139-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="a6139-112">Bir `if` deyim içermeyen bir `else` deyimde, `condition` eğer doğruysa, `then-statement` çalışır.</span><span class="sxs-lookup"><span data-stu-id="a6139-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="a6139-113">Yanlışsa, `condition` denetim deyimden `if` sonra bir sonraki ifadeye aktarılır.</span><span class="sxs-lookup"><span data-stu-id="a6139-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="a6139-114">Hem `then-statement` de `else-statement` parantez içinde kapalı tek bir ifade veya birden çok`{}`ifadeden oluşabilir ( ).</span><span class="sxs-lookup"><span data-stu-id="a6139-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="a6139-115">Tek bir ifade için ayraçlar isteğe bağlıdır, ancak önerilir.</span><span class="sxs-lookup"><span data-stu-id="a6139-115">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="a6139-116">İfade veya ifadeler `then-statement` ve `else-statement` orijinal `if` deyimi içinde iç içe `if` başka bir ifade de dahil olmak üzere, her türlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a6139-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="a6139-117">İç içe `if` geçen `else` ifadelerde, her `if` bir yan tümce `else`karşılık gelen olmayan son maddeye aittir.</span><span class="sxs-lookup"><span data-stu-id="a6139-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="a6139-118">Aşağıdaki örnekte, `Result1` her ikisi `m > 10` `n > 20` de ve doğru değerlendirmek görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a6139-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="a6139-119">Doğruysa `m > 10` ancak `n > 20` yanlışsa `Result2` görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a6139-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="a6139-120">Bunun yerine, yanlış `Result2` olduğunda `(m > 10)` görünmek istiyorsanız, aşağıdaki örnekte görüldüğü gibi iç içe alan `if` deyimin başlangıç ve sonunu oluşturmak için ayraçları kullanarak bu ilişkilendirme belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6139-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="a6139-121">`Result2`koşul `(m > 10)` yanlış olarak değerlendirilirse görünür.</span><span class="sxs-lookup"><span data-stu-id="a6139-121">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="a6139-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6139-122">Example</span></span>

<span data-ttu-id="a6139-123">Aşağıdaki örnekte, klavyeden bir karakter girersiniz ve program `if` giriş karakterinin alfabetik bir karakter olup olmadığını belirlemek için iç içe bir deyim kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6139-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="a6139-124">Giriş karakteri alfabetik bir karakterse, program giriş karakterinin küçük veya büyük harf olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="a6139-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="a6139-125">Her servis talebi için bir ileti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a6139-125">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="a6139-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6139-126">Example</span></span>

<span data-ttu-id="a6139-127">Aşağıdaki kısmi kodun gösterdiği gibi, bir `if` ifadeyi başka bir bloğun içine de ekte yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6139-127">You can also nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="a6139-128">Örnek, deyimleri diğer iki blok ve bir blok içinde yuvalar. `if`</span><span class="sxs-lookup"><span data-stu-id="a6139-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="a6139-129">Açıklamalar, her blokta hangi koşulların doğru veya yanlış olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6139-129">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="a6139-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6139-130">Example</span></span>

<span data-ttu-id="a6139-131">Aşağıdaki örnek, giriş karakterinin küçük harf mi, büyük harf mi yoksa bir sayı mı olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="a6139-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="a6139-132">Üç koşul da yanlışsa, karakter alfasayısal bir karakter değildir.</span><span class="sxs-lookup"><span data-stu-id="a6139-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="a6139-133">Örnek, her servis talebi için bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a6139-133">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="a6139-134">Else bloğundaki veya sonrabloğundaki bir deyimin geçerli bir ifade olması gibi, durum için geçerli boolean ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6139-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="a6139-135">, , `&&` `||`, `&` `|`, `!`gibi [mantıksal işleçleri](../operators/boolean-logical-operators.md) kullanabilirsiniz ve `^` bileşik koşullar yapmak için.</span><span class="sxs-lookup"><span data-stu-id="a6139-135">You can use [logical operators](../operators/boolean-logical-operators.md) such as `!`, `&&`, `||`, `&`, `|`, and `^` to make compound conditions.</span></span> <span data-ttu-id="a6139-136">Aşağıdaki kod örnekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6139-136">The following code shows examples.</span></span>

```csharp
// NOT
bool result = true;
if (!result)
{
    Console.WriteLine("The condition is true (result is false).");
}
else
{
    Console.WriteLine("The condition is false (result is true).");
}

// Short-circuit AND
int m = 9;
int n = 7;
int p = 5;
if (m >= n && m >= p)
{
    Console.WriteLine("Nothing is larger than m.");
}

// AND and NOT
if (m >= n && !(p > m))
{
    Console.WriteLine("Nothing is larger than m.");
}

// Short-circuit OR
if (m > n || m > p)
{
    Console.WriteLine("m isn't the smallest.");
}

// NOT and OR
m = 4;
if (!(m >= n || m >= p))
{
    Console.WriteLine("Now m is the smallest.");
}
// Output:
// The condition is false (result is true).
// Nothing is larger than m.
// Nothing is larger than m.
// m isn't the smallest.
// Now m is the smallest.
```

## <a name="c-language-specification"></a><span data-ttu-id="a6139-137">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a6139-137">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a6139-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6139-138">See also</span></span>

- [<span data-ttu-id="a6139-139">C# Referans</span><span class="sxs-lookup"><span data-stu-id="a6139-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a6139-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a6139-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a6139-141">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="a6139-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a6139-142">?: Operatör</span><span class="sxs-lookup"><span data-stu-id="a6139-142">?: Operator</span></span>](../operators/conditional-operator.md)
- [<span data-ttu-id="a6139-143">if-else Deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="a6139-143">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)
- [<span data-ttu-id="a6139-144">switch</span><span class="sxs-lookup"><span data-stu-id="a6139-144">switch</span></span>](switch.md)
