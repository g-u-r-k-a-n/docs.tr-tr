---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic genel türler (Visual Basic)'
title: Genel Türler
ms.date: 07/20/2015
helpviewer_keywords:
- generic interfaces
- data type arguments [Visual Basic], defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures [Visual Basic], generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes [Visual Basic], Visual Basic
- parameters [Visual Basic], type
- type arguments
- interfaces [Visual Basic], generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generic structures [Visual Basic]
- generic classes [Visual Basic]
- type parameters
- data type arguments
- structures [Visual Basic], generic
- parameters [Visual Basic], data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
ms.openlocfilehash: 1164513825240b1e83fbce2aeb6478430b0bc250
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428551"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a><span data-ttu-id="5d2f6-103">Visual Basic'de Genel Türler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d2f6-103">Generic Types in Visual Basic (Visual Basic)</span></span>

<span data-ttu-id="5d2f6-104">*Genel tür* , çeşitli veri türleri için aynı işlevselliği gerçekleştirmeye uyum sağlayan tek bir programlama öğesidir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-104">A *generic type* is a single programming element that adapts to perform the same functionality for a variety of data types.</span></span> <span data-ttu-id="5d2f6-105">Genel bir sınıf veya yordam tanımladığınızda, bu işlevi gerçekleştirmek isteyebileceğiniz her bir veri türü için ayrı bir sürüm tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-105">When you define a generic class or procedure, you do not have to define a separate version for each data type for which you might want to perform that functionality.</span></span>  
  
 <span data-ttu-id="5d2f6-106">Benzerleme vurguladı, çıkarılabilir kafaları olan bir screwdriver kümesidir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-106">An analogy is a screwdriver set with removable heads.</span></span> <span data-ttu-id="5d2f6-107">Vidalı 'yi inceleyerek, bu vidalı için doğru kafa (slosıya, çapraz, starred) açmanız ve seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-107">You inspect the screw you need to turn and select the correct head for that screw (slotted, crossed, starred).</span></span> <span data-ttu-id="5d2f6-108">Screwdriver işleyicisine doğru bir baş ekledikten sonra, vida ' ı etkinleştirerek, Screwdriver ile tam olarak aynı işlevi gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-108">Once you insert the correct head in the screwdriver handle, you perform the exact same function with the screwdriver, namely turning the screw.</span></span>  
  
 ![Farklı kafaları olan bir screwdriver kümesi diyagramı.](./media/generic-types/generic-screwdriver-set.gif)  
  
 <span data-ttu-id="5d2f6-110">Genel bir tür tanımladığınızda, bir veya daha fazla veri türüyle parametreleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-110">When you define a generic type, you parameterize it with one or more data types.</span></span> <span data-ttu-id="5d2f6-111">Bu, veri türlerini gereksinimlerine uyarlamak için kodun kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-111">This allows the using code to tailor the data types to its requirements.</span></span> <span data-ttu-id="5d2f6-112">Kodunuz, her biri farklı veri türleri kümesi üzerinde davranan genel öğeden birkaç farklı programlama öğesi bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-112">Your code can declare several different programming elements from the generic element, each one acting on a different set of data types.</span></span> <span data-ttu-id="5d2f6-113">Ancak, görüntülenen öğeler, kullandıkları veri türleri ne olduğuna bakılmaksızın özdeş mantığı gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-113">But the declared elements all perform the identical logic, no matter what data types they are using.</span></span>  
  
 <span data-ttu-id="5d2f6-114">Örneğin, gibi belirli bir veri türü üzerinde çalışan bir sıra sınıfı oluşturmak ve kullanmak isteyebilirsiniz `String` .</span><span class="sxs-lookup"><span data-stu-id="5d2f6-114">For example, you might want to create and use a queue class that operates on a specific data type such as `String`.</span></span> <span data-ttu-id="5d2f6-115"><xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, bu tür bir sınıfı ' den bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-115">You can declare such a class from <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 <span data-ttu-id="5d2f6-116">Artık `stringQ` değerlerle özel olarak çalışmak için ' i kullanabilirsiniz `String` .</span><span class="sxs-lookup"><span data-stu-id="5d2f6-116">You can now use `stringQ` to work exclusively with `String` values.</span></span> <span data-ttu-id="5d2f6-117">`stringQ` `String` , Değerleri için genelleştirilmesi yerine için özel olduğundan `Object` , geç bağlama veya tür dönüştürme izniniz yoktur.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-117">Because `stringQ` is specific for `String` instead of being generalized for `Object` values, you do not have late binding or type conversion.</span></span> <span data-ttu-id="5d2f6-118">Bu, yürütme süresini kaydeder ve çalışma zamanı hatalarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-118">This saves execution time and reduces run-time errors.</span></span>  
  
 <span data-ttu-id="5d2f6-119">Genel bir tür kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: genel bir sınıf kullanma](how-to-use-a-generic-class.md).</span><span class="sxs-lookup"><span data-stu-id="5d2f6-119">For more information on using a generic type, see [How to: Use a Generic Class](how-to-use-a-generic-class.md).</span></span>  
  
