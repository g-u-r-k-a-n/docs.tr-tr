---
description: 'Daha fazla bilgi edinin: nasıl yapılır: Içeriğe benzer dosyalardan Içerik ekleme (LINQ) (Visual Basic)'
title: 'Nasıl yapılır: Farklı Dosyalardan İçerik Birleştirme (LINQ)'
ms.date: 06/27/2018
ms.assetid: e7530857-c467-41ea-9730-84e6b1065a4d
ms.openlocfilehash: a0718463a36e1a3e1e312fbe0c0947e39648846d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468518"
---
# <a name="how-to-join-content-from-dissimilar-files-linq-visual-basic"></a>Nasıl yapılır: farklı dosyalardan Içerik ekleme (LINQ) (Visual Basic)

Bu örnek, eşleşen anahtar olarak kullanılan ortak bir değeri paylaşan, virgülle ayrılmış iki dosyadan verilerin nasıl birleştirileceğini gösterir. Bu teknik, iki elektronik tablodan veya bir elektronik tabloda ve başka bir biçime sahip bir dosyadan yeni bir dosyaya veri birleştirmek istiyorsanız yararlı olabilir. Örneği herhangi bir tür yapılandırılmış metinle çalışacak şekilde değiştirebilirsiniz.

## <a name="to-create-the-data-files"></a>Veri dosyalarını oluşturmak için

1. Aşağıdaki satırları scores.csv adlı bir dosyaya kopyalayın ve proje klasörünüze kaydedin. Dosya, elektronik tablo verilerini temsil eder. 1. sütun, öğrencinin KIMLIĞIDIR ve 2 ile 5 arasındaki sütunlar test puanlarıdır.

    ```csv
    111, 97, 92, 81, 60
    112, 75, 84, 91, 39
    113, 88, 94, 65, 91
    114, 97, 89, 85, 82
    115, 35, 72, 91, 70
    116, 99, 86, 90, 94
    117, 93, 92, 80, 87
    118, 92, 90, 83, 78
    119, 68, 79, 88, 92
    120, 99, 82, 81, 79
    121, 96, 85, 91, 60
    122, 94, 92, 91, 91
    ```

2. Aşağıdaki satırları names.csv adlı bir dosyaya kopyalayın ve proje klasörünüze kaydedin. Dosya, öğrencinin Soyadı, adı ve öğrenci KIMLIĞINI içeren bir elektronik tabloyu temsil eder.

    ```csv
    Omelchenko,Svetlana,111
    O'Donnell,Claire,112
    Mortensen,Sven,113
    Garcia,Cesar,114
    Garcia,Debra,115
    Fakhouri,Fadi,116
    Feng,Hanying,117
    Garcia,Hugo,118
    Tucker,Lance,119
    Adams,Terry,120
    Zabokritski,Eugene,121
    Tucker,Michael,122
    ```

## <a name="example"></a>Örnek

```vb
Imports System.Collections.Generic
Imports System.Linq

Class JoinStrings

    Shared Sub Main()

        ' Join content from spreadsheet files that contain
        ' related information. names.csv contains the student name
        ' plus an ID number. scores.csv contains the ID and a
        ' set of four test scores. The following query joins
        ' the scores to the student names by using ID as a
        ' matching key.

        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' Name:    Last[0],       First[1],  ID[2],     Grade Level[3]
        '          Omelchenko,    Svetlana,  111,       2
        ' Score:   StudentID[0],  Exam1[1]   Exam2[2],  Exam3[3],  Exam4[4]
        '          111,           97,        92,        81,        60

        ' This query joins two dissimilar spreadsheets based on common ID value.
        ' Multiple from clauses are used instead of a join clause
        ' in order to store results of id.Split.
        Dim scoreQuery1 = From name In names
                         Let n = name.Split(New Char() {","})
                            From id In scores
                            Let n2 = id.Split(New Char() {","})
                            Where Convert.ToInt32(n(2)) = Convert.ToInt32(n2(0))
                            Select n(0) & "," & n2(1) & "," & n2(2) & "," & n2(3) & "," &  n2(4)

        ' Pass a query variable to a Sub and execute it there.
        ' The query itself is unchanged.
        OutputQueryResults(scoreQuery1, "Merge two spreadsheets:")

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

    Shared Sub OutputQueryResults(ByVal query As IEnumerable(Of String), ByVal message As String)

        Console.WriteLine(System.Environment.NewLine & message)
        For Each item As String In query
            Console.WriteLine(item)
        Next
        Console.WriteLine(query.Count & " total names in list")

    End Sub
End Class
' Output:
' Merge two spreadsheets:
' Omelchenko, 97, 92, 81, 60
' O'Donnell, 75, 84, 91, 39
' Mortensen, 88, 94, 65, 91
' Garcia, 97, 89, 85, 82
' Garcia, 35, 72, 91, 70
' Fakhouri, 99, 86, 90, 94
' Feng, 93, 92, 80, 87
' Garcia, 92, 90, 83, 78
' Tucker, 68, 79, 88, 92
' Adams, 99, 82, 81, 79
' Zabokritski, 96, 85, 91, 60
' Tucker, 94, 92, 91, 91
' 12 total names in list
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](linq-and-strings.md)
- [LINQ ve dosya dizinleri (Visual Basic)](linq-and-file-directories.md)
