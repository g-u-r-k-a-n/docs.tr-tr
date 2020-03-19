---
title: ByRef’ler
description: Düşük seviyeli programlama için kullanılan F#'daki byref ve byref benzeri türleri hakkında bilgi edinin.
ms.date: 11/04/2019
ms.openlocfilehash: 527f465ee87fe153a2deae1306b6730531dc4123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187047"
---
# <a name="byrefs"></a><span data-ttu-id="d41ac-103">ByRef’ler</span><span class="sxs-lookup"><span data-stu-id="d41ac-103">Byrefs</span></span>

<span data-ttu-id="d41ac-104">F# düşük düzeyprogramlama alanında anlaşma iki ana özellik alanları vardır:</span><span class="sxs-lookup"><span data-stu-id="d41ac-104">F# has two major feature areas that deal in the space of low-level programming:</span></span>

* <span data-ttu-id="d41ac-105">`byref` / Yönetilen `inref` / işaretçiler olan `outref` türler.</span><span class="sxs-lookup"><span data-stu-id="d41ac-105">The `byref`/`inref`/`outref` types, which are managed pointers.</span></span> <span data-ttu-id="d41ac-106">Çalışma zamanında geçersiz olan bir programı derleyemiyorsanız, kullanımla ilgili kısıtlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="d41ac-106">They have restrictions on usage so that you cannot compile a program that is invalid at run time.</span></span>
* <span data-ttu-id="d41ac-107">Benzer `byref`semantik ve aynı derleme zamanı kısıtlamaları olan bir [yapıdır](structures.md) `byref<'T>`- struct gibi .</span><span class="sxs-lookup"><span data-stu-id="d41ac-107">A `byref`-like struct, which is a [structure](structures.md) that has similar semantics and the same compile-time restrictions as `byref<'T>`.</span></span> <span data-ttu-id="d41ac-108">Bir <xref:System.Span%601>örnek.</span><span class="sxs-lookup"><span data-stu-id="d41ac-108">One example is <xref:System.Span%601>.</span></span>

## <a name="syntax"></a><span data-ttu-id="d41ac-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d41ac-109">Syntax</span></span>

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a><span data-ttu-id="d41ac-110">Byref, inref ve outref</span><span class="sxs-lookup"><span data-stu-id="d41ac-110">Byref, inref, and outref</span></span>

<span data-ttu-id="d41ac-111">Üç şekli `byref`vardır:</span><span class="sxs-lookup"><span data-stu-id="d41ac-111">There are three forms of `byref`:</span></span>

* <span data-ttu-id="d41ac-112">`inref<'T>`, temel değeri okumak için yönetilen bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d41ac-112">`inref<'T>`, a managed pointer for reading the underlying value.</span></span>
* <span data-ttu-id="d41ac-113">`outref<'T>`, temel değere yazmak için yönetilen bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d41ac-113">`outref<'T>`, a managed pointer for writing to the underlying value.</span></span>
* <span data-ttu-id="d41ac-114">`byref<'T>`, temel değeri okumak ve yazmak için yönetilen bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d41ac-114">`byref<'T>`, a managed pointer for reading and writing the underlying value.</span></span>

<span data-ttu-id="d41ac-115">Bir `byref<'T>` beklenen yerde `inref<'T>` geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d41ac-115">A `byref<'T>` can be passed where an `inref<'T>` is expected.</span></span> <span data-ttu-id="d41ac-116">Benzer şekilde, `byref<'T>` bir beklenen `outref<'T>` yerde geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d41ac-116">Similarly, a `byref<'T>` can be passed where an `outref<'T>` is expected.</span></span>

## <a name="using-byrefs"></a><span data-ttu-id="d41ac-117">Byrefs kullanma</span><span class="sxs-lookup"><span data-stu-id="d41ac-117">Using byrefs</span></span>

<span data-ttu-id="d41ac-118">Bir , `inref<'T>`bir işaretçi değeri almak `&`için gereken bir kullanmak için:</span><span class="sxs-lookup"><span data-stu-id="d41ac-118">To use a `inref<'T>`, you need to get a pointer value with `&`:</span></span>

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

