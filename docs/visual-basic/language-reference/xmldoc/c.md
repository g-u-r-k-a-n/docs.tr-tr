---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 4ea19ed5330dcbb8fcd84708d1546a81d909b04e
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523935"
---
# <a name="c-visual-basic"></a><span data-ttu-id="e6d4f-102">\<c > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6d4f-102">\<c> (Visual Basic)</span></span>
<span data-ttu-id="e6d4f-103">Açıklama içindeki metnin kod olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6d4f-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6d4f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6d4f-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6d4f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6d4f-105">Parameters</span></span>  
  
|<span data-ttu-id="e6d4f-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="e6d4f-106">Parameter</span></span>|<span data-ttu-id="e6d4f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6d4f-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="e6d4f-108">Kod olarak göstermek istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="e6d4f-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6d4f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6d4f-109">Remarks</span></span>  
 <span data-ttu-id="e6d4f-110">@No__t_0 etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6d4f-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="e6d4f-111">Birden çok satırı kod olarak göstermek için [\<code >](../../../visual-basic/language-reference/xmldoc/code.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6d4f-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="e6d4f-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="e6d4f-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6d4f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6d4f-113">Example</span></span>  
 <span data-ttu-id="e6d4f-114">Bu örnek, `Counter` kodun olduğunu göstermek için Özet bölümündeki `<c>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6d4f-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e6d4f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6d4f-115">See also</span></span>

- [<span data-ttu-id="e6d4f-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="e6d4f-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
