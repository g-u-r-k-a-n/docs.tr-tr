---
title: F# kod biçimlendirme yönergeleri
description: 'F # kodunu biçimlendirmeye yönelik yönergeleri öğrenin.'
ms.date: 08/31/2020
ms.openlocfilehash: b8997a3cd854bd89e292e1090b5ebba3f7e6ae99
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255486"
---
# <a name="f-code-formatting-guidelines"></a>F# kod biçimlendirme yönergeleri

Bu makalede, F # kodunuzun olması için kodunuzu biçimlendirme yönergeleri sunulmaktadır:

* Daha okunaklı
* Visual Studio ve diğer düzenleyicilerde biçimlendirme araçları tarafından uygulanan kurallara uygun olarak
* Çevrimiçi diğer koda benzer

Bu yönergeler, [Anh-Dung Phan](https://github.com/dungpa)tarafından oluşturulan [F # biçimlendirme kurallarına yönelik kapsamlı bir kılavuza](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) dayanır.

## <a name="general-rules-for-indentation"></a>Girintileme için genel kurallar

F # varsayılan olarak önemli boşluk kullanır. Aşağıdaki kılavuzlar, bu, uygulayabileceğine dair bazı güçlüklerin nasıl ele alınacağını gösteren yönergeler sağlamaya yöneliktir.

### <a name="using-spaces"></a>Boşluk kullanma

Girintileme gerekli olduğunda, sekmeler değil, boşluk kullanmanız gerekir. En az bir alan gereklidir. Kuruluşunuz, girintileme için kullanılacak boşluk sayısını belirtmek için kodlama standartları oluşturabilir; her düzeyde girintileme her zamanki iki, üç veya dört boşluk.

**Girintileme başına dört boşluk önerilir.**

Bu şekilde, programların girintileme öznel bir önemi olur. Çeşitlemeler Tamam, ancak izlemeniz gereken ilk kural *girintileme tutarlılığından* oluşur. Genellikle kabul edilen bir girintileme stili seçin ve kod tabanınızın tamamında sistematik olarak kullanın.

## <a name="formatting-white-space"></a>Boşluk biçimlendirme

F #, boşluk duyarlıdır. Beyaz boşluktan çok sayıda anlambilim doğru girintileme kapsamında olmakla birlikte göz önünde bulundurmanız gereken bazı şeyler vardır.

### <a name="formatting-operators-in-arithmetic-expressions"></a>Aritmetik İfadelerdeki biçimlendirme işleçleri

Her zaman ikili aritmetik ifadelerin etrafında boşluk kullanın:

```fsharp
let subtractThenAdd x = x - 1 + 3
```

Birli `-` işleçler her zaman, yoksayıdıkları değer tarafından hemen izlenir:

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

İşleçten sonra bir boşluk karakteri eklemek, `-` Diğerlerinin karışıklığına neden olabilir.

Özetle, her zaman için önemlidir:

* Boşluk ile ikili işleçler çevreleme
* Birli işleçten sonra hiç bir sondaki boşluk yok

İkili aritmetik işleç Kılavuzu özellikle önemlidir. `-`Belirli biçimlendirme seçenekleriyle birleştirildiğinde ikili bir işlecin sarlamaması, tek bir birli olarak yorumlanmasına neden olabilir `-` .

### <a name="surround-a-custom-operator-definition-with-white-space"></a>Bir özel operatör tanımını boşluk ile çevreleyin

Her zaman bir operatör tanımını çevrelemek için boşluk kullanın:

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

İle başlayan ve birden fazla karakter içeren herhangi bir özel operatör için `*` , bir derleyici belirsizliğini önlemek için tanımın başlangıcına boşluk eklemeniz gerekir. Bu nedenle, tek bir boşluk karakteriyle tüm işleçlerin tanımlarını çevrelemeyi öneririz.

### <a name="surround-function-parameter-arrows-with-white-space"></a>Boşluk işlevi parametre okları boşluk ile

Bir işlevin imzasını tanımlarken, simgenin etrafında boşluk kullanın `->` :

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>Boşluk ile çevreleme işlevi bağımsız değişkenleri

Bir işlevi tanımlarken, her bağımsız değişken etrafında boşluk kullanın.

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="avoid-name-sensitive-alignments"></a>Ad duyarlı hizalamaları önleyin

Genel olarak, şu şekilde adlandırmaya duyarlı olan girintileme ve hizalamadan kaçınmak için arama yapın:

```fsharp
// OK
let myLongValueName =
    someExpression
    |> anotherExpression


// Bad
let myLongValueName = someExpression
                      |> anotherExpression
```

Bu bazen "Vanity hizalaması" veya "Vanity girintileme" olarak adlandırılır. Bunu önlemenin başlıca nedenleri şunlardır:

* Önemli kod en sağa taşınır
* Gerçek kod için daha az genişlik kalmadı
* Yeniden adlandırma, hizalamayı bozabilir

`do` / `do!` Girintiden tutarlı kalmasını sağlamak için aynısını yapın `let` / `let!` . Aşağıda bir sınıfta kullanılan örnek verilmiştir `do` :

```fsharp
// OK
type Foo () =
    let foo =
        fooBarBaz
        |> loremIpsumDolorSitAmet
        |> theQuickBrownFoxJumpedOverTheLazyDog
    do
        fooBarBaz
        |> loremIpsumDolorSitAmet
        |> theQuickBrownFoxJumpedOverTheLazyDog

// Bad - notice the "do" expression is indented one space less than the `let` expression
type Foo () =
    let foo =
        fooBarBaz
        |> loremIpsumDolorSitAmet
        |> theQuickBrownFoxJumpedOverTheLazyDog
    do fooBarBaz
       |> loremIpsumDolorSitAmet
       |> theQuickBrownFoxJumpedOverTheLazyDog
```

Aşağıda, girintileme 2 ' nin kullanılmasıyla ilgili bir örnek verilmiştir `do!` ( `do!` 4 ' ün girintileme ile yaklaşımlar arasında fark yoktur):

