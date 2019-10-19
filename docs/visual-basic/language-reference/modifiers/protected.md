---
title: Korumalı (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 8370d15e99a6f7ed0868441a4e44360fb258be13
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583064"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="8fce4-102">Korumalı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fce4-102">Protected (Visual Basic)</span></span>

<span data-ttu-id="8fce4-103">Bir veya daha fazla tanımlanmış programlama öğesinin yalnızca kendi sınıfının içinden veya türetilmiş bir sınıftan erişilebilir olduğunu belirten bir üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="8fce4-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>

## <a name="remarks"></a><span data-ttu-id="8fce4-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fce4-104">Remarks</span></span>

<span data-ttu-id="8fce4-105">Bazen bir sınıfta tanımlanan programlama öğesi hassas veriler veya kısıtlı kod içeriyorsa ve öğeye erişimi sınırlandırmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="8fce4-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="8fce4-106">Ancak, sınıf devralınabilir ise ve türetilmiş sınıfların hiyerarşisini düşünüyorsanız, bu türetilmiş sınıfların verilere veya koda erişmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="8fce4-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="8fce4-107">Böyle bir durumda, öğesinin hem taban sınıftan hem de tüm türetilmiş sınıflardan erişilebilir olmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="8fce4-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="8fce4-108">Bu şekilde bir öğeye erişimi sınırlandırmak için, `Protected` ile bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fce4-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>

> [!NOTE]
> <span data-ttu-id="8fce4-109">@No__t_0 erişim değiştiricisi iki farklı değiştiriciyle birleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="8fce4-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
>
> - <span data-ttu-id="8fce4-110">[Protected Friend](protected-friend.md) değiştiricisi, bir sınıf üyesini türetilmiş sınıflardan ve sınıfın tanımlandığı aynı derlemeden erişilebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="8fce4-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span>
> - <span data-ttu-id="8fce4-111">[Özel korumalı](private-protected.md) değiştirici, bir sınıf üyesini türetilmiş türler tarafından erişilebilir hale getirir, ancak yalnızca kendi kapsayıcı bütünleştirilmiş kodu içinde.</span><span class="sxs-lookup"><span data-stu-id="8fce4-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="8fce4-112">Kurallar</span><span class="sxs-lookup"><span data-stu-id="8fce4-112">Rules</span></span>

<span data-ttu-id="8fce4-113">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="8fce4-113">**Declaration Context.**</span></span> <span data-ttu-id="8fce4-114">@No__t_0 yalnızca sınıf düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fce4-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="8fce4-115">Yani, bir `Protected` öğesi için bildirim bağlamı bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="8fce4-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="8fce4-116">Davranış</span><span class="sxs-lookup"><span data-stu-id="8fce4-116">Behavior</span></span>

- <span data-ttu-id="8fce4-117">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="8fce4-117">**Access Level.**</span></span> <span data-ttu-id="8fce4-118">Bir sınıftaki tüm kod öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="8fce4-118">All code in a class can access its elements.</span></span> <span data-ttu-id="8fce4-119">Bir taban sınıftan türetilen herhangi bir sınıftaki kod, temel sınıfın tüm `Protected` öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="8fce4-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="8fce4-120">Bu, tüm türetme oluşumlarında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8fce4-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="8fce4-121">Bu, bir sınıfın temel sınıfın temel sınıfının `Protected` öğelerine erişebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8fce4-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>

     <span data-ttu-id="8fce4-122">Korumalı erişim arkadaş erişiminin bir üst kümesi veya alt kümesi değil.</span><span class="sxs-lookup"><span data-stu-id="8fce4-122">Protected access is not a superset or subset of friend access.</span></span>

- <span data-ttu-id="8fce4-123">**Erişim değiştiricileri.**</span><span class="sxs-lookup"><span data-stu-id="8fce4-123">**Access Modifiers.**</span></span> <span data-ttu-id="8fce4-124">Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir.</span><span class="sxs-lookup"><span data-stu-id="8fce4-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="8fce4-125">Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8fce4-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="8fce4-126">@No__t_0 değiştiricisi şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="8fce4-126">The `Protected` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="8fce4-127">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fce4-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

- [<span data-ttu-id="8fce4-128">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fce4-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="8fce4-129">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fce4-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="8fce4-130">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fce4-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [<span data-ttu-id="8fce4-131">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fce4-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- [<span data-ttu-id="8fce4-132">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fce4-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)

- [<span data-ttu-id="8fce4-133">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fce4-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="8fce4-134">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fce4-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="8fce4-135">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fce4-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)

- [<span data-ttu-id="8fce4-136">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fce4-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="8fce4-137">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fce4-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

- [<span data-ttu-id="8fce4-138">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="8fce4-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="8fce4-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fce4-139">See also</span></span>

- [<span data-ttu-id="8fce4-140">Public</span><span class="sxs-lookup"><span data-stu-id="8fce4-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="8fce4-141">Friend</span><span class="sxs-lookup"><span data-stu-id="8fce4-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="8fce4-142">Private</span><span class="sxs-lookup"><span data-stu-id="8fce4-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="8fce4-143">Private Protected</span><span class="sxs-lookup"><span data-stu-id="8fce4-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="8fce4-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="8fce4-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="8fce4-145">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="8fce4-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="8fce4-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8fce4-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="8fce4-147">Yapılar</span><span class="sxs-lookup"><span data-stu-id="8fce4-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="8fce4-148">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="8fce4-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
