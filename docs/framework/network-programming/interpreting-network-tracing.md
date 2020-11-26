---
title: Ağ İzlemeyi Yorumlama
description: Uygulamanızın .NET Framework çeşitli System.Net sınıf üyelerine yaptığı çağrıları yakalamak için izlemeyi nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 63d7e36bb95054303fc4f26b0fd14dc3d10dbb7d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241570"
---
# <a name="interpreting-network-tracing"></a>Ağ İzlemeyi Yorumlama

Ağ izleme etkinleştirildiğinde, uygulamanızın çeşitli sınıf üyelerine yaptığı çağrıları yakalamak için izlemeyi kullanabilirsiniz <xref:System.Net> . Bu çağrılardan alınan çıkış aşağıdaki örneklere benzer olabilir.  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 Yukarıdaki örnekte, [588] geçerli iş parçacığının benzersiz tanımlayıcısıdır. (4357) ve (4387), uygulamanın başlatılmasından bu yana geçen milisaniye sayısını belirten tarih damgalardır. Zaman damgasından sonraki veriler, uygulamanın **yuva. Send** yöntemine giriş ve çıkış yöntemini gösterir. **Send** metodunu yürüten nesne benzersiz tanımlayıcı olarak 33574638 sahiptir. Çıkış izleme yöntemi, dönüş değerini (önceki örnekte 61) içerir.  
  
 Ağ izlemeleri, uygulamanız tarafından gönderilen veya alınan ve Köprü Metni Aktarım Protokolü (HTTP) gibi uygulama düzeyi protokoller kullanılarak gönderilen ağ trafiğini yakalayabilir. Bu veriler metin ve isteğe bağlı olarak onaltılık veri olarak yakalanabilir. **TraceMode** özniteliğinin değeri olarak **ıncludehex** belirttiğinizde onaltılık veriler kullanılabilir. (Bu öznitelikle ilgili ayrıntılı bilgi için bkz. [nasıl yapılır: ağ Izlemeyi yapılandırma](how-to-configure-network-tracing.md).) Aşağıdaki örnek izleme **ıncludehex** kullanılarak oluşturulmuştur.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Onaltılık verileri atlamak için, yalnızca bir **TraceMode** özniteliği değeri olarak **protocolbelirtin** . Aşağıdaki örnek, **yalnızca protocolbelirtildiğinde** izlemeyi gösterir.  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ İzlemeyi Etkinleştirme](enabling-network-tracing.md)
- [Nasıl yapılır: Ağ İzlemeyi Yapılandırma](how-to-configure-network-tracing.md)
- [.NET Framework'te Ağ İzleme](network-tracing.md)
