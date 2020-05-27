---
title: .NET uygulamalarını genelleştirmek ve yerelleştirme
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET]
- globalization [.NET], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
ms.openlocfilehash: c5c601d18d92d9b57781bc8a09f26f0bc3a9216a
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842016"
---
# <a name="globalizing-and-localizing-net-applications"></a><span data-ttu-id="85224-102">.NET uygulamalarını genelleştirmek ve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="85224-102">Globalizing and localizing .NET applications</span></span>

<span data-ttu-id="85224-103">Bir veya daha fazla dilde yerelleştirilebilecek bir uygulama da dahil olmak üzere dünya çapında kullanılabilir bir uygulama geliştirme, üç adımdan oluşur: Genelleştirme, Yerelleştirilebilirlik incelemesi ve yerelleştirme.</span><span class="sxs-lookup"><span data-stu-id="85224-103">Developing a world-ready application, including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>

[<span data-ttu-id="85224-104">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="85224-104">Globalization</span></span>](globalization.md)

<span data-ttu-id="85224-105">Bu adım kültür ve dil açısından nötr olan ve tüm kullanıcılar için yerelleştirilmiş kullanıcı arabirimleri ve bölgesel verileri destekleyen bir uygulamanın tasarlanması ve kodlanmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="85224-105">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="85224-106">Tasarım yapma ve kültüre özgü varsayımlara dayalı olmayan kararları programlama ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="85224-106">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="85224-107">Global uygulamalar yerelleştirilmez, ancak daha sonra bir veya birden çok dile görece kolay yerelleştirilebilecek şekilde tasarlanır ve yazılırlar.</span><span class="sxs-lookup"><span data-stu-id="85224-107">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>