<span data-ttu-id="d41ac-119">Bir `outref<'T>` veya `byref<'T>`kullanarak işaretçiye yazmak için `mutable`, ayrıca bir işaretçi kapmak değeri yapmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="d41ac-119">To write to the pointer by using an `outref<'T>` or `byref<'T>`, you must also make the value you grab a pointer to `mutable`.</span></span>

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

<span data-ttu-id="d41ac-120">İşaretçiyi okumak yerine yalnızca yazıyorsanız, `outref<'T>` 'yi `byref<'T>`yerine kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="d41ac-120">If you are only writing the pointer instead of reading it, consider using `outref<'T>` instead of `byref<'T>`.</span></span>

### <a name="inref-semantics"></a><span data-ttu-id="d41ac-121">İnref semantik</span><span class="sxs-lookup"><span data-stu-id="d41ac-121">Inref semantics</span></span>

<span data-ttu-id="d41ac-122">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="d41ac-122">Consider the following code:</span></span>

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

<span data-ttu-id="d41ac-123">Semantically, bu aşağıdaki anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="d41ac-123">Semantically, this means the following:</span></span>

* <span data-ttu-id="d41ac-124">`x` İşaretçinin sahibi yalnızca değeri okumak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d41ac-124">The holder of the `x` pointer may only use it to read the value.</span></span>
* <span data-ttu-id="d41ac-125">İç `struct` `SomeStruct` içe yuvalanmış alanlara edinilen `inref<_>`işaretçilere tür verilir.</span><span class="sxs-lookup"><span data-stu-id="d41ac-125">Any pointer acquired to `struct` fields nested within `SomeStruct` are given type `inref<_>`.</span></span>

<span data-ttu-id="d41ac-126">Aşağıdaki ler de doğrudur:</span><span class="sxs-lookup"><span data-stu-id="d41ac-126">The following is also true:</span></span>

* <span data-ttu-id="d41ac-127">Diğer iş parçacıklarının veya diğer adların `x`yazma erişiminin olmadığı ima edilmez.</span><span class="sxs-lookup"><span data-stu-id="d41ac-127">There is no implication that other threads or aliases do not have write access to `x`.</span></span>
* <span data-ttu-id="d41ac-128">Bir `SomeStruct` `x` varlık nedeniyle değişmez bir ima `inref`yoktur.</span><span class="sxs-lookup"><span data-stu-id="d41ac-128">There is no implication that `SomeStruct` is immutable by virtue of `x` being an `inref`.</span></span>

<span data-ttu-id="d41ac-129">Ancak, **değişmez** olan F# değer türleri `this` için işaretçi . `inref`</span><span class="sxs-lookup"><span data-stu-id="d41ac-129">However, for F# value types that **are** immutable, the `this` pointer is inferred to be an `inref`.</span></span>

<span data-ttu-id="d41ac-130">Tüm bu kurallar birlikte, bir `inref` işaretçinin sahibinin işaret edilen belleğin hemen içeriğini değiştiremeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d41ac-130">All of these rules together mean that the holder of an `inref` pointer may not modify the immediate contents of the memory being pointed to.</span></span>

### <a name="outref-semantics"></a><span data-ttu-id="d41ac-131">Outref semantik</span><span class="sxs-lookup"><span data-stu-id="d41ac-131">Outref semantics</span></span>

<span data-ttu-id="d41ac-132">`outref<'T>` Amaç, işaretçinin yalnızca yazılması gerektiğini belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="d41ac-132">The purpose of `outref<'T>` is to indicate that the pointer should only be written to.</span></span> <span data-ttu-id="d41ac-133">Beklenmedik bir `outref<'T>` şekilde, adından da aynı sıcanda temel değeri okumaya izin verir.</span><span class="sxs-lookup"><span data-stu-id="d41ac-133">Unexpectedly, `outref<'T>` permits reading the underlying value despite its name.</span></span> <span data-ttu-id="d41ac-134">Bu uyumluluk amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="d41ac-134">This is for compatibility purposes.</span></span> <span data-ttu-id="d41ac-135">Semantik olarak, `outref<'T>` farklı `byref<'T>`değil.</span><span class="sxs-lookup"><span data-stu-id="d41ac-135">Semantically, `outref<'T>` is no different than `byref<'T>`.</span></span>

### <a name="interop-with-c"></a><span data-ttu-id="d41ac-136">C ile Interop\#</span><span class="sxs-lookup"><span data-stu-id="d41ac-136">Interop with C\#</span></span>

<span data-ttu-id="d41ac-137">C# ve `in ref` `out ref` anahtar kelimeleri destekler, döner ek `ref` olarak.</span><span class="sxs-lookup"><span data-stu-id="d41ac-137">C# supports the `in ref` and `out ref` keywords, in addition to `ref` returns.</span></span> <span data-ttu-id="d41ac-138">Aşağıdaki tablo, F#'ın C#'ın ne yaksalar yayıştırdığını nasıl yorumladığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="d41ac-138">The following table shows how F# interprets what C# emits:</span></span>

|<span data-ttu-id="d41ac-139">C# yapı</span><span class="sxs-lookup"><span data-stu-id="d41ac-139">C# construct</span></span>|<span data-ttu-id="d41ac-140">F# çıkarımları</span><span class="sxs-lookup"><span data-stu-id="d41ac-140">F# infers</span></span>|
|------------|---------|
|<span data-ttu-id="d41ac-141">`ref`iade değeri</span><span class="sxs-lookup"><span data-stu-id="d41ac-141">`ref` return value</span></span>|`outref<'T>`|
|<span data-ttu-id="d41ac-142">`ref readonly`iade değeri</span><span class="sxs-lookup"><span data-stu-id="d41ac-142">`ref readonly` return value</span></span>|`inref<'T>`|
|<span data-ttu-id="d41ac-143">`in ref`Parametre</span><span class="sxs-lookup"><span data-stu-id="d41ac-143">`in ref` parameter</span></span>|`inref<'T>`|
|<span data-ttu-id="d41ac-144">`out ref`Parametre</span><span class="sxs-lookup"><span data-stu-id="d41ac-144">`out ref` parameter</span></span>|`outref<'T>`|

