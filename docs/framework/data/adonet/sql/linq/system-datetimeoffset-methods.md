---
description: ': System. DateTimeOffset yöntemleri hakkında daha fazla bilgi'
title: System.DateTimeOffset Yöntemleri
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 050c710d4a3f3db8112d0d108338c010345afdda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681337"
---
# <a name="systemdatetimeoffset-methods"></a>System.DateTimeOffset Yöntemleri

Nesne modelinde veya dış eşleme dosyasında eşlendikten sonra LINQ to SQL, <xref:System.DateTimeOffset?displayProperty=nameWithType> LINQ to SQL Sorgularınızdaki yöntemlerin, işleçlerin ve özelliklerin çoğunu çağırabilmeniz için izin verir.  
  
 Desteklenmeyen tek Yöntemler, <xref:System.Object?displayProperty=nameWithType> :,, ve gibi LINQ to SQL sorgularının bağlamında anlamayan Devralınanlar `Finalize` `GetHashCode` `GetType` `MemberwiseClone` . LINQ to SQL SQL Server yürütülmek üzere çevrilemediğinden bu yöntemler desteklenmez.  
  
> [!NOTE]
> Ortak dil çalışma zamanı (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> yapısı ve LINQ to SQL ile BIR SQL sütunuyla eşleme özelliği `DATETIMEOFFSET` .NET Framework 3,5 SP1 veya daha fazlasını gerektirir. SQL `DATETIMEOFFSET` sütunu yalnızca Microsoft SQL Server 2008 ve sonraki bir sürümünde kullanılabilir.  
  
## <a name="sqlmethods-date-and-time-methods"></a>SQLMethods tarih ve saat yöntemleri  

 Yapı tarafından sunulan yöntemlerin yanı sıra <xref:System.DateTimeOffset> , LINQ to SQL <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> Tarih ve saat ile çalışmaya yönelik sınıftan aşağıdaki tabloda listelenen yöntemleri sunar.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
- [Nesne Modeli Oluşturma](creating-the-object-model.md)
- [SQL-CLR Tür Eşlemesi](sql-clr-type-mapping.md)
