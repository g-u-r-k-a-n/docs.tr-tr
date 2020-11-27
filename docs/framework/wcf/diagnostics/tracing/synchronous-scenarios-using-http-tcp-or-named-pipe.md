---
title: HTTP, TCP veya Named-Pipe Kullanan Eşzamanlı Senaryolar
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 906bceadf56d82570b41cfbb2c96e4b89d595d02
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274445"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="1589f-102">HTTP, TCP veya Named-Pipe Kullanan Eşzamanlı Senaryolar</span><span class="sxs-lookup"><span data-stu-id="1589f-102">Synchronous Scenarios using HTTP, TCP or Named-Pipe</span></span>

<span data-ttu-id="1589f-103">Bu konuda, HTTP, TCP veya adlandırılmış kanal kullanarak, tek iş parçacıklı bir istemciyle farklı zaman uyumlu istek/yanıt senaryolarına yönelik etkinlikler ve aktarımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1589f-103">This topic describes the activities and transfers for different synchronous request/reply scenarios, with a single-threaded client, using HTTP, TCP or named pipe.</span></span> <span data-ttu-id="1589f-104">Çoklu iş parçacıklı istekler hakkında daha fazla bilgi için bkz. [http, TCP veya Named-Pipe kullanan zaman uyumsuz senaryolar](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) .</span><span class="sxs-lookup"><span data-stu-id="1589f-104">See [Asynchronous Scenarios using HTTP, TCP, or Named-Pipe](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) for more information on multi-threaded requests.</span></span>  
  
## <a name="synchronous-requestreply-without-errors"></a><span data-ttu-id="1589f-105">Hata olmadan zaman uyumlu Istek/yanıt</span><span class="sxs-lookup"><span data-stu-id="1589f-105">Synchronous Request/Reply without Errors</span></span>  

 <span data-ttu-id="1589f-106">Bu bölümde, tek iş parçacıklı istemciyle geçerli bir zaman uyumlu istek/yanıt senaryosuna yönelik etkinlikler ve aktarımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1589f-106">This section describes the activities and transfers for a valid synchronous request/reply scenario, with single-threaded client.</span></span>  
  
### <a name="client"></a><span data-ttu-id="1589f-107">İstemci</span><span class="sxs-lookup"><span data-stu-id="1589f-107">Client</span></span>  
  
#### <a name="establishing-communication-with-service-endpoint"></a><span data-ttu-id="1589f-108">Hizmet uç noktası ile Iletişim kurma</span><span class="sxs-lookup"><span data-stu-id="1589f-108">Establishing Communication with Service Endpoint</span></span>  

 <span data-ttu-id="1589f-109">İstemci oluşturulur ve açılır.</span><span class="sxs-lookup"><span data-stu-id="1589f-109">A client is constructed and opened.</span></span> <span data-ttu-id="1589f-110">Bu adımların her biri için, çevresel etkinlik (A) sırasıyla bir "yapı Istemcisi" (B) ve "açık Istemci" (C) etkinliğine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="1589f-110">For each of these steps, the ambient activity (A) is transferred to a "Construct Client" (B) and "Open Client" (C) activity respectively.</span></span> <span data-ttu-id="1589f-111">Aktarılmakta olan her etkinlik için, bir aktarım geri alınana kadar, diğer bir deyişle, ServiceModel kodu yürütülene kadar çevresel etkinlik askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="1589f-111">For each activity being transferred to, the ambient activity is suspended until there is a transfer back, that is, until ServiceModel code is executed.</span></span>  
  
#### <a name="making-a-request-to-service-endpoint"></a><span data-ttu-id="1589f-112">Hizmet uç noktasına Istek yapılıyor</span><span class="sxs-lookup"><span data-stu-id="1589f-112">Making a Request to Service Endpoint</span></span>  

 <span data-ttu-id="1589f-113">Çevresel etkinlik bir "ProcessAction" (D) etkinliğine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="1589f-113">The ambient activity is transferred to a "ProcessAction" (D) activity.</span></span> <span data-ttu-id="1589f-114">Bu etkinlik dahilinde bir istek iletisi gönderilir ve bir yanıt iletisi alınır.</span><span class="sxs-lookup"><span data-stu-id="1589f-114">Within this activity, a request message is sent, and a response message is received.</span></span> <span data-ttu-id="1589f-115">Denetim Kullanıcı koduna döndüğünde etkinlik sona erer.</span><span class="sxs-lookup"><span data-stu-id="1589f-115">The activity ends when control returns to user code.</span></span> <span data-ttu-id="1589f-116">Bu zaman uyumlu bir istek olduğundan, ortam etkinliği denetim tarafından dönüşene kadar askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="1589f-116">Because this is a synchronous request, the ambient activity suspends until control returns.</span></span>  
  
