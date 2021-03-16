---
title: <list> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <list> Etiket. Bu etiket, ' item ' blokları kullanılarak tablolar ve tanım, madde işaretli veya numaralandırılmış listeler oluşturmak için kullanılır.
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 39674e3c07444e454dfeeceff6c99e65f34bb02f
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478386"
---
# <a name="list-c-programming-guide"></a>\<list> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<list type="bullet|number|table">
    <listheader>
        <term>term</term>
        <description>description</description>
    </listheader>
    <item>
        <term>term</term>
        <description>description</description>
    </item>
</list>
```

## <a name="parameters"></a>Parametreler

- `term`

  ' De tanımlanacak bir terim `description` .

- `description`

  Bir madde işareti veya numaralandırılmış listedeki bir öğe ya da bir tanımı `term` .
  
## <a name="remarks"></a>Açıklamalar

`<listheader>`Blok, bir tablo ya da tanım listesinin başlık satırını tanımlamak için kullanılır. Bir tablo tanımlarken, yalnızca başlıktaki terim için bir giriş sağlamanız gerekir.

Listedeki her öğe bir `<item>` blokla belirtilir. Bir tanım listesi oluştururken, hem hem de belirtmeniz gerekecektir `term` `description` . Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca bir giriş sağlamanız gerekir `description` .

Bir liste veya tablo gerektiği kadar çok `<item>` blok içerebilir.

Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
