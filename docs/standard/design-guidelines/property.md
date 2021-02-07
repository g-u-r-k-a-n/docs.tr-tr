---
description: 'Daha fazla bilgi edinin: Özellik tasarımı'
title: Özellik Tasarımı
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: b2f776a5fb651f8b2e61b750a556704fa6c8c366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731805"
---
# <a name="property-design"></a><span data-ttu-id="1ca51-103">Özellik Tasarımı</span><span class="sxs-lookup"><span data-stu-id="1ca51-103">Property Design</span></span>

<span data-ttu-id="1ca51-104">Özellikler teknik açıdan yöntemlere çok benzer olsa da, bunlar kullanım senaryolarında oldukça farklıdır.</span><span class="sxs-lookup"><span data-stu-id="1ca51-104">Although properties are technically very similar to methods, they are quite different in terms of their usage scenarios.</span></span> <span data-ttu-id="1ca51-105">Akıllı alanlar olarak görülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-105">They should be seen as smart fields.</span></span> <span data-ttu-id="1ca51-106">Alanların çağırma söz dizimi ve yöntemlerin esnekliği vardır.</span><span class="sxs-lookup"><span data-stu-id="1ca51-106">They have the calling syntax of fields, and the flexibility of methods.</span></span>

 <span data-ttu-id="1ca51-107">çağıranın özelliğin değerini değiştirememelidir ✔️ salt-al özellikleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ca51-107">✔️ DO create get-only properties if the caller should not be able to change the value of the property.</span></span>

 <span data-ttu-id="1ca51-108">Özelliğin türü kesilebilir bir başvuru türü ise, özellik salt al olsa bile Özellik değerinin değiştirilebileceğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1ca51-108">Keep in mind that if the type of the property is a mutable reference type, the property value can be changed even if the property is get-only.</span></span>

 <span data-ttu-id="1ca51-109">❌ Ayarlayıcının, alıcı tarafından daha geniş erişilebilirliği olan salt ayarlı özelliklerini veya özelliklerini sağlamaktan.</span><span class="sxs-lookup"><span data-stu-id="1ca51-109">❌ DO NOT provide set-only properties or properties with the setter having broader accessibility than the getter.</span></span>

 <span data-ttu-id="1ca51-110">Örneğin, özellikleri ortak bir ayarlayıcı ve korumalı bir alıcı ile birlikte kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="1ca51-110">For example, do not use properties with a public setter and a protected getter.</span></span>

 <span data-ttu-id="1ca51-111">Özellik alıcısı sağlanmadıysa, işlevi bir yöntem olarak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1ca51-111">If the property getter cannot be provided, implement the functionality as a method instead.</span></span> <span data-ttu-id="1ca51-112">Yöntem adını ile başlatmayı `Set` ve özelliği adlandırdıklarınız ile birlikte izlemenizi düşünün.</span><span class="sxs-lookup"><span data-stu-id="1ca51-112">Consider starting the method name with `Set` and follow with what you would have named the property.</span></span> <span data-ttu-id="1ca51-113">Örneğin, <xref:System.AppDomain> `SetCachePath` yalnızca set-Only özelliği olmak yerine çağrılan bir yöntemi vardır `CachePath` .</span><span class="sxs-lookup"><span data-stu-id="1ca51-113">For example, <xref:System.AppDomain> has a method called `SetCachePath` instead of having a set-only property called `CachePath`.</span></span>

 <span data-ttu-id="1ca51-114">✔️ Tüm özellikler için, varsayılan değerlerin bir güvenlik deliğe veya daha fazla verimsiz bir koda neden olmamasını sağlamak için, tüm özellikler için hazır varsayılan değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ca51-114">✔️ DO provide sensible default values for all properties, ensuring that the defaults do not result in a security hole or terribly inefficient code.</span></span>

 <span data-ttu-id="1ca51-115">✔️, nesnenin geçici olarak geçersiz bir durumuna neden olsa da, özelliklerin herhangi bir sırada ayarlanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-115">✔️ DO allow properties to be set in any order even if this results in a temporary invalid state of the object.</span></span>

 <span data-ttu-id="1ca51-116">İki veya daha fazla özelliğin, bir özelliğin bazı değerlerinin aynı nesne üzerindeki diğer özelliklerin değerleri verildiğinde geçersiz olabileceği bir nokta ile ilişkili olması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="1ca51-116">It is common for two or more properties to be interrelated to a point where some values of one property might be invalid given the values of other properties on the same object.</span></span> <span data-ttu-id="1ca51-117">Bu gibi durumlarda, ilişkili özellikler gerçekten nesne tarafından birlikte kullanıldığından, geçersiz durumdan kaynaklanan özel durumlar ertelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-117">In such cases, exceptions resulting from the invalid state should be postponed until the interrelated properties are actually used together by the object.</span></span>

 <span data-ttu-id="1ca51-118">bir özellik ayarlayıcısı özel durum oluşturursa, önceki değeri koruma ✔️.</span><span class="sxs-lookup"><span data-stu-id="1ca51-118">✔️ DO preserve the previous value if a property setter throws an exception.</span></span>

 <span data-ttu-id="1ca51-119">❌ Getters Özellikler 'den özel durumlar oluşturmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="1ca51-119">❌ AVOID throwing exceptions from property getters.</span></span>

 <span data-ttu-id="1ca51-120">Özellik alıcıları basit işlemler olmalıdır ve herhangi bir önkoşullara sahip olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ca51-120">Property getters should be simple operations and should not have any preconditions.</span></span> <span data-ttu-id="1ca51-121">Alıcı bir özel durum oluştur, büyük olasılıkla bir yöntem olarak yeniden tasarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-121">If a getter can throw an exception, it should probably be redesigned to be a method.</span></span> <span data-ttu-id="1ca51-122">Bu kuralın, bağımsız değişkenlerin doğrulanması sonucunda özel durumlar beklediğimiz Dizin oluşturucular için uygulanmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="1ca51-122">Notice that this rule does not apply to indexers, where we do expect exceptions as a result of validating the arguments.</span></span>

