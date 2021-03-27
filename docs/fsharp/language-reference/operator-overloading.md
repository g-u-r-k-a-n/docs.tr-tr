---
title: İşleç Aşırı Yüklemesi
description: "Aritmetik işleçleri bir sınıf veya kayıt türünde ve F # ' da genel düzeyde aşırı yüklemeyi öğrenin."
ms.date: 08/15/2020
ms.openlocfilehash: 64ff87a8706e6a05754b5328a7d95cd6a2b360c1
ms.sourcegitcommit: 80f38cb67bd02f51d5722fa13d0ea207e3b14a8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2021
ms.locfileid: "105610856"
---
# <a name="operator-overloading"></a><span data-ttu-id="f97f1-103">İşleç Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="f97f1-103">Operator Overloading</span></span>

<span data-ttu-id="f97f1-104">Bu konu, bir sınıf veya kayıt türünde ve genel düzeyde aritmetik işleçlerin nasıl aşırı yükleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f97f1-104">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>

## <a name="syntax"></a><span data-ttu-id="f97f1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f97f1-105">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="f97f1-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f97f1-106">Remarks</span></span>

<span data-ttu-id="f97f1-107">Önceki sözdiziminde, *operator-symbol* ,,,, vb `+` . ' den biridir `-` `*` `/` `=` .</span><span class="sxs-lookup"><span data-stu-id="f97f1-107">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="f97f1-108">*Parametre-listesi* , işlenenleri söz konusu işlecin olağan sözdiziminde göründükleri sırada belirtir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-108">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="f97f1-109">*Yöntem-gövde* , elde edilen değeri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f97f1-109">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="f97f1-110">İşleçler için işleç aşırı yüklemelerinin statik olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-110">Operator overloads for operators must be static.</span></span> <span data-ttu-id="f97f1-111">Ve gibi Birli İşleçler için işleç aşırı yüklemeleri, işlecin, `+` `-` `~` aşağıdaki bildirimde gösterildiği gibi bir birli işleç olduğunu ve ikili işleç olduğunu göstermek için *operator-symbol* içinde bir tilde () kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-111">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="f97f1-112">Aşağıdaki kod, biri birli eksi ve bir skalar ile çarpma için olmak üzere yalnızca iki işleçle bir vektör sınıfını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-112">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="f97f1-113">Örnekte, skalar çarpma için iki aşırı yükleme gerekir, çünkü operatör vektör ve skaler 'in göründüğü sıraya bakılmaksızın çalışır.</span><span class="sxs-lookup"><span data-stu-id="f97f1-113">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="f97f1-114">Yeni Işleçler oluşturma</span><span class="sxs-lookup"><span data-stu-id="f97f1-114">Creating New Operators</span></span>

<span data-ttu-id="f97f1-115">Tüm standart işleçleri aşırı yükleyebilirsiniz, ancak belirli karakter dizileri dışında yeni işleçler de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f97f1-115">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="f97f1-116">İzin verilen işleç karakterleri,,,, `!` `$` `%` `&` `*` , `+` , `-` , `.` , `/` , `<` , `=` , `>` , `?` , `@` , `^` , `|` , ve `~` .</span><span class="sxs-lookup"><span data-stu-id="f97f1-116">Allowed operator characters are `!`, `$`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="f97f1-117">`~`Karakter, bir işleç birli oluşturma ve işleç karakter sırasının bir parçası olmayan özel anlamdadır.</span><span class="sxs-lookup"><span data-stu-id="f97f1-117">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="f97f1-118">Tüm işleçler birli yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="f97f1-118">Not all operators can be made unary.</span></span>

