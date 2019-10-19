---
title: '#If... Sonra... #Else yönergeleri (Visual Basic)'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: aaf5e7dd82cebf734da59e9feb89174705468a4b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580087"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="c6ca3-102">#If...Then...#Else Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c6ca3-102">#If...Then...#Else Directives</span></span>

<span data-ttu-id="c6ca3-103">Seçili Visual Basic kodu bloklarını koşullu olarak derler.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6ca3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6ca3-104">Syntax</span></span>

```vb
#If expression Then
   statements
[ #ElseIf expression Then
   [ statements ]
...
#ElseIf expression Then
   [ statements ] ]
[ #Else
   [ statements ] ]
#End If
```

## <a name="parts"></a><span data-ttu-id="c6ca3-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c6ca3-105">Parts</span></span>

`expression`  
<span data-ttu-id="c6ca3-106">@No__t_0 ve `#ElseIf` deyimleri için gereklidir, başka bir yerde.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="c6ca3-107">Yalnızca bir veya daha fazla koşullu derleyici sabiti, sabit değer ve işleçlerden oluşan, `True` veya `False` değerlendirilen herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>

`statements`  
<span data-ttu-id="c6ca3-108">@No__t_0 bildiri bloğu için gerekli, başka bir yerde.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="c6ca3-109">İlişkili ifade `True` olarak değerlendirilirse derlenen program satırları veya derleyici yönergeleri Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>

`#End If`  
<span data-ttu-id="c6ca3-110">@No__t_0 bildiri bloğunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-110">Terminates the `#If` statement block.</span></span>

## <a name="remarks"></a><span data-ttu-id="c6ca3-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6ca3-111">Remarks</span></span>

<span data-ttu-id="c6ca3-112">Yüzeyde, `#If...Then...#Else` yönergelerinin davranışı `If...Then...Else` deyimleriyle aynı şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="c6ca3-113">Ancak, `#If...Then...#Else` yönergeleri derleyicinin derlendiğini değerlendirir, ancak `If...Then...Else` deyimleri çalışma zamanında koşulları değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>

<span data-ttu-id="c6ca3-114">Koşullu derleme genellikle farklı platformlar için aynı programı derlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="c6ca3-115">Hata ayıklama kodunun yürütülebilir bir dosyada görünmesini engellemek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="c6ca3-116">Koşullu derleme sırasında dışlanan kod, son yürütülebilir dosyadan tamamen atlandığından, boyut veya performans üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>

<span data-ttu-id="c6ca3-117">Herhangi bir değerlendirmenin sonucuna bakılmaksızın, tüm ifadeler `Option Compare Binary` kullanılarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="c6ca3-118">@No__t_0 deyimi `#If` ve `#ElseIf` deyimlerindeki ifadeleri etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>

> [!NOTE]
> <span data-ttu-id="c6ca3-119">@No__t_0, `#Else`, `#ElseIf` ve `#End If` yönergelerinin tek satırlık formu yoktur.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="c6ca3-120">Diğer hiçbir kod, yönergelerden biriyle aynı satırda görünemez.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-120">No other code can appear on the same line as any of the directives.</span></span>

<span data-ttu-id="c6ca3-121">Koşullu derleme bloğunun içindeki deyimler, tamamlanmış Mantıksal deyimler olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="c6ca3-122">Örneğin, yalnızca bir işlevin özniteliklerini koşullu olarak derlenemez, ancak işlevi öznitelikleri ile birlikte koşullu olarak bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c6ca3-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a><span data-ttu-id="c6ca3-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6ca3-123">Example</span></span>

<span data-ttu-id="c6ca3-124">Bu örnek, belirli deyimlerin derlenip derlenmeyeceğini anlamak için `#If...Then...#Else` yapısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="c6ca3-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6ca3-125">See also</span></span>

- [<span data-ttu-id="c6ca3-126">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="c6ca3-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="c6ca3-127">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="c6ca3-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="c6ca3-128">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="c6ca3-128">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
