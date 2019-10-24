---
title: .NET Standard’daki Yenilikler
description: Bu makalede, .NET Standard her yeni sürümünde bulunan yeni özellikler ve geliştirmeler özetlenmektedir.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f69dfe77e5d485c4c7ffcbf2b98657eab87d452d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775229"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="a72fd-103">.NET Standard’daki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="a72fd-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="a72fd-104">.NET Standard, standart sürümü olan .NET uygulamalarında kullanılabilir olması gereken, sürümlenmiş bir API kümesini tanımlayan bir biçimsel belirtimdir.</span><span class="sxs-lookup"><span data-stu-id="a72fd-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="a72fd-105">.NET Standard, kitaplık geliştiricileri 'ne yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="a72fd-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="a72fd-106">.NET Standard sürümünü hedefleyen bir kitaplık, standart sürümünü destekleyen tüm .NET Framework, .NET Core veya Xamarin uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a72fd-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="a72fd-107">.NET Standard en son sürümü 2,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="a72fd-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="a72fd-108">.NET Core 2,0 SDK 'sının yanı sıra .NET Core iş yükünün yüklü olduğu Visual Studio 2017 sürüm 15,3 ile de birlikte bulunur.</span><span class="sxs-lookup"><span data-stu-id="a72fd-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="a72fd-109">Desteklenen .NET uygulamaları</span><span class="sxs-lookup"><span data-stu-id="a72fd-109">Supported .NET implementations</span></span>

