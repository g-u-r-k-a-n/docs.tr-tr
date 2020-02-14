---
title: dangerousThreadingAPI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
ms.openlocfilehash: 4e7e858dfb85eeccbadb23da60d081d1407e89d8
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216679"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="afe8f-102">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="afe8f-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="afe8f-103">`dangerousThreadingAPI` yönetilen hata ayıklama Yardımcısı (MDA), <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> yöntemi geçerli iş parçacığı dışında bir iş parçacığında çağrıldığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="afe8f-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="afe8f-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="afe8f-104">Symptoms</span></span>  
 <span data-ttu-id="afe8f-105">Bir uygulama süresiz olarak yanıt vermemeye başlıyor veya askıda kalıyor.</span><span class="sxs-lookup"><span data-stu-id="afe8f-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="afe8f-106">Sistem veya uygulama verileri, geçici olarak veya bir uygulama kapatıldıktan sonra bile öngörülemeyen bir durumda kalabilir.</span><span class="sxs-lookup"><span data-stu-id="afe8f-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="afe8f-107">Bazı işlemler beklendiği gibi tamamlanmıyor.</span><span class="sxs-lookup"><span data-stu-id="afe8f-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="afe8f-108">Belirtiler, soruna bağlı rasgelelik nedeniyle büyük ölçüde farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="afe8f-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="afe8f-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="afe8f-109">Cause</span></span>  
 <span data-ttu-id="afe8f-110">Bir iş parçacığı <xref:System.Threading.Thread.Suspend%2A> yöntemi kullanılarak başka bir iş parçacığı tarafından zaman uyumsuz olarak askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="afe8f-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="afe8f-111">Bir işlemin ortasında olabilecek başka bir iş parçacığını askıya almanın ne zaman güvenli olduğunu belirlemenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="afe8f-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="afe8f-112">İş parçacığını askıya almak, verilerin bozulmasına veya ınvarıant 'ların bozulmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="afe8f-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="afe8f-113">Bir iş parçacığının askıya alınma durumuna yerleştirilmesi ve <xref:System.Threading.Thread.Resume%2A> yöntemi kullanılarak hiçbir şekilde sürdürülmemesi, uygulamanın süresiz olarak askıda kalması ve muhtemelen uygulama verilerine zarar verebiliyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="afe8f-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="afe8f-114">Bu yöntemler artık kullanılmıyor olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="afe8f-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="afe8f-115">Eşitleme temelleri hedef iş parçacığı tarafından tutuluyorsa, askıya alma sırasında tutuluyor olarak kalırlar.</span><span class="sxs-lookup"><span data-stu-id="afe8f-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="afe8f-116">Bu, kilitlenmeleri başka bir iş parçacığı olmalıdır, örneğin <xref:System.Threading.Thread.Suspend%2A>yapan iş parçacığı temel üzerinde bir kilit elde etmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="afe8f-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="afe8f-117">Bu durumda, sorun kendi kendine bir kilitlenme olarak bildirim gösterir.</span><span class="sxs-lookup"><span data-stu-id="afe8f-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="afe8f-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="afe8f-118">Resolution</span></span>  
 <span data-ttu-id="afe8f-119"><xref:System.Threading.Thread.Suspend%2A> ve <xref:System.Threading.Thread.Resume%2A>kullanımını gerektiren tasarımlardan kaçının.</span><span class="sxs-lookup"><span data-stu-id="afe8f-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="afe8f-120">İş parçacıkları arasındaki ortak işlem için <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>veya C# `lock` ifadesiyle ilgili eşitleme temel öğelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="afe8f-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="afe8f-121">Bu yöntemleri kullanmanız gerekiyorsa, zaman penceresini küçültün ve iş parçacığı askıya alınma durumundayken yürütülen kod miktarını en aza indirin.</span><span class="sxs-lookup"><span data-stu-id="afe8f-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="afe8f-122">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="afe8f-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="afe8f-123">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="afe8f-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="afe8f-124">Yalnızca tehlikeli iş parçacığı oluşturma işlemleriyle ilgili verileri raporlar.</span><span class="sxs-lookup"><span data-stu-id="afe8f-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="afe8f-125">Çıktı</span><span class="sxs-lookup"><span data-stu-id="afe8f-125">Output</span></span>  
 <span data-ttu-id="afe8f-126">MDA, etkinleştirilmesinin nedeni olan tehlikeli iş parçacığı yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="afe8f-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="afe8f-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="afe8f-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="afe8f-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="afe8f-128">Example</span></span>  
 <span data-ttu-id="afe8f-129">Aşağıdaki kod örneği, `dangerousThreadingAPI`etkinleştirmesine neden olan <xref:System.Threading.Thread.Suspend%2A> yöntemine yapılan çağrıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="afe8f-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();   
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="afe8f-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afe8f-130">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="afe8f-131">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="afe8f-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="afe8f-132">lock Deyimi</span><span class="sxs-lookup"><span data-stu-id="afe8f-132">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
