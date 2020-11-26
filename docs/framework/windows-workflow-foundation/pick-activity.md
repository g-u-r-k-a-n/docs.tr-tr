---
title: Pick Etkinliği
description: Workflow Foundation 'da, çekme etkinliği bir olay tetikleyicisi kümesinin ve ardından bunlara karşılık gelen işleyicileri modellemesini basitleştirir.
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 6fc31679c20e24115e790bb50b0b5fa8dd62c705
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246140"
---
# <a name="pick-activity"></a><span data-ttu-id="c9dc8-103">Pick Etkinliği</span><span class="sxs-lookup"><span data-stu-id="c9dc8-103">Pick Activity</span></span>

<span data-ttu-id="c9dc8-104"><xref:System.Activities.Statements.Pick>Etkinlik, ardından karşılık gelen işleyiciler tarafından izlenen bir olay tetikleyicisi kümesinin modelleme işlemini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-104">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="c9dc8-105">Bir <xref:System.Activities.Statements.Pick> etkinlik <xref:System.Activities.Statements.PickBranch> , her birinin <xref:System.Activities.Statements.PickBranch> bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> etkinlik ve etkinlik arasında bir eşleştirme olduğu etkinlik koleksiyonunu içerir <xref:System.Activities.Statements.PickBranch.Action%2A> .</span><span class="sxs-lookup"><span data-stu-id="c9dc8-105">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="c9dc8-106">Yürütme sırasında, tüm dallar için Tetikleyiciler paralel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-106">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="c9dc8-107">Bir tetikleyici tamamlandığında, ilgili eylem yürütülür ve diğer tüm tetikleyiciler iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-107">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="c9dc8-108">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> Etkinliğin davranışı .NET Framework 3,5 <xref:System.Workflow.Activities.ListenActivity> etkinliğine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-108">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the .NET Framework 3.5 <xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="c9dc8-109">[Çekme etkinliği](./samples/using-the-pick-activity.md) SDK 'sını kullanan aşağıdaki ekran görüntüsünde, iki dala sahip bir çekme etkinliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-109">The following screenshot from the [Using the Pick Activity](./samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="c9dc8-110">Bir dalın, komut satırından girişi okuyan özel bir etkinlik olan **Read Input** adlı bir tetikleyicisi vardır.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-110">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="c9dc8-111">İkinci dalın bir <xref:System.Activities.Statements.Delay> etkinlik tetikleyicisi vardır.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-111">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="c9dc8-112">**Girişi oku** etkinliği etkinlik bitmeden önce verileri alırsa <xref:System.Activities.Statements.Delay> , <xref:System.Activities.Statements.Delay> gecikme iptal edilir ve konsola bir selamlama yazılır.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-112">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="c9dc8-113">Aksi takdirde, **okundu girişi** etkinliği ayrılan sürede veri almazsa, iptal edilir ve konsola bir zaman aşımı iletisi yazılır.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-113">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="c9dc8-114">Bu, herhangi bir eyleme zaman aşımı eklemek için kullanılan yaygın bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-114">This is a common pattern used to add a timeout to any action.</span></span>  
  
 ![Pick Etkinliği](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a><span data-ttu-id="c9dc8-116">En iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="c9dc8-116">Best practices</span></span>  

 <span data-ttu-id="c9dc8-117">Seçme kullanılırken, yürüten dal, tetikleyicisi önce tamamlanan daldır.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-117">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="c9dc8-118">Kavramsal olarak, tüm tetikleyiciler paralel olarak yürütülür ve bir tetikleyici, başka bir tetikleyicinin tamamlanmasına kadar iptal edilmeden önce mantığının çoğunluğunu yürütülemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-118">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="c9dc8-119">Bu göz önünde bulundurularak, çekme etkinliğini kullanırken izlenecek genel bir kılavuz, tetikleyiciyi tek bir olayı temsil edecek şekilde değerlendirmek ve buna mümkün olduğunca az mantık koymak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-119">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="c9dc8-120">İdeal olarak, tetikleyici yalnızca bir olay almak için yeterli mantık içermelidir ve bu olayın tüm işlemleri dalın eylemine gitmelidir.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-120">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="c9dc8-121">Bu yöntem, tetikleyicilerin yürütülmesi arasındaki çakışma miktarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-121">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="c9dc8-122">Örneğin, <xref:System.Activities.Statements.Pick> her tetikleyicinin bir etkinlik içerdiği ve <xref:System.ServiceModel.Activities.Receive> ardından ek mantık tarafından izlenen iki tetikleyici ile düşünün.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-122">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="c9dc8-123">Ek mantık bir boşta noktası tanıttığında, her iki <xref:System.ServiceModel.Activities.Receive> etkinliğin de başarıyla tamamması olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-123">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="c9dc8-124">Bir tetikleyici tamamen tamamlanır, diğeri kısmen tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-124">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="c9dc8-125">Bazı senaryolarda bir ileti kabul edilir ve sonra işlenmesi kısmen tamamlankabul edilemez.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-125">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="c9dc8-126">Bu nedenle, ve gibi WF yerleşik mesajlaşma etkinliklerini kullanırken <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> , <xref:System.ServiceModel.Activities.Receive> genellikle tetikleyicide kullanılır <xref:System.ServiceModel.Activities.SendReply> ve diğer mantığın mümkün olan her durumda yerine konacak olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-126">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="c9dc8-127">Tasarımcıda çekme etkinliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="c9dc8-127">Using the Pick activity in the designer</span></span>  

 <span data-ttu-id="c9dc8-128">Tasarımcıda seçimi kullanmak için araç kutusunda **seçme** ve **PickBranch dalını** bulun.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-128">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="c9dc8-129">**Seçimi** tuval üzerine sürükleyip bırakın.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-129">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="c9dc8-130">Varsayılan olarak, tasarımcıda yeni bir **çekme** etkinliği iki dal içerecektir.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-130">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="c9dc8-131">Ek dallar eklemek için **PickBranch** etkinliğini sürükleyin ve var olan dalların yanına bırakın.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-131">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="c9dc8-132">Etkinlikler, **çekme** etkinliğine herhangi bir **PickBranch**'In Action alanı **veya** **eylem** alanı üzerinde bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-132">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="c9dc8-133">Koddaki çekme etkinliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="c9dc8-133">Using the Pick Activity in code</span></span>  

 <span data-ttu-id="c9dc8-134"><xref:System.Activities.Statements.Pick>Etkinlik, <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonu etkinliklerle doldurularak kullanılır <xref:System.Activities.Statements.PickBranch> .</span><span class="sxs-lookup"><span data-stu-id="c9dc8-134">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="c9dc8-135"><xref:System.Activities.Statements.PickBranch>Her birinin <xref:System.Activities.Statements.PickBranch.Trigger%2A> türünde bir özelliği vardır <xref:System.Activities.Activity> .</span><span class="sxs-lookup"><span data-stu-id="c9dc8-135">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="c9dc8-136">Belirtilen etkinlik yürütmeyi tamamladığında, <xref:System.Activities.Statements.PickBranch.Action%2A> yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-136">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="c9dc8-137">Aşağıdaki kod örneği, <xref:System.Activities.Statements.Pick> konsolundan bir satırı okuyan bir etkinlik için zaman aşımı uygulamak üzere etkinliğin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="c9dc8-137">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
```csharp  
Sequence body = new Sequence()  
{  
    Variables = { name },  
    Activities =
   {  
       new System.Activities.Statements.Pick  
        {  
           Branches =
           {  
               new PickBranch  
               {  
                   Trigger = new ReadLine  
                   {  
                      Result = name,  
                      BookmarkName = "name"  
                   },  
                   Action = new WriteLine
                   {
                       Text = ExpressionServices.Convert<string>(ctx => "Hello " +
                           name.Get(ctx))
                   }  
               },  
               new PickBranch  
               {  
                   Trigger = new Delay  
                   {  
                      Duration = new TimeSpan(0, 0, 5)  
                   },  
                   Action = new WriteLine  
                   {  
                      Text = "Time is up."  
                   }  
               }  
           }  
       }  
   }  
};  
```  
  
```xaml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:String" Name="username" />  
  </Sequence.Variables>  
  <Pick>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <ReadLine BookmarkName="name" Result="username" />  
      </PickBranch.Trigger>  
      <WriteLine>[String.Concat("Hello ", username)]</WriteLine>  
    </PickBranch>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <Delay>00:00:05</Delay>  
      </PickBranch.Trigger>  
      <WriteLine>Time is up.</WriteLine>  
    </PickBranch>  
  </Pick>  
</Sequence>  
```
