---
description: Daha fazla bilgi edinin:-doc
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: da1ff6ad133dd2f46484b61ff73e1c6159eae557
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461430"
---
# <a name="-doc"></a>-doc

Belge açıklamalarını bir XML dosyasına işler.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-doc[+ | -]  
```

veya  

```console
-doc:file  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. Yalnızca + veya belirtildiğinde `-doc` , derleyicinin belge bilgilerini oluşturmasına ve BIR XML dosyasına yerleştirmesine neden olur. Belirtildiğinde `-` `-doc` , hiçbir belge bilgisinin oluşturulmamasına neden olmayan bir değer belirtilmiyor.|  
|`file`|Kullanılıyorsa gereklidir `-doc:` . Derlemenin kaynak kodu dosyalarındaki yorumlarla doldurulan çıkış XML dosyasını belirtir. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  

 `-doc`Seçeneği, derleyicinin belge açıklamalarını içeren BIR XML dosyası oluşturup üretmediğini denetler. `-doc:file`Söz dizimini kullanırsanız `file` PARAMETRESI, XML dosyasının adını belirtir. `-doc`Veya kullanıyorsanız `-doc+` , derleyici XML dosya adını derleyicinin oluşturmakta olduğu yürütülebilir dosya veya kitaplıktan alır. `-doc-`Seçeneğini kullanırsanız veya belirtmezseniz `-doc` , DERLEYICI bir XML dosyası oluşturmaz.  
  
 Kaynak kodu dosyalarında, belge açıklamaları aşağıdaki tanımlardan önce olabilir:  
  
- Bir [sınıf](../../language-reference/statements/class-statement.md) veya [arabirim](../../language-reference/statements/interface-statement.md) gibi Kullanıcı tanımlı türler  
  
- Alan, [olay](../../language-reference/statements/event-statement.md), [özellik](../../language-reference/statements/property-statement.md), [işlev](../../language-reference/statements/function-statement.md)veya alt [yordam](../../language-reference/statements/sub-statement.md)gibi Üyeler.  
  
 Oluşturulan XML dosyasını Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) özelliğiyle birlikte kullanmak IÇIN, XML dosyasının dosya adının desteklemek istediğiniz derlemeyle aynı olmasına izin verin. XML dosyasının derlemeyle aynı dizinde olduğundan emin olun; böylece derlemeye Visual Studio projesinde başvuruluyorsa,. xml dosyası da bulunur. IntelliSense 'in bir proje içinde veya bir proje tarafından başvurulan projelerde kod için çalışması için XML belge dosyaları gerekli değildir.  
  
 İle derleme yapmadığınız takdirde `-target:module` , XML dosyası etiketleri içerir `<assembly></assembly>` . Bu Etiketler, derlemenin çıkış dosyası için derleme bildirimini içeren dosyanın adını belirtir.  
  
 Kodunuzda açıklamalardan belge oluşturma yolları için bkz. [XML açıklama etiketleri](../../language-reference/xmldoc/index.md) .  
  
|Visual Studio tümleşik geliştirme ortamında belge ayarlamak için|  
|---|  
|1. **Çözüm Gezgini** bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Derle** sekmesine tıklayın.<br />3. **XML belgesi oluştur dosyası** kutusunda değeri ayarlayın.|  
  
## <a name="example"></a>Örnek  

 Bkz. bir örnek için [kodunuzu XML Ile belgeleme](../../programming-guide/program-structure/documenting-your-code-with-xml.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [XML ile Kodunuzu Belgeleme](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
