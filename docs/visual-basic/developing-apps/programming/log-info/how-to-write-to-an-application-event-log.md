---
title: 'Nasıl yapılır: Uygulama Olay Günlüğüne Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 298d6d85f8b21176b72db8e676617577eb03fada
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410042"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="7e013-102">Nasıl Yapılır: Uygulama Olay Günlüğüne Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e013-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="7e013-103">`My.Application.Log` `My.Log` Uygulamanızda gerçekleşen olaylar hakkında bilgi yazmak için ve nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e013-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="7e013-104">Bu örnek, bir olay günlüğü dinleyicisinin `My.Application.Log` izleme bilgilerini uygulama olay günlüğü 'ne yazmalarını sağlayacak şekilde nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e013-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="7e013-105">Güvenlik günlüğüne yazılamıyor.</span><span class="sxs-lookup"><span data-stu-id="7e013-105">You cannot write to the Security log.</span></span> <span data-ttu-id="7e013-106">Sistem günlüğüne yazmak için LocalSystem veya Administrator hesabının bir üyesi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e013-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="7e013-107">Bir olay günlüğünü görüntülemek için **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi**kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e013-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="7e013-108">Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7e013-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

## <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="7e013-109">Olay günlüğü dinleyicisini eklemek ve yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="7e013-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="7e013-110">**Çözüm Gezgini** içinde App. config öğesine sağ tıklayın ve **Aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7e013-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="7e013-111">\-veya</span><span class="sxs-lookup"><span data-stu-id="7e013-111">\- or -</span></span>

    <span data-ttu-id="7e013-112">App. config dosyası yoksa,</span><span class="sxs-lookup"><span data-stu-id="7e013-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="7e013-113">**Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7e013-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="7e013-114">**Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="7e013-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="7e013-115">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7e013-115">Click **Add**.</span></span>

2. <span data-ttu-id="7e013-116">`<listeners>`Uygulama yapılandırma dosyasında bölümünü bulun.</span><span class="sxs-lookup"><span data-stu-id="7e013-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="7e013-117">Bölümünün, `<listeners>` `<source>` `<system.diagnostics>` üst düzey bölüm altında iç içe yerleştirilmiş olan bölümünde iç içe yerleştirilmiş olan "DefaultSource" adlı ad özniteliğiyle birlikte bölümünü bulabilirsiniz `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="7e013-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="7e013-118">Bu öğeyi bu bölüme ekleyin `<listeners>` :</span><span class="sxs-lookup"><span data-stu-id="7e013-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="7e013-119">Bölümünde, `<sharedListeners>` üst düzey bölümünde bölümünde bulunan bölümünü bulun `<system.diagnostics>` `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="7e013-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="7e013-120">Bu öğeyi bu bölüme ekleyin `<sharedListeners>` :</span><span class="sxs-lookup"><span data-stu-id="7e013-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="7e013-121">`APPLICATION_NAME`Uygulamanızın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7e013-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7e013-122">Genellikle, bir uygulama olay günlüğüne yalnızca hataları yazar.</span><span class="sxs-lookup"><span data-stu-id="7e013-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="7e013-123">Günlük çıkışını filtreleme hakkında daha fazla bilgi için bkz. [Izlenecek yol: filtreleme My. Application. log output](walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="7e013-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).</span></span>

## <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="7e013-124">Olay günlüğüne olay bilgilerini yazmak için</span><span class="sxs-lookup"><span data-stu-id="7e013-124">To write event information to the event log</span></span>

<span data-ttu-id="7e013-125">`My.Application.Log.WriteEntry` `My.Application.Log.WriteException` Olay günlüğüne bilgi yazmak için veya yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7e013-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="7e013-126">Daha fazla bilgi için bkz. [nasıl yapılır: yazma günlüğü iletileri](how-to-write-log-messages.md) ve [nasıl yapılır: günlüğe kaydetme özel durumları](how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="7e013-126">For more information, see [How to: Write Log Messages](how-to-write-log-messages.md) and [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

<span data-ttu-id="7e013-127">Bir derleme için olay günlüğü dinleyicisini yapılandırdıktan sonra, `My.Application.Log` Bu derlemeden yazan tüm iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="7e013-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e013-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e013-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="7e013-129">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="7e013-129">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="7e013-130">Nasıl yapılır: Özel Durumları Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="7e013-130">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="7e013-131">İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="7e013-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