### <a name="indexed-property-design"></a><span data-ttu-id="1ca51-123">Dizinli özellik tasarımı</span><span class="sxs-lookup"><span data-stu-id="1ca51-123">Indexed Property Design</span></span>

 <span data-ttu-id="1ca51-124">Dizinli bir özellik, parametrelere sahip olabilecek ve dizi dizine benzer özel söz dizimi ile çağrılabilen özel bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-124">An indexed property is a special property that can have parameters and can be called with special syntax similar to array indexing.</span></span>

 <span data-ttu-id="1ca51-125">Dizinli özellikler genellikle Dizin oluşturucular olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1ca51-125">Indexed properties are commonly referred to as indexers.</span></span> <span data-ttu-id="1ca51-126">Dizin oluşturucular yalnızca bir mantıksal koleksiyondaki öğelere erişim sağlayan API 'lerde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ca51-126">Indexers should be used only in APIs that provide access to items in a logical collection.</span></span> <span data-ttu-id="1ca51-127">Örneğin, bir dize bir karakter koleksiyonudur ve üzerindeki Dizin Oluşturucu, <xref:System.String?displayProperty=nameWithType> kendi karakterlerine erişmek için eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-127">For example, a string is a collection of characters, and the indexer on <xref:System.String?displayProperty=nameWithType> was added to access its characters.</span></span>

 <span data-ttu-id="1ca51-128">✔️, iç dizide depolanan verilere erişim sağlamak için Dizin oluşturucular kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="1ca51-128">✔️ CONSIDER using indexers to provide access to data stored in an internal array.</span></span>

 <span data-ttu-id="1ca51-129">✔️ öğe koleksiyonlarını temsil eden türlerde Dizin oluşturucular sağlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="1ca51-129">✔️ CONSIDER providing indexers on types representing collections of items.</span></span>

 <span data-ttu-id="1ca51-130">❌ Birden fazla parametreli dizinli Özellikler kullanmaktan KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="1ca51-130">❌ AVOID using indexed properties with more than one parameter.</span></span>

 <span data-ttu-id="1ca51-131">Tasarım birden çok parametre gerektiriyorsa, özelliğin bir mantıksal koleksiyona bir erişimciyi temsil edip etmediğini yeniden düşünün.</span><span class="sxs-lookup"><span data-stu-id="1ca51-131">If the design requires multiple parameters, reconsider whether the property really represents an accessor to a logical collection.</span></span> <span data-ttu-id="1ca51-132">Yoksa, bunun yerine yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ca51-132">If it does not, use methods instead.</span></span> <span data-ttu-id="1ca51-133">Veya ile yöntem adını başlatmayı düşünün `Get` `Set` .</span><span class="sxs-lookup"><span data-stu-id="1ca51-133">Consider starting the method name with `Get` or `Set`.</span></span>

 <span data-ttu-id="1ca51-134">❌ ,,, <xref:System.Int32?displayProperty=nameWithType> <xref:System.Int64?displayProperty=nameWithType> <xref:System.String?displayProperty=nameWithType> Veya enum dışında parametre türlerine sahip dizin oluşturuculardan kaçının <xref:System.Object?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1ca51-134">❌ AVOID indexers with parameter types other than <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, or an enum.</span></span>

 <span data-ttu-id="1ca51-135">Tasarımda diğer parametre türleri gerekiyorsa, API 'nin mantıksal bir koleksiyona bir erişimciyi temsil edip etmediğini kesin olarak yeniden değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="1ca51-135">If the design requires other types of parameters, strongly reevaluate whether the API really represents an accessor to a logical collection.</span></span> <span data-ttu-id="1ca51-136">Değilse, bir yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ca51-136">If it does not, use a method.</span></span> <span data-ttu-id="1ca51-137">Veya ile yöntem adını başlatmayı düşünün `Get` `Set` .</span><span class="sxs-lookup"><span data-stu-id="1ca51-137">Consider starting the method name with `Get` or `Set`.</span></span>

 <span data-ttu-id="1ca51-138">✔️, `Item` açıkça daha iyi bir ad olmadıkça, dizinli özellikler için adı kullanın (ör., <xref:System.String.Chars%2A> özelliği üzerinde bkz. `System.String` ).</span><span class="sxs-lookup"><span data-stu-id="1ca51-138">✔️ DO use the name `Item` for indexed properties unless there is an obviously better name (e.g., see the <xref:System.String.Chars%2A> property on `System.String`).</span></span>

 <span data-ttu-id="1ca51-139">C# ' de, Dizin oluşturucular varsayılan olarak adlandırılmış öğedir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-139">In C#, indexers are by default named Item.</span></span> <span data-ttu-id="1ca51-140"><xref:System.Runtime.CompilerServices.IndexerNameAttribute>Bu adı özelleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-140">The <xref:System.Runtime.CompilerServices.IndexerNameAttribute> can be used to customize this name.</span></span>

 <span data-ttu-id="1ca51-141">❌ Hem bir Dizin Oluşturucu hem de anlamsal olarak eşdeğer Yöntemler sağlamaın.</span><span class="sxs-lookup"><span data-stu-id="1ca51-141">❌ DO NOT provide both an indexer and methods that are semantically equivalent.</span></span>

 <span data-ttu-id="1ca51-142">❌ Bir tür içinde birden fazla aşırı yüklenmiş Dizin Oluşturucu sağlamaktan biridir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-142">❌ DO NOT provide more than one family of overloaded indexers in one type.</span></span>

 <span data-ttu-id="1ca51-143">Bu, C# derleyicisi tarafından zorlanır.</span><span class="sxs-lookup"><span data-stu-id="1ca51-143">This is enforced by the C# compiler.</span></span>

 <span data-ttu-id="1ca51-144">❌ Varsayılan olmayan dizinli özellikleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="1ca51-144">❌ DO NOT use nondefault indexed properties.</span></span>

 <span data-ttu-id="1ca51-145">Bu, C# derleyicisi tarafından zorlanır.</span><span class="sxs-lookup"><span data-stu-id="1ca51-145">This is enforced by the C# compiler.</span></span>

