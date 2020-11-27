---
title: NativeActivity Temel Sınıfı
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: d875f62dacadb2baf6b5d7e93ddb2933aed9cdb0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274965"
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="eaa5a-102">NativeActivity Temel Sınıfı</span><span class="sxs-lookup"><span data-stu-id="eaa5a-102">NativeActivity Base Class</span></span>

<span data-ttu-id="eaa5a-103"><xref:System.Activities.NativeActivity> , korumalı Oluşturucusu olan soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-103"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="eaa5a-104">Benzer şekilde <xref:System.Activities.CodeActivity> , <xref:System.Activities.NativeActivity> bir yöntemi uygulayarak kesinlik davranışı yazmak için kullanılır <xref:System.Activities.NativeActivity.Execute%2A> .</span><span class="sxs-lookup"><span data-stu-id="eaa5a-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="eaa5a-105">Aksine <xref:System.Activities.CodeActivity> , <xref:System.Activities.NativeActivity> yöntemine geçirilen nesne aracılığıyla iş akışı çalışma zamanının tüm sunulan özelliklerine erişimi vardır <xref:System.Activities.NativeActivityContext> <xref:System.Activities.NativeActivity.Execute%2A> .</span><span class="sxs-lookup"><span data-stu-id="eaa5a-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

## <a name="using-nativeactivitycontext"></a><span data-ttu-id="eaa5a-106">NativeActivityContext kullanma</span><span class="sxs-lookup"><span data-stu-id="eaa5a-106">Using NativeActivityContext</span></span>

 <span data-ttu-id="eaa5a-107">İş akışı çalışma zamanının özelliklerine <xref:System.Activities.NativeActivity.Execute%2A> , türünün ' nin üyelerini kullanarak yönteminin içinden erişilebilir `context` <xref:System.Activities.NativeActivityContext> .</span><span class="sxs-lookup"><span data-stu-id="eaa5a-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="eaa5a-108">Aracılığıyla kullanılabilen özellikler şunları <xref:System.Activities.NativeActivityContext> içerir:</span><span class="sxs-lookup"><span data-stu-id="eaa5a-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>

- <span data-ttu-id="eaa5a-109">Bağımsız değişkenlerin ve değişkenlerin alınması ve ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-109">Getting and setting of arguments and variables.</span></span>

- <span data-ttu-id="eaa5a-110">İle alt etkinlikleri zamanlama <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span><span class="sxs-lookup"><span data-stu-id="eaa5a-110">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>

- <span data-ttu-id="eaa5a-111">Kullanılarak Etkinlik yürütme durduruluyor <xref:System.Activities.NativeActivityContext.Abort%2A> .</span><span class="sxs-lookup"><span data-stu-id="eaa5a-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>

- <span data-ttu-id="eaa5a-112">Ve kullanarak alt yürütme iptal ediliyor <xref:System.Activities.NativeActivityContext.CancelChild%2A> <xref:System.Activities.NativeActivityContext.CancelChildren%2A> .</span><span class="sxs-lookup"><span data-stu-id="eaa5a-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>

- <span data-ttu-id="eaa5a-113">, Ve gibi yöntemler kullanılarak etkinlik yer işaretlerine <xref:System.Activities.NativeActivityContext.CreateBookmark%2A> erişin <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A> <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A> .</span><span class="sxs-lookup"><span data-stu-id="eaa5a-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>

- <span data-ttu-id="eaa5a-114">Kullanarak özel izleme özellikleri <xref:System.Activities.CodeActivityContext.Track%2A> .</span><span class="sxs-lookup"><span data-stu-id="eaa5a-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="eaa5a-115">Ve kullanarak etkinliğin yürütme özelliklerine ve değer özelliklerine erişin <xref:System.Activities.CodeActivityContext.GetProperty%2A> <xref:System.Activities.NativeActivityContext.GetValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="eaa5a-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>

- <span data-ttu-id="eaa5a-116">Ve kullanarak etkinlik eylemlerini ve işlevleri <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> zamanlama <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A> .</span><span class="sxs-lookup"><span data-stu-id="eaa5a-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="eaa5a-117">NativeActivity 'den devralan özel etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="eaa5a-117">To create a custom activity that inherits from NativeActivity</span></span>

1. <span data-ttu-id="eaa5a-118">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-118">OpenVisual Studio 2010.</span></span>

2. <span data-ttu-id="eaa5a-119">**Dosya**, **Yeni** ve ardından **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="eaa5a-120">**Proje türleri** penceresinde **Visual C#** altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="eaa5a-121">**Şablonlar** penceresinde **etkinlik kitaplığı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="eaa5a-122">Yeni proje Merhaba etkinliğini adlandırın.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-122">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="eaa5a-123">Merhaba etkinlik projesinde Activity1. xaml öğesine sağ tıklayın ve **Sil**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="eaa5a-124">Merhaba etkinlik projesine sağ tıklayın ve **Ekle**' yi ve ardından **sınıf**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="eaa5a-125">Yeni sınıfı HelloActivity.cs olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-125">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="eaa5a-126">HelloActivity.cs dosyasında aşağıdaki `using` yönergeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="eaa5a-127"><xref:System.Activities.NativeActivity>Sınıf bildirimine bir temel sınıf ekleyerek yeni sınıfın öğesinden devralmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. <span data-ttu-id="eaa5a-128">Bir yöntem ekleyerek sınıfa işlevsellik ekleyin <xref:System.Activities.NativeActivity.Execute%2A> .</span><span class="sxs-lookup"><span data-stu-id="eaa5a-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="eaa5a-129">Yöntemi geçersiz kılın <xref:System.Activities.NativeActivity.CacheMetadata%2A> ve iş akışı çalışma zamanının özel etkinliğin değişkenleri, bağımsız değişkenleri, alt öğeleri ve Temsilciler hakkında bilgi almasına izin vermek için uygun ekleme yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="eaa5a-130">Daha fazla bilgi için <xref:System.Activities.NativeActivityMetadata> sınıfına bakın.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>

9. <span data-ttu-id="eaa5a-131"><xref:System.Activities.NativeActivityContext>Bir yer işareti zamanlamak için nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="eaa5a-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="eaa5a-132"><xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A>Bir yer işaretinin oluşturulması, zamanlanzamanlaması ve sürdürülmesine ilişkin ayrıntılar için bkz..</span><span class="sxs-lookup"><span data-stu-id="eaa5a-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```
