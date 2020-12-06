---
title: Fixed anahtar sözcüğü
description: "F # ' fixed ' anahtar sözcüğüyle toplamayı engellemek için yerel olarak yığına nasıl ' sabitleyebileceğinizi öğrenin."
ms.date: 08/15/2020
ms.openlocfilehash: b4b0d1ae101d5f7b65bff80fa070c9fd54de8d66
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740360"
---
# <a name="the-fixed-keyword"></a>Fixed anahtar sözcüğü

`fixed`Anahtar sözcüğü, atık toplama sırasında toplanmasını veya taşınmasını engellemek için yerel olarak yığına "sabitlemenizi" sağlar.  Alt düzey programlama senaryolarında kullanılır.

## <a name="syntax"></a>Syntax

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Açıklamalar

Bu, bir işaretçinin ayıklanmasına izin vermek ve atık toplama sırasında toplanmasının veya taşınmasını önleyen bir ada bağlamak için ifadelerin sözdizimini genişletir.  

Bir ifadeden bir işaretçi, anahtar sözcüğü aracılığıyla `fixed` bir tanımlayıcıya bağlanır `use` .  Bunun semantiği, anahtar sözcüğü aracılığıyla kaynak yönetimine benzerdir `use` .  İşaretçi kapsamdayken sabitlenmiştir ve kapsam dışına alındıktan sonra artık sabit değildir.  `fixed` bağlama bağlamı dışında kullanılamaz `use` .  İşaretçiyi ile bir ada bağlamanız gerekir `use` .

Öğesinin kullanımı, `fixed` bir işlev veya metot içindeki bir ifadede gerçekleşmelidir.  Betik düzeyinde veya modül düzeyinde bir kapsamda kullanılamaz.

Tüm işaretçi kodu gibi, bu güvenli olmayan bir özelliktir ve kullanıldığında bir uyarı oluşturulur.

## <a name="example"></a>Örnek

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn $"pnt before - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn $"pnt after - X: %d{pnt.X} Y: %d{pnt.Y}" // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a>Ayrıca bkz.

- [NativePtr modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)