```fsharp
// OK
async {
  let! foo =
    fooBarBaz
    |> loremIpsumDolorSitAmet
    |> theQuickBrownFoxJumpedOverTheLazyDog
  do!
    fooBarBaz
    |> loremIpsumDolorSitAmet
    |> theQuickBrownFoxJumpedOverTheLazyDog
}

// Bad - notice the "do!" expression is indented two spaces more than the `let!` expression
async {
  let! foo =
    fooBarBaz
    |> loremIpsumDolorSitAmet
    |> theQuickBrownFoxJumpedOverTheLazyDog
  do! fooBarBaz
      |> loremIpsumDolorSitAmet
      |> theQuickBrownFoxJumpedOverTheLazyDog
}
```

### <a name="place-parameters-on-a-new-line-for-long-definitions"></a>Uzun tanımlarda parametreleri yeni bir satıra yerleştir

Uzun bir işlev tanımınız varsa, parametreleri yeni satırlara yerleştirip sonraki parametrenin girintileme düzeyiyle eşleşecek şekilde Girintile.

```fsharp
module M =
    let longFunctionWithLotsOfParameters
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        =
        // ... the body of the method follows

    let longFunctionWithLotsOfParametersAndReturnType
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        : ReturnType =
        // ... the body of the method follows

    let longFunctionWithLongTupleParameter
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) =
        // ... the body of the method follows

    let longFunctionWithLongTupleParameterAndReturnType
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) : ReturnType =
        // ... the body of the method follows
```

Bu Ayrıca, tanımlama gruplarını kullanan üyeler, oluşturucular ve parametreler için de geçerlidir:

```fsharp
type TM() =
    member _.LongMethodWithLotsOfParameters
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) =
        // ... the body of the method

type TC
    (
        aVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aSecondVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aThirdVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse
    ) =
    // ... the body of the class follows
```

Parametreler bir daha belirtilmişse, `=` karakteri yeni bir satıra herhangi bir dönüş türü ile birlikte yerleştirin:

```fsharp
type C() =
    member _.LongMethodWithLotsOfCurrifiedParamsAndReturnType
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        : ReturnType =
        // ... the body of the method
    member _.LongMethodWithLotsOfCurrifiedParams
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        =
        // ... the body of the method
```

Bu, çok uzun çizgileri önlemenin bir yoludur (Bu durumda, dönüş türü uzun bir ada sahip olabilir) ve parametreler eklenirken daha az sayıda satır hasarı olabilir.

### <a name="type-annotations"></a>Tür ek açıklamaları

#### <a name="right-pad-function-argument-type-annotations"></a>Sağ panel işlevi bağımsız değişken türü ek açıklamaları

Tür ek açıklamalarıyla bağımsız değişkenler tanımlarken, simgeden sonra boşluk kullanın `:` :

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>Boşluk içeren surround dönüş türü ek açıklamaları

