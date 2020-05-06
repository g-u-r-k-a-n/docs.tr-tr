---
title: Ad-Değer Çiftleri Sağlama
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: b8c9487330239e7e6365055d5f08a02f2dbb0e37
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796164"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a><span data-ttu-id="1e37f-102">Ad/değer çiftlerini koruma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e37f-102">Maintaining Name/Value Pairs (Visual Basic)</span></span>
<span data-ttu-id="1e37f-103">Birçok uygulamanın ad/değer çiftleri olarak en iyi şekilde tutulan bilgileri tutması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e37f-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="1e37f-104">Bu bilgiler yapılandırma bilgileri veya genel ayarlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e37f-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1e37f-105">bir ad/değer çiftleri kümesini saklamayı kolaylaştıran bazı yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="1e37f-105">contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="1e37f-106">Bilgileri öznitelik olarak veya bir alt öğe kümesi olarak tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e37f-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="1e37f-107">Bilgileri öznitelik veya alt öğe olarak tutma arasındaki tek fark, özniteliklerin bir öğe için yalnızca belirli bir ada sahip tek bir öznitelik olabilecek kısıtlamaya sahip olduğu kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="1e37f-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="1e37f-108">Bu sınırlama alt öğeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1e37f-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="1e37f-109">SetAttributeValue ve SetElementValue</span><span class="sxs-lookup"><span data-stu-id="1e37f-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="1e37f-110">Ad/değer çiftlerini tutmaya yardımcı olan iki yöntem ve ' <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> <xref:System.Xml.Linq.XElement.SetElementValue%2A>dir.</span><span class="sxs-lookup"><span data-stu-id="1e37f-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="1e37f-111">Bu iki yöntem benzer anlamlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1e37f-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="1e37f-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>bir öğenin özniteliklerini ekleyebilir, değiştirebilir veya kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="1e37f-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
- <span data-ttu-id="1e37f-113">Varolmayan bir özniteliğin <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> adıyla çağırırsanız, yöntemi yeni bir öznitelik oluşturur ve belirtilen öğeye ekler.</span><span class="sxs-lookup"><span data-stu-id="1e37f-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="1e37f-114">Var olan bir <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> özniteliğin adı ile ve belirtilen içeriklerde bir çağrı yaparsanız, özniteliğin içeriği belirtilen içerikle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e37f-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="1e37f-115">Varolan bir özniteliğin <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> adıyla çağrı yaparsanız ve içerik için null belirtirseniz, öznitelik üst öğesinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="1e37f-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="1e37f-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A>bir öğenin alt öğelerini ekleyebilir, değiştirebilir veya kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="1e37f-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
- <span data-ttu-id="1e37f-117">Var olmayan bir <xref:System.Xml.Linq.XElement.SetElementValue%2A> alt öğe adı ile çağırırsanız, yöntemi yeni bir öğesi oluşturur ve belirtilen öğeye ekler.</span><span class="sxs-lookup"><span data-stu-id="1e37f-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="1e37f-118">Var olan bir <xref:System.Xml.Linq.XElement.SetElementValue%2A> öğenin adı ile ve belirtilen içeriklerle çağırırsanız, öğenin içeriği belirtilen içerikle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e37f-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="1e37f-119">Varsa, varolan <xref:System.Xml.Linq.XElement.SetElementValue%2A> bir öğenin adıyla çağrı yaparsanız ve içerik için null belirtirseniz, öğe üst öğesinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="1e37f-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e37f-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e37f-120">Example</span></span>  
 <span data-ttu-id="1e37f-121">Aşağıdaki örnek, öznitelikleri olmayan bir öğesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e37f-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="1e37f-122">Daha sonra bir ad <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> /değer çiftleri listesi oluşturmak ve korumak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e37f-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22)  
root.SetAttributeValue("Left", 20)  
root.SetAttributeValue("Bottom", 122)  
root.SetAttributeValue("Right", 300)  
root.SetAttributeValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
  
' Replace the value of Top.  
root.SetAttributeValue("Top", 10)  
Console.WriteLine(root)  
  
' Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="1e37f-123">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1e37f-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="1e37f-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e37f-124">Example</span></span>  
 <span data-ttu-id="1e37f-125">Aşağıdaki örnek, alt öğeleri olmayan bir öğe oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e37f-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="1e37f-126">Daha sonra bir ad <xref:System.Xml.Linq.XElement.SetElementValue%2A> /değer çiftleri listesi oluşturmak ve korumak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e37f-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22)  
root.SetElementValue("Left", 20)  
root.SetElementValue("Bottom", 122)  
root.SetElementValue("Right", 300)  
root.SetElementValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Replace the value of Top.  
root.SetElementValue("Top", 10)  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Remove DefaultColor.  
root.SetElementValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="1e37f-127">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1e37f-127">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>
----
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>
```  
  
## <a name="see-also"></a><span data-ttu-id="1e37f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e37f-128">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [<span data-ttu-id="1e37f-129">XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e37f-129">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
