---
description: 'Hakkında daha fazla bilgi edinin: panodaki verileri depolama ve okuma (Visual Basic)'
title: Verileri Panoda Depolama ve Panodan Okuma
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 18cb66f6d8093757ce34ddb20659824787460920
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666348"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Verileri Panoda Depolama ve Panodan Okuma (Visual Basic)

Pano, metin ve görüntü gibi verileri depolamak için kullanılabilir. Pano tüm etkin süreçler tarafından paylaşıldığından, bunlar arasında veri aktarmak için kullanılabilir. `My.Computer.Clipboard`Nesnesi panoya kolayca erişmenizi ve bu panoyu okuyup yazmanızı sağlar.  
  
## <a name="reading-from-the-clipboard"></a>Panodan Okuma  

 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A>Panodaki metni okumak için yöntemini kullanın. Aşağıdaki kod, metni okur ve bir ileti kutusunda görüntüler. Örneğin doğru şekilde çalışması için Panoda depolanan metin olmalıdır.  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **pano > Windows Forms uygulamalarda** bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A>Panodan bir görüntü almak için yöntemini kullanın. Bu örnek, yüklemeden önce panoda bir resim olup olmadığını ve üzerine atamayı denetler `PictureBox1` .  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **pano > Windows Forms uygulamalarda** bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
 Pano 'ya yerleştirilmiş öğeler, uygulama kapatıldıktan sonra bile kalır.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Panoda depolanan dosya türünü belirleme  

 Panodaki veriler metin, ses dosyası veya görüntü gibi çeşitli biçimlerde olabilir. Panodaki dosya sıralamasını belirlemek için,, ve gibi yöntemleri kullanabilirsiniz <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A> <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A> <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A> <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A> . <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A>Denetlemek istediğiniz özel bir biçim varsa yöntemi kullanılabilir.  
  
 `ContainsImage`Panoda bulunan verilerin bir görüntü olup olmadığını anlamak için işlevini kullanın. Aşağıdaki kod, verilerin bir görüntü ve raporların uygun olup olmadığını denetler.  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a>Panoyu Temizleme  

 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A>Yöntemi panoyu temizler. Pano başka süreçler tarafından paylaşıldığından, temizleme işlemi bu işlemlere etkisi olabilir.  
  
 Aşağıdaki kod yönteminin nasıl kullanılacağını gösterir `Clear` .  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a>Panoya yazma  

 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A>Panoya metin yazmak için yöntemini kullanın. Aşağıdaki kod, panoya "This bir test dizesidir" dizesini yazar.  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 `SetText`Yöntemi, türü içeren bir biçim parametresini kabul edebilir <xref:System.Windows.Forms.TextDataFormat> . Aşağıdaki kod, "Bu bir test dizesi" dizesini RTF metni olarak panoya yazar.  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A>Verileri panoya yazmak için yöntemini kullanın. Bu örnek, öğesini `DataObject` `dataChunk` panoya özel biçimde yazar `specialFormat` .  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 Pano 'ya <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> ses verileri yazmak için yöntemini kullanın. Bu örnek, Byte dizisini oluşturur `musicReader` , dosyayı onunla okur `cool.wav` ve panoya yazar.  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> Panoya diğer kullanıcılar tarafından erişilebildiğinden, parola veya gizli veriler gibi hassas bilgileri depolamak için bu uygulamayı kullanmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [Nasıl yapılır: bir XML dosyasından nesne verilerini okuma](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Nasıl yapılır: nesne verilerini bir XML dosyasına yazma](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
