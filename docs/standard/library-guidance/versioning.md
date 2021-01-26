---
title: Sürüm oluşturma ve .NET kitaplıkları
description: .NET kitaplıklarını sürüm oluşturma için en iyi yöntem önerileri.
ms.date: 01/26/2021
ms.openlocfilehash: 1f3a14a7c32091621dda30a2d86724915d629564
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794724"
---
# <a name="versioning"></a><span data-ttu-id="d2fe0-103">Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2fe0-103">Versioning</span></span>

<span data-ttu-id="d2fe0-104">Yazılım kitaplığı sürüm 1,0 ' de nadiren tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="d2fe0-105">İyi kitaplıklar zaman içinde geliştikçe, özellikler eklenerek, hataları düzeltiyor ve performansı artırdı.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-105">Good libraries evolve over time, adding features, fixing bugs, and improving performance.</span></span> <span data-ttu-id="d2fe0-106">Mevcut kullanıcıları bozmadan, her bir sürümle ek değer sağlayan bir .NET kitaplığının yeni sürümlerini yayınlanbilmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="d2fe0-107">Yeni değişiklikler</span><span class="sxs-lookup"><span data-stu-id="d2fe0-107">Breaking changes</span></span>

<span data-ttu-id="d2fe0-108">Sürümler arasındaki önemli değişiklikleri işleme hakkında daha fazla bilgi için bkz. [son değişiklikler](./breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="d2fe0-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="d2fe0-109">Sürüm numaraları</span><span class="sxs-lookup"><span data-stu-id="d2fe0-109">Version numbers</span></span>

<span data-ttu-id="d2fe0-110">.NET kitaplığı, bir sürümü belirtmek için birçok yol sunar.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="d2fe0-111">Bu sürümler en önemli öneme sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d2fe0-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="d2fe0-112">NuGet paket sürümü</span><span class="sxs-lookup"><span data-stu-id="d2fe0-112">NuGet package version</span></span>

<span data-ttu-id="d2fe0-113">[NuGet paket sürümü](/nuget/reference/package-versioning) , NuGet.org, Visual Studio NuGet Paket Yöneticisi ve paket kullanıldığında kaynak koda eklenir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="d2fe0-114">NuGet paket sürümü, kullanıcıların yaygın olarak görebilecekleri sürüm numarasıdır ve kullandıkları bir kitaplığın sürümü hakkında konuşduklarında bu bilgileri ifade eder.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="d2fe0-115">NuGet paket sürümü NuGet tarafından kullanılır ve çalışma zamanı davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="d2fe0-116">NuGet paket sürümü ile birlikte bulunan NuGet paket tanımlayıcısı, NuGet içindeki bir paketi tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="d2fe0-117">Örneğin, `Newtonsoft.Json` + `11.0.2`.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="d2fe0-118">Soneki olan bir paket yayın öncesi paketidir ve test için ideal hale getiren özel davranışları vardır.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="d2fe0-119">Daha fazla bilgi için bkz. [yayın öncesi paketleri](./nuget.md#pre-release-packages).</span><span class="sxs-lookup"><span data-stu-id="d2fe0-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="d2fe0-120">NuGet paketi sürümü geliştiricilerin en çok görülebilen sürümü olduğu için, [anlamsal sürüm oluşturma (SemVer)](https://semver.org/)kullanılarak güncelleştirilmesi iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="d2fe0-121">SemVer, yayın arasındaki değişikliklerin önemini gösterir ve geliştiricilerin hangi sürümü kullanacağınızı seçerken bilinçli bir karar vermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="d2fe0-122">Örneğin, ' dan ' a giderek, `1.0` `2.0` olası büyük değişiklikler olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="d2fe0-123">✔️ NuGet paketinizi sürüm için [Semver 2.0.0](https://semver.org/) kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-123">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="d2fe0-124">✔️, kullanıcıların yaygın olarak göreceği sürüm numarası olduğundan, ortak belgelerde NuGet paketi sürümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-124">✔️ DO use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="d2fe0-125">kararlı olmayan bir paket yayınlarken yayın öncesi son eki dahil ✔️.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-125">✔️ DO include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="d2fe0-126">Kullanıcılar, yayın öncesi paketleri almak için kabul etmelidir, dolayısıyla paketin tamamlanmamış olduğunu anlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="d2fe0-127">Derleme sürümü</span><span class="sxs-lookup"><span data-stu-id="d2fe0-127">Assembly version</span></span>

<span data-ttu-id="d2fe0-128">Derleme sürümü, CLR 'nin hangi derleme sürümünü yükleneceğini seçmek için çalışma zamanında kullandığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-128">The assembly version is what the CLR uses at run time to select which version of an assembly to load.</span></span> <span data-ttu-id="d2fe0-129">Sürüm oluşturma kullanılarak bir derlemeyi seçmek, yalnızca güçlü bir ada sahip derlemeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="d2fe0-130">.NET Framework CLR, tanımlayıcı adlı bir derlemeyi yüklemek için tam bir eşleşme talep ister.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-130">The .NET Framework CLR demands an exact match to load a strong-named assembly.</span></span> <span data-ttu-id="d2fe0-131">Örneğin, `Libary1, Version=1.0.0.0` bir başvurusu ile derlendi `Newtonsoft.Json, Version=11.0.0.0` .</span><span class="sxs-lookup"><span data-stu-id="d2fe0-131">For example, `Libary1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="d2fe0-132">.NET Framework bu sürümü yalnızca tam olarak yükler `11.0.0.0` .</span><span class="sxs-lookup"><span data-stu-id="d2fe0-132">.NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="d2fe0-133">Çalışma zamanında farklı bir sürüm yüklemek için .NET uygulamasının yapılandırma dosyasına bir bağlama yeniden yönlendirmesi eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-133">To load a different version at run time, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="d2fe0-134">Bütünleştirilmiş kod sürümüyle birlikte tanımlayıcı adlandırma [katı derleme sürümü yüklemeye](../assembly/versioning.md)izin vermez.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-134">Strong naming combined with assembly version enables [strict assembly version loading](../assembly/versioning.md).</span></span> <span data-ttu-id="d2fe0-135">Bir kitaplıkta güçlü adlandırma, bir dizi avantaja sahip olsa da, genellikle bir derlemenin bulunamamasına neden olan çalışma zamanı özel durumları ile sonuçlanır ve ' de veya düzeltilmesi için [bağlama yeniden yönlendirmeleri gerekir](../../framework/configure-apps/redirect-assembly-versions.md) `app.config` `web.config` .</span><span class="sxs-lookup"><span data-stu-id="d2fe0-135">While strong naming a library has a number of benefits, it often results in run-time exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config` or `web.config` to be fixed.</span></span> <span data-ttu-id="d2fe0-136">.NET Core 'da, derleme yükleme daha gevşek olur.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-136">In .NET Core, assembly loading is more relaxed.</span></span> <span data-ttu-id="d2fe0-137">.NET Core çalışma zamanı, derlemeleri çalışma zamanında daha yüksek bir sürümle otomatik olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-137">The .NET Core runtime automatically loads assemblies with a higher version at run time.</span></span>

<span data-ttu-id="d2fe0-138">✔️ yalnızca AssemblyVersion içinde önemli bir sürüm dahil olmak üzere göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-138">✔️ CONSIDER only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="d2fe0-139">Örneğin, Library 1,0 ve Library 1.0.1 'in AssemblyVersion `1.0.0.0` 'ı vardır, ancak kitaplığı 2,0 ' nin AssemblyVersion 'ı vardır `2.0.0.0` .</span><span class="sxs-lookup"><span data-stu-id="d2fe0-139">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="d2fe0-140">Derleme sürümü genellikle daha az değiştiğinde bağlama yeniden yönlendirmelerini azaltır.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-140">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="d2fe0-141">✔️ AssemblyVersion 'ın ana sürüm numarasını ve NuGet paket sürümünü eşitlenmiş halde tutmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-141">✔️ CONSIDER keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="d2fe0-142">AssemblyVersion, kullanıcıya görüntülenen bazı bilgilendirici iletilere, örneğin, özel durum iletilerinde derleme adı ve derleme nitelikli tür adlarına dahildir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-142">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="d2fe0-143">Sürümler arasındaki ilişkinin saklanması, geliştiriciler tarafından hangi sürümü kullandıkları hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-143">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="d2fe0-144">❌ Sabit bir AssemblyVersion yok.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-144">❌ DO NOT have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="d2fe0-145">Bir AssemblyVersion, bağlama yeniden yönlendirmeleri gereksinimini ortadan kaldırdıkça, derlemenin yalnızca tek bir sürümünün genel derleme önbelleği 'ne (GAC) yüklenebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-145">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="d2fe0-146">Ayrıca, GAC 'de derlemeye başvuruda bulunan uygulamalar, başka bir uygulama GAC derlemesini bozan değişikliklerle güncelleştirmiş olursa kesilir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-146">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="d2fe0-147">Bütünleştirilmiş kod dosyası sürümü</span><span class="sxs-lookup"><span data-stu-id="d2fe0-147">Assembly file version</span></span>

<span data-ttu-id="d2fe0-148">Derleme dosyası sürümü, Windows 'ta bir dosya sürümünü göstermek için kullanılır ve çalışma zamanı davranışına hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-148">The assembly file version is used to display a file version in Windows and has no effect on run-time behavior.</span></span> <span data-ttu-id="d2fe0-149">Bu sürümün ayarlanması isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-149">Setting this version is optional.</span></span> <span data-ttu-id="d2fe0-150">Windows Gezgini 'nde dosya özellikleri iletişim kutusunda görünür:</span><span class="sxs-lookup"><span data-stu-id="d2fe0-150">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="d2fe0-151">![Windows Gezgini](./media/versioning/win-properties.png "Windows Gezgini")</span><span class="sxs-lookup"><span data-stu-id="d2fe0-151">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

<span data-ttu-id="d2fe0-152">✔️ AssemblyFileVersion düzeltmesi olarak bir sürekli tümleştirme yapı numarası dahil etmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-152">✔️ CONSIDER including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="d2fe0-153">Örneğin, projenizin sürüm 1.0.0 derleniyor ve sürekli tümleştirme derleme numarası 99 ' dir; bu nedenle AssemblyFileVersion 1.0.0.99.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-153">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

<span data-ttu-id="d2fe0-154">✔️ dosya sürümü biçimini kullanır `Major.Minor.Build.Revision` .</span><span class="sxs-lookup"><span data-stu-id="d2fe0-154">✔️ DO use the format `Major.Minor.Build.Revision` for file version.</span></span>

> <span data-ttu-id="d2fe0-155">Dosya sürümü hiçbir şekilde .NET tarafından kullanılmadığından, [Windows dosya sürümünün](/windows/desktop/menurc/versioninfo-resource) biçimde olmasını bekler `Major.Minor.Build.Revision` .</span><span class="sxs-lookup"><span data-stu-id="d2fe0-155">While the file version is never used by .NET, [Windows expects the file version](/windows/desktop/menurc/versioninfo-resource) to be in the `Major.Minor.Build.Revision` format.</span></span> <span data-ttu-id="d2fe0-156">Sürüm bu biçimi izmezse bir uyarı tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-156">A warning is raised if the version doesn't follow this format.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="d2fe0-157">Derleme bilgilendirici sürümü</span><span class="sxs-lookup"><span data-stu-id="d2fe0-157">Assembly informational version</span></span>

<span data-ttu-id="d2fe0-158">Derleme bilgilendirici sürümü, ek sürüm bilgilerini kaydetmek için kullanılır ve çalışma zamanı davranışına hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-158">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="d2fe0-159">Bu sürümün ayarlanması isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-159">Setting this version is optional.</span></span> <span data-ttu-id="d2fe0-160">Kaynak bağlantısı kullanıyorsanız, bu sürüm NuGet paketi sürümü ve kaynak denetimi sürümü ile derleme üzerinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-160">If you're using Source Link, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="d2fe0-161">Örneğin, `1.0.0-beta1+204ff0a` derlemenin oluşturulduğu kaynak kodun COMMIT karmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-161">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="d2fe0-162">Daha fazla bilgi için bkz. [kaynak bağlantısı](./sourcelink.md).</span><span class="sxs-lookup"><span data-stu-id="d2fe0-162">For more information, see [Source Link](./sourcelink.md).</span></span>

```xml
<InformationalVersion>The quick brown fox jumped over the lazy dog.</InformationalVersion>
```

> [!NOTE]
> <span data-ttu-id="d2fe0-163">Visual Studio 'nun eski sürümleri, bu sürüm biçimini izmazsa derleme uyarısı oluşturur `Major.Minor.Build.Revision` .</span><span class="sxs-lookup"><span data-stu-id="d2fe0-163">Older versions of Visual Studio raise a build warning if this version doesn't follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="d2fe0-164">Uyarı güvenle yoksayılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-164">The warning can be safely ignored.</span></span>

<span data-ttu-id="d2fe0-165">❌ Derleme bilgilendirici sürümünü kendiniz ayarlamaktan KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-165">❌ AVOID setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="d2fe0-166">SourceLink 'in NuGet ve kaynak denetimi meta verilerini içeren sürümü otomatik olarak oluşturmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="d2fe0-166">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d2fe0-167">[Önceki](publish-nuget-package.md) 
> [Sonraki](breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="d2fe0-167">[Previous](publish-nuget-package.md)
[Next](breaking-changes.md)</span></span>
