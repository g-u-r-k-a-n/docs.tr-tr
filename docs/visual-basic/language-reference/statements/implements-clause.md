---
title: Implements Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: 46ab1a1148e8d73d91293aedfc407e5efdc7cfb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404569"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="ec6a5-102">Implements Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec6a5-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="ec6a5-103">Bir sınıf veya yapı üyesinin, arabirim içinde tanımlanmış bir üye için uygulama sağladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec6a5-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec6a5-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec6a5-104">Remarks</span></span>  
<span data-ttu-id="ec6a5-105">`Implements`Anahtar sözcüğü, [Implements ifadesiyle](implements-statement.md)aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="ec6a5-105">The `Implements` keyword is not the same as the [Implements Statement](implements-statement.md).</span></span> <span data-ttu-id="ec6a5-106">`Implements`Bir sınıf ya da yapının bir veya daha fazla arabirim uyguladığını belirtmek için ifadesini kullanın ve ardından her üye için `Implements` hangi arabirimin ve hangi üyenin uyguladığı, anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ec6a5-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="ec6a5-107">Bir sınıf veya yapı bir arabirim uygularsa, `Implements` [sınıf deyimden](class-statement.md) veya [Yapı deyimden](structure-statement.md)hemen sonra ifadesini içermesi gerekir ve arabirim tarafından tanımlanan tüm üyeleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ec6a5-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](class-statement.md) or [Structure Statement](structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="ec6a5-108">Yeniden uygulama</span><span class="sxs-lookup"><span data-stu-id="ec6a5-108">Reimplementation</span></span>  
<span data-ttu-id="ec6a5-109">Türetilmiş bir sınıfta, temel sınıfın zaten uygulanmış olduğu bir arabirim üyesini yeniden uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec6a5-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="ec6a5-110">Bu, aşağıdaki gibi temel sınıf üyesini geçersiz kılmadan farklıdır:</span><span class="sxs-lookup"><span data-stu-id="ec6a5-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="ec6a5-111">Temel sınıf üyesinin yeniden uygulanması için [geçersiz kılınabilir](../modifiers/overridable.md) olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ec6a5-111">The base class member does not need to be [Overridable](../modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="ec6a5-112">Üyeyi farklı bir adla yeniden uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec6a5-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="ec6a5-113">`Implements`Anahtar sözcüğü aşağıdaki bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ec6a5-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="ec6a5-114">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec6a5-114">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="ec6a5-115">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec6a5-115">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="ec6a5-116">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec6a5-116">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="ec6a5-117">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec6a5-117">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec6a5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec6a5-118">See also</span></span>

- [<span data-ttu-id="ec6a5-119">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec6a5-119">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="ec6a5-120">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec6a5-120">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="ec6a5-121">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec6a5-121">Class Statement</span></span>](class-statement.md)
- [<span data-ttu-id="ec6a5-122">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="ec6a5-122">Structure Statement</span></span>](structure-statement.md)
