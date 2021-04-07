---
title: 'Son değişiklik: Blazor: RenderTreeFrame ReadOnly ortak alanları özellikler haline geldi'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: RenderTreeFrame ReadOnly ortak alanları özellikler haline geldi"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c4d70279b4280b079570099b82b056299405508b
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498171"
---
# <a name="blazor-rendertreeframe-readonly-public-fields-have-become-properties"></a><span data-ttu-id="ff33e-103">Blazor: RenderTreeFrame ReadOnly ortak alanları özellikler haline geldi</span><span class="sxs-lookup"><span data-stu-id="ff33e-103">Blazor: RenderTreeFrame readonly public fields have become properties</span></span>

<span data-ttu-id="ff33e-104">ASP.NET Core 3,0 ve 3,1 ' de, <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> Yapı, `readonly public` <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType> ve diğer gibi çeşitli alanları kullanıma sunuldu <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="ff33e-104">In ASP.NET Core 3.0 and 3.1, the <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> struct exposed various `readonly public` fields, including <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType>, <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence>, and others.</span></span> <span data-ttu-id="ff33e-105">ASP.NET Core 5,0 RC1 ve sonraki sürümlerinde, tüm `readonly public` alanlar özellikler olarak değiştirilmiştir `readonly public` .</span><span class="sxs-lookup"><span data-stu-id="ff33e-105">In ASP.NET Core 5.0 RC1 and later versions, all the `readonly public` fields changed to `readonly public` properties.</span></span>

<span data-ttu-id="ff33e-106">Bu değişiklik birçok geliştirici etkilemez, çünkü:</span><span class="sxs-lookup"><span data-stu-id="ff33e-106">This change won't affect many developers because:</span></span>

* <span data-ttu-id="ff33e-107">`.razor`Bileşenlerini tanımlamak için dosyaları (veya hatta el ile çağrıları) kullanan herhangi bir uygulama veya kitaplık <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> , bu türe doğrudan başvurmaz.</span><span class="sxs-lookup"><span data-stu-id="ff33e-107">Any app or library that simply uses `.razor` files (or even manual <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> calls) to define its components wouldn't be referencing this type directly.</span></span>
* <span data-ttu-id="ff33e-108">`RenderTreeFrame`Türün kendisi, Framework dışında kullanılması amaçlanmayan bir uygulama ayrıntısı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ff33e-108">The `RenderTreeFrame` type itself is regarded as an implementation detail, not intended for use outside of the framework.</span></span> <span data-ttu-id="ff33e-109">ASP.NET Core 3,0 ve üzeri, tür doğrudan kullanılıyorsa Derleyici uyarıları veren bir çözümleyici içerir.</span><span class="sxs-lookup"><span data-stu-id="ff33e-109">ASP.NET Core 3.0 and later includes an analyzer that issues compiler warnings if the type is being used directly.</span></span>
* <span data-ttu-id="ff33e-110">Doğrudan başvursanız bile `RenderTreeFrame` Bu değişiklik ikili bir değer değildir ancak kaynak bölünmez.</span><span class="sxs-lookup"><span data-stu-id="ff33e-110">Even if you reference `RenderTreeFrame` directly, this change is binary-breaking but not source-breaking.</span></span> <span data-ttu-id="ff33e-111">Diğer bir deyişle, var olan kaynak kodunuz doğru şekilde derlenir ve davranacaktır.</span><span class="sxs-lookup"><span data-stu-id="ff33e-111">That is, your existing source code will compile and behave properly.</span></span> <span data-ttu-id="ff33e-112">Yalnızca bir .NET Core 3. x çerçevesinde derleme yaptıysanız ve daha sonra bu ikili dosyaları .NET 5,0 RC1 ve sonraki bir çerçeveye karşı çalıştırmak için bir sorunla karşılaşacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ff33e-112">You'll only encounter an issue if compiling against a .NET Core 3.x framework and then running those binaries against the .NET 5.0 RC1 and later framework.</span></span>

