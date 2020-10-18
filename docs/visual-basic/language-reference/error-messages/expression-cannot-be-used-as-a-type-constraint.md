---
title: "'<expression>' tür kısıtlaması olarak kullanılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 6e55bfdc175f285b335512e64f4c2407bdb0e8c7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163096"
---
# <a name="bc32061-expression-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="e2cee-102">BC32061: ' \<expression> ' tür kısıtlaması olarak kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="e2cee-102">BC32061: '\<expression>' cannot be used as a type constraint</span></span>

<span data-ttu-id="e2cee-103">Kısıtlama listesi, bir tür parametresinde geçerli bir kısıtlamayı temsil eden bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="e2cee-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>

 <span data-ttu-id="e2cee-104">Bir kısıtlama listesi, tür parametresine geçirilen tür bağımsız değişkenine gereksinimleri uygular.</span><span class="sxs-lookup"><span data-stu-id="e2cee-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="e2cee-105">Aşağıdaki gereksinimleri herhangi bir kombinasyonda belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e2cee-105">You can specify the following requirements in any combination:</span></span>

- <span data-ttu-id="e2cee-106">Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="e2cee-106">The type argument must implement one or more interfaces</span></span>

- <span data-ttu-id="e2cee-107">Tür bağımsız değişkeni en çok bir sınıftan devralması gerekir</span><span class="sxs-lookup"><span data-stu-id="e2cee-107">The type argument must inherit from at most one class</span></span>

- <span data-ttu-id="e2cee-108">Tür bağımsız değişkeni, oluşturma kodunun erişebileceği parametresiz bir Oluşturucu kullanıma sunmalıdır ( `New` kısıtlamayı dahil)</span><span class="sxs-lookup"><span data-stu-id="e2cee-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>

 <span data-ttu-id="e2cee-109">Kısıtlama listesine belirli bir sınıf veya arabirim eklemezseniz, aşağıdakilerden birini belirterek daha genel bir gereksinim uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e2cee-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>

- <span data-ttu-id="e2cee-110">Tür bağımsız değişkeni bir değer türü olmalıdır ( `Structure` kısıtlamayı dahil)</span><span class="sxs-lookup"><span data-stu-id="e2cee-110">The type argument must be a value type (include the `Structure` constraint)</span></span>

- <span data-ttu-id="e2cee-111">Tür bağımsız değişkeni bir başvuru türü olmalıdır ( `Class` kısıtlamayı dahil)</span><span class="sxs-lookup"><span data-stu-id="e2cee-111">The type argument must be a reference type (include the `Class` constraint)</span></span>

 <span data-ttu-id="e2cee-112">`Structure` `Class` Aynı tür parametresi için hem hem de belirtemezsiniz ve birden çok kez belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2cee-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>

 <span data-ttu-id="e2cee-113">**Hata kimliği:** BC32061</span><span class="sxs-lookup"><span data-stu-id="e2cee-113">**Error ID:** BC32061</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e2cee-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e2cee-114">To correct this error</span></span>

- <span data-ttu-id="e2cee-115">İfadenin ve öğelerinin doğru yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e2cee-115">Verify that the expression and its elements are spelled correctly.</span></span>

- <span data-ttu-id="e2cee-116">İfade önceki gereksinimler listesine uygun değilse, kısıtlama listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="e2cee-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>

- <span data-ttu-id="e2cee-117">İfade bir arabirime veya sınıfa başvuruyorsa, derleyicinin bu arabirime veya sınıfa erişimi olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e2cee-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="e2cee-118">Adını nitelemeniz gerekebilir ve projenize bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e2cee-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="e2cee-119">Daha fazla bilgi için, bkz. [belirtilen öğelere başvurularda](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)"projelere başvurular".</span><span class="sxs-lookup"><span data-stu-id="e2cee-119">For more information, see "References to Projects" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2cee-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2cee-120">See also</span></span>

- [<span data-ttu-id="e2cee-121">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="e2cee-121">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="e2cee-122">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="e2cee-122">Value Types and Reference Types</span></span>](../../programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="e2cee-123">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="e2cee-123">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
