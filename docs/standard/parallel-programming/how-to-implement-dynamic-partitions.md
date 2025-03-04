---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: dinamik bölümleri uygulama'
title: 'Nasıl yapılır: Dinamik Bölümleri Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
ms.openlocfilehash: 3f0b383b9f4f7a47acb21d3ec3451b1761a3368c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701969"
---
# <a name="how-to-implement-dynamic-partitions"></a>Nasıl yapılır: Dinamik Bölümleri Uygulama

Aşağıdaki örnek, dinamik bölümlendirme uygulayan bir özel nasıl uygulanacağını <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> ve belirli aşırı yüklerden <xref:System.Threading.Tasks.Parallel.ForEach%2A> ve PLINQ 'ten nasıl kullanılabileceğini gösterir.  
  
## <a name="example"></a>Örnek

Numaralandırıcı üzerinde bir bölüm çağırdığında <xref:System.Collections.IEnumerator.MoveNext%2A> , Numaralandırıcı bölüm bir liste öğesiyle birlikte sunulur. PLıNQ ve durumunda <xref:System.Threading.Tasks.Parallel.ForEach%2A> , bölüm bir <xref:System.Threading.Tasks.Task> örneğidir. İstekler birden çok iş parçacığında eşzamanlı olarak yapıldığından, geçerli dizine erişim eşitlenir.  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

Bu, öbek bölümlendirme bir örneğidir ve her bir öbek bir öğeden oluşur. Tek seferde daha fazla öğe sağlayarak kilit üzerindeki çekişmeyi azaltabilir ve teorik olarak daha hızlı performans elde edersiniz. Ancak, bazı bir noktada, tüm işler tamamlanana kadar tüm iş parçacıklarını meşgul tutmak için daha büyük parçalar ek yük dengeleme mantığını gerektirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

* [PLıNQ ve TPL için Özel Bölümleyiciler](custom-partitioners-for-plinq-and-tpl.md)
* [Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama](how-to-implement-a-partitioner-for-static-partitioning.md)
