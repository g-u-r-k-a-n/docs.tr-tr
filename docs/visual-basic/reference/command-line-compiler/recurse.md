---
description: Hakkında daha fazla bilgi edinin:-recurse
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 2c0f1788c3811e24e2d51ff30e4cb2842aa0bd7a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475883"
---
# <a name="-recurse"></a>-recurse

Belirtilen dizinin ya da proje dizininin tüm alt dizinlerindeki kaynak kodu dosyalarını derler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `dir`  
 İsteğe bağlı. Aramanın başlamasını istediğiniz dizin. Belirtilmemişse, arama proje dizininde başlar.  
  
 `file`  
 Gereklidir. Aranacak dosya (lar). Joker karakterlere izin verilir.  
  
## <a name="remarks"></a>Açıklamalar  

 Kullanarak proje dizinindeki tüm eşleşen dosyaları derlemek için dosya adında joker karakterler kullanabilirsiniz `-recurse` . Çıkış dosyası adı belirtilmemişse, derleyici, çıktı dosyasının adını işlenen ilk girdi dosyasında temel alır. Bu genellikle alfabetik olarak görüntülendiklerinde derlenen dosyalar listesindeki ilk dosyadır. Bu nedenle, seçeneğini kullanarak bir çıkış dosyası belirtmek en iyisidir `-out` .  
  
> [!NOTE]
> `-recurse`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki komut, geçerli dizindeki tüm Visual Basic dosyalarını derler.  
  
```console
vbc *.vb  
```  
  
 Aşağıdaki komut dizindeki tüm Visual Basic dosyalarını `Test\ABC` ve altındaki tüm dizinleri derler ve sonra üretir `Test.ABC.dll` .  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [-Out (Visual Basic)](out.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
