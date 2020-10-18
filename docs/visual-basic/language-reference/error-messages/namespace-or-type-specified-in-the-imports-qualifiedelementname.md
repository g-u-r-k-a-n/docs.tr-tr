---
title: Imports '<qualifiedelementname>' içinde belirtilen ad alanı veya tür ortak üye içermiyor veya bulunamıyor
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 284a8c71fee8835f78ca5435932819fded1b1f30
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160138"
---
# <a name="bc40056-namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="cda8d-102">BC40056: Imports ' ' içinde belirtilen ad alanı veya tür \<qualifiedelementname> ortak üye içermiyor veya bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="cda8d-102">BC40056: Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="cda8d-103">Imports ' ' içinde belirtilen ad alanı veya tür \<qualifiedelementname> ortak üye içermiyor veya bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="cda8d-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="cda8d-104">Ad alanının veya türün tanımlandığından ve en az bir ortak üye içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cda8d-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="cda8d-105">Diğer ad adının başka diğer adlar içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cda8d-105">Make sure the alias name doesn't contain other aliases.</span></span>

<span data-ttu-id="cda8d-106">Bir `Imports` ifade, bulunamayan veya hiçbir üye tanımlamayan bir kapsayan öğe belirtiyor `Public` .</span><span class="sxs-lookup"><span data-stu-id="cda8d-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

<span data-ttu-id="cda8d-107">*Kapsayan bir öğe* bir Namespace, Class, Structure, Module, Interface veya Enumeration olabilir.</span><span class="sxs-lookup"><span data-stu-id="cda8d-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="cda8d-108">Kapsayan öğe, değişkenler, yordamlar veya içerilen diğer öğeler gibi Üyeler içerir.</span><span class="sxs-lookup"><span data-stu-id="cda8d-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

<span data-ttu-id="cda8d-109">İçeri aktarma amacı, kodunuzun ad alanına veya tür üyelerine, bunları nitelemek zorunda kalmadan erişmesine izin versağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="cda8d-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="cda8d-110">Projenizin ad alanına veya türe bir başvuru eklemesi de gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="cda8d-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="cda8d-111">Daha fazla bilgi için, bkz. "Içerilen öğeleri Içeri aktarma", [belirtilen öğelerin başvuruları](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="cda8d-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="cda8d-112">Derleyici belirtilen içeren öğeyi bulamazsa, onu kullanan başvuruları çözemez.</span><span class="sxs-lookup"><span data-stu-id="cda8d-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="cda8d-113">Öğe bulunursa ancak öğe hiçbir üye sunmadığında `Public` , hiçbir başvuru başarılı olmaz.</span><span class="sxs-lookup"><span data-stu-id="cda8d-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="cda8d-114">Her iki durumda da, öğesini içeri aktarmak anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="cda8d-114">In either case it is meaningless to import the element.</span></span>

<span data-ttu-id="cda8d-115">İçeren bir öğeyi içeri aktarıp buna bir içeri aktarma diğer adı atarsanız, başka bir öğeyi almak için bu içeri aktarma diğer adını kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="cda8d-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="cda8d-116">Aşağıdaki kod bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cda8d-116">The following code generates a compiler error.</span></span>

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

<span data-ttu-id="cda8d-117">**Hata kimliği:** BC40056</span><span class="sxs-lookup"><span data-stu-id="cda8d-117">**Error ID:** BC40056</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="cda8d-118">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="cda8d-118">To correct this error</span></span>

1. <span data-ttu-id="cda8d-119">İçeren öğenin projenizden erişilebilir olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="cda8d-119">Verify that the containing element is accessible from your project.</span></span>

2. <span data-ttu-id="cda8d-120">İçerilen öğe belirtiminin başka bir içeri aktarma ile herhangi bir içeri aktarma diğer adı içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cda8d-120">Verify that the specification of the containing element does not include any import alias from another import.</span></span>

3. <span data-ttu-id="cda8d-121">Kapsayan öğenin en az bir üye gösterdiğinden emin olun `Public` .</span><span class="sxs-lookup"><span data-stu-id="cda8d-121">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="cda8d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cda8d-122">See also</span></span>

- [<span data-ttu-id="cda8d-123">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="cda8d-123">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="cda8d-124">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="cda8d-124">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="cda8d-125">Geneldir</span><span class="sxs-lookup"><span data-stu-id="cda8d-125">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="cda8d-126">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="cda8d-126">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="cda8d-127">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="cda8d-127">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