<span data-ttu-id="f97f1-119">Kullandığınız tam karakter dizisine bağlı olarak, operatörünüzün belirli bir önceliği ve ilişkilendirilebilirliği olur.</span><span class="sxs-lookup"><span data-stu-id="f97f1-119">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="f97f1-120">İlişkilendirilebilirlik, sola veya sağdan sola doğru olabilir ve aynı öncelik düzeyindeki operatörler parantez olmadan sırayla gösterildiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f97f1-120">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="f97f1-121">İşleç karakteri `.` önceliği etkilemez, örneğin, normal çarpma ile aynı önceliğe ve ilişkilendirilebilirliği olan kendi çarpma sürümünüzü tanımlamak istiyorsanız gibi işleçler oluşturabilirsiniz `.*` .</span><span class="sxs-lookup"><span data-stu-id="f97f1-121">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="f97f1-122">Yalnızca işleçler `?` ve `?<-` ile başlayabilir `?` .</span><span class="sxs-lookup"><span data-stu-id="f97f1-122">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="f97f1-123">`$`Operatör tek başına ve ek semboller olmadan kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f97f1-123">The `$` operator must stand alone and without additional symbols.</span></span>

<span data-ttu-id="f97f1-124">F # içindeki tüm işleçlerin önceliğini gösteren bir tablo, [sembol ve Işleç başvurusunda](./symbol-and-operator-reference/index.md)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-124">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](./symbol-and-operator-reference/index.md).</span></span>

## <a name="overloaded-operator-names"></a><span data-ttu-id="f97f1-125">Aşırı yüklenmiş Işleç adları</span><span class="sxs-lookup"><span data-stu-id="f97f1-125">Overloaded Operator Names</span></span>

<span data-ttu-id="f97f1-126">F # derleyicisi bir işleç ifadesi derlediğinde, bu işleç için derleyicinin ürettiği bir ada sahip bir yöntem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f97f1-126">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="f97f1-127">Bu, yöntemi için Microsoft ara dili (MSIL) ve ayrıca yansıma ve IntelliSense içinde görünen addır.</span><span class="sxs-lookup"><span data-stu-id="f97f1-127">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="f97f1-128">Normalde bu adları F # kodunda kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f97f1-128">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="f97f1-129">Aşağıdaki tabloda, standart işleçler ve bunlara karşılık gelen oluşturulan adlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-129">The following table shows the standard operators and their corresponding generated names.</span></span>

|<span data-ttu-id="f97f1-130">Operatör</span><span class="sxs-lookup"><span data-stu-id="f97f1-130">Operator</span></span>|<span data-ttu-id="f97f1-131">Oluşturulan ad</span><span class="sxs-lookup"><span data-stu-id="f97f1-131">Generated name</span></span>|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|

<span data-ttu-id="f97f1-132">`not`Bir sembolik işleç olmadığından F # içindeki işlecin yaymadığını unutmayın `op_Inequality` .</span><span class="sxs-lookup"><span data-stu-id="f97f1-132">Note that the `not` operator in F# does not emit `op_Inequality` because it is not a symbolic operator.</span></span> <span data-ttu-id="f97f1-133">Bu, bir Boolean ifadesini geçersiz hale getirir Il 'yi gösteren bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-133">It is a function that emits IL that negates a boolean expression.</span></span>

<span data-ttu-id="f97f1-134">Burada listelenmeyen işleç karakterlerinin diğer birleşimleri, işleçler olarak kullanılabilir ve aşağıdaki tablodaki tek karakterlerin adlarını birleştirerek oluşturulan adlara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-134">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="f97f1-135">Örneğin, +!</span><span class="sxs-lookup"><span data-stu-id="f97f1-135">For example, +!</span></span> <span data-ttu-id="f97f1-136">olur `op_PlusBang` .</span><span class="sxs-lookup"><span data-stu-id="f97f1-136">becomes `op_PlusBang`.</span></span>

|<span data-ttu-id="f97f1-137">İşleç karakteri</span><span class="sxs-lookup"><span data-stu-id="f97f1-137">Operator character</span></span>|<span data-ttu-id="f97f1-138">Name</span><span class="sxs-lookup"><span data-stu-id="f97f1-138">Name</span></span>|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`$`|`Dollar`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="f97f1-139">Ön ek ve ınfıx Işleçleri</span><span class="sxs-lookup"><span data-stu-id="f97f1-139">Prefix and Infix Operators</span></span>

