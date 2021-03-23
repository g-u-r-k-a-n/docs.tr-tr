---
title: .NET Framework ve .NET Core için projeleri düzenleme
description: Çözümlerini .NET Framework ve .NET Core ile yan yana derlemek isteyen proje sahipleri için yardım.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: 0d495ce7b21b45d3fabe444f117667e5908ac81a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873672"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="9886b-103">Projenizi hem .NET Framework hem de .NET Core 'ı destekleyecek şekilde düzenleyin</span><span class="sxs-lookup"><span data-stu-id="9886b-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="9886b-104">Hem .NET Framework hem de .NET Core yan yana için derlenen bir çözüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9886b-104">You can create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="9886b-105">Bu makalede, bu amaca ulaşmanıza yardımcı olacak çeşitli proje kuruluş seçenekleri ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9886b-105">This article covers several project-organization options to help you achieve this goal.</span></span> <span data-ttu-id="9886b-106">.NET Core ile proje düzeninizi ayarlamaya karar verirken göz önünde bulundurmanız gereken bazı tipik senaryolar aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9886b-106">Here are some typical scenarios to consider when you're deciding how to set up your project layout with .NET Core.</span></span> <span data-ttu-id="9886b-107">Liste istediğiniz her şeyi kapsamayabilir; projenizin ihtiyaçlarına göre öncelik verir.</span><span class="sxs-lookup"><span data-stu-id="9886b-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="9886b-108">**Mevcut projeleri ve .NET Core projelerini tek projeler halinde birleştirin**</span><span class="sxs-lookup"><span data-stu-id="9886b-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="9886b-109">*Bunun için uygun olan şey:*</span><span class="sxs-lookup"><span data-stu-id="9886b-109">*What this is good for:*</span></span>
  - <span data-ttu-id="9886b-110">Her biri farklı bir .NET Framework sürümü veya platformu hedefleyen birden çok proje yerine tek bir projeyi derleyerek yapı işleminizi basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="9886b-110">Simplifies your build process by compiling a single project rather than multiple projects that each target a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="9886b-111">Tek bir proje dosyasını yönetmeniz gerektiğinden, çok hedefli projeler için kaynak dosya yönetimini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="9886b-111">Simplifies source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="9886b-112">Kaynak dosyaları eklendiğinde veya kaldırılırken, alternatifler bunları diğer projelerinizle el ile eşitlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9886b-112">When adding or removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="9886b-113">Tüketim için kolayca bir NuGet paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9886b-113">Easily generate a NuGet package for consumption.</span></span>
  - <span data-ttu-id="9886b-114">Derleyici yönergelerinin kullanımı aracılığıyla kitaplıklarınızdaki belirli bir .NET Framework sürümü için kod yazmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9886b-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="9886b-115">*Desteklenmeyen senaryolar:*</span><span class="sxs-lookup"><span data-stu-id="9886b-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="9886b-116">Geliştiricilerin, var olan projeleri açmak için Visual Studio 2017 veya sonraki bir sürümü kullanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9886b-116">Requires developers to use Visual Studio 2017 or a later version to open existing projects.</span></span> <span data-ttu-id="9886b-117">Visual Studio 'nun eski sürümlerini desteklemek için, [Proje dosyalarınızın farklı klasörlerde tutulması](#support-vs) daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9886b-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="9886b-118">[**Mevcut projeleri ve yeni .NET Core projelerini ayrı tutun**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="9886b-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="9886b-119">*Bunun için uygun olan şey:*</span><span class="sxs-lookup"><span data-stu-id="9886b-119">*What this is good for:*</span></span>
  - <span data-ttu-id="9886b-120">, Visual Studio 2017 veya sonraki bir sürüme sahip olmayan geliştiriciler ve katkıda bulunanlar için mevcut projelerde geliştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="9886b-120">Supports development on existing projects for developers and contributors who may not have Visual Studio 2017 or a later version.</span></span>
  - <span data-ttu-id="9886b-121">Mevcut projelerde yeni hata oluşturma olasılığını azaltır çünkü bu projelerde hiçbir kod karmaşıklığı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9886b-121">Decreases the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="9886b-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="9886b-122">Example</span></span>

<span data-ttu-id="9886b-123">Aşağıdaki depoyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9886b-123">Consider the repository below:</span></span>

![Mevcut proje](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="9886b-125">**Kaynak Kodu**</span><span class="sxs-lookup"><span data-stu-id="9886b-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library/)

<span data-ttu-id="9886b-126">Aşağıda, mevcut projelerin kısıtlamalarına ve karmaşıklığına bağlı olarak bu depoya yönelik .NET Core desteği eklemenin çeşitli yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9886b-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="9886b-127">Mevcut projeleri çok hedefli bir .NET Core projesiyle değiştirme</span><span class="sxs-lookup"><span data-stu-id="9886b-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="9886b-128">Tüm mevcut *\* . csproj* dosyalarının kaldırılması ve birden çok çerçeveyi hedefleyen tek bir *\* . csproj* dosyası oluşturulması için depoyu yeniden düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="9886b-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="9886b-129">Tek bir proje farklı çerçeveler için derleyebildiğinden bu harika bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9886b-129">This is a great option, because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="9886b-130">Ayrıca hedeflenen çerçeveye göre farklı derleme seçeneklerini ve bağımlılıklarını işlemek için de güç vardır.</span><span class="sxs-lookup"><span data-stu-id="9886b-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Birden çok çerçeveyi hedefleyen bir csproj oluşturma](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="9886b-132">**Kaynak Kodu**</span><span class="sxs-lookup"><span data-stu-id="9886b-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="9886b-133">Notda yapılan değişiklikler:</span><span class="sxs-lookup"><span data-stu-id="9886b-133">Changes to note are:</span></span>

- <span data-ttu-id="9886b-134">*packages.config* ve *\* . csproj* 'un yeni bir [.NET Core *\* . csproj*](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library-csproj/src/Car/Car.csproj)ile değiştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="9886b-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="9886b-135">NuGet paketleri ile belirtilir `<PackageReference> ItemGroup` .</span><span class="sxs-lookup"><span data-stu-id="9886b-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="9886b-136">Mevcut projeleri tut ve bir .NET Core projesi oluştur</span><span class="sxs-lookup"><span data-stu-id="9886b-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="9886b-137">Eski çerçeveleri hedefleyen mevcut projeler varsa, bu projeleri dokunmadan bırakmak ve gelecekteki çerçeveleri hedeflemek için bir .NET Core projesi kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9886b-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Farklı klasördeki mevcut projeyi içeren .NET Core projesi](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="9886b-139">**Kaynak Kodu**</span><span class="sxs-lookup"><span data-stu-id="9886b-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/main/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="9886b-140">.NET Core ve var olan projeler ayrı klasörlerde tutulur.</span><span class="sxs-lookup"><span data-stu-id="9886b-140">The .NET Core and existing projects are kept in separate folders.</span></span> <span data-ttu-id="9886b-141">Projelerin ayrı klasörlerde tutulması, Visual Studio 2017 veya sonraki sürümlerini yapmanızı zorunlu tutar.</span><span class="sxs-lookup"><span data-stu-id="9886b-141">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="9886b-142">Yalnızca eski projeleri açan ayrı bir çözüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9886b-142">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9886b-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9886b-143">See also</span></span>

- [<span data-ttu-id="9886b-144">.NET Core taşıma belgeleri</span><span class="sxs-lookup"><span data-stu-id="9886b-144">.NET Core porting documentation</span></span>](index.md)
