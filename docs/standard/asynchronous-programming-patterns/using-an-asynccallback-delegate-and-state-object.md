---
description: 'Hakkında daha fazla bilgi edinin: bir AsyncCallback temsilcisi ve durum nesnesi kullanma'
title: Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
ms.openlocfilehash: b7ffb3180d7e2e15a12d3bf0f98311b0310112e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732242"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma

<xref:System.AsyncCallback>Zaman uyumsuz işlemin sonuçlarını ayrı bir iş parçacığında işlemek için bir temsilci kullandığınızda, geri çağrılar arasında bilgi geçirmek ve nihai sonucu almak için bir durum nesnesi kullanabilirsiniz. Bu konuda, [zaman uyumsuz bir Işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)içindeki örneği genişleterek bu alıştırma gösterilmektedir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, <xref:System.Net.Dns> Kullanıcı tarafından belirtilen bilgisayarlar Için etki alanı adı sistemi (DNS) bilgilerini almak üzere sınıfında zaman uyumsuz yöntemleri kullanmayı gösterir. Bu örnek, `HostRequest` durum bilgilerini depolamak için sınıfını tanımlar ve kullanır. `HostRequest`Kullanıcı tarafından girilen her bilgisayar adı için bir nesne oluşturulur. Bu nesne <xref:System.Net.Dns.BeginGetHostByName%2A> yöntemine geçirilir. `ProcessDnsInformation`Yöntemi, istek her tamamlandığında çağrılır. `HostRequest`Nesnesi, özelliği kullanılarak alınır <xref:System.IAsyncResult.AsyncState%2A> . `ProcessDnsInformation`Yöntemi, `HostRequest` <xref:System.Net.IPHostEntry> istek tarafından döndürülen veya istek tarafından oluşturulan bir öğesini depolamak için nesnesini kullanır <xref:System.Net.Sockets.SocketException> . Tüm istekler tamamlandığında, uygulama nesneler üzerinde dolaşır `HostRequest` ve DNS bilgilerini veya <xref:System.Net.Sockets.SocketException> hata iletisini görüntüler.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](event-based-asynchronous-pattern-overview.md)
- [Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
