---
title: Belirli bir sözcük kümesini (LINQ) içeren cümleleri sorgulama (LINQ) (C#)
description: Çalışma zamanında doldurulabilen her bir sözcük kümesi için eşleşmeler içeren bir metin dosyasında tümceler bulmak Için C# ' de LINQ kullanmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: c334c7948f19fb857709ff04a83e1dae56fc69da
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104531"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="fbbd0-103">Belirli bir sözcük kümesini (LINQ) içeren cümleleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fbbd0-103">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>
<span data-ttu-id="fbbd0-104">Bu örnek, belirli bir sözcük kümesinin her biri için eşleşmeler içeren bir metin dosyasında Tümcelerin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fbbd0-104">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="fbbd0-105">Bu örnekte, arama terimleri dizisi sabit kodlanmış olsa da, çalışma zamanında dinamik olarak doldurulabilir.</span><span class="sxs-lookup"><span data-stu-id="fbbd0-105">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="fbbd0-106">Bu örnekte sorgu, "tarihsel olarak", "Data" ve "Integrated" sözcüklerini içeren cümleleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="fbbd0-106">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbbd0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbbd0-107">Example</span></span>  
  
```csharp  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET Framework APIs. On the other side " +  
        @"are tables, columns, rows, nodes, and separate languages for dealing with " +  
        @"them. Data types often require translation between the two worlds; there are " +  
        @"different standard functions. Because the object world has no notion of query, a " +  
        @"query can only be represented as a string without compile-time type checking or " +  
        @"IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " +  
        @"objects in memory is often tedious and error-prone.";  
  
        // Split the text block into an array of sentences.  
        string[] sentences = text.Split(new char[] { '.', '?', '!' });  
  
        // Define the search terms. This list could also be dynamically populated at runtime.  
        string[] wordsToMatch = { "Historically", "data", "integrated" };  
  
        // Find sentences that contain all the terms in the wordsToMatch array.  
        // Note that the number of terms to match is not specified at compile time.  
        var sentenceQuery = from sentence in sentences  
                            let w = sentence.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' },  
                                                    StringSplitOptions.RemoveEmptyEntries)  
                            where w.Distinct().Intersect(wordsToMatch).Count() == wordsToMatch.Count()  
                            select sentence;  
  
        // Execute the query. Note that you can explicitly type  
        // the iteration variable here even though sentenceQuery  
        // was implicitly typed.
        foreach (string str in sentenceQuery)  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
Historically, the world of data and the world of objects have not been well integrated  
*/  
```  
  
 <span data-ttu-id="fbbd0-108">Sorgu önce metni cümlelere bölerek ve sonra cümleleri her bir sözcüğü tutan dizeler dizisine bölerek işe yarar.</span><span class="sxs-lookup"><span data-stu-id="fbbd0-108">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="fbbd0-109">Bu dizilerin her biri için yöntem, <xref:System.Linq.Enumerable.Distinct%2A> tüm yinelenen sözcükleri kaldırır ve sonra sorgu, <xref:System.Linq.Enumerable.Intersect%2A> Word dizisi ve dizi üzerinde bir işlem gerçekleştirir `wordsToMatch` .</span><span class="sxs-lookup"><span data-stu-id="fbbd0-109">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="fbbd0-110">Kesişimin sayısı dizinin sayısıyla aynıysa `wordsToMatch` , sözcüklerde tüm sözcükler bulunur ve özgün tümce döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fbbd0-110">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="fbbd0-111">Çağrısında <xref:System.String.Split%2A> , noktalama işaretleri dizeden kaldırmak için ayırıcılar olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fbbd0-111">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="fbbd0-112">Bunu yapmadıysanız, örneğin, dizide "tarihsel" olarak eşleşmeyen "tarihsel" bir dizeye sahip olabilirsiniz `wordsToMatch` .</span><span class="sxs-lookup"><span data-stu-id="fbbd0-112">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="fbbd0-113">Kaynak metinde bulunan noktalama türlerine bağlı olarak ek ayırıcılar kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="fbbd0-113">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fbbd0-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fbbd0-114">Compiling the Code</span></span>  
<span data-ttu-id="fbbd0-115">`using`System. LINQ ve System.IO ad alanları için yönergeler içeren bir C# konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fbbd0-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbbd0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbbd0-116">See also</span></span>

- [<span data-ttu-id="fbbd0-117">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="fbbd0-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
