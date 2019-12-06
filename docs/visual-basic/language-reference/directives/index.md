---
title: Yönergeler
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5e857198351b30c0d7a38dce1a9e6d1209b5258
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838149"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="94feb-102">Yönergeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94feb-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="94feb-103">Bu bölümdeki konular Visual Basic kaynak kodu derleyici yönergelerini belgeleyin.</span><span class="sxs-lookup"><span data-stu-id="94feb-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94feb-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="94feb-104">In This Section</span></span>  

 <span data-ttu-id="94feb-105">[#Const Yönergesi](../../../visual-basic/language-reference/directives/const-directive.md) --derleyici sabiti tanımlama</span><span class="sxs-lookup"><span data-stu-id="94feb-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="94feb-106">[#ExternalSource yönergesi](../../../visual-basic/language-reference/directives/externalsource-directive.md) --kaynak satırları ile kaynağın harici metni arasında bir eşleme belirtin</span><span class="sxs-lookup"><span data-stu-id="94feb-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="94feb-107">[#If... Sonra... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --seçili kod bloklarını derle</span><span class="sxs-lookup"><span data-stu-id="94feb-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="94feb-108">[#Region yönergesi](../../../visual-basic/language-reference/directives/region-directive.md) --Visual Studio düzenleyicisinde kodun bölümlerini daraltma ve gizleme</span><span class="sxs-lookup"><span data-stu-id="94feb-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="94feb-109">**#Disable, #Enable** --kod bölgeleri için belirli uyarıları devre dışı bırakın ve etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="94feb-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="94feb-110">Virgülle ayrılmış bir uyarı kodları listesini devre dışı bırakabilir ve etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94feb-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="94feb-111">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="94feb-111">Related Sections</span></span>  

 [<span data-ttu-id="94feb-112">Visual Basic Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="94feb-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  