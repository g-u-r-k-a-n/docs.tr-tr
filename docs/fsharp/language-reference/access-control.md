---
title: Erişim Denetimi
description: F# Programlama dilindeki türler, Yöntemler ve işlevler gibi programlama öğelerine erişimi nasıl denetleyeceğinizi öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: fe204a883a440794fdd033c54d6d8d4fb68e0ce2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425107"
---
# <a name="access-control"></a><span data-ttu-id="b39c1-103">Erişim Denetimi</span><span class="sxs-lookup"><span data-stu-id="b39c1-103">Access Control</span></span>

<span data-ttu-id="b39c1-104">*Erişim denetimi* , hangi istemcilerin türler, Yöntemler ve işlevler gibi belirli program öğelerini kullanbileceği bildirimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="b39c1-105">Access Control temelleri</span><span class="sxs-lookup"><span data-stu-id="b39c1-105">Basics of Access Control</span></span>

<span data-ttu-id="b39c1-106">' F#De, erişim denetimi belirticileri `public`, `internal`ve `private`, modüller, türler, Yöntemler, değer tanımları, işlevler, Özellikler ve açık alanlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="b39c1-107">`public`, varlığa tüm çağıranlar tarafından erişilebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="b39c1-108">`internal`, varlığa yalnızca aynı derlemeden erişilebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="b39c1-109">`private`, varlığa yalnızca kapsayan tür veya modülden erişilebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

> [!NOTE]
> <span data-ttu-id="b39c1-110">`protected` erişim belirleyicisi ' de F#kullanılamaz, ancak `protected` erişimi destekleyen dillerde yazılmış türler kullanıyorsanız bu kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="b39c1-111">Bu nedenle, korumalı bir yöntemi geçersiz kılarsınız, yönteminiz yalnızca sınıf ve alt öğelerinden biri içinde erişilebilir kalır.</span><span class="sxs-lookup"><span data-stu-id="b39c1-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="b39c1-112">Genel olarak, tanımlayıcı, erişim denetimi belirticisinden sonra görünen bir `mutable` veya `inline` belirticisi dışında, varlığın adının önüne konur.</span><span class="sxs-lookup"><span data-stu-id="b39c1-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="b39c1-113">Herhangi bir erişim belirticisi kullanılmazsa, bir tür `let` bağlamaları dışında, her zaman türüne `private` olan `public`varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="b39c1-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="b39c1-114">İçindeki F# imzalar F# program öğelerine erişimi denetlemek için başka bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="b39c1-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="b39c1-115">İmza, erişim denetimi için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-115">Signatures are not required for access control.</span></span> <span data-ttu-id="b39c1-116">Daha fazla bilgi için bkz. [imzalar](signature-files.md).</span><span class="sxs-lookup"><span data-stu-id="b39c1-116">For more information, see [Signatures](signature-files.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="b39c1-117">Access Control kuralları</span><span class="sxs-lookup"><span data-stu-id="b39c1-117">Rules for Access Control</span></span>

<span data-ttu-id="b39c1-118">Erişim denetimi aşağıdaki kurallara tabidir:</span><span class="sxs-lookup"><span data-stu-id="b39c1-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="b39c1-119">Devralma bildirimleri (yani, bir sınıf için bir taban sınıf belirtmek için `inherit` kullanımı), arabirim bildirimleri (yani bir sınıfın bir arabirim uyguladığı) ve soyut üyelerin her zaman kapsayan türle aynı erişilebilirliği vardır.</span><span class="sxs-lookup"><span data-stu-id="b39c1-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="b39c1-120">Bu nedenle, bir erişim denetim belirticisi bu yapılar üzerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b39c1-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="b39c1-121">Ayrılmış bir Union içindeki bireysel durumlar için erişilebilirlik, ayrılmış birleşimin erişilebilirliğine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="b39c1-122">Diğer bir deyişle, belirli bir birleşim durumunun birleşimin kendisinden daha az erişilebilir olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="b39c1-123">Kayıt türündeki ayrı alanlar için erişilebilirlik, kaydın kendisinin erişilebilirliği tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-123">Accessibility for individual fields of a record type is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="b39c1-124">Diğer bir deyişle, belirli bir kayıt etiketi kaydın kendisinden daha az erişilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="b39c1-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="b39c1-125">Example</span></span>

<span data-ttu-id="b39c1-126">Aşağıdaki kod, erişim denetimi belirticilerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="b39c1-127">Projede iki dosya vardır `Module1.fs` ve `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="b39c1-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="b39c1-128">Her dosya örtük olarak bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="b39c1-128">Each file is implicitly a module.</span></span> <span data-ttu-id="b39c1-129">Bu nedenle, `Module1` ve `Module2`iki modül vardır.</span><span class="sxs-lookup"><span data-stu-id="b39c1-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="b39c1-130">Özel bir tür ve bir iç tür `Module1`tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b39c1-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="b39c1-131">Özel türe `Module2`erişilemez, ancak iç tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="b39c1-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="b39c1-132">Aşağıdaki kod `Module1.fs`içinde oluşturulan türlerin erişilebilirliğini sınar.</span><span class="sxs-lookup"><span data-stu-id="b39c1-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="b39c1-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b39c1-133">See also</span></span>

- [<span data-ttu-id="b39c1-134">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b39c1-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="b39c1-135">İmzalar</span><span class="sxs-lookup"><span data-stu-id="b39c1-135">Signatures</span></span>](signature-files.md)
