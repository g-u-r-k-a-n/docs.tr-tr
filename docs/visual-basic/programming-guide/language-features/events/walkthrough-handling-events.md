---
description: 'Daha fazla bilgi edinin: Izlenecek yol: olayları Işleme (Visual Basic)'
title: Olayları İşleme
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 5101bd2287c81e03efb69b398d6cc961d3e6d9dc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436193"
---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="0b1ec-103">İzlenecek yol: Olayları İşleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b1ec-103">Walkthrough: Handling Events (Visual Basic)</span></span>

<span data-ttu-id="0b1ec-104">Bu, etkinliklerle nasıl çalışabileceğini gösteren iki konunun ikinci konudır.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-104">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="0b1ec-105">[Izlenecek yol: Izlenecek yol: olayları bildirme ve](walkthrough-declaring-and-raising-events.md)oluşturma, olayların nasıl bildirilemeyeceğini ve tetikleyeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-105">The first topic, [Walkthrough: Declaring and Raising Events](walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="0b1ec-106">Bu bölüm, bu kılavuzda yer alan formu ve sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-106">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="0b1ec-107">`Widget`Sınıf örneği geleneksel olay işleme deyimlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-107">The `Widget` class example uses traditional event-handling statements.</span></span> <span data-ttu-id="0b1ec-108">Visual Basic olaylarla çalışmaya yönelik başka teknikler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-108">Visual Basic provides other techniques for working with events.</span></span> <span data-ttu-id="0b1ec-109">Bir alıştırma olarak, ve deyimlerini kullanmak için bu örneği değiştirebilirsiniz `AddHandler` `Handles` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-109">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="0b1ec-110">Pencere öğesi sınıfının PercentDone olayını işlemek için</span><span class="sxs-lookup"><span data-stu-id="0b1ec-110">To handle the PercentDone event of the Widget class</span></span>  
  
1. <span data-ttu-id="0b1ec-111">Aşağıdaki kodu içine yerleştirin `Form1` :</span><span class="sxs-lookup"><span data-stu-id="0b1ec-111">Place the following code in `Form1`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     <span data-ttu-id="0b1ec-112">`WithEvents`Anahtar sözcüğü, değişkenin `mWidget` bir nesnenin olaylarını işlemek için kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-112">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="0b1ec-113">Nesnenin türünü, nesnenin oluşturulacağı sınıfın adını sağlayarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-113">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="0b1ec-114">`mWidget` `Form1` Değişkenler sınıf düzeyi olması gerektiğinden değişken içinde olarak belirtilir `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-114">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="0b1ec-115">Bu, yerleştirdiğiniz sınıf türünden bağımsız olarak geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-115">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="0b1ec-116">Değişkeni, `mblnCancel` yöntemi iptal etmek için kullanılır `LongTask` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-116">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="0b1ec-117">Bir olayı Işlemek için kod yazma</span><span class="sxs-lookup"><span data-stu-id="0b1ec-117">Writing Code to Handle an Event</span></span>  

 <span data-ttu-id="0b1ec-118">Kullanarak bir değişken bildirdikten hemen sonra `WithEvents` , sınıfın **kod düzenleyicisinin** sol açılır listesinde değişken adı belirir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-118">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="0b1ec-119">Seçtiğinizde `mWidget` , `Widget` sınıfın olayları sağ açılan listede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-119">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="0b1ec-120">Bir olay seçilmesi, ilgili olay yordamını önek `mWidget` ve alt çizgi ile görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-120">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="0b1ec-121">Bir değişkenle ilişkili tüm olay yordamlarına `WithEvents` önek olarak değişken adı verilir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-121">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="0b1ec-122">Bir olayı işlemek için</span><span class="sxs-lookup"><span data-stu-id="0b1ec-122">To handle an event</span></span>  
  
1. <span data-ttu-id="0b1ec-123">`mWidget` **Kod düzenleyicisinde** sol aşağı açılan listeden seçim yapın.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-123">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2. <span data-ttu-id="0b1ec-124">`PercentDone`Sağ açılan listeden olayı seçin.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-124">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="0b1ec-125">**Kod Düzenleyicisi** `mWidget_PercentDone` olay yordamını açar.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-125">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0b1ec-126">**Kod Düzenleyicisi** , yeni olay işleyicileri eklemek için yararlıdır, ancak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-126">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="0b1ec-127">Bu kılavuzda, yalnızca olay işleyicilerini doğrudan kodunuza kopyalamak daha doğrudan bir örnek olur.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-127">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3. <span data-ttu-id="0b1ec-128">Aşağıdaki kodu `mWidget_PercentDone` olay işleyicisine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0b1ec-128">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     <span data-ttu-id="0b1ec-129">Olay gerçekleştiğinde `PercentDone` olay yordamı bir denetimdeki tamamlanma yüzdesini gösterir `Label` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-129">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="0b1ec-130">`DoEvents`Yöntemi etiketin yeniden çizileceğü sağlar ve kullanıcıya **iptal** düğmesine tıklama fırsatı verir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-130">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="0b1ec-131">Olay işleyicisi için aşağıdaki kodu ekleyin `Button2_Click` :</span><span class="sxs-lookup"><span data-stu-id="0b1ec-131">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 <span data-ttu-id="0b1ec-132">Kullanıcı çalışırken **iptal** düğmesine tıkladığında `LongTask` , etkinlik `Button2_Click` `DoEvents` olay işlemenin oluşmasına izin verdiği anda olay yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-132">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="0b1ec-133">Sınıf düzeyi değişkeni `mblnCancel` olarak ayarlanır `True` ve `mWidget_PercentDone` olay bundan sonra test eder ve `ByRef Cancel` bağımsız değişkenini olarak ayarlar `True` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-133">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="0b1ec-134">Bir WithEvents değişkenini bir nesneye bağlama</span><span class="sxs-lookup"><span data-stu-id="0b1ec-134">Connecting a WithEvents Variable to an Object</span></span>  

 <span data-ttu-id="0b1ec-135">`Form1` Artık bir nesnenin olaylarını işleyecek şekilde ayarlanır `Widget` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-135">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="0b1ec-136">Her şey bir yerde bulunmaya devam etmektedir `Widget` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-136">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="0b1ec-137">Tasarım zamanında bir değişken bildirdiğinizde `WithEvents` , onunla ilişkili bir nesne yoktur.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-137">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="0b1ec-138">`WithEvents`Değişken, tıpkı diğer nesne değişkenleri gibi.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-138">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="0b1ec-139">Bir nesnesi oluşturmanız ve değişkenine bir başvuru atamanız gerekir `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-139">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="0b1ec-140">Bir nesne oluşturmak ve buna bir başvuru atamak için</span><span class="sxs-lookup"><span data-stu-id="0b1ec-140">To create an object and assign a reference to it</span></span>  
  
1. <span data-ttu-id="0b1ec-141">**Kod düzenleyicisinde** sol aşağı açılan listeden **(Form1 olayları)** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-141">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2. <span data-ttu-id="0b1ec-142">`Load`Sağ açılan listeden olayı seçin.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-142">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="0b1ec-143">**Kod Düzenleyicisi** `Form1_Load` olay yordamını açar.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-143">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3. <span data-ttu-id="0b1ec-144">`Form1_Load`Oluşturmak için olay yordamı için aşağıdaki kodu ekleyin `Widget` :</span><span class="sxs-lookup"><span data-stu-id="0b1ec-144">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 <span data-ttu-id="0b1ec-145">Bu kod yürütüldüğünde, Visual Basic bir nesnesi oluşturur `Widget` ve olaylarını ile ilişkili olay yordamlarına bağlar `mWidget` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-145">When this code executes, Visual Basic creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="0b1ec-146">Bu noktadan itibaren, olayı her ne zaman `Widget` oluşturur `PercentDone` `mWidget_PercentDone` olay yordamı yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-146">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="0b1ec-147">LongTask yöntemini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="0b1ec-147">To call the LongTask method</span></span>  
  
- <span data-ttu-id="0b1ec-148">Aşağıdaki kodu `Button1_Click` olay işleyicisine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0b1ec-148">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 <span data-ttu-id="0b1ec-149">`LongTask`Yöntemi çağrılmadan önce, tamamlanma yüzdesini gösteren etiketin başlatılması ve `Boolean` yöntemin iptal edilmesi için sınıf düzeyi bayrağının olarak ayarlanması gerekir `False` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-149">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="0b1ec-150">`LongTask` , 12,2 saniyelik bir görev süresiyle çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-150">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="0b1ec-151">`PercentDone`Olay, saniyenin her biri üçte bir kez tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-151">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="0b1ec-152">Olay her oluşturulduğunda `mWidget_PercentDone` olay yordamı yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-152">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="0b1ec-153">İşiniz `LongTask` bittiğinde, `mblnCancel` `LongTask` normal olarak mı sonlandırıldığı, yoksa durdurulmuş mi olduğunu görmek için test edilmiştir `mblnCancel` `True` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-153">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="0b1ec-154">Tamamlanma yüzdesi yalnızca önceki durumda güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-154">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="0b1ec-155">Programı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0b1ec-155">To run the program</span></span>  
  
1. <span data-ttu-id="0b1ec-156">Projeyi çalışma moduna almak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-156">Press F5 to put the project in run mode.</span></span>  
  
2. <span data-ttu-id="0b1ec-157">**Görevi Başlat** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-157">Click the **Start Task** button.</span></span> <span data-ttu-id="0b1ec-158">`PercentDone`Olay her oluşturulduğunda etiket, tamamlanan görevin yüzdesine göre güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-158">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3. <span data-ttu-id="0b1ec-159">Görevi durdurmak için **iptal** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-159">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="0b1ec-160">**İptal** düğmesinin görünümü tıkladığınızda hemen değişmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-160">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="0b1ec-161">`Click`Etkinlik `My.Application.DoEvents` Olay işlemeye izin verdiğinden olay gerçekleşmeyecek.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-161">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0b1ec-162">`My.Application.DoEvents`Yöntemi, olayları yalnızca formla aynı şekilde işlemez.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-162">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="0b1ec-163">Örneğin, bu kılavuzda, **iptal** düğmesine iki kez tıklamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-163">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="0b1ec-164">Formun olayları doğrudan işlemesine izin vermek için çoklu iş parçacığı kullanımı ' nı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-164">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="0b1ec-165">Daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="0b1ec-165">For more information, see [Managed Threading](../../../../standard/threading/index.md).</span></span>
  
 <span data-ttu-id="0b1ec-166">Programı F11 ile çalıştırmaya ve bir kerede bir satırda bir satır adım adım ilerlebileceğinizi fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-166">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="0b1ec-167">Yürütmenin nasıl girdiğini açıkça görebilir `LongTask` ve `Form1` olay her oluşturulduğunda kısa bir süre sonra yeniden girebilirsiniz `PercentDone` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-167">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="0b1ec-168">Yürütme kodunda geri yüklenirken ne olur `Form1` `LongTask` ?, yöntem yeniden çağırılır mi?</span><span class="sxs-lookup"><span data-stu-id="0b1ec-168">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="0b1ec-169">En kötü, `LongTask` olay her oluştuğunda çağrılırsa bir yığın taşması meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-169">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="0b1ec-170">`mWidget` `Widget` Yeni öğesine bir başvuru atayarak, değişkenin farklı bir nesne için olayları işlemesine neden olabilirsiniz `Widget` `mWidget` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-170">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="0b1ec-171">Aslında, `Button1_Click` düğmeye her tıkladığınızda kodu bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-171">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="0b1ec-172">Farklı bir pencere öğesinin olaylarını işlemek için</span><span class="sxs-lookup"><span data-stu-id="0b1ec-172">To handle events for a different widget</span></span>  
  
- <span data-ttu-id="0b1ec-173">Aşağıdaki kod satırını, şu şekilde `Button1_Click` görüntülenen satırdan hemen önce ekleyin `mWidget.LongTask(12.2, 0.33)` :</span><span class="sxs-lookup"><span data-stu-id="0b1ec-173">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 <span data-ttu-id="0b1ec-174">Yukarıdaki kod, düğme tıklandığında yeni bir oluşturur `Widget` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-174">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="0b1ec-175">Yöntemi tamamlandıktan hemen sonra, `LongTask` başvurusu serbest bırakılır ve yok edilir `Widget` `Widget` .</span><span class="sxs-lookup"><span data-stu-id="0b1ec-175">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="0b1ec-176">Bir `WithEvents` değişken tek seferde yalnızca bir nesne başvurusu içerebilir, bu nedenle ' ye farklı bir nesne atarsanız `Widget` `mWidget` , önceki `Widget` nesnenin olayları artık işlenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-176">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="0b1ec-177">Eğer `mWidget` eski bir başvuruyu içeren tek nesne değişkense `Widget` , nesne yok edilir.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-177">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="0b1ec-178">Çeşitli nesnelerden olayları işlemek istiyorsanız `Widget` , `AddHandler` her bir nesneden olayları ayrı olarak işlemek için ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-178">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b1ec-179">`WithEvents`İhtiyaç duyduğunuz kadar çok değişken bildirebilirsiniz, ancak `WithEvents` değişkenlerin dizileri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-179">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b1ec-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b1ec-180">See also</span></span>

- [<span data-ttu-id="0b1ec-181">İzlenecek yol: Olay Bildirme ve Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0b1ec-181">Walkthrough: Declaring and Raising Events</span></span>](walkthrough-declaring-and-raising-events.md)
- [<span data-ttu-id="0b1ec-182">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="0b1ec-182">Events</span></span>](index.md)
