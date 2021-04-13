---
title: 'Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma'
description: .NET Framework 4 veya üstünü desteklemek üzere masaüstü uygulamanızı nasıl yapılandıracağınızı öğrenmek için dahil edilen örneği kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- configuring apps to support .NET Framework
- .NET Framework, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
ms.openlocfilehash: 66a6ec5f6cad0225e48f480eeae8b7d3862241dd
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369692"
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-later-versions"></a>Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma

Ortak dil çalışma zamanını (CLR) barındıran tüm uygulamaların, yönetilen kodu çalıştırmak için CLR 'yi başlatması veya *etkinleştirmesi* gerekir. Genellikle, bir .NET Framework uygulama üzerinde oluşturulduğu CLR sürümünde çalışır, ancak bir uygulama yapılandırma dosyası (bazen app.config dosyası olarak adlandırılır) kullanarak masaüstü uygulamaları için bu davranışı değiştirebilirsiniz. Ancak bir uygulama yapılandırma dosyası Windows Mağazası uygulamaları ya da Windows Phone uygulamaları için varsayılan etkinleştirme davranışını değiştiremezsiniz. Bu makalede, masaüstü uygulamanızın .NET Framework başka bir sürümünde çalışacak şekilde nasıl etkinleştirileceği ve sürüm 4 veya sonraki sürümlerin nasıl hedefleneceği hakkında bir örnek verilmiştir.

 Bir uygulamanın üzerinde çalıştığı .NET Framework sürümü aşağıdaki sırada belirlenir:

- Yapılandırma dosyası.

     Uygulama yapılandırma dosyası [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) bir veya daha fazla .NET Framework sürümünü belirten girişler içeriyorsa ve bu sürümlerden biri kullanıcının bilgisayarında mevcutsa, uygulama o sürümde çalışır. Yapılandırma dosyası [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) girişleri listelendikleri sırada okur ve kullanıcının bilgisayarında mevcut olan ilk .NET Framework sürümünü kullanır. (Sürüm 1,0 için [ \<requiredRuntime> öğesini](../configure-apps/file-schema/startup/requiredruntime-element.md) kullanın.)

- Derlenmiş sürüm.

     Bir yapılandırma dosyası yoksa, ancak uygulamanın oluşturulduğu .NET Framework sürümü kullanıcının makinesinde mevcutsa, uygulama o sürümde çalışır.

- En son sürüm yüklendi.

     Uygulamanın üzerinde oluşturulduğu .NET Framework sürümü yoksa ve yapılandırma dosyası bir [ \<supportedRuntime> öğesinde](../configure-apps/file-schema/startup/supportedruntime-element.md)bir sürüm belirtmezse, uygulama, kullanıcının bilgisayarında mevcut olan .NET Framework en son sürümünü çalıştırmayı dener.

     Ancak .NET Framework 1.0, 1.1, 2.0, 3.0 ve 3.5 uygulamaları, .NET Framework 4 ve sonraki sürümleri otomatik çalıştırmaz ve bazı durumlarda kullanıcı bir hata alabilir ve kullanıcının .NET Framework 3.5 yüklemesi istenebilir. Windows sisteminin farklı sürümleri .NET Framework'ün farklı sürümlerinin içerdiğinden etkinleştirme davranışı kullanıcının işletim sistemine de bağlı olabilir. Uygulamanız hem .NET Framework 3.5 hem de 4 ve üstünü destekliyorsa, .NET Framework başlatma hatalarını önlemek için bunu yapılandırma dosyasında birden çok giriş işe belirtmenizi öneririz. Daha fazla bilgi için bkz. [sürümler ve bağımlılıklar](versions-and-dependencies.md).

 Ayrıca, sürüm 4 ve sonraki sürümlerindeki performans iyileştirmelerinden faydalanmak için, .NET Framework 3,5 uygulamalarınızı .NET Framework 4 veya sonraki sürümlerde .NET Framework 3,5 yüklü bilgisayarlarda bile çalışacak şekilde yapılandırmak isteyebilirsiniz.

> [!IMPORTANT]
> Uygulamanızı desteklediğiniz her .NET Framework sürümünde her zaman test etmenizi öneririz. Daha sonra .NET Framework sürümlerini desteklemek üzere uygulamanızı yükseltme hakkında bilgi için bkz. [sürüm uyumluluğu](version-compatibility.md) .

 .NET Framework 1,0 ve 1,1 uygulamalarınızı Windows 7 ve Windows 8 ' i destekleyecek şekilde değiştirme hakkında bilgi için, bkz. [.NET Framework 1,1 ' den geçiş](migrating-from-the-net-framework-1-1.md).

