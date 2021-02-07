---
description: 'Daha fazla bilgi edinin: zaman uyumsuz Işlemler'
title: Zaman Uyumsuz İşlemler
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: 415da1c8a9891bcca13ad26cbbc4c09bfd8909f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718570"
---
# <a name="asynchronous-operations"></a>Zaman Uyumsuz İşlemler

Komut yürütmeleri gibi bazı veritabanı işlemlerinin tamamlanması önemli ölçüde zaman alabilir. Böyle bir durumda, tek iş parçacıklı uygulamaların diğer işlemleri engellemesi ve komutun kendi işlemlerine devam edebilmesi için bitmesini beklemesi gerekir. Buna karşılık, uzun süre çalışan işlemi bir arka plan iş parçacığına atayabilmeniz, ön plan iş parçacığının işlem boyunca etkin kalmasına izin verir. Örneğin, bir Windows uygulamasında, uzun süreli işlemin bir arka plan iş parçacığına atanmasını sağlamak, işlem yürütülürken Kullanıcı arabirimi iş parçacığının yanıt vermeye devam etmesine olanak tanır.  
  
 .NET Framework, geliştiricilerin arka plan iş parçacıklarından yararlanmak ve diğer işlemleri gerçekleştirmek için Kullanıcı arabirimini veya yüksek öncelikli iş parçacıklarını serbest bırakmak için kullanabileceği birkaç standart zaman uyumsuz tasarım desenleri sağlar. ADO.NET, bu tasarım düzenlerini <xref:System.Data.SqlClient.SqlCommand> sınıfında destekler. Özellikle, ve <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A> <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> yöntemleriyle eşleştirilmiş,, ve <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> yöntemleri, <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A> <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A> <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> zaman uyumsuz destek sağlar.  
  
> [!NOTE]
> Zaman uyumsuz programlama, .NET Framework temel bir özelliğidir ve ADO.NET standart tasarım desenlerinden tam olarak yararlanır. Geliştiriciler için kullanılabilen farklı zaman uyumsuz teknikler hakkında daha fazla bilgi için bkz. [zaman uyumlu yöntemleri zaman uyumsuz olarak çağırma](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
 ADO.NET özellikleriyle zaman uyumsuz tekniklerin kullanılması özel bir dikkat eklemez, ancak daha fazla geliştirici, .NET Framework diğer alanlarından farklı olarak ADO.NET 'de zaman uyumsuz Özellikler kullanacaktır. Çok iş parçacıklı uygulamalar oluşturmanın avantajlarının ve haklarının farkında olmak önemlidir. Bu bölümde yer alan örnekler, geliştiricilerin çok iş parçacıklı işlevselliği içeren uygulamalar oluştururken dikkate almanız gereken birkaç önemli sorunu işaret eder.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Geri Çağırma Kullanan Windows Uygulamaları](windows-applications-using-callbacks.md)  
 Zaman uyumsuz bir komutun, bir formla etkileşimi doğru bir şekilde nasıl yürütülediğinizi ve ayrı bir iş parçacığından bir formla içeriğini doğru şekilde işlemesini gösteren bir örnek sağlar.  
  
 [Bekleme Tanıtıcıları Kullanan ASP.NET Uygulamaları](aspnet-apps-using-wait-handles.md)  
 Bir ASP.NET sayfasından birden çok eş zamanlı komutun nasıl yürütüleceğini gösteren bir örnek sağlar.  
  
 [Konsol Uygulamalarında Yoklama](polling-in-console-applications.md)  
 Bir konsol uygulamasından zaman uyumsuz komut yürütmenin tamamlanmasını beklemek için yoklama kullanımını gösteren bir örnek sağlar. Bu teknik, bir sınıf kitaplığı veya Kullanıcı arabirimi olmayan başka bir uygulama için de geçerlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](index.md)
- [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
