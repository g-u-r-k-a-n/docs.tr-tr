---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f36ac1337dd0d1400180fbd3deae2bb24ad9c58
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348489"
---
# <a name="example-visual-basic"></a>\<example> (Visual Basic)
Specifies an example for the member.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>Parametreler  
 `description`  
 A description of the code sample.  
  
## <a name="remarks"></a>Açıklamalar  
 The `<example>` tag lets you specify an example of how to use a method or other library member. This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.  
  
 Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.  
  
## <a name="example"></a>Örnek  
 This example uses the `<example>` tag to include an example for using the `ID` field.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
