---
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
ms.openlocfilehash: 8497f46453d586fb94e1f7c82c81c6b923dd6f60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404427"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="5c5e6-102">Of Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c5e6-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="5c5e6-103">Bir `Of` *genel* sınıf, yapı, arabirim, temsilci veya yordamda bir *tür parametresi* tanımlayan bir yan tümce tanıtır.</span><span class="sxs-lookup"><span data-stu-id="5c5e6-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="5c5e6-104">Genel türler hakkında bilgi için bkz. [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="5c5e6-104">For information on generic types, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="5c5e6-105">Anahtar sözcüğünü kullanma</span><span class="sxs-lookup"><span data-stu-id="5c5e6-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="5c5e6-106">Aşağıdaki kod örneği, `Of` iki tür parametresi alan bir sınıfın ana hattını tanımlamak için anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="5c5e6-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="5c5e6-107">Parametreyi *constrains* arabirimini kısıtlar `keyType` , bu da <xref:System.IComparable> tüketen kodun uygulayan bir tür bağımsız değişkeni sağlaması gerektiği anlamına gelir <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="5c5e6-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="5c5e6-108">`add`Yordamın yöntemi çağırabilmesi için bu gereklidir <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5c5e6-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5c5e6-109">Kısıtlamalar hakkında daha fazla bilgi için bkz. [tür listesi](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="5c5e6-109">For more information on constraints, see [Type List](type-list.md).</span></span>  
  
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
  
 <span data-ttu-id="5c5e6-110">Önceki sınıf tanımını tamamlarınızda, bundan çok çeşitli `dictionary` sınıflar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c5e6-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="5c5e6-111">İçin sağladığınız türler, `entryType` `keyType` sınıfın ne tür bir girişi olduğunu ve her bir girdiyle ne tür bir anahtar ilişkilendiğini belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="5c5e6-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="5c5e6-112">Kısıtlama nedeniyle, `keyType` uygulayan bir türe sağlamanız gerekir <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="5c5e6-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="5c5e6-113">Aşağıdaki kod örneği, `String` girdileri tutan ve bir anahtarı her biriyle ilişkilendiren bir nesne oluşturur `Integer` .</span><span class="sxs-lookup"><span data-stu-id="5c5e6-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="5c5e6-114">`Integer`' <xref:System.IComparable> i uygular ve bu nedenle üzerindeki kısıtlamayı karşılar `keyType` .</span><span class="sxs-lookup"><span data-stu-id="5c5e6-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="5c5e6-115">`Of`Anahtar sözcüğü şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="5c5e6-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="5c5e6-116">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="5c5e6-116">Class Statement</span></span>](class-statement.md)  
  
 [<span data-ttu-id="5c5e6-117">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="5c5e6-117">Delegate Statement</span></span>](delegate-statement.md)  
  
 [<span data-ttu-id="5c5e6-118">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="5c5e6-118">Function Statement</span></span>](function-statement.md)  
  
 [<span data-ttu-id="5c5e6-119">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="5c5e6-119">Interface Statement</span></span>](interface-statement.md)  
  
 [<span data-ttu-id="5c5e6-120">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="5c5e6-120">Structure Statement</span></span>](structure-statement.md)  
  
 [<span data-ttu-id="5c5e6-121">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="5c5e6-121">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5c5e6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c5e6-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="5c5e6-123">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="5c5e6-123">Type List</span></span>](type-list.md)
- [<span data-ttu-id="5c5e6-124">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="5c5e6-124">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="5c5e6-125">İçinde</span><span class="sxs-lookup"><span data-stu-id="5c5e6-125">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="5c5e6-126">Dışı</span><span class="sxs-lookup"><span data-stu-id="5c5e6-126">Out</span></span>](../modifiers/out-generic-modifier.md)