## <a name="example-of-a-generic-class"></a><span data-ttu-id="5d2f6-120">Genel sınıf örneği</span><span class="sxs-lookup"><span data-stu-id="5d2f6-120">Example of a Generic Class</span></span>  

 <span data-ttu-id="5d2f6-121">Aşağıdaki örnek, bir genel sınıfın iskelet tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-121">The following example shows a skeleton definition of a generic class.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 <span data-ttu-id="5d2f6-122">Önceki çatı içinde, `t` bir *tür parametresidir*, diğer bir deyişle, sınıfı bildirdiğinizde sağladığınız veri türü için bir yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-122">In the preceding skeleton, `t` is a *type parameter*, that is, a placeholder for a data type that you supply when you declare the class.</span></span> <span data-ttu-id="5d2f6-123">Kodunuzun başka bir yerinde, `classHolder` için çeşitli veri türleri sunarak çeşitli sürümlerini bildirebilirsiniz `t` .</span><span class="sxs-lookup"><span data-stu-id="5d2f6-123">Elsewhere in your code, you can declare various versions of `classHolder` by supplying various data types for `t`.</span></span> <span data-ttu-id="5d2f6-124">Aşağıdaki örnek, bu iki bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-124">The following example shows two such declarations.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 <span data-ttu-id="5d2f6-125">Önceki deyimler, belirli bir türün tür parametresinin yerini aldığı *oluşturulan sınıfları* bildirir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-125">The preceding statements declare *constructed classes*, in which a specific type replaces the type parameter.</span></span> <span data-ttu-id="5d2f6-126">Bu değişiklik, oluşturulan sınıf içindeki kod boyunca yayılır.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-126">This replacement is propagated throughout the code within the constructed class.</span></span> <span data-ttu-id="5d2f6-127">Aşağıdaki örnek, `processNewItem` yordamının içinde nasıl göründüğünü gösterir `integerClass` .</span><span class="sxs-lookup"><span data-stu-id="5d2f6-127">The following example shows what the `processNewItem` procedure looks like in `integerClass`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 <span data-ttu-id="5d2f6-128">Daha kapsamlı bir örnek için bkz. [nasıl yapılır: farklı veri türlerinde özdeş Işlevsellik sağlayabilen bir sınıf tanımlama](how-to-define-a-class-that-can-provide-identical-functionality.md).</span><span class="sxs-lookup"><span data-stu-id="5d2f6-128">For a more complete example, see [How to: Define a Class That Can Provide Identical Functionality on Different Data Types](how-to-define-a-class-that-can-provide-identical-functionality.md).</span></span>  
  
## <a name="eligible-programming-elements"></a><span data-ttu-id="5d2f6-129">Uygun programlama öğeleri</span><span class="sxs-lookup"><span data-stu-id="5d2f6-129">Eligible Programming Elements</span></span>  

 <span data-ttu-id="5d2f6-130">Genel sınıfları, yapıları, arabirimleri, yordamları ve temsilcileri tanımlayabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-130">You can define and use generic classes, structures, interfaces, procedures, and delegates.</span></span> <span data-ttu-id="5d2f6-131">.NET Framework, yaygın olarak kullanılan genel öğeleri temsil eden çeşitli genel sınıfları, yapıları ve arabirimleri tanımladığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-131">Note that the .NET Framework defines several generic classes, structures, and interfaces that represent commonly used generic elements.</span></span> <span data-ttu-id="5d2f6-132"><xref:System.Collections.Generic?displayProperty=nameWithType>Ad alanı sözlükler, listeleri, kuyrukları ve yığınları sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-132">The <xref:System.Collections.Generic?displayProperty=nameWithType> namespace provides dictionaries, lists, queues, and stacks.</span></span> <span data-ttu-id="5d2f6-133">Kendi genel öğesini tanımlamadan önce, ' de zaten kullanılabilir olup olmadığını görün <xref:System.Collections.Generic?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5d2f6-133">Before defining your own generic element, see if it is already available in <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="5d2f6-134">Yordamlar türler değildir, ancak genel yordamları tanımlayabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-134">Procedures are not types, but you can define and use generic procedures.</span></span> <span data-ttu-id="5d2f6-135">Bkz. [Visual Basic genel yordamlar](generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5d2f6-135">See [Generic Procedures in Visual Basic](generic-procedures.md).</span></span>  
  