<span data-ttu-id="f97f1-140">*Önek* işleçlerinin, bir işlev gibi bir işlenenin veya işlenenlerin önüne yerleştirilmesi beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-140">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="f97f1-141">*Indüzeltilme* işleçlerinin iki işlenen arasına yerleştirilmesi beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-141">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="f97f1-142">Yalnızca belirli işleçler önek işleçleri olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-142">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="f97f1-143">Bazı işleçler her zaman ön ek işleçleridir, diğerleri geçersiz veya ön ek olabilir ve REST, her zaman geri düzeltilebilirler.</span><span class="sxs-lookup"><span data-stu-id="f97f1-143">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="f97f1-144">,, `!` `!=` , Ve işleç `~` veya yinelenen dizileri ile başlayan işleçler `~` her zaman önek işleçleridir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-144">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="f97f1-145">,,,,,, `+` `-` Ve işleçleri `+.` `-.` `&` `&&` `%` `%%` önek işleçleri veya ınfıx işleçleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-145">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="f97f1-146">Bu işleçlerin ön ek sürümünü, `~` tanımlandığında önek işlecinin başlangıcına ekleyerek bir ınfıx sürümünden ayırt edersiniz.</span><span class="sxs-lookup"><span data-stu-id="f97f1-146">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="f97f1-147">`~`İşleci kullanıldığında, yalnızca tanımlandığında kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="f97f1-147">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="f97f1-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="f97f1-148">Example</span></span>

<span data-ttu-id="f97f1-149">Aşağıdaki kod, bir kesir türü uygulamak için işleç aşırı yüklemesi kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-149">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="f97f1-150">Kesir, pay ve payda ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f97f1-150">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="f97f1-151">İşlevi, `hcf` kesirleri azaltmak için kullanılan en yüksek ortak faktörü belirlemekte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f97f1-151">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="f97f1-152">**Çıktıların**</span><span class="sxs-lookup"><span data-stu-id="f97f1-152">**Output:**</span></span>

```console
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="f97f1-153">Genel düzeyde işleçler</span><span class="sxs-lookup"><span data-stu-id="f97f1-153">Operators at the Global Level</span></span>

<span data-ttu-id="f97f1-154">Ayrıca, genel düzeyde işleçler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f97f1-154">You can also define operators at the global level.</span></span> <span data-ttu-id="f97f1-155">Aşağıdaki kod bir işleci tanımlar `+?` .</span><span class="sxs-lookup"><span data-stu-id="f97f1-155">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="f97f1-156">Yukarıdaki kodun çıktısı `12` .</span><span class="sxs-lookup"><span data-stu-id="f97f1-156">The output of the above code is `12`.</span></span>

<span data-ttu-id="f97f1-157">Bu şekilde normal aritmetik işleçleri yeniden tanımlayabilirsiniz çünkü F # için kapsam kuralları, yeni tanımlanan işleçlerin yerleşik işleçlerden öncelikli olduğunu dikte ediyor.</span><span class="sxs-lookup"><span data-stu-id="f97f1-157">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="f97f1-158">Anahtar sözcüğü `inline` genellikle, çağıran kodla en iyi şekilde tümleşik olan küçük işlevler olan genel işleçlerle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f97f1-158">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="f97f1-159">İşleç işlevlerini satır içi olarak oluşturmak, statik olarak çözümlenen genel kod üretmek için statik olarak çözümlenen tür parametreleriyle birlikte çalışabilmelerini de sağlar.</span><span class="sxs-lookup"><span data-stu-id="f97f1-159">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="f97f1-160">Daha fazla bilgi için bkz. [satır Içi işlevler](./functions/inline-functions.md) ve [statik olarak çözümlenen tür parametreleri](./generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f97f1-160">For more information, see [Inline Functions](./functions/inline-functions.md) and [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f97f1-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f97f1-161">See also</span></span>

- [<span data-ttu-id="f97f1-162">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f97f1-162">Members</span></span>](./members/index.md)