Bir izin-bağlantılı işlevinde veya değer türü ek açıklamasında (bir işlev durumunda dönüş türü), simgeden önce ve sonra boşluk kullanın `:` :

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

### <a name="formatting-bindings"></a>Bağlamaları biçimlendirme

Her durumda, bir bağlamanın sağ tarafı tek bir satırda veya (çok uzunsa) yeni bir satır girintilenir bir kapsamda gider.

Örneğin, aşağıdakiler uyumlu değil:

```fsharp
let a = """
foobar, long string
"""

type File =
    member this.SaveAsync(path: string) : Async<unit> = async {
        // IO operation
        return ()
    }

let c = {
    Name = "Bilbo"
    Age = 111
    Region = "The Shire"
}

let d = while f do
    printfn "%A" x
```

Aşağıdakiler uyumludur:

```fsharp
let a =
    """
foobar, long string
"""

type File =
    member this.SaveAsync(path: string) : Async<unit> =
        async {
            // IO operation
            return ()
        }

let c =
    { Name = "Bilbo"
      Age = 111
      Region = "The Shire" }

let d =
    while f do
        printfn "%A" x
```

## <a name="formatting-blank-lines"></a>Boş satırları biçimlendirme

* En üst düzey işlev ve sınıf tanımlarını iki boş satır ile ayırın.
* Bir sınıf içindeki yöntem tanımları, tek bir boş satırla ayrılır.
* İlgili işlevlerin gruplarını ayırmak için fazladan boş satırlar kullanılabilir (gelişigüzel). Bir arada ilgili tek bir grup (örneğin, bir kukla uygulamalar kümesi) arasında boş satırlar atlanabilir.
* Mantıksal bölümleri göstermek için işlevlerde boş satırları gelişigüzel bir şekilde kullanın.

## <a name="formatting-comments"></a>Biçimlendirme açıklamaları

Genellikle, ML stili blok açıklamaları üzerinde birden çok çift eğik açıklama tercih eder.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Satır içi yorumların ilk harfi büyük harfle yazılmalıdır.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="formatting-string-literals-and-interpolated-strings"></a>Dize değişmezlerini ve enterpolasyonlu dizeleri biçimlendirme

Dize değişmezleri ve enterpolasyonlu dizeler, çizginin ne kadar süreyle olduğuna bakmaksızın yalnızca tek bir satırda bırakılabilir.

```fsharp
let serviceStorageConnection =
    $"DefaultEndpointsProtocol=https;AccountName=%s{serviceStorageAccount.Name};AccountKey=%s{serviceStorageAccountKey.Value}"
```

Çok satırlı enterpolasyonlu ifadeler kesinlikle önerilmez. Bunun yerine, ifade sonucunu bir değere bağlayın ve bunu, enterpolasyonlu dizede kullanın.

## <a name="naming-conventions"></a>Adlandırma kuralları

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Sınıf bağlantılı, ifade ile bağlantılı ve kalıp bağlantılı değerler ve işlevler için camelCase kullanın

Yerel değişkenler veya kalıp eşleşmeleri ve işlev tanımları ile bağlantılı tüm adlar için camelCase kullanmak için ortak ve kabul edilen F # stili kullanılır.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Sınıflarda yerel olarak bağlantılı işlevler de camelCase kullanmalıdır.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Modül bağlantılı ortak işlevler için camelCase kullanın

Modül bağlantılı bir işlev ortak bir API 'nin parçasıysa, camelCase kullanmalıdır:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>İç ve özel modüle yönelik değerler ve işlevler için camelCase kullanın

Aşağıdakiler de dahil olmak üzere, özel modül bağlantılı değerler için camelCase kullanın:

* Betiklerdeki geçici işlevler

* Modül veya türün iç uygulamasını oluşturan değerler

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Parametreler için camelCase kullanın

Tüm parametrelerin, .NET adlandırma kurallarına uygun olarak camelCase kullanması gerekir.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Modüller için PascalCase kullanın

Tüm modüller (üst düzey, iç, özel, iç içe) PascalCase kullanmalıdır.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Tür bildirimleri, Üyeler ve Etiketler için PascalCase kullanın

Sınıflar, arabirimler, yapılar, numaralandırmalar, temsilciler, kayıtlar ve ayırt edici birleşimler PascalCase ile adlandırılmalıdır. Kayıt ve ayrılmış birleşimler için türler ve Etiketler içindeki Üyeler PascalCase de kullanmalıdır.

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>.NET 'e iç yapılar için PascalCase kullanın

