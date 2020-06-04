---
title: Zaman Uyumsuz Uygulamanızda Hassas Ayar Yapma
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: e33f86177a3680d41ec04842dbc120713a48f61c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396655"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="cb55e-102">Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb55e-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="cb55e-103">Türün kullanılabilir hale getiren yöntemleri ve özellikleri kullanarak, zaman uyumsuz uygulamalarınıza duyarlık ve esneklik ekleyebilirsiniz <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="cb55e-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="cb55e-104">Bu bölümdeki konularda, <xref:System.Threading.CancellationToken> ve gibi önemli Yöntemler ve kullanılan örnekler gösterilmektedir `Task` <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cb55e-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="cb55e-105">Ve kullanarak `WhenAny` `WhenAll` , birden çok görevi daha kolay başlatabilir ve tek bir görevi izleyerek tamamlanmasını deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb55e-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="cb55e-106">`WhenAny`bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb55e-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="cb55e-107">Kullanan örnekler için `WhenAny` , bkz. [kalan zaman uyumsuz görevleri bir işlem tamamlandıktan sonra iptal etme (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)ve [birden çok zaman uyumsuz görev başlatın ve bunları tamamladıktan sonra işleyin (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="cb55e-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="cb55e-108">`WhenAll`bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb55e-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="cb55e-109">Daha fazla bilgi ve kullanan bir örnek için `WhenAll` bkz. [nasıl yapılır: görev. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="cb55e-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="cb55e-110">Bu bölüm aşağıdaki örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cb55e-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="cb55e-111">[Zaman uyumsuz bir görevi veya görev listesini Iptal edin (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="cb55e-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="cb55e-112">Zaman uyumsuz görevleri bir süre sonra iptal et (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb55e-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="cb55e-113">Kalan zaman uyumsuz görevleri bir süre tamamlandıktan sonra iptal et (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb55e-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="cb55e-114">Birden çok zaman uyumsuz görev başlatın ve bunları tamamlarsa Işleyin (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb55e-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> <span data-ttu-id="cb55e-115">Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb55e-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="cb55e-116">Projeler, aşağıdaki görüntüde gösterildiği gibi, işlemi başlatan bir düğme ve bunu iptal eden bir düğme içeren bir kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb55e-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="cb55e-117">Düğmeler ve olarak adlandırılır `startButton` `cancelButton` .</span><span class="sxs-lookup"><span data-stu-id="cb55e-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="cb55e-118">![Iptal düğmesi olan WPF penceresi](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Başlat ve Durdur düğmesi ile iletişim kutusu")</span><span class="sxs-lookup"><span data-stu-id="cb55e-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="cb55e-119">Tüm Windows Presentation Foundation (WPF) projelerini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="cb55e-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb55e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb55e-120">See also</span></span>

- [<span data-ttu-id="cb55e-121">Async ve await ile zaman uyumsuz programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb55e-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
