---
title: Yerel birlikte çalışabilirlik en iyi uygulamaları-.NET
description: .NET 'teki yerel bileşenlerle arabirimlendirme için en iyi uygulamaları öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: e5d96471e796dca712d25d2d9e2609508180d83f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391227"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="9df8f-103">Yerel birlikte çalışabilirlik en iyi uygulamaları</span><span class="sxs-lookup"><span data-stu-id="9df8f-103">Native interoperability best practices</span></span>

<span data-ttu-id="9df8f-104">.NET, yerel birlikte çalışabilirlik kodunuzu özelleştirmek için kullanabileceğiniz çeşitli yollar sunar.</span><span class="sxs-lookup"><span data-stu-id="9df8f-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="9df8f-105">Bu makale, Microsoft 'un .NET ekiplerinin yerel birlikte çalışabilirlik için izlediği yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="9df8f-106">Genel kılavuz</span><span class="sxs-lookup"><span data-stu-id="9df8f-106">General guidance</span></span>

<span data-ttu-id="9df8f-107">Bu bölümdeki kılavuz tüm birlikte çalışma senaryoları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="9df8f-108">✔️, yöntemlerinizi ve parametreleriniz için, çağırmak istediğiniz yerel yöntem olarak aynı adlandırma ve büyük harfleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-108">✔️ DO use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="9df8f-109">✔️ sabit değerler için aynı adlandırma ve büyük harfleri kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="9df8f-109">✔️ CONSIDER using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="9df8f-110">✔️, yerel türe en yakın eşleme olan .NET türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-110">✔️ DO use .NET types that map closest to the native type.</span></span> <span data-ttu-id="9df8f-111">Örneğin, C# ' de, yerel `uint` tür olduğunda kullanın `unsigned int`.</span><span class="sxs-lookup"><span data-stu-id="9df8f-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="9df8f-112">✔️ yalnızca, istediğiniz `[In]` davranış `[Out]` varsayılan davranıştan farklı olduğunda ve özniteliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-112">✔️ DO only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="9df8f-113">✔️, yerel <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> dizi arabelleklerinizi havuza almak IÇIN kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="9df8f-113">✔️ CONSIDER using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="9df8f-114">✔️, P/Invoke bildirimlerinizi yerel kitaplığınız ile aynı ada ve büyük harfe sahip bir sınıfta sarmalamanızı düşünün.</span><span class="sxs-lookup"><span data-stu-id="9df8f-114">✔️ CONSIDER wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="9df8f-115">Bu, özniteliklerinizin `[DllImport]` yerel kitaplığın adını geçirmek `nameof` için C# dil özelliğini kullanmasını sağlar ve yerel kitaplığın adını yanlış yazmadığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9df8f-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="9df8f-116">DllImport öznitelik ayarları</span><span class="sxs-lookup"><span data-stu-id="9df8f-116">DllImport attribute settings</span></span>

| <span data-ttu-id="9df8f-117">Ayar</span><span class="sxs-lookup"><span data-stu-id="9df8f-117">Setting</span></span> | <span data-ttu-id="9df8f-118">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="9df8f-118">Default</span></span> | <span data-ttu-id="9df8f-119">Öneri</span><span class="sxs-lookup"><span data-stu-id="9df8f-119">Recommendation</span></span> | <span data-ttu-id="9df8f-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9df8f-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="9df8f-121">Varsayılanı tut</span><span class="sxs-lookup"><span data-stu-id="9df8f-121">keep default</span></span>  | <span data-ttu-id="9df8f-122">Bu açık olarak yanlış olarak ayarlandığında, başarısız HRESULT dönüş değerleri özel durumlara açılır (ve tanımdaki dönüş değeri sonuç olarak null olur).</span><span class="sxs-lookup"><span data-stu-id="9df8f-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="9df8f-123">API 'ye bağlıdır</span><span class="sxs-lookup"><span data-stu-id="9df8f-123">depends on the API</span></span>  | <span data-ttu-id="9df8f-124">API GetLastError kullanıyorsa bunu true olarak ayarlayın ve değeri almak için Marshal. GetLastWin32Error kullanın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="9df8f-125">API bir hata olduğunu bildiren bir koşul ayarlarsa, yanlışlıkla üzerine yazılmasını önlemek için başka çağrılar yapmadan önce hatayı alın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="9df8f-126">`CharSet.None`, `CharSet.Ansi` davranışa geri döner</span><span class="sxs-lookup"><span data-stu-id="9df8f-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="9df8f-127">Tanımda `CharSet.Unicode` dizeler `CharSet.Ansi` veya karakterler varsa, açıkça kullanın</span><span class="sxs-lookup"><span data-stu-id="9df8f-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="9df8f-128">Bu, dizelerin sıralama davranışını ve ne zaman `ExactSpelling` `false`yapılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="9df8f-129">`CharSet.Ansi` Bunun aslında UNIX üzerinde UTF8 olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="9df8f-130">_Çoğu_ zaman Windows Unicode kullanır, ancak UNIX UTF8 kullanır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="9df8f-131">[Değiştirmeye belgeleri](./charset.md)hakkında daha fazla bilgi için bkz..</span><span class="sxs-lookup"><span data-stu-id="9df8f-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="9df8f-132">Bunu true olarak ayarlayın ve çalışma zamanı, `CharSet` ayarın değerine bağlı olarak bir "a" veya "w" sonekiyle (Için `CharSet.Ansi` `CharSet.Unicode`"a" ve "w") farklı işlev adlarını araymaz.</span><span class="sxs-lookup"><span data-stu-id="9df8f-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="9df8f-133">Dize parametreleri</span><span class="sxs-lookup"><span data-stu-id="9df8f-133">String parameters</span></span>

