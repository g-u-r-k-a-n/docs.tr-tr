---
description: 'Hakkında daha fazla bilgi edinin: OLE DB, ODBC ve Oracle bağlantı havuzu'
title: OLE DB, ODBC ve Oracle Bağlantı Havuzu
ms.date: 03/30/2017
ms.assetid: 2bd83b1e-3ea9-43c4-bade-d9cdb9bbbb04
ms.openlocfilehash: da30d70f88c8d109d50716347e7deaacdc65991a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672653"
---
# <a name="ole-db-odbc-and-oracle-connection-pooling"></a>OLE DB, ODBC ve Oracle bağlantı havuzu

Havuzlama bağlantıları, uygulamanızın performansını ve ölçeklenebilirliğini önemli ölçüde geliştirebilir. Bu bölümde OLE DB, ODBC ve Oracle .NET Framework veri sağlayıcıları için bağlantı havuzu ele alınmaktadır.

## <a name="oledb"></a>OleDb

OLE DB için .NET Framework Veri Sağlayıcısı, OLE DB oturum havuzu kullanarak bağlantıları otomatik olarak havuza. Bağlantı dizesi bağımsız değişkenleri, havuz dahil OLE DB hizmetlerini etkinleştirmek veya devre dışı bırakmak için kullanılabilir. Örneğin, aşağıdaki bağlantı dizesi OLE DB oturum kuyruğunu ve otomatik işlem kaydı 'nı devre dışı bırakır.

```csharp
Provider=SQLOLEDB;OLE DB Services=-4;Data Source=localhost;Integrated Security=SSPI;
```

 Havuzun bağlantısını döndürmek için kullanmayı bitirdiğinizde bir bağlantıyı her zaman kapatmanızı veya atmayı öneririz. Açıkça kapatılmayan bağlantılar havuza döndürülmeyebilir. Örneğin, kapsam dışına çıkan ancak açıkça kapatılmayan bir bağlantı yalnızca en büyük havuz boyutuna ulaşılmışsa ve bağlantı hala geçerliyse bağlantı havuzuna döndürülür.

 OLE DB oturum veya kaynak havuzlama hakkında daha fazla bilgi için ve OLE DB sağlayıcısı hizmet varsayılanlarını geçersiz kılarak havuzlamayı devre dışı bırakma hakkında daha fazla bilgi için bkz. [OLE DB Programcı Kılavuzu](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="odbc"></a>ODBC

 ODBC için .NET Framework Veri Sağlayıcısı bağlantı havuzu, bağlantı için kullanılan ODBC Sürücü Yöneticisi tarafından yönetilir ve ODBC için .NET Framework Veri Sağlayıcısı bundan etkilenmez.

 Bağlantı havuzunu etkinleştirmek veya devre dışı bırakmak için, Denetim Masası 'nın Yönetimsel Araçlar klasöründe **ODBC veri kaynağı Yöneticisi** ' ni açın. **Bağlantı havuzu oluşturma** sekmesi, yüklü her ODBC sürücüsü için bağlantı havuzu oluşturma parametrelerini belirtmenize olanak tanır. Belirli bir ODBC sürücüsüne yönelik bağlantı havuzu değişiklikleri, bu ODBC sürücüsünü kullanan tüm uygulamaları etkiler.

## <a name="oracleclient"></a>OracleClient

 Oracle için .NET Framework Veri Sağlayıcısı, ADO.NET istemci uygulamanız için otomatik olarak bağlantı havuzu sağlar. Ayrıca, bağlantı havuzu davranışlarını denetlemek için çeşitli bağlantı dizesi değiştiricileri sağlayabilirsiniz (Bu konunun ilerleyen kısımlarında "bağlantı dizesi anahtar kelimeleri ile bağlantı havuzunu denetleme" konusuna bakın).

### <a name="create-and-assign-pools"></a>Havuz oluşturma ve atama

 Bir bağlantı açıldığında, havuzu bağlantıdaki bağlantı dizesiyle ilişkilendiren tam bir eşleşen algoritmaya dayalı bir bağlantı havuzu oluşturulur. Her bağlantı havuzu ayrı bir bağlantı dizesiyle ilişkilendirilir. Yeni bir bağlantı açıldığında, bağlantı dizesi var olan bir havuza tam eşleşme değilse yeni bir havuz oluşturulur.

 Oluşturulduktan sonra, bağlantı havuzları etkin işlem bitene kadar yok edilmez. Etkin olmayan veya boş havuzların saklanması çok az sistem kaynağı kullanır.

### <a name="connection-addition"></a>Bağlantı ekleme

 Her benzersiz bağlantı dizesi için bir bağlantı havuzu oluşturulur. Bir havuz oluşturulduğunda, en düşük havuz boyutu gereksiniminin karşılanması için birden fazla bağlantı nesnesi oluşturulur ve havuza eklenir. Bağlantı, en fazla havuz boyutuna kadar gerektiği şekilde havuza eklenir.

 Bir <xref:System.Data.OracleClient.OracleConnection> nesne istendiğinde, kullanılabilir bir bağlantı varsa havuzdan alınır. Kullanılabilir olması için bağlantının Şu anda kullanılmamış olması, eşleşen bir işlem bağlamına sahip olması veya hiçbir işlem içeriğiyle ilişkili olmaması ve sunucuya geçerli bir bağlantısı olması gerekir.

 En büyük havuz boyutuna ulaşılmışsa ve kullanılabilir bir bağlantı yoksa, istek sıraya alınır. Bağlantı havuzlayıcı, havuza geri yayımlandıklarında bağlantıları yeniden bulmaya yönelik bu istekleri karşılar. Bağlantılar, kapalı veya atılmış olmaları durumunda havuza geri yayımlanır.

### <a name="connection-removal"></a>Bağlantı kaldırma

 Bağlantı havuzlayıcı, uzun bir süre boşta kaldıktan sonra havuzdan bir bağlantıyı kaldırır veya havuzlayıcı sunucuyla bağlantının bozulmuş olduğunu algılarsa. Bu, yalnızca sunucuyla iletişim kurmaya çalıştıktan sonra algılanabilir. Artık sunucuya bağlı olmayan bir bağlantı bulunursa, geçersiz olarak işaretlenir. Bağlantı havuzlayıcı, havuzda yayınlanan ve geçersiz olarak işaretlenmiş nesneleri arayan bağlantı havuzlarını düzenli olarak tarar. Bu bağlantılar daha sonra kalıcı olarak kaldırılır.

 Kaybolan bir sunucuya bağlantı varsa, bağlantı havuzlayıcı bağlantıyı algılamadıysa ve geçersiz olarak işaretlediği takdirde bu bağlantı havuzdan çizilebilirler. Bu gerçekleştiğinde, bir özel durum oluşturulur. Bununla birlikte, yine de havuzdan yeniden dağıtım yapmak için bağlantıyı kapatmanız gerekir.

 `Close` `Dispose` Sınıfınızın yönteminde bir, veya `Connection` ya da başka bir `DataReader` yönetilen nesneyi `Finalize` çağırmayın. Sonlandırıcıda yalnızca, sınıfınızın doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın. Sınıfınız hiçbir yönetilmeyen kaynağa sahip değilse, `Finalize` sınıf tanımınıza bir yöntem eklemeyin. Daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).

