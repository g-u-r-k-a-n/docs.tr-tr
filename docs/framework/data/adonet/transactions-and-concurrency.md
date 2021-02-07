---
description: 'Daha fazla bilgi edinin: Işlemler ve eşzamanlılık'
title: İşlemler ve Eşzamanlılık
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: c77b9abc72ae662eec76fc40a9856ad73f000c27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766770"
---
# <a name="transactions-and-concurrency"></a>İşlemler ve Eşzamanlılık

Bir işlem, paket olarak yürütülen tek bir komuttan veya bir komut grubundan oluşur. İşlemler, birden çok işlemi tek bir iş biriminde birleştirmenizi sağlar. İşlemdeki bir noktada bir hata oluşursa, tüm güncelleştirmeler ön işlem durumuna geri alınabilir.  
  
 Veri tutarlılığını güvence altına almak için bir işlemin ACID özelliklerine (kararlılık, tutarlılık, yalıtım ve dayanıklılık) uyması gerekir. Microsoft SQL Server gibi çoğu ilişkisel veritabanı sistemi, bir istemci uygulaması bir güncelleştirme, ekleme veya silme işlemi gerçekleştirdiğinde kilitleme, günlüğe kaydetme ve işlem yönetimi olanakları sağlayarak işlemleri destekler.  
  
> [!NOTE]
> Kilitler çok uzun tutuluyorsa birden çok kaynağı içeren işlemler eşzamanlılık daha düşük olabilir. Bu nedenle, işlemleri mümkün olduğunca kısa tutun.  
  
 Bir işlem aynı veritabanı veya sunucuda birden çok tablo içeriyorsa, saklı yordamlardaki açık işlemler genellikle daha iyi gerçekleştirilir. Transact-SQL `BEGIN TRANSACTION` , `COMMIT TRANSACTION` , ve deyimlerini kullanarak SQL Server saklı yordamda işlem oluşturabilirsiniz `ROLLBACK TRANSACTION` . Daha fazla bilgi için bkz. Books Online SQL Server.  
  
 SQL Server ve Oracle arasındaki bir işlem gibi farklı kaynak yöneticileriyle ilgili işlemler, dağıtılmış bir işlem gerektirir.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Yerel İşlemler](local-transactions.md)  
 Bir veritabanına yönelik işlemlerin nasıl gerçekleştirileceğini gösterir.  
  
 [Dağıtılmış Işlemler](distributed-transactions.md)  
 ADO.NET içinde dağıtılmış işlemlerin nasıl gerçekleştirileceğini açıklar.  
  
 [SQL Server ile System.Transactions Tümleştirmesi](system-transactions-integration-with-sql-server.md)  
 <xref:System.Transactions>Dağıtılmış işlemlerle çalışmak için SQL Server ile tümleştirmeyi açıklar.  
  
 [İyimser Eşzamanlılık](optimistic-concurrency.md)  
 İyimser ve Kötümser eşzamanlılık ve eşzamanlılık ihlalleri için nasıl test kullanabileceğinizi açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlem Temelleri](../transactions/transaction-fundamentals.md)
- [Bir veri kaynağına bağlanma](connecting-to-a-data-source.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [DbProviderFactories](dbproviderfactories.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