#### <a name="closing-communication-with-service-endpoint"></a><span data-ttu-id="1589f-117">Hizmet uç noktası ile Iletişim kapatılıyor</span><span class="sxs-lookup"><span data-stu-id="1589f-117">Closing Communication with Service Endpoint</span></span>  

 <span data-ttu-id="1589f-118">İstemci kapatma etkinliği (I) çevresel etkinlikten oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1589f-118">The client's close activity (I) is created from the ambient activity.</span></span> <span data-ttu-id="1589f-119">Bu, New ve Open ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1589f-119">This is identical to new and open.</span></span>  
  
### <a name="server"></a><span data-ttu-id="1589f-120">Sunucu</span><span class="sxs-lookup"><span data-stu-id="1589f-120">Server</span></span>  
  
#### <a name="setting-up-a-service-host"></a><span data-ttu-id="1589f-121">Hizmet ana bilgisayarı ayarlama</span><span class="sxs-lookup"><span data-stu-id="1589f-121">Setting up a Service Host</span></span>  

 <span data-ttu-id="1589f-122">ServiceHost 'un yeni ve açık Etkinlikleri (N ve O) çevresel etkinlikten (M) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1589f-122">The ServiceHost’s new and open activities (N and O) are created from the ambient activity (M).</span></span>  
  
 <span data-ttu-id="1589f-123">Her dinleyici için bir ServiceHost açılmadan bir dinleyici etkinliği (P) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1589f-123">A listener activity (P) is created from opening a ServiceHost for each listener.</span></span> <span data-ttu-id="1589f-124">Dinleyici etkinliği verileri almak ve işlemek için bekler.</span><span class="sxs-lookup"><span data-stu-id="1589f-124">The listener activity waits to receive and process data.</span></span>  
  
#### <a name="receiving-data-on-the-wire"></a><span data-ttu-id="1589f-125">Hattaki verileri alma</span><span class="sxs-lookup"><span data-stu-id="1589f-125">Receiving Data on the Wire</span></span>  

 <span data-ttu-id="1589f-126">Veriler kabloya ulaştığında, alınan verileri işlemek için zaten mevcut değilse (Q) bir "ReceiveBytes" etkinliği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1589f-126">When data arrives on the wire, a "ReceiveBytes" activity is created if it does not already exist (Q) to process the received data.</span></span> <span data-ttu-id="1589f-127">Bu etkinlik bir bağlantı veya kuyruk içindeki birden çok ileti için yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1589f-127">This activity can be reused for multiple messages within a connection or queue.</span></span>  
  
 <span data-ttu-id="1589f-128">Bir SOAP eylem iletisi oluşturmak için yeterli veri varsa, ReceiveBytes etkinliği bir ProcessMessage etkinliği (R) başlatır.</span><span class="sxs-lookup"><span data-stu-id="1589f-128">The ReceiveBytes activity launches a ProcessMessage activity (R) if it has enough data to form a SOAP action message.</span></span>  
  
 <span data-ttu-id="1589f-129">Etkinlik R ' de ileti üstbilgileri işlenir ve ActivityId üst bilgisi doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="1589f-129">In activity R, the message headers are processed, and the activityID header is verified.</span></span> <span data-ttu-id="1589f-130">Bu üst bilgi varsa, etkinlik KIMLIĞI ProcessAction etkinliğine ayarlanır; Aksi takdirde, yeni bir KIMLIK oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1589f-130">If this header is present, the activity ID is set to the ProcessAction activity; otherwise, a new ID is created.</span></span>  
  
 <span data-ttu-id="1589f-131">Çağrı işlendiğinde ProcessAction etkinlikleri oluşturulur ve ' a aktarılır.</span><span class="sxs-lookup"><span data-stu-id="1589f-131">ProcessAction activity (S) is created and being transferred to, when the call is processed.</span></span> <span data-ttu-id="1589f-132">Bu etkinlik, Kullanıcı kodu (T) yürütülüyor ve uygunsa yanıt iletisini gönderme dahil olmak üzere, gelen iletiyle ilgili tüm işlemler tamamlandığında sona erer.</span><span class="sxs-lookup"><span data-stu-id="1589f-132">This activity ends when all processing related to the incoming message is completed, including executing user code (T) and sending the response message if applicable.</span></span>  
  
