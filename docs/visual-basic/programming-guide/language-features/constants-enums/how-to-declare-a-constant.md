---
title: 'Nasıl yapılır: Bir Sabit Bildirme'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: 5054d4a4fc02d8bd22efceb01770fc54167d8cb3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347467"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Nasıl yapılır: Bir Sabit Bildirme (Visual Basic)
You use the `Const` statement to declare a constant and set its value. By declaring a constant, you assign a meaningful name to a value. Once a constant is declared, it cannot be modified or assigned a new value.  
  
 You declare a constant within a procedure or in the declarations section of a module, class, or structure. Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.  
  
 The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>To declare a constant  
  
- Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).  
  
     When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause. The compiler determines the type of the constant from the type of the expression. For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>To declare a constant that has an explicitly stated data type  
  
- Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line. If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>To declare multiple constants on a single line  
  
- Separate the declarations with a comma and a space, as in the following example:  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Const Deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)
- [Sabit ve Değişmez Değerli Veri Türleri](constant-and-literal-data-types.md)
- [Sabitlere Genel Bakış](constants-overview.md)
- [Nasıl yapılır: Bir Sabit Bildirme](how-to-declare-a-constant.md)
- [Kullanıcı Tanımlı Sabitler](user-defined-constants.md)
- [Sabit ve Değişmez Değerli Veri Türleri](constant-and-literal-data-types.md)
- [Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma](how-to-group-related-constant-values-together.md)
- [Sabit Listelerine Genel Bakış](enumerations-overview.md)
- [Nasıl yapılır: Bir Sabit Listesi Bildirme](how-to-declare-enumerations.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](how-to-refer-to-an-enumeration-member.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Nasıl yapılır: Sabit Listesi Yoluyla Yineleme](how-to-iterate-through-an-enumeration.md)
- [Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Sabit Listesi Ne Zaman Kullanılır?](when-to-use-an-enumeration.md)

- [Sabit Listelerine Genel Bakış](enumerations-overview.md)
- [Sabitlere Genel Bakış](constants-overview.md)
- [How to: Declare an Enumeration](how-to-declare-enumerations.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
