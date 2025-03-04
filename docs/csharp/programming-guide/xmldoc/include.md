---
title: <include> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <include> Etiket. Bu etiket, kaynak kodunuzda türleri ve üyeleri tanımlayan başka bir dosyadaki açıklamalara başvurmanıza olanak sağlar.
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: d2de8fea17850685668766bc4ec6e64b1be77cce
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053197"
---
# <a name="include-c-programming-guide"></a>\<include> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Söz dizimi

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a>Parametreler

- `filename`

  Belgeleri içeren XML dosyasının adı. Dosya adı, kaynak kodu dosyası ile ilişkili bir yol ile nitelenme yapılabilir. `filename`Tek tırnak işaretleri (' ') içine alın.

- `tagpath`

  İçindeki etiketlerin yolu, etikete yol `filename` açar `name` . Yolu tek tırnak işaretleri (' ') içine alın.

- `name`

  Yorumlarla önce gelen etiketteki ad Belirleyicisi; `name` , olur `id` .

- `id`

  Açıklamaların önündeki etiketin KIMLIĞI. KIMLIĞI çift tırnak işareti ("") içine alın.

## <a name="remarks"></a>Açıklamalar

`<include>`Etiketi, kaynak kodunuzda türleri ve üyeleri tanımlayan başka bir dosyadaki açıklamalara başvurmanıza olanak sağlar. Bu, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeye alternatiftir. Belgeler ayrı bir dosyaya yerleştirilerek, kaynak denetimini belgelere kaynak koddan ayrı olarak uygulayabilirsiniz. Bir kişinin kaynak kodu dosyası kullanıma alınmış olabilir ve başka birisinin belge dosyası kullanıma alınmış olabilir.

`<include>`Etiketi, XML XPath söz dizimini kullanır. Kullanımı özelleştirmenin yolları için XPath belgelerine başvurun `<include>` .

## <a name="example"></a>Örnek

Bu çok dosyalı bir örnektir. Tarafından kullanılan ilk dosya aşağıda verilmiştir `<include>` .

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

İkinci dosya *xml_include_tag.doc*, aşağıdaki belge açıklamalarını içerir.

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a>Program çıktısı

Aşağıdaki komut satırı ile test ve test2 sınıflarını derlerken aşağıdaki çıktı oluşturulur: `-doc:DocFileName.xml.` Visual Studio 'da, proje Tasarımcısı 'Nın derleme BÖLMESINDE XML belgesi açıklamaları seçeneğini belirtirsiniz. C# derleyicisi `<include>` etiketini gördüğünde, geçerli kaynak dosya yerine *xml_include_tag.doc* belge açıklamalarını arar. Derleyici daha sonra *DocFileName.xml*oluşturur ve bu, son belgeleri oluşturmak Için [sandrole](https://github.com/EWSoftware/SHFB) gibi belge araçları tarafından tüketilen dosyadır.  
  
```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xml_include_tag</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
