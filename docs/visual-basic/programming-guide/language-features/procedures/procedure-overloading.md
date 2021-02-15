---
description: 'Daha fazla bilgi edinin: yordam aşırı yüklemesi (Visual Basic)'
title: Yordam Aşırı Yüklemesi
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 27e79e12153bc7ac6a9e3b3b5997a50c1c354195
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466646"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="8a9a9-103">Yordam Aşırı Yüklemesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a9a9-103">Procedure Overloading (Visual Basic)</span></span>

<span data-ttu-id="8a9a9-104">Bir yordamın *aşırı yüklenmesi* , aynı ad ancak farklı parametre listeleri kullanılarak birden çok sürümde tanımlanması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-104">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="8a9a9-105">Aşırı yükleme amacı, bir yordamın adına göre ayrım yapmadan daha yakından ilgili birkaç sürümünü tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-105">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="8a9a9-106">Bunu parametre listesini değiştirerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-106">You do this by varying the parameter list.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="8a9a9-107">Kuralları aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="8a9a9-107">Overloading Rules</span></span>

<span data-ttu-id="8a9a9-108">Bir yordamı aşırı yüklerken, aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="8a9a9-108">When you overload a procedure, the following rules apply:</span></span>

- <span data-ttu-id="8a9a9-109">**Aynı ad**.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-109">**Same Name**.</span></span> <span data-ttu-id="8a9a9-110">Her aşırı yüklenmiş sürüm aynı yordam adını kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-110">Each overloaded version must use the same procedure name.</span></span>

- <span data-ttu-id="8a9a9-111">**Farklı imza**.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-111">**Different Signature**.</span></span> <span data-ttu-id="8a9a9-112">Her aşırı yüklenmiş sürüm, aşağıdaki yönden en az birindeki diğer tüm aşırı yüklenmiş sürümlerden farklı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="8a9a9-112">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>

  - <span data-ttu-id="8a9a9-113">Parametre sayısı</span><span class="sxs-lookup"><span data-stu-id="8a9a9-113">Number of parameters</span></span>

  - <span data-ttu-id="8a9a9-114">Parametrelerin sırası</span><span class="sxs-lookup"><span data-stu-id="8a9a9-114">Order of the parameters</span></span>

  - <span data-ttu-id="8a9a9-115">Parametrelerin veri türleri</span><span class="sxs-lookup"><span data-stu-id="8a9a9-115">Data types of the parameters</span></span>

  - <span data-ttu-id="8a9a9-116">Tür parametrelerinin sayısı (genel yordam için)</span><span class="sxs-lookup"><span data-stu-id="8a9a9-116">Number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="8a9a9-117">Dönüş türü (yalnızca bir dönüştürme işleci için)</span><span class="sxs-lookup"><span data-stu-id="8a9a9-117">Return type (only for a conversion operator)</span></span>

  <span data-ttu-id="8a9a9-118">Yordam adı ile birlikte, önceki öğeler her topluca yordamın *imzası* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-118">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="8a9a9-119">Aşırı yüklenmiş bir yordamı çağırdığınızda, derleyici, çağrının tanımıyla doğru şekilde eşleşip eşleşmediğini denetlemek için imzayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-119">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>

- <span data-ttu-id="8a9a9-120">**İmzanın bir parçası değil öğeleri**.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-120">**Items Not Part of Signature**.</span></span> <span data-ttu-id="8a9a9-121">İmzayı değiştirmeden bir yordamı aşırı yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-121">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="8a9a9-122">Özellikle, aşağıdaki öğelerden yalnızca birini veya birkaçını değiştirerek bir yordamı aşırı yükleyemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="8a9a9-122">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>

  - <span data-ttu-id="8a9a9-123">, Ve gibi yordam değiştirici anahtar `Public` sözcükleri `Shared``Static`</span><span class="sxs-lookup"><span data-stu-id="8a9a9-123">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>

  - <span data-ttu-id="8a9a9-124">Parametre veya tür parametre adları</span><span class="sxs-lookup"><span data-stu-id="8a9a9-124">Parameter or type parameter names</span></span>

  - <span data-ttu-id="8a9a9-125">Tür parametresi kısıtlamaları (genel yordam için)</span><span class="sxs-lookup"><span data-stu-id="8a9a9-125">Type parameter constraints (for a generic procedure)</span></span>

  - <span data-ttu-id="8a9a9-126">Ve gibi parametre değiştirici anahtar sözcükleri `ByRef``Optional`</span><span class="sxs-lookup"><span data-stu-id="8a9a9-126">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>

  - <span data-ttu-id="8a9a9-127">Değer döndürüp döndürmeksizin</span><span class="sxs-lookup"><span data-stu-id="8a9a9-127">Whether it returns a value</span></span>

  - <span data-ttu-id="8a9a9-128">Dönüş değerinin veri türü (dönüştürme işleci dışında)</span><span class="sxs-lookup"><span data-stu-id="8a9a9-128">The data type of the return value (except for a conversion operator)</span></span>

  <span data-ttu-id="8a9a9-129">Yukarıdaki listede yer olan öğeler imzaya ait değildir.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-129">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="8a9a9-130">Bunları aşırı yüklenmiş sürümler arasında ayrım yapmak için kullanamazsınız, ancak bunları imzalarıyla düzgün şekilde ayırt edilen aşırı yüklenmiş sürümler arasında değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-130">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>

