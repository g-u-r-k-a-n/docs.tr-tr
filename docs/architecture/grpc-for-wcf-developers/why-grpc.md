---
title: WCF geliştiricileri için GRPC 'yi neden öneriyoruz
description: GRPC 'nin neden modern mimarilere ve platformlara geçiş yapmak isteyen WCF geliştiricileri için iyi bir uyum olduğuna ilişkin bir tartışma.
ms.date: 12/15/2020
ms.openlocfilehash: 058f85297610116e96c8580fcefb10ee6dfcf935
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97937980"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a>WCF geliştiricileri için gRPC’yi neden öneriyoruz?

GRPC 'nin diline ve tekniklerine ek olarak, gRPC 'nin .NET 'e geçiş yapmak isteyen Windows Communication Foundation (WCF) geliştiricileri için doğru çözüm olduğunu tartışmak de önemlidir.

## <a name="similarity-to-wcf"></a>WCF benzerliği

Uygulama ve yaklaşım gRPC için farklı olsa da, gRPC ile hizmetleri geliştirme ve kullanma deneyimi WCF geliştiricileri için sezgisel olmalıdır. Temel amaç aynıdır: ağ hakkında endişelenmenize gerek kalmadan, istemci ve sunucu aynı platformda olsa da kodun kodlanmasını sağlar.

Her iki platform da, bu arabirimi bildirme işlemi farklı olsa da, bir arabirimi oluşturma ve uygulama ilkesini paylaşır. Bölüm 5 ' te, gRPC 'nin WCF Hizmetleri için kullanılabilen bağlamalara yönelik eşlemeyi desteklediği farklı RPC çağrısı türleri de göreceğiniz gibi.

## <a name="benefits-of-grpc"></a>GRPC 'nin avantajları

gRPC, aşağıdaki nedenlerden dolayı diğer çözümlerin üzerine gelir.

### <a name="performance"></a>Performans

Http/1.1 yerine HTTP/2 kullanılması, insan tarafından okunabilen iletiler gereksinimini ortadan kaldırır ve bunun yerine daha küçük, daha hızlı ikili protokolü kullanır. Bu, bilgisayarların ayrıştırılmasında daha etkilidir. HTTP/2 aynı zamanda tek bir bağlantı üzerinden çoğullama isteklerini destekler. Bu destek, yanıtları bir kuyrukta beklemenize gerek kalmadan, yanıt verilen anda gönderilmek üzere kullanıma sunar. (HTTP/1.1 'de, bu sorun "satır başı (HOL) engelleme" olarak bilinir. GRPC kullanırken, mobil cihazlarda ve yavaş ağlarda kullanılması iyi bir çözüm sunan daha az kaynak gereklidir.

### <a name="interoperability"></a>Birlikte çalışabilirlik

.NET, Java, Python, Go, C++, Node.js, Swift, Dart, Ruby ve PHP dahil olmak üzere tüm önemli programlama dilleri ve platformları için gRPC araçları ve kitaplıkları vardır. Her platform için protokol arabelleklerinin ikili kablo biçimi ve verimli kod üretimi sayesinde, geliştiriciler, tam platformlar arası destekten hala keyif alırken performanslı uygulamalar oluşturabilir.

### <a name="usability-and-productivity"></a>Kullanılabilirlik ve üretkenlik

gRPC, kapsamlı bir RPC çözümüdür. Birden çok dil ve platformda sürekli olarak işe yarar. Ayrıca, gerekli ortak kodun büyük bölümü otomatik olarak oluşturulan mükemmel araçlar da sağlar. Böylece, iş mantığına odaklanmak için daha fazla geliştirici saati serbest bırakılır.

### <a name="streaming"></a>Akış

gRPC 'de, WCF 'nin tam çift yönlü hizmetlerine benzer işlevler sağlayan tam çift yönlü akış vardır. gRPC akışı, normal internet bağlantıları, yük dengeleyiciler ve hizmet kafesleri üzerinden çalışabilir.

### <a name="deadlinetimeouts-and-cancellation"></a>Son tarih/zaman aşımları ve iptal

gRPC, istemcilerin bir RPC 'nin tamamlaması için en uzun süreyi belirtmesini sağlar. Belirtilen son tarih aşılırsa sunucu, işlemi istemciden bağımsız olarak iptal edebilir. Son tarihler ve iptaller, kaynak kullanım sınırlarını zorlamaya yardımcı olmak için ek gRPC çağrıları aracılığıyla yayılamaz. İstemciler ayrıca son tarih aşıldığında veya daha önce (örneğin, bir kullanıcı etkileşimi nedeniyle) işlemleri durdurur.

### <a name="security"></a>Güvenlik

gRPC, bir TLS uçtan uca şifreli bağlantı üzerinden HTTP/2 kullanıyorsa, örtülü olarak güvenli hale gelir. İstemci sertifikası kimlik doğrulaması desteği (bkz. [Bölüm 6](security.md)) istemci ve sunucu arasındaki güvenliği ve güveni daha da artırır.

>[!div class="step-by-step"]
>[Önceki](network-protocols.md) 
> [Sonraki](protocol-buffers.md)