### <a name="transaction-support"></a>İşlem Desteği

 Bağlantılar havuzdan çizilir ve işlem bağlamına göre atanır. İstekte bulunan iş parçacığının ve atanan bağlantının bağlamı eşleşmelidir. Bu nedenle, her bağlantı havuzu ilişkili işlem bağlamı olmayan bağlantılara ve her biri belirli bir işlem bağlamı ile bağlantı içeren *N* alt bölümüne bölünür.

 Bir bağlantı kapatıldığında, havuza ve işlem bağlamına göre uygun alt bölüme geri gönderilir. Bu nedenle, dağıtılmış bir işlem hala beklense de bir hata oluşturmadan bağlantıyı kapatabilirsiniz. Bu, dağıtılmış işlemi daha sonra yürütmeniz veya iptal etmenizi sağlar.

### <a name="control-connection-pooling-with-connection-string-keywords"></a>Bağlantı dizesi anahtar sözcükleriyle denetim bağlantısı havuzu

 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>Nesnesinin özelliği, <xref:System.Data.OracleClient.OracleConnection> bağlantı havuzu mantığının davranışını ayarlamak için kullanılabilen bağlantı dizesi anahtar/değer çiftlerini destekler.

 Aşağıdaki tabloda, <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> bağlantı havuzu davranışlarını ayarlamak için kullanabileceğiniz değerler açıklanmaktadır.

|Name|Varsayılan|Açıklama|
|----------|-------------|-----------------|
|`Connection Lifetime`|0|Havuza bir bağlantı döndürüldüğünde, oluşturma süresi geçerli zamandan karşılaştırılır ve bu zaman aralığı (saniye cinsinden) tarafından belirtilen değeri aşarsa bağlantı yok edilir `Connection Lifetime` . Bu, çalışan bir sunucu ve daha önce çevrimiçi hale getirilen bir sunucu arasında yük dengelemeyi zorlamak için kümelenmiş yapılandırmalarda yararlıdır.<br /><br /> Sıfır (0) değeri, havuza alınan bağlantıların en uzun zaman aşımı süresine sahip olmasına neden olur.|
|`Enlist`|değeri|Ne zaman `true` , bir işlem bağlamı varsa, havuzlayıcı oluşturma iş parçacığının geçerli işlem bağlamındaki bağlantıyı otomatik olarak listeler.|
|`Max Pool Size`|100|Havuzda izin verilen en fazla bağlantı sayısı.|
|`Min Pool Size`|0|Havuzda tutulan en az bağlantı sayısı.|
|`Pooling`|değeri|Ne zaman `true` , bağlantı uygun havuzdan çizilir veya gerekirse, uygun havuza oluşturulur ve eklenir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Havuzu](connection-pooling.md)
- [Performans sayaçları](performance-counters.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