[<span data-ttu-id="85224-108">Yerelleştirilebilirlik incelemesi</span><span class="sxs-lookup"><span data-stu-id="85224-108">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="85224-109">Bu adım, bir uygulamanın kod ve tasarımının, kolayca yerelleştirilebilir olmasını sağlamak ve yerelleştirme için olası engelleri tanımlamak üzere gözden geçirilmesi ve uygulamanın yürütülebilir kodunun kaynaklarından ayrı olduğunun doğrulanması ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="85224-109">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="85224-110">Genelleştirme aşaması etkili olduysa, yerelleştirme incelemesi, genelleştirme sırasında yapılan tasarım ve kodlama seçimlerini onaylar.</span><span class="sxs-lookup"><span data-stu-id="85224-110">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="85224-111">Yerelleştirilebilirlik aşaması, bir uygulamanın kaynak kodunu yerelleştirme aşamasında değiştirmek zorunda kalmamanızı sağlayacak şekilde geri kalan sorunları tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="85224-111">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>

[<span data-ttu-id="85224-112">Localization (Yerelleştirme)</span><span class="sxs-lookup"><span data-stu-id="85224-112">Localization</span></span>](localization.md)

<span data-ttu-id="85224-113">Bu adım özel kültürler veya bölgeler için bir uygulamanın özelleştirilmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="85224-113">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="85224-114">Genelleştirme ve yerelleştirme adımları doğru olarak gerçekleştirilmişse, yerelleştirme, öncelikli olarak kullanıcı arabirimini çevirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="85224-114">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>

<span data-ttu-id="85224-115">Aşağıdaki üç adımı izlemenin iki avantajı vardır:</span><span class="sxs-lookup"><span data-stu-id="85224-115">Following these three steps provides two advantages:</span></span>

- <span data-ttu-id="85224-116">ABD İngilizcesi gibi tek bir kültürü desteklemek için tasarlanmış bir uygulamayı ek kültürleri desteklemek üzere yükseltmek zorunda kalmanızı önler.</span><span class="sxs-lookup"><span data-stu-id="85224-116">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>

- <span data-ttu-id="85224-117">Daha kararlı ve daha az hatası olan yerelleştirilmiş uygulamalar olarak sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="85224-117">It results in localized applications that are more stable and have fewer bugs.</span></span>

<span data-ttu-id="85224-118">.NET, dünya çapında ve yerelleştirilmiş uygulamaların geliştirilmesi için kapsamlı destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="85224-118">.NET provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="85224-119">Özellikle, .NET sınıf kitaplığındaki birçok üye türü, geçerli kullanıcının kültürünün veya belirtilen kültürün kurallarını yansıtan değerler döndürerek Genelleştirme 'ye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="85224-119">In particular, many type members in the .NET class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="85224-120">Ayrıca, .NET, bir uygulamayı yerelleştirme işlemini kolaylaştıran uydu derlemelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="85224-120">Also, .NET supports satellite assemblies, which facilitate the process of localizing an application.</span></span>

<span data-ttu-id="85224-121">Daha fazla bilgi için bkz. [Genelleştirme belgeleri](/globalization/).</span><span class="sxs-lookup"><span data-stu-id="85224-121">For additional information, see the [Globalization documentation](/globalization/).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="85224-122">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="85224-122">In this section</span></span>

[<span data-ttu-id="85224-123">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="85224-123">Globalization</span></span>](globalization.md)

<span data-ttu-id="85224-124">Nötr kültüre ve nötr dile sahip bir uygulama tasarlamayı ve kodlamayı da içeren, dünya çapında kullanılmaya hazır uygulama bir oluşturmanın ilk aşamasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="85224-124">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>

[<span data-ttu-id="85224-125">.NET Genelleştirme ve ıCU</span><span class="sxs-lookup"><span data-stu-id="85224-125">.NET globalization and ICU</span></span>](globalization-icu.md)

<span data-ttu-id="85224-126">.NET Genelleştirme 'nin [Unicode (ıCU) Için Uluslararası bileşenleri](http://site.icu-project.org/home)nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="85224-126">Describes how .NET globalization uses [International Components for Unicode (ICU)](http://site.icu-project.org/home).</span></span>

[<span data-ttu-id="85224-127">Yerelleştirilebilirlik incelemesi</span><span class="sxs-lookup"><span data-stu-id="85224-127">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="85224-128">Yerelleştirmede potansiyel bariyerler tanımlamayı da içeren yerelleştirilmiş uygulama oluşturmanın ikinci aşamasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="85224-128">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>

[<span data-ttu-id="85224-129">Localization (Yerelleştirme)</span><span class="sxs-lookup"><span data-stu-id="85224-129">Localization</span></span>](localization.md)

<span data-ttu-id="85224-130">Özel bölgeler ve kültürler için bir uygulamanın kullanıcı arabirimini özelleştirmeyi içeren yerelleştirilmiş bir uygulama oluşturmanın son adımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="85224-130">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>

[<span data-ttu-id="85224-131">Kültüre duyarsız dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="85224-131">Culture-insensitive string operations</span></span>](culture-insensitive-string-operations.md)

<span data-ttu-id="85224-132">Kültüre duyarsız sonuçlar elde etmek için varsayılan olarak kültüre duyarlı olan .NET yöntemlerinin ve sınıflarının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="85224-132">Describes how to use .NET methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>

[<span data-ttu-id="85224-133">Dünya çapında kullanmaya yönelik uygulamalar geliştirmek için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="85224-133">Best practices for developing world-ready applications</span></span>](best-practices-for-developing-world-ready-apps.md)

<span data-ttu-id="85224-134">Genelleştirme, yerelleştirme ve dünya çapında kullanılmaya hazır ASP.NET uygulamaları geliştirmek için izlenebilecek en iyi uygulamaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="85224-134">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>

## <a name="reference"></a><span data-ttu-id="85224-135">Başvuru</span><span class="sxs-lookup"><span data-stu-id="85224-135">Reference</span></span>

- <span data-ttu-id="85224-136"><xref:System.Globalization?displayProperty=nameWithType>uzayına</span><span class="sxs-lookup"><span data-stu-id="85224-136"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>

   <span data-ttu-id="85224-137">Bu ad alanındaki, dil, ülke/bölge, kullanılan takvimler, tarihler için biçim desenleri, para birimi, sayılar ve dizeler için sıralama düzeni gibi kültürle ilişkili bilgileri tanımlayan sınıflar içerir</span><span class="sxs-lookup"><span data-stu-id="85224-137">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>

- <span data-ttu-id="85224-138"><xref:System.Resources>uzayına</span><span class="sxs-lookup"><span data-stu-id="85224-138"><xref:System.Resources> namespace</span></span>

   <span data-ttu-id="85224-139">Kaynaklar oluşturmak, düzenlemek ve kullanmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="85224-139">Provides classes for creating, manipulating, and using resources.</span></span>

- <span data-ttu-id="85224-140"><xref:System.Text>uzayına</span><span class="sxs-lookup"><span data-stu-id="85224-140"><xref:System.Text> namespace</span></span>

   <span data-ttu-id="85224-141">ASCII, ANSI, Unicode ve diğer karakter kodlamalarını temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="85224-141">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>

- [<span data-ttu-id="85224-142">Resgen. exe (kaynak dosya Oluşturucu)</span><span class="sxs-lookup"><span data-stu-id="85224-142">Resgen.exe (Resource File Generator)</span></span>](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)

   <span data-ttu-id="85224-143">.txt dosyalarını ve XML tabanlı kaynak biçimi (.resx) dosyalarını ortak dil çalışma zamanı ikili .resources dosyalarına dönüştürmek için Resgen.exe öğesinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="85224-143">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>

- [<span data-ttu-id="85224-144">Winres. exe (Windows Forms Kaynak Düzenleyicisi)</span><span class="sxs-lookup"><span data-stu-id="85224-144">Winres.exe (Windows Forms Resource Editor)</span></span>](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)

   <span data-ttu-id="85224-145">Windows Forms formlarını yerelleştirmek için Winres.exe yürütme dosyasının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="85224-145">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>
