---
title: <c> C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: 97d5949a1a1528befeffdc27a3e727ac510e8da2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75697240"
---
# <a name="c-c-programming-guide"></a>\<c > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>Parametreler  
 `text`  
 Kod olarak göstermek istediğiniz metin.  
  
## <a name="remarks"></a>Açıklamalar  
 \<c > etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini belirtmek için bir yol sağlar. Birden çok satırı kod olarak göstermek için [\<kodu >](./code.md) kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
