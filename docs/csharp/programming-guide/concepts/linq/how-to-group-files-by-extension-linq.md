---
title: Dosyaları uzantıya göre gruplama (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: d12b40c7dba7bd3e10f30ddfd394b25c36794428
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345894"
---
# <a name="how-to-group-files-by-extension-linq-c"></a><span data-ttu-id="0fcdc-102">Dosyaları uzantıya göre gruplama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="0fcdc-102">How to group files by extension (LINQ) (C#)</span></span>
<span data-ttu-id="0fcdc-103">Bu örnek, LINQ 'ın dosya veya klasör listelerinde gelişmiş gruplandırma ve sıralama işlemleri gerçekleştirmek için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0fcdc-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="0fcdc-104">Ayrıca, <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> yöntemleri kullanılarak konsol penceresinde nasıl çıkış yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0fcdc-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fcdc-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0fcdc-105">Example</span></span>  
 <span data-ttu-id="0fcdc-106">Aşağıdaki sorguda, belirtilen dizin ağacının içeriğini dosya adı uzantısı tarafından nasıl gruplandırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0fcdc-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```csharp  
class GroupByExtension  
{  
    // This query will sort all the files under the specified folder  
    //  and subfolder into groups keyed by the file extension.  
    private static void Main()  
    {  
        // Take a snapshot of the file system.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Used in WriteLine to trim output lines.  
        int trimLength = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Create the query.  
        var queryGroupByExt =  
            from file in fileList  
            group file by file.Extension.ToLower() into fileGroup  
            orderby fileGroup.Key  
            select fileGroup;  
  
        // Display one group at a time. If the number of   
        // entries is greater than the number of lines  
        // in the console window, then page the output.  
        PageOutput(trimLength, queryGroupByExt);  
    }  
  
    // This method specifically handles group queries of FileInfo objects with string keys.  
    // It can be modified to work for any long listings of data. Note that explicit typing  
    // must be used in method signatures. The groupbyExtList parameter is a query that produces  
    // groups of FileInfo objects with string keys.  
    private static void PageOutput(int rootLength,  
                                    IEnumerable<System.Linq.IGrouping<string, System.IO.FileInfo>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine(filegroup.Key == String.Empty ? "[none]" : filegroup.Key);  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var f in resultPage)  
                {  
                    Console.WriteLine("\t{0}", f.FullName.Substring(rootLength));  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="0fcdc-107">Bu programın çıktısı, yerel dosya sisteminin ayrıntılarına ve `startFolder` ne şekilde ayarlandığına bağlı olarak uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="0fcdc-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="0fcdc-108">Tüm sonuçların görüntülenmesini sağlamak için bu örnek, sonuçların nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0fcdc-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="0fcdc-109">Windows ve Web uygulamalarına aynı teknikler de uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="0fcdc-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="0fcdc-110">Kodun bir gruptaki öğelerin, iç içe geçmiş `foreach` döngüsünün gerekli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0fcdc-110">Notice that because the code pages the items in a group, a nested `foreach` loop is required.</span></span> <span data-ttu-id="0fcdc-111">Ayrıca, listedeki geçerli konumu hesaplamak için bazı ek Logic de vardır ve kullanıcının sayfalamayı durdurmasına ve programdan çıkmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0fcdc-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="0fcdc-112">Bu durumda, disk belleği sorgusu özgün sorgudaki önbelleğe alınmış sonuçlara karşı çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="0fcdc-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="0fcdc-113">Diğer bağlamlarda, örneğin LINQ to SQL, önbelleğe alma gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0fcdc-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0fcdc-114">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="0fcdc-114">Compiling the Code</span></span>  
 <span data-ttu-id="0fcdc-115">System. C# lınq ve System.IO ad alanları için `using` yönergeler içeren bir konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0fcdc-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fcdc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fcdc-116">See also</span></span>

- [<span data-ttu-id="0fcdc-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="0fcdc-117">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="0fcdc-118">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="0fcdc-118">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
