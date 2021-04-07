---
title: .NET çalışma zamanı tanımlayıcısı (RID) kataloğu
description: Çalışma zamanı tanımlayıcısı (RID) ve RID 'Lerin .NET 'te nasıl kullanıldığını öğrenin.
ms.date: 01/28/2021
ms.openlocfilehash: 87fbad990fce5431769fa1631be7e079c2eb27a5
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496676"
---
# <a name="net-rid-catalog"></a><span data-ttu-id="29e9c-103">.NET RID kataloğu</span><span class="sxs-lookup"><span data-stu-id="29e9c-103">.NET RID Catalog</span></span>

<span data-ttu-id="29e9c-104">*Çalışma zamanı tanımlayıcısı* için RID kısadır.</span><span class="sxs-lookup"><span data-stu-id="29e9c-104">RID is short for *Runtime Identifier*.</span></span> <span data-ttu-id="29e9c-105">RID değerleri, uygulamanın çalıştığı hedef platformları belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29e9c-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="29e9c-106">.NET paketleri tarafından, NuGet paketlerindeki platforma özgü varlıkları göstermek için kullanılırlar.</span><span class="sxs-lookup"><span data-stu-id="29e9c-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="29e9c-107">Aşağıdaki değerler, rids örnekleri: `linux-x64` , `ubuntu.14.04-x64` , `win7-x64` veya `osx.10.12-x64` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="29e9c-108">Yerel bağımlılıklara sahip paketler için RID, paketin geri yüklenebileceği platformları belirler.</span><span class="sxs-lookup"><span data-stu-id="29e9c-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="29e9c-109">Tek bir RID, `<RuntimeIdentifier>` proje dosyanızın öğesinde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="29e9c-110">Çoklu RID 'Ler, proje dosyasının öğesinde noktalı virgülle ayrılmış bir liste olarak tanımlanabilir `<RuntimeIdentifiers>` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="29e9c-111">Bunlar ayrıca, `--runtime` aşağıdaki [.net CLI komutlarıyla](./tools/index.md)seçeneği aracılığıyla da kullanılır:</span><span class="sxs-lookup"><span data-stu-id="29e9c-111">They're also used via the `--runtime` option with the following [.NET CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="29e9c-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="29e9c-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="29e9c-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="29e9c-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="29e9c-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="29e9c-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="29e9c-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="29e9c-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="29e9c-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="29e9c-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="29e9c-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="29e9c-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="29e9c-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="29e9c-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="29e9c-119">Somut işletim sistemlerini temsil eden RID 'Ler genellikle şu düzene uyar: `[os].[version]-[architecture]-[additional qualifiers]` burada:</span><span class="sxs-lookup"><span data-stu-id="29e9c-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="29e9c-120">`[os]` işletim/platform sistem adıdır.</span><span class="sxs-lookup"><span data-stu-id="29e9c-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="29e9c-121">Örneğin, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="29e9c-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="29e9c-122">`[version]` , bir noktayla ayrılmış () sürüm numarası biçimindeki işletim sistemi sürümüdür `.` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="29e9c-123">Örneğin, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="29e9c-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="29e9c-124">Sürüm, genellikle farklı platform API yüzey alanı ile birlikte işletim sisteminin birden fazla ayrı sürümünü temsil ettiğinden, **Pazarlama sürümü olmamalıdır** .</span><span class="sxs-lookup"><span data-stu-id="29e9c-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="29e9c-125">`[architecture]` işlemci mimarisidir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="29e9c-126">Örneğin: `x86` ,, `x64` `arm` veya `arm64` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="29e9c-127">`[additional qualifiers]` farklı platformları daha da birbirinden ayırt edin.</span><span class="sxs-lookup"><span data-stu-id="29e9c-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="29e9c-128">Örneğin: `aot`.</span><span class="sxs-lookup"><span data-stu-id="29e9c-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="29e9c-129">RID grafiği</span><span class="sxs-lookup"><span data-stu-id="29e9c-129">RID graph</span></span>

<span data-ttu-id="29e9c-130">RID Graf veya çalışma zamanı geri dönüş grafiği, birbirleriyle uyumlu RID 'lerin bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="29e9c-131">RID 'Ler, [Microsoft. NETCore. Platform](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) paketinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="29e9c-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="29e9c-132">Desteklenen RID 'lerin listesini, depoda bulunan dosyada [*runtime.js*](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) , RID grafiğinin listesini görebilirsiniz `dotnet/runtime` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) file, which is located in the `dotnet/runtime` repository.</span></span> <span data-ttu-id="29e9c-133">Bu dosyada, temel öğe hariç tüm RID 'lerin bir ekstre içerdiğini görebilirsiniz `"#import"` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="29e9c-134">Bu deyimler, uyumlu RID 'Ler gösterir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="29e9c-135">NuGet paketleri geri yüklediğinde, belirtilen çalışma zamanı için tam bir eşleşme bulmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="29e9c-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="29e9c-136">Tam eşleşme bulunamazsa NuGet, RID grafiğine göre en yakın uyumlu sistemi bulana kadar grafiği geri yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="29e9c-137">Aşağıdaki örnek, RID için gerçek giriştir `osx.10.12-x64` :</span><span class="sxs-lookup"><span data-stu-id="29e9c-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="29e9c-138">Yukarıdaki RID, `osx.10.12-x64` içeri aktarmaların belirtir `osx.10.11-x64` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="29e9c-139">Bu nedenle, NuGet paketleri geri yüklediğinde, pakette tam eşleşmeyi bulmaya çalışır  `osx.10.12-x64` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="29e9c-140">NuGet belirli çalışma zamanını bulamazsa, örneğin çalışma zamanlarını belirten paketleri geri yükleyebilir `osx.10.11-x64` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="29e9c-141">Aşağıdaki örnek, dosyasında *runtime.js*  de tanımlanan biraz daha büyük bir RID grafiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="29e9c-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

<span data-ttu-id="29e9c-142">Tüm RID 'Ler sonunda kök RID 'e geri eşlenir `any` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="29e9c-143">RID 'Ler hakkında, bunlarla çalışırken göz önünde bulundurmanız gereken bazı noktalar vardır:</span><span class="sxs-lookup"><span data-stu-id="29e9c-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="29e9c-144">Bileşen parçalarını almak için RID ayrıştırmaya çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="29e9c-144">Don't try to parse RIDs to retrieve component parts.</span></span>
- <span data-ttu-id="29e9c-145">Program aracılığıyla RID oluşturma.</span><span class="sxs-lookup"><span data-stu-id="29e9c-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="29e9c-146">Platform için önceden tanımlanmış olan RID 'leri kullanın.</span><span class="sxs-lookup"><span data-stu-id="29e9c-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="29e9c-147">RID 'Lerin özel olması gerekir, bu nedenle gerçek RID değerinden herhangi bir şeyi varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="29e9c-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="29e9c-148">RID 'leri kullanma</span><span class="sxs-lookup"><span data-stu-id="29e9c-148">Using RIDs</span></span>

<span data-ttu-id="29e9c-149">RID 'leri kullanabilmeniz için hangi RID 'Lerin mevcut olduğunu bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="29e9c-150">Yeni değerler platforma düzenli olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="29e9c-151">En son ve tüm sürüm için depodaki [runtime.js](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) dosyasına bakın `dotnet/runtime` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) file in the `dotnet/runtime` repository.</span></span>