## <a name="advantages-of-generic-types"></a><span data-ttu-id="5d2f6-136">Genel türlerin avantajları</span><span class="sxs-lookup"><span data-stu-id="5d2f6-136">Advantages of Generic Types</span></span>  

 <span data-ttu-id="5d2f6-137">Genel bir tür, her biri belirli bir veri türü üzerinde çalışan birkaç farklı programlama öğesi bildirmek için temel görevi görür.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-137">A generic type serves as a basis for declaring several different programming elements, each of which operates on a specific data type.</span></span> <span data-ttu-id="5d2f6-138">Genel tür alternatifleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5d2f6-138">The alternatives to a generic type are:</span></span>  
  
1. <span data-ttu-id="5d2f6-139">Veri türünde çalışan tek bir tür `Object` .</span><span class="sxs-lookup"><span data-stu-id="5d2f6-139">A single type operating on the `Object` data type.</span></span>  
  
2. <span data-ttu-id="5d2f6-140">Türün *türüne özgü* bir dizi, her sürüm tek tek kodlanmış ve, gibi belirli bir veri türü üzerinde, `String` veya gibi `Integer` Kullanıcı tanımlı bir tür `customer` .</span><span class="sxs-lookup"><span data-stu-id="5d2f6-140">A set of *type-specific* versions of the type, each version individually coded and operating on one specific data type such as `String`, `Integer`, or a user-defined type such as `customer`.</span></span>  
  
 <span data-ttu-id="5d2f6-141">Genel bir tür, bu alternatifler üzerinde aşağıdaki avantajlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5d2f6-141">A generic type has the following advantages over these alternatives:</span></span>  
  
- <span data-ttu-id="5d2f6-142">**Tür güvenliği.**</span><span class="sxs-lookup"><span data-stu-id="5d2f6-142">**Type Safety.**</span></span> <span data-ttu-id="5d2f6-143">Genel türler derleme zamanı tür denetimini uygular.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-143">Generic types enforce compile-time type checking.</span></span> <span data-ttu-id="5d2f6-144">`Object`Herhangi bir veri türünü kabul etmek için türler ve bir giriş veri türünün kabul edilebilir olup olmadığını denetlemek için kod yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-144">Types based on `Object` accept any data type, and you must write code to check whether an input data type is acceptable.</span></span> <span data-ttu-id="5d2f6-145">Genel türlerle, derleyici çalışma zamanından önce tür uyuşmazlıkları yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-145">With generic types, the compiler can catch type mismatches before run time.</span></span>  
  
- <span data-ttu-id="5d2f6-146">**Mının.**</span><span class="sxs-lookup"><span data-stu-id="5d2f6-146">**Performance.**</span></span> <span data-ttu-id="5d2f6-147">Her biri bir veri türü için *özelleştirilmediği* için genel türler, verileri *Box* ve serbest bırakmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-147">Generic types do not have to *box* and *unbox* data, because each one is specialized for one data type.</span></span> <span data-ttu-id="5d2f6-148">`Object`Giriş veri türlerine göre `Object` , çıkış için hedeflenen verileri dönüştürmek ve bunları kaldırmak için gereken işlemler.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-148">Operations based on `Object` must box input data types to convert them to `Object` and unbox data destined for output.</span></span> <span data-ttu-id="5d2f6-149">Kutulama ve kutudan çıkarma performansı azaltır.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-149">Boxing and unboxing reduce performance.</span></span>  
  
     <span data-ttu-id="5d2f6-150">' Ye dayalı türler `Object` de geç bağlı olduğundan, üyelerine erişim çalışma zamanında ek kod gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-150">Types based on `Object` are also late-bound, which means that accessing their members requires extra code at run time.</span></span> <span data-ttu-id="5d2f6-151">Bu ayrıca performansı azaltır.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-151">This also reduces performance.</span></span>  
  
