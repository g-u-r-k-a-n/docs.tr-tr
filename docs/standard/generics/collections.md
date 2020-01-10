---
title: .NET’te Genel Koleksiyonlar
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
ms.openlocfilehash: dce0e38b0198396ec0dbc3ced7f2f59c2b112b56
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708416"
---
# <a name="generic-collections-in-net"></a>.NET 'teki genel Koleksiyonlar

 .NET sınıf kitaplığı <xref:System.Collections.Generic> ve <xref:System.Collections.ObjectModel> ad alanlarında çok sayıda genel koleksiyon sınıfı sağlar. Bu sınıflar hakkında daha ayrıntılı bilgi için bkz. [yaygın olarak kullanılan koleksiyon türleri](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
## <a name="systemcollectionsgeneric"></a>System. Collections. Generic

 Genel koleksiyon türlerinin birçoğu genel olmayan türlerin doğrudan analoglarından. <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Hashtable>genel bir sürümüdür; <xref:System.Collections.DictionaryEntry>yerine numaralandırma için <xref:System.Collections.Generic.KeyValuePair%602> genel yapıyı kullanır.  
  
 <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>genel bir sürümüdür. Genel olmayan sürümlere karşılık gelen genel <xref:System.Collections.Generic.Queue%601> ve <xref:System.Collections.Generic.Stack%601> sınıfları vardır.  
  
 <xref:System.Collections.Generic.SortedList%602>genel ve genel olmayan sürümleri vardır. Her iki sürüm de bir sözlüğün ve listenin hybrilar. <xref:System.Collections.Generic.SortedDictionary%602> genel sınıfı saf bir sözlüktür ve genel olmayan bir karşılığı yoktur.  
  
 <xref:System.Collections.Generic.LinkedList%601> genel sınıfı, doğru bağlantılı bir listesidir. Genel olmayan bir karşılığı yoktur.  
  
## <a name="systemcollectionsobjectmodel"></a>System. Collections. ObjectModel

 <xref:System.Collections.ObjectModel.Collection%601> genel sınıfı, kendi genel koleksiyon türlerinizi türetmede bir temel sınıf sağlar. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> sınıfı, <xref:System.Collections.Generic.IList%601> genel arabirimini uygulayan herhangi bir türden salt okunurdur bir koleksiyon oluşturmak için kolay bir yol sağlar. <xref:System.Collections.ObjectModel.KeyedCollection%602> genel sınıfı, kendi anahtarlarını içeren nesneleri depolamanın bir yolunu sağlar.  
  
## <a name="other-generic-types"></a>Diğer genel türler

 <xref:System.Nullable%601> genel yapısı, `null`atanmaları gibi değer türlerini kullanmanıza olanak sağlar. Bu, değer türlerini içeren alanların eksik olduğu veritabanı sorgularıyla çalışırken yararlı olabilir. Genel tür parametresi herhangi bir değer türü olabilir.  
  
> [!NOTE]
> C# Ve Visual Basic, dilin Nullable türler için sözdizimi olduğundan, <xref:System.Nullable%601> açıkça kullanılması gerekli değildir. Bkz. [Nullable değer türleriC# (başvuru)](../../csharp/language-reference/builtin-types/nullable-value-types.md) ve [null yapılabilir değer türleri (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).
  
 <xref:System.ArraySegment%601> genel yapısı, herhangi bir türdeki bir öğe aralığını tek boyutlu, sıfır tabanlı bir dizi içinde sınırlamak için bir yol sağlar. Genel tür parametresi, dizinin öğelerinin türüdür.  
  
 <xref:System.EventHandler%601> genel temsilci, olaylarınız .NET Framework tarafından kullanılan olay işleme deseninin ardından olayları işlemek için bir temsilci türü bildirme gereksinimini ortadan kaldırır. Örneğin, olayınıza ilişkin verileri tutmak için <xref:System.EventArgs>türetilmiş bir `MyEventArgs` sınıfı oluşturduğunuzu varsayalım. Olayı daha sonra aşağıdaki gibi bildirebilirsiniz:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](../../../docs/standard/generics/index.md)
- [Dizi ve Listeleri Düzenlemek için Genel Temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Genel Arabirimler](../../../docs/standard/generics/interfaces.md)
