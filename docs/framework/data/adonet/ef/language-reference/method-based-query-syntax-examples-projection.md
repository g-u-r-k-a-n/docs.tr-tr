---
description: 'Hakkında daha fazla bilgi edinin: Method-Based sorgu söz dizimi örnekleri: projeksiyon'
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Projeksiyon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: ed4d53166f15f5a2b618ccae92b40fc07d370299
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696665"
---
# <a name="method-based-query-syntax-examples-projection"></a>Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Projeksiyon

Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Select%2A> ve <xref:System.Linq.Enumerable.SelectMany%2A> yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için nasıl kullanılacağı gösterilmektedir. Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a>Şunu seçin:  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Queryable.Select%2A> `Product.Name` ve `Product.ProductID` özelliklerini bir anonim türler dizisi halinde proje yapmak için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Select%2A> yalnızca ürün adlarından oluşan bir dizi döndürmek için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a>SelectMany  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, 500,00 ' <xref:System.Linq.Enumerable.SelectMany%2A> den küçük olan tüm siparişleri seçmek için yöntemini kullanır `TotalDue` .  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Enumerable.SelectMany%2A> 1 ekim 2002 veya sonraki sürümlerde siparişin yapıldığı tüm siparişleri seçmek için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
