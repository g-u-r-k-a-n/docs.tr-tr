---
title: Otomatik
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 7ea46e5f8b882bb986f23e792b240bad0c5be7a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351612"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="023df-102">Otomatik (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="023df-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="023df-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span><span class="sxs-lookup"><span data-stu-id="023df-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="023df-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span><span class="sxs-lookup"><span data-stu-id="023df-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="023df-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span><span class="sxs-lookup"><span data-stu-id="023df-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="023df-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span><span class="sxs-lookup"><span data-stu-id="023df-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="023df-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span><span class="sxs-lookup"><span data-stu-id="023df-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="023df-108">It also affects how Visual Basic searches the external file for the external procedure name.</span><span class="sxs-lookup"><span data-stu-id="023df-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="023df-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span><span class="sxs-lookup"><span data-stu-id="023df-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="023df-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="023df-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="023df-111">If no character set modifier is specified, `Ansi` is the default.</span><span class="sxs-lookup"><span data-stu-id="023df-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="023df-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="023df-112">Remarks</span></span>  
 <span data-ttu-id="023df-113">The `Auto` modifier can be used in this context:</span><span class="sxs-lookup"><span data-stu-id="023df-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="023df-114">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="023df-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="023df-115">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="023df-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="023df-116">This keyword is not supported.</span><span class="sxs-lookup"><span data-stu-id="023df-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="023df-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="023df-117">See also</span></span>

- [<span data-ttu-id="023df-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="023df-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="023df-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="023df-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="023df-120">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="023df-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
