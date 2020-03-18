---
title: 'Nasıl Yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
ms.openlocfilehash: 43ca52359a48d3ac5a27933fcc8ce56c07159cac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137986"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="d0ac7-102">Nasıl Yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme</span><span class="sxs-lookup"><span data-stu-id="d0ac7-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="d0ac7-103">Bir yöntem, bir olayın sinyal verilen olmasını beklerken engellenirse, iptal jetonunun değerini denetleyemez ve zamanında yanıt veremez.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="d0ac7-104">İlk örnek, birleşik iptal çerçevesini yerel olarak desteklemeyen olaylarla <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> çalışırken bu sorunu nasıl çözeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="d0ac7-105">İkinci örnek, birleşik iptali destekleyen <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>daha akıcı bir yaklaşım gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0ac7-106">"Yalnızca Kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satırda kırılır ve "kullanıcı kodu tarafından işlenmemiş özel durum" yazan bir hata iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="d0ac7-107">Bu hata iyi huylu.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-107">This error is benign.</span></span> <span data-ttu-id="d0ac7-108">Devam etmek için F5 tuşuna basabilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="d0ac7-109">Visual Studio'nun ilk hatayı kırmasını önlemek **için, Araçlar, Seçenekler, Hata Ayıklama, Genel**altında "Sadece Kodum" onay kutusunun işaretlerini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0ac7-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0ac7-110">Example</span></span>  
 <span data-ttu-id="d0ac7-111">Aşağıdaki örnek, <xref:System.Threading.ManualResetEvent> birleşik iptali desteklemeyen bekleme tanıtıcılarının engelini nasıl kaldırılacağını göstermek için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="d0ac7-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0ac7-112">Example</span></span>  
 <span data-ttu-id="d0ac7-113">Aşağıdaki örnek, <xref:System.Threading.ManualResetEventSlim> birleşik iptali destekleyen koordinasyon ilkellerinin engelini nasıl kaldırılabildiğini göstermek için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="d0ac7-114">Aynı yaklaşım gibi <xref:System.Threading.Semaphore> `Slim` diğer hafif koordinasyon ilkel, ve <xref:System.Threading.CountdownEvent>kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="d0ac7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0ac7-115">See also</span></span>

- [<span data-ttu-id="d0ac7-116">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="d0ac7-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