- <span data-ttu-id="5d2f6-152">**Kod birleştirme.**</span><span class="sxs-lookup"><span data-stu-id="5d2f6-152">**Code Consolidation.**</span></span> <span data-ttu-id="5d2f6-153">Genel bir türdeki kodun yalnızca bir kez tanımlanması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-153">The code in a generic type has to be defined only once.</span></span> <span data-ttu-id="5d2f6-154">Bir türün tür özgü sürümlerinin bir kümesine, her sürümde aynı kod çoğaltılmalıdır ve bu sürüm için tek fark aynı şekilde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-154">A set of type-specific versions of a type must replicate the same code in each version, with the only difference being the specific data type for that version.</span></span> <span data-ttu-id="5d2f6-155">Genel türler ile, türe özgü sürümlerin hepsi özgün genel türden oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-155">With generic types, the type-specific versions are all generated from the original generic type.</span></span>  
  
- <span data-ttu-id="5d2f6-156">**Kod yeniden kullanımı.**</span><span class="sxs-lookup"><span data-stu-id="5d2f6-156">**Code Reuse.**</span></span> <span data-ttu-id="5d2f6-157">Belirli bir veri türüne bağımlı olmayan kod, genel ise çeşitli veri türleriyle yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-157">Code that does not depend on a particular data type can be reused with various data types if it is generic.</span></span> <span data-ttu-id="5d2f6-158">Genellikle, ilk olarak tahmin etmemiş olduğunuz bir veri türüyle bile onu yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-158">You can often reuse it even with a data type that you did not originally predict.</span></span>  
  
- <span data-ttu-id="5d2f6-159">**IDE desteği.**</span><span class="sxs-lookup"><span data-stu-id="5d2f6-159">**IDE Support.**</span></span> <span data-ttu-id="5d2f6-160">Genel bir türden belirtilen oluşturulmuş bir tür kullandığınızda tümleşik geliştirme ortamı (IDE), kodunuzu geliştirirken daha fazla destek verebilir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-160">When you use a constructed type declared from a generic type, the integrated development environment (IDE) can give you more support while you are developing your code.</span></span> <span data-ttu-id="5d2f6-161">Örneğin, IntelliSense, bir oluşturucuya veya yöntemine bir bağımsız değişken için tür özgü seçenekler gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-161">For example, IntelliSense can show you the type-specific options for an argument to a constructor or method.</span></span>  
  
- <span data-ttu-id="5d2f6-162">**Genel algoritmalar.**</span><span class="sxs-lookup"><span data-stu-id="5d2f6-162">**Generic Algorithms.**</span></span> <span data-ttu-id="5d2f6-163">Tür bağımsız olan soyut algoritmalar genel türler için iyi adaylardır.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-163">Abstract algorithms that are type-independent are good candidates for generic types.</span></span> <span data-ttu-id="5d2f6-164">Örneğin, arabirimini kullanarak öğeleri sıralayan genel yordam, <xref:System.IComparable> uygulayan herhangi bir veri türü ile kullanılabilir <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="5d2f6-164">For example, a generic procedure that sorts items using the <xref:System.IComparable> interface can be used with any data type that implements <xref:System.IComparable>.</span></span>  
  
## <a name="constraints"></a><span data-ttu-id="5d2f6-165">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="5d2f6-165">Constraints</span></span>  

 <span data-ttu-id="5d2f6-166">Genel tür tanımındaki kodun mümkün olduğunca bağımsız olması gerekir olsa da, genel türündefinizin verilen herhangi bir veri türünün belirli bir özelliğini sağlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-166">Although the code in a generic type definition should be as type-independent as possible, you might need to require a certain capability of any data type supplied to your generic type.</span></span> <span data-ttu-id="5d2f6-167">Örneğin, iki öğeyi sıralama veya harmanlama amacıyla karşılaştırmak istiyorsanız, veri türlerinin arabirimini uygulaması gerekir <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="5d2f6-167">For example, if you want to compare two items for the purpose of sorting or collating, their data type must implement the <xref:System.IComparable> interface.</span></span> <span data-ttu-id="5d2f6-168">Tür parametresine bir *kısıtlama* ekleyerek bu gereksinimi zorunlu kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-168">You can enforce this requirement by adding a *constraint* to the type parameter.</span></span>  
  