<span data-ttu-id="ff33e-113">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 25727](https://github.com/dotnet/aspnetcore/issues/25727).</span><span class="sxs-lookup"><span data-stu-id="ff33e-113">For discussion, see GitHub issue [dotnet/aspnetcore#25727](https://github.com/dotnet/aspnetcore/issues/25727).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ff33e-114">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ff33e-114">Version introduced</span></span>

<span data-ttu-id="ff33e-115">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="ff33e-115">5.0 RC1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="ff33e-116">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="ff33e-116">Old behavior</span></span>

<span data-ttu-id="ff33e-117">Ortak Üyeler `RenderTreeFrame` alan olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ff33e-117">Public members on `RenderTreeFrame` are defined as fields.</span></span> <span data-ttu-id="ff33e-118">Örneğin `renderTreeFrame.Sequence` ve `renderTreeFrame.ElementName`.</span><span class="sxs-lookup"><span data-stu-id="ff33e-118">For example, `renderTreeFrame.Sequence` and `renderTreeFrame.ElementName`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="ff33e-119">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="ff33e-119">New behavior</span></span>

<span data-ttu-id="ff33e-120">Ortak Üyeler `RenderTreeFrame` , önceki ile aynı adlara sahip özellikler olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ff33e-120">Public members on `RenderTreeFrame` are defined as properties with the same names as before.</span></span> <span data-ttu-id="ff33e-121">Örneğin `renderTreeFrame.Sequence` ve `renderTreeFrame.ElementName`.</span><span class="sxs-lookup"><span data-stu-id="ff33e-121">For example, `renderTreeFrame.Sequence` and `renderTreeFrame.ElementName`.</span></span>

<span data-ttu-id="ff33e-122">Daha önceden derlenmiş kod bu değişiklikten bu yana yeniden derlenmemişse, MissingFieldException şuna benzer bir özel durum oluşturabilir: *alan bulunamadı: ' Microsoft. AspNetCore. components. RenderTree. RenderTreeFrame. FrameType '*.</span><span class="sxs-lookup"><span data-stu-id="ff33e-122">If older precompiled code hasn't been recompiled since this change, it may throw an exception similar to *MissingFieldException: Field not found: 'Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType'*.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ff33e-123">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="ff33e-123">Reason for change</span></span>

<span data-ttu-id="ff33e-124">Bu değişiklik, ASP.NET Core 5,0 ' de Blazor bileşeni işlemede yüksek etkili performans iyileştirmeleri uygulamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ff33e-124">This change was necessary to implement high-impact performance improvements in Blazor component rendering in ASP.NET Core 5.0.</span></span> <span data-ttu-id="ff33e-125">Aynı güvenlik ve kapsülleme düzeyleri korunur.</span><span class="sxs-lookup"><span data-stu-id="ff33e-125">The same levels of safety and encapsulation are maintained.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ff33e-126">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ff33e-126">Recommended action</span></span>

<span data-ttu-id="ff33e-127">Çoğu Blazor geliştiricisi bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="ff33e-127">Most Blazor developers are unaffected by this change.</span></span> <span data-ttu-id="ff33e-128">Bu değişiklik, kitaplığı ve paket yazarlarını yalnızca nadir bir durumda etkilemekle daha olasıdır.</span><span class="sxs-lookup"><span data-stu-id="ff33e-128">The change is more likely to affect library and package authors, but only in rare cases.</span></span> <span data-ttu-id="ff33e-129">Geliştirmekte olduğunuz özel olarak:</span><span class="sxs-lookup"><span data-stu-id="ff33e-129">Specifically, if you're developing:</span></span>

* <span data-ttu-id="ff33e-130">Bir uygulama ve ASP.NET Core 3. x veya 5,0 RC1 veya sonraki bir sürüme yükseltme yapmak için kendi kodunuzu değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ff33e-130">An app and using ASP.NET Core 3.x or upgrading to 5.0 RC1 or later, you don't need to change your own code.</span></span> <span data-ttu-id="ff33e-131">Ancak, bu değişiklik için hesaba yükseltilen bir kitaplığa bağlı değilseniz, bu kitaplığın daha yeni bir sürümüne güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff33e-131">However, if you depend on a library that upgraded to account for this change, then you need to update to a newer version of that library.</span></span>
* <span data-ttu-id="ff33e-132">Bir kitaplık ve yalnızca ASP.NET Core 5,0 RC1 veya üstünü desteklemek istiyorsanız, herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ff33e-132">A library and want to support only ASP.NET Core 5.0 RC1 or later, no action is needed.</span></span> <span data-ttu-id="ff33e-133">Yalnızca proje dosyanızın bir `<TargetFramework>` değeri `net5.0` veya daha sonraki bir sürümü bildirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ff33e-133">Just ensure that your project file declares a `<TargetFramework>` value of `net5.0` or a later version.</span></span>
* <span data-ttu-id="ff33e-134">Bir kitaplık ve ASP.NET Core 3. x *ve* 5,0 ' i desteklemek istiyorsanız, kodunuzun herhangi bir üyeyi okuyup okumadığını saptayın `RenderTreeFrame` .</span><span class="sxs-lookup"><span data-stu-id="ff33e-134">A library and want to support both ASP.NET Core 3.x *and* 5.0, determine whether your code reads any `RenderTreeFrame` members.</span></span> <span data-ttu-id="ff33e-135">Örneğin, değerlendirme `someRenderTreeFrame.FrameType` .</span><span class="sxs-lookup"><span data-stu-id="ff33e-135">For example, evaluating `someRenderTreeFrame.FrameType`.</span></span>
  * <span data-ttu-id="ff33e-136">Çoğu kitaplık `RenderTreeFrame` , bileşenleri içeren kitaplıklar da dahil olmak üzere, üyeleri okummaz `.razor` .</span><span class="sxs-lookup"><span data-stu-id="ff33e-136">Most libraries won't read `RenderTreeFrame` members, including libraries that contain `.razor` components.</span></span> <span data-ttu-id="ff33e-137">Bu durumda, hiçbir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ff33e-137">In this case, no action is needed.</span></span>
  * <span data-ttu-id="ff33e-138">Ancak, kitaplığınız bunu destekliyorsa, hem hem de desteklemek için birden çok hedef gerekir `netstandard2.1` `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="ff33e-138">However, if your library does that, you'll need to multi-target to support both `netstandard2.1` and `net5.0`.</span></span> <span data-ttu-id="ff33e-139">Proje dosyanıza aşağıdaki değişiklikleri uygulayın:</span><span class="sxs-lookup"><span data-stu-id="ff33e-139">Apply the following changes in your project file:</span></span>
    * <span data-ttu-id="ff33e-140">Var olan `<TargetFramework>` öğeyi ile değiştirin `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>` .</span><span class="sxs-lookup"><span data-stu-id="ff33e-140">Replace the existing `<TargetFramework>` element with `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>`.</span></span>
    * <span data-ttu-id="ff33e-141">`Microsoft.AspNetCore.Components`Desteklemek istediğiniz her iki sürümü de hesaba eklemek için koşullu paket başvurusu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ff33e-141">Use a conditional `Microsoft.AspNetCore.Components` package reference to account for both versions you wish to support.</span></span> <span data-ttu-id="ff33e-142">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ff33e-142">For example:</span></span>

        ```xml
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="3.0.0" Condition="'$(TargetFramework)' == 'netstandard2.0'" />
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="5.0.0-rc.1.*" Condition="'$(TargetFramework)' != 'netstandard2.0'" />
        ```

<span data-ttu-id="ff33e-143">Daha fazla açıklama için, [ @jsakamoto `Toolbelt.Blazor.HeadElement` kitaplığın zaten nasıl yükseltildiğini gösteren bu fark](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ff33e-143">For further clarification, see this [diff showing how @jsakamoto already upgraded the `Toolbelt.Blazor.HeadElement` library](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ff33e-144">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ff33e-144">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame`

-->
