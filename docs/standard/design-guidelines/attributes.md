---
title: Öznitelikler
ms.date: 10/22/2008
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: cc4752066124a0ea8081390bfb5f3791d21ec96d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821625"
---
# <a name="attributes"></a><span data-ttu-id="37329-102">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37329-102">Attributes</span></span>
<span data-ttu-id="37329-103"><xref:System.Attribute?displayProperty=nameWithType> , özel öznitelikler tanımlamak için kullanılan bir temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="37329-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>

 <span data-ttu-id="37329-104">Öznitelikler, derlemeler, türler, Üyeler ve parametreler gibi programlama öğelerine eklenebilen ek açıklamalardır.</span><span class="sxs-lookup"><span data-stu-id="37329-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="37329-105">Bunlar derlemenin meta verilerinde depolanır ve yansıma API 'Leri kullanılarak çalışma zamanında erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="37329-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="37329-106">Örneğin Framework, <xref:System.ObsoleteAttribute> türün veya üyenin kullanım dışı olduğunu göstermek için bir türe veya üyeye uygulanabilen öğesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="37329-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>

 <span data-ttu-id="37329-107">Öznitelikler, özniteliğiyle ilgili ek verileri taşıyan bir veya daha fazla özelliğe sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="37329-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="37329-108">Örneğin, `ObsoleteAttribute` bir tür veya üyenin kullanım dışı aldığı ve eski API 'yi değiştiren yeni API 'lerin açıklaması hakkında daha fazla bilgi taşıyabildi.</span><span class="sxs-lookup"><span data-stu-id="37329-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>

 <span data-ttu-id="37329-109">Özniteliği uygulandığında bir özniteliğin bazı özelliklerinin belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="37329-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="37329-110">Bunlar, konumsal Oluşturucu parametreleri olarak temsil edildiği için gereken özellikler veya gerekli bağımsız değişkenler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="37329-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="37329-111">Örneğin, <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> öğesinin özelliği <xref:System.Diagnostics.ConditionalAttribute> gerekli bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="37329-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>

 <span data-ttu-id="37329-112">Özniteliği uygulandığında belirtilmesi gereken özellikler isteğe bağlı Özellikler (veya isteğe bağlı bağımsız değişkenler) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="37329-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="37329-113">Bunlar ayarlanabilir özelliklerle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="37329-113">They are represented by settable properties.</span></span> <span data-ttu-id="37329-114">Derleyiciler, bir öznitelik uygulandığında bu özellikleri ayarlamak için özel söz dizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="37329-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="37329-115">Örneğin, <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Özellik isteğe bağlı bir bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="37329-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>

 <span data-ttu-id="37329-116">✔️ Özel öznitelik sınıflarını "Attribute" sonekiyle birlikte adlandırın.</span><span class="sxs-lookup"><span data-stu-id="37329-116">✔️ DO name custom attribute classes with the suffix "Attribute."</span></span>

 <span data-ttu-id="37329-117">✔️ <xref:System.AttributeUsageAttribute> özel özniteliklere uygulayın.</span><span class="sxs-lookup"><span data-stu-id="37329-117">✔️ DO apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>

 <span data-ttu-id="37329-118">✔️ isteğe bağlı bağımsız değişkenler için ayarlanabilir özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="37329-118">✔️ DO provide settable properties for optional arguments.</span></span>

 <span data-ttu-id="37329-119">✔️ gerekli bağımsız değişkenler için salt al özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="37329-119">✔️ DO provide get-only properties for required arguments.</span></span>

 <span data-ttu-id="37329-120">✔️ gerekli bağımsız değişkenlere karşılık gelen özellikleri başlatmak için Oluşturucu parametreleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="37329-120">✔️ DO provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="37329-121">Her parametrenin karşılık gelen özellik olarak aynı ada sahip olması gerekir (büyük/küçük harfe karşın).</span><span class="sxs-lookup"><span data-stu-id="37329-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>

 <span data-ttu-id="37329-122">❌ İsteğe bağlı bağımsız değişkenlere karşılık gelen özellikleri başlatmak için Oluşturucu parametreleri sağlamaktan KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="37329-122">❌ AVOID providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>

 <span data-ttu-id="37329-123">Diğer bir deyişle, hem Oluşturucu hem de ayarlayıcı ile ayarlanabilir özellikleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="37329-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="37329-124">Bu kılavuz, hangi bağımsız değişkenlerin isteğe bağlı ve gerekli olduğunu ve aynı şeyi yapmanın iki yolu olmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="37329-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>

 <span data-ttu-id="37329-125">❌ Özel öznitelik oluşturucularını aşırı yüklemeyi ÖNLEYIN.</span><span class="sxs-lookup"><span data-stu-id="37329-125">❌ AVOID overloading custom attribute constructors.</span></span>

 <span data-ttu-id="37329-126">Yalnızca bir oluşturucunun, bağımsız değişkenlerin gerekli olduğu ve isteğe bağlı olduğu kullanıcıya açıkça iletişim kurduğu.</span><span class="sxs-lookup"><span data-stu-id="37329-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>

 <span data-ttu-id="37329-127">Mümkünse, özel öznitelik sınıflarını mühürlemek ✔️.</span><span class="sxs-lookup"><span data-stu-id="37329-127">✔️ DO seal custom attribute classes, if possible.</span></span> <span data-ttu-id="37329-128">Bu, özniteliğe yönelik arama işlemini daha hızlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="37329-128">This makes the look-up for the attribute faster.</span></span>

 <span data-ttu-id="37329-129">*Bölüm &copy; 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="37329-129">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="37329-130">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="37329-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="37329-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37329-131">See also</span></span>

- [<span data-ttu-id="37329-132">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="37329-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="37329-133">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="37329-133">Usage Guidelines</span></span>](usage-guidelines.md)
