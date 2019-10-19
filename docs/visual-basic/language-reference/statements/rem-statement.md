---
title: REM Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 729d0710d65c0cda750061e72309ced527bbcfe7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582054"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="99627-102">REM Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99627-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="99627-103">Bir programın kaynak kodunda açıklayıcı açıklamalar eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99627-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99627-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99627-104">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="99627-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="99627-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="99627-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="99627-106">Optional.</span></span> <span data-ttu-id="99627-107">Dahil etmek istediğiniz açıklamanın metni.</span><span class="sxs-lookup"><span data-stu-id="99627-107">The text of any comment you want to include.</span></span> <span data-ttu-id="99627-108">@No__t_0 anahtar sözcüğü ve `comment` arasında bir boşluk olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99627-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99627-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99627-109">Remarks</span></span>  
 <span data-ttu-id="99627-110">Bir `REM` ifadesini tek başına bir satıra koyabilirsiniz ya da başka bir deyimden sonraki bir satıra koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99627-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="99627-111">@No__t_0 deyimin satırdaki son ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99627-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="99627-112">Başka bir deyimden sonra `REM`, bu deyimden bir boşluk ile ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="99627-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="99627-113">@No__t_1 yerine tek tırnak işareti (`'`) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99627-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="99627-114">Bu, yorumunuz aynı satırdaki başka bir deyime veya bir satırda tek başına oturduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="99627-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99627-115">Bir satır devamlılık sırası (`_`) kullanarak `REM` bildirimine devam edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="99627-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="99627-116">Bir yorum başladıktan sonra derleyici, özel anlam için karakterleri denetlemez.</span><span class="sxs-lookup"><span data-stu-id="99627-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="99627-117">Birden çok satırlık bir açıklama için, her satırda başka bir `REM` ifadesini veya bir açıklama sembolünü (`'`) kullanın.</span><span class="sxs-lookup"><span data-stu-id="99627-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99627-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="99627-118">Example</span></span>  
 <span data-ttu-id="99627-119">Aşağıdaki örnek, bir programda açıklayıcı açıklamaları dahil etmek için kullanılan `REM` ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="99627-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="99627-120">Ayrıca, `REM` yerine tek tırnak işareti karakteri (`'`) kullanmanın alternatifini gösterir.</span><span class="sxs-lookup"><span data-stu-id="99627-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="99627-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99627-121">See also</span></span>

- [<span data-ttu-id="99627-122">Code’daki Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99627-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="99627-123">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="99627-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
