---
title: Verileri Gruplandırma
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 8996eee748489c596bc5adc32f53b6b39dbfc6ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398389"
---
# <a name="grouping-data-visual-basic"></a>Verileri gruplandırma (Visual Basic)
Gruplandırma, her bir gruptaki öğelerin ortak bir özniteliği paylaşması için verileri gruplara yerleştirme işlemini ifade eder.  
  
 Aşağıdaki çizimde, bir karakter dizisini gruplandırmanın sonuçları gösterilmektedir. Her grup için anahtar karakterdir.  
  
 ![LINQ gruplama işlemini gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 Veri öğelerini gruplamak için kullanılan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Description|Sorgu Ifadesi söz dizimini Visual Basic|Daha Fazla Bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|GroupBy|Ortak bir özniteliği paylaşan öğeleri gruplandırır. Her grup bir nesne tarafından temsil edilir <xref:System.Linq.IGrouping%602> .|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|Bir <xref:System.Linq.Lookup%602> anahtar Seçici işlevine göre öğeleri (bire çok sözlüğüne) ekler.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu Ifadesi söz dizimi örneği  
 Aşağıdaki kod örneği, `Group By` bir listedeki tamsayıları, hatta veya tek olup olmadığına göre gruplamak için yan tümcesini kullanır.  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [Group By Yan Tümcesi](../../../language-reference/queries/group-by-clause.md)
- [Nasıl yapılır: dosyaları uzantıya göre gruplama (LINQ) (Visual Basic)](how-to-group-files-by-extension-linq.md)
- [Nasıl yapılır: grupları (LINQ) kullanarak bir dosyayı birçok dosyaya bölme (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
