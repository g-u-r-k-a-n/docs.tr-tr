---
title: 'Derleme bildirimi oluşturulurken hata oldu: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: e90ad1905123a3c5426ada15e21179abe5c078ab
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874401"
---
# <a name="error-creating-assembly-manifest-error-message"></a>Derleme bildirimi oluşturulurken hata oldu: \<error message>

Visual Basic derleyici, bildirime sahip bir derleme oluşturmak için derleme bağlayıcı (Al.exe, Alink olarak da bilinir) çağırır. Bağlayıcı, derlemeyi oluşturmak için önceden egörev aşamasında bir hata bildirdi.  
  
 Anahtar dosyası veya belirtilen anahtar kapsayıcısı ile ilgili sorunlar varsa bu durum oluşabilir. Bir derlemeyi tamamen imzalamak için ortak ve özel anahtarlarla ilgili bilgileri içeren geçerli bir anahtar dosyası sağlamanız gerekir. Bir derlemeyi imzalamayı geciktirmek için **yalnızca gecikmeli imzala** onay kutusunu seçmeniz ve ortak anahtar bilgileri hakkında bilgi içeren geçerli bir anahtar dosyası sağlamanız gerekir. Bir derleme Gecikmeli imzalanmışsa özel anahtar gerekli değildir. Daha fazla bilgi için bkz. [nasıl yapılır: derlemeyi güçlü bir adla imzalama](../../../standard/assembly/sign-strong-name.md).  
  
 **Hata kimliği:** BC30140  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Alıntı yapılan hata iletisini inceleyin ve [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)konusuna başvurun. hata AL1019 daha fazla açıklama ve öneri  
  
2. Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama](../../../standard/assembly/sign-strong-name.md)
- [İmzalama Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/signing-page-project-designer)
- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Bizimle iletişime geçin](/visualstudio/ide/feedback-options)
