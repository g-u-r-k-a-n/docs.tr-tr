---
description: 'Hakkında daha fazla bilgi edinin: SKIP (Entity SQL)'
title: Atla (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: f4924acae6e351e076b5795cf47d63966ebdcb43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768018"
---
# <a name="skip-entity-sql"></a>Atla (Entity SQL)

ORDER BY yan tümcesindeki SKIP alt yan tümcesini kullanarak fiziksel sayfalama işlemi gerçekleştirebilirsiniz. SKIP, ORDER BY yan tümcesinde ayrı olarak kullanılamaz.

## <a name="syntax"></a>Söz dizimi

```sql
[ SKIP n ]
```

## <a name="arguments"></a>Bağımsız değişkenler

`n` \
Atlanacak öğe sayısı.

## <a name="remarks"></a>Açıklamalar

ORDER BY yan tümcesinde bir SKIP ifadesi Sub yan tümcesi varsa, sonuçlar sıralama belirtimine göre sıralanır ve sonuç kümesi, atlama ifadesinden hemen sonra gelen sonraki satırdan başlayan satırları içerir. Örneğin, 5 ' i atlamak ilk beş satırı atlar ve altıncı satırdan ileriye geri dönecektir.

> [!NOTE]
> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Aynı sorgu ifadesinde hem top Modifier hem de SKIP alt yan tümcesi mevcutsa sorgu geçersizdir. ÜST ifade sınır ifadesine değiştirilerek sorgunun yeniden yazılması gerekir.

> [!NOTE]
> SQL Server 2000 ' de, anahtar olmayan sütunlarda SıRALAMA ile atla kullanılması yanlış sonuçlar döndürebilir. Anahtar olmayan sütunda Yinelenen veriler varsa, belirtilen sayıda satırdan daha fazla satır atlanmayabilir. Bunun nedeni, atlama 'nin SQL Server 2000 ' de çevrilmesine neden olur. Örneğin, aşağıdaki kodda yinelenen değerler varsa beş satırdan daha fazla satır atlanabilir `E.NonKeyColumn` :
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] [Nasıl yapılır: sorgu sonuçları aracılığıyla yapılan](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) sorgu, Select ifadesinde döndürülen nesnelerde kullanılan sıralama DÜZENINI belirtmek IÇIN SKIP ile order by işlecini kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [ORDER BY](order-by-entity-sql.md)
- [Nasıl yapılır: sorgu sonuçları aracılığıyla sayfa oluşturma](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Sayfalama](paging-entity-sql.md)
- [Sayfanın Üstü](top-entity-sql.md)
