---
title: DLL İşlevleri için bir Sınıf Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
ms.openlocfilehash: 765d4344553a6e65b930a7bf586a41144d220fc6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123631"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="931b3-102">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="931b3-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="931b3-103">Yönetilen bir sınıfta sık kullanılan bir DLL işlevinin sarmalanması, platform işlevlerini kapsüllemek için etkili bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="931b3-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="931b3-104">Her durumda bunu yapmak zorunlu olmasa da, DLL işlevlerinin tanımlanması çok fazla ve hataya açık olabileceğinden sınıf sarmalayıcı sağlanması kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="931b3-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="931b3-105">Visual Basic veya C#' de programlıyorsanız, bir sınıf veya Visual Basic modülü içinde DLL işlevleri bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="931b3-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="931b3-106">Bir sınıf içinde, çağırmak istediğiniz her DLL işlevi için bir statik yöntem tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="931b3-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="931b3-107">Tanım, yöntem bağımsız değişkenlerinde kullanılan karakter kümesi veya çağırma kuralı gibi ek bilgileri içerebilir; Bu bilgileri atlayarak varsayılan ayarları seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="931b3-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="931b3-108">Bildirim seçeneklerinin ve varsayılan ayarlarının tüm listesi için bkz. [yönetilen kodda prototipler oluşturma](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="931b3-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="931b3-109">Sarmalanan bir kez, diğer herhangi bir sınıfta statik yöntemleri çağırmış olduğunuz sınıftaki yöntemleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="931b3-109">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="931b3-110">Platform çağırma, temel alınan içe aktarılmış işlevi otomatik olarak işler.</span><span class="sxs-lookup"><span data-stu-id="931b3-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="931b3-111">Platform çağırma için yönetilen bir sınıf tasarlarken sınıflar ve DLL işlevleri arasındaki ilişkileri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="931b3-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="931b3-112">Örneğin, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="931b3-112">For example, you can:</span></span>  
  
- <span data-ttu-id="931b3-113">Varolan bir sınıf içinde DLL işlevleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="931b3-113">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="931b3-114">Her DLL işlevi için tek bir sınıf oluşturun ve işlevleri yalıtılmış ve kolay bir şekilde bulabilir.</span><span class="sxs-lookup"><span data-stu-id="931b3-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="931b3-115">Mantıksal gruplandırmaları biçimlendirmek ve ek yükü azaltmak için bir dizi ilgili DLL işlevi için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="931b3-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="931b3-116">Sınıfı ve yöntemlerini sizin gibi adlandırın.</span><span class="sxs-lookup"><span data-stu-id="931b3-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="931b3-117">Nasıl oluşturulacağını gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="931b3-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="931b3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="931b3-118">See also</span></span>

- [<span data-ttu-id="931b3-119">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="931b3-119">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="931b3-120">DLL'lerde İşlevleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="931b3-120">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="931b3-121">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="931b3-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="931b3-122">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="931b3-122">Calling a DLL Function</span></span>](calling-a-dll-function.md)
