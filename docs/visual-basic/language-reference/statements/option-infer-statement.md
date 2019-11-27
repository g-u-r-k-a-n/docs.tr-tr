---
title: Option Infer Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: 53bc9d41f28f63061db2012395480aa6be7515dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346491"
---
# <a name="option-infer-statement"></a><span data-ttu-id="d8906-102">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="d8906-102">Option Infer Statement</span></span>

<span data-ttu-id="d8906-103">Değişkenleri bildirirken yerel tür çıkarımı kullanımını mümkün.</span><span class="sxs-lookup"><span data-stu-id="d8906-103">Enables the use of local type inference in declaring variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8906-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8906-104">Syntax</span></span>

```vb
Option Infer { On | Off }
```

## <a name="parts"></a><span data-ttu-id="d8906-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d8906-105">Parts</span></span>

|<span data-ttu-id="d8906-106">Terim</span><span class="sxs-lookup"><span data-stu-id="d8906-106">Term</span></span>|<span data-ttu-id="d8906-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="d8906-107">Definition</span></span>|
|---|---|
|`On`|<span data-ttu-id="d8906-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d8906-108">Optional.</span></span> <span data-ttu-id="d8906-109">Yerel tür çıkarımı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d8906-109">Enables local type inference.</span></span>|
|`Off`|<span data-ttu-id="d8906-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d8906-110">Optional.</span></span> <span data-ttu-id="d8906-111">Yerel tür çıkarımını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="d8906-111">Disables local type inference.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d8906-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8906-112">Remarks</span></span>

<span data-ttu-id="d8906-113">Bir dosyada `Option Infer` ayarlamak için, dosyanın en üstüne, diğer herhangi bir kaynak koddan önce `Option Infer On` veya `Option Infer Off` yazın.</span><span class="sxs-lookup"><span data-stu-id="d8906-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="d8906-114">Bir dosyadaki `Option Infer` için ayarlanan değer IDE 'de veya komut satırında ayarlanan değer ile çakışıyorsa, dosyadaki değerin önceliği vardır.</span><span class="sxs-lookup"><span data-stu-id="d8906-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="d8906-115">`Option Infer` `On`ayarladığınızda, açıkça bir veri türü belirtmeden yerel değişkenler bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8906-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="d8906-116">Derleyici, başlangıç ifadesinin türünden bir değişkenin veri türünü ifade eden.</span><span class="sxs-lookup"><span data-stu-id="d8906-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>

<span data-ttu-id="d8906-117">Aşağıdaki çizimde `Option Infer` açıktır.</span><span class="sxs-lookup"><span data-stu-id="d8906-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="d8906-118">Bildirim `Dim someVar = 2` değişkeni tür çıkarımı tarafından tamsayı olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d8906-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

<span data-ttu-id="d8906-119">Aşağıdaki ekran görüntüsünde, seçenek çıkarımı açık olduğunda IntelliSense gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d8906-119">The following screenshot shows IntelliSense when Option Infer is on:</span></span>

![Seçenek çıkarımı açık olduğunda IntelliSense görünümünü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-integer-on.png)

