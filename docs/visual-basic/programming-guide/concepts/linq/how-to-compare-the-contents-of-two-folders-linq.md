---
title: 'Nasıl yapılır: İki Klasörün İçeriğini Karşılaştırma (LINQ)'
ms.date: 07/20/2015
ms.assetid: 903c7e9a-f48d-4a07-a8a8-5450d2646efa
ms.openlocfilehash: 05031466eeafae2dc63db36e9380034ddf9cbf15
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337538"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-visual-basic"></a><span data-ttu-id="ab08a-102">Nasıl yapılır: Iki klasörün Içeriğini karşılaştırma (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab08a-102">How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="ab08a-103">Bu örnekte iki dosya listesi karşılaştırmanın üç yolu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ab08a-103">This example demonstrates three ways to compare two file listings:</span></span>

- <span data-ttu-id="ab08a-104">İki dosya listelerinin aynı olup olmadığını belirten bir Boolean değeri sorgulayarak.</span><span class="sxs-lookup"><span data-stu-id="ab08a-104">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>

- <span data-ttu-id="ab08a-105">Her iki klasördeki dosyaları almak için kesişimini sorgulayarak.</span><span class="sxs-lookup"><span data-stu-id="ab08a-105">By querying for the intersection to retrieve the files that are in both folders.</span></span>

- <span data-ttu-id="ab08a-106">Bir klasörde olan ancak diğeri olmayan dosyaları almak için ayarlanan farkı sorgulayarak.</span><span class="sxs-lookup"><span data-stu-id="ab08a-106">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ab08a-107">Burada gösterilen teknikler, herhangi bir türdeki nesne dizilerini karşılaştırmak için uyarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ab08a-107">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>

<span data-ttu-id="ab08a-108">Burada gösterilen `FileComparer` sınıfı, standart sorgu Işleçleri ile birlikte özel bir karşılaştırıcı sınıfının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab08a-108">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="ab08a-109">Sınıfı, gerçek dünyada senaryolarda kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="ab08a-109">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="ab08a-110">Her bir klasörün içeriğinin aynı olup olmadığını anlamak için her bir dosyanın bayt cinsinden adını ve uzunluğunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab08a-110">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="ab08a-111">Gerçek dünyada bir senaryoda, daha kapsamlı bir eşitlik denetimi gerçekleştirmek için bu karşılaştırıcıyı değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ab08a-111">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>

## <a name="example"></a><span data-ttu-id="ab08a-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab08a-112">Example</span></span>

```vb
Module CompareDirs
    Public Sub Main()

        ' Create two identical or different temporary folders
        ' on a local drive and add files to them.
        ' Then set these file paths accordingly.
        Dim pathA As String = "C:\TestDir"
        Dim pathB As String = "C:\TestDir2"

        ' Take a snapshot of the file system.
        Dim dir1 As New System.IO.DirectoryInfo(pathA)
        Dim dir2 As New System.IO.DirectoryInfo(pathB)

        Dim list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories)
        Dim list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories)

        ' Create the FileCompare object we'll use in each query
        Dim myFileCompare As New FileCompare

        ' This query determines whether the two folders contain
        ' identical file lists, based on the custom file comparer
        ' that is defined in the FileCompare class.
        ' The query executes immediately because it returns a bool.
        Dim areIdentical As Boolean = list1.SequenceEqual(list2, myFileCompare)
        If areIdentical = True Then
            Console.WriteLine("The two folders are the same.")
        Else
            Console.WriteLine("The two folders are not the same.")
        End If

        ' Find common files in both folders. It produces a sequence and doesn't execute
        ' until the foreach statement.
        Dim queryCommonFiles = list1.Intersect(list2, myFileCompare)

        If queryCommonFiles.Count() > 0 Then

            Console.WriteLine("The following files are in both folders:")
            For Each fi As System.IO.FileInfo In queryCommonFiles
                Console.WriteLine(fi.FullName)
            Next
        Else
            Console.WriteLine("There are no common files in the two folders.")
        End If

        ' Find the set difference between the two folders.
        ' For this example we only check one way.
        Dim queryDirAOnly = list1.Except(list2, myFileCompare)
        Console.WriteLine("The following files are in dirA but not dirB:")
        For Each fi As System.IO.FileInfo In queryDirAOnly
            Console.WriteLine(fi.FullName)
        Next

        ' Keep the console window open in debug mode
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

    ' This implementation defines a very simple comparison
    ' between two FileInfo objects. It only compares the name
    ' of the files being compared and their length in bytes.
    Public Class FileCompare
        Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo)

        Public Function Equals1(ByVal x As System.IO.FileInfo, ByVal y As System.IO.FileInfo) _
            As Boolean Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo).Equals

            If (x.Name = y.Name) And (x.Length = y.Length) Then
                Return True
            Else
                Return False
            End If
        End Function

        ' Return a hash that reflects the comparison criteria. According to the
        ' rules for IEqualityComparer(Of T), if Equals is true, then the hash codes must
        ' also be equal. Because equality as defined here is a simple value equality, not
        ' reference identity, it is possible that two or more objects will produce the same
        ' hash code.
        Public Function GetHashCode1(ByVal fi As System.IO.FileInfo) _
            As Integer Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo).GetHashCode
            Dim s As String = fi.Name & fi.Length
            Return s.GetHashCode()
        End Function
    End Class
End Module
```

## <a name="compile-the-code"></a><span data-ttu-id="ab08a-113">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="ab08a-113">Compile the code</span></span>

<span data-ttu-id="ab08a-114">System. Linq ad alanı için `Imports` bildirimiyle bir Visual Basic konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ab08a-114">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab08a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab08a-115">See also</span></span>

- [<span data-ttu-id="ab08a-116">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab08a-116">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="ab08a-117">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab08a-117">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
