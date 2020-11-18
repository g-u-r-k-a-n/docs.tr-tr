---
title: 'Nasıl yapılır: Birden Çok İptal İsteğini Dinleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
ms.openlocfilehash: 37f42ad4de2d468cd14a916ab4e35e6577f8e375
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819779"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="e7eb6-102">Nasıl yapılır: Birden Çok İptal İsteğini Dinleme</span><span class="sxs-lookup"><span data-stu-id="e7eb6-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="e7eb6-103">Bu örnek, herhangi bir belirteç istediğinde bir işlemi iptal edebilmeniz için iki iptal belirtecinin aynı anda nasıl dinleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7eb6-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7eb6-104">"Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e7eb6-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="e7eb6-105">Bu hata zararsız.</span><span class="sxs-lookup"><span data-stu-id="e7eb6-105">This error is benign.</span></span> <span data-ttu-id="e7eb6-106">F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7eb6-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="e7eb6-107">Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel** altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="e7eb6-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7eb6-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7eb6-108">Example</span></span>  
 <span data-ttu-id="e7eb6-109">Aşağıdaki örnekte, <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> yöntemi iki belirteci tek bir belirteçte birleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7eb6-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="e7eb6-110">Bu, belirtecin bağımsız değişken olarak yalnızca bir iptal belirteci alan yöntemlere geçirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7eb6-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="e7eb6-111">Örnek, bir yöntemin, sınıfın dışından geçirilen bir belirteci ve sınıf içinde oluşturulan bir belirteci gözlemleyecek ortak bir senaryoyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7eb6-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="e7eb6-112">Bağlantılı belirteç bir oluşturduğunda <xref:System.OperationCanceledException> , özel duruma geçirilen belirteç, öncül belirteçlerinden biri değil bağlı belirteçtir.</span><span class="sxs-lookup"><span data-stu-id="e7eb6-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="e7eb6-113">Belirteçlerin hangilerinin iptal edildiğini öğrenmek için, öncül belirteçlerin durumunu doğrudan denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e7eb6-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="e7eb6-114">Bu örnekte, <xref:System.AggregateException> hiçbir şekilde oluşturulmamalıdır, ancak gerçek dünyada senaryolar <xref:System.OperationCanceledException> , görev temsilcisinden oluşturulan diğer tüm özel durumlar ' a sarıldığından, burada yakalanmalıdır <xref:System.AggregateException> .</span><span class="sxs-lookup"><span data-stu-id="e7eb6-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7eb6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7eb6-115">See also</span></span>

- [<span data-ttu-id="e7eb6-116">Yönetilen Iş parçacıklarında iptal</span><span class="sxs-lookup"><span data-stu-id="e7eb6-116">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
