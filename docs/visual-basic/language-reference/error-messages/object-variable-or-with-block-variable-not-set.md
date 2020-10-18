---
title: Nesne değişkeni veya With bloğu değişkeni ayarlanmamış
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 5eff7622ce2a35cf2846c5141cede98ea033d708
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159891"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Nesne değişkeni veya With bloğu değişkeni ayarlanmamış

Geçersiz bir nesne değişkenine başvuruluyor. Bu hata, birkaç nedenden dolayı oluşabilir:

- Bir değişken, bir tür belirtilmeden bildirildi. Bir değişken bir tür belirtilmeden bildirilirse, varsayılan olarak yazın `Object` .

    Örneğin, ile tanımlanan bir değişken, `Dim x` `Object;` ile tanımlanan bir değişken türünde olacaktır `Dim x As String` `String` .

    > [!TIP]
    > `Option Strict`İfade, bir tür ile sonuçlanan örtük yazmaya izin vermez `Object` . Türü atlarsanız, bir derleme zamanı hatası oluşur. Bkz. [Option Strict deyimdir](../statements/option-strict-statement.md).

- Olarak ayarlanmış bir nesneye başvurmaya çalışıyorsunuz `Nothing` .

- Düzgün şekilde bildirilmeyen bir dizi değişkeninin öğesine erişmeye çalışıyorsunuz.

    Örneğin, `products() As String` dizi öğesine başvuru yapmayı denerseniz, olarak tanımlanan bir dizi hatayı tetikler `products(3) = "Widget"` . Dizide hiç öğe yok ve bir nesne olarak değerlendirildi.

- Blok başlatılmadan önce bir blok içindeki koda erişmeye çalışıyorsunuz `With...End With` .   Bir `With...End With` blok, `With` ifade giriş noktası yürütülerek başlatılmalıdır.

> [!NOTE]
> Visual Basic veya VBA 'nın önceki sürümlerinde bu hata, anahtar sözcüğü kullanılmadan bir değişkene bir değer atanarak da tetikleniyor `Set` ( `x = "name"` yerine `Set x = "name"` ). `Set`Anahtar sözcüğü artık Visual Basic .NET içinde geçerli değildir.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. `Option Strict` `On` Aşağıdaki kodu dosyanın başlangıcına ekleyerek olarak ayarlayın:

    ```vb
    Option Strict On
    ```

    Projeyi çalıştırdığınızda, bir tür olmadan belirtilen herhangi bir değişken için **hata listesi** bir derleyici hatası görüntülenir.

2. Etkinleştirmek istemiyorsanız `Option Strict` , kodunuzda bir tür olmadan belirtilen herhangi bir değişken ( `Dim x` yerine `Dim x As String` ) arayın ve hedeflenen türü bildirime ekleyin.

3. Olarak ayarlanmış bir nesne değişkenine başvurmadığından emin olun `Nothing` .  Anahtar sözcüğü için kodunuzda arama `Nothing` yapın ve bu nesnenin, başvurulduktan sonra olarak ayarlanmaması için kodunuzu düzeltin `Nothing` .

4. Herhangi bir dizi değişkeninin, erişmeden önce boyutlanır olduğundan emin olun. İlk olarak diziyi oluştururken bir boyut atayabilir ( `Dim x(5) As String` yerine `Dim x() As String` ) veya `ReDim` ilk kez erişmeden önce dizinin boyutlarını ayarlamak için anahtar sözcüğünü kullanabilirsiniz.

5. `With`Deyiminizin giriş noktasını yürüterek blobunun başlatıldığından emin olun `With` .

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişken Bildirimi](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim Deyimi](../statements/redim-statement.md)
- [With...End With Deyimi](../statements/with-end-with-statement.md)