<span data-ttu-id="9df8f-134">Karakter kümesi Unicode olduğunda veya bağımsız değişken açıkça `[MarshalAs(UnmanagedType.LPWSTR)]` olarak işaretlenmişse _ve_ dize değer ile geçirildiğinde (değil `ref` `out`), dize sabitlenir ve doğrudan yerel kod tarafından kullanılır (kopyalanmaktansa).</span><span class="sxs-lookup"><span data-stu-id="9df8f-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="9df8f-135">Dizelerinizin ANSI düzeltmesini `[DllImport]` açıkça `Charset.Unicode` istemediğiniz sürece, işaretini işaretlemeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="9df8f-136">❌Parametreleri kullanmayın `[Out] string` .</span><span class="sxs-lookup"><span data-stu-id="9df8f-136">❌ DO NOT use `[Out] string` parameters.</span></span> <span data-ttu-id="9df8f-137">Değer tarafından `[Out]` özniteliği ile geçirilen dize parametreleri, dize bir dizilmiş dize ise çalışma zamanının kararlılığını bozabilir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="9df8f-138">İçin <xref:System.String.Intern%2A?displayProperty=nameWithType>belgelerde dize oluşturma hakkında daha fazla bilgi görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="9df8f-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="9df8f-139">❌Parametrelerden `StringBuilder` kaçının.</span><span class="sxs-lookup"><span data-stu-id="9df8f-139">❌ AVOID `StringBuilder` parameters.</span></span> <span data-ttu-id="9df8f-140">`StringBuilder`hazırlama *her zaman* yerel bir arabellek kopyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9df8f-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="9df8f-141">Bu nedenle, son derece verimsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="9df8f-142">Bir dize alan bir Windows API 'SI çağırmanın tipik senaryosunu gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="9df8f-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="9df8f-143">İstenen kapasiteyi (yönetilen kapasiteyi ayırır) bir SB oluşturun**{1}**</span><span class="sxs-lookup"><span data-stu-id="9df8f-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="9df8f-144">Çağır</span><span class="sxs-lookup"><span data-stu-id="9df8f-144">Invoke</span></span>
   1. <span data-ttu-id="9df8f-145">Yerel bir arabellek ayırır**{2}**</span><span class="sxs-lookup"><span data-stu-id="9df8f-145">Allocates a native buffer **{2}**</span></span>
   2. <span data-ttu-id="9df8f-146">`[In]` _(Bir `StringBuilder` parametre için varsayılan)_ içeriğini kopyalar</span><span class="sxs-lookup"><span data-stu-id="9df8f-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>
   3. <span data-ttu-id="9df8f-147">Yerel arabelleği yeni ayrılmış bir yönetilen diziye `[Out]` **{3}** _(Ayrıca için `StringBuilder`varsayılan)_ kopyalar</span><span class="sxs-lookup"><span data-stu-id="9df8f-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>
