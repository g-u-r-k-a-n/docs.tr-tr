---
description: 'Daha fazla bilgi edinin: MustInherit (Visual Basic)'
title: MustInherit
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 6ca11dd3fee8240f39ea1a3d278870d167d283d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701046"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="ae33f-103">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae33f-103">MustInherit (Visual Basic)</span></span>

<span data-ttu-id="ae33f-104">Bir sınıfın sadece temel sınıf olarak kullanılabileceğini ve doğrudan bundan bir nesne oluşturkullanılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae33f-104">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae33f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae33f-105">Remarks</span></span>  

 <span data-ttu-id="ae33f-106">*Temel sınıfın* amacı ( *soyut sınıf* olarak da bilinir), bundan türetilmiş tüm sınıflar için ortak olan işlevleri tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="ae33f-106">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="ae33f-107">Bu, türetilmiş sınıfları ortak öğeleri yeniden tanımlamak zorunda kalmadan kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ae33f-107">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="ae33f-108">Bazı durumlarda, bu ortak işlevsellik kullanılabilir bir nesne oluşturmak için yeterli değildir ve her türetilmiş sınıf eksik işlevselliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae33f-108">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="ae33f-109">Böyle bir durumda, tüketen kodun yalnızca türetilmiş sınıflardan nesneler oluşturmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="ae33f-109">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="ae33f-110">`MustInherit`Bunu zorlamak için temel sınıfta kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae33f-110">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="ae33f-111">Bir sınıfının başka bir kullanımı `MustInherit` , bir değişkeni ilgili sınıflar kümesiyle kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="ae33f-111">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="ae33f-112">Bir temel sınıf tanımlayabilir ve bu ilgili sınıfları bundan türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae33f-112">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="ae33f-113">Temel sınıfın tüm türetilmiş sınıflarda ortak bir işlev sağlaması gerekmez, ancak değişkenlere değer atamak için bir filtre işlevi görebilir.</span><span class="sxs-lookup"><span data-stu-id="ae33f-113">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="ae33f-114">Tüketim kodunuz temel sınıf olarak bir değişken bildirirse Visual Basic, yalnızca türetilmiş sınıflardan birindeki bir nesneyi bu değişkene atamanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="ae33f-114">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="ae33f-115">.NET Framework, `MustInherit` ve arasında birkaç sınıfı tanımlar <xref:System.Array> <xref:System.Enum> <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="ae33f-115">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="ae33f-116"><xref:System.ValueType> , bir değişkeni kısıtlayan temel sınıfa bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="ae33f-116"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="ae33f-117">Tüm değer türleri öğesinden türetilir <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="ae33f-117">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="ae33f-118">Bir değişkeni olarak bildirirseniz <xref:System.ValueType> , bu değişkene yalnızca değer türlerini atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae33f-118">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ae33f-119">Kurallar</span><span class="sxs-lookup"><span data-stu-id="ae33f-119">Rules</span></span>  
  
- <span data-ttu-id="ae33f-120">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="ae33f-120">**Declaration Context.**</span></span> <span data-ttu-id="ae33f-121">`MustInherit`Yalnızca bir `Class` ifadede kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae33f-121">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
- <span data-ttu-id="ae33f-122">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="ae33f-122">**Combined Modifiers.**</span></span> <span data-ttu-id="ae33f-123">`MustInherit`Aynı bildirimde ile birlikte belirtemezsiniz `NotInheritable` .</span><span class="sxs-lookup"><span data-stu-id="ae33f-123">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae33f-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae33f-124">Example</span></span>  

 <span data-ttu-id="ae33f-125">Aşağıdaki örnek, hem zorunlu devralmayı hem de geçersiz kılmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae33f-125">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="ae33f-126">Temel sınıf `shape` bir değişkeni tanımlar `acrossLine` .</span><span class="sxs-lookup"><span data-stu-id="ae33f-126">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="ae33f-127">Sınıflar `circle` ve `square` türetilir `shape` .</span><span class="sxs-lookup"><span data-stu-id="ae33f-127">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="ae33f-128">Tanımları devralınır `acrossLine` , ancak `area` Bu hesaplama her bir şekil türü için farklı olduğu için işlevi tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ae33f-128">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="ae33f-129">`shape1`' İ ve `shape2` türünü belirtebilirsiniz `shape` .</span><span class="sxs-lookup"><span data-stu-id="ae33f-129">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="ae33f-130">Ancak, `shape` işlevin işlevselliğine sahip olmadığı ve işaretlendiği için bir nesnesi oluşturamazsınız `area` `MustInherit` .</span><span class="sxs-lookup"><span data-stu-id="ae33f-130">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="ae33f-131">`shape`, Değişkenleri olarak bildirildiği `shape1` için, ve `shape2` türetilmiş sınıflardaki nesnelerle kısıtlıdır `circle` `square` .</span><span class="sxs-lookup"><span data-stu-id="ae33f-131">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="ae33f-132">Visual Basic, bu değişkenlere başka herhangi bir nesne atamanıza izin vermez, bu da size yüksek düzeyde güvenlik düzeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae33f-132">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="ae33f-133">Kullanım</span><span class="sxs-lookup"><span data-stu-id="ae33f-133">Usage</span></span>  

 <span data-ttu-id="ae33f-134">`MustInherit`Değiştirici Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ae33f-134">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="ae33f-135">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="ae33f-135">Class Statement</span></span>](../statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ae33f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae33f-136">See also</span></span>

- [<span data-ttu-id="ae33f-137">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="ae33f-137">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="ae33f-138">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="ae33f-138">NotInheritable</span></span>](notinheritable.md)
- [<span data-ttu-id="ae33f-139">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="ae33f-139">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="ae33f-140">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="ae33f-140">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
