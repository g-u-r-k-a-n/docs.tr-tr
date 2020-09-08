---
title: C#-LINQ to XML metin olarak XML 'e akış dönüştürmeleri gerçekleştirme
description: İşlem için bir metin dosyasını akışa almak üzere bir kerede bir satırı serbest bırakma uzantısı yöntemini kullanabilirsiniz. Bu teknik, tüm dosyayı yükleyen ve sonra işleyen tekniklere kıyasla bellek gereksinimlerini azaltır.
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 8e0d710d7cbc6de8cc60721c211376a82b6c29fc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553919"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-in-c-linq-to-xml"></a><span data-ttu-id="70555-104">C# ' de metnin XML 'e akış dönüştürmeleri gerçekleştirme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="70555-104">How to perform streaming transformations of text to XML in C# (LINQ to XML)</span></span>

<span data-ttu-id="70555-105">İşlem için bir metin dosyasını akışa almak üzere bir kerede bir satırı serbest bırakma uzantısı yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70555-105">You can use an extension method that releases a line at a time to stream a text file for processing.</span></span> <span data-ttu-id="70555-106">Bu teknik, tüm dosyayı yükleyen ve sonra işleyen tekniklere kıyasla bellek gereksinimlerini azaltır.</span><span class="sxs-lookup"><span data-stu-id="70555-106">This technique reduces memory requirements compared to techniques which load the entire file and then process it.</span></span>

<span data-ttu-id="70555-107">Genişletme yöntemi, yapıyı kullanarak satırı sağlayabilir `yield return` .</span><span class="sxs-lookup"><span data-stu-id="70555-107">The extension method can provide the line using the `yield return` construct.</span></span> <span data-ttu-id="70555-108">Bir LINQ sorgusu, akışı yavaş ertelenmiş bir biçimde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="70555-108">A LINQ query can process the stream in a lazy deferred fashion.</span></span> <span data-ttu-id="70555-109"><xref:System.Xml.Linq.XStreamingElement>Çıktıyı akışa almak için kullanırsanız, kaynak metin dosyasının boyutundan bağımsız olarak en az miktarda belleği kullanan metin DOSYASıNDAN XML 'e bir dönüşüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70555-109">If you use <xref:System.Xml.Linq.XStreamingElement> to stream output, you can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

> [!NOTE]
> <span data-ttu-id="70555-110">Bu teknik en iyi şekilde, tüm dosyayı bir kez işleyebilmeniz ve satırları kaynak belgeden sırayla ele almanız durumunda en iyi şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="70555-110">The technique is best applied in situations in which you can process the entire file once, taking the lines in order from the source document.</span></span> <span data-ttu-id="70555-111">Dosyayı birden çok kez işleme veya işlemeden önce sıralama, bir akış tekniğinin performans avantajlarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="70555-111">Processing the file more than once, or sorting before processing, reduces the performance benefits of a streaming technique.</span></span>

## <a name="example-use-an-extension-method-to-stream-text"></a><span data-ttu-id="70555-112">Örnek, metin akışı için bir genişletme yöntemi kullanın</span><span class="sxs-lookup"><span data-stu-id="70555-112">Example Use an extension method to stream text</span></span>

<span data-ttu-id="70555-113">Örnek, People.txt, kaynağı olarak aşağıdaki metin dosyasını kullanır:</span><span class="sxs-lookup"><span data-stu-id="70555-113">The example uses the following text file, People.txt, as its source:</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

<span data-ttu-id="70555-114">Örneğin kodunda, genişletme yöntemi `Lines` metni bir kerede bir satır sağlar:</span><span class="sxs-lookup"><span data-stu-id="70555-114">In the code for the example, extension method `Lines` provides the text a line at a time:</span></span>

```csharp
public static class StreamReaderSequence
{
    public static IEnumerable<string> Lines(this StreamReader source)
    {
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
        while ((line = source.ReadLine()) != null)
        {
            yield return line;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
            from line in sr.Lines()
            let items = line.Split(',')
            where !line.StartsWith("#")
            select new XElement("Person",
                       new XAttribute("ID", items[0]),
                       new XElement("First", items[1]),
                       new XElement("Last", items[2]),
                       new XElement("Occupation", items[3])
                   )
        );
        Console.WriteLine(xmlTree);
        sr.Close();
    }
}
```

<span data-ttu-id="70555-115">Örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="70555-115">The example produces the following output:</span></span>

```xml
<Root>
  <Person ID="1">
    <First>Tai</First>
    <Last>Yee</Last>
    <Occupation>Writer</Occupation>
  </Person>
  <Person ID="2">
    <First>Nikolay</First>
    <Last>Grachev</Last>
    <Occupation>Programmer</Occupation>
  </Person>
  <Person ID="3">
    <First>David</First>
    <Last>Wright</Last>
    <Occupation>Inventor</Occupation>
  </Person>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="70555-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70555-116">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
