---
description: :-Moduleassemblyname hakkında daha fazla bilgi edinin
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 1b5daac8fea264e86b7200f3cead4cb657641000
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434322"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname

Bu modülün bir parçası olacağı derlemenin adını belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`assembly_name`|Bu modülün bir parçası olacağı derlemenin adı.|  
  
## <a name="remarks"></a>Açıklamalar  

 Derleyici, `-moduleassemblyname` seçeneği yalnızca `-target:module` seçenek belirtilmişse işler. Bu, derleyicinin bir modül oluşturmasına neden olur. Derleyici tarafından oluşturulan modül yalnızca seçeneğiyle belirtilen derleme için geçerlidir `-moduleassemblyname` . Modülü farklı bir derlemeye yerleştirirseniz, çalışma zamanı hataları oluşur.  
  
 `-moduleassemblyname`Seçeneği yalnızca aşağıdakilerin doğru olması durumunda gereklidir:  
  
- Modüldeki bir veri türünün başvurulan derlemedeki bir türe erişmesi gerekir `Friend` .  
  
- Başvurulan derleme, modülün derleyecek olduğu derlemeye arkadaş bütünleştirilmiş kodu erişimi verdi.  
  
 Modül oluşturma hakkında daha fazla bilgi için bkz. [-target (Visual Basic)](target.md). Arkadaş derlemeleri hakkında daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).  
  
> [!NOTE]
> `-moduleassemblyname`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca bir komut isteminden derlerken kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: çok dosyalı bütünleştirilmiş kod derleme](../../../framework/app-domains/build-multifile-assembly.md)
- [Visual Basic Command-Line derleyicisi](index.md)
- [-target (Visual Basic)](target.md)
- [-Main](main.md)
- [-başvuru (Visual Basic)](reference.md)
- [-addmodule](addmodule.md)
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [Arkadaş derlemeleri](../../../standard/assembly/friend.md)
