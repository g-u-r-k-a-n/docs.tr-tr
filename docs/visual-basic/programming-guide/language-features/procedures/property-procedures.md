---
title: Özellik Yordamları
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: a4b8ac3e27348764f537ee9502ce1fbb165bb3ef
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352571"
---
# <a name="property-procedures-visual-basic"></a>Özellik Yordamları (Visual Basic)

Özellik yordamı bir modül, sınıf veya yapıda özel bir özelliği düzenleyen Visual Basic deyimlerinin bir dizisidir. Özellik yordamları, *özellik erişimcileri*olarak da bilinir.

Visual Basic aşağıdaki özellik yordamları için sağlar:

- `Get` yordam bir özelliğin değerini döndürür. Bir ifadede özelliğe eriştiğinizde çağrılır.
- `Set` yordam bir özelliği bir nesne başvurusu dahil olmak üzere bir değere ayarlar. Özelliğe bir değer atadığınızda çağrılır.

Genellikle özellik yordamlarını `Get` ve `Set` deyimlerini kullanarak çiftler halinde tanımlarsınız, ancak özellik salt okunurdur ([Get deyimi](../../../../visual-basic/language-reference/statements/get-statement.md)) veya salt yazılır ([küme deyimi](../../../../visual-basic/language-reference/statements/set-statement.md)) olduğunda tek başına yordamı tanımlayabilirsiniz.

Otomatik uygulanan bir özellik kullanırken `Get` ve `Set` yordamını atlayabilirsiniz. Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](./auto-implemented-properties.md).

Sınıflar, yapılar ve modüllerde özellikler tanımlayabilirsiniz. Özellikler varsayılan olarak `Public`, bu da bunları, uygulamanızın özelliğin kapsayıcısına erişebilen herhangi bir yerinden çağırabilmeniz anlamına gelir.

Özelliklerin ve değişkenlerin karşılaştırması için [Visual Basic Özellikler ve değişkenler arasındaki farklılıklar](differences-between-properties-and-variables.md)bölümüne bakın.

## <a name="declaration-syntax"></a>Bildirim söz dizimi

Bir özelliğin kendisi, [özellik ifadesinin](../../../../visual-basic/language-reference/statements/property-statement.md) içinde ve `End Property` ifadesiyle bir kod bloğu tarafından tanımlanır. Bu bloğun içinde her özellik yordamı bir bildirim bildirimi (`Get` veya `Set`) ve eşleşen `End` bildirimi içinde iç bir blok olarak görünür.

Bir özelliği ve yordamlarını bildirmek için sözdizimi aşağıdaki gibidir:

```vb
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]
    [AccessLevel] Get
        ' Statements of the Get procedure.
        ' The following statement returns an expression as the property's value.
        Return Expression
    End Get
    [AccessLevel] Set[(ByVal NewValue As DataType)]
        ' Statements of the Set procedure.
        ' The following statement assigns newvalue as the property's value.
        LValue = NewValue
    End Set
End Property
' - or -
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]
```

`Modifiers`, aşırı yükleme, geçersiz kılma, paylaşma ve gölgeleme ile ilgili erişim düzeyini ve bilgileri belirtebilir, özelliğin salt okunurdur mi yoksa salt yazılır mı olduğunu belirtir. `Get` veya `Set` yordamındaki `AccessLevel`, özelliğin kendisi için belirtilen erişim düzeyinden daha kısıtlayıcı olan herhangi bir düzey olabilir. Daha fazla bilgi için bkz. [özellik açıklaması](../../../../visual-basic/language-reference/statements/property-statement.md).

### <a name="data-type"></a>Veri Türü

Özelliğin veri türü ve asıl erişim düzeyi, özellik yordamlarında değil, `Property` bildiriminde tanımlanmıştır. Bir özellik yalnızca bir veri türüne sahip olabilir. Örneğin, `Decimal` bir değeri depolamak için bir özellik tanımlayamazsınız, ancak bir `Double` değeri alabilirsiniz.

### <a name="access-level"></a>Erişim düzeyi

Ancak, bir özellik için bir asıl erişim düzeyi tanımlayabilir ve özellik yordamlarından birinde erişim düzeyini daha da kısıtlayabilirsiniz. Örneğin, bir `Public` özelliği tanımlayabilir ve sonra bir `Private Set` yordamı tanımlayabilirsiniz. `Get` yordam `Public`kalır. Erişim düzeyini bir özelliğin yordamlarından yalnızca birinde değiştirebilirsiniz ve yalnızca asıl erişim düzeyinden daha kısıtlayıcı hale getirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: karışık erişim düzeylerine sahip bir özellik bildirme](how-to-declare-a-property-with-mixed-access-levels.md).

## <a name="parameter-declaration"></a>Parametre bildirimi

Geçirilen mekanizmanın `ByVal`olması dışında, her bir parametreyi [alt yordamlar](sub-procedures.md)için yaptığınız gibi bildirirsiniz.

Parametre listesindeki her bir parametre için sözdizimi aşağıdaki gibidir:

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

Parametre isteğe bağlı ise, bildiriminin bir parçası olarak bir varsayılan değer de belirtmeniz gerekir. Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a>Özellik değeri

`Get` yordamında, dönüş değeri, özelliğin değeri olarak çağırma ifadesine sağlanır.

`Set` yordamında, yeni özellik değeri `Set` deyimin parametresine geçirilir. Açıkça bir parametre bildirirseniz, özelliği ile aynı veri türüyle bildirmeniz gerekir. Bir parametre bildirmezsiniz derleyici, özelliğe atanacak yeni değeri göstermek için `Value` örtük parametresini kullanır.

## <a name="calling-syntax"></a>Çağırma sözdizimi

Özelliğe başvuru yaparak bir özellik yordamını örtük olarak çağırılır. Özelliği, isteğe bağlı olmayan tüm bağımsız değişkenlerin değerlerini sağlamanız ve bağımsız değişken listesini parantez içine almanız gerekir, ancak, özelliğin adını bir değişkenin adını kullandığınız şekilde kullanırsınız. Herhangi bir bağımsız değişken sağlanmazsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.

Bir `Set` yordamına örtük çağrının sözdizimi aşağıdaki gibidir:

```vb
propertyname[(argumentlist)] = expression
```

Bir `Get` yordamına örtük çağrının sözdizimi aşağıdaki gibidir:

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı gösterimi

Aşağıdaki özellik, tam adı iki anayent adı, ad ve soyadı olarak depolar. Çağıran kod `fullName`okurken, `Get` yordamı iki anayent adını birleştirir ve tam adı döndürür. Çağıran kod yeni bir tam ad atarken, `Set` yordamı onu iki anayada bölmek için çalışır. Bir boşluk bulamazsa, ilk ad olarak tümünü depolar.

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

Aşağıdaki örnek, `fullName`Özellik yordamlarına yapılan tipik çağrıları gösterir:

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](index.md)
- [İşlev Yordamları](function-procedures.md)
- [İşleç Yordamları](operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](procedure-parameters-and-arguments.md)
- [Visual Basic Özellikler ve değişkenler arasındaki farklar](differences-between-properties-and-variables.md)
- [Nasıl yapılır: Özellik Oluşturma](how-to-create-a-property.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Visual Basic varsayılan bir özellik bildirme ve çağırma](how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliğe Değer Ekleme](how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](how-to-get-a-value-from-a-property.md)
