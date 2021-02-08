---
description: 'Hakkında daha fazla bilgi edinin: + (dize birleştirme) (Entity SQL)'
title: + (Dize birleştirme) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 7b6aac5b865e2127bb23446248e20d83ea3c7ea3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791848"
---
# <a name="-string-concatenation-entity-sql"></a>+ (Dize birleştirme) (Entity SQL)

İki dizeyi birleştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression + expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 EDM 'un geçerli herhangi bir ifadesi. Dize veri türleri. Her iki ifade de aynı veri türünde olmalıdır veya bir ifadenin örtük olarak diğer ifadenin veri türüne dönüştürülmesi gerekir.  
  
## <a name="result-types"></a>Sonuç türleri  

 İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü. Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu iki dizeyi birleştiren + işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#CONCAT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#concat)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Kavramsal model türleri (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
