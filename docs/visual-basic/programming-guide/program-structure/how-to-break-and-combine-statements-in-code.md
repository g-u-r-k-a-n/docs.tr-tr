---
description: 'Daha fazla bilgi edinin: nasıl yapılır: koddaki deyimleri kesme ve birleştirme (Visual Basic)'
title: 'Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 33a8b87171c4ee14e73ada564cff406637e96783
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476000"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="0f9a8-103">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f9a8-103">How to: Break and Combine Statements in Code (Visual Basic)</span></span>

<span data-ttu-id="0f9a8-104">Kodunuzu yazarken, kod düzenleyicisinde yatay kaydırmayı gerektiren uzun deyimler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-104">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="0f9a8-105">Bu, kodunuzun çalışma biçimini etkilemese de, siz veya başka birinin izleyiciden göründüğü şekilde kodu okumasını zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-105">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="0f9a8-106">Böyle durumlarda, tek uzun bir ifadeyi birkaç satıra bozmalısınız.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-106">In such cases, you should consider breaking the single long statement into several lines.</span></span>

## <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="0f9a8-107">Tek bir ifadeyi birden çok satıra bölmek için</span><span class="sxs-lookup"><span data-stu-id="0f9a8-107">To break a single statement into multiple lines</span></span>

<span data-ttu-id="0f9a8-108">Çizginin kesilmesini istediğiniz noktada alt çizgi () olan satır devamlılık karakterini kullanın `_` .</span><span class="sxs-lookup"><span data-stu-id="0f9a8-108">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="0f9a8-109">Alt çizgi hemen öncesinde bir boşluk ve hemen arkasından bir satır Sonlandırıcı (satır sonu) ya da (sürüm 16,0 ' den başlayarak) bir yorum ve ardından bir satır başı gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-109">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return) or (starting with version 16.0) a comment followed by a carriage return.</span></span>

  > [!NOTE]
  > <span data-ttu-id="0f9a8-110">Bazı durumlarda, satır devamlılık karakterini atlarsanız Visual Basic derleyici bir sonraki kod satırında ifadeye dolaylı olarak devam eder.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-110">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="0f9a8-111">Satır devamlılık karakterini yok saybileceğiniz sözdizimi öğelerinin listesi için, bkz. [deyimlerde](../language-features/statements.md)"örtük satır devamlılığı".</span><span class="sxs-lookup"><span data-stu-id="0f9a8-111">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../language-features/statements.md).</span></span>

  <span data-ttu-id="0f9a8-112">Aşağıdaki örnekte,, son satır hariç tüm satır devamlılık karakterleriyle dört satıra bölünmüştür.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-112">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  <span data-ttu-id="0f9a8-113">Bu dizinin kullanılması, kodunuzun hem çevrimiçi hem de yazdırıldığında okunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-113">Using this sequence makes your code easier to read, both online and when printed.</span></span>

  <span data-ttu-id="0f9a8-114">Satır devamlılık karakteri bir satırdaki son karakter olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-114">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="0f9a8-115">Aynı satırdaki başka herhangi bir şeyle takip edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-115">You can't follow it with anything else on the same line.</span></span>

  <span data-ttu-id="0f9a8-116">Satır devamlılık karakterini nerede kullanabileceğiniz gibi bazı sınırlamalar vardır; Örneğin, bunu bir bağımsız değişken adının ortasında kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-116">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="0f9a8-117">Bir bağımsız değişken listesini satır devamlılık karakteriyle kesebilirsiniz, ancak bağımsız değişkenlerin bağımsız adları değişmeden kalmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-117">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>

  <span data-ttu-id="0f9a8-118">Bir satır devamlılık karakteri kullanarak açıklamaya devam edemiyorum.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-118">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="0f9a8-119">Derleyici, bir yorum içindeki karakterleri özel anlam açısından inceetmez.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-119">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="0f9a8-120">Birden çok satırlık bir açıklama için, her satırda açıklama sembolünü ( `'` ) yineleyin.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-120">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>

 <span data-ttu-id="0f9a8-121">Her deyimin ayrı bir satıra yerleştirilmesi önerilen yöntem olduğundan, Visual Basic aynı satıra birden çok deyim yerleştirseniz de sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-121">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>

## <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="0f9a8-122">Aynı satıra birden çok deyim yerleştirmek için</span><span class="sxs-lookup"><span data-stu-id="0f9a8-122">To place multiple statements on the same line</span></span>

<span data-ttu-id="0f9a8-123">Deyimlerini aşağıdaki örnekte olduğu gibi iki nokta üst üste ( `:` ) ayırın:</span><span class="sxs-lookup"><span data-stu-id="0f9a8-123">Separate the statements with a colon (`:`), as in the following example:</span></span>

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a><span data-ttu-id="0f9a8-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-124">See also</span></span>

- [<span data-ttu-id="0f9a8-125">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="0f9a8-125">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="0f9a8-126">Deyimler</span><span class="sxs-lookup"><span data-stu-id="0f9a8-126">Statements</span></span>](../language-features/statements.md)
