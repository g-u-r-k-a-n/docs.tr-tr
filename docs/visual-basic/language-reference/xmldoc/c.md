---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 857ea1ccca4d74daf65bba03845004561afefd55
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348505"
---
# <a name="c-visual-basic"></a>\<c> (Visual Basic)
Indicates that text within a description is code.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---|---|  
|`text`|The text you would like to indicate as code.|  
  
## <a name="remarks"></a>Açıklamalar  
 The `<c>` tag gives you a way to indicate that text within a description should be marked as code. Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.  
  
 Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.  
  
## <a name="example"></a>Örnek  
 This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
