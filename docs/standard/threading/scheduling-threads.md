---
title: İş parçacıklarını zamanlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
ms.openlocfilehash: 806d6620fd236c69a4f461f1e30f68a3fefc9b17
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188958"
---
# <a name="scheduling-threads"></a>İş parçacıklarını zamanlama

Her iş parçacığının kendisine atanmış bir iş parçacığı önceliği vardır. Ortak dil çalışma zamanı içinde oluşturulan iş parçacıklarında öncelikle öncelik atanır <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType> . Çalışma zamanının dışında oluşturulan iş parçacıkları, yönetilen ortama girmeden önce sahip oldukları önceliği korurlar. Özelliği ile herhangi bir iş parçacığının önceliğini alabilir veya ayarlayabilirsiniz <xref:System.Threading.Thread.Priority?displayProperty=nameWithType> .  
  
 İş parçacıkları önceliklerine göre yürütme için zamanlanır. İş parçacıkları çalışma zamanı içinde yürütülebilse de, tüm iş parçacıkları işletim sistemi tarafından işlemci zamanı dilimlerine atanır. İş parçacıklarının yürütüldüğü sırayı belirlemede kullanılan zamanlama algoritmasının ayrıntıları her bir işletim sistemiyle farklılık gösterir. Bazı işletim sistemleri altında, en yüksek önceliğe sahip iş parçacığı (yürütülebilecek iş parçacıklarından) her zaman ilk çalışacak şekilde zamanlanır. Aynı önceliğe sahip birden çok iş parçacığı varsa, Zamanlayıcı ilgili öncelikteki iş parçacıkları arasında geçiş yapar ve her iş parçacığına yürütülecek sabit bir zaman dilimi verir. Daha yüksek önceliğe sahip bir iş parçacığı çalıştırmak için kullanılabilir olduğu sürece, düşük öncelikli iş parçacıkları yürütülmeye ulaşmaz. Belirli bir önceliğe göre daha fazla çalıştırılabilir iş parçacığı kalmadığında, Zamanlayıcı bir sonraki düşük önceliğe gider ve yürütme için bu öncelikteki iş parçacıklarını zamanlar. Daha yüksek öncelikli bir iş parçacığı çalıştırılabilir hale gelirse, daha düşük öncelikli iş parçacığı yok edilir ve daha yüksek öncelikli iş parçacığının bir kez daha yürütülmesine izin verilir. Her birinin üzerine, işletim sistemi, bir uygulamanın kullanıcı arabirimi ön plan ve arka plan arasında taşındığında, iş parçacığı önceliklerini dinamik olarak da ayarlayabilir. Diğer işletim sistemleri farklı bir zamanlama algoritması kullanmayı tercih edebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Iş parçacıkları ve Iş parçacığı kullanma](using-threads-and-threading.md)
- [Windows'da Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma](managed-and-unmanaged-threading-in-windows.md)