Ad alanları, özel durumlar, olaylar ve proje/ `.dll` adlar PascalCase ' i de kullanmalıdır. Bu, diğer .NET dillerinden gelen tüketimin tüketicilere daha doğal bir fikir sunmasına değil, büyük olasılıkla karşılaşabileceğiniz .NET adlandırma kurallarıyla de tutarlıdır.

### <a name="avoid-underscores-in-names"></a>Adlarda alt çizgileri önleyin

Tarihsel olarak, bazı F # kitaplıklarında adlarda alt çizgiler kullanıldı. Ancak, bu, kısmen kabul edilmez, kısmen de .NET adlandırma kurallarına çakışıyor. Yani, bazı F # programcıları büyük ölçüde, kısmen geçmiş nedenlerle alt çizgi kullanır ve tolerans ve saygı önemli öneme sahiptir. Ancak, bu stil genellikle kullanılıp kullanılmayacağını öğrenmek için bir seçenek olan başkaları tarafından ayırt edilir.

Bir özel durum, yerel bileşenlerle birlikte çalışmaya dahildir ve alt çizgilerin ortak olduğu durumdur.

### <a name="use-standard-f-operators"></a>Standart F # işleçlerini kullanın

Aşağıdaki işleçler F # standart kitaplığı 'nda tanımlanmıştır ve eşdeğerleri tanımlamak yerine kullanılmalıdır. Bu işleçlerin kullanılması, kodun daha okunaklı ve farklı hale getirme eğilimi için önerilir. OCaml veya diğer işlevsel programlama dilinde arka plan içeren geliştiriciler farklı ıoms 'ye alışkın olabilir. Aşağıdaki listede önerilen F # işleçleri özetlenmektedir.

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>`Foo<T>`Tercihe sonek sözdizimi () içinde genel türler () için önek sözdizimini `T Foo` kullanın

F #, genel türleri (örneğin, `int list` ) ve önek .net stili (örneğin,) adlandırmanın SONEK ml stilini devralır `list<int>` . Beş özel tür hariç .NET stilini tercih edin:

1. F # listeleri için sonek biçimini kullanın: `int list` yerine `list<int>` .
2. F # seçenekleri için sonek biçimini kullanın: `int option` yerine `option<int>` .
3. F # değer seçenekleri için sonek biçimini kullanın: `int voption` yerine `voption<int>` .
4. F # dizileri için veya yerine sözdizimsel adı kullanın `int[]` `int array` `array<int>` .
5. Başvuru hücreleri için `int ref` veya yerine kullanın `ref<int>` `Ref<int>` .

Diğer tüm türler için önek formunu kullanın.

## <a name="formatting-tuples"></a>Tanımlama gruplarını biçimlendirme

Tanımlama grubu örneklemesi parantez içine alınmalıdır ve içindeki sınırlandırma virgüller tek bir boşluk gelmelidir, örneğin: `(1, 2)` , `(x, y, z)` .

Tanımlama gruplarının düzeniyle eşleştirilirken parantezleri atlamak için genellikle kabul edilir:

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

Kayıt düzeni bir işlevin dönüş değeri ise ayraçları atlamak için de kabul edilir:

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

Özet ' te, parantez içine alınmış demet örneklemeleri tercih eder, ancak kalıp eşleme veya dönüş değeri için tanımlama grupları kullanıldığında, ayraçları önlemek için ince olarak kabul edilir.

## <a name="formatting-discriminated-union-declarations"></a>Ayırt edici birleşim bildirimlerini biçimlendirme

`|`Tür tanımında dört boşlukla Girintile:

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

Tek bir kısa birleşim olduğunda, öndeki boşluğu atlayabilirsiniz `|` .

```fsharp
type Address = Address of string
```

Daha uzun veya çok satırlı bir birleşim için, ' yi tutun `|` .

```fsharp
[<NoEquality; NoComparison>]
type SynBinding =
    | SynBinding of
        accessibility: SynAccess option *
        kind: SynBindingKind *
        mustInline: bool *
        isMutable: bool *
        attributes: SynAttributes *
        xmlDoc: PreXmlDoc *
        valData: SynValData *
        headPat: SynPat *
        returnInfo: SynBindingReturnInfo option *
        expr: SynExpr *
        range: range *
        seqPoint: DebugPointAtBinding
```

