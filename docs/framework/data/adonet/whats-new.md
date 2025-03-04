---
title: Yenilikler
description: .NET Framework 4,5 ' deki yeni özellikler hakkında bilgi edinin, SqlClient veri sağlayıcısı ve ADO.NET Entity Framework için yeni özellikler de dahildir.
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: b34a27574b6aab75539f9ab30e2978e45b4ad9e3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553863"
---
# <a name="whats-new-in-adonet"></a>ADO.NET’teki Yenilikler

Aşağıdaki özellikler .NET Framework 4,5 ' de yeni ADO.NET.

## <a name="sqlclient-data-provider"></a>SqlClient Veri Sağlayıcısı

Aşağıdaki özellikler .NET Framework 4,5 ' de SQL Server için .NET Framework Veri Sağlayıcısı yenidir:

- ConnectRetryCount ve ConnectRetryInterval bağlantı dizesi anahtar sözcükleri ( <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> ), boştaki bağlantı dayanıklılığı özelliğini denetlemenizi sağlar.

- SQL Server bir uygulamaya akış desteği, sunucudaki verilerin yapılandırılmamış olduğu senaryoları destekler.  Daha fazla bilgi için bkz. [SqlClient akış desteği](sqlclient-streaming-support.md) .

- Zaman uyumsuz programlama için destek eklenmiştir.  Daha fazla bilgi için bkz. [zaman uyumsuz programlama](asynchronous-programming.md) .

- Bağlantı hatalarıyla artık genişletilmiş olaylar günlüğüne kaydedilecek. Daha fazla bilgi için bkz. [ADO.net 'de veri izleme](data-tracing.md).

- SqlClient artık SQL Server yüksek kullanılabilirlik, olağanüstü durum kurtarma özelliği, AlwaysOn desteğine sahiptir. Daha fazla bilgi için bkz. [yüksek kullanılabilirlik Için SqlClient desteği, olağanüstü durum kurtarma](./sql/sqlclient-support-for-high-availability-disaster-recovery.md).

- Parola, <xref:System.Security.SecureString> SQL Server kimlik doğrulaması kullanılırken bir olarak geçirilebilir. Daha fazla bilgi edinmek için bkz. <xref:System.Data.SqlClient.SqlCredential>.

- `TrustServerCertificate`Yanlış olduğunda ve `Encrypt` doğru olduğunda, BIR SQL Server SSL sertifikasındaki sunucu adı (veya IP adresi), bağlantı dizesinde belirtilen sunucu adı (veya IP adresi) ile tam olarak eşleşmelidir. Aksi takdirde, bağlantı denemesi başarısız olur. Daha fazla bilgi için, `Encrypt` bağlantısındaki bağlantı seçeneğinin açıklamasına bakın <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> .

  Bu değişiklik, mevcut bir uygulamanın artık bağlanmasına neden olursa, aşağıdakilerden birini kullanarak uygulamayı çözebilirsiniz:

  - Ortak ad (CN) veya konu diğer adı (SAN) alanındaki kısa adı belirten bir sertifika verin. Bu çözüm, veritabanı yansıtma için çalışacaktır.

  - Kısa adı, tam etki alanı adına eşleyen bir diğer ad ekleyin.

  - Bağlantı dizesindeki tam etki alanı adını kullanın.

- SqlClient genişletilmiş korumayı destekler. Genişletilmiş koruma hakkında daha fazla bilgi için bkz. [genişletilmiş koruma kullanarak veritabanı altyapısına bağlanma](/sql/database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection).

- SqlClient, LocalDB veritabanlarına bağlantıları destekler. Daha fazla bilgi için bkz. [LocalDB Için SqlClient desteği](./sql/sqlclient-support-for-localdb.md).

- `Type System Version=SQL Server 2012;` , bağlantı özelliğine geçirilecek yeni bir değerdir `Type System Version` . `Type System Version=Latest;`Değer artık kullanılmıyor ve ile eşdeğer hale getirilir `Type System Version=SQL Server 2008;` . Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

- SqlClient, SQL Server 2008 ' de eklenen bir özellik olan seyrek sütunlar için ek destek sağlar. Uygulamanız seyrek sütun kullanan bir tablodaki verilere zaten eriştiğinde performansta bir artış görmeniz gerekir. Icolumnset sütunu, <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> bir sütunun bir sütun kümesinin üyesi olan seyrek sütun olup olmadığını gösterir. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> bir sütunun seyrek sütun olup olmadığını gösterir (daha fazla bilgi için bkz. [SQL Server şeması koleksiyonları](sql-server-schema-collections.md) ). Seyrek sütunlar hakkında daha fazla bilgi için bkz. [seyrek sütun kullanma](/sql/relational-databases/tables/use-sparse-columns).

- Uzamsal veri türlerini içeren derleme Microsoft.SqlServer.Types.dll sürüm 10,0 ' den sürüm 11,0 ' den yükseltildi. Bu derlemeye başvuran uygulamalar başarısız olabilir. Daha fazla bilgi için bkz. [veritabanı altyapısı özelliklerine yönelik son değişiklikler](/previous-versions/sql/sql-server-2012/ms143179(v=sql.110)).

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

.NET Framework 4,5, Entity Framework 5,0 ile çalışırken yeni senaryolar sağlayan API 'Ler ekler. 5,0 Entity Framework eklenen geliştirmeler ve özellikler hakkında daha fazla bilgi için, şu konulara [bakın: yenilikler](/previous-versions/gg696190(v=vs.103)) ve [Entity Framework sürümleri ve sürüm oluşturma](/ef/ef6/what-is-new/past-releases).

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
- [SQL Server ve ADO.NET](./sql/index.md)
- [WCF Veri Hizmetleri 5,0 ' deki yenilikler](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
