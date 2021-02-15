---
description: 'Hakkında daha fazla bilgi edinin: XML dosyası Işleme (Visual Basic)'
title: XML Dosyasını İşleme
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 2314e7dafbd747f9a19b73d06d71c73631e53861
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468401"
---
# <a name="processing-the-xml-file-visual-basic"></a>XML Dosyasını İşleme (Visual Basic)

Derleyici, kodunuzda belge oluşturmak için etiketlenmiş her yapı için bir KIMLIK dizesi oluşturur. (Kodunuzu etiketleme hakkında daha fazla bilgi için bkz. [XML açıklama etiketleri](../../language-reference/xmldoc/index.md).) KIMLIK dizesi yapıyı benzersiz bir şekilde tanımlar. XML dosyasını işleyen programlar, karşılık gelen .NET Framework meta veri/yansıma öğesini tanımlamak için KIMLIK dizesini kullanabilir.  
  
 XML dosyası, kodunuzun hiyerarşik bir temsili değildir; her öğe için oluşturulmuş KIMLIĞI olan düz bir liste.  
  
 Derleyici, KIMLIK dizelerini oluşturduğunda aşağıdaki kuralları sunar:  
  
- Dizeye boşluk yerleştirilmez.  
  
- KIMLIK dizesinin ilk bölümü, tanımlanmakta olan üyenin türünü tanımlar, tek bir karakter ve iki nokta üst üste gelir. Aşağıdaki üye türleri kullanılır.  
  
|Karakter|Açıklama|  
|---|---|  
|N|ad alanı<br /><br /> Bir ad alanına belge açıklamaları ekleyemezsiniz, ancak bu kişilere, desteklenmiş olduğu durumlarda bu başvuruları yapabilirsiniz.|  
|T|Tür: `Class` , `Module` ,,, `Interface` `Structure` `Enum` , `Delegate`|  
|F|alanla `Dim`|  
|P|Özellik: `Property` (varsayılan özellikler dahil)|  
|M|Yöntem: `Sub` , `Function` ,, `Declare``Operator`|  
|E|olay `Event`|  
|!|hata dizesi<br /><br /> Dizenin geri kalanı hata hakkında bilgi sağlar. Visual Basic Derleyicisi çözümlenemeyen bağlantılar için hata bilgileri oluşturur.|  
  
- Öğesinin ikinci bölümü, `String` ad alanının kökünden başlayarak öğenin tam nitelikli adıdır. Öğenin adı, kapsayan tür (ler) ve ad alanı noktalarla ayrılır. Öğenin adının kendisi noktalar içeriyorsa, bunlar sayı işaretiyle (#) değiştirilmiştir. Hiçbir öğenin doğrudan adında numara işareti olmadığı varsayılır. Örneğin, oluşturucunun tam adı `String` olacaktır `System.String.#ctor` .  
  
- Özellikler ve yöntemler için, yöntem için bağımsız değişkenler varsa, parantez içine alınmış bağımsız değişken listesi aşağıda verilmiştir. Bağımsız değişken yoksa, parantezler yok. Bağımsız değişkenler virgülle ayrılır. Her bağımsız değişkenin kodlaması, .NET Framework imzasında nasıl kodlandığını doğrudan izler.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, bir sınıfa ve üyelerine ait KIMLIK dizelerinin nasıl oluşturulduğunu gösterir.  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-doc](../../reference/command-line-compiler/doc.md)
- [Nasıl yapılır: XML Belgesi Oluşturma](how-to-create-xml-documentation.md)