Üçlü eğik çizgi açıklamalarını da kullanabilirsiniz `///` .

```fsharp
type Foobar =
    /// Code comment
    | Foobar of int
```

## <a name="formatting-discriminated-unions"></a>Ayırt edici birleşimleri biçimlendirme

Birleşim durumlarını ayırt etmek için parantez içine alınmış/tupled parametrelerinden önce bir boşluk kullanın:

```fsharp
// OK
let opt = Some ("A", 1)

// Not OK
let opt = Some("A", 1)
```

Birden çok satıra bölünen oluşturulmuş ayrılmış birleşimler, içerilen verileri girintileme ile yeni bir kapsam olarak vermelidir:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode (BinaryValue 1, BinaryValue 2),
         BinaryNode (BinaryValue 3, BinaryValue 4))
```

Kapanış parantezi de yeni bir satır üzerinde olabilir:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode (BinaryValue 1, BinaryValue 2),
        BinaryNode (BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Kayıt bildirimlerini biçimlendirme

`{`Tür tanımında dört boşlukla girinti yapın ve alan listesini aynı satırda başlatın:

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = $"{x.Zip} {x.City}"

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = $"{x.Zip} {x.City}"

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

Kayıt üzerinde arabirim uygulamaları veya Üyeler bildirirken, açma belirtecinin yeni bir satıra yerleştirilmesi ve yeni bir satırdaki kapatma belirteci tercih edilir:

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = $"{x.Zip} {x.City}"

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>Kayıtları biçimlendirme

Kısa kayıtlar tek bir satırda yazılabilir:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Daha uzun olan kayıtlar, Etiketler için yeni satırları kullanmalıdır:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Açma belirtecinin yeni bir satıra yerleştirilmesi, bir kapsam üzerinde sekmeli içerikler ve yeni bir satırdaki kapatma belirteci, şu durumlarda tercih edilir:

* Farklı girintileme kapsamları ile koddaki kayıtları taşıma
* Bir işleve boru oluşturma

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map
           (fun x ->
                {
                    MyField = x
                })
```

Liste ve dizi öğeleri için aynı kurallar geçerlidir.

## <a name="formatting-copy-and-update-record-expressions"></a>Copy ve Update kayıt ifadelerini biçimlendirme

Bir kopyalama ve güncelleştirme kayıt ifadesi hala bir kayıt olduğundan benzer yönergeler geçerlidir.

Kısa ifadeler tek bir satıra uygun olabilir:

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

Daha uzun ifadeler yeni satırları kullanmalıdır:

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = [ "Zippy"; "George"; "Bungle" ] }
```

Kayıt kılavuzunda olduğu gibi, küme ayraçları için ayrı satırlar atamak ve bir kapsamın sağına doğru bir kapsamını girintilemek isteyebilirsiniz. Parantez olmadan isteğe bağlı bir değeri sarmalama gibi bazı özel durumlarda, bir satır için bir küme ayracı tutmanız gerekebilir:

```fsharp
type S = { F1: int; F2: string }
type State = { Foo: S option }

