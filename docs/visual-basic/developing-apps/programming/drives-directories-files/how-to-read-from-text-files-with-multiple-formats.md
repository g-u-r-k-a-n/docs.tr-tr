---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic birden çok biçimdeki fext dosyalarından okuma'
title: 'Nasıl yapılır: birden çok biçimdeki metin dosyalarından okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: 90d981ad051fb395d57604434cf9ba6b74603e7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797451"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a>Nasıl yapılır: Visual Basic birden çok biçimdeki fext dosyalarından okuma

<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>Nesnesi, günlük gibi yapılandırılmış metin dosyalarını kolayca ve verimli bir şekilde ayrıştırabilmeniz için bir yol sağlar. `PeekChars`Dosya aracılığıyla ayrıştırdığınızda her satırın biçimini belirleyebilmek için yöntemini kullanarak birden çok biçimdeki bir dosyayı işleyebilirsiniz.
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>Birden çok biçimdeki bir metin dosyasını ayrıştırmak için

1. Projenize *testfile.txt* adlı bir metin dosyası ekleyin. Aşağıdaki içeriği metin dosyasına ekleyin:

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. Beklenen biçimi ve bir hata bildirildiğinde kullanılan biçimi tanımlayın. Her dizideki son giriş-1 ' dir, bu nedenle son alan, değişken genişliği olarak kabul edilir. Bu, dizideki son giriş 0 ' dan küçük veya buna eşit olduğunda gerçekleşir.

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>Genişliği ve biçimi tanımlayarak yeni bir nesne oluşturun.

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. Okumadan önce biçim için test eden satırlarda döngü yapın.

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. Konsola hataları yazın.

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a>Örnek

Aşağıda, dosyadan okuyan tüm örnek verilmiştir `testfile.txt` :

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a>Güçlü programlama

Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Satır belirtilen biçim () kullanılarak ayrıştırılamıyor <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> . Özel durum iletisi, özel duruma neden olan satırı belirtir, ancak <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> özellik satırda bulunan metne atanır.
- Belirtilen dosya yok ( <xref:System.IO.FileNotFoundException> ).
- Kullanıcının dosyaya erişmek için yeterli izinlere sahip olmadığı kısmi güven durumu. (<xref:System.Security.SecurityException>).
- Yol çok uzun ( <xref:System.IO.PathTooLongException> ).
- Kullanıcı, dosyaya () erişmek için yeterli izinlere sahip değil <xref:System.UnauthorizedAccessException> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [Nasıl yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma](how-to-read-from-comma-delimited-text-files.md)
- [Nasıl yapılır: Sabit Genişlikli Metin Dosyalarından Okuma](how-to-read-from-fixed-width-text-files.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](parsing-text-files-with-the-textfieldparser-object.md)
