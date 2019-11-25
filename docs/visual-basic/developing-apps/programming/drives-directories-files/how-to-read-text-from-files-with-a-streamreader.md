---
title: 'Nasıl Yapılır: StreamReader Olan Dosyalardaki Metni Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 572463d1f03d768fb133f2dac59b012051f053bb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334557"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Nasıl Yapılır: StreamReader Olan Dosyalardaki Metni Okuma (Visual Basic)

The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>. These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>To read a line from a file with a text reader  
  
- Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file. This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 The file that is read must be a text file.  
  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. For example, the file Form1.vb may not be a Visual Basic source file.  
  
 Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class. If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges. For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md). The user also needs access to the file. For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [SaveFileDialog Bileşeni](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
