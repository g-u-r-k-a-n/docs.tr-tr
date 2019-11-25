---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 62f70ae7f40fa3cde9492563b7bd14dfa5940a5f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352238"
---
# <a name="returns-visual-basic"></a>\<returns> (Visual Basic)
Specifies the return value of the property or function.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a>Parametreler  
 `description`  
 A description of the return value.  
  
## <a name="remarks"></a>Açıklamalar  
 Use the `<returns>` tag in the comment for a method declaration to describe the return value.  
  
 Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.  
  
## <a name="example"></a>Örnek  
 This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