<span data-ttu-id="29e9c-152">Taşınabilir RID 'Ler, belirli bir sürüme veya işletim sistemi dağıtımına bağlı olmayan RID grafiğine eklenen değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-152">Portable RIDs are values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="29e9c-153">Çoğu dağıtım merkezi taşınabilir RID 'lerle eşlendiğinden, özellikle birden çok Linux ile ilgilenirken tercih edilen seçenektir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-153">They are the preferred choice, especially when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="29e9c-154">Aşağıdaki liste, her bir işletim sistemi için kullanılan en yaygın RID 'lerin küçük bir alt kümesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-154">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="29e9c-155">Windows RID 'leri</span><span class="sxs-lookup"><span data-stu-id="29e9c-155">Windows RIDs</span></span>

<span data-ttu-id="29e9c-156">Yalnızca ortak değerler listelenir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-156">Only common values are listed.</span></span> <span data-ttu-id="29e9c-157">En son ve tüm sürüm için depodaki [runtime.js](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) dosyasına bakın `dotnet/runtime` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-157">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) file in the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="29e9c-158">In</span><span class="sxs-lookup"><span data-stu-id="29e9c-158">Portable</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="29e9c-159">Windows 7/Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="29e9c-159">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="29e9c-160">Windows 8.1/Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="29e9c-160">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="29e9c-161">Windows 10/Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="29e9c-161">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="29e9c-162">Daha fazla bilgi için bkz. [.net bağımlılıkları ve gereksinimleri](./install/windows.md#dependencies).</span><span class="sxs-lookup"><span data-stu-id="29e9c-162">For more information, see [.NET dependencies and requirements](./install/windows.md#dependencies).</span></span>

## <a name="linux-rids"></a><span data-ttu-id="29e9c-163">Linux RID 'leri</span><span class="sxs-lookup"><span data-stu-id="29e9c-163">Linux RIDs</span></span>

<span data-ttu-id="29e9c-164">Yalnızca ortak değerler listelenir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-164">Only common values are listed.</span></span> <span data-ttu-id="29e9c-165">En son ve tüm sürüm için depodaki [runtime.js](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) dosyasına bakın `dotnet/runtime` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-165">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) file in the `dotnet/runtime` repository.</span></span> <span data-ttu-id="29e9c-166">Aşağıda listelenmeyen bir dağıtımı çalıştıran cihazlar taşınabilir RID 'Ler ile çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-166">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="29e9c-167">Örneğin, listelenmemiş bir Linux dağıtımını çalıştıran Raspberry PI cihazları ile hedeflenebilir `linux-arm` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-167">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="29e9c-168">In</span><span class="sxs-lookup"><span data-stu-id="29e9c-168">Portable</span></span>
  - <span data-ttu-id="29e9c-169">`linux-x64` (CentOS, deler, Fedora, Ubuntu ve türetmeler gibi masaüstü dağıtımlarını en iyi şekilde)</span><span class="sxs-lookup"><span data-stu-id="29e9c-169">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu, and derivatives)</span></span>
  - <span data-ttu-id="29e9c-170">`linux-musl-x64` (Alp Linux gibi [MUSL](https://wiki.musl-libc.org/projects-using-musl.html) kullanan hafif dağıtımlar)</span><span class="sxs-lookup"><span data-stu-id="29e9c-170">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="29e9c-171">`linux-arm` (Raspbian gibi ARM üzerinde çalışan Linux dağıtımları Raspberry PI model 2 +)</span><span class="sxs-lookup"><span data-stu-id="29e9c-171">`linux-arm` (Linux distributions running on ARM like Raspbian on Raspberry Pi Model 2+)</span></span>
  - <span data-ttu-id="29e9c-172">`linux-arm64` (Raspberry PI model 3 + üzerinde Ubuntu Server 64-bit gibi 64 bit ARM üzerinde çalışan Linux dağıtımları</span><span class="sxs-lookup"><span data-stu-id="29e9c-172">`linux-arm64` (Linux distributions running on 64-bit ARM like Ubuntu Server 64-bit on Raspberry Pi Model 3+)</span></span>
- <span data-ttu-id="29e9c-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="29e9c-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="29e9c-174">`rhel-x64` (X sürüm 6 ' dan önce `linux-x64` RHEL için yerine geçti)</span><span class="sxs-lookup"><span data-stu-id="29e9c-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - `rhel.6-x64`
- <span data-ttu-id="29e9c-175">Tizen</span><span class="sxs-lookup"><span data-stu-id="29e9c-175">Tizen</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="29e9c-176">Daha fazla bilgi için bkz. [.net bağımlılıkları ve gereksinimleri](./install/linux.md).</span><span class="sxs-lookup"><span data-stu-id="29e9c-176">For more information, see [.NET dependencies and requirements](./install/linux.md).</span></span>

## <a name="macos-rids"></a><span data-ttu-id="29e9c-177">macOS RIDs</span><span class="sxs-lookup"><span data-stu-id="29e9c-177">macOS RIDs</span></span>

<span data-ttu-id="29e9c-178">macOS 'Ler eski "OSX" markasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="29e9c-178">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="29e9c-179">Yalnızca ortak değerler listelenir.</span><span class="sxs-lookup"><span data-stu-id="29e9c-179">Only common values are listed.</span></span> <span data-ttu-id="29e9c-180">En son ve tüm sürüm için depodaki [runtime.js](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) dosyasına bakın `dotnet/runtime` .</span><span class="sxs-lookup"><span data-stu-id="29e9c-180">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) file in the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="29e9c-181">In</span><span class="sxs-lookup"><span data-stu-id="29e9c-181">Portable</span></span>
  - <span data-ttu-id="29e9c-182">`osx-x64` (En düşük işletim sistemi sürümü macOS 10,12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="29e9c-182">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="29e9c-183">macOS 10,10 Yosemite</span><span class="sxs-lookup"><span data-stu-id="29e9c-183">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="29e9c-184">macOS 10,11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="29e9c-184">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="29e9c-185">macOS 10,12 Sierra</span><span class="sxs-lookup"><span data-stu-id="29e9c-185">macOS 10.12 Sierra</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="29e9c-186">macOS 10,13 High Sierra</span><span class="sxs-lookup"><span data-stu-id="29e9c-186">macOS 10.13 High Sierra</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="29e9c-187">macOS 10,14 Mojave</span><span class="sxs-lookup"><span data-stu-id="29e9c-187">macOS 10.14 Mojave</span></span>
  - `osx.10.14-x64`
- <span data-ttu-id="29e9c-188">macOS 10,15 Catalina</span><span class="sxs-lookup"><span data-stu-id="29e9c-188">macOS 10.15 Catalina</span></span>
  - `osx.10.15-x64`
- <span data-ttu-id="29e9c-189">macOS 11,01 Big Sur</span><span class="sxs-lookup"><span data-stu-id="29e9c-189">macOS 11.01 Big Sur</span></span>
  - `osx.11.0-x64`
  - `osx.11.0-arm64`

<span data-ttu-id="29e9c-190">Daha fazla bilgi için bkz. [.net bağımlılıkları ve gereksinimleri](./install/macos.md#dependencies).</span><span class="sxs-lookup"><span data-stu-id="29e9c-190">For more information, see [.NET dependencies and requirements](./install/macos.md#dependencies).</span></span>

## <a name="see-also"></a><span data-ttu-id="29e9c-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29e9c-191">See also</span></span>

- [<span data-ttu-id="29e9c-192">Çalışma zamanı kimlikleri</span><span class="sxs-lookup"><span data-stu-id="29e9c-192">Runtime IDs</span></span>](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/readme.md)