let state = { Foo = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            Foo =
                Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a>Listeleri ve dizileri biçimlendirme

`x :: l`İşlecin etrafında boşluk ile yazın `::` ( `::` Bu nedenle boşluklarla çevrelenmiş bir işleçtir).

Tek bir satırda tanımlanan liste ve diziler, açma köşeli ayracından sonra ve kapatma parantezinden önce bir boşluk içermelidir:

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

Her zaman iki farklı küme ayracı benzeri işleç arasında en az bir boşluk kullanın. Örneğin, ve arasında bir boşluk bırakın `[` `{` .

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

Aynı kılavuz, tanımlama gruplarının listeleri veya dizileri için geçerlidir.

Birden çok satıra bölünen listeler ve diziler, kayıt olarak benzer bir kuralı izler:

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

Kayıtlarda olduğu gibi, açılış ve kapanış köşeli ayracını kendi satırlarıyla birlikte bildirmek, kodun etrafında ve boru işlevlerine daha kolay bir şekilde sahip olmasını sağlar.

Program aracılığıyla diziler ve listeler oluştururken, `->` `do ... yield` her zaman bir değer oluşturulduğunda tercih edin:

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

F # dilinin, `yield` verilerin koşullu olarak üretilebileceği durumlarda belirtilmesi gerekir veya değerlendirilecek ardışık ifadeler olabilir. `yield`Daha eski bir F # dil sürümüyle derlemeniz gerekmedikçe bu anahtar sözcüklerin atlanması tercih edin:

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

Bazı durumlarda okunabilirlik konusunda `do...yield` yardımcı olabilir. Bu durumlarda, öznel, dikkate alınması gerekir.

## <a name="formatting-if-expressions"></a>İfadeleri biçimlendirme

Koşullular girintileme, bunları yapan ifadelerin boyutuna ve karmaşıklığına bağlıdır.
Bunları bir satıra yazın:

- `cond`, `e1` , ve `e2` kısacası
- `e1` ve `e2` `if/then/else` kendi kendilerine deyimler değildir.

```fsharp
if cond then e1 else e2
```

Deyimlerden herhangi biri çok satırlı veya `if/then/else` deyimlerdir.

```fsharp
if cond then
    e1
else
    e2
```

Ve ile birden çok koşul, `elif` `else` `if` tek satır ifadelerinin kurallarını izlediklerinde ile aynı kapsamda girintilenir `if/then/else` .

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

Koşulların veya ifadelerden herhangi biri çok satırlıdır, tüm `if/then/else` ifade çok satırlı olur:

```fsharp
if cond1 then
    e1
elif cond2 then
    e2
elif cond3 then
    e3
else
    e4
```

### <a name="pattern-matching-constructs"></a>Model eşleştirme yapıları

Bir `|` eşleşmenin for each yan tümcesini girintileme olmadan kullanın. İfade kısaysa, her alt ifade da basit olduğunda tek bir satır kullanmayı düşünebilirsiniz.

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

Bir düzenin sağ tarafındaki ifade çok büyükse, bu satırı aşağıdaki satıra taşıyın ve ' den bir adım girintilenir `match` / `|` .

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Tarafından başlayan anonim işlevlerin örüntüme göre `function` , genellikle çok uzakta girintisiz. Örneğin, bir kapsamı aşağıda gösterildiği gibi girintileme iyi bir şekilde belirlenir:

```fsharp
lambdaList
|> List.map
       (function
            | Abs(x, body) -> 1 + sizeLambda 0 body
            | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
            | Var v -> 1)
```

Ya da tarafından tanımlanan işlevlerde desenler `let` eşleştirmesi `let rec` `let` , `function` anahtar sözcüğünün kullanılsa bile, başlatıldıktan sonra dört boşluk olmalıdır:

```fsharp
let rec sizeLambda acc =
    function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Okları hizalamayı önermiyoruz.

## <a name="formatting-trywith-expressions"></a>Try/with ifadelerini biçimlendirme

Özel durum türünde model eşleştirme, ile aynı düzeyde girintili olmalıdır `with` .

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a>İşlev parametresi uygulamasını biçimlendirme

Genel olarak, çoğu bağımsız değişken aynı satırda sağlanır:

```fsharp
let x = sprintf "\t%s - %i\n\r" x.IngredientName x.Quantity

let printListWithOffset a list1 =
    List.iter (fun elem -> printfn $"%d{a + elem}") list1
```

İşlem hatları söz konusu olduğunda, aynı satırda bir curried işlevin bağımsız değişken olarak uygulandığı de aynı zamanda aynı şekilde geçerlidir:

```
let printListWithOffsetPiped a list1 =
    list1
    |> List.iter (fun elem -> printfn $"%d{a + elem}")
```

Ancak, bağımsız değişkenleri bir işleve, okunabilirliği veya bağımsız değişkenlerin listesi veya bağımsız değişken adlarının çok uzun olmasından bağımsız olarak yeni bir satıra geçirmek isteyebilirsiniz. Bu durumda, bir kapsamla Girintile:

```fsharp

// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

Lambda ifadelerinde, bir lambda ifadesinin gövdesini yeni bir satıra yerleştirmeyi, yeterince uzunsa bir kapsama göre de düşünmek isteyebilirsiniz:

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
             printfn $"A very long line to format the value: %d{a + elem}")
        list1

let printListWithOffsetPiped a list1 =
    list1
    |> List.iter
           (fun elem ->
                printfn $"A very long line to format the value: %d{a + elem}")
```

Lambda ifadesinin gövdesi birden çok satır uzunsa, bunu yerel olarak kapsamlı bir işleve yeniden düzenlemeyi göz önünde bulundurmanız gerekir.

`fun` / `function` İşlevin göründüğü bağlamdan bağımsız olarak, parametreler genellikle işlev veya anahtar sözcüğe göre girintilenir:

```fsharp
// With 4 spaces indentation
list1
|> List.fold
       someLongParam
       anotherLongParam

