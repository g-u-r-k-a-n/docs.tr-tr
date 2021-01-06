---
title: Ağ protokolleri-WCF geliştiricileri için gRPC
description: GRPC ağ protokollerine genel bakış.
ms.date: 09/02/2019
ms.openlocfilehash: 801d57c95aec748e5dcf667ca480775ff945b55c
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938565"
---
# <a name="network-protocols"></a>Ağ protokolleri

Windows Communication Foundation (WCF) aksine gRPC, ağı için bir taban olarak HTTP/2 kullanır. Bu protokol, WCF ve SOAP üzerinde yalnızca HTTP/1.1 üzerinde çalışan önemli avantajlar sunar. GRPC 'yi kullanmak isteyen geliştiriciler için, HTTP/2 için başka bir seçenek olmadığından, HTTP/2 ' yi daha ayrıntılı bir şekilde incelemek ve gRPC kullanmanın ek avantajlarını belirlemek için ideal bir süre görünür.

2015 ' de Internet Mühendisliği görev gücü tarafından yayınlanan HTTP/2, zaten Google tarafından kullanılmakta olan deneysel SPDY protokolünden türetilmiştir. Özellikle HTTP/1.1 'den daha verimli, daha hızlı ve daha güvenli olacak şekilde tasarlanmıştır.

## <a name="key-features-of-http2"></a>HTTP/2 ' nin önemli özellikleri

Bu listede HTTP/2 ' nin bazı temel özellikleri ve avantajları gösterilmektedir:

### <a name="binary-protocol"></a>İkili protokol

İstek/yanıt döngülerinde artık metin komutlarına gerek yok. Bu etkinlik, komutlarının uygulanmasını basitleştirir ve hızlandırır. Özellikle, verileri ayrıştırmak daha hızlıdır ve daha az bellek kullanır, ağ gecikmesi, hızsız ilgili açık geliştirmeler ve ağ kaynaklarının genel olarak daha iyi kullanıldığı bir şekilde azaltılır.

### <a name="streams"></a>Akışlar

Akışlar, gönderici ve alıcı arasında çok fazla ileti veya çerçevenin zaman uyumsuz olarak gönderilebileceği uzun süreli bağlantılar oluşturmanızı sağlar. Birden çok akış, tek bir HTTP/2 bağlantısı üzerinden bağımsız olarak çalışabilir.

### <a name="request-multiplexing-over-a-single-tcp-connection"></a>Tek bir TCP bağlantısı üzerinden çoğullama isteme

Bu özellik HTTP/2 ' nin en önemli yeniliklerinden biridir. Veriler için birden çok paralel isteğe izin verdiğinden, artık Web dosyalarını tek bir sunucudan aynı anda indirmek mümkündür. Web siteleri daha hızlı yüklenir ve iyileştirme gereksinimi azaltılır. Daha önceki bir istek tamamlanana kadar, izin verilen yanıtların gönderilmesini beklemesi gereken, satır başı (HOL) engelleme, aynı zamanda da azaltılmalıdır (ancak, HOL engelleme yine de TCP-Transport düzeyinde gerçekleşecektir).

### <a name="nettcp-like-performance-cross-platform"></a>Net. TCP benzeri performans, platformlar arası

Temel olarak, gRPC ve HTTP/2 ' nin birleşimi, geliştiricilere en azından WCF için net. TCP bağlamalarının ve bazı durumlarda daha fazla hız ve verimlilik sağlayan, büyük hız ve verimlilik sunmaktadır. Ancak, net. TCP 'den farklı olarak, HTTP/2 üzerinden gRPC, .NET uygulamalarıyla sınırlı değildir.

>[!div class="step-by-step"]
>[Önceki](interface-definition-language.md) 
> [Sonraki](why-grpc.md)
