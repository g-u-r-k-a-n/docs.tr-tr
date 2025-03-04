---
title: 'İçeri Aktarma Bildirimleri: open Anahtar Sözcüğü'
description: 'F # içeri aktarma bildirimleri hakkında bilgi edinin ve öğelerin tam nitelikli bir ad kullanmadan başvurdukları bir modül veya ad alanı belirtmeleri hakkında bilgi edinin.'
ms.date: 08/15/2020
ms.openlocfilehash: 4d3fd159aa4b334e9db0d7f756047470ad9c0829
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739691"
---
# <a name="import-declarations-the-open-keyword"></a>İçeri aktarma bildirimleri: `open` anahtar sözcüğü

*İçeri aktarma bildirimi* , öğelerini tam nitelikli bir ad kullanmadan başvuralabileceğiniz bir modül veya ad alanını belirtir.

## <a name="syntax"></a>Syntax

```fsharp
open module-or-namespace-name
open type type-name
```

## <a name="remarks"></a>Açıklamalar

Her seferinde tam nitelikli ad alanı veya modül yolunu kullanarak koda başvurmak, yazmak, okumak ve sürdürmek zor olan kod oluşturabilir. Bunun yerine `open` sık kullanılan modüller ve ad alanları için anahtar sözcüğünü kullanarak bu modülün veya ad alanının bir üyesine başvurduğunuzda, tam ad yerine adın kısa formunu kullanabilirsiniz. Bu anahtar sözcük `using` , `using namespace` Visual C++ ve Visual Basic içindeki C# anahtar sözcüğüne benzerdir `Imports` .

Belirtilen modül veya ad alanı aynı projede veya başvurulan bir proje ya da derlemede olmalıdır. Yoksa, projeye bir başvuru ekleyebilir veya `-reference` komut satırı seçeneğini (ya da kısaltmasının `-r` ) kullanabilirsiniz. Daha fazla bilgi için bkz. [derleyici seçenekleri](compiler-options.md).

İçeri aktarma bildirimi, kapsayan ad alanı, modül veya dosyanın sonuna kadar, bildirimi izleyen koddaki adları kullanılabilir hale getirir.

Çoklu içeri aktarma bildirimleri kullandığınızda, bunlar ayrı satırlarda görünmelidir.

Aşağıdaki kod, `open` kodu basitleştirmek için anahtar sözcüğünün kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

Aynı ad birden fazla açık modülde veya ad alanında gerçekleştiğinde, F # derleyicisi bir hata veya uyarı göstermez. Belirsizlikleri gerçekleştiğinde, F # daha yeni açılan modüle veya ad alanına tercih verir. Örneğin, aşağıdaki kodda hem hem de `empty` `Seq.empty` `empty` `List` modüllerinde bulunur `Seq` .

```fsharp
open List
open Seq
printfn %"{empty}"
```

Bu nedenle, ya da gibi özdeş adlara sahip üyeler içeren veya gibi modülleri veya ad alanlarını açtığınızda dikkatli olun `List` `Seq` ; bunun yerine nitelikli adları kullanmayı göz önünde bulundurun. Kodun içeri aktarma bildirimlerinin sırasına bağlı olduğu herhangi bir durumu kullanmaktan kaçının.

## <a name="open-type-declarations"></a>Açık tür bildirimleri

F # `open` şöyle bir türde destekler:

```fsharp
open type System.Math
PI
```

Bu, türdeki tüm erişilebilir statik alanları ve üyeleri kullanıma sunar.

`open`Statik üyeleri açığa çıkarmak için F # tanımlı [kaydı](records.md) ve [ayrılmış birleşim](discriminated-unions.md) türlerini de kullanabilirsiniz. Ayırt edici birleşimler söz konusu olduğunda, birleşim durumlarını da kullanıma sunabilirsiniz. Bu işlem, açmak istemediğiniz bir modülün içinde bildirildiği bir türdeki birleşim çalışmalarına erişmek için yararlı olabilir, örneğin:

```fsharp
module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

## <a name="namespaces-that-are-open-by-default"></a>Varsayılan olarak açık olan ad alanları

Bazı ad alanları, F # kodunda açık bir içeri aktarma bildirimine gerek kalmadan örtük olarak açıldıkları sıklıkla kullanılır. Aşağıdaki tabloda varsayılan olarak açık olan ad alanları gösterilmektedir.

|Ad Alanı|Açıklama|
|---------|-----------|
|`FSharp.Core`|Ve gibi yerleşik türler için temel F # tür tanımlarını içerir `int` `float` .|
|`FSharp.Core.Operators`|Ve gibi temel aritmetik işlemleri içerir `+` `*` .|
|`FSharp.Collections`|Ve gibi sabit koleksiyon sınıflarını içerir `List` `Array` .|
|`FSharp.Control`|Yavaş değerlendirme ve zaman uyumsuz iş akışları gibi denetim yapıları için türler içerir.|
|`FSharp.Text`|İşlev gibi, biçimlendirilen GÇ işlevleri içerir `printf` .|

## <a name="autoopen-attribute"></a>Oto aç özniteliği

`AutoOpen`Derlemeye başvuruluyorsa bir ad alanını veya modülü otomatik olarak açmak istiyorsanız, özniteliği bir derlemeye uygulayabilirsiniz. `AutoOpen`Üst modül veya ad alanı açıldığında bu modülü otomatik olarak açmak için bir modüle özniteliği de uygulayabilirsiniz. Daha fazla bilgi için bkz. [oto Openattribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html).

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess özniteliği

Bazı modüller, kayıtlar veya birleşim türleri `RequireQualifiedAccess` özniteliği belirtebilir. Bu modüllerin, kayıtların veya birleşimlerin öğelerine başvurduğunuzda, bir içeri aktarma bildirimi eklenip eklenmeyeceğini fark etmeksizin nitelikli bir ad kullanmanız gerekir. Bu özniteliği yaygın olarak kullanılan adları tanımlayan türler üzerinde stratejik olarak kullanırsanız, ad çakışmalarını önlemeyi ve bu sayede kodu kitaplıklarda değişikliklere daha dayanıklı hale getirmenize yardımcı olursunuz. Daha fazla bilgi için bkz. [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html).

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [Ad alanları](namespaces.md)
- [Modül](modules.md)
