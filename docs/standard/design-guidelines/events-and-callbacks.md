---
title: Etkinlikler ve Geri Aramalar
ms.date: 10/22/2008
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: c63a88cb4e500504f993352a03478f40cad58400
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734743"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="031b4-102">Etkinlikler ve Geri Aramalar</span><span class="sxs-lookup"><span data-stu-id="031b4-102">Events and Callbacks</span></span>

<span data-ttu-id="031b4-103">Geri çağrılar, bir çerçevenin bir temsilci aracılığıyla Kullanıcı koduna geri çağırmasını sağlayan genişletilebilirlik noktalarıdır.</span><span class="sxs-lookup"><span data-stu-id="031b4-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="031b4-104">Bu temsilciler genellikle bir yöntemin parametresi aracılığıyla çerçeveye geçirilir.</span><span class="sxs-lookup"><span data-stu-id="031b4-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>

 <span data-ttu-id="031b4-105">Olaylar, temsilciyi (bir olay işleyicisi) sağlamak için uygun ve tutarlı sözdizimini destekleyen, geri çağırmaların özel bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="031b4-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="031b4-106">Ayrıca, Visual Studio 'nun bildirim tamamlama ve tasarımcıları, olay tabanlı API 'Leri kullanma konusunda yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="031b4-106">In addition, Visual Studio's statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="031b4-107">(Bkz. [olay tasarımı](event.md).)</span><span class="sxs-lookup"><span data-stu-id="031b4-107">(See [Event Design](event.md).)</span></span>

 <span data-ttu-id="031b4-108">✔️, kullanıcıların çerçeve tarafından yürütülmesi için özel kod sağlamasına izin vermek için geri çağırmaları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="031b4-108">✔️ CONSIDER using callbacks to allow users to provide custom code to be executed by the framework.</span></span>

 <span data-ttu-id="031b4-109">✔️, kullanıcıların, nesne odaklı tasarımı anlamak zorunda kalmadan bir Framework davranışını özelleştirmesini sağlamak için olayları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="031b4-109">✔️ CONSIDER using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>

 <span data-ttu-id="031b4-110">✔️, daha geniş bir geliştirici yelpazdakilere daha tanıdık ve Visual Studio deyimin tamamlanmasına tümleştirildiği için düz geri çağırmalar üzerinde olayları tercih etme.</span><span class="sxs-lookup"><span data-stu-id="031b4-110">✔️ DO prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>

 <span data-ttu-id="031b4-111">❌ Performans duyarlı API 'lerde geri çağırmaları kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="031b4-111">❌ AVOID using callbacks in performance-sensitive APIs.</span></span>

 <span data-ttu-id="031b4-112">✔️, `Func<...>` `Action<...>` `Expression<...>` geri çağırmalar ile API 'leri tanımlarken özel temsilciler yerine yeni, veya türlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="031b4-112">✔️ DO use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>

 <span data-ttu-id="031b4-113">`Func<...>` ve `Action<...>` genel temsilcileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="031b4-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="031b4-114">`Expression<...>` derlenebilecek ve sonra çalışma zamanında çağrılabilen ancak aynı zamanda seri hale getirilebilir ve uzak işlemlere geçirilebilecek işlev tanımlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="031b4-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>

 <span data-ttu-id="031b4-115">✔️ `Expression<...>` , ve temsilcileri yerine kullanmanın performans etkilerine ilişkin etkilerini anlayın `Func<...>` `Action<...>` .</span><span class="sxs-lookup"><span data-stu-id="031b4-115">✔️ DO measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>

 <span data-ttu-id="031b4-116">`Expression<...>` türler çoğu durumda mantıksal olarak eşit `Func<...>` ve `Action<...>` Temsilcilerde bulunur.</span><span class="sxs-lookup"><span data-stu-id="031b4-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="031b4-117">Aralarındaki temel fark, temsilcilerin yerel işlem senaryolarında kullanılması amaçlanmasıdır; ifadeler, uzak bir işlem veya makinedeki ifadeyi değerlendirmek yararlı ve mümkün olduğu durumlar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="031b4-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it's beneficial and possible to evaluate the expression in a remote process or machine.</span></span>

 <span data-ttu-id="031b4-118">✔️, bir temsilciyi çağırarak, rastgele kod yürüttüğünü ve güvenlik, doğruluk ve uyumluluk repercusumu olduğunu anlamış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="031b4-118">✔️ DO understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>

 <span data-ttu-id="031b4-119">*Bölüm &copy; 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="031b4-119">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="031b4-120">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="031b4-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="031b4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="031b4-121">See also</span></span>

- [<span data-ttu-id="031b4-122">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="031b4-122">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="031b4-123">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="031b4-123">Framework Design Guidelines</span></span>](index.md)
