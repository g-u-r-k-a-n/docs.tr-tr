---
title: Pürüzlü Diziler-C# Programlama Kılavuzu
description: C# ' deki pürüzlü bir dizi, öğeleri farklı boyutlarda diziler olan bir dizidir. Pürüzlü dizileri tanımlamayı, başlatmayı ve erişmeyi öğrenin.
ms.date: 12/18/2020
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 6d4fb939fb6594c7644a80eb688ea852ddf8a5c5
ms.sourcegitcommit: c3093e9d106d8ca87cc86eef1f2ae4ecfb392118
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97737287"
---
# <a name="jagged-arrays-c-programming-guide"></a>Basit Diziler (C# Programlama Kılavuzu)

Pürüzlü bir dizi, öğeleri dizi olan ve muhtemelen farklı boyutlarda olan bir dizidir. Pürüzlü bir dizi bazen "dizi dizisi" olarak adlandırılır. Aşağıdaki örneklerde, pürüzlü dizileri bildirme, başlatma ve erişme işlemlerinin nasıl yapılacağı gösterilmektedir.

 Aşağıda, her biri tek boyutlu tamsayılar dizisi olan üç öğesi olan tek boyutlu bir dizinin bildirimi verilmiştir:

 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]

 Kullanabilmeniz için `jaggedArray` , öğesinin öğelerinin başlatılmış olması gerekir. Aşağıdaki gibi öğeleri başlatabilirsiniz:

 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]

 Öğelerin her biri, tamsayıların tek boyutlu dizisidir. İlk öğe, 5 tamsayının dizisidir, ikincisi 4 tamsayının dizisidir ve üçüncüsü 2 tamsayının dizisidir.

 Ayrıca, dizi öğelerini değerlerle doldurmanız için başlatıcıları kullanmak mümkündür, bu durumda dizi boyutuna ihtiyacınız yoktur. Örneğin:

 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]

 Ayrıca, aşağıdaki gibi bildirim üzerine diziyi de başlatabilirsiniz:

 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]

 Aşağıdaki toplu formu kullanabilirsiniz. `new`Öğeler için varsayılan başlatma olmadığından öğe başlatmasında operatörü atlayamazsınız.

 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]

 Sivri dizi dizi dizilerdir ve bu nedenle öğeleri başvuru türleridir ve olarak başlatılır `null` .

 Aşağıdaki örnekler gibi ayrı dizi öğelerine erişebilirsiniz:

 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]

 Sivri ve çok boyutlu dizileri karıştırmak mümkündür. Aşağıda, farklı boyutlarda 3 2 boyutlu dizi öğeleri içeren tek boyutlu pürüzlü bir dizinin bildirimi ve başlatılması yer almaktadır. Daha fazla bilgi için bkz. [çok boyutlu diziler](./multidimensional-arrays.md).

 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]

 Bu örnekte gösterildiği gibi, her bir öğeye, `[1,0]` ilk dizinin (değer) öğesinin değerini görüntüleyen tek bir erişebilirsiniz `5` :

 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]

 Yöntemi, `Length` pürüzlü dizide bulunan dizilerin sayısını döndürür. Örneğin, önceki diziyi bildirdiğiniz varsayılarak, bu satır:

 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]

 3 değerini döndürür.

## <a name="example"></a>Örnek

 Bu örnek, öğeleri kendi dizileri olan bir dizi oluşturur. Dizi öğelerinden her birinin farklı bir boyutu vardır.

 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- [C# Programlama Kılavuzu](../index.md)
- [Diziler](./index.md)
- [Tek Boyutlu Diziler](./single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](./multidimensional-arrays.md)