### <a name="example-of-a-constraint"></a><span data-ttu-id="5d2f6-169">Kısıtlama örneği</span><span class="sxs-lookup"><span data-stu-id="5d2f6-169">Example of a Constraint</span></span>  

 <span data-ttu-id="5d2f6-170">Aşağıdaki örnek, tür bağımsız değişkeninin uygulanmasını gerektiren kısıtlama içeren bir sınıfın iskelet tanımını gösterir <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="5d2f6-170">The following example shows a skeleton definition of a class with a constraint that requires the type argument to implement <xref:System.IComparable>.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 <span data-ttu-id="5d2f6-171">Sonraki kod, uygulamayan bir tür sağlayan bir sınıf oluşturmaya çalışırsa `itemManager` <xref:System.IComparable> , derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-171">If subsequent code attempts to construct a class from `itemManager` supplying a type that does not implement <xref:System.IComparable>, the compiler signals an error.</span></span>  
  
### <a name="types-of-constraints"></a><span data-ttu-id="5d2f6-172">Kısıtlama türleri</span><span class="sxs-lookup"><span data-stu-id="5d2f6-172">Types of Constraints</span></span>  

 <span data-ttu-id="5d2f6-173">Kısıtlamalarınız herhangi bir kombinasyonda aşağıdaki gereksinimleri belirtebilir:</span><span class="sxs-lookup"><span data-stu-id="5d2f6-173">Your constraint can specify the following requirements in any combination:</span></span>  
  
- <span data-ttu-id="5d2f6-174">Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır</span><span class="sxs-lookup"><span data-stu-id="5d2f6-174">The type argument must implement one or more interfaces</span></span>  
  
- <span data-ttu-id="5d2f6-175">Tür bağımsız değişkeni, en fazla bir sınıfta bulunan veya ondan devralma türünden olmalıdır</span><span class="sxs-lookup"><span data-stu-id="5d2f6-175">The type argument must be of the type of, or inherit from, at most one class</span></span>  
  
- <span data-ttu-id="5d2f6-176">Tür bağımsız değişkeni, içinden nesneler oluşturan koda erişilebilen parametresiz bir oluşturucuyu kullanıma sunmalıdır</span><span class="sxs-lookup"><span data-stu-id="5d2f6-176">The type argument must expose a parameterless constructor accessible to the code that creates objects from it</span></span>  
  
