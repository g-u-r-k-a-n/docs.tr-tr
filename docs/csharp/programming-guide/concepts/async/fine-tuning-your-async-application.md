---
title: Async Uygulamanızda İnce Ayar (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: cff50e62ff62b70e97e7ea6e03714326d774e407
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970236"
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="da4d5-102">Async Uygulamanızda İnce Ayar (C#)</span><span class="sxs-lookup"><span data-stu-id="da4d5-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="da4d5-103">Async uygulamalarınız için, <xref:System.Threading.Tasks.Task> türün kullanıma sunduğu yöntemleri ve özellikleri kullanarak hassasiyet ve esneklik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da4d5-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="da4d5-104">Bu bölümdeki konular, kullanılan <xref:System.Threading.CancellationToken> örnekleri `Task` ve <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> önemli <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>yöntemleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="da4d5-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="da4d5-105">Kullanarak `WhenAny` ve, `WhenAll`daha kolay birden çok görevi başlatabilir ve tek bir görevi izleyerek bunların tamamlanmasını bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da4d5-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="da4d5-106">`WhenAny`Bir koleksiyondaki herhangi bir görev tamamlandığında tamamlayan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="da4d5-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="da4d5-107">Kullanan `WhenAny`örnekler için bkz: [Bir Tamamlandıktan Sonra Kalan Async Görevlerini İptal Et (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) ve [Birden Çok Async Görevi Başlatın ve Bunları Tamamlanında İşleyin (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="da4d5-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="da4d5-108">`WhenAll`Bir koleksiyondaki tüm görevler tamamlandığında tamamlayan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="da4d5-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="da4d5-109">Daha fazla bilgi ve `WhenAll`kullanan bir örnek için [Task.WhenAll (C#) kullanarak async walkthrough genişletmek için nasıl](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="da4d5-109">For more information and an example that uses `WhenAll`, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="da4d5-110">Bu bölümde aşağıdaki örnekler yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="da4d5-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="da4d5-111">[Bir Async Görevi veya Görev Listesi (C#) iptal edin.](./cancel-an-async-task-or-a-list-of-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="da4d5-111">[Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="da4d5-112">Bir Süre Sonra Async Görevlerini İptal Etme (C#)</span><span class="sxs-lookup"><span data-stu-id="da4d5-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="da4d5-113">Bir Tamamlandıktan Sonra Kalan Async Görevlerini İptal Et (C#)</span><span class="sxs-lookup"><span data-stu-id="da4d5-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="da4d5-114">Birden Çok Async Görevi Başlatın ve Tamamlanındıkları Gibi İşleyin (C#)</span><span class="sxs-lookup"><span data-stu-id="da4d5-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> <span data-ttu-id="da4d5-115">Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="da4d5-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="da4d5-116">Projeler, aşağıdaki resimde görüldüğü gibi işlemi başlatan bir düğme ve iptal eden bir düğme içeren bir ui oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da4d5-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="da4d5-117">Düğmeler adlandırılmış `startButton` `cancelButton`ve .</span><span class="sxs-lookup"><span data-stu-id="da4d5-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="da4d5-118">![İptal düğmesi ile WPF penceresi](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Başlat ve Durdur düğmesi olan iletişim kutusu")</span><span class="sxs-lookup"><span data-stu-id="da4d5-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="da4d5-119">Windows Presentation Foundation (WPF) projelerinin tamamını [Async Sample: Fine Tuning Your Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da4d5-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da4d5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da4d5-120">See also</span></span>

- [<span data-ttu-id="da4d5-121">Async ve await ile Asynchronous Programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="da4d5-121">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