## <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-later-versions"></a>Uygulamanızı .NET Framework 4 veya sonraki sürümlerde çalışacak şekilde yapılandırmak için

1. .NET Framework projesinin yapılandırma dosyasını ekleyin ya da bulun. Bir uygulamanın yapılandırma dosyası aynı dizindedir ve uygulama ile aynı ada ancak .config uzantısına sahiptir. Örneğin, MyExecutable.exe adlı bir uygulama için uygulama yapılandırma dosyası MyExecutable.exe.config olarak adlandırılır.

     Bir yapılandırma dosyası eklemek için, Visual Studio menü çubuğunda **Proje**, **Yeni öğe Ekle**' yi seçin. Sol bölmeden **genel** ' i ve ardından **yapılandırma dosyası**' nı seçin. Yapılandırma dosyasını *App.config* olarak adlandırın. Bu platformlardaki etkinleştirme ilkesini değiştiremediğinden bu menü seçenekleri Windows Mağazası uygulaması veya Windows Phone uygulama projeleri için kullanılamaz.

2. [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md)Öğesini uygulama yapılandırma dosyasına aşağıdaki şekilde ekleyin:

    ```xml
    <configuration>
      <startup>
        <supportedRuntime version="version"/>
      </startup>
    </configuration>
    ```

     Burada *\<version>* , uygulamanızın desteklediği .NET Framework sürümle HIZALANAN CLR sürümünü belirtir. Aşağıdaki dizeleri kullanın:

    - .NET Framework 1.0: "v1.0.3705"

    - .NET Framework 1.1: "v1.1.4322"

    - .NET Framework 2.0, 3.0 ve 3.5: "v2.0.50727"

    - .NET Framework 4 ve sonraki sürümler: "v 4.0"

     [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md).NET Framework birden çok sürümü için destek belirtmek üzere tercih sırasına göre listelenen birden çok öğe ekleyebilirsiniz.

 Aşağıdaki tablo, bir bilgisayara yüklenen uygulama yapılandırma dosyası ayarlarının ve .NET Framework sürümlerinin bir .NET Framework 3.5 uygulamasının üzerinde çalıştığı sürümü nasıl belirlediğini göstermektedir. Örnekler, .NET Framework 3.5 uygulamasına özgüdür, ancak daha eski .NET Framework sürümlerini kullanarak oluşturulan hedef uygulamalar için de aynı mantığı kullanabilirsiniz. NET Framework 2.0 sürüm numarasının (v2.0.50727), uygulama yapılandırma dosyasında .NET Framework 3.5'i belirtmek için kullanıldığını unutmayın.

|App.config dosyası ayarı|3.5 sürümü yüklü bilgisayarda|3,5 sürümleri ve 4 veya sonraki sürümleri yüklü olan bilgisayarda|Sürüm 4 veya sonraki sürümleri yüklü bilgisayarda|
|-|-|-|-|
|Yok|3.5 üzerinde çalışır|3.5 üzerinde çalışır|Kullanıcının doğru sürümü* yüklemesini isteyen hata iletisini görüntüler|
|`<supportedRuntime version="v2.0.50727"/>`|3.5 üzerinde çalışır|3.5 üzerinde çalışır|Kullanıcının doğru sürümü* yüklemesini isteyen hata iletisini görüntüler|
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|3.5 üzerinde çalışır|3.5 üzerinde çalışır|4 veya sonraki sürümlerde çalışır|
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|3.5 üzerinde çalışır|4 veya sonraki sürümlerde çalışır|4 veya sonraki sürümlerde çalışır|
|`<supportedRuntime version="v4.0"/>`|Kullanıcının doğru sürümü* yüklemesini isteyen hata iletisini görüntüler|4 veya sonraki sürümlerde çalışır|4 veya sonraki sürümlerde çalışır|

 \* Bu hata iletisi ve bunu önlemenin yolları hakkında daha fazla bilgi için bkz. [.NET Framework başlatma hataları: Kullanıcı deneyimini yönetme](../deployment/initialization-errors-managing-the-user-experience.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 1.1'den Geçiş](migrating-from-the-net-framework-1-1.md)
- [Geçiş Kılavuzu](index.md)
