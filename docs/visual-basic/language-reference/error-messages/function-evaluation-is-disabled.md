---
description: 'Şu konuda daha fazla bilgi edinin: BC30957: önceki bir işlev değerlendirmesi zaman aşımına uğradığından Işlev değerlendirmesi devre dışı bırakıldı'
title: Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 32e4b460a0334a542d59091bfc0b9a2337fdd089
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796190"
---
# <a name="bc30957-function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>BC30957: önceki bir işlev değerlendirmesi zaman aşımına uğradığından Işlev değerlendirmesi devre dışı bırakıldı

Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı. İşlev değerlendirmesini yeniden etkinleştirmek için tekrar adımla veya hata ayıklamayı yeniden başlatın.

 Visual Studio hata ayıklayıcısında bir ifade bir yordam çağrısını belirtir, ancak başka bir değerlendirme zaman aşımına uğradı.

 Bir yordam çağrısının zaman aşımına yönelik olası nedenleri sonsuz döngü veya sonsuz *döngü* içerir. Daha fazla bilgi için bkz.... [ Sonraki Ifade](../statements/for-next-statement.md).

 Sonsuz bir döngünün özel bir durumu *özyinelemedir*. Daha fazla bilgi için bkz. [özyinelemeli yordamlar](../../programming-guide/language-features/procedures/recursive-procedures.md).

 **Hata kimliği:** BC30957

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Mümkünse, önceki işlev değerlendirmesinin ne olduğunu ve bunun neden zaman aşımına uğramadığını saptayın. Aksi takdirde, bu hatayla yeniden karşılaşabilirsiniz.

2. Hata ayıklayıcıyı yeniden deneyin ya da Terminate ve hata ayıklamayı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](/visualstudio/debugger/debugger-feature-tour)
- [Hata Ayıklayıcısı ile Kodlarda gezinme](/visualstudio/debugger/navigating-through-code-with-the-debugger)
