---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic dizi değişkeni başlatma'
title: 'Nasıl yapılır: Dizi Değişkeni Başlatma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 05cca98457a56db52ee99cfc4ac93c860da7a51d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427618"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="6194b-103">Nasıl yapılır: Visual Basic'te Dizi Değişkeni Başlatma</span><span class="sxs-lookup"><span data-stu-id="6194b-103">How to: Initialize an Array Variable in Visual Basic</span></span>

<span data-ttu-id="6194b-104">Bir yan tümcesine dizi değişmez değeri ekleyerek `New` ve dizinin başlangıç değerlerini belirterek bir dizi değişkenini başlatırsınız.</span><span class="sxs-lookup"><span data-stu-id="6194b-104">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="6194b-105">Türü belirtebilir veya dizi sabit değerindeki değerlerden çıkarsanamıyor izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6194b-105">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="6194b-106">Türün nasıl çıkarsandığına ilişkin daha fazla bilgi için, [diziler](index.md)Içindeki "başlangıç değerleriyle bir diziyi doldurma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="6194b-106">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="6194b-107">Dizi değişmezi kullanarak bir dizi değişkeni başlatmak için</span><span class="sxs-lookup"><span data-stu-id="6194b-107">To initialize an array variable by using an array literal</span></span>  
  
- <span data-ttu-id="6194b-108">`New`Yan tümcesinde veya dizi değerini atadığınızda, öğe değerlerini küme ayracı () içinde sağlayın `{}` .</span><span class="sxs-lookup"><span data-stu-id="6194b-108">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="6194b-109">Aşağıdaki örnek, türünde öğeleri olan bir dizi içeren bir değişkeni bildirmek, oluşturmak ve başlatmak için çeşitli yollar gösterir `Char` .</span><span class="sxs-lookup"><span data-stu-id="6194b-109">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     <span data-ttu-id="6194b-110">Her bir deyimden sonra oluşturulan dizi 3 uzunluğuna sahiptir ve dizin 0 ' dan başlayarak başlangıç değerlerini içeren dizin 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6194b-110">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="6194b-111">Hem üst sınırı hem de değerleri sağlarsanız, üst sınır aracılığıyla 0 dizininden her öğe için bir değer eklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6194b-111">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="6194b-112">Dizi sabit değerinde öğe değerleri sağlarsanız, dizin üst sınırını belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6194b-112">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="6194b-113">Üst sınır belirtilmemişse, dizi boyutu dizi sabit değerindeki değer sayısına göre algılanır.</span><span class="sxs-lookup"><span data-stu-id="6194b-113">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="6194b-114">Dizi değişmez değerlerini kullanarak çok boyutlu bir dizi değişkeni başlatmak için</span><span class="sxs-lookup"><span data-stu-id="6194b-114">To initialize a multidimensional array variable by using array literals</span></span>  
  
- <span data-ttu-id="6194b-115">Küme ayraçları içinde parantez () içinde iç içe değerler `{}` .</span><span class="sxs-lookup"><span data-stu-id="6194b-115">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="6194b-116">İç içe geçmiş dizi değişmez değerlerinin tümünün aynı türdeki ve uzunluktaki diziler olarak çıkardığına emin olun.</span><span class="sxs-lookup"><span data-stu-id="6194b-116">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="6194b-117">Aşağıdaki kod örneğinde çok boyutlu dizi başlatmanın birkaç örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6194b-117">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- <span data-ttu-id="6194b-118">Dizi sınırlarını açıkça belirtebilir veya dışarı bırakabilir ve derleyicinin dizi sınırlarını, dizi değişmez değerindeki değerlere göre çıkarmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6194b-118">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="6194b-119">Hem üst sınırı hem de değerleri sağlarsanız, her boyuttaki üst sınır aracılığıyla 0 dizininden her öğe için bir değer eklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6194b-119">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="6194b-120">Aşağıdaki örnek, türünde öğeleri olan iki boyutlu bir dizi içeren bir değişkeni bildirmek, oluşturmak ve başlatmak için çeşitli yollar gösterir `Short`</span><span class="sxs-lookup"><span data-stu-id="6194b-120">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     <span data-ttu-id="6194b-121">Her bir deyimden sonra oluşturulan dizi,,,,, ve dizinleri olan altı adet başlatılmış öğe içerir `(0,0)` `(0,1)` `(0,2)` `(1,0)` `(1,1)` `(1,2)` .</span><span class="sxs-lookup"><span data-stu-id="6194b-121">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="6194b-122">Her dizi konumu değeri içerir `10` .</span><span class="sxs-lookup"><span data-stu-id="6194b-122">Each array location contains the value `10`.</span></span>  
  
- <span data-ttu-id="6194b-123">Aşağıdaki örnek, çok boyutlu bir dizi aracılığıyla yinelenir.</span><span class="sxs-lookup"><span data-stu-id="6194b-123">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="6194b-124">Visual Basic yazılan bir Windows konsol uygulamasında kodu yönteminin içine yapıştırın `Sub Main()` .</span><span class="sxs-lookup"><span data-stu-id="6194b-124">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="6194b-125">Son açıklamalar çıktıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6194b-125">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="6194b-126">Dizi değişmez değerlerini kullanarak pürüzlü bir dizi değişkeni başlatmak için</span><span class="sxs-lookup"><span data-stu-id="6194b-126">To initialize a jagged array variable by using array literals</span></span>  
  
- <span data-ttu-id="6194b-127">Nesne değerlerini küme ayracı () içinde iç içe `{}` .</span><span class="sxs-lookup"><span data-stu-id="6194b-127">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="6194b-128">Ayrıca, farklı uzunluklardan oluşan dizileri belirten dizi sabit değerlerini iç içe geçirebilirsiniz, ancak pürüzlü bir dizi söz konusu olduğunda, iç içe geçmiş dizi değişmez değerlerinin parantez () içine alındığına emin olun `()` .</span><span class="sxs-lookup"><span data-stu-id="6194b-128">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="6194b-129">Parantezler, iç içe geçmiş dizi değişmez değerlerinin değerlendirilmesini zorlar ve ortaya çıkan diziler, pürüzlü dizinin başlangıç değerleri olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6194b-129">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="6194b-130">Aşağıdaki kod örneğinde, pürüzlü dizi başlatmanın iki örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6194b-130">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- <span data-ttu-id="6194b-131">Aşağıdaki örnek, pürüzlü bir dizi aracılığıyla yinelenir.</span><span class="sxs-lookup"><span data-stu-id="6194b-131">The following example iterates through a jagged array.</span></span> <span data-ttu-id="6194b-132">Visual Basic yazılan bir Windows konsol uygulamasında kodu yönteminin içine yapıştırın `Sub Main()` .</span><span class="sxs-lookup"><span data-stu-id="6194b-132">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="6194b-133">Koddaki son açıklamalar çıktıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6194b-133">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="6194b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6194b-134">See also</span></span>

- [<span data-ttu-id="6194b-135">Diziler</span><span class="sxs-lookup"><span data-stu-id="6194b-135">Arrays</span></span>](index.md)
- [<span data-ttu-id="6194b-136">Dizilerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="6194b-136">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
