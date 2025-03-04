---
description: "Hakkında daha fazla bilgi edinin: BC40025: ' ' üyesinin türü <membername> CLS uyumlu değil"
title: "'<membername>' üyesinin türü CLS uyumlu değil"
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: 4fe83999a0cb2d678ccc0119509a368160dfc3ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774882"
---
# <a name="bc40025-type-of-member-membername-is-not-cls-compliant"></a>BC40025: ' ' üyesinin türü \<membername> CLS uyumlu değil

Bu üye için belirtilen veri türü, [dil bağımsızlık ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) 'nin (CLS) bir parçası değil. .NET Framework ve Visual Basic bu veri türünü desteklediği için bu, bileşeninizdeki bir hata değildir. Ancak, tamamen CLS uyumlu kodda yazılmış başka bir bileşen bu veri türünü desteklemeyebilir. Bu tür bir bileşen, bileşeniniz ile başarılı bir şekilde etkileşim kurabilmeyebilir.

 Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:

- [SByte Veri Türü](../data-types/sbyte-data-type.md)

- [UInteger Veri Türü](../data-types/uinteger-data-type.md)

- [ULong Veri Türü](../data-types/ulong-data-type.md)

- [UShort Veri Türü](../data-types/ushort-data-type.md)

 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **Hata kimliği:** BC40025

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Bileşeniniz yalnızca diğer .NET Framework bileşenleriyle arabirimlerinizde veya başka herhangi bir bileşenle arabirim içermiyorsa, herhangi bir şeyi değiştirmenize gerek yoktur.

- .NET Framework için yazılmayan bir bileşenle ilgili bir arabiriminiz varsa, bu veri türünü destekleyip desteklemediğine göre, yansıma veya belgelerinden birini belirleyebilirsiniz. Varsa, herhangi bir değişiklik yapmanız gerekmez.

- Bu veri türünü desteklemeyen bir bileşenle ilgili arabiriminiz varsa, bunu en yakın CLS uyumlu türle değiştirmelisiniz. Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz. Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .

- Otomasyon veya COM nesneleriyle arabirimsiz değilseniz, bazı türlerin .NET Framework farklı veri genişliklerine sahip olduğunu aklınızda bulundurun. Örneğin, `uint` genellikle diğer ortamlarda 16 bittir. Böyle bir bileşene 16 bitlik bir bağımsız değişken geçirirseniz, bunu `UShort` `UInteger` yönetilen Visual Basic kodunuzda değil olarak bildirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma](../../../framework/reflection-and-codedom/reflection.md)
