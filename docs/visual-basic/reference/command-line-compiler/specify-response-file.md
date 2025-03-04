---
description: 'Hakkında daha fazla bilgi edinin: @ (yanıt dosyası belirtme) (Visual Basic)'
title: '@ (Yanıt Dosyasını Belirtin)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 7a28be0d0bf6da177d9cfe85ecdb40eccf8a339f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473920"
---
# <a name="-specify-response-file-visual-basic"></a>@ (Yanıt Dosyası Belirtme) (Visual Basic)

Derlemek için derleyici seçeneklerini ve kaynak kodu dosyalarını içeren bir dosyayı belirtir.

## <a name="syntax"></a>Söz dizimi

```console
@response_file
```

## <a name="arguments"></a>Bağımsız değişkenler

`response_file`  
Gereklidir. Derlemek için derleyici seçeneklerini veya kaynak kodu dosyalarını listeleyen bir dosya. Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.

## <a name="remarks"></a>Açıklamalar

Derleyici, bir yanıt dosyasında belirtilen derleyici seçeneklerini ve kaynak kodu dosyalarını komut satırında belirtildikleri gibi işler.

Bir derlemede birden fazla yanıt dosyası belirtmek için, aşağıdaki gibi birden çok yanıt dosyası seçeneği belirtin.

```console
@file1.rsp @file2.rsp
```

Bir yanıt dosyasında, tek satırda birden çok derleyici seçeneği ve kaynak kodu dosyası görünebilir. Tek bir derleyici-seçenek belirtiminin tek bir satırda görünmesi gerekir (birden çok satıra yayılamaz). Yanıt dosyaları sembolle başlayan açıklamalara sahip olabilir `#` .

Komut satırında belirtilen seçenekleri, bir veya daha fazla yanıt dosyasında belirtilen seçeneklerle birleştirebilirsiniz. Derleyici, komut seçeneklerini kendileriyle karşılaştığı şekilde işler. Bu nedenle, komut satırı bağımsız değişkenleri yanıt dosyalarında daha önce listelenen seçenekleri geçersiz kılabilir. Buna karşılık, bir yanıt dosyasındaki seçenekler, önceden komut satırında veya diğer yanıt dosyalarında listelenen seçenekleri geçersiz kılar.

Visual Basic, Vbc.exe dosyası ile aynı dizinde bulunan Vbc. rsp dosyasını sağlar. Seçenek kullanılmamışsa, vbc. rsp dosyası varsayılan olarak dahil edilir `-noconfig` . Daha fazla bilgi için bkz. [-noconfig](noconfig.md).

> [!NOTE]
> `@`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki satırlar örnek bir yanıt dosyasından alınır.

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a>Örnek

Aşağıdaki örnek, `@` seçeneğinin adlı yanıt dosyası ile nasıl kullanılacağını gösterir `File1.rsp` .

```console
vbc @file1.rsp
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [-noconfig](noconfig.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
