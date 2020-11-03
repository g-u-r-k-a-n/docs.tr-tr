---
title: Ön Plan ve Arka Plan İş Parçacıklarını Seçme
description: .NET 'teki Thread. IsBackground özelliğini kullanarak bir iş parçacığının arka plan iş parçacığı veya bir ön plan iş parçacığı olup olmadığını belirleme veya değiştirme.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET], foreground
- threading [.NET], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
ms.openlocfilehash: 3b468d2de382719496d5dfaf4c704d43f3e748c3
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188074"
---
# <a name="foreground-and-background-threads"></a>Ön plan ve arka plan iş parçacıkları

Yönetilen iş parçacığı, bir arka plan iş parçacığı veya bir ön plan iş parçacığıdır. Arka plan iş parçacıkları tek bir özel durum içeren ön plan iş parçacıklarıyla aynıdır: arka plan iş parçacığı yönetilen yürütme ortamını çalışır durumda tutar. Yönetilen bir işlemde (. exe dosyasının yönetilen bir derleme olduğu) tüm ön plan iş parçacıkları durdurulduktan sonra, sistem tüm arka plan iş parçacıklarını durduruyor ve kapatır.  
  
> [!NOTE]
> Çalışma zamanı bir arka plan iş parçacığını durdurduğundan, iş parçacığında hiçbir özel durum oluşturulmaz. Ancak, yöntem uygulama etki alanını kaldırdığından iş parçacıkları durdurulduğunda, <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> <xref:System.Threading.ThreadAbortException> hem ön planda hem de arka plan iş parçacıklarında bir oluşturulur.  
  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>Bir iş parçacığının arka plan veya ön plan iş parçacığı olduğunu veya durumunu değiştirmek için özelliğini kullanın. Bir iş parçacığı, özelliği olarak ayarlanarak herhangi bir zamanda arka plan iş parçacığına değiştirilebilir <xref:System.Threading.Thread.IsBackground%2A> `true` .  
  
> [!IMPORTANT]
> Bir iş parçacığının ön plan veya arka plan durumu, iş parçacığında işlenmeyen bir özel durumun sonucunu etkilemez. Ön planda veya arka plan iş parçacıklarında işlenmeyen bir özel durum, uygulamanın sonlandırmasına neden olur. Bkz. [yönetilen Iş parçacıklarında özel durumlar](exceptions-in-managed-threads.md).  
  
 Yönetilen iş parçacığı havuzuna ait olan iş parçacıkları (diğer bir deyişle, özelliği olan iş parçacıkları <xref:System.Threading.Thread.IsThreadPoolThread%2A> `true` ) arka plan iş parçacığıdır. Yönetilmeyen koddan yönetilen yürütme ortamına giriş yapan tüm iş parçacıkları arka plan iş parçacıkları olarak işaretlenir. Yeni bir nesne oluşturup başlattıktan sonra oluşturulan tüm iş parçacıkları <xref:System.Threading.Thread> varsayılan ön plan iş parçacıklarından oluşur.  
  
 Yuva bağlantısı gibi bir etkinliği izlemek için bir iş parçacığı kullanıyorsanız, <xref:System.Threading.Thread.IsBackground%2A> `true` iş parçacığının sonlandırmasını önleyememesi için özelliğini olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
