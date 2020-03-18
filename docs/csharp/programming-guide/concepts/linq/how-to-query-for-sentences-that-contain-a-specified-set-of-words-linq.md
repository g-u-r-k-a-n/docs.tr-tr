---
title: Belirli bir sözcük kümesi (LINQ) (C#) içeren cümleler için sorgulama
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: df279f57d9965d796397cbcf7a0f3ba05bf9e5c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168862"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="2acf6-102">Belirli bir sözcük kümesi (LINQ) (C#) içeren cümleler için sorgulama</span><span class="sxs-lookup"><span data-stu-id="2acf6-102">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>
<span data-ttu-id="2acf6-103">Bu örnek, belirtilen sözcük kümesinin her biri için eşleşmeler içeren bir metin dosyasındaki cümlelerin nasıl bulunup bulunulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2acf6-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="2acf6-104">Bu örnekte arama terimleri dizisi sabit kodlanmış olsa da, çalışma zamanında dinamik olarak doldurulabilir.</span><span class="sxs-lookup"><span data-stu-id="2acf6-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="2acf6-105">Bu örnekte, sorgu "Geçmiş", "veri" ve "tümleşik" sözcüklerini içeren tümceleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2acf6-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="2acf6-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2acf6-106">Example</span></span>  
  
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
  
 <span data-ttu-id="2acf6-107">Sorgu, önce metni cümlelere bölerek, sonra da cümleleri her sözcüğü tutan bir dizi dizeye bölerek çalışır.</span><span class="sxs-lookup"><span data-stu-id="2acf6-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="2acf6-108">Bu dizilerin her biri <xref:System.Linq.Enumerable.Distinct%2A> için yöntem tüm yinelenen sözcükleri kaldırır <xref:System.Linq.Enumerable.Intersect%2A> ve sorgu sözcük `wordsToMatch` dizisi ve dizi üzerinde bir işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2acf6-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="2acf6-109">Kesişim sayısı `wordsToMatch` dizinin sayısıyla aynıysa, tüm sözcükler sözcüklerde bulunur ve özgün tümce döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2acf6-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="2acf6-110">Çağrıda <xref:System.String.Split%2A>noktalama işaretleri, dizeden kaldırmak için ayırıcı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2acf6-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="2acf6-111">Bunu yapmadıysanız, örneğin `wordsToMatch` dizideki "Tarihsel" dizesini "Tarihsel olarak" eşleştirmez.</span><span class="sxs-lookup"><span data-stu-id="2acf6-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="2acf6-112">Kaynak metinde bulunan noktalama işaretleritürlerine bağlı olarak ek ayırıcılar kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2acf6-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2acf6-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2acf6-113">Compiling the Code</span></span>  
<span data-ttu-id="2acf6-114">System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2acf6-114">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="2acf6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2acf6-115">See also</span></span>

- [<span data-ttu-id="2acf6-116">LINQ ve Dizeleri (C#)</span><span class="sxs-lookup"><span data-stu-id="2acf6-116">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
