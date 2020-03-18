---
title: LINQ - XML Olayları (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 8e0cb4519dd0fc2bed443d9a62b9a2545d10e161
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253168"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="4532c-102">LINQ - XML Olayları (C#)</span><span class="sxs-lookup"><span data-stu-id="4532c-102">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="4532c-103">olaylar, bir XML ağacı değiştirildiğinde bilgilendirilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4532c-103">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="4532c-104">Herhangi bir örneğine olaylar <xref:System.Xml.Linq.XObject>ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4532c-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="4532c-105">Olay işleyicisi daha sonra bu <xref:System.Xml.Linq.XObject> ve onun torunları herhangi bir değişiklik için olaylar alırsınız.</span><span class="sxs-lookup"><span data-stu-id="4532c-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="4532c-106">Örneğin, ağacın köküne bir olay işleyicisi ekleyebilir ve bu olay işleyicisinden ağaca yapılan tüm değişiklikleri işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4532c-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="4532c-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Olay örnekleri için <xref:System.Xml.Linq.XObject.Changing> bkz. <xref:System.Xml.Linq.XObject.Changed></span><span class="sxs-lookup"><span data-stu-id="4532c-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="4532c-108">Türleri ve Etkinlikler</span><span class="sxs-lookup"><span data-stu-id="4532c-108">Types and Events</span></span>  
 <span data-ttu-id="4532c-109">Olaylarla çalışırken aşağıdaki türleri kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="4532c-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="4532c-110">Tür</span><span class="sxs-lookup"><span data-stu-id="4532c-110">Type</span></span>|<span data-ttu-id="4532c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4532c-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="4532c-112">Bir olay için yükseltildiğinde olay türünü <xref:System.Xml.Linq.XObject>belirtir.</span><span class="sxs-lookup"><span data-stu-id="4532c-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="4532c-113">Olaylar <xref:System.Xml.Linq.XObject.Changing> ve olaylar <xref:System.Xml.Linq.XObject.Changed> için veri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4532c-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="4532c-114">Bir XML ağacını değiştirdiğinizde aşağıdaki olaylar yükseltilir:</span><span class="sxs-lookup"><span data-stu-id="4532c-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="4532c-115">Olay</span><span class="sxs-lookup"><span data-stu-id="4532c-115">Event</span></span>|<span data-ttu-id="4532c-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4532c-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="4532c-117">Şu <xref:System.Xml.Linq.XObject> ya da onun soyundan herhangi biri değişmeden hemen önce meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="4532c-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="4532c-118">Bir <xref:System.Xml.Linq.XObject> değişti veya onun torunlarından herhangi biri değişti oluşur.</span><span class="sxs-lookup"><span data-stu-id="4532c-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4532c-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="4532c-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4532c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4532c-120">Description</span></span>  
 <span data-ttu-id="4532c-121">Olaylar, bir XML ağacında bazı toplu bilgileri korumak istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4532c-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="4532c-122">Örneğin, faturanın satır maddelerinin toplamı olan bir fatura toplamını korumak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4532c-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="4532c-123">Bu örnek, karmaşık öğe `Items`altında tüm alt öğelerin toplamını korumak için olayları kullanır.</span><span class="sxs-lookup"><span data-stu-id="4532c-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4532c-124">Kod</span><span class="sxs-lookup"><span data-stu-id="4532c-124">Code</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Total", "0"),  
    new XElement("Items")  
);  
XElement total = root.Element("Total");  
XElement items = root.Element("Items");  
items.Changed += (object sender, XObjectChangeEventArgs cea) =>  
{  
    switch (cea.ObjectChange)  
    {  
        case XObjectChange.Add:  
            if (sender is XElement)  
                total.Value = ((int)total + (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();  
            break;  
        case XObjectChange.Remove:  
            if (sender is XElement)  
                total.Value = ((int)total - (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();  
            break;  
    }  
    Console.WriteLine("Changed {0} {1}",  
      sender.GetType().ToString(), cea.ObjectChange.ToString());  
};  
items.SetElementValue("Item1", 25);  
items.SetElementValue("Item2", 50);  
items.SetElementValue("Item2", 75);  
items.SetElementValue("Item3", 133);  
items.SetElementValue("Item1", null);  
items.SetElementValue("Item4", 100);  
Console.WriteLine("Total:{0}", (int)total);  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a><span data-ttu-id="4532c-125">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="4532c-125">Comments</span></span>  
 <span data-ttu-id="4532c-126">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4532c-126">This code produces the following output:</span></span>  
  
```output  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  