- <span data-ttu-id="8a9a9-131">**Geç bağlantılı bağımsız değişkenler**.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-131">**Late-Bound Arguments**.</span></span> <span data-ttu-id="8a9a9-132">Geç bağlantılı bir nesne değişkenini aşırı yüklenmiş bir sürüme geçirmek istiyorsanız, uygun parametreyi olarak bildirmeniz gerekir <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="8a9a9-132">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>

## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="8a9a9-133">Yordamın birden çok sürümü</span><span class="sxs-lookup"><span data-stu-id="8a9a9-133">Multiple Versions of a Procedure</span></span>

<span data-ttu-id="8a9a9-134">Bir `Sub` müşterinin bakiyesine karşı bir işlem göndermek için bir yordam yazıyorsanız ve müşteriye ada veya hesap numarasına göre başvurmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-134">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="8a9a9-135">Buna uyum sağlamak için, `Sub` Aşağıdaki örnekte olduğu gibi iki farklı yordam tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8a9a9-135">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a><span data-ttu-id="8a9a9-136">Aşırı yüklenmiş sürümler</span><span class="sxs-lookup"><span data-stu-id="8a9a9-136">Overloaded Versions</span></span>

<span data-ttu-id="8a9a9-137">Bir alternatif, tek bir yordam adının aşırı yüklenmesine yönelik bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-137">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="8a9a9-138">Her bir parametre listesi için yordamın bir sürümünü tanımlamak üzere [overloads](../../../language-reference/modifiers/overloads.md) anahtar sözcüğünü aşağıda gösterildiği gibi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8a9a9-138">You can use the [Overloads](../../../language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a><span data-ttu-id="8a9a9-139">Ek aşırı yüklemeler</span><span class="sxs-lookup"><span data-stu-id="8a9a9-139">Additional Overloads</span></span>

<span data-ttu-id="8a9a9-140">Ya da veya ' de bir işlem tutarını kabul etmek isterseniz `Decimal` `Single` , `post` Bu varyasyon için izin vermek için daha fazla tekrar yükleme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-140">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="8a9a9-141">Yukarıdaki örnekteki aşırı yüklemelerin her birini yaptıysanız, `Sub` hepsi aynı ada sahip ancak dört farklı imzaya sahip dört yordamımız olur.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-141">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>

## <a name="advantages-of-overloading"></a><span data-ttu-id="8a9a9-142">Aşırı yükleme avantajları</span><span class="sxs-lookup"><span data-stu-id="8a9a9-142">Advantages of Overloading</span></span>

<span data-ttu-id="8a9a9-143">Bir yordamı aşırı yükleme avantajı, çağrının esnekliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-143">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="8a9a9-144">`post`Yukarıdaki örnekte açıklanan yordamı kullanmak için, çağıran kod müşteri kimliğini bir veya olarak alabilir `String` `Integer` ve ardından aynı yordamı her iki durumda da çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-144">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="8a9a9-145">Aşağıdaki örnekte bu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8a9a9-145">The following example illustrates this:</span></span>

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a><span data-ttu-id="8a9a9-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a9a9-146">See also</span></span>

- [<span data-ttu-id="8a9a9-147">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8a9a9-147">Procedures</span></span>](./index.md)
- [<span data-ttu-id="8a9a9-148">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama</span><span class="sxs-lookup"><span data-stu-id="8a9a9-148">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="8a9a9-149">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="8a9a9-149">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="8a9a9-150">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="8a9a9-150">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="8a9a9-151">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="8a9a9-151">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="8a9a9-152">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="8a9a9-152">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="8a9a9-153">Aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="8a9a9-153">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="8a9a9-154">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="8a9a9-154">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="8a9a9-155">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="8a9a9-155">Generic Types in Visual Basic</span></span>](../data-types/generic-types.md)
