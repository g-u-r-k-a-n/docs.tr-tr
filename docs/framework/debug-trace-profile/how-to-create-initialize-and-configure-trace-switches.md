---
title: 'Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma'
description: .NET 'teki System. Diagnostics. BooleanSwitch ve System. Diagnostics. TraceSwitch sınıflarını kullanarak izleme anahtarları oluşturun, başlatın ve yapılandırın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
ms.openlocfilehash: 4e8c076645f19e197ea820c052b20d5dde5e7565
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272260"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma

İzleme anahtarları, izleme çıkışını etkinleştirmenizi, devre dışı bırakmanızı ve filtrelemenizi sağlar.  
  
<a name="create"></a>

## <a name="creating-and-initializing-a-trace-switch"></a>İzleme anahtarı oluşturma ve başlatma  

 İzleme anahtarlarını kullanmak için, önce bunları oluşturmanız ve kodunuza yerleştirmeniz gerekir. Anahtar nesneleri oluşturabileceğiniz önceden tanımlanmış iki sınıf vardır: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> sınıfı ve <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> sınıfı. <xref:System.Diagnostics.BooleanSwitch>Yalnızca bir izleme iletisinin görünüp gösterilmediğini düşünüyorsanız, öğesini kullanarak <xref:System.Diagnostics.TraceSwitch> izleme düzeyleri arasında ayrım yapmak isteyebilirsiniz. Kullanıyorsanız <xref:System.Diagnostics.TraceSwitch> , kendi hata ayıklama iletilerinizi tanımlayabilir ve bunları farklı izleme düzeyleriyle ilişkilendirebilirsiniz. İzleme veya hata ayıklama ile her iki anahtar türünü de kullanabilirsiniz. Varsayılan olarak,, <xref:System.Diagnostics.BooleanSwitch> devre dışıdır ve, <xref:System.Diagnostics.TraceSwitch> düzeyi olarak ayarlanır <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType> . İzleme anahtarları, kodunuzun bunları kullanan herhangi bir kısmına oluşturulabilir ve eklenebilir.  
  
 Koddaki izleme düzeylerini ve diğer yapılandırma seçeneklerini ayarlayabilmenize karşın, anahtarlarınızın durumunu yönetmek için yapılandırma dosyasını kullanmanızı öneririz. Bunun nedeni, yapılandırma sistemindeki anahtarlarınızın yapılandırılmasını yönetmenin daha fazla esneklik sağladığından, uygulamanızı yeniden derlemeden çeşitli anahtarları açıp kapamenize ve seviyelerini değiştirmenize olanak sağlar.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>Bir izleme anahtarı oluşturmak ve başlatmak için  
  
1. Tür ya da tür olarak bir anahtar tanımlayın <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> ve anahtarın adını ve açıklamasını ayarlayın.  
  
