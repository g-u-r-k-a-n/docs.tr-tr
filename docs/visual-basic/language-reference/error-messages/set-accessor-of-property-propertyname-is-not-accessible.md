---
title: "'<propertyname>' özelliğinin 'Set' erişimcisine erişilemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 3cf828eb5f11090a74a65388e2b89a191046a456
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162251"
---
# <a name="bc31102-set-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="1dd02-102">BC31102: ' ' özelliğinin ' Set ' erişimcisine \<propertyname> erişilemiyor</span><span class="sxs-lookup"><span data-stu-id="1dd02-102">BC31102: 'Set' accessor of property '\<propertyname>' is not accessible</span></span>

<span data-ttu-id="1dd02-103">Bir ifade, özelliğin yordamına erişimi olmayan bir özelliğin değerini depolamaya çalışır `Set` .</span><span class="sxs-lookup"><span data-stu-id="1dd02-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>

 <span data-ttu-id="1dd02-104">[Set deyimleri](../statements/set-statement.md) , [Property deyiminden](../statements/property-statement.md)daha kısıtlayıcı bir erişim düzeyiyle işaretlenmişse, aşağıdaki durumlarda özellik değerini ayarlama girişimi başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="1dd02-104">If the [Set Statement](../statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>

- <span data-ttu-id="1dd02-105">`Set`Ifade [Private](../modifiers/private.md) olarak işaretlenir ve çağıran kod, özelliğin tanımlandığı sınıfın veya yapının dışındadır.</span><span class="sxs-lookup"><span data-stu-id="1dd02-105">The `Set` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>

- <span data-ttu-id="1dd02-106">`Set`Ifade [korumalı](../modifiers/protected.md) olarak işaretlenir ve çağıran kod, özelliğin tanımlandığı sınıf veya yapı içinde ya da türetilmiş bir sınıfta değil.</span><span class="sxs-lookup"><span data-stu-id="1dd02-106">The `Set` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>

- <span data-ttu-id="1dd02-107">`Set`Ifade [arkadaş](../modifiers/friend.md) olarak işaretlenmiş ve çağıran kod, özelliğin tanımlandığı derlemede değil.</span><span class="sxs-lookup"><span data-stu-id="1dd02-107">The `Set` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>

 <span data-ttu-id="1dd02-108">**Hata kimliği:** BC31102</span><span class="sxs-lookup"><span data-stu-id="1dd02-108">**Error ID:** BC31102</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1dd02-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1dd02-109">To correct this error</span></span>

- <span data-ttu-id="1dd02-110">Özelliği tanımlayan kaynak kodun denetimine sahipseniz, `Set` yordamı özelliğin kendisiyle aynı erişim düzeyiyle bildirmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1dd02-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>

- <span data-ttu-id="1dd02-111">Özelliği tanımlayan kaynak kodu denetimine sahip değilseniz veya `Set` yordam erişim düzeyini özelliğin kendisinden daha fazla kısıtlamanız gerekiyorsa, özellik değerini ayarlayan ifadeyi özelliğe daha iyi erişimi olan bir kod bölgesine taşımayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="1dd02-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>

## <a name="see-also"></a><span data-ttu-id="1dd02-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dd02-112">See also</span></span>

- [<span data-ttu-id="1dd02-113">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="1dd02-113">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="1dd02-114">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="1dd02-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
