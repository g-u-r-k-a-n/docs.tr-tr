---
description: 'Daha fazla bilgi edinin: sorun giderme: metin dosyalarını okuma ve yazma (Visual Basic)'
title: 'Sorun giderme: metin dosyalarını okuma ve yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: 1c01f7673ef021759a9c1892f685aa90ef1acdf6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675344"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Sorun giderme: metin dosyalarını okuma ve yazma (Visual Basic)

Bu konuda, metin dosyalarıyla çalışırken karşılaşılan yaygın sorunlar ele alınmaktadır ve her birine bir yaklaşım önerisinde bulunur.  
  
## <a name="common-problems"></a>Sık karşılaşılan sorunlar  

 Metin dosyalarıyla çalışırken karşılaşılan en yaygın sorunlar, güvenlik özel durumları, dosya kodlamaları veya geçersiz yollar içerir.  
  
### <a name="security-exceptions"></a>Güvenlik özel durumları  

 Bir <xref:System.Security.SecurityException> güvenlik hatası oluştuğunda oluşturulur. Bu genellikle kullanıcının gerekli izinlere sahip olmadığı bir sonucudur. Bu, izinleri ekleyerek veya yalıtılmış depolamada dosyalarla çalışarak çözülebilen bir sonucudur.  
  
### <a name="file-encodings"></a>Dosya kodlamaları  

 Karakter kodlamaları olarak da bilinen dosya kodlamaları, metin işleme sırasında karakterlerin nasıl temsil edileceğini belirtir. Metin dosyasında beklenmeyen karakterler yanlış kodlamadan kaynaklanıyor olabilir. Çoğu dosya için, tek bir kodlama bir veya işleyemeyen dil karakterleri açısından tercih edilebilir, ancak UNICODE genellikle tercih edilir. Daha fazla bilgi için bkz. [dosya kodlamaları](file-encodings.md) ve <xref:System.Text.Encoding> .  
  
### <a name="incorrect-paths"></a>Yanlış yollar  

 Dosya yollarını ayrıştırırken özellikle göreli yollar, yanlış verileri sağlamak kolaydır. Doğru yolu belirttiğinizden emin olmak için birçok sorun düzeltilebilir. Daha fazla bilgi için bkz. [nasıl yapılır: dosya yollarını ayrıştırma](how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Dosyalardan Okuma](reading-from-files.md)
- [Dosyalara Yazma](writing-to-files.md)
- [TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma](parsing-text-files-with-the-textfieldparser-object.md)
