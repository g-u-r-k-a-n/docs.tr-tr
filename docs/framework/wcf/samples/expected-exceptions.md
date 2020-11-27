---
title: Beklenen Özel Durumlar
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 367397f738a2a0219a7bdaf3073b37890506929d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262056"
---
# <a name="expected-exceptions"></a><span data-ttu-id="a264b-102">Beklenen Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="a264b-102">Expected Exceptions</span></span>

<span data-ttu-id="a264b-103">Bu örnek, yazılan bir istemci kullanılırken beklenen özel durumların nasıl yakalanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a264b-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="a264b-104">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="a264b-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="a264b-105">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="a264b-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a264b-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="a264b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a264b-107">Bu örnek, doğru programların işlemesi gereken iki beklenen özel durum türünü yakalama ve işlemeyi gösterir: `TimeoutException` ve `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="a264b-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="a264b-108">Windows Communication Foundation (WCF) istemcisinde iletişim yöntemlerinden oluşturulan özel durumlar bekleniyor veya beklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="a264b-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="a264b-109">Beklenmeyen özel durumlar `OutOfMemoryException` , veya gibi programlama hataları gibi çok zararlı hatalar içerir `ArgumentNullException` `InvalidOperationException` .</span><span class="sxs-lookup"><span data-stu-id="a264b-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="a264b-110">Genellikle beklenmeyen hataları işlemenin yararlı bir yolu yoktur, bu nedenle genellikle WCF istemci iletişim yöntemini çağırırken bunları yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="a264b-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="a264b-111">Bir WCF istemcisinde iletişim yöntemlerinden beklenen özel durumlar `TimeoutException` , `CommunicationException` ve tüm türetilmiş sınıflarını içerir `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="a264b-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="a264b-112">Bu, WCF istemcisini iptal ederek ve bir iletişim hatası bildirerek güvenli bir şekilde işlenebilen iletişim sırasında bir sorun olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a264b-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="a264b-113">Dış faktörler herhangi bir uygulamada bu hatalara neden olabileceğinden, doğru uygulamalar bu özel durumları yakalamalı ve oluştuğunda kurtarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a264b-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="a264b-114">`CommunicationException`Bir istemcinin oluşturbileceği birkaç türetilmiş sınıf vardır.</span><span class="sxs-lookup"><span data-stu-id="a264b-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="a264b-115">Bazı durumlarda, uygulamalar özel işlem yapmak için bunlardan bazılarını da yakalar, ancak diğerlerinin bir olarak işlenmesine izin verir `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="a264b-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="a264b-116">Bu, önce daha özel bir özel durum türü yakalayıp daha sonra `CommunicationException` bir catch yan tümcesinde yakalanarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a264b-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="a264b-117">İstemci iletişim yöntemini çağıran kodun ve ' i yakalamalı olması gerekir `TimeoutException` `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="a264b-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="a264b-118">Bu tür hataları işlemenin bir yolu, istemciyi durdurmak ve iletişim başarısızlığını raporlamak olur.</span><span class="sxs-lookup"><span data-stu-id="a264b-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```csharp
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="a264b-119">Beklenen bir özel durum oluşursa, istemci daha sonra kullanılabilir olmayabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a264b-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="a264b-120">İstemcinin hala kullanılabilir olup olmadığını anlamak için, özelliğinin olduğunu kontrol edin `State` `CommunicationState` . Makta.</span><span class="sxs-lookup"><span data-stu-id="a264b-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="a264b-121">Hala açılırsa, hala kullanılabilir olur.</span><span class="sxs-lookup"><span data-stu-id="a264b-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="a264b-122">Aksi takdirde, istemciyi iptal etmeniz ve tüm başvurularını serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a264b-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="a264b-123">Bir oturumun bulunduğu istemciler genellikle özel bir durum sonrasında artık kullanılamaz ve bir oturumu olmayan istemciler genellikle bir özel durumla sonra hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a264b-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="a264b-124">Ancak, bunlardan hiçbiri garanti edilmez, bu nedenle istemciyi kullanmaya devam etmeyi denemek istiyorsanız, uygulamanızın `State` hala açık olduğunu doğrulamak için özelliği denetlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a264b-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="a264b-125">Örneği çalıştırdığınızda, işlem yanıtları ve özel durumlar istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a264b-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="a264b-126">İstemci süreci iki senaryo çalıştırır, her biri ' ın her birini çağırma girişiminde bulunur `Add` `Divide` .</span><span class="sxs-lookup"><span data-stu-id="a264b-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="a264b-127">İlk senaryo, çağrısını yapmadan önce istemciyi iptal ederek bir ağ sorununun benzetimini yapar `Divide` .</span><span class="sxs-lookup"><span data-stu-id="a264b-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="a264b-128">İkinci senaryo, yöntemin tamamlanabilmesi için çok kısa süre sonu ayarlayarak zaman aşımı koşuluna neden olur.</span><span class="sxs-lookup"><span data-stu-id="a264b-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="a264b-129">İstemci işlemindeki beklenen çıkış:</span><span class="sxs-lookup"><span data-stu-id="a264b-129">The expected output from the client process is:</span></span>  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a264b-130">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a264b-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a264b-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a264b-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a264b-132">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a264b-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a264b-133">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a264b-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a264b-134">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a264b-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a264b-135">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a264b-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a264b-136">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a264b-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a264b-137">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a264b-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
