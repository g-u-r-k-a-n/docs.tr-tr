---
description: 'Daha fazla bilgi edinin: Izlenecek yol: My. Application. log bilgi yazma bilgileri (Visual Basic)'
title: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: aa4e1b8ce33e2afd8dd51c68340feb3e85eb8966
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731428"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="cca88-103">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cca88-103">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="cca88-104">`My.Application.Log` `My.Log` Uygulamanızda gerçekleşen olaylar hakkındaki bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cca88-104">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="cca88-105">Bu izlenecek yol, varsayılan ayarların nasıl geçersiz kılınacağını ve `Log` nesnenin diğer günlük dinleyicilerine yazmasına neden olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cca88-105">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cca88-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="cca88-106">Prerequisites</span></span>

<span data-ttu-id="cca88-107">`Log`Nesnesi, çeşitli günlük dinleyicilerine bilgi yazabilir.</span><span class="sxs-lookup"><span data-stu-id="cca88-107">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="cca88-108">Yapılandırmaları değiştirmeden önce günlük dinleyicilerinin geçerli yapılandırmasını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cca88-108">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="cca88-109">Daha fazla bilgi için bkz. [Izlenecek yol: My. Application. log bilgisinin nereden yazabileceğini belirleme](walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="cca88-109">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

<span data-ttu-id="cca88-110">[Nasıl yapılır: bir metin dosyasına olay bilgilerini yazma](how-to-write-event-information-to-a-text-file.md) veya [nasıl yapılır: uygulama olay günlüğüne yazma](how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="cca88-110">You may want to review [How to: Write Event Information to a Text File](how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](how-to-write-to-an-application-event-log.md).</span></span>

### <a name="to-add-listeners"></a><span data-ttu-id="cca88-111">Dinleyicileri eklemek için</span><span class="sxs-lookup"><span data-stu-id="cca88-111">To add listeners</span></span>

1. <span data-ttu-id="cca88-112">**Çözüm Gezgini** app.config sağ tıklayın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="cca88-112">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="cca88-113">\- veya</span><span class="sxs-lookup"><span data-stu-id="cca88-113">\- or -</span></span>

     <span data-ttu-id="cca88-114">app.config dosya yoksa:</span><span class="sxs-lookup"><span data-stu-id="cca88-114">If there is no app.config file:</span></span>

    1. <span data-ttu-id="cca88-115">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cca88-115">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="cca88-116">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="cca88-116">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>

    3. <span data-ttu-id="cca88-117">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cca88-117">Click **Add**.</span></span>

2. <span data-ttu-id="cca88-118">Bölümünde `<listeners>` `<source>` `name` "DefaultSource" özniteliğine sahip bölümün altındaki bölümü bulun `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="cca88-118">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="cca88-119">`<sources>`Bölümü, `<system.diagnostics>` üst düzey bölümündeki bölümünde bulunur `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="cca88-119">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="cca88-120">Bu öğeleri bu bölüme ekleyin `<listeners>` .</span><span class="sxs-lookup"><span data-stu-id="cca88-120">Add these elements to that `<listeners>` section.</span></span>

    ```xml
    <!-- Uncomment to connect the application file log. -->
    <!-- <add name="FileLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="EventLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="Delimited" /> -->
    <!-- Uncomment to connect the XML log. -->
    <!-- <add name="XmlWriter" /> -->
    <!-- Uncomment to connect the console log. -->
    <!-- <add name="Console" /> -->
    ```

4. <span data-ttu-id="cca88-121">İleti almak istediğiniz günlük dinleyicilerinin açıklamasını kaldırın `Log` .</span><span class="sxs-lookup"><span data-stu-id="cca88-121">Uncomment the log listeners that you want to receive `Log` messages.</span></span>

5. <span data-ttu-id="cca88-122">Bölümünde, `<sharedListeners>` üst düzey bölümünde bölümünde bulunan bölümünü bulun `<system.diagnostics>` `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="cca88-122">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="cca88-123">Bu öğeleri bu bölüme ekleyin `<sharedListeners>` .</span><span class="sxs-lookup"><span data-stu-id="cca88-123">Add these elements to that `<sharedListeners>` section.</span></span>

    ```xml
    <add name="FileLog"
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
               Microsoft.VisualBasic, Version=8.0.0.0,
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
         initializeData="FileLogWriter" />
    <add name="EventLog"
         type="System.Diagnostics.EventLogTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="sample application"/>
    <add name="Delimited"
         type="System.Diagnostics.DelimitedListTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleDelimitedFile.txt"
         traceOutputOptions="DateTime" />
    <add name="XmlWriter"
         type="System.Diagnostics.XmlWriterTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleLogFile.xml" />
    <add name="Console"
         type="System.Diagnostics.ConsoleTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="true" />
    ```

7. <span data-ttu-id="cca88-124">app.config dosyasının içeriği aşağıdaki XML 'e benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="cca88-124">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Uncomment to connect the application file log. -->
              <!-- <add name="FileLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="EventLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="Delimited" /> -->
              <!-- Uncomment to connect the XML log. -->
              <!-- <add name="XmlWriter" /> -->
              <!-- Uncomment to connect the console log. -->
              <!-- <add name="Console" /> -->
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="Information" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
               initializeData="FileLogWriter" />
          <add name="EventLog"
               type="System.Diagnostics.EventLogTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="sample application"/>
          <add name="Delimited"
               type="System.Diagnostics.DelimitedListTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleDelimitedFile.txt"
               traceOutputOptions="DateTime" />
          <add name="XmlWriter"
               type="System.Diagnostics.XmlWriterTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleLogFile.xml" />
          <add name="Console"
               type="System.Diagnostics.ConsoleTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="true" />
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="cca88-125">Bir dinleyiciyi yeniden yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="cca88-125">To reconfigure a listener</span></span>

1. <span data-ttu-id="cca88-126">Bölümünden dinleyicinin öğesini bulun `<add>` `<sharedListeners>` .</span><span class="sxs-lookup"><span data-stu-id="cca88-126">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>

2. <span data-ttu-id="cca88-127">`type`Öznitelik, dinleyici türünün adını verir.</span><span class="sxs-lookup"><span data-stu-id="cca88-127">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="cca88-128">Bu tür sınıfından devralması gerekir <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="cca88-128">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="cca88-129">Doğru türün kullanıldığından emin olmak için kesin adlandırılmış tür adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="cca88-129">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="cca88-130">Daha fazla bilgi için, aşağıdaki "kesin adlandırılmış türe başvurmak Için" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cca88-130">For more information, see the "To reference a strongly named type" section below.</span></span>

     <span data-ttu-id="cca88-131">Kullanabileceğiniz bazı türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cca88-131">Some types that you can use are:</span></span>

    - <span data-ttu-id="cca88-132"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>Bir dosya günlüğüne yazan bir dinleyici.</span><span class="sxs-lookup"><span data-stu-id="cca88-132">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>

    - <span data-ttu-id="cca88-133"><xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>Parametresi tarafından belirtilen bilgisayar olay günlüğüne bilgi yazan bir dinleyici `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="cca88-133">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>

    - <span data-ttu-id="cca88-134"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> Parametresinde belirtilen dosyaya yazılan ve dinleyicileri `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="cca88-134">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="cca88-135"><xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>Komut satırı konsoluna yazan bir dinleyici.</span><span class="sxs-lookup"><span data-stu-id="cca88-135">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>

     <span data-ttu-id="cca88-136">Diğer günlük dinleyicisi türlerinin yazma bilgileri hakkında daha fazla bilgi için, bu türün belgelerine başvurun.</span><span class="sxs-lookup"><span data-stu-id="cca88-136">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

3. <span data-ttu-id="cca88-137">Uygulama, log-Listener nesnesini oluşturduğunda, `initializeData` özniteliği Oluşturucu parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="cca88-137">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="cca88-138">Özniteliğin anlamı, `initializeData` izleme dinleyicisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cca88-138">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>

4. <span data-ttu-id="cca88-139">Günlük dinleyicisini oluşturduktan sonra uygulama, dinleyicinin özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cca88-139">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="cca88-140">Bu özellikler, öğesindeki diğer öznitelikler tarafından tanımlanır `<add>` .</span><span class="sxs-lookup"><span data-stu-id="cca88-140">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="cca88-141">Belirli bir dinleyicinin özellikleri hakkında daha fazla bilgi için, bu dinleyicinin türüne yönelik belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="cca88-141">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>

### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="cca88-142">Kesin adlandırılmış türe başvurmak için</span><span class="sxs-lookup"><span data-stu-id="cca88-142">To reference a strongly named type</span></span>

1. <span data-ttu-id="cca88-143">Doğru türün günlük dinleyiciniz için kullanıldığından emin olmak için tam tür adı ve kesin adlandırılmış derleme adını kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cca88-143">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="cca88-144">Kesin adlandırılmış türün sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="cca88-144">The syntax of a strongly named type is as follows:</span></span>

     <span data-ttu-id="cca88-145">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span><span class="sxs-lookup"><span data-stu-id="cca88-145">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>

2. <span data-ttu-id="cca88-146">Bu kod örneği, bu durumda "System. Diagnostics. FileLogTraceListener" tam türü için kesin adlandırılmış tür adının nasıl belirleneceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="cca88-146">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     <span data-ttu-id="cca88-147">Bu çıktı, yukarıdaki "dinleyicileri ekleme" yordamında olduğu gibi kesin adlandırılmış bir türe benzersiz olarak başvurmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cca88-147">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a><span data-ttu-id="cca88-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cca88-148">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [<span data-ttu-id="cca88-149">Nasıl yapılır: Olay Bilgilerini Metin Dosyasına Yazma</span><span class="sxs-lookup"><span data-stu-id="cca88-149">How to: Write Event Information to a Text File</span></span>](how-to-write-event-information-to-a-text-file.md)
- [<span data-ttu-id="cca88-150">Nasıl yapılır: Uygulama Olay Günlüğüne Yazma</span><span class="sxs-lookup"><span data-stu-id="cca88-150">How to: Write to an Application Event Log</span></span>](how-to-write-to-an-application-event-log.md)
