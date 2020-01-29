---
title: RichTextBox denetimine dosya yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
ms.openlocfilehash: c31e004ea4cd0821b5f18f0ab0fe2708e6ac4b59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736291"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimine Dosyaları Yükleme

Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi düz metin, Unicode düz metin veya zengin metin biçimi (RTF) dosyası görüntüleyebilir. Bunu yapmak için <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemini çağırın. Bir akıştan veri yüklemek için <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemini de kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.

### <a name="to-load-a-file-into-the-richtextbox-control"></a>RichTextBox denetimine bir dosya yüklemek için

1. <xref:System.Windows.Forms.OpenFileDialog> bileşeni kullanılarak açılacak dosyanın yolunu saptayın. Genel bakış için bkz. [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).

2. Yüklenecek dosyayı ve isteğe bağlı olarak bir dosya türünü belirterek <xref:System.Windows.Forms.RichTextBox> denetiminin <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemini çağırın. Aşağıdaki örnekte, yüklenecek dosya <xref:System.Windows.Forms.OpenFileDialog> bileşenin <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliğinden alınır. Yöntemini tek bağımsız değişkeni olarak bir dosya adı ile çağırırsanız, dosya türünün RTF olacağı varsayılır. Başka bir dosya türü belirtmek için, ikinci bağımsız değişkeni olarak <xref:System.Windows.Forms.RichTextBoxStreamType> numaralandırması değeri ile yöntemini çağırın.

    Aşağıdaki örnekte, bir düğmeye tıklandığında <xref:System.Windows.Forms.OpenFileDialog> bileşeni gösterilir. Seçili dosya daha sonra açılır ve <xref:System.Windows.Forms.RichTextBox> denetiminde görüntülenir. Bu örnekte, bir formun bir düğme olduğunu varsayar`btnOpenFile`.

    ```vb
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _
       ByVal e As System.EventArgs) Handles btnOpenFile.Click
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _
              RichTextBoxStreamType.RichText)
          End If
    End Sub
    ```

    ```csharp
    private void btnOpenFile_Click(object sender, System.EventArgs e)
    {
       if(openFileDialog1.ShowDialog() == DialogResult.OK)
       {
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);
       }
    }
    ```

    ```cpp
    private:
       void btnOpenFile_Click(System::Object ^  sender,
          System::EventArgs ^  e)
       {
          if(openFileDialog1->ShowDialog() == DialogResult::OK)
          {
             richTextBox1->LoadFile(openFileDialog1->FileName,
                RichTextBoxStreamType::RichText);
          }
       }
    ```

    (Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.

    ```csharp
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);
    ```

    ```cpp
    this->btnOpenFile->Click += gcnew
       System::EventHandler(this, &Form1::btnOpenFile_Click);
    ```

    > [!IMPORTANT]
    > Bu işlemi çalıştırmak için, derlemeniz <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı tarafından verilen bir ayrıcalık düzeyi gerektirebilir. Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
