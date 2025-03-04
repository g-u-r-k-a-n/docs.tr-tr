---
description: 'Hakkında daha fazla bilgi edinin: LINQ sorgularını normal ifadelerle birleştirme (Visual Basic)'
title: Normal ifadelerle LINQ sorgularını birleştirme
ms.date: 07/20/2015
ms.assetid: 3da1bd10-b0d8-4d5b-a637-966891c13592
ms.openlocfilehash: a2fd06f76c5c278ad1a67f3822151e5f73a2630e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424521"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-visual-basic"></a>LINQ sorgularını normal ifadelerle birleştirme (Visual Basic)

Bu örnek, <xref:System.Text.RegularExpressions.Regex> metin dizelerinde daha karmaşık eşleştirme için bir normal ifade oluşturmak üzere sınıfının nasıl kullanılacağını gösterir. LINQ sorgusu, normal ifadeyle arama yapmak istediğiniz dosyaları tam olarak filtrelemenizi ve sonuçları şekillendirmenizi kolaylaştırır.

## <a name="example"></a>Örnek

```vb
Imports System.IO
Imports System.Text.RegularExpressions

Class LinqRegExVB

    Shared Sub Main()

        ' Root folder to query, along with all subfolders.
        ' Modify this path as necessary so that it accesses your Visual Studio folder.
        Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio 14.0\"
        ' One of the following paths may be more appropriate on your computer.
        'Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio\2017\"

        ' Take a snapshot of the file system.
        Dim fileList As IEnumerable(Of FileInfo) = GetFiles(startFolder)

        ' Create a regular expression to find all things "Visual".
        Dim searchTerm As New Regex("Visual (Basic|C#|C\+\+|Studio)")

        ' Search the contents of each .htm file.
        ' Remove the where clause to find even more matches!
        ' This query produces a list of files where a match
        ' was found, and a list of the matches in that file.
        ' Note: Explicit typing of "Match" in select clause.
        ' This is required because MatchCollection is not a
        ' generic IEnumerable collection.
        Dim queryMatchingFiles = From afile In fileList
                                Where afile.Extension = ".htm"
                                Let fileText = File.ReadAllText(afile.FullName)
                                Let matches = searchTerm.Matches(fileText)
                                Where (matches.Count > 0)
                                Select Name = afile.FullName,
                                       Matches = From match As Match In matches
                                                 Select match.Value

        ' Execute the query.
        Console.WriteLine("The term " & searchTerm.ToString() & " was found in:")

        For Each fileMatches In queryMatchingFiles
            ' Trim the path a bit, then write
            ' the file name in which a match was found.
            Dim s = fileMatches.Name.Substring(startFolder.Length - 1)
            Console.WriteLine(s)

            ' For this file, write out all the matching strings
            For Each match In fileMatches.Matches
                Console.WriteLine("  " + match)
            Next
        Next

        ' Keep the console window open in debug mode
        Console.WriteLine("Press any key to exit")
        Console.ReadKey()
    End Sub

    ' Function to retrieve a list of files. Note that this is a copy
    ' of the file information.
    Shared Function GetFiles(root As String) As IEnumerable(Of FileInfo)
        Return From file In My.Computer.FileSystem.GetFiles(
                   root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")
               Select New FileInfo(file)
    End Function

End Class
```

<xref:System.Text.RegularExpressions.MatchCollection>Bir arama tarafından döndürülen nesneyi de sorgulayabileceğinizi unutmayın `RegEx` . Bu örnekte, sonuçlarda yalnızca her bir eşleşmenin değeri üretilir. Ancak, bu koleksiyonda tüm filtreleme, sıralama ve gruplama türlerini gerçekleştirmek için LINQ kullanmak da mümkündür. <xref:System.Text.RegularExpressions.MatchCollection>Genel olmayan bir <xref:System.Collections.IEnumerable> koleksiyon olduğundan, sorgudaki aralık değişkeninin türünü açıkça belirtmelisiniz.

## <a name="compile-the-code"></a>Kodu derle

Visual Basic konsol uygulaması projesi oluşturun, kod örneğini kopyalayıp yapıştırın ve proje özelliklerindeki başlangıç nesnesi değerini ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](linq-and-strings.md)
- [LINQ ve dosya dizinleri (Visual Basic)](linq-and-file-directories.md)
