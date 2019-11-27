---
title: Parçalara Ayrılmış XName ve XNamespace Nesneleri (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: 0ffed5d00364f6614b439480607ed521f52754ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345728"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="0b8a7-102">Atomlanmış XName ve XNamespace nesneleri (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b8a7-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="0b8a7-103"><xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> nesneleri *atomlanmış*; diğer bir deyişle, aynı nitelikli adı içeriyorsa, aynı nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="0b8a7-104">Bu, sorgular için performans avantajları sağlar: iki atomılı adı eşitlik için karşılaştırdığınızda, temel alınan ara dilin yalnızca iki başvuruyu aynı nesneye işaret edip etmediğini belirlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="0b8a7-105">Temel alınan kodun, zaman alıcı olabilecek dize karşılaştırmaları yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>

## <a name="atomization-semantics"></a><span data-ttu-id="0b8a7-106">Atomleştirme semantiği</span><span class="sxs-lookup"><span data-stu-id="0b8a7-106">Atomization Semantics</span></span>

<span data-ttu-id="0b8a7-107">Atomleştirme, iki <xref:System.Xml.Linq.XName> nesnenin aynı yerel ada sahip olması ve aynı ad alanında olmaları durumunda aynı örneği paylaştıkları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="0b8a7-108">Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesnesi aynı ad alanı URI 'sine sahip ise, aynı örneği paylaşır.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>

<span data-ttu-id="0b8a7-109">Atomlanmış nesneleri etkinleştirmek için bir sınıf için, sınıf için Oluşturucu genel değil, özel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="0b8a7-110">Bunun nedeni, oluşturucunun genel olması, atomsuz olmayan bir nesne oluşturmanız olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="0b8a7-111"><xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> sınıfları bir dizeyi <xref:System.Xml.Linq.XName> veya <xref:System.Xml.Linq.XNamespace>dönüştürmek için örtük bir dönüştürme işleci uygular.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="0b8a7-112">Bu nesnelerin bir örneğini alma işlemi budur.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="0b8a7-113">Oluşturucuya erişilemediği için bir oluşturucuyu kullanarak bir örnek alınamaz.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>

<span data-ttu-id="0b8a7-114"><xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace>, karşılaştırılan iki nesnenin aynı örneğe başvuru olup olmadığını anlamak için eşitlik ve eşitsizlik işleçlerini da uygular.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>

## <a name="example"></a><span data-ttu-id="0b8a7-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b8a7-115">Example</span></span>

<span data-ttu-id="0b8a7-116">Aşağıdaki kod bazı <xref:System.Xml.Linq.XElement> nesneler oluşturur ve aynı adların aynı örneği paylaşacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>

```vb
Dim r1 As New XElement("Root", "data1")
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")

If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")
Else
    Console.WriteLine("Different")
End If

Dim n As XName = "Root"

If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")
Else
    Console.WriteLine("Different")
End If
```

<span data-ttu-id="0b8a7-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0b8a7-117">This example produces the following output:</span></span>

```console
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

<span data-ttu-id="0b8a7-118">Daha önce belirtildiği gibi, atomlanmış nesnelerin avantajı, bir <xref:System.Xml.Linq.XName> parametre olarak alan eksen yöntemlerinden birini kullandığınızda, eksen yönteminin yalnızca iki adların istenen öğeleri seçmek için aynı örneğe başvurulacağını belirlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>

<span data-ttu-id="0b8a7-119">Aşağıdaki örnek, bir <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> yöntemi çağrısına geçirir ve bu da atomleştirme deseninin nedeniyle daha iyi performansa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

<span data-ttu-id="0b8a7-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0b8a7-120">This example produces the following output:</span></span>

```xml
<C1>1</C1>
<C1>1</C1>
```

## <a name="see-also"></a><span data-ttu-id="0b8a7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b8a7-121">See also</span></span>

- [<span data-ttu-id="0b8a7-122">Performans (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b8a7-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
