---
title: Bu dizi sabit veya geçici olarak kilitli
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 8d5e4add2d92a575126fb934ac3874a2e37685f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350783"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="ce262-102">Bu dizi sabit veya geçici olarak kilitli (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce262-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="ce262-103">Bu hatanın olası nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ce262-103">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="ce262-104">Sabit boyutlu bir dizinin öğelerinin sayısını değiştirmek için `ReDim` kullanma.</span><span class="sxs-lookup"><span data-stu-id="ce262-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
- <span data-ttu-id="ce262-105">Bir öğe için bağımsız değişken olarak geçirilen bir modül düzeyinde dinamik dizi yeniden boyutlama.</span><span class="sxs-lookup"><span data-stu-id="ce262-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="ce262-106">Bir öğe geçirilirse, işlem içindeki başvuru parametresi için bellek ayırmayı engellemek üzere dizi kilitlenir.</span><span class="sxs-lookup"><span data-stu-id="ce262-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
- <span data-ttu-id="ce262-107">Bir dizi içeren `Variant` değişkenine değer atamaya çalışılıyor, ancak `Variant` Şu anda kilitli.</span><span class="sxs-lookup"><span data-stu-id="ce262-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ce262-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ce262-108">To correct this error</span></span>  
  
1. <span data-ttu-id="ce262-109">`ReDim` (dizi bir yordam içinde bildirilirse) veya öğe sayısını belirtmeden (dizi modül düzeyinde bildirilmişse), özgün diziyi sabit yerine dinamik hale getirin.</span><span class="sxs-lookup"><span data-stu-id="ce262-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2. <span data-ttu-id="ce262-110">Modüldeki tüm yordamlarda görünür olduğundan, gerçekten öğeyi iletmeniz gerekip gerekmediğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="ce262-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3. <span data-ttu-id="ce262-111">`Variant` kilitlemenin ne olduğunu ve sorunu nasıl yaptığını saptayın.</span><span class="sxs-lookup"><span data-stu-id="ce262-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce262-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce262-112">See also</span></span>

- [<span data-ttu-id="ce262-113">Diziler</span><span class="sxs-lookup"><span data-stu-id="ce262-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
