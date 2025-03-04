---
title: .NET Framework'te Ağ İzleme
description: Yönetilen bir uygulama için yöntem etkinleştirmeleri ve ağ trafiği hakkında bilgi sağlayan .NET Framework ağ izleme hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework], network tracing
- methods, network tracing
- Networking
- trace enabled debugging
- network tracing, about network tracing
- network tracing
- network, network tracing
- traffic tracing
- tracing [.NET Framework], network
- deploying applications [.NET Framework], network traffic
- capturing network traffic
- Internet, network tracing
- Network Resources
- output, network tracing
- method invocations
ms.assetid: e993b7c3-087f-45d8-9c02-9dded936d804
ms.openlocfilehash: c3c710d99c9597120b0c4d9674439a27c3bedfcc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261689"
---
# <a name="network-tracing-in-the-net-framework"></a>.NET Framework'te Ağ İzleme

.NET Framework'te ağ izleme, yönetilen uygulama tarafından oluşturulan yöntem çağrıları ve ağ trafiğiyle ilgili bilgilere erişim sağlar. Bu özellik, geliştirilen uygulamalarda hata ayıklanırken ve dağıtılan uygulamalar analiz edilirken yararlı olur. Ağ izleme tarafından sağlanan çıkış, geliştirme zamanı ve üretim ortamında farklı kullanım senaryolarını destekleyecek şekilde özelleştirilebilir.  
  
 .NET Framework'te ağ izlemeyi etkinleştirmek üzere izleme çıkışı için bir hedef seçmeniz ve ağ izleme yapılandırma ayarlarını uygulamaya ve makine yapılandırma dosyasına eklemeniz gerekir. Yapılandırma dosyalarının açıklamaları ve bunların nasıl kullanıldığı hakkında bilgi için bkz. [yapılandırma dosyaları](../configure-apps/index.md). Ağ izlemeyi etkinleştirme hakkında daha fazla bilgi için bkz. [ağ Izlemeyi etkinleştirme](enabling-network-tracing.md). Yapılandırma dosyasına eklemeniz gereken ayarlar hakkında daha fazla bilgi için bkz. [nasıl yapılır: ağ Izlemeyi yapılandırma](how-to-configure-network-tracing.md).  
  
 İzleme etkinleştirildiğinde, **System.net** sınıfları tarafından çıktı olan izleme bilgilerini yakalayabilirsiniz. İzleme bilgileri oluşturan ağ sınıfı üyelerinin .NET Framework sınıf kitaplığı belgelerindeki Açıklamalar bölümünde aşağıdaki not vardır:  
  
> [!NOTE]
> Uygulamanızda ağ izlemeyi etkinleştirdiğinizde, bu üye izleme bilgilerini çıkarır. Daha fazla bilgi için bkz. Ağ İzleme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ İzlemeyi Etkinleştirme](enabling-network-tracing.md)
- [Nasıl yapılır: Ağ İzlemeyi Yapılandırma](how-to-configure-network-tracing.md)
- [Ağ İzlemeyi Yorumlama](interpreting-network-tracing.md)
- [Uygulamaları izleme ve İşaretleme](../debug-trace-profile/tracing-and-instrumenting-applications.md)
