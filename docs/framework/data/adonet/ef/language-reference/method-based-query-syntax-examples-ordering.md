---
description: 'Hakkında daha fazla bilgi edinin: Method-Based sorgu söz dizimi örnekleri: sıralama'
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Sıralama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: 7b1c67ba66f549e82a57b5b34c645d36d1255a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696704"
---
# <a name="method-based-query-syntax-examples-ordering"></a>Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Sıralama

Bu konudaki örneklerde, yöntem <xref:System.Linq.Enumerable.ThenBy%2A> tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir. Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a>ThenBy  
  
### <a name="example"></a>Örnek  

 Yöntem tabanlı sorgu söz diziminde aşağıdaki örnek, <xref:System.Linq.Queryable.OrderBy%2A> <xref:System.Linq.Queryable.ThenBy%2A> son ada göre sıralanmış kişilerin listesini ve sonra adı ve sonra adını döndürmek için ve kullanır.  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a>ThenByDescending  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, ilk olarak <xref:System.Linq.Queryable.OrderBy%2A> <xref:System.Linq.Queryable.ThenByDescending%2A> liste fiyatına göre sıralama yapmak için ve yöntemlerini kullanır ve ardından ürün adlarının azalan sıralamasını gerçekleştirir.  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
