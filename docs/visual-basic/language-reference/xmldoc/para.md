---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <para> (Visual Basic)'
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 51dd9ff300d980b4c0576566cad5d17375889ba1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740775"
---
# <a name="para-visual-basic"></a>\<para> (Visual Basic)

İçeriğin bir paragraf olarak biçimlendirildiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Parametreler  

 `content`  
 Paragrafın metni.  
  
## <a name="remarks"></a>Açıklamalar  

 `<para>`Etiketi,, veya gibi bir etiket içinde kullanım içindir [\<summary>](summary.md) [\<remarks>](remarks.md) [\<returns>](returns.md) ve metne yapı eklemenizi sağlar.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<para>` yöntemi için açıklamalar bölümünü iki paragrafa bölmek için etiketini kullanır `UpdateRecord` .  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
