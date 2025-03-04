---
description: Hakkında daha fazla bilgi edinin:-Reference (Visual Basic)
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: e84cdf447294a299c26a775327528a94ebba03da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474154"
---
# <a name="-reference-visual-basic"></a>-başvuru (Visual Basic)

Derleyicinin, belirtilen derlemelerde bulunan tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-reference:fileList  
```

veya

```console
-r:fileList  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`fileList`|Gereklidir. Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  

 İçeri aktardığınız dosya (ler) bütünleştirilmiş kod meta verisi içermelidir. Yalnızca ortak türler derleme dışında görünür. [-Addmodule](addmodule.md) seçeneği bir modülden meta verileri içeri aktarır.  
  
 Kendisi başka bir derlemeye (derleme B) başvuran bir derlemeye (derleme A) başvuruyorsa, şu durumlarda derleme B 'ye başvurmanız gerekir:  
  
- Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.  
  
- B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.  
  
 Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-libpath](libpath.md) kullanın.  
  
 Derleyicinin bir derlemede (modül değil) bir türü tanıması için, türün çözümlenmesinin zorunlu olması gerekir. Bunu nasıl yapabileceğiniz bir örnek, türün bir örneğini tanımlamaktır. Derleyici için bir derlemede tür adlarını çözümlemek için diğer yollar mevcuttur. Örneğin, derlemedeki bir türden devralma yaparsanız, tür adı derleyici tarafından bilinmiş olur.  
  
 Yaygın olarak kullanılan .NET Framework derlemelerine başvuran Vbc. rsp yanıt dosyası varsayılan olarak kullanılır. `-noconfig`Derleyicinin Vbc. rsp kullanmasını istemiyorsanız kullanın.  
  
 Öğesinin kısa biçimi `-reference` `-r` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki komut, kaynak dosya `Input.vb` ve başvuru derlemelerini ' den `Metad1.dll` ve `Metad2.dll` üretilecek şekilde derler `Out.exe` .  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [-noconfig](noconfig.md)
- [-target (Visual Basic)](target.md)
- [Genel](../../language-reference/modifiers/public.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
