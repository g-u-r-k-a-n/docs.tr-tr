---
title: WCF geliştiricileri için Yük Dengeleme gRPC-gRPC
description: GRPC hizmetleriyle çalışmak için bir yük dengeleyici seçme.
ms.date: 12/15/2020
ms.openlocfilehash: 55f61608dce1f159b11d7265a47938ba49e9e188
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938591"
---
# <a name="load-balancing-grpc"></a>GRPC yük dengelemesi

Bir gRPC uygulamasının tipik bir dağıtımı, hizmetin bir dizi özdeş örneğini içerir, bu da esnekliği ve yatay ölçeklenebilirlik sağlar. Yük Dengeleme, tüm kullanılabilir kaynakların tam kullanımını sağlamak için gelen istekleri bu örneklerde dağıtır. Bu yük dengelemeyi istemcide görünmez hale getirmek için, istemcilerden gelen istekleri işlemek ve arka uç örneklerine yönlendirmek için bir proxy yük dengeleyici sunucusu kullanılması yaygındır.

Yük dengeleyiciler üzerinde çalıştıkları *katmana* göre sınıflandırılmaktadır. Katman 4 yük dengeleyiciler *Aktarım* düzeyinde (ÖRNEĞIN, TCP yuvaları, bağlantılar ve paketlerle) çalışır. Katman 7 yük dengeleyiciler, özel olarak gRPC uygulamaları için HTTP/2 isteklerini işleyerek *uygulama* düzeyinde çalışır.

## <a name="l4-load-balancers"></a>L4 yük dengeleyiciler

Bir L4 yük dengeleyici bir istemciden gelen TCP bağlantı isteğini kabul eder, arka uç örneklerinden birine başka bir bağlantı açar ve gerçek bir işleme olmadan iki bağlantı arasında verileri kopyalar. L4, mükemmel performans ve düşük gecikme süresi sunar, ancak çok az denetim veya zeka sağlar. İstemci bağlantıyı açık sakladığı sürece tüm istekler aynı arka uç örneğine yönlendirilir.

 [Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) , bir L4 yük dengeleyiciye bir örnektir.

## <a name="l7-load-balancers"></a>L7 yük dengeleyiciler

Bir L7 yük dengeleyici gelen HTTP/2 isteklerini ayrıştırır ve bağlantının istemci tarafından ne kadar süreceğine bakılmaksızın bunları istek temelli olarak bir istek temelinde, arka uç örneklerine geçirir.

L7 yük dengeleyiciler örnekleri:

- [NGıNX](https://www.nginx.com/)
- [HAProxy](https://www.haproxy.com/)
- [Traefik](https://traefik.io/)

Bir Thumb kuralı olarak, L7 yük dengeleyiciler gRPC ve diğer HTTP/2 uygulamaları için en iyi seçenektir (ve genellikle HTTP uygulamaları için). L4 yük dengeleyiciler gRPC uygulamalarıyla *çalışır* , ancak düşük gecikme süresi ve düşük ek yük önemli olduğunda özellikle faydalıdır.

> [!IMPORTANT]
> Bu yazma sırasında, bazı L7 yük dengeleyiciler, üst bilgiler gibi gRPC Hizmetleri için gerekli olan HTTP/2 belirtiminin tüm parçalarını desteklemez.

TLS şifrelemesini kullanıyorsanız, yük dengeleyiciler TLS bağlantısını sonlandırabilir ve şifrelenmemiş istekleri arka uç uygulamasına geçirebilir veya şifreli isteği de geçirebilir. Her iki durumda da yük dengeleyicinin, işleme isteklerinin şifresini çözebilmesi için sunucunun ortak ve özel anahtarıyla yapılandırılması gerekir.

Arka uç hizmetleriniz ile HTTP/2 isteklerini işlemek üzere nasıl yapılandıracağınızı öğrenmek için tercih ettiğiniz yük dengeleyiciye yönelik belgelere bakın.

## <a name="load-balancing-within-kubernetes"></a>Kubernetes içinde yük dengeleme

Kubernetes 'deki iç hizmetlerde yük dengelemenin tartışılması için [hizmet kafesleri bölümüne](service-mesh.md) bakın.

>[!div class="step-by-step"]
>[Önceki](service-mesh.md) 
> [Sonraki](application-performance-management.md)
