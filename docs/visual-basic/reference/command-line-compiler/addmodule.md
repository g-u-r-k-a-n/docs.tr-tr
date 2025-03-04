---
description: :-AddModule hakkında daha fazla bilgi edinin
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: ca08aa599003897e680240af21c4a0eb568e31d8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468297"
---
# <a name="-addmodule"></a>-addmodule

Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `fileList`  
 Gereklidir. Meta veri içeren ancak derleme bildirimleri içermeyen dosyaların virgülle ayrılmış listesi. Boşluk içeren dosya adları tırnak işaretleri ("") içine alınmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  

 Parametresi tarafından listelenen dosyaların `fileList` `-target:module` seçeneğiyle oluşturulması veya başka bir derleyicinin eşdeğeri olması gerekir `-target:module` .  
  
 İle eklenen tüm modüller `-addmodule` , çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır. Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modülün çalışma zamanında uygulama dizininde olması gerekir. Aksi takdirde bir <xref:System.TypeLoadException> hata alırsınız.  
  
 İle dışında herhangi bir[hedef Visual Basic (](target.md) örtük veya açık) herhangi bir seçeneği belirtirseniz, bu `-target:module` `-addmodule` Dosya `-addmodule` projenin derlemesinin bir parçası haline gelir. Bir veya daha fazla dosya eklenmiş bir çıkış dosyası çalıştırmak için bütünleştirilmiş kod gereklidir `-addmodule` .  
  
 Derleme içeren bir dosyadan meta verileri içeri aktarmak için [-Reference (Visual Basic)](reference.md) kullanın.  
  
> [!NOTE]
> `-addmodule`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod bir modül oluşturur.  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 Aşağıdaki kod modülün türlerini içeri aktarır.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 Çalıştırdığınızda `t1` , çıkış çıkışları `802` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [-target (Visual Basic)](target.md)
- [-başvuru (Visual Basic)](reference.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
