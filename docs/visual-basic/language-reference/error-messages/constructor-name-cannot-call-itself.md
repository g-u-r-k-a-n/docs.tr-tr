---
description: "Hakkında daha fazla bilgi edinin: BC30298: ' <name> ' Oluşturucusu kendisini çağıramaz"
title: Yapıcı '<name>' kendisini çağıramaz
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 486495eb822e3e3008382232091fe3923851f97c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796723"
---
# <a name="bc30298-constructor-name-cannot-call-itself"></a>BC30298: ' \<name> ' Oluşturucusu kendisini çağıramaz

`Sub New`Bir sınıf veya yapıdaki yordam kendisini çağırır.

 Bir oluşturucunun amacı, ilk oluşturulduğunda bir sınıfın veya yapının örneğini başlatmaktır. Bir sınıf veya yapı, hepsi farklı parametre listelerine sahip olmaları şartıyla çeşitli oluşturuculara sahip olabilir. Bir oluşturucunun kendisine ek olarak kendi işlevlerini yerine getirmek için başka bir Oluşturucu çağırması izin verilir. Ancak bir oluşturucunun kendisini çağırması anlamlı değildir ve aslında bu, izin verildiğinde sonsuz özyineleme oluşmasına neden olur.

 **Hata kimliği:** BC30298

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Çağrılan oluşturucunun parametre listesini denetleyin. Çağrıyı yapan oluşturucudan farklı olmalıdır.

2. Farklı bir Oluşturucu çağırmak istemiyorsanız, `Sub New` çağrıyı tamamen kaldırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