<span data-ttu-id="d41ac-145">Aşağıdaki tablo, F#'nın ne yaksalar yayıştırolduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="d41ac-145">The following table shows what F# emits:</span></span>

|<span data-ttu-id="d41ac-146">F# yapısı</span><span class="sxs-lookup"><span data-stu-id="d41ac-146">F# construct</span></span>|<span data-ttu-id="d41ac-147">Yayılan yapı</span><span class="sxs-lookup"><span data-stu-id="d41ac-147">Emitted construct</span></span>|
|------------|-----------------|
|<span data-ttu-id="d41ac-148">`inref<'T>` bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="d41ac-148">`inref<'T>` argument</span></span>|<span data-ttu-id="d41ac-149">`[In]`bağımsız değişkene öznitelik</span><span class="sxs-lookup"><span data-stu-id="d41ac-149">`[In]` attribute on argument</span></span>|
|<span data-ttu-id="d41ac-150">`inref<'T>`Dönüş</span><span class="sxs-lookup"><span data-stu-id="d41ac-150">`inref<'T>` return</span></span>|<span data-ttu-id="d41ac-151">`modreq`değere öznitelik</span><span class="sxs-lookup"><span data-stu-id="d41ac-151">`modreq` attribute on value</span></span>|
|<span data-ttu-id="d41ac-152">`inref<'T>`soyut yuva veya uygulamada</span><span class="sxs-lookup"><span data-stu-id="d41ac-152">`inref<'T>` in abstract slot or implementation</span></span>|<span data-ttu-id="d41ac-153">`modreq`bağımsız değişken veya dönüş</span><span class="sxs-lookup"><span data-stu-id="d41ac-153">`modreq` on argument or return</span></span>|
|<span data-ttu-id="d41ac-154">`outref<'T>` bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="d41ac-154">`outref<'T>` argument</span></span>|<span data-ttu-id="d41ac-155">`[Out]`bağımsız değişkene öznitelik</span><span class="sxs-lookup"><span data-stu-id="d41ac-155">`[Out]` attribute on argument</span></span>|

### <a name="type-inference-and-overloading-rules"></a><span data-ttu-id="d41ac-156">Tür çıkarım ve aşırı yükleme kuralları</span><span class="sxs-lookup"><span data-stu-id="d41ac-156">Type inference and overloading rules</span></span>

<span data-ttu-id="d41ac-157">Bir `inref<'T>` tür aşağıdaki durumlarda F# derleyicisi tarafından çıkarılır:</span><span class="sxs-lookup"><span data-stu-id="d41ac-157">An `inref<'T>` type is inferred by the F# compiler in the following cases:</span></span>

