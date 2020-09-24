---
title: System.TimeSpan Yöntemleri
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: 15b6c8bd5c9cce8e6d1bac030c6b7f6b40df6cd4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155594"
---
# <a name="systemtimespan-methods"></a>System.TimeSpan Yöntemleri

İçin üye desteği <xref:System.TimeSpan?displayProperty=nameWithType> büyük ölçüde kullandığınız .NET Framework ve Microsoft SQL Server sürümlerine bağlıdır.  
  
 Bir yöntem, işleç veya özellik desteklenmiyorsa; LINQ to SQL, SQL Server yürütme için üyeyi çeviremediği anlamına gelir. Kodunuzda bu üyeleri yine de kullanabilirsiniz. Ancak, sorgu Transact-SQL ' e çevrilmeden veya sonuçlar veritabanından alındıktan sonra değerlendirilmelidir.  
  
## <a name="previous-limitations"></a>Önceki sınırlamalar  

 .NET Framework 3,5 SP1 'den önceki .NET Framework sürümleriyle LINQ to SQL kullanırken, SQL Server veritabanı alanlarını ile eşleyemezsiniz <xref:System.TimeSpan?displayProperty=nameWithType> . Ancak, <xref:System.TimeSpan> <xref:System.TimeSpan> değerler çıkarma işleminden döndürülebilecek <xref:System.DateTime> veya bir ifadenin bir sabit değer ya da bağlı değişken olarak tanıtıldığı için üzerinde işlemler desteklenir.  
  
## <a name="supported-systemtimespan-member-support"></a>Desteklenen System. TimeSpan üye desteği

 Aşağıdaki LINQ to SQL desteklenen yöntemler, işleçler ve Özellikler LINQ to SQL sorgularda kullanabileceğiniz şekilde kullanılabilir. Nesne modelinde veya dış eşleme dosyasında eşlendikten sonra, LINQ to SQL LINQ to SQL Sorgularınızdaki birçok üyeyi çağırabilmeniz için izin verir <xref:System.TimeSpan?displayProperty=nameWithType> .  
  
|Desteklenen <xref:System.TimeSpan> Yöntemler|Desteklenen <xref:System.TimeSpan> işleçler|Desteklenen <xref:System.TimeSpan> Özellikler|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
> <xref:System.TimeSpan?displayProperty=nameWithType>LINQ to SQL ile BIR SQL sütunuyla eşleme özelliği, `TIME` .NET Framework 3,5 SP1 ve daha fazlasını gerektirir. SQL `TIME` veri türü yalnızca Microsoft SQL Server 2008 ve daha ötesi bir sürümünde kullanılabilir.  
  
### <a name="addition-and-subtraction"></a>Toplama ve çıkarma  

 CLR <xref:System.TimeSpan?displayProperty=nameWithType> türü ekleme ve çıkarma desteği sağlasa da, SQL `TIME` türü değildir. Bu nedenle, LINQ to SQL sorgularınız, SQL türüne eşlendiklerinde ekleme ve çıkarma işlemi gerçekleştirmeye çalıştıklarında hatalar oluşturur `TIME` . SQL [-CLR tür EŞLEMESINDE](sql-clr-type-mapping.md)SQL tarih ve saat türleriyle çalışmaya yönelik başka hususlar bulabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
- [Nesne Modeli Oluşturma](creating-the-object-model.md)
- [SQL-CLR Tür Eşlemesi](sql-clr-type-mapping.md)
- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
