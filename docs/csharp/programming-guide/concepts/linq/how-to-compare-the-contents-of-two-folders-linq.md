---
title: İki klasörün içeriği (LINQ) (C#) nasıl karşılaştırılır?
ms.date: 07/20/2015
ms.assetid: c7c4870e-c500-4de3-afa4-2c8e07f510e6
ms.openlocfilehash: 44dc97d6d48bed5e8b4d0376838e4dada2e8300c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169408"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-c"></a><span data-ttu-id="4742d-102">İki klasörün içeriği (LINQ) (C#) nasıl karşılaştırılır?</span><span class="sxs-lookup"><span data-stu-id="4742d-102">How to compare the contents of two folders (LINQ) (C#)</span></span>
<span data-ttu-id="4742d-103">Bu örnek, iki dosya girişini karşılaştırmanın üç yolunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="4742d-103">This example demonstrates three ways to compare two file listings:</span></span>  
  
- <span data-ttu-id="4742d-104">İki dosya listesinin aynı olup olmadığını belirten bir Boolean değeri için sorgu yaparak.</span><span class="sxs-lookup"><span data-stu-id="4742d-104">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>  
  
- <span data-ttu-id="4742d-105">Her iki klasörde bulunan dosyaları almak için kavşak için sorgulayarak.</span><span class="sxs-lookup"><span data-stu-id="4742d-105">By querying for the intersection to retrieve the files that are in both folders.</span></span>  
  
- <span data-ttu-id="4742d-106">Bir klasörde değil, diğer dosyaları almak için ayarlanan fark için sorgulayarak.</span><span class="sxs-lookup"><span data-stu-id="4742d-106">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4742d-107">Burada gösterilen teknikler, her türden nesne dizilerini karşılaştırmak için uyarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="4742d-107">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>  
  
 <span data-ttu-id="4742d-108">Burada `FileComparer` gösterilen sınıf, Standart Sorgu Operatörleri ile birlikte özel bir karşılayıcı sınıfının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4742d-108">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="4742d-109">Sınıf gerçek dünya senaryolarında kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="4742d-109">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="4742d-110">Her klasörün içeriğinin aynı olup olmadığını belirlemek için her dosyanın ad ve uzunluğunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="4742d-110">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="4742d-111">Gerçek bir senaryoda, daha sıkı bir eşitlik denetimi gerçekleştirmek için bu karşılayıcıyı değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4742d-111">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4742d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="4742d-112">Example</span></span>  
  
```csharp  
namespace QueryCompareTwoDirs  
{  
    class CompareDirs  
    {  
  
        static void Main(string[] args)  
        {  
  
            // Create two identical or different temporary folders
            // on a local drive and change these file paths.  
            string pathA = @"C:\TestDir";  
            string pathB = @"C:\TestDir2";  
  
            System.IO.DirectoryInfo dir1 = new System.IO.DirectoryInfo(pathA);  
            System.IO.DirectoryInfo dir2 = new System.IO.DirectoryInfo(pathB);  
  
            // Take a snapshot of the file system.  
            IEnumerable<System.IO.FileInfo> list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
            IEnumerable<System.IO.FileInfo> list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
            //A custom file comparer defined below  
            FileCompare myFileCompare = new FileCompare();  
  
            // This query determines whether the two folders contain  
            // identical file lists, based on the custom file comparer  
            // that is defined in the FileCompare class.  
            // The query executes immediately because it returns a bool.  
            bool areIdentical = list1.SequenceEqual(list2, myFileCompare);  
  
            if (areIdentical == true)  
            {  
                Console.WriteLine("the two folders are the same");  
            }  
            else  
            {  
                Console.WriteLine("The two folders are not the same");  
            }  
  
            // Find the common files. It produces a sequence and doesn't
            // execute until the foreach statement.  
            var queryCommonFiles = list1.Intersect(list2, myFileCompare);  
  
            if (queryCommonFiles.Any())  
            {  
                Console.WriteLine("The following files are in both folders:");  
                foreach (var v in queryCommonFiles)  
                {  
                    Console.WriteLine(v.FullName); //shows which items end up in result list  
                }  
            }  
            else  
            {  
                Console.WriteLine("There are no common files in the two folders.");  
            }  
  
            // Find the set difference between the two folders.  
            // For this example we only check one way.  
            var queryList1Only = (from file in list1  
                                  select file).Except(list2, myFileCompare);  
  
            Console.WriteLine("The following files are in list1 but not list2:");  
            foreach (var v in queryList1Only)  
            {  
                Console.WriteLine(v.FullName);  
            }  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
  
    // This implementation defines a very simple comparison  
    // between two FileInfo objects. It only compares the name  
    // of the files being compared and their length in bytes.  
    class FileCompare : System.Collections.Generic.IEqualityComparer<System.IO.FileInfo>  
    {  
        public FileCompare() { }  
  
        public bool Equals(System.IO.FileInfo f1, System.IO.FileInfo f2)  
        {  
            return (f1.Name == f2.Name &&  
                    f1.Length == f2.Length);  
        }  
  
        // Return a hash that reflects the comparison criteria. According to the
        // rules for IEqualityComparer<T>, if Equals is true, then the hash codes must  
        // also be equal. Because equality as defined here is a simple value equality, not  
        // reference identity, it is possible that two or more objects will produce the same  
        // hash code.  
        public int GetHashCode(System.IO.FileInfo fi)  
        {  
            string s = $"{fi.Name}{fi.Length}";
            return s.GetHashCode();  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4742d-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4742d-113">Compiling the Code</span></span>  
 <span data-ttu-id="4742d-114">System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4742d-114">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4742d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4742d-115">See also</span></span>

- [<span data-ttu-id="4742d-116">Nesnelere LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="4742d-116">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="4742d-117">LINQ ve Dosya Dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="4742d-117">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