list1
|> List.iter
       (fun elem ->
            printfn $"A very long line to format the value: %d{elem}")

// With 2 spaces indentation
list1
|> List.fold
     someLongParam
     anotherLongParam

list1
|> List.iter
       (fun elem ->
          printfn $"A very long line to format the value: %d{elem}")
```

İşlev tek bir çok satırlı dizi bağımsız değişkeni aldığınızda, [biçimlendirme oluşturucuları, statik üyeler ve üye etkinleştirmeleri](#formatting-constructors-static-members-and-member-invocations) için aynı kurallar geçerlidir.

```fsharp
let myFunction (a: int, b: string, c: int, d: bool) =
    ()

myFunction(
    478815516,
    "A very long string making all of this multi-line",
    1515,
    false
)
```

### <a name="formatting-infix-operators"></a>Hatalı bir şekilde biçimlendirme işleçleri

İşleçleri boşluklara göre ayırın. Bu kuralın belirgin özel durumları `!` ve `.` işleçleridir.

Indüzeltilme ifadeleri aynı sütundaki sıralama için Tamam:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators-or-mutable-assignments"></a>Ardışık düzen işleçlerini veya kesilebilir atamaları biçimlendirme

`|>`İşlem hattı işleçleri üzerinde çalıştıkları ifadelerin altına gitmelidir.

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat

// Not OK either
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
               |> List.ofArray
               |> List.map (fun assm -> assm.GetTypes())
               |> Array.concat
               |> List.ofArray
               |> List.map (fun t -> t.GetMethods())
               |> Array.concat
```

Bu, kesilebilir ayarlayıcılar için de geçerlidir:

```fsharp
// Preferred approach
ctx.Response.Headers.[HeaderNames.ContentType] <-
    Constants.jsonApiMediaType |> StringValues
ctx.Response.Headers.[HeaderNames.ContentLength] <-
    bytes.Length |> string |> StringValues

// Not OK
ctx.Response.Headers.[HeaderNames.ContentType] <- Constants.jsonApiMediaType
                                                  |> StringValues
ctx.Response.Headers.[HeaderNames.ContentLength] <- bytes.Length
                                                    |> string
                                                    |> StringValues
```

### <a name="formatting-modules"></a>Biçimlendirme modülleri

Yerel modüldeki kodun modüle bağlı olması gerekir, ancak üst düzey modüldeki kod girintilenmemelidir. Ad alanı öğelerinin girintili olması gerekmez.

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a>Nesne ifadelerini ve arabirimleri biçimlendirme

Nesne ifadeleri ve arabirimler, `member` dört boşluktan sonra girintilenmiş şekilde hizalanmalıdır.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>İfadelerde boşluk biçimlendirme

F # ifadelerinde gereksiz boşluk kullanmaktan kaçının.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Adlandırılmış bağımsız değişkenler de çevreleyen boşluk içermemelidir `=` :

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

### <a name="formatting-constructors-static-members-and-member-invocations"></a>Biçimlendirme oluşturucuları, statik üyeler ve üye etkinleştirmeleri

İfade kısaysa, bağımsız değişkenleri boşluklarla ayırın ve tek bir satırda saklayın.

```fsharp
let person = new Person(a1, a2)

let myRegexMatch = Regex.Match(input, regex)

let untypedRes = checker.ParseFile(file, source, opts)
```

İfade uzunsa, köşeli ayracını girintileme yerine newlines kullanın ve bir kapsamı girintileyin.

```fsharp
let person =
    new Person(
        argument1,
        argument2
    )

let myRegexMatch =
    Regex.Match(
        "my longer input string with some interesting content in it",
        "myRegexPattern"
    )

let untypedRes =
    checker.ParseFile(
        fileName,
        sourceText,
        parsingOptionsWithDefines
    )
```

Aynı kurallar yalnızca tek bir çok satırlı bağımsız değişken olsa bile geçerlidir.

```fsharp
let poemBuilder = StringBuilder()
poemBuilder.AppendLine(
    """
The last train is nearly due
The Underground is closing soon
And in the dark, deserted station
Restless in anticipation
A man waits in the shadows
    """
)

Option.traverse(
    create
    >> Result.setError [ invalidHeader "Content-Checksum" ]
)
```

