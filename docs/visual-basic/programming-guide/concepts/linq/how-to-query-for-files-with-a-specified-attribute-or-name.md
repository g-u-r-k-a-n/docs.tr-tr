---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: belirtilen bir özniteliğe veya ada sahip dosyaları sorgulama (Visual Basic)'
title: 'Nasıl yapılır: Belirli bir Öznitelik veya Ada Sahip Dosyaları Sorgulama'
ms.date: 07/20/2015
ms.assetid: b26026a3-3f43-448f-a582-259997af6be0
ms.openlocfilehash: 3eb58bf683b97c5806145395cb489f0e85c2071b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425730"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-visual-basic"></a><span data-ttu-id="8a7e6-103">Nasıl yapılır: belirtilen bir özniteliğe veya ada sahip dosyaları sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a7e6-103">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>

<span data-ttu-id="8a7e6-104">Bu örnek, belirtilen bir dizin ağacında belirtilen dosya adı uzantısına (örneğin ". txt") sahip tüm dosyaların nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a7e6-104">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="8a7e6-105">Ayrıca, oluşturma zamanına göre ağaçta en yeni veya en eski dosyanın nasıl dönegösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a7e6-105">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a7e6-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a7e6-106">Example</span></span>  
  
```vb  
Module FindFileByExtension  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' This query will produce the full path for all .txt files  
        ' under the specified folder including subfolders.  
        ' It orders the list according to the file name.  
        Dim fileQuery = From file In fileList _  
                        Where file.Extension = ".txt" _  
                        Order By file.Name _  
                        Select file  
  
        For Each file In fileQuery  
            Console.WriteLine(file.FullName)  
        Next  
  
        ' Create and execute a new query by using  
        ' the previous query as a starting point.  
        ' fileQuery is not executed again until the  
        ' call to Last  
        Dim fileQuery2 = From file In fileQuery _  
                         Order By file.CreationTime _  
                         Select file.Name, file.CreationTime  
  
        ' Execute the query  
        Dim newestFile = fileQuery2.Last  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}", _  
                newestFile.Name, newestFile.CreationTime)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="8a7e6-107">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="8a7e6-107">Compile the code</span></span>  

<span data-ttu-id="8a7e6-108">`Imports`System. Linq ad alanı için bir deyimle birlikte Visual Basic konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8a7e6-108">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8a7e6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a7e6-109">See also</span></span>

- [<span data-ttu-id="8a7e6-110">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a7e6-110">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="8a7e6-111">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a7e6-111">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
