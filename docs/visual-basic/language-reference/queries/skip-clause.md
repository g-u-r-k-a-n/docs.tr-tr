---
description: 'Daha fazla bilgi edinin: Skip tümcesi (Visual Basic)'
title: Skip Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 6af702f65a724ea8c3d5a6122fb5f7a0ed5f6755
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653556"
---
# <a name="skip-clause-visual-basic"></a>Skip Tümcesi (Visual Basic)

Koleksiyonda belirtilen sayıda öğeyi atlar ve kalan öğeleri döndürür.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>Bölümler  

 `count`  
 Gereklidir. Atlanacak dizinin öğe sayısını değerlendiren bir değer veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 `Skip`Yan tümce bir sorgunun bir sonuç listesinin başlangıcında öğeleri atlamasına ve kalan öğeleri döndürmesini sağlar. Atlanacak öğe sayısı parametresi tarafından tanımlanır `count` .  
  
 `Skip` `Take` Bir sorgunun herhangi bir segmentinden bir veri aralığı döndürmek için yan tümcesini kullanın. Bunu yapmak için aralığın ilk öğesinin dizinini `Skip` yan tümcesine ve aralığın boyutunu `Take` yan tümcesine geçirin.  
  
 `Skip`Bir sorguda yan tümcesini kullandığınızda, sonuçların `Skip` amaçlanan sonuçları atlayıp atlamalarını sağlayacak bir sırada döndürüldüğünden emin olmanız da gerekebilir. Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [order by yan tümcesi](order-by-clause.md).  
  
 `SkipWhile`Belirtilen koşula bağlı olarak yalnızca belirli öğelerin yoksayılacağını belirtmek için yan tümcesini kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, yan tümcesini, `Skip` `Take` sayfalardaki bir sorgudan veri döndürmek için yan tümcesiyle birlikte kullanır. `GetCustomers`İşlevi, `Skip` sağlanan başlangıç dizini değerine kadar listedeki müşterileri atlamak için yan tümcesini kullanır ve `Take` Bu dizin değerinden başlayan müşterilerin bir sayfasını döndürmek için yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [Select yan tümcesi](select-clause.md)
- [From yan tümcesi](from-clause.md)
- [Order by yan tümcesi](order-by-clause.md)
- [Skip While Yan Tümcesi](skip-while-clause.md)
- [Take Yan Tümcesi](take-clause.md)
