---
title: Kaynak Office Open XML Belgesi Oluşturma
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 9f44c8d0f4080224c461736fdbdf3acd854e4a89
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410844"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Kaynak Office Open XML belgesi (Visual Basic) oluşturuluyor
Bu konu başlığında, bu öğreticideki diğer örneklerin kullandığı Office Open XML WordprocessingML belgesinin nasıl oluşturulacağı gösterilmektedir. Bu yönergeleri izlerseniz, çıktılarınız her örnekte girilen çıktıyla eşleşir.  
  
 Ancak, bu öğreticideki örnekler geçerli bir WordprocessingML belgesiyle çalışacaktır.  
  
 Bu öğreticinin kullandığı belgeyi oluşturmak için Microsoft Office 2007 veya sonraki bir sürümü yüklemiş olmanız ya da Word, Excel ve PowerPoint 2007 dosya biçimleri için Microsoft Office Uyumluluk Paketi ile Microsoft Office 2003 olmalıdır.  
  
## <a name="creating-the-wordprocessingml-document"></a>WordprocessingML belgesi oluşturma  
  
#### <a name="to-create-the-wordprocessingml-document"></a>WordprocessingML belgesi oluşturmak için  
  
1. Yeni bir Microsoft Word belgesi oluşturun.  
  
2. Aşağıdaki metni yeni belgeye yapıştırın:  
  
    ```text  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3. İlk satırı "Başlık 1" stiliyle biçimlendirin.  
  
4. Visual Basic kodunu içeren satırları seçin. İlk satır `Imports` anahtar sözcüğüyle başlar. Son satır "End Class" dır. Çizgileri Courier yazı tipiyle biçimlendirin. Bunları yeni bir stille biçimlendirin ve yeni "Code" stilini adlandırın.  
  
5. Son olarak, çıktıyı içeren satırın tamamını seçin ve `Code` stille biçimlendirin.  
  
6. Belgeyi kaydedin ve SampleDoc. docx olarak adlandırın.  
  
    > [!NOTE]
    > Microsoft Word 2003 kullanıyorsanız, **farklı kaydet türü** açılan listesinde **Word 2007 belgesi** ' ni seçin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: WordprocessingML belgesindeki Içeriği düzenleme (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