<span data-ttu-id="d8906-121">Aşağıdaki çizimde `Option Infer` kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8906-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="d8906-122">Bildirim `Dim someVar = 2` değişkeni tür çıkarımı tarafından `Object` olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d8906-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="d8906-123">Bu örnekte, **seçenek katı** ayarı [derleme sayfasında, Proje tasarımcısı 'nda (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) **kapalı** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d8906-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="d8906-124">Aşağıdaki ekran görüntüsünde, seçenek çıkarımı kapalı olduğunda IntelliSense gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d8906-124">The following screenshot shows IntelliSense when Option Infer is off:</span></span>

![Seçenek çıkarımı kapalıyken IntelliSense görünümünü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> <span data-ttu-id="d8906-126">Bir değişken `Object`olarak bildirildiğinde, program çalışırken çalışma zamanı türü değişebilir.</span><span class="sxs-lookup"><span data-stu-id="d8906-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="d8906-127">Visual Basic, bir `Object` ve değer türü arasında dönüştürmek için *kutulama* ve *kutudan* çıkarma adlı işlemleri gerçekleştirir, bu da yürütmeyi daha yavaş yapar.</span><span class="sxs-lookup"><span data-stu-id="d8906-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="d8906-128">Kutulama ve kutudan çıkarma hakkında daha fazla bilgi için [Visual Basic dil belirtimine](~/_vblang/spec/conversions.md#value-type-conversions)bakın.</span><span class="sxs-lookup"><span data-stu-id="d8906-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>

<span data-ttu-id="d8906-129">Tür çıkarımı yordam düzeyinde uygulanır ve bir sınıf, yapı, modül veya arabirimdeki bir yordamın dışında uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="d8906-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>

<span data-ttu-id="d8906-130">Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="d8906-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>

## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="d8906-131">Bir Option Infer deyimleri mevcut olmadığında</span><span class="sxs-lookup"><span data-stu-id="d8906-131">When an Option Infer Statement Is Not Present</span></span>

<span data-ttu-id="d8906-132">Kaynak kodu `Option Infer` bir ifade içermiyorsa, derleme sayfasındaki **seçenek çıkarımı** ayarı, [proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8906-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="d8906-133">Komut satırı derleyicisi kullanılırsa [-OptionInfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8906-133">If the command-line compiler is used, the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>

#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="d8906-134">IDE 'de seçenek çıkarımı ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d8906-134">To set Option Infer in the IDE</span></span>

1. <span data-ttu-id="d8906-135">**Çözüm Gezgini**bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="d8906-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="d8906-136">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d8906-136">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="d8906-137">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d8906-137">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="d8906-138">**Seçenek çıkarımı** kutusunda değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d8906-138">Set the value in the **Option infer** box.</span></span>

<span data-ttu-id="d8906-139">Yeni bir proje oluşturduğunuzda, **Derle** sekmesindeki **seçenek** çıkar ayarı, **vb Varsayılanları** iletişim kutusundaki **seçenek çıkarımı** ayarı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d8906-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="d8906-140">**Vb Varsayılanları** iletişim kutusuna erişmek Için, **Araçlar** menüsünde **Seçenekler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d8906-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="d8906-141">**Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d8906-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="d8906-142">**Vb Varsayılanları** içindeki ilk varsayılan ayar `On`.</span><span class="sxs-lookup"><span data-stu-id="d8906-142">The initial default setting in **VB Defaults** is `On`.</span></span>

#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="d8906-143">Komut satırında bir seçenek çıkarımı ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d8906-143">To set Option Infer on the command line</span></span>

<span data-ttu-id="d8906-144">**Vbc** komutuna [-OptionInfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d8906-144">Include the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>

## <a name="default-data-types-and-values"></a><span data-ttu-id="d8906-145">Varsayılan veri türleri ve değerleri</span><span class="sxs-lookup"><span data-stu-id="d8906-145">Default Data Types and Values</span></span>

<span data-ttu-id="d8906-146">Aşağıdaki tabloda, bir `Dim` bildiriminde veri türünü ve başlatıcıyı belirtmenin çeşitli birleşimlerinin sonuçları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8906-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="d8906-147">Veri türü belirtildi mi?</span><span class="sxs-lookup"><span data-stu-id="d8906-147">Data type specified?</span></span>|<span data-ttu-id="d8906-148">Başlatıcı belirtildi mi?</span><span class="sxs-lookup"><span data-stu-id="d8906-148">Initializer specified?</span></span>|<span data-ttu-id="d8906-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8906-149">Example</span></span>|<span data-ttu-id="d8906-150">Sonuç</span><span class="sxs-lookup"><span data-stu-id="d8906-150">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="d8906-151">Hayır</span><span class="sxs-lookup"><span data-stu-id="d8906-151">No</span></span>|<span data-ttu-id="d8906-152">Hayır</span><span class="sxs-lookup"><span data-stu-id="d8906-152">No</span></span>|`Dim qty`|<span data-ttu-id="d8906-153">`Option Strict` kapalıysa (varsayılan), değişken `Nothing`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d8906-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="d8906-154">`Option Strict` açık ise, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="d8906-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="d8906-155">Hayır</span><span class="sxs-lookup"><span data-stu-id="d8906-155">No</span></span>|<span data-ttu-id="d8906-156">Evet</span><span class="sxs-lookup"><span data-stu-id="d8906-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="d8906-157">`Option Infer` açık ise (varsayılan), değişkeni başlatıcının veri türünü alır.</span><span class="sxs-lookup"><span data-stu-id="d8906-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="d8906-158">Bkz. [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="d8906-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="d8906-159">`Option Infer` kapalıysa ve `Option Strict` kapalıysa, değişken `Object`veri türünü alır.</span><span class="sxs-lookup"><span data-stu-id="d8906-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="d8906-160">`Option Infer` kapalıysa ve `Option Strict` açık ise, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="d8906-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="d8906-161">Evet</span><span class="sxs-lookup"><span data-stu-id="d8906-161">Yes</span></span>|<span data-ttu-id="d8906-162">Hayır</span><span class="sxs-lookup"><span data-stu-id="d8906-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="d8906-163">Değişken, veri türü için varsayılan değer olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d8906-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="d8906-164">Daha fazla bilgi için bkz. [Dim deyimleri](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d8906-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|
|<span data-ttu-id="d8906-165">Evet</span><span class="sxs-lookup"><span data-stu-id="d8906-165">Yes</span></span>|<span data-ttu-id="d8906-166">Evet</span><span class="sxs-lookup"><span data-stu-id="d8906-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="d8906-167">Başlatıcının veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="d8906-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

## <a name="example"></a><span data-ttu-id="d8906-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8906-168">Example</span></span>

<span data-ttu-id="d8906-169">Aşağıdaki örneklerde `Option Infer` ifadesinin yerel tür çıkarımı nasıl etkinleştirdiğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d8906-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a><span data-ttu-id="d8906-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8906-170">Example</span></span>

<span data-ttu-id="d8906-171">Aşağıdaki örnek, bir değişken `Object`olarak tanımlandığında çalışma zamanı türünün farklı kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8906-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a><span data-ttu-id="d8906-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8906-172">See also</span></span>

- [<span data-ttu-id="d8906-173">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="d8906-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="d8906-174">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="d8906-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="d8906-175">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="d8906-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="d8906-176">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="d8906-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="d8906-177">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="d8906-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="d8906-178">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="d8906-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="d8906-179">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="d8906-179">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="d8906-180">Kutulama ve Kutudan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="d8906-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