#### <a name="closing-a-service-host"></a><span data-ttu-id="1589f-133">Hizmet konağını kapatma</span><span class="sxs-lookup"><span data-stu-id="1589f-133">Closing a Service Host</span></span>  

 <span data-ttu-id="1589f-134">ServiceHost 'un Close etkinliği (Z) çevresel etkinlikten oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1589f-134">The ServiceHost’s close activity (Z) is created from the ambient activity.</span></span>  
  
 ![Zaman uyumlu senaryoları gösteren diyagram: HTTP, TCP veya adlandırılmış kanallar.](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 <span data-ttu-id="1589f-136">İçinde \<A: name> , `A` önceki metinde ve tablo 3 ' te etkinliği açıklayan bir kısayol simgedir.</span><span class="sxs-lookup"><span data-stu-id="1589f-136">In \<A: name>, `A` is a shortcut symbol that describes the activity in the previous text and in table 3.</span></span> <span data-ttu-id="1589f-137">`Name` etkinliğin kısaltılmış bir adıdır.</span><span class="sxs-lookup"><span data-stu-id="1589f-137">`Name` is a shortened name of the activity.</span></span>  
  
 <span data-ttu-id="1589f-138">Eğer `propagateActivity` = `true` , hem istemci hem de hizmette işlem eylemi aynı etkinlik kimliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1589f-138">If `propagateActivity`=`true`, Process Action on both the client and service have the same activity ID.</span></span>  
  
## <a name="synchronous-requestreply-with-errors"></a><span data-ttu-id="1589f-139">Zaman uyumlu Istek/hatalarla yanıtla</span><span class="sxs-lookup"><span data-stu-id="1589f-139">Synchronous Request/Reply with Errors</span></span>  

 <span data-ttu-id="1589f-140">Önceki senaryoya ilişkin tek fark, bir SOAP hata iletisinin yanıt iletisi olarak döndürüldüğünden olur.</span><span class="sxs-lookup"><span data-stu-id="1589f-140">The only difference with the previous scenario is that a SOAP fault message is returned as a response message.</span></span> <span data-ttu-id="1589f-141">İse `propagateActivity` = `true` , istek iletisinin etkinlik kimliği SOAP hata iletisine eklenir.</span><span class="sxs-lookup"><span data-stu-id="1589f-141">If `propagateActivity`=`true`, the activity ID of the request message is added to the SOAP fault message.</span></span>  
  
## <a name="synchronous-one-way-without-errors"></a><span data-ttu-id="1589f-142">Hata olmadan zaman uyumlu One-Way</span><span class="sxs-lookup"><span data-stu-id="1589f-142">Synchronous One-Way without Errors</span></span>  

 <span data-ttu-id="1589f-143">İlk senaryoya göre tek fark, sunucuya hiçbir ileti döndürülmüyor.</span><span class="sxs-lookup"><span data-stu-id="1589f-143">The only difference with the first scenario is that no message is returned to the server.</span></span> <span data-ttu-id="1589f-144">HTTP tabanlı protokoller için istemciye bir durum (geçerli veya hata) döndürülmeye devam edilir.</span><span class="sxs-lookup"><span data-stu-id="1589f-144">For HTTP-based protocols, a status (valid or error) is still returned to the client.</span></span> <span data-ttu-id="1589f-145">Bunun nedeni, HTTP 'nin WCF protokol yığınının parçası olan bir istek-yanıt semantiğinin bulunduğu tek protokoldür.</span><span class="sxs-lookup"><span data-stu-id="1589f-145">This is because HTTP is the only protocol with a request-response semantics that is part of the WCF protocol stack.</span></span> <span data-ttu-id="1589f-146">TCP işlemi WCF 'den gizlendiğinden, istemciye hiçbir onay gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="1589f-146">Because TCP processing is hidden from WCF, no acknowledgement is sent to the client.</span></span>  
  
## <a name="synchronous-one-way-with-errors"></a><span data-ttu-id="1589f-147">Hatalarla zaman uyumlu One-Way</span><span class="sxs-lookup"><span data-stu-id="1589f-147">Synchronous One-Way with Errors</span></span>  

 <span data-ttu-id="1589f-148">İleti işlenirken bir hata oluşursa (Q veya daha fazla), istemciye hiçbir bildirim döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="1589f-148">If an error occurs while processing the message (Q or beyond), no notification is returned to the client.</span></span> <span data-ttu-id="1589f-149">Bu, "hata olmadan zaman uyumlu One-Way" senaryosu ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1589f-149">This is identical to the "Synchronous One-Way without Errors" scenario.</span></span> <span data-ttu-id="1589f-150">Bir hata iletisi almak istiyorsanız One-Way senaryosu kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="1589f-150">You should not use a One-Way scenario if you want to receive an error message.</span></span>  
  
## <a name="duplex"></a><span data-ttu-id="1589f-151">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="1589f-151">Duplex</span></span>  

 <span data-ttu-id="1589f-152">Önceki senaryolarla aradaki fark, istemcinin zaman uyumsuz senaryolara benzer şekilde ReceiveBytes ve ProcessMessage etkinlikleri oluşturduğu bir hizmet olarak davranmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1589f-152">The difference with the previous scenarios is that the client acts as a service, in which it creates the ReceiveBytes and ProcessMessage activities, similar to the Asynchronous scenarios.</span></span>
