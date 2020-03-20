---
title: 'Azaltma: Uygulama Etki Alanlarında Nesneleri Seri Durumdan Çıkarma'
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
ms.openlocfilehash: e2d90a77cab699646bd31eaa162d1bd1744fd51b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457932"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a>Azaltma: Uygulama Etki Alanlarında Nesneleri Seri Durumdan Çıkarma
Bazı durumlarda, bir uygulama farklı uygulama temeli kullanan iki veya daha fazla uygulama etki alanı kullandığında, uygulama etki alanları arasında nesnelerin mantıksal çağrı bağlamında serisini kaldırma girişimi özel bir durum oluşturur.  
  
## <a name="diagnosing-the-issue"></a>Sorunu tanılama  
 Sorun, sırasıyla aşağıdaki koşullar altında ortaya çıkar:  
  
1. Bir uygulama, farklı uygulama temel dizini kullanan iki veya daha fazla uygulama etki alanı kullanır.  
  
2. Bazı türler, <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> veya <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> gibi bir yöntem çağrılarak açıkça <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType> içine eklenir. Bu türler seri hale getirilebilir olarak işaretlenmez ve genel bütünleştirilmiş derleme önbelleği içinde saklanmaz.  
  
3. Daha sonra, varsayılan olmayan uygulama etki alanında çalışan kod, bir yapılandırma dosyasından değer okumayı veya bir nesnenin serisini kaldırmak için XML kullanmayı dener.  
  
4. Bir yapılandırma dosyasından okumak veya nesnenin serisini kaldırmak için, bir <xref:System.Xml.XmlReader> nesnesi yapılandırma sistemine erişmeyi dener.  
  
5. Eğer yapılandırma sistemi daha başlatılmadıysa, başlatılmasını tamamlamalıdır. Bu, diğer şeylerin yanı sıra, çalışma zamanının bir yapılandırma sistemi için tutarlı bir yol oluşturması gerektiği anlamına gelir ki bunu aşağıdaki şekilde gerçekleştirir:  
  
    1. Varsayılan olmayan uygulama etki alanı için kanıt arar.  
  
    2. Varsayılan uygulama etki alanını temel alarak, varsayılan olmayan etki alanı için olan kanıtları hesaplamayı dener.  
  
    3. Varsayılan uygulama etki alanı için kanıt alma çağrısı, varsayılan olmayan uygulama etki alanından varsayılan uygulama etki alanına, uygulama etki alanları arasında bir çağrıyı tetikler.  
  
    4. .NET Framework'teki uygulama etki alanları arası anlaşması kapsamında, mantıksal çağrı bağlamının içeriğinin uygulama etki alanı sınırları arasında sıralanması gerekir.  
  
6. Mantıksal çağrı bağlamındaki türler varsayılan uygulama etki alanında çözümlenemediği için, bir özel durum oluşturulur.  
  
## <a name="mitigation"></a>Risk azaltma  
 Bu sorunun geçici çözümü için, aşağıdakini yapın  
  
1. Özel durumun oluşturulduğu çağrı yığınındaki `get_Evidence` çağrısını bulun. Özel durum, <xref:System.IO.FileNotFoundException> ve <xref:System.Runtime.Serialization.SerializationException> dahil birçok özel durumun ait olduğu büyük bir alt kümedeki özel durumlardan herhangi biri olabilir.  
  
2. Uygulamada mantıksal çağrı bağlamına hiçbir nesnenin eklenmediği yeri bulun ve aşağıdaki kodu ekleyin:  
  
    ```csharp
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
