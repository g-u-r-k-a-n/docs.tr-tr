---
title: Ara materialization (C#)
description: Bu C# örneği, ilk öğeyi bırakmadan önce bir sorgunun AppendString 'in kaynağın tamamını numaralandırması için yol gösteren ara materialization 'ı gösterir.
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 30951aaeea261efbd414205bcc54b63106324344
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165724"
---
# <a name="intermediate-materialization-c"></a>Ara materialization (C#)
Dikkatli değilseniz, bazı durumlarda, Sorgularınızdaki koleksiyonların erken olarak kullanıma hazır hale gelmesine neden olarak uygulamanızın bellek ve performans profilini büyük ölçüde değiştirebilirsiniz. Bazı standart sorgu işleçleri, tek bir öğeyi oluşturmadan önce kaynak koleksiyonlarının çalışmasının oluşturulmasına neden olur. Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> ilk olarak tüm kaynak koleksiyonu boyunca yinelenir, sonra tüm öğeleri sıralar ve son olarak ilk öğeyi verir. Bu, sıralı bir koleksiyonun ilk öğesini almak pahalı olduğu anlamına gelir; Bundan sonra her öğe pahalı değildir. Bu anlamlı olur: Bu sorgu işlecinin başka bir şekilde yapması imkansız olabilir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, önceki örneği değiştirir. `AppendString`Yöntemi, <xref:System.Linq.Enumerable.ToList%2A> kaynak üzerinde yineleme yapmadan önce çağırır. Bu, materialization oluşturulmasına neden olur.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 Bu örnekte, çağrısının <xref:System.Linq.Enumerable.ToList%2A> `AppendString` ilk öğeyi bırakmadan önce tüm kaynağını numaralandırmasına neden olduğunu görebilirsiniz. Kaynak büyük bir diziyse, bu, uygulamanın bellek profilini önemli ölçüde değiştirecek.  
  
 Standart sorgu işleçleri de birlikte zincirlenebilir. Bu öğreticideki son konu, bunu gösterir.  
  
- [Standart sorgu Işleçlerini birlikte zincirleme (C#)](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: sorguları birlikte zincirleme (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
