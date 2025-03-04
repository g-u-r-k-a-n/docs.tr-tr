---
description: 'Hakkında daha fazla bilgi edinin: Iki sıranın küme kesişimini döndürme'
title: İki Dizinin Küme Kesişimini Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 163e138761caadb73b6dc5d672c02353a88a2c22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662993"
---
# <a name="return-the-set-intersection-of-two-sequences"></a>İki Dizinin Küme Kesişimini Döndürme

<xref:System.Linq.Queryable.Intersect%2A>İki sıranın küme kesişimini döndürmek için işlecini kullanın.  
  
## <a name="example"></a>Örnek  

 Bu örnek, <xref:System.Linq.Queryable.Intersect%2A> hem hem de canlı olan tüm ülkelerin/bölgelerin bir dizisini döndürmek için kullanır `Customers` `Employees` .  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, <xref:System.Linq.Queryable.Intersect%2A> işlem yalnızca kümeler üzerinde tanımlıdır. Multisets semantiği tanımsızdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu örnekleri](query-examples.md)
- [Standart Sorgu İşleci Çevirisi](standard-query-operator-translation.md)
