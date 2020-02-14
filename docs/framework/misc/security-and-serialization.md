---
title: Güvenlik ve Serileştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
ms.openlocfilehash: cb0ba120eeb57788c0525d45b714ad8edd2c39ed
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216970"
---
# <a name="security-and-serialization"></a>Güvenlik ve Serileştirme
Serileştirme diğer kodun başka bir şekilde erişilemeyen nesne örneği verilerini görmesine veya değiştirmesine izin abileceğinden, kod serileştirme: <xref:System.Security.Permissions.SecurityPermission> belirtilen <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> bayrağıyla özel bir izin gerekir. Varsayılan ilke altında, bu izin Internet 'Ten indirilen veya intranet koduna verilmez; yalnızca yerel bilgisayardaki koda bu izin verilir.  
  
 Normalde, bir nesne örneğinin tüm alanları serileştirilir ve bu, verilerin örnek için seri hale getirilmiş verilerde temsil edildiği anlamına gelir. Veri değerlerinin ne olduğunu, üyenin erişilebilirliğiyle bağımsız olarak belirlemek için biçimi yorumlayabilen kod mümkündür. Benzer şekilde, seri durumdan çıkarma, verileri serileştirilmiş gösterimden ayıklar ve doğrudan, nesne durumunu erişilebilirlik kurallarından bağımsız olarak ayarlar.  
  
 Güvenlik duyarlı veriler içerebilen herhangi bir nesne, mümkünse seri hale getirilebilir olmayan bir şekilde yapılmalıdır. Seri hale getirilebilir olması gerekiyorsa, gizli verileri tutan, seri hale getirilebilen belirli alanları yapmayı deneyin. Bu işlem yapılabiliyorsa, bu verilerin serileştirme izni olan herhangi bir koda sunulamadığını ve kötü amaçlı bir kodun bu izni alamazsanız emin olun.  
  
 <xref:System.Runtime.Serialization.ISerializable> arabirimi yalnızca serileştirme altyapısı tarafından kullanılmaya yöneliktir. Ancak korumasız ise, hassas bilgileri serbest bırakabilir. **ISerializable**uygulayarak özel serileştirme sağlarsanız, aşağıdaki önlemleri aldığınızdan emin olun:  
  
- <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi, **SerializationFormatter** Iznine sahip **SecurityPermission** 'ı belirtilen veya yöntem çıkışıyla hiçbir hassas bilgi yayınlanmadan emin olarak açıkça güvenli hale getirmelidir. Örneğin:  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter   
    =true)]  
    public override void GetObjectData(SerializationInfo info,   
    StreamingContext context)  
    {  
    }  
    ```  
  
- Serileştirme için kullanılan özel Oluşturucu ayrıca tam giriş doğrulaması gerçekleştirmeyi ve kötü amaçlı kodun kötüye kullanılmasına karşı korumaya yardımcı olmak için korumalı veya özel olmalıdır. Bu, sınıfın açıkça oluşturulması veya bir tür fabrika aracılığıyla dolaylı olarak oluşturulması gibi bazı yollarla bu tür bir sınıfın bir örneğini almak için gereken güvenlik denetimlerini ve izinlerini zorunlu kılar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