1. <span data-ttu-id="d41ac-158">`IsReadOnly` Bir .NET parametresi veya özniteliği olan iade türü.</span><span class="sxs-lookup"><span data-stu-id="d41ac-158">A .NET parameter or return type that has an `IsReadOnly` attribute.</span></span>
2. <span data-ttu-id="d41ac-159">Mutable alanları olmayan bir yapı türündeki `this` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d41ac-159">The `this` pointer on a struct type that has no mutable fields.</span></span>
3. <span data-ttu-id="d41ac-160">Başka `inref<_>` bir işaretçiden türetilen bellek konumunun adresi.</span><span class="sxs-lookup"><span data-stu-id="d41ac-160">The address of a memory location derived from another `inref<_>` pointer.</span></span>

<span data-ttu-id="d41ac-161">Bir `inref` örtük adres alınırken, türü `SomeType` bağımsız değişkeni olan aşırı yük, türünden `inref<SomeType>`bir bağımsız değişkeniçeren aşırı yüke tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="d41ac-161">When an implicit address of an `inref` is being taken, an overload with an argument of type `SomeType` is preferred to an overload with an argument of type `inref<SomeType>`.</span></span> <span data-ttu-id="d41ac-162">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d41ac-162">For example:</span></span>

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

<span data-ttu-id="d41ac-163">Her iki durumda da, `System.DateTime` aşırı yüklemeler alma `inref<System.DateTime>`yerine çözülür.</span><span class="sxs-lookup"><span data-stu-id="d41ac-163">In both cases, the overloads taking `System.DateTime` are resolved rather than the overloads taking `inref<System.DateTime>`.</span></span>

## <a name="byref-like-structs"></a><span data-ttu-id="d41ac-164">Byref benzeri structs</span><span class="sxs-lookup"><span data-stu-id="d41ac-164">Byref-like structs</span></span>

<span data-ttu-id="d41ac-165">`byref` / `inref` Üçlüye / ek olarak, semantik gibi lere uyabilen `byref`kendi yapılarınızı tanımlayabilirsiniz. `outref`</span><span class="sxs-lookup"><span data-stu-id="d41ac-165">In addition to the `byref`/`inref`/`outref` trio, you can define your own structs that can adhere to `byref`-like semantics.</span></span> <span data-ttu-id="d41ac-166">Bu öznitelik <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> ile yapılır:</span><span class="sxs-lookup"><span data-stu-id="d41ac-166">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="d41ac-167">`IsByRefLike`anlamına `Struct`gelmez.</span><span class="sxs-lookup"><span data-stu-id="d41ac-167">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="d41ac-168">Her ikisi de türünde mevcut olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d41ac-168">Both must be present on the type.</span></span>

<span data-ttu-id="d41ac-169">F#'daki "-like"`byref`struct, yığına bağlı bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="d41ac-169">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="d41ac-170">Yönetilen yığına hiçbir zaman ayrılmaz.</span><span class="sxs-lookup"><span data-stu-id="d41ac-170">It is never allocated on the managed heap.</span></span> <span data-ttu-id="d41ac-171">Bir `byref`-benzeri yapı, yaşam boyu ve yakalamama ile ilgili güçlü denetimler kümesiyle uygulandığından, yüksek performanslı programlama için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d41ac-171">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="d41ac-172">Kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d41ac-172">The rules are:</span></span>

* <span data-ttu-id="d41ac-173">İşlev parametreleri, yöntem parametreleri, yerel değişkenler, yöntem döndürürler olarak kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="d41ac-173">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="d41ac-174">Bunlar statik veya bir sınıfın veya normal yapının örnek üyeleri olamaz.</span><span class="sxs-lookup"><span data-stu-id="d41ac-174">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="d41ac-175">Herhangi bir kapatma yapısı (yöntemler`async` veya lambda ifadeleri) tarafından ele geçirilemezler.</span><span class="sxs-lookup"><span data-stu-id="d41ac-175">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="d41ac-176">Genel bir parametre olarak kullanılamazlar.</span><span class="sxs-lookup"><span data-stu-id="d41ac-176">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="d41ac-177">Bu son nokta, giriş türlerini parametreize `|>` eden genel bir işlev olduğu gibi F# ardışık ardışık programlama için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d41ac-177">This last point is crucial for F# pipeline-style programming, as `|>` is a generic function that parameterizes its input types.</span></span> <span data-ttu-id="d41ac-178">Bu kısıtlama gelecekte `|>` için rahat olabilir, çünkü satır içi dir ve gövdesinde çizgisiz genel işlevlere herhangi bir çağrı yapmaz.</span><span class="sxs-lookup"><span data-stu-id="d41ac-178">This restriction may be relaxed for `|>` in the future, as it is inline and does not make any calls to non-inlined generic functions in its body.</span></span>