3. <span data-ttu-id="9df8f-148">`ToString()`henüz başka bir yönetilen diziyi ayırır**{4}**</span><span class="sxs-lookup"><span data-stu-id="9df8f-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="9df8f-149">Bu, *{4}* yerel koddan bir dizeyi almak için ayırmaların bir dizesidir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="9df8f-150">Bunu sınırlamak için en iyi yöntem, `StringBuilder` başka bir çağrıda öğesini yeniden kullanmak olacaktır ancak yalnızca *1* ayırmayı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9df8f-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="9df8f-151">' Den `ArrayPool`bir karakter arabelleğini kullanmak ve önbelleğe almak çok daha iyidir. daha sonra, `ToString()` sonraki çağrılar için yalnızca ayırmaya erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9df8f-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="9df8f-152">İle ilgili `StringBuilder` diğer sorun, geri dönüş arabelleğini her zaman ilk null değere kopyasın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="9df8f-153">Geçilen geri dize sonlandırılmazsa veya çift null ile sonlandırılmış bir dize ise, P/Invoke uygulamanız en iyi şekilde yanlış olur.</span><span class="sxs-lookup"><span data-stu-id="9df8f-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="9df8f-154">*Kullanıyorsanız* `StringBuilder`, bir adet son Gotcha, kapasitenin birlikte çalışma içinde her zaman hesaba katılmış bir gizli null değer **içermemelidir** .</span><span class="sxs-lookup"><span data-stu-id="9df8f-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="9df8f-155">Çoğu API 'nin, null değeri *de dahil olmak üzere* arabellek boyutunu istediği için bu, insanların bu yanlış alması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="9df8f-156">Bu, harcanan/gereksiz ayırmalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="9df8f-157">Ayrıca, bu Gotcha, çalışma zamanının kopyaları en `StringBuilder` aza indirmek için sıralama iyileştirmesine engel olur.</span><span class="sxs-lookup"><span data-stu-id="9df8f-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="9df8f-158">✔️ içinden ' `char[]`i kullanmayı düşünün `ArrayPool`.</span><span class="sxs-lookup"><span data-stu-id="9df8f-158">✔️ CONSIDER using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="9df8f-159">Dize sıralaması hakkında daha fazla bilgi için bkz. [dizeler Için varsayılan sıralama](../../framework/interop/default-marshaling-for-strings.md) ve [dize sıralamasını özelleştirme](customize-parameter-marshaling.md#customizing-string-parameters).</span><span class="sxs-lookup"><span data-stu-id="9df8f-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="9df8f-160">__Windows 'A özgü__ CLR `[Out]` 'nin varsayılan olarak boş dizeler `CoTaskMemFree` veya `SysStringFree` olarak `UnmanagedType.BSTR`işaretlenen dizeler için kullanacağı dizeler.</span><span class="sxs-lookup"><span data-stu-id="9df8f-160">__Windows Specific__ For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>
> <span data-ttu-id="9df8f-161">**Çıkış dizesi arabelleğine sahip çoğu API için:** Geçirilen karakter sayısı null içermelidir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-161">**For most APIs with an output string buffer:** The passed in character count must include the null.</span></span> <span data-ttu-id="9df8f-162">Döndürülen değer geçilen karakter sayısından küçükse, çağrı başarılı olur ve değer sondaki null *olmayan* karakter sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-162">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="9df8f-163">Aksi takdirde, sayı null karakter *dahil olmak üzere* arabelleğin gerekli boyutudur.</span><span class="sxs-lookup"><span data-stu-id="9df8f-163">Otherwise the count is the required size of the buffer *including* the null character.</span></span>
>
> - <span data-ttu-id="9df8f-164">5 ' te geçiş yapın, 4 ' ü alın: dize sonunda null olan 4 karakter uzunluğundadır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-164">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="9df8f-165">5 ' te geçiş yapın, 6: dize 5 karakter uzunluğundadır, null tutmak için 6 karakterlik bir arabellek gerekir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-165">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>
> [<span data-ttu-id="9df8f-166">Dizeler için Windows veri türleri</span><span class="sxs-lookup"><span data-stu-id="9df8f-166">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="9df8f-167">Boole parametreleri ve alanları</span><span class="sxs-lookup"><span data-stu-id="9df8f-167">Boolean parameters and fields</span></span>

<span data-ttu-id="9df8f-168">Boole değerleri daha kolay.</span><span class="sxs-lookup"><span data-stu-id="9df8f-168">Booleans are easy to mess up.</span></span> <span data-ttu-id="9df8f-169">Varsayılan olarak, .NET `bool` , 4 baytlık bir değer olan `BOOL`bir Windows için sıralanır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-169">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="9df8f-170">`_Bool`Ancak, ve `bool` C ve C++ içindeki türler *tek* bir bayttır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-170">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="9df8f-171">Bu, dönüş değerinin atıldığı ve yalnızca *büyük olasılıkla* sonucu değiştirecek olan hataları takip etmek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-171">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="9df8f-172">.NET `bool` değerlerini C veya C++ `bool` türlerine hazırlama hakkında daha fazla bilgi için, [Boole alanı sıralamasını özelleştirme](customize-struct-marshaling.md#customizing-boolean-field-marshaling)hakkındaki belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-172">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="9df8f-173">Yapılamıyor</span><span class="sxs-lookup"><span data-stu-id="9df8f-173">GUIDs</span></span>

<span data-ttu-id="9df8f-174">GUID 'Ler doğrudan imzalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-174">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="9df8f-175">Birçok Windows API 'si `GUID&` , gibi `REFIID`tür diğer adlarını alır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-175">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="9df8f-176">Ref tarafından geçirildiğinde, `ref` ya da `[MarshalAs(UnmanagedType.LPStruct)]` özniteliğiyle geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-176">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="9df8f-177">GUID</span><span class="sxs-lookup"><span data-stu-id="9df8f-177">GUID</span></span> | <span data-ttu-id="9df8f-178">-Başvuru GUID 'SI</span><span class="sxs-lookup"><span data-stu-id="9df8f-178">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="9df8f-179">❌GUID parametrelerinden başka bir şey için kullanmayın `[MarshalAs(UnmanagedType.LPStruct)]` `ref`</span><span class="sxs-lookup"><span data-stu-id="9df8f-179">❌ DO NOT Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="9df8f-180">Blittable türleri</span><span class="sxs-lookup"><span data-stu-id="9df8f-180">Blittable types</span></span>

<span data-ttu-id="9df8f-181">Blittable türleri, yönetilen ve yerel kodda aynı bit düzeyi gösterimine sahip olan türlerdir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-181">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="9df8f-182">Bu şekilde, yerel koda ve yerel koddan sıralanmaları için başka bir biçime dönüştürülmesi gerekmez ve bu da performansı artırdığı için tercih edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-182">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="9df8f-183">**Blittable türleri:**</span><span class="sxs-lookup"><span data-stu-id="9df8f-183">**Blittable types:**</span></span>

- <span data-ttu-id="9df8f-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="9df8f-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="9df8f-185">blittable türlerin iç içe olmayan tek boyutlu dizileri (örneğin, `int[]`)</span><span class="sxs-lookup"><span data-stu-id="9df8f-185">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="9df8f-186">örnek alanlar için yalnızca blittable değer türlerine sahip sabit düzenine sahip yapılar ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="9df8f-186">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="9df8f-187">Sabit düzen için `[StructLayout(LayoutKind.Sequential)]` veya`[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="9df8f-187">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="9df8f-188">yapılar varsayılan `LayoutKind.Sequential` olarak, sınıflardır`LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="9df8f-188">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="9df8f-189">**Blittable DEĞIL:**</span><span class="sxs-lookup"><span data-stu-id="9df8f-189">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="9df8f-190">**Bazen blittable:**</span><span class="sxs-lookup"><span data-stu-id="9df8f-190">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="9df8f-191">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="9df8f-191">`char`, `string`</span></span>

<span data-ttu-id="9df8f-192">Blittable türleri başvuru ile geçirildiğinde, bir ara belleğe kopyalamak yerine yalnızca hazırlayıcısı tarafından sabitlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-192">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="9df8f-193">(Sınıflar kendiliğinden başvuruya göre geçirilir, yapılar veya `ref` `out`ile kullanıldığında başvuruya göre geçirilir.)</span><span class="sxs-lookup"><span data-stu-id="9df8f-193">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="9df8f-194">`char`tek boyutlu bir dizide **veya** ile birlikte `[StructLayout]` açık olarak işaretlenen bir türün parçasıysa blittable `CharSet = CharSet.Unicode`.</span><span class="sxs-lookup"><span data-stu-id="9df8f-194">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="9df8f-195">`string`blittable, başka bir türde yoksa ve ile `[MarshalAs(UnmanagedType.LPWStr)]` `[DllImport]` `CharSet = CharSet.Unicode` işaretlenmiş bir bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-195">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="9df8f-196">Bir türün blittable olup olmadığını, sabitlenmiş `GCHandle`bir oluşturma girişiminde görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9df8f-196">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="9df8f-197">Tür bir dize değilse veya blittable `GCHandle.Alloc` olarak kabul edilir. `ArgumentException`</span><span class="sxs-lookup"><span data-stu-id="9df8f-197">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="9df8f-198">✔️ yapılarınızı mümkün olduğunca blittable yapın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-198">✔️ DO make your structures blittable when possible.</span></span>

<span data-ttu-id="9df8f-199">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="9df8f-199">For more information, see:</span></span>

- [<span data-ttu-id="9df8f-200">Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler</span><span class="sxs-lookup"><span data-stu-id="9df8f-200">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)
- [<span data-ttu-id="9df8f-201">Tür sıralaması</span><span class="sxs-lookup"><span data-stu-id="9df8f-201">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="9df8f-202">Yönetilen nesneleri canlı tutma</span><span class="sxs-lookup"><span data-stu-id="9df8f-202">Keeping managed objects alive</span></span>

<span data-ttu-id="9df8f-203">`GC.KeepAlive()`bir nesnenin, KeepAlive yöntemi vurana kadar kapsamda kalmasını güvence altına alınır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-203">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="9df8f-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)hazırlayıcısı 'in bir P/Invoke süresince bir nesneyi canlı tutmaya izin verir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="9df8f-205">Yöntemi, yöntem imzaları yerine `IntPtr` kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-205">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="9df8f-206">`SafeHandle`Bu sınıfın yerini etkin bir şekilde değiştirir ve bunun yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-206">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="9df8f-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)yönetilen bir nesnenin sabitlenmesini ve yerel işaretçisine alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9df8f-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="9df8f-208">Temel model:</span><span class="sxs-lookup"><span data-stu-id="9df8f-208">The basic pattern is:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="9df8f-209">Sabitleme için `GCHandle`varsayılan değer değildir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-209">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="9df8f-210">Diğer büyük model, yerel kod aracılığıyla yönetilen bir nesneye başvuru geçirmek ve genellikle bir geri çağırma ile yönetilen koda geri dönmek içindir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-210">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="9df8f-211">Bu, şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="9df8f-211">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="9df8f-212">Bellek sızıntılarını `GCHandle` önlemek için açıkça serbest bırakılmış olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-212">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="9df8f-213">Ortak Windows veri türleri</span><span class="sxs-lookup"><span data-stu-id="9df8f-213">Common Windows data types</span></span>

<span data-ttu-id="9df8f-214">Aşağıda, Windows API 'Lerinde yaygın olarak kullanılan ve Windows koduna çağrılırken hangi C# türlerinin kullanılacağı veri türlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-214">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="9df8f-215">Aşağıdaki türler, adlarına rağmen 32-bit ve 64-bit Windows üzerinde aynı boyutlardır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-215">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="9df8f-216">Genişlik</span><span class="sxs-lookup"><span data-stu-id="9df8f-216">Width</span></span> | <span data-ttu-id="9df8f-217">Windows</span><span class="sxs-lookup"><span data-stu-id="9df8f-217">Windows</span></span>          | <span data-ttu-id="9df8f-218">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="9df8f-218">C (Windows)</span></span>          | <span data-ttu-id="9df8f-219">C#</span><span class="sxs-lookup"><span data-stu-id="9df8f-219">C#</span></span>       | <span data-ttu-id="9df8f-220">Yapıyı</span><span class="sxs-lookup"><span data-stu-id="9df8f-220">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="9df8f-221">32</span><span class="sxs-lookup"><span data-stu-id="9df8f-221">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="9df8f-222">8</span><span class="sxs-lookup"><span data-stu-id="9df8f-222">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="9df8f-223">8</span><span class="sxs-lookup"><span data-stu-id="9df8f-223">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="9df8f-224">8</span><span class="sxs-lookup"><span data-stu-id="9df8f-224">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="9df8f-225">8</span><span class="sxs-lookup"><span data-stu-id="9df8f-225">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="9df8f-226">16</span><span class="sxs-lookup"><span data-stu-id="9df8f-226">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="9df8f-227">16</span><span class="sxs-lookup"><span data-stu-id="9df8f-227">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="9df8f-228">16</span><span class="sxs-lookup"><span data-stu-id="9df8f-228">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="9df8f-229">16</span><span class="sxs-lookup"><span data-stu-id="9df8f-229">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="9df8f-230">16</span><span class="sxs-lookup"><span data-stu-id="9df8f-230">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="9df8f-231">32</span><span class="sxs-lookup"><span data-stu-id="9df8f-231">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="9df8f-232">32</span><span class="sxs-lookup"><span data-stu-id="9df8f-232">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="9df8f-233">32</span><span class="sxs-lookup"><span data-stu-id="9df8f-233">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="9df8f-234">32</span><span class="sxs-lookup"><span data-stu-id="9df8f-234">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="9df8f-235">64</span><span class="sxs-lookup"><span data-stu-id="9df8f-235">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="9df8f-236">64</span><span class="sxs-lookup"><span data-stu-id="9df8f-236">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="9df8f-237">64</span><span class="sxs-lookup"><span data-stu-id="9df8f-237">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="9df8f-238">64</span><span class="sxs-lookup"><span data-stu-id="9df8f-238">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="9df8f-239">64</span><span class="sxs-lookup"><span data-stu-id="9df8f-239">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="9df8f-240">32</span><span class="sxs-lookup"><span data-stu-id="9df8f-240">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="9df8f-241">32</span><span class="sxs-lookup"><span data-stu-id="9df8f-241">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="9df8f-242">Aşağıdaki türler, işaretçiler olması, platformun genişliğini izler.</span><span class="sxs-lookup"><span data-stu-id="9df8f-242">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="9df8f-243">Bunlar `IntPtr` / `UIntPtr` için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-243">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="9df8f-244">İmzalı Işaretçi türleri (kullanım `IntPtr`)</span><span class="sxs-lookup"><span data-stu-id="9df8f-244">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="9df8f-245">İşaretsiz Işaretçi türleri (kullanım `UIntPtr`)</span><span class="sxs-lookup"><span data-stu-id="9df8f-245">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="9df8f-246">`PVOID` C `void*` olan bir Windows ya `IntPtr` `UIntPtr`da olarak sıralanabilir, ancak mümkün olduğunda tercih `void*` edilebilir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-246">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="9df8f-247">Windows veri türleri</span><span class="sxs-lookup"><span data-stu-id="9df8f-247">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="9df8f-248">Veri türü aralıkları</span><span class="sxs-lookup"><span data-stu-id="9df8f-248">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="9df8f-249">Yapılar</span><span class="sxs-lookup"><span data-stu-id="9df8f-249">Structs</span></span>

<span data-ttu-id="9df8f-250">Yönetilen yapılar yığında oluşturulur ve Yöntem dönene kadar kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="9df8f-250">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="9df8f-251">Daha sonra, tanım olarak "sabitlenmiş" olur (GC tarafından taşınmaz).</span><span class="sxs-lookup"><span data-stu-id="9df8f-251">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="9df8f-252">Ayrıca, yerel kod geçerli yöntemin sonundan sonra işaretçiyi kullanmayacaksa, güvenli olmayan kod bloklarıyla adresi de alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9df8f-252">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="9df8f-253">Blittable yapılar, doğrudan hazırlama katmanı tarafından yalnızca kullanılabilecek şekilde daha fazla performanızdır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-253">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="9df8f-254">Yapıları blittable yapmayı deneyin (örneğin, kullanmaktan kaçının `bool`).</span><span class="sxs-lookup"><span data-stu-id="9df8f-254">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="9df8f-255">Daha fazla bilgi için [blittable Types](#blittable-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-255">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="9df8f-256">Yapı *blittable ise,* daha iyi performans `sizeof()` `Marshal.SizeOf<MyStruct>()` için yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-256">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="9df8f-257">Yukarıda da belirtildiği gibi, sabitlenmiş bir sabitlenmiş `GCHandle`oluşturma girişiminde, türün blittable olduğunu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9df8f-257">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="9df8f-258">Tür bir dize değilse veya blittable olarak kabul edilir, `GCHandle.Alloc` bir `ArgumentException`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9df8f-258">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="9df8f-259">Tanımlarda yapıların işaretçilerine ya da `ref` `unsafe` ile `*`geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-259">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="9df8f-260">✔️, resmi platform belgelerinde veya üstbilgisinde kullanılan şekle ve adlara göre, yönetilen yapı ile mümkün olduğunca yakından eşleşir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-260">✔️ DO match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="9df8f-261">✔️ performansı artırmak için blittable `sizeof()` yapıları yerine `Marshal.SizeOf<MyStruct>()` C# kullanın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-261">✔️ DO use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="9df8f-262">❌Yapılardaki `System.Delegate` işlev `System.MulticastDelegate` işaretçisi alanlarını temsil etmek IÇIN veya alanlarını kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="9df8f-262">❌ AVOID using `System.Delegate` or `System.MulticastDelegate` fields to represent function pointer fields in structures.</span></span>

<span data-ttu-id="9df8f-263"><xref:System.Delegate?displayProperty=fullName> Gerekli bir imzaya sahip olmadığından, geçirilen temsilcinin yerel kodun beklediği imzayla eşleşeceğini garanti <xref:System.MulticastDelegate?displayProperty=fullName> etmez.</span><span class="sxs-lookup"><span data-stu-id="9df8f-263">Since <xref:System.Delegate?displayProperty=fullName> and <xref:System.MulticastDelegate?displayProperty=fullName> don't have a required signature, they don't guarantee that the delegate passed in will match the signature the native code expects.</span></span> <span data-ttu-id="9df8f-264">Ayrıca, .NET Framework ve .NET Core ' da, yerel temsilindeki alanın `System.Delegate` değeri `System.MulticastDelegate` yönetilen bir temsilciyi sarmalayan bir işlev işaretçisi değilse, bir veya yerel gösteriminden yönetilen bir nesne içeren bir yapının sıralaması çalışma zamanının kararlılığını bozabilir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-264">Additionally, in .NET Framework and .NET Core, marshaling a struct containing a `System.Delegate` or `System.MulticastDelegate` from its native representation to a managed object can destabilize the runtime if the value of the field in the native representation isn't a function pointer that wraps a managed delegate.</span></span> <span data-ttu-id="9df8f-265">.NET 5 ve sonraki sürümlerde, bir `System.Delegate` veya `System.MulticastDelegate` alanını yerel gösterimden yönetilen bir nesneye sıralama desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9df8f-265">In .NET 5 and later versions, marshaling a `System.Delegate` or `System.MulticastDelegate` field from a native representation to a managed object is not supported.</span></span> <span data-ttu-id="9df8f-266">`System.Delegate` Veya `System.MulticastDelegate`yerine belirli bir temsilci türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="9df8f-266">Use a specific delegate type instead of `System.Delegate` or `System.MulticastDelegate`.</span></span>

### <a name="fixed-buffers"></a><span data-ttu-id="9df8f-267">Sabit arabellekler</span><span class="sxs-lookup"><span data-stu-id="9df8f-267">Fixed Buffers</span></span>

<span data-ttu-id="9df8f-268">Benzer `INT_PTR Reserved1[2]` bir dizi iki `IntPtr` alan için sıralanmalıdır `Reserved1a` ve. `Reserved1b`</span><span class="sxs-lookup"><span data-stu-id="9df8f-268">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="9df8f-269">Yerel dizi basit bir tür olduğunda, `fixed` anahtar sözcüğünü kullanarak biraz daha düzgün bir şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9df8f-269">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="9df8f-270">Örneğin, `SYSTEM_PROCESS_INFORMATION` yerel üst bilgisinde şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="9df8f-270">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="9df8f-271">C# ' de, bunu şöyle yazalım:</span><span class="sxs-lookup"><span data-stu-id="9df8f-271">In C#, we can write it like this:</span></span>

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

<span data-ttu-id="9df8f-272">Ancak, sabit arabelleklerle bazı tuzakları vardır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-272">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="9df8f-273">Blittable olmayan türlerin sabit arabellekleri doğru sıralanmayacak, bu nedenle yerinde dizinin birden çok ayrı alana genişletilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9df8f-273">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="9df8f-274">Ayrıca, .NET Framework ve .NET Core 'da 3,0 öncesinde, sabit bir arabellek alanı içeren bir struct, blittable olmayan bir yapı içinde iç içe geçmişse, sabit arabellek alanı yerel koda doğru şekilde sıralanmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="9df8f-274">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
