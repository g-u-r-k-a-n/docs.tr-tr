---
description: Daha fazla bilgi edinin:-belirleyici
title: -deterministic
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
ms.openlocfilehash: b339b76d4f95ba80f8e92c4961586fa390b0839a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461521"
---
# <a name="-deterministic"></a>-deterministic

Derleyicinin bayt çıkışı, aynı girişlerin derlemeleri arasında özdeş olan bir derleme üretmesine neden olur.

## <a name="syntax"></a>Syntax

```console
-deterministic
```

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak, belirli bir giriş kümesinden Derleyici çıktısı benzersizdir, çünkü derleyici bir zaman damgası ve rastgele sayıdan oluşturulan bir GUID ekliyor. `-deterministic`Değer aynı kaldığı sürece, bir *belirleyici derleme* oluşturmak için bu seçeneği kullanın.

Derleyici, belirlemeleri için aşağıdaki girişleri dikkate alır:

- Komut satırı parametrelerinin sırası.
- Derleyicinin. rsp yanıt dosyasının içeriği.
- Kullanılan derleyicinin kesin sürümü ve başvurulan derlemeleri.
- Geçerli dizin yolu.
- Açıkça derleyiciye doğrudan veya dolaylı olarak geçirilen tüm dosyaların ikili içeriği:
  - Kaynak dosyalar
  - Başvurulan derlemeler
  - Başvurulan modüller
  - Kaynaklar
  - Tanımlayıcı ad anahtar dosyası
  - @ Yanıt dosyaları
  - Çözümleyiciler
  - RuleSets
  - Çözümleyiciler tarafından kullanılabilecek ek dosyalar
- Geçerli kültür (tanılama ve özel durum iletilerinin oluşturulduğu dil için).
- Kodlama belirtilmemişse, varsayılan kodlama (veya geçerli kod sayfası).
- Derleyicinin arama yollarındaki dosyaların varlığı, var olmayan ve içeriği (örneğin, `-lib` veya ile `-recurse` ).
- Derleyicinin çalıştırıldığı CLR platformu.
- `%LIBPATH%`, Çözümleyici bağımlılığı yüklemeyi etkileyebilecek değeri.

Kaynaklar herkese açık olduğunda, bir ikilinin güvenilir bir kaynaktan derlenip derlenmediğini oluşturmak için belirleyici derleme kullanılabilir. Ayrıca, bir ikiliye yapılan değişikliklere bağımlı derleme adımlarının yürütülmesi gerekip gerekmediğini belirlemek için sürekli bir derleme sisteminde de yararlı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
