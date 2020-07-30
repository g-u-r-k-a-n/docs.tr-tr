---
title: Bir öğenin yüzeysel değerini alma (C#)
description: Bir öğenin yüzeysel değerini alma hakkında bilgi edinin. Yüzeysel değer yalnızca belirli bir öğe içindir.
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 597859e5b66606aa0cff9c1a475e79e6b66c39fc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301586"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>Bir öğenin yüzeysel değerini alma (C#)
Bu konu, bir öğenin yüzeysel değerinin nasıl alınacağını gösterir. Yüzeysel değer, tek bir dizeye birleştirilmiş tüm alt öğelerin değerlerini içeren derin değeri aksine, yalnızca belirli bir öğenin değeridir.  
  
 Ya da özelliğini kullanarak bir öğe değeri aldığınızda <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> , derin değeri alırsınız. Yüzeysel değeri almak için, `ShallowValue` Aşağıdaki örnekte gösterildiği gibi genişletme yöntemini kullanabilirsiniz. Yüzeysel değer alma, içeriğine göre öğeleri seçmek istediğinizde faydalıdır.  
  
 Aşağıdaki örnek, bir öğenin yüzeysel değerini alan bir genişletme yöntemi bildirir. Daha sonra, hesaplanmış bir değer içeren tüm öğeleri listelemek için bir sorgudaki genişletme yöntemini kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki metin dosyası Report.xml, bu örneğin kaynağıdır.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```csharp  
public static class MyExtensions  
{  
    public static string ShallowValue(this XElement xe)  
    {  
        return xe  
               .Nodes()  
               .OfType<XText>()  
               .Aggregate(new StringBuilder(),  
                          (s, c) => s.Append(c),  
                          s => s.ToString());  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement root = XElement.Load("Report.xml");  
  
        IEnumerable<XElement> query = from el in root.Descendants()  
                                      where el.ShallowValue().StartsWith("=")  
                                      select el;  
  
        foreach (var q in query)  
        {  
            Console.WriteLine("{0}{1}{2}",  
                q.Name.ToString().PadRight(8),  
                q.Attribute("Name").ToString().PadRight(20),  
                q.ShallowValue());  
        }  
    }  
}  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (C#)](./linq-to-xml-axes-overview.md)
