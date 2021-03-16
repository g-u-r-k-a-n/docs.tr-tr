---
title: <c> -C# Programlama Kılavuzu
description: XML etiketi hakkında bilgi edinin <c> . Bu etiket, bir açıklamada tek satırlık metni kod olarak işaretler, ancak <code>indicates multiple lines.
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
ms.openlocfilehash: fc445c7245287c3835543e4bbe4b3b46ec46fd35
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478692"
---
# <a name="c-c-programming-guide"></a>\<c> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<c>text</c>
```

## <a name="parameters"></a>Parametreler

- `text`

  Kod olarak göstermek istediğiniz metin.

## <a name="remarks"></a>Açıklamalar

`<c>`Etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için bir yol sağlar. [\<code>](./code.md)Birden çok satırı kod olarak göstermek için kullanın.

Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