- <span data-ttu-id="5d2f6-177">Tür bağımsız değişkeni bir *başvuru türü* olmalı veya bir *değer türü* olmalıdır</span><span class="sxs-lookup"><span data-stu-id="5d2f6-177">The type argument must be a *reference type*, or it must be a *value type*</span></span>  
  
 <span data-ttu-id="5d2f6-178">Birden fazla gereksinim belirlemeniz gerekiyorsa, küme ayracı () içinde virgülle ayrılmış bir *kısıtlama listesi* kullanırsınız `{ }` .</span><span class="sxs-lookup"><span data-stu-id="5d2f6-178">If you need to impose more than one requirement, you use a comma-separated *constraint list* inside braces (`{ }`).</span></span> <span data-ttu-id="5d2f6-179">Erişilebilir bir Oluşturucu istemek için, [Yeni işleç](../../../language-reference/operators/new-operator.md) anahtar sözcüğünü listeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-179">To require an accessible constructor, you include the [New Operator](../../../language-reference/operators/new-operator.md) keyword in the list.</span></span> <span data-ttu-id="5d2f6-180">Bir başvuru türü gerektirmek için, `Class` anahtar sözcüğünü dahil edersiniz; bir değer türü gerektirmek için anahtar sözcüğünü dahil edersiniz `Structure` .</span><span class="sxs-lookup"><span data-stu-id="5d2f6-180">To require a reference type, you include the `Class` keyword; to require a value type, you include the `Structure` keyword.</span></span>  
  
 <span data-ttu-id="5d2f6-181">Kısıtlamalar hakkında daha fazla bilgi için bkz. [tür listesi](../../../language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="5d2f6-181">For more information on constraints, see [Type List](../../../language-reference/statements/type-list.md).</span></span>  
  
### <a name="example-of-multiple-constraints"></a><span data-ttu-id="5d2f6-182">Birden çok kısıtlama örneği</span><span class="sxs-lookup"><span data-stu-id="5d2f6-182">Example of Multiple Constraints</span></span>  

 <span data-ttu-id="5d2f6-183">Aşağıdaki örnek, tür parametresinde kısıtlama listesi olan bir genel sınıfın iskelet tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-183">The following example shows a skeleton definition of a generic class with a constraint list on the type parameter.</span></span> <span data-ttu-id="5d2f6-184">Bu sınıfın bir örneğini oluşturan kodda, tür bağımsız değişkeni hem hem de <xref:System.IComparable> <xref:System.IDisposable> arabirimlerini uygulamalıdır, bir başvuru türü olmalıdır ve erişilebilir parametresiz bir Oluşturucu kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-184">In the code that creates an instance of this class, the type argument must implement both the <xref:System.IComparable> and <xref:System.IDisposable> interfaces, be a reference type, and expose an accessible parameterless constructor.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a><span data-ttu-id="5d2f6-185">Önemli koşullar</span><span class="sxs-lookup"><span data-stu-id="5d2f6-185">Important Terms</span></span>  

 <span data-ttu-id="5d2f6-186">Genel türler aşağıdaki terimleri sunar ve kullanır:</span><span class="sxs-lookup"><span data-stu-id="5d2f6-186">Generic types introduce and use the following terms:</span></span>  
  
- <span data-ttu-id="5d2f6-187">*Genel tür*.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-187">*Generic Type*.</span></span> <span data-ttu-id="5d2f6-188">Bir sınıf, yapı, arabirim, yordam veya temsilci için en az bir veri türü sağladığınız temsilcinin tanımı.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-188">A definition of a class, structure, interface, procedure, or delegate for which you supply at least one data type when you declare it.</span></span>  
  
- <span data-ttu-id="5d2f6-189">*Tür parametresi*.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-189">*Type Parameter*.</span></span> <span data-ttu-id="5d2f6-190">Genel tür tanımında, türü bildirdiğinizde sağladığınız veri türü için yer tutucu.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-190">In a generic type definition, a placeholder for a data type you supply when you declare the type.</span></span>  
  
- <span data-ttu-id="5d2f6-191">*Tür bağımsız değişkeni*.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-191">*Type Argument*.</span></span> <span data-ttu-id="5d2f6-192">Genel bir türden oluşturulmuş bir tür bildirdiğinizde bir tür parametresini değiştiren belirli bir veri türü.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-192">A specific data type that replaces a type parameter when you declare a constructed type from a generic type.</span></span>  
  
- <span data-ttu-id="5d2f6-193">*Kısıtlama*.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-193">*Constraint*.</span></span> <span data-ttu-id="5d2f6-194">Bir tür parametresindeki, için sağlayabilmeniz gereken tür bağımsız değişkenini kısıtlayan bir koşul.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-194">A condition on a type parameter that restricts the type argument you can supply for it.</span></span> <span data-ttu-id="5d2f6-195">Bir kısıtlama, tür bağımsız değişkeninin belirli bir arabirim uygulaması, belirli bir sınıftan olması veya devralması, erişilebilir parametresiz bir oluşturucuya sahip olması veya bir başvuru türü ya da bir değer türü olması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-195">A constraint can require that the type argument must implement a particular interface, be or inherit from a particular class, have an accessible parameterless constructor, or be a reference type or a value type.</span></span> <span data-ttu-id="5d2f6-196">Bu kısıtlamaları birleştirebilirsiniz, ancak en fazla bir sınıf belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-196">You can combine these constraints, but you can specify at most one class.</span></span>  
  
- <span data-ttu-id="5d2f6-197">*Oluşturulan tür*.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-197">*Constructed Type*.</span></span> <span data-ttu-id="5d2f6-198">Tür parametreleri için tür bağımsız değişkenleri sağlayarak genel bir türden belirtilen bir sınıf, yapı, arabirim, yordam veya temsilci.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-198">A class, structure, interface, procedure, or delegate declared from a generic type by supplying type arguments for its type parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d2f6-199">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d2f6-199">See also</span></span>

- [<span data-ttu-id="5d2f6-200">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="5d2f6-200">Data Types</span></span>](index.md)
- [<span data-ttu-id="5d2f6-201">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="5d2f6-201">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="5d2f6-202">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="5d2f6-202">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="5d2f6-203">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="5d2f6-203">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="5d2f6-204">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="5d2f6-204">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="5d2f6-205">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="5d2f6-205">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="5d2f6-206">Durumunu</span><span class="sxs-lookup"><span data-stu-id="5d2f6-206">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="5d2f6-207">Gerektiği</span><span class="sxs-lookup"><span data-stu-id="5d2f6-207">As</span></span>](../../../language-reference/statements/as-clause.md)
- [<span data-ttu-id="5d2f6-208">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5d2f6-208">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="5d2f6-209">Kovaryans ve değişken sapması</span><span class="sxs-lookup"><span data-stu-id="5d2f6-209">Covariance and Contravariance</span></span>](../../concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="5d2f6-210">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="5d2f6-210">Iterators</span></span>](../../concepts/iterators.md)
