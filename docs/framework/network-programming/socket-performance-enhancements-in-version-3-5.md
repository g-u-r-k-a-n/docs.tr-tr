---
title: Sürüm 3.5’teki Yuva Performansı Geliştirmeleri
description: .NET Framework sürüm 3,5 ' de sistem .net. Sockets. Socket sınıfına yönelik performans iyileştirmeleri hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 5a640c58e47bf1630a3a551aed72b9bc9d4fd6fe
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502151"
---
# <a name="socket-performance-enhancements-in-version-35"></a>Sürüm 3.5’teki Yuva Performansı Geliştirmeleri
<xref:System.Net.Sockets.Socket?displayProperty=nameWithType>Sınıf, en yüksek performansa ulaşmak için zaman uyumsuz ağ g/ç kullanan uygulamalar tarafından kullanılmak üzere 3,5 sürümünde geliştirilmiştir. <xref:System.Net.Sockets.Socket>Özel yüksek performanslı yuva uygulamaları tarafından kullanılabilen alternatif bir zaman uyumsuz model sağlayan bir sınıf geliştirme kümesinin parçası olarak bir dizi yeni sınıf eklenmiştir. Bu geliştirmeler özellikle yüksek performans gerektiren ağ sunucusu uygulamaları için tasarlanmıştır. Bir uygulama geliştirilmiş zaman uyumsuz modelini özel olarak veya yalnızca uygulamalarının hedeflenen etkin alanlarında kullanabilir (örneğin, büyük miktarlarda veri alırken).  
  
## <a name="class-enhancements"></a>Sınıf geliştirmeleri  
 Bu geliştirmelerin ana özelliği, yüksek hacimli zaman uyumsuz yuva g/ç sırasında nesnelerin yinelenen ayırma ve eşitlemesine yönelik engelleme. Şu anda <xref:System.Net.Sockets.Socket> zaman uyumsuz yuva g/ç için sınıf tarafından uygulanan başlangıç/bitiş tasarım deseninin <xref:System.IAsyncResult?displayProperty=nameWithType> her zaman uyumsuz yuva işlemi için bir nesne ayrılması gerekir.  
  
 Yeni <xref:System.Net.Sockets.Socket> sınıf geliştirmelerinden zaman uyumsuz yuva işlemleri, <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> uygulama tarafından ayrılan ve korunan yeniden kullanılabilir sınıf nesneleri tarafından açıklanmıştır. Yüksek performanslı soket uygulamaları, sürekli olması gereken örtüşen yuva işlemlerinin en iyi miktarını bilir. Uygulama, ihtiyacı olan nesnelerin birçoğu tarafından oluşturulabilir <xref:System.Net.Sockets.SocketAsyncEventArgs> . Örneğin, bir sunucu uygulamasının gelen istemci bağlantı hızlarını desteklemesi için her zaman bekleyen 15 soketli kabul etme işlemi olması gerekiyorsa, bu amaçla 15 yeniden kullanılabilir <xref:System.Net.Sockets.SocketAsyncEventArgs> nesne daha önceden ayrılabilir.  
  
 Bu sınıfla zaman uyumsuz yuva işlemi gerçekleştirmeye yönelik model aşağıdaki adımlardan oluşur:  
  
1. Yeni bir <xref:System.Net.Sockets.SocketAsyncEventArgs> bağlam nesnesi ayırın veya bir uygulama havuzundan ücretsiz olarak alın.  
  
2. Bağlam nesnesindeki özellikleri gerçekleştirilecek işleme (örneğin, geri çağırma temsilcisi yöntemi ve veri arabelleği) ayarlayın.  
  
3. Zaman uyumsuz işlemi başlatmak için uygun yuva yöntemini (xxxAsync) çağırın.  
  
4. Zaman uyumsuz yuva yöntemi (xxxAsync) geri çağırmada true döndürürse, tamamlanma durumu için bağlam özelliklerini sorgulayın.  
  
5. Zaman uyumsuz yuva yöntemi (xxxAsync) geri çağırmada yanlış döndürürse, işlem zaman uyumlu olarak tamamlanır. Bağlam özellikleri, işlem sonucu için sorgulanabilecek.  
  
6. Bağlamı başka bir işlem için yeniden kullanın, havuza geri koyun veya atın.  
  
 Yeni zaman uyumsuz yuva işlemi bağlam nesnesinin yaşam süresi, uygulama kodundaki ve zaman uyumsuz g/ç başvurularıyla belirlenir. Uygulamanın zaman uyumsuz yuva işlemi yöntemlerinden birine bir parametre olarak gönderildikten sonra zaman uyumsuz bir yuva işlemi bağlam nesnesine başvuruyu tutmasına gerek yoktur. Tamamlama geri araması dönene kadar başvurulan olarak kalır. Ancak, uygulamanın, daha sonra zaman uyumsuz yuva işlemi için yeniden kullanılabilmesi için bağlam nesnesine başvuruyu korumasını avantajlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>
- [Ağ Programlama Örnekleri](network-programming-samples.md)
- [Yuva Kod Örnekleri](socket-code-examples.md)