<span data-ttu-id="a72fd-110">.NET Standard 2,0 aşağıdaki .NET uygulamaları tarafından desteklenir:</span><span class="sxs-lookup"><span data-stu-id="a72fd-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="a72fd-111">.NET Core 2,0 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="a72fd-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="a72fd-112">.NET Framework 4.6.1 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="a72fd-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="a72fd-113">Mono 5,4 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="a72fd-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="a72fd-114">Xamarin. iOS 10,14 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="a72fd-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="a72fd-115">Xamarin. Mac 3,8 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="a72fd-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="a72fd-116">Xamarin. Android 8,0 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="a72fd-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="a72fd-117">Evrensel Windows Platformu 10.0.16299 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="a72fd-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="a72fd-118">.NET Standard 2,0 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="a72fd-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="a72fd-119">.NET Standard 2,0 aşağıdaki yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="a72fd-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="a72fd-120">Büyük ölçüde genişletilmiş bir API kümesi</span><span class="sxs-lookup"><span data-stu-id="a72fd-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="a72fd-121">Sürüm 1,6 ' den .NET Standard, API 'lerin karşılaştırarak küçük bir alt kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="a72fd-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="a72fd-122">Dışlananlar arasında, .NET Framework veya Xamarin içinde yaygın olarak kullanılan birçok API.</span><span class="sxs-lookup"><span data-stu-id="a72fd-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="a72fd-123">Bu, geliştiricilerin birden çok .NET uygulamasını hedefleyen uygulamalar ve kitaplıklar geliştirdiklerinde tanıdık API 'Ler için uygun değişiklikleri bulmasını gerektirdiğinden geliştirmeyi karmaşıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="a72fd-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="a72fd-124">2,0 .NET Standard, Standard 'ın önceki sürümü olan .NET Standard 1,6 ' de bulunandan daha fazla 20.000 ' den fazla API ekleyerek bu sınırlamaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="a72fd-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="a72fd-125">2,0 .NET Standard eklenen API 'lerin bir listesi için, bkz. [.NET Standard 2,0 vs 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="a72fd-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="a72fd-126">.NET Standard 2,0 ' de <xref:System> ad alanına yapılan eklemelerin bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a72fd-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="a72fd-127">@No__t_0 sınıfı için destek.</span><span class="sxs-lookup"><span data-stu-id="a72fd-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="a72fd-128">@No__t_0 sınıfında ek üyelerden diziler ile çalışmaya yönelik daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="a72fd-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="a72fd-129">@No__t_0 sınıfında ek üyelerin öznitelikleriyle çalışma için daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="a72fd-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="a72fd-130">@No__t_0 değerler için daha iyi takvim desteği ve ek biçimlendirme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="a72fd-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="a72fd-131">Ek <xref:System.Decimal> yuvarlama işlevselliği.</span><span class="sxs-lookup"><span data-stu-id="a72fd-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="a72fd-132">@No__t_0 sınıfında ek işlevsellik.</span><span class="sxs-lookup"><span data-stu-id="a72fd-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="a72fd-133">@No__t_0 sınıfı aracılığıyla çöp toplayıcı üzerinde Gelişmiş denetim.</span><span class="sxs-lookup"><span data-stu-id="a72fd-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="a72fd-134">@No__t_0 sınıfında dize karşılaştırma, numaralandırma ve normalleştirme için geliştirilmiş destek.</span><span class="sxs-lookup"><span data-stu-id="a72fd-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="a72fd-135">@No__t_0 ve <xref:System.TimeZoneInfo.TransitionTime> sınıflarında gün ışığından yararlanma ayarlamaları ve geçiş süreleri için destek.</span><span class="sxs-lookup"><span data-stu-id="a72fd-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="a72fd-136">@No__t_0 sınıfında önemli ölçüde gelişmiş işlevsellik.</span><span class="sxs-lookup"><span data-stu-id="a72fd-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="a72fd-137">@No__t_0 ve <xref:System.Runtime.Serialization.StreamingContext> parametrelere sahip bir özel durum Oluşturucusu ekleyerek özel durum nesnelerinin serisini kaldırma için daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="a72fd-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="a72fd-138">.NET Framework kitaplıkları için destek</span><span class="sxs-lookup"><span data-stu-id="a72fd-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="a72fd-139">Kitaplıkların büyük bölümü .NET Standard yerine .NET Framework hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="a72fd-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="a72fd-140">Ancak, bu kitaplıklardaki çağrıların çoğu .NET Standard 2,0 ' ye dahil olan API 'lere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a72fd-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="a72fd-141">2,0 .NET Standard başlayarak, bir [Uyumluluk dolgusu](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification)kullanarak bir .NET Standard kitaplığından .NET Framework kitaplıklarına erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a72fd-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="a72fd-142">Bu uyumluluk katmanı geliştiriciler için saydamdır; .NET Framework kitaplıklarından yararlanmak için herhangi bir şey yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a72fd-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="a72fd-143">Tek gereksinim, .NET Framework sınıf kitaplığı tarafından çağrılan API 'Lerin .NET Standard 2,0 ' ye dahil edilmesini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a72fd-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="a72fd-144">Visual Basic için destek</span><span class="sxs-lookup"><span data-stu-id="a72fd-144">Support for Visual Basic</span></span>

<span data-ttu-id="a72fd-145">Artık Visual Basic .NET Standard kitaplıklarını geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a72fd-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="a72fd-146">.NET Core iş yükü yüklüyken Visual Studio 2017 sürüm 15,3 veya üstünü kullanan Visual Basic geliştiriciler için, Visual Studio artık bir .NET Standard sınıf kitaplığı şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="a72fd-146">For Visual Basic developers using Visual Studio 2017 version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="a72fd-147">Diğer geliştirme araçları ve ortamları kullanan Visual Basic geliştiriciler için, bir .NET Standard kitaplığı projesi oluşturmak üzere [DotNet New](../../core/tools/dotnet-new.md) komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a72fd-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="a72fd-148">Daha fazla bilgi için bkz. [.NET Standard kitaplıkları Için araç desteği](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="a72fd-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="a72fd-149">.NET Standard kitaplıkları için araç desteği</span><span class="sxs-lookup"><span data-stu-id="a72fd-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="a72fd-150">.NET Core 2,0 ve .NET Standard 2,0 sürümü ile hem Visual Studio 2017 hem de [.NET Core komut satırı arabirimi (CLI)](../../core/tools/index.md) , .NET Standard kitaplıkları oluşturmak için araç desteğini içerir.</span><span class="sxs-lookup"><span data-stu-id="a72fd-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="a72fd-151">Visual Studio 'Yu **.NET Core platformlar arası geliştirme** iş yüküyle birlikte yüklerseniz, aşağıdaki şekilde gösterildiği gibi bir proje şablonu kullanarak bir .NET Standard 2,0 kitaplık projesi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a72fd-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="a72fd-152">C#</span><span class="sxs-lookup"><span data-stu-id="a72fd-152">C#</span></span>](#tab/csharp)

![Yeni .NET Standard kitaplığı projesi Ekle](./media/std-project-cs.png)

<span data-ttu-id="a72fd-154">.NET Core CLI kullanıyorsanız, aşağıdaki [DotNet yeni](../../core/tools/dotnet-new.md) komut, .NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı projesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a72fd-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="a72fd-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a72fd-155">Visual Basic</span></span>](#tab/vb)

![Yeni .NET Standard kitaplığı projesi Ekle](./media/std-project-vb.png)

<span data-ttu-id="a72fd-157">.NET Core CLI kullanıyorsanız, aşağıdaki [DotNet yeni](../../core/tools/dotnet-new.md) komut, .NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı projesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a72fd-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="a72fd-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a72fd-158">See also</span></span>

- [<span data-ttu-id="a72fd-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="a72fd-159">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="a72fd-160">.NET Standard tanıtımı</span><span class="sxs-lookup"><span data-stu-id="a72fd-160">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
