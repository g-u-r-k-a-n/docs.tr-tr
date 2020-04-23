---
title: x:Subclass Yönergesi
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: e85e0fb5a0e1a865ed84a93767f8152a115bbe5f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071369"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="bca21-102">x:Subclass Yönergesi</span><span class="sxs-lookup"><span data-stu-id="bca21-102">x:Subclass Directive</span></span>

<span data-ttu-id="bca21-103">XAML biçimlendirmesi de sağlandığında davranışı `x:Class` derle'i değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bca21-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="bca21-104">Buna dayalı kısmi bir sınıf `x:Class`oluşturmak yerine, sağlanan `x:Class` bir ara sınıf olarak oluşturulur ve daha sonra `x:Class`sağlanan türemiş sınıfın temel alınması beklenir.</span><span class="sxs-lookup"><span data-stu-id="bca21-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="bca21-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="bca21-105">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="bca21-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="bca21-106">XAML Values</span></span>

|||
|-|-|
|`namespace`|<span data-ttu-id="bca21-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bca21-107">Optional.</span></span> <span data-ttu-id="bca21-108">Bir CLR ad alanı içerir. `classname`</span><span class="sxs-lookup"><span data-stu-id="bca21-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="bca21-109">`namespace` Belirtilirse, nokta (.) ayrılır `namespace` `classname`ve .</span><span class="sxs-lookup"><span data-stu-id="bca21-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|
|`classname`|<span data-ttu-id="bca21-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bca21-110">Required.</span></span> <span data-ttu-id="bca21-111">Yüklenen XAML'yi ve bu XAML için kod arkanızı bağlayan kısmi sınıfın CLR adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bca21-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="bca21-112">Bkz. Açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="bca21-112">See Remarks.</span></span>|
|`subclassNamespace`|<span data-ttu-id="bca21-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bca21-113">Optional.</span></span> <span data-ttu-id="bca21-114">Her ad `namespace` alanı diğerini çözebilirse farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="bca21-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="bca21-115">Bir CLR ad alanı içerir. `subclassName`</span><span class="sxs-lookup"><span data-stu-id="bca21-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="bca21-116">`subclassName` Belirtilirse, nokta (.) ayrılır `subclassNamespace` `subclassName`ve .</span><span class="sxs-lookup"><span data-stu-id="bca21-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|
|`subclassName`|<span data-ttu-id="bca21-117">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bca21-117">Required.</span></span> <span data-ttu-id="bca21-118">Alt sınıfın CLR adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bca21-118">Specifies the CLR name of the subclass.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="bca21-119">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="bca21-119">Dependencies</span></span>

<span data-ttu-id="bca21-120">[x:Sınıf Yönergesi](xclass-directive.md) de aynı nesne üzerinde sağlanmalıdır ve bu nesne XAML üretiminin kök öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bca21-120">[x:Class Directive](xclass-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>

## <a name="remarks"></a><span data-ttu-id="bca21-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bca21-121">Remarks</span></span>

<span data-ttu-id="bca21-122">`x:Subclass`kullanımı öncelikle kısmi sınıf bildirimlerini desteklemeyen diller için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bca21-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>

<span data-ttu-id="bca21-123">İç içe sınıf `x:Subclass` olarak kullanılan sınıf, `x:Subclass` "Bağımlılıklar" bölümünde açıklandığı gibi kök nesneye başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bca21-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>

<span data-ttu-id="bca21-124">Aksi takdirde, kavramsal `x:Subclass` anlamı .NET XAML Hizmetleri uygulaması ile tanımlanmaz.</span><span class="sxs-lookup"><span data-stu-id="bca21-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET XAML Services implementation.</span></span> <span data-ttu-id="bca21-125">Bunun nedeni, .NET XAML Hizmetleri davranışının XAML biçimlendirme ve destek kodunun bağlı olduğu genel programlama modelini belirtmesidir.</span><span class="sxs-lookup"><span data-stu-id="bca21-125">This is because .NET XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="bca21-126">XAML `x:Class` biçimlendirmesi, derlenmiş biçimlendirme ve CLR tabanlı kod arkası bağlamayı tanımlamak için programlama modellerini veya uygulama modellerini kullanan belirli çerçevelerle ilgili ve `x:Subclass` diğer kavramların uygulamaları gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bca21-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="bca21-127">Her çerçevenin, bazı davranışları veya yapı ortamına dahil edilmesi gereken belirli bileşenleri etkinleştiren kendi yapı eylemleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="bca21-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="bca21-128">Bir çerçeve içinde, yapı eylemleri de kod arkası için kullanılan belirli CLR dile bağlı olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="bca21-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="bca21-129">WPF Kullanım Notları</span><span class="sxs-lookup"><span data-stu-id="bca21-129">WPF Usage Notes</span></span>

<span data-ttu-id="bca21-130">`x:Subclass`bir sayfa kökünde veya <xref:System.Windows.Application> zaten var `x:Class`uygulama tanımında kök üzerinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="bca21-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="bca21-131">Bir `x:Subclass` sayfa veya uygulama kökü dışındaki herhangi bir öğeüzerinde `x:Class` bildirimde bulunmak veya varsa belirtme, derleme zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="bca21-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>

<span data-ttu-id="bca21-132">`x:Subclass` Senaryo için doğru çalışan türemiş sınıflar oluşturmak oldukça karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="bca21-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="bca21-133">Ara dosyaları (.xaml dosya adlarını içeren adlarla birlikte biçimlendirme derlemesi ile projenizin obj klasöründe üretilen .g dosyalarını) incelemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="bca21-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="bca21-134">Bu ara dosyalar, derlenen uygulamada birleştirilmiş kısmi sınıflardaki belirli programlama yapılarının kaynağını belirlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="bca21-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>

<span data-ttu-id="bca21-135">Türemiş sınıftaki olay işleyicileri, derleme sırasında ara sınıfta oluşturulan işleyicilerin saplamalarını geçersiz kılmak için (Microsoft `internal override` `Friend Overrides` Visual Basic'te) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bca21-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="bca21-136">Aksi takdirde, türemiş sınıf uygulamaları ara sınıf uygulamasını gizle (gölge) ve ara sınıf işleyicileri çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="bca21-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>

<span data-ttu-id="bca21-137">Her ikisini `x:Class` ve `x:Subclass`, tarafından başvurulan sınıf için herhangi bir uygulama `x:Class`sağlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bca21-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="bca21-138">Derleyicinin ara dosyalarda oluşturduğu `x:Class` sınıf için bazı yönergelere sahip olması için öznitelik üzerinden bir ad vermeniz gerekir (derleyici bu durumda varsayılan bir ad seçmez).</span><span class="sxs-lookup"><span data-stu-id="bca21-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="bca21-139">Sınıfa `x:Class` bir uygulama verebilirsiniz; ancak, bu hem `x:Class` ve `x:Subclass`kullanmak için tipik bir senaryo değildir.</span><span class="sxs-lookup"><span data-stu-id="bca21-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>

## <a name="see-also"></a><span data-ttu-id="bca21-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bca21-140">See also</span></span>

- [<span data-ttu-id="bca21-141">x:Class Yönergesi</span><span class="sxs-lookup"><span data-stu-id="bca21-141">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="bca21-142">WPF için XAML ve Özel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="bca21-142">XAML and Custom Classes for WPF</span></span>](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