## <a name="formatting-generic-type-arguments-and-constraints"></a>Genel tür bağımsız değişkenlerini ve kısıtlamalarını biçimlendirme

Aşağıdaki yönergeler hem işlevler, Üyeler ve tür tanımları için geçerlidir.

Çok uzun değilse, genel tür bağımsız değişkenlerini ve kısıtlamalarını tek bir satırda tutun:

```fsharp
let f<'a, 'b when 'a : equality and 'b : comparison> param =
    // function body
```

Hem genel tür bağımsız değişkenleri/kısıtlamaları hem de işlev parametreleri uygun değilse, ancak tür parametreleri/kısıtlamaları tek başına ise, parametreleri yeni satırlara yerleştirin:

```fsharp
let f<'a, 'b when 'a : equality and 'b : comparison>
    param
    =
    // function body
```

Tür parametreleri veya kısıtlamaları çok uzunsa, break ve bunları aşağıda gösterildiği gibi hizalayın. Tür parametrelerinin listesini, uzunluğundan bağımsız olarak işlevle aynı satırda tutun. Kısıtlamalar için `when` ilk satıra yerleştirin ve her kısıtlamayı, uzunluğundan bağımsız olarak tek bir satırda tutun. `>`Son satırın sonuna yerleştirin. Kısıtlamaları bir düzey ile girintileyin.

```fsharp
let inline f< ^a, ^b
    when ^a : (static member Foo1: unit -> ^b)
    and ^b : (member Foo2: unit -> int)
    and ^b : (member Foo3: string -> ^a option)>
    arg1
    arg2
    =
    // function body
```

Tür parametreleri/kısıtlamaları bozulur, ancak normal işlev parametreleri yoksa, aşağıdakileri göz `=` önüne alarak yeni bir satıra yerleştirin:

```f#
let inline f<^a, ^b
    when ^a : (static member Foo1: unit -> ^b)
    and ^b : (member Foo2: unit -> int)
    and ^b : (member Foo3: string -> ^a option)>
    =
    // function body
```

## <a name="formatting-attributes"></a>Biçimlendirme öznitelikleri

[Öznitelikler](../language-reference/attributes.md) bir yapının üzerine yerleştirilir:

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

XML belgelerinden sonra gitmeleri gerekir:

```fsharp
/// Module with some things in it.
[<RequireQualifiedAccess>]
module M =
    let f x = x
```

### <a name="formatting-attributes-on-parameters"></a>Parametrelerde öznitelikleri biçimlendirme

Öznitelikler, parametrelere de yerleştirilebilir. Bu durumda, daha sonra parametresiyle aynı satıra ve adından önce yerleştirin:

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>Birden çok özniteliği biçimlendirme

Bir parametre olmayan bir yapı için birden çok öznitelik uygulandığında, her satır için bir öznitelik olması gibi yerleştirilmelidir:

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

Bir parametreye uygulandığında, bunların aynı satırda olmaları ve bir `;` ayırıcıyla ayrılması gerekir.

## <a name="formatting-literals"></a>Sabit değerleri biçimlendirme

Özniteliği kullanan [F # değişmez değerleri](../language-reference/literals.md) `Literal` özniteliği kendi satırına yerleştirip PascalCase adlandırmayı kullanmalıdır:

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

Özniteliği değeri ile aynı satıra yerleştirmekten kaçının.

## <a name="formatting-computation-expression-operations"></a>Hesaplama ifade işlemlerini biçimlendirme

[Hesaplama ifadeleri](../language-reference/computation-expressions.md)için özel işlemler oluştururken, camelCase adlandırması kullanılması önerilir:

```fsharp
type MathBuilder () =
    member _.Yield _ = 0

    [<CustomOperation("addOne")>]
    member _.AddOne (state: int) =
        state + 1

    [<CustomOperation("subtractOne")>]
    member _.SubtractOne (state: int) =
        state - 1

    [<CustomOperation("divideBy")>]
    member _.DivideBy (state: int, divisor: int) =
        state / divisor

    [<CustomOperation("multiplyBy")>]
    member _.MultiplyBy (state: int, factor: int) =
        state * factor

let math = MathBuilder()

// 10
let myNumber =
    math {
        addOne
        addOne
        addOne

        subtractOne

        divideBy 2

        multiplyBy 10
    }
```

Modellenen etki alanı, sonunda adlandırma kuralını kullanmalıdır.
Farklı bir kural kullanmak istiyorsanız, bunun yerine bu kural kullanılmalıdır.
