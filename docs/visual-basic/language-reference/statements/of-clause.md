---
description: For yan tümcesi hakkında daha fazla bilgi edinin (Visual Basic)
title: Of Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: d6002041a2fe8db5b07e12e9e396a65fde30b716
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768850"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="2792c-103">Of Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2792c-103">Of Clause (Visual Basic)</span></span>

<span data-ttu-id="2792c-104">Bir `Of` *genel* sınıf, yapı, arabirim, temsilci veya yordamda bir *tür parametresi* tanımlayan bir yan tümce tanıtır.</span><span class="sxs-lookup"><span data-stu-id="2792c-104">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="2792c-105">Genel türler hakkında bilgi için bkz. [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="2792c-105">For information on generic types, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="2792c-106">Anahtar sözcüğünü kullanma</span><span class="sxs-lookup"><span data-stu-id="2792c-106">Using the Of Keyword</span></span>  

 <span data-ttu-id="2792c-107">Aşağıdaki kod örneği, `Of` iki tür parametresi alan bir sınıfın ana hattını tanımlamak için anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="2792c-107">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="2792c-108">Parametreyi  arabirimini kısıtlar `keyType` , bu da <xref:System.IComparable> tüketen kodun uygulayan bir tür bağımsız değişkeni sağlaması gerektiği anlamına gelir <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="2792c-108">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="2792c-109">`add`Yordamın yöntemi çağırabilmesi için bu gereklidir <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2792c-109">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2792c-110">Kısıtlamalar hakkında daha fazla bilgi için bkz. [tür listesi](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="2792c-110">For more information on constraints, see [Type List](type-list.md).</span></span>  
  
```vb  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="2792c-111">Önceki sınıf tanımını tamamlarınızda, bundan çok çeşitli `dictionary` sınıflar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2792c-111">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="2792c-112">İçin sağladığınız türler, `entryType` `keyType` sınıfın ne tür bir girişi olduğunu ve her bir girdiyle ne tür bir anahtar ilişkilendiğini belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="2792c-112">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="2792c-113">Kısıtlama nedeniyle, `keyType` uygulayan bir türe sağlamanız gerekir <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="2792c-113">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="2792c-114">Aşağıdaki kod örneği, `String` girdileri tutan ve bir anahtarı her biriyle ilişkilendiren bir nesne oluşturur `Integer` .</span><span class="sxs-lookup"><span data-stu-id="2792c-114">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="2792c-115">`Integer` ' <xref:System.IComparable> i uygular ve bu nedenle üzerindeki kısıtlamayı karşılar `keyType` .</span><span class="sxs-lookup"><span data-stu-id="2792c-115">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="2792c-116">`Of`Anahtar sözcüğü şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="2792c-116">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2792c-117">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="2792c-117">Class Statement</span></span>](class-statement.md)  
  
 [<span data-ttu-id="2792c-118">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="2792c-118">Delegate Statement</span></span>](delegate-statement.md)  
  
 [<span data-ttu-id="2792c-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="2792c-119">Function Statement</span></span>](function-statement.md)  
  
 [<span data-ttu-id="2792c-120">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="2792c-120">Interface Statement</span></span>](interface-statement.md)  
  
 [<span data-ttu-id="2792c-121">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="2792c-121">Structure Statement</span></span>](structure-statement.md)  
  
 [<span data-ttu-id="2792c-122">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="2792c-122">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2792c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2792c-123">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="2792c-124">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="2792c-124">Type List</span></span>](type-list.md)
- [<span data-ttu-id="2792c-125">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="2792c-125">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="2792c-126">İçinde</span><span class="sxs-lookup"><span data-stu-id="2792c-126">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="2792c-127">Dışı</span><span class="sxs-lookup"><span data-stu-id="2792c-127">Out</span></span>](../modifiers/out-generic-modifier.md)
