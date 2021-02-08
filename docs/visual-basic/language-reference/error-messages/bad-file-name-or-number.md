---
description: 'Daha fazla bilgi edinin: Hatalı dosya adı veya numarası'
title: Hatalı dosya adı veya numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 6e568a721fb3606c5b4bc046041c9d6f24b6d126
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797074"
---
# <a name="bad-file-name-or-number"></a>Hatalı dosya adı veya numarası

Belirtilen dosyaya erişmeye çalışırken bir hata oluştu. Bu hatanın olası nedenleri arasında aşağıdakiler bulunur:  
  
- Bir ifade, içinde belirtilmeyen `FileOpen` veya bir `FileOpen` ifadede belirtilen ancak daha sonra kapatılan bir dosya adı veya numarası olan bir dosyaya başvurur.  
  
- Bir ifade, dosya numarası aralığının dışında bir sayı içeren bir dosyaya başvurur.  
  
- Bir ifade, geçerli olmayan bir dosya adı veya sayı anlamına gelir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Dosya adının bir bildirimde belirtildiğinden emin olun `FileOpen` . `FileClose`Deyiminizi bağımsız değişkenler olmadan çağırdıysanız, tüm açık dosyaları yanlışlıkla kapattığını unutmayın.  
  
2. Kodunuz algorithmically dosya numaralarını üretiyorsa, sayıların geçerli olduğundan emin olun.  
  
3. İşletim sistemi kurallarına uyduğundan emin olmak için dosya adlarını denetleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Visual Basic Adlandırma Kuralları](../../programming-guide/program-structure/naming-conventions.md)
