---
title: 'Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
ms.openlocfilehash: aa583d8c31381d23e22f271db3d42d35e1fa14b2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826950"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="baded-102">Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="baded-102">How to: Handle Exceptions in a PLINQ Query</span></span>

<span data-ttu-id="baded-103">Bu konudaki ilk örnek, çalıştırıldığında PLıNQ sorgusundan oluşturulabilecek öğesinin nasıl işleneceğini gösterir <xref:System.AggregateException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="baded-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="baded-104">İkinci örnek, temsilcilerin içindeki try-catch bloklarının, özel durumun oluştuğu yere mümkün olduğunca yakın şekilde nasıl yerleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="baded-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="baded-105">Bu şekilde, bunları gerçekleştikleri anda yakalayabilir ve muhtemelen sorgu yürütmeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baded-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="baded-106">Özel durumların katılan iş parçacığına balon ekleme yapmasına izin verildiğinde, bir sorgu özel durum oluşturulduktan sonra bazı öğeleri işlemeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="baded-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>

<span data-ttu-id="baded-107">PLıNQ, sıralı yürütmeye geri düştüğünde bazı durumlarda özel durum ortaya çıkabilir ve bir özel durum oluşur <xref:System.AggregateException> .</span><span class="sxs-lookup"><span data-stu-id="baded-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="baded-108">Ayrıca, <xref:System.Threading.ThreadAbortException> s her zaman doğrudan yayılır.</span><span class="sxs-lookup"><span data-stu-id="baded-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>

> [!NOTE]
> <span data-ttu-id="baded-109">"Yalnızca kendi kodum" etkinleştirildiğinde, Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="baded-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="baded-110">Bu hata zararsız.</span><span class="sxs-lookup"><span data-stu-id="baded-110">This error is benign.</span></span> <span data-ttu-id="baded-111">F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baded-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="baded-112">Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel** altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="baded-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="baded-113">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="baded-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="baded-114">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="baded-114">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="baded-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="baded-115">Example</span></span>

<span data-ttu-id="baded-116">Bu örnek, her türlü oluşturulan öğeleri yakalamak için sorguyu yürüten kodun çevresine try-catch bloklarının nasıl yerleştirileceğini gösterir <xref:System.AggregateException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="baded-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

<span data-ttu-id="baded-117">Bu örnekte, özel durum oluşturulduktan sonra sorgu devam edemez.</span><span class="sxs-lookup"><span data-stu-id="baded-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="baded-118">Uygulama kodunuzun özel durumu yakalamasına göre PLıNQ, sorguyu tüm iş parçacıklarında zaten durdurdu.</span><span class="sxs-lookup"><span data-stu-id="baded-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>

## <a name="example"></a><span data-ttu-id="baded-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="baded-119">Example</span></span>

<span data-ttu-id="baded-120">Aşağıdaki örnek, bir özel durum yakalamak ve sorgu yürütmeye devam etmek için bir temsilciye bir try-catch bloğunun nasıl yerleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="baded-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a><span data-ttu-id="baded-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="baded-121">Compiling the Code</span></span>

- <span data-ttu-id="baded-122">Bu örnekleri derlemek ve çalıştırmak için onları PLıNQ veri örneği örneğine kopyalayın ve Main 'den yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="baded-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="baded-123">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="baded-123">Robust Programming</span></span>

<span data-ttu-id="baded-124">Programınızın durumunu bozmadığınız için nasıl işleneceğini bilmiyorsanız bir özel durum yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="baded-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>

## <a name="see-also"></a><span data-ttu-id="baded-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baded-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="baded-126">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="baded-126">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
