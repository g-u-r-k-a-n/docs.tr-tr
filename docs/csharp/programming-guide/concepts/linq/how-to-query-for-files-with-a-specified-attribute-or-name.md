---
title: Belirtilen bir özniteliğe veya ada (C#) sahip dosyaları sorgulama
ms.date: 07/20/2015
ms.assetid: 560e3879-b0b3-4549-ad02-0a53aff2f83c
ms.openlocfilehash: 8ecf3263dcee9b54d01dd0b577ba8bec2a199da9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346724"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-c"></a><span data-ttu-id="22874-102">Belirtilen bir özniteliğe veya ada (C#) sahip dosyaları sorgulama</span><span class="sxs-lookup"><span data-stu-id="22874-102">How to query for files with a specified attribute or name (C#)</span></span>
<span data-ttu-id="22874-103">Bu örnek, belirtilen bir dizin ağacında belirtilen dosya adı uzantısına (örneğin ". txt") sahip tüm dosyaların nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="22874-103">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="22874-104">Ayrıca, oluşturma zamanına göre ağaçta en yeni veya en eski dosyanın nasıl dönegösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="22874-104">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22874-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="22874-105">Example</span></span>  
  
```csharp  
class FindFileByExtension  
{  
    // This query will produce the full path for all .txt files  
    // under the specified folder including subfolders.  
    // It orders the list according to the file name.  
    static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Create the query  
        IEnumerable<System.IO.FileInfo> fileQuery =  
            from file in fileList  
            where file.Extension == ".txt"  
            orderby file.Name  
            select file;  
  
        //Execute the query. This might write out a lot of files!  
        foreach (System.IO.FileInfo fi in fileQuery)  
        {  
            Console.WriteLine(fi.FullName);  
        }  
  
        // Create and execute a new query by using the previous   
        // query as a starting point. fileQuery is not   
        // executed again until the call to Last()  
        var newestFile =  
            (from file in fileQuery  
             orderby file.CreationTime  
             select new { file.FullName, file.CreationTime })  
            .Last();  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}",  
            newestFile.FullName, newestFile.CreationTime);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="22874-106">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="22874-106">Compiling the Code</span></span>  
  <span data-ttu-id="22874-107">System. C# lınq ve System.IO ad alanları için `using` yönergeler içeren bir konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="22874-107">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="22874-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22874-108">See also</span></span>

- [<span data-ttu-id="22874-109">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="22874-109">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="22874-110">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="22874-110">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
