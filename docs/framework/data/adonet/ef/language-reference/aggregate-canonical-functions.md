---
description: 'Daha fazla bilgi edinin: Birleşik kurallı Işlevler'
title: Toplu Kurallı İşlevler
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: e26888ac15553a592f7d2cb9b1a0941161115615
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697302"
---
# <a name="aggregate-canonical-functions"></a>Toplu Kurallı İşlevler

Toplamalar, bir giriş değerlerini serisini, örneğin tek bir değer gibi azaltan ifadelerdir. Toplamalar normalde SELECT ifadesinin GROUP BY yan tümcesiyle birlikte kullanılır ve nerede kullanılabilecekleri konusunda kısıtlamalar vardır.

## <a name="aggregate-entity-sql-canonical-functions"></a>Entity SQL kurallı işlevleri toplama

Aşağıda, toplu Entity SQL kurallı işlevler verilmiştir.

### <a name="avgexpression"></a>Ort (ifade)

Null olmayan değerlerin ortalamasını döndürür.

**Bağımsız değişkenler**

`Int32`,, `Int64` `Double` Ve `Decimal` .

**Dönüş Değeri**

Türü `expression` veya `null` tüm giriş değerleri `null` değer ise.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a>BigCount (ifade)

Null ve yinelenen değerler dahil olmak üzere toplamanın boyutunu döndürür.

**Bağımsız değişkenler**

Herhangi bir tür.

**Dönüş Değeri**

Bir `Int64` .

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a>Count (ifade)

Null ve yinelenen değerler dahil olmak üzere toplamanın boyutunu döndürür.

**Bağımsız değişkenler**

Herhangi bir tür.

**Dönüş Değeri**

Bir `Int32` .

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a>Max (ifade)

Null olmayan değerlerin en büyük değerini döndürür.

**Bağımsız değişkenler**

A `Byte` , `Int16` , `Int32` , `Int64` , `Byte` , `Single` , `Double` , `Decimal` , `DateTime` , `DateTimeOffset` , `Time` , `String` , `Binary` .

**Dönüş Değeri**

Türü `expression` veya `null` tüm giriş değerleri `null` değer ise.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a>Min (ifade)

Null olmayan değerlerin en küçük değerini döndürür.

**Bağımsız değişkenler**

A `Byte` , `Int16` , `Int32` , `Int64` , `Byte` , `Single` , `Double` , `Decimal` , `DateTime` , `DateTimeOffset` , `Time` , `String` , `Binary` .

**Dönüş Değeri**

Türü `expression` veya `null` tüm giriş değerleri `null` değer ise.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a>StDev (ifade)

Null olmayan değerlerin standart sapmasını döndürür.

**Bağımsız değişkenler**

Bir `Int32` , `Int64` , `Double` , `Decimal` .

**Dönüş Değeri**

Bir `Double`. `Null`Tüm giriş değerleri `null` değer ise.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a>STDSAPMAS (ifade)

Tüm değerlerin popülasyonu için standart sapmayı döndürür.

**Bağımsız değişkenler**

Bir `Int32` , `Int64` , `Double` , `Decimal` .

**Dönüş Değeri**

`Double`Ya da `null` tüm giriş değerleri `null` değer ise.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a>Sum (ifade)

Null olmayan değerlerin toplamını döndürür.

**Bağımsız değişkenler**

Bir `Int32` , `Int64` , `Double` , `Decimal` .

**Dönüş Değeri**

`Double`Ya da `null` tüm giriş değerleri `null` değer ise.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a>Var (ifade)

Null olmayan tüm değerlerin varyansını döndürür.

**Bağımsız değişkenler**

Bir `Int32` , `Int64` , `Double` , `Decimal` .

**Dönüş Değeri**

`Double`Ya da `null` tüm giriş değerleri `null` değer ise.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a>VarP (ifade)

Null olmayan tüm değerlerin popülasyon varyansını döndürür.

**Bağımsız değişkenler**

Bir `Int32` , `Int64` , `Double` , `Decimal` .

**Dönüş Değeri**

`Double`Ya da `null` tüm giriş değerleri `null` değer ise.

**Örnek**

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

Eşdeğer işlevsellik, Microsoft SQL Istemci tarafından yönetilen sağlayıcıda bulunur. Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).

## <a name="collection-based-aggregates"></a>Koleksiyon tabanlı toplamalar

Koleksiyon tabanlı toplamalar (koleksiyon işlevleri) koleksiyonlar üzerinde çalışır ve bir değer döndürür. Örneğin, SIPARIŞLER tüm siparişlerin bir koleksiyonudur, en erken sevk tarihini aşağıdaki ifadeyle hesaplayabilirsiniz:

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

Koleksiyon tabanlı toplamaların içindeki ifadeler geçerli ortam adı çözümleme kapsamı içinde değerlendirilir.

## <a name="group-based-aggregates"></a>Grup tabanlı toplamalar

Grup tabanlı toplamalar GROUP BY yan tümcesi tarafından tanımlanan bir grup üzerinden hesaplanır. Sonuç içindeki her grup için, her bir gruptaki öğeler toplam hesaplamaya giriş olarak kullanılarak ayrı bir toplama hesaplanır. Bir Group by yan tümcesi bir Select ifadesinde kullanıldığında, yalnızca gruplandırma ifadesi adları, toplamalar veya sabit ifadeler İzdüşüm veya order by yan tümcesinde bulunabilir.

Aşağıdaki örnek, her bir ürün için sipariş edilen ortalama miktarı hesaplar:

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

SELECT ifadesinde açık bir Group by yan tümcesi olmadan grup tabanlı bir toplamaya sahip olmak mümkündür. Bu durumda, tüm öğeler tek bir grup olarak değerlendirilir. Bu, bir sabiti temel alan bir gruplama belirtmeyle eşdeğerdir. Örneğin, aşağıdaki ifadeyi alın:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

Bu, aşağıdaki gibi eşdeğerdir:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

Grup tabanlı toplamanın içindeki ifadeler, WHERE yan tümcesi ifadesinde görünür olacak ad çözümleme kapsamı içinde değerlendirilir.

Transact-SQL ' de olduğu gibi, grup tabanlı toplamalarda de tümü veya ayrı bir değiştirici belirtilebilir. AYRı değiştirici belirtilirse, toplama hesaplanmadan önce, yinelenen giriş koleksiyonundan yinelemeler ortadan kaldırılır. Tüm değiştirici belirtilirse (ya da değiştirici belirtilmemişse), yinelenen eleme yapılmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kurallı İşlevler](canonical-functions.md)
