---
title: Derleme Bağlama Yönlendirmesini Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: c7b9dcb99e08a1ef2844c5811897aa87ff86f866
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716562"
---
# <a name="configuring-assembly-binding-redirection"></a>Derleme Bağlama Yönlendirmesini Yapılandırma
Uygulamalar, varsayılan olarak, uygulamayı derlemek için kullanılan çalışma zamanı sürümüyle birlikte gelen .NET Framework derlemeleri kümesini kullanır. Derleme bağlama başvurularını .NET Framework derlemelerinin belirli bir sürümüne yönlendirmek için bir uygulama yapılandırma dosyasında [\<assemblyBinding >](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) öğesinde **AppliesTo** özniteliğini kullanabilirsiniz. Bu isteğe bağlı öznitelik, hangi sürümün uygulanacağını göstermek için .NET Framework bir sürüm numarası kullanır. Hiçbir **AppliesTo** özniteliği belirtilmemişse, **\<assemblyBinding >** öğesi tüm .NET Framework sürümleri için geçerlidir.  
  
 **AppliesTo** özniteliği .NET Framework sürüm 1,1 ' de tanıtılmıştı; .NET Framework 1,0 sürümü tarafından yok sayılır. Bu, bir **AppliesTo** özniteliği belirtilmiş olsa bile .NET Framework sürüm 1,0 kullanılırken tüm **\<assemblyBinding >** öğelerinin uygulandığı anlamına gelir.  
  
> [!NOTE]
> Derleme bağlama yeniden yönlendirmesini, çalışma zamanının belirli bir sürümüyle sınırlamak için **AppliesTo** özniteliğini kullanın.  
  
 Örneğin, .NET Framework sürüm 1,0 derlemesi için derleme bağlamayı yeniden yönlendirmek için, uygulama yapılandırma dosyanıza aşağıdaki XML kodunu dahil edersiniz.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 **\<AssemblyBinding >** sipariş duyarlı öğeleridir. Önce .NET Framework herhangi bir sürüm 1,0 derlemesi için derleme bağlama yeniden yönlendirme bilgilerini, ardından herhangi bir .NET Framework sürümü 1,1 derlemesi için derleme bağlama yeniden yönlendirme bilgilerini girmeniz gerekir. Son olarak, **AppliesTo** özniteliğini kullanmayan ve bu nedenle .NET Framework tüm sürümleri için geçerli olan tüm .NET Framework bütünleştirilmiş kod yönlendirmesi için derleme bağlama yeniden yönlendirme bilgilerini girin. Yeniden yönlendirmenin bir çakışma olması durumunda, yapılandırma dosyasındaki ilk eşleşen yeniden yönlendirme ekstresi kullanılır.  
  
 Örneğin, bir başvuruyu .NET Framework sürüm 1,0 derlemesine ve .NET Framework sürüm 1,1 derlemesine başka bir başvuruya yeniden yönlendirmek için aşağıdaki sözde kodda gösterilen kalıbı kullanacaksınız.  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
  <!-- .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
  <!-- .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
  <!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a>Yapılandırma Dosyası Hatalarını Ayıklama  
 Çalışma zamanı, bir uygulama etki alanı oluşturulduğunda yapılandırma dosyalarını bir kez ayrıştırır ve kodu bu uygulama etki alanına yükler. Ortak dil çalışma zamanı, girdiyi yoksayarak bir yapılandırma dosyasındaki hataları işler. Çalışma zamanı, hatalı biçimlendirilmiş XML içeriyorsa tüm yapılandırma dosyalarını yoksayar. Geçersiz XML için yalnızca geçersiz bölümler yok sayılır.  
  
 Derleme bağlama yeniden yönlendirmelerinin oluşup oluşmadığını belirleyerek bir yapılandırma dosyasının kullanılıp kullanılmadığını belirleyebilirsiniz. Hangi derlemelerin yüklenmekte olduğunu görmek için [derleme bağlama günlüğü görüntüleyicisini (Fuslogvw. exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) kullanın. Tüm derleme bağlamalarını görmek için kayıt defterinde **ForceLog** için bir girdi ayarlamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
