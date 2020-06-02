---
title: 'Nasıl Yapılır: İptal İstekleri için Geri Çağırmaları Kaydetme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: 0482d43925f4f547114119a95909501cbf09eedb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279368"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="5dbed-102">Nasıl Yapılır: İptal İstekleri için Geri Çağırmaları Kaydetme</span><span class="sxs-lookup"><span data-stu-id="5dbed-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="5dbed-103">Aşağıdaki örnek, <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> <xref:System.Threading.CancellationTokenSource.Cancel%2A> belirteci oluşturan nesne üzerinde yapılan bir çağrı nedeniyle bir özellik doğru olduğunda çağrılacak bir temsilcinin nasıl kaydedileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5dbed-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="5dbed-104">Birleşik iptal çerçevesini yerel olarak desteklemeyen zaman uyumsuz işlemleri iptal etmek ve zaman uyumsuz bir işlemin tamamlanmasını bekleyen yöntemlerin engellenmesini kaldırma için bu tekniği kullanın.</span><span class="sxs-lookup"><span data-stu-id="5dbed-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5dbed-105">"Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5dbed-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="5dbed-106">Bu hata zararsız.</span><span class="sxs-lookup"><span data-stu-id="5dbed-106">This error is benign.</span></span> <span data-ttu-id="5dbed-107">F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5dbed-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="5dbed-108">Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="5dbed-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dbed-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5dbed-109">Example</span></span>  
 <span data-ttu-id="5dbed-110">Aşağıdaki örnekte, <xref:System.Net.WebClient.CancelAsync%2A> yöntemi iptal belirteci aracılığıyla iptal istendiğinde çağrılacak yöntem olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5dbed-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="5dbed-111">Geri çağırma kaydedildiğinde iptal işlemi zaten isteniyorsa, geri aramanın çağrılması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="5dbed-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="5dbed-112">Bu durumda, <xref:System.Net.WebClient.CancelAsync%2A> zaman uyumsuz bir işlem devam ederken yöntem hiçbir şey yapmaz, bu nedenle yöntemi çağırmak her zaman güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="5dbed-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dbed-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dbed-113">See also</span></span>

- [<span data-ttu-id="5dbed-114">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="5dbed-114">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