2. İzleme anahtarını yapılandırın. Daha fazla bilgi için bkz. [izleme anahtarlarını yapılandırma](#configure).  
  
     Aşağıdaki kod, her türden biri olmak üzere iki anahtar oluşturur:  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =
       new System.Diagnostics.TraceSwitch("General",
       "Entire application");  
    ```  
  
<a name="configure"></a>

## <a name="configuring-trace-switches"></a>İzleme anahtarlarını yapılandırma  

 Uygulamanız dağıtıldıktan sonra, uygulamanızdaki izleme anahtarlarını yapılandırarak izleme çıkışını etkinleştirebilir veya devre dışı bırakabilirsiniz. Bir anahtarı yapılandırmak, başlatıldıktan sonra bir dış kaynaktan değerini değiştirmenin anlamına gelir. Yapılandırma dosyasını kullanarak Switch nesnelerinin değerlerini değiştirebilirsiniz. Bir izleme anahtarını açmak ve kapatmak için ya da düzeyini ayarlamak için, dinleyicilerinin yanı sıra aktardığı iletilerin miktarını ve türünü belirlemek için yapılandırın.  
  
 Anahtarlarınız. config dosyası kullanılarak yapılandırılır. Bir Web uygulaması için bu, projeyle ilişkili Web.config dosyasıdır. Bir Windows uygulamasında, bu dosyanın adı (uygulama adı) .exe.config. Dağıtılan bir uygulamada, bu dosya çalıştırılabilirle aynı klasörde bulunmalıdır.  
  
 Uygulamanız bir anahtarın bir örneğini ilk kez oluşturan kodu yürüttüğünde, bu, adlandırılmış anahtarla ilgili izleme düzeyi bilgileri için yapılandırma dosyasını denetler. İzleme sistemi, uygulama anahtarı ilk kez oluşturduğunda yapılandırma dosyasını belirli bir anahtar için yalnızca bir kez inceler.  
  
 Dağıtılmış bir uygulamada, uygulamanız çalışmadığı zaman geçiş nesnelerini yeniden yapılandırarak izleme kodunu etkinleştirirsiniz. Genellikle bu, anahtar nesnelerinin açık ve kapalı olduğunu ya da izleme düzeylerini değiştirerek ve sonra uygulamanızı yeniden başlatarak içerir.  
  
 Anahtarın bir örneğini oluşturduğunuzda, iki bağımsız değişken belirterek de başlatabilirsiniz: *DisplayName* bağımsız değişkeni ve bir *Açıklama* bağımsız değişkeni. Oluşturucunun *DisplayName* bağımsız değişkeni, <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Switch> sınıf örneğinin özelliğini ayarlar. *DisplayName* ,. config dosyasında anahtarı yapılandırmak için kullanılan addır ve *Açıklama* bağımsız değişkeni, anahtarın kısa bir açıklamasını ve hangi iletileri denetlediğini döndürmelidir.  
  
 Yapılandırılacak anahtarın adını belirtmenin yanı sıra, anahtar için de bir değer belirtmeniz gerekir. Bu değer bir tamsayıdır. İçin <xref:System.Diagnostics.BooleanSwitch> , 0 değeri **kapalı** ve sıfır dışında bir değer **Açık** öğesine karşılık gelir. İçin <xref:System.Diagnostics.TraceSwitch> , 0, 1, 2, 3 ve 4 sırasıyla **kapalı**, **hata**, **Uyarı**, **bilgi** ve **ayrıntılıdır**. 4 ' ten büyük herhangi bir sayı **verbose** olarak değerlendirilir ve sıfırdan küçük herhangi bir sayı **kapalı** olarak kabul edilir.  
  
> [!NOTE]
> .NET Framework sürüm 2,0 ' de, bir anahtarın değerini belirtmek için metin kullanabilirsiniz. Örneğin, `true` bir <xref:System.Diagnostics.BooleanSwitch> veya için gibi bir numaralandırma değerini temsil eden metin için `Error` <xref:System.Diagnostics.TraceSwitch> . Satır `<add name="myTraceSwitch" value="Error" />` ile eşdeğerdir `<add name="myTraceSwitch" value="1" />` .  
  
 Son kullanıcıların bir uygulamanın izleme anahtarlarını yapılandırabilmesi için uygulamanızdaki anahtarlara ayrıntılı belgeler sağlamanız gerekir. Hangi anahtarların ne olduğunu, hangilerinin açıp kapanmasını kontrol edin. Ayrıca son kullanıcıya açıklamalarda uygun yardım bulunan bir. config dosyası sağlamanız gerekir.  
  
#### <a name="to-configure-trace-switches"></a>İzleme anahtarlarını yapılandırmak için  
  
1. İzleme anahtarlarını kullanmak için, önce bunları oluşturmanız ve [bir izleme anahtarı oluşturma ve başlatma](#create)bölümünde açıklandığı gibi kodunuza yerleştirmeniz gerekir.  
  
2. Projeniz bir yapılandırma dosyası (app.config veya Web.config) içermiyorsa, **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.  
  
    - **Visual Basic:** **Yeni öğe Ekle** Iletişim kutusunda **uygulama yapılandırma dosyası**' nı seçin.  
  
         Uygulama yapılandırma dosyası oluşturulup açılır. Bu, kök öğesi olan bir XML belgesidir `<configuration>.`  
  
    - **Visual C#:** **Yeni öğe Ekle** Iletişim kutusunda **XML dosyası**' nı seçin. Bu dosyayı **app.config** olarak adlandırın. XML düzenleyicisinde, XML bildiriminden sonra aşağıdaki XML 'i ekleyin:  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         Projeniz derlendiğinde app.config dosyası proje çıktı klasörüne kopyalanır ve *applicationname*.exe.config yeniden adlandırılır.  
  
3. Etiketinden sonra, etiketinden sonra `<configuration>` `</configuration>` , anahtarlarınızı yapılandırmak IÇIN uygun XML 'i ekleyin. Aşağıdaki örneklerde **DisplayName** özelliği olan bir **BooleanSwitch** `DataMessageSwitch` ve **DisplayName** özelliği olan bir **TraceSwitch** gösterilmektedir `TraceLevelSwitch` .  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     Bu yapılandırmada her iki anahtar de kapalıdır.  
  
4. Önceki örnekte gösterildiği gibi bir **BooleanSwitch** açmanız gerekiyorsa `DataMessagesSwitch` **değeri** 0 dışında bir tamsayı olarak değiştirin.  
  
5. Önceki örnekte gösterildiği gibi bir **TraceSwitch** açmanız gerekiyorsa `TraceLevelSwitch` **değeri** uygun düzey ayarı (1 ile 4 arasında) olarak değiştirin.  
  
6. Son kullanıcının anahtarları uygun şekilde yapılandırmak için hangi değerlerin değiştirileceği hakkında net bir şekilde anlayabilmesi için. config dosyasına Yorumlar ekleyin.  
  
     Aşağıdaki örnek, açıklamalar dahil olmak üzere son kodun nasıl görünebileceğini göstermektedir:  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulamaları izleme ve İşaretleme](tracing-and-instrumenting-applications.md)
- [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](how-to-add-trace-statements-to-application-code.md)
- [İzleme Anahtarları](trace-switches.md)
- [İzleme ve hata ayıklama ayarları şeması](../configure-apps/file-schema/trace-debug/index.md)