<span data-ttu-id="d41ac-179">Bu kurallar kullanımı güçlü bir şekilde kısıtlasa da, bunu yüksek performanslı bilgi işlem sözünü güvenli bir şekilde yerine getirmek için yapar.</span><span class="sxs-lookup"><span data-stu-id="d41ac-179">Although these rules strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="byref-returns"></a><span data-ttu-id="d41ac-180">Byref döndürür</span><span class="sxs-lookup"><span data-stu-id="d41ac-180">Byref returns</span></span>

<span data-ttu-id="d41ac-181">Byref F# işlevlerinden döner veya üye üretilebilir ve tüketilebilir.</span><span class="sxs-lookup"><span data-stu-id="d41ac-181">Byref returns from F# functions or members can be produced and consumed.</span></span> <span data-ttu-id="d41ac-182">`byref`-returning yöntemi tüketirken, değer örtülü olarak dereferenced.</span><span class="sxs-lookup"><span data-stu-id="d41ac-182">When consuming a `byref`-returning method, the value is implicitly dereferenced.</span></span> <span data-ttu-id="d41ac-183">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d41ac-183">For example:</span></span>

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

<span data-ttu-id="d41ac-184">Bir değer byref döndürmek için, değeri içeren değişkenin geçerli kapsamdan daha uzun yaşaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d41ac-184">To return a value byref, the variable that contains the value must live longer than the current scope.</span></span>
<span data-ttu-id="d41ac-185">Ayrıca, byref dönmek `&value` için, kullanın (değer geçerli kapsamdaha uzun yaşayan bir değişkendir).</span><span class="sxs-lookup"><span data-stu-id="d41ac-185">Also, to return byref, use `&value` (where value is a variable that lives longer than the current scope).</span></span>

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

<span data-ttu-id="d41ac-186">Birden çok zincirleme arama yoluyla bir başvuru nun geçirilmesi `&x` gibi `x` örtük dereference'ı önlemek için kullanın (değer nerededir).</span><span class="sxs-lookup"><span data-stu-id="d41ac-186">To avoid the implicit dereference, such as passing a reference through multiple chained calls, use `&x` (where `x` is the value).</span></span>

<span data-ttu-id="d41ac-187">Ayrıca doğrudan bir dönüş `byref`atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d41ac-187">You can also directly assign to a return `byref`.</span></span> <span data-ttu-id="d41ac-188">Aşağıdaki (son derece zorunlu) programı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d41ac-188">Consider the following (highly imperative) program:</span></span>

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

<span data-ttu-id="d41ac-189">Bu çıktı.</span><span class="sxs-lookup"><span data-stu-id="d41ac-189">This is the output:</span></span>

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a><span data-ttu-id="d41ac-190">Byrefs için kapsam</span><span class="sxs-lookup"><span data-stu-id="d41ac-190">Scoping for byrefs</span></span>

<span data-ttu-id="d41ac-191">Bağlı `let`bir değer, referansını tanımlandığı kapsamı aşamaz.</span><span class="sxs-lookup"><span data-stu-id="d41ac-191">A `let`-bound value cannot have its reference exceed the scope in which it was defined.</span></span> <span data-ttu-id="d41ac-192">Örneğin, aşağıdakiler izin verilmez:</span><span class="sxs-lookup"><span data-stu-id="d41ac-192">For example, the following is disallowed:</span></span>

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

<span data-ttu-id="d41ac-193">Bu, optimizasyonlarla derlep girmediğinize bağlı olarak farklı sonuçlar elde etmenizi önler.</span><span class="sxs-lookup"><span data-stu-id="d41ac-193">This prevents you from getting different results depending on if you compile with optimizations or not.</span></span>