### <a name="property-change-notification-events"></a><span data-ttu-id="1ca51-146">Özellik değişiklik bildirimi olayları</span><span class="sxs-lookup"><span data-stu-id="1ca51-146">Property Change Notification Events</span></span>

 <span data-ttu-id="1ca51-147">Bazen bir özellik değerindeki değişiklikleri kullanıcıya bildiren bir olay sağlamak yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="1ca51-147">Sometimes it is useful to provide an event notifying the user of changes in a property value.</span></span> <span data-ttu-id="1ca51-148">Örneğin, `System.Windows.Forms.Control` `TextChanged` özelliğinin değeri değiştirildikten sonra bir olay oluşturur `Text` .</span><span class="sxs-lookup"><span data-stu-id="1ca51-148">For example, `System.Windows.Forms.Control` raises a `TextChanged` event after the value of its `Text` property has changed.</span></span>

 <span data-ttu-id="1ca51-149">✔️, üst düzey API 'lerde (genellikle Tasarımcı bileşenleri) özellik değerleri değiştirildiğinde değişiklik bildirimi olaylarını yükseltmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1ca51-149">✔️ CONSIDER raising change notification events when property values in high-level APIs (usually designer components) are modified.</span></span>

 <span data-ttu-id="1ca51-150">Bir kullanıcının bir nesnenin özelliğinin ne zaman değiştiğini bilmesini sağlamak için iyi bir senaryo varsa, nesne özellik için bir değişiklik bildirimi olayı tetiklemelidir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-150">If there is a good scenario for a user to know when a property of an object is changing, the object should raise a change notification event for the property.</span></span>

 <span data-ttu-id="1ca51-151">Bununla birlikte, temel türler veya Koleksiyonlar gibi alt düzey API 'Ler için bu tür olayları yükseltme yüküyle ilgili ek yükün olması düşüktür.</span><span class="sxs-lookup"><span data-stu-id="1ca51-151">However, it is unlikely to be worth the overhead to raise such events for low-level APIs such as base types or collections.</span></span> <span data-ttu-id="1ca51-152">Örneğin, <xref:System.Collections.Generic.List%601> listeye yeni bir öğe eklendiğinde ve özelliği değiştiğinde bu tür olayları oluşturmaz `Count` .</span><span class="sxs-lookup"><span data-stu-id="1ca51-152">For example, <xref:System.Collections.Generic.List%601> would not raise such events when a new item is added to the list and the `Count` property changes.</span></span>

 <span data-ttu-id="1ca51-153">✔️, bir özelliğin değeri dış güçlerle değiştirildiğinde değişiklik bildirimi olaylarını yükseltmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1ca51-153">✔️ CONSIDER raising change notification events when the value of a property changes via external forces.</span></span>

 <span data-ttu-id="1ca51-154">Bir özellik değeri, bazı dış zorlanarak (nesne üzerinde Yöntemler çağırma dışında bir şekilde) değişirse, olay oluşturma, geliştiricinin değerin değiştiğini ve değiştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-154">If a property value changes via some external force (in a way other than by calling methods on the object), raise events indicate to the developer that the value is changing and has changed.</span></span> <span data-ttu-id="1ca51-155">`Text`Bir metin kutusu denetiminin özelliği iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-155">A good example is the `Text` property of a text box control.</span></span> <span data-ttu-id="1ca51-156">Kullanıcı öğesine metin yazdığında `TextBox` , özellik değeri otomatik olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="1ca51-156">When the user types text in a `TextBox`, the property value automatically changes.</span></span>

 <span data-ttu-id="1ca51-157">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="1ca51-157">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1ca51-158">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="1ca51-158">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1ca51-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ca51-159">See also</span></span>

- [<span data-ttu-id="1ca51-160">Üye tasarımı yönergeleri</span><span class="sxs-lookup"><span data-stu-id="1ca51-160">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="1ca51-161">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="1ca51-161">Framework Design Guidelines</span></span>](index.md)